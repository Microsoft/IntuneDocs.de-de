---
title: Kioskeinstellungen für Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Konfigurieren Sie Ihre Windows 10-Geräte (und höher) als Single- und Multi-App-Kiosks, und passen Sie das Startmenü an, indem Sie Apps und eine Taskleiste hinzufügen und einen Webbrowser konfigurieren. Konfigurieren Sie außerdem Windows Holographic for Business-Geräte als Multi-App-Kiosks in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6db58b1b1f19f789a2163f497c1f0da4c7c034a5
ms.sourcegitcommit: 5f6117b83f96f7d93dde3685c2ff2b67ae53740b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39481120"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Kioskeinstellungen für Windows 10 und höher in Intune

Mit Kioskprofilen können Sie Windows 10-Geräte so konfigurieren, dass sie entweder eine oder mehrere Apps ausführen. Wenn Sie ein Kioskprofil erstellen, können Sie u.a. festlegen, ob ein Startmenü angezeigt oder ein Webbrowser installiert wird.

## <a name="kiosk-settings"></a>Kioskeinstellungen

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Microsoft Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

   - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
   - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. Dies ist optional, wird jedoch empfohlen.
   - **Plattform**: Wählen Sie **Windows 10 und höher** aus.
   - **Profiltyp**: Wählen Sie **Kiosk (Vorschauversion)** aus.
   
4. Klicken Sie auf **Kiosk** > **Hinzufügen**.
5. Geben Sie einen **Kioskkonfigurationsnamen** für Ihren Kiosk ein. Dieser Name gibt eine Anwendungsgruppe, das Layout dieser Anwendungen im Startmenü und die Benutzer an, denen diese Kioskkonfiguration zugewiesen ist.
6. Wählen Sie den **Kioskmodus** aus. **Kioskmodus:** Gibt den Typ des Kioskmodus an, der von der Richtlinie unterstützt wird. Zu den Optionen gehören:

    - **Nicht konfiguriert** (Standard): Die Richtlinie aktiviert den Kioskmodus nicht.
    - **Kiosk mit einzelner Vollbild-App:** Das Profil lässt die Ausführung eines einzelnen Benutzerkontos auf dem Gerät zu und legt es auf eine einzelne UWP-App fest. Wenn sich der Benutzer anmeldet, wird so eine bestimmte App gestartet. Dieser Modus hindert den Benutzer auch daran, neue Apps zu öffnen oder die App zu ändern, die ausgeführt wird.
    - **Kiosk mit mehreren Apps:** Das Profil lässt die Ausführung mehrerer UWP-Apps bzw. Win32-Apps auf dem Gerät zu. Sie können unterschiedlichen Benutzerkonten unterschiedliche Apps zuweisen. Es sind nur die Apps, die Sie hinzufügen, für den Benutzer verfügbar. Der Vorteil eines Kiosks mit mehreren Apps oder eines Geräts mit festem Zweck ist ein leicht verständlicher Prozess für die Benutzer, da diese nur auf die Apps zugreifen, die sie benötigen. Apps, die sie nicht benötigen, werden aus der Ansicht entfernt.

#### <a name="single-full-screen-app-kiosks"></a>Kiosk mit einzelner Vollbild-App
Legen Sie folgende Einstellungen fest:

- **Bezeichner der UWP-App:** Geben Sie die **Modell-ID des Anwendungsbenutzers (AUMID)** der Kiosk-App ein. Alternativ können Sie eine vorhandene verwaltete App auswählen, die Sie über [Mobile Apps](apps-add.md) hinzugefügt haben.

    Weitere Informationen finden Sie unter [Find the Application User Model ID of an installed app (Ermitteln der Modell-ID eines Anwendungsbenutzers einer installierten App)](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

- **Typ des Benutzerkontos:** Sie haben folgende Optionen:

  - **Automatische Anmeldung:** Für Kiosks in öffentlichen Umgebungen, für die die automatische Anmeldung aktiviert ist, muss ein Benutzer mit den geringsten Berechtigungen (z.B. das lokale Standardbenutzerkonto) verwendet werden. Verwenden Sie das `AzureAD\user@contoso.com`-Format, um ein Azure Active Directory-Konto (AD) für den Kioskmodus zu konfigurieren.
  - **Lokales Benutzerkonto:** Geben Sie das (auf das Gerät bezogene) lokale Benutzerkonto oder die Anmeldeinformationen des Azure AD-Kontos ein, das der Kiosk-App zugeordnet ist. Geben Sie für Konten, die Mitglieder von Azure AD-Domänen sind, das Konto in der Form `domain\username@tenant.org` ein.

#### <a name="multi-app-kiosks"></a>Kiosks für mehrere Apps
Apps, die sich in diesem Modus befinden, sind über das Startmenü verfügbar. Diese Apps sind die einzigen Apps, die der Benutzer öffnen kann. 

[Kiosks für mehrere Apps](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune) verwenden eine Kioskkonfiguration, mit der die zugelassenen Apps aufgelistet werden, sowie andere Einstellungen.

Legen Sie folgende Einstellungen fest:

- **Win32-App hinzufügen:** Eine Win32-App ist eine herkömmliche Desktop-App. Geben Sie den **App-Namen** und den **Bezeichner** ein. Der **Bezeichner** ist der Name des vollqualifizierten Pfads der ausführbaren Datei bezogen auf das Gerät.
- **Verwaltete Apps hinzufügen:** Wählen Sie eine vorhandene verwaltete App aus, die Sie über [Mobile Apps in Intune](apps-add.md) hinzugefügt haben.
- **Add app by AUMID** (App nach AUMID hinzufügen): Geben Sie die [AUMID der App](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) ein (UWP-Apps).
- **Taskleiste**: Wählen Sie aus, ob Sie die Taskleiste **aktivieren** (anzeigen) oder sie im Kioskmodus **nicht konfiguriert** (ausgeblendet) lassen möchten.
- **Layout des Startmenüs:** Geben Sie eine XML-Datei ein, die beschreibt, wie die Apps im Startmenü dargestellt werden (u.a. die Reihenfolge der Apps). [Anpassen und Exportieren des Startlayouts](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout): bietet Anweisungen und XML-Beispiele.

  [Erstellen eines Windows 10-Kiosks, in dem mehrere Apps ausgeführt werden](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file): bietet weitere Details zur Verwendung und Erstellung von XML-Dateien.

- **Typ des Benutzerkontos:** Fügen Sie mindestens ein Benutzerkonto hinzu, das die von Ihnen hinzugefügten Apps verwenden kann. Wenn sich ein Benutzer mit einem Konto anmeldet, sind nur die in der Konfiguration definierten Apps verfügbar. Das Konto ist entweder nur lokal auf dem Gerät vorhanden oder umfasst Azure AD-Kontoanmeldeinformationen, die der Kiosk-App zugeordnet sind.

    Für Kiosks in öffentlichen Umgebungen, für die die automatische Anmeldung aktiviert ist, muss ein Benutzertyp mit den geringsten Berechtigungen (z.B. das lokale Standardbenutzerkonto) verwendet werden. Verwenden Sie das `domain\user@tenant.com`-Format, um ein Azure Active Directory-Konto (AD) für den Kioskmodus zu konfigurieren.

## <a name="kiosk-web-browser-settings"></a>Kioskbrowsereinstellungen

Mit diesen Einstellungen können Sie die Webbrowser-App im Kiosk steuern. Achten Sie darauf, dass Sie eine Webbrowser-App mit [Mobile Apps](apps-add.md) auf dem Kiosk-Gerät bereitstellen.

1. Legen Sie folgende Einstellungen fest:

    - **Standard-URL der Startseite:** Geben Sie die Standard-URL ein, die im Webbrowser geöffnet wird, wenn der Browser geöffnet oder neu gestartet wird.

    - **Startschaltfläche** Zeigen (**Zulassen**) Sie die Startschaltfläche des Kioskbrowsers an, oder verbergen Sie diese (**Nicht konfiguriert**). Standardmäßig ist die Schaltfläche nicht konfiguriert.

    - **Navigationsschaltfläche:** Zeigen (**Zulassen**) Sie die Schaltflächen „Weiter“ und „Zurück“ an, oder verbergen Sie diese (**Nicht konfiguriert**). Standardmäßig sind die Navigationsschaltflächen nicht konfiguriert.

    - **Schaltfläche „Sitzung beenden“**: Zeigen (**Zulassen**) Sie die Schaltfläche „Sitzung beenden“ an, oder verbergen Sie diese (**Nicht konfiguriert**). Wenn die Schaltfläche angezeigt wird, tippt der Benutzer darauf, und die App fragt, ob die Sitzung beendet werden soll. Wenn dies bestätigt wird, löscht der Browser alle Browserdaten (z.B. Cookies und Cache) und navigiert zurück zur Standard-URL. Standardmäßig ist die Schaltfläche nicht konfiguriert. 

    - **Refresh browser when user exceeds idle time limit** (Browser aktualisieren, wenn der Benutzer die zulässige Leerlaufzeit überschreitet): Geben Sie die zulässige Leerlaufzeit einer Sitzung in Minuten ein, nach der der Kioskbrowser aktualisiert wird. Der Wert ist eine ganze Zahl zwischen einer und 1440 Minuten. Standardmäßig ist der Wert leer, d.h., es gibt kein Leerlauftimeout.

    - **Blockierte Websites:** Eine Liste der URLs blockierter Websites (Platzhalter werden unterstützt). Verwenden Sie diese Einstellung, um zu verhindern, dass bestimmte Websites im Browser geöffnet werden. Sie können auch eine CSV-Datei **importieren**, die eine Liste enthält. Alternativ können Sie eine CSV-Datei erstellen (**Exportieren**), die von Ihnen hinzugefügt Websites enthält.

    - **Websiteausnahmen:** Eine Liste mit URLs, die von den blockierten Websites ausgenommen sind (Platzhalter werden unterstützt). Verwenden Sie diese Einstellung, um dem Browser das Öffnen bestimmter Websites zu gestatten. Diese Ausnahmen sind ein Teil der blockierten URLs. Wenn sich eine URL sowohl in der Liste der blockierten Websites als auch in der Liste der Websiteausnahmen befindet, gilt die Ausnahme.

    Sie können auch eine CSV-Datei **importieren**, die eine Liste enthält. Alternativ können Sie eine CSV-Datei erstellen (**Exportieren**), die von Ihnen hinzugefügt Websites enthält.

2. Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Sie können Windows Holographic for Business-Geräte so konfigurieren, dass sie im Single-App- oder im Multi-App-Kioskmodus ausgeführt werden. 

#### <a name="single-full-screen-app-kiosks"></a>Kiosk mit einzelner Vollbild-App
Legen Sie folgende Einstellungen fest:

- **Bezeichner der UWP-App:** Geben Sie die **Modell-ID des Anwendungsbenutzers (AUMID)** der Kiosk-App ein. Alternativ können Sie eine vorhandene verwaltete App auswählen, die Sie über [Mobile Apps](apps-add.md) hinzugefügt haben.

    Weitere Informationen zum Abrufen der ID finden Sie unter [Find the Application User Model ID of an installed app (Ermitteln der Anwendungsbenutzer-ID einer installierten App)](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

- **Typ des Benutzerkontos**: Klicken Sie auf **Lokales Benutzerkonto**, um das (auf das Gerät bezogene) lokale Benutzerkonto oder die Anmeldeinformationen des Microsoft-Kontos anzugeben, das der Kiosk-App zugeordnet ist. Der Typ **Autologon** wird unter Windows Holographic for Business nicht unterstützt.

#### <a name="multi-app-kiosks"></a>Kiosks für mehrere Apps
Apps, die sich in diesem Modus befinden, sind über das Startmenü verfügbar. Diese Apps sind die einzigen Apps, die der Benutzer öffnen kann.

Legen Sie folgende Einstellungen fest:

- **Verwaltete Apps hinzufügen:** Wählen Sie eine vorhandene verwaltete App aus, die Sie über [Mobile Apps in Intune](apps-add.md) hinzugefügt haben.
- **Add app by AUMID** (App nach AUMID hinzufügen): Geben Sie die [AUMID der App](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) ein (UWP-Apps).
- **Layout des Startmenüs:** Geben Sie eine XML-Datei ein, die beschreibt, wie die Apps im Startmenü dargestellt werden (u.a. die Reihenfolge der Apps). [Startlayout anpassen und exportieren](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens): Diese Option umfasst eine Anleitung und eine XML-Datei für Windows Holographic for Business-Geräte.
- **Typ des Benutzerkontos:** Fügen Sie mindestens ein Benutzerkonto hinzu, das die von Ihnen hinzugefügten Apps verwenden kann. Folgende Optionen werden unterstützt: 
  - **HoloLens-Besucher**: Beim Besucherkonto handelt es sich um ein Gastkonto, für das weder Anmeldeinformationen noch eine Authentifizierung erforderlich sind. Weitere Informationen dazu finden Sie unter [shared PC mode concepts (Konzepte für den Modus freigegebener Computer)](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).
  - **Azure AD-Benutzer**: Bei dieser Option sind Benutzeranmeldeinformationen für die Anmeldung auf dem Gerät erforderlich. Verwenden Sie das Format `domain\user@tenant.com`.
  - **Lokale Benutzerkonten**: Bei dieser Option sind Benutzeranmeldeinformationen für die Anmeldung auf dem Gerät erforderlich. 

Wenn sich ein Benutzer mit einem Konto anmeldet, sind nur die in der Konfiguration definierten Apps verfügbar.

## <a name="next-steps"></a>Nächste Schritte
[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
