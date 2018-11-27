---
title: Erstellen von iOS- oder macOS-Geräteprofilen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie in Microsoft Intune ein iOS- oder macOS-Geräteprofil, oder fügen Sie ein solches Profil hinzu. Konfigurieren Sie dann Einstellungen für AirPrint, AirPlay, das Layout des Startbildschirms, App-Benachrichtigungen, freigegebene Geräte, einmaliges Anmelden und Webinhaltsfilter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 65457a65504b633018bb61851f16c8c65fa1c806
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185677"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Hinzufügen von Einstellungen für iOS- oder macOS-Gerätefunktionen in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Mit Gerätefunktionen können Sie verschiedene Einstellungen und Features auf iOS- und macOS-Geräten steuern, wie z.B. diese:

- AirPrint- und AirPlay-Einstellungen
- Layout des Startbildschirms
- Benachrichtigungen von Apps
- Konfiguration für freigegebene Geräte
- Einrichten des einmaligen Anmeldens
- Filtern von Webinhalten

Dieser Artikel erläutert die Grundlagen der Konfiguration von Profilen für iOS-Gerätefunktionen. Danach können Sie weitere Artikel lesen, um plattformspezifische Einstellungen für Ihre Geräte zu konfigurieren.

## <a name="create-a-device-profile"></a>Erstellen eines Geräteprofils

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
4. Geben Sie die folgenden Eigenschaften ein:

   - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
   - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. (Optional, jedoch empfohlen)
   - **Plattform:** Wählen Sie den Plattformtyp aus:
     - **iOS**
     - **macOS**
   - **Profiltyp:** Wählen Sie **Gerätefunktionen** aus.
   - **Einstellungen**: Die Einstellungen richten sich nach der ausgewählten Plattform. Die folgenden Artikel beschreiben die Einstellungen für die einzelnen Profiltypen:

     - [AirPrint settings for iOS and MacOS](air-print-settings-ios-macos.md) (AirPrint-Einstellungen für iOS- und macOS-Geräte)
     - [AirPlay settings for iOS](airplay-settings-ios.md) (AirPlay-Einstellungen für iOS-Geräte)
     - [Home screen layout settings for iOS](home-screen-settings-ios.md) (Einstellungen des Startbildschirmlayouts für iOS-Geräte)
     - [App notification settings for iOS](app-notification-settings-ios.md) (App-Benachrichtigungseinstellungen für iOS-Geräte)
     - [Shared device configuration settings for iOS](shared-device-settings-ios.md) (Konfigurationseinstellungen für freigegebene iOS-Geräte)
     - [Konfigurieren von Intune für einmaliges Anmelden von iOS-Geräten](sso-ios.md)
     - [Web content filter settings for iOS](web-content-filter-settings-ios.md) (Filtereinstellungen für Webinhalte für iOS-Geräte)

5. Wenn Sie fertig sind, klicken Sie auf **OK** und dann auf **Erstellen**, um Ihre Änderungen zu speichern.

Das Profil wird erstellt und in der Liste angezeigt.

## <a name="next-step"></a>Nächster Schritt

Informationen zum Zuweisen dieses Profils an Gruppen finden Sie unter [Zuweisen von Microsoft Intune-Geräteprofilen](device-profile-assign.md).