---
title: 'Behandeln von Problemen mit Softwareupdates in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Lösen Sie Probleme mit Softwareupdates in Microsoft Intune.
keywords: ''
author: Brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7da927754971fb66a5d8442d0cdf18e0ebfbcd4a
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059076"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Behandlung von Problemen bei Softwareupdates in Microsoft Intune

Lösen Sie Probleme mit Softwareupdates in Microsoft Intune. Eine Liste der Fehlercodes und -beschreibungen finden Sie im Abschnitt der [Fehlercodes zum Softwareupdate-Agent in Microsoft Intune](../protect/software-update-agent-error-codes.md).

## <a name="windows-7-devices-with-many-superseded-updates-stop-reporting-to-intune"></a>Windows 7-Geräte mit vielen ersetzten Updates stellen die Berichterstattung an Intune ein

Bei Microsoft Intune-Clients kann mindestens eines der folgenden Symptome auftreten:

- Geräte stellen plötzlich die Berichterstattung an Intune ein.  
- Bei den Geräten tritt eine hohe CPU-Auslastung auf.
- Anwendungen werden nur langsam installiert, wenn die Installation über das Intune-Portal erfolgt.
- Im Microsoft Intune Center wird der folgende Fehler angezeigt: `An error occurred while updating your computer. Error found: Code 0x800705b4`.
- Unter „Intune-Verwaltungskonsole“ > „Gruppen“ > „Alle Geräte“ > „Status“ wird folgende Meldung angezeigt: `One or more agents that are installed on this computer have errors. The information for this computer may not be accurate or up-to-date.`

Dieses Problem kann auftreten, wenn ersetzte Updates (Updates, die durch ein anderes Update abgelöst wurden) für einen längeren Zeitraum nicht abgelehnt wurden. Während bestimmter Prozesse, z.B. beim Installieren einer Anwendung, überprüft Windows nacheinander alle ersetzten Updates, damit die Updates und deren Nachfolger ordnungsgemäß zugeordnet werden. Wenn die Liste der ersetzten Updates zu lang wird, kann diese Überprüfung aufgrund der Verarbeitungslast und des Zeitaufwands eine hohe CPU-Auslastung verursachen. Dieses Problem betrifft aufgrund der großen Anzahl von ersetzten Updates, die für Windows 7 verfügbar sind, hauptsächlich Windows 7-Geräte. Bei neueren Betriebssystemen ist die Zahl der verfügbaren ersetzten Updates niedriger, und sie sind daher nicht so anfällig für dieses Problem.

**Lösung**

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Softwareupdates**.
3. Lehnen Sie alle ersetzten Updates ab, die für Windows 7 oder für Anwendungen (z.B. Microsoft Office) gelten, die auf den betroffenen Clients installiert wurden.
4. Starten Sie die betroffenen Clients neu.

Wenn Sie Windows 7 ausführen, stellen Sie sicher, dass Sie das folgende Update installiert haben:[3050265 Windows Update-Client für Windows 7: Juni 2015](https://support.microsoft.com/kb/3050265).

## <a name="next-steps"></a>Nächste Schritte

Fordern Sie [Hilfe beim Microsoft-Support](get-support.md) an, oder nutzen Sie die [Communityforen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).