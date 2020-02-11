---
title: Übersicht über den App-Lebenszyklus für Microsoft Intune
description: Informationen zum Lebenszyklus von verwalteten Apps in Microsoft Intune. Der App-Lebenszyklus umfasst das Hinzufügen, Bereitstellen, Konfigurieren, und Außerkraftsetzen von Apps.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: apps; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ce23d77d9b9d89ce51738a9c4e244dfca9a1c59
ms.sourcegitcommit: b0d683917af83170f85022b270270d8ced8e301c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76812401"
---
# <a name="overview-of-the-app-lifecycle-in-microsoft-intune"></a>Übersicht über den App-Lebenszyklus in Microsoft Intune

Der Microsoft Intune-Lebenszyklus von Apps beginnt, wenn eine App hinzugefügt wird, und durchläuft weitere Phasen, bis Sie die App entfernen. Wenn Sie verstanden haben, was in den einzelnen Phasen geschieht, verfügen Sie über sämtliche Informationen, die Sie für die ersten Schritte zur App-Verwaltung in Intune benötigen.

![Der App-Lebenszyklus: Hinzufügen, Bereitstellen, Konfigurieren, Schützen und Einstellen](./media/app-lifecycle/app-lifecycle.png "Der App-Lebenszyklus von Intune")

## <a name="add"></a>Add

Der erste Schritt bei der App-Bereitstellung besteht darin, die Apps, die Sie verwalten und zuweisen möchten, zu Intune hinzuzufügen. Sie können zwar mit vielen verschiedenen App-Typen arbeiten, aber die grundlegenden Verfahren sind identisch. Mithilfe von Intune können Sie verschiedene App-Typen hinzufügen. Dazu gehören u.a. intern erstellte (branchenspezifische) Apps, Apps aus dem Store, integrierte Apps und Apps im Web. Weitere Informationen zu den einzelnen App-Typen finden Sie unter [So fügen Sie eine App zu Microsoft Intune hinzu](apps-add.md).

## <a name="deploy"></a>Bereitstellen

Nachdem Sie die App zu Intune hinzugefügt haben, können Sie diese [für die von Ihnen verwalteten Benutzer und Geräte bereitstellen](apps-deploy.md). Intune vereinfacht diesen Vorgang, und nachdem die App bereitgestellt wurde, können Sie [die erfolgreiche Bereitstellung über Intune im Azure-Portal überwachen](apps-monitor.md). Darüber hinaus können Sie in einigen App-Stores wie dem [Apple](vpp-apps-ios.md)- und dem [Windows](windows-store-for-business.md)-App Store App-Lizenzen für Ihr Unternehmen in einem Massenvorgang erwerben. Intune kann Daten mit diesen Stores synchronisieren, sodass Sie die Bereitstellung und Verfolgung der Lizenznutzung für diese Typen von Apps direkt von der Intune-Verwaltungskonsole aus bereitstellen und verfolgen können.

## <a name="configure"></a>Konfigurieren

Im Rahmen des App-Lebenszyklus werden regelmäßig neue Versionen von Apps veröffentlicht. Intune bietet Tools, mit denen Sie die bereitgestellten Apps leicht auf eine neuere Version [aktualisieren können](apps-add.md). Darüber hinaus können Sie für einige Apps zusätzliche Funktionalität konfigurieren, zum Beispiel:

- Mit [iOS-App-Konfigurationsrichtlinien](app-configuration-policies-use-ios.md) können Sie Einstellungen für kompatible iOS-Apps angeben, die bei Ausführung der App verwendet werden. Eine App kann beispielsweise bestimmte Brandingeinstellungen oder den Namen eines Servers abfragen, mit dem diese eine Verbindung herstellen muss.
- [Verwaltete Browserrichtlinien](app-configuration-managed-browser.md) helfen Ihnen beim Konfigurieren von Einstellungen für den Browser [Microsoft Edge](~/apps/apps-supported-intune-apps.md#microsoft-apps), der den Standardbrowser für das Gerät ersetzt und Ihnen das Einschränken der Websites ermöglicht, die die Benutzer besuchen können.

## <a name="protect"></a>Schützen

Intune bietet Ihnen viele Möglichkeiten zum Schutz der Daten in Ihren Apps. Die wichtigsten Methoden sind:

- Der [bedingte Zugriff](../protect/conditional-access.md) steuert den Zugriff auf E-Mails und andere Dienste basierend auf Bedingungen, die Sie festlegen. Bedingungen sind z. B. Gerätetypen oder die Einhaltung einer von Ihnen bereitgestellten [Gerätekompatibilitätsrichtlinie](../protect/device-compliance-get-started.md).
- [App-Schutzrichtlinien](app-protection-policy.md) arbeiten mit einzelnen Apps, mit denen Sie die von diesen Apps verwendeten Unternehmensdaten schützen können. Beispielsweise können Sie das Kopieren von Daten zwischen nicht verwalteten Apps und von Ihnen verwalteten Apps einschränken, oder Sie können die Ausführung von Apps auf Geräten verhindern, die per Jailbreak oder Rooting manipuliert wurden.

## <a name="retire"></a>Außerkraftsetzen

Letztlich ist es wahrscheinlich, dass von Ihnen bereitgestellte Apps irgendwann nicht mehr aktuell sind und entfernt werden müssen. Intune vereinfacht die [Außerbetriebnahme von Apps](../remote-actions/device-management.md).

## <a name="next-steps"></a>Nächste Schritte

- Informationen zur [App-Verwaltung in Microsoft Intune](app-management.md)
