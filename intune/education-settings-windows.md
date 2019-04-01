---
title: Windows 10-Education-Einstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hier finden Sie eine Liste aller Education-Einstellungen für Windows 10-Geräte. Verwenden Sie diese Einstellungen in einem Gerätekonfigurationsprofil mit der „Take a Test“-App, wählen Sie aus, mit welcher Methode Benutzer oder Kursteilnehmer sich anmelden, überwachen Sie den Bildschirm während des Tests, und nehmen Sie Weiteres in Intune vor.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 206bc3276f3c175fe61852f235c722b835ad60b4
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57564855"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Konfigurieren der „Take a Test“-App für Windows 10-Geräte mit Intune

In diesem Artikel erhalten Sie Informationen zu allen Einstellungen für „Take a Test“-App in Microsoft Intune-Education, die Sie für Geräte auf Windows 10 und höher konfigurieren können. Mit dieser App können Kursteilnehmer sich bei einem Gerät anmelden und einen Test absolvieren.

Diese Einstellungen werden einem Gerätekonfigurationsprofil hinzugefügt und dann Ihren Geräten mit Microsoft Intune zugewiesen oder bereitgestellt.

[Konfigurieren von Einstellungen für Bildungseinrichtungen für Windows 10 in Microsoft Intune](education-settings-configure.md) bietet weitere Informationen zu dieser Funktion.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](education-settings-configure.md#create-a-device-profile)

## <a name="take-a-test-settings"></a>„Take a Test“-Einstellungen

- **Kontotyp**: Wählen Sie, wie Benutzer für den Test melden Sie sich. Folgende Optionen sind verfügbar:
  - Azure AD-Konto
  - Domänenkonto
  - Lokales Konto
- **Kontobenutzername**: Geben Sie den Benutzernamen des Kontos ein, das mit der Take a Test-App verwendet wird. Sie können die Konten im folgenden Format eingeben:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **Bewertungs-URL**: Geben Sie die URL des Tests ein, den Benutzer ausführen sollen. Weitere Informationen zum Abrufen der URL finden Sie in der [„Take a Test“-Dokumentation](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Bildschirmüberwachung**: Wählen Sie **Zulassen** aus, um die Bildschirmaktivität zu überwachen, während Benutzer einen Test ausführen. **Nicht konfiguriert** verhindert, dass Sie den Bildschirm während des Tests überwachen.
- **Textvorschlag**: Wählen Sie **Zulassen** aus, damit Testteilnehmern Textvorschläge angezeigt werden. **Nicht konfiguriert** blockiert Textvorschläge, während Benutzer einen Test ausführen.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber vielleicht noch keine Aktionen durch. Denken Sie daran, das [Profil zuzuweisen](device-profile-assign.md) und [seinen Status zu überwachen](device-profile-monitor.md).
