---
title: Verwalten von Geräten mit Microsoft Intune
titleSuffix: ''
description: Überprüfen Sie die mit Intune verwalteten Geräte, und führen Sie verschiedene Vorgänge auf diesen aus.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/21/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 436eeb306bf4ba343ae4d88a824aeed2077a3426
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="what-is-microsoft-intune-device-management"></a>Was ist die Microsoft Intune Geräteverwaltung?


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Als IT-Administrator müssen Sie sicherstellen, dass verwaltete Geräte die Ressourcen bereitstellen, die Ihre Endbenutzer für Ihre Arbeit benötigen, während gleichzeitig die Daten vor Risiken geschützt werden.

Die Workload **Geräte** liefert Informationen zu den verwalteten Geräten und ermöglicht die Ausführung von Remoteaufgaben auf diesen Geräten. So greifen Sie auf die Workload zu

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie in **Intune** die Option **Geräte** aus.
4. Sie können Informationen über Geräte anzeigen und die folgenden Remotegeräteaktionen durchführen:
    - **Übersicht**: Eine Momentaufnahme der registrierten Geräte, die Sie verwalten können.
    - **Alle Geräte**: Eine Liste der registrierten Geräte, die Sie verwalten. Wählen Sie **Filter** oder **Spalten** aus, um die angezeigten Informationen einzuschränken. Wählen Sie ein Gerät aus, um den [Gerätebestand](device-inventory.md) anzuzeigen.
    - **Azure AD-Geräte**: Eine Liste der Geräte, die in Azure Active Directory (AD) registriert oder damit verbunden sind. Weitere Informationen zur [Azure AD-Geräteverwaltung](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
    - **Geräteaktionen**: Ein Verlauf der Remoteaktionen, die auf Geräten ausgeführt wurden, einschließlich die Aktion, der Status, wer die Aktion initiiert hat und der Zeitpunkt.

        ![Screenshot der Überwachung von Geräteaktionen](./media/monitor-device-actions.png)

    - **Überwachungsprotokolle**: Überwachungsprotokolle stellen Ihnen einen Datensatz von Aktivitäten zur Verfügung, die eine Änderung in Microsoft Intune bewirken. Sie finden weitere Informationen unter [Überwachungsprotokolle](monitor-audit-logs.md).
    - **TeamViewer Connector**: Über den TeamViewer-Dienst können Benutzer von mit Intune verwalteten Android-Geräten Remoteunterstützung von ihrem IT-Administrator erhalten. Erfahren Sie mehr über [TeamViewer](device-profile-android-teamviewer.md).
    - **Hilfe und Support**: Ermöglicht das Behandeln von Problemen, das Anfordern von Unterstützung oder das Anzeigen des Intune-Status.  
    
## <a name="available-device-actions"></a>Verfügbare Geräteaktionen
Die verfügbaren Aktionen hängen von der Geräteplattform und der Konfiguration des Geräts ab.

- [Anzeigen des Gerätebestands](device-inventory.md)
- So führen Sie Remotegeräteaktionen durch:
    - [Unternehmensdaten entfernen](devices-wipe.md#remove-company-data)
    - [Zurücksetzen auf Werkseinstellungen](devices-wipe.md#factory-reset)
    - [Remotesperre](device-remote-lock.md)
    - [Kennung zurücksetzen](device-passcode-reset.md)
    - [Umgehen der Aktivierungssperre](device-activation-lock-bypass.md) (nur iOS)
    - [Sauberer Start](device-fresh-start.md) (nur Windows)
    - [Modus für verlorene Geräte](device-lost-mode.md) (nur iOS)
    - [Gerät suchen](device-locate.md) (nur iOS)
    - [Neu starten](device-restart.md) (nur Windows)
    - [Zurücksetzen der PIN unter Windows 10](device-windows-pin-reset.md)
    - [Remotesteuerung für Android](device-profile-android-teamviewer.md)
    - [Synchronisieren von Geräten](device-sync.md)


## <a name="next-steps"></a>Nächste Schritte

- Wählen Sie **Geräteaktionen** aus, um den Status von Aktionen auf von Ihnen verwalteten Geräten anzuzeigen.
