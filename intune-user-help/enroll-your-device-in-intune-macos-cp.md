---
title: Registrieren Sie Ihren Mac mit InTune-Unternehmensportal | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Ihren Mac mit der Unternehmensportal-app in InTune registrieren.
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: kakyker
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba285fc9de58b3fb739a16722e0e05e36e840e87
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74098155"
---
# <a name="enroll-your-macos-device-using-the-company-portal-app"></a>Registrieren Ihres macOS-Geräts mit der Unternehmensportal-App  

Registrieren Sie Ihr macOS-Gerät bei der Intune-Unternehmensportal-App, um sicheren Zugriff auf E-Mails, Dateien und Apps Ihres Geschäfts-, Schul- oder Unikontos zu erhalten.

Organisationen verlangen in der Regel, dass Sie Ihr Gerät registrieren, bevor Sie auf proprietäre Daten zugreifen können. Sobald Ihr Gerät registriert ist, gilt es als *verwaltet*. Ihre Organisation kann dem Gerät über einen MDM-Anbieter (Mobile Device Management, Verwaltung mobiler Geräte) wie Intune Richtlinien und Anwendungen zuweisen. Sie müssen Ihr Gerät entsprechend der Richtlinieneinstellungen Ihrer Organisation konfigurieren, um über Ihr Gerät kontinuierlich auf Ihre Geschäfts-, Schul- oder Uniressourcen zugreifen zu können.  

In diesem Artikel wird beschrieben, wie Sie Ihr Gerät mit der Unternehmensportal-App für macOS registrieren, konfigurieren und verwalten, um die Anforderungen Ihrer Organisation zu erfüllen.  


## <a name="what-to-expect-from-the-company-portal-app"></a>Vorteile der Unternehmensportal-App

Während des anfänglichen Setups müssen Sie für die Unternehmensportal-APP sich anmelden und sich bei Ihrer Organisation authentifizieren. Unternehmensportal informiert Sie dann über alle Geräteeinstellungen, die Sie konfigurieren müssen, um die Anforderungen Ihrer Organisation zu erfüllen. Beispielsweise legen Organisationen oft Anforderungen an die minimale oder maximale Zeichenanzahl des Kennworts fest, die Sie einhalten müssen.    

Nachdem Sie Ihr Gerät registriert haben, stellen Unternehmensportal immer sicher, dass Ihr Gerät gemäß den Anforderungen Ihres Unternehmens geschützt ist. Wenn Sie z. b. eine APP von einer nicht vertrauenswürdigen Quelle installieren, werden Sie von Unternehmensportal benachrichtigt und möglicherweise der Zugriff auf die Ressourcen Ihrer Organisation eingeschränkt. App-Schutzrichtlinien wie diese werden häufig durchgängig gemacht. Um wieder Zugriff zu erhalten, müssen Sie wahrscheinlich die nicht vertrauenswürdige APP deinstallieren. 

Wenn Ihre Organisation nach der Registrierung eine neue Sicherheitsanforderung durchsetzt, z. B. die mehrstufige Authentifizierung, erhalten Sie eine Benachrichtigung vom Unternehmensportal. Sie haben dann die Möglichkeit, Ihre Einstellungen so zu ändern, dass Sie von Ihrem Gerät aus weiterarbeiten können.  

Weitere Informationen zur Registrierung finden Sie unter [Was geschieht, wenn ich die Unternehmensportal-App installiere und mein Gerät registriere?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md).  

## <a name="get-your-macos-device-managed"></a>Verwalten Ihres macOS-Geräts  
Führen Sie die folgenden Schritte aus, um Ihr macOS-Gerät bei Ihrer Organisation zu registrieren. Auf Ihrem Gerät muss macOS 10,12 oder höher ausgeführt werden.   

> [!NOTE]
> Während dieses Vorgangs werden Sie möglicherweise aufgefordert, Unternehmensportal vertrauliche Informationen zu verwenden, die in ihrer Keychain gespeichert sind. Diese Eingabe Aufforderungen sind Teil der Apple-Sicherheit. Wenn Sie die Eingabeaufforderung erhalten, geben Sie Ihr Kennwort für die Schlüsselbund Anmeldung ein, und wählen Sie **immer zulassen**. Wenn Sie die **Eingabe** Taste drücken oder auf der Tastatur **zurückkehren** , wird die Eingabeaufforderung stattdessen " **zulassen**" ausgewählt. Dies kann zu zusätzlichen Eingabe Aufforderungen führen.  

### <a name="install-company-portal-app"></a>Installieren der Unternehmensportal-App  
1. Wechseln Sie zu " [mein Mac registrieren](https://go.microsoft.com/fwlink/?linkid=853070)".  
2. Der Unternehmensportal Installer. pkg-Datei wird heruntergeladen. Öffnen Sie das Installationsprogramm, und führen Sie die Schritte aus. 
3. Stimmen Sie den Softwarelizenzbedingungen zu. 
4. Geben Sie Ihr Geräte Kennwort oder den registrierten Fingerabdruck zum Installieren der Software ein.  
5. Öffnen Sie Unternehmensportal. 

> [!IMPORTANT]
> Microsoft AutoUpdate kann zum Aktualisieren Ihrer Microsoft-Software geöffnet werden. Nachdem alle Updates installiert wurden, öffnen Sie die Unternehmensportal-app. Zur optimalen Einrichtung installieren Sie die neuesten Versionen von Microsoft AutoUpdate und Unternehmensportal.  


### <a name="enroll-your-mac"></a>Registrieren Ihres Mac  


1. Melden Sie sich mit Ihrem Geschäfts-, Schul- oder Unikonto beim Unternehmensportal an.  
2. Wenn die APP geöffnet wird, wählen Sie **starten**aus.  
3. Überprüfen Sie, was Ihre Organisation auf Ihrem registrierten Gerät [sehen kann und was nicht](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md) . Wählen Sie dann **Weiter** aus.  
4. Wählen Sie auf dem Bildschirm **Verwaltungs Profil installieren** die Option **Profil herunterladen**aus.   

    ![Beispiel eines Screenshots der Unternehmensportal, Seite "Verwaltungs Profil installieren", Hervorhebung der Schaltfläche "Profil herunterladen".](./media/install-mgmt-profile-mac-1911.PNG)   
5. Die Systemeinstellungen Ihres Geräts werden geöffnet. Wählen Sie **Installieren** aus, und wählen Sie dann erneut **Installieren** . Wenn Sie dazu aufgefordert werden, geben Sie Ihr Geräte Kennwort ein.  

    ![Beispiel eines Screenshots der macOS-Systemeinstellungen, Installations Aufforderung, Hervorhebung der Schaltfläche "installieren".](./media/system-preference-install-1911.PNG)  
6. Nachdem das Profil installiert wurde, wird es in der Liste Profile unter **Verwaltungs Profil angezeigt.**  

   ![Beispiel eines Screenshots von macOS-Systemeinstellungen, profilbildschirm, Hervorhebung des installierten Verwaltungs Profils.](./media/system-preference-verify-1911.PNG)   
7. Kehren Sie zu Unternehmensportal zurück.   
8. In Ihrer Organisation ist es möglicherweise erforderlich, dass Sie Ihre Geräteeinstellungen aktualisieren. Wenn Sie mit dem Aktualisieren der Einstellungen fertig sind, wählen Sie **Einstellungen überprüfen**.  

    ![Beispiel eines Screenshots von Unternehmensportal, Bildschirm "Geräteeinstellungen aktualisieren", markieren der Schaltfläche "Einstellungen überprüfen".](./media/update-settings-mac-1911.PNG)  
9. Wenn Setup abgeschlossen ist, wählen Sie **Fertig**aus.  


 ## <a name="troubleshooting-and-feedback"></a>Problembehandlung und Feedback   

Wenn bei der Registrierung Probleme auftreten, gehen Sie zu **Hilfe** > **Diagnosebericht senden** , um das Problem an Microsoft-App-Entwickler zu melden. Diese Informationen werden verwendet, um die APP zu verbessern. Diese Informationen werden auch verwendet, um das Problem zu beheben, wenn Ihre IT-Supportmitarbeiter Ihnen helfen, Hilfe zu erhalten.  

Nachdem Sie das Problem an Microsoft gemeldet haben, können Sie die Details Ihrer Benutzer Arbeit an Ihren IT-Supportmitarbeiter senden. Wählen Sie **Email Details**aus. Geben Sie ein, was Sie im Text der e-Mail haben. Um die e-Mail-Adresse Ihrer Support Person zu ermitteln, wechseln Sie zum Unternehmensportal APP **->.** Oder überprüfen Sie die [Unternehmensportal Website](https://go.microsoft.com/fwlink/?linkid=2010980).  
 

Außerdem würde das Microsoft InTune Unternehmensportal Team gern Ihr Feedback hören. Wechseln Sie zu " **Hilfe** > **Feedback senden** , um Ihre Gedanken und Ideen zu teilen.  

## <a name="unverified-profiles"></a>Nicht überprüfte Profile  
Wenn Sie die installierten MDM-Profile (mobile Geräteverwaltung) unter **Systemeinstellungen** > **Profile** anzeigen, wird für einige Profile möglicherweise der Status „Nicht überprüft“ angezeigt. Solange das Verwaltungsprofil den Status „Geprüft“ aufweist, müssen Sie sich keine Sorgen machen.  

Das Verwaltungsprofil definiert die MDM-Kanalverbindung. Solange das Verwaltungsprofil geprüft ist, erben alle anderen Profile, die über diesen Kanal auf dem Computer bereitgestellt werden, die Sicherheitseigenschaften des Verwaltungsprofils.  

## <a name="updating-the-company-portal-app"></a>Aktualisieren der Unternehmensportal-App

Das Aktualisieren des Unternehmensportals erfolgt auf die gleiche Weise wie bei jeder anderen Office-App, nämlich über Microsoft AutoUpdate für macOS. Weitere Informationen finden Sie im Artikel zum [Aktualisieren von Microsoft-Apps für macOS](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1).  

## <a name="next-steps"></a>Nächste Schritte  
Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).  


