---
title: Verwenden der rollenbasierten Zugriffs Steuerung (Role-Based Access Control, RBAC) und Bereichs Tags für die verteilte IT in InTune | Microsoft-Dokumentation
description: Verwenden Sie Bereichsmarkierungen, um Konfigurationsprofile nach bestimmten Rollen zu filtern.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.assetid: a21d3039-f2ed-4f43-b6fa-d00c071edbc4
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b92dca399afeb035bf58d998efdd469318de389
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504943"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Verwenden der rollenbasierten Zugriffssteuerung und Bereichsmarkierungen für verteilte IT

Sie können die rollenbasierte Zugriffssteuerung und Bereichsmarkierungen verwenden, um sicherzustellen, dass die richtigen Administratoren über die korrekten Zugriffsrechte und Sichtbarkeit für die entsprechenden Intune-Objekte verfügen. Mit Rollen wird bestimmt, über welchen Zugriff Administratoren auf welche Objekte verfügen. Mit Bereichsmarkierungen wird bestimmt, welche Objekte Administratoren sehen können.

Angenommen, ein Administrator der Bezirksdirektion von Seattle hat die Rolle „Richtlinien- und Profil-Manager“. Sie möchten, dass dieser Administrator nur die Profile und Richtlinien sieht und verwalten kann, die für Geräte in Seattle gelten. Um diesen Zugriff einzurichten, würden Sie Folgendes tun:

1. Erstellen Sie eine Bereichsmarkierung namens „Seattle“.
2. Erstellen Sie eine Rollenzuweisung für die Rolle „Richtlinien- und Profil-Manager“ mit: 
    - Mitglieder (Gruppen): Eine Sicherheitsgruppe namens „Seattle-IT-Administratoren“. Alle Administratoren in dieser Gruppe verfügen über die Berechtigung zum Verwalten von Richtlinien und Profilen für Benutzer/Geräte im Bereich (Gruppen).
    - Mitglieder (Gruppen): Eine Sicherheitsgruppe namens „Seattle-Benutzer“. Alle Benutzer/Geräte in dieser Gruppe können über ihre eigenen Profile und Richtlinien verfügen, die von den Administratoren in Mitglieder (Gruppen) verwaltet werden. 
    - Bereich (Markierungen): Seattle. Die Administratoren in Mitglieder (Gruppen) können Intune-Objekte sehen, die ebenfalls über die Bereichsmarkierung „Seattle“ verfügen.
3. Fügen Sie die Seattle-Bereichsmarkierung Richtlinien und Profilen hinzu, auf die Administratoren in Mitglieder (Gruppen) zugreifen können sollen.
4. Fügen Sie die Seattle-Bereichsmarkierung zu Geräten hinzu, die für Administratoren in Mitglieder (Gruppen) sichtbar sein sollen. 

## <a name="default-scope-tag"></a>Standardbereichsmarkierung
Das Standard Bereichs Kennzeichen wird automatisch allen nicht markierten Objekten hinzugefügt, die Bereichs Tags unterstützen.

Das Feature Standardbereichsmarkierung ähnelt dem Feature für Sicherheitsbereiche in System Center Configuration Manager. 

## <a name="to-create-a-scope-tag"></a>So erstellen Sie eine Bereichsmarkierung

1. Klicken Sie in Intune auf **Rollen** > **Bereich (Markierungen)**  > **Erstellen**.

    ![Screenshot: Erstellen einer Bereichsmarkierung](./media/scope-tags/create-scope-tag.png)

3. Wenn Sie alle Geräte in bestimmten Gruppen möchten, wählen Sie **bereichstag allen Geräten in ausgewählten Gruppen zuweisen aus**.
    1. Wählen Sie auf der Seite **Wählen Sie die einzuschließenden Gruppen** aus die Gruppen mit den Geräten aus, denen dieses bereichstag zugewiesen werden soll.
    2. Klicken Sie auf **Auswählen**.
4. Wählen Sie **Erstellen** aus.

## <a name="to-assign-a-scope-tag-to-a-role"></a>So weisen Sie einer Rolle eine Bereichsmarkierung zu

1. Klicken Sie in Intune auf **Rollen** > **Alle Rollen**, wählen Sie eine Rolle aus, und klicken Sie dann auf **Zuweisungen** > **Zuweisen**.

    ![Screenshot: Zuweisen des Bereichs zu einer Rolle](./media/scope-tags/assign-scope-to-role.png)

2. Geben Sie einen **Zuweisungsnamen** und eine **Beschreibung** an.
3. Klicken Sie auf **Mitglieder (Gruppen)**  > **Hinzufügen**, wählen Sie die Gruppen aus, die Sie als Teil dieser Zuweisung verwenden möchten, und klicken Sie dann auf **Auswählen** > **OK**. Benutzer in dieser Gruppe verfügen über Berechtigungen zum Verwalten von Benutzern und Geräten im Bereich (Gruppen).

    ![Screenshot: Benutzergruppen auswählen](./media/scope-tags/select-member-groups.png)

4. Wenn Sie die Benutzer/Geräte bestimmter Gruppen verwalten möchten, klicken Sie auf **Bereich (Gruppen)**  > **Ausgewählte Gruppen** > **Select groups to include** (Einzuschließende Gruppen auswählen), wählen Sie die Gruppen aus, und klicken Sie dann auf **Auswählen** > **OK**. Alle Benutzer/Geräte in dieser Gruppe werden von den Administratoren in den Mitgliedern (Gruppe) verwaltet.

    ![Screenshot: Bereichsgruppen auswählen](./media/scope-tags/select-scope-groups.png)

    Alternativ können Sie **Alle Geräte**, **Alle Benutzer** oder **All Users & All Devices**. (Alle Benutzer & Alle Geräte) auswählen.

    ![Screenshot: Weitere Optionen zum Auswählen von Bereichsgruppen](./media/scope-tags/scope-group-other-options.png)
    
5. Klicken Sie auf **Bereich (Markierungen)**  > **Hinzufügen**, wählen Sie die Markierungen aus, die Sie zur Rolle hinzufügen möchten, und klicken Sie dann auf **Auswählen** > **OK**. Benutzer in Mitgliedern (Gruppen) haben Zugriff auf InTune-Objekte, die ebenfalls über das gleiche bereichstag verfügen.

    ![Screenshot: Bereichsmarkierungen auswählen](./media/scope-tags/select-scope-tags.png)

6. Wählen Sie **OK** aus. 

## <a name="assign-scope-tags-to-other-objects"></a>Zuweisen von Bereichs Tags zu anderen Objekten

Bei Objekten, die Bereichs Tags unterstützen, werden Bereichs Markierungen normalerweise unter **Eigenschaften**angezeigt. Gehen Sie z. b. folgendermaßen vor, um einem Konfigurations Profil ein Bereichs Kennzeichen zuzuweisen:

1. Klicken Sie in Intune auf **Gerätekonfiguration** > **Profile**, und wählen Sie ein Profil aus.

    ![Screenshot: Profil auswählen](./media/scope-tags/choose-profile.png)

2. Klicken Sie auf **Eigenschaften** > **Bereich (Markierungen)**  > **Hinzufügen**.

    ![Screenshot: Bereichsmarkierungen hinzufügen](./media/scope-tags/add-scope-tags.png)

3. Wählen Sie unter **Markierungen auswählen** die Markierungen aus, die Sie zum Profil hinzufügen möchten.
4. Klicken Sie auf **Auswählen** > **OK** > **Speichern**.


## <a name="scope-tag-details"></a>Informationen zu Bereichsmarkierungen
Bei der Arbeit mit Bereichsmarkierungen sollten Sie Folgendes beachten: 

- Sie können einem InTune-Objekttyp Bereichs Tags zuweisen, wenn der Mandant mehrere Versionen dieses Objekts (z. b. Rollenzuweisungen oder Apps) aufweisen kann.
  Die folgenden InTune-Objekte sind Ausnahmen zu dieser Regel und unterstützen derzeit keine Bereichs Tags:
    - Windows-ESP-profile
    - Gerätekategorien
    - Registrierungseinschränkungen
    - Corp-Geräte Bezeichner
    - Autopilot-Geräte
    - Geräte Konformitäts Orte
    - JAMF-Geräte
- VPP-apps und die dem VPP-Token zugeordneten eBooks erben die dem zugeordneten VPP-Token zugewiesenen Bereichs Tags.
- Programm zur Geräteregistrierung (DEP)-Geräte und DEP-Profile, die dem DEP-Token zugeordnet sind, erben die dem zugeordneten DEP-Token zugewiesenen Bereichs Tags.
- Wenn ein Administrator ein Objekt in Intune erstellt, werden alle Bereichsmarkierungen, die diesem Administrator zugewiesen sind, automatisch dem neuen Objekt zugewiesen.
- Die rollenbasierte Zugriffssteuerung von Intune gilt nicht für Azure Active Directory-Rollen. Intune-Dienstadministratoren und globale Administratoren verfügen unabhängig von ihren Bereichsmarkierungen über vollständigen Administratorzugriff auf Intune.
- Wenn für eine Rollenzuweisung kein bereichstag vorhanden ist, kann der IT-Administrator alle Objekte auf der Grundlage der IT-Administratoren anzeigen. Administratoren ohne Bereichs Tags verfügen im Wesentlichen über alle Bereichs Tags.
- Sie können nur Bereichsmarkierungen zuweisen, die in Ihren Rollenzuweisungen enthalten sind.
- Sie können nur Zielgruppen verwenden, die in Bereich (Gruppen) Ihrer Rollenzuweisung enthalten sind.
- Wenn Ihrer Rolle eine Bereichsmarkierung zugewiesen ist, können Sie nicht alle Bereichsmarkierungen eines Intune-Objekts löschen. Mindestens eine Bereichsmarkierung ist erforderlich.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie sich Bereichs Tags Verhalten, wenn [mehrere Rollenzuweisungen](role-based-access-control.md#multiple-role-assignments)vorhanden sind.
Verwalten Sie Ihre [Rollen](role-based-access-control.md) und [Profile](../configuration/device-profile-assign.md).
