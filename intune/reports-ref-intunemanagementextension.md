---
title: Die Entität „IntuneManagementExtension“
titleSuffix: Microsoft Intune
description: Referenzthema für die Entitätskategorie „IntuneManagementExtension“ von Entitätensammlungen in der Intune Data Warehouse-API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 70802626c79f11748e81c39afdd8bc8c5d0622b3
ms.sourcegitcommit: c3ac858bbadb63d248ed54069e48160d703bbaf2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2019
ms.locfileid: "68313775"
---
# <a name="reference-for-intune-management-extensions"></a>Verweis für die Intune-Verwaltungserweiterungen

Die Kategorie **intuneManagementExtensions** enthält Entitäten für mobile Geräte zur Nachverfolgung von Informationen wie etwa der folgenden:

- Versionen einer IntuneManagementExtension
- Installationsstatus einer IntuneManagementExtension

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions

Die Entität **intuneManagementExtensionVersion** listet alle von intuneManagementExtensions verwendeten Versionen auf.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| extensionVersionKey |Eindeutiger Bezeichner für die intuneManagementExtensions-Version. | 1 |
| extensionVersion |Die vierstellige Versionsnummer |1.0.2.0 |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates

**intuneManagementExtensionHealthState** listet alle möglichen Status der intuneManagementExtensions auf.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| extensionStateKey |Eindeutiger Bezeichner des Integritätszustands | 2 |
| extensionState |Der Integritätsstatus einer IntuneManagementExtension | Healthy |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions

Die **intuneManagementExtensions** listet täglich den Integritätsstatus von intuneManagementExtension auf jedem Windows 10-Gerät auf.
Die Daten der letzten 60 Tage werden aufbewahrt. 


|      Eigenschaft       |                         Beschreibung                         | Beispiel |
|---------------------|-------------------------------------------------------------|---------|
|       dateKey       |               Eindeutiger Datumsbezeichner                |   123   |
|      tenantKey      |              Eindeutiger Mandantenbezeichner               |   456   |
|      deviceKey      |              Eindeutiger Bezeichner des Geräts               |   789   |
| extensionVersionKey | Eindeutiger Bezeichner für die intuneManagementExtension-Version. |    1    |
|  extensionStateKey  |             Eindeutiger Bezeichner des Integritätszustands              |    2    |

