---
title: Rollenbasierte Zugriffssteuerung für Microsoft Intune
description: Erfahren Sie, wie Sie mithilfe der rollenbasierten Zugriffssteuerung (Role-Based Access Control, RBAC) steuern können, wer in Microsoft Intune Aktionen ausführen und Änderungen vornehmen kann.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 98e2229194287ff644e9503fa21c9536cbff4734
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61507306"
---
# <a name="role-based-access-control-rbac-with-microsoft-intune"></a>Rollenbasierte Zugriffssteuerung für Microsoft Intune

Mithilfe der rollenbasierten Zugriffssteuerung (Role-Based Access Control, RBAC) können Sie verwalten, wer Zugriff auf die Ressourcen Ihrer Organisation hat und wozu diese verwendet werden können.  Wenn Sie Ihren Intune-Benutzern [Rollen zuweisen](assign-role.md), können Sie einschränken, welche Elemente diese sehen und ändern können. Jeder Rolle sind Berechtigungen zugewiesen, die festlegen, auf welche Elemente Benutzer mit dieser Rolle innerhalb Ihrer Organisation zugreifen können und welche Elemente sie ändern können.

Für das Erstellen, Bearbeiten oder Zuweisen von Rollen muss das Konto in Azure AD über eine der folgenden Berechtigungen verfügen:
- **Globaler Administrator**
- **Intune-Dienstadministrator** (auch als **Intune-Administrator** bezeichnet)

## <a name="roles"></a>Rollen
Eine Rolle definiert die Berechtigungen, die den ihr zugewiesenen Benutzern gewährt werden.
Sie können sowohl integrierte als auch benutzerdefinierte Rollen verwenden. Integrierte Rollen decken einige häufige Szenarios in Intune ab. Sie können aber auch Ihre [eigenen benutzerdefinierten Rollen](create-custom-role.md) mit den gewünschten Berechtigungen erstellen. Mehrere Azure Active Directory-Rollen beinhalten den Zugriff auf Intune.
Wenn Sie eine Rolle abrufen möchten, klicken Sie auf **Intune** > **Rollen** > **Alle Rollen**, und wählen Sie eine Rolle aus. Dann werden die folgenden Seiten angezeigt:

-   **Eigenschaften**: der Name, die Beschreibung, der Typ, die Zuweisungen und die Bereichsmarkierungen für die Rolle 
-   **Berechtigungen**: Listet eine Reihe von Optionen auf, die die Berechtigungen der jeweiligen Rolle definieren
-   **Zuweisungen:** Eine Liste mit [Rollenzuweisungen]( assign-role.md), in der definiert wird, welche Benutzer Zugriff auf welche Benutzer/Geräte haben. Eine Rolle kann mehrere Zuweisungen aufweisen, und ein Benutzer kann Teil mehrerer Zuweisungen sein.

### <a name="built-in-roles"></a>Integrierte Rollen
Sie können Gruppen ohne weitere Konfiguration integrierte Rollen zuweisen. Sie können den Namen, die Beschreibung, den Typ oder die Berechtigungen einer integrierten Rolle löschen oder bearbeiten. Eine vollständige Liste der Berechtigungen für die einzelnen integrierten Rollen finden Sie in der [Intune RBAC Table (Tabelle zur rollenbasierten Zugriffssteuerung in Intune)](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a).

- **Helpdesk-Operator**: Führt Remoteaufgaben für Benutzer und Geräte durch und kann Anwendungen oder Richtlinien Benutzern oder Geräten zuweisen.
- **Richtlinien- und Profil-Manager**: Verwaltet Konformitätsrichtlinien, Konfigurationsprofile, die Apple-Registrierung, unternehmensbezogene Geräte-IDs und Sicherheitsbaselines.
- **Schreibgeschützter Operator**: Kann Benutzer-, Geräte-, Registrierungs-, Konfigurations- und Anwendungsinformationen anzeigen. Kann keine Änderungen in Intune vornehmen.
- **Anwendungs-Manager**: Verwaltet mobile und verwaltete Anwendungen und kann Geräteinformationen lesen sowie Gerätekonfigurationsprofile anzeigen.
- **Intune-Rollenadministrator**: Verwaltet benutzerdefinierte Intune-Rollen und fügt integrierten Intune-Rollen Aufgaben hinzu. Dies ist die einzige Intune-Rolle, die Administratoren Berechtigungen zuweisen kann.
- **Schuladministrator**: Verwaltet Windows 10-Geräte in [Intune for Education](introduction-intune-education.md).

### <a name="custom-roles"></a>Benutzerdefinierte Rollen
Sie können mithilfe von benutzerdefinierten Berechtigungen Ihre eigenen Rollen erstellen. Weitere Informationen zu benutzerdefinierten Rollen finden Sie unter [Create a custom role (Erstellen von benutzerdefinierten Rollen)](create-custom-role.md).

### <a name="azure-active-directory-roles-with-intune-access"></a>Azure Active Directory-Rollen mit Zugriff auf Intune
| Azure Active Directory-Rolle | Alle Intune-Daten | Intune-Überwachungsdaten |
| --- | :---: | :---: |
| Globaler Administrator | Lesen + Schreiben | Lesen + Schreiben |
| Intune-Dienstadministrator | Lesen + Schreiben | Lesen + Schreiben |
| Administrator für bedingten Zugriff | Keine | Keine |
| Sicherheitsadministrator | Schreibgeschützt | Schreibgeschützt |
| Sicherheitsoperator | Schreibgeschützt | Schreibgeschützt |
| Sicherheitsleseberechtigter | Schreibgeschützt | Schreibgeschützt |
| Complianceadministrator | Keine | Schreibgeschützt |
| Administrator für Konformitätsdaten | Keine | Schreibgeschützt |

> [!TIP]
> Intune zeigt außerdem drei Azure AD-Erweiterungen an: **Benutzer**, **Gruppen** und **Bedingter Zugriff**, die mithilfe der rollenbasierten Zugriffssteuerung von Azure AD gesteuert werden. Darüber hinaus führt der **Benutzerkontoadministrator** lediglich auf AAD-Benutzer- und Gruppen bezogene Aktivitäten aus und verfügt nicht über Vollzugriffsberechtigungen zum Ausführen aller Aktivitäten in Intune. Weitere Informationen finden Sie unter [Berechtigungen der Administratorrolle in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles).
### <a name="roles-created-in-the-intune-classic-portal"></a>Im klassischen Intune-Portal erstellte Rollen
Nur Benutzer mit der Rolle **Intune-Dienstadministrator** mit Vollzugriffsberechtigung werden vom klassischen Intune-Portal zu Intune in Azure migriert. Sie müssen Benutzer mit der Rolle **Intune-Dienstadministrator** mit der Zugriffsebene „Schreibgeschützt“ oder „Support“ Intune-Rollen im Azure-Portal neu zuweisen und aus dem klassischen Azure-Portal entfernen.
> [!IMPORTANT]
> Sie können den Zugriff für Intune-Dienstadministratoren im klassischen Portal ggf. beibehalten, wenn Ihre Administratoren weiterhin einen Zugriff zum Verwalten von PCs mit Intune benötigen.

## <a name="role-assignments"></a>Rollenzuweisungen
Eine Rollenzuweisung definiert Folgendes:

- die einer Rolle zugewiesenen Benutzer
- die Ressourcen, die diese sehen können
- die Ressourcen, die diese ändern können

Sie können Ihren Benutzern sowohl benutzerdefinierte als auch integrierte Rollen zuweisen. Um einer Intune-Rolle zugewiesen zu werden, muss der Benutzer über eine Intune-Lizenz verfügen.
Wenn Sie eine Rollenzuweisung abrufen möchten, klicken Sie auf **Intune** > **Rollen** > **Alle Rollen**, und wählen Sie erst eine Rolle und dann eine Zuweisung aus. Dann werden die folgenden Seiten angezeigt:

-   **Eigenschaften**: der Name, die Beschreibung, die Rolle, die Mitglieder, die Bereiche und die Markierungen einer Zuweisung
-   **Mitglieder**: Alle einer Gruppe angehörenden Benutzer haben die Berechtigung, die Benutzer/Geräte zu verwalten, die in diesem Bereich (der Gruppe) aufgelistet sind.
-   **Bereich (Gruppen)**: Alle Benutzer/Geräte in dieser Gruppe können von den Benutzern verwaltet werden, die unter „Mitglieder“ aufgeführt sind.
-   **[Bereich (Tags)](scope-tags.md)**: Benutzer, die unter „Mitglieder“ aufgeführt sind, können die Ressourcen sehen, die dieselben Bereichsmarkierungen aufweisen.

### <a name="multiple-role-assignments"></a>Mehrere Rollenzuweisungen
Wenn einem Benutzer mehrere Rollen zugewiesen sind, gelten die Berechtigungen in diesen Rollenzuweisungen wie folgt für verschiedene Objekte:

- Zuweisungsberechtigungen gelten nur für die Objekte (wie Richtlinien oder Apps) im Zuweisungsbereich (Gruppe) dieser Rolle. Zuweisungsberechtigungen gelten nur für Objekte in anderen Rollenzuweisungen, wenn die andere Zuweisung dies explizit zulässt.
- Andere Berechtigungen (wie Lesen und Schreiben) gelten für alle Objekte desselben Typs (wie alle Richtlinien oder alle Apps) in den Zuweisungen des Benutzers.
- Berechtigungen für Objekte verschiedener Typen (wie Richtlinien oder Apps) gelten nicht gleichzeitig für alle Objekte. Eine Leseberechtigung für eine Richtlinie umfasst beispielsweise keine Leseberechtigung für Apps in den Zuweisungen des Benutzers.

## <a name="next-steps"></a>Nächste Schritte
- [Assign a role to a user (Zuweisen einer Rolle an einen Benutzer)](assign-role.md)
- [Create a custom role (Erstellen einer benutzerdefinierten Rolle)](create-custom-role.md)
