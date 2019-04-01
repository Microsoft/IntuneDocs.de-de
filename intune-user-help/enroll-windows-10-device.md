---
title: Windows 10-Gerät bei Intune-Unternehmensportal registrieren | Microsoft-Dokumentation
description: Schritte zum Registrieren von Windows 10-Geräte in Intune-Unternehmensportal
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/11/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 812e82df-76df-402b-bfe9-29302838f40e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4eb5dbb150559de7ad30a598fb78a4fa78033c42
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2019
ms.locfileid: "58069168"
---
# <a name="enroll-windows-10-devices-with-intune-company-portal"></a>Registrieren von Windows 10-Geräten mit Intune-Unternehmensportal

Verwenden Sie Intune-Unternehmensportal-App, um Windows 10-Geräten in Ihrer Organisation registrieren. In diesem Artikel wird beschrieben, wie zum Registrieren von Geräten mit Windows 10 Version 1607 und höher und Windows 10 Version 1511 und früher wird. Bevor Sie beginnen, stellen Sie sicher, dass Sie [überprüfen Sie die Version auf Ihrem Gerät](windows-enrollment-company-portal.md#find-windows-10-version-number) , damit Sie die richtigen Schritte ausführen können.  

Windows 10 wird über verschiedene Gerätetypen, einschließlich Desktop, Smartphone und Tablet unterstützt. Die Registrierungsschritte entsprechen vom verwendeten Gerät, das Sie verwenden. Ihr Bildschirm kann jedoch über Images aus dem in diesem Artikel gezeigten etwas anders aussehen.  

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/Windows-Enrollment/player]  

## <a name="enroll-windows-10-version-1607-and-later-device"></a>Registrieren von Windows 10 Version 1607 und höher Gerät 
Diese Schritte beschrieben, wie Sie ein Gerät zu registrieren, die auf Windows 10, Version 1607 und höher ausgeführt wird.  

1. Öffnen Sie das **Startmenü**. Wenn Sie ein Windows 10 Mobile-Gerät verwenden, fahren Sie mit der **alle Apps** Liste.

2. Öffnen Sie die App **Einstellungen**. Wenn die app nicht in der Liste Ihrer apps verfügbar ist, finden Sie unter die Suchleiste und den Typ "Einstellungen".

3. Wählen Sie **Konten** > **Zugriff auf Geschäfts-, Schul- oder Unikonto** > **Verbinden** aus.  


    ![Wählen Sie „Auf Geschäfts-,Schul- oder Unikonto zugreifen“ aus](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

4. Geben Sie die E-Mail-Adresse Ihres Geschäfts-, Schul- oder Unikontos ein, und wählen Sie **Weiter** aus.  


   ![Enter your work or school-account](./media/w10-enroll-rs1-set-up-work-or-school-account.png)  

5. Melden Sie sich mit Ihrem Geschäfts-, Schul- oder Unikonto bei Intune an.  


    ![Geschäfts- oder Schulkonto hinzufügen](./media/w10-enroll-rs1-enter-your-credentials.png)  

    In einer Meldung wird schließlich angezeigt, dass Ihr Unternehmen oder Ihre Bildungseinrichtung das Gerät registriert.

6. Wenn Sie eine PIN für Windows Hello Einrichten Ihrer Organisation erforderlich ist, werden Sie aufgefordert, einen Prüfcode eingeben. Geben Sie den Code, und durchlaufen Sie die Schritte zum Erstellen einer PIN auf dem Bildschirm aus.  

7. Auf dem Bildschirm **Alles erledigt!** sehen, klicken Sie auf **Fertig**. Ihr Gerät ist jetzt bei registriert.  

8. Um die Verbindung zu überprüfen, wechseln Sie zurück zum **Einstellungen** > **Konten** > **Zugriff auf Geschäfts-, Schul- oder unikonto**.  Ihr Konto sollte jetzt aufgeführt werden.  


    ![Validate that the connection was set up correctly](./media/w10-enroll-rs1-validate-successful-enrollment.png)  

Können Sie immer noch nicht auf Ihre Geschäfts-, Schul- oder Uni-E-Mails, -Dateien oder entsprechende andere Daten zugreifen? Erfahren Sie, wie Sie [Konto Problembehandlung](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).  

## <a name="enroll-windows-10-version-1511-and-earlier-device"></a>Registrieren von Windows 10 Version 1511 und früher Gerät  
Diese Schritte beschrieben, wie Sie ein Gerät zu registrieren, die auf Windows 10, Version 1511 und früher ausgeführt wird.  

1. Öffnen Sie das **Startmenü**. Wenn Sie ein Windows 10 Mobile-Gerät verwenden, fahren Sie mit der **alle Apps** Liste.

2. Öffnen Sie die App **Einstellungen**. Wenn die app nicht in der Liste Ihrer apps verfügbar ist, finden Sie unter die Suchleiste und den Typ "Einstellungen".

3. Wählen Sie **Konten** > **Ihr Konto**.  


    ![Wählen Sie „Ihr Konto“ aus.](./media/W10-enroll-2-accounts-your-account.png)  

5. Wählen Sie **Geschäfts- oder Schulkonto hinzufügen** aus.  


    ![Wählen Sie „Geschäfts- oder Schulkonto hinzufügen“ aus.](./media/w10-enroll-3-add-work-school-acct.png)  

6. Melden Sie sich mit den Anmeldeinformationen Ihres Geschäfts- oder Schulkontos an.  


    ![Anmelden](./media/W10-enroll-4-sign-in.png)  

Können Sie immer noch nicht auf Ihre Geschäfts-, Schul- oder Uni-E-Mails, -Dateien oder entsprechende andere Daten zugreifen? Erfahren Sie, wie Sie [Konto Problembehandlung](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account).   

## <a name="next-steps"></a>Nächste Schritte  

Wenden Sie sich an den Support Ihres Unternehmens um Hilfe zu erhalten. Finden Sie Ihrer Organisation IT-Informationen zu den [unternehmensportalwebsite](https://go.microsoft.com/fwlink/?linkid=2010980). Melden Sie sich mit Ihrem Geschäfts-, Schul- oder Unikonto bei der Website an.  

 

