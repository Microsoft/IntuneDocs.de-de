---
title: Erstellen von Gruppen zum Organisieren von Benutzern und Geräten
description: Erstellen von Benutzern und Gruppen für Ihr Intune-Abonnement
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 02/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5fdf98c8-fe67-4d7a-9837-ed1234348014
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f8590fc524e770536a66c604add2ce82d0c28afc
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="create-groups-to-organize-users-and-devices"></a>Erstellen von Gruppen zum Organisieren von Benutzern und Geräten

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

In diesem Thema erfahren Administratoren, wie sie Benutzergruppen in Intune erstellen können.

Mit Gruppen erhalten Sie in Intune maximale Flexibilität beim Verwalten Ihrer Geräte und Benutzer. Sie können Gruppen einrichten, die Ihren organisatorischen Anforderungen (z. B. nach geografischem Standort, nach Abteilung oder nach Hardwareeigenschaften) entsprechen und diese dazu verwenden, um eine Vielzahl von Verwaltungsaufgaben ausführen, die von der Bereitstellung von Richtlinien für eine Gruppe von Benutzern bis zur Bereitstellung von Anwendungen auf einer Reihe von Geräten reichen.

## <a name="group-management-moving-to-azure-ad"></a>Gruppenverwaltung wechselt zu Azure AD

**Ab November 2016** erfolgt die Verwaltung von Benutzer- und Gerätegruppen für neue Konten im Azure Active Directory-Portal (Azure AD). Im Dezember 2016 beginnt das Intune-Produktteam mit der Migration von Bestandskunden zur neuen Azure AD-basierten Gruppenverwaltungsoberfläche. Alle Benutzer- und -Gerätegruppen werden zu Azure AD-Sicherheitsgruppen migriert. Mit den Migrationen wird erst begonnen, wenn wir die Auswirkungen auf Ihre alltägliche Arbeit auf ein Minimum beschränken und erwarten können, dass Auswirkungen auf Ihre Benutzer ausbleiben. Außerdem benachrichtigen wir Sie, bevor wir Ihr Konto migrieren.


>[!IMPORTANT]
>
>Wenn Sie den Arbeitsbereich „Gruppen“ im Intune-Portal öffnen und dort den Hinweis **Intune-Benutzergruppen werden jetzt als Gruppen in Active Directory verwaltet** mit einem Link zum Azure Active Directory-Portal sehen, verwenden Sie bereits den *neuen* Ansatz für Azure AD-Sicherheitsgruppen für die Gruppenverwaltung in Intune. Informationen zum Erstellen von Gruppen finden Sie unter [Verwalten von Gruppen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
>
>Wenn kein Link zum Azure AD-Portal angezeigt wird, verwenden Sie noch das Intune-Portal für die Gruppenverwaltung.

## <a name="group-management-in-the-intune-portal"></a>Gruppenverwaltung im Intune-Portal

Sowohl Geräte als auch Benutzergruppen werden im Arbeitsbereich „Gruppen“ der Intune-Administratorkonsole erstellt.

![Arbeitsbereich „Gruppen“ der Verwaltungskonsole](./media/groups.png)


> [!TIP]
> Weitere Informationen zum Verwenden von Gruppen finden Sie unter [Erstellen von Gruppen zum Verwalten von Benutzern und Geräten in Microsoft Intune](/intune-classic/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).


## <a name="create-a-device-group"></a>Erstellen einer Gerätegruppe
Verwenden Sie Gerätegruppen zum Bereitstellen von Apps und Updates sowie zum Konfigurieren anderer Features. Richten Sie z. B. die Gruppe „Meine Geräte“ mithilfe der folgenden Schritte ein:

1.  Wählen Sie in der [Intune-Administratorkonsole](https://manage.microsoft.com/) **Gruppen** > **Übersicht** > **Gruppe erstellen** aus.

2.  Geben Sie unter **Gruppenname** „Meine Geräte“ ein, und wählen Sie in der übergeordneten Gruppenliste **Alle Geräte** und anschließend **Weiter** aus.

3.  Wählen Sie **Alle Geräte** auf der Seite **Mitgliedschaftskriterien definieren** aus, um anzugeben, dass die Gruppe sowohl mobile Geräte als auch Computer enthält.

4.  Klicken Sie auf der Seite **Direkte Mitgliedschaft definieren** auf **Weiter**. Hätten Sie zuvor eine Gruppe erstellt, die nicht alle Geräte enthält, und wollten Sie dieser neuen Gruppe nun bestimmte Geräte hinzufügen, dann können Sie dies an dieser Stelle tun.

5.  Überprüfen Sie auf der Seite **Zusammenfassung** die Aktionen, die ausgeführt werden, und wählen Sie anschließend **Fertig stellen** aus.

Sie finden die neue Gruppe in der Liste **Gruppen** im Arbeitsbereich **Gruppen** unter **Alle Geräte**. Hier können Sie die Gruppe auch bearbeiten oder löschen.

## <a name="create-a-user-group"></a>Erstellen einer Benutzergruppe
Verwenden Sie Benutzergruppen, um Software- und Geräterichtlinien bereitzustellen. Richten Sie z. B. die Gruppe „Intune-Benutzer“ mithilfe der folgenden Schritte ein:

1.  Wählen Sie in der [Intune-Administratorkonsole](https://manage.microsoft.com/) **Gruppen** > **Übersicht** > **Gruppe erstellen** aus.

2.  Geben Sie unter **Gruppenname** „Intune-Benutzer“ ein, und wählen Sie aus der übergeordneten Gruppenliste **Alle Benutzer** und anschließend **Weiter** aus.

3.  Setzen Sie auf der Seite **Mitgliedschaftskriterien definieren** die Option **Gruppenmitgliedschaft starten mit** auf **Alle Benutzer in der übergeordneten Gruppe**.

4.  Klicken Sie neben **Mitglieder dieser Sicherheitsgruppen ausschließen** auf **Durchsuchen** und anschließend auf **Unternehmensadministrator**. Durch diesen Ausschluss können Sie die Gruppe „Intune-Benutzer“ verwalten, ohne dass das Konto „Unternehmensadministrator“ (auch als Mandantenadministrator bezeichnet) davon betroffen ist.

5.  Klicken Sie auf der Seite **Direkte Mitgliedschaft definieren** auf **Weiter**. Hier brauchen Sie nichts zu tun, denn die Gruppe „Intune-Benutzer“ soll alle Benutzer außer dem Unternehmensadministrator einschließen.

6.  Überprüfen Sie auf der Seite **Zusammenfassung** die Aktionen, die ausgeführt werden, und wählen Sie anschließend **Fertig stellen** aus.

Sie finden die neue Gruppe in der Liste **Gruppen** im Arbeitsbereich **Gruppen** unter **Alle Benutzer**. Hier können Sie die Gruppe auch bearbeiten oder löschen.

> [!div class="step-by-step"]
> /intune/licenses-assign [&larr; **Verwalten von Intune-Lizenzen**](/intune/licenses-assign)       [**Erstellen von Richtlinien und Apps** &rarr;](./start-with-a-paid-subscription-to-microsoft-intune-step-6.md)  
