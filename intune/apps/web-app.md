---
title: Hinzufügen von Web-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie Web-Apps (Client-Server-Anwendungen) zu Microsoft Intune hinzufügen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/13/2019
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
ms.openlocfilehash: 997cf043f8ea61133d6e61f4584ad9349aedbf73
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74060039"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Hinzufügen von Web-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune unterstützt eine Vielzahl von App-Typen, einschließlich Web-Apps. Bei einer Web-App handelt es sich um eine Client/Server-Anwendung. Der Server stellt die Web-App bereit, welche die Benutzeroberfläche, den Inhalt und die Funktionen umfasst. Außerdem bieten moderne Webhostingplattformen häufig Vorteile bei Sicherheit und Lastenausgleich. Eine Web-App wird separat im Web verwaltet. Verwenden Sie Microsoft Intune, um auf diesen App-Typ zu verweisen. Sie legen ebenfalls fest, welche Benutzergruppen auf diese App zugreifen können. 

Bevor Sie eine App verwalten und Benutzern zuweisen können, müssen Sie diese in Intune hinzufügen. 

Intune erstellt auf dem Gerät des Benutzers eine Verknüpfung zu der Web-App. Für iOS-Geräte wird dem Startbildschirm eine Verknüpfung mit der Web-App hinzugefügt. Für Android-Geräte wird dem Intune-Unternehmensportalwidget eine Verknüpfung mit der Web-App hinzugefügt, und das Widget muss manuell vom Benutzer angeheftet werden. Für Windows-Geräte wird eine Verknüpfung mit der Web-App im Startmenü platziert.

> [!Note]
> Zum Starten von Web-Apps muss ein Browser auf dem Gerät des Benutzers installiert sein. 

## <a name="add-a-web-app-to-intune"></a>Hinzufügen einer Web-App zu Intune
Führen Sie die folgenden Schritte aus, um eine App als Verknüpfung zu einer App im Internet zu Intune hinzuzufügen:

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** **Client-Apps** aus.
4. Wählen Sie im Workloadbereich **Client-Apps** unter **Verwalten** die Option **Apps** aus.
5. Klicken Sie im Bereich **Apps** auf **Hinzufügen**.
6. Wählen Sie im Bereich **App hinzufügen** aus der Dropdownliste **App-Typ** den Typ **Weblink** aus.
7. Klicken Sie auf **Konfigurieren**.
8. Fügen Sie im Bereich **App-Informationen** die folgenden Informationen hinzu:
    - **Name**:  Geben Sie den Namen der App so ein, wie er im Unternehmensportal angezeigt werden soll. 

        > [!NOTE]
        > Wenn Sie den Namen der App über das Intune Azure-Portal ändern, nachdem Sie sie bereitgestellt und installiert haben, kann die App mit Befehlen nicht mehr erreicht werden.

    - **Beschreibung**: Geben Sie eine Beschreibung der App ein. Die Beschreibung wird Benutzern im Unternehmensportal angezeigt.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers dieser App ein.
    - **App-URL**: Geben Sie die URL der Website ein, auf der die App gehostet wird, die Sie zuweisen möchten.
    - **Kategorie**: Wählen Sie optional eine oder mehrere der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch ist es für Benutzer einfacher, die App im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Wählen Sie diese Option, um die App-Suite auf der Hauptseite des Unternehmensportals hervorgehoben anzuzeigen, wenn die Benutzer nach Apps suchen.
    - **Managed Browser zum Öffnen dieses Links anfordern**: Wählen Sie diese Option aus, um den Benutzern ein Link zu einer Website oder Web-App zuzuweisen, den sie in Intune Managed Browser öffnen können. Dieser Browser muss auf ihrem Gerät installiert sein.
    - **Logo**: Laden Sie ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
9. Wählen Sie **OK** aus.
10. Klicken Sie anschließend im Bereich **App hinzufügen** auf **Hinzufügen**.

> [!Note]
> Benutzer müssen dem Startbildschirm das Intune-Widget hinzufügen, um Web-Apps anzuzeigen, die Android-Geräten zugewiesen wurden.
>
> Derzeit ist die Bereitstellung von Intune-Web-Apps für iOS-Geräte mit dem Verwaltungsprofil verbunden und kann nicht manuell entfernt werden. Sie können den Bereitstellungstyp im Intune-Portal in **Deinstallieren** ändern – an diesem Punkt kann die Web-App automatisch entfernt werden. Aber wenn Sie die Bereitstellung vor dem Ändern der App-Zuweisungsabsicht in **Deinstallieren** entfernen, ist die Web-App dauerhaft auf dem Gerät vorhanden, bis die Registrierung des Geräts bei Intune aufgehoben wird.

Endbenutzer können Web-Apps direkt aus der Windows-Unternehmensportal-App starten, indem sie die Web-App auswählen und dann die Option **Im Browser öffnen** auswählen. Die veröffentlichte Web-URL wird direkt im Webbrowser geöffnet. 

## <a name="next-steps"></a>Nächste Schritte

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md). 
