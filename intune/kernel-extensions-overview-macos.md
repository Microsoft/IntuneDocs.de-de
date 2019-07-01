---
title: Erstellen Sie MacOS-Geräteprofil für Kernel-Erweiterungen mit Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Fügen Sie hinzu oder erstellen Sie ein MacOS-Geräteprofil, und dann die konfigurieren Sie Kernelerweiterungen Außerkraftsetzung durch Benutzer zulassen möchten, Hinzufügen von Team-ID und ein Paket und Team-ID in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd2e03c09cb2bed49ee7607283bf63e2c3ae67da
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403905"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Hinzufügen von Erweiterungen für MacOS-Kernel in Intune

Auf MacOS-Geräten können Sie auf der Ebene der Kernel Features hinzufügen. Diese Funktionen zuzugreifen, Teile des Betriebssystems, die nicht auf normale Programme zugreifen können. Ihre Organisation möglicherweise Anforderungen oder Anforderungen, die nicht in eine app, eine Funktion zur usw. zur Verfügung stehen. 

Fügen Sie zum Hinzufügen von Kernelerweiterungen, die immer zulässig sind, um auf Ihren Geräten zu laden, "Kernel-Extensions" (Kernel-Extension) in Microsoft Intune, und klicken Sie dann diese Erweiterungen auf Ihren Geräten bereitstellen.

Beispielsweise müssen Sie ein Antivirenprogramm, die das Gerät auf schädlichen Inhalt überprüft. Sie können diese virenprüfung Kernel-Erweiterung des Programms als eine zulässige Kernel-Erweiterung in Intune hinzufügen. Klicken Sie dann "weisen Sie zu" die Erweiterung auf Ihrem MacOS-Geräte.

Mit diesem Feature können Administratoren Benutzer außer Kraft setzen Kernelerweiterungen, Hinzufügen von Team-IDs und bestimmte Kernel-Erweiterungen in Intune hinzufügen.

Diese Funktion gilt für:

- macOS 10.13.2 und höher

Um dieses Feature verwenden zu können, müssen Geräte sein:

- In Intune mithilfe des Apple Device Enrollment Program (DEP) registriert. [Automatisches Registrieren von MacOS-Geräten](device-enrollment-program-enroll-macos.md) finden Sie weitere Informationen.

  ODER

- Bei Intune registriert sind, mit "Registrierung Benutzer genehmigt" (Apple Begriff). [Vorbereiten für Änderungen an den Kernelerweiterungen in MacOS High Sierra](https://support.apple.com/en-us/HT208019) (öffnet die Apple-Website) finden Sie weitere Informationen.

Intune verwendet „Konfigurationsprofile“ zum Erstellen und Anpassen dieser Einstellungen für die Anforderungen Ihrer Organisation. Nachdem Sie diese Features in einem Profil hinzugefügt haben, können Sie das Profil auf macOS-Geräte in Ihrer Organisation übertragen oder für sie bereitstellen.

In diesem Artikel veranschaulicht das Erstellen eines gerätekonfigurationsprofils, die mithilfe von Kernelerweiterungen in Intune.

> [!TIP]
> Weitere Informationen zu Kernelerweiterungen finden Sie unter [Kernel-Erweiterung (Übersicht)](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (öffnet die Apple-Website).

## <a name="what-you-need-to-know"></a>Was Sie wissen müssen

- Nicht signierte älteren Kernelerweiterungen können hinzugefügt werden.
- Achten Sie darauf, geben die richtige Team-ID und die Paket-ID der Kernel-Erweiterung. Intune nicht die Werte zu überprüfen, die Sie eingeben. Wenn Sie falsche Informationen eingeben, funktioniert die Erweiterung nicht auf dem Gerät.

> [!NOTE]
> Apple hat Informationen zu signieren und Nachweis für die gesamte Software veröffentlicht. Unter MacOS 10.14.5 und höher, Kernel, die Erweiterungen, die über Intune bereitgestellt werden müssen keine Apple Nachweis Richtlinie erfüllt.
>
> Informationen zu dieser Richtlinie Nachweis und alle Updates oder Änderungen finden Sie unter den folgenden Ressourcen:
>
>  - [Ihre app vor der Verteilung notarizing](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (öffnet die Apple-Website) 
>  - [Vorbereiten für Änderungen an den Kernelerweiterungen in MacOS High Sierra](https://support.apple.com/en-us/HT208019) (öffnet die Apple-Website)

## <a name="create-the-profile"></a>Erstellen des Profils

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie **macOS** aus.
    - **Profiltyp**: Wählen Sie **Erweiterungen**.
    - **Einstellungen**: Geben Sie die Einstellungen ein, die Sie konfigurieren möchten. Eine Liste aller Einstellungen und ihrer Funktionen finden Sie unter:

        - [macOS](kernel-extensions-settings-macos.md)

4. Wenn Sie fertig sind, wählen Sie **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern.

Das Profil wird erstellt und in der Liste angezeigt. Denken Sie daran, das [Profil zuzuweisen](device-profile-assign.md) und [seinen Status zu überwachen](device-profile-monitor.md).

## <a name="next-steps"></a>Nächste Schritte

Nachdem das Profil erstellt wurde, kann es zugewiesen werden. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).
