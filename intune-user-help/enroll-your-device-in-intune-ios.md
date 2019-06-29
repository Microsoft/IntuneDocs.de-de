---
title: Einrichten des iOS-Gerätezugriffs auf Unternehmensressourcen | Microsoft-Dokumentation
description: Beschreibt die Aktivierung der Verwaltung Ihrer iOS-Geräte über Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4c8dfdea552d035c036828bfd2e6695cc5e4cb7b
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402734"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Einrichten des iOS-Gerätezugriffs auf Unternehmensressourcen  

Registrieren Sie Ihr iOS-Gerät bei der Intune-Unternehmensportal-App, um sicheren Zugriff auf E-Mails, Dateien und Apps Ihrer Organisation zu erhalten.

Sobald Ihr Gerät registriert ist, gilt es als *verwaltet*. Ihre Organisation kann dem Gerät über einen MDM-Anbieter (Mobile Device Management, Verwaltung mobiler Geräte) wie Intune Richtlinien und Anwendungen zuweisen.  

Um auf Ihrem Gerät auf Ihre Geschäfts-, Schul- oder Uniressourcen zugreifen zu können, müssen Sie Ihr Gerät entsprechend der von Ihrer Organisation bevorzugten Einstellungen konfigurieren. In diesem Artikel wird beschrieben, wie Sie mithilfe des Unternehmensportals Ihr Gerät registrieren und die Einstellungsanforderungen Ihrer Organisation erfüllen können.  
</br>
> [!VIDEO https://www.youtube.com/embed/mJyv6YcHi7c?rel=0]

> [!NOTE]
> Wenn Sie versucht haben, in der E-Mail-App auf Unternehmens-E-Mails zuzugreifen und aufgefordert wurden, Ihr Gerät verwalten zu lassen, sind Sie hier richtig. Befolgen Sie die untenstehenden Anweisungen, um über Ihr iOS-Gerät den Zugriff auf Ihre E-Mails und andere Unternehmensressourcen zu ermöglichen.  

## <a name="what-to-expect-from-the-company-portal-app"></a>Vorteile der Unternehmensportal-App  

### <a name="security"></a>Sicherheit  
Während der ersten Einrichtung werden Sie von der App aufgefordert, sich bei Ihrer Organisation zu authentifizieren. Anschließend werden Sie über alle notwendigen Geräteeinstellungen informiert, die Sie aktualisieren müssen. Beispielsweise legen Organisationen oft Anforderungen an die minimale oder maximale Zeichenanzahl des Kennworts fest, die Sie einhalten müssen.

### <a name="protection"></a>Schutz  
Nachdem Ihr Gerät registriert ist, wird es mithilfe der Unternehmensportal-App weiter geschützt. Wenn Sie beispielsweise eine App aus einer nicht vertrauenswürdigen Quelle installieren, benachrichtigt Sie die Unternehmensportal-App und entzieht Ihnen in manchen Fällen den Zugriff auf Unternehmensdaten. Diese Art von Richtlinie ist in Organisationen üblich und erfordert oft die Deinstallation der nicht vertrauenswürdigen App, ehe Sie Ihre Zugriffsrechte zurück erhalten.  

### <a name="setting-notifications"></a>Benachrichtigungseinstellungen  
Wenn Ihre Organisation nach der Registrierung eine neue Sicherheitsanforderung, wie beispielsweise eine mehrstufige Authentifizierung, durchsetzt, erhalten Sie eine Benachrichtigung von der Unternehmensportal-App. Sie haben dann die Möglichkeit, Ihre Einstellungen so zu ändern, dass Sie von Ihrem Gerät aus weiterarbeiten können.  

Weitere Informationen zur Registrierung finden Sie unter [Was geschieht, wenn ich die Unternehmensportal-App installiere und mein Gerät registriere?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>Registrieren Ihres iOS-Geräts  

Navigieren Sie zum App Store, um die [Intune-Unternehmensportal-App](install-and-sign-in-to-the-intune-company-portal-app-ios.md) auf Ihr Gerät herunterzuladen und zu installieren. Außerdem müssen Sie während der Registrierung über eine WLAN-Verbindung verfügen und Zugriff auf Safari haben. 

Eine Unterbrechung von mehr als einigen Minuten während der Registrierung kann dazu führen, dass die App das Setup schließt oder beendet. Öffnen Sie in diesem Fall die Unternehmensportal-App, und wiederholen Sie den Vorgang.  

1. Öffnen Sie das Unternehmensportal, und melden Sie sich mit Ihrem Geschäfts-, Schul- oder Unikonto an. 

    ![Beispielscreenshot der Anmeldung bei der Unternehmensportal-App.](./media/ios-01-cp-enroll-1904.PNG)  

2. Wenn Sie gefragt werden, ob Sie Benachrichtigungen vom Unternehmensportal empfangen möchten, tippen Sie auf **Zulassen.** Das Unternehmensportal informiert Sie anhand von Benachrichtigungen, wenn z.B. Ihre Geräteeinstellungen aktualisiert werden müssen. 

    ![Beispielscreenshot der Startseite des Unternehmensportals, Frage zu Benachrichtigungen.](./media/ios-02-cp-enroll-1904.PNG)  

3. Klicken Sie auf dem Bildschirm **Zugriff einrichten** auf **Anfang**.  

     ![Beispielscreenshot des Bildschirms „Zugriff einrichten“ im Unternehmensportal.](./media/ios-03-cp-enroll-1904.PNG)  

4. Lesen Sie die Liste der Geräteinformationen durch, die Ihre Organisation sehen kann und nicht sehen kann. Tippen Sie dann auf **Weiter**.  

5. Lesen Sie die Anweisungen auf dem Bildschirm **Wie geht es weiter?** . Wenn Sie bereit sind, das Verwaltungsprofil herunterzuladen und zu installieren, tippen Sie auf **Weiter**.  

 > [!IMPORTANT]
> Diese nächsten Schritte und Bildschirme sind je nach iOS-Version unterschiedlich. Führen Sie die Schritte für Ihre iOS-Version aus. 

6. Safari öffnet die Unternehmensportal-Website auf Ihrem Gerät. Wenn Sie aufgefordert werden, das Konfigurationsprofil herunterzuladen, tippen Sie auf **Zulassen**. Falls Sie ein Gerät haben mit:  
    * iOS 12.2 und höher: Wenn der Download abgeschlossen ist, tippen Sie auf **Fertig**. Fahren Sie mit Schritt 7 in diesem Artikel fort.
    * iOS 12.1 und früher: Sie werden automatisch zur App „Einstellungen“ umgeleitet. Fahren Sie mit Schritt 8 in diesem Artikel fort.  
 
    Wenn Sie versehentlich auf **Ignorieren** tippen sollten, aktualisieren Sie die Seite. Sie werden aufgefordert, die Unternehmensportal-App zu öffnen. In der App können Sie auf **Erneut herunterladen** tippen.

  > [!NOTE]
  > Sie müssen das Verwaltungsprofil, wie in den nächsten Schritten beschrieben, innerhalb von 8 Minuten nach dem Herunterladen installieren. Wenn dies nicht geschieht, wird das Profil entfernt, woraufhin Sie die Registrierung erneut starten müssen.  

7. iOS 12.2 oder neuer: Wenn Sie aufgefordert werden, das Unternehmensportal zu öffnen, tippen Sie auf **Öffnen**. Auf dem Bildschirm **Verwaltungsprofil installieren** sind die Schritte zum Installieren des Profils aufgelistet.

    ![Beispielscreenshot des Bildschirms „Verwaltungsprofil installieren“ im Unternehmensportal](./media/ios-07-cp-enroll-1904.PNG)  

8. Wechseln Sie zur App „Einstellungen“, und tippen Sie auf **Profil heruntergeladen**.  

    Wenn **Profil heruntergeladen** nicht als Option angezeigt wird, wechseln Sie zu **Allgemein** > **Profile**. Wenn das Profil weiterhin nicht angezeigt wird, müssen Sie es möglicherweise erneut herunterladen.  

    ![Beispielscreenshot der App „Einstellungen“ mit der Einstellung „Profil heruntergeladen“.](./media/ios-1904-settings-badge.PNG)  

9. Tippen Sie auf **Installieren**.  
    
10. Geben Sie das Gerätekennwort ein. Tippen Sie dann auf **Installieren**.    

    ![Beispielscreenshot der App „Einstellungen“ mit dem Bildschirm „Profil installieren“ mit Cursor auf der Schaltfläche „Installieren“.](./media/ios-10-cp-enroll-1904.PNG)  


11. Der nächste Bildschirm ist eine standardmäßige Systemwarnung für die Geräteverwaltung. Um mit der Installation fortzufahren, tippen Sie auf **Installieren**. Wenn Sie aufgefordert werden, der Remoteverwaltung zu vertrauen, tippen Sie auf **Vertrauen**.  

    ![Beispielscreenshot der App „Einstellungen“ mit dem Bildschirm mit einer standardmäßigen Systemwarnung zu Stammzertifikat und Verwaltung mobiler Geräte.](./media/ios-11-cp-enroll-1904.PNG)  

12. Klicken Sie nach Abschluss der Installation auf **Fertig**. Um zu bestätigen, dass das Profil installiert wurde, wechseln Sie zu den Einstellungen unter **Profile und Geräteverwaltung**. Daraufhin sollte das Profile unter **Verwaltung mobiler Geräte** aufgeführt sein.   

    ![Beispielscreenshot der App „Einstellungen“ mit den Einstellungen unter „Profile und Geräteverwaltung“ mit gezeigtem Verwaltungsprofil.](./media/ios-12-cp-enroll-1904.PNG)  

13. Kehren Sie zur Unternehmensportal-App zurück. Das Unternehmensportal beginnt mit der Synchronisierung und Einrichtung Ihres Geräts. Das Unternehmensportal fordert Sie möglicherweise auf, zusätzliche Geräteeinstellungen zu aktualisieren. Wenn das der Fall ist, tippen Sie auf **Weiter**.  

    ![Beispielscreenshot der Unternehmensportal-App, Bildschirm „Zugriff einrichten“ mit gelbem Dreieck neben einer geforderten Einstellung.](./media/ios-13-cp-enroll-1904.PNG)  

14. Sie erkennen, dass das Setup abgeschlossen ist, wenn alle Elemente in der Liste einen grünen Kreis aufweisen. Tippen Sie auf **Fertig**.   
    
    ![Beispielscreenshot des Unternehmensportals mit der Meldung „Alles erledigt!“ Es werden nur grüne Kreise angezeigt.](./media/ios-14-cp-enroll-1904.PNG)  

> [!Note]
> Wenn in Ihrer Organisation Obergrenzen für Gesprächsminuten oder Datenvolumen gelten oder sie Ihnen ein unternehmenseigenes Gerät zur Verfügung stellt, müssen Sie möglicherweise noch einige weitere Schritte durchführen. Wenn Sie aufgefordert werden, die App **Datalert** zu installieren, lesen Sie [Registrieren Ihres Geräts im Telecom Expense Management](enroll-your-device-with-telecom-expense-management-ios.md). Wenn Ihr Unternehmen am Apple-Programm zur Geräteregistrierung teilnimmt, finden Sie heraus, [wie Sie Ihr unternehmenseigenes Gerät registrieren können](enroll-your-device-dep-ios.md).  

## <a name="it-administrator-support"></a>Unterstützung für IT-Administratoren  
Wenn Sie IT-Administrator sind und Probleme bei der Registrierung von Geräten haben, lesen Sie [Behandeln von Problemen bei der Registrierung von iOS-Geräten in Microsoft Intune](https://support.microsoft.com/en-us/help/4039809). Dieser Artikel listet häufige Fehler, ihre Ursachen und Schritte zur Behebung auf.  

## <a name="next-steps"></a>Nächste Schritte  
Finden Sie Apps, die Ihnen bei der Arbeit oder in der Schule oder Hochschule helfen. Erfahren Sie, wie über das Unternehmensportal [Apps zur Verfügung gestellt werden](use-managed-apps-on-your-device-ios.md).  

Benötigen Sie weitere Unterstützung? Kontaktieren Sie die Supportabteilung Ihres Unternehmens. Sie finden entsprechende Kontaktinformationen auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).  
