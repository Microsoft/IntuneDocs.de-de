---
title: Konfigurationsrichtlinie für Android for Work-Apps
description: Verwenden Sie Konfigurationsrichtlinien für mobile Apps in Intune, um Einstellungen anzugeben, die beim Ausführen einer Android for Work-App durch Benutzer erforderlich sind.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 02/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7bebf6137b7378c52741195a1dce048caaa03e3d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="configure-android-for-work-apps-with-mobile-app-configuration-policies-in-microsoft-intune"></a>Konfigurieren von Apps mit Konfigurationsrichtlinien für mobile Apps in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Verwenden Sie Konfigurationsrichtlinien für mobile Apps in Microsoft Intune, um Einstellungen anzugeben, die beim Ausführen einer App durch Benutzer erforderlich sind. Beispielsweise kann eine App vom Benutzer Folgendes anfordern:

-   Eine benutzerdefinierte Portnummer
-   Spracheinstellungen
-   Brandingeinstellungen wie z. B. ein Unternehmenslogo

Wenn Benutzer Einstellungen nicht ordnungsgemäß eingeben, kann dies zur erhöhten Belastung Ihres Helpdesks führen und die Annahme der neuen Apps verlangsamen.

Mit Richtlinien zur Konfiguration von mobilen Apps können Sie diese Einstellungen auf Geräten bereitstellen, bevor Benutzer die App ausführen. Die Einstellungen werden automatisch bereitgestellt, und die Benutzer müssen keine weitere Aktion durchführen.

Damit Richtlinien für die App-Konfiguration verwendet werden können, muss der App-Entwickler beim Erstellen der App Konfigurationseinstellungen für Unternehmens-Apps verfügbar machen. Für Google Chrome werden beispielsweise Einstellungen bereitgestellt, mit denen Sie Standardlesezeichen, zulässige und verweigerte Websites und vieles mehr festlegen können. Wenden Sie sich an den Entwickler der App, um herauszufinden, ob diese Einstellungen unterstützt und wie sie in der Richtlinie angegeben werden.

Die Richtlinie für die App-Konfiguration stellen Sie für die Benutzer bereit, für die Sie die App bereitgestellt haben, die Sie konfigurieren möchten. App-Einstellungen werden angewendet, wenn die App ausgeführt wird.

## <a name="configure-a-mobile-app-configuration-policy"></a>Konfigurieren einer Konfigurationsrichtlinie für mobile Apps

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Optionen **Richtlinie** &gt; **Übersicht** &gt; **Richtlinie hinzufügen**.

2.  Erweitern Sie in der Liste der Richtlinien den Eintrag **Android for Work**, wählen Sie **Richtlinie zur Konfiguration mobiler Apps (Android for Work)** und anschließend **Richtlinie erstellen** aus.

    > [!TIP]
    > Sie können für diesen Richtlinientyp nur benutzerdefinierte Einstellungen konfigurieren. Empfohlene Einstellungen sind nicht verfügbar.

3.  Im Abschnitt **Allgemein** der Seite **Richtlinie erstellen** geben Sie einen Namen und eine optionale Beschreibung für die Konfigurationsrichtlinie für mobile Apps an.

4. Geben Sie im Abschnitt **Richtlinie zur Konfiguration mobiler Apps** der Seite die folgenden Informationen an:
    - **Paket-ID für die Anwendung, auf die diese Konfiguration angewendet wird**: Die Paket-ID finden Sie im Abschnitt „id=“ der App-URL auf der entsprechenden Google Play-Seite. Die Paket-ID der Microsoft Excel-App lautet z.B. **com.microsoft.office.excel**.
    - Geben Sie in das Textfeld die Daten für die App-Einstellungen ein, die Sie konfigurieren möchten. Diese Einstellungen erhalten Sie vom Anbieter der App. Nicht alle Apps unterstützen diese Einstellungen.
5.  Klicken Sie auf **Überprüfen** um sicherzustellen, dass die eingegebenen Daten einem gültigen Format für Eigenschaftenlisten entspricht.

    > [!IMPORTANT]
    > Beim Klicken auf **Überprüfen** prüft Intune, ob die von Ihnen eingegebenen Konfigurationsdaten in einem gültigen Format vorliegen. Es wird nicht überprüft, ob die Daten mit der App verwendet werden können, der sie zugeordnet sind.

6.  Klicken Sie abschließend auf **Richtlinie speichern**.

Die neue Richtlinie wird im Knoten **Konfigurationsrichtlinien** angezeigt.


## <a name="deploy-the-app-configuration-policy"></a>Bereitstellen der Richtlinie für die App-Konfiguration
Nachdem Sie die Richtlinie zur Konfiguration mobiler Apps erstellt haben, müssen Sie sie für die Benutzer bereitstellen, für die Sie die App bereitstellen, für die die Einstellungen gelten.

Informationen zum Bereitstellen von Richtlinien finden Sie unter [Bereitstellen einer Konfigurationsrichtlinie](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy).

Informationen zum Bereitstellen von Apps für Android for Work-Geräte finden Sie unter [How to deploy apps to Android for Work devices with Intune (Bereitstellen von Apps für Android for Work-Geräte mit Intune)](android-for-work-apps.md).

Wenn die bereitgestellte App auf einem Gerät gestartet wird, wird sie mit den Einstellungen ausgeführt, die Sie in der Konfigurationsrichtlinie für mobile Apps konfiguriert haben.

> [!TIP]
> Stellen Sie für jede App nur eine App-Konfigurationsrichtlinie für einen Benutzer bereit.
