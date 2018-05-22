---
title: Endpunkt der Intune Data Warehouse-API
titlesuffix: Microsoft Intune
description: Das Referenzthema beschreibt die URL-Struktur der Intune Data Warehouse-API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6f99ce2ae7937fe0b90353037e72f453a703dd8c
ms.sourcegitcommit: 49dc405bb26270392ac010d4729ec88dfe1b68e4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2018
---
# <a name="intune-data-warehouse-api-endpoint"></a>Endpunkt der Intune Data Warehouse-API

Sie können die Intune-Data Warehouse-API mit einem Konto mit bestimmten rollenbasierten Zugriffssteuerungen und Azure AD-Anmeldeinformationen verwenden. Anschließend autorisieren Sie Ihren REST-Client mithilfe von OAuth 2.0 für Azure AD. Schließlich erstellen Sie eine aussagekräftige URL, um eine Data Warehouse-Ressource aufzurufen.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="authorization"></a>Autorisierung

Azure Active Directory (Azure AD) bietet Ihnen über OAuth 2.0 die Möglichkeit, den Zugriff auf Webanwendungen und Web-APIs in Ihrem Azure AD-Mandanten zu autorisieren. Dieses Handbuch ist sprachenunabhängig und beschreibt, wie HTTP-Nachrichten gesendet und empfangen werden können, ohne irgendeine unserer Open Source-Bibliotheken zu verwenden. Der Codefluss zur Autorisierung mit OAuth 2.0 wird in [section 4.1 (Abschnitt 4.1)](https://tools.ietf.org/html/rfc6749#section-4.1) der OAuth 2.0-Spezifikation beschrieben.

Weitere Informationen finden Sie unter [Authorize access to web applications using OAuth 2.0 and Azure Active Directory (Autorisieren des Zugriffs zu Webanwendungen mithilfe von OAuth 2.0 und Azure Active Directory)](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).

## <a name="api-url-structure"></a>API-URL-Struktur

Die Endpunkte der Data Warehouse-API lesen die Entitäten für jeden Satz. Die API unterstützt ein **GET** HTTP-Verb und eine Teilmenge der Abfrageoptionen.

Die URL für Intune verwendet das folgende Format:  
`https://fef.{<strong><em>location</em></strong>}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{<strong><em>entity-collection</em></strong>}?api-version={<strong><em>api-version</em></strong>}`

Die URL enthält die folgenden Elemente:

| Element | Beispiel | Beschreibung |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| location | msua06 | Die Basis-URL kann im Blatt „Data Warehouse API“ im Azure Portal gefunden werden. |
| Entitätssammlung | Daten | Der Name der OData-Entitätssammlung. Weitere Informationen zu Sammlungen und Entitäten im Datenmodell finden Sie unter [Data Model (Datenmodell)](reports-ref-data-model.md). |
| api-version | Beta | Die Version ist die Version der API, auf die zugegriffen wird. Weitere Informationen finden Sie unter [Version](#API-version-information). |


## <a name="api-version-information"></a>Information zur API-Version

Die aktuelle Version der API ist `beta`. 

## <a name="odata-query-options"></a>OData-Abfrageoptionen

Die aktuelle Version unterstützt die OData-Abfrageparameter `$filter, $orderby, $select, $skip,` und `$top`.
