---
title: Skycure Mobile Threat Defense-Connector
description: Schützen Sie den Zugriff auf Unternehmensressourcen basierend auf Geräte-, Netzwerk- und Anwendungsrisiko mithilfe des Skycure Mobile Threat Defense-Connectors und Intune.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7a004e6c-604a-448c-bfb8-cfda63749f5b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f79e793ec6931d6497c6b66eee98aea39786e962
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="skycure-mobile-threat-defense-connector"></a>Skycure Mobile Threat Defense-Connector

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

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

![Apps mit Schadsoftware entdeckt](../media/mtp/skycure-arch-1.png)

**Zugriff nach Beseitigung gewährt:**

![Apps mit Schadsoftware entdeckt, Zugriff gewährt](../media/mtp/skycure-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Steuern des Zugriffs basierend auf der Bedrohung für das Netzwerk

Erkennen Sie Bedrohungen wie **Man-in-the-Middle** im Netzwerk, und schützen Sie den Zugriff auf WLAN-Netzwerke auf der Grundlage des Geräterisikos.

**Blockieren des Netzwerkzugriffs über WLAN:**

![Blockieren des Netzwerkzugriffs über WLAN](../media/mtp/skycure-arch-3.png)

**Zugriff nach Beseitigung gewährt:**

![Zugriff erteilt nach der Behebung](../media/mtp/skycure-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Steuern des Zugriffs auf SharePoint Online basierend auf der Bedrohung für das Netzwerk

Erkennen von Bedrohungen wie **Man-in-the-Middle** im Netzwerk und Verhindern der Synchronisierung von Unternehmensdateien auf der Grundlage des Geräterisikos.

**Blockieren des Zugriffs auf SharePoint Online bei Erkennen von Bedrohungen für das Netzwerk**

![Blockieren von SharePoint Online bei Erkennung von Bedrohungen für das Netzwerk](../media/mtp/skycure-arch-5.png)

**Zugriff nach Beseitigung gewährt:**

![Zugriff erteilt nach der Behebung für Sharepoint-Beispiel](../media/mtp/skycure-arch-6.png)

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

1.  [Konfigurieren von Skycure für die Verwendung von Azure Active Directory-SSO](/intune-classic/deploy-use/configure-skycure-to-use-azure-active-directory-single-sign-on)

2.  [Herunterladen der Skycure iOS-App-Konfigurationsrichtlinie](/intune-classic/deploy-use/download-skycure-ios-app-configuration-policy)

3.  [Hinzufügen von Skycure-Apps, der Microsoft Authenticator-App und der iOS-Konfigurationsrichtlinie](/intune-classic/deploy-use/add-skycure-apps-microsoft-authenticator-and-ios-app-configuration-policy)

4.  [Bereitstellen von Skycure-Apps, der Microsoft Authenticator-App und der iOS-Konfigurationsrichtlinie](/intune-classic/deploy-use/deploy-skycure-apps-microsoft-authenticator-app-and-ios-app-configuration-policy)

5.  [Einrichten der Skycure-Integration in Intune](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)

6.  [Aktivieren von Skycure Mobile Threat Defense in Intune](/intune-classic/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

7.  [Erstellen der Mobile Threat Defense-Kompatibilitätsrichtlinie in Intune](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
