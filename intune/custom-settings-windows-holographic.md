---
title: "Benutzerdefinierte Intune-Einstellungen für Windows Holographic for Business-Geräte"
titlesuffix: Azure portal
description: "Erfahren Sie etwas über die Einstellungen, die Sie in einem benutzerdefinierten Windows Holographic for Business-Profil verwenden können."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 2/26/2018
ms.article: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d204f9de5c02835fe059783807558496b0cff039
ms.sourcegitcommit: 80a2eefc1896a42cc2bc16be23093d1abf58b088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2018
---
# <a name="custom-device-settings-for-windows-holographic-for-business-devices-in-microsoft-intune"></a>Benutzerdefinierte Geräteeinstellungen für Windows Holographic for Business-Geräte in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Stellen Sie mithilfe des **benutzerdefinierten** Profils von Microsoft Intune für Windows Holographic for Business OMA-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) bereit, um Features auf Geräten zu steuern. Windows Holographic for Business stellt viele Konfigurationsdienstanbieter-Einstellungen (Configuration Service Providers, CSPs) zur Verfügung. Ein CSP-Übersicht finden Sie unter [Einführung in Konfigurationsdienstanbieter (Configuration Service Providers, CSPs) für IT-Experten](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers). Bestimmte CSPs, die von Windows Holographic unterstützt werden, finden Sie unter [CSPs, die in Windows Holographic unterstützt werden](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens).

Wenn Sie nach einer bestimmten Einstellung suchen, beachten Sie, dass das [Geräteeinschränkungsprofil von Windows Holographic for Business](device-restrictions-windows-holographic.md) viele integrierte Einstellungen enthält und keine Angabe benutzerdefinierter Werte erfordert.

1. Anweisungen zu den ersten Schritten finden Sie unter [Konfigurieren von benutzerdefinierten Geräteeinstellungen in Microsoft Intune](custom-settings-configure.md).
2. Wählen Sie unter **Profil erstellen** die Option **Einstellungen** aus, um eine oder mehrere OMA-URI-Einstellungen hinzufügen.
3. Klicken Sie unter **Benutzerdefinierte OMA-URI-Einstellungen** auf **Hinzufügen**, um einen neuen Wert hinzuzufügen. Sie können auch auf **Exportieren** klicken, um eine Liste aller konfigurierten Werte in einer durch Trennzeichen getrennten Wertedatei (CSV) anzuzeigen.
4. Geben Sie für jede OMA-URI-Einstellung, die Sie hinzufügen möchten, die folgenden Informationen ein:
    - **Einstellungsname** – Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung ein, damit Sie sie in der Liste der Einstellungen leichter identifizieren können.
    - **Beschreibung der Einstellung** – Geben Sie optional eine Beschreibung für die Einstellung ein.
    - **Datentyp** – Wählen Sie aus:
        - **Zeichenfolge**
        - **Zeichenfolge (XML)**
        - **Datum und Uhrzeit**
        - **Ganze Zahl**
        - **Gleitkomma**
        - **Boolesch**
    - **OMA-URI (Groß-/Kleinschreibung beachten)** – Geben Sie den OMA-URI an, für den Sie eine Einstellung festlegen möchten.
    - **Wert** – Geben Sie den Wert an, der mit der von Ihnen eingegebenen OMA-URI verknüpft werden soll.
1. Navigieren Sie anschließend zurück zu **Profil erstellen**, und klicken Sie auf **Erstellen**.
Das Profil wird erstellt und in der Profilliste angezeigt.

## <a name="recommended-custom-settings"></a>Empfohlene benutzerdefinierte Einstellungen

Die folgenden Einstellungen sind nützlich für Geräte unter Windows Holographic for Business:


|Name der Einstellung|OMA-URI|Datentyp  |
|---------|---------|---------|
|[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)|./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Integer<br>0 – Nicht zulässig<br>1 – Zulässig (Standard)|
|[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)|./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Integer<br>0 – Nicht zulässig<br>1 – Zulässig (Standard)|
|[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)|./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|Integer<br>0 – Aktualisierungsdienst ist nicht zulässig. <br>1 – Aktualisierungsdienst ist zulässig (Standard).|
|[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)|./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|Zeichenfolge<br>URL – Das Gerät prüft, ob an der angegebenen URL Updates vom WSUS-Server vorliegen.<br>Nicht konfiguriert – Das Gerät prüft, ob Updates von Microsoft Update vorliegen.|
|[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)|./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Integer<br>0 – Nicht konfiguriert Das Gerät installiert alle anwendbaren Updates.<br>1 – Das Gerät installiert nur Updates, die anwendbar sind und in der Liste der genehmigten Updates stehen. Legen Sie diese Richtlinie auf 1 fest, wenn die IT die Bereitstellung von Updates auf Geräten steuern möchte, etwa wenn vor der Bereitstellung Tests erforderlich sind.|
|[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)|./Vendor/MSFT/Update/ApprovedUpdates<br><br>**Wichtig**<br>Sie müssen die Update-EULAs im Namen Ihrer Endbenutzer lesen und diesen zustimmen. Andernfalls stellt dies eine Verletzung von rechtlichen oder vertraglichen Verpflichtungen dar.|Knoten für Updategenehmigungen und die Zustimmung zu EULAs im Namen des Endbenutzers.|
[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)|./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br><br>**Wichtig**<br>Im Artikel zum AppLocker-CSP finden Sie Beispiele für geschützten XML-Code. Für die Konfiguration der Einstellungen mit benutzerdefinierten Intune-Profilen müssen Sie einfachen XML-Code verwenden.|Zeichenfolge<br>Weitere Informationen finden Sie im Artikel [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp) (AppLocker-CSP). 

## <a name="how-to-find-the-policies-you-can-configure"></a>Suchen konfigurierbarer Richtlinien

Sie finden eine vollständige Liste aller von Windows Holographic unterstützten Konfigurationsdienstanbieter (Configuration Service Providers, CSPs) in [CSPs, die in Windows Holographic unterstützt werden](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). Nicht alle Einstellungen sind mit allen Windows Holographic-Versionen kompatibel. Die Tabelle im Windows-Artikel enthält entsprechende Informationen, welche Versionen für die einzelnen Konfigurationsdienstanbieter unterstützt werden.

Darüber hinaus unterstützt Intune nicht alle Einstellungen, die in diesem Artikel aufgeführt werden. Öffnen Sie den Artikel für die jeweilige Einstellung, um herauszufinden, ob die gewünschte Einstellung von Intune unterstützt wird. Jede Einstellungsseite zeigt ihren unterstützten Vorgang an. Damit die Einstellung mit Intune funktioniert, muss sie die Vorgänge **Hinzufügen** oder **Ersetzen** unterstützen.
