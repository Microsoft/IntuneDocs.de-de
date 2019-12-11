---
title: Datenspeicherung und -verarbeitung in Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie mehr darüber, wie personenbezogene Daten in Intune gespeichert und verarbeitet werden.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: edb07842-6a16-482e-8c1d-541a29e169a8
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 07a9232203c7d93eb1b9e81b962d2369e77b7421
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72509050"
---
# <a name="data-storage-and-processing-in-intune"></a>Datenspeicherung und -verarbeitung in Intune

Nachdem Intune die [Daten sammelt](privacy-data-collect.md), werden sie wie im Folgenden beschrieben gespeichert und verarbeitet.

## <a name="storing-personal-data"></a>Speichern von personenbezogenen Daten

Alle Daten, bei denen es sich nicht um Telemetriedaten handelt, werden vom Intune-Dienst verarbeitet und an einem oder mehreren der folgenden Speicherorte gespeichert: 

- SQLAzure 
- Zuverlässige Sammlungen (Service Fabric)  
- Azure Storage 

Telemetriedaten (Dienstprotokolle, Leistungsprotokolle, Fehler usw.), die wichtig für die Überwachung und die Stabilität von Diensten sind, werden an die Microsoft-Telemetriedatenspeicher gesendet.

### <a name="storage-locations"></a>Speicherorte

Microsoft betreibt Intune-Dienste in vielen Regionen weltweit. Intune berücksichtigt die Auswahl des Speicherorts, die vom Administrator für Kundendaten festgelegt wurde.

Weitere Informationen finden Sie unter [Wo wir Ihre Daten speichern](https://www.microsoft.com/trust-center/privacy/data-location).

### <a name="personal-data-retention"></a>Aufbewahrung personenbezogener Daten

Im Allgemeinen werden personenbezogene Daten von Intune noch bis zu 30 Tage aufbewahrt, nachdem der Benutzer aus der Intune-Verwaltung entfernt wurde.

Telemetriedaten, die durch die Verwendung von Intune gesammelt wurden, werden bis zu 30 Tage aufbewahrt.

Überwachungsprotokolle werden bis zu einem Jahr aufbewahrt.

## <a name="processing-personal-data"></a>Verarbeiten von personenbezogenen Daten

Intune verarbeitet personenbezogene Daten mit ISO-zertifizierten Systemen. Weitere Informationen finden Sie im [Service Trust Portal](https://www.microsoft.com/en-us/TrustCenter/stp).

### <a name="profiling-and-marketing"></a>Profilerstellung und Marketing

Microsoft Intune verwendet keine personenbezogenen Daten, die durch den Dienst gesammelt wurden, für Profilerstellungs- oder Marketingzwecke. 

### <a name="restrict-processing-of-personal-data"></a>Einschränken der Verarbeitung von personenbezogenen Daten

Wenn Sie die Verarbeitung der personenbezogenen Daten eines Benutzers einschränken möchten, können Sie dessen Konto löschen, indem Sie Folgendes durchführen:
1. Exportieren Sie eine elektronische Kopie der personenbezogenen Daten des Benutzers. Dazu zählen:
    - Konten
    - Dienstdaten
    - Zugeordnete Protokolle
2. Löschen Sie das Konto des Benutzers und die zugehörigen Daten aus Intune.

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr darüber, wie Intune personenbezogene Daten [sichert und freigibt](privacy-data-secure-share.md). 
