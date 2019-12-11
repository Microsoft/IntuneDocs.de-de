---
title: Firewallrichtlinien für Windows-PCs
titleSuffix: Microsoft Intune
description: Intune kann Ihnen auf verschiedene Weisen helfen, die mit dem Intune-Client verwalteten PCs zu schützen, beispielsweise durch Konfigurieren der Windows-Firewall-Einstellungen.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2c736c905045fd3afd40a12243986fbe69452ecd
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502829"
---
# <a name="help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune"></a>Unterstützen des Schutzes von Windows-PCs mithilfe von Windows-Firewall-Richtlinien in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

> [!NOTE]
> Die Informationen in diesem Thema gelten nur für Windows-Desktops, die Sie als PCs mithilfe des Intune-Softwareclients verwalten. Wenn Sie Firewalleinstellungen für als mobile Geräte registrierte Windows-PCs verwalten möchten, finden Sie weitere Informationen unter [Hinzufügen von Endpoint Protection-Einstellungen in InTune](../protect/endpoint-protection-configure.md).

Microsoft Intune kann Ihnen auf verschiedene Weisen helfen, die mit dem Intune-Client verwalteten PCs zu schützen. Eine Möglichkeit sind Richtlinien, über die sich Windows-Firewall-Einstellungen auf PCs konfigurieren lassen.

Falls Sie den Intune-Windows-PC-Client noch nicht auf Ihren Computern installiert haben, finden Sie unter [Installieren des Windows-PC-Clients mit Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md) weitere Informationen.

Verwenden Sie die Informationen in den folgenden Abschnitten, um Windows-Firewall-Richtlinien auf Windows-PCs zu konfigurieren, bereitzustellen und zu überwachen.

## <a name="use-intune-policies-to-manage-windows-firewall"></a>Verwalten der Windows-Firewall mithilfe von Intune-Richtlinien
Mit der Windows-Firewall-Richtlinie können Sie Einstellungen erstellen und bereitstellen, durch die die Windows-Firewall auf verwalteten PCs gesteuert wird. Es ist nicht möglich, benutzerdefinierte Ausnahmen für die Windows-Firewall zu verwalten, und die Einstellungen haben keine Auswirkungen auf Firewalls anderer Hersteller.

> [!NOTE]
> Wenn sowohl die Microsoft Intune-Richtlinie als auch die Gruppenrichtlinie zur Verwaltung der gleichen Einstellung auf einem Computer konfiguriert sind, hat die Einstellung der Gruppenrichtlinie Vorrang vor der Microsoft Intune-Richtlinie. Weitere Informationen zur Vermeidung von Konflikten zwischen Intune-Richtlinien und Gruppenrichtlinien finden Sie unter [Lösen von Konflikten mit Gruppenrichtlinienobjekten und Microsoft Intune-Richtlinien](resolve-gpo-and-microsoft-intune-policy-conflicts.md).
>
> Wenn Sie die Windows-Firewall-Einstellungen auf Computern mit Windows Vista bereitstellen möchten, müssen Sie auf diesen Computern zuerst [Hotfix KB971800](https://support2.microsoft.com/kb/971800) installieren.

> [!IMPORTANT]
> Zum Verwalten der Windows-Firewall mit Intune müssen Sie sicherstellen, dass die folgenden beiden Dienste auf den verwalteten Computern aktiviert sind:
>
> - Windows-Firewall
> - IPsec-Richtlinien-Agent

## <a name="configure-a-windows-firewall-policy"></a>Konfigurieren einer Windows-Firewall-Richtlinie

1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) **Richtlinie** &gt; **Richtlinie hinzufügen** aus.

2. Konfigurieren Sie eine Richtlinie für **Windows-Firewall-Einstellungen**, und stellen Sie sie bereit. Sie können die empfohlenen Einstellungen verwenden oder die Einstellungen anpassen. Weitere Informationen zum Erstellen und Bereitstellen von Richtlinien finden Sie unter [Allgemeine Aufgaben zur Verwaltung von Windows-PCs mit dem Microsoft Intune-Computerclient](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

    Im folgenden Abschnitt sind die Werte, die Sie in der Richtlinie konfigurieren können, sowie die Standardwerte aufgeführt, die verwendet werden, wenn Sie die Richtlinie nicht anpassen.

Nach Bereitstellen einer Windows-Firewall-Richtlinie können Sie ihren Status im Arbeitsbereich **Richtlinie** auf der Seite **Alle Richtlinien** anzeigen.

## <a name="specify-policy-settings-for-windows-firewall"></a>Angeben von Richtlinieneinstellungen für die Windows-Firewall

### <a name="turn-on-windows-firewall"></a>Windows-Firewall einschalten

Mit diesen Richtlinien aktivieren Sie die Windows-Firewall auf verwalteten Computern, die
- mit einer Domäne (z. B. am Arbeitsplatz) verbunden sind
- mit einem privaten (vertrauenswürdigen) Netzwerk (z. B. einem Heimnetzwerk) verbunden sind
- mit einem nicht vertrauenswürdigen öffentlichen Netzwerk (z. B. einem Internetcafé) verbunden sind

Der Standardwert für jede dieser Einstellungen ist **Ja** (der sicherste Wert).



### <a name="block-all-incoming-connections-including-those-in-the-list-of-allowed-programs"></a>Alle eingehenden Verbindungen blockieren, einschließlich der in der Liste der zugelassenen Programme

Mit diesen Richtlinieneinstellungen konfigurieren Sie die Windows-Firewall zum Blockieren von eingehendem Netzwerkverkehr auf verwalteten Computern, die
- mit einer Domäne (z. B. am Arbeitsplatz) verbunden sind
- mit einem privaten (vertrauenswürdigen) Netzwerk (z. B. einem Heimnetzwerk) verbunden sind
- mit einem nicht vertrauenswürdigen öffentlichen Netzwerk (z. B. einem Internetcafé) verbunden sind

Der Standardwert für jede dieser Einstellungen ist **Ja** (der sicherste Wert).

> [!IMPORTANT]
> Wenn in Ihrer Umgebung verwaltete Computer mit Windows Vista ohne installierte Service Packs vorhanden sind, müssen Sie entweder das Update installieren, das mit [Artikel 971800](https://go.microsoft.com/fwlink/?LinkId=188405) in der Microsoft Knowledge Base verknüpft ist, oder die Richtlinieneinstellung **Alle eingehenden Verbindungen blockieren** in den Richtlinien auf den entsprechenden Computern deaktivieren.

### <a name="notify-the-user-when-windows-firewall-blocks-a-new-program"></a>Benutzer benachrichtigen, wenn ein neues Programm von der Windows-Firewall blockiert wird

Mit diesen Richtlinieneinstellungen konfigurieren Sie, ob die Windows-Firewall die PC-Benutzer über das Blockieren von eingehendem Netzwerkverkehr auf verwalteten Computern benachrichtigt, die
- mit einer Domäne (z. B. am Arbeitsplatz) verbunden sind
- mit einem privaten (vertrauenswürdigen) Netzwerk (z. B. einem Heimnetzwerk) verbunden sind
- mit einem nicht vertrauenswürdigen öffentlichen Netzwerk (z. B. einem Internetcafé) verbunden sind

Der Standardwert für jede dieser Einstellungen ist **Ja**.


### <a name="configure-predefined-exceptions"></a>Konfigurieren vordefinierter Ausnahmen

Sie können Ausnahmen konfigurieren, die bestimmten durch die Firewall geleiteten Netzwerkverkehr unabhängig von den zuvor konfigurierten Werten zulassen. Standardmäßig ist keine dieser Einstellungen konfiguriert.

|Name der Einstellung|Details|
|------------------|--------------------|
|**BranchCache – Inhaltsabruf**<br>(Windows 7 oder höher)|Ermöglicht BranchCache-Clients, mithilfe von HTTP im verteilten Modus Inhalte von anderen BranchCache-Clients und im gehosteten Cachemodus Inhalte aus dem gehosteten Cache abzurufen. Bei dieser Einstellung wird HTTP verwendet.|
|**BranchCache – Gehosteter Cacheclient**<br>(Windows 7 oder höher)|Ermöglicht BranchCache-Clients, einen gehosteten Cache zu verwenden. Bei dieser Einstellung wird HTTPS verwendet.|
|**BranchCache – Gehosteter Cacheserver**|Ermöglicht BranchCache-Clients, einen gehosteten Cache zur Kommunikation mit anderen Clients zu verwenden. Bei dieser Einstellung wird HTTPS verwendet.|
|**BranchCache – Peerermittlung**<br>(Windows 7 oder höher)|Ermöglicht BranchCache-Clients, das WS-Discovery-Protokoll (Web Services Dynamic Discovery) zu verwenden, um die Verfügbarkeit von Inhalt im lokalen Subnetz zu ermitteln.|
|**BITS-Peercaching**|Ermöglicht Clients, BITS (Background Intelligent Transfer Service) zu verwenden, um Dateien zu finden und freizugeben, die im BITS-Cache von Clients im gleichen Subnetz gespeichert sind. Bei dieser Einstellung werden Webdienste für Geräte (Web Services on Devices, WSDAPI) und Remoteprozeduraufruf (Remote Procedure Call, RPC) verwendet.|
|**Verbindung mit einem Netzwerkprojektor herstellen**|Ermöglicht Benutzer, zum Projizieren von Präsentationen über drahtgebundene oder Drahtlosnetzwerke eine Verbindung mit Projektoren herzustellen. Bei dieser Einstellung wird WSDAPI verwendet.|
|**Kernnetzwerk**|Ermöglicht Clients das Verwenden von IPv4 und IPv6, um Verbindungen mit Netzwerkressourcen herzustellen.|
|**Distributed Transaction Coordinator**|Ermöglicht verwalteten Computern, Transaktionen zu koordinieren, durch die transaktionsgeschützte Ressourcen wie Datenbanken, Nachrichtenwarteschlangen und Dateisysteme aktualisiert werden.|
|**Datei- und Druckerfreigabe**|Ermöglicht Benutzern, lokale Dateien und Drucker für andere Benutzer im Netzwerk freizugeben. Bei dieser Einstellung werden NetBIOS, Multicastnamenauflösung für lokale Verbindungen (Link-Local Multicast Namensresolution, LLMNR), Server Message Block-Protokoll (SMB) und RPC verwendet.|
|**Heimnetzgruppe**<br>(Windows 7 oder höher)|Ermöglicht verwalteten Computern die Teilnahme an einem Netzwerk des Typs Heimnetzgruppe.|
|**iSCSI-Dienst**|Ermöglicht verwalteten Computern das Herstellen von Verbindungen mit iSCSI-Servern und -Geräten.|
|**Schlüsselverwaltungsdienst**|Ermöglicht die Zählung von Computern zur Lizenzüberprüfung in Unternehmensumgebungen.|
|**Media Center Extender**|Ermöglicht Media Center Extendern die Kommunikation mit Computern, auf denen Windows Media Center ausgeführt wird. Bei dieser Einstellung werden das Simple Service Discovery-Protokoll (SSDP) und qWave verwendet.|
|**Anmeldedienst**|Dient zum Konfigurieren eines Sicherheitskanals zwischen Domänenclients und einem Domänencontroller zum Authentifizieren von Benutzern und Diensten. Bei dieser Einstellung wird RPC verwendet.|
|**Netzwerkermittlung**|Ermöglicht, dass andere Geräte im Netzwerk von Computern erkannt werden, und die Computer ihrerseits von anderen Geräten im Netzwerk erkannt werden können. Bei dieser Einstellung werden Funktionssuchehost und Veröffentlichungsdienste sowie die Netzwerkprotokolle SSDP, NetBIOS, LLMNR und UPnP verwendet.|
|**Leistungsprotokolle und -warnungen**|Ermöglicht die Remoteverwaltung des Diensts für Leistungsprotokolle und -warnungen. Bei dieser Einstellung wird RPC verwendet.|
|**Remoteverwaltung**|Ermöglicht die Remoteverwaltung des Computers.|
|**Remoteunterstützung**|Diese Einstellung ermöglicht Benutzer verwalteter Computer Remoteunterstützung von anderen Benutzern im Netzwerk anzufordern. Bei dieser Einstellung werden die Netzwerkprotokolle SSDP, PNRP (Peer Name Resolution Protocol), Teredo und UPnP verwendet.|
|**Remotedesktop**|Ermöglicht dem Computer, Remotedesktop zu verwenden, um auf andere Computer zuzugreifen.|
|**Remote-Ereignisprotokollverwaltung**|Ermöglicht die Remoteanzeige bzw. -verwaltung von Clientereignisprotokollen. Bei dieser Einstellung werden Named Pipes und RPC verwendet.|
|**Remoteverwaltung geplanter Aufgaben**|Ermöglicht die Remoteverwaltung des Aufgabenplanungsdiensts. Bei dieser Einstellung wird RPC verwendet.|
|**Remotedienstverwaltung**|Ermöglicht die Remoteverwaltung lokaler Dienste auf Clients. Bei dieser Einstellung werden Named Pipes und RPC verwendet.|
|**Remotevolumeverwaltung**|Ermöglicht die Remoteverwaltung von Software- und Datenträgervolumes. Bei dieser Einstellung wird RPC verwendet.|
|**Routing und Remotezugriff**|Ermöglicht eingehende VPN- und Remotezugriffsverbindungen mit Computern.|
|**Secure Socket Tunneling-Protokoll**|Ermöglicht eingehende VPN-Verbindungen mit verwalteten Computern unter Verwendung des Secure Socket Tunneling-Protokolls (SSTP). Bei dieser Einstellung wird HTTPS verwendet.|
|**SNMP-Trap**|Ermöglicht verwalteten Computern das Empfangen von Datenverkehr des SNMP-Ablaufverfolgungsdiensts.|
|**UPnP-Framework**|Dient zum Konfigurieren des UPnP-Frameworkdiensts auf Computern, sodass UPnP-zertifizierte Geräte erkannt und verwendet werden können.|
|**Computernamen-Registrierungsdienst von Windows-Teamarbeit**|Ermöglicht Computern, unter Verwendung von SSDP und PNRP nach anderen Computern zu suchen und mit diesen zu kommunizieren.|
|**Windows Media Player**|Ermöglicht Benutzern das Empfangen von Streamingmedien über UDP (User Datagram Protocol).|
|**Windows Media Player-Netzwerkfreigabedienst**|Ermöglicht Benutzern das Freigeben von Medien über ein Netzwerk. Bei dieser Einstellung werden die Netzwerkprotokolle SSDP, qWave und UPnP verwendet.|
|**Windows Media Player-Netzwerkfreigabedienst (Internet)**<br>(Windows 7 oder höher)|Ermöglicht Benutzern, Heimmedien über das Internet freizugeben.|
|**Windows-Teamarbeit**|Ermöglicht Benutzern, über ein Netzwerk zusammenzuarbeiten, um Dokumente, Programme und den Desktop freizugeben. Bei dieser Einstellung werden die DFS-Replikation (Distributed File System Replication, DFSR) und P2P verwendet.|
|**Windows-Peer-zu-Peer-Zusammenarbeits-Foundation**|Konfiguriert verschiedene Peer-zu-Peer-Programme und -Technologien, um ihnen das Herstellen von Verbindungen zu ermöglichen. Bei dieser Einstellung werden SSDP und PNRP verwendet.|
|**Windows-Remoteverwaltung (Kompatibilität)**|Ermöglicht die Remoteverwaltung verwalteter Computer unter Verwendung von WS-Management, einem auf Webdiensten basierenden Protokoll für die Remoteverwaltung von Betriebssystemen und Geräten.|
|**Windows-Remoteverwaltung**<br>(Windows 8 oder höher)|Ermöglicht die Remoteverwaltung verwalteter Computer unter Verwendung von WS-Management, einem auf Webdiensten basierenden Protokoll für die Remoteverwaltung von Betriebssystemen und Geräten.|
|**Windows Virtual PC**<br>(Windows 7 oder höher)|Ermöglicht virtuellen Computern die Kommunikation mit anderen Computern.|
|**Tragbare Drahtlosgeräte**|Ermöglicht die Medienübertragung von einer netzwerkfähigen Kamera oder einem Mediengerät auf verwaltete Computer unter Verwendung des MTP-Protokolls (Media Transfer Protocol). Bei dieser Einstellung werden die Netzwerkprotokolle SSDP und UPnP verwendet.|

## <a name="see-also"></a>Siehe auch
[Richtlinien zum Schutz von Windows-PCs](policies-to-protect-windows-pcs-in-microsoft-intune.md)
