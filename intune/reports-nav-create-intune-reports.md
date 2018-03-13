---
title: Verwenden des Data Warehouse von Intune
titlesuffix: Microsoft Intune
description: "Verwenden Sie das Data Warehouse von Intune zum Erstellen von Berichten, die einen Einblick in Ihre mobile Unternehmensumgebung ermöglichen."
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: dd90c9d51fe212b0675da4d6039a535be0ff3c89
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="use-the-intune-data-warehouse"></a>Verwenden des Data Warehouse von Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Verwenden Sie das Data Warehouse von Intune zum Erstellen von Berichten, die einen Einblick in Ihre mobile Unternehmensumgebung ermöglichen. Einige der Berichte enthalten beispielsweise:
-   Trend der Benutzer, die sich bei Intune registrieren, sodass Sie Ihre Lizenzkäufe optimieren können
-   Strukturplan für App- und BS-Versionen, damit Sie den Zustand von Mobilgeräten überprüfen können
-   Trends zur Konformität der Registrierungen und Geräte, sodass Sie reibungslos Richtlinienaktualisierungen durchführen können

Das Data Warehouse bietet Ihnen Zugriff auf mehr Informationen über Ihre mobile Umgebung als das Azure-Portal. Mit dem Data Warehouse von Intune können Sie auf Folgendes zugreifen:

  -  Verlaufsdaten für Intune
  -  Daten, die täglich aktualisiert werden
  -  Ein Datenmodell, das den OData-Standard verwendet

> [!Note]
> Wenn Sie eine hybride Verwaltung mobiler Geräte (mobile device management, MDM) mit System Center Configuration Manager und Microsoft Intune verwenden, sollten Sie Ihre Daten aus SCCM abrufen. Das Intune Data Warehouse enthält nur Intune-Daten. Sie können ein SCCM Power BI-Dashboard für Ihre benutzerdefinierten Berichte verwenden. Weitere Informationen finden Sie unter [Announcing the Power BI solution template for System Center Configuration Manager (Ankündigung der Power BI-Lösungsvorlage für System Center Configuration Manager)]( https://powerbi.microsoft.com/blog/sccm-solution-template). und [Create a Power BI report and dashboard (Erstellen eines Power BI-Berichts und -Dashboards)](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/create-powerbi-report-dashboard).


> [!Important]  
> Sie können die neuesten Funktionen des Data Warehouse mithilfe der Betaversion ausprobieren. Für die Verwendung die Betaversion muss Ihre URL den Abfrageparameter `api-version=beta` enthalten. Die Betaversion bietet Features, bevor sie als unterstützter Dienst allgemein verfügbar gemacht werden. Da Intune kontinuierlich neue Features hinzufügt, könnten sich in der Betaversion Verhalten und Datenverträge ändern. Benutzerdefinierter Code oder Berichtstools, die von der Betaversion abhängig sind, könnten mit laufenden Updates nicht mehr funktionieren.

**Nächste Schritte**

- Rufen Sie einen Link ab und verwenden Sie Power BI, um Einblicke zu erhalten. Anweisungen hierzu finden Sie unter [Connect to the Intune Data Warehouse with Power BI (Verbinden mit dem Data Warehouse von Intune mit Power BI)](reports-proc-get-a-link-powerbi.md).
- Erstellen Sie mit Ihrem Link einen benutzerdefinierten Bericht mit Power BI. Weitere Anweisungen hierzu finden Sie unter [Create a report from the OData feed with Power BI (Erstellen eines Berichts aus dem OData-Feed mit Power BI)](reports-proc-create-with-odata.md).
- Weitere Informationen über die Intune-Data Warehouse-API, das Datenmodell und Beziehungen zwischen Entitäten<!-- , and an example of creating a custom client to retrieve data,--> finden Sie unter [Intune Data Warehouse-API](reports-nav-intune-data-warehouse.md).