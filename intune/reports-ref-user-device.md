---
title: Zuordnung von Benutzergeräten – Intune Data Warehouse
titlesuffix: Microsoft Intune
description: Die Entität „UserDeviceAssociation“ enthält Zuordnungen von Benutzergeräten in Ihrer Organisation.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 777484A7-09CE-4409-987F-76B3F87DFE93
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.openlocfilehash: 02c579a7371a59a46cfb0017e6aa1a17af92bd03
ms.sourcegitcommit: 1c9ef5cfac2fc024528d2cfc9d590fa68dd58080
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53429558"
---
# <a name="reference-for-user-device-association-entity"></a>Verweis für die Entität „Benutzergerätezuordnung“

Die Entität **UserDeviceAssociation** enthält Zuweisungen von Benutzergeräten in Ihrer Organisation.

## <a name="userdeviceassociation"></a>UserDeviceAssociation


|        Name        |                                           Beschreibung                                            |        Beispiel         |
|--------------------|--------------------------------------------------------------------------------------------------|------------------------|
|      UserKey       |              Eindeutiger Bezeichner für den Benutzer im Data Warehouse (Ersatzschlüssel)               |          123           |
|     DeviceKey      |                      Eindeutiger Bezeichner für das Gerät im Data Warehouse                      |          123           |
| CreatedDateTimeUTC |           Datum und Uhrzeit, als die Benutzergerätezuordnung erstellt wurde Verwendet UTC-Format           | 23.11.2016 12:00:00 Uhr |
|     isDeleted      | Gibt an, dass der Benutzer dieses Geräts die Registrierung aufgehoben hat und die Zuordnung nicht mehr aktuell ist |       Wahr/falsch       |
|  EndedDateTimeUTC  |              Datum und Uhrzeit in UTC, als IsDeleted in <strong>TRUE</strong> geändert wurde               | 23.06.2017, 12:00:00 Uhr |

## <a name="next-steps"></a>Nächste Schritte

- Erfahren Sie mehr über das [Data Warehouse von Intune](reports-nav-create-intune-reports.md).