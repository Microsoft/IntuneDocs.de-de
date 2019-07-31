---
title: 'Schnellstart: Erstellen einer Gruppe zum Verwalten von Benutzern'
titleSuffix: Microsoft Intune
description: Bei dieser Schnellstartanleitung verwenden Sie Microsoft Intune zum Erstellen einer Gruppe basierend auf vorhandenen Benutzern.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a8a444f886a5b754fd6ba3763e183db0fe95d5f
ms.sourcegitcommit: d2ac912b834c4840de9cc92ba1815b6ecfbfb52b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68482981"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Schnellstart: Erstellen einer Gruppe zum Verwalten von Benutzern

Bei dieser Schnellstartanleitung verwenden Sie Intune zum Erstellen einer Gruppe basierend auf einem vorhandenen Benutzer. Mit Gruppen können Sie Benutzer verwalten und den Zugriff Ihrer Mitarbeiter auf Ihre Unternehmensressourcen steuern. Bei diesen Ressourcen kann es sich um Teile des Intranets Ihres Unternehmens oder um externe Ressourcen wie SharePoint-Websites, SaaS-Apps oder Web-Apps handeln.

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

>[!NOTE]
>Intune bietet die vorab erstellten Gruppen **Alle Benutzer** und **Alle Geräte** in der Konsole zur Vereinfachung mit integrierten Optimierungen an.

## <a name="prerequisites"></a>Voraussetzungen

- Um dieser Schnellstartanleitung zu folgen, müssen Sie [einen Benutzer erstellen](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Melden Sie sich beim [Intune](https://aka.ms/intuneportal)-Portal als [globaler Administrator oder Intune-Dienstadministrator](users-add.md#types-of-administrators) an. Wenn Sie ein Testabonnement für Intune erstellt haben, besitzt das Konto, mit dem Sie das Abonnement erstellt haben, die Rolle des globalen Administrators.

## <a name="create-a-group"></a>Erstellen einer Gruppe

Mit den folgenden Schritten erstellen Sie eine Gruppe, die im späteren Verlauf dieser Schnellstartreihe verwendet wird. So erstellen Sie eine Gruppe:

1. Sobald Sie den Bereich **Microsoft Intune** geöffnet haben, wählen Sie **Gruppen** > **Neue Gruppe** aus.
2. Wählen Sie im Dropdownfeld **Gruppentyp** die Option **Sicherheit** aus.
3. Geben Sie im Feld **Gruppenname** den Namen für die neue Gruppe (z.B. **Contoso Testers**) ein.
4. Fügen Sie eine **Beschreibung** für die Gruppe hinzu.
5. Legen Sie den **Mitgliedschaftstyp** auf **Zugewiesen** fest. 
6. Klicken Sie auf **Mitglieder**, und wählen Sie mindestens ein Mitglied aus der Liste für die Gruppe aus.

    ![Screenshot: Erstellen einer Gruppe in Microsoft Intune](./media/quickstart-use-groups-01.png)

7. Klicken Sie auf **Auswählen** > **Erstellen**.

Sobald Sie die Gruppe erfolgreich erstellt haben, wird sie in der Liste **Alle Gruppen** angezeigt. 

## <a name="next-steps"></a>Nächste Schritte

Bei dieser Schnellstartanleitung haben Sie Intune zum Erstellen einer Gruppe basierend auf einem vorhandenen Benutzer verwendet. Weitere Informationen zum Hinzufügen von Gruppen zu Intune finden Sie unter [Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten](groups-add.md).

Weitere Informationen zu Intune erhalten Sie im nächsten Schnellstart.

> [!div class="nextstepaction"]
> [Schnellstart: Einrichten der automatischen Registrierung für Windows 10-Geräte](quickstart-setup-auto-enrollment.md)
