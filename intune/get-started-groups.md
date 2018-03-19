---
title: Erstellen einer Gruppe in Microsoft Intune
titleSuffix: 
description: "Organisieren Sie Benutzer in Gruppen, um die Richtlinien und Apps leichter zu verwalten, auf die sie zugreifen können."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e052f7c8d5742859d009816473fe97a98c499b17
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="create-a-group-to-manage-your-users-and-data-access"></a>Erstellen Sie eine Gruppe zur Verwaltung Ihrer Benutzer und Ihres Datenzugriffs

Mit Gruppen können Sie Benutzer verwalten und den Zugriff Ihrer Mitarbeiter auf Ihre Unternehmensressourcen steuern. Diese Ressourcen können Teil Ihres Verzeichnisses oder externe Ressourcen wie SaaS-Apps oder SharePoint-Websites sein.

Microsoft Intune verwendet Azure Active Directory (Azure AD) zum Verwalten des Zugriffs auf Unternehmensressourcen. Dieser Zugriff wird mithilfe von Rollen im Verzeichnis gesteuert. Intune verwaltet dann diesen Zugriff für mobile Geräte, wodurch Mitgliedern dieser Gruppe der Zugriff auf Ressourcen gewährt wird.

## <a name="how-do-i-create-a-group"></a>Wie erstelle ich eine Gruppe?

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Suchen Sie über **Ressourcen durchsuchen** nach **Intune**.
3. Wenn Sie das Blatt **Microsoft Intune** geöffnet haben, wählen Sie **Gruppen** aus.
4. Wählen Sie auf dem Blatt **Users and Groups – All Groups** (Benutzer und Gruppen – Alle Gruppen) die Option **Neue Gruppe** aus.
5. Fügen Sie auf dem Blatt **Gruppe** einen **Namen** und eine **Beschreibung** für die Gruppe hinzu.
6. Legen Sie den **Mitgliedschaftstyp** auf **Zugewiesen** fest. Für die Testgruppe sollten Sie **Office-Features nicht aktivieren**.
7. Klicken Sie auf **Erstellen**.

Wenn Sie eine Gruppe erfolgreich erstellt haben, sollte sie in der Liste **Alle Gruppen** angezeigt werden. Versuchen Sie andernfalls, eine andere Gruppe zu erstellen.

## <a name="next-steps"></a>Nächste Schritte

[Erste Schritte mit Richtlinien:](get-started-policies.md) Erstellen Sie Richtlinien, um zu verhindern, dass Benutzer nicht autorisierte Aktionen mit ihren Geräten vornehmen.

## <a name="learn-more"></a>Erfahren Sie mehr

* [Hinzufügen von Gruppen in Intune](groups-add.md)
* [Verwalten des Zugriffs auf Ressourcen mit Azure Active Directory-Gruppen](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
