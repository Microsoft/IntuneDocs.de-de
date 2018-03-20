---
title: "Installieren von Office 365 für macOS-Geräte mit Microsoft Intune"
titlesuffix: 
description: "Erfahren Sie, wie Sie Microsoft Intune verwenden können, um Office 365-Apps auf macOS-Geräten installieren zu können."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8de14184c4d23adc79d5b519fdcf272f0d7f6804
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>Zuweisen von Office 365 zu macOS-Geräten mit Microsoft Intune

Der Typ **Store-App** macht es Ihnen einfach, Office 365-Apps macOS-Geräten zuzuweisen. Dieser App-Typ ermöglicht Ihnen die Installation von Word, Excel, PowerPoint, Outlook und OneNote. Diese Apps sind auch im Lieferumfang von Microsoft AutoUpdate (MAU) enthalten, um die Apps sicherer und auf dem neuesten Stand zu halten. Die Apps, die als eine App in der Liste der Apps in der Intune-Konsole erscheinen sollen.


## <a name="before-you-start"></a>Vorbereitung

Bevor Sie damit beginnen, Office 365 macOS-Geräten hinzuzufügen, müssen Sie sich die folgenden Details bewusst machen:

- Auf Geräten, für die Sie diese Apps bereitstellen, muss macOS 10.10 oder höher ausgeführt werden.
- Intune unterstützt nur das Hinzufügen von Office-Apps, die in der Office 2016 für Mac-Suite enthalten sind.
- Wenn bei der Installation der App-Suite durch Intune Office-Apps geöffnet sind, verlieren Endbenutzer möglicherweise Daten aus nicht gespeicherten Dateien.

## <a name="create-and-configure-the-app-suite"></a>Erstellen und Konfigurieren der App-Suite

Fügen Sie Office 365 auf dem Blatt **Apps** hinzu.
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Überwachung + Verwaltung** > **Intune**.
3. Klicken Sie auf dem Blatt **Intune** auf die Option **Mobile Apps**.
4. Klicken Sie in der Workload **Mobile Apps** auf **Apps** im Abschnitt **Verwalten**. 
5. Klicken Sie auf **Hinzufügen**, um das Blatt **App hinzufügen** anzuzeigen.
6. Wählen Sie aus der Liste **App-Typ** in der Gruppe **Office 365 Suite** **macOS** aus.
7. Klicken Sie auf **App Suite Information** (Informationen zur App Suite), um Informationen zur App-Suite anzugeben. Diese Informationen helfen Ihnen dabei, die App-Suite in Intune zu identifizieren, und außerdem können Endbenutzer sie in der Unternehmensportal-App finden.
8.  Geben Sie die folgenden Informationen an:
    - **Sammlungsname:** Geben Sie den Namen der App-Sammlung ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle Sammlungsnamen eindeutig sind. Wenn ein Sammlungsname zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Sammlungsbeschreibung:** Geben Sie eine Beschreibung für die Sammlung ein.
    - **Herausgeber**: Als Herausgeber wird Microsoft angezeigt.
    - **Kategorie:** Wählen Sie eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Diese Einstellung erleichtert den Benutzern die Suche nach der App-Suite im Unternehmensportal.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Diese Einstellung zeigt die App-Suite auf der Hauptseite des Unternehmensportals hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL** (optional): Geben Sie eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen** (optional): Geben Sie eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Als Entwickler wird Microsoft angezeigt.
    - **Besitzer**: Als Besitzer wird Microsoft angezeigt.
    - **Anmerkungen** (optional): Geben Sie Anmerkungen ein, die dieser App zugewiesen werden sollen.
    - **Logo:** Das Office 365-Logo wird gemeinsam mit der App angezeigt, wenn der Benutzer das Unternehmensportal durchsucht.
9.  Klicken Sie auf dem Blatt **App-Informationen** auf **OK**.
10. Klicken Sie auf dem Blatt **App hinzufügen** auf **Hinzufügen**.
    Die Suite wird in der Liste der Apps als einzelnen Eintrag angezeigt.

## <a name="configure-app-assignments"></a>Konfigurieren von App-Zuweisungen

In diesem Schritt konfigurieren Sie Zuweisungen für die App-Suite. 

1. Wählen Sie aus der Liste mit Apps die App-Suite **Office 365** aus, um das Übersichtsblatt **Office 365** anzuzeigen.
2. Klicken Sie auf dem Blatt **Office 365** auf **Zuweisungen**.
3. Klicken Sie auf **Gruppe hinzufügen**, um eine Gruppe hinzuzufügen, die die App-Suite verwenden soll. Das Blatt **Gruppe hinzufügen** wird angezeigt.
3. Legen Sie den **Zuweisungstyp** auf **Erforderlich** fest.
4. Ordnen Sie die Suite den von Ihnen ausgewählten Gruppen zu. Weitere Informationen finden Sie unter [Zuweisen von Apps zu Gruppen mit Microsoft Intune](apps-deploy.md).

    >[!Note]
    > Wenn Sie die Office 365-App-Suite für bestimmte Gruppen erfordern, kann diese nicht über Microsoft Intune für diese Gruppen deinstalliert werden.

5. Klicken Sie auf dem Blatt **Zuweisen** auf **OK**.
6. Klicken Sie auf dem Blatt **Gruppe hinzufügen** auf **OK**.
7. Wählen Sie **Speichern**, um Ihre Zuweisungen zu committen.

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zum Hinzufügen von Office 365-Apps zu Windows 10-Geräten finden Sie unter [Wie Sie Office 365 ProPlus 2016-Apps mit Microsoft Intune](apps-add-office365.md) Windows 10-Geräten zuweisen.
- Informationen zum Ein- und Ausschließen von App-Zuweisungen für Gruppen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](apps-inc-exl-assignments.md).
