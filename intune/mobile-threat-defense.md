---
title: Mobile Threat Defense mit Microsoft Intune
titleSuffix: 
description: "Verwenden Sie Intune Mobile Threat Defense (MTD) mit Ihrem Mobile Threat Defense-Partner, um den Zugriff auf Unternehmensressourcen basierend auf dem Geräterisiko zu schützen."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 11/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2eaba4f04d6a1daedf40b7b37d2b44ed5aff4533
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>Was ist die Mobile Threat Defense-Integration in Intune?


Mit Intune Mobile Threat Defense-Connectors können Sie Ihren ausgewählten Mobile Threat Defense-Hersteller als Informationsquelle für Ihre Konformitätsrichtlinien und bedingte Zugriffsregeln nutzen. Dadurch können IT-Administratoren insbesondere für gefährdete Mobilgeräte eine Schutzebene zu ihren Unternehmensressourcen wie Exchange und SharePoint hinzufügen.

## <a name="what-problem-does-this-solve"></a>Welches Problem wird dadurch gelöst?

Unternehmen müssen vertrauliche Daten vor auftretenden Bedrohungen schützen. Dazu gehören physische, App-und netzwerkbasierte Bedrohungen sowie Sicherheitsrisiken beim Betriebssystem.

In der Vergangenheit haben Firmen PCs vor Angriffen proaktiv geschützt, während mobile Geräte nicht überwacht wurden und ungeschützt blieben. Mobile Plattformen bieten integrierten Schutz in Form von App-Isolierung und sicherheitsgeprüfter App Stores für Verbraucher, doch diese Plattformen bleiben weiterhin für komplexe Angriffe anfällig. Immer mehr Mitarbeiter nutzen ihre Geräte für die Arbeit und benötigen Zugriff auf vertrauliche Informationen. Geräte müssen gegen zunehmend raffinierter werdende Angriffe geschützt werden.

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Wie funktionieren die Intune Mobile Threat Defense-Connectors?

Der Connector schützt Unternehmensressourcen, indem er einen Kommunikationskanal zwischen Intune und Ihrem ausgewählten Mobile Threat Defense-Hersteller erstellt. Intune Mobile Threat Defense-Partner bieten intuitive und leicht bereitzustellende Anwendungen für Mobilgeräte, die aktiv Informationen zu Bedrohungen überprüfen und analysieren, um sie mit Intune für Berichts- oder Erzwingungszwecke zu teilen. 

Wenn eine verbundene Mobile Threat Defense-App z.B. einem Mobile Threat Defense-Hersteller mitteilt, dass ein Telefon in Ihrem Netzwerk aktuell mit einem Netzwerk verbunden ist, das anfällig für „Man in the Middle“-Angriffe ist, wird diese Information an eine entsprechende Risikostufe (niedrig/mittel/hoch) weitergeleitet. Diese kann anschließend mit Ihren konfigurierten Zulassungen der Risikostufe in Intune verglichen werden, um zu bestimmen, ob der Zugriff auf bestimmte Ressourcen Ihrer Wahl aufgehoben werden sollte, während das Gerät gefährdet ist.

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Welche Daten erfasst Intune für Mobile Threat Defense?

Intune erfasst sowohl von privaten als auch von unternehmenseigenen Geräten Informationen zum App-Bestand und stellt diese für Anbieter von Bedrohungserkennung auf Mobilgeräten (Mobile Thread Defense, MTD) wie Lookout for Work zur Verfügung. Sie können Informationen zum App-Bestand auf iOS 11-Geräten (oder höher) erfassen.

**App-Bestand**  
Die Bestände von sowohl unternehmenseigenen als auch privaten iOS 11-Geräten (oder höher) werden an Ihren MTD-Dienstanbieter übermittelt. Die Daten in den App-Beständen umfassen:

 - App-ID
 - App-Version
 - Kurzversion der App
 - App-Name
 - Größe des App-Pakets
 - Dynamische Größe der App
 - App wird geprüft oder nicht
 - App wird verwaltet oder nicht

## <a name="sample-scenarios"></a>Beispielszenarien

Wenn ein Gerät von der Mobile Threat Defense-Lösung als gefährdet eingestuft wird:

![Abbildung: mit Mobile Threat Defense geschütztes, gefährdetes Gerät](./media/MTD-image-1.png)

Der Zugriff wird gewährt, wenn das Gerät wiederhergestellt ist:

![Abbildung: Mobile Threat Defense – Zugriff gewährt](./media/MTD-image-2.png)

> [!NOTE] 
> Das Verwenden von mehreren Anbietern für Mobile Threat Defense (MTD) mit Intune wird nicht unterstützt. Wenn mehrere MTD-Tools aktiviert sind, wird die Installation von allen MTD-Apps erzwungen, die anschließend geräteübergreifend nach Bedrohungen sucht.

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense-Partner

Lernen Sie, wie Sie den Zugriffs auf Unternehmensressourcen auf der Basis von Geräte-, Netzwerk- und Anwendungsrisiko schützen:

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Skycure](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
