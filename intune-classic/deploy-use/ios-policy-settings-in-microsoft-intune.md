---
title: iOS-Richtlinieneinstellungen
description: Erstellen Sie Richtlinien, die Einstellungen und Funktionen auf iOS-Geräten steuern, die Sie mit Intune verwalten.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9785078341c8e3469067042a3f3e8588f29c3a3b
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ios-policy-settings-in-microsoft-intune"></a>iOS-Richtlinieneinstellungen in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune bietet eine Reihe integrierter allgemeiner Einstellungen, die Sie auf iOS-Geräten konfigurieren können. Darüber hinaus können Sie das Apple Configurator-Tool verwenden, um benutzerdefinierte Einstellungen zu erstellen, die nicht von Intune verfügbar sind.

## <a name="general-configuration-policy-settings"></a>Allgemeine Konfigurationsrichtlinieneinstellungen

Verwenden Sie die allgemeine **iOS-Konfigurationsrichtlinie** von Microsoft Intune zum Konfigurieren von Einstellungen für:

-   **Allgemeine Geräte- und Sicherheitseinstellungen**: Wählen Sie aus einer Liste mit vordefinierten Einstellungen, mit denen Sie verschiedene Features und Funktionen auf dem Gerät steuern können.

-   **Kioskmodus**: Sie können ein Gerät so konfigurieren, dass nur bestimmte Features funktionieren. Beispielsweise können Sie festlegen, dass auf einem Gerät nur eine von Ihnen angegebene verwaltete App ausgeführt werden kann, oder Sie können die Lautstärkeregler eines Geräts deaktivieren. Diese Einstellungen können für ein Demomodell eines Geräts oder ein Gerät verwendet werden, das nur eine bestimmte Funktion ausführen soll, z. B. ein Point-of-Sale-Gerät.

-   **Kompatible und nicht kompatible Apps**: Geben Sie eine Liste von Apps an, die in Ihrem Unternehmen kompatibel oder nicht kompatibel sind. Auf Android- und iOS-Geräten können Sie mit dem **Bericht über nicht kompatible Apps** überprüfen, ob die von Benutzern installierten Apps zu den von Ihnen in der Liste als kompatibel angegebenen Apps gehören (die Installation der App kann jedoch nicht blockiert werden).

> [!TIP]
> Sie können Bestimmungen konfigurieren. Beispielsweise müssen Benutzer zustimmen, dass die auf ihrem Gerät installierten Apps (einschließlich persönlicher Apps) beurteilt werden und dass nicht kompatible Apps entweder blockiert oder als nicht kompatibel gemeldet werden. Benutzer müssen diese Bestimmungen akzeptieren, bevor sie ihr Gerät registrieren und Apps über das Unternehmensportal abrufen können. Weitere Informationen zur Verwendung von Nutzungsbedingungen finden Sie unter [Einstellungen für Nutzungsbedingungsrichtlinien in Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Wenn die gesuchte Einstellung nicht in diesem Thema enthalten ist, können Sie sie ggf. mithilfe einer benutzerdefinierten iOS-Richtlinie erstellen, die Ihnen das Importieren von Einstellungen erlaubt, die Sie mit dem [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12)-Tool erstellt haben. Weitere Informationen finden Sie weiter unten in diesem Thema unter „Benutzerdefinierte Richtlinieneinstellungen“.

### <a name="security-settings"></a>Sicherheitseinstellungen
Alle Einstellungen beziehen sich auf iOS 8.0 und höher.


|                                           Name der Einstellung                                            |                                                            Details                                                             |
|---------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
|                   <strong>Anfordern eines Kennworts zum Entsperren mobiler Geräte</strong>                    |                        Gibt an, ob der Benutzer ein Kennwort eingeben muss, um auf sein Gerät zuzugreifen.                        |
|                              <strong>Erforderlicher Kennworttyp</strong>                              |                   Gibt den erforderlichen Typ des Kennworts an, z. B. nur numerisch oder alphanumerisch.                    |
|                <strong>Erforderliche Anzahl komplexer Zeichen im Kennwort</strong>                 | Gibt die Anzahl von Symbolzeichen (wie <strong>#</strong> oder <strong>@</strong>) an, die im Kennwort enthalten sein müssen. |
|                             <strong>Minimale Kennwortlänge</strong>                              |                                   Gibt die Mindestanzahl von Zeichen an, die das Kennwort enthalten muss.                                    |
|                              <strong>Einfache Kennwörter zulassen</strong>                              |                          Lässt einfache Kennwörter wie <strong>0000</strong> und <strong>1234</strong> zu.                          |
|     <strong>Anzahl zulässiger wiederholter Anmeldefehler, bevor das Gerät zurückgesetzt wird</strong>      |                       Gibt die Anzahl fehlerhafter Anmeldeversuche an, bevor das Gerät durch diese Einstellung zurückgesetzt wird.                        |
|          <strong>Minuten Inaktivität vor Anforderung des Kennworts</strong><sup>1</sup>           |                   Gibt an, wie lange das Gerät im Leerlauf bleiben kann, bevor der Benutzer sein Kennwort erneut eingeben muss.                    |
|                            <strong>Kennwortablauf (Tage)</strong>                            |                             Gibt die Anzahl der Tage an, bevor das Gerätekennwort geändert werden muss.                             |
|                            <strong>Kennwortverlauf speichern</strong>                             |                           Gibt an, ob der Benutzer zuvor verwendete Kennwörter wiederverwenden kann.                           |
| <strong>Kennwortverlauf speichern</strong> – <strong>Wiederverwendung vorheriger Kennwörter verhindern</strong> |                           Gibt an, wie viele zuvor verwendete Kennwörter vom Gerät gespeichert werden.                           |
|            <strong>Minuten Inaktivität bis zur Abschaltung des Bildschirms</strong><sup>1</sup>             |                             Geben Sie die Anzahl der Minuten an, bevor die Anzeige des Geräts deaktiviert wird.                             |
|                             <strong>Fingerabdruckentsperrung zulassen</strong>                             |                                        Lässt das Entsperren des Geräts mittels Fingerabdruck zu.                                         |

<sup>1</sup> Wenn Sie für iOS-Geräte die Einstellungen **Minuten Inaktivität bis zur Abschaltung des Bildschirms** und **Minuten Inaktivität vor Anforderung des Kennworts** konfigurieren, werden diese nacheinander angewendet. Wenn Sie beispielsweise den Wert für beide Einstellungen auf **5** Minuten einstellen, wird der Bildschirm automatisch nach 5 Minuten deaktiviert, und das Gerät wird nach weiteren 5 Minuten gesperrt. Wenn der Benutzer den Bildschirm jedoch manuell deaktiviert, wird die zweite Einstellung sofort angewendet. Im selben Beispiel wird das Gerät 5 Minuten später gesperrt, nachdem der Benutzer den Bildschirm deaktiviert hat.

### <a name="system-settings"></a>Systemeinstellungen
Alle Einstellungen beziehen sich auf iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Bildschirmfoto zulassen**|Ermöglicht es dem Benutzer, den Bildschirminhalt als Bild zu erfassen.|
|**Kontrollcenter auf Sperrbildschirm zulassen**|Erlaubt dem Benutzer den Zugriff auf die Kontrollcenter-App, während das Gerät gesperrt ist.|
|**Benachrichtigungsansicht auf Sperrbildschirm zulassen**|Erlaubt dem Benutzer den Zugriff auf die Benachrichtigungsansicht, ohne dass das Gerät entsperrt werden muss.|
|**Ansicht „Heute“ auf Sperrbildschirm zulassen**|Ermöglicht dem Benutzer das Anzeigen von Benachrichtigungen, während das Gerät gesperrt ist.|
|**Nicht vertrauenswürdige TLS-Zertifikate zulassen**|Hiermit werden nicht vertrauenswürdige TLS-Zertifikate (Transport Layer Security) auf dem Gerät zugelassen.|
|**Übermitteln von Diagnosedaten zulassen**|Ermöglicht dem Gerät das Senden von Diagnosedaten an Apple.|
|**Passbook bei Sperre zulassen**|Erlaubt dem Benutzer den Zugriff auf die Passbook-App, während das Gerät gesperrt ist.|

### <a name="cloud-settings-for-documents-and-data"></a>Cloudeinstellungen für Dokumente und Daten
Alle Einstellungen beziehen sich auf iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Sicherung in iCloud zulassen**|Ermöglicht es dem Benutzer, das Gerät in iCloud zu sichern.|
|**Dokumentsynchronisierung in iCloud zulassen**|Erlaubt die Dokument- und Schlüssel-/Wertsynchronisierung in Ihrem iCloud-Speicher.|
|**Fotostream-Synchronisierung auf iCloud zulassen**|Ermöglicht Benutzern das Aktivieren von **Mein Photo Stream** auf ihrem Gerät, um Fotos mit iCloud zu synchronisieren, damit diese auf allen Geräten des Benutzers verfügbar sind.|
|**Verschlüsselte Sicherung erforderlich**|Fordert an, dass Gerätesicherungen verschlüsselt werden.|
|**Datensynchronisierung mit iCloud durch verwaltete Apps zulassen**|Ermöglicht es Apps, die Sie mit Intune verwalten, Daten mit dem iCloud-Konto des Benutzers zu synchronisieren.|
|**Fortsetzung von Aktivitäten durch Handoff auf einem anderen Gerät zulassen**|Ermöglicht es dem Benutzer, die Arbeit, die er auf einem iOS-Gerät gestartet hat, auf einem anderen iOS- oder Mac OS X-Gerät fortzusetzen.|
|**iCloud-Fotofreigabe zulassen**|Legen Sie diese Einstellung auf **Nein** fest, um die **iCloud-Fotofreigabe** auf dem Gerät zu deaktivieren.|
|**iCloud-Fotomediathek zulassen**|Bei Festlegung auf **Nein** wird die Verwendung der iCloud-Fotomediathek deaktiviert, die Benutzern das Speichern von Fotos und Videos in der Cloud ermöglicht.   Fotos, die nicht vollständig aus der iCloud-Fotomediathek auf das Gerät heruntergeladen wurden, werden bei Festlegung auf **Nein** vom Gerät entfernt.|

### <a name="application-settings-for-the-browser"></a>Anwendungseinstellungen für den Browser
Alle Einstellungen beziehen sich auf iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Safari zulassen**|Geben Sie an, ob der Safari-Browser auf dem Gerät verwendet werden kann.|
|**AutoAusfüllen zulassen**|Ermöglicht es dem Benutzer, die Einstellungen für AutoVervollständigen im Browser zu ändern.|
|**Popupblocker zulassen**|Aktivieren oder deaktivieren Sie den Popupblocker des Browsers.|
|**Cookies zulassen**|Ermöglicht dem Browser die Verwendung von Cookies.|
|**JavaScript zulassen**|Ermöglichen, dass Java-Skripts im Browser ausgeführt werden.|
|**Betrugswarnung zulassen**|Ermöglicht die Verwendung von Betrugswarnungen im Browser.|

### <a name="application-settings-for-apps"></a>Anwendungseinstellungen für Apps
Alle Einstellungen beziehen sich auf iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Installation von Apps zulassen**|Ermöglicht dem Gerät den Zugriff auf den App Store und die Installation von Apps.|
|**Kennwort für den Zugriff auf den Anwendungsspeicher erforderlich**|Erzwingt die Kennworteingabe vom Benutzer, bevor er den App Store besuchen kann.|
|**In-App-Einkäufe zulassen**|Zulassen, dass Einkäufe im Store in einer ausgeführten App erfolgen.|
|**Verwaltete Dokumente in anderen nicht verwalteten Apps zulassen**|Hiermit wird die Anzeige von Unternehmensdokumenten in beliebigen Apps zugelassen.<br>**Beispiel:** Sie möchten verhindern, dass Benutzer Dateien aus der OneDrive-App in Dropbox speichern. Legen Sie für diese Einstellung „Nein“ fest. Sobald das Gerät die Richtlinie empfängt (z. B. nach einem Neustart), ist kein Speichern mehr möglich.|
|**Nicht verwaltete Dokumente in anderen verwalteten Apps zulassen**|Hiermit wird die Anzeige beliebiger Dokumente in verwalteten Apps zugelassen.|
|**Videokonferenz zulassen**|Lässt Videokonferenz-Apps wie FaceTime auf dem Gerät zu.|
|**Benutzern das Einstufen von Autoren neuer Unternehmens-Apps als vertrauenswürdig gestatten**|Ermöglicht es dem Benutzer zu entscheiden, ob Apps, die nicht aus dem App Store heruntergeladen wurden, vertraut werden soll.|


### <a name="application-settings-for-games"></a>Anwendungseinstellungen für Spiele
Alle Einstellungen beziehen sich auf iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Hinzufügung von Game Center-Freunden zulassen**|Ermöglichen, dass der Benutzer im Game Center Freunde hinzufügt.|
|**Spielen für mehrere Spieler zulassen**|Ermöglichen, dass der Benutzer Spiele für mehrere Spieler auf dem Gerät spielt.|

### <a name="application-settings-for-media-content"></a>Anwendungseinstellungen für Medieninhalte
Alle Einstellungen beziehen sich auf iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Bewertungsregion**|Wählen Sie eine Region aus, und wählen Sie die maximale Bewertung aus, die Benutzer für **Filme**, **Fernsehsendungen** und **Apps** herunterladen können.|
|**Nicht jugendfreie Inhalte im Medienstore zulassen**|Zulassen, dass das Gerät im Store auf nicht jugendfreie Inhalte zugreift.|
|**Benutzern das Herunterladen von iBooks Store-Inhalt mit der Kennzeichnung „Erotik“ gestatten**|Gestattet dem Benutzer das Herunterladen von Büchern aus der Kategorie „Erotik“.|


### <a name="device-capabilities-settings-for-hardware"></a>Einstellungen für Gerätefunktionen der Hardware
Alle Einstellungen beziehen sich auf iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Kamera zulassen**|Gibt an, ob die Kamera des Geräts verwendet werden darf.|
|**Handgelenkerkennung für gekoppelte Apple Watch-Geräte erzwingen**|Wenn diese Funktion aktiviert ist, zeigt die Apple Watch keine Benachrichtigungen an, wenn sie nicht getragen wird.|
|**Kopplungskennwort für ausgehende AirPlay-Anforderungen erforderlich**|Erfordert ein Kopplungskennwort, wenn der Benutzer AirPlay zum Streamen von Inhalten auf andere Apple-Geräte verwendet.|

### <a name="device-capabilities-settings-for-cellular"></a>Einstellungen für Gerätefunktionen von Mobiltelefonen
Alle Einstellungen beziehen sich auf iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Sprachroaming zulassen**|Zulassen des Sprachroamings, wenn das Gerät in einem Mobilfunknetz verwendet wird.|
|**Datenroaming zulassen**|Zulassen des Datenroamings, wenn das Gerät in einem Mobilfunknetz verwendet wird.|
|**Globales Abrufen im Hintergrund beim Roaming zulassen**|Zulassen, dass das Gerät Daten wie E-Mails beim Roaming in einem Mobilfunknetz abruft.|

### <a name="device-capabilities-settings-for-features"></a>Einstellungen für Gerätefunktionen von Features
Alle Einstellungen beziehen sich auf iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|-------|
|**Siri zulassen**|Verwendung des Sprach-Assistenten Siri auf dem Gerät zulassen.|
|**Siri bei gesperrtem Gerät zulassen**|Verwendung des Sprach-Assistenten Siri auf dem Gerät zulassen, während das Gerät gesperrt ist.|
|**Sprachwahl zulassen**|Die Verwendung des Features „Sprachwahlverfahren“ auf dem Gerät erlauben.|
|**Airdrop für verwaltete Apps nicht zulassen**|Verwaltete Apps am Senden von Daten mit Airdrop hindern.|


### <a name="settings-for-compliant-and-noncompliant-apps"></a>Einstellungen für kompatible und nicht kompatible Anwendungen
Geben Sie in der Liste der **kompatiblen und nicht kompatiblen Apps** anhand der folgenden Informationen eine Liste kompatibler oder nicht kompatibler Apps an.

> [!NOTE]
> Eine einzelne Richtlinie kann nur eine Liste kompatibler Apps oder eine Liste nicht kompatibler Apps enthalten. Sie können nicht beide Typen in derselben Richtlinie angeben.

|Name der Einstellung|Details|
|----------------|--------------------|
|**Nichtkompatibilität melden, wenn Benutzer die aufgelisteten Apps installieren**|Listet die (nicht von Intune verwalteten) Apps auf, die Benutzer nicht installieren und ausführen dürfen.|
|**Nichtkonformität melden, wenn Benutzer die nicht aufgelisteten Apps installieren**|Listet die Apps auf, die Benutzer installieren dürfen. Um die Kompatibilität zu gewährleisten, dürfen Benutzer keine Apps installieren, die in dieser Liste nicht aufgeführt sind. Apps, die von Intune verwaltet werden, sind automatisch zugelassen.|
|**Hinzufügen**|Fügt der ausgewählten Liste eine App hinzu. Geben Sie einen Namen Ihrer Wahl sowie die URL zur App im App-Store und optional den Herausgeber der App an. Weitere Informationen finden Sie unter „Angeben von URLs zu App-Stores“ weiter unten in diesem Thema.|
|**Anwendungen importieren**|Importiert eine Liste von Apps, die Sie in einer durch Trennzeichen getrennten Datei angegeben haben. Verwenden Sie in der Datei das Format Anwendungsname, Herausgeber, App-URL.|
|**Bearbeiten**|Ermöglicht das Bearbeiten des Namens, Herausgebers und der URL der ausgewählten App.|
|**Löschen**|Löscht die ausgewählte App aus der Liste.|

Richtlinien mit kompatiblen und nicht kompatiblen App-Einstellungen müssen für Benutzergruppen bereitgestellt werden.

### <a name="kiosk-mode-settings"></a>Einstellungen für den Kioskmodus

|                                            Name der Einstellung                                            |                                                                                                                                      Details                                                                                                                                       |
|----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>Wählen Sie eine verwalteten App aus, die ausgeführt werden darf, während sich das Gerät im Kiosk-Modus befindet</strong> | Wählen Sie <strong>Durchsuchen</strong> aus, und geben Sie dann die verwaltete App oder eine App aus einem Store an, die ausgeführt werden darf, wenn sich das Gerät im Kioskmodus befindet. Andere Apps dürfen auf dem Gerät nicht ausgeführt werden. Weitere Informationen finden Sie unter „Angeben von URLs zu App-Stores“ weiter unten in diesem Thema. |
|                                    <strong>Toucheingabe zulassen</strong>                                    |                                                                                                                  Aktiviert oder deaktiviert den Touchscreen des Geräts.                                                                                                                  |
|                               <strong>Bildschirmdrehung zulassen</strong>                               |                                                                                                Aktiviert oder deaktiviert das Ändern der Bildschirmausrichtung, wenn der Benutzer das Gerät dreht.                                                                                                 |
|                               <strong>Lautstärkeregler zulassen</strong>                                |                                                                                                           Aktiviert oder deaktiviert die Verwendung der Lautstärkeregler am Gerät.                                                                                                           |
|                                <strong>Ruftonschalter zulassen</strong>                                |                                                                                                             Aktiviert oder deaktiviert den Ruftonschalter (Stummschaltung) am Gerät.                                                                                                              |
|                          <strong>Schaltfläche für Standby und Aktivieren zulassen</strong>                           |                                                                                                           Aktiviert oder deaktiviert die Schaltfläche für das Standby/die Aktivierung des Bildschirms am Gerät.                                                                                                            |
|                                  <strong>Automatische Sperrung zulassen</strong>                                  |                                                                                                                 Aktiviert oder deaktiviert die automatische Sperrung des Geräts.                                                                                                                 |
|                                 <strong>Mono/Audio aktivieren</strong>                                 |                                                                                                      Aktiviert oder deaktiviert die Barrierefreiheitseinstellung <strong>Mono/Audio</strong>.                                                                                                      |
|                                 <strong>Voice-over aktivieren</strong>                                 |                                                                               Aktiviert oder deaktiviert die Barrierefreiheitseinstellung <strong>VoiceOver</strong>, die den Text auf dem Gerätedisplay laut vorliest.                                                                                |
|                           <strong>Voice-over-Anpassungen aktivieren</strong>                           |                                                                  Aktiviert oder deaktiviert Voice-over-Anpassungen, die dem Benutzer das Anpassen der VoiceOver-Funktion ermöglichen (z. B. wie schnell Bildschirmtext laut vorgelesen wird).                                                                   |
|                                    <strong>Zoom aktivieren</strong>                                    |                                                                         Aktiviert oder deaktiviert die Barrierefreiheitseinstellung <strong>Zoom</strong>, die dem Benutzer das Vergrößern des Inhalts auf dem Gerätedisplay durch Tippen ermöglicht.                                                                         |
|                              <strong>Zoom-Anpassungen aktivieren</strong>                              |                                                                                                  Aktiviert oder deaktiviert Zoom-Anpassungen zur individuellen Verwendung der Zoomfunktion.                                                                                                  |
|                               <strong>Farben umkehren zulassen</strong>                                |                                                                    Aktiviert oder deaktiviert die Barrierefreiheitseinstellung <strong>Farben umkehren</strong>, die die Anzeige für Benutzer mit eingeschränkter Sehfähigkeit anpasst.                                                                    |
|                         <strong>Farbumkehr-Anpassungen aktivieren</strong>                          |                                                                                         Aktiviert oder deaktiviert Farbumkehr-Anpassungen, mit denen der Benutzer die Funktion zur Farbumkehr individuell verwenden kann.                                                                                         |
|                              <strong>Touch-Unterstützung aktivieren</strong>                               |                                                     Aktiviert oder deaktiviert die Barrierefreiheitseinstellung <strong>Touch-Unterstützung</strong>, die den Benutzer bei der Ausführung von Bildschirmgesten unterstützt, die ihm u. U. Schwierigkeiten bereiten.                                                     |
|                        <strong>Touch-Unterstützungsanpassungen aktivieren</strong>                         |                                                                                       Aktiviert oder deaktiviert Touch-Unterstützungsanpassungen, mit denen der Benutzer die Touch-Unterstützung individuell verwenden kann.                                                                                       |
|                              <strong>Sprachauswahl aktivieren</strong>                              |                                                                        Aktiviert oder deaktiviert die Barrierefreiheitseinstellung <strong>Auswahl vorlesen</strong>, mit der der vom Benutzer ausgewählte Text laut vorgelesen werden kann.                                                                         |

> [!NOTE]
> Die folgenden Hinweise gelten für Kiosk-Moduseinstellungen für iOS-Geräte:
>
> -   Damit Sie ein iOS-Gerät für den Kioskmodus konfigurieren können, müssen Sie das [Apple Configurator-Tool](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) oder das [Apple-Programm zur Geräteregistrierung](ios-device-enrollment-program-in-microsoft-intune.md) verwenden, um das Gerät in den überwachten Modus zu versetzen. Weitere Informationen zum Apple Configurator-Tool finden Sie in der Apple-Dokumentation.
> -   Wenn die angegebene iOS-App nach der Bereitstellung der Konfigurationsrichtlinie installiert wird, wird das Gerät erst nach einem Neustart in den Kioskmodus versetzt.

### <a name="reference-information-for-compliant-and-noncompliant-apps"></a>Referenzinformationen für konforme und nicht konforme Apps

Im **Bericht über nicht kompatible Apps** können Sie sich über die Konformität zulässiger und blockierter Anwendungen informieren.

##### <a name="to-run-the-noncompliant-apps-report"></a>So führen Sie den Bericht über nicht kompatible Apps aus

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Optionen **Berichte** &gt; **Bericht über nicht kompatible Apps**.

2.  Wählen Sie die Gerätegruppen aus, die Sie überprüfen möchten, geben Sie an, ob Sie nach kompatiblen und/oder nicht kompatiblen Apps suchen möchten, und wählen Sie dann **Bericht anzeigen** aus.

#### <a name="how-to-specify-urls-to-app-stores"></a>Angeben von URLs zu App-Stores
Um eine App-URL in der Liste mit kompatiblen und nicht kompatiblen Apps oder in der Option **Verwaltete App auswählen, die ausgeführt werden darf, wenn sich das Gerät im Kioskmodus befindet (nur iOS)** anzugeben, verwenden Sie das folgende Format:

1. Suchen Sie mithilfe einer Suchmaschine die gewünschte App im iTunes App Store, und öffnen Sie die Seite für die App.

2. Kopieren Sie die URL der Seite, und verwenden Sie diese als URL zur Konfiguration der Liste kompatibler oder nicht kompatibler Apps oder der App, die Sie im Kioskmodus ausführen möchten.

**Beispiel:** Suchen Sie nach **Microsoft Word für iPad**. Verwenden Sie die URL **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> Sie können auch die iTunes-Software verwenden, um die App zu suchen, und dann den Befehl **Link kopieren** , um die App-URL abzurufen.

### <a name="enrollment-settings"></a>Registrierungseinstellungen
Alle Einstellungen beziehen sich auf iOS 8.0 und höher.

|Name der Einstellung|Details|
|----------------|--------------------|
|**Aktivierungssperre zulassen, wenn sich das Gerät im überwachten Modus befindet**|Aktiviert die Aktivierungssperre auf überwachten iOS-Geräten.|

### <a name="supervised-mode-settings"></a>Einstellungen für den überwachten Modus
Die folgenden Einstellungen können auf Geräten mit iOS 8.0 und höher konfiguriert werden, die sich im überwachten Modus befinden.

### <a name="supervised-mode-settings-for-device-restrictions"></a>Einstellungen für den überwachten Modus für Gerätebeschränkungen

|Name der Einstellung|Details|
|----------------|--------------------|
|**Kontoänderung zulassen**|Benutzern die Änderung der Kontoeinstellungen zulassen, z. B. der E-Mail-Konfigurationen.|
|**Änderungen an Mobilfunk-Datennutzungseinstellungen für Apps zulassen**|Gestatten Sie Benutzern die Steuerung, welche Apps Mobilfunkdaten verwenden dürfen.|
|**Verwendung der Option zum Löschen aller Inhalte und Einstellungen auf dem Gerät zulassen**|Erlaubt dem Benutzer die Verwendung der Option zum Löschen aller Inhalte und Einstellungen auf dem Gerät.|
|**Aktivierung von Einschränkungen in den Geräteeinstellungen durch den Benutzer zulassen**|Erlaubt dem Benutzer das Konfigurieren von Geräteeinschränkungen (Jugendschutz) auf dem Gerät.|
|**Steuerung der Geräte, mit denen ein iOS-Gerät gekoppelt werden kann, durch Hostkopplung zulassen**|Ermöglicht die Hostkopplung, damit der Administrator steuern kann, mit welchen Geräten ein iOS-Gerät gekoppelt werden kann.|
|**Installation von Konfigurationsprofilen und Zertifikaten durch den Benutzer zulassen**|Ermöglicht dem Benutzer die Installation von Konfigurationsprofilen und Zertifikaten.|
|**Änderung von Gerätenamen zulassen**|Ermöglicht es dem Benutzer, den Namen des Geräts zu ändern.|
|**Änderung von Kennungen zulassen**|Ermöglicht das Hinzufügen, Ändern oder Entfernen des Gerätekennworts.|
|**Apple Watch-Kopplung zulassen**|Ermöglicht die Gerätekopplung mit einer Apple Watch.|
|**Änderung der Benachrichtigungseinstellungen zulassen**|Ermöglicht es dem Benutzer, die Benachrichtigungseinstellungen des Geräts zu ändern.|
|**Änderung von Hintergrundbildern zulassen**|Ermöglicht es dem Benutzer, das Hintergrundbild auf dem Gerät zu ändern.|

### <a name="supervised-mode-settings-for-feature-restrictions"></a>Einstellungen für den überwachten Modus für Funktionsbeschränkungen

|Name der Einstellung|Details|
|----------------|--------------------|
|**AirDrop zulassen**|Lässt die Verwendung von AirDrop zum Austauschen von Inhalten mit Geräten in der Nähe zu.|
|**Abfrage von benutzergeneriertem Inhalt aus dem Internet durch Siri zulassen**|Erlaubt Siri den Zugriff auf Websites, um Fragen zu beantworten.|
|**Siri-Filter für anstößige Ausdrücke verwenden**|Verhindert, dass Siri anstößige Ausdrücke diktiert oder verwendet.|
|**Zurückgeben von Ergebnissen aus dem Internet über die Spotlight-Suche zulassen**|Erlaubt der Spotlight-Suche, eine Verbindung mit dem Internet herzustellen, um weitere Ergebnisse bereitzustellen.|
|**Suche nach Wortdefinitionen zulassen**|Aktiviert die iOS-Funktion, mit der Sie ein Wort markieren und dessen Definition nachschlagen können.|
|**Tastaturwortvorschläge zulassen**|Ermöglicht Tastaturwortvorschläge, die Wörter vorschlagen, die der Benutzer möglicherweise verwenden möchte.|
|**Autokorrektur zulassen**|Ermöglicht dem Gerät die automatische Korrektur von falsch geschriebenen Wörter.|
|**Rechtschreibprüfung über Tastatur zulassen**|Aktiviert die Rechtschreibprüfung des Geräts.|
|**Tastaturkurzbefehle zulassen**|Ermöglicht die Verwendung von Tastaturkurzbefehlen.|

### <a name="supervised-mode-settings-for-app-restrictions"></a>Einstellungen für den überwachten Modus für App-Beschränkungen

|Name der Einstellung|Details|
|----------------|--------------------|
|**Änderung von Vertrauensstellungseinstellungen für Unternehmens-Apps zulassen**|Ermöglicht Benutzern das Ändern der Vertrauensstellungseinstellungen für Unternehmens-Apps.|
|**Installation von Apps nur mit Apple Configurator und iTunes zulassen**|Aktiviert oder deaktiviert den App Store auf dem Startbildschirm des Geräts. Benutzer können weiterhin iTunes oder das Apple Configurator-Tool zum Installieren und Aktualisieren von Apps verwenden.|
|**Automatische App-Downloads zulassen**|Den automatischen Download von auf anderen Geräten erworbenen Apps auf dieses Gerät erlauben. Diese Einstellung wirkt sich nicht auf App-Updates aus.|
|**Änderungen an den Einstellungen der App „Meine Freunde suchen“ zulassen**|Gestatten Sie Benutzern das Ändern von Einstellungen für die App „Meine Freunde suchen“.|
|**Zugriff auf iBooks Store zulassen**|Gestatten Sie Benutzern die Suche nach Büchern im iBooks-Store sowie den Kauf gefundener Bücher.|
|**Verwendung der Nachrichten-App auf dem Gerät zulassen**|Gestatten Sie die Verwendung der Nachrichten-App zum Senden von SMS.|
|**Verwendung von Podcasts zulassen**|Ermöglicht die Verwendung Podcast-App.|
|**Verwendung des Music-Diensts zulassen**|Ermöglicht die Verwendung der Apple Music-App.|
|**iTunes Radio-Dienst zulassen**|Ermöglicht die Verwendung der iTunes Radio-App.|
|**Apple News zulassen**|Ermöglicht die Verwendung der Apple News-App.|
|**Game Center zulassen**|Gestatten Sie die Verwendung der Game Center-App.|


### <a name="show-or-hide-apps"></a>Einblenden oder Ausblenden von Apps

Verwenden Sie die **Liste von aus- und eingeblendeten Apps**, um auf überwachten Geräten mit iOS 9.3 oder höher Folgendes zu steuern:

- Angeben einer Liste von Apps, die vor Benutzern verborgen werden. Benutzer können diese Apps weder anzeigen noch starten.
- Angeben einer Liste von Apps, die Benutzer anzeigen und starten können. Es können keine anderen Apps angezeigt oder gestartet werden.


#### <a name="how-to-create-a-hidden-or-shown-app-list"></a>So erstellen Sie eine Liste von aus- oder eingeblendeten Apps

Geben Sie die folgenden Einstellungen an:

|Name der Einstellung|Details|
|-|-|
|**Liste von aus- und eingeblendeten Apps**|Aktivieren Sie diese Einstellung, wenn Sie eine Liste von aus- oder eingeblendeten Apps erstellen möchten.|
|**Ausblenden der aufgelisteten Apps vor Benutzern**|Wählen Sie diese Option aus, wenn Sie eine Liste von Apps erstellen möchten, die vor Benutzern ausgeblendet werden.<br>Beim Erstellen dieses Listentyps können alle Apps mit Ausnahme der iOS-Apps **Einstellungen** und **Telefon** (für iPhones) ausgeblendet werden.|
|**Einblenden ausschließlich der aufgelisteten Apps für Benutzer**|Wählen Sie diese Option aus, wenn Sie eine Liste von Apps erstellen möchten, die Benutzern angezeigt werden.<br>Beim Erstellen dieses Listentyps werden alle anderen Apps mit Ausnahme der iOS-**Einstellungen** und **Telefon**-Apps (für iPhones) ausgeblendet.<br>Sie müssen der Liste darüber hinaus das Unternehmensportal und alle Apps hinzufügen, die Sie bereitgestellt haben und über Intune verwalten.|
|**Hinzufügen**|Fügt eine App zur ausgewählten Liste hinzu.<br>Für die Liste von ausgeblendeten Apps müssen Sie den **Namen**, den **Herausgeber** und die **App-URL oder Paket-ID** jeder App angeben, die Sie ausblenden möchten.<br>Für die Liste von eingeblendeten Apps können Sie entweder **eine verwaltete App auswählen**, wodurch Ihnen eine Liste von Apps zum Auswählen angezeigt wird, die Sie über Intune verwalten. Alternativ können Sie eine Store-App auswählen, wobei Sie den **Namen**, den **Herausgeber** und die **App-URL oder Paket-ID** jeder App angeben müssen, die Sie anzeigen möchten.|
|**Anwendungen importieren**|Importiert eine Liste von Apps, die Sie in einer CSV-Datei angegeben haben. Verwenden Sie in der Datei das Format Anwendungsname, Herausgeber und App-URL.|
|**Bearbeiten**|Ermöglicht Ihnen das Bearbeiten von Name, Herausgeber und URL der ausgewählten App.|
|**Löschen**|Löscht die ausgewählte App aus der Liste.|

#### <a name="app-information-for-built-in-ios-apps"></a>App-Informationen für integrierte iOS-Apps

Verwenden Sie die Informationen in dieser Liste zur Identifizierung des Namens, des Herausgebers und der Paket-ID der integrierten iOS-Apps, die Sie ein- oder ausblenden möchten. Wenn Sie alle Apps in der Liste ein- oder ausblenden möchten, können Sie die nachstehenden Daten in eine Textdatei mit der Erweiterung **.csv** kopieren. Verwenden Sie anschließend die Option **Anwendungen importieren**, um alle Apps gleichzeitig zu importieren.

```
,com.apple.AppStore,App Store,Apple
,com.apple.calculator,Calculator,Apple
,com.apple.mobilecal,Calendar,Apple
,com.apple.camera,Camera,Apple
,com.apple.mobiletimer,Clock,Apple
,com.apple.compass,Compass,Apple
,com.apple.MobileAddressBook,Contacts,Apple
,com.apple.facetime,FaceTime,Apple
,com.apple.mobileme.fmf1,Find Friends,Apple
,com.apple.mobileme.fmip1,Find iPhone,Apple
,com.apple.gamecenter,Game Center,Apple
,com.apple.mobilegarageband,GarageBand,Apple
,com.apple.Health,Health,Apple
,com.apple.iBooks,iBooks,Apple
,com.apple.MobileStore,iTunes Store,Apple
,com.apple.itunesu,iTunes U,Apple
,com.apple.Keynote,Keynote,Apple
,com.apple.mobilemail,Mail,Apple
,com.apple.MapsMaps,Apple
,com.apple.MobileSMS,Messages,Apple
,com.apple.Music,Music,Apple
,com.apple.news,News,Apple
,com.apple.mobilenotes,Notes,Apple
,com.apple.Numbers,Numbers,Apple
,com.apple.Pages,Pages,Apple
,com.apple.Photo-Booth,Photo Booth,Apple
,com.apple.mobileslideshow,Photos,Apple
,com.apple.podcasts,Podcasts,Apple
,com.apple.reminders,Reminders,Apple
,com.apple.MobileSafari,Safari,Apple
,com.apple.Preferences,Settings,Apple
,com.apple.stocks,Stocks,Apple
,com.apple.tips,Tips,Apple
,com.apple.videos,Videos,Apple
,com.apple.VoiceMemos,VoiceMemos,Apple
,com.apple.Passbook,Wallet,Apple
,com.apple.Bridge,Watch,Apple
,com.apple.weather,Weather,Apple
```




## <a name="custom-policy-settings"></a>Benutzerdefinierte Richtlinieneinstellungen

Verwenden Sie die **benutzerdefinierte iOS-Richtlinie** von Microsoft Intune, um Einstellungen, die Sie mit dem [Apple Configurator-Tool](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) erstellt haben, auf iOS-Geräten bereitzustellen. Mit diesem Tool können Sie zahlreiche Einstellungen zur Betriebssteuerung dieser Geräte erstellen und in ein Konfigurationsprofil exportieren. Sie können dieses Konfigurationsprofil anschließend in eine benutzerdefinierte iOS-Richtlinie von Intune importieren und die Einstellungen für Benutzer und Geräte in Ihrer Organisation bereitstellen.

Diese Funktion ermöglicht die Bereitstellung von iOS-Einstellungen, die nicht mit allgemeinen Intune-Konfigurationsrichtlinien konfigurierbar sind.

### <a name="prerequisites"></a>Voraussetzungen
Bevor Sie beginnen, müssen Sie Apple Configurator installiert und eine Konfigurationsdatei mit den Einstellungen erstellt haben, die Sie für Benutzer oder Geräte bereitstellen möchten. Um Apple Configurator herunterzuladen und mehr darüber zu erfahren, besuchen Sie den [Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12).

> [!NOTE]
> Intune meldet nicht die Konformität der einzelnen Einstellungen einer benutzerdefinierten iOS-Richtlinie. Die Gesamtkompatibilität der Richtlinie wird jedoch angegeben.

### <a name="general-settings"></a>Allgemeine Einstellungen

|Name der Einstellung|Details|
    |----------------|--------------------|
    |**Name**|Geben Sie einen eindeutigen Namen für die benutzerdefinierte iOS-Richtlinie ein, damit Sie sie leichter in der Intune-Konsole bestimmen können.|
    |**Beschreibung**|Geben Sie eine Beschreibung ein, die einen Überblick über die benutzerdefinierte iOS-Richtlinie bietet, sowie weitere relevante Informationen, mit denen Sie danach suchen können.|

### <a name="custom-settings"></a>Benutzerdefinierte Einstellungen

|Name der Einstellung|Details|
    |----------------|--------------------|
|**Name des benutzerdefinierten Konfigurationsprofils (wird Benutzern angezeigt)**|Geben Sie einen Namen für die Richtlinie an, der auf dem Gerät und in Intune-Richtlinienberichten angezeigt wird.|
|**Konfigurationsprofildatei**|Wählen Sie **Importieren** aus, und suchen Sie dann das mit Apple Configurator erstellte Konfigurationsprofil. **Hinweis:** Stellen Sie sicher, dass die Einstellungen, die Sie aus dem Apple Configurator-Tool exportieren, mit der iOS-Version auf den Geräten kompatibel sind, für die Sie die benutzerdefinierte iOS-Richtlinie bereitstellen. Um Informationen zum Korrigieren inkompatibler Einstellungen zu erhalten, suchen Sie auf der [Apple Developer-Website](https://developer.apple.com/) nach der **Referenz zu Konfigurationsprofilen** und der **Referenz zum Protokoll für die Verwaltung mobiler Geräte**.|
    |**Details zum Konfigurationsprofil**|Zeigt den XML-Code des importierten Konfigurationsprofils an.|

### <a name="see-also"></a>Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
