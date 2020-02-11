---
title: Hinzufügen von Microsoft Store-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie mehr über das Hinzufügen von Microsoft Store-Apps (Windows Store) in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8743af2a05f6daebca5e1394ba5b7b8f13fcf7e3
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754897"
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Hinzufügen von Microsoft Store-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Bevor Sie Apps zuweisen, überwachen, konfigurieren oder schützen können, müssen Sie sie zu Intune hinzufügen. 

## <a name="add-an-app-to-intune"></a>Hinzufügen einer App zu Intune
Führen Sie die folgenden Schritte aus, um eine Microsoft Store-App zu Intune hinzuzufügen:

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus.
3. Wählen Sie im Bereich **App-Typ auswählen** unter den verfügbaren **Store-App**-Typen **Windows Store-App** aus.
4. Klicken Sie auf **Auswählen**. Die **App hinzufügen**-Schritte werden angezeigt.
5. Um die **App-Informationen** für Windows Store-Apps zu konfigurieren, navigieren Sie zum [Microsoft Store](https://www.microsoft.com/store/apps), und suchen Sie nach der App, die Sie bereitstellen möchten. Zeigen Sie die App-Seite an, und notieren Sie sich die App-Details. 
6. Fügen Sie auf der Seite **App-Informationen** die App-Details hinzu:
    - **Name:** Geben Sie den Namen der App so ein, wie er im Unternehmensportal angezeigt werden soll. Stellen Sie sicher, dass der App-Name eindeutig ist. Bei doppelten App-Namen wird den Benutzern im Unternehmensportal nur ein Name angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung der App ein. Die Beschreibung wird Benutzern im Unternehmensportal angezeigt.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.
    - **Appstore-URL**: Geben Sie die App-Store-URL der App ein, die Sie erstellen möchten. Die URL finden Sie, indem Sie im [Microsoft Store](https://www.microsoft.com/store/apps) nach der gewünschten App suchen. Verwenden Sie die URL in der Adressleiste des Browsers.
    - **Kategorie**: Wählen Sie optional eine oder mehrere der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch ist es für Benutzer einfacher, die App im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Wählen Sie diese Option, um die App-Suite auf der Hauptseite des Unternehmensportals hervorgehoben anzuzeigen, wenn die Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer**: Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. *Personalabteilung*.
    - **Anmerkungen**: Geben Sie optional Hinweise zu dieser App ein.
    - **Logo**: Laden Sie optional ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
7. Klicken Sie auf **Weiter**, um die Seite **Bereichsmarkierungen** anzuzeigen.
8. Klicken Sie auf **Bereichstags auswählen**, um optional Bereichsmarkierungen für die App hinzuzufügen. Weitere Informationen dazu finden Sie unter [Verwenden der rollenbasierten Zugriffssteuerung und Bereichsmarkierungen für verteilte IT](~/fundamentals/scope-tags.md).
9. Klicken Sie auf **Weiter**, um die Seite **Zuweisungen** anzuzeigen.
10. Wählen Sie die Gruppenzuweisungen für die App aus. Weitere Informationen finden Sie unter [Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten](~/fundamentals/groups-add.md). 
11. Klicken Sie auf **Weiter**, um die Seite **Überprüfen + erstellen** anzuzeigen. Überprüfen Sie die Werte und Einstellungen, die Sie für die App eingegeben haben.
12. Klicken Sie abschließend auf **Erstellen**, um Intune die App hinzuzufügen.

Die von Ihnen erstellte App wird im Blatt **Übersicht** angezeigt.

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können.

> [!IMPORTANT]
> Microsoft Store-Apps können nur Gruppen zugewiesen werden, die den Zuweisungstyp **Für registrierte Geräte verfügbar** aufweisen (Benutzer installieren die App über die Unternehmensportal-App oder -Website).

## <a name="next-steps"></a>Nächste Schritte
- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md)
