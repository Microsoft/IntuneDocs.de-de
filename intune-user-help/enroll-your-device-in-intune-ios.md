---
title: Einrichten des iOS-Gerätezugriffs auf Unternehmensressourcen | Microsoft-Dokumentation
description: Beschreibt die Aktivierung der Verwaltung Ihrer iOS-Geräte über Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: bd9fd38fdc244bc48333496c2f266ff039e55585
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75855562"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Einrichten des iOS-Gerätezugriffs auf Unternehmensressourcen  

Registrieren Sie Ihr iOS-Gerät bei der Intune-Unternehmensportal-App, um sicheren Zugriff auf E-Mails, Dateien und Apps Ihrer Organisation zu erhalten.

Sobald Ihr Gerät registriert ist, gilt es als *verwaltet*. Ihre Organisation kann dem Gerät über einen MDM-Anbieter (Mobile Device Management, Verwaltung mobiler Geräte) wie Intune Richtlinien und Anwendungen zuweisen.  

> [!NOTE]
> Die von unserem Dienst gesammelten Daten werden keinesfalls an Dritte verkauft.  

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

2. Wenn Sie gefragt werden, ob Sie Benachrichtigungen vom Unternehmensportal empfangen möchten, tippen Sie auf **Zulassen.** Das Unternehmensportal informiert Sie anhand von Benachrichtigungen, wenn z.B. Ihre Geräteeinstellungen aktualisiert werden müssen.  

3. Klicken Sie auf dem Bildschirm **Zugriff einrichten** auf **Anfang**.   

    ![Beispielscreenshot des Bildschirms „Zugriff einrichten“ im Unternehmensportal.](./media/ios-enrollment-checklist-1909.PNG)  

4. Der Bildschirm **Gerät und Anmeldetyp auswählen** wird angezeigt, und Sie werden zur Eingabe Ihres Gerätetyps aufgefordert.  
    * Tippen **(Organisation) besitzt dieses Gerät** , wenn Sie Ihr Gerät aus Ihrer Organisation erhalten haben. Fahren Sie anschließend mit dem voll [ständigen Gerät](###secure-entire-device) in diesem Artikel fort, um das Setup abzuschließen.  
    * Tippen Sie auf **Ich besitze dieses Gerät** , wenn Sie ein persönliches Gerät verwenden, das Sie von Zuhause gebracht haben. Fahren Sie anschließend mit dem nächsten Schritt fort.  

    Wenn dieser Bildschirm nicht angezeigt wird, fahren Sie mit dem [sicheren vollständigen Gerät](enroll-your-device-in-intune-ios.md#secure-entire-device) fort, um das Setup abzuschließen.  
    
    ![Beispiel eines Screenshots der Unternehmensportal, dem Bildschirm "Geräte-und Registrierungstyp auswählen", Gerätetyp Optionen.](./media/ios-device-type-1909.PNG)  


5. Wählen Sie aus, wie die Daten auf Ihrem Gerät geschützt werden sollen, nachdem Sie registriert wurden.  
    * Tippen Sie auf **sicheres gesamtes Gerät** , um alle apps und Daten auf dem Gerät zu sichern. Wechseln Sie dann zu [Secure all Device](enroll-your-device-in-intune-ios.md#secure-entire-device) , um das Setup abzuschließen.
    * Tippen Sie auf **sichere arbeitsbezogene apps und Daten** , um nur die apps und Daten zu sichern, auf die Sie mit Ihrem Geschäftskonto zugreifen. Wechseln Sie dann zu [sichere arbeitsbezogene apps und Daten](enroll-your-device-in-intune-ios.md#secure-work-related-apps-and-data).  

    ![Beispiel eines Screenshots der Unternehmensportal, dem Bildschirm "Geräte-und Registrierungstyp auswählen", Optionen für den Anmeldetyp.](./media/ios-enrollment-type-1909.PNG)  


### <a name="secure-entire-device"></a>Sicheres gesamtes Gerät  

1. Lesen Sie auf dem Bildschirm " **Geräteverwaltung und Datenschutz** " die Liste der Geräteinformationen, die Ihre Organisation sehen und nicht sehen kann. Tippen Sie dann auf **Weiter**.  


 > [!IMPORTANT]
> Diese nächsten Schritte und Bildschirme sind je nach iOS-Version unterschiedlich. Führen Sie die Schritte für Ihre iOS-Version aus. 

2. Safari öffnet die Unternehmensportal-Website auf Ihrem Gerät. Wenn Sie aufgefordert werden, das Konfigurationsprofil herunterzuladen, tippen Sie auf **Zulassen**. Falls Sie ein Gerät haben mit:  
    * iOS 12.2 und höher: Wenn der Download abgeschlossen ist, tippen Sie auf **Schließen**. Fahren Sie dann mit Schritt 3 fort.  
    * IOS 12,1 und früher: nach Abschluss des Downloads werden Sie automatisch an die app "Einstellungen" umgeleitet. Fahren Sie mit Schritt 4 fort.  
 
    Wenn Sie versehentlich auf **Ignorieren** tippen sollten, aktualisieren Sie die Seite. Sie werden aufgefordert, die Unternehmensportal-App zu öffnen. Wenn Sie dort sind, tippen Sie **erneut auf herunterladen**.

  > [!NOTE]
  > Sie müssen das Verwaltungsprofil, wie in den nächsten Schritten beschrieben, innerhalb von 8 Minuten nach dem Herunterladen installieren. Wenn dies nicht geschieht, wird das Profil entfernt, woraufhin Sie die Registrierung erneut starten müssen.  

3. Wenn Sie aufgefordert werden, Unternehmensportal zu öffnen, tippen Sie auf **Öffnen**. Lesen Sie die Informationen auf dem Bildschirm **Installieren des Verwaltungs Profils** .  

4. Wechseln Sie zur App "Einstellungen", und tippen Sie auf **Anmelden in < Organisationsnamen >** oder auf **heruntergeladene profile**.  

    ![Beispiel eines Screenshots der App "Einstellungen", registrieren bei der Organisation.](./media/enroll-in-organization-ios-1909.PNG)  

   Wenn keine der Optionen angezeigt wird, wechseln Sie zu **Allgemein** > **Profile & Geräteverwaltung**> **Verwaltungs Profil**. Wenn weiterhin kein Verwaltungsprofil angezeigt wird, müssen Sie es möglicherweise erneut herunterladen.  

5. Tippen Sie auf **Installieren**.  
    
6. Geben Sie das Gerätekennwort ein. Tippen Sie dann auf **Installieren**.    

7. Der nächste Bildschirm ist eine standardmäßige Systemwarnung zur Geräteverwaltung. Um mit der Installation fortzufahren, tippen Sie auf **Installieren**. Wenn Sie aufgefordert werden, der Remoteverwaltung zu vertrauen, tippen Sie auf **Vertrauen**.  

8. Klicken Sie nach Abschluss der Installation auf **Fertig**. Um zu bestätigen, dass das Profil installiert wurde, wechseln Sie zu den Einstellungen unter **Profile und Geräteverwaltung**. Daraufhin sollte das Profile unter **Verwaltung mobiler Geräte** aufgeführt sein.   

    ![Beispielscreenshot der App „Einstellungen“ mit den Einstellungen unter „Profile und Geräteverwaltung“ mit gezeigtem Verwaltungsprofil.](./media/ios-12-cp-enroll-1904.PNG)  

9. Kehren Sie zur Unternehmensportal-App zurück. Das Unternehmensportal beginnt mit der Synchronisierung und Einrichtung Ihres Geräts. Das Unternehmensportal fordert Sie möglicherweise auf, zusätzliche Geräteeinstellungen zu aktualisieren. Wenn das der Fall ist, tippen Sie auf **Weiter**.  

10. Sie erkennen, dass das Setup abgeschlossen ist, wenn alle Elemente in der Liste ein grünes Häkchen aufweisen. Tippen Sie auf **Fertig**.   

> [!Note]
> Wenn in Ihrer Organisation Obergrenzen für Gesprächsminuten oder Datenvolumen gelten oder sie Ihnen ein unternehmenseigenes Gerät zur Verfügung stellt, müssen Sie möglicherweise noch einige weitere Schritte durchführen. Wenn Sie aufgefordert werden, die App **Datalert** zu installieren, lesen Sie [Registrieren Ihres Geräts im Telecom Expense Management](enroll-your-device-with-telecom-expense-management-ios.md). Wenn Ihr Unternehmen am Apple-Programm zur Geräteregistrierung teilnimmt, finden Sie heraus, [wie Sie Ihr unternehmenseigenes Gerät registrieren können](enroll-your-device-dep-ios.md).  

### <a name="secure-work-related-apps-and-data"></a>Sichern von arbeitsbezogenen apps und Daten  
1. Der Bildschirm **Microsoft Authenticator herunterladen** wird angezeigt (wenn Sie bereits über Authentifikator verfügen, wird dieser Bildschirm nicht angezeigt, und fahren Sie dann mit Schritt 2 fort).  
    1. Tippen **Sie im App Store auf herunterladen**.
    2. Wenn der App Store geöffnet wird, installieren Sie die app. 
    3. Kehren Sie zu Unternehmensportal zurück, und tippen Sie auf **weiter**.    
    
   Nachdem Sie Microsoft Authenticator installiert haben, müssen Sie nichts mehr mit der app ausführen. Es muss nur auf Ihrem Gerät vorhanden sein. 

   ![Beispiel eines Screenshots der Unternehmensportal "Microsoft Authenticator" herunterladen.](./media/download-ms-authenticator-1909.PNG)  

2. Lesen Sie auf dem Bildschirm " **Geräteverwaltung und Datenschutz** " die Liste der Geräteinformationen, die Ihre Organisation sehen und nicht sehen kann. Tippen Sie dann auf **Weiter**.  


 > [!IMPORTANT]
> Diese nächsten Schritte und Bildschirme sind je nach iOS-Version unterschiedlich. Führen Sie die Schritte für Ihre iOS-Version aus. 

3. Safari öffnet die Unternehmensportal-Website auf Ihrem Gerät. Wenn Sie aufgefordert werden, das Konfigurationsprofil herunterzuladen, tippen Sie auf **Zulassen**. Falls Sie ein Gerät haben mit:  
    * iOS 12.2 und höher: Wenn der Download abgeschlossen ist, tippen Sie auf **Schließen**. Fahren Sie dann mit Schritt 4 fort.  
    * IOS 12,1 und früher: nach Abschluss des Downloads werden Sie automatisch an die app "Einstellungen" umgeleitet. Fahren Sie mit Schritt 5 fort.  
 
    Wenn Sie versehentlich auf **Ignorieren** tippen sollten, aktualisieren Sie die Seite. Sie werden aufgefordert, die Unternehmensportal-App zu öffnen. In der App können Sie auf **Erneut herunterladen** tippen.

  > [!NOTE]
  > Sie müssen das Verwaltungsprofil, wie in den nächsten Schritten beschrieben, innerhalb von 8 Minuten nach dem Herunterladen installieren. Wenn dies nicht geschieht, wird das Profil entfernt, woraufhin Sie die Registrierung erneut starten müssen.  

4. Wenn Sie aufgefordert werden, Unternehmensportal zu öffnen, tippen Sie auf **Öffnen**. Lesen Sie die Informationen auf dem Bildschirm **Installieren des Verwaltungs Profils** . 

5. Wechseln Sie zur App "Einstellungen", und tippen Sie auf **Anmelden in < Organisationsnamen >** oder auf **heruntergeladene profile**.  

    ![Beispiel eines Screenshots der App "Einstellungen", registrieren bei der Organisation.](./media/enroll-in-organization-ios-1909.PNG)  

   Wenn keine der Optionen angezeigt wird, wechseln Sie zu **Allgemein** > **Profile & Geräteverwaltung**> **Verwaltungs Profil**. Wenn weiterhin kein Verwaltungsprofil angezeigt wird, müssen Sie es möglicherweise erneut herunterladen.   


6. Tippen Sie auf dem Bildschirm **Benutzer** Registrierung auf **mein iPhone registrieren**.  

    ![Beispiel: Screenshot der App "Einstellungen", Benutzer Registrierungs Bildschirm, Hervorhebung der Schaltfläche "registrieren".](./media/user-enrollment-information-1909.PNG)  

7. Geben Sie das Geräte Kennwort ein. Tippen Sie dann auf **Installieren**.  

8. Geben Sie auf dem Bildschirm **Anmelden** das Kennwort für Ihre verwaltete Apple-ID ein. In den meisten Fällen sind diese Anmelde Informationen dieselben, die Sie zum Anmelden bei Ihrem Geschäfts-, Schul-oder unikonto verwenden, es sei denn, Ihre Organisation hat Ihnen einen anderen Satz von Anmelde Informationen bereitgestellt. 
9. Tippen Sie **auf Anmelden**.  
10. Eine Erfolgsmeldung wird nach der Installation des Profils kurz auf dem Bildschirm angezeigt. Um zu überprüfen, ob das Profil installiert ist, wechseln Sie zu den **Profilen & Geräteverwaltung** Einstellungen. Daraufhin sollte das Profil unter  **Verwaltung mobiler Geräte** aufgeführt sein.  

    ![Beispielscreenshot der App „Einstellungen“ mit den Einstellungen unter „Profile und Geräteverwaltung“ mit gezeigtem Verwaltungsprofil.](./media/ios-12-cp-enroll-1904.PNG)  

11. Kehren Sie zur Unternehmensportal-App zurück. Das Unternehmensportal beginnt mit der Synchronisierung und Einrichtung Ihres Geräts. Das Unternehmensportal fordert Sie möglicherweise auf, zusätzliche Geräteeinstellungen zu aktualisieren. Wenn das der Fall ist, tippen Sie auf **Weiter**.    

12. Sie erkennen, dass das Setup abgeschlossen ist, wenn alle Elemente in der Liste ein grünes Häkchen aufweisen. Tippen Sie auf **done**.  

## <a name="it-administrator-support"></a>Unterstützung für IT-Administratoren  
Wenn Sie IT-Administrator sind und Probleme bei der Registrierung von Geräten haben, lesen Sie [Behandeln von Problemen bei der Registrierung von iOS-Geräten in Microsoft Intune](https://support.microsoft.com/en-us/help/4039809). Dieser Artikel listet häufige Fehler, ihre Ursachen und Schritte zur Behebung auf.  

## <a name="next-steps"></a>Nächste Schritte  
Finden Sie Apps, die Ihnen bei der Arbeit oder in der Schule oder Hochschule helfen. Erfahren Sie, wie über das Unternehmensportal [Apps zur Verfügung gestellt werden](use-managed-apps-on-your-device-ios.md).  

Benötigen Sie weitere Unterstützung? Kontaktieren Sie die Supportabteilung Ihres Unternehmens. Sie finden entsprechende Kontaktinformationen auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).  
