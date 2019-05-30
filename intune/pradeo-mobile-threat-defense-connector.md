---
title: Mobile Threat Defense-Connector Pradeo in Intune
titleSuffix: Intune on Azure
description: Richten Sie den Mobile Threat Defense-Connector Pradeo mit Intune ein.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: cde4d389-1770-4226-85a3-a2f3b3fb92a3
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: df1a3fcfe0f6fd0fc2a5fbfe73935c8f47c106ff
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041611"
---
# <a name="pradeo-mobile-threat-defense-connector-with-intune"></a>Mobile Threat Defense-Connector Pradeo in Intune

Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen mit bedingtem Zugriff basierend auf Risikobewertungen steuern, die von Pradeo vorgenommen werden, einer MTD-Lösung (Multi Threat Defense), die in Microsoft Intune integriert werden kann. Das Risiko wird basierend auf Telemetriedaten von Geräten bewertet, auf denen die Pradeo-App ausgeführt wird.

Sie können Richtlinien für bedingten Zugriff basierend auf der Pradeo-Risikobewertung konfigurieren, die über Intune-Gerätekompatibilitätsrichtlinien aktiviert werden, und so anhand der erkannten Bedrohungen nicht kompatible Geräte für den Zugriff auf Unternehmensressourcen zulassen oder blockieren.

## <a name="how-do-intune-and-pradeo-help-protect-your-company-resources"></a>Wie helfen Intune und Pradeo beim Schutz von Unternehmensressourcen?

Die Pradeo-App für Android oder iOS erfasst Telemetriedaten des Dateisystems, Netzwerkstapels sowie von Geräten und Anwendungen, sofern verfügbar, und sendet diese dann an den Pradeo-Clouddienst, mit dessen Hilfe die Anfälligkeit des Geräts für mobile Bedrohungen bewertet wird.

Die Intune-Gerätekonformitätsrichtlinie enthält eine Regel für Pradeo Mobile Threat Defense, die auf der Pradeo-Risikobewertung basiert. Wenn diese Regel aktiviert ist, bewertet Intune die Gerätekompatibilität mit der von Ihnen aktivierten Richtlinie. Wird das Gerät als nicht kompatibel eingestuft, wird der Zugriff auf Ressourcen wie Exchange Online und SharePoint Online für Benutzer blockiert. Benutzer erhalten zudem einen Leitfaden von der auf ihren Geräten installierten Pradeo-App, um das Problem zu beheben und den Zugriff auf Unternehmensressourcen zurückzuerlangen.

## <a name="sample-scenarios"></a>Beispielszenarien

Es folgen einige gängige Szenarios.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Steuern des Zugriffs basierend auf Bedrohungen durch Apps, die Schadsoftware enthalten

Wenn Apps, die Schadsoftware enthalten, auf Geräten erkannt werden, können Sie Geräte an folgenden Aktionen hindern, bis die Bedrohung beseitigt ist:

-   Herstellen einer Verbindung mit Unternehmens-E-Mail

-   Synchronisieren von Unternehmensdateien mithilfe der OneDrive for Work-App

-   Zugreifen auf Unternehmens-Apps

**Blockieren, wenn Apps mit Schadsoftware entdeckt werden:**

![Darstellung des Szenarios, wenn Apps mit Schadsoftware erkannt werden](./media/pradeo_maliciousapps_blocked.png)

**Zugriff nach Beseitigung gewährt:**

![Apps mit Schadsoftware entdeckt, Zugriff gewährt](./media/pradeo_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Steuern des Zugriffs basierend auf der Bedrohung für das Netzwerk

Erkennen von Bedrohungen wie **Man-in-the-Middle-Angriffe** für Ihr Netzwerk und Schützen des Zugriffs auf WLAN-Netzwerke basierend auf dem Geräterisiko.

**Blockieren des Netzwerkzugriffs über WLAN:**

![Blockieren des Netzwerkzugriffs über WLAN](./media/pradeo_network_wifi_blocked.png)

**Zugriff nach Beseitigung gewährt:**

![Darstellung des Szenarios, wenn der Zugriff nach der Behebung wieder erteilt wird](./media/pradeo_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Steuern des Zugriffs auf SharePoint Online basierend auf der Bedrohung für das Netzwerk

Erkennen von Bedrohungen wie **Man-in-the-Middle-Angriffe** für Ihr Netzwerk und Verhindern der Synchronisierung von Unternehmensdateien basierend auf dem Geräterisiko.

**Blockieren des Zugriffs auf SharePoint Online bei Erkennen von Bedrohungen für das Netzwerk**

![Blockieren von SharePoint Online bei Erkennung von Bedrohungen für das Netzwerk](./media/pradeo_network_spo_blocked.png)

**Zugriff nach Beseitigung gewährt:**

![Darstellung des Szenarios für das Sharepoint-Beispiel, wenn der Zugriff nach der Behebung wieder erteilt wird](./media/pradeo_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Unterstützte Plattformen

-   **Android 4.0.3 und höher**

-   **iOS 7 und höher**

## <a name="prerequisites"></a>Voraussetzungen

-   Azure Active Directory Premium

-   Microsoft Intune-Abonnement

-   Pradeo Security für Mobile Threat Defense-Abonnements

    -   Weitere Informationen finden Sie auf der [Pradeo-Website](https://www.pradeo.com/en-US/mobile-threat-protection).

## <a name="next-steps"></a>Nächste Schritte

- [Integrate Pradeo with Intune (Integrieren von Pradeo in Intune)](pradeo-mtd-connector-integration.md)

- [Einrichten von Pradeo-Apps](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Erstellen einer Pradeo-Gerätekonformitätsrichtlinie](mtd-device-compliance-policy-create.md)

- [Aktivieren eines Pradeo MTD-Connectors](mtd-connector-enable.md)
