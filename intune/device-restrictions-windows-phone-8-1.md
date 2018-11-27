---
title: Einstellungen für Geräteeinschränkungen für Windows Phone 8.1 in Microsoft Intune
titleSuffix: ''
description: In diesem Artikel erhalten Sie Informationen zu den Intune-Einstellungen zur Steuerung von Geräteeinstellungen und -funktionen auf Windows Phone 8.1-Geräten.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 28f9891e953bf420e608993cea39ff81b98cb5e0
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185167"
---
# <a name="microsoft-intune-windows-phone-81-device-restriction-settings"></a>Einstellungen für Geräteeinschränkungen für Windows Phone 8.1 in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel erhalten Sie Informationen zu den Einstellungen für Microsoft Intune-Geräteeinschränkungen, die Sie für Windows Phone 8.1-Geräte konfigurieren können.


## <a name="general"></a>Allgemein

-   **Kamera:** Erlaubt oder sperrt die Verwendung der Kamera des Geräts.
-   **Kopieren und einfügen:** Lässt Kopier- und Einfügefunktionen auf Geräten zu oder sperrt diese Funktionen.
-   **Wechselmedien:** Erlaubt dem Gerät, Wechselmedien wie SD-Karten zu verwenden.
-   **Geolocation:** Erlaubt dem Gerät die Nutzung von Standortinformationen.
-   **Microsoft-Konto:** Erlaubt oder sperrt das Verknüpfen des Geräts mit einem Microsoft-Konto durch den Benutzer.
-   **Bildschirmaufnahme:** Erlaubt dem Benutzer, den Bildschirminhalt als Bilddatei zu erfassen.
-   **Übermittlung von Diagnosedaten:** Ermöglicht dem Gerät die Übermittlung von Diagnoseinformationen an Microsoft.
-   **Synchronisierung benutzerdefinierter E-Mail-Konten:** Ermöglicht dem Gerät das Herstellen einer Verbindung mit nicht von Microsoft stammenden E-Mail-Konten.

## <a name="password"></a>Kennwort

-   **Kennwort:** Der Endbenutzer muss ein Kennwort eingeben, um auf das Gerät zugreifen zu können.
    -   **Erforderlicher Kennworttyp:** Gibt den erforderlichen Typ des Kennworts an, z.B. alphanumerisch oder nur numerisch.
    -   **Minimale Kennwortlänge:** Gibt die Mindestanzahl von Zeichen an, die das Kennwort enthalten muss.
    -   **Einfache Kennwörter:** Gibt an, dass einfache Kennwörter, wie z.B: „0000“ und „1234“ verwendet werden können.
    -   **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird:** Gibt an, wie häufig ein falsches Kennwort eingegeben werden kann, bevor das Gerät zurückgesetzt wird.
    -   **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung:** Gibt die Zeitdauer der Inaktivität für ein Gerät an, bevor der Bildschirm automatisch gesperrt wird.
    -   **Kennwortablauf (Tage):** Gibt die Anzahl der Tage an, bevor das Gerätekennwort geändert werden muss.
    -   **Wiederverwendung vorheriger Kennwörter verhindern:** Gibt an, wie viele zuvor verwendete Kennwörter gespeichert werden.
-   **Verschlüsselung:** Schreibt vor, dass die Daten auf unterstützten mobilen Geräten verschlüsselt werden müssen.

## <a name="app-store"></a>App Store

-   **App-Store:** Erlaubt Benutzern, über das Gerät eine Verbindung mit dem App Store herzustellen.

## <a name="restricted-apps"></a>Eingeschränkte Apps

In der Liste der eingeschränkten Apps können Sie eine der folgenden Listen konfigurieren:

**Blockierte Apps:** Listet die (nicht von Intune verwalteten) Apps auf, die Benutzer nicht installieren und ausführen dürfen.
**Zulässige Apps:** Listet die Apps auf, die Benutzer installieren dürfen. Apps, die von Intune verwaltet werden, sind automatisch zugelassen.

Klicken Sie zum Konfigurieren einer Liste auf **Hinzufügen**. Geben Sie einen Namen Ihrer Wahl sowie die URL zur App im App-Store und optional den Herausgeber der App an.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Angeben der URL zu einer App im Store

Verwenden Sie das folgende Format, um eine App-URL in der Liste zulässiger und blockierter Apps anzugeben:

Suchen Sie im [Windows Phone Store](https://www.microsoft.com/store/apps/windows-phone) nach der App, die Sie verwenden möchten.

Öffnen Sie die Seite der App, und kopieren Sie die URL in die Zwischenablage. Sie können diese URL nun in der Liste kompatibler oder nicht kompatibler Apps verwenden.

Beispiel: Durchsuchen Sie den Store nach der Skype-App. Verwenden Sie dazu die URL `http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51`.



### <a name="additional-options"></a>Zusätzliche Optionen

Sie können auch auf **Importieren** klicken, um die Liste mithilfe einer CSV-Datei im Format <*App-URL*>, <*App-Name*>, <app publisher> aufzufüllen. Sie können stattdessen aber auch auf **Exportieren** klicken, um eine CSV-Datei mit dem Inhalt der Liste der eingeschränkten Apps im gleichen Format zu erstellen.


## <a name="browser"></a>Browser

-   **Webbrowser:** Erlaubt oder sperrt die Verwendung des integrierten Webbrowsers auf Geräten.

## <a name="cellular-and-connectivity"></a>Mobilfunk und Konnektivität

-   **WLAN:** Aktiviert oder deaktiviert die WLAN-Funktionalität des Geräts.
-   **WLAN-Tethering:** Erlaubt die Verwendung des WLAN-Tetherings auf dem Gerät.
-   **Automatische Verbindung mit WLAN-Hotspots herstellen:** Erlaubt, dass das Gerät automatisch eine Verbindung mit unverschlüsselten WLAN-Hotspots herstellen und die Geschäftsbedingungen für die Verbindung automatisch akzeptieren kann.
-   **WLAN-Hotspotmeldung:** Sendet Informationen über WLAN-Verbindungen, um nahegelegene Verbindungen zu ermitteln.
-   **NFC:** Aktiviert oder deaktiviert Vorgänge, die NFC (Near Field Communication, Nahfeldkommunikation) verwenden, sofern dies vom Gerät unterstützt wird.
-   **Bluetooth:** Aktiviert oder deaktiviert die Bluetooth-Funktionalität des Geräts.
