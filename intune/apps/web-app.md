---
title: Hinzufügen von Web-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie Web-Apps (Client-Server-Anwendungen) zu Microsoft Intune hinzufügen.
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
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 90cdff66d32ac5edb3b1867a545f2c9627ccfe39
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754778"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Hinzufügen von Web-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune unterstützt eine Vielzahl von App-Typen, einschließlich Web-Apps. Bei einer Web-App handelt es sich um eine Client/Server-Anwendung. Der Server stellt die Web-App bereit, welche die Benutzeroberfläche, den Inhalt und die Funktionen umfasst. Außerdem bieten moderne Webhostingplattformen häufig Vorteile bei Sicherheit und Lastenausgleich. Eine Web-App wird separat im Web verwaltet. Verwenden Sie Microsoft Intune, um auf diesen App-Typ zu verweisen. Sie legen ebenfalls fest, welche Benutzergruppen auf diese App zugreifen können. 

Bevor Sie eine App verwalten und Benutzern zuweisen können, müssen Sie diese in Intune hinzufügen. 

Intune erstellt auf dem Gerät des Benutzers eine Verknüpfung zu der Web-App. Für iOS-Geräte wird dem Startbildschirm eine Verknüpfung mit der Web-App hinzugefügt. Für Android Device-Admin-Geräte wird dem Intune-Unternehmensportalwidget eine Verknüpfung mit der Web-App hinzugefügt, und das Widget muss manuell vom Benutzer angeheftet werden. Für Windows-Geräte wird eine Verknüpfung mit der Web-App im Startmenü platziert.

> [!Note]
> Zum Starten von Web-Apps muss ein Browser auf dem Gerät des Benutzers installiert sein. 

> [!Note]
> Für Android Enterprise-Geräte: [Weblinks „Verwaltetes Google Play“](apps-add-android-for-work.md#managed-google-play-web-links)

## <a name="add-a-web-app-to-intune"></a>Hinzufügen einer Web-App zu Intune
Führen Sie die folgenden Schritte aus, um eine App als Verknüpfung zu einer App im Internet zu Intune hinzuzufügen:

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus.
3. Wählen Sie im Bereich **App-Typ auswählen** aus den verfügbaren **Sonstigen** Typen **Weblink** aus.
4. Klicken Sie auf **Auswählen**. Die **App hinzufügen**-Schritte werden angezeigt.
5. Fügen Sie auf der Seite **App-Informationen** die folgenden Informationen hinzu:
    - **Name:**  Geben Sie den Namen der App so ein, wie er im Unternehmensportal angezeigt werden soll. 

        > [!NOTE]
        > Wenn Sie den Namen der App über das Intune Azure-Portal ändern, nachdem Sie sie bereitgestellt und installiert haben, kann die App mit Befehlen nicht mehr erreicht werden.

    - **Beschreibung:** Geben Sie eine Beschreibung der App ein. Die Beschreibung wird Benutzern im Unternehmensportal angezeigt.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers dieser App ein.
    - **App-URL**: Geben Sie die URL der Website ein, auf der die App gehostet wird, die Sie zuweisen möchten.
    - **Kategorie**: Wählen Sie optional eine oder mehrere der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch ist es für Benutzer einfacher, die App im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Wählen Sie diese Option, um die App-Suite auf der Hauptseite des Unternehmensportals hervorgehoben anzuzeigen, wenn die Benutzer nach Apps suchen.
    - **Managed Browser zum Öffnen dieses Links anfordern**: Wählen Sie diese Option aus, um den Benutzern ein Link zu einer Website oder Web-App zuzuweisen, den sie in Intune Managed Browser öffnen können. Dieser Browser muss auf ihrem Gerät installiert sein.
    - **Logo**: Laden Sie ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
6. Klicken Sie auf **Weiter**, um die Seite **Bereichsmarkierungen** anzuzeigen.
7. Klicken Sie auf **Bereichstags auswählen**, um optional Bereichsmarkierungen für die App hinzuzufügen. Weitere Informationen dazu finden Sie unter [Verwenden der rollenbasierten Zugriffssteuerung und Bereichsmarkierungen für verteilte IT](~/fundamentals/scope-tags.md).
8. Klicken Sie auf **Weiter**, um die Seite **Zuweisungen** anzuzeigen.
9. Wählen Sie die Gruppenzuweisungen für die App aus. Weitere Informationen finden Sie unter [Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten](~/fundamentals/groups-add.md). 
10. Klicken Sie auf **Weiter**, um die Seite **Überprüfen + erstellen** anzuzeigen. Überprüfen Sie die Werte und Einstellungen, die Sie für die App eingegeben haben.
11. Klicken Sie abschließend auf **Erstellen**, um Intune die App hinzuzufügen.

    Die von Ihnen erstellte App wird im Blatt **Übersicht** angezeigt.

> [!Note]
> Derzeit ist die Bereitstellung von Intune-Web-Apps für iOS-Geräte mit dem Verwaltungsprofil verbunden und kann nicht manuell entfernt werden. Sie können den Bereitstellungstyp im Intune-Portal in **Deinstallieren** ändern – an diesem Punkt kann die Web-App automatisch entfernt werden. Aber wenn Sie die Bereitstellung vor dem Ändern der App-Zuweisungsabsicht in **Deinstallieren** entfernen, ist die Web-App dauerhaft auf dem Gerät vorhanden, bis die Registrierung des Geräts bei Intune aufgehoben wird.

Endbenutzer können Web-Apps direkt aus der Windows-Unternehmensportal-App starten, indem sie die Web-App auswählen und dann die Option **Im Browser öffnen** auswählen. Die veröffentlichte Web-URL wird direkt im Webbrowser geöffnet. 

## <a name="next-steps"></a>Nächste Schritte

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md). 
