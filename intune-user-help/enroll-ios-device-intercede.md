---
title: Registrieren eines IOS-oder ipados-Geräts mit InTune-Unternehmensportal und Intercede
description: Erfahren Sie, wie Sie ein IOS-oder ipados-Gerät registrieren und die Authentifizierung abgeleiteter Anmelde Informationen mit Intercede einrichten.
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
ms.collection: M365-identity-device-management
ms.openlocfilehash: 02293b29f8634161582af2348b1cb30039ca3c52
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415710"
---
# <a name="set-up-ios-or-ipados-device-with-company-portal-and-intercede"></a>Einrichten eines IOS-oder ipados-Geräts mit Unternehmensportal und Intercede

Registrieren Sie Ihr Gerät bei der Intune-Unternehmensportal-App, um sicheren mobilen Zugriff auf E-Mails, Dateien und Apps Ihrer Organisation zu erhalten.  Sobald Ihr Gerät registriert ist, gilt es als *verwaltet*. Ihre Organisation kann dem Gerät über einen MDM-Anbieter (Mobile Device Management, Verwaltung mobiler Geräte) wie Intune Richtlinien und Anwendungen zuweisen.  

Während der Registrierung installieren Sie auch abgeleitete Anmelde Informationen auf Ihrem Gerät. In Ihrer Organisation ist es möglicherweise erforderlich, dass Sie die abgeleiteten Anmelde Informationen als Authentifizierungsmethode für den Zugriff auf Ressourcen oder zum Signieren und Verschlüsseln von e-Mails verwenden. 

Sie müssen wahrscheinlich eine abgeleitete Anmelde Information einrichten, wenn Sie eine Smartcard für Folgendes verwenden:

* Anmelden bei Schul-oder Arbeits-apps, Wi-Fi und virtuellen privaten Netzwerken (VPN)
* Signieren und Verschlüsseln von Schul-oder Geschäfts-e-Mails mithilfe von S/MIME  

Folgendes wird in diesem Artikel beschrieben:  

* Registrieren Sie ein mobiles IOS-oder ipados-Gerät mit InTune-Unternehmensportal.  
* Erhalten Sie vom abgeleiteten Anmelde Informationsanbieter Ihrer Organisation abgeleitete Anmelde Informationen ( [Intercede](https://www.intercede.com/)).   


## <a name="what-are-derived-credentials"></a>Was sind abgeleitete Anmelde Informationen?  
Abgeleitete Anmelde Informationen sind ein Zertifikat, das von ihren Smartcard-Anmelde Informationen abgeleitet und auf Ihrem Gerät installiert ist. Dadurch erhalten Sie Remote Zugriff auf Arbeitsressourcen und verhindern, dass nicht autorisierte Benutzer auf sensible Informationen zugreifen.  

Abgeleitete Anmelde Informationen werden für Folgendes verwendet: 
* Authentifizieren von Schülern und Mitarbeitern, die sich bei Schul-oder Arbeits-apps, Wi-Fi und VPN anmelden
* Signieren und Verschlüsseln von Schul-oder geschäftliche e-Mails mit S/MIME-Zertifikaten  

Abgeleitete Anmeldeinformationen sind eine Implementierung der NIST-Richtlinien (National Institute of Standards and Technology) für PIV-Anmeldeinformationen (Personal Identity Verification) aus SP 800-157 (Special Publication).  

## <a name="prerequisites"></a>Voraussetzungen

 Um die Registrierung abzuschließen, benötigen Sie Folgendes:

* Ihre Schul-oder arbeitsbereit gestellte Smartcard
* Zugriff auf einen Computer oder einen Self-Service-Kiosk, auf dem Sie sich mit Ihrer Smartcard anmelden können
* Ihr mobiles Gerät
* Die Intune-Unternehmensportal-App für IOS und ipados, die auf Ihrem Gerät installiert ist


## <a name="enroll-device"></a>Registrieren eines Geräts  
1. Öffnen Sie die Unternehmensportal-App für IOS/ipados auf Ihrem mobilen Gerät, und melden Sie sich mit Ihrem Geschäftskonto an.  
2. Notieren Sie sich den Code, der auf dem Bildschirm angezeigt wird.  

    ![Beispiel Bild der Unternehmensportal-App mit Bildschirm Meldung und Code.](./media/copy-code-intercede.png)  
1. Wechseln Sie zu Ihrem smartcardfähigen Gerät, und wechseln Sie zu https://microsoft.com/devicelogin. 

1. Geben Sie den Code ein, den Sie zuvor notiert haben.
 
2. Fügen Sie Ihre Smartcard ein, um sich anzumelden.   

3. Kehren Sie zur Unternehmensportal-App auf Ihrem mobilen Gerät zurück, und befolgen Sie die Anweisungen auf dem Bildschirm, um Ihr Gerät zu registrieren.  
4. Nach Abschluss der Registrierung werden Sie von Unternehmensportal benachrichtigt, dass Sie Ihre Smartcard einrichten. Tippen Sie auf die Benachrichtigung. Wenn Sie keine Benachrichtigung erhalten, überprüfen Sie Ihre e-Mail-Adresse.   

    ![Beispiel eines Screenshots der Unternehmensportal Pushbenachrichtigung auf dem Startbildschirm des Geräts.](./media/action-required-in-app-intercede.png)  

5. Auf dem Bildschirm **Mobile Smartcard-Zugriff einrichten** :  
    ein. Tippen Sie auf den Link zu den Setup Anweisungen Ihrer Organisation. Wenn Ihre Organisation keine weiteren Anweisungen bereitstellt, werden Sie zu diesem Artikel weitergeleitet.  
    b. Tippen Sie auf **starten**.  

    ![Screenshot der Unternehmensportal Einrichten des mobilen smartcardzugriffs (Bildschirm).](./media/smart-card-info-intercede.png)  

6. Wechseln Sie zu Ihrem smartcardfähigen Gerät oder Self-Service-Kiosk, und öffnen Sie die myid-app. Melden Sie sich mit Ihren Anmelde Informationen an.  
7. Wählen Sie die Option zum Anfordern der ID aus. 
8. Wenn Sie gefragt werden, welches Profil Sie verwenden möchten, wählen Sie die Option zum Aktivieren mit mobilen Anmelde Informationen aus. Ein QR-Code wird angezeigt.  
9. Wechseln Sie zurück zu Ihrem mobilen Gerät. Tippen Sie auf dem Bildschirm Unternehmensportal > **QR-Code** anzeigen auf **weiter**.  

    ![Screenshot des Bildschirms "Unternehmensportal Get QR Code".](./media/get-qr-code-intercede.png) 
 
10. Tippen Sie auf **Kamera verwenden** > **OK**.  

    ![Beispiel eines Screenshots einer Unternehmensportal Aufforderung, die die Berechtigung zum Zulassen des Kamera Zugriffs anfordert.](./media/allow-cp-camera-access-intercede.png)  

11. Scannen Sie das Bild des QR-Codes auf Ihrem smartcardfähigen Gerät. 
12. Warten Sie, bis Unternehmensportal das Einrichten Ihres Geräts abgeschlossen haben.  

## <a name="next-steps"></a>Nächste Schritte  
Nachdem die Registrierung durchgeführt wurde, haben Sie Zugriff auf Arbeitsressourcen wie e-Mail, Wi-Fi und alle apps, die Ihre Organisation zur Verfügung stellt. Weitere Informationen zum Installieren und Deinstallieren von apps im Unternehmensportal finden Sie unter:

* [Verwalten von Apps von der Unternehmensportalwebsite](manage-apps-cpweb.md)  
* [Verwenden verwalteter Apps auf Ihrem Gerät](use-managed-apps-on-your-device-ios.md)  

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).
