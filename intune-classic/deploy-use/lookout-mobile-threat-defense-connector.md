---
title: Lookout Mobile Threat Defense-Connector
description: Schützen Sie den Zugriff auf Unternehmensressourcen basierend auf dem Gerät, Netzwerk und Anwendungsrisiko mithilfe des Lookout Mobile Threat Defense-Connectors und Intune.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 01/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 201c431f2c30538139f0dc9c436781aae2bd9735
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Lookout Mobile Threat Defense-Connector mit Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen basierend auf Risikobewertungen steuern, die von Lookout vorgenommen werden, einer Mobile Threat Defense-Lösung, die in Microsoft Intune integriert ist. Das Risiko wird basierend auf Telemetriedaten bewertet, die vom Lookout-Dienst auf Geräten erfasst werden, wie z.B.:
- Sicherheitsrisiken des Betriebssystems
- Installierte Apps, die Schadsoftware enthalten
- Netzwerkprofile mit böswilligen Absichten

Sie können Richtlinien für bedingten Zugriff basierend auf Risikobewertungen von Lookout konfigurieren, die mithilfe von Intune-Kompatibilitätsrichtlinien aktiviert werden. Mithilfe von Einstellungen können Sie basierend auf den erkannten Bedrohungen nicht kompatible Geräte zulassen oder blockieren.

## <a name="how-do-intune-and-lookout-mobile-threat-defense-help-protect-company-resources"></a>In welcher Form unterstützen Intune und Lookout Mobile Threat Defense den Schutz von Unternehmensressourcen?
Die mobile Lookout-App **Lookout for Work** wird auf Mobilgeräten installiert und ausgeführt. Diese App erfasst Telemetriedaten des Dateisystems, Netzwerkstapels sowie von Geräten und Anwendungen, sofern verfügbar, und sendet diese dann an den Lookout-Clouddienst, mit dessen Hilfe die Anfälligkeit des Geräts für mobile Bedrohungen bewertet wird. Sie können die Klassifizierung der Risikostufe für Bedrohungen in der Lookout-Konsole gemäß Ihren Anforderungen ändern.  

Die Konformitätsrichtlinie in Intune enthält eine Regel für Lookout Mobile Threat Defense, die auf der Risikobewertung durch Lookout basiert. Wenn diese Regel aktiviert ist, bewertet Intune die Gerätekompatibilität mit der von Ihnen aktivierten Richtlinie.

Wird das Gerät als nicht kompatibel eingestuft, kann der Zugriff auf Ressourcen wie Exchange Online und SharePoint Online blockiert werden. Benutzer auf blockierten Geräten erhalten Anweisungen zum Beheben des Problems und erneuten Erlangen des Zugriffs. Die Anleitung wird in der Lookout for Work-App gestartet.

## <a name="supported-platforms"></a>Unterstützte Plattformen:
Bei Registrierung in Intune werden die folgenden Plattformen für Lookout unterstützt:
* **Android 4.1 und höher**
* **iOS 8 und höher** Weitere Informationen zur Unterstützung von Plattformen und Sprachen finden Sie auf der [Lookout-Website](https://personal.support.lookout.com/hc/articles/114094140253).

## <a name="prerequisites"></a>Voraussetzungen:
* Microsoft Intune-Abonnement
* Azure Active Directory
* Ein Enterprise-Abonnement für Lookout Mobile EndPoint Security.  

Weitere Informationen finden Sie unter [Lookout Mobile EndPoint Security](https://www.lookout.com/products/mobile-endpoint-security).

## <a name="sample-scenarios"></a>Beispielszenarien
Es folgen einige gängige Szenarien:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Steuern des Zugriffs basierend auf Bedrohungen durch Apps, die Schadsoftware enthalten
Wenn Apps, die Schadsoftware enthalten, auf Geräten erkannt werden, können Sie Geräte an folgenden Aktionen hindern, bis die Bedrohung beseitigt ist:
* Herstellen einer Verbindung mit Unternehmens-E-Mail
* Synchronisieren von Unternehmensdateien mithilfe der OneDrive for Work-App
* Zugreifen auf Unternehmens-Apps

**Zugriff blockiert, wenn Apps mit Schadsoftware erkannt werden:**
![Diagramm, das eine Richtlinie für bedingten Zugriff zeigt, die den Zugriff blockiert, wenn ein Gerät aufgrund vorhandener Apps mit Schadsoftware als nicht kompatibel eingestuft wird](../media/mtp/malicious-apps-blocked.png)

**Zugriff nach Beseitigung gewährt:**

![Diagramm, das die Richtlinie für bedingten Zugriff darstellt, die den Zugriff erteilt, nachdem das Gerät nach der Sanierung als kompatibel bewertet wurde](../media/mtp/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Steuern des Zugriffs basierend auf der Bedrohung für das Netzwerk
Erkennen von Bedrohungen Ihres Netzwerks, wie etwa Man-in-the-Middle-Angriffe, und Schutz des Zugriffs auf WLANs auf der Grundlage des Geräterisikos.

**Zugriff auf das Netzwerk über WLAN blockiert:**
![Diagramm, das die Blockierung des WLAN-Zugriffs durch bedingten Zugriff auf Grundlage von Netzwerkbedrohungen zeigt](../media/mtp/network-wifi-blocked.png)

**Nach Korrektur erteilter Zugriff:**

![Diagramm, das den Zugriff durch bedingten Zugriff nach der Beseitigung der Bedrohung erteilt](../media/mtp/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Steuern des Zugriffs auf SharePoint Online basierend auf der Bedrohung für das Netzwerk

Erkennen von Bedrohungen Ihres Netzwerks, wie etwa Man-in-the-Middle-Angriffen, und Verhindern der Synchronisierung von Unternehmensdateien auf der Grundlage des Geräterisikos.

**Blockieren des Zugriffs auf SharePoint Online bei Erkennen von Bedrohungen für das Netzwerk**

![Diagramm, das die Blockierung des Gerätezugriffs auf SharePoint Online mithilfe von bedingtem Zugriff basierend auf der Erkennung von Bedrohungen darstellt](../media/mtp/network-spo-blocked.png)


**Zugriff nach Beseitigung gewährt:**

![Diagramm, das den bedingten Zugriff nach dem Beheben der Netzwerkbedrohung darstellt](../media/mtp/network-spo-unblocked.png)

## <a name="next-steps"></a>Nächste Schritte
Hier sind die wichtigsten Schritte, die Sie ausführen müssen, um diese Lösung zu implementieren:
1.  [Ihr Lookout-Abonnement einrichten](setup-your-lookout-mtd-subscription.md)
2.  [Lookout Mobile Threat Defense in Intune aktivieren](enable-lookout-mtd-connection.md)
3.  [Die Lookout Mobile Threat Defense-App konfigurieren und bereitstellen](configure-deploy-lookout-for-work-app.md)
4.  [Die Lookout-Gerätekonformitätsrichtlinie konfigurieren](create-lookout-device-compliance-policy.md)
5.  [Problembehandlung der Lookout Mobile Threat Defense-Integration durchführen](/intune-classic/troubleshoot/device-threat-protection-troubleshooting)
