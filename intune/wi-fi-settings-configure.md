---
title: Erstellen eines WLAN-Profils für Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein WLAN-Gerätekonfigurationsprofil in Microsoft Intune erstellen. Erstellen Sie Profile für Android, Android Enterprise, Android-Kiosk, iOS, macOS, Windows 10 und höher sowie Windows Holographic for Business. Verwenden Sie diese Profile, um beispielsweise eine WLAN-Verbindung zu erstellen, um Zertifikate zu verwenden, einen EAP-Typ und eine Authentifizierungsmethode auszuwählen oder einen Proxy zu aktivieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a338cce6249cc7c5214a9d69a897cad3eaa09e93
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188397"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Hinzufügen und Verwenden von WLAN-Einstellungen auf Microsoft Intune-Geräten

Verwenden Sie WLAN-Profile in Microsoft Intune, um Benutzern und Geräten in Ihrer Organisation Einstellungen für Drahtlosnetzwerke zuzuweisen. Wenn Sie ein WLAN-Profil zuweisen, können Ihre Benutzer auf das WLAN Ihrer Organisation zugreifen, ohne es selbst zu konfigurieren.

Angenommen, Sie installieren ein neues WLAN mit dem Namen „Contoso-WLAN“. Daraufhin möchten Sie alle iOS-Geräte so einrichten, dass sie sich mit diesem Netzwerk verbinden. Gehen Sie dazu folgendermaßen vor:

1. Erstellen Sie ein WLAN-Profil mit den Einstellungen zum Verbinden mit dem Drahtlosnetzwerk „Contoso-WLAN“.
2. Weisen Sie das Profil einer Gruppe zu, die alle iOS-Gerätebenutzer enthält.
3. Benutzer finden nun das neue WLAN von Contoso in der Liste der Drahtlosnetzwerke auf ihrem Gerät. Sie können sich dann über die von Ihnen ausgewählte Authentifizierungsmethode mit dem Netzwerk verbinden.

Verwenden Sie die Schritte in diesem Artikel, um ein WLAN-Profil zu erstellen. Lesen Sie dann die Themen zu den plattformspezifischen Einstellungen und die Details.

## <a name="supported-device-platforms"></a>Unterstützte Geräteplattformen

WLAN-Profile unterstützen folgende Geräteplattformen:

- Android 4 und höher
- Android Enterprise und -Kiosk
- iOS 8.0 und höher
- macOS (Mac OS X 10.11 und höher)
- Windows 10 und höher, Windows 10 Mobile und Windows Holographic for Business

> [!NOTE]
> Auf Geräten mit Windows 8.1 können Sie eine WLAN-Konfiguration importieren, die zuvor von einem anderen Gerät exportiert wurde.

## <a name="create-a-wi-fi-device-profile"></a>Erstellen eines WLAN-Geräteprofils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Microsoft Intune** aus. 
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie einen **Namen** und eine **Beschreibung** für das WLAN-Profil ein.
4. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform aus, auf die die WLAN-Einstellungen angewendet werden sollen. Folgende Optionen sind verfügbar:

    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 und höher**
    - **Windows 10 und höher**

5. Wählen Sie unter **Profiltyp** **WLAN** aus.

    - Für **Android Enterprise**-Geräte, die als Kiosk ausgeführt werden, ist die Option **Nur Gerätebesitzer** > **WLAN** verfügbar.
    - Für **Windows 8.1 und höher** können Sie **WLAN (Import)** auswählen. Mit dieser Option können Sie WLAN-Einstellungen als XML-Datei importieren, die Sie zuvor von einem anderen Gerät exportiert haben.

6. Einige WLAN-Einstellungen unterscheiden sich je nach Plattform. Klicken Sie auf die jeweilige Plattform, um die entsprechenden Einstellungen anzuzeigen:

    - [Android](wi-fi-settings-android.md)
    - [Android Enterprise und -Kiosk](wi-fi-settings-android-enterprise.md)
    - [iOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 und höher](wi-fi-settings-windows.md)
    - [Windows 8.1 und höher](wi-fi-settings-import-windows-8-1.md) (einschließlich Windows Holographic for Business)

    Die meisten Plattformen verfügen über **grundlegende** Einstellungen und Einstellungen für **Unternehmen**. **Grundlegende Einstellungen** umfassen Funktionen wie den Netzwerknamen und die SSID. Mit **Einstellungen für Unternehmen** können Sie weitere Informationen angeben, z.B. das Extensible Authentication Protocol (EAP).

7. Wenn Sie Ihre WLAN-Einstellungen hinzugefügt haben, wählen Sie **Profil erstellen** > **Erstellen** aus, um das Konfigurationsprofil hinzuzufügen. Das Profil wird erstellt und in der Profilliste angezeigt (**Gerätekonfiguration** > **Profile**).

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt. [Weisen Sie dieses Profil nun zu.](device-profile-assign.md)
