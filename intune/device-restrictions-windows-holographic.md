---
title: Geräteeinschränkungen für Windows Holographic for Business-Geräte in Microsoft Intune Azure | Microsoft-Dokumentation
description: 'In diesem Artikel erhalten Sie Informationen zum Konfigurieren von Einstellungen zur Geräteeinschränkung in Microsoft Intune für Windows Holographic for Business. Die folgenden Aspekte werden behandelt: Aufhebung einer Registrierung, Geolocation, Kennwörter, Installieren von Apps aus dem App Store, Cookies und Popupmenüs in Edge, Windows Defender, Suchen, Cloud und Speicher, Bluetooth-Verbindungen, Systemzeit und Benutzerdaten in Azure.'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/9/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5b0784aeb1dc1022b4be824c2f858f9525d03918
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="device-restriction-settings-for-windows-holographic-for-business-in-intune"></a>Einstellungen für Geräteeinschränkungen für Windows Holographic for Business in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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

## <a name="kiosk-preview"></a>Kiosk (Vorschauversion)

Ein Kiosk-Gerät führt in der Regel eine spezifische App aus. Benutzer werden daran gehindert, auf Features oder Funktionen auf dem Gerät außerhalb von Kiosk-Apps zuzugreifen.

- **Kioskmodus**: Ermittelt den Typ des Kioskmodus, der von der Richtlinie unterstützt wird. Zu den Optionen gehören:

  - **Nicht konfiguriert**: (Standard). Die Richtlinie aktiviert keinen Kioskmodus. 
  - **Kiosk mit einzelner App**: Das Profil erlaubt dem Gerät, nur eine App auszuführen. Wenn sich der Benutzer anmeldet, wird eine bestimmte App gestartet. Dieser Modus hindert den Benutzer auch daran, neue Apps zu öffnen oder die App zu ändern, die ausgeführt wird.

#### <a name="single-app-kiosks"></a>Kiosks für einzelne Apps
Legen Sie folgende Einstellungen fest:

- **Benutzerkonto**: Geben Sie das (auf das Gerät bezogene) lokale Benutzerkonto oder die Azure AD-Kontoanmeldung ein, das bzw. die der Kiosk-App zugeordnet ist. Geben Sie für Konten, die Mitglieder von Azure AD-Domänen sind, das Konto in der Form `domain\username@tenant.org` ein. 

    Für Kiosks in öffentlichen Umgebungen, für die die automatische Anmeldung aktiviert ist, muss ein Benutzertyp mit den geringsten Berechtigungen (z.B. das lokale Standardbenutzerkonto) verwendet werden. Verwenden Sie das `AzureAD\user@contoso.com`-Format, um ein Azure Active Directory-Konto (AD) für den Kioskmodus zu konfigurieren.

- **Anwendungsbenutzermodell-ID (AUMID) der App**: Geben Sie die AUMID der Kiosk-App ein. Weitere Informationen finden Sie unter [Find the Application User Model ID of an installed app (Ermitteln der Anwendungsbenutzer-ID einer installierten App)](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

## <a name="reporting-and-telemetry"></a>Berichterstellung und Telemetrie

- **Nutzungsdaten freigeben**: Wählen Sie die Ebene der Diagnosedatenübermittlung.