---
title: "Hinzufügen integrierter Apps zu mobilen Geräten mit Intune"
titlesuffix: Azure portal
description: "Erfahren Sie, wie Sie Intune verwenden können, um integrierte Apps einfacher auf mobilen Geräten installieren zu können."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 90bec6442084e46f499c57cf128e6ef57fe1ce9c
ms.sourcegitcommit: 0a5f424a8f683daa919b13b5c363173040d561c8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-add-built-in-apps-to-microsoft-intune"></a>Hinzufügen von integrierten Apps zu Microsoft Intune

Der **integrierte** App-Typ erleichtert Ihnen das Zuweisen geordneter verwalteter Apps, z.B. Office 365-Apps, zu iOS- und Android-Geräten. Sie können bestimmte Apps für diesen App-Typ zuweisen, z.B. Excel, Power BI, SharePoint, Teams, OneDrive, Outlook, Skype und andere. Nach dem Hinzufügen einer App sehen Sie den App-Typ entweder als **Integrierte iOS-App** oder **Integrierte Android-App**. Mithilfe des integrierten App-Typs können Sie wählen, welche dieser bestimmten Apps Sie für Gerätebenutzer veröffentlichen möchten.

 In früheren Versionen der Intune-Konsole stellte Intune mehrere standardmäßig verwaltete Office 365-Apps wie Outlook und OneDrive bereit. Diese verwalteten Apps wurden mit dem App-Typ „Verwaltete iOS Store-App" oder „Verwaltete Android-App“ bezeichnet. Sie sollten die integrierten App-Typen anstelle von „Verwaltete iOS Store-App" oder „Verwaltete Android-App“ verwenden, da diese zusätzliche Flexibilität zum Bearbeiten und Löschen von Office 365-Apps bieten.

>[!NOTE]
>Als „Verwaltete iOS Store-App" oder „Verwaltete Android-App“ bezeichnete standardmäßige Office 365-Apps werden aus der Liste der Apps entfernt, wenn alle Zuweisungen für diese Apps gelöscht sind.

## <a name="add-built-in-app"></a>Hinzufügen einer integrierten App

Mit den folgenden Schritten können Sie eine integrierte App Ihren verfügbaren Apps in Microsoft Intune hinzufügen.
1.  Melden Sie sich beim Azure-Portal an.
2.  Zeigen Sie das Blatt „Microsoft Intune“ an, indem Sie **Mehr Dienste** > **Überwachung und Verwaltung** > **Intune** auswählen.
3.  Wählen Sie auf dem Blatt **Intune** die Option **Mobile Apps** aus.
4.  Wählen Sie auf dem Blatt **Mobile Apps** die Option **Apps** in der Gruppe **Verwalten** aus.
5.  Wählen Sie **Hinzufügen**, um eine neue App hinzuzufügen.
6.  Wählen Sie auf dem App-Blatt **Hinzufügen** die Option **Integrierte App** in der Liste **App-Typ** aus.
7.  Klicken Sie auf **App auswählen**, um die einzuschließenden integrierten Apps auszuwählen.
8.  Wählen Sie auf dem Blatt „Integrierte App“ die einzuschließenden Apps aus.
9.  Klicken Sie auf dem Blatt **App hinzufügen** auf **Hinzufügen**, um die Apps einzuschließen.


## <a name="configure-app-information"></a>Konfigurieren von App-Informationen

Sie können die Informationen zu der integrierten App ändern. Diese Informationen helfen Ihnen, die App in Intune zu identifizieren, und Endbenutzer können sie leichter in der Unternehmensportal-App finden.
1.  Wählen Sie auf dem Blatt **Mobile Apps – Apps** die integrierte App aus, die Sie ändern möchten. Es wird ein Blatt für die integrierte App angezeigt.
2.  Wählen Sie die Option **Eigenschaften** in der Gruppe **Verwalten**.
3.  Wählen Sie die Option **Konfigurieren** aus, um die Informationen zu der integrierten App zu ändern.
4.  Auf dem Blatt **App-Informationen** können Sie die folgenden Informationen ändern:
    -   **Name:** Geben Sie den Namen der integrierten App ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    -   **Beschreibung:** Geben Sie eine Beschreibung für die App ein. 
    -   **Herausgeber:** Geben Sie den Namen des Herausgebers der App ein.
    -   **Kategorie:** Wählen Sie optional mindestens eine der Kategorien für integrierte Apps aus. Die Einstellung dieser Option erleichtert Benutzern, die App im Unternehmensportal zu finden.
    -   **Diese App als ausgewählte App im Unternehmensportal anzeigen:** Zeigen Sie die App auf der Hauptseite des Unternehmensportal hervorgehoben an, wenn Benutzer nach Apps suchen.
    -   **Informations-URL:** Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    -   **URL zu den Datenschutzbestimmungen:** Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    -   **Entwickler:** Geben Sie optional den Namen des App-Entwicklers ein.
    -   **Besitzer:** Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. „Personalabteilung“.
    -   **Anmerkungen:** Geben Sie Hinweise zu dieser App ein.
    -   **Symbol hochladen:** Laden Sie ein Symbol hoch, das gemeinsam mit der App angezeigt wird, wenn die Benutzer das Unternehmensportal durchsuchen.
3.  Klicken Sie dann auf dem Blatt **App-Informationen** auf **OK**.
4.  Klicken Sie auf dem Blatt **Eigenschaften** auf **Speichern**.

## <a name="next-steps"></a>Nächste Schritte

Sie können die Apps jetzt den ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).