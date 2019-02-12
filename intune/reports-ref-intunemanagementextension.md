---
title: Die Entität „IntuneManagementExtension“
titlesuffix: Microsoft Intune
description: Referenzthema für die Entitätskategorie „IntuneManagementExtension“ von Entitätensammlungen in der Intune Data Warehouse-API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0df0d97b41933f316db788fd0af09ba75196549b
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836868"
---
# <a name="reference-for-intune-management-extension"></a>Referenz für die Intune-Verwaltungserweiterung

Die Kategorie **IntuneManagementExtension** enthält Entitäten für mobile Geräte zur Nachverfolgung von Informationen wie etwa der folgenden:

  -  Versionen einer IntuneManagementExtension
  -  Installationsstatus einer IntuneManagementExtension

## <a name="intunemanagementextensionversion"></a>IntuneManagementExtensionVersion

Die Entität **IntuneManagementExtensionVersion** listet alle von IntuneManagementExtension verwendeten Versionen auf.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| ExtensionVersionKey |Eindeutiger Bezeichner für die IntuneManagementExtension-Version. | 1 |
| ExtensionVersion |Die vierstellige Versionsnummer |1.0.2.0 |

## <a name="intunemanagementextensionhealthstate"></a>IntuneManagementExtensionHealthState

**IntuneManagementExtensionHealthState** listet alle möglichen Status der IntuneManagementExtension auf.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| ExtensionStateKey |Eindeutiger Bezeichner des Integritätszustands | 2 |
| ExtensionState |Der Integritätsstatus einer IntuneManagementExtension | Healthy |

## <a name="intunemanagementextension"></a>IntuneManagementExtension

Die **IntuneManagementExtension** listet täglich den Integritätsstatus von IntuneManagementExtension auf jedem Windows 10-Gerät auf.
Die Daten der letzten 60 Tage werden aufbewahrt. 


|      Eigenschaft       |                         Beschreibung                         | Beispiel |
|---------------------|-------------------------------------------------------------|---------|
|       DateKey       |               Eindeutiger Datumsbezeichner                |   123   |
|      TenantKey      |              Eindeutiger Mandantenbezeichner               |   456   |
|      DeviceKey      |              Eindeutiger Bezeichner des Geräts               |   789   |
| ExtensionVersionKey | Eindeutiger Bezeichner für die IntuneManagementExtension-Version. |    1    |
|  ExtensionStateKey  |             Eindeutiger Bezeichner des Integritätszustands              |    2    |

