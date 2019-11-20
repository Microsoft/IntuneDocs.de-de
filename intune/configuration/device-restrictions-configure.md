---
title: Einschränkung der Gerätefeatures durch Richtlinien in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hinzufügen eines Geräteprofils zum Einschränken von Funktionen auf Android-, macOS-, iOS-, iPadOS-, Windows Phone- und Windows 10-Geräten in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 704da2ee4f0f2e6dce222c89704c83a35368c02c
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059542"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Konfigurieren von Einstellungen für Geräteeinschränkungen in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune enthält Richtlinien zur Geräteeinschränkung, die Administratoren bei der Steuerung von Android-, iOS-, macOS- und Windows-Geräten unterstützen. Mit diesen Einschränkungen können Sie eine Vielzahl von Einstellungen und Features steuern, um die Ressourcen Ihres Unternehmens zu schützen. Administratoren können z.B.:

- Die Kamera des Geräts zulassen, oder sie blockieren
- Den Zugriff auf Google Play, App-Stores, das Anzeigen von Dokumenten und Spiele steuern.
- integrierte Apps blockieren oder eine Liste von Apps erstellen, die zugelassen oder nicht zugelassen werden.
- das Speichern von Dateien in Cloud- oder Speicherkonten erlauben oder verhindern.
- Eine minimale Kennwortlänge einstellen und einfache Kennwörter blockieren

Diese Features sind in Intune verfügbar und werden vom Administrator konfiguriert. Intune verwendet „Konfigurationsprofile“ zum Erstellen und Anpassen dieser Einstellungen für die Anforderungen Ihrer Organisation. Nachdem Sie diese Features in einem Profil hinzugefügt haben, können Sie das Profil anschließend auf Geräte in Ihrer Organisation pushen oder bereitstellen.

In diesem Artikel erfahren Sie, wie Sie ein Geräteeinschränkungsprofil erstellen. Sie können auch alle verfügbaren Einstellungen für die verschiedenen Plattformen anzeigen.

## <a name="create-the-profile"></a>Erstellen des Profils

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für die Richtlinie ein. Benennen Sie Ihre Richtlinien so, dass Sie diese später leicht wiedererkennen. Ein guter Richtlinienname ist beispielsweise **iOS: Kamera auf Geräten blockieren**.
    - **Beschreibung**: Geben Sie eine Beschreibung für die Richtlinie ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie die Plattform Ihrer Geräte aus. Folgende Optionen sind verfügbar:  

        - **Android**
        - **Android Enterprise**
        - **iOS/iPadOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 und höher**
        - **Windows 10 und höher**

    - **Profiltyp**: Wählen Sie **Geräteeinschränkungen** aus.

        Um ein Geräteeinschränkungsprofil für Windows 10 Team-Geräte wie etwa ein Surface Hub zu erstellen, wählen Sie **Geräteeinschränkungen (Windows 10 Team)** aus.

4. Die konfigurierbaren Einstellungen variieren je nach der ausgewählten Plattform. Wählen Sie Ihre Plattform für detaillierte Einstellungen aus:

    - [Einstellungen für Android](../device-restrictions-android.md)
    - [Android-Einstellungen für Unternehmen](../device-restrictions-android-for-work.md)
    - [iOS/iPadOS-Einstellungen](device-restrictions-ios.md)
    - [Einstellungen für macOS](device-restrictions-macos.md)
    - [Einstellungen für Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Einstellungen für Windows 10](device-restrictions-windows-10.md)
    - [Einstellungen für Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Einstellungen für Windows Holographic for Business](device-restrictions-windows-holographic.md)

5. Wenn Sie fertig sind, wählen Sie **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern.

Das Profil wird erstellt und in der Profilliste angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Nachdem das Profil erstellt wurde, kann es zugewiesen werden. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](../device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](../device-profile-monitor.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/device-restrictions-configure/disable-android-camera.png)

-->
