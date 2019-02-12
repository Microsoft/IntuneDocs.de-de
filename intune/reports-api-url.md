---
title: Endpunkt der Intune Data Warehouse-API
titlesuffix: Microsoft Intune
description: Dieses Referenzthema beschreibt die URL-Struktur der Microsoft Intune-Data Warehouse-API. Es werden Beispiele für Filter bereitgestellt.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: caf4401a2274a74050ec0eb404363cfc15b23e76
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55851439"
---
# <a name="intune-data-warehouse-api-endpoint"></a>Endpunkt der Intune Data Warehouse-API

Sie können die Intune-Data Warehouse-API mit einem Konto mit bestimmten rollenbasierten Zugriffssteuerungen und Azure AD-Anmeldeinformationen verwenden. Anschließend autorisieren Sie Ihren REST-Client mithilfe von OAuth 2.0 für Azure AD. Schließlich erstellen Sie eine aussagekräftige URL, um eine Data Warehouse-Ressource aufzurufen.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="authorization"></a>Autorisierung

Azure Active Directory (Azure AD) bietet Ihnen über OAuth 2.0 die Möglichkeit, den Zugriff auf Webanwendungen und Web-APIs in Ihrem Azure AD-Mandanten zu autorisieren. Dieser Leitfaden ist sprachenunabhängig und beschreibt, wie HTTP-Nachrichten gesendet und empfangen werden können, ohne Open Source-Bibliotheken zu verwenden. Der Codefluss zur Autorisierung mit OAuth 2.0 wird in [section 4.1 (Abschnitt 4.1)](https://tools.ietf.org/html/rfc6749#section-4.1) der OAuth 2.0-Spezifikation beschrieben.

Weitere Informationen finden Sie unter [Authorize access to web applications using OAuth 2.0 and Azure Active Directory (Autorisieren des Zugriffs zu Webanwendungen mithilfe von OAuth 2.0 und Azure Active Directory)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).

## <a name="api-url-structure"></a>API-URL-Struktur

Die Endpunkte der Data Warehouse-API lesen die Entitäten für jeden Satz. Die API unterstützt ein **GET** HTTP-Verb und eine Teilmenge der Abfrageoptionen.

Die URL für Intune verwendet das folgende Format:  
`https://fef.{location}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity-collection}?api-version={api-version}`

> [!NOTE]
> Ersetzen Sie in der obigen URL `{location}`, `{entity-collection}` und `{api-version}` basierend auf den Details, die in folgender Tabelle bereitgestellt wurden.

Die URL enthält die folgenden Elemente:

| Element | Beispiel | Beschreibung |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| location | msua06 | Die Basis-URL kann im Blatt „Data Warehouse API“ im Azure Portal gefunden werden. |
| Entitätssammlung | Daten | Der Name der OData-Entitätssammlung. Weitere Informationen zu Sammlungen und Entitäten im Datenmodell finden Sie unter [Data Model (Datenmodell)](reports-ref-data-model.md). |
| api-version | Beta | Die Version ist die Version der API, auf die zugegriffen wird. Weitere Informationen finden Sie unter [Version](#API-version-information). |
| maxhistorydays | 7 | (Optional) Die maximale Anzahl an Tagen des Verlaufs, die abgerufen werden soll Dieser Parameter kann für jede Sammlung bereitgestellt werden, hat jedoch nur bei Sammlungen einen Effekt, deren Schlüsseleigenschaft `dateKey` enthält. Weitere Informationen finden Sie unter [DateKey Range Filters (DateKey-Bereichsfilter)](reports-api-url.md#datekey-range-filters). |

## <a name="api-version-information"></a>Information zur API-Version

Die aktuelle Version der API ist `beta`. 

## <a name="odata-query-options"></a>OData-Abfrageoptionen

Die aktuelle Version unterstützt die OData-Abfrageparameter `$filter, $orderby, $select, $skip,` und `$top`.

## <a name="datekey-range-filters"></a>DateKey-Bereichsfilter

`DateKey`-Bereichsfilter können verwendet werden, um die Menge der Daten zu begrenzen, die für einige der Sammlungen mit `dateKey` als Schlüsseleigenschaft heruntergeladen werden sollen. Der `DateKey`-Filter kann verwendet werden, um die Leistung des Diensts zu optimieren, indem folgende `$filter`-Abfrageparameter bereitgestellt werden:

1.  Nur `DateKey` in `$filter`. Dadurch werden die Operatoren `lt/le/eq/ge/gt` und das Verknüpfen mit dem Logikoperator `and` unterstützt. Dort können diese einem Anfangs- und/oder Enddatum zugeordnet werden.
2.  `maxhistorydays` wird als benutzerdefinierte Abfrageoption bereitgestellt.<br>

## <a name="filter-examples"></a>Filterbeispiele

> [!NOTE]
> In den Filterbeispielen wird davon ausgegangen, dass heute der 21.02.2018 ist.

|                             Filter                             |           Leistungsoptimierung           |                                          Beschreibung                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    Vollständig                                      |    Gibt Daten mit `DateKey` zwischen 20180214 und 20180221 zurück.                                     |
|    `$filter=DateKey eq 20180214`                                 |    Vollständig                                      |    Gibt Daten mit `DateKey` gleich 20180214 zurück.                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    Vollständig                                      |    Gibt Daten mit `DateKey` zwischen 20180214 und 20180220 zurück.                                     |
|    `maxhistorydays=7&$filter=Id gt 1`                            |    Teilweise; Id größer als 1 wird nicht optimiert.    |    Gibt Daten mit `DateKey` zwischen 20180214 und 20180221, und Id ist größer als 1.             |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    Vollständig                                      |    Gibt Daten mit `DateKey` gleich 20180214 zurück. `maxhistorydays` wird ignoriert.                            |
|    `$filter=DateKey eq 20180214 and Id gt 1`                     |    Keine                                      |    Wird nicht als `DateKey`-Bereichsfilter behandelt, die Leistung wird also nicht gesteigert.                              |
|    `$filter=DateKey ne 20180214`                                 |    Keine                                      |    Wird nicht als `DateKey`-Bereichsfilter behandelt, die Leistung wird also nicht gesteigert.                              |
|    `maxhistorydays=7&$filter=DateKey eq 20180214 and Id gt 1`    |    Keine                                      |    Wird nicht als `DateKey`-Bereichsfilter behandelt, die Leistung wird also nicht gesteigert. `maxhistorydays` wird ignoriert.    |
