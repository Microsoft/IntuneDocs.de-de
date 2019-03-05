---
title: Behandeln von Problemen mit Endpoint Protection in Intune – Azure | Microsoft-Dokumentation
description: Lösen Sie Probleme, während Sie den Endpunktschutz von Microsoft Intune verwenden.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4a07ddbe5d69077229b3b9392f7aa5a23520796
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238794"
---
# <a name="troubleshoot-endpoint-protection-in-intune"></a>Beheben von Problemen mit Endpoint Protection in Intune

Diese Informationen helfen Ihnen, Probleme bei der Verwendung von Endpoint Protection zu beheben. Sie können auch [die Ereignisprotokolle und Fehlercodes überprüfen, um Probleme mit Windows Defender Antivirus zu behandeln](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

Wenn Sie weitere Hilfe benötigen, können Sie auch [Support für Microsoft Intune](get-support.md) anfordern.

### <a name="error-messages"></a>Fehlermeldungen
Dieser Abschnitt beschreibt mögliche Ursachen und Lösungen für die folgenden Fehler und Warnungen.

|Angezeigter Status|Mögliche Ursachen|Mögliche Lösungen|
|---------------|--------------------|-----------------------|
|**Die Endpoint Protection-Engine ist nicht verfügbar**|Die Endpoint Protection-Engine von Intune wurde beschädigt oder gelöscht.|Wenn die Endpoint Protection-Engine von Intune beschädigt ist, können Sie versuchen, die Software zu aktualisieren oder neu zu installieren.<br /><br />Klicken Sie zum Erzwingen eines sofortigen Updates in der Endpoint Protection-Clientsoftware auf **Update** (auf verwalteten Computern auf der Taskleiste).<br /><br />Wenn die Engine nicht aktualisiert werden kann, müssen Sie die Endpoint Protection-Engine erneut installieren.<br /><br />Suchen Sie in der Liste der installierten Programme in der Systemsteuerung auf dem verwalteten Computer nach **Microsoft Intune Endpoint Protection-Agent**, und deinstallieren Sie die Anwendung.<br /><br />Während der nächsten Updatesynchronisierung wird das fehlende Programm von Microsoft Online Management Update Manager erkannt und zum geplanten Installationszeitpunkt neu installiert.|
|**Endpoint Protection ist deaktiviert**|Intune Endpoint Protection wurde durch einen Administrator mithilfe eines Konfigurationsprofils oder durch einen Benutzer auf einem verwalteten Computer deaktiviert.|Aktivieren Sie Endpoint Protection. Lesen Sie hierzu [Festlegen von Endpoint Protection-Einstellungen](endpoint-protection-configure.md) in Intune, oder [aktivieren Sie Windows Defender für den Zugriff auf Unternehmensressourcen](/intune-user-help/turn-on-defender-windows).|
|**Echtzeitschutz wurde deaktiviert**|Auf einem verwalteten Computer wurde der Echtzeitschutz durch einen Administrator mithilfe eines Profils oder durch einen Benutzer auf einem verwalteten Computer deaktiviert.|Aktivieren Sie Endpoint Protection. Lesen Sie hierzu die Informationen zu [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) in Intune, oder [aktivieren Sie den Echtzeitschutz für den Zugriff auf Unternehmensressourcen](/intune-user-help/turn-on-defender-windows). |
|**Download-Überprüfung deaktiviert**|Die Downloadüberprüfung wurde von einem Administrator mithilfe eines Profils oder von einem Benutzer auf einem verwalteten Computer deaktiviert.|Aktivieren Sie die Überprüfung. Lesen Sie hierzu die Informationen zu [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) in Intune, oder [aktivieren Sie den Echtzeitschutz für den Zugriff auf Unternehmensressourcen](/intune-user-help/turn-on-defender-windows). |
|**Datei- und Programmaktivitätsüberwachung deaktiviert**|Die Datei- und Programmaktivitätsüberwachung wurde von einem Administrator mithilfe eines Profils oder von einem Benutzer auf einem verwalteten Computer deaktiviert.|Aktivieren Sie die Datei- und Programmaktivität. Lesen Sie hierzu die Informationen zu [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) in Intune, oder [aktivieren Sie den Echtzeitschutz für den Zugriff auf Unternehmensressourcen](/intune-user-help/turn-on-defender-windows). |
|**Verhaltensüberwachung deaktiviert**|Die Verhaltensüberwachung wurde von einem Administrator mithilfe eines Profils oder von einem Benutzer auf einem verwalteten Computer deaktiviert.|Aktivieren Sie die Verhaltensüberwachung. Lesen Sie hierzu die Informationen zu [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) in Intune, oder [aktivieren Sie den Echtzeitschutz für den Zugriff auf Unternehmensressourcen](/intune-user-help/turn-on-defender-windows). |
|**Skriptüberprüfung deaktiviert**|Die Skriptüberprüfung wurde von einem Administrator mithilfe eines Profils oder von einem Benutzer auf einem verwalteten Computer deaktiviert.|Aktivieren Sie die Skriptüberprüfung. Lesen Sie hierzu die Informationen zu [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) in Intune, oder [aktivieren Sie den Echtzeitschutz für den Zugriff auf Unternehmensressourcen](/intune-user-help/turn-on-defender-windows). |
|**Netzwerkinspektionssystem deaktiviert**|Das Netzwerkinspektionssystem wurde durch einen Administrator mithilfe eines Profils oder von einem Benutzer auf einem verwalteten Computer deaktiviert.|Aktivieren Sie das Netzwerkinspektionssystem (NIS). Lesen Sie hierzu die Informationen zu [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) in Intune, oder [aktivieren Sie den Echtzeitschutz für den Zugriff auf Unternehmensressourcen](/intune-user-help/turn-on-defender-windows). |
|**Malwaredefinitionen sind veraltet**|Möglicherweise war der Computer über einen längeren Zeitraum vom Internet getrennt, sodass seine Malwaredefinitionen länger nicht aktualisiert worden sind. Dieser Status wird angezeigt, wenn die Malwaredefinitionen auf dem Computer mehr als 14 Tage veraltet sind.|Wenn Schadsoftwaredefinitionen veraltet sind, können Sie die Definitionen mit [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) aktualisieren.|
|**Vollständige Überprüfung ist überfällig**|Seit 14 Tagen wurde keine vollständige Überprüfung ausgeführt. Ursache hierfür kann ein Neustart des Computers während einer vollständigen Überprüfung sein.|Wenn eine vollständige Überprüfung überfällig ist, können Sie eine einmalige vollständige Überprüfung ausführen oder wiederholte vollständige Überprüfungen planen. Weitere Informationen finden Sie unter [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus). |
|**Schnellüberprüfung ist überfällig**|Seit 14 Tagen wurde keine Schnellüberprüfung ausgeführt. Ursache hierfür kann ein Neustart während einer Schnellüberprüfung sein.|Wenn eine Schnellüberprüfung überfällig ist, können Sie eine einmalige Schnellüberprüfung ausführen oder wiederholte Schnellüberprüfungen planen. Weitere Informationen finden Sie unter [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus).|
|**Eine andere Endpunktschutzanwendung wird ausgeführt**|Eine andere Endpunktschutzanwendung wird ausgeführt, und der Computer befindet sich in einem fehlerfreien Zustand.|Wenn bereits eine andere Endpunktschutzanwendung installiert ist und Intune diese Anwendung erkennt, wird das Geräte möglicherweise instabil.|

### <a name="next-steps"></a>Nächste Schritte
Wenn Sie weitere Hilfe benötigen, können Sie auch [Support für Microsoft Intune](get-support.md) anfordern.
