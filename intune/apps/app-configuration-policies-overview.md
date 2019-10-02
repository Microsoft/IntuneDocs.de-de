---
title: App-Konfigurationsrichtlinien für Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie App-Konfigurationsrichtlinien in Microsoft Intune für iOS- oder Android-Geräte verwenden.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/28/2019
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
ms.openlocfilehash: af81552942805bed07e818d6005231e9305b3460
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725789"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>App-Konfigurationsrichtlinien für Microsoft Intune

Mit App-Konfigurationsrichtlinien können Sie App-Einrichtungsprobleme beseitigen, indem Sie diese Konfigurationseinstellungen einer Richtlinie zuweisen, die Endbenutzern zugewiesen ist, bevor diese die App ausführen. Die Einstellungen werden dann automatisch bereitgestellt, wenn die App auf dem Gerät des Endbenutzers konfiguriert wird. Endbenutzer müssen keine Maßnahmen ergreifen. Die Konfigurationseinstellungen sind für jede App eindeutig. 

Sie können App-Konfigurationsrichtlinien erstellen und verwenden, um Konfigurationseinstellungen für iOS- oder Android-Apps anzugeben. Mithilfe dieser Konfigurationseinstellungen kann eine App unter Verwendung der App-Konfiguration und -Verwaltung angepasst werden. Die Konfigurationsrichtlinieneinstellungen werden verwendet, wenn die App danach sucht (in der Regel beim ersten Ausführen der App). 

Beispielsweise kann eine App-Konfigurationseinstellung erfordern, dass Sie folgende Informationen angeben:

- Eine benutzerdefinierte Portnummer
- Spracheinstellungen
- Sicherheitseinstellungen
- Brandingeinstellungen wie z. B. ein Unternehmenslogo

Wenn Endbenutzer diese Einstellungen stattdessen eingeben würden, könnten ihnen dabei Fehler passieren. Mithilfe von App-Konfigurationsrichtlinien kann die Konsistenz in einem Unternehmen sichergestellt werden. Zudem können Anrufe beim Helpdesk von Endbenutzern reduziert werden, die versuchen, ihre Einstellungen selbst zu konfigurieren. Durch die Verwendung von App-Konfigurationsrichtlinien kann die Einführung neuer Apps vereinfacht und beschleunigt werden.

Die verfügbaren Konfigurationsparameter werden letztendlich von den Entwicklern der App festgelegt. Die Dokumentation des Anwendungsanbieters sollte darauf überprüft werden, ob eine App die Konfiguration unterstützt, und welche Konfigurationen verfügbar sind. Bei einigen Anwendungen füllt Intune die verfügbaren Konfigurationseinstellungen auf. 

> [!NOTE]
> Im verwalteten Google Play Store werden Apps, die die Konfiguration unterstützen, wie folgt gekennzeichnet:
> 
> ![Screenshot einer konfigurierten App](./media/app-configuration-policies-overview/configured-app.png)
>
> Wenn Sie als Registrierungstyp für Android-Geräte „Verwaltete Geräte“ verwenden, werden Ihnen nur Apps aus dem [verwalteten Google Play Store](https://play.google.com/work) statt aus dem [Google Play Store](https://play.google.com/store/apps) angezeigt. Der verwaltete Google Play Store, auch als Android for Work (AfW) und Android Enterprise bekannt, besteht aus den Apps im Arbeitsprofil, die App-Versionen umfassen, die die App-Konfiguration unterstützen.

Sie können einer Gruppe von Endbenutzern und Geräten mithilfe einer Kombination aus [Ein- und Ausschlusszuweisungen](apps-inc-exl-assignments.md) eine App-Konfigurationsrichtlinie zuweisen. Nachdem Sie eine App-Konfigurationsrichtlinie hinzugefügt haben, können Sie die Zuweisungen für die App-Konfigurationsrichtlinie festlegen. Wenn Sie die Zuweisungen für die Richtlinie festlegen, können Sie entscheiden, ob [Gruppen](../fundamentals/groups-add.md) von Endbenutzern ein- und ausgeschlossen werden, für die die Richtlinie angewendet wird. Wenn Sie entscheiden, eine oder mehrere Gruppen einzuschließen, können Sie bestimmte einzuschließende Gruppen oder integrierte Gruppen auswählen. Zu den integrierten Gruppen zählen **Alle Benutzer**, **Alle Geräte** und **Alle Benutzer und alle Geräte**.

Ihnen stehen zwei Optionen für das Verwenden der App-Konfigurationsrichtlinien mit Intune zur Verfügung:
- **Verwaltete Geräte:** Das Gerät wird von Intune als MDM-Anbieter (Mobile Device Management, Verwaltung mobiler Geräte) verwaltet. Die App muss so entworfen werden, dass sie die App-Konfiguration unterstützt.
- **Verwaltete Apps**: Eine App, die für die Integration des Intune App SDK entwickelt wurde. Dies ist als mobile Anwendungsverwaltung ohne Registrierung ([MAM-WE](app-management.md#mobile-application-management-mam-basics)) bekannt. Sie können eine App auch umschließen, damit das Intune App SDK implementiert und unterstützt wird. Weitere Informationen zum Umschließen einer App finden Sie unter [Vorbereiten branchenspezifischer Apps für App-Schutzrichtlinien](../developer/apps-prepare-mobile-application-management.md).

    > [!NOTE]
    > Wenn von Intune verwaltete Apps zusammen mit einer App-Schutzrichtlinie von Intune bereitgestellt werden, prüfen sie in einem Intervall von 30 Minuten den Status der App-Konfigurationsrichtlinie von Intune. Wenn dem Benutzer keine App-Schutzrichtlinie von Intune zugewiesen ist, wird das Überprüfungsintervall der App-Konfigurationsrichtlinie von Intune auf 720 Minuten festgelegt.

## <a name="apps-that-support-app-configuration"></a>Apps, die die App-Konfiguration unterstützen

### <a name="managed-devices"></a>Verwaltete Geräte
Sie können App-Konfigurationsrichtlinien für Apps verwenden, die diese unterstützen. Zur Unterstützung der App-Konfiguration in Intune müssen Apps so programmiert sein, dass sie die Verwendung von App-Konfigurationen unterstützen, die vom Betriebssystem definiert wurden. Weitere Informationen zu den unterstützten App-Konfigurationsschlüsseln erhalten Sie vom App-Anbieter.

### <a name="managed-apps"></a>Verwaltete Apps
Sie können Ihre branchenspezifischen Apps vorbereiten, indem Sie entweder das [Intune App SDK](../developer/app-sdk.md) in die App integrieren oder die App nach der Entwicklung mithilfe des [Intune App Wrapping Tools](../developer/apps-prepare-mobile-application-management.md) umschließen. Mithilfe des Intune App SDK soll die Anzahl der vom App-Entwickler vorzunehmenden Codeänderungen minimiert werden. Weitere Informationen finden Sie unter [Übersicht über das Intune App SDK](../developer/app-sdk.md). Einen Vergleich zwischen dem Intune App SDK und dem Intune App Wrapping Tool finden Sie unter [Vorbereiten branchenspezifischer Apps für App-Schutzrichtlinien](../developer/apps-prepare-mobile-application-management.md#feature-comparison).

Die Auswahl von **Verwaltete Apps** als **Geräteregistrierungstyp** bezieht sich speziell auf Apps, die durch Intune-Konfigurationsrichtlinien auf einem Gerät konfiguriert werden, das nicht für die Geräteregistrierung registriert ist. **Verwaltete Geräte** gilt dagegen für Apps, die über den MDM-Kanal bereitgestellt und somit von Intune verwaltet werden. Wählen Sie basierend auf diesen Beschreibungen die geeignete Option aus. 

![Geräteregistrierungstyp](./media/app-configuration-policies-overview/device-enrollment-type.png)

> [!NOTE]
> Für Apps mit mehreren Identitäten, z. B. Microsoft Outlook, können Benutzereinstellungen berücksichtigt werden. Bei einem Posteingang mit Relevanz wird die Benutzereinstellung beispielsweise berücksichtigt und die Konfiguration nicht geändert. Mit anderen Parametern können Sie steuern, ob ein Benutzer die Einstellung ändern kann oder nicht. Weitere Informationen finden Sie unter [Bereitstellen von Outlook für iOS- und Android-App-Konfigurationseinstellungen](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="validate-the-applied-app-configuration-policy"></a>Überprüfen der angewendeten App-Konfigurationsrichtlinie

Sie können die App-Konfigurationsrichtlinie mithilfe der folgenden drei Methoden überprüfen:

   1. Sichtbar auf dem Gerät. Weist die Ziel-App das in der App-Konfigurationsrichtlinie angewendete Verhalten auf?
   2. Über Diagnoseprotokolle (weitere Informationen finden Sie im Abschnitt „Diagnoseprotokolle“ weiter unten).
   3. Im Intune-Portal. Im Abschnitt **Überwachen** einer Richtlinie kann der entsprechende Status angezeigt werden:

      ![Erster Screenshot des Status der Geräteinstallation](./media/app-configuration-policies-overview/device-install-status-1.png)

      ![Zweiter Screenshot des Status der Geräteinstallation](./media/app-configuration-policies-overview/device-install-status-2.png)

      Zusätzlich zeigt die Option **App-Konfiguration** unter **Intune** -> **Geräte** -> **Alle Geräte** auf der linken Seite des Bildschirms alle zugewiesenen Richtlinien und deren Status an:

      ![Screenshot der App-Konfiguration](./media/app-configuration-policies-overview/app-configuration.png)

## <a name="graph-api-support-for-app-configuration"></a>Graph-API-Unterstützung für die App-Konfiguration

Sie können die Graph-API verwenden, um App-Konfigurationsaufgaben abzuschließen. Weitere Informationen finden Sie in der [Graph-API-Referenz für die MAM-Zielkonfiguration](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="troubleshooting"></a>Problembehandlung

### <a name="using-logs-to-show-a-configuration-parameter"></a>Verwenden von Protokollen zum Anzeigen eines Konfigurationsparameters
Wenn die Protokolle einen Konfigurationsparameter anzeigen, der eigentlich angewendet werden müsste, jedoch anscheinend nicht funktioniert, besteht möglicherweise ein Problem mit der Konfigurationsimplementierung durch den App-Entwickler. Möglicherweise sparen Sie sich einen Anruf beim Microsoft-Support, indem Sie zunächst den App-Entwickler kontaktieren oder sich dessen Knowledge Base ansehen. Wenn das Problem damit zusammenhängt, wie die Konfiguration innerhalb einer App verarbeitet wird, müsste in einer künftigen, aktualisierten Version der App eine Lösung dafür gefunden werden.

## <a name="next-steps"></a>Nächste Schritte

### <a name="managed-devices"></a>Verwaltete Geräte

- Erfahren Sie, wie Sie die App-Konfiguration mit Ihren iOS-Geräten verwenden.  Siehe [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete iOS-Geräte](app-configuration-policies-use-ios.md).
- Erfahren Sie, wie Sie die App-Konfiguration mit Ihren Android-Geräten verwenden.  Siehe [Add app configuration policies for managed Android devices (Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android-Geräte)](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Verwaltete Apps

- Erfahren Sie, wie Sie die App-Konfiguration mit verwalteten Geräten verwenden. Siehe [Add app configuration policies for managed apps without device enrollment (Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Apps ohne Geräteregistrierung)](app-configuration-policies-managed-app.md).
