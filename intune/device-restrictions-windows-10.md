---
title: Intune-Einstellungen für Geräteeinschränkungen für Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Eine Liste mit allen Einstellungen und ihren Beschreibungen zum Erstellen von Geräteeinschränkungen für Windows 10 und höher wird angezeigt. Verwenden Sie diese Einstellungen in einem Konfigurationsprofil zum Steuern von Screenshots, Kennwortanforderungen, Kioskeinstellungen, Apps im Store, Microsoft Edge-Browser, Windows Defender, Cloudzugriff, Startmenü und mehr in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.openlocfilehash: e297169757f1bcc703ce698302ce6f7129104827
ms.sourcegitcommit: 0142020a7cd75348c6367facf072ed94238e667f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2019
ms.locfileid: "55230119"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Einstellungen für Windows 10-Geräte (und höher) zum Zulassen oder Einschränken von Features mit Intune

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie auf Geräten mit Windows 10 und höher festlegen können. Verwenden Sie diese Einstellungen als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM), um Features zuzulassen oder zu deaktivieren, Kennwortregeln festzulegen, den Sperrbildschirm anzupassen, Windows Defender zu verwenden usw.

Diese Einstellungen werden erst einem Gerätekonfigurationsprofil in Intune hinzugefügt und dann Ihren Windows 10-Geräten zugewiesen oder für diese bereitgestellt.

> [!Note]
> Nicht alle Optionen sind in allen Windows-Editionen verfügbar.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](device-restrictions-configure.md)

## <a name="app-store"></a>App Store

- **App Store (nur mobil)**: aktiviert oder blockiert die Verwendung des App Stores auf Windows 10 Mobile-Geräten.
- **Apps aus Store automatisch aktualisieren**: Apps aus dem Microsoft Store können automatisch aktualisiert werden.
- **Installation vertrauenswürdiger Apps**: Ermöglicht das Querladen von Apps, die mit einem vertrauenswürdigen Zertifikat signiert sind.
- **Entwicklersperre aufheben**: Ermöglicht dem Endbenutzer, Windows-Entwicklereinstellungen – z.B. das Zulassen quergeladener Apps – zu ändern.
- **Gemeinsam genutzte App-Benutzerdaten:** erlaubt Apps, die gemeinsame Nutzung von Daten durch verschiedene Benutzer auf dem gleichen Gerät zuzulassen.
- **Nur privaten Store verwenden:** aktivieren Sie diese Option, um Benutzern das Herunterladen von Apps aus Ihrem privaten Store zu erlauben.
- **Store-App starten:** Mit dieser Option deaktivieren Sie auf Geräten alle Apps, die vorinstalliert waren oder aus dem Microsoft Store heruntergeladen wurden.
- **App-Daten in Systemvolume installieren:** hindert Apps daran, Daten im Systemvolume des Geräts zu speichern.
- **Apps auf Systemlaufwerk installieren:** hindert Apps daran, Daten auf dem Systemlaufwerk des Geräts zu speichern.
- **Game DVR (nur Desktop):** konfiguriert, ob Aufzeichnen und Übertragen von Spielen zulässig ist.
- **Apps from the store only** (Nur Apps aus dem Store): konfiguriert, ob Benutzer Apps von anderen Orten als aus dem App Store installieren können.

## <a name="cellular-and-connectivity"></a>Mobilfunk und Konnektivität

- **Mobilfunkdatenkanal:** verhindert, dass Benutzer z. B. beim Browsen im Web Daten verbrauchen, wenn sie mit einem Mobilfunknetz verbunden sind. 
- **Datenroaming:** Ermöglicht beim Zugriff auf Daten das Roaming zwischen Netzwerken.
- **VPN over the cellular network** (VPN über das Mobilfunknetz): Steuert, ob das Gerät auf VPN-Verbindungen zugreifen kann, wenn es mit einem Mobilfunknetz verbunden ist.
- **VPN roaming over the cellular network** (VPN-Roaming über das Mobilfunknetz): Steuert, ob das Gerät beim Roaming in einem Mobilfunknetz auf VPN-Verbindungen zugreifen kann.
- **Bluetooth**: Steuert, ob der Benutzer Bluetooth auf dem Gerät aktivieren und konfigurieren kann.
- **Bluetooth-Erkennbarkeit**: Ermöglicht die Erkennung dieses Geräts durch andere Bluetooth-Geräte.
- **Bluetooth-Vorabkopplung:** ermöglicht das Konfigurieren spezifischer Bluetooth-Geräte für automatisches Koppeln mit einem Hostgerät.
- **Bluetooth-Ankündigung**: Ermöglicht Geräten den Empfang von Ankündigungen über Bluetooth.
- **Dienst für verbundene Geräte:** ermöglicht die Entscheidung, ob dem Dienst für verbundene Geräte die Ermittlung von und Verbindung mit anderen Bluetooth-Geräten erlaubt wird.
- **NFC:** erlaubt dem Benutzer das Aktivieren und Konfigurieren von NFC-Features (Near Field Communication) auf dem Gerät.
- **WLAN:** erlaubt dem Benutzer das Aktivieren und Konfigurieren von WLAN auf dem Gerät (nur Windows 10 Mobile).
- **Automatically connect to Wi-Fi hotspots** (Automatische Verbindung mit WLAN-Hotspots): Ermöglicht automatische Verbindungen des Geräts mit unverschlüsselten WLAN-Hotspots und das automatische Akzeptieren der Geschäftsbedingungen für die Verbindung.
- **Manuelle WLAN-Konfiguration:** steuert, ob die Benutzer eigene WLAN-Verbindungen konfigurieren dürfen oder ob nur über WLAN-Profile konfigurierte Verbindungen (nur bei Windows 10 Mobile) verwendet werden dürfen.
- **Intervall für WLAN-Suche:** gibt an, wie oft Geräte nach WLAN-Netzwerken suchen. Geben Sie einen Wert zwischen 1 (am häufigsten) und 500 (am seltensten) an.
- **Zulässige Bluetooth-Dienste:** gibt in Form von hexadezimalen Zeichenfolgen eine Liste zulässiger Bluetooth-Dienste und -Profile an.

## <a name="cloud-and-storage"></a>Cloud und Speicher

- **Microsoft-Konto**: Ermöglicht dem Benutzer, das Gerät einem Microsoft-Konto zuzuordnen.
- **Nicht-Microsoft-Konto:** erlaubt dem Benutzer, dem Gerät E-Mail-Konten hinzuzufügen, die nicht mit einem Microsoft-Konto verknüpft sind.
- **Settings synchronization for Microsoft account** (Einstellungssynchronisierung für das Microsoft-Konto): ermöglicht das Synchronisieren der mit einem Microsoft-Konto verknüpften Geräte- und App-Einstellungen zwischen Geräten.

## <a name="cloud-printer"></a>Clouddrucker

- **URL für Druckerermittlung:** Geben Sie die URL zum Finden von Clouddruckern ein.
- **Autoritäts-URL für Druckerzugriff:** Geben Sie die Authentifizierungsendpunkt-URL zum Abrufen von OAuth-Token ein. Geben Sie zum Beispiel `https://login.microsoftonline.com/your Azure AD Tenant ID` ein.
- **GUID für native Azure-Client-App:** Geben Sie die GUID einer Clientanwendung ein, die OAuth-Token von der OAuthAuthority abrufen darf.
- **Druckdienstressourcen-URI:** Geben Sie den OAuth-Ressourcen-URI für den im Azure-Portal konfigurierten Druckdienst ein. Geben Sie zum Beispiel `http://MicrosoftEnterpriseCloudPrint/CloudPrint` ein.
- **Maximum printers to query (Mobile only)** (Maximal abgefragte Drucker (nur Mobilgeräte)): geben Sie die maximale Anzahl von Druckern ein, die abgefragt werden sollen. Geben Sie beispielsweise `10` ein.
- **Ressourcen-URI für Druckerermittlungsdienst:** Geben Sie den OAuth-Ressourcen-URI für den im Azure-Portal konfigurierten Druckererkennungsdienst ein. Geben Sie zum Beispiel `http://MopriaDiscoveryService/CloudPrint` ein.

> [!TIP]
> Nachdem Sie [Windows Server Hybrid Cloud Print](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview) eingerichtet haben, können Sie diese Einstellungen konfigurieren und auf Windows-Geräten bereitstellen.

## <a name="control-panel-and-settings"></a>Systemsteuerung und Einstellungen

- **App „Einstellungen“:** blockiert den Zugriff auf die Windows-App „Einstellungen“.
  - **System:** blockiert den Zugriff auf den Systembereich der App „Einstellungen“.
    - **Power and sleep settings modification (desktop only)** (Änderung der Energie- und Energiesparmoduseinstellungen (nur Desktopgeräte)): hindert Benutzer daran, die Einstellungen für die Stromversorgung und den Standbymodus zu ändern
  - **Geräte:** blockiert den Zugriff auf den Gerätebereich der App „Einstellungen“.
  - **Netzwerk und Internet:** blockiert den Zugriff auf den Netzwerk- und Internetbereich der App „Einstellungen“.
  - **Personalisierung:** blockiert den Zugriff auf den Personalisierungsbereich der App „Einstellungen“.
  - **Konten**: blockiert den Zugriff auf den Kontenbereich der App „Einstellungen“.
  - **Time and Language** (Zeit und Sprache): blockiert den Zugriff auf den Zeit- und Sprachenbereich der App „Einstellungen“.
    - **Änderung der Systemzeit**: hindert Benutzer daran, die Systemzeit auf dem Gerät zu ändern.
    - **Änderung von Regionseinstellungen (nur Desktop):** hindert Benutzer daran, die Regionseinstellungen auf dem Gerät zu ändern.
    - **Änderung der Spracheinstellungen (nur Desktop):** hindert Benutzer daran, die Spracheinstellungen auf dem Gerät zu ändern
  - **Gaming:** blockiert den Zugriff auf die Gaming-App in den Einstellungen.
  - **Ease of Access** (Erleichterte Bedienung): blockiert den Zugriff auf den Bereich „Ease of Access“ (Erleichterte Bedienung) der App „Einstellungen“.
  - **Datenschutz:** blockiert den Zugriff auf den Datenschutzbereich der App „Einstellungen“.
  - **Update and Security** (Update und Sicherheit): blockiert den Zugriff auf den Update- und Sicherheitsbereich der App „Einstellungen“.

## <a name="display"></a>Anzeige

- **GDI-Skalierung für Apps aktivieren**
- **GDI-Skalierung für Apps deaktivieren**

  Mit der GDI-DPI-Skalierung können Apps, die nicht mit DPI-Werten kompatibel sind, mit monitorspezifischen DPI-Werten kompatibel sein. Geben Sie die Legacy-Apps an, bei denen die GDI-DPI-Skalierung aktiviert ist. Wenn die GDI-DPI-Skalierung so konfiguriert ist, dass sie sowohl ein- als auch ausgeschaltet wird, wird die Skalierung für die App deaktiviert.

## <a name="general"></a>Allgemein

- **Screen capture (mobile only)** (Bildschirmaufnahme (nur Mobilgeräte)): ermöglicht dem Benutzer, eine Bildschirmaufnahme des Geräts zu erstellen.
- **Copy and paste (mobile only)** (Kopieren und Einfügen (nur Mobilgeräte)): Erlaubt Kopier- und Einfügevorgänge zwischen Apps auf dem Gerät.
- **Manuelles Aufheben der Registrierung**: Ermöglicht dem Benutzer das manuelle Löschen des Unternehmensbereichskontos vom Gerät.
  - Diese Richtlinieneinstellung wird nicht angewendet, wenn der Computer mit Azure Active Directory (Azure AD) verknüpft ist und die automatische Registrierung aktiviert ist. 
  - Diese Richtlinieneinstellung gilt nicht für Computer mit Windows 10 Home.
- **Manual root certificate installation (mobile only)** (Manuelle Installation von Stammzertifikaten (nur Mobilgeräte)): hindert den Benutzer daran, Stammzertifikate und CAP-Zwischenzertifikate manuell zu installieren.

- **Kamera:** erlaubt oder sperrt die Verwendung der Kamera auf dem Gerät.
- **OneDrive-Dateisynchronisierung:** hindert das Gerät daran, Dateien mit OneDrive zu synchronisieren.
- **Wechselmedien:** gibt an, ob externe Speichergeräte wie SD-Karten mit dem Gerät verwendet werden können.
- **Geolocation**: Gibt an, ob das Gerät Ortungsdienstinformationen verwenden kann.
- **Internetfreigabe:** Ermöglicht die gemeinsame Nutzung der Internetverbindung auf dem Gerät.
- **Zurücksetzung des Telefons:** steuert, ob Benutzer ihre Geräte zurücksetzen können.
- **USB-Verbindung (nur Mobilgerät):** Steuert, ob die Geräte über eine USB-Verbindung auf externe Speichergeräte zugreifen können.
- **AntiTheft-Modus (nur Mobilgerät):** Konfigurieren Sie, ob der Windows-Diebstahlschutzmodus aktiviert ist.
- **Cortana**: Aktivieren oder deaktivieren Sie den Cortana-Sprach-Assistenten.
- **Sprachaufzeichnung (nur Mobilgerät)**: erlaubt oder sperrt die Verwendung der Sprachaufzeichnung auf dem Gerät.
- **Bearbeitung des Gerätenamens:** verhindert, dass der Endbenutzer den Gerätenamen ändert (nur Windows 10 Mobile).
- **Bereitstellungspakete hinzufügen:** blockiert den Laufzeitkonfigurations-Agent, der Bereitstellungspakete installiert.
- **Bereitstellungspakete entfernen:** blockiert den Laufzeitkonfigurations-Agent, der die Bereitstellungspakete entfernt.
- **Geräteerkennung:** verhindert, dass ein Gerät von anderen Geräten erkannt wird.
- **Programmumschaltung (nur mobile Geräte):** blockiert die Programmumschaltung auf dem Gerät.
- **Dialogfeld bei SIM-Kartenfehler (nur mobile Geräte):** blockiert die Anzeige einer Fehlermeldung auf dem Gerät, wenn keine SIM-Karte erkannt wird.
- **Ink-Arbeitsbereich:** blockiert den Benutzerzugriff auf den Ink-Arbeitsbereich. **Nicht konfiguriert** aktiviert den Ink-Arbeitsbereich, und der Benutzer kann ihn über den Sperrbildschirm verwenden.
- **Automatische erneute Bereitstellung:** Mit dieser Einstellung können Benutzer mit Administratorrechten alle Benutzerdaten und -einstellungen über **STRG+WINDOWS+R** vom Sperrbildschirm des Geräts aus löschen. Das Gerät wird automatisch neu konfiguriert und bei der Verwaltung neu registriert.
- **Require users to connect to network during device setup (Windows Insider only)** (Benutzer müssen während der Geräteeinrichtung eine Netzwerkverbindung herstellen (nur für Windows-Insider)): Klicken Sie auf **Anfordern**, damit das Gerät eine Verbindung mit einem Netzwerk herstellen muss, bevor es während der Einrichtung von Windows 10 mit dem Prozess nach der Seite „Netzwerk“ fortfährt. Solange sich diese Funktion in der Vorschau befindet, ist für die Verwendung dieser Einstellung der Windows-Insider-Build 1809 oder höher erforderlich.
- **End processes from Task Manager** (Prozesse über den Task-Manager beenden): Diese Einstellung bestimmt, ob der Task-Manager von anderen Benutzern als Administratoren zum Beenden von Tasks verwendet werden darf. Die Option **Blockieren** verhindert, dass Standardbenutzer (also keine Administratoren) den Task-Manager zum Beenden von Prozessen oder Tasks auf dem Gerät verwenden. Über die Option **Nicht konfiguriert** (Standard) erhalten Standardbenutzer die Erlaubnis, Prozesse oder Tasks mithilfe des Task-Managers zu beenden.

## <a name="kiosk-preview---obsolete"></a>Kiosk (Vorschauversion) (Veraltet)

Diese Einstellungen sind schreibgeschützt und können nicht verändert werden. Informationen zum Konfigurieren des Kioskmodus finden Sie unter [Kiosk settings in Windows 10 and later (Kioskeinstellungen für Windows 10 und höher)](kiosk-settings.md).

Ein Kiosk-Gerät führt in der Regel eine App oder eine bestimmte Gruppe von Apps aus. Benutzer werden daran gehindert, auf Features oder Funktionen auf dem Gerät zuzugreifen.

- **Kioskmodus:** Gibt den Typ des Kioskmodus an, der von der Richtlinie unterstützt wird. Zu den Optionen gehören:

  - **Nicht konfiguriert** (Standardeinstellung): Die Richtlinie aktiviert den Kioskmodus auf dem Gerät nicht.
  - **Kiosk mit einzelner App:** Das Profil erlaubt dem Gerät die Ausführung von nur einer App. Wenn sich der Benutzer anmeldet, wird eine bestimmte App gestartet. Dieser Modus hindert den Benutzer auch daran, neue Apps zu öffnen oder die App zu ändern, die ausgeführt wird.
  - **Kiosk mit mehreren Apps:** Das Profil erlaubt dem Gerät, mehrere Apps auszuführen. Es sind nur die Apps, die Sie hinzufügen, für den Benutzer verfügbar. Der Vorteil eines Kiosks mit mehreren Apps oder eines Geräts mit festem Zweck ist eine leicht verständliche Benutzererfahrung für einzelne Personen, da sie nur auf die Apps zugreifen, die sie benötigen, und die Apps entfernen, die sie nicht benötigen.

#### <a name="single-app-kiosks"></a>Kiosks für einzelne Apps

Legen Sie folgende Einstellungen fest:

- **Benutzerkonto**: Geben Sie das (auf das Gerät bezogene) lokale Benutzerkonto, AD-Domänenkonto oder Azure AD-Konto ein, das der Kiosk-App zugeordnet ist.
  - Lokales Konto: Geben Sie dieses als `devicename\accountname`, `.\accountname` oder `accountname` ein.
  - Domänenkonto: Geben Sie dieses als `domain\accountname` ein.
  - Azure AD-Konto: Geben Sie dieses als `AzureAD\emailaddress` ein. Stellen Sie sicher, dass Sie „AzureAD“ eingeben, da es sich dabei um einen festen Domänennamen handelt. Geben Sie anschließend die Azure AD-E-Mail-Adresse ein. Geben Sie beispielsweise `AzureAD\user@contoso.onmicrosoft.com` ein.

    Für Kiosks in öffentlichen Umgebungen, für die die automatische Anmeldung aktiviert ist, muss ein Benutzertyp mit den geringsten Berechtigungen (z.B. das lokale Standardbenutzerkonto) verwendet werden. Wenn Sie ein Azure AD-Konto für den Kioskmodus verwenden, geben Sie `AzureAD\user@yourorganization.com` ein.

- **Anwendungsbenutzermodell-ID (AUMID) der App**: Geben Sie die AUMID der Kiosk-App ein. Weitere Informationen finden Sie unter [Find the Application User Model ID of an installed app (Ermitteln der Anwendungsbenutzer-ID einer installierten App)](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

#### <a name="multi-app-kiosks"></a>Kiosks für mehrere Apps

[Kiosks für mehrere Apps](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune) verwenden eine Kioskkonfiguration, mit der die zugelassenen Apps aufgelistet werden, sowie andere Einstellungen. 

Verwenden Sie die Schaltfläche **Hinzufügen**, um eine Kioskkonfiguration zu erstellen oder eine vorhandene auszuwählen. Legen Sie folgende Einstellungen fest:

- **Kioskkonfigurationsname:** Geben Sie einen Anzeigenamen an, der zur Identifikation einer bestimmten Konfiguration dient.

- **Kiosk-Apps:** Geben Sie die Apps ein, die im Startmenü verfügbar sein sollen. Die von Ihnen hinzugefügten Apps sind die einzigen Apps, die der Benutzer öffnen kann.

  - **App-Typ:** Wählen Sie den Typ der Kiosk-App aus:
    - **Win32-App:** Eine herkömmliche Desktop-App. Sie benötigen den vollqualifizierten Pfadnamen der ausführbaren Datei bezogen auf das Gerät.
    - **UWP-App:** eine Universelle Windows-App. Sie benötigen die [AUMID für die App](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

  - **Bezeichner:** Geben Sie entweder den Namen des vollqualifizierten Pfads für die ausführbare Datei (Win32-Apps) oder die [App-Benutzermodell-ID](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (UWP-Apps) ein.

- **Taskleiste:** Wählen Sie aus, ob Sie die Taskleiste **Aktivieren** (anzeigen) oder sie im Kioskmodus **Nicht konfiguriert** (ausgeblendet) lassen möchten.

- **Startmenülayout:** Geben Sie eine XML-Datei an, die beschreibt, wie die Apps im Startmenü dargestellt werden. [Anpassen und Exportieren des Startlayouts](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout): bietet Anweisungen und XML-Beispiele.

  [Erstellen eines Windows 10-Kiosks, in dem Apps ausgeführt werden](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file): Bietet weitere Details zur Verwendung und Erstellung von XML-Dateien.

- **Zugewiesene Benutzer:** Fügen Sie mindestens ein Benutzerkonto hinzu, das die von Ihnen hinzugefügten Apps verwenden kann. Wenn sich ein Benutzer mit einem Konto anmeldet, sind nur die in der Konfiguration definierten Apps verfügbar. Das Konto kann für das Gerät lokal oder ein Azure AD-Konto sein, das der Kiosk-App zugeordnet ist.

    Für Kiosks in öffentlichen Umgebungen, für die die automatische Anmeldung aktiviert ist, muss ein Benutzertyp mit den geringsten Berechtigungen (z.B. das lokale Standardbenutzerkonto) verwendet werden. Verwenden Sie das `domain\user@tenant.com`-Format, um ein Azure Active Directory-Konto (AD) für den Kioskmodus zu konfigurieren.

## <a name="locked-screen-experience"></a>Gesperrter Bildschirm

- **Benachrichtigungen des Info-Centers (nur Mobilgerät):** lässt Info-Center-Benachrichtigungen auf dem Gerätesperrbildschirm anzeigen (nur Windows 10 Mobile).
- **URL zu Bild für gesperrten Bildschirm (nur Desktop):** Geben Sie die URL zu einem Bild im JPEG-Format ein, das als Hintergrund für den Windows-Sperrbildschirm verwendet wird. Benutzer können diese Einstellung nicht ändern.
- **Vom Benutzer konfigurierbares Bildschirmtimeout (nur Mobilgeräte):** lässt Benutzer die Zeitspanne konfigurieren. 
- **Cortana on locked screen (desktop only)** (Cortana auf Sperrbildschirm (nur Desktopgeräte)): lässt nicht zu, dass der Benutzer mit Cortana interagiert, wenn auf dem Gerät der Sperrbildschirm zu sehen ist (nur Windows 10 Desktop).
- **Toast notifications on locked screen** (Popupbenachrichtigungen auf Sperrbildschirm): verhindert, dass Warnmeldungen auf dem Gerätesperrbildschirm angezeigt werden.
- **Bildschirmtimeout (nur Mobilgeräte):** gibt die Zeit in Sekunden an, nach der der Sperrbildschirm ausgeschaltet wird.

## <a name="messaging"></a>Messaging

- **Nachrichtensynchronisierung (nur mobil):** deaktiviert das Feature „Nachrichten – Überall“ sowie die SMS-Sicherung und -Wiederherstellung.
- **MMS (nur mobil):** deaktiviert die Funktion zum Senden/Empfangen von MMS auf dem Gerät.
- **RCS (nur mobil)**: deaktiviert die Funktion für RCS-Sendevorgänge/Empfangsvorgänge (Rich Communication Services) auf dem Gerät.

## <a name="microsoft-edge-browser"></a>Microsoft Edge-Browser

### <a name="start-experience"></a>Startoberfläche

- **Start Microsoft Edge with** (Microsoft Edge starten mit): Wählen Sie aus, welche Seiten beim Starten von Microsoft Edge geöffnet werden. Folgende Optionen sind verfügbar:
  - **Startseiten:** Microsoft Edge beginnt mit der vom Betriebssystem definierten Standardstartseite.
  - **Neue Registerkartenseite:** Microsoft Edge lädt, was in der Einstellung **URL für neue Registerkartenseite** definiert ist.
  - **Seite der letzten Sitzung:** Microsoft Edge lädt die Seite der letzten Sitzung. 
  - **Custom start page** (Benutzerdefinierte Startseite): Microsoft Edge lädt die vom IT-Administrator definierte Startseite.
- **User can change Start pages** (Der Benutzer kann Startseiten ändern): Wenn die Option **Zulassen** ausgewählt ist, können Benutzer die Startseiten ändern. Administratoren können mithilfe der `EdgeHomepageUrls` die Startseiten eingeben, die Benutzern standardmäßig beim Öffnen von Microsoft Edge angezeigt werden. **Nicht konfiguriert** hindert Benutzer daran, Änderungen an den Startseiten vorzunehmen.
- **URL für neue Registerkartenseite:** Geben Sie die URL an, die auf der neuen Registerkartenseite geöffnet werden soll. Geben Sie beispielsweise `https://www.bing.com` ein.
- **Open web content on New Tab page** (Webinhalt auf der neuen Registerkartenseite öffnen): Wählen Sie die Option **Blockieren** aus, um zu verhindern, dass Microsoft Edge eine Website auf einer neuen Registerkarte öffnet. Wenn blockiert, wird eine neue Registerkarte leer geöffnet. **Nicht konfiguriert** verwendet das Standardverhalten des Betriebssystems auf dem Gerät, das Benutzern möglicherweise gestattet, auszuwählen, was angezeigt wird.
- **Startschaltfläche:** Wählen Sie aus, was geschieht, wenn die Startschaltfläche ausgewählt wird. Folgende Optionen sind verfügbar:
  - **Startseiten:** Die Option, die Sie für die Einstellung **Start Microsoft Edge with** (Microsoft Edge starten mit) ausgewählt haben, wird geöffnet.
  - **Neue Registerkartenseite:** Die Option, die Sie für die Einstellung **URL für neue Registerkartenseite** ausgewählt haben, wird geöffnet.
  - **Benutzerdefinierte URL der Startschaltfläche:** Die Option, die Sie für die Einstellung **URL der Startschaltfläche** ausgewählt haben, wird geöffnet.
  - **Startschaltfläche ausblenden:** blendet die Startschaltfläche aus.
- **User can change Home button** (Benutzer kann Startschaltfläche ändern): Wenn die Option **Zulassen** ausgewählt ist, können Benutzer die Startschaltfläche ändern. Die Änderungen des Benutzers setzen Administratoreinstellungen für die Startschaltfläche außer Kraft. **Nicht konfiguriert** verwendet das Standardverhalten des Betriebssystems auf dem Gerät, das Benutzern möglicherweise das Ändern der Administratorkonfiguration der Startschaltfläche nicht erlaubt.
- **Willkommensseite anzeigen:** Die Option **Blockieren** verhindert, dass die Einführungsseite bei der ersten Ausführung von Microsoft Edge angezeigt wird. Diese Funktion ermöglicht Unternehmen, die z.B. in Nullemissionskonfigurationen registriert sind, diese Seite zu blockieren. **Nicht konfiguriert** zeigt die Einführungsseite an.
  - **URL für Willkommensseite:** Geben Sie die URL der Seite an, die angezeigt wird, wenn der Benutzer Microsoft Edge zum ersten Mal ausführt (nur Windows 10 Mobile).
- **Popups**: Wählen Sie **Blockieren** aus, um das Anzeigen von Popupfenstern im Browser zu beenden. Gilt nur für Windows 10 Desktop. **Nicht konfiguriert** lässt Popups im Webbrowser zu.
- **Send intranet traffic to Internet Explorer** (Intranetdatenverkehr an Internet Explorer senden): Die Option **Zulassen** erlaubt Benutzern, Websites im Intranet im Internet Explorer anstatt in Microsoft Edge zu öffnen (nur Windows 10 Desktop). **Nicht konfiguriert** ermöglicht Benutzern die Verwendung von Microsoft Edge.
- **Enterprise mode site list location** (Speicherort der Siteliste für den Unternehmensmodus): Geben Sie die URL ein, die eine Liste der Websites enthält, die im Unternehmensmodus geöffnet werden. Benutzer können diese Liste nicht ändern. Gilt nur für Windows 10 Desktop.
- **Message when opening sites in Internet Explorer** (Meldung beim Öffnen von Websites im Internet Explorer): Verwenden Sie diese Einstellung, um zu konfigurieren, dass Microsoft Edge eine Benachrichtigung anzeigt, bevor eine Website in Internet Explorer 11 geöffnet wird. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert:** Das Standardverhalten des Betriebssystems wird verwendet, d. h. möglicherweise wird keine Meldung angezeigt.
  - **Show message without option to open sites in Microsoft Edge** (Meldung ohne Option zum Öffnen von Websites in Microsoft Edge anzeigen): zeigt die Meldung beim Öffnen von Websites im Internet Explorer an. Websites werden im Internet Explorer geöffnet. Es gibt keine Option, Websites in Microsoft Edge zu öffnen.
  - **Show message when opening sites in Microsoft Edge** (Meldung beim Öffnen von Websites in Microsoft Edge anzeigen): zeigt die Meldung beim Öffnen von Websites im Internet Explorer an. Die Meldung enthält einen Link **Weiter in Microsoft Edge**, damit Benutzer Microsoft Edge anstelle von Internet Explorer auswählen können.

  > [!IMPORTANT]
  > Für diese Einstellung müssen Sie die Einstellung **Unternehmensmodus-Websiteliste** konfigurieren, die Einstellung **Alle Intranet-Websites an Internet Explorer 11 senden** oder beide Einstellungen aktivieren.

- **Microsoft-Kompatibilitätsliste:** Die Option **Blockieren** verhindert die Verwendung der Microsoft-Kompatibilitätsliste in Microsoft Edge. Mithilfe dieser Liste von Microsoft kann Microsoft Edge Websites mit bekannten Kompatibilitätsproblemen ordnungsgemäß anzeigen. **Nicht konfiguriert** ermöglicht die Verwendung einer Microsoft-Kompatibilitätsliste.
- **Preload Start pages and New Tab page** (Startseiten und neue Registerkartenseite vorab laden): Wählen Sie die Option **Blockieren** aus, um zu verhindern, dass Microsoft Edge Startseiten und die neue Registerkartenseite vorab lädt. Das Vorabladen minimiert die Zeit zum Starten von Microsoft Edge und Laden einer neuen Registerkarte. **Nicht konfiguriert** verwendet das Standardverhalten des Betriebssystems, d.h. die Seiten werden möglicherweise vorab geladen.
- **Prelaunch Start pages and New Tab page** (Startseiten und neue Registerkartenseite vorab starten): Wählen Sie die Option **Blockieren** aus, um zu verhindern, dass Microsoft Edge Startseiten und die neue Registerkartenseite vorab startet. Vorabstarten steigert die Leistung von Microsoft Edge und minimiert die zum Starten von Microsoft Edge erforderliche Zeit. **Nicht konfiguriert** verwendet das Standardverhalten des Betriebssystems, d.h. die Seiten werden möglicherweise vorab gestartet.

### <a name="favorites-and-search"></a>Favoriten und Suche

- **Favoritenleiste:** Wählen Sie aus, was mit der Favoritenleiste auf einer beliebigen Seite von Microsoft Edge geschehen soll. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert:** verwendet das Standardverhalten des Betriebssystems, d. h. die Favoritenleiste wird möglicherweise auf allen Seiten ausgeblendet. Der Benutzer kann diese Einstellung ändern.
  - **Ausblenden:** blendet die Favoritenleiste auf allen Seiten aus. Der Benutzer kann diese Einstellung nicht ändern.
  - **Anzeigen:** zeigt die Favoritenleiste auf allen Seiten an. Der Benutzer kann diese Einstellung nicht ändern.
- **Favoritenliste:** Fügt eine Liste von URLs zur Favoritendatei hinzu. Fügen Sie z.B. `http://contoso.com/favorites.html` hinzu.
- **Restrict changes to Favorites** (Änderungen an Favoriten einschränken): Wählen Sie die Option **Blockieren** aus, um zu verhindern, dass Benutzer die Favoritenliste hinzufügen, importieren, sortieren oder bearbeiten. **Nicht konfiguriert** verwendet den Betriebssystemstandard, sodass Benutzer die Liste möglicherweise ändern können.
- **Sync favorites between Microsoft browsers (desktop only)** (Das Synchronisieren von Favoriten zwischen Microsoft-Browsern zulassen (nur Desktopgeräte)): Die Option **Anfordern** erzwingt, dass Windows die Favoriten zwischen Internet Explorer und Microsoft Edge synchronisiert. Favoriten betreffende Hinzufügungen, Löschungen, Änderungen und Anordnungsänderungen werden zwischen Browsern freigegeben.  **Nicht konfiguriert** verwendet den Betriebssystemstandard, sodass Benutzer möglicherweise die Synchronisierung von Favoriten zwischen den Browsern auswählen können.
- **Default search engine** (Standardsuchmaschine): Wählen Sie die Standardsuchmaschine für das Gerät aus. Endbenutzer können diesen Wert jederzeit ändern. Folgende Optionen sind verfügbar:
  - Standard
  - Bing
  - Google
  - Yahoo
  - Benutzerdefinierter Wert
- **Suchvorschläge**: Die Option **Nicht konfiguriert** ermöglicht der Suchmaschine, Websites während der Eingabe von Suchausdrücken in der Adressleiste vorzuschlagen. **Blockieren** verhindert die Verwendung dieser Funktion.

### <a name="privacy-and-security"></a>Datenschutz und Sicherheit

- **InPrivate-Browsen:** Die Option **Blockieren** hindert den Endbenutzer daran, InPrivate-Browsersitzungen zu öffnen. **Nicht konfiguriert** lässt diese Funktion zu.
- **Browserverlauf speichern:** Die Option **Blockieren** verhindert, dass Microsoft Edge den Browserverlauf speichert. **Nicht konfiguriert** ermöglicht das Speichern des Browserverlaufs.
- **Clear browsing data on exit (Desktop only)** (Browserdaten beim Beenden löschen (Nur Desktopgeräte)): Die Option **Anfordern** löscht den Verlauf sowie die Browserdaten, wenn der Benutzer Microsoft Edge beendet. **Nicht konfiguriert** verwendet den Betriebssystemstandard, d.h. die Suchdaten werden möglicherweise zwischengespeichert.
- **Sync browser settings between user's devices** (Browsereinstellungen zwischen Benutzergeräten synchronisieren): Legen Sie fest, wie die Browsereinstellungen zwischen den Geräten synchronisiert werden sollen. Folgende Optionen sind verfügbar:
  - **Zulassen:** Lässt die Synchronisierung von Microsoft Edge-Browsereinstellungen zwischen Benutzergeräten zu.
  - **Block and enable user override** (Außerkraftsetzung durch Benutzer blockieren und aktivieren): blockiert die Synchronisierung von Microsoft Edge-Browsereinstellungen zwischen Benutzergeräten. Benutzer können diese Einstellung überschreiben.
  - **Blockieren:** Blockiert die Synchronisierung von Microsoft Edge-Browsereinstellungen zwischen Benutzergeräten. Benutzer können diese Einstellung nicht überschreiben.
- **Kennwort-Manager**: Die Option **Blockieren** deaktiviert den Kennwort-Manager von Microsoft Edge. **Nicht konfiguriert** lässt diese Funktion zu.
- **Cookies**: Wählen Sie aus, wie Cookies im Webbrowser verarbeitet werden sollen. Folgende Optionen sind verfügbar:
  - **Zulassen:** ermöglicht das Speichern von Cookies auf dem Gerät.
  - **Block all cookies** (Alle Cookies blockieren): Cookies werden nicht auf dem Gerät gespeichert.
  - **Nur Cookies von Drittanbietern blockieren:** Cookies von Drittanbietern oder Partnern werden nicht auf dem Gerät gespeichert.
- **AutoAusfüllen:** Die Option **Blockieren** deaktiviert das Feature „AutoAusfüllen“ auf dem Gerät. **Nicht konfiguriert** erlaubt Benutzern, die Einstellungen für AutoAusfüllen im Browser zu ändern (nur Windows 10 Desktop).
- **DNT-Kopfzeilen senden**: Die Option **Nicht konfiguriert** setzt voraus, dass Geräte DNT-Kopfzeilen an Websites senden, die Nachverfolgungsinformationen anfordern (empfohlen). Wählen Sie **Blockieren** aus, um zu verhindern, dass das Gerät diese Kopfzeilen sendet, die Websites ermöglichen, den Benutzer nachzuverfolgen.
- **WebRTC-LocalHost-IP-Adresse:** Die Option **Blockieren** verhindert die Anzeige der LocalHost-IP-Adressen von Benutzern bei Telefonaten mit dem WebRTC-Protokoll. **Nicht konfiguriert** ermöglicht die Anzeige der Localhost-IP-Adressen von Benutzern bei Telefonaten mit diesem Protokoll.
- **Datenerfassung für Livekacheln:** Wählen Sie die Option **Blockieren** aus, um das Sammeln von Daten durch Windows aus den Livekacheln zu beenden, wenn eine Seite an das Startmenü von Microsoft Edge angeheftet ist. **Nicht konfiguriert** erlaubt das Sammeln dieser Informationen.
- **User can override certificate errors** (Benutzer kann Zertifikatfehler außer Kraft setzen): Die Option **Blockieren** verhindert, dass Benutzer auf Websites mit SSL- oder TLS-Fehlern zugreifen. **Nicht konfiguriert** ermöglicht Benutzern den Zugriff auf diese Websites.

### <a name="additional"></a>Zusätzliche Informationen

- **Microsoft Edge-Browser (nur mobil):** Wählen Sie die Option **Blockieren** aus, um die Verwendung von Microsoft Edge auf dem Gerät zu verhindern. Wenn Sie Microsoft Edge blockieren, gelten die individuellen Einstellungen nur für den Desktop. **Nicht konfiguriert** ermöglicht die Verwendung des Microsoft Edge-Webbrowsers auf dem Gerät.
- **Adressleisten-Dropdown (nur Desktop):** Die Option **Blockieren** verhindert, dass Microsoft Edge bei der Eingabe weiterhin eine Liste mit Vorschlägen in einer Dropdownliste anzeigt. Mit dieser Option kann die zwischen Microsoft Edge und Microsoft-Diensten genutzte Netzwerkbandbreite minimiert werden. **Nicht konfiguriert** ermöglicht Microsoft Edge, eine Liste mit Vorschlägen anzuzeigen.
- **Vollbild:** Wählen Sie die Option **Blockieren** aus, damit Microsoft Edge nicht nur den Webinhalt anzeigt und Microsoft Edge (Vollbildmodus) ausgeblendet wird. **Nicht konfiguriert** verwendet den Betriebssystemstandard, d.h. Microsoft Edge kann den Vollbildmodus verwenden.
- **Informationen zu Flags:** Die Option **Blockieren** verhindert, dass Endbenutzer auf die `about:flags`-Seite in Microsoft Edge zugreifen, die die Entwicklereinstellungen und experimentellen Einstellungen enthält. **Nicht konfiguriert** verwendet den Betriebssystemstandard, sodass Benutzer auf die `about:flags`-Seite zugreifen können.
- **Entwicklertools:** Die Option **Blockieren** hindert den Endbenutzer daran, die Microsoft Edge-Entwicklertools aufzurufen. **Nicht konfiguriert** ermöglicht Benutzern, die Entwicklertools zu öffnen.
- **Erweiterungen:** Die Option **Nicht konfiguriert** lässt zu, dass der Benutzer Microsoft Edge-Erweiterungen auf dem Gerät installiert. **Blockieren** verhindert die Installation.
- **Querladen von Entwicklererweiterungen:** Die Option **Blockieren** verhindert das Querladen durch Microsoft Edge, wodurch nicht überprüfte Erweiterungen mit dem Feature **Load extensions** (Erweiterungen laden) installiert und ausgeführt werden. **Nicht konfiguriert** verwendet den Betriebssystemstandard, der das Querladen möglicherweise erlaubt.
- **Erforderliche Erweiterungen:** Wählen Sie aus, welche Erweiterungen in Microsoft Edge nicht von Endbenutzern deaktiviert werden können. Geben Sie die Paketfamiliennamen ein, und wählen Sie **Hinzufügen** aus. [Paketfamiliennamen (PFN) suchen](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) listet einige hilfreiche Informationen auf.

  Sie können auch eine CSV-Datei **Importieren**, die die Paketfamiliennamen enthält.

- **JavaScript:** Wählen Sie **Blockieren** aus, um zu verhindern, dass Java-Skripts im Browser auf dem Gerät ausgeführt werden. **Nicht konfiguriert** lässt die Ausführung von Skripts wie z.B. JavaScript im Microsoft Edge-Browser zu.

## <a name="network-proxy"></a>Netzwerkproxy

- **Proxyeinstellungen automatisch erkennen:** Bei Aktivierung versucht das Gerät, den Pfad zu einem PAC-Skript zu finden.
- **Use proxy script** (Proxyskript verwenden): Verwenden Sie diese Option, um einen Pfad zu einem PAC-Skript zum Konfigurieren des Proxyservers anzugeben.
  - **Adress-URL für Setupskript:** Geben Sie die URL eines PAC-Skripts an, das Sie verwenden möchten, um den Proxyserver zu konfigurieren.
- **Use manual proxy server** (Manuellen Proxyserver verwenden): Verwenden Sie diese Option, wenn Sie Proxyserverinformationen manuell eingeben möchten.
  - **Adresse:** Geben Sie den Namen oder die IP-Adresse des Proxyservers an.
  - **Portnummer:** Geben Sie die Portnummer Ihres Proxyservers ein.
  - **Proxyausnahmen:** Geben Sie URLs an, die den Proxyserver nicht verwenden dürfen. Trennen Sie die einzelnen Elemente durch Semikola.
  - **Bypass proxy server for local address** (Proxyserver für lokale Adressen umgehen): Aktivieren Sie diese Option, wenn Sie den Proxyserver nicht für lokale Adressen in Ihrem Intranet verwenden möchten.

## <a name="password"></a>Kennwort

- **Kennwort**: Der Endbenutzer muss ein Passwort eingeben, um auf das Gerät zugreifen zu können.
  - **Erforderlicher Kennworttyp:** Gibt an, ob das Kennwort nur numerisch oder alphanumerisch sein muss.
  - **Minimale Kennwortlänge:** Gilt nur für Windows 10 Mobile.
  - **Anzahl von fehlgeschlagenen Anmeldungen, bevor das Gerät zurückgesetzt wird:** Für Windows 10-Geräte: Wenn auf dem Gerät BitLocker aktiviert ist, wird in den BitLocker-Wiederherstellungsmodus gewechselt, sobald die Anzahl der von Ihnen angegebenen Anmeldeversuche erreicht ist. Wenn BitLocker nicht für dieses Gerät aktiviert ist, wird diese Einstellung nicht angewendet. Für Windows 10 Mobile-Geräte: Das Gerät wird zurückgesetzt, sobald die Anzahl der von Ihnen angegebenen Anmeldeversuche erreicht ist.
  - **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung:** Gibt den Zeitraum an, für den sich das Gerät im Leerlauf befinden muss, bevor der Bildschirm gesperrt wird.
  - **Kennwortablauf (Tage):** Gibt die Zeitspanne an, nach der das Kennwort für das Gerät geändert werden muss.
  - **Wiederverwendung vorheriger Kennwörter verhindern:** Gibt an, wie viele zuvor verwendete Kennwörter vom Gerät gespeichert werden.
  - **Require password when device returns from idle state (Mobile only)** (Kennwort anfordern, wenn das Gerät aus Leerlaufzustand zurückkehrt (nur Mobilgeräte)): Gibt an, dass der Benutzer ein Kennwort zum Entsperren des Geräts eingeben muss (nur Windows 10 Mobile).
  - **Einfache Kennwörter:** Erlaubt die Verwendung einfacher Kennwörter wie 1111 oder 1234. Diese Einstellung ermöglicht es auch, die Verwendung von Windows-Bildcodes zu blockieren.
- **Verschlüsselung:** Ermöglicht die Verschlüsselung auf Zielgeräten.

## <a name="per-app-privacy-exceptions"></a>App-bezogene Datenschutzausnahmen

Sie können Apps hinzufügen, die ein anderes Datenschutzverhalten aufweisen als das unter „Standarddatenschutz“ definierte Verhalten.

- **Paketname:** Name der App-Paketfamilie.
- **App-Name:** Der Name der App.

### <a name="exceptions"></a>Ausnahmen

- **Kontoinformationen:** Legen Sie fest, ob diese App auf den Benutzernamen, das Bild und andere Kontaktinformationen zugreifen darf.
- **Hintergrund-Apps:** Legen Sie fest, ob diese App im Hintergrund ausgeführt werden darf.
- **Kalender:** Legen Sie fest, ob diese App auf den Kalender zugreifen darf.
- **Anrufliste:** Legen Sie fest, ob diese App auf Ihre Anrufliste zugreifen darf.
- **Kamera:** Legen Sie fest, ob diese App auf die Kamera zugreifen darf.
- **Kontakte:** Legen Sie fest, ob diese App auf Kontakte zugreifen darf.
- **E-Mail:** Legen Sie fest, ob diese App auf E-Mails zugreifen und diese versenden darf.
- **Speicherort:** Legen Sie fest, ob diese App auf Standortinformationen zugreifen darf.
- **Nachrichten:** Legen Sie fest, ob diese App SMS oder MMS-Nachrichten lesen oder senden darf.
- **Mikrofon:** Legen Sie fest, ob diese App das Mikrofon verwenden darf.
- **Bewegung:** Legen Sie fest, ob diese App auf Gerätebewegungsinformationen zugreifen darf.
- **Benachrichtigungen:** Legen Sie fest, ob diese App auf Benachrichtigungen zugreifen darf.
- **Telefon:** Legen Sie fest, ob diese App auf das Telefon zugreifen darf.
- **Funkempfang:** Einige Apps verwenden Funkempfang (z. B. Bluetooth) auf Ihrem Gerät, um Daten zu senden und zu empfangen, und müssen diesen ein- oder ausschalten. Legen Sie fest, ob diese App diese Radios steuern kann.
- **Aufgaben:** Legen Sie fest, ob diese App auf Ihre Aufgaben zugreifen darf.
- **Vertrauenswürdige Geräte:** Legen Sie diese Einstellung fest, wenn diese App vertrauenswürdige Geräte verwenden soll, d. h. bereits verbundene oder im Lieferumfang dieses Geräts enthaltene Hardware. Verwenden Sie z. B. Fernsehgeräte oder Projektoren als vertrauenswürdige Geräte.
- **Feedback and diagnostics** (Feedback und Diagnose): Legen Sie fest, ob diese App auf Diagnoseinformationen zugreifen darf.
- **Sync with devices** (Mit Geräten synchronisieren): Legen Sie fest, ob diese App automatisch Informationen mit Drahtlosgeräten teilen und synchronisieren darf, die nicht explizit an das Gerät gekoppelt sind.

## <a name="personalization"></a>Personalization

- **URL zu Desktophintergrundbild (nur Desktop):** Geben Sie die URL zu einem Bild im JPEG-Format an, das Sie als Windows-Desktophintergrund verwenden möchten. Benutzer können das Bild nicht ändern.

## <a name="printer"></a>Drucker

- **Drucker:** Liste der lokalen Drucker, die hinzugefügt wurden.
- **Standarddrucker:** legt einen Standarddrucker fest.
- **User access to add new printers** (Benutzerzugriff für das Hinzufügen neuer Drucker): Erlauben oder blockieren Sie die Verwendung lokaler Drucker.

## <a name="privacy"></a>Datenschutz

- **Eingabepersonalisierung:** verhindert die Verwendung cloudbasierter Sprachdienste für Cortana, Diktierfunktionen oder Microsoft Store-Apps. Wenn Sie diese Dienste zulassen, kann Microsoft Voice-Daten erfassen, um den Dienst zu verbessern.
- **Automatisches Akzeptieren der Zustimmungsaufforderung des Benutzers zu Kopplung und Datenschutz:** erlaubt Windows das automatische Akzeptieren der Zustimmungsaufforderung des Benutzers zu Kopplung und Datenschutz.
- **Benutzeraktivitäten veröffentlichen**: Die Option **Blockieren** verhindert geteilte Aktivitäten und die Ermittlung von kürzlich verwendeten Ressourcen in der Programmumschaltung.
- **Nur lokale Aktivitäten**: Die Option **Blockieren** verhindert geteilte Aktivitäten und Ermittlungen von kürzlich in der Programmumschaltung verwendeten Ressourcen anhand von ausschließlich lokalen Aktivitäten.

Sie können Informationen definieren, auf die alle Apps auf dem Gerät zugreifen können. Zudem können Sie mithilfe von **App-bezogenen Datenschutzausnahmen** Ausnahmen für jede App definieren.

### <a name="exceptions"></a>Ausnahmen

- **Kontoinformationen:** Legen Sie fest, ob diese App auf den Benutzernamen, das Bild und andere Kontaktinformationen zugreifen darf.
- **Hintergrund-Apps:** Legen Sie fest, ob diese App im Hintergrund ausgeführt werden darf.
- **Kalender:** Legen Sie fest, ob diese App auf den Kalender zugreifen darf.
- **Anrufliste:** Legen Sie fest, ob diese App auf Ihre Anrufliste zugreifen darf.
- **Kamera:** Legen Sie fest, ob diese App auf die Kamera zugreifen darf.
- **Kontakte:** Legen Sie fest, ob diese App auf Kontakte zugreifen darf.
- **E-Mail:** Legen Sie fest, ob diese App auf E-Mails zugreifen und diese versenden darf.
- **Speicherort:** Legen Sie fest, ob diese App auf Standortinformationen zugreifen darf.
- **Nachrichten:** Legen Sie fest, ob diese App SMS oder MMS-Nachrichten lesen oder senden darf.
- **Mikrofon:** Legen Sie fest, ob diese App das Mikrofon verwenden darf.
- **Bewegung:** Legen Sie fest, ob diese App auf Gerätebewegungsinformationen zugreifen darf.
- **Benachrichtigungen:** Legen Sie fest, ob diese App auf Benachrichtigungen zugreifen darf.
- **Telefon:** Legen Sie fest, ob diese App auf das Telefon zugreifen darf.
- **Funkempfang:** Einige Apps verwenden Funkempfang (z. B. Bluetooth) auf Ihrem Gerät, um Daten zu senden und zu empfangen, und müssen diesen ein- oder ausschalten. Legen Sie fest, ob diese App diese Radios steuern kann.
- **Aufgaben:** Legen Sie fest, ob diese App auf Ihre Aufgaben zugreifen darf.
- **Vertrauenswürdige Geräte:** Legen Sie fest, ob diese App vertrauenswürdige Geräte verwenden kann. Als vertrauenswürdige Geräte wird Hardware angesehen, mit der Sie bereits eine Verbindung hergestellt haben oder die in das Gerät integriert ist. Verwenden Sie z.B. Fernsehgeräte, Projektoren usw. als vertrauenswürdige Geräte.
- **Feedback and diagnostics** (Feedback und Diagnose): Legen Sie fest, ob diese App auf Diagnoseinformationen zugreifen kann.
- **Mit Geräten synchronisieren**: Legen Sie fest, ob diese App automatisch Informationen mit Drahtlosgeräten teilen und synchronisieren darf, die nicht explizit mit Ihrem PC, Tablet oder Telefon gekoppelt sind.

## <a name="projection"></a>Projektion

- **Benutzereingabe über Empfänger der drahtlosen Anzeige:** blockiert die Benutzereingabe über Empfänger der drahtlosen Anzeige.
- **Projection to this PC** (Projektion auf diesen PC): verhindert, dass andere Geräte den PC für die Projektion finden.
- **PIN für Kopplung erforderlich:** Erfordert eine PIN beim Herstellen der Verbindung mit einem Projektionsgerät.

## <a name="reporting-and-telemetry"></a>Berichterstellung und Telemetrie

- **Nutzungsdaten freigeben**: Wählen Sie die Ebene der Diagnosedaten aus, die gesendet werden. Folgende Optionen sind verfügbar:
  - Sicherheit
  - Basic
  - Erweitert
  - Vollständig
- **Send Microsoft Edge browsing data to Microsoft 365 Analytics** (Microsoft Edge-Browserdaten an die Microsoft 365-Analyse senden): Damit Sie dieses Feature verwenden können, müssen Sie die Einstellungen für die Option **Nutzungsdaten freigeben** auf **Erweitert** oder **Full** (Vollständig) festlegen. Dieses Feature steuert, welche Daten Microsoft Edge an Microsoft 365 Analytics für Unternehmensgeräte mit einer konfigurierten kommerziellen ID sendet. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert:** Verwendung des Betriebssystemstandards, d. h. Browserverlaufsdaten werden möglicherweise nicht gesendet.
  - **Only send intranet data** (Nur Intranetdaten senden): Ermöglicht dem Administrator, den Intranetdatenverlauf zu senden.
  - **Only send internet data** (Nur Internetdaten senden): Ermöglicht dem Administrator, den Internetdatenverlauf zu senden.
  - **Send intranet and internet data** (Intranet- und Internetdaten senden): Ermöglicht dem Administrator, den Intranet- und den Internetdatenverlauf zu senden.
- **Telemetrieproxyserver:** Geben Sie den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) oder die IP-Adresse eines Proxyservers ein, um Anforderungen zu Benutzerservicequalität und Telemetrie im verbundenen Modus über eine SSL-Verbindung (Secure Sockets Layer) weiterzuleiten. Das Format dieser Einstellung lautet *Server*:*Port*. Wenn beim benannten Proxy ein Fehler auftritt oder kein Proxy angegeben wurde, obwohl diese Richtlinie aktiviert ist, werden die Daten zu Benutzererfahrung und Telemetrie im verbundenen Modus nicht gesendet und verbleiben auf dem lokalen Gerät.

  Beispiele für das Format:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

## <a name="search"></a>Suchen

- **SafeSearch (nur Mobilgeräte):** steuert, wie Cortana nicht jugendfreie Inhalte in den Suchergebnissen filtert. Sie können **Streng** oder **Mittel** auswählen oder dem Endbenutzer ermöglichen, seine eigenen Einstellungen zu wählen.
- **Display web results in search** (Webergebnisse in der Suche anzeigen): Diese Einstellung blockiert, dass Webergebnisse für Suchvorgänge auf dem Gerät angezeigt werden, oder lässt dies zu.

## <a name="start"></a>Starten

- **Startmenülayout:** Sie können eine XML-Datei hochladen, die Ihre Anpassungen einschließlich der Reihenfolge der aufgeführten Apps etc. enthält, um das Startmenü auf Desktopgeräten anzupassen. Benutzer können das von Ihnen festgelegte Startmenülayout nicht ändern.
- **Pin websites to tiles in Start menu** (Websites an Kacheln im Startmenü anheften): Importieren Sie Bilder von Microsoft Edge, die im Windows-Startmenü von Desktopgeräten als Links angezeigt werden.
- **Unpin apps from task bar** (Apps von der Taskleiste lösen): Wählen Sie die Option **Blockieren** aus, damit der Benutzer keine Apps von der Taskleiste lösen kann.
- **Schneller Wechsel zwischen Benutzern:** Wählen Sie die Option **Blockieren** aus, um das Wechseln zwischen zwei gleichzeitig angemeldeten Benutzern ohne Abmeldung zu verhindern.
- **Most used apps** (Meistverwendete Apps): Wählen Sie die Option **Blockieren** aus, um die Anzeige der meistverwendeten Apps im Startmenü auszublenden. Damit wird auch der entsprechende Schalter in der App „Einstellungen“ deaktiviert.
- **Zuletzt hinzugefügte Apps:** Wählen Sie die Option **Blockieren** aus, um die Anzeige der zuletzt hinzugefügten Apps im Startmenü auszublenden. Damit wird auch der entsprechende Schalter in der App „Einstellungen“ deaktiviert.
- **Startbildschirmmodus:** Wählen Sie aus, wie der Startbildschirm angezeigt werden soll. Sie können **Vollbild** oder **Kein Vollbild** festlegen.
- **Recently opened items in Jump Lists** (Zuletzt geöffnete Elemente in Sprunglisten): Wählen Sie die Option **Blockieren** aus, um die Anzeige zuletzt verwendeter Sprunglisten im Startmenü auszublenden. Damit wird auch der entsprechende Schalter in der App „Einstellungen“ deaktiviert.
- **App-Liste:** Legen Sie fest, wie die App „Einstellungen“ angezeigt werden soll. Folgende Optionen sind verfügbar: 
  - Ausblenden
  - Die App „Einstellungen“ reduzieren und deaktivieren 
  - Die App „Einstellungen“ entfernen und deaktivieren
- **Netzschaltersymbol:** Wählen Sie die Option **Blockieren** aus, um das Netzschaltersymbol im Startmenü auszublenden.
- **Benutzerkachel:** Wählen Sie die Option **Blockieren** aus, um die Benutzerkachel im Startmenü auszublenden.
  - **Sperren:** Wählen Sie die Option **Blockieren** aus, um die Option `Lock` in der Benutzerkachel im Startmenü auszublenden.
  - **Abmelden:** Wählen Sie die Option **Blockieren** aus, um die Option `Sign out` in der Benutzerkachel im Startmenü auszublenden.
- **Herunterfahren:** Wählen Sie die Option **Blockieren** aus, um die Optionen `Update and shut down` und `Shut down` im Netzschaltersymbol im Startmenü auszublenden.
- **Standbymodus:** Wählen Sie die Option **Blockieren** aus, um die Option `Sleep` im Netzschaltersymbol im Startmenü auszublenden.
- **Ruhezustand:** Wählen Sie die Option **Blockieren** aus, um die Option `Hibernate` im Netzschaltersymbol im Startmenü auszublenden.
- **Konto wechseln:** Wählen Sie die Option **Blockieren** aus, um die Option `Switch account` in der Benutzerkachel im Startmenü auszublenden.
- **Neustartoptionen:**  Wählen Sie die Option **Blockieren** aus, um die Optionen `Update and restart` und `Restart` im Netzschaltersymbol im Startmenü auszublenden.
- **Documents on Start** (Dokumente im Startmenü): Blendet den Ordner „Dokumente“ im Windows-Startmenü aus oder ein.
- **Downloads on Start** (Downloads im Startmenü): Blendet den Ordner „Downloads“ im Windows-Startmenü aus oder ein.
- **File Explorer on Start** (Datei-Explorer im Startmenü): Blendet die Datei-Explorer-App im Windows-Startmenü aus oder ein.
- **HomeGroup on Start** (Heimnetzgruppe im Startmenü): Blendet den Ordner „Heimnetzgruppe“ im Windows-Startmenü aus oder ein.
- **Music on Start** (Musik im Startmenü): Blendet den Ordner „Musik“ im Windows-Startmenü aus oder ein.
- **Network on Start** (Netzwerk im Startmenü): Blendet den Ordner „Netzwerk“ im Windows-Startmenü aus oder ein.
- **Personal folder on Start** (Persönlicher Ordner im Startmenü): Blendet den persönlichen Ordner im Windows-Startmenü aus oder ein.
- **Pictures on Start** (Bilder im Startmenü): Blendet den Ordner für Bilder im Windows-Startmenü aus oder ein.
- **Settings on Start** (Einstellungen im Startmenü): Blendet die App „Einstellungen“ im Windows-Startmenü aus oder ein.
- **Videos on Start** (Videos im Startmenü): Blendet den Ordner für Videos im Windows-Startmenü aus oder ein.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen für Microsoft Edge**: Hiermit wird Edge SmartScreen für den Zugriff auf Website- und Dateidownloads aktiviert.
- **Zugriff auf schädliche Websites:** Hindern Sie Benutzer daran, die Warnungen des Windows Defender SmartScreen-Filters zu ignorieren und die Website aufzurufen.
- **Download nicht überprüfter Dateien:** Hindern Sie Benutzer daran, die Warnungen des Windows Defender SmartScreen-Filters zu ignorieren und nicht überprüfte Dateien herunterzuladen.

## <a name="windows-spotlight"></a>Windows-Blickpunkt

- **Windows-Blickpunkt:** Verwenden Sie diese Einstellung, um auf Windows 10-Geräten alle Funktionen von Windows-Blickpunkt zu blockieren. Wenn Sie diese Einstellung blockieren, sind die folgenden Einstellungen nicht verfügbar:
  - **Windows Spotlight on lock screen** (Windows-Blickpunkt auf dem Sperrbildschirm): verhindert, dass Windows-Blickpunkt Informationen auf dem Sperrbildschirm des Geräts anzeigt.
  - **Third-party suggestions in Windows Spotlight** (Drittanbietervorschläge in Windows-Blickpunkt): verhindert, dass Windows-Blickpunkt Inhalte vorschlägt, die nicht von Microsoft stammen.
  - **Endbenutzerfeatures:** blockiert Endbenutzerfeatures wie Startmenüvorschläge und Mitgliedschaftsbenachrichtigungen.
  - **Windows-Tipps:** blockiert die Anzeige von Tipps als Popupbenachrichtigungen in Windows.
  - **Windows Spotlight in action center** (Windows-Blickpunkt im Info-Center): verhindert, dass Vorschläge von Windows-Blickpunkt wie neue Apps oder Sicherheitsinhalte im Windows-Info-Center angezeigt werden.
  - **Personalisierung von Windows-Blickpunkt:** verhindert, dass Windows-Blickpunkt Ergebnisse basierend auf der Nutzung eines Geräts personalisiert.
  - **Windows-Begrüßungsseite:** blockiert die Windows-Begrüßungsseite, die dem Benutzer Informationen zu neuen oder aktualisierten Features anzeigt.

## <a name="windows-defender-antivirus"></a>Windows Defender Antivirus

- **Real-time monitoring** (Echtzeitüberwachung): Ermöglicht die Echtzeitüberwachung auf Schadsoftware, Spyware und andere unerwünschte Software.
- **Verhaltensüberwachung:** Ermöglicht Defender, Geräte auf bestimmte bekannte Muster verdächtiger Aktivitäten zu überprüfen.
- **Netzwerkinspektionssystem (NIS):** Das NIS trägt zum Schutz von Geräten vor netzwerkbasierten Exploits bei. Es verwendet die Signaturen bekannter Sicherheitsrisiken aus dem Microsoft Endpoint Protection Center, um schädlichen Datenverkehr zu erkennen und zu blockieren.
- **Alle Downloads überprüfen:** Steuert, ob Defender alle aus dem Internet heruntergeladenen Dateien überprüft.
- **Scan scripts loaded in Microsoft web browsers** (In Microsoft-Webbrowsern geladene Skripts überprüfen): Ermöglicht Defender die Überprüfung von Skripts, die in Internet Explorer verwendet werden.
- **End user access to Defender** (Endbenutzerzugriff auf Defender): Steuert, ob die Benutzeroberfläche von Windows Defender für Endbenutzer ausgeblendet ist. Wenn diese Einstellung geändert wird, wird die Änderung wirksam, wenn der Endbenutzer-PC das nächste Mal neu gestartet wird.
- **Signature update interval (in hours)** (Intervall zum Aktualisieren von Signaturen (in Stunden)): Gibt das Intervall an, in dem Defender eine Überprüfung auf neue Signaturdateien durchführt.
- **Datei- und Programmaktivität überwachen:** Ermöglicht Defender die Überwachung der Datei- und Programmaktivität auf Geräten.
- **Days before deleting quarantined malware** (Tage bis zum Löschen von in Quarantäne befindlicher Schadsoftware): Ermöglicht Defender die fortgesetzte Nachverfolgung behandelter Schadsoftware für die angegebene Anzahl von Tagen, damit Sie zuvor betroffene Geräte manuell überprüfen können. Wenn Sie die Anzahl von Tagen auf **0** festlegen, bleibt Schadsoftware im Quarantäneordner und wird nicht automatisch entfernt.
- **CPU usage limit during a scan** (CPU-Auslastung während einer Überprüfung): Ermöglicht die Begrenzung des Umfangs an CPU, der bei Überprüfungen genutzt werden darf (von **1** bis **100**).
- **Archivdateien überprüfen:** Ermöglicht Defender die Überprüfung von Archivdateien wie ZIP- oder CAB-Dateien.
- **Eingehende E-Mail überprüfen:** Ermöglicht Defender das Überprüfen von E-Mail-Nachrichten beim Eingang auf dem Gerät.
- **Scan removable drives during a full scan** (Bei einer vollständigen Überprüfung Wechseldatenträger überprüfen): Ermöglicht Defender das Überprüfen von Wechseldatenträgern wie USB-Sticks.
- **Scan mapped network drives during a full scan** (Bei einer vollständigen Überprüfung zugeordnete Netzlaufwerke überprüfen): Ermöglicht Defender das Überprüfen von Dateien auf zugeordneten Netzwerklaufwerken.
  Wenn die Dateien auf dem Laufwerk schreibgeschützt sind, kann Defender gefundene Schadsoftware nicht entfernen.
- **Scan files opened from network folders** (Über Netzwerkordner geöffnete Dateien überprüfen): Ermöglicht Defender das Überprüfen von Dateien auf freigegebenen Netzlaufwerken (z. B. solche, auf die über einen UNC-Pfad zugegriffen wird). Wenn die Dateien auf dem Laufwerk schreibgeschützt sind, kann Defender gefundene Schadsoftware nicht entfernen.
- **Cloudschutz:** Lässt zu oder verhindert, dass Microsoft Active Protection Service Informationen über Schadsoftwareaktivitäten von den von Ihnen verwalteten Geräten erhält. Diese Informationen werden verwendet, um den Dienst in der Zukunft zu verbessern.
- **Prompt users before sample submission** (Vor dem Senden von Beispielen bei Benutzern nachfragen): steuert, ob potenziell schädliche Dateien, die möglicherweise genauer analysiert werden müssen, automatisch an Microsoft gesendet werden.
- **Time to perform a daily quick scan** (Uhrzeit für die Durchführung einer täglichen Schnellüberprüfung): Ermöglicht Ihnen die Planung einer Schnellüberprüfung, die täglich zum ausgewählten Zeitpunkt erfolgt.
- **Type of system scan to perform** (Art der durchzuführenden Systemüberprüfung): Geben Sie die Überprüfungsebene für eine geplante Systemüberprüfung ein.
- **Möglichweise unerwünschte Software erkennen:** ermöglicht die Auswahl einer der folgenden Schutzebenen, wenn Windows potenziell unerwünschte Software erkennt:
  - **Blockieren**
  - **Überwachung** Weitere Informationen zu potenziell unerwünschten Apps finden Sie in [Erkennen und Blockieren möglicherweise unerwünschter Anwendungen](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).
- **Actions on detected malware threats** (Aktionen für erkannte Schadsoftwarebedrohungen): Wählen Sie mit dieser Option die Maßnahmen aus, die Defender bei den einzelnen erkannten Bedrohungsstufen (Niedrig, Mittel, Hoch und Schwerwiegend) ergreifen soll. Folgende Optionen sind verfügbar:
  - **Bereinigen**
  - **Quarantäne**
  - **Entfernen**
  - **Zulassen**
  - **Benutzerdefiniert**
  - **Blockieren**

### <a name="windows-defender-antivirus-exclusions"></a>Windows Defender Antivirus-Ausschlüsse

- **Files and folders to exclude from scans and real-time protection** (Dateien und Ordner, die bei Überprüfungen und Echtzeitschutz ausgeschlossen werden sollen): Fügt Dateien und Ordner wie **C:\Pfad** oder **%ProgramFiles%\Pfad\Dateiname.exe** der Ausschlussliste hinzu. Diese Dateien und Ordner werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.
- **File extensions to exclude from scans and real-time protection** (Dateierweiterungen, die bei Überprüfungen und Echtzeitschutz ausgeschlossen werden sollen): Fügen Sie Dateierweiterungen wie **JPG** oder **TXT** der Ausschlussliste hinzu. Dateien mit diesen Erweiterungen werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.
- **Processes to exclude from scans and real-time protection** (Prozesse, die bei Überprüfungen und Echtzeitschutz ausgeschlossen werden sollen): Fügen Sie Prozesse des Typs **.exe**, **.com** oder **.scr** der Ausschlussliste hinzu. Diese Prozesse werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.

## <a name="next-steps"></a>Nächste Schritte

Weitere technische Details zu den einzelnen Einstellungen und den unterstützten Windows-Editionen finden Sie in der Referenz zum [Richtlinien-Konfigurationsdienstanbieter für Windows 10](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider).
