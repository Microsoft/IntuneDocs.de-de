---
title: Anmelden bei der Unternehmensportal-App | Microsoft-Dokumentation
description: Vorgehensweise beim Anmelden bei der Unternehmensportal-App auf verschiedenen Plattformen.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cfd214bc-f072-4808-af2e-a3cbf7af9bca
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6bfd8496061b4b3aba2589b73c3e98bce94a5011
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67528651"
---
# <a name="sign-in-to-company-portal"></a>Melden Sie sich beim Unternehmensportal  

Es gibt drei Möglichkeiten zur Anmeldung beim Unternehmensportal-app:

* Anmeldung mit Ihrer geschäftlichen E-Mail-Adresse und Ihrem Kennwort  
* Anmeldung über die zertifikatbasierte Authentifizierung  
* Anmeldung über ein anderes Gerät    


## <a name="sign-in-with-your-email-address-and-password"></a>Anmeldung mit Ihrer E-Mail-Adresse und Ihrem Kennwort
Die folgenden Schritte zeigen die Screenshots aus der Unternehmensportal-App für iOS.  

1. Öffnen Sie die app auf dem Gerät und Tap **Anmeldung**.  

   ![Die Seite für die Anmeldung beim Unternehmensportal mit einem Symbol für eine Person vor der grafischen Darstellung einer Website. Darunter werden der Text „Greifen Sie auf Unternehmensressourcen zu, und sorgen Sie für deren Schutz.“ sowie die Schaltfläche „Anmelden“ angezeigt. Ein Link am unteren Seitenrand führt zu Informationen von Microsoft zu Datenschutz und Cookies.](/intune-user-help/media/cp_ios_aad_signin_after_1804_001.png)



2. Geben Sie Ihr **Geschäfts-, Schul- oder Unikonto** ein, und klicken Sie auf **Weiter**.

   ![Der Benutzer wird nur zur Eingabe der E-Mail-Adresse aufgefordert, nicht zur Eingabe von E-Mail-Adresse und Kennwort im gleichen Bildschirm.](/intune-user-help/media/cp_ios_aad_signin_after_1804_002.png)

3. Geben Sie Ihr Kennwort ein, und tippen Sie dann auf **Anmelden**.

   ![Der Benutzer wird erst zur Eingabe des Kennworts aufgefordert, wenn die E-Mail-Adresse akzeptiert wurde.](/intune-user-help/media/cp_ios_aad_signin_after_1804_003.png)

4. Die app werden Ihre Anmeldeinformationen überprüfen. Abschließend können Sie Zugriff auf die Ressourcen Ihres Unternehmens, und Installieren verfügbarer apps.  

   ![Nach dem Durchlaufen des Authentifizierungsprozesses erfolgt die Anmeldung bei der Unternehmensportal-App, und es wird ein Balken zum Ladefortschritt angezeigt.](/intune-user-help/media/cp_ios_aad_signin_after_1804_004.png)

## <a name="sign-in-with-certificate-based-authentication"></a>Anmeldung über die zertifikatbasierte Authentifizierung

1. Öffnen Sie die Unternehmensportal-App auf Ihrem Gerät.  

2. Geben Sie den Namen Ihres **Geschäfts- oder Schulkontos** ein.  

3. Tippen Sie auf den Link **Sign in with a certificate (Anmelden über ein Zertifikat)** .  

4. Tippen Sie auf **Fortfahren**, um das Zertifikat zu verwenden.  

## <a name="sign-in-from-another-device"></a>Anmeldung über ein anderes Gerät

Wenn Ihr Unternehmen Smartcards verwendet, den Zugriff auf Ihre Computer, ist es wahrscheinlich, dass Sie durch Ihre Anmeldung von einem anderen Gerät authentifizieren müssen.  

1. Öffnen Sie die Unternehmensportal-App auf Ihrem Gerät. Stellen Sie sicher, dass es sich um das Gerät handelt, die, das Sie verwenden möchten, die Zugriff auf Ihre Arbeitsressourcen.       

1. Wählen Sie **melden Sie sich von einem anderen Gerät**.  

   ![Auf der Anmeldeseite für das Unternehmensportal werden die Benutzer zur Eingabe ihrer E-Mail-Adresse aufgefordert.  Ferner werden die Schaltfläche „Weiter“ und der Link „Von anderem Gerät aus anmelden“ angezeigt. Außerdem wird der Link „Kein Zugriff auf Ihr Konto?“ angezeigt. Ein Link am unteren Seitenrand führt zu Informationen von Microsoft zu Datenschutz und Cookies.](/intune-user-help/media/cp_ios_aad_signin_after_1804_005.png)

2. Sie erhalten einen eindeutigen, einmal gültigen Code für die Anmeldung im Unternehmensportal. Kopieren Sie den Code ein.

   ![Der Benutzer erhält die Anweisung, mit einer über den Arbeitscomputer bezogenen eindeutigen Kennung zur Seite https://microsoft.com/devicelogin zu wechseln und sich dort mit dieser Kennung anzumelden.](/intune-user-help/media/cp_ios_aad_signin_after_1804_006.png)

3. Auf Ihrem anderen Gerät (die eine, die Sie zur Authentifizierung verwenden), öffnen Sie Ihren Browser, und wechseln Sie zu [ https://microsoft.com/devicelogin ](https://microsoft.com/devicelogin). Geben Sie an, oder fügen Sie den Code.  

   ![Ein Bild des Browsers des Benutzers auf dem Arbeitscomputer statt in der Unternehmensportal-App. Die angezeigte Seite „Geräteanmeldung“ fordert den Benutzer auf, den über die Unternehmensportal-App empfangenen Code einzugeben.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. Wählen Sie __Weiter__ auf der Unternehmensportal-App für die Anmeldung auf dem Gerät arbeiten kann.   

   ![Der Benutzer hat den eindeutigen Code in das Feld eingegeben und wurde auf der Seite „Geräteanmeldung“ aufgefordert, zu bestätigen, dass das Intune-Unternehmensportal die App ist, die zur Anmeldung autorisiert werden soll.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. Sobald der Code überprüft wurde, können Sie das Fenster schließen.  

   ![Eine Bestätigungsseite informiert darüber, dass der Benutzer sich jetzt auf dem Gerät bei der Unternehmensportal-App angemeldet hat und dass diese Seite geschlossen werden kann.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. Die Unternehmensportal-app angemeldet auf Ihrem Gerät arbeiten.  

   ![Nach Abschluss des Authentifizierungsprozesses meldet sich die Unternehmensportal-App Sie an und zeigt einen entsprechenden Ladebalken an.](/intune-user-help/media/cp_ios_aad_signin_after_1804_007.png)

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).  
