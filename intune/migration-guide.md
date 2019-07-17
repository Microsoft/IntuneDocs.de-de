---
title: Migrationshandbuch für die Verwaltung mobiler Geräte mit Intune
titleSuffix: Microsoft Intune
description: Dieses Handbuch führt Sie durch die detaillierten Informationen zu den verschiedenen Aspekten bei der Migration von einem MDM-Drittanbieter zu Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 97a0d9074b8617dec2fb28ed59168e08ada57fba
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882764"
---
# <a name="intune-migration-guide"></a>Intune-Migrationshandbuch

![Abbildung zum MDM-Migrationshandbuch von Microsoft Intune](./media/MDM-migration-guide-art.PNG)

Eine erfolgreiche Migration in Microsoft Intune beginnt mit einem soliden Plan, der Ihre aktuelle MDM-Umgebung (Mobile Device Management, Verwaltung mobiler Geräte), Geschäftsziele und technische Anforderungen miteinbezieht. Zusätzlich müssen Sie die wichtigsten Projektbeteiligten einschließen, die Ihren Migrationsplan unterstützen und bei diesem mit Ihnen zusammenarbeiten werden.

Hier finden Sie detaillierte Informationen zu den verschiedenen Aspekten bei der Migration von einem MDM-Drittanbieter zu Intune.

## <a name="whats-included-in-this-guide"></a>Inhalt dieses Handbuchs

Dieses Handbuch teilt die Migration in zwei Phasen auf, die beide Aufgaben, Strategien und Unterstützung bei der Vorgehensweise beinhalten, die Sie während der Migration zu Intune MDM Schritt für Schritt begleiten.

- [Phase 1: Vorbereitung von Microsoft Intune für die Verwaltung mobiler Geräte (MDM)](migration-guide-prepare.md)

  - [Anforderungen Ihrer MDM-Migration analysieren](migration-guide-prepare.md#assess-mdm-requirements)

  - [Grundlegende Einrichtung](migration-guide-setup.md)

  - [Konfigurieren von Richtlinien für die Verwaltung von Apps und Geräten](migration-guide-configure-policies.md)

  - [Konfigurieren von App-Schutzrichtlinien](migration-guide-app-protection-policies.md)

  - [Besondere Überlegungen bei der Migration](migration-guide-considerations.md)

- [Phase 2: Migrationskampagne](migration-guide-campaign.md)

  - [Kommunikationsplan](migration-guide-communication-plan.md)

  - [Fördern der Akzeptanz des bedingten Zugriffs bei Endbenutzern](migration-guide-drive-adoption.md)

  - [typischer Migrationszyklus](migration-guide-cycle.md)
    - [Migrationsüberwachung](migration-guide-cycle.md#monitoring-migration)
    - [Aufgaben nach der Migration](migration-guide-cycle.md#post-migration)

## <a name="assumptions"></a>Annahmen

- Sie haben Intune bereits in einer PoC-Umgebung (Proof of Concept) evaluiert und entschieden, diese Lösung zur Verwaltung mobiler Geräte in Ihrer Organisation einzusetzen.

- Sie sind bereits mit Intune und seinen Funktionen vertraut.

## <a name="before-you-begin"></a>Vorbereitung

Es ist wichtig, dass Sie wissen, dass Ihre Bereitstellung mit Intune möglicherweise von Ihrer alten MDM-Bereitstellung unterscheidet. Im Gegensatz zu herkömmlichen MDM-Diensten baut Intune auf der identitätsgesteuerten Zugriffssteuerung auf, weshalb keine Netzwerkproxyvorrichtung zur Zugriffssteuerung auf Unternehmensdaten von mobilen Geräten außerhalb des Netzwerkumkreises der Organisation erforderlich ist. Microsoft bietet Lösungen zur Sicherung von Datendiensten innerhalb der Cloud selbst durch eine Folge von fest integrierten Clouddiensten, die zusammen als Angebot von Enterprise Client und Security bezeichnet werden.

- Erfahren Sie mehr über die [gängigsten Arten der Verwendung von Intune](common-scenarios.md).

## <a name="next-steps"></a>Nächste Schritte

[Phase 1: Vorbereitung von Microsoft Intune für die Verwaltung mobiler Geräte (MDM)](migration-guide-prepare.md)
