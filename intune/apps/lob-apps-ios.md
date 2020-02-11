---
title: Hinzufügen von branchenspezifischen iOS-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie eine branchenspezifische (Line-of-Business, LOB) iOS-App zu Microsoft Intune hinzufügen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0b7c0a7dfa4337983c12ada2d0f415c771bd0548
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755186"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>Hinzufügen von branchenspezifischen iOS-Apps zu Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Fügen Sie mithilfe der Informationen in diesem Artikel branchenspezifische (LOB) iOS-Apps zu Microsoft Intune hinzu. Eine branchenspezifische App (LOB) ist eine App, die Sie aus einer IPA-App-Installationsdatei zu Intune hinzufügen. Diese Art von App wird in der Regel intern geschrieben. Sie müssen zunächst dem iOS Developer Enterprise Program beitreten. Weitere Informationen hierzu finden Sie auf der [Apple-Website](https://developer.apple.com/programs/ios/enterprise/).

>[!NOTE]
>Benutzer von iOS-Geräten können einige der integrierten iOS-Apps wie Stocks und Maps entfernen. Über Intune können diese Apps jedoch nicht erneut bereitgestellt werden. Wenn Benutzer diese Apps löschen, müssen sie zum App Store navigieren und die Apps manuell erneut installieren.
>
>Für branchenspezifische iOS-Apps gilt das Größenlimit von maximal 4 GB pro App.

## <a name="select-the-app-type"></a>Auswählen des App-Typs

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus.
3. Wählen Sie im Bereich **App-Typ auswählen** unter den App-Typen **Sonstige** die Option **Branchenspezifische App** aus.
4. Klicken Sie auf **Auswählen**. Die **App hinzufügen**-Schritte werden angezeigt.

## <a name="step-1---app-information"></a>Schritt 1: App-Informationen

### <a name="select-the-app-package-file"></a>Auswählen der App-Paketdatei

1. Klicken Sie im Bereich **App hinzufügen** auf **App-Paketdatei auswählen**. 
2. Wählen Sie im Bereich **App-Paketdatei** die Schaltfläche zum Durchsuchen. Wählen Sie dann eine iOS-Installationsdatei mit der Erweiterung **IPA**.
   Die App-Details werden angezeigt.
3. Wenn Sie fertig sind, wählen Sie im Bereich **App-Paketdatei** die Option **OK** aus, um die App hinzuzufügen.

### <a name="set-app-information"></a>Festlegen von App-Informationen

1. Fügen Sie auf der Seite **App-Informationen** die Details zu Ihrer App hinzu. Abhängig von der ausgewählten App wurden einige der Werte in diesem Bereich möglicherweise automatisch ausgefüllt.
    - **Name:** Geben Sie den Namen der App so ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein. Die Beschreibung wird im Unternehmensportal angezeigt.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.
    - **Mindestens erforderliches Betriebssystem**: Wählen Sie aus der Liste die mindestens erforderliche Betriebssystemversion aus, unter der die App installiert werden kann. Wenn Sie die App einem Gerät mit einem älteren Betriebssystem zuweisen, wird sie nicht installiert.
    - **Kategorie**: Wählen Sie eine oder mehrere der integrierten oder von Ihnen erstellten App-Kategorien aus. Kategorien erleichtern es dem Benutzer, die App über das Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Präsentieren Sie die App herausgehoben auf der Hauptseite des Unternehmensportals, wenn die Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Die URL wird im Unternehmensportal angezeigt.
    - **URL der Datenschutzrichtlinien:** Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Die URL wird im Unternehmensportal angezeigt.
    - **Entwickler**: Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer**: Geben Sie optional einen Namen für den Besitzer dieser App ein. Ein Beispiel ist **Personalabteilung**.
    - **Anmerkungen**: Geben Sie Hinweise zu dieser App ein.
    - **Logo**: Laden Sie ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
2. Klicken Sie auf **Weiter**, um die Seite **Bereichsmarkierungen** anzuzeigen.

## <a name="step-2---select-scope-tags-optional"></a>Schritt 2: Auswählen von Bereichsmarkierungen (optional)
Sie können Bereichsmarkierungen verwenden, um zu bestimmen, wer Client-App-Informationen in Intune anzeigen kann. Ausführliche Informationen zu Bereichsmarkierungen finden Sie unter [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md) (Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen für verteilte IT).

1. Klicken Sie auf **Bereichstags auswählen**, um optional Bereichsmarkierungen für die App hinzuzufügen. 
2. Klicken Sie auf **Weiter**, um die Seite **Zuweisungen** anzuzeigen.

## <a name="step-3---assignments"></a>Schritt 3: Zuweisungen

1. Wählen Sie die Gruppenzuweisungen **Erforderlich**, **Für registrierte Geräte verfügbar** oder **Deinstallieren** für die App aus. Weitere Informationen finden Sie unter [Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten](~/fundamentals/groups-add.md) und [Zuweisen von Apps zu Gruppen mit Microsoft Intune](apps-deploy.md).
2. Klicken Sie auf **Weiter**, um die Seite **Überprüfen + erstellen** anzuzeigen. 

## <a name="step-4---review--create"></a>Schritt 4: Überprüfen und Erstellen

1. Überprüfen Sie die Werte und Einstellungen, die Sie für die App eingegeben haben.
2. Klicken Sie abschließend auf **Erstellen**, um Intune die App hinzuzufügen.

    Das Blatt **Übersicht** für die branchenspezifische App wird angezeigt.

Die von Ihnen erstellte App wird nun in der Liste der Apps angezeigt. Sie können die App über die Liste den von Ihnen ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

> [!NOTE]
> Bei Bereitstellungsprofilen für branchenspezifische iOS-Apps gibt es eine Mitteilung für 30 Tage, bevor sie ablaufen.

## <a name="step-5-update-a-line-of-business-app"></a>Schritt 5: Aktualisieren einer branchenspezifischen App

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

Das Update für die branchenspezifische App wird automatisch installiert.

> [!NOTE]
> Damit der Intune-Dienst erfolgreich eine neue IPA-Datei auf dem Gerät bereitstellt, müssen Sie die Zeichenfolge `CFBundleVersion` in der Datei „Info.plist“ in Ihrem IPA-Paket schrittweise erhöhen.

## <a name="next-steps"></a>Nächste Schritte

- Die von Ihnen erstellte App wird in der Liste der Apps angezeigt. Sie können sie jetzt den ausgewählten Gruppen zuweisen. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

- Erfahren Sie mehr darüber, wie Sie die Eigenschaften und Zuweisungen Ihrer App überwachen können. Siehe [Überwachen von App-Informationen und -Zuweisungen](apps-monitor.md).

- Erfahren Sie mehr über den Kontext Ihrer App in Intune. Siehe [Übersicht über die Lebenszyklen von Geräten und Apps](../fundamentals/device-lifecycle.md).
