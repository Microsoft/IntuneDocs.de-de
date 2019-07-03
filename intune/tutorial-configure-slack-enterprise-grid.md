---
title: 'Tutorial: Konfigurieren von Slack zur Verwendung von Intune für EMM und die App-Konfiguration'
titleSuffix: Microsoft Intune
description: In diesem Tutorial konfigurieren Sie Slack zur Verwendung von Intune für EMM und die App-Konfiguration.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 06/11/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 55db37c5-0da7-4d9c-8027-525afb1c6349
Customer intent: As an Intune admin, I want to learn how to configure Slack to use Intune for EMM and app configuration..
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0829a2b3f9aff5f30a971d176591bf838510a606
ms.sourcegitcommit: 43ba5a05b2e1dc1997126d3574884f65cde449c7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2019
ms.locfileid: "67197613"
---
# <a name="tutorial-configure-slack-to-use-intune-for-emm-and-app-configuration"></a>Tutorial: Konfigurieren von Slack zur Verwendung von Intune für EMM und die App-Konfiguration

Slack ist eine App für die Zusammenarbeit, die Sie mit Microsoft Intune verwenden können.   

Inhalt des Tutorials:
> [!div class="checklist"]
> - Sie legen Intune in Ihrem Slack Enterprise Grid als EMM-Anbieter (Enterprise Mobility Management) fest. Sie können den Zugriff auf die Arbeitsbereiche Ihres Grid-Plans auf von Intune verwaltete Geräte beschränken.
> - Sie erstellen App-Konfigurationsrichtlinien zur Verwaltung der Slack for EMM-App unter iOS und der Slack-App für Geräte mit Android-Arbeitsprofil.
> - Sie erstellen Intune-Gerätekonformitätsrichtlinien zum Festlegen der Bedingungen, die iOS- und Android-Gerät erfüllen müssen, um als konform angesehen zu werden.

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="prerequisites"></a>Voraussetzungen
Sie benötigen für dieses Tutorial einen Testmandanten mit den folgenden Abonnements:
- Azure Active Directory Premium ([kostenlose Testversion](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Intune-Abonnement ([kostenlose Testversion](free-trial-sign-up.md))

Sie benötigen auch einen Plan für [Slack Enterprise Grid](https://get.slack.help/hc/articles/360004150931-What-is-Slack-Enterprise-Grid-).

## <a name="configure-your-slack-enterprise-grid-plan"></a>Konfigurieren Ihres Slack Enterprise Grid-Plans
Aktivieren Sie EMM für Ihren Slack Enterprise Grid-Plan, indem Sie die [Anweisungen von Slack](https://get.slack.help/hc/articles/115002579426-Enable-Enterprise-Mobility-Management-for-your-org#step-2:-turn-on-emm) befolgen und eine [Verbindung mit Azure Active Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/slack-tutorial) als Identitätsanbieter Ihres Grid-Plans herstellen.

## <a name="sign-in-to-intune"></a>Anmelden bei Intune
Registrieren Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) als globaler Administrator oder als Intune-Dienstadministrator. Wenn Sie ein Testabonnement für Intune erstellt haben, besitzt das Konto, mit dem Sie das Abonnement erstellt haben, die Rolle des globalen Administrators.

## <a name="set-up-slack-for-emm-on-ios-devices"></a>Einrichten von Slack for EMM auf iOS-Geräten
Fügen Sie die iOS App „Slack for EMM“ zu Ihrem Intune-Mandanten hinzu, und erstellen Sie eine App-Konfigurationsrichtlinie, um den iOS-Benutzern Ihrer Organisation den Zugriff auf Slack mit Intune als EMM-Anbieter zu ermöglichen.

### <a name="add-slack-for-emm-to-intune"></a>Hinzufügen von Slack for EMM zu Intune
Fügen Sie Slack for EMM als verwaltete iOS-App zu Intune hinzu, und weisen Sie Slack-Benutzer zu. Apps sind plattformspezifisch, daher müssen Sie für Ihre Slack-Benutzer mit Android-Geräten eine separate Intune-App hinzufügen.
1.  Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**.
2.  Wählen Sie unter „App-Typ“ die Option **Store-App – iOS** aus.
3.  Wählen Sie **App Store durchsuchen** aus. Geben Sie den Suchbegriff „Slack for EMM“ ein, und wählen Sie die App aus.
4.  Klicken Sie auf **App-Informationen**, und konfigurieren Sie alle für Ihre Organisation erforderlichen Änderungen.
5.  Wählen Sie **Hinzufügen** aus.
6.  Geben Sie in der Suchleiste „Slack for EMM“ ein, und wählen Sie die App aus, die Sie gerade hinzugefügt haben.
7.  Wählen Sie unter „Verwalten“ die Option **Zuweisungen** aus.
8.  Wählen Sie **Gruppe hinzufügen** aus. Je nachdem, auf welche Benutzer und Geräte sich die Aktivierung von Slack for EMM auswirken soll, können Sie unter **Zuweisungstyp** Folgendes auswählen:
    -  **Verfügbar für registrierte Geräte**, wenn Sie „Alle Mitglieder (einschließlich Gäste)“ ausgewählt haben, ODER
    -  **Verfügbar mit oder ohne Registrierung**, wenn Sie „Alle Mitglieder (außer Gästen)“ oder „Optional“ ausgewählt haben.
9.  Wählen Sie **Eingeschlossene Gruppen** aus, und klicken Sie unter „Diese App für alle Benutzer verfügbar machen“ auf **Ja**.
10. Klicken Sie auf **OK** und dann erneut auf **OK**.
11. Klicken Sie auf **Speichern**.

### <a name="add-an-app-configuration-policy-for-slack-for-emm"></a>Hinzufügen einer App-Konfigurationsrichtlinie für Slack for EMM
Fügen Sie eine App-Konfigurationsrichtlinie für Slack for EMM unter iOS hinzu. App-Konfigurationsrichtlinien für verwaltete Geräte sind plattformspezifisch, daher müssen Sie für Ihre Slack-Benutzer mit Android-Geräten eine separate Richtlinie hinzufügen.
1.  Klicken Sie in Intune auf **Client-Apps** > **App-Konfigurationsrichtlinien** > **Hinzufügen**.
2.  Geben Sie als Namen „Test der Konfigurationsrichtlinie für Slack-App“ ein.
3.  Wählen Sie unter „Geräteregistrierungstyp“ die Option **Verwaltete Geräte** aus.
4.  Wählen Sie unter „Plattform“ die Option **iOS** aus.
5.  Wählen Sie **Zugeordnete App** aus.
6.  Geben Sie in der Suchleiste „Slack for EMM“ ein, und wählen Sie die App aus.
7.  Klicken Sie auf **OK**, und wählen Sie dann **Konfigurationseinstellungen** aus. 
    -   Informationen zu Konfigurationsschlüsseln und ihren Werten finden Sie auf der [Webseite der AppConfig-Community für Slack](https://www.appconfig.org/company/slack/) auf der Registerkarte „Technical“.
8.  Klicken Sie auf **OK** und dann auf **Hinzufügen**.
9.  Geben Sie in der Suchleiste den Begriff „Test der Konfigurationsrichtlinie für Slack-App“ ein, und wählen Sie die Richtlinie aus, die Sie gerade hinzugefügt haben.
10. Wählen Sie unter „Verwalten“ die Option **Zuweisungen** aus.
11. Wählen Sie unter „Zuweisen zu“ die Option **Alle Benutzer und alle Geräte** aus.
12. Klicken Sie auf **Speichern**.

### <a name="optional-create-an-ios-device-compliance-policy"></a>(Optional) Erstellen einer iOS-Gerätekonformitätsrichtlinie
Richten Sie eine Intune-Gerätekonformitätsrichtlinie ein, um die Bedingungen festzulegen, die ein Gerät erfüllen muss, um als konform angesehen zu werden. Für dieses Tutorial erstellen wir eine Gerätekonformitätsrichtlinie für iOS-Geräte. Konformitätsrichtlinien sind plattformspezifisch, daher müssen Sie für Ihre Slack-Benutzer mit Android-Geräten eine separate Richtlinie erstellen.
1.  Wählen Sie in Intune **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** aus.
2.  Geben Sie als Namen „Test für iOS-Konformitätsrichtlinie“ ein.
3.  Geben Sie als Beschreibung „Test für iOS-Konformitätsrichtlinie“ ein.
4.  Wählen Sie unter „Plattform“ die Option **iOS** aus.
5.  Klicken Sie auf **Geräteintegrität**. Klicken Sie neben „Geräte mit Jailbreak“ auf **Blockieren** und dann auf **OK**.
6.  Klicken Sie auf **Systemsicherheit**, und geben Sie Kennworteinstellungen an. Legen Sie für dieses Tutorial die folgenden empfohlenen Einstellungen fest:
    -   Wählen Sie für „Kennwort zum Entsperren mobiler Geräte anfordern“ die Option **Anfordern** aus.
    -   Wählen Sie für „Einfache Kennwörter“ die Option **Blockieren** aus.
    -   Geben Sie für „Minimale Kennwortlänge“ die Zahl 4 ein.
    -   Wählen Sie für „Erforderlicher Kennworttyp“ die Option **Alphanumerisch** aus.
    -   Wählen Sie für „Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts“ die Option **Sofort** aus.
    -   Geben Sie für „Kennwortablauf (Tage)“ die Zahl 41 ein.
    -   Geben Sie für „Anzahl vorheriger Kennwörter, deren Wiederverwendung verhindert wird“ die Zahl 5 ein.
7.  Klicken Sie auf **OK** und dann erneut auf **OK**.
8.  Klicken Sie auf **Erstellen**.

## <a name="set-up-slack-on-android-work-profile-devices"></a>Einrichten von Slack auf Geräten mit Android-Arbeitsprofil
Fügen Sie die verwaltete Google Play-App „Slack“ zu Ihrem Intune-Mandanten hinzu, und erstellen Sie eine App-Konfigurationsrichtlinie, um den Android-Benutzern Ihrer Organisation den Zugriff auf Slack mit Intune als EMM-Anbieter zu ermöglichen.

### <a name="add-slack-to-intune"></a>Hinzufügen von Slack zu Intune
Fügen Sie Slack als verwaltete Google Play-App zu Intune hinzu, und weisen Sie Slack-Benutzer zu. Apps sind plattformspezifisch, daher müssen Sie für Ihre Slack-Benutzer mit iOS-Geräten eine separate Intune-App hinzufügen.
1.  Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**.
2.  Wählen Sie unter „App-Typ“ die Option **Store-App – verwaltetes Google Play** aus.
3.  Wählen Sie **Verwaltetes Google Play – genehmigen** aus. Geben Sie den Suchbegriff „Slack for EMM“ ein, und wählen Sie die App aus.
4.  Wählen Sie **Genehmigen** aus.
5.  Geben Sie in der Suchleiste „Slack“ ein, und wählen Sie die App aus, die Sie gerade hinzugefügt haben.
6.  Wählen Sie unter „Verwalten“ die Option **Zuweisungen** aus.
7.  Wählen Sie **Gruppe hinzufügen** aus. Je nachdem, auf welche Benutzer und Geräte sich die Aktivierung von Slack for EMM auswirken soll, können Sie unter **Zuweisungstyp** Folgendes auswählen:
    -   **Verfügbar für registrierte Geräte**, wenn Sie „Alle Mitglieder (einschließlich Gäste)“ ausgewählt haben, ODER
    -   **Verfügbar mit oder ohne Registrierung**, wenn Sie „Alle Mitglieder (außer Gästen)“ oder „Optional“ ausgewählt haben.
8.  Wählen Sie „Eingeschlossene Gruppen“ aus, und klicken Sie unter „Diese App für alle Benutzer verfügbar machen“ auf **Ja**.
9.  Klicken Sie auf **OK** und dann erneut auf **OK**.
10. Klicken Sie auf **Speichern**.

### <a name="add-an-app-configuration-policy-for-slack"></a>Hinzufügen einer App-Konfigurationsrichtlinie für Slack
Fügen Sie eine App-Konfigurationsrichtlinie für Slack hinzu. App-Konfigurationsrichtlinien für verwaltete Geräte sind plattformspezifisch, daher müssen Sie für Ihre Slack-Benutzer mit iOS-Geräten eine separate Richtlinie hinzufügen.
1.  Klicken Sie in Intune auf **Client-Apps** > **App-Konfigurationsrichtlinien** > **Hinzufügen**.
2.  Geben Sie als Namen „Test der Konfigurationsrichtlinie für Slack-App“ ein.
3.  Wählen Sie unter „Geräteregistrierungstyp“ die Option **Verwaltete Geräte** aus.
4.  Wählen Sie unter „Plattform die Option **Android** aus.
5.  Wählen Sie **Zugeordnete App** aus.
6.  Geben Sie in der Suchleiste „Slack“ ein, und wählen Sie die App aus.
7.  Klicken Sie auf **OK**, und wählen Sie dann **Konfigurationseinstellungen** aus.
    -   Informationen zu Konfigurationsschlüsseln und ihren Werten finden Sie auf der [Webseite der AppConfig-Community für Slack](https://www.appconfig.org/company/slack/) auf der Registerkarte „Technical“.
8.  Klicken Sie auf **OK** und dann auf **Hinzufügen**.
9.  Geben Sie in der Suchleiste den Begriff „Test der Konfigurationsrichtlinie für Slack-App“ ein, und wählen Sie die Richtlinie aus, die Sie gerade hinzugefügt haben.
10. Wählen Sie unter „Verwalten“ die Option **Zuweisungen** aus.
11. Wählen Sie unter „Zuweisen zu“ die Option **Alle Benutzer und alle Geräte** aus.
12. Klicken Sie auf **Speichern**.

### <a name="optional-create-an-android-device-compliance-policy"></a>(Optional) Erstellen einer Android-Gerätekonformitätsrichtlinie
Richten Sie eine Intune-Gerätekonformitätsrichtlinie ein, um die Bedingungen festzulegen, die ein Gerät erfüllen muss, um als konform angesehen zu werden. Für dieses Tutorial erstellen wir eine Gerätekonformitätsrichtlinie für Android-Geräte. Konformitätsrichtlinien sind plattformspezifisch, daher müssen Sie für Ihre Slack-Benutzer mit iOS-Geräten eine separate Richtlinie erstellen.
1.  Wählen Sie in Intune **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** aus.
2.  Geben Sie als Namen „Test für Android-Konformitätsrichtlinie“ ein.
3.  Geben Sie als Beschreibung „Test für Android-Konformitätsrichtlinie“ ein.
4.  Wählen Sie unter „Plattform“ die Option **Android Enterprise** aus.
5.  Wählen Sie unter „Profiltyp“ die Option **Arbeitsprofil** aus.
6.  Klicken Sie auf **Geräteintegrität**. Klicken Sie neben „Geräte mit entfernten Nutzungsbeschränkungen“ auf **Blockieren** und dann auf **OK**.
7.  Klicken Sie auf **Systemsicherheit**, und geben Sie **Kennworteinstellungen** an. Legen Sie für dieses Tutorial die folgenden empfohlenen Einstellungen fest:
    -   Wählen Sie für „Kennwort zum Entsperren mobiler Geräte anfordern“ die Option **Anfordern** aus.
    -   Wählen Sie für „Erforderlicher Kennworttyp“ die Option **Mindestens alphanumerisch** aus.
    -   Geben Sie für „Minimale Kennwortlänge“ die Zahl 4 ein.
    -   Wählen Sie für „Maximaler Zeitraum der Bildschirmsperre (in Minuten) bis zur Anforderung eines Kennworts“ die Option **15 Minuten** aus.
    -   Geben Sie für „Kennwortablauf (Tage)“ die Zahl 41 ein.
    -   Geben Sie für „Anzahl vorheriger Kennwörter, deren Wiederverwendung verhindert wird“ die Zahl 5 ein.
8.  Klicken Sie auf **OK** und dann erneut auf **OK**.
9.  Klicken Sie auf **Erstellen**.

## <a name="launch-slack"></a>Starten von Slack

Mit den Richtlinien, die Sie soeben erstellt haben, müssen alle Geräte mit iOS- oder Android-Arbeitsprofil, die versuchen, sich bei einem Ihrer Arbeitsbereiche anzumelden, bei Intune registriert sein. Um dieses Szenario zu testen, versuchen Sie, Slack for EMM auf einem bei Intune registrierten Gerät mit iOS-Arbeitsprofil oder Slack auf einem bei Intune registrierten Gerät mit Android-Arbeitsprofil zu starten. 

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial:
- Sie haben Intune in Ihrem Slack Enterprise Grid als EMM-Anbieter (Enterprise Mobility Management) festgelegt. 
- Sie haben App-Konfigurationsrichtlinien zur Verwaltung der Slack for EMM-App unter iOS und der Slack-App für Geräte mit Android-Arbeitsprofil erstellt.
- Sie haben Intune-Gerätekonformitätsrichtlinien zum Festlegen der Bedingungen erstellt, die iOS- und Android-Gerät erfüllen müssen, um als konform angesehen zu werden.

Weitere Informationen zu App-Konfigurationsrichtlinien finden Sie unter [App-Konfigurationsrichtlinien für Microsoft Intune](app-configuration-policies-overview.md). Weitere Informationen zu Gerätekonformitätsrichtlinien finden Sie unter [Legen Sie mit Intune Regeln auf Geräten fest, um Zugriff auf Ressourcen in Ihrer Organisation zu gewähren](device-compliance-get-started.md).