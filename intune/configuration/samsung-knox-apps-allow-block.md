---
title: Microsoft Intune-Richtlinie zum Zulassen/Blockieren von Apps für Samsung KNOX
titleSuffix: ''
description: Erstellen eines benutzerdefinierten Profils zum Zulassen und Blockieren von Apps für Samsung KNOX Standard-Geräte
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b83a0339d87375502159467af323fceae5eb6e2
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207076"
---
# <a name="use-custom-policies-in-microsoft-intune-to-allow-and-block-apps-for-samsung-knox-standard-devices"></a>Verwenden von benutzerdefinierten Richtlinien zum Zulassen und Blockieren von Apps für Samsung KNOX Standardgeräte in Microsoft Intune 

Verwenden Sie die in diesem Artikel beschriebenen Verfahren, um eine benutzerdefinierte Microsoft Intune-Richtlinie zu erstellen, die eine der folgenden Listen erstellt:

- Eine Liste von Apps, deren Ausführung auf dem Gerät blockiert wird. Die Ausführung der Apps in dieser Liste wird blockiert, auch wenn diese bereits vor der Anwendung der Richtlinie installiert waren.
- Eine Liste der Apps, die Benutzer des Geräts aus dem Google Play Store installieren dürfen. Nur die aufgelisteten Apps können installiert werden. Es können keine anderen Apps aus dem Store installiert werden.

Diese Einstellungen können nur von Geräten verwendet werden, auf denen Samsung KNOX Standard ausgeführt wird.

## <a name="create-an-allowed-or-blocked-app-list"></a>Erstellen einer Liste mit zulässigen oder blockierten Apps

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.
3. Legen Sie folgende Einstellungen fest:

    - **Name:** Geben Sie einen aussagekräftigen Namen für das Profil ein. Benennen Sie Ihre Profile, damit Sie diese später leicht wiedererkennen. Ein guter Profilname ist beispielsweise das **benutzerdefinierte Profil von Windows Phone**.
    - **Beschreibung:** Geben Sie eine Beschreibung ein, die einen Überblick über die Einstellung und andere wichtige Details bietet.
    - **Plattform**: Wählen Sie **Android** aus.
    - **Profiltyp**: Wählen Sie **Benutzer**definiert aus.

4. Klicken Sie unter **Benutzerdefinierte OMA-URI-Einstellungen** auf **Hinzufügen**. Legen Sie folgende Einstellungen fest:

    Für eine Liste von Apps, deren Ausführung auf dem Gerät blockiert wird:

    - **Name:** Geben Sie **PreventStartPackages** ein.
    - **Beschreibung:** Geben Sie eine Beschreibung, die eine Übersicht über die Einstellung bietet, und andere relevante Informationen ein, die Ihnen die Suche nach dem Profil erleichtern. Beispiel: Geben Sie **die Liste der apps ein, deren Ausführung blockiert ist**.
    - **OMA-URI** (Groß-/Kleinschreibung beachten): Geben Sie **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/PreventStartPackages** ein.
    - **Datentyp**: Wählen Sie **String**aus.
    - **Wert:** Geben Sie eine Liste mit den Namen der App-Pakete ein, die Sie zulassen möchten. Sie können `;`, `:` oder `|` als Trennzeichen verwenden. Geben Sie beispielsweise `package1;package2;` ein.

   Für eine Liste von Apps, die Benutzer des Geräts aus Google Play Store installieren dürfen, wobei alle anderen Apps ausgeschlossen werden:

    - **Name:** Geben Sie **AllowInstallPackages** ein.
    - **Beschreibung**: Geben Sie eine Beschreibung, die eine Übersicht über die Einstellung bietet, und andere relevante Informationen ein, die Ihnen die Suche nach dem Profil erleichtern. Beispiel: Geben Sie eine **Liste von apps ein, die Benutzer aus Google Play installieren können**.
    - **OMA-URI** (Groß-/Kleinschreibung beachten): Geben Sie **./Vendor/MSFT/PolicyManager/My/ApplicationManagement/AllowInstallPackages** ein.
    - **Datentyp**: Wählen Sie **String**aus.
    - **Wert:** Geben Sie eine Liste mit den Namen der App-Pakete ein, die Sie zulassen möchten. Sie können `;`, `:` oder `|` als Trennzeichen verwenden. Geben Sie beispielsweise `package1;package2;` ein.

5. Klicken Sie auf **OK**, um die Änderungen zu speichern.
6. Klicken Sie anschließend auf **OK** > **Erstellen**, um das Intune-Profil zu erstellen. Das Profil wird erstellt und in der Liste **Gerätekonfiguration > Konfigurationsprofile** angezeigt.

>[!TIP]
> Sie finden die Paket-ID einer App, indem Sie im Google Play Store zu der App navigieren. Die Paket-ID ist in der URL der Seite der App enthalten. Die Paket-ID der Microsoft Word-App lautet z.B. **com.microsoft.office.word**.

Die App-Einstellungen werden beim nächsten Einchecken jedes Zielgeräts angewendet.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](../device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).
