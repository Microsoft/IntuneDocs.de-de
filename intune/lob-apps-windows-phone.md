---
title: Hinzufügen branchenspezifischer Windows Phone-Apps zu Microsoft Intune
titlesuffix: ''
description: Erfahren Sie mehr über das Hinzufügen einer branchenspezifischen Windows Phone-App zu Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e86db15fb4c69b57a1dc572d5a7e4f06eee3b760
ms.sourcegitcommit: bea4a81d262607c6e9dd1e26f5cd1a2faf7d051b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2018
ms.locfileid: "45602111"
---
# <a name="add-a-windows-phone-line-of-business-app-to-microsoft-intune"></a>Hinzufügen branchenspezifischer Windows Phone-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Fügen Sie mithilfe der Informationen in diesem Artikel eine branchenspezifische Windows Phone-App zu Microsoft Intune hinzu. Eine branchenspezifische App (LOB) ist eine App, die Sie aus einer App-Installationsdatei zu Intune hinzufügen. Diese Art von App wird in der Regel intern geschrieben. Intune installiert die branchenspezifische App auf dem Gerät des Benutzers. 

## <a name="step-1-specify-the-software-setup-file"></a>Schritt 1: Angeben der Softwaresetupdatei

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** **Client-Apps** aus.
4. Wählen Sie in der Workload **Client-Apps** die Option **Verwalten** > **Apps** aus.
5. Wählen Sie oberhalb der App-Liste **Hinzufügen** aus.
6. Wählen Sie im Bereich **App hinzufügen** die Option **Branchenspezifische App** aus.

## <a name="step-2-configure-the-app-package-file"></a>Schritt 2: Konfigurieren der App-Paketdatei

1. Wählen Sie im Bereich **App hinzufügen** die Option **App-Paketdatei** aus.
2. Wählen Sie im Bereich **App-Paketdatei** die Schaltfläche zum Durchsuchen. Wählen Sie dann eine Windows Phone-Installationsdatei mit der Erweiterung **XAP**.
3. Wählen Sie danach **OK**.


## <a name="step-3-configure-app-information"></a>Schritt 3: Konfigurieren von App-Informationen

1. Wählen Sie im Bereich **App hinzufügen** die Option **App-Informationen**.
2. Konfigurieren Sie im Bereich **App-Informationen** die App-Informationen. Abhängig von der ausgewählten App wurden einige der Werte in diesem Bereich möglicherweise automatisch ausgefüllt.
    - **Name:** Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein. Die Beschreibung wird im Unternehmensportal angezeigt.
    - **Herausgeber:** Geben Sie den Namen des Herausgebers der App ein.
    - **App-Version ignorieren**: Legen Sie **Ja** fest, wenn der Entwickler die App automatisch aktualisiert.
    - **Kategorie:** Wählen Sie eine der integrierten oder von Ihnen erstellten App-Kategorien aus. Kategorien erleichtern es dem Benutzer, die App über das Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Zeigen Sie die App auf der Hauptseite des Unternehmensportals hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL:** Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Die URL wird im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen:** Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Die URL wird im Unternehmensportal angezeigt.
    - **Entwickler:** Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer:** Geben Sie optional einen Namen für den Besitzer dieser App ein. Ein Beispiel ist **Personalabteilung**.
    - **Anmerkungen:** Geben Sie Hinweise zu dieser App ein.
    - **Logo**: Laden Sie ein Symbol für die App hoch. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
3. Wählen Sie danach **OK**.

## <a name="step-4-finish-up"></a>Schritt 4: Fertig stellen

1. Überprüfen Sie im Bereich **App hinzufügen**, ob die konfigurierten Informationen richtig sind.
2. Wählen Sie **Hinzufügen**, um die App in Intune hochzuladen.

## <a name="next-steps"></a>Nächste Schritte

- Die von Ihnen erstellte App wird in der Liste der Apps angezeigt. Sie können sie jetzt den ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

- Erfahren Sie mehr darüber, wie Sie die Eigenschaften und Zuweisungen Ihrer App überwachen können. Siehe [Überwachen von App-Informationen und -Zuweisungen](apps-monitor.md).

- Erfahren Sie mehr über den Kontext Ihrer App in Intune. Siehe [Übersicht über die Lebenszyklen von Geräten und Apps](introduction-device-app-lifecycles.md).
