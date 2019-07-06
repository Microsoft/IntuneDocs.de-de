---
title: Endpunkt der Intune Data Warehouse-API
titleSuffix: Microsoft Intune
description: Dieses Referenzthema beschreibt die URL-Struktur der Microsoft Intune-Data Warehouse-API. Es werden Beispiele für Filter bereitgestellt.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 38e24bff110cea7d7a565ca00fc0e3e13e37744f
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530762"
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
| api-version | Beta | Die Version ist die Version der API, auf die zugegriffen wird. Weitere Informationen finden Sie unter [Version](reports-api-url.md#api-version-information). |
| maxhistorydays | 7 | (Optional) Die maximale Anzahl an Tagen des Verlaufs, die abgerufen werden soll Dieser Parameter kann für jede Sammlung bereitgestellt werden, hat jedoch nur bei Sammlungen einen Effekt, deren Schlüsseleigenschaft `dateKey` enthält. Weitere Informationen finden Sie unter [DateKey Range Filters (DateKey-Bereichsfilter)](reports-api-url.md#datekey-range-filters). |

## <a name="api-version-information"></a>Information zur API-Version

Jetzt können Sie die Version v1.0 von Intune Data Warehouse durch Festlegen des Abfrageparameters  `api-version=v1.0`verwenden. Updates von Sammlungen in Data Warehouse bauen aufeinander auf und beschädigen keine vorhandenen Szenarios.

Sie können die neuesten Funktionen des Data Warehouse mithilfe der Betaversion ausprobieren. Für die Verwendung die Betaversion muss Ihre URL den Abfrageparameter  `api-version=beta` enthalten. Die Betaversion bietet Features, bevor sie als unterstützter Dienst allgemein verfügbar gemacht werden. Da Intune kontinuierlich neue Features hinzufügt, könnten sich in der Betaversion Verhalten und Datenverträge ändern. Benutzerdefinierter Code oder Berichtstools, die von der Betaversion abhängig sind, könnten mit laufenden Updates nicht mehr funktionieren.

## <a name="odata-query-options"></a>OData-Abfrageoptionen

Die aktuelle Version unterstützt die OData-Abfrageparameter `$filter`, `$select`, `$skip,` und `$top`. In `$filter` kann nur `DateKey` oder `RowLastModifiedDateTimeUTC` unterstützt werden, wenn die Spalten in Frage kommen und andere Eigenschaften eine fehlerhafte Anforderung auslösen würden.

## <a name="datekey-range-filters"></a>DateKey-Bereichsfilter

`DateKey`-Bereichsfilter können verwendet werden, um die Menge der Daten zu begrenzen, die für einige der Sammlungen mit `dateKey` als Schlüsseleigenschaft heruntergeladen werden sollen. Der `DateKey`-Filter kann verwendet werden, um die Leistung des Diensts zu optimieren, indem folgende `$filter`-Abfrageparameter bereitgestellt werden:

1. Nur `DateKey` in `$filter`. Dadurch werden die Operatoren `lt/le/eq/ge/gt` und das Verknüpfen mit dem Logikoperator `and` unterstützt. Dort können diese einem Anfangs- und/oder Enddatum zugeordnet werden.
2. `maxhistorydays` wird als benutzerdefinierte Abfrageoption bereitgestellt.<br>

## <a name="filter-examples"></a>Filterbeispiele

> [!NOTE]
> In den Filterbeispielen wird davon ausgegangen, dass heute der 21.02.2019 ist.

|                             Filter                             |           Leistungsoptimierung           |                                          Beschreibung                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    Vollständig                                      |    Gibt Daten mit `DateKey` zwischen 20180214 und 20180221 zurück.                                     |
|    `$filter=DateKey eq 20180214`                                 |    Vollständig                                      |    Gibt Daten mit `DateKey` gleich 20180214 zurück.                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    Vollständig                                      |    Gibt Daten mit `DateKey` zwischen 20180214 und 20180220 zurück.                                     |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    Vollständig                                      |    Gibt Daten mit `DateKey` gleich 20180214 zurück. `maxhistorydays` wird ignoriert.                            |
|    `$filter=RowLastModifiedDateTimeUTC ge 2018-02-21T23:18:51.3277273Z`                                |    Vollständig                                       |    Rückgabedaten, bei denen `RowLastModifiedDateTimeUTC` größer oder gleich `2018-02-21T23:18:51.3277273Z` ist                             |
