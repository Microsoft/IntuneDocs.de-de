---
title: Überprüfen des Gerätezugriffs | Microsoft-Dokumentation
description: Überprüfen Sie den Gerätezugriff, um zu ermitteln, ob Ihr Gerät die Anforderungen erfüllt und auf Geschäfts-, Schul- oder Uniressourcen zugreifen kann.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 49075fd750ade6aaa412d551f4177822b52ce7f2
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72490105"
---
# <a name="check-access-from-company-portal-app-for-windows"></a>Überprüfen des Zugriffs über die Unternehmensportal-App für Windows

Vergewissern Sie sich, dass Ihr Gerät Zugriff auf Geschäfts-, Schul- oder Uniressourcen hat. 

Unternehmen erzwingen Anforderungen &ndash;wie Verschlüsselung und Kennwortbegrenzung&ndash;, um sicherzustellen, dass nur sichere, vertrauenswürdige Geräte auf ihre Daten zugreifen. Verwaltete Geräte müssen diese Anforderungen erfüllen und einhalten, um auf die Ressourcen des Unternehmens zugreifen zu können.

Die Aktion **Zugriff prüfen** wertet die Einstellungen Ihres Geräts und seinen Zugriffsstatus aus. Auf der Seite **Gerätedetails** sind die Einstellungen aufgeführt, die Sie anpassen müssen, um den Zugriff wiederherzustellen. 

Führen Sie die Schritte in diesem Artikel aus, um den Zugriff von der Unternehmensportal-App für Windows zu überprüfen.  

## <a name="check-access-from-device-details-page"></a>Überprüfen des Zugriffs über die Seite „Gerätedetails“  
1. Öffnen Sie die Unternehmensportal-App für Windows und wechseln Sie zu **Meine Geräte**.  

    ![Beispielscreenshot der Unternehmensportal-App für Windows, Startseite mit hervorgehobenem Abschnitt „Meine Geräte“](./media/1809_CheckAccess_Context_Select_Device.png)  
2. Wählen Sie ein Gerät aus.  
3. Wählen Sie auf der Seite **Gerätedetails** die Option **Zugriff prüfen** aus. Die App synchronisiert Ihr Gerät mit den aktuellen Anforderungen Ihres Unternehmens und überprüft, ob Ihr Gerät mit diesen übereinstimmt. Diese Überprüfung kann einige Minuten dauern.  

    ![Beispielscreenshot der Unternehmensportal-App für Windows, Seite „Gerätedetails“, hervorgehobene Schaltfläche „Zugriff prüfen“](./media/1809_CheckAccess_Checking_Status.png) 

4. Betrachten Sie das Statusupdate. Es wird angezeigt, dass Ihr Gerät **auf die Ressourcen Ihres Unternehmens zugreifen kann** oder **nicht auf die Ressourcen Ihres Unternehmens zugreifen kann**.  

   ![Beispielscreenshot der Unternehmensportal-App für Windows, Seite „Gerätedetails“, hervorgehobener Abschnitt „Status“](./media/1809_CheckAccess_Device_details_status1.png)  
   
5. Wenn Ihr Gerät nicht auf Ressourcen zugreifen kann, wechseln Sie oben auf der Seite zu der Warnung. Klicken Sie auf **Mehr**, um die Details zu erweitern. Klicken Sie auf **Weniger**, um sie auszublenden.  

    ![Beispielscreenshot der Unternehmensportal-App für Windows, Seite „Gerätedetails“, hervorgehobene Warnung am Seitenanfang](./media/1809_CheckAccess_Device_details_alert1.png)  

6. Gegebenenfalls zeigt die Meldung zusätzliche Hilfelinks und Korrekturmaßnahmen an. Wählen Sie mindestens eine dieser Optionen aus, um die Problembehandlung sofort zu starten. Die &ndash;unten beschriebenen&ndash; Auflösungs-, Synchronisierungs- und Kontaktaktionen werden nur angezeigt, wenn Sie das Unternehmensportal auf dem betroffenen Gerät verwenden.  

     * **Problembehebung** öffnet einen entsprechenden Hilfeartikel, falls verfügbar.  
     * **Auflösen** leitet Sie zu der Einstellung auf Ihrem Gerät weiter.  
     * **Synchronisieren** wertet Ihr Gerät aus, um sicherzustellen, dass es den Anforderungen Ihres Unternehmens entspricht.  
     * **An IT-Abteilung wenden** leitet Sie zu den Kontaktinformationen Ihres IT-Teams weiter.   
 
6. Nachdem Sie die Einstellungen aktualisiert haben, klicken Sie auf **Zugriff prüfen**, um den Status Ihres Geräts zu bestätigen.  

    ![Beispielscreenshot der Unternehmensportal-App für Windows, Seite „Gerätedetails“, hervorgehobener Abschnitt „Status“](./media/1809_CheckAccess_Device_details_status1.png)  

## <a name="check-access-from-device-context-menu"></a>Prüfen des Zugriffs über das Kontextmenü des Geräts  
1. Öffnen Sie die Unternehmensportal-App für Windows und wechseln Sie zu **Meine Geräte**.  

    ![Beispielscreenshot der Unternehmensportal-App für Windows, Startseite mit hervorgehobenem Abschnitt „Meine Geräte“](./media/1809_CheckAccess_Context_Select_Device.png)  

2. Klicken Sie mit der rechten Maustaste, oder tippen Sie auf ein Gerät, und halten Sie es gedrückt, um das [Kontextmenü](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus) zu öffnen.  

    ![Beispielscreenshot der Unternehmensportal-App für Windows, Startseite Das Kontextmenü für das Gerät wird im Abschnitt **Meine Geräte** auf der Seite angezeigt und enthält die Aktionen „Umbenennen“, „Entfernen“ und „Zugriff prüfen“.](./media/1809_DeviceContextMenu_Windows_CP.png)  
3. Wählen Sie **Zugriff prüfen** aus. Die App synchronisiert Ihr Gerät mit den aktuellen Anforderungen Ihres Unternehmens und überprüft, ob Ihr Gerät mit diesen übereinstimmt. Diese Überprüfung kann einige Minuten dauern.  
 
4. Unter dem Gerät wird eine Meldung angezeigt, die Sie darüber informiert, ob das Gerät **auf Unternehmensressourcen zugreifen kann** oder **nicht auf Unternehmensressourcen zugreifen kann**. 

    ![Beispielscreenshot der Unternehmensportal-App für Windows, Seite „Gerätedetails“, hervorgehobener Abschnitt „Status“](./media/1809_CheckAccess_Context_Menu_Alert2.png) 

5. Wenn Ihr Gerät nicht auf Ressourcen zugreifen kann, wählen Sie das Gerät aus.  
6. Wechseln Sie auf der Seite **Gerätedetails** am oberen Seitenrand zu der Warnung. Klicken Sie auf **Mehr**, um die Details zu erweitern. Klicken Sie auf **Weniger**, um sie auszublenden.  

    ![Beispielscreenshot der Unternehmensportal-App für Windows, Seite „Gerätedetails“, hervorgehobene Warnung am Seitenanfang](./media/1809_CheckAccess_Device_details_alert1.png)  

6. Gegebenenfalls zeigt die Meldung zusätzliche Hilfelinks und Korrekturmaßnahmen an. Wählen Sie mindestens eine dieser Optionen aus, um die Problembehandlung sofort zu starten. Die &ndash;unten beschriebenen&ndash; Auflösungs-, Synchronisierungs- und Kontaktaktionen werden nur angezeigt, wenn Sie das Unternehmensportal auf dem betroffenen Gerät verwenden.  

     * **Problembehebung** öffnet einen entsprechenden Hilfeartikel, falls verfügbar.  
     * **Auflösen** leitet Sie zu der Einstellung auf Ihrem Gerät weiter.  
     * **Synchronisieren** wertet Ihr Gerät aus, um sicherzustellen, dass es den Anforderungen Ihres Unternehmens entspricht.  
     * **An IT-Abteilung wenden** leitet Sie zu den Kontaktinformationen Ihres IT-Teams weiter.    

7. Nachdem Sie die Einstellungen aktualisiert haben, klicken Sie am unteren Seitenrand auf **Zugriff prüfen**.  

    ![Beispielscreenshot der Unternehmensportal-App für Windows, Seite „Gerätedetails“, hervorgehobene Aktion „Zugriff prüfen“](./media/1809_CheckAccess_Device_details_button.png) 


Benötigen Sie weitere Hilfe? Die Kontaktinformationen für die Supportabteilung Ihres Unternehmens finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).
