---
title: App-Bereitstellungsprofile
description: Intune stellt Ihnen die Tools zum proaktiven Bereitstellen einer neuen Richtlinie für Bereitstellungsprofile auf Geräten zur Verfügung, auf denen Apps installiert sind, die bald ablaufen.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 86fbe736-7bdb-4f5e-ae21-13c91eb2462c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: cadd7070e8e3c7c0c5aca42324635af627f91e14
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="use-ios-mobile-provisioning-profile-policies-to-prevent-your-apps-from-expiring"></a>Verwenden von Richtlinien für mobile iOS-Bereitstellungsprofile, um zu verhindern, dass Apps ablaufen

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Die auf iPhones und iPads bereitgestellten branchenspezifischen Apple iOS-Apps wurden mit integriertem Bereitstellungsprofil und per Zertifikat signiertem Code erstellt. Beim Ausführen der App bestätigt iOS die Integrität der iOS-App und erzwingt Richtlinien, die durch das Bereitstellungsprofil definiert werden. Folgende Überprüfungen finden statt:

- **Integrität der Installationsdateien**: iOS vergleicht die Details der App mit dem öffentlichen Schlüssel des Unternehmenssignaturzertifikats. Wenn Unterschiede festgestellt werden, wurde der Inhalt der App möglicherweise verändert, und die Ausführung der App wird nicht zugelassen.
- **Erzwingen von Funktionen**: iOS versucht, die App-Funktionen aus dem Bereitstellungsprofil des Unternehmens (nicht den Bereitstellungsprofilen der einzelnen Entwickler) zu erzwingen, die in der App-Installationsdatei (IPA) enthalten sind.


Das Unternehmenssignaturzertifikat, das Sie zum Signieren von Apps verwenden, ist in der Regel drei Jahre lang gültig. Allerdings läuft das Bereitstellungsprofil nach einem Jahr ab. Während das Zertifikat noch gültig ist, stellt Intune Ihnen die Tools zum proaktiven Bereitstellen einer neuen Richtlinie für Bereitstellungsprofile auf Geräten zur Verfügung, auf denen Apps installiert sind, die bald ablaufen.
Nach Ablauf des Zertifikats müssen Sie die App mit einem neuen Zertifikat erneut signieren und ein neues Bereitstellungsprofil mit dem Schlüssel des neuen Zertifikats einbetten.



## <a name="how-to-find-out-when-a-line-of-business-app-will-expire"></a>Herausfinden, wann eine Branchen-App abläuft

1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Optionen **Apps** > **Apps** aus.
2. Überprüfen Sie in der App-Liste die Spalte **Ablaufdatum**, um das Ablaufdatum für die App zu ermitteln. Sie können auch die Dropdownliste **Filter** auf **Abgelaufen oder bald abgelaufen** festlegen, um nur die Apps anzuzeigen, für die Sie Maßnahmen ergreifen müssen.

## <a name="how-to-create-an-ios-mobile-provisioning-profile-policy"></a>Erstellen einer Richtlinie für mobile iOS-Bereitstellungsprofile


1. Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) auf **Richtlinie** > **Übersicht** > **Richtlinie hinzufügen**.
2. Wählen Sie im Dialogfeld **Neue Richtlinie erstellen** erst die Optionen **iOS** > **Richtlinie für mobiles Bereitstellungsprofil** und dann **Richtlinie erstellen** aus.
3. Konfigurieren Sie auf der Seite **Allgemein** die folgenden Werte:
    - **Name**: Stellen Sie einen Namen für diese Richtlinie für ein mobiles Bereitstellungsprofil bereit.
    - **Beschreibung**: Geben Sie optional eine Beschreibung der Richtlinie ein.
    - **Konfigurationsprofildatei**: Klicken Sie auf **Importieren**, und wählen Sie eine Datei mit einem mobilen Apple-Konfigurationsprofil (mit der Erweiterung **.mobileprovision**) aus, die Sie von der Apple Developer-Website heruntergeladen haben.
4. Wählen Sie abschließend **Richtlinie speichern** aus.
5. Stellen Sie jetzt die Richtlinie auf den erforderlichen iOS-Geräten bereit. Weitere Informationen finden Sie unter [Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).
