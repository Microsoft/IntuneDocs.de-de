---
title: Data Warehouse-Zeitachse für die Benutzerentität
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie das Intune Data Warehouse Benutzer auf einer Zeitachse darstellt.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 363D148E-688F-4830-B6DE-AB4FE3648817
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7448954fce2b81c5783845c9fbdaaebf43fdf326
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2018
---
# <a name="user-lifetime-representation-in-the-microsoft-intune-data-warehouse"></a>Darstellung der Benutzerlebensdauer im Microsoft Intune-Data Warehouse

Anhand des Monats der Datenmomentaufnahmen, die im Intune Data Warehouse gespeichert werden, können Sie Fragen zu zeitbasierten Trends beantworten. Sie können sich z.B. die Anzahl von Benutzern ansehen, die im Laufe eines Monats hinzugefügt werden. Sie können auch die Anzahl von Benutzern abfragen, die aus dem System entfernt wurden.

Um diese Erkenntnis bereitzustellen, speichert das Data Warehouse Verlaufsinformationen. Das Data Warehouse kann die Lebensdauer einer Entität verfolgen. Das Warehouse zeichnet auf, wann eine Entität erstellt wurde, wann sich der Status der Entität geändert hat und wann eine Entität gelöscht wird. Anhand des Verlaufs, der durch tägliche Momentaufnahmen quantitativer Messungen erfasst wird, können Sie einen Tag mit dem vorherigen Tag vergleichen und so weiter.

Die Arbeit mit der Lebensdauer von Entitäten kann verwirrend sein, da die Entitäten ihren Zustand ändern. Wenn Sie daher eine Momentaufnahme an Tag 30 betrachten, liegt ein Benutzerdatensatz in den Daten möglicherweise nicht im aktiven Zustand vor. An den Tagen 29 und 28 ist der Datensatz der Entität jedoch möglicherweise aktiv. Vor Tag 28 war der Benutzer vielleicht noch gar nicht vorhanden.

Dieses Szenario wird klarer, wenn Sie die Lebensdauer einer Entität durchlaufen.

Angenommen, einem Benutzer **John Smith** wird am 01.06.2017 eine Lizenz zugewiesen. Die Tabelle **Benutzer** weist in diesem Fall den folgenden Eintrag auf: 
 
| DisplayName | isDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | 12/31/9999 | TRUE
 
John Smith gibt seine Lizenz am 25.07.2017 auf. Die Tabelle **Benutzer** weist die folgenden Einträge auf. Änderungen in vorhandenen Datensätzen werden gekennzeichnet: `marked`. 

| DisplayName | isDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | `07/26/2017` | `FALSE` 
| John Smith | TRUE | 07/26/2017 | 12/31/9999 | TRUE 

Die erste Zeile gibt an, dass John Smith vom 01.06.2017 bis zum 25.07.2017 in Intune vorhanden war. Der zweite Eintrag gibt an, dass der Benutzer am 25.07.2017 gelöscht wurde und in Intune nicht mehr vorhanden ist.

Nehmen wir jetzt an, dass dem Benutzer John Smith am 31.08.2017 eine neue Lizenz zugewiesen wird. Die Tabelle „Benutzer“ weist in diesem Fall die folgenden Einträge auf:
 
| DisplayName | isDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | 07/26/2017 | FALSE 
| John Smith | TRUE | 07/26/2017 | `08/31/2017` | `FALSE` 
| John Smith | FALSE | 08/31/2017 | 12/31/9999 | TRUE 
 
Eine Person, die den aktuellen Status aller Benutzer anzeigen möchte, kann den folgenden Filter anwenden: `IsCurrent = TRUE`. 
 
Eine Person, die nur vorhandene Benutzer anzeigen möchte, kann den folgenden Filter anwenden: `IsCurrent = TRUE AND IsDeleted = FALSE`.

## <a name="dimension-tables-in-the-entity-lifetime"></a>Dimensionstabellen in der Entitätslebensdauer

Um den Verlauf von Zustandsänderungen bei Entitäten zu speichern, werden in Intune keine Datensätze gelöscht. Stattdessen wird ein Datensatz als gelöscht markiert. Dies bezeichnet man als vorläufiges Löschen. Die Dimensionstabellen verwenden verschiedene Metadatenspalten zum Nachverfolgen der Lebensdauer von Datensätzen. 

Am häufigsten werden folgende Metadatenspalten verwendet: 

| Name der Metadateneigenschaft  | Interpretation von Werten |
|--|--|
| isDeleted | Gibt an, ob die Entität in Intune gelöscht wurde. |
| StartDateInclusiveUTC  | Das UTC-Datum, an dem die Entität in das Intune Data Warehouse geladen wurde. Möglicherweise wurde die Entität erstellt, bevor sie in das Intune Data Warehouse importiert wurde. |
| DeletedDateUTC  | Das UTC-Datum, an dem die Entität in Intune gelöscht wurde. |  

Jede Metadatenspalte, die mit dem Präfix **Row** beginnt, wie z.B. **RowLastModifiedDateTimeUTC**, gibt an, wann ein Datensatz im Intune Data Warehouse erstellt oder geändert wurde. Das Warehouse ist den Daten in Intune nachgelagert. Dieser Wert weist keine Beziehung zur Lebensdauer der Entität in Intune auf.  
 
Eine Person, die nur die derzeit vorhandenen Dimensionsentitäten anzeigen möchte, sollte einen Filter **IsDeleted = "false"** anwenden.

## <a name="next-steps"></a>Nächste Schritte

 - Weitere Informationen zur Entität **Aktueller Benutzer** finden Sie unter [Verweis für die Entität „Aktueller Benutzer“](reports-ref-current-user.md).
 - Weitere Informationen zur Entität **Benutzer** finden Sie unter [Verweis für die Benutzerentität](reports-ref-user.md).