---
title: Hinzufügen von integrierten Apps zu mobilen Geräten mit Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie Intune verwenden können, um integrierte Apps einfacher auf mobilen Geräten installieren zu können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96cd4997029c15396db91e9866bbb387c20f1044
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414452"
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>Hinzufügen von integrierten Apps zu Microsoft Intune

Der *integrierte* App-Typ erleichtert Ihnen das Zuweisen geordneter verwalteter Apps, z. B. Office 365-Apps, zu iOS-/iPadOS- und Android-Geräten. Sie können bestimmte Apps für diesen App-Typ zuweisen, z.B. Excel, OneDrive, Outlook oder Skype. Nach dem Hinzufügen einer App wird als App-Typ entweder *Integrierte iOS-App* oder *Integrierte Android-App* angezeigt. Mithilfe des integrierten App-Typs können Sie wählen, welche dieser Apps Sie für Gerätebenutzer veröffentlichen möchten.

In früheren Versionen der Intune-Konsole stellte Intune mehrere standardmäßig verwaltete Office 365-Apps wie Outlook und OneDrive bereit. Diese verwalteten Apps wurden mit den App-Typen *Verwaltete iOS Store-App* oder *Verwaltete Android-App* bezeichnet. Es wird empfohlen, anstelle dieser App-Typen den integrierten App-Typen zu verwenden. Mit dem integrierten App-Typen können Sie außerdem Office 365-Apps flexibler bearbeiten und löschen.

>[!NOTE]
>Als *Verwaltete iOS Store-App* oder *Verwaltete Android-App* bezeichnete standardmäßige Office 365-Apps werden aus der Liste der Apps entfernt, wenn alle Zuweisungen gelöscht sind.

## <a name="add-a-built-in-app"></a>Hinzufügen einer integrierten App

So fügen Sie eine integrierte App Ihren verfügbaren Apps in Microsoft Intune hinzu
1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus.
3. Wählen Sie im Bereich **App-Typ auswählen** aus den verfügbaren **Store-App**-Typen die Option **Integrierte App** aus.
4. Klicken Sie auf **Auswählen**. Die **App hinzufügen**-Schritte werden angezeigt.
5. Klicken Sie auf der Seite **Integrierte Apps auswählen** auf **App auswählen**, um die einzuschließenden Apps auszuwählen.
6. Wählen Sie die integrierten Apps aus, die Sie einschließen möchten. 
7. Nachdem Sie die Apps ausgewählt haben, klicken Sie im Bereich **Integrierte Apps auswählen** auf **Auswählen**.
8. Klicken Sie auf **Weiter**, um die Seite **Bereichsmarkierungen** anzuzeigen.
9. Klicken Sie auf **Bereichstags auswählen**, um optional Bereichsmarkierungen für die App hinzuzufügen. Weitere Informationen dazu finden Sie unter [Verwenden der rollenbasierten Zugriffssteuerung und Bereichsmarkierungen für verteilte IT](~/fundamentals/scope-tags.md).
10. Klicken Sie auf **Weiter**, um die Seite **Zuweisungen** anzuzeigen.
11. Wählen Sie die Gruppenzuweisungen für die App aus. Weitere Informationen finden Sie unter [Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten](~/fundamentals/groups-add.md). 
12. Klicken Sie auf **Weiter**, um die Seite **Überprüfen + erstellen** anzuzeigen. Überprüfen Sie die Werte und Einstellungen, die Sie für die App eingegeben haben.
13. Klicken Sie abschließend auf **Erstellen**, um Intune die App hinzuzufügen.

    Die von Ihnen erstellte App wird auf dem Blatt **Übersicht** angezeigt.

## <a name="configure-app-information"></a>Konfigurieren von App-Informationen

Sie können die Informationen zu der integrierten App ändern. Diese Informationen helfen Ihnen, die App in Intune zu identifizieren, und Endbenutzer können sie leichter im Unternehmensportal finden.
1. Wählen Sie **Apps** > **Alle Apps** und dann die integrierte App aus, die Sie ändern möchten.  
   Es wird ein Bereich für die integrierte App angezeigt.
2. Wählen Sie **Eigenschaften** aus.
3. Wählen Sie neben **App-Information** die Option **Bearbeiten** aus.
4. Im Bereich **App-Informationen** können Sie die folgenden Informationen ändern:
    - **Name:** Geben Sie den Namen der integrierten App ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung der App ein. 
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.
    - **Kategorie**: Wählen Sie optional mindestens eine der Kategorien für integrierte Apps aus. Die Einstellung dieser Option erleichtert Benutzern, die App im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Präsentieren Sie die App herausgehoben auf der Hauptseite des Unternehmensportals, wenn die Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer**: Geben Sie optional einen Namen für den Besitzer dieser App ein, (z. B. *Personalabteilung*).
    - **Anmerkungen**: Geben Sie Hinweise zu dieser App ein.
    - **Symbol hochladen:** Laden Sie ein Symbol hoch, das mit der App angezeigt wird, wenn Benutzer das Unternehmensportal durchsuchen.
5. Klicken Sie auf **Überprüfen + speichern**, um die Seite **Überprüfen + erstellen** anzuzeigen. Überprüfen Sie die Werte und Einstellungen, die Sie für die App eingegeben haben.
13. Klicken Sie abschließend auf **Speichern**, um die App in Intune zu aktualisieren.

    Die von Ihnen erstellte App wird auf dem Blatt **Übersicht** angezeigt.

## <a name="next-steps"></a>Nächste Schritte

- Sie können die Apps jetzt den ausgewählten Gruppen zuweisen. Weitere Informationen finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).
