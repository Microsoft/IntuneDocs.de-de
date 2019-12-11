---
title: Hinzufügen oder Konfigurieren von Education-Einstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie die „Take a Test“-App in einem Gerätekonfigurationsprofil für Geräte auf Windows 10 und höher in Microsoft Intune. Erstellen Sie ein Konfigurationsprofil mithilfe der Education-Einstellungen, und geben Sie eine Test-App-URL ein; wählen Sie aus, wie Benutzer sich anmelden, überwachen Sie den Bildschirm während des Tests, und lassen Sie Textvorschläge während des Tests zu, oder verhindern Sie sie.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be6cc64c3a65af72fd74bc58ed7c06a214797510
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059464"
---
# <a name="use-the-take-a-test-app-on-windows-10-devices-in-microsoft-intune"></a>Verwenden der „Take a Test“-App für Windows 10-Geräte in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Education-Profile in Intune sind dafür konzipiert, dass Kursteilnehmer einen Test oder eine Prüfung auf Geräten absolvieren. Dieses Feature umfasst die **Take a Test**-App und Einstellungen zum Hinzufügen einer Test-URL, das Auswählen der Methode, mit der Endbenutzer sich bei dem Test anmelden, und Sonstiges. Dieses Feature unterstützt die folgende Plattform:

- Windows 10 und höher

Wenn der Benutzer sich anmeldet, wird die „Take a Test“-App automatisch mit dem Test geöffnet, den Sie eingegeben haben. Keine anderen Apps können auf dem Gerät ausgeführt werden, während der Test ausgeführt wird. [Durchführen von Prüfungen in Windows 10](https://docs.microsoft.com/education/windows/take-tests-in-windows-10) enthält weitere Details zur „Take a Test“-App.

In diesem Artikel sind die Schritte zum Erstellen eines Gerätekonfigurationsprofil in Microsoft Intune aufgelistet. Darüber hinaus enthält er Informationen zum Lesen und Lernen der verfügbaren Education-Einstellungen für Ihre Windows 10-Geräte.

## <a name="create-a-device-profile"></a>Erstellen eines Geräteprofils

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
    - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie **Windows 10 und höher** aus.
    - **Profil**: Wählen Sie **Education-Profil** aus.

4. Geben Sie die Einstellungen ein, die Sie konfigurieren möchten:

    - [Windows 10 und höher](education-settings-windows.md)

5. Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern.

Nachdem Sie Ihre Einstellungen eingegeben und das Profil erstellt haben, wird das Profil in der Liste angezeigt. Im nächsten Schritt [weisen Sie dieses Profil nun einigen Gruppen zu](device-profile-assign.md).

## <a name="next-steps"></a>Nächste Schritte

Lesen Sie eine Liste mit den [Education-Einstellungen für Windows 10](education-settings-windows.md) und deren Beschreibungen.

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
