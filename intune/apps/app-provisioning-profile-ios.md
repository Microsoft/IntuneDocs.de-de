---
title: iOS-App-Bereitstellungsprofile in Microsoft Intune
titleSuffix: ''
description: Intune stellt Ihnen die Tools zum proaktiven Zuweisen eines neuen Bereitstellungsprofils auf Geräten zur Verfügung, auf denen Apps installiert sind, die bald ablaufen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 624c6cec2a887396cb6ef6508ab26a16d72f8f7c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725321"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Verwenden von Bereitstellungsprofilen für iOS-Apps, um zu verhindern, dass Apps ablaufen

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

## <a name="introduction"></a>Einführung

Die iPhones und iPads zugewiesenen branchenspezifischen Apple iOS-Apps wurden mit integriertem Bereitstellungsprofil und per Zertifikat signiertem Code erstellt. Beim Ausführen der App bestätigt iOS die Integrität der iOS-App und erzwingt Richtlinien, die durch das Bereitstellungsprofil definiert werden. Folgende Überprüfungen finden statt:

- **Integrität der Installationsdateien**: iOS vergleicht die Details der App mit dem öffentlichen Schlüssel des Unternehmenssignaturzertifikats. Wenn Unterschiede festgestellt werden, wird der Inhalt der App möglicherweise verändert, und die Ausführung der App wird nicht zugelassen.
- **Erzwingen von Funktionen**: iOS versucht, die App-Funktionen aus dem Bereitstellungsprofil des Unternehmens (nicht den Bereitstellungsprofilen der einzelnen Entwickler) zu erzwingen, die in der App-Installationsdatei (IPA) enthalten sind.


Das Unternehmenssignaturzertifikat, das Sie zum Signieren von Apps verwenden, ist in der Regel drei Jahre lang gültig. Allerdings läuft das Bereitstellungsprofil nach einem Jahr ab. Während das Zertifikat noch gültig ist, stellt Intune Ihnen die Tools zum proaktiven Zuweisen eines neuen Bereitstellungsprofils auf Geräten zur Verfügung, auf denen Apps installiert sind, die bald ablaufen.
Nach Ablauf des Zertifikats müssen Sie die App mit einem neuen Zertifikat erneut signieren und ein neues Bereitstellungsprofil mit dem Schlüssel des neuen Zertifikats einbetten.

Wenn Sie über Administratorberechtigungen verfügen, können Sie Sicherheitsgruppen hinzufügen oder entfernen, um in iOS-Apps Bereitstellungskonfigurationen zuzuweisen. Sie können z.B. in iOS-Apps „Allen Benutzern“ Bereitstellungskonfigurationen zuweisen, aber gleichzeitig eine ausführende Gruppe davon ausschließen.

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Erstellen eines Bereitstellungsprofils für mobile iOS-Apps

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** die Option **Client-Apps** aus.
1. Wählen Sie in der Workload **Client-Apps** die Option **Verwalten** > **iOS-App-Bereitstellungsprofile** aus.
2. Klicken Sie in dem Bereich mit der Profilliste auf die Option **Profil erstellen**.
3. Konfigurieren Sie im Bereich **Profil erstellen** folgende Werte:
    - **Name**: Geben Sie einen Namen für dieses mobile Bereitstellungsprofil an.
    - **Beschreibung**: Geben Sie optional eine Beschreibung der Richtlinie ein.
    - **Profildatei hochladen:** Klicken Sie auf das Symbol **Öffnen**, und wählen Sie eine Datei mit einem Konfigurationsprofil für Apple-Mobilgeräte (mit der Erweiterung `.mobileprovision`) aus, die Sie von der [Apple Developer-Website](https://developer.apple.com/) heruntergeladen haben.
4. Wählen Sie abschließend **Erstellen** aus.

## <a name="next-steps"></a>Nächste Schritte

Weisen Sie das Profil den entsprechenden iOS-Geräten zu. Weitere Informationen und Anweisungen finden Sie unter [Zuweisen von Geräteprofilen](../device-profile-assign.md).
