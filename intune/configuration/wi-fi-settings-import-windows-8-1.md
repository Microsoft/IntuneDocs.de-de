---
title: 'Importieren von WLAN-Einstellungen für Windows-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Exportieren Sie WLAN-Einstellungen als XML-Datei von einem Windows-Gerät mithilfe von „netsh wlan“. Importieren Sie anschließend diese Datei in Intune, um ein WLAN-Profil für Geräte zu erstellen, auf denen Windows 8.1, Windows 10 oder Windows Holographic for Business ausgeführt wird.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/18/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40569af35a812074cc62546e3f85929416202b3b
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506429"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Importieren von WLAN-Einstellungen für Windows-Geräte in Intune

Für Geräte, die Windows ausführen, können Sie ein WLAN-Konfigurationsprofil aus einer zuvor exportierten Datei importieren. **Für Geräte, auf denen Windows 10 und höher ausgeführt wird, können Sie auch direkt in Intune [ein WLAN-Profil erstellen](wi-fi-settings-windows.md)** .

Gilt für:  
- Windows 8.1 und höher
- Windows 10 und höher
- Windows 10 Desktop oder Mobile
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportieren von WLAN-Einstellungen von einem Windows-Gerät

Verwenden Sie unter Windows `netsh wlan`, um ein vorhandenes WLAN-Profil in eine XML-Datei zu exportieren, die von Intune gelesen werden kann. Der Schlüssel muss in Nur-Text exportiert werden, damit das Profil erfolgreich verwendet werden kann.

Führen Sie auf einem Windows-Computer, auf dem das erforderliche WLAN-Profil bereits installiert ist, die folgenden Schritte aus:

1. Erstellen Sie einen lokalen Ordner für die exportierten WLAN-Profile, z.B. **C:\WiFi**.
2. Öffnen Sie eine Eingabeaufforderung als Administrator.
3. Führen Sie den Befehl `netsh wlan show profiles` aus, und notieren Sie sich den Namen des Profils, das Sie exportieren möchten. In diesem Beispiel lautet der Profilname **WiFiName**.
4. Führen Sie den Befehl `netsh wlan export profile name="ProfileName" folder=c:\Wifi` aus. Dieser Befehl erstellt eine WLAN-Profildatei mit dem Namen **Wi-Fi-WiFiName.xml** im Zielordner.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importieren der WLAN-Einstellungen in Intune

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie einen **Namen** und eine **Beschreibung** für das Geräteeinschränkungsprofil ein.

    > [!IMPORTANT]
    > - Der Name **muss** mit dem Namensattribut in der WLAN-Profil-XML-Datei identisch sein. Andernfalls tritt ein Fehler auf.
    > - Wenn Sie ein WLAN-Profil mit einem vorinstallierten Schlüssel exportieren, **müssen** Sie `key=clear` zu dem Befehl hinzufügen. Geben Sie beispielsweise `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi` ein.
    > - Die Verwendung eines vorinstallierten Schlüssels mit Windows 10 verursacht einen Wartungsfehler in Intune. In diesem Fall wird das WLAN-Profil ordnungsgemäß dem Gerät zugewiesen, und das Profil funktioniert wie erwartet.
    > - Vergewissern Sie sich, dass die Datei geschützt ist, wenn Sie ein WLAN-Profil exportieren, das einen vorinstallierten Schlüssel enthält. Der Schlüssel wird in Nur-Text angegeben. Daher sind Sie für die Sicherheit des Schlüssels verantwortlich.

4. Klicken Sie unter **Plattform** auf **Windows 8.1 und höher**.
5. Klicken Sie unter **Profiltyp** auf **Wi-Fi import** (WLAN-Import).
6. Konfigurieren Sie die folgenden Einstellungen:
    - **Verbindungsname**: Geben Sie einen Namen für diese Verbindung ein. Dieser Name wird beim Durchsuchen der verfügbaren WLAN-Netzwerke für Endbenutzer angezeigt.
    - **Profil-XML**: Wählen Sie die Schaltfläche „Durchsuchen“ und die XML-Datei mit den WLAN-Profileinstellungen aus, die Sie importieren möchten.
    - **Dateiinhalt:** Zeigt den XML-Code des ausgewählte Konfigurationsprofils an.
7. Wenn Sie fertig sind, wählen Sie **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern. Das Profil wird erstellt und in der Profilliste angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt. [Weisen Sie dieses Profil nun zu.](device-profile-assign.md)

## <a name="more-resources"></a>Weitere Ressourcen

[Übersicht über WLAN-Einstellungen](wi-fi-settings-configure.md) auf unterschiedlichen Plattformen
