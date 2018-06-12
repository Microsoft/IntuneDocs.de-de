---
title: Kioskeinstellungen für Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: In diesem Artikel lernen Sie die Microsoft Intune-Einstellungen zur Steuerung von Geräteeinstellungen und -funktionen auf Windows 10-Geräten kennen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 897ff48253961d6e1aa83bf36113c362d4548fbf
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745147"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Kioskeinstellungen für Windows 10 und höher in Intune

Mit Kioskprofilen können Sie Windows 10-Geräte so konfigurieren, dass sie eine oder mehrere Apps ausführen. Wenn Sie ein Kioskprofil konfigurieren, können Sie u.a. festlegen, ob ein Startmenü angezeigt und ob ein Webbrowser installiert wird.

## <a name="kiosk-settings"></a>Kioskeinstellungen

1. Klicken Sie auf **Hinzufügen**, um eine Kioskumgebung zu erstellen.
2. Geben Sie einen **Kioskkonfigurationsnamen** für Ihren Kiosk ein. Dieser Name gibt eine Anwendungsgruppe, das Layout dieser Anwendungen im Startmenü und die Benutzer an, denen diese Kioskkonfiguration zugewiesen ist.
3. Wählen Sie den **Kioskmodus** aus. **Kioskmodus:** Gibt den Typ des Kioskmodus an, der von der Richtlinie unterstützt wird. Zu den Optionen gehören:

  - **Nicht konfiguriert** (Standard): Die Richtlinie aktiviert keinen Kioskmodus.
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

  - **Startschaltfläche anzeigen:** Anzeigen (**Erforderlich**) oder Verbergen (**Nicht konfiguriert**) der Startschaltfläche des Kioskbrowsers. Standardmäßig ist die Schaltfläche nicht konfiguriert.

  - **Navigationsschaltflächen anzeigen:** Anzeigen (**Erforderlich**) oder Verbergen (**Nicht konfiguriert**) der Schaltflächen „Weiter“ und „Zurück“. Standardmäßig sind die Navigationsschaltflächen nicht konfiguriert.

  - **Refresh browser when user exceeds idle time limit** (Browser aktualisieren, wenn der Benutzer die zulässige Leerlaufzeit überschreitet): Geben Sie die zulässige Leerlaufzeit einer Sitzung in Minuten ein, nach der der Kioskbrowser aktualisiert wird. Der Wert ist eine ganze Zahl zwischen einer und 1440 Minuten. Standardmäßig ist der Wert leer, d.h., es gibt kein Leerlauftimeout.

  - **Blockierte Websites:** Eine Liste der URLs blockierter Websites (Platzhalter werden unterstützt). Verwenden Sie diese Einstellung, um zu verhindern, dass bestimmte Websites im Browser geöffnet werden. Sie können auch eine CSV-Datei **importieren**, die eine Liste enthält. Alternativ können Sie eine CSV-Datei erstellen (**Exportieren**), die von Ihnen hinzugefügt Websites enthält.

  - **Websiteausnahmen:** Eine Liste mit URLs, die von den blockierten Websites ausgenommen sind (Platzhalter werden unterstützt). Verwenden Sie diese Einstellung, um dem Browser das Öffnen bestimmter Websites zu gestatten. Diese Ausnahmen sind ein Teil der blockierten URLs. Wenn sich eine URL sowohl in der Liste der blockierten Websites als auch in der Liste der Websiteausnahmen befindet, gilt die Ausnahme.

    Sie können auch eine CSV-Datei **importieren**, die eine Liste enthält. Alternativ können Sie eine CSV-Datei erstellen (**Exportieren**), die von Ihnen hinzugefügt Websites enthält.

2. Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="next-steps"></a>Nächste Schritte
[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)