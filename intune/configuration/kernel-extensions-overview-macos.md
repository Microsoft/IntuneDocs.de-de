---
title: Erstellen von macOS-Kernel Erweiterungen Geräte Profil mit Microsoft InTune-Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Fügen Sie ein macOS-Geräte Profil hinzu, oder erstellen Sie es, und konfigurieren Sie dann die Kernel Erweiterungen, um die außer Kraft Setzung von Benutzern, das Hinzufügen von Team Bezeichnern und ein Bündel Microsoft InTune und
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
ms.openlocfilehash: 9832089cf73405a9e39795b076e9ead84bc7d7cd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734452"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Hinzufügen von macOS-Kernel Erweiterungen in InTune

Auf macOS-Geräten können Sie Features auf Kernel Ebene hinzufügen. Diese Features greifen auf Teile des Betriebssystems zu, auf die reguläre Programme nicht zugreifen können. Ihre Organisation hat möglicherweise bestimmte Anforderungen oder Anforderungen, die in einer APP, einem Geräte Feature usw. nicht verfügbar sind. 

Fügen Sie zum Hinzufügen von Kernel Erweiterungen, die immer auf Ihren Geräten geladen werden dürfen, in Microsoft InTune "Kernel Erweiterungen" (kext) hinzu, und stellen Sie diese Erweiterungen dann auf Ihren Geräten bereit.

Angenommen, Sie verfügen über ein Programm zum Überprüfen von Viren, das Ihr Gerät auf schädlichen Inhalt scannt. Sie können die Kernel Erweiterung dieses Virus Scan Programms als zulässige Kernel Erweiterung in InTune hinzufügen. Anschließend können Sie die Erweiterung den macOS-Geräten zuweisen.

Mit dieser Funktion können Administratoren es Benutzern ermöglichen, Kernel Erweiterungen außer Kraft zu setzen, Team-IDs hinzuzufügen und bestimmte Kernel Erweiterungen in InTune hinzuzufügen.

Diese Funktion gilt für:

- macOS 10.13.2 und höher

Um dieses Feature verwenden zu können, müssen die Geräte wie folgt lauten:

- In InTune registriert mithilfe von Apple Programm zur Geräteregistrierung (DEP). Weitere Informationen finden Sie unter [Automatisches Registrieren von macOS-Geräten](../enrollment/device-enrollment-program-enroll-macos.md) .

  ODER

- Registriert bei InTune mit "Benutzer genehmigter Registrierung" (Apple-Laufzeit). Weitere Informationen finden [Sie unter Vorbereiten auf Änderungen an Kernel Erweiterungen in macOS High Sierra](https://support.apple.com/en-us/HT208019) (öffnet die Website von Apple).

Intune verwendet „Konfigurationsprofile“ zum Erstellen und Anpassen dieser Einstellungen für die Anforderungen Ihrer Organisation. Nachdem Sie diese Features in einem Profil hinzugefügt haben, können Sie das Profil auf macOS-Geräte in Ihrer Organisation übertragen oder für sie bereitstellen.

In diesem Artikel erfahren Sie, wie Sie ein Geräte Konfigurations Profil mithilfe von Kernel Erweiterungen in InTune erstellen.

> [!TIP]
> Weitere Informationen zu Kernel Erweiterungen finden Sie unter [Übersicht über die Kernel Erweiterung](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (öffnet die Website von Apple).

## <a name="what-you-need-to-know"></a>Was Sie wissen müssen

- Nicht signierte Legacy-Kernel Erweiterungen können hinzugefügt werden.
- Stellen Sie sicher, dass Sie die richtige Team-ID und Bündel-ID der Kernel Erweiterung eingeben. InTune überprüft die eingegebenen Werte nicht. Wenn Sie falsche Informationen eingeben, funktioniert die Erweiterung auf dem Gerät nicht.

> [!NOTE]
> Apple hat Informationen über Signierung und Notarisierung für die gesamte Software veröffentlicht. Unter macOS 10.14.5 und höher müssen Kernel Erweiterungen, die über InTune bereitgestellt werden, die notalisierungsrichtlinie von Apple nicht erfüllen.
>
> Informationen zu dieser notariations Richtlinie sowie zu allen Updates oder Änderungen finden Sie in den folgenden Ressourcen:
>
> - [Notariierung der APP vor der Verteilung](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (öffnet die Website von Apple) 
> - [Vorbereiten auf Änderungen an Kernel Erweiterungen in macOS High Sierra](https://support.apple.com/en-us/HT208019) (öffnet die Website von Apple)

## <a name="create-the-profile"></a>Erstellen des Profils

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie **macOS** aus.
    - **Profiltyp**: Wählen Sie **Erweiterungen**aus.
    - **Einstellungen**: Geben Sie die Einstellungen ein, die Sie konfigurieren möchten. Eine Liste aller Einstellungen und ihrer Funktionen finden Sie unter:

        - [macOS](kernel-extensions-settings-macos.md)

4. Wenn Sie fertig sind, wählen Sie **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern.

Das Profil wird erstellt und in der Liste angezeigt. Denken Sie daran, das [Profil zuzuweisen](../device-profile-assign.md) und [seinen Status zu überwachen](../device-profile-monitor.md).

## <a name="next-steps"></a>Nächste Schritte

Nachdem das Profil erstellt wurde, kann es zugewiesen werden. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](../device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](../device-profile-monitor.md).
