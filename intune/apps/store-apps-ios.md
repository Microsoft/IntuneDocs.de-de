---
title: Hinzufügen von iOS Store-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie mehr über das Hinzufügen von iOS Store-Apps in Microsoft Intune. Sie können mit dieser Methode Apps zuweisen, die im App Store kostenlos angeboten werden.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
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
ms.openlocfilehash: f2baf60fed2c6010e5ae0784cda166ac4fabfd57
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511734"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>Hinzufügen von iOS Store-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Fügen Sie mithilfe der Informationen in diesem Artikel iOS Store-Apps zu Microsoft Intune hinzu. iOS Store-Apps sind Apps, die von Intune auf den Geräten Ihrer Benutzer installiert werden. Ein Benutzer ist ein Mitarbeiter Ihres Unternehmens. iOS Store-Apps werden automatisch aktualisiert.

>[!NOTE]
>Obgleich Benutzer von iOS/iPadOS-Geräten einige der integrierten iOS/iPadOS-Apps wie Stocks und Maps entfernen können, lassen sich diese Apps über Intune nicht erneut bereitstellen. Wenn Ihre Benutzer diese Apps löschen, müssen sie zum App Store navigieren und die Apps manuell erneut installieren.

## <a name="before-you-start"></a>Vorbereitung

Sie können mit dieser Methode nur Apps zuweisen, die im App Store kostenlos angeboten werden. Erwägen Sie die Nutzung des [iOS/iPadOS Volume Purchase Program](vpp-apps-ios.md), wenn Sie mithilfe von Intune kostenpflichtige Apps zuweisen möchten.

>[!NOTE]
>Für die Arbeit mit Microsoft Intune wird als Browser Microsoft Edge oder Google Chrome empfohlen.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus.
3. Wählen Sie im Bereich **App-Typ auswählen** unter den verfügbaren **Store-App**-Typen **iOS Store-App** aus.
4. Klicken Sie auf **Auswählen**.<br>
   Die **App hinzufügen**-Schritte werden angezeigt.
5. Wählen Sie **App Store durchsuchen** aus.
6. Wählen Sie im Bereich **App Store durchsuchen** das Gebietsschema des App Store aus.
7. Geben Sie in das Feld **Suchen** den Namen (oder einen Teil des Namens) der App ein.  
    Intune durchsucht den Store und gibt eine Liste mit relevanten Ergebnissen zurück.
8. Wählen Sie in der Ergebnisliste die gewünschte App und dann **Auswählen** aus.<br>

   Die Seite **App-Informationen** wird im Bereich **App hinzufügen** angezeigt. Nach Möglichkeit werden App-Informationen basierend auf der App hinzugefügt, die Sie im Store ausgewählt haben.

9. Fügen Sie auf der Seite **App-Informationen** die App-Details hinzu. Abhängig von der ausgewählten App wurden einige der Werte in diesem Bereich möglicherweise automatisch ausgefüllt:
    - **Name:** Geben Sie den Namen der App so ein, wie er im Unternehmensportal angezeigt werden soll. Stellen Sie sicher, dass der App-Name eindeutig ist. Bei doppelten App-Namen wird den Benutzern im Unternehmensportal nur ein Name angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung der App ein. Die Beschreibung wird Benutzern im Unternehmensportal angezeigt.
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
10. Klicken Sie auf **Weiter**, um die Seite **Bereichsmarkierungen** anzuzeigen.
11. Klicken Sie auf **Bereichstags auswählen**, um optional Bereichsmarkierungen für die App hinzuzufügen. Weitere Informationen dazu finden Sie unter [Verwenden der rollenbasierten Zugriffssteuerung und Bereichsmarkierungen für verteilte IT](~/fundamentals/scope-tags.md).
12. Klicken Sie auf **Weiter**, um die Seite **Zuweisungen** anzuzeigen.
13. Wählen Sie die Gruppenzuweisungen für die App aus. Weitere Informationen finden Sie unter [Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten](~/fundamentals/groups-add.md). 
14. Klicken Sie auf **Weiter**, um die Seite **Überprüfen + erstellen** anzuzeigen. Überprüfen Sie die Werte und Einstellungen, die Sie für die App eingegeben haben.
15. Klicken Sie abschließend auf **Erstellen**, um Intune die App hinzuzufügen.

Die von Ihnen erstellte App wird im Blatt **Übersicht** angezeigt.

## <a name="next-steps"></a>Nächste Schritte

- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md)
