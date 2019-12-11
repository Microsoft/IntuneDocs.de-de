---
title: Zuordnung von Benutzergeräten – Intune Data Warehouse
titleSuffix: Microsoft Intune
description: Die Entität „UserDeviceAssociation“ enthält Zuordnungen von Benutzergeräten in Ihrer Organisation.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7f04575ce32d3d02a1869ed8c3225905b9e6b7dc
ms.sourcegitcommit: 7cc45ef52dda08479bc6bdff7d11d2f6c0e7b93b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/06/2019
ms.locfileid: "74899270"
---
# <a name="reference-for-user-device-association-entity"></a>Verweis für die Entität „Benutzergerätezuordnung“

Die Entität **userDeviceAssociation** enthält Zuordnungen von Benutzergeräten in Ihrer Organisation.

## <a name="userdeviceassociations"></a>userDeviceAssociations


|        Name        |                                           Beschreibung                                            |        Beispiel         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      userKey       |              Eindeutiger Bezeichner für den Benutzer im Data Warehouse (Ersatzschlüssel)               |          123           |
|     deviceKey      |                      Eindeutiger Bezeichner für das Gerät im Data Warehouse                      |          123           |
| CreatedDateTimeUTC |           Datum und Uhrzeit, als die Benutzergerätezuordnung erstellt wurde Verwendet UTC-Format           | 23.11.2016 12:00:00 Uhr |
|     isDeleted      | Gibt an, dass der Benutzer dieses Geräts die Registrierung aufgehoben hat und die Zuordnung nicht mehr aktuell ist |       Wahr/falsch       |
|  EndedDateTimeUTC  |              Datum und Uhrzeit in UTC, als IsDeleted in <strong>TRUE</strong> geändert wurde               | 23.06.2017, 12:00:00 Uhr |

## <a name="next-steps"></a>Nächste Schritte

- Erfahren Sie mehr über das [Data Warehouse von Intune](../reports-nav-create-intune-reports.md).
