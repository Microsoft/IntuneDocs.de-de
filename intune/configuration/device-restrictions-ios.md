---
title: 'iOS-Geräteeinstellungen in Microsoft Intune: Azure | Microsoft-Dokumentation'
titleSuffix: ''
description: Fügen Sie Einstellungen auf iOS-Geräten hinzu, konfigurieren oder erstellen Sie sie, um Funktionen einzuschränken. Zu diesen gehört das Festlegen von Anforderungen für Kennwörter, die Anpassung des Sperrbildschirms, die Verwendung integrierter Apps, das Hinzufügen eingeschränkter oder genehmigter Apps, die Handhabung von Bluetooth-Geräten, das Herstellen einer Verbindung zur Cloud für Sicherung und Speicherung, die Aktivierung den Kioskmodus, das Hinzufügen und die Steuerung von Domänen und wie Benutzer mit dem Safari-Webbrowser in Microsoft Intune interagieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5f9a01adaa6f5ab59819c2924172c30a437ebd8c
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992921"
---
# <a name="ios-and-ipados-device-settings-to-allow-or-restrict-features-using-intune"></a>iOS- und iPadOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie auf iOS- und iPadOS-Geräten steuern können. Verwenden Sie als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) diese Einstellungen, um Features zuzulassen oder zu deaktivieren, Kennwortregeln festzulegen, bestimmte Apps zu erlauben oder einzuschränken usw.

Diese Einstellungen werden einem Gerätekonfigurationsprofil in Intune hinzugefügt und dann Ihren iOS-Geräten zugewiesen oder bereitgestellt.

> [!TIP]
> Diese Einstellungen verwenden die MDM-Einstellungen von Apple. Weitere Informationen zu diesen Einstellungen finden Sie unter [Einstellungen für die Verwaltung mobiler Geräte von Apple](https://support.apple.com/guide/mdm/welcome/web) (öffnet die Website von Apple).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Konfigurationsprofil mit Geräteeinschränkungen](../device-restrictions-configure.md).

> [!NOTE]
> Diese Einstellungen gelten für verschiedene Registrierungs Typen, wobei einige Einstellungen auf alle Registrierungs Optionen angewendet werden. Weitere Informationen zu den verschiedenen Registrierungs Typen finden Sie unter [IOS](../ios-enroll.md)-Registrierung.

## <a name="general"></a>Allgemein

### <a name="settings-apply-to-all-enrollment-types"></a>Einstellungen gelten für: alle Registrierungs Typen

- **Nutzungsdaten freigeben**: Wählen Sie **Blockieren** aus, um zu verhindern, dass das Gerät Diagnose- und Nutzungsdaten an Apple sendet. **Nicht konfiguriert** (Standard) erlaubt das Senden dieser Daten.

- **Bildschirmaufnahme**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Screenshots oder Bildschirmaufnahmen auf dem Gerät vorgenommen werden. In ios 9,0 und neueren Blöcken werden auch Bildschirmaufzeichnungen blockiert. **Nicht konfiguriert** (Standard) erlaubt dem Benutzer, den Bildschirminhalt als Bild oder Video zu erfassen.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **Nicht vertrauenswürdige TLS-Zertifikate:** Wählen Sie **Blockieren** aus, um zu verhindern, dass nicht vertrauenswürdige TLS-Zertifikate (Transport Layer Security) auf das Gerät gelangen. Die Standardeinstellung **Nicht konfiguriert** lässt TLS-Zertifikate zu.
- VPN **-PKI-Aktualisierungen blockieren**: **blockieren** verhindert, dass Ihre Benutzer Software Updates erhalten, ohne Ihre Geräte mit einem Computer zu verbinden. **Nicht konfiguriert** (Standardeinstellung) aktualisiert diese Einstellung nicht auf dem Gerät.
- **Anzeigennachverfolgung begrenzen**: Wählen Sie **Begrenzen** aus, um die Geräteanzeigen-ID zu deaktivieren. Die Standardeinstellung **Nicht konfiguriert** behält die Aktivierung bei.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Einstellungen gelten für: automatisierte Geräteregistrierung (überwacht)

- **Änderung der Einstellungen zur Diagnoseübermittlung** : **Blockieren** verhindert, dass der Benutzer in **Diagnose- und Nutzung** (Geräteeinstellungen) Änderungen an den Einstellungen für Diagnoseübermittlung und App-Analyse vornimmt. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Geräteeinstellungen zu ändern.

  Um diese Einstellung zu verwenden, legen Sie die Einstellung **Nutzungsdaten freigeben** auf **blockieren**fest.

  Diese Funktion gilt für:  
  - iOS 9.3.2 und neuer

- **Remotebildschirmüberwachung über die Classroom-App:** Wählen Sie **Blockieren** aus, um zu verhindern, dass die Classroom-App den Bildschirm des Geräts remote anzeigt. **Nicht konfiguriert** (Standard) erlaubt der Classroom-App von Apple, den Bildschirm anzuzeigen.

  Um diese Einstellung zu verwenden, legen Sie die Einstellung für die **Bildschirmaufzeichnung** auf **blockieren**fest.

  Diese Funktion gilt für:  
  - iOS 9.3. und neuer

- **Unangekündigte Bildschirmüberwachung über Classroom-App**: Falls auf **Zulassen** festgelegt, können Lehrer im Hintergrund die Bildschirme der iOS-Geräte ihrer Kursteilnehmer mithilfe der Classroom-App überwachen, ohne dass die Kursteilnehmer dies mitbekommen. In einer Klasse registrierte Kursteilnehmergeräte, die die Classroom-App verwenden, gewähren der Lehrkraft des Kurses automatisch die Berechtigung. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature deaktiviert.

  Um diese Einstellung zu verwenden, legen Sie die Einstellung für die **Bildschirmaufzeichnung** auf **blockieren**fest.

- **Vertrauen für Unternehmens-App**: Wählen Sie **Blockieren** aus, um die Schaltfläche **Unternehmensentwickler vertrauen** aus „Einstellungen > Allgemein > Profile und Geräteverwaltung“ auf dem Gerät zu entfernen. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer zu wählen, ob Apps, die nicht aus dem App Store heruntergeladen wurden, vertraut werden soll.
- **Kontoänderung**: Bei Festlegung auf **Blockieren** kann der Benutzer die gerätespezifischen Einstellungen nicht über die iOS-Einstellungen-App aktualisieren. Der Benutzer kann z. B. nicht neue Gerätekonten erstellen oder Benutzernamen bzw. Kennwort ändern. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Einstellungen zu ändern.

  Diese Funktion gilt auch für Einstellungen, auf die über die iOS-Einstellungen-App zugegriffen werden kann, wie z. B. E-Mail, Kontakte, Kalender, Twitter und mehr. Diese Funktion gilt nicht für Apps mit Kontoeinstellungen, die nicht über die iOS-Einstellungen-App konfiguriert werden können, wie z. B. die Microsoft Outlook-App.

- **Bildschirmzeit**: Wählen Sie **Blockieren**, um zu verhindern, dass Benutzer ihre eigenen Einschränkungen in „Bildschirmzeit“ (Geräteeinstellungen) vornehmen. **Nicht konfiguriert** erlaubt dem Benutzer das Konfigurieren von Geräteeinschränkungen (z. B. Jugendschutz oder Inhalts- und Datenschutzeinschränkungen) auf dem Gerät.

  Diese Einstellung hieß zuvor **Aktivieren von Einschränkungen in den Geräteeinstellungen**. Auswirkungen dieser Änderung:  
  
  - iOS 11.4.1 und früher: **Blockieren** verhindert, dass Endbenutzer die für sie geltenden Einschränkungen der Geräteeinstellungen bearbeiten. Dieses Verhalten bewirkt dasselbe, sodass es keine Änderungen für Endbenutzer gibt.
  - iOS 12.0 und neuer: **Blockieren** verhindert, dass Endbenutzer die für sie geltende **Bildschirmzeit** (einschließlich Einschränkungen von Inhalt und Datenschutz) in den Geräteeinstellungen (Einstellungen > Allgemein > Bildschirmzeit) bearbeiten. Bei auf iOS 12.0 aktualisierten Geräten wird die Registerkarte „Einschränkungen“ in den Geräteeinstellungen nicht mehr angezeigt (Einstellungen > Allgemein > Geräteverwaltung > Verwaltungsprofil > Einschränkungen). Diese Einstellungen befinden sich unter **Bildschirmzeit**.
  
- **Verwendung der Option zum Löschen aller Inhalte und Einstellungen auf dem Gerät**: Wählen Sie **Blockieren** aus, damit Benutzer nicht die Option zum Löschen aller Inhalte und Einstellungen auf dem Gerät verwenden können. **Nicht konfiguriert** (Standard) ermöglicht Benutzern den Zugriff auf diese Einstellungen.
- **Gerätenamensänderung**: Wählen Sie **Blockieren** aus, damit der Gerätenamen nicht geändert werden kann. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, den Namen des Geräts zu ändern.
- **Änderung von Benachrichtigungseinstellungen:** Wählen Sie **Blockieren**, damit die Benachrichtigungseinstellungen nicht geändert werden können. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, die Benachrichtigungseinstellungen des Geräts zu ändern.
- **Änderung des Hintergrundbilds**: **Blockieren** verhindert, dass das Hintergrundbild geändert wird. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, das Hintergrundbild des Geräts zu ändern.
- **Änderung der Vertrauenseinstellungen für die Unternehmens-App**: **Blockieren** verhindert, dass der Benutzer die Vertrauensstellungseinstellungen für die Unternehmens-App auf überwachten Geräten ändert. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, Apps zu vertrauen, die nicht aus dem App Store heruntergeladen wurden.
- **Konfigurationsprofiländerungen**: **Blockieren** verhindert Änderungen des Konfigurationsprofils auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, Konfigurationsprofile zu installieren.
- **Anwendungssperre**: Wählen Sie **Zulassen** aus, um die Aktivierungssperre auf überwachten iOS-Geräten zu aktivieren. Die Aktivierungssperre erschwert die erneute Aktivierung verlorener oder gestohlener Geräte.
- **Entfernen von Apps blockieren:** Wenn Sie **Blockieren** festlegen, können Benutzer keine Apps entfernen. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, Apps vom Gerät zu entfernen.
- **USB-Zubehör bei gesperrtem Gerät zulassen** **: Hiermit können USB** -Zubehör Daten mit einem Gerät austauschen, das über eine Stunde gesperrt ist. **Nicht konfiguriert** (Standard) aktualisiert den eingeschränkten USB-Modus nicht auf dem Gerät.
- **Automatische Datums- und Uhrzeiteinstellung erzwingen**: **Anfordern** erzwingt die automatische Einstellung von Datum und Uhrzeit auf überwachten Geräten. Die Zeitzone für das Gerät wird aktualisiert, wenn das Gerät über Mobilfunkverbindungen verfügt oder WLAN mit Standortdiensten aktiviert ist.
- **Von Kursteilnehmern eine Berechtigung zum Verlassen des Classroom-Kurses verlangen**: **Anfordern** erzwingt, dass in einem nicht verwalteten Kurs registrierte Kursteilnehmer, die die Classroom-App verwenden, vom Kursleiter eine Berechtigung zum Verlassen des Kurses anfordern müssen. **Nicht konfiguriert** (Standard) erzwingt nicht, dass Kursteilnehmer um eine Berechtigung bitten müssen.

  Diese Funktion gilt für:  
  - iOS 11.3 und neuer

- **Das Beschränken von Classroom auf eine App und das Sperren von Geräten ohne vorherige Aufforderung zulassen**: **Aktivieren** ermöglicht es der Lehrkraft, Apps zu sperren oder das Gerät über die Classroom-App zu sperren, ohne die Lernenden zu fragen. Das Sperren von Apps bedeutet, dass das Gerät nur auf die von der Lehrkraft angegebenen Apps zugreifen kann. Die Standardeinstellung **Nicht konfiguriert** verhindert, dass Lehrkräfte Anwendungen oder Geräte, die die Classroom-App verwenden, sperren, ohne die Lernenden zu fragen.

  Diese Funktion gilt für:  
  - iOS 11.0 und neuer

- **Ohne Aufforderung automatisch Classroom-Kursen beitreten**: **Aktivieren** erlaubt es Lernenden, einem Kurs in der Classroom-App automatisch beizutreten, ohne die Lehrkraft zu fragen. In der Standardeinstellung **Nicht konfiguriert** wird die Lehrkraft gefragt, wenn Lernende einem Kurs in der Classroom-App beitreten möchten.

  Diese Funktion gilt für:  
  - iOS 11.0 und neuer

- **VPN-Erstellung blockieren**: **Blockieren** hindert Benutzer daran, VPN-Konfigurationseinstellungen zu erstellen. **Nicht konfiguriert** (Standard) ermöglicht Benutzern das Erstellen von VPNs auf dem Gerät.
- **eSIM-Einstellungen ändern**: **Blockieren** hindert Benutzer am Entfernen oder Hinzufügen eines Mobilfunktarifplans zum eSIM auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Einstellungen zu ändern.

  Diese Funktion gilt für:  
  - iOS 12.1 und neuer

- **Softwareupdates zurückstellen**: In der Standardeinstellung **Nicht konfiguriert** werden Softwareupdates auf dem Gerät angezeigt, sobald Apple sie veröffentlicht. Wenn beispielsweise ein iOS-Update von Apple an einem bestimmten Datum veröffentlicht wird, wird dieses Update normalerweise um oder am Veröffentlichungsdatum auf dem Gerät angezeigt.

  **Aktivieren** ermöglicht Ihnen, die Anzeige von Softwareupdates auf Geräten zu verzögern (0-90 Tage). Diese Einstellung steuert nicht, ob Updates installiert werden oder nicht. 

  - **Sichtbarkeit von Softwareupdates verzögern**: Geben Sie einen Wert von 0-90 Tagen ein. Nach der Verzögerung erhalten Benutzer eine Benachrichtigung für ein Update auf die früheste Version des Betriebssystems, die verfügbar war, als die Verzögerung ausgelöst wurde.

    Wenn beispielsweise iOS 12.a am **1. Januar** verfügbar ist und **Sichtbarkeit verzögern** auf **5 Tage** festgelegt ist, wird iOS 12.a nicht als verfügbares Update auf Endbenutzergeräten angezeigt. Am **6. Tag** nach Veröffentlichung ist dieses Update verfügbar, sodass Endbenutzer es installieren können.

    Diese Einstellung gilt für:  
    - iOS 11.3 und neuer

## <a name="password"></a>Kennwort

### <a name="settings-apply-to-all-enrollment-types"></a>Einstellungen gelten für: alle Registrierungs Typen

- **Kennwort**: **Anfordern** der Eingabe eines Kennworts durch den Endbenutzer, um auf das Gerät zugreifen zu können. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, ohne Kennworteingabe auf das Gerät zuzugreifen.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

> [!IMPORTANT]
> Wenn Sie auf von Benutzern registrierten Geräten eine Kennworteinstellung konfigurieren, wird die Einstellung **Einfache Kennwörter** automatisch auf **Blockieren** festgelegt und eine sechsstellige PIN erzwungen.
>
> Sie konfigurieren beispielsweise die Einstellung **Kennwortablauf** und übertragen diese Richtlinie per Push auf vom Benutzer registrierte Geräte. Auf diesen Geräten geschieht Folgendes:
>
> - Die Einstellung **Kennwortablauf** wird ignoriert.
> - Einfache Passwörter wie `1111` oder `1234` sind nicht zulässig.
> - Eine sechsstellige PIN wird erzwungen.

- **Einfache Kennwörter**: Wählen Sie **Blockieren** aus, um komplexere Kennwörter zu erzwingen. **Nicht konfiguriert** ermöglicht einfache Kennwörter wie z. B. `0000` und `1234`.

- **Erforderlicher Kennworttyp**: Wählen Sie den Kennworttyp aus, den Ihre Organisation fordert. Folgende Optionen sind verfügbar:
  - **Gerätestandard**
  - **Numerisch**
  - **Alphanumerisch**
- **Anzahl nicht alphanumerischer Zeichen im Kennwort**: Geben Sie die Anzahl von Symbolzeichen ein (z. B. `#` oder `@`), die im Kennwort enthalten sein müssen.

- **Minimale Kennwortlänge**: Geben Sie die Mindestlänge an, die ein Benutzer eingeben muss (zwischen 4 und 14 Zeichen). Geben Sie auf Benutzer registrierten Geräten eine Länge zwischen 4 und 6 Zeichen ein.
  
  > [!NOTE]
  > Bei Geräten, die Benutzer registriert sind, können Benutzer eine PIN mit mehr als 6 Ziffern festlegen. Auf dem Gerät werden jedoch höchstens 6 Ziffern erzwungen. Ein Administrator legt z. b. die Mindestlänge auf `8`fest. Auf Geräten, die für den Benutzer registriert sind, müssen Benutzer nur eine 6-stellige PIN festlegen. InTune erzwingt keine PIN, die für Benutzer registrierte Geräte mehr als 6 Ziffern umfasst.

- **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird**: Geben Sie die Anzahl zulässiger Anmeldefehler (von 4 bis 11) ein, bevor das Gerät zurückgesetzt wird.
  
  IOS verfügt über integrierte Sicherheit, die sich auf diese Einstellung auswirken kann. Beispielsweise kann IOS das Auslösen der Richtlinie abhängig von der Anzahl der Anmeldefehler verzögern. Es kann auch in Erwägung gezogen werden, die gleiche Kennung wie ein Versuch einzugeben. Das [IOS-Sicherheitshandbuch](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) von Apple (öffnet die Website von Apple) ist eine gute Ressource und bietet spezifischere Informationen zu Kennungen.
  
- **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts**<sup>1</sup>: Geben Sie an, wie lange das Gerät inaktiv bleibt, bevor der Benutzer sein Kennwort erneut eingeben muss. Wenn Sie einen längeren Zeitraum eingeben, als derzeit auf dem Gerät eingestellt ist, ignoriert das Gerät Ihre Eingabe. Wird auf Geräten ab iOS 8.0 unterstützt.

- **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung**<sup>1</sup>: Geben Sie an, wie viele Minuten ein Gerät höchstens inaktiv sein darf, bevor es automatisch gesperrt wird.

  **IOS-Optionen**:  

  - **Nicht konfiguriert** (Standardeinstellung): InTune berührt diese Einstellung nicht.
  - **Sofort**: Bildschirm sperren nach 30 Sekunden Inaktivität.
  - **1**: Bildschirm sperren nach 1 Minute Inaktivität.
  - **2**: Bildschirm sperren nach 2 Minuten Inaktivität.
  - **3**: Bildschirm sperren nach drei Minuten Inaktivität.
  - **4**: Bildschirm sperren nach 4 Minuten Inaktivität.
  - **5**: Bildschirm sperren nach 5 Minuten Inaktivität.
    
  **ipados-Optionen**:  

  - **Nicht konfiguriert** (Standardeinstellung): InTune berührt diese Einstellung nicht.
  - **Sofort**: Bildschirm sperren nach 2 Minuten Inaktivität.
  - **2**: Bildschirm sperren nach 2 Minuten Inaktivität.
  - **5**: Bildschirm sperren nach 5 Minuten Inaktivität.
  - **10**: Bildschirm sperren nach 10 Minuten Inaktivität.
  - **15**: Bildschirm sperren nach 15 Minuten Inaktivität.

  Wenn ein Wert nicht für IOS oder ipados gilt, verwendet Apple den nächstgelegenen *niedrigsten* Wert. Wenn Sie z. b. `4` Minuten eingeben, werden für ipados-Geräte `2` Minuten verwendet. Wenn Sie `10` Minuten eingeben, werden für IOS-Geräte `5` Minuten verwendet. Dies ist eine Apple-Einschränkung.
  
  > [!NOTE]
  > Die Intune-Benutzeroberfläche für diese Einstellung trennt die unterstützten Werte für IOS und ipados nicht. Die Benutzeroberfläche wird in einer zukünftigen Version möglicherweise aktualisiert.

- **Kennwortablauf (Tage)** : Geben Sie die Anzahl der Tage an, nach denen das Gerätekennwort geändert werden muss.
- **Wiederverwendung vorheriger Kennwörter verhindern**: Geben Sie die Anzahl neuer Kennwörter ein, die verwendet werden müssen, bevor ein altes Kennwort wiederverwendet werden kann.
- Entsperrung der Fingereingabe **-ID und der Gesichts Kennung**: Wählen Sie **Block** aus, um zu verhindern, dass das Gerät mithilfe eines Fingerabdrucks **Nicht konfiguriert** ermöglicht dem Benutzer das Entsperren des Geräts mittels dieser Methoden.

  Durch das Blockieren dieser Einstellung wird auch die Verwendung der fakeid-Authentifizierung zum Entsperren des Geräts verhindert.

  Face ID gilt für:  
  - iOS 11.0 und neuer

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Einstellungen gelten für: automatisierte Geräteregistrierung (überwacht)

- **Änderung von Kennung**: Wählen Sie **Blockieren** aus, damit die Kennung nicht geändert, hinzugefügt oder entfernt werden kann. Änderungen an Kennungseinschränkungen werden nach der Blockierung dieser Funktion auf überwachten Geräten ignoriert. **Nicht konfiguriert** (Standard) ermöglicht, Passcodes hinzuzufügen, zu ändern oder zu entfernen.

  - **Änderung von Touch ID und Face ID**: die **Sperre** hindert den Benutzer daran, touchid-Fingerabdrücke und die Gesichts-ID zu ändern, hinzuzufügen oder zu entfernen. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer das Aktualisieren der TouchID-Fingerabdrücke und Face ID auf dem Gerät.

    Wenn Sie diese Einstellung blockieren, wird der Benutzer auch daran hindern, die-fakeid-Authentifizierung zu ändern, hinzuzufügen oder

    Face ID gilt für:  
    - iOS 11.0 und neuer

- **AutoAusfüllen für Kennwörter blockieren**: Wählen Sie **Blockieren**, um die Verwendung der Funktion zum automatischen Ausfüllen von Kennwörtern unter iOS zu verhindern. Das Wählen von **Blockieren** bewirkt auch Folgendes:

  - Benutzer werden nicht aufgefordert, in Safari oder beliebigen Apps gespeicherte Kennwörter zu verwenden.
  - Automatische sichere Kennwörter sind deaktiviert, und sichere Kennwörter werden Benutzern nicht empfohlen.

  **Nicht konfiguriert** (Standard) lässt diese Funktionen zu.

- **Kennwortanforderungen durch Näherung blockieren**: Wählen Sie **Blockieren** aus, damit das Gerät eines Benutzers keine Kennwörter von in der Nähe befindlichen Geräten anfordert. **Nicht konfiguriert** (Standard) lässt diese Kennwortanforderungen zu.
- **Kennwortfreigabe blockieren**: **Blockieren** verhindert die Freigabe von Kennwörtern zwischen Geräten mit AirDrop. **Nicht konfiguriert** (Standard) ermöglicht die Freigabe von Kennwörtern.
- **Touch ID oder Face ID für AutoAusfüllen von Kennwörtern und Kreditkarteninformationen erforderlich**: Bei Festlegung auf **Anfordern** müssen sich Benutzer mit TouchID oder FaceID authentifizieren, bevor Kennwörter oder Kreditkarteninformationen in Safari und anderen Anwendungen automatisch eingefügt werden können. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern, diese Funktion in den Geräteeinstellungen zu steuern.

  Diese Funktion gilt für:  
  - iOS 11.0 und neuer
  
<sup>1</sup> Wenn Sie die Einstellungen **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung** und **Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts** konfigurieren, werden diese nacheinander angewendet. Wenn Sie beispielsweise den Wert für beide Einstellungen auf **5** Minuten einstellen, wird der Bildschirm automatisch nach fünf Minuten deaktiviert, und das Gerät wird nach weiteren fünf Minuten gesperrt. Wenn der Benutzer den Bildschirm jedoch manuell deaktiviert, wird die zweite Einstellung sofort angewendet. Im selben Beispiel wird das Gerät fünf Minuten später gesperrt, nachdem der Benutzer den Bildschirm deaktiviert hat.

## <a name="locked-screen-experience"></a>Benutzererfahrung „Gesperrter Bildschirm“

### <a name="settings-apply-to-all-enrollment-types"></a>Einstellungen gelten für: alle Registrierungs Typen

- **Kontrollcenterzugriff bei gesperrtem Gerät**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Kontrollcenter-App zu verhindern, während das Gerät gesperrt ist. **Nicht konfiguriert** (Standard) erlaubt dem Benutzer den Zugriff auf die Kontrollcenter-App, während das Gerät gesperrt ist.
- **Benachrichtigungen bei Gerätesperre**: **Blockieren** verhindert den Zugriff auf Benachrichtigungen, wenn das Gerät gesperrt ist. **Nicht konfiguriert** (Standard) erlaubt dem Benutzer den Zugriff auf die Benachrichtigungen, ohne dass das Gerät entsperrt werden muss.
- **Ansicht „Heute“ bei Gerätesperre**: **Blockieren** verhindert den Zugriff auf die Ansicht „Heute“, während das Gerät gesperrt ist. **Nicht konfiguriert** (Standard) erlaubt dem Benutzer den Zugriff auf die Ansicht „Heute“, während das Gerät gesperrt ist.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **Wallet-Benachrichtigungen bei gesperrtem Gerät**: **Blockieren** verhindert den Zugriff auf die Wallet-App, wenn das Gerät gesperrt ist. **Nicht konfiguriert** (Standard) erlaubt dem Benutzer den Zugriff auf die Wallet-App, während das Gerät gesperrt ist.

## <a name="app-store-doc-viewing-gaming"></a>App Store, Dokumentanzeige, Spiele

### <a name="settings-apply-to-all-enrollment-types"></a>Einstellungen gelten für: alle Registrierungs Typen

- **Anzeige von Unternehmensdokumenten in nicht verwalteten Apps**: **Blockieren** verhindert die Anzeige unternehmenseigener Dokumente in nicht verwalteten Apps. **Nicht konfiguriert** (Standard) gestattet die Anzeige von Unternehmensdokumenten in beliebigen Apps. Beispiel: Sie möchten verhindern, dass Benutzer Dateien aus der OneDrive-App in Dropbox speichern. Legen Sie für diese Einstellung **Blockieren** fest. Sobald das Gerät die Richtlinie empfängt (z. B. nach einem Neustart), ist kein Speichern mehr möglich.


  > [!NOTE]
  > Wenn diese Einstellung blockiert ist, werden Drittanbieter-Tastaturen, die aus dem App Store installiert werden, ebenfalls blockiert.

  - **Nicht verwaltete apps das Lesen von verwalteten Kontakt Konten gestatten**: Wenn diese Option auf **zulassen**festgelegt ist, können nicht verwaltete apps, wie z. b. die integrierte IOS Contacts-APP, Kontaktinformationen aus verwalteten apps lesen und darauf zugreifen, einschließlich des Outlook-Mobile App. **Nicht konfiguriert** (Standard) verhindert, dass die integrierte App „Kontakte“ auf dem Gerät gelesen oder Duplikate entfernt werden können.  
  
    Diese Einstellung ermöglicht oder verhindert das Lesen von Kontaktinformationen. Das Synchronisieren von Kontakten zwischen den apps wird nicht gesteuert.
  
    Wenn Sie diese Einstellung verwenden möchten, legen Sie die Einstellung **Anzeige von Unternehmensdokumenten in nicht verwalteten Apps** auf **Blockieren** fest.

  Weitere Informationen zu diesen beiden Einstellungen und deren Auswirkung auf die Verbindung von Outlook für IOS finden Sie [unter Support Tipp: Verwenden von benutzerdefinierten InTune-Profileinstellungen mit der IOS Native Contacts-App](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453).

- **AirDrop als nicht verwaltetes Ziel behandeln**: **Anfordern** erzwingt, dass AirDrop als nicht verwaltetes Drop-Ziel betrachtet wird. Es hindert verwaltete Apps daran, Daten mithilfe von AirDrop zu senden. 
- **Anzeige nicht unternehmenseigener Dokumente in Unternehmens-Apps**: **Blockieren** verhindert die Anzeige nicht unternehmenseigener Dokumente in Unternehmens-Apps. **Nicht konfiguriert** (Standard) gestattet die Anzeige beliebiger Dokumente in verwalteten Unternehmens-Apps.

  Wenn Sie auf **blockieren** festlegen, wird auch die Kontakt Synchronisierung in Outlook für IOS verhindert. Weitere Informationen finden [Sie unter Support Tipp: Aktivieren der Outlook IOS-Kontakt Synchronisierung mit iOS12 MDM](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Enabling-Outlook-iOS-Contact-Sync-with-iOS12-MDM/ba-p/298453)-Steuerelementen.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **ITunes Store-Kennwort für alle Käufe erforderlich**: **fordern** Sie den Benutzer auf, das Apple-ID-Kennwort für jeden in-App-oder iTunes-Kauf einzugeben. **Nicht konfiguriert** (Standardeinstellung): ermöglicht Käufe nicht jedes Mal, wenn ein Kennwort angefordert wird.
- **In-App-Einkäufe**: Wählen Sie **Blockieren** aus, um In-App-Einkäufe im Store zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht Einkäufe im Store in einer ausgeführten App.
- **Als „Erotik“ gekennzeichneten Inhalt aus dem iBook Store herunterladen**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer Medien aus dem iBook Store herunterladen, die als „Erotik“ gekennzeichnet sind. **Nicht konfiguriert** (Standard) gestattet dem Benutzer das Herunterladen von Büchern aus der Kategorie „Erotik“.
- **Verwalteten apps das Schreiben von Kontakten in nicht verwaltete Kontakt Konten gestatten**: Wenn diese Option auf " **zulassen**" festgelegt ist, können verwaltete apps, wie z. b. das Outlook-Mobile App, Kontaktinformationen, einschließlich geschäftlichen und Unternehmens Kontakten, in der integrierten IOS Contacts-APP speichern oder synchronisieren. Wenn diese Einstellung auf " **nicht konfiguriert** " (Standard) festgelegt ist, können verwaltete apps keine Kontaktinformationen für die integrierte IOS-app "Kontakte" auf dem Gerät speichern oder synchronisieren.
  
  Wenn Sie diese Einstellung verwenden möchten, legen Sie die Einstellung **Anzeige von Unternehmensdokumenten in nicht verwalteten Apps** auf **Blockieren** fest.

- **Bewertungsregion**: Wählen Sie die Bewertungsregion aus, die Sie für die zulässigen Downloads verwenden möchten. Wählen Sie dann die zulässigen Bewertungen für **Filme**, **Fernsehsendungen** und **Apps** aus.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Einstellungen gelten für: automatisierte Geräteregistrierung (überwacht)

- **App Store**: **Blockieren** verhindert den Zugriff auf den App Store auf überwachten Geräte. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.

  Ab IOS 13,0 sind für diese Einstellung überwachte Geräte erforderlich.

  - **Installieren von Apps über den App Store**: Wählen Sie **Blockieren** aus, um den App Store auf dem Startbildschirm des Geräts zu blockieren. Endbenutzer können weiterhin iTunes oder das Apple Configurator-Tool zum Installieren von Apps verwenden. **Nicht konfiguriert** (Standard) lässt den App Store auf dem Startbildschirm zu.
  - **Automatische App-Downloads**: Wählen Sie **Blockieren** aus, um den automatischen Download von Apps zu verhindern, die auf anderen Geräten erworben wurden. Updates vorhandener Apps sind nicht betroffen. **Nicht konfiguriert** (Standard) ermöglicht, Apps auf das Gerät herunterzuladen, die auf anderen iOS-Geräten gekauft wurden.

- **Anstößige iTunes-Musik-, Podcast- oder Nachrichteninhalte**: Wählen Sie **Blockieren** aus, um anstößige iTunes-Musik-, Podcast- oder Nachrichteninhalte zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht, dass das Gerät im Store auf nicht jugendfreie Inhalte zugreift. IOS 13 und höher erfordert möglicherweise nur überwachte Geräte. 

  Ab IOS 13,0 sind für diese Einstellung überwachte Geräte erforderlich.

- **Hinzufügen von Game Center-Freunden**: **Blockieren** hindert Benutzer daran, Game Center-Freunde hinzuzufügen. **Nicht konfiguriert** (Standard) gestattet dem Benutzer, im Game Center Freunde hinzuzufügen.

  Ab IOS 13,0 sind für diese Einstellung überwachte Geräte erforderlich.

- **Game Center**: **Blockieren** verhindert, dass die Game Center-App verwendet werden kann. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der Game Center-App auf dem Gerät.
- **Multiplayerspiele**: Wählen Sie **Block** aus, um Multiplayerspiele **Nicht konfiguriert** (Standard) ermöglicht, dass der Benutzer Multiplayerspiele auf dem Gerät spielt.

  Ab IOS 13,0 sind für diese Einstellung überwachte Geräte erforderlich.

- **Zugriff auf das Netzwerklaufwerk in der Datei-App**: mit dem SMB-Protokoll (Server Message Block) können Geräte auf Dateien oder andere Ressourcen auf einem Netzwerk Server zugreifen. **Deaktivieren** verhindert den Zugriff auf Dateien auf einem SMB-Netzwerklaufwerk. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.

  Diese Funktion gilt für:  
  - IOS und ipados 13,0 und höher

## <a name="built-in-apps"></a>Integrierte Apps

### <a name="settings-apply-to-all-enrollment-types"></a>Einstellungen gelten für: alle Registrierungs Typen

- **Siri**: **Blockieren** verhindert den Zugriff auf Siri. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung des Sprach-Assistenten Siri auf dem Gerät.
  - **Siri bei Gerätesperre**: Wählen Sie **Blockieren** aus, um den Zugriff auf Siri zu verhindern, wenn das Gerät gesperrt ist. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung des Sprach-Assistenten Siri auf dem Gerät, wenn das Gerät gesperrt ist.

- **Safari-Betrugswarnungen**: **Anfordern**, dass Betrugswarnungen im Webbrowser auf dem Gerät angezeigt werden. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird dieses Feature deaktiviert.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **Spotlight-Suche gibt Ergebnisse aus dem Internet zurück**: **Blockieren** verhindert, dass Spotlight Ergebnisse einer Internetsuche zurückgibt. **Nicht konfiguriert** (Standard) ermöglicht der Spotlight-Suchfunktion das Herstellen einer Verbindung mit dem Internet zur Bereitstellung von Suchergebnissen.

- **Safari-Cookies**: Wählen Sie aus, wie Cookies auf dem Gerät behandelt werden. Folgende Optionen sind verfügbar:
  - Zulassen
  - Alle Cookies blockieren
  - Cookies von besuchten Websites zulassen
  - Cookies von aktueller Website zulassen

- **Safari-JavaScript**: **Blockieren** verhindert, dass Java-Skripts im Browser auf dem Gerät ausgeführt werden. **Nicht konfiguriert** (Standardeinstellung) ermöglicht Java-Skripts.

- **Safari-Popups**: **Blockieren** deaktiviert den Popupblocker im Webbrowser. **Nicht konfiguriert** (Standardeinstellung): lässt den Popup Blocker zu.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Einstellungen gelten für: automatisierte Geräteregistrierung (überwacht)

- **Kamera**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Kamera des Geräts zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf die Kamera des Geräts.

  Ab IOS 13,0 sind für diese Einstellung überwachte Geräte erforderlich.

  - **FaceTime**: Mit **Blockieren** verhindern Sie den Zugriff auf die FaceTime-App. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf die FaceTime-App des Geräts.

    Ab IOS 13,0 sind für diese Einstellung überwachte Geräte erforderlich.

- **Siri-Filter für anstößige Ausdrücke**: **Anfordern** verhindert, dass Siri anstößige Ausdrücke diktiert oder verwendet.

  Um diese Einstellung zu verwenden, legen Sie die **Siri** -Einstellung auf **Block**fest.

- **Abfrage von benutzergeneriertem Inhalt aus dem Internet durch Siri**: **Blockieren** hindert Siri daran, für die Beantwortung von Fragen auf Websites zuzugreifen. **Nicht konfiguriert** (Standard) ermöglicht Siri, auf benutzergenerierten Inhalt aus dem Internet zuzugreifen.

  Um diese Einstellung zu verwenden, legen Sie die **Siri** -Einstellung auf **Block**fest.

- **Apple News**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Apple News-App des Geräts zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der Apple News-App.
- **iBooks-Store**: **Blockieren** verhindert, dass auf den iBooks-Store zugegriffen werden kann. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, den iBooks Store zu durchsuchen und dort Bücher zu erwerben.
- **Nachrichten-APP auf dem Gerät**: **blockieren** hindert Benutzer an der Verwendung der Nachrichten-APP für IMESS Age. Wenn das Gerät Textnachrichten unterstützt, kann der Benutzer weiterhin Textnachrichten senden und mit SMS empfangen. **Nicht konfiguriert** (Standardeinstellung): ermöglicht die Verwendung der Nachrichten-APP zum Senden und Lesen von Nachrichten über das Internet.
- **Podcasts**: **Blockieren** hindert Benutzer an der Verwendung der Podcasts-App. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der Podcasts-App.
- **Musikdienst**: **Blockieren** setzt die Musik-App in den klassischen Modus zurück und deaktiviert den Musikdienst. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der Apple Music-App.
- **iTunes Radio-Dienst**: **Blockieren** hindert Benutzer daran, die iTunes Radio-App zu verwenden. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der iTunes Radio-App.
- **iTunes Store**: **nicht konfiguriert** (Standardeinstellung): ermöglicht iTunes auf den Geräten. **Blockieren** hindert Benutzer daran, iTunes auf dem Gerät zu verwenden. 

  Diese Funktion gilt für:  
  - iOS 4.0 und neuer

- **Mein iPhone suchen**: **nicht konfiguriert** (Standard) ermöglicht die Verwendung dieser Funktion "meine APP suchen", um den ungefähren Speicherort des Geräts zu erhalten. **Blockieren** verhindert diese Funktion in der App "meine APP suchen". 

  Diese Funktion gilt für:  
  - IOS 13,0 und ipados 13,0 und höher

- **Meine Freunde suchen**: **nicht konfiguriert** (Standard) ermöglicht die Verwendung dieses Features "meine APP suchen", um nach Familie und Freunden von einem Apple-Gerät oder icloud.com zu suchen. **Blockieren** verhindert diese Funktion in der App "meine APP suchen".

  Diese Funktion gilt für:  
  - IOS 13,0 und ipados 13,0 und höher

- **Änderungen an den Einstellungen der App „Meine Freunde suchen“** : **Blockieren** verhindert Änderungen der Einstellungen für die App „Meine Freunde suchen“. **Nicht konfiguriert** (Standard) ermöglicht Benutzern das Ändern von Einstellungen für die App „Meine Freunde suchen“.

- **Spotlight-Suche gibt Ergebnisse aus dem Internet zurück**: **Blockieren** verhindert, dass Spotlight Ergebnisse einer Internetsuche zurückgibt. **Nicht konfiguriert** (Standard) ermöglicht der Spotlight-Suchfunktion das Herstellen einer Verbindung mit dem Internet zur Bereitstellung von Suchergebnissen.

- **Entfernen von System-Apps vom Gerät blockieren**: Die Auswahl von **Blockieren** deaktiviert die Möglichkeit, System-Apps vom Gerät zu entfernen. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, System-Apps zu entfernen.

- **Safari**: **Blockieren** der Verwendung des Safari-Browsers auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht Benutzern die Verwendung des Safari-Browsers.

  Ab IOS 13,0 sind für diese Einstellung überwachte Geräte erforderlich.

- **AutoAusfüllen in Safari**: **Blockieren** deaktiviert AutoAusfüllen in Safari auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, die AutoAusfüllen-Einstellungen im Browser zu ändern.

  Ab IOS 13,0 sind für diese Einstellung überwachte Geräte erforderlich.

## <a name="restricted-apps"></a>Eingeschränkte Apps

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **Typ der Liste der eingeschränkten apps**: Erstellen Sie eine Liste von apps, die Benutzer nicht installieren oder verwenden dürfen. Folgende Optionen sind verfügbar:

  - **Nicht konfiguriert** (Standard): Es gibt keine Einschränkungen von InTune. Benutzer haben Zugriff auf apps, die Sie zuweisen, und integrierte apps.
  - **Unzulässige Apps:** Eine Reihe nicht von Intune verwalteter Apps, die nicht auf dem Gerät installiert werden sollen. Benutzer werden daran gehindert, eine unzulässige APP zu installieren. Wenn jedoch ein Benutzer eine APP aus dieser Liste installiert, wird er in InTune gemeldet.
  - **Genehmigte Apps:** Listet die Apps auf, die Benutzer installieren dürfen. Benutzer dürfen keine Apps installieren, die in dieser Liste nicht aufgeführt sind. Apps, die von Intune verwaltet werden, sind automatisch zugelassen. Benutzer werden nicht daran gehindert, eine App zu installieren, die nicht in der Liste zulässiger Apps enthalten ist. Wenn dies der Fall ist, wird er in InTune gemeldet.

Um diesen Listen Apps hinzuzufügen, können Sie:

- Die iTunes App-Store-URL der App **hinzufügen**, die Sie wünschen. Geben Sie beispielsweise zum Hinzufügen der Microsoft Work Folders-App `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` oder `https://apps.apple.com/us/app/work-folders/id950878067?mt=8` ein.

  Um die URL einer App zu suchen, öffnen Sie den iTunes App Store, und suchen Sie nach der App. Suchen Sie beispielsweise nach `Microsoft Remote Desktop` oder `Microsoft Word`. Wählen Sie die App aus, und kopieren Sie die URL.

  Sie können auch iTunes verwenden, um die App zu suchen, und dann die Aufgabe **Link kopieren**, um die App-URL abzurufen.

- **Importieren** Sie eine CSV-Datei mit den Details der App, einschließlich der URL. Verwenden Sie das Format `<app url>, <app name>, <app publisher>`. **Exportieren** Sie alternativ eine vorhandene Liste, die die Liste der eingeschränkten Apps im gleichen Format enthält.

> [!IMPORTANT]
> Geräteprofile, die Einstellungen für eingeschränkte Apps verwenden, müssen Benutzergruppen zugewiesen werden.

## <a name="show-or-hide-apps"></a>Apps ein- oder ausblenden

Gilt für Geräte, auf denen IOS 9,3 oder höher ausgeführt wird.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Einstellungen gelten für: automatisierte Geräteregistrierung (überwacht)

- **Liste der APP-Typen**: Erstellen Sie eine Liste von apps, die angezeigt oder ausgeblendet werden sollen. Sie können integrierte apps und branchenspezifische apps anzeigen oder ausblenden. Die Apple-Website enthält eine Liste [integrierter Apple-Apps](https://support.apple.com/HT208094). Folgende Optionen sind verfügbar:

  - **Ausgeblendete Apps:** Geben Sie eine Liste von Apps an, die vor Benutzern verborgen werden. Benutzer können diese Apps weder anzeigen noch öffnen.
  
    Apple verhindert, dass einige Native apps ausgeblendet werden. Beispielsweise können Sie die **Einstellungen** oder **Wallet** -apps auf dem Gerät nicht ausblenden. [Integrierte Apple-Apps löschen](https://support.apple.com/HT208094) listet die apps auf, die ausgeblendet werden können.
  
  - **Sichtbare Apps**: Geben Sie eine Liste von Apps ein, die Benutzer anzeigen und starten können. Es können keine anderen Apps angezeigt oder gestartet werden.

- **App-URL**: Geben Sie die Store-App-URL der APP ein, die Sie anzeigen oder ausblenden möchten. Beispiel:

  - Geben Sie zum Hinzufügen der Microsoft Work Folders-App `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8` oder `https://apps.apple.com/us/app/work-folders/id950878067?mt=8` ein. 

  - Geben Sie `https://itunes.apple.com/de/app/microsoft-word/id586447913` oder `https://apps.apple.com/de/app/microsoft-word/id586447913`ein, um die Microsoft Word-App hinzuzufügen.

  Um die URL einer App zu suchen, öffnen Sie den iTunes App Store, und suchen Sie nach der App. Suchen Sie beispielsweise nach `Microsoft Remote Desktop` oder `Microsoft Word`. Wählen Sie die App aus, und kopieren Sie die URL.

  Sie können auch iTunes verwenden, um die App zu suchen, und dann die Aufgabe **Link kopieren**, um die App-URL abzurufen.
  
  Weitere Informationen zum Suchen einer Bündel-ID [finden Sie untersuchen der Bündel-ID für eine IOS-App](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app).

- **App-Bündel-ID**: Geben Sie die [App-Bündel-ID](bundle-ids-built-in-ios-apps.md) der App ein, die Sie hinzufügen möchten. Sie können integrierte apps und branchenspezifische apps anzeigen oder ausblenden. Die Apple-Website enthält eine Liste [integrierter Apple-Apps](https://support.apple.com/HT208094).
- **App-Name:** Geben Sie den Namen der App ein, die Sie hinzufügen möchten. Sie können integrierte apps und branchenspezifische apps anzeigen oder ausblenden. Die Apple-Website enthält eine Liste [integrierter Apple-Apps](https://support.apple.com/HT208094).
- **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein, die Sie hinzufügen.

Apps können Sie wie folgt hinzufügen:

- **Add**: Wählen Sie diese Option aus, um die Liste der apps zu erstellen
- **Importieren** Sie eine CSV-Datei mit den Details der App, einschließlich der URL. Verwenden Sie das Format `<app url>, <app name>, <app publisher>`. Sie können auch **exportieren** , um eine Liste der eingeschränkten apps im gleichen Format zu erstellen.

## <a name="wireless"></a>Drahtlos

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

Hinweis für das Datenroaming (Tipp oder wichtiger Hinweis zur Unterstützung der Kunden Verwirrung): Diese Einstellung wird im Verwaltungs Profil des Zielgeräts nicht angezeigt. Dies liegt daran, dass diese Einstellung als Remote Geräte Aktion behandelt wird und jedes Mal, wenn der Status des Datenroaming auf dem Gerät geändert wird, vom InTune-Dienst erneut blockiert wird. Obwohl es sich nicht im Verwaltungs Profil befindet, funktioniert es, wenn es in der Verwaltungskonsole als Erfolgsmeldung angezeigt wird. 
- **Datenroaming**: Wählen Sie **Blockieren** aus, um Datenroaming über das Mobilfunknetz zu verhindern. **Nicht konfiguriert** (Standard) erlaubt das Datenroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.

  > [!IMPORTANT]
  > Diese Einstellung wird als Remote Geräte Aktion behandelt. Diese Einstellung wird also nicht im Verwaltungs Profil auf dem Gerät angezeigt. Jedes Mal, wenn sich der datenroamingstatus auf dem Gerät ändert, wird das **Datenroaming** durch den InTune-Dienst blockiert. Wenn in InTune der Bericht Erstellungs Status erfolgreich angezeigt wird, wissen Sie, dass es funktioniert, auch wenn die Einstellung im Verwaltungs Profil auf dem Gerät nicht angezeigt wird.

- **Globales Abrufen im Hintergrund beim Roaming**: **Blockieren** verhindert, dass die Funktion des globalen Abrufens im Hintergrund beim Roaming über das Mobilfunknetz verwendet wird. **Nicht konfiguriert** (Standard) ermöglicht, dass das Gerät Daten wie E-Mails beim Roaming in einem Mobilfunknetz abruft.
- **Sprachwahlverfahren**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer das Sprachwahlverfahren auf dem Gerät verwenden. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung des Sprachwahlverfahrens auf dem Gerät.
- **Sprachroaming**: Wählen Sie **Blockieren** aus, um Sprachroaming über das Mobilfunknetz zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht das Sprachroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.
- **Privater Hotspot**: **Blockieren** schaltet den privaten Hotspot auf dem Gerät des Benutzers bei jeder Gerätesynchronisierung aus. Diese Einstellung kann mit einigen Anbietern nicht kompatibel sein. In der Standardeinstellung **Nicht konfiguriert** wird die Konfiguration des privaten Hotspots als vom Benutzer festgelegter Standard beibehalten.

  > [!IMPORTANT]
  > Diese Einstellung wird als Remote Geräte Aktion behandelt. Diese Einstellung wird also nicht im Verwaltungs Profil auf dem Gerät angezeigt. Jedes Mal, wenn sich der Status des persönlichen Hotspots auf dem Gerät ändert, wird der **persönliche Hotspot** durch den InTune-Dienst blockiert. Wenn in InTune der Bericht Erstellungs Status erfolgreich angezeigt wird, wissen Sie, dass es funktioniert, auch wenn die Einstellung im Verwaltungs Profil auf dem Gerät nicht angezeigt wird.

- **Mobilfunk-Verwendungsregeln (nur verwaltete Apps)** : Definieren Sie die Datentypen, die von verwalteten Apps genutzt werden können, wenn sie sich in Mobilfunknetzwerken befinden. Folgende Optionen sind verfügbar:
  - **Verwendung von Datenverbindungen blockieren**: Blockieren Sie die Verwendung von Datenverbindungen für **Alle verwalteten Apps**, oder Sie können **Bestimmte Apps wählen**.
  - **Verwendung von Datenverbindungen beim Roaming blockieren:** Blockieren Sie die Verwendung von Datenverbindungen beim Roaming für **Alle verwalteten Apps**, oder Sie können **Bestimmte Apps wählen**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Einstellungen gelten für: automatisierte Geräteregistrierung (überwacht)

- **Änderungen an den Einstellungen zur App-Mobilfunkdatennutzung**: Wählen Sie **Blockieren** aus, um Änderungen an den Einstellungen zur App-Mobilfunkdatennutzung zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht Benutzern zu steuern, welche Apps Mobilfunkdaten verwenden dürfen.
- **Änderungen an den Einstellungen des Mobilfunktarifplans**: **Blockieren** verhindert, dass Benutzer Einstellungen am Mobilfunktarifplan ändern. Die Standardeinstellung **Nicht konfiguriert** ermöglicht Benutzern, Änderungen vorzunehmen.

  Diese Funktion gilt für:  
  - iOS 11.0 und neuer

- **Benutzer Änderung des persönlichen Hotspots**: Wenn " **blockieren**" festgelegt ist, kann der Benutzer die Einstellung für den persönlichen Hotspot nicht ändern. **Nicht konfiguriert** (Standardeinstellung): ermöglicht Endbenutzern das Aktivieren oder Deaktivieren Ihres persönlichen Hotspots.

  Wenn Sie diese Einstellung blockieren und die Einstellung für den **persönlichen Hotspot** blockieren, wird der persönliche Hotspot ausgeschaltet.

  Diese Funktion gilt für:  
  - iOS 12.2 und neuer

- **Verknüpfen von WLAN-Netzwerken nur mithilfe von Konfigurationsprofilen:** **Anfordern** erzwingt, dass das Gerät nur WLAN-Netzwerke verwendet, die mit Intune-Konfigurationsprofilen eingerichtet wurden. **Nicht konfiguriert** (Standard) ermöglicht dem Gerät, andere WLAN-Netzwerke zu verwenden.
- **Wi-Fi ist immer eingeschaltet**: Wenn dies auf **erforderlich**festgelegt ist, bleibt WLAN in der App "Einstellungen" aktiviert. Sie kann nicht in den Einstellungen oder in der Steuerungs Stelle ausgeschaltet werden, auch wenn sich das Gerät im Flugzeug Modus befindet. **Nicht konfiguriert** (Standardeinstellung): ermöglicht es dem Benutzer, die Aktivierung oder das Ausschalten des WLAN zu steuern.

  Durch das Konfigurieren dieser Einstellung wird nicht verhindert, dass Benutzer ein Wi-Fi-Netzwerk auswählen.

  Diese Funktion gilt für:  
  - IOS und ipados 13,0 und höher

## <a name="connected-devices"></a>Verbundene Geräte

### <a name="settings-apply-to-all-enrollment-types"></a>Einstellungen gelten für: alle Registrierungs Typen

- **Handgelenkerkennung für gekoppelte Apple Watch**: **Anfordern** erzwingt, dass eine gekoppelte Apple Watch die Handgelenkerkennung verwendet. Wenn dies erforderlich ist, zeigt die Apple Watch keine Benachrichtigungen an, wenn sie nicht getragen wird. 

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **Kopplungskennwort für ausgehende AirPlay-Anforderungen anfordern**: **Anfordern** eines Kopplungskennworts, wenn der Benutzer AirPlay zum Streamen von Inhalten auf andere Apple-Geräte verwendet. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer das Streamen von Inhalten über AirPlay ohne Kennworteingabe.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Einstellungen gelten für: automatisierte Geräteregistrierung (überwacht)

- **AirDrop**: **Blockieren** verhindert die Verwendung von AirDrop auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung von AirDrop zum Austauschen von Inhalten mit Geräten in der Nähe.
- **Apple Watch**Kopplung: der **Block** verhindert die Kopplung mit einem Apple Watch. **Nicht konfiguriert** (Standard) ermöglicht die Gerätekopplung mit einer Apple Watch.
- **Bluetooth-Änderung**: **Blockieren** hindert den Endbenutzer an der Änderung von Bluetooth-Einstellungen auf dem Gerät. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Einstellungen zu ändern.
- **Hostkopplung, um zu steuern, mit welchen Geräten ein iOS-Gerät gekoppelt werden kann**: **Nicht konfiguriert** (Standard) erlaubt die Hostkopplung, damit der Administrator steuern kann, mit welchen Geräten ein iOS-Gerät gekoppelt werden kann. **Blockieren** verhindert die Hostkopplung.
- **AirPrint blockieren**: Wählen Sie **Blockieren** aus, um die Verwendung des AirPrint-Features auf dem Gerät zu verhindern. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, AirPrint zu verwenden.
  - **Speichern von AirPrint-Anmeldeinformationen in Keychain blockieren**: **Blockieren** verhindert, dass der Keychain-Speicher für Benutzername und Kennwort auf dem Gerät verwendet wird. **Nicht konfiguriert** (Standard) ermöglicht das Speichern von AirPrint-Benutzername und -Kennwort in der Keychain-App.
  - **Vertrauenswürdiges TLS-Zertifikat für AirPrint anfordern**: **Anfordern** erzwingt, dass das Gerät vertrauenswürdige Zertifikate für die TLS-Druckkommunikation verwendet.
  - **iBeacon-Ermittlung von AirPrint-Druckern blockieren**: **Blockieren** hindert böswillige AirPrint Bluetooth-Beacons am Phishing nach Netzwerkverkehr. **Nicht konfiguriert** (Standard) ermöglicht das Ankündigen von AirPrint-Druckern auf dem Gerät.
- **Einrichten neuer Geräte in der Nähe blockieren**: **Blockieren** deaktiviert die Aufforderung zum Einrichten neuer Geräte, die sich in der Nähe befinden. Die Standardeinstellung **Nicht konfiguriert** ermöglicht das Auffordern von Benutzern, sich mit anderen Apple-Geräten in der Nähe zu verbinden.

  Diese Funktion gilt für:  
  - iOS 11.0 und neuer

- **Zugriff auf Dateien auf dem USB-Laufwerk**: Geräte können eine Verbindung herstellen und Dateien auf einem USB-Laufwerk öffnen. **Deaktivieren** verhindert den Gerätezugriff auf das USB-Laufwerk in der Datei-app, wenn ein USB-Gerät mit dem Gerät verbunden ist. Durch das Deaktivieren dieses Features wird verhindert, dass Endbenutzer Dateien auf ein USB-Laufwerk übertragen, das mit einem iPad verbunden ist. **Nicht konfiguriert** (Standardeinstellung): ermöglicht den Zugriff auf ein USB-Laufwerk in der App "Dateien".

  Diese Funktion gilt für:  
  - IOS und ipados 13,0 und höher

## <a name="keyboard-and-dictionary"></a>Tastatur und Wörterbuch

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Einstellungen gelten für: automatisierte Geräteregistrierung (überwacht)

- **Suche nach Wortdefinitionen**: **Blockieren** hindert Benutzer daran, ein Wort zu markieren und dann auf dem Gerät nach seiner Definition zu suchen. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf die Definitionssuchfunktion.
- **Tastaturwortvorschläge**: **Nicht konfiguriert** (Standard) erlaubt die Verwendung von Tastaturwortvorschlägen für Wörter, die der Benutzer möglicherweise verwenden möchte. **Blockieren** verhindert die Verwendung dieser Funktion.
- **Autokorrektur**: **Nicht konfiguriert** (Standard) erlaubt dem Gerät die automatische Korrektur von falsch geschriebenen Wörtern. **Blockieren** verhindert die Verwendung von Autokorrektur.
- **Tastatur Rechtschreibprüfung**: **nicht konfiguriert** (Standardeinstellung) ermöglicht die Verwendung von Rechtschreibprüfung auf dem Gerät. **Blockieren** ermöglicht die Rechtschreibprüfung.
- **Tastenkombinationen**: **nicht konfiguriert** (Standardeinstellung) ermöglicht die Verwendung von Tastenkombinationen auf dem Gerät. **Blockieren** hindert den Benutzer an der Verwendung von Tastenkombinationen.
- **Diktat**: **Blockieren** verhindert, dass der Benutzer die Spracheingabe zur Eingabe von Text verwenden kann. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, die Spracheingabe zu verwenden.
- **QuickPath**: **nicht konfiguriert** (Standardeinstellung) ermöglicht Benutzern die Verwendung von QuickPath, wodurch eine kontinuierliche Eingabe auf der Tastatur des Geräts möglich ist. Benutzer können eingeben, indem Sie über die Schlüssel zum Erstellen von Wörtern schwenken. **Blockieren** hindert Benutzer daran, QuickPath zu verwenden. 

  Diese Funktion gilt für:  
  - IOS 13,0 und ipados 13,0 und höher

## <a name="cloud-and-storage"></a>Cloud und Speicher

### <a name="settings-apply-to-all-enrollment-types"></a>Einstellungen gelten für: alle Registrierungs Typen

- **Verschlüsselte Sicherung**: **Anfordern** erzwingt die Verschlüsselung von Gerätesicherungen.
- **Synchronisierung verwalteter Apps mit der Cloud**: **Nicht konfiguriert** (Standard) ermöglicht Ihren mit Intune verwalteten Apps, Daten mit dem iCloud-Konto des Benutzers zu synchronisieren. **Blockieren** verhindert diese Datensynchronisierung mit iCloud.
- **Enterprise Book-Sicherung blockieren**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer Enterprise Books sichern. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Bücher zu sichern.
- **Synchronisierung von Enterprise Book-Metadaten blockieren (Notizen und Highlights)** : **Blockieren** verhindert, dass Notizen und Highlights in Enterprise Books synchronisiert werden. **Nicht konfiguriert** (Standardeinstellung) ermöglicht die Synchronisierung.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **Synchronisierung von Fotostreams in iCloud**: **Nicht konfiguriert** (Standard) ermöglicht Benutzern das Aktivieren von **Mein Photo Stream** auf ihren Geräten zum Synchronisieren mit iCloud, damit Fotos auf allen Geräten der Benutzer verfügbar sind. **Blockieren** verhindert die Fotostream-Synchronisierung mit iCloud. Das Blockieren dieser Funktion kann zu Datenverlusten führen. 
- **iCloud-Fotomediathek**: Deaktivieren Sie mit **Blockieren** die Verwendung der iCloud-Fotomediathek zum Speichern von Fotos und Videos in der Cloud. Fotos, die nicht vollständig aus der iCloud-Fotomediathek auf das Gerät heruntergeladen wurden, werden vom Gerät entfernt. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der iCloud-Fotomediathek.
- **Streaming freigegebener Fotos**: Wählen Sie **Blockieren** aus, um die **iCloud-Fotofreigabe** auf dem Gerät zu deaktivieren. **Nicht konfiguriert** (Standard) ermöglicht das Streaming freigegebener Fotos.
- **Übergabe**: **nicht konfiguriert** (Standardeinstellung) ermöglicht Benutzern das Starten von Arbeit auf einem IOS-Gerät und das anschließende fortsetzen der Arbeit, die Sie auf einem anderen ios-oder macOS-Gerät gestartet haben. **Blockieren** verhindert diese Übergabe.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Einstellungen gelten für: automatisierte Geräteregistrierung (überwacht)

- **In iCloud sichern**: **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, das Gerät in iCloud zu sichern. **Blockieren** hindert den Benutzer daran, das Gerät in iCloud zu sichern.

  Ab IOS 13,0 sind für diese Einstellung überwachte Geräte erforderlich.

- **Block iCloud Document sync** (Dokumentsynchronisierung in iCloud blockieren): **Nicht konfiguriert** (Standard) ermöglicht die Dokument- und Schlüssel-/Wertsynchronisierung in Ihrem iCloud-Speicher. **Blockieren** hindert iCloud daran, Dokumente und Daten zu synchronisieren.

  Ab IOS 13,0 sind für diese Einstellung überwachte Geräte erforderlich.

- **Synchronisierung zwischen iCloud und Keychain blockieren**: Wählen Sie **Blockieren** aus, um die Synchronisierung in der Keychain gespeicherter Anmeldeinformationen mit iCloud zu deaktivieren. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer, diese Anmeldeinformationen zu synchronisieren.

  Ab IOS 13,0 sind für diese Einstellung überwachte Geräte erforderlich.

## <a name="autonomous-single-app-mode"></a>Modus der autonomen einzelnen App

Verwenden Sie diese Einstellungen, um iOS-Geräte zur Ausführung bestimmter Apps im Modus der autonomen einzelnen App zu konfigurieren. Wenn dieser Modus konfiguriert ist und die App ausgeführt wird, wird das Gerät gesperrt. Es kann nur die App ausführen. Fügen Sie z. B. eine App hinzu, mit der Benutzer einen Test auf dem Gerät durchführen können. Wenn die Aktionen der App abgeschlossen sind, oder Sie diese Richtlinie entfernen, kehrt das Gerät in seinen normalen Zustand zurück.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Einstellungen gelten für: automatisierte Geräteregistrierung (überwacht)

- **App-Name**: Geben Sie den Namen der App ein, die Sie hinzufügen möchten.
- **App-Bündel-ID**: Geben Sie die [Bündel-ID](bundle-ids-built-in-ios-apps.md) der App ein, die Sie hinzufügen möchten.
- **Add**: Wählen Sie diese Option aus, um die Liste der apps zu erstellen

**Importieren** Sie alternativ eine CSV-Datei mit der Liste der App-Namen und der Bündel-IDs. **Exportieren** Sie alternativ eine vorhandene Liste, die die Apps enthält.

## <a name="kiosk"></a>Kiosk

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Einstellungen gelten für: automatisierte Geräteregistrierung (überwacht)

- **Im Kioskmodus auszuführende App**: Wählen Sie den Typ der Apps aus, die Sie im Kioskmodus ausführen möchten. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Kioskeinstellungen werden nicht angewendet. Das Gerät wird nicht im Kioskmodus ausgeführt.
  - **Store-App**: Geben Sie die URL zu einer App im iTunes App-Store ein.
  - **Verwaltete App**: Wählen Sie eine App aus, die Sie in Intune hinzugefügt haben.
  - **Integrierte App**: Geben Sie die [Bündel-ID](bundle-ids-built-in-ios-apps.md) der integrierten App ein.

- **Touch-Unterstützung**: Zum **Anfordern** der Barrierefreiheitseinstellung „Touch-Unterstützung“ auf dem Gerät. Diese Funktion hilft Benutzern mit Bildschirmgesten bei Vorgängen, die für sie schwierig sein könnten. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- **Farben umkehren:** **Anfordern** der Barrierefreiheitseinstellung „Farben umkehren“, die die Anzeige für Benutzer mit eingeschränkter Sehfähigkeit anpasst. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- **Mono-Audio**: **Anfordern** der Barrierefreiheitseinstellung „Mono-Audio“ auf dem Gerät. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- **Sprachsteuerung**: **erfordert** die Sprachsteuerung auf dem Gerät und ermöglicht es Benutzern, das Betriebssystem mithilfe von Siri-Befehlen vollständig zu steuern. **Nicht konfiguriert** deaktiviert die Sprachsteuerung auf dem Gerät.

  Diese Einstellung gilt für:  
  - iOS 13.0 und neuer
  - iOS 13.0 und höher
  
  > [!TIP]
  > Wenn Sie Lob-Apps für Ihre Organisation zur Verfügung haben und die **sprach Kontrolle** an Tag 0 bei der Veröffentlichung von IOS 13,0 nicht bereit ist, empfiehlt es sich, diese Einstellung als **nicht konfiguriert**zu belassen.

- **VoiceOver**: **Anfordern** der Barrierefreiheitseinstellung „VoiceOver“ auf dem Gerät, um Text auf dem Bildschirm vorlesen zu lassen. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- **Zoom**: **Anfordern** der Einstellung „Zoom“ auf dem Gerät, damit Benutzer die Bildschirmausgabe mittels Toucheingabe vergrößern können. Mit **Nicht konfiguriert** wird dieses Feature im Kioskmodus nicht ausgeführt, oder es wird nicht aktiviert.
- Automatische **Sperre**: der **Block** verhindert das automatische Sperren des Geräts. **Nicht konfiguriert** lässt diese Funktion zu.
- **Stummschalter**: **Blockieren** deaktiviert die Stummschaltung (Ruftonschalter) am Gerät. **Nicht konfiguriert** lässt diese Funktion zu.
- **Bildschirmdrehung:** **Blockieren** verhindert, dass die Bildschirmausrichtung geändert werden kann, wenn der Benutzer das Gerät dreht. **Nicht konfiguriert** lässt diese Funktion zu.
- **Standbytaste:** Wählen Sie **Blockieren** aus, um die Standbytaste am Gerät zu deaktivieren. **Nicht konfiguriert** lässt diese Funktion zu.
- **Touch**: **Blockieren** deaktiviert den Touchscreen des Geräts. **Nicht konfiguriert** ermöglicht dem Benutzer, den Touchscreen zu verwenden.
- **** Volumeschaltflächen: **blockieren** verhindert die Verwendung der volumeschaltflächen des Geräts. **Nicht konfiguriert** ermöglicht die volumeschaltflächen.
- **Steuerelement der Touch-Unterstützung**: Mit **Zulassen** können Benutzer die Touch-Unterstützungsfunktion verwenden. **Nicht konfiguriert** deaktiviert dieses Feature.
- **Steuerelement zum Umkehren von Farben**: **Zulassen** von Farbumkehr-Änderungen, mit denen der Benutzer die Funktion zur Farbumkehr individuell verwenden kann. **Nicht konfiguriert** deaktiviert dieses Feature.
- **Ausgewählten Text sprechen**: **Zulassen** der Sprachauswahl-Barrierefreiheitseinstellungen auf dem Gerät. Diese Funktion liest Text, den der Benutzer auswählt, laut vor. **Nicht konfiguriert** deaktiviert dieses Feature.
- **Änderung der Sprachsteuerung**: **erlauben** Sie Benutzern, den Zustand der Sprachsteuerung auf Ihren Geräten zu ändern. **Nicht konfiguriert** hindert Benutzer daran, den Zustand der Sprachsteuerung auf Ihren Geräten zu ändern.

  Diese Einstellung gilt für:  
  - iOS 13.0 und neuer
  - iOS 13.0 und höher

- **VoiceOver-Steuerelement**: **Zulassen** von VoiceOver-Änderungen, damit Benutzer die VoiceOver-Funktion aktualisieren können, z. B. wie schnell auf dem Bildschirm ausgegebener Text von der Sprachausgabe vorgelesen wird. **Nicht konfiguriert** verhindert VoiceOver-Änderungen.
- **Zoomsteuerelement**: **Zulassen** von Zoomänderungen durch den Benutzer. **Nicht konfiguriert** verhindert Zoomänderungen.

> [!NOTE]
> Damit Sie ein iOS-Gerät für den Kioskmodus konfigurieren können, müssen Sie das Apple Configurator-Tool oder das Apple-Programm zur Geräteregistrierung verwenden, um das Gerät in den überwachten Modus zu versetzen. Informationen zur Verwendung des Apple Configurator-Tools finden Sie im Apple-Handbuch.
> Wenn die iOS-App, die Sie eingeben, nach der Zuweisung des Profils installiert wird, wird das Gerät erst nach einem Neustart in den Kioskmodus versetzt.

## <a name="domains"></a>Domains

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Einstellungen gelten für: Geräteregistrierung, automatisierte Geräteregistrierung (überwacht)

- **Nicht markierte E-Mail-Domänen** > **E-Mail-Domänen-URL**: Fügen Sie der Liste eine oder mehrere URLs hinzu. Wenn Endbenutzer eine E-Mail von einer anderen Domäne als den von Ihnen eingegebenen erhalten, wird die E-Mail in der iOS-Mail-App als nicht vertrauenswürdig gekennzeichnet.

- **Verwaltete Webdomänen** > **Webdomänen-URL**: Fügen Sie der Liste eine oder mehrere URLs hinzu. Wenn Dokumente von den Domänen, die Sie eingeben, heruntergeladen werden, gelten sie als verwaltet. Diese Einstellung gilt nur für Dokumente, die mit dem Safari-Browser heruntergeladen werden.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Einstellungen gelten für: automatisierte Geräteregistrierung (überwacht)

- **Safari-Domänen für automatische Kennworteingabe** > **Domänen-URL**: Fügen Sie der Liste eine oder mehrere URLs hinzu. Benutzer können nur Webkennwörter von URLs in dieser Liste speichern. Diese Einstellung gilt nur für den Safari-Browser und Geräte im überwachten Modus. Wenn Sie keine URLs eingeben, können Kennwörter von allen Websites gespeichert werden.

  Diese Einstellung gilt für:  
  - iOS 9.3. und neuer

## <a name="settings-that-require-supervised-mode"></a>Einstellungen, die den überwachten Modus erfordern

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
>
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

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](../device-profile-assign.md) und [Überwachen von Profilen](../device-profile-monitor.md)

Sie können auch Gerätefeatures und -einstellungen auf [macOS](device-restrictions-macos.md)-Geräten einschränken.
