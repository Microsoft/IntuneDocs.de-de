---
title: 'Verwenden von benutzerdefinierten Geräteeinstellungen in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Erstellen Sie ein Profil, oder fügen Sie ein Profil hinzu, um mithilfe von Microsoft Intune benutzerdefinierte Einstellungen für Geräte unter Windows Phone, Windows 8.1 Windows 10 und höher, Android, Android Enterprise, macOS und iOS zu verwenden.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1c815a2c911dba6d17fc864b446122931fa88e91
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73755382"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Erstellen eines Profils mit benutzerdefinierten Einstellungen in Intune

## <a name="what-are-custom-profiles"></a>Eigenschaften von benutzerdefinierten Profilen

Microsoft Intune umfasst einige integrierte Einstellungen zum Steuern verschiedener Features auf einem Gerät. Sie können auch benutzerdefinierte Profile erstellen. Benutzerdefinierte Profile eignen sich gut, wenn Sie Geräteeinstellungen und -features verwenden möchten, die nicht in Intune integriert sind. Diese Profile umfassen Features und Einstellungen, die Sie auf Geräten innerhalb Ihrer Organisation steuern können. Sie können beispielsweise ein benutzerdefiniertes Profil erstellen, das für alle iOS-Geräte ein bestimmtes Feature festlegt.

Weitere Informationen zu Konfigurationsprofilen finden Sie unter [Was sind Microsoft Intune-Geräteprofile?](device-profiles.md). 

Dieser Artikel umfasst Links zum Erstellen von benutzerdefinierten Profilen für Android, Android Enterprise, iOS, macOS und Windows.

## <a name="available-platforms"></a>Verfügbare Plattformen

Benutzerdefinierte Einstellungen werden für jede Plattform anders konfiguriert. Bei Android- und Windows-Geräten können Sie beispielsweise OMA-URI-Werte (Open Mobile Alliance Uniform Resource Identifier) zum Steuern von Features auf Geräten eingeben. Sie können für Apple-Geräte eine Datei importieren, die Sie mit [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) oder dem [Apple-Profil-Manager](https://support.apple.com/profile-manager) erstellt haben.

Benutzerdefinierte Profile werden auf ähnliche Weise wie integrierte Profile erstellt und sind auf den folgenden Plattformen verfügbar:

- [Android](../custom-settings-android.md)
- [Android Enterprise](../custom-settings-android-for-work.md)
- [iOS/iPadOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)

## <a name="next-steps"></a>Nächste Schritte

Wählen Sie Ihre Plattform aus, und legen Sie los:

- [Android](../custom-settings-android.md)
- [Android Enterprise](../custom-settings-android-for-work.md)
- [iOS/iPadOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
