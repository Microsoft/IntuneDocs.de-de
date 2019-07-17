---
title: App-Konfigurationsrichtlinien für Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie App-Konfigurationsrichtlinien in Microsoft Intune für iOS- oder Android-Geräte verwenden.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1e5ddf39a201f1a70f997e03f0b65706853adefa
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67885116"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>App-Konfigurationsrichtlinien für Microsoft Intune

Verwenden Sie App-Konfigurationsrichtlinien in Microsoft Intune, um Konfigurationseinstellungen für eine iOS- oder Android-App anzugeben. Bei Verwendung dieser Konfigurationseinstellungen kann eine App mithilfe eines Branchenstandardverfahrens für die App-Konfiguration und -Verwaltung angepasst werden. Die Konfigurationsrichtlinieneinstellungen werden verwendet, wenn die App danach sucht (in der Regel beim ersten Ausführen).

Sie können einer Gruppe von Benutzern und Geräten mithilfe einer Kombination aus Ein- und Ausschlusszuweisungen eine App-Konfigurationsrichtlinie zuweisen. Nachdem Sie eine App-Konfigurationsrichtlinie hinzugefügt haben, können Sie die Zuweisungen für die App-Konfigurationsrichtlinie festlegen. Wenn Sie die Zuweisungen für die Richtlinie festlegen, können Sie entscheiden, ob Gruppen von Benutzern ein- und ausgeschlossen werden, für welche die Richtlinie angewendet wird. Wenn Sie entscheiden, eine oder mehrere Gruppen einzuschließen, können Sie bestimmte einzuschließende Gruppen oder integrierte Gruppen auswählen. Zu den integrierten Gruppen zählen **Alle Benutzer**, **Alle Geräte** und **Alle Benutzer und alle Geräte**.

Beispielsweise kann eine App-Konfigurationseinstellung erfordern, dass Sie folgende Informationen angeben:

- Eine benutzerdefinierte Portnummer
- Spracheinstellungen
- Sicherheitseinstellungen
- Brandingeinstellungen wie z. B. ein Unternehmenslogo

Wenn Benutzer stattdessen diese Einstellungen eingeben müssten, könnten sie dies möglicherweise nicht ordnungsgemäß tun; dies könnte zu einer erhöhten Belastung Ihres Helpdesks führen und die Annahme der neuen Apps verlangsamen.

Mit App-Konfigurationsrichtlinien können Sie App-Einrichtungsprobleme beseitigen, indem Sie diese Konfigurationseinstellungen einer Richtlinie zuweisen, die Benutzern zugewiesen ist, bevor diese die App ausführen. Die Einstellungen werden dann automatisch bereitgestellt, und die Benutzer müssen keine weitere Aktion durchführen.

Die Konfigurationseinstellungen werden verwendet, wenn die App nach ihnen prüft. In der Regel überprüft eine App die Konfigurationseinstellungen, wenn der Benutzer sie zum ersten Mal ausführt.

Ihnen stehen zwei Optionen für das Verwenden der App-Konfigurationen mit Intune zur Verfügung:
- **Verwaltete Geräte:** Das Gerät wird von Intune als MDM-Anbieter (Mobile Device Management, Verwaltung mobiler Geräte) verwaltet.
- **Verwaltete Apps:** Eine App wird ohne Geräteregistrierung verwaltet.

> [!NOTE]
> Wie der Microsoft Intune-Administrator können Sie steuern, welche Benutzerkonten Microsoft Office-Anwendungen auf verwalteten Geräten hinzugefügt werden. Sie können den Zugriff auf zulässige Organisationsbenutzerkonten beschränken und persönliche Konten auf registrierten Geräten blockieren. Die unterstützenden Anwendungen verarbeiten die App-Konfiguration und entfernen und blockieren nicht genehmigte Konten.

## <a name="apps-that-support-app-configuration"></a>Apps, die die App-Konfiguration unterstützen

### <a name="managed-devices"></a>Verwaltete Geräte
Sie können App-Konfigurationsrichtlinien für Apps verwenden, die diese unterstützen. Zur Unterstützung der App-Konfiguration in Intune müssen Apps so programmiert sein, dass sie die Verwendung von App-Konfigurationen unterstützen, die von der [Appconfig-Community](https://www.appconfig.org/members) definiert wurden. Wenden Sie sich für Details an Ihren App-Anbieter.

### <a name="managed-apps"></a>Verwaltete Apps
Sie können Ihre branchenspezifischen Apps dafür vorbereiten, indem Sie entweder das Intune App SDK in die App integrieren oder die App nach der Entwicklung damit umschließen. Das für iOS und Android verfügbare Intune App SDK aktiviert Ihre App für Konfigurationsrichtlinien für den Intune-App-Schutz. Es zielt darauf ab, die vom App-Entwickler vorzunehmenden Codeänderungen zu minimieren. Weitere Informationen finden Sie unter [Übersicht über das Intune App SDK](app-sdk.md).

## <a name="graph-api-support-for-app-configuration"></a>Graph-API-Unterstützung für die App-Konfiguration

Zusätzlich können Sie die Graph-API verwenden, um die App-Konfiguration abzuschließen. Weitere Informationen finden Sie in der [Graph-API-Referenz für die MAM-Zielkonfiguration](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="next-steps"></a>Nächste Schritte

### <a name="managed-devices"></a>Verwaltete Geräte

- Erfahren Sie, wie Sie die App-Konfiguration mit Ihren iOS-Geräten verwenden.  Siehe [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete iOS-Geräte](app-configuration-policies-use-ios.md).
- Erfahren Sie, wie Sie die App-Konfiguration mit Ihren Android-Geräten verwenden.  Siehe [Add app configuration policies for managed Android devices (Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android-Geräte)](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Verwaltete Apps

- Erfahren Sie, wie Sie die App-Konfiguration mit verwalteten Geräten verwenden. Siehe [Add app configuration policies for managed apps without device enrollment (Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Apps ohne Geräteregistrierung)](app-configuration-policies-managed-app.md).
