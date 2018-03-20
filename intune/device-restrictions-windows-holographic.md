---
title: "Einstellungen für Geräteeinschränkungen für Windows Holographic for Business in Microsoft Intune"
titlesuffix: Azure portal
description: "In diesem Artikel erhalten Sie Informationen zu den Intune-Einstellungen zur Steuerung von Geräteeinstellungen und -funktionen auf Windows Holographic for Business-Geräten."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 10bb5a2eac9e72ba5b09a9a6f02932e872328c75
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-windows-holographic-for-business-device-restriction-settings"></a>Einstellungen für Geräteeinschränkungen für Windows Holographic for Business in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Die folgenden Einstellungen für Geräteeinschränkungen werden auf Geräten unterstützt, die Windows Holographic for Business ausführen, z.B. Microsoft HoloLens.

## <a name="general"></a>Allgemein

- **Manuelle Aufhebung der Registrierung:** Erlaubt dem Benutzer das manuelle Löschen des Unternehmensbereichskontos vom Gerät.
- **Cortana:** Aktiviert oder deaktiviert den Cortana-Sprach-Assistenten.
- **Geolocation:** Gibt an, ob das Gerät Standortdienstinformationen verwenden kann.



## <a name="password"></a>Kennwort
-   **Kennwort:** Der Endbenutzer muss ein Kennwort eingeben, um auf das Gerät zugreifen zu können.
    -   **Kennwort anfordern, wenn Gerät aus Leerlaufzustand zurückkehrt:** Gibt an, dass der Benutzer ein Kennwort zum Entsperren des Geräts eingeben muss.



## <a name="app-store"></a>App Store

-   **Apps aus Store automatisch aktualisieren:** Ermöglicht die automatische Aktualisierung von Apps, die aus dem Microsoft Store installiert wurden.
-   **Installation vertrauenswürdiger Apps:** Ermöglicht das Querladen von Apps, die mit einem vertrauenswürdigen Zertifikat signiert sind.
-   **Entwicklersperre aufheben:** Ermöglicht dem Endbenutzer, Windows-Entwicklereinstellungen – z.B. das Zulassen quergeladener Apps – zu ändern.

## <a name="edge-browser"></a>Edge-Browser

-   **Microsoft Edge-Browser:** Erlaubt die Verwendung des Edge-Webbrowsers auf dem Gerät.
-   **Cookies:** Erlaubt Browsern das Speichern von Internetcookies auf dem Gerät.
-   **Popups:** Blockiert Popupfenster im Browser (gilt nur für Windows 10 Desktop).
-   **Suchvorschläge:** Ermöglicht dem Suchmodul, Websites während der Eingabe von Suchausdrücken vorzuschlagen.
-   **Kennwort-Manager:** Aktiviert oder deaktiviert den Edge-Kennwort-Manager.
- **DNT-Kopfzeilen senden:** Konfiguriert den Edge-Browser zum Senden von DNT-Headern (Do Not Track, nicht nachverfolgen) an Websites, die Benutzer besuchen.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen für Microsoft Edge**: Aktivieren Sie Edge SmartScreen für den Zugriff auf Website- und Dateidownloads.

## <a name="search"></a>Suchen
- **Standortsuche:** Hiermit geben Sie an, ob bei der Suche der Standort verwendet werden kann. Informationen zu


## <a name="cloud-and-storage"></a>Cloud und Speicher
-   **Microsoft-Konto:** Erlaubt dem Benutzer, das Gerät einem Microsoft-Konto zuzuordnen.

## <a name="cellular-and-connectivity"></a>Mobilfunk und Konnektivität

-   **Bluetooth:** Steuert, ob der Benutzer Bluetooth auf dem Gerät aktivieren und konfigurieren kann.
-   **Bluetooth-Erkennbarkeit:** Ermöglicht die Erkennung dieses Geräts durch andere Bluetooth-Geräte.
-   **Bluetooth-Werbung:** Ermöglicht das Empfangen von Werbung per Bluetooth durch das Gerät.

## <a name="control-panel-and-settings"></a>Systemsteuerung und Einstellungen

- **Änderung der Systemzeit:** Verhindert, dass der Endbenutzer auf dem Gerät Datum und Uhrzeit ändert.

## <a name="reporting-and-telemetry"></a>Berichterstellung und Telemetrie

- **Nutzungsdaten freigeben**: Wählen Sie die Ebene der Diagnosedatenübermittlung.