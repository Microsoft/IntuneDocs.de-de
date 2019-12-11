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
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6af0718f2b926383bb943b6321b4d5839346ce7
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991981"
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

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie Mandanten **Verwaltung** > Überwachungs **Protokolle**aus.
3. Um die Ergebnisse zu filtern, wählen Sie **Filtern** aus, und verfeinern Sie die Ergebnisse mithilfe der folgenden Optionen.
    - **Kategorie**: z. b. **Konformität**, **Gerät**und **Rolle**.
    - **Aktivität**: die hier aufgeführten Optionen werden durch die Option unter **Kategorie**eingeschränkt.
    - **Datumsbereich**: Sie können Protokolle für den vorherigen Monat, die Woche oder den Tag auswählen.
4. Wählen Sie **Anwenden** aus.
4. Wählen Sie ein Element in der Liste aus, um die Aktivitäts Details anzuzeigen.

## <a name="route-logs-to-azure-monitor"></a>Routen von Protokollen an Azure Monitor

Überwachungsprotokolle und Betriebsprotokolle können auch zu Azure Monitor weitergeleitet werden. Wählen Sie im Bereich **Überwachungsprotokolle** die **Einstellungen für das Exportieren von Daten** aus:

![Exportieren von Protokolldaten in Azure Monitor, indem die Einstellungen für das Exportieren von Daten in Intune ausgewählt werden](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

> [!NOTE]
> Weitere Informationen zu dieser Funktion und zum Überprüfen der Voraussetzungen für deren Verwendung finden Sie unter [Senden von Protokolldaten an Storage, Event Hubs oder Log Analytics](review-logs-using-azure-monitor.md).

> [!NOTE]
> **Initiiert von (Akteur)** enthält Informationen dazu, wer die Aufgabe ausgeführt hat, und wo sie ausgeführt wurde. Wenn Sie beispielsweise im Azure-Portal in Intune die Aktivität ausführen, wird unter **Anwendung** immer **Microsoft Intune-Portalerweiterung** und unter **Anwendungs-ID** immer dieselbe GUID aufgeführt.
>
> Im Abschnitt **Ziel(e)** werden mehrere Ziele und die geänderten Eigenschaften aufgeführt.  

## <a name="use-graph-api-to-retrieve-audit-events"></a>Abrufen von Überwachungsereignissen mithilfe der Graph-API

Details zur Verwendung der Graph-API, um bis zu einem Jahr an Überwachungsereignissen zu erhalten, finden Sie unter [List auditEvents (Auflisten von Überwachungsereignissen)](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Nächste Schritte

[Senden von Daten an den Speicher, an Event Hubs oder Azure Monitor-Protokolle in Intune (Vorschauversion)](review-logs-using-azure-monitor.md)

[Überprüfen der Schutzprotokolle für Client-Apps](../apps/app-protection-policy-settings-log.md).
