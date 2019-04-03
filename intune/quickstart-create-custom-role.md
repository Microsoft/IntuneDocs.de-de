---
title: 'Schnellstart: Erstellen und Zuweisen einer benutzerdefinierten Rolle in Intune'
description: 'Schnellstart: Erstellen und Zuweisen einer benutzerdefinierten Rolle für einen Remotegeräte-Manager'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/26/2019
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6cf4e365f4e68920ea5d24dc3ce2e1bd5eb9f817
ms.sourcegitcommit: 9af102e1232d9a568a7901783c30ba9905e64d99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/26/2019
ms.locfileid: "58477127"
---
# <a name="quickstart-create-and-assign-a-custom-role"></a>Schnellstart: Erstellen und Zuweisen einer benutzerdefinierten Rolle

In diesem Intune-Schnellstart erstellen Sie eine benutzerdefinierte Rolle mit bestimmten Berechtigungen für eine Abteilung für Sicherheitsvorgänge. Anschließend weisen Sie diese Rolle einer Gruppe zu, die aus Mitgliedern dieser Abteilung besteht. Es gibt mehrere Standardrollen, die Sie sofort verwenden können. Wenn Sie benutzerdefinierte Rollen wie diese erstellen, verfügen Sie über präzise Zugriffssteuerung für alle Teile Ihres Verwaltungssystems für mobile Geräte.

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="prerequisites"></a>Voraussetzungen

- Um dieser Schnellstartanleitung zu folgen, müssen Sie [eine Gruppe erstellen](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als globaler Administrator oder als Intune-Dienstadministrator. Wenn Sie ein Testabonnement für Intune erstellt haben, besitzt das Konto, mit dem Sie das Abonnement erstellt haben, die Rolle des globalen Administrators.

## <a name="create-a-custom-role"></a>Erstellen einer benutzerdefinierten Rolle

Wenn Sie eine benutzerdefinierte Rolle erstellen, können Sie Berechtigungen für eine Vielzahl von Aktionen festlegen. Für die Sicherheitsvorgangsrolle legen wir einige Leseberechtigungen fest, sodass der Anwender die Konfigurationen und Richtlinien eines Geräts überprüfen kann.

1. Wählen Sie in Intune die Option **Rollen** > **Alle Rollen** > **Hinzufügen** aus.
![Browser](media/quickstart-create-custom-role/add-custom-role.png)
2. Geben Sie im Feld **Name** unter **Benutzerdefinierte Rolle hinzufügen** *Sicherheitsvorgänge* ein.
3. Geben Sie *This role lets a security operator monitor device configuration and compliance information.* (Mit dieser Rolle kann ein Sicherheitsmitarbeiter die Gerätekonfiguration und Kompatibilitätsinformationen überwachen.) im Feld **Beschreibung** ein.
4. Klicken Sie neben **Lesen** > **OK** auf **Konfigurieren** > **Bezeichner von Unternehmensgeräten** > **Ja**.
![Browser](media/quickstart-create-custom-role/corp-device-id-read.png)
5. Klicken Sie neben **Lesen** > **OK** auf **Gerätekompatibilitätsrichtlinien** > **Ja**.
6. Klicken Sie neben **Lesen** > **OK** auf **Gerätekonfigurationen** > **Ja**.
7. Klicken Sie neben **Lesen** > **OK** auf **Organisation** > **Ja**.
8. Klicken Sie auf **OK** > **Erstellen**.

## <a name="assign-the-role-to-a-group"></a>Zuweisen einer Rolle zu einer Gruppe

Bevor Ihr Sicherheitsoperator die neuen Berechtigungen verwenden kann, müssen Sie die Rolle einer Gruppe zuweisen, die den Sicherheitsbenutzer enthält.

1. Wählen Sie in Intune die Optionen **Rollen** > **Alle Rollen** > **Sicherheitsvorgänge** aus.
2. Klicken Sie unter **Intune-Rollen** auf **Zuweisungen** > **Zuweisen**.
3. Geben Sie im Feld **Zuweisungsname** *Sec ops* ein.
4. Klicken Sie auf **Mitglied (Gruppen)** > **Hinzufügen**.
5. Wählen Sie die Gruppe **Contoso Tester** aus.
6. Klicken Sie auf **Auswählen** > **OK**.
7. Klicken Sie auf **Bereich (Gruppen)** > **Wählen Sie die Gruppen aus, die eingeschlossen werden sollen.** > **Contoso Tester**.
8. Klicken Sie auf **Auswählen** > **OK** > **OK**.

Nun ist jeder in der Gruppe ein Mitglied der Rolle *Sicherheitsvorgänge* und kann die folgenden Informationen über ein Gerät überprüfen: Unternehmensgerätebezeichner, Gerätekompatibilitätsrichtlinien, Gerätekonfigurationen und Organisationsinformationen.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Wenn Sie die neue benutzerdefinierte Rolle nicht mehr verwenden möchten, können Sie sie löschen. Wählen Sie **Rollen** > **Alle Rollen** aus, und klicken Sie auf die Auslassungspunkte neben der Rolle. Klicken Sie anschließend auf **Löschen**.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie eine benutzerdefinierte Sicherheitsvorgangsrolle erstellt und diese einer Gruppe zugewiesen. Weitere Informationen finden Sie unter [Role-based administration control (RBAC) with Microsoft Intune (Rollenbasierte Zugriffssteuerung mit Microsoft Intune)](role-based-access-control.md).

Weitere Informationen zu Intune erhalten Sie im nächsten Schnellstart.

> [!div class="nextstepaction"]
> [Schnellstart: Erstellen eines E-Mail-Geräteprofils für iOS](quickstart-email-profile.md)
