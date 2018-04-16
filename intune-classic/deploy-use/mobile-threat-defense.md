---
title: Intune Mobile Threat Defense
description: "Schützen Sie den Zugriff auf Unternehmensressourcen auf der Basis von Geräterisiko."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 08d87906-8158-4d5e-a49d-ad919efef3d1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 97711301422dd86ed0a76375add54987809c07b7
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="intune-mobile-threat-defense-connectors"></a>Intune Mobile Threat Defense-Connector

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Mit Intune Mobile Threat Defense-Connectors können Sie Ihren ausgewählten Mobile Threat Defense-Hersteller als Informationsquelle für Ihre Konformitätsrichtlinien und bedingte Zugriffsregeln nutzen. Dadurch können IT-Administratoren eine Schutzeben auf ihre Unternehmensressoucen wie Exchange und Sharepoint anwenden, besonders von gefährdeten Mobilgeräten.

## <a name="what-problem-does-this-solve"></a>Welches Problem wird dadurch gelöst?

Unternehmen müssen vertrauliche Daten vor auftretenden Bedrohungen schützen. Dazu gehören physische, App-und netzwerkbasierte Bedrohungen sowie Sicherheitsrisiken beim Betriebssystem.
In der Vergangenheit haben Firmen PCs vor Angriffen proaktiv geschützt, während mobile Geräte nicht überwacht wurden und ungeschützt blieben. Mobile Plattformen verfügen über einen integrierten Schutz des Betriebssystems durch Techniken wie die Isolierung von Apps oder überprüfte App Stores für Heimanwender, aber diese Plattformen sind trotzdem noch anfällig für komplexe Angriffe. Immer mehr Mitarbeiter nutzen ihre Geräte für die Arbeit und benötigen Zugriff auf vertrauliche Informationen. Geräte müssen gegen zunehmend raffinierter werdende Angriffe geschützt werden.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Wie funktioniert der Intune Mobile Threat Defense-Connector?

Der Connector schützt Unternehmensressourcen, indem er einen Kommunikationskanal zwischen Intune und Ihrem ausgewählten Mobile Threat Defense-Hersteller erstellt. Intune Mobile Threat Defense-Partner bieten intuitive und leicht bereitzustellende Anwendungen für Mobilgeräte, die aktiv Informationen zu Bedrohungen überprüfen und analysieren, um sie mit Intune für Berichts- oder Erzwingungszwecke zu teilen. Wenn eine verbundene Mobile Threat Defense-App z.B. einem Mobile Threat Defense-Hersteller mitteilt, dass ein Telefon in Ihrem Netzwerk aktuell mit einem Netzwerk verbunden ist, das anfällig für „Man in the Middle“-Angriffe ist, wird diese Information an eine entsprechende Risikostufe (niedrig/mittel/hoch) weitergeleitet. Diese kann anschließend mit Ihren konfigurierten Zulassungen der Risikostufe in Intune verglichen werden, um zu bestimmen, ob der Zugriff auf bestimmte Ressourcen Ihrer Wahl aufgehoben werden sollte, während das Gerät gefährdet ist.

## <a name="sample-scenarios"></a>Beispielszenarien

Wenn ein Gerät von der Mobile Threat Defense-Lösung als gefährdet eingestuft wird:

![Mobile Threat Defense infected device (Mobile Threat Defense – Gefährdetes Gerät)](../media/mtp/MTD-image-1.png)

Der Zugriff wird gewährt, wenn das Gerät wiederhergestellt ist:

![Mobile Threat Defense Access granted (Mobile Threat Defense – Zugriff gewährt)](../media/mtp/MTD-image-2.png)

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense-Partner

Lernen Sie, wie Sie den Zugriffs auf Unternehmensressourcen auf der Basis von Geräte-, Netzwerk- und Anwendungsrisiko schützen:

- [Lookout](/intune-classic/deploy-use/lookout-mobile-threat-defense-connector)
- [Skycure](/intune-classic/deploy-use/skycure-mobile-threat-defense-connector)
