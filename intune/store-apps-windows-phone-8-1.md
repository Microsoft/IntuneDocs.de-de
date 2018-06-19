---
title: Hinzufügen einer Windows Phone 8.1 Store-App zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie mehr über das Hinzufügen von Windows Phone 8.1 Store-Apps in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e8b3e34e72775061dcc3b40f60e75243972cedd2
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34223593"
---
# <a name="add-windows-phone-81-store-apps-to-microsoft-intune"></a>Hinzufügen einer Windows Phone 8.1 Store-App zu Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Bevor Sie einem Gerät oder einer Gruppe von Benutzern eine App zuweisen, müssen Sie diese zunächst zu Microsoft-Intune hinzufügen. 

## <a name="add-an-app-to-intune"></a>Hinzufügen einer App zu Intune
Mit den folgenden Schritten können Sie eine Windows Phone 8.1 Store-App aus dem Azure-Portal zu Intune hinzufügen:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**.  
    Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** die Option **Mobile Apps** aus.
4. Wählen Sie im Workloadbereich **Mobile Apps** unter **Verwalten** die Option **Apps** aus.
5. Klicken Sie im Bereich **Apps** auf **Hinzufügen**.
6. Wählen Sie im Bereich **App hinzufügen** als **App-Typ** die Option **Windows Phone 8.1** aus, und klicken Sie auf **App-Informationen**.
7. Fügen Sie im Bereich **App-Informationen** die App-Informationen hinzu. Abhängig von der ausgewählten App wurden einige der Werte in diesem Bereich möglicherweise automatisch ausgefüllt:
    - **Name**: Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt werden soll. Stellen Sie sicher, dass der App-Name eindeutig ist. Bei doppelten App-Namen wird den Benutzern im Unternehmensportal nur ein Name angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein. Die Beschreibung wird Benutzern im Unternehmensportal angezeigt.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.
    - **App Store-URL**: Geben Sie die App Store-URL der App ein, die Sie erstellen möchten.
    - **Kategorie**: Wählen Sie optional mindestens eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch ist es für Benutzer einfacher, die App im Unternehmensportal zu finden.
    - **Display this as a featured app in the Company Portal** (Diese App als ausgewählte App im Unternehmensportal anzeigen): Diese Einstellung zeigt die App-Suite auf der Hauptseite des Unternehmensportals hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer**: Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. *Personalabteilung*.
    - **Hinweise**: Geben Sie optional Hinweise zu dieser App ein.
    - **Logo**: Laden Sie optional ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
8. Wählen Sie **OK** aus.
9. Wählen Sie **Hinzufügen** aus.

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können.

## <a name="next-steps"></a>Nächste Schritte

- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md)
