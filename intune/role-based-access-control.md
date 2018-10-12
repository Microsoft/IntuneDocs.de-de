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
ms.custom: intune-azure; get-started
ms.openlocfilehash: 5c75bd80e848bbd309051a9c6f3e149abd7a46ed
ms.sourcegitcommit: 378474debffbc85010c54e20151d81b59b7a7828
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "47028697"
---
# <a name="role-based-administration-control-rbac-with-microsoft-intune"></a>Rollenbasierte Zugriffssteuerung mit Microsoft Intune

Mithilfe der rollenbasierten Zugriffssteuerung können Sie bestimmen, wer verschiedene Intune-Aufgaben in Ihrer Organisation ausführen darf und für wen diese Aufgaben gelten. Sie können entweder die integrierten Rollen verwenden, die einige allgemeine Intune-Szenarien abdecken, oder Sie können eigene Rollen erstellen. Eine Rolle wird durch Folgendes definiert:

- **Rollendefinition**: Der Name einer Rolle, die von ihr verwalteten Ressourcen und die jeder Ressource erteilten Berechtigungen.
- **Mitglieder**: Die Benutzergruppen, denen die Berechtigungen erteilt werden.
- **Bereich**: Die Benutzer- bzw. Gerätegruppen, die die Mitglieder verwalten können.
- **Zuweisung:** Nachdem die Definition, Mitglieder und der Bereich konfiguriert wurden, wird die Rolle zugewiesen.

![Beispiel für die rollenbasierte Zugriffssteuerung mit Intune](./media/intune-rbac-1.PNG)

Beginnend mit dem neuen Azure-Portal bietet **Azure Active Directory (Azure AD)** zwei Verzeichnisrollen, die mit Intune verwendet werden können. Diese Rollen haben die Vollzugriffsberechtigung für alle Aktivitäten in Intune:

- **Globaler Administrator:** Benutzer mit dieser Rolle haben Zugriff auf alle administrativen Funktionen in Azure AD sowie auf Dienste, die mit Azure AD einen Verbund bilden, wie z.B. Exchange Online, SharePoint Online und Skype for Business Online. Die Person, die sich für den Azure AD-Mandanten registriert, wird ein globaler Administrator. Nur globale Administratoren können weitere Azure AD-Administratorrollen zuweisen. Es kann mehr als einen globalen Administrator in Ihrem Unternehmen geben. Globale Administratoren können das Kennwort aller Benutzer und aller anderen Administratoren zurücksetzen.

- **Intune-Dienstadministrator:** Benutzer mit dieser Rolle haben globale Berechtigungen in Intune, sobald der Dienst aktiviert ist. Neben ersetzenden Azure-Einschränkungen bietet diese Rolle die Möglichkeit, Benutzer und Geräte zu verwalten sowie Intune-Gruppen zu erstellen und zu verwalten.

- **Administrator für bedingten Zugriff**: Benutzer mit dieser Rolle haben nur Berechtigungen, Richtlinien für den bedingten Zugriff anzuzeigen, zu erstellen, zu bearbeiten und zu löschen.

    > [!IMPORTANT]
    > Die Rolle „Intune-Dienstadministrator“ ermöglicht nicht das Verwalten der Azure AD-Einstellungen für bedingten Zugriff.
    > Für Member von Intune-Rollen ist eine Intune-Lizenz erforderlich.

    > [!TIP]
    > Intune zeigt außerdem drei Azure AD-Erweiterungen an, **Benutzer**, **Gruppen** und **Bedingter Zugriff**, die mithilfe der rollenbasierten Zugriffssteuerung von Azure AD gesteuert werden. Darüber hinaus führt der **Benutzerkontoadministrator** lediglich auf AAD-Benutzer- und Gruppen bezogene Aktivitäten aus und verfügt nicht über Vollzugriffsberechtigungen zum Ausführen aller Aktivitäten in Intune. Unter [Rollenbasierte Zugriffssteuerung in Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles) finden Sie weitere Details.

## <a name="roles-created-in-the-intune-classic-portal"></a>Im klassischen Intune-Portal erstellte Rollen

Nur Benutzer mit der Rolle **Intune-Dienstadministrator** mit Vollzugriffsberechtigung werden vom klassischen Intune-Portal zu Intune in Azure migriert. Sie müssen Benutzer mit der Rolle **Intune-Dienstadministrator** mit der Zugriffsebene „Schreibgeschützt“ oder „Support“ Intune-Rollen im Azure-Portal neu zuweisen und aus dem klassischen Azure-Portal entfernen.

> [!IMPORTANT]
> Sie können den Zugriff für Intune-Dienstadministratoren im klassischen Portal ggf. beibehalten, wenn Ihre Administratoren weiterhin einen Zugriff zum Verwalten von PCs mit Intune benötigen.

## <a name="built-in-roles"></a>Integrierte Rollen

Die folgenden Rollen sind in Intune integriert. Sie können sie ohne weitere Konfiguration Gruppen zuweisen:

- **Support**: Führt Remoteaufgaben für Benutzer und Geräte durch und kann Anwendungen oder Richtlinien Benutzern oder Geräten zuweisen.
- **Richtlinien- und Profil-Manager**: Verwaltet Konformitätsrichtlinien, Konfigurationsprofile, die Apple-Registrierung und unternehmensbezogene Geräte-IDs.
- **Operator mit beschränkter Leseberechtigung**: Kann Benutzer-, Geräte-, Registrierungs-, Konfigurations- und Anwendungsinformationen anzeigen. Es können keine Änderungen in Intune vorgenommen werden.
- **Anwendungs-Manager:** Verwaltet mobile und verwaltete Anwendungen und kann Geräteinformationen lesen sowie Gerätekonfigurationsprofile anzeigen.
- **Intune-Rollenadministrator:** Verwaltet benutzerdefinierte Intune-Rollen und fügt integrierten Intune-Rollen Aufgaben hinzu. Dies ist die einzige Intune-Rolle, die Administratoren Berechtigungen zuweisen kann.
- **Schuladministrator:** verwaltet Windows 10-Geräte in [Intune for Education](introduction-intune-education.md) und kann die folgenden Aktionen ausführen: 

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
3. Wählen Sie im Bereich **Intune** die Option **Rollen** > **Alle Rollen** aus.
1. Klicken Sie im Bereich **Intune-Rollen – Alle Rollen** auf die integrierte Rolle, die Sie zuweisen möchten.

2. Klicken Sie im Bereich <*Rollenname*>-**Übersicht** erst auf **Verwalten** und dann auf **Zuweisungen**.

    > [!NOTE]
    > Sie können die integrierten Rollen nicht löschen oder bearbeiten.

3. Klicken Sie im Bereich „Benutzerdefinierte Rolle“ auf **Zuweisen**.

4. Geben Sie im Bereich **Rollenzuweisungen** einen **Namen** und eine optionale **Beschreibung** für die Zuweisung ein, und wählen Sie dann Folgendes aus:
    - **Mitglieder:** Wählen Sie eine Gruppe aus, die den Benutzer enthält, dem Sie die Berechtigungen erteilen möchten.
    - **Bereich:** Wählen Sie eine Gruppe aus, die die Benutzer enthält, die das oben ausgewählte Mitglied verwalten soll.
<br></br>
5. Klicken Sie abschließend auf **OK**. Die neue Zuweisung wird in der Liste der Zuweisungen angezeigt.

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

3. Wählen Sie **Intune** > **Rollen** > **Alle Rollen** > **Benutzerdefiniertes Element hinzufügen** aus.

4. Geben Sie im Bereich **Benutzerdefinierte Rolle hinzufügen** einen Namen und eine Beschreibung für die neue Rolle ein, und klicken Sie dann auf **Berechtigungen**.

5. Klicken Sie im Bereich **Berechtigungen** auf die Berechtigungen, die Sie mit dieser Rolle verwenden möchten. Entscheiden Sie mithilfe der [Tabelle zur rollenbasierten Zugriffssteuerung in Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a), welche Berechtigungen gelten sollen.

6. Wählen Sie abschließend **OK** aus.

7. Klicken Sie im Bereich **Benutzerdefinierte Rolle hinzufügen** auf **Erstellen**. Die neue Rolle wird in der Liste im Bereich **Intune-Rollen – Alle Rollen** angezeigt.

### <a name="to-assign-a-custom-role"></a>So weisen Sie eine benutzerdefinierte Rolle zu

1. Klicken Sie im Bereich **Intune-Rollen – Alle Rollen** auf die benutzerdefinierte Rolle, die Sie zuweisen möchten.

2. Klicken Sie im Bereich <*Rollenname*>-**Übersicht** erst auf **Verwalten** und dann auf **Zuweisungen**. Sie können in diesem Bereich auch vorhandene Rollen bearbeiten oder löschen.

3. Klicken Sie im Bereich „Benutzerdefinierte Rolle“ auf **Zuweisen**.

4. Geben Sie im Bereich **Rollenzuweisungen** einen **Namen** und eine optionale **Beschreibung** für die Zuweisung ein, und wählen Sie dann Folgendes aus:
    - **Mitglieder:** Wählen Sie eine Gruppe aus, die den Benutzer enthält, dem Sie die Berechtigungen erteilen möchten.
    - **Bereich:** Wählen Sie eine Gruppe aus, die die Benutzer enthält, die das oben ausgewählte Mitglied verwalten soll.
<br></br>
5. Klicken Sie abschließend auf **OK**. Die neue Zuweisung wird in der Liste der Zuweisungen angezeigt.

## <a name="next-steps"></a>Nächste Schritte

[Verwenden der Rolle „Intune-Support“ im Portal zur Problembehandlung](help-desk-operators.md)

## <a name="see-also"></a>Siehe auch

[Zuweisen von Rollen mithilfe von Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)
