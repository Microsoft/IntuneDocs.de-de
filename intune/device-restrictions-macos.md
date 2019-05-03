---
title: 'macOS-Geräteeinstellungen in Microsoft Intune: Azure | Microsoft-Dokumentation'
titleSuffix: ''
description: Fügen Sie Einstellungen auf macOS-Geräten hinzu, und konfigurieren oder erstellen Sie sie, um Funktionen einzuschränken. Hierzu gehören das Festlegen von Anforderungen für Kennwörter, die Anpassung des Sperrbildschirms, die Verwendung integrierter Apps, das Hinzufügen eingeschränkter oder genehmigter Apps, die Handhabung von Bluetooth-Geräten, das Herstellen einer Verbindung zur Cloud für Sicherung und Speicherung, die Aktivierung des Kioskmodus, das Hinzufügen von Domänen und die Steuerung, wie Benutzer mit dem Safari-Webbrowser in Microsoft Intune interagieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/13/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5feec66e791da4038bd069cdad69a7ba573f27f3
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798376"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>macOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie auf macOS-Geräten steuern können. Verwenden Sie als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) diese Einstellungen, um Features zuzulassen oder zu deaktivieren, Kennwortregeln festzulegen, bestimmte Apps zu erlauben oder einzuschränken usw.

Diese Einstellungen werden einem Gerätekonfigurationsprofil in Intune hinzugefügt und dann Ihren macOS-Geräten zugewiesen oder bereitgestellt.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen ein gerätekonfigurationsprofils von Einschränkungen](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Allgemein

- **Definitionssuche blockieren**: **Blockieren** hindert Benutzer daran, ein Wort zu markieren und dann auf dem Gerät nach seiner Definition zu suchen. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf die Definitionssuchfunktion.
- **Block Dictation** (Diktat blockieren): **Blockieren** verhindert, dass der Benutzer die Spracheingabe zur Eingabe von Text verwenden kann. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, die Spracheingabe zu verwenden.
- **Zwischenspeichern von Inhalten zu blockieren**: Wählen Sie **nicht konfiguriert** (Standard) zum Zwischenspeichern von Inhalten aktivieren. Zwischenspeichern von Inhalten werden app-Daten, Webbrowserdaten, Downloads und vieles mehr lokal auf dem Gerät speichert. Wählen Sie **Block** zu verhindern, dass diese Daten, die im Cache gespeichert werden.

  Weitere Informationen zum Zwischenspeichern von Inhalten unter MacOS, finden Sie unter [verwalten Zwischenspeichern von Inhalten auf Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (öffnet eine andere Website).

  Diese Funktion gilt für:  
  - macOS 10.13 und höher

- **Zurückstellen von Softwareupdates**: bei Festlegung auf **nicht konfiguriert** (Standard), Softwareupdates angezeigt werden, auf dem Gerät wie Apple veröffentlicht. Z. B. wenn ein MacOS-Update von Apple an einem bestimmten Datum veröffentlicht ruft wird dann das Update auf natürliche Weise auf dem Gerät, um das Datum der Veröffentlichung. SEED-Build-Updates werden ohne Verzögerung zulässig.

  **Aktivieren Sie** lässt sich verzögern, wenn Softwareupdates auf Geräten, von 0 bis 90 Tage angezeigt werden. Diese Einstellung steuern nicht, wann Updates sind, oder werden nicht installiert. 

  - **Sichtbarkeit von Softwareupdates verzögern**: Geben Sie einen Wert von 0 bis 90 Tage. Nach der Verzögerung erhalten Benutzer eine Benachrichtigung für ein Update auf die früheste Version des Betriebssystems, die verfügbar war, als die Verzögerung ausgelöst wurde.

    Angenommen, ein MacOS-Update verfügbar ist **am 1. Januar**, und **verzögern Sichtbarkeit** nastaven NA hodnotu **5 Tage**, und klicken Sie dann das Update nicht als verfügbares Update auf Geräten angezeigt. Auf der **sechsten Tag** nach der Freigabe, die, dass Update verfügbar ist, und Benutzer können es installieren.

    Diese Funktion gilt für:  
    - macOS 10.13.4 und höher

## <a name="password"></a>Kennwort

- **Kennwort**: **Anfordern** der Eingabe eines Kennworts durch den Endbenutzer, um auf das Gerät zugreifen zu können. **Nicht konfiguriert** (Standard) nicht anfordern eines Kennworts, und nicht erzwingen, dass alle Einschränkungen, z. B. einfache Kennwörter blockieren oder eine minimale Länge festlegen.
  - **Erforderlicher Kennworttyp**: Geben Sie an, ob das Kennwort rein numerisch sein darf oder ob es alphanumerisch sein muss (also Buchstaben und Zahlen enthalten muss). Diese Einstellung wird lediglich unter Mac OS X 10.10.3 und höher unterstützt.
  - **Anzahl nicht alphanumerischer Zeichen im Kennwort**: Geben Sie die erforderliche Anzahl komplexer Zeichen im Kennwort an (**0** bis **4**).<br>Bei einem komplexen Zeichen handelt es sich um ein Symbol, z.B. **?**.
  - **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl von Zeichen an, die Benutzer für das Kennwort festlegen müssen (zwischen **4** und **16** Zeichen).
  - **Einfache Kennwörter**: Erlauben Sie die Verwendung einfacher Kennwörter wie **0000** oder **1234**.
  - **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts**: Geben Sie an, wie lange der Computer inaktiv sein muss, bevor er mithilfe eines Kennworts entsperrt werden muss.
  - **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung**: Geben Sie die Zeitdauer an, die der Computer inaktiv sein muss, bevor der Bildschirm gesperrt wird.
  - **Kennwortablauf (Tage)**: Geben Sie an, nach wie vielen Tagen der Benutzer das Kennwort ändern muss (**1** bis **255** Tage).
  - **Wiederverwendung vorheriger Kennwörter verhindern**: Geben Sie die Anzahl von vorherigen Kennwörtern an, die nicht erneut verwendet werden dürfen (**1** bis **24**).

- **Benutzer von Kennung ändern**: Wählen Sie **Block** beenden Sie die Kennung geändert werden, hinzugefügt oder entfernt. **Nicht konfiguriert** (Standard) ermöglicht, Passcodes hinzuzufügen, zu ändern oder zu entfernen.
- **Entsperren per Fingerabdruck blockieren**: Wählen Sie **Blockieren** aus, um die Verwendung eines Fingerabdrucks zum Entsperren des Geräts zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer das Entsperren des Geräts mittels Fingerabdruck.

- **AutoAusfüllen für Kennwörter blockieren**: Wählen Sie **Blockieren**, um die Verwendung der Funktion zum automatischen Ausfüllen von Kennwörtern unter MacOS zu verhindern. Auswahl **Block** auch hat folgende Auswirkungen:

  - Benutzer werden nicht aufgefordert, in Safari oder beliebigen Apps gespeicherte Kennwörter zu verwenden.
  - Automatische sichere Kennwörter sind deaktiviert, und sichere Kennwörter werden Benutzern nicht empfohlen.

  **Nicht konfiguriert** (Standard) lässt diese Funktionen zu.

- **Kennwortanforderungen durch Näherung blockieren**: Wählen Sie **Blockieren** aus, damit das Gerät eines Benutzers keine Kennwörter von in der Nähe befindlichen Geräten anfordert. **Nicht konfiguriert** (Standard) lässt diese Kennwortanforderungen zu.

- **Kennwortfreigabe blockieren**: **Blockieren** verhindert die Freigabe von Kennwörtern zwischen Geräten mit AirDrop. **Nicht konfiguriert** (Standard) ermöglicht die Freigabe von Kennwörtern.

## <a name="built-in-apps"></a>Integrierte Apps

- **Block Safari AutoFill** (AutoAusfüllen in Safari blockieren): **Blockieren** deaktiviert AutoAusfüllen in Safari auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, die AutoAusfüllen-Einstellungen im Browser zu ändern.
- **Kamera blockieren**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Kamera des Geräts zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf die Kamera des Geräts.
- **Apple Music blockieren**:  **Blockieren** setzt die Musik-App in den klassischen Modus zurück und deaktiviert den Musikdienst. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der Apple Music-App.
- **Block Spotlight-Suchergebnissen Internet**: **Block** verhindert, dass Blickpunkt Ergebnisse über eine Internetsuche zurückzugeben. **Nicht konfiguriert** (Standard) ermöglicht der Spotlight-Suchfunktion das Herstellen einer Verbindung mit dem Internet zur Bereitstellung von Suchergebnissen.
- **Block Dateiübertragung mit iTunes**: **Block** Dateifreigabedienste Anwendung deaktiviert. In MacOS 10.13 und höher verfügbar. **Nicht konfiguriert** (Standard) ermöglicht die Anwendung Dateifreigabedienste.

## <a name="restricted-apps"></a>Eingeschränkte Apps

In der Liste der eingeschränkten Apps können Sie eine der folgenden Listen konfigurieren:

- Liste **Unzulässige Apps**: Listet die nicht von Intune verwalteten Apps auf, die Benutzer nicht installieren und ausführen dürfen. Benutzer werden nicht daran gehindert eine verbotene app zu installieren, jedoch ist dies der Fall ist, wird es dem Administrator gemeldet.
- Liste **Genehmigte Apps**: Listet die Apps auf, die Benutzer installieren dürfen. Benutzer dürfen keine Apps installieren, die in dieser Liste nicht aufgeführt sind. Apps, die von Intune verwaltet werden, sind automatisch zugelassen. Benutzer werden nicht daran gehindert, eine app, die auf der Genehmigungsliste aufgeführt ist nicht zu installieren. Allerdings ist dies der Fall ist, wird es dem Administrator gemeldet.

Klicken Sie zum Konfigurieren einer Liste auf **Hinzufügen**. Geben Sie dann einen Namen Ihrer Wahl sowie optional den Herausgeber der App und die Paket-ID der App an (z.B. *com.apple.calculator*).

## <a name="connected-devices"></a>Verbundene Geräte

- **AirDrop blockieren**: **Blockieren** verhindert die Verwendung von AirDrop auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung von AirDrop zum Austauschen von Inhalten mit Geräten in der Nähe.
- **Block Apple Watch automatisch Entsperren**: **Block** verhindert, dass Benutzer ihre MacOS-Gerät mit ihrer Apple Watch-entsperren. **Nicht konfiguriert** (Standard) kann Benutzer mit ihrer Apple Watch-sein MacOS-Gerät zu entsperren.

## <a name="cloud-and-storage"></a>Cloud und Speicher

- **Synchronisierung zwischen iCloud und Keychain blockieren**: Wählen Sie **Blockieren** aus, um die Synchronisierung in der Keychain gespeicherter Anmeldeinformationen mit iCloud zu deaktivieren. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Anmeldeinformationen zu synchronisieren.
- **Blockieren von iCloud Dokumentsynchronisierung**: **Block** verhindert, dass iCloud synchronisieren, Dokumente und Daten. **Nicht konfiguriert** (Standard) erlaubt die Dokument- und Schlüssel-/Wertsynchronisierung in Ihrem iCloud-Speicher.
- **ICloud-Sicherung der E-Mails blockieren**: **Block** verhindert, dass iCloud auf dem MacOS-Mail-app synchronisiert. **Nicht konfiguriert** ermöglicht das e-Mail-Synchronisierung mit icloud zulassen (Standard).
- **Blockieren von iCloud-Sicherung der Kontakt**: **Block** verhindert, dass iCloud synchronisieren die Geräte-Kontakte. **Nicht konfiguriert** (Standard) ermöglicht es, wenden Sie sich an, über die iCloud synchronisieren.
- **ICloud-Sicherung für Kalender blockieren**: **Block** verhindert, dass iCloud synchronisieren, um die Kalender-app für MacOS. **Nicht konfiguriert** (Standard) ermöglicht die Kalender-Synchronisierung in iCloud.
- **Blockieren von iCloud-Sicherung der Erinnerung**: **Block** verhindert, dass iCloud synchronisieren für die MacOS-Erinnerungen-app. **Nicht konfiguriert** (Standard) ermöglicht die Erinnerungen Synchronisierung in iCloud.
- **Blockieren von iCloud-Sicherung von Lesezeichen**: **Block** verhindert, dass iCloud synchronisieren die Lesezeichen-Geräte. **Nicht konfiguriert** (Standard) ermöglicht die Lesezeichen-Synchronisierung in iCloud.
- **ICloud-Sicherung von Anmerkungen zu dieser Version blockieren**: **Block** verhindert, dass iCloud synchronisieren die Anmerkungen zu dieser Geräte. **Nicht konfiguriert** (Standard) ermöglicht die Anmerkungen zu dieser Synchronisierung in iCloud.

## <a name="domains"></a>Domänen

- **E-Mail-Domänen-URL**: Fügen Sie eine oder mehrere URLs zur Liste hinzu. Wenn Benutzer eine E-Mail von einer Domäne erhalten, die Sie nicht konfiguriert haben, wird die E-Mail in der macOS-Mail-App als nicht vertrauenswürdig gekennzeichnet.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Sie können auch Gerätefunktionen und-Einstellungen auf einschränken [iOS](device-restrictions-ios.md) Geräte.
