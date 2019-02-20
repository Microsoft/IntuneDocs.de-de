---
title: Rollenbasierte Zugriffssteuerung mit Microsoft Intune
description: Erfahren Sie, wie Sie mit der rollenbasierten Zugriffssteuerung (Role-Based Access Control, RBAC) steuern können, wer Aktionen durchführen und Änderungen in Microsoft Intune vornehmen kann.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: a57dca7f6b817177cbd131e969c1b5aa52a248a8
ms.sourcegitcommit: e0374b3ced83c8876a4f78b326869c10588a55e5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56307769"
---
# <a name="role-based-administration-control-rbac-with-microsoft-intune"></a>Rollenbasierte Zugriffssteuerung mit Microsoft Intune

Mithilfe der rollenbasierten Zugriffssteuerung können Sie bestimmen, wer verschiedene Intune-Aufgaben in Ihrer Organisation ausführen darf und für wen diese Aufgaben gelten. Sie können entweder die integrierten Rollen verwenden, die einige allgemeine Intune-Szenarien abdecken, oder Sie können eigene Rollen erstellen. Eine Rolle wird durch Folgendes definiert:

- **Rollendefinition**: Der Name einer Rolle, die von ihr verwalteten Ressourcen und die jeder Ressource erteilten Berechtigungen.
- **Mitglieder**: Die Benutzergruppen, denen die Berechtigungen erteilt werden.
- **Bereich (Gruppen)**: Die Benutzer- bzw. Gerätegruppen, die die Mitglieder verwalten können.
- **[Bereich (Tags)](https://docs.microsoft.com/intune/scope-tags)**: Tags für die Rollenzuweisung.
- **Zuweisung**: Nachdem die Definition, Mitglieder und der Bereich konfiguriert wurden, wird die Rolle zugewiesen.

![Beispiel für die rollenbasierte Zugriffssteuerung mit Intune](./media/intune-rbac-1.PNG)

Beginnend mit dem neuen Azure-Portal bietet **Azure Active Directory (Azure AD)** zwei Verzeichnisrollen, die mit Intune verwendet werden können. Diese Rollen haben die Vollzugriffsberechtigung für alle Aktivitäten in Intune:

- **Globaler Administrator**: Benutzer mit dieser Rolle haben Zugriff auf alle administrativen Funktionen in Azure AD sowie auf Dienste, die mit Azure AD einen Verbund bilden, wie z.B. Exchange Online, SharePoint Online und Skype for Business Online. Die Person, die sich für den Azure AD-Mandanten registriert, wird ein globaler Administrator. Nur globale Administratoren können weitere Azure AD-Administratorrollen zuweisen. Es kann mehr als einen globalen Administrator in Ihrem Unternehmen geben. Globale Administratoren können das Kennwort aller Benutzer und aller anderen Administratoren zurücksetzen.

- **Intune-Dienstadministrator**: Benutzer mit dieser Rolle haben globale Berechtigungen in Intune, sobald der Dienst aktiviert ist. Neben ersetzenden Azure-Einschränkungen bietet diese Rolle die Möglichkeit, Benutzer und Geräte zu verwalten sowie Intune-Gruppen zu erstellen und zu verwalten.

- **Administrator für bedingten Zugriff**: Benutzer mit dieser Rolle haben nur Berechtigungen, Richtlinien für den bedingten Zugriff anzuzeigen, zu erstellen, zu bearbeiten und zu löschen.

    > [!IMPORTANT]
    > Die Rolle „Intune-Dienstadministrator“ ermöglicht nicht das Verwalten der Azure AD-Einstellungen für bedingten Zugriff.
    > Um einer Intune-Rolle zugewiesen zu werden, muss der Benutzer über eine Intune-Lizenz verfügen.

    > [!TIP]
    > Intune zeigt außerdem drei Azure AD-Erweiterungen an: **Benutzer**, **Gruppen** und **Bedingter Zugriff**, die mithilfe der rollenbasierten Zugriffssteuerung von Azure AD gesteuert werden. Darüber hinaus führt der **Benutzerkontoadministrator** lediglich auf AAD-Benutzer- und Gruppen bezogene Aktivitäten aus und verfügt nicht über Vollzugriffsberechtigungen zum Ausführen aller Aktivitäten in Intune. Weitere Informationen finden Sie unter [Berechtigungen der Administratorrolle in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles).

## <a name="roles-created-in-the-intune-classic-portal"></a>Im klassischen Intune-Portal erstellte Rollen

Nur Benutzer mit der Rolle **Intune-Dienstadministrator** mit Vollzugriffsberechtigung werden vom klassischen Intune-Portal zu Intune in Azure migriert. Sie müssen Benutzer mit der Rolle **Intune-Dienstadministrator** mit der Zugriffsebene „Schreibgeschützt“ oder „Support“ Intune-Rollen im Azure-Portal neu zuweisen und aus dem klassischen Azure-Portal entfernen.

> [!IMPORTANT]
> Sie können den Zugriff für Intune-Dienstadministratoren im klassischen Portal ggf. beibehalten, wenn Ihre Administratoren weiterhin einen Zugriff zum Verwalten von PCs mit Intune benötigen.

## <a name="built-in-roles"></a>Integrierte Rollen

Sie können Gruppen ohne weitere Konfiguration integrierte Rollen zuweisen. Sie können eine integrierte Rolle nicht löschen oder bearbeiten.

- **Helpdesk-Operator**: Führt Remoteaufgaben für Benutzer und Geräte durch und kann Anwendungen oder Richtlinien Benutzern oder Geräten zuweisen.
- **Richtlinien- und Profil-Manager**: Verwaltet Konformitätsrichtlinien, Konfigurationsprofile, die Apple-Registrierung und unternehmensbezogene Geräte-IDs.
- **Schreibgeschützter Operator**: Kann Benutzer-, Geräte-, Registrierungs-, Konfigurations- und Anwendungsinformationen anzeigen. Kann keine Änderungen in Intune vornehmen.
- **Anwendungs-Manager**: Verwaltet mobile und verwaltete Anwendungen und kann Geräteinformationen lesen sowie Gerätekonfigurationsprofile anzeigen.
- **Intune-Rollenadministrator**: Verwaltet benutzerdefinierte Intune-Rollen und fügt integrierten Intune-Rollen Aufgaben hinzu. Dies ist die einzige Intune-Rolle, die Administratoren Berechtigungen zuweisen kann.
- **Schuladministrator**: Verwaltet Windows 10-Geräte in [Intune for Education](introduction-intune-education.md) und kann die folgenden Aktionen ausführen: 

    |Permission|Vorgang|
    |---|---|
    |Überwachungsdaten|Überwachungsdaten|
    |DeviceConfigurations:|Zuweisen, Erstellen, Löschen, Lesen, Aktualisieren|
    |Geräteregistrierungs-Manager|Lesen, Aktualisieren|
    |Verwaltete Geräte|Lesen, Aktualisieren<!--, Delete [To be added in 1803]-->|
    |Mobile Apps|Zuweisen, Erstellen, Löschen, Lesen, Aktualisieren|
    |Berichte|Überwachungsdaten|
    |Remoteaktionen|PC bereinigen, Neustart, Remotesperre, außer Kraft setzen, Geräte synchronisieren, Zurücksetzen|
    |Organisation|Überwachungsdaten|

### <a name="to-assign-a-built-in-role"></a>So weisen Sie eine integrierte Rolle zu

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie auf dem Blatt **Intune** die Option **Rollen** > **Alle Rollen** aus.
4. Klicken Sie auf dem Blatt **Intune-Rollen – Alle Rollen** auf die integrierte Rolle, die Sie zuweisen möchten.

5. Wählen Sie auf dem Blatt <*Rollenname*> – **Übersicht** die Option **Verwalten** > **Zuweisungen** aus.

6. Wählen Sie auf dem Blatt „Benutzerdefinierte Rolle“ **Zuweisen** aus.

7. Geben Sie auf dem Blatt **Rollenzuweisungen** einen **Zuweisungsnamen** und eine optionale **Zuweisungsbeschreibung** für die Zuweisung ein.

8. Wählen Sie für **Mitglieder (Gruppe)** eine Gruppe aus, die den Benutzer enthält, dem Sie die Berechtigungen erteilen möchten.

9. Wählen Sie für **Bereich (Gruppen)** eine Gruppe aus, die die Benutzer enthält, die das oben ausgewählte Mitglied verwalten soll.

10. Wählen Sie für **Bereich (Tags)** Tags aus, wo diese Rollenzuweisung angewendet wird.

11. Wenn Sie fertig sind, klicken Sie auf **OK**. Die neue Zuweisung wird in der Liste der Zuweisungen angezeigt.

### <a name="intune-rbac-table"></a>Intune-Tabelle zur rollenbasierten Zugriffsteuerung

- Laden Sie die [Intune-Tabelle zur rollenbasierten Zugriffsteuerung](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) herunter, um weitere Details zu den Möglichkeiten jeder Rolle zu erfahren.

## <a name="custom-roles"></a>Benutzerdefinierte Rollen

Sie können eine benutzerdefinierte Sicherheitsrolle erstellen, die alle für einen bestimmten Aufgabenbereich erforderlichen Berechtigungen enthält. Wenn beispielsweise eine IT-Abteilungsgruppe Anwendungen, Richtlinien und Konfigurationsprofile verwaltet, können Sie alle diese Berechtigungen gemeinsam einer benutzerdefinierten Rolle hinzufügen.

> [!IMPORTANT]
> Für das Erstellen, Bearbeiten oder Zuweisen von Rollen muss das Konto in Azure AD über eine der folgenden Berechtigungen verfügen:
> - **Globaler Administrator**
> - **Intune-Dienstadministrator**

### <a name="to-create-a-custom-role"></a>So erstellen Sie eine benutzerdefinierte Rolle

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) mit Ihren Intune-Anmeldeinformationen an.

2. Klicken Sie im Menü links auf **Alle Dienste**, und geben Sie in das Filtertextfeld **Intune** ein.

3. Wählen Sie **Intune** > **Rollen** > **Alle Rollen** > **Hinzufügen** aus.

4. Geben Sie auf dem Blatt **Benutzerdefinierte Rolle hinzufügen** einen Namen und eine Beschreibung für die neue Rolle ein, und klicken Sie dann auf **Berechtigungen**.

5. Wählen Sie auf dem Blatt **Berechtigungen** die Berechtigungen aus, die Sie mit dieser Rolle verwenden möchten. Entscheiden Sie mithilfe der [Tabelle zur rollenbasierten Zugriffssteuerung in Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a), welche Berechtigungen gelten sollen.

6. Wählen auf dem Blatt **Bereich (Tags)** Tags aus, wo diese benutzerdefinierte Rolle angewendet wird.

7. Wenn Sie fertig sind, klicken Sie auf **OK**.

7. Klicken Sie auf dem Blatt **Benutzerdefinierte Rolle hinzufügen** auf **Erstellen**. Die neue Rolle wird in der Liste auf dem Blatt **Intune-Rollen – Alle Rollen** angezeigt.

### <a name="to-assign-a-custom-role"></a>So weisen Sie eine benutzerdefinierte Rolle zu

Führen Sie die gleichen Schritte wie unter [So weisen Sie eine integrierte Rolle zu](https://docs.microsoft.com/intune/role-based-access-control#to-assign-a-built-in-role) beschrieben aus, und wählen Sie die benutzerdefinierte Rolle aus.

## <a name="next-steps"></a>Nächste Schritte

[Verwenden der Rolle „Intune-Support“ im Portal zur Problembehandlung](help-desk-operators.md)

## <a name="see-also"></a>Siehe auch

[Zuweisen von Rollen mithilfe von Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)
