---
title: Android Enterprise-Geräteeinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Auf Geräten mit Android Enterprise oder Android for Work können Sie auf dem Gerät Einstellungen einschränken, darunter Kopieren und Einfügen, Benachrichtigungen anzeigen, App-Berechtigungen, Datenfreigabe, Kennwortlänge, Anmeldefehler, Entsperren per Fingerabdruck, Wiederverwenden von Kennwörtern und Aktivieren der Freigabe von Geschäftskontakten per Bluetooth. Konfigurieren Sie Geräte als Kiosk zur Ausführung einer oder mehrerer Apps.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.openlocfilehash: 62c44768f17ecc82dc748eb4dfda74da421ee3b5
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2019
ms.locfileid: "54387017"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie auf Android Enterprise-Geräten steuern können. Verwenden Sie als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) diese Einstellungen, um Features zuzulassen oder zu deaktivieren, Apps im Kioskmodus auszuführen, die Sicherheit zu steuern usw.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](device-restrictions-configure.md)

## <a name="device-owner-only"></a>Nur Gerätebesitzer

### <a name="general-settings"></a>Allgemeine Einstellungen

- **Bildschirmaufnahme:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Screenshots oder Bildschirmaufnahmen auf dem Gerät vorgenommen werden. Zudem wird verhindert, dass der Inhalt auf Anzeigegeräten angezeigt wird, die über keine sichere Videoausgabe verfügen. **Nicht konfiguriert** erlaubt dem Benutzer, den Bildschirminhalt als Bild zu erfassen.
- **Kamera:** Wählen Sie **Blockieren** aus, um den Zugriff auf die Kamera des Geräts zu verhindern. **Nicht erforderlich** ermöglicht den Zugriff auf die Kamera des Geräts.
- **Standardberechtigungsrichtlinie:** Diese Einstellung definiert die Standardberechtigungsrichtlinie für Anforderungen für Laufzeitberechtigungen. Folgende Werte sind zulässig:
  - **Gerätestandard:** Die Standardeinstellung des Geräts wird verwendet.
  - **Eingabeaufforderung:** Der Benutzer wird dazu aufgefordert, die Berechtigung zu genehmigen.
  - **Automatisch zulassen:** Berechtigungen werden automatisch gewährt.
  - **Automatisch ablehnen:** Berechtigungen werden automatisch verweigert.
- **Datums- und Uhrzeitänderungen:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer manuell Datum und Uhrzeit einstellen. **Nicht konfiguriert** ermöglicht Benutzern, Datum und Uhrzeit auf dem Gerät einzustellen.
- **Änderung der Lautstärke:** Wenn Sie **Blockieren** auswählen, können Benutzer die Lautstärke des Geräts nicht ändern. **Nicht konfiguriert** ermöglicht die Verwendung der Lautstärkeeinstellungen am Gerät.
- **Auf Werkseinstellungen zurücksetzen:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer die Option zum Zurücksetzen auf Werkseinstellungen in den Einstellungen des Geräts verwenden. **Nicht konfiguriert** ermöglicht Benutzern, diese Einstellung auf dem Gerät zu verwenden.
- **Abgesicherter Start:** Wenn Sie **Blockieren** auswählen, können Benutzer das Gerät nicht im abgesicherten Modus neu starten. **Nicht konfiguriert** ermöglicht Benutzern, das Gerät im abgesicherten Modus neu zu starten.
- **Statusleiste:** Wählen Sie **Blockieren** aus, um den Zugriff auf die Statusleiste einschließlich Benachrichtigungen und Schnelleinstellungen zu verhindern. **Nicht konfiguriert** ermöglicht Benutzern den Zugriff auf die Statusleiste.
- **Roamingdatendienste:** Wählen Sie **Blockieren** aus, um Datenroaming über das Mobilfunknetz zu verhindern. **Nicht konfiguriert** erlaubt das Datenroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.
- **Änderung der WLAN-Einstellungen:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer vom Gerätebesitzer erstellte WLAN-Einstellungen ändern. Benutzer können eigene WLAN-Konfigurationen erstellen. **Nicht konfiguriert** ermöglicht Benutzern, die WLAN-Einstellungen auf dem Gerät ändern.
- **Konfiguration des WLAN-Zugriffspunkts:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer WLAN-Konfigurationen erstellen oder ändern. **Nicht konfiguriert** ermöglicht Benutzern, die WLAN-Einstellungen auf dem Gerät ändern.
- **Bluetooth-Konfiguration:** Wählen Sie **Blockieren** aus, um Benutzer daran zu hindern, Bluetooth auf dem Gerät zu konfigurieren. **Nicht konfiguriert** ermöglicht die Verwendung von Bluetooth auf dem Gerät.
- **Kontaktfreigabe über Bluetooth:** Wählen Sie **Blockieren** aus, um den Zugriff auf Geschäftskontakte von einem anderen Gerät wie z.B. einem Kfz-System aus zu verhindern, wenn ein Android-Gerät mittels Bluetooth gekoppelt ist. **Nicht konfiguriert** ermöglicht den Zugriff auf Arbeitskontakte auf einem anderen Bluetooth-Gerät, das mit dem Android-Gerät gekoppelt ist.
- **Tethering und Zugriff auf Hotspots:** Wählen Sie **Blockieren** aus, um Tethering und Zugriff auf portable Hotspots zu verhindern. **Nicht konfiguriert** ermöglicht Tethering und Zugriff auf portable Hotspots.
- **USB-Speicher:** Wählen Sie **Zulassen** aus, um auf USB-Speicher auf dem Gerät zuzugreifen. **Nicht konfiguriert** verhindert den Zugriff auf USB-Speicher.
- **USB-Dateiübertragung:** Wählen Sie **Blockieren** aus, um das Übertragen von Dateien per USB zu verhindern. **Nicht konfiguriert** ermöglicht das Übertragen von Dateien.
- **Externe Medien:** Wählen Sie **Blockieren** aus, um die Verwendung externer Medien oder das Herstellen einer Verbindung mit solchen auf dem Gerät zu verhindern. **Nicht konfiguriert** lässt externe Medien auf dem Gerät zu.
- **Daten mithilfe von NFC übertragen:** Wählen Sie **Blockieren** aus, um die Verwendung der Nahfeldkommunikation (Near Field Communication, NFC) zum Übertragen von Dateien aus Apps zu verhindern. **Nicht konfiguriert** ermöglicht die Verwendung von NFC zum Freigeben von Daten zwischen Geräten.
- **Debugfunktionen:** Wenn Sie **Zulassen** auswählen, können Benutzer Features zum Debuggen auf dem Gerät verwenden. **Nicht konfiguriert** verhindert, dass Benutzer Features zum Debuggen auf dem Gerät verwenden.
- **Mikrofonanpassung:** Wenn Sie **Blockieren** auswählen, können Benutzer weder die Stummschaltung des Mikrofons aufheben noch die Lautstärke am Mikrofon anpassen. **Nicht konfiguriert** ermöglicht dem Benutzer, die Lautstärke am Mikrofon des Geräts anzupassen.
- **E-Mail-Adressen für Schutz vor Zurücksetzung auf Werkseinstellungen:** Wählen Sie **E-Mail-Adressen für Google-Konto** aus. Geben Sie die E-Mail-Adressen der Geräteadministratoren ein, die das Gerät entsperren können, nachdem es zurückgesetzt wurde. Achten Sie darauf, dass Sie die E-Mail-Adressen durch ein Semikolon trennen, z. B. `admin1@gmail.com;admin2@gmail.com`. Wenn keine E-Mail-Adresse eingegeben wird, kann jeder das Gerät entsperren, sobald die Werkseinstellungen wiederhergestellt sind.
- **Notausstieg für Netzwerk:** Das **Aktivieren** dieser Option erlaubt Benutzern, das Feature „Notausstieg für Netzwerk“ zu aktivieren. Wenn beim Starten des Geräts keine Netzwerkverbindung hergestellt wird, fordert die Notausstiegsfunktion zum Herstellen einer vorübergehenden Verbindung mit einem Netzwerk und Aktualisieren der Geräterichtlinie auf. Nach dem Anwenden der Richtlinie wird das temporäre Netzwerk ignoriert, und das Gerät setzt den Start fort. Dieses Feature verbindet Geräte mit einem Netzwerk, wenn:
  - Kein geeignetes Netzwerk in der letzten Richtlinie enthalten ist.
  - Das Gerät im Aufgabensperrmodus in eine App startet.
  - Der Benutzer die Einstellungen für das Gerät nicht erreichen kann.

  **Nicht konfiguriert** verhindert, dass Benutzer die Netzwerk-Notausstiegsfunktion auf dem Gerät aktivieren.

- **Installation aus unbekannten Quellen zulassen:** Wenn Sie **Zulassen** auswählen, können Benutzer **unbekannte Quellen** nutzen. Mit dieser Einstellung können Apps aus unbekannten Quellen installiert werden. **Nicht konfiguriert** verhindert, dass Benutzer **Unbekannte Quellen** nutzen.
- **Systemupdate:** Hier können Sie eine Option auswählen, um zu definieren, wie das Gerät Over-the-Air-Updates verarbeitet:
  - **Gerätestandard:** Die Standardeinstellung des Geräts wird verwendet.
  - **Automatisch:** Updates werden ohne Interaktion mit dem Benutzer automatisch installiert. Durch das Festlegen dieser Richtlinie werden sofort alle ausstehenden Updates installiert.
  - **Zurückgestellt:** Updates werden für 30 Tage zurückgestellt. Nach Ablauf der 30 Tage fordert Android den Benutzer zur Installation des Updates auf. Gerätehersteller oder Mobilfunkanbieter können verhindern (ausschließen), dass wichtige Sicherheitsupdates zurückgestellt werden. Bei einem ausgeschlossenen Update wird dem Benutzer eine Systembenachrichtigung auf dem Gerät angezeigt. 
  - **Wartungsfenster:** Updates werden automatisch in einem täglichen Wartungsfenster installiert, das Sie in Intune festlegen. Die Installation wird 30 Tage lang täglich versucht, und es kann aufgrund von zu geringem Speicherplatz oder Akkustand ein Fehler auftreten. Nach 30 Tagen wird der Benutzer von Android zum Installieren aufgefordert. Dieses Fenster wird auch verwendet, um Updates für Google Play-Apps zu installieren. Verwenden Sie diese Option für dedizierte Geräte wie Kioskgeräte, da Apps, die im Vordergrund auf einem Gerät ausgeführt werden, auf dem der Kioskmodus für die Ausführung einer einzelnen App aktiviert ist, aktualisiert werden können.
- **Automatische App-Updates:** Wählen Sie diese Option aus, wenn automatische Updates installiert werden. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert**
  - **Benutzerauswahl**
  - **Nie**
  - **Nur WLAN**
  - **Immer**

- **Benachrichtigungsfenster:** Wenn **Deaktivieren** ausgewählt ist, werden Fensterbenachrichtigungen, wie Popups, eingehende Anrufe, ausgehende Anrufe, Systemwarnungen und Systemfehler, nicht auf dem Gerät angezeigt. Bei **Nicht konfiguriert** wird die Standardeinstellung des Betriebssystems verwendet, wodurch Benachrichtigungen möglicherweise angezeigt werden.
- **Hinweise zur ersten Verwendung überspringen:** Wählen Sie **Aktivieren** aus, um Vorschläge aus Apps auszublenden oder zu überspringen, Tutorials schrittweise durchzuarbeiten oder beim Starten der App einführende Hinweise zu lesen. Bei **Nicht konfiguriert** wird die Standardeinstellung des Betriebssystems verwendet, wodurch diese Vorschläge beim Starten der App möglicherweise angezeigt werden.


### <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit

- **Bedrohungsüberprüfung für Apps:** Die Option **Anfordern** erzwingt, dass die Einstellung **Apps überprüfen** für Arbeitsprofile und persönliche Profile aktiviert ist.

### <a name="kiosk-settings"></a>Kioskeinstellungen

Sie können ein Gerät zum Ausführen einer App oder mehrerer Apps konfigurieren. Im Kioskmodus eines Geräts stehen nur die Apps zur Verfügung, die Sie hinzufügen. Diese Einstellungen gelten für dedizierte Android-Geräte, nicht aber für vollständig verwaltete dedizierte Android-Geräte.

**Kioskmodus:** Wählen Sie aus, ob das Gerät eine App oder mehrere Apps ausführt.

- **Kiosk mit einzelner App:** Benutzer können auf dem Gerät nur auf eine einzelne App zugreifen. Wenn das Gerät gestartet wird, wird nur die jeweilige App gestartet. Benutzer können keine neuen Apps öffnen oder die ausgeführte App ändern.

  **Schritte**
  1. Wählen Sie **Verwaltete App auswählen** aus und dann die verwaltete Google Play-App aus der Liste. 

      Wenn keine Apps aufgelistet werden, können Sie dem Gerät [einige Android-Apps hinzufügen](apps-add-android-for-work.md). Achten Sie darauf, [die App der Gruppe zuzuweisen, die für Ihre Kioskgeräte erstellt wurde](apps-deploy.md).

  2. Wählen Sie **OK** > **OK** aus, um die App hinzuzufügen.

- **Kiosk mit mehreren Apps:** Benutzer können auf dem Gerät nur auf eine begrenzte Anzahl von Apps zugreifen. Wenn das Gerät gestartet wird, werden nur die von Ihnen hinzugefügten Apps gestartet. Sie können auch einige Weblinks hinzufügen, die Benutzer öffnen können. Wenn die Richtlinie angewendet wird, können Benutzer die Symbole für die zulässigen Apps auf dem Startbildschirm sehen.

  > [WICHTIG] Für Multi-App-Kiosk-Geräte **muss** die [Managed Home Screen-App](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) aus Google Play:
  >   - in Intune [als Client-App hinzugefügt](apps-add-android-for-work.md) sein
  >   - [der Gerätegruppe zugewiesen sein](apps-deploy.md), die für Ihre Kioskgeräte erstellt wurde
  > 
  > Die **Managed Home Screen**-App muss sich nicht im Konfigurationsprofil befinden, aber als Client-App hinzugefügt werden. Wenn die **Managed Home Screen**-App als Client-App hinzugefügt wird, werden alle anderen Apps, die Sie im Konfigurationsprofil hinzufügen, in der **Managed Home Screen**-App als Symbole angezeigt. 

  - Wählen Sie **Hinzufügen** und dann Ihre Apps in der Liste aus.

    Wenn die **Managed Home Screen**-App nicht aufgeführt wird, [fügen Sie sie aus Google Play hinzu](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Achten Sie darauf, [die App der Gerätegruppe zuzuweisen](apps-deploy.md), die für Ihre Kioskgeräte erstellt wurde.

    Sie können auch andere [Android-Apps](apps-add-android-for-work.md) und [Web-Apps](web-app.md) hinzufügen, die von Ihrer Organisation für das Gerät erstellt wurden. Achten Sie darauf, [die App der Gruppe zuzuweisen, die für Ihre Kioskgeräte erstellt wurde](apps-deploy.md).

  - **Virtuelle Startschaltfläche:** Wählen Sie **Aktivieren** aus, um eine Startschaltfläche auf dem Kioskgerät anzuzeigen. Bei Auswahl dieser Option gelangt der Benutzer zurück zum Startbildschirm des Geräts, wo er problemlos zwischen Apps wechseln kann. Auf einigen Android-Geräten müssen Benutzer möglicherweise mit dem Finger über den Bildschirm wischen, damit die Startschaltfläche angezeigt wird. Mit **Deaktivieren** wird keine Startschaltfläche angezeigt, sodass Benutzer mit der Schaltfläche „Zurück“ zwischen Apps wechseln müssen.
  - **Kioskmodus verlassen:** Wählen Sie **Aktivieren** aus, um Administratoren zu ermöglichen, den Kioskmodus vorübergehend zu beenden, um das Gerät zu aktualisieren. Um dieses Feature verwenden zu können, führt der Administrator Folgendes aus: 
  
    1. Weiteres Betätigen der Schaltfläche „Zurück“, bis die Schaltfläche „Kiosk beenden“ angezeigt wird. 
    2. Auswählen der Schaltfläche und Eingabe der **Code zum Verlassen des Kioskmodus**-PIN.
    3. Wenn Sie alle gewünschten Änderungen vorgenommen haben, wählen Sie die **Managed Home Screen**-App aus. Mit diesem Schritt wird das Gerät erneut im Multi-App-Kioskmodus gesperrt. 
    
    **Deaktivieren** bietet keine Möglichkeit zum Anhalten des Kioskmodus. Wenn der Administrator weiterhin die Schaltfläche „Zurück“ betätigt und die Schaltfläche „Kiosk beenden“ auswählt, teilt eine Meldung mit, dass eine Kennung erforderlich ist.
    
    - **Code zum Verlassen des Kioskmodus:** Geben Sie eine 4-6-stellige numerische PIN ein. Der Administrator verwendet diese PIN zum vorübergehenden Anhalten des Kioskmodus.
 
  - **Benutzerdefinierten URL-Hintergrund festlegen:** Geben Sie eine URL zum Anpassen des Hintergrundbildschirms auf dem Kioskgerät ein.

### <a name="device-password-settings"></a>Gerätekennworteinstellungen

- **Keyguard:** Wenn Sie **Deaktivieren** auswählen, können Benutzer das Bildschirmsperrfeature Keyguard nicht auf dem Gerät verwenden. **Nicht konfiguriert** ermöglicht dem Benutzer, die Keyguard-Features zu verwenden.
- **Deaktivierte Keyguard-Features:** Wenn Keyguard auf dem Gerät aktiviert ist, wählen Sie die Features aus, die Sie deaktivieren möchten. Ist beispielsweise **Kamera absichern** ausgewählt, ist die Kamerafunktion auf dem Gerät deaktiviert. Alle nicht ausgewählten Features sind auf dem Gerät aktiviert.
- **Erforderlicher Kennworttyp:** Hiermit wird der Typ des erforderlichen Kennworts für das Gerät definiert. Folgende Optionen sind verfügbar:
  - **Mindestens numerisch**
  - **Numerisch, komplex:** Sich wiederholende oder fortlaufende Ziffern wie „1111“ oder „1234“ sind nicht zulässig.
  - **Mindestens alphabetisch**
  - **Mindestens alphanumerisch**
  - **Mindestens alphanumerisch mit Symbolen**
- **Minimale Kennwortlänge:** Geben Sie die Mindestanzahl von Zeichen ein, die Benutzer für das Kennwort eingeben müssen (zwischen 4 und 16 Zeichen).
- **Anzahl von fehlgeschlagenen Anmeldungen, bevor das Gerät zurückgesetzt wird:** Geben Sie die Anzahl der Anmeldungen ein, die fehlschlagen können, bevor das Gerät zurückgesetzt wird (zwischen 1 und 11).

### <a name="power-settings"></a>Energieeinstellungen

- **Zeit bis Bildschirmsperre:** Hiermit wird die Leerlaufzeit festgelegt, nach der das Gerät gesperrt wird.
- **Bildschirm aktiviert, wenn Gerät angeschlossen ist:** Hiermit kann ausgewählt werden, bei welchen Stromquellen der Bildschirm des Geräts aktiviert bleibt, wenn es angeschlossen ist.

### <a name="users-and-accounts-settings"></a>Einstellungen für Benutzer und Konten

- **Neue Benutzer hinzufügen:** Wenn Sie **Blockieren** auswählen, können Benutzer keine neuen Benutzer hinzufügen. Jeder Benutzer hat einen persönlichen Bereich auf dem Gerät für benutzerdefinierte Startseiten, Konten, Apps und Einstellungen. **Nicht konfiguriert** ermöglicht Benutzern, dem Gerät andere Benutzer hinzuzufügen.
- **Entfernen von Benutzern:** Wenn Sie **Blockieren** auswählen, können Benutzer keine Benutzer entfernen. **Nicht konfiguriert** ermöglicht Benutzern, andere Benutzer vom Gerät zu entfernen.
- **Kontoänderungen:** Wenn Sie **Blockieren** auswählen, können Benutzer Konten nicht bearbeiten. **Nicht konfiguriert** ermöglicht Benutzern, Benutzerkonten auf dem Gerät zu aktualisieren.

### <a name="connectivity"></a>Verbindung

- **Always On-VPN:** Wählen Sie **Aktivieren** aus, um einen VPN-Client so festzulegen, dass er automatisch eine Verbindung mit dem VPN herstellt und erneut herstellt. Always On-VPN-Verbindungen bleiben erhalten oder werden sofort hergestellt, wenn der Benutzer sein Gerät sperrt, das Gerät neu gestartet wird oder das drahtlose Netzwerk sich ändert. 

  Wählen Sie **Nicht konfiguriert** aus, um das Always On-VPN für alle VPN-Clients zu deaktivieren.

  > [!IMPORTANT]
  > Stellen Sie sicher, dass Sie nur eine Always On-VPN-Richtlinie auf einem einzelnen Gerät bereitstellen. Die Bereitstellung mehrerer Always VPN-Richtlinien auf einem einzelnen Gerät wird nicht unterstützt.

- **VPN-Client:** Wählen Sie einen VPN-Client aus, der Always On unterstützt. Folgende Optionen sind verfügbar:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Benutzerdefiniert
    - **Paket-ID:** Geben Sie die Paket-ID der App im Google Play Store ein. Wenn z. B. die URL für die App im Play Store `https://play.google.com/store/details?id=com.contosovpn.android.prod` lautet, dann ist die Paket-ID `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  >  - Der von Ihnen ausgewählte VPN-Client muss auf dem Gerät installiert sein und VPN pro Anwendung in Arbeitsprofilen unterstützen. Andernfalls tritt ein Fehler auf. 
  >  - Sie müssen die VPN-Client-App im **verwalteten Google Play Store** genehmigen, die App mit Intune synchronisieren und die App auf dem Gerät bereitstellen. Danach wird die App im Arbeitsprofil des Benutzers installiert.
  >  - Es gibt eventuell bekannte Probleme bei der Verwendung von VPN pro App mit F5 Access for Android 3.0.4. Weitere Informationen finden Sie unter [F5's release notes for F5 Access for Android 3.0.4 (Versionshinweise zu F5 Access for Android 3.0.4)](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android).

- **Sperrmodus:** Wählen Sie **Aktivieren** aus, um den gesamten Netzwerkdatenverkehr zu zwingen, den VPN-Tunnel zu verwenden. Wenn keine Verbindung zum VPN hergestellt wird, hat das Gerät keinen Netzwerkzugriff.

  Wählen Sie **Nicht konfiguriert** aus, damit der Datenverkehr durch den VPN-Tunnel oder durch das Mobilfunknetz fließen kann.

## <a name="work-profile-only"></a>Nur Arbeitsprofil 

### <a name="work-profile-settings"></a>Arbeitsprofileinstellungen

#### <a name="general"></a>Allgemein

- **Kopieren und Einfügen zwischen Arbeitsprofilen und persönlichen Profilen:** Wenn Sie **Blockieren** auswählen, wird das Kopieren und Einfügen zwischen Arbeits-Apps und persönlichen Apps verhindert. **Nicht konfiguriert** ermöglicht Benutzern, Daten mithilfe von Kopieren und Einfügen mit Apps im persönlichen Profil freizugeben. 
- **Datenaustausch zwischen Arbeitsprofilen und persönlichen Profilen:** Wählen Sie diese Option aus, damit Apps im Arbeitsprofil Daten mit Apps im persönlichen Profil austauschen können. Sie können z.B. Freigabeaktionen in Anwendungen steuern, wie etwa die Option **Freigeben**. in der Chrome-Browser-App. Diese Einstellung gilt nicht für das Verhalten beim Kopieren/Einfügen der Zwischenablage. Ihre Freigabeoptionen:
  - **Standardeinschränkungen für Freigabe:** Dies ist das standardmäßige Freigabeverhalten des Geräts, das abhängig von der Android-Version variiert. Standardmäßig ist die Freigabe von Daten des persönlichen Profils für das Arbeitsprofil zulässig. Die Freigabe von Daten des Arbeitsprofils für das persönliche Profil ist dagegen standardmäßig blockiert. Durch diese Einstellung wird die Freigabe von Daten des Arbeitsprofils für das persönliche Profil verhindert. Auf Geräten mit den Versionen 6.0 und höher blockiert Google die Freigabe vom persönlichen Profil zum Arbeitsprofil nicht.
  - **Apps im Arbeitsprofil können Freigabeanforderungen vom persönlichen Profil verarbeiten:** Dadurch wird das integrierte Android-Feature aktiviert, das die Freigabe vom persönlichen Profil zum Arbeitsprofil erlaubt. Wenn diese Option aktiviert ist, können Daten durch eine Freigabeanfrage einer App im persönlichen Profil für Apps im Arbeitsprofil freigegeben werden. Diese Einstellung ist das Standardverhalten für Android-Geräte, die frühere Versionen als 6.0 ausführen.
  - **Grenzübergreifende Freigabe zulassen:** Ermöglicht die Freigabe von Daten in beide Richtungen über die Begrenzung des Arbeitsprofils hinaus. Wenn Sie diese Einstellung auswählen, können Apps im Arbeitsprofil Daten für Apps ohne Badgeverwendung im persönlichen Profil freigeben. Diese Einstellung gestattet es verwalteten Apps im Arbeitsprofil, die Daten für Apps auf der nicht verwalteten Seite des Geräts freizugeben. Verwenden Sie diese Einstellung also mit Bedacht.

- **Arbeitsprofilbenachrichtigungen bei Gerätesperre:** Steuert, ob Apps im Arbeitsprofil Daten in Benachrichtigungen anzeigen können, wenn das Gerät gesperrt ist. **Blockieren** verhindert die Datenanzeige. **Nicht konfiguriert** zeigt die Daten an.
- **Standardmäßige App-Berechtigungen:** Legt die Standardberechtigungsrichtlinie für alle Apps im Arbeitsprofil fest. Ab Android 6 wird der Benutzer aufgefordert, bestimmte von den Apps benötigte Berechtigungen zu erteilen, wenn die App gestartet wird. Bei dieser Richtlinieneinstellung können Sie festlegen, ob Benutzer aufgefordert werden sollen, Berechtigungen für alle Apps im Arbeitsprofil zu gewähren. Beispielsweise können Sie dem Arbeitsprofil eine App zuweisen, die Standortzugriff benötigt. In der Regel fordert diese App den Benutzer dazu auf, den Standortzugriff durch die App zu genehmigen oder abzulehnen. Verwenden Sie diese Richtlinie, um Berechtigungen automatisch ohne Aufforderung zu erteilen, Berechtigungen ohne Aufforderung automatisch zu verweigern oder den Endbenutzer entscheiden zu lassen. Es stehen die folgenden Optionen zur Auswahl:
  - **Gerätestandard**
  - **Eingabeaufforderung**
  - **Automatisch gewähren**
  - **Automatisch verweigern**

  Sie können auch eine App-Konfigurationsrichtlinie verwenden, um Berechtigungen für einzelne Anwendungen zu erteilen (**Clientanwendungen** > **App-Konfigurationsrichtlinien**).

- **Konten hinzufügen und entfernen:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Endbenutzer Konten im Arbeitsprofil manuell hinzufügen oder daraus entfernen. Wenn Sie beispielsweise die Gmail-App in einem Android-Arbeitsprofil bereitstellen, können Sie verhindern, dass Benutzer Konten in diesem Arbeitsprofil hinzufügen oder entfernen. **Nicht konfiguriert** ermöglicht das Hinzufügen von Konten im Arbeitsprofil.  

- **Kontaktfreigabe über Bluetooth:** Ermöglicht den Zugriff auf Geschäftskontakte von einem anderen Gerät aus, z.B. aus dem Auto, wenn es mit Bluetooth gekoppelt ist. Diese Einstellung ist standardmäßig nicht konfiguriert, und Kontakte aus dem Arbeitsprofil werden nicht angezeigt. Klicken Sie auf **Aktivieren**, um diese Freigabe zuzulassen und um Kontakte aus dem Arbeitsprofil anzuzeigen. Diese Einstellung ist auf Geräten unter Android OS 6.0 und höher verfügbar, auf denen Arbeitsprofile eingerichtet wurden. Wenn Sie diese Einstellung aktivieren, können bestimmte Bluetooth-Geräte bei der ersten Verbindung Arbeitskontakte zwischenspeichern. Durch das Deaktivieren dieser Richtlinie nach einer ersten Kopplung bzw. Synchronisierung werden die Arbeitskontakte von einem Bluetooth-Gerät möglicherweise nicht entfernt.

- **Bildschirmaufnahme:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Screenshots oder Bildschirmaufnahmen auf dem Gerät im Arbeitsprofil vorgenommen werden. Zudem wird verhindert, dass der Inhalt auf Anzeigegeräten angezeigt wird, die über keine sichere Videoausgabe verfügen. **Nicht konfiguriert** ermöglicht das Erstellen von Screenshots.

- **Anrufer-ID des Geschäftskontakts im persönlichen Profil anzeigen:** Wenn diese Option aktiviert ist (**Nicht konfiguriert**), werden die Anruferdetails des Geschäftskontakts im persönlichen Profil angezeigt. Mit **Blockieren** wird die Anrufernummer des Arbeitskontakts im persönlichen Profil nicht angezeigt. Gilt für Android OS v6.0 und neuere Versionen.

- **Geschäftskontakte vom persönlichen Profil aus suchen:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer in Apps im persönlichen Profil nach Geschäftskontakten suchen. **Nicht erforderlich** ermöglicht das Suchen nach Arbeitskontakten im persönlichen Profil.

- **Kamera:** Wählen Sie **Blockieren** aus, um den Zugriff auf die Kamera des Geräts im Arbeitsprofil zu verhindern. Die Kamera im persönlichen Profil ist von dieser Einstellung nicht betroffen. **Nicht erforderlich** ermöglicht den Zugriff auf die Kamera im Arbeitsprofil.

#### <a name="work-profile-password"></a>Arbeitsprofilkennwort

- **Arbeitsprofilkennwort erforderlich:** Gilt für Android 7.0 und höher mit aktiviertem Arbeitsprofil. Wählen Sie **Anfordern** aus, um eine Kennungsrichtlinie einzugeben, die nur für Apps im Arbeitsprofil gilt. Standardmäßig kann der Endbenutzer die beiden separat definierten PINs verwenden oder diese zu einer PIN kombinieren, die die Stärke der jeweils stärkeren PIN übernimmt. **Nicht konfiguriert** ermöglicht dem Benutzer, Arbeits-Apps ohne Kennworteingabe zu verwenden.
- **Minimale Kennwortlänge:** Geben Sie eine Mindestanzahl von **4**-**16** Zeichen ein, die das Benutzerkennwort enthalten muss.
- **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Sperrung des Arbeitsprofils:** Wählen Sie den Zeitraum aus, nach dem das Arbeitsprofil gesperrt wird. Der Benutzer muss dann seine Anmeldeinformationen eingeben, um wieder Zugriff zu erhalten.
- **Anzahl von fehlgeschlagenen Anmeldungen, bevor das Gerät zurückgesetzt wird:** Geben Sie ein, wie häufig ein falsches Kennwort eingegeben werden kann, bevor das Arbeitsprofil vom Gerät gelöscht wird.
- **Kennwortablauf (Tage):** Geben Sie eine Anzahl von Tagen von **1**-**255** ein, nach deren Verstreichen das Kennwort eines Endbenutzers geändert werden muss.
- **Erforderlicher Kennworttyp:** Wählen Sie den Typ des Kennworts aus, das auf dem Gerät festgelegt werden muss. Es stehen die folgenden Optionen zur Auswahl:
  - **Gerätestandard**
  - **Biometrie auf niedriger Sicherheitsstufe**
  - **Erforderlich**
  - **Mindestens numerisch**
  - **Numerisch, komplex:** Sich wiederholende oder fortlaufende Ziffern wie „1111“ oder „1234“ sind nicht zulässig.
  - **Mindestens alphabetisch**
  - **Mindestens alphanumerisch**
  - **Mindestens alphanumerisch mit Symbolen**
- **Wiederverwendung vorheriger Kennwörter verhindern:** Geben Sie eine Anzahl neuer Kennwörter von **1**-**24** ein, die verwendet werden müssen, bevor ein altes Kennwort wiederverwendet werden kann.
- **Entsperrung durch Fingerabdruck:** Wählen Sie **Blockieren** aus, um zu verhindern, dass ein Endbenutzer das Gerät mithilfe des Fingerabdruckscanners entsperren kann. **Nicht konfiguriert** ermöglicht Benutzern das Entsperren von Geräten mit einem Fingerabdruck im Arbeitsprofil.
- **Smart Lock und andere Vertrauens-Agents:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Smart Lock oder andere Vertrauens-Agents Sperrbildschirmeinstellungen auf kompatiblen Geräten anpassen können. Dieses Feature wird manchmal auch als Vertrauens-Agent bezeichnet und ermöglicht Ihnen, das Kennwort für den Gerätesperrbildschirm zu deaktivieren oder zu umgehen, wenn sich das Gerät an einem vertrauenswürdigen Standort befindet. Umgehen Sie z. B. das Kennwort für das Arbeitsprofil, wenn das Gerät mit einem bestimmten Bluetooth-Gerät verbunden ist oder sich in der Nähe eines NFC-Tags befindet. Mit dieser Einstellung können Sie verhindern, dass Benutzer Smart Lock konfigurieren.

### <a name="device-password"></a>Gerätekennwort

Diese Kennworteinstellungen gelten für persönliche Profile auf Geräten, die ein Arbeitsprofil verwenden.

- **Minimale Kennwortlänge:** Geben Sie eine Mindestanzahl von **4**-**14** Zeichen ein, die das Benutzerkennwort enthalten muss.
- **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung:** Wählen Sie den Zeitraum aus, nach dem ein inaktives Gerät automatisch gesperrt wird.
- **Anzahl von fehlgeschlagenen Anmeldungen, bevor das Gerät zurückgesetzt wird:** Geben Sie ein, wie häufig ein falsches Kennwort eingegeben werden kann, bevor alle Daten vom Gerät gelöscht werden.
- **Kennwortablauf (Tage):** Geben Sie eine Anzahl von Tagen von **1**-**255** ein, nach deren Verstreichen das Kennwort eines Endbenutzers geändert werden muss.
- **Erforderlicher Kennworttyp:** Wählen Sie den Typ des Kennworts aus, das auf dem Gerät festgelegt werden muss. Es stehen die folgenden Optionen zur Auswahl:
  - **Gerätestandard**
  - **Biometrie auf niedriger Sicherheitsstufe**
  - **Erforderlich**
  - **Mindestens numerisch**
  - **Numerisch, komplex:** Sich wiederholende oder fortlaufende Ziffern wie „1111“ oder „1234“ sind nicht zulässig.
  - **Mindestens alphabetisch**
  - **Mindestens alphanumerisch**
  - **Mindestens alphanumerisch mit Symbolen**
- **Wiederverwendung vorheriger Kennwörter verhindern:** Geben Sie eine Anzahl neuer Kennwörter von **1**-**24** ein, die verwendet werden müssen, bevor ein altes Kennwort wiederverwendet werden kann.
- **Entsperrung durch Fingerabdruck:** Wählen Sie **Blockieren** aus, um zu verhindern, dass ein Endbenutzer das Gerät mithilfe des Fingerabdruckscanners entsperren kann. **Nicht konfiguriert** ermöglicht dem Benutzer das Entsperren des Geräts mittels Fingerabdruck.
- **Smart Lock und andere Vertrauens-Agents:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Smart Lock oder andere Vertrauens-Agents Sperrbildschirmeinstellungen auf kompatiblen Geräten anpassen können. Dieses Feature wird manchmal auch als Vertrauens-Agent bezeichnet und ermöglicht Ihnen, das Kennwort für den Gerätesperrbildschirm zu deaktivieren oder zu umgehen, wenn sich das Gerät an einem vertrauenswürdigen Standort befindet. Umgehen Sie z. B. das Kennwort für das Arbeitsprofil, wenn das Gerät mit einem bestimmten Bluetooth-Gerät verbunden ist oder sich in der Nähe eines NFC-Tags befindet. Mit dieser Einstellung können Sie verhindern, dass Benutzer Smart Lock konfigurieren.

### <a name="system-security"></a>Systemsicherheit

- **Bedrohungsüberprüfung für Apps:** Die Option **Anfordern** erzwingt, dass die Einstellung **Apps überprüfen** für Arbeitsprofile und persönliche Profile aktiviert ist.

   > [!Note]
   > Diese Einstellung funktioniert nur auf Geräten mit Android O und höher.

### <a name="connectivity"></a>Verbindung

- **Always On-VPN:** Wählen Sie **Aktivieren** aus, um einen VPN-Client so festzulegen, dass er automatisch eine Verbindung mit dem VPN herstellt und erneut herstellt. Always On-VPN-Verbindungen bleiben erhalten oder werden sofort hergestellt, wenn der Benutzer sein Gerät sperrt, das Gerät neu gestartet wird oder das drahtlose Netzwerk sich ändert. 

  Wählen Sie **Nicht konfiguriert** aus, um das Always On-VPN für alle VPN-Clients zu deaktivieren.

  > [!IMPORTANT]
  > Stellen Sie sicher, dass Sie nur eine Always On-VPN-Richtlinie auf einem einzelnen Gerät bereitstellen. Die Bereitstellung mehrerer Always VPN-Richtlinien auf einem einzelnen Gerät wird nicht unterstützt.

- **VPN-Client:** Wählen Sie einen VPN-Client aus, der Always On unterstützt. Folgende Optionen sind verfügbar:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Benutzerdefiniert
    - **Paket-ID:** Geben Sie die Paket-ID der App im Google Play Store ein. Wenn z. B. die URL für die App im Play Store `https://play.google.com/store/details?id=com.contosovpn.android.prod` lautet, dann ist die Paket-ID `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  >  - Der von Ihnen ausgewählte VPN-Client muss auf dem Gerät installiert sein und VPN pro Anwendung in Arbeitsprofilen unterstützen. Andernfalls tritt ein Fehler auf. 
  >  - Sie müssen die VPN-Client-App im **verwalteten Google Play Store** genehmigen, die App mit Intune synchronisieren und die App auf dem Gerät bereitstellen. Danach wird die App im Arbeitsprofil des Benutzers installiert.
  >  - Es gibt eventuell bekannte Probleme bei der Verwendung von VPN pro App mit F5 Access for Android 3.0.4. Weitere Informationen finden Sie unter [F5's release notes for F5 Access for Android 3.0.4 (Versionshinweise zu F5 Access for Android 3.0.4)](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android).

- **Sperrmodus:** Wählen Sie **Aktivieren** aus, um den gesamten Netzwerkdatenverkehr zu zwingen, den VPN-Tunnel zu verwenden. Wenn keine Verbindung zum VPN hergestellt wird, hat das Gerät keinen Netzwerkzugriff.

  Wählen Sie **Nicht konfiguriert** aus, damit der Datenverkehr durch den VPN-Tunnel oder durch das Mobilfunknetz fließen kann.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Außerdem können Sie Kioskmodusprofile für [Android](device-restrictions-android.md#kiosk)- und [Windows 10](kiosk-settings.md)-Geräte erstellen.
