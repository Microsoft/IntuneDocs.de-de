---
title: Hinzufügen von Endpoint Protection unter macOS in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie auf macOS-Geräten den Gatekeeper, um zu bestimmen, wo Apps, einschließlich der Mac App Store, installiert werden können. Aktivieren oder Konfigurieren Sie ebenfalls eine Firewall, um bestimmte Apps zuzulassen, zu blockieren, den geschützten Modus zu verwenden oder bestimmte Arten von eingehenden Verbindungen mithilfe von Microsoft Intune zu blockieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e050d188d4508225ef384fbf557e7724efacab18
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047736"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Endpoint Protection-Einstellungen in Intune unter macOS

In diesem Artikel werden die Endpoint Protection-Einstellungen beschrieben, die Sie für Ihre macOS-Geräte konfigurieren können. Zu diesen Einstellungen zählen Gatekeeper- und Firewalleinstellungen auf diesen Geräten. Die Einstellungen können mithilfe eines Geräteprofils in Microsoft Intune konfiguriert werden.

## <a name="gatekeeper"></a>Gatekeeper

- **Apps aus den folgenden Downloadquellen zulassen:** Beschränkt Apps abhängig davon, von wo sie heruntergeladen wurden. Dadurch sollen Geräte vor Schadsoftware geschützt werden, außerdem werden nur Apps von vertrauenswürdigen Quellen zugelassen. Folgende Optionen sind verfügbar: 
  - **Mac App Store**
  - **Mac App Store und verifizierte Entwickler**
  - **Anywhere** (Beliebig)

- **Benutzer kann Gatekeeper außer Kraft setzen:** Hindert Benutzer am Außerkraftsetzen der Gatekeeper-Einstellungen und vom Installieren von Apps durch STRG+Klick Wenn diese Einstellung aktiviert ist, kann der Benutzer eine beliebige App mithilfe von STRG+Klick installieren.

## <a name="firewall"></a>Firewall

Verwenden Sie die Firewall, um Verbindungen pro Anwendung statt pro Port zu steuern. Wenn Sie die Einstellung „Pro Anwendung“ verwenden, können Sie die Vorteile des Schutzes durch die Firewall besser nutzen. Dadurch wird ebenfalls verhindert, dass unerwünschte Apps die Netzwerkports steuern, die für zulässige Apps geöffnet sind.

- **Verwenden der Firewall zum Schützen von Geräten vor unautorisiertem Netzwerkzugriff durch Steuern der Verbindung pro Anwendung**
  - **Firewall:** Aktivieren Sie die Firewall, um zu konfigurieren, wie eingehende Verbindung in Ihrer Umgebung behandelt werden.
  - **Eingehende Verbindungen:** Blockiert alle eingehenden Verbindungen außer denen, die für grundlegende Internetdienste erforderlich sind, z.B. DHCP, Bonjour und IPSec. Durch dieses Feature werden alle Freigabedienste blockiert, z.B. die Dateifreigabe und die Bildschirmfreigabe. Wenn Sie Freigabedienste verwenden, behalten Sie **Nicht konfiguriert** für diese Einstellung bei.

- **Zulassen oder Blockieren eingehender Verbindungen für bestimmte Apps**
  - **Zugelassene Apps:** Wählen Sie die Apps aus, die explizit für eingehende Verbindungen zugelassen sind.
  - **Blockierte Apps:** Wählen Sie die Apps aus, für die eingehende Verbindungen blockiert werden sollen.
  - **Geschützter Modus:** Hindern Sie den Computer daran, auf Suchanforderungen zu antworten, indem Sie den geschützten Modus aktivieren. Das Gerät antwortet weiterhin auf eingehende Anforderungen für autorisierte Apps. Unerwartete Anforderungen, wie z.B. ICMP (Ping), werden ignoriert.
