---
title: 'Hinzufügen von benutzerdefinierten Einstellungen für iOS-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
titleSuffix: ''
description: Exportieren Sie iOS-Einstellungen aus Apple Configurator oder dem Apple-Profil-Manager, und importieren Sie diese Einstellungen in Microsoft Intune. Diese Einstellungen können benutzerdefinierte Einstellungen und Features auf iOS-Geräten erstellen, verwenden und steuern. Dieses benutzerdefinierte Profil kann dann iOS-Geräten in Ihrer Organisation zugewiesen oder an diese verteilt werden, um eine Baseline oder einen Standard zu erstellen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6bfd832d9225221bcc6aaefe091a3cebf57a54c
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048623"
---
# <a name="use-custom-settings-for-ios-devices-in-microsoft-intune"></a>Verwenden benutzerdefinierter Einstellungen für iOS-Geräte in Microsoft Intune

Mit Microsoft Intune können Sie benutzerdefinierte Einstellungen für iOS-Geräte mit einem benutzerdefinierten Profil hinzufügen oder erstellen. Benutzerdefinierte Profile sind ein Feature in Intune. Sie sind dafür da, Geräteeinstellungen und -features hinzuzufügen, die nicht in Intune integriert sind.

Wenn Sie iOS-Geräte verwenden, gibt es zwei Möglichkeiten, benutzerdefinierte Einstellungen in Intune zu importieren:

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple-Profil-Manager](https://support.apple.com/profile-manager)

Mit diesen beiden Tools können Sie Einstellungen in ein Konfigurationsprofil exportieren. Diese Datei importieren Sie dann in Intune und weisen das Profil Ihren iOS-Benutzern und -Geräten zu. Wenn Sie das Profil zugewiesen haben, werden die Einstellung verteilt, und es wird eine Baseline oder ein Standard für iOS in Ihrer Organisation erstellt.

In diesem Artikel erfahren Sie, wie Sie ein benutzerdefiniertes Profil für iOS-Geräte erstellen. Außerdem erhalten Sie Informationen zu Apple Configurator und zum Apple-Profil-Manager.

## <a name="before-you-begin"></a>Vorbereitung

- Wenn Sie mit **Apple Configurator** das Konfigurationsprofil erstellen, achten Sie darauf, dass die exportierten Einstellungen mit der iOS-Version auf den verwendeten Geräten kompatibel ist. In der **Referenz zu Konfigurationsprofilen** und der **Referenz zum Protokoll für die Verwaltung mobiler Geräte** auf der [Apple Developer-Website](https://developer.apple.com/) finden Sie Informationen zum Beheben von Kompatibilitätsproblemen.

- Beachten Sie bei der Verwendung des **Apple-Profil-Managers** Folgendes:

  - Aktivieren Sie die [Verwaltung mobiler Geräte](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) im Profil-Manager.
  - Fügen Sie im Profil-Manager [iOS-Geräte](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) hinzu.
  - Nachdem Sie ein Gerät im Profil-Manager hinzugefügt haben, navigieren Sie zu **Bibliothek** > **Geräte**, wählen Sie Ihr Gerät aus, und klicken Sie auf **Einstellungen**. Legen Sie die allgemeinen Einstellungen für das Gerät fest.

    Laden Sie diese Datei herunter, und speichern Sie sie. Diese Datei fügen Sie in das Intune-Profil ein.

  - Achten Sie darauf, dass die Einstellungen, die Sie aus dem Apple-Profil-Manager exportieren, mit der iOS-Version auf den verwendeten Geräten kompatibel sind. In der **Referenz zu Konfigurationsprofilen** und der **Referenz zum Protokoll für die Verwaltung mobiler Geräte** auf der [Apple Developer-Website](https://developer.apple.com/) finden Sie Informationen zum Beheben von Kompatibilitätsproblemen.

## <a name="create-the-profile"></a>Erstellen des Profils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen Profilnamen ein, z.B. `ios custom profile`.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein.
    - **Plattform**: Wählen Sie **iOS**.
    - **Profiltyp:** Wählen Sie **Benutzerdefiniert** aus.

4. Legen Sie unter **Benutzerdefinierte Konfiguration** die folgenden Einstellungen fest:

    - **Name des benutzerdefinierten Konfigurationsprofils:** Geben Sie einen Namen für die Richtlinie ein. Dieser Name wird auf dem Gerät und im Intune-Status angezeigt.
    - **Konfigurationsprofildatei:** Navigieren Sie zum mit Apple Configurator oder dem Apple-Profil-Manager erstellten Konfigurationsprofil. Die importierte Datei wird im Bereich **Dateiinhalt** angezeigt.

5. Klicken Sie auf **OK** > **Erstellen** aus, um das Intune-Profil zu erstellen. Dann wird das Profil erstellt und in der Liste **Gerätekonfiguration > Profile** angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. [Weisen Sie anschließend das Profil zu](device-profile-assign.md).

Weitere Informationen finden Sie im [Artikel zum Erstellen eines Profils auf einem macOS-Gerät](custom-settings-macos.md). 
