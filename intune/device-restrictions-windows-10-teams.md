---
title: "Windows Intune-Geräteeinschränkungen für Windows 10 Team"
titlesuffix: 
description: "In diesem Artikel erfahren Sie etwas über die verfügbaren Geräteeinschränkungen für Windows 10 Team-Geräte."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 69cceda6857412f7e9a50c58d075caeee4ea9c20
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-windows-10-team-device-restriction-settings"></a>Einstellungen für Geräteeinschränkungen für Windows 10 Team in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

In diesem Artikel erhalten Sie Informationen zu den Einstellungen für Microsoft Intune-Geräteeinschränkungen, die Sie für Windows 10 Team-Geräte konfigurieren können.


## <a name="apps-and-experience"></a>Apps und Benutzerfreundlichkeit

- **Bildschirm aktivieren, wenn eine Person im Raum ist:** Erlaubt das automatische Aktivieren des Geräts, wenn der Sensor eine Person im Raum erkennt.
- **Anzeige von Besprechungsinformationen auf dem Willkommensbildschirm:** Aktivieren Sie diese Option, um die Informationen auszuwählen, die auf der Kachel „Besprechungen“ auf dem Willkommensbildschirm angezeigt werden. Sie können:
    - **Nur Organisator und Zeit anzeigen**
    - **Organisator, Zeit und Thema anzeigen (Thema bei privaten Besprechungen ausblenden)**
- **URL für Hintergrundbild des Willkommensbildschirms:** Aktivieren Sie diese Einstellung, um auf dem **Willkommensbildschirm** von Windows 10 Team-Geräten einen benutzerdefinierten Hintergrund aus der angegebenen URL anzuzeigen.<br>Das Bild muss im PNG-Format vorliegen und die URL muss mit **https://** beginnen.

## <a name="azure-operational-insights"></a>Azure Operational Insights

- **Azure Operational Insights:** Azure Operational Insights ist Teil der Microsoft Operations Manager-Suite und sammelt, speichert und analysiert Protokolldateidaten von Windows 10-Team-Geräten.
Sie müssen eine **Arbeitsbereichs-ID** und einen **Arbeitsbereichsschlüssel** angeben, um die Verbindung mit Azure Operational Insights herstellen zu können.

## <a name="maintenance"></a>Wartung

- **Wartungsfenster für Updates:** Konfiguriert das Fenster, in dem Updates am Gerät vorgenommen werden können. Sie können die **Startzeit** des Fensters und **Dauer in Stunden** (1 bis 5 Stunden) konfigurieren.

## <a name="wireless-projection"></a>Drahtlose Projektion

- **PIN für Funkprojektion:** Gibt an, ob Sie eine PIN eingeben müssen, bevor Sie die drahtlosen Projektionsfunktionen des Geräts verwenden können.
- **Miracast-Funkprojektion:** Aktivieren Sie diese Option, wenn Sie auf dem Gerät mit Windows 10-Team erlauben möchten, für Miracast aktivierte Geräte zum Projizieren zu verwenden.
- **Kanal für die Miracast-Funkprojektion**: Wählen Sie den Miracast-Kanal aus, der zum Herstellen der Verbindung verwendet wird.


## <a name="next-steps"></a>Nächste Schritte

Verwenden Sie die Informationen unter [Konfigurieren von Einstellungen für Geräteeinschränkungen](device-restrictions-configure.md), um das Profil zu speichern und es Benutzern und Geräten zuzuweisen.
