---
title: Registrierung für Active Directory Hybrid-Geräte – Windows Autopilot
titleSuffix: ''
description: Verwenden Sie Windows Autopilot, um in Azure AD Hybrid eingebundene Geräte in Microsoft Intune zu registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ab90dc9a95e461ad8c5913131a23a0355e9d072c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509219"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-by-using-intune-and-windows-autopilot"></a>Bereitstellen von in Azure AD Hybrid eingebundenen Geräten mit Intune und Windows Autopilot
Sie können in Azure AD Hybrid eingebundene Geräte mithilfe von Intune und Windows Autopilot einrichten. Führen Sie dazu die Schritte in diesen Artikel durch.

## <a name="prerequisites"></a>Voraussetzungen

Konfigurieren Sie Ihre [Azure AD Hybrid-Geräte](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan). Stellen Sie sicher, dass Sie [die Geräteregistrierung mithilfe des Cmdlets „Get-MsolDevice“ überprüfen](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration).

Für die Registrierung müssen die Geräte über Folgendes verfügen:
- Windows 10, Version 1809 oder höher, muss ausgeführt werden.
- Internetzugriff gemäß den [dokumentierten Netzwerkanforderungen für Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements#networking-requirements) muss vorhanden sein.
- Die Geräte müssen auf einen Active Directory-Domänencontroller zugreifen können, daher ist eine Verbindung mit dem Netzwerk der Organisation erforderlich (dort werden die DNS-Einträge für die AD-Domäne und den AD-Domänencontroller aufgelöst, und über dieses Netzwerk erfolgt die Kommunikation mit dem Domänencontroller zur Authentifizierung des Benutzers. VPN-Verbindungen werden derzeit nicht unterstützt).
- Die Fähigkeit, den Domänencontroller der Domäne zu pingen, der Sie beitreten möchten
- Bei Verwendung eines Proxys müssen WPAD-Proxyeinstellungen aktiviert und konfiguriert sein.
- Sie müssen eingerichtet worden sein.

## <a name="set-up-windows-10-automatic-enrollment"></a>Einrichten der automatischen Registrierung von Windows 10

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an, und klicken Sie im linken Bereich auf **Azure Active Directory**.

   ![Das Azure-Portal](./media/windows-autopilot-hybrid/auto-enroll-azure-main.png)

1. Wählen Sie **Mobilität (MDM und MAM)** aus.

   ![Der Azure Active Directory-Bereich](./media/windows-autopilot-hybrid/auto-enroll-mdm.png)

1. Wählen Sie **Microsoft Intune** aus.

   ![Der Bereich „Mobilität (MDM und MAM)“](./media/windows-autopilot-hybrid/auto-enroll-intune.png)

1. Stellen Sie sicher, dass die Benutzer, die in Azure AD eingebundene Geräte mit Intune und Windows bereitstellen, Mitglieder einer Gruppe aus dem **MDM-Benutzerbereich** sind.

   ![Der Bereich „Mobilität (MDM und MAM), Konfigurieren“](./media/windows-autopilot-hybrid/auto-enroll-scope.png)

1. Verwenden Sie die Standardwerte in den Feldern **URL zu den MDM-Nutzungsbedingungen**, **URL für MDM-Ermittlung** und **MDM Compliance-URL**, und klicken Sie dann auf **Speichern**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Erhöhen des Kontolimits für den Computer in der Organisationseinheit

Der Intune-Connector für Active Directory erstellt Computer mit Registrierung per Autopilot in der lokalen Active Directory-Domäne. Der Hostcomputer des Intune-Connectors muss über die Berechtigung verfügen, die Computerobjekte innerhalb der Domäne zu erstellen. 

In einigen Domänen werden Computern keine Berechtigungen zum Erstellen von Computern gewährt. Darüber hinaus verfügen Domänen über ein integriertes Limit (Standardeinstellung: 10), das für alle Benutzer und Computer gilt, denen keine Berechtigungen zum Erstellen von Computerobjekten gewährt wurden. Deshalb müssen die Berechtigungen Computern gewährt werden, die den Intune-Connector in der Organisationseinheit hosten, in der in Azure AD Hybrid eingebundene Geräte erstellt werden.

Die Organisationseinheit, der die Berechtigung zum Erstellen von Computern gewährt wird, muss mit Folgendem übereinstimmen:
- Mit der Organisationseinheit, die im Domänenbeitrittsprofil eingetragen ist
- Mit dem Domänennamen des Computers für Ihre Domäne, wenn kein Profil ausgewählt ist

1. Öffnen Sie **Active Directory-Benutzer und -Computer** („DSA.msc“).

1. Klicken Sie mit der rechten Maustaste auf die Organisationseinheit, mit der Sie Azure AD Hybrid-Computer erstellen möchten, und wählen Sie **Delegate Control...** (Objektverwaltung zuweisen...) aus.

    ![Menübefehl „Delegate Control...“ (Objektverwaltung zuweisen...)](./media/windows-autopilot-hybrid/delegate-control.png)

1. Wählen Sie im Assistenten zum Zuweisen der **Objektverwaltung** die Optionen **Weiter** > **Hinzufügen...**  > **Objekttypen** aus.

1. Aktivieren Sie im Bereich **Objekttypen** das Kontrollkästchen **Computer**, und klicken Sie dann auf **OK**.

    ![Bereich „Object Types“ (Objekttypen)](./media/windows-autopilot-hybrid/object-types-computers.png)

1. Geben Sie im Bereich zur Auswahl von **Benutzern, Computern oder Gruppen** im Feld **Geben Sie die zu verwenden Objektnamen ein** den Namen des Computers ein, auf dem der Connector installiert ist.

    ![Bereich „Select Users, Computers, or Groups“ (Benutzer, Computer oder Gruppen auswählen)](./media/windows-autopilot-hybrid/enter-object-names.png)

1. Klicken Sie auf **Check Names** (Namen überprüfen), um Ihren Eintrag zu prüfen, klicken Sie auf **OK** und dann auf **Next** (Weiter).

1. Wählen Sie **Create a custom task to delegate** > **Next** (Benutzerdefinierte Aufgaben zum Zuweisen erstellen > Weiter) aus.

1. Aktivieren Sie das Kontrollkästchen **Only the following objects in the folder** (Nur die folgenden Objekte im Ordner) und anschließen die Kontrollkästchen **Computer objects** (Computerobjekte), **Delete selected objects in this folder** (Gewählte Objekte in diesem Ordner löschen) und **Create selected objects in this folder** (Gewählte Objekte in diesem Ordner erstellen).

    ![Bereich „Active Directory Object Type“ (Active Directory-Objekttyp)](./media/windows-autopilot-hybrid/only-following-objects.png)
    
1. Wählen Sie **Weiter** aus.

1. Aktivieren Sie unter **Permissions** (Berechtigungen) das Kontrollkästchen **Full Control** (Vollzugriff).  
    Durch diese Auswahl werden auch alle anderen Optionen aktiviert.

    ![Bereich „Permissions“ (Berechtigungen)](./media/windows-autopilot-hybrid/full-control.png)

1. Klicken Sie auf **Next** (Weiter) und dann auf **Finish** (Fertig stellen).

## <a name="install-the-intune-connector"></a>Installieren des Intune-Connectors

Der Intune-Connector für Azure AD muss auf einem Computer mit Windows Server 2016 oder höher installiert werden. Der Computer muss zudem über Internetzugriff und eine Active Directory-Instanz verfügen. Für höhere Skalierbarkeit und Verfügbarkeit oder Unterstützung mehrerer Active Directory-Domänen können Sie mehrere Connectors in der Umgebung installieren. Es wird empfohlen, den Connector auf einem Server zu installieren, auf dem keine anderen Intune-Connectors ausgeführt werden.

1. Klicken Sie unter [Intune](https://aka.ms/intuneportal) auf **Geräteregistrierung** > **Windows-Registrierung** > **Intune-Connector für Active Directory** > **Hinzufügen**. 
2. Folgen Sie den Anweisungen, um den Connector herunterzuladen.
3. Öffnen Sie die heruntergeladene Connectorsetupdatei (*ODJConnectorBootstrapper.exe*), um den Connector zu installieren.
4. Klicken Sie am Ende des Setups auf **Konfigurieren**.
5. Klicken Sie auf **Sign In** (Anmelden).
6. Geben Sie die Anmeldedaten für die Rolle „Globaler Administrator“ oder „Intune-Administrator“ ein.  
   Dem Benutzerkonto muss eine Intune-Lizenz zugewiesen werden.
7. Navigieren Sie zu **Geräteregistrierung** > **Windows-Registrierung** > **Intune-Connector für Active Directory**, und stellen Sie sicher, dass der Verbindungsstatus **Aktiv** lautet.

> [!NOTE]
> Nach der Anmeldung im Connector dauert es möglicherweise einige Minuten, bis er in [Intune](https://aka.ms/intuneportal) angezeigt wird. Er wird nur angezeigt, wenn er mit Intune kommunizieren kann.

### <a name="turn-off-ie-enhanced-security-configuration"></a>Deaktivieren der verstärkten Sicherheitskonfiguration für IE
Bei Windows Server ist die verstärkte Sicherheitskonfiguration für Internet Explorer standardmäßig aktiviert. Wenn Sie sich beim Intune-Connector für Active Directory nicht anmelden können, deaktivieren Sie die verstärkte Sicherheitskonfiguration für IE für den Administrator. [Deaktivieren der verstärkten Sicherheitskonfiguration für Internet Explorer](https://blogs.technet.microsoft.com/chenley/2011/03/10/how-to-turn-off-internet-explorer-enhanced-security-configuration)

### <a name="configure-web-proxy-settings"></a>Konfigurieren von Webproxyeinstellungen

Wenn ein Webproxy in der Netzwerkumgebung vorhanden ist, stellen Sie sicher, dass der Intune-Connector für Active Directory ordnungsgemäß funktioniert. Informationen finden Sie unter [Verwenden von vorhandenen lokalen Proxyservern](autopilot-hybrid-connector-proxy.md).


## <a name="create-a-device-group"></a>Erstellen einer Gerätegruppe
1. Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Gruppen** > **Neue Gruppe**.

1. Führen Sie im Bereich **Gruppe** folgende Aktionen aus:

    ein. Wählen Sie unter **Gruppentyp** die Option **Sicherheit** aus.

    b. Geben Sie einen **Gruppennamen** und eine **Gruppenbeschreibung** ein.

    c. Wählen Sie einen **Mitgliedschaftstyp** aus.

1. Wenn Sie oben **Dynamische Geräte** als Mitgliedschaftstyp ausgewählt haben,wählen Sie anschließend im Bereich **Gruppe** die Option **Dynamische Gerätemitglieder** aus, und geben Sie einen der folgenden Codes in das Feld **Erweiterte Regel** ein:
    - Wenn Sie eine Gruppe mit all Ihren Autopilot-Geräten erstellen möchten, geben Sie `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")` ein.
    - Das Intune-Feld „Gruppentag“ wird dem Attribut „OrderID“ auf Azure AD-Geräten zugeordnet. Wenn Sie eine Gruppe erstellen möchten, die all Ihre Autopilot-Geräte mit einem bestimmten Gruppentag („OrderID“) enthält, müssen Sie Folgendes eingeben: `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Wenn Sie eine Gruppe mit all Ihren Autopilot-Geräten mit einer bestimmten Bestellungs-ID erstellen möchten, geben Sie `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")` ein.
    
1. Wählen Sie **Speichern** aus.

1. Wählen Sie **Erstellen** aus.  

## <a name="register-your-autopilot-devices"></a>Registrieren der Autopilot-Geräte

Wählen Sie eine der folgenden Möglichkeiten, um Ihre Autopilot-Geräte zu registrieren.

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Registrieren von bereits angemeldeten Autopilot-Geräten

1. Erstellen Sie ein Autopilot-Bereitstellungsprofil, in dem **Alle als Ziel angegebenen Geräte in Autopilot konvertieren** auf **Ja** festgelegt ist. 
2. Ordnen Sie das Profil einer Gruppe zu, die die Mitglieder enthält, die Sie automatisch bei Autopilot registrieren möchten.

Weitere Informationen finden Sie unter [Erstellen eines Autopilot-Bereitstellungsprofils](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Registrieren von noch nicht angemeldeten Autopilot-Geräten

Wenn Ihre Geräte noch nicht registriert sind, können Sie sie selbst registrieren. Weitere Informationen finden Sie unter [Hinzufügen von Geräten](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Registrieren von Geräten eines OEMs

Beim Kauf neuer Geräte können einige OEMs die Geräte für Sie registrieren. Weitere Informationen finden Sie auf der Seite [Windows Autopilot](https://aka.ms/WindowsAutopilot).

Wenn Autopilot-Geräte *registriert* werden (bevor sie in Intune registriert werden), werden sie an drei Stellen (mit Namen, die auf ihre Seriennummern festgelegt sind) angezeigt:
- Im Bereich **Autopilot-Geräte** unter Intune im Azure-Portal. Klicken Sie auf **Geräteregistrierung** > **Windows-Registrierung** > **Geräte**.
- Im Bereich **Azure AD-Geräte** unter Intune im Azure-Portal. Klicken Sie auf **Geräte** > **Azure AD-Geräte**.
- Der Bereich **Alle Geräte** unter Azure Active Directory im Azure-Portal (**Geräte** > **Alle Geräte**).

Nachdem Ihre Autopilot-Geräte *registriert* wurden, werden sie an vier Stellen angezeigt:
- Im Bereich **Autopilot-Geräte** unter Intune im Azure-Portal. Klicken Sie auf **Geräteregistrierung** > **Windows-Registrierung** > **Geräte**.
- Im Bereich **Azure AD-Geräte** unter Intune im Azure-Portal. Klicken Sie auf **Geräte** > **Azure AD-Geräte**.
- Im Bereich **Alle Geräte** unter Azure Active Directory im Azure-Portal. Klicken Sie auf **Geräte** > **Alle Geräte**.
- Im Bereich **Alle Geräte** unter Intune im Azure-Portal. Klicken Sie auf **Geräte** > **Alle Geräte**.

Nachdem Ihre Autopilot-Geräte registriert wurden, werden die Gerätenamen in den Hostnamen des Geräts geändert. Standardmäßig beginnt der Hostname mit *DESKTOP-* .


## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Erstellen und Zuweisen eines Autopilot-Bereitstellungsprofils
Autopilot-Bereitstellungsprofile werden verwendet, um die Autopilot-Geräte zu konfigurieren.

1. Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Geräteregistrierung** > **Windows-Registrierung** > **Bereitstellungsprofile** > **Profil erstellen**.
2. Geben Sie auf der Seite **Grundlagen** einen Wert in **Name** und eine optionale **Beschreibung** ein.
3. Wenn Sie möchten, dass alle Geräte in den zugewiesenen Gruppen automatisch in Autopilot konvertiert werden, legen Sie für **Alle Zielgeräte in Autopilot-Geräte konvertieren** den Wert **Ja** fest. Alle unternehmenseigenen, Nicht-Autopilot-Geräte in zugewiesenen Gruppen werden mit dem Autopilot-Bereitstellungsdienst registriert. Private Geräte werden nicht in Autopilot konvertiert. Die Verarbeitung der Registrierung kann 48 Stunden dauern. Wenn die Registrierung des Geräts aufgehoben und es zurückgesetzt ist, registriert Autopilot es. Nachdem ein Gerät auf diese Weise registriert wurde, wird das Gerät durch Deaktivieren dieser Option oder Entfernen der Profilzuordnung nicht aus dem Autopilot-Bereitstellungsdienst entfernt. Sie müssen stattdessen [das Gerät direkt entfernen](enrollment-autopilot.md#delete-autopilot-devices).
4. Wählen Sie **Weiter** aus.
5. Wählen Sie auf der Seite **Windows-Willkommensseite** als **Bereitstellungsmodus** die Option **Benutzergesteuert** aus.
6. Wählen Sie im Feld **Azure AD beitreten als** die Option **In Azure AD Hybrid eingebunden** aus.
7. Konfigurieren Sie die restlichen Optionen auf der Seite **Windows-Willkommensseite** nach Bedarf.
8. Wählen Sie **Weiter** aus.
9. Wählen Sie auf der Seite **Bereichstags** die [Bereichstags](../fundamentals/scope-tags.md) für dieses Profil aus.
10. Wählen Sie **Weiter** aus.
11. Wählen Sie auf der Seite **Zuweisungen** die Option **Einzuschließende Gruppen auswählen** aus, suchen Sie nach der Gerätegruppe, und wählen Sie sie durch Klicken auf **Auswählen** aus.
12. Wählen Sie **Weiter** > **Erstellen** aus.

Es dauert etwa 15 Minuten, bis sich der Status des Geräteprofils von *Nicht zugewiesen* in *Wird zugewiesen* und schließlich in *Zugewiesen* ändert.

## <a name="optional-turn-on-the-enrollment-status-page"></a>Aktivieren der Registrierungsstatusseite (optional)

1. Wählen Sie in [Intune](https://aka.ms/intuneportal) **Geräteregistrierung** > **Windows-Registrierung** > **Seite zum Registrierungsstatus** aus.
1. Klicken Sie im Bereich **Seite zum Registrierungsstatus** auf **Standard** > **Einstellungen**.
1. Legen Sie für **Installationsfortschritt für Apps und Profile anzeigen** **Yes** (Ja) fest.
1. Konfigurieren Sie die anderen Optionen je nach Bedarf.
1. Wählen Sie **Speichern** aus.

## <a name="create-and-assign-a-domain-join-profile"></a>Erstellen und Zuweisen eines Domänenbeitrittsprofils

1. Wählen Sie in [Intune](https://aka.ms/intuneportal) **Gerätekonfiguration** > **Profile** > **Profil erstellen** aus.
1. Geben Sie die folgenden Eigenschaften ein:
   - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
   - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein.
   - **Plattform**: Wählen Sie **Windows 10 und höher** aus.
   - **Profiltyp**: Wählen Sie **Domänenbeitritt (Vorschau)** aus.
1. Wählen Sie **Einstellungen** aus, und geben Sie anschließend ein **Computernamenspräfix**, einen **Domänennamen** und optional eine **Organisationseinheit** im [DN-Format](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name) ein. 
   > [!NOTE]
   > Verwenden Sie keine Anführungszeichen um den Wert in **Organisationseinheit**.
1. Klicken Sie auf **OK** > **Erstellen**.  
    Das Profil wird erstellt und in der Liste angezeigt.
1. Um das Profil zuzuweisen, führen Sie die Schritte unter [Zuweisen eines Geräteprofils](../configuration/device-profile-assign.md#assign-a-device-profile) aus, und weisen Sie das Profil derselben Gruppe zu, die beim Schritt [Erstellen einer Gerätegruppe](windows-autopilot-hybrid.md#create-a-device-group) verwendet wurde.
   - Bereitstellen mehrerer Domänenbeitrittsprofile
   
     ein. Erstellen Sie eine dynamische Gruppe, die alle Ihre Autopilot-Geräte mit einem bestimmten Autopilot-Bereitstellungsprofil enthält. Geben Sie dazu „(device.enrollmentProfileName -eq ‚Autopilot-Profilname‘)“ ein. 
     
     b. Ersetzen Sie ‚Autopilot-Profilname‘ durch den Anzeigenamen des Profils, das Sie unter [Erstellen und Zuweisen eines Autopilot-Bereitstellungsprofils](windows-autopilot-hybrid.md#create-and-assign-an-autopilot-deployment-profile) erstellt haben. 
     
     c. Erstellen Sie mehrere Autopilot-Bereitstellungsprofile, und weisen Sie dieses Gerät dem Profil zu, das Sie in dieser dynamischen Gruppe angegeben haben.

> [!NOTE]
> Die Benennungsfunktionen für Windows Autopilot für Azure AD Hybrid Join unterstützen keine Variablen wie %SERIAL%. Sie unterstützen ausschließlich Präfixe für den Computernamen.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Windows Autopilot konfiguriert haben, erfahren Sie mehr über die Verwaltung dieser Geräte. Weitere Informationen finden Sie unter [Was ist die Microsoft Intune-Geräteverwaltung?](../remote-actions/device-management.md).
