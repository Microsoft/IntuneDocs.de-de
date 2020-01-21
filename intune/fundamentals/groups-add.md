---
title: Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten
titleSuffix: Microsoft Intune
description: Fügen Sie Gruppen zum Organisieren von Benutzern und Geräten nach Geografie, Abteilung oder nach Hardwareeigenschaften hinzu.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 237eca2f8e00f00fda5fa3cf401be87de9602743
ms.sourcegitcommit: de663ef5f3e82e0d983899082a7f5b62c63f24ef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "75956257"
---
# <a name="add-groups-to-organize-users-and-devices"></a>Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten

Intune verwendet Azure Active Directory-Gruppen (Azure AD) zur Verwaltung von Geräten und Benutzern. Als Intune-Administrator können Sie Gruppen entsprechend der Anforderungen Ihrer Organisation einrichten. Sie können Gruppen erstellen, um Benutzer oder Geräte nach geografischem Standort, Abteilung oder Hardwareeigenschaften zu organisieren. Sie können Gruppen zur bedarfsgerechten Verwaltung von Aufgaben verwenden. So können Sie beispielsweise Richtlinien für viele Benutzer festlegen oder Apps für mehrere Geräte bereitstellen.

Sie können die folgenden Gruppentypen hinzufügen:

- **Zugewiesene Gruppen:** Fügen Sie manuell Benutzer oder Geräten zu einer statischen Gruppe hinzu. 
- **Dynamische Gruppen** (erfordert Azure AD Premium): Lassen Sie automatisch auf Basis eines von Ihnen erstellen Ausdrucks Benutzer oder Geräte zu Benutzer- oder Gerätegruppen hinzufügen.

  Wenn z. B. ein Benutzer mit dem Titel „Manager“ hinzugefügt wird, wird er automatisch der Benutzergruppe **Alle Manager** hinzugefügt. Wenn ein Gerät hingegen den Betriebssystemtyp „iOS-Gerät“ aufweist, wird es automatisch zur Benutzergruppe **Alle iOS-Geräte** hinzugefügt.

## <a name="add-a-new-group"></a>Hinzufügen einer neuen Gruppe

Führen Sie die folgenden Schritte aus, um eine neue Gruppe zu erstellen:

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Klicken Sie auf **Gruppen** > **Neue Gruppe**:

   ![Screenshot: Azure-Portal, Option „Neue Gruppe“ ausgewählt](./media/groups-add/groups-add-new.png)

3. Wählen Sie unter **Gruppentyp** eine der folgenden Optionen aus:

    - **Sicherheit**: Mithilfe von Sicherheitsgruppen wird definiert, wer auf Ressourcen zugreifen kann. Sie sollten sie für Ihre Gruppen in Intune verwenden. Sie können einerseits Gruppen für Benutzer erstellen, z. B. **Alle Mitarbeiter in Charlotte** oder **Remotemitarbeiter**. Zum Anderen können Sie auch Gruppen für Geräte erstellen, z. B. **Alle iOS-Geräte** oder **Alle Geräte von Schülern mit Windows 10**.

        > [!TIP]
        > Die erstellten Benutzer und Gruppen können auch im [Microsoft 365 Admin Center](https://admin.microsoft.com), im Azure Active Directory Admin Center und im [Azure-Portal unter Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2090973) angezeigt werden. Im Organisationsmandanten können Sie Gruppen in all diesen Bereichen erstellen und verwalten.
        >
        > Wenn Sie in erster Linie für die Geräteverwaltung verantwortlich sind, sollten Sie das [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) verwenden.

    - **Office 365:** Bietet Möglichkeiten zur Zusammenarbeit, indem Mitglieder Zugriff auf freigegebene Postfächer, Kalender, Dateien, SharePoint-Websites und mehr erhalten. Mit dieser Option können Sie auch Personen außerhalb Ihrer Organisation Zugriff auf die Gruppe gewähren. Weitere Informationen zu Office 365-Gruppen finden Sie unter [diesem Link](https://support.office.com/article/learn-about-office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).

4. Geben Sie einen **Gruppennamen** und eine **Gruppenbeschreibung** für die neue Gruppe ein. Seien Sie konkret, und fügen Sie Informationen hinzu, anhand derer andere Benutzer erkennen können, wofür die Gruppe vorgesehen ist.

    Geben Sie beispielsweise **Alle Geräte von Schülern mit Windows 10** als Gruppennamen und **Alle Windows 10-Geräte, die von Schülern der Klassen 9–12 der High School Contoso verwendet werden** als Gruppenbeschreibung ein.

5. Geben Sie den **Mitgliedschaftstyp** ein. Folgende Optionen sind verfügbar:

    - **Zugewiesen:** Administratoren weisen dieser Gruppe manuell Benutzer oder Geräte hinzu und entfernen sie auch manuell wieder.
    - **Dynamischer Benutzer:** Administratoren erstellen Mitgliedschaftsregeln, um Mitglieder automatisch hinzufügen und entfernen zu lassen.
    - **Dynamisches Gerät:** Administratoren erstellen Regeln für dynamische Gruppen, um Geräte automatisch hinzufügen und entfernen zu lassen.

        ![Screenshot der Intune-Gruppeneigenschaften](./media/groups-add/groups-add-properties.png)

    Weitere Informationen zu diesen Mitgliedschaftstypen und zum Erstellen dynamischer Ausdrücke finden Sie unter:

    - [Erstellen einer Basisgruppe und Hinzufügen von Mitgliedern mithilfe von Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    - [Regeln für eine dynamische Mitgliedschaft für Gruppen in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)

    > [!NOTE]
    > Wenn Sie in diesem Admin Center Benutzer oder Gruppen erstellen, wird das **Azure Active Directory**-Branding möglicherweise nicht angezeigt. Sie verwenden aber trotzdem Azure Active Directory.

6. Klicken Sie auf die Option **Erstellen**, um die neue Gruppe hinzuzufügen. Dann sollte Ihre Gruppe in der Liste angezeigt werden.

> [!TIP]
> Im Folgenden finden Sie einige weitere Beispiele für Gruppen, die Sie für dynamische Benutzer und Geräte erstellen können:
>
> - Alle Schüler der High School Contoso
> - Alle Android Enterprise-Geräte
> - Alle Geräte unter iOS 11 und höher
> - Marketing
> - Personalabteilung
> - Alle Mitarbeiter in Charlotte
> - Alle Mitarbeiter in Washington

## <a name="groups-and-policies"></a>Gruppen und Richtlinien

Der Zugriff auf die Ressourcen Ihrer Organisation wird von Benutzern und Gruppen gesteuert, die von Ihnen erstellt werden.

Bestimmen Sie bei der Erstellung von Gruppen, wie [Konformitätsrichtlinien](../protect/device-compliance-get-started.md) und [Konfigurationsprofile](../configuration/device-profiles.md) angewendet werden sollen Beispielsweise verfügen Sie möglicherweise über:

- Richtlinien, die sich auf das Betriebssystem eines Geräts beziehen
- Richtlinien, die sich auf verschiedene Rollen in Ihrer Organisation beziehen
- Richtlinien, die sich auf bestimmte Organisationseinheiten beziehen, die Sie in Active Directory definiert haben

Sie können eine Standardrichtlinie erstellen, die für alle Gruppen und Geräte gilt, um die grundlegenden Konformitätsanforderungen Ihrer Organisation festzulegen. Anschließend können Sie spezifischere Richtlinien für bestimmte Kategorien von Benutzern und Geräten erstellen. Beispielsweise können Sie E-Mail-Richtlinien für jedes der Betriebssysteme der mobilen Geräte erstellen.

Empfehlungen und Anleitungen zu Konfigurationsprofilen finden Sie unter [Zuweisen von Richtlinien für Benutzer- und Gerätegruppen](../configuration/device-profile-assign.md#user-groups-vs-device-groups) und [Profilempfehlungen](../configuration/device-profile-create.md#recommendations).

## <a name="see-also"></a>Weitere Informationen:

- [Rollenbasierte Zugriffssteuerung für Microsoft Intune](role-based-access-control.md)
- [Verwalten des Zugriffs auf Ressourcen mit Azure AD-Gruppen](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
