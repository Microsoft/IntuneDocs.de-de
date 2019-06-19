---
title: Netzwerkendpunkte für US Government-Bereitstellungen – Microsoft Intune
titleSuffix: ''
description: Überprüfen Sie die US Government-Endpunkte für Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4712c2958e2beee8853ad0d2620414d823da327
ms.sourcegitcommit: 6e07c35145f70b008cf170bae57143248a275b67
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66804498"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>US Government-Endpunkte für Microsoft Intune

Auf dieser Seite werden die US Government-Endpunkte aufgelistet, die für die Proxyeinstellungen in Ihren Intune-Bereitstellungen erforderlich sind.

Sie müssen die Kommunikation für Intune aktivieren, um Geräte hinter Firewalls und Proxyservern zu verwalten.

- Der Proxyserver muss sowohl **HTTP** (80) als auch **HTTPS** (443) unterstützen, da Intune-Clients beide Protokolle verwenden.
- Für einige Aufgaben wie das Herunterladen von Software und Updates erfordert Intune nicht authentifizierten Zugriff über Proxyserver auf manage.microsoft.com.

Sie können die Proxyservereinstellungen auf einzelnen Clientcomputern festlegen. Sie können zudem Gruppenrichtlinieneinstellungen verwenden, um die Einstellungen für alle Clientcomputer hinter einem bestimmten Proxyserver anzupassen.

Für verwaltete Geräte sind Konfigurationen erforderlich, über die **Alle Benutzer** über Firewalls auf Dienste zugreifen können.

In den folgenden Tabellen sind die Ports und Dienste aufgeführt, auf die der Intune-Client zugreift:

|**Endpunkt**|**IP-Adresse**|
|---------------------|-----------|
|*.manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>Vom Kunden festgelegte US Government-Endpunkte:
- Azure-Portal: https://portal.azure.us/ 
- Office 365: https://portal.office365.us/ 
- Intune-Unternehmensportal: https://portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Partner-Dienstendpunkte, von denen Intune abhängig ist:
- AAD Sync-Dienst: https://syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Evo STS: https://login.microsoftonline.us
- Directory-Anwendungsproxy: https://directoryproxy.microsoftazure.us/DirectoryProxy.svc
- AAD Graph: https://directory.microsoftazure.us und https://graph.microsoftazure.us
- MS Graph: https://graph.microsoft.us
- ADRS: https://enterpriseregistration.microsoftonline.us
