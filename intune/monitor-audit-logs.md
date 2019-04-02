---
title: Überwachen von Änderungen und Ereignisse in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Überwachungsprotokolle, die Microsoft Intune-Aktivitäten erfassen, überprüfen können.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93072ba4730de0252f54d93fa1169062d496ce38
ms.sourcegitcommit: 1069b3b1ed593c94af725300aafd52610c7d8f04
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58394900"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>Verwendung von Überwachungsprotokollen zum Nachverfolgen und Überwachen von Ereignissen in Microsoft Intune

Überwachungsprotokolle umfassen einen Datensatz von Aktivitäten, die eine Änderung in Microsoft Intune bewirken. Erstellen, aktualisieren (Bearbeiten), Delete, zuweisen und Remoteaktionen erstellen Überwachungsereignisse, die Administratoren für die meisten Intune-Workloads überprüfen können. Standardmäßig ist die Überwachung für alle Kunden aktiviert. Es kann nicht deaktiviert werden.

> [!NOTE]
> Überwachen von Ereignissen, die auf der Feature-Release von Dezember 2017 eine Aufzeichnung gestartet hat. Ereignisse vor sind nicht verfügbar.

## <a name="who-can-access-the-data"></a>Wer kann auf die Daten zugreifen?

Benutzer mit den folgenden Berechtigungen können Überwachungsprotokolle überprüfen:

- Globaler Administrator
- Intune-Dienstadministrator
- Administratoren, denen eine Intune-Rolle mit den Berechtigungen **Überwachungsdaten** - **Lesen** zugewiesen wurde

## <a name="audit-logs-for-intune-workloads"></a>Überwachungsprotokolle für Intune-Workloads

Sie können für jede Intune-Workload Überwachungsprotokolle in der Überwachungsgruppe einsehen.

1. Wählen Sie im [Azure-Portal](https://portal.azure.com/) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.
2. Wählen Sie die arbeitsauslastung, die Sie Überwachungsprotokolle überprüfen möchten. Wählen Sie z. B. **Geräte**.
3. Klicken Sie unter **Überwachung**, wählen Sie **Überwachungsprotokolle**.

## <a name="route-logs-to-azure-monitor"></a>Routen von Protokollen an Azure Monitor

Überwachung und Betriebsprotokolle können auch auf Azure Monitor weitergeleitet werden. In **Überwachungsprotokolle**Option **Dateneinstellungen exportieren**:

![Exportieren von Daten in Azure Monitor durch Auswählen von Einstellungen für den Export Data in Intune](./media/audit-logs-export-data-settings.png)

Weitere Informationen zu diesem Feature finden Sie unter [Senden von Daten an den Speicher, an Event Hubs oder Log Analytics in Intune](review-logs-using-azure-monitor.md).

## <a name="review-audit-events"></a>Überprüfen von Überwachungsereignissen

![Wählen Sie die Überwachungsprotokolle in Intune finden Sie unter Aktionen und Daten, wenn Ereignisse aufgetreten sind](./media/monitor-audit-logs.png "Überwachungsprotokolle")

Ein Überwachungsprotokoll verfügt über eine Standardlistenansicht, in der die folgenden Elemente angezeigt werden:

- Datum und Uhrzeit des Auftretens
- Initiiert von (Akteur)
- Anwendungsname
- Aktivität
- Ziel(e)
- Category
- Status

Um weitere Informationen zu einem Ereignis anzuzeigen, wählen Sie ein Element in der Liste aus:

![Erhalten Sie ausführlichere Informationen zu wer getan hat, was in der Überwachung in der Intune-Protokolle](./media/monitor-audit-log-detail.png "Details des Überwachungsprotokolls")

> [!NOTE]
> **Initiiert von (Akteur)** enthält Informationen, die die Aufgabe ausgeführt wurde, und, wo er ausgeführt wurde. Wenn Sie beispielsweise im Azure-Portal in Intune die Aktivität ausführen, wird unter **Anwendung** immer **Microsoft Intune-Portalerweiterung** und unter **Anwendungs-ID** immer dieselbe GUID aufgeführt.
> 
> Im Abschnitt **Ziel(e)** werden mehrere Ziele und die geänderten Eigenschaften aufgeführt.  

## <a name="filter-audit-events"></a>Filtern von Überwachungsereignissen

Jede Workload verfügt über ein Menüelement, das die Kategorie der mit diesem Bereich verknüpften Überwachungsereignisse vorfiltert. Mit einer separaten Filteroption können Sie zu verschiedenen Kategorien wechseln und Details zu Ereignisaktionen innerhalb dieser Kategorie anzeigen. Sie können nach dem UPN, z. B. der Benutzer suchen, die die Aktion ausgeführt hat. Ein Datumsbereichsfilter bietet die Optionen „24 Stunden“, „7 Tage“ oder „30 Tage“ an. Standardmäßig werden die letzten 30 Tage der Überwachungsereignisse angezeigt.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Abrufen von Überwachungsereignissen mithilfe der Graph-API

Ausführliche Informationen zum Abrufen von bis zu einem Jahr von Überwachungsereignissen mithilfe der Graph-API, finden Sie unter [List AuditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Nächste Schritte

[Senden von Daten in den Speicher, Event Hubs oder log Analytics](review-logs-using-azure-monitor.md).

[Überprüfen der Schutzprotokolle für Client-Apps](app-protection-policy-settings-log.md).
