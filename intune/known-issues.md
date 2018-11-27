---
title: Bekannte Probleme in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Informationen zu bekannten Problemen in Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 08/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: db655c49277051267036d76e518cc870757f67c2
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183042"
---
# <a name="known-issues-in-microsoft-intune"></a>Bekannte Probleme in Microsoft Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel erhalten Sie Informationen zu bekannten Problemen in Microsoft Intune.

Wenn Sie einen Fehler melden möchten, der hier nicht aufgeführt ist, [öffnen Sie eine Supportanfrage](get-support.md).

Wenn Sie sich ein neues Feature für Intune wünschen, können Sie auf der [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console)-Website einen Bericht erstellen.

## <a name="migration"></a>Migration

### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal"></a>Exportieren von klassischen Azure-Portal-Konformitätsrichtlinien zur Neuerstellung dieser Richtlinien im Azure-Portal für Intune

Konformitätsrichtlinien, die im klassischen Azure-Portal erstellt wurden, werden als veraltet markiert. Sie können vorhandene Konformitätsrichtlinien überprüfen und löschen, aber nicht aktualisieren. Wenn Sie Konformitätsrichtlinien zum aktuellen Azure-Portal für Intune migrieren müssen, können Sie die Richtlinien als durch Trennzeichen getrennte Datei (CSV-Datei) exportieren. Verwenden Sie anschließend die Informationen in der Datei, um die Richtlinien im Azure-Portal für Intune neu zu erstellen.

> [!IMPORTANT]
> Sobald das klassische Azure-Portal eingestellt wird, haben Sie keinen Zugriff mehr auf Ihre Konformitätsrichtlinien und können diese nicht mehr einsehen. Exportieren Sie Ihre Richtlinien deshalb auf jeden Fall, und erstellen Sie sie im Azure-Portal neu, bevor das klassische Azure-Portal eingestellt wird.

### <a name="intune-legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Intune-Funktionen für Legacy-PC-Clients sind nur in der Silverlight-Konsole verfügbar

Die Möglichkeit zum Verwalten von Windows 10 über die Registrierung bei Windows MDM steht in Intune über das Azure-Portal zur Verfügung. Weitere Informationen finden Sie unter [Intune in der Azure-Konsole und der Legacy-Intune-PC-Client](https://docs.microsoft.com/intune-classic/deploy-use/intune-on-azure).

### <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>Während der Migration von Intune erstellte Gruppen könnten die Funktionalität anderer Microsoft-Produkte beeinträchtigen.

Beim Migrieren von Intune zum Azure-Portal könnten Sie eine neue Gruppe mit dem Namen **All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421** sehen. Diese Gruppe enthält alle Benutzer in Ihrem Azure Active Directory, nicht nur Benutzer mit Intune-Lizenz. Dies könnte zu Problemen mit anderen Microsoft-Produkten führen, wenn Sie erwarten, dass einige vorhandene oder neue Benutzer nicht Mitglieder von Gruppen sind.

### <a name="status-blades-for-migrated-policies-do-not-work"></a>Statusblätter für migrierte Richtlinien funktionieren nicht

Sie können keine Statusinformationen für Richtlinien anzeigen, die aus dem klassischen Azure-Portal in das Azure-Portal migriert wurden. Im klassischen Portal können Sie jedoch weiterhin Berichte für diese Richtlinien anzeigen. Zum Anzeigen von Statusinformationen für migrierte Konfigurationsrichtlinien müssen Sie diese im Azure-Portal neu erstellen.

## <a name="apps"></a>Apps


### <a name="multiple-app-install-prompts-for-certain-vpp-apps"></a>Mehrfache Aufforderungen zur App-Installation für bestimmte VPP-Apps
Möglicherweise werden mehrfache Aufforderungen zur App-Installation für bestimmte VPP-Apps angezeigt, die auf den Benutzergeräten bereits installiert sind. Dieses Problem tritt auf, wenn Sie für das VPP-Token, das Sie auf das Intune Azure-Portal hochgeladen haben, die Option **Automatische App-Updates** auf **ON** festgelegt haben.    

Deaktivieren Sie zum Umgehen dieses Problems die Option **Automatische App-Updates** für das VPP-Token. Öffnen Sie dazu Microsoft Intune im Azure-Portal. Wählen Sie in Intune **Client-Apps** > **iOS-VPP-Token** aus. Wählen Sie anschließend das VPP-Token aus, das die betroffene App bereitgestellt hat. Klicken Sie auf **Bearbeiten** > **Automatische App-Updates** > **OFF** (Deaktivieren) > **Speichern**. Alternativ können Sie die Bereitstellung der betroffenen App als VPP-App beenden, um die Aufforderungen zu beenden.    

Dies ist ein bekanntes Problem im aktuellen Release. Eine Behebung des Problems ist bereits geplant. Sobald die Fehlerbehebung implementiert ist, werden den Benutzern keine mehrfachen Aufforderungen zur App-Installation mehr angezeigt.

### <a name="ios-volume-purchased-apps-only-available-in-default-intune-tenant-language"></a>Per Volumenlizenz erworbene Apps nur in Standardsprache des Intune-Mandanten verfügbar
Per Volumenlizenz erworbene iOS-Apps werden angezeigt und können nur für den gleichen Ländercode wie Ihr Intune-Konto zugewiesen werden. Intune synchronisiert nur Apps aus dem gleichen iTunes-Gebietsschema wie der Ländercode des Intune-Mandantenkontos. Wenn Sie beispielsweise eine App kaufen, die nur im US-Store verfügbar ist, Ihr Intune-Konto jedoch auf Deutsch ist, zeigt Intune diese App nicht an.

### <a name="multiple-copies-of-the-same-ios-volume-purchase-program-are-uploaded"></a>Es werden mehrere Kopien desselben iOS-Volumenlizenzprogramms hochgeladen.
Klicken Sie nicht mehrmals für das gleiche VPP-Token auf die Schaltfläche **Hochladen**. Dies führt dazu, dass doppelte VPP-Token hochgeladen und Apps mehrmals für das gleiche VPP-Token synchronisiert werden.

### <a name="some-managed-browser-traffic-not-routed-through-azure-app-proxy----2463492---"></a>Bestimmter Managed Browser-Datenverkehr wird nicht über Azure-App-Proxy weitergeleitet <!-- 2463492 -->
Es gibt ein bekanntes Problem bei der Integration von Managed Browser und App-Proxy, aufgrund dessen bestimmter tertiärer Datenverkehr (wie JavaScript- oder AJAX-Aufrufe) nicht über den Azure-App-Proxy geleitet wird. Dies ist ein bekanntes Problem im aktuellen Release.  

<!-- ## Groups -->

## <a name="device-configuration"></a>Gerätekonfiguration

### <a name="you-cannot-save-a-windows-information-protection-policy-for-some-devices"></a>Eine Windows Information Protection-Richtlinie kann für einige Geräte nicht gespeichert werden

Für Geräte, die nicht bei Intune registriert sind, können Sie in den Einstellungen für eine Windows Information Protection-Richtlinie im Feld **Unternehmensidentität** nur eine primäre Domäne angeben.
Wenn Sie (über **Erweiterte Einstellungen** > **Umkreisnetzwerk** > **Geschützte Domäne hinzufügen**) weitere Domänen hinzufügen, können Sie die Richtlinie nicht speichern. Die angezeigte Fehlermeldung wird in Kürze geändert, um mehr Genauigkeit zu bieten.

### <a name="cisco-anyconnect-and-cisco-legacy-anyconnect-vpn-client-support---ios"></a>Cisco AnyConnect- und Cisco Legacy AnyConnect-VPN-Clientunterstützung – iOS

Auf iOS-Geräten funktioniert die NAC-Integration (Network Access Control) nicht mit dem neuen Cisco AnyConnect-Client. Zusammen mit Cisco wird versucht, eine NAC-Integration bereitzustellen.

Weitere Informationen zu den Cisco AnyConnect- und Cisco Legacy AnyConnect-Clients finden Sie unter [Erstellen von VPN-Profilen in Intune](vpn-settings-ios.md).

### <a name="using-the-numeric-password-type-with-macos-sierra-devices"></a>Verwenden des numerischen Kennworttyps mit macOS Sierra-Geräten

Wenn Sie derzeit in einem Geräteregistrierungsprofil für macOS Sierra-Geräte **Numerisch** **Erforderlicher Kennworttyp** auswählen, wird **Alphanumerisch** erzwungen. Wenn Sie kein numerisches Kennwort mit diesen Geräten verwenden möchten, konfigurieren Sie diese Einstellung nicht.
Dieses Problem wird ggf. in einer künftigen Version von MacOS korrigiert.

Weitere Informationen zu diesen Einstellungen finden Sie unter [Einstellungen für Geräteeinschränkungen für macOS-Geräte in Microsoft Intune](device-restrictions-macos.md).

## <a name="compliance"></a>Konformität

### <a name="compliance-policies-from-intune-do-not-show-up-in-new-console"></a>Konformitätsrichtlinien von Intune werden in der neuen Konsole nicht angezeigt

Konformitätsrichtlinien, die Sie im klassischen Intune-Portal erstellt haben, werden migriert, jedoch im Azure-Portal aufgrund von Änderungen am Design nicht angezeigt. Konformitätsrichtlinien, die Sie im klassischen Intune-Portal erstellt haben, werden noch erzwungen, jedoch müssen Sie sie im klassischen Portal anzeigen und bearbeiten.

Darüber hinaus werden neue Konformitätsrichtlinien, die Sie im Azure-Portal erstellen, im klassischen Portal nicht angezeigt.

Weitere Informationen finden Sie unter [Was ist die Gerätekonformität in Intune in Azure (Vorschau)?](device-compliance.md).

<!-- ## Enrollment -->

## <a name="conditional-access"></a>Bedingter Zugriff

### <a name="conditional-access-settings-from-intune-do-not-show-up-in-new-console"></a>Einstellungen für den bedingten Zugriff von Intune werden in der neuen Konsole nicht angezeigt

Nachdem Ihr Mandant zum Azure-Portal migriert wurde, werden Ihre Einstellungen für den bedingten Zugriff weiter angewendet werden; sie werden jedoch nicht im Azure Intune-Portal erscheinen. 

Wenn Sie diese Einstellungen im Azure-Portal anzeigen und verwalten möchten, müssen Sie die alten Einstellungen aus dem klassischen Portal entfernen und sie im Azure-Portal neu erstellen. 

Weitere Informationen finden Sie unter [Best Practices für den bedingten Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/best-practices).

## <a name="data-protection"></a>Datenschutz

### <a name="ios-app-protection-policies"></a>iOS-App-Schutzrichtlinien

Sie können [App-Schutzrichtlinien für iOS](app-protection-policy-settings-ios.md) definieren, die für Benutzer auf Geräten verfügbar sind, die über die Verwaltung mobiler Geräte (MAM) ohne Registrierung verwaltet werden. Aufgrund eines temporären Fehlers können Sie diese Richtlinien nur für iOS-Versionen mit einer Version mit einem einzelnen Dezimaltrennzeichen anstatt mehreren Dezimaltrennzeichen definieren. Anstatt also eine Mindestversion von iOS 10.3.1 festzulegen, legen Sie sie für iOS 10.3. fest. Diese Problem wird mit einem zukünftigen Update für das iOS SDK gelöst.


## <a name="administration-and-accounts"></a>Verwaltung und Konten

Globale Administratoren (auch als Mandantenadministratoren bezeichnet) können weiterhin alltägliche Verwaltungsaufgaben ausführen, ohne über eine separate Intune- oder EMS-Lizenz (Enterprise Mobility Suite) zu verfügen. Wenn sie den Dienst jedoch verwenden möchten, um z. B. ihr eigenes Gerät oder ein unternehmenseigenes Gerät zu registrieren bzw. das Intune-Unternehmensportal zu verwenden, benötigen sie eine Intune- oder EMS-Lizenz.

<!-- ## Additional items -->
