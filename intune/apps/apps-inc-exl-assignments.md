---
title: Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie mit Microsoft Intune App-Zuweisungen ein- und ausschließen können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f073c8ad7a8e087a791ee756683011fac6947162
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547967"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune

In Intune können Sie bestimmen, wer Zugriff auf eine App hat, indem Sie sowohl die ein- als auch auszuschließenden Gruppen von Benutzern zuweisen. Bevor Sie der App Gruppen zuweisen, müssen Sie den Zuweisungstyp einer App festlegen. Der Zuweisungstyp macht die App verfügbar, erforderlich oder deinstalliert diese. 

Um die Verfügbarkeit einer App festzulegen, schließen Sie mithilfe einer Kombination von Ein- und Ausschlussgruppenzuweisungen App-Zuweisungen für eine Gruppe von Benutzern oder Geräten ein bzw. aus. Diese Funktion kann nützlich sein, wenn Sie die App verfügbar machen, indem Sie eine große Gruppe einschließen und dann die ausgewählten Benutzer auch durch Ausschluss einer kleineren Gruppe einschränken. Die kleinere Gruppe könnte eine Testgruppe oder ausführende Gruppe sein. 

Es wird empfohlen, Apps speziell für Ihre Benutzergruppen und separat für Ihre Gerätegruppen zu erstellen und zuzuweisen. Weitere Informationen zu Gruppen finden Sie unter [Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten](~/fundamentals/groups-add.md).  

Das Einschließen und Ausschließen von App-Zuweisungen sind wichtige Szenarios:

- Der Ausschluss hat in folgenden Szenarien für denselben Gruppentyp Vorrang vor der Einbeziehung:
    - Einschließen von Benutzergruppen und Ausschließen von Benutzergruppen beim Zuweisen von Apps
    - Einschließen von Gerätegruppen und Ausschließen von Gerätegruppen beim Zuweisen von Apps

    Wenn Sie z. B. eine Gerätegruppe der Benutzergruppe **All corporate users** (Alle Unternehmensbenutzer) zuweisen, jedoch Mitglieder der Benutzergruppe **Senior Management Staff** (Mitarbeiter des oberen Managements) ausschließen, erhalten **Alle Unternehmensbenutzer** mit Ausnahme der **Mitarbeiter des oberen Managements** die Zuweisung, da beide Gruppen Benutzergruppen sind.
- Intune bewertet keine Beziehungen zwischen Benutzer- und Gerätegruppen. Wenn Sie Apps gemischten Gruppen zuweisen, entsprechen die Ergebnisse möglicherweise nicht Ihren Erwartungen.

    Wenn Sie beispielsweise der Benutzergruppe **Alle Benutzer** eine Gerätegruppe zuweisen, jedoch eine Gerätegruppe **Alle persönlichen Geräte** ausschließen. In dieser gemischten Gruppen-App-Zuweisung erhalten **Alle Benutzer** die App. Der Ausschluss wird nicht angewendet.

Daher wird das Zuweisen von Apps zu gemischten Gruppen nicht empfohlen.

> [!NOTE]
> Wenn Sie eine Gruppenzuweisung für eine App festlegen, ist der Typ **Nicht zutreffend** veraltet und wird mit der Ausschlussgruppenfunktionalität ersetzt. 
>
> Intune bietet die vorab erstellten Gruppen **Alle Benutzer** und **Alle Geräte** in der Konsole an. Die Gruppen verfügen der Einfachheit halber über integrierte Optimierungen. Sie sollten diese Gruppen unbedingt anstelle möglicherweise selbst erstellter „Alle Benutzer“- oder „Alle Geräte“-Gruppen verwenden, um alle Benutzer und alle Geräte zu erreichen.  
>
> Android Enterprise unterstützt das Einschließen und Ausschließen von Gruppen. Sie können die integrierten Gruppen **Alle Benutzer** und **Alle Geräte** für die Android Enterprise-App-Zuweisung nutzen. 

## <a name="include-and-exclude-groups-when-assigning-apps"></a>Ein- und Ausschließen von Gruppen beim Zuweisen von Apps 
So weisen Sie eine App Gruppen mithilfe der Ein- und Ausschlusszuweisung zu:
1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** **Client-Apps** aus.
4. Wählen Sie im Bereich **Client-Apps** die Option **Apps** aus. Die Liste der hinzugefügten Apps wird angezeigt.
5. Wählen Sie die App aus, die zugewiesen werden soll. In einem Dashboard werden Informationen zu der App angezeigt. 
6. Wählen Sie im Abschnitt **Verwalten** des Menüs **Zuweisungen** aus. 

    ![Einschließen von App-Zuweisungen beim Zuweisen von Apps](./media/apps-inc-exl-assignments/apps-inc-exl-01.png)
7. Wählen Sie **Gruppe hinzufügen** aus, um die Gruppen von Benutzern hinzuzufügen, denen die App zugewiesen wird. 
8. Wählen Sie im Bereich **Gruppe hinzufügen** einen **Zuweisungstyp** aus den verfügbaren Zuweisungstypen aus.
9. Wählen Sie als Zuweisungstyp **Verfügbar mit oder ohne Registrierung** aus.

    ![Intune-App-Zuweisungen – Gruppe hinzufügen](./media/apps-inc-exl-assignments/apps-inc-exl-02.png)
10. Wählen Sie **Eingeschlossene Gruppen** aus, um die Gruppe von Benutzern auszuwählen, denen Sie diese App zur Verfügung stellen möchten.

    > [!NOTE]
    > Beachten Sie beim Hinzufügen einer Gruppe Folgendes: Wenn eine andere Gruppe bereits für einen bestimmten Zuweisungstyp eingeschlossen wurde, ist die App vorausgewählt und kann für andere Einschlusszuweisungstypen nicht mehr geändert werden. Die Gruppe, die verwendet wurde, kann nicht als eingeschlossene Gruppe verwendet werden.

11. Wählen Sie **Ja**, um diese App für alle Benutzer verfügbar zu machen.

    ![Intune-App-Zuweisungen – Gruppen einschließen](./media/apps-inc-exl-assignments/apps-inc-exl-03.png)
12. Wählen Sie **OK** aus, um die einzuschließende Gruppe festzulegen.
13. Wählen Sie **Ausgeschlossene Gruppen** aus, um die Gruppen von Benutzern auszuwählen, denen diese App nicht zur Verfügung stehen soll. 
14. Wählen Sie die auszuschließenden Gruppen aus. Damit ist diese App für diese Gruppen nicht verfügbar.

    ![Intune-App-Zuweisungen – Gruppen ausschließen](./media/apps-inc-exl-assignments/apps-inc-exl-04.png)
15. Wählen Sie **Auswählen** aus, um Ihre Gruppenauswahl abzuschließen.
16. Wählen Sie im Bereich **Gruppe hinzufügen** die Option **OK** aus. Die Liste der App-**Zuweisungen** wird angezeigt.
17. Klicken Sie auf **Speichern**, um Ihre Gruppenzuweisungen für die App zu aktivieren.

Wenn Sie Gruppenzuweisungen vornehmen, können Gruppen, die bereits zugewiesen wurden, nicht geändert werden. Wenn Sie eine derzeit deaktivierte Gruppe auswählen möchten, entfernen Sie zuerst die App aus der „Zugewiesen“-Liste der App. 

Um Zuweisungen zu bearbeiten, wählen Sie in der App-**Zuweisungen**-Liste die Zeile mit der jeweiligen Zuweisung aus, die Sie ändern möchten. Sie können eine Zuweisung auch entfernen, indem Sie die Auslassungspunkte ( **...** ) am Ende einer Zeile und dann **Entfernen** auswählen. Um die Ansicht der Liste **Zuweisungen** zu ändern, gruppieren Sie nach **Zuweisungstyp** oder **Eingeschlossen/Ausgeschlossen**.

![Intune-App-Zuweisungen – Abschluss](./media/apps-inc-exl-assignments/apps-inc-exl-05.png)

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zu ein- und ausschließenden Gruppenzuweisungen für Apps finden Sie im [Microsoft Intune-Blog](https://aka.ms/new_app_assignment_process).
- Weitere Informationen zum [Überwachen von App-Informationen und -Zuweisungen](apps-monitor.md).
