---
title: Datensicherheit und -freigabe in Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie mehr darüber, wie personenbezogene Daten in Intune gesichert und freigegeben werden.
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
ms.assetid: 68921fd6-5f50-456c-a3af-83d7bc4b134b
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b17b87462b2c73e265f062c33a06a810e7c58bf8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504330"
---
# <a name="data-security-and-sharing-in-intune"></a>Datensicherheit und -freigabe in Intune


## <a name="data-security"></a>Datensicherheit

Microsoft Intune ist eine wichtige Komponente des Clouddienstangebots Microsoft Enterprise Mobility and Security Suite. Alle Microsoft Cloud Services werden mit den Methoden [Microsoft Privacy](https://www.microsoft.com/en-us/trustcenter/privacy) und [Microsoft Security](https://www.microsoft.com/en-us/trustcenter/security/) entwickelt, um die [Strategie zur Datenkontrolle](https://www.microsoft.com/en-us/TrustCenter/Security/default.aspx) zu unterstützen.  

Für Microsoft Intune werden die gleichen technischen und organisatorischen Maßnahmen wie bei Microsoft Azure ergriffen, um den Dienst gegen Datenschutzverletzungen zu sichern.

Weitere Informationen finden Sie im [Service Trust Portal](https://www.microsoft.com/en-us/TrustCenter/stp).

Intune verwendet beispielsweise folgende Techniken zur Datenminimierung:

- aggregation
- Optionale Datensammlung für einige Features
- Weniger präzise oder vertrauliche Daten

Intune verwendet ebenfalls Techniken wie RBAC und JIT-Sicherheit für Supportincidents, um den Datenschutz standardmäßig sicherzustellen. 

### <a name="data-breach-reporting"></a>Melden von Datenschutzverletzungen

Wenn ein Sicherheitsincident identifiziert wird, der den Kunden gemeldet werden sollte, werden diese darüber benachrichtigt. Dieser Prozess umfasst die Zusammenarbeit mit dem Microsoft Office 365-Team, um Benachrichtigungen über Datenschutzverletzungen mithilfe von Intune an alle Microsoft Office 365-Kunden zu übermitteln.

## <a name="data-sharing"></a>Datenfreigabe

Wenn Mandantenadministratoren bestimmte Funktionen aktivieren (z.B. das Apple-Programm zur Geräteregistrierung), erhält Microsoft Intune die Zustimmung des Administrators zum Freigeben von Daten an entsprechende Drittanbieter. In solchen Fällen kann Intune personenbezogene Daten für folgende Drittanbieter freigeben:

- Drittanbieter, die im Auftrag von Microsoft handeln.
- Drittanbieter, die nicht im Auftrag von Microsoft handeln, wenn Mandantenadministratoren Intune explizit die Berechtigung hierfür erteilen.

Alle Drittanbieter, die im Auftrag von Microsoft handeln, werden auf der [Liste der Onlinedienst-Zulieferer](https://aka.ms/Online_Serv_Subcontractor_List) aufgeführt.

Das Freigeben von Daten für diese Drittanbieter soll den technischen Support und den Kundensupport, die Wartung von Diensten und andere Vorgänge unterstützen.

Der Vertrag eines Mandanten mit dem Drittanbieter regelt den Umgang mit den personenbezogenen Intune-Daten, die im Drittanbieterdienst vorhanden sind. Dieser erteilt Intune ebenfalls die Berechtigung, Daten an den Drittanbieterdienst zu übertragen.  

Weitere Informationen zu für Drittanbieter freigegebenen Daten finden Sie in folgenden Artikeln:
- [Von Intune an Apple gesendete Daten](data-intune-sends-to-apple.md)
- [Von Intune an Google gesendete Daten](data-intune-sends-to-google.md)
- [Von Apple an Intune gesendete Daten](data-apple-sends-to-intune.md)
- [Von Google an Intune gesendete Daten](data-google-sends-to-intune.md)
- [Data Jamf Pro sends to Intune (Von Jamf Pro an Intune gesendete Daten)](data-jamf-sends-to-intune.md)

### <a name="system-center-configuration-manager-data-sharing"></a>Freigeben von Daten für System Center Configuration Manager

Microsoft Intune gibt keine Daten für System Center Configuration Manager frei. System Center Configuration Manager ist ein lokales Produkt, das direkt vom Kunden bereitgestellt, verwaltet und betrieben wird. Die Diagnose- und Nutzungsdaten, die von Configuration Manager gesammelt werden, dienen ausschließlich zur Verbesserung der Installation, der Qualität und der Sicherheit von zukünftigen Releases.

Weitere Informationen finden Sie unter [Diagnose- und Nutzungsdaten für System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data). 


## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr darüber, wie personenbezogene Daten in Intune [angezeigt und korrigiert](privacy-data-view-correct.md) werden.
