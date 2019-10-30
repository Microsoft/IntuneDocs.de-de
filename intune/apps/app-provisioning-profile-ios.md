---
title: iOS-App-Bereitstellungsprofile in Microsoft Intune
titleSuffix: ''
description: Intune stellt Ihnen die Tools zum proaktiven Zuweisen eines neuen Bereitstellungsprofils auf Geräten zur Verfügung, auf denen Apps installiert sind, die bald ablaufen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/14/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c0b5f087494e8033cb9645d0a08edd4e1c481a2c
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584920"
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
2. Klicken Sie im Bereich **Intune** auf **Client-Apps** > **iOS-App-Bereitstellungsprofile** > **Profil erstellen**.
3. Fügen Sie auf der Seite **Basics** (Grundeinstellungen) die folgenden Werte hinzu:
    - **Name**: Geben Sie einen Namen für dieses mobile Bereitstellungsprofil an.
    - **Beschreibung**: Geben Sie optional eine Beschreibung der Richtlinie ein.
    - **Profildatei hochladen:** Klicken Sie auf das Symbol **Öffnen**, und wählen Sie eine Datei mit einem Konfigurationsprofil für Apple-Mobilgeräte (mit der Erweiterung `.mobileprovision`) aus, die Sie von der [Apple Developer-Website](https://developer.apple.com/) heruntergeladen haben.

   Das **Ablaufdatum** wird mit einem Wert aus der Datei mit einem Konfigurationsprofil für Apple-Mobilgeräte aufgefüllt, die Sie oben hinzugefügt haben.<br>

   <img alt="Create profile - Basics" src="~/apps/media/app-provisioning-profile-ios/app-provisioning-profile-ios-01.png">

4. Klicken Sie auf **Weiter: Bereichstags**.<br>
   Auf der Seite **Bereichstags** können Sie optional Bereichstags konfigurieren, um zu bestimmen, wer das iOS-App-Bereitstellungsprofil in Intune sehen kann. Weitere Informationen zu Bereichsmarkierungen finden Sie unter [Use role-based access control and scope tags for distributed IT (Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen für verteilte IT)](../fundamentals/scope-tags.md).
5. Klicken Sie auf **Weiter: Zuweisungen**.<br>
   Auf der Seite **Zuweisungen** können Sie das Profil Benutzern und Geräten zuweisen. Beachten Sie unbedingt, dass Sie einem Gerät unabhängig davon ein Profil zuweisen können, ob das Gerät von Intune verwaltet wird oder nicht.
6. Klicken Sie auf **Weiter: Überprüfen + erstellen**, um die für das Profil eingegebenen Werte zu überprüfen.
7. Sobald Sie damit fertig sind, klicken Sie auf **Erstellen**, um das iOS-App-Bereitstellungsprofil in Intune zu erstellen. 

## <a name="next-steps"></a>Nächste Schritte

Weisen Sie das Profil den entsprechenden iOS-Geräten zu. Weitere Informationen und Anweisungen finden Sie unter [Zuweisen von Geräteprofilen](../device-profile-assign.md).
