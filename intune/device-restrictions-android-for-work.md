---
title: Android Enterprise-Geräteeinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Auf Geräten mit Android Enterprise oder Android for Work können Sie auf dem Gerät Einstellungen einschränken, darunter Kopieren und Einfügen, Benachrichtigungen anzeigen, App-Berechtigungen, Datenfreigabe, Kennwortlänge, Anmeldefehler, Entsperren per Fingerabdruck, Wiederverwenden von Kennwörtern und Aktivieren der Freigabe von Geschäftskontakten per Bluetooth. Konfigurieren Sie Geräte als dedizierten Gerätekiosk zur Ausführung einer oder mehrerer Apps.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53a9c3e8b80f611bc9e293ba7e07c1aece0cfc58
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71163037"
---
# <a name="android-enterprise-device-settings-to-allow-or-restrict-features-using-intune"></a>Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie auf Android Enterprise-Geräten steuern können. Verwenden Sie als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) diese Einstellungen, um Funktionen zuzulassen oder zu deaktivieren, Apps auf dedizierten Geräten auszuführen, die Sicherheit zu steuern usw.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](device-restrictions-configure.md)

## <a name="device-owner-only"></a>Nur Gerätebesitzer

### <a name="general-settings"></a>Allgemeine Einstellungen

- **Bildschirmaufnahme**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Screenshots oder Bildschirmaufnahmen auf dem Gerät vorgenommen werden. Zudem wird verhindert, dass der Inhalt auf Anzeigegeräten angezeigt wird, die über keine sichere Videoausgabe verfügen. **Nicht konfiguriert** erlaubt dem Benutzer, den Bildschirminhalt als Bild zu erfassen.
- **Kamera**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Kamera des Geräts zu verhindern. **Nicht erforderlich** ermöglicht den Zugriff auf die Kamera des Geräts.
- **Standardberechtigungsrichtlinie:** Diese Einstellung definiert die Standardberechtigungsrichtlinie für Anforderungen für Laufzeitberechtigungen. Folgende Werte sind zulässig:
  - **Gerätestandard:** Die Standardeinstellung des Geräts wird verwendet.
  - **Eingabeaufforderung:** Der Benutzer wird dazu aufgefordert, die Berechtigung zu genehmigen.
  - **Automatisch zulassen:** Berechtigungen werden automatisch gewährt.
  - **Automatisch ablehnen:** Berechtigungen werden automatisch verweigert.
- **Datums- und Uhrzeitänderungen**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer manuell Datum und Uhrzeit einstellen. **Nicht konfiguriert** ermöglicht Benutzern, Datum und Uhrzeit auf dem Gerät einzustellen.
- **Änderung der Lautstärke:** Wenn Sie **Blockieren** festlegen, können Benutzer die Lautstärke des Geräts nicht ändern. **Nicht konfiguriert** ermöglicht die Verwendung der Lautstärkeeinstellungen am Gerät.
- **Auf Werkseinstellungen zurücksetzen**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer die Option zum Zurücksetzen auf Werkseinstellungen in den Einstellungen des Geräts verwenden. **Nicht konfiguriert** ermöglicht Benutzern, diese Einstellung auf dem Gerät zu verwenden.
- **Abgesicherter Start:** Wenn Sie **Blockieren** festlegen, können Benutzer das Gerät nicht im abgesicherten Modus neustarten. **Nicht konfiguriert** ermöglicht Benutzern, das Gerät im abgesicherten Modus neu zu starten.
- **Statusleiste**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Statusleiste einschließlich Benachrichtigungen und Schnelleinstellungen zu verhindern. **Nicht konfiguriert** ermöglicht Benutzern den Zugriff auf die Statusleiste.
- **Roamingdatendienste**: Wählen Sie **Blockieren** aus, um Datenroaming über das Mobilfunknetz zu verhindern. **Nicht konfiguriert** erlaubt das Datenroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.
- **Änderung der WLAN-Einstellungen**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer vom Gerätebesitzer erstellte WLAN-Einstellungen ändern. Benutzer können eigene WLAN-Konfigurationen erstellen. **Nicht konfiguriert** ermöglicht Benutzern, die WLAN-Einstellungen auf dem Gerät ändern.
- **Konfiguration des WLAN-Zugriffspunkts**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer WLAN-Konfigurationen erstellen oder ändern. **Nicht konfiguriert** ermöglicht Benutzern, die WLAN-Einstellungen auf dem Gerät ändern.
- **Bluetooth-Konfiguration**: Wählen Sie **Blockieren** aus, um Benutzer daran zu hindern, Bluetooth auf dem Gerät zu konfigurieren. **Nicht konfiguriert** ermöglicht die Verwendung von Bluetooth auf dem Gerät.
- **Tethering und Zugriff auf Hotspots**: Wählen Sie **Blockieren** aus, um Tethering und Zugriff auf portable Hotspots zu verhindern. **Nicht konfiguriert** ermöglicht Tethering und Zugriff auf portable Hotspots.
- **USB-Speicher**: Wählen Sie **Zulassen** zum Zugriff auf USB-Speicher auf dem Gerät. **Nicht konfiguriert** verhindert den Zugriff auf USB-Speicher.
- **USB-Dateiübertragung**: Wählen Sie **Blockieren** aus, um das Übertragen von Dateien per USB zu verhindern. **Nicht konfiguriert** ermöglicht das Übertragen von Dateien.
- **Externe Medien**: Wählen Sie **Blockieren** aus, um die Verwendung beliebiger externen Medien oder das Herstellen der Verbindung mit solchen auf dem Gerät zu verhindern. **Nicht konfiguriert** lässt externe Medien auf dem Gerät zu.
- **Daten mithilfe von NFC übertragen**: Wählen Sie **Blockieren** aus, um die Verwendung der Near Field Communication-Technologie (NFC) zum Übertragen von Dateien aus Apps zu verhindern. **Nicht konfiguriert** ermöglicht die Verwendung von NFC zum Freigeben von Daten zwischen Geräten.
- **Debugfunktionen**: Wenn Sie **Zulassen** festlegen, können Benutzer Features zum Debuggen auf dem Gerät verwenden. **Nicht konfiguriert** verhindert, dass Benutzer Features zum Debuggen auf dem Gerät verwenden.
- **Mikrofonanpassung:** Wenn Sie **Blockieren** festlegen, können Benutzer weder das Mikrofon stummschalten noch die Lautstärke am Mikrofon anpassen. **Nicht konfiguriert** ermöglicht dem Benutzer, die Lautstärke am Mikrofon des Geräts anzupassen.
- **E-Mail-Adressen für Schutz vor Zurücksetzung auf Werkseinstellungen**: Wählen Sie **E-Mail-Adressen für Google-Konto** aus. Geben Sie die E-Mail-Adressen der Geräteadministratoren ein, die das Gerät entsperren können, nachdem es zurückgesetzt wurde. Achten Sie darauf, dass Sie die E-Mail-Adressen durch ein Semikolon trennen, z. B. `admin1@gmail.com;admin2@gmail.com`. Wenn keine E-Mail-Adresse eingegeben wird, kann jeder das Gerät entsperren, sobald die Werkseinstellungen wiederhergestellt sind. Diese e-Mail-Adressen gelten nur, wenn eine Nichtbenutzer-zurück setzung auf die Werkseinstellungen ausgeführt wird, z. b. das Zurücksetzen auf die Werkseinstellungen
- **Notausstieg für Netzwerk**: **Aktivieren** dieser Option erlaubt Benutzern, das Feature „Notausstieg für Netzwerk“ zu aktivieren. Wenn beim Starten des Geräts keine Netzwerkverbindung hergestellt wird, fordert die Notausstiegsfunktion zum Herstellen einer vorübergehenden Verbindung mit einem Netzwerk und Aktualisieren der Geräterichtlinie auf. Nach dem Anwenden der Richtlinie wird das temporäre Netzwerk ignoriert, und das Gerät setzt den Start fort. Dieses Feature verbindet Geräte mit einem Netzwerk, wenn:
  - Kein geeignetes Netzwerk in der letzten Richtlinie enthalten ist.
  - Das Gerät im Aufgabensperrmodus in eine App startet.
  - Der Benutzer die Einstellungen für das Gerät nicht erreichen kann.

  **Nicht konfiguriert** verhindert, dass Benutzer die Netzwerk-Notausstiegsfunktion auf dem Gerät aktivieren.

- **Systemupdate**: Hier können Sie eine Option auswählen, um zu definieren, wie das Geräte Over-the-Air-Updates verarbeitet:
  - **Gerätestandard:** Die Standardeinstellung des Geräts wird verwendet.
  - **Automatisch:** Updates werden ohne Interaktion des Benutzers automatisch installiert. Durch das Festlegen dieser Richtlinie werden sofort alle ausstehenden Updates installiert.
  - **Zurückgestellt:** Updates werden für 30 Tage zurückgestellt. Nach Ablauf der 30 Tage fordert Android den Benutzer zur Installation des Updates auf. Gerätehersteller oder Mobilfunkanbieter können verhindern (ausschließen), dass wichtige Sicherheitsupdates zurückgestellt werden. Bei einem ausgeschlossenen Update wird dem Benutzer eine Systembenachrichtigung auf dem Gerät angezeigt. 
  - **Wartungsfenster:** Updates werden automatisch in einem täglichen Wartungsfenster installiert, das Sie in Intune festlegen. Die Installation wird 30 Tage lang täglich versucht, und es kann aufgrund von zu geringem Speicherplatz oder Akkustand ein Fehler auftreten. Nach 30 Tagen wird der Benutzer von Android zum Installieren aufgefordert. Dieses Fenster wird auch verwendet, um Updates für Google Play-Apps zu installieren. Verwenden Sie diese Option für dedizierte Geräte wie etwa Kioskgeräte, da Apps, die im Vordergrund auf einem dedizierten Gerät im Einzelanwendungsmodus ausgeführt werden, aktualisiert werden können.

- **Benachrichtigungsfenster**: Bei Festlegung auf **Deaktivieren** werden Fensterbenachrichtigungen, wie Popups, eingehende Anrufe, ausgehende Anrufe, Systemwarnungen und Systemfehler, nicht auf dem Gerät angezeigt. Bei **Nicht konfiguriert** wird die Standardeinstellung des Betriebssystems verwendet, wodurch Benachrichtigungen möglicherweise angezeigt werden.
- **Hinweise zur ersten Verwendung überspringen**: Wählen Sie **Aktivieren** aus, um Vorschläge aus Apps auszublenden oder zu überspringen, Tutorials schrittweise durchzuarbeiten oder beim Starten der App einführende Hinweise zu lesen. Bei **Nicht konfiguriert** wird die Standardeinstellung des Betriebssystems verwendet, wodurch diese Vorschläge beim Starten der App möglicherweise angezeigt werden.

### <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit

- **Bedrohungsüberprüfung für Apps**: Die Standardeinstellung **Anfordern** aktiviert Google Play Protect so, dass Apps vor und nach der Installation überprüft werden. Wenn das Tool eine Bedrohung erkennt, kann es den Benutzer warnen, damit er die App vom Gerät entfernt. Bei Wahl von **Nicht konfiguriert** wird Google Play Protect nicht zum Überprüfen von Apps aktiviert oder ausgeführt.

### <a name="dedicated-device-settings"></a>Einstellungen dedizierter Geräte

Verwenden Sie diese Einstellungen, um eine Umgebung im Kioskstil auf Ihren dedizierten Geräten zu konfigurieren. Sie können ein Gerät so konfigurieren, dass eine App oder mehrerer Apps ausgeführt werden. Im Kioskmodus eines Geräts stehen nur die Apps zur Verfügung, die Sie hinzufügen. Diese Einstellungen gelten für dedizierte Android Enterprise-Geräte. Sie gelten nicht für vollständig verwaltete Android Enterprise-Geräte.

**Kioskmodus**: Wählen Sie aus, ob auf dem Gerät eine App oder mehrere Apps ausgeführt werden.

- **Einzelanwendungsmodus**: Benutzer können auf dem Gerät nur auf eine einzelne App zugreifen. Wenn das Gerät gestartet wird, wird nur die jeweilige App gestartet. Benutzer können keine neuen Apps öffnen oder die ausgeführte App ändern.

  - **Verwaltete App auswählen**: Wählen Sie dann die verwaltete Google Play-App aus der Liste aus.

    Wenn keine Apps aufgelistet werden, können Sie dem Gerät [einige Android-Apps hinzufügen](apps-add-android-for-work.md). Achten Sie darauf, [die App der Gerätegruppe zuzuweisen, die für Ihre dedizierten Geräte erstellt wurde](apps-deploy.md).

  > [!IMPORTANT]
  > Wenn Sie den Kiosk Modus für Einzelanwendungen verwenden, funktionieren Dialer/Phone-Apps möglicherweise nicht ordnungsgemäß. 
  
- **Modus für mehrere Apps**: Benutzer können auf dem Gerät nur auf eine begrenzte Anzahl von Apps zugreifen. Wenn das Gerät gestartet wird, werden nur die von Ihnen hinzugefügten Apps gestartet. Sie können auch einige Weblinks hinzufügen, die Benutzer öffnen können. Wenn die Richtlinie angewendet wird, können Benutzer die Symbole für die zulässigen Apps auf dem Startbildschirm sehen.

  > [!IMPORTANT]
  > Für dedizierte Geräte mit mehreren Apps **muss** die [Managed Home Screen-App](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) aus Google Play:
  >   - in Intune [als Client-App hinzugefügt](apps-add-android-for-work.md) sein
  >   - [der Gerätegruppe zugewiesen sein](apps-deploy.md), die für Ihre dedizierten Geräte erstellt wurde.
  > 
  > Die **Managed Home Screen**-App muss sich nicht im Konfigurationsprofil befinden, aber als Client-App hinzugefügt werden. Wenn die **Managed Home Screen**-App als Client-App hinzugefügt wird, werden alle anderen Apps, die Sie im Konfigurationsprofil hinzufügen, in der **Managed Home Screen**-App als Symbole angezeigt. 
  >
  > Wenn Sie den Kiosk Modus für mehrere Apps verwenden, funktionieren Dialer/Phone-Apps möglicherweise nicht ordnungsgemäß. 

  - **Hinzufügen**: Wählen Sie Ihre apps aus der Liste aus.

    Wenn die **Managed Home Screen**-App nicht aufgeführt wird, [fügen Sie sie aus Google Play hinzu](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise). Achten Sie darauf, [die App der Gerätegruppe zuzuweisen](apps-deploy.md), die für Ihre dedizierten Geräte erstellt wurde.

    Sie können auch andere [Android-Apps](apps-add-android-for-work.md) und [Web-Apps](web-app.md) hinzufügen, die von Ihrer Organisation für das Gerät erstellt wurden. Achten Sie darauf, [die App der Gerätegruppe zuzuweisen, die für Ihre dedizierten Geräte erstellt wurde](apps-deploy.md).

  - **Virtuelle Start Schaltfläche**: eine weiche Taste, die Benutzer an den verwalteten Startbildschirm zurückgibt, damit Benutzer zwischen apps wechseln können. Folgende Optionen sind verfügbar:

    - **Nicht konfiguriert** (Standard): eine Start Schaltfläche wird nicht angezeigt. Benutzer müssen die Schaltfläche "zurück" verwenden, um zwischen apps zu wechseln.
    - **Schwenken**: eine Start Schaltfläche wird angezeigt, wenn ein Benutzer auf dem Gerät aufrichtet.
    - **Floating**: zeigt eine permanente, unverankerte Start Schaltfläche auf dem Gerät an.

  - **Kioskmodus verlassen**: Wählen Sie **Aktivieren** aus, um Administratoren zu ermöglichen, den Kioskmodus vorübergehend zu beenden, um das Gerät zu aktualisieren. Um dieses Feature verwenden zu können, führt der Administrator Folgendes aus:
  
    1. Weiteres Betätigen der Schaltfläche „Zurück“, bis die Schaltfläche **Kiosk beenden** angezeigt wird. 
    2. Auswählen der Schaltfläche **Kiosk beenden** und Eingabe der PIN für den **Code zum Verlassen des Kioskmodus**.
    3. Wenn Sie fertig sind, wählen Sie die **verwaltete Startbildschirm** -App aus. Mit diesem Schritt wird das Gerät erneut im Multi-App-Kioskmodus gesperrt.

      Wenn die Einstellung **nicht konfiguriert**ist, können Administratoren den Kiosk Modus nicht anhalten. Wenn der Administrator weiterhin die Schaltfläche „Zurück“ betätigt und die Schaltfläche **Kiosk beenden** auswählt, wird eine Meldung angezeigt, dass eine Kennung erforderlich ist.

    - **Code zum Verlassen des Kioskmodus**: Geben Sie eine aus 4 bis 6 Ziffern bestehende numerische PIN ein. Der Administrator verwendet diese PIN zum vorübergehenden Anhalten des Kioskmodus.

  - **Benutzerdefinierten URL-Hintergrund festlegen**: Geben Sie eine URL zum Anpassen des Hintergrundbildschirms auf dem dedizierten Gerät ein.

    > [!NOTE]
    > In den meisten Fällen empfehlen wir, mit Bildern mit mindestens den folgenden Größen zu beginnen:
    >
    > - Smartphone: 1080 x 1920 Pixel
    > - Tablet: 1920 × 1080 Pixel
    >
    > Für ein optimales Erlebnis und scharfe Details wird empfohlen, Bildobjekte gerätebezogen gemäß den Displayspezifikationen zu erstellen.
    >
    > Moderne Displays haben höhere Pixeldichten und können entsprechende Bilder mit 2K-/4K-Auflösung anzeigen.

  - **Wi-Fi-Konfiguration**: **aktivieren** zeigt das WLAN-Steuerelement auf dem verwalteten Startbildschirm an und ermöglicht Endbenutzern das Herstellen einer Verbindung zwischen dem Gerät und verschiedenen WLAN-Netzwerken. Durch Aktivieren dieses Features wird auch der Gerätestandort aktiviert. **Nicht konfiguriert** (Standard) zeigt das WLAN-Steuerelement nicht auf dem verwalteten Startbildschirm an. Es verhindert, dass Benutzer Verbindungen mit WLAN-Netzwerken herstellen, während Sie den verwalteten Startbildschirm verwenden.

  - **Bluetooth-Konfiguration**: **aktivieren** zeigt das Bluetooth-Steuerelement auf dem verwalteten Startbildschirm an und ermöglicht Endbenutzern das Koppeln von Geräten über Bluetooth. Durch Aktivieren dieses Features wird auch der Gerätestandort aktiviert. **Nicht konfiguriert** (Standard) zeigt das Bluetooth-Steuerelement nicht auf dem verwalteten Startbildschirm an. Sie hindert Benutzer daran, Bluetooth zu konfigurieren und Geräte zu koppeln, während Sie den verwalteten Startbildschirm verwenden.

  - **Taschen Taschen Zugriff**: **aktivieren** zeigt das Taschen Taschen Steuerelement auf dem verwalteten Startbildschirm an und ermöglicht es Endbenutzern, die Taschenlampe ein-oder auszuschalten. **Nicht konfiguriert** (Standard) zeigt das Taschen Taschen Steuerelement nicht auf dem verwalteten Startbildschirm an. Er verhindert, dass Benutzer die Taschenlampe verwenden, während Sie den verwalteten Startbildschirm verwenden.

  - **Medien Volume-Steuerung**: **aktivieren** zeigt die Medien Volume-Steuerung auf dem verwalteten Startbildschirm an und ermöglicht Endbenutzern das Anpassen des Medien Volumens des Geräts mithilfe eines Schiebereglers. **Nicht konfiguriert** (Standard) zeigt das Medien Volume-Steuerelement auf dem verwalteten Startbildschirm nicht an. Sie hindert Benutzer daran, das Medien Volume des Geräts zu verwenden, wenn Sie den verwalteten Startbildschirm verwenden, sofern die Hardware Schaltflächen Sie nicht unterstützen. 

  - **Bildschirmschoner Modus**: **aktivieren** zeigt einen Bildschirmschoner auf dem verwalteten Startbildschirm an, wenn das Gerät gesperrt ist oder ein Timeout auftritt. **Nicht konfiguriert** (Standard) zeigt keinen Bildschirmschoner auf dem verwalteten Startbildschirm an.

    Wenn diese Option aktiviert ist, konfigurieren Sie auch:

    - **Benutzerdefiniertes Bildschirmschoner festlegen**: Geben Sie die URL zu einem benutzerdefinierten Image ein. Geben Sie beispielsweise Folgendes ein:

      - `http://www.contoso.com/image.jpg`
      - `www.contoso.com/image.bmp`
      - `https://www.contoso.com/image.html`

      Wenn Sie keine URL eingeben, wird das Standard Image des Geräts verwendet, wenn ein Standard Image vorhanden ist.

    - **Anzahl von Sekunden, die das Gerät vor dem Ausschalten des Bildschirms anzeigt**: Wählen Sie aus, wie lange das Gerät den Bildschirmschoner anzeigt. Geben Sie einen Wert zwischen 0-9999999 Sekunden ein. Der Standardwert beträgt `0` Sekunden. Wenn das Feld leer gelassen oder auf 0 (`0`null) festgelegt ist, wird der Bildschirmschoner aktiv, bis ein Benutzer mit dem Gerät interagiert.
    - **Anzahl der Sekunden, die das Gerät inaktiv ist, bevor der Bildschirmschoner angezeigt wird**: Wählen Sie aus, wie lange das Gerät im Leerlauf ist, bevor der Bildschirm Geben Sie einen Wert zwischen 1-9999999 Sekunden ein. Der Standardwert beträgt `30` Sekunden. Geben Sie eine Zahl ein, die größer als null (`0`) ist.
    - **Medien vor dem Starten des Bildschirmschoners erkennen**: durch **aktivieren** (Standard) wird der Bildschirmschoner nicht angezeigt, wenn auf dem Gerät Audiodaten oder Videos abgespielt werden. **Nicht konfiguriert** zeigt den Bildschirmschoner an, selbst wenn Audiodaten oder Videos abgespielt werden.

### <a name="device-password-settings"></a>Gerätekennworteinstellungen

- **Sperrbildschirm deaktivieren:** Wenn Sie **Deaktivieren** festlegen, können Benutzer das Bildschirmsperrfeature Keyguard nicht auf dem Gerät verwenden. **Nicht konfiguriert** ermöglicht dem Benutzer, die Keyguard-Features zu verwenden.
- **Deaktivierte Sperrbildschirmfeatures**: Wenn Keyguard auf dem Gerät aktiviert ist, wählen Sie die Features aus, die Sie deaktivieren möchten. Ist beispielsweise **Kamera absichern** ausgewählt, ist die Kamerafunktion auf dem Gerät deaktiviert. Alle nicht ausgewählten Features sind auf dem Gerät aktiviert.

  Diese Features sind für Benutzer verfügbar, wenn das Gerät gesperrt ist. Benutzer können mit einem Häkchen versehene Features weder anzeigen noch darauf zugreifen.

- **Erforderlicher Kennworttyp:** Hiermit wird der Typ des erforderlichen Kennworts für das Gerät definiert. Folgende Optionen sind verfügbar:
  - **Gerätestandard**
  - **Kennwort erforderlich, keine Einschränkungen**
  - **Schwach biometrisch**: [Vergleich von stark und schwach biometrisch](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (öffnet Android-Website)
  - **Numerisch**: Kennwort darf nur aus Zahlen bestehen. Beispiel: `123456789`. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
  - **Numerisch komplex**: Sich wiederholende oder fortlaufende Ziffern wie „1111“ oder „1234“ sind nicht zulässig. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
  - **Alphabetisch**: Buchstaben des Alphabets sind erforderlich. Zahlen und Symbole sind nicht erforderlich. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
  - **Alphanumerisch**: Schließt Großbuchstaben, Kleinbuchstaben und Ziffern ein. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
  - **Alphanumerisch mit Symbolen**: Schließt Großbuchstaben, Kleinbuchstaben, Ziffern, Interpunktionszeichen und Symbole ein. Geben Sie außerdem Folgendes ein:

    - **Minimale Kennwortlänge**: Geben Sie die Mindestlänge des Kennworts ein (4 bis 16 Zeichen).
    - **Erforderliche Anzahl von Zeichen**: Geben Sie die erforderliche Anzahl von Zeichen des Kennworts ein (0 bis 16 Zeichen).
    - **Erforderliche Anzahl von Kleinbuchstaben**: Geben Sie die erforderliche Anzahl von Kleinbuchstaben des Kennworts ein (0 bis 16 Zeichen).
    - **Erforderliche Anzahl von Großbuchstaben**: Geben Sie die erforderliche Anzahl von Großbuchstaben des Kennworts ein (0 bis 16 Zeichen).
    - **Erforderliche Anzahl anderer Zeichen als Buchstaben**: Geben Sie die erforderliche Anzahl anderer Zeichen als Buchstaben (alles außer Buchstaben im Alphabet) des Kennworts ein (0 bis 16 Zeichen).
    - **Erforderliche Anzahl numerischer Zeichen**: Geben Sie die erforderliche Anzahl numerischer Zeichen (`1`, `2`, `3` usw.) des Kennworts ein (0 bis 16 Zeichen).
    - **Erforderliche Anzahl von Symbolen**: Geben Sie die erforderliche Anzahl von Symbolen (`&`, `#`, `%` usw.) des Kennworts ein (0 bis 16 Zeichen).

- **Anzahl von Tagen bis zum Kennwortablauf**: Geben Sie die Anzahl der Tage (1-365) an, nach denen das Gerätekennwort geändert werden muss. Geben Sie beispielsweise zum Ändern des Kennworts nach 60 Tagen `60` ein. Wenn das Kennwort abläuft, werden Benutzer aufgefordert, ein neues Kennwort zu erstellen.
- **Anzahl erforderlicher Kennwörter, bevor ein Benutzer ein Kennwort wiederverwenden kann**: Geben Sie die Anzahl der letzten Kennwörter ein, die nicht wiederverwendet werden können (1-24). Verwenden Sie diese Einstellung, um zu verhindern, dass der Benutzer zuvor verwendete Kennwörter erstellt.
- **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird**: Geben Sie die Anzahl zulässiger Anmeldefehler (4 bis 11) ein, bevor das Gerät zurückgesetzt wird.

### <a name="power-settings"></a>Energieeinstellungen

- **Zeit bis Bildschirmsperre:** Hiermit wird die Leerlaufzeit festgelegt, nach der das Gerät gesperrt wird.
- **Bildschirm aktiviert, wenn Gerät angeschlossen ist:** Hiermit kann ausgewählt werden, bei welchen Stromquellen der Bildschirm des Geräts aktiviert bleibt, wenn es angeschlossen ist.

### <a name="users-and-accounts-settings"></a>Einstellungen für Benutzer und Konten

- **Neue Benutzer hinzufügen:** Wenn Sie **Blockieren** festlegen, können Benutzer keine neuen Benutzer hinzufügen. Jeder Benutzer hat einen persönlichen Bereich auf dem Gerät für benutzerdefinierte Startseiten, Konten, Apps und Einstellungen. **Nicht konfiguriert** ermöglicht Benutzern, dem Gerät andere Benutzer hinzuzufügen.
- **Entfernen von Benutzern:** Wenn Sie **Blockieren** festlegen, können Benutzer keine Benutzer entfernen. **Nicht konfiguriert** ermöglicht Benutzern, andere Benutzer vom Gerät zu entfernen.
- **Kontoänderungen:** Wenn Sie **Blockieren** festlegen, können Benutzer Konten nicht bearbeiten. **Nicht konfiguriert** ermöglicht Benutzern, Benutzerkonten auf dem Gerät zu aktualisieren.

  > [!NOTE]
  > Diese Einstellung wird auf Geräten mit Geräte Besitzern (vollständig verwaltet) nicht berücksichtigt. Wenn Sie diese Einstellung konfigurieren, wird die Einstellung ignoriert und hat keine Auswirkungen.

### <a name="applications"></a>Applications

- **Installation über unbekannte Quellen zulassen**: Wenn Sie **Zulassen** festlegen, können Benutzer **Unbekannte Quellen** aktivieren. Diese Einstellung ermöglicht die Installation von Apps aus unbekannten Quellen, einschließlich anderer Quellen als Google Play Store. **Nicht konfiguriert** verhindert, dass Benutzer **Unbekannte Quellen** nutzen.
- **Zugriff auf alle Apps im Google Play Store zulassen**: Bei Festlegung auf **Zulassen** erhalten Benutzer Zugriff auf alle Apps im Google Play Store. Sie erhalten keinen Zugriff auf die Apps, die der Administrator in [Client-Apps](apps-add-android-for-work.md) sperrt. **Nicht konfiguriert** zwingt Benutzer, nur auf die Apps zuzugreifen, die der Administrator im Google Play Store zur Verfügung stellt, oder auf die Apps, die in [Client-Apps](apps-add-android-for-work.md) erforderlich sind.
- **Automatische App-Updates**: Wählen Sie diese Option aus, wenn automatische Updates installiert werden. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert**
  - **Benutzerauswahl**
  - **Nie**
  - **Nur WLAN**
  - **Immer**

### <a name="connectivity"></a>Verbindung

- **Always On-VPN**: Wählen Sie **Aktivieren** aus, um einen VPN-Client so festzulegen, dass er automatisch eine Verbindung mit dem VPN herstellt und erneut herstellt. Always On-VPN-Verbindungen bleiben erhalten oder werden sofort hergestellt, wenn der Benutzer sein Gerät sperrt, das Gerät neu gestartet wird oder das drahtlose Netzwerk sich ändert. 

  Wählen Sie **Nicht konfiguriert** aus, um das Always On-VPN für alle VPN-Clients zu deaktivieren.

  > [!IMPORTANT]
  > Stellen Sie sicher, dass Sie nur eine Always On-VPN-Richtlinie auf einem einzelnen Gerät bereitstellen. Die Bereitstellung mehrerer Always VPN-Richtlinien auf einem einzelnen Gerät wird nicht unterstützt.

- **VPN-Client**: Wählen Sie einen VPN-Client aus, der Always On unterstützt. Folgende Optionen sind verfügbar:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Benutzerdefiniert
    - **Paket-ID**: Geben Sie die Paket-ID der App im Google Play Store ein. Wenn z. B. die URL für die App im Play Store `https://play.google.com/store/details?id=com.contosovpn.android.prod` lautet, dann ist die Paket-ID `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  > - Der von Ihnen ausgewählte VPN-Client muss auf dem Gerät installiert sein und VPN pro Anwendung in Arbeitsprofilen unterstützen. Andernfalls tritt ein Fehler auf. 
  > - Sie müssen die VPN-Client-App im **verwalteten Google Play Store** genehmigen, die App mit Intune synchronisieren und die App auf dem Gerät bereitstellen. Danach wird die App im Arbeitsprofil des Benutzers installiert.
  > - Es gibt eventuell bekannte Probleme bei der Verwendung von VPN pro App mit F5 Access for Android 3.0.4. Weitere Informationen finden Sie unter [F5's release notes for F5 Access for Android 3.0.4 (Versionshinweise zu F5 Access for Android 3.0.4)](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android).

- **Sperrmodus**: Wählen Sie **Aktivieren** aus, um den gesamten Netzwerkdatenverkehr zu zwingen, den VPN-Tunnel zu verwenden. Wenn keine Verbindung zum VPN hergestellt wird, hat das Gerät keinen Netzwerkzugriff.

  Wählen Sie **Nicht konfiguriert** aus, damit der Datenverkehr durch den VPN-Tunnel oder durch das Mobilfunknetz fließen kann.

## <a name="work-profile-only"></a>Nur Arbeitsprofil 

### <a name="work-profile-settings"></a>Arbeitsprofileinstellungen

#### <a name="general"></a>Allgemein

- **Kopieren und Einfügen zwischen Arbeitsprofilen und persönlichen Profilen**: Wählen Sie **Blockieren** aus, um das Kopieren und Einfügen zwischen Arbeits-Apps und persönlichen Apps zu verhindern. **Nicht konfiguriert** ermöglicht Benutzern, Daten mithilfe von Kopieren und Einfügen mit Apps im persönlichen Profil freizugeben. 
- **Datenfreigabe zwischen Arbeitsprofilen und persönlichen Profilen**: Wählen Sie aus, ob Apps im Arbeitsprofil Daten für Apps im persönlichen Profil freigeben können. Sie können z.B. Freigabeaktionen in Anwendungen steuern, wie etwa die Option **Freigeben**. in der Chrome-Browser-App. Diese Einstellung gilt nicht für das Verhalten beim Kopieren/Einfügen der Zwischenablage. Ihre Freigabeoptionen:
  - **Standardeinschränkungen für Freigabe**: Dies ist das standardmäßige Freigabeverhalten des Geräts, das abhängig von der Android-Version variiert. Standardmäßig ist die Freigabe von Daten des persönlichen Profils für das Arbeitsprofil zulässig. Die Freigabe von Daten des Arbeitsprofils für das persönliche Profil ist dagegen standardmäßig blockiert. Durch diese Einstellung wird die Freigabe von Daten des Arbeitsprofils für das persönliche Profil verhindert. Auf Geräten mit den Versionen 6.0 und höher blockiert Google die Freigabe vom persönlichen Profil zum Arbeitsprofil nicht.
  - **Apps im Arbeitsprofil können Freigabeanforderungen vom persönlichen Profil verarbeiten**: Aktiviert das integrierte Android-Feature, dass die Freigabe vom persönlichen Profil zum Arbeitsprofil ermöglicht. Wenn diese Option aktiviert ist, können Daten durch eine Freigabeanfrage einer App im persönlichen Profil für Apps im Arbeitsprofil freigegeben werden. Diese Einstellung ist das Standardverhalten für Android-Geräte, die frühere Versionen als 6.0 ausführen.
  - **Grenzübergreifende Freigabe zulassen**: Ermöglicht die Freigabe von Daten in beide Richtungen über die Begrenzungen des Arbeitsprofils hinaus. Wenn Sie diese Einstellung auswählen, können Apps im Arbeitsprofil Daten für Apps ohne Badgeverwendung im persönlichen Profil freigeben. Diese Einstellung gestattet es verwalteten Apps im Arbeitsprofil, die Daten für Apps auf der nicht verwalteten Seite des Geräts freizugeben. Verwenden Sie diese Einstellung also mit Bedacht.

- **Arbeitsprofilbenachrichtigungen bei Gerätesperre**: Steuert, ob Apps im Arbeitsprofil Daten in Benachrichtigungen anzeigen können, wenn das Gerät gesperrt ist. **Blockieren** verhindert die Datenanzeige. **Nicht konfiguriert** zeigt die Daten an.
- **Standardmäßige App-Berechtigungen**: Legt die Standardberechtigungsrichtlinie für alle Apps im Arbeitsprofil fest. Ab Android 6 wird der Benutzer aufgefordert, bestimmte von den Apps benötigte Berechtigungen zu erteilen, wenn die App gestartet wird. Bei dieser Richtlinieneinstellung können Sie festlegen, ob Benutzer aufgefordert werden sollen, Berechtigungen für alle Apps im Arbeitsprofil zu gewähren. Beispielsweise können Sie dem Arbeitsprofil eine App zuweisen, die Standortzugriff benötigt. In der Regel fordert diese App den Benutzer dazu auf, den Standortzugriff durch die App zu genehmigen oder abzulehnen. Verwenden Sie diese Richtlinie, um Berechtigungen automatisch ohne Aufforderung zu erteilen, Berechtigungen ohne Aufforderung automatisch zu verweigern oder den Endbenutzer entscheiden zu lassen. Es stehen die folgenden Optionen zur Auswahl:
  - **Gerätestandard**
  - **Eingabeaufforderung**
  - **Automatisch gewähren**
  - **Automatisch verweigern**

  Sie können auch eine App-Konfigurationsrichtlinie verwenden, um Berechtigungen für einzelne Anwendungen zu erteilen (**Clientanwendungen** > **App-Konfigurationsrichtlinien**).

- **Konten hinzufügen und entfernen**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer Konten im Arbeitsprofil manuell hinzufügen oder daraus entfernen. Wenn Sie beispielsweise die Gmail-App in einem Android-Arbeitsprofil bereitstellen, können Sie verhindern, dass Benutzer Konten in diesem Arbeitsprofil hinzufügen oder entfernen. **Nicht konfiguriert** ermöglicht das Hinzufügen von Konten im Arbeitsprofil.  

- **Kontaktfreigabe über Bluetooth:** Ermöglicht den Zugriff auf Arbeitskontakte von einem anderen Gerät aus, z.B. aus dem Auto, wenn es mit Bluetooth gekoppelt ist. Diese Einstellung ist standardmäßig nicht konfiguriert, und Kontakte aus dem Arbeitsprofil werden nicht angezeigt. Klicken Sie auf **Aktivieren**, um diese Freigabe zuzulassen und um Kontakte aus dem Arbeitsprofil anzuzeigen. Diese Einstellung ist auf Geräten unter Android OS 6.0 und höher verfügbar, auf denen Arbeitsprofile eingerichtet wurden. Wenn Sie diese Einstellung aktivieren, können bestimmte Bluetooth-Geräte bei der ersten Verbindung Arbeitskontakte zwischenspeichern. Durch das Deaktivieren dieser Richtlinie nach einer ersten Kopplung bzw. Synchronisierung werden die Arbeitskontakte von einem Bluetooth-Gerät möglicherweise nicht entfernt.

- **Bildschirmaufnahme**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Screenshots oder Bildschirmaufnahmen auf dem Gerät im Arbeitsprofil vorgenommen werden. Zudem wird verhindert, dass der Inhalt auf Anzeigegeräten angezeigt wird, die über keine sichere Videoausgabe verfügen. **Nicht konfiguriert** ermöglicht das Erstellen von Screenshots.

- **Anrufer-ID des Arbeitskontakts im persönlichen Profil anzeigen**: Wenn aktiviert (**Nicht konfiguriert**), werden die Anruferdetails des Arbeitskontakts im persönlichen Profil angezeigt. Mit **Blockieren** wird die Anrufernummer des Arbeitskontakts im persönlichen Profil nicht angezeigt. Gilt für Android OS v6.0 und neuere Versionen.

- **Arbeitskontakte vom persönlichen Profil aus suchen**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer in Apps im persönlichen Profil Arbeitskontakte suchen. **Nicht erforderlich** ermöglicht das Suchen nach Arbeitskontakten im persönlichen Profil.

- **Kamera**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Kamera des Geräts im Arbeitsprofil zu verhindern. Die Kamera im persönlichen Profil ist von dieser Einstellung nicht betroffen. **Nicht erforderlich** ermöglicht den Zugriff auf die Kamera im Arbeitsprofil.

- **Widgets von Arbeitsprofil-apps zulassen**: **aktivieren** ermöglicht Endbenutzern das Platzieren von Widgets, die von apps auf dem Startbildschirm verfügbar gemacht werden. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird dieses Feature deaktiviert.

  Beispielsweise wird Outlook in den Arbeits Profilen Ihrer Benutzer installiert. Wenn diese Option auf **aktivieren**festgelegt ist, können Benutzer das Agenda-Widget auf dem Startbildschirm des Geräts platzieren.

#### <a name="work-profile-password"></a>Arbeitsprofilkennwort

- **Arbeitsprofilkennwort erforderlich**: Gilt für Android 7.0 und höher mit aktiviertem Arbeitsprofil. Wählen Sie **Anfordern** aus, um eine Kennungsrichtlinie einzugeben, die nur für Apps im Arbeitsprofil gilt. Standardmäßig kann der Endbenutzer die beiden separat definierten PINs verwenden oder diese zu einer PIN kombinieren, die die Stärke der jeweils stärkeren PIN übernimmt. **Nicht konfiguriert** ermöglicht dem Benutzer, Arbeits-Apps ohne Kennworteingabe zu verwenden.
- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl (von **4**-**16**) an Zeichen an, die das Benutzerkennwort enthalten muss.
- **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Sperrung des Arbeitsprofils**: Wählen Sie die Zeitspanne aus, nach der das Arbeitsprofil gesperrt wird. Der Benutzer muss dann seine Anmeldeinformationen eingeben, um wieder Zugriff zu erhalten.
- **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird**: Geben Sie an, wie häufig ein falsches Kennwort eingegeben werden kann, bevor das Arbeitsprofil auf dem Gerät zurückgesetzt wird.
- **Kennwortablauf (Tage)** : Geben Sie die Anzahl der Tage an (von **1**-**255**), nach deren Verstreichen das Kennwort eines Endbenutzers geändert werden muss.
- **Erforderlicher Kennworttyp**: Wählen Sie den Typ des Kennworts, das auf dem Gerät festgelegt werden muss. Es stehen die folgenden Optionen zur Auswahl:
  - **Gerätestandard**
  - **Biometrie auf niedriger Sicherheitsstufe**
  - **Erforderlich**
  - **Mindestens numerisch**
  - **Numerisch komplex**: Sich wiederholende oder fortlaufende Ziffern wie „1111“ oder „1234“ sind nicht zulässig.
  - **Mindestens alphabetisch**
  - **Mindestens alphanumerisch**
  - **Mindestens alphanumerisch mit Symbolen**
- **Wiederverwendung vorheriger Kennwörter verhindern**: Geben Sie die Anzahl neuer Kennwörter ein (von **1**-**24**), die verwendet werden müssen, bevor ein altes Kennwort wiederverwendet werden kann.
- **Entsperrung durch Fingerabdruck**: Wählen Sie **Blockieren** aus, um zu verhindern, dass ein Endbenutzer das Gerät mithilfe des Fingerabdruckscanners entsperren kann. **Nicht konfiguriert** ermöglicht Benutzern das Entsperren von Geräten mit einem Fingerabdruck im Arbeitsprofil.
- **Smart Lock und andere Vertrauens-Agents**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Smart Lock oder andere Vertrauens-Agents Sperrbildschirmeinstellungen auf kompatiblen Geräten anpassen. Dieses Feature wird manchmal auch als Vertrauens-Agent bezeichnet und ermöglicht Ihnen, das Kennwort für den Gerätesperrbildschirm zu deaktivieren oder zu umgehen, wenn sich das Gerät an einem vertrauenswürdigen Standort befindet. Umgehen Sie z. B. das Kennwort für das Arbeitsprofil, wenn das Gerät mit einem bestimmten Bluetooth-Gerät verbunden ist oder sich in der Nähe eines NFC-Tags befindet. Mit dieser Einstellung können Sie verhindern, dass Benutzer Smart Lock konfigurieren.

### <a name="device-password"></a>Gerätekennwort

Diese Kennworteinstellungen gelten für persönliche Profile auf Geräten, die ein Arbeitsprofil verwenden.

- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl (von **4**-**14**) an Zeichen an, die das Benutzerkennwort enthalten muss.
- **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung**: Wählen Sie den Zeitraum, nach dessen Verstreichen ein inaktives Gerät automatisch gesperrt wird.
- **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird**: Geben Sie an, wie häufig ein falsches Kennwort eingegeben werden kann, bevor alle Daten auf dem Gerät gelöscht werden.
- **Kennwortablauf (Tage)** : Geben Sie die Anzahl der Tage an (von **1**-**255**), nach deren Verstreichen das Kennwort eines Endbenutzers geändert werden muss.
- **Erforderlicher Kennworttyp**: Wählen Sie den Typ des Kennworts, das auf dem Gerät festgelegt werden muss. Es stehen die folgenden Optionen zur Auswahl:
  - **Gerätestandard**
  - **Biometrie auf niedriger Sicherheitsstufe**
  - **Erforderlich**
  - **Mindestens numerisch**
  - **Numerisch komplex**: Sich wiederholende oder fortlaufende Ziffern wie „1111“ oder „1234“ sind nicht zulässig.
  - **Mindestens alphabetisch**
  - **Mindestens alphanumerisch**
  - **Mindestens alphanumerisch mit Symbolen**
- **Wiederverwendung vorheriger Kennwörter verhindern**: Geben Sie die Anzahl neuer Kennwörter ein (von **1**-**24**), die verwendet werden müssen, bevor ein altes Kennwort wiederverwendet werden kann.
- **Entsperrung durch Fingerabdruck**: Wählen Sie **Blockieren** aus, um zu verhindern, dass ein Endbenutzer das Gerät mithilfe des Fingerabdruckscanners entsperren kann. **Nicht konfiguriert** ermöglicht dem Benutzer das Entsperren des Geräts mittels Fingerabdruck.
- **Smart Lock und andere Vertrauens-Agents**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Smart Lock oder andere Vertrauens-Agents Sperrbildschirmeinstellungen auf kompatiblen Geräten anpassen. Dieses Feature wird manchmal auch als Vertrauens-Agent bezeichnet und ermöglicht Ihnen, das Kennwort für den Gerätesperrbildschirm zu deaktivieren oder zu umgehen, wenn sich das Gerät an einem vertrauenswürdigen Standort befindet. Umgehen Sie z. B. das Kennwort für das Arbeitsprofil, wenn das Gerät mit einem bestimmten Bluetooth-Gerät verbunden ist oder sich in der Nähe eines NFC-Tags befindet. Mit dieser Einstellung können Sie verhindern, dass Benutzer Smart Lock konfigurieren.

### <a name="system-security"></a>Systemsicherheit

- **Bedrohungsüberprüfung für Apps**: **Anfordern** erzwingt, dass die Einstellung **Apps überprüfen** für Arbeits- und persönliche Profile aktiviert ist.

   > [!Note]
   > Diese Einstellung funktioniert nur auf Geräten mit Android O und höher.

### <a name="connectivity"></a>Verbindung

- **Always On-VPN**: Wählen Sie **Aktivieren** aus, um einen VPN-Client so festzulegen, dass er automatisch eine Verbindung mit dem VPN herstellt und erneut herstellt. Always On-VPN-Verbindungen bleiben erhalten oder werden sofort hergestellt, wenn der Benutzer sein Gerät sperrt, das Gerät neu gestartet wird oder das drahtlose Netzwerk sich ändert. 

  Wählen Sie **Nicht konfiguriert** aus, um das Always On-VPN für alle VPN-Clients zu deaktivieren.

  > [!IMPORTANT]
  > Stellen Sie sicher, dass Sie nur eine Always On-VPN-Richtlinie auf einem einzelnen Gerät bereitstellen. Die Bereitstellung mehrerer Always VPN-Richtlinien auf einem einzelnen Gerät wird nicht unterstützt.

- **VPN-Client**: Wählen Sie einen VPN-Client aus, der Always On unterstützt. Folgende Optionen sind verfügbar:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Benutzerdefiniert
    - **Paket-ID**: Geben Sie die Paket-ID der App im Google Play Store ein. Wenn z. B. die URL für die App im Play Store `https://play.google.com/store/details?id=com.contosovpn.android.prod` lautet, dann ist die Paket-ID `com.contosovpn.android.prod`.

  > [!IMPORTANT]
  > - Der von Ihnen ausgewählte VPN-Client muss auf dem Gerät installiert sein und VPN pro Anwendung in Arbeitsprofilen unterstützen. Andernfalls tritt ein Fehler auf. 
  > - Sie müssen die VPN-Client-App im **verwalteten Google Play Store** genehmigen, die App mit Intune synchronisieren und die App auf dem Gerät bereitstellen. Danach wird die App im Arbeitsprofil des Benutzers installiert.
  > - Es gibt eventuell bekannte Probleme bei der Verwendung von VPN pro App mit F5 Access for Android 3.0.4. Weitere Informationen finden Sie unter [F5's release notes for F5 Access for Android 3.0.4 (Versionshinweise zu F5 Access for Android 3.0.4)](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-4.html#relnotes_known_issues_f5_access_android).

- **Sperrmodus**: Wählen Sie **Aktivieren** aus, um den gesamten Netzwerkdatenverkehr zu zwingen, den VPN-Tunnel zu verwenden. Wenn keine Verbindung zum VPN hergestellt wird, hat das Gerät keinen Netzwerkzugriff.

  Wählen Sie **Nicht konfiguriert** aus, damit der Datenverkehr durch den VPN-Tunnel oder durch das Mobilfunknetz fließen kann.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Außerdem können Sie Kioskprofile auf dedizierten Geräten für [Android](device-restrictions-android.md#kiosk)- und [Windows 10](kiosk-settings.md)-Geräte erstellen.

## <a name="see-also"></a>Siehe auch

[Konfigurieren und Problembehandlung von Android Enterprise-Geräten in Microsoft Intune](https://support.microsoft.com/help/4476974)
