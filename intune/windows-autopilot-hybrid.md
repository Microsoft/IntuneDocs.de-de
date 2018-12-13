---
title: Registrierung für in Active Directory Hybrid eingebundene Geräte – Windows Autopilot
titleSuffix: ''
description: Verwenden Sie Windows Autopilot, um in Active Directory Hybrid eingebundene Geräte in Microsoft Intune zu registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: ced67b2dcdd5720a9708868808ec885938b8ddcd
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112441"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-using-intune-and-windows-autopilot-preview"></a>Bereitstellen von in Azure AD Hybrid eingebundenen Geräten mit Intune und Windows Autopilot (Vorschauversion)
Sie können in Azure Active Directory Hybrid eingebundenen Geräte mithilfe von Intune und Windows Autopilot einrichten. Führen Sie dazu die folgenden Schritte aus.

> [!NOTE]
> Dieses Feature wird in den nächsten Tagen für Benutzer eingeführt. Daher können Sie diese Schritte möglicherweise erst ausführen, wenn es für Ihr Konto eingeführt wurde.

## <a name="prerequisites"></a>Voraussetzungen

- Erfolgreiche Konfiguration von [in Azure Active Directory Hybrid eingebundenen Geräten](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)
    - Stellen Sie sicher, dass Sie [die Registrierung mithilfe des Cmdlets „Get-MsolDevice“ überprüfen]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration).

Für die Registrierung müssen die Geräte über Folgendes verfügen:
- Windows 10 mit dem [Update von Oktober 2018](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/)
- Internetverbindung
- Zugriff auf die Active Directory-Instanz (VPN-Verbindung wird nicht unterstützt)
- Ausgeführte erste Schritte über die Willkommensseite

## <a name="set-up-windows-10-automatic-enrollment"></a>Einrichten der automatischen Registrierung von Windows 10

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an, und klicken Sie auf **Azure Active Directory**.

   ![Screenshot des Azure-Portals](./media/auto-enroll-azure-main.png)

2. Wählen Sie **Mobilität (MDM und MAM)** aus.

   ![Screenshot des Azure-Portals](./media/auto-enroll-mdm.png)

3. Wählen Sie **Microsoft Intune** aus.

   ![Screenshot des Azure-Portals](./media/auto-enroll-intune.png)

4. Stellen Sie sicher, dass die Benutzer, die in Azure Active Directory eingebundene Geräte mit Intune und Windows bereitstellen, Mitglieder einer Gruppe aus dem **MDM-Benutzerbereich** sind.

   ![Screenshot des Azure-Portals](./media/auto-enroll-scope.png)

5. Verwenden Sie die Standardwerte für die folgenden URLs:
    - **URL für MDM-Nutzungsbedingungen**
    - **URL für MDM-Ermittlung**
    - **MDM Compliance-URL**
6. Wählen Sie **Speichern** aus.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Erhöhen des Kontolimits für den Computer in der Organisationseinheit

Der Intune-Connector für Active Directory erstellt Computer mit Registrierung per Autopilot in der lokalen Active Directory-Domäne. Der Hostcomputer des Intune-Connectors muss über die Berechtigung verfügen, die Computerobjekte innerhalb der Domäne zu erstellen. 

In einigen Domänen werden Computern keine Berechtigungen zum Erstellen von Computern gewährt. Darüber hinaus verfügen Domänen über ein integriertes Limit (Standardeinstellung: 10), das für alle Benutzer und Computer gilt, an die keine Rechte zum Erstellen von Computerobjekten delegiert wurden. Deshalb müssen die Rechte an Computer delegiert werden, die den Intune-Connector in der Organisationseinheit hosten, in der in Azure AD Hybrid eingebundene Geräte erstellt werden.

Die Organisationseinheit, die die Berechtigung zum Erstellen von Computern erhalten hat, muss mit Folgendem übereinstimmen:
- Mit der Organisationseinheit, die im Profil „Domäne beitreten“ eingetragen ist.
- Oder, wenn kein Profil ausgewählt ist, mit dem Domänennamen des Computers für die Domäne.

1. Öffnen Sie **Active Directory-Benutzer und -Computer** (DSA.msc) aus.

2. Klicken Sie mit der rechten Maustaste auf die Organisationseinheit, mit der Sie die in Azure AD Hybrid eingebundenen Computer erstellen möchten, und wählen Sie **Objektverwaltung zuweisen** aus.

    ![Screenshot der Objektverwaltung](media/windows-autopilot-hybrid/delegate-control.png)

3. Wählen Sie im Assistenten zum Zuweisen der **Objektverwaltung** die Optionen **Weiter** > **Hinzufügen...** > **Objekttypen** aus.

4. Aktivieren Sie im Dialogfeld **Objekttypen** die Option **Computer**, und wählen Sie dann **OK** aus.

    ![Screenshot der Objektverwaltung](media/windows-autopilot-hybrid/object-types-computers.png)

5. Geben Sie im Dialogfeld zur **Auswahl von Benutzern, Computern oder Gruppen** im Feld **Geben Sie die zu verwenden Objektnamen ein** den Namen des Computers ein, auf dem der Connector installiert ist.

    ![Screenshot der Objektverwaltung](media/windows-autopilot-hybrid/enter-object-names.png)

6. Wählen Sie **Namen überprüfen** aus, um Ihre Eingabe zu überprüfen, und klicken Sie dann auf **OK** > **Weiter**.

7. Wählen Sie **Benutzerdefinierte Aufgaben zum Zuweisen erstellen** > **Weiter** aus.

8. Wählen Sie **Folgenden Objekten im Ordner** aus, und überprüfen Sie dann die folgenden Optionen:
    - **Computerobjekte**
    - **Gewählte Objekte in diesem Ordner erstellen**
    - **Gewählte Objekte in diesem Ordner löschen**

    ![Screenshot der Objektverwaltung](media/windows-autopilot-hybrid/only-following-objects.png)
    
9. Klicken Sie auf **Weiter**.

10. Aktivieren Sie unter **Berechtigungen** die Option **Vollzugriff** (dadurch werden alle anderen Optionen aktiviert), und wählen Sie dann **Weiter** > **Fertig stellen** aus.

    ![Screenshot der Objektverwaltung](media/windows-autopilot-hybrid/full-control.png)

## <a name="install-the-intune-connector"></a>Installieren des Intune-Connectors

Der Intune-Connector für Active Directory muss auf einem Computer mit Windows Server 2016 installiert sein, der Zugriff auf das Internet und die Active Directory-Instanz hat. Für höhere Skalierbarkeit und Verfügbarkeit oder Unterstützung mehrerer Active Directory-Domänen können Sie mehrere Connectors in der Umgebung installieren. Es wird empfohlen, den Connector auf einem Server zu installieren, auf dem keine anderen Intune-Connectors ausgeführt werden.

1. Stellen Sie sicher, dass Sie ein Language Pack installiert und konfiguriert haben, wie unter [Sprachanforderungen für den Intune-Connector (Vorschau)](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector) beschrieben wird.
2. Klicken Sie unter [Intune](https://aka.ms/intuneportal) auf **Geräteregistrierung** > **Windows-Registrierung** > **Intune-Connector für Active Directory (Vorschau)** > **Connector hinzufügen**. 
3. Folgen Sie den Anweisungen, um den Connector herunterzuladen.
4. Öffnen Sie die heruntergeladene Connector-Setupdatei (ODJConnectorBootstrapper.exe), um den Connector zu installieren.
5. Wählen Sie am Ende des Setups die Option **Konfigurieren** aus.
6. Wählen Sie **Anmelden** aus.
7. Geben Sie die Anmeldedaten für die Rolle „Globaler Administrator“ oder „Intune-Administrator“ ein.
8. Wechseln Sie zu **Geräteregistrierung** > **Windows-Registrierung** > **Intune-Connector für Active Directory (Vorschau)**, und bestätigen Sie, dass der Verbindungsstatus **Aktiv** ist.

### <a name="configure-web-proxy-settings"></a>Konfigurieren von Webproxyeinstellungen

Wenn ein Webproxy in der Netzwerkumgebung vorhanden ist, folgen Sie den hier dargelegten Anweisungen, damit der Intune-Connector für Active Directory ordnungsgemäß funktioniert: [Verwenden von vorhandenen lokalen Proxyservern](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers).


## <a name="create-a-device-group"></a>Erstellen einer Gerätegruppe
1. Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Gruppen** > **Neue Gruppe**.
2. Auf dem Blatt **Gruppe**:
    1. Wählen Sie für **Gruppentyp** die Option **Sicherheit**.
    2. Geben Sie einen **Gruppennamen** und eine **Gruppenbeschreibung** ein.
    3. Wählen Sie einen **Mitgliedschaftstyp** aus.
3. Wenn Sie oben **Dynamisches Geräte** als **Mitgliedschaftstyp** ausgewählt haben,wählen Sie anschließend auf dem Blatt **Gruppe** die Option **Dynamische Gerätemitglieder**, und geben Sie einen der folgenden Codes in das Feld **Erweiterte Regel** ein.
    - Wenn Sie eine Gruppe mit all Ihren Autopilot-Geräten erstellen möchten, geben Sie `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")` ein.
    - Wenn Sie eine Gruppe mit all Ihren Autopilot-Geräten mit einer bestimmten Bestell-ID erstellen möchten, geben Sie `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") ` ein.
    - Wenn Sie eine Gruppe mit all Ihren Autopilot-Geräten mit einer bestimmten Bestellungs-ID erstellen möchten, geben Sie `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")` ein.
    
    Wählen Sie nach dem Hinzufügen des Codes im Feld **Erweiterte Regel** die Option **Speichern**.
5. Wählen Sie **Erstellen** aus.  

## <a name="register-your-autopilot-devices"></a>Registrieren der Autopilot-Geräte

Wählen Sie eine der folgenden Möglichkeiten, um Ihre Autopilot-Geräte zu registrieren:

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Registrieren von bereits angemeldeten Autopilot-Geräten

1. Erstellen Sie ein Autopilot-Bereitstellungsprofil, in dem **Alle als Ziel angegebenen Geräte in Autopilot konvertieren** auf **Ja** festgelegt ist. 
2. Ordnen Sie das Profil einer Gruppe zu, die die Mitglieder enthält, die Sie automatisch mit Autopilot registrieren möchten.

Weitere Informationen finden Sie unter [Erstellen eines Autopilot-Bereitstellungsprofils](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Registrieren von noch nicht angemeldeten Autopilot-Geräten

Wenn Ihre Geräte noch nicht registriert sind, können Sie sie selbst registrieren. Weitere Informationen finden Sie unter [Hinzufügen von Geräten](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Registrieren von Geräten eines OEMs

Beim Kauf neuer Geräte können einige OEMs die Geräte für Sie registrieren. Weitere Informationen finden Sie auf der Seite [Windows Autopilot](http://aka.ms/WindowsAutopilot).

Wenn Autopilot-Geräte registriert sind (und bevor sie in Intune registriert werden), werden sie an drei Stellen (mit Namen, die auf ihre Seriennummern festgelegt sind) angezeigt:
- Autopilot-Blatt „Geräte“ in Intune im Azure-Portal (**Geräteregistrierung** > **Windows-Registrierung** > **Geräte**)
- Blatt „Azure AD-Geräte“ in Intune im Azure-Portal (**Geräte** > **Azure AD-Geräte**)
- AAD-Blatt „Alle Geräte“ in Azure Active Directory im Azure-Portal (**Geräte** > **Alle Geräte**)

Nachdem die Autopilot-Geräte registriert sind, sehen Sie diese an vier Stellen:
- Autopilot-Blatt „Geräte“ in Intune im Azure-Portal (**Geräteregistrierung** > **Windows-Registrierung** > **Geräte**)
- Blatt „Azure AD-Geräte“ in Intune im Azure-Portal (**Geräte** > **Azure AD-Geräte**)
- AAD-Blatt „Alle Geräte“ in Azure Active Directory im Azure-Portal (**Geräte** > **Alle Geräte**)
- Blatt „Alle Geräte“ in Intune im Azure-Portal (**Geräte** > **Alle Geräte**)

Nachdem Autopilot-Geräte registriert sind, werden die Gerätenamen in den Hostnamen des Geräts geändert. Dieser beginnt standardmäßig mit „DESKTOP-“.




## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Erstellen und Zuweisen eines Autopilot-Bereitstellungsprofils
Autopilot-Bereitstellungsprofile werden verwendet, um die Autopilot-Geräte zu konfigurieren.

1. Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Geräteregistrierung** > **Windows-Registrierung** > **Bereitstellungsprofile** > **Profil erstellen**.
2. Geben Sie einen **Namen** und optional eine **Beschreibung** ein.
3. Wählen Sie für **Bereitstellungsmodus** **Benutzergesteuert** aus.
4. Wählen Sie im Feld **Verknüpfen mit Azure AD als** die Option **In Azure AD Hybrid eingebunden (Vorschau)**.
5. Wählen Sie **Willkommensseite**, konfigurieren Sie die benötigten Optionen, und wählen Sie dann **Speichern** aus.
6. Wählen Sie **Erstellen** aus, um das Profil zu erstellen. 
7. Wählen Sie auf dem Profilblatt die Option **Zuweisungen** aus.
8. Wählen Sie **Gruppen auswählen** und dann im Blatt **Gruppen auswählen** die Gerätegruppe aus. Klicken Sie auf **Auswählen**.

Es dauert etwa 15 Minuten, bis sich der Status des Geräteprofils von **Nicht zugewiesen** in **Wird zugewiesen** und schließlich in **Zugewiesen** ändert.

## <a name="turn-on-the-enrollment-status-page-optional"></a>Aktivieren der Registrierungsstatusseite (optional)

1. Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Geräteregistrierung** > **Windows-Registrierung** > **Seite zum Registrierungsstatus (Vorschau)**.
2. Klicken Sie auf dem Blatt **Seite zum Registrierungsstatus** auf **Standard** > **Einstellungen**.
3. Klicken Sie für **Show app and profile installation progress** (Installationsfortschritt für die App und das Profil anzeigen) auf **Ja**.
4. Konfigurieren Sie die anderen Optionen je nach Bedarf.
5. Wählen Sie **Speichern** aus.

## <a name="create-and-assign-a-domain-join-profile"></a>Erstellen und Zuweisen eines Domänenbeitrittsprofils

1. Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
2. Geben Sie die folgenden Eigenschaften ein:
   - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
   - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein.
   - **Plattform**: Wählen Sie **Windows 10 und höher** aus.
   - **Profiltyp**: Wählen Sie **Domänenbeitritt (Vorschau)** aus.
3. Wählen Sie **Einstellungen** aus, und geben Sie ein **Computernamenspräfix**, einen **Domänennamen** und eine **Organisationseinheit** (optional) ein. 
4. Klicken Sie auf **OK** > **Erstellen**. Das Profil wird erstellt und in der Liste angezeigt.
5. Um das Profil zuzuweisen, führen Sie die Schritte unter [Zuweisen eines Geräteprofils](device-profile-assign.md#assign-a-device-profile) aus. 

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Windows Autopilot konfiguriert haben, erfahren Sie mehr über die Verwaltung dieser Geräte. Weitere Informationen finden Sie unter [Was ist die Microsoft Intune-Geräteverwaltung?](device-management.md).
