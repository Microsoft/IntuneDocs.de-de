---
title: Anfordern von Support für Microsoft Intune
titleSuffix: Microsoft Intune
description: Erhalten Sie online und telefonisch Support für kostenpflichtige Abonnements und Testabonnements von Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: srik
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5aca7dbae7a74af399bcbf21aec1dd9dd2d1e851
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390751"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Anfordern von Support für Microsoft Intune

Microsoft bietet für Microsoft Intune Unterstützung bei allgemeinen technischen Fragen, der Vertriebsvorbereitung sowie bei Fragen zu Rechnungen und Abonnements. Der Support ist für kostenpflichtige Abonnements und für Testabonnements online und telefonisch verfügbar. Der technische Onlinesupport ist nur auf Englisch und Japanisch verfügbar. Der telefonische Support und der Support zu Abrechnungen sind in zusätzlichen Sprachen verfügbar.

Als Intune-Administrator können Sie die Option **Hilfe und Support** verwenden, um ein Onlinesupportticket für Intune über das Azure-Portal einzureichen. Damit Sie einen Supportfall erstellen und verwalten können, muss Ihr Konto eine Azure Active Directory-Rolle (Azure AD) besitzen, die die *Aktion* **microsoft.office365.supportTickets** enthält. Weitere Informationen zu Azure AD-Rollen und -Berechtigungen, die zum Erstellen eines Supporttickets erforderlich sind, finden Sie unter [Berechtigungen der Administratorrolle in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).

>[!IMPORTANT]
> Wenden Sie sich für den technischen Support für Drittanbieterprodukte, die mit Intune eingesetzt werden können (z.B. Saaswedo, Cisco oder Lookout), zuerst an den Lieferanten des Produkts. Bevor Sie beim Intune-Support eine Anforderung stellen, sollten Sie sicherstellen, dass Sie das andere Produkt richtig konfiguriert haben.
>
> Weitere Informationen zur Problembehandlung im Zusammenhang mit Microsoft Intune finden Sie im [Abschnitt zur Problembehandlung](help-desk-operators.md) in der Intune-Dokumentation.


## <a name="help-and-support-experience"></a>Benutzeroberfläche für Hilfe und Support

Die Benutzeroberfläche für Hilfe und Support für Intune ist über das [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) und über alle Blätter (oder Seiten) unter Intune im Azure-Portal verfügbar.

Die Benutzeroberfläche *Hilfe und Support* ähnelt derjenigen im [Microsoft 365 Admin Center](https://admin.microsoft.com/) und ersetzt die bisherige Benutzeroberfläche *Hilfe und Support*, die aber für andere Dienste in Azure beibehalten wird.

> [!TIP]
> Ab dem 18. November 2019 wird eine aktualisierte und optimierte konsoleninterne Benutzeroberfläche für Hilfe und Support an die Mandanten verteilt. Wenn diese neue Benutzeroberfläche noch nicht für Sie verfügbar ist, wird sie in Kürze verfügbar sein.

### <a name="options-to-access-help-and-support"></a>Optionen für den Zugriff auf Hilfe und Support

Wenn Sie einen neu erstellten Mandanten für Intune verwenden, kann *Hilfe und Support* nicht geöffnet werden, und die folgende Meldung wird zurückgegeben:

- *Es ist ein unbekanntes Problem aufgetreten. Aktualisieren Sie die Seite. Wenn das Problem weiterhin besteht, erstellen Sie einen Fall über das [M365 Admin Center](https://admin.microsoft.com), und verweisen Sie auf die angegebene Sitzungs-ID.*

Die Fehlerdetails enthalten eine *Sitzungs-ID*, *Erweiterungsdetails* usw. 
 
Dieses Problem tritt auf, wenn Sie Ihr neues Mandantenkonto noch nicht über das **M365 Admin Center** auf https://admin.microsoft.com oder das **Office 365-Portal** unter https://portal.office.com authentifiziert haben. Wählen Sie zur Lösung des Problems den Link für das *M365 Admin Center* in der Meldung aus, oder rufen Sie https://portal.office.com auf, und melden Sie sich an. Nach der Authentifizierung bei einer der beiden Websites ist *Hilfe und Support* für Intune verfügbar.


**Zugriff auf Hilfe und Support:**

- **Im Azure-Portal**

  - Wählen Sie **Hilfe und Support** auf Intune-Blätter oder -Seiten aus.

  > [!NOTE]  
  > Wenn Ihre Intune-Instanz in der privaten Cloud für Regierungsbehörden – auch als Sovereign Cloud bezeichnet, Beispiel: Azure Government – gehostet wird, finden Sie weitere Informationen weiter unten in diesem Artikel unter [Intune-Support für die private Cloud für Regierungsbehörden](#intune-support-for-private-cloud-for-government). Die Intune-Benutzeroberfläche *Hilfe und Support* wird für die private Cloud für Regierungsbehörden erst nächstes Jahr verfügbar sein.

- **Aus dem Microsoft Endpoint Manager Admin Center**
  - Wählen Sie zunächst einen Featurebereich für Intune und dann die Option **Hilfe und Support** aus.
  - Wählen Sie von einem beliebigen Knoten im Microsoft Endpoint Manager Admin Center das **?** - Symbol in der oberen rechten Ecke des Portals, und verwenden Sie dann die Dropdownliste, um den Dienst auszuwählen, für den Sie Hilfe benötigen. Das **?** - Symbol im Microsoft Endpoint Manager Admin Center unterstützt eine Vielzahl von Diensten, und Sie müssen den bestimmten Dienst auswählen, für den Sie Hilfe benötigen.  

    ![Dienst auswählen](./media/get-support/select-a-service.png)

    Nach der Auswahl eines Diensts wird die *Hilfe und Support*-Seite dafür angezeigt, auf der Sie Details angeben können, um zu einem bestimmten Problem [Lösungen zu finden](#find-solutions).

    Wenn die Suchergebnisse nicht Ihren Erwartungen für den Dienst entsprechen, überprüfen Sie, ob der richtige Dienst ausgewählt wurde. Der ausgewählte Dienst wird direkt hinter *Hilfe und Support* angezeigt.  Wenn nicht der richtige Dienst ausgewählt wurde, klicken Sie auf *Dienst auswählen*, um zur Dropdownliste für die Dienstauswahl zurückzukehren.

    ![Dienst bestätigen](./media/get-support/confirm-your-service-selection.png)

###  <a name="the-support-experience"></a>Die Benutzeroberfläche für Support

  Wenn Sie Hilfe und Support öffnen, wird im Portal das **Benötigen Sie Hilfe?** -Fenster angezeigt:

  ![Anzeigen des „Benötigen Sie Hilfe?“-Fensters](./media/get-support/need-help.png)

  In der linken oberen Ecke gibt es drei Symbole, die Sie auswählen können, um unterschiedliche Bereiche des *Benötigen Sie Hilfe?* -Fensters zu öffnen. Der Bereich, den Sie anzeigen, wird durch die Unterstreichung gekennzeichnet.

  Kunden mit einem **Premier Support**- oder **Unified Support**-Vertrag haben [zusätzliche Optionen](#premier-and-unified-support-customers), um Support zu erhalten, und sehen ein Banner in *Benötigen Sie Hilfe?* , das der folgenden Abbildung ähnelt: ![Premier-Banner](./media/get-support/premier-banner.png)

  *Benötigen Sie Hilfe?* öffnet den Bereich *Lösungen suchen*. Wenn bei Ihnen jedoch ein aktiver Supportfall vorliegt, öffnet das Fenster den Bereich *Serviceanforderungen*, in dem Sie Details zu Ihren aktiven und geschlossenen Supportfällen anzeigen können.

#### <a name="find-solutions"></a>Lösungen suchen

![Auswählen des Bereichs „Lösungen suchen“](./media/get-support/find-solutions.png)

Geben Sie im Bereich *Lösungen suchen* Details zu einem Problem im angegebenen Textfeld an. Basierend auf dem Text, den Sie zu einem Problem bereitstellen, füllt sich der Bereich mit Erkenntnissen, die mögliche Übereinstimmungen sind. Sie erhalten auch Links zu empfohlenen Artikeln, die Ihnen helfen könnten, das Problem zu beheben.

Wenn für die Details, die Sie beschreiben, eine starke Entsprechung gefunden wird, können Tipps zur Problembehandlung direkt im *Benötigen Sie Hilfe?* -Fenster angezeigt werden.

Beispielsweise könnten Sie **Fehler bei der Kennwortsynchronisierung** eingeben. Die Ergebnisse enthalten direkt im Bereich Anleitungen zur Problembehandlung und Links zu empfohlenen Artikeln in unserer Dokumentationsbibliothek.

![Anzeigen von Erkenntnissen zur Problembehandlung](./media/get-support/troubleshooting-insights.png)

#### <a name="contact-support"></a>Kontaktieren Sie den Support.

![Auswählen des „Support kontaktieren“-Bereichs](./media/get-support/contact-support.png)

Im Bereich *Support kontaktieren* können Sie eine Unterstützungsanforderung einreichen. Dieser Bereich ist verfügbar, nachdem Sie einige grundlegende Schlüsselwörter im Bereich *Lösungen suchen* bereitgestellt haben.

Wenn Sie Unterstützung anfordern, geben Sie eine möglichst detaillierte Beschreibung des Problems an.  Nachdem Sie Ihre Telefonnummer und Ihre E-Mail-Kontaktinformationen bestätigt haben, wählen Sie die gewünschte Kontaktmethode aus. Das Fenster zeigt eine Antwortzeit für jede Kontaktmethode an, die Sie darüber informiert, wann Sie erwarten können, kontaktiert zu werden. Fügen Sie vor dem Übermitteln der Anforderung Dateien wie Protokolle oder Screenshots an, die Detailinformationen zum Problem liefern können.

![„Support kontaktieren“-Formular](./media/get-support/contact-support-form.png)

Nachdem Sie die erforderlichen Informationen eingetragen haben, wählen Sie **Kontakt mit mir aufnehmen**  aus, um die Anforderung zu übermitteln.

#### <a name="service-requests"></a>Serviceanforderungen

![Auswählen des Bereichs „Serviceanforderungen“](./media/get-support/service-requests.png)

Im Bereich *Serviceanforderungen* wird der Verlauf Ihres Falls angezeigt. Aktive Fälle befinden sich am Anfang der Liste, und abgeschlossene Probleme sind auch zur Einsicht verfügbar.

![Anzeigen Ihrer Serviceanforderungenliste](./media/get-support/service-requests-pane.png)

Wenn Sie eine aktive Supportfallnummer haben, können Sie sie hier eingeben, um zu diesem Problem zu wechseln, oder Sie können einen Vorfall aus der Liste der aktiven und geschlossenen Vorfälle auswählen, um weitere Informationen dazu anzuzeigen.

Wenn Sie die Details eines Vorfalls angezeigt haben, wählen Sie den Pfeil nach links aus, der am oberen Rand des Serviceanforderungenfensters direkt oberhalb der drei *Benötigen Sie Hilfe?* -Bereichssymbole angezeigt wird. Mit dem Zurück-Pfeil kehren Sie zur Anzeige der Liste der von Ihnen geöffneten Supportfälle zurück.

#### <a name="premier-and-unified-support-customers"></a>Premier Support- und Unified Support-Kunden

Als Kunde mit einem **Premier Support**- oder **Unified Support**-Vertrag können Sie einen Schweregrad für Ihr Problem angeben und einen Supportrückruf für eine bestimmte Uhrzeit und einen bestimmten Tag planen. Diese Optionen sind verfügbar, wenn Sie ein neues Problem öffnen oder einreichen, und wenn Sie einen aktiven Supportfall bearbeiten.

**Schweregrad**: Die Optionen zum Angeben des Schweregrads eines Problems sind von Ihrem Supportvertrag abhängig:

- *Premier*: Schweregrad A, B oder C
- *Unified*: Kritisch oder nicht kritisch

Wenn Sie für ein Problem entweder Schweregrad **A** oder **Kritisch** auswählen, gilt dies als Telefonsupportfall, der die schnellste Möglichkeit bietet, Support zu erhalten.

**Rückrufzeitplan**: Sie können einen Rückruf an einem bestimmten Tag und zu einer bestimmten Uhrzeit anfordern.

## <a name="azure-help--support-experience"></a>Azure-Benutzeroberfläche für Hilfe und Support

Sie können nicht mehr auf die Azure-Benutzeroberfläche *Hilfe und Support* zugreifen, um Unterstützung für Intune zu erhalten, es sei denn, Ihr Abonnement befindet sich in einer privaten Cloud für Regierungsbehörden.
Wenn Ihre Intune-Instanz nicht in einer privaten Cloud für Regierungsbehörden ausgeführt wird, werden Sie beim Navigieren zur Azure-Benutzeroberfläche *Hilfe und Support* zur Intune-Benutzeroberfläche *Hilfe und Support* umgeleitet, wo Sie Supportincidents erstellen und verwalten können:

Wenn Sie die Option **Hilfe und Support** im linken Navigationsbereich oder das **?** - Option zum Öffnen des Bereichs *Hilfe* verwenden und dann auf **Hilfe und Support** klicken, öffnen Sie die Azure-Seite *Hilfe und Support*. 


Klicken Sie auf dieser Seite auf **+ Neue Supportanfrage**, um die Registerkarte *Grundeinstellungen* der Seite *Hilfe und Support + Neue Supportanfrage* zu öffnen.

![Hilfe und Support](./media/get-support/help-plus-support.png)

Gehen Sie auf dieser Seite wie folgt vor:

- Wählen Sie für *Problemtyp* die Option **Technisch** aus.
- Wählen Sie für *Dienst* die Option **Microsoft Intune** aus.

  Daraufhin wird ein Link angezeigt, mit dem Sie zur [Intune-Seite für Hilfe und Support](https://aka.ms/intunehelpsupport) umgeleitet werden.
  
  ![Neue Supportanfrage](./media/get-support/new-request.png)


## <a name="intune-support-for-private-cloud-for-government"></a>Intune-Support für die private Cloud für Regierungsbehörden

Wenn Ihr Intune-Abonnement in der privaten Cloud für Regierungsbehörden – auch als Sovereign Cloud bezeichnet, Beispiel: Azure Government – gehostet wird, haben Sie noch keinen Zugriff auf die neuere Intune-Benutzeroberfläche für Hilfe und Support.  Verwenden Sie stattdessen die folgenden Informationen, um Support für Intune zu erhalten.

### <a name="create-an-online-support-ticket"></a>Erstellen eines Onlinesupporttickets

>[!IMPORTANT]
> Da der Bereich *Hilfe und Support* in ein neues System verlagert wird, das für die private Cloud für Regierungsbehörden noch nicht verfügbar ist, identifiziert das Portal beim Erstellen eines Supportincidents einen Supportfall, der eine 15-stellige Identifikationsnummer verwendet. Beim Erstellen des Falls mit 15-stelliger Nummer wird eine Spiegelversion dieses Falls erstellt, die vom Microsoft-Support verwendet wird. Dieser gespiegelte Fall wird in einem neuen Supportsystem erstellt, verwendet eine 8-stellige Fall-ID und wird von Supportdiensten zum Nachverfolgen der ausgeführten Arbeiten und der erfolgten Kommunikation für Ihren Supportincident verwendet. Kurz nach der Erstellung der 15-stelligen Fallnummer erhalten Sie eine E-Mail mit der 8-stelligen Nummer des gespiegelten Supportfalls, die von den Supportdiensten verwendet wird.
>
> Die Supportmitarbeiter arbeiten und kommunizieren mit der 8-stelligen Supportfallnummer und verwenden nur diese zum Protokollieren der Kommunikation und zum Nachverfolgen des Incidentstatus. Daher erhalten Sie E-Mail-Updates mit dieser 8-stelligen Supportfallnummer, die zum Aufzeichnen der Bearbeitung Ihres Falls dienen. Im Supportincident mit der 15-stelligen Nummer werden keine Details protokolliert. Wenn der Support beendet und der 8-stellige Supportfall abgeschlossen ist, wird dieser Status in dem 15-stelligen Supportfall gespiegelt, den Sie im Azure-Portal anzeigen können.  Für den 15-stelligen Supportfall sind keine weiteren Updates oder Statusänderungen zu erwarten.
>
> Wenn der Verlagerung der Supporttools später in diesem Jahr abgeschlossen sein wird, wird die Supportoberfläche, die Intune in der Government Cloud gehostet hat, der standardmäßigen *Hilfe und Support*-Benutzeroberfläche entsprechen, die derzeit für in der öffentlichen Cloud gehostete Intune-Abonnements verfügbar ist.

1. Melden Sie sich im Azure-Portal (<https://portal.azure.us>) mit Ihren Intune-Administratoranmeldeinformationen an, und wählen Sie das Symbol **?** aus. in der oberen rechten Ecke des Portals aus, und wählen Sie dann **Hilfe und Support** aus, um zur Seite [Azure Hilfe und Support](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview) zu gelangen.

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
   > Kunden der privaten Cloud für Regierungsbehörden können nur die 15-stellige Supportnummer und den Incidentstatus anzeigen. Sämtliche Kommunikation zum Fall sowie die Aufzeichnungen der erledigten Arbeiten sowie mögliche Warnungen werden per E-Mail gesendet und geben die 8-stellige Supportfallnummer an, die als Spiegel des in der Intune-Konsole eröffneten Supportfalls erstellt wird.

## <a name="additional-resources"></a>Zusätzliche Ressourcen  

- [Support für Abrechnung und Abonnementverwaltung](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Volumenlizenzierung](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Problembehandlung bei Intune](help-desk-operators.md)
