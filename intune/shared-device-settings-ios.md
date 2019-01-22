---
title: 'Anpassen des Sperrbildschirms auf iOS-Geräten mithilfe von Microsoft Intune: Azure | Microsoft-Dokumentation'
titlesuffix: ''
description: Erfahren Sie mehr über die Microsoft Intune-Einstellungen zur Anzeige von Informationen auf dem Sperrbildschirm von iOS-Geräten mithilfe der Konfigurationseinstellungen für freigegebene Geräte für iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9f4d75d795421c761398f349c324b498fd21ca01
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203075"
---
# <a name="add-custom-messages-to-lock-screen-and-login-window-on-ios-devices-using-microsoft-intune"></a>Hinzufügen benutzerdefinierter Nachrichten zum Sperrbildschirm und Anmeldefenster auf iOS-Geräten mithilfe von Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel erfahren Sie mehr über die Microsoft Intune-Einstellungen zur Anzeige von Informationen auf dem Sperrbildschirm und im Anmeldefenster von iOS-Geräten. 

Verwenden Sie diese Einstellungen, um eine benutzerdefinierte Nachricht oder einen Text im Anmeldefenster und auf dem Sperrbildschirm anzuzeigen. So können Sie z.B. eine „Wenn verloren, zurück an“-Nachricht und Bestandskennzeicheninformationen eingeben.

Diese Einstellungen unterstützen überwachte Geräte, auf denen iOS 9.3 oder höher ausgeführt wird.

## <a name="create-the-profile"></a>Erstellen des Profils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie einen **Namen** und eine **Beschreibung** für das Profil ein.
4. Wählen Sie in **Plattform** die Option **iOS** aus. Wählen Sie in **Profiltyp** die Option **Gerätefunktionen** aus.
5. Wählen Sie in **Einstellungen** die Option **Nachricht auf Sperrbildschirm (nur überwacht)**  aus. Konfigurieren Sie die folgenden Einstellungen:

    - **Bestandskennzeicheninformationen:** Geben Sie Informationen zum Bestandskennzeichen des Geräts ein. Geben Sie beispielsweise `123xyz` ein.

        Der von Ihnen eingegebene Text wird im Anmeldefenster und Sperrbildschirm auf dem Gerät angezeigt.

    - **Fußnote im Sperrbildschirm:** Geben Sie einen Hinweis ein, der Ihnen helfen könnte, das Gerät zurückzubekommen, wenn es verloren geht oder gestohlen wird. In dem Feld können Sie einen beliebigen Text eingeben. Geben Sie zum Beispiel `If found, call Contoso at ...` ein.

    Gerätetoken können auch verwendet werden, um gerätespezifische Informationen zu diesen Feldern hinzuzufügen. Geben Sie zum Beispiel zur Anzeige der Seriennummer `Serial Number: {{serialnumber}}` ein. Auf dem Sperrbildschirm sieht der Text dann in etwa so aus: `Serial Number 123456789ABC`. Achten Sie darauf, bei der Eingabe von Variablen geschweifte Klammern `{{ }}` zu verwenden. [App-Konfigurationstoken](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) umfassen eine Reihe von Variablen, die Sie nutzen können. Zudem können Sie `deviceName` oder einen anderen gerätespezifischen Wert verwenden.

6. Wählen Sie abschließend **OK** > **OK** > **Erstellen** aus. Ihr Profil wird in der Liste angezeigt.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).
