---
title: Problembehandlung bei häufigen Problemen mit dem InTune Exchange Connector
titleSuffix: Microsoft Intune
description: Beheben Sie häufige Probleme für den lokalen Microsoft InTune Exchange-Connector, und beheben Sie diese.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: de365312a7d293527c3c83fbbd84ab55de41d530
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547677"
---
# <a name="resolve-common-problems-with-the-intune-exchange-connector"></a>Beheben allgemeiner Probleme mit dem InTune Exchange Connector
 
Dieser Artikel hilft dem InTune-Administrator dabei, häufige Probleme beim Betrieb von InTune Exchange Connector zu beheben.

Bevor Sie mit der Problembehandlung beginnen, finden Sie unter Problembehandlung [beim lokalen Exchange-Connector für InTune](troubleshoot-exchange-connector.md) grundlegende Informationen zum Connector. Überprüfen Sie auch häufige Probleme für die Connector-Konfiguration.

## <a name="an-exchange-activesync-device-isnt-discovered-from-exchange"></a>Ein Exchange ActiveSync-Gerät wurde von Exchange nicht ermittelt.

Wenn ein Exchange ActiveSync-Gerät nicht von Exchange ermittelt wird, [Überwachen Sie die Exchange Connector-Aktivität](exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support) , um festzustellen, ob der Exchange-Connector mit dem Exchange-Server synchronisiert wird. Wenn seit dem Hinzufügen des Geräts keine Synchronisierung erfolgt ist, erfassen Sie die Synchronisierungs Protokolle, und fügen Sie Sie an eine Supportanfrage an. Wenn eine vollständige Synchronisierung oder eine schnelle Synchronisierung erfolgreich abgeschlossen wurde, seit das Gerät verknüpft ist, überprüfen Sie die folgenden Probleme:

- Stellen Sie sicher, dass Benutzer über eine InTune-Lizenz verfügen. Andernfalls findet der Exchange Connector keine Geräte.

- Wenn die primäre SMTP-Adresse eines Benutzers sich von seinem Benutzerprinzipalnamen (UPN) in Azure Active Directory (Azure AD) unterscheidet, erkennt der Exchange Connector keine Geräte für diesen Benutzer. Korrigieren Sie die primäre SMTP-Adresse, um das Problem zu beheben.

- Wenn in Ihrer Umgebung Exchange 2010- und Exchange 2013-Postfachserver vorhanden sind, wird empfohlen, den Exchange Connector auf einen Exchange 2013-Clientzugriffsserver (CAS) zu verweisen. Wenn der Exchange Connector für die Kommunikation mit einem Exchange 2010-Clientzugriffsserver eingerichtet ist, erkennt dieser keine Exchange 2013-Geräte von Benutzern.

- Bei Exchange Online Dedicated-Umgebungen müssen Sie den Exchange-Connector während der ersten Installation auf eine Exchange 2013-Zertifizierungsstelle (keine Exchange 2010-Zertifizierungsstelle) in der dedizierten Umgebung verweisen. Der Connector kommuniziert nur mit Exchange 2013-CAS, wenn er PowerShell-Cmdlets ausführt.

## <a name="problems-with-the-notification-email-message"></a>Probleme mit der Benachrichtigungs-e-Mail

Um den bedingten Zugriff für lokale Postfächer auf Geräten zu unterstützen, auf denen Android Knox nicht ausgeführt wird, müssen Sie sicherstellen, dass die Intune-Registrierung über die e-Mail-Nachricht "jetzt starten" beginnt, die der InTune Exchange Connector sendet. Durch das Starten der Registrierung über die Nachricht wird sichergestellt, dass das Gerät eine eindeutige activesyncid auf allen Plattformen (Exchange, Azure AD, InTune) empfängt.

Ein Benutzer erhält möglicherweise die Benachrichtigungs-e-Mail nicht, weil

- Das Benachrichtigungs Konto wurde nicht ordnungsgemäß eingerichtet.
- Fehler bei der Auto Ermittlung für das Benachrichtigungs Konto.
- Fehler bei der Anforderung zum Senden der e-Mail-Nachricht durch die Exchange-Webdienste (EWS).

In den folgenden Abschnitten finden Sie Informationen zur Behandlung von e-Mail-Benachrichtigungen.

### <a name="check-the-notification-account-that-retrieves-autodiscover-settings"></a>Überprüfen Sie das Benachrichtigungs Konto, das die Einstellungen für die automatische Ermittlung

1. Stellen Sie sicher, dass der AutoErmittlungsdienst und die Exchange-Webdienste in den Exchange-Clientzugriffsdiensten konfiguriert sind. Weitere Informationen finden Sie unter [Client Zugriffs Dienste](https://docs.microsoft.com/Exchange/architecture/client-access/client-access) und [autodiscover-Dienst in Exchange Server](https://docs.microsoft.com/Exchange/architecture/client-access/autodiscover?view=exchserver-2019).

2. Vergewissern Sie sich, dass Ihr Benachrichtigungs Konto die folgenden Anforderungen erfüllt:

   - Das Konto verfügt über ein aktives Postfach, das von Ihrem lokalen Exchange-Server gehostet wird.

   - Der Konto-UPN entspricht der SMTP-Adresse.

3. Autodiscover erfordert einen DNS-Server mit einem DNS-Datensatz für **autodiscover.SMTPdomain.com** (z. b. autodiscover.contoso.com), der auf den Exchange-Client Zugriffs Server zeigt. Um nach dem Datensatz zu suchen, geben Sie Ihren FQDN anstelle von *autodiscover.SMTPdomain.com* an, und führen Sie die folgenden Schritte aus:

   1. Geben Sie an einer Eingabeaufforderung *nslookup*ein.

   2. Geben Sie *autodiscover.SMTPdomain.com*ein. Die Ausgabe sollte in etwa wie in der folgenden Abbildung aussehen: ![Nslookup-Ergebnisse](./media/troubleshoot-exchange-connector-common-problems/nslookup-results.png
      )

   Sie können auch den autodiscover-Dienst über das Internet auf https://testconnectivity.microsoft.com testen. Oder testen Sie es von einer lokalen Domäne mithilfe des Microsoft Connectivity Analyzer-Tools. Weitere Informationen finden Sie unter [Microsoft Connectivity Analyzer-Tool](https://docs.microsoft.com/previous-versions/office/exchange-remote-connectivity/jj851141(v=exchg.80)).


### <a name="check-autodiscovery"></a>AutoDiscovery überprüfen

Wenn autodiscover fehlschlägt, führen Sie die folgenden Schritte aus:

1. [Konfigurieren Sie einen gültigen DNS-Datensatz](https://docs.microsoft.com/previous-versions/exchange-server/exchange-150/mt473798(v=exchg.150))für die automatische Ermittlung.

2. Hardcodieren der EWS-URL in der InTune Exchange Connector-Konfigurationsdatei:

   1. Bestimmen Sie die EWS-URL. Die standardmäßige EWS-URL für Exchange ist `https://<mailServerFQDN>/ews/exchange.asmx`, aber Ihre URL kann abweichen. Wenden Sie sich an den Exchange-Administrator, um die richtige URL für Ihre Umgebung zu prüfen.

   2. Bearbeiten Sie die Datei *OnPremisesExchangeConnectorServiceConfiguration.xml*. Standardmäßig befindet sich die Datei unter *%ProgramData%\Microsoft\Windows InTune Exchange Connector* auf dem Computer, auf dem Exchange Connector ausgeführt wird. Öffnen Sie die Datei in einem Text-Editor, und ändern Sie dann die folgende Zeile, um die EWS-URL für Ihre Umgebung widerzuspiegeln: `<ExchangeWebServiceURL>https://<YourExchangeHOST>/EWS/Exchange.asmx</ExchangeWebServiceURL>`

3. Speichern Sie die Datei, und starten Sie dann den Microsoft Intune Exchange Connector neu.

>[!NOTE]
> In dieser Konfiguration wird die automatische Ermittlung von InTune Exchange Connector nicht mehr verwendet. stattdessen wird eine direkte Verbindung mit der EWS-URL hergestellt.

## <a name="next-steps"></a>Nächste Schritte

Hilfe zu bestimmten Fehlern finden Sie unter [Beheben von häufigen Fehlern für den InTune Exchange Connector](troubleshoot-exchange-connector-common-errors.md).

Um Support zu erhalten oder Hilfe von der InTune-Community zu erhalten:

- Weitere Informationen finden Sie [unter Support](../fundamentals/get-support.md) für die Intune-Konsole, um das Problem zu beheben oder eine Supportanfrage bei Microsoft zu eröffnen.
- Veröffentlichen Sie Ihr Problem in den [Microsoft InTune-Foren](https://social.technet.microsoft.com/Forums/home?forum=microsoftintuneprod).