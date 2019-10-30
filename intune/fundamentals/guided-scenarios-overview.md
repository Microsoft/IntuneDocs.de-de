---
title: Geführte Szenarien – Übersicht
titleSuffix: Microsoft Intune
description: Erfahren Sie mehr über die im Microsoft 365-Geräteverwaltungsportal verfügbaren geführten Szenarios zu Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 43c88366ea64182ccf8d45bc3e890a2579df20f1
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585643"
---
# <a name="intune-guided-scenarios-overview"></a>Übersicht über geführte Szenarios zu Intune 

Ein geführtes Szenario beschreibt eine angepasste Reihe von Schritten für einen End-to-End-Anwendungsfall. Gängige Szenarios basieren auf der Rolle eines Administrators, Benutzers oder Geräts in Ihrer Organisation. Diese Rollen erfordern in der Regel eine Sammlung sorgfältig orchestrierter Profile, Einstellungen, Anwendungen und Sicherheitskontrollen, um die beste Benutzererfahrung und Sicherheit bereitzustellen.    

Wenn Sie nicht mit allen Schritten und Ressourcen vertraut sind, die zum Implementieren eines bestimmten Intune-Szenarios benötigt werden, können Sie geführte Szenarios als Ausgangspunkt verwenden. Im Rahmen des geführten Szenarios werden Richtlinien, Apps, Zuweisungen und andere Verwaltungskonfigurationen automatisch zusammengetragen. Darüber hinaus können geführte Szenarios bestimmte Optionen absichtlich auslassen, die auf das jeweilige Szenario nicht anwendbar oder dafür nicht üblich sind. 

Bei geführten Szenarios handelt es sich nicht um einen anderen Verwaltungsbereich als bei normalen Intune-Workflows. Diese Workflows sind für die Verwendung in Verbindung mit vorhandenen Intune-Workflows für Profile, Apps und Richtlinien vorgesehen. Nach Abschluss eines geführten Szenarios muss die zukünftige Verwaltung des Szenarios über die vorhandenen Menüs für Richtlinien, Apps und Profile erfolgen. Ein geführtes Szenario speichert keinen Ressourcentyp für „geführte Szenarios“ und verfolgt keine zukünftigen Änderungen an den Ressourcen. Alle Ressourcen, die von einem geführten Szenario erstellt werden, befinden sich in ihrer jeweiligen Workload. Alle Optionen, sogar die Optionen, die vom geführten Szenario ausgelassen werden, können anschließend in den jeweiligen vorhandenen Menüs bearbeitet werden.  

## <a name="types-of-guided-scenarios"></a>Typen von geführten Szenarios 

Der Einfachheit halber werden komplexe Bereichsfeatures wie Bereichstags <link>, Ausschlussgruppen und virtuelle Gruppenzuweisungen <link> aus allen geführten Szenarios ausgelassen. Alle Ressourcen, die im Rahmen eines geführten Szenarios erstellt wurde, erben alle Bereichstags des Administrators, der das Szenario durchführt. Bestimmte Szenarios bieten ein gewisses Maß an Anpassung für allgemeine Einstellungen, um eng verwandte Szenarios zu behandeln. Diese Szenarios unterstützen die Gruppenzuweisung nur für Einschlussgruppen. Bei anderen geführten Szenarios garantiert das gesamte Szenario eine konsistente Funktion, indem keine Anpassung angeboten und automatisch eine neue Gruppe erstellt wird, um alle Zuweisungen zu empfangen. Sobald das geführte Szenario abgeschlossen ist, können Sie anspruchsvollere Zuweisungen direkt über vorhandene Richtlinien-, App- und Profilworkloads verwenden.  

Die folgenden geführten Szenarios sind verfügbar: 
- Bereitstellen von Microsoft Edge für Mobilgeräte 
- Testen eines in der Cloud verwalteten Computers
- Sicheres Microsoft Office für Mobilgeräte 

## <a name="guided-scenario-functionality"></a>Funktionalität von geführten Szenarios 

Geführte Szenarios bieten eine spezifische Funktionalität. In den folgenden Details wird erläutert, was Sie beim Befolgen eines geführten Szenarios tun können und was nicht.

### <a name="launching"></a>Starten  

Alle geführten Szenarios sind über **[Device Management portal](https://devicemanagement.microsoft.com)**  > **Troubleshooting + Help** > **Guided scenarios** (Geräteverwaltungsportal > Problembehandlung + Hilfe > Geführte Szenarios) verfügbar. 

Das geführte Szenario beginnt mit einer Einführung, in der der Zweck des Szenarios und alle Voraussetzungen zum Abschließen des Setups erläutert werden. Zu diesem Zeitpunkt werden Ihre Administratorberechtigungen überprüft, um sicherzustellen, dass Sie über alle erforderlichen Berechtigungen verfügen, um das Szenario abzuschließen.  

Nachdem alle Überprüfungen des Voraussetzungen durchgeführt wurden, bietet das Szenario entsprechende Einstellungen zur Anpassung an. Geführte Szenarios sind dazu konzipiert, nur Eingaben für eine Mindestmenge an Einstellungen zu erfordern und ungewöhnliche oder erweiterte Einstellungen basierend auf speziellen Umständen und bis sie benötigt werden auszublenden. Alle geführten Szenarios enthalten Links zu Dokumentationen mit zusätzlichen Informationen. 

Nachdem alle erforderlichen Einstellungen vorgenommen wurden, zeigt das geführte Szenario eine Zusammenfassung der konfigurierten Einstellungen und der für das Szenario erforderlichen Ressourcen an. Zu diesem Zeitpunkt wurde noch nichts gespeichert, es sei denn, es wurde explizit darauf hingewiesen.

Der nächste Schritt besteht darin, das Szenario bereitzustellen. Bei der Bereitstellung eines Szenarios werden alle erforderlichen Ressourcen und ausgewählten Einstellungen erstellt und gespeichert. Die Zeit zum Durchführen einer Bereitstellung variiert je nach Szenario. Sobald die Bereitstellung abgeschlossen wird, stellt das geführte Szenario eine Liste der erstellten Ressourcen mit Links zur Verwaltungsansicht der einzelnen Ressourcen, zur normalen Workload der Ressource und zur Dokumentation dar. 

> [!IMPORTANT]
> Die Liste, die am Ende des geführten Szenario angezeigt wird, wird nicht gespeichert und kann nur angezeigt werden, während das geführte Szenario geöffnet ist.  
Wenn bei der Bereitstellung des Szenarios ein Fehler auftritt, werden alle Änderungen zurückgesetzt. 

### <a name="editing"></a>Bearbeitung 

Geführte Szenarios können nicht zum Bearbeiten vorhandener Ressourcen verwendet werden. Sobald sie erstellt wurden, müssen alle Ressourcen, Gruppen und Zuweisungen mithilfe der vorhandenen Workloads bearbeitet werden.

### <a name="monitoring"></a>Überwachung 

Geführte Szenarios können abgesehen von Erstellungsvorgang nicht zum Überwachen vorhandener Ressourcen verwendet werden. Sobald sie erstellt wurden, müssen alle Ressourcen, Gruppen und Zuweisungen mithilfe der vorhandenen Workloads überwacht werden. 

### <a name="retiring"></a>Deaktivierung 

Geführte Szenarios können nicht zum Deaktivieren vorhandener Ressourcen verwendet werden, mit Ausnahme der automatisierten Bereinigung bei einem Fehler bei der ersten Bereitstellung. Sobald sie erstellt wurden, müssen alle Ressourcen, Gruppen und Zuweisungen mithilfe der vorhandenen Workloads deaktiviert werden. 

### <a name="updating"></a>Aktualisierung

Mit der Entwicklung der Technologie werden auch geführte Szenarios von Intune von Zeit zu Zeit aktualisiert, um die Benutzererfahrung, die Sicherheit oder andere Aspekte der Szenarios zu verbessern. Diese Aktualisierung wirkt sich nur auf neue Bereitstellungen aus, die von geführten Szenarios vorgenommen wurden. Vorhandene Ressourcen, die im Rahmen von geführten Szenarios erstellt wurden, werden nicht von Intune aktualisiert, um neuen bewährten Methoden oder Empfehlungen zu entsprechen.  

## <a name="next-steps"></a>Nächste Schritte

Durchlaufen Sie die geführten Szenarios von Intune, um schnell in Microsoft Intune einzusteigen. Wenn Sie noch nicht mit Intune vertraut sind, richten Sie Ihren Intune-Mandanten ein, indem Sie den [Schnellstart für die kostenlose Testversion](free-trial-sign-up.md) befolgen.