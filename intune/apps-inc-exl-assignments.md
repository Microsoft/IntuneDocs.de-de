---
title: "Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune"
titlesuffix: 
description: "Erfahren Sie, wie Sie mit Microsoft Intune App-Zuweisungen ein- und ausschließen können."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dbe8669dc2bf448e0738147758d90ba6d2d69b06
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune

Mithilfe von Intune können Sie bestimmen, wer Zugriff auf eine App hat, indem Sie sowohl die ein- als auch auszuschließenden Gruppen zuweisen. Allerdings müssen Sie den Zuweisungstyp einer App festlegen, bevor Sie dieser Gruppen zuweisen. Der Zuweisungstyp macht die App verfügbar, erforderlich oder deinstalliert diese. 

Wenn Sie sich auf die Verfügbarkeit einer App konzentrieren, schließen Sie mithilfe einer Kombination von Ein- und Ausschlussgruppenzuweisungen App-Zuweisungen für eine Gruppe von Benutzern oder Geräten ein bzw. aus. Diese Funktion kann nützlich sein, wenn Sie die App verfügbar machen, indem Sie eine große Gruppe einschließen und dann die ausgewählten Benutzer auch durch Ausschluss einer kleineren Gruppe einschränken. Die kleinere Gruppe könnte eine Testgruppe oder ausführende Gruppe sein. 

Wenn Sie Gruppen aus einer App-Zuweisung ausschließen, dürfen Sie nur Benutzer oder nur Gerätegruppen ausschließen und keine Kombinationen von Gruppen. Intune berücksichtigt beim Ausschließen von Gruppen keine Zuweisung eines Benutzers zu einem Gerät. Es ist unwahrscheinlich, dass das Einschließen von Benutzergruppen und gleichzeitige Ausschließen von Gerätegruppen die von Ihnen gewünschten Ergebnisse liefert, da das Einschließen vor dem Ausschließen Vorrang hat. Wenn Sie z.B. **Alle Benutzer** eine iOS-App zuweisen und **Alle iPads** ausschließen, kommt dabei heraus, dass jeder Benutzer mit einem iPad weiterhin die Anwendung erhält. Wenn Sie jedoch die iOS-App **Alle Geräte** zuweisen und **Alle iPads** ausschließen, ist die Bereitstellung erfolgreich.  

>[!NOTE]
>Beim Festlegen einer Gruppenzuweisung für eine App ist der Typ **Nicht zutreffend** veraltet und wird mit der Ausschlussgruppenfunktionalität ersetzt. 
>
>Intune bietet die vorab erstellten Gruppen **Alle Benutzer** und **Alle Geräte** in der Konsole zur Vereinfachung mit integrierten Optimierungen an. Sie sollten diese Gruppen unbedingt anstelle möglicherweise selbst erstellter „Alle Benutzer“- oder „Alle Geräte“-Gruppen verwenden, um alle Benutzer und alle Geräte zu erreichen.  

## <a name="including-and-excluding-groups-when-assigning-apps"></a>Ein- und Ausschließen von Gruppen beim Zuweisen von Apps 
So weisen Sie eine App Gruppen mithilfe der Ein- und Ausschlusszuweisung zu:
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie auf dem Blatt Microsoft Intune die Option **Mobile Apps** aus.
4. Wählen Sie auf dem Blatt **Mobile Apps** die Option **Apps** aus. Die Liste der hinzugefügten Apps wird angezeigt.
5. Wählen Sie die App aus, die zugewiesen werden soll. Ein Dashboard wird im Zusammenhang mit der App angezeigt. 
6. Wählen Sie **Zuweisungen** im Abschnitt **Verwalten** aus. 

    ![Intune-App-Zuweisungen](./media/apps-inc-exl-01.png)
7. Wählen Sie **Gruppe hinzufügen** aus, um die Gruppen von Benutzern hinzuzufügen, denen die App zugewiesen wird. 
8. Wählen Sie einen **Zuweisungstyp** aus den verfügbaren Zuweisungstypen im Bereich **Gruppe hinzufügen** aus.
9. Wählen Sie **Verfügbar mit oder ohne Registrierung** als Zuweisungstyp aus.

    ![Intune-App-Zuweisungen – Gruppe hinzufügen](./media/apps-inc-exl-02.png)
10. Wählen Sie **Eingeschlossene Gruppen** aus, um die Gruppe von Benutzern auszuwählen, denen Sie diese App zur Verfügung stellen möchten.

    >[!NOTE]
    >Beachten Sie beim Hinzufügen einer Gruppe: Wenn eine Gruppe bereits für einen bestimmten Zuweisungstyp eingeschlossen wurde, ist diese vorausgewählt und kann nicht mehr für andere Einschlusszuweisungstypen geändert werden. Darum kann die Gruppe, die verwendet wurde, nicht als eingeschlossene Gruppe verwendet werden.

11. Wählen Sie **Ja**, um diese App für alle Benutzer verfügbar zu machen.

    ![Intune-App-Zuweisungen – Gruppen einschließen](./media/apps-inc-exl-03.png)
12. Klicken Sie auf **OK**, um die einzuschließende Gruppe festzulegen.
13. Wählen Sie **Ausgeschlossene Gruppen** aus, um die Gruppen von Benutzern auszuwählen, denen diese App nicht zur Verfügung stehen soll. 
14. Wählen Sie die auszuschließenden Gruppen aus, für die diese App nicht verfügbar ist.

    ![Intune-App-Zuweisungen – Gruppen ausschließen](./media/apps-inc-exl-04.png)
15. Klicken Sie auf **Auswählen**, um Ihre Gruppenauswahl abzuschließen.
16. Klicken Sie auf dem Blatt **Gruppe hinzufügen** auf **OK**. Die Liste der App-**Zuweisungen** wird angezeigt.
17. Klicken Sie auf **Speichern**, um Ihre Gruppenzuweisungen für die App zu aktivieren.

Wenn Sie Gruppenzuweisungen vornehmen, sind Gruppen deaktiviert, die bereits zugewiesen oder ausgewählt wurden. Wenn Sie eine derzeit deaktivierte Gruppe auswählen möchten, entfernen Sie sie aus der „Zugewiesen“-Liste der App. Sie können Zuweisungen in der App-**Zuweisungen**-Liste durch Auswahl der Zeile mit der jeweiligen Zuweisung, die Sie ändern möchten, bearbeiten. Darüber hinaus können Sie eine Zuweisung entfernen, indem Sie auf die Auslassungspunkte (...) am Ende einer Zeile klicken und **Entfernen** auswählen. Außerdem können Sie die Ansicht der Liste **Zuweisungen** ändern, indem Sie die Gruppierung nach **Zuweisungstyp** oder **Eingeschlossen/Ausgeschlossen** auswählen.

![Intune-App-Zuweisungen – Abschluss](./media/apps-inc-exl-05.png)

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zu ein- und ausschließenden Gruppenzuweisungen für Apps finden Sie im [Microsoft Intune-Blog](https://aka.ms/new_app_assignment_process).
- [Überwachen von App-Informationen und -Zuweisungen](apps-monitor.md)