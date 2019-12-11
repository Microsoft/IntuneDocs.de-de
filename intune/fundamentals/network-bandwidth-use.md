---
title: Netzwerkanforderungen und Details zur Bandbreite für Microsoft Intune
titleSuffix: ''
description: Hier finden Sie Informationen zu den Netzwerkanforderungen und Details zur Bandbreite für Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0507d607bfac6c084f1ce0b1f59d7474810ec8b7
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73415108"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Anforderungen und Bandbreite an die Intune-Netzwerkkonfiguration

Sie können diese Informationen nutzen, um die Bandbreitenanforderungen für Ihre Intune-Bereitstellungen zu ermitteln.

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

Weitere Informationen zu BITS und Windows-Computern finden Sie unter [Background Intelligent Transfer Service](https://technet.microsoft.com/library/bb968799.aspx) in der TechNet-Bibliothek.

### <a name="delivery-optimization"></a>Übermittlungsoptimierung

Dank der Übermittlungsoptimierung können Sie Intune verwenden, um die Bandbreitennutzung zu reduzieren, wenn Ihre Windows 10-Geräte Anwendungen und Updates herunterladen. Durch einen sich selbst organisierenden, verteilten Cache können Downloads per Pull von herkömmlichen Servern und alternativen Quellen (wie z. B. Netzwerkpeers) abgerufen werden.

Die vollständige Liste aller Windows 10-Versionen und Inhaltstypen, die von der Übermittlungsoptimierung unterstützt werden, finden Sie im Artikel [Übermittlungsoptimierung für Windows 10-Updates](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#requirements).

Sie können die [Übermittlungsoptimierung](../configuration/delivery-optimization-settings.md) im Rahmen Ihrer Gerätekonfigurationsprofile einrichten.

### <a name="use-branchcache-on-computers"></a>Verwenden von BranchCache auf Computern

Intune-Clients können BranchCache verwenden, um den WAN-Datenverkehr zu verringern. Die folgenden Betriebssysteme unterstützen BranchCache:

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Zum Verwenden von BranchCache muss BranchCache auf dem Clientcomputer aktiviert und für den Modus **Verteilter Cache** konfiguriert sein.

Standardmäßig werden BranchCache und der Modus „Verteilter Cache“ auf Computern aktiviert, wenn der Intune-Client installiert wird. Wenn jedoch die Gruppenrichtlinie BranchCache deaktiviert, setzt Intune diese Richtlinie nicht außer Kraft, und BranchCache bleibt deaktiviert.

Wenn Sie BranchCache verwenden, arbeiten Sie mit den Administratoren in Ihrer Organisation, um die Gruppenrichtlinien und die Intune-Firewallrichtlinie zu verwalten. Stellen Sie sicher, dass sie keine Richtlinien bereitstellen, von denen BranchCache oder Firewall-Ausnahmen deaktiviert werden. Weitere Informationen zu BranchCache finden Sie unter [BranchCache: Übersicht](https://technet.microsoft.com/library/hh831696.aspx).

> [!NOTE]
> Sie können Ihre Windows-PCs mit Microsoft Intune entweder [mithilfe der Verwaltung mobiler Geräte (Mobile Device Management, MDM) als mobile Geräte](../enrollment/windows-enroll.md) oder mithilfe des Intune-Softwareclients als Computer verwalten. Microsoft empfiehlt Kunden, nach Möglichkeit die [MDM-Verwaltungslösung zu nutzen](../enrollment/windows-enroll.md). Bei dieser Art der Verwaltung wird BranchCache nicht unterstützt. Weitere Informationen finden Sie unter [Vergleichen der Verwaltung von Windows-PCs als Computer oder mobile Geräte](../pc-management-comparison.md).


## <a name="next-steps"></a>Nächste Schritte

[Endpunkte für Intune](../intune-endpoints.md)

