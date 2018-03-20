---
title: Skycure-Connector mit Microsoft Intune
titlesuffix: 
description: "Informationen zum Integrieren von Intune mit Skycure Mobile Threat Defense (MTD), um den Zugriff mobiler Geräte auf Ihre Unternehmensressourcen zu steuern."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b3148a24b077dfd491ce06fcf708a81de7d12dc1
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="skycure-mobile-threat-defense-connector"></a>Skycure Mobile Threat Defense-Connector

Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen mit bedingtem Zugriff basierend auf Risikobewertungen steuern, die von Skycure vorgenommen werden, einer Mobile Threat Defense-Lösung, die mit Microsoft Intune zusammenarbeitet. Das Risiko wird basierend auf Telemetriedaten von Geräten bewertet, auf denen Skycure ausgeführt wird, wie z.B.:

-   Physische Verteidigung

-   Netzwerkverteidigung

-   Anwendungsverteidigung

-   Verteidigung gegen Sicherheitsrisiken

Sie können Richtlinien für bedingten Zugriff basierend auf der Skycure-Risikobewertung konfigurieren, die über Intune-Gerätekompatibilitätsrichtlinien aktiviert werden, und so anhand der erkannten Bedrohungen nicht kompatible Geräte für den Zugriff auf Unternehmensressourcen zulassen oder blockieren.

## <a name="how-do-intune-and-skycure-help-protect-your-company-resources"></a>Wie helfen Intune und Skycure beim Schutz von Unternehmensressourcen?

Die mobile Skycure-App für Android oder iOS erfasst Telemetriedaten des Dateisystems, Netzwerkstapels sowie von Geräten und Anwendungen, sofern verfügbar, und sendet diese dann an den Skycure-Clouddienst, mit dessen Hilfe die Anfälligkeit des Geräts für mobile Bedrohungen bewertet wird.

Die Intune-Gerätekompatibilitätsrichtlinie enthält eine Regel für Skycure Mobile Threat Defense, die auf der Skycure-Risikobewertung basiert. Wenn diese Regel aktiviert ist, bewertet Intune die Gerätekompatibilität mit der von Ihnen aktivierten Richtlinie.

Wird das Gerät als nicht kompatibel eingestuft, wird der Zugriff auf Ressourcen wie Exchange Online und SharePoint Online blockiert. Benutzer auf blockierten Geräten erhalten Anleitungen von der mobilen Skycure-App, um das Problem zu beheben und den Zugriff auf Unternehmensressourcen zurückzuerlangen.

Intune unterstützt zwei Modi der Integration mit Skycure:

-   Die **grundlegende Installation** ist ein schreibgeschützter Modus, der die Sichtbarkeit von Skycure für Geräte in Intune zulässt.

-   Die **vollständige Integration** ermöglicht Skycure, Details zu Geräterisiken und Sicherheitsvorfällen an Intune zu melden.

## <a name="sample-scenarios"></a>Beispielszenarien

Hier einige gängige Szenarios:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Steuern des Zugriffs basierend auf Bedrohungen durch Apps, die Schadsoftware enthalten

Wenn Apps, die Schadsoftware enthalten, auf Geräten erkannt werden, können Sie Geräte blockieren, bis die Bedrohung beseitigt ist:

-   Herstellen einer Verbindung mit Unternehmens-E-Mail

-   Synchronisieren von Unternehmensdateien mithilfe der OneDrive for Work-App

-   Zugreifen auf Unternehmens-Apps

**Blockieren, wenn Apps mit Schadsoftware entdeckt werden:**

![Apps mit Schadsoftware entdeckt](./media/skycure-arch-1.png)

**Zugriff nach Beseitigung gewährt:**

![Zugriff nach Beseitigung von entdeckten Apps mit Schadsoftware gewährt](./media/skycure-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Steuern des Zugriffs basierend auf der Bedrohung für das Netzwerk

Erkennen Sie Bedrohungen wie **Man-in-the-Middle** im Netzwerk, und schützen Sie den Zugriff auf WLAN-Netzwerke auf der Grundlage des Geräterisikos.

**Blockieren des Netzwerkzugriffs über WLAN:**

![Blockieren des Netzwerkzugriffs über WLAN](./media/skycure-arch-3.png)

**Zugriff nach Beseitigung gewährt:**

![Zugriff erteilt nach der Behebung](./media/skycure-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Steuern des Zugriffs auf SharePoint Online basierend auf der Bedrohung für das Netzwerk

Erkennen von Bedrohungen wie **Man-in-the-Middle** im Netzwerk und Verhindern der Synchronisierung von Unternehmensdateien auf der Grundlage des Geräterisikos.

**Blockieren des Zugriffs auf SharePoint Online bei Erkennen von Bedrohungen für das Netzwerk**

![Blockieren von SharePoint Online bei Erkennung von Bedrohungen für das Netzwerk](./media/skycure-arch-5.png)

**Zugriff nach Beseitigung gewährt:**

![Zugriff erteilt nach der Behebung für Sharepoint-Beispiel](./media/skycure-arch-6.png)

## <a name="supported-platforms"></a>Unterstützte Plattformen

-   **Android 4.1 und höher**

-   **iOS 8 und höher**

## <a name="pre-requisites"></a>Voraussetzungen

-   Azure Active Directory Premium

-   Microsoft Intune-Abonnement

-   Skycure Mobile Threat Defense-Abonnement

Weitere Informationen erhalten Sie auf der [Skycure-Website](https://www.skycure.com/skycure-microsoft-integration/).

## <a name="next-steps"></a>Nächste Schritte

Dies sind die Schritte, die Sie für die Integration von Intune und Skycure durchführen müssen:

- [Einrichten der Skycure-Integration in Intune](skycure-mtd-connector-integration.md)

- [Hinzufügen und Zuweisen von Skycure-Apps, der Microsoft Authenticator-App und der iOS-Konfigurationsrichtlinie](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Erstellen einer Skycure-Gerätekompatibilitätsrichtlinie mit Intune](mtd-device-compliance-policy-create.md)

- [Aktivieren des Skycure MTP-Connectors in Intune](mtd-connector-enable.md)
