---
title: Mobile Threat Defense mit Microsoft Intune
titleSuffix: Microsoft Intune
description: Verwenden Sie Intune Mobile Threat Defense (MTD) mit Ihrem Mobile Threat Defense-Partner, um den Zugriff auf Unternehmensressourcen basierend auf dem Geräterisiko zu schützen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/20/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e364ad88591b8ecc945702659255d9378723624f
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61513014"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>Was ist die Mobile Threat Defense-Integration in Intune?
Intune kann Daten von einem Mobile Threat Defense-Hersteller als Informationsquelle für Kompatibilitätsrichtlinien und bedingte Zugriffsregeln integrieren. Sie können diese Informationen verwenden, um Unternehmensressourcen wie Exchange und SharePoint zu schützen, indem Sie den Zugriff von manipulierten mobilen Geräten blockieren.  

## <a name="what-problem-does-this-solve"></a>Welches Problem wird dadurch gelöst?
Die Integration von Informationen von einem Mobile Threat Defense-Hersteller unterstützt Sie dabei, Ihre Unternehmensressourcen vor Bedrohungen zu schützen, die mobile Plattformen beeinträchtigen.  

Normalerweise schützen Firmen PCs proaktiv vor Sicherheitsrisiken und Angriffen, während mobile Geräte oft nicht überwacht werden und ungeschützt bleiben. Während mobile Plattformen integrierten Schutz in Form von App-Isolierung und sicherheitsgeprüfter App Stores für Verbraucher bieten, bleiben diese Plattformen anfällig für komplexe Angriffe. Da mehr Angestellte Geräte für die Arbeit und für den Zugriff auf vertrauliche Informationen verwenden, unterstützen Sie die Informationen des Mobile Threat Defense-Herstellers dabei, Geräte und Ihre Ressourcen vor immer komplexeren Angriffen zu schützen.  

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Wie funktionieren die Intune Mobile Threat Defense-Connectors?

Intune verwendet einen Mobile Threat Defense-Connector, um einen Kommunikationskanal zwischen Intune und Ihrem ausgewählten Mobile Threat Defense-Hersteller zu erstellen. Mobile Threat Defense-Partner von Intune bieten intuitive, einfach anwendbare Anwendungen für mobile Geräte an. Diese Anwendungen überprüfen und analysieren aktiv Bedrohungsinformationen und teilen diese mit Intune. Intune verwendet diese Daten dann entweder für Berichte oder für Erzwingungen.  

Beispiel: Eine verbundene Mobile Threat Defense-App meldet dem Mobile Threat Defense-Hersteller, dass ein Telefon in Ihrem Netzwerk gegenwärtig mit einem Netzwerk verbunden ist, das für Man-in-the-Middle-Angriffe anfällig ist. Diese Informationen werden in eine entsprechende Risikostufe eingeteilt: niedrig, mittel oder hoch. Die Risikostufe wird dann mit den Toleranzwerten für Risikostufen verglichen, die Sie in Intune festgelegt haben. Auf Grundlage dieses Vergleichs kann der Zugriff auf bestimmte Ressourcen, die Sie auswählen, widerrufen werden, während das Gerät manipuliert ist.

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Welche Daten erfasst Intune für Mobile Threat Defense?

Wenn die Einstellung aktiviert ist, erfasst Intune sowohl von privaten als auch von unternehmenseigenen Geräten Informationen zum App-Bestand und stellt diese für MTD-Anbieter (Mobile Threat Defense) wie Lookout for Work zur Verfügung. Sie können Informationen zum App-Bestand der Benutzer von iOS-Geräten erfassen.

Dieser Dienst muss aktiviert werden. Informationen zum App-Bestand werden nicht standardmäßig freigegeben. Die App-Synchronisierung für iOS-Geräte muss in den Diensteinstellungen von einem Intune-Administrator aktiviert werden, bevor Informationen zum App-Bestand freigegeben werden.

**App-Bestand**  
Wenn Sie die App-Synchronisierung für iOS-Geräte aktivieren, werden die Bestände der unternehmenseigenen und privaten iOS-Geräte an Ihren MTD-Dienstanbieter gesendet. Die Daten in den App-Beständen umfassen:

 - App-ID
 - App-Version
 - Kurzversion der App
 - App-Name
 - Größe des App-Pakets
 - Dynamische Größe der App
 - Ob die App gültig ist oder nicht
 - Ob die App verwaltet wird oder nicht

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
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- Sophos (weitere Informationen folgen bald)
- Wandera (weitere Informationen folgen bald)
