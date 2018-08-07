---
title: 'Importieren von WLAN-Einstellungen für Windows-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Exportieren Sie WLAN-Einstellungen als XML-Datei von einem Windows-Gerät mithilfe von „netsh wlan“. Importieren Sie anschließend diese Datei in Intune, um ein WLAN-Profil für Geräte zu erstellen, auf denen Windows 8.1, Windows 10 oder Windows Holographic for Business ausgeführt wird.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6ce5cdd9509ed3407491714ccfa853613eb43973
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321134"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Importieren von WLAN-Einstellungen für Windows-Geräte in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Für Geräte, die Windows ausführen, können Sie ein WLAN-Konfigurationsprofil aus einer zuvor exportierten Datei importieren. **Für Geräte, auf denen Windows 10 und höher ausgeführt wird, können Sie direkt in Intune [ein WLAN-Profil erstellen](wi-fi-settings-windows.md)**.

Gilt für:  
- Windows 8.1 und höher
- Windows 10 und höher
- Windows 10 Desktop oder Mobile
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportieren von WLAN-Einstellungen von einem Windows-Gerät

In Windows können Sie WLAN-Profile mit **netsh wlan** in eine XML-Datei exportieren, die von Intune gelesen werden kann. Der Schlüssel muss in Nur-Text exportiert werden, damit das Profil erfolgreich verwendet werden kann.

Führen Sie auf einem Windows-Computer, auf dem das erforderliche WLAN-Profil bereits installiert ist, die folgenden Schritte aus:

1. Erstellen Sie einen lokalen Ordner für die exportierten WLAN-Profile, z.B. **C:\WiFi**.
2. Öffnen Sie eine Eingabeaufforderung als Administrator.
3. Führen Sie den Befehl `netsh wlan show profiles` aus, und notieren Sie sich den Namen des Profils, das Sie exportieren möchten. In diesem Beispiel lautet der Profilname **WiFiName**.
4. Führen Sie den Befehl `netsh wlan export profile name="ProfileName" folder=c:\Wifi` aus. Dadurch wird im Zielordner ein WLAN-Profil mit dem Namen **Wi-Fi-WiFiName.xml** erstellt.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importieren der WLAN-Einstellungen in Intune

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
4. Geben Sie einen **Namen** und eine **Beschreibung** für das Geräteeinschränkungsprofil ein.

    > [!IMPORTANT]
    > - Der Name **muss** mit dem Namensattribut in der WLAN-Profil-XML-Datei identisch sein. Andernfalls tritt ein Fehler auf.
    > - Wenn Sie ein WLAN-Profil mit einem vorinstallierten Schlüssel exportieren, **müssen** Sie `key=clear` zu dem Befehl hinzufügen. Geben Sie beispielsweise `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi` ein.
    > - Die Verwendung eines vorinstallierten Schlüssels mit Windows 10 verursacht einen Wartungsfehler in Intune. In diesem Fall wird das WLAN-Profil ordnungsgemäß dem Gerät zugewiesen, und das Profil funktioniert wie erwartet.
    > - Vergewissern Sie sich, dass die Datei geschützt ist, wenn Sie ein WLAN-Profil exportieren, das einen vorinstallierten Schlüssel enthält. Der Schlüssel wird in Nur-Text angegeben. Daher sind Sie für die Sicherheit des Schlüssels verantwortlich.

5. Klicken Sie unter **Plattform** auf **Windows 8.1 und höher**.
6. Klicken Sie unter **Profiltyp** auf **Wi-Fi import** (WLAN-Import).
7. Konfigurieren Sie die folgenden Einstellungen:
  - **Verbindungsname**: Geben Sie einen Namen für diese Verbindung ein. Dieser Name wird beim Durchsuchen der verfügbaren WLAN-Netzwerke für Endbenutzer angezeigt.
  - **Profil-XML**: Klicken Sie auf die Schaltfläche „Durchsuchen“, und wählen Sie die XML-Datei mit den WLAN-Profileinstellungen aus, die Sie in Intune importieren möchten.
  - **Dateiinhalt:** Zeigt den XML-Code des ausgewählte Konfigurationsprofils an.
8. Wenn Sie fertig sind, klicken Sie auf **OK**, und **erstellen** Sie das Profil.

Das Profil wird erstellt und in der Profilliste aufgeführt.
