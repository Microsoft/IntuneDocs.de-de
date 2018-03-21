---
title: "Anzeigen von Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation"
description: "Zeigen Sie Details zu Ihren Geräten an, z.B. Betriebssysteme, Speicherplatz, Hersteller und Modell und vieles mehr. Mit Microsoft Intune in Azure können Sie eine Liste der installierten Apps abrufen, Konformitätsrichtlinien überprüfen, TeamViewer einrichten und viele weitere Aktionen ausführen. Die Vorgehensweise ähnelt der Anzeige des Bestands der Geräte, die Sie verwalten."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 934ba0853f8bee851f7027580c276a9fff911b7f
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="see-device-details-in-intune"></a>Anzeigen von Gerätedetails in Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Das Feature **Geräte** bietet zusätzliche Informationen zu den von Ihnen verwalteten Geräten, z.B. zur Hardware und zu installierten Apps. 

Dieser Artikel erläutert, wie Sie all Ihre Geräte und deren Eigenschaften im Azure-Portal anzeigen.

## <a name="view-your-device-details"></a>Anzeigen der Gerätedetails

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte**. Im Bereich „Geräte“ sind mehrere Optionen verfügbar:

  - **Übersicht**: Erhalten Sie Informationen zu Geräten, die Sie registriert haben, und zu den Betriebssystemen der einzelnen Geräte.
  - **Verwalten**: Wählen Sie **Alle Geräte** oder **Azure AD-Geräte** aus, um eine Liste aller von Ihnen verwalteten Geräte anzuzeigen.
    Wählen Sie in der Liste eins der Geräte aus. Dieser Schritt öffnet den Bereich <*Gerätename*>  – **Übersicht**, in dem Sie Folgendes auswählen können:
    - **Übersicht**: Hier sehen Sie den Gerätenamen, den Besitzer und Informationen dazu, ob es sich um ein BYOD-Gerät (Bring Your Own Device) handelt und wann es eingecheckt wurde, sowie weitere Details.
    - **Hardware**: Hier finden Sie Informationen zum freien Speicherplatz, zu Modell und Hersteller und weitere Details zum Gerät.
    - **Ermittelte Apps**: Listet alle auf dem Gerät installierten Apps auf, die von Intune gefunden wurden.
    - **Gerätekonformität**: Zeigt den Status aller Konformitätsrichtlinien an, die dem Gerät zugewiesen wurden.
    - **Gerätekonfiguration**: Zeigt den Konformitätsstatus aller Gerätekonfigurationsrichtlinien an, die dem Gerät zugewiesen sind.
- **Monitor**: Wählen Sie **Geräteaktionen** aus, um eine Liste der Aktionen, die auf von Ihnen verwalteten Geräten ausgeführt wurden, und deren aktuellen Status anzuzeigen. **Überwachungsprotokolle** zeigen den Status verschiedener Tasks.
- **Setup** > **TeamViewer-Connector**: Hier können Sie Remoteverwaltung auf Geräten mithilfe der Software TeamViewer konfigurieren. Weitere Informationen finden Sie unter [Bereitstellen von Remoteunterstützung für mit Intune verwaltete Android-Geräte](device-profile-android-teamviewer.md).

Intune erfasst nur auf unternehmenseigenen Geräten eine App-Liste. Auf persönlichen Geräten werden keine Apps überprüft. Bei unternehmenseigenen Windows 10 PCs werden nur moderne Apps aufgeführt. Intune sammelt keine Informationen über Win32-Apps auf dem Gerät. Je nach Netzbetreiber werden möglicherweise nicht alle Apps erfasst.

## <a name="next-steps"></a>Nächste Schritte
Finden Sie heraus, welche Aktionen beim [Verwalten Ihrer Geräte](device-management.md) mit Intune noch möglich sind.
