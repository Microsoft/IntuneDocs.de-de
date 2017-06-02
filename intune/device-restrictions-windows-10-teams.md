---
title: "Intune-Geräteeinschränkungen für Windows 10 Team"
titleSuffix: Intune Azure preview
description: "Intune in Azure (Vorschau): Erfahren Sie etwas über die verfügbaren Geräteeinschränkungen für Windows 10 Team-Geräte."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 677c41a2-5344-4c52-85f0-809dce3a5d5b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: afbbe6b7649e1ffc3f84ada64396d9033a2db200
ms.contentlocale: de-de
ms.lasthandoff: 05/23/2017


---

# <a name="windows-10-team-device-restriction-settings-in-microsoft-intune"></a>Einstellungen für Geräteeinschränkungen für Windows 10 Team in Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

- **Bildschirm aktivieren, wenn eine Person im Raum ist:** Erlaubt das automatische Aktivieren des Geräts, wenn der Sensor eine Person im Raum erkennt.
- **PIN für Funkprojektion:** Gibt an, ob Sie eine PIN eingeben müssen, bevor Sie die drahtlosen Projektionsfunktionen des Geräts verwenden können.
- **Miracast-Funkprojektion:** Aktivieren Sie diese Option, wenn Sie auf dem Gerät mit Windows 10-Team erlauben möchten, für Miracast aktivierte Geräte zum Projizieren zu verwenden.
- **Anzeige von Besprechungsinformationen auf dem Willkommensbildschirm:** Aktivieren Sie diese Option, um die Informationen auszuwählen, die auf der Kachel „Besprechungen“ des Willkommensbildschirms angezeigt werden. Sie können:
    - **Nur Organisator und Zeit anzeigen**
    - **Organisator, Zeit und Thema anzeigen (Thema bei privaten Besprechungen ausblenden)**
- **URL für Hintergrundbild des Willkommensbildschirms:** Aktivieren Sie diese Einstellung, um auf dem **Willkommensbildschirm** von Windows 10 Team-Geräten einen benutzerdefinierten Hintergrund aus der angegebenen URL anzuzeigen.<br>Das Bild muss im PNG-Format vorliegen und die URL muss mit **https://** beginnen.
- **Wartungsfenster für Updates:** Konfiguriert das Fenster, in dem Updates am Gerät vorgenommen werden können. Sie können die Startzeit und Länge des Fensters (1 bis 5 Stunden) konfigurieren.
- **Azure Operational Insights:** Azure Operational Insights ist Teil der Microsoft Operations Management Suite und sammelt, speichert und analysiert Protokolldaten von Windows 10-Team-Geräten.<br>Sie müssen eine **Arbeitsbereichs-ID** und einen **Arbeitsbereichsschlüssel** angeben, um die Verbindung mit Azure Operational Insights herstellen zu können.
