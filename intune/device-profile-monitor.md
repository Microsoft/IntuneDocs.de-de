---
title: Anzeigen von Geräteprofilen mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Zeigen Sie die Gerätekonfigurationsprofil-Details in Microsoft Intune an, und verwalten Sie sie, zeigen Sie ein grafisches Diagramm der Anzahl der Geräte an, die einem Profil zugewiesen wurden, und zeigen Sie an, welchen Geräten Profile zugewiesen bzw. für welche Geräte sie bereitgestellt wurden. Es können auch Probleme in Profilen behoben werden, die in Konflikt stehende Einstellungen beinhalten.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: dc3a9620532951bd78e545e87b0d43dd6be3efe5
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186595"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Überwachen von Geräteprofilen in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune umfasst einige Features im Azure-Portal zum Überwachen und Verwalten Ihrer Gerätekonfigurationsprofile. Sie können z.B. den Status eines Profils überprüfen, anzeigen, welche Geräte zugewiesen sind, und die Eigenschaften eines Profils aktualisieren.

## <a name="view-existing-profiles"></a>Anzeigen von vorhandenen Profilen

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Gerätekonfiguration** > **Profile**.

Alle Ihre vorhandenen Profile werden aufgelistet und beinhalten Details wie z.B. die Plattform und ob das Profil einem Gerät zugewiesen ist.

## <a name="view-details-on-a-profile"></a>Anzeigen von Details zu einem Profil

Nachdem Sie Ihr Geräteprofil erstellt haben, bietet Intune grafische Diagramme. Diese Diagramme zeigen den Status eines Profils an, etwa ob es erfolgreich Geräten zugewiesen wurde, oder ob das Profil einen Konflikt aufweist.

1. Wählen Sie ein vorhandenes Profil aus. Wählen Sie z.B. ein macOS-Profil aus.
2. Wählen Sie die Registerkarte **Übersicht** aus.

    Das Grafikdiagramm oben zeigt die Anzahl der Geräte an, die einem bestimmten Geräteprofil zugewiesen sind. Wenn das Gerätekonfigurationsprofil z.B. für macOS-Geräte gilt, wird im Diagramm nur die Anzahl der macOS-Geräte aufgelistet.

    Es zeigt auch die Anzahl der Geräte anderer Plattformen an, die dem gleichen Geräteprofil zugewiesen sind. Es zeigt beispielsweise die Anzahl der Nicht-macOS-Geräte an.

    ![Anzeigen der Anzahl der Geräte, die dem Geräteprofil zugewiesen sind](./media/device-configuration-profile-graphical-chart.png)

    Das Grafikdiagramm unten zeigt die Anzahl der Benutzer an, die einem bestimmten Geräteprofil zugewiesen sind. Wenn das Gerätekonfigurationsprofil z.B. für macOS-Benutzer gilt, wird im Diagramm nur die Anzahl der macOS-Benutzer aufgelistet.

3. Wählen Sie den Kreis im oberen Grafikdiagramm aus. Der **Gerätestatus** wird geöffnet.

    Die dem Profil zugeordneten Geräte sind aufgelistet, und es wird angezeigt, ob das Profil erfolgreich bereitgestellt wurde. Beachten Sie auch, dass nur die Geräte der spezifischen Plattform (z.B. macOS) aufgelistet sind.

    Schließen Sie die **Gerätestatusdetails**.

4. Wählen Sie den Kreis im unteren Grafikdiagramm. Der **Benutzerstatus** wird angezeigt. 

    Die dem Profil zugeordneten Benutzer sind aufgelistet, und es wird angezeigt, ob das Profil erfolgreich bereitgestellt wurde. Beachten Sie auch, dass nur die Benutzer der spezifischen Plattform (z.B. macOS) aufgelistet sind.

    Schließen Sie die **Benutzerstatusdetails**.

5. Wählen Sie in der Liste **Profile** dann ein bestimmtes Profil aus. Sie können auch vorhandene Eigenschaften ändern:
  - **Eigenschaften**: Ändern Sie den Namen, oder aktualisieren Sie alle vorhandenen Einstellungen.
  - **Zuweisungen**: Schließen Sie Geräte für die Anwendung der Richtlinie ein oder davon aus. Wählen Sie **Ausgewählte Gruppen** aus, um bestimmte Gruppen auszuwählen.
  - **Gerätestatus**: Die dem Profil zugeordneten Geräte sind aufgelistet, und es wird angezeigt, ob das Profil erfolgreich bereitgestellt wurde. Sie können ein bestimmtes Gerät einschließlich der installierten Apps auswählen, um noch mehr Details zu erfahren.
  - **Benutzerstatus**: Listet die Namen der Benutzer mit Geräten auf, die diesem Profil unterliegen, und ob das Profil erfolgreich bereitgestellt wurde. Sie können einen bestimmten Benutzer auswählen, um noch mehr Informationen zu erhalten.
  - **Status pro Einstellung**: Filtert die Ausgabe durch Anzeige der einzelnen Einstellungen innerhalb des Profils, und zeigt an, ob die Einstellung erfolgreich angewendet wurde.

## <a name="view-conflicts"></a>Anzeigen von Konflikten

Unter **Geräte** > **Alle Geräte** können Sie alle Einstellungen anzeigen, die einen Konflikt verursachen. Wenn ein Konflikt vorliegt, werden Ihnen auch alle Konfigurationsprofile angezeigt, die diese Einstellung enthalten. Administratoren können dieses Feature verwenden, um das Problem zu beheben und alle Unstimmigkeiten mit diesem Profil zu lösen.

1. Wählen Sie in Intune **Geräte** > **Alle Geräte** aus, und wählen Sie dann ein vorhandenes Geräte in der Liste aus. Ein Endbenutzer kann den Gerätenamen über die Unternehmensportal-App abrufen.
2. Wählen Sie **Gerätekonfiguration** aus. Alle Konfigurationsrichtlinien, die für das Gerät gelten, sind aufgeführt.
3. Wählen Sie die Richtlinie aus. Es werden alle Einstellungen in dieser Richtlinie angezeigt, die für das Gerät relevant sind. Wenn ein Gerät den Zustand **Konflikt** besitzt, wählen Sie diese Zeile aus. Im Fenster, das neu geöffnet wird, werden alle Profile sowie die Profilnamen angezeigt, die über die Einstellung verfügen, die den Konflikt verursacht.

Da Sie jetzt die Konflikt verursachende Einstellung und die Richtlinien kennen, die diese Einstellung enthalten, dürfte es einfach sein, den Konflikt zu lösen. 

## <a name="next-steps"></a>Nächste Schritte
[Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md)  
[Häufig auftretende Probleme und Lösungen für Geräteprofile in Microsoft Intune](device-profile-troubleshoot.md)