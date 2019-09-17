---
title: Windows 10-Education-Einstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hier finden Sie eine Liste aller Education-Einstellungen für Windows 10-Geräte. Verwenden Sie diese Einstellungen in einem Gerätekonfigurationsprofil mit der „Take a Test“-App, wählen Sie aus, mit welcher Methode Benutzer oder Kursteilnehmer sich anmelden, überwachen Sie den Bildschirm während des Tests, und nehmen Sie Weiteres in Intune vor.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: kakyker
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 07d3488d509339fc48eb8449b12725b757775eb5
ms.sourcegitcommit: 98f2597eec28c6096985d5a1acae72430c2afb1a
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70877978"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Konfigurieren der „Take a Test“-App für Windows 10-Geräte mit Intune

Mit der App "Take a Test" können Sie Online Tests auf den Windows 10-Geräten Ihres Classroom sicher verwalten. Zum Einrichten einer Test-App müssen Sie in InTune ein Geräte Konfigurations Profil erstellen und die Einstellungen für die sichere Bewertung konfigurieren. In diesem Artikel werden die Einstellungen beschrieben, die Sie für das Erstellen einer Test-App finden. 

Nachdem Sie das Profil konfiguriert haben, können Sie es ihren Studenten zuweisen und bereitstellen. 

[Konfigurieren von Einstellungen für Bildungseinrichtungen für Windows 10 in Microsoft Intune](education-settings-configure.md) bietet weitere Informationen zu dieser Funktion.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](education-settings-configure.md#create-a-device-profile)

## <a name="take-a-test-settings"></a>„Take a Test“-Einstellungen
Nachdem Sie ein Geräte Konfigurations Profil erstellt haben, wechseln Sie zu **Profiltyp** , und wählen Sie dann **sichere Bewertung (Education)** aus. Sie finden die folgenden Test-App-Einstellungen. 


- **Kontotyp:** Wählen Sie aus, wie sich Benutzer für den Test anmelden. Folgende Optionen sind verfügbar:
  - Azure AD-Konto
  - Domänenkonto
  - Lokales Konto
  - Lokales Gastkonto: nur auf Geräten mit Windows 10, Version 1903 und höher verfügbar.    
- **Kontobenutzername**: Geben Sie den Benutzernamen des Kontos ein, das mit der Take a Test-App verwendet wird. Sie können die Konten im folgenden Format eingeben:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **Kontoname**: Geben Sie zum Einrichten eines lokalen gastkontotyps den Namen des Kontos ein, das mit der APP zum Erstellen einer Test-App verwendet wird. Der Kontoname wird als Kachel auf dem Anmeldebildschirm angezeigt. Schüler/Studenten klicken auf die Kachel, um den Test zu starten.  
- **Bewertungs-URL**: Geben Sie die URL des Tests ein, den Benutzer ausführen sollen. Weitere Informationen zum Abrufen der URL finden Sie in der [„Take a Test“-Dokumentation](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Druckerverbindung**: Wählen Sie **erforderlich** aus, um nur den Zugriff auf das Erstellen einer Test-App von Geräten zuzulassen, die mit einem Drucker verbunden sind. Mit dieser Einstellung wird die Schaltfläche Drucken der APP auch für Testteilnehmer verfügbar. **Nicht konfiguriert** ermöglicht Studenten, von Geräten, die nicht mit einem Drucker verbunden sind, auf die APP zuzugreifen.  
- **Bildschirmüberwachung**: Wählen Sie **Zulassen** aus, um die Bildschirmaktivität zu überwachen, während Benutzer einen Test ausführen. **Nicht konfiguriert** verhindert, dass Sie den Bildschirm während des Tests überwachen.
- **Textvorschläge**: Wählen Sie **Zulassen** aus, damit Testteilnehmern Textvorschläge angezeigt werden. **Nicht konfiguriert** blockiert Textvorschläge, während Benutzer einen Test ausführen.

## <a name="next-steps"></a>Nächste Schritte

Denken Sie daran, das [Profil zuzuweisen](device-profile-assign.md) und [seinen Status zu überwachen](device-profile-monitor.md).
