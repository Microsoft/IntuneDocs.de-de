---
title: Verwenden von stagenow-Protokollen auf Android-Zebra Geräten in Microsoft InTune-Azure | Microsoft-Dokumentation
description: Weitere Informationen finden Sie unter Häufige Probleme und Lösungen bei der Verwendung von stagenow auf Android-Geräten mit Microsoft InTune. Außerdem erfahren Sie, wie Sie Protokolle erhalten und wie Sie die Protokolle für Erfolg oder Fehler lesen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e7ed93c86d3fbe7ed7a6ac5d4b1a3494fb55f2bc
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506994"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Problembehandlung und mögliche Probleme auf Android-Zebra Geräten in Microsoft InTune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In Microsoft InTune können Sie mit der Verwendung [von "Zebra Mobility Extensions (MX)" Android-Zebra Geräte verwalten](android-zebra-mx-overview.md). Bei der Verwendung von Zebra Geräten erstellen Sie Profile in stagenow, um Einstellungen zu verwalten und Sie in InTune hochzuladen. InTune verwendet die stagenow-App zum Anwenden der Einstellungen auf den Geräten. Die stagenow-App erstellt außerdem eine ausführliche Protokolldatei auf dem Gerät, das für die Problembehandlung verwendet wird.

Diese Funktion gilt für:

- Android

Beispielsweise erstellen Sie ein Profil in stagenow, um ein Gerät zu konfigurieren. Wenn Sie das stagenow-Profil erstellen, wird im letzten Schritt eine Datei für das Testen des Profils generiert. Diese Datei wird mit der stagenow-App auf dem Gerät genutzt.

In einem anderen Beispiel erstellen Sie ein Profil in stagenow und testen es. Fügen Sie in InTune das Profil stagenow hinzu, und weisen Sie es dann Ihren Zebra-Geräten zu. Beim Überprüfen des Status des zugewiesenen Profils zeigt das Profil einen Status auf hoher Ebene an.

In beiden Fällen erhalten Sie weitere Informationen aus der stagenow-Protokolldatei, die bei jeder Anwendung eines stagenow-Profils auf dem Gerät gespeichert wird.

Einige Probleme stehen nicht im Zusammenhang mit dem Inhalt des stagenow-Profils und werden nicht in den Protokollen widergespiegelt.

In diesem Artikel erfahren Sie, wie Sie die stagenow-Protokolle lesen und einige andere potenzielle Probleme mit Zebra-Geräten auflisten, die möglicherweise nicht in den Protokollen widergespiegelt werden.

[Verwenden und Verwalten von Zebra-Geräten mit Zebra Mobility Extensions](android-zebra-mx-overview.md) enthält weitere Informationen zu diesem Feature.

## <a name="get-the-logs"></a>Protokolle erhalten

### <a name="use-the-stagenow-app-on-the-device"></a>Verwenden der stagenow-App auf dem Gerät
Wenn Sie ein Profil direkt mithilfe von stagenow auf dem Computer testen, anstatt [InTune zum Bereitstellen des Profils zu](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow)verwenden, speichert die stagenow-App auf dem Gerät die Protokolle aus dem Test. Um die Protokolldatei zu erhalten, verwenden Sie die Option **More (...)** in der stagenow-App auf dem Gerät.

### <a name="get-logs-using-android-debug-bridge"></a>Protokolle mithilfe von Android Debug Bridge
Um Protokolle zu erhalten, nachdem das Profil bereits mit InTune bereitgestellt wurde, verbinden Sie das Gerät mit einem Computer [Android Debug Bridge (ADB)](https://developer.android.com/studio/command-line/adb) (öffnet die Website von Android).

Auf dem Gerät werden Protokolle in `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files` gespeichert.

### <a name="get-logs-from-email"></a>Protokolle per e-Mail erhalten
Um Protokolle zu erhalten, nachdem das Profil bereits mit InTune bereitgestellt wurde, können Endbenutzer die Protokolle per e-Mail über eine e-Mail-App auf dem Gerät senden. Öffnen Sie auf dem Zebra-Gerät die Unternehmensportal-APP, und [Senden Sie die Protokolle](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). Mit der Funktion "Sende Protokolle" wird auch eine Powerlift-incidentkennung erstellt, auf die Sie verweisen können, wenn der Microsoft-Support kontaktiert

## <a name="read-the-logs"></a>Lesen der Protokolle

Wenn Sie sich die Protokolle ansehen, gibt es immer dann einen Fehler, wenn Sie das `<characteristic-error>`-Tag sehen. Fehlerdetails werden in das `<parm-error>`-Tag > `desc`-Eigenschaft geschrieben.

## <a name="error-types"></a>Fehlertypen

Auf den Zebra Geräten sind verschiedene Fehler Berichterstattungs Stufen enthalten:

- Der CSP wird auf dem Gerät nicht unterstützt. Beispielsweise handelt es sich bei dem Gerät nicht um ein Mobilgerät, und es ist kein Mobilfunk-Manager vorhanden.
- Die MX-oder OSX-Version ist nicht übereinstimmen. Jeder CSP ist versioniert. Eine vollständige Unterstützungs Matrix finden Sie in [der Dokumentation von Zebra](http://techdocs.zebra.com/mx/) (öffnet die Website von Zebra).
- Das Gerät meldet ein anderes Problem oder einen Fehler.

## <a name="examples"></a>Beispiele

Beispielsweise verfügen Sie über das folgende Eingabe Profil:

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

Im Protokoll ist der XML-Code mit der Eingabe identisch. Diese abgleichsausgabe bedeutet, dass das Profil ohne Fehler erfolgreich auf das Gerät angewendet wurde:

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

In einem anderen Beispiel haben Sie die folgende Eingabe:

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

Das Protokoll zeigt einen Fehler an, da es ein `<characteristic-error>`-Tag enthält. In diesem Szenario hat das Profil versucht, ein Android-Paket (APK) zu installieren, das im angegebenen Pfad nicht vorhanden ist:

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

## <a name="other-potential-issues-with-zebra-devices"></a>Andere potenzielle Probleme mit Zebra-Geräten

In diesem Abschnitt werden andere mögliche Probleme aufgelistet, die bei der Verwendung von Zebra-Geräten mit dem Geräte Administrator auftreten können. Diese Probleme werden nicht in den stagenow-Protokollen gemeldet.

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView ist veraltet.

Wenn sich ältere Geräte mit der Unternehmensportal-App anmelden, sehen Benutzer möglicherweise eine Meldung, dass die System-WebView-Komponente veraltet ist und aktualisiert werden muss. Wenn auf dem Gerät Google Play installiert ist, stellen Sie eine Verbindung mit dem Internet her, und suchen Sie nach Updates. Wenn auf dem Gerät Google Play nicht installiert ist, erhalten Sie die aktualisierte Version der Komponente, und wenden Sie Sie auf die Geräte an. Oder aktualisieren Sie auf das neueste von Zebra ausgestellte Geräte Betriebssystem.

### <a name="management-actions-take-a-long-time"></a>Verwaltungs Aktionen nehmen lange Zeit in Anspruch.

Wenn Google Play Dienste nicht verfügbar sind, dauert es bis zu 8 Stunden, bis einige Aufgaben abgeschlossen sind. [Einschränkungen für InTune-Unternehmensportal-App für Android](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (öffnet eine andere Microsoft-Website) können eine gute Ressource sein.

### <a name="device-spoofing-suspected-shows-in-intune"></a>"Verdächtiger Geräte Spoofing" wird in InTune angezeigt.

Dieser Fehler weist darauf hin, dass InTune verdächtige Android-Geräte als ein Zebra-Gerät meldet.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>Unternehmensportal APP ist älter als die mindestens erforderliche Version.

InTune kann die mindestens erforderliche Version der Unternehmensportal-APP aktualisieren. Wenn Google Play nicht auf dem Gerät installiert ist, wird die APP Unternehmensportal nicht automatisch aktualisiert. Wenn die mindestens erforderliche Version neuer als die installierte Version ist, wird die Unternehmensportal-APP nicht mehr funktionieren. Aktualisieren Sie auf die neueste Unternehmensportal-App mithilfe [von Sideload auf Zebra Geräten](android-zebra-mx-overview.md#sideload-the-company-portal-app).

## <a name="next-steps"></a>Nächste Schritte

[Zebra-Diskussionsforen](https://developer.zebra.com/community/home/discussions) (öffnet die Website von Zebra)

[Verwenden und Verwalten von Zebra-Geräten mit Zebra Mobility Extensions in Intune](android-zebra-mx-overview.md)
