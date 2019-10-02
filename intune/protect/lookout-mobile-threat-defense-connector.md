---
title: Lookout MTD-Connector mit Microsoft Intune
titleSuffix: Microsoft Intune
description: Informationen zum Integrieren von Intune mit Lookout Mobile Threat Defense (MTD), um den Zugriff von mobilen Geräten auf Ihre Unternehmensressourcen zu steuern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e16907f39fe8c6ea5e9a12f1e2b25026a5db225
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721317"
---
# <a name="lookout-mobile-endpoint-security-connector-with-intune"></a>Lookout Mobile Endpoint Security-Connector mit Intune

Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen basierend auf Risikobewertungen steuern, die von Lookout vorgenommen werden, einer Mobile Threat Defense-Lösung, die in Microsoft Intune integriert ist. Das Risiko wird basierend auf Telemetriedaten bewertet, die vom Lookout-Dienst auf Geräten erfasst werden, wie z.B.:
- Sicherheitsrisiken des Betriebssystems
- Installierte Apps, die Schadsoftware enthalten
- Netzwerkprofile mit böswilligen Absichten

Sie können Richtlinien für bedingten Zugriff basierend auf Risikobewertungen von Lookout konfigurieren, die über Intune-Konformitätsrichtlinien aktiviert werden. Mithilfe von Einstellungen können Sie basierend auf den erkannten Bedrohungen nicht kompatible Geräte zulassen oder blockieren.

## <a name="how-do-intune-and-lookout-mobile-endpoint-security-help-protect-company-resources"></a>Wie unterstützen Intune und Lookout Mobile Endpoint Security den Schutz von Unternehmensressourcen?
Die mobile Lookout-App **Lookout for Work** wird auf Mobilgeräten installiert und ausgeführt. Diese App erfasst Telemetriedaten des Dateisystems, Netzwerkstapels sowie von Geräten und Anwendungen, sofern verfügbar, und sendet diese dann an den Lookout-Clouddienst, mit dessen Hilfe die Anfälligkeit des Geräts für mobile Bedrohungen bewertet wird. Sie können die Klassifizierung der Risikostufe für Bedrohungen in der Lookout-Konsole gemäß Ihren Anforderungen ändern.  

Die Konformitätsrichtlinie in Intune enthält eine Regel für Lookout Mobile Threat Defense, die auf der Risikobewertung durch Lookout basiert. Wenn diese Regel aktiviert ist, bewertet Intune die Gerätekompatibilität mit der von Ihnen aktivierten Richtlinie.

Wird das Gerät als nicht konform eingestuft, kann der Zugriff auf Ressourcen wie Exchange Online und SharePoint Online blockiert werden. Benutzer auf blockierten Geräten erhalten Anweisungen, mit denen sie das Problem beheben und wieder Zugriff erlangen können. Die Anleitung wird in der Lookout for Work-App gestartet.

## <a name="supported-platforms"></a>Unterstützte Plattformen  
Bei Registrierung in Intune werden die folgenden Plattformen für Lookout unterstützt:
* **Android 4.1 und höher**  
* **iOS 8 und höher**  

Weitere Informationen zur Plattform- und Sprachunterstützung finden Sie auf der [Lookout-Website](https://personal.support.lookout.com/hc/articles/114094140253).  

## <a name="prerequisites"></a>Voraussetzungen
* Ein Enterprise-Abonnement für Lookout Mobile EndPoint Security.  
* Microsoft Intune-Abonnement
* Azure Active Directory Premium
* Enterprise Mobility + Security (EMS) E3 oder E5 mit Lizenzen, die Benutzern zugewiesen wurden.  

Weitere Informationen finden Sie unter [Lookout Mobile EndPoint Security](https://www.lookout.com/products/mobile-endpoint-security).

## <a name="sample-scenarios"></a>Beispielszenarien

Im Folgenden finden Sie allgemeine Szenarien für die Verwendung von Mobile Endpoint Security mit Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Steuern des Zugriffs basierend auf Bedrohungen durch Apps, die Schadsoftware enthalten
Wenn Apps, die Schadsoftware enthalten, auf Geräten erkannt werden, können Sie Geräte an folgenden Aktionen hindern, bis die Bedrohung beseitigt ist:
* Herstellen einer Verbindung mit Unternehmens-E-Mail
* Synchronisieren von Unternehmensdateien mithilfe der OneDrive for Work-App
* Zugreifen auf Unternehmens-Apps

**Blockieren, wenn Apps mit Schadsoftware entdeckt werden:**

![Darstellung der Richtlinie, die den Zugriff aufgrund von Apps mit Schadsoftware blockiert](./media/lookout-mobile-threat-defense-connector/malicious-apps-blocked.png)

**Zugriff nach Beseitigung gewährt:**

![Darstellung des gewährten Zugriffs nach der Beseitigung](./media/lookout-mobile-threat-defense-connector/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Steuern des Zugriffs basierend auf der Bedrohung für das Netzwerk
Erkennen Sie Bedrohungen Ihres Netzwerks, wie etwa Man-in-the-Middle-Angriffe, und Schützen Sie den Zugriff auf WLANs auf der Grundlage des Geräterisikos.

**Blockieren des Netzwerkzugriffs über WLAN:**

![Darstellung des blockierten WLAN-Zugriffs basierend auf Netzwerkbedrohungen](./media/lookout-mobile-threat-defense-connector/network-wifi-blocked.png)

**Zugriff nach Beseitigung gewährt:**

![Darstellung des bedingten Zugriffs, der nach Beseitigung der Bedrohung den Zugriff gewährt](./media/lookout-mobile-threat-defense-connector/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Steuern des Zugriffs auf SharePoint Online basierend auf der Bedrohung für das Netzwerk

Erkennen von Bedrohungen Ihres Netzwerks, wie etwa Man-in-the-Middle-Angriffen, und Verhindern der Synchronisierung von Unternehmensdateien auf der Grundlage des Geräterisikos.

**Blockieren des Zugriffs auf SharePoint Online bei Erkennen von Bedrohungen für das Netzwerk**

![Darstellung des blockierten Zugriffs auf SharePoint Online](./media/lookout-mobile-threat-defense-connector/network-spo-blocked.png)


**Zugriff nach Beseitigung gewährt:**

![Darstellung des gewährten Zugriffs, nachdem die Netzwerkbedrohung beseitigt wurde](./media/lookout-mobile-threat-defense-connector/network-spo-unblocked.png)

## <a name="next-steps"></a>Nächste Schritte
Hier sind die wichtigsten Schritte, die Sie ausführen müssen, um diese Lösung zu implementieren:
1. [Einrichten Ihrer Lookout-Integration](lookout-mtd-connector-integration.md)
2. [Aktivieren von Mobile Endpoint Security in Intune](mtd-connector-enable.md)
3. [Die Lookout for Work-App hinzufügen und zuweisen](mtd-apps-ios-app-configuration-policy-add-assign.md)
4. [Die Lookout-Gerätekonformitätsrichtlinie konfigurieren](mtd-device-compliance-policy-create.md)
