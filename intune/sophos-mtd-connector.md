---
title: Einrichten der Sophos Mobile-Integration in Intune
titleSuffix: Intune on Azure
description: Einrichten der Sophos Mobile-Lösung in Microsoft Intune, um den Zugriff mobiler Geräte auf Ihre Unternehmensressourcen zu steuern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 550dfe58687806f7ead65dab2d7e15b310ae4b6e
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044041"
---
# <a name="sophos-mobile-threat-defense-connector-with-intune"></a>Sophos Mobile Threat Defense-Connector mit Intune
Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen mithilfe des bedingten Zugriffs auf Risikobewertungen steuern, die von Sophos Mobile vorgenommen werden, einer Mobile Threat Defense-Lösung (MTD), die in Microsoft Intune integriert werden kann. Das Risiko wird basierend auf Telemetriedaten von Geräten bewertet, auf denen die Sophos Mobile-App ausgeführt wird.
Sie können Richtlinien für bedingten Zugriff basierend auf der Sophos Mobile-Risikobewertung konfigurieren, die über Intune-Gerätekompatibilitätsrichtlinien aktiviert wird, und so anhand der erkannten Bedrohungen den Zugriff auf Unternehmensressourcen durch nicht konforme Geräte zulassen oder blockieren.

## <a name="how-do-intune-and-sophos-mobile-help-protect-your-company-resources"></a>Wie helfen Intune und Sophos Mobile beim Schutz von Unternehmensressourcen?
Die Sophos Mobile-App für Android oder iOS erfasst Telemetriedaten des Dateisystems, Netzwerkstapels sowie von Geräten und Anwendungen (sofern verfügbar), und sendet diese dann an den Sophos Mobile-Clouddienst, mit dessen Hilfe die Anfälligkeit des Geräts für mobile Bedrohungen bewertet wird.
Die Intune-Gerätekonformitätsrichtlinie enthält eine Regel für Sophos Mobile Threat Defense, die auf der Sophos Mobile-Risikobewertung basiert. Wenn diese Regel aktiviert ist, bewertet Intune die Gerätekompatibilität mit der von Ihnen aktivierten Richtlinie. Wird das Gerät als nicht kompatibel eingestuft, wird der Zugriff auf Ressourcen wie Exchange Online und SharePoint Online für Benutzer blockiert. Benutzer erhalten außerdem einen Leitfaden von der auf ihren Geräten installierten Sophos Mobile-App, um das Problem zu beheben und den Zugriff auf Unternehmensressourcen zurückzuerlangen.  

## <a name="sample-scenarios"></a>Beispielszenarien
Es folgen einige gängige Szenarios.  
### <a name="control-access-based-on-threats-from-malicious-apps"></a>Steuern des Zugriffs basierend auf Bedrohungen durch Apps, die Schadsoftware enthalten
Wenn Apps, die Schadsoftware enthalten, auf Geräten erkannt werden, können Sie Geräte an folgenden Aktionen hindern, bis die Bedrohung beseitigt ist:
- Herstellen einer Verbindung mit Unternehmens-E-Mail
- Synchronisieren von Unternehmensdateien mithilfe der OneDrive for Work-App
- Zugreifen auf Unternehmens-Apps

**Blockieren, wenn Apps mit Schadsoftware erkannt werden**:
 
![Darstellung des Szenarios, wenn Apps mit Schadsoftware erkannt werden](./media/sophos-mtd-connector/sophos_malicious_apps_blocked.png)  

**Zugriff erteilt nach der Behebung**:  
![Darstellung des Szenarios, wenn der Zugriff nach der Behebung wieder erteilt wird](./media/sophos-mtd-connector/sophos_malicious_apps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Steuern des Zugriffs basierend auf der Bedrohung für das Netzwerk  
Erkennen von Bedrohungen wie Man-in-the-Middle-Angriffe für Ihr Netzwerk und Schützen des Zugriffs auf WLAN-Netzwerke basierend auf dem Geräterisiko.  

**Blockieren des Netzwerkzugriffs über WLAN**:  
![Blockieren des Netzwerkzugriffs über WLAN](./media/sophos-mtd-connector/sophos_network_wifi_blocked.png)

**Zugriff erteilt nach der Behebung**:   
![Zugriff erteilt nach der Behebung](./media/sophos-mtd-connector/sophos_network_wifi_unblocked.png)  

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Steuern des Zugriffs auf SharePoint Online basierend auf der Bedrohung für das Netzwerk  
Erkennen von Bedrohungen wie Man-in-the-Middle-Angriffe für Ihr Netzwerk und Verhindern der Synchronisierung von Unternehmensdateien basierend auf dem Geräterisiko.  

**Blockieren von SharePoint Online bei Erkennung von Bedrohungen für das Netzwerk**:   
![Blockieren von SharePoint Online bei Erkennung von Bedrohungen für das Netzwerk](./media/sophos-mtd-connector/sophos_network_spo_blocked.png)  

**Zugriff erteilt nach der Behebung**:  
![Zugriff erteilt nach der Behebung für SharePoint – Beispiel](./media/sophos-mtd-connector/sophos_network_spo_unblocked.png)  

## <a name="supported-platforms"></a>Unterstützte Plattformen  
- Android 5.0 und höher
- iOS 11.0 und höher

## <a name="prerequisites"></a>Voraussetzungen  
- Azure Active Directory Premium
- Microsoft Intune-Abonnement 
- Sophos Mobile Threat Defense-Abonnement

Weitere Informationen finden Sie auf der [Sophos-Website](https://www.sophos.com/products/mobile-control).  

## <a name="next-steps"></a>Nächste Schritte  
- [Integrieren von Sophos in Intune](sophos-mtd-connector-integration.md)
- [Einrichten von Sophos-Apps](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Erstellen einer Konformitätsrichtlinie für Sophos-Geräte](mtd-device-compliance-policy-create.md)
- [Aktivieren des Sophos MTD-Connectors](mtd-connector-enable.md)
