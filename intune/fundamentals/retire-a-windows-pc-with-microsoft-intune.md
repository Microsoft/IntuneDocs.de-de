---
title: Abkoppeln eines Windows-PCs
titleSuffix: Microsoft Intune
description: Abkoppeln eines mit Intune verwalteten Windows-PCs.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7134b61197d671cacc493da1532a7b5d92d095dd
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509821"
---
# <a name="retire-a-windows-pc"></a>Abkoppeln eines Windows-PCs

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Gehen Sie folgendermaßen vor, um Desktops abzukoppeln, die durch Ausführen des Intune-Softwareclients als PCs verwaltet werden. Wenn Sie einen PC abkoppeln, wird dieser aus der Intune-Verwaltung entfernt. Ein PC kann von Intune aus nicht auf die ursprünglichen Werkseinstellungen zurückgesetzt werden.

1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) die Option **Gruppen** &gt; **Alle Geräte** aus (oder eine andere Gruppe, in der der PC enthalten ist, den Sie abkoppeln möchten).

2. Wählen Sie die Geräte aus, die Sie abkoppeln möchten, und wählen Sie dann **Abkoppeln/Zurücksetzen** aus.

Installieren Sie zum erneuten Registrieren eines PC bei Intune den Softwareclient erneut auf dem PC. Gehen Sie hierzu vor wie unter [Installieren des Windows-PC-Clients mit Microsoft Intune](../install-the-windows-pc-client-with-microsoft-intune.md) beschrieben.

Wenn von einem PC keine Verbindung mit Intune hergestellt werden kann, wird im Arbeitsbereich **Dashboard** eine Meldung angezeigt.

Wenn Sie einen PC abkoppeln, werden folgende Aktionen ausgeführt:

- Der PC wird aus Intune-Verwaltung und -Inventar entfernt, und die dem PC zugeordnete Lizenz steht zur erneuten Verwendung zur Verfügung. Durch „Abkoppeln/Zurücksetzen“ wird der Intune-Softwareclient vom PC entfernt, es werden aber keine Apps oder Daten gelöscht. Durch diese Abkopplung wird keine vollständige Zurücksetzung auf dem PC ausgeführt.

- Der Status des Computers wird nicht mehr in der Intune-Konsole angezeigt.

- Intune entfernt den Softwareclient vom PC. Wenn der PC nicht mit Intune verbunden ist, wird der Softwareclient nach der nächsten Verbindungsherstellung entfernt.

- Microsoft Intune Endpoint Protection wird vom PC entfernt. Wenn auf dem PC eine andere Endpunktanwendung installiert, aber deaktiviert ist, kann sie unter Umständen nach dem Entfernen von Microsoft Intune Endpoint Protection wieder aktiviert werden, um sicherzustellen, dass Ihr PC geschützt ist.

- Alle vorhandenen Richtlinien werden vom PC entfernt, und die durch die Richtlinie festgelegten Werte werden geändert.

- Der PC erhält vom Intune-Dienst keine weiteren Softwareupdates oder aktualisierten Schadsoftwaredefinitionen.

- Abgekoppelte PCs können je nach Konfiguration weiterhin Updates über Windows Server Update Services, Windows Update oder Microsoft Update empfangen.

    > [!IMPORTANT]
    > Wurde die Clientsoftware mithilfe eines Gruppenrichtlinienobjekts installiert, dann müssen Sie zuerst das Gruppenrichtlinienobjekt entfernen, bevor Sie die Clientsoftware entfernen können. So wird verhindert, dass die Software erneut installiert wird.

    Wenn der Endpoint Protection-Client nicht deinstalliert werden kann, finden Sie hilfreiche Informationen unter [Problembehandlung für Endpoint Protection](/intune/troubleshoot-endpoint-protection-in-microsoft-intune).

## <a name="see-also"></a>Siehe auch

[Allgemeine Aufgaben zur Verwaltung von Windows-PCs mit dem Intune-Softwareclient](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
