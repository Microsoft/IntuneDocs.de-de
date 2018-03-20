---
title: "Hinzufügen von Web-Apps in Microsoft Intune"
titleSuffix: 
description: "Erfahren Sie mehr über das Hinzufügen von Web-Apps in Microsoft Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ecb44f8b98501f6c82f91994cd8a06b8177208d7
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>Hinzufügen von Web-Apps in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune unterstützt eine Vielzahl von App-Typen, einschließlich Web-Apps. Bei einer Web-App handelt es sich um eine Client/Server-Anwendung. Der Server stellt die Web-App bereit, welche die Benutzeroberfläche, den Inhalt und die Funktionen umfasst. Außerdem bieten moderne Webhostingplattformen häufig Vorteile bei Sicherheit und Lastenausgleich. Eine Web-App wird separat im Web verwaltet. Verwenden Sie Microsoft Intune, um auf diesen App-Typ zu verweisen. Sie legen ebenfalls fest, welche Benutzergruppen auf diese App zugreifen können. 

Bevor Sie eine App verwalten und Benutzern zuweisen können, müssen Sie diese in Intune hinzufügen. Intune erstellt eine Verknüpfung zu der Web-App auf dem Startbildschirm des Geräts des Benutzers.

> [!Note]
> Web-Apps werden nicht für Android for Work- und macOS-Geräte unterstützt.

Führen Sie die folgenden Schritte durch, um eine App als Verknüpfung zu einer App im Internet zu Intune hinzuzufügen:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Microsoft Intune** auf die Option **Mobile Apps**.
4. Klicken Sie im Bereich **Mobile Apps** auf die Option **Apps**.
5. Wählen Sie oberhalb der App-Liste **Hinzufügen** aus. Der Bereich **App hinzufügen** wird angezeigt.
6. Wählen Sie im Bereich **App hinzufügen** den Typ **Weblink** aus der Dropdownliste **App-Typ** aus.
7. Klicken Sie im Bereich **App-Informationen** auf die Option **Konfigurieren**.
8. Fügen Sie im Bereich **App-Informationen** die folgenden Informationen hinzu:
    - **Name**: Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt wird.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein. Diese Beschreibung wird den Endbenutzern im Unternehmensportal angezeigt.
    - **Herausgeber:** Geben Sie den Namen des Herausgebers dieser App ein.
    - **App-URL:** Geben Sie die URL der Website an, auf der die zuzuweisende App gehostet wird.
    - **Kategorie (optional):** Wählen Sie eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Durch diese Auswahl ist es für Benutzer einfacher, die App im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen:** Zeigen Sie die App auf der Hauptseite des Unternehmensportal hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Managed Browser zum Öffnen dieses Links anfordern:** Wenn Sie Benutzern einen Link zu einer Website oder Web-App zuweisen, können sie diesen in Intune Managed Browser öffnen. Dieser Browser muss auf ihrem Gerät installiert sein.
    - **Logo**: Laden Sie ein Logo für die App hoch. Dieses Logo wird gemeinsam mit der App angezeigt, wenn der Benutzer das Unternehmensportal durchsucht.
9. Klicken Sie dann im Bereich **Informationen hinzufügen** auf die Option **OK**.
10. Klicken Sie anschließend im Bereich **App hinzufügen** auf **Hinzufügen**.

> [!Note]
> Benutzer müssen Ihrem Startbildschirm das Intune-Widget hinzufügen, um Web-Apps anzuzeigen, die Android-Geräten zugewiesen wurden.

## <a name="next-steps"></a>Nächste Schritte

- Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).