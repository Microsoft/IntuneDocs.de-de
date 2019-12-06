---
title: Hinzufügen von iOS Store-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie mehr über das Hinzufügen von iOS Store-Apps in Microsoft Intune. Sie können mit dieser Methode Apps zuweisen, die im App Store kostenlos angeboten werden.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c5616b27b97d5623958ec872390e2a6de79db3c5
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563450"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>Hinzufügen von iOS Store-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Fügen Sie mithilfe der Informationen in diesem Artikel iOS Store-Apps zu Microsoft Intune hinzu. iOS Store-Apps sind Apps, die von Intune auf den Geräten Ihrer Benutzer installiert werden. Ein Benutzer ist ein Mitarbeiter Ihres Unternehmens. iOS Store-Apps werden automatisch aktualisiert.

>[!NOTE]
>Obgleich Benutzer von iOS-Geräten einige der integrierten iOS-Apps wie Stocks und Maps entfernen können, lassen sich diese Apps über Intune nicht erneut bereitstellen. Wenn Ihre Benutzer diese Apps löschen, müssen sie zum App Store navigieren und die Apps manuell erneut installieren.

## <a name="before-you-start"></a>Vorbereitung

Sie können mit dieser Methode nur Apps zuweisen, die im App Store kostenlos angeboten werden. Wenn Sie mithilfe von Intune kostenpflichtige Apps zuweisen möchten, erwägen Sie die Nutzung des [iOS Volume Purchase Program](vpp-apps-ios.md).

>[!NOTE]
>Für die Arbeit mit Microsoft Intune wird als Browser Microsoft Edge oder Google Chrome empfohlen.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus.
3. Wählen Sie in der Liste **App-Typ** unter dem Typ **Store-App** die Option **iOS** aus.
4. Wählen Sie **App Store durchsuchen** aus.
5. Wählen Sie im Bereich **App Store durchsuchen** das Gebietsschema des App Store aus.
6. Geben Sie in das Feld **Suchen** den Namen (oder einen Teil des Namens) der App ein.  
    Intune durchsucht den Store und gibt eine Liste mit relevanten Ergebnissen zurück.
7. Wählen Sie in der Ergebnisliste die gewünschte App und dann **Auswählen** aus.
8. Wählen Sie im Bereich **App hinzufügen** die Option **App-Informationen** aus, um die App zu konfigurieren.
9. Fügen Sie im Bereich **App-Informationen** die App-Informationen hinzu. Abhängig von der ausgewählten App wurden einige der Werte in diesem Bereich möglicherweise automatisch ausgefüllt:
    - **Name**: Geben Sie den Namen der App so ein, wie er im Unternehmensportal angezeigt werden soll. Stellen Sie sicher, dass der App-Name eindeutig ist. Bei doppelten App-Namen wird den Benutzern im Unternehmensportal nur ein Name angezeigt.
    - **Beschreibung**: Geben Sie eine Beschreibung der App ein. Die Beschreibung wird Benutzern im Unternehmensportal angezeigt.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.
    - **Appstore-URL**: Geben Sie die App-Store-URL der App ein, die Sie erstellen möchten.
    - **Mindestens erforderliches Betriebssystem**: Wählen Sie aus der Liste die früheste Betriebssystemversion aus, unter der die App installiert werden kann. Wenn Sie die App einem Gerät mit einem älteren Betriebssystem zuweisen, wird sie nicht installiert.
    - **Anwendbarer Gerätetyp**: Wählen Sie in der Liste die Geräte aus, die von der App verwendet werden.
    - **Kategorie**: Wählen Sie optional eine oder mehrere der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch ist es für Benutzer einfacher, die App im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Wählen Sie diese Option, um die App-Suite auf der Hauptseite des Unternehmensportals hervorgehoben anzuzeigen, wenn die Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Geben Sie optional den Namen des App-Entwicklers ein. Dieses Feld ist nur für Administratoren sichtbar. Ihren Benutzern wird es nicht angezeigt.
    - **Besitzer**: Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. *Personalabteilung*. Dieses Feld ist nur für Administratoren sichtbar. Ihren Benutzern wird es nicht angezeigt.
    - **Anmerkungen**: Geben Sie optional Hinweise zu dieser App ein. Dieses Feld ist nur für Administratoren sichtbar, für Endbenutzer nicht.
    - **Logo**: Laden Sie optional ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
10. Wählen Sie **OK** aus.
11. Wählen Sie **Hinzufügen** aus.

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können.

## <a name="next-steps"></a>Nächste Schritte

- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md)
