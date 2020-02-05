---
title: Hinzufügen von Microsoft Edge zu macOS-Geräten mit Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie mit Microsoft Intune Microsoft Edge zu macOS-Geräten hinzufügen können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ebcb81cd0f186a3fd23e0701d12ea871eab129a
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912570"
---
# <a name="add-microsoft-edge-to-macos-devices-using-microsoft-intune"></a>Hinzufügen von Microsoft Edge zu macOS-Geräten mit Microsoft Intune

Bevor Sie Apps bereitstellen, konfigurieren, überwachen oder schützen können, müssen Sie sie zu Intune hinzufügen. Einer der verfügbaren [App-Typen](~/apps/apps-add.md#app-types-in-microsoft-intune) ist Microsoft Edge *Version 77 und höher*. Wenn Sie den App-Typ in Intune auswählen, können Sie Microsoft Edge *Version 77 und höher* zuweisen und auf Geräten mit macOS installieren. Dieser App-Typ erleichtert Ihnen das Zuweisen von Microsoft Edge zu macOS-Geräten, ohne dass Sie das macOS App Wrapping Tool verwenden müssen. Diese Apps sind auch im Lieferumfang von Microsoft AutoUpdate (MAU) enthalten, um die App sicherer und auf dem neuesten Stand zu halten.

> [!IMPORTANT]
> Dieser App-Typ befindet sich in der **öffentlichen Vorschau** und bietet Entwickler- und Beta-Channels für macOS an. Die Bereitstellung ist nur in englischer Sprache verfügbar, Endbenutzer können die Anzeigesprache im Browser jedoch unter **Einstellungen** > **Sprachen** ändern. 

> [!NOTE]
> Microsoft Edge *Version 77 und höher* ist auch für Windows 10 verfügbar.

## <a name="prerequisites"></a>Voraussetzungen
- Auf dem macOS-Gerät muss macOS 10.12 oder höher ausgeführt werden, bevor Microsoft Edge installiert werden kann.

## <a name="add-microsoft-edge-to-intune"></a>Hinzufügen von Microsoft Edge zu Intune
Mithilfe der folgenden Schritte können Sie Microsoft Edge, Version 77 und höher, zu Intune hinzufügen:

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus.
3. Wählen Sie in der Liste **App-Typ** unter **Microsoft Edge, Version 77 und höher** die Option **macOS** aus.

## <a name="configure-app-information"></a>Konfigurieren von App-Informationen
In diesem Schritt stellen Sie Informationen über diese App-Bereitstellung bereit. Diese Informationen helfen Ihnen, die App in Intune zu identifizieren, und Endbenutzer können sie leichter im Unternehmensportal finden.

1. Klicken Sie auf **App-Informationen**, um den Bereich **App-Informationen** anzuzeigen.
2. Stellen Sie im Bereich **App-Informationen** Informationen über diese App-Bereitstellung bereit. Diese Informationen helfen Ihnen, die App in Intune zu identifizieren, und Endbenutzer können sie leichter im Unternehmensportal finden.
    - **Name:** Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt wird. Stellen Sie sicher, dass alle Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung der App ein. Beispielsweise können Sie die Zielbenutzer in der Beschreibung auflisten.
    - **Herausgeber**: Als Herausgeber wird Microsoft angezeigt.
    - **Kategorie**: Wählen Sie optional eine oder mehrere der integrierten oder von Ihnen erstellten App-Kategorien aus. Diese Einstellung erleichtert den Benutzern die Suche nach der App im Unternehmensportal.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen**: Wählen Sie diese Option aus, um die App auf der Hauptseite des Unternehmensportals hervorgehoben anzuzeigen, wenn die Benutzer nach Apps suchen.
    - **Informations-URL**: Geben Sie optional eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen**: Geben Sie optional eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird Benutzern im Unternehmensportal angezeigt.
    - **Entwickler**: Als Entwickler wird Microsoft angezeigt.
    - **Besitzer**: Als Besitzer wird Microsoft angezeigt.
    - **Anmerkungen**: Geben Sie optional Hinweise zu dieser App ein.
3. Klicken Sie auf **OK**.

## <a name="configure-microsoft-edge-settings"></a>Konfigurieren von Microsoft Edge-Einstellungen
In diesem Schritt konfigurieren Sie Installationsoptionen für die App.

1. Wählen Sie im Bereich **App hinzufügen** die Option **App-Einstellungen** aus.
2. Wählen Sie im Bereich **App-Einstellungen** entweder **Stabil**, **Beta** oder **Dev** aus der Liste **Kanal** aus, um festzulegen, über welchen Edge-Kanal Sie die App bereitstellen.

    - Der Kanal **Stabil** wird für die umfassende Bereitstellung in Unternehmensumgebungen empfohlen. Der Kanal wird alle sechs Wochen aktualisiert, und jedes Release umfasst Verbesserungen aus dem Betakanal.
    - Der Kanal **Beta** ist die stabilste Microsoft Edge-Vorschauversion und damit die beste Wahl für ein vollständiges Pilotprojekt in Ihrer Organisation. Der Kanal bietet alle sechs Wochen umfassende Updates, und jedes Release umfasst die Erkenntnisse und Verbesserungen aus dem Entwicklerkanal.
    - Der Kanal für **Entwickler** dient für Unternehmensfeedback zu Windows, Windows Server und macOS. Er wird wöchentlich aktualisiert und enthält die neuesten Verbesserungen und Fehlerbehebungen.

    > [!NOTE]
    > Das Microsoft Edge-Browserlogo wird gemeinsam mit der App angezeigt, wenn der Benutzer das Unternehmensportal durchsucht.

3.  Klicken Sie auf **OK**.

## <a name="select-scope-tags-optional"></a>Auswählen von Bereichsmarkierungen (optional)
Sie können Bereichsmarkierungen verwenden, um zu bestimmen, wer Client-App-Informationen in Intune anzeigen kann. Ausführliche Informationen zu Bereichsmarkierungen finden Sie unter „Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen für verteilte IT“.
1.  Wählen Sie **Scope (Tags)**  > **Add** (Bereich (Markierungen) > Hinzufügen) aus.
2.  Verwenden Sie das Feld **Auswählen**, um nach Bereichsmarkierungen zu suchen.
3.  Aktivieren Sie das Kontrollkästchen neben den Bereichsmarkierungen, die Sie dieser App zuweisen möchten.
4.  Klicken Sie auf **Auswählen** > **OK**.

## <a name="add-the-app"></a>Hinzufügen der App
Wenn Sie die Konfiguration abgeschlossen haben, wählen Sie **Hinzufügen** im Bereich **App hinzufügen** aus. 

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können. 

> [!NOTE]
> Apple bietet derzeit keine Möglichkeit, Microsoft Edge auf macOS-Geräten mit Intune zu deinstallieren.

## <a name="next-steps"></a>Nächste Schritte
- Informationen zum Konfigurieren von Microsoft Edge auf macOS-Geräten finden Sie unter [Konfigurieren von Microsoft Edge auf macOS-Geräten](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac).
- Informationen zum Ein- und Ausschließen von App-Zuweisungen für Gruppen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](~/apps/apps-inc-exl-assignments.md).
- [Das Zuweisen von Apps zu Gruppen](~/apps/apps-deploy.md)

