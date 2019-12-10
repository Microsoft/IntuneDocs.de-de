---
title: Microsoft Intune-Berichte
titleSuffix: Microsoft Intune
description: Intune stellt bestimmte Arten von Berichten mit fokussierten Ansichten zur Verfügung, die konsistente und aktuelle Daten enthalten.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 05258c5363b43398dee1815bb91c50878803e426
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74391941"
---
# <a name="intune-reports"></a>Intune-Berichte
Mithilfe von Microsoft Intune-Berichten können Sie die Integrität und Aktivität von Endpunkten in Ihrem Unternehmen effektiver und proaktiver überwachen. Zudem erhalten Sie weitere Berichtsdaten zu Intune. Sie können beispielsweise Berichte zur Gerätekonformität, -integrität und zu -trends abrufen. Darüber hinaus können Sie benutzerdefinierte Berichte erstellen, um spezifischere Daten zu erhalten. 

> [!NOTE]
> Die Änderungen an der Berichterstellung in Intune werden schrittweise vorgenommen, damit Sie sich auf die neue Struktur vorbereiten und an diese gewöhnen können.

Die Berichtstypen sind in die folgenden Schwerpunktbereiche unterteilt:
- **Operational** (operativ): bietet gezielt erfasste und aktuelle Daten, anhand derer Sie Maßnahmen ergreifen können. Diese Berichte sind besonders für Administratoren, Fachexperten und Helpdeskmitarbeiter nützlich.
- **Organizational** (organisatorisch): bietet eine umfassendere Zusammenfassung zum allgemeinen Zustand, z. B. den Status der Geräteverwaltung. Diese Berichte sind besonders für Manager und Administratoren nützlich.
- **Historical** (verlaufsbezogen): bietet Informationen zu Mustern und Trends für einen bestimmten Zeitraum. Diese Berichte sind besonders für Manager und Administratoren nützlich.
- **Specialist** (spezialisiert): ermöglicht die Verwendung von Rohdaten zur Erstellung Ihrer eigenen benutzerdefinierten Berichte. Diese Berichte sind besonders für Administratoren nützlich.

Das Berichterstellungsframework bietet konsistente und umfassendere Funktionen zur Berichterstellung. Die verfügbaren Berichte umfassen die folgenden Funktionen:
- **Search and sort** (Suchen und Sortieren): Sie können einzelne Spalten suchen und sortieren. Dabei spielt es keine Rolle, wie groß das Dataset jeweils ist.
- **Data paging** (Datenpaging): Sie können Ihre Daten auf der Grundlage von Paging scannen – entweder Seite für Seite oder indem Sie zu einer bestimmten Seite springen.
- **Performance** (Leistung): Sie können schnell über große Mandanten Berichte generieren und anzeigen.
- **Export** (Exportieren): Sie können schnell über große Mandanten generierte Berichtsdaten exportieren.

### <a name="who-can-access-the-data"></a>Wer kann auf die Daten zugreifen?

Benutzer mit den folgenden Berechtigungen können Protokolle überprüfen:

- Globaler Administrator
- Intune-Dienstadministrator
- Administratoren, denen eine Intune-Rolle mit **Leseberechtigungen** zugewiesen ist

## <a name="non-compliant-devices-report-operational"></a>Bericht zu nicht konformen Geräten (operativ)
Der Bericht zu nicht konformen Geräten enthält Daten, die in der Regel von Helpdeskmitarbeitern oder Administratoren verwendet werden, um Probleme zu identifizieren und zu beheben. Die in diesen Berichten enthaltenen Daten sind aktuell und können verwendet werden, um unerwartetes Verhalten zu ermitteln und angemessene Maßnahmen zu ergreifen. Der Bericht wird zusammen mit der Workload bereitgestellt. So können Sie auf die nicht konformen Geräte zugreifen, ohne aktive Workflows unterbrechen zu müssen. Dieser Bericht enthält Funktionen zum Filtern, Suchen, Paging und Sortieren. Außerdem können Sie einen Drilldown ausführen, um die Problembehandlung zu erleichtern.

Sie können den Bericht zu **nicht konformen Geräten** wie folgt abrufen:

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonformität** > **Nicht konforme Geräte**.

    ![Bericht zu nicht konformen Geräten](./media/intune-reports/intune-reports-02.png)

## <a name="device-compliance-report-organizational"></a>Bericht zur Gerätekonformität (organisatorisch)
Berichte zur Gerätekonformität sollten möglichst umfassend sein und eine traditionellere Berichtsansicht zu Daten bereitstellen, auf deren Grundlage aggregierte Metriken ermittelt werden. Dieser Bericht ist für die Arbeit mit großen Datasets konzipiert, sodass Sie einen vollständigen Überblick über die Gerätekonformität erhalten. Der Bericht zur Gerätekonformität enthält die Konformitätszustände aller Geräte und gibt damit unabhängig von der Größe des Datasets einen umfassenderen Überblick über die Daten. Außerdem umfasst er eine vollständige Aufschlüsselung der Datensätze sowie eine praktische Visualisierung der aggregierten Metriken. Sie können ihn generieren, indem Sie Filter anwenden und auf die Schaltfläche „Bericht generieren“ klicken. Dadurch werden die Daten aktualisiert, sodass jeweils der aktuelle Zustand im Bericht angezeigt wird. Außerdem können die einzelnen Datensätze abgerufen werden, aus denen die aggregierten Daten bestehen. Wie die meisten Berichte im neuen Framework können diese Datensätze sortiert und durchsucht werden, sodass Sie nach den Informationen filtern können, die Sie benötigen. 

Zum Anzeigen eines generierten Berichts zu den Gerätezuständen können Sie wie folgt vorgehen:
1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Berichte**, um die Berichtsübersicht abzurufen.
3. Wählen Sie **Gerätekompatibilität** aus.
4. Klicken Sie auf die Filter **Konformitätsstatus** > **Betriebssystem** und **Besitz**, um Ihren Bericht einzuschränken.
5. Klicken Sie auf **Bericht generieren** (oder **Erneut generieren**), um aktuelle Daten abzurufen.

    ![Bericht zur Richtlinienkonformität](./media/intune-reports/intune-reports-02a.png)

    > [!NOTE]
    > Dieser Bericht zur **Gerätekonformität** enthält einen Zeitstempel, an dem Sie erkennen können, wann der Bericht zuletzt erstellt wurde. 

Weitere Informationen finden Sie unter [Erzwingen der Konformität für Microsoft Defender ATP mit bedingtem Zugriff in Intune](~/protect/advanced-threat-protection.md).

## <a name="reports-summary"></a>Berichtsübersicht 

Sie können den Bericht zur Gerätekonformität in Form eines Zusammenfassungsberichts in der Workload **Berichte** abrufen. Sie können den Bericht zur Gerätekonformität wie folgt abrufen:

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Berichte**, um die Berichtsübersicht abzurufen.

    ![Zusammenfassung der Intune-Berichte](./media/intune-reports/intune-reports-01.png)

## <a name="device-compliance-trend-report-historical"></a>Bericht zu Gerätekonformitätstrends (verlaufsbezogen)
Berichte zu Gerätekonformitätstrends werden häufig von Administratoren und Architekten verwendet, um Langzeittrends zur Gerätekonformität zu ermitteln. Es werden aggregierte Daten zu einem bestimmten Zeitraum angezeigt. Dies ist nützlich, um Entscheidungen zu zukünftigen Investitionen zu treffen, Prozesse zu verbessern oder Untersuchungen von möglichen Anomalien anzufordern. Es können auch Filter angewendet werden, um bestimmte Trends zu ermitteln. Bei den von diesem Bericht bereitgestellten Daten handelt es sich um eine Momentaufnahme des aktuellen Mandantenzustands (beinahe in Echtzeit). 

Berichte zu Gerätekonformitätstrends enthalten Informationen zu Gerätekonformitätszuständen über einen bestimmten Zeitraum hinweg. Sie können diese Berichte verwenden, um Höchstwerte zur Konformität zu ermitteln und den Zeit- und Arbeitsaufwand entsprechend anzupassen.

Führen Sie die folgenden Schritte aus, um den Bericht zu den **Trends** abzurufen:

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Berichte** > **Trends**, um Daten zur Gerätekonformität für einen Zeitraum von 60 Tagen abzurufen.

    ![Intune-Trendbericht](./media/intune-reports/intune-reports-03.png)

## <a name="azure-monitor-integration-reports-specialist"></a>Integrationsberichte für Azure Monitor (spezialisiert)
Sie können Ihre eigenen Berichte im Hinblick auf die Daten anpassen, die Sie benötigen. Alternativ können Sie auch die Daten in Ihren Berichten mithilfe von [Log Analytics](reports.md#log-analytics) und [Azure Monitor-Arbeitsmappen](reports.md#workbooks) über [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview) abrufen. Mit diesen Lösungen können Sie Warnungen konfigurieren sowie benutzerdefinierte Abfragen und Dashboards erstellen, auf denen die Daten zur Gerätekonformität Ihren Anforderungen entsprechend angezeigt werden. Zudem können Sie Aktivitätsprotokolle in Ihrem Azure Storage-Konto speichern, über [SIEM-Tools (Security Information & Event Management)](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration) in die Berichte integrieren und eine Korrelation zwischen den Berichten und Azure Active Directory-Aktivitätsprotokollen herstellen. Azure Monitor-Arbeitsmappen können zusätzlich zu importierten Dashboards zur benutzerdefinierten Berichterstellung verwendet werden.

> [!NOTE]
> Für komplexe Berichterstellungsfunktionen ist ein Azure-Abonnement erforderlich.

Spezialisierte Berichte stellen beispielsweise in Form von benutzerdefinierten Berichten eine Korrelation zwischen Daten zum Gerätebesitz und Daten zur Plattformregistrierung her. Anschließend können diese benutzerdefinierten Berichte auf vorhandenen Dashboards im Azure Active Directory-Portal angezeigt werden.

Gehen Sie wie folgt vor, um benutzerdefinierte Berichte zu erstellen und abzurufen:

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Berichte** > **Diagnoseeinstellungen**, und fügen Sie eine [Diagnoseeinstellung](reports.md#diagnostic-settings) hinzu.

    ![Zusammenfassung der Intune-Berichte](./media/intune-reports/intune-reports-04.png)

3. Klicken Sie auf **Diagnoseeinstellung hinzufügen**, um den Bereich **Diagnoseeinstellungen** abzurufen. 
4. Geben Sie einen **Namen** für die Diagnoseeinstellungen ein. 
5. Wählen Sie die Einstellungen **An Log Analytics senden** und **DeviceComplianceOrg** aus.

    ![Zusammenfassung der Intune-Berichte](./media/intune-reports/intune-reports-04a.png)

6. Klicken Sie auf **Speichern**.
7. Klicken Sie als Nächstes auf **Log Analytics**, um mithilfe von [Log Analytics](reports.md#log-analytics) eine neue Protokollabfrage zu erstellen und auszuführen.

   ![Log Analytics: Protokollabfrage](./media/intune-reports/intune-reports-05.png)

8. Klicken Sie auf **Arbeitsmappen**, um mithilfe von [Azure Monitor-Arbeitsmappen](reports.md#workbooks) einen interaktiven Bericht zu erstellen und zu öffnen.

   ![Arbeitsmappen: interaktive Berichte](./media/intune-reports/intune-reports-07.png)

### <a name="diagnostic-settings"></a>Diagnoseeinstellungen
Jede Azure-Ressource erfordert eine eigene Diagnoseeinstellung. Damit wird für jede Ressource Folgendes definiert:

- Kategorien von Protokollen und Metrikdaten, die an die in der Einstellung definierten Ziele gesendet werden. Die verfügbaren Kategorien variieren je nach Ressourcentyp.
- Mindestens ein Ziel, an das die Protokolle gesendet werden sollen. Zu den aktuellen Zielen gehören der Log Analytics-Arbeitsbereich, Event Hubs und Azure Storage.
- Eine Aufbewahrungsrichtlinie für Daten, die in Azure Storage gespeichert werden

Eine einzelne Diagnoseeinstellung kann jeweils eins der Ziele definieren. Wenn Sie Daten an mehr als einen bestimmten Zieltyp senden möchten (z. B. an zwei unterschiedliche Log Analytics-Arbeitsbereiche), sollten Sie mehrere Einstellungen festlegen. Jede Ressource kann bis zu fünf Diagnoseeinstellungen aufweisen.

Weitere Informationen zu Diagnoseeinstellungen finden Sie unter [Erstellen einer Diagnoseeinstellung zum Erfassen von Plattformprotokollen und Metriken in Azure](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-settings).

### <a name="log-analytics"></a>Protokollanalysen
Log Analytics ist das wichtigste Tool im Azure-Portal zum Schreiben von Protokollabfragen und zum interaktiven Analysieren der Ergebnisse dieser Abfragen. Auch wenn eine Protokollabfrage an einer anderen Stelle in Azure Monitor verwendet wird, schreiben und testen Sie sie in der Regel zuerst mithilfe von Log Analytics. Ausführliche Informationen zur Verwendung von Log Analytics und zum Erstellen von Protokollabfragen finden Sie unter [Übersicht über Protokollabfragen in Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview). 

### <a name="workbooks"></a>Arbeitsmappen
Arbeitsmappen kombinieren Text, Analytics-Abfragen, Azure-Metriken und Parameter in umfangreichen interaktiven Berichten. Sie können von allen anderen Teammitgliedern bearbeitet werden, die Zugriff auf dieselben Azure-Ressourcen haben. Weitere Informationen zu Arbeitsmappen finden Sie unter [Azure Monitor-Arbeitsmappen](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks). Außerdem können Sie mit Arbeitsmappenvorlagen arbeiten und eigene Beiträge hinzufügen. Weitere Informationen finden Sie unter [Azure Monitor-Arbeitsmappenvorlagen](https://go.microsoft.com/fwlink/?linkid=867045).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie unter den folgenden Links:
- [Blog: Berichterstellungsframework für Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553)
- [Azure Monitor](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-activity-logs-azure-monitor)
- [Was ist Log Analytics?](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview#what-is-log-analytics)
- [Protokollabfragen](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview)
- [Erste Schritte mit Log Analytics in Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/log-query/get-started-portal)
- [Azure Monitor-Arbeitsmappen](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks)
- [SIEM-Tools (Security Information & Event Management)](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)
