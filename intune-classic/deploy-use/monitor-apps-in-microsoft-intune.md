---
title: "Überwachen von App-Bereitstellungen"
description: "Erfahren Sie, wie Sie Apps überwachen, die Sie mit Intune bereitgestellt haben."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5daad56d-71c8-455b-8a55-f8b33e279a8a
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f583dba7e5ade0e06bc68589623558de0de667c8
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="monitor-app-deployments-in-microsoft-intune"></a>Überwachen von App-Bereitstellungen in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="monitor-an-app-deployment"></a>Überwachen einer App-Bereitstellung
Sie können die verwalteten Apps und den Status aller Bereitstellungen in der Intune-Verwaltungskonsole anzeige. <!---App status is displayed in real-time. You don't have to wait for the device to check-in before you can see this.--->

### <a name="to-view-apps-that-you-manage-and-their-status"></a>So zeigen Sie die von Ihnen verwalteten Apps und ihren Status an
Wählen Sie im Arbeitsbereich **Apps** den Knoten **Apps** und dann die Option **Apps** aus.

Die Liste der von Ihnen verwalteten Apps wird angezeigt. Sie können eine beliebige App auswählen, um im unteren Bereich des Konsolenfensters den Installationsstatus anzuzeigen. Klicken Sie auf diesen Status, um weitere Details anzuzeigen. Angenommen, es wird folgender Status angezeigt: **1 Benutzer steht diese Software zur Verfügung**. Sie können dann auf diese Meldung klicken, um den Namen des Benutzers anzuzeigen.

> [!TIP]
> Über die Dropdownliste **Filter** können Sie die Anzeige auf diejenigen Apps beschränken, die von Ihnen angegebenen Kriterien entsprechen, z. B. die Apps, bei denen ein Installationsfehler aufgetreten ist oder die erfolgreich installiert wurden.
>
> ![Beispiel für App-Filter](./media/app-filters.png)

Außerdem wird im Arbeitsbereich **Dashboard** eine Übersicht über den Status der Apps angezeigt. Wenn Sie in der Übersicht auf eine beliebige Stelle klicken, gelangen Sie zur Liste der Apps.

## <a name="to-view-more-detailed-information-about-an-app"></a>So zeigen Sie detailliertere Informationen über eine App an
Wählen Sie in der Liste der Apps eine beliebige App aus, und klicken Sie dann auf **Eigenschaften anzeigen**.

Wählen Sie auf der Seite **Softwareeigenschaften** für die App eine dieser Registerkarten aus: **Allgemein:** Zeigt allgemeine Informationen über die App und deren Installationsstatus an. **Geräte:** Zeigt die Geräte an, bei denen eine gezielte Bereitstellung der App erfolgreich installiert wurde. **Benutzer:** Zeigt die Benutzer an, auf deren Geräten eine gezielte Bereitstellung der App erfolgreich installiert wurde.

Wie bereits zuvor können Sie auch hier die Dropdownliste **Filter** verwenden, um die auf den Registerkarten angezeigten Werte zu konfigurieren.
