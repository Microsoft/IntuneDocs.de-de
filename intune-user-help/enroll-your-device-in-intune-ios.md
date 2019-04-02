---
title: Einrichten des iOS-Gerätezugriffs auf Unternehmensressourcen | Microsoft-Dokumentation
description: Beschreibt die Aktivierung der Verwaltung Ihrer iOS-Geräte über Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/26/2019
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
ms.openlocfilehash: ee0f438d929abd6b5b90acbaeeddc41e3ce11f98
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490641"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Einrichten des iOS-Gerätezugriffs auf Unternehmensressourcen  

Registrieren Sie Ihr iOS-Gerät bei der Intune-Unternehmensportal-App, um sicheren Zugriff auf E-Mails, Dateien und Apps Ihrer Organisation zu erhalten.

Bevor Sie von einem firmeneigenen oder persönlichen Gerät aus auf proprietäre Daten zugreifen können, müssen Sie Ihr Gerät verwalten lassen. Sobald es sich dann um ein verwaltetes Gerät handelt, überträgt Ihre Organisation über einen Anbieter für mobile Geräteverwaltung (z.B. Intune) Richtlinien und Apps auf das Gerät. 

Um von Ihrem Gerät aus auf Ihre Geschäfts-, Schul- oder Uniressourcen zugreifen zu können, müssen Sie Ihr Gerät entsprechend der von Ihrer Organisation bevorzugten Einstellungen konfigurieren. Dieser Artikel beschreibt, wie Sie die Unternehmensportal-App verwenden, registrieren Sie Geräte und Anforderungen Ihrer Organisation verwalten. 

> [!NOTE]
> Wenn Sie versucht haben, in der E-Mail-App auf Unternehmens-E-Mails zuzugreifen und aufgefordert wurden, Ihr Gerät verwalten zu lassen, sind Sie hier richtig. Befolgen Sie die untenstehenden Anweisungen, um über Ihr iOS-Gerät den Zugriff auf Ihre E-Mails und andere Unternehmensressourcen zu ermöglichen.  

## <a name="what-to-expect-from-the-company-portal-app"></a>Vorteile der Unternehmensportal-App  

### <a name="security"></a>Sicherheit  
Während der ersten Einrichtung werden Sie von der App aufgefordert, sich bei Ihrer Organisation zu authentifizieren. Anschließend werden Sie über alle notwendigen Geräteeinstellungen informiert, die Sie aktualisieren müssen. Beispielsweise legen Organisationen oft Anforderungen an die minimale oder maximale Zeichenanzahl des Kennworts fest, die Sie einhalten müssen.     

### <a name="protection"></a>Schutz  
Nachdem Ihr Gerät registriert ist, wird es mithilfe der Unternehmensportal-App weiter geschützt. Wenn Sie beispielsweise eine App aus einer nicht vertrauenswürdigen Quelle installieren, benachrichtigt Sie die Unternehmensportal-App und entzieht Ihnen in manchen Fällen den Zugriff auf Unternehmensdaten. Eine solche Richtlinie kommt häufig bei Unternehmen, und häufig erfordert, dass Sie die nicht vertrauenswürdige app deinstallieren, bevor Sie erneut zugreifen können.  

### <a name="setting-notifications"></a>Benachrichtigungseinstellungen  
Wenn Ihre Organisation nach der Registrierung eine neue Sicherheitsanforderung, wie beispielsweise eine mehrstufige Authentifizierung, durchsetzt, erhalten Sie eine Benachrichtigung von der Unternehmensportal-App. Sie haben dann die Möglichkeit, Ihre Einstellungen so zu ändern, dass Sie von Ihrem Gerät aus weiterarbeiten können.  

Weitere Informationen zur Registrierung finden Sie unter [Was geschieht, wenn ich die Unternehmensportal-App installiere und mein Gerät registriere?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios).  

## <a name="enroll-your-ios-device"></a>Registrieren Ihres iOS-Geräts   

> [!IMPORTANT]
> Die Screenshots in diesem Abschnitt zeigen die Erfahrung für Geräte unter iOS-Version, 12.1 und früher. Falls zutreffend, haben wir die Anweisungen, die spezifisch für iOS-Version 12.2 und höher eingefügt. Wenn Sie feststellen, dass Ihre Umgebung von den hier gezeigten Screenshots unterscheidet, finden Sie in den 12.2 Anweisungen werden müssen.      

Wechseln Sie zu den appstore herunterladen und Installieren der [Intune-Unternehmensportal-app](install-and-sign-in-to-the-intune-company-portal-app-ios.md) auf Ihrem Gerät. Während der Registrierung benötigen Sie auch eine Wi-Fi-Verbindung und den Zugriff auf Safari. 

Wenn Sie mehr als ein paar Minuten, während der Registrierung anhalten, kann die app schließen, oder Setup zu beenden. In diesem Fall, öffnen Sie die Unternehmensportal-app, und versuchen Sie es erneut.  

1. Öffnen Sie das Unternehmensportal, und melden Sie sich mit Ihrem Geschäfts-, Schul- oder Unikonto an. 

    ![Beispielscreenshot der Unternehmensportal-app anmelden.](./media/ios-01-cp-enroll-1903.PNG)  

2. Wenn Sie aufgefordert werden, die Unternehmensportal-App-Benachrichtigungen zu empfangen, tippen Sie auf **zulassen.** Unternehmensportal-App verwendet Benachrichtigungen, um Sie zu warnen, wenn Sie beispielsweise Ihren geräteeinstellungen aktualisiert werden müssen. 

    ![Beispielscreenshot der Homepage "Unternehmensportal", "Benachrichtigungen"-Eingabeaufforderung.](./media/ios-04-cp-enroll-1903.PNG)  

3. Auf der **Einrichten des Zugriffs** auf **beginnen.**  

     ![Beispielscreenshot der Unternehmensportal-App, Bildschirm "Einrichten von Zugriff".](./media/ios-05-cp-enroll-1903.PNG)  

4. Lesen Sie die Liste der Geräteinformationen Ihrer Organisation bzw. nicht sehen kann. [Weitere Informationen zu diesem Thema](what-info-can-your-company-see-when-you-enroll-your-device-in-Intune.md) finden Sie über die **erfahren Sie mehr** Link. Wenn Sie fertig sind, tippen Sie auf **Weiter**.  

    ![Beispielhafter Screenshot der Unternehmensportal-app "Was sehen Meine Organisation", mit der Schaltfläche "Weiter".](./media/ios-06-cp-enroll-1903.PNG)  
 
5. Die **Ausblick?** Bildschirm werden die verbleibenden Schritte zusammengefasst. Diese Schritte können abhängig von Ihrer iOS-Version unterscheiden. 
    * **iOS 12.2 und höher**: Sie stattdessen Ihre Erfahrungen müssen eventuell:  

        ein. **Download des verwaltungsprofils erlauben**: Browsers öffnen Sie die Unternehmensportal-Website wird, und Sie werden aufgefordert, den Download zulassen. Der Download wird in der Einstellungen-app gespeichert werden.  

        b. **Öffnen Sie die Einstellungen-app, und installieren Sie das Profil**: Sie müssen die Einstellungs-app und das verwaltungsprofil installieren.  

        c. **Wechseln Sie zurück zur Unternehmensportal-app**: Sie müssen zurück an den Unternehmensportal-app, um die Installation abzuschließen.  

    Wenn Sie das verwaltungsprofil herunterladen möchten, tippen Sie auf **Weiter**.  

6. Safari wird die Unternehmensportal-Website geöffnet. Wenn Sie dazu aufgefordert werden, um das Konfigurationsprofil herunterzuladen, tippen Sie auf **zulassen**.  
    * **iOS 12.2 und höher**: Warten auf das Profil heruntergeladen wurde in Safari und dann auf **Fertig**. Öffnen Sie dann die App **Einstellungen** auf Ihrem Gerät.  

    > [!IMPORTANT]
    > Wechseln Sie zu der **Einstellungen** app herunter, und installieren Sie dieses Profil innerhalb von 8 Minuten herunterladen. Falls nicht, das Profil entfernt werden, und Sie die Registrierung neu starten müssen. 

7. In der **Einstellungen** app, tippen Sie auf **heruntergeladene Profil installieren** > **installieren**. Wenn **heruntergeladene Profil installieren** nicht als Option angezeigt wird, wechseln Sie zu **allgemeine** > **Profile**. Wenn Sie das Profil weiterhin nicht angezeigt wird, müssen Sie möglicherweise erneut herunterladen.  

    ![Beispielhafter Screenshot der Einstellungen-app, heruntergeladene Profil installieren-Einstellung, mit einer roten Signal mit einem heruntergeladenen Profil.](./media/ios-10-cp-enroll-1903.PNG)  
    
8. Wenn Sie dazu aufgefordert werden, geben Sie das Gerätekennwort aus. Tippen Sie dann auf **installieren**.      

9. Im nächste Bildschirm wird eine Warnung Standardsystem für die geräteverwaltung. Weitere Informationen finden Sie Informationen zu was Ihrer Organisation zugreifen bzw. nicht auf Ihrem Gerät sehen kann, finden Sie unter der entsprechenden [Intune dokumentationsartikel](what-info-can-your-company-see-when-you-enroll-your-device-in-Intune.md). Um mit der Installation fortzufahren, tippen Sie auf **installieren**. Wenn Sie aufgefordert werden, die remote-Verwaltung vertrauen, tippen Sie auf **Vertrauensstellung**.  

    ![Beispielscreenshot der app "Einstellungen", Standardsystem Warnbildschirm für das Stammzertifikat und die Verwaltung mobiler Geräte.](./media/ios-15-cp-enroll-1903.PNG)  

10. Nachdem die Installation abgeschlossen ist, tippen Sie auf **Fertig**. Um sicherzustellen, dass das Profil installiert wurde, wechseln Sie zu der **Profile und Geräteverwaltung** Einstellungen. Daraufhin sollte die Profile unter **Verwaltung mobiler Geräte**.   

    ![Beispielhafter Screenshot der Einstellungs-app, Profile und Geräteverwaltung Einstellungen, die das verwaltungsprofil angezeigt.](./media/ios-00-cp-enroll-1903.PNG)  


11. Kehren Sie zur **Unternehmensportal**-App zurück. Unternehmensportal-App wird gestartet, um zu synchronisieren, und richten Sie Ihr Gerät. Unternehmensportal-App können Sie zusätzliche Einstellungen für Geräte aktualisieren aufgefordert. Wenn es der Fall ist, tippen **Weiter**.

    ![Beispielscreenshot der Unternehmensportal-App, Bildschirm "Einrichten von Zugriff" mit dem gelben Dreieck neben der Anforderung festlegen.](./media/ios-12-cp-enroll-1903.PNG)  

12. Sie wissen, dass das Setup abgeschlossen ist, wenn alle Elemente in der Liste einen grünen Kreis angezeigt. Tippen Sie auf **Fertig**.  
    
    ![Beispielscreenshot der Unternehmensportal-App, "Sie alles erledigt!" Bildschirm, alle grüne Kreise angezeigt.](./media/ios-13-cp-enroll-1903.PNG)  

> [!Note]
> Wenn es sich bei Ihrer Organisation überwacht die Sprach- und die Grenzwerte oder ein unternehmenseigenes Gerät bietet, müssen Sie möglicherweise einige weitere Schritte ausführen. Wenn Sie aufgefordert werden, installieren Sie die **Datalert** -app finden Sie unter [Registrierung Ihres Geräts im Telecom Expense Management](enroll-your-device-with-telecom-expense-management-ios.md). Wenn Ihre Organisation Teil des Apple Device Enrollment Program ist, informieren Sie sich [wie zum Registrieren Ihres unternehmenseigenen Geräts](enroll-your-device-dep-ios.md).  

## <a name="next-steps"></a>Nächste Schritte  
Apps, mit denen Sie bei der Arbeit oder Schule zu finden. Erfahren Sie, [wie apps zur Verfügung gestellt werden](use-managed-apps-on-your-device-ios.md) Ihnen über die Unternehmensportal-App.  

Benötigen Sie weitere Unterstützung? Kontaktieren Sie die Supportabteilung Ihres Unternehmens. Sie finden entsprechende Kontaktinformationen auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).  
