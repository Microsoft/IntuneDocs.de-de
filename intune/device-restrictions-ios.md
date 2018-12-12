---
title: Hinzufügen von Einstellungen für iOS-Geräteeinschränkungen in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Fügen Sie Einstellungen auf iOS-Geräten hinzu, konfigurieren oder erstellen Sie sie, um Anforderungen für Kennwörter festzulegen, den gesperrten Bildschirm zu steuern, integrierte Apps zu verwenden, eingeschränkte oder genehmigte Apps hinzuzufügen, Bluetooth-Geräte zu handhaben, für Sicherung und Speicherung eine Verbindung mit der Cloud herzustellen, den Kioskmodus zu aktivieren, Domänen hinzuzufügen und zu steuern, wie Benutzer mit dem Safari-Webbrowser in Microsoft Intune interagieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a677742c5d2f876c0714f13c4f62d059ced98584
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728972"
---
# <a name="ios-device-restrictions-settings-list-in-microsoft-intune"></a>Liste der Einstellungen für iOS-Geräteeinschränkungen in Microsoft Intune

In diesem Artikel werden alle Einstellungen für Geräteeinschränkungen aufgelistet und beschrieben, die Sie für iOS-Geräte konfigurieren können. Diese Einstellungen werden einem Gerätekonfigurationsprofil hinzugefügt und dann Ihren iOS-Geräten mit Microsoft Intune zugewiesen oder bereitgestellt.

## <a name="general"></a>Allgemein

- **Nutzungsdaten freigeben**: Wählen Sie **Blockieren** aus, um zu verhindern, dass das Gerät Diagnose- und Nutzungsdaten an Apple sendet. **Nicht konfiguriert** lässt das Senden dieser Daten zu.
  - **Übermittlung von Diagnosedaten**: **Blockieren** verhindert, dass der Benutzer Änderungen an den Einstellungen für Diagnoseübermittlung und App-Analyse in **Diagnose- und Nutzung** (Geräteeinstellungen) vornimmt. Um diese Einstellung verwenden, muss sich das Gerät im überwachten Modus befinden (iOS 9.3.2+). **Nicht konfiguriert** ermöglicht dem Benutzer, diese Geräteeinstellungen zu ändern.
- **Bildschirmaufnahme**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Screenshots oder Bildschirmaufnahmen auf dem Gerät vorgenommen werden. **Nicht konfiguriert** erlaubt dem Benutzer, den Bildschirminhalt als Bild zu erfassen.
  - **Remotebildschirmüberwachung über die Classroom-App (nur überwacht):** Wählen Sie **Blockieren** aus, um zu verhindern, dass die Classroom-App den Bildschirm des Geräts remote anzeigt. Um diese Einstellung zu verwenden, muss sich das Gerät im überwachten Modus befinden (iOS 9.3+). **Nicht konfiguriert** ermöglicht der Apple Classroom-App, den Bildschirm anzuzeigen.
  - **Unaufgeforderte Bildschirmbeobachtung durch die Classroom-App (nur überwacht)**: Falls auf **Zulassen** festgelegt, können Lehrer im Hintergrund die Bildschirme der iOS-Geräte ihrer Kursteilnehmer mithilfe der Classroom-App überwachen, ohne dass die Kursteilnehmer dies mitbekommen. In einer Klasse registrierte Kursteilnehmergeräte, die die Classroom-App verwenden, gewähren der Lehrkraft des Kurses automatisch die Berechtigung. **Nicht konfiguriert** verhindert diese Funktion.
- **Nicht vertrauenswürdige TLS-Zertifikate:** Wählen Sie **Blockieren** aus, um zu verhindern, dass nicht vertrauenswürdige TLS-Zertifikate (Transport Layer Security) auf das Gerät gelangen. **Nicht konfiguriert** lässt TLS-Zertifikate zu.
- **Vertrauen für Unternehmens-App**: Wählen Sie **Blockieren** aus, um die Schaltfläche **Unternehmensentwickler vertrauen** aus „Einstellungen > Allgemein > Profile und Geräteverwaltung“ auf dem Gerät zu entfernen. **Nicht konfiguriert** ermöglicht dem Benutzer, zu wählen, ob Apps, die nicht aus dem App Store heruntergeladen wurden, vertraut werden soll.
- **Kontoänderung (nur überwacht)**: Bei Festlegung auf **Blockieren** kann der Benutzer die gerätespezifischen Einstellungen nicht über die iOS-Einstellungen-App aktualisieren. Der Benutzer kann z.B. nicht neue Gerätekonten erstellen oder Benutzernamen bzw. Kennwort ändern. **Nicht konfiguriert** ermöglicht dem Benutzer, diese Einstellungen zu ändern.
  Diese Funktion gilt auch für Einstellungen, auf die über die iOS-Einstellungen-App zugegriffen werden kann, wie z.B. E-Mail, Kontakte, Kalender, Twitter und mehr. Diese Funktion gilt nicht für Apps mit Kontoeinstellungen, die nicht über die iOS-Einstellungen-App konfiguriert werden können, wie z.B. die Microsoft Outlook-App.
- **Aktivieren von Einschränkungen in den Geräteeinstellungen (nur überwacht)**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer Einschränkungen in den Geräteeinstellungen aktivieren. **Nicht konfiguriert** erlaubt dem Benutzer das Konfigurieren von Geräteeinschränkungen (z.B. Jugendschutz) auf dem Gerät.
- **Verwendung der Option zum Löschen aller Inhalte und Einstellungen auf dem Gerät (nur überwacht)**: Wählen Sie **Blockieren** aus, damit Benutzer nicht die Option zum Löschen aller Inhalte und Einstellungen auf dem Gerät (nur überwacht) verwenden können. **Nicht konfiguriert** ermöglicht Benutzern den Zugriff auf diese Einstellungen.
- **Gerätenamensänderung (nur überwacht)**: Wählen Sie **Blockieren** aus, damit der Gerätenamen nicht geändert werden kann. **Nicht konfiguriert** ermöglicht dem Benutzer, den Namen des Geräts zu ändern.
- **Änderung von Benachrichtigungseinstellungen (nur überwacht):** Wählen Sie **Blockieren**, damit die Benachrichtigungseinstellungen nicht geändert werden können. **Nicht konfiguriert** ermöglicht dem Benutzer, die Benachrichtigungseinstellungen des Geräts zu ändern.
- **Änderung des Hintergrundbilds (nur überwacht)**: **Blockieren** verhindert, dass das Hintergrundbild geändert wird. **Nicht konfiguriert** ermöglicht dem Benutzer, das Hintergrundbild des Geräts zu ändern.
- **Änderung der Vertrauenseinstellungen für die Unternehmens-App (nur überwacht)**: **Blockieren** verhindert, dass der Benutzer die Vertrauensstellungseinstellungen für die Unternehmens-App auf überwachten Geräten ändert. **Nicht konfiguriert** ermöglicht dem Benutzer, Apps zu vertrauen, die nicht aus dem App Store heruntergeladen wurden.
- **Konfigurationsprofiländerungen (nur überwacht)**: **Blockieren** verhindert Änderungen des Konfigurationsprofils auf dem Gerät. **Nicht konfiguriert** ermöglicht dem Benutzer, Konfigurationsprofile zu installieren.
- **Aktivierungssperre (nur überwacht)**: Wählen Sie **Zulassen** aus, um die Aktivierungssperre auf überwachten iOS-Geräten zu aktivieren. Die Aktivierungssperre erschwert die erneute Aktivierung verlorener oder gestohlener Geräte.
- **Entfernen von Apps blockieren (nur überwacht)**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer Apps entfernen. **Nicht konfiguriert** ermöglicht Benutzern, Apps vom Gerät zu entfernen.
- **Modus mit USB-Einschränkung blockieren (nur überwacht)**: Wählen Sie **Blockieren** aus, um den Modus mit USB-Einschränkung auf überwachten Geräten zu deaktivieren. Der Modus mit USB-Einschränkung verhindert, dass USB-Zubehör Daten mit einem Gerät austauscht, das für mehr als einer Stunde gesperrt ist. **Nicht konfiguriert** ermöglicht den Modus mit USB-Einschränkung.
- **Automatische Datums- und Uhrzeiteinstellung erzwingen (nur überwacht)**: **Anfordern** erzwingt die automatische Einstellung von Datum und Uhrzeit auf überwachten Geräten. Die Zeitzone für das Gerät wird aktualisiert, wenn das Gerät über Mobilfunkverbindungen verfügt oder WLAN mit Standortdiensten aktiviert ist.
- **Von Kursteilnehmern eine Berechtigung zum Verlassen des Classroom-Kurses verlangen**: **Anfordern** erzwingt, dass in einem nicht verwalteten Kurs registrierte Kursteilnehmer, die die Classroom-App verwenden, vom Kursleiter eine Berechtigung zum Verlassen des Kurses anfordern müssen. Nur in iOS 11.3 oder höher verfügbar. **Nicht konfiguriert** erzwingt nicht, dass Kursteilnehmer um eine Berechtigung bitten müssen.
- **Drahtlose PKI-Updates zulassen**: Mit **Zulassen** können Ihre Benutzer Softwareupdates empfangen, ohne eine Verbindung ihrer Geräte mit einem Computer herzustellen.
- **Anzeigennachverfolgung begrenzen**: Wählen Sie **Begrenzen** aus, um die Geräteanzeigen-ID zu deaktivieren. **Nicht konfiguriert** behält die Aktivierung bei.
- **VPN-Erstellung blockieren (nur überwacht)**: **Blockieren** hindert Benutzer daran, VPN-Konfigurationseinstellungen zu erstellen. **Nicht konfiguriert** ermöglicht Benutzern das Erstellen von VPNs auf dem Gerät.

## <a name="configurations-requiring-supervision"></a>Konfigurationen, die Überwachung erfordern

Der überwachte Modus von iOS kann nur während der ersten Einrichtung des Geräts über das Apple-Programm zur Geräteregistrierung oder mithilfe von Apple Configurator aktiviert werden. Sobald der überwachte Modus aktiviert ist, kann Intune ein Gerät mit folgenden Funktionen konfigurieren:

- App-Sperre (Einzelanwendungsmodus) 
- Globaler HTTP-Proxy 
- Umgehung der Aktivierungssperre 
- Modus der autonomen einzelnen App 
- Webinhaltsfilter 
- Festlegen von Hintergrund und Sperrbildschirm 
- App-Pushbenachrichtigung im Hintergrund 
- Always On-VPN 
- Zulassen von ausschließlich verwalteter App-Installation 
- iBookstore 
- iMessages 
- Gamecenter 
- AirDrop 
- AirPlay 
- Hostkopplung 
- Cloudsynchronisierung 
- Spotlight-Suche 
- Übergabe 
- Gerät löschen 
- Einschränkungen-Benutzeroberfläche 
- Installation von Konfigurationsprofilen von der Benutzeroberfläche 
- News 
- Tastenkombinationen 
- Kennungsänderungen 
- Änderungen des Gerätenamens 
- Automatische App-Downloads 
- Änderungen der Vertrauensstellung für Unternehmens-Apps 
- Apple Music 
- E-Mail-Ablage 
- Kopplung mit Apple Watch 

> [!NOTE]
> Apple hat angekündigt, dass bestimmte Einstellungen im Jahr 2019 in den überwachten Modus übergehen. Bedenken Sie dies, wenn Sie diese Einstellungen verwenden, und warten Sie nicht, bis Apple diese zum überwachten Modus migriert:
> - App-Installation durch Benutzer
> - App-Deinstallation
> - FaceTime
> - Safari
> - iTunes
> - Anstößiger Inhalt
> - Dokumente und Daten von iCloud
> - Multiplayerspiele
> - Gamecenter-Freunde hinzufügen
> - Siri

## <a name="password"></a>Kennwort

- **Kennwort:** Der Endbenutzer muss ein Kennwort eingeben, um auf das Gerät zugreifen zu können. „Nicht konfiguriert“ ermöglicht Benutzern, ohne Kennworteingabe auf das Gerät zuzugreifen.
  - **Einfache Kennwörter**: Wählen Sie **Blockieren** aus, um komplexere Kennwörter zu erzwingen. **Nicht konfiguriert** ermöglicht einfache Kennwörter wie z.B. `0000` und `1234`.
  - **Erforderlicher Kennworttyp**: Wählen Sie den Kennworttyp aus, den Ihre Organisation fordert. Folgende Optionen sind verfügbar:
    - **Gerätestandard**
    - **Numerisch**
    - **Alphanumerisch**
  - **Anzahl nicht alphanumerischer Zeichen im Kennwort**: Geben Sie die Anzahl von Symbolzeichen ein (z.B. `#` oder `@`), die im Kennwort enthalten sein müssen.
  - **Minimale Kennwortlänge**: Geben Sie die Mindestlänge an, die ein Benutzer eingeben muss (zwischen 4 und 14 Zeichen).
  - **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird**: Geben Sie die Anzahl zulässiger Anmeldefehler (von 1 bis 11) ein, bevor das Gerät zurückgesetzt wird.
  - **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts**<sup>1</sup>: Geben Sie an, wie lange das Gerät inaktiv bleibt, bevor der Benutzer sein Kennwort erneut eingeben muss. Wenn Sie einen längeren Zeitraum eingeben, als derzeit auf dem Gerät eingestellt ist, ignoriert das Gerät Ihre Eingabe. Wird auf Geräten ab iOS 8.0 unterstützt.
  - **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung**<sup>1</sup>: Geben Sie an, wie viele Minuten ein Gerät höchstens inaktiv sein darf, bevor es automatisch gesperrt wird. Wenn Sie einen längeren Zeitraum eingeben, als derzeit auf dem Gerät eingestellt ist, ignoriert das Gerät Ihre Eingabe.
  - **Kennwortablauf (Tage)**: Geben Sie die Anzahl der Tage an, nach denen das Gerätekennwort geändert werden muss.
  - **Wiederverwendung vorheriger Kennwörter verhindern**: Geben Sie die Anzahl neuer Kennwörter ein, die verwendet werden müssen, bevor ein altes Kennwort wiederverwendet werden kann.
  - **Entsperrung durch Fingerabdruck**: Wählen Sie **Blockieren** aus, um die Verwendung eines Fingerabdrucks zum Entsperren des Geräts zu verhindern. **Nicht konfiguriert** ermöglicht dem Benutzer das Entsperren des Geräts mittels Fingerabdruck.
- **Änderung von Kennung (nur überwacht)**: Wählen Sie **Blockieren** aus, damit die Kennung nicht geändert, hinzugefügt oder entfernt werden kann. Änderungen an Kennungseinschränkungen werden nach der Blockierung dieser Funktion auf überwachten Geräten ignoriert. **Nicht konfiguriert** ermöglicht, Kennungen hinzuzufügen, zu ändern oder zu entfernen.
  - **Fingerabdruckänderung (nur überwacht):** **Blockieren** hindert den Benutzer daran, TouchID-Fingerabdrücke zu ändern, hinzuzufügen oder zu entfernen. **Nicht konfiguriert** ermöglicht dem Benutzer das Aktualisieren der TouchID-Fingerabdrücke auf dem Gerät.
- **AutoAusfüllen für Kennwörter blockieren (nur überwacht)**: Wählen Sie **Blockieren** aus, um die Verwendung der Funktion zum automatischen Ausfüllen von Kennwörtern unter iOS zu verhindern. Die Auswahl von **Blockieren** bewirkt auch Folgendes:
  - Benutzer werden nicht aufgefordert, in Safari oder beliebigen Apps gespeicherte Kennwörter zu verwenden.
  - Automatische sichere Kennwörter sind deaktiviert, und sichere Kennwörter werden Benutzern nicht empfohlen.

  **Nicht konfiguriert** lässt diese Funktionen zu.

- **Kennwortanforderungen durch Näherung blockieren (nur überwacht)**: Wählen Sie **Blockieren** aus, damit das Gerät eines Benutzers keine Kennwörter von in der Nähe befindlichen Geräten anfordert. **Nicht konfiguriert** lässt diese Kennwortanforderungen zu.
- **Kennwortfreigabe blockieren (nur überwacht)**: **Blockieren** verhindert die Freigabe von Kennwörtern zwischen Geräten mit AirDrop. **Nicht konfiguriert** ermöglicht die Freigabe von Kennwörtern.

<sup>1</sup> Wenn Sie die Einstellungen **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung** und **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts** konfigurieren, werden diese nacheinander angewendet. Wenn Sie beispielsweise den Wert für beide Einstellungen auf **5** Minuten einstellen, wird der Bildschirm automatisch nach fünf Minuten deaktiviert, und das Gerät wird nach weiteren fünf Minuten gesperrt. Wenn der Benutzer den Bildschirm jedoch manuell deaktiviert, wird die zweite Einstellung sofort angewendet. Im selben Beispiel wird das Gerät fünf Minuten später gesperrt, nachdem der Benutzer den Bildschirm deaktiviert hat.

## <a name="locked-screen-experience"></a>Benutzererfahrung „Gesperrter Bildschirm“

- **Kontrollcenterzugriff bei gesperrtem Gerät**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Kontrollcenter-App zu verhindern, während das Gerät gesperrt ist. **Nicht konfiguriert** erlaubt dem Benutzer den Zugriff auf die Kontrollcenter-App, während das Gerät gesperrt ist.
- **Benachrichtigungen bei Gerätesperre**: **Blockieren** verhindert den Zugriff auf Benachrichtigungen, wenn das Gerät gesperrt ist. **Nicht konfiguriert** erlaubt dem Benutzer den Zugriff auf die Benachrichtigungen, ohne dass das Gerät entsperrt werden muss.
- **Wallet-Benachrichtigungen bei gesperrtem Gerät**: **Blockieren** verhindert den Zugriff auf die Wallet-App, wenn das Gerät gesperrt ist. **Nicht konfiguriert** erlaubt dem Benutzer den Zugriff auf die Wallet-App, während das Gerät gesperrt ist.
- **Ansicht „Heute“ bei Gerätesperre**: **Blockieren** verhindert den Zugriff auf die Ansicht „Heute“, während das Gerät gesperrt ist. **Nicht konfiguriert** erlaubt dem Benutzer den Zugriff auf die Ansicht „Heute“, während das Gerät gesperrt ist.

## <a name="app-store-doc-viewing-gaming"></a>App Store, Dokumentanzeige, Spiele

- **App Store**: **Blockieren** verhindert den Zugriff auf den App Store auf überwachten Geräte. **Nicht konfiguriert** ermöglicht den Zugriff.
  - **Installieren von Apps über den App Store (nur überwacht)**: Wählen Sie **Blockieren** aus, um den App Store auf dem Startbildschirm des Geräts zu blockieren. Endbenutzer können weiterhin iTunes oder das Apple Configurator-Tool zum Installieren von Apps verwenden. **Nicht konfiguriert** lässt den App Store auf dem Startbildschirm zu.
  - **Automatische App-Downloads (nur überwacht)**: Wählen Sie **Blockieren** aus, um den automatischen Download von Apps zu verhindern, die auf anderen Geräten erworben wurden. Updates vorhandener Apps sind nicht betroffen. **Nicht konfiguriert** ermöglicht, Apps auf das Gerät herunterzuladen, die auf anderen iOS-Geräten gekauft wurden.
- **Kennwort für Zugriff auf App Store**: Mit **Anfordern** erzwingen Sie die Kennworteingabe durch Benutzer, bevor diese den App Store besuchen können. **Nicht konfiguriert** ermöglicht Benutzern, ohne Eingabe eines Kennworts auf den App Store zuzugreifen.
- **In-App-Einkäufe**: Wählen Sie **Blockieren** aus, um In-App-Einkäufe im Store zu verhindern. **Nicht konfiguriert** ermöglicht Einkäufe im Store in einer ausgeführten App.
- **Anstößige iTunes-Musik-, Podcast- oder Nachrichteninhalte (nur überwachter Modus)**: Wählen Sie **Blockieren** aus, um anstößige iTunes-Musik-, Podcast- oder Nachrichteninhalte zu verhindern. **Nicht konfiguriert** ermöglicht, dass das Gerät im Store auf nicht jugendfreie Inhalte zugreift.
- **Als „Erotik“ gekennzeichneten Inhalt aus dem iBook Store herunterladen**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer Medien aus dem iBook Store herunterladen, die als „Erotik“ gekennzeichnet sind. **Nicht konfiguriert** gestattet dem Benutzer das Herunterladen von Büchern aus der Kategorie „Erotik“.
- **Anzeige von Unternehmensdokumenten in nicht verwalteten Apps**: **Blockieren** verhindert die Anzeige unternehmenseigener Dokumente in nicht verwalteten Apps. **Nicht konfiguriert** gestattet die Anzeige von Unternehmensdokumenten in beliebigen Apps. Beispiel: Sie möchten verhindern, dass Benutzer Dateien aus der OneDrive-App in Dropbox speichern. Legen Sie für diese Einstellung **Blockieren** fest. Sobald das Gerät die Richtlinie empfängt (z.B. nach einem Neustart), ist kein Speichern mehr möglich.
- **Anzeige nicht unternehmenseigener Dokumente in Unternehmens-Apps**: **Blockieren** verhindert die Anzeige nicht unternehmenseigener Dokumente in Unternehmens-Apps. **Nicht konfiguriert** gestattet die Anzeige beliebiger Dokumente in verwalteten Unternehmens-Apps.
- **AirDrop als nicht verwaltetes Ziel behandeln**: **Anfordern** erzwingt, dass AirDrop als nicht verwaltetes Drop-Ziel betrachtet wird. Es hindert verwaltete Apps daran, Daten mithilfe von AirDrop zu senden. 
- **Hinzufügen von Game Center-Freunden (nur überwachter Modus)**: **Blockieren** hindert Benutzer daran, Game Center-Freunde hinzuzufügen. **Nicht konfiguriert** gestattet dem Benutzer, im Game Center Freunde hinzuzufügen.
- **Game Center (nur überwacht)**: **Blockieren** Sie die Verwendung der Game Center-App. **Nicht konfiguriert** ermöglicht die Verwendung der Game Center-App auf dem Gerät.
- **Multiplayerspiele (nur überwachter Modus)**: Wählen Sie **Blockieren** aus, um Multiplayerspiele zu verhindern. **Nicht konfiguriert** ermöglicht, dass der Benutzer Multiplayerspiele auf dem Gerät spielt.
- **Bewertungsregion**: Wählen Sie die Bewertungsregion aus, die Sie für die zulässigen Downloads verwenden möchten. Wählen Sie dann die zulässigen Bewertungen für **Filme** und **Fernsehsendungen** aus.
- **Apps**: Wählen Sie die zulässigen Altersfreigaben von Apps aus, die Benutzer herunterladen dürfen. Sie können auch **Alle Apps** auswählen.

## <a name="built-in-apps"></a>Integrierte Apps

- **Kamera**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Kamera des Geräts zu verhindern. **Nicht konfiguriert** ermöglicht den Zugriff auf die Kamera des Geräts.
  - **FaceTime**: Mit **Blockieren** verhindern Sie den Zugriff auf die FaceTime-App. **Nicht konfiguriert** ermöglicht den Zugriff auf die FaceTime-App des Geräts.
- **Siri**: **Blockieren** verhindert den Zugriff auf Siri. **Nicht konfiguriert** ermöglicht die Verwendung des Sprach-Assistenten Siri auf dem Gerät.
  - **Siri bei Gerätesperre**: Wählen Sie **Blockieren** aus, um den Zugriff auf Siri zu verhindern, wenn das Gerät gesperrt ist. **Nicht konfiguriert** ermöglicht die Verwendung des Sprach-Assistenten Siri auf dem Gerät, wenn das Gerät gesperrt ist.
  - **Siri-Filter für anstößige Ausdrücke (nur überwacht)**: **Anfordern** verhindert, dass Siri anstößige Ausdrücke diktiert oder verwendet.
  - **Abfrage von benutzergeneriertem Inhalt aus dem Internet durch Siri (nur überwacht)**: **Blockieren** hindert Siri daran, für die Beantwortung von Fragen auf Websites zuzugreifen. **Nicht konfiguriert** ermöglicht Siri, auf benutzergenerierten Inhalt aus dem Internet zuzugreifen.
- **Apple News (nur überwacht)**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Apple News-App auf dem Gerät zu verhindern. **Nicht konfiguriert** ermöglicht die Verwendung der Apple News-App.
- **Zugriff auf den iBooks Store (nur überwacht)**: **Blockieren** verhindert den Zugriff auf den iBooks Store. **Nicht konfiguriert** ermöglicht Benutzern, den iBooks Store zu durchsuchen und dort Bücher zu erwerben.
- **Nachrichten-App auf dem Gerät (nur überwacht)**: Wählen Sie **Blockieren** aus, damit Benutzer die Nachrichten-App auf dem Gerät nicht verwenden können. **Nicht konfiguriert** ermöglicht die Verwendung der Nachrichten-App zum Senden und Lesen von Textnachrichten.
- **Podcasts (nur überwacht)**: **Blockieren** hindert Benutzer an der Verwendung der Podcasts-App. **Nicht konfiguriert** ermöglicht die Verwendung der Podcasts-App.
- **Musikdienst (nur überwacht)**: **Blockieren** setzt die Music-App in den klassischen Modus zurück und deaktiviert den Musikdienst. **Nicht konfiguriert** ermöglicht die Verwendung der Apple Music-App.
- **iTunes Radio-Dienst (nur überwacht)**: **Blockieren** hindert Benutzer daran, die iTunes Radio-App zu verwenden. **Nicht konfiguriert** ermöglicht die Verwendung der iTunes Radio-App.
- **Änderungen an den Einstellungen der App „Meine Freunde suchen“ (nur überwacht)**: **Blockieren** verhindert Änderungen der Einstellungen für die App „Meine Freunde suchen“. **Nicht konfiguriert** ermöglicht Benutzern das Ändern von Einstellungen für die App „Meine Freunde suchen“.
- **Spotlight-Suche gibt Ergebnisse aus dem Internet zurück (nur überwacht)**: **Blockieren** verhindert, dass Spotlight Ergebnisse einer Internetsuche zurückgibt. **Nicht konfiguriert** ermöglicht Spotlight das Herstellen einer Verbindung mit dem Internet zur Bereitstellung von Suchergebnissen.
- **Entfernen von System-Apps vom Gerät blockieren (nur überwacht)**: Die Auswahl von **Blockieren** deaktiviert die Möglichkeit, System-Apps vom Gerät zu entfernen. **Nicht konfiguriert** ermöglicht Benutzern, System-Apps zu entfernen.

## <a name="restricted-apps"></a>Eingeschränkte Apps

In der Liste der eingeschränkten Apps können Sie eine der folgenden Listen konfigurieren:

- **Unzulässige Apps**: Eine Liste nicht von Intune verwalteter Apps, die nicht auf dem Gerät installiert werden sollen. Wenn ein Benutzer eine App aus dieser Liste installiert, werden Sie von Intune benachrichtigt.
- **Genehmigte Apps**: Eine Liste von Apps, die Benutzer installieren dürfen. Um die Kompatibilität zu gewährleisten, dürfen Benutzer keine anderen Apps installieren. Apps, die von Intune verwaltet werden, sind automatisch zugelassen. Wenn ein Benutzer eine App aus dieser Liste installiert, werden Sie von Intune benachrichtigt.

Um diesen Listen Apps hinzuzufügen, können Sie:

- Die iTunes App-Store-URL der App **hinzufügen**, die Sie wünschen. Geben Sie beispielsweise zum Hinzufügen der Microsoft Work Folders-App `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` ein.

  Um die URL einer App zu suchen, öffnen Sie den iTunes App Store, und suchen Sie nach der App. Suchen Sie beispielsweise nach `Microsoft Remote Desktop` oder `Microsoft Word`. Wählen Sie die App aus, und kopieren Sie die URL.

  Sie können auch iTunes verwenden, um die App zu suchen, und dann die Aufgabe **Link kopieren**, um die App-URL abzurufen.

- Importieren Sie eine CSV-Datei mit den Details der App, einschließlich der URL. Verwenden Sie das Format <app url>, <app name>, <app publisher>. Exportieren Sie alternativ eine vorhandene Liste, die die Liste der eingeschränkten Apps im gleichen Format enthält.

> [!IMPORTANT]
> Geräteprofile, die Einstellungen für eingeschränkte Apps verwenden, müssen Benutzergruppen zugewiesen werden.

## <a name="show-or-hide-apps-supervised-only"></a>Ein- oder Ausblenden von Apps (nur überwacht)

In der Liste „Apps ein- oder ausblenden“ können Sie eine der folgenden Listen konfigurieren (erfordert überwachte Geräte mit iOS 9.3 oder höher).

- **Ausgeblendete Apps:** Geben Sie eine Liste von Apps an, die vor Benutzern verborgen werden. Benutzer können diese Apps weder anzeigen noch öffnen.
- **Sichtbare Apps**: Geben Sie eine Liste von Apps ein, die Benutzer anzeigen und starten können. Es können keine anderen Apps angezeigt oder gestartet werden.

Um diesen Listen Apps hinzuzufügen, können Sie:

- Die iTunes App-Store-URL der App **hinzufügen**, die Sie wünschen. Geben Sie beispielsweise zum Hinzufügen der Microsoft Work Folders-App `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` ein.

  Um die URL einer App zu suchen, öffnen Sie den iTunes App Store, und suchen Sie nach der App. Suchen Sie beispielsweise nach `Microsoft Remote Desktop` oder `Microsoft Word`. Wählen Sie die App aus, und kopieren Sie die URL.

  Sie können auch iTunes verwenden, um die App zu suchen, und dann die Aufgabe **Link kopieren**, um die App-URL abzurufen.

- Importieren Sie eine CSV-Datei mit den Details der App, einschließlich der URL. Verwenden Sie das Format <app url>, <app name>, <app publisher>. Exportieren Sie alternativ eine vorhandene Liste, die die Liste der eingeschränkten Apps im gleichen Format enthält.

## <a name="wireless"></a>Drahtlos

- **Datenroaming**: Wählen Sie **Blockieren** aus, um Datenroaming über das Mobilfunknetz zu verhindern. **Nicht konfiguriert** ermöglicht das Datenroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.
- **Globales Abrufen im Hintergrund beim Roaming**: **Blockieren** verhindert, dass die Funktion des globalen Abrufens im Hintergrund beim Roaming über das Mobilfunknetz verwendet wird. **Nicht konfiguriert** ermöglicht, dass das Gerät Daten wie E-Mails beim Roaming in einem Mobilfunknetz abruft.
- **Sprachwahlverfahren**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer das Sprachwahlverfahren auf dem Gerät verwenden. **Nicht konfiguriert** ermöglicht die Verwendung des Sprachwahlverfahrens auf dem Gerät.
- **Sprachroaming**: Wählen Sie **Blockieren** aus, um Sprachroaming über das Mobilfunknetz zu verhindern. **Nicht konfiguriert** ermöglicht das Sprachroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.
- **Änderungen an den Einstellungen zur App-Mobilfunkdatennutzung (nur überwacht)**: Wählen Sie **Blockieren** aus, um Änderungen an den Einstellungen zur App-Mobilfunkdatennutzung zu verhindern. **Nicht konfiguriert** ermöglicht Benutzern, zu steuern, welche Apps Mobilfunkdaten verwenden dürfen.
- **Privater Hotspot**: **Blockieren** verhindert, dass das Gerät als privater Hotspot verwendet wird. Diese Einstellung kann mit einigen Anbietern nicht kompatibel sein. **Nicht konfiguriert** lässt diese Funktion zu.
- **Verknüpfen von WLAN-Netzwerken nur mithilfe von Konfigurationsprofilen (nur überwacht):** **Anfordern** erzwingt, dass das Gerät nur WLAN-Netzwerke verwendet, die mit Intune-Konfigurationsprofilen eingerichtet wurden. **Nicht konfiguriert** ermöglicht dem Gerät, andere WLAN-Netzwerke zu verwenden.
- **Mobilfunk-Verwendungsregeln (nur verwaltete Apps)**: Definieren Sie die Datentypen, die von verwalteten Apps genutzt werden können, wenn sie sich in Mobilfunknetzwerken befinden. Folgende Optionen sind verfügbar:
  - **Verwendung von Datenverbindungen blockieren**: Blockieren Sie die Verwendung von Datenverbindungen für **Alle verwalteten Apps**, oder Sie können **Bestimmte Apps wählen**.
  - **Verwendung von Datenverbindungen beim Roaming blockieren:** Blockieren Sie die Verwendung von Datenverbindungen beim Roaming für **Alle verwalteten Apps**, oder Sie können **Bestimmte Apps wählen**.

## <a name="connected-devices"></a>Verbundene Geräte

- **AirDrop (nur überwacht)**: **Blockieren** verhindert die Verwendung von AirDrop auf dem Gerät. **Nicht konfiguriert** ermöglicht die Verwendung von AirDrop zum Austauschen von Inhalten mit Geräten in der Nähe.
- **Apple Watch-Kopplung (nur überwacht):** **Blockieren** verhindert die Gerätekopplung mit einer Apple Watch. **Nicht konfiguriert** ermöglicht die Gerätekopplung mit einer Apple Watch.
- **Handgelenkerkennung für gekoppelte Apple Watch**: **Anfordern** erzwingt, dass eine gekoppelte Apple Watch die Handgelenkerkennung verwendet. Wenn dies erforderlich ist, zeigt die Apple Watch keine Benachrichtigungen an, wenn sie nicht getragen wird. 
- **Bluetooth-Änderung (nur überwacht)**: **Blockieren** hindert den Endbenutzer an der Änderung von Bluetooth-Einstellungen auf dem Gerät. **Nicht konfiguriert** ermöglicht dem Benutzer, diese Einstellungen zu ändern.
- **Hostkopplung, um zu steuern, mit welchen Geräten ein iOS-Gerät gekoppelt werden kann (nur überwacht)**: **Nicht konfiguriert** erlaubt die Hostkopplung, damit der Administrator steuern kann, mit welchen Geräten ein iOS-Gerät gekoppelt werden kann. **Blockieren** verhindert die Hostkopplung.
- **Kopplungskennwort für ausgehende AirPlay-Anforderungen anfordern**: **Anfordern** eines Kopplungskennworts, wenn der Benutzer AirPlay zum Streamen von Inhalten auf andere Apple-Geräte verwendet. **Nicht konfiguriert** ermöglicht dem Benutzer das Streamen von Inhalten über AirPlay ohne Kennworteingabe.
- **Block AirPrint (nur überwacht)**: Wählen Sie **Blockieren** aus, um die Verwendung der AirPrint-Funktion auf dem Gerät zu verhindern. **Nicht konfiguriert** ermöglicht dem Benutzer, AirPrint zu verwenden.
  - **Speichern von AirPrint-Anmeldeinformationen in Keychain blockieren (nur überwacht)**: **Blockieren** verhindert, dass der Keychain-Speicher für Benutzername und Kennwort auf dem Gerät verwendet wird. **Nicht konfiguriert** ermöglicht das Speichern von AirPrint-Benutzername und -Kennwort in der Keychain-App.
  - **Vertrauenswürdiges TLS-Zertifikat für AirPrint anfordern (nur überwacht)**: **Anfordern** erzwingt, dass das Gerät vertrauenswürdige Zertifikate für die TLS-Druckkommunikation verwendet.
  - **iBeacon-Ermittlung von AirPrint-Druckern blockieren (nur überwacht)**: **Blockieren** hindert böswillige AirPrint Bluetooth-Beacons am Phishing nach Netzwerkverkehr. **Nicht konfiguriert** ermöglicht das Ankündigen von AirPrint-Druckern auf dem Gerät.

## <a name="keyboard-and-dictionary"></a>Tastatur und Wörterbuch

- **Suche nach Wortdefinitionen (nur überwacht)**: **Blockieren** hindert Benutzer daran, ein Wort zu markieren und dann auf dem Gerät nach seiner Definition zu suchen. **Nicht konfiguriert** ermöglicht den Zugriff auf die Definitionssuchfunktion.
- **Tastaturwortvorschläge (nur überwacht)**: **Nicht konfiguriert** erlaubt die Verwendung von Tastaturwortvorschlägen für Wörter, die der Benutzer möglicherweise verwenden möchte. **Blockieren** verhindert die Verwendung dieser Funktion.
- **Autokorrektur (nur überwacht)**: **Nicht konfiguriert** erlaubt dem Gerät die automatische Korrektur von falsch geschriebenen Wörtern. **Blockieren** verhindert die Verwendung von Autokorrektur.
- **Rechtschreibprüfung über Tastatur (nur überwacht)**: **Nicht konfiguriert** ermöglicht das Verwenden der Rechtschreibprüfung auf dem Gerät. **Blockieren** ermöglicht die Rechtschreibprüfung.
- **Tastenkombinationen (nur überwacht)**: **Nicht konfiguriert** ermöglicht die Verwendung von Tastenkombinationen auf dem Gerät. **Blockieren** hindert den Benutzer an der Verwendung von Tastenkombinationen.
- **Diktatfunktion (nur überwacht)**: **Blockieren** verhindert, dass der Benutzer die Spracheingabe zur Eingabe von Text verwendet. **Nicht konfiguriert** ermöglicht dem Benutzer, die Spracheingabe zu verwenden.

## <a name="cloud-and-storage"></a>Cloud und Speicher

- **In iCloud sichern**: **Nicht konfiguriert** ermöglicht dem Benutzer, das Gerät in iCloud zu sichern. **Blockieren** hindert den Benutzer daran, das Gerät in iCloud zu sichern.
- **Dokumentsynchronisierung in iCloud (nur überwachter Modus)**: **Nicht konfiguriert** ermöglicht die Dokument- und Schlüssel-/Wertsynchronisierung in Ihrem iCloud-Speicher. **Blockieren** hindert iCloud daran, Dokumente und Daten zu synchronisieren.
- **Synchronisierung von Fotostreams in iCloud**: **Nicht konfiguriert** ermöglicht Benutzern das Aktivieren von **Mein Photo Stream** auf ihren Geräten zum Synchronisieren mit iCloud, damit Fotos auf allen Geräten der Benutzer verfügbar sind. **Blockieren** verhindert die Fotostream-Synchronisierung mit iCloud.
- **Verschlüsselte Sicherung**: **Anfordern** erzwingt die Verschlüsselung von Gerätesicherungen.
- **iCloud-Fotomediathek**: Deaktivieren Sie mit **Blockieren** die Verwendung der iCloud-Fotomediathek zum Speichern von Fotos und Videos in der Cloud. Fotos, die nicht vollständig aus der iCloud-Fotomediathek auf das Gerät heruntergeladen wurden, werden vom Gerät entfernt. **Nicht konfiguriert** ermöglicht die Verwendung der iCloud-Fotomediathek.
- **Synchronisierung verwalteter Apps mit der Cloud**: **Nicht konfiguriert** ermöglicht Ihren mit Intune verwalteten Apps, Daten mit dem iCloud-Konto des Benutzers zu synchronisieren. **Blockieren** verhindert diese Datensynchronisierung mit iCloud.
- **Streaming freigegebener Fotos**: Wählen Sie **Blockieren** aus, um die **iCloud-Fotofreigabe** auf dem Gerät zu deaktivieren. **Nicht konfiguriert** ermöglicht das Streaming freigegebener Fotos.
- **Aktivitätsfortsetzung**: **Nicht konfiguriert** ermöglicht Benutzern, die Arbeit, die sie auf einem iOS-Gerät gestartet haben, auf einem anderen iOS- oder macOS-Gerät fortzusetzen (Übergabe). **Blockieren** verhindert diese Übergabe.
- **Synchronisierung zwischen iCloud und Keychain blockieren**: Wählen Sie **Blockieren** aus, um die Synchronisierung in der Keychain gespeicherter Anmeldeinformationen mit iCloud zu deaktivieren. **Nicht konfiguriert** ermöglicht dem Benutzer, diese Anmeldeinformationen zu synchronisieren.
- **Enterprise Book-Sicherung blockieren**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer Enterprise Books sichern. **Nicht konfiguriert** ermöglicht dem Benutzer, diese Bücher zu sichern.
- **Synchronisierung von Enterprise Book-Metadaten blockieren (Notizen und Highlights)**: **Blockieren** verhindert, dass Notizen und Highlights in Enterprise Books synchronisiert werden. **Nicht konfiguriert** ermöglicht die Synchronisierung.

## <a name="autonomous-single-app-mode-supervised-only"></a>Modus der autonomen einzelnen App (nur überwacht)

Verwenden Sie diese Einstellungen, um iOS-Geräte zur Ausführung bestimmter Apps im Modus der autonomen einzelnen App zu konfigurieren. Wenn dieser Modus konfiguriert ist und die App ausgeführt wird, wird das Gerät gesperrt. Es kann nur die App ausführen. Fügen Sie z.B. eine App hinzu, mit der Benutzer einen Test auf dem Gerät durchführen können. Wenn die Aktionen der App abgeschlossen sind, oder Sie diese Richtlinie entfernen, kehrt das Gerät in seinen normalen Zustand zurück.

Apps können Sie wie folgt hinzufügen:

- Geben Sie den **App-Namen** und die **App-Bündel-ID** ein, und wählen Sie **Hinzufügen** aus. [Bündel-ID-Referenz für integrierte iOS-Apps](#bundle-id-reference-for-built-in-ios-apps) (in diesem Artikel) enthält einige Apps mit ihren IDs.
- **Importieren** Sie eine CSV-Datei mit der Liste der App-Namen und der Bündel-IDs. **Exportieren** Sie alternativ eine vorhandene Liste, die die Apps enthält.

## <a name="kiosk-supervised-only"></a>Kiosk (nur überwacht)

- **Im Kioskmodus auszuführende App**: Wählen Sie den Typ der Apps aus, die Sie im Kioskmodus ausführen möchten. Folgende Optionen sind verfügbar: 
  - **Store-App**: Geben Sie die URL zu einer App im iTunes App-Store ein
  - **Verwaltete App**: Wählen Sie eine App aus, die Sie in Intune hinzugefügt haben
  - **Integrierte App**: Geben Sie die [Bündel-ID](#bundle-id-reference-for-built-in-ios-apps) der integrierten App ein

- **Touch-Unterstützung**: Zum **Anfordern** der Barrierefreiheitseinstellung „Touch-Unterstützung“ auf dem Gerät. Diese Funktion hilft Benutzern mit Bildschirmgesten bei Vorgängen, die für sie schwierig sein könnten. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- **Farben umkehren:** **Anfordern** der Barrierefreiheitseinstellung „Farben umkehren“, die die Anzeige für Benutzer mit eingeschränkter Sehfähigkeit anpasst. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- **Mono-Audio**: **Anfordern** der Barrierefreiheitseinstellung „Mono-Audio“ auf dem Gerät. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- **VoiceOver**: **Anfordern** der Barrierefreiheitseinstellung „VoiceOver“ auf dem Gerät, um Text auf dem Bildschirm vorlesen zu lassen. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- **Zoom**: **Anfordern** der Einstellung „Zoom“ auf dem Gerät, damit Benutzer die Bildschirmausgabe mittels Toucheingabe vergrößern können. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- **Automatische Sperre**: Automatische Sperrung des Geräts **Zulassen**. **Nicht konfiguriert** deaktiviert dieses Feature.
- **Ruftonschalter:** Stummschaltung (Ruftonschalter) am Gerät **Zulassen**. **Nicht konfiguriert** deaktiviert dieses Feature.
- **Bildschirmdrehung:** Ändern der Bildschirmausrichtung, wenn der Benutzer das Gerät dreht, **Zulassen**. **Nicht konfiguriert** deaktiviert dieses Feature.
- **Standbytaste:** Wählen Sie **Zulassen** aus, um die Standbytaste am Gerät zu aktivieren oder deaktivieren. **Nicht konfiguriert** aktiviert diese Funktion.
- **Touch**: **Blockieren** deaktiviert den Touchscreen des Geräts. **Nicht konfiguriert** ermöglicht dem Benutzer, den Touchscreen zu verwenden.
- **Lautstärkeregler**: **Zulassen** der Verwendung der Lautstärkeregler am Gerät. **Nicht konfiguriert** deaktiviert die Lautstärkeregler.
- **Steuerelement der Touch-Unterstützung**: Mit **Zulassen** können Benutzer die Touch-Unterstützungsfunktion verwenden. **Nicht konfiguriert** deaktiviert dieses Feature.
- **Steuerelement zum Umkehren von Farben**: **Zulassen** von Farbumkehr-Anpassungen, mit denen der Benutzer die Funktion zur Farbumkehr individuell verwenden kann. **Nicht konfiguriert** deaktiviert dieses Feature.
- **Ausgewählten Text sprechen**: **Zulassen** der Sprachauswahl-Barrierefreiheitseinstellungen auf dem Gerät. Diese Funktion liest Text, den der Benutzer auswählt, laut vor. **Nicht konfiguriert** deaktiviert dieses Feature.
- **VoiceOver-Steuerelement**: **Zulassen** von VoiceOver-Änderungen, damit Benutzer die VoiceOver-Funktion aktualisieren können, z.B. wie schnell auf dem Bildschirm ausgegebener Text von der Sprachausgabe vorgelesen wird. **Nicht konfiguriert** verhindert VoiceOver-Änderungen.
- **Zoomsteuerelement**: **Zulassen** von Zoomänderungen durch den Benutzer. **Nicht konfiguriert** verhindert Zoomänderungen.

> [!NOTE]
> Damit Sie ein iOS-Gerät für den Kioskmodus konfigurieren können, müssen Sie das Apple Configurator-Tool oder das Apple-Programm zur Geräteregistrierung verwenden, um das Gerät in den überwachten Modus zu versetzen. Informationen zur Verwendung des Apple Configurator-Tools finden Sie im Apple-Handbuch.
> Wenn die iOS-App, die Sie eingeben, nach der Zuweisung des Profils installiert wird, wird das Gerät erst nach einem Neustart in den Kioskmodus versetzt.

## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Bündel-ID-Referenz für integrierte iOS-Apps

Diese Liste zeigt die Bündel-ID einiger gängiger integrierter iOS-Apps. Um die Bündel-ID von anderen Apps zu finden, wenden Sie sich an den Softwarehersteller.

| Paket-ID                   | App-Name     | Herausgeber |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | App Store    | Apple     |
| com.apple.calculator        | Calculator   | Apple     |
| com.apple.mobilecal         | Kalender     | Apple     |
| com.apple.camera            | Kamera       | Apple     |
| com.apple.mobiletimer       | Clock        | Apple     |
| com.apple.compass           | Compass      | Apple     |
| com.apple.MobileAddressBook | Kontakte     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.mobileme.fmf1     | Find Friends | Apple     |
| com.apple.mobileme.fmip1    | Find iPhone  | Apple     |
| com.apple.gamecenter        | Gamecenter  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Integrität       | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.Maps              | Zuordnungen         | Apple     |
| com.apple.MobileSMS         | Nachrichten     | Apple     |
| com.apple.Music             | Musik        | Apple     |
| com.apple.news              | News         | Apple     |
| com.apple.mobilenotes       | Hinweise        | Apple     |
| com.apple.Numbers           | Zahlen      | Apple     |
| com.apple.Pages             | Seiten        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Fotos       | Apple     |
| com.apple.podcasts          | Podcasts     | Apple     |
| com.apple.reminders         | Reminders    | Apple     |
| com.apple.MobileSafari      | Safari       | Apple     |
| com.apple.Preferences       | Einstellung     | Apple     |
| com.apple.stocks            | Stocks       | Apple     |
| com.apple.tips              | Tipps         | Apple     |
| com.apple.videos            | Videos       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Überwachen        | Apple     |
| com.apple.weather           | Weather      | Apple     |

## <a name="safari"></a>Safari

- **Safari (nur überwacht)**: **Blockieren** der Verwendung des Safari-Browsers auf dem Gerät. **Nicht konfiguriert** ermöglicht Benutzern die Verwendung des Safari-Browsers.
- **AutoAusfüllen**: **Blockieren** deaktiviert das AutoAusfüllen-Feature in Safari auf dem Gerät. **Nicht konfiguriert** ermöglicht Benutzern, die Einstellungen für AutoVervollständigen im Browser zu ändern.
- **Cookies**: Wählen Sie aus, wie Cookies auf dem Gerät behandelt werden. Folgende Optionen sind verfügbar:
  - Allow
  - Alle Cookies blockieren
  - Cookies von besuchten Websites zulassen
  - Cookies von aktueller Website zulassen
- **JavaScript**: **Blockieren** verhindert, dass Java-Skripts im Browser auf dem Gerät ausgeführt werden. **Nicht konfiguriert** lässt Java-Skripts zu.
- **Betrugswarnungen**: **Anfordern**, dass Betrugswarnungen im Webbrowser auf dem Gerät angezeigt werden. **Nicht konfiguriert** deaktiviert dieses Feature.
- **Popups**: **Blockieren** deaktiviert den Popupblocker im Webbrowser. **Nicht konfiguriert** lässt den Popupblocker zu.

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Nicht markierte E-Mail-Domänen

Fügen Sie in **E-Mail-Domänen-URL** eine oder mehrere URLs der Liste hinzu. Wenn Endbenutzer eine E-Mail von einer anderen Domäne als den von Ihnen eingegebenen erhalten, wird die E-Mail in der iOS-Mail-App als nicht vertrauenswürdig gekennzeichnet.

### <a name="managed-web-domains"></a>Verwaltete Webdomänen

Fügen Sie in **Webdomänen-URL** eine oder mehrere URLs der Liste hinzu. Wenn Dokumente von den Domänen heruntergeladen werden, die Sie eingeben, gelten sie als verwaltet. Diese Einstellung gilt nur für Dokumente, die mit dem Safari-Browser heruntergeladen werden.

### <a name="safari-password-autofill-domains"></a>Domänen für automatisches Ausfüllen des Safari-Kennworts

Fügen Sie in **Domänen-URL** eine oder mehrere URLs der Liste hinzu. Benutzer können nur Webkennwörter von URLs in dieser Liste speichern. Diese Einstellung gilt nur für den Safari-Browser und Geräte mit iOS 9.3 und höher im überwachten Modus. Wenn Sie keine URLs angeben, können Kennwörter von allen Websites gespeichert werden.

## <a name="next-steps"></a>Nächste Schritte

[Weisen Sie das Profil zu](device-profile-assign.md), und [überwachen Sie seinen Status](device-profile-monitor.md).
