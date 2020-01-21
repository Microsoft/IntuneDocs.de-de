---
title: 'Importieren von WLAN-Einstellungen für Windows-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Exportieren Sie WLAN-Einstellungen als XML-Datei von einem Windows-Gerät mithilfe von „netsh wlan“. Importieren Sie anschließend diese Datei in Intune, um ein WLAN-Profil für Geräte zu erstellen, auf denen Windows 8.1, Windows 10 oder Windows Holographic for Business ausgeführt wird.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f79ccdc71ddbfa3f25daef629515fb612de01852
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207008"
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

1. Erstellen Sie einen lokalen Ordner für die exportierten WLAN-Profile, z. B. **C:\WiFi**.
2. Öffnen Sie eine Eingabeaufforderung als Administrator.
3. Führen Sie den Befehl `netsh wlan show profiles` aus. Notieren Sie den Namen des Profils, das Sie exportieren möchten. In diesem Beispiel lautet der Profilname **WiFiName**.
4. Führen Sie den Befehl `netsh wlan export profile name="ProfileName" folder=c:\Wifi` aus. Dieser Befehl erstellt eine WLAN-Profildatei mit dem Namen **Wi-Fi-WiFiName.xml** im Zielordner.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importieren der WLAN-Einstellungen in Intune

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.
3. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen aussagekräftigen Namen für das Profil ein. Der Name **muss** mit dem Namensattribut in der WLAN-Profil-XML-Datei identisch sein. Andernfalls tritt ein Fehler auf.
    - **Beschreibung:** Geben Sie eine Beschreibung ein, die einen Überblick über die Einstellung und andere wichtige Details bietet.
    - **Plattform**: Wählen Sie **Windows 8.1 und höher** aus.
    - **Profiltyp**: Wählen Sie **WLAN-Import** aus.

    > [!IMPORTANT]
    > - Wenn Sie ein WLAN-Profil mit einem vorinstallierten Schlüssel exportieren, **müssen** Sie `key=clear` zu dem Befehl hinzufügen. Geben Sie beispielsweise `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi` ein.
    > - Die Verwendung eines vorinstallierten Schlüssels mit Windows 10 verursacht einen Wartungsfehler in Intune. In diesem Fall wird das WLAN-Profil ordnungsgemäß dem Gerät zugewiesen, und das Profil funktioniert wie erwartet.
    > - Vergewissern Sie sich, dass die Datei geschützt ist, wenn Sie ein WLAN-Profil exportieren, das einen vorinstallierten Schlüssel enthält. Der Schlüssel wird in Nur-Text angegeben. Daher sind Sie für die Sicherheit des Schlüssels verantwortlich.

4. Legen Sie folgende Einstellungen fest:

    - **Verbindungsname:** Geben Sie einen Namen für die WLAN-Verbindung ein. Dieser Name wird Benutzern angezeigt, wenn Sie verfügbare Wi-Fi-Netzwerke durchsuchen.
    - **Profil-XML**: Wählen Sie die Schaltfläche „Durchsuchen“ und die XML-Datei mit den WLAN-Profileinstellungen aus, die Sie importieren möchten.
    - **Dateiinhalte**: Zeigt den XML-Code des ausgewählten Konfigurationsprofils an.

5. Klicken Sie auf **OK**, um die Änderungen zu speichern.
6. Klicken Sie anschließend auf **OK** > **Erstellen**, um das Intune-Profil zu erstellen. Das Profil wird erstellt und in der Liste **Gerätekonfiguration > Konfigurationsprofile** angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](../device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).

Weitere Informationen, auch zu anderen Plattformen, finden Sie in der [Übersicht über WLAN-Einstellungen](wi-fi-settings-configure.md).
