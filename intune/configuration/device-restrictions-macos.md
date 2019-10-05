---
title: 'macOS-Geräteeinstellungen in Microsoft Intune: Azure | Microsoft-Dokumentation'
titleSuffix: ''
description: Fügen Sie Einstellungen auf macOS-Geräten hinzu, und konfigurieren oder erstellen Sie sie, um Funktionen einzuschränken. Hierzu gehören das Festlegen von Anforderungen für Kennwörter, die Anpassung des Sperrbildschirms, die Verwendung integrierter Apps, das Hinzufügen eingeschränkter oder genehmigter Apps, die Handhabung von Bluetooth-Geräten, das Herstellen einer Verbindung zur Cloud für Sicherung und Speicherung, die Aktivierung des Kioskmodus, das Hinzufügen von Domänen und die Steuerung, wie Benutzer mit dem Safari-Webbrowser in Microsoft Intune interagieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 675f98d952cb243b5aa43e94972b3ef42fbee463
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734816"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>macOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie auf macOS-Geräten steuern können. Verwenden Sie als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) diese Einstellungen, um Features zuzulassen oder zu deaktivieren, Kennwortregeln festzulegen, bestimmte Apps zu erlauben oder einzuschränken usw.

Diese Einstellungen werden einem Gerätekonfigurationsprofil in Intune hinzugefügt und dann Ihren macOS-Geräten zugewiesen oder bereitgestellt.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Konfigurationsprofil mit Geräteeinschränkungen](../device-restrictions-configure.md).

> [!NOTE]
> Diese Einstellungen gelten für verschiedene Registrierungs Typen. Weitere Informationen zu den verschiedenen Registrierungs Typen finden Sie unter [macOS](../macos-enroll.md)-Registrierung.

## <a name="general"></a>Allgemein

### <a name="settings-apply-to-device-enrollment"></a>Einstellungen gelten für: Geräteregistrierung

- **Definitionssuche**: **Blockieren** hindert Benutzer daran, ein Wort zu markieren und dann auf dem Gerät nach seiner Definition zu suchen. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf die Definitionssuchfunktion.
- **Diktat**: **Blockieren** verhindert, dass der Benutzer die Spracheingabe zur Eingabe von Text verwenden kann. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, die Spracheingabe zu verwenden.
- **Content Caching**: Wählen Sie **Nicht konfiguriert** (Standard) aus, um Content Caching zu aktivieren. Bei Zwischenspeicherung von Inhalten werden u.a. App- und Webbrowserdaten und Downloads lokal auf dem Gerät gespeichert. Wählen Sie **Blockieren** aus, um zu verhindern, dass diese Daten im Cache gespeichert werden.

  Weitere Informationen zum Zwischenspeichern von Inhalten unter macOS finden Sie unter [Verwalten des Inhaltscaching auf dem Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (öffnet eine andere Website).

  Diese Funktion gilt für:  
  - macOS 10.13 und höher

- **Softwareupdates zurückstellen**: In der Standardeinstellung **Nicht konfiguriert** werden Softwareupdates auf dem Gerät angezeigt, sobald Apple sie veröffentlicht. Wenn beispielsweise ein macOS-Update von Apple an einem bestimmten Datum veröffentlicht wird, wird dieses Update normalerweise um oder am Veröffentlichungsdatum auf dem Gerät angezeigt. Updates von Seedbuilds sind ohne Verzögerung zulässig.

  **Aktivieren** ermöglicht Ihnen, die Anzeige von Softwareupdates auf Geräten zu verzögern (0-90 Tage). Diese Einstellung steuert nicht, ob Updates installiert werden oder nicht. 

  - **Sichtbarkeit von Softwareupdates verzögern**: Geben Sie einen Wert von 0-90 Tagen ein. Nach der Verzögerung erhalten Benutzer eine Benachrichtigung für ein Update auf die früheste Version des Betriebssystems, die verfügbar war, als die Verzögerung ausgelöst wurde.

    Wenn beispielsweise ein macOS-Update am **1. Januar** verfügbar ist und **Delay visibility** (Sichtbarkeit verzögern) auf **5 Tage** festgelegt ist, wird das Update nicht als verfügbares Update angezeigt. Am **6. Tag** nach Veröffentlichung ist dieses Update verfügbar, sodass Endbenutzer es installieren können.

    Diese Funktion gilt für:  
    - macOS 10.13.4 und höher

- **Screenshots**: das Gerät muss in der automatisierten Geräteregistrierung (DEP) von Apple registriert werden. Wenn " **blockieren**" festgelegt ist, können Benutzer keinen Screenshot der Anzeige speichern. Außerdem wird verhindert, dass die Classroom-App Remote Bildschirme beobachtet. **Nicht konfiguriert** (Standardeinstellung) ermöglicht Benutzern das Erfassen von Screenshots und ermöglicht der Classroom-APP das Anzeigen von Remote Bildschirmen.

### <a name="settings-apply-to-automated-device-enrollment"></a>Einstellungen gelten für: automatisierte Geräteregistrierung

- **Remote Bildschirm Überwachung über die Classroom-App**: **Deaktivieren** hindert Lehrkräfte an der Verwendung der Classroom-APP, um die Bildschirme Ihrer Studenten anzuzeigen. **Nicht konfiguriert** (Standardeinstellung) ermöglicht es Lehrkräften, die Bildschirme Ihrer Schüler und Studenten anzuzeigen.

  Um diese Einstellung zu verwenden, legen Sie die Einstellung **Screenshots** auf **nicht konfiguriert** fest (Screenshots sind zulässig).

- **Nicht Aufforderungs Bildschirm Überwachung durch Classroom-App**: erlauben Sie den Lehrkräften, die Bildschirme Ihrer Studenten anzuzeigen, ohne **dass** der Student zustimmen muss. **Nicht konfiguriert** (Standard) erfordert, dass der Student zustimmt, bevor der Lehrer die Bildschirme sehen kann.

  Um diese Einstellung zu verwenden, legen Sie die Einstellung **Screenshots** auf **nicht konfiguriert** fest (Screenshots sind zulässig).

- **Schüler/Studenten müssen die Berechtigung zum Verlassen der Classroom-Klasse anfordern** **:** erzwingt, dass Schüler/Studenten, die an einem nicht verwalteten Kurs Kurs angemeldet sind, die Genehmigung des Lehr Kurses erhalten **Nicht konfiguriert** (Standardeinstellung): ermöglicht Student, den Kurs zu verlassen, wenn sich der Student entscheidet.

- **Lehrkräfte können Geräte oder apps in der Classroom-App automatisch sperren**: mit **zulassen** können Lehrer das Gerät oder die APP eines Studenten sperren, ohne die Genehmigung des Studenten zu erhalten. **Nicht konfiguriert** (Standard) erfordert, dass der Student zustimmt, bevor der Lehrer das Gerät oder die App Sperren kann.

- **Schüler/Studenten können der Classroom-Klasse automatisch beitreten**: mit " **zulassen** " können Studenten einer Klasse beitreten, ohne den Lehrer aufzufordern **Nicht konfiguriert** (Standard) erfordert die Genehmigung eines Lehrkräfte für den Beitritt zu einer Klasse.

## <a name="password"></a>Kennwort

### <a name="settings-apply-to-device-enrollment"></a>Einstellungen gelten für: Geräteregistrierung

- **Kennwort**: **Anfordern** der Eingabe eines Kennworts durch den Endbenutzer, um auf das Gerät zugreifen zu können. **Nicht konfiguriert** (Standard) erfordert kein Kennwort. Außerdem werden keine Einschränkungen erzwungen, wie z. b. das Blockieren einfacher Kenn Wörter oder das Festlegen einer Mindestlänge.
  - **Erforderlicher Kennworttyp**: Geben Sie an, ob das Kennwort rein numerisch sein darf oder ob es alphanumerisch sein muss (also Buchstaben und Zahlen enthalten muss).

    Diese Funktion gilt für:  
    - macOS 10.10.3 und höher

  - **Anzahl nicht alphanumerischer Zeichen im Kennwort**: Geben Sie die erforderliche Anzahl komplexer Zeichen im Kennwort an (**0** bis **4**).<br>Bei einem komplexen Zeichen handelt es sich um ein Symbol, z.B. **?** .
  - **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl von Zeichen an, die Benutzer für das Kennwort festlegen müssen (zwischen **4** und **16** Zeichen).
  - **Einfache Kennwörter**: Erlauben Sie die Verwendung einfacher Kennwörter wie **0000** oder **1234**.
  - **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts**: Geben Sie an, wie lange der Computer inaktiv sein muss, bevor er mithilfe eines Kennworts entsperrt werden muss.
  - **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung**: Geben Sie die Zeitdauer an, die der Computer inaktiv sein muss, bevor der Bildschirm gesperrt wird.
  - **Kennwortablauf (Tage)** : Geben Sie an, nach wie vielen Tagen der Benutzer das Kennwort ändern muss (**1** bis **255** Tage).
  - **Wiederverwendung vorheriger Kennwörter verhindern**: Geben Sie die Anzahl von vorherigen Kennwörtern an, die nicht erneut verwendet werden dürfen (**1** bis **24**).

- **Ändern des Passcodes durch Benutzer blockieren**: Wählen Sie **Blockieren**, damit der Passcode nicht geändert, hinzugefügt oder entfernt werden kann. **Nicht konfiguriert** (Standard) ermöglicht, Passcodes hinzuzufügen, zu ändern oder zu entfernen.
- **Entsperren per Fingerabdruck blockieren**: Wählen Sie **Blockieren** aus, um die Verwendung eines Fingerabdrucks zum Entsperren des Geräts zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer das Entsperren des Geräts mittels Fingerabdruck.

- **AutoAusfüllen für Kennwörter blockieren**: Wählen Sie **Blockieren**, um die Verwendung der Funktion zum automatischen Ausfüllen von Kennwörtern unter MacOS zu verhindern. Das Wählen von **Blockieren** bewirkt auch Folgendes:

  - Benutzer werden nicht aufgefordert, in Safari oder beliebigen Apps gespeicherte Kennwörter zu verwenden.
  - Automatische sichere Kennwörter sind deaktiviert, und sichere Kennwörter werden Benutzern nicht empfohlen.

  **Nicht konfiguriert** (Standard) lässt diese Funktionen zu.

- **Kennwortanforderungen durch Näherung blockieren**: Wählen Sie **Blockieren** aus, damit das Gerät eines Benutzers keine Kennwörter von in der Nähe befindlichen Geräten anfordert. **Nicht konfiguriert** (Standard) lässt diese Kennwortanforderungen zu.

- **Kennwortfreigabe blockieren**: **Blockieren** verhindert die Freigabe von Kennwörtern zwischen Geräten mit AirDrop. **Nicht konfiguriert** (Standard) ermöglicht die Freigabe von Kennwörtern.

## <a name="built-in-apps"></a>Integrierte Apps

### <a name="settings-apply-to-device-enrollment"></a>Einstellungen gelten für: Geräteregistrierung

- **Block Safari AutoFill** (AutoAusfüllen in Safari blockieren): **Blockieren** deaktiviert AutoAusfüllen in Safari auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, die AutoAusfüllen-Einstellungen im Browser zu ändern.
- **Kamera blockieren**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Kamera des Geräts zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf die Kamera des Geräts.
- **Apple Music blockieren**:  **Blockieren** setzt die Musik-App in den klassischen Modus zurück und deaktiviert den Musikdienst. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der Apple Music-App.
- **Rückgabe von Internetsuchergebnissen in Spotlight blockieren**: **Blockieren** verhindert, dass Spotlight Ergebnisse einer Internetsuche zurückgibt. **Nicht konfiguriert** (Standard) ermöglicht der Spotlight-Suchfunktion das Herstellen einer Verbindung mit dem Internet zur Bereitstellung von Suchergebnissen.
- **Dateiübertragung mit iTunes blockieren**: Bei Wahl von **Blockieren** werden Freigabedienste für Anwendungsdateien deaktiviert. Die Standardeinstellung **Nicht konfiguriert** lässt Freigabedienste für Anwendungsdateien zu.

  Diese Funktion gilt für:  
  - macOS 10.13 und höher

## <a name="restricted-apps"></a>Eingeschränkte Apps

### <a name="settings-apply-to-device-enrollment"></a>Einstellungen gelten für: Geräteregistrierung

- **Typ der Liste der eingeschränkten apps**: Erstellen Sie eine Liste von apps, die Benutzer nicht installieren oder verwenden dürfen. Folgende Optionen sind verfügbar:

  - **Nicht konfiguriert** (Standard): Es gibt keine Einschränkungen von InTune. Benutzer haben Zugriff auf apps, die Sie zuweisen, und integrierte apps.
  - **Unzulässige Apps:** Eine Reihe nicht von Intune verwalteter Apps, die nicht auf dem Gerät installiert werden sollen. Benutzer werden daran gehindert, eine unzulässige APP zu installieren. Wenn jedoch ein Benutzer eine APP aus dieser Liste installiert, wird er in InTune gemeldet.
  - **Genehmigte Apps:** Listet die Apps auf, die Benutzer installieren dürfen. Benutzer dürfen keine Apps installieren, die in dieser Liste nicht aufgeführt sind. Apps, die von Intune verwaltet werden, sind automatisch zugelassen. Benutzer werden nicht daran gehindert, eine App zu installieren, die nicht in der Liste zulässiger Apps enthalten ist. Wenn dies der Fall ist, wird er in InTune gemeldet.
- **App-Bündel-ID:** Geben Sie die [App-Bündel-ID](bundle-ids-built-in-ios-apps.md) der App ein, die Sie hinzufügen möchten. Sie können integrierte apps und branchenspezifische apps anzeigen oder ausblenden. Die Apple-Website enthält eine Liste [integrierter Apple-Apps](https://support.apple.com/HT208094).
- **App-Name:** Geben Sie den Namen der App ein, die Sie hinzufügen möchten. Sie können integrierte apps und branchenspezifische apps anzeigen oder ausblenden. Die Apple-Website enthält eine Liste [integrierter Apple-Apps](https://support.apple.com/HT208094).
- **Herausgeber:** Geben Sie den Namen des Herausgebers der App ein, die Sie hinzufügen möchten.

Um diesen Listen Apps hinzuzufügen, können Sie:

- **Add**: Wählen Sie diese Option aus, um die Liste der apps zu erstellen
- **Importieren** Sie eine CSV-Datei mit den Details der App, einschließlich der URL. Verwenden Sie das Format `<app bundle ID>, <app name>, <app publisher>`. Sie können auch **exportieren** , um eine Liste der von Ihnen hinzugefügten apps im gleichen Format zu erstellen.

## <a name="connected-devices"></a>Verbundene Geräte

### <a name="settings-apply-to-device-enrollment"></a>Einstellungen gelten für: Geräteregistrierung

- **AirDrop blockieren**: **Blockieren** verhindert die Verwendung von AirDrop auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung von AirDrop zum Austauschen von Inhalten mit Geräten in der Nähe.
- **Automatisches Entsperren von Apple Watch blockieren**: **Blockieren** hindert Benutzer daran, ihr macOS-Gerät mit ihrer Apple Watch zu entsperren. Die Standardeinstellung **Nicht konfiguriert** erlaubt Benutzern, ihr macOS-Gerät mit ihrer Apple Watch zu entsperren.

## <a name="cloud-and-storage"></a>Cloud und Speicher

### <a name="settings-apply-to-device-enrollment"></a>Einstellungen gelten für: Geräteregistrierung

- **Synchronisierung zwischen iCloud und Keychain blockieren**: Wählen Sie **Blockieren** aus, um die Synchronisierung in der Keychain gespeicherter Anmeldeinformationen mit iCloud zu deaktivieren. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Anmeldeinformationen zu synchronisieren.
- **iCloud-Synchronisierung von Dokumenten blockieren**: **Blockieren** hindert iCloud daran, Dokumente und Daten zu synchronisieren. **Nicht konfiguriert** (Standard) erlaubt die Dokument- und Schlüssel-/Wertsynchronisierung in Ihrem iCloud-Speicher.
- **iCloud-Sicherung von Mail blockieren**: **Blockieren** hindert iCloud an der Synchronisierung mit der der macOS-App „Mail“. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung der Mail-App mit iCloud zu.
- **iCloud-Sicherung von Kontakten blockieren**: **Blockieren** hindert iCloud an der Synchronisierung der Kontakte auf Geräten. Die Standardeinstellung **Nicht konfiguriert** erlaubt die Kontaktsynchronisierung über iCloud.
- **iCloud-Sicherung von Kalender blockieren**: **Blockieren** hindert iCloud an der Synchronisierung mit der macOS-App „Kalender“. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung der Kalender-App mit iCloud zu.
- **iCloud-Sicherung von Erinnerungen blockieren**: **Blockieren** hindert iCloud an der Synchronisierung mit der macOS-App „Erinnerungen“. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung der Erinnerungen-App mit iCloud zu.
- **iCloud-Sicherung von Lesezeichen blockieren**: **Blockieren** hindert iCloud an der Synchronisierung der Lesezeichen auf Geräten. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung von Lesezeichen mit iCloud zu.
- **iCloud-Sicherung von Notizen blockieren**: **Blockieren** hindert iCloud an der Synchronisierung der Notizen auf Geräten. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung von Notizen mit iCloud zu.
- **Icloud-Fotobibliothek blockieren**: der **Block** deaktiviert die icloud-Fotobibliothek und verhindert, dass icloud die Geräte Fotos synchronisiert. Fotos, die nicht vollständig aus der iCloud-Fotomediathek heruntergeladen wurden, werden aus dem lokalen Speicher des jeweiligen Geräts entfernt. **Nicht konfiguriert** (Standardeinstellung) ermöglicht die Synchronisierung von Fotos zwischen dem Gerät und der icloud-Fotobibliothek.
- **Übergabe**: **nicht konfiguriert** (Standardeinstellung): ermöglicht Benutzern das Starten der Arbeit auf einem macOS-Gerät und das anschließende fortsetzen der Arbeit, die Sie auf einem anderen ios-oder macOS-Gerät gestartet haben. **Block** verhindert die Übergabe Funktion auf dem Gerät. 

  Diese Funktion gilt für:  
  - macOS 10.15 und neuer

## <a name="domains"></a>Domains

### <a name="settings-apply-to-device-enrollment"></a>Einstellungen gelten für: Geräteregistrierung

- **E-Mail-Domänen-URL:** **Fügen** Sie mindestens eine URL zur Liste hinzu. Wenn Benutzer eine E-Mail von einer Domäne erhalten, die Sie nicht konfiguriert haben, wird die E-Mail in der macOS-Mail-App als nicht vertrauenswürdig gekennzeichnet.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](../device-profile-assign.md) und [Überwachen von Profilen](../device-profile-monitor.md)

Sie können auch Gerätefeatures und -einstellungen auf [iOS](../device-restrictions-ios.md)-Geräten einschränken.
