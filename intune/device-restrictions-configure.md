---
title: Intune-Einstellungen für Geräteeinschränkungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hinzufügen eines Geräteprofils zum Einschränken von Features unter Android-, macOS-, iOS-, Windows Phone- und Windows 10-Geräten in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 11b241a14ed70a2e999fa505449cd12cdd1e025e
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728785"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Konfigurieren von Einstellungen für Geräteeinschränkungen in Microsoft Intune

Mit Geräteeinschränkungen können Sie eine Vielzahl von Einstellungen und Features für eine ganze Reihe von Kategorien steuern, z.B.:
- Sicherheit
- Browser
- Hardware
- Einstellungen für die Datenfreigabe

Sie können beispielsweise ein Geräteeinschränkungsprofil erstellen, das verhindert, dass Benutzer von iOS-Geräten auf die Kamera des Geräts zugreifen.

Sie lernen die Grundlagen der Geräteeinschränkungsprofile und lesen weitere Artikel zu den Besonderheiten der Geräte auf jeder Plattform.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Erstellen von Geräteprofilen mit Einstellungen für Geräteeinschränkungen

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie einen **Namen** und eine **Beschreibung** für das Geräteeinschränkungsprofil ein.
4. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform aus, auf die Sie benutzerdefinierte Einstellungen anwenden möchten. Derzeit können Sie eine der folgenden Plattformen für die Einstellungen für Geräteeinschränkungen auswählen:

    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 und höher**
    - **Windows 10 und höher**

5. Wählen Sie in der Dropdownliste **Profiltyp** die Option **Geräteeinschränkungen** aus. Um ein Geräteeinschränkungsprofil für Windows 10 Team-Geräte wie etwa ein Surface Hub zu erstellen, wählen Sie **Geräteeinschränkungen (Windows 10 Team)** aus.
6. Die konfigurierbaren Einstellungen variieren je nach der ausgewählten Plattform. Wählen Sie detaillierte Einstellungen für Ihre Plattform aus:

    - [Einstellungen für Android](device-restrictions-android.md)
    - [Android-Einstellungen für Unternehmen](device-restrictions-android-for-work.md)
    - [Einstellungen für iOS](device-restrictions-ios.md)
    - [Einstellungen für macOS](device-restrictions-macos.md)
    - [Einstellungen für Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Einstellungen für Windows 10](device-restrictions-windows-10.md)
    - [Einstellungen für Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Einstellungen für Windows Holographic for Business](device-restrictions-windows-holographic.md)

7. Wechseln Sie anschließend wieder zur Seite **Profil erstellen**, und klicken Sie auf **Erstellen**.

Das Profil wird erstellt und auf der Seite mit der Profilliste angezeigt. 

## <a name="next-step"></a>Nächster Schritt

Nachdem das Profil erstellt wurde, kann es zugewiesen werden. Eine exemplarische Vorgehensweise finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md). 

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
