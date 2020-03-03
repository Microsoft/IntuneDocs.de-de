---
title: 'Tutorial: Exemplarische Vorgehensweise zu Intune in Microsoft Endpoint Manager'
titleSuffix: Microsoft Intune
description: In diesem Tutorial wird Microsoft Intune im Microsoft Endpoint Manager Admin Center vorgestellt, um Sie in die Arbeitsweise mit Intune einzuführen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune from the Microsoft Endpoint Manager admin center.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d8950e57c2427c522d337807d315ed5c399c0d5
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514080"
---
# <a name="tutorial-walkthrough-intune-in-microsoft-endpoint-manager"></a>Tutorial: Exemplarische Vorgehensweise für Intune in Microsoft Endpoint Manager

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) enthält über 100 Dienste, die Sie bei vielen Cloud Computing-Szenarios unterstützen. Microsoft Intune ist nur einer von vielen Diensten, die in Azure verfügbar sind. Mithilfe von Intune können Sie sicherstellen, dass die Geräte, Apps und Daten Ihres Unternehmens die entsprechenden Sicherheitsanforderungen erfüllen. Sie können festlegen, welche Anforderungen erfüllt werden müssen, und welche Maßnahmen vorgenommen werden, wenn diese nicht erfüllt sind. Im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) finden Sie den Microsoft Intune-Dienst sowie andere Einstellungen für die Geräteverwaltung. Mithilfe der Features in Intune können Sie verschiedene MDM- (Mobile Geräteverwaltung) und MAM-Aufgaben (Mobile Anwendungsverwaltung) erledigen.

> [!NOTE]
> Bei Microsoft Endpoint Manager handelt es sich um eine einzelne, integrierte Endpunktverwaltungsplattform zum Verwalten aller Endpunkte. Im Microsoft Endpoint Manager Admin Center sind ConfigMgr und Microsoft Intune integriert.

Inhalt des Tutorials:
> [!div class="checklist"]
> * Vorstellung des Microsoft Endpoint Manager Admin Centers
> * Anpassung der Ansicht des Microsoft Endpoint Manager Admin Centers

Wenn Sie über kein Intune-Abonnement verfügen, [registrieren Sie sich für eine kostenlose Testversion](free-trial-sign-up.md).

## <a name="prerequisites"></a>Voraussetzungen
Prüfen Sie vor der Einrichtung von Microsoft Intune die folgenden Anforderungen:

- [Unterstützte Betriebssysteme und Browser](../supported-devices-browsers.md) 
- [Bandbreite und Anforderungen an die Netzkonfiguration](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Registrieren für eine kostenlose Testversion von Microsoft Intune

Sie können Intune 30 Tage lang kostenlos testen. Wenn Sie bereits über ein Arbeits- oder Schulkonto verfügen, **melden Sie sich mit diesem Konto an**, und fügen Sie Intune Ihrem Abonnement hinzu. Sie können sich auch für ein [kostenloses Testkonto registrieren](free-trial-sign-up.md), um Intune für Ihre Organisation zu verwenden.

> [!IMPORTANT]
> Sie können kein bestehendes Arbeits- oder Schulkonto nach der Registrierung für ein neues Konto kombinieren.

## <a name="tour-microsoft-intune-in-the-microsoft-endpoint-manager-admin-center"></a>Vorstellung des Microsoft Intune-Diensts im Microsoft Endpoint Manager Admin Center

Befolgen Sie die folgenden Schritte, um Intune im Microsoft Endpoint Manager Admin Center besser zu verstehen. Nach der Tour durch Intune sollten Sie mit den wichtigsten Features von Intune vertraut sein.

1. Öffnen Sie einen Browser, und melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an. Wenn Sie noch nicht bei Intune registriert sind, können Sie ein kostenloses Testabonnement anlegen.

    ![Screenshot: „Homepage“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-01.png)

    Wenn Sie Microsoft Endpoint Manager oder einen anderen Dienst in Azure öffnen, wird der Dienst in einem Bereich angezeigt. Sie verwenden in Intune voraussichtlich zunächst die Workloads **Geräte**, **Apps**, **Benutzer** und **Gruppen**. Bei einer Workload handelt es sich um einen Unterbereich eines Diensts. Wenn Sie eine Workload auswählen, wird dieser Bereich im Vollbildmodus geöffnet. Wenn Sie weitere Bereiche öffnen, werden diese von der rechten Seite des aktuellen Bereichs aus geöffnet. Wenn Sie einen Bereich schließen, wird der vorherige Bereich wieder angezeigt. 

    Sie werden standardmäßig den Bereich **Homepage** sehen, wenn Sie Microsoft Endpoint Manager öffnen. Dieser Bereich bietet eine allgemeine visuelle Momentaufnahme des Mandantenstatus und des Konformitätsstatus sowie weitere hilfreiche zugehörige Links.

2. Wählen Sie im Navigationsbereich **Dashboard** aus, um die allgemeinen Details über die Geräte und Client-Apps in Ihrem Intune-Mandanten zu erhalten. Wenn Sie einen neuen Intune-Mandanten erstellt haben, sind noch keine Geräte registriert. 

    ![Screenshot: „Dashboard“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-02.png)
    
    Intune ermöglicht es Ihnen, die Geräte und Apps Ihrer Mitarbeiter sowie deren Zugriff auf Ihre Unternehmensdaten zu verwalten. Damit diese mobile Geräteverwaltung (Mobile Device Management, MDM) genutzt werden kann, müssen die Geräte zunächst bei Intune registriert werden. Wenn ein Gerät registriert ist, wird ein MDM-Zertifikat für das Gerät ausgestellt. Dieses Zertifikat wird für die Kommunikation mit dem Intune-Dienst verwendet. 

    Es gibt verschiedene Methoden, um die Geräte Ihrer Mitarbeiter in Intune zu registrieren. Die einzelnen Methoden hängen vom Gerätebesitz (persönlich oder unternehmenseigen), vom Gerätetyp (iOS/iPadOS, Windows, Android) und den Verwaltungsanforderungen (Zurücksetzungen, Affinität, Sperren) ab. Bevor Sie die Geräteregistrierung aktivieren können, müssen Sie jedoch Ihre Intune-Infrastruktur einrichten. Besonders für die Geräteregistrierung ist es erforderlich, dass Sie [die MDM-Autorität festlegen](mdm-authority-set.md). Weitere Informationen zum Einrichten Ihrer Intune-Umgebung (d.h. Ihres Intune-Mandanten) finden Sie unter [Einrichten von Intune](setup-steps.md). Sobald Ihr Intune-Mandant eingerichtet ist, können Sie Geräte registrieren. Weitere Informationen finden Sie unter [What is device enrollment? (Was ist eine Geräteregistrierung?)](../enrollment/device-enrollment.md)

3. Wählen Sie im Navigationsbereich **Geräte** aus, um Details zu registrierten Geräten in Ihrem Intune-Mandanten zu erhalten. 

    > [!TIP]
    > Wenn Sie im Azure-Portal zuvor bereits Intune verwendet haben, befanden sich die oben aufgeführten Details im Azure-Portal, indem Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) angemeldet und **Geräte** ausgewählt haben.

    Der Bereich **Devices – Overview** (Geräte – Übersicht) verfügt über mehrere Registerkarten, mit denen Sie eine Zusammenfassung der folgenden Status und Warnmeldungen sehen können:
    - **Registrierungsstatus:** Überprüfen Sie die Details über die mit Intune registrierten Geräte nach Plattform- und Registrierungsfehler.
    - **Registrierungswarnungen:** Erfahren Sie weitere Details über nicht zugewiesene Geräte nach Plattform. 
    - **Compliance status:** (Konformitätsstatus) Überprüfen Sie basierend auf dem Gerät, der Richtlinie, der Einstellung, der Bedrohung und dem Schutz den Konformitätsstatus. Zusätzlich dazu finden Sie in diesem Bereich eine Liste mit Geräten ohne eine Konformitätsrichtlinie.
    - **Konfigurationsstatus:** Überprüfen Sie den Konfigurationsstatus von Geräteprofilen als auch von der Gerätebereitstellung. 
    - **Softwareupdatestatus:** Sehen Sie ein Visual des Bereitstellungsstatus für alle Geräte und für alle Benutzer.

    ![Screenshot: „Devices – Overview“ (Geräte – Übersicht) des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-03.png)

4. Wählen Sie im Bereich **Devices – Overview** (Geräte – Übersicht) **Konformitätsrichtlinien** aus, um Details zu durch Intune verwaltete Gerätekonformitätsrichtlinien zu erhalten. Diese Details sollten folgender Abbildung ähneln.

    ![Screenshot: „Konformitätsrichtlinien“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-04.png)
    
    > [!TIP]
    > Wenn Sie im Azure-Portal zuvor bereits Intune verwendet haben, befanden sich die oben aufgeführten Details im Azure-Portal, indem Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) angemeldet und **Gerätekonformität** ausgewählt haben.

    Bei Konformitätsanforderungen handelt es sich um die wesentlichen Regeln (z. B. das Erfordern eines Geräte-PIN oder der Geräteverschlüsselung). Über Gerätekonformitätsrichtlinien werden diese Regeln und Einstellungen definiert, die ein Gerät erfüllen muss, damit es als konform eingestuft wird. Voraussetzungen für die Verwendung der Option „Gerätekonformität“:
    - Ein Intune- und ein Azure Active Directory Premium-Abonnement
    - Geräte mit einer unterstützten Plattform
    - Bei Intune registrierte Geräte
    - Geräte, die für einen Benutzer oder ohne primären Benutzer registriert wurden
    
    Weitere Informationen finden Sie unter [Erste Schritte mit den Gerätekonformitätsrichtlinien in Intune](../protect/device-compliance-get-started.md).

5. Wählen Sie im Bereich **Devices – Overview** (Geräte – Übersicht) **Bedingter Zugriff** aus, um Details zu den Zugriffsrichtlinien zu erhalten.

    ![Screenshot: „Bedingter Zugriff“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-05.png)

    > [!TIP]
    > Wenn Sie im Azure-Portal zuvor bereits Intune verwendet haben, befanden sich die oben aufgeführten Details im Azure-Portal, indem Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) angemeldet und **Bedingter Zugriff** ausgewählt haben.

    Der Begriff „bedingter Zugriff“ bezieht sich auf Möglichkeiten zum Steuern der Geräte und Apps, die eine Verbindung mit E-Mail- und Unternehmensressourcen herstellen dürfen. Weitere Informationen zu gerätebasiertem und App-basiertem bedingtem Zugriff und zu gängigen Szenarien zur Verwendung des bedingten Zugriffs mit Intune finden Sie unter [Was ist bedingter Zugriff?](../protect/conditional-access.md).

6. Wählen Sie im Navigationsbereich **Geräte** > **Konfigurationsprofile** aus, um Details zu den Geräteprofilen in Intune zu erhalten.

    ![Screenshot: „Konfigurationsprofile“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-06.png)
    
    > [!TIP]
    > Wenn Sie im Azure-Portal zuvor bereits Intune verwendet haben, befanden sich die oben aufgeführten Details im Azure-Portal, indem Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) angemeldet und **Gerätekonfiguration** ausgewählt haben.

    Intune umfasst Einstellungen und Features, die Sie auf unterschiedlichen Geräten in Ihrer Organisation aktivieren oder deaktivieren können. Diese Einstellungen und Funktionen werden zu „Konfigurationsprofilen“ hinzugefügt. Sie können Profile für unterschiedliche Geräte und Plattformen erstellen, z. B. für iOS/iPadOS, Android, macOS und Windows. Anschließend können Sie Intune verwenden, um das Profil auf die Geräte in Ihrer Organisation anzuwenden.   

    Weitere Informationen zur Gerätekonfiguration finden Sie unter [Anwenden von Einstellungen für Funktionen auf Ihren Geräten mit Geräteprofilen in Microsoft Intune](../configuration/device-profiles.md).

7. Wählen Sie im Navigationsbereich **Geräte** > **Alle Geräte** aus, um Details zu registrierten Geräten Ihrer Intune-Mandanten zu erhalten. Wenn Sie eine neue Intune-Instanz erstellt haben, sind noch keine Geräte registriert.

    ![Screenshot: „Alle Geräte“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-07.png)

    Diese Geräteliste enthält wichtige Details zur Konformität, Betriebssystemversion und zum letzten Eincheckvorgang.

    > [!TIP]
    > Wenn Sie im Azure-Portal zuvor bereits Intune verwendet haben, befanden sich die oben aufgeführten Details im Azure-Portal, indem Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) angemeldet und **Geräte** > **Alle Geräte** ausgewählt haben.
 
8. Wählen Sie im Navigationsbereich **Apps** aus, um eine Übersicht über den App-Status zu erhalten. Dieser Bereich enthält den App-Installationsstatus basierend auf den folgenden Registerkarten:

    > [!TIP]
    > Wenn Sie im Azure-Portal zuvor bereits Intune verwendet haben, befanden sich die oben aufgeführten Details im Azure-Portal, indem Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) angemeldet und **Client-Apps** ausgewählt haben.

    Der Bereich **Apps – Overview** (Apps – Übersicht) verfügt über zwei Registerkarten, mit denen Sie eine Zusammenfassung der folgenden Status sehen können:
    - **Installationsstatus:** Sehen Sie die häufigsten Installationsfehler nach Gerät und die Apps mit Installationsfehlern.  
    - **App-Schutzrichtlinienstatus:** Erhalten Sie Details zu zugewiesenen und gekennzeichneten Benutzern in App-Schutzrichtlinien.

    ![Screenshot: „Apps“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-08.png)

    Als IT-Administrator können Sie mit Microsoft Intune die Client-Apps verwalten, die Mitarbeiter Ihres Unternehmens verwenden. Diese Funktion besteht zusätzlich zur Verwaltung von Geräten und dem Schutz von Daten. Eine der Prioritäten eines Administrators ist es, sicherzustellen, dass die Endbenutzer Zugriff auf die Apps haben, die sie für ihre Arbeit benötigen. Darüber hinaus sollten Sie Apps auf Geräten, die nicht bei Intune registriert sind, zuweisen und verwalten. Intune bietet eine Reihe von Funktionen, die die Installation der erforderlichen Apps auf den gewünschten Geräten unterstützen. 

    > [!NOTE]
    > Der Bereich **Apps – Overview** (Apps – Übersicht) enthält außerdem den Mandantenstatus und Kontodetails.

    Weitere Informationen zum Hinzufügen und Zuweisen von Apps finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](../apps/apps-add.md) und [Zuweisen von Apps zu Gruppen mit Microsoft Intune](../apps/apps-deploy.md).

9. Wählen Sie im Bereich **Apps – Overview** (Apps – Übersicht) **Alle Apps** aus, um die in Intune hinzugefügte App-Liste zu erhalten.

    > [!TIP]
    > Wenn Sie im Azure-Portal zuvor bereits Intune verwendet haben, befanden sich die oben aufgeführten Details im Azure-Portal, indem Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) angemeldet und **Client-Apps** > **Apps** ausgewählt haben.

    Sie können mehrere unterschiedliche App-Typen basierend auf der Plattform in Intune hinzufügen. Sobald eine App hinzugefügt wurde, können Sie diese Benutzergruppen zuweisen. 

    ![Screenshot: „Alle Apps“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-09.png)

    Weitere Informationen finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](~/apps/apps-add.md). 

10. Wählen Sie im Navigationsbereich **Benutzer** aus, um Details zu in Intune inbegriffenen Benutzern zu erhalten. Bei diesen Benutzern handelt es sich um die Mitarbeiter Ihres Unternehmens.

    ![Screenshot: „Benutzer“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-10.png)

    > [!TIP]
    > Wenn Sie im Azure-Portal zuvor bereits Intune verwendet haben, befanden sich die oben aufgeführten Details im Azure-Portal, indem Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) angemeldet und **Benutzer** ausgewählt haben.

    Sie können Benutzer direkt oder durch Synchronisieren mit einer lokalen Active Directory-Instanz zu Intune hinzufügen. Nachdem ein Benutzer hinzugefügt wurde, kann er Geräte registrieren und auf Unternehmensressourcen zugreifen. Sie können den Benutzern auch zusätzliche Berechtigungen für den Zugriff auf Intune erteilen. Weitere Informationen finden Sie unter [Hinzufügen von Benutzern und Gewähren von Administratorrechten für Intune](users-add.md).

11. Wählen Sie im Navigationsbereich **Gruppen** aus, um Details zu in Intune inbegriffenen Azure AD-Gruppen (Azure Active Directory) zu erhalten. Intune-Administratoren verwenden Gruppen, um Geräte und Benutzer zu verwalten.

    ![Screenshot: „Gruppen“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-11.png)

    > [!TIP]
    > Wenn Sie im Azure-Portal zuvor bereits Intune verwendet haben, befanden sich die oben aufgeführten Details im Azure-Portal, indem Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) angemeldet und **Gruppen** ausgewählt haben.

    Sie können Gruppen so einrichten, dass sie den Anforderungen Ihrer Organisation entsprechen. Sie können Gruppen erstellen, um Benutzer oder Geräte nach geografischem Standort, Abteilung oder Hardwareeigenschaften zu organisieren. Sie können Gruppen zur bedarfsgerechten Verwaltung von Aufgaben verwenden. So können Sie beispielsweise Richtlinien für viele Benutzer festlegen oder Apps für mehrere Geräte bereitstellen. Weitere Informationen zu Gruppen finden Sie unter [Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten](../groups-add.md).

12. Wählen Sie im Navigationsbereich **Mandantenverwaltung** aus, um Details zu Ihrem Intune-Mandanten zu erhalten.

    > [!TIP]
    > Wenn Sie im Azure-Portal zuvor bereits Intune verwendet haben, befanden sich die oben aufgeführten Details im Azure-Portal, indem Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) angemeldet und **Mandantenstatus** ausgewählt haben.

    Der Bereich **Tenant – Tenant status** (Mandant – Mandantenstatus) enthält Registerkarten für **Mandantendetails**, für den **Connectorstatus** und für das **Dashboard zur Dienstintegrität**. Wenn Probleme mit Ihrem Mandanten oder Intune vorliegen, finden Sie in diesem Bereich weitere Details. 

    ![Screenshot: „Mandantenstatus“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-12.png)

    Weitere Informationen finden Sie unter [Seite des Intune-Mandantenstatus](../tenant-status.md).

13. Wählen Sie im Navigationsbereich **Problembehandlung + Support** > **Problembehandlung** aus, um Statusdetails zu einem bestimmten Benutzer zu überprüfen. 

    > [!TIP]
    > Wenn Sie im Azure-Portal zuvor bereits Intune verwendet haben, befanden sich die oben aufgeführten Details im Azure-Portal, indem Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) angemeldet und **Problembehandlung** ausgewählt haben.

    In der Dropdownliste **Zuweisungen** können Sie die Zielzuweisungen von Client-Apps, Richtlinien, Updateringen und Registrierungsbeschränkungen anzeigen und daraus auswählen. Zusätzlich enthält dieser Bereich Gerätedetails, App-Schutzstatus und Registrierungsfehler für einen bestimmten Benutzer.

    ![Screenshot: „Problembehandlung“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-13.png)

    Weitere Informationen zur Problembehandlung in Intune finden Sie unter [Verwenden des Problembehandlungsportals zur Unterstützung von Benutzern Ihres Unternehmens](../help-desk-operators.md).

14. Wählen Sie aus dem Navigationsbereich **Problembehandlung + Support** > **Hilfe und Support** aus, um Hilfe anzufordern. 

    > [!TIP]
    > Wenn Sie im Azure-Portal zuvor bereits Intune verwendet haben, befanden sich die oben aufgeführten Details im Azure-Portal, indem Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) angemeldet und **Hilfe und Support** ausgewählt haben.

    Als IT-Administrator können Sie die Option **Hilfe und Support** verwenden, um Problembehebungen zu durchsuchen und ein Onlinesupportticket für Intune einzureichen. 

    ![Screenshot: „Hilfe und Support“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-14.png)

    Damit Sie ein Supportticket erstellen können, muss Ihrem Konto eine Administratorrolle in Azure Active Directory zugewiesen sein. Zu den Administratorrollen zählen **Intune-Administrator**, **Globaler Administrator** und **Dienstadministrator**. 

    Weitere Informationen finden Sie unter [Anfordern von Support für Microsoft Intune](../get-support.md).

15. Wählen Sie im Navigationsbereich **Problembehandlung + Support** > **Geführte Szenarios** aus, um verfügbare geführte Szenarios in Intune anzuzeigen. 

    Ein geführtes Szenario beschreibt eine angepasste Reihe von Schritten für einen End-to-End-Anwendungsfall. Gängige Szenarios basieren auf der Rolle eines Administrators, Benutzers oder Geräts in Ihrer Organisation. Diese Rollen erfordern in der Regel eine Sammlung sorgfältig orchestrierter Profile, Einstellungen, Anwendungen und Sicherheitskontrollen, um die beste Benutzererfahrung und Sicherheit bereitzustellen.

    Wenn Sie nicht mit allen Schritten und Ressourcen vertraut sind, die zum Implementieren eines bestimmten Intune-Szenarios benötigt werden, können Sie geführte Szenarios als Ausgangspunkt verwenden. 

    ![Screenshot: „Geführte Szenarios“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-15.png)

    Weitere Informationen über geführte Szenarios finden Sie unter [Übersicht über geführte Szenarios in Intune](~/fundamentals/guided-scenarios-overview.md).

## <a name="configure-the-microsoft-endpoint-manager-admin-center"></a>Konfigurieren des Microsoft Endpoint Manager Admin Centers

Mit Azure können Sie die Ansicht des Portals nach Belieben konfigurieren.

### <a name="change-the-dashboard"></a>Ändern des Dashboards

Im **Dashboard** können Sie allgemeine Details zu den Geräten und Client-Apps in Ihrem Intune-Mandanten anzeigen. Dashboards bieten Ihnen die Möglichkeit, eine fokussierte und übersichtliche Ansicht im Microsoft Endpoint Manager Admin Center zu erstellen. Verwenden Sie Dashboards als Arbeitsbereich, in dem Sie schnell Aufgaben für tägliche Vorgänge starten und Ressourcen überwachen können. Erstellen Sie beispielsweise benutzerdefinierte Dashboards basierend auf Projekten, Aufgaben oder Benutzerrollen. Das Microsoft Endpoint Manager Admin Center enthält ein Standarddashboard als Startpunkt. Sie können das Standarddashboard bearbeiten, zusätzliche Dashboards erstellen und anpassen sowie Dashboards veröffentlichen und freigeben, um sie anderen Benutzern zur Verfügung zu stellen. 

   ![Screenshot: „Dashboard“ des Microsoft Endpoint Manager Admin Centers](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-16.png)

Klicken Sie auf **Bearbeiten**, um Ihr aktuelles Dashboard zu ändern. Wenn Sie das Standarddashboard nicht ändern möchten, können Sie auch ein **neues Dashboard** erstellen. Beim Erstellen eines neuen Dashboards beginnen Sie mit einem leeren, privaten Dashboard mit dem **Kachelkatalog**, mit dem Sie Kacheln hinzufügen oder neu arrangieren können. Sie können Kacheln nach Kategorie oder Ressourcentyp suchen. Sie können auch nach bestimmten Kacheln suchen. Wählen Sie **My Dashboard** (Mein Dashboard) aus, um eins Ihrer vorhandenen benutzerdefinierten Dashboards auszuwählen.

### <a name="change-the-portal-settings"></a>Ändern der Portaleinstellungen

Sie können das Microsoft Endpoint Manager Admin Center anpassen, indem Sie die Standardansicht, das Design, den Zeitraum des Zeitlimits für Anmeldeinformationen sowie Sprach- und Regionseinstellungen auswählen.

   <img alt="Screenshot of the Microsoft Endpoint Manager admin center - Portal settings" src="./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-17.png" width="250">

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie schnell in Microsoft Intune einsteigen möchten, sollten Sie die Intune-Schnellstarts abschließen. Hierfür müssen Sie zunächst ein kostenloses Intune-Konto erstellen.

> [!div class="nextstepaction"]
> [Schnellstart: Testen Sie Microsoft Intune kostenlos](free-trial-sign-up.md)
