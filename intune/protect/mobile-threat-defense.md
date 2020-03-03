---
title: Mobile Threat Defense mit Microsoft Intune
titleSuffix: Microsoft Intune
description: Verwenden Sie Intune Mobile Threat Defense (MTD) mit Ihrem Mobile Threat Defense-Partner, um den Zugriff auf Unternehmensressourcen basierend auf dem Geräterisiko zu schützen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f056f665ebee0d1e2315129a4fe739b2c490ca98
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514845"
---
# <a name="mobile-threat-defense-integration-with-intune"></a>Integration von Mobile Threat Defense in Intune

Intune kann Daten von einem MTD-Anbieter (Mobile Threat Defense) als Informationsquelle für Gerätekonformitätsrichtlinien und Geräterichtlinien für bedingten Zugriff integrieren. Sie können diese Informationen verwenden, um Unternehmensressourcen wie Exchange und SharePoint zu schützen, indem Sie den Zugriff von manipulierten mobilen Geräten blockieren.

Intune kann dieselben Daten als Quelle für nicht registrierte Geräte mit Intune-App-Schutzrichtlinien verwenden. Daher können Administratoren diese Informationen verwenden, um Unternehmensdaten in einer [geschützten Microsoft Intune-App](~/apps/apps-supported-intune-apps.md) zu schützen und einen Block auszugeben oder selektives Zurücksetzen durchzuführen.

## <a name="protect-corporate-resources"></a>Schützen von Unternehmensressourcen

Die Integration von Informationen von einem MTD-Hersteller unterstützt Sie dabei, Ihre Unternehmensressourcen vor Bedrohungen zu schützen, die mobile Plattformen beeinträchtigen.  

Normalerweise schützen Firmen PCs proaktiv vor Sicherheitsrisiken und Angriffen, während mobile Geräte oft nicht überwacht werden und ungeschützt bleiben. Während mobile Plattformen integrierten Schutz in Form von App-Isolierung und sicherheitsgeprüfter App Stores für Verbraucher bieten, bleiben diese Plattformen anfällig für komplexe Angriffe. Da mehr Angestellte Geräte für die Arbeit und für den Zugriff auf vertrauliche Informationen verwenden, unterstützen Sie die Informationen des MTD-Herstellers dabei, Geräte und Ihre Ressourcen vor immer komplexeren Angriffen zu schützen.

## <a name="intune-mobile-threat-defense-connectors"></a>Intune Mobile Threat Defense-Connector

Intune verwendet einen Mobile Threat Defense-Connector, um einen Kommunikationskanal zwischen Intune und Ihrem ausgewählten MTD-Hersteller zu erstellen. MTD-Partner von Intune bieten intuitive, einfach anwendbare Anwendungen für mobile Geräte an. Diese Anwendungen überprüfen und analysieren aktiv Bedrohungsinformationen und teilen diese mit Intune. Intune verwendet diese Daten dann entweder für Berichte oder für Erzwingungen.

Beispiel: Eine verbundene MTD-App meldet dem MTD-Hersteller, dass ein Telefon in Ihrem Netzwerk gegenwärtig mit einem Netzwerk verbunden ist, das für Man-in-the-Middle-Angriffe anfällig ist. Diese Informationen werden in eine entsprechende Risikostufe eingeteilt: niedrig, mittel oder hoch. Die Risikostufe wird dann mit den Toleranzwerten für Risikostufen verglichen, die Sie in Intune festgelegt haben. Auf Grundlage dieses Vergleichs kann der Zugriff auf bestimmte Ressourcen, die Sie auswählen, widerrufen werden, während das Gerät manipuliert ist.

## <a name="data-that-intune-collects-for-mobile-threat-defense"></a>Daten, die Intune für Mobile Threat Defense erfasst

Wenn die Einstellung aktiviert ist, erfasst Intune sowohl von privaten als auch von unternehmenseigenen Geräten Informationen zum App-Bestand und stellt diese für MTD-Anbieter wie Lookout for Work zur Verfügung. Sie können Informationen zum App-Bestand der Benutzer von iOS-Geräten erfassen.

Dieser Dienst muss aktiviert werden. Informationen zum App-Bestand werden nicht standardmäßig freigegeben. Die **App-Synchronisierung für iOS-Geräte** muss in den MTD-Connectoreinstellungen von einem Intune-Administrator aktiviert werden, bevor Informationen zum App-Bestand freigegeben werden.

**App-Bestand**  
Wenn Sie die App-Synchronisierung für iOS/iPadOS-Geräte aktivieren, werden die Bestände der unternehmenseigenen und privaten iOS/iPadOS-Geräte an Ihren MTD-Dienstanbieter gesendet. Die Daten in den App-Beständen umfassen:

- App-ID
- App-Version
- Kurzversion der App
- App-Name
- Größe des App-Pakets
- Dynamische Größe der App
- Ob die App gültig ist oder nicht
- Ob die App verwaltet wird oder nicht

## <a name="sample-scenarios-for-enrolled-devices-using-device-compliance-policies"></a>Beispielszenarios für registrierte Geräte mit Gerätekonformitätsrichtlinien

Wenn ein Gerät von der Mobile Threat Defense-Lösung als infiziert eingestuft wird:

![Abbildung: mit Mobile Threat Defense geschütztes, gefährdetes Gerät](./media/mobile-threat-defense/MTD-image-1.png)

Der Zugriff wird ermöglicht, wenn das Gerät wiederhergestellt ist:

![Abbildung: Mobile Threat Defense – Zugriff gewährt](./media/mobile-threat-defense/MTD-image-2.png)

## <a name="sample-scenarios-for-unenrolled-devices-using-intune-app-protection-policies"></a>Beispielszenarios für nicht registrierte Geräte mit Intune-App-Schutzrichtlinien

Wenn ein Gerät von der Mobile Threat Defense-Lösung als infiziert eingestuft wird:<br>
![Abbildung: mit Mobile Threat Defense geschütztes, gefährdetes Gerät](./media/mobile-threat-defense/MTD-image-3.png)

Der Zugriff wird ermöglicht, wenn das Gerät wiederhergestellt ist:<br>
![Abbildung: Mobile Threat Defense-Zugriff gewährt](./media/mobile-threat-defense/MTD-image-4.png)

> [!NOTE]
> Sie können mehrere Mobile Threat Defense-Anbieter mit einem einzelnen Intune-Mandanten verwenden. Wenn jedoch zwei oder mehr Anbieter für die Verwendung auf derselben Plattform konfiguriert sind, müssen alle Geräte, auf denen diese Plattform ausgeführt wird, jede MTD-App installieren und nach Bedrohungen suchen. Wenn Sie eine Überprüfung von einer konfigurierten App nicht übermitteln, wird das Gerät als nicht kompatibel gekennzeichnet. 

## <a name="mobile-threat-defense-partners"></a>Partner von Mobile Threat Defense

Erfahren Sie, wie Sie den Zugriff auf Unternehmensressourcen basierend auf Gerät, Netzwerk und Anwendungsrisiko schützen können mithilfe von:

- [Lookout for Work](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [Wandera Mobile Threat Defense](wandera-mtd-connector.md)
