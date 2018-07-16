---
title: 'Verwenden von benutzerdefinierten Geräteeinstellungen in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Hinzufügen oder Erstellen von Profilen zur Verwendung von benutzerdefinierten Einstellungen für Windows-, Android- und iOS-Geräte unter Verwendung von Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d917d2449e75b89db00d453b72940a93efb03321
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905001"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Erstellen eines Profils mit benutzerdefinierten Einstellungen in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Möglicherweise sind nicht alle Einstellungen in Intune integriert, die Sie verwenden wollen oder müssen. Alternativ sollten Sie eine Einstellung verwenden, die für andere Geräteprofile verfügbar ist. Wenn Sie diese Einstellungen verwenden möchten, erstellen Sie ein Geräteprofil, und konfigurieren Sie das Profil mit benutzerdefinierten Einstellungen.

In diesem Artikel werden die grundlegenden Schritte zum Erstellen eines Profils mit benutzerdefinierten Einstellungen aufgeführt. Außerdem werden Links zu Artikeln bereitgestellt, in denen detaillierter erläutert wird, wie Sie benutzerdefinierte Einstellungen für die verschiedenen Plattformen erstellen können.

## <a name="custom-settings-on-different-platforms"></a>Benutzerdefinierte Einstellungen für verschiedene Plattformen
Benutzerdefinierte Einstellungen werden für jede Plattform anders konfiguriert. Bei Android- und Windows-Geräten können Sie beispielsweise OMA-URI-Werte (Open Mobile Alliance Uniform Resource Identifier) zum Steuern von Features auf Geräten eingeben. Auf Apple-Geräten können Sie eine Datei importieren, die Sie mit [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) erstellt haben.

## <a name="create-the-profile"></a>Erstellen des Profils

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf die Option **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
4. Geben Sie einen **Namen** und eine **Beschreibung** für das benutzerdefinierte Profil an.
5. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform aus, auf die benutzerdefinierte Einstellungen angewendet werden sollen. Sie können eine der folgenden Plattformen verwenden:

    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 und höher**
    - **Windows 10 und höher**

6. Wählen Sie in der Dropdownliste **Profiltyp** die Option **Benutzerdefiniert** aus.
7. Die konfigurierbaren Einstellungen variieren je nach ausgewählter Plattform. Unter den folgenden Links finden Sie nähere Details zu benutzerdefinierten Einstellungen für die jeweiligen Plattformen:

    - [Einstellungen für Android](custom-settings-android.md)
    - [Einstellungen für iOS](custom-settings-ios.md)
    - [Einstellungen für macOS](custom-settings-macos.md)
    - [Einstellungen für Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
    - [Einstellungen für Windows 10](custom-settings-windows-10.md)
    - [Einstellungen für Windows Holographic for Business](custom-settings-windows-holographic.md)
    - [Android-Arbeitsprofileinstellungen](custom-settings-android-for-work.md)

8. Wenn Sie fertig sind, klicken Sie auf **Erstellen**.

Das Profil wird erstellt und in der Profilliste angezeigt. Informationen zum Zuweisen dieses Profils an Gruppen finden Sie unter [Zuweisen von Microsoft Intune-Geräteprofilen](device-profile-assign.md).
