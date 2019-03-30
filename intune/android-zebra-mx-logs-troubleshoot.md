---
title: Verwendung StageNow anmeldet Zebra von Android-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Finden Sie häufige Probleme und Lösungen aus, wenn StageNow auf Android-Geräten mit Microsoft Intune verwenden. Außerdem erfahren Sie, wie Protokolle zu erhalten, und sehen Beispiele für das Lesen der Protokolle für den Erfolg oder Fehler.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36476820805c00cefafcd9f64dd2f08a014762c0
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490540"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Problembehandlung und finden Sie mögliche Probleme Zebra von Android-Geräte in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In Microsoft Intune können Sie [Zebra Mobility Extensions (MX) zum Verwalten von Geräten mit Android Zebra](android-zebra-mx-overview.md). Wenn Zebra Geräte zu verwenden, Sie Erstellen von Profilen in StageNow zum Verwalten von Einstellungen und laden diese in Intune hoch. Intune verwendet die StageNow-app zum Anwenden der Einstellungen auf den Geräten. Die app StageNow erstellt auch eine ausführliche Protokolldatei auf dem Gerät, das zur Problembehandlung verwendet wird.

Diese Funktion gilt für:

- Android

Beispielsweise erstellen Sie ein Profil in StageNow so konfigurieren Sie ein Gerät an. Bei der Erstellung des Profils StageNow generiert im letzte Schritt eine Datei aus, für das Profil zu testen. Sie nutzen diese Datei mit der StageNow-app auf dem Gerät.

Weiteres Beispiel: Sie erstellen ein Profil in StageNow und testen. In Intune Sie fügen die StageNow-Profil hinzu und weisen es dann an Ihre Geräte Zebra. Wenn Sie den Status des zugewiesenen Profils zu überprüfen, zeigt das Profil den allgemeinen Status an.

In beiden Fällen erhalten Sie weitere Details aus der Protokolldatei StageNow, das auf dem Gerät gespeichert wird, jedes Mal, wenn ein Profil StageNow gilt.

Einige Probleme im Zusammenhang mit der sind nicht auf den Inhalt des Profils StageNow und sind nicht in den Protokollen angezeigt.

In diesem Artikel erfahren Sie, wie zum Lesen der Protokolle StageNow, und führt einige andere potenzielle Probleme mit Zebra-Geräten, die in den Protokollen nicht wiedergegeben werden können.

[Verwenden und Verwalten von Zebra Geräte mit Zebra Mobility Erweiterungen](android-zebra-mx-overview.md) finden Sie weitere Informationen zu dieser Funktion.

## <a name="get-the-logs"></a>Rufen Sie die Protokolle

### <a name="use-the-stagenow-app-on-the-device"></a>Verwenden Sie die StageNow-app auf dem Gerät
Beim Testen eines Profils mithilfe der StageNow direkt auf Ihrem Computer, anstelle von [Intune zum Bereitstellen des Profils](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow), speichert die StageNow-app auf dem Gerät die Protokolle aus dem Test. Rufen Sie die Protokolldatei mit dem **Weitere (...)**  Option in der StageNow-app auf dem Gerät.

### <a name="get-logs-using-android-debug-bridge"></a>Abrufen von Protokollen mithilfe von Android Debug Bridge
Um Protokolle zu erhalten, nachdem das Profil in Intune bereits bereitgestellt wurde, schließen Sie das Gerät auf einem Computer mit [Android Debug Bridge (Adb)](https://developer.android.com/studio/command-line/adb) (öffnet die Android-Website).

Auf dem Gerät werden die Protokolle in gespeichert. `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>Abrufen von Protokollen per e-Mail
Um Protokolle zu erhalten, nachdem das Profil in Intune bereits bereitgestellt wurde, können Sie Endbenutzern die Protokolle mit einer e-Mail-app auf dem Gerät senden. Öffnen Sie die Unternehmensportal-app auf dem Gerät Zebra und [senden die Protokolle](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). Mit der Send-Protokolle-Funktion erstellt außerdem eine PowerLift Incident-ID, die Sie verweisen können, wenn Sie sich an Microsoft Support wenden.

## <a name="read-the-logs"></a>Lesen Sie die Protokolle

Wenn Sie die Protokolle zu suchen, ein Fehler vorliegt, wenn Sie sehen die `<characteristic-error>` Tag. Fehlerdetails werden geschrieben, um die `<parm-error>` Tag > `desc` Eigenschaft.

## <a name="error-types"></a>Fehlertypen

Zebra Geräten sind verschiedene Ebenen für die Fehlerberichterstattung:

- Der CSP wird auf Gerät nicht unterstützt. Beispielsweise wird das Gerät wird nicht von einem Mobile-Gerät und verfügt nicht über einen Mobilfunk-Manager.
- Die MX- oder OS x-Version ist falsch zugeordnet. Jeder CSP ist versionsspezifisch. Eine vollständige Support-Matrix finden Sie unter [des Zebra Dokumentation](http://techdocs.zebra.com/mx/) (öffnet die Zebra-Website).
- Das Gerät meldet ein anderes Problem oder Fehler.

## <a name="examples"></a>Beispiele

Beispielsweise haben Sie die folgende Eingabe-Profil:

```xml
<wap-provisioningdoc>
    <characteristic type="Clock">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

Im Protokoll ist die XML identisch mit der Eingabe. Diese übereinstimmende Ausgabe bedeutet, dass das Profil auf das Gerät ohne Fehler erfolgreich angewendet:

```xml
<wap-provisioningdoc>
    <characteristic type="Clock" version="6.0">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

In einem anderen Beispiel müssen Sie die folgende Eingabe:

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2" >
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic type="AppMgr" version="4.2" >
        <parm name="Action" value="Install"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic>
</wap-provisioningdoc>
```

Das Protokoll enthält einen Fehler, da er enthält eine `<characteristic-error>` Tag. In diesem Szenario versucht haben, installieren ein Android-Paket (APK), die nicht vorhanden, im angegebenen Pfad "das Profil":

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2">
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic-error type="AppMgr" version="5.1" desc="missing">
        <parm-error name="Action" value="Install" desc="apk doesnot exist in the path"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic-error>
</wap-provisioningdoc>
```

## <a name="other-potential-issues-with-zebra-devices"></a>Andere mögliche Probleme mit Zebra-Geräte

Dieser Abschnitt enthält andere mögliche Probleme, die möglicherweise angezeigt werden, wenn Zebra-Geräte mit dem Geräteadministrator verwenden. Diese Probleme sind nicht in den Protokollen StageNow gemeldet.

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView ist veraltet.

Wenn ältere Geräte über die Unternehmensportal-app anmelden, können Benutzer finden Sie unter eine Meldung, dass die System WebView-Komponente veraltet ist und muss aktualisiert. Wenn das Gerät verfügt über Google Play installiert ist, verbinden Sie es mit dem Internet, und suchen Sie nach Updates. Wenn das Gerät über keine Google Play installiert, die aktualisierte Version der Komponente zu erhalten und auf den Geräten anwenden. Oder mit dem aktuellen Gerät Zebra Ausstellendes Betriebssystem aktualisieren.

### <a name="management-actions-take-a-long-time"></a>Verwaltungsaktionen dauern sehr lange

Wenn Sie Google Play-Dienste nicht verfügbar sind, werden einige Aufgaben bis zu 8 Stunden in Anspruch. [Einschränkungen der Intune-Unternehmensportal-app für Android](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (öffnet eine andere Microsoft-Website) ist möglicherweise eine gute Ressource.

### <a name="device-spoofing-suspected-shows-in-intune"></a>"Gerätespoofing vermuteten" zeigt, in Intune

Dieser Fehler weist darauf hin, dass Intune vermutet, dass ein nicht - Zebra Android-Gerät seines Modells und Herstellers als Zebra Gerät meldet.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>Die Unternehmensportal-app ist älter als die mindestens erforderliche version

Intune kann die mindestens erforderliche Version der Unternehmensportal-app aktualisieren. Wenn Sie Google Play nicht auf dem Gerät installiert ist, die Unternehmensportal-app nicht automatisch aktualisiert. Wenn die mindestens Version neuer als die installierte Version ist erforderliche, wird die Unternehmensportal-app funktioniert nicht. Update für die aktuelle Unternehmensportal-app, mit [sideload auf Zebra Geräten](android-zebra-mx-overview.md#sideload-the-company-portal-app).

## <a name="next-steps"></a>Nächste Schritte

[Zebra Diskussionsrunden](https://developer.zebra.com/community/home/discussions) (öffnet die Zebra-Website)

[Verwenden und Verwalten von Zebra-Geräten mit Zebra Mobility-Erweiterungen in Intune](android-zebra-mx-overview.md)
