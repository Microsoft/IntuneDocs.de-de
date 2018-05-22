---
title: Erste Schritte mit Apps in Microsoft Intune
titlesuffix: ''
description: Suchen Sie Apps, und fügen Sie sie zu Geräten hinzu, um Ihren Mitarbeitern die Arbeit zu erleichtern.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5d99812c57596e10d0cdfa2c0f4504f8a6ac583c
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>Erste Schritte beim Hinzufügen von Apps in Microsoft Intune

Bevor Sie Apps zuweisen, überwachen, konfigurieren oder schützen können, müssen Sie sie zu Intune hinzufügen. Intune unterstützt mehrere verschiedene App-Typen. Zudem unterscheiden sich die verfügbaren Optionen bei den einzelnen App-Typen.

Mit Intune können Sie folgende App-Typen zu Ihren Unternehmensgeräten hinzufügen und zuweisen:
- **Apps aus dem Store**: Für Geräte, für die zusätzliche mobile Anwendungsverwaltung für im App-Store verfügbare Apps erforderlich ist.
- **Interne (branchenspezifische) Apps**: Hochladen einer heruntergeladenen Datei auf das Gerät Ihres Benutzers.
- **Integrierte Apps**: Zuweisen geordneter verwalteter Apps, wie z.B. Office 365-Apps, zu iOS- und Android-Geräten.
- **Apps im Web**: Intune erstellt eine Verknüpfung für die Web-App auf dem Startbildschirm des Geräts.

## <a name="how-do-i-assign-a-public-store-app"></a>Wie weise ich eine öffentliche Store-App zu?

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie auf **Mobile Apps** und dann auf **Apps**.
4. Klicken Sie auf **Hinzufügen**, und wählen Sie **iOS** als **App-Typ** aus.
5. Wählen Sie **App auswählen** aus, um den Bereich **App Store durchsuchen** anzuzeigen.
6. Suchen Sie über das Textfeld nach einer App, die Sie dem Gerät zuweisen können. Wählen Sie die App aus, und klicken Sie dann auf **Auswählen**.
7. Klicken Sie im Bereich **App hinzufügen** auf **App-Information**, und stellen Sie sicher, dass alle App-Informationen aufgefüllt wurden. Sie können andere optionale Details hinzufügen, um diese App zu organisieren, wie z.B. **Besitzer**, **Anmerkungen**, **Entwickler** und **URL zu den Datenschutzbestimmungen** für die Datenschutzrichtlinie Ihres Unternehmens.
8. Achten Sie darauf, dass Sie **Ja** für **Diese App als ausgewählte App im Unternehmensportal anzeigen** ausgewählt haben, und klicken Sie dann auf **OK**.
9. Klicken Sie im Bereich **App hinzufügen** auf **Hinzufügen**, um die App hinzuzufügen. Damit werden Sie zur **Übersicht** der App weitergeleitet. Klicken Sie auf **Zuweisungen** und dann auf **Gruppe hinzufügen**, um sie Ihrer Testgruppe hinzuzufügen. Machen Sie die App zum Herunterladen **verfügbar**. Dann sollte die App als **Empfohlene App** auf Ihrem Testgerät angezeigt werden.


- [Zuweisen von Apps zu Gruppen](apps-deploy.md)

## <a name="learn-more"></a>Erfahren Sie mehr

* [Was ist die Microsoft Intune App-Verwaltung?](app-management.md)
* [Übersicht über den App-Lebenszyklus](app-lifecycle.md)
* [Was sind App-Schutzrichtlinien?](app-protection-policy.md)
