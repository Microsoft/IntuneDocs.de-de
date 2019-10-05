---
title: Einstellungen für Geräteeinschränkungen für Android in Microsoft Intune – Azure | Microsoft-Dokumentation
description: 'Hier finden Sie eine Liste aller Android-Geräteeinstellungen, die Sie in Microsoft Intune steuern und einschränken können. Mit diesen Einstellungen können Sie Folgendes steuern: Kennwort, Zugriff auf Google Play, Zulassen oder Verbieten von Apps, Steuern der Browsereinstellungen, Blockieren von Apps, Sicherung in der Google-Cloud sowie Steuern der Optionen für Nachrichten, Spracheinstellungen, Datenroaming, WLAN und Bluetooth-Verbindungen.'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a1eac5b7959232fe747dd8ba87546269ff7a95af
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734933"
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-lists-in-intune"></a>Listen der Standardeinstellungen für Geräteeinschränkungen für Android und Samsung KNOX in Intune

In diesem Artikel lernen Sie alle Einstellungen für Geräteeinschränkungen in Microsoft Intune kennen, die Sie für Android-Geräte konfigurieren können.

>[!TIP]
>Wenn Ihre gewünschten Einstellungen nicht verfügbar sind, können Sie Ihre Geräte möglicherweise mit einem [benutzerdefinierten Profil](../custom-settings-android.md) konfigurieren.

## <a name="general"></a>Allgemein

- **Kamera**: Wählen Sie **Blockieren** aus, um den Zugriff auf die Kamera zu verhindern. **Nicht konfiguriert** ermöglicht den Zugriff auf die Kamera des Geräts.
- **Kopieren und einfügen (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um Kopieren und Einfügen zu verhindern. **Nicht konfiguriert** lässt Kopier- und Einfügefunktionen auf dem Gerät zu.
- **Gemeinsame Nutzung der Zwischenablage durch Apps (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um die Verwendung der Zwischenablage für das Kopieren und Einfügen zwischen Apps zu verhindern. **Nicht konfiguriert** ermöglicht die Verwendung der Zwischenablage zum Kopieren und Einfügen zwischen Apps.
- **Übermittlung von Diagnosedaten (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um den Benutzer an der Übermittlung von Diagnosedaten vom Gerät zu hindern. **Nicht konfiguriert** ermöglicht dem Benutzer, Daten zu übermitteln.
- **Zurücksetzung auf Werkseinstellungen (nur Samsung KNOX)** : Erlaubt dem Benutzer das [Zurücksetzen](../remote-actions/devices-wipe.md) des Geräts.
- **Geolocation (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um die Verwendung von Standortinformationen durch das Gerät zu deaktivieren. **Nicht konfiguriert** erlaubt dem Gerät die Nutzung von Standortinformationen.
- **Ausschalten (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um zu verhindern, dass der Benutzer das Gerät ausschaltet. Wenn diese Einstellung deaktiviert ist, kann die Einstellung **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird** nicht festgelegt werden und funktioniert nicht. **Nicht konfiguriert** erlaubt dem Benutzer das Ausschalten des Geräts.
- **Bildschirmaufnahme (nur Samsung Knox)** : Wählen Sie **Blockieren** aus, um Screenshots zu verhindern. **Nicht konfiguriert** erlaubt dem Benutzer, den Bildschirminhalt als Bild zu erfassen.
- **Sprach-Assistent (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um den S Voice-Dienst zu deaktivieren. **Nicht konfiguriert** erlaubt die Verwendung des S Voice-Diensts und der -App auf dem Gerät. Diese Einstellung gilt nicht für Bixby oder den Sprach-Assistenten für die Bedienungshilfe, der den Bildschirminhalt laut vorliest.
- **YouTube (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer die YouTube-App verwenden. **Nicht konfiguriert** ermöglicht die Verwendung der YouTube-App auf dem Gerät.
- **Freigegebene Geräte (nur Samsung KNOX)** : Konfigurieren Sie ein verwaltetes Samsung KNOX Standard-Gerät als freigegeben. Bei Festlegung auf **Zulassen** können sich Endbenutzer des Geräts mit ihren Azure AD-Anmeldeinformationen an- und abmelden. Das Gerät wird weiterhin verwaltet, ganz gleich, ob es verwendet wird oder nicht.</br>In Verbindung mit einem SCEP-Zertifikatsprofil ermöglicht diese Funktion Endbenutzern die gemeinsame Nutzung eines Geräts mit denselben Apps für alle Benutzer. Aber jeder Benutzer verfügt über ein eigenes SCEP-Benutzerzertifikat. Wenn sich Benutzer abmelden, werden alle App-Daten gelöscht. Dieses Feature ist ausschließlich auf branchenspezifische Apps beschränkt. </br>**Nicht konfiguriert** verhindert, dass mehrere Endbenutzer sich bei der Unternehmensportal-App auf dem Gerät mit ihren Azure AD-Anmeldeinformationen anmelden.
- **Datums- und Uhrzeitänderungen blockieren (Samsung KNOX)** : Wählen Sie **Blockieren** aus, um zu verhindern, dass der Benutzer Datums- und Uhrzeiteinstellungen auf dem Gerät ändert. **Nicht konfiguriert** ermöglicht dem Benutzer, die Datums- und Uhrzeiteinstellungen zu ändern.

## <a name="password"></a>Kennwort

- **Kennwort**: **Anfordern** der Eingabe eines Kennworts durch den Endbenutzer, um auf das Gerät zugreifen zu können. **Nicht konfiguriert** ermöglicht Benutzern, ohne Kennworteingabe auf das Gerät zuzugreifen.

    > [!NOTE]
    > Samsung Knox-Geräte erfordern automatisch eine vierstellige PIN bei der MDM-Registrierung. Native Android-Geräte erfordern möglicherweise automatisch eine PIN, damit sie mit den bedingten Zugriffsvoraussetzungen konform sind.

- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl von Zeichen an, die Benutzer für das Kennwort festlegen müssen (zwischen 4 und 16 Zeichen).
- **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung**: Geben Sie an, wie viele Minuten ein Gerät höchstens inaktiv sein darf, bevor es automatisch gesperrt wird. Ein Endbenutzer kann auf dem Gerät keinen höheren Wert als die im Profil konfigurierte Zeit festlegen. Der Endbenutzer kann einen niedrigeren Zeitwert festlegen. Wenn das Profil auf 15 Minuten festgelegt ist, kann ein Endbenutzer den Wert auf 5 Minuten festlegen, aber nicht auf 30 Minuten. 
- **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird**: Geben Sie die Anzahl zulässiger Anmeldefehler ein, bevor das Gerät zurückgesetzt wird.
- **Kennwortablauf (Tage)** : Geben Sie die Anzahl der Tage an, nach denen das Gerätekennwort geändert werden muss.
- **Erforderlicher Kennworttyp**: Geben Sie den erforderlichen Grad der Kennwortkomplexität an und ob biometrische Geräte zulässig sind. Folgende Optionen sind verfügbar:
  - **Gerätestandard**
  - **Biometrie auf niedriger Sicherheitsstufe**
  - **Mindestens numerisch**
  - **Numerisch komplex**: Sich wiederholende oder fortlaufende Ziffern wie „1111“ oder „1234“ sind nicht zulässig.<sup>1</sup>
  - **Mindestens alphabetisch**
  - **Mindestens alphanumerisch**
  - **Mindestens alphanumerisch mit Symbolen**
- **Wiederverwendung vorheriger Kennwörter verhindern**: Hindert den Endbenutzer daran, ein bereits verwendetes Kennwort erneut festzulegen.
- **Entsperrung durch Fingerabdruck (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um die Verwendung eines Fingerabdrucks zum Entsperren des Geräts zu verhindern. **Nicht konfiguriert** ermöglicht dem Benutzer das Entsperren des Geräts mittels Fingerabdruck.
- **Smart Lock und andere Vertrauens-Agents**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Smart Lock oder andere Vertrauens-Agents (Samsung KNOX Standard 5.0 und höher) Sperrbildschirmeinstellungen anpassen. Dieses Telefonfeature wird manchmal auch als Vertrauens-Agent bezeichnet und ermöglicht Ihnen, das Kennwort für den Gerätesperrbildschirm zu deaktivieren oder zu umgehen, wenn sich das Gerät an einem vertrauenswürdigen Standort befindet. Dieses Feature kann beispielsweise verwendet werden, wenn das Gerät mit einem bestimmten Bluetooth-Gerät verbunden ist oder sich in der Nähe eines NFC-Tags befindet. Mit dieser Einstellung können Sie verhindern, dass Benutzer Smart Lock konfigurieren.
- **Verschlüsselung**: Wählen Sie **Anfordern** aus, sodass die Dateien auf dem Gerät verschlüsselt werden. Nicht alle Geräte unterstützen die Verschlüsselung. Legen Sie zur Nutzung dieser Funktion außerdem Folgendes fest: 
  1. Legen Sie für **Kennwort** **Anfordern** fest.
  2. Legen Sie für **Erforderlicher Kennworttyp** **Mindestens numerisch** fest.
  3. Legen Sie für **Minimale Kennwortlänge** mindestens 4 fest, um ordnungsgemäß Kompatibilität für diese Einstellung zu melden.

  > [!NOTE]
  > Wenn eine Verschlüsselungsrichtlinie erzwungen wird, erfordern Samsung Knox-Geräte, dass Benutzer ein komplexes Kennwort, das aus sechs Zeichen besteht, für die Gerätekennung festlegen.

<sup>1</sup> Bevor Sie diese Einstellung Geräten zuweisen, aktualisieren Sie die Unternehmensportal-App auf diesen Geräten auf jeden Fall auf die neueste Version.

Wenn Sie für **Erforderlicher Kennworttyp** **Numerisch komplex** festlegen und dies dann einem Gerät mit einer früheren Android-Version als 5.0 zuweisen, gilt das folgende Verhalten:

- Wenn die Unternehmensportal-App eine ältere Version als 1704 ausführt, wird keine PIN-Richtlinie auf das Gerät angewendet, und eine Fehlermeldung wird im Azure-Portal angezeigt.
- Wenn die Unternehmensportal-App die Version 1704 oder höher ausführt, kann nur eine einfache PIN angewendet werden. Frühere Android-Versionen als 5.0 unterstützen diese Einstellung nicht. Im Azure-Portal wird kein Fehler angezeigt.

## <a name="google-play-store"></a>Google Play Store

- **Google Play Store (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer den Google Play Store verwenden. **Nicht konfiguriert** ermöglicht dem Benutzer den Zugriff auf den Google Play Store auf dem Gerät.

## <a name="restricted-apps"></a>Eingeschränkte Apps

Verwenden Sie diese Einstellungen, um bestimmte Apps auf dem Gerät zuzulassen oder zu verhindern. Dieses Feature wird auf Android- und Samsung KNOX Standard-Geräten unterstützt:

- **Unzulässige Apps**: Eine Liste nicht von Intune verwalteter Apps, die nicht auf dem Gerät installiert werden sollen. Wenn ein Benutzer eine App aus dieser Liste installiert, werden Sie von Intune benachrichtigt.
- **Genehmigte Apps**: Eine Liste von Apps, die Benutzer installieren dürfen. Um die Kompatibilität zu gewährleisten, dürfen Benutzer keine anderen Apps installieren. Apps, die von Intune verwaltet werden, sind automatisch zugelassen.

Um diesen Listen Apps hinzuzufügen, können Sie:

- Die Google Play Store-URL der App, die Sie wünschen, **hinzufügen**. Um z.B. die Microsoft-Remotedesktop-App für Android hinzuzufügen, geben Sie `https://play.google.com/store/apps/details?id=com.microsoft.rdc.android` ein. Um die URL einer App zu suchen, öffnen Sie den [Google Play Store](https://play.google.com/store/apps), und suchen Sie nach der App. Suchen Sie beispielsweise nach `Microsoft Remote Desktop Play Store` oder `Microsoft Planner`. Wählen Sie die App aus, und kopieren Sie die URL.
- Importieren Sie eine CSV-Datei mit den Details der App, einschließlich der URL. Verwenden Sie das Format <*App-URL*>, <*App-Name*>, <*App-Herausgeber*>. **Exportieren** Sie alternativ eine vorhandene Liste, die die Liste der eingeschränkten Apps im gleichen Format enthält.

> [!IMPORTANT]
> Geräteprofile, die Einstellungen für eingeschränkte Apps verwenden, müssen Benutzergruppen zugewiesen werden.

## <a name="browser"></a>Browser

- **Webbrowser (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um zu verhindern, dass der Standardwebbrowser auf dem Gerät verwendet wird. **Nicht konfiguriert** ermöglicht die Verwendung des Standardwebbrowsers des Geräts.
- **AutoAusfüllen (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um das automatische Ausfüllen von Text im Browser zu verhindern. **Nicht konfiguriert** ermöglicht die Verwendung der AutoAusfüllen-Funktion des Webbrowsers.
- **Cookies (nur Samsung KNOX)** : Wählen Sie aus, wie Sie mit Cookies von Websites auf dem Gerät umgehen möchten. Folgende Optionen sind verfügbar:
  - Zulassen
  - Alle Cookies blockieren
  - Cookies von besuchten Websites zulassen
  - Cookies von aktueller Website zulassen
- **JavaScript (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um zu verhindern, dass der Webbrowser Java-Skripts ausführt. **Nicht konfiguriert** ermöglicht die Ausführung von Java-Skripts im Webbrowser des Geräts.
- **Popups (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um Popups im Webbrowser zu verhindern. **Nicht konfiguriert** lässt Popups im Webbrowser zu.

## <a name="allow-or-block-apps"></a>Zulassen oder Blockieren von Apps

Verwenden Sie diese Einstellungen zum Zulassen und Blockieren bzw. Ausblenden bestimmter Apps auf Samsung KNOX Standard-Geräten. Ausgeblendete Apps können nicht vom Benutzer geöffnet oder ausgeführt werden.

Folgende Optionen sind verfügbar:

- **Zur Installation zugelassene Apps (nur Samsung KNOX Standard)**
- **Apps, deren Start blockiert wird (nur Samsung KNOX Standard)**
- **Für den Benutzer ausgeblendete Apps (nur Samsung KNOX Standard)**

Fügen Sie für jede Einstellung eine Liste von Apps hinzu. Folgende Optionen sind verfügbar:

- **Apps nach Paketname hinzufügen**: Wird in erster Linie für Geschäftsanwendungen verwendet. Geben Sie den Namen der App und den Namen des App-Pakets ein.
- **Apps nach URL hinzufügen**: Geben Sie den Namen der App und ihre URL im Google Play Store ein.
- **Store-App hinzufügen**: Wählen Sie eine App aus der vorhandenen Liste von Apps aus, die Sie in Intune verwalten.

## <a name="cloud-and-storage"></a>Cloud und Speicher

- **Google-Sicherung (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um zu verhindern, dass das Gerät mit der Google-Sicherung synchronisiert wird. **Nicht konfiguriert** erlaubt die Verwendung der Google-Sicherung.
- **Automatische Synchronisierung des Google-Kontos (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um die automatische Synchronisierung des Google-Kontos auf dem Gerät zu verhindern. **Nicht konfiguriert** erlaubt die automatische Synchronisierung der Einstellungen von Google-Konten.
- **Wechselmedien (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um den Einsatz von Wechselmedien auf dem Gerät zu verhindern. **Nicht konfiguriert** ermöglicht dem Gerät die Verwendung von Wechselmedien, z.B. SD-Karten.
- **Verschlüsselung auf Speicherkarten (nur Samsung KNOX)** : **Anfordern** erzwingt die Verschlüsselung von Speicherkarten. **Nicht konfiguriert** ermöglicht die Verwendung unverschlüsselter Speicherkarten. Nicht alle Geräte unterstützen die Speicherkartenverschlüsselung. Wenden Sie sich zur Bestätigung an den Gerätehersteller.

## <a name="cellular-and-connectivity"></a>Mobilfunk und Konnektivität

- **Datenroaming (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um Datenroaming über das Mobilfunknetz zu verhindern. **Nicht konfiguriert** ermöglicht das Datenroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.
- **SMS-/MMS-Nachrichten (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um Textnachrichten auf dem Gerät zu verhindern. **Nicht konfiguriert** ermöglicht die Verwendung von SMS- und MMS-Nachrichten auf dem Gerät.
- **Sprachwahlverfahren (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um zu verhindern, dass Benutzer das Sprachwahlverfahren auf dem Gerät verwenden. **Nicht konfiguriert** ermöglicht die Verwendung des Sprachwahlverfahrens auf dem Gerät.
- **Sprachroaming (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um Sprachroaming über das Mobilfunknetz zu verhindern. **Nicht konfiguriert** ermöglicht das Sprachroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.
- **Bluetooth (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um die Verwendung von Bluetooth auf dem Gerät zu verhindern. **Nicht konfiguriert** ermöglicht die Verwendung von Bluetooth auf dem Gerät.
- **NFC (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um die Near Field Communication-Technologie (NFC) zu beenden. **Nicht konfiguriert** ermöglicht Vorgänge, bei dem NFC (Near Field Communication) auf unterstützten Geräten zum Einsatz kommt.
- **WLAN (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um die WLAN-Verwendung auf dem Gerät zu verhindern. **Nicht konfiguriert** ermöglicht die Verwendung der WLAN-Features auf dem Gerät.
- **WLAN-Tethering (nur Samsung KNOX)** : Wählen Sie **Blockieren** aus, um die WLAN-Tethering-Verwendung auf dem Gerät zu verhindern. **Nicht konfiguriert** ermöglicht die Verwendung des WLAN-Tetherings auf dem Gerät.

## <a name="kiosk"></a>Kiosk

Kioskeinstellungen gelten nur für Samsung KNOX Standard-Geräte, und nur für Apps, die Sie mit Intune verwalten.

- Fügen Sie Apps hinzu, die Sie im Kioskmodus des Geräts ausführen möchten. Im Kioskmodus werden nur die Apps ausgeführt, die Sie hinzufügen; nicht hinzugefügte Apps werden nicht ausgeführt. Vorinstallierte Browser werden nicht ausgeführt, wenn das Gerät sich im Kioskmodus befindet. Wenn ein Browser erforderlich ist, erwägen Sie den Einsatz von [Managed Browser](../apps/app-configuration-managed-browser.md).

  Ihre App-Optionen sind:

  - **Apps nach Paketname hinzufügen**: Wird in erster Linie für Geschäftsanwendungen verwendet. Geben Sie den Namen der App und den Namen des App-Pakets ein.
  - **Apps nach URL hinzufügen**: Geben Sie den Namen der App und ihre URL im Google Play Store ein.
  - **Store-App hinzufügen**: Wählen Sie eine App aus der vorhandenen Liste von Apps aus, die Sie in Intune verwalten.

- **Standbytaste**: Wählen Sie **Blockieren** aus, um die Funktion der Standbytaste zu verhindern oder sie auszublenden. **Nicht konfiguriert** ermöglicht die Verwendung der Standbytaste am Gerät.
- **Lautstärkeregler**: Wählen Sie **Blockieren** aus, um durch Deaktivieren der Lautstärkeregler zu verhindern, dass der Benutzer die Lautstärke einstellt. **Nicht konfiguriert** ermöglicht die Verwendung der Lautstärkeregler am Gerät.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](../device-profile-assign.md) und [Überwachen von Profilen](../device-profile-monitor.md)

Außerdem können Sie Kioskmodusprofile für [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)- und [Windows 10](kiosk-settings.md)-Geräte erstellen.
