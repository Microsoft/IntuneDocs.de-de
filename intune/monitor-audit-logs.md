---
title: Überwachungsänderungen und -ereignisse in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Überwachungsprotokolle, die Microsoft Intune-Aktivitäten erfassen, überprüfen können.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d01b1f745450785209bf289be5b6e36ac65cc2d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66046303"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>Verwenden von Überwachungsprotokollen, um Ereignisse in Microsoft Intune zu verfolgen und zu überwachen

Überwachungsprotokolle umfassen einen Datensatz von Aktivitäten, die eine Änderung in Microsoft Intune bewirken. Durch Vorgänge zum Erstellen, Aktualisieren (Bearbeiten), Löschen, Zuweisen sowie Remoteaktionen werden alle Überwachungsereignisse erstellt, die Administratoren für die meisten Intune-Workloads überprüfen können. Die Überwachung ist standardmäßig für alle Kunden aktiviert. Sie kann nicht deaktiviert werden.

> [!NOTE]
> Die Aufzeichnung der Überwachungsereignisse wurde im Rahmen des Featurerelease im Dezember 2017 eingeführt und ab da begonnen. Frühere Ereignisse sind nicht verfügbar.

## <a name="who-can-access-the-data"></a>Wer kann auf die Daten zugreifen?

Benutzer mit den folgenden Berechtigungen können Überwachungsprotokolle überprüfen:

- Globaler Administrator
- Intune-Dienstadministrator
- Administratoren, denen eine Intune-Rolle mit den Berechtigungen **Überwachungsdaten** - **Lesen** zugewiesen wurde

## <a name="audit-logs-for-intune-workloads"></a>Überwachungsprotokolle für Intune-Workloads

Sie können für jede Intune-Workload Überwachungsprotokolle in der Überwachungsgruppe einsehen.

1. Wählen Sie im [Azure-Portal](https://portal.azure.com/) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.
2. Wählen Sie die Workload aus, deren Überwachungsprotokolle Sie überprüfen möchten. Wählen Sie beispielsweise **Geräte** aus.
3. Wählen Sie unter **Überwachung** die Option **Überwachungsprotokolle** aus.

## <a name="route-logs-to-azure-monitor"></a>Routen von Protokollen an Azure Monitor

Überwachungsprotokolle und Betriebsprotokolle können auch zu Azure Monitor weitergeleitet werden. Wählen Sie im Bereich **Überwachungsprotokolle** die **Einstellungen für das Exportieren von Daten** aus:

![Exportieren von Protokolldaten in Azure Monitor, indem die Einstellungen für das Exportieren von Daten in Intune ausgewählt werden](./media/audit-logs-export-data-settings.png)

Weitere Informationen zu diesem Feature finden Sie unter [Senden von Daten an den Speicher, an Event Hubs oder Log Analytics in Intune](review-logs-using-azure-monitor.md).

## <a name="review-audit-events"></a>Überprüfen von Überwachungsereignissen

![Auswählen von Überwachungsprotokollen in Intune, um Aktionen und das jeweilige Datum anzusehen, an dem ein Ereignis stattfand](./media/monitor-audit-logs.png "Überwachungsprotokolle")

Ein Überwachungsprotokoll verfügt über eine Standardlistenansicht, in der die folgenden Elemente angezeigt werden:

- Datum und Uhrzeit des Auftretens
- Initiiert von (Akteur)
- Anwendungsname
- Aktivität
- Ziel(e)
- Category
- Status

Wenn Sie detailliertere Informationen zu einem Ereignis sehen möchten, wählen Sie ein Element in der Liste aus:

![Abrufen detaillierterer Informationen aus Überwachungsprotokollen in Intune dazu, wer welche Aktionen durchgeführt hat](./media/monitor-audit-log-detail.png "Überwachungsprotokolldetails")

> [!NOTE]
> **Initiiert von (Akteur)** enthält Informationen dazu, wer die Aufgabe ausgeführt hat, und wo sie ausgeführt wurde. Wenn Sie beispielsweise im Azure-Portal in Intune die Aktivität ausführen, wird unter **Anwendung** immer **Microsoft Intune-Portalerweiterung** und unter **Anwendungs-ID** immer dieselbe GUID aufgeführt.
> 
> Im Abschnitt **Ziel(e)** werden mehrere Ziele und die geänderten Eigenschaften aufgeführt.  

## <a name="filter-audit-events"></a>Filtern von Überwachungsereignissen

Jede Workload verfügt über ein Menüelement, das die Kategorie der mit diesem Bereich verknüpften Überwachungsereignisse vorfiltert. Mit einer separaten Filteroption können Sie zu verschiedenen Kategorien wechseln und Details zu Ereignisaktionen innerhalb dieser Kategorie anzeigen. Sie können nach dem UPN suchen (z. B. nach dem Benutzer, der die Aktion ausgeführt hat). Ein Datumsbereichsfilter bietet die Optionen „24 Stunden“, „7 Tage“ oder „30 Tage“ an. Standardmäßig werden die letzten 30 Tage der Überwachungsereignisse angezeigt.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Abrufen von Überwachungsereignissen mithilfe der Graph-API

Details zur Verwendung der Graph-API, um bis zu einem Jahr an Überwachungsereignissen zu erhalten, finden Sie unter [List auditEvents (Auflisten von Überwachungsereignissen)](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Nächste Schritte

[Senden von Daten an den Speicher, an Event Hubs oder Azure Monitor-Protokolle in Intune (Vorschauversion)](review-logs-using-azure-monitor.md)

[Überprüfen der Schutzprotokolle für Client-Apps](app-protection-policy-settings-log.md).
