---
title: Intune-Einstellungen für Geräteeinschränkungen für Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Eine Liste mit allen Einstellungen und ihren Beschreibungen zum Erstellen von Geräteeinschränkungen für Windows 10 und höher wird angezeigt. Verwenden Sie diese Einstellungen in einem Konfigurationsprofil zum Steuern von Screenshots, Kennwortanforderungen, Kioskeinstellungen, Apps im Store, Microsoft Edge-Browser, Windows Defender, Cloudzugriff, Startmenü und mehr in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8957c8d8aad2eaa1741b1a625afd4b5a41a8bb51
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423695"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Einstellungen für Windows 10-Geräte (und höher) zum Zulassen oder Einschränken von Features mit Intune

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie auf Geräten mit Windows 10 und höher festlegen können. Verwenden Sie diese Einstellungen als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM), um Features zuzulassen oder zu deaktivieren, Kennwortregeln festzulegen, den Sperrbildschirm anzupassen, Windows Defender zu verwenden usw.

Diese Einstellungen werden erst einem Gerätekonfigurationsprofil in Intune hinzugefügt und dann Ihren Windows 10-Geräten zugewiesen oder für diese bereitgestellt.

> [!Note]
> Nicht alle Optionen sind in allen Windows-Editionen verfügbar. Die unterstützten Editionen finden Sie in unter [Konfigurationsdienstanbieter für Richtlinien](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (öffnet eine andere Microsoft-Website).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](device-restrictions-configure.md#create-the-profile)

## <a name="app-store"></a>App Store

- **App Store (nur mobil)**: Erlaubt oder sperrt die Verwendung des App Stores auf Windows 10 Mobile-Geräten.
- **Apps aus Store automatisch aktualisieren**: Ermöglicht die automatische Aktualisierung von Apps, die aus dem Microsoft Store installiert wurden.
- **Installation vertrauenswürdiger Apps**: Ermöglicht das Querladen von Apps, die mit einem vertrauenswürdigen Zertifikat signiert sind.
- **Entwicklersperre aufheben**: Ermöglicht dem Endbenutzer, Windows-Entwicklereinstellungen – z.B. das Zulassen quergeladener Apps – zu ändern.
- **Gemeinsam genutzte App-Benutzerdaten**: Ermöglicht Apps, die gemeinsame Nutzung von Daten durch verschiedene Benutzer auf dem gleichen Gerät zuzulassen.
- **Nur privaten Store verwenden**: Aktivieren Sie diese Option, um Endbenutzern das Herunterladen von Apps nur aus Ihrem privaten Store zu ermöglichen.
- **Store-App starten**: Hiermit werden alle Apps deaktiviert, die bereits auf dem Gerät installiert waren oder aus dem Microsoft Store heruntergeladen wurden.
- **App-Daten in Systemvolume installieren**: Hindert Apps daran, Daten auf dem Systemvolume des Geräts zu speichern.
- **Apps auf Systemlaufwerk installieren**: Hindert Apps daran, Daten auf dem Systemlaufwerk des Geräts zu speichern.
- **Game DVR (nur Desktop)**: Konfiguriert, ob Aufzeichnen und Senden von Spielen zulässig ist.
- **Nur Apps aus dem Store**: Konfiguriert, ob Benutzer Apps von anderen Orten als aus dem App-Store installieren können.

## <a name="cellular-and-connectivity"></a>Mobilfunk und Konnektivität

- **Mobilfunkdatenkanal**: Verhindert, dass Benutzer Daten verbrauchen wie z.B. beim Browsen im Web, wenn sie mit einem Mobilfunknetz verbunden sind. 
- **Datenroaming**: Erlaubt beim Zugriff auf Daten das Roaming zwischen Netzwerken.
- **VPN über Mobilfunknetz**: Steuert, ob das Gerät auf VPN-Verbindungen zugreifen kann, wenn es mit einem Mobilfunknetz verbunden ist.
- **VPN-Roaming über Mobilfunknetz**: Steuert, ob das Gerät beim Roaming in einem Mobilfunknetz auf VPN-Verbindungen zugreifen kann.
- **Bluetooth**: Steuert, ob der Benutzer Bluetooth auf dem Gerät aktivieren und konfigurieren kann.
- **Bluetooth-Erkennbarkeit**: Ermöglicht die Erkennung dieses Geräts durch andere Bluetooth-Geräte.
- **Bluetooth-Vorabkopplung**: Ermöglicht das Konfigurieren spezifischer Bluetooth-Geräte für automatisches Koppeln mit einem Hostgerät.
- **Bluetooth-Werbung**: Ermöglicht das Empfangen von Werbung per Bluetooth durch das Gerät.
- **Dienst für verbundene Geräte:** Ermöglicht die Entscheidung, dem Dienst für verbundene Geräte die Ermittlung von und Verbindung mit anderen Bluetooth-Geräten zu erlauben.
- **NFC:** Erlaubt dem Benutzer das Aktivieren und Konfigurieren von NFC-Funktionen (Near Field Communication) auf dem Gerät.
- **WLAN**: Erlaubt dem Benutzer das Aktivieren und Konfigurieren von WLAN auf dem Gerät (nur Windows 10 Mobile).
- **Automatische Verbindung mit WLAN-Hotspots herstellen**: Ermöglicht automatische Verbindungen des Geräts mit unverschlüsselten WLAN-Hotspots und das automatische Akzeptieren der Geschäftsbedingungen für die Verbindung.
- **Manuelle WLAN-Konfiguration**: Steuert, ob die Benutzer eigene WLAN-Verbindungen konfigurieren dürfen oder ob nur über WLAN-Profile konfigurierte Verbindungen verwendet werden dürfen (nur Windows 10 Mobile).
- **Intervall für WLAN-Suche:** Geben Sie ein, wie oft Geräte nach WLAN-Netzwerken suchen. Geben Sie einen Wert zwischen 1 (am häufigsten) und 500 (am seltensten) ein.
- **Zulässige Bluetooth-Dienste:** Geben Sie eine Liste zulässiger Bluetooth-Dienste und -Profile in Form von hexadezimalen Zeichenfolgen ein.

## <a name="cloud-and-storage"></a>Cloud und Speicher

- **Microsoft-Konto**: Erlaubt dem Benutzer, das Gerät einem Microsoft-Konto zuzuordnen.
- **Nicht-Microsoft-Konto**: Erlaubt dem Benutzer, dem Gerät E-Mail-Konten hinzuzufügen, die nicht mit einem Microsoft-Konto verknüpft sind.
- **Synchronisierung der Einstellungen für Microsoft-Konto**: Erlaubt das Synchronisieren der mit einem Microsoft-Konto verknüpften Geräte- und App-Einstellungen zwischen Geräten.
- **Anmeldeassistent für Microsoft-Konten**: Bei Festlegung auf **Deaktivieren** können Sie verhindern, dass Benutzer den Anmeldeassistenten für Microsoft-Konten (wlidsvc) steuern, z.B. den Dienst manuell anhalten oder starten. Wenn der wlidsvc NT-Dienst auf **Not configured** (nicht konfiguriert) festgelegt wurde, verwendet er die Standardeinstellung des Betriebssystems, wodurch Endbenutzer den Dienst starten und anhalten können. Dieser Dienst wird vom Betriebssystem genutzt, damit sich Benutzer bei ihrem Microsoft-Konto anmelden können.

## <a name="cloud-printer"></a>Clouddrucker

- **URL für Druckerermittlung**: Geben Sie die URL zum Finden von Clouddruckern ein.
- **Autoritäts-URL für Druckerzugriff**: Geben Sie die Authentifizierungsendpunkt-URL zum Abrufen von OAuth-Token ein. Geben Sie zum Beispiel `https://login.microsoftonline.com/your Azure AD Tenant ID` ein.
- **GUID für native Azure-Client-App**: Geben Sie die GUID einer Clientanwendung ein, die OAuth-Tokens von der OAuthAuthority abrufen darf.
- **Druckdienstressourcen-URI**: Geben Sie den OAuth-Ressourcen-URI für den im Azure-Portal konfigurierten Druckdienst ein. Geben Sie zum Beispiel `http://MicrosoftEnterpriseCloudPrint/CloudPrint` ein.
- **Maximal abgefragte Drucker (nur Mobilgerät)**: Geben Sie die maximale Anzahl von Druckern ein, die abgefragt werden sollen. Geben Sie beispielsweise `10` ein.
- **Ressourcen-URI für Druckerermittlungsdienst**: Geben Sie den OAuth-Ressourcen-URI für den im Azure-Portal konfigurierten Druckererkennungsdienst ein. Geben Sie zum Beispiel `http://MopriaDiscoveryService/CloudPrint` ein.

> [!TIP]
> Nachdem Sie [Windows Server Hybrid Cloud Print](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview) eingerichtet haben, können Sie diese Einstellungen konfigurieren und auf Windows-Geräten bereitstellen.

## <a name="control-panel-and-settings"></a>Systemsteuerung und Einstellungen

- **App „Einstellungen“**: Blockiert den Zugriff auf die Windows-Einstellungen-App.
  - **System**: Blockiert den Zugriff auf den Systembereich der Einstellungen-App.
    - **Änderung der Energie- und Energiesparmoduseinstellungen (nur Desktop)**: Verhindert, dass der Endbenutzer Energie- und Energiesparmoduseinstellungen auf dem Gerät ändert.
  - **Geräte**: Blockiert den Zugriff auf den Gerätebereich der Einstellungen-App.
  - **Netzwerk und Internet**: Blockiert den Zugriff auf den Netzwerk- und Internet-Bereich der Einstellungen-App.
  - **Personalisierung**: Blockiert den Zugriff auf den Personalisierungsbereich der Einstellungen-App.
  - **Konten**: Blockiert den Zugriff auf den Kontenbereich der Einstellungen-App.
  - **Zeit und Sprache**: Blockiert den Zugriff auf den Zeit- und Sprachenbereich der Einstellungen-App.
    - **Änderung der Systemzeit**: Verhindert, dass der Endbenutzer auf dem Gerät Datum und Uhrzeit ändert.
    - **Änderung von Regionseinstellungen (nur Desktop)**: Verhindert, dass der Endbenutzer Regionseinstellungen auf dem Gerät ändert.
    - **Änderung der Spracheinstellungen (nur Desktop)**: Verhindert, dass der Benutzer Spracheinstellungen auf dem Gerät ändert.
  - **Gaming**: Blockiert den Zugriff auf die Gaming-App in den Einstellungen.
  - **Erleichterte Bedienung**: Blockiert den Zugriff auf den Bereich „Erleichterte Bedienung“ der Einstellungen-App.
  - **Datenschutz**: Blockiert den Zugriff auf den Datenschutzbereich der Einstellungen-App.
  - **Update und Sicherheit**: Blockiert den Zugriff auf den Update- und Sicherheitsbereich der Einstellungen-App.

## <a name="display"></a>Anzeige

- **GDI-Skalierung für Apps aktivieren**
- **GDI-Skalierung für Apps deaktivieren**

  Mit der GDI-DPI-Skalierung können Apps, die nicht mit DPI-Werten kompatibel sind, mit monitorspezifischen DPI-Werten kompatibel sein. Geben Sie die Legacy-Apps an, bei denen die GDI-DPI-Skalierung aktiviert ist. Wenn die GDI-DPI-Skalierung so konfiguriert ist, dass sie sowohl ein- als auch ausgeschaltet wird, wird die Skalierung für die App deaktiviert.

## <a name="general"></a>Allgemein

- **Bildschirmaufnahme (nur Mobilgerät)**: Erlaubt dem Benutzer, den Bildschirm des Geräts als Bild zu erfassen.
- **Kopieren und einfügen (nur mobil)**: Erlaubt Kopier- und Einfügevorgänge zwischen Apps auf dem Gerät.
- **Manuelle Aufhebung der Registrierung**: Erlaubt dem Benutzer das manuelle Löschen des Unternehmensbereichskontos vom Gerät.
  - Diese Richtlinieneinstellung wird nicht angewendet, wenn der Computer mit Azure Active Directory (Azure AD) verknüpft ist und die automatische Registrierung aktiviert ist. 
  - Diese Richtlinieneinstellung gilt nicht für Computer mit Windows 10 Home.
- **Manuelle Installation von Stammzertifikaten (nur Mobilgerät)**: Hindert den Benutzer daran, Stammzertifikate und CAP-Zwischenzertifikate manuell zu installieren.

- **Kamera**: Erlaubt oder sperrt die Verwendung der Kamera auf dem Gerät.
- **OneDrive-Dateisynchronisierung**: Hindert das Gerät daran, Dateien mit OneDrive zu synchronisieren.
- **Wechselmedien**: Gibt an, ob externe Speichergeräte wie SD-Karten mit dem Gerät verwendet werden können.
- **Geolocation**: Gibt an, ob das Gerät Standortdienstinformationen verwenden kann.
- **Internetfreigabe**: Erlaubt die gemeinsame Nutzung der Internetverbindung auf dem Gerät.
- **Zurücksetzung des Telefons**: Steuert, ob Benutzer ihre Geräte zurücksetzen können.
- **USB-Verbindung (nur Mobilgerät)**: Steuert, ob Geräte über eine USB-Verbindung auf externe Speichergeräte zugreifen können.
- **AntiTheft-Modus (nur Mobilgerät)**: Konfigurieren Sie, ob der Windows-AntiTheft-Modus aktiviert ist.
- **Cortana**: Aktiviert oder deaktiviert den Cortana-Sprach-Assistenten.
- **Sprachaufzeichnung (nur Mobilgerät)**: Erlaubt oder sperrt die Verwendung der Sprachaufzeichnung des Geräts.
- **Bearbeitung des Gerätenamens**: Verhindert, dass der Endbenutzer den Gerätenamen ändert (nur Windows 10 Mobile).
- **Bereitstellungspakete hinzufügen**: Blockiert den Laufzeitkonfigurations-Agent, der Bereitstellungspakete installiert.
- **Bereitstellungspakete entfernen**: Blockiert den Laufzeitkonfigurations-Agent, der die Bereitstellungspakete entfernt.
- **Geräteerkennung**: Verhindert, dass ein Gerät von anderen Geräten erkannt wird.
- **Programmumschaltung (nur mobile Geräte)**: Blockiert die Programmumschaltung auf dem Gerät.
- **Dialogfeld bei SIM-Kartenfehler (nur mobile Geräte)**: Blockiert die Anzeige einer Fehlermeldung auf dem Gerät, wenn keine SIM-Karte erkannt wird.
- **Ink-Arbeitsbereich**: Blockiert den Benutzerzugriff auf den Ink-Arbeitsbereich. **Nicht konfiguriert** aktiviert den Ink-Arbeitsbereich, und der Benutzer kann ihn über den Sperrbildschirm verwenden.
- **Automatische erneute Bereitstellung**: Ermöglicht Benutzern mit Administratorrechten, alle Benutzerdaten und -einstellungen über **STRG+Windows+R** vom Sperrbildschirm des Geräts aus zu löschen. Das Gerät wird automatisch neu konfiguriert und bei der Verwaltung neu registriert.
- **Benutzer müssen während der Geräteeinrichtung eine Netzwerkverbindung herstellen**: Wählen Sie **Anfordern** aus, damit das Gerät eine Verbindung mit einem Netzwerk herstellt, bevor das Setup von Windows 10 über die Seite „Netzwerk“ hinaus fortgesetzt werden kann.

  Die Einstellung wird beim nächsten Zurücksetzen des Geräts wirksam. Wie jede andere Intune-Konfiguration muss das Gerät von Intune registriert und verwaltet werden, um Konfigurationseinstellungen zu empfangen. Sobald es jedoch registriert ist und Richtlinien empfängt, erzwingt das Zurücksetzen des Geräts die Einstellung während des nächsten Setups von Windows.

- **Direkter Speicherzugriff**: Bei Festlegung auf **Blockieren** wird der direkte Speicherzugriff (Direct Memory Access, DMA) für alle Hot-Plug-PCI-Downstreamanschlüsse verhindert, bis sich ein Benutzer bei Windows anmeldet. **Aktiviert** (Standardeinstellung) ermöglicht den Zugriff auf DMA selbst dann, wenn ein Benutzer nicht angemeldet ist.

  CSP: [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Prozesse über den Task-Manager beenden**: Diese Einstellung bestimmt, ob der Task-Manager von anderen Benutzern als Administratoren zum Beenden von Tasks verwendet werden darf. Die Option **Blockieren** verhindert, dass Standardbenutzer (also keine Administratoren) den Task-Manager zum Beenden von Prozessen oder Tasks auf dem Gerät verwenden. Über die Option **Nicht konfiguriert** (Standard) erhalten Standardbenutzer die Erlaubnis, Prozesse oder Tasks mithilfe des Task-Managers zu beenden.

## <a name="locked-screen-experience"></a>Gesperrter Bildschirm

- **Info-Center-Benachrichtigungen (nur Mobilgerät)**: Lässt Info-Center-Benachrichtigungen auf dem Gerätesperrbildschirm anzeigen (nur Windows 10 Mobile).
- **URL zu Bild für gesperrten Bildschirm (nur Desktop)**: Geben Sie die URL zu einem Bild im JPEG-Format ein, das als Hintergrund für den Windows-Sperrbildschirm verwendet wird. Durch dieses Einstellung wird das Bild gesperrt. Das Bild kann im Nachhinein nicht geändert werden.
- **Vom Benutzer konfigurierbares Bildschirmtimeout (nur Mobilgeräte)**: Ermöglicht Benutzern das Einstellen der Zeitspanne. 
- **Cortana auf Sperrbildschirm (nur Desktop)**: Lässt nicht zu, dass der Benutzer mit Cortana interagiert, wenn auf dem Gerät der Sperrbildschirm zu sehen ist (nur Windows 10 Desktop).
- **Popupbenachrichtigungen auf Sperrbildschirm**: Verhindert, dass Warnmeldungen auf dem Gerätesperrbildschirm angezeigt werden.
- **Bildschirmtimeout (nur Mobilgerät)**: Gibt die Zeit in Sekunden an, nach der der gesperrte Bildschirm ausgeschaltet wird.

## <a name="messaging"></a>Messaging

- **Nachrichtensynchronisierung (nur mobil):** Deaktivieren Sie das Feature „Nachrichten – Überall“ sowie die SMS-Sicherung und -Wiederherstellung.
- **MMS (nur mobil)**: Deaktivieren Sie die Funktion zum Senden/Empfangen von MMS auf dem Gerät.
- **RCS (nur mobil)**: Deaktivieren Sie die Funktion für RCS-Sendevorgänge/Empfangsvorgänge (Rich Communication Services) auf dem Gerät.

## <a name="microsoft-edge-browser"></a>Microsoft Edge-Browser

### <a name="use-microsoft-edge-kiosk-mode"></a>Verwenden des Microsoft Edge-Kioskmodus

Die verfügbaren Einstellungen hängen davon ab, was Sie wählen. Folgende Optionen sind verfügbar:

- **Nein** (Standard): Microsoft Edge wird nicht im Kioskmodus ausgeführt. Sie können alle Microsoft Edge-Einstellungen ändern und konfigurieren.
- **Digitale/interaktive Beschilderung (Kiosk mit einzelner App)**: Filtert Microsoft Edge-Einstellungen, die für „Digitale/interaktive Beschilderung“ in Frage kommen. Der Kioskmodus von Microsoft Edge ist nur für die Verwendung auf Windows 10-Kiosks mit einzelner App vorgesehen. Wählen Sie diese Einstellung, um eine URL im Vollbildmodus zu öffnen und nur den Inhalt dieser Website anzuzeigen. Unter [Einrichten digitaler Beschilderungen](https://docs.microsoft.com/windows/configuration/setup-digital-signage) finden weitere Informationen zu dieser Funktion.
- **Öffentliches Browsen (InPrivate, Kiosk mit einzelner App) **: Filtert Microsoft Edge-Einstellungen, die für „Öffentliches Browsen (InPrivate)“ in Frage kommen. Der Kioskmodus von Microsoft Edge ist für die Verwendung auf Windows 10-Kiosks mit einzelner App vorgesehen. Führt eine Version von Microsoft Edge mit mehreren Registerkarten aus.
- **Normalmodus (Kiosk mit mehreren Apps)**: Filtert Microsoft Edge-Einstellungen, die für den normalen Kioskmodus von Microsoft Edge gelten. Führt eine Vollversion von Microsoft Edge mit sämtlichen Funktionen für das Browsen aus.
- **Öffentliches Browsen (Kiosk mit mehreren Apps)**: Filtert Microsoft Edge-Einstellungen, die für das öffentliche Browsen auf einem Windows 10-Kiosk mit mehreren Apps gelten.  Führt eine Version von Microsoft Edge-InPrivate mit mehreren Registerkarten aus.

> [!TIP]
> Weitere Informationen zur Aufgabe dieser Optionen finden Sie unter [Konfigurationstypen für den Microsoft Edge-Kioskmodus](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

Dieses Geräteeinschränkungsprofil steht in direktem Zusammenhang mit dem Kioskprofil, das Sie mithilfe der [Windows-Kioskeinstellungen](kiosk-settings-windows.md) erstellen. Zusammenfassung:

1. Erstellen Sie das Profil [Windows-Kioskeinstellungen](kiosk-settings-windows.md), um das Gerät im Kioskmodus auszuführen. Wählen Sie Microsoft Edge als Anwendung aus, und legen Sie den Microsoft Edge-Kioskmodus im Profil „Kiosk“ fest.
2. Erstellen Sie das in diesem Artikel beschriebene Profil für Geräteeinschränkungen, und konfigurieren Sie spezifische Funktionen und Einstellungen, die in Microsoft Edge zulässig sind. Stellen Sie sicher, dass Sie den gleichen Microsoft Edge-Kioskmodustyp wie in Ihrem Kioskprofil wählen ([Windows-Kioskeinstellungen](kiosk-settings-windows.md)). 

    Unter [Unterstützte Einstellungen für den Kioskmodus ](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode) finden Sie hilfreiche Informationen.

> [!IMPORTANT] 
> Achten Sie darauf, dass dieses Microsoft Edge-Profil den gleichen Geräten wie Ihr Kioskprofil zugewiesen wird ([Windows-Kioskeinstellungen](kiosk-settings-windows.md)).

[CSP: ConfigureKioskMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>Startoberfläche

- **Microsoft Edge starten mit**: Wählen Sie aus, welche Seiten beim Starten von Microsoft Edge geöffnet werden. Folgende Optionen sind verfügbar:
  - **Startseiten**: Microsoft Edge beginnt mit der vom Betriebssystem definierten Standardstartseite
  - **Seite „Neue Registerkarte“**: Microsoft Edge lädt, was in der Einstellung **URL für neue Registerkartenseite** definiert ist.
  - **Seite der letzten Sitzung**: Microsoft Edge lädt die Seite der letzten Sitzung 
  - **Benutzerdefinierte Startseite**: Microsoft Edge lädt die vom IT-Administrator definierte Startseite
- **Benutzer kann die Startseiten ändern**: **Zulassen** ermöglicht Benutzern das Ändern der Startseiten. Administratoren können mithilfe der `EdgeHomepageUrls` die Startseiten eingeben, die Benutzern standardmäßig beim Öffnen von Microsoft Edge angezeigt werden. **Nicht konfiguriert** hindert Benutzer daran, Änderungen an den Startseiten vorzunehmen.
- **URL für neue Registerkartenseite**: Geben Sie die URL an, die auf der Seite „Neue Registerkarte“ geöffnet wird. Geben Sie beispielsweise `https://www.bing.com` ein.
- **Webinhalt für neue Registerkartenseite öffnen**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Microsoft Edge eine Website auf einer neuen Registerkarte öffnet. Wenn blockiert, wird eine neue Registerkarte leer geöffnet. **Nicht konfiguriert** verwendet das Standardverhalten des Betriebssystems auf dem Gerät, das Benutzern möglicherweise gestattet, auszuwählen, was angezeigt wird.
- **Startschaltfläche**: Wählen Sie, was geschieht, wenn die Startschaltfläche ausgewählt wird. Folgende Optionen sind verfügbar:
  - **Startseiten**: Die Option, die Sie für die Einstellung **Microsoft Edge starten mit** ausgewählt haben, wird ausgeführt.
  - **Seite „Neue Registerkarte“**: Die Option, die Sie für die Einstellung **URL für neue Registerkartenseite** ausgewählt haben, wird ausgeführt.
  - **Benutzerdefinierte URL der Startschaltfläche**: Die Option, die Sie für die Einstellung **URL der Startschaltfläche** ausgewählt haben, wird ausgeführt.
  - **Startschaltfläche ausblenden**: Blendet die Startschaltfläche aus.
- **Benutzer kann Startschaltfläche ändern**: **Zulassen** ermöglicht Benutzern das Ändern der Startschaltfläche. Die Änderungen des Benutzers setzen Administratoreinstellungen für die Startschaltfläche außer Kraft. **Nicht konfiguriert** verwendet das Standardverhalten des Betriebssystems auf dem Gerät, das Benutzern möglicherweise das Ändern der Administratorkonfiguration der Startschaltfläche nicht erlaubt.
- **Willkommensseite anzeigen**: **Blockieren** verhindert, dass die Einführungsseite bei der ersten Ausführung von Microsoft Edge angezeigt wird. Diese Funktion ermöglicht Unternehmen, also z. B. die Organisationen, die in Nullemissionskonfigurationen registriert sind, diese Seite zu blockieren. **Nicht konfiguriert** zeigt die Einführungsseite an.
  - **URL für Willkommensseite**: Geben Sie die URL der Seite an, die angezeigt wird, wenn der Benutzer Microsoft Edge zum ersten Mal ausführt (nur Windows 10 Mobile).
- **Browser nach Leerlaufzeit aktualisieren:**: Geben Sie die Anzahl der Leerlaufminuten bis zur Aktualisierung des Browsers ein (von 0-1440 Minuten). Der Standardwert ist `5` Minuten. Bei Festlegung auf `0` wird der Browser nach einem Leerlauf nicht aktualisiert.

  Diese Einstellung ist nur bei Ausführung im Modus [Öffentliches Browsen (InPrivate, Kiosk mit einzelner App)](#use-microsoft-edge-kiosk-mode) verfügbar.

  CSP: [ConfigureKioskResetAfterIdleTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskresetafteridletimeout)

- **Popups**: Wählen Sie **Blockieren** aus, um das Anzeigen von Popupfenstern im Browser zu beenden. Gilt nur für Windows 10 Desktop. **Nicht konfiguriert** lässt Popups im Webbrowser zu.
- **Datenverkehr im Intranet an Internet Explorer senden**: **Zulassen** erlaubt Benutzern, Intranetsites im Internet Explorer anstatt in Microsoft Edge zu öffnen (nur Windows 10 Desktop). **Nicht konfiguriert** ermöglicht Benutzern die Verwendung von Microsoft Edge.
- **Speicherort der Websiteliste für den Unternehmensmodus:** Geben Sie die URL ein, die eine Liste der Websites enthält, die im Unternehmensmodus geöffnet werden. Benutzer können diese Liste nicht ändern. Gilt nur für Windows 10 Desktop.
- **Meldung beim Öffnen von Websites in Internet Explorer**: Verwenden Sie diese Einstellung, um zu konfigurieren, dass Microsoft Edge eine Benachrichtigung anzeigt, bevor eine Website in Internet Explorer 11 geöffnet wird. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert**: Das Standardverhalten des Betriebssystems wird verwendet, d.h. möglicherweise wird keine Meldung angezeigt.
  - **Meldung ohne Option zum Öffnen von Websites in Microsoft Edge anzeigen**: Beim Öffnen von Websites in Internet Explorer wird die Meldung angezeigt. Websites werden im Internet Explorer geöffnet. Es gibt keine Option, Websites in Microsoft Edge zu öffnen.
  - **Meldung beim Öffnen von Websites in Microsoft Edge anzeigen**: Beim Öffnen von Websites im Internet Explorer wird die Meldung angezeigt. Die Meldung enthält einen Link **Weiter in Microsoft Edge**, damit Benutzer Microsoft Edge anstelle von Internet Explorer auswählen können.

  > [!IMPORTANT]
  > Für diese Einstellung müssen Sie die Einstellung **Unternehmensmodus-Websiteliste** konfigurieren, die Einstellung **Alle Intranet-Websites an Internet Explorer 11 senden** oder beide Einstellungen aktivieren.

- **Microsoft-Kompatibilitätsliste**: **Blockieren** verhindert die Microsoft-Kompatibilitätsliste in Microsoft Edge. Mithilfe dieser Liste von Microsoft kann Microsoft Edge Websites mit bekannten Kompatibilitätsproblemen ordnungsgemäß anzeigen. **Nicht konfiguriert** ermöglicht die Verwendung einer Microsoft-Kompatibilitätsliste.
- **Startseiten und Seite „Neue Registerkarte“ vorab laden**: Wählen Sie **Blockieren**, um zu verhindern, dass Microsoft Edge Startseiten und Seite „Neue Registerkarte“ vorab lädt. Das Vorabladen minimiert die Zeit zum Starten von Microsoft Edge und Laden einer neuen Registerkarte. **Nicht konfiguriert** verwendet das Standardverhalten des Betriebssystems, d.h. die Seiten werden möglicherweise vorab geladen.
- **Startseiten und Seite „Neue Registerkarte“ vorab starten**: Wählen Sie **Blockieren**, um zu verhindern, dass Microsoft Edge Startseiten und Seite „Neue Registerkarte“ vorab startet. Vorabstarten steigert die Leistung von Microsoft Edge und minimiert die zum Starten von Microsoft Edge erforderliche Zeit. **Nicht konfiguriert** verwendet das Standardverhalten des Betriebssystems, d.h. die Seiten werden möglicherweise vorab gestartet.

### <a name="favorites-and-search"></a>Favoriten und Suche

- **Favoritenleiste**: Wählen Sie, was mit der Favoritenleiste auf einer beliebigen Seite von Microsoft Edge geschehen soll. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert**: Verwendet das Standardverhalten des Betriebssystems, d.h. die Favoritenleiste wird möglicherweise auf allen Seiten ausgeblendet. Der Benutzer kann diese Einstellung ändern.
  - **Ausblenden**: Blendet die Favoritenleiste auf allen Seiten aus. Der Benutzer kann diese Einstellung nicht ändern.
  - **Anzeigen**: Zeigt die Favoritenleiste auf allen Seiten an. Der Benutzer kann diese Einstellung nicht ändern.
- **Favoritenliste**: Fügt eine Liste von URLs der Favoritendatei hinzu. Fügen Sie z.B. `http://contoso.com/favorites.html` hinzu.
- **Änderungen an Favoriten einschränken**: Legen Sie **Blockieren** fest, um zu verhindern, dass Benutzer die Favoritenliste hinzufügen, importieren, sortieren oder bearbeiten. **Nicht konfiguriert** verwendet den Betriebssystemstandard, sodass Benutzer die Liste möglicherweise ändern können.
- **Favoriten zwischen Microsoft-Browsern synchronisieren (nur Desktop)**: **Anfordern** erzwingt, dass Windows die Favoriten zwischen Internet Explorer und Microsoft Edge synchronisiert. Favoriten betreffende Hinzufügungen, Löschungen, Änderungen und Anordnungsänderungen werden zwischen Browsern freigegeben.  **Nicht konfiguriert** verwendet den Betriebssystemstandard, sodass Benutzer möglicherweise die Synchronisierung von Favoriten zwischen den Browsern auswählen können.
- **Standardsuch-Engine**: Wählen Sie die auf dem Gerät zu verwendende Standardsuch-Engine aus. Endbenutzer können diesen Wert jederzeit ändern. Folgende Optionen sind verfügbar:
  - Standard
  - Bing
  - Google
  - Yahoo
  - Benutzerdefinierter Wert
- **Suchvorschläge**: **Nicht konfiguriert** ermöglicht der Such-Engine, Websites während der Eingabe von Suchausdrücken in der Adressleiste vorzuschlagen. **Blockieren** verhindert die Verwendung dieser Funktion.
- **Änderungen an der Suchmaschine zulassen**: **Ja** (Standard) ermöglicht es Benutzern, neue Suchmaschinen hinzuzufügen oder die Standardsuchmaschine in Microsoft Edge zu ändern. Wählen Sie **Nein**, um zu verhindern, dass Benutzer die Suchmaschine anpassen.

  Diese Einstellung ist nur bei Ausführung im [Normalmodus (Kiosk mit mehreren Apps)](#use-microsoft-edge-kiosk-mode) verfügbar.

  CSP: [AllowSearchEngineCustomization](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsearchenginecustomization)

### <a name="privacy-and-security"></a>Datenschutz und Sicherheit

- **InPrivate-Browsen**: **Blockieren** hindert den Endbenutzer daran, InPrivate-Browsersitzungen zu öffnen. **Nicht konfiguriert** lässt diese Funktion zu.
- **Browserverlauf speichern**: **Blockieren** verhindert, dass Microsoft Edge den Browserverlauf speichert. **Nicht konfiguriert** ermöglicht das Speichern des Browserverlaufs.
- **Browserdaten beim Beenden löschen (nur Desktop)**: **Anfordern** löscht Verlauf und Browserdaten, wenn der Benutzer Microsoft Edge beendet. **Nicht konfiguriert** verwendet den Betriebssystemstandard, d.h. die Suchdaten werden möglicherweise zwischengespeichert.
- **Browsereinstellungen zwischen Benutzergeräten synchronisieren**: Wählen Sie aus, wie die Browsereinstellungen zwischen Geräten synchronisiert werden sollen. Folgende Optionen sind verfügbar:
  - **Zulassen**: Zulassen der Synchronisierung von Microsoft Edge-Browsereinstellungen zwischen Geräten des Benutzers.
  - **Außerkraftsetzung durch Benutzer blockieren und aktivieren**: Blockieren der Synchronisierung von Microsoft Edge-Browsereinstellungen zwischen Geräten des Benutzers. Benutzer können diese Einstellung überschreiben.
  - **Blockieren**: Blockieren der Synchronisierung von Microsoft Edge-Browsereinstellungen zwischen Geräten des Benutzers. Benutzer können diese Einstellung nicht überschreiben.
- **Kennwort-Manager**: **Blockieren** deaktiviert den Kennwort-Manager von Microsoft Edge. **Nicht konfiguriert** lässt diese Funktion zu.
- **Cookies**: Wählen Sie aus, wie Cookies im Webbrowser behandelt werden. Folgende Optionen sind verfügbar:
  - **Zulassen**: Ermöglicht das Speichern von Cookies auf dem Gerät.
  - **Alle Cookies blockieren**: Cookies werden nicht auf dem Gerät gespeichert.
  - **Nur Cookies von Drittanbietern blockieren**: Cookies von Drittanbietern oder Partnern werden nicht auf dem Gerät gespeichert.
- **AutoAusfüllen**: **Blockieren** deaktiviert das AutoAusfüllen-Feature auf dem Gerät. **Nicht konfiguriert** erlaubt Benutzern, die Einstellungen für AutoAusfüllen im Browser zu ändern (nur Windows 10 Desktop).
- **DNT-Kopfzeilen senden**: **Nicht konfiguriert** setzt voraus, dass Geräte DNT-Kopfzeilen an Websites senden, die Nachverfolgungsinformationen anfordern (empfohlen). Wählen Sie **Blockieren** aus, um zu verhindern, dass das Gerät diese Kopfzeilen sendet, die Websites ermöglichen, den Benutzer nachzuverfolgen.
- **WebRTC-Localhost-IP-Adresse**: **Blockieren** verhindert die Anzeige der Localhost-IP-Adressen von Benutzern bei Telefonaten mit dem WebRTC-Protokoll. **Nicht konfiguriert** ermöglicht die Anzeige der Localhost-IP-Adressen von Benutzern bei Telefonaten mit diesem Protokoll.
- **Datenerfassung für Livekacheln**: Wählen Sie **Blockieren** aus, um das Sammeln von Daten durch Windows aus den Livekacheln zu beenden, wenn eine Seite an das Startmenü von Microsoft Edge angeheftet ist. **Nicht konfiguriert** erlaubt das Sammeln dieser Informationen.
- **Benutzer kann Zertifikatfehler außer Kraft setzen**: **Blockieren** verhindert, dass Benutzer auf Websites mit SSL- oder TLS-Fehlern zugreifen. **Nicht konfiguriert** ermöglicht Benutzern den Zugriff auf diese Websites.

### <a name="additional"></a>Zusätzliche Informationen

- **Microsoft Edge-Browser (nur Mobilgerät)**: Wählen Sie **Blockieren** aus, um die Verwendung von Microsoft Edge auf dem Gerät zu verhindern. Wenn Sie Microsoft Edge blockieren, gelten die individuellen Einstellungen nur für den Desktop. **Nicht konfiguriert** ermöglicht die Verwendung des Microsoft Edge-Webbrowsers auf dem Gerät.
- **Adressleisten-Dropdown (nur Desktop)**: **Blockieren** verhindert, dass Microsoft Edge bei der Eingabe weiterhin eine Liste mit Vorschlägen in einer Dropdownliste anzeigt. Mit dieser Option kann die zwischen Microsoft Edge und Microsoft-Diensten genutzte Netzwerkbandbreite minimiert werden. **Nicht konfiguriert** ermöglicht Microsoft Edge, eine Liste mit Vorschlägen anzuzeigen.
- **Vollbild**: Wählen Sie **Blockieren** aus, damit Microsoft Edge nicht nur den Webinhalt anzeigt und Microsoft Edge (Vollbildmodus) ausblendet. **Nicht konfiguriert** verwendet den Betriebssystemstandard, d.h. Microsoft Edge kann den Vollbildmodus verwenden.
- **Informationen zu Flags**: **Blockieren** verhindert, dass Endbenutzer auf die `about:flags`-Seite in Microsoft Edge zugreifen, die die Entwickler- und Experimentaleinstellungen enthält. **Nicht konfiguriert** verwendet den Betriebssystemstandard, sodass Benutzer auf die `about:flags`-Seite zugreifen können.
- **Entwicklungstools:** **Blockieren** hindert den Endbenutzer daran, die Microsoft Edge-Entwicklertools aufzurufen. **Nicht konfiguriert** ermöglicht Benutzern, die Entwicklertools zu öffnen.
- **Erweiterungen**: **Nicht konfiguriert** lässt zu, dass der Benutzer Microsoft Edge-Erweiterungen auf dem Gerät installiert. **Blockieren** verhindert die Installation.
- **Querladen von Entwicklererweiterungen**: **Blockieren** verhindert das Querladen durch Microsoft Edge, wodurch nicht überprüfte Erweiterungen mit dem Feature **Erweiterungen laden** installiert und ausgeführt werden. **Nicht konfiguriert** verwendet den Betriebssystemstandard, der das Querladen möglicherweise erlaubt.
- **Erforderliche Erweiterungen**: Wählen Sie aus, welche Erweiterungen in Microsoft Edge nicht von Endbenutzern deaktiviert werden können. Geben Sie die Paketfamiliennamen ein, und wählen Sie **Hinzufügen** aus. [Paketfamiliennamen (PFN) suchen](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) listet einige hilfreiche Informationen auf.

  Sie können auch eine CSV-Datei **Importieren**, die die Paketfamiliennamen enthält.

- **JavaScript**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Java-Skripts im Browser auf dem Gerät ausgeführt werden. **Nicht konfiguriert** lässt die Ausführung von Skripts wie z.B. JavaScript im Microsoft Edge-Browser zu.

## <a name="network-proxy"></a>Netzwerkproxy

- **Proxyeinstellungen automatisch ermitteln**: Bei Aktivierung versucht das Gerät, den Pfad zu einem PAC-Skript zu finden.
- **Proxyskript verwenden**: Verwenden Sie diese Option, um einen Pfad zu einem PAC-Skript zum Konfigurieren des Proxyservers anzugeben.
  - **Adress-URL für Setupskript**: Geben Sie die URL eines PAC-Skripts an, das Sie verwenden möchten, um den Proxyserver zu konfigurieren.
- **Manuellen Proxyserver verwenden**: Verwenden Sie diese Option, wenn Sie Proxyserverinformationen manuell eingeben möchten.
  - **Adresse**: Geben Sie den Namen oder die IP-Adresse des Proxyservers an.
  - **Portnummer**: Geben Sie die Portnummer Ihres Proxyservers ein.
  - **Proxyausnahmen**: Geben Sie URLs an, die den Proxyserver nicht verwenden dürfen. Trennen Sie die einzelnen Elemente durch Semikola.
  - **Proxyserver für lokale Adresse umgehen**: Aktivieren Sie diese Option, wenn Sie den Proxyserver nicht für lokale Adressen in Ihrem Intranet verwenden möchten.

## <a name="password"></a>Kennwort

- **Kennwort**: Der Endbenutzer muss ein Kennwort eingeben, um auf das Gerät zugreifen zu können.
  - **Erforderlicher Kennworttyp**: Gibt an, ob das Kennwort nur numerisch sein muss oder alphanumerisch.
  - **Minimale Kennwortlänge**: Gilt nur für Windows 10 Mobile.
  - **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird**: Für Geräte mit Microsoft 10: Wenn auf dem Gerät BitLocker aktiviert ist, wird in den BitLocker-Wiederherstellungsmodus gewechselt, sobald die Anzahl der von Ihnen angegebenen Anmeldefehler erreicht ist. Wenn BitLocker nicht für dieses Gerät aktiviert ist, wird diese Einstellung nicht angewendet. Für Geräte mit Windows 10 Mobile: Das Gerät wird zurückgesetzt, sobald die Anzahl der von Ihnen angegebenen Anmeldeversuche fehlgeschlagen ist.
  - **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung**: Gibt den Zeitraum der Inaktivität für ein Gerät an, bevor der Bildschirm gesperrt wird.
  - **Kennwortablauf (Tage)**: Gibt den Zeitraum an, nach dem das Kennwort für das Gerät geändert werden muss.
  - **Wiederverwendung vorheriger Kennwörter verhindern**: Gibt an, wie viele zuvor verwendete Kennwörter vom Gerät gespeichert werden.
  - **Kennwort anfordern, wenn Gerät aus Leerlaufzustand zurückkehrt (nur Mobile)**: Gibt an, dass der Benutzer ein Kennwort zum Entsperren des Geräts eingeben muss (nur Windows 10 Mobile).
  - **Einfache Kennwörter**: Erlaubt die Verwendung einfacher Kennwörter wie 1111 oder 1234. Diese Einstellung ermöglicht es auch, die Verwendung von Windows-Bildcodes zu blockieren.
- **Automatische Verschlüsselung bei AADJ**: Die Wahl von **Blockieren** verhindert die automatische BitLocker-Geräteverschlüsselung bei der Vorbereitung des Geräts für die erste Verwendung, wenn das Gerät Azure AD beitritt. **Nicht konfiguriert** (Standard) verwendet die Standardeinstellung des Betriebssystems, die ggf. die Verschlüsselung aktiviert. Weitere Informationen zur [Geräteverschlüsselung mit BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption).

  [CSP: Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **FIPS-Richtlinie (Federal Information Processing Standard)**: Bei Wahl von **Zulassen** wird die FIPS-Richtlinie (Federal Information Processing Standard) verwendet, die in den USA ein bundesgesetzlicher Standard für Verschlüsselung, Hashing und Signatur ist. Bei Wahl von **Nicht konfiguriert** (Standard) gilt die Standardeinstellung des Betriebssystems, die FIPS nicht verwendet.

  [CSP: Cryptography/AllowFipsAlgorithmPolicy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Windows Hello-Geräteauthentifizierung**: Bei Wahl von **Zulassen** wird Benutzern ermöglicht, sich mit einem Windows Hello-Begleitgerät, wie beispielsweise einem Smartphone, Fitnessband oder IoT-Gerät, bei einem Windows 10-Computer anzumelden. Bei Wahl von **Nicht konfiguriert** (Standard) gilt die Standardeinstellung des Betriebssystems, die Windows Hello-Begleitgeräte an der Authentifizierung bei Windows hindern kann.

  [CSP: Authentication/AllowSecondaryAuthenticationDevice](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Webanmeldung**: Ermöglicht die Unterstützung der Windows-Anmeldung für nicht zu AD FS (Active Directory-Verbunddienste) gehörige Verbundanbieter, wie beispielsweise SAML (Security Assertion Markup Language). SAML verwendet sichere Token, die Benutzern in Webbrowsern einmaliges Anmelden (SSO) ermöglichen. Folgende Optionen sind verfügbar:

  - Bei Wahl von **Nicht konfiguriert** (Standard) wird die Standardeinstellung des Betriebssystems auf dem Gerätverwendet.
  - **Aktiviert**: Der Anbieter für Webanmeldeinformationen ist für die Anmeldung aktiviert.
  - **Deaktiviert**: Der Anbieter für Webanmeldeinformationen ist für die Anmeldung deaktiviert.

  [CSP: Authentifizierung/EnableWebSignIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **Bevorzugte Azure AD-Mandantendomäne**: Geben Sie einen in Ihrer Azure AD-Organisation vorhandenen Domänennamen ein. Wenn sich Benutzer bei dieser Domäne anmelden, müssen sie den Domänennamen nicht eingeben. Geben Sie beispielsweise `contoso.com` ein. Benutzer in der Domäne `contoso.com` können sich mit ihrem Benutzernamen, wie beispielsweise „abby“, statt mit „abby@contoso.com“ anmelden.

  [CSP: Authentication/PreferredAadTenantDomainName](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

## <a name="per-app-privacy-exceptions"></a>App-bezogene Datenschutzausnahmen

Sie können Apps hinzufügen, die ein anderes Datenschutzverhalten aufweisen als das unter „Standarddatenschutz“ definierte Verhalten.

- **Paketname**: App-Paketfamilienname.
- **Name**: Der Name der App.

### <a name="exceptions"></a>Ausnahmen

- **Kontoinformationen**: Legen Sie fest, ob diese App auf den Benutzernamen, das Bild und andere Kontaktinformationen zugreifen darf.
- **Hintergrund-Apps**: Legen Sie fest, ob diese App im Hintergrund ausgeführt werden darf.
- **Kalender**: Legen Sie fest, ob diese App auf den Kalender zugreifen darf.
- **Anrufliste**: Legen Sie fest, ob diese App auf Ihre Anrufliste zugreifen darf.
- **Kamera**: Legen Sie fest, ob diese App auf die Kamera zugreifen darf.
- **Kontakte**: Legen Sie fest, ob diese App auf Kontakte zugreifen darf.
- **E-Mail**: Legen Sie fest, ob diese App auf E-Mails zugreifen und diese versenden darf.
- **Standort**: Legen Sie fest, ob diese App auf Standortinformationen zugreifen darf.
- **Nachrichten**: Legen Sie fest, ob diese App SMS oder MMS-Nachrichten lesen oder senden darf.
- **Mikrofon**: Legen Sie fest, ob diese App das Mikrofon verwenden darf.
- **Bewegung**: Legen Sie fest, ob diese App auf die Gerätebewegungsinformationen zugreifen darf.
- **Benachrichtigungen**: Legen Sie fest, ob diese App auf Benachrichtigungen zugreifen darf.
- **Telefon**: Legen Sie fest, ob diese App auf das Telefon zugreifen darf.
- **Radios**: Einige Apps verwenden Radios (z.B. Bluetooth) auf Ihrem Gerät, um Daten zu senden und zu empfangen, und müssen diese Radios ein- oder ausschalten. Legen Sie fest, ob diese App diese Radios steuern kann.
- **Aufgaben**: Legen Sie fest, ob diese App auf Ihre Aufgaben zugreifen darf.
- **Vertrauenswürdige Geräte:** Legen Sie fest, ob diese App vertrauenswürdige Geräte verwenden kann. Als vertrauenswürdige Geräte wird Hardware angesehen, mit der Sie bereits eine Verbindung hergestellt haben oder die in das Gerät integriert ist. Verwenden Sie z. B. Fernsehgeräte oder Projektoren als vertrauenswürdige Geräte.
- **Feedback und Diagnose**: Legen Sie fest, ob diese App auf Diagnoseinformationen zugreifen darf.
- **Mit Geräten synchronisieren**: Legen Sie fest, ob diese App automatisch Informationen mit Drahtlosgeräten teilen und synchronisieren darf, die nicht explizit mit dem Gerät gekoppelt sind.

## <a name="personalization"></a>Personalization

- **URL zu Desktophintergrundbild (nur Desktop)**: Geben Sie die URL zu einem Bild im JPEG-Format an, das Sie als Windows-Desktophintergrund verwenden möchten. Benutzer können das Bild nicht ändern.

## <a name="printer"></a>Drucker

- **Drucker**: Liste der lokalen Drucker, die hinzugefügt wurden.
- **Standarddrucker**: Festlegen als Standarddrucker.
- **Benutzerzugriff für das Hinzufügen neuer Drucker**: Zulassen oder Blockieren der Verwendung von lokalen Druckern.

## <a name="privacy"></a>Datenschutz

- **Eingabepersonalisierung**: Verhindert die Verwendung cloudbasierter Sprachdienste für Cortana, Diktierfunktionen oder Microsoft Store-Apps. Wenn Sie diese Dienste zulassen, kann Microsoft Voice-Daten erfassen, um den Dienst zu verbessern.
- **Automatisches Akzeptieren der Zustimmungsaufforderung des Benutzers zu Kopplung und Datenschutz**: Erlaubt Windows beim Ausführen von Apps das automatische Akzeptieren von Benachrichtigungen zur Zustimmung zu Kopplung und Datenschutz.
- **Benutzeraktivitäten veröffentlichen**: **Blockieren** Sie diese Einstellung, um geteilte Aktivitäten und die Ermittlungen von kürzlich verwendeten Ressourcen in der Programmumschaltung zu vermeiden.
- **Nur lokale Aktivitäten**: **Blockieren** Sie diese Einstellung, um geteilte Aktivitäten und Ermittlungen von kürzlich in der Programmumschaltung verwendeten Ressourcen anhand von ausschließlich lokalen Aktivitäten zu vermeiden.

Sie können Informationen definieren, auf die alle Apps auf dem Gerät zugreifen können. Definieren Sie ebenfalls Ausnahmen für jede App mithilfe von **App-bezogenen Datenschutzausnahmen**.

### <a name="exceptions"></a>Ausnahmen

- **Kontoinformationen**: Legen Sie fest, ob diese App auf den Benutzernamen, das Bild und andere Kontaktinformationen zugreifen darf.
- **Hintergrund-Apps**: Legen Sie fest, ob diese App im Hintergrund ausgeführt werden darf.
- **Kalender**: Legen Sie fest, ob diese App auf den Kalender zugreifen darf.
- **Anrufliste**: Legen Sie fest, ob diese App auf Ihre Anrufliste zugreifen darf.
- **Kamera**: Legen Sie fest, ob diese App auf die Kamera zugreifen darf.
- **Kontakte**: Legen Sie fest, ob diese App auf Kontakte zugreifen darf.
- **E-Mail**: Legen Sie fest, ob diese App auf E-Mails zugreifen und diese versenden darf.
- **Standort**: Legen Sie fest, ob diese App auf Standortinformationen zugreifen darf.
- **Nachrichten**: Legen Sie fest, ob diese App SMS oder MMS-Nachrichten lesen oder senden darf.
- **Mikrofon**: Legen Sie fest, ob diese App das Mikrofon verwenden darf.
- **Bewegung**: Legen Sie fest, ob diese App auf die Gerätebewegungsinformationen zugreifen darf.
- **Benachrichtigungen**: Legen Sie fest, ob diese App auf Benachrichtigungen zugreifen darf.
- **Telefon**: Legen Sie fest, ob diese App auf das Telefon zugreifen darf.
- **Radios**: Einige Apps verwenden Radios (z.B. Bluetooth) auf Ihrem Gerät, um Daten zu senden und zu empfangen, und müssen diese Radios ein- oder ausschalten. Legen Sie fest, ob diese App diese Radios steuern kann.
- **Aufgaben**: Legen Sie fest, ob diese App auf Ihre Aufgaben zugreifen darf.
- **Vertrauenswürdige Geräte:** Legen Sie fest, ob diese App vertrauenswürdige Geräte verwenden kann. Als vertrauenswürdige Geräte wird Hardware angesehen, mit der Sie bereits eine Verbindung hergestellt haben oder die in das Gerät integriert ist. Verwenden Sie z. B. Fernsehgeräte oder Projektoren als vertrauenswürdige Geräte.
- **Feedback und Diagnose**: Legen Sie diese Einstellung fest, wenn diese App auf Diagnoseinformationen zugreifen soll.
- **Mit Geräten synchronisieren**: Legen Sie fest, ob diese App automatisch Informationen mit Drahtlosgeräten teilen und synchronisieren darf, die nicht explizit mit Ihrem PC, Tablet oder Telefon gekoppelt sind.

## <a name="projection"></a>Projektion

- **Benutzereingabe über Empfänger der drahtlosen Anzeige**: Blockiert Benutzereingaben über Empfänger der drahtlosen Anzeige.
- **Projektion auf diesem PC**: Verhindert, dass andere Geräte den PC für die Projektion finden.
- **PIN für Kopplung erforderlich**: Erfordert eine PIN beim Herstellen der Verbindung mit einem Projektionsgerät.

## <a name="reporting-and-telemetry"></a>Berichterstellung und Telemetrie

- **Nutzungsdaten freigeben**: Wählen Sie die Ebene der Diagnosedaten, die gesendet werden. Folgende Optionen sind verfügbar:
  - Sicherheit
  - Einfach
  - Erweitert
  - Vollständig
- **Microsoft Edge-Browserdaten an Microsoft 365 Analytics senden**: Um dieses Feature verwenden zu können, legen Sie für die Einstellung **Nutzungsdaten freigeben** **Erweitert** oder **Vollständig** fest. Dieses Feature steuert, welche Daten Microsoft Edge an Microsoft 365 Analytics für Unternehmensgeräte mit einer konfigurierten kommerziellen ID sendet. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert**: Verwendung des Betriebssystemstandards, d.h. Browserverlaufsdaten werden möglicherweise nicht gesendet.
  - **Nur Intranetdaten senden**: Ermöglicht dem Administrator, den Intranetdatenverlauf zu senden.
  - **Nur Internetdaten senden**: Ermöglicht dem Administrator, den Internetdatenverlauf zu senden.
  - **Intranet- und Internetdaten senden**: Ermöglicht dem Administrator, den Intranet- und Internetdatenverlauf zu senden.
- **Telemetrieproxyserver**: Geben Sie den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) oder die IP-Adresse eines Proxyservers an, um Anforderungen zu Benutzererfahrung und Telemetrie im verbundenen Modus über eine SSL-Verbindung (Secure Sockets Layer) weiterzuleiten. Das Format dieser Einstellung lautet *Server*:*Port*. Wenn beim benannten Proxy ein Fehler auftritt oder kein Proxy angegeben wurde, obwohl diese Richtlinie aktiviert ist, werden die Daten zu Benutzererfahrung und Telemetrie im verbundenen Modus nicht gesendet und verbleiben auf dem lokalen Gerät.

  Beispiele für das Format:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

## <a name="search"></a>Suchen

- **SafeSearch (nur Mobilgeräte)**: Steuert, wie Cortana nicht jugendfreie Inhalte in den Suchergebnissen filtert. Sie können **Streng** oder **Mittel** auswählen oder dem Endbenutzer ermöglichen, seine eigenen Einstellungen zu wählen.
- **Webergebnisse in der Suche anzeigen**: Blockieren oder Zulassen, dass Webergebnisse für Suchvorgänge auf dem Gerät angezeigt werden.

## <a name="start"></a>Starten

- **Startmenülayout**: Sie können eine XML-Datei hochladen, die Ihre Anpassungen, einschließlich der Reihenfolge der aufgeführten Apps und mehr, enthält, um das Startmenü auf Desktopgeräten anzupassen. Benutzer können das von Ihnen festgelegte Startmenülayout nicht ändern.
- **Websites an Kacheln im Startmenü anheften**: Importieren Sie Bilder von Microsoft Edge, die im Windows-Startmenü von Desktopgeräten als Links angezeigt werden.
- **Apps von der Taskleiste lösen**: Bei Festlegung auf **Blockieren** wird verhindert, dass der Benutzer Apps von der Taskleiste lösen kann.
- **Schneller Wechsel zwischen Benutzern**: Legen Sie **Blockieren** fest, um das Wechseln zwischen zwei gleichzeitig angemeldeten Benutzern ohne Abmeldung zu verhindern.
- **Meistverwendete Apps**: Legen Sie **Blockieren** fest, um die Anzeige der meistverwendeten Apps im Startmenü auszublenden. Damit wird auch der entsprechende Schalter in der App „Einstellungen“ deaktiviert.
- **Zuletzt hinzugefügte Apps**: Legen Sie **Blockieren** fest, um die Anzeige der zuletzt hinzugefügten Apps im Startmenü auszublenden. Damit wird auch der entsprechende Schalter in der App „Einstellungen“ deaktiviert.
- **Startbildschirmmodus**: Wählen Sie aus, wie der Startbildschirm angezeigt werden soll. Sie können **Vollbild** oder **Kein Vollbild** festlegen.
- **Zuletzt geöffnete Elemente in Sprunglisten**: Legen Sie **Blockieren** fest, um die Anzeige zuletzt verwendeter Sprunglisten im Startmenü auszublenden. Damit wird auch der entsprechende Schalter in der App „Einstellungen“ deaktiviert.
- **App-Liste**: Legen Sie fest, wie die App „Einstellungen“ angezeigt werden soll. Folgende Optionen sind verfügbar: 
  - Ausblenden
  - Die App „Einstellungen“ reduzieren und deaktivieren 
  - Die App „Einstellungen“ entfernen und deaktivieren
- **Netzschaltersymbol**: Legen Sie **Blockieren** fest, um das Netzschaltersymbol im Startmenü auszublenden.
- **Benutzerkachel**: Legen Sie **Blockieren** fest, um die Benutzerkachel im Startmenü auszublenden.
  - **Sperren**: Legen Sie **Blockieren** fest, um die Option `Lock` in der Benutzerkachel im Startmenü auszublenden.
  - **Abmelden**: Legen Sie **Blockieren** fest, um die Option `Sign out` in der Benutzerkachel im Startmenü auszublenden.
- **Herunterfahren**: Legen Sie **Blockieren** fest, um die Optionen `Update and shut down` und `Shut down` im Netzschaltersymbol im Startmenü auszublenden.
- **Energie sparen**: Legen Sie **Blockieren** fest, um die Option `Sleep` im Netzschaltersymbol im Startmenü auszublenden.
- **Ruhezustand**: Legen Sie **Blockieren** fest, um die Option `Hibernate` im Netzschaltersymbol im Startmenü auszublenden.
- **Benutzer wechseln**: Legen Sie **Blockieren** fest, um die Option `Switch account` in der Benutzerkachel im Startmenü auszublenden.
- **Neustartoptionen**: Legen Sie **Blockieren** fest, um die Optionen `Update and restart` und `Restart` im Netzschaltersymbol im Startmenü auszublenden.
- **Dokumente im Startmenü**: Blendet den Ordner „Dokumente“ im Windows-Startmenü aus oder ein.
- **Downloads im Startmenü**: Blendet den Ordner „Downloads“ im Windows-Startmenü aus oder ein.
- **Datei-Explorer im Startmenü**: Blendet die Datei-Explorer-App im Windows-Startmenü aus oder ein.
- **Heimnetzgruppe im Startmenü**: Blendet den Ordner „Heimnetzgruppe“ im Windows-Startmenü aus oder ein.
- **Musik im Startmenü**: Blendet den Ordner „Musik“ im Windows-Startmenü aus oder ein.
- **Netzwerk im Startmenü**: Blendet den Ordner „Netzwerk“ im Windows-Startmenü aus oder ein.
- **Persönlicher Ordner im Startmenü**: Blendet den persönlichen Ordner im Windows-Startmenü aus oder ein.
- **Bilder im Startmenü**: Blendet den Ordner für Bilder im Windows-Startmenü aus oder ein.
- **Einstellungen im Startmenü**: Blendet die Einstellungen-App im Windows-Startmenü aus oder ein.
- **Videos im Startmenü**: Blendet den Ordner für Videos im Windows-Startmenü aus oder ein.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen für Microsoft Edge**: Aktiviert SmartScreen für Microsoft Edge für den Zugriff auf Website- und Dateidownloads.
- **Zugriff auf schädliche Websites**: Hindern Sie Benutzer daran, die Warnungen des Windows Defender SmartScreen-Filters zu ignorieren, und blockieren Sie sie, damit sie die Website nicht besuchen.
- **Download nicht überprüfter Dateien**: Hindern Sie Benutzer daran, die Warnungen des Windows Defender SmartScreen-Filters zu ignorieren, und blockieren Sie sie, damit sie nicht überprüfte Dateien herunterladen.

## <a name="windows-spotlight"></a>Windows-Blickpunkt

- **Windows-Blickpunkt**: Verwenden Sie diese Einstellung, um auf Windows 10-Geräten alle Funktionen von Windows-Blickpunkt zu blockieren. Wenn Sie diese Einstellung blockieren, sind die folgenden Einstellungen nicht verfügbar:
  - **Windows-Blickpunkt auf dem Sperrbildschirm**: Verhindert, dass Windows-Blickpunkt Informationen auf dem Gerätesperrbildschirm anzeigt.
  - **Drittanbietervorschläge in Windows-Blickpunkt**: Verhindert, dass Windows-Blickpunkt Inhalte vorschlägt, die nicht von Microsoft stammen.
  - **Endbenutzerfeatures**: Blockiert Endbenutzerfeatures wie Startmenüvorschläge und Mitgliedschaftsbenachrichtigungen.
  - **Windows-Tipps**: Blockiert die Anzeige von Popuptipps in Windows.
  - **Windows-Blickpunkt im Info-Center**: Verhindert, dass Vorschläge von Windows-Blickpunkt wie neue Apps oder Sicherheitsinhalte im Windows-Info-Center angezeigt werden.
  - **Personalisierung von Windows-Blickpunkt**: Verhindert, dass Windows-Blickpunkt Ergebnisse basierend auf der Nutzung eines Geräts personalisiert.
  - **Windows-Begrüßungsseite**: Blockiert die Windows-Begrüßungsseite, die dem Benutzer Informationen zu neuen oder aktualisierten Funktionen anzeigt.

## <a name="windows-defender-antivirus"></a>Windows Defender Antivirus

- **Echtzeitüberwachung**: Aktiviert die Echtzeitüberwachung auf Schadsoftware, Spyware und andere unerwünschte Software.
- **Verhaltensüberwachung**: Ermöglicht Defender, Geräte auf bestimmte bekannte Muster verdächtiger Aktivitäten zu überprüfen.
- **Netzwerkinspektionssystem (NIS)**: NIS trägt zum Schutz von Geräten vor netzwerkbasierten Exploits bei. Es verwendet die Signaturen bekannter Sicherheitsrisiken aus dem Microsoft Endpoint Protection Center, um schädlichen Datenverkehr zu erkennen und zu blockieren.
- **Alle Downloads überprüfen**: Steuert, ob Defender alle aus dem Internet heruntergeladenen Dateien überprüft.
- **In Microsoft-Webbrowsern geladene Skripts überprüfen**: Ermöglicht Defender die Überprüfung von Skripts, die in Internet Explorer verwendet werden.
- **Endbenutzerzugriff auf Defender**: Steuert, ob die Benutzeroberfläche von Windows Defender für Endbenutzer ausgeblendet ist. Wenn diese Einstellung geändert wird, wird die Änderung wirksam, wenn der Endbenutzer-PC das nächste Mal neu gestartet wird.
- **Intervall für Signaturaktualisierung (in Stunden):** Geben Sie das Intervall ein, in dem Defender auf neue Signaturdateien prüft.
- **Datei- und Programmaktivität überwachen**: Ermöglicht Defender die Überwachung der Datei- und Programmaktivität auf Geräten.
- **Tage bis zum Löschen von in Quarantäne befindlicher Schadsoftware**: Ermöglicht die fortgesetzte Nachverfolgung behandelter Schadsoftware für die eingegebene Anzahl von Tagen, damit Sie zuvor betroffene Geräte manuell überprüfen können. Wenn Sie die Anzahl von Tagen auf **0** festlegen, bleibt Schadsoftware im Quarantäneordner und wird nicht automatisch entfernt.
- **CPU-Nutzungslimit während einer Überprüfung:** Begrenzen Sie die CPU-Nutzung, die bei Überprüfungen genutzt werden darf (von **1** bis **100**).
- **Archivdateien überprüfen**: Ermöglicht Defender die Überprüfung von Archivdateien wie ZIP- oder CAB-Dateien.
- **Eingehende E-Mail überprüfen**: Ermöglicht Defender das Überprüfen von E-Mail-Nachrichten beim Eingang auf dem Gerät.
- **Bei einer vollständigen Überprüfung Wechseldatenträger überprüfen**: Ermöglicht Defender das Überprüfen von Wechseldatenträgern wie USB-Sticks.
- **Bei einer vollständigen Überprüfung zugeordnete Netzlaufwerke überprüfen**: Ermöglicht Defender das Überprüfen von Dateien auf zugeordneten Netzwerklaufwerken.
  Wenn die Dateien auf dem Laufwerk schreibgeschützt sind, kann Defender gefundene Schadsoftware nicht entfernen.
- **Über Netzwerkordner geöffnete Dateien überprüfen**: Ermöglicht Defender das Überprüfen von Dateien auf freigegebenen Netzlaufwerken (z.B. Dateien, auf die über einen UNC-Pfad zugegriffen wird). Wenn die Dateien auf dem Laufwerk schreibgeschützt sind, kann Defender gefundene Schadsoftware nicht entfernen.
- **Cloudschutz**: Erlaubt oder sperrt den Empfang von Informationen über Schadsoftwareaktivitäten der von Ihnen verwalteten Geräten durch den Microsoft Active Protection Service. Diese Informationen dienen zum Verbessern des Diensts für die Zukunft.
- **Vor dem Senden von Beispielen bei Benutzern nachfragen**: Steuert, ob potenziell schädliche Dateien, die möglicherweise genauer analysiert werden müssen, automatisch an Microsoft gesendet werden.
- **Uhrzeit für die Durchführung einer täglichen Schnellüberprüfung**: Wählen Sie die Uhrzeit der Ausführung einer täglichen Schnellüberprüfung. Bei Wahl von **Nicht konfiguriert** erfolgt keine tägliche Überprüfung. Wenn Sie eine weitere Anpassung wünschen, konfigurieren Sie die Einstellung **Art der durchzuführenden Systemüberprüfung**.

  [Defender/ScheduleQuickScanTime (CSP)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)
- **Art der durchzuführenden Systemüberprüfung**: Planen Sie eine Systemüberprüfung, einschließlich des Grads der Überprüfung, sowie Tag und Uhrzeit der Ausführung der Überprüfung. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert**: Es erfolgt keine Planung einer Systemüberprüfung auf dem Gerät. Endbenutzer können Überprüfungen nach Bedarf oder Wunsch manuell auf ihren Geräten durchführen.
  - **Deaktivieren**: Deaktiviert die Systemüberprüfung auf dem Gerät. Wählen Sie diese Option, wenn Sie eine Antivirenlösung eines Partners verwenden, die Geräte überprüft.
  - **Schnellüberprüfung**: Dient zum Überprüfen gängiger Speicherorte, an denen Schadsoftware registriert sein kann (z.B. Registrierungsschlüssel und bekannte Windows-Startordner).
    - **Geplanter Tag**: Wählen Sie den Tag der Ausführung der Überprüfung.
    - **Geplante Zeit**: Wählen Sie die Uhrzeit der Ausführung der Überprüfung.
  - **Vollständige Überprüfung**: Dient zum Überprüfen gängiger Speicherorte, an denen Schadsoftware registriert sein kann sowie aller Dateien und Ordner auf dem Gerät.
    - **Geplanter Tag**: Wählen Sie den Tag der Ausführung der Überprüfung.
    - **Geplante Zeit**: Wählen Sie die Uhrzeit der Ausführung der Überprüfung.

  Diese Einstellung steht ggf. in Konflikt mit der Einstellung **Uhrzeit für die Durchführung einer täglichen Schnellüberprüfung**. Empfehlungen:

  - Konfigurieren Sie zum Ausführen einer täglichen Schnellüberprüfung die Einstellung **Uhrzeit für die Durchführung einer täglichen Schnellüberprüfung**.
  - Um eine tägliche Schnellüberprüfung und vollständige Überprüfung einmal pro Woche auszuführen, konfigurieren Sie die Einstellung **Uhrzeit für die Durchführung einer täglichen Schnellüberprüfung**, und legen Sie die Einstellung **Art der durchzuführenden Systemüberprüfung** auf eine vollständige Überprüfung mit Tag und Uhrzeit fest.
  - Konfigurieren Sie **Uhrzeit für die Durchführung einer täglichen Schnellüberprüfung** nicht parallel mit auf **Schnellüberprüfung** festgelegter Einstellung **Art der durchzuführenden Systemüberprüfung**. Diese Einstellungen können in Konflikt stehen und eine Überprüfung möglicherweise verhindern.
  - Um jeden Dienstag um 6 Uhr eine Schnellüberprüfung durchzuführen, konfigurieren Sie die Einstellung **Art der durchzuführenden Systemüberprüfung**.

  [CSP: Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [CSP: Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [CSP: Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **Möglicherweise unerwünschte Software erkennen**: Ermöglicht die Auswahl einer der folgenden Schutzebenen, wenn Windows potenziell unerwünschte Software erkennt:
  - **Blockieren**
  - **Überwachung** Weitere Informationen zu potenziell unerwünschten Apps finden Sie in [Erkennen und Blockieren möglicherweise unerwünschter Anwendungen](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).
- **Aktionen für erkannte Schadsoftwarebedrohungen**: Wählen Sie die Maßnahmen aus, die Defender bei den einzelnen erkannten Bedrohungsstufen (Niedrig, Mittel, Hoch und Schwerwiegend) ergreifen soll. Folgende Optionen sind verfügbar:
  - **Bereinigen**
  - **Quarantäne**
  - **Entfernen**
  - **Zulassen**
  - **Benutzerdefiniert**
  - **Blockieren**

### <a name="windows-defender-antivirus-exclusions"></a>Windows Defender Antivirus-Ausschlüsse

- **Dateien und Ordner, die bei Überprüfungen und Echtzeitschutz ausgeschlossen werden sollen**: Fügt Dateien und Ordner wie **C:\Pfad** oder **%ProgramFiles%\Pfad\Dateiname.exe** der Ausschlussliste hinzu. Diese Dateien und Ordner werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.
- **Dateierweiterungen, die bei Überprüfungen und Echtzeitschutz ausgeschlossen werden sollen**: Fügt der Ausschlussliste eine oder mehrere Erweiterungen wie **jpg** oder **txt** hinzu. Dateien mit diesen Erweiterungen werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.
- **Prozesse, die von Überprüfungen und Echtzeitschutz ausgenommen werden sollen**: Fügt der Ausschlussliste einen oder mehrere Prozesse vom Typ **.exe**, **.com** oder **.scr** hinzu. Diese Prozesse werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.

## <a name="next-steps"></a>Nächste Schritte

Weitere technische Details zu den einzelnen Einstellungen und den unterstützten Windows-Editionen finden Sie in der Referenz zum [Richtlinien-Konfigurationsdienstanbieter für Windows 10](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider).
