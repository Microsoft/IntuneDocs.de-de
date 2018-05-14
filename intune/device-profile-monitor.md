---
title: Anzeigen von Geräteprofilen mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Zeigen Sie die Gerätekonfigurationsprofil-Details in Microsoft Intune an und verwalten Sie sie dort, zeigen Sie dort ein grafisches Diagramm der Anzahl der Geräte an, die einem Profil zugewiesen wurden, und zeigen Sie an, welchen Geräten Profile zugewiesen bzw. für welche Geräte sie bereitgestellt wurden.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e1c2eb08db58940ed575b3dea011395edd6711fc
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2018
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Überwachen von Geräteprofilen in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune umfasst einige Features im Azure-Portal zum Überwachen und Verwalten Ihrer Gerätekonfigurationsprofile. Sie können z.B. den Status eines Profils überprüfen, anzeigen, welche Geräte zugewiesen sind, und die Eigenschaften eines Profils aktualisieren.

## <a name="view-existing-profiles"></a>Anzeigen von vorhandenen Profilen

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Gerätekonfiguration** > **Profile**.

Alle Ihre vorhandenen Profile werden aufgelistet und beinhalten Details wie z.B. die Plattform, und ob das Profil einem Gerät zugewiesen ist.

## <a name="view-details-on-a-profile"></a>Anzeigen von Details zu einem Profil

Nachdem Sie Ihr Geräteprofil erstellt haben, bietet Intune grafische Diagramme. Diese Diagramme zeigen den Status eines Profils an, etwa ob es erfolgreich Geräten zugewiesen wurde, oder ob das Profil einen Konflikt aufweist.

1. Wählen Sie ein vorhandenes Profil aus. Wählen Sie z.B. ein macOS-Profil aus.
2. Wählen Sie die Registerkarte **Übersicht** aus.

    Das grafische Diagramm zeigt die Anzahl der Geräte an, die einem bestimmten Geräteprofil zugewiesen sind. Wenn das Gerätekonfigurationsprofil z.B. für macOS-Geräte gilt, wird im Diagramm nur die Anzahl der macOS-Geräte aufgelistet.

    Es zeigt auch die Anzahl der Geräte anderer Plattformen an, die dem gleichen Geräteprofil zugewiesen sind. Es zeigt beispielsweise die Anzahl der Nicht-macOS-Geräte an.

    ![Anzeigen der Anzahl der Geräte, die dem Geräteprofil zugewiesen sind](./media/device-configuration-profile-graphical-chart.png)

3. Wählen Sie den Kreis im grafischen Diagramms an. Der **Gerätestatus** wird geöffnet.

    Die dem Profil zugeordneten Geräte sind aufgelistet, und es wird angezeigt, ob das Profil erfolgreich bereitgestellt wurde. Beachten Sie auch, dass nur die Geräte der spezifischen Plattform (z.B. macOS) aufgelistet sind.

    Schließen Sie die Gerätestatusdetails.

4. In den Eigenschaften des Profils (wählen Sie unter **Profile** ein bestimmtes Profil aus) können Sie auch vorhandene Eigenschaften ändern:
  - **Eigenschaften**: Ändern Sie den Namen, oder aktualisieren Sie alle vorhandenen Einstellungen.
  - **Zuweisungen**: Schließen Sie Geräte für die Anwendung der Richtlinie ein oder davon aus. Wählen Sie **Ausgewählte Gruppen** aus, um bestimmte Gruppen auszuwählen.
  - **Gerätestatus**: Die dem Profil zugeordneten Geräte sind aufgelistet, und es wird angezeigt, ob das Profil erfolgreich bereitgestellt wurde. Sie können ein bestimmtes Gerät einschließlich der installierten Apps auswählen, um noch mehr Details zu erfahren.
  - **Benutzerstatus**: Listet die Namen der Benutzer mit Geräten auf, die diesem Profil unterliegen, und ob das Profil erfolgreich bereitgestellt wurde. Sie können einen bestimmten Benutzer auswählen, um noch mehr Informationen zu erhalten.
  - **Status pro Einstellung**: Filtert die Ausgabe durch Anzeige der einzelnen Einstellungen innerhalb des Profils, und zeigt an, ob die Einstellung erfolgreich angewendet wurde.

## <a name="next-steps"></a>Nächste Schritte
[Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md)  
[Häufig auftretende Probleme und Lösungen für Geräteprofile in Microsoft Intune](device-profile-troubleshoot.md)