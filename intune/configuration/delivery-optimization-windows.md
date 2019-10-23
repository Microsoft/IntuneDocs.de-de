---
title: Übermittlungsoptimierungseinstellungen für Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Konfigurieren Sie, wie von Ihnen mit Intune verwaltete Windows 10-Geräte die Übermittlungsoptimierung verwenden sollen. Erstellen Sie in Intune ein Gerätekonfigurationsprofil zum Installieren von Updates über das Internet. Erfahren Sie auch, wie vorhandene Updateringe mit einem Übermittlungsoptimierungsprofil ersetzt werden.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 7d94a2c7e47b3cfcc9f4592faf0a4c2a09a24ac4
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72495246"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Übermittlungsoptimierungseinstellungen in Microsoft Intune

Mithilfe von Intune können Sie die Übermittlungsoptimierungseinstellungen für Ihre Windows 10-Geräte verwenden, um die Auslastung der Bandbreite zu verringern, wenn diese Geräte Anwendungen und Updates herunterladen. Die Übermittlungsoptimierung wird als Bestandteil Ihrer Gerätekonfigurationsprofile konfiguriert.  

In diesem Artikel wird beschrieben, wie Sie Übermittlungsoptimierungseinstellungen als Teil eines Gerätekonfigurationsprofils konfigurieren können. Nachdem Sie ein Profil erstellt haben, sollten Sie dieses Ihren Windows 10-Geräten zuweisen oder für diese bereitstellen. 

Eine Liste der von Intune unterstützten Übermittlungsoptimierungseinstellungen finden Sie unter [Delivery optimization settings for Intune (Übermittlungsoptimierungseinstellungen für Intune)](../delivery-optimization-settings.md).  

Weitere Informationen zur Übermittlungsoptimierung unter Windows 10 finden Sie in der Windows-Dokumentation unter [Delivery Optimization updates (Updates für die Übermittlungsoptimierung)](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization).  


> [!NOTE]
> **Softwareupdates – Windows 10-Updateringe** wird durch die Einstellungen für **Übermittlungsoptimierung** ersetzt. Ihre vorhandenen Updateringe können zur Verwendung der Einstellungen für die **Übermittlungsoptimierung** geändert werden. [Wechseln vorhandener Updateringe zur Übermittlungsoptimierung](#move-existing-update-rings-to-delivery-optimization) (in diesem Artikel) 
## <a name="create-the-profile"></a>Erstellen des Profils

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.

2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.

3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
    - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie die Plattform aus:  

        - **Windows 10 und höher**

    - **Profiltyp**: Wählen Sie **Übermittlungsoptimierung** aus.
    - **Einstellungen:** Konfigurieren Sie Einstellungen, die definieren, wie Updates und Apps heruntergeladen werden sollen. Weitere Informationen zu verfügbaren Einstellungen finden Sie unter [Delivery optimization settings for Intune (Übermittlungsoptimierungseinstellungen für Intune)](../delivery-optimization-settings.md).

4. Wählen Sie anschließend **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern.

Das Profil wird erstellt und in der Liste angezeigt. [Weisen](device-profile-assign.md) Sie als Nächstes das Profil zu, und [überwachen Sie dessen Status](device-profile-monitor.md).

## <a name="move-existing-update-rings-to-delivery-optimization"></a>Wechseln vorhandener Updateringe zur Übermittlungsoptimierung

Die **Übermittlungsoptimierungseinstellungen** ersetzen die **Softwareupdates im Rahmen der Windows 10-Updateringe**. Ihre vorhandenen Updateringe können problemlos zur Verwendung der Einstellungen für die **Übermittlungsoptimierung** geändert werden. Wenn Sie beim Erstellen eines Übermittlungsoptimierungsprofils dieselben Einstellungen beibehalten möchten, verwenden Sie denselben *Downloadmodus für Übermittlungsoptimierung*, und legen Sie dann die Einstellungen fest, die Sie bereits verwenden. Sie können die Übermittlungsoptimierungseinstellungen allerdings auch erneut konfigurieren, um sämtliche zusätzlichen Einstellungen zu nutzen, die das Übermittlungsoptimierungsprofil verwalten kann.

1. Erstellen Sie ein Konfigurationsprofil für die Übermittlungsoptimierung:

    1. Wählen Sie in Intune **Gerätekonfiguration** > **Profile** > **Profil erstellen** aus.
    2. Geben Sie die folgenden Eigenschaften ein:

        - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
        - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
        - **Plattform**: Wählen Sie **Windows 10 und höher** aus.
        - **Profiltyp**: Wählen Sie **Übermittlungsoptimierung** aus.
        - **Einstellungen:** Legen Sie für den **Downloadmodus für Übermittlungsoptimierung** den Modus fest, der bereits vom vorhanden Softwareupdatering verwendet wird, wenn Sie die Einstellungen für Ihre Geräte nicht ändern möchten. Folgende Optionen sind verfügbar:
            - **Nicht konfiguriert**
            - **Nur HTTP, kein Peering**
            - **HTTP kombiniert mit Peering hinter derselben NAT**
            - **HTTP kombiniert mit eine Privatgruppe übergreifendem Peering**
            - **HTTP kombiniert mit Internetpeering**
            - **Einfacher Downloadmodus ohne Peering**
            - **Umgehungsmodus**
    3. Konfigurieren Sie jegliche zusätzlichen Einstellungen, die Sie möglicherweise verwalten möchten.
1. Weisen Sie dieses neue Profil den gleichen Geräten und Benutzern zu, die zu dem vorhandenen Softwareupdatering gehören. In [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) sind die Schritte aufgeführt.

3. Heben Sie die Konfiguration des vorhandenen Softwarerings auf:
    1. Wechseln Sie in Intune zu **Softwareupdates** > Windows 10-Updateringe.
    2. Wählen Sie in der Liste Ihren Updatering aus.
    3. Legen Sie in den Einstellungen für den **Downloadmodus für Bereitstellungsoptimierung** **Nicht konfiguriert** fest.
    4. Wählen Sie zum Speichern der Änderungen **OK** > **Speichern** aus.

## <a name="next-steps"></a>Nächste Schritte

[Weisen Sie das Profil zu](device-profile-assign.md), und [überwachen Sie seinen Status](device-profile-monitor.md).  
Sehen Sie sich die [Übermittlungsoptimierungseinstellungen](../delivery-optimization-settings.md) für Intune an.
