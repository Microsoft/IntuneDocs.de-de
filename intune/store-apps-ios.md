---
title: Hinzufügen von iOS Store-Apps zu Microsoft Intune
titlesuffix: ''
description: Erfahren Sie mehr über das Hinzufügen von iOS Store-Apps in Microsoft Intune.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 832105078572b3229334ccdcb2e3e89ace9e0408
ms.sourcegitcommit: 63b74a60aafa8d2d6af0594448ae0471fbd79194
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494063"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>Hinzufügen von iOS Store-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Fügen Sie mithilfe der Informationen in diesem Artikel iOS Store-Apps zu Microsoft Intune hinzu. iOS Store-Apps sind Apps, die von Intune auf den Geräten Ihrer Benutzer installiert werden. Ein Benutzer ist ein Mitarbeiter Ihres Unternehmens. iOS Store-Apps werden automatisch aktualisiert.

>[!NOTE]
>Obgleich Benutzer von iOS-Geräten einige der integrierten iOS-Apps wie Stocks und Maps entfernen können, lassen sich diese Apps über Intune nicht erneut bereitstellen. Wenn Ihre Benutzer diese Apps löschen, müssen sie zum App Store navigieren und die Apps manuell erneut installieren.

## <a name="before-you-start"></a>Vorbereitungen

Sie können mit dieser Methode nur Apps zuweisen, die im App Store kostenlos angeboten werden. Wenn Sie mithilfe von Intune kostenpflichtige Apps zuweisen möchten, erwägen Sie die Nutzung des [iOS Volume Purchase Program](vpp-apps-ios.md).

>[!NOTE]
>Für die Arbeit mit Microsoft Intune wird als Browser Microsoft Edge oder Google Chrome empfohlen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**.  
    Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** **Client-Apps** aus.
4. Wählen Sie im Workloadbereich **Client-Apps** unter **Verwalten** die Option **Apps** aus.
5. Klicken Sie im Bereich **Apps** auf **Hinzufügen**.
6. Wählen Sie in der Liste **App-Typ** unter dem Typ **Store-App** die Option **iOS** aus.
7. Wählen Sie **App Store durchsuchen** aus.
8. Wählen Sie im Bereich **App Store durchsuchen** das Gebietsschema des App Store aus.
9. Geben Sie in das Feld **Suchen** den Namen (oder einen Teil des Namens) der App ein.  
    Intune durchsucht den Store und gibt eine Liste mit relevanten Ergebnissen zurück.
10. Wählen Sie in der Ergebnisliste die gewünschte App und dann **Auswählen** aus.
11. Wählen Sie im Bereich **App hinzufügen** die Option **App-Informationen** aus, um die App zu konfigurieren.
12. Fügen Sie im Bereich **App-Informationen** die App-Informationen hinzu. Abhängig von der ausgewählten App wurden einige der Werte in diesem Bereich möglicherweise automatisch ausgefüllt:
    - **Name**: Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt werden soll. Stellen Sie sicher, dass der App-Name eindeutig ist. Bei doppelten App-Namen wird den Benutzern im Unternehmensportal nur ein Name angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein. Die Beschreibung wird Benutzern im Unternehmensportal angezeigt.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.
    - **App Store-URL**: Geben Sie die App Store-URL der App ein, die Sie erstellen möchten.
    - **Minimale Version des Betriebssystems**: Wählen Sie aus der Liste die minimal erforderliche Version des Betriebssystems aus, auf der die App installiert werden kann. Wenn Sie die App einem Gerät mit einem älteren Betriebssystem zuweisen, wird sie nicht installiert.
    - **Verwendbarer Gerätetyp**: Wählen Sie in der Liste die Geräte aus, die von der App verwendet werden.
    - **Kategorie**: Wählen Sie optional mindestens eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch ist es für Benutzer einfacher, die App im Unternehmensportal zu finden.
    - **Display this as a featured app in the Company Portal** (Diese App als ausgewählte App im Unternehmensportal anzeigen): Diese Einstellung zeigt die App-Suite auf der Hauptseite des Unternehmensportals hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Geben Sie optional den Namen des App-Entwicklers ein. Dieses Feld ist nur für Administratoren sichtbar. Ihren Benutzern wird es nicht angezeigt.
    - **Besitzer**: Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. *Personalabteilung*. Dieses Feld ist nur für Administratoren sichtbar. Ihren Benutzern wird es nicht angezeigt.
    - **Hinweise**: Geben Sie optional Hinweise zu dieser App ein. Dieses Feld ist nur für Administratoren sichtbar, für Endbenutzer nicht.
    - **Logo**: Laden Sie optional ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
13. Wählen Sie **OK** aus.
14. Wählen Sie **Hinzufügen** aus.

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können.

## <a name="next-steps"></a>Nächste Schritte

- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md)
