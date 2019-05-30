---
title: Installieren von Office 365 für macOS-Geräte mit Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie Microsoft Intune verwenden können, um Office 365-Apps auf macOS-Geräten installieren zu können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 618557c129b693ad035dd82c823db43dcca2ee4d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66049461"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Zuweisen von Office 365 zu macOS-Geräten mit Microsoft Intune

Dieser App-Typ macht es Ihnen einfach, Office 365 2016-Apps macOS-Geräten zuzuweisen. Dieser App-Typ ermöglicht Ihnen die Installation von Word, Excel, PowerPoint, Outlook und OneNote. Diese Apps sind auch im Lieferumfang von Microsoft AutoUpdate (MAU) enthalten, um die Apps sicherer und auf dem neuesten Stand zu halten. Die gewünschten Apps werden in der Intune-Konsole als einzelne App in der App-Liste angezeigt.


## <a name="before-you-start"></a>Vorbereitung

Bevor Sie damit beginnen, macOS-Geräten Office 365 hinzuzufügen, sollten Sie sich Folgendes bewusst machen:

- Auf Geräten, für die Sie diese Apps bereitstellen, muss macOS 10.10 oder höher ausgeführt werden.
- Intune unterstützt nur das Hinzufügen von Office-Apps, die in der Office 2016 für Mac-Suite enthalten sind.
- Wenn Office-Apps geöffnet sind, wenn Intune die App-Suite installiert, verlieren Benutzer möglicherweise Daten aus nicht gespeicherten Dateien.

## <a name="create-and-configure-the-app-suite"></a>Erstellen und Konfigurieren der App-Suite

Fügen Sie Office 365 aus dem Bereich **Apps** hinzu.
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Überwachung + Verwaltung** > **Intune**.
3. Wählen Sie im Bereich **Intune** **Client-Apps** aus.
4. Wählen Sie im Workloadbereich **Client-Apps** unter **Verwalten** die Option **Apps** aus. 
5. Wählen Sie **Hinzufügen** aus.
6. Wählen Sie aus der Liste **App-Typ** in der Gruppe **Office 365 Suite** **macOS** aus.
7. Klicken Sie auf **Informationen zur App Suite**, um Informationen zur App-Suite abzurufen.  
    Diese Informationen helfen Ihnen dabei, die App-Suite in Intune zu identifizieren. Außerdem können Benutzer sie im Unternehmensportal leichter finden.
8. Geben Sie die folgenden Informationen ein:
    - **Name der Suite**: Geben Sie den Namen der App-Suite so ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle Suitenamen eindeutig sind. Wenn ein Sammlungsname zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung der Suite**: Geben Sie eine Beschreibung der App-Suite ein.
    - **Herausgeber**: Als Herausgeber wird Microsoft angezeigt.
    - **Kategorie**: Wählen Sie eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Diese Einstellung erleichtert den Benutzern die Suche nach der App-Suite im Unternehmensportal.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Wählen Sie diese Option, um die App-Suite auf der Hauptseite des Unternehmensportals hervorgehoben anzuzeigen, wenn die Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Als Entwickler wird Microsoft angezeigt.
    - **Besitzer**: Als Besitzer wird Microsoft angezeigt.
    - **Anmerkungen**: Geben Sie optional Hinweise zu dieser App ein.
    - **Logo**: Das Office 365-Logo wird gemeinsam mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
9. Wählen Sie **OK** aus.
10. Klicken Sie anschließend im Bereich **App hinzufügen** auf **Hinzufügen**.  
    Die Suite wird in der Liste der Apps als einzelnen Eintrag angezeigt.

## <a name="configure-app-assignments"></a>Konfigurieren von App-Zuweisungen

In diesem Schritt konfigurieren Sie Zuweisungen für die App-Suite. 

1. Wählen Sie aus der Liste mit Apps die App-Suite **Office 365** aus, um den Übersichtsbereich **Office 365** anzuzeigen.
2. Wählen Sie im Bereich **Office 365** **Assignments** aus.
3. Wählen Sie **Gruppe hinzufügen** aus, um eine Gruppe hinzuzufügen, die die App-Suite verwenden wird.  
    Der Bereich **Gruppe hinzufügen** wird angezeigt.
4. Legen Sie den **Zuweisungstyp** auf **Erforderlich** oder **Verfügbar** fest.
5. Ordnen Sie die Suite den von Ihnen ausgewählten Gruppen zu. Weitere Informationen finden Sie unter [Zuweisen von Apps zu Gruppen mit Microsoft Intune](apps-deploy.md).

    >[!Note]
    > Sie können die Office 365-App nicht über Intune deinstallieren.

5. Wählen Sie im Bereich **Zuweisen** **OK** aus.
6. Wählen Sie im Bereich **Gruppe hinzufügen** die Option **OK** aus.
7. Wählen Sie **Speichern** aus, um Ihre Zuweisungen zu committen.

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zum Hinzufügen von Office 365-Apps zu Windows 10-Geräten finden Sie unter [Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune](apps-add-office365.md).
- Informationen zum Ein- und Ausschließen von App-Zuweisungen für Gruppen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](apps-inc-exl-assignments.md).
