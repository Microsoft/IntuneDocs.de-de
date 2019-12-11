---
title: Better Mobile Threat Defense-Connector mit Intune
titleSuffix: Intune on Azure
description: Richten Sie Better Mobile Threat Defense-Connector mit Intune ein.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a52636a140778f6e78bfe081cda40b36ef2354f
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72509636"
---
# <a name="better-mobile-threat-defense-connector-with-intune"></a>Better Mobile Threat Defense-Connector mit Intune

Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen mithilfe des bedingten Zugriffs basierend auf Risikobewertungen steuern, die von Better Mobile vorgenommen werden, einer Mobile Threat Defense-Lösung (MTD), die in Microsoft Intune integriert werden kann. Das Risiko wird basierend auf Telemetriedaten von Geräten bewertet, auf denen die Better Mobile-App ausgeführt wird.

Sie können Richtlinien für bedingten Zugriff basierend auf der Better Mobile-Risikobewertung konfigurieren, die über Intune-Gerätekompatibilitätsrichtlinien aktiviert wird, und so anhand der erkannten Bedrohungen den Zugriff auf Unternehmensressourcen durch nicht konforme Geräte zulassen oder blockieren.

## <a name="how-do-intune-and-better-mobile-help-protect-your-company-resources"></a>Wie helfen Intune und Better Mobile beim Schutz von Unternehmensressourcen?

Die Better Mobile-App wird auf Mobilgeräten installiert und ausgeführt. Diese App erfasst Telemetriedaten des Dateisystems, Netzwerkstapels, von Geräten und Anwendungen, sofern verfügbar, und sendet diese Daten dann an den Better Mobile-Clouddienst, mit dessen Hilfe die Anfälligkeit des Geräts für mobile Bedrohungen bewertet wird.

Die Intune-Gerätekonformitätsrichtlinie enthält eine Regel für Mobile Threat Defense, die auf der Better Mobile-Risikobewertung basiert. Wenn diese Regel aktiviert ist, bewertet Intune die Gerätekompatibilität mit der von Ihnen aktivierten Richtlinie. Wird das Gerät als nicht kompatibel eingestuft, wird der Zugriff auf Ressourcen wie Exchange Online und SharePoint Online für Benutzer blockiert. Benutzer erhalten zudem einen Leitfaden von der auf ihren Geräten installierten Better Mobile-App, um das Problem zu beheben und den Zugriff auf Unternehmensressourcen zurückzuerlangen.

## <a name="sample-scenarios"></a>Beispielszenarien

Es folgen einige gängige Szenarios.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Steuern des Zugriffs basierend auf Bedrohungen durch Apps, die Schadsoftware enthalten

Wenn Apps, die Schadsoftware enthalten, auf Geräten erkannt werden, können Sie Geräte an folgenden Aktionen hindern, bis die Bedrohung beseitigt ist:

- Herstellen einer Verbindung mit Unternehmens-E-Mail

- Synchronisieren von Unternehmensdateien mithilfe der OneDrive for Work-App

- Zugreifen auf Unternehmens-Apps

**Blockieren, wenn Apps mit Schadsoftware entdeckt werden:**

![Darstellung: Apps mit Schadsoftware wurden erkannt](./media/better-mobile-threat-defense-connector/better_mobile_maliciousapps_blocked.png)

**Zugriff nach Beseitigung gewährt:**

![Apps mit Schadsoftware entdeckt, Zugriff gewährt](./media/better-mobile-threat-defense-connector/better_mobile_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Steuern des Zugriffs basierend auf der Bedrohung für das Netzwerk

Erkennen von Bedrohungen wie **Man-in-the-Middle-Angriffe** für Ihr Netzwerk und Schützen des Zugriffs auf WLAN-Netzwerke basierend auf dem Geräterisiko.

**Blockieren des Netzwerkzugriffs über WLAN:**

![Blockieren des Netzwerkzugriffs über WLAN](./media/better-mobile-threat-defense-connector/better_mobile_network_wifi_blocked.png)

**Zugriff nach Beseitigung gewährt:**

![Darstellung: Zugriff nach der Behebung erteilt](./media/better-mobile-threat-defense-connector/better_mobile_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Steuern des Zugriffs auf SharePoint Online basierend auf der Bedrohung für das Netzwerk

Erkennen von Bedrohungen wie **Man-in-the-Middle-Angriffe** für Ihr Netzwerk und Verhindern der Synchronisierung von Unternehmensdateien basierend auf dem Geräterisiko.

**Blockieren des Zugriffs auf SharePoint Online bei Erkennen von Bedrohungen für das Netzwerk**

![Blockieren von SharePoint Online bei Erkennung von Bedrohungen für das Netzwerk](./media/better-mobile-threat-defense-connector/better_mobile_network_spo_blocked.png)

**Zugriff nach Beseitigung gewährt:**

![Zugriff erteilt nach der Behebung für Sharepoint-Beispiel](./media/better-mobile-threat-defense-connector/better_mobile_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Unterstützte Plattformen

- **Android 4.1 und höher**

- **iOS 8.0 und höher**

## <a name="prerequisites"></a>Voraussetzungen

- Azure Active Directory Premium

- Microsoft Intune-Abonnement

- Better Mobile Threat Defense-Abonnement

  - Weitere Informationen finden Sie auf der [Better Mobile-Website](https://www.better.mobi/).

## <a name="next-steps"></a>Nächste Schritte

- [Integrieren von Better Mobile in Intune](better-mobile-mtd-connector-integration.md)

- [Einrichten von Better Mobile-Apps](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Erstellen einer Better Mobile -Gerätekompatibilitätsrichtlinie](mtd-device-compliance-policy-create.md)

- [Aktivieren des Better Mobile MTD-Connectors](mtd-connector-enable.md)
