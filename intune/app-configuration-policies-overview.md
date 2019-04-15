---
title: App-Konfigurationsrichtlinien für Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie App-Konfigurationsrichtlinien in Microsoft Intune für iOS- oder Android-Geräte verwenden.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 844342d0d21110f46ac9a344edbd7409f7d779cb
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567217"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>App-Konfigurationsrichtlinien für Microsoft Intune

Verwenden Sie App-Konfigurationsrichtlinien in Microsoft Intune, um Konfigurationseinstellungen für eine iOS- oder Android-App anzugeben. Mit diesen Konfigurationseinstellungen kann eine App angepasst werden. Sie weisen diese Konfigurationsrichtlinien nicht direkt Benutzern und Geräten zu. Stattdessen verknüpfen Sie eine Konfigurationsrichtlinie mit einer App und weisen dann die App zu. Die Konfigurationsrichtlinieneinstellungen werden verwendet, wenn die App danach sucht (in der Regel beim ersten Ausführen).

Sie können einer Gruppe von Benutzern und Geräten mithilfe einer Kombination aus Ein- und Ausschlusszuweisungen eine App-Konfigurationsrichtlinie zuweisen. Nachdem Sie eine App-Konfigurationsrichtlinie hinzugefügt haben, können Sie die Zuweisungen für die App-Konfigurationsrichtlinie festlegen. Wenn Sie die Zuweisungen für die Richtlinie festlegen, können Sie entscheiden, ob Gruppen von Benutzern ein- und ausgeschlossen werden, für welche die Richtlinie angewendet wird. Wenn Sie entscheiden, eine oder mehrere Gruppen einzuschließen, können Sie bestimmte einzuschließende Gruppen oder integrierte Gruppen auswählen. Zu den integrierten Gruppen zählen **Alle Benutzer**, **Alle Geräte** und **Alle Benutzer und alle Geräte**.

Beispielsweise kann eine App erfordern, dass Sie folgende Informationen angeben:

- Eine benutzerdefinierte Portnummer
- Spracheinstellungen
- Sicherheitseinstellungen
- Brandingeinstellungen wie z. B. ein Unternehmenslogo

Wenn Benutzer diese Einstellungen nicht ordnungsgemäß eingeben, kann dies zur erhöhten Belastung Ihres Helpdesks führen und die Annahme der neuen Apps verlangsamen.

Mit App-Konfigurationsrichtlinien können Sie diese Probleme beseitigen, da Sie diese Einstellungen in einer Richtlinie Benutzern zuweisen können, bevor diese die App ausführen. Die Einstellungen werden dann automatisch bereitgestellt, und die Benutzer müssen keine weitere Aktion durchführen.

Die Konfigurationseinstellungen werden verwendet, wenn die App nach ihnen prüft. In der Regel überprüft eine App die Konfigurationseinstellungen, wenn der Benutzer sie zum ersten Mal ausführt.

Ihnen stehen zwei Optionen für das Verwenden der App-Konfigurationen mit Intune zur Verfügung:
 - **Verwaltete Geräte:** Das Gerät wird von Intune als MDM-Anbieter (Mobile Device Management, Verwaltung mobiler Geräte) verwaltet.
 - **Verwaltete Apps:** Eine App wird ohne Geräteregistrierung verwaltet.

> [!NOTE]
> Wie der Microsoft Intune-Administrator können Sie steuern, welche Benutzerkonten Microsoft Office-Anwendungen auf verwalteten Geräten hinzugefügt werden. Sie können den Zugriff auf zulässige Organisationsbenutzerkonten beschränken und persönliche Konten auf registrierten Geräten blockieren. Die unterstützenden Anwendungen verarbeiten die App-Konfiguration und entfernen und blockieren nicht genehmigte Konten.

## <a name="apps-that-support-app-configuration"></a>Apps, die die App-Konfiguration unterstützen

Sie können App-Konfigurationsrichtlinien für Apps verwenden, die diese unterstützen. Für die Unterstützung der App-Konfiguration in Intune müssen Apps dafür geschrieben sein, die Verwendung von App-Konfigurationen zu unterstützen. Wenden Sie sich für Details an Ihren App-Anbieter.

Sie können Ihre branchenspezifischen Apps dafür vorbereiten, indem Sie entweder das Intune App SDK in die App integrieren oder die App nach der Entwicklung damit umschließen. Das für iOS und Android verfügbare Intune App SDK aktiviert Ihre App für Intune-App-Konfigurationsrichtlinien. Es zielt darauf ab, die vom App-Entwickler vorzunehmenden Codeänderungen zu minimieren. Weitere Informationen finden Sie unter [Übersicht über das Intune App SDK](app-sdk.md).

## <a name="graph-api-support-for-app-configuration"></a>Graph-API-Unterstützung für die App-Konfiguration

Zusätzlich können Sie die Graph-API verwenden, um die App-Konfiguration abzuschließen. Weitere Informationen finden Sie in der [Graph-API-Referenz für die MAM-Zielkonfiguration](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="next-steps"></a>Nächste Schritte

### <a name="managed-devices"></a>Verwaltete Geräte

 - Erfahren Sie, wie Sie die App-Konfiguration mit Ihren iOS-Geräten verwenden.  Siehe [Add app configuration policies for managed iOS devices (Hinzufügen von App-Konfigurationsrichtlinien für verwaltete iOS-Geräte)](app-configuration-policies-use-ios.md).
 - Erfahren Sie, wie Sie die App-Konfiguration mit Ihren Android-Geräten verwenden.  Siehe [Add app configuration policies for managed Android devices (Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android-Geräte)](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Verwaltete Apps

 - Erfahren Sie, wie Sie die App-Konfiguration mit verwalteten Geräten verwenden. Siehe [Add app configuration policies for managed apps without device enrollment (Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Apps ohne Geräteregistrierung)](app-configuration-policies-managed-app.md).
