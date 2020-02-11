---
title: Verwalten von Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: 'In diesem Artikel erhalten Sie Informationen zum Überprüfen der von Ihnen verwalteten Geräte mit Microsoft Intune. Die folgenden Aspekte werden behandelt: Exportieren einer Geräteliste im CSV-Format, Anzeigen Ihrer mit Azure Active Directory verknüpften Geräte, Überprüfen eines Änderungsprotokolls der Aktionen auf dem Gerät, Verwenden des TeamViewer-Connectors, damit IT-Administratoren Fehler auf Android-Geräten über eine Remoteverbindung behandeln können, und Anzeigen aller Aktionen, die auf dem Gerät ausgeführt werden können.'
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: dde69fc70522684193f9cf6712a2192f77110dab
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754251"
---
# <a name="what-is-microsoft-intune-device-management"></a>Was ist die Microsoft Intune Geräteverwaltung?

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Als IT-Administrator müssen Sie sicherstellen, dass verwaltete Geräte die Ressourcen bereitstellen, die Benutzer für Ihre Arbeit benötigen, während gleichzeitig die Daten vor Risiken geschützt werden.

Die Workload **Geräte** liefert Informationen zu den verwalteten Geräten und ermöglicht die Ausführung von Remoteaufgaben auf diesen Geräten.

## <a name="get-to-your-devices"></a>Zugreifen auf Geräte

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
3. Klicken Sie auf **Geräte**. In dieser Anzeige finden Sie detaillierte Informationen zu den einzelnen Geräten und deren möglichen Funktionen:

   - Unter **Übersicht** wird eine Momentaufnahme der registrierten Geräte angezeigt. Außerdem wird angezeigt, wie viele Geräte die verschiedenen Plattformen verwenden, einschließlich Android, iOS usw.
   - Unter **Alle Geräte** wird eine Liste der registrierten Geräte angezeigt, die Sie verwalten.

     Verwenden Sie das **Export**-Feature, um eine CSV-Liste aller Geräte in Zehntausender- (Internet Explorer) bzw. Dreißigtausenderschritten (Microsoft Edge, Chrome) zu erstellen.

     Wählen Sie ein beliebiges Gerät aus, [um zusätzliche Details zu dem jeweiligen Gerät anzuzeigen](device-inventory.md), einschließlich Hardwaredetails, installierten Apps, den Status der Konformitätsrichtlinie usw.

   - Unter **Azure AD-Geräte** wird eine Liste der Geräte angezeigt, die in Azure Active Directory (Azure AD) registriert oder damit verknüpft sind. Weitere Informationen zur [Azure AD-Geräteverwaltung](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
   - Die **Geräteaktionen** umfassen einen Verlauf der Remoteaktionen, die auf Geräten ausgeführt wurden, einschließlich der Aktion, dem Status, der Person, die die Aktion initiiert hat, und dem Zeitpunkt.

     ![Screenshot der Überwachung von Geräteaktionen](./media/device-management/monitor-device-actions.png)

   - **Überwachungsprotokolle** stellen Ihnen einen Datensatz von Aktivitäten zur Verfügung, die eine Änderung in Intune bewirken. [Überwachungsprotokolle](../fundamentals/monitor-audit-logs.md) enthalten weitere Details.
   - Der **TeamViewer-Connector** ist ein Dienst, über den Benutzer von mit Intune verwalteten Android-Geräten Remoteunterstützung von ihrem IT-Administrator erhalten. Erfahren Sie mehr über [TeamViewer](teamviewer-support.md).
   - Über **Help and Support** (Hilfe und Unterstützung) finden Sie eine Verknüpfung zu Tipps zur Problembehandlung, zum Anfordern von Unterstützung und zum Überprüfen des Status von Intune.

## <a name="available-device-actions"></a>Verfügbare Geräteaktionen
Die verfügbaren Aktionen hängen von der Geräteplattform und der Konfiguration des Geräts ab.

- [Anzeigen des Gerätebestands](device-inventory.md)
- Ausführen von Remotegeräteaktionen:
  - [Außerkraftsetzen](devices-wipe.md#retire)
  - [Zurücksetzen](devices-wipe.md#wipe)
  - [Remotesperre](device-remote-lock.md)
  - [Kennung zurücksetzen](device-passcode-reset.md)
  - [Deaktivieren der Aktivierungssperre](device-activation-lock-bypass.md) (nur iOS)
  - [Sauberer Start](device-fresh-start.md) (nur Windows)
  - [Modus für verlorene Geräte](device-lost-mode.md) (nur iOS)
  - [Gerät suchen](device-locate.md) (nur iOS)
  - [Neu starten](device-restart.md) (nur Windows)
  - [Zurücksetzen der PIN unter Windows 10](device-windows-pin-reset.md)
  - [Remotesteuerung für Android](teamviewer-support.md)
  - [Synchronisieren von Geräten](device-sync.md)
  - [Gerät umbenennen](device-rename.md)
  - [Senden von benutzerdefinierten Benachrichtigungen](custom-notifications.md#send-a-custom-notification-to-a-single-device) (Android, iOS)
  - [BitLocker-Schlüsselrotation](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys) (nur Windows)

## <a name="next-steps"></a>Nächste Schritte

- Wählen Sie unter **Alle Geräte** ein Gerät aus, um mehr Details zu dem bestimmten Gerät anzuzeigen.
- Wählen Sie **Geräteaktionen** aus, um den Status von Aktionen auf von Ihnen verwalteten Geräten anzuzeigen.
