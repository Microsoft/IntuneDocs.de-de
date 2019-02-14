---
title: Kioskeinstellungen für Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Konfigurieren Sie Ihre Geräte mit Windows 10 (und höher) als Kiosks mit einer App oder mehreren Apps, und passen Sie das Startmenü an, fügen Sie Apps hinzu, zeigen Sie die Taskleiste an und konfigurieren Sie einen Webbrowser in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7886f533f6ffa379132ac7c898bc5c1a1dac9111
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836539"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Geräteeinstellungen bei Windows 10 (und höher) zur Ausführung als Kiosk in Intune

Sie können Geräte mit Windows 10 und höher so konfigurieren, dass sie im Single-App- oder im Multi-App-Kioskmodus ausgeführt werden.

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie auf Geräten mit Windows 10 und höher festlegen können. Als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) verwenden Sie diese Einstellungen, um Ihre Geräte mit Windows 10 und höher für die Ausführung im Kioskmodus zu konfigurieren.

Als Intune-Administrator können Sie Ihre Geräte diese Einstellungen erstellen und zuweisen.

Weitere Informationen zur Windows-Kioskfunktion in Intune finden Sie unter [Konfigurieren der Kiosk-Einstellungen](kiosk-settings.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie das Profil.](kiosk-settings.md#create-the-profile)

## <a name="single-full-screen-app-kiosks"></a>Kiosk mit einzelner Vollbild-App

Wenn Sie den Einzel-App-Kioskmodus auswählen, nehmen Sie die folgenden Einstellungen vor:

- **Typ der Benutzeranmeldung:** Die Apps, die Sie hinzufügen, werden als das von Ihnen eingegebene Benutzerkonto ausgeführt. Folgende Optionen sind verfügbar:

  - **Automatische Anmeldung (Windows 10, Version 1803 und höher):** Für Kiosks in öffentlichen Umgebungen, die keine Benutzeranmeldung erfordern, ähnlich einem Gastkonto. Diese Einstellung verwendet [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Lokales Benutzerkonto:** Geben Sie das lokale Benutzerkonto (auf dem Gerät) an. Das von Ihnen eingegebene Konto wird zum Anmelden im Kiosk verwendet.

- **Anwendungstyp:** Wählen Sie **Store-App** aus.

- **App zur Ausführung im Kioskmodus:** Klicken Sie auf **Store-App hinzufügen**, und wählen Sie eine App aus der Liste aus.

    Es sind keine Apps aufgelistet? Fügen Sie einige mithilfe der Schritte unter [Client-Apps](apps-add.md) hinzu.

    Klicken Sie auf **OK**, um die Änderungen zu speichern.

- **Einstellungen für Kioskbrowser:** Mit diesen Einstellungen können Sie die Webbrowser-App im Kiosk steuern. Laden Sie die [Kioskbrowser-App](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) aus dem Store herunter, fügen Sie sie Intune als [Client-App](apps-add.md) hinzu, und ordnen Sie sie dann den Kioskgeräten zu.

  Legen Sie folgende Einstellungen fest:

  - **URL der Standardhomepage:** Geben Sie die Standard-URL ein, die angezeigt wird, wenn der Kioskbrowser geöffnet oder neu gestartet wird. Geben Sie beispielsweise `http://bing.com` oder `http://www.contoso.com` ein.

  - **Startschaltfläche:** Sie können die Startschaltfläche des Kioskbrowsers **einblenden** oder **ausblenden**. Standardmäßig wird die Schaltfläche ausgeblendet.

  - **Navigationsschaltflächen:** Sie können die Schaltflächen „Weiter“ und „Zurück“ **einblenden** oder **ausblenden**. Standardmäßig werden sie ausgeblendet.

  - **Schaltfläche „Sitzung beenden“:** Sie können die Schaltfläche „Sitzung beenden“ **einblenden** oder **ausblenden**. Wenn die Schaltfläche angezeigt wird, tippt der Benutzer darauf, und die App fragt, ob die Sitzung beendet werden soll. Wenn dies bestätigt wird, löscht der Browser alle Browserdaten (z.B. Cookies und Cache) und öffnet dann die Standard-URL. Standardmäßig wird die Schaltfläche ausgeblendet.

  - **Browser nach Leerlaufzeit aktualisieren:** Geben Sie die Leerlaufzeit ein (1–1.440 Minuten), nach der der Kioskbrowser im aktualisierten Zustand neu gestartet wird. Die Leerlaufzeit ist die Anzahl von Minuten seit der letzten Benutzerinteraktion. Standardmäßig ist der Wert leer, d.h., es gibt kein Leerlauftimeout.

  - **Zulässige Websites:** Verwenden Sie diese Einstellung, um das Öffnen bestimmter Websites zu ermöglichen. Mithilfe dieser Funktion können Sie also auf dem Gerät den Zugriff auf bestimmte Websites einschränken oder verhindern. Sie können z.B. gewähren, dass alle Websites unter `http://contoso.com*` geöffnet werden. Standardmäßig sind alle Websites zulässig.
 
      Um den Zugriff auf bestimmte Websites zu erlauben, laden Sie eine Datei mit einer in Zeilen unterteilten Liste der zulässigen Websites hoch. Wenn Sie keine Datei hinzufügen, können alle Websites aufgerufen werden. Intune unterstützt „*“ (Sternchen) als Platzhalter.

      Die Beispieldatei sollte der folgenden Beispielliste ähnlich sein:

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`  

  Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="multi-app-kiosks"></a>Kiosks für mehrere Apps

Apps, die sich in diesem Modus befinden, sind über das Startmenü verfügbar. Diese Apps sind die einzigen Apps, die der Benutzer öffnen kann.

Wenn Sie den Multi-App-Kioskmodus auswählen, nehmen Sie die folgenden Einstellungen vor:

- **Geräte unter Windows 10 im S Modus als Ziel verwenden:** Wählen Sie **Nein** aus, um Store-Apps und AUMID-Apps im Kioskprofil zu erlauben (ausgenommen Win32-Apps). Wählen Sie **Nein** aus, um Win32-Apps, Store-Apps und AUMID-Apps im Kioskprofil zu erlauben. Wenn Sie **Nein** auswählen, wird dieses Kioskprofil nicht für Geräte im S Modus bereitgestellt.

- **Typ der Benutzeranmeldung:** Die Apps, die Sie hinzufügen, werden als das von Ihnen eingegebene Benutzerkonto ausgeführt. Folgende Optionen sind verfügbar:

  - **Automatische Anmeldung (Windows 10, Version 1803 und höher):** Für Kiosks in öffentlichen Umgebungen, die keine Benutzeranmeldung erfordern, ähnlich einem Gastkonto. Diese Einstellung verwendet [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Lokales Benutzerkonto:** **Fügen Sie das lokale Benutzerkonto (auf dem Gerät) hinzu**. Das von Ihnen eingegebene Konto wird zum Anmelden im Kiosk verwendet.
  - **Azure AD-Benutzer oder Gruppe (Windows 10, Version 1803 und höher):** Wählen Sie **Hinzufügen** aus, um Azure AD-Benutzer oder Gruppen aus der Liste auszuwählen. Sie können mehrere Benutzer und Gruppen auswählen. Wählen Sie **OK** aus, um die Änderungen zu speichern.
  - **HoloLens-Besucher:** Beim Besucherkonto handelt es sich um ein Gastkonto, für das keine Anmeldeinformationen oder Authentifizierung erforderlich ist. Weitere Informationen dazu finden Sie unter [shared PC mode concepts (Konzepte für den Modus „Freigegebener Computer“)](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Anwendungen:** Wählen Sie die Apps aus, die auf dem Kioskgerät ausgeführt werden sollen. Denken Sie daran, dass Sie mehrere Apps hinzufügen können.

  - **Store-App hinzufügen:** Fügen Sie eine App aus dem Microsoft Store for Business hinzu. Wenn keine Apps aufgelistet sind, können Sie Apps abrufen und [Intune hinzufügen](store-apps-windows.md). Beispielsweise lassen sich der Kioskbrowser, Excel und OneNote hinzufügen.

  - **Win32-App hinzufügen:** Eine Win32-App ist eine klassische Desktop-App wie Visual Studio Code oder Google Chrome. Geben Sie die folgenden Eigenschaften ein:

    - **Anwendungsname:** Erforderlich. Geben Sie einen Namen für die Anwendung ein.
    - **Lokaler Pfad:** Erforderlich. Geben Sie den Pfad zur ausführbaren Datei ein, z.B. `C:\Program Files (x86)\Microsoft VS Code\Code.exe` oder `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
    - **Anwendungsbenutzermodell-ID (AUMID):** Geben Sie die AUMID der Win32-App ein. Diese Einstellung bestimmt das Startlayout der Kachel auf dem Desktop. Informationen zum Abrufen dieser ID finden Sie unter [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).
    - **Kachelgröße:** Erforderlich. Wählen Sie eine der folgenden App-Kachelgrößen aus: „Klein“, „Mittelgroß“, „Breit“ oder „Groß“.
  
  - **Nach AUMID hinzufügen:** Mit dieser Option können Sie Windows-Posteingangs-Apps wie Editor oder Rechner hinzufügen. Geben Sie die folgenden Eigenschaften ein: 

    - **Anwendungsname:** Erforderlich. Geben Sie einen Namen für die Anwendung ein.
    - **Anwendungsbenutzermodell-ID (AUMID):** Erforderlich. Geben Sie die AUMID der Windows-App ein. Weitere Informationen zum Abrufen dieser ID finden Sie unter [Ermitteln der Anwendungsbenutzermodell-ID einer installierten App](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Kachelgröße:** Erforderlich. Wählen Sie eine der folgenden App-Kachelgrößen aus: „Klein“, „Mittelgroß“, „Breit“ oder „Groß“.

  > [!TIP]
  > Nachdem Sie alle Apps hinzugefügt haben, können Sie die Anzeigereihenfolge ändern, indem Sie auf die Apps in der Liste klicken und sie dann verschieben.  

  Klicken Sie auf **OK**, um die Änderungen zu speichern.

- **Einstellungen für Kioskbrowser:** Mit diesen Einstellungen können Sie die Webbrowser-App im Kiosk steuern. Achten Sie darauf, dass Sie eine Webbrowser-App auf dem Kioskgerät über [Client-Apps](apps-add.md) bereitstellen.

  Legen Sie folgende Einstellungen fest:

  - **URL der Standardhomepage:** Geben Sie die Standard-URL ein, die angezeigt wird, wenn der Kioskbrowser geöffnet oder neu gestartet wird. Geben Sie beispielsweise `http://bing.com` oder `http://www.contoso.com` ein.

  - **Startschaltfläche:** Sie können die Startschaltfläche des Kioskbrowsers **einblenden** oder **ausblenden**. Standardmäßig wird die Schaltfläche ausgeblendet.

  - **Navigationsschaltflächen:** Sie können die Schaltflächen „Weiter“ und „Zurück“ **einblenden** oder **ausblenden**. Standardmäßig werden sie ausgeblendet.

  - **Schaltfläche „Sitzung beenden“:** Sie können die Schaltfläche „Sitzung beenden“ **einblenden** oder **ausblenden**. Wenn die Schaltfläche angezeigt wird, tippt der Benutzer darauf, und die App fragt, ob die Sitzung beendet werden soll. Wenn dies bestätigt wird, löscht der Browser alle Browserdaten (z.B. Cookies und Cache) und öffnet dann die Standard-URL. Standardmäßig wird die Schaltfläche ausgeblendet.

  - **Browser nach Leerlaufzeit aktualisieren:** Geben Sie die Leerlaufzeit ein (1–1.440 Minuten), nach der der Kioskbrowser im aktualisierten Zustand neu gestartet wird. Die Leerlaufzeit ist die Anzahl von Minuten seit der letzten Benutzerinteraktion. Standardmäßig ist der Wert leer, d.h., es gibt kein Leerlauftimeout.

  - **Zulässige Websites:** Verwenden Sie diese Einstellung, um das Öffnen bestimmter Websites zu ermöglichen. Mithilfe dieser Funktion können Sie also auf dem Gerät den Zugriff auf bestimmte Websites einschränken oder verhindern. Sie können z.B. gewähren, dass alle Websites unter `contoso.com*` geöffnet werden. Standardmäßig sind alle Websites zulässig.

    Um den Zugriff auf bestimmte Websites zu erlauben, laden Sie eine CSV-Datei mit einer Liste der zulässigen Websites hoch. Wenn Sie keine CSV-Datei hinzufügen, können alle Websites aufgerufen werden.

  Klicken Sie auf **OK**, um die Änderungen zu speichern.

- **Alternatives Startlayout verwenden:** Wählen Sie **Ja** aus, um eine XML-Datei einzufügen, die beschreibt, wie die Apps im Startmenü dargestellt werden (u. a. die Reihenfolge der Apps). Verwenden Sie diese Option, wenn Sie in Ihrem Startmenü weitere Anpassungen vornehmen möchten. [Anpassen und Exportieren des Startlayouts](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout): bietet Anweisungen und XML-Beispiele.

- **Windows-Taskleiste:** Sie können die Taskleiste **einblenden** oder **ausblenden**. Standardmäßig wird sie ausgeblendet. Symbole, z.B. das WLAN-Symbol werden dargestellt, die Einstellungen können jedoch nicht vom Endbenutzer geändert werden.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Außerdem können Sie Kioskprofile für Geräte mit [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings), and [Windows Holographic for Business](kiosk-settings-holographic.md) erstellen.
