---
title: Netzwerkanforderungen und Details zur Bandbreite für Microsoft Intune
titlesuffix: ''
description: Hier finden Sie Informationen zu den Netzwerkanforderungen und Details zur Bandbreite für Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.openlocfilehash: 243e9602a253fecf2eda1dd73dfb49a488db0974
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190250"
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

Informationen zur Verwendung eines Proxyservers zum Zwischenspeichern von Inhalt entnehmen Sie der Dokumentation zu Ihrer Proxyserverlösung.

### <a name="use-background-intelligent-transfer-service-on-computers"></a>Verwenden von Background Intelligent Transfer Service auf Computern
Intune unterstützt die Verwendung von BITS (Background Intelligent Transfer Service) auf einem Windows-Computer, um die im von Ihnen konfigurierten Zeitraum beanspruchte Netzwerkbandbreite zu verringern. Die BITS-Richtlinie können Sie auf der Seite **Netzwerkbandbreite** der Intune-Agent-Richtlinie konfigurieren.

Weitere Informationen zu BITS und Windows-Computern finden Sie unter [Background Intelligent Transfer Service](http://technet.microsoft.com/library/bb968799.aspx) in der TechNet-Bibliothek.

### <a name="use-branchcache-on-computers"></a>Verwenden von BranchCache auf Computern
Intune-Clients können BranchCache verwenden, um den WAN-Datenverkehr zu verringern. Die folgenden Betriebssysteme unterstützen BranchCache:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Zum Verwenden von BranchCache muss BranchCache auf dem Clientcomputer aktiviert und für den Modus **Verteilter Cache** konfiguriert sein.

Standardmäßig werden BranchCache und der Modus „Verteilter Cache“ auf Computern aktiviert, wenn der Intune-Client installiert wird. Wenn jedoch die Gruppenrichtlinie BranchCache deaktiviert hat, überschreibt Intune diese Richtlinie nicht, und BranchCache bleibt deaktiviert.

Wenn Sie BranchCache verwenden, arbeiten Sie mit den Administratoren in Ihrer Organisation, um die Gruppenrichtlinien und die Intune-Firewallrichtlinie zu verwalten. Stellen Sie sicher, dass sie keine Richtlinien bereitstellen, von denen BranchCache oder Firewall-Ausnahmen deaktiviert werden. Weitere Informationen zu BranchCache finden Sie unter [BranchCache: Übersicht](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Anforderungen für die Netzwerkkommunikation

Aktivieren Sie die Netzwerkkommunikation zwischen den verwalteten Geräten und den Websites, die für cloudbasierte Dienste benötigt werden.

Intune verwendet keine lokale Infrastruktur, z.B. einen Server, auf dem die Intune-Software ausgeführt wird. Es gibt jedoch Optionen zum Verwenden einer lokalen Infrastruktur, darunter Synchronisierungstools für Exchange und Active Directory.

Um Computer hinter Firewalls und Proxyserver zu verwalten, müssen Sie die Kommunikation für Intune aktivieren.

-   Der Proxyserver muss sowohl **HTTP** (80) als auch **HTTPS** (443) unterstützen, da Intune-Clients beide Protokolle verwenden.
-   Intune erfordert Zugriff auf nicht authentifizierte Proxyserver auf manage.microsoft.com für einige Aufgaben wie das Herunterladen von Software und Updates.

Sie können Proxyservereinstellungen entweder auf einzelnen Clientcomputern modifizieren oder mithilfe der Gruppenrichtlinieneinstellungen für alle Clientcomputer hinter einem bestimmten Proxyserver ändern.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

Für verwaltete Geräte sind Konfigurationen erforderlich, über die **Alle Benutzer** über Firewalls auf Dienste zugreifen können.

In den folgenden Tabellen sind die Ports und Dienste aufgeführt, auf die der Intune-Client zugreift:

|**Domänen**|**IP-Adresse**|
|---------------------|-----------|
|login.microsoftonline.com | Weitere Informationen finden Sie unter [URLs und IP-Adressbereiche von Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2). |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |40.86.181.86<br>13.82.59.78<br>13.74.184.100<br>40.68.188.2<br>13.75.42.6<br>52.230.25.184 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 104.40.82.191 <br>13.82.96.212 <br>52.169.9.87 <br>52.174.26.23 <br>40.83.123.72 <br>13.76.177.110 <br>52.234.146.75 |
|portal.fei.msua01.manage.microsoft.com<br>m.fei.msua01.manage.microsoft.com |13.64.196.170|
|fei.msua01.manage.microsoft.com<br> portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com |40.71.34.120 |
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com |13.64.198.190|
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br> m.fei.msua02.manage.microsoft.com |  13.64.198.190|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |13.64.188.173|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |40.71.32.174|
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |13.64.197.181 |
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |40.71.38.205|
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |13.64.191.182 |
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |40.71.37.51 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |40.118.250.246 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |13.90.142.194 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.64.250.226 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.90.151.142 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.169.155.165 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.174.188.97 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.178.190.24 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.174.16.215 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |40.69.69.27 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |52.166.196.199 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |40.69.71.164 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |52.174.182.102 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |40.69.78.145 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |52.174.192.105 |
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |13.94.46.250|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |52.163.119.15 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |13.75.124.145 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |52.163.119.5|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.175.35.226|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.163.119.6|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.175.38.24|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.163.119.3|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|23.97.165.17|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
|enterpriseregistration.windows.net|52.175.211.189|

### <a name="apple-device-network-information"></a>Informationen zum Netzwerk von Apple-Geräten

|         Hostname         |                                        URL (IP-Adresse/Subnetz)                                        |  Protokoll  |     Port     |                          Gerät                           |
|--------------------------|-------------------------------------------------------------------------------------------------------|------------|--------------|-----------------------------------------------------------|
|      Verwaltungskonsole       |                                  gateway.push.apple.com (17.0.0.0/8)                                  |    TCP     |     2195     |                    Apple iOS und macOS                    |
|      Verwaltungskonsole       |                                  feedback.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2196     |                    Apple iOS und macOS                    |
|      Verwaltungskonsole       | Apple iTunesitunes.apple.com, \*.mzstatic.com, \*.phobos.apple.com, \*.phobos.apple.com.edgesuite.net |    HTTP    |      80      |                    Apple iOS und macOS                    |
|        PI-Server         |                gateway.push.apple.com(17.0.0.0/8) feedback.push.apple.com(17.0.0.0/8)                 |    TCP     |  2195, 2196  |         Zum Cloud Messaging unter Apple iOS und macOS          |
|     Gerätedienste      |                                        gateway.push.apple.com                                         |    TCP     |     2195     |                           Apple                           |
|     Gerätedienste      |                                        feedback.push.apple.com                                        |    TCP     |     2196     |                           Apple                           |
|     Gerätedienste      |   Apple iTunesitunes.apple.com \*.mzstatic.com\*.phobos.apple.com \*.phobos.apple.com.edgesuite.net   |    HTTP    |      80      |                           Apple                           |
| Geräte (Internet/WLAN) |                                 #-courier.push.apple.com(17.0.0.0/8)                                  |    TCP     | 5223 und 443 | Nur Apple &#39;#&#39; ist eine zufällige Zahl zwischen 0 und 200. |
| Geräte (Internet/WLAN) |                           phobos.apple.comocsp.apple.comax.itunes.apple.com                           | HTTP/HTTPS |  80 oder 443   |                        Nur Apple                         |

