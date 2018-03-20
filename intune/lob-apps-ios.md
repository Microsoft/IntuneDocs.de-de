---
title: "Hinzufügen von branchenspezifischen iOS-Apps zu Microsoft Intune"
titlesuffix: 
description: "Erfahren Sie mehr über das Hinzufügen von branchenspezifischen iOS-Apps zu Microsoft Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 225d598cfeb1c358131365efd1664dbdd9a76a5c
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-ios-line-of-business-lob-apps-to-microsoft-intune"></a>Hinzufügen von branchenspezifischen iOS-Apps in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Fügen Sie mithilfe der Informationen in diesem Artikel branchenspezifische iOS-Apps zu Microsoft Intune hinzu.

>[!NOTE]
>Während Benutzer von iOS-Geräten einige der integrierten iOS-Apps wie Stocks und Maps entfernen können, können Sie diese Apps über Intune nicht erneut bereitstellen. Wenn Endbenutzer diese Apps löschen, müssen sie zum App Store navigieren und die Apps manuell erneut installieren.

## <a name="step-1---specify-the-software-setup-file"></a>Schritt 1: Angeben der Softwaresetupdatei

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Mobile Apps**.
4. Wählen Sie in der Workload **Mobile Apps** die Option **Verwalten** > **Apps** aus.
5. Wählen Sie über der Liste der Apps **Hinzufügen** aus.
6. Klicken Sie im Bereich **App hinzufügen** auf die Option **Branchenspezifische App**.

## <a name="step-2---configure-the-app-package-file"></a>Schritt 2: Konfigurieren der App-Paketdatei

1. Klicken Sie im Bereich **App hinzufügen** auf die Option **App-Paketdatei**.
2. Klicken Sie im Bereich **App-Paketdatei** auf die Schaltfläche „Durchsuchen“, und wählen Sie eine iOS-Installationsdatei mit der Erweiterung **.ipa** aus.
3. Wenn Sie fertig sind, wählen Sie **OK** aus.


## <a name="step-3---configure-app-information"></a>Schritt 3: Konfigurieren von App-Informationen

1. Klicken Sie im Bereich **App hinzufügen** auf die Option **App-Informationen**.
2. Fügen Sie im Bereich **App-Informationen** Details zu Ihrer App hinzu. Abhängig von der ausgewählten App wurden einige der Werte in diesem Bereich möglicherweise automatisch ausgefüllt:
    - **Name:** Geben Sie den Namen der App ein, der im Unternehmensportal angezeigt werde soll. Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein, die den Benutzern im Unternehmensportal angezeigt werden soll.
    - **Herausgeber:** Geben Sie den Namen des Herausgebers der App ein.
    - **Mindestens erforderliches Betriebssystem:** Wählen Sie in der Liste die mindestens erforderliche Betriebssystemversion aus, auf der die App installiert werden kann. Wenn Sie die App einem Gerät mit einem älteren Betriebssystem zuweisen, wird sie nicht installiert.
    - **App-Version ignorieren:** Legen Sie **Ja** fest, wenn die App automatisch vom Entwickler aktualisiert wird.
    - **Kategorie:** Wählen Sie eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Dadurch ist es für Benutzer einfacher, die App im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen:** Zeigen Sie die App auf der Hauptseite des Unternehmensportal hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL:** Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen:** Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler:** Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer:** Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. **Personalabteilung**.
    - **Anmerkungen:** Geben Sie Hinweise zu dieser App ein.
    - **Logo:** Laden Sie ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird gemeinsam mit der App angezeigt, wenn der Benutzer das Unternehmensportal durchsucht.
3. Wenn Sie fertig sind, wählen Sie **OK** aus.

## <a name="step-4---finish-up"></a>Schritt 4: Fertig stellen

1. Prüfen Sie Ihre Angaben im Bereich **App hinzufügen**.
2. Wählen Sie **Hinzufügen** aus, um die App in Intune hochzuladen.

Die von Ihnen erstellte App erscheint in der Liste der Apps, in der Sie sie den ausgewählten Gruppen zuweisen können. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

## <a name="step-5---update-a-line-of-business-app"></a>Schritt 5: Aktualisieren einer branchenspezifischen App

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]  

> [!NOTE]
> Damit der Intune-Dienst erfolgreich eine neue IPA-Datei auf dem Gerät bereitstellt, müssen Sie die Zeichenfolge *CFBundleVersion* in der Datei *Info.plist* in Ihrem IPA-Paket schrittweise erhöhen.

## <a name="next-steps"></a>Nächste Schritte

- Die von Ihnen erstellte App wird in der Liste der Apps angezeigt. Sie können sie jetzt den ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

- Erfahren Sie mehr darüber, wie Sie die Eigenschaften und Zuweisungen Ihrer App überwachen können. Weitere Informationen finden Sie unter [Überwachen von App-Informationen und -Zuweisungen](apps-monitor.md).

- Erfahren Sie mehr über den Kontext Ihrer App in Intune. Weitere Informationen finden Sie unter [Übersicht über die Lebenszyklen von Geräten und Apps](introduction-device-app-lifecycles.md).
