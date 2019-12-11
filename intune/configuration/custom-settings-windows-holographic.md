---
title: Benutzerdefinierte Einstellungen – Windows Holographic for Business-Geräte – Microsoft Intune
description: 'Fügen Sie ein benutzerdefiniertes Profil zur Verwendung der OMA-URI-Einstellungen für Windows Holographic for Business-Geräte in Microsoft Intune (einschließlich Microsoft Hololens) hinzu, oder erstellen Sie ein solches Profil. Sie können die folgenden Einstellungen für den Konfigurationsdienstanbieter für Richtlinien verwenden: AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates und ApplicationLaunchRestrictions.'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.article: article
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.topic: reference
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 54c38bac5ddf9eee1dd5f1dc6d544de3fa2395ab
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506903"
---
# <a name="use-custom-settings-for-windows-holographic-for-business-devices-in-intune"></a>Verwenden von benutzerdefinierten Einstellungen für Windows Holographic for Business-Geräte in Intune

Mithilfe von Microsoft Intune können Sie benutzerdefinierte Einstellungen für Windows Holographic for Business-Geräte mit einem benutzerdefinierten Profil hinzufügen oder erstellen. Benutzerdefinierte Profile sind ein Feature in Intune. Sie sind dafür da, Geräteeinstellungen und -features hinzuzufügen, die nicht in Intune integriert sind.

Benutzerdefinierte Profile für Windows Holographic for Business verwenden die OMA-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) zum Konfigurieren verschiedener Features. Diese Einstellungen werden in der Regel von den Herstellern der Geräte verwendet, um die Features auf dem Gerät zu steuern.

Windows Holographic for Business stellt viele Konfigurationsdienstanbieter-Einstellungen (Configuration Service Providers, CSPs) zur Verfügung. Ein CSP-Übersicht finden Sie unter [Einführung in Konfigurationsdienstanbieter (Configuration Service Providers, CSPs) für IT-Experten](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers). Bestimmte CSPs, die von Windows Holographic unterstützt werden, finden Sie unter [CSPs, die in Windows Holographic unterstützt werden](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens).

Wenn Sie nach einer bestimmten Einstellung suchen, beachten Sie, dass das [Geräteeinschränkungsprofil von Windows Holographic for Business](device-restrictions-windows-holographic.md) viele integrierte Einstellungen enthält. Sie müssen also möglicherweise keine benutzerdefinierten Werte eingeben.

In diesem Artikel erfahren Sie, wie Sie ein benutzerdefiniertes Profil für Windows Holographic für Business-Geräte erstellen. Außerdem werden die empfohlenen OMA-URI-Einstellungen aufgeführt.

## <a name="create-the-profile"></a>Erstellen des Profils

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen Profilnamen ein, z.B. `hololens custom profile`.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein.
    - **Plattform:** Wählen Sie **Windows 10 und höher** aus.
    - **Profiltyp:** Wählen Sie **Benutzerdefiniert** aus.

4. Klicken Sie unter **Benutzerdefinierte OMA-URI-Einstellungen** auf **Hinzufügen**. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung ein, damit Sie sie in der Liste der Einstellungen einfacher identifizieren können.
    - **Beschreibung:** Geben Sie eine Beschreibung ein, die einen Überblick über die Einstellung und andere wichtige Details bietet.
    - **OMA-URI** (Groß-/Kleinschreibung beachten): Geben Sie den OMA-URI an, den Sie als Einstellung verwenden möchten.
    - **Datentyp:** Wählen Sie den Datentyp aus, den Sie für diese OMA-URI-Einstellung verwenden möchten. Folgende Optionen sind verfügbar:

        - Zeichenfolge
        - Zeichenfolge (XML-Datei)
        - Datum und Uhrzeit
        - Ganze Zahl
        - Gleitkomma
        - Boolesch
        - Base64 (Datei)

    - **Wert:** Geben Sie den gewünschten Datenwert an, der dem von Ihnen eingegebenen OMA-URI zugeordnet werden soll. Der Wert hängt vom ausgewählten Datentyp ab. Beim Datentyp **Datum und Uhrzeit** wählen Sie den Wert beispielsweise aus einer Datumsauswahl aus.

    Wenn Sie einige Einstellungen hinzugefügt haben, können Sie auf **Exportieren** klicken. Wenn Sie auf **Exportieren** klicken, wird eine Liste aller hinzugefügten Werte in einer Datei mit durch Trennzeichen getrennten Werten (CSV) erstellt.

5. Klicken Sie auf **OK**, um die Änderungen zu speichern. Fügen Sie nach Bedarf weitere Einstellungen hinzu.
6. Klicken Sie anschließend auf **OK** > **Erstellen**, um das Intune-Profil zu erstellen. Dann wird das Profil erstellt und in der Liste **Gerätekonfiguration > Profile** angezeigt.

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

Sie finden eine vollständige Liste aller von Windows Holographic unterstützten Konfigurationsdienstanbieter (Configuration Service Providers, CSPs) in [CSPs, die in Windows Holographic unterstützt werden](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). Nicht alle Einstellungen sind mit allen Windows Holographic-Versionen kompatibel. In der Tabelle [CSPs supported in Windows Holographic (In Windows Holographic unterstützte CSPs)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) werden die unterstützten Versionen der einzelnen CSPs aufgeführt.

Darüber hinaus unterstützt Intune nicht alle Einstellungen, die unter [CSPs supported in Windows Holographic (In Windows Holographic unterstützte CSPs)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) aufgeführt sind. Öffnen Sie den Artikel für die jeweilige Einstellung, um herauszufinden, ob die gewünschte Einstellung von Intune unterstützt wird. Auf jeder Einstellungsseite wird angezeigt, welcher Vorgang jeweils unterstützt wird. Damit die Einstellung mit Intune funktioniert, muss sie die Vorgänge **Hinzufügen** oder **Ersetzen** unterstützen.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. [Weisen Sie anschließend das Profil zu](device-profile-assign.md).

Weitere Informationen zum Erstellen eines benutzerdefinierten Profils finden Sie unter [Windows 10-Geräte](../custom-settings-windows-10.md).
