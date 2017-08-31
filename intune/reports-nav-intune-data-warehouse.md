---
title: Date Warehouse-API von Intune | Microsoft-Dokumentation
description: "Mithilfe dieser API können Sie Berichte erstellen, die einen Einblick in Ihre mobile Unternehmensumgebung ermöglichen."
keywords: Intune Data Warehouse
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 701D6CE9-43F6-4A29-8E84-E2B59931C635
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 52b498beb024b86282c93be7aa5a248800db6609
ms.sourcegitcommit: 294de4d4058de2c625abb8143e90880d27da9284
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2017
---
#  <a name="intune-data-warehouse-api"></a>Intune Data Warehouse-API

Die Data Warehouse-API von Intune können ermöglicht es Ihnen, auf Ihre Intune-Daten in einem computerlesbaren Format zuzugreifen, um sie in Ihren bevorzugten analytischen Tools zu verwenden. Mithilfe dieser API können Sie Berichte erstellen, die einen Einblick in Ihre mobile Unternehmensumgebung ermöglichen. Die API verwendet das OData-Protokoll, das folgenden Standardmustern folgt:

  -   Anforderungs- und Antwortheader
  -   Statuscodes
  -   HTTP-Methoden
  -   URL-Konventionen
  -   Medientypen
  -   Nutzlastformate
  -   Abfrageoptionen

OData (Open Data Protocol) erfüllt den OASIS-Standard (Organization for the Advancement of Structured Information Standards), der die bewährten Methoden zum Erstellen und Nutzen von Rest-APIs definiert. Intune Data Warehouse verwendet OData Version 4.0.

Dieser Abschnitt enthält einen Überblick über die Endpunkte, unterstützten HTTP-Methoden, zurückgegebenen Nutzlastformate und Dokumentation zum Intune Data Warehouse-Datenmodell.

> [!Important]  
> Sie können die neuesten Funktionen des Data Warehouse mithilfe der Betaversion ausprobieren. Für die Verwendung die Betaversion muss Ihre URL den Abfrageparameter `api-version=beta` enthalten. Die Betaversion bietet Features, bevor sie als unterstützter Dienst allgemein verfügbar gemacht werden. Da Intune kontinuierlich neue Features hinzufügt, könnten sich in der Betaversion Verhalten und Datenverträge ändern. Benutzerdefinierter Code oder Berichtstools, die von der Betaversion abhängig sind, könnten mit laufenden Updates nicht mehr funktionieren. <!--If you experience problems with the beta service, follow [link to feedback process]() to report the issue or provide feedback.-->

## <a name="odata-custom-client"></a>Benutzerdefinierter OData-Client

Sie können auf das Intune-Data Warehouse-Datenmodell über RESTful-Endpunkte zugreifen. Um auf Ihre zuzugreifen, muss sich der Client mithilfe von OAuth 2.0 bei Microsoft Azure Active Directory (Azure AD) autorisieren. Zuerst richten Sie eine Web-App und eine Client-App in Azure ein und erteilen dem Client Berechtigungen. Der lokale Client erhält die Autorisierung und kann dann mit den Data Warehouse-Endpunkten kommunizieren.

Weitere Informationen finden Sie unter [Abrufen von Daten aus der Data Warehouse-API mit einem REST-Client](reports-proc-data-rest.md).

## <a name="interacting-with-the-api"></a>Interagieren mit der API

Die API erfordert eine Autorisierung mit Azure AD. Azure AD verwendet OAuth 2.0. Nach der Autorisierung können Sie Daten aus der API abrufen, indem Sie ein HTTP GET-Verb verwenden und sich die verfügbar gemachten Entitätsauflistungen wenden. Weitere Informationen finden Sie hier:

 -  [Authorization (Autorisierung)](reports-api-url.md)
 -  [API URL Structure (API-URL-Struktur)](reports-api-url.md)

## <a name="intune-data-warehouse-data-model"></a>Intune Data Warehouse-Datenmodell

OData definiert ein abstraktes Datenmodell und ein Protokoll, mit denen alle Clients auf Informationen zugreifen können, die von einer beliebigen Datenquelle verfügbar gemacht wurden. Das Dokumentationsthema zum Datenmodell enthält eine Erläuterung der Namespaces, Entitäten und zurückgegebenen Objekte im Intune Data Warehouse-Datenmodell. Weitere Informationen finden Sie unter [Data Warehouse Data Model (Data Warehouse-Datenmodell)](reports-ref-data-model.md).

## <a name="next-steps"></a>Nächste Schritte

[Authentifizierungsszenarien für Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)  
[odata.org](http://www.odata.org)  
[OData Version 4.0](http://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)  