---
title: Behandlung von Problemen bei der Geräteregistrierung
titleSuffix: Microsoft Intune
description: Vorschläge zur Behandlung von Problemen bei der Geräteregistrierung in Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/09/2018
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6982ba0e-90ff-4fc4-9594-55797e504b62
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 06a8bd8d0a46b7d7eed8efb4cb8b4c2d4e21f77d
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61509230"
---
# <a name="troubleshoot-device-enrollment-in-microsoft-intune"></a>Behandlung von Problemen bei der Geräteregistrierung in Microsoft Intune

Dieser Artikel enthält Vorschläge zur Behandlung von Problemen bei der [Geräteregistrierung](device-enrollment.md). Wenn sich das Problem mit diesen Informationen nicht beheben lässt, finden Sie unter [Anfordern von Support für Microsoft Intune](get-support.md) weitere Möglichkeiten, Hilfe zu erhalten.


## <a name="initial-troubleshooting-steps"></a>Erste Schritte bei der Problembehandlung

Bevor Sie mit der Problembehandlung beginnen, stellen Sie sicher, dass Intune ordnungsgemäß konfiguriert wurde, um die Registrierung zu ermöglichen. Informationen zu diesen Konfigurationsanforderungen finden Sie unter:

-   [Vorbereiten der Registrierung von Geräten in Microsoft Intune](setup-steps.md)
-   [Einrichten der iOS- und Mac-Geräteverwaltung](ios-enroll.md)
-   [Einrichten der Windows-Geräteverwaltung](windows-enroll.md)
-   [Einrichten der Android-Geräteverwaltung](android-enroll.md) – Keine weiteren Schritte erforderlich

Sie können auch sicherstellen, dass Uhrzeit und Datum auf dem Gerät des Benutzers korrekt festgelegt werden:

1. Starten Sie das Gerät neu.
2. Stellen Sie sicher, dass Uhrzeit und Datum auf die Zeitzone des Endbenutzers relativ zur GMT-Zeit (+ oder - 12 Stunden) eingestellt sind.
3. Deinstallieren Sie das Intune-Unternehmensportal (falls zutreffend), und installieren Sie es wieder.

Ihre Benutzer verwalteter Geräte können Registrierungs- und Diagnoseprotokolle erfassen, die Sie überprüfen können. Benutzeranleitungen zur Erfassung der Protokolle finden Sie unter:

- [Senden von Android-Registrierungsfehlern an Ihren IT-Administrator](https://docs.microsoft.com/intune-user-help/send-enrollment-errors-to-your-it-admin-android)
- [Send iOS errors to your IT admin (Senden von iOS-Fehlern an Ihren IT-Administrator)](https://docs.microsoft.com/intune-user-help/send-errors-to-your-it-admin-ios)


## <a name="general-enrollment-issues"></a>Allgemeine Probleme bei der Registrierung
Diese Probleme können auf allen Geräteplattformen auftreten.

### <a name="device-cap-reached"></a>Gerätekapazität erreicht
**Problem:** Benutzer erhalten während der Registrierung eine Fehlermeldung (z.B. **Unternehmensportal vorübergehend nicht verfügbar**), und die Datei „DMPdownloader.log“ in Configuration Manager enthält den Fehler **DeviceCapReached**.

**Lösung:**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>Überprüfen Sie die Anzahl der registrierten und zulässigen Geräte.

Überprüfen Sie, dass dem Benutzer nicht mehr als die zulässige Zahl an Geräten zugewiesen wurde. Gehen Sie dafür wie folgt vor:

1. Navigieren Sie in Intune zu **Geräteregistrierung** > **Registrierungseinschränkungen** > **Einschränkungen zum Gerätelimit**. Achten Sie auf den Wert in der Spalte **Gerätelimit**.

2. Klicken Sie in Intune auf **Benutzer** > **Alle Benutzer**, wählen Sie den Benutzer aus, und klicken Sie anschließend auf **Geräte**. Überprüfen Sie die Anzahl der Geräte.

3. Wenn die Anzahl der registrierten Geräte des Benutzers bereits das Gerätelimit erreicht hat, kann er keine weiteren Geräte registrieren, bis eine der folgenden Aktionen durchgeführt wird:
    - [Vorhandene Geräte werden entfernt](devices-wipe.md) oder
    - Sie erhöhen das Gerätelimit, indem Sie die [Geräteeinschränkungen anpassen](enrollment-restrictions-set.md#set-device-limit-restrictions).

Entfernen Sie alte Geräteeinträge, um zu verhindern, dass das Limit erreicht wird.

> [!NOTE]
> 
> Sie können das Erreichen der Kapazitätsgrenze für Geräteregistrierungen vermeiden, indem Sie das Konto des Geräteregistrierungs-Managers verwenden, wie unter [Registrieren unternehmenseigener Geräte mit dem Geräteregistrierungs-Manager in Microsoft Intune](device-enrollment-manager-enroll.md) beschrieben.
> 
> Ein Benutzerkonto das dem Konto „Geräteregistrierungs-Manager“ hinzugefügt wird, kann die Registrierung nicht abschließen, wenn die bedingte Zugriffsrichtlinie für diese spezielle Benutzeranmeldung erzwungen wird.

### <a name="company-portal-temporarily-unavailable"></a>Unternehmensportal vorübergehend nicht verfügbar
**Problem:** Benutzer erhalten auf dem Gerät die Fehlermeldung **Unternehmensportal vorübergehend nicht verfügbar**.

**Lösung:**

1.  Entfernen Sie die Intune-Unternehmensportal-App von dem Gerät.

2.  Öffnen Sie auf dem Gerät den Browser, navigieren Sie zu [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com), und versuchen Sie sich als Benutzer anzumelden.

3.  Wenn sich der Benutzer nicht anmelden kann, sollte er ein anderes Netzwerk ausprobieren.

4.  Wenn auch dies fehlschlägt, überprüfen Sie, ob die Anmeldeinformationen des Benutzers korrekt mit Azure Active Directory synchronisiert wurden.

5.  Wenn sich der Benutzer erfolgreich angemeldet hat, werden Sie auf einem iOS-Gerät aufgefordert, die Intune-Unternehmensportal-App zu installieren und sich zu registrieren. Auf einem Android-Geräten müssen Sie die Intune-Unternehmensportal-App manuell installieren, wonach Sie die Registrierung erneut versuchen können.

### <a name="mdm-authority-not-defined"></a>MDM-Autorität nicht definiert
**Problem:** Sie erhalten die Fehlermeldung **MDM-Autorität nicht definiert**.

**Lösung:**

1.  Achten Sie darauf, dass die MDM-Autorität [entsprechend festgelegt wurde](mdm-authority-set.md).
    
2.  Überprüfen Sie, ob die Anmeldeinformationen des Benutzers korrekt mit Azure Active Directory synchronisiert wurden. Sie können überprüfen, ob die UPN des Benutzers mit den Active Directory-Informationen im Microsoft 365 Admin Center übereinstimmt.
    Wenn der UPN nicht mit den Active Directory-Informationen übereinstimmt:

    1.  Deaktivieren Sie DirSync auf dem lokalen Server.

    2.  Löschen Sie den nicht übereinstimmenden Benutzer aus der Benutzerliste **Intune-Kontoportal** .

    3.  Warten Sie etwa eine Stunde, damit der Azure-Dienst die fehlerhaften Daten entfernen kann.

    4.  Aktivieren Sie DirSync erneut, und überprüfen Sie, ob der Benutzer jetzt ordnungsgemäß synchronisiert ist.

3.  In einem Szenario, in dem Sie System Center Configuration Manager mit Intune verwenden, stellen Sie sicher, dass der Benutzer eine gültige Cloudbenutzer-ID besitzt:

    1.  Öffnen Sie SQL Management Studio.

    2.  Stellen Sie eine Verbindung mit der geeigneten Datenbank her.

    3.  Öffnen Sie den Datenbankenordner, und suchen und öffnen Sie den Ordner **CM_DBName**, wobei „DBName“ der Name der Kundendatenbank ist.

    4.  Klicken Sie im oberen Bereich auf **Neue Abfrage**, und führen Sie die folgenden Abfragen aus:

        -   Zum Anzeigen aller Benutzer: `select * from [CM_ DBName].[dbo].[User_DISC]`

        -   Zum Anzeigen bestimmter Benutzer verwenden Sie die folgende Abfrage, wobei „%testuser1%“ ein Platzhalter für username@domain.com ist, den Sie nachschlagen möchten: `select * from [CM_ DBName].[dbo].[User_DISC] where User_Principal_Name0 like '%testuser1%'`

        Wählen Sie nach dem Schreiben der Abfrage die Option **Ausführen** aus.
        Nachdem die Ergebnisse zurückgegeben wurden, suchen Sie nach der Cloudbenutzer-ID.  Wenn Sie keine ID finden, ist der Benutzer nicht für die Verwendung von Intune lizenziert.

### <a name="unable-to-create-policy-or-enroll-devices-if-the-company-name-contains-special-characters"></a>Erstellen einer Richtlinie oder Registrieren von Geräten ist nicht möglich, wenn der Firmenname Sonderzeichen enthält
**Problem:** Sie können keine Richtlinie erstellen bzw. keine Geräte registrieren.

**Lösung:** Entfernen Sie im [Microsoft 365 Admin Center](https://admin.microsoft.com/) die Sonderzeichen aus dem Firmennamen, und speichern Sie die Unternehmensinformationen.

### <a name="unable-to-sign-in-or-enroll-devices-when-you-have-multiple-verified-domains"></a>Anmelden oder Registrieren von Geräten ist nicht möglich, wenn Sie mehrere überprüfte Domänen haben
**Problem:** Dieses Problem kann auftreten, wenn Sie eine zweite verifizierte Domäne zu Ihrer ADFS-Instanz hinzufügen. Benutzer mit dem Benutzerprinzipalnamen-Suffix (UPN) der zweiten Domäne können sich möglicherweise nicht bei Portalen anmelden oder Geräte registrieren.


<strong>Lösung:</strong> Kunden von Microsoft Office 365 müssen für jedes Suffix eine separate Instanz des AD FS 2.0-Verbunddienst bereitstellen, wenn Folgendes zutrifft:
- Sie verwenden das einmalige Anmelden (SSO) über AD FS 2.0 und
- verfügen über mehrere Domänen der obersten Ebene für UPN-Suffixe des Benutzers in ihrer Organisation (z. B. @contoso.com oder @fabrikam.com).


Ein [Rollup für AD FS 2.0](http://support.microsoft.com/kb/2607496) funktioniert in Verbindung mit der Option <strong>SupportMultipleDomain</strong>, um den AD FS-Server zur Unterstützung dieses Szenarios zu aktivieren, ohne dass zusätzliche AD FS 2.0-Server erforderlich sind. Weitere Informationen finden Sie in diesem [Blog](https://blogs.technet.microsoft.uucom/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/).


## <a name="android-issues"></a>Android-Probleme

### <a name="android-enrollment-errors"></a>Android-Registrierungsfehler

In der folgenden Tabelle sind Fehler aufgeführt, die bei der Registrierung von Android-Geräten bei Intune auftreten können.

|Fehlermeldung|Problem|Lösung|
|---|---|---|
|**IT-Administrator muss eine Lizenz für den Zugriff zuweisen**<br>Ihr IT-Administrator hat Ihnen keinen Zugriff für die Verwendung dieser App erteilt. Wenden Sie sich an Ihren IT-Administrator, oder versuchen Sie es später erneut.|Das Gerät kann nicht registriert werden, da das Benutzerkonto nicht über die erforderliche Lizenz verfügt.|Bevor Benutzer ihre Geräte registrieren können, müssen Sie die nötigen Lizenzen zugewiesen bekommen. Diese Meldung bedeutet, dass der Benutzer den falschen Lizenztyp für die Autorität für die Verwaltung mobiler Geräte hat. Diese Fehlermeldung wird z. B. angezeigt, wenn die beiden folgenden Punkte zutreffen:<ol><li>Intune wurde als Autorität für die Verwaltung mobiler Geräte festgelegt.</li><li>Sie verwenden eine System Center 2012 R2 Configuration Manager-Lizenz.</li></ol>Weitere Informationen finden Sie unter [Zuweisen von Intune-Lizenzen zu Benutzerkonten](/intune/licenses-assign).|
|**Der IT-Administrator muss die MDM-Autorität festlegen**<br>Es sieht so aus, als hätte Ihr IT-Administrator keine MDM-Autorität festgelegt. Wenden Sie sich an Ihren IT-Administrator, oder versuchen Sie es später erneut.|Die Autorität für die Verwaltung mobiler Geräte wurde nicht festgelegt.|Die Autorität für die Verwaltung mobiler Geräte wurde in Intune festgelegt. Sehen Sie sich die Informationen zum [Festlegen der Autorität für die Verwaltung mobiler Geräte](/intune/mdm-authority-set) an.|


### <a name="devices-fail-to-check-in-with-the-intune-service-and-display-as-unhealthy-in-the-intune-admin-console"></a>Geräte können nicht beim Intune-Dienst eingecheckt werden und werden als in der Intune-Administratorkonsole als „Fehlerhaft“ angezeigt.
**Problem:** Einige Samsung-Geräte, auf denen die Android-Versionen 4.4.x und 5.x ausgeführt werden, beenden den Vorgang zum Einchecken beim Intune-Dienst. Für nicht eingecheckte Geräte gilt Folgendes:

- Sie können keine Richtlinien, Apps und Remotebefehle vom Intune-Dienst empfangen.
- Sie werden in der Administratorkonsole mit dem Status **Fehlerhaft** angezeigt.
- Benutzer, die über Richtlinien für den bedingten Zugriff geschützt werden, verlieren möglicherweise ihren Zugriff auf Unternehmensressourcen.

Samsung Smart Manager-Software, die auf bestimmten Samsung-Geräten vorinstalliert ist, kann das Intune-Unternehmensportal und die zugehörigen Komponenten deaktivieren. Wenn sich das Unternehmensportal in einem deaktivierten Zustand befindet, kann es nicht im Hintergrund ausgeführt werden und nicht mit dem Intune-Dienst kommunizieren.

**Lösung 1**:

Weisen Sie Ihre Benutzer an, die Unternehmensportal-App manuell zu starten. Nach dem App-Neustart wird das Gerät beim Intune-Dienst eingecheckt.

> [!IMPORTANT]
> Das manuelle Öffnen der Unternehmensportal-App ist eine vorübergehende Lösung, weil die Unternehmensportal-App durch den Samsung Smart Manager erneut deaktiviert werden kann.

**Lösung 2**:

Weisen Sie Ihre Benutzer an, ein Upgrade auf Android 6.0 durchzuführen. Das Problem der Deaktivierung tritt auf Android 6.0-Geräten nicht auf. Um zu überprüfen, ob ein Update verfügbar ist, können Sie zu **Einstellungen** > **Geräteinformationen** > **Updates manuell herunterladen** wechseln und den Anweisungen folgen.

**Lösung 3**:

Wenn Lösung 2 nicht zur Behebung des Problems führt, führen Sie die folgenden Schritte aus, um die Unternehmensportal-App als Smart Manager-Ausnahme festzulegen:

1. Starten Sie die Smart Manager-App auf dem Gerät.

   ![Smart Manager-Symbol auf dem Gerät auswählen](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-icon.png)

2. Wählen Sie die Kachel **Akku** aus.

   ![Kachel „Akku“ auswählen](./media/troubleshoot-device-enrollment-in-intune/smart-manager-battery-tile.png)

3. Wählen Sie unter **App-Energiesparmodus** oder **App-Optimierung** die Option **Detail** aus.

   ![Option „Detail“ unter „App-Energiesparmodus“ oder „App-Optimierung“ auswählen](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-power-saving-detail.png)

4. Wählen Sie aus der Liste der Apps den Eintrag **Unternehmensportal** aus.

   ![Unternehmensportal aus der Liste der Apps auswählen](./media/troubleshoot-device-enrollment-in-intune/smart-manager-company-portal.png)

5. Wählen Sie **Deaktivieren** aus.

   ![Option „Deaktivieren“ im Dialogfeld „App-Optimierung“ auswählen](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-optimization-turned-off.png)

6. Vergewissern Sie sich unter **App-Energiesparmodus** oder **App-Optimierung**, dass das Unternehmensportal deaktiviert ist.

   ![Überprüfen, ob das Unternehmensportal deaktiviert ist](./media/troubleshoot-device-enrollment-in-intune/smart-manager-verify-comp-portal-turned-off.png)


### <a name="profile-installation-failed"></a>Fehler bei der Profilinstallation
**Problem:** Sie erhalten auf einem Android-Gerät die Fehlermeldung **Fehler bei der Profilinstallation**.

**Lösung:**

1.  Vergewissern Sie sich, dass dem Benutzer eine geeignete Lizenz für die Version des von Ihnen verwendeten Intune-Diensts zugewiesen wurde.

2.  Vergewissern Sie sich, dass das Gerät nicht bereits bei einem anderen MDM-Anbieter registriert ist.

3. Vergewissern Sie sich, dass auf dem Gerät noch kein Verwaltungsprofil installiert ist.

4.  Vergewissern Sie sich, dass Chrome für Android der Standardbrowser ist und dass Cookies aktiviert sind.

### <a name="android-certificate-issues"></a>Android-Zertifikatsprobleme

**Problem:** Benutzer erhalten die folgende Meldung auf ihrem Gerät: *Sie können sich nicht anmelden, da dem Gerät ein erforderliches Zertifikat fehlt.*

**Lösung 1**:

Der Benutzer kann das fehlende Zertifikat abrufen, indem er die Anweisungen unter [Auf Ihrem Gerät ist ein erforderliches Zertifikat nicht vorhanden](/intune-user-help/your-device-is-missing-a-required-certificate-android) befolgt. Wenn der Fehler weiterhin auftritt, versuchen Sie es mit Lösung 2.

**Lösung 2**:

Nach der Eingabe ihrer Unternehmensanmeldeinformationen und der Weiterleitung zur Verbundanmeldung wird den Benutzern möglicherweise noch der Fehler für das fehlende Zertifikat angezeigt. In diesem Fall kann der Fehler bedeuten, dass auf Ihrem AD FS-Server (Active Directory-Verbunddienste) ein Zwischenzertifikat fehlt.

Der Zertifikatsfehler tritt auf, weil Android-Geräte Zwischenzertifikate benötigen, die in eine [SSL-Server-Hello-Nachricht](https://technet.microsoft.com/library/cc783349.aspx) eingebunden werden müssen. Derzeit sendet eine standardmäßige AD FS-Serverinstallation oder eine AD FS-Proxyserverinstallation mit WAP nur das SSL-Zertifikat des AD FS-Diensts in der SSL-Server-Hello-Antwort auf eine SSL-Client-Hello-Nachricht.

Um das Problem zu beheben, importieren Sie die Zertifikate wie folgt in die persönlichen Zertifikate des Computers auf dem AD FS-Server oder den Proxys:

1.  Klicken Sie im AD FS oder in den Proxyservern mit der rechten Maustaste auf **Start**, und wählen Sie **Ausführen** > **certlm.msc**, um die Verwaltungskonsole für Zertifikate lokaler Computer zu starten.
2.  Erweitern Sie **Persönlich**, und wählen Sie **Zertifikate** aus.
3.  Suchen Sie das Zertifikat für Ihre Kommunikation mit dem AD FS-Dienst (ein öffentlich signiertes Zertifikat), und doppelklicken Sie darauf, um seine Eigenschaften anzuzeigen.
4.  Klicken Sie auf die Schaltfläche **Zertifizierungspfad**, um die übergeordneten Zertifikate des Zertifikats anzuzeigen.
5.  Wählen Sie in jedem übergeordneten Zertifikat die Option **Zertifikat anzeigen** aus.
6.  Klicken Sie auf **Details** > **In Datei kopieren**.
7.  Führen Sie die Anweisungen des Assistenten aus, um den öffentlichen Schlüssel des übergeordneten Zertifikats an den gewünschten Speicherort zu exportieren oder zu speichern.
8.  Klicken Sie mit der rechten Maustaste auf **Zertifikate** > **Alle Aufgaben** > **Importieren**.
9.  Befolgen Sie die Anweisungen des Assistenten, um das übergeordnete Zertifikat bzw. die übergeordneten Zertifikate in das Verzeichnis **Lokale Computer\Eigene Zertifikate\Zertifikate** zu importieren.
10. Starten Sie die AD FS-Server neu.
11. Wiederholen Sie die oben stehenden Schritte auf allen AD FS- und Proxyservern.

Um eine ordnungsgemäße Installation des Zertifikats zu gewährleisten, können Sie das auf der Seite [https://www.digicert.com/help/](https://www.digicert.com/help/) erhältliche Diagnosetool verwenden. Geben Sie unter **Serveradresse** den FQDN Ihres AD FS-Servers (IE: sts.contso.com) ein, und klicken Sie auf **Server überprüfen**.

**So überprüfen Sie, ob das Zertifikat richtig installiert wurde**

Die folgenden Schritte beschreiben nur eine von vielen Methoden und Tools, die Sie verwenden können, um zu überprüfen, ob das Zertifikat richtig installiert wurde.

1. Wechseln Sie zum [kostenlosen Digicert-Tool](ttps://www.digicert.com/help/).
2. Geben Sie den vollqualifizierten Domänennamen Ihres AD FS-Servers ein (z.B. sts.contoso.com), und wählen Sie **Server überprüfen** aus.

Wenn das Serverzertifikat ordnungsgemäß installiert wurde, werden in den Ergebnissen alle Häkchen angezeigt. Wenn das oben beschriebene Problem vorhanden ist, wird in den Abschnitten „Certificate Name Matches“ und „SSL Certificate is correctly Installed“ des Berichts ein rotes X angezeigt.


## <a name="ios-issues"></a>iOS-Probleme

### <a name="ios-enrollment-errors"></a>iOS-Registrierungsfehler
In der folgenden Tabelle sind Fehler aufgeführt, die bei der Registrierung von iOS-Geräten bei Intune auftreten können.

|Fehlermeldung|Problem|Lösung|
|-------------|-----|----------|
|NoEnrollmentPolicy|Keine Registrierungsrichtlinie gefunden|Vergewissern Sie sich, dass alle für die Registrierung erforderlichen Komponenten, wie der Apple Push Notification Service (APNs), eingerichtet wurden, und dass „iOS as a platform“ (iOS als Plattform) aktiviert ist. Anweisungen hierzu finden Sie unter [Einrichten der iOS- und Mac-Geräteverwaltung](ios-enroll.md).|
|DeviceCapReached|Es sind bereits zu viele mobile Geräte registriert.|Der Benutzer muss eines seiner derzeit registrierten mobilen Geräte aus dem Unternehmensportal entfernen, bevor ein weiteres mobiles Gerät registriert werden kann. Sehen Sie sich die Anweisungen für Ihren Gerätetyp an: [Android](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android), [iOS](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-ios), [Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-windows).|
|APNSCertificateNotValid|Es liegt ein Problem mit dem Zertifikat vor, über das die Kommunikation Ihres mobilen Geräts mit Ihrem Unternehmensnetzwerk ermöglicht wird.<br /><br />|Über den Apple Push Notification Service (APNs) ist der Zugriff auf registrierte iOS-Geräte möglich. Die Registrierung schlägt fehl und diese Meldung wird angezeigt, wenn:<ul><li>Die Schritte zum Abrufen eines APNs-Zertifikats nicht abgeschlossen wurden oder</li><li>Das Zertifikat des APNs abgelaufen ist.</li></ul>Überprüfen Sie die Informationen über das Einrichten von Benutzern unter [Synchronisieren von Active Directory und Hinzufügen von Benutzern zu Intune](users-add.md) und [Erstellen von Gruppen zum Organisieren von Benutzern und Geräten](groups-add.md).|
|AccountNotOnboarded|Es liegt ein Problem mit dem Zertifikat vor, über das die Kommunikation Ihres mobilen Geräts mit Ihrem Unternehmensnetzwerk ermöglicht wird.<br /><br />|Über den Apple Push Notification Service (APNs) ist der Zugriff auf registrierte iOS-Geräte möglich. Die Registrierung schlägt fehl und diese Meldung wird angezeigt, wenn:<ul><li>Die Schritte zum Abrufen eines APNs-Zertifikats nicht abgeschlossen wurden oder</li><li>Das Zertifikat des APNs abgelaufen ist.</li></ul>Weitere Informationen finden Sie unter [Einrichten der iOS- und Mac-Geräteverwaltung](ios-enroll.md).|
|DeviceTypeNotSupported|Der Benutzer hat möglicherweise versucht, eine Registrierung mit einem Nicht-iOS-Gerät auszuführen. Der Mobilgerättyp, den Sie versuchen zu registrieren, wird nicht unterstützt.<br /><br />Stellen Sie sicher, dass auf dem Gerät mindestens Version 8.0 von iOS ausgeführt wird.<br /><br />|Stellen Sie sicher, dass auf dem Gerät des Benutzers mindestens die iOS-Version 8.0 ausgeführt wird.|
|UserLicenseTypeInvalid|Das Gerät kann nicht registriert werden, da das Benutzerkonto noch kein Mitglied einer erforderlichen Benutzergruppe ist.<br /><br />|Bevor Benutzer ihre Geräte registrieren können, müssen sie Mitglied der richtigen Benutzergruppe sein. Diese Meldung bedeutet, dass der Benutzer den falschen Lizenztyp für die Autorität für die Verwaltung mobiler Geräte hat. Diese Fehlermeldung wird z. B. angezeigt, wenn die beiden folgenden Punkte zutreffen:<ol><li>Intune wurde als Autorität für die Verwaltung mobiler Geräte festgelegt.</li><li>Sie verwenden eine System Center 2012 R2 Configuration Manager-Lizenz.</li></ol>Weitere Informationen finden Sie in den folgenden Artikeln:<br /><br />Weitere Informationen finden Sie unter [Einrichten der iOS- und Mac-Geräteverwaltung](ios-enroll.md) und im Abschnitt über das Einrichten von Benutzern in [Synchronisieren von Active Directory und Hinzufügen von Benutzern zu Intune](users-add.md) und unter [Erstellen von Gruppen zum Organisieren von Benutzern und Geräten](groups-add.md).|
|MdmAuthorityNotDefined|Die Autorität für die Verwaltung mobiler Geräte wurde nicht festgelegt.<br /><br />|Die Autorität für die Verwaltung mobiler Geräte wurde in Intune festgelegt.<br /><br />Überprüfen Sie Punkt 1 im Abschnitt „Schritt 6: Registrieren mobiler Geräte und Installieren einer App“ unter [Erste Schritte mit einer 30-Tage-Testversion von Microsoft Intune](free-trial-sign-up.md).|

### <a name="devices-are-inactive-or-the-admin-console-cant-communicate-with-them"></a>Geräte sind inaktiv oder die Verwaltungskonsole kann nicht mit ihnen kommunizieren.
**Problem:** iOS-Geräte sind nicht beim Intune-Dienst eingecheckt. Geräte müssen in regelmäßigen Abständen beim Dienst eingecheckt sein, um den Zugriff auf geschützte Unternehmensressourcen zu behalten. Für nicht eingecheckte Geräte gilt Folgendes:

- Sie können keine Richtlinien, Apps und Remotebefehle vom Intune-Dienst empfangen.
- Sie werden in der Administratorkonsole mit dem Status **Fehlerhaft** angezeigt.
- Benutzer, die über Richtlinien für den bedingten Zugriff geschützt werden, verlieren möglicherweise ihren Zugriff auf Unternehmensressourcen.

**Lösung:** Teilen Sie die folgenden Lösungen mit Ihren Endbenutzern, damit Sie wieder Zugriff auf Unternehmensressourcen erhalten.

Wenn Benutzer die iOS-Unternehmensportal-App starten, können sie sehen, ob deren Gerät keinen Kontakt mehr mit Intune hat. Wenn erkannt wird, dass kein Kontakt mehr mit Intune besteht, wird automatisch versucht, eine Synchronisation mit Intune durchzuführen, um die Verbindung wieder herzustellen (Benutzer sehen die **Synchronisierungsversuch...**- Meldung).

  ![Versuch, Benachrichtigungen zu synchronisieren](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_trying_to_sync_notification.png)

Wenn die Synchronisierung erfolgreich ist, sehen Sie die Inlinemeldung **Synchronisierung erfolgreich** in der iOS-Unternehmensportal-App, die zeigt, dass der Integritätsstatus Ihres Geräts gut ist.

  ![Benachrichtigung „Synchronisierung erfolgreich“](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_sync_successful_notification.png)

Wenn die Synchronisierung nicht erfolgreich ist, sehen Benutzer die Inlinemeldung **Synchronisierung nicht möglich** in der iOS-Unternehmensportal-App.

  ![Benachrichtigung „Synchronisierung nicht möglich“](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_unable_to_sync_notification.png)

Um das Problem zu beheben, müssen Benutzer die Schaltfläche **Set up** (Einrichten) auswählen, die sich rechts von der Meldung **Synchronisierung nicht möglich** befindet. Die Schaltfläche „Set up“ (Einrichten) führt die Benutzer zum Bildschirm „Company Access Setup“ (Unternehmenszugriff einrichten), auf dem sie die Anforderungen befolgen können, um ihr Gerät zu registrieren.

  ![Bildschirm „Unternehmenszugriff einrichten“](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_company_access_setup.png)

Sobald die Geräte registriert sind, ist ihr Integritätsstatus gut, und sie erhalten erneut Zugriff auf Unternehmensressourcen.

### <a name="verify-ws-trust-13-is-enabled"></a>Sicherstellen, dass WS-Trust 1.3 aktiviert ist
**Problem:** Geräte des Programms zur Geräteregistrierung für iOS können nicht registriert werden

Für die Registrierung von Geräten des Programms zur Geräteregistrierung mit Benutzeraffinität muss der Endpunkt „WS-Trust 1.3 Username/Mixed“ aktiviert sein, um Benutzertoken anzufordern. Dieser Endpunkt wird von Active Directory standardmäßig aktiviert. Eine Liste der aktivierten Endpunkte erhalten Sie mithilfe des PowerShell-Cmdlets „Get-AdfsEndpoint“ und der Suche nach dem Endpunkt Trust/13/UsernameMixed. Beispiel:

      Get-AdfsEndpoint -AddressPath “/adfs/services/trust/13/UsernameMixed”

Weitere Informationen finden Sie in der [Get-AdfsEndpoint-Dokumentation](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

Weitere Informationen finden Sie unter [Best practices for securing Active Directory Federation Services (Bewährte Methoden zum Schützen von Active Directory-Verbunddiensten)](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/best-practices-securing-ad-fs). Hilfe bei der Entscheidung, ob WS-Trust 1.3 Username/Mixed bei Ihrem Identitätsverbundanbieter aktiviert ist, erhalten Sie wie folgt:
- Wenden Sie sich an den Microsoft-Support, wenn Sie ADFS verwenden.
- Wenden Sie sich an den Anbieter Ihrer Drittanbieteridentität.


### <a name="profile-installation-failed"></a>Fehler bei der Profilinstallation
**Problem:** Sie erhalten auf einem iOS-Gerät die Fehlermeldung **Fehler bei der Profilinstallation**.

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>Schritte zur Problembehandlung bei fehlgeschlagener Profilinstallation

1.  Vergewissern Sie sich, dass dem Benutzer eine geeignete Lizenz für die Version des von Ihnen verwendeten Intune-Diensts zugewiesen wurde.

2.  Vergewissern Sie sich, dass das Gerät nicht bereits bei einem anderen MDM-Anbieter registriert ist.

3. Vergewissern Sie sich, dass auf dem Gerät noch kein Verwaltungsprofil installiert ist.

4.  Navigieren Sie zu [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com), und versuchen Sie das Profil zu installieren, wenn Sie dazu aufgefordert werden.

5.  Vergewissern Sie sich, dass Safari für iOS der Standardbrowser ist und dass Cookies aktiviert sind.

### <a name="enrolled-ios-device-doesnt-appear-in-console-when-using-system-center-configuration-manager-with-intune"></a>Ein registriertes iOS-Gerät wird nicht in der Konsole angezeigt, wenn der System Center Configuration Manager mit Intune verwendet wird.
**Problem:** Der Benutzer registriert das iOS-Gerät, aber es wird nicht in der Configuration Manager-Verwaltungskonsole angezeigt. Das Gerät zeigt nicht an, dass es registriert wurde. Mögliche Ursachen:

- Der Microsoft Intune-Connector an Ihrem Configuration Manager-Standort kommuniziert nicht mit dem Intune-Dienst.
- Entweder die ddm-Komponente (Data Discovery Manager) oder die statmgr-Komponente (Status-Manager) verarbeitet keine Nachrichten vom Intune-Dienst.
- Vielleicht haben Sie das MDM-Zertifikat von einem Konto heruntergeladen und auf einem anderen Konto verwendet.


**Lösung:** Prüfen Sie die folgenden Protokolldateien auf mögliche Fehler:

- dmpdownloader.log
- ddm.log
- statmgr.log

Demnächst werden Beispiele hinzugefügt, die zeigen, wonach in diesen Protokolldateien zu suchen ist.


### <a name="users-ios-device-is-stuck-on-an-enrollment-screen-for-more-than-10-minutes"></a>Das iOS-Gerät des Benutzers verharrt mehr als 10 Minuten bei einem Registrierungsbildschirm.

**Problem:** Ein Gerät verbleibt während der Registrierung auf einem von zwei Bildschirmen:
- Erwarten der endgültigen Konfiguration von „Microsoft“.
- Guided Access-App nicht verfügbar. Wenden Sie sich an den Administrator.

Das Problem kann in den folgenden Fällen auftreten:
- Die Apple-Dienste sind temporär ausgefallen oder
- Für die iOS-Registrierung ist die Verwendung von VPP-Token festgelegt, wie in der Tabelle gezeigt, aber es gibt ein Problem mit dem VPP-Token.

| Registrierungseinstellungen | Wert |
| ---- | ---- |
| Plattform | iOS |
| Benutzeraffinität | Mit Benutzeraffinität registrieren |
|Mit dem Unternehmensportal anstelle des Apple Setup-Assistenten authentifizieren | Ja |
| Installieren des Unternehmensportals mit VPP | Token verwenden: Tokenadresse |
| Unternehmensportal bis zur Authentifizierung im Einzelanwendungsmodus ausführen | Ja |

**Lösung**: Sie müssen wie folgt vorgehen, um das Problem zu beheben:
1. Ermitteln Sie, ob ein Problem mit dem VPP-Token vorliegt und beheben Sie es.
2. Ermitteln Sie, welche Geräte blockiert sind.
3. Setzen Sie die betroffenen Geräte zurück.
4. Weisen Sie den Benutzer an, den Registrierungsvorgang neu zu starten.

#### <a name="determine-if-theres-something-wrong-with-the-vpp-token"></a>Ermitteln Sie, ob ein Problem mit dem VPP-Token vorliegt.
1. Wechseln Sie zu **Intune** > **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** > Tokenname > **Profile** > Profilname > **Verwalten** > **Eigenschaften**.
2. Überprüfen Sie die Eigenschaften, um festzustellen, ob ähnliche Fehler wie die folgenden auftreten:
    - Dieses Token ist abgelaufen.
    - Dieses Token enthält keine Lizenzen für das Unternehmensportal.
    - Dieses Token wird von einem anderen Dienst verwendet.
    - Dieser Token wird von einem anderen Mandanten verwendet.
    - Dieses Token wurde gelöscht.
3. Beheben Sie die Probleme mit dem Token.

#### <a name="identify-which-devices-are-blocked-by-the-vpp-token"></a>Ermitteln der vom VPP-Token blockierten Geräte
1. Wechseln Sie zu **Intune** > **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** > Tokenname > **Geräte**.
2. Filtern Sie die Spalte **Profilstatus** nach **Blockiert**.
3. Notieren Sie sich die Seriennummern aller Geräte, für die **Blockiert** angegeben ist.

#### <a name="remotely-wipe-the-blocked-devices"></a>Remote-Zurücksetzung der blockierten Geräte
Nachdem Sie die Probleme mit dem VPP-Token behoben haben, müssen Sie die blockierten Geräte zurücksetzen.
1. Wechseln Sie zu **Intune** > **Geräte** > **Alle Geräte** > **Spalten** > **Seriennummer** > **Anwenden**. 
2. Wählen Sie jedes blockierte Gerät in der Liste **Alle Geräte** aus und wählen Sie dann **Zurücksetzen** > **Ja** aus.

#### <a name="tell-the-users-to-restart-the-enrollment-process"></a>Anweisen des Benutzers, den Registrierungsvorgang neu zu starten
Nachdem Sie die blockierten Geräte zurückgesetzt haben, können Sie den Benutzern mitteilen, dass sie den Registrierungsvorgang neu starten sollen.

## <a name="macos-issues"></a>macOS-Probleme

### <a name="macos-enrollment-errors"></a>macOS-Registrierungsfehler
**Fehlermeldung 1:** *It looks like you're using a virtual machine. Make sure you've fully configured your virtual machine, including serial number and hardware model. If this isn't a virtual machine, please contact support. (Sie verwenden scheinbar einen virtuellen Computer. Vergewissern Sie sich, dass Sie diesen vollständig konfiguriert haben und sowohl eine Seriennummer als auch ein Hardwaremodell vorhanden ist. Wenn es sich nicht um einen virtuellen Computer handelt, kontaktieren Sie den Support.)*  

**Fehlermeldung 2:** *We’re having trouble getting your device managed. This problem could be caused if you're using a virtual machine, have a restricted serial number, or if this device is already assigned to someone else. Learn how to resolve these problems or contact your company support. (Die Verwaltung Ihres Geräts bereitet Probleme, die dadurch entstanden sein könnten, dass Sie einen virtuellen Computer verwenden, die Seriennummer eingeschränkt ist oder das Gerät bereits einer anderen Person zugewiesen ist. Informieren Sie sich, wie Sie diese Probleme lösen können, oder kontaktieren Sie den Support Ihres Unternehmens.)*

**Problem:** Diese Meldung kann aus einem der folgenden Gründe angezeigt werden:  
* ein virtueller macOS-Computer ist nicht richtig konfiguriert  
* für Sie sind Geräteeinschränkungen aktiviert, die erfordern, dass das Gerät einem Unternehmen angehört oder dass die Seriennummer eines registrierten Geräts in Intune verfügbar ist  
* das Gerät wurde bereits registriert und ist noch einem anderen Benutzer in Intune zugewiesen  

**Lösung:** Bestimmen Sie zunächst gemeinsam mit dem Benutzer, welches Problem vorliegt. Führen Sie dann die folgenden betreffenden Schritte zur Lösung des Problems aus:
* Wenn ein Benutzer eine VM zu Testzwecken registriert, vergewissern Sie sich, dass diese vollständig konfiguriert ist, damit Intune die Seriennummer und das Hardwaremodell erkennen kann. Erfahren Sie mehr über [das Einrichten von VMs](macos-enroll.md#enroll-virtual-macos-machines-for-testing) in Intune.  
* Wenn für Ihre Organisation Registrierungsbeschränkungen aktiviert sind, die persönliche macOS-Geräte blockieren, müssen Sie manuell die [Seriennummer des Geräts](corporate-identifiers-add.md#manually-enter-corporate-identifiers) zu Intune hinzufügen.  
* Wenn das Gerät weiterhin einem anderen Benutzer in Intune zugewiesen ist, hat der vorherige Besitzer nicht die Unternehmensportal-App verwendet, um die Zuweisung aufzuheben oder zu entfernen. Gehen Sie wie folgt vor, um die veralteten Geräteinstellungen über Intune zu bereinigen:  

    1. Navigieren Sie im [Azure-Portal zu Intune](https://portal.manage.microsoft.com), und melden Sie sich mit Ihren Anmeldeinformationen als Administrator an.
    2. Navigieren Sie zu Intune > **Geräte** > **Alle Geräte**.  
    3. Suchen Sie das Gerät, für das ein Registrierungsproblem aufgetreten ist. Geben Sie den Gerätenamen oder die MAC/HW-Adresse ein, um die Ergebnisse einzuschränken.
    4. Wählen Sie das Gerät aus, und klicken Sie auf **Löschen**. Löschen Sie alle anderen Einträge, die diesem Gerät zugeordnet sind.  

## <a name="issues-when-using-system-center-configuration-manager-with-intune"></a>Probleme bei der Verwendung von System Center Configuration Manager mit Intune
### <a name="mobile-devices-disappear"></a>Mobile Geräte verschwinden
**Problem:** Nach der erfolgreichen Registrierung eines mobilen Geräts bei Configuration Manager verschwindet es aus der Auflistung der Mobilgeräte. Allerdings besitzt das Gerät weiterhin das Verwaltungsprofil und wird im CSS-Gateway aufgeführt.

**Lösung:** Dieses Problem kann folgende Ursachen haben:
- Es liegt ein benutzerdefinierter Prozess vor, der nicht zu Domänen beigetretene Geräte entfernt, oder 
- Der Benutzer hat das Gerät aus dem Abonnement entfernt.
Um zu verifizieren und überprüfen, welcher Prozess oder welches Benutzerkonto das Gerät aus der Configuration Manager-Konsole entfernt hat, führen Sie die folgenden Schritte aus.

#### <a name="check-how-device-was-removed"></a>Überprüfen, wie das Gerät entfernt wurde

1.  Wählen Sie in der Configuration Manager-Verwaltungskonsole **Überwachung** &gt; **Systemstatus** &gt; **Statusmeldungsabfragen** aus.

2.  Klicken Sie mit der rechten Maustaste auf **Manuell gelöschte Auflistungselementressourcen**, und wählen Sie **Meldungen anzeigen** aus.

3.  Wählen Sie eine geeignete Datum/Uhrzeit-Kombination innerhalb der letzten 12 Stunden aus.

4.  Suchen Sie das fragliche Gerät, und überprüfen Sie, wie das Gerät entfernt wurde. Das folgende Beispiel zeigt, dass das Konto „SCCMInstall“ das Gerät über eine unbekannte Anwendung gelöscht hat.

    ![Screenshot für die Gerätelöschungsdiagnose](./media/troubleshoot-device-enrollment-in-intune/CM_With_Intune_Unknown_App_Deleted_Device.jpg)

5.  Überprüfen Sie, ob der Configuration Manager keine geplante Aufgabe, ein geplantes Skript oder einen anderen geplanten Prozess hat, der eventuell keiner Domäne beigetretene, mobile oder verwandte Geräte automatisch löscht.

### <a name="other-ios-enrollment-errors"></a>Weitere iOS-Registrierungsfehler
In unserer Dokumentation unter [Troubleshooting iOS device enrollment problems in Microsoft Intune (Behandeln von Problemen bei der iOS-Geräteregistrierung in Microsoft Intune)](https://support.microsoft.com/help/4039809/troubleshooting-ios-device-enrollment-in-intune) finden Sie eine Liste der Fehler bei der iOS-Registrierung.

## <a name="pc-issues"></a>PC-Probleme

|Fehlermeldung|Problem|Lösung|
|---|---|---|
|**IT-Administrator muss eine Lizenz für den Zugriff zuweisen**<br>Ihr IT-Administrator hat Ihnen keinen Zugriff für die Verwendung dieser App erteilt. Wenden Sie sich an Ihren IT-Administrator, oder versuchen Sie es später erneut.|Das Gerät kann nicht registriert werden, da das Benutzerkonto nicht über die erforderliche Lizenz verfügt.|Bevor Benutzer ihre Geräte registrieren können, müssen Sie die nötigen Lizenzen zugewiesen bekommen. Diese Meldung bedeutet, dass der Benutzer den falschen Lizenztyp für die Autorität für die Verwaltung mobiler Geräte hat. Diese Fehlermeldung wird z. B. angezeigt, wenn die beiden folgenden Punkte zutreffen: <ol><li>Intune wurde als Autorität für die Verwaltung mobiler Geräte festgelegt.</li><li>Sie verwenden eine System Center 2012 R2 Configuration Manager-Lizenz.</li></ol>Weitere Informationen finden Sie unter [Zuweisen von Intune-Lizenzen zu Benutzerkonten](https://docs.microsoft.com/intune/licenses-assign).|



### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>Der Computer ist bereits registriert – Fehler hr 0x8007064c
**Problem:** Fehler bei Registrierung: **Der Computer ist bereits registriert**. Das Registrierungsprotokoll zeigt Fehler **hr 0x8007064c** an.

Dieser Fehler kann wie folgt durch den Computer verursacht werden:
- Der Computer wurde bereits registriert oder
- Der Computer verwendet das geklonte Image eines Computers, der bereits registriert wurde.
Das Kontozertifikat des vorherigen Kontos ist immer noch auf dem Computer vorhanden.

**Lösung:**

1. Geben Sie im Menü **Start** **Ausführen** -> **MMC** ein.
1. Wählen Sie **Datei** > **Snap-Ins hinzufügen/entfernen** aus.
1. Doppelklicken Sie auf **Zertifikate**, wählen Sie **Computerkonto**,  >  **Weiter**, und wählen Sie die Option **Lokaler Computer** aus.
1. Doppelklicken Sie auf **Zertifikate (lokaler Computer)**, und wählen Sie **Persönlich/Zertifikate** aus.
1. Suchen Sie nach dem von Sc_Online_Issuing ausgestellten Intune-Zertifikat, und löschen Sie es, falls vorhanden.
1. Falls der folgende Registrierungsschlüssel vorhanden ist, löschen Sie ihn: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey**. Löschen Sie auch eventuell vorhandene untergeordnete Schlüssel.
1. Versuchen Sie, eine erneute Registrierung durchzuführen.
1. Falls der PC weiterhin nicht registriert werden kann, löschen Sie diesen Schlüssel (sofern vorhanden): **KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**.
1. Versuchen Sie, eine erneute Registrierung durchzuführen.

    > [!IMPORTANT]
    > Dieser Abschnitt, diese Methode oder Aufgabe enthält Schritte, die Ihnen zeigen, wie Sie die Registrierung ändern. Wenn Sie die Registrierung falsch ändern, können jedoch schwerwiegende Probleme auftreten. Achten Sie darum auf eine sorgfältige Ausführung der folgenden Schritte. Sichern Sie die Registrierung zum zusätzlichen Schutz, bevor Sie sie ändern. Sie können dann die Registrierung wiederherstellen, falls ein Problem auftritt.
    > Weitere Informationen zum Sichern und Wiederherstellen der Registrierung finden Sie unter [How to back up and restore the registry in Windows](https://support.microsoft.com/kb/322756) (Sichern und Wiederherstellen der Registrierung in Windows).

## <a name="general-enrollment-error-codes"></a>Allgemeine Fehlercodes bei der Registrierung

|Fehlercode|Mögliches Problem|Lösungsvorschlag|
|--------------|--------------------|----------------------------------------|
|0x80CF0437 |Die Uhr des Clientcomputers ist nicht auf die richtige Uhrzeit eingestellt.|Stellen Sie sicher, dass die Uhr und die Zeitzone des Clientcomputers richtig eingestellt sind.|
|0x80240438, 0x80CF0438, 0x80CF402C|Verbindung mit dem Intune-Dienst ist nicht möglich. Überprüfen Sie die Proxy-Einstellungen des Clients.|Stellen Sie sicher, dass Intune die Proxykonfiguration auf dem Clientcomputer unterstützt. Stellen Sie sicher, dass der Clientcomputer über Internetzugriff verfügt.|
|0x80240438, 0x80CF0438|Proxyeinstellungen in Internet Explorer und im lokalen System sind nicht konfiguriert.|Verbindung mit dem Intune-Dienst ist nicht möglich. Überprüfen Sie die Clientproxyeinstellungen. Stellen Sie sicher, dass Intune die Proxykonfiguration auf dem Clientcomputer unterstützt. Stellen Sie sicher, dass der Clientcomputer über Internetzugriff verfügt.|
|0x80043001, 0x80CF3001, 0x80043004, 0x80CF3004|Das Registrierungspaket ist nicht mehr aktuell.|Laden Sie das aktuellste Clientsoftwarepaket vom Arbeitsbereich „Verwaltung“ herunter, und installieren Sie es.|
|0x80043002, 0x80CF3002|Das Konto befindet sich im Wartungsmodus.|Wenn sich das Konto im Wartungsmodus befindet, können Sie keine neuen Clientcomputer registrieren. Melden Sie sich zum Anzeigen Ihrer Kontoeinstellungen bei Ihrem Konto an.|
|0x80043003, 0x80CF3003|Das Konto wurde gelöscht.|Prüfen Sie, ob Ihr Konto und Ihr Abonnement für Intune noch aktiv sind. Melden Sie sich zum Anzeigen Ihrer Kontoeinstellungen bei Ihrem Konto an.|
|0x80043005, 0x80CF3005|Der Clientcomputer wurde abgekoppelt.|Warten Sie einige Stunden, entfernen Sie ältere Versionen der Clientsoftware von dem Computer, und versuchen Sie dann erneut, die Clientsoftware auf dem Computer zu installieren.|
|0x80043006, 0x80CF3006|Die für das Konto maximal zulässige Anzahl Arbeitsplätze ist erreicht.|Ihr Unternehmen muss zusätzliche Arbeitsplätze erwerben, bevor Sie weitere Clientcomputer bei dem Dienst registrieren können.|
|0x80043007, 0x80CF3007|Zertifikatsdatei wurde im Ordner des Installationsprogramms nicht gefunden.|Extrahieren Sie alle Dateien, bevor Sie die Installation starten. Die extrahierten Dateien dürfen nicht umbenannt oder verschoben werden: Alle Dateien müssen im selben Ordner vorhanden sein, da die Installation sonst fehlschlägt.|
|0x8024D015, 0x00240005, 0x80070BC2, 0x80070BC9, 0x80CFD015|Die Software kann nicht installiert werden, weil ein Neustart des Clientcomputers aussteht.|Starten Sie den Computer neu, und wiederholen Sie dann die Installation der Clientsoftware.|
|0x80070032|Eine oder mehrere Voraussetzungen, die für die Installation der Clientsoftware erforderlich sind, wurden auf dem Clientcomputer nicht gefunden.|Stellen Sie sicher, dass alle erforderlichen Updates auf dem Clientcomputer installiert sind, und versuchen Sie dann erneut, die Clientsoftware zu installieren.|
|0x80043008, 0x80CF3008|Microsoft-Onlinedienst zur Updateverwaltung konnte nicht gestartet werden.|Wenden Sie sich dazu an den Microsoft Support, wie unter [Anfordern von Support für Microsoft Intune](get-support.md) beschrieben.|
|0x80043009, 0x80CF3009|Der Clientcomputer ist bereits für den Dienst registriert.|Sie müssen den Clientcomputer abkoppeln, bevor sie ihn erneut für den Dienst registrieren können.|
|0x8004300B, 0x80CF300B|Das Installationspaket für die Clientsoftware kann nicht ausgeführt werden, da die Windows-Version auf dem Client nicht unterstützt wird.|Die auf dem Client ausgeführte Windows-Version wird von Intune nicht unterstützt.|
|0xAB2|Fehler beim Zugriff von Windows Installer auf die VBScript-Laufzeit für die benutzerdefinierte Aktion.|Dieser Fehler wird von einer benutzerdefinierten Aktion verursacht, die auf DLLs (Dynamic-Link Libraries) aufbaut. Um den DLL-Fehler zu behandeln, benötigen Sie möglicherweise die Tools, die unter [Microsoft Support KB198038: Useful Tools for Package and Deployment Issues (Microsoft-Support KB198038: Hilfreiche Tools bei Problemen mit der Erstellung und Bereitstellung von Paketen)](https://support.microsoft.com/kb/198038) beschrieben werden.|
|0x80cf0440|Die Verbindung zum Dienstendpunkt wurde abgebrochen.|Test- oder kostenpflichtige Konto wird angehalten. Erstellen Sie ein neues Test- oder kostenpflichtiges Konto und registrieren Sie sich erneut.|




### <a name="next-steps"></a>Nächste Schritte
Wenn diese Informationen zur Problembehandlung für Sie nicht hilfreich waren, wenden Sie sich wie in [Anfordern von Support für Microsoft Intune](get-support.md) beschrieben an den Microsoft Support.
