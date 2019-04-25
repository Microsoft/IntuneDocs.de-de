---
title: Zimperium MTD-Connector in Intune
titleSuffix: Intune on Azure
description: Informationen zum Integrieren von Zimperium Mobile Threat Defense in Intune, um den Zugriff von mobilen Geräten auf Ihre Unternehmensressourcen zu steuern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/29/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a5cb4758cefc1a206e8dae32dfa31994814b3f06
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61510255"
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Zimperium Mobile Threat Defense-Connector in Intune

Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen mit bedingtem Zugriff basierend auf Risikobewertungen steuern, die von Zimperium vorgenommen werden, einer Mobile Threat Defense-Lösung (MTD), die mit Microsoft Intune zusammenarbeitet. Das Risiko wird basierend auf Telemetriedaten von Geräten bewertet, auf denen die Zimperium-App ausgeführt wird.

Sie können Richtlinien für bedingten Zugriff basierend auf Risikobewertungen von Zimperium konfigurieren, die mithilfe von Intune-Gerätekonformitätsrichtlinien aktiviert werden. Richtlinien für die Risikobewertung können den Zugriff nicht konformer Geräte auf Unternehmensressourcen basierend auf den erkannten Bedrohungen gewähren oder verweigern.

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>Wie helfen Intune und Zimperium beim Schutz von Unternehmensressourcen?

Die Zimperium-App für Android oder iOS erfasst Telemetriedaten des Dateisystems, Netzwerkstapels sowie von Geräten und Anwendungen, sofern verfügbar, und sendet diese dann an den Zimperium-Clouddienst, mit dessen Hilfe die Anfälligkeit des Geräts für mobile Bedrohungen bewertet wird.

Die Intune-Gerätekompatibilitätsrichtlinie enthält eine Regel für Zimperium Mobile Threat Defense, die auf der Zimperium-Risikobewertung basiert. Wenn diese Regel aktiviert ist, bewertet Intune die Gerätekompatibilität mit der von Ihnen aktivierten Richtlinie. Wird das Gerät als nicht kompatibel eingestuft, wird der Zugriff auf Ressourcen wie Exchange Online und SharePoint Online für Benutzer blockiert. Benutzer erhalten zudem einen Leitfaden von der auf ihren Geräten installierten Zimperium-App, um das Problem zu beheben und den Zugriff auf Unternehmensressourcen zurückzuerlangen.

## <a name="sample-scenarios"></a>Beispielszenarien

Nachstehend finden Sie einige Szenarios für die Integration von Zimperium in Intune:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Steuern des Zugriffs basierend auf Bedrohungen durch Apps, die Schadsoftware enthalten

Wenn Apps, die Schadsoftware enthalten, auf Geräten erkannt werden, können Sie Geräte blockieren, bis die Bedrohung beseitigt ist:

-   Herstellen einer Verbindung mit Unternehmens-E-Mail

-   Synchronisieren von Unternehmensdateien mithilfe der OneDrive for Work-App

-   Zugreifen auf Unternehmens-Apps

**Blockieren, wenn Apps mit Schadsoftware entdeckt werden:**

![Darstellung des Szenarios, wenn Apps mit Schadsoftware erkannt werden](./media/Maliciousapps_blocked_Zimperium.png)

**Zugriff nach Beseitigung gewährt:**

![Darstellung des Szenarios, wenn der Zugriff nach der Behebung wieder erteilt wird](./media/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>Steuern des Zugriffs basierend auf der Bedrohung für das Netzwerk

Erkennen Sie Bedrohungen wie  **Man-in-the-Middle**  im Netzwerk, und schützen Sie den Zugriff auf WLAN-Netzwerke auf der Grundlage des Geräterisikos.

**Blockieren des Netzwerkzugriffs über WLAN:**

![Blockieren des Netzwerkzugriffs über WLAN](./media/network_wifi_blocked_Zimperium.png)

**Zugriff nach Beseitigung gewährt:**

![Zugriff erteilt nach der Behebung](./media/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Steuern des Zugriffs auf SharePoint Online basierend auf der Bedrohung für das Netzwerk

Erkennen von Bedrohungen wie  **Man-in-the-Middle** im Netzwerk und Verhindern der Synchronisierung von Unternehmensdateien auf der Grundlage des Geräterisikos.

**Blockieren des Zugriffs auf SharePoint Online bei Erkennen von Bedrohungen für das Netzwerk**

![Blockieren von SharePoint Online bei Erkennung von Bedrohungen für das Netzwerk](./media/network_spo_blocked_Zimperium.png)

**Zugriff nach Beseitigung gewährt:**

![Zugriff erteilt nach der Behebung für Sharepoint-Beispiel](./media/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>Unterstützte Plattformen

-   **Android 4.1 und höher**

-   **iOS 8 und höher**

## <a name="prerequisites"></a>Voraussetzungen

-   Azure Active Directory Premium

-   Microsoft Intune-Abonnement

-   Zimperium Mobile Threat Defense-Abonnement

    -   Weitere Informationen finden Sie auf der  [Zimperium-Website](https://www.zimperium.com/zips-mobile-ips).

## <a name="next-steps"></a>Nächste Schritte

- [Integrate Zimperium with Intune (Integrieren von Zimperium in Intune)](zimperium-mtd-connector-integration.md)

- [Einrichten von Zimperium-Apps](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Erstellen einer Zimperium-Gerätekompatibilitätsrichtlinie](mtd-device-compliance-policy-create.md)

- [Aktivieren des Zimperium MTD-Connectors](mtd-connector-enable.md)
