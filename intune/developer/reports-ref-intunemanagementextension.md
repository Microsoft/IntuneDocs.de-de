---
title: Die Entität „IntuneManagementExtension“
titleSuffix: Microsoft Intune
description: Referenzthema für die Entitätskategorie „IntuneManagementExtension“ von Entitätensammlungen in der Intune Data Warehouse-API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2efddc75c5819a25d9ba097cb24726e80df14f2
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654191"
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

