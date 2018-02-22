---
title: "Registrieren von iOS-Geräten – Programm zur Geräteregistrierung"
titlesuffix: Azure portal
description: "In diesem Artikel erfahren Sie, wie Sie unternehmenseigene iOS-Geräte mithilfe des Programms zur Geräteregistrierung (Device Enrollment Program, DEP) registrieren (neue Benutzeroberfläche)."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b97da0c8ca0a1e3891a64508b565749dec06de93
ms.sourcegitcommit: 9bd6278d129fa29f184b2d850138f8f65f3674ea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Automatisches Registrieren von iOS-Geräten mit dem Programm zur Geräteregistrierung von Apple

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>Temporäre Unterschiede bei der Benutzeroberfläche
> Die Benutzeroberflächen für die auf dieser Seite beschriebenen Funktionen werden aktualisiert. Diese Updates werden bis Ende April für alle Benutzerkonten eingeführt.
>
> Wenn Ihre Seite für die **Geräteregistrierung** der folgenden Abbildung ähnelt, wurden die Benutzeroberflächen aktualisiert.
>
> ![Neue Benutzeroberfläche](./media/appleenroll-newui.png)
>
> Wenn Ihre Seite für die **Geräteregistrierung** der folgenden Abbildung ähnelt, wurde Ihr Konto noch nicht für die neue Benutzeroberfläche aktualisiert, und Sie können diese Hilfeseite verwenden. Wechseln Sie zu [dieser Hilfeseite](device-enrollment-program-enroll-ios.md).
>
> ![Alte Benutzeroberfläche](./media/appleenroll-oldui.png)

Dieses Thema unterstützt Sie dabei, die iOS-Geräteregistrierung für Geräte zu aktivieren, die über das [Programm zur Geräteregistrierung (Device Enrollment Program, DEP)](https://deploy.apple.com) von Apple erworben wurden. Sie können die Registrierung des Programms zur Geräteregistrierung für eine große Anzahl von Geräten aktivieren, ohne diese auch nur zu berühren. Sie können Geräte wie iPhones und iPad direkt an Benutzer versenden. Wenn der Benutzer das Gerät anschaltet, wird der Setup-Assistent mit vordefinierten Einstellungen ausgeführt, und das Gerät wird für die Verwaltung registriert.

Zur Aktivierung der DEP-Registrierung können Sie sowohl das Intune-Portal als auch das Apple DEP-Portal verwenden. Sie benötigen auch eine Liste von Seriennummern oder eine Bestellnummer, um Geräte in Intune zur Verwaltung zuweisen zu können. Sie erstellen DEP-Registrierungsprofile, die Einstellungen enthalten, die für Geräte während der Registrierung gelten.

Die Registrierung mit DEP funktioniert übrigens nicht mit dem [Geräteregistrierungs-Manager](device-enrollment-manager-enroll.md).

## <a name="what-is-supervised-mode"></a>Überwachter Modus
Apple hat für iOS 5 den überwachten Modus eingeführt. Ein iOS-Gerät im überwachten Modus kann über zusätzliche Steuerelemente verwaltet werden. Dies ist bei unternehmenseigenen Geräten besonders nützlich. Intune unterstützt die Konfiguration von Geräten für den überwachten Modus als Teil des Apple-Programms zur Geräteregistrierung (DEP). 

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
- [MDM-Autorität](mdm-authority-set.md)
- [Apple-MDM-Push-Zertifikat](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Abrufen eines Apple-DEP-Tokens

Bevor Sie iOS-Geräte mit DEP registrieren können, benötigen Sie ein DEP-Token-Datei (.p7m) von Apple. Mit diesem Token kann Intune Informationen zu DEP-Geräten synchronisieren, die Ihrem Unternehmen gehören. Damit kann Intune außerdem Registrierungsprofile zu Apple hochladen und diesen Profilen Geräte zuweisen.

Verwenden Sie das Apple DEP-Portal, um ein DEP-Token zu erstellen. Sie verwenden das DEP-Portal auch, um in Intune Geräte für die Verwaltung zuzuweisen.

> [!NOTE]
> Wenn Sie das Token vor der Migration zu Azure aus dem klassischen Intune-Portal löschen, stellt Intune womöglich ein gelöschtes Apple DEP-Token wieder her. Sie können das DEP-Token erneut aus dem Azure-Portal löschen. Sie können das DEP-Token erneut aus dem Azure-Portal löschen.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Schritt 1: Laden Sie das Intune-Zertifikat mit öffentlichem Schlüssel herunter, das zum Erstellen des Tokens erforderlich ist.

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** > **Hinzufügen** aus.

    ![Rufen Sie ein Registrierungsprogrammtoken ab.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Wählen Sie **Laden Sie Ihr Zertifikat mit öffentlichem Schlüssel herunter** aus, um die Verschlüsselungsschlüsseldatei (PEM) herunterzuladen und lokal zu speichern. Die PEM-Datei wird verwendet, um ein Vertrauensstellungszertifikat vom Apple Device Enrollment Program-Portal anzufordern.
  ![Screenshot des Bereichs „Registrierungsprogrammtoken“ im Arbeitsbereich „Apple-Zertifikate“ zum Herunterladen des öffentlichen Schlüssels](./media/device-enrollment-program-enroll-ios/image02.png)

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
Wechseln Sie im Feld **Apple-Token** zur Zertifikatsdatei (PEM), wählen Sie **Öffnen** und dann **Erstellen** aus. Mit dem Push-Zertifikat kann Intune iOS-Geräte registrieren und verwalten, indem die Richtlinie auf registrierte mobile Geräte übertragen wird. Intune führt eine automatische Synchronisierung mit Apple durch, um Ihr Registrierungsprogrammkonto anzuzeigen.

## <a name="create-an-apple-enrollment-profile"></a>Erstellen eines Apple-Registrierungsprofils

Da Sie nun Ihr Token installiert haben, können Sie ein Registrierungsprofil für DEP-Geräte erstellen. Ein Geräteregistrierungsprofil definiert die Einstellungen, die während der Registrierung auf eine Gruppe von Geräten angewendet werden.

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus.
2. Wählen Sie ein Token aus, und wählen Sie dann **Profile** und **Profil erstellen** aus.
    ![Erstellen Sie einen Screenshot des Profils.](./media/device-enrollment-program-enroll-ios/image04.png)
3. Geben Sie zu administrativen Zwecken unter **Profil erstellen** einen **Namen** und eine **Beschreibung** für das Profil ein. Benutzer können diese Informationen nicht sehen. Sie können das Feld **Name** zum Erstellen einer dynamischen Gruppe in Azure Active Directory verwenden. Verwenden Sie den Profilnamen, um den Parameter „enrollmentProfileName“ zu definieren, um Geräte mit diesem Registrierungsprofil zuzuweisen. Erfahren Sie mehr über [dynamische Gruppen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).
    ![Profilname und Beschreibung](./media/device-enrollment-program-enroll-ios/image05.png)

4. Wählen Sie unter **Benutzeraffinität** aus, ob sich Geräte mit diesem Profil mit oder ohne einen zugewiesenen Benutzer registrieren müssen.
    - **Mit Benutzeraffinität registrieren**: Wählen Sie diese Option für Geräte aus, die Benutzern gehören und das Unternehmensportal verwenden sollen, um Dienste wie z. B. die Installation von Apps nutzen zu können. Mit dieser Option können Benutzer ihre Geräte auch über das Unternehmensportal authentifizieren. Benutzeraffinität erfordert [den Endpunkt WS-Trust 13 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints). [Erfahren Sie mehr](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Ohne Benutzeraffinität registrieren**: Wählen Sie diese Option für Geräte aus, die keinem einzelnen Benutzer zugeordnet sind. Verwenden Sie diese Option für Geräte, die Aufgaben ohne den Zugriff auf lokale Benutzerdaten ausführen. Apps wie die Unternehmensportal-App funktionieren nicht.

5. Wenn Sie **Mit Benutzeraffinität registrieren** ausgewählt haben, können Sie die Benutzerauthentifizierung über das Unternehmensportal statt über den Apple-Setup-Assistenten erlauben.

    ![Authentifizieren über das Unternehmensportal](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Die mehrstufige Authentifizierung (MFA) funktioniert bei der DEP-Registrierung nicht, wenn Sie die Profileigenschaften auf **Mit Benutzeraffinität registrieren** festgelegt haben und kein Unternehmensportal verwenden. Nach der Registrierung funktioniert die MFA auf Geräten wie erwartet. Geräte können Benutzer nicht dazu auffordern, ihr Kennwort zu ändern, wenn sie sich zum ersten Mal anmelden. Außerdem werden Benutzer, deren Kennwörter abgelaufen sind, während der Registrierung nicht aufgefordert, ihr Kennwort zurückzusetzen. Benutzer müssen ihr Kennwort auf einem anderen Gerät zurücksetzen.

6. Wählen Sie **Geräteverwaltungseinstellungen** aus, und geben Sie an, ob Geräte mit diesem Profil überwacht werden sollen.
    Bei **überwachten** Geräten stehen mehr Verwaltungsfunktionen zur Verfügung, und die Aktivierungssperre ist standardmäßig deaktiviert. Es wird von Microsoft empfohlen, DEP als Mechanismus zur Aktivierung des überwachten Modus zu verwenden. Dies gilt insbesondere für Organisationen, die eine große Anzahl von iOS-Geräten bereitstellen.

    Die Benutzer werden auf zweierlei Weise benachrichtigt, dass ihre Geräte überwacht werden:

    - Auf dem Sperrbildschirm wird angezeigt: „This iPhone is managed by Contoso (Dieses iPhone wird von Contoso verwaltet)“.
    - Auf dem unter **Einstellungen** > **Allgemein** > **Info** angezeigten Bildschirm steht: „This iPhone is supervised. Contoso can monitor your Internet traffic and locate this device“ (Dieses iPhone wird überwacht. Contoso kann Ihren Internetdatenverkehr überwachen und dieses Gerät suchen.)

     > [!NOTE]
     > Ein Gerät, das ohne Überwachung registriert wurde, kann nur mithilfe von Apple Configurator auf den Status „Überwacht“ zurückgesetzt werden. Wenn Sie das Gerät auf diese Weise zurücksetzen möchten, müssen Sie ein iOS-Gerät über ein USB-Kabel mit einem Mac verbinden. Erfahren Sie mehr über dieses Thema in der [Dokumentation zu Apple Configurator](http://help.apple.com/configurator/mac/2.3).
     
7. Wählen Sie aus, ob für Geräte mit diesem Profil die gesperrte Registrierung verwendet werden soll. Wenn **Gesperrte Registrierung** aktiviert ist, sind die iOS-Einstellungen deaktiviert, mit denen das Verwaltungsprofil aus dem Menü **Einstellungen** entfernt werden kann. Nach der Gerätebereitstellung können Sie diese Einstellung ändern, ohne das Gerät auf Werkseinstellung zurückzusetzen. Bei solchen Geräten muss der Verwaltungsmodus **Überwacht** auf *Ja* eingestellt sein. 

8. Wählen Sie aus, ob für Geräte mit diesem Profil die Option **Mit Computern synchronisieren** verwendet werden soll. Wenn Sie **Apple Configurator nach Zertifikat zulassen** auswählen, müssen Sie unter **Apple Configurator-Zertifikate** ein Zertifikat auswählen.

9. Wenn Sie im vorherigen Schritt **Apple Configurator nach Zertifikat zulassen** ausgewählt haben, müssen Sie ein Apple Configurator-Zertifikat zum Importieren auswählen.

10. Wählen Sie **OK** aus.

11. Wählen Sie **Einstellungen des Einrichtungs-Assistenten** aus, um die folgenden Profileinstellungen zu konfigurieren: ![Anpassung des Setup-Assistenten](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)

    | Einstellung | Beschreibung |
    | --- | --- |
    | **Abteilungsname** | Wird angezeigt, wenn der Benutzer während der Aktivierung auf **Info zur Konfiguration** tippt. |
    | **Abteilungstelefonnummer** | Wird angezeigt, wenn der Benutzer während der Aktivierung auf die Schaltfläche **Benötigen Sie Hilfe?** klickt. |
    | **Setup-Assistent-Optionen** | Die folgenden optionalen Einstellungen können später im iOS-Menü **Einstellungen** eingerichtet werden. |
    | **Kennung** | Fordert während der Aktivierung zur Eingabe der Kennung auf. Fordern Sie immer eine Kennung an, es sei denn, das Gerät und der Zugriff darauf werden auf andere Weise geschützt (d.h. im Kioskmodus zum Einschränken des Geräts auf eine App). |
    | **Standortdienste** | Falls aktiviert, fordert der Setup-Assistent während der Aktivierung zur Ausführung dieses Dienstes auf. |
    | **Wiederherstellen** | Falls aktiviert, fordert der Setup-Assistent während der Aktivierung die iCloud-Sicherung an. |
    | **iCloud und Apple-ID** | Falls aktiviert, fordert der Setup-Assistent den Benutzer auf, sich mit einer Apple-ID anzumelden, und im Bildschirm „Apps und Daten“ kann das Gerät von einer iCloud-Sicherung wiederhergestellt werden. |
    | **Geschäftsbedingungen** | Falls aktiviert, fordert der Setup-Assistenten während der Aktivierung den Benutzer auf, die Apple-Geschäftsbedingungen zu akzeptieren. |
    | **Touch ID** | Falls aktiviert, fordert der Setup-Assistent während der Aktivierung zur Ausführung dieses Dienstes auf. |
    | **Apple Pay** | Falls aktiviert, fordert der Setup-Assistent während der Aktivierung zur Ausführung dieses Dienstes auf. |
    | **Zoom** | Falls aktiviert, fordert der Setup-Assistent während der Aktivierung zur Ausführung dieses Dienstes auf. |
    | **Siri** | Falls aktiviert, fordert der Setup-Assistent während der Aktivierung zur Ausführung dieses Dienstes auf. |
    | **Diagnosedaten** | Falls aktiviert, fordert der Setup-Assistent während der Aktivierung zur Ausführung dieses Dienstes auf. |

12. Wählen Sie **OK** aus.

13. Wählen Sie **Erstellen** aus, um das Profil zu speichern.

## <a name="sync-managed-devices"></a>Synchronisieren verwalteter Geräte
Nachdem Intune nun die Berechtigung zum Verwalten Ihrer Geräte besitzt, können Sie Intune mit Apple synchronisieren, um Ihre verwalteten Geräte in Intune im Azure-Portal anzuzeigen.

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus, wählen Sie in der Liste ein Token aus, und wählen Sie dann **Geräte** > **Synchronisieren** aus. ![Screenshot des ausgewählten Knotens „Geräte des Registrierungprogramms“ und des ausgewählten Links „Synchronisierung“](./media/device-enrollment-program-enroll-ios/image06.png)
  
  Zur Einhaltung der Apple-Bedingungen für zulässigen Datenverkehr des Registrierungsprogramms erzwingt Intune die folgenden Einschränkungen:
  - Eine vollständige Synchronisation kann nicht öfter als einmal alle sieben Tage erfolgen. Während einer vollständigen Synchronisierung aktualisiert Intune jede Seriennummer von Apple, die Intune zugewiesen ist. Wenn eine vollständige Synchronisierung innerhalb von sieben Tagen nach der vorherigen vollständigen Synchronisierung versucht wird, aktualisiert Intune nur Seriennummern, die nicht bereits in Intune aufgeführt sind.
  - Synchronisierungsanforderungen müssen innerhalb von 15 Minuten abgeschlossen sein. Während dieser Zeit oder bis zum erfolgreichen Erfüllen der Anforderung wird die Schaltfläche **Synchronisieren** deaktiviert.
  - Intune synchronisiert alle 24 Stunden neue und entfernte Geräte für Apple.

## <a name="assign-an-enrollment-profile-to-devices"></a>Zuweisen eines Registrierungsprofils an Geräte
Sie müssen Geräten ein Profil des Registrierungsprogramms zuweisen, bevor Sie mit der Registrierung beginnen können.

>[!NOTE]
>Sie können auch auf dem Blatt **Apple-Seriennummern** Profilen Seriennummern zuweisen.

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus, und wählen Sie in der Liste ein Token aus.
2. Wählen Sie **Geräte** aus, wählen Sie in der Liste die Geräte aus, und wählen Sie dann **Profil zuweisen** aus.
3. Wählen Sie unter **Profil zuweisen** ein Profil für die Geräte aus, und wählen Sie dann **Zuweisen** aus.

### <a name="assign-a-default-profile"></a>Zuweisen eines Standardprofils

Sie können ein Standardprofil auswählen, das auf alle Geräte angewendet wird, die sich mit einem bestimmten Token registrieren.

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** aus, und wählen Sie in der Liste ein Token aus.
2. Wählen Sie **Standardprofil festlegen** aus, wählen Sie ein Profil in der Dropdownliste aus, und wählen Sie dann **Speichern** aus. Dieses Profil wird auf alle Geräte angewendet, die sich mit dem Token registrieren.

## <a name="distribute-devices"></a>Verteilen von Geräten
Sie haben die Verwaltung und Synchronisierung zwischen Apple und Intune aktiviert und haben ein Profil zugewiesen, damit Ihre DEP-Geräte registriert werden können. Sie können jetzt Geräte an Benutzer verteilen. Für Geräte mit Benutzeraffinität muss jedem Benutzer eine Intune-Lizenz zugewiesen werden. Geräte ohne Benutzeraffinität benötigen eine Gerätelizenz. Ein aktiviertes Gerät kann kein Registrierungsprofil anwenden, bis das Gerät nicht auf Werkseinstellung zurückgesetzt wurde.

Informationen finden Sie unter [Registrieren Ihres iOS-Geräts in Intune mit dem Programm zur Geräteregistrierung](/intune-user-help/enroll-your-device-dep-ios).


