---
title: Filtern von Richtlinien mit Bereichsmarkierungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie Bereichsmarkierungen, um Konfigurationsprofile nach bestimmten Rollen zu filtern.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb57ea2ef5c99c58968ee25b3a75b2165ece787a
ms.sourcegitcommit: 0adb41c0640743d5cb726e66ad2427e3ad6faf20
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658548"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Verwenden Sie rollenbasierte Zugriffssteuerung (RBAC) und bereichsmarkierungen für verteilte IT

Sie können rollenbasierten Zugriff Kontrolle und Bereich-Tags verwenden, um sicherzustellen, dass die richtigen Administratoren die richtigen Zugriffsrechte und die Sichtbarkeit auf die richtige Intune-Objekte verfügen. Rollen bestimmen, welche Administratoren haben, auf welche Objekte. Bereichsmarkierungen bestimmen, welche Objekte Administratoren anzeigen können.

Nehmen wir beispielsweise an, dass ein Niederlassung Seattle-Administrator die Richtlinien- und Profil-Manager-Rolle zugewiesen ist. Sie möchten diesen Administrator anzeigen und verwalten nur die Profile und Richtlinien, die nur für Seattle Geräte gelten. Zu diesem Zweck sollen wie folgt vor:

1. Erstellen Sie eine bereichsmarkierung namens Seattle.
2. Erstellen einer rollenzuweisung für die Richtlinien- und Profil-Manager-Rolle mit: 
    - Mitglieder (Gruppen) = eine Sicherheitsgruppe namens Seattle IT-Administratoren. Alle Administratoren in dieser Gruppe werden über die Berechtigung zum Verwalten von Richtlinien und Profile für Benutzer/Geräte im Bereich (Gruppen).
    - Bereich (Gruppen) = ein Gruppe mit dem Namen Seattle Benutzer. Alle Benutzer/Geräte in dieser Gruppe haben ihre Profile und Richtlinien, die von den Administratoren in der Mitglieder (Gruppen) verwaltet werden. 
    - Bereich (Markierungen) = Seattle. Administratoren in der Member (Gruppen) können Geräte anzuzeigen, die außerdem den Seattle bereichsmarkierung verfügen.
3. Hinzufügen der bereichsmarkierung Seattle, Richtlinien und Profile, die Administratoren in Mitglieder (Gruppen) in der Lage, den Zugriff auf sein soll.
4. Fügen Sie der bereichsmarkierung Seattle für Geräte, die Gruppe "Administratoren" in der Mitglieder (Gruppen) angezeigt werden soll. 


## <a name="to-create-a-scope-tag"></a>So erstellen Sie eine Bereichsmarkierung

1. Wählen Sie in Intune **Rollen** > **Bereich (Markierungen)** > **erstellen**.

    ![Screenshot: Erstellen Sie eine bereichsmarkierung.](./media/scope-tags/create-scope-tag.png)

2. Geben Sie einen **Namen** und eine **Beschreibung** an.
3. Wählen Sie **Erstellen** aus.

## <a name="to-assign-a-scope-tag-to-a-role"></a>So weisen Sie einer Rolle eine Bereichsmarkierung zu

1. Wählen Sie in Intune **Rollen** > **alle Rollen** > Wählen Sie eine Rolle > **Zuweisungen** > **weisen**.

    ![Screenshot des Bereichs einer Rolle zuweisen.](./media/scope-tags/assign-scope-to-role.png)

2. Geben Sie eine **Zuweisungsname** und **Beschreibung**.
3. Wählen Sie **Mitglieder (Gruppen)** > **hinzufügen** > Wählen Sie die Gruppen, die im Rahmen dieser Aufgabe sollen > **wählen**  >   **OK**. mUsers in dieser Gruppe haben die Berechtigung zum Verwalten von Richtlinien und Profile für Benutzer/Geräte im Bereich (Gruppen).

    ![Screenshot der select-Elementgruppen.](./media/scope-tags/select-member-groups.png)

4. Wenn Sie Benutzer/Geräte in einem bestimmten Satz von Gruppen verwalten möchten, wählen Sie **Bereich (Gruppen)** > **ausgewählte Gruppen** > **einzuschließendeGruppenauswählen**> Wählen Sie die Gruppen > **wählen** > **OK**. Alle Benutzer/Geräte in dieser Gruppe haben ihre Profile und Richtlinien, die von den Administratoren in die Elemente (Gruppe) verwaltet werden.

    ![Screenshot der Option Bereichsgruppen.](./media/scope-tags/select-scope-groups.png)

    Alternativ können Sie **alle Geräte**, **alle Benutzer**, oder **alle Benutzer und alle Geräte**.

    ![Screenshot der anderen Optionen für die Option Bereichsgruppen.](./media/scope-tags/scope-group-other-options.png)
    
5. Wählen Sie **Bereich (Markierungen)** > **hinzufügen** > Wählen Sie die Tags, die Sie dieser Rolle hinzufügen möchten > **wählen** > **OK**. Benutzer in Mitglieder (Gruppen) müssen den Zugriff auf die Richtlinien und Profile, die außerdem die gleichen bereichsmarkierung verfügen.

    ![Screenshot der Option bereichsmarkierungen.](./media/scope-tags/select-scope-tags.png)

6. Wählen Sie **OK** aus. 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>So fügen Sie eine Bereichsmarkierung einem Konfigurationsprofil hinzu
1. Wählen Sie in Intune **Gerätekonfiguration** > **Profile** > Auswählen eines Profils.

    ![Screenshot der Option-Profil.](./media/scope-tags/choose-profile.png)

2. Wählen Sie **Eigenschaften** > **Bereich (Markierungen)** > **hinzufügen**.

    ![Screenshot des Bereichs Hinzufügen von Tags.](./media/scope-tags/add-scope-tags.png)

3. Klicken Sie unter **Tags auswählen**, wählen Sie die Tags, die Sie zum Profil hinzufügen möchten.
4. Wählen Sie **wählen** > **OK** > **speichern**.

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>Eine app-Konfigurationsrichtlinie eine bereichsmarkierung zuweisen
Für Geräte mit **geräteregistrierungstyp** festgelegt **verwaltete Geräte**:
1. Wählen Sie **Clientanwendungen** > **App-Konfigurationsrichtlinien** > Wählen Sie eine app-Konfigurationsrichtlinie.
2. Wählen Sie **Eigenschaften** > **Bereich (Markierungen)** > Wählen Sie die Tags, die Sie für die Richtlinie zuweisen möchten.

Für Geräte mit **geräteregistrierungstyp** festgelegt **verwaltete apps**:
1. Wählen Sie **Clientanwendungen** > **App-Konfigurationsrichtlinien** > Wählen Sie eine app-Konfigurationsrichtlinie.
2. Wählen Sie **Bereich (Markierungen)** > Wählen Sie die Tags, die Sie für die Richtlinie zuweisen möchten.


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>Eine iOS-app, das Bereitstellungsprofil eine bereichsmarkierung zuweisen
1. Wählen Sie in Intune **Clientanwendungen** > **iOS-app-bereitstellungsprofile** > Auswählen eines Profils.
2. Wählen Sie **Eigenschaften** > **Bereich (Markierungen)** > Wählen Sie die Tags, die Sie dem Profil zuweisen möchten.
3. Wählen Sie **wählen** > **OK** > **speichern**.

## <a name="scope-tag-details"></a>Tag-Details des berechtigungsbereichs
Bei der Arbeit mit bereichsmarkierungen Beachten Sie Folgendes aus:

- Sie können derzeit Bereich Tags zuweisen:
    - Rollenzuweisungen
    - Gerätekompatibilitätsrichtlinien
    - Gerätekonfigurierungsprofile
    - Windows 10-Ringe updates
    - Verwaltete Geräte
    - Apps
    - App-Konfigurationsrichtlinien für verwaltete Geräte
    - PowerShell-Skripts
    - DEP-Token
    - Bereitstellungsprofil für iOS-Apps
- Wenn ein Administrator ein Objekt in Intune erstellt, werden alle bereichsmarkierungen, die den betreffenden Administrator zugewiesen automatisch das neue Objekt zugewiesen werden.
- Intune RBAC gilt nicht für Azure Active Directory-Rollen. Daher haben, die Intune-Dienstadministratoren Gruppenverwaltungsaufgaben und globale Administratoren von Rollen vollständigen Administratorzugriff auf Intune unabhängig davon, welche bereichsmarkierungen, sie haben.
- Administratoren in einer rollenzuweisung mit bereichsmarkierungen können auch keine bereichsmarkierungen Intune Objekten anzeigen.
- Sie können nur eine bereichsmarkierung zuweisen, die Sie in Ihren rollenzuweisungen verfügen.
- Sie können nur für den Zielgruppen, die im Bereich (Gruppen) der rollenzuweisung aufgeführt sind.
- Wenn Sie eine bereichsmarkierung für Ihre Rolle zugewiesen haben, kann nicht alle bereichsmarkierungen für ein Intune-Objekt gelöscht werden. Mindestens eine bereichsmarkierung ist erforderlich.

## <a name="next-steps"></a>Nächste Schritte

Verwalten Sie Ihre [Rollen](role-based-access-control.md) und [Profile](device-profile-assign.md).
