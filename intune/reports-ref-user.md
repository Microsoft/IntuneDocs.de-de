---
title: Benutzer | Microsoft-Dokumentation
description: "Referenzthema für die Kategorie „Benutzer“ der Entitätsauflistungen in der Intune Data Warehouse-API."
keywords: Intune Data Warehouse
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: C29A6EEA-72B7-427E-9601-E05B408F3BB0
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2b9739299c52c668117116f54c08715f1218d130
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2017
---
# <a name="reference-for-user-entity"></a>Verweis für die Benutzerentität

Die Kategorie **User** (Benutzer) enthält die Entität **User** (Benutzer), die die Eigenschaften von Benutzern und Agents im Datenmodell definiert.

**Benutzer**

Die Entität **User** (Benutzer) listet alle Benutzer von Azure Active Directory (Azure AD) mit zugewiesenen Lizenzen in Ihrem Unternehmen auf.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| UserKey |Eindeutiger Bezeichner des Benutzers im Data Warehouse – Ersatzschlüssel |123 |
| UserId |Eindeutiger Bezeichner des Benutzers. Ähnlich wie UserKey, ist jedoch ein natürlicher Schlüssel |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |E-Mail-Adresse des Benutzers |John@constoso.com |
| DisplayName |Anzeigename des Benutzers |John |
| IntuneLicensed |Gibt an, ob dieser Benutzer über Intune lizenziert ist oder nicht. |Wahr/falsch |
| isDeleted |Gibt an, ob dieser Benutzerdatensatz aktualisiert wurde.  Wahr: Dieser Benutzer verfügt über einen neuen Datensatz mit aktualisierten Feldern in dieser Tabelle. Falsch: der neueste Datensatz für diesen Benutzer. |Wahr/falsch |
| StartDateInclusiveUTC |Datum und Uhrzeit in UTC, als dieser Benutzer im Data Warehouse erstellt wurde |23.11.2016 12:00:00 Uhr |
| EndDateExclusiveUTC |Datum und Uhrzeit in UTC, wenn IsDeleted auf Wahr geändert wird |23.11.2016 12:00:00 Uhr |
| IsCurrent |Gibt an, ob dieser Benutzerdatensatz aktuell im Data Warehouse vorhanden ist oder nicht |Wahr/falsch |
| RowLastModifiedDateTimeUTC |Datum und Uhrzeit in UTC, als dieser Benutzer zuletzt im Data Warehouse geändert wurde |23.11.2016 12:00:00 Uhr |
