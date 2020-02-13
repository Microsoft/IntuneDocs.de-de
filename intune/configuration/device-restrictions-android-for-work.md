---
title: Android Enterprise-Geräteeinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: 'Auf Geräten mit Android Enterprise oder Android for Work können Sie auf dem Gerät Einstellungen einschränken, darunter folgende: Kopieren und Einfügen, Benachrichtigungen anzeigen, App-Berechtigungen, Datenfreigabe, Kennwortlänge, Anmeldefehler, Entsperren per Fingerabdruck, Wiederverwenden von Kennwörtern und Aktivieren der Freigabe von Geschäftskontakten per Bluetooth. Konfigurieren Sie Geräte als dedizierten Gerätekiosk zur Ausführung einer oder mehrerer Apps.'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 122f0b0194a96b844e274ab39a73224eb23cc6b3
ms.sourcegitcommit: 9b29478f815e10c46c8030abe0146d601ce0e28c
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051591"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie auf Android Enterprise-Geräten steuern können. Verwenden Sie als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) diese Einstellungen, um Funktionen zuzulassen oder zu deaktivieren, Apps auf dedizierten Geräten auszuführen, die Sicherheit zu steuern usw.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](device-restrictions-configure.md)

## <a name="device-owner-only"></a>Nur Gerätebesitzer

Diese Einstellungen gelten für Android Enterprise-Registrierungstypen, bei denen das gesamte Gerät von Intune verwaltet wird, z. B. vollständig verwaltete Android Enterprise-Geräte oder dedizierte Android Enterprise-Geräte.

### <a name="general-settings"></a>Allgemeine Einstellungen

- **Bildschirmaufnahme:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Screenshots oder Bildschirmaufnahmen auf dem Gerät vorgenommen werden. Zudem wird verhindert, dass der Inhalt auf Anzeigegeräten angezeigt wird, die über keine sichere Videoausgabe verfügen. **Nicht konfiguriert** erlaubt dem Benutzer, den Bildschirminhalt als Bild zu erfassen.
- **Kamera:** Wählen Sie **Blockieren** aus, um den Zugriff auf die Kamera des Geräts zu verhindern. **Nicht erforderlich** ermöglicht den Zugriff auf die Kamera des Geräts.
- **Standardberechtigungsrichtlinie:** Diese Einstellung definiert die Standardberechtigungsrichtlinie für Anforderungen für Laufzeitberechtigungen. Folgende Werte sind zulässig:
  - **Gerätestandard:** Die Standardeinstellung des Geräts wird verwendet.
  - **Eingabeaufforderung:** Der Benutzer wird dazu aufgefordert, die Berechtigung zu genehmigen.
  - **Automatisch zulassen:** Berechtigungen werden automatisch gewährt.
  - **Automatisch ablehnen:** Berechtigungen werden automatisch verweigert.
- **Datums- und Uhrzeitänderungen:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer manuell Datum und Uhrzeit einstellen. **Nicht konfiguriert** ermöglicht Benutzern, Datum und Uhrzeit auf dem Gerät einzustellen.
- **Änderung der Lautstärke:** **Blockieren** verhindert, dass Benutzer die Lautstärke des Geräts ändern können. Außerdem wird die Hauptlautstärke des Geräts stummgeschaltet. **Nicht konfiguriert** ermöglicht die Verwendung der Lautstärkeeinstellungen am Gerät.
- **Auf Werkseinstellungen zurücksetzen:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer die Option zum Zurücksetzen auf Werkseinstellungen in den Einstellungen des Geräts verwenden. **Nicht konfiguriert** ermöglicht Benutzern, diese Einstellung auf dem Gerät zu verwenden.
- **Abgesicherter Start:** Wenn Sie **Blockieren** auswählen, können Benutzer das Gerät nicht im abgesicherten Modus neu starten. **Nicht konfiguriert** ermöglicht Benutzern, das Gerät im abgesicherten Modus neu zu starten.
- **Statusleiste:** Wählen Sie **Blockieren** aus, um den Zugriff auf die Statusleiste einschließlich Benachrichtigungen und Schnelleinstellungen zu verhindern. **Nicht konfiguriert** ermöglicht Benutzern den Zugriff auf die Statusleiste.
- **Roamingdatendienste:** Wählen Sie **Blockieren** aus, um Datenroaming über das Mobilfunknetz zu verhindern. **Nicht konfiguriert** erlaubt das Datenroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.
- **Änderung der WLAN-Einstellungen:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer vom Gerätebesitzer erstellte WLAN-Einstellungen ändern. Benutzer können eigene WLAN-Konfigurationen erstellen. **Nicht konfiguriert** ermöglicht Benutzern, die WLAN-Einstellungen auf dem Gerät ändern.
- **Konfiguration des WLAN-Zugriffspunkts:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer WLAN-Konfigurationen erstellen oder ändern. **Nicht konfiguriert** ermöglicht Benutzern, die WLAN-Einstellungen auf dem Gerät ändern.
- **Bluetooth-Konfiguration:** Wählen Sie **Blockieren** aus, um Benutzer daran zu hindern, Bluetooth auf dem Gerät zu konfigurieren. **Nicht konfiguriert** ermöglicht die Verwendung von Bluetooth auf dem Gerät.
- **Tethering und Zugriff auf Hotspots:** Wählen Sie **Blockieren** aus, um Tethering und Zugriff auf portable Hotspots zu verhindern. **Nicht konfiguriert** ermöglicht Tethering und Zugriff auf portable Hotspots.
- **USB-Speicher:** Wählen Sie **Zulassen** aus, um auf USB-Speicher auf dem Gerät zuzugreifen. **Nicht konfiguriert** verhindert den Zugriff auf USB-Speicher.
- **USB-Dateiübertragung:** Wählen Sie **Blockieren** aus, um das Übertragen von Dateien per USB zu verhindern. **Nicht konfiguriert** ermöglicht das Übertragen von Dateien.
- **Externe Medien:** Wählen Sie **Blockieren** aus, um die Verwendung externer Medien oder das Herstellen einer Verbindung mit solchen auf dem Gerät zu verhindern. **Nicht konfiguriert** lässt externe Medien auf dem Gerät zu.
- **Daten mithilfe von NFC übertragen:** Wählen Sie **Blockieren** aus, um die Verwendung der Nahfeldkommunikation (Near Field Communication, NFC) zum Übertragen von Dateien aus Apps zu verhindern. **Nicht konfiguriert** ermöglicht die Verwendung von NFC zum Freigeben von Daten zwischen Geräten.
- **Debugfunktionen:** Wenn Sie **Zulassen** auswählen, können Benutzer Features zum Debuggen auf dem Gerät verwenden. **Nicht konfiguriert** verhindert, dass Benutzer Features zum Debuggen auf dem Gerät verwenden.
- **Mikrofonanpassung:** Wenn Sie **Blockieren** auswählen, können Benutzer weder die Stummschaltung des Mikrofons aufheben noch die Lautstärke am Mikrofon anpassen. **Nicht konfiguriert** ermöglicht dem Benutzer, die Lautstärke am Mikrofon des Geräts anzupassen.
- **E-Mail-Adressen für Schutz vor Zurücksetzung auf Werkseinstellungen:** Wählen Sie **E-Mail-Adressen für Google-Konto** aus. Geben Sie die E-Mail-Adressen der Geräteadministratoren ein, die das Gerät entsperren können, nachdem es zurückgesetzt wurde. Achten Sie darauf, dass Sie die E-Mail-Adressen durch ein Semikolon trennen, z. B. `admin1@gmail.com;admin2@gmail.com`. Wenn keine E-Mail-Adresse eingegeben wird, kann jeder das Gerät entsperren, sobald die Werkseinstellungen wiederhergestellt sind. Diese E-Mail-Adressen sind nur gültig, wenn eine nicht von einem Benutzer initiierte Zurücksetzung auf Werkseinstellungen ausgeführt wird, z. B. die Ausführung einer Zurücksetzung auf Werkseinstellungen über das Wiederherstellungsmenü.
- **Notausstieg für Netzwerk:** Das **Aktivieren** dieser Option erlaubt Benutzern, das Feature „Notausstieg für Netzwerk“ zu aktivieren. Wenn beim Starten des Geräts keine Netzwerkverbindung hergestellt wird, fordert die Notausstiegsfunktion zum Herstellen einer vorübergehenden Verbindung mit einem Netzwerk und Aktualisieren der Geräterichtlinie auf. Nach dem Anwenden der Richtlinie wird das temporäre Netzwerk ignoriert, und das Gerät setzt den Start fort. Dieses Feature verbindet Geräte mit einem Netzwerk, wenn:
  - Kein geeignetes Netzwerk in der letzten Richtlinie enthalten ist.
  - Das Gerät im Aufgabensperrmodus in eine App startet.
  - Der Benutzer die Einstellungen für das Gerät nicht erreichen kann.

  **Nicht konfiguriert** verhindert, dass Benutzer die Netzwerk-Notausstiegsfunktion auf dem Gerät aktivieren.

- **Systemupdate:** Hier können Sie eine Option auswählen, um zu definieren, wie das Gerät Over-the-Air-Updates verarbeitet:
  - **Gerätestandard:** Die Standardeinstellung des Geräts wird verwendet.
  - **Automatisch:** Updates werden ohne Interaktion mit dem Benutzer automatisch installiert. Durch das Festlegen dieser Richtlinie werden sofort alle ausstehenden Updates installiert.
  - **Zurückgestellt:** Updates werden für 30 Tage zurückgestellt. Nach Ablauf der 30 Tage fordert Android den Benutzer zur Installation des Updates auf. Gerätehersteller oder Mobilfunkanbieter können verhindern (ausschließen), dass wichtige Sicherheitsupdates zurückgestellt werden. Bei einem ausgeschlossenen Update wird dem Benutzer eine Systembenachrichtigung auf dem Gerät angezeigt.
  - **Wartungsfenster:** Updates werden automatisch in einem täglichen Wartungsfenster installiert, das Sie in Intune festlegen. Die Installation wird 30 Tage lang täglich versucht, und es kann aufgrund von zu geringem Speicherplatz oder Akkustand ein Fehler auftreten. Nach 30 Tagen wird der Benutzer von Android zum Installieren aufgefordert. Dieses Fenster wird auch verwendet, um Updates für Google Play-Apps zu installieren. Verwenden Sie diese Option für dedizierte Geräte wie etwa Kioskgeräte, da Apps, die im Vordergrund auf einem dedizierten Gerät im Einzelanwendungsmodus ausgeführt werden, aktualisiert werden können.

- **Benachrichtigungsfenster:** Wenn **Deaktivieren** ausgewählt ist, werden Fensterbenachrichtigungen, wie Popups, eingehende Anrufe, ausgehende Anrufe, Systemwarnungen und Systemfehler, nicht auf dem Gerät angezeigt. Bei **Nicht konfiguriert** wird die Standardeinstellung des Betriebssystems verwendet, wodurch Benachrichtigungen möglicherweise angezeigt werden.
- **Hinweise zur ersten Verwendung überspringen:** **Aktivieren** führt dazu, dass Vorschläge von Apps beim Durchführen von Tutorials oder Hinweise beim Start einer App ausgeblendet oder übersprungen werden. Bei Festlegung auf **Nicht konfiguriert** wird die Standardeinstellung des Betriebssystems verwendet, wodurch diese Vorschläge beim Starten der App möglicherweise angezeigt werden.

### <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit

- **Bedrohungsüberprüfung für Apps:** Die Standardeinstellung **Anfordern** aktiviert Google Play Protect so, dass Apps vor und nach der Installation überprüft werden. Wenn das Tool eine Bedrohung erkennt, kann es den Benutzer warnen, damit er die App vom Gerät entfernt. Bei Wahl von **Nicht konfiguriert** wird Google Play Protect nicht zum Überprüfen von Apps aktiviert oder ausgeführt.

### <a name="dedicated-device-settings"></a>Einstellungen dedizierter Geräte

Verwenden Sie diese Einstellungen, um eine Umgebung im Kioskstil auf Ihren dedizierten Geräten zu konfigurieren. Sie können ein Gerät so konfigurieren, dass eine App oder mehrerer Apps ausgeführt werden. Im Kioskmodus eines Geräts stehen nur die Apps zur Verfügung, die Sie hinzufügen. Diese Einstellungen gelten für dedizierte Android Enterprise-Geräte. Sie gelten nicht für vollständig verwaltete Android Enterprise-Geräte.

**Kioskmodus:** Wählen Sie aus, ob auf dem Gerät eine App oder mehrere Apps ausgeführt werden.

- **Einzelne App**: Benutzer können auf dem Gerät nur auf eine einzelne App zugreifen. Wenn das Gerät gestartet wird, wird nur die jeweilige App gestartet. Benutzer können keine neuen Apps öffnen oder die ausgeführte App ändern.

  - **Verwaltete App auswählen**: Wählen Sie die verwaltete Google Play-App aus der Liste aus.

    Wenn keine Apps aufgelistet werden, können Sie dem Gerät [einige Android-Apps hinzufügen](../apps/apps-add-android-for-work.md). Achten Sie darauf, [die App der Gerätegruppe zuzuweisen, die für Ihre dedizierten Geräte erstellt wurde](../apps/apps-deploy.md).

  > [!IMPORTANT]
  > Wenn Sie den Kioskmodus für einzelne Apps verwenden, funktionieren Apps mit Wähltasten/Telefon-Apps möglicherweise nicht ordnungsgemäß. 
  
- **Multi-App**: Benutzer können auf dem Gerät nur auf eine begrenzte Anzahl von Apps zugreifen. Wenn das Gerät gestartet wird, werden nur die von Ihnen hinzugefügten Apps gestartet. Sie können auch einige Weblinks hinzufügen, die Benutzer öffnen können. Wenn die Richtlinie angewendet wird, können Benutzer die Symbole für die zulässigen Apps auf dem Startbildschirm sehen.

  > [!IMPORTANT]
  > Für dedizierte Geräte mit mehreren Apps **muss** die [Managed Home Screen-App](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) aus Google Play:
  >   - in Intune [als Client-App hinzugefügt](../apps/apps-add-android-for-work.md) sein
  >   - [der Gerätegruppe zugewiesen sein](../apps/apps-deploy.md), die für Ihre dedizierten Geräte erstellt wurde.
  >
  > Die **Managed Home Screen**-App muss sich nicht im Konfigurationsprofil befinden, aber als Client-App hinzugefügt werden. Wenn die **Managed Home Screen**-App als Client-App hinzugefügt wird, werden alle anderen Apps, die Sie im Konfigurationsprofil hinzufügen, in der **Managed Home Screen**-App als Symbole angezeigt.
  >
  > Wenn Sie den Normalmodus (Kiosk mit mehreren Apps) verwenden, funktionieren Apps mit Wähltasten/Telefon-Apps möglicherweise nicht ordnungsgemäß. 

  - **Hinzufügen:** Wählen Sie Ihre Apps aus der Liste aus.

    Wenn die **Managed Home Screen**-App nicht aufgeführt wird, [fügen Sie sie aus Google Play hinzu](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Achten Sie darauf, [die App der Gerätegruppe zuzuweisen](../apps/apps-deploy.md), die für Ihre dedizierten Geräte erstellt wurde.

    Sie können auch andere [Android-Apps](../apps/apps-add-android-for-work.md) und [Web-Apps](../apps/web-app.md) hinzufügen, die von Ihrer Organisation für das Gerät erstellt wurden. Achten Sie darauf, [die App der Gerätegruppe zuzuweisen, die für Ihre dedizierten Geräte erstellt wurde](../apps/apps-deploy.md).

  - **Virtuelle Startschaltfläche:** Eine Softkey-Schaltfläche, die Benutzer auf den verwalteten Startbildschirm zurückleitet, damit Benutzer zwischen Apps wechseln können. Folgende Optionen sind verfügbar:

    - **Nicht konfiguriert** (Standardwert): Es wird keine Startschaltfläche angezeigt. Benutzer müssen die Schaltfläche „Zurück“ verwenden, um zwischen Apps wechseln zu können.
    - **Nach oben wischen:** Eine Startschaltfläche wird angezeigt, wenn ein Benutzer auf dem Gerät nach oben wischt.
    - **Unverankert:** Auf dem Gerät wird dauerhaft eine unverankerte Startschaltfläche angezeigt.

  - **Kioskmodus verlassen:** Wählen Sie **Aktivieren** aus, um Administratoren zu ermöglichen, den Kioskmodus vorübergehend zu beenden, um das Gerät zu aktualisieren. Um dieses Feature verwenden zu können, führt der Administrator Folgendes aus:
  
    1. Weiteres Betätigen der Schaltfläche „Zurück“, bis die Schaltfläche **Kiosk beenden** angezeigt wird. 
    2. Auswählen der Schaltfläche **Kiosk beenden** und Eingabe der PIN für den **Code zum Verlassen des Kioskmodus**.
    3. Wenn Sie fertig sind, wählen Sie die App **Verwalteter Startbildschirm** aus. Mit diesem Schritt wird das Gerät erneut im Multi-App-Kioskmodus gesperrt.

      Wenn **Nicht konfiguriert** festgelegt ist, können Administratoren den Kioskmodus nicht pausieren. Wenn der Administrator weiterhin die Schaltfläche „Zurück“ betätigt und die Schaltfläche **Kiosk beenden** auswählt, wird eine Meldung angezeigt, dass eine Kennung erforderlich ist.

    - **Code zum Verlassen des Kioskmodus:** Geben Sie eine 4-6-stellige numerische PIN ein. Der Administrator verwendet diese PIN zum vorübergehenden Anhalten des Kioskmodus.

  - **Benutzerdefinierten URL-Hintergrund festlegen:** Geben Sie eine URL zum Anpassen des Hintergrundbildschirms auf dem dedizierten Gerät ein.

    > [!NOTE]
    > In den meisten Fällen empfehlen wir, mit Bildern mit mindestens den folgenden Größen zu beginnen:
    >
    > - Smartphone: 1080 x 1920 Pixel
    > - Tablet: 1920 × 1080 Pixel
    >
    > Für ein optimales Erlebnis und scharfe Details wird empfohlen, Bildobjekte gerätebezogen gemäß den Displayspezifikationen zu erstellen.
    >
    > Moderne Displays haben höhere Pixeldichten und können entsprechende Bilder mit 2K-/4K-Auflösung anzeigen.

  - **WLAN-Konfiguration:** **Aktivieren** zeigt die WLAN-Steuerelement auf dem verwalteten Startbildschirm an und ermöglicht es Endbenutzern, das Gerät mit anderen WLAN-Netzwerken zu verbinden. Durch Aktivieren dieses Features wird auch der Gerätestandort aktiviert. **Nicht konfiguriert** (Standardwert) zeigt das WLAN-Steuerelement nicht auf dem verwalteten Startbildschirm an. Dieser Wert verhindert, dass Benutzer Verbindungen mit WLAN-Netzwerken herstellen, während Sie den verwalteten Startbildschirm verwenden.

  - **Bluetooth-Konfiguration:** **Aktivieren** zeigt das Bluetooth-Steuerelement auf dem verwalteten Startbildschirm an und ermöglicht es Endbenutzern, Geräte über Bluetooth miteinander zu koppeln. Durch Aktivieren dieses Features wird auch der Gerätestandort aktiviert. **Nicht konfiguriert** (Standardwert) zeigt das Bluetooth-Steuerelement nicht auf dem verwalteten Startbildschirm an. Dieser Wert verhindert, dass Benutzer Bluetooth konfigurieren und Geräte koppeln, während sie den verwalteten Startbildschirm verwenden.

  - **Zugriff auf Taschenlampe:** **Aktivieren** zeigt das Taschenlampensteuerfeld auf dem verwalteten Startbildschirm an und ermöglicht es Endbenutzern, die Taschenlampe ein- oder auszuschalten. **Nicht konfiguriert** (Standardwert) zeigt das Taschenlampensteuerelement nicht auf dem verwalteten Startbildschirm an. Dieser Wert verhindert, dass Benutzer die Taschenlampe verwenden, während sie den verwalteten Startbildschirm verwenden.

  - **Medienlautstärkeregler:** **Aktivieren** zeigt den Medienlautstärkeregler auf dem verwalteten Startbildschirm an und ermöglicht es Endbenutzern, die Medienlautstärke auf dem Gerät mithilfe eines Reglers anzupassen. **Nicht konfiguriert** (Standardwert) zeigt den Medienlautstärkeregler nicht auf dem verwalteten Startbildschirm an. Dieser Wert verhindert, dass Benutzer die Medienlautstärke auf dem Gerät anpassen können, während sie den verwalteten Startbildschirm verwenden, außer die Tasten ihrer Hardware unterstützen dies. 

  - **Bildschirmschonermodus:** **Aktivieren** zeigt einen Bildschirmschoner auf dem verwalteten Startbildschirm, wenn das Gerät gesperrt ist oder im Fall eines Timeouts. **Nicht konfiguriert** (Standardwert) zeigt keinen Bildschirmschoner auf dem verwalteten Startbildschirm.

    Wenn diese Einstellung aktiviert ist, konfigurieren Sie auch die folgende Einstellung:

    - **Benutzerdefiniertes Hintergrundbild für Bildschirmschoner festlegen:** Geben Sie die URL zu einem benutzerdefinierten PNG-, JPG-, JPEG-, GIF-, MBP-, WebP- oder ICO-Bild an. Geben Sie z. B. Folgendes ein:

      - `http://www.contoso.com/image.jpg`
      - `www.contoso.com/image.bmp`
      - `https://www.contoso.com/image.webp`

      Wenn Sie keine URL eingeben, wird das Standardbild des Geräts verwendet, wenn es ein Standardbild gibt.
      
      > [!TIP]
      > Alle URLs zu Dateiressourcen, die in das Bitmap-Format umgewandelt werden können, werden unterstützt.

    - **Die Anzahl von Sekunden, die das Gerät den Bildschirmschoner anzeigt, bevor der Bildschirm deaktiviert wird:** Wählen Sie aus, wie lange der Bildschirmschoner auf dem Gerät angezeigt werden soll. Geben Sie einen Wert zwischen 0 und 9999999 Sekunden ein. Der Standardwert beträgt `0` Sekunden. Wenn das Feld leer gelassen wird oder auf `0` (null) festgelegt ist, ist der Bildschirmschoner solange aktiv, bis ein Benutzer mit dem Gerät interagiert.
    - **Anzahl von Sekunden, in denen das Gerät inaktiv ist, bevor der Bildschirmschoner angezeigt wird:** Wählen Sie aus, wie lange ein Gerät inaktiv sein kann, bevor der Bildschirmschoner angezeigt wird. Geben Sie einen Wert zwischen 1 und 9999999 Sekunden ein. Der Standardwert beträgt `30` Sekunden. Geben Sie eine Zahl ein, die größer als null (`0`) ist.
    - **Vor dem Start des Bildschirmschoners Medien ermitteln:** **Aktivieren** (Standardwert) zeigt den Bildschirmschoner nicht an, wenn auf dem Gerät Audio- oder Videodateien wiedergeben werden. **Nicht konfiguriert** zeigt den Bildschirmschoner an, auch wenn Audiodaten oder Videos abgespielt werden.

### <a name="device-password-settings"></a>Gerätekennworteinstellungen

- **Sperrbildschirm deaktivieren**: Wenn Sie **Deaktivieren** auswählen, können Benutzer das Bildschirmsperrfeature Keyguard nicht auf dem Gerät verwenden. **Nicht konfiguriert** ermöglicht dem Benutzer, die Keyguard-Features zu verwenden.
- **Deaktivierte Sperrbildschirmfeatures**: Wenn Keyguard auf dem Gerät aktiviert ist, wählen Sie die Features aus, die Sie deaktivieren möchten. Ist beispielsweise **Kamera absichern** ausgewählt, ist die Kamerafunktion auf dem Gerät deaktiviert. Alle nicht ausgewählten Features sind auf dem Gerät aktiviert.

  Diese Features sind für Benutzer verfügbar, wenn das Gerät gesperrt ist. Benutzer können mit einem Häkchen versehene Features weder anzeigen noch darauf zugreifen.

- **Erforderlicher Kennworttyp:** Hiermit wird der Typ des erforderlichen Kennworts für das Gerät definiert. Folgende Optionen sind verfügbar:
  - **Gerätestandard**
  - **Kennwort erforderlich, keine Einschränkungen**
  - **Schwach biometrisch**: [Vergleich von stark und schwach biometrisch](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (öffnet Android-Website)
  - **Numerisch**: Kennwort darf nur aus Zahlen bestehen. Beispiel: `123456789`. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
  - **Numerisch, komplex:** Sich wiederholende oder fortlaufende Ziffern wie „1111“ oder „1234“ sind nicht zulässig. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
  - **Alphabetisch**: Buchstaben des Alphabets sind erforderlich. Zahlen und Symbole sind nicht erforderlich. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
  - **Alphanumerisch**: Schließt Großbuchstaben, Kleinbuchstaben und Ziffern ein. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
  - **Alphanumerisch mit Symbolen**: Schließt Großbuchstaben, Kleinbuchstaben, Ziffern, Interpunktionszeichen und Symbole ein. Geben Sie außerdem Folgendes ein:

    - **Minimale Kennwortlänge:** Geben Sie die Mindestlänge des Kennworts ein (4 bis 16 Zeichen).
    - **Erforderliche Zeichenanzahl**: Geben Sie die erforderliche Anzahl von Zeichen des Kennworts ein (0 bis 16 Zeichen).
    - **Erforderliche Anzahl Kleinbuchstaben**: Geben Sie die erforderliche Anzahl Kleinbuchstaben für das Kennwort ein, von 0 bis 16 Zeichen.
    - **Erforderliche Anzahl Großbuchstaben**: Geben Sie die erforderliche Anzahl Großbuchstaben für das Kennwort ein, von 0 bis 16 Zeichen.
    - **Erforderliche Anzahl anderer Zeichen als Buchstaben**: Geben Sie die erforderliche Anzahl anderer Zeichen als Buchstaben (alles außer Buchstaben im Alphabet) für das Kennwort ein, von 0 bis 16 Zeichen.
    - **Erforderliche Anzahl numerischer Zeichen**: Geben Sie die erforderliche Anzahl numerischer Zeichen (`1`, `2`, `3` usw.) für das Kennwort ein, von 0 bis 16 Zeichen.
    - **Erforderliche Anzahl Symbole**: Geben Sie die erforderliche Anzahl der Symbole (`&`, `#`, `%` usw.) für das Kennwort ein, von 0 bis 16 Zeichen.

- **Anzahl Tage bis zum Kennwortablauf**: Geben Sie die Anzahl der Tage von 1–365 an, bis das Gerätekennwort geändert werden muss. Geben Sie beispielsweise zum Ändern des Kennworts nach 60 Tagen `60` ein. Wenn das Kennwort abläuft, werden Benutzer aufgefordert, ein neues Kennwort zu erstellen.
- **Anzahl erforderlicher Kennwörter, bevor ein Benutzer ein Kennwort wiederverwenden kann**: Geben Sie die Anzahl von vorherigen Kennwörtern ein, die nicht wiederverwendet werden dürfen, von 1 bis 24. Verwenden Sie diese Einstellung, um zu verhindern, dass der Benutzer zuvor verwendete Kennwörter erstellt.
- **Anzahl von fehlgeschlagenen Anmeldungen, bevor das Gerät zurückgesetzt wird:** Geben Sie die Anzahl der Anmeldungen von 4 bis 11 ein, die fehlschlagen können, bevor das Gerät zurückgesetzt wird.

### <a name="power-settings"></a>Energieeinstellungen

- **Zeit bis Bildschirmsperre:** Geben Sie die maximale Zeit an, die ein Benutzer als Zeit bis zur Bildschirmsperre festlegen kann. Wenn Sie als Wert beispielsweise **10 Minuten** festlegen, können Benutzer eine beliebige Zeit zwischen 15 Sekunden und zehn Minuten wählen. Wenn **Nicht konfiguriert** (Standardwert) festgelegt ist, wird diese Einstellung von Intune nicht geändert oder verwaltet.

- **Bildschirm aktiviert, wenn Gerät angeschlossen ist:** Hiermit kann ausgewählt werden, bei welchen Stromquellen der Bildschirm des Geräts aktiviert bleibt, wenn es angeschlossen ist.

### <a name="users-and-accounts-settings"></a>Einstellungen für Benutzer und Konten

- **Neue Benutzer hinzufügen:** Wenn Sie **Blockieren** auswählen, können Benutzer keine neuen Benutzer hinzufügen. Jeder Benutzer hat einen persönlichen Bereich auf dem Gerät für benutzerdefinierte Startseiten, Konten, Apps und Einstellungen. Eine Festlegung auf **Nicht konfiguriert** (Standardeinstellung) ermöglicht es Benutzern, dem Gerät andere Benutzer hinzufügen.
- **Entfernen von Benutzern:** Wenn Sie **Blockieren** auswählen, können Benutzer keine Benutzer entfernen. Eine Festlegung auf **Nicht konfiguriert** (Standardeinstellung) ermöglicht es Benutzern, andere Benutzer vom Gerät zu entfernen.
- **Kontoänderungen** (nur dedizierte Geräte): Wählen Sie **Blockieren** aus, damit Benutzer Konten nicht ändern können. Eine Festlegung auf **Nicht konfiguriert** (Standardeinstellung) ermöglicht es Benutzern, Benutzerkonten auf dem Gerät zu aktualisieren.

  > [!NOTE]
  > Diese Einstellung gilt nicht für vollständig verwaltete Geräte von Gerätebesitzern. Wenn Sie diese Einstellung konfigurieren, wird die Einstellung ignoriert und hat keine Auswirkungen.

- **Benutzer kann Anmeldeinformationen konfigurieren:** **Blockieren** verhindert, dass Benutzer Zertifikate konfigurieren, die Geräten zugewiesen sind, auch wenn es sich um Geräte handelt, die keinem Benutzerkonto zugewiesen sind. **Nicht konfiguriert** kann es Benutzern ermöglichen, ihre Anmeldeinformationen zu konfigurieren oder zu ändern, wenn sie im Keystore darauf zugreifen. 
- **Persönliche Google-Konten:** **Blockieren** verhindert, dass Benutzer ihre privaten Google-Konten auf dem Gerät hinzufügen. **Nicht konfiguriert** (Standardwert) ermöglicht Benutzern das Hinzufügen ihres persönlichen Google-Kontos.

### <a name="applications"></a>Applications

- **Installation aus unbekannten Quellen zulassen:** Wählen Sie **Zulassen** aus, damit die Benutzer **Unbekannte Quellen** aktivieren können. Diese Einstellung ermöglicht die Installation von Apps aus unbekannten Quellen, einschließlich anderer Quellen als Google Play Store. **Nicht konfiguriert** verhindert, dass Benutzer **Unbekannte Quellen** nutzen.
- **Zugriff auf alle Apps im Google Play Store zulassen**: Wenn diese Option auf **Zulassen** festgelegt ist, erhalten Benutzer Zugriff auf alle Apps im Google Play Store. Sie erhalten keinen Zugriff auf die Apps, die der Administrator in [Client-Apps](../apps/apps-add-android-for-work.md) sperrt. **Nicht konfiguriert** zwingt Benutzer, nur auf die Apps zuzugreifen, die der Administrator im Google Play Store zur Verfügung stellt, oder auf die Apps, die in [Client-Apps](../apps/apps-add-android-for-work.md) erforderlich sind.
- **Automatische App-Updates:** Wählen Sie diese Option aus, wenn automatische Updates installiert werden. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert**
  - **Benutzerauswahl**
  - **Nie**
  - **Nur WLAN**
  - **Immer**

### <a name="connectivity"></a>Verbindung

- **Always On-VPN:** Wählen Sie **Aktivieren** aus, um einen VPN-Client so festzulegen, dass er automatisch eine Verbindung mit dem VPN herstellt und erneut herstellt. Always On-VPN-Verbindungen bleiben erhalten oder werden sofort hergestellt, wenn der Benutzer sein Gerät sperrt, das Gerät neu gestartet wird oder das drahtlose Netzwerk sich ändert. 

  Wählen Sie **Nicht konfiguriert** aus, um das Always On-VPN für alle VPN-Clients zu deaktivieren.

  > [!IMPORTANT]
  > Stellen Sie sicher, dass Sie nur eine Always On-VPN-Richtlinie auf einem einzelnen Gerät bereitstellen. Die Bereitstellung mehrerer Always On-VPN-Richtlinien auf einem einzelnen Gerät wird nicht unterstützt.

- **VPN-Client:** Wählen Sie einen VPN-Client aus, der Always On unterstützt. Folgende Optionen sind verfügbar:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Benutzerdefiniert
    - **Paket-ID:** Geben Sie die Paket-ID der App im Google Play Store ein. Wenn z. B. die URL für die App im Play Store `https://play.google.com/store/details?id=com.contosovpn.android.prod` lautet, dann ist die Paket-ID `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  > - Der von Ihnen ausgewählte VPN-Client muss auf dem Gerät installiert sein und VPN pro Anwendung in Arbeitsprofilen unterstützen. Andernfalls tritt ein Fehler auf. 
  > - Sie müssen die VPN-Client-App im **verwalteten Google Play Store** genehmigen, die App mit Intune synchronisieren und die App auf dem Gerät bereitstellen. Danach wird die App im Arbeitsprofil des Benutzers installiert.
  > - Sie müssen den VPN-Client dann trotzdem noch mit einem [VPN-Profil](vpn-settings-android-enterprise.md) oder über ein [App-Konfigurationsprofil](../apps/app-configuration-policies-use-android.md) konfigurieren.
  > - Es gibt eventuell bekannte Probleme bei der Verwendung von VPN pro App mit F5 Access for Android 3.0.4. Weitere Informationen finden Sie unter [F5's release notes for F5 Access for Android 3.0.4 (Versionshinweise zu F5 Access for Android 3.0.4)](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android).

- **Sperrmodus:** Wählen Sie **Aktivieren** aus, um den gesamten Netzwerkdatenverkehr zu zwingen, den VPN-Tunnel zu verwenden. Wenn keine Verbindung zum VPN hergestellt wird, hat das Gerät keinen Netzwerkzugriff.

  Wählen Sie **Nicht konfiguriert** aus, damit der Datenverkehr durch den VPN-Tunnel oder durch das Mobilfunknetz fließen kann.

- **Empfohlener globaler Proxy:** Wählen Sie **Aktivieren** aus, um den Geräten einen globalen Proxy hinzuzufügen. Wenn diese Einstellung aktiviert ist, wird für HTTP- und HTTPS-Datenverkehr einschließlich einiger Apps auf dem Gerät den von Ihnen eingegebenen Proxy. Dieser Proxy ist nur eine Empfehlung. Es ist möglich, dass einige Apps den Proxy nicht verwenden. **Nicht konfiguriert** (Standardwert) fügt keinen empfohlenen globalen Proxy hinzu.

  Weitere Informationen zu diesem Feature finden Sie auf der Android-Website zu [setRecommendedGlobalProxy](https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setRecommendedGlobalProxy(android.content.ComponentName,%20android.net.ProxyInfo)).

  Wenn diese Einstellung aktiviert ist, geben Sie auch den **Proxytyp** ein. Folgende Optionen sind verfügbar:

  - **Direkt:** : Wählen Sie diese Option aus, um die Proxyserverdetails einschließlich folgender Informationen manuell einzugeben:
    - **Host:** Geben Sie den Hostnamen oder die IP-Adresse Ihres Proxy Servers ein. Geben Sie beispielsweise `proxy.contoso.com` oder `127.0.0.1` ein.
    - **Portnummer:** Geben Sie die vom Proxyserver verwendete TCP-Portnummer ein. Geben Sie beispielsweise `8080` ein.
    - **Ausgeschlossene Hosts:** Geben Sie eine Liste von Hostnamen oder IP-Adressen ein, die den Proxy nicht verwenden. Diese Liste kann ein Asterisk-Platzhalterzeichen (`*`) und mehrere durch Semikolons (`;`) getrennte Hosts ohne Leerzeichen. Geben Sie beispielsweise `127.0.0.1;web.contoso.com;*.microsoft.com` ein.

  - **Automatische Proxy-Konfiguration:** Geben Sie die **PAC-URL** in einem Proxyautokonfigurationsskript. Geben Sie beispielsweise `https://proxy.contoso.com/proxy.pac` ein.

    Weitere Informationen zu PAC-Dateien finden Sie unter [Proxy Auto-Configuration (PAC) file (Datei für die automatische Proxykonfiguration)](https://developer.mozilla.org/docs/Web/HTTP/Proxy_servers_and_tunneling/Proxy_Auto-Configuration_(PAC)_file) (öffnet eine Drittanbieterwebsite).

## <a name="work-profile-only"></a>Nur Arbeitsprofil

Diese Einstellung gelten für Android Enterprise-Registrierungstypen, bei denen nur das Arbeitsprofil von Intune verwaltet wird, z. B. die Registrierung für ein Android Enterprise-Arbeitsprofil auf einem privaten oder BYOD-Gerät.

### <a name="work-profile-settings"></a>Arbeitsprofileinstellungen

#### <a name="general"></a>Allgemein

- **Kopieren und Einfügen zwischen Arbeitsprofilen und persönlichen Profilen:** Wenn Sie **Blockieren** auswählen, wird das Kopieren und Einfügen zwischen Arbeits-Apps und persönlichen Apps verhindert. **Nicht konfiguriert** ermöglicht Benutzern, Daten mithilfe von Kopieren und Einfügen mit Apps im persönlichen Profil freizugeben. 
- **Datenaustausch zwischen Arbeitsprofilen und persönlichen Profilen:** Wählen Sie diese Option aus, damit Apps im Arbeitsprofil Daten mit Apps im persönlichen Profil austauschen können. Sie können z.B. Freigabeaktionen in Anwendungen steuern, wie etwa die Option **Freigeben**. in der Chrome-Browser-App. Diese Einstellung gilt nicht für das Verhalten beim Kopieren/Einfügen der Zwischenablage. Ihre Freigabeoptionen:
  - **Gerätestandard:** Dies ist das standardmäßige Freigabeverhalten des Geräts, das abhängig von der Android-Version variiert. Standardmäßig ist die Freigabe von Daten des persönlichen Profils für das Arbeitsprofil zulässig. Die Freigabe von Daten des Arbeitsprofils für das persönliche Profil ist dagegen standardmäßig blockiert. Durch diese Einstellung wird die Freigabe von Daten des Arbeitsprofils für das persönliche Profil verhindert. Auf Geräten mit den Versionen 6.0 und höher blockiert Google die Freigabe vom persönlichen Profil zum Arbeitsprofil nicht.
  - **Apps im Arbeitsprofil können Freigabeanforderungen vom persönlichen Profil verarbeiten:** Dadurch wird das integrierte Android-Feature aktiviert, das die Freigabe vom persönlichen Profil zum Arbeitsprofil erlaubt. Wenn diese Option aktiviert ist, können Daten durch eine Freigabeanfrage einer App im persönlichen Profil für Apps im Arbeitsprofil freigegeben werden. Diese Einstellung ist das Standardverhalten für Android-Geräte, die frühere Versionen als 6.0 ausführen.
  - **Grenzüberschreitende Freigabe verhindern:** Diese Einstellung verhindert die Freigabe zwischen Arbeits- und privaten Profilen.
  - **Keine Einschränkungen bei Freigabe:** Diese Einstellung ermöglicht die Freigabe über die Grenzen eines Arbeitsprofils hinweg in beide Richtungen. Wenn Sie diese Einstellung auswählen, können Apps im Arbeitsprofil Daten für Apps ohne Badgeverwendung im persönlichen Profil freigeben. Diese Einstellung gestattet es verwalteten Apps im Arbeitsprofil, die Daten für Apps auf der nicht verwalteten Seite des Geräts freizugeben. Verwenden Sie diese Einstellung also mit Bedacht.

- **Arbeitsprofilbenachrichtigungen bei Gerätesperre:** Steuert, ob Apps im Arbeitsprofil Daten in Benachrichtigungen anzeigen können, wenn das Gerät gesperrt ist. **Blockieren** verhindert die Datenanzeige. **Nicht konfiguriert** zeigt die Daten an.
- **Standardmäßige App-Berechtigungen:** Legt die Standardberechtigungsrichtlinie für alle Apps im Arbeitsprofil fest. Ab Android 6 wird der Benutzer aufgefordert, bestimmte von den Apps benötigte Berechtigungen zu erteilen, wenn die App gestartet wird. Bei dieser Richtlinieneinstellung können Sie festlegen, ob Benutzer aufgefordert werden sollen, Berechtigungen für alle Apps im Arbeitsprofil zu gewähren. Beispielsweise können Sie dem Arbeitsprofil eine App zuweisen, die Standortzugriff benötigt. In der Regel fordert diese App den Benutzer dazu auf, den Standortzugriff durch die App zu genehmigen oder abzulehnen. Verwenden Sie diese Richtlinie, um Berechtigungen automatisch ohne Aufforderung zu erteilen, Berechtigungen ohne Aufforderung automatisch zu verweigern oder den Endbenutzer entscheiden zu lassen. Es stehen die folgenden Optionen zur Auswahl:
  - **Gerätestandard**
  - **Eingabeaufforderung**
  - **Automatisch gewähren**
  - **Automatisch verweigern**

  Sie können auch eine App-Konfigurationsrichtlinie verwenden, um Berechtigungen für einzelne Anwendungen zu erteilen (**Clientanwendungen** > **App-Konfigurationsrichtlinien**).

- **Konten hinzufügen und entfernen:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Endbenutzer Konten im Arbeitsprofil manuell hinzufügen oder daraus entfernen. Wenn Sie beispielsweise die Gmail-App in einem Android-Arbeitsprofil bereitstellen, können Sie verhindern, dass Benutzer Konten in diesem Arbeitsprofil hinzufügen oder entfernen. **Nicht konfiguriert** ermöglicht das Hinzufügen von Konten im Arbeitsprofil.  

  > [!NOTE]
  > Google-Konten können keinem Arbeitsprofil hinzugefügt werden.

- **Kontaktfreigabe über Bluetooth:** Ermöglicht den Zugriff auf Geschäftskontakte von einem anderen Gerät aus, z.B. aus dem Auto, wenn es mit Bluetooth gekoppelt ist. Diese Einstellung ist standardmäßig nicht konfiguriert, und Kontakte aus dem Arbeitsprofil werden nicht angezeigt. Klicken Sie auf **Aktivieren**, um diese Freigabe zuzulassen und um Kontakte aus dem Arbeitsprofil anzuzeigen. Diese Einstellung ist auf Geräten unter Android OS 6.0 und höher verfügbar, auf denen Arbeitsprofile eingerichtet wurden. Wenn Sie diese Einstellung aktivieren, können bestimmte Bluetooth-Geräte bei der ersten Verbindung Arbeitskontakte zwischenspeichern. Durch das Deaktivieren dieser Richtlinie nach einer ersten Kopplung bzw. Synchronisierung werden die Arbeitskontakte von einem Bluetooth-Gerät möglicherweise nicht entfernt.

- **Bildschirmaufnahme:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Screenshots oder Bildschirmaufnahmen auf dem Gerät im Arbeitsprofil vorgenommen werden. Zudem wird verhindert, dass der Inhalt auf Anzeigegeräten angezeigt wird, die über keine sichere Videoausgabe verfügen. **Nicht konfiguriert** ermöglicht das Erstellen von Screenshots.

- **Anrufer-ID des Geschäftskontakts im persönlichen Profil anzeigen:** Wenn diese Option aktiviert ist (**Nicht konfiguriert**), werden die Anruferdetails des Geschäftskontakts im persönlichen Profil angezeigt. Mit **Blockieren** wird die Anrufernummer des Arbeitskontakts im persönlichen Profil nicht angezeigt. Gilt für Android OS v6.0 und neuere Versionen.

- **Geschäftskontakte vom persönlichen Profil aus suchen:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer in Apps im persönlichen Profil nach Geschäftskontakten suchen. **Nicht erforderlich** ermöglicht das Suchen nach Arbeitskontakten im persönlichen Profil.

- **Kamera:** Wählen Sie **Blockieren** aus, um den Zugriff auf die Kamera des Geräts im Arbeitsprofil zu verhindern. Die Kamera im persönlichen Profil ist von dieser Einstellung nicht betroffen. **Nicht erforderlich** ermöglicht den Zugriff auf die Kamera im Arbeitsprofil.

- **Widgets aus Arbeitsprofil-Apps zulassen:** **Aktivieren** ermöglicht, dass Endbenutzer von Apps verfügbar gemachte Widgets auf dem Startbildschirm platzieren. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird dieses Feature deaktiviert.

  Angenommen, Outlook ist für das Arbeitsprofil Ihrer Benutzer installiert. Wenn diese Einstellung auf **Aktivieren** festgelegt ist, können Benutzer das Agenda-Widget auf dem Startbildschirm des Geräts platzieren.

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
- **Smart Lock und andere Vertrauens-Agents:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Smart Lock oder andere Vertrauens-Agents Sperrbildschirmeinstellungen auf kompatiblen Geräten anpassen können. Dieses Feature wird auch als Vertrauens-Agent bezeichnet und ermöglicht es Ihnen, das Kennwort für den Gerätesperrbildschirm zu deaktivieren oder zu umgehen, wenn sich das Gerät an einem vertrauenswürdigen Standort befindet. Umgehen Sie z. B. das Kennwort für das Arbeitsprofil, wenn das Gerät mit einem bestimmten Bluetooth-Gerät verbunden ist oder sich in der Nähe eines NFC-Tags befindet. Mit dieser Einstellung können Sie verhindern, dass Benutzer Smart Lock konfigurieren.

### <a name="device-password"></a>Gerätekennwort

Diese Kennworteinstellungen gelten für persönliche Profile auf Geräten, die ein Arbeitsprofil verwenden.

- **Minimale Kennwortlänge:** Geben Sie eine Mindestanzahl von **4**-**14** Zeichen ein, die das Benutzerkennwort enthalten muss.
- **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung:** Wählen Sie den Zeitraum aus, nach dem ein inaktives Gerät automatisch gesperrt wird.
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
- **Entsperrung durch Fingerabdruck:** Wählen Sie **Blockieren** aus, um zu verhindern, dass ein Endbenutzer das Gerät mithilfe des Fingerabdruckscanners entsperren kann. **Nicht konfiguriert** ermöglicht dem Benutzer das Entsperren des Geräts mittels Fingerabdruck.
- **Smart Lock und andere Vertrauens-Agents:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Smart Lock oder andere Vertrauens-Agents Sperrbildschirmeinstellungen auf kompatiblen Geräten anpassen können. Dieses Feature wird auch als Vertrauens-Agent bezeichnet und ermöglicht es Ihnen, das Kennwort für den Gerätesperrbildschirm zu deaktivieren oder zu umgehen, wenn sich das Gerät an einem vertrauenswürdigen Standort befindet. Umgehen Sie z. B. das Kennwort für das Arbeitsprofil, wenn das Gerät mit einem bestimmten Bluetooth-Gerät verbunden ist oder sich in der Nähe eines NFC-Tags befindet. Mit dieser Einstellung können Sie verhindern, dass Benutzer Smart Lock konfigurieren.

### <a name="system-security"></a>Systemsicherheit

- **Bedrohungsüberprüfung für Apps:** Die Option **Anfordern** erzwingt, dass die Einstellung **Apps überprüfen** für Arbeitsprofile und persönliche Profile aktiviert ist.

   > [!Note]
   > Diese Einstellung funktioniert nur auf Geräten mit Android 8 (Oreo) und höher.

- **App-Installationen aus unbekannten Quellen im persönlichen Profil verhindern:** Entwurfsbedingt können auf Android Enterprise-Geräten mit Arbeitsprofil keine Apps aus Quellen außerhalb des Play Store installiert werden. Geräte mit Arbeitsprofil sind auf zwei Profile ausgelegt:

  - Ein MDM-verwaltetes Arbeitsprofil
  - Ein privates, von der MDM-Verwaltung unabhängiges Profil

  Diese Einstellung ermöglicht Administratoren eine bessere Kontrolle über App-Installationen aus unbekannten Quellen. **Nicht konfiguriert** (Standardwert) ermöglicht im persönlichen Profil App-Installationen aus unbekannten Quellen. **Blockieren** verhindert App-Installationen im privaten Profil aus anderen Quellen als dem Play Store.

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
  > - Der von Ihnen ausgewählte VPN-Client muss auf dem Gerät installiert sein und VPN pro Anwendung in Arbeitsprofilen unterstützen. Andernfalls tritt ein Fehler auf. 
  > - Sie müssen die VPN-Client-App im **verwalteten Google Play Store** genehmigen, die App mit Intune synchronisieren und die App auf dem Gerät bereitstellen. Danach wird die App im Arbeitsprofil des Benutzers installiert.
  > - Es gibt eventuell bekannte Probleme bei der Verwendung von VPN pro App mit F5 Access for Android 3.0.4. Weitere Informationen finden Sie unter [F5's release notes for F5 Access for Android 3.0.4 (Versionshinweise zu F5 Access for Android 3.0.4)](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android).

- **Sperrmodus:** Wählen Sie **Aktivieren** aus, um den gesamten Netzwerkdatenverkehr zu zwingen, den VPN-Tunnel zu verwenden. Wenn keine Verbindung zum VPN hergestellt wird, hat das Gerät keinen Netzwerkzugriff.

  Wählen Sie **Nicht konfiguriert** aus, damit der Datenverkehr durch den VPN-Tunnel oder durch das Mobilfunknetz fließen kann.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Außerdem können Sie Kioskprofile auf dedizierten Geräten für [Android](device-restrictions-android.md#kiosk)- und [Windows 10](kiosk-settings.md)-Geräte erstellen.

## <a name="see-also"></a>Weitere Informationen:

[Konfigurieren und Problembehandlung von Android Enterprise-Geräten in Microsoft Intune](https://support.microsoft.com/help/4476974)
