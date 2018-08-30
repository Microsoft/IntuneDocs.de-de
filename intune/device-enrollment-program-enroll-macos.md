---
title: Registrieren von macOS-Geräten – Programm zur Geräteregistrierung
titleSuffix: Microsoft Intune
description: Hier erfahren Sie, wie Sie unternehmenseigene macOS-Geräte mit dem Programm zur Geräteregistrierung (Device Enrollment Program, DEP) registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d6f9035b5a31d04e7d6ec6c5ec5b8f69a7c0943f
ms.sourcegitcommit: 0ac196d1d06f4f52f01610eb26060419d248168b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "40090135"
---
# <a name="automatically-enroll-macos-devices-with-apples-device-enrollment-program"></a>Automatisches Registrieren von macOS-Geräten mit dem Programm zur Geräteregistrierung von Apple

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Dieser Artikel unterstützt Sie dabei, die macOS-Geräteregistrierung für Geräte zu aktivieren, die über das [Device Enrollment Program](https://deploy.apple.com) (DEP, Programm zur Geräteregistrierung) von Apple erworben wurden. Sie können die Registrierung des Programms zur Geräteregistrierung für eine große Anzahl von Geräten einrichten, ohne diese physisch berühren zu müssen. Sie können macOS-Geräte direkt an Benutzer senden. Wenn ein Benutzer das Gerät einschaltet, wird der Setup-Assistent mit vordefinierten Einstellungen ausgeführt, und das Gerät wird bei der Intune-Verwaltung registriert.

Zum Einrichten der DEP-Registrierung können Sie sowohl das Intune-Portal als auch das Apple DEP-Portal verwenden. Sie erstellen DEP-Registrierungsprofile, die Einstellungen enthalten, die für Geräte während der Registrierung gelten.

Die Registrierung mit DEP funktioniert übrigens nicht mit dem [Geräteregistrierungs-Manager](device-enrollment-manager-enroll.md).

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Voraussetzungen
- Geräte, die unter dem [Programm zur Geräteregistrierung von Apple](http://deploy.apple.com) erworben werden.
- Eine Liste mit Seriennummern oder eine Auftragsnummer. 
- [MDM-Autorität](mdm-authority-set.md)
- [Apple-MDM-Push-Zertifikat](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Abrufen eines Apple-DEP-Tokens

Bevor Sie macOS-Geräte mit DEP registrieren können, benötigen Sie ein DEP-Token (P7M-Datei) von Apple. Mit diesem Token kann Intune Informationen zu DEP-Geräten synchronisieren, die Ihrem Unternehmen gehören. Zudem ermöglicht es Intune das Hochladen von Registrierungsprofilen bei Apple und das Zuweisen dieser Profile zu Geräten.

Verwenden Sie das Apple DEP-Portal, um ein DEP-Token zu erstellen. Sie verwenden das DEP-Portal auch, um in Intune Geräte für die Verwaltung zuzuweisen.

> [!NOTE]
> Wenn Sie das Token vor der Migration zu Azure aus dem klassischen Intune-Portal löschen, stellt Intune womöglich ein gelöschtes Apple DEP-Token wieder her. Sie können das DEP-Token erneut aus dem Azure-Portal löschen.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Schritt 1: Laden Sie das Intune-Zertifikat mit öffentlichem Schlüssel herunter, das zum Erstellen des Tokens erforderlich ist.

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Token für Registrierungsprogramm** > **Hinzufügen** aus.

    ![Rufen Sie ein Registrierungsprogrammtoken ab.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Erteilen Sie Microsoft die Berechtigung, Benutzer- und Geräteinformationen an Apple zu senden, indem Sie auf **Ich stimme zu** klicken.

   ![Screenshot des Bereichs „Registrierungsprogrammtoken“ im Arbeitsbereich „Apple-Zertifikate“ zum Herunterladen des öffentlichen Schlüssels](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Wählen Sie **Laden Sie Ihr Zertifikat mit öffentlichem Schlüssel herunter** aus, um die Verschlüsselungsschlüsseldatei (PEM) herunterzuladen und lokal zu speichern. Die PEM-Datei wird verwendet, um ein Vertrauensstellungszertifikat vom Apple Device Enrollment Program-Portal anzufordern.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Schritt 2. Verwenden Sie Ihren Schlüssel, um ein Token von Apple herunterzuladen.

1. Wählen Sie **Create a token for Apple's Device Enrollment Program** (Token für das Programm zur Geräteregistrierung von Apple erstellen) aus, um das Portal des Bereitstellungsprogramms von Apple zu öffnen. Melden Sie sich mit der Apple-ID Ihres Unternehmens an. Diese Apple-ID kann später zum Erneuern Ihres DEP-Token verwendet werden.
2.  Wählen Sie im [Portal des Bereitstellungsprogramms](https://deploy.apple.com) von Apple die Option **Erste Schritte** für das **Programm zur Geräteregistrierung** aus.

3. Wählen Sie auf der Seite **Server verwalten** die Option **MDM-Server hinzufügen** aus.
4. Geben Sie den **MDM-Servernamen** ein, und wählen Sie anschließend **Weiter** aus. Der Servername dient als Referenz zum Identifizieren des MDM-Servers (mobile device management, Verwaltung mobiler Geräte). Es handelt sich nicht um den Namen oder die URL des Microsoft Intune-Servers.

5. Das Dialogfeld **&lt;Servername&gt; hinzufügen** wird geöffnet, und die Meldung **Laden Sie Ihren öffentlichen Schlüssel hoch** wird angezeigt. Wählen Sie **Datei auswählen** aus, um die PEM-Datei hochzuladen, und wählen Sie anschließend **Weiter** aus.

6. Wechseln Sie zu **Bereitstellungsprogramme** &gt; **Programm zur Geräteregistrierung** &gt; **Geräte verwalten**.
7. Geben Sie unter **Geräte auswählen nach** an, wie die Geräte identifiziert werden sollen:
    - **Seriennummer**
    - **Reihenfolge**
    - **Upload der CSV-Datei**

   ![Screenshot bei Festlegen von „Geräte auswählen nach“ auf „Seriennummer“, der Einstellung „Aktion auswählen“ auf „Zu Server zuweisen“ und der Auswahl des Servernamens.](./media/enrollment-program-token-specify-serial.png)

8. Wählen Sie als Nächstes für **Aktion auswählen** die Option **Zu Server zuweisen** aus. Wählen Sie den für Microsoft Intune angegebenen &lt;Servernamen&gt; und anschließend **OK** aus. Das Apple-Portal weist die angegebenen Geräte dem Intune-Server für die Verwaltung zu und zeigt dann **Zuweisung abgeschlossen** an.

   Wechseln Sie im Apple-Portal zu **Bereitstellungsprogramme** &gt; **Programm zur Geräteregistrierung** &gt; **Zuweisungsverlauf anzeigen**, um eine Liste der Geräte und ihre MDM-Server-Zuordnung anzuzeigen.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Schritt 3: Speichern Sie die zum Erstellen dieses Tokens verwendete Apple-ID.

Geben Sie in Intune im Azure-Portal für die zukünftige Verwendung Ihre Apple-ID an.

![Screenshot der Angabe der Apple-ID zur Erstellung des Registrierungsprogrammtokens und Navigieren zu diesem Token](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Schritt 4: Laden Sie Ihr Token hoch.
Navigieren Sie im Feld **Apple-Token** zur Zertifikatsdatei (PEM), und wählen Sie **Öffnen** und dann **Erstellen** aus. Mit dem Pushzertifikat kann Intune macOS-Geräte registrieren und verwalten, indem die Richtlinie per Push auf registrierte Geräte übertragen wird. Intune führt eine automatische Synchronisierung mit Apple durch, um Ihr Registrierungsprogrammkonto anzuzeigen.

## <a name="create-an-apple-enrollment-profile"></a>Erstellen eines Apple-Registrierungsprofils

Da Sie nun Ihr Token installiert haben, können Sie ein Registrierungsprofil für DEP-Geräte erstellen. Ein Geräteregistrierungsprofil definiert die Einstellungen, die während der Registrierung auf eine Gruppe von Geräten angewendet werden.

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus.
2. Wählen Sie ein Token aus, und wählen Sie dann **Profile** und **Profil erstellen** aus.

    ![Screenshot der Erstellung eines Profils](./media/device-enrollment-program-enroll-ios/image04.png)

3. Geben Sie zu administrativen Zwecken unter **Profil erstellen** einen **Namen** und eine **Beschreibung** für das Profil ein. Benutzer können diese Informationen nicht sehen. Sie können das Feld **Name** zum Erstellen einer dynamischen Gruppe in Azure Active Directory verwenden. Verwenden Sie den Profilnamen, um den Parameter „enrollmentProfileName“ zu definieren, um Geräte mit diesem Registrierungsprofil zuzuweisen. Erfahren Sie mehr über [dynamische Gruppen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

    ![Profilname und Beschreibung](./media/device-enrollment-program-enroll-macos/createprofile.png)

4. Wählen Sie als **Plattform** die Option **macOS** aus.

5. Wählen Sie unter **Benutzeraffinität** aus, ob sich Geräte mit diesem Profil mit oder ohne einen zugewiesenen Benutzer registrieren müssen.
    - **Mit Benutzeraffinität registrieren**: Wählen Sie diese Option für Geräte aus, die Benutzern gehören und das Unternehmensportal verwenden sollen, um Dienste wie z.B. die Installation von Apps nutzen zu können. Bei ADFS ist für Benutzeraffinität [Endpunkt WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints) erforderlich. [Weitere Informationen](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint): Auf macOS-Geräten mit Benutzeraffinität, die über DEP registriert wurden, wird die mehrstufige Authentifizierung nicht unterstützt.

    - **Ohne Benutzeraffinität registrieren**: Wählen Sie diese Option für Geräte aus, die keinem einzelnen Benutzer zugeordnet sind. Verwenden Sie diese Option für Geräte, die Aufgaben ohne den Zugriff auf lokale Benutzerdaten ausführen. Apps wie die Unternehmensportal-App funktionieren nicht.

6. Wählen Sie **Geräteverwaltungseinstellungen** aus, und geben Sie an, ob für Geräte mit diesem Profil die gesperrte Registrierung verwendet werden soll. Die **gesperrte Registrierung** deaktiviert die macOS-Einstellungen, mit denen das Verwaltungsprofil aus dem Menü **Einstellungen** oder über das **Terminal** entfernt werden kann. Nach der Gerätebereitstellung können Sie diese Einstellung ändern, ohne das Gerät auf Werkseinstellung zurückzusetzen.

    ![Screenshot der Geräteverwaltungseinstellungen](./media/device-enrollment-program-enroll-macos/devicemanagementsettingsblade-macos.png)
 
7. Wählen Sie **OK** aus.

8. Wählen Sie **Einstellungen des Einrichtungs-Assistenten** aus, um die folgenden Profileinstellungen zu konfigurieren: ![Anpassung des Setup-Assistenten](./media/device-enrollment-program-enroll-macos/setupassistantcustom-macos.png)


    |                 Einstellung                  |                                                                                               Beschreibung                                                                                               |
    |------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |     <strong>Abteilungsname</strong>     |                                                             Wird angezeigt, wenn der Benutzer während der Aktivierung auf <strong>Info zur Konfiguration</strong> tippt.                                                              |
    |    <strong>Abteilungstelefonnummer</strong>     |                                                          Wird angezeigt, wenn der Benutzer während der Aktivierung auf die Schaltfläche <strong>Benötigen Sie Hilfe?</strong> klickt.                                                          |
    | <strong>Setup-Assistent-Optionen</strong> |                                                     Die folgenden optionalen Einstellungen können später im macOS-Menü <strong>Einstellungen</strong> eingerichtet werden.                                                      |
    |        <strong>Kennung</strong>         | Fordert während der Aktivierung zur Eingabe der Kennung auf. Fordern Sie immer eine Kennung an, es sei denn, das Gerät und der Zugriff darauf werden auf andere Weise geschützt (d.h. im Kioskmodus zum Einschränken des Geräts auf eine App). |
    |    <strong>Standortdienste</strong>    |                                                                 Falls aktiviert, fordert der Setup-Assistent während der Aktivierung zur Ausführung dieses Dienstes auf.                                                                  |
    |         <strong>Wiederherstellen</strong>         |                                                                Falls aktiviert, fordert der Setup-Assistent während der Aktivierung die iCloud-Sicherung an.                                                                 |
    |   <strong>iCloud und Apple-ID</strong>   |                         Falls aktiviert, fordert der Setup-Assistent den Benutzer auf, sich mit einer Apple-ID anzumelden, und im Bildschirm „Apps und Daten“ kann das Gerät von einer iCloud-Sicherung wiederhergestellt werden.                         |
    |  <strong>Geschäftsbedingungen</strong>   |                                                   Falls aktiviert, fordert der Setup-Assistenten während der Aktivierung den Benutzer auf, die Apple-Geschäftsbedingungen zu akzeptieren.                                                   |
    |        <strong>Touch ID</strong>         |                                                                 Falls aktiviert, fordert der Setup-Assistent während der Aktivierung zur Ausführung dieses Dienstes auf.                                                                 |
    |        <strong>Apple Pay</strong>        |                                                                 Falls aktiviert, fordert der Setup-Assistent während der Aktivierung zur Ausführung dieses Dienstes auf.                                                                 |
    |          <strong>Zoom</strong>           |                                                                 Falls aktiviert, fordert der Setup-Assistent während der Aktivierung zur Ausführung dieses Dienstes auf.                                                                 |
    |          <strong>Siri</strong>           |                                                                 Falls aktiviert, fordert der Setup-Assistent während der Aktivierung zur Ausführung dieses Dienstes auf.                                                                 |
    |     <strong>Diagnosedaten</strong>     |                                                                 Falls aktiviert, fordert der Setup-Assistent während der Aktivierung zur Ausführung dieses Dienstes auf.                                                                 |
    |     <strong>FileVault</strong>           |  |
    |     <strong>iCloud Diagnostics</strong>  |  |
    |     <strong>Registrierung</strong>        |  |


10. Wählen Sie **OK** aus.

11. Wählen Sie **Erstellen** aus, um das Profil zu speichern.

## <a name="sync-managed-devices"></a>Synchronisieren verwalteter Geräte
Nachdem Intune nun die Berechtigung zum Verwalten Ihrer Geräte besitzt, können Sie Intune mit Apple synchronisieren, um Ihre verwalteten Geräte in Intune im Azure-Portal anzuzeigen.

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus, wählen Sie in der Liste ein Token aus, und wählen Sie dann **Geräte** > **Synchronisieren** aus. ![Screenshot des ausgewählten Knotens „Geräte des Registrierungprogramms“ und des ausgewählten Links „Synchronisierung“](./media/device-enrollment-program-enroll-ios/image06.png)

   Zur Einhaltung der Apple-Bedingungen für zulässigen Datenverkehr des Registrierungsprogramms erzwingt Intune die folgenden Einschränkungen:
   - Eine vollständige Synchronisation kann nicht öfter als einmal alle sieben Tage erfolgen. Während einer vollständigen Synchronisierung ruft Intune die vollständig aktualisierte Liste der Seriennummern auf, die dem mit Intune verbundenen Apple MDM-Server zugewiesen sind. Nachdem ein Registrierungsprogrammgerät aus dem Intune-Portal gelöscht wurde, ohne dass es vom Apple MDM-Server im DEP-Portal entfernt wurde, wird es erst wieder in Intune importiert, wenn die vollständige Synchronisierung ausgeführt wurde.   
   - Die Synchronisierung wird automatisch alle 24 Stunden ausgeführt. Sie können eine Synchronisierung ebenfalls durchführen, indem Sie auf die Schaltfläche **Synchronisierung** klicken (nicht öfter als einmal alle 15 Minuten). Alle Synchronisierungsanforderungen müssen innerhalb von 15 Minuten abgeschlossen werden. Die Schaltfläche **Synchronisierung** bleibt bis zum Abschluss der Synchronisierung deaktiviert. Durch diese Synchronisierung werden vorhandene Gerätestatus aktualisiert und neue Geräte importiert, die dem Apple MDM-Server zugewiesen sind.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Zuweisen eines Registrierungsprofils an Geräte
Sie müssen Geräten ein Profil des Registrierungsprogramms zuweisen, bevor Sie mit der Registrierung beginnen können.

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus, und wählen Sie in der Liste ein Token aus.
2. Wählen Sie **Geräte** aus, wählen Sie in der Liste die Geräte aus, und wählen Sie dann **Profil zuweisen** aus.
3. Wählen Sie unter **Profil zuweisen** ein Profil für die Geräte aus, und wählen Sie dann **Zuweisen** aus.

### <a name="assign-a-default-profile"></a>Zuweisen eines Standardprofils

Sie können ein macOS- und iOS-Standardprofil auswählen, das auf alle Geräte angewendet wird, die sich mit einem bestimmten Token registrieren. 

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus, und wählen Sie in der Liste ein Token aus.
2. Wählen Sie **Standardprofil festlegen** aus, wählen Sie ein Profil in der Dropdownliste aus, und wählen Sie dann **Speichern** aus. Dieses Profil wird auf alle Geräte angewendet, die sich mit dem Token registrieren.

## <a name="distribute-devices"></a>Verteilen von Geräten
Sie haben die Verwaltung und Synchronisierung zwischen Apple und Intune aktiviert und haben ein Profil zugewiesen, damit Ihre DEP-Geräte registriert werden können. Sie können jetzt Geräte an Benutzer verteilen. Für Geräte mit Benutzeraffinität muss jedem Benutzer eine Intune-Lizenz zugewiesen werden. Geräte ohne Benutzeraffinität benötigen eine Gerätelizenz. Ein aktiviertes Gerät kann kein Registrierungsprofil anwenden, bis das Gerät nicht auf Werkseinstellung zurückgesetzt wurde.

## <a name="renew-a-dep-token"></a>Erneuern eines DEP-Tokens  
1. Wechseln Sie zu deploy.apple.com.  
2. Wählen Sie unter **Server verwalten** Ihren MDM-Server aus, der der Tokendatei zugeordnet ist, die Sie erneuern möchten.
3. Klicken Sie auf **Neues Token generieren**.

    ![Screenshot von „Neues Token generieren“](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. Klicken Sie auf **Ihr Servertoken**.  
5. Klicken Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) auf **Geräteregistrierung** > **Apple-Registrierung** > **Token für Registrierungsprogramm**, und wählen Sie anschließend das Token aus.
    ![Screenshot der Registrierungsprogrammtoken.](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. Wählen Sie **Token erneuern** aus, und geben Sie die Apple-ID ein, die zum Erstellen des ursprünglichen Tokens verwendet wurde.  
    ![Screenshot von „Token erneuern“](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. Laden Sie das neu heruntergeladene Token hoch.  
9. Klicken Sie auf **Token erneuern**. Es wird eine Bestätigung angezeigt, dass das Token erneuert wurde.   
    ![Screenshot der Bestätigung](./media/device-enrollment-program-enroll-ios/confirmation.png)

## <a name="next-steps"></a>Nächste Schritte

Nach der Registrierung der macOS-Geräte können Sie mit der [Verwaltung](device-management.md) beginnen.