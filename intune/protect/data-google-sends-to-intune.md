---
title: Von Google an Intune gesendete Daten
titleSuffix: Microsoft Intune
description: Liste der Daten, die von Google an Intune gesendet werden.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c379c8db-788a-454e-9098-665ea3bc7b56
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 914ce3aa15099b7692d524dbfa368f99f0d092e8
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504489"
---
# <a name="data-google-sends-to-intune"></a>Von Google an Intune gesendete Daten

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Wenn die Android-Geräteverwaltung für Unternehmen auf einem Gerät installiert ist, richtet Microsoft Intune eine Verbindung mit Google ein, und es werden Benutzer- und Geräteinformationen zwischen Intune und Google freigegeben. Damit Microsoft Intune eine Verbindung einrichten kann, müssen Sie zunächst ein Google-Konto erstellen.

In der folgenden Tabelle sind die Daten aufgeführt, die Google an Intune versendet, wenn auf einem Gerät die Geräteverwaltung aktiviert ist:


| Von Google an Intune gesendete Daten | Details | Verwendet für | Beispiel |
|:---:|:---:|:---:|:---:|
| Unternehmensdaten | Unternehmens-IDs des Kunden in Google. | Verknüpft die Kundeninformationen zwischen Intune und Google. | **enterpriseId** Beispiel: LC04eik8a6.<br>**Name**. Der Administratorname, wie bei der Konfiguration von Android für das Unternehmen eingegeben. Beispiel: Joe Smith<br>**Administrator-E-Mail-Adresse**. YourAdmin@gmail.com, die bei der Konfiguration von Android für das Unternehmen verwendet wurde. |
| Anwendungsdaten | Daten für verwaltete Play Store-Anwendungen. | Zuordnen der Anwendung zu Benutzern und Geräten wie verfügbar oder erforderlich. | **Anwendungsname** – Beispiel: Contoso Warehouse Inventory Application<br>**Eindeutiger Bezeichner zur Darstellung der Anwendung** – Beispiel: app:com.Contoso.Warehouse.InventoryTracking |
| Dienstkonto | Eindeutiges internes Google-Dienstkonto für die Verwendung bei bestimmten Kundenanrufen. | Wird für Anrufe in Google im Namen des Kunden verwendet (zum Anzeigen von Apps, Geräten und mehr). | **Name** – Beispiel: InternalAccount@InternalService.com.<br>**Schlüssel** – Beispiel: ServiceAccountPassword |


Wenn Sie die Android-Geräteverwaltung für Unternehmen mit Microsoft Intune nicht mehr verwenden und die Daten löschen möchten, müssen Sie die Microsoft Intune Android-Geräteverwaltung für Unternehmen und das Google-Konto löschen. Informationen zur Kontenverwaltung in der Dokumentation zum Google-Konto.


