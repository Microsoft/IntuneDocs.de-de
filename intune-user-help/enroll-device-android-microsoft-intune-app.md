---
title: Registrieren von Unternehmensgeräten in der Microsoft Intune-App | Microsoft-Dokumentation
description: In diesem Artikel wird beschrieben, wie Sie ein unternehmenseigenes Android-Gerät bei Intune registrieren.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/07/2019
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
ms.collection: M365-identity-device-management
ms.openlocfilehash: 81c842eb27b1b9131c164ced5aeed86a78a37353
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506292"
---
# <a name="enroll-your-corporate-device-with-the-microsoft-intune-app"></a>Registrieren Ihres Unternehmensgeräts in der Microsoft Intune-App

Registrieren Sie Ihr unternehmenseigenes Android-Gerät, um sicheren Zugriff auf Unternehmens-E-Mails, -Apps und andere -Daten zu erhalten. Die Microsoft Intune-App unterstützt unternehmenseigene Geräte, auf denen Android 6.0 oder höher ausgeführt wird. Sie wird bei der Registrierung auf neuen und auf Werkseinstellungen zurückgesetzten Geräten automatisch installiert. 

Es gibt vier Registrierungsmethoden. Ihr Unternehmen sollte Sie informieren, welche Option verwendet werden soll.
 
* NFC (Near Field Communication)  
* Token  
* QR-Code   
* Google Zero Touch  

## <a name="enroll-device"></a>Registrieren eines Geräts 
Führen Sie die folgenden Schritte durch, um Ihr Gerät einzurichten und zu registrieren.  

> [!NOTE]
> Die Android-Version oder der Gerätehersteller kann weitere Schritte von Ihnen erfordern, die in dieser Vorgehensweise nicht behandelt werden. Die Darstellung von Farben und Text auf den hier gezeigten Screenshots kann von der Anzeige auf Ihrem Gerät abweichen.  

1. Schalten Sie Ihr neues oder auf Werkseinstellungen zurückgesetztes Gerät ein.  
2. Wählen Sie auf dem **Willkommenssbildschirm** Ihre Sprache aus.   Wenn Sie angewiesen wurden, sich mit einem QR-Code oder per NFC zu registrieren, führen Sie die für diese Methoden unten beschriebenen Schritte aus.  
     * NFC: Halten Sie Ihr Gerät mit NFC-Unterstützung an das hierzu vorgesehene Gerät, um eine Verbindung mit dem Netzwerk Ihres Unternehmens herzustellen. Führen Sie die angezeigten Schritte aus. Fahren Sie mit Schritt 5 dieser Anleitung fort, wenn Sie die Nutzungsbedingungen von Google Chrome erreichen.  

     * QR-Code: Führen Sie die unter [Registrierung per QR-Code](#qr-code-enrollment) beschriebenen Schritte aus.  

     Wenn Sie angewiesen wurden, eine andere Methode zu verwenden, fahren Sie mit Schritt 3 fort.    

3. Stellen Sie eine Verbindung mit dem WLAN-Netzwerk her, und tippen Sie dann auf **NEXT** (WEITER). Führen Sie den Schritt aus, der Ihrer Registrierungsmethode entspricht. 

    * Token: Wenn Sie zum Google-Anmeldebildschirm erreichen, führen Sie die Schritte unter [Registrierung per Token](#token-enrollment) aus.  
    * Google Zero Touch: Sobald Sie mit dem WLAN-Netzwerk verbunden sind, wird Ihr Gerät vom Unternehmen erkannt. Fahren Sie mit Schritt 4 fort, und führen Sie die auf dem Bildschirm angezeigten Anweisungen aus, bis das Setup abgeschlossen ist.    
 
       ![Beispielbild der Anzeige der Google-Nutzungsbedingungen, die bei der Verwendung von Google Zero Touch angezeigt werden, mit hervorgehobener Schaltfläche „Accept & Continue“ (Zustimmen & Weiter).](./media/google-zero-touch-intune-app-01.png)   
   
4. Prüfen Sie die Nutzungsbedingungen von Google. Tippen Sie anschließend auf **ACCEPT & CONTINUE** (ZUSTIMMEN & WEITER).  

      ![Beispielbild der Google-Nutzungsbedingungen mit hervorgehobener Schaltfläche „Accept & Continue“ (Akzeptieren & Weiter)](./media/fully-managed-intune-app-04.png)   

6. Prüfen Sie die Nutzungsbedingungen von Google Chrome. Tippen Sie anschließend auf **ACCEPT & CONTINUE** (ZUSTIMMEN & WEITER).  

   ![Beispielbild der Google Chrome-Nutzungsbedingungen mit hervorgehobener Schaltfläche „Accept & Continue“ (Akzeptieren & Weiter)](./media/fully-managed-intune-app-06.png)   

7. Melden Sie sich auf dem Anmeldebildschirm mit Ihrem Geschäfts-, Schul- oder Unikonto an.   

    ein. Geben Sie Ihre E-Mail-Adresse ein, und tippen Sie dann auf **Weiter**.      
    b. Geben Sie Ihr Kennwort ein, und tippen Sie dann auf **Anmelden**.  

8. Je nach Anforderungen Ihres Unternehmens werden Sie möglicherweise dazu aufgefordert, Ihre Einstellungen zu aktualisieren (z. B. die Bildschirmsperre oder Verschlüsselung). Wenn Ihnen diese Aufforderungen angezeigt werden, tippen Sie auf **SET** (ANPASSEN), und befolgen Sie die angezeigten Anweisungen.  

   ![Beispielbild der Einrichtung Ihres Arbeitssmartphones mit hervorgehobener Schaltfläche „Set“ (Anpassen)](./media/fully-managed-intune-app-10.png)   

9. Tippen Sie auf **INSTALL** (Installieren), um die Geschäfts-Apps zu installieren. Klicken Sie nach Abschluss der Installation auf **NEXT** (WEITER).  

   ![Beispielbild der Einrichtung Ihres Arbeitssmartphones mit hervorgehobener Schaltfläche „Install“ (Installieren)](./media/fully-managed-intune-app-11.png)   

10. Tippen Sie auf **starten** , um die APP Microsoft InTune zu öffnen und Ihr Gerät zu registrieren. 

    ![Beispielbild der Einrichtung Ihres Arbeitssmartphones mit hervorgehobener Schaltfläche „Start“](./media/fully-managed-intune-app-17.png)   

11. Tippen Sie auf **Anmelden** und dann auf **weiter** , um die Registrierung zu starten. Wenn die Meldung angezeigt wird, dass die Registrierung abgeschlossen ist, tippen Sie auf **Fertig**.  

    ![Beispiel Bild für das Einrichten des Zugriffs, das Registrieren Ihres Geräts, das Markieren der Schaltfläche "durch Klicken".](./media/fully-managed-intune-app-19.png)   

10. Wenn die Nachricht angezeigt wird, die angibt, dass Ihr Gerät einsatzbereit ist, tippen Sie auf **DONE** (FERTIG).  

    ![Beispielbild der Einrichtung Ihres Arbeitssmartphones mit hervorgehobener Schaltfläche „Done“ (Fertig)](./media/fully-managed-intune-app-18.png)   

Wenn Sie Probleme beim Zugriff auf die Ressourcen Ihrer Organisation haben, müssen Sie möglicherweise zusätzliche Einstellungen auf Ihrem Gerät aktualisieren. Melden Sie sich bei der Microsoft InTune-APP an, um nach erforderlichen Updates zu suchen.   


## <a name="qr-code-enrollment"></a>Registrierung per QR-Code  
In diesem Abschnitt scannen Sie den von Ihrem Unternehmen bereitgestellten QR-Code.  Wenn Sie fertig sind, werden Sie an die Schritte für die Geräteregistrierung weitergeleitet.     
  
1. Tippen Sie auf dem **Willkommensbildschirm** fünfmal auf den Bildschirm, um das Setup per QR-Code zu starten.  

   ![Beispielbild des Willkommensbildschirms der Geräteeinrichtung mit hervorgehobener Anweisung, auf den Bildschirm zu tippen](./media/qr-code-intune-app-01.png)  

2. Führen Sie die angezeigten Anweisungen aus, um eine Verbindung mit dem WLAN-Netzwerk herzustellen.  
3. Wenn Ihr Gerät über keinen QR-Scanner verfügt, wird der Fortschritt der Installation eines QR-Scanners angezeigt. Warten Sie auf den Abschluss der Installation.  
4. Scannen Sie den QR-Code des Bereitstellungsprofils Ihres Unternehmens, wenn Sie dazu aufgefordert werden.  
5. Kehren Sie zu Schritt 4 des Abschnitts [Registrieren eines Geräts](#enroll-device) zurück, um mit dem Setup fortzufahren.  

## <a name="token-enrollment"></a>Registrierung per Token  
In diesem Abschnitt geben Sie das von Ihrem Unternehmen bereitgestellte Token ein. Wenn Sie fertig sind, werden Sie an die Schritte für die Geräteregistrierung weitergeleitet.  

1. Geben Sie **afw#setup** auf dem Google-Anmeldebildschirm in das Feld **Email or phone** (E-Mail-Adresse oder Telefonnummer) ein. Tippen Sie auf **Weiter**. 

   ![Beispielbild des Google-Anmeldebildschirms mit „afw#setup“ im Feld](./media/token-intune-app-01.png)   

2. Tippen Sie bei der **Android-Geräterichtlinien**-App auf **Installieren**. Führen Sie die weiteren Schritte der Installation aus. Möglicherweise müssen Sie je nach Gerät weitere Nutzungsbedingungen prüfen und akzeptieren.    

3. Tippen Sie auf der Anzeige **Dieses Gerät registrieren** auf **Weiter**.  

4. Tippen Sie auf **Enter code** (Code eingeben).  

5. Geben Sie auf der Anzeige **Scan or enter code** (Code scannen oder eingeben) den Code ein, den Sie von Ihrem Unternehmen erhalten haben.  Klicken Sie anschließend auf **Weiter**.  

   ![Beispielbild der Anzeige „Scan or enter code“ (Code scannen oder eingeben) mit hervorgehobener Schaltfläche „Weiter“](./media/token-intune-app-04.png)  

6. Kehren Sie zu Schritt 4 des Abschnitts [Registrieren eines Geräts](#enroll-device) zurück, um mit dem Setup fortzufahren.  



## <a name="next-steps"></a>Nächste Schritte   
Benötigen Sie weitere Unterstützung? Wenden Sie sich an den Support Ihres Unternehmens (suchen Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980) nach Kontaktinformationen) oder an das <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-Team</a>.  
