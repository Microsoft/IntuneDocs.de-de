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
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f6682cb-5fcd-4018-b7f7-71768ad3152e
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: dfa93bb758447c872d172ded7706fd7507a42f11
ms.sourcegitcommit: c7c6be3833d9a63d43f31d598b555b49b33cf5cb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2020
ms.locfileid: "76966282"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>US Government-Endpunkte für Microsoft Intune

Auf dieser Seite werden die US Government-Endpunkte aufgelistet, die für die Proxyeinstellungen in Ihren Intune-Bereitstellungen erforderlich sind.

Sie müssen die Kommunikation für Intune aktivieren, um Geräte hinter Firewalls und Proxyservern zu verwalten.

- Der Proxyserver muss sowohl **HTTP** (80) als auch **HTTPS** (443) unterstützen, da Intune-Clients beide Protokolle verwenden.
- Für einige Aufgaben wie das Herunterladen von Software und Updates erfordert Intune nicht authentifizierten Zugriff über Proxyserver auf manage.microsoft.com.

Sie können die Proxyservereinstellungen auf einzelnen Clientcomputern festlegen. Sie können zudem Gruppenrichtlinieneinstellungen verwenden, um die Einstellungen für alle Clientcomputer hinter einem bestimmten Proxyserver anzupassen.

Für verwaltete Geräte sind Konfigurationen erforderlich, über die **Alle Benutzer** über Firewalls auf Dienste zugreifen können.

Weitere Informationen zur automatischen Windows 10-Registrierung und zur Geräteregistrierung für Kunden der US-Registrierung finden Sie unter [Einrichten der Registrierung für Windows-Geräte](../enrollment/windows-enroll.md#windows-10-auto-enrollment-and-device-registration).

In den folgenden Tabellen sind die Ports und Dienste aufgeführt, auf die der Intune-Client zugreift:

|**Endpunkt**|**IP-Adresse**|
|---------------------|-----------|
|*.manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>Vom Kunden festgelegte US Government-Endpunkte:
- Azure-Portal: https:\//portal.azure.us/ 
- Office 365: https:\//portal.office365.us/ 
- Intune-Unternehmensportal: https:\//portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Partner-Dienstendpunkte, von denen Intune abhängig ist:
- AAD Sync-Dienst: https:\//syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Evo STS: https:\//login.microsoftonline.us
- Verzeichnisproxy: https:\//directoryproxy.microsoftazure.us/DirectoryProxy.svc
- AAD Graph: https:\//directory.microsoftazure.us and https:\//graph.microsoftazure.us
- MS Graph: https:\//graph.microsoft.us
- ADRS: https:\//enterpriseregistration.microsoftonline.us

## <a name="windows-push-notification-services"></a>Windows-Pushbenachrichtigungsdienste
Für von Intune verwaltete Geräte, die mithilfe der mobilen Geräteverwaltung (Mobile Device Management, MDM) verwaltet werden, sind Windows-Pushbenachrichtigungsdienste (Windows Push Notification Services, WNS) für Geräteaktionen und andere sofortige Aktivitäten erforderlich. Weitere Informationen finden Sie unter [Enterprise-Firewall und Proxykonfigurationen zur Unterstützung von WNS-Datenverkehr](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config).

## <a name="apple-device-network-information"></a>Informationen zum Netzwerk von Apple-Geräten

|**Verwendung**|**Hostname (IP-Adresse/-Subnetz)**|**Protokoll**|**Port**|
|------------|-----------|------------|-----------|
|Abrufen und Anzeigen von Inhalten von Apple-Servern|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br>\*.phobos.itunes-apple.com.akadns.net|HTTP|80|
|Kommunikation mit APNs-Servern|#-courier.push.apple.com<br># ist eine zufällige Zahl zwischen 0 und 50.|TCP|5223 und 443|
|Verschiedene Funktionen, z. B. Zugriff auf das Internet, den iTunes Store, den macOS App Store, iCloud, Messaging usw.|phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net|HTTP/HTTPS|80 oder 443|

Weitere Informationen finden Sie in folgenden Quellen:

- [Von Apple-Softwareprodukten verwendete TCP- und UDP-Ports](https://support.apple.com/HT202944)
- [Informationen zu macOS-, iOS- und iTunes-Server-Hostverbindungen und iTunes-Hintergrundprozessen](https://support.apple.com/HT201999)
- [Wenn Ihre macOS- und iOS-Clients keine Apple Push-Benachrichtigungen empfangen](https://support.apple.com/HT203609)

## <a name="next-steps"></a>Nächste Schritte
[Netzwerkendpunkte für Microsoft Intune](intune-endpoints.md)

