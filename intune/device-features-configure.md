---
title: Erstellen von iOS- oder macOS-Geräteprofilen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie in Microsoft Intune ein iOS- oder macOS-Geräteprofil, oder fügen Sie ein solches Profil hinzu. Konfigurieren Sie dann Einstellungen für AirPrint, das Layout des Startbildschirms, App-Benachrichtigungen, freigegebene Geräte, einmaliges Anmelden und Webinhaltsfilter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5ae03a4155fa2d170648548bb9a08b570f49c673
ms.sourcegitcommit: 25e17a1d002ee1faa49bb89648eb59373528539f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "59566619"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Hinzufügen von Einstellungen für iOS- oder macOS-Gerätefunktionen in Intune

Intune umfasst zahlreiche Funktionen und Einstellungen, mit denen Administratoren iOS- und macOS-Geräte steuern können. Administratoren können z.B.:

- Benutzern den Zugriff auf AirPrint-Drucker in Ihrem Netzwerk ermöglichen
- Apps und Ordner dem Startbildschirm hinzufügen, einschließlich Hinzufügen von neuen Seiten
- Wählen, ob und wie App-Benachrichtigungen angezeigt werden
- Den Sperrbildschirm so konfigurieren, dass eine Nachricht oder das Bestandskennzeichen angezeigt wird, insbesondere für gemeinsam genutzte Geräte
- Benutzern sicheres einmaliges Anmelden ermöglichen, um Anmeldeinformationen zwischen Apps freizugeben
- Websites herausfiltern, die nicht jugendfreie Sprache verwenden, und bestimmte Websites zulassen oder blockieren

Diese Features sind in Intune verfügbar und werden vom Administrator konfiguriert. Intune verwendet „Konfigurationsprofile“ zum Erstellen und Anpassen dieser Einstellungen für die Anforderungen Ihrer Organisation. Nachdem Sie diese Features in einem Profil hinzugefügt haben, können Sie das Profil auf iOS- und macOS-Geräte in Ihrer Organisation übertragen oder für sie bereitstellen.

In diesem Artikel erfahren Sie, wie Sie ein Gerätekonfigurationsprofil erstellen. Sie können auch alle verfügbaren Einstellungen für [iOS](ios-device-features-settings.md)- und [macOS](macos-device-features-settings.md)-Geräte sehen.

## <a name="create-a-device-profile"></a>Erstellen eines Geräteprofils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
    - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie Ihre Plattform aus:
        - **iOS**
        - **macOS**
    - **Profiltyp**: Wählen Sie **Gerätefunktionen** aus.
    - **Einstellungen:** Geben Sie die Einstellungen ein, die Sie konfigurieren möchten. Eine Liste aller Einstellungen und ihrer Funktionen finden Sie unter:

        - [iOS](ios-device-features-settings.md)
        - [macOS](macos-device-features-settings.md)

4. Wenn Sie fertig sind, klicken Sie auf **OK** und dann auf **Erstellen**, um Ihre Änderungen zu speichern.

Das Profil wird erstellt und in der Liste angezeigt. Denken Sie daran, das [Profil zuzuweisen](device-profile-assign.md) und [seinen Status zu überwachen](device-profile-monitor.md).

## <a name="next-steps"></a>Nächste Schritte

Nachdem das Profil erstellt wurde, kann es zugewiesen werden. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).

Zeigen Sie alle Einstellungen für Gerätefunktionen für [iOS](ios-device-features-settings.md)- und [macOS](macos-device-features-settings.md)-Geräte an.
