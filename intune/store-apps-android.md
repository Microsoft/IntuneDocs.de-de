---
title: "Hinzufügen von Android Store-Apps in Microsoft Intune"
titleSuffix: 
description: "Erfahren Sie mehr über das Hinzufügen von Android Store-Apps zu Microsoft Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c2cbc68aa3ea11e3b5593597a94aa059dd2927ed
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="how-to-add-android-store-apps-to-microsoft-intune"></a>Hinzufügen von Android Store-Apps in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Bevor Sie einem Gerät oder einer Gruppe von Benutzern eine App zuweisen, müssen Sie diese zunächst zu Microsoft-Intune hinzufügen. Über die im Folgenden beschriebenen Schritte können Sie eine App aus dem Android-Store aus dem Azure-Portal zu Intune hinzufügen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.
3. Klicken Sie auf dem Blatt **Microsoft Intune** auf die Option **Mobile Apps**.
4. Klicken Sie in der Workload **Mobile Apps** im Abschnitt **Verwalten** auf **Apps**.
5. Wählen Sie über der Liste der Apps **Hinzufügen** aus.
6. Klicken Sie auf dem Blatt **App hinzufügen** unter den verfügbaren **Store-App**-Typen auf **Android**.
7. Klicken Sie auf **Konfigurieren**, um die App-Informationen mit den folgenden Informationen zu konfigurieren. Je nachdem, welche App ausgewählt wurde, werden einige der Werte automatisch in dieses Blatt eingetragen:
    - **Name:** Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein. Diese Beschreibung wird den Benutzern im Unternehmensportal angezeigt.
    - **Herausgeber:** Geben Sie den Namen des Herausgebers der App ein.
    - **App Store-URL:** Geben Sie die App Store-URL der App an, die Sie erstellen möchten.
    - **Mindestens erforderliches Betriebssystem**: Wählen Sie aus der Liste die mindestens erforderliche Betriebssystemversion aus, auf der die App installiert werden kann. Wenn Sie die App einem Gerät mit einem älteren Betriebssystem zuweisen, wird sie nicht installiert.
    - **Kategorie (optional):** Wählen Sie eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch wird es für die Benutzer leichter, die App im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen:** Zeigen Sie die App auf der Hauptseite des Unternehmensportal hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL** (optional): Geben Sie eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird den Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen** (optional): Geben Sie eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird den Benutzern im Unternehmensportal angezeigt.
    - **Entwickler** (optional): Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer** (optional): Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. **Personalabteilung**.
    - **Anmerkungen** (optional): Geben Sie Anmerkungen ein, die dieser App zugewiesen werden sollen.
    - **Logo** (optional): Laden Sie ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
8. Klicken Sie auf **OK**, nachdem Sie die App-Informationen eingerichtet haben.
9. Klicken Sie auf **Hinzufügen**, um die App hinzuzufügen.

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können. 

##<a name="next-steps"></a>Nächste Schritte

- [Zuweisen von Apps zu Gruppen](apps-deploy.md)