---
title: Einstellungen für Windows Holographic for Business-Geräte – Microsoft Intune – Azure | Microsoft-Dokumentation
description: 'In diesem Artikel erhalten Sie Informationen zum Konfigurieren von Einstellungen zur Geräteeinschränkung in Microsoft Intune für Windows Holographic for Business. Die folgenden Aspekte werden behandelt: Aufhebung einer Registrierung, Geolocation, Kennwörter, Installieren von Apps aus dem App Store, Cookies und Pop-up-Menüs in Microsoft Edge, Windows Defender, Suchen, Cloud und Speicher, Bluetooth-Verbindungen, Systemzeit und Benutzerdaten in Azure.'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 477b8a0c9b4cdb575988524cea1f73615254baec
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838477"
---
# <a name="windows-holographic-for-business-device-settings-to-allow-or-restrict-features-using-intune"></a>Windows Holographic for Business-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie für Windows Holographic for Business-Geräte steuern können, z.B. Microsoft Hololens. Als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) verwenden Sie diese Einstellungen, um Features zuzulassen oder zu deaktivieren, die Sicherheit zu steuern und mehr.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Profil für die Gerätekonfiguration.](device-restrictions-configure.md#create-the-profile)

## <a name="general"></a>Allgemein

- **Manuelles Aufheben der Registrierung**: Ermöglicht dem Benutzer das manuelle Löschen des Unternehmensbereichskontos vom Gerät.
- **Cortana**: Aktivieren oder deaktivieren Sie den Cortana-Sprach-Assistenten.
- **Geolocation**: Gibt an, ob das Gerät Ortungsdienstinformationen verwenden kann.

## <a name="password"></a>Kennwort

- **Kennwort**: Der Endbenutzer muss ein Passwort eingeben, um auf das Gerät zugreifen zu können.
- **Kennwort anfordern, wenn das Gerät aus Leerlaufzustand zurückkehrt**: Gibt an, dass der Benutzer ein Kennwort zum Entsperren des Geräts eingeben muss.

## <a name="app-store"></a>App Store

- **Apps aus Store automatisch aktualisieren**: Apps aus dem Microsoft Store können automatisch aktualisiert werden.
- **Installation vertrauenswürdiger Apps**: Ermöglicht das Querladen von Apps, die mit einem vertrauenswürdigen Zertifikat signiert sind.
- **Entwicklersperre aufheben**: Ermöglicht dem Endbenutzer, Windows-Entwicklereinstellungen – z.B. das Zulassen quergeladener Apps – zu ändern.

## <a name="microsoft-edge-browser"></a>Microsoft Edge-Browser

- **Cookies**: Erlaubt Browsern das Speichern von Internetcookies auf dem Gerät.
- **Popups**: Blockiert Popupfenster im Browser (gilt nur für Windows 10 Desktop).
- **Suchvorschläge**: Ermöglicht der Such-Engine, Websites während der Eingabe von Suchausdrücken vorzuschlagen.
- **Kennwort-Manager**: Aktiviert oder deaktiviert den Kennwort-Manager von Microsoft Edge.
- **DNT-Kopfzeilen senden**: Konfiguriert den Microsoft Edge-Browser zum Senden von DNT-Kopfzeilen (Do Not Track, nicht nachverfolgen) an Websites, die Benutzer besuchen.

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen für Microsoft Edge**: Hiermit wird Edge SmartScreen für den Zugriff auf Website- und Dateidownloads aktiviert.

## <a name="search"></a>Suchen

- **Standortsuche:** Hiermit geben Sie an, ob bei der Suche der Standort verwendet werden kann. Informationen zu

## <a name="cloud-and-storage"></a>Cloud und Speicher

- **Microsoft-Konto**: Ermöglicht dem Benutzer, das Gerät einem Microsoft-Konto zuzuordnen.

## <a name="cellular-and-connectivity"></a>Mobilfunk und Konnektivität

- **Bluetooth**: Steuert, ob der Benutzer Bluetooth auf dem Gerät aktivieren und konfigurieren kann.
- **Bluetooth-Erkennbarkeit**: Ermöglicht die Erkennung dieses Geräts durch andere Bluetooth-Geräte.
- **Bluetooth-Ankündigung**: Ermöglicht Geräten den Empfang von Ankündigungen über Bluetooth.

## <a name="control-panel-and-settings"></a>Systemsteuerung und Einstellungen

- **Änderung der Systemzeit**: hindert Benutzer daran, die Systemzeit auf dem Gerät zu ändern.

## <a name="kiosk---obsolete"></a>Kiosk – veraltet

Diese Einstellungen sind schreibgeschützt und können nicht verändert werden. Informationen zum Konfigurieren des Kioskmodus finden Sie unter [Kiosk settings (Kioskeinstellungen)](kiosk-settings-holographic.md).

Ein Kiosk-Gerät führt in der Regel eine spezifische App aus. Benutzer werden daran gehindert, auf Features oder Funktionen auf dem Gerät außerhalb von Kiosk-Apps zuzugreifen.

- **Kioskmodus**: Gibt den Typ des Kioskmodus an, der von der Richtlinie unterstützt wird. Zu den Optionen gehören:

  - **Nicht konfiguriert** (Standardeinstellung): Die Richtlinie aktiviert keinen Kioskmodus. 
  - **Kiosk mit einzelner App**: Das Profil erlaubt dem Gerät die Ausführung von nur einer App. Wenn sich der Benutzer anmeldet, wird eine bestimmte App gestartet. Dieser Modus hindert den Benutzer auch daran, neue Apps zu öffnen oder die App zu ändern, die ausgeführt wird.
  - **Kiosk mit mehreren Apps**: Das Profil erlaubt dem Gerät, mehrere Apps auszuführen. Es sind nur die Apps, die Sie hinzufügen, für den Benutzer verfügbar. Der Vorteil eines Kiosks mit mehreren Apps oder eines Geräts mit festem Zweck ist eine leicht verständliche Benutzererfahrung für einzelne Personen, da sie nur auf die Apps zugreifen, die sie benötigen. Apps, die sie nicht benötigen, werden aus der Ansicht entfernt. 
  
    Wenn Sie einem Kiosk mit mehreren Apps Apps hinzufügen, fügen Sie auch eine Datei für das Layout des Startmenüs hinzu. Die [Datei für das Layout des Startmenüs](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-file-for-intune) enthält XML-Beispiele, die in Intune verwendet werden können. 

#### <a name="single-app-kiosks"></a>Kiosks für einzelne Apps

Legen Sie folgende Einstellungen fest:

- **Benutzerkonto**: Geben Sie das (auf das Gerät bezogene) lokale Benutzerkonto oder die Azure AD-Kontoanmeldung ein, das bzw. die der Kiosk-App zugeordnet ist. Geben Sie für Konten, die Mitglieder von Azure AD-Domänen sind, das Konto in der Form `domain\username@tenant.org` ein. 

    Für Kiosks in öffentlichen Umgebungen, für die die automatische Anmeldung aktiviert ist, muss ein Benutzertyp mit den geringsten Berechtigungen (z.B. das lokale Standardbenutzerkonto) verwendet werden. Verwenden Sie das `AzureAD\user@contoso.com`-Format, um ein Azure Active Directory-Konto (AD) für den Kioskmodus zu konfigurieren.

- **Anwendungsbenutzermodell-ID (AUMID) der App**: Geben Sie die AUMID der Kiosk-App ein. Weitere Informationen finden Sie unter [Find the Application User Model ID of an installed app (Ermitteln der Anwendungsbenutzer-ID einer installierten App)](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

## <a name="reporting-and-telemetry"></a>Berichterstellung und Telemetrie

- **Nutzungsdaten freigeben**: Wählen Sie die Ebene der Diagnosedatenübermittlung.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
