---
title: Hinzufügen von integrierten Apps zu mobilen Geräten mit Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie Intune verwenden können, um integrierte Apps einfacher auf mobilen Geräten installieren zu können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: a92699ccce4f0b2590e526b3442cd45bfda6407c
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563597"
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>Hinzufügen von integrierten Apps zu Microsoft Intune

Der *integrierte* App-Typ erleichtert Ihnen das Zuweisen geordneter verwalteter Apps, z.B. Office 365-Apps, zu iOS- und Android-Geräten. Sie können bestimmte Apps für diesen App-Typ zuweisen, z.B. Excel, OneDrive, Outlook oder Skype. Nach dem Hinzufügen einer App wird als App-Typ entweder *Integrierte iOS-App* oder *Integrierte Android-App* angezeigt. Mithilfe des integrierten App-Typs können Sie wählen, welche dieser Apps Sie für Gerätebenutzer veröffentlichen möchten.

In früheren Versionen der Intune-Konsole stellte Intune mehrere standardmäßig verwaltete Office 365-Apps wie Outlook und OneDrive bereit. Diese verwalteten Apps wurden mit den App-Typen *Verwaltete iOS Store-App* oder *Verwaltete Android-App* bezeichnet. Es wird empfohlen, anstelle dieser App-Typen den integrierten App-Typen zu verwenden. Mit dem integrierten App-Typen können Sie außerdem Office 365-Apps flexibler bearbeiten und löschen.

>[!NOTE]
>Als *Verwaltete iOS Store-App* oder *Verwaltete Android-App* bezeichnete standardmäßige Office 365-Apps werden aus der Liste der Apps entfernt, wenn alle Zuweisungen gelöscht sind.

## <a name="add-a-built-in-app"></a>Hinzufügen einer integrierten App

So fügen Sie eine integrierte App Ihren verfügbaren Apps in Microsoft Intune hinzu
1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus.
3. Wählen Sie im App-Bereich **Hinzufügen** in der Liste **App-Typ** die Option **Integrierte App** aus.
4. Wählen Sie **App auswählen** aus.
5. Wählen Sie im Bereich **Integrierte App** die Apps aus, die enthalten sein sollen.
6. Klicken Sie anschließend im Bereich **App hinzufügen** auf **Hinzufügen**.


## <a name="configure-app-information"></a>Konfigurieren von App-Informationen

Sie können die Informationen zu der integrierten App ändern. Diese Informationen helfen Ihnen, die App in Intune zu identifizieren, und Endbenutzer können sie leichter im Unternehmensportal finden.
1. Wählen Sie **Apps** > **Alle Apps** und dann die integrierte App aus, die Sie ändern möchten.  
   Es wird ein Bereich für die integrierte App angezeigt.
2. Wählen Sie **Eigenschaften** > **Konfigurieren** aus.
4. Im Bereich **App-Informationen** können Sie die folgenden Informationen ändern:
    - **Name**: Geben Sie den Namen der integrierten App ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung**: Geben Sie eine Beschreibung der App ein. 
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.
    - **Kategorie**: Wählen Sie optional mindestens eine der Kategorien für integrierte Apps aus. Die Einstellung dieser Option erleichtert Benutzern, die App im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen:** Präsentieren Sie die App herausgehoben auf der Hauptseite des Unternehmensportals, wenn die Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer**: Geben Sie optional einen Namen für den Besitzer dieser App ein, (z. B. *Personalabteilung*).
    - **Anmerkungen**: Geben Sie Hinweise zu dieser App ein.
    - **Symbol hochladen:** Laden Sie ein Symbol hoch, das mit der App angezeigt wird, wenn Benutzer das Unternehmensportal durchsuchen.
4. Wählen Sie **OK** aus.
5. Wählen Sie im Bereich **Eigenschaften** die Option **Speichern**.

## <a name="next-steps"></a>Nächste Schritte

- Sie können die Apps jetzt den ausgewählten Gruppen zuweisen. Weitere Informationen finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).
