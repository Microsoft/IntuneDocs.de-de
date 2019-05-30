---
title: 'Tutorial: Überblick über Intune im Azure-Portal'
titleSuffix: Microsoft Intune
description: In diesem Tutorial wird Microsoft Intune vorgestellt, um Sie in die Arbeitsweise mit Intune einzuführen.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 03/28/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e892d8a3-7f74-498c-98d5-e968a8fbb049
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c84cd0ec61ea08956bbebd040167991c6285d073
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66044984"
---
# <a name="tutorial-walkthrough-of-microsoft-intune-in-the-azure-portal"></a>Tutorial: Überblick über Microsoft Intune im Azure-Portal

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) enthält über 100 Dienste, die Sie bei vielen Cloud Computing-Szenarios unterstützen. Microsoft Intune ist nur einer von vielen Diensten, die in Azure verfügbar sind. Mithilfe von Intune können Sie sicherstellen, dass die Geräte, Apps und Daten Ihres Unternehmens die entsprechenden Sicherheitsanforderungen erfüllen. Sie können festlegen, welche Anforderungen erfüllt werden müssen, und welche Maßnahmen vorgenommen werden, wenn diese nicht erfüllt sind. Sie finden den Microsoft Intune-Dienst im [Azure-Portal](https://portal.azure.com). Mithilfe der Features in Intune können Sie verschiedene MDM- (Mobile Geräteverwaltung) und MAM-Aufgaben (Mobile Anwendungsverwaltung) erledigen.

Inhalt des Tutorials:
> [!div class="checklist"]
> * Überblick über Microsoft Intune
> * Konfigurieren des Azure-Portals

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="prerequisites"></a>Voraussetzungen
Prüfen Sie vor der Einrichtung von Microsoft Intune die folgenden Anforderungen:

   - [Unterstützte Betriebssysteme und Browser](supported-devices-browsers.md) 
   - [Bandbreite und Anforderungen an die Netzkonfiguration](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Registrieren für eine kostenlose Testversion von Microsoft Intune

Sie können Intune 30 Tage lang kostenlos testen. Wenn Sie bereits über ein Arbeits- oder Schulkonto verfügen, **melden Sie sich mit diesem Konto an**, und fügen Sie Intune Ihrem Abonnement hinzu. Sie können sich auch für ein [kostenloses Testkonto registrieren](free-trial-sign-up.md), um Intune für Ihre Organisation zu verwenden.

> [!IMPORTANT]
> Sie können kein bestehendes Arbeits- oder Schulkonto nach der Registrierung für ein neues Konto kombinieren.

## <a name="tour-microsoft-intune"></a>Überblick über Microsoft Intune

Befolgen Sie diese Schritte, um Intune im Azure-Portal besser kennen zu lernen. Nach der Tour durch Intune sollten Sie mit den wichtigsten Features von Intune vertraut sein.

1. Öffnen Sie einen Browser, und melden Sie sich beim [Intune-Portal](https://aka.ms/intuneportal) an. Wenn Sie noch nicht bei Intune registriert sind, können Sie ein kostenloses Testabonnement anlegen.

    ![Screenshot des Microsoft Intune-Portals](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-01.png)

    Wenn Sie Intune oder einen anderen Dienst in Azure öffnen, wird der Dienst in einem Bereich angezeigt. Sie verwenden in Intune voraussichtlich zunächst die Workloads **Geräte**, **Client-Apps**, **Benutzer** und **Gruppen**. Bei einer Workload handelt es sich um einen Unterbereich eines Diensts. Wenn Sie eine Workload auswählen, wird dieser Bereich im Vollbildmodus geöffnet. Wenn Sie weitere Bereiche öffnen, werden diese von der rechten Seite des aktuellen Bereichs aus geöffnet. Wenn Sie einen Bereich schließen, wird der vorherige Bereich wieder angezeigt. Bereiche werden auch als Blätter bezeichnet. 

    Wenn Sie Intune öffnen, wird standardmäßig der Bereich **Übersicht** angezeigt. In diesem Bereich finden Sie eine Gesamtübersicht über die Gerätezuweisungen, den Konformitätsstatus und den Installationsstatus von Apps.

2. Navigieren Sie in [Intune](https://aka.ms/intuneportal) zu **Geräteregistrierung**, um Details zu den im Intune-Mandanten registrierten Geräten anzuzeigen. Wenn Sie einen neuen Intune-Mandanten erstellt haben, sind noch keine Geräte registriert. 

    ![Screenshot des Bereichs „Geräteregistrierung“](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-02.png)
    
    Intune ermöglicht es Ihnen, die Geräte und Apps Ihrer Mitarbeiter sowie deren Zugriff auf Ihre Unternehmensdaten zu verwalten. Damit diese mobile Geräteverwaltung (Mobile Device Management, MDM) genutzt werden kann, müssen die Geräte zunächst bei Intune registriert werden. Wenn ein Gerät registriert ist, wird ein MDM-Zertifikat für das Gerät ausgestellt. Dieses Zertifikat wird für die Kommunikation mit dem Intune-Dienst verwendet. 

    Es gibt verschiedene Methoden, um die Geräte Ihrer Mitarbeiter in Intune zu registrieren. Die einzelnen Methoden hängen vom Gerätebesitz (persönlich oder unternehmenseigen), vom Gerätetyp (iOS, Windows, Android) und den Verwaltungsanforderungen (Zurücksetzungen, Affinität, Sperren) ab. Bevor Sie die Geräteregistrierung aktivieren können, müssen Sie jedoch Ihre Intune-Infrastruktur einrichten. Besonders für die Geräteregistrierung ist es erforderlich, dass Sie [die MDM-Autorität festlegen](mdm-authority-set.md). Weitere Informationen zum Einrichten Ihrer Intune-Umgebung (d.h. Ihres Intune-Mandanten) finden Sie unter [Einrichten von Intune](setup-steps.md). Sobald Ihr Intune-Mandant eingerichtet ist, können Sie Geräte registrieren. Weitere Informationen finden Sie unter [What is device enrollment? (Was ist eine Geräteregistrierung?)](device-enrollment.md)

3. Navigieren Sie in [Intune](https://aka.ms/intuneportal) zu **Gerätekonformität**, um Details zur Konformität der Geräte anzuzeigen, die von Intune verwaltet werden. Diese Details sollten folgender Abbildung ähneln.

    ![Screenshot des Bereichs „Gerätekonformität“](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-03.png)
    
    Bei Konformitätsanforderungen handelt es sich um die wesentlichen Regeln (z.B. das Erfordern eines Geräte-PIN oder der Geräteverschlüsselung). Über Gerätekonformitätsrichtlinien werden diese Regeln und Einstellungen definiert, die ein Gerät erfüllen muss, damit es als konform eingestuft wird. Voraussetzungen für die Verwendung der Option „Gerätekonformität“:
    - Ein Intune- und ein Azure Active Directory Premium-Abonnement
    - Geräte mit einer unterstützten Plattform
    - Bei Intune registrierte Geräte
    - Geräte, die für einen Benutzer oder ohne primären Benutzer registriert wurden
    
    Weitere Informationen finden Sie unter [Erste Schritte mit den Gerätekonformitätsrichtlinien in Intune](device-compliance-get-started.md).

4. Navigieren Sie in [Intune](https://aka.ms/intuneportal) zu **Gerätekonfiguration**, um Details zu den Geräteprofilen in Intune anzuzeigen. 

    ![Screenshot des Bereichs „Gerätekonfiguration“](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-04.png)
    
    Intune umfasst Einstellungen und Features, die Sie auf unterschiedlichen Geräten in Ihrer Organisation aktivieren oder deaktivieren können. Diese Einstellungen und Funktionen werden zu „Konfigurationsprofilen“ hinzugefügt. Sie können Profile für unterschiedliche Geräte und Plattformen einrichten, z.B. für iOS, Android und Windows. Anschließend können Sie Intune verwenden, um das Profil auf die Geräte in Ihrer Organisation anzuwenden.   

    Weitere Informationen zur Gerätekonfiguration finden Sie unter [Anwenden von Einstellungen für Funktionen auf Ihren Geräten mit Geräteprofilen in Microsoft Intune](device-profiles.md).

5. Navigieren Sie in [Intune](https://aka.ms/intuneportal) zu **Geräte**, um Details zu den im Intune-Mandanten registrierten Geräten anzuzeigen. Wenn Sie eine neue Intune-Instanz erstellt haben, sind noch keine Geräte registriert. 

    ![Screenshot des Bereichs „Geräteregistrierung“](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-05.png)
    
    Im Bereich **Geräte** finden Sie Details zu den im Mandanten registrierten Geräten. Sie können auf **Alle Geräte** klicken, um die Liste der Geräte im Intune-Mandanten anzuzeigen. 

6. Navigieren Sie in [Intune](https://aka.ms/intuneportal) zu **Client-Apps**, um den Installationsstatus Ihrer Apps anzuzeigen.

    ![Screenshot des Bereichs „Client-Apps“](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-06.png)
    
    Als IT-Administrator können Sie mit Microsoft Intune die Client-Apps verwalten, die Mitarbeiter Ihres Unternehmens verwenden. Diese Funktion besteht zusätzlich zur Verwaltung von Geräten und dem Schutz von Daten. Eine der Prioritäten eines Administrators ist es, sicherzustellen, dass die Endbenutzer Zugriff auf die Apps haben, die sie für ihre Arbeit benötigen. Darüber hinaus sollten Sie Apps auf Geräten, die nicht bei Intune registriert sind, zuweisen und verwalten. Intune bietet eine Reihe von Funktionen, die die Installation der erforderlichen Apps auf den gewünschten Geräten unterstützen. Weitere Informationen zum Hinzufügen und Zuweisen von Apps finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md) und [Zuweisen von Apps zu Gruppen mit Microsoft Intune](apps-deploy.md).

7. Navigieren Sie in [Intune](https://aka.ms/intuneportal) zu **Bedingter Zugriff**, um Details zu den Zugriffsrichtlinien anzuzeigen.

    ![Screenshot des Bereichs „Bedingter Zugriff“](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-07.png)

    Der Begriff „bedingter Zugriff“ bezieht sich auf Möglichkeiten zum Steuern der Geräte und Apps, die eine Verbindung mit E-Mail- und Unternehmensressourcen herstellen dürfen. Weitere Informationen zu gerätebasiertem und App-basiertem bedingtem Zugriff und zu häufigen Szenarios zur Verwendung des bedingten Zugriffs mit Intune finden Sie unter [Was ist bedingter Zugriff?](conditional-access.md).

8. Navigieren Sie in [Intune](https://aka.ms/intuneportal) zu **Benutzer**, um Details zu den Benutzern anzuzeigen, die über Intune verwaltet werden. Bei diesen Benutzern handelt es sich um die Mitarbeiter Ihres Unternehmens. 
 
    ![Screenshot des Bereichs „Benutzer“](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-08.png)

    Sie können Benutzer direkt oder durch Synchronisieren mit einer lokalen Active Directory-Instanz zu Intune hinzufügen. Nachdem ein Benutzer hinzugefügt wurde, kann er Geräte registrieren und auf Unternehmensressourcen zugreifen. Sie können den Benutzern auch zusätzliche Berechtigungen für den Zugriff auf Intune erteilen. Weitere Informationen finden Sie unter [Hinzufügen von Benutzern und Gewähren von Administratorrechten für Intune](users-add.md).

9. Navigieren Sie in [Intune](https://aka.ms/intuneportal) zu **Gruppen**, um Details zu den Azure Active Directory-Gruppen in Intune anzuzeigen. Intune-Administratoren verwenden Gruppen, um Geräte und Benutzer zu verwalten. 

    ![Screenshot des Bereichs „Gruppen“](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-09.png)

    Sie können Gruppen so einrichten, dass sie den Anforderungen Ihrer Organisation entsprechen. Sie können Gruppen erstellen, um Benutzer oder Geräte nach geografischem Standort, Abteilung oder Hardwareeigenschaften zu organisieren. Sie können Gruppen zur bedarfsgerechten Verwaltung von Aufgaben verwenden. So können Sie beispielsweise Richtlinien für viele Benutzer festlegen oder Apps für mehrere Geräte bereitstellen. Weitere Informationen zu Gruppen finden Sie unter [Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten](groups-add.md).

10. Navigieren Sie in [Intune](https://aka.ms/intuneportal) zu **Hilfe und Support**, wenn Sie Hilfe benötigen. Als IT-Administrator können Sie die Option **Hilfe und Support** verwenden, um Problembehebungen zu durchsuchen und ein Onlinesupportticket für Intune einzureichen. 

    ![Screenshot des Bereichs „Hilfe und Support“](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-10.png)

    Damit Sie ein Supportticket erstellen können, muss Ihrem Konto eine Administratorrolle in Azure Active Directory zugewiesen sein. Zu den Administratorrollen zählen **Intune-Administrator**, **Globaler Administrator** und **Dienstadministrator**. Weitere Informationen finden Sie unter [Anfordern von Support für Microsoft Intune](get-support.md).

11. Navigieren Sie in [Intune](https://aka.ms/intuneportal) zu **Tenant Status** (Mandantenstatus), um Details zu Ihrem Intune-Mandanten anzuzeigen.

    ![Screenshot des Bereichs „Tenant Status“ (Mandantenstatus)](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-11.png)

    In diesem Bereich werden Details zum Connectorstatus, zur Integrität des Intune-Diensts und Neuigkeiten zu Intune angezeigt. Wenn Probleme mit Ihrem Mandanten oder Intune vorliegen, finden Sie im Bereich **Tenant Status** (Mandantenstatus) weitere Details dazu. Weitere Informationen finden Sie unter [Seite des Intune-Mandantenstatus](tenant-status.md).

12. Navigieren Sie in [Intune](https://aka.ms/intuneportal) zu **Problembehandlung**, um schnell und einfach Tipps zur Problembehandlung zu erhalten, Support anzufordern oder den Status von Intune zu überprüfen. Diese Informationen hängen vom ausgewählten Intune-Benutzer ab.

    ![Screenshot des Bereichs „Problembehandlung“](media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-12.png)

Weitere Informationen zur Problembehandlung in Intune finden Sie unter [Verwenden des Problembehandlungsportals zur Unterstützung von Benutzern Ihres Unternehmens](help-desk-operators.md).

## <a name="configure-the-azure-portal"></a>Konfigurieren des Azure-Portals

Mit Azure können Sie die Ansicht des Portals nach Belieben konfigurieren.

### <a name="change-the-sidebar"></a>Ändern der Randleiste

Die **Randleiste** links im Azure-Portal zeigt eine Liste aller verfügbaren Azure-Dienste. Die Standardansicht dieser umfassenden Liste kann geändert werden, damit Sie einen Überblick über die Dienste behalten, die für Sie am wichtigsten sind. Die unten stehenden Informationen verwenden Intune als das Beispiel für einen Dienst, der am Anfang der Liste hinzugefügt werden soll.

![Ein Benutzer, der in der Liste „Weitere Dienste“ nach Microsoft Intune sucht.](./media/azure-add-intune1.png)

1. Wählen Sie in der linken Randleiste **Alle Dienste** aus.
2. Suchen Sie im Filterfeld nach **Intune**.
3. Klicken Sie auf den **Stern**, um Intune am Ende der Liste Ihrer bevorzugten Dienste hinzuzufügen.
4. Zeigen Sie auf den Intune-Dienst. Wählen Sie Intune aus, und ziehen Sie Intune mit den **drei vertikalen Punkten** rechts neben dem Dienstnamen.

### <a name="change-the-dashboard"></a>Ändern des Dashboards

Ihre Standardstartseite ist das **Dashboard**. Auf dieser Seite passen Sie Ihre Kacheln so an, dass nur die wichtigsten Informationen angezeigt werden.

![Bild eines generischen neuen Dashboards Dort wird links die Randleiste mit allen Diensten und das Hauptdashboard in der Mitte dargestellt. Die Schaltflächen für das Anpassen des Dashboards sind entlang des oberen Rands angeordnet. Die Kacheln darauf bieten Zugriff auf alle Ressourcen, Schnellstart-Tutorials, den Dienststatus und den Azure Marketplace.](./media/azure-default-dashboard.png)

Um Ihr aktuelles Dashboard anzupassen, klicken Sie auf **Dashboard bearbeiten**. Wenn Sie das Standarddashboard nicht ändern möchten, können Sie auch ein **neues Dashboard** erstellen. Beim Erstellen eines neuen Dashboards beginnen Sie mit einem leeren, privaten Dashboard mit dem **Kachelkatalog**, mit dem Sie Kacheln hinzufügen oder neu arrangieren können. Die Kacheln lassen sich anhand der Kategorie **Allgemein**, ihrem **Typ**, über die **Suche** und über eine **Ressourcengruppe** oder ein **Tag** finden.

Sie können Ihrem Dashboard über eine Schaltfläche mit **Auslassungspunkten** und anschließendem Auswählen von **An Dashboard anheften** auch direkt Kacheln hinzufügen.

![Eine Nahaufnahme des Speicherorts „Benutzer und Gruppen“ > „Alle Gruppen“ in Intune, mit der Option „An Dashboard anheften“ rechts von einer Gruppe](./media/azure-pin-to-dashboard.png)

Diese Fähigkeit wird wichtiger, wenn Sie mehr Inhalte wie Gruppen und Benutzer in Intune hinzugefügt haben.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie schnell in Microsoft Intune einsteigen möchten, sollten Sie die Intune-Schnellstarts abschließen. Hierfür müssen Sie zunächst ein kostenloses Intune-Konto erstellen.

> [!div class="nextstepaction"]
> [Schnellstart: Testen Sie Microsoft Intune kostenlos](free-trial-sign-up.md)


