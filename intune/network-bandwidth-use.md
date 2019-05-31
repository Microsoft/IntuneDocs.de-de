---
title: Netzwerkanforderungen und Details zur Bandbreite für Microsoft Intune
titleSuffix: ''
description: Hier finden Sie Informationen zu den Netzwerkanforderungen und Details zur Bandbreite für Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40f9ada715570de7b5b2f95292b7ed0d238242d2
ms.sourcegitcommit: 04d29d47b61486b3586a0e0e5e8e48762351f2a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59570792"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Anforderungen und Bandbreite an die Intune-Netzwerkkonfiguration

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Diese Anleitung klärt Intune-Administratoren über die Netzwerkanforderungen für den Intune-Dienst auf. Mithilfe dieser Informationen können Sie feststellen, welche Bandbreitenanforderungen gestellt werden und welche IP-Adressen und Porteinstellungen für die Proxyeinstellungen erforderlich sind.

## <a name="average-network-traffic"></a>Durchschnittlicher Netzwerkdatenverkehr
Die Tabelle führt den ungefähren Umfang und die Häufigkeit gemeinsamer Inhalte auf, die pro Client über das Netzwerk übertragen werden.

> [!NOTE]
> Um sicherzustellen, dass Geräte Updates und Inhalt von Intune empfangen, müssen Sie zeitweise mit dem Internet verbunden sein. Die Zeit, die für das Empfangen von Updates oder Inhalten benötigt wird, kann variieren, sie sollten jedoch für mindestens eine Stunde pro Tag kontinuierlich mit dem Internet verbunden sein.

|Art des Inhalts|Ungefähre Größe|Häufigkeit und Details|
|----------------|--------------------|-------------------------|
|Intune-Clientinstallation<br /><br />**Die folgenden Anforderungen gelten zusätzlich zur Intune-Clientinstallation**|125 MB|**Einmalig**<br /><br />Der Umfang des Clientdownloads schwankt je nach Betriebssystem des Clientcomputers.|
|Clientregistrierungspaket|15 MB|**Einmalig**<br /><br />Weitere Downloads sind möglich, wenn Updates für diesen Inhaltstyp vorliegen.|
|Endpoint Protection-Agent|65 MB|**Einmalig**<br /><br />Weitere Downloads sind möglich, wenn Updates für diesen Inhaltstyp vorliegen.|
|Operations Manager-Agent|11 MB|**Einmalig**<br /><br />Weitere Downloads sind möglich, wenn Updates für diesen Inhaltstyp vorliegen.|
|Richtlinien-Agent|3 MB|**Einmalig**<br /><br />Weitere Downloads sind möglich, wenn Updates für diesen Inhaltstyp vorliegen.|
|Remoteunterstützung über den Microsoft Easy Assist-Agent|6 MB|**Einmalig**<br /><br />Weitere Downloads sind möglich, wenn Updates für diesen Inhaltstyp vorliegen.|
|Tägliche Clientvorgänge|6 MB|**Täglich**<br /><br />Der Intune-Client kommuniziert regelmäßig mit dem Intune-Dienst, um nach Updates und Richtlinien zu suchen und den Status des Clients an den Dienst zu melden.|
|Malwaredefinitionsupdates für Endpoint Protection|Variiert<br /><br />Normalerweise zwischen 40 KB und 2 MB|**Täglich**<br /><br />Bis zu drei Mal täglich.|
|Endpoint Protection-Engine-Update|5 MB|**Monatlich**|
|Softwareupdates|Variiert<br /><br />Die Größe hängt von den von Ihnen bereitgestellten Updates ab.|**Monatlich**<br /><br />Normalerweise werden Softwareupdates am zweiten Dienstag eines jeden Monats bereitgestellt.<br /><br />Durch einen neu registrierten oder bereitgestellten Computer kann mehr Netzwerkbandbreite verwendet werden, solange alle zuvor veröffentlichten Updates heruntergeladen werden.|
|Service Packs|Variiert<br /><br />Die Größe variiert für jedes von Ihnen bereitgestellte Service Pack.|**Variiert**<br /><br />Hängt vom Zeitpunkt der Service Pack-Bereitstellung ab.|
|Softwareverteilung|Variiert<br /><br />Die Größe hängt von der von Ihnen bereitgestellten Software ab.|**Variiert**<br /><br />Hängt vom Zeitpunkt der Softwarebereitstellung ab.|

## <a name="ways-to-reduce-network-bandwidth-use"></a>Möglichkeiten zum Verringern der Bandbreitennutzung
Mithilfe der folgenden Methoden können Sie die Nutzung der Netzwerkbandbreite für Intune-Clients reduzieren.

### <a name="use-a-proxy-server-to-cache-content-requests"></a>Verwenden eines Proxyservers zum Zwischenspeichern von Inhaltsanforderungen
Ein Proxyserver kann Inhalt zwischenspeichern, um doppelte Downloads zu vermeiden und die Bandbreitennutzung von Inhalten aus dem Internet zu verringern.

Ein Proxyserver mit Zwischenspeicherung, der Inhaltsanfragen von Clients empfängt, kann diesen Inhalt abrufen und Webantworten und Downloads zwischenspeichern. Der Server verwendet zwischengespeicherte Daten, um nachfolgende Anforderungen von Clients zu beantworten.

Nachfolgend werden typische Einstellungen für die Verwendung eines Proxyservers aufgeführt, mit dem Inhalt für Intune-Clients zwischengespeichert wird.


|          Einstellung           |           Empfohlener Wert           |                                                                                                  Details                                                                                                  |
|----------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Cachegröße         |             5-30 GB             | Dieser Wert schwankt abhängig von der Anzahl von Clientcomputern in Ihrem Netzwerk und den von Ihnen verwendeten Konfigurationen. Damit Dateien nicht zu schnell gelöscht werden, stellen Sie die Größe des Zwischenspeichers passend für Ihre Umgebung ein. |
| Größe der einzelnen Cachedatei |                950 MB                 |                                                                     Diese Einstellung ist möglicherweise nicht für alle Proxyserver mit Zwischenspeicherung verfügbar.                                                                     |
|   Objekttypen, die zwischengespeichert werden    | HTTP<br /><br />HTTPS<br /><br />BITS |                                               Intune-Pakete sind CAB-Dateien, die per BITS-Download (Background Intelligent Transfer Service) über HTTP abgerufen wurden.                                               |
> [!NOTE]
> Wenn Sie einen Proxyserver zum Zwischenspeichern von Inhaltsanforderungen verwenden, wird die Kommunikation nur zwischen dem Client und dem Proxy und zwischen dem Proxy und Intune verschlüsselt. Die Verbindung zwischen dem Client und Intune wird nicht durchgehend verschlüsselt.

Informationen zur Verwendung eines Proxyservers zum Zwischenspeichern von Inhalt entnehmen Sie der Dokumentation zu Ihrer Proxyserverlösung.

### <a name="use-background-intelligent-transfer-service-bits-on-computers"></a>Verwenden des Background Intelligent Transfer Service (BITS) auf Computern
Sie können in einem in Ihnen festgelegten Zeitraum den BITS auf einem Windows-Computer verwenden, um die Netzwerkbandbreite zu reduzieren. Sie können die BITS-Richtlinie auf der Seite **Netzwerkbandbreite** der Intune-Agent-Richtlinie konfigurieren.

> [!NOTE]
> Für die Verwaltung mobiler Geräte unter Windows verwendet nur die Verwaltungsschnittstelle des Betriebssystems für den App-Typ MobileMSI den BITS zum Download. AppX/MsiX verwenden ihren eigenen Nicht-BITS-Downloadstapel, und Win32-Apps verwenden die Übermittlungsoptimierung statt des BITS über den Intune-Agent.

Weitere Informationen zu BITS und Windows-Computern finden Sie unter [Background Intelligent Transfer Service](http://technet.microsoft.com/library/bb968799.aspx) in der TechNet-Bibliothek.

### <a name="use-branchcache-on-computers"></a>Verwenden von BranchCache auf Computern
Intune-Clients können BranchCache verwenden, um den WAN-Datenverkehr zu verringern. Die folgenden Betriebssysteme unterstützen BranchCache:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Zum Verwenden von BranchCache muss BranchCache auf dem Clientcomputer aktiviert und für den Modus **Verteilter Cache** konfiguriert sein.

Standardmäßig werden BranchCache und der Modus „Verteilter Cache“ auf Computern aktiviert, wenn der Intune-Client installiert wird. Wenn jedoch die Gruppenrichtlinie BranchCache deaktiviert, setzt Intune diese Richtlinie nicht außer Kraft, und BranchCache bleibt deaktiviert.

Wenn Sie BranchCache verwenden, arbeiten Sie mit den Administratoren in Ihrer Organisation, um die Gruppenrichtlinien und die Intune-Firewallrichtlinie zu verwalten. Stellen Sie sicher, dass sie keine Richtlinien bereitstellen, von denen BranchCache oder Firewall-Ausnahmen deaktiviert werden. Weitere Informationen zu BranchCache finden Sie unter [BranchCache: Übersicht](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Anforderungen für die Netzwerkkommunikation

Aktivieren Sie die Netzwerkkommunikation zwischen den von Ihnen verwalteten Geräten und den Endpunkten, die für cloudbasierte Dienste erforderlich sind.

Da Intune ein Clouddienst ist, ist keine lokale Infrastruktur wie etwa Server oder Gateways erforderlich.

Sie müssen die Kommunikation für Intune aktivieren, um Geräte hinter Firewalls und Proxyservern zu verwalten.

- Der Proxyserver muss sowohl **HTTP** (80) als auch **HTTPS** (443) unterstützen, da Intune-Clients beide Protokolle verwenden.
- Für einige Aufgaben wie das Herunterladen von Software und Updates erfordert Intune nicht authentifizierten Zugriff über Proxyserver auf manage.microsoft.com.

Sie können die Proxyservereinstellungen auf einzelnen Clientcomputern festlegen. Sie können zudem Gruppenrichtlinieneinstellungen verwenden, um die Einstellungen für alle Clientcomputer hinter einem bestimmten Proxyserver anzupassen.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

Für verwaltete Geräte sind Konfigurationen erforderlich, über die **Alle Benutzer** über Firewalls auf Dienste zugreifen können.

In den folgenden Tabellen sind die Ports und Dienste aufgeführt, auf die der Intune-Client zugreift:

|**Domänen**|**IP-Adresse**|
|---------------------|-----------|
|login.microsoftonline.com | Weitere Informationen finden Sie unter [URLs und IP-Adressbereiche von Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2). |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |52.175.12.209<br>20.188.107.228<br>52.138.193.149<br>51.144.161.187<br>52.160.70.20<br>52.168.54.64 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 40.83.123.72<br>13.76.177.110<br>52.169.9.87<br>52.174.26.23<br>104.40.82.191<br>13.82.96.212|
|fei.msua01.manage.microsoft.com<br>portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com<br>fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>fei.msua04.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.amsua0202.manage.microsoft.com <br>portal.fei.amsua0202.manage.microsoft.com <br>m.fei.amsua0202.manage.microsoft.com<br>fei.amsua0402.manage.microsoft.com <br>portal.fei.amsua0402.manage.microsoft.com <br>m.fei.amsua0402.manage.microsoft.com|52.160.70.20<br>52.168.54.64 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>fei.amsub0202.manage.microsoft.com <br>portal.fei.amsub0202.manage.microsoft.com <br>m.fei.amsub0202.manage.microsoft.com<br>fei.amsub0302.manage.microsoft.com <br>portal.fei.amsub0302.manage.microsoft.com <br>m.fei.amsub0302.manage.microsoft.com|52.138.193.149<br>51.144.161.187|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com|52.175.12.209<br>20.188.107.228|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|52.169.82.238|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
|fef.amsua0202.manage.microsoft.com|52.165.165.17|
|fef.amsua0402.manage.microsoft.com|40.69.157.122|
|fef.amsua0502.manage.microsoft.com|13.85.68.142|
|fef.amsua0602.manage.microsoft.com|52.161.28.64|
|fef.amsub0102.manage.microsoft.com|40.118.98.207|
|fef.amsub0202.manage.microsoft.com|40.69.208.122|
|fef.amsub0302.manage.microsoft.com|13.74.145.65|
|enterpriseregistration.windows.net|52.175.211.189|
|Admin.manage.microsoft.com|52.224.221.227<br>52.161.162.117<br>52.178.44.195<br>52.138.206.56<br>52.230.21.208<br>13.75.125.10|
|wip.mam.manage.microsoft.com|52.187.76.84<br>13.76.5.121<br>52.165.160.237<br>40.86.82.163<br>52.233.168.142<br>168.63.101.57|
|mam.manage.microsoft.com|104.40.69.125<br>13.90.192.78<br>40.85.174.177<br>40.85.77.31<br>137.116.229.43<br>52.163.215.232<br>52.174.102.180|






### <a name="apple-device-network-information"></a>Informationen zum Netzwerk von Apple-Geräten


|Verwendet für|Hostname (IP-Adresse/-Subnetz)|Protokoll|Port|
|-----|--------|------|-------|
|Empfangen von Pushbenachrichtigungen von Intune über den Apple Push Notification Service (APNs). Weitere Informationen finden Sie in der [Apple-Dokumentation](https://support.apple.com/en-us/HT203609).|                                    gateway.push.apple.com (17.0.0.0/8)                                  |    TCP     |     2195     |
|Senden von Feedback an Intune über den Apple Push Notification Service (APNs)|                                  feedback.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2196     |
|Abrufen und Anzeigen von Inhalten von Apple-Servern|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br> \*.phobos.itunes-apple.com.akadns.net |    HTTP    |      80      |
|Kommunikation mit APNs-Servern|#-courier.push.apple.com (17.0.0.0/8)<br># ist eine zufällige Zahl zwischen 0 und 50.|    TCP     |  5223 und 443  |
|Verschiedene Funktionen, z. B. Zugriff auf das Internet, den iTunes Store, den App Store, iCloud, Messaging usw. |phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net| HTTP/HTTPS |  80 oder 443   |

Weitere Informationen finden Sie in den Apple-Artikeln [Von Apple-Softwareprodukten verwendete TCP- und UDP-Ports](https://support.apple.com/en-us/HT202944), [Informationen zu macOS-, iOS- und iTunes-Server-Hostverbindungen und iTunes-Hintergrundprozessen](https://support.apple.com/en-us/HT201999) und [Wenn Ihre macOS- und iOS-Clients keine Apple Push-Benachrichtigungen empfangen](https://support.apple.com/en-us/HT203609).
