---
title: Erste Schritte mit Apps in Microsoft Intune
titlesuffix: 
description: "Suchen Sie Apps, und fügen Sie sie zu Geräten hinzu, um Ihren Mitarbeitern die Arbeit zu erleichtern."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 3/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0185eebbe436da73e1920d7cd834f0897a143894
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>Erste Schritte beim Hinzufügen von Apps in Microsoft Intune

Bevor Sie Apps zuweisen, überwachen, konfigurieren oder schützen können, müssen Sie sie zu Intune hinzufügen. Intune unterstützt mehrere verschiedene App-Typen. Zudem unterscheiden sich die verfügbaren Optionen bei den einzelnen App-Typen.

Mit Intune können Sie folgende App-Typen zu Ihren Unternehmensgeräten hinzufügen und zuweisen:
- **Apps aus dem Store**: Für Geräte, für die zusätzliche mobile Anwendungsverwaltung für im App-Store verfügbare Apps erforderlich ist.
- **Interne (branchenspezifische) Apps**: Hochladen einer heruntergeladenen Datei auf das Gerät Ihres Benutzers.
- **Integrierte Apps**: Zuweisen geordneter verwalteter Apps, wie z.B. Office 365-Apps, zu iOS- und Android-Geräten. 
- **Apps im Web**: Intune erstellt eine Verknüpfung für die Web-App auf dem Startbildschirm des Geräts.

## <a name="how-do-i-assign-a-public-store-app"></a>Wie weise ich eine öffentliche Store-App zu?

Das folgende Beispiel führt Sie schrittweise durch die Vorgehensweise beim Hinzufügen einer iOS-App in Microsoft Intune.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie auf dem Blatt **Intune** die Option **Mobile Apps** aus.
4. Klicken Sie in der Workload **Mobile Apps** im Abschnitt **Verwalten** auf **Apps**.
5. Wählen Sie rechts von dem Bereich **Apps** die Option **Hinzufügen** aus.
6. Wählen Sie in der Liste **App-Typ** unter den verfügbaren Typen der **Store-Apps** die Option **iOS** aus.
6. Wählen Sie **Search the App Store** (App Store durchsuchen) aus.
7. Wählen Sie auf dem Blatt **Search the App Store** (App Store durchsuchen) das Gebietsschema des App Store aus.
8. Geben Sie den Namen (oder einen Teil des Namens) in das Suchfeld ein. Intune durchsucht den Store und gibt eine Liste mit relevanten Ergebnissen zurück.
9. Wählen Sie die gewünschte App aus der Liste aus, und klicken Sie anschließend auf **Auswählen**.
10. Wählen Sie **App-Informationen** aus, um die App-Informationen zu konfigurieren.
11. (Optional) Sie können andere Details hinzufügen, um diese App zu organisieren, wie z.B. **Besitzer**, **Anmerkungen**, **Entwickler** und **URL zu den Datenschutzbestimmungen** (für die Datenschutzrichtlinie Ihres Unternehmens).
12. Wählen Sie bei der Option **Display this as a featured app in the Company Portal** (Diese App als ausgewählte App im Unternehmensportal anzeigen) den Eintrag **Ja** aus. 
13. Klicken Sie auf **OK**, nachdem Sie alle erforderlichen App-Informationen hinzugefügt haben.
14. Klicken Sie auf dem Blatt **App hinzufügen** auf **Hinzufügen**. Dadurch gelangen Sie zu der **Übersicht** dieser App. 

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie eine App zu Intune hinzugefügt haben, können Sie die Mitarbeitergruppen zuweisen, welche die App auf ihren Geräten verwenden können.

- [Zuweisen von Apps zu Gruppen](apps-deploy.md)
- 
## <a name="learn-more"></a>Erfahren Sie mehr

* [Was ist die Microsoft Intune App-Verwaltung?](app-management.md)
* [Übersicht über den App-Lebenszyklus](app-lifecycle.md)
* [Was sind App-Schutzrichtlinien?](app-protection-policy.md)
