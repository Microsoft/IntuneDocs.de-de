---
title: Anzeigen von Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Zeigen Sie Details zu Ihren Geräten an, z.B. Betriebssystem, Speicherplatz, Hersteller und Modell. Mit Microsoft Intune in Azure können Sie eine Liste der installierten Apps abrufen, Konformitätsrichtlinien überprüfen und TeamViewer einrichten. Die Vorgehensweise ähnelt der Anzeige des Bestands der Geräte, die Sie verwalten.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: eaaf3e9807a8eab66c24f4d1bb3c3c5ea9f4cfe0
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="see-device-details-in-intune"></a>Anzeigen von Gerätedetails in Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Das Feature **Geräte** bietet zusätzliche Informationen zu den von Ihnen verwalteten Geräten, z.B. zur Hardware und zu installierten Apps. 

Dieser Artikel erläutert, wie Sie all Ihre Geräte und deren Eigenschaften im Azure-Portal anzeigen.

## <a name="view-your-device-details"></a>Anzeigen der Gerätedetails

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte**. Im Bereich „Geräte“ sind mehrere Optionen verfügbar:

   - **Übersicht**: Erhalten Sie Informationen zu Geräten, die Sie registriert haben, und zu den Betriebssystemen der einzelnen Geräte.
   - **Verwalten**: Wählen Sie **Alle Geräte** oder **Azure AD-Geräte** aus, um eine Liste aller von Ihnen verwalteten Geräte anzuzeigen.
    Wählen Sie in der Liste eins der Geräte aus. Dieser Schritt öffnet den Bereich <*Gerätename*>  – **Übersicht**, in dem Sie Folgendes auswählen können:
     - **Übersicht**: Hier sehen Sie u.a. den Gerätenamen, den Besitzer und Informationen dazu, ob es sich um ein BYOD-Gerät (Bring Your Own Device) handelt und wann es eingecheckt wurde.
     - **Hardware**: Hier finden Sie Informationen zum freien Speicherplatz, zu Modell und Hersteller, und weitere Details zum Gerät.
     - **Ermittelte Apps**: Zeigt eine Liste aller auf dem Gerät installierten Apps an, die von Intune gefunden wurden.
     - **Gerätekonformität**: Zeigt den Status aller Konformitätsrichtlinien an, die dem Gerät zugewiesen wurden.
     - **Gerätekonfiguration**: Zeigt den Konformitätsstatus aller Gerätekonfigurationsrichtlinien an, die dem Gerät zugewiesen wurden.
   - **Monitor**: Wählen Sie **Geräteaktionen** aus, um eine Liste der Aktionen, die auf von Ihnen verwalteten Geräten ausgeführt wurden, und deren aktuellen Status anzuzeigen. **Überwachungsprotokolle** zeigen den Status verschiedener Tasks.
   - **Setup** > **TeamViewer-Connector**: Hier können Sie Remoteverwaltung auf Geräten mithilfe der Software TeamViewer konfigurieren. Weitere Informationen finden Sie unter [Bereitstellen von Remoteunterstützung für mit Intune verwaltete Android-Geräte](device-profile-android-teamviewer.md).

Intune erfasst nur auf unternehmenseigenen Geräten eine App-Liste. Auf persönlichen Geräten werden keine Apps überprüft. Bei unternehmenseigenen Windows 10 PCs werden nur moderne Apps aufgeführt. Intune sammelt keine Informationen über Win32-Apps auf dem Gerät. Je nach Netzbetreiber der Geräte werden möglicherweise nicht alle Apps erfasst.

## <a name="next-steps"></a>Nächste Schritte
Finden Sie heraus, welche Aktionen beim [Verwalten Ihrer Geräte](device-management.md) mit Intune noch möglich sind.
