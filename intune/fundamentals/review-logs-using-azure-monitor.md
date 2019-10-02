---
title: Weiterleiten von Protokollen an Azure Monitor mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie Diagnoseeinstellungen, um die Überwachungs- und Betriebsprotokolle in Microsoft Intune zum Azure-Speicherkonto, Event Hubs oder Log Analytics zu senden. Sie können wählen, wie lange Sie die Daten aufbewahren möchten, und können einige geschätzte Kosten für Mandanten unterschiedlicher Größe anzeigen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 99799f695b9398c455f92220c436c7a6c6d76d56
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721850"
---
# <a name="send-log-data-to-storage-event-hubs-or-log-analytics-in-intune-preview"></a>Senden von Daten an den Speicher, an Event Hubs oder Log Analytics in Intune (Vorschauversion)

Microsoft Intune umfasst integrierte Protokolle, die Informationen zu Ihrer Umgebung bereitstellen:

- **Überwachungsprotokolle** zeigen Details zu verschiedenen Ereignissen oder Task an, die in Intune auftreten.
- **Betriebsprotokolle (Vorschauversion)** zeigen Details für Benutzer und Geräte, die sich erfolgreich (oder erfolglos) registriert haben, sowie Informationen zu nicht konformen Geräten an.
- **Betriebsprotokolle für die Gerätekonformität (Vorschauversion)** zeigen einen Organisationsbericht für die Gerätekonformität in Intune und Details zu nicht konformen Geräten an.

Die Protokolle können an Azure Monitor-Dienste gesendet werden, einschließlich Speicherkonten, Event Hubs und Log Analytics. Insbesondere bestehen die folgenden Möglichkeiten:

* Archivieren Sie Intune-Protokolle in einem Azure-Speicherkonto, um Daten beizubehalten, oder archivieren Sie sie für eine festgelegte Zeit.
* Sie können Intune-Protokolle zur Analyse mit beliebten SIEM-Tools (Security Information & Event Management), wie Splunk und QRadar, zu einem Azure Event Hub streamen.
* Integrieren Sie Intune-Protokolle in Ihre eigene benutzerdefinierte Protokolllösungen, indem sie an einen Event Hub streamen.
* Senden Sie Intune-Protokolle an Log Analytics, um ansprechende Visualisierungen, die Überwachung und Warnungen für die verbundenen Daten zu aktivieren.

Diese Funktionen sind Teil der **Diagnoseeinstellungen** in Intune.

Dieser Artikel zeigt Ihnen, wie Sie **Diagnoseeinstellungen** verwenden können, um Protokolldaten an verschiedene Dienste zu senden, und er enthält Beispiele und Kostenschätzungen und beantwortet einige häufige Fragen. Nachdem Sie diese Funktion aktiviert haben, werden Ihre Protokolle an den von Ihnen gewählten Azure Monitor-Dienst weitergeleitet.

## <a name="prerequisites"></a>Voraussetzungen

Für die Nutzung dieser Funktion benötigen Sie:

* Ein Azure-Abonnement: Wenn Sie kein Azure-Abonnement besitzen, können Sie sich für [eine kostenlose Testversion registrieren](https://azure.microsoft.com/free/).
* Eine Microsoft Intune-Umgebung (Mandant) in Azure
* Einen Benutzer, der ein **globaler Administrator** oder **Intune-Dienstadministrator** für den Intune-Mandanten ist.

Je nachdem, wohin Sie die Überwachungsprotokolldaten weiterleiten möchten, benötigen Sie einen der folgenden Dienste:

* Ein [Azure-Speicherkonto](https://docs.microsoft.com/azure/storage/common/storage-account-overview) mit *ListKeys*-Berechtigungen. Es wird empfohlen, dass Sie ein allgemeines Speicherkonto und kein Blob-Speicherkonto verwenden. Informationen zu den Speicherpreisen finden Sie im [Azure Storage-Preisrechner](https://azure.microsoft.com/pricing/calculator/?service=storage). 
* Ein [Azure Event Hubs-Namespace](https://docs.microsoft.com/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace) für die Integration von Drittanbieterlösungen.
* Ein [Azure Log Analytics-Arbeitsbereich](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) zum Senden von Protokolle an Log Analytics.

## <a name="send-logs-to-azure-monitor"></a>Senden von Protokollen an Azure Monitor

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie unter **Überwachung** die Option **Diagnoseeinstellungen**. Aktivieren Sie diese Option beim ersten Öffnen. Fügen Sie andernfalls eine Einstellung hinzu.

    ![Aktivieren der Diagnoseeinstellungen in Intune, um die Protokolle an Azure Monitor zu senden](./media/review-logs-using-azure-monitor/diagnostics-settings-turn-on.png)

3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen Namen für die Diagnoseeinstellungen ein. Diese Einstellung enthält alle von Ihnen eingegebene Eigenschaften. Geben Sie beispielsweise `Route audit logs to storage account` ein.
    - **In ein Speicherkonto archivieren**: Damit werden die Protokolldaten in einem Azure-Speicherkonto gespeichert. Verwenden Sie diese Option, wenn Sie die Daten speichern oder archivieren möchten.

        1. Wählen Sie diese Option > **Konfigurieren** aus. 
        2. Wählen Sie ein vorhandenes Speicherkonto aus der Liste > **OK**.

    - **An einen Event Hub streamen**: Streamt die Protokolle an einen Azure Event Hub. Wenn Sie Ihre Protokolldaten mit Hilfe von SIEM-Tools wie Splunk und QRadar analysieren möchten, wählen Sie diese Option.

        1. Wählen Sie diese Option > **Konfigurieren** aus. 
        2. Wählen Sie aus der Liste einen vorhandenen Event Hub-Namespace und die Richtlinie > **OK**.

    - **An Log Analytics senden**: Sendet die Daten an Azure Log Analytics. Wenn Sie Visualisierung, Überwachung und Benachrichtigung für Ihre Protokolle nutzen möchten, wählen Sie diese Option aus.

        1. Wählen Sie diese Option > **Konfigurieren** aus. 
        2. Erstellen Sie einen neuen Arbeitsbereich, und geben Sie die Details des Arbeitsbereichs ein. Oder wählen Sie einen vorhandenen Arbeitsbereich aus der Liste aus > **OK**.

            IN [Azure Log Analytics-Arbeitsbereich](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) finden Sie weitere Details zu diesen Einstellungen.

    - **LOG** > **AuditLogs**: Wählen Sie diese Option, um die [Intune-Überwachungsprotokolle](../monitor-audit-logs.md) an Ihr Speicherkonto, Ihren Event Hub oder Log Analytics zu senden. Die Überwachungsprotokolle zeigen den Verlauf aller Aufgaben, die eine Änderung in Intune bewirkt haben, z.B. wer die Änderung durchgeführt hat und wann diese erfolgt ist.

      Wenn Sie sich für ein Speicherkonto entscheiden, geben Sie auch an, wie viele Tage Sie die Daten aufbewahren möchten (Vermerkdauer). Um Daten für immer zu behalten, setzen Sie **Vermerkdauer (Tage)**  auf `0` (Null) fest.

    - **LOG** > **OperationalLogs**: Betriebsprotokolle (Vorschau) zeigen den Erfolg oder Misserfolg von Benutzern und Geräten an, die in Intune registriert werden, sowie Informationen zu nicht-konformen Geräten. Wählen Sie diese Option, um die Registrierungsprotokolle an Ihr Speicherkonto, Ihren Event Hub oder Log Analytics zu senden.

      Wenn Sie sich für ein Speicherkonto entscheiden, geben Sie auch an, wie viele Tage Sie die Daten aufbewahren möchten (Vermerkdauer). Um Daten für immer zu behalten, setzen Sie **Vermerkdauer (Tage)**  auf `0` (Null) fest.

      > [!NOTE]
      > Betriebsprotokolle befinden sich noch in der Vorschauversion. Navigieren Sie zu [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback), um uns Feedback einschließlich der in den Betriebsprotokollen enthaltenen Informationen zu geben.

    - **LOG** > **DeviceComplianceOrg**: Die Betriebsprotokolle für die Gerätekonformität (Vorschauversion) zeigen den Organisationsbericht für die Gerätekonformität in Intune und Details zu nicht konformen Geräten an. Wählen Sie diese Option, um die Konformitätsprotokolle an Ihr Speicherkonto, Ihren Event Hub oder Log Analytics zu senden.

      Wenn Sie sich für ein Speicherkonto entscheiden, geben Sie auch an, wie viele Tage Sie die Daten aufbewahren möchten (Vermerkdauer). Um Daten für immer zu behalten, setzen Sie **Vermerkdauer (Tage)**  auf `0` (Null) fest.
 
      > [!NOTE]
      > Die Unternehmensprotokolle für die Gerätekonformität befinden sich in der Vorschauversion. Navigieren Sie zu [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback), um uns Feedback einschließlich der im Bericht enthaltenen Informationen zu geben.

    Wenn Sie fertig sind, sehen Ihre Einstellungen ähnlich aus wie die folgenden Einstellungen: 

    ![Beispielbild, bei dem Intune-Überwachungsprotokolle an ein Azure-Speicherkonto gesendet werden](./media/review-logs-using-azure-monitor/diagnostics-settings-example.png)

4. **Speichern** Sie die Änderungen. Ihre Einstellung wird in der Liste angezeigt. Nach der Erstellung können Sie die Einstellungen ändern. Gehen Sie dazu zu **Einstellung bearbeiten** > **Speichern**.

## <a name="use-audit-logs-throughout-intune"></a>Verwenden von Überwachungsprotokollen in allen Bereichen von Intune

Sie können die Überwachungsprotokolle auch in andere Bereiche von Intune exportieren. Dazu gehören u. a. Registrierung, Konformität, Konfiguration, Geräte und Client-Apps.

So exportieren Sie beispielsweise die Überwachungsprotokolle bei Verwendung von Gerätekonformität:

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie **Gerätekonformität** > **Überwachung** > **Überwachungsprotokolle** aus:

    ![Screenshot: Auswählen der Überwachungsprotokolle, um Intune-Daten an Azure Monitor-Speicher, -Event Hubs oder Analytics zu senden](./media/review-logs-using-azure-monitor/audit-logs-under-monitor-in-compliance.png)

3. Wählen Sie **Einstellungen für das Exportieren von Daten** aus. Wenn die **Diagnoseeinstellungen** nicht aktiviert sind, aktivieren Sie sie. Sie können auch auswählen, wohin die Protokolle gesendet werden sollen. Dies ist in diesem Artikel unter [Senden von Protokollen an Azure Monitor](#send-logs-to-azure-monitor) beschrieben.

## <a name="cost-considerations"></a>Überlegungen zu Kosten

Wenn Sie bereits eine Microsoft Intune-Lizenz besitzen, benötigen Sie ein Azure-Abonnement, um das Speicherkonto und einen Event Hub einzurichten. Das Azure-Abonnement ist in der Regel kostenlos. Aber Sie zahlen für die Nutzung von Azure-Ressourcen, einschließlich des Speicherkonto für die Archivierung und des Event Hubs für das Streaming. Die Menge an Daten und die Kosten hängen von der Größe des Mandanten ab.

### <a name="storage-size-for-activity-logs"></a>Speichergröße für Aktivitätsprotokolle

Jedes Überwachungsprotokollereignis verbraucht ca. 2 KB Datenspeicher. Für einen Mandanten mit 100.000 Benutzern sind etwa 1,5 Millionen Ereignisse pro Tag möglich. Möglicherweise benötigen Sie ca. 3 GB Datenspeicher pro Tag. Da Schreibvorgänge typischerweise in Fünf-Minuten-Batches erfolgen, können Sie mit ca. 9.000 Schreibvorgängen pro Monat rechnen.

Die folgenden Tabellen zeigen eine Kostenschätzung in Abhängigkeit von der Größe des Mandanten. Enthalten ist auch ein universelles v2-Speicherkonto in den USA für mindestens ein Jahr der Datenaufbewahrung. Um eine Schätzung für das Datenvolumen zu erhalten, das Sie für Ihre Protokolle erwarten, verwenden Sie den [Azure Storage-Preisrechner](https://azure.microsoft.com/pricing/details/storage/blobs/).

**Überwachungsprotokoll mit 100.000 Benutzern**

| | |
|---|---|
|Ereignisse pro Tag| 1,5 Millionen|
|Geschätzte Datenvolumen pro Monat| 90 GB|
|Geschätzte Kosten pro Monat (USD)| 1,93 US-Dollar|
|Geschätzte Kosten pro Jahr (USD)| 23,12 US-Dollar|

**Überwachungsprotokoll mit 1.000 Benutzern**

| | |
|---|---|
|Ereignisse pro Tag| 15.000|
|Geschätzte Datenvolumen pro Monat| 900 MB|
|Geschätzte Kosten pro Monat (USD)| 0,02 US-Dollar|
|Geschätzte Kosten pro Jahr (USD)| 0,24 US-Dollar|

### <a name="event-hub-messages-for-activity-logs"></a>Event Hub-Nachrichten für Aktivitätsprotokolle

Ereignisse werden typischerweise in Fünf-Minuten-Intervallen zusammengefasst und als eine einzige Nachricht mit allen Ereignissen innerhalb dieses Zeitraums gesendet. Eine Nachricht im Event Hub hat eine maximale Größe von 256 KB. Wenn die Gesamtgröße aller Nachrichten innerhalb des Zeitrahmens dieses Volumen überschreitet, werden mehrere Nachrichten gesendet.

Beispielsweise treten bei einem großen Mandanten mit mehr als 100.000 Benutzern typischerweise etwa 18 Ereignisse pro Sekunde auf. Dies entspricht 5.400 Ereignissen alle fünf Minuten (300 Sekunden x 18 Ereignisse). Überwachungsprotokolle haben eine Größe von ungefähr 2 KB pro Ereignis. Dies entspricht 10,8 MB an Daten. So werden 43 Nachrichten in diesem Fünf-Minuten-Intervall an den Event Hub gesendet.

Die folgende Tabelle enthält geschätzte monatliche Kosten für einen einfachen Event Hub in den USA, abhängig vom Volumen der Ereignisdaten. Um eine Schätzung für das Datenvolumen zu erhalten, das Sie für Ihre Protokolle erwarten, verwenden Sie den [Event Hub-Preisrechner](https://azure.microsoft.com/pricing/details/event-hubs/).

**Überwachungsprotokoll mit 100.000 Benutzern**

| | |
|---|---|
|Ereignisse pro Sekunde| 18|
|Ereignisse pro Fünf-Minuten-Intervall| 5\.400|
|Volume pro Intervall| 10,8 MB|
|Nachrichten pro Intervall| 43|
|Nachrichten pro Monat| 371.520|
|Geschätzte Kosten pro Monat (USD)| 10,83 US-Dollar|

**Überwachungsprotokoll mit 1.000 Benutzern**

| | |
|---|---|
|Ereignisse pro Sekunde|0,1 |
|Ereignisse pro Fünf-Minuten-Intervall| 52|
|Volume pro Intervall|104 KB |
|Nachrichten pro Intervall|1 |
|Nachrichten pro Monat|8\.640 |
|Geschätzte Kosten pro Monat (USD)|10,80 US-Dollar |

### <a name="log-analytics-cost-considerations"></a>Kostenüberlegungen zu Log Analytics

Informationen zu den Kosten im Zusammenhang mit der Verwaltung des Log Analytics-Arbeitsbereichs finden Sie unter [Verwalten von Kosten durch Steuern des Datenvolumens und Vermerkdauer in Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage).

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

Erhalten Sie Antworten auf häufig gestellte Fragen und lesen Sie mehr über alle bekannten Probleme mit Intune-Protokollen in Azure Monitor.

### <a name="which-logs-are-included"></a>Welche Protokolle sind enthalten?

Zum Weiterleiten mit dieser Funktion sind sowohl Überwachungsprotokolle als auch Betriebsprotokolle (Vorschauversion) verfügbar.

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-event-hub"></a>Wann werden die entsprechenden Protokolle nach einer Aktion im Event Hub angezeigt?

Die Protokolle werden in der Regel innerhalb weniger Minuten nach Ausführung der Aktion in Ihrem Event Hub angezeigt. Weitere Informationen finden Sie in [Was sind Azure Event Hubs?](https://docs.microsoft.com/azure/event-hubs/).

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-storage-account"></a>Wann werden die entsprechenden Protokolle nach einer Aktion im Speicherkonto angezeigt?

Bei Azure-Speicherkonten liegt die Latenzzeit zwischen 5 und 15 Minuten nach Ausführung der Aktion.

### <a name="what-happens-if-an-administrator-changes-the-retention-period-of-a-diagnostic-setting"></a>Was passiert, wenn ein Administrator den Aufbewahrungszeitraum einer Diagnoseeinstellung ändert?

Die neue Aufbewahrungsrichtlinie wird auf Protokolle angewendet, die nach der Änderung gesammelt wurden. Protokolle, die vor der Änderung der Richtlinie gesammelt wurden, sind davon nicht betroffen.

### <a name="how-much-does-it-cost-to-store-my-data"></a>Wie viel kostet das Speichern meiner Daten?

Die Speicherkosten hängen von der Größe Ihrer Protokolle und dem gewählten Aufbewahrungszeitraum ab. Eine Liste der geschätzten Kosten für die Mandanten, die vom erzeugten Protokollvolumen abhängen, finden Sie in der [Speichergröße für Aktivitätsprotokolle](#storage-size-for-activity-logs) (in diesem Artikel).

### <a name="how-much-does-it-cost-to-stream-my-data-to-an-event-hub"></a>Wie viel kostet das Streamen meiner Daten zu einem Event Hub?

Die Streamingkosten richten sich nach der Anzahl der eingegangenen Nachrichten pro Minute. Einzelheiten zur Kostenberechnung und Kalkulation auf Basis der Anzahl der Nachrichten finden Sie unter [Event Hub-Nachrichten für Aktivitätsprotokolle](#event-hub-messages-for-activity-logs) (in diesem Artikel).

### <a name="how-do-i-integrate-intune-audit-logs-with-my-siem-system"></a>Wie integriere ich Intune-Überwachungsprotokolle in mein SIEM-System?

Verwenden Sie Azure Monitor mit Event Hubs zum Streamen von Protokollen an Ihr SIEM-System. Zuerst [streamen Sie die Protokolle an einen Event Hub](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub). Dann [richten Sie Ihr SIEM-Tool](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#access-data-from-your-event-hub) mit dem konfigurierten Event Hub ein. 

### <a name="what-siem-tools-are-currently-supported"></a>Welche SIEM-Tools werden derzeit unterstützt?

Derzeit wird Azure Monitor von [Splunk](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-integrate-activity-logs-with-splunk), QRadar und [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory) (öffnet eine neue Website) unterstützt. Weitere Informationen zur Funktionsweise von Connectors finden Sie unter [Streamen von Azure-Überwachungsdaten an einen Event Hub für die Nutzung durch ein externes Tool](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs).

### <a name="can-i-access-the-data-from-an-event-hub-without-using-an-external-siem-tool"></a>Kann ich auf die Daten von einem Event Hub auch ohne ein externes SIEM-Tool zugreifen?

Ja. Um von Ihrer benutzerdefinierten Anwendung aus auf die Protokolle zuzugreifen, können Sie die [Event Hubs-API](https://docs.microsoft.com/azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph) verwenden.

### <a name="what-data-is-stored"></a>Welche Daten werden gespeichert?

Intune speichert keine Daten, die über die Pipeline gesendet wurden. Intune leitet Daten im Auftrag des Mandanten an die Azure Monitor-Pipeline. Weitere Informationen finden Sie in der [Übersicht zu Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview).

## <a name="next-steps"></a>Nächste Schritte

* [Archivieren von Aktivitätsprotokollen in einem Speicherkonto](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-azure-monitor-route-logs-to-storage-account)
* [Weiterleiten von Aktivitätsprotokollen an einen Event Hub](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)
* [Integrieren von Aktivitätsprotokollen in Log Analytics](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)
