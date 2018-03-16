---
title: "Konfigurieren der Einstellungen für Gerätefeatures in Microsoft Intune"
titleSuffix: 
description: "Erfahren Sie, wie Sie mit Microsoft Intune Features auf von Ihnen verwalteten Geräten konfigurieren können."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6cd646976deb1599c4cbc9154b6f2a487029dd79
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
#<a name="configure-device-feature-settings-in-microsoft-intune"></a>Konfigurieren der Einstellungen für Gerätefeatures in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Mit Gerätefunktionen können Sie Funktionen auf iOS- und macOS-Geräten wie AirPrint, Benachrichtigungen und freigegebene Gerätekonfigurationen steuern.

Anhand der Informationen in diesem Artikel lernen Sie die Grundlagen zum Konfigurieren von Gerätefeatureprofilen kennen. In den weiterführenden Artikeln zu den einzelnen Plattformen erfahren Sie etwas über die Besonderheiten der jeweiligen Geräte.

## <a name="create-a-device-profile-containing-device-feature-settings"></a>Erstellen eines Geräteprofils mit Einstellungen für Gerätefeatures

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie auf der Seite **Intune** die Option **Gerätekonfiguration** aus.
2. Wählen Sie auf der Seite **Gerätekonfiguration** im Abschnitt **Verwalten** die Option **Profile** aus.
3. Klicken Sie auf der Seite „Profile“ auf **Profil erstellen**.
4. Geben Sie auf der Seite **Profil erstellen** einen **Namen** und eine **Beschreibung** für das Gerätefeatureprofil ein.
5. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform aus, auf die Sie die Einstellungen anwenden möchten. Derzeit können Sie eine der folgenden Plattformen für Gerätefunktionen auswählen:
    - **iOS**
    - **macOS**
6. Wählen Sie in der Dropdownliste **Profiltyp** die Option **Gerätefunktionen** aus. 
7. Die konfigurierbaren Einstellungen variieren je nach der ausgewählten Plattform. In den folgenden Artikeln finden Sie ausführliche Informationen zu den Einstellungen für die einzelnen Plattformen:
    - [AirPrint settings for iOS and MacOS](air-print-settings-ios-macos.md) (AirPrint-Einstellungen für iOS- und macOS-Geräte)
    - [AirPlay settings for iOS](airplay-settings-ios.md) (AirPlay-Einstellungen für iOS-Geräte)
    - [Home screen layout settings for iOS](home-screen-settings-ios.md) (Einstellungen des Startbildschirmlayouts für iOS-Geräte)
    - [App notification settings for iOS](app-notification-settings-ios.md) (App-Benachrichtigungseinstellungen für iOS-Geräte)
    - [Shared device configuration settings for iOS](shared-device-settings-ios.md) (Konfigurationseinstellungen für freigegebene iOS-Geräte)
    - [Konfigurieren von Intune für einmaliges Anmelden von iOS-Geräten](sso-ios.md)
    - [Web content filter settings for iOS](web-content-filter-settings-ios.md) (Filtereinstellungen für Webinhalte für iOS-Geräte)

8. Wählen Sie anschließend **OK** aus, navigieren Sie wieder zur Seite **Profil erstellen** und wählen Sie **Erstellen** aus.

Das Profil wird erstellt und auf der Seite mit der Profilliste angezeigt.
## <a name="next-steps"></a>Nächste Schritte

Wenn Sie dieses Profil Gruppen zuweisen möchten, finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md) weitere Informationen.



