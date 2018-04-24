---
title: Einstellungen für Windows Team-Konfigurationsrichtlinie
description: Verwenden Sie die **allgemeine Windows 10 Team-Konfigurationsrichtlinie** von Microsoft Intune, um Einstellungen für registrierte Windows 10 Team-Geräte (z. B. Microsoft Surface Hub) zu konfigurieren.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 70b1091cd58439b7d42eab1a612b0b63ca39103d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="windows-team-configuration-policy-settings-in-microsoft-intune"></a>Einstellungen für Windows Team-Konfigurationsrichtlinie in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Verwenden Sie die **allgemeine Windows 10 Team-Konfigurationsrichtlinie** von Microsoft Intune, um Einstellungen für registrierte Windows 10 Team-Geräte (z. B. Microsoft Surface Hub) zu konfigurieren.


|                                  Name der Einstellung                                   |                                                                                                                                                                Details                                                                                                                                                                |
|---------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <strong>Zulassen der automatischen Aktivierung des Bildschirms, wenn Sensoren eine Person im Raum feststellen</strong>   |                                                                                                                         Ermöglicht das automatische Aktivieren des Geräts, wenn der Sensor eine Person im Raum erkennt.                                                                                                                          |
|              <strong>PIN für Funkprojektion anfordern</strong>               |                                                                                                             Gibt an, ob Sie eine PIN eingeben müssen, bevor Sie die drahtlosen Projektionsfunktionen des Geräts verwenden können.                                                                                                             |
|          <strong>Wartungsfenster für Geräteupdates festlegen</strong>           |                                                                                          Konfiguriert das Fenster, in dem Updates am Gerät vorgenommen werden können. Sie können die Startzeit und Länge des Fensters (1 bis 5 Stunden) konfigurieren.                                                                                           |
|               <strong>Azure Operational Insights aktivieren</strong>                |                  Azure Operational Insights ist Teil der Microsoft Operations Manager-Suite und sammelt, speichert und analysiert Protokolldaten von Windows 10-Teamgeräten.<br /><br />Sie müssen eine <strong>Arbeitsbereichs-ID</strong> und einen <strong>Arbeitsbereichsschlüssel</strong> angeben, um die Verbindung mit Azure Operational Insights herstellen zu können.                   |
|              <strong>Miracast-Funkprojektion aktivieren</strong>               |                                          Aktivieren Sie diese Option, wenn Sie es dem Windows 10-Teamgerät ermöglichen möchten, für Miracast aktivierte Geräte zum Projizieren zu verwenden.<br /><br />Wenn Sie diese Option aktivieren, wählen Sie unter <strong>Miracast-Kanal auswählen</strong> den Miracast-Kanal aus, der zum Projizieren von Inhalten verwendet wurde.                                           |
| <strong>Im Willkommensbildschirm angezeigte Besprechungsinformationen auswählen</strong> | Wenn Sie diese Option aktivieren, können Sie die Informationen auswählen, die auf der Kachel <strong>Besprechungen</strong> des Bildschirms <strong>Willkommen</strong> angezeigt werden. Sie können:<br /><br />-   <strong>Nur Organisator und Zeit anzeigen</strong><br />-   <strong>Organisator, Zeit und Thema anzeigen (Thema bei privaten Besprechungen ausblenden)</strong> |
|                <strong>URL zum Bild für den Sperrbildschirmhintergrund</strong>                 |                                           Aktivieren Sie diese Einstellung, um auf dem <strong>Willkommensbildschirm</strong> von Windows 10 Team-Geräten einen benutzerdefinierten Hintergrund aus der angegebenen URL anzuzeigen.<br /><br />Das Bild muss im PNG-Format vorliegen und die URL muss mit <strong>https://</strong> beginnen.                                            |

### <a name="see-also"></a>Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

