---
title: Die Entität „IntuneManagementExtension“
titleSuffix: Microsoft Intune
description: Referenzthema für die Entitätskategorie „IntuneManagementExtension“ von Entitätensammlungen in der Intune Data Warehouse-API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2019
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
ms.openlocfilehash: ebece46bac8ebee5cb3c6a573f0b09c4b308abe3
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66040986"
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

