---
title: "Apple DEP-Verwaltung für iOS-Geräte"
description: "Stellen Sie ein Registrierungsprofil bereit, das über das iOS-Programm zur Geräteregistrierung (Device Enrollment Program, DEP) erworbene iOS-Geräte drahtlos registriert, damit Sie Apple-Geräte verwalten können."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 885e3f0608cd367cb23658c342451a4a56e5474d
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="enroll-corporate-owned-device-enrollment-program-ios-devices"></a>Registrieren unternehmenseigener iOS-Geräte mithilfe des Programm zur Geräteregistrierung (Device Enrollment Program, DEP)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune kann ein Registrierungsprofil bereitstellen, das über das Programm zur Geräteregistrierung (Device Enrollment Program, DEP) erworbene iOS-Geräte drahtlos registriert. Das Registrierungspaket kann Setup-Assistent-Optionen für das Gerät enthalten.

>[!NOTE]
>Die Registrierung mit DEP (Device Enrollment Program) kann nicht mit dem [Geräteregistrierungs-Manager](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) verwendet werden.
>Wenn Benutzer iOS-Geräte registrieren (d.h.die Unternehmensportal-App verwenden) und die Seriennummer dieser Geräte dann importiert und einem DEP-Profil zugewiesen werden, wird die Registrierung des Geräts in Intune wieder rückgängig gemacht.

## <a name="prerequisites-for-enrolling-ios-devices-by-using-apple-dep-management"></a>Voraussetzungen für die Anmeldung von iOS-Geräten mithilfe der DEP-Verwaltung für Apple

- [Installieren eines APNS-Zertifikats](set-up-ios-and-mac-management-with-microsoft-intune.md)

- Ihre Organisation muss Apple-DEP beitreten und Geräte über dieses Programm beziehen. Details zu diesem Prozess finden Sie unter:  [https://deploy.apple.com](https://deploy.apple.com). Das Programm bietet den Vorteil, dass Geräte eingerichtet werden können, ohne dass ein USB-Kabel für die Verbindung jedes Geräts mit einem Computer verwendet werden muss.

- Bevor Sie unternehmenseigene iOS-Geräte mit DEP registrieren können, benötigen Sie ein DEP-Token von Apple. Mit diesem Token kann Intune Informationen zu DEP-Geräten synchronisieren, die Ihrem Unternehmen gehören. Damit kann Intune außerdem Registrierungsprofile an Apple übermitteln und diesen Profile Geräte zuweisen.

## <a name="steps-to-enroll-ios-devices-by-using-apple-dep-management"></a>Schritte zum Anmelden von iOS-Geräten mithilfe der DEP-Verwaltung für Apple

In den folgenden Schritten wird erläutert, wie Sie iOS-Geräte am „Tag 0“ mithilfe der Apple-DEP-Verwaltung registrieren. Da Geräte zu Ihrer Organisation hinzugefügt und auch wieder aus dieser entfernt werden, werden Sie wahrscheinlich einige dieser Schritte wiederholen, z.B. das Hinzufügen und Entfernen von Seriennummern, so wie unten beschrieben.

### <a name="get-an-encryption-key"></a>Abrufen eines Verschlüsselungsschlüssels

1. Öffnen Sie als Administrator die [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com), wechseln Sie zu **Verwaltung** &gt; **Verwaltung mobiler Geräte** &gt; **iOS** &gt; **Programm zur Geräteregistrierung**, und wählen Sie anschließend **Verschlüsselungsschlüssel herunterladen** aus.

2. Speichern Sie die Verschlüsselungsschlüsseldatei (PEM) lokal. Die PEM-Datei wird verwendet, um ein Vertrauensstellungszertifikat vom Apple Device Enrollment Program-Portal anzufordern.

![Abrufen eines Tokens für Geräteregistrierungsprogramm](../media/dev-sa-ios-dep.png)

### <a name="get-a-device-enrollment-program-token"></a>Abrufen eines Device Enrollment Program-Tokens

1. Wechseln Sie zum [Portal des Programms zur Geräteregistrierung](https://deploy.apple.com) (https://deploy.apple.com), und melden Sie sich mit Ihrer Unternehmens-Apple-ID an. Diese Apple-ID muss später verwendet werden, um Ihr DEP-Token zu erneuern.

2.  Wechseln Sie im Portal des Programms zur Geräteregistrierung zu **Programm zur Geräteregistrierung** &gt; **Server verwalten**, und wählen Sie anschließend **MDM-Server hinzufügen** aus.

3.  Geben Sie den **MDM-Servernamen** ein, und wählen Sie anschließend **Weiter** aus. Der Servername dient als Referenz zum Identifizieren des MDM-Servers (mobile device management, Verwaltung mobiler Geräte). Es handelt sich nicht um den Namen oder die URL des Microsoft Intune-Servers.

4.  Das Dialogfeld **&lt;Servername&gt; hinzufügen** wird geöffnet. Wählen Sie **Datei auswählen** aus, um die PEM-Datei hochzuladen, und wählen Sie anschließend **Weiter** aus.

5.  Im Dialogfeld **&lt;Servername&gt; hinzufügen** wird der Link **Ihr Servertoken** angezeigt. Laden Sie die Servertokendatei (.p7m) auf Ihren Computer herunter, und wählen Sie anschließend **Fertig** aus.

   Diese Zertifikatdatei (.p7m) wird verwendet, um eine Vertrauensstellung zwischen dem Intune- und Apple Device Enrollment Program-Server herzustellen.

### <a name="add-the-dep-token-to-intune"></a>Hinzufügen des DEP-Tokens zu Intune

1. Wechseln Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) zu **Verwaltung** &gt; **Verwaltung mobiler Geräte** &gt; **iOS** &gt; **Programm zur Geräteregistrierung**.

2. Wählen Sie **DEP-Token hochladen** aus. **Wechseln Sie** zur Zertifikatdatei (.p7m), geben Sie Ihre **Apple-ID**ein, und wählen Sie anschließend **Hochladen** aus.

### <a name="add-the-corporate-device-enrollment-policy"></a>Hinzufügen der Corporate Device Enrollment-Richtlinie

1. Wechseln Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) zu **Richtlinie** &gt; **Unternehmensgeräteregistrierung**, und wählen Sie anschließend **Hinzufügen** aus.

2. Geben Sie **allgemeine** Details ein, wie z.B. **Name** und **Beschreibung**. Geben Sie außerdem an, ob die dem Profil zugeordneten Geräte zu einem Benutzer oder einer Gruppe gehören:

   - **Benutzeraffinität anfordern**: Das Gerät muss während der ersten Installation einem Benutzer zugewiesen werden, bevor es dazu berechtigt sein kann, im Namen dieses Benutzers auf Unternehmensdaten und -E-Mails zuzugreifen. **Benutzeraffinität** muss für DEP-verwaltete Geräte eingerichtet werden, die Benutzern gehören und das Unternehmensportal verwenden müssen (um Apps zu installieren). Mehrstufige Authentifizierung (Multifactor authentication, MFA) funktioniert nicht während der Registrierung auf DEP-Geräten mit Benutzeraffinität. Nach der Registrierung funktioniert die MFA auf diesen Geräten wie erwartet. Neue Benutzer, die bei der ersten Anmeldung ihr Kennwort ändern müssen, können während der Registrierung auf DEP-Geräten nicht aufgefordert werden. Außerdem werden Benutzer, deren Passwörter abgelaufen sind, während der Registrierung nicht aufgefordert, ihr Kennwort zurückzusetzen; sie müssen ihr Kennwort von einem anderen Gerät aus zurücksetzen.

    >[!NOTE]
    >Für DEP mit Benutzeraffinität muss der [Endpunkt WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints) aktiviert sein, um Benutzertoken anzufordern. [Erfahren Sie mehr über WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

   - **Keine Benutzeraffinität**: Das Gerät ist keinem Benutzer zugeordnet. Verwenden Sie diese Zuweisung für Geräte, die Aufgaben ohne den Zugriff auf lokale Benutzerdaten ausführen. Apps, die eine Benutzerzugehörigkeit erfordern, einschließlich der Unternehmensportal-App, die für die Installation branchenspezifischer Apps verwendet wird, funktionieren nicht.

   Sie können auch **Geräte folgender Gruppe zuweisen**. Wählen Sie **Auswählen...** aus, um eine Gruppe auszuwählen.

   > [!Important]
   > Gruppenzuweisungen werden von Intune zu Azure Active Directory verschoben. Sobald Ihr Intune-Konto die anwendbaren Updates erhält, wird Ihnen nicht mehr die Option **Geräte folgender Gruppe zuweisen** angezeigt. [Erfahren Sie mehr](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune#changes-to-intune-group-assignments).

3. Aktivieren Sie **DEP-Einstellungen für diese Richtlinie konfigurieren**, um DEP zu unterstützen.

      ![Bereich „Setup-Assistent“](../media/pol-sa-corp-enroll.png)

   Die folgenden Einstellungen sind für DEP-verwaltete Geräte verfügbar:

   - **Abteilung**: Wird angezeigt, wenn Benutzer während der Aktivierung auf **Info zur Konfiguration** tippen
   - **Supportrufnummer**: Wird angezeigt, wenn der Benutzer während der Aktivierung auf die Schaltfläche **Hilfe erforderlich** klickt
   - **Vorbereitungsmodus**: Wird während der Aktivierung festgelegt und kann ohne Zurücksetzen des Geräts auf die Werkseinstellungen nicht geändert werden:
       - **Nicht überwacht**: Verwaltungsfunktionen sind eingeschränkt.
       - **Überwacht**: Ermöglicht weitere Verwaltungsfunktionen und deaktiviert standardmäßig die Aktivierungssperre.
   - **Registrierungsprofil für Gerät sperren**: Wird während der Aktivierung festgelegt und kann ohne Zurücksetzen des Geräts auf die Werkseinstellungen nicht geändert werden
       - **Deaktivieren** – Das Verwaltungsprofil kann aus dem Menü **Einstellungen** entfernt werden.
       - **Aktivieren**: (Erfordert **Preparation Mode** (Vorbereitungsmodus) = **Supervised** (Überwacht)) Deaktiviert die Menüoption „iOS-Einstellungen“ zum Entfernen des Verwaltungsprofils.
   - **Setup-Assistent-Optionen**: Diese optionalen Einstellungen können später im iOS-Menü **Einstellungen** eingerichtet werden.
        - **Kennung** – Aufforderung zur Eingabe der Kennung während der Aktivierung. Fordern Sie immer eine Kennung an, es sei denn, das Gerät und der Zugriff darauf werden auf andere Weise geschützt (d.h. im Kioskmodus zum Einschränken des Geräts auf eine App).
       - **Standortdienste** – Falls aktiviert, fragt der Setup-Assistent ab, ob der Diensts aktiviert werden soll.
       - **Wiederherstellen**: Falls aktiviert, fordert der Setup-Assistent die iCloud-Sicherung während der Aktivierung an.
       - **Apple-ID**: Falls aktiviert, fordert iOS Benutzer zur Angabe einer Apple-ID an, wenn Intune versucht, eine App ohne eine ID zu installieren. Eine Apple ID ist erforderlich, um iOS App Store-Apps herunterzuladen, einschließlich Apps, die von Intune installiert wurden.
       - **Geschäftsbedingungen**: Falls aktiviert, fordert der Setup-Assistenten Benutzer auf, die Apple-Geschäftsbedingungen während der Aktivierung zu akzeptieren.
       - **Touch ID**: Falls aktiviert, fordert der Setup-Assistent zur Ausführung dieses Dienst während der Aktivierung auf.
       - **Apple Pay**: Falls aktiviert, fordert der Setup-Assistent zur Ausführung dieses Dienst während der Aktivierung auf.
       - **Zoom**: Falls aktiviert, fordert der Setup-Assistent zur Ausführung dieses Dienst während der Aktivierung auf.
       - **Siri** – Falls aktiviert, fordert der Setup-Assistent zur Ausführung dieses Dienst während der Aktivierung auf
       - **Diagnosedaten an Apple senden**: Falls aktiviert, fordert der Setup-Assistent diesen Dienst während der Aktivierung an.
   -  **Zusätzliche Verwaltung durch Apple Configurator aktivieren**: Auf **Nicht zulassen** festlegen, um das Synchronisieren von Dateien mit iTunes oder die Verwaltung per Apple Configurator zu verhindern. Es empfiehlt sich, **Nicht zulassen** auszuwählen, weitere Konfigurationen aus Apple Configurator zu exportieren und diese anschließend als benutzerdefiniertes iOS-Konfigurationsprofil per Intune bereitzustellen, anstatt diese Einstellung zu wählen, um eine manuelle Bereitstellung mit oder ohne Zertifikat zuzulassen.
       - **Nicht zulassen**: Verhindert, dass das Gerät per USB kommuniziert (Verbindung wird deaktiviert).
       - **Zulassen**: Erlaubt einem Gerät das Kommunizieren über eine USB-Verbindung mit jedem PC oder Mac
       - **Zertifikat anfordern**: Ermöglicht eine Verbindung mit einem Mac, indem ein Zertifikat in das Registrierungsprofil importiert wird.

### <a name="assign-the-profile-to-devices"></a>Zuweisen des Profils zu Geräten

1. Wechseln Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) zu **Richtlinie** &gt; **Unternehmensgeräteregistrierung**, und wählen Sie anschließend **Zuweisen** aus.

2. Wählen sie das Gerät aus, dem Sie das von Ihnen erstellte Profil zuweisen möchten. Sie können **Alle Geräte** oder bestimmte Geräte auswählen, und dann **Hinzufügen** auswählen.

> [!Important]
> Gegenwärtig können Sie in Intune noch ein „Standardprofil“ für die Geräteregistrierung angeben. Das bedeutet, dass neue Seriennummern automatisch diesem Standardprofil zugewiesen werden, wenn Sie sie mit dem Apple DEP-Dienst synchronisieren. Wenn Ihr Mandant demnächst zum Azure-Portal migriert wird, können Sie kein Standardprofil mehr festlegen, und Seriennummern werden nicht mehr automatisch diesem Profil zugewiesen. Sie müssen die Seriennummern stattdessen einem bestimmten Profil zuweisen. [Erfahren Sie mehr](https://docs.microsoft.com/intune/device-enrollment-program-enroll-ios)

### <a name="assign-dep-devices-for-management"></a>Zuweisen von DEP-Geräten zur Verwaltung

1. Wechseln Sie zum [Device Enrollment Program-Portal](https://deploy.apple.com) (https://deploy.apple.com), und melden Sie sich mit der Apple-ID Ihres Unternehmens an.

2. Wechseln Sie zu **Bereitstellungsprogramm** &gt; **Programm zur Geräteregistrierung** &gt; **Geräte verwalten**.

3. Geben Sie an, wie Sie **Geräte wählen**, fügen Sie Geräteinformationen hinzu, und geben Sie die Details zum Gerät wie **Seriennummer**und **Bestellnummer**an, oder **laden Sie eine CSV-Datei hoch**.

4. Wählen Sie **Zu Server zuweisen** aus. Wählen Sie den für Microsoft Intune angegebenen &lt;Servernamen&gt; und anschließend **OK** aus.

### <a name="synchronize-dep-managed-devices"></a>Synchronisieren von DEP-verwalteten Geräten

In diesem Schritt werden die Geräte mit dem Apple DEP-Dienst synchronisiert und in der Intune-Konsole angezeigt.

1. Öffnen Sie als Administrator die [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com), wechseln Sie zu **Verwaltung** &gt; **Verwaltung mobiler Geräte** &gt; **iOS** &gt; **Programm zur Geräteregistrierung**, und wählen Sie anschließend **Jetzt synchronisieren** aus. Eine Synchronisierungsanforderung wird an Apple gesendet.

2. Um mit DEP verwaltete Geräte nach der Synchronisierung anzuzeigen, navigieren Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) zu **Gruppen** &gt; **Alle Geräte** &gt; **Vorabregistrierte Unternehmensgeräte** &gt; **Nach iOS-Seriennummer**. Im Arbeitsbereich **Nach iOS-Seriennummer** wird der **Status** verwalteter Geräte als „Nicht kontaktiert“ angezeigt, bis das Gerät eingeschaltet und der Setup-Assistent darauf ausgeführt wird.

   Zur Einhaltung der Apple-Bedingungen für zulässigen DEP-Datenverkehr erzwingt Intune die folgenden Einschränkungen:

   - Eine vollständige DEP-Synchronisation kann nicht öfter als einmal alle sieben Tage erfolgen. Während einer vollständigen Synchronisierung aktualisiert Intune jede Seriennummer, die Intune von Apple zugewiesen wurde, und zwar unabhängig davon, ob die Seriennummer vorher synchronisiert wurde oder nicht. Wenn eine vollständige Synchronisierung innerhalb von sieben Tagen nach der vorherigen vollständigen Synchronisierung versucht wird, aktualisiert Intune nur Seriennummern, die nicht bereits in Intune aufgeführt sind.

   - Synchronisierungsanforderungen müssen binnen 10 Minuten abgeschlossen werden. Während dieser Zeit oder bis zum erfolgreichen Erfüllen der Anforderung wird die Schaltfläche **Synchronisieren** deaktiviert.

### <a name="distribute-devices-to-users"></a>Verteilen von Geräten an Benutzer

Ihre firmeneigenen Geräte können jetzt an Benutzer verteilt werden. Wenn ein iOS-Gerät eingeschaltet wird, wird es für die Verwaltung durch Intune registriert. Der Gerätegrenzwert des Benutzers gilt für von DEP verwaltete Geräte.

>[!NOTE]
>Wenn ein Benutzer versucht, ein DEP-Geräte zu registrieren, der Gerätegrenzwert aber bereits überschritten ist, schlägt die Registrierung fehl, ohne das der Benutzer Warnmeldungen erhält.

## <a name="changes-to-intune-group-assignments"></a>Änderungen an den Intune-Gruppenzuweisungen

Ab April 2017 werden Gerätegruppen in Azure Active Directory verschoben. Nach dieser Änderung und dem Übergang zu Azure Active Directory-Gruppen wird die Gruppenzuweisung nicht länger in den Optionen des Unternehmensregistrierungsprofils angezeigt. Da diese Änderung über mehrere Monate hinweg umgesetzt wird, wird Ihnen die Änderung möglicherweise nicht sofort angezeigt. Nach dem Wechsel zum neuen Portal können die Zuweisungen dynamischer Gerätegruppen basierend auf dem Namen des Unternehmensregistrierungsprofils definiert werden.

Bei der Migration wird für jede Intune-Gerätegruppe, die durch ein Profil für die Unternehmensgeräteregistrierung vorab zugewiesen ist, eine entsprechende dynamische Gerätegruppe in Azure AD auf Grundlage des Profilnamens der Unternehmensgeräteregistrierung erstellt. Neue Profilnamen besitzen das Format *EnrollmentProfile:&lt;Name des verknüpften Profils&gt;*. Mit diesem Vorgang wird sichergestellt, dass Geräte, die bereits einer Gerätegruppe zugewiesen wurden, automatisch mit bereitgestellter Richtlinie und bereitgestellten Apps in der Gruppe registriert werden.

Diese automatische Gruppenerstellung erfolgt nur einmal während der Migration von Gruppen. Nach der Migration müssen Intune-Administratoren über das Azure-Portal Gruppen erstellen. Informationen dazu, wie sich dies auf die Registrierung von iOS-Unternehmensgeräten auswirkt, finden Sie unter [Changes to Automatic Grouping for Corporate Pre-enrolled iOS Devices](https://blogs.technet.microsoft.com/intunesupport/2017/04/19/changes-to-automatic-grouping-for-corporate-pre-enrolled-ios-devices/) (Änderungen der automatischen Gruppierung für vorabregistrierte iOS-Unternehmensgeräte).

Sie können auch mehr über das [Verwalten von Gruppen in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/) erfahren.

### <a name="see-also"></a>Siehe auch
[Voraussetzungen für die Registrierung von Geräten](prerequisites-for-enrollment.md)
