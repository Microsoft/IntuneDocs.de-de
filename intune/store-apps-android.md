---
title: Hinzufügen von Android Store-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie mehr über das Hinzufügen von Android Store-Apps zu Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5f191a8e03710d97842ad31083fe3c07008afb56
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190182"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>Hinzufügen von Android Store-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Bevor Sie einem Gerät oder einer Gruppe von Benutzern eine App zuweisen, müssen Sie diese zunächst zu Microsoft-Intune hinzufügen. Mit den folgenden Schritten können Sie eine Android Store-App aus dem Azure-Portal zu Intune hinzufügen:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**.  
    Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** **Client-Apps** aus.
4. Wählen Sie im Workloadbereich **Client-Apps** unter **Verwalten** die Option **Apps** aus.
5. Wählen Sie **Hinzufügen** aus.
6. Wählen Sie im Bereich **App hinzufügen** aus den verfügbaren **Store-App**-Typen den Typ **Android** aus.
7. Wählen Sie zum Konfigurieren der App-Informationen die Option **Konfigurieren** aus, und geben Sie die folgenden Informationen an. Öffnen Sie für Android-Apps den [Google Play Store](https://play.google.com/store), und suchen Sie nach der App, die Sie bereitstellen möchten. Wählen Sie die App aus, und notieren Sie sich die App-Informationen. Abhängig von der ausgewählten App wurden einige Werte möglicherweise automatisch ausgefüllt.
    - **Name**: Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt werden soll. Stellen Sie sicher, dass der App-Name eindeutig ist. Bei doppelten App-Namen wird den Benutzern im Unternehmensportal nur ein Name angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein. Die Beschreibung wird Benutzern im Unternehmensportal angezeigt.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.
    - **App Store-URL**: Geben Sie die App Store-URL der App an, die Sie erstellen möchten.
    - **Minimale Version des Betriebssystems**: Wählen Sie aus der Liste die minimal erforderliche Version des Betriebssystems aus, auf der die App installiert werden kann. Wenn Sie die App einem Gerät mit einem älteren Betriebssystem zuweisen, wird sie nicht installiert.
    - **Kategorie**: Wählen Sie optional mindestens eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch ist es für Benutzer einfacher, die App im Unternehmensportal zu finden.
    - **Display this as a featured app in the Company Portal** (Diese App als ausgewählte App im Unternehmensportal anzeigen): Diese Einstellung zeigt die App-Suite auf der Hauptseite des Unternehmensportals hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer**: Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. *Personalabteilung*.
    - **Hinweise**: Geben Sie optional Hinweise zu dieser App ein.
    - **Logo**: Laden Sie optional ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
1. Wählen Sie **OK** aus.
2. Wählen Sie **Hinzufügen** aus.

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können. 

## <a name="next-steps"></a>Nächste Schritte

- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md)
