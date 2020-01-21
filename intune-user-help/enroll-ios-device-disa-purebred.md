---
title: Registrieren eines IOS-oder ipados-Geräts mit InTune-Unternehmensportal und DISA purebred
description: Erfahren Sie, wie Sie ein IOS-oder ipados-Gerät registrieren und die Authentifizierung abgeleiteter Anmelde Informationen mit DISA-purebred einrichten.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilver
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 31858828cbbfaa1ca71d94f6e0f568c35bb490c1
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856578"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-disa-purebred"></a>Einrichten eines IOS-oder ipados-Geräts mit Unternehmensportal und DISA purebred  

Registrieren Sie Ihr Gerät bei der Intune-Unternehmensportal-App, um sicheren mobilen Zugriff auf E-Mails, Dateien und Apps Ihrer Organisation zu erhalten. Sobald Ihr Gerät registriert ist, gilt es als *verwaltet*. Ihre Organisation kann dem Gerät über einen MDM-Anbieter (Mobile Device Management, Verwaltung mobiler Geräte) wie Intune Richtlinien und Anwendungen zuweisen.  

Während der Registrierung installieren Sie auch abgeleitete Anmelde Informationen auf Ihrem Gerät. In Ihrer Organisation ist es möglicherweise erforderlich, dass Sie die abgeleiteten Anmelde Informationen als Authentifizierungsmethode für den Zugriff auf Ressourcen oder zum Signieren und Verschlüsseln von e-Mails verwenden. 

Sie müssen wahrscheinlich eine abgeleitete Anmelde Information einrichten, wenn Sie eine Smartcard für Folgendes verwenden:

* Anmelden bei Schul-oder Arbeits-apps, Wi-Fi und virtuellen privaten Netzwerken (VPN)
* Signieren und Verschlüsseln von Schul-oder Geschäfts-e-Mails mithilfe von S/MIME  

Folgendes wird in diesem Artikel beschrieben:  

   * Registrieren Sie ein mobiles IOS-oder ipados-Gerät mit InTune-Unternehmensportal.  
   * Sie erhalten abgeleitete Anmelde Informationen vom abgeleiteten Anmelde Informationsanbieter Ihrer Organisation, [DISA purebred](https://cyber.mil/pki-pke/purebred/).  

## <a name="what-are-derived-credentials"></a>Was sind abgeleitete Anmelde Informationen?  
Abgeleitete Anmelde Informationen sind ein Zertifikat, das von ihren Smartcard-Anmelde Informationen abgeleitet und auf Ihrem Gerät installiert ist. Dadurch erhalten Sie Remote Zugriff auf Arbeitsressourcen und verhindern, dass nicht autorisierte Benutzer auf sensible Informationen zugreifen.  

Abgeleitete Anmelde Informationen werden für Folgendes verwendet: 
* Authentifizieren von Schülern und Mitarbeitern, die sich bei Schul-oder Arbeits-apps, Wi-Fi und VPN anmelden
* Signieren und Verschlüsseln von Schul-oder geschäftliche e-Mails mit S/MIME-Zertifikaten

Abgeleitete Anmeldeinformationen sind eine Implementierung der NIST-Richtlinien (National Institute of Standards and Technology) für PIV-Anmeldeinformationen (Personal Identity Verification) aus SP 800-157 (Special Publication).  

## <a name="prerequisites"></a>Voraussetzungen

 Um die Registrierung abzuschließen, benötigen Sie Folgendes:

* Ihre Schul-oder arbeitsbereit gestellte Smartcard
* Zugriff auf einen Computer oder Kiosk, auf dem Sie sich mit Ihrer Smartcard anmelden können
* Ihr mobiles Gerät
* Die Intune-Unternehmensportal-App für IOS und ipados, die auf Ihrem Gerät installiert ist   

Beim Setup müssen Sie sich auch an einen purebred Agent oder einen repräsentativen Mitarbeiter wenden.      

## <a name="enroll-device"></a>Registrieren eines Geräts  
1. Öffnen Sie die Unternehmensportal-App für IOS/ipados auf Ihrem mobilen Gerät, und melden Sie sich mit Ihrem Geschäftskonto an.  

2. Notieren Sie sich den Bildschirm-Code.  

    ![Beispiel Bild der Unternehmensportal-App mit Bildschirm Meldung und Code.](./media/copy-code-intercede.png)  
3. Wechseln Sie zu Ihrem smartcardfähigen Gerät, und wechseln Sie zu https://microsoft.com/devicelogin. 
4. Geben Sie den Code ein, den Sie zuvor notiert haben.  

    ![Beispiel-Screenshot der Eingabeaufforderung "Code eingeben" der Unternehmensportal Website.](./media/enter-code-intercede.png)   

5. Fügen Sie Ihre Smartcard ein, um sich anzumelden.  
6. Kehren Sie zur Unternehmensportal-App auf Ihrem mobilen Gerät zurück, und befolgen Sie die Anweisungen auf dem Bildschirm, um Ihr Gerät zu registrieren.  
7. Nach Abschluss der Registrierung werden Sie von Unternehmensportal benachrichtigt, dass Sie Ihre Smartcard einrichten. Tippen Sie auf die Benachrichtigung. Wenn Sie keine Benachrichtigung erhalten, überprüfen Sie Ihre e-Mail-Adresse.   

    ![Beispiel eines Screenshots der Unternehmensportal Pushbenachrichtigung auf dem Startbildschirm des Geräts.](./media/action-required-in-app-intercede.png)  
8. Auf dem Bildschirm **Mobile Smartcard-Zugriff einrichten** :  
    a. Tippen Sie auf den Link zu den Setup Anweisungen Ihrer Organisation. Wenn Ihre Organisation keine weiteren Anweisungen bereitstellt, werden Sie zu diesem Artikel weitergeleitet.  
    b. Klicken Sie auf **Öffnen** , um die purebred-APP zu öffnen.  

    ![Screenshot der Unternehmensportal Einrichten des mobilen smartcardzugriffs (Bildschirm).](./media/smart-card-open-disa-purebred.png)  
9. Wenn Sie aufgefordert werden, Unternehmensportal das Öffnen der purebred-Registrierungs-App zuzulassen, wählen Sie **Öffnen**aus.   

    ![Beispiel eines Screenshots der Unternehmensportal Aufforderung zum Öffnen der DISA-purebred app.](./media/open-app-prompt-disa-purbred.png)  
10. Wenn die APP funktioniert, arbeiten Sie mit dem purebred Agent Ihrer Organisation zusammen, um das purebred-Konfigurations Profil vor der Registrierung zu konfigurieren und herunterzuladen.   
11. Wechseln Sie zur App "Einstellungen" > " **Allgemeine** > **Profile & Geräteverwaltung** > **Installieren** Sie Profile, und tippen Sie auf **Installieren**.  
12. Geben Sie Ihren Gerätepasscode ein.  
13. Installieren des Profils Sie müssen möglicherweise mehr als einmal **Installieren** , um die Installation zu starten. 
14. Kehren Sie zur purebred-Registrierungs-app zurück. Befolgen Sie die Anweisungen Ihres purebred Agents, um den Vorgang fortzusetzen.  
 
15. Nachdem Sie das Konfigurations Profil heruntergeladen haben, wechseln Sie zur App "Einstellungen" > " **Allgemeine** > **Profile & Geräteverwaltung** > **Installieren** Sie Profile, und tippen Sie auf **Installieren**.   
16.  Geben Sie Ihren Gerätepasscode ein.
17. Installieren des Profils Sie müssen möglicherweise mehr als einmal **Installieren** , um die Installation zu starten. 
18. Kehren Sie nach Abschluss der Installation zur Unternehmensportal-app zurück.  
19.  Tippen Sie auf dem Bildschirm **Mobile Smartcard-Zugriff einrichten** auf **weiter**.  

20. Auf dem Bildschirm **Zertifikate importieren** rufen Sie die abgeleiteten Anmelde Informationen ab, die Sie von DISA purebred erhalten haben, und importieren Sie.  

    a. Tippen Sie auf **Weiter**.   

    ![Beispiel Bildschirm Abbildung des Bildschirms Unternehmensportal Festlegen der Zertifikate importieren.](./media/import-certificate-disa-purebred.png)  
    b. Wechseln Sie zu icloud Drive **Durchsuchen** > **Standorte** , und tippen Sie auf **weitere Speicherorte**.  

    ![Screenshot des icloud-Laufwerks, Menü "Durchsuchen", das die Option "weitere Speicherorte](./media/icloud-drive-more-locations.png)  
    c. Tippen Sie zum Aktivieren der **purebred Key-Kette**auf den Schalter.  

    ![Screenshot des icloud-Laufwerks, browseinsicht, das hervorgehoben ist, dass der Schalter der purebred Key-Kette aktiviert ist.](./media/icloud-drive-enable-purebred-keychain.png)   

    d. Tippen Sie auf **purebred Credential Package**.  

    ![Screenshot eines IOS-Bildschirms mit einer auswählbaren purebred Credential Package-Option.](./media/purebred-credential-package.png)  
    f. Eine Liste der Zertifikate wird angezeigt. Wählen Sie eine aus, und tippen Sie dann auf **Schlüssel importieren**  

    ![Beispiel eines Screenshots einer Liste auswählbarer Zertifikate, bei dem bereits eine ausgewählt ist.](./media/import-purebred-keychain.png) 
21. Kehren Sie zur Unternehmensportal-app zurück, und warten Sie, bis Unternehmensportal das Einrichten Ihres Geräts abgeschlossen haben.   

## <a name="next-steps"></a>Nächste Schritte  
Nachdem die Registrierung durchgeführt wurde, haben Sie Zugriff auf Arbeitsressourcen wie e-Mail, Wi-Fi und alle apps, die Ihre Organisation zur Verfügung stellt. Weitere Informationen zum Installieren und Deinstallieren von apps im Unternehmensportal finden Sie unter:

* [Verwalten von Apps von der Unternehmensportalwebsite](manage-apps-cpweb.md)  
* [Verwenden verwalteter Apps auf Ihrem Gerät](use-managed-apps-on-your-device-ios.md)  

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).
