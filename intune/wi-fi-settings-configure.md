---
title: Erstellen eines WLAN-Profils für Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie ein WLAN-Gerätekonfigurationsprofil in Microsoft Intune erstellen. Erstellen Sie Profile für Android, Android Enterprise, Android-Kiosk, iOS, macOS, Windows 10 und höher sowie Windows Holographic for Business. Verwenden Sie diese Profile, um beispielsweise eine WLAN-Verbindung zu erstellen, um Zertifikate zu verwenden, einen EAP-Typ und eine Authentifizierungsmethode auszuwählen oder einen Proxy zu aktivieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 80e70db4b64770af1a96ee7f24a3cf875269adce
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71163490"
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
- macOS X 10.11 und neuer
- Windows 10 und höher, Windows 10 Mobile und Windows Holographic for Business

> [!NOTE]
> Auf Geräten mit Windows 8.1 können Sie eine WLAN-Konfiguration importieren, die zuvor von einem anderen Gerät exportiert wurde.

## <a name="create-a-device-profile"></a>Erstellen eines Geräteprofils

1. Wählen Sie in [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) **Gerätekonfiguration** > **Profile** > **Profil erstellen** aus.
2. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das Profil ein. Benennen Sie Ihre Profile, damit Sie diese später leicht wiedererkennen. Ein angemessener Profilname ist beispielsweise **WLAN-Profil für das gesamte Unternehmen**.
    - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie die Plattform Ihrer Geräte aus. Folgende Optionen sind verfügbar:

      - **Android**
      - **Android Enterprise**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows 8.1 und höher**
      - **Windows 10 und höher**

    - **Profiltyp**: Wählen Sie **WLAN** aus.

      > [!TIP]
      >
      > - Für **Android Enterprise**-Geräte, die als dedizierte Geräte (Kiosk) ausgeführt werden, wählen Sie **Nur Gerätebesitzer** > **WLAN** aus.
      > - Für **Windows 8.1 und höher** können Sie **WLAN (Import)** auswählen. Mit dieser Option können Sie WLAN-Einstellungen als XML-Datei importieren, die Sie zuvor von einem anderen Gerät exportiert haben.

3. Einige WLAN-Einstellungen unterscheiden sich je nach Plattform. Um die Einstellungen einer bestimmten Plattform anzuzeigen, wählen Sie Ihre Plattform aus:

    - [Android](wi-fi-settings-android.md)
    - [Android Enterprise](wi-fi-settings-android-enterprise.md), einschließlich dedizierter Geräte
    - [iOS/iPadOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 und höher](wi-fi-settings-windows.md)
    - [Windows 8.1 und höher](wi-fi-settings-import-windows-8-1.md) (einschließlich Windows Holographic for Business)

4. Wenn Sie fertig sind, wählen Sie **Profil erstellen** > **Erstellen** aus.

Das Profil wird erstellt und in der Profilliste angezeigt (**Gerätekonfiguration** > **Profile**).

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt. Die nächsten Schritte sind das [Zuweisen dieses Profils](device-profile-assign.md) und das [Überwachen seines Status](device-profile-monitor.md).
