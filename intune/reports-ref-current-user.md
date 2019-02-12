---
title: Aktueller Benutzer – Intune Data Warehouse
titlesuffix: Microsoft Intune
description: Referenzthema für die Kategorie „Aktueller Benutzer“ der Entitätssammlungen in der Intune-Data Warehouse-API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: C10E6752-E925-40AD-ABBF-6B621FB7AFC4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9fdd1891f8a0e893d61ac3a0b40dac5a01f602c
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55851337"
---
# <a name="reference-for-current-user-entity"></a>Verweis für die Entität „Aktueller Benutzer“

Die Kategorie **Aktueller Benutzer** enthält die Benutzereigenschaften im Datenmodell. Die Entitätssammlung **Aktueller Benutzer** ist auf die derzeit aktiven Benutzer begrenzt. Die Entität enthält alle Azure Active Directory-Benutzer, denen derzeit eine Lizenz zugewiesen ist. Bei der Lizenz kann es sich um eine Intune-Lizenz, eine Hybrid-Lizenz oder eine Microsoft Office 365-Lizenz handeln. Wenn ein Benutzer entfernt wurde, wird er nicht in der Sammlung „Aktueller Benutzer“ dargestellt. Eine Sammlung mit dem Änderungsverlauf der Benutzerzustände finden Sie unter [Referenz für die Entität „Benutzer“](reports-ref-user.md).


## <a name="current-user"></a>Aktueller Benutzer

Die Entität **Aktueller Benutzer** listet alle Benutzer von Azure Active Directory (Azure AD) mit zugewiesenen Lizenzen in Ihrem Unternehmen auf.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| UserKey |Eindeutiger Bezeichner des Benutzers im Data Warehouse – Ersatzschlüssel |123 |
| UserId |Eindeutiger Bezeichner des Benutzers – Ähnlich wie UserKey, ist jedoch ein natürlicher Schlüssel |b66bc706-ffff-7437-0340-032819502773 |
| UserEmail |E-Mail-Adresse des Benutzers |John@constoso.com |
| UPN | Benutzerprinzipalname des Benutzers | John@constoso.com |
| DisplayName |Anzeigename des Benutzers |John |
| IntuneLicensed |Gibt an, ob dieser Benutzer über Intune lizenziert ist oder nicht. |Wahr/falsch |
| StartDateInclusiveUTC |Datum und Uhrzeit in UTC, als der Benutzer im Data Warehouse erstellt wurde |23.11.2016 12:00:00 Uhr |
| RowLastModifiedDateTimeUTC |Datum und Uhrzeit in UTC, als dieser Benutzer das letzte Mal im Data Warehouse geändert wurde |23.11.2016 12:00:00 Uhr |

## <a name="next-steps"></a>Nächste Schritte
 - Sie können die Entitätssammlung **Benutzer** verwenden, um die Benutzerdaten auf Benutzer auszuweiten, die derzeit nicht aktiv sind. Weitere Informationen finden Sie unter [Referenz für die Entität „Benutzer“](reports-ref-user.md).
 - Informationen zur Nachverfolgung der Benutzerlebensdauer über das Data Warehouse in Intune finden Sie unter [Darstellung der Benutzerlebensdauer im Intune Data Warehouse](reports-ref-user-timeline.md).
