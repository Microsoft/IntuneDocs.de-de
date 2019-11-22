---
title: Einstellungen für Windows Holographic for Business-Geräte – Microsoft Intune – Azure | Microsoft-Dokumentation
description: 'In diesem Artikel erhalten Sie Informationen zum Konfigurieren von Einstellungen zur Geräteeinschränkung in Microsoft Intune für Windows Holographic for Business. Die folgenden Aspekte werden behandelt: Aufhebung einer Registrierung, Geolocation, Kennwörter, Installieren von Apps aus dem App Store, Cookies und Popupmenüs in Microsoft Edge, Microsoft Defender, Suchen, Cloud und Speicher, Bluetooth-Verbindungen, Systemzeit und Nutzungsdaten in Azure.'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1f90a5a13859ff19765e22444a84b9c11405af73
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059506"
---
# <a name="windows-holographic-for-business-device-settings-to-allow-or-restrict-features-using-intune"></a>Windows Holographic for Business-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie für Windows Holographic for Business-Geräte steuern können, z.B. Microsoft Hololens. Als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) verwenden Sie diese Einstellungen, um Features zuzulassen oder zu deaktivieren, die Sicherheit zu steuern und mehr.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Profil für die Gerätekonfiguration.](device-restrictions-configure.md#create-the-profile)

## <a name="general"></a>Allgemein

- **Manuelle Aufhebung der Registrierung**: Erlaubt dem Benutzer das manuelle Löschen des Unternehmensbereichskontos vom Gerät.
- **Cortana**: Aktiviert oder deaktiviert den Cortana-Sprach-Assistenten.
- **Geolocation**: Gibt an, ob das Gerät Standortdienstinformationen verwenden kann.

## <a name="password"></a>Kennwort

- **Kennwort**: Der Endbenutzer muss ein Kennwort eingeben, um auf das Gerät zugreifen zu können.
- **Kennwort anfordern, wenn Gerät aus Leerlaufzustand zurückkehrt**: Gibt an, dass der Benutzer ein Kennwort zum Entsperren des Geräts eingeben muss.

## <a name="app-store"></a>App Store

- **Apps aus Store automatisch aktualisieren**: Ermöglicht die automatische Aktualisierung von Apps, die aus dem Microsoft Store installiert wurden.
- **Installation vertrauenswürdiger Apps**: Ermöglicht das Querladen von Apps, die mit einem vertrauenswürdigen Zertifikat signiert sind.
- **Entwicklersperre aufheben**: Ermöglicht dem Endbenutzer, Windows-Entwicklereinstellungen – z.B. das Zulassen quergeladener Apps – zu ändern.

## <a name="microsoft-edge-browser"></a>Microsoft Edge-Browser

- **Cookies**: Ermöglicht Browsern das Speichern von Internetcookies auf dem Gerät.
- **Popups**: Blockiert Popupfenster im Browser (gilt nur für Windows 10 Desktop).
- **Suchvorschläge**: Ermöglicht der Suchmaschine, während der Eingabe von Suchausdrücken Websites vorzuschlagen.
- **Kennwort-Manager**: Aktiviert oder deaktiviert die Funktion des Kennwort-Managers von Microsoft Edge.
- **DNT-Kopfzeilen senden**: Konfiguriert den Microsoft Edge-Browser für das Senden von DNT-Headern (Do Not Track, nicht verfolgen) an Websites, die Benutzer besuchen.

## <a name="microsoft-defender-smart-screen"></a>Microsoft Defender-SmartScreen

- **SmartScreen für Microsoft Edge**: Aktiviert SmartScreen für Microsoft Edge für den Zugriff auf Website- und Dateidownloads.

## <a name="search"></a>Suchen

- **Standortsuche:** Hiermit geben Sie an, ob bei der Suche der Standort verwendet werden kann. Informationen zu

## <a name="cloud-and-storage"></a>Cloud und Speicher

- **Microsoft-Konto**: Erlaubt dem Benutzer, das Gerät einem Microsoft-Konto zuzuordnen.

## <a name="cellular-and-connectivity"></a>Mobilfunk und Konnektivität

- **Bluetooth**: Steuert, ob der Benutzer Bluetooth auf dem Gerät aktivieren und konfigurieren kann.
- **Bluetooth-Erkennbarkeit**: Ermöglicht die Erkennung dieses Geräts durch andere Bluetooth-Geräte.
- **Bluetooth-Werbung**: Ermöglicht das Empfangen von Werbung per Bluetooth durch das Gerät.

## <a name="control-panel-and-settings"></a>Systemsteuerung und Einstellungen

- **Änderung der Systemzeit**: Verhindert, dass der Endbenutzer auf dem Gerät Datum und Uhrzeit ändert.

## <a name="kiosk---obsolete"></a>Kiosk – veraltet

Diese Einstellungen sind schreibgeschützt und können nicht verändert werden. Informationen zum Konfigurieren des Kioskmodus finden Sie unter [Kiosk settings (Kioskeinstellungen)](kiosk-settings-holographic.md).

Ein Kiosk-Gerät führt in der Regel eine spezifische App aus. Benutzer werden daran gehindert, auf Features oder Funktionen auf dem Gerät außerhalb von Kiosk-Apps zuzugreifen.

- **Kioskmodus**: Gibt den Typ des Kioskmodus an, der von der Richtlinie unterstützt wird. Zu den Optionen gehören:

  - **Nicht konfiguriert** (Standard): Die Richtlinie aktiviert keinen Kioskmodus. 
  - **Kiosk mit einzelner App**: Das Profil erlaubt dem Gerät, nur eine App auszuführen. Wenn sich der Benutzer anmeldet, wird eine bestimmte App gestartet. Dieser Modus hindert den Benutzer auch daran, neue Apps zu öffnen oder die App zu ändern, die ausgeführt wird.
  - **Kiosk mit mehreren Apps**: Das Profil ermöglicht dem Gerät, mehrere Apps auszuführen. Es sind nur die Apps, die Sie hinzufügen, für den Benutzer verfügbar. Der Vorteil eines Kiosks mit mehreren Apps oder eines Geräts mit festem Zweck ist eine leicht verständliche Benutzererfahrung für einzelne Personen, da sie nur auf die Apps zugreifen, die sie benötigen. Apps, die sie nicht benötigen, werden aus der Ansicht entfernt. 
  
    Wenn Sie einem Kiosk mit mehreren Apps Apps hinzufügen, fügen Sie auch eine Datei für das Layout des Startmenüs hinzu. Die [Datei für das Layout des Startmenüs](/hololens/hololens-kiosk#start-layout-file-for-mdm-intune-and-others) enthält XML-Beispiele, die in Intune verwendet werden können. 

### <a name="single-app-kiosks"></a>Kiosks für einzelne Apps

Legen Sie folgende Einstellungen fest:

- **Benutzerkonto**: Geben Sie das (auf das Gerät bezogene) lokale Benutzerkonto oder die Azure AD-Kontoanmeldung ein, das bzw. die der Kiosk-App zugeordnet ist. Geben Sie für Konten, die Mitglieder von Azure AD-Domänen sind, das Konto in der Form `domain\username@tenant.org` ein. 

    Für Kiosks in öffentlichen Umgebungen, für die die automatische Anmeldung aktiviert ist, muss ein Benutzertyp mit den geringsten Berechtigungen (z.B. das lokale Standardbenutzerkonto) verwendet werden. Verwenden Sie das `AzureAD\user@contoso.com`-Format, um ein Azure Active Directory-Konto (AD) für den Kioskmodus zu konfigurieren.

- **Anwendungsbenutzermodell-ID (AUMID) der App**: Geben Sie die AUMID der Kiosk-App ein. Weitere Informationen finden Sie unter [Find the Application User Model ID of an installed app (Ermitteln der Anwendungsbenutzer-ID einer installierten App)](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

## <a name="reporting-and-telemetry"></a>Berichterstellung und Telemetrie

- **Nutzungsdaten freigeben**: Wählen Sie die Ebene der Übermittlung von Diagnosedaten aus.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
