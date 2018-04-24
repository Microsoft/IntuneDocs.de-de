---
title: Hinzufügen von Microsoft Store-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie mehr über das Hinzufügen von Microsoft Store-Apps (Windows Store) in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 511cf2e01a2f5db93f0e0db9dbe2a32326c17723
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Hinzufügen von Microsoft Store-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Bevor Sie Apps zuweisen, überwachen, konfigurieren oder schützen können, müssen Sie sie zu Intune hinzufügen. Mit den folgenden Schritte können Sie eine Microsoft Store-App zu Microsoft Intune hinzufügen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Mobile Apps**.
4. Wählen Sie in der Workload **Mobile Apps** die Option **Verwalten** > **Apps** aus.
5. Wählen Sie über der Liste der Apps **Hinzufügen** aus.
6. Wählen Sie im Bereich **App hinzufügen** als **App-Typ** die Option **Windows** aus, und klicken Sie auf **App-Informationen**.
7. Konfigurieren Sie im Bereich **App-Informationen** die folgenden Informationen. Klicken Sie abschließend auf **OK**. Abhängig von der ausgewählten App wurden einige der Werte in diesem Bereich möglicherweise automatisch ausgefüllt:
    - **Name:** Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein, die den Benutzern im Unternehmensportal angezeigt werden soll.
    - **Herausgeber:** Geben Sie den Namen des Herausgebers der App ein.
    - **App Store-URL:** Geben Sie die App Store-URL der App an, die Sie erstellen möchten.
    - **Kategorie** (optional): Wählen Sie mindestens eine der integrierten App-Kategorien oder eine von Ihnen erstellte Kategorie aus. So können Benutzer die App im Unternehmensportal leichter finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen:** Zeigen Sie die App auf der Hauptseite des Unternehmensportal hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL:** Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird den Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen:** Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird den Benutzern im Unternehmensportal angezeigt.
    - **Entwickler:** Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer:** Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. **Personalabteilung**.
    - **Anmerkungen:** Geben Sie Hinweise zu dieser App ein.
    - **Logo:** Laden Sie ein Symbol für die App hoch. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
8. Wenn Sie fertig sind, klicken Sie im Bereich **App hinzufügen** auf **Hinzufügen**.

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie ausgewählten Gruppen zuweisen können. 

## <a name="next-steps"></a>Nächste Schritte
- [Zuweisen von Apps zu Gruppen](apps-deploy.md)