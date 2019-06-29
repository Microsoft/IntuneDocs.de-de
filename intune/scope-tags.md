---
title: Filtern von Richtlinien mit Bereichsmarkierungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie Bereichsmarkierungen, um Konfigurationsprofile nach bestimmten Rollen zu filtern.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba1d7669e80fd91398f41c57ca2d27ce78a06041
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403791"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Verwenden der rollenbasierten Zugriffssteuerung und Bereichsmarkierungen für verteilte IT

Sie können die rollenbasierte Zugriffssteuerung und Bereichsmarkierungen verwenden, um sicherzustellen, dass die richtigen Administratoren über die korrekten Zugriffsrechte und Sichtbarkeit für die entsprechenden Intune-Objekte verfügen. Mit Rollen wird bestimmt, über welchen Zugriff Administratoren auf welche Objekte verfügen. Mit Bereichsmarkierungen wird bestimmt, welche Objekte Administratoren sehen können.

Angenommen, einem Administrator der Bezirksdirektion von Seattle wird die Rolle „Richtlinien- und Profil-Manager“ zugewiesen. Sie möchten, dass dieser Administrator nur die Profile und Richtlinien sieht und verwalten kann, die für Geräte in Seattle gelten. Hierzu müssten Sie folgendermaßen vorgehen:

1. Erstellen Sie eine Bereichsmarkierung namens „Seattle“.
2. Erstellen Sie eine Rollenzuweisung für die Rolle „Richtlinien- und Profil-Manager“ mit: 
    - Mitglieder (Gruppen): Eine Sicherheitsgruppe namens „Seattle-IT-Administratoren“. Alle Administratoren in dieser Gruppe verfügen über die Berechtigung zum Verwalten von Richtlinien und Profilen für Benutzer/Geräte im Bereich (Gruppen).
    - Mitglieder (Gruppen): Eine Sicherheitsgruppe namens „Seattle-Benutzer“. Alle Benutzer/Geräte in dieser Gruppe können über ihre eigenen Profile und Richtlinien verfügen, die von den Administratoren in Mitglieder (Gruppen) verwaltet werden. 
    - Bereich (Markierungen): Seattle. Die Administratoren in Mitglieder (Gruppen) können Geräte sehen, die ebenfalls über die Bereichsmarkierung „Seattle“ verfügen.
3. Fügen Sie die Seattle-Bereichsmarkierung zu Richtlinien und Profilen hinzu, auf die Administratoren in Mitglieder (Gruppen) zugreifen können sollen.
4. Fügen Sie die Seattle-Bereichsmarkierung zu Geräten hinzu, die für Administratoren in Mitglieder (Gruppen) sichtbar sein sollen. 


## <a name="to-create-a-scope-tag"></a>So erstellen Sie eine Bereichsmarkierung

1. Klicken Sie in Intune auf **Rollen** > **Bereich (Markierungen)**  > **Erstellen**.

    ![Screenshot: Erstellen einer Bereichsmarkierung](./media/scope-tags/create-scope-tag.png)

3. Wenn Sie alle Geräte in bestimmten Gruppen möchten, wählen Sie **bereichsmarkierung für alle Geräte in der ausgewählten Gruppen zuweisen**.
    1. In der **einzuschließende Gruppen auswählen** Seite, wählen Sie die Gruppen, enthält die Geräte, die Sie dieser bereichsmarkierung, zuweisen möchten.
    2. Klicken Sie auf **Auswählen**.
4. Wählen Sie **Erstellen** aus.

## <a name="to-assign-a-scope-tag-to-a-role"></a>So weisen Sie einer Rolle eine Bereichsmarkierung zu

1. Klicken Sie in Intune auf **Rollen** > **Alle Rollen**, wählen Sie eine Rolle aus, und klicken Sie dann auf **Zuweisungen** > **Zuweisen**.

    ![Screenshot: Zuweisen des Bereichs zu einer Rolle](./media/scope-tags/assign-scope-to-role.png)

2. Geben Sie einen **Zuweisungsnamen** und eine **Beschreibung** an.
3. Klicken Sie auf **Mitglieder (Gruppen)**  > **Hinzufügen**, wählen Sie die Gruppen aus, die Sie als Teil dieser Zuweisung verwenden möchten, und klicken Sie dann auf **Auswählen** > **OK**. Die Benutzer in dieser Gruppe verfügen über die Berechtigungen zum Verwalten von Richtlinien und Profilen für Benutzer/Geräte im Bereich (Gruppen).

    ![Screenshot: Benutzergruppen auswählen](./media/scope-tags/select-member-groups.png)

4. Wenn Sie die Benutzer/Geräte bestimmter Gruppen verwalten möchten, klicken Sie auf **Bereich (Gruppen)**  > **Ausgewählte Gruppen** > **Select groups to include** (Einzuschließende Gruppen auswählen), wählen Sie die Gruppen aus, und klicken Sie dann auf **Auswählen** > **OK**. Alle Benutzer/Geräte in dieser Gruppe können über ihre eigenen Profile und Richtlinien verfügen, die von den Administratoren in Mitglieder (Gruppen) verwaltet werden.

    ![Screenshot: Bereichsgruppen auswählen](./media/scope-tags/select-scope-groups.png)

    Alternativ können Sie **Alle Geräte**, **Alle Benutzer** oder **All Users & All Devices**. (Alle Benutzer & Alle Geräte) auswählen.

    ![Screenshot: Weitere Optionen zum Auswählen von Bereichsgruppen](./media/scope-tags/scope-group-other-options.png)
    
5. Klicken Sie auf **Bereich (Markierungen)**  > **Hinzufügen**, wählen Sie die Markierungen aus, die Sie zur Rolle hinzufügen möchten, und klicken Sie dann auf **Auswählen** > **OK**. Dadurch erhalten Benutzer in Mitglieder (Gruppen) Zugriff auf die Richtlinien und Profile, die dieselbe Bereichsmarkierung aufweisen.

    ![Screenshot: Bereichsmarkierungen auswählen](./media/scope-tags/select-scope-tags.png)

6. Wählen Sie **OK** aus. 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>So fügen Sie eine Bereichsmarkierung einem Konfigurationsprofil hinzu
1. Klicken Sie in Intune auf **Gerätekonfiguration** > **Profile**, und wählen Sie ein Profil aus.

    ![Screenshot: Profil auswählen](./media/scope-tags/choose-profile.png)

2. Klicken Sie auf **Eigenschaften** > **Bereich (Markierungen)**  > **Hinzufügen**.

    ![Screenshot: Bereichsmarkierungen hinzufügen](./media/scope-tags/add-scope-tags.png)

3. Wählen Sie unter **Markierungen auswählen** die Markierungen aus, die Sie zum Profil hinzufügen möchten.
4. Klicken Sie auf **Auswählen** > **OK** > **Speichern**.

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>Zuweisen einer Bereichsmarkierung zu einer App-Konfigurationsrichtlinie
Geräte mit **Verwaltete Geräte** als **Geräteregistrierungstyp**:
1. Klicken Sie auf **Client-Apps** > **App-Konfigurationsrichtlinien**, und wählen Sie eine App-Konfigurationsrichtlinie aus.
2. Klicken Sie auf **Eigenschaften** > **Bereich (Markierungen)** , und wählen Sie die Markierungen aus, die Sie der Richtlinie zuweisen möchten.

Geräte mit **Verwaltete Apps** als **Geräteregistrierungstyp**:
1. Klicken Sie auf **Client-Apps** > **App-Konfigurationsrichtlinien**, und wählen Sie eine App-Konfigurationsrichtlinie aus.
2. Klicken Sie auf **Bereich (Markierungen)** , und wählen Sie die Markierungen aus, die Sie der Richtlinie zuweisen möchten.


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>Zuweisen einer Bereichsmarkierung zu einem iOS-App-Bereitstellungsprofil
1. Klicken Sie in Intune auf **Client-Apps** > **iOS-App-Bereitstellungsprofile**, und wählen Sie ein Profil aus.
2. Klicken Sie auf **Eigenschaften** > **Bereich (Markierungen)** , und wählen Sie die Markierungen aus, die Sie dem Profil zuweisen möchten.
3. Klicken Sie auf **Auswählen** > **OK** > **Speichern**.

## <a name="to-assign-a-scope-tag-to-an-apple-volume-purchase-program-vpp-token"></a>Zuweisen einer Bereichsmarkierung zu einem Apple Volume Purchase Program-Token (VPP)
1. Klicken Sie in Intune auf **Client-Apps** > **Apple-VPP-Token**, und wählen Sie ein VPP-Token aus.
2. Klicken Sie auf **Bereich (Markierungen)** , und wählen Sie die Markierungen aus, die Sie dem Profil zuweisen möchten. Die VPP-Apps und E-Books, die dem VPP-Token zugeordnet sind, erben die zugewiesenen Markierungen.
3. Klicken Sie auf **Auswählen** > **OK** > **Speichern**.

## <a name="scope-tag-details"></a>Informationen zu Bereichsmarkierungen
Bei der Arbeit mit Bereichsmarkierungen sollten Sie Folgendes beachten:

- Derzeit können Sie Folgendem Bereichsmarkierungen zuweisen:
    - Rollenzuweisungen
    - Gerätekompatibilitätsrichtlinien
    - Gerätekonfigurierungsprofile
    - Windows 10-Updateringe
    - Verwaltete Geräte
    - Apps
    - App-Konfigurationsrichtlinien – verwaltete Geräte
    - PowerShell-Skripts
    - DEP-Token
    - Bereitstellungsprofil für iOS-Apps
    - Volume Purchase Program-Token (VPP)
- Wenn ein Administrator ein Objekt in Intune erstellt, werden alle Bereichsmarkierungen, die diesem Administrator zugewiesen sind, automatisch dem neuen Objekt zugewiesen.
- Die rollenbasierte Zugriffssteuerung von Intune gilt nicht für Azure Active Directory-Rollen. Intune-Dienstadministratoren und globale Administratoren verfügen unabhängig von ihren Bereichsmarkierungen über vollständigen Administratorzugriff auf Intune.
- Administratoren in einer Rollenzuweisung mit Bereichsmarkierungen können auch Intune-Objekte sehen, denen keine Bereichsmarkierungen zugewiesen sind.
- Sie können nur Bereichsmarkierungen zuweisen, die in Ihren Rollenzuweisungen enthalten sind.
- Sie können nur Zielgruppen verwenden, die in Bereich (Gruppen) Ihrer Rollenzuweisung enthalten sind.
- Wenn Ihrer Rolle eine Bereichsmarkierung zugewiesen ist, können Sie nicht alle Bereichsmarkierungen eines Intune-Objekts löschen. Mindestens eine Bereichsmarkierung ist erforderlich.

## <a name="next-steps"></a>Nächste Schritte

Verwalten Sie Ihre [Rollen](role-based-access-control.md) und [Profile](device-profile-assign.md).
