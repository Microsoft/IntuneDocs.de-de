---
title: 'Schnellstart: Erstellen einer Gruppe zum Verwalten von Benutzern'
titlesuffix: Microsoft Intune
description: Bei dieser Schnellstartanleitung verwenden Sie Microsoft Intune zum Erstellen einer Gruppe basierend auf vorhandenen Benutzern.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2b52265bb9b3df800c0e13450a2154e46098a933
ms.sourcegitcommit: 9d08545727543b434dd270371fa50233470f2bce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "50410819"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>Schnellstart: Erstellen einer Gruppe zum Verwalten von Benutzern

Bei dieser Schnellstartanleitung verwenden Sie Intune zum Erstellen einer Gruppe basierend auf einem vorhandenen Benutzer. Mit Gruppen können Sie Benutzer verwalten und den Zugriff Ihrer Mitarbeiter auf Ihre Unternehmensressourcen steuern. Bei diesen Ressourcen kann es sich um Teile des Intranets Ihres Unternehmens oder um externe Ressourcen wie SharePoint-Websites, SaaS-Apps oder Web-Apps handeln.

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

>[!NOTE]
>Intune bietet die vorab erstellten Gruppen **Alle Benutzer** und **Alle Geräte** in der Konsole zur Vereinfachung mit integrierten Optimierungen an.

## <a name="prerequisites"></a>Voraussetzungen

- Um dieser Schnellstartanleitung zu folgen, müssen Sie [einen Benutzer erstellen](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als [globaler Administrator oder Intune-Dienstadministrator](users-add.md#types-of-administrators). Wenn Sie ein Testabonnement für Intune erstellt haben, besitzt das Konto, mit dem Sie das Abonnement erstellt haben, die Rolle des globalen Administrators.

## <a name="create-a-group"></a>Erstellen einer Gruppe

Mit den folgenden Schritten erstellen Sie eine Gruppe, die im späteren Verlauf dieser Schnellstartreihe verwendet wird.

1. Sobald Sie den Bereich **Microsoft Intune** geöffnet haben, wählen Sie **Gruppen** > **Neue Gruppe** aus.
2. Wählen Sie im Dropdownfeld **Gruppentyp** die Option **Sicherheit** aus.
3. Geben Sie als **Gruppenname** „Contoso Tester“ ein, und fügen Sie eine **Gruppenbeschreibung** hinzu.
4. Legen Sie den **Mitgliedschaftstyp** auf **Zugewiesen** fest. 
5. Klicken Sie auf **Mitglieder**, und wählen Sie mindestens ein Mitglied aus der vorhandenen Liste für die Gruppe aus.

    ![Screenshot: Erstellen einer Gruppe in Microsoft Intune](./media/quickstart-use-groups-01.png)

6. Klicken Sie auf **Auswählen** > **Erstellen**.

Sobald Sie die Gruppe erfolgreich erstellt haben, wird sie in der Liste **Alle Gruppen** angezeigt. 

## <a name="next-steps"></a>Nächste Schritte

Bei dieser Schnellstartanleitung haben Sie Intune zum Erstellen einer Gruppe basierend auf einem vorhandenen Benutzer verwendet.

> [!div class="nextstepaction"]
> [Erstellen einer Gerätekompatibilitätsrichtlinie](quickstart-create-policy.md)
