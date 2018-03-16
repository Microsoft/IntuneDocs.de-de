---
title: "Konfigurieren von Einstellungen für Geräteeinschränkungen in Microsoft Intune"
titleSuffix: 
description: "In diesem Artikel erfahren Sie, wie Sie mit Microsoft Intune Einstellungen und Features auf Geräten, die Sie verwalten, konfigurieren."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c5ccb928b8ff3f9cebbd6f51d99cddd1f36fb074
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-configure-device-restriction-settings-in-microsoft-intune"></a>So konfigurieren Sie Einstellungen für Geräteeinschränkungen in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Mit Geräteeinschränkungen können Sie eine Vielzahl von Einstellungen und Features für eine ganze Reihe von Kategorien steuern, z.B.:
- Sicherheit
- Browser
- Hardware
- Einstellungen für die Datenfreigabe

Sie können beispielsweise ein Geräteeinschränkungsprofil erstellen, das verhindert, dass Benutzer von iOS-Geräten auf die Kamera des Geräts zugreifen.

Sie lernen die Grundlagen der Geräteeinschränkungsprofile und lesen weitere Artikel zu den Besonderheiten der Geräte auf jeder Plattform.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Erstellen von Geräteprofilen mit Einstellungen für Geräteeinschränkungen

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie auf der Seite **Intune** die Option **Gerätekonfiguration** aus.
2. Wählen Sie auf der Seite **Gerätekonfiguration** im Abschnitt **Verwalten** **Profile** aus.
3. Wählen Sie auf der Seite **Profile** **Profil erstellen** aus.
4. Geben Sie auf der Seite **Profil erstellen** einen **Namen** und eine **Beschreibung** für das Geräteeinschränkungsprofil ein.
5. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform aus, auf die Sie benutzerdefinierte Einstellungen anwenden möchten. Derzeit können Sie eine der folgenden Plattformen für die Einstellungen für Geräteeinschränkungen auswählen:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 und höher**
    - **Windows 10 und höher**
6. Wählen Sie in der Dropdownliste **Profiltyp** die Option **Geräteeinschränkungen** aus. Wenn Sie ein Geräteeinschränkungsprofil für Windows 10 Team-Geräte wie etwa ein Surface Hub erstellen möchten, wählen Sie **Geräteeinschränkungen (Windows 10 Team)** aus.
7. Die konfigurierbaren Einstellungen variieren je nach der ausgewählten Plattform. In den folgenden Themen finden Sie ausführliche Informationen zu den Einstellungen für die einzelnen Plattformen:
    - [Einstellungen für Android](device-restrictions-android.md)
    - [Einstellungen für iOS](device-restrictions-ios.md)
    - [Einstellungen für macOS](device-restrictions-macos.md)
    - [Einstellungen für Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Einstellungen für Windows 10](device-restrictions-windows-10.md)
    - [Einstellungen für Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Einstellungen für Windows Holographic for Business](device-restrictions-windows-holographic.md)
    - [Einstellungen für Android for Work](device-restrictions-android-for-work.md)
8. Navigieren Sie anschließend zurück zur Seite **Profil erstellen**, und klicken Sie auf **Erstellen**.

Das Profil wird erstellt und auf der Seite mit der Profilliste angezeigt.
Wenn Sie fortfahren und dieses Profil Gruppen zuweisen möchten, lesen Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md) nach.

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
