---
title: iOS-App-Bereitstellungsprofile in Microsoft Intune
titlesuffix: ''
description: Intune stellt Ihnen die Tools zum proaktiven Zuweisen eines neuen Bereitstellungsprofils auf Geräten zur Verfügung, auf denen Apps installiert sind, die bald ablaufen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bbc3ba4a-df48-4aeb-988b-69a177764e3a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5d3cc718c0bfd0bba68480b4cd4003cd52489a50
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225037"
---
# <a name="use-ios-app-provisioning-profiles-to-prevent-your-apps-from-expiring"></a>Verwenden von Bereitstellungsprofilen für iOS-Apps, um zu verhindern, dass Apps ablaufen

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>Einführung

Die iPhones und iPads zugewiesenen branchenspezifischen Apple iOS-Apps wurden mit integriertem Bereitstellungsprofil und per Zertifikat signiertem Code erstellt. Beim Ausführen der App bestätigt iOS die Integrität der iOS-App und erzwingt Richtlinien, die durch das Bereitstellungsprofil definiert werden. Folgende Überprüfungen finden statt:

- **Integrität der Installationsdateien**: iOS vergleicht die Details der App mit dem öffentlichen Schlüssel des Unternehmenssignaturzertifikats. Wenn Unterschiede festgestellt werden, wird der Inhalt der App möglicherweise verändert, und die Ausführung der App wird nicht zugelassen.
- **Erzwingen von Funktionen**: iOS versucht, die App-Funktionen aus dem Bereitstellungsprofil des Unternehmens (nicht den Bereitstellungsprofilen der einzelnen Entwickler) zu erzwingen, die in der App-Installationsdatei (IPA) enthalten sind.


Das Unternehmenssignaturzertifikat, das Sie zum Signieren von Apps verwenden, ist in der Regel drei Jahre lang gültig. Allerdings läuft das Bereitstellungsprofil nach einem Jahr ab. Während das Zertifikat noch gültig ist, stellt Intune Ihnen die Tools zum proaktiven Zuweisen eines neuen Bereitstellungsprofils auf Geräten zur Verfügung, auf denen Apps installiert sind, die bald ablaufen.
Nach Ablauf des Zertifikats müssen Sie die App mit einem neuen Zertifikat erneut signieren und ein neues Bereitstellungsprofil mit dem Schlüssel des neuen Zertifikats einbetten.

Wenn Sie über Administratorberechtigungen verfügen, können Sie Sicherheitsgruppen hinzufügen oder entfernen, um in iOS-Apps Bereitstellungskonfigurationen zuzuweisen. Sie können z.B. in iOS-Apps „Allen Benutzern“ Bereitstellungskonfigurationen zuweisen, aber gleichzeitig eine ausführende Gruppe davon ausschließen.

## <a name="how-to-create-an-ios-mobile-app-provisioning-profile"></a>Erstellen eines Bereitstellungsprofils für mobile iOS-Apps

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** die Option **Mobile Apps** aus.
1.  Wählen Sie in der Workload **Mobile Apps** die Option **Verwalten** > **iOS-App-Bereitstellungsprofile** aus.
2.  Wählen Sie in dem Bereich mit der Profilliste die Option **Profil erstellen** aus.
3. Konfigurieren Sie im Bereich **Profil erstellen** folgende Werte:
    - **Name**: Geben Sie einen Namen für dieses mobile Bereitstellungsprofil an.
    - **Beschreibung**: Geben Sie optional eine Beschreibung der Richtlinie ein.
    - **Profildatei hochladen**: Klicken Sie auf **Importieren**, und wählen Sie eine Datei mit einem mobilen Apple-Konfigurationsprofil (mit der Erweiterung **.mobileprovision**) aus, die Sie von der Apple Developer-Website heruntergeladen haben.
4. Wählen Sie abschließend **Erstellen** aus.

## <a name="next-steps"></a>Nächste Schritte

Weisen Sie das Profil den entsprechenden iOS-Geräten zu. Weitere Informationen und Anweisungen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).
