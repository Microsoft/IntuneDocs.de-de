---
title: 'Tutorial: Schützen des Exchange Online-E-Mail-Diensts auf durch Intune verwalteten Geräten'
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Exchange Online durch Intune-Konformitätsrichtlinien für iOS und bedingten Azure AD-Zugriff auf verwaltete Geräte und die Outlook-App schützen können.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 80f9d3d2799732f2d019189913c5c47cc6973809
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66044589"
---
# <a name="tutorial-protect-exchange-online-email-on-managed-devices"></a>Tutorial: Schützen des Exchange Online-E-Mail-Diensts auf verwalteten Geräten
In diesem Artikel erfahren Sie, wie Sie mithilfe von Gerätekonformitätsrichtlinien mit bedingtem Zugriff sicherstellen können, dass iOS-Geräte nur dann auf den Exchange Online-E-Mail-Dienst zugreifen können, wenn sie von Intune verwaltet werden und eine genehmigte E-Mail-App verwenden. 

In diesem Tutorial lernen Sie Folgendes: 
> [!div class="checklist"]
> * Erstellen einer Intune-iOS-Gerätekonformitätsrichtlinie zum Festlegen der Bedingungen, die ein Gerät erfüllen muss, um als konform angesehen zu werden
> * Erstellen einer Azure Active Directory-Richtlinie (Azure AD) für bedingten Zugriff, die von iOS-Geräten erfordert, sich bei Intune zu registrieren, Intune-Richtlinien zu erfüllen und die genehmigte mobile Outlook-App zu verwenden, um auf den Exchange Online-E-Mail-Dienst zugreifen zu können

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="prerequisites"></a>Voraussetzungen
  - Sie benötigen für dieses Tutorial einen Testmandanten mit den folgenden Abonnements:
    - Azure Active Directory Premium ([kostenlose Testversion](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
    - Office 365 Business-Abonnement, das Exchange Server ([kostenlose Testversion](https://go.microsoft.com/fwlink/p/?LinkID=510938)) umfasst
  - Bevor Sie beginnen, erstellen Sie ein Testgeräteprofil für iOS-Geräte, indem Sie die Schritte unter [Schnellstart: Erstellen eines E-Mail-Geräteprofils für iOS](quickstart-email-profile.md) ausführen.

## <a name="sign-in-to-intune"></a>Anmelden bei Intune

Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als globaler Administrator oder als Intune-Dienstadministrator. Wenn Sie ein Testabonnement für Intune erstellt haben, besitzt das Konto, mit dem Sie das Abonnement erstellt haben, die Rolle des globalen Administrators.

## <a name="create-the-ios-device-compliance-policy"></a>Erstellen der iOS-Gerätekonformitätsrichtlinie
Richten Sie eine Intune-Gerätekonformitätsrichtlinie ein, um die Bedingungen festzulegen, die ein Gerät erfüllen muss, um als konform angesehen zu werden. Für dieses Tutorial erstellen wir eine Gerätekonformitätsrichtlinie für iOS-Geräte. Konformitätsrichtlinien sind plattformspezifisch, weshalb Sie eine separate Konformitätsrichtlinie für jede Geräteplattform benötigen, die Sie auswerten möchten.

1.  Wählen Sie in Intune **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** aus.
2.  Geben Sie unter **Name** Folgendes ein: **Test für iOS-Konformitätsrichtlinie**. 
3.  Geben Sie unter **Beschreibung** Folgendes ein: **Test für iOS-Konformitätsrichtlinie**.
4.  Wählen Sie unter **Plattform** die Option **iOS** aus. 
5.  Klicken Sie auf **Einstellungen** > **E-Mail**. 
     
    1.  Klicken Sie neben **Verlangen, dass Mobilgeräte über ein verwaltetes E-Mail-Profil verfügen** auf **Erfordern**.
    2. Wählen Sie **OK** aus.

    ![Festlegen der E-Mail-Konformitätsrichtlinie, um ein verwaltetes E-Mail-Profil zu erfordern](media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-email.png)
    
6.  Klicken Sie auf **Geräteintegrität**. Klicken Sie neben **Geräte mit Jailbreak** auf **Blockieren** und dann auf **OK**.
7.  Klicken Sie auf **Systemsicherheit**, und geben Sie die **Kennwort**-Einstellungen an. Legen Sie für dieses Tutorial die folgenden empfohlenen Einstellungen fest:
     
    - Wählen Sie für **Ein Kennwort zum Entsperren von Mobilgeräten anfordern** **Erfordern** aus.
    - Wählen Sie für **Einfache Kennwörter** **Blockieren** aus.
    - Wählen Sie für **Minimale Kennwortlänge** **4** aus.
    - Wählen Sie für **Erforderlicher Kennworttyp** **Alphanumerisch** aus.
    - Wählen Sie für **Maximaler Zeitraum, bevor ein Kennwort erforderlich ist** **Sofort** aus.
    - Geben Sie für **Kennwortablauf (Tage)** **41** ein.
    - Geben Sie für **Anzahl vorheriger Kennwörter zum Verhindern der Wiederverwendung** **5** ein.
 
    ![Festlegen der Kennworteinstellungen für die E-Mail-Konformitätsrichtlinie](media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-system-security.png)

8.  Klicken Sie auf **OK** und erneut auf **OK**.
9.  Wählen Sie **Erstellen** aus.

## <a name="create-the-conditional-access-policy"></a>Erstellen der Richtlinie für bedingten Zugriff
Jetzt erstellen wir eine Richtlinie für bedingten Zugriff, die für den Zugriff auf Exchange Online von allen Geräteplattformen eine Registrierung bei Intune und die Erfüllung unserer Intune-Konformitätsrichtlinie verlangt. Zudem wird auch die Outlook-App für den E-Mail-Zugriff verlangt. Richtlinien für bedingten Zugriff können im Azure AD-Portal oder im Intune-Portal konfiguriert werden. Da wir uns bereits im Intune-Portal befinden, erstellen wir die Richtlinie über dieses Portal.
1.  Klicken Sie in Intune auf **Bedingter Zugriff** > **Richtlinien** > **Neue Richtlinie**.
1.  Geben Sie unter **Name** Folgendes ein: **Testrichtlinie für Office 365-E-Mail**. 
3.  Klicken Sie unter **Zuweisungen** auf **Benutzer und Gruppen**. Klicken Sie auf der Registerkarte **Einschließen** auf **Alle Benutzer** und dann auf **Fertig**.

4.  Klicken Sie unter **Zuweisungen** auf **Cloud-Apps**. Da wir den Office 365 Exchange Online-E-Mail-Dienst schützen möchten, wählen wir diese in den folgenden Schritten aus:
     
    1. Klicken Sie auf der Registerkarte **Einschließen** auf **Apps auswählen**.
    2. Klicken Sie auf **Auswählen**. 
    3. Klicken Sie in der Anwendungsliste auf **Office 365 Exchange Online** und dann auf **Auswählen**. 
    4. Wählen Sie **Fertig** aus.
  
    ![Auswählen der Office 365 Exchange Online-App](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-apps.png)

5.  Klicken Sie unter **Zuweisungen** auf **Bedingungen** > **Geräteplattformen**.
     
    1. Klicken Sie unter **Konfigurieren** auf **Ja**.
    2. Wählen Sie auf der Registerkarte **Einschließen** die Option **Alle Benutzer** und dann **Fertig** aus. 
    3. Klicken Sie erneut auf **Fertig**.
   
    ![Auswählen der Office 365 Exchange Online-App](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-device-platforms.png)

6.  Klicken Sie unter **Zuweisungen** auf **Bedingungen** > **Client-Apps**.
     
    1. Klicken Sie unter **Konfigurieren** auf **Ja**.
    2. Klicken Sie für dieses Tutorial auf **Mobile Apps und Desktopclients** und auf **Clients mit moderner Authentifizierung** (bezieht sich auf Apps wie Outlook für iOS und Outlook für Android). Deaktivieren Sie alle anderen Kontrollkästchen.
    3. Klicken Sie auf **Fertig** und dann erneut auf **Fertig**.
    
    ![Auswählen der Office 365 Exchange Online-App](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-client-apps.png)

7.  Klicken Sie unter **Zugriffssteuerungen** auf **Gewähren**. 
     
    1. Klicken Sie im Bereich **Gewähren** auf **Zugriff gewähren**.
    2. Klicken Sie auf **Markieren des Geräts als konform erforderlich**. 
    3. Klicken Sie auf **Genehmigte Client-App erforderlich**.
    4. Klicken Sie unter **Für mehrere Steuerelemente** auf **Alle ausgewählten Kontrollen anfordern**. Durch diese Einstellung wird sichergestellt, dass beide Anforderungen, die Sie ausgewählt haben, erzwungen werden, wenn ein Gerät versucht, auf E-Mails zuzugreifen.
    5. Klicken Sie auf **Auswählen**.
     
    ![Auswählen der Office 365 Exchange Online-App](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-grant-access.png)

8.  Klicken Sie unter **Richtlinie aktivieren** auf **Ein**.
     
    ![Auswählen der Office 365 Exchange Online-App](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-enable-policy.png)

9.  Wählen Sie **Erstellen** aus.

## <a name="try-it-out"></a>Probieren Sie es aus
Mit den von Ihnen erstellten Richtlinien müssen iOS-Geräte, die sich beim Office 365-E-Mail-Dienst anmelden, bei Intune registrieren und die mobile Outlook-App für iOS verwenden. Um dieses Szenario auf iOS-Geräten zu testen, melden Sie sich bei Exchange Online mit den Anmeldeinformationen für einen Benutzer auf Ihrem Testmandanten an. Sie werden aufgefordert, das Gerät zu registrieren und die mobile Outlook-App zu installieren.
1. Um dies auf einem iPhone zu testen, navigieren Sie zu **Einstellungen** > **Kennwörter & Konten** > **Konto hinzufügen** > **Exchange**.
2. Geben Sie die E-Mail-Adresse für einen Benutzer auf Ihrem Testmandanten ein, und klicken Sie dann auf **Weiter**.
3. Klicken Sie auf **Anmelden**.
4. Geben Sie das Kennwort des Testbenutzers ein, und klicken Sie auf **Anmelden**.
5. Eine Meldung wird angezeigt, die besagt, dass Ihr Gerät für den Zugriff auf die Ressource zusammen mit einer Option zur Registrierung verwaltet werden muss. 

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen
Wenn die Testrichtlinien nicht mehr benötigt werden, können Sie diese entfernen.
1. Registrieren Sie sich bei [Intune](https://aka.ms/intuneportal) als globaler Administrator oder als Intune-Dienstadministrator.
2. Klicken Sie auf **Gerätekonformität** > **Richtlinien**.
3. Rufen Sie in der Liste **Richtlinienname** das Kontextmenü (**...**) für Ihre Testrichtlinie auf, und klicken Sie dann auf **Löschen**. Klicken Sie zum Bestätigen auf **OK**.
4. Klicken Sie auf **Bedingter Zugriff** > **Richtlinien**.
5. Rufen Sie in der Liste **Richtlinienname** das Kontextmenü (**...**) für Ihre Testrichtlinie auf, und klicken Sie dann auf **Löschen**. Klicken Sie zum Bestätigen auf **Ja**.

 ## <a name="next-steps"></a>Nächste Schritte 
In diesem Tutorial haben Sie Richtlinien erstellt, die für den Zugriff auf den Exchange Online-E-Mail-Dienst von iOS-Geräten verlangen, sich bei Intune zu registrieren und die Outlook-App zu verwenden. Weitere Informationen zur Verwendung von Intune mit bedingtem Zugriff zum Schutz von anderen Apps und Diensten (z.B. Exchange ActiveSync-Clients für Office 365 Exchange Online) finden Sie unter [Was ist ein bedingter Zugriff?](conditional-access.md).
