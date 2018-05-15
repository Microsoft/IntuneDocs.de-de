---
title: Hinzufügen von Web-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie mehr über das Hinzufügen von Web-Apps in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 58d04de3c4f77a5599bc5a13f2fe1e382654bd73
ms.sourcegitcommit: 2b5d88c434bda7f1cdc32d1ccacc6b341a9a399b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="add-web-apps-to-microsoft-intune"></a>Hinzufügen von Web-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune unterstützt eine Vielzahl von App-Typen, einschließlich Web-Apps. Bei einer Web-App handelt es sich um eine Client/Server-Anwendung. Der Server stellt die Web-App bereit, welche die Benutzeroberfläche, den Inhalt und die Funktionen umfasst. Außerdem bieten moderne Webhostingplattformen häufig Vorteile bei Sicherheit und Lastenausgleich. Eine Web-App wird separat im Web verwaltet. Verwenden Sie Microsoft Intune, um auf diesen App-Typ zu verweisen. Sie legen ebenfalls fest, welche Benutzergruppen auf diese App zugreifen können. 

Bevor Sie eine App verwalten und Benutzern zuweisen können, müssen Sie diese in Intune hinzufügen. Intune erstellt eine Verknüpfung zu der Web-App auf dem Startbildschirm des Geräts des Benutzers.

> [!Note]
> Web-Apps werden nicht für Android for Work- und macOS-Geräte unterstützt.

## <a name="add-a-web-app-to-intune"></a>Hinzufügen einer Web-App zu Intune
Führen Sie die folgenden Schritte aus, um eine App als Verknüpfung zu einer App im Internet zu Intune hinzuzufügen:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**.  
    Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Mobile Apps**.
4. Wählen Sie im Arbeitsbereich **Mobile Apps** unter **Verwalten** die Option **Apps** aus.
5. Klicken Sie im Bereich **Apps** auf **Hinzufügen**.
6. Wählen Sie im Bereich **App hinzufügen** aus der Dropdownliste **App-Typ** den Typ **Weblink** aus.
7. Klicken Sie auf **Konfigurieren**.
8. Fügen Sie im Bereich **App-Informationen** die folgenden Informationen hinzu:
    - **Name**: Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt werden soll.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein. Die Beschreibung wird Benutzern im Unternehmensportal angezeigt.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers dieser App ein.
    - **App-URL**: Geben Sie die URL der Website ein, auf der die zuzuweisende App gehostet wird.
    - **Kategorie**: Wählen Sie optional mindestens eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch ist es für Benutzer einfacher, die App im Unternehmensportal zu finden.
    - **Display this as a featured app in the Company Portal** (Diese App als ausgewählte App im Unternehmensportal anzeigen): Diese Einstellung zeigt die App-Suite auf der Hauptseite des Unternehmensportals hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Fordern Sie zum Öffnen dieses Links Managed Browser an**: Mit dieser Einstellung wird den Benutzern ein Link zu einer Website oder Web-App zugewiesen, den sie in Intune Managed Browser öffnen können. Dieser Browser muss auf ihrem Gerät installiert sein.
    - **Logo**: Laden Sie ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
9. Wählen Sie **OK** aus.
10. Klicken Sie anschließend im Bereich **App hinzufügen** auf **Hinzufügen**.

> [!Note]
> Benutzer müssen dem Startbildschirm das Intune-Widget hinzufügen, um Web-Apps anzuzeigen, die Android-Geräten zugewiesen wurden.

## <a name="next-steps"></a>Nächste Schritte

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md). 
