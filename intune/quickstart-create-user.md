---
title: 'Schnellstart: Erstellen eines Benutzers in Intune'
description: 'Schnellstart: Erstellen eines Benutzers in Intune'
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 6a1d591e635dccd99551d9b8d40e099724a85d77
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581672"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>Schnellstart: Erstellen eines Benutzers und Zuweisen einer Lizenz zu diesem Benutzer

In dieser Schnellstartanleitung erstellen Sie einen Benutzer und weisen diesem eine Lizenz zu. Wenn Sie Intune verwenden, muss jede Person, die Zugriff auf Unternehmensdaten haben soll, über ein Benutzerkonto verfügen. Intune-Administratoren können dann festlegen, dass diese Benutzer die Zugriffssteuerung verwalten sollen.

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als globaler Administrator oder als Intune-Dienstadministrator.

## <a name="create-a-user"></a>Erstellen eines Benutzers

Benutzer benötigen ein Benutzerkonto, um sich für die Intune-Geräteverwaltung registrieren zu können.

1. Wählen Sie in Intune **Benutzer** > **Alle Benutzer** > **Neuer Benutzer** aus.
![Browser](media/quickstart-create-user/create-user.png)
2. Geben Sie im Feld **Name** *Dewey Kellum* ein.
3. Geben Sie im Feld **Benutzername** *Dewey@contoso.onmicrosoft.com* ein.
4. Wählen Sie **Gruppen** > **Jeder** > **Auswählen** aus.
5. Klicken Sie auf **Kennwort anzeigen**, und notieren Sie sich das automatisch generierte Kennwort, mit dem Sie sich bei einem Testgerät anmelden können.
6. Wählen Sie **Erstellen** aus.

## <a name="assign-a-license-to-the-user"></a>Zuweisen einer Benutzerlizenz

Nachdem Sie einen Benutzer erstellt haben, müssen Sie diesem über das [Office 365-Portal](http://go.microsoft.com/fwlink/p/?LinkId=698854) eine Intune-Lizenz zuweisen. Wenn ein Benutzer keine Lizenz hat, kann er sein Gerät auch nicht bei Intune registrieren. 

1. Melden Sie sich im [Office 365-Portal](http://go.microsoft.com/fwlink/p/?LinkId=698854) mit den gleichen Anmeldeinformationen an, die Sie auch zur Anmeldung in Intune verwendet haben.
2. Klicken Sie auf **Benutzer** > **Aktive Benutzer**, und wählen Sie den Benutzer aus, den Sie soeben erstellt haben.
3. Wählen Sie unter **Standort** einen Standort für den Benutzer aus.
3. Klicken Sie auf **Produktlizenzen**, und legen Sie **Enterprise Mobility + Security E3** (oder eine andere Ihrer Lizenzen, die Intune einschließt) auf **Ein** fest.
   > [!NOTE]
   > Dadurch wird eine Ihrer Lizenzen für den Benutzer verwendet. Wenn Sie ihre dynamische Umgebung verwenden, können Sie später die Verwendung dieser Lizenz rückgängig machen, um Sie einem echten Benutzer zuzuweisen.
5. Wählen Sie **Speichern** aus.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Wenn Sie diesen Benutzer nicht mehr benötigen, können Sie ihn unter **Benutzer** > **Alle Benutzer** löschen, indem Sie den Benutzer in der Liste auswählen und auf **Benutzer löschen** > **Ja** klicken.

## <a name="next-steps"></a>Nächste Schritte

In dieser Schnellstartanleitung haben Sie einen Benutzer erstellt und diesem eine Lizenz zugewiesen. Nun können Sie den Benutzer einer Gruppe zuweisen.

> [!div class="nextstepaction"]
> [Erstellen einer Gruppe](quickstart-create-group.md)
