---
title: Benutzerdefinierte Einstellungen für Windows Holographic for Business-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: 'Erstellen eines benutzerdefinierten Profils zur Verwendung der OMA-URI-Einstellungen für Windows Holographic for Business-Geräte in Microsoft Intune Sie können die folgenden Einstellungen für den Konfigurationsdienstanbieter für Richtlinien verwenden: AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates und ApplicationLaunchRestrictions.'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/26/2018
ms.article: article
ms.prod: ''
ms.service: microsoft-intune
ms.topic: article
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b8ba5078d304c0e9d6b10e4efb868642323c901c
ms.sourcegitcommit: 2795255e89cbe97d0b17383d446cca57c7335016
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2018
ms.locfileid: "47403577"
---
# <a name="custom-device-settings-for-devices-running-windows-holographic-for-business-in-intune"></a>Benutzerdefinierte Geräteeinstellungen für Windows Holographic for Business-Geräte in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 Stellen Sie mithilfe des **benutzerdefinierten** Profils von Microsoft Intune für Windows Holographic for Business OMA-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) bereit, um Features auf Geräten zu steuern. Windows Holographic for Business stellt viele Konfigurationsdienstanbieter-Einstellungen (Configuration Service Providers, CSPs) zur Verfügung. Ein CSP-Übersicht finden Sie unter [Einführung in Konfigurationsdienstanbieter (Configuration Service Providers, CSPs) für IT-Experten](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers). Bestimmte CSPs, die von Windows Holographic unterstützt werden, finden Sie unter [CSPs, die in Windows Holographic unterstützt werden](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens).

Wenn Sie nach einer bestimmten Einstellung suchen, beachten Sie, dass das [Geräteeinschränkungsprofil von Windows Holographic for Business](device-restrictions-windows-holographic.md) viele integrierte Einstellungen enthält und keine Angabe benutzerdefinierter Werte erfordert.

## <a name="create-the-custom-oma-uri-profile"></a>Erstellen des benutzerdefinierten OMA-URI-Profils

1. Verwenden Sie die unter [Konfigurieren von benutzerdefinierten Geräteeinstellungen in Microsoft Intune](custom-settings-configure.md) beschriebenen Anweisungen, um die ersten Schritte auszuführen.
2. Wählen Sie unter **Profil erstellen** die Option **Einstellungen** aus, um eine oder mehrere OMA-URI-Einstellungen hinzufügen.
3. Klicken Sie unter **Benutzerdefinierte OMA-URI-Einstellungen** auf **Hinzufügen**, um einen neuen Wert hinzuzufügen. Sie können auch auf **Exportieren** klicken, um eine Liste aller konfigurierten Werte in einer durch Trennzeichen getrennten Wertedatei (CSV) anzuzeigen.
4. Geben Sie für jede OMA-URI-Einstellung, die Sie hinzufügen möchten, die folgenden Informationen ein:
  - **Einstellungsname**: Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung ein, damit Sie sie in der Liste der Einstellungen leichter identifizieren können.
  - **Beschreibung der Einstellung**: Geben Sie optional eine Beschreibung für die Einstellung ein.
  - **Datentyp**: Wählen Sie aus dem Folgenden:
    - **Zeichenfolge**
    - **Zeichenfolge (XML)**
    - **Datum und Uhrzeit**
    - **Ganze Zahl**
    - **Gleitkomma**
    - **Boolesch**
  - **OMA-URI (Groß-/Kleinschreibung beachten)**: Geben Sie den OMA-URI an, für den Sie eine Einstellung festlegen möchten.
  - **Wert:** Geben Sie den gewünschten Wert an, der dem von Ihnen eingegebenen OMA-URI zugeordnet werden soll.
5. Navigieren Sie anschließend zurück zu **Profil erstellen**, und klicken Sie auf **Erstellen**. Das Profil wird erstellt und in der Profilliste angezeigt.

## <a name="recommended-custom-settings"></a>Empfohlene benutzerdefinierte Einstellungen

Die folgenden Einstellungen sind nützlich für Geräte unter Windows Holographic for Business:

### <a name="allowfastreconnecthttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-authenticationauthentication-allowfastreconnect"></a>[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datentyp|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Integer<br/>0 – Nicht zulässig<br/>1 – Zulässig (Standard)|

### <a name="allowupdateservicehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-allowupdateservice"></a>[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datentyp|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|Integer<br/>0 – Aktualisierungsdienst ist nicht zulässig. <br/>1 – Aktualisierungsdienst ist zulässig (Standard).|

### <a name="allowvpnhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-settingssettings-allowvpn"></a>[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datentyp|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Integer<br/>0 – Nicht zulässig<br/>1 – Zulässig (Standard)|

### <a name="requireupdatesapprovalhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-requireupdateapproval"></a>[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datentyp|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Integer<br/>0 – Nicht konfiguriert Das Gerät installiert alle anwendbaren Updates.<br/>1 – Das Gerät installiert nur Updates, die anwendbar sind und in der Liste der genehmigten Updates stehen. Legen Sie diese Richtlinie auf 1 fest, wenn die IT die Bereitstellung von Updates auf Geräten steuern möchte, etwa wenn vor der Bereitstellung Tests erforderlich sind.|

### <a name="scheduledinstalltimehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-scheduledinstalltime"></a>[ScheduledInstallTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduledinstalltime)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datentyp|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Ganze Zahl 0-23, wobei 0=12AM und 23=11PM<br/>Der Standardwert ist 3.|

### <a name="updateserviceurlhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-updateserviceurl"></a>[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datentyp|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|Zeichenfolge<br/>URL – Das Gerät prüft, ob an der angegebenen URL Updates vom WSUS-Server vorliegen.<br/>Nicht konfiguriert – Das Gerät prüft, ob Updates von Microsoft Update vorliegen.|

### <a name="approvedupdateshttpsdocsmicrosoftcomwindowsclient-managementmdmupdate-csp"></a>[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datentyp|
> |---|---|
> |./Vendor/MSFT/Update/ApprovedUpdates/*GUID*<br/><br/>**Wichtig**<br/>Sie müssen die Update-EULAs im Namen Ihrer Endbenutzer lesen und diesen zustimmen. Andernfalls stellt dies eine Verletzung von rechtlichen oder vertraglichen Verpflichtungen dar.|Knoten für Updategenehmigungen und die Zustimmung zu EULAs im Namen des Endbenutzers.<br/><br/>Weitere Informationen finden Sie unter [Update CSP (Aktualisieren von CSP)](https://docs.microsoft.com/windows/client-management/mdm/update-csp).|

### <a name="applicationlaunchrestrictionshttpsdocsmicrosoftcomwindowsclient-managementmdmapplocker-csp"></a>[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datentyp|
> |----|---|
> |./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br/><br/>**Wichtig**<br/>Im Artikel zum AppLocker-CSP finden Sie Beispiele für geschützten XML-Code. Für die Konfiguration der Einstellungen mit benutzerdefinierten Intune-Profilen müssen Sie einfachen XML-Code verwenden.|Zeichenfolge<br/>Weitere Informationen finden Sie unter [AppLocker CSP (AppLocker-CSP)](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp).|

### <a name="deletionpolicyhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[DeletionPolicy](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datentyp|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/DeletionPolicy|Integer<br/>0: umgehend löschen, wenn das Gerät sich wieder in einem Status ohne aktive Benutzer befindet<br/>1: beim Erreichen des Schwellenwerts der Speicherkapazität löschen (Standardeinstellung)<br/>2: beim Erreichen des Schwellenwerts der Speicherkapazität und des Schwellenwerts für Profilinaktivität löschen|

### <a name="enableprofilemanagerhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[EnableProfileManager](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datentyp|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/EnableProfileManager|Boolesch<br/>TRUE: aktivieren<br/>FALSE: deaktivieren (Standardeinstellung)|

### <a name="profileinactivitythresholdhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[ProfileInactivityThreshold](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datentyp|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/ProfileInactivityThreshold|Integer<br/>Der Standardwert ist 30.|


### <a name="storagecapacitystartdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStartDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datentyp|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStartDeletion|Integer<br/>Der Standardwert ist 25.|

### <a name="storagecapacitystopdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStopDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datentyp|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStopDeletion|Integer<br/>Der Standardwert ist 50.|

## <a name="find-the-policies-you-can-configure"></a>Suchen konfigurierbarer Richtlinien

Sie finden eine vollständige Liste aller von Windows Holographic unterstützten Konfigurationsdienstanbieter (Configuration Service Providers, CSPs) in [CSPs, die in Windows Holographic unterstützt werden](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). Nicht alle Einstellungen sind mit allen Windows Holographic-Versionen kompatibel. Die Tabelle im Windows-Artikel enthält entsprechende Informationen, welche Versionen für die einzelnen Konfigurationsdienstanbieter unterstützt werden.

Darüber hinaus unterstützt Intune nicht alle Einstellungen, die in diesem Artikel aufgeführt werden. Öffnen Sie den Artikel für die jeweilige Einstellung, um herauszufinden, ob die gewünschte Einstellung von Intune unterstützt wird. Jede Einstellungsseite zeigt ihren unterstützten Vorgang an. Damit die Einstellung mit Intune funktioniert, muss sie die Vorgänge **Hinzufügen** oder **Ersetzen** unterstützen.
