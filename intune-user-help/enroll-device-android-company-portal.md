---
title: Registrieren eines Android-Geräts im Intune-Unternehmensportal | Microsoft-Dokumentation
description: Beschreibt, wie Sie ein Android-Gerät im Intune-Unternehmensportal registrieren
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: e0a2297509d6077d6508adaab96ae6eb3cf9b28f
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856733"
---
# <a name="enroll-your-device-with-company-portal"></a>Registrieren Ihres Geräts im Unternehmensportal  
Registrieren Sie Ihr privates oder unternehmenseigenes Android-Gerät, um sicheren Zugriff auf Unternehmens-E-Mails, -Apps und -Daten zu erhalten. Das Unternehmensportal unterstützt Android-Geräte, einschließlich Samsung Knox, mit Android 4.4 und höher.  
</br>
> [!VIDEO https://www.youtube.com/embed/k0Q_sGLSx6o?rel=0]

> [!NOTE]
> Samsung Knox ist ein Sicherheitssystem, mit dem bestimmte Geräte von Samsung neben den nativen Android-Sicherheitsfeatures zusätzlichen Schutz bieten. Navigieren Sie zu **Einstellungen** > **System > Über das Telefon**, um zu überprüfen, ob es sich bei Ihrem Gerät um ein Samsung Knox-Gerät handelt. Wird dort keine **Knox-Version** angezeigt, verfügen Sie über ein natives Android-Gerät.

## <a name="enroll-device"></a>Registrieren eines Geräts  
[Installieren Sie die kostenlose Intune-Unternehmensportal-App über Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). 

Während der Registrierung werden Sie möglicherweise aufgefordert, eine Kategorie auszuwählen, die am besten beschreibt, wie Sie Ihr Gerät nutzen. Der Support Ihres Unternehmens verwendet Ihre Antwort, um die Apps zu überprüfen, auf die Sie Zugriff haben.  

1. Öffnen Sie die Unternehmensportal-App, und melden Sie sich mit Ihrem Geschäfts-, Schul- oder Unikonto an.  

2. Wenn Sie dazu aufgefordert werden, die Geschäftsbedingungen Ihrer Organisation zu akzeptieren, tippen Sie auf **ALLE AKZEPTIEREN**.  

   ![Beispiel Bild des Bildschirms für die Unternehmensportal, Begriffe und Hervorhebung der Schaltfläche "alle akzeptieren".](./media/accept-terms-1911.png)  


3. Überprüfen Sie, was Ihre Organisation sehen kann und was nicht. Tippen Sie dann auf **WEITER**.


    ![Beispiel Bild Unternehmensportal, wir kümmern uns um den Datenschutz Bildschirm, der die Schaltfläche "weiter" hervorhebt.](./media/android-privacy-screen-1911.png)  
4. Überprüfen Sie, was in den anstehenden Schritten zu erwarten ist. Tippen Sie dann auf **weiter**.  

    ![Beispiel Bild Unternehmensportal, der nächste Bildschirm, Hervorhebung der Schaltfläche Weiter.](./media/android-whats-next-1911.png)  


5. Abhängig von Ihrer Android-Version werden Sie möglicherweise aufgefordert, den Zugriff auf bestimmte Teile des Geräts zuzulassen. Diese Eingabe Aufforderungen sind für Google erforderlich und werden nicht von Microsoft gesteuert.  

    Tippen Sie auf **zulassen** für die folgenden Berechtigungen:  
    * **Zulassen und Verwalten von Telefon anrufen durch Unternehmensportal**: diese Berechtigung ermöglicht dem Gerät, seine IMEI-Nummer (International Mobile Station Equipment Identity) mit InTune, dem Geräte Verwaltungs Anbieter Ihres Unternehmens, gemeinsam zu nutzen. Es ist sicher, diese Berechtigung zuzulassen. Microsoft wird niemals Telefonanrufe tätigen oder verwalten.  
    * **Zugriff auf Ihre Kontakte durch Unternehmensportal zulassen**: mit dieser Berechtigung kann die Unternehmensportal-App Ihr Geschäftskonto erstellen, verwenden und verwalten.  Es ist sicher, diese Berechtigung zuzulassen. Microsoft greift nie auf Ihre Kontakte zu. 

    Wenn Sie die Berechtigung verweigern, werden Sie erneut aufgefordert, wenn Sie sich das nächste Mal bei Unternehmensportal anmelden. Wenn Sie dies nicht wünschen, wählen Sie **Never ask again** (Nicht noch mal fragen) aus. Um App-Berechtigungen zu verwalten, wechseln Sie zu Einstellungen app > **apps** > **Unternehmensportal** > **Berechtigungen** > **Phone**.  

6. Aktivieren Sie die Geräte Administrator-app. 

    Unternehmensportal benötigt Geräte Administrator Berechtigungen zur sicheren Verwaltung Ihres Geräts. Wenn Sie die APP aktivieren, kann Ihre Organisation mögliche Sicherheitsprobleme erkennen, z. b. wiederholte fehlgeschlagene Versuche, das Gerät zu entsperren, und entsprechend reagieren.  

    ![Beispiel Bild des Bildschirms "Geräte Administrator aktivieren", Hervorhebung der Schaltfläche "aktivieren".](./media/activate-device-administrator-1911.png)  

> [!NOTE]
> Microsoft steuert das Messaging auf diesem Bildschirm nicht. Wir wissen, dass der Ausdruck etwas drastisch erscheinen kann. Unternehmensportal können nicht angeben, welche Einschränkungen und der Zugriff für Ihre Organisation relevant sind. Wenn Sie Fragen haben, wie Ihre Organisation die APP verwendet, wenden Sie sich an Ihren IT-Support. Besuchen Sie die [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980), um die Kontaktinformationen für Ihre Organisation zu erhalten.  


7. Ihr Gerät beginnt mit der Einschreibung. Wenn Sie ein Samsung Knox-Gerät verwenden, werden Sie aufgefordert, die Datenschutzrichtlinie für den Elm-Agent zuerst zu überprüfen und zu bestätigen.   

    ![Beispiel Bild des Bildschirms für die Samsung Knox-Datenschutzrichtlinie, der während der Registrierung angezeigt wird.](./media/and-enroll-7-knox-privacy-policy.png)  

8. Überprüfen Sie auf dem Bildschirm **Unternehmens Zugriff einrichten** , ob Ihr Gerät registriert ist. Tippen Sie dann auf **WEITER**.  

    ![Beispiel Abbildung von Unternehmensportal, Bildschirm zum Einrichten des Unternehmens Zugriffs, das anzeigt, dass das Gerät verwaltet wird.](./media/update-settings-1911.png)  

9. In Ihrer Organisation ist es möglicherweise erforderlich, dass Sie Ihre Geräteeinstellungen aktualisieren. Tippen Sie auf **Auflösen** , um eine Einstellung anzupassen. Wenn Sie mit dem Aktualisieren der Einstellungen fertig sind, tippen Sie auf **weiter**.  

   ![Beispiel Abbildung Unternehmensportal, Aktualisieren von Geräteeinstellungen und hervorheben der Schaltflächen auflösen und fortfahren.](./media/resolve-settings-1911.png)  

10. Wenn das Setup abgeschlossen ist, tippen Sie auf **Fertig**.    

    ![Beispiel Abbildung Unternehmensportal, Bildschirm "Unternehmens Zugriff einrichten", zeigt die abgeschlossene Schaltfläche "Setup" und "Fertig".](./media/android-enrollment-done-1911.png) 

## <a name="next-steps"></a>Nächste Schritte  

Bevor Sie versuchen, eine Schul-oder Arbeits-APP zu installieren, wechseln Sie zu **Einstellungen** > **Sicherheit**, und aktivieren Sie **unbekannte Quellen**. Wenn Sie diese Option nicht aktivieren, wird die folgende Meldung angezeigt, wenn Sie versuchen, eine App zu installieren: "Installation blockiert. Aus Sicherheitsgründen ist Ihr Gerät so eingestellt, dass die Installation von Apps aus unbekannten Quellen blockiert wird.“ Sie können in der Nachricht auf **Einstellungen** tippen, um direkt zu **unbekannten Quellen**zu wechseln.  

> [!Note]
> Wenn Ihre Organisation Telecom Expense Management-Software verwendet, müssen Sie ein paar zusätzliche Schritte ausführen, bevor das Gerät vollständig registriert ist. [Hier](enroll-your-device-with-telecom-expense-management-android.md) erfahren Sie mehr.

Sollte beim Versuch der Registrierung Ihres Geräts bei Intune ein Fehler auftreten, können Sie [Registrierungsfehler an den Support Ihres Unternehmens senden](send-logs-to-your-it-admin-by-email-android.md).  

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).  