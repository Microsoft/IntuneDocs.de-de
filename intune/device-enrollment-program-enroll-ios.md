---
title: "Registrieren von iOS-Geräten mithilfe des Programms zur Geräteregistrierung"
titlesuffix: Microsoft Intune
description: "In diesem Artikel erfahren Sie, wie Sie unternehmenseigene iOS-Geräte mithilfe des Programms zur Geräteregistrierung (Device Enrollment Program, DEP) registrieren."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 24b1ffb1d89f52a51f21dc6c4a588324f3cd87d3
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="automatically-enroll-ios-devices-by-using-apples-device-enrollment-program"></a>Automatisches Registrieren von iOS-Geräten mit dem Programm zur Geräteregistrierung von Apple

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>Temporäre Unterschiede bei der Benutzeroberfläche
>
>Die Benutzeroberflächen für die auf dieser Seite beschriebenen Funktionen werden aktualisiert. Diese Updates werden bis Ende April für alle Benutzerkonten eingeführt.
>
>Wenn Ihre Seite für die **Geräteregistrierung** der folgenden Abbildung ähnelt, wurde Ihr Konto noch nicht für die neue Benutzeroberfläche aktualisiert, und Sie können diese Hilfeseite verwenden.
>
>![Alte Intune-Benutzeroberfläche](./media/appleenroll-oldui.png)
>
>Wenn Ihre Seite für die **Geräteregistrierung** der folgenden Abbildung ähnelt, wurden die Benutzeroberflächen aktualisiert.  Wechseln Sie zu [dieser Hilfeseite](device-enrollment-program-enroll-ios-newui.md).
>
>![Neue Intune-Benutzeroberfläche](./media/appleenroll-newui.png)

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

> [!NOTE]
> Mehrstufige Authentifizierung (Multifactor authentication, MFA) funktioniert nicht während der Einrichtung der DEP-Registrierung mit Benutzeraffinität. Nach der Registrierung funktioniert die MFA auf Geräten wie erwartet. Geräte können Benutzer nicht dazu auffordern, ihr Kennwort zu ändern, wenn sie sich zum ersten Mal anmelden. Außerdem werden Benutzer, deren Kennwörter abgelaufen sind, während der Registrierung nicht aufgefordert, ihr Kennwort zurückzusetzen. Benutzer müssen ihr Kennwort auf einem anderen Gerät zurücksetzen.

## <a name="get-the-apple-dep-token"></a>Abrufen des Apple-DEP-Tokens

Bevor Sie iOS-Geräte mit DEP registrieren können, benötigen Sie ein DEP-Token-Datei (.p7m) von Apple. Mit diesem Token kann Intune Informationen zu DEP-Geräten synchronisieren, die Ihrem Unternehmen gehören. Damit kann Intune außerdem Registrierungsprofile zu Apple hochladen und diesen Profilen Geräte zuweisen.

Verwenden Sie das Apple DEP-Portal, um ein DEP-Token zu erstellen. Sie verwenden das DEP-Portal auch, um in Intune Geräte für die Verwaltung zuzuweisen.

> [!NOTE]
> Wenn Sie das Token vor der Migration zu Azure aus dem klassischen Intune-Portal löschen, stellt Intune womöglich ein gelöschtes Apple DEP-Token wieder her. Sie können das DEP-Token erneut aus dem Azure-Portal löschen. Sie können das DEP-Token erneut aus dem Azure-Portal löschen.

**Schritt 1: Laden Sie ein Intune-Zertifikat mit öffentlichem Schlüssel herunter, das zum Erstellen eines Apple-DEP-Tokens erforderlich ist.**<br>

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Token für Registrierungsprogramm** aus.

  ![Bereich „Registrierungsprogrammtoken“ im Arbeitsbereich „Apple-Zertifikate“](./media/enrollment-program-token-add.png)

2. Wählen Sie **Laden Sie Ihr Zertifikat mit öffentlichem Schlüssel herunter** aus, um die Verschlüsselungsschlüsseldatei (PEM) herunterzuladen und lokal zu speichern. Die PEM-Datei wird verwendet, um ein Vertrauensstellungszertifikat vom Apple Device Enrollment Program-Portal anzufordern.

  ![Bereich „Registrierungsprogrammtoken“ im Arbeitsbereich „Apple-Zertifikate“ zum Herunterladen des öffentlichen Schlüssels](./media/enrollment-program-token-download.png)

**Schritt 2: Erstellen Sie ein Apple-DEP-Token und laden Sie es herunter.**<br>
1. Wählen Sie **Create a token via Apple's Device Enrollment Program** (Token über das Programm zur Geräteregistrierung von Apple erstellen) aus, um das Portal des Bereitstellungsprogramms von Apple zu öffnen. Melden Sie sich mit der Apple-ID Ihres Unternehmens an. Diese Apple-ID kann später zum Erneuern Ihres DEP-Token verwendet werden.
2.  Wählen Sie im [Portal des Bereitstellungsprogramms](https://deploy.apple.com) von Apple die Option **Erste Schritte** für das **Programm zur Geräteregistrierung** aus.

3. Wählen Sie auf der Seite **Server verwalten** die Option **MDM-Server hinzufügen** aus.
4. Geben Sie den **MDM-Servernamen** ein, und wählen Sie anschließend **Weiter** aus. Der Servername dient als Referenz zum Identifizieren des MDM-Servers (mobile device management, Verwaltung mobiler Geräte). Es handelt sich nicht um den Namen oder die URL des Microsoft Intune-Servers.

   ![Hinzufügen eines MDM-Servernamens für DEP und Klick auf „Weiter“](./media/enrollment-program-token-add-server.png)

5. Das Dialogfeld **&lt;Servername&gt; hinzufügen** wird geöffnet, und die Meldung **Laden Sie Ihren öffentlichen Schlüssel hoch** wird angezeigt. Wählen Sie **Datei auswählen** aus, um die PEM-Datei hochzuladen, und wählen Sie anschließend **Weiter** aus.  

6. Wechseln Sie zu **Bereitstellungsprogramme** &gt; **Programm zur Geräteregistrierung** &gt; **Geräte verwalten**.
7. Geben Sie unter **Geräte auswählen nach** an, wie die Geräte identifiziert werden sollen:
    - **Seriennummer**
    - **Reihenfolge**
    - **Upload der CSV-Datei**

   ![Festlegen von „Geräte auswählen nach“ auf „Seriennummer“, der Einstellung „Aktion auswählen“ auf „Zu Server zuweisen“ und der Auswahl des Servernamens](./media/enrollment-program-token-specify-serial.png)

8. Wählen Sie als Nächstes für **Aktion auswählen** die Option **Zu Server zuweisen** aus. Wählen Sie den für Microsoft Intune angegebenen &lt;Servernamen&gt; und anschließend **OK** aus. Das Apple-Portal weist die angegebenen Geräte dem Intune-Server für die Verwaltung zu und zeigt dann **Zuweisung abgeschlossen** an.

   Wechseln Sie im Apple-Portal zu **Bereitstellungsprogramme** &gt; **Programm zur Geräteregistrierung** &gt; **Zuweisungsverlauf anzeigen**, um eine Liste der Geräte und ihre MDM-Server-Zuordnung anzuzeigen.

**Schritt 3: Geben Sie die zum Erstellen Ihres Registrierungsprogrammtokens verwendete Apple-ID ein.**<br>Geben Sie in Intune im Azure-Portal für die zukünftige Verwendung Ihre Apple-ID an.

![Angabe der Apple-ID zur Erstellung des Registrierungsprogrammtokens und Navigieren zu diesem Token](./media/enrollment-program-token-apple-id.png)

**Schritt 4: Navigieren Sie zu Ihrem Registrierungsprogrammtoken, das hochgeladen werden soll.**<br>
Wechseln Sie zur Zertifikatsdatei (.pem), wählen Sie **Öffnen** aus, und wählen Sie dann **Hochladen**aus. Mit dem Push-Zertifikat kann Intune iOS-Geräte registrieren und verwalten, indem die Richtlinie auf registrierte mobile Geräte übertragen wird. Intune führt eine automatische Synchronisierung mit Apple durch, um Ihr Registrierungsprogrammkonto anzuzeigen.

## <a name="create-an-apple-enrollment-profile"></a>Erstellen eines Apple-Registrierungsprofils

Da Sie nun Ihr Token installiert haben, können Sie ein Registrierungsprofil für DEP-Geräte erstellen. Ein Geräteregistrierungsprofil definiert die Einstellungen, die während der Registrierung auf eine Gruppe von Geräten angewendet werden.

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Apple Registrierung** aus.
2. Wählen Sie unter **Registrierungsprogramm für Apple**  den Eintrag **Profile des Registrierungsprogramms** > **Erstellen** aus.
3. Geben Sie unter **Registrierungsprofil erstellen** einen **Namen** und eine **Beschreibung** für das Profil zu administrativen Zwecken ein. Benutzer können diese Informationen nicht sehen. Sie können das Feld **Name** zum Erstellen einer dynamischen Gruppe in Azure Active Directory verwenden. Verwenden Sie den Profilnamen, um den Parameter „enrollmentProfileName“ zu definieren, um Geräte mit diesem Registrierungsprofil zuzuweisen. Erfahren Sie mehr über [dynamische Gruppen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

  Wählen Sie für **Benutzeraffinität** aus, ob Geräte mit diesem Profil mit oder ohne einen zugewiesenen Benutzer registriert werden.

 - **Mit Benutzeraffinität registrieren**: Wählen Sie diese Option für Geräte aus, die Benutzern gehören und das Unternehmensportal verwenden müssen, um Dienste wie z.B. die Installation von Apps nutzen zu können. Benutzeraffinität erfordert [den Endpunkt WS-Trust 13 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints). [Erfahren Sie mehr](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

 - **Ohne Benutzeraffinität registrieren**: Wählen Sie diese Option für ein Gerät aus, das an keinen Benutzer angeschlossen ist. Verwenden Sie diese Zuweisung für Geräte, die Aufgaben ohne den Zugriff auf lokale Benutzerdaten ausführen. Apps wie die Unternehmensportal-App funktionieren nicht.

4. Wählen Sie **Geräteverwaltungseinstellungen** aus, um folgenden Profileinstellungen zu konfigurieren.

  ![Auswählen des Verwaltungsmodus](./media/enrollment-program-profile-mode.png)
  - **Überwacht:** Dieser Verwaltungsmodus ermöglicht weitere Verwaltungsoptionen und deaktiviert standardmäßig die Aktivierungssperre. Wenn Sie das Kontrollkästchen nicht aktivieren, stehen Ihnen nur beschränkte Verwaltungsfunktionen zur Verfügung. Es wird von Microsoft empfohlen, DEP als Mechanismus zur Aktivierung des überwachten Modus zu verwenden. Dies gilt insbesondere für Organisationen, die eine große Anzahl von iOS-Geräten bereitstellen.

 > [!NOTE]
 > Geräte können nicht über Intune für den überwachten Modus konfiguriert werden, wenn sie bereits registriert wurden. Nach der Registrierung kann der überwachte Modus nur aktiviert werden, indem Sie ein iOS-Gerät über ein USB-Kabel mit einem Mac verbinden und den Apple Configurator verwenden. Dadurch wird das Gerät zurückgesetzt und für den überwachten Modus konfiguriert. Erfahren Sie mehr über dieses Thema in der [Dokumentation zu Apple Configurator](http://help.apple.com/configurator/mac/2.3). Auf überwachten Geräten wird folgende Meldungen auf dem Sperrbild angezeigt: „This iPhone is managed by Contoso“ (Dieses iPhone wird von Contoso verwaltet). Außerdem wird die Meldung „This iPhone is supervised. Contoso can monitor your Internet traffic and locate this device“ (Dieses iPhone wird überwacht. Contoso kann Ihren Internetdatenverkehr überwachen und dieses Gerät suchen.) unter **Einstellungen** > **Allgemein** > **Info** angezeigt.

  - **Registrierung gesperrt**: (Erfordert den Vorbereitungsmodus „Überwacht“) Deaktiviert iOS-Einstellungen, die das Entfernen des Verwaltungsprofils zulassen könnten. Wenn Sie dieses Kontrollkästchen nicht aktivieren, kann das Verwaltungsprofil aus dem Menü „Einstellungen“ entfernt werden. Nach der Gerätebereitstellung können Sie diese Einstellung ändern, ohne das Gerät auf Werkseinstellung zurückzusetzen.

  - **Enable Shared iPad** (gemeinsam genutztes iPad aktivieren): Das Programm zur Geräteregistrierung von Apple unterstützt nicht gemeinsam genutzte iPads.

  - **Kopplung zulassen:** Gibt an, ob iOS-Geräte mit Computern synchronisiert werden können. Wenn Sie **Apple Configurator nach Zertifikat zulassen** auswählen, müssen Sie unter **Apple Configurator-Zertifikate** ein Zertifikat auswählen.

  - **Apple Configurator-Zertifikate:** Wenn Sie **Apple Configurator nach Zertifikat zulassen** unter **Kopplung zulassen** ausgewählt haben, wählen Sie ein Apple Configurator-Zertifikat aus, das Sie importieren möchten.

  Wählen Sie **Speichern** aus.

5. Wählen Sie **Einstellungen des Einrichtungs-Assistenten** aus, um die folgenden Profileinstellungen zu konfigurieren:

  ![Auswahl der Konfigurationseinstellungen mit verfügbaren Einstellungen für ein neues Profil des Registrierungsprogramms](./media/enrollment-program-profile-settings.png)
  - **Abteilungsname:** Wird angezeigt, wenn Benutzer während der Aktivierung auf **Info zur Konfiguration** tippen.

  - **Abteilungstelefonnummer:** Wird angezeigt, wenn der Benutzer während der Aktivierung auf die Schaltfläche **Benötigen Sie Hilfe?** klickt.
    - **Setup-Assistent-Optionen**: Diese optionalen Einstellungen können später im iOS-Menü **Einstellungen** eingerichtet werden.
        - **Kennung**
        - **Standortdienste**
        - **Wiederherstellen**
        - **Apple-ID**
        - **Geschäftsbedingungen**
        - **Touch ID**
        - **Apple Pay**
        - **Zoom**
        - **Siri**
        - **Diagnosedaten**

    Wählen Sie **Speichern** aus.

9. Wählen Sie zum Speichern der Profileinstellungen **Erstellen** auf dem Blatt **Registrierungsprofil erstellen** aus. Das Registrierungsprofil wird in der Liste der Registrierungsprofile des Apple-Registrierungsprogramms angezeigt.

## <a name="sync-managed-devices"></a>Synchronisieren verwalteter Geräte
Nachdem Intune nun die Berechtigung zum Verwalten Ihrer Geräte besitzt, können Sie Intune mit Apple synchronisieren, um Ihre verwalteten Geräte in Intune im Azure-Portal anzuzeigen.

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Geräte des Registrierungsprogramms** > **Synchronisieren** aus. Die Statusanzeige zeigt die Zeitdauer, die Sie warten müssen, bevor Sie die Synchronisierung erneut anfordern können.

  ![Ausgewählter Knoten „Geräte des Registrierungsprogramms“ und ausgewählter Link „Synchronisierung“](./media/enrollment-program-device-sync.png)
  
2. Wählen Sie auf dem Blatt **Synchronisieren** die Option **Synchronisierung anfordern** aus. Die Statusanzeige zeigt die Zeitdauer, die Sie warten müssen, bevor Sie die Synchronisierung erneut anfordern können.

   ![Blatt „Synchronisierung“ mit ausgewähltem Link „Synchronisierung anfordern“](./media/enrollment-program-device-request-sync.png)

   Zur Einhaltung der Apple-Bedingungen für zulässigen Datenverkehr des Registrierungsprogramms erzwingt Intune die folgenden Einschränkungen:
     -  Eine vollständige Synchronisation kann nicht öfter als einmal alle sieben Tage erfolgen. Während einer vollständigen Synchronisierung aktualisiert Intune jede Seriennummer von Apple, die Intune zugewiesen ist. Wenn eine vollständige Synchronisierung innerhalb von sieben Tagen nach der vorherigen vollständigen Synchronisierung versucht wird, aktualisiert Intune nur Seriennummern, die nicht bereits in Intune aufgeführt sind.
     -  Synchronisierungsanforderungen müssen innerhalb von 15 Minuten abgeschlossen sein. Während dieser Zeit oder bis zum erfolgreichen Erfüllen der Anforderung wird die Schaltfläche **Synchronisieren** deaktiviert.
     - Intune synchronisiert alle 24 Stunden neue und entfernte Geräte für Apple.

3. Wählen Sie im Arbeitsbereich „Geräte des Registrierungsprogramms“ die Option **Aktualisieren** aus, um Ihre Geräte anzuzeigen.

## <a name="assign-an-enrollment-profile-to-devices"></a>Zuweisen eines Registrierungsprofils an Geräte
Sie müssen Geräten ein Profil des Registrierungsprogramms zuweisen, bevor Sie mit der Registrierung beginnen können.

>[!NOTE]
>Sie können auch auf dem Blatt **Apple-Seriennummern** Profilen Seriennummern zuweisen.

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Optionen **Geräteregistrierung** > **Apple-Registrierung** und dann **Profile des Registrierungsprogramms** aus.
2. Wählen Sie aus der Liste **Profile des Registrierungsprogramms** das Profil aus, das den Geräten zugewiesen werden soll, und wählen Sie anschließend **Geräte zuweisen** aus.

 ![Gerätezuweisungen mit ausgewählter Option „Zuweisen“](./media/enrollment-program-device-assign.png)

3. Wählen Sie **Zuweisen** und anschließend die Geräte aus, die diesem Profil zugewiesen werden sollen. Sie können die Ansicht nach verfügbaren Geräten filtern:
  - **Nicht zugewiesen**
  - **Beliebig**
  - **&lt;Profilname&gt;**
4. Wählen Sie die Geräte aus, die zugewiesen werden sollen. Mit dem Kontrollkästchen oberhalb der Spalte werden bis zu 1000 aufgelistete Geräte ausgewählt. Klicken Sie dann auf **Zuweisen**. Um mehr als 1000 Geräte zu registrieren, wiederholen Sie die Zuweisungsschritte, bis allen Geräten ein Registrierungsprofil zugewiesen ist.

  ![Schaltfläche „Zuweisen“ zum Zuweisen des Profils des Registrierungsprogramms in Intune](media/dep-profile-assignment.png)

## <a name="distribute-devices"></a>Verteilen von Geräten
Sie haben die Verwaltung und Synchronisierung zwischen Apple und Intune aktiviert und haben ein Profil zugewiesen, damit Ihre DEP-Geräte registriert werden können. Sie können jetzt Geräte an Benutzer verteilen. Für Geräte mit Benutzeraffinität muss jedem Benutzer eine Intune-Lizenz zugewiesen werden. Geräte ohne Benutzeraffinität benötigen eine Gerätelizenz. Ein aktiviertes Gerät kann kein Registrierungsprofil anwenden, bis das Gerät nicht auf Werkseinstellung zurückgesetzt wurde.

Informationen finden Sie unter [Registrieren Ihres iOS-Geräts in Intune mit dem Programm zur Geräteregistrierung](/intune-user-help/enroll-your-device-dep-ios). 


