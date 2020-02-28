---
title: 'macOS-Geräteeinstellungen in Microsoft Intune: Azure | Microsoft-Dokumentation'
titleSuffix: ''
description: Fügen Sie Einstellungen auf macOS-Geräten hinzu, und konfigurieren oder erstellen Sie sie, um Funktionen einzuschränken. Hierzu gehören das Festlegen von Anforderungen für Kennwörter, die Anpassung des Sperrbildschirms, die Verwendung integrierter Apps, das Hinzufügen eingeschränkter oder genehmigter Apps, die Handhabung von Bluetooth-Geräten, das Herstellen einer Verbindung zur Cloud für Sicherung und Speicherung, die Aktivierung des Kioskmodus, das Hinzufügen von Domänen und die Steuerung, wie Benutzer mit dem Safari-Webbrowser in Microsoft Intune interagieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3d26c4c6cd05a411555f7824ad21b72431eb569c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511171"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>macOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune



In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie auf macOS-Geräten steuern können. Verwenden Sie als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) diese Einstellungen, um Features zuzulassen oder zu deaktivieren, Kennwortregeln festzulegen, bestimmte Apps zu erlauben oder einzuschränken usw.

Diese Einstellungen werden einem Gerätekonfigurationsprofil in Intune hinzugefügt und dann Ihren macOS-Geräten zugewiesen oder bereitgestellt.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Konfigurationsprofil mit Geräteeinschränkungen](../device-restrictions-configure.md).

> [!NOTE]
> Diese Einstellungen gelten für verschiedene Registrierungstypen. Weitere Informationen zu den verschiedenen Registrierungstypen finden Sie unter [macOS-Registrierung](../macos-enroll.md).

## <a name="general"></a>Allgemein

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Die Einstellungen gelten für: Geräteregistrierung und Automatische Geräteregistrierung

- **Definitionssuche**: **Blockieren** hindert Benutzer daran, ein Wort zu markieren und dann auf dem Gerät nach seiner Definition zu suchen. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf die Definitionssuchfunktion.
- **Dictation**: **Blockieren** verhindert, dass der Benutzer die Spracheingabe zur Eingabe von Text verwenden kann. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, die Spracheingabe zu verwenden.
- **Inhalte zwischenspeichern**: Wählen Sie **Nicht konfiguriert** (Standard) aus, um Content Caching zu aktivieren. Bei Zwischenspeicherung von Inhalten werden u.a. App- und Webbrowserdaten und Downloads lokal auf dem Gerät gespeichert. Wählen Sie **Blockieren** aus, um zu verhindern, dass diese Daten im Cache gespeichert werden.

  Weitere Informationen zum Zwischenspeichern von Inhalten unter macOS finden Sie unter [Verwalten des Inhaltscaching auf dem Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (öffnet eine andere Website).

  Diese Funktion gilt für:  
  - macOS 10.13 und höher

- **Softwareupdates zurückstellen**: In der Standardeinstellung **Nicht konfiguriert** werden Softwareupdates auf dem Gerät angezeigt, sobald Apple sie veröffentlicht. Wenn beispielsweise ein macOS-Update von Apple an einem bestimmten Datum veröffentlicht wird, wird dieses Update normalerweise um oder am Veröffentlichungsdatum auf dem Gerät angezeigt. Updates von Seedbuilds sind ohne Verzögerung zulässig.

  **Aktivieren** ermöglicht Ihnen, die Anzeige von Softwareupdates auf Geräten zu verzögern (0-90 Tage). Diese Einstellung steuert nicht, ob Updates installiert werden oder nicht. 

  - **Sichtbarkeit von Softwareupdates verzögern**: Geben Sie einen Wert zwischen 0–90 Tagen ein. Nach der Verzögerung erhalten Benutzer eine Benachrichtigung für ein Update auf die früheste Version des Betriebssystems, die verfügbar war, als die Verzögerung ausgelöst wurde.

    Wenn beispielsweise ein macOS-Update am **1. Januar** verfügbar ist und **Delay visibility** (Sichtbarkeit verzögern) auf **5 Tage** festgelegt ist, wird das Update nicht als verfügbares Update angezeigt. Am **6. Tag** nach Veröffentlichung ist dieses Update verfügbar, sodass Endbenutzer es installieren können.

    Diese Funktion gilt für:  
    - macOS 10.13.4 und höher

- **Screenshots**: Das Gerät muss bei der automatischen Geräteregistrierung (DEP) von Apple registriert sein. Wurde die Einstellung auf **Blockieren** festgelegt, können Benutzer keinen Screenshot der Anzeige speichern. Außerdem wird verhindert, dass die Classroom-App Remotebildschirme überwacht. Bei der Standardeinstellung **Nicht konfiguriert** können Benutzer Screenshots erstellen, und die Classroom-App darf Remotebildschirme anzeigen.

### <a name="settings-apply-to-automated-device-enrollment"></a>Die Einstellungen gelten für: Automatisierte Geräteregistrierung

- **Remotebildschirmüberwachung über Classroom-App**: Mit der Einstellung **Deaktivieren** wird verhindert, dass Lehrkräfte über die Classroom-App die Bildschirme der Kursteilnehmer anzeigen können. Bei der Standardeinstellung **Nicht konfiguriert** können Lehrkräfte die Bildschirme der Kursteilnehmer anzeigen.

  Legen Sie hierfür den Wert für **Screenshots** auf **Nicht konfiguriert** fest (Screenshots sind zulässig).

- **Unangekündigte Bildschirmüberwachung über Classroom-App**: Mit der Einstellung **Zulassen** ist es Lehrkräften möglich, die Bildschirme der Kursteilnehmer ohne deren Zustimmung anzuzeigen. Bei der Standardeinstellung **Nicht konfiguriert** ist vor dem Anzeigen der Bildschirme die Zustimmung der Kursteilnehmer erforderlich.

  Legen Sie hierfür den Wert für **Screenshots** auf **Nicht konfiguriert** fest (Screenshots sind zulässig).

- **Kursteilnehmer müssen die Erlaubnis zum Verlassen der Classroom-Klasse anfordern**: Mit der Einstellung **Anfordern** müssen Kursteilnehmer, die bei einem nicht verwalteten Classroom-Kurs angemeldet sind, zum Verlassen des Kurses die Erlaubnis der Lehrkraft anfordern. Bei der Standardeinstellung **Nicht konfiguriert** können die Kursteilnehmer den Kurs jederzeit verlassen.

- **Lehrkräfte können Geräte oder Apps in der Classroom-App automatisch sperren**: Mit der Einstellung **Zulassen** können Lehrkräfte die Geräte oder Apps von Kursteilnehmern ohne deren Zustimmung sperren. Bei der Standardeinstellung **Nicht konfiguriert** ist vor dem Sperren eines Geräts oder einer App die Zustimmung des Kursteilnehmers erforderlich.

- **Kursteilnehmer können der Classroom-Klasse automatisch beitreten**: Mit der Einstellung **Zulassen** können Kursteilnehmer einer Klasse beitreten, ohne die Lehrkraft um Erlaubnis fragen zu müssen. Bei der Standardeinstellung **Nicht konfiguriert** ist für den Beitritt zu einer Klasse die Zustimmung der Lehrkraft erforderlich.

## <a name="password"></a>Kennwort

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Die Einstellungen gelten für: Geräteregistrierung und Automatische Geräteregistrierung

- **Kennwort:** **Anfordern** der Kennworteingabe durch den Endbenutzer für den Zugriff auf das Gerät. Bei der Standardeinstellung **Nicht konfiguriert** ist kein Kennwort erforderlich. Außerdem werden keine Einschränkungen erzwungen, wie z. B. das Blockieren einfacher Kennwörter oder das Festlegen einer Mindestlänge.
  - **Erforderlicher Kennworttyp:** Gibt an, ob das Kennwort rein numerisch sein darf oder ob es alphanumerisch sein muss (also Buchstaben und Zahlen enthalten muss).

    Diese Funktion gilt für:  
    - macOS 10.10.3 und höher

  - **Anzahl nicht alphanumerischer Zeichen im Kennwort:** Gibt die Anzahl komplexer Zeichen an, die das Kennwort enthalten muss (**0** bis **4**).<br>Bei einem komplexen Zeichen handelt es sich um ein Symbol, z.B. **?** .
  - **Minimale Kennwortlänge:** Geben Sie die Mindestanzahl von Zeichen an, die Benutzer für das Kennwort verwenden müssen (zwischen **4** und **16** Zeichen).
  - **Einfache Kennwörter:** Ermöglicht die Verwendung einfacher Kennwörter (z. B.**0000**oder**1234**).
  - **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts**: Gibt an, wie lange der Computer inaktiv sein muss, bevor er mithilfe eines Kennworts entsperrt werden muss.
  - **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung:** Gibt an, wie lange sich der Computer im Leerlauf befinden muss, bevor der Bildschirm gesperrt wird.
  - **Kennwortablauf (Tage):** Gibt an, nach wie vielen Tagen der Benutzer das Kennwort ändern muss (**1** bis **255** Tage).
  - **Wiederverwendung vorheriger Kennwörter verhindern:** Geben Sie die Anzahl der zuvor verwendeten Kennwörter ein, die nicht erneut verwendet werden können, von **1** bis **24**.

- **Ändern des Passcodes durch Benutzer blockieren**: Wählen Sie **Blockieren** aus, damit die Kennung nicht geändert, hinzugefügt oder entfernt werden kann. **Nicht konfiguriert** (Standard) ermöglicht, Passcodes hinzuzufügen, zu ändern oder zu entfernen.
- **Entsperren per Fingerabdruck blockieren**: Wählen Sie **Blockieren** aus, um die Verwendung eines Fingerabdrucks zum Entsperren des Geräts zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer das Entsperren des Geräts mittels Fingerabdruck.

- **AutoAusfüllen für Kennwörter blockieren**: Wählen Sie **Blockieren** aus, um die Verwendung des Features zum automatischen Ausfüllen von Kennwörtern unter macOS zu verhindern. Das Wählen von **Blockieren** bewirkt auch Folgendes:

  - Benutzer werden nicht aufgefordert, in Safari oder beliebigen Apps gespeicherte Kennwörter zu verwenden.
  - Automatische sichere Kennwörter sind deaktiviert, und sichere Kennwörter werden Benutzern nicht empfohlen.

  **Nicht konfiguriert** (Standard) lässt diese Funktionen zu.

- **Kennwortanforderungen durch Näherung blockieren**: Wählen Sie **Blockieren** aus, damit das Gerät eines Benutzers keine Kennwörter von in der Nähe befindlichen Geräten anfordert. **Nicht konfiguriert** (Standard) lässt diese Kennwortanforderungen zu.

- **Kennwortfreigabe blockieren**: **Blockieren** verhindert die Freigabe von Kennwörtern zwischen Geräten mit AirDrop. **Nicht konfiguriert** (Standard) ermöglicht die Freigabe von Kennwörtern.

## <a name="built-in-apps"></a>Integrierte Apps

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Die Einstellungen gelten für: Geräteregistrierung und Automatische Geräteregistrierung

- **AutoAusfüllen in Safari blockieren**: **Blockieren** deaktiviert auf dem Gerät das AutoAusfüllen-Feature in Safari. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, die AutoAusfüllen-Einstellungen im Browser zu ändern.
- **Kamera blockieren**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Kamera des Geräts zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf die Kamera des Geräts.
- **Apple Music blockieren**: **Blockieren** setzt die Musik-App in den klassischen Modus zurück und deaktiviert den Musikdienst. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der Apple Music-App.
- **Internetsuchergebnisse für Spotlight blockieren**: **Blockieren** verhindert, dass Spotlight Ergebnisse einer Internetsuche zurückgibt. **Nicht konfiguriert** (Standard) ermöglicht der Spotlight-Suchfunktion das Herstellen einer Verbindung mit dem Internet zur Bereitstellung von Suchergebnissen.
- **Dateiübertragung über iTunes blockieren**: **Blockieren** deaktiviert Dateifreigabedienste der Anwendung. Die Standardeinstellung **Nicht konfiguriert** lässt Freigabedienste für Anwendungsdateien zu.

  Diese Funktion gilt für:  
  - macOS 10.13 und höher

## <a name="restricted-apps"></a>Eingeschränkte Apps

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Die Einstellungen gelten für: Geräteregistrierung und Automatische Geräteregistrierung

- **Liste der eingeschränkten App-Typen:** Mit dieser Einstellung wird eine Liste der Apps erstellt, die Benutzer nicht installieren oder verwenden dürfen. Folgende Optionen sind verfügbar:

  - **Nicht konfiguriert** (Standardeinstellung): Bei dieser Einstellung liegen keine Einschränkungen durch Intune vor. Benutzer können auf integrierte Apps und Apps zugreifen, die Sie ihnen zuweisen.
  - **Unzulässige Apps:** Nicht von Intune verwaltete Apps, die nicht auf dem Gerät installiert werden sollen. Benutzer können unzulässige Apps nicht installieren. Wenn ein Benutzer jedoch eine App aus dieser Liste installiert, wird dies in Intune gemeldet.
  - **Genehmigte Apps:** Apps, die Benutzer installieren dürfen. Benutzer dürfen keine Apps installieren, die in dieser Liste nicht aufgeführt sind. Apps, die von Intune verwaltet werden, sind automatisch zugelassen. Benutzer werden nicht daran gehindert, eine App zu installieren, die nicht in der Liste zulässiger Apps enthalten ist. Wenn sie es jedoch tun, wird dies in Intune gemeldet.
- **App-Bündel-ID:** Geben Sie die [App-Bündel-ID](bundle-ids-built-in-ios-apps.md) der gewünschten App ein. Sie können sowohl integrierte Apps als auch branchenspezifische Apps anzeigen oder ausblenden. Eine Liste der integrierten Apple-Apps finden Sie auf [dieser Apple-Website](https://support.apple.com/HT208094).
- **App-Name:** Geben Sie den App-Namen der gewünschten App ein. Sie können sowohl integrierte Apps als auch branchenspezifische Apps anzeigen oder ausblenden. Eine Liste der integrierten Apple-Apps finden Sie auf [dieser Apple-Website](https://support.apple.com/HT208094).
- **Herausgeber**: Geben Sie den Herausgeber der gewünschten App ein.

Um diesen Listen Apps hinzuzufügen, können Sie:

- **Hinzufügen**: Verwenden Sie diese Option, um Ihre Liste mit Apps zu erstellen.
- **Importieren** Sie eine CSV-Datei mit den Details der App, einschließlich der URL. Verwenden Sie das Format `<app bundle ID>, <app name>, <app publisher>`. Oder **exportieren** Sie eine Datei im selben Format, um eine Liste der hinzugefügten Apps zu erstellen.

## <a name="connected-devices"></a>Verbundene Geräte

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Die Einstellungen gelten für: Geräteregistrierung und Automatische Geräteregistrierung

- **AirDrop blockieren**: **Blockieren** verhindert die Verwendung von AirDrop auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung von AirDrop zum Austauschen von Inhalten mit Geräten in der Nähe.
- **Automatisches Entsperren mit Apple Watch blockieren**: **Blockieren** hindert Benutzer daran, ihr macOS-Gerät mit ihrer Apple Watch zu entsperren. Die Standardeinstellung **Nicht konfiguriert** erlaubt Benutzern, ihr macOS-Gerät mit ihrer Apple Watch zu entsperren.

## <a name="cloud-and-storage"></a>Cloud und Speicher

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Die Einstellungen gelten für: Geräteregistrierung und Automatische Geräteregistrierung

- **Synchronisierung zwischen iCloud und Keychain blockieren:** Wählen Sie **Blockieren** aus, um die Synchronisierung von in der Keychain gespeicherten Anmeldeinformationen mit iCloud zu deaktivieren. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Anmeldeinformationen zu synchronisieren.
- **iCloud-Dokumentsynchronisierung blockieren**: **Blockieren** hindert iCloud daran, Dokumente und Daten zu synchronisieren. **Nicht konfiguriert** (Standard) erlaubt die Dokument- und Schlüssel-/Wertsynchronisierung in Ihrem iCloud-Speicher.
- **iCloud-E-Mail-Sicherung blockieren**: **Blockieren** hindert iCloud an der Synchronisierung mit der macOS-App „Mail“. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung der Mail-App mit iCloud zu.
- **iCloud-Kontaktsicherung blockieren**: **Blockieren** hindert iCloud an der Synchronisierung der Kontakte auf Geräten. Die Standardeinstellung **Nicht konfiguriert** erlaubt die Kontaktsynchronisierung über iCloud.
- **iCloud-Kalendersicherung blockieren**: **Blockieren** hindert iCloud an der Synchronisierung mit der Kalender-App von macOS. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung der Kalender-App mit iCloud zu.
- **iCloud-Sicherung von Erinnerungen blockieren**: **Blockieren** hindert iCloud an der Synchronisierung mit der Erinnerungen-App von macOS. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung der Erinnerungen-App mit iCloud zu.
- **iCloud-Lesezeichensicherung blockieren**: **Blockieren** hindert iCloud an der Synchronisierung der Lesezeichen auf Geräten. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung von Lesezeichen mit iCloud zu.
- **iCloud-Notizensicherung blockieren**: **Blockieren** hindert iCloud an der Synchronisierung der Notizen auf Geräten. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung von Notizen mit iCloud zu.
- **iCloud-Fotomediathek blockieren**: Mit der Einstellung **Blockieren** wird die iCloud-Fotomediathek deaktiviert und die Synchronisierung der Gerätefotos verhindert. Fotos, die nicht vollständig aus der iCloud-Fotomediathek heruntergeladen wurden, werden aus dem lokalen Speicher des jeweiligen Geräts entfernt. Mit der Standardeinstellung **Nicht konfiguriert** ist die Synchronisierung von Fotos zwischen dem Gerät und der iCloud-Fotomediathek möglich.
- **Handoff:** Bei der Standardeinstellung **Nicht konfiguriert** können Benutzer mit der Arbeit auf einem macOS-Gerät beginnen und ihre Arbeit auf einem anderen iOS-/iPadOS- oder macOS-Gerät fortsetzen. Mit der Einstellung **Blockieren** wird die Handoff-Funktion auf dem Gerät verhindert. 

  Diese Funktion gilt für:  
  - macOS 10.15 und neuer

## <a name="domains"></a>Domänen

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Die Einstellungen gelten für: Geräteregistrierung und Automatische Geräteregistrierung

- **E-Mail-Domänen-URL**: **Fügen** Sie der Liste eine oder mehrere URLs hinzu. Wenn Benutzer eine E-Mail von einer Domäne erhalten, die Sie nicht konfiguriert haben, wird die E-Mail in der macOS-Mail-App als nicht vertrauenswürdig gekennzeichnet.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](../device-profile-assign.md) und [Überwachen von Profilen](../device-profile-monitor.md)

Sie können auch Gerätefunktionen und -einstellungen auf [iOS-/iPadOS](../device-restrictions-ios.md)-Geräten einschränken.
