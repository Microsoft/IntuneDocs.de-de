---
title: 'Tutorial: Schützen des Exchange Online-E-Mail-Diensts auf nicht verwalteten Geräten'
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Office 365 Exchange Online mit Intune-App-Schutzrichtlinien und dem bedingten Zugriff in Azure AD sichern.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/11/2018
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8339f91468abca548b3923df4d4380aabb88c5a8
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848711"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>Tutorial: Schützen des Exchange Online-E-Mail-Diensts auf nicht verwalteten Geräten

Erfahren Sie, wie Sie App-Schutzrichtlinien mit bedingtem Zugriff verwenden, um Exchange Online zu schützen, auch wenn Geräte nicht in einer Geräteverwaltungslösung wie Intune registriert sind. In diesem Tutorial lernen Sie Folgendes: 

> [!div class="checklist"]
> * Erstellen einer Intune-App-Schutzrichtlinie für die Outlook-App. Sie schränken die möglichen Aktivitäten von Benutzern für App-Daten ein, indem Sie „Speichern unter“-Aktionen ganz verhindern und Optionen zum Ausschneiden, Kopieren und Einfügen begrenzen. 
> * Erstellen Sie Richtlinien für den bedingten Zugriff in Azure Active Directory (Azure AD), mit denen die Outlook-App in Exchange Online nur auf Unternehmens-E-Mails zugreifen darf. Sie fordern auch die mehrstufige Authentifizierung (Multi-Factor Authentication, MFA) für Clients mit moderner Authentifizierung wie Outlook für iOS und Android an.

## <a name="prerequisites"></a>Voraussetzungen
  - Sie benötigen für dieses Tutorial einen Testmandanten mit den folgenden Abonnements:
    - Azure Active Directory Premium ([kostenlose Testversion](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
    - Intune-Abonnement ([kostenlose Testversion](free-trial-sign-up.md))
    - Office 365 Business-Abonnement, das Exchange Server ([kostenlose Testversion](https://go.microsoft.com/fwlink/p/?LinkID=510938)) umfasst

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als globaler Administrator oder als Intune-Dienstadministrator. Intune finden Sie im Azure-Portal, indem Sie **Alle Dienste** > **Intune** auswählen.

## <a name="create-the-app-protection-policy"></a>Erstellen der App-Schutzrichtlinie
In diesem Tutorial richten wir eine Intune-App-Schutzrichtlinie für die Outlook-App ein, mit der Schutzfunktionen auf App-Ebene aktiviert werden. Wir fordern eine PIN zum Öffnen einer App in einem geschäftlichen Kontext an. Wir beschränken auch die gemeinsame Datennutzung von Apps und verhindern, dass Unternehmensdaten in privaten Speicherorten gespeichert werden.

1.  Klicken Sie in Intune auf **Client-Apps** > **App-Schutzrichtlinien** > **Richtlinie hinzufügen**.
2.  Geben Sie **Outlook-App-Richtlinientest** als **Namen** ein.
3.  Geben Sie **Outlook-App-Richtlinientest** als **Beschreibung** ein.
4.  Klicken Sie auf **Apps**. Wählen Sie in der Liste der Apps den Eintrag **Outlook** aus, und klicken Sie auf **Auswählen**.
5.  Klicken Sie auf **Einstellungen**. 
6.  Wählen Sie unter **Datenverschiebung** für dieses Tutorial die folgenden Einstellungen aus:

    - Wählen Sie für **Zulassen, dass die App Daten an andere Apps überträgt** die Option **Keine** aus.
    - Wählen Sie für **Zulassen, dass die App Daten von anderen Apps empfängt** die Option **Keine** aus.
    - Wählen Sie für **"Speichern unter" verhindern** die Option **Ja** aus.
    - Wählen Sie für **Ausschneiden, Kopieren und Einfügen mit anderen Apps einschränken** die Option **Blockiert** aus.
   
     ![Auswählen der Einstellungen für die Datenverschiebung im Rahmen der Outlook-App-Schutzrichtlinie](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-data-relocation.png)
    
7.  Wählen Sie unter **Zugriffsaktionen** für dieses Tutorial die folgenden Einstellungen aus:

    - Wählen Sie für **PIN für Zugriff anfordern** die Option **Ja** aus.
    - Wählen Sie unter **Unternehmensanmeldeinformationen für den Zugriff erforderlich** die Option **Ja** aus.
    - Behalten Sie für alle anderen Einstellungen die Standardwerte bei.
 
     ![Auswählen der Zugriffsaktionen im Rahmen der Outlook-App-Schutzrichtlinie](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-access-actions.png)

9.  Wählen Sie **OK** aus.
10. Wählen Sie **Erstellen** aus.

Die App-Schutzrichtlinie für Outlook wird erstellt. Jetzt können Sie den bedingten Zugriff einrichten, um zu erzwingen, dass Geräte die Outlook-App verwenden.

## <a name="create-conditional-access-policies"></a>Erstellen von Richtlinien für den bedingten Zugriff
Nun erstellen wir zwei Richtlinien für den bedingten Zugriff, um alle Geräteplattformen abzudecken. Die erste Richtlinie erfordert, dass Clients mit moderner Authentifizierung wie Outlook für iOS und Outlook für Android die genehmigte Outlook-App sowie die mehrstufige Authentifizierung verwenden. Die zweite Richtlinie erfordert, dass Exchange ActiveSync-Clients die genehmigte Outlook-App verwenden. (Zurzeit unterstützt Exchange Active Sync keine anderen Bedingungen als die Geräteplattform). Sie können Richtlinien für den bedingten Zugriff im Azure AD-Portal oder im Intune-Portal konfigurieren. Da wir uns bereits im Intune-Portal befinden, erstellen wir die Richtlinie über dieses Portal.
### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>Erstellen einer MFA-Richtlinie für Clients mit moderner Authentifizierung
1.  Klicken Sie in Intune auf **Bedingter Zugriff** > **Richtlinien** > **Neue Richtlinie**.
1.  Geben Sie **Testrichtlinie für Clients mit moderner Authentifizierung** als **Namen** ein. 
3.  Klicken Sie unter **Zuweisungen** auf **Benutzer und Gruppen**. Klicken Sie auf der Registerkarte **Einschließen** auf **Alle Benutzer** und dann auf **Fertig**.

4.  Klicken Sie unter **Zuweisungen** auf **Cloud-Apps**. Da wir den Office 365 Exchange Online-E-Mail-Dienst schützen möchten, wählen wir diese in den folgenden Schritten aus:
     
    1. Klicken Sie auf der Registerkarte **Einschließen** auf **Apps auswählen**.
    2. Klicken Sie auf **Auswählen**. 
    3. Klicken Sie in der Anwendungsliste auf **Office 365 Exchange Online** und dann auf **Auswählen**. 
    4. Wählen Sie **Fertig** aus.
  
    ![Auswählen der Office 365 Exchange Online-App](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

5.  Klicken Sie unter **Zuweisungen** auf **Bedingungen** > **Geräteplattformen**.
     
    1. Klicken Sie unter **Konfigurieren** auf **Ja**.
    2. Klicken Sie auf der Registerkarte **Einschließen** auf **Alle Plattformen (auch nicht unterstützte)**. 
    3. Wählen Sie **Fertig** aus.
   
6.  Wählen Sie im Bereich **Bedingungen** die Option **Client-Apps** aus.
     
    1. Klicken Sie unter **Konfigurieren** auf **Ja**.
    2. Wählen Sie **Mobile Apps und Desktopclients** und **Clients mit moderner Authentifizierung** aus.
    3. Deaktivieren Sie alle anderen Kontrollkästchen.
    4. Klicken Sie auf **Fertig** und dann erneut auf **Fertig**.
    
    ![Auswählen der Office 365 Exchange Online-App](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

7.  Klicken Sie unter **Zugriffssteuerungen** auf **Gewähren**. 
     
    1. Klicken Sie im Bereich **Gewähren** auf **Zugriff gewähren**.
    2. Wählen Sie **Mehrstufige Authentifizierung erforderlich** aus.
    4. Klicken Sie auf **Genehmigte Client-App erforderlich**.
    5. Klicken Sie unter **Für mehrere Steuerelemente** auf **Alle ausgewählten Kontrollen anfordern**. Durch diese Einstellung wird sichergestellt, dass beide Anforderungen, die Sie ausgewählt haben, erzwungen werden, wenn ein Gerät versucht, auf E-Mails zuzugreifen.
    6. Klicken Sie auf **Auswählen**.
     
    ![Auswählen der Office 365 Exchange Online-App](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

8.  Klicken Sie unter **Richtlinie aktivieren** auf **Ein**.
     
    ![Auswählen der Office 365 Exchange Online-App](media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)

9.  Wählen Sie **Erstellen** aus.

Die Richtlinie für bedingten Zugriff für Clients mit moderner Authentifizierung wird erstellt. Jetzt können Sie eine Richtlinie für Exchange Active Sync-Clients erstellen.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Erstellen einer Richtlinie für Exchange Active Sync-Clients
1.  Klicken Sie in Intune auf **Bedingter Zugriff** > **Richtlinien** > **Neue Richtlinie**.
2.  Geben Sie **Testrichtlinie für EAS-Clients** als **Namen** ein. 
3.  Klicken Sie unter **Zuweisungen** auf **Benutzer und Gruppen**. Klicken Sie auf der Registerkarte **Einschließen** auf **Alle Benutzer** und dann auf **Fertig**.

4.  Klicken Sie unter **Zuweisungen** auf **Cloud-Apps**. Wählen Sie die Option für Office 365 Exchange Online-E-Mail folgendermaßen aus:
     
    1. Klicken Sie auf der Registerkarte **Einschließen** auf **Apps auswählen**.
    2. Klicken Sie auf **Auswählen**. 
    3. Klicken Sie in der Anwendungsliste auf **Office 365 Exchange Online** und dann auf **Auswählen**. 
    4. Wählen Sie **Fertig** aus.

5.  Klicken Sie unter **Zuweisungen** auf **Bedingungen** > **Geräteplattformen**.
     
    1. Klicken Sie unter **Konfigurieren** auf **Ja**.
    2. Klicken Sie auf der Registerkarte **Einschließen** auf **Alle Plattformen (auch nicht unterstützte)** und dann auf **Fertig**. 
    3. Klicken Sie erneut auf **Fertig**.

6.  Wählen Sie im Bereich **Bedingungen** die Option **Client-Apps** aus.
     
    1. Klicken Sie unter **Konfigurieren** auf **Ja**.
    2. Wählen Sie **Mobile Apps und Desktopclients** aus.
    3. Wählen Sie **Exchange ActiveSync-Clients** und **Richtlinie nur auf unterstützte Plattformen anwenden** aus. 
    4. Deaktivieren Sie alle anderen Kontrollkästchen.
    5. Klicken Sie auf **Fertig** und dann erneut auf **Fertig**.
    
    ![Auswählen der Office 365 Exchange Online-App](media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)

7.  Klicken Sie unter **Zugriffssteuerungen** auf **Gewähren**. 
     
    1. Klicken Sie im Bereich **Gewähren** auf **Zugriff gewähren**.
    4. Klicken Sie auf **Genehmigte Client-App erforderlich**. Deaktivieren Sie alle anderen Kontrollkästchen.
    6. Klicken Sie auf **Auswählen**.
     
    ![Auswählen der Office 365 Exchange Online-App](media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)

8.  Klicken Sie unter **Richtlinie aktivieren** auf **Ein**.

9.  Wählen Sie **Erstellen** aus.

Die App-Schutzrichtlinien und der bedingte Zugriff sind jetzt eingerichtet und können getestet werden. 

## <a name="try-it-out"></a>Probieren Sie es aus
Mit den von Ihnen erstellten Richtlinien müssen Geräte sich bei Intune registrieren und die mobile Outlook-App verwenden, um auf Office 365-E-Mails zuzugreifen. Um dieses Szenario auf iOS-Geräten zu testen, melden Sie sich bei Exchange Online mit den Anmeldeinformationen für einen Benutzer auf Ihrem Testmandanten an.
1. Um dies auf einem iPhone zu testen, navigieren Sie zu **Einstellungen** > **Kennwörter & Konten** > **Konto hinzufügen** > **Exchange**.
2. Geben Sie die E-Mail-Adresse für einen Benutzer auf Ihrem Testmandanten ein, und klicken Sie dann auf **Weiter**.
3. Klicken Sie auf **Anmelden**.
4. Geben Sie das Kennwort des Testbenutzers ein, und klicken Sie auf **Anmelden**.
5. Die Meldung **Es sind weitere Informationen erforderlich** wird angezeigt, mit der Sie aufgefordert werden, die mehrstufige Authentifizierung einzurichten. Richten Sie eine zusätzliche Überprüfungsmethode ein.
6. Danach werden Sie in einer Meldung darüber informiert, dass Sie versuchen, diese Ressource mit einer App zu öffnen, die von Ihrer IT-Abteilung nicht genehmigt ist. Das bedeutet, dass die Nutzung der nativen Mail-App für Sie gesperrt ist. Brechen Sie die Anmeldung ab.
7.  Öffnen Sie die Outlook-App, und klicken Sie auf **Einstellungen** > **Konto hinzufügen** > **E-Mail-Konto hinzufügen**.
8. Geben Sie die E-Mail-Adresse für einen Benutzer auf Ihrem Testmandanten ein, und klicken Sie dann auf **Weiter**.
9. Klicken Sie auf **Mit Office 365 anmelden**. Sie werden aufgefordert, weitere Authentifizierungs- und Registrierungsinformationen anzugeben. Nachdem Sie sich angemeldet haben, können Sie Aktionen wie „Ausschneiden“, „Kopieren“, „Einfügen“ und „Speichern unter“ testen.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen
Wenn die Testrichtlinien nicht mehr benötigt werden, können Sie diese entfernen.
1. Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als globaler Administrator oder als Intune-Dienstadministrator.
2. Klicken Sie auf **Gerätekonformität** > **Richtlinien**.
3. Rufen Sie in der Liste **Richtlinienname** das Kontextmenü (**...**) für Ihre Testrichtlinie auf, und klicken Sie dann auf **Löschen**. Klicken Sie zum Bestätigen auf **OK**.
4. Klicken Sie auf **Bedingter Zugriff** > **Richtlinien**.
5. Öffnen Sie in der Liste **Richtlinienname** das Kontextmenü (**...**) für jede Ihrer Testrichtlinien, und klicken Sie dann auf **Löschen**. Klicken Sie zum Bestätigen auf **Ja**.

 ## <a name="next-steps"></a>Nächste Schritte 
In diesem Tutorial haben Sie App-Schutzrichtlinien erstellt, um die Aktionen zu begrenzen, die ein Benutzer in der Outlook-App ausführen kann. Sie haben zudem Richtlinien für den bedingten Zugriff erstellt, um die Outlook-App sowie die mehrstufige Authentifizierung für Clients mit moderner Authentifizierung zu erzwingen. Weitere Informationen zur Verwendung von Intune mit bedingtem Zugriff zum Schutz von anderen Apps und Diensten finden Sie unter [Einrichten des bedingten Zugriffs](conditional-access.md).
