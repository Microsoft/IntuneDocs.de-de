---
title: Anmelden bei der Unternehmensportal-App | Microsoft-Dokumentation
description: Vorgehensweise beim Anmelden bei der Unternehmensportal-App auf verschiedenen Plattformen.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
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
ms.openlocfilehash: 370d6372cf3df2ff807069fe8d54f30da23e7ba2
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842608"
---
# <a name="how-do-i-sign-in-to-the-company-portal-app---user-story-1132123--"></a>Wie melde ich mich bei der Unternehmensportal-App an? <!--User Story 1132123-->

Mit der Unternehmensportal-App erhalten Sie Zugriff auf die Ressourcen Ihres Unternehmens, z.B. E-Mails und geschäftliche Apps. Sie haben zwei Möglichkeiten, sich beim Unternehmensportal anzumelden:

* Mit Ihrer geschäftlichen E-Mail-Adresse und Ihrem Kennwort
* Anmelden über ein anderes Gerät

Die folgenden Screenshots wurden unter iOS gemacht. Die Vorgehensweise auf Android- und Windows-Geräten ist aber nahezu identisch.

## <a name="signing-in-with-your-email-address-and-password"></a>Anmelden mit Ihrer E-Mail-Adresse und Ihrem Passwort

1. Öffnen Sie die Unternehmensportal-App auf dem Gerät, und tippen Sie auf **Anmelden**.

   ![Die Seite für die Anmeldung beim Unternehmensportal mit einem Symbol für eine Person vor der grafischen Darstellung einer Website. Darunter werden der Text „Get access to company resources and keep them secure“ (Erhalten Sie Zugriff auf Unternehmensressourcen, und sichern Sie diese) sowie die Schaltfläche „Anmelden“ angezeigt. Ein Link am unteren Seitenrand führt zu Informationen von Microsoft zu Datenschutz und Cookies.](/intune-user-help/media/cp_ios_aad_signin_after_1804_001.png)

   Sie haben die Unternehmensportal-App noch nicht installiert? Hier finden Sie die Anleitungen für den Download und die Installation unter [iOS](install-and-sign-in-to-the-intune-company-portal-app-ios.md) und [Android](install-the-company-portal-app-android.md).

2. Geben Sie Ihr **Geschäfts-, Schul- oder Unikonto** ein, und klicken Sie auf **Weiter**.

   ![Der Benutzer wird nur zur Eingabe der E-Mail-Adresse aufgefordert, nicht zur Eingabe von E-Mail-Adresse und Kennwort im gleichen Bildschirm.](/intune-user-help/media/cp_ios_aad_signin_after_1804_002.png)

3. Geben Sie Ihr Kennwort ein, und tippen Sie dann auf **Anmelden**.

   ![Der Benutzer wird erst zur Eingabe des Kennworts aufgefordert, wenn die E-Mail-Adresse akzeptiert wurde.](/intune-user-help/media/cp_ios_aad_signin_after_1804_003.png)

4. Nachdem Ihre Anmeldedaten in der Unternehmensportal-App akzeptiert wurden, werden Sie angemeldet und können auf Ihre Unternehmensressourcen zugreifen.   

   ![Nach Abschluss des Authentifizierungsprozesses meldet sich die Unternehmensportal-App an und zeigt einen entsprechenden Ladebalken an.](/intune-user-help/media/cp_ios_aad_signin_after_1804_004.png)

## <a name="signing-in-with-certificate-based-authentication"></a>Anmelden über die Zertifikat-basierte Authentifizierung

1.  Öffnen Sie die Unternehmensportal-App auf Ihrem Gerät.

2.  Geben Sie den Namen Ihres **Geschäfts- oder Schulkontos** ein.

3.  Tippen Sie auf den Link **Sign in with a certificate (Anmelden über ein Zertifikat)**.

4.  Tippen Sie auf **Fortfahren**, um das Zertifikat zu verwenden.

## <a name="signing-in-from-another-device"></a>Anmelden über ein anderes Gerät

Für den Zugriff auf Ihre Unternehmensressourcen können Sie statt einem Kennwort auch ein anderes Gerät verwenden, um zu bestätigen, dass Sie die richtige Person mit den richtigen Zugriffsrechten sind. Wenn in Ihrem Unternehmen der Computerzugriff per Smartcards geregelt wird, müssen Sie sich sehr wahrscheinlich über ein anderes Gerät anmelden.

1. Statt Ihre E-Mail-Adresse einzugeben, klicken Sie unter dem Textfeld für die E-Mail-Adresse auf den Link **Von anderem Gerät aus anmelden**.

   ![Auf der Anmeldeseite des Unternehmensportals müssen Benutzer ihre E-Mail-Adressen eingeben.  Darunter werden die Schaltfläche „Weiter“ und der Link „Sign in from another device“ (Über ein anderes Gerät anmelden) angezeigt. Außerdem wird der Link „Kein Zugriff auf Ihr Konto?“ angezeigt. Ein Link am unteren Seitenrand führt zu Informationen von Microsoft zu Datenschutz und Cookies.](/intune-user-help/media/cp_ios_aad_signin_after_1804_005.png)

2. Sie erhalten einen eindeutigen, einmal gültigen Code für die Anmeldung im Unternehmensportal.

   ![Der Benutzer erhält die Anweisung, mit einer über den Arbeitscomputer bezogenen eindeutigen Kennung zur Seite https://microsoft.com/devicelogin zu wechseln und sich dort mit dieser Kennung anzumelden.](/intune-user-help/media/cp_ios_aad_signin_after_1804_006.png)

3. Öffnen Sie auf Ihrem anderen Gerät einen Browser, und gehen Sie zu [https://microsoft.com/devicelogin](https://microsoft.com/devicelogin), um den Code einzugeben.

   ![Ein Bild des Browsers des Benutzers auf dem Arbeitscomputer statt in der Unternehmensportal-App. Die angezeigte Seite „Geräteanmeldung“ fordert den Benutzer auf, den über die Unternehmensportal-App empfangenen Code einzugeben.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. Sobald der auf der Seite **Geräteanmeldung** eingegebene Code überprüft wurde, klicken Sie auf __Weiter__, um dem Unternehmensportal die Anmeldung über Ihr anderes Gerät zu erlauben.

   ![Der Benutzer hat den eindeutigen Code in das Feld eingegeben und wurde auf der Seite „Geräteanmeldung“ aufgefordert, zu bestätigen, dass das Intune-Unternehmensportal die App ist, die zur Anmeldung autorisiert werden soll.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. Sobald der Code überprüft wurde, können Sie das Fenster schließen.

   ![Eine Bestätigungsseite informiert darüber, dass der Benutzer sich jetzt auf dem Gerät bei der Unternehmensportal-App angemeldet hat und dass diese Seite geschlossen werden kann.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. Auf Ihrem eigentlichen Gerät wird nur über die Unternehmensportal-App der Anmeldevorgang eingeleitet.

   ![Nach Abschluss des Authentifizierungsprozesses meldet sich die Unternehmensportal-App Sie an und zeigt einen entsprechenden Ladebalken an.](/intune-user-help/media/cp_ios_aad_signin_after_1804_007.png)

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).
