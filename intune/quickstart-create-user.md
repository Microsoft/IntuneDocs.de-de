---
title: 'Schnellstart: Erstellen eines Benutzers in Intune'
description: 'Schnellstart: Erstellen eines Benutzers in Intune'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 10/30/2018
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: b5653c67766a3312cf7ce2872e8b0cd4301b0e8b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189488"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>Schnellstart: Erstellen eines Benutzers und Zuweisen einer Lizenz zu diesem Benutzer

In diesem Schnellstart erfahren Sie, wie Sie einen Benutzer erstellen und diesem anschließend eine Lizenz zuweisen können. Wenn Sie Intune verwenden, muss jede Person, die Zugriff auf Unternehmensdaten haben soll, über ein Benutzerkonto verfügen. Intune-Administratoren können später festlegen, dass diese Benutzer die Zugriffssteuerung verwalten sollen.

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als [globaler Administrator oder Intune-Dienstadministrator](users-add.md#types-of-administrators). Wenn Sie ein Testabonnement für Intune erstellt haben, besitzt das Konto, mit dem Sie das Abonnement erstellt haben, die Rolle des globalen Administrators.

## <a name="create-a-user"></a>Erstellen von Benutzern

Benutzer benötigen ein Benutzerkonto, um sich für die Intune-Geräteverwaltung registrieren zu können.

1. Wählen Sie in Intune **Benutzer** > **Alle Benutzer** > **Neuer Benutzer** aus.
![Browser](media/quickstart-create-user/create-user.png)
2. Geben Sie in das Feld **Name** z.B. *Dewey Kellum* ein.
3. Geben Sie in das Feld **Benutzername** eine Benutzer-ID ein, z.B. Dewey@contoso.onmicrosoft.com.

    > [!NOTE]
    > Wenn Sie noch keinen Kundendomänennamen erstellt haben, verwenden Sie den überprüften Domänennamen, den Sie zum Erstellen des Intune-Abonnements (oder der [kostenlosen Testversion](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial)) verwendet haben. 

4. Klicken Sie auf **Kennwort anzeigen**, und notieren Sie sich das automatisch generierte Kennwort, mit dem Sie sich bei einem Testgerät anmelden können.
5. Wählen Sie **Erstellen** aus.

## <a name="assign-a-license-to-the-user"></a>Zuweisen einer Benutzerlizenz

Nachdem Sie einen Benutzer erstellt haben, müssen Sie diesem über das [Office 365-Portal](http://go.microsoft.com/fwlink/p/?LinkId=698854) eine Intune-Lizenz zuweisen. Wenn ein Benutzer keine Lizenz hat, kann er sein Gerät auch nicht bei Intune registrieren. 

1. Melden Sie sich im [Office 365-Portal](http://go.microsoft.com/fwlink/p/?LinkId=698854) mit den gleichen Anmeldeinformationen an, die Sie auch zur Anmeldung in Intune verwendet haben.
2. Klicken Sie auf **Benutzer** > **Aktive Benutzer**, und wählen Sie den Benutzer aus, den Sie soeben erstellt haben.
3. Klicken Sie neben **Produktlizenzen** auf **Bearbeiten**.
4. Wählen Sie unter **Standort** einen Standort für den Benutzer aus.
5. Klicken Sie neben der Intune-Lizenz (oder einer anderen Ihrer Lizenzen, die Intune betrifft) auf **On** (Ein). Der angezeigte [Produktname](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)** wird als Dienstplan in der Azure-Verwaltung verwendet. 

   > [!NOTE]
   > Diese Einstellung verwendet eine Ihrer Lizenzen für diesen Benutzer. Wenn Sie eine Testumgebung verwenden, sollten Sie diese Lizenz später einem echten Benutzer in einer Liveumgebung zuweisen.
6. Klicken Sie auf **Speichern** > **Schließen**.

Für den neuen aktiven Intune-Benutzer wird jetzt angezeigt, dass er eine **Intune**-Lizenz verwendet.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Wenn Sie diesen Benutzer nicht mehr benötigen, können Sie diesen löschen, indem Sie zum [Office 365-Portal](http://go.microsoft.com/fwlink/p/?LinkId=698854) navigieren und auf **Benutzer** > **Aktive Benutzer** klicken, den *Benutzer aus der Liste auswählen*, und dann auf **Benutzer löschen** > **Benutzer löschen** > **Änderungen bestätigen** > **Schließen** klicken.

## <a name="next-steps"></a>Nächste Schritte

In diesem Schnellstart haben Sie erfahren, wie Sie einen Benutzer erstellen und diesem eine Lizenz zugewiesen. Weitere Informationen zum Hinzufügen von Benutzern zu Intune finden Sie unter [Hinzufügen von Benutzern und Gewähren von Administratorrechten für Intune](users-add.md).

Weitere Informationen zu Intune erhalten Sie im nächsten Schnellstart.

> [!div class="nextstepaction"]
> [Schnellstart: Erstellen einer Gruppe zum Verwalten von Benutzern](quickstart-create-group.md)
