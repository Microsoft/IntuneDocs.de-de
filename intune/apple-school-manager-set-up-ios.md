---
title: Apple School Manager-Programm zur Registrierung von iOS-Geräten
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie das Apple School Manager-Programm für die Registrierung von unternehmenseigenen iOS-Geräten bei Intune einrichten.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4c35a23e-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: fdda0edd8c7bf67dbfce9d428f1b3ce0266b3726
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032417"
---
# <a name="set-up-ios-device-enrollment-with-apple-school-manager"></a>Einrichten der iOS-Geräteregistrierung mit Apple School Manager

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Sie können Intune für die Registrierung von iOS-Geräten einrichten, die über das [Apple School Manager](https://school.apple.com/)-Programm erworben wurden. Wenn Sie Intune mit Apple School Manager verwenden, können Sie eine große Zahl von iOS-Geräten registrieren, ohne diese in den Händen zu halten. Wenn ein Schüler oder ein Lehrer das Gerät anschaltet, wird der Setup-Assistent mit vordefinierten Einstellungen ausgeführt, und das Gerät wird für die Verwaltung registriert.

Um die Registrierung mit Apple School Manager möglich zu machen, müssen Sie die Portale von Intune und Apple School Manager verwenden. Sie benötigen auch eine Liste von Seriennummern oder eine Bestellnummer, um Geräte in Intune zur Verwaltung zuweisen zu können. Sie erstellen DEP-Registrierungsprofile, die Einstellungen enthalten, die für Geräte während der Registrierung gelten.

Die Registrierung von Apple School Manager kann nicht mit dem [Programm zur Geräteregistrierung von Apple](device-enrollment-program-enroll-ios.md) oder dem [Geräteregistrierungs-Manager](device-enrollment-manager-enroll.md) verwendet werden.

**Voraussetzungen**
- [Apple-MDM-Push-Zertifikat](apple-mdm-push-certificate-get.md)
- [MDM-Autorität](mdm-authority-set.md)
- [Apple-MDM-Push-Zertifikat](apple-mdm-push-certificate-get.md)
- Bei ADFS ist für Benutzeraffinität [Endpunkt WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints) erforderlich. [Erfahren Sie mehr](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
- Geräte, die über das Programm [Apple School Management](http://school.apple.com) erworben wurden

## <a name="get-an-apple-token-and-assign-devices"></a>Abrufen eines Apple-Tokens und Zuweisen von Geräten

Bevor Sie unternehmenseigene iOS-Geräte mit dem Apple School Manager registrieren können, benötigen Sie ein Token (P7M-Datei) von Apple. Mit diesem Token kann Intune Informationen zu Geräten synchronisieren, die zum Apple School Manager-Programm gehören. Damit kann Intune außerdem Registrierungsprofile an Apple übermitteln und diesen Profilen Geräte zuweisen. Im Apple-Portal können Sie auch Geräteseriennummern für die Verwaltung zuweisen.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-an-apple-token"></a>Schritt 1: Herunterladen des Intune-Zertifikats mit öffentlichem Schlüssel, das zum Erstellen eines Apple-Tokens erforderlich ist

1. Wählen Sie in [Intune](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** > **Hinzufügen** aus.

   ![Rufen Sie ein Registrierungsprogrammtoken ab.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Wählen Sie auf dem Blatt **Registrierungsprogrammtoken** die Option **Laden Sie Ihr Zertifikat mit öffentlichem Schlüssel herunter** aus, um die Verschlüsselungsschlüsseldatei (PEM) herunterzuladen und lokal zu speichern. Die PEM-Datei wird verwendet, um ein Vertrauensstellungszertifikat vom Apple School Manager-Portal anzufordern.
     ![Blatt „Registrierungsprogrammtoken“](./media/device-enrollment-program-enroll-ios/image02.png)

### <a name="step-2-download-a-token-and-assign-devices"></a>Schritt 2. Herunterladen eines Tokens und Zuweisen von Geräten
1. Wählen Sie **Token über Apple School Manager erstellen** aus, und melden Sie sich mit Ihrer Apple-Unternehmens-ID bei Apple School an. Sie können diese Apple-ID auch zum Erneuern Ihres Apple School Manager-Tokens verwenden.
2.  Wechseln Sie im [Apple School Manager-Portal](https://school.apple.com) zu **MDM-Server**, und klicken Sie auf **MDM-Server hinzufügen** (oben rechts).
3.  Geben Sie den **MDM-Servernamen** ein. Der Servername dient als Referenz zum Identifizieren des MDM-Servers (mobile device management, Verwaltung mobiler Geräte). Es handelt sich nicht um den Namen oder die URL des Microsoft Intune-Servers.
   ![Screenshot des Apple School Manager-Portals mit der ausgewählter Option „Seriennummer“](./media/asm-server-assignment.png)

4.  Wählen Sie im Apple-Portal die Option **Datei hochladen...**, navigieren Sie zur PEM-Datei, und wählen Sie **MDM-Server speichern** (unten rechts).
5.  Klicken Sie auf **Token abrufen**, und laden Sie die Servertokendatei (P7M) auf Ihren Computer herunter.
6. Wechseln Sie zu **Gerätezuweisungen**, und verwenden Sie die Option **Gerät auswählen**, indem Sie **Seriennummern** oder **Bestellnummer** manuell eingeben oder eine **CSV-Datei hochladen**.
     ![Screenshot des Apple School Manager-Portals mit der ausgewählter Option „Seriennummer“](./media/asm-device-assignment.png)
7.  Wählen Sie die Aktion **Zu Server zuweisen**, und wählen Sie den von Ihnen erstellten **MDM-Server** aus.
8. Geben Sie an Sie **Geräte ausgewählt werden**, und stellen Sie dann Geräteinformationen sowie Details bereit.
9. Wählen Sie **Zu Server zuweisen** aus. Wählen Sie den für Microsoft Intune angegebenen &lt;Servernamen&gt; und anschließend **OK** aus.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Schritt 3: Speichern der zum Erstellen dieses Tokens verwendeten Apple-ID

Geben Sie in Intune im Azure-Portal für die zukünftige Verwendung Ihre Apple-ID an.

![Screenshot der Angabe der Apple-ID zur Erstellung des Registrierungsprogrammtokens und Navigieren zu diesem Token](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Schritt 4: Hochladen des Tokens
Navigieren Sie im Feld **Apple-Token** zur Zertifikatsdatei (PEM), und wählen Sie **Öffnen** und dann **Erstellen** aus. Mit dem Push-Zertifikat kann Intune iOS-Geräte registrieren und verwalten, indem die Richtlinie auf registrierte mobile Geräte übertragen wird. Intune synchronisiert Ihre Apple School Manager-Geräte automatisch mit Apple.

## <a name="create-an-apple-enrollment-profile"></a>Erstellen eines Apple-Registrierungsprofils
Da Sie nun Ihr Token installiert haben, können Sie ein Registrierungsprofil für Apple School-Geräte erstellen. Ein Geräteregistrierungsprofil definiert die Einstellungen, die während der Registrierung auf eine Gruppe von Geräten angewendet werden.

1. Wählen Sie in [Intune](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus.
2. Wählen Sie ein Token aus, und wählen Sie dann **Profile** und **Profil erstellen** aus.

3. Geben Sie zu administrativen Zwecken unter **Profil erstellen** einen **Namen** und eine **Beschreibung** für das Profil ein. Benutzer können diese Informationen nicht sehen. Sie können das Feld **Name** zum Erstellen einer dynamischen Gruppe in Azure Active Directory verwenden. Verwenden Sie den Profilnamen, um den Parameter „enrollmentProfileName“ zu definieren, um Geräte mit diesem Registrierungsprofil zuzuweisen. Erfahren Sie mehr über [dynamische Gruppen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

    ![Profilname und Beschreibung](./media/device-enrollment-program-enroll-ios/image05.png)

4. Wählen Sie unter **Benutzeraffinität** aus, ob sich Geräte mit diesem Profil mit oder ohne einen zugewiesenen Benutzer registrieren müssen.
    - **Mit Benutzeraffinität registrieren**: Wählen Sie diese Option für Geräte aus, die Benutzern gehören und das Unternehmensportal verwenden sollen, um Dienste wie z. B. die Installation von Apps nutzen zu können. Mit dieser Option können Benutzer ihre Geräte auch über das Unternehmensportal authentifizieren. Bei ADFS ist für Benutzeraffinität [Endpunkt WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints) erforderlich. [Erfahren Sie mehr](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).   Der Apple School Manager-Modus „Gemeinsam genutztes iPad“ erfordert, dass Benutzer sich ohne Affinität zwischen Benutzer und Gerät registrieren.

    - **Ohne Benutzeraffinität registrieren**: Wählen Sie diese Option für Geräte aus, die keinem einzelnen Benutzer zugeordnet sind, z. B. ein gemeinsam genutztes Gerät. Verwenden Sie diese Option für Geräte, die Aufgaben ohne Zugriff auf lokale Benutzerdaten ausführen. Apps wie die Unternehmensportal-App funktionieren nicht.

5. Wenn Sie **Mit Benutzeraffinität registrieren** ausgewählt haben, können Sie die Benutzerauthentifizierung über das Unternehmensportal statt über den Apple-Setup-Assistenten erlauben.

    ![Authentifizieren über das Unternehmensportal](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Wenn Sie einen der folgenden Schritte ausführen möchten, legen Sie **Über das Unternehmensportal statt über den Setup-Assistenten authentifizieren** auf **Ja** fest.
    >    - Sie möchten die mehrstufige Authentifizierung verwenden.
    >    - Sie möchten Benutzer zum Ändern ihres Kennworts auffordern, wenn sie sich zum ersten Mal anmelden.
    >    - Sie möchten Benutzer dazu auffordern, ihre abgelaufenen Kennwörter bei der Registrierung zurückzusetzen.
    >
    > Diese Optionen werden für die Authentifizierung beim Setup-Assistenten von Apple nicht unterstützt.

6. Wählen Sie **Geräteverwaltungseinstellungen** aus, und geben Sie an, ob Geräte mit diesem Profil überwacht werden sollen.
    Bei **überwachten** Geräten stehen mehr Verwaltungsfunktionen zur Verfügung, und die Aktivierungssperre ist standardmäßig deaktiviert. Es wird von Microsoft empfohlen, DEP als Mechanismus zur Aktivierung des überwachten Modus zu verwenden. Dies gilt insbesondere für Organisationen, die eine große Anzahl von iOS-Geräten bereitstellen.

    Die Benutzer werden auf zweierlei Weise benachrichtigt, dass ihre Geräte überwacht werden:

   - Auf dem Sperrbildschirm wird Folgendes angezeigt: „This iPhone is managed by Contoso“ (Dieses iPhone wird von Contoso verwaltet).
   - Auf dem Bildschirm **Settings** > **General** > **About** (Einstellungen > Allgemein > Info) wird Folgendes angezeigt: „This iPhone is supervised. Contoso can monitor your Internet traffic and locate this device.“ (Dieses iPhone wird überwacht. Contoso kann Ihren Internetdatenverkehr überwachen und dieses Gerät orten.)

     > [!NOTE]
     > Ein Gerät, das ohne Überwachung registriert wurde, kann nur mithilfe von Apple Configurator auf den Status „Überwacht“ zurückgesetzt werden. Wenn Sie das Gerät auf diese Weise zurücksetzen möchten, müssen Sie ein iOS-Gerät über ein USB-Kabel mit einem Mac verbinden. Erfahren Sie mehr über dieses Thema in der [Dokumentation zu Apple Configurator](http://help.apple.com/configurator/mac/2.3).

7. Wählen Sie aus, ob für Geräte mit diesem Profil die gesperrte Registrierung verwendet werden soll. Wenn **Gesperrte Registrierung** aktiviert ist, sind die iOS-Einstellungen deaktiviert, mit denen das Verwaltungsprofil aus dem Menü **Einstellungen** entfernt werden kann. Nach der Geräteregistrierung können Sie diese Einstellung ändern, ohne das Gerät zurückzusetzen. Bei solchen Geräten muss der Verwaltungsmodus **Überwacht** auf *Ja* eingestellt sein. 

8. Wenn Sie möchten, dass sich mehrere Benutzer mit einer verwalteten Apple-ID auf den registrierten iPads anmelden, wählen Sie unter **Gemeinsam genutztes iPad** **Ja** aus. Für diese Option müssen **Ohne Benutzeraffinität registrieren** und der Modus **Überwacht** auf **Ja** eingestellt sein. Verwaltete Apple-IDs werden im Apple School Manager-Portal erstellt. Weitere Informationen zu [gemeinsam genutzten iPads](education-settings-configure-ios-shared.md) finden Sie in den [entsprechenden Apple-Anforderungen](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56).

9. Wählen Sie aus, ob für Geräte mit diesem Profil die Option **Mit Computern synchronisieren** verwendet werden soll. Wenn Sie **Apple Configurator nach Zertifikat zulassen** auswählen, müssen Sie unter **Apple Configurator-Zertifikate** ein Zertifikat auswählen.

10. Wenn Sie im vorherigen Schritt **Apple Configurator nach Zertifikat zulassen** ausgewählt haben, müssen Sie ein Apple Configurator-Zertifikat zum Importieren auswählen.

11. Wählen Sie **OK** aus.

12. Wählen Sie **Einstellungen des Einrichtungs-Assistenten** aus, um die folgenden Profileinstellungen zu konfigurieren: ![Anpassung des Setup-Assistenten](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    |                 Einstellung                  |                                                                                               Beschreibung                                                                                               |
    |------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |     <strong>Abteilungsname</strong>     |                                                             Wird angezeigt, wenn der Benutzer während der Aktivierung auf <strong>Info zur Konfiguration</strong> tippt.                                                              |
    |    <strong>Abteilungstelefonnummer</strong>     |                                                          Wird angezeigt, wenn der Benutzer während der Aktivierung auf die Schaltfläche <strong>Benötigen Sie Hilfe?</strong> klickt.                                                          |
    | <strong>Setup-Assistent-Optionen</strong> |                                                     Die folgenden optionalen Einstellungen können später im iOS-Menü <strong>Einstellungen</strong> eingerichtet werden.                                                      |
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


13. Wählen Sie **OK** aus.

14. Wählen Sie **Erstellen** aus, um das Profil zu speichern.

## <a name="connect-school-data-sync"></a>Verbinden mit School Data Sync
(Optional) Apple School Manager unterstützt die Synchronisierung von Kursplandaten mit Azure Active Directory (AD) über Microsoft School Data Sync (SDS). Sie können nur ein Token mit SDS synchronisieren. Wenn Sie ein anderes Token mit School Data Sync einrichten, wird SDS aus dem bisherigen Token entfernt. Das aktuelle Token wird durch eine neue Verbindung ersetzt. Führen Sie die folgenden Schritte aus, um SDS zum Synchronisieren von Schul- bzw. Unidaten zu verwenden.

1. Wählen Sie in [Intune](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus.
2. Wählen Sie ein Apple School Manager-Token und dann **School Data Sync** aus.
3. Wählen Sie unter **School Data Sync** die Option **Zulassen** aus. Mit dieser Einstellung kann Intune in Office 365 eine Verbindung mit SDS herstellen.
4. Um eine Verbindung zwischen Apple School Manager und Azure AD zu ermöglichen, klicken Sie auf **Microsoft-Synchronisierung von Schul-/Unidaten einrichten**. Erfahren Sie mehr über [das Einrichten von School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1).
5. Klicken Sie auf **Speichern** > **OK**.

## <a name="sync-managed-devices"></a>Synchronisieren verwalteter Geräte

Nachdem Intune die Berechtigung zum Verwalten Ihrer Apple School Manager-Geräte zugewiesen wurde, synchronisieren Sie Intune mit dem Apple-Dienst, um Ihre verwalteten Geräte in Intune anzuzeigen.

Wählen Sie in [Intune](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus, wählen Sie in der Liste ein Token aus, und wählen Sie dann **Geräte** > **Synchronisieren** aus. ![Screenshot des ausgewählten Knotens „Geräte des Registrierungprogramms“ und des ausgewählten Links „Synchronisierung“](./media/device-enrollment-program-enroll-ios/image06.png)

  Zur Einhaltung der Apple-Bedingungen für zulässigen Datenverkehr des Registrierungsprogramms erzwingt Intune die folgenden Einschränkungen:
  - Eine vollständige Synchronisation kann nicht öfter als einmal alle sieben Tage erfolgen. Während einer vollständigen Synchronisierung aktualisiert Intune jede Seriennummer von Apple, die Intune zugewiesen ist. Wenn eine vollständige Synchronisierung innerhalb von sieben Tagen nach der vorherigen vollständigen Synchronisierung versucht wird, aktualisiert Intune nur Seriennummern, die nicht bereits in Intune aufgeführt sind.
  - Synchronisierungsanforderungen müssen innerhalb von 15 Minuten abgeschlossen sein. Während dieser Zeit oder bis zum erfolgreichen Erfüllen der Anforderung wird die Schaltfläche **Synchronisieren** deaktiviert.
  - Intune synchronisiert alle 24 Stunden neue und entfernte Geräte für Apple.

>[!NOTE]
>Sie können auch über das Blatt **Geräte des Registrierungsprogramms** Apple School Manager-Seriennummern zu Geräten zuweisen.

## <a name="assign-a-profile-to-devices"></a>Zuweisen eines Profils zu Geräten
Apple School Manager-Geräten, die von Intune verwaltet werden, muss vor der Registrierung ein Registrierungsprofil zugewiesen werden.

1. Wählen Sie in [Intune](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus, und wählen Sie dann in der Liste ein Token aus.
2. Wählen Sie **Geräte** aus, wählen Sie in der Liste die Geräte aus, und wählen Sie dann **Profil zuweisen** aus.
3. Wählen Sie unter **Profil zuweisen** ein Profil für die Geräte aus, und wählen Sie dann **Zuweisen** aus.

## <a name="distribute-devices-to-users"></a>Verteilen von Geräten an Benutzer

Sie haben die Verwaltung und Synchronisierung zwischen Apple und Intune aktiviert und ein Profil zugewiesen, damit Ihre Apple School-Geräte registriert werden können. Sie können jetzt Geräte an Benutzer verteilen. Wenn ein iOS-Apple School Manager-Gerät eingeschaltet wird, wird es für die Verwaltung durch Intune registriert. Wenn das Gerät aktiviert wurde und verwendet wird, kann das Profil erst angewendet werden, wenn das Gerät zurückgesetzt wird.
