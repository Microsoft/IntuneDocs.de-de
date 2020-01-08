---
title: Anzeigen von Geräteprofilen mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Zeigen Sie die Gerätekonfigurationsprofil-Details in Microsoft Intune an, und verwalten Sie sie, zeigen Sie ein grafisches Diagramm der Anzahl der Geräte an, die einem Profil zugewiesen wurden, und zeigen Sie an, welchen Geräten Profile zugewiesen bzw. für welche Geräte sie bereitgestellt wurden. Es können auch Probleme in Profilen behoben werden, die in Konflikt stehende Einstellungen beinhalten.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 25983117864f44b8131fdc49e60b7d24048da9fe
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206651"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Überwachen von Geräteprofilen in Microsoft Intune



Intune enthält einige Funktionen, die Ihnen bei der Überwachung und Verwaltung Ihrer Gerätekonfigurationsprofile helfen. Sie können z.B. den Status eines Profils überprüfen, anzeigen, welche Geräte zugewiesen sind, und die Eigenschaften eines Profils aktualisieren.

## <a name="view-existing-profiles"></a>Anzeigen von vorhandenen Profilen

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** aus.

Alle Ihre vorhandenen Profile werden aufgelistet und beinhalten Details wie z.B. die Plattform und ob das Profil einem Gerät zugewiesen ist.

## <a name="view-details-on-a-profile"></a>Anzeigen von Details zu einem Profil

Nachdem Sie Ihr Geräteprofil erstellt haben, bietet Intune grafische Diagramme. Diese Diagramme zeigen den Status eines Profils an, etwa ob es erfolgreich Geräten zugewiesen wurde, oder ob das Profil einen Konflikt aufweist.

1. Wählen Sie ein vorhandenes Profil aus. Wählen Sie z.B. ein macOS-Profil aus.
2. Wählen Sie die Registerkarte **Übersicht** aus.

    Das Grafikdiagramm oben zeigt die Anzahl der Geräte an, die dem Geräteprofil zugewiesen sind. Wenn das Gerätekonfigurationsprofil z.B. für macOS-Geräte gilt, wird im Diagramm nur die Anzahl der macOS-Geräte aufgelistet.

    Es zeigt auch die Anzahl der Geräte anderer Plattformen an, die dem gleichen Geräteprofil zugewiesen sind. Es zeigt beispielsweise die Anzahl der Nicht-macOS-Geräte an.

    ![Anzeigen der Anzahl der Geräte, die dem Geräteprofil zugewiesen sind](./media/device-profile-monitor/device-configuration-profile-graphical-chart.png)

    Das Grafikdiagramm oben zeigt die Anzahl der Benutzer an, die dem Geräteprofil zugewiesen sind. Wenn das Gerätekonfigurationsprofil z.B. für macOS-Benutzer gilt, wird im Diagramm nur die Anzahl der macOS-Benutzer aufgelistet.

3. Wählen Sie den Kreis im oberen Grafikdiagramm aus. Der **Gerätestatus** wird geöffnet.

    Die dem Profil zugeordneten Geräte sind aufgelistet, und es wird angezeigt, ob das Profil erfolgreich bereitgestellt wurde. Beachten Sie auch, dass nur die Geräte der spezifischen Plattform (z.B. macOS) aufgelistet sind.

    Schließen Sie die **Gerätestatusdetails**.

4. Wählen Sie den Kreis im unteren Grafikdiagramm. Der **Benutzerstatus** wird angezeigt. 

    Die dem Profil zugeordneten Benutzer sind aufgelistet, und es wird angezeigt, ob das Profil erfolgreich bereitgestellt wurde. Beachten Sie auch, dass nur die Benutzer der spezifischen Plattform (z.B. macOS) aufgelistet sind.

    Schließen Sie die **Benutzerstatusdetails**.

5. Wählen Sie in der Liste **Profile** dann ein bestimmtes Profil aus. Sie können auch vorhandene Eigenschaften ändern:
    - **Eigenschaften:** Ändern Sie den Namen, oder aktualisieren Sie alle vorhandenen Einstellungen.
    - **Zuweisungen:** Schließen Sie Geräte für die Anwendung der Richtlinie ein oder davon aus. Wählen Sie **Ausgewählte Gruppen** aus, um bestimmte Gruppen auszuwählen.
    - **Gerätestatus:** Die dem Profil zugeordneten Geräte sind aufgelistet, und es wird angezeigt, ob das Profil erfolgreich bereitgestellt wurde. Sie können ein bestimmtes Gerät einschließlich der installierten Apps auswählen, um noch mehr Details zu erfahren.
    - **Benutzerstatus:** Listet die Namen der Benutzer mit Geräten auf, die von diesem Profil beeinflusst sind, und ob das Profil erfolgreich bereitgestellt wurde. Sie können einen bestimmten Benutzer auswählen, um noch mehr Informationen zu erhalten.
    - **Einstellungsspezifischer Status:** Filtert die Ausgabe durch Anzeigen der einzelnen Einstellungen innerhalb des Profils, und zeigt an, ob die Einstellung erfolgreich angewendet wurde.

## <a name="view-conflicts"></a>Anzeigen von Konflikten

Unter **Geräte** > **Alle Geräte** können Sie alle Einstellungen anzeigen, die einen Konflikt verursachen. Wenn ein Konflikt vorliegt, werden Ihnen auch alle Konfigurationsprofile angezeigt, die diese Einstellung enthalten. Administratoren können dieses Feature verwenden, um das Problem zu beheben und alle Unstimmigkeiten mit diesem Profil zu lösen.

1. Wählen Sie in Intune **Geräte** > **Alle Geräte** aus, und wählen Sie dann ein vorhandenes Geräte in der Liste aus. Ein Endbenutzer kann den Gerätenamen über die Unternehmensportal-App abrufen.
2. Wählen Sie **Gerätekonfiguration** aus. Alle Konfigurationsrichtlinien, die für das Gerät gelten, sind aufgeführt.
3. Wählen Sie die Richtlinie aus. Es werden alle Einstellungen in dieser Richtlinie angezeigt, die für das Gerät relevant sind. Wenn ein Gerät den Zustand **Konflikt** besitzt, wählen Sie diese Zeile aus. Im Fenster, das neu geöffnet wird, werden alle Profile sowie die Profilnamen angezeigt, die über die Einstellung verfügen, die den Konflikt verursacht.

Da Sie jetzt die Konflikt verursachende Einstellung und die Richtlinien kennen, die diese Einstellung enthalten, dürfte es einfach sein, den Konflikt zu lösen. 

## <a name="device-firmware-configuration-interface-profile-reporting"></a>Bericht der DFCI-Profile (Device Firmware Configuration Interface; Schnittstelle zur Konfiguration der Gerätefirmware)

> [!WARNING]
> Die Überwachung der DFCI-Profile wird derzeit erstellt. Während sich DFCI in der öffentlichen Vorschau befindet, können Überwachungsdaten fehlen oder unvollständig sein.

DFCI-Profile werden wie andere Gerätekonfigurationsprofile pro Einstellung gemeldet. Abhängig von der Unterstützung des Herstellers für DFCI können einige Einstellungen nicht angewendet werden.

Mit Ihren DFCI-Profileinstellungen können Sie die folgenden Zustände sehen:

- **Konform**: Dieser Zustand zeigt an, wenn ein Einstellungswert im Profil mit der Einstellung am Gerät übereinstimmt. Dies kann in den folgenden Szenarios geschehen:

  - Das DFCI-Profil hat die Einstellung im Profil erfolgreich konfiguriert.
  - Das Gerät verfügt nicht über die von der Einstellung gesteuerte Hardwarefunktion, und die Profileinstellung ist **Deaktiviert**.
  - UEFI erlaubt es DFCI nicht, die Funktion zu deaktivieren, und die Profileinstellung ist **Aktiviert**.
  - Dem Gerät fehlt die Hardware, um die Funktion zu deaktivieren, und die Profileinstellung ist **Aktiviert**.

- **Nicht zutreffend:** Dieser Zustand zeigt an, wenn ein Einstellungswert im Profil **Aktiviert** ist und die übereinstimmende Einstellung am Gerät nicht gefunden wird. Dieser Zustand kann auftreten, wenn die Gerätehardware nicht über die Funktion verfügt.

- **Nicht konform:** Dieser Zustand zeigt an, wenn ein Einstellungswert im Profil mit der Einstellung am Gerät nicht übereinstimmt. Dies kann in den folgenden Szenarios geschehen:

  - UEFI erlaubt es DFCI nicht, eine Einstellung zu deaktivieren, und die Profileinstellung ist **Deaktiviert**.
  - Dem Gerät fehlt die Hardware, um die Funktion zu deaktivieren, und die Profileinstellung ist **Deaktiviert**.
  - Das Gerät verfügt nicht über die neueste DFCI-Firmwareversion.
  - DFCI wurde deaktiviert, bevor es in Intune über ein lokales „Deaktivieren“-Steuerelement im UEFI-Menü registriert wurde.
  - Das Gerät wurde außerhalb der Autopilot-Registrierung für Intune angemeldet.
  - Das Gerät wurde nicht von einem Microsoft CSP auf dem Autopiloten registriert oder direkt vom OEM registriert.

## <a name="next-steps"></a>Nächste Schritte

[Häufige Fragen, Probleme und entsprechende Behebungen mit Geräterichtlinien und -profilen in Microsoft Intune](device-profile-troubleshoot.md)  
[Richtlinien und Profile zur Problembehandlung in Intune](troubleshoot-policies-in-microsoft-intune.md)
