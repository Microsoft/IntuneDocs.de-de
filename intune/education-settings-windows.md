---
title: Windows 10-Education-Einstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hier finden Sie eine Liste aller Education-Einstellungen für Windows 10-Geräte. Verwenden Sie diese Einstellungen in einem Gerätekonfigurationsprofil mit der „Take a Test“-App, wählen Sie aus, mit welcher Methode Benutzer oder Kursteilnehmer sich anmelden, überwachen Sie den Bildschirm während des Tests, und nehmen Sie Weiteres in Intune vor.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ae26d35a50ffd2b5b40f262ddebeab8d53d87223
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55846688"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Konfigurieren der „Take a Test“-App für Windows 10-Geräte mit Intune

In diesem Artikel erhalten Sie Informationen zu allen Einstellungen für „Take a Test“-App in Microsoft Intune-Education, die Sie für Geräte auf Windows 10 und höher konfigurieren können. Mit dieser App können Kursteilnehmer sich bei einem Gerät anmelden und einen Test absolvieren.

Diese Einstellungen werden einem Gerätekonfigurationsprofil hinzugefügt und dann Ihren Geräten mit Microsoft Intune zugewiesen oder bereitgestellt.

[Konfigurieren von Einstellungen für Bildungseinrichtungen für Windows 10 in Microsoft Intune](education-settings-configure.md) bietet weitere Informationen zu dieser Funktion.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](education-settings-configure.md#create-a-device-profile)

## <a name="take-a-test-settings"></a>„Take a Test“-Einstellungen

- **Kontotyp**: Wählen Sie aus, wie Benutzer sich für den Test anmelden können. Folgende Optionen sind verfügbar:
  - Azure AD-Konto
  - Domänenkonto
  - Lokales Konto
- **Kontobenutzername**: Geben Sie den Benutzernamen des Kontos ein, das mit der „Take a Test“-App verwendet wird. Sie können die Konten im folgenden Format eingeben:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **Bewertungs-URL**: Geben Sie die URL des Tests an, den Benutzer ausführen sollen. Weitere Informationen zum Abrufen der URL finden Sie in der [„Take a Test“-Dokumentation](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Bildschirmüberwachung**: Wählen Sie **Zulassen** aus, um die Bildschirmaktivität zu überwachen, während Benutzer einen Test ausführen. **Nicht konfiguriert** verhindert, dass Sie den Bildschirm während des Tests überwachen.
- **Textvorschlag**: Wählen Sie **Zulassen** aus, damit Testteilnehmer Textvorschläge sehen können. **Nicht konfiguriert** blockiert Textvorschläge, während Benutzer einen Test ausführen.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber vielleicht noch keine Aktionen durch. Denken Sie daran, das [Profil zuzuweisen](device-profile-assign.md) und [seinen Status zu überwachen](device-profile-monitor.md).
