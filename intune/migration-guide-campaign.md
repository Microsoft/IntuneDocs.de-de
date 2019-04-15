---
title: Starten einer Intune-Migration
titleSuffix: Microsoft Intune
description: Dieser Artikel enthält einen Leitfaden für die Vorgehensweise beim Starten einer Migrationskampagne zu Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f781b029-50f2-46ee-8ff7-03b4a6719e80
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: db56bbc180a84e8b3972ffc6473126efd366faa8
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568270"
---
# <a name="phase-2-migration-campaign"></a>Phase 2: Migration

Wählen Sie einen Migrationsansatz aus, der am besten für die Anforderungen Ihres Unternehmens geeignet ist, und passen Sie Implementierungstaktiken basierend auf Ihren speziellen Anforderungen entsprechend an. Diese Anleitung hilft Ihnen bei der Registrierung Ihrer Geräte in Intune.

## <a name="keys-to-a-successful-migration"></a>Wichtige Faktoren für eine erfolgreiche Migration

Dies sind die Schlüssel für die erfolgreiche Migration eines MDM-Drittanbieters in Intune:

-   Durch eine klare und hilfreiche Kommunikation können Ausfallzeiten und Unzufriedenheit von Endbenutzern minimiert werden.

-   Achten Sie darauf, dass Sie genaue Anweisungen für die Migration geben.

-   Die Registrierung aller verwalteten Geräte Ihres vorhandenen MDM-Anbieters muss vor der Registrierung in Intune aufgehoben werden.

-   Stellen Sie für die Endbenutzer eine Anleitung des alten MDM-Anbieters für das Aufheben der Geräteregistrierung bereit.

-   Gehen Sie schrittweise vor. Beginnen Sie mit einer kleinen Gruppe von Pilotbenutzern und fügen Sie nach und nach mehr Benutzergruppen hinzu, bis alle bereitgestellt wurden.

-   Überwachen Sie das Laden des Helpdesks und den Registrierungserfolg der jeweiligen Zyklen. Planen Sie großzügig, um sicherzustellen, dass Erfolgskriterien für jede Gruppe ausgewertet werden können, bevor Sie mit der Migration der nächsten beginnen. Ihre Pilotbereitstellung sollte Folgendes überprüfen:

    -   ob sich die Registrierungerfolgs- und Fehlerraten im Rahmen bewegen

    -   Benutzerproduktivität:

        -   Unternehmensressourcen wie z.B. VPN, Wi-Fi, E-Mail und Zertifikate funktionieren ordnungsgemäß.

        -   Auf bereitgestellte Apps kann zugegriffen werden.

    -   Datensicherheit:

        -   Kompatibilitätsberichte treten auf.

        -   Schutzmaßnahmen für mobile Apps werden erzwungen.

Wenn Sie mit der ersten Phase der Migration zufrieden sind, wiederholen Sie den [Migrationszyklus](migration-guide-cycle.md) für die nächste Phase.

-   Wiederholen Sie die Zyklen in Phasen, bis alle Benutzer zu Intune migriert wurden.

-   Stellen Sie sicher, dass das Helpdesk-Team zur Unterstützung der Endbenutzer während der gesamten Migration zur Verfügung steht. Führen Sie eine freiwillige Migration aus, bis Sie die Arbeitsauslastung für Supportanrufe einschätzen können.

-   Legen Sie keine Frist für die Registrierung fest, bis die verbleibende Auffüllung von Ihrem Helpdesk verarbeitet werden kann

> [!IMPORTANT]
> Konfigurieren Sie Intune und Ihre vorhandene Drittanbieter-MDM-Projektmappe nicht gleichzeitig so, dass Zugriffssteuerelemente auf Ressourcen wie Exchange oder SharePoint Online angewendet werden. Zusätzlich sollten Geräte immer nur in einer Projektmappe gleichzeitig registriert sein.

## <a name="next-steps"></a>Nächste Schritte

Erstellen Sie Ihren [Kommunikationsplan](migration-guide-communication-plan.md).
