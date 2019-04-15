---
title: Datenmodell von Data Warehouse
titleSuffix: Microsoft Intune
description: Microsoft Intune Data Warehouse überprüft täglich die Daten, um eine Verlaufsansicht Ihrer sich ständig ändernden mobilen Umgebung bereitzustellen.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/10/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a56c06970e267d8ba604e9d4e53f4a3f315fbcb
ms.sourcegitcommit: af2512a1342d8037a96a61c8cc2c63e107913733
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59533558"
---
# <a name="microsoft-intune-data-warehouse-data-model"></a>Microsoft Intune-Data Warehouse-Datenmodell

Intune Data Warehouse entnimmt täglich Datenstichproben, um eine Verlaufsansicht Ihrer sich ständig ändernden Umgebung mobiler Geräte bereitzustellen. Die Ansicht besteht aus zeitlich aufeinander bezogenen Entitäten.

## <a name="entities-entity-sets"></a>Entitäten: Entitätenmengen

Das Warehouse macht Daten in den folgenden allgemeinen Bereichen verfügbar:

  -  Apps und Nutzung mit aktiviertem App-Schutz
  -  Registrierte Geräte, Eigenschaften und Inventar
  -  Apps- und Softwareinventar
  -  Gerätekonfiguration und Konformitätsrichtlinien

Diese Bereiche enthalten die Entitäten, die für Ihre Intune-Umgebung von Bedeutung sind. Informationen zu den Entitätenmengen finden Sie in den folgenden Themen:

  -  [Anwendung](reports-ref-application.md)
  -  [Datum](reports-ref-date.md)
  -  [Geräte](reports-ref-devices.md)
  -  [Intune-Verwaltungserweiterung](reports-ref-intunemanagementextension.md)
  -  [Richtlinie](reports-ref-policy.md)
  -  [Mobile App-Verwaltung (MAM)](reports-ref-mobile-app-management.md)
  -  [Benutzer](reports-ref-user.md)
  -  [Aktueller Benutzer](reports-ref-current-user.md)
  -  [Zuordnung der Benutzergeräte](reports-ref-user-device.md)

## <a name="relationships-star-schema-model"></a>Beziehungen: Sternschemamodell

Das Warehouse strukturiert die Entitäten in Beziehungen, die für die von Ihnen gestellten Fragen relevant sind. Beispielsweise können Sie die Anzahl von Installationen einer intern entwickelten Android-Anwendung überprüfen. Die Struktur des Data Warehouse ermöglicht Ihnen Einblicke in Ihre mobile Umgebung. Andere Analysetools wie Microsoft Power BI können das Datenmodell von Data Warehouse wiederum nutzen, um Visualisierungen und dynamische Dashboards zu erstellen.

Die Entitäten und Beziehungen verwenden ein Sternschemamodell. Ein Sternschema stellt Zusammenhänge zwischen Fakten über die Zeitdimension dar. Im Kontext des Modells ist ein *Fakt* eine quantitative Messung, z.B. die Anzahl der Geräte, die Anzahl von Apps oder der Zeitpunkt der Registrierung. In Faktentabellen werden große Datenmengen gespeichert. Sie können sehr groß werden, daher werden Informationen normalerweise auf 30 Tage beschränkt. Eine *Dimension* stellt Kontext zu den Fakten bereit. Während Fakten darstellen, was passiert ist, geben Dimensionen an, wem etwas passiert ist. Dimensionstabellen, wie z.B. die Tabelle **Benutzer**, sind kleiner und können Daten für längere Zeit aufbewahren als Faktentabellen. 

Ein Sternschema-Modell bietet hohe für Flexibilität und Analysefunktionen, damit Sie die Berichte erstellen können, die zum Verständnis der Entwicklung Ihrer mobilen Umgebung benötigen.

## <a name="time-daily-snapshots"></a>Zeit: Tägliche Momentaufnahmen

Das Warehouse ist Ihren Intune-Daten nachgelagert. Intune erstellt täglich um Mitternacht UTC eine Momentaufnahme und speichert die Momentaufnahme im Warehouse. Die Dauer der Aufbewahrung von Momentaufnahmen unterscheidet sich von Faktentabelle zu Faktentabelle. Einige werden sieben Tage, andere 30 Tage und einige auch länger gespeichert.

## <a name="next-steps"></a>Nächste Schritte

 - Informationen zur Nachverfolgung der Benutzerlebensdauer über das Data Warehouse in Intune finden Sie unter [Darstellung der Benutzerlebensdauer im Intune Data Warehouse](reports-ref-user-timeline.md).
 - Weitere Informationen zum Arbeiten mit Data Warehouses finden Sie unter [Erstellen des ersten Data Warehouse](https://www.codeproject.com/Articles/652108/Create-First-Data-WareHouse).
 - Weitere Informationen zum Arbeiten mit Power BI und einem Data Warehouse finden Sie unter [Erstellen eines neuen Power BI-Berichts durch Importieren eines Datasets](https://powerbi.microsoft.com/documentation/powerbi-service-create-a-new-report/). 
