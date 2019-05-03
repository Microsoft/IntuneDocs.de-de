---
title: Einrichten des iOS-Gerätezugriffs auf Unternehmensressourcen | Microsoft-Dokumentation
description: Beschreibt die Aktivierung der Verwaltung Ihrer iOS-Geräte über Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/05/2019
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
ms.openlocfilehash: d0c7ac239a67a51ba7165771206883f3c46f5f55
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292423"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Einrichten des iOS-Gerätezugriffs auf Unternehmensressourcen  

Registrieren Sie Ihr iOS-Gerät bei der Intune-Unternehmensportal-App, um sicheren Zugriff auf E-Mails, Dateien und Apps Ihrer Organisation zu erhalten.

Nachdem Ihr Gerät registriert ist, wird es *verwaltet*. Ihrer Organisation kann das Gerät über einen mobile Device Management (MDM)-Anbieter, wie z.B. Intune-Richtlinien und apps zuweisen.  

Um von Ihrem Gerät aus auf Ihre Geschäfts-, Schul- oder Uniressourcen zugreifen zu können, müssen Sie Ihr Gerät entsprechend der von Ihrer Organisation bevorzugten Einstellungen konfigurieren. Dieser Artikel beschreibt, wie Sie die Unternehmensportal-App verwenden, registrieren Sie Geräte und Anforderungen Ihrer Organisation verwalten. 

> [!NOTE]
> Wenn Sie versucht haben, in der E-Mail-App auf Unternehmens-E-Mails zuzugreifen und aufgefordert wurden, Ihr Gerät verwalten zu lassen, sind Sie hier richtig. Befolgen Sie die untenstehenden Anweisungen, um über Ihr iOS-Gerät den Zugriff auf Ihre E-Mails und andere Unternehmensressourcen zu ermöglichen.  

## <a name="what-to-expect-from-the-company-portal-app"></a>Vorteile der Unternehmensportal-App  

### <a name="security"></a>Sicherheit  
Während der ersten Einrichtung werden Sie von der App aufgefordert, sich bei Ihrer Organisation zu authentifizieren. Anschließend werden Sie über alle notwendigen Geräteeinstellungen informiert, die Sie aktualisieren müssen. Beispielsweise legen Organisationen oft Anforderungen an die minimale oder maximale Zeichenanzahl des Kennworts fest, die Sie einhalten müssen.     

### <a name="protection"></a>Schutz  
Nachdem Ihr Gerät registriert ist, wird es mithilfe der Unternehmensportal-App weiter geschützt. Wenn Sie beispielsweise eine App aus einer nicht vertrauenswürdigen Quelle installieren, benachrichtigt Sie die Unternehmensportal-App und entzieht Ihnen in manchen Fällen den Zugriff auf Unternehmensdaten. Diese Art von Richtlinie kommt häufig bei Unternehmen und häufig erfordert, dass Sie die nicht vertrauenswürdige app deinstallieren, bevor Sie erneut zugreifen können.  

### <a name="setting-notifications"></a>Benachrichtigungseinstellungen  
Wenn Ihre Organisation nach der Registrierung eine neue Sicherheitsanforderung, wie beispielsweise eine mehrstufige Authentifizierung, durchsetzt, erhalten Sie eine Benachrichtigung von der Unternehmensportal-App. Sie haben dann die Möglichkeit, Ihre Einstellungen so zu ändern, dass Sie von Ihrem Gerät aus weiterarbeiten können.  

Weitere Informationen zur Registrierung finden Sie unter [Was geschieht, wenn ich die Unternehmensportal-App installiere und mein Gerät registriere?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>Registrieren Ihres iOS-Geräts  

Wechseln Sie zu den appstore herunterladen und Installieren der [Intune-Unternehmensportal-app](install-and-sign-in-to-the-intune-company-portal-app-ios.md) auf Ihrem Gerät. Sie müssen auch eine Wi-Fi-Verbindung aufrechterhalten und haben Zugriff auf Safari, während der Registrierung. 

Wird der Prozess für mehr als ein paar Minuten, während der Registrierung kann dazu führen, dass die app schließen, oder Beenden von Setup. In diesem Fall, öffnen Sie die Unternehmensportal-app, und versuchen Sie es erneut.  

1. Öffnen Sie das Unternehmensportal, und melden Sie sich mit Ihrem Geschäfts-, Schul- oder Unikonto an. 

    ![Beispielscreenshot der Unternehmensportal-app anmelden.](./media/ios-01-cp-enroll-1903.PNG)  

2. Wenn Sie aufgefordert werden, die Unternehmensportal-App-Benachrichtigungen zu empfangen, tippen Sie auf **zulassen.** Unternehmensportal-App verwendet Benachrichtigungen, um Sie zu warnen, wenn Sie beispielsweise Ihren geräteeinstellungen aktualisiert werden müssen. 

    ![Beispielscreenshot der Homepage "Unternehmensportal", "Benachrichtigungen"-Eingabeaufforderung.](./media/ios-04-cp-enroll-1903.PNG)  

3. Auf der **Einrichten des Zugriffs** auf **beginnen.**  

     ![Beispielscreenshot der Unternehmensportal-App, Bildschirm "Einrichten von Zugriff".](./media/ios-05-cp-enroll-1903.PNG)  

4. Lesen Sie die Liste der Geräteinformationen Ihrer Organisation bzw. nicht sehen kann. Tippen Sie dann auf **Weiter**.  

5. Lesen die Anweisungen auf der **Ausblick?** Bildschirm. Wenn Sie bereit zum Herunterladen und Installieren des verwaltungsprofils tippen sind **Weiter**.  

 > [!IMPORTANT]
> Diesen nächsten Schrittfolgen und Bildschirme variiert abhängig von Ihrer iOS-Version. Führen Sie die Schritte für Ihre iOS-Version aus. 

6. Safari wird auf Ihrem Gerät die Unternehmensportal-Website geöffnet. Wenn Sie dazu aufgefordert werden, um das Konfigurationsprofil herunterzuladen, tippen Sie auf **zulassen**. Wenn Sie auf einem Gerät mit sind:  
    * iOS 12.2 und höher: Wenn der Download abgeschlossen ist, tippen Sie auf **durchgeführt.** Fahren Sie mit Schritt 7 in diesem Artikel.
    * iOS 12.1 und früher: Sie werden automatisch zu der Einstellungs-app umgeleitet. Fahren Sie mit Schritt 8 in diesem Artikel.  
 
    Wenn Sie versehentlich tippen **ignorieren**, aktualisieren Sie die Seite. Sie werden aufgefordert, die Unternehmensportal-app zu öffnen. Sie können von der app, tippen **erneut heruntergeladen,**.

  > [!NOTE]
  > Sie müssen das verwaltungsprofil wie beschrieben in den nächsten Schritten innerhalb von 8 Minuten herunterladen installieren. Falls nicht, das Profil entfernt werden, und Sie die Registrierung neu starten müssen.  

7. iOS 12.2 oder neuer: Wenn Sie aufgefordert werden, öffnen Sie die Unternehmensportal-App, tippen Sie auf **öffnen**. Die **Verwaltungsprofil installieren** Bildschirm werden die Schritte zum Installieren des Profils.

    ![Beispielscreenshot der Unternehmensportal-App, Verwaltungsprofil installieren Bildschirm.](./media/ios-1904-settings-icon.PNG)  

8. Wechseln Sie zu der Einstellungs-app, und tippen Sie auf **Profil heruntergeladen**.  

    Wenn **Profil heruntergeladen** nicht als Option angezeigt wird, wechseln Sie zu **allgemeine** > **Profile**. Wenn Sie das Profil weiterhin nicht angezeigt wird, müssen Sie möglicherweise erneut herunterladen.  

    ![Beispielscreenshot der Einstellungen-app, heruntergeladenen Profil festlegen.](./media/ios-1904-settings-badge.PNG)  

9. Tippen Sie auf **Installieren**.  
    
10. Ändern Sie Ihr Gerätekennwort. Tippen Sie dann auf **installieren**.    

    ![Beispielhafter Screenshot der Einstellungen-app, Bildschirm "Profil installieren", mit der ein Cursor für die ** installieren ** Schaltfläche.](./media/ios-1904-password-install.PNG)  


11. Im nächste Bildschirm wird eine Warnung Standardsystem für die geräteverwaltung. Um mit der Installation fortzufahren, tippen Sie auf **installieren**. Wenn Sie aufgefordert werden, die remote-Verwaltung vertrauen, tippen Sie auf **Vertrauensstellung**.  

    ![Beispielscreenshot der app "Einstellungen", Standardsystem Warnbildschirm für das Stammzertifikat und die Verwaltung mobiler Geräte.](./media/ios-15-cp-enroll-1903.PNG)  

12. Nachdem die Installation abgeschlossen ist, tippen Sie auf **Fertig**. Um sicherzustellen, dass das Profil installiert wurde, wechseln Sie zu der **Profile und Geräteverwaltung** Einstellungen. Daraufhin sollte die Profile unter **Verwaltung mobiler Geräte**.   

    ![Beispielhafter Screenshot der Einstellungs-app, Profile und Geräteverwaltung Einstellungen, die das verwaltungsprofil angezeigt.](./media/ios-00-cp-enroll-1903.PNG)  

13. Kehren Sie zur Unternehmensportal-App zurück. Unternehmensportal-App wird gestartet, um zu synchronisieren, und richten Sie Ihr Gerät. Unternehmensportal-App können Sie zusätzliche Einstellungen für Geräte aktualisieren aufgefordert. Wenn es der Fall ist, tippen **Weiter**.  

    ![Beispielscreenshot der Unternehmensportal-App, Bildschirm "Einrichten von Zugriff" mit dem gelben Dreieck neben der Anforderung festlegen.](./media/ios-12-cp-enroll-1903.PNG)  

14. Sie wissen, dass das Setup abgeschlossen ist, wenn alle Elemente in der Liste einen grünen Kreis angezeigt. Tippen Sie auf **Fertig**.   
    
    ![Beispielscreenshot der Unternehmensportal-App, "Sie alles erledigt!" Bildschirm, alle grüne Kreise angezeigt.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> Wenn es sich bei Ihrer Organisation überwacht die Sprach- und die Grenzwerte oder ein unternehmenseigenes Gerät bietet, müssen Sie möglicherweise einige weitere Schritte ausführen. Wenn Sie aufgefordert werden, installieren Sie die **Datalert** -app finden Sie unter [Registrierung Ihres Geräts im Telecom Expense Management](enroll-your-device-with-telecom-expense-management-ios.md). Wenn Ihre Organisation Teil des Apple Device Enrollment Program ist, informieren Sie sich [wie zum Registrieren Ihres unternehmenseigenen Geräts](enroll-your-device-dep-ios.md).  

## <a name="next-steps"></a>Nächste Schritte  
Apps, mit denen Sie bei der Arbeit oder Schule zu finden. Erfahren Sie, [wie apps zur Verfügung gestellt werden](use-managed-apps-on-your-device-ios.md) Ihnen über die Unternehmensportal-App.  

Benötigen Sie weitere Unterstützung? Kontaktieren Sie die Supportabteilung Ihres Unternehmens. Sie finden entsprechende Kontaktinformationen auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).  
