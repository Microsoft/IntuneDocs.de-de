---
title: "Einrichten der Registrierung von iOS-Geräten über das Apple School Manager-Programm"
titlesuffix: Microsoft Intune
description: "Erfahren Sie, wie Sie das Apple School Manager-Programm für die Registrierung von unternehmenseigenen iOS-Geräten bei Intune einrichten."
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
ms.openlocfilehash: f639a61c4d481a891156383c3a23e0e1511a5fbe
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="set-up-ios-device-enrollment-with-apple-school-manager"></a>Einrichten der iOS-Geräteregistrierung mit Apple School Manager

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
>Wenn Ihre Seite für die **Geräteregistrierung** der folgenden Abbildung ähnelt, wurden die Benutzeroberflächen aktualisiert.  Wechseln Sie zu [dieser Hilfeseite](apple-school-manager-set-up-ios-newui.md).
>
>![Neue Intune-Benutzeroberfläche](./media/appleenroll-newui.png)

Dieses Thema unterstützt Sie dabei, die iOS-Geräteregistrierung für Geräte einzurichten, die über das Programm [Apple School Manager](https://school.apple.com/) erworben wurden. Wenn Sie Intune mit Apple School Manager verwenden, können Sie eine große Zahl von iOS-Geräten registrieren, ohne diese in den Händen zu halten. Wenn ein Schüler oder ein Lehrer das Gerät anschaltet, wird der Setup-Assistent mit vordefinierten Einstellungen ausgeführt, und das Gerät wird für die Verwaltung registriert.

Um die Registrierung mit Apple School Manager möglich zu machen, müssen Sie die Portale von Intune und Apple School Manager verwenden. Sie benötigen auch eine Liste von Seriennummern oder eine Bestellnummer, um Geräte in Intune zur Verwaltung zuweisen zu können. Sie erstellen DEP-Registrierungsprofile, die Einstellungen enthalten, die für Geräte während der Registrierung gelten.

Die Registrierung von Apple School Manager kann übrigens nicht mit dem [Programm zur Geräteregistrierung von Apple](device-enrollment-program-enroll-ios.md) oder dem [Geräteregistrierungs-Manager](device-enrollment-manager-enroll.md) verwendet werden.

**Voraussetzungen**
- [Apple-MDM-Push-Zertifikat](apple-mdm-push-certificate-get.md)
- [MDM-Autorität](mdm-authority-set.md)
- [Apple-MDM-Push-Zertifikat](apple-mdm-push-certificate-get.md)
- Benutzeraffinität erfordert [den Endpunkt WS-Trust 13 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints). [Erfahren Sie mehr](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
- Geräte, die über das Programm [Apple School Management](http://school.apple.com) erworben wurden

>[!NOTE]
>Die mehrstufige Authentifizierung (Multifactor Authentication, MFA) funktioniert während der Registrierung auf Apple School Manager-Geräten mit Benutzeraffinität nicht. Nach der Registrierung funktioniert die MFA auf diesen Geräten wie erwartet. Nach der Registrierung funktioniert die MFA auf Geräten wie erwartet. Geräte können Benutzer nicht dazu auffordern, ihr Kennwort zu ändern, wenn sie sich zum ersten Mal anmelden. Außerdem werden Benutzer, deren Kennwörter abgelaufen sind, während der Registrierung nicht aufgefordert, ihr Kennwort zurückzusetzen. Benutzer müssen ihr Kennwort auf einem anderen Gerät zurücksetzen.

## <a name="get-the-apple-token-and-assign-devices"></a>Abrufen des Apple-Tokens und Zuweisen von Geräten

Bevor Sie unternehmenseigene iOS-Geräte mit dem Apple School Manager registrieren können, benötigen Sie ein Token (P7M-Datei) von Apple. Mit diesem Token kann Intune Informationen zu Geräten synchronisieren, die zum Apple School Manager-Programm gehören. Damit kann Intune außerdem Registrierungsprofile an Apple übermitteln und diesen Profilen Geräte zuweisen. Im Apple-Portal können Sie auch Geräteseriennummern für die Verwaltung zuweisen.

**Schritt 1: Laden Sie ein Intune-Zertifikat mit öffentlichem Schlüssel herunter, das zum Erstellen eines Apple-Tokens erforderlich ist.**<br>
1. Wählen Sie unter [Intune im Azure-Portal](https://aka.ms/intuneportal) die Option **Geräteregistrierung** und dann **Token des Registrierungsprogramms** aus.

  ![Bereich „Registrierungsprogrammtoken“ im Arbeitsbereich „Apple-Zertifikate“ zum Herunterladen des öffentlichen Schlüssels](./media/enrollment-program-token-download.png)

2. Wählen Sie auf dem Blatt **Registrierungsprogrammtoken** die Option **Laden Sie Ihr Zertifikat mit öffentlichem Schlüssel herunter** aus, um die Verschlüsselungsschlüsseldatei (PEM) herunterzuladen und lokal zu speichern. Die PEM-Datei wird verwendet, um ein Vertrauensstellungszertifikat vom Apple School Manager-Portal anzufordern.

**Schritt 2: Rufen Sie ein Token ab, und weisen Sie Geräte zu.**<br>
1. Klicken Sie auf **Token über Apple School Manager erstellen**, und melden Sie sich mit Ihrer Apple-Unternehmens-ID an. Sie können diese Apple-ID auch zum Erneuern Ihres Apple School Manager-Tokens verwenden.
2.  Wechseln Sie im [Apple School Manager-Portal](https://school.apple.com) zu **MDM-Server**, und klicken Sie auf **MDM-Server hinzufügen** (oben rechts).
3.  Geben Sie den **MDM-Servernamen** ein. Der Servername dient als Referenz zum Identifizieren des MDM-Servers (mobile device management, Verwaltung mobiler Geräte). Es handelt sich nicht um den Namen oder die URL des Microsoft Intune-Servers.
   ![Apple School Manager-Portal mit der ausgewählten Option „Seriennummer“](./media/asm-server-assignment.png)

4.  Wählen Sie im Apple-Portal die Option **Datei hochladen...**, navigieren Sie zur PEM-Datei, und wählen Sie **MDM-Server speichern** (unten rechts).
5.  Klicken Sie auf **Token abrufen**, und laden Sie die Servertokendatei (P7M) auf Ihren Computer herunter.
6. Wechseln Sie zu **Gerätezuweisungen**, und verwenden Sie die Option **Gerät auswählen**, indem Sie **Seriennummern** oder **Bestellnummer** manuell eingeben oder eine **CSV-Datei hochladen**.
     ![Apple School Manager-Portal mit der ausgewählten Option „Seriennummer“](./media/asm-device-assignment.png)
7.  Wählen Sie die Aktion **Zu Server zuweisen**, und wählen Sie den von Ihnen erstellten **MDM-Server** aus.
8. Geben Sie an Sie **Geräte ausgewählt werden**, und stellen Sie dann Geräteinformationen sowie Details bereit.
9. Wählen Sie **Zu Server zuweisen** aus. Wählen Sie den für Microsoft Intune angegebenen &lt;Servernamen&gt; und anschließend **OK** aus.

**Schritt 3: Geben Sie die Apple-ID ein, die Sie zum Erstellen Ihres Apple School Manager-Tokens verwendet haben.**<br>Diese ID muss zum Erneuern Ihres Apple School Manager-Tokens verwendet werden und wird zur späteren Referenz gespeichert.

![Angabe der Apple-ID zur Erstellung des Registrierungsprogrammtokens und zur Navigation zu diesem Token](./media/enrollment-program-token-apple-id.png)

**Schritt 4: Suchen Sie Ihr Token, und laden Sie es hoch.**<br>
Wechseln Sie zur Zertifikatsdatei (P7M), und wählen Sie **Öffnen** und anschließend **Hochladen** aus. Intune synchronisiert Ihre Apple School Manager-Geräte automatisch mit Apple.

## <a name="create-an-apple-enrollment-profile"></a>Erstellen eines Apple-Registrierungsprofils
Ein Geräteregistrierungsprofil definiert die Einstellungen, die während der Registrierung auf eine Gruppe von Geräten angewendet werden.

1. Wählen Sie unter „Intune“ im Azure-Portal nacheinander die Optionen **Geräteregistrierung** und **Apple-Registrierung** aus.
2. Wählen Sie unter **Registrierungsprogramm** den Eintrag **Profile des Registrierungsprogramms** aus.
3. Wählen Sie auf dem Blatt **Profile des Registrierungsprogramms** die Option **Erstellen** aus.
4. Geben Sie auf dem Blatt **Registrierungsprofil erstellen** einen **Namen** und eine **Beschreibung** für das Profil ein, das in Intune angezeigt wird.
5. Wählen Sie für **Benutzeraffinität** aus, ob Geräte mit diesem Profil mit oder ohne Benutzeraffinität registriert werden.

 - **Mit Benutzeraffinität registrieren**: Fügt ein Gerät einem Benutzer während der Einrichtung bei.

  Der Apple School Manager-Modus „Gemeinsam genutztes iPad“ erfordert, dass Benutzer sich ohne Affinität registrieren.

 - **Ohne Benutzeraffinität registrieren**: Wählen Sie diese Option für ein Gerät aus, das an keinen Benutzer angeschlossen ist, wie z.B. freigegebene Geräte. Verwenden Sie diese Zuweisung für Geräte, die Aufgaben ohne den Zugriff auf lokale Benutzerdaten ausführen. Apps wie die Unternehmensportal-App funktionieren nicht.

6. Wählen Sie **Geräteverwaltungseinstellungen** aus. Diese Elemente werden während der Aktivierung festgelegt und erfordern ein Zurücksetzen auf die Werkseinstellungen, damit die Änderungen wirksam werden. Konfigurieren Sie die folgenden Profileinstellungen, und klicken Sie dann auf **Speichern**:

  ![Auswählen des Verwaltungsmodus](./media/enrollment-program-profile-mode.png)

    - **Überwacht:** Dieser Verwaltungsmodus ermöglicht weitere Verwaltungsoptionen und deaktiviert standardmäßig die Aktivierungssperre. Wenn Sie das Kontrollkästchen nicht aktivieren, stehen Ihnen nur beschränkte Verwaltungsfunktionen zur Verfügung.

     - **Registrierung gesperrt**: (Erfordert den Vorbereitungsmodus „Überwacht“) Deaktiviert iOS-Einstellungen, die das Entfernen des Verwaltungsprofils zulassen könnten. Wenn Sie dieses Kontrollkästchen nicht aktivieren, kann das Verwaltungsprofil aus dem Menü „Einstellungen“ entfernt werden.
   - **Gemeinsam genutztes iPad**: (erfordert die Option **Ohne Benutzeraffinität registrieren** und den Modus „Überwacht“.) Diese Einstellung ermöglicht es, dass mehrere Benutzer sich mithilfe einer verwalteten Apple-ID bei registrierten iPads anmelden können. Verwaltete Apple-IDs werden im Apple School Manager-Portal erstellt. Weitere Informationen zu gemeinsam genutzten iPads finden Sie [in diesem Artikel](education-settings-configure-ios-shared.md). Sie sollten sich auch die [von Apple freigegebenen Anforderungen für das iPad](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56) ansehen.

   >[!NOTE]
   >Wenn **Benutzeraffinität** auf den Modus **Mit Benutzeraffinität** oder **Überwacht**  auf **deaktiviert** festgelegt wird, wird der Modus „Gemeinsam genutztes iPad“ für das Registrierungsprofil deaktiviert.

        - **Maximum Cached Users** - (Requires **Shared iPad** = **Yes**) Creates a partition on the device for each user. The recommended value is the number of students likely to use the device over a period of time. For example, if six students use the device regularly during the week, set this number to six.  

    - **Kopplung zulassen:** Gibt an, ob iOS-Geräte mit Computern synchronisiert werden können. Wenn Sie **Apple Configurator nach Zertifikat zulassen** auswählen, müssen Sie unter **Apple Configurator-Zertifikate** ein Zertifikat auswählen.

      - **Apple Configurator-Zertifikate:** Wenn Sie **Apple Configurator nach Zertifikat zulassen** unter **Kopplung zulassen** ausgewählt haben, wählen Sie ein Apple Configurator-Zertifikat aus, das Sie importieren möchten.

7. Klicken Sie auf **Einstellungen des Einrichtungs-Assistenten**, konfigurieren Sie die folgenden Profileinstellungen, und klicken Sie dann auf **Speichern**:

    - **Abteilungsname:** Wird angezeigt, wenn Benutzer während der Aktivierung auf **Info zur Konfiguration** tippen.

    - **Abteilungstelefonnummer:** Wird angezeigt, wenn der Benutzer während der Aktivierung auf die Schaltfläche „Benötigen Sie Hilfe?“ klickt.
    - **Setup-Assistent-Optionen**: Wenn diese Einstellungen im Setup-Assistenten ausgeschlossen wurden, können sie später im iOS-Menü **Einstellungen** eingerichtet werden.
        - **Kennung** – Aufforderung zur Eingabe der Kennung während der Aktivierung. Fordern Sie immer eine Kennung an, es sei denn, das Gerät und der Zugriff darauf werden auf andere Weise geschützt (d.h. im Kioskmodus zum Einschränken des Geräts auf eine App).
        - **Standortdienste** – Falls aktiviert, fragt der Setup-Assistent ab, ob der Diensts aktiviert werden soll.
        - **Wiederherstellen**: Falls aktiviert, fordert der Setup-Assistent die iCloud-Sicherung während der Aktivierung an.
        - **Apple-ID**: Falls aktiviert, fordert iOS Benutzer zur Angabe einer Apple-ID an, wenn Intune versucht, eine App ohne eine ID zu installieren. Eine Apple ID ist erforderlich, um iOS App Store-Apps herunterzuladen, einschließlich Apps, die von Intune installiert wurden.
        - **Geschäftsbedingungen**: Falls aktiviert, fordert der Setup-Assistenten Benutzer auf, die Apple-Geschäftsbedingungen während der Aktivierung zu akzeptieren.
        - **Touch ID**: Falls aktiviert, fordert der Setup-Assistent zur Ausführung dieses Dienst während der Aktivierung auf.
        - **Apple Pay**: Falls aktiviert, fordert der Setup-Assistent zur Ausführung dieses Dienst während der Aktivierung auf.
        - **Zoom**: Falls aktiviert, fordert der Setup-Assistent zur Ausführung dieses Dienst während der Aktivierung auf.
        - **Siri** – Falls aktiviert, fordert der Setup-Assistent zur Ausführung dieses Dienst während der Aktivierung auf
        - **Diagnosedaten:** Bei Aktivierung fordert der Setup-Assistent während der Aktivierung zur Ausführung dieses Dienst auf.

8. Wählen Sie zum Speichern der Profileinstellungen **Erstellen** auf dem Blatt **Registrierungsprofil erstellen** aus.

## <a name="connect-school-data-sync"></a>Verbinden mit School Data Sync
(Optional) Apple School Manager unterstützt die Synchronisierung von Kursplandaten mit Azure Active Directory (AD) über Microsoft School Data Sync (SDS). Führen Sie die folgenden Schritte aus, um SDS zum Synchronisieren von Schul- bzw. Unidaten zu verwenden.

1. Klicken Sie auf dem Blatt **Registrierungsprogrammtoken** entweder auf das blaue Informationsbanner oder auf **SDS verbinden**.
2. Legen Sie die Einstellung **Der Microsoft-Synchronisierung von Schul-/Unidaten die Verwendung dieses Tokens gestatten** auf **Zulassen** fest. Mit dieser Einstellung kann Intune in Office 365 eine Verbindung mit SDS herstellen.
3. Um eine Verbindung zwischen Apple School Manager und Azure AD zu ermöglichen, klicken Sie auf **Microsoft-Synchronisierung von Schul-/Unidaten einrichten**. Erfahren Sie mehr über [das Einrichten von School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1).
4. Klicken Sie zum Speichern und Fortfahren auf **OK**.

## <a name="sync-managed-devices"></a>Synchronisieren verwalteter Geräte
Nachdem Intune nun die Berechtigung zum Verwalten Ihrer Apple School Manager-Geräte zugewiesen wurde, können Sie Intune mit dem Apple-Dienst synchronisieren, um Ihre verwalteten Geräte im Intune-Portal anzuzeigen.

1. Wählen Sie in Intune im Azure-Portal die Optionen **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammgeräte** > **Synchronisierung** aus. Die Statusanzeige zeigt die Zeitdauer, die Sie warten müssen, bevor Sie die Synchronisierung erneut anfordern können.

  ![Ausgewählter Knoten „Geräte des Registrierungprogramms“ und ausgewählter Link „Synchronisierung“](./media/enrollment-program-device-sync.png)
2. Wählen Sie auf dem Blatt **Synchronisieren** die Option **Synchronisierung anfordern** aus. Die Statusanzeige zeigt die Zeitdauer, die Sie warten müssen, bevor Sie die Synchronisierung erneut anfordern können.

  ![Blatt „Synchronisierung“ mit ausgewähltem Link „Synchronisierung anfordern“](./media/enrollment-program-device-request-sync.png)

  Zur Einhaltung der Apple-Bedingungen für zulässigen Datenverkehr erzwingt Intune die folgenden Einschränkungen:
   -    Eine vollständige Synchronisation kann nicht öfter als einmal alle sieben Tage erfolgen. Während einer vollständigen Synchronisierung aktualisiert Intune jede Seriennummer, die Intune von Apple zugewiesen wurde, und zwar unabhängig davon, ob die Seriennummer vorher synchronisiert wurde oder nicht. Wenn eine vollständige Synchronisierung innerhalb von sieben Tagen nach der vorherigen vollständigen Synchronisierung versucht wird, aktualisiert Intune nur Seriennummern, die nicht bereits in Intune aufgeführt sind.
   -    Synchronisierungsanforderungen müssen innerhalb von 15 Minuten abgeschlossen sein. Während dieser Zeit oder bis zum erfolgreichen Erfüllen der Anforderung wird die Schaltfläche **Synchronisieren** deaktiviert.

>[!NOTE]
>Sie können auch über das Blatt **Geräte des Registrierungsprogramms** Apple School Manager-Seriennummern zu Geräten zuweisen.

## <a name="assign-a-profile-to-devices"></a>Zuweisen eines Profils zu Geräten
Apple School Manager-Geräten, die von Intune verwaltet werden, muss vor der Registrierung ein Registrierungsprofil zugewiesen werden.

1. Wählen Sie im Intune-Portal die Option **Geräteregistrierung** > **Apple-Registrierung** und dann **Profile des Registrierungsprogramms** aus.
2. Wählen Sie aus der Liste **Profile des Registrierungsprogramms** das Profil aus, das den Geräten zugewiesen werden soll, und wählen Sie anschließend **Gerätezuweisungen** aus.

 ![Gerätezuweisungen mit ausgewählter Option „Zuweisen“.](./media/enrollment-program-device-assign.png)

3. Klicken Sie auf **Zuweisen** und dann auf die Apple School Manager-Geräte, denen dieses Profil zugewiesen werden soll. Sie können die Ansicht nach verfügbaren Geräten filtern:
  - **Nicht zugewiesen**
  - **Beliebig**
  - **&lt;Profilname&gt;**
4. Wählen Sie die Geräte aus, die zugewiesen werden sollen. Mit dem Kontrollkästchen oberhalb der Spalte können bis zu 1.000 gelistete Geräte ausgewählt werden. Klicken Sie auf **Zuweisen**. Um mehr als 1000 Geräte zu registrieren, wiederholen Sie die Zuweisungsschritte, bis allen Geräten ein Registrierungsprofil zugewiesen ist.

  ![Schaltfläche „Zuweisen“ zum Zuweisen des Profils des Registrierungsprogramms in Intune](media/dep-profile-assignment.png)

## <a name="distribute-devices-to-users"></a>Verteilen von Geräten an Benutzer

Ihre unternehmenseigenen Geräte können jetzt an Benutzer verteilt werden. Wenn ein iOS-Apple School Manager-Gerät eingeschaltet wird, wird es für die Verwaltung durch Intune registriert. Wenn das Gerät aktiviert wurde und verwendet wird, kann das Profil erst angewendet werden, wenn das Gerät auf die Werkseinstellungen zurückgesetzt wird.
