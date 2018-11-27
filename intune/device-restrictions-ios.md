---
title: Einstellungen für Geräteeinschränkungen für iOS in Microsoft Intune
titleSuffix: ''
description: In diesem Artikel lernen Sie die Intune-Einstellungen zur Steuerung von Geräteeinstellungen und -funktionen auf iOS-Geräten kennen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 8f9e9533793a8792e9ad354392b9d8e911cd07f4
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188703"
---
# <a name="microsoft-intune-ios-device-restriction-settings"></a>Einstellungen für Geräteeinschränkungen für iOS-Geräte in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel lernen Sie die Einstellungen für Geräteeinschränkungen in Microsoft Intune kennen, die Sie für iOS-Geräte konfigurieren können.

## <a name="general"></a>Allgemein

-   **Nutzungsdaten freigeben:** Hiermit erlauben oder verhindern Sie, dass das Gerät Diagnose- und Nutzungstelemetriedaten an Apple sendet.
-   **Übermittlung von Diagnosedaten:** Ermöglicht dem Gerät das Senden von Diagnosedaten an Apple.
-   **Bildschirmaufnahme:** Erlauben Sie dem Benutzer, den Bildschirminhalt als Bild zu erfassen.
    - **Remotebildschirmüberwachung über die Classroom-App (nur überwacht):** Erlauben oder sperren Sie die Anzeige des Bildschirms auf iOS-Geräten durch die Apple Classroom-App.
    - **Unaufgeforderte Bildschirmbeobachtung durch die Classroom-App (nur überwacht)**: Falls zulässig, können Lehrer im Hintergrund die Bildschirme der iOS-Geräte ihrer Schüler mithilfe der Classroom-App überwachen, ohne dass die Schüler dies mitbekommen.
-   **Nicht vertrauenswürdige TLS-Zertifikate:** Erlauben Sie nicht vertrauenswürdige TLS-Zertifikate (Transport Layer Security) auf dem Gerät.
-   **Vertrauen für Unternehmens-App:** Ermöglicht es dem Benutzer zu entscheiden, ob Apps, die nicht aus dem App Store heruntergeladen wurden, vertraut werden soll.
- **Kontoänderung (nur überwacht):** Wenn diese Funktion blockiert ist, kann der Benutzer keine gerätespezifischen Einstellungen der iOS-Einstellungs-App ändern wie z.B. neue Gerätekonten erstellen, den Benutzernamen oder das Kennwort ändern.
Dies gilt auch für Einstellungen, auf die über die iOS-Einstellungs-App zugegriffen werden kann wie z.B. E-Mail, Kontakte, Kalender, Facebook und Twitter. Dies gilt nicht für Apps mit Kontoeinstellungen, die nicht über die iOS-Einstellungs-App konfiguriert werden können wie z.B. die Microsoft Outlook-App.
- **Aktivieren von Einschränkungen in den Geräteeinstellungen (nur überwacht):** Erlauben Sie Benutzern das Konfigurieren von Geräteeinschränkungen (Jugendschutz) auf dem Gerät.
- **Verwendung der Option zum Löschen aller Inhalte und Einstellungen auf dem Gerät (nur überwacht):** Erlauben Sie dem Benutzer die Verwendung der Option zum Löschen aller Inhalte und Einstellungen auf dem Gerät.
- **Gerätenamensänderung (nur überwacht):** Erlauben Sie dem Benutzer, den Namen des Geräts zu ändern.
- **Änderung von Benachrichtigungseinstellungen (nur überwacht):** Erlauben Sie dem Benutzer, die Benachrichtigungseinstellungen des Geräts zu ändern.
- **Änderung der Vertrauenseinstellungen für die Unternehmens-App (nur überwacht):** Ermöglicht es dem Benutzer zu entscheiden, ob Apps, die nicht aus dem App Store heruntergeladen wurden, vertraut werden soll.
- **Konfigurationsprofiländerungen (nur überwacht):** Erlauben Sie dem Benutzer die Installation von Konfigurationsprofilen.
- **Aktivierungssperre (nur überwacht):** Aktivieren Sie die Aktivierungssperre auf überwachten iOS-Geräten.

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
-   **Kennwort:** Der Endbenutzer muss ein Kennwort eingeben, um auf das Gerät zugreifen zu können.
    -   **Einfache Kennwörter:** Erlauben Sie einfache Kennwörter wie 0000 oder 1234.
    -   **Erforderlicher Kennworttyp:** Geben Sie den erforderlichen Typ des Kennworts an, z.B. nur numerisch oder alphanumerisch.
    -   **Anzahl nicht alphanumerischer Zeichen im Kennwort:** Geben Sie die Anzahl von Symbolzeichen (wie **#** oder **@**) an, die im Kennwort enthalten sein müssen.
    -   **Minimale Kennwortlänge:** Geben Sie die Mindestanzahl von Zeichen an, die das Kennwort enthalten muss.
    -   **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird:** Gibt die Anzahl fehlerhafter Anmeldeversuche an, bevor das Gerät durch diese Einstellung zurückgesetzt wird.
    -   **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts:**<sup>1</sup> Geben Sie an, wie lange das Gerät inaktiv bleiben kann, bevor der Benutzer sein Kennwort erneut eingeben muss.
    -   **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung:**<sup>1</sup> Geben Sie die Anzahl der Minuten an, bevor die Anzeige des Geräts deaktiviert wird.
    -   **Kennwortablauf (Tage):** Geben Sie die Anzahl der Tage an, bevor das Gerätekennwort geändert werden muss.
    -   **Wiederverwendung vorheriger Kennwörter verhindern:** Geben Sie an, wie viele zuvor verwendete Kennwörter vom Gerät gespeichert werden.
    -   **Entsperrung durch Fingerabdruck:** Erlauben Sie die Verwendung von Fingerabdrücken zum Entsperren kompatibler Geräte.
- **Änderung von Kennung (nur überwacht):** Die Kennung kann dadurch nicht geändert, hinzugefügt oder entfernt werden.
    - **Fingerabdruckänderung (nur überwacht):** Der Benutzer kann dadurch keine TouchID-Einstellungen ändern, hinzufügen oder entfernen.

<sup>1</sup> Wenn Sie die Einstellungen **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung** und **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts** konfigurieren, werden diese nacheinander angewendet. Wenn Sie beispielsweise den Wert für beide Einstellungen auf **5** Minuten einstellen, wird der Bildschirm automatisch nach fünf Minuten deaktiviert, und das Gerät wird nach weiteren fünf Minuten gesperrt. Wenn der Benutzer den Bildschirm jedoch manuell deaktiviert, wird die zweite Einstellung sofort angewendet. Im selben Beispiel wird das Gerät fünf Minuten später gesperrt, nachdem der Benutzer den Bildschirm deaktiviert hat.

## <a name="locked-screen-experience"></a>Benutzererfahrung „Gesperrter Bildschirm“

-   **Kontrollcenterzugriff bei gesperrtem Gerät:** Erlauben Sie dem Benutzer den Zugriff auf die Kontrollcenter-App, während das Gerät gesperrt ist.
-   **Benachrichtigungen bei Gerätesperre:** Erlauben Sie dem Benutzer den Zugriff auf die Benachrichtigungsansicht, ohne dass das Gerät entsperrt werden muss.
-   **Wallet-Benachrichtigungen bei gesperrtem Gerät:** Erlauben Sie dem Benutzer den Zugriff auf die Wallet-App, während das Gerät gesperrt ist.
-   **Ansicht „Heute“ bei Gerätesperre:** Erlauben Sie dem Benutzer den Zugriff auf die Ansicht „Heute“, während das Gerät gesperrt ist.

## <a name="app-store-doc-viewing-gaming"></a>App Store, Dokumentanzeige, Spiele


-   **App Store:** Sperren Sie den Zugriff auf den App Store auf überwachten Geräte.
    - **Installieren von Apps über den App Store (nur überwacht):** Blockiert den App Store vom Home-Bildschirm des Geräts. Endbenutzer können weiterhin iTunes oder das Apple Configurator-Tool zum Installieren von Apps verwenden.
    - **Automatische App-Downloads (nur überwacht):** Dadurch können keine Apps, die auf einem anderen iOS-Gerät erworben wurden, auf dieses Gerät heruntergeladen werden.
-   **Kennwort für Zugriff auf App Store:** Erzwingen Sie die Kennworteingabe durch Benutzer, bevor diese den App Store besuchen können.
-   **In-App-Käufe:** Erlauben Sie Einkäufe im Store in einer ausgeführten App.
-   **Anstößige iTunes-Musik-, Podcast- oder Nachrichteninhalte (nur überwachter Modus):** Erlauben Sie, dass das Gerät im Store auf nicht jugendfreie Inhalte zugreift.
-   **Als „Erotik“ gekennzeichneten Inhalt aus dem iBook Store herunterladen:** Erlauben Sie dem Benutzer das Herunterladen von Büchern aus der Kategorie „Erotik“.
-   **Anzeige von Unternehmensdokumenten in nicht verwalteten Apps:** Erlauben Sie die Anzeige von Unternehmensdokumenten in beliebigen Apps.<br>**Beispiel:** Sie möchten verhindern, dass Benutzer Dateien aus der OneDrive-App in Dropbox speichern. Legen Sie für diese Einstellung „Nein“ fest. Sobald das Gerät die Richtlinie empfängt (z. B. nach einem Neustart), ist kein Speichern mehr möglich.
-   **Anzeige nicht unternehmenseigener Dokumente in Unternehmens-Apps:** Erlauben Sie die Anzeige beliebiger Dokumente in verwalteten Apps.
-   **AirDrop als nicht verwaltetes Ziel behandeln:** Verwaltete Apps am Senden von Daten mit Airdrop hindern.
-   **Hinzufügen von Game Center-Freunden (nur überwachter Modus):** Erlauben Sie, dass der Benutzer im Game Center Freunde hinzufügt.
-   **Game Center (nur überwacht):** Sperren oder erlauben Sie die Verwendung der Game Center-App.
-   **Multiplayerspiele (nur überwachter Modus):** Erlauben Sie, dass der Benutzer Spiele für mehrere Spieler auf dem Gerät spielt.
-   **Bewertungsregion:** Wählen Sie die Bewertungsregion aus, für die Sie die zulässigen Downloads konfigurieren möchten, und wählen anschließend die zulässigen Bewertungen für **Filme** und **Fernsehsendungen** aus.
-   **Apps:** Wählen Sie die zulässigen Altersfreigaben von Apps aus, die Benutzer herunterladen dürfen. Sie können auch **Alle Apps** auswählen.

## <a name="built-in-apps"></a>Integrierte Apps

-   **Kamera:** Legen Sie fest, ob die Kamera des Geräts verwendet werden darf.
    -   **FaceTime:** Erlauben Sie die Verwendung der FaceTime-App auf dem Gerät.
-   **Siri:** Erlauben Sie die Verwendung des Sprach-Assistenten Siri auf dem Gerät.
    -   **Siri bei Gerätesperre:** Erlauben Sie die Verwendung des Sprach-Assistenten Siri auf dem Gerät, während das Gerät gesperrt ist.
    -   **Siri-Filter für anstößige Ausdrücke (nur überwacht):** Verhindert, dass Siri anstößige Ausdrücke diktiert oder verwendet.
    -   **Abfrage von benutzergeneriertem Inhalt aus dem Internet durch Siri (nur überwacht):** Erlauben Sie Siri, für die Beantwortung von Fragen auf Websites zuzugreifen.
- **Apple News (nur überwacht):** Erlauben Sie die Verwendung der Apple News-App.
- **iBooks Store (nur überwacht):** Erlauben Sie Benutzern die Suche nach Büchern im iBooks Store sowie den Kauf gefundener Bücher.
- **Nachrichten-App auf dem Gerät (nur überwacht):** Erlauben Sie die Verwendung der Nachrichten-App zum Senden und Empfangen von Textnachrichten.
- **Podcasts (nur überwacht):** Erlauben Sie die Verwendung der Podcasts-App.
- **Musikdienst (nur überwacht):** Erlauben Sie die Verwendung der Apple Music-App.
- **iTunes Radio-Dienst (nur überwacht):** Erlauben Sie die Verwendung der iTunes Radio-App.
- **Änderungen an den Einstellungen der App „Meine Freunde suchen“ (nur überwacht):** Gestatten Sie Benutzern das Ändern von Einstellungen für die App „Meine Freunde suchen“.
- **Spotlight-Suche gibt Ergebnisse aus dem Internet zurück (nur überwacht):** Erlauben Sie der Spotlight-Suche, eine Verbindung mit dem Internet herzustellen, um weitere Ergebnisse bereitzustellen.

## <a name="restricted-apps"></a>Eingeschränkte Apps

In der Liste der eingeschränkten Apps können Sie eine der folgenden Listen konfigurieren:

- **Unzulässige Apps:** Listet die (nicht von Intune verwalteten) Apps auf, die Benutzer nicht installieren und ausführen dürfen. Benutzer werden nicht daran gehindert, eine verbotene App zu installieren. Wenn sie dies jedoch tun, wird es Ihnen gemeldet.
- **Genehmigte Apps:** Listet die Apps auf, die Benutzer installieren dürfen. Benutzer dürfen keine Apps installieren, die in dieser Liste nicht aufgeführt sind. Apps, die von Intune verwaltet werden, sind automatisch zugelassen. Benutzer werden nicht daran gehindert, eine App zu installieren, die nicht auf der Genehmigungsliste aufgeführt ist. Wenn sie dies jedoch tun, wird es Ihnen gemeldet.

Klicken Sie zum Konfigurieren einer Liste auf **Hinzufügen**. Geben Sie einen Namen Ihrer Wahl sowie die URL zur App im App-Store und optional den Herausgeber der App an.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Angeben der URL zu einer App im Store

Verwenden Sie das folgende Format, um eine App-URL in der App-Liste anzugeben:

Suchen Sie mithilfe einer Suchmaschine die gewünschte App im iTunes App Store, und öffnen Sie die Seite für die App.
Kopieren Sie die URL der Seite, und verwenden Sie diese als URL zur Konfiguration der Liste zulässiger oder unzulässiger Apps oder einer App, die Sie im Kioskmodus ausführen möchten.
Geräteprofile, die Einstellungen für eingeschränkte Apps enthalten, müssen Benutzergruppen zugewiesen werden.

Beispiel: Suchen Sie nach Microsoft Word für iPad. Verwenden Sie die URL https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> Sie können auch iTunes verwenden, um die App zu suchen, und dann den Befehl **Link kopieren**, um die App-URL abzurufen.

### <a name="additional-options"></a>Zusätzliche Optionen

Sie können auch auf **Importieren** klicken, um die Liste mithilfe einer CSV-Datei im Format <*App-URL*>, <*App-Name*>, <*App-Herausgeber*> aufzufüllen. Sie können auch auf **Exportieren** klicken, um eine CSV-Datei mit dem Inhalt der Liste der eingeschränkten Apps im gleichen Format zu erstellen.

## <a name="show-or-hide-apps-supervised-only"></a>Ein- oder Ausblenden von Apps (nur überwacht)

In der Liste „Apps ein- oder ausblenden“ können Sie eine der folgenden Listen konfigurieren (erfordert überwachte Geräte mit iOS 9.3 oder höher).

- **Ausgeblendete Apps:** Geben Sie eine Liste von Apps an, die vor Benutzern verborgen werden. Benutzer können diese Apps weder anzeigen noch starten.
- **Sichtbare Apps:** Geben Sie eine Liste von Apps an, die Benutzer anzeigen und starten können. Es können keine anderen Apps angezeigt oder gestartet werden.

Klicken Sie zum Konfigurieren einer Liste auf **Hinzufügen**. Geben Sie einen Namen Ihrer Wahl sowie die URL zur App im App-Store und optional den Herausgeber der App an.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Angeben der URL zu einer App im Store

Verwenden Sie das folgende Format, um eine App-URL in der App-Liste anzugeben:

Suchen Sie mithilfe einer Suchmaschine die gewünschte App im iTunes App Store, und öffnen Sie die Seite für die App.
Kopieren Sie die URL der Seite, und verwenden Sie diese als URL zur Konfiguration der Liste zulässiger oder unzulässiger Apps oder einer App, die Sie im Kioskmodus ausführen möchten.

Beispiel: Suchen Sie nach Microsoft Word für iPad. Verwenden Sie die URL https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8.

> [!Note]
> Sie können auch die iTunes-Software verwenden, um die App zu suchen, und dann den Befehl **Link kopieren** , um die App-URL abzurufen.

### <a name="additional-options"></a>Zusätzliche Optionen

Sie können auch auf **Importieren** klicken, um die Liste mithilfe einer CSV-Datei im Format <*App-URL*>, <*App-Name*>, <*App-Herausgeber*> aufzufüllen. Sie können auch auf **Exportieren** klicken, um eine CSV-Datei mit dem Inhalt der Liste der ein- und ausgeblendeten Apps im gleichen Format zu erstellen.


## <a name="wireless"></a>Drahtlos
-   **Datenroaming:** Erlauben Sie das Datenroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.
-   **Globales Abrufen im Hintergrund beim Roaming:** Erlauben Sie, dass das Gerät Daten wie E-Mails beim Roaming in einem Mobilfunknetz abruft.
-   **Sprachwahlverfahren:** Erlauben Sie die Verwendung des Features „Sprachwahlverfahren“ auf dem Gerät.
-   **Sprachroaming:** Erlauben Sie das Sprachroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.
-   **Änderungen an den App-Einstellungen zur Verwendung von Datenverbindungen (nur überwacht):** Erlauben Sie Benutzern die Steuerung, welche Apps Mobilfunkdaten verwenden dürfen.
-   **Persönlicher Hotspot:** Verhindern Sie, dass das Gerät als persönlicher Hotspot genutzt wird. Diese Einstellung kann mit einigen Anbietern nicht kompatibel sein.
-   **Verknüpfen von WLAN-Netzwerken nur mithilfe von Konfigurationsprofilen (nur überwacht):** Dem Gerät nur erlauben, eine Verbindung mit WLAN-Netzwerken herzustellen, die mit einem Intune-WLAN-Profil konfiguriert wurden.

- **Mobilfunk-Verwendungsregeln (nur verwaltete Apps):** Definieren Sie die Datentypen, die von verwalteten Apps genutzt werden können, wenn Sie sich in Mobilfunknetzwerken befinden. Es stehen die folgenden Optionen zur Auswahl:
    - **Verwendung von Datenverbindungen blockieren:** Sie können die Verwendung von Datenverbindungen für **alle verwalteten Apps** blockieren oder **bestimmte Apps wählen**.
    - **Verwendung von Datenverbindungen beim Roaming blockieren:** Sie können die Verwendung von Datenverbindungen beim Roaming für **alle verwalteten Apps** blockieren oder **bestimmte Apps wählen**.

## <a name="connected-devices"></a>Verbundene Geräte

-   **AirDrop (nur überwacht):** Lässt die Verwendung von AirDrop zum Austauschen von Inhalten mit Geräten in der Nähe zu.
-   **Apple Watch-Kopplung (nur überwacht):** Erlauben Sie die Gerätekopplung mit einer Apple Watch.
-   **Handgelenkerkennung für gekoppelte Apple Watch:** Wenn diese Funktion aktiviert ist, zeigt die Apple Watch keine Benachrichtigungen an, wenn sie nicht getragen wird.
-   **Bluetooth-Änderung (nur überwacht):** Sperren Sie die Änderung von Bluetooth-Einstellungen auf dem Gerät durch Endbenutzer.
-   **Hostkopplung, um zu steuern, mit welchen Geräten ein iOS-Gerät gekoppelt werden kann (nur überwacht):** Erlauben Sie die Hostkopplung, damit der Administrator steuern kann, mit welchen Geräten ein iOS-Gerät gekoppelt werden kann.
-   **Kopplungskennwort für ausgehende AirPlay-Anforderungen anfordern:** Erfordert ein Kopplungskennwort, wenn der Benutzer AirPlay zum Streamen von Inhalten auf andere Apple-Geräte verwendet.

## <a name="keyboard-and-dictionary"></a>Tastatur und Wörterbuch

-   **Suche nach Wortdefinitionen (nur überwacht):** Aktivieren Sie das iOS-Feature, mit dem Sie ein Wort markieren und dessen Definition nachschlagen können.
-   **Tastaturwortvorschläge (nur überwacht):** Erlauben Sie Tastaturwortvorschläge für Wörter, die der Benutzer möglicherweise verwenden möchte.
-   **Autokorrektur (nur überwacht):** Ermöglicht dem Gerät die automatische Korrektur von falsch geschriebenen Wörter.
-   **Rechtschreibprüfung über Tastatur (nur überwacht):** Erlaubt die Verwendung der Rechtschreibprüfung auf dem Gerät.
-   **Tastenkombinationen (nur überwacht):** Erlaubt die Verwendung von Tastaturkurzbefehlen.
-   **Diktieren (nur überwacht):** Verhindert, dass der Benutzer die Spracheingabe zur Eingabe von Text verwendet.

## <a name="cloud-and-storage"></a>Cloud und Speicher
-   **In iCloud sichern:** Erlauben Sie dem Benutzer, das Gerät in iCloud zu sichern.
-   **Dokumentsynchronisierung in iCloud (nur überwachter Modus):** Erlauben Sie die Dokument- und Schlüssel-/Wertsynchronisierung in Ihrem iCloud-Speicher.
-   **Synchronisierung von Fotostreams in iCloud:** Ermöglicht Benutzern das Aktivieren von **Mein Photo Stream** auf ihrem Gerät, um Fotos mit iCloud zu synchronisieren, damit diese auf allen Geräten des Benutzers verfügbar sind.
-   **Verschlüsselte Sicherung:** Erzwingen Sie die Verschlüsselung von Gerätesicherungen.
-   **iCloud-Fotomediathek:** Bei Festlegung auf **Nein** wird die Verwendung der iCloud-Fotomediathek deaktiviert, die Benutzern das Speichern von Fotos und Videos in der Cloud ermöglicht.   Fotos, die nicht vollständig aus der iCloud-Fotomediathek auf das Gerät heruntergeladen wurden, werden bei Festlegung auf **Nein** vom Gerät entfernt.
-   **Synchronisierung verwalteter Apps mit der Cloud:** Erlauben Sie Apps, die Sie mit Intune verwalten, Daten mit dem iCloud-Konto des Benutzers zu synchronisieren.
-   **Streaming freigegebener Fotos:** Legen Sie diese Einstellung auf **Nein** fest, um die **iCloud-Fotofreigabe** auf dem Gerät zu deaktivieren.
-   **Aktivitätsfortsetzung:** Erlauben Sie dem Benutzer, die Arbeit, die er auf einem iOS-Gerät gestartet hat, auf einem anderen iOS- oder macOS-Gerät fortzusetzen (Übergabe).

## <a name="autonomous-single-app-mode-supervised-only"></a>Modus der autonomen einzelnen App (nur überwacht)

Verwenden Sie diese Einstellungen, um iOS-Geräte zur Ausführung bestimmter Apps im Modus der autonomen einzelnen App zu konfigurieren. Wenn dieser Modus konfiguriert ist und die App ausgeführt wird, wird das Gerät gesperrt, sodass es nur die App ausführen kann. Ein Beispiel hierfür ist, wenn Sie eine App konfigurieren, mit der Benutzer einen Test auf dem Gerät ausführen können. Wenn die Aktionen der App abgeschlossen sind, oder Sie diese Richtlinie entfernen, kehrt das Gerät in seinen normalen Zustand zurück.

### <a name="settings"></a>Einstellung

- **App-Name**: Geben Sie den Namen der App so ein, wie er in der Liste der Apps auf diesem Blatt angezeigt wird.
- **App-Bündel-ID**: Geben Sie die Bündel-ID der App ein. Hilfe finden Sie in diesem Thema unter **Bündel-ID-Referenz für integrierte iOS-Apps**.

Nachdem Sie jeden App-Namen und jede Bündel-ID angegeben haben, wählen Sie **Hinzufügen** zum Anfügen zur Liste.

- **Importieren**: Importieren einer Datei mit kommagetrennten Werten (CSV) mit einer Liste von App-Namen und ihren zugeordneten Bündel-IDs.
- **Exportieren**: Exportieren der von Ihnen konfigurierten App-Namen und zugeordneten Bündel-IDs nach einer Datei mit kommagetrennten Werten (CSV).

## <a name="kiosk-supervised-only"></a>Kiosk (nur überwacht)
-   **App, die im Kioskmodus ausgeführt wird**: Klicken Sie auf **Verwaltete App**, um eine App auszuwählen, die Sie Intune hinzugefügt haben. Klicken Sie alternativ auf **Store-App**, um die URL zu einer App im Store anzugeben, oder auf **Integrierte App**, um die Paket-ID für die integrierte App anzugeben. Weitere Informationen finden Sie unter [Paket-ID-Referenz für integrierte iOS-Apps](device-restrictions-ios.md#bundle-id-reference-for-built-in-ios-apps) und [Angeben der URL zu einer App im Store](device-restrictions-ios.md#how-to-specify-the-url-to-an-app-in-the-store-1).
    -   **Touch-Unterstützung:** Aktivieren oder deaktivieren Sie die Barrierefreiheitseinstellung **Touch-Unterstützung**, die den Benutzer bei der Ausführung von Bildschirmgesten unterstützt, die ihm u.U. Schwierigkeiten bereiten.
    -   **Farben umkehren:** Aktivieren oder deaktivieren Sie die Barrierefreiheitseinstellung „Farben umkehren“, die die Anzeige für Benutzer mit eingeschränkter Sehfähigkeit anpasst.
    -   **Mono-Audio:** Aktivieren oder deaktivieren Sie die Barrierefreiheitseinstellung „Mono-Audio“.
    -   **VoiceOver:** Aktivieren oder deaktivieren Sie die Barrierefreiheitseinstellung **VoiceOver**, die den Text auf dem Gerätedisplay laut vorliest.
    -   **Zoom:** Aktivieren oder deaktiviere Sie die Barrierefreiheitseinstellung **Zoom**, die dem Benutzer das Vergrößern des Inhalts auf dem Gerätedisplay durch Tippen ermöglicht.
    -   **Automatische Sperre:** Aktivieren oder deaktivieren Sie die automatische Sperrung des Geräts.
    -   **Ruftonschalter:** Aktivieren oder deaktivieren Sie die Stummschaltung (Ruftonschalter) am Gerät.
    -   **Bildschirmdrehung:** Aktivieren oder deaktivieren Sie das Ändern der Bildschirmausrichtung, wenn der Benutzer das Gerät dreht.
    -   **Standbytaste:** Aktivieren oder deaktivieren Sie die Standbytaste am Gerät.
    -   **Touch:** Aktivieren oder deaktivieren Sie den Touchscreen des Geräts.
    -   **Lautstärketasten:** Aktivieren oder deaktivieren Sie die Verwendung der Lautstärketasten am Gerät.
    -   **AssistiveTouch-Steuerung:** Aktivieren oder deaktivieren Sie Touch-Unterstützungsanpassungen, mit denen der Benutzer die Touch-Unterstützung individuell verwenden kann.
    -   **Steuerelement zum Umkehren von Farben:** Aktivieren oder deaktivieren Sie Farbumkehr-Anpassungen, mit denen der Benutzer die Funktion zur Farbumkehr individuell verwenden kann.
    -   **Ausgewählten Text sprechen:** Aktivieren oder deaktivieren Sie die Barrierefreiheitseinstellung „Auswahl vorlesen“, mit der der vom Benutzer ausgewählte Text laut vorgelesen werden kann.
    -   **VoiceOver-Steuerelement:** Aktivieren oder deaktivieren Sie VoiceOver-Anpassungen, die dem Benutzer das Anpassen der VoiceOver-Funktion ermöglichen (z.B. wie schnell Bildschirmtext laut vorgelesen wird).
    -   **Zoomsteuerelement:** Aktivieren oder deaktivieren Sie Zoomanpassungen zur individuellen Verwendung der Zoomfunktion.

>[!NOTE]
> Damit Sie ein iOS-Gerät für den Kioskmodus konfigurieren können, müssen Sie das Apple Configurator-Tool oder das Apple-Programm zur Geräteregistrierung verwenden, um das Gerät in den überwachten Modus zu versetzen. Weitere Informationen zum Apple Configurator-Tool finden Sie in der Apple-Dokumentation.
>Wenn die angegebene iOS-App nach der Zuweisung des Profils installiert wird, wird das Gerät erst nach einem Neustart in den Kioskmodus versetzt.

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
| com.apple.MapsMaps          |              | Apple     |
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
-   **Safari (nur überwachter Modus):** Geben Sie an, ob der Safari-Browser auf dem Gerät verwendet werden kann.
-   **AutoAusfüllen:** Erlauben Sie dem Benutzer, die Einstellungen für AutoAusfüllen im Browser zu ändern.
-   **Cookies:** Erlaubt dem Browser die Verwendung von Cookies.
-   **Javascript:** Erlaubt die Ausführung von Java-Skripts im Browser.
-   **Betrugswarnungen:** Erlaubt die Verwendung von Betrugswarnungen im Browser.
-   **Popups:** Aktivieren oder deaktivieren Sie den Popupblocker des Browsers.


## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Nicht markierte E-Mail-Domänen

Fügen Sie im Feld **E-Mail-Domänen-URL** eine oder mehrere URLs der Liste hinzu. Wenn Endbenutzer eine E-Mail von einer anderen Domäne als einer erhalten, die Sie konfiguriert haben, wird die E-Mail in der iOS-Mail-App als nicht vertrauenswürdig gekennzeichnet.


### <a name="managed-web-domains"></a>Verwaltete Webdomänen

Fügen Sie im Feld **Webdomänen-URL** eine oder mehrere URLs der Liste hinzu. Wenn Dokumente von den Domänen heruntergeladen werden, die Sie angeben, gelten sie als verwaltet. Diese Einstellung gilt nur für Dokumente, die mit dem Safari-Browser heruntergeladen werden.


### <a name="safari-password-autofill-domains"></a>Domänen für automatisches Ausfüllen des Safari-Kennworts

Fügen Sie im Feld **Domänen-URL** eine oder mehrere URLs der Liste hinzu. Benutzer können nur Webkennwörter von URLs in dieser Liste speichern. Diese Einstellung gilt nur für den Safari-Browser und Geräte mit iOS 9.3 und höher im überwachten Modus. Wenn Sie keine URLs angeben, können Kennwörter von allen Websites gespeichert werden.
