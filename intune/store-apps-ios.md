---
title: "Hinzufügen von iOS Store-Apps in Microsoft Intune"
titlesuffix: 
description: "Erfahren Sie mehr über das Hinzufügen von iOS Store-Apps in Microsoft Intune."
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4bd10c4f05204d0e911a7538f5d5133e4a336320
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>Hinzufügen von iOS Store-Apps in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Fügen Sie mithilfe der Informationen in diesem Artikel iOS Store-Apps zu Microsoft Intune hinzu. iOS Store-Apps sind Apps, die von Intune auf einem Gerät des Benutzers installiert werden. Der Benutzer ist ein Mitarbeiter Ihres Unternehmens. iOS Store-Apps werden automatisch aktualisiert.

>[!NOTE]
>Während Benutzer von iOS-Geräten einige der integrierten iOS-Apps wie Stocks und Maps entfernen können, können Sie diese Apps über Intune nicht erneut bereitstellen. Wenn Endbenutzer diese Apps löschen, müssen sie zum App Store navigieren und die Apps manuell erneut installieren.

## <a name="before-you-start"></a>Vorbereitung

Sie können mit dieser Methode nur Apps zuweisen, die im App Store kostenlos angeboten werden. Wenn Sie mithilfe von Intune kostenpflichtige Apps zuweisen möchten, erwägen Sie die Nutzung des [iOS Volume Purchase Program](vpp-apps-ios.md).

>[!NOTE]
>Die Browser Chrome und Edge werden für die Arbeit mit Microsoft Intune empfohlen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie auf dem Blatt **Intune** die Option **Mobile Apps** aus.
4. Klicken Sie in der Workload **Mobile Apps** im Abschnitt **Verwalten** auf **Apps**.
5. Wählen Sie rechts von dem Bereich **Apps** die Option **Hinzufügen** aus.
6. Wählen Sie in der Liste **App-Typ** unter den verfügbaren Typen der **Store-Apps** die Option **iOS** aus.
7. Wählen Sie **Search the App Store** (App Store durchsuchen) aus.
8. Wählen Sie auf dem Blatt **App Store durchsuchen** das Gebietsschema des App Store aus.
9. Geben Sie den Namen (oder einen Teil des Namens) in das Suchfeld ein. Intune durchsucht den Store und gibt eine Liste mit relevanten Ergebnissen zurück.
10. Wählen Sie die gewünschte App aus der Liste aus, und klicken Sie anschließend auf **Auswählen**.
11. Wählen Sie auf dem Blatt **App hinzufügen** die Option **App-Informationen** aus, um die App zu konfigurieren.
12. Fügen Sie auf dem Blatt **App-Informationen** die App-Informationen hinzu. Abhängig von der ausgewählten App werden einige der Werte auf diesem Blatt möglicherweise automatisch ausgefüllt:
    - **Name**: Geben Sie den Namen der App ein, der im Unternehmensportal angezeigt werden soll. Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, zeigt das Unternehmensportal den Benutzern nur eine der Apps an.
    - **Beschreibung**: Geben Sie eine Beschreibung für die App ein, die den Benutzern im Unternehmensportal angezeigt werden soll.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.
    - **App Store-URL**: Geben Sie die App Store-URL der App ein, die Sie erstellen möchten.
    - **Mindestens erforderliches Betriebssystem**: Wählen Sie aus der Liste die mindestens erforderliche Betriebssystemversion aus, auf der die App installiert werden kann. Die App wird auf einem Gerät mit einem älteren Betriebssystem nicht installiert.
    - **Verwendbarer Gerätetyp**: Wählen Sie die Geräte aus der Liste aus, die von der App verwendet werden.
    - **Kategorie** (optional). Wählen Sie eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Kategorien erleichtern es dem Benutzer, die App im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Zeigen Sie die App auf der Hauptseite des Unternehmensportals hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Die URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Die URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Geben Sie optional den Namen des App-Entwicklers ein. Dieses Feld ist nur für Administratoren sichtbar, für Endbenutzer nicht.
    - **Besitzer**: Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. **Personalabteilung**.  Dieses Feld ist nur für Administratoren sichtbar, für Endbenutzer nicht.
    - **Anmerkungen**: Geben Sie Hinweise zu dieser App ein. Dieses Feld ist nur für Administratoren sichtbar, für Endbenutzer nicht.
    - **Logo**: Laden Sie ein Symbol für die App hoch. Das Symbol wird gemeinsam mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
13. Klicken Sie dann auf dem Blatt **App-Informationen** auf **OK**.
14. Klicken Sie auf dem Blatt **App hinzufügen** auf **Hinzufügen**.

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können.

## <a name="next-steps"></a>Nächste Schritte

- [Zuweisen von Apps zu Gruppen](apps-deploy.md)
