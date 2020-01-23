---
title: 'Schnellstart: Erstellen eines Benutzers in Intune'
description: 'Schnellstart: Erstellen eines Benutzers in Intune'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/25/2019
ms.author: erikje
ms.manager: dougeby
ms.assetid: 820fcb18-0927-4ebd-be79-dce92b51c261
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: fdd97e69c97df5a266e147381d94b3d4419bab34
ms.sourcegitcommit: 52475fcd8d05d2f6b858d780ebb3d88eaadb0849
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "76036572"
---
# <a name="quickstart-create-a-user-in-intune-and-assign-them-a-license"></a>Schnellstart: Erstellen eines Benutzers in Intune und Zuweisen einer Lizenz

In dieser Schnellstartanleitung erstellen Sie einen Benutzer und weisen ihm eine Intune-Lizenz zu. Wenn Sie Intune verwenden, muss jede Person, die Zugriff auf Unternehmensdaten haben soll, über ein eigenes Benutzerkonto verfügen. Intune-Administratoren können später festlegen, dass Benutzer die Zugriffssteuerung verwalten.

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als [globaler Administrator oder Intune-Dienstadministrator](users-add.md#types-of-administrators). Wenn Sie ein Testabonnement für Intune erstellt haben, besitzt das Konto, mit dem Sie das Abonnement erstellt haben, die Rolle des Unternehmensadministrators.

## <a name="create-a-user"></a>Erstellen eines Benutzers

Benutzer benötigen ein Benutzerkonto, um sich für die Intune-Geräteverwaltung registrieren zu können. So erstellen Sie einen neuen Benutzer:

1. Wählen Sie in Intune **Benutzer** > **Alle Benutzer** > **Neuer Benutzer** aus.
![Browser](./media/quickstart-create-user/create-user.png)
2. Geben Sie in das Feld **Name** z.B. *Dewey Kellum* ein.
3. Geben Sie in das Feld **Benutzername** eine Benutzer-ID ein, z.B. Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Wenn Sie noch keinen Kundendomänennamen erstellt haben, verwenden Sie den überprüften Domänennamen, den Sie zum Erstellen des Intune-Abonnements (oder der [kostenlosen Testversion](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)) verwendet haben. 

4. Klicken Sie auf **Kennwort anzeigen**, und notieren Sie sich das automatisch generierte Kennwort, mit dem Sie sich bei einem Testgerät anmelden können.
5. Wählen Sie **Erstellen** aus.

## <a name="assign-a-license-to-the-user"></a>Zuweisen einer Benutzerlizenz

Nachdem Sie einen Benutzer erstellt haben, müssen Sie diesem über das [Microsoft 365 Admin Center](https://go.microsoft.com/fwlink/p/?LinkId=698854) eine Intune-Lizenz zuweisen. Wenn Sie dem Benutzer keine Lizenz zuweisen, kann er sein Gerät nicht bei Intune registrieren. 

So weisen Sie einem Benutzer eine Intune-Lizenz zu:

1. Melden Sie sich im [Microsoft 365 Admin Center](https://go.microsoft.com/fwlink/p/?LinkId=698854) mit den gleichen Anmeldeinformationen an, die Sie auch zur Anmeldung in Intune verwendet haben.
2. Wählen Sie **Benutzer** > **Aktive Benutzer** aus, und wählen Sie den Benutzer aus, den Sie soeben erstellt haben.
3. Klicken Sie neben **Produktlizenzen** auf **Bearbeiten**.
4. Wählen Sie unter **Standort** einen Standort für den Benutzer aus.
5. Klicken Sie neben der Intune-Lizenz (oder einer anderen Ihrer Lizenzen, die Intune betrifft) auf **On** (Ein). Der angezeigte [Produktname](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)** wird als Dienstplan in der Azure-Verwaltung verwendet. 

   > [!NOTE]
   > Diese Einstellung verwendet eine Ihrer Lizenzen für diesen Benutzer. Wenn Sie eine Testumgebung verwenden, sollten Sie diese Lizenz später einem echten Benutzer in einer Liveumgebung zuweisen.
6. Klicken Sie auf **Speichern** > **Schließen**.

Dem neuen aktiven Intune-Benutzer wird jetzt angezeigt, dass er eine **Intune**-Lizenz verwendet.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Wenn Sie diesen Benutzer nicht mehr benötigen, können Sie diesen löschen, indem Sie zum [Microsoft 365 Admin Center](https://go.microsoft.com/fwlink/p/?LinkId=698854) navigieren und auf Folgendes klicken: **Benutzer** > **Aktive Benutzer** > *den Benutzer in der Liste* > **Benutzer löschen** > **Benutzer löschen** > **Änderungen bestätigen** > **Schließen**.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie einen Benutzer erstellt und ihm eine Intune-Lizenz zugewiesen. Weitere Informationen zum Hinzufügen von Benutzern zu Intune finden Sie unter [Hinzufügen von Benutzern und Gewähren von Administratorrechten für Intune](users-add.md).

Weitere Informationen zu Intune erhalten Sie im nächsten Schnellstart.

> [!div class="nextstepaction"]
> [Schnellstart: Erstellen einer Gruppe zum Verwalten von Benutzern](../quickstart-create-group.md)
