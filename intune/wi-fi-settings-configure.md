---
title: Erstellen eines WLAN-Profils für Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein WLAN-Gerätekonfigurationsprofil in Microsoft Intune erstellen. Erstellen Sie Profile für Android, Android Enterprise, Android-Kiosk, iOS, macOS, Windows 10 und höher sowie Windows Holographic for Business. Verwenden Sie diese Profile, um beispielsweise eine WLAN-Verbindung zu erstellen, um Zertifikate zu verwenden, einen EAP-Typ und eine Authentifizierungsmethode auszuwählen oder einen Proxy zu aktivieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c780f68d3c332cec899250ea4a0ee85745247b37
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842438"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Hinzufügen und Verwenden von WLAN-Einstellungen auf Microsoft Intune-Geräten

WLAN ist ein drahtloses Netzwerk, das von vielen mobilen Geräten verwendet wird, um Zugriff auf das Netzwerk zu erhalten. Microsoft Intune umfasst integrierte WLAN-Einstellungen, die für Benutzer und Geräte in Ihrer Organisation bereitgestellt werden können. Diese Gruppe von Einstellungen wird als „Profil“ bezeichnet und kann verschiedenen Benutzern und Gruppen zugewiesen werden. Nach der Zuweisung können Ihre Benutzer Zugriff auf das WLAN Ihrer Organisation erhalten, ohne es selbst zu konfigurieren.

Angenommen, Sie installieren ein neues WLAN mit dem Namen „Contoso-WLAN“. Daraufhin möchten Sie alle iOS-Geräte so einrichten, dass sie sich mit diesem Netzwerk verbinden. Gehen Sie dazu folgendermaßen vor:

1. Erstellen Sie ein WLAN-Profil mit den Einstellungen zum Herstellen der Verbindung mit dem Drahtlosnetzwerk „Contoso-WLAN“.
2. Weisen Sie das Profil einer Gruppe zu, die alle iOS-Gerätebenutzer enthält.
3. Benutzer finden nun das neue WLAN von Contoso in der Liste der Drahtlosnetzwerke auf ihrem Gerät. Sie können sich dann über die von Ihnen ausgewählte Authentifizierungsmethode mit dem Netzwerk verbinden.

In diesem Artikel sind die Schritte zum Erstellen eines WLAN-Profils aufgelistet. Darüber hinaus enthält er Links, in denen die verschiedenen Einstellungen für die einzelnen Plattformen beschrieben werden.

## <a name="supported-device-platforms"></a>Unterstützte Geräteplattformen

WLAN-Profile unterstützen folgende Geräteplattformen:

- Android 4 und höher
- Android Enterprise und -Kiosk
- iOS 8.0 und höher
- macOS (Mac OS X 10.11 und höher)
- Windows 10 und höher, Windows 10 Mobile und Windows Holographic for Business

> [!NOTE]
> Auf Geräten mit Windows 8.1 können Sie eine WLAN-Konfiguration importieren, die zuvor von einem anderen Gerät exportiert wurde.

## <a name="create-a-device-profile"></a>Erstellen eines Geräteprofils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Microsoft Intune** aus. 
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie einen **Namen** und eine **Beschreibung** für das WLAN-Profil ein.
4. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform aus, auf die die WLAN-Einstellungen angewendet werden sollen. Folgende Optionen sind verfügbar:

    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
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

Das Profil ist nun erstellt. Die nächsten Schritte sind das [Zuweisen dieses Profils](device-profile-assign.md) und das [Überwachen seines Status](device-profile-monitor.md).
