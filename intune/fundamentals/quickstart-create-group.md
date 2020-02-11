---
title: 'Schnellstart: Erstellen einer Gruppe zum Verwalten von Benutzern'
titleSuffix: Microsoft Intune
description: Bei dieser Schnellstartanleitung verwenden Sie Microsoft Intune zum Erstellen einer Gruppe basierend auf vorhandenen Benutzern.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/17/2020
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9b06043dd10f92b6176d4b2e9f90f1b7c87aac9
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540950"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Schnellstart: Erstellen einer Gruppe zum Verwalten von Benutzern

Bei dieser Schnellstartanleitung verwenden Sie Intune zum Erstellen einer Gruppe basierend auf einem vorhandenen Benutzer. Mit Gruppen können Sie Benutzer verwalten und den Zugriff Ihrer Mitarbeiter auf Ihre Unternehmensressourcen steuern. Bei diesen Ressourcen kann es sich um Teile des Intranets Ihres Unternehmens oder um externe Ressourcen wie SharePoint-Websites, SaaS-Apps oder Web-Apps handeln.

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

>[!NOTE]
>Intune bietet die vorab erstellten Gruppen **Alle Benutzer** und **Alle Geräte** in der Konsole zur Vereinfachung mit integrierten Optimierungen an.

## <a name="prerequisites"></a>Voraussetzungen

- Microsoft Intune-Abonnement: [Registrieren Sie sich für eine kostenlose Testversion](../fundamentals/free-trial-sign-up.md).
- Um dieser Schnellstartanleitung zu folgen, müssen Sie [einen Benutzer erstellen](quickstart-create-user.md).

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>Anmelden bei Intune im Microsoft Endpoint Manager

Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) als [globaler Administrator oder Intune-Dienstadministrator](users-add.md#types-of-administrators) an. Wenn Sie ein Testabonnement für Intune erstellt haben, besitzt das Konto, mit dem Sie das Abonnement erstellt haben, die Rolle des globalen Administrators.

## <a name="create-a-group"></a>Erstellen einer Gruppe

Mit den folgenden Schritten erstellen Sie eine Gruppe, die im späteren Verlauf dieser Schnellstartreihe verwendet wird. So erstellen Sie eine Gruppe:

1. Sobald Sie den **Microsoft Endpoint Manager** geöffnet haben, wählen Sie die Option **Gruppen** > **Neue Gruppe** aus.
2. Wählen Sie im Dropdownfeld **Gruppentyp** die Option **Sicherheit** aus.
3. Geben Sie im Feld **Gruppenname** den Namen für die neue Gruppe (z.B. **Contoso Testers**) ein.
4. Fügen Sie eine **Gruppenbeschreibung** für die Gruppe hinzu.
5. Legen Sie den **Mitgliedschaftstyp** auf **Zugewiesen** fest. 
6. Wählen Sie den Link unter **Mitglieder** aus, und fügen Sie mindestens ein Mitglied aus der Liste für die Gruppe hinzu.

    ![Screenshot: Erstellen einer Gruppe in Microsoft Intune](./media/quickstart-create-group/quickstart-use-groups-01.png)

7. Klicken Sie auf **Auswählen** > **Erstellen**.

Sobald Sie die Gruppe erfolgreich erstellt haben, wird sie in der Liste **Alle Gruppen** angezeigt. 

## <a name="next-steps"></a>Nächste Schritte

Bei dieser Schnellstartanleitung haben Sie Intune zum Erstellen einer Gruppe basierend auf einem vorhandenen Benutzer verwendet. Weitere Informationen zum Hinzufügen von Gruppen zu Intune finden Sie unter [Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten](../groups-add.md).

Weitere Informationen zu Intune erhalten Sie im nächsten Schnellstart.

> [!div class="nextstepaction"]
> [Schnellstart: Einrichten der automatischen Registrierung für Windows 10-Geräte](../enrollment/quickstart-setup-auto-enrollment.md)
