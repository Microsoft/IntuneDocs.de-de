---
title: Einrichten von Wandera Mobile Security in Intune
titleSuffix: Intune on Azure
description: Einrichten der Wandera Mobile Security-Lösung in Microsoft Intune, um den Zugriff mobiler Geräte auf Ihre Unternehmensressourcen zu steuern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3ee253b50ea525f7d156c77a83f486cf990da030
ms.sourcegitcommit: af384c46ec8d8def6aa32c3b89947748dc6fd28f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2020
ms.locfileid: "76517455"
---
# <a name="wandera-mobile-threat-defense-connector-with-intune"></a>Wandera Mobile Threat Defense-Connector mit Intune  

Steuern Sie den Zugriff mobiler Geräte auf Unternehmensressourcen mithilfe des bedingten Zugriffs basierend auf der Risikobewertung von Wandera. Wandera ist eine Mobile Threat Defense-Lösung (MTD), die in Microsoft Intune integriert ist.  Das Risiko wird basierend auf Telemetriedaten bewertet, die vom Wandera-Dienst auf Geräten erfasst werden, wie z.B.:
- Sicherheitsrisiken des Betriebssystems
- Installierte Apps, die Schadsoftware enthalten
- Netzwerkprofile mit böswilligen Absichten
- Cryptojacking

Sie können Richtlinien für *bedingten Zugriff* basierend auf Risikobewertungen von Wandera konfigurieren, die über Intune-Gerätekonformitätsrichtlinien aktiviert werden. Richtlinien für die Risikobewertung können den Zugriff nicht konformer Geräte auf Unternehmensressourcen basierend auf den erkannten Bedrohungen gewähren oder verweigern.  


## <a name="how-do-intune-and-wandera-mobile-threat-defense-help-protect-your-company-resources"></a>In welcher Form unterstützen Intune und Wandera Mobile Threat Defense den Schutz Ihrer Unternehmensressourcen?  

Die mobile App von Wandera lässt sich mithilfe von Microsoft Intune nahtlos installieren. Diese App erfasst Daten zum Dateisystem, Netzwerkstapel sowie Geräte- und Anwendungstelemetriedaten (sofern verfügbar). Diese Informationen werden mit dem Wandera-Clouddienst synchronisiert, um das Risiko des Geräts für mobile Bedrohungen zu bewerten. Diese Klassifizierungen der Risikostufen sind in der Wandera-Konsole RADAR nach Ihren Bedürfnissen konfigurierbar.

Die Konformitätsrichtlinie in Intune enthält eine Regel für MTD, die auf der Risikobewertung von Wandera basiert. Wenn diese Regel aktiviert ist, bewertet Intune die Gerätekompatibilität mit der von Ihnen aktivierten Richtlinie.

Für Geräte, die nicht konform sind, kann der Zugriff auf Ressourcen wie Office 365 blockiert werden. Benutzer auf blockierten Geräten erhalten Anleitungen von der Wandera-App, wie sie das Problem beheben und den Zugriff zurückzuerlangen können.

## <a name="supported-platforms"></a>Unterstützte Plattformen  

Bei Registrierung in Intune werden die folgenden Plattformen für Wandera unterstützt:

- Android 5.0 und höher  
- iOS 10.2 und höher  

Weitere Informationen zu Plattform und Gerät finden Sie auf der [Website von Wandera](https://www.wandera.com/mobile-threat-defense/).

## <a name="prerequisites"></a>Voraussetzungen  

- Microsoft Intune-Abonnement  
- Azure Active Directory  
- Wandera Mobile Threat Defense (früher Wandera Secure)  

Weitere Informationen finden Sie unter [Wandera Mobile Security](https://www.wandera.com/mobile-security/).
 
## <a name="sample-scenarios"></a>Beispielszenarios

Im Folgenden finden Sie allgemeine Szenarien für die Verwendung von Wandera MTD mit Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Steuern des Zugriffs basierend auf Bedrohungen durch Apps, die Schadsoftware enthalten  

Wenn Apps mit Schadsoftware auf Geräten erkannt werden, können Sie Geräte an gängigen Aktionen hindern, bis die Bedrohung beseitigt ist. Dazu gehören u.a.:  
- Herstellen einer Verbindung mit Unternehmens-E-Mail  
- Synchronisieren von Unternehmensdateien mithilfe der OneDrive for Work-App  
- Zugreifen auf Unternehmens-Apps  

**Blockieren, wenn Apps mit Schadsoftware erkannt werden**:

![Darstellung des Szenarios, wenn Apps mit Schadsoftware erkannt werden](./media/wandera-mtd-connector/wandera-malicious-apps-blocked.png)  

**Zugriff erteilt nach der Behebung**: 

![Darstellung des Szenarios, wenn der Zugriff nach der Behebung wieder erteilt wird](./media/wandera-mtd-connector/wandera-malicious-apps-unblocked.png)


### <a name="control-access-based-on-threat-to-network"></a>Steuern des Zugriffs basierend auf Bedrohung für das Netzwerk  

Erkennen Sie Bedrohungen Ihres Netzwerks, wie etwa Man-in-the-Middle-Angriffe, und schützen Sie den Zugriff auf WLANs auf der Grundlage des Geräterisikos.  

**Blockieren des Netzwerkzugriffs über WLAN**:  

![Blockieren des Netzwerkzugriffs über WLAN](./media/wandera-mtd-connector/wandera-network-wifi-blocked.png)

**Zugriff erteilt nach der Behebung**:  

![Zugriff nach Beseitigung gewährt](./media/wandera-mtd-connector/wandera-network-wifi-unblocked.png)  

## <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Steuern des Zugriffs auf SharePoint Online basierend auf Netzwerkbedrohungen

Erkennen Sie Bedrohungen für Ihr Netzwerk wie Man-in-the-Middle-Angriffe, und verhindern Sie die Synchronisierung von Unternehmensdateien basierend auf den Risiken für Geräte.

**Blockieren von SharePoint Online bei Erkennung von Bedrohungen für das Netzwerk**:  

![Blockieren von SharePoint Online bei Erkennung von Bedrohungen für das Netzwerk](./media/wandera-mtd-connector/wandera-network-spo-blocked.png)  


**Zugriff erteilt nach der Behebung**:  

![Zugriff erteilt nach der Behebung für SharePoint – Beispiel](./media/wandera-mtd-connector/wandera-network-spo-unblocked.png)  

## <a name="next-steps"></a>Nächste Schritte

- [Integrieren von Wandera in Intune](wandera-mtd-connector-integration.md)
- [Einrichten von Wandera-Apps](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Erstellen einer Wandera-Konformitätsrichtlinie für Geräte](mtd-device-compliance-policy-create.md)
- [Aktivieren des Wandera MTD-Connectors](mtd-connector-enable.md)
