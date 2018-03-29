---
title: Einstellungen für Android- und Samsung KNOX-Richtlinien
description: Erstellen Sie Richtlinien, die Einstellungen und Features auf Android-Geräten steuern, die Sie mit Intune verwalten.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 10/20/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a75380f578eeea57b8f6e694923d84b42b844045
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="android-and-samsung-knox-standard-policy-settings-in-microsoft-intune"></a>Einstellungen für Android- und Samsung KNOX Standard-Richtlinien in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune bietet eine Vielzahl von integrierten allgemeinen Einstellungen, die Sie auf Android-Geräten konfigurieren können. Darüber hinaus können Sie OMA-URI-Werte (Open Mobile Alliance Uniform Resource Identifier) angeben, um benutzerdefinierte Einstellungen zu erstellen, die über Intune nicht verfügbar sind.

## <a name="general-configuration-policy"></a>Allgemeine Konfigurationsrichtlinie

Verwenden Sie die allgemeine **Android-Konfigurationsrichtlinie** von Intune zum Konfigurieren von Einstellungen für:

-   **Sicherheitseinstellungen für mobile Geräte**: Treffen Sie in einer Liste mit vordefinierten Einstellungen eine Auswahl, mit denen Sie eine Reihe von Features und Funktionen auf dem Gerät steuern können.

-   **Kiosk-Modus** (nur für Samsung KNOX Standard-Geräte): Sperren Sie ein Gerät, sodass nur bestimmte Features ausgeführt werden können. Beispielsweise können Sie festlegen, dass auf einem Gerät nur eine von Ihnen angegebene verwaltete App ausgeführt werden kann, oder Sie können die Lautstärkeregler eines Geräts deaktivieren. Diese Einstellungen können für ein Demomodell eines Geräts oder ein Gerät nützlich sein, das nur eine bestimmte Funktion ausführen soll, z. B. ein Point-of-Sale-Gerät.

-   **Kompatible und nicht kompatible Apps**: Geben Sie eine Liste von Apps an, die in Ihrem Unternehmen kompatibel bzw. nicht kompatibel sind. Auf Android- und iOS-Geräten können Sie mit dem **Bericht über nicht kompatible Apps** überprüfen, ob die vom Benutzer installierten Apps zu den als von Ihnen kompatibel angegebenen Apps gehören. Die Installation der App kann jedoch nicht durch den Bericht blockiert werden.

> [!TIP]
> Sie können Bestimmungen für Benutzer konfigurieren, um sicherzustellen, dass sie bestätigen, dass alle Apps auf ihrem Gerät, einschließlich persönlicher Apps, ausgewertet werden und dass nicht kompatible Anwendungen entweder blockiert oder als nicht kompatibel gemeldet werden. Benutzer müssen diese Bestimmungen akzeptieren, bevor sie ihr Gerät registrieren und Apps über das Unternehmensportal abrufen können. Weitere Informationen zur Verwendung von Geschäftsbedingungen finden Sie unter [Einstellungen für Geschäftsbedingungensrichtlinien in Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Wenn die gesuchte Einstellung nicht in diesem Thema enthalten ist, können Sie sie ggf. mithilfe einer benutzerdefinierten Android-Richtlinie erstellen, die Ihnen das Steuern des Geräts mithilfe von OMA-URI-Einstellungen erlaubt. Weitere Informationen finden Sie weiter unten in diesem Thema unter [Benutzerdefinierte Richtlinieneinstellungen](#custom-policy-settings).

### <a name="password-settings"></a>Kennworteinstellungen

|Name der Einstellung|Details|Android 4.0+|Samsung KNOX Standard|
|----------------|-|----------------|----------------|
|**Anfordern eines Kennworts zum Entsperren mobiler Geräte**|Gibt an, ob auf unterstützten Geräten ein Kennwort erforderlich ist.|Ja |Ja |
|**Minimale Kennwortlänge**|Gibt die Mindestlänge für das Kennwort an.|Ja |Ja |
|**Anzahl zulässiger wiederholter Anmeldefehler, bevor das Gerät zurückgesetzt wird**|Gibt die Anzahl zulässiger Anmeldefehler an, bevor das Gerät zurückgesetzt wird.|Ja |Ja |
|**Minuten der Inaktivität, bevor der Bildschirm ausgeschaltet wird**|Gibt die Anzahl der inaktiven Minuten an, bevor das Gerät automatisch gesperrt wird.|Ja |Ja |
|**Kennwortablauf (Tage)**|Gibt die Anzahl der Tage an, bevor das Kennwort geändert werden muss.|Ja |Ja |
|**Kennwortverlauf speichern**|Gibt die Anzahl der zuvor bereits verwendeten Kennwörter an, die gespeichert werden sollen.|Ja |Ja |
|**Kennwortverlauf speichern** - **Wiederverwendung vorheriger Kennwörter verhindern**|Verhindert die Wiederverwendung vorheriger Kennwörter.|Ja |Ja |
|**Kennwortqualität**|Gibt den erforderlichen Grad der Kennwortkomplexität an. Zudem wird angegeben, ob biometrische Geräte zulässig sind.|Ja |Ja |
|**Fingerabdruckentsperrung zulassen**|Lässt das Entsperren des Geräts mittels Fingerabdruck zu.|Nein|Ja |
|**Smart Lock und andere Vertrauens-Agents zulassen**<br>(Android 5 und höher)|Ermöglicht Ihnen die Steuerung der Smart Lock-Funktion auf kompatiblen Android-Geräten. Diese Telefonfunktion wird manchmal als Vertrauens-Agent bezeichnet und ermöglicht Ihnen das Deaktivieren oder Umgehen des Kennworts für den Gerätesperrbildschirm, wenn sich das Gerät an einem vertrauenswürdigen Standort befindet, (wenn es z. B. mit einem bestimmten Bluetooth-Gerät verbunden ist oder sich in der Nähe eines NFC-Tags befindet). Mit dieser Einstellung können Sie verhindern, dass Benutzer Smart Lock konfigurieren.|Ja |Nein|

### <a name="encryption-settings"></a>Verschlüsselungseinstellungen

|Name der Einstellung|Details|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Verschlüsselung auf mobilem Gerät anfordern**|Erfordert die Verschlüsselung von Dateien auf dem mobilen Gerät.|Ja |Ja |
|**Verschlüsselung auf Speicherkarten vorschreiben**|Gibt an, ob die Gerätespeicherkarte verschlüsselt werden muss.|Nein|Ja |

### <a name="system-settings"></a>Systemeinstellungen

|Name der Einstellung|Details|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Bildschirmaufnahme zulassen**|Ermöglicht dem Benutzer, den Bildschirminhalt als Bild zu erfassen.|Nein|Ja |
|**Übermitteln von Diagnosedaten zulassen**|Ermöglicht, dass das Gerät Diagnoseinformationen an Google übermittelt.|Nein|Ja |
|**Zurücksetzen auf Werkseinstellungen zulassen**|Ermöglicht dem Benutzer das Zurücksetzen des Geräts auf die Werkseinstellungen.|Nein|Ja |

### <a name="cloud-settings---documents-and-data"></a>Cloudeinstellungen – Dokumente und Daten

|Name der Einstellung|Details|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------------------|----------------|
|**Google-Sicherung zulassen**|Ermöglicht die Verwendung der Google-Sicherung.|Nein|Ja |

### <a name="cloud-settings---accounts-and-synchronization"></a>Cloudeinstellungen – Konten und Synchronisierung

|Name der Einstellung|Details|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Automatische Synchronisierung mit Google-Konto zulassen**|Ermöglicht die automatische Synchronisierung der Einstellungen von Google-Konten.|Nein|Ja |

### <a name="application-settings---browser"></a>Anwendungseinstellungen – Browser

|Name der Einstellung|Details|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Webbrowser zulassen**|Gibt an, ob der Standardwebbrowser des Geräts verwendet werden darf.|Nein|Ja |
|**AutoAusfüllen zulassen**|Ermöglicht die Verwendung der AutoAusfüllen-Funktion des Webbrowsers.|Nein|Ja |
|**Popupblocker zulassen**|Hiermit wird die Verwendung des Popupblockers im Webbrowser zugelassen.|Nein|Ja |
|**Cookies zulassen**|Ermöglicht die Verwendung von Cookies durch den Webbrowser des Geräts.|Nein|Ja |
|**Active Scripting zulassen**|Ermöglicht die Verwendung von Active Scripting durch den Webbrowser des Geräts.|Nein|Ja |

### <a name="application-settings---apps"></a>Anwendungseinstellungen – Apps

|Name der Einstellung|Details|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------|----------------|
|**Google Play Store zulassen**|Ermöglicht dem Benutzer den Zugriff auf den Google Play Store auf dem Gerät.|Nein|Ja |

### <a name="device-capabilities-settings---hardware"></a>Einstellungen für Gerätefunktionen - Hardware

|Name der Einstellung|Details|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Kamera zulassen**|Ermöglicht die Verwendung der Gerätekamera.|Ja |Ja |
|**Wechselspeichermedien zulassen**|Ermöglicht dem Gerät die Verwendung von Wechselmedien, z. B. SD-Karten.|Nein|Ja |
|**WLAN zulassen**|Ermöglicht die Verwendung der WLAN-Funktionen des Geräts.|Nein|Ja |
|**WLAN-Tethering zulassen**|Ermöglicht die Verwendung des WLAN-Tetherings auf dem Gerät.|Nein|Ja |
|**Geolocation zulassen**|Erlaubt dem Gerät die Nutzung von Standortinformationen.|Nein|Ja |
|**NFC zulassen**|Erlaubt Vorgänge, die NFC (Near Field Communication) verwenden, sofern dies vom Gerät unterstützt wird.|Nein|Ja |
|**Bluetooth zulassen**|Hiermit wird die Verwendung von Bluetooth auf dem Gerät zugelassen.|Nein|Ja |
|**Ausschalten zulassen**|Hiermit wird dem Benutzer das Ausschalten des Geräts gestattet.<br /><br />Wenn diese Einstellung deaktiviert ist, funktioniert die Einstellung **Anzahl der zulässigen wiederholten Anmeldefehler, bevor die Gerätedaten zurückgesetzt werden** für Samsung KNOX Standard-Geräte nicht.|Nein|Ja |

### <a name="device-capabilities-settings---cellular"></a>Einstellungen für Gerätefunktionen - Mobiltelefon

|Name der Einstellung|Details|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Sprachroaming zulassen**|Ermöglicht das Sprachroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.|Nein|Ja |
|**Datenroaming zulassen**|Ermöglicht das Datenroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.|Nein|Ja |
|**SMS/MMS-Messaging zulassen**|Ermöglicht die Verwendung von SMS- und MMS-Nachrichten auf dem Gerät.|Nein|Ja |

### <a name="device-capabilities-settings---features"></a>Einstellungen für Gerätefunktionen - Funktionen

|Name der Einstellung|Details|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------|----------------|
|**Sprach-Assistent zulassen**|Zulassen der Verwendung von Sprach-Assistent-Software auf dem Gerät.|Nein|Ja |
|**Sprachwahl zulassen**|Aktiviert oder deaktiviert die Verwendung des Features „Sprachwahlverfahren“ auf dem Gerät.|Nein|Ja |
|**Kopieren und Einfügen zulassen**|Ermöglicht Kopier- und Einfügefunktionen auf dem Gerät.|Nein|Ja |
|**Freigabe der Zwischenablage zwischen Anwendungen zulassen**|Ermöglicht die Verwendung der Zwischenablage zum Kopieren und Einfügen zwischen Apps.|Nein|Ja |
|**YouTube zulassen**|Ermöglicht die Verwendung von YouTube auf dem Gerät.|Nein|Ja |

### <a name="settings-for-compliant-and-noncompliant-apps"></a>Einstellungen für kompatible und nicht kompatible Anwendungen
Geben Sie in der Liste der **kompatiblen &amp; nicht kompatiblen Apps** eine Liste kompatibler oder nicht kompatibler Apps mit den folgenden Informationen ein:

> [!NOTE]
> Eine einzelne Richtlinie kann nur eine Liste kompatibler Apps oder eine Liste nicht kompatibler Apps enthalten. Sie können nicht beide Typen in derselben Richtlinie angeben.

|Name der Einstellung|Details|
|----------------|--------------------|
|**Nichtkompatibilität melden, wenn Benutzer die aufgelisteten Apps installieren**|Listet die Apps auf, die nicht von Intune verwaltet werden und die Benutzer nicht installieren und ausführen sollen. Wenn Benutzer diese Apps installieren, werden sie in den Berichten über nicht richtlinienkonforme Apps aufgeführt.|
|**Nichtkompatibilität nicht melden, wenn Benutzer die aufgelisteten Apps installieren**|Listet die Apps auf, die zulässig sein sollen. Um die Konformität zu gewährleisten, dürfen Benutzer keine Apps installieren, die in dieser Liste nicht aufgeführt sind. Apps, die von Intune verwaltet werden, sind automatisch zugelassen.|
|**Hinzufügen**|Fügt eine App zur ausgewählten Liste hinzu. Geben Sie den Namen der App, den Herausgeber der App (optional) sowie die URL zur App im App-Store an.<br /><br />Weitere Informationen finden Sie unter [Angeben von URLs zu App Stores](#specify-urls-to-app-stores) weiter unten in diesem Thema.|
|**Anwendungen importieren**|Importiert eine Liste von Apps, die Sie in einer CSV-Datei angegeben haben. Verwenden Sie in der Datei das Format Anwendungsname, Herausgeber und App-URL.|
|**Bearbeiten**|Ermöglicht Ihnen das Bearbeiten von Name, Herausgeber und URL der ausgewählten App.|
|**Löschen**|Löscht die ausgewählte App aus der Liste.|

Richtlinien mit kompatiblen und nicht kompatiblen App-Einstellungen müssen für Benutzergruppen bereitgestellt werden.

### <a name="kiosk-mode-settings"></a>Einstellungen für den Kioskmodus
Geben Sie die folgenden Einstellungen für **Samsung KNOX Standard-Geräte** an:

|Name der Einstellung|Details|
|----------------|--------------------|
|**Wählen Sie eine verwalteten App aus, die ausgeführt werden kann, während sich das Gerät im Kioskmodus befindet**|Wählen Sie **Durchsuchen**, und wählen Sie dann die verwaltete App aus, die ausgeführt werden kann, wenn sich das Gerät im Kioskmodus befindet (Apps, die als Link zum Store angegeben sind, werden derzeit nicht unterstützt). Andere Apps dürfen auf dem Gerät nicht ausgeführt werden.|
|**Lautstärkeregler zulassen**|Aktiviert oder deaktiviert die Verwendung der Lautstärkeregler am Gerät.|
|**Schaltfläche für Standby und Aktivieren zulassen**|Aktiviert oder deaktiviert die Taste für Standby/Aktivierung des Bildschirms am Gerät.|

### <a name="reference-information-for-compliant-and-noncompliant-apps"></a>Referenzinformationen für konforme und nicht konforme Apps

#### <a name="monitor-compliant-and-noncompliant-apps"></a>Überwachen konformer und nicht konformer Apps
Im **Bericht über nicht kompatible Apps** können Sie sich über die Konformität zulässiger und blockierter Anwendungen informieren.

###### <a name="to-run-the-noncompliant-apps-report"></a>So führen Sie den Bericht über nicht kompatible Apps aus

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Optionen **Berichte** &gt; **Bericht über nicht kompatible Apps**.

2.  Wählen Sie die Gerätegruppen aus, die Sie überprüfen möchten. Wählen Sie dann aus, ob Sie auf kompatible und/oder nicht kompatible Apps prüfen möchten. Wählen Sie abschließend **Bericht anzeigen** aus.

#### <a name="specify-urls-to-app-stores"></a>Angeben von URLs zu App-Stores
Verwenden Sie zum Festlegen einer App-URL in der Liste kompatibler und nicht kompatibler Apps die folgenden Schritte:

Suchen Sie im [Apps-Bereich von Google Play](https://play.google.com/store/apps) nach der App, die Sie verwenden möchten.

Öffnen Sie die Installationsseite für die App, und kopieren Sie dann die URL in die Zwischenablage. Jetzt können Sie diese als URL in der Liste mit konformen oder nicht konformen Apps verwenden.

Beispiel: Suchen Sie in Google Play nach Microsoft Office Mobile. Verwenden Sie die URL **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

## <a name="custom-policy-settings"></a>Benutzerdefinierte Richtlinieneinstellungen
Stellen Sie mithilfe der **benutzerdefinierten Android-Konfigurationsrichtlinie** von Microsoft Intune die Einstellungen für OMA-URI bereit, um Features auf Android-Geräten zu steuern. Dies sind die Standardeinstellungen, die viele Hersteller von mobilen Geräten verwenden, um Gerätefunktionen zu steuern.

Diese Funktion soll es Ihnen ermöglichen, Android-Einstellungen bereitzustellen, die nicht mit Intune-Richtlinien konfigurierbar sind.
Intune unterstützt zurzeit eine begrenzte Anzahl von benutzerdefinierten Android-Richtlinien. Mit den Beispielen in diesem Thema finden Sie heraus, welche Richtlinien Sie konfigurieren können.

### <a name="general-settings"></a>Allgemeine Einstellungen

|Name der Einstellung|Details|
    |----------------|--------------------|
    | **Name** |Geben Sie einen eindeutigen Namen für die benutzerdefinierte Android-Richtlinie ein, damit Sie sie leichter in der Intune-Konsole identifizieren können.|
    | **Beschreibung** |Geben Sie eine Beschreibung ein, die einen Überblick über die Richtlinie bietet, und andere relevante Informationen, die Ihnen die Suche danach erleichtern.|

### <a name="oma-uri-settings"></a>OMA-URI-Einstellungen

   |Name der Einstellung|Details|
    |--------|--------------------|
    | **Einstellungsname** |Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung ein, damit Sie sie in der Liste der Einstellungen leichter identifizieren können.|
    | **Einstellungsbeschreibung** |Geben Sie eine Beschreibung ein, die einen Überblick über die Einstellung bietet, und andere relevante Informationen, die Ihnen die Suche danach erleichtern.|
    | **Datentyp** |Wählen Sie den Datentyp aus, in dem Sie diese OMA-URI-Einstellung angeben. Wählen Sie aus **Zeichenfolge, Zeichenfolge (XML), Datum und Uhrzeit, ganze Zahl, Gleitkomma** oder **Boolesch** aus.|
    | **OMA-URI (Groß-/Kleinschreibung beachten)** |Geben Sie den OMA-URI an, für den Sie eine Einstellung festlegen möchten.|
    | **Wert** |Geben Sie den mit der zuvor festgelegten OMA-URI-Einstellung zu verknüpfenden Wert an.|

### <a name="examples"></a>Beispiele

- [Erstellen eines WLAN-Profils über einen vorinstallierten Schlüssel](pre-shared-key-wi-fi-profile.md)
- [Verwenden einer benutzerdefinierten Richtlinie zum Erstellen eines Profils für ein App-bezogenes VPN für Android-Geräte](per-app-vpn-for-android-pulse-secure.md)
- [Verwenden von benutzerdefinierten Richtlinien zum Zulassen und Blockieren von Apps für Samsung KNOX-Geräte](custom-policy-to-allow-and-block-samsung-knox-apps.md)

## <a name="supported-samsung-knox-standard-devices"></a>Unterstützte Samsung KNOX Standard-Geräte

Die Unternehmensportal-App führt während der MDM-Registrierung nur dann einen Aktivierungsversuch für Samsung KNOX durch, wenn das Gerät in der [Liste der unterstützten KNOX-Geräte](https://www.samsungknox.com/knox-supported-devices/knox-workspace) angezeigt wird. Dadurch werden für KNOX Aktivierungsfehler vermieden, die eine MDM-Registrierung verhindern würden. Geräte, die die Samsung KNOX-Aktivierung nicht unterstützen, werden als Android-Standardgeräte registriert. Wenn für ein Samsung-Gerät mehrere Modellnummern vorhanden sind, wird KNOX möglicherweise nicht von allen Modellen unterstützt. Überprüfen Sie daher mithilfe des Wiederverkäufers Ihrer Geräte, ob diese mit KNOX kompatibel sind, bevor Sie Samsung-Geräte erwerben und bereitstellen.

Sie finden eine Liste der unterstützten Samsung KNOX-Geräte sowie die Liste der von [Intune unterstützten Geräte](/intune/supported-devices-browsers.md#intune-supported-devices).

### <a name="see-also"></a>Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
