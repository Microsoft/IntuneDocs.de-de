---
title: Anfordern von Support für Microsoft Intune
titleSuffix: Microsoft Intune
description: Erhalten Sie online und telefonisch Support für kostenpflichtige Abonnements und Testabonnements von Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c4d40d3f15fe23511f3f15f7c13181a0fa72f6b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726517"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Anfordern von Support für Microsoft Intune  

[!INCLUDE [azure_portal](../../intune-classic/includes/note-for-both-portals.md)]  
  
Microsoft bietet für Microsoft Intune Unterstützung bei allgemeinen technischen Fragen, der Vertriebsvorbereitung sowie bei Fragen zu Rechnungen und Abonnements. Der Support ist für kostenpflichtige Abonnements und für Testabonnements online und telefonisch verfügbar. Der technische Onlinesupport ist nur auf Englisch und Japanisch verfügbar. Der telefonische Support und der Support zu Abrechnungen sind in zusätzlichen Sprachen verfügbar.

Als Intune-Administrator können Sie die Option **Hilfe und Support** verwenden, um ein Onlinesupportticket für Intune über das Azure-Portal einzureichen. Damit Sie einen Supportincident erstellen und verwalten können, muss Ihr Konto eine Azure Active Directory-Rolle (Azure AD) besitzen, die die *Aktion* **microsoft.office365.supportTickets/tickets/manage** enthält. Weitere Informationen zu Azure AD-Rollen und -Berechtigungen, die zum Erstellen eines Supporttickets erforderlich sind, finden Sie unter [Berechtigungen der Administratorrolle in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).  

>[!IMPORTANT]  
> Wenden Sie sich für den technischen Support für Drittanbieterprodukte, die mit Intune eingesetzt werden können (z.B. Saaswedo, Cisco oder Lookout), zuerst an den Lieferanten des Produkts. Bevor Sie beim Intune-Support eine Anforderung stellen, sollten Sie sicherstellen, dass Sie das andere Produkt richtig konfiguriert haben.
>
> Weitere Informationen zur Problembehandlung im Zusammenhang mit Microsoft Intune finden Sie im [Abschnitt zur Problembehandlung](help-desk-operators.md) in der Intune-Dokumentation.

## <a name="known-issues-for-creating-support-incidents"></a>Bekannte Probleme beim Erstellen von Supportincidents  

Wenn Ihr Konto über die erforderlichen Berechtigungen verfügt, aber nicht auf „Hilfe und Support“ zugreifen kann oder keine Supportanfrage erstellen oder bearbeiten kann, sehen Sie sich die folgenden bekannten Probleme und entsprechenden Lösungen an:  
- Veraltetes Benutzertoken für Ihr Konto. Sie können dieses Problem beheben, indem Sie sich von allen aktiven Konsolensitzungen abmelden, dann erneut anmelden und dann versuchen, eine Supportanfrage zu erstellen oder zu bearbeiten. 
- Mehrere aktive Sitzungen. Wenn Sie mit mehr als einem Benutzer oder mehr als einer Sitzung angemeldet sind, melden Sie sich von allen Konsolen außer einer ab. Versuchen Sie dann, mit einer einzigen aktiven Sitzung eine Supportanfrage zu erstellen oder zu bearbeiten.

Weitere Aktionen, die möglicherweise erforderlich sind, um Zugriffsprobleme zu beheben:
- Löschen Sie alle Cookies in aktiven Browsersitzungen, und versuchen Sie danach erneut, eine Supportanfrage zu erstellen oder zu bearbeiten.
- Verwenden Sie eine InPrivate-Browsersitzung, um sich bei Intune anzumelden, und versuchen Sie danach erneut, eine Supportanfrage zu erstellen oder zu bearbeiten.  

Wenn Sie die oben aufgeführten Punkte beachtet haben, aber dennoch nicht keine Anfragen erstellen/bearbeiten können, navigieren Sie zum [Microsoft 365 Admin Center](https://admin.microsoft.com), und erstellen Sie dort ein Supportticket. Wir arbeiten derzeit an einer Problembehebung, die im Spätsommer zur Verfügung stehen soll.  

## <a name="help-and-support-experience"></a>Benutzeroberfläche für Hilfe und Support  

Die Benutzeroberfläche für Hilfe und Support für Intune ist über das [Microsoft 365-Portal für die Geräteverwaltung](https://devicemanagement.microsoft.com) und über alle Blätter (oder Seiten) unter Intune im Azure-Portal verfügbar. 

![Blätter „Intune“](./media/get-support/intune-blades.png)


Die Benutzeroberfläche *Hilfe und Support* ähnelt derjenigen im [Microsoft 365 Admin Center](https://admin.microsoft.com/) und ersetzt die bisherige Benutzeroberfläche *Hilfe und Support*, die aber für andere Dienste in Azure beibehalten wird. 

Sie können über die folgenden Optionen auf „Hilfe und Support“ zugreifen:  
- **Im Dashboard für die Geräteverwaltung:**
  - Wählen Sie zunächst einen Featurebereich für Intune und dann die Option **Hilfe und Support** aus.
  - Klicken Sie in einem beliebigen Knoten im Geräteverwaltungsportal auf das **?** - Symbol in der oberen rechten Ecke des Portals, und verwenden Sie dann die Dropdownliste, um den Dienst auszuwählen, für den Sie Hilfe benötigen. Das **?** - Symbol im Geräteverwaltungsportal unterstützt eine Vielzahl von Diensten, und Sie müssen den Dienst auswählen, für den Sie Hilfe benötigen.  

    ![Dienst auswählen](./media/get-support/select-a-service.png)

    Nach der Auswahl eines Diensts wird die *Hilfe und Support*-Seite für diesen angezeigt, auf der Sie [Details angeben](#specify-details-about-an-issue) können, um das Problem zu beschreiben, für das Sie Hilfe benötigen.  

    Wenn die Suchergebnisse nicht Ihren Erwartungen für den Dienst entsprechen, überprüfen Sie, ob der richtige Dienst ausgewählt wurde. Der ausgewählte Dienst wird direkt hinter *Hilfe und Support* angezeigt.  Wenn nicht der richtige Dienst ausgewählt wurde, klicken Sie auf *Dienst auswählen*, um zur Dropdownliste für die Dienstauswahl zurückzukehren.   

    ![Dienst bestätigen](./media/get-support/confirm-your-service-selection.png) 


- **Im Azure-Portal**:
  - Wählen Sie **Hilfe und Support** auf einer der Intune-Blätter oder -Seiten aus.

  Wenn Sie im Azure-Portal das **?** - Symbol in der oberen rechten Ecke oder *Hilfe und Support* im linken Navigationsbereich auswählen, wird die Seite **Hilfe und Support** für Azure geöffnet. Auf der Seite *Hilfe und Support* für Azure können Sie nicht direkt einen Intune-Supportincident erstellen, aber Sie können durch folgende Aktionen zur Intune-Seite *Hilfe und Support* gelangen: 
  1. Wählen Sie „Neue Supportanfrage“ aus.
  2. Geben Sie „Technisch“ als Issuetyp an.
  3. Geben Sie „Microsoft Intune“ als Dienst an.
  4. Wählen Sie den Link zur Intune-Seite „Hilfe und Support“ aus.

> [!NOTE]  
> Wenn Ihre Intune-Instanz in der Government Compute Cloud (GCC) – auch als Sovereign Cloud bezeichnet, Beispiel: Azure Government – gehostet wird, finden Sie weitere Informationen weiter unten in diesem Artikel unter „Intune-Support für die Government Compute Cloud“. Die Intune-Benutzeroberfläche *Hilfe und Support* wird erst zu einem späteren Zeitpunkt in diesem Jahr verfügbar sein. 


Wenn Sie *Hilfe und Support* öffnen, richtet sich die Ansicht im Portal danach, ob aktive Supportincidents vorhanden sind. Wenn Sie über Premier Support verfügen, werden einige zusätzliche Elemente und Optionen angezeigt:
- **Keine aktiven Supportincidents**: Die Seite **Benötigen Sie Hilfe?** wird angezeigt, wie in der folgenden Abbildung des Geräteverwaltungsdashboards zu sehen ist.  
- **Aktive Supportincidents**: Die Seite [Supporttickets](#view-support-cases) wird mit einer Liste Ihrer aktiven Incidents angezeigt.  
- **Premier Support-Vertrag**: Die Benutzeroberflächen sind die gleichen wie bei den beiden oben genannten Optionen. Allerdings sehen Sie auf der Seite „Benötigen Sie Hilfe?“ die folgenden zusätzlichen Optionen: 
  - Hinter dem Seitentitel **Benötigen Sie Hilfe?** wird das Banner für den Premier Support angezeigt:  
    ![Premier Support-Banner](./media/get-support/premier-banner.png)
  - Im Abschnitt **Support erhalten** können Sie die anfängliche Stufe für den **Schweregrad** festlegen, die verwendet wird, wenn Sie telefonisch einen Service Request erstellen.


![Geräteverwaltungsdashboard und die Seite „Benötigen Sie Hilfe?“](./media/get-support/help-support-dashboard.png)

In dieser Ansicht können Sie die folgenden Aktionen durchführen:

1. [Geben Sie Details](#specify-details-about-an-issue) zum spezifischen Problem an, bei dem Sie Hilfe benötigen.  
2. [Zeigen Sie kontextbezogene Hilfe](#view-context-sensitive-help) und zugehörige Lösungen an, die auf den von Ihnen angegebenen Details basieren.  
3. [Erhalten Sie Support](#get-support) per E-Mail oder Telefon.  
4. [Zeigen Sie Supportfälle](#view-support-cases) an, die Sie zuvor mit diesem neuen Workflow geöffnet haben.  

### <a name="specify-details-about-an-issue"></a>Angeben von Details zu einem Problem 

Wenn Sie „Hilfe und Support“ von einem Ort aus öffnen, an dem die neue Benutzeroberfläche unterstützt wird, wird die Seite **Benötigen Sie Hilfe?** geöffnet. Auf dieser Seite können Sie Details zu einem Problem angeben. Während der Eingabe bietet die Konsole gängige Abfragen basierend auf den von Ihnen verwendeten Schlüsselwörtern an. Sie können einen aufgeführte Option auswählen oder Ihre eigene Problembeschreibung eingeben. Wenn Sie eine eigene Beschreibung eingeben, klicken Sie auf **Hilfe anfordern**, um sie zu übermitteln. Nachdem Sie eine Abfrage gesendet haben, gibt die Konsole kontextbezogene Informationen zurück, die zur Lösung des Problems beitragen können.

Im Folgenden finden Sie Beispiele für Problembeschreibungen, die Sie absenden können:
  
- *Ich kann das iOS-Gerät nicht wiederherstellen.*  
- *Ich kann keine Richtlinie für bedingten Zugriff erstellen*.  

![Angeben des Problems auf der Seite „Benötigen Sie Hilfe?“](./media/get-support/describe-the-issue.png)

### <a name="view-context-sensitive-help"></a>Anzeigen von kontextbezogener Hilfe 

Nachdem Sie sich für eine angebotene Auswahl entschieden oder eine eigene Abfrage gestellt haben, werden unter **Lösungen anzeigen** kontextbezogene Ergebnisse angezeigt. Diese Ergebnisse beinhalten sowohl Intune-spezifische Anleitungen zur Selbsthilfe als auch zusätzliche Ergebnisse aus einer auf den Abfragekriterien basierenden Websuche.  
![Anzeige der Ergebnisse](./media/get-support/view-results.png)

### <a name="get-support"></a>Anfordern von Support 

Wenn Sie die Selbsthilfe oder die webbasierte Anleitung bei der Problemlösung nicht weiterbringt, können Sie über die Konsole eine Anfrage für E-Mail- oder Telefonsupport einreichen.  
Wählen Sie auf der Seite **Benötigen Sie Hilfe?** die gewünschte Option aus.  

  > [!NOTE] 
  > Supportanfragen per E-Mail stehen nicht für alle Mandanten zur Verfügung.  

- Geben Sie für eine E-Mail-Anfrage Ihre E-Mail-Adresse an. Optional haben Sie die Möglichkeit, vor dem Senden Anlagen hinzuzufügen. Wählen Sie **Senden** aus, um die Anfrage zu öffnen. 

  ![E-Mail-Anfrage](./media/get-support/email-support.png)
  
- Wenn Sie Telefonsupport wünschen, geben Sie Ihre Telefonnummer an. Optional können Sie auch Ihre E-Mail-Adresse angeben und zu Ihrer Anfrage Anlagen hinzufügen. Wählen Sie „Anrufen“ aus, um die Anfrage zu übermitteln.  



   ![Anfrage für Telefonsupport](./media/get-support/phone-support.png)

**Premier Support**:  
Wenn Sie über einen Premier Support-Vertrag verfügen, stehen Ihnen die gleichen Optionen zum telefonischen Erstellen eines Supportincidents zur Verfügung. Sie können auch den **Schweregrad** für den Supportrückruf angeben und das Supportticket im Rahmen Ihres Vertrags für unternehmenskritischen Support erstellen.  

![Premier Support-Optionen](./media/get-support/premier-phone-support-options.png)


### <a name="view-support-cases"></a>Anzeigen von Supportfällen  

Wählen Sie die Schaltfläche für den Verlauf, um die von Ihnen erstellten Supportanfragen anzuzeigen.  

![Anzeigen von Supportfällen](./media/get-support/view-support-tickets.png)

- Nur die mit dem neuen Workflow geöffneten Supportfälle sind in diesem Workflow sichtbar. Um sie anzuzeigen, wechseln Sie in der Geräteverwaltungskonsole oder über ein Intune-Blatt im Azure-Portal auf die Ansicht „Hilfe und Support“. Für jeden Fall wird eine achtstellige Nummer vergeben. Sie können diese Fälle auch im Microsoft 365 Admin Center einsehen.  

- Fälle, die Sie nicht über die Intune-Benutzeroberfläche für Hilfe und Support geöffnet haben, bleiben unverändert. Um sie anzuzeigen, müssen Sie eine Hilfe- und Support-Ansicht verwenden, die nicht zur Intune-Benutzeroberfläche oder dem Dashboard für die Geräteverwaltung gehört. Diese Fälle erhalten Nummern, die mit **117** oder **118** beginnen und 15 Ziffern umfassen. So zeigen Sie diese an:

    1. Melden Sie sich in Azure (<https://portal.azure.com>) mit Ihren Intune-Administratoranmeldeinformationen an, und wählen Sie das *?* aus. in der oberen rechten Ecke des Portals aus, und wählen Sie dann *Hilfe und Support* aus, um zur Seite [Azure Hilfe und Support](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) zu gelangen.

    2. Auf der Seite **Hilfe und Support** können Sie die Liste der **kürzlich gesendeten Supportanfragen** anzeigen und diese auswählen, um weitere Details anzuzeigen.
 

## <a name="azure-help--support-experience"></a>Azure-Benutzeroberfläche für Hilfe und Support 

Wenn Sie die Option **Hilfe und Support** im linken Navigationsbereich oder das **?** - Symbol in der oberen rechten Ecke des Azure-Portals verwenden, öffnen Sie damit die Azure-Benutzeroberfläche „Hilfe und Support“, die sich von der Intune-Benutzeroberfläche „Hilfe und Support“ unterscheidet.  

Seit April 2019 können Sie nicht mehr auf die Azure-Benutzeroberfläche *Hilfe und Support* zugreifen, um Unterstützung für Intune zu erhalten, es sei denn, Ihr Abonnement befindet sich in der Government Compute Cloud (GCC).  

Wenn Ihre Intune-Instanz nicht in der GCC ausgeführt wird, werden Sie beim Navigieren zur Azure-Benutzeroberfläche *Hilfe und Support* zur Intune-Benutzeroberfläche *Hilfe und Support* umgeleitet, wo Sie Supportincidents erstellen und verwalten können.  


## <a name="intune-support-for-government-compute-cloud"></a>Intune-Support für die Government Compute Cloud  

Wenn Ihr Intune-Abonnement in der Government Compute Cloud (GCC) – auch als Sovereign Cloud bezeichnet, Beispiel: Azure Government – gehostet wird, haben Sie noch keinen Zugriff auf die neuere Intune-Benutzeroberfläche für Hilfe und Support.  Verwenden Sie stattdessen die folgenden Informationen, um Support für Intune zu erhalten. 


### <a name="create-an-online-support-ticket"></a>Erstellen eines Onlinesupporttickets 

>[!IMPORTANT]    
> Da der Bereich *Hilfe und Support* in ein neues System verlagert wird, das für die GCC noch nicht verfügbar ist, identifiziert das Portal beim Erstellen eines Supportincidents einen Supportfall, der eine 15-stellige Identifikationsnummer verwendet. Beim Erstellen des Falls mit 15-stelliger Nummer wird eine Spiegelversion dieses Falls erstellt, die vom Microsoft-Support verwendet wird. Dieser gespiegelte Fall wird in einem neuen Supportsystem erstellt, verwendet eine 8-stellige Fall-ID und wird von Supportdiensten zum Nachverfolgen der ausgeführten Arbeiten und der erfolgten Kommunikation für Ihren Supportincident verwendet. Kurz nach der Erstellung der 15-stelligen Fallnummer erhalten Sie eine E-Mail mit der 8-stelligen Nummer des gespiegelten Supportfalls, die von den Supportdiensten verwendet wird.  
> 
> Die Supportmitarbeiter arbeiten und kommunizieren mit der 8-stelligen Supportfallnummer und verwenden nur diese zum Protokollieren der Kommunikation und zum Nachverfolgen des Incidentstatus. Daher erhalten Sie E-Mail-Updates mit dieser 8-stelligen Supportfallnummer, die zum Aufzeichnen der Bearbeitung Ihres Falls dienen. Im Supportincident mit der 15-stelligen Nummer werden keine Details protokolliert. Wenn der Support beendet und der 8-stellige Supportfall abgeschlossen ist, wird dieser Status in dem 15-stelligen Supportfall gespiegelt, den Sie im Azure-Portal anzeigen können.  Für den 15-stelligen Supportfall sind keine weiteren Updates oder Statusänderungen zu erwarten.  
> 
> Wenn der Verlagerung der Supporttools später in diesem Jahr abgeschlossen sein wird, wird die Supportoberfläche, die Intune in der Government Cloud gehostet hat, der standardmäßigen *Hilfe und Support*-Benutzeroberfläche entsprechen, die derzeit für in der öffentlichen Cloud gehostete Intune-Abonnements verfügbar ist.  


1. Melden Sie sich im Azure-Portal (<https://portal.azure.com>) mit Ihren Intune-Administratoranmeldeinformationen an, und wählen Sie das Symbol **?** aus. in der oberen rechten Ecke des Portals aus, und wählen Sie dann **Hilfe und Support** aus, um zur Seite [Azure Hilfe und Support](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) zu gelangen.

   ![Darstellung des Fragezeichenlinks mit Hervorhebung des Links „Hilfe + Support“](./media/get-support/azure-get-support.png)

2. Wählen Sie auf der Seite **Hilfe und Support** in Azure die Option **Neue Supportanfrage** aus.

   ![Darstellung des hervorgehobenen Links „Neue Supportanfrage“ auf der Seite „Hilfe und Support“](./media/get-support/azure-support-ticket-link.png)

3. Für die meisten technischen Probleme mit Intune wählen Sie auf dem Blatt **Grundlagen** folgende Optionen aus:
   - **Problemtyp**: **Technisch**
   - **Abonnement**: <*Ihr Abonnement*>
   - **Dienst**: **Microsoft Intune**
   - **Problemtyp**: Wählen Sie den Problemtyp im Dropdownmenü aus.
   - **Problemuntertyp**: Wählen Sie den Problemuntertyp im Dropdownmenü aus.
   - **Betreff**: Beschreiben Sie kurz das Problem, bei dem Sie Hilfe benötigen.

   ![Darstellung der Registerkarte „Grundlagen“ auf der Seite „Hilfe und Support“ > „Neue Supportanfrage“](./media/get-support/help-new-support-case-basics.png)

   Klicken Sie auf **Weiter: Lösungen**, um den Vorgang fortzusetzen.
4. Überprüfen Sie auf der Registerkarte **Lösungen** die empfohlenen Schritte, mit denen Sie das Problem möglicherweise lösen können, ohne ein Ticket einreichen zu müssen. Wenn Sie nach dem Überprüfen der Schritte weiterhin eine Supportanfrage erstellen möchten, klicken Sie auf **Weiter: Details**.

   ![Darstellung der Registerkarte „Lösungen“ auf der Seite „Hilfe und Support“ > „Neue Supportanfrage“](./media/get-support/help-new-support-case-solutions.png)
5. Geben Sie auf der Registerkarte **Details** Informationen zum Problem, zur Supportmethode sowie Ihre Kontaktinformationen an, und klicken Sie auf **Weiter: Überprüfen und erstellen**.

   ![Darstellung der Registerkarte „Details“ auf der Seite „Hilfe und Support“ > „Neue Supportanfrage“](./media/get-support/help-new-support-case-details.png)
6. Überprüfen Sie die Informationen auf ihre Richtigkeit, und klicken Sie dann auf **Erstellen**, um die Supportanfrage zu übermitteln.

   ![Darstellung der Registerkarte „Überprüfen und erstellen“ auf der Seite „Neue Supportanfrage“](./media/get-support/help-new-support-case-create.png)

>[!IMPORTANT]
>Wenn Sie eine Frage zur Abrechnung oder zum Abonnement haben, können Sie über das [Microsoft 365 Admin Center](https://admin.microsoft.com/Support/SupportEntry.aspx) eine Anfrage einreichen, um Support zu erhalten.

### <a name="view-support-requests"></a>Anzeigen aller Supportanfragen  

Sie können Ihre Supportanfragen im Azure-Portal anzeigen. Es sind jedoch nur eingeschränkte Informationen verfügbar.  So zeigen Sie Ihre Incidents an: 

1. Melden Sie sich in Azure (<https://portal.azure.com>) mit Ihren Intune-Administratoranmeldeinformationen an, und wählen Sie das **?** aus. in der oberen rechten Ecke des Portals aus, und wählen Sie dann **Hilfe und Support** aus, um zur Seite [Azure Hilfe und Support](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) zu gelangen.

2. Auf der Seite **Hilfe und Support** können Sie die Liste der **kürzlich gesendeten Supportanfragen** anzeigen.

   > [!IMPORTANT]  
   > Government Compute Cloud-Kunden können nur die 15-stellige Supportnummer und den Incidentstatus anzeigen. Sämtliche Kommunikation zum Fall sowie die Aufzeichnungen der erledigten Arbeiten sowie mögliche Warnungen werden per E-Mail gesendet und geben die 8-stellige Supportfallnummer an, die als Spiegel des in der Intune-Konsole eröffneten Supportfalls erstellt wird.   

## <a name="additional-resources"></a>Zusätzliche Ressourcen  

- [Support für Abrechnung und Abonnementverwaltung](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Volumenlizenzierung](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Problembehandlung bei Intune](help-desk-operators.md)
