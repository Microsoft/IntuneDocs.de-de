---
title: Konfigurieren von App-Schutzrichtlinien während der Migration
titleSuffix: Microsoft Intune
description: Dieser Artikel gibt einen Überblick über die für die Einrichtung der App-Schutzrichtlinien notwendigen Schritte während einer Migration zu Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 183a1dc7083aa9b427df225297fb7c393939220f
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515049"
---
# <a name="configure-app-protection-policies-optional"></a>Konfigurieren von App-Schutzrichtlinien (optional)


Mit App-Schutzrichtlinien können Sie Folgendes tun:
* Apps verschlüsseln
* Definieren einer PIN, wenn auf die App zugegriffen wird
* Verhindern, das Apps auf Geräten, bei denen Nutzungsbeschränkungen entfernt wurden, ausgeführt werden und viele weitere Schutzmaßnahmen.

Wenn das Gerät des Benutzer verloren geht oder gestohlen wurde, können Sie die Unternehmensdaten remote selektiv zurücksetzen, ohne dass die persönlichen Daten davon betroffen wären.

App-Schutzrichtlinien wenden Sicherheitsmaßnahmen auf der Geräteebene an und erfordern keine Geräteregistrierung. Sie können sie sowohl für Geräte, die in Intune registriert sind, als auch für nicht registrierte Geräte verwenden. Des Weiteren können Sie auch für Geräte verwendet werden, die für Drittanbieter-MDM registriert sind.

## <a name="app-protection-policies-with-lob-apps"></a>App-Schutzrichtlinien für branchenspezifische Apps

Sie können die Schutzrichtlinien für mobile Apps auch auf branchenspezifische Apps ausweiten, indem Sie das [Microsoft Intune App SDK](../developer/app-sdk-get-started.md) oder das Microsoft Intune App Wrapping Tool für iOS/iPadOS- und Android-Plattformen verwenden. Weitere Informationen finden Sie unter [App Wrapping Tool für iOS](../developer/app-wrapper-prepare-ios.md) und [App Wrapping Tool für Android](./../developer/app-wrapper-prepare-android.md). Lesen Sie auch [Vorbereiten von branchenspezifischen Apps für den App-Schutz](../developer/apps-prepare-mobile-application-management.md).

## <a name="how-do-app-protection-policies-help-during-migration"></a>Wie helfen App-Schutzrichtlinien bei der Migration?

Bei der Migration müssen Sie Geräte vom alten MDM-Anbieter entfernen und in Intune registrieren. Dies sollten Sie berücksichtigen und Ihre Endbenutzer dazu anhalten, den alten MDM-Anbieter zu verlassen und sich umgehend in Intune zu registrieren. Bei der Migration kann es allerdings Benutzer geben, die den Abschluss des Registrierungsprozesses verzögern, weil Ihre Geräte von keinem der beiden MDM-Anbieter verwaltet werden.

In diesem Zeitraum kann Ihre Organisation anfälliger sein für den Geräteklau und den Verlust von Unternehmensdaten, wenn der Zugriff auf Unternehmensressourcen immer noch möglich ist. Außerdem kann die Benutzerproduktivität abnehmen, wenn der Zugriff auf Unternehmensressourcen blockiert ist.

Intune bietet Schutz für Unternehmensdaten während der Migration, damit Ihre Unternehmensdaten weiterhin geschützt sind, auch wenn es gerade keine Verwaltung auf der Geräteebene gibt.

Wenn Sie den bedingten Zugriff beim alten MDM-Anbieter deaktivieren, können Benutzer weiterhin produktiv arbeiten, während Sie das Onboarding der Benutzer in Intune durchführen.

## <a name="task-list-for-app-protection-policies"></a>Aufgabenliste für App-Schutzrichtlinien

- [Erstellen und Zuweisen von App-Schutzrichtlinien](~/apps/app-protection-policies.md)

## <a name="next-steps"></a>Nächste Schritte

[Besondere Überlegungen bei der Migration](migration-guide-considerations.md)
