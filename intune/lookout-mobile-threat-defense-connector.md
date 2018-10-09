---
title: Lookout MTD-Connector mit Microsoft Intune
titlesuffix: ''
description: Informationen zum Integrieren von Intune mit Lookout Mobile Threat Defense (MTD), um den Zugriff von mobilen Geräten auf Ihre Unternehmensressourcen zu steuern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/09/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a10c392f91c3c2992f1eebf8e71814520fbb4aa0
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231932"
---
# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Lookout Mobile Threat Defense-Connector mit Intune

Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen basierend auf Risikobewertungen steuern, die von Lookout vorgenommen werden, einer Mobile Threat Defense-Lösung, die in Microsoft Intune integriert ist. Das Risiko wird basierend auf Telemetriedaten bewertet, die vom Lookout-Dienst auf Geräten erfasst werden, wie z.B.:
- Sicherheitsrisiken des Betriebssystems
- Installierte Apps, die Schadsoftware enthalten
- Netzwerkprofile mit böswilligen Absichten

Sie können Richtlinien für bedingten Zugriff basierend auf Risikobewertungen von Lookout konfigurieren, die mithilfe von Intune-Konformitätsrichtlinien aktiviert werden. Mithilfe von Einstellungen können Sie basierend auf den erkannten Bedrohungen nicht kompatible Geräte zulassen oder blockieren.

## <a name="how-do-intune-and-lookout-mobile-threat-defense-help-protect-company-resources"></a>In welcher Form unterstützen Intune und Lookout Mobile Threat Defense den Schutz von Unternehmensressourcen?
Die mobile Lookout-App **Lookout for Work** wird auf Mobilgeräten installiert und ausgeführt. Diese App erfasst Telemetriedaten des Dateisystems, Netzwerkstapels sowie von Geräten und Anwendungen, sofern verfügbar, und sendet diese dann an den Lookout-Clouddienst, mit dessen Hilfe die Anfälligkeit des Geräts für mobile Bedrohungen bewertet wird. Sie können die Klassifizierung der Risikostufe für Bedrohungen in der Lookout-Konsole gemäß Ihren Anforderungen ändern.  

Die Konformitätsrichtlinie in Intune enthält eine Regel für Lookout Mobile Threat Defense, die auf der Risikobewertung durch Lookout basiert. Wenn diese Regel aktiviert ist, bewertet Intune die Gerätekompatibilität mit der von Ihnen aktivierten Richtlinie.

Wird das Gerät als nicht kompatibel eingestuft, kann der Zugriff auf Ressourcen wie Exchange Online und SharePoint Online blockiert werden. Benutzer auf blockierten Geräten erhalten Anweisungen zum Beheben des Problems und erneuten Erlangen des Zugriffs. Die Anleitung wird in der Lookout for Work-App gestartet.

## <a name="supported-platforms"></a>Unterstützte Plattformen
Bei Registrierung in Intune werden die folgenden Plattformen für Lookout unterstützt:
* **Android 4.1 und höher**
* **iOS 8 und höher** Weitere Informationen zur Unterstützung von Plattformen und Sprachen finden Sie auf der [Lookout-Website](https://personal.support.lookout.com/hc/articles/114094140253).

## <a name="prerequisites"></a>Voraussetzungen
* Microsoft Intune-Abonnement
* Azure Active Directory
* Ein Enterprise-Abonnement für Lookout Mobile EndPoint Security.  

Weitere Informationen finden Sie unter [Lookout Mobile EndPoint Security](https://www.lookout.com/products/mobile-endpoint-security).

## <a name="sample-scenarios"></a>Beispielszenarien

Nachstehend sind die allgemeinen Szenarien bei Verwenden von Lookout Mobile Threat Defense mit Intune aufgeführt.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Steuern des Zugriffs basierend auf Bedrohungen durch Apps, die Schadsoftware enthalten
Wenn Apps, die Schadsoftware enthalten, auf Geräten erkannt werden, können Sie Geräte an folgenden Aktionen hindern, bis die Bedrohung beseitigt ist:
* Herstellen einer Verbindung mit Unternehmens-E-Mail
* Synchronisieren von Unternehmensdateien mithilfe der OneDrive for Work-App
* Zugreifen auf Unternehmens-Apps

**Blockieren, wenn Apps mit Schadsoftware entdeckt werden:**

![Diagramm das zeigt, wie die Richtlinie für bedingten Zugriff den Zugriff blockiert, wenn das Gerät aufgrund von böswilligen Apps auf dem Gerät als nicht konform eingestuft wird](./media/malicious-apps-blocked.png)

**Zugriff nach Beseitigung gewährt:**

![Diagramm, das die Richtlinie für bedingten Zugriff darstellt, die den Zugriff erteilt, nachdem das Gerät nach der Sanierung als kompatibel bewertet wurde](./media/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Steuern des Zugriffs basierend auf der Bedrohung für das Netzwerk
Erkennen Sie Bedrohungen Ihres Netzwerks, wie etwa Man-in-the-Middle-Angriffe, und Schützen Sie den Zugriff auf WLANs auf der Grundlage des Geräterisikos.

**Blockieren des Netzwerkzugriffs über WLAN:**

![Diagramm das zeigt, wie bedingter Zugriff den Zugriff auf WLAN basierend auf Netzwerkbedrohungen blockiert](./media/network-wifi-blocked.png)

**Zugriff nach Beseitigung gewährt:**

![Diagramm, das den Zugriff durch bedingten Zugriff nach der Beseitigung der Bedrohung erteilt](./media/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Steuern des Zugriffs auf SharePoint Online basierend auf der Bedrohung für das Netzwerk

Erkennen von Bedrohungen Ihres Netzwerks, wie etwa Man-in-the-Middle-Angriffen, und Verhindern der Synchronisierung von Unternehmensdateien auf der Grundlage des Geräterisikos.

**Blockieren des Zugriffs auf SharePoint Online bei Erkennen von Bedrohungen für das Netzwerk**

![Diagramm, das die Blockierung des Gerätezugriffs auf SharePoint Online mithilfe von bedingtem Zugriff basierend auf der Erkennung von Bedrohungen darstellt](./media/network-spo-blocked.png)


**Zugriff nach Beseitigung gewährt:**

![Diagramm, das den bedingten Zugriff nach dem Beheben der Netzwerkbedrohung darstellt](./media/network-spo-unblocked.png)

## <a name="next-steps"></a>Nächste Schritte
Hier sind die wichtigsten Schritte, die Sie ausführen müssen, um diese Lösung zu implementieren:
1.  [Einrichten Ihrer Lookout-Integration](lookout-mtd-connector-integration.md)
2.  [Lookout Mobile Threat Defense in Intune aktivieren](mtd-connector-enable.md)
3.  [Die Lookout for Work-App hinzufügen und zuweisen](mtd-apps-ios-app-configuration-policy-add-assign.md)
4.  [Die Lookout-Gerätekonformitätsrichtlinie konfigurieren](mtd-device-compliance-policy-create.md)
