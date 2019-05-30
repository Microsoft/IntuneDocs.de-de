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

[Erstellen Sie ein Konfigurationsprofil mit Geräteeinschränkungen](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Allgemein

- **Definitionssuche blockieren**: **Blockieren** hindert Benutzer daran, ein Wort zu markieren und dann auf dem Gerät nach seiner Definition zu suchen. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf die Definitionssuchfunktion.
- **Block Dictation** (Diktat blockieren): **Blockieren** verhindert, dass der Benutzer die Spracheingabe zur Eingabe von Text verwenden kann. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, die Spracheingabe zu verwenden.
- **Zwischenspeicherung von Inhalten blockieren**: In der Standardeinstellung **Nicht konfiguriert** ist die Zwischenspeicherung von Inhalten aktiviert. Bei Zwischenspeicherung von Inhalten werden u.a. App- und Webbrowserdaten und Downloads lokal auf dem Gerät gespeichert. Wählen Sie **Blockieren** aus, um zu verhindern, dass diese Daten im Cache gespeichert werden.

  Weitere Informationen zum Zwischenspeichern von Inhalten unter macOS finden Sie unter [Verwalten des Inhaltscaching auf dem Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (öffnet eine andere Website).

  Diese Funktion gilt für:  
  - macOS 10.13 und höher

- **Softwareupdates zurückstellen**: In der Standardeinstellung **Nicht konfiguriert** werden Softwareupdates auf dem Gerät angezeigt, sobald Apple sie veröffentlicht. Wenn beispielsweise ein macOS-Update von Apple an einem bestimmten Datum veröffentlicht wird, wird dieses Update normalerweise um oder am Veröffentlichungsdatum auf dem Gerät angezeigt. Updates von Seedbuilds sind ohne Verzögerung zulässig.

  **Aktivieren** ermöglicht Ihnen, die Anzeige von Softwareupdates auf Geräten zu verzögern (0-90 Tage). Diese Einstellung steuert nicht, ob Updates installiert werden oder nicht. 

  - **Sichtbarkeit von Softwareupdates verzögern**: Geben Sie einen Wert von 0-90 Tagen ein. Nach der Verzögerung erhalten Benutzer eine Benachrichtigung für ein Update auf die früheste Version des Betriebssystems, die verfügbar war, als die Verzögerung ausgelöst wurde.

    Wenn beispielsweise ein macOS-Update am **1. Januar** verfügbar ist und **Sichtbarkeit verzögern** auf **5 Tage** festgelegt ist, wird das Update nicht als verfügbares Update auf Endbenutzergeräten angezeigt. Am **6. Tag** nach der Veröffentlichung ist dieses Update verfügbar, sodass Endbenutzer es installieren können.

    Diese Funktion gilt für:  
    - macOS 10.13.4 und höher

## <a name="password"></a>Kennwort

- **Kennwort**: **Anfordern** der Eingabe eines Kennworts durch den Endbenutzer, um auf das Gerät zugreifen zu können. In der Standardeinstellung **Nicht konfiguriert** ist kein Kennwort erforderlich, und es werden keine Einschränkungen erzwungen, wie z.B. das Blockieren einfacher Kennwörter oder das Festlegen einer Mindestlänge.
  - **Erforderlicher Kennworttyp**: Geben Sie an, ob das Kennwort rein numerisch sein darf oder ob es alphanumerisch sein muss (also Buchstaben und Zahlen enthalten muss). Diese Einstellung wird lediglich unter Mac OS X 10.10.3 und höher unterstützt.
  - **Anzahl nicht alphanumerischer Zeichen im Kennwort**: Geben Sie die erforderliche Anzahl komplexer Zeichen im Kennwort an (**0** bis **4**).<br>Bei einem komplexen Zeichen handelt es sich um ein Symbol, z.B. **?**.
  - **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl von Zeichen an, die Benutzer für das Kennwort festlegen müssen (zwischen **4** und **16** Zeichen).
  - **Einfache Kennwörter**: Erlauben Sie die Verwendung einfacher Kennwörter wie **0000** oder **1234**.
  - **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts**: Geben Sie an, wie lange der Computer inaktiv sein muss, bevor er mithilfe eines Kennworts entsperrt werden muss.
  - **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung**: Geben Sie die Zeitdauer an, die der Computer inaktiv sein muss, bevor der Bildschirm gesperrt wird.
  - **Kennwortablauf (Tage)**: Geben Sie an, nach wie vielen Tagen der Benutzer das Kennwort ändern muss (**1** bis **255** Tage).
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

- **Block Safari AutoFill** (AutoAusfüllen in Safari blockieren): **Blockieren** deaktiviert AutoAusfüllen in Safari auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, die AutoAusfüllen-Einstellungen im Browser zu ändern.
- **Kamera blockieren**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Kamera des Geräts zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf die Kamera des Geräts.
- **Apple Music blockieren**: ** Blockieren** setzt die Musik-App in den klassischen Modus zurück und deaktiviert den Musikdienst. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der Apple Music-App.
- **Rückgabe von Internetsuchergebnissen in Spotlight blockieren**: **Blockieren** verhindert, dass Spotlight Ergebnisse einer Internetsuche zurückgibt. **Nicht konfiguriert** (Standard) ermöglicht der Spotlight-Suchfunktion das Herstellen einer Verbindung mit dem Internet zur Bereitstellung von Suchergebnissen.
- **Dateiübertragung mit iTunes blockieren**: Bei Wahl von **Blockieren** werden Freigabedienste für Anwendungsdateien deaktiviert. In macOS 10.13 und höher verfügbar. Die Standardeinstellung **Nicht konfiguriert** lässt Freigabedienste für Anwendungsdateien zu.

## <a name="restricted-apps"></a>Eingeschränkte Apps

In der Liste der eingeschränkten Apps können Sie eine der folgenden Listen konfigurieren:

- Liste **Unzulässige Apps**: Listet die nicht von Intune verwalteten Apps auf, die Benutzer nicht installieren und ausführen dürfen. Benutzer werden nicht daran gehindert, eine unzulässige App zu installieren. Wenn sie dennoch tun, wird es dem Administrator gemeldet.
- Liste **Genehmigte Apps**: Listet die Apps auf, die Benutzer installieren dürfen. Benutzer dürfen keine Apps installieren, die in dieser Liste nicht aufgeführt sind. Apps, die von Intune verwaltet werden, sind automatisch zugelassen. Benutzer werden nicht daran gehindert, eine App zu installieren, die nicht in der Liste zulässiger Apps enthalten ist. Falls sie es dennoch tun, wird dies dem Administrator gemeldet.

Klicken Sie zum Konfigurieren einer Liste auf **Hinzufügen**. Geben Sie dann einen Namen Ihrer Wahl sowie optional den Herausgeber der App und die Paket-ID der App an (z.B. *com.apple.calculator*).

## <a name="connected-devices"></a>Verbundene Geräte

- **AirDrop blockieren**: **Blockieren** verhindert die Verwendung von AirDrop auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung von AirDrop zum Austauschen von Inhalten mit Geräten in der Nähe.
- **Automatisches Entsperren von Apple Watch blockieren**: **Blockieren** hindert Benutzer daran, ihr macOS-Gerät mit ihrer Apple Watch zu entsperren. Die Standardeinstellung **Nicht konfiguriert** erlaubt Benutzern, ihr macOS-Gerät mit ihrer Apple Watch zu entsperren.

## <a name="cloud-and-storage"></a>Cloud und Speicher

- **Synchronisierung zwischen iCloud und Keychain blockieren**: Wählen Sie **Blockieren** aus, um die Synchronisierung in der Keychain gespeicherter Anmeldeinformationen mit iCloud zu deaktivieren. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Anmeldeinformationen zu synchronisieren.
- **iCloud-Synchronisierung von Dokumenten blockieren**: **Blockieren** hindert iCloud daran, Dokumente und Daten zu synchronisieren. **Nicht konfiguriert** (Standard) erlaubt die Dokument- und Schlüssel-/Wertsynchronisierung in Ihrem iCloud-Speicher.
- **iCloud-Sicherung von Mail blockieren**: **Blockieren** hindert iCloud an der Synchronisierung mit der der macOS-App „Mail“. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung der Mail-App mit iCloud zu.
- **iCloud-Sicherung von Kontakten blockieren**: **Blockieren** hindert iCloud an der Synchronisierung der Kontakte auf Geräten. Die Standardeinstellung **Nicht konfiguriert** erlaubt die Kontaktsynchronisierung über iCloud.
- **iCloud-Sicherung von Kalender blockieren**: **Blockieren** hindert iCloud an der Synchronisierung mit der macOS-App „Kalender“. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung der Kalender-App mit iCloud zu.
- **iCloud-Sicherung von Erinnerungen blockieren**: **Blockieren** hindert iCloud an der Synchronisierung mit der macOS-App „Erinnerungen“. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung der Erinnerungen-App mit iCloud zu.
- **iCloud-Sicherung von Lesezeichen blockieren**: **Blockieren** hindert iCloud an der Synchronisierung der Lesezeichen auf Geräten. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung von Lesezeichen mit iCloud zu.
- **iCloud-Sicherung von Notizen blockieren**: **Blockieren** hindert iCloud an der Synchronisierung der Notizen auf Geräten. Die Standardeinstellung **Nicht konfiguriert** lässt die Synchronisierung von Notizen mit iCloud zu.

## <a name="domains"></a>Domains

- **E-Mail-Domänen-URL**: Fügen Sie eine oder mehrere URLs zur Liste hinzu. Wenn Benutzer eine E-Mail von einer Domäne erhalten, die Sie nicht konfiguriert haben, wird die E-Mail in der macOS-Mail-App als nicht vertrauenswürdig gekennzeichnet.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Sie können auch Gerätefeatures und -einstellungen auf [iOS](device-restrictions-ios.md)-Geräten einschränken.
