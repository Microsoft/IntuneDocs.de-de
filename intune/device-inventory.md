---
title: Anzeigen von Gerätedetails mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Zeigen Sie Details zu Ihren Geräten an, z.B. Betriebssystem, Speicherplatz, Hersteller und Modell. Mit Microsoft Intune in Azure können Sie eine Liste der installierten Apps abrufen, Konformitätsrichtlinien überprüfen und TeamViewer einrichten. Die Vorgehensweise ähnelt der Anzeige des Bestands der Geräte, die Sie verwalten.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f66c0695c7e3d1f4bb7a5ca3abceeb13f6af41f2
ms.sourcegitcommit: 3c4ea8d6809a63042705b5ed4f25ba80f522070e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2018
ms.locfileid: "34051605"
---
# <a name="see-device-details-in-intune"></a>Anzeigen von Gerätedetails in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Das Feature **Geräte** bietet zusätzliche Informationen zu den von Ihnen verwalteten Geräten, z.B. zur Hardware und zu installierten Apps.

Dieser Artikel erläutert, wie Sie all Ihre Geräte und deren Eigenschaften im Azure-Portal anzeigen.

## <a name="view-the-device-details"></a>Anzeigen der Gerätedetails

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte** > **Alle Geräte**, und wählen Sie anschließend eins der aufgeführten Geräte aus, damit dessen Gerätedetails geöffnet werden:

   - In der **Übersicht** wird der Gerätename angezeigt, und es sind einige der Schlüsseleigenschaften des Geräts aufgeführt. Sie erfahren also z.B., ob es sich um ein Bring Your Own Device-Gerät (BYOD) handelt, wann es eingecheckt hat usw. Klicken Sie auf **More** (Mehr), um außerdem die folgenden Vorgänge auszuführen:
     - Entfernen von Unternehmensdaten
     - Löschen des Geräts
     - Sperren des Geräts über eine Remotesperre
     - Löschen
     - Starten einer Remoteunterstützungssitzung
   - Verwenden Sie die **Eigenschaften**, um eine [von Ihnen erstellte Gerätekategorie](device-group-mapping.md) zuzuweisen, und ändern Sie den Besitz des Geräts in ein privates oder ein unternehmenseigenes Gerät.
   - Der Bereich **Hardware** umfasst einige Details zu dem Gerät, einschließlich der Geräte-ID, dem Betriebssystem und der Betriebssystemversion, dem Speicherplatz, dem Modell und dem Hersteller, Einstellungen für bedingten Zugriff etc.
   - Unter **Ermittelte Apps** werden alle auf dem Gerät installierten Apps aufgeführt, die von Intune gefunden wurden. Sie können die App-Liste als eine CSV-Datei **exportieren**.
   - Unter **Gerätekonformität** werden alle zugewiesenen Konformitätsrichtlinien aufgeführt, und es wird angezeigt, ob das Gerät mit diesen Richtlinien konform ist.
   - Unter **Gerätekonfiguration** werden alle Gerätekonfigurationsrichtlinien angezeigt, die dem Gerät zugewiesen sind, und Sie können erkennen, ob die Richtlinie erfolgreich war oder fehlgeschlagen ist.

Intune erfasst nur auf unternehmenseigenen Geräten eine App-Liste. Auf persönlichen Geräten werden keine Apps überprüft. Bei unternehmenseigenen Windows 10 PCs werden nur moderne Apps aufgeführt. Intune sammelt keine Informationen über Win32-Apps auf dem Gerät. Je nach Netzbetreiber der Geräte werden möglicherweise nicht alle Apps erfasst.

|Plattform|Geräte, die einem Benutzer gehören|Geräte, die dem Unternehmen gehören|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10 (ohne Configuration Manager-Client)|Nur verwaltete Apps|Nur verwaltete Apps|
|Windows 8.1 (ohne Configuration Manager-Client)|Nur verwaltete Apps|Nur verwaltete Apps|  
|Windows Phone 8|Nur verwaltete Apps|Nur verwaltete Apps|  
|Windows RT|Nur verwaltete Apps|Nur verwaltete Apps|  
|iOS|Nur verwaltete Apps|Alle auf dem Gerät installierten Apps|
|macOS|Alle auf dem Gerät installierten Apps|Alle auf dem Gerät installierten Apps|  
|Android|Nur verwaltete Apps|Alle auf dem Gerät installierten Apps|  

## <a name="next-steps"></a>Nächste Schritte
Finden Sie heraus, welche Aktionen beim [Verwalten Ihrer Geräte](device-management.md) mit Intune noch möglich sind.