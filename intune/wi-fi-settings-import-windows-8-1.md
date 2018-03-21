---
title: "Importieren von WLAN-Einstellungen für Windows 8.1 und höher"
titleSuffix: Microsoft Intune
description: Importieren von WLAN-Einstellungen von Windows in ein Intune-WLAN-Profil.
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 890a10ecf4212656c189adaf46bb2839898758c1
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>Importieren von WLAN-Einstellungen für Geräte mit Windows 8.1 und höher in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Für Geräte mit Windows 8.1, Windows 10 (Desktop oder Mobile) oder Windows Holographic for Business können Sie ein WLAN-Konfigurationsprofil importieren, das zuvor in eine Datei exportiert wurde.

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportieren von WLAN-Einstellungen von einem Windows-Gerät

In Windows können Sie WLAN-Profile mit dem Hilfsprogramm **netsh wlan** in eine XML-Datei exportieren, die von Intune gelesen werden kann. Führen Sie auf einem Windows-Computer, auf dem das erforderliche WLAN-Profil bereits installiert ist, das folgende Verfahren aus.
1. Erstellen Sie einen lokalen Ordner für die exportierten WLAN-Profile, z.B. **C:\WiFi**.
1. Öffnen Sie eine Eingabeaufforderung als Administrator.
1. Führen Sie den Befehl **netsh wlan show profiles** aus, und notieren Sie den Namen des Profils, das Sie exportieren möchten. In diesem Beispiel lautet der Profilname **WiFiName**.
1. Führen Sie diesen Befehl aus: **netsh wlan export profile name="Profilname" folder=c:\Wifi**. Dadurch wird eine WLAN-Profildatei namens **Wi-Fi-WiFiName.xml** im Zielordner erstellt.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importieren der WLAN-Einstellungen in Intune

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie im Bereich **Intune** die Option **Gerätekonfiguration** aus.
4. Klicken Sie im Bereich **Gerätekonfiguration** im Abschnitt **Verwalten** auf **Profile**.
5. Klicken Sie im Bereich „Profile“ auf **Profil erstellen**.
6. Geben Sie im Bereich **Profil erstellen** einen **Namen** und eine **Beschreibung** für das Geräteeinschränkungsprofil ein.


   > [!WARNING]
   > Der Name **muss** mit dem Namensattribut in der WLAN-Profil-XML-Datei identisch sein, andernfalls tritt ein Fehler auf.

7. Wählen Sie in der Dropdownliste **Plattform** die Option **Windows 8.1 und höher** aus.
8. Wählen Sie in der Dropdownliste **Profiltyp** die Option **WLAN (Import)** aus.
9. Konfigurieren Sie im Bereich **WLAN** folgende Einstellungen:
    - **Verbindungsname:** Geben Sie den Namen der WLAN-Verbindung ein. Dieser Name wird beim Durchsuchen der verfügbaren WLAN-Netzwerke für Endbenutzer angezeigt.
    - **Profil-XML:** Klicken Sie auf die Schaltfläche „Durchsuchen“, und wählen Sie die XML-Datei mit den WLAN-Profileinstellungen aus, die Sie in Intune importieren möchten.
    - **Dateiinhalt:** Zeigt den XML-Code des ausgewählte Konfigurationsprofils an.
10. Klicken Sie anschließend auf **OK**, navigieren Sie wieder zum Bereich **Profil erstellen**, und klicken Sie auf **Erstellen**.

Das Profil wird erstellt und im Bereich „Profilliste“ angezeigt.
