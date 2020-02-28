---
title: 'iOS/iPadOS-Geräteeinstellungen in Microsoft Intune: Azure | Microsoft-Dokumentation'
titleSuffix: ''
description: Fügen Sie Einstellungen auf iOS/iPadOS-Geräten hinzu, konfigurieren oder erstellen Sie sie, um Funktionen einzuschränken. Zu diesen gehört das Festlegen von Anforderungen für Kennwörter, die Anpassung des Sperrbildschirms, die Verwendung integrierter Apps, das Hinzufügen eingeschränkter oder genehmigter Apps, die Handhabung von Bluetooth-Geräten, die Verbindungsherstellung mit der Cloud für Sicherung und Speicherung, die Aktivierung des Kioskmodus, das Hinzufügen und die Steuerung von Domänen und die Art der Benutzerinteraktion mit dem Safari-Webbrowser in Microsoft Intune.
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
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1e352ca0c0100ebe1756d621feb725e040521901
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513066"
---
# <a name="ios-and-ipados-device-settings-to-allow-or-restrict-features-using-intune"></a>iOS- und iPadOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie auf iOS- und iPadOS-Geräten steuern können. Verwenden Sie als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) diese Einstellungen, um Features zuzulassen oder zu deaktivieren, Kennwortregeln festzulegen, bestimmte Apps zu erlauben oder einzuschränken usw.

Diese Einstellungen werden einem Gerätekonfigurationsprofil in Intune hinzugefügt und dann Ihren iOS/iPadOS-Geräten zugewiesen oder auf diesen bereitgestellt.

> [!TIP]
> Für diese Einstellungen werden die MDM-Einstellungen von Apple verwendet. Weitere Informationen zu diesen Einstellungen finden Sie auf der Apple-Website zu den [MDM-Einstellungen von Apple](https://support.apple.com/guide/mdm/welcome/web).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Konfigurationsprofil mit Geräteeinschränkungen](../device-restrictions-configure.md).

> [!NOTE]
> Diese Einstellungen gelten für verschiedene Registrierungstypen, wobei einige Einstellungen für alle Registrierungsoptionen gelten. Weitere Informationen zu den verschiedenen Registrierungstypen finden Sie unter [iOS/iPadOS-Registrierung](../ios-enroll.md).

## <a name="general"></a>Allgemein

### <a name="settings-apply-to-all-enrollment-types"></a>Die Einstellungen gelten für: Alle Registrierungstypen

- **Nutzungsdaten freigeben**: Wählen Sie **Blockieren** aus, um zu verhindern, dass das Gerät Diagnose- und Nutzungsdaten an Apple sendet. **Nicht konfiguriert** (Standard) erlaubt das Senden dieser Daten.

- **Bildschirmaufnahme:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Screenshots oder Bildschirmaufnahmen auf dem Gerät vorgenommen werden. Ab iOS/iPadOS 9.0 werden auch Bildschirmaufzeichnungen blockiert. **Nicht konfiguriert** (Standard) erlaubt dem Benutzer, den Bildschirminhalt als Bild oder Video zu erfassen.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **Nicht vertrauenswürdige TLS-Zertifikate:** Wählen Sie **Blockieren** aus, um zu verhindern, dass nicht vertrauenswürdige TLS-Zertifikate (Transport Layer Security) auf das Gerät gelangen. Die Standardeinstellung **Nicht konfiguriert** lässt TLS-Zertifikate zu.
- **Drahtlose PKI-Updates blockieren**: **Blockieren**: Verhindert, dass Ihre Benutzer Softwareupdates erhalten, wenn das Gerät nicht an einen Computer angeschlossen ist. **Nicht konfiguriert** (Standardeinstellung): Ermöglicht es einem Gerät, Softwareupdates zu empfangen, ohne mit einem Computer verbunden zu sein.
- **Anzeigennachverfolgung begrenzen:** Wählen Sie **Limit** aus, um den Advertising Identifier eines Gerätes zu deaktivieren. Die Standardeinstellung **Nicht konfiguriert** behält die Aktivierung bei.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Automatisierte Geräteregistrierung (überwacht)

- **Änderung der Einstellungen zur Diagnoseübermittlung**: **Blockieren** verhindert, dass der Benutzer in den Geräteeinstellungen in **Diagnose & Nutzung** Änderungen an den Einstellungen für Diagnoseübermittlung und App-Analyse vornimmt. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Geräteeinstellungen zu ändern.

  Legen Sie **Blockieren** für die Einstellung **Nutzungsdaten freigeben** fest, um diese Einstellung zu verwenden.

  Diese Funktion gilt für:  
  - iOS 9.3.2 und neuer
  - iOS 13.0 und höher

- **Beobachtung von Remotebildschirmen durch Classroom-App**: Wählen Sie **Blockieren** aus, um zu verhindern, dass die Classroom-App den Bildschirm des Geräts remote anzeigt. **Nicht konfiguriert** (Standard) erlaubt der Classroom-App von Apple, den Bildschirm anzuzeigen.

  Legen Sie **Blockieren** für die Einstellung **Bildschirmaufnahme** fest, um diese Einstellung zu verwenden.

  Diese Funktion gilt für:  
  - iOS 9.3 und höher
  - iOS 13.0 und höher

- **Unangekündigte Bildschirmüberwachung über Classroom-App**: Wenn diese Einstellung auf **Zulassen** festgelegt wird, können Lehrkräfte die Bildschirme der iOS/iPadOS-Geräte ihrer Kursteilnehmer mithilfe der Classroom-App überwachen, ohne dass die Kursteilnehmer dies mitbekommen. In einer Klasse registrierte Kursteilnehmergeräte, die die Classroom-App verwenden, gewähren der Lehrkraft des Kurses automatisch die Berechtigung. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature deaktiviert.

  Legen Sie **Blockieren** für die Einstellung **Bildschirmaufnahme** fest, um diese Einstellung zu verwenden.

- **Vertrauen für Unternehmens-App:** Wählen Sie **Blockieren** aus, um die Schaltfläche **Trust Enterprise Developer** (Unternehmensentwickler vertrauen) über „Einstellungen > Allgemein > Profile & Geräteverwaltung“ auf dem Gerät zu entfernen. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer zu wählen, ob Apps, die nicht aus dem App Store heruntergeladen wurden, vertraut werden soll.
- **Kontoänderung**: Bei Festlegung auf **Blockieren** kann der Benutzer die gerätespezifischen Einstellungen nicht über die iOS/iPadOS-App „Einstellungen“ aktualisieren. Der Benutzer kann z. B. nicht neue Gerätekonten erstellen oder Benutzernamen bzw. Kennwort ändern. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Einstellungen zu ändern.

  Diese Funktion gilt auch für Einstellungen, auf die über die iOS/iPadOS-App „Einstellungen“ zugegriffen werden kann, wie z. B. E-Mail, Kontakte, Kalender, Twitter und mehr. Diese Funktion gilt nicht für Apps mit Kontoeinstellungen, die nicht über die iOS/iPadOS-App „Einstellungen“ konfiguriert werden können, wie z. B. die Microsoft Outlook-App.

- **Bildschirmzeit**: Wählen Sie **Blockieren**, um zu verhindern, dass Benutzer ihre eigenen Einschränkungen in „Bildschirmzeit“ (Geräteeinstellungen) vornehmen. **Nicht konfiguriert** erlaubt dem Benutzer das Konfigurieren von Geräteeinschränkungen (z. B. Jugendschutz oder Inhalts- und Datenschutzeinschränkungen) auf dem Gerät.

  Diese Einstellung hieß zuvor **Aktivieren von Einschränkungen in den Geräteeinstellungen**. Auswirkungen dieser Änderung:  
  
  - iOS 11.4.1 und älter: Durch die Option **Blockieren** kann verhindert werden, dass Endbenutzer die für sie geltenden Einschränkungen in den Geräteeinstellungen bearbeiten. Dieses Verhalten bewirkt dasselbe, sodass es keine Änderungen für Endbenutzer gibt.
  - iOS 12.0 und höher: **Blockieren** verhindert, dass Endbenutzer die für sie geltende **Bildschirmzeit** (einschließlich Einschränkungen von Inhalt und Datenschutz) in den Geräteeinstellungen (Einstellungen > Allgemein > Bildschirmzeit) bearbeiten. Bei auf iOS 12.0 aktualisierten Geräten wird die Registerkarte „Einschränkungen“ in den Geräteeinstellungen nicht mehr angezeigt (Einstellungen > Allgemein > Geräteverwaltung > Verwaltungsprofil > Einschränkungen). Diese Einstellungen befinden sich unter **Bildschirmzeit**.
  
- **Verwendung der Option zum Löschen aller Inhalte und Einstellungen auf dem Gerät**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer die Option zum Löschen aller Inhalte und Einstellungen auf dem Gerät verwenden können. **Nicht konfiguriert** (Standard) ermöglicht Benutzern den Zugriff auf diese Einstellungen.
- **Bearbeitung des Gerätenamens:** Wählen Sie **Blockieren** aus, damit der Gerätename nicht geändert werden kann. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, den Namen des Geräts zu ändern.
- **Änderung der Benachrichtigungseinstellungen**: Wählen Sie **Blockieren** aus, damit die Benachrichtigungseinstellungen nicht geändert werden können. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, die Benachrichtigungseinstellungen des Geräts zu ändern.
- **Hintergrundbild ändern**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Hintergrundbilder geändert werden können. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, das Hintergrundbild des Geräts zu ändern.
- **Änderung der Vertrauenseinstellungen für Unternehmens-Apps**: **Blockieren** verhindert, dass der Benutzer die Vertrauensstellungseinstellungen für die Unternehmens-App auf überwachten Geräten ändert. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, Apps zu vertrauen, die nicht aus dem App Store heruntergeladen wurden.
- **Konfigurationsprofiländerungen**: **Blockieren** verhindert Konfigurationsprofiländerungen auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, Konfigurationsprofile zu installieren.
- **Aktivierungssperre**: Wählen Sie **Zulassen** aus, um die Aktivierungssperre auf überwachten iOS/iPadOS-Geräten zu aktivieren. Die Aktivierungssperre erschwert die erneute Aktivierung verlorener oder gestohlener Geräte.
- **Entfernen von Apps blockieren**: Wenn Sie **Blockieren** auswählen, können Benutzer keine Apps entfernen. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, Apps vom Gerät zu entfernen.
- **USB-Zubehör bei gesperrtem Gerät zulassen**: **Zulassen**: USB-Zubehör kann Daten mit einem Gerät austauschen, das seit mehr als einer Stunde gesperrt ist. **Nicht konfiguriert** (Standardeinstellung): Der Modus mit USB-Einschränkung auf dem Gerät wird nicht aktualisiert, und USB-Zubehör wird daran gehindert, Daten vom Gerät zu übertragen, wenn dieses länger als eine Stunde gesperrt ist.
- **Automatische Datums- und Uhrzeiteinstellung erzwingen**: **Anfordern** erzwingt, dass überwachte Geräte das Datum und die Uhrzeit automatisch einstellen. Die Zeitzone für das Gerät wird aktualisiert, wenn das Gerät über Mobilfunkverbindungen verfügt oder WLAN mit Standortdiensten aktiviert ist.
- **Erlaubnis für Kursteilnehmer vor dem Verlassen des Classroom-Kurses erforderlich**: **Anfordern** erzwingt, dass in einem nicht verwalteten Kurs registrierte Kursteilnehmer, die die Classroom-App verwenden, vom Kursleiter eine Berechtigung zum Verlassen des Kurses anfordern müssen. **Nicht konfiguriert** (Standard) erzwingt nicht, dass Kursteilnehmer um eine Berechtigung bitten müssen.

  Diese Funktion gilt für:  
  - iOS 11.3 und neuer
  - iOS 13.0 und höher

- **Das Beschränken von Classroom auf eine App und das Sperren von Geräten ohne vorherige Aufforderung zulassen**: **Aktivieren** ermöglicht Lehrkräften das Sperren von Apps oder das Sperren des Geräts mithilfe der Classroom-App, ohne den Kursteilnehmer aufzufordern. Das Sperren von Apps bedeutet, dass das Gerät nur auf die von der Lehrkraft angegebenen Apps zugreifen kann. Die Standardeinstellung **Nicht konfiguriert** verhindert, dass Lehrkräfte Anwendungen oder Geräte, die die Classroom-App verwenden, sperren, ohne die Lernenden zu fragen.

  Diese Funktion gilt für:  
  - iOS 11.0 und neuer
  - iOS 13.0 und höher

- **Classroom-Kursen automatisch ohne Aufforderung beitreten**: **Aktivieren** erlaubt es Lernenden, einem Kurs in der Classroom-App automatisch beizutreten, ohne die Lehrkraft zu fragen. In der Standardeinstellung **Nicht konfiguriert** wird die Lehrkraft gefragt, wenn Lernende einem Kurs in der Classroom-App beitreten möchten.

  Diese Funktion gilt für:  
  - iOS 11.0 und neuer
  - iOS 13.0 und höher

- **VPN-Erstellung blockieren**: **Blockieren** hindert Benutzer daran, VPN-Konfigurationseinstellungen zu erstellen. **Nicht konfiguriert** (Standard) ermöglicht Benutzern das Erstellen von VPNs auf dem Gerät.
- **eSIM-Einstellungen ändern**: **Blockieren** hindert Benutzer am Entfernen oder Hinzufügen eines Mobilfunktarifplans zum eSIM auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Einstellungen zu ändern.

  Diese Funktion gilt für:  
  - iOS 12.1 und neuer
  - iOS 13.0 und höher

- **Softwareupdates zurückstellen**: In der Standardeinstellung **Nicht konfiguriert** werden Softwareupdates auf dem Gerät angezeigt, sobald Apple sie veröffentlicht. Wenn beispielsweise ein iOS/iPadOS-Update von Apple an einem bestimmten Datum veröffentlicht wird, wird dieses Update normalerweise am Veröffentlichungsdatum auf dem Gerät angezeigt.

  **Aktivieren** ermöglicht Ihnen, die Anzeige von Softwareupdates auf Geräten zu verzögern (0-90 Tage). Diese Einstellung steuert nicht, ob Updates installiert werden oder nicht. 

  - **Sichtbarkeit von Softwareupdates verzögern**: Geben Sie einen Wert zwischen 0–90 Tagen ein. Nach der Verzögerung erhalten Benutzer eine Benachrichtigung für ein Update auf die früheste Version des Betriebssystems, die verfügbar war, als die Verzögerung ausgelöst wurde.

    Wenn beispielsweise iOS 12.a am **1. Januar** verfügbar ist und **Sichtbarkeit verzögern** auf **5 Tage** festgelegt ist, wird iOS 12.a nicht als verfügbares Update auf Endbenutzergeräten angezeigt. Am **6. Tag** nach Veröffentlichung ist dieses Update verfügbar, sodass Endbenutzer es installieren können.

    Diese Einstellung gilt für:  
    - iOS 11.3 und neuer
    - iOS 13.0 und höher

## <a name="password"></a>Kennwort

### <a name="settings-apply-to-all-enrollment-types"></a>Die Einstellungen gelten für: Alle Registrierungstypen

- **Kennwort:** **Anfordern** der Kennworteingabe durch den Endbenutzer für den Zugriff auf das Gerät. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, ohne Kennworteingabe auf das Gerät zuzugreifen.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

> [!IMPORTANT]
> Wenn Sie auf von Benutzern registrierten Geräten eine Kennworteinstellung konfigurieren, wird die Einstellung **Einfache Kennwörter** automatisch auf **Blockieren** festgelegt und eine sechsstellige PIN erzwungen.
>
> Sie konfigurieren beispielsweise die Einstellung **Kennwortablauf** und übertragen diese Richtlinie per Push auf vom Benutzer registrierte Geräte. Auf diesen Geräten geschieht Folgendes:
>
> - Die Einstellung **Kennwortablauf** wird ignoriert.
> - Einfache Passwörter wie `1111` oder `1234` sind nicht zulässig.
> - Eine sechsstellige PIN wird erzwungen.

- **Einfache Kennwörter:** Wählen Sie **Blockieren** aus, um komplexere Kennwörter zu erzwingen. **Nicht konfiguriert** ermöglicht einfache Kennwörter wie z. B. `0000` und `1234`.

- **Erforderlicher Kennworttyp:** Wählen Sie den Kennworttyp aus, den Ihre Organisation fordert. Folgende Optionen sind verfügbar:
  - **Gerätestandard**
  - **Numerisch**
  - **Alphanumerisch**
- **Anzahl nicht alphanumerischer Zeichen im Kennwort:** Geben Sie die Anzahl von Symbolzeichen wie `#` oder `@` an, die im Kennwort enthalten sein müssen.

- **Minimale Kennwortlänge:** Geben Sie die Mindestanzahl von Zeichen ein, die Benutzer für das Kennwort eingeben müssen (zwischen 4 und 14 Zeichen). Geben Sie auf von Benutzern registrierten Geräten eine Länge von 4 bis 6 Zeichen an.
  
  > [!NOTE]
  > Bei Geräten, die vom Benutzer registriert werden, können Benutzer eine PIN angeben, die länger als 6 Zeichen ist. Es werden jedoch nicht mehr als 6 Zeichen auf dem Gerät erzwungen. Wenn ein Administrator die Mindestlänge beispielsweise auf `8` festlegt, müssen Benutzer von Geräten mit Benutzerregistrierung eine PIN mit nur 6 Ziffern festlegen. Intune erzwingt auf von Benutzern registrierten Geräten keine PINs, die länger als 6 Zeichen sind.

- **Anzahl von fehlgeschlagenen Anmeldungen, bevor das Gerät zurückgesetzt wird:** Geben Sie die Anzahl der Anmeldungen ein, die fehlschlagen können, bevor das Gerät zurückgesetzt wird (zwischen 4 und 11).
  
  Die integrierte iOS/iPadOS-Sicherheit kann sich auf diese Einstellung auswirken. iOS/iPadOS kann die Auslösung der Richtlinie beispielsweise je nach Anzahl der Anmeldefehler verzögern. Die wiederholte Eingabe desselben Kennworts kann beispielsweise auch als ein Versuch anerkannt werden. Der [iOS/iPadOS-Sicherheitsleitfaden von Apple](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) (Apple-Website) ist eine gute Ressource mit ausführlichen Informationen zu Passcodes.
  
- **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts<sup>1</sup>:** Geben Sie an, wie lange das Gerät im Leerlauf bleiben kann, bevor der Benutzer sein Kennwort erneut eingeben muss. Wenn Sie einen längeren Zeitraum eingeben, als derzeit auf dem Gerät eingestellt ist, ignoriert das Gerät Ihre Eingabe. Unterstützt auf Geräten mit iOS 8.0+ und iPadOS 13.0+.

- **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung<sup>1</sup>:** Geben Sie an, wie viele Minuten ein Gerät höchstens inaktiv sein darf, bevor es automatisch gesperrt wird.

  **iOS/iPadOS-Optionen:**  

  - **Nicht konfiguriert** (Standard): Diese Einstellung wird von Intune nicht verändert.
  - **Sofort:** Der Bildschirm wird nach 30 Sekunden Inaktivität gesperrt.
  - **1:** Der Bildschirm wird nach einer Minute Inaktivität gesperrt.
  - **2:** Der Bildschirm wird nach zwei Minuten Inaktivität gesperrt.
  - **3:** Der Bildschirm wird nach drei Minuten Inaktivität gesperrt.
  - **4**: Der Bildschirm wird nach vier Minuten Inaktivität gesperrt.
  - **5:** Der Bildschirm wird nach fünf Minuten Inaktivität gesperrt.

  **iPadOS-Optionen:**  

  - **Nicht konfiguriert** (Standard): Diese Einstellung wird von Intune nicht verändert.
  - **Sofort:** Der Bildschirm wird nach zwei Minuten Inaktivität gesperrt.
  - **2:** Der Bildschirm wird nach zwei Minuten Inaktivität gesperrt.
  - **5:** Der Bildschirm wird nach fünf Minuten Inaktivität gesperrt.
  - **10:** Der Bildschirm wird nach zehn Minuten Inaktivität gesperrt.
  - **15:** Der Bildschirm wird nach 15 Minuten Inaktivität gesperrt.

  Wenn ein Wert nicht für iOS und iPadOS zulässig ist, verwendet Apple den *niedrigsten* nächstgelegenen Wert. Wenn Sie beispielsweise `4` Minuten angeben, verwenden iPadOS-Geräte `2` Minuten. Wenn Sie `10` Minuten angeben, verwenden iOS-Geräte `5` Minuten. Dies ist eine Apple-Einschränkung.
  
  > [!NOTE]
  > Die Benutzeroberfläche von Intune für diese Einstellung trennt die von iOS und iPadOS unterstützten Werte nicht voneinander. Diese Benutzeroberfläche wird in einem zukünftigen Release möglicherweise aktualisiert.

- **Kennwortablauf (Tage):** Geben Sie die Anzahl der Tage an, bis das Gerätekennwort geändert werden muss.
- **Wiederverwendung vorheriger Kennwörter verhindern:** Geben Sie die Anzahl neuer Kennwörter ein, die verwendet werden müssen, bevor ein altes Kennwort wiederverwendet werden darf.
- **Touch ID und Face ID entsperren:** Wählen Sie **Blockieren** aus, um die Verwendung eines Fingerabdrucks oder eines Gesichts zum Entsperren des Geräts zu verhindern. **Nicht konfiguriert** ermöglicht dem Benutzer das Entsperren des Geräts mittels dieser Methoden.

  Wenn Sie diese Einstellung blockieren, wird auch die Verwendung der Face ID-Authentifizierung zum Entsperren des Geräts verhindert.

  Face ID gilt für:  
  - iOS 11.0 und neuer
  - iOS 13.0 und höher

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Automatisierte Geräteregistrierung (überwacht)

- **Passcodeänderung**: Wählen Sie **Blockieren** aus, damit die Kennung nicht geändert, hinzugefügt oder entfernt werden kann. Änderungen an Kennungseinschränkungen werden nach der Blockierung dieser Funktion auf überwachten Geräten ignoriert. **Nicht konfiguriert** (Standard) ermöglicht, Passcodes hinzuzufügen, zu ändern oder zu entfernen.

  - **Touch-ID and Face-ID-Änderungen:** Die Option **Blockieren** hindert den Benutzer daran, TouchID-Fingerabdrücke und Face ID zu ändern, hinzuzufügen oder zu entfernen. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer das Aktualisieren der TouchID-Fingerabdrücke und Face ID auf dem Gerät.

    Wenn Sie diese Einstellung blockieren, können Benutzer die Face ID-Authentifizierung nicht ändern, hinzufügen oder entfernen.

    Face ID gilt für:  
    - iOS 11.0 und neuer
    - iOS 13.0 und höher

- **AutoAusfüllen für Kennwörter blockieren**: Wählen Sie **Blockieren** aus, um die Verwendung des Features zum automatischen Ausfüllen von Kennwörtern unter iOS/iPadOS zu verhindern. Das Wählen von **Blockieren** bewirkt auch Folgendes:

  - Benutzer werden nicht aufgefordert, in Safari oder beliebigen Apps gespeicherte Kennwörter zu verwenden.
  - Automatische sichere Kennwörter sind deaktiviert, und sichere Kennwörter werden Benutzern nicht empfohlen.

  **Nicht konfiguriert** (Standard) lässt diese Funktionen zu.

- **Kennwortanforderungen durch Näherung blockieren**: Wählen Sie **Blockieren** aus, damit das Gerät eines Benutzers keine Kennwörter von in der Nähe befindlichen Geräten anfordert. **Nicht konfiguriert** (Standard) lässt diese Kennwortanforderungen zu.
- **Kennwortfreigabe blockieren**: **Blockieren** verhindert die Freigabe von Kennwörtern zwischen Geräten mit AirDrop. **Nicht konfiguriert** (Standard) ermöglicht die Freigabe von Kennwörtern.
- **Authentifizierung über Touch-ID oder Face-ID für AutoAusfüllen von Kennwörtern und Kreditkarteninformationen erforderlich**: Bei Festlegung auf **Anfordern** müssen sich Benutzer mit TouchID oder FaceID authentifizieren, bevor Kennwörter oder Kreditkarteninformationen in Safari und anderen Anwendungen automatisch eingefügt werden können. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern, diese Funktion in den Geräteeinstellungen zu steuern.

  Diese Funktion gilt für:  
  - iOS 11.0 und neuer
  - iOS 13.0 und höher
  
<sup>1</sup> Wenn Sie die Einstellungen **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung** und **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts** konfigurieren, werden diese nacheinander angewendet. Wenn Sie beispielsweise den Wert für beide Einstellungen auf **5** Minuten einstellen, wird der Bildschirm automatisch nach fünf Minuten deaktiviert, und das Gerät wird nach weiteren fünf Minuten gesperrt. Wenn der Benutzer den Bildschirm jedoch manuell deaktiviert, wird die zweite Einstellung sofort angewendet. Im selben Beispiel wird das Gerät fünf Minuten später gesperrt, nachdem der Benutzer den Bildschirm deaktiviert hat.

## <a name="locked-screen-experience"></a>Benutzererfahrung „Gesperrter Bildschirm“

### <a name="settings-apply-to-all-enrollment-types"></a>Die Einstellungen gelten für: Alle Registrierungstypen

- **Kontrollcenterzugriff bei gesperrtem Gerät:** Wählen Sie **Blockieren** aus, um den Zugriff auf die Kontrollcenter-App zu verhindern, während das Gerät gesperrt ist. **Nicht konfiguriert** (Standard) erlaubt dem Benutzer den Zugriff auf die Kontrollcenter-App, während das Gerät gesperrt ist.
- **Benachrichtigungen bei Gerätesperre:** **Blockieren** verhindert den Zugriff auf Benachrichtigungen, wenn das Gerät gesperrt ist. **Nicht konfiguriert** (Standard) erlaubt dem Benutzer den Zugriff auf die Benachrichtigungen, ohne dass das Gerät entsperrt werden muss.
- **Ansicht „Heute“ bei Gerätesperre:** **Blockieren** verhindert den Zugriff auf die Ansicht „Heute“, wenn das Gerät gesperrt ist. **Nicht konfiguriert** (Standard) erlaubt dem Benutzer den Zugriff auf die Ansicht „Heute“, während das Gerät gesperrt ist.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **Wallet-Benachrichtigungen bei gesperrtem Gerät:** **Blockieren** verhindert den Zugriff auf die Wallet-App, wenn das Gerät gesperrt ist. **Nicht konfiguriert** (Standard) erlaubt dem Benutzer den Zugriff auf die Wallet-App, während das Gerät gesperrt ist.

## <a name="app-store-doc-viewing-gaming"></a>App Store, Dokumentanzeige, Spiele

### <a name="settings-apply-to-all-enrollment-types"></a>Die Einstellungen gelten für: Alle Registrierungstypen

- **Anzeige von Unternehmensdokumenten in nicht verwalteten Apps:** **Blockieren** verhindert die Anzeige unternehmenseigener Dokumente in nicht verwalteten Apps. **Nicht konfiguriert** (Standard) gestattet die Anzeige von Unternehmensdokumenten in beliebigen Apps. Beispiel: Sie möchten verhindern, dass Benutzer Dateien aus der OneDrive-App in Dropbox speichern. Legen Sie für diese Einstellung **Blockieren** fest. Sobald das Gerät die Richtlinie empfängt (z. B. nach einem Neustart), ist kein Speichern mehr möglich.


  > [!NOTE]
  > Wenn diese Einstellung blockiert wird, werden Tastaturen von Drittanbietern, die über den App Store installiert wurden, ebenfalls blockiert.

  - **Lesen aus verwalteten Kontaktkonten für nicht verwaltete Apps zulassen**: Wenn **Zulassen** für diese Einstellung festgelegt wird, können nicht verwaltete Apps wie die integrierte iOS/iPadOS-App „Kontakte“ Kontaktinformationen aus verwalteten Apps wie der mobilen Outlook-App lesen und auf diese zugreifen. **Nicht konfiguriert** (Standard) verhindert, dass die integrierte App „Kontakte“ auf dem Gerät gelesen oder Duplikate entfernt werden können.  
  
    Mit dieser Einstellung kann das Lesen von Kontaktinformationen zugelassen oder verhindert werden. Das Synchronisieren von Kontakten zwischen den Apps wird nicht von dieser Einstellung gesteuert.
  
    Wenn Sie diese Einstellung verwenden möchten, legen Sie die Einstellung **Anzeige von Unternehmensdokumenten in nicht verwalteten Apps**auf **Blockieren** fest.

  Weitere Informationen zu diesen beiden Einstellungen und deren Auswirkung auf die Kontaktexportsynchronisierung von Outlook für iOS/iPadOS finden Sie unter [Tipp zur Unterstützung: Verwenden von benutzerdefinierten Intune-Profileinstellungen mit der nativen iOS/iPadOS-App „Kontakte“](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453).

- **AirDrop als nicht verwaltetes Ziel behandeln:** **Anfordern** erzwingt, dass AirDrop als nicht verwaltetes Drop-Ziel behandelt wird. Es hindert verwaltete Apps daran, Daten mithilfe von AirDrop zu senden. 
- **Anzeige nicht unternehmenseigener Dokumente in Unternehmens-Apps:** **Blockieren** verhindert, dass nicht unternehmenseigene Dokumente in Unternehmens-Apps angesehen werden können. **Nicht konfiguriert** (Standard) gestattet die Anzeige beliebiger Dokumente in verwalteten Unternehmens-Apps.

  Wenn Sie **Blockieren** für diese Einstellung festlegen, wird auch die Kontaktexportsynchronisierung in Outlook für iOS/iPadOS verhindert. Weitere Informationen finden Sie unter [Tipp zur Unterstützung: Aktivieren der Kontaktsynchronisierung von Outlook für iOS/iPadOS mit iOS12-MDM-Steuerelementen](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Enabling-Outlook-iOS-Contact-Sync-with-iOS12-MDM/ba-p/298453).

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **iTunes Store-Kennwort für alle Käufe erforderlich:** Wenn **Erforderlich** festgelegt wird, muss der Benutzer seine Apple-ID und sein Kennwort für jeden In-App- oder iTunes-Kauf eingeben. **Nicht konfiguriert** (Standardeinstellung): Bei dieser Einstellungen wird kein Kennwort für Käufe angefordert.
- **In-App-Einkäufe:** Wählen Sie **Blockieren** aus, um In-App-Einkäufe im Store zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht Einkäufe im Store in einer ausgeführten App.
- **Download content from iBook store flagged as 'Erotica'** (Als „Erotik“ gekennzeichneten Inhalt aus dem iBooks Store herunterladen): Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer Medien aus dem iBook Store herunterladen, die als „Erotik“ gekennzeichnet sind. **Nicht konfiguriert** (Standard) gestattet dem Benutzer das Herunterladen von Büchern aus der Kategorie „Erotik“.
- **Schreiben von Kontakten in nicht verwaltete Kontaktkonten für verwaltete Apps zulassen**: Wenn **Zulassen** für diese Einstellung festgelegt wird, können verwaltete Apps wie die mobile Outlook-App Kontaktinformationen (einschließlich Geschäftskontakte) in der integrierten iOS/iPadOS-App „Kontakte“ speichern oder mit ihr synchronisieren. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt wird, können verwaltete Apps Kontaktinformationen nicht in der integrierten iOS/iPadOS-App „Kontakte“ auf dem Gerät speichern oder mit dieser synchronisieren.
  
  Wenn Sie diese Einstellung verwenden möchten, legen Sie die Einstellung **Anzeige von Unternehmensdokumenten in nicht verwalteten Apps**auf **Blockieren** fest.

- **Bewertungsregion:** Wählen Sie die Bewertungsregion aus, die Sie für zulässige Downloads verwenden möchten. Wählen Sie dann die zulässigen Bewertungen für **Filme**, **Fernsehsendungen** und **Apps** aus.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Automatisierte Geräteregistrierung (überwacht)

- **App Store:** **Blockieren** verhindert, dass auf überwachten Geräten auf den App Store zugegriffen werden kann. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.

  Ab iOS/iPadOS 13.0 muss es sich bei Geräten mit dieser Einstellung um überwachte Geräte handeln.

  - **Installieren von Apps über den App Store**: Wählen Sie **Blockieren** aus, um den App Store auf dem Startbildschirm des Geräts zu blockieren. Endbenutzer können weiterhin iTunes oder das Apple Configurator-Tool zum Installieren von Apps verwenden. **Nicht konfiguriert** (Standard) lässt den App Store auf dem Startbildschirm zu.
  - **Automatische App-Downloads**: Wählen Sie **Blockieren** aus, um den automatischen Download von Apps zu verhindern, die auf anderen Geräten erworben wurden. Updates vorhandener Apps sind nicht betroffen. **Nicht konfiguriert** (Standard) ermöglicht, Apps auf das Gerät herunterzuladen, die auf anderen iOS/iPadOS-Geräten gekauft wurden.

- **Anstößige iTunes-Musik, Podcasts oder Nachrichteninhalte**: Wählen Sie **Blockieren** aus, um anstößige iTunes-Musik, Podcasts oder Nachrichteninhalte zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht, dass das Gerät im Store auf nicht jugendfreie Inhalte zugreift.

  Ab iOS/iPadOS 13.0 muss es sich bei Geräten mit dieser Einstellung um überwachte Geräte handeln.

- **Hinzufügen von Game Center-Freunden**: **Blockieren** verhindert, dass Benutzer Game Center-Freunde hinzufügen können. **Nicht konfiguriert** (Standard) gestattet dem Benutzer, im Game Center Freunde hinzuzufügen.

  Ab iOS/iPadOS 13.0 muss es sich bei Geräten mit dieser Einstellung um überwachte Geräte handeln.

- **Game Center**: **Blockieren** verhindert, dass die Game Center-App verwendet werden kann. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der Game Center-App auf dem Gerät.
- **Multiplayerspiele:** Wählen Sie **Blockieren** aus, um Multiplayerspiele zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht, dass der Benutzer Multiplayerspiele auf dem Gerät spielt.

  Ab iOS/iPadOS 13.0 muss es sich bei Geräten mit dieser Einstellung um überwachte Geräte handeln.

- **Zugriff auf Netzlaufwerk in Dateien-App:** Mithilfe des SMB-Protokolls (Server Message Block) können Geräte auf Dateien und andere Ressourcen auf einem Netzwerkserver zugreifen. Wenn **Deaktivieren** für diese Einstellung festgelegt wird, wird der Zugriff auf Dateien auf einem SMB-Netzwerklaufwerk verhindert. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.

  Diese Funktion gilt für:  
  - iOS 13.0 und neuer
  - iOS 13.0 und höher

## <a name="built-in-apps"></a>Integrierte Apps

### <a name="settings-apply-to-all-enrollment-types"></a>Die Einstellungen gelten für: Alle Registrierungstypen

- **Siri:** **Blockieren** verhindert den Zugriff auf Siri. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung des Sprach-Assistenten Siri auf dem Gerät.
  - **Siri bei Gerätesperre:** Wählen Sie **Blockieren** aus, um den Zugriff auf Siri zu verhindern, wenn das Gerät gesperrt ist. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung des Sprach-Assistenten Siri auf dem Gerät, wenn das Gerät gesperrt ist.

- **Safari-Betrugswarnungen**: **Anfordern**, dass Betrugswarnungen im Webbrowser auf dem Gerät angezeigt werden. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird dieses Feature deaktiviert.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **Spotlight-Suche gibt Ergebnisse aus dem Internet zurück**: **Blockieren** verhindert, dass Spotlight Ergebnisse einer Internetsuche zurückgibt. **Nicht konfiguriert** (Standard) ermöglicht der Spotlight-Suchfunktion das Herstellen einer Verbindung mit dem Internet zur Bereitstellung von Suchergebnissen.

- **Safari-Cookies**: Wählen Sie aus, wie Cookies auf dem Gerät behandelt werden. Folgende Optionen sind verfügbar:
  - Zulassen
  - Alle Cookies blockieren
  - Cookies von besuchten Websites zulassen
  - Cookies von aktueller Website zulassen

- **Safari-JavaScript**: **Blockieren** verhindert, dass auf dem Gerät Java-Skripts im Browser ausgeführt werden. Bei der Standardeinstellung **Nicht konfiguriert** werden Java-Skripts zugelassen.

- **Safari-Popups**: **Blockieren** deaktiviert den Popupblocker im Webbrowser. Bei der Standardeinstellung **Nicht konfiguriert** wird der Popupblocker zugelassen.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Automatisierte Geräteregistrierung (überwacht)

- **Kamera:** Wählen Sie **Blockieren** aus, um den Zugriff auf die Kamera des Geräts zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf die Kamera des Geräts.

  Ab iOS/iPadOS 13.0 muss es sich bei Geräten mit dieser Einstellung um überwachte Geräte handeln.

  - **FaceTime:** Mit **Blockieren** verhindern Sie den Zugriff auf die FaceTime-App. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf die FaceTime-App des Geräts.

    Ab iOS/iPadOS 13.0 muss es sich bei Geräten mit dieser Einstellung um überwachte Geräte handeln.

- **Siri-Filter für anstößige Ausdrücke**: **Anfordern** verhindert, dass Siri anstößige Ausdrücke diktiert oder verwendet.

  Legen Sie **Blockieren** für die **Siri**-Einstellung fest, um diese Einstellung zu verwenden.

- **Abfrage von benutzergenerierten Inhalten aus dem Internet durch Siri**: **Blockieren** verhindert, dass Siri auf Websites zugreifen darf, um Fragen zu beantworten. **Nicht konfiguriert** (Standard) ermöglicht Siri, auf benutzergenerierten Inhalt aus dem Internet zuzugreifen.

  Legen Sie **Blockieren** für die **Siri**-Einstellung fest, um diese Einstellung zu verwenden.

- **Apple News**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Apple News-App des Geräts zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der Apple News-App.
- **iBooks Store**: **Blockieren** verhindert, dass auf den iBooks-Store zugegriffen werden kann. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, den iBooks Store zu durchsuchen und dort Bücher zu erwerben.
- **Nachrichten-App auf dem Gerät:** Wenn **Blockieren** für diese Einstellung festgelegt wird, werden Benutzer daran gehindert, die Nachrichten-App für iMessage zu verwenden. Wenn das Gerät Textnachrichten unterstützt, kann der Benutzer weiterhin Textnachrichten per SMS senden und empfangen. **Nicht konfiguriert** (Standardeinstellung): Diese Einstellung ermöglicht die Verwendung der Nachrichten-App zum Senden und Empfangen von Nachrichten über das Internet.
- **Podcasts**: **Blockieren** hindert Benutzer an der Verwendung der Podcasts-App. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der Podcasts-App.
- **Musikdienst**: **Blockieren** setzt die Musik-App in den klassischen Modus zurück und deaktiviert den Musikdienst. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der Apple Music-App.
- **iTunes Radio-Dienst**: **Blockieren** verhindert, dass Benutzer die iTunes Radio-App verwenden können. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der iTunes Radio-App.
- **iTunes Store:** Wenn **Nicht konfiguriert** (Standardeinstellung) festgelegt wird, wird iTunes auf den Geräten zugelassen. Wenn **Blockieren** festgelegt wird, können Benutzer iTunes nicht auf dem Gerät verwenden. 

  Diese Funktion gilt für:  
  - iOS 4.0 und neuer
  - iOS 13.0 und höher

- **Mein iPhone suchen:** Die Standardeinstellung **Nicht konfiguriert** erlaubt die Verwendung des App-Features „Wo ist?“ zum Abrufen des ungefähren Standorts des Geräts. Die Einstellung **Blockieren** verhindert die Verwendung dieses Features der App. 

  Diese Funktion gilt für:  
  - iOS 13.0 und neuer
  - iOS 13.0 und höher

- **Meine Freunde suchen:** Die Standardeinstellung **Nicht konfiguriert** erlaubt die Verwendung der App „Wo ist?“ zum Suchen von Familienmitgliedern und Freunden über ein Apple-Gerät oder iCloud.com. Die Einstellung **Blockieren** verhindert die Verwendung dieses Features der App.

  Diese Funktion gilt für:  
  - iOS 13.0 und neuer
  - iOS 13.0 und höher

- **Änderungen an den Einstellungen der App "Meine Freunde suchen"** : **Blockieren** verhindert, dass Änderungen an den Einstellungen der App „Meine Freunde suchen“ durchgeführt werden. **Nicht konfiguriert** (Standard) ermöglicht Benutzern das Ändern von Einstellungen für die App „Meine Freunde suchen“.

- **Spotlight-Suche gibt Ergebnisse aus dem Internet zurück**: **Blockieren** verhindert, dass Spotlight Ergebnisse einer Internetsuche zurückgibt. **Nicht konfiguriert** (Standard) ermöglicht der Spotlight-Suchfunktion das Herstellen einer Verbindung mit dem Internet zur Bereitstellung von Suchergebnissen.

- **Entfernen von System-Apps vom Gerät blockieren**: **Blockieren** deaktiviert die Möglichkeit, System-Apps auf dem Gerät zu entfernen. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, System-Apps zu entfernen.

- **Safari**: **Blockieren** der Verwendung des Safari-Browsers auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht Benutzern die Verwendung des Safari-Browsers.

  Ab iOS/iPadOS 13.0 muss es sich bei Geräten mit dieser Einstellung um überwachte Geräte handeln.

- **AutoAusfüllen in Safari**: **Blockieren** deaktiviert auf dem Gerät das AutoAusfüllen-Feature in Safari. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, die AutoAusfüllen-Einstellungen im Browser zu ändern.

  Ab iOS/iPadOS 13.0 muss es sich bei Geräten mit dieser Einstellung um überwachte Geräte handeln.

## <a name="restricted-apps"></a>Eingeschränkte Apps

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **Liste der eingeschränkten App-Typen:** Mit dieser Einstellung wird eine Liste der Apps erstellt, die Benutzer nicht installieren oder verwenden dürfen. Folgende Optionen sind verfügbar:

  - **Nicht konfiguriert** (Standardeinstellung): Bei dieser Einstellung liegen keine Einschränkungen durch Intune vor. Benutzer können auf integrierte Apps und Apps zugreifen, die Sie ihnen zuweisen.
  - **Unzulässige Apps:** Nicht von Intune verwaltete Apps, die nicht auf dem Gerät installiert werden sollen. Benutzer können unzulässige Apps nicht installieren. Wenn ein Benutzer jedoch eine App aus dieser Liste installiert, wird dies in Intune gemeldet.
  - **Genehmigte Apps:** Apps, die Benutzer installieren dürfen. Benutzer dürfen keine Apps installieren, die in dieser Liste nicht aufgeführt sind. Apps, die von Intune verwaltet werden, sind automatisch zugelassen. Benutzer werden nicht daran gehindert, eine App zu installieren, die nicht in der Liste zulässiger Apps enthalten ist. Wenn sie es jedoch tun, wird dies in Intune gemeldet.

Um diesen Listen Apps hinzuzufügen, können Sie:

- Die iTunes App-Store-URL der App **hinzufügen**, die Sie wünschen. Geben Sie beispielsweise zum Hinzufügen der Microsoft Work Folders-App `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` oder `https://apps.apple.com/us/app/work-folders/id950878067?mt=8` ein.

  Um die URL einer App zu suchen, öffnen Sie den iTunes App Store, und suchen Sie nach der App. Suchen Sie beispielsweise nach `Microsoft Remote Desktop` oder `Microsoft Word`. Wählen Sie die App aus, und kopieren Sie die URL.

  Sie können auch iTunes verwenden, um die App zu suchen, und dann die Aufgabe **Link kopieren**, um die App-URL abzurufen.

- **Importieren** Sie eine CSV-Datei mit den Details der App, einschließlich der URL. Verwenden Sie das Format `<app url>, <app name>, <app publisher>`. **Exportieren** Sie alternativ eine vorhandene Liste, die die Liste der eingeschränkten Apps im gleichen Format enthält.

> [!IMPORTANT]
> Geräteprofile, die Einstellungen für eingeschränkte Apps verwenden, müssen Benutzergruppen zugewiesen werden.

## <a name="show-or-hide-apps"></a>Apps ein- oder ausblenden

Gilt für Geräte, auf denen iOS 9.3+ und iPadOS 13.0+ ausgeführt wird.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Automatisierte Geräteregistrierung (überwacht)

- **Liste der App-Typen:** Mit dieser Einstellung wird eine Liste der anzuzeigenden oder auszublendenden Apps erstellt. Sie können sowohl integrierte Apps als auch branchenspezifische Apps anzeigen oder ausblenden. Eine Liste der integrierten Apple-Apps finden Sie auf [dieser Apple-Website](https://support.apple.com/HT208094). Folgende Optionen sind verfügbar:

  - **Ausgeblendete Apps:** Geben Sie eine Liste von Apps an, die für Benutzer ausgeblendet werden. Benutzer können diese Apps weder anzeigen noch öffnen.
  
    Apple verhindert, dass einige native Apps ausgeblendet werden. Beispielsweise können Sie die Apps **Einstellungen** und **Apple Wallet** nicht auf dem Gerät ausblenden. Unter [Delete built-in Apple apps](https://support.apple.com/HT208094) (Löschen integrierter Apple-Apps) werden alle Apps aufgeführt, die ausgeblendet werden können.
  
  - **Sichtbare Apps:** Geben Sie eine Liste von Apps an, die Benutzer anzeigen und starten können. Es können keine anderen Apps angezeigt oder gestartet werden.

- **App-URL**: Geben Sie die App Store-URLs der Apps ein, die angezeigt oder ausgeblendet werden sollen. Beispiel:

  - Geben Sie zum Hinzufügen der Microsoft Work Folders-App `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` oder `https://apps.apple.com/us/app/work-folders/id950878067?mt=8` ein. 

  - Geben Sie zum Hinzufügen der Microsoft Word-App `https://itunes.apple.com/de/app/microsoft-word/id586447913` oder `https://apps.apple.com/de/app/microsoft-word/id586447913` ein.

  Um die URL einer App zu suchen, öffnen Sie den iTunes App Store, und suchen Sie nach der App. Suchen Sie beispielsweise nach `Microsoft Remote Desktop` oder `Microsoft Word`. Wählen Sie die App aus, und kopieren Sie die URL.

  Sie können auch iTunes verwenden, um die App zu suchen, und dann die Aufgabe **Link kopieren**, um die App-URL abzurufen.

- **App-Bündel-ID:** Geben Sie die [App-Bündel-ID](bundle-ids-built-in-ios-apps.md) der gewünschten App ein. Sie können sowohl integrierte Apps als auch branchenspezifische Apps anzeigen oder ausblenden. Eine Liste der integrierten Apple-Apps finden Sie auf [dieser Apple-Website](https://support.apple.com/HT208094).
- **App-Name:** Geben Sie den App-Namen der gewünschten App ein. Sie können sowohl integrierte Apps als auch branchenspezifische Apps anzeigen oder ausblenden. Eine Liste der integrierten Apple-Apps finden Sie auf [dieser Apple-Website](https://support.apple.com/HT208094).
- **Herausgeber**: Geben Sie den Herausgeber der gewünschten App ein.

Apps können Sie wie folgt hinzufügen:

- **Hinzufügen**: Verwenden Sie diese Option, um Ihre Liste mit Apps zu erstellen.
- **Importieren** Sie eine CSV-Datei mit den Details der App, einschließlich der URL. Verwenden Sie das Format `<app url>, <app name>, <app publisher>`. Oder **exportieren** Sie eine Datei im selben Format, um eine Liste der hinzugefügten eingeschränkten Apps zu erstellen.

## <a name="wireless"></a>Drahtlos

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

Hinweis zum Datenroaming (Tipp oder wichtiger Hinweis, um Verwirrung beim Kunden zu vermeiden): Diese Einstellung wird im Verwaltungsprofil des Zielgeräts nicht angezeigt. Das liegt daran, dass diese Einstellung als Remotegeräteaktion behandelt wird, die jedes Mal erneut vom Intune-Dienst blockiert wird, wenn der Datenroamingstatus des Geräts geändert wird. Obwohl sich diese Einstellung nicht im Verwaltungsprofil befindet, funktioniert sie, wenn sie in der Verwaltungskonsole als erfolgreich gemeldet wird. 
- **Datenroaming:** Wählen Sie **Blockieren** aus, um Datenroaming über das Mobilfunknetz zu verhindern. **Nicht konfiguriert** (Standard) erlaubt das Datenroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.

  > [!IMPORTANT]
  > Diese Einstellung wird als Remotegeräteaktion behandelt. Diese Einstellung wird also nicht im Verwaltungsprofil auf dem Gerät angezeigt. Jedes Mal, wenn der Datenroamingstatus auf dem Gerät geändert wird, wird **Datenroaming** durch den Intune-Dienst blockiert. Wenn der Berichtsstatus in Intune als erfolgreich gemeldet wird, können Sie davon ausgehen, dass die Einstellung funktioniert, obwohl sie nicht im Verwaltungsprofil auf dem Gerät angezeigt wird.

- **Globales Abrufen im Hintergrund beim Roaming:** **Blockieren** verhindert, dass das Feature des globalen Abrufens im Hintergrund beim Roaming über das Mobilfunknetz verwendet wird. **Nicht konfiguriert** (Standard) ermöglicht, dass das Gerät Daten wie E-Mails beim Roaming in einem Mobilfunknetz abruft.
- **Sprachwahlverfahren:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer das Sprachwahlverfahren auf dem Gerät verwenden können. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung des Sprachwahlverfahrens auf dem Gerät.
- **Sprachroaming:** Wählen Sie **Blockieren** aus, um Sprachroaming über das Mobilfunknetz zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht das Sprachroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.
- **Privater Hotspot:** **Blockieren** schaltet den privaten Hotspot auf dem Gerät des Benutzers bei jeder Gerätesynchronisierung aus. Diese Einstellung kann mit einigen Anbietern nicht kompatibel sein. In der Standardeinstellung **Nicht konfiguriert** wird die Konfiguration des privaten Hotspots als vom Benutzer festgelegter Standard beibehalten.

  > [!IMPORTANT]
  > Diese Einstellung wird als Remotegeräteaktion behandelt. Diese Einstellung wird also nicht im Verwaltungsprofil auf dem Gerät angezeigt. Jedes Mal, wenn der Status des privaten Hotspots auf dem Gerät geändert wird, wird die Einstellung **Privater Hotspot** vom Intune-Dienst blockiert. Wenn der Berichtsstatus in Intune als erfolgreich gemeldet wird, können Sie davon ausgehen, dass die Einstellung funktioniert, obwohl sie nicht im Verwaltungsprofil auf dem Gerät angezeigt wird.

- **Regeln für die Verwendung von Datenverbindungen (nur verwaltete Apps):** Definieren Sie die Datentypen, die von verwalteten Apps genutzt werden können, wenn sie sich in Mobilfunknetzwerken befinden. Folgende Optionen sind verfügbar:
  - **Verwendung von Datenverbindungen blockieren:** Blockieren Sie die Verwendung von Datenverbindungen für **Alle verwalteten Apps**, oder Sie können **Bestimmte Apps wählen**.
  - **Verwendung von Datenverbindungen beim Roaming blockieren:** Blockieren Sie die Verwendung von Datenverbindungen beim Roaming für **Alle verwalteten Apps**, oder Sie können **Bestimmte Apps wählen**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Automatisierte Geräteregistrierung (überwacht)

- **Änderungen an den Einstellungen zur App-Mobilfunkdatennutzung**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Änderungen an den Einstellungen der Mobilfunkdatennutzung von Apps vorgenommen werden können. **Nicht konfiguriert** (Standard) ermöglicht Benutzern zu steuern, welche Apps Mobilfunkdaten verwenden dürfen.
- **Änderungen an den Einstellungen des Mobilfunktarifs**: **Blockieren** verhindert, dass Benutzer Einstellungen am Mobilfunktarifplan ändern. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern, Änderungen vorzunehmen.

  Diese Funktion gilt für:  
  - iOS 11.0 und neuer
  - iOS 13.0 und höher

- **Änderung des persönlichen Hotspots durch den Benutzer:** Wenn diese Einstellung auf **Blockieren** festgelegt wird, kann der Benutzer die Einstellung für den privaten Hotspot nicht ändern. **Nicht konfiguriert** (Standardeinstellung): Bei dieser Einstellung können Benutzer ihren privaten Hotspot aktivieren oder deaktivieren.

  Wenn Sie diese Einstellung und die Einstellung **Privater Hotspot** blockieren, wird der private Hotspot deaktiviert.

  Diese Funktion gilt für:  
  - iOS 12.2 und neuer
  - iOS 13.0 und höher

- **WLANs nur unter Verwendung von Konfigurationsprofilen beitreten**: **Anfordern** zwingt das Gerät, nur WLAN-Netzwerke zu verwenden, die mithilfe von Intune-Konfigurationsprofilen eingerichtet wurden. **Nicht konfiguriert** (Standard) ermöglicht dem Gerät, andere WLAN-Netzwerke zu verwenden.

  Stellen Sie sicher, dass das Gerät über ein WLAN-Profil verfügt, wenn **Erforderlich** für diese Einstellung festgelegt wird. Wenn Sie kein WLAN-Profil zuweisen, kann diese Einstellung verhindern, dass das Gerät eine Verbindung mit dem Internet herstellt. Das bedeutet, dass das Herstellen einer Internetverbindung für das Gerät blockiert werden kann, wenn das Geräteeinschränkungsprofil vor dem WLAN-Profil zugewiesen wird.
  
  Wenn keine Verbindung hergestellt werden kann, heben Sie die Registrierung des Geräts auf, und registrieren Sie es noch mal mit einem WLAN-Profil. Legen Sie für diese Einstellung anschließend in einem Geräteeinschränkungsprofil die Option **Erforderlich** fest, und weisen Sie das Profil dem Gerät zu.

- **WLAN immer aktiviert:** Wenn für diese Einstellung **Erforderlich** festgelegt ist, bleibt das WLAN in der App „Einstellungen“ aktiviert. Das WLAN kann weder in den Einstellungen noch im Kontrollzentrum deaktiviert werden, selbst wenn das Gerät sich im Flugmodus befindet. **Nicht konfiguriert** (Standardeinstellung): Bei dieser Einstellung kann der Benutzer das WLAN aktivieren oder deaktivieren.

  Durch die Konfiguration dieser Einstellung werden Benutzer nicht daran gehindert, ein WLAN-Netzwerk auszuwählen.

  Diese Funktion gilt für:  
  - iOS 13.0 und neuer
  - iOS 13.0 und höher

## <a name="connected-devices"></a>Verbundene Geräte

### <a name="settings-apply-to-all-enrollment-types"></a>Die Einstellungen gelten für: Alle Registrierungstypen

- **Handgelenkerkennung für gekoppelte Apple Watch:** **Erfordern** erzwingt, dass eine gekoppelte Apple Watch die Handgelenkerkennung verwendet. Wenn dies erforderlich ist, zeigt die Apple Watch keine Benachrichtigungen an, wenn sie nicht getragen wird. 

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **Kopplungskennwort für ausgehende AirPlay-Anforderungen anfordern:** **Anfordern** benötigt ein Kopplungskennwort, wenn der Benutzer AirPlay zum Streamen von Inhalten auf andere Apple-Geräte verwendet. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer das Streamen von Inhalten über AirPlay ohne Kennworteingabe.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Automatisierte Geräteregistrierung (überwacht)

- **AirDrop**: **Blockieren** verhindert die Verwendung von AirDrop auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung von AirDrop zum Austauschen von Inhalten mit Geräten in der Nähe.
- **Apple Watch-Kopplung:** **Blockieren** verhindert die Kopplung mit einer Apple Watch. **Nicht konfiguriert** (Standard) ermöglicht die Gerätekopplung mit einer Apple Watch.
- **Bluetooth-Änderung**: **Blockieren** hindert Benutzer daran, die Bluetootheinstellungen auf dem Gerät zu ändern. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Einstellungen zu ändern.
- **Hostkopplung zum Steuern der Geräte, mit denen ein iOS/iPadOS-Gerät gekoppelt werden kann**: **Nicht konfiguriert** (Standardeinstellung) ermöglicht die Hostkopplung, damit der Administrator steuern kann, mit welchen Geräten ein iOS/iPadOS-Gerät gekoppelt werden darf. **Blockieren** verhindert die Hostkopplung.
- **AirPrint blockieren**: Wählen Sie **Blockieren** aus, um die Verwendung des AirPrint-Features auf dem Gerät zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, AirPrint zu verwenden.
  - **Speicherung von AirPrint-Anmeldeinformationen im Schlüsselbund blockieren**: **Blockieren** verhindert, dass Benutzername und Kennwort auf dem Gerät im Keychain-Speicher gespeichert werden. **Nicht konfiguriert** (Standard) ermöglicht das Speichern von AirPrint-Benutzername und -Kennwort in der Keychain-App.
  - **Vertrauenswürdiges TLS-Zertifikat für AirPrint erforderlich**: **Anfordern** erzwingt, dass das Gerät für die TLS-Druckkommunikation ein vertrauenswürdiges Zertifikat verwendet.
  - **iBeacon-Ermittlung durch AirPrint-Drucker blockieren**: **Blockieren** hindert schädliche Air Print Bluetooth-Beacons am Pishing nach Netzwerkdatenverkehr. **Nicht konfiguriert** (Standard) ermöglicht das Ankündigen von AirPrint-Druckern auf dem Gerät.
- **Einrichten neuer Geräte in der Nähe blockieren**: **Blockieren** deaktiviert die Aufforderung zum Einrichten neuer Geräte, die sich in der Nähe befinden. Die Standardeinstellung **Nicht konfiguriert** ermöglicht das Auffordern von Benutzern, sich mit anderen Apple-Geräten in der Nähe zu verbinden.

  Diese Funktion gilt für:  
  - iOS 11.0 und neuer
  - iOS 13.0 und höher

- **Zugriff auf Dateien in USB-Laufwerk:** Geräte können eine Verbindung mit Dateien auf einem USB-Laufwerk herstellen und diese öffnen. Wenn **Deaktivieren** für diese Einstellung festgelegt wird, wird der Gerätezugriff auf das USB-Laufwerk in der App „Dateien“ blockiert, wenn ein USB-Gerät mit dem Gerät verbunden ist. Wenn dieses Feature deaktiviert wird, können Endbenutzer auch keine Dateien auf ein USB-Laufwerk verschieben, das mit einem iPad verbunden ist. **Nicht konfiguriert** (Standardeinstellung): Bei dieser Einstellung wird der Zugriff auf ein USB-Laufwerk über die App „Dateien“ zugelassen.

  Diese Funktion gilt für:  
  - iOS 13.0 und neuer
  - iOS 13.0 und höher

## <a name="keyboard-and-dictionary"></a>Tastatur und Wörterbuch

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Automatisierte Geräteregistrierung (überwacht)

- **Suche nach Wortdefinition**: **Blockieren** hindert Benutzer daran, ein Wort zu markieren und dann auf dem Gerät nach seiner Definition zu suchen. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf die Definitionssuchfunktion.
- **Tastaturwortvorschläge**: **Nicht konfiguriert** (Standardeinstellung) erlaubt die Verwendung von Tastaturwortvorschlägen für Wörter, die der Benutzer möglicherweise verwenden möchte. **Blockieren** verhindert die Verwendung dieser Funktion.
- **Autokorrektur**: **Nicht konfiguriert** (Standardeinstellung) erlaubt dem Gerät die automatische Korrektur von falsch geschriebenen Wörtern. **Blockieren** verhindert die Verwendung von Autokorrektur.
- **Rechtschreibprüfung über Tastatur:** Die Standardeinstellung **Nicht konfiguriert** ermöglicht die Verwendung der Rechtschreibprüfung auf dem Gerät. **Blockieren** ermöglicht die Rechtschreibprüfung.
- **Tastenkombinationen:** Die Standardeinstellung **Nicht konfiguriert** ermöglicht die Verwendung von Tastenkombinationen auf dem Gerät. **Blockieren** hindert den Benutzer an der Verwendung von Tastenkombinationen.
- **Dictation**: **Blockieren** verhindert, dass der Benutzer die Spracheingabe zur Eingabe von Text verwenden kann. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, die Spracheingabe zu verwenden.
- **QuickPath:** Bei der Standardeinstellung **Nicht konfiguriert** können Benutzer QuickPath verwenden, wodurch eine kontinuierliche Eingabe über die Tastatur des Geräts ermöglicht wird. Benutzer können Wörter durch Wischgesten auf den Tasten schreiben. Wenn **Blockieren** festgelegt wird, können Benutzer QuickPath nicht verwenden. 

  Diese Funktion gilt für:  
  - iOS 13.0 und neuer
  - iOS 13.0 und höher

## <a name="cloud-and-storage"></a>Cloud und Speicher

### <a name="settings-apply-to-all-enrollment-types"></a>Die Einstellungen gelten für: Alle Registrierungstypen

- **Verschlüsselte Sicherung:** **Anfordern** erzwingt die Verschlüsselung von Gerätesicherungen.
- **Synchronisierung verwalteter Apps mit der Cloud:** **Nicht konfiguriert** (Standardeinstellung) ermöglicht Ihren mit Intune verwalteten Apps, Daten mit dem iCloud-Konto des Benutzers zu synchronisieren. **Blockieren** verhindert diese Datensynchronisierung mit iCloud.
- **Enterprise Book-Sicherung blockieren:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer Enterprise Books sichern. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Bücher zu sichern.
- **Synchronisierung von Enterprise Book-Metadaten blockieren (Notizen und Highlights):** **Blockieren** verhindert, dass Notizen und Highlights in Enterprise Books synchronisiert werden können. **Nicht konfiguriert** (Standardeinstellung) lässt die Synchronisierung zu.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **Synchronisierung von Fotostreams in iCloud:** **Nicht konfiguriert** (Standardeinstellung) ermöglicht Benutzern das Aktivieren von **Mein Fotostream** auf ihren Geräten zum Synchronisieren mit iCloud, damit Fotos auf allen Geräten der Benutzer verfügbar sind. **Blockieren** verhindert die Fotostream-Synchronisierung mit iCloud. Wenn dieses Feature blockiert wird, kann es zu Datenverlust kommen. 
- **iCloud-Fotomediathek:** Deaktivieren Sie mit **Blockieren** die Verwendung der iCloud-Fotomediathek zum Speichern von Fotos und Videos in der Cloud. Fotos, die nicht vollständig aus der iCloud-Fotomediathek auf das Gerät heruntergeladen wurden, werden vom Gerät entfernt. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der iCloud-Fotomediathek.
- **Streaming freigegebener Fotos:** Wählen Sie **Blockieren** aus, um die **iCloud-Fotofreigabe** auf dem Gerät zu deaktivieren. **Nicht konfiguriert** (Standard) ermöglicht das Streaming freigegebener Fotos.
- **Handoff:** Bei der Standardeinstellung **Nicht konfiguriert** können Benutzer mit der Arbeit auf einem iOS/iPadOS-Gerät beginnen und ihre Arbeit auf einem anderen iOS/iPadOS- oder macOS-Gerät fortsetzen. **Blockieren** verhindert diese Übergabe.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Automatisierte Geräteregistrierung (überwacht)

- **In iCloud sichern:** **Nicht konfiguriert** (Standardeinstellung) ermöglicht dem Benutzer, das Gerät in iCloud zu sichern. **Blockieren** hindert den Benutzer daran, das Gerät in iCloud zu sichern.

  Ab iOS/iPadOS 13.0 muss es sich bei Geräten mit dieser Einstellung um überwachte Geräte handeln.

- **iCloud-Dokumentsynchronisierung blockieren**: **Nicht konfiguriert** (Standard) erlaubt die Dokument- und Schlüssel-/Wertsynchronisierung in Ihrem iCloud-Speicher. **Blockieren** hindert iCloud daran, Dokumente und Daten zu synchronisieren.

  Ab iOS/iPadOS 13.0 muss es sich bei Geräten mit dieser Einstellung um überwachte Geräte handeln.

- **Synchronisierung zwischen iCloud und Keychain blockieren:** Wählen Sie **Blockieren** aus, um die Synchronisierung von in der Keychain gespeicherten Anmeldeinformationen mit iCloud zu deaktivieren. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Anmeldeinformationen zu synchronisieren.

  Ab iOS/iPadOS 13.0 muss es sich bei Geräten mit dieser Einstellung um überwachte Geräte handeln.

## <a name="autonomous-single-app-mode"></a>Modus der autonomen einzelnen App

Verwenden Sie diese Einstellungen, um iOS-/iPadOS-Geräte zur Ausführung bestimmter Apps im autonomen Einzelanwendungsmodus zu konfigurieren. Wenn dieser Modus konfiguriert ist und der Benutzer eine der konfigurierten Apps startet, wird das Gerät für diese App gesperrt. Der Benutzer kann erst die App bzw. den Task wechseln, wenn er die zulässige App schließt.

Sie können beispielsweise für eine Schul- oder Universitätsumgebung eine App hinzufügen, mit der Benutzer einen Test auf dem Gerät durchführen können. Alternativ können Sie auch das Gerät in der Unternehmensportal-App sperren, bis sich der Endbenutzer authentifiziert hat. Wenn der Benutzer die App-Aktionen abschließt oder Sie diese Richtlinie entfernen, kehrt das Gerät in seinen normalen Zustand zurück.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Automatisierte Geräteregistrierung (überwacht)

- **App-Name:** Geben Sie den Namen der gewünschten App ein.
- **App-Bündel-ID:** Geben Sie die [Bündel-ID](bundle-ids-built-in-ios-apps.md) der gewünschten App ein.
- **Hinzufügen**: Verwenden Sie diese Option, um Ihre Liste mit Apps zu erstellen.

**Importieren** Sie alternativ eine CSV-Datei mit der Liste der App-Namen und der Bündel-IDs. **Exportieren** Sie alternativ eine vorhandene Liste, die die Apps enthält.

## <a name="kiosk"></a>Kiosk

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Automatisierte Geräteregistrierung (überwacht)

- **App zur Ausführung im Kioskmodus:** Wählen Sie die App-Typen aus, die Sie im Kioskmodus ausführen möchten. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standardeinstellung): Kioskeinstellungen werden nicht angewendet. Das Gerät wird nicht im Kioskmodus ausgeführt.
  - **Store-App:** Geben Sie die URL zu einer App im iTunes App-Store ein.
  - **Verwaltete App:** Wählen Sie eine App aus, die Sie Intune hinzugefügt haben.
  - **Integrierte App:** Geben Sie die [Bündel-ID](bundle-ids-built-in-ios-apps.md) der integrierten App ein.

- **Touch-Unterstützung:** **Anfordern** der Barrierefreiheitseinstellung „Touch-Unterstützung“ auf dem Gerät. Diese Funktion hilft Benutzern mit Bildschirmgesten bei Vorgängen, die für sie schwierig sein könnten. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- **Farben umkehren:** **Anfordern** der Barrierefreiheitseinstellung „Farben umkehren“, die die Anzeige für Benutzer mit eingeschränkter Sehfähigkeit anpasst. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- **Mono-Audio:** **Anfordern** der Barrierefreiheitseinstellung „Mono-Audio“ auf dem Gerät. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- **Sprachsteuerung**: Bei der Einstellung **Erforderlich** wird die Sprachsteuerung auf dem Gerät aktiviert. Dies ermöglicht Benutzern die vollständige Steuerung des Betriebssystems mithilfe von Siri-Befehlen. Wenn **Nicht konfiguriert** festgelegt wird, wird die Sprachsteuerung auf dem Gerät deaktiviert.

  Diese Einstellung gilt für:  
  - iOS 13.0 und neuer
  - iOS 13.0 und höher
  
  > [!TIP]
  > Wenn Ihre Organisation über branchenspezifische Apps verfügt, die die **Sprachsteuerung** nicht zum Release von iOS 13.0 unterstützt, wird empfohlen, dass Sie die Einstellung **Nicht konfiguriert** beibehalten.

- **VoiceOver:** **Anfordern** der Barrierefreiheitseinstellung „VoiceOver“ auf dem Gerät, um Text auf dem Bildschirm laut vorlesen zu lassen. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- **Zoom:** **Anfordern** der Einstellung „Zoom“ auf dem Gerät, damit Benutzer die Bildschirmausgabe mittels Toucheingabe vergrößern können. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- **Automatische Sperre:** Bei der Einstellung **Blockieren** wird die automatische Sperrung des Geräts deaktiviert. **Nicht konfiguriert** lässt diese Funktion zu.
- **Ruftonschalter:** **Blockieren** deaktiviert den Ruftonschalter (Stummschaltung) am Gerät. **Nicht konfiguriert** lässt diese Funktion zu.
- **Automatische Ausrichtung:** **Blockieren** verhindert, dass die Bildschirmausrichtung geändert werden kann, wenn der Benutzer das Gerät dreht. **Nicht konfiguriert** lässt diese Funktion zu.
- **Standbytaste:** Wählen Sie **Blockieren** aus, um die Schaltfläche für das Standby des Bildschirms am Gerät zu deaktivieren. **Nicht konfiguriert** lässt diese Funktion zu.
- **Touch:** **Blockieren** deaktiviert den Touchscreen des Geräts. **Nicht konfiguriert** ermöglicht dem Benutzer, den Touchscreen zu verwenden.
- **Lautstärkeregler:** Bei der Einstellung **Blockieren** werden die Lautstärkeregler des Geräts deaktiviert. Bei der Einstellung **Nicht konfiguriert** sind die Lautstärkeregler aktiviert.
- **AssistiveTouch-Steuerung:** Wenn Sie **Zulassen** auswählen, können Benutzer die Funktion „AssistiveTouch“ verwenden. **Nicht konfiguriert** deaktiviert dieses Feature.
- **Steuerelement zum Umkehren von Farben:** **Zulassen** von Farbumkehr-Anpassungen, mit denen der Benutzer die Funktion zur Farbumkehr individuell verwenden kann. **Nicht konfiguriert** deaktiviert dieses Feature.
- **Ausgewählten Text sprechen:** **Zulassen** der Barrierefreiheitseinstellungen „Auswahl vorlesen“ auf dem Gerät. Diese Funktion liest Text, den der Benutzer auswählt, laut vor. **Nicht konfiguriert** deaktiviert dieses Feature.
- **Änderung der Sprachsteuerung:** Bei der Einstellung **Zulassen** können Benutzer den Zustand der Sprachsteuerung auf ihren Geräten ändern. Bei der Einstellung **Nicht konfiguriert** wird verhindert, dass Benutzer den Zustand der Sprachsteuerung auf ihren Geräten ändern können.

  Diese Einstellung gilt für:  
  - iOS 13.0 und neuer
  - iOS 13.0 und höher

- **VoiceOver-Steuerelement:** **Zulassen** von VoiceOver-Änderungen, damit Benutzer die VoiceOver-Funktion aktualisieren können, z. B. wie schnell auf dem Bildschirm ausgegebener Text von der Sprachausgabe vorgelesen wird. **Nicht konfiguriert** verhindert VoiceOver-Änderungen.
- **Zoomsteuerelement:** **Zulassen** von Änderungen des Zooms durch den Benutzer. **Nicht konfiguriert** verhindert Zoomänderungen.

> [!NOTE]
> Damit Sie ein iOS/iPadOS-Gerät für den Kioskmodus konfigurieren können, müssen Sie das Apple Configurator-Tool oder das Apple-Programm zur Geräteregistrierung verwenden, um das Gerät in den überwachten Modus zu versetzen. Informationen zur Verwendung des Apple Configurator-Tools finden Sie im Apple-Handbuch.
> Wenn die iOS/iPadOS-App, die Sie eingeben, nach der Zuweisung des Profils installiert wird, wird das Gerät erst nach einem Neustart in den Kioskmodus versetzt.

## <a name="domains"></a>Domänen

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **Nicht markierte E-Mail-Domänen** > **E-Mail-Domänen-URL**: Fügen Sie der Liste eine oder mehrere URLs hinzu. Wenn Endbenutzer eine E-Mail von einer anderen Domäne als den von Ihnen eingegebenen erhalten, wird die E-Mail in der iOS/iPadOS-Mail-App als nicht vertrauenswürdig gekennzeichnet.

- **Verwaltete Webdomänen** > **Webdomänen-URL**: Fügen Sie der Liste eine oder mehrere URLs hinzu. Wenn Dokumente von den Domänen, die Sie eingeben, heruntergeladen werden, gelten sie als verwaltet. Diese Einstellung gilt nur für Dokumente, die mit dem Safari-Browser heruntergeladen werden.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Die Einstellungen gelten für: Automatisierte Geräteregistrierung (überwacht)

- **Domänen für automatisches Ausfüllen des Safari-Kennworts** > **Domänen-URL**: Fügen Sie der Liste eine oder mehrere URLs hinzu. Benutzer können nur Webkennwörter von URLs in dieser Liste speichern. Diese Einstellung gilt nur für den Safari-Browser und Geräte im überwachten Modus. Wenn Sie keine URLs eingeben, können Kennwörter von allen Websites gespeichert werden.

  Diese Einstellung gilt für:  
  - iOS 9.3 und höher
  - iOS 13.0 und höher

## <a name="settings-that-require-supervised-mode"></a>Einstellungen, die den überwachten Modus erfordern

Der überwachte Modus von iOS/iPadOS kann nur während der ersten Einrichtung des Geräts über das Apple-Programm zur Geräteregistrierung oder mithilfe von Apple Configurator aktiviert werden. Sobald der überwachte Modus aktiviert ist, kann Intune ein Gerät mit folgenden Funktionen konfigurieren:

- App-Sperre (Einzelanwendungsmodus) 
- Globaler HTTP-Proxy 
- Aktivierungssperre deaktivieren 
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
>
> - App-Installation durch Benutzer
> - App-Deinstallation
> - FaceTime
> - Safari
> - iTunes
> - Anstößiger Inhalt
> - Dokumente und Daten von iCloud
> - Multiplayerspiele
> - Game Center-Freunde hinzufügen
> - Siri

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](../device-profile-assign.md) und [Überwachen von Profilen](../device-profile-monitor.md)

Sie können auch Gerätefeatures und -einstellungen auf [macOS](device-restrictions-macos.md)-Geräten einschränken.
