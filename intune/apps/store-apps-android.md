---
title: Hinzufügen von Android Store-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie Android Store-Apps aus dem Google Play Store zu Microsoft Intune hinzufügen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3153a470649e86bbafc9e8295a1c68532fc27c63
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72497699"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>Hinzufügen von Android Store-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Bevor Sie einem Gerät oder einer Gruppe von Benutzern eine App zuweisen, müssen Sie diese zunächst zu Microsoft-Intune hinzufügen. 

## <a name="add-an-app"></a>Hinzufügen einer App

Mit den folgenden Schritten können Sie eine Android Store-App aus dem Azure-Portal zu Intune hinzufügen:

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** **Client-Apps** aus.
4. Wählen Sie im Workloadbereich **Client-Apps** unter **Verwalten** die Option **Apps** aus.
5. Wählen Sie **Hinzufügen** aus.
6. Wählen Sie im Bereich **App hinzufügen** aus den verfügbaren **Store-App**-Typen den Typ **Android** aus.
7. Wählen Sie zum Konfigurieren der App-Informationen die Option **Konfigurieren** aus, und geben Sie die folgenden Informationen an. Öffnen Sie für Android-Apps den [Google Play Store](https://play.google.com/store), und suchen Sie nach der App, die Sie bereitstellen möchten. Wählen Sie die App aus, und notieren Sie sich die App-Informationen. Abhängig von der ausgewählten App wurden einige Werte möglicherweise automatisch ausgefüllt.
    - **Name**: Geben Sie den Namen der App so ein, wie er im Unternehmensportal angezeigt werden soll. Stellen Sie sicher, dass der App-Name eindeutig ist. Bei doppelten App-Namen wird den Benutzern im Unternehmensportal nur ein Name angezeigt.
    - **Beschreibung**: Geben Sie eine Beschreibung der App ein. Die Beschreibung wird Benutzern im Unternehmensportal angezeigt.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.
    - **Appstore-URL**: Geben Sie die App-Store-URL der App ein, die Sie erstellen möchten.
    - **Mindestens erforderliches Betriebssystem**: Wählen Sie aus der Liste die früheste Betriebssystemversion aus, unter der die App installiert werden kann. Wenn Sie die App einem Gerät mit einem älteren Betriebssystem zuweisen, wird sie nicht installiert.
    - **Kategorie**: Wählen Sie optional eine oder mehrere der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch ist es für Benutzer einfacher, die App im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Wählen Sie diese Option, um die App-Suite auf der Hauptseite des Unternehmensportals hervorgehoben anzuzeigen, wenn die Benutzer nach Apps suchen. Gilt für Apps, die mit der Absicht „Verfügbar“ bereitgestellt wurden.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer**: Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. *Personalabteilung*.
    - **Anmerkungen**: Geben Sie optional Hinweise zu dieser App ein.
    - **Logo**: Laden Sie optional ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
8. Wählen Sie **OK** aus.
9. Wählen Sie **Hinzufügen** aus.

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können. 

## <a name="next-steps"></a>Nächste Schritte

- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md)
