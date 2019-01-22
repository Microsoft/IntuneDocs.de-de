---
title: Kioskeinstellungen für Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Konfigurieren Sie Ihre Geräte mit Windows 10 (und höher) als Kiosks mit einer App oder mehreren Apps, und passen Sie das Startmenü an, fügen Sie Apps hinzu, zeigen Sie die Taskleiste an und konfigurieren Sie einen Webbrowser. Konfigurieren Sie außerdem Windows Holographic for Business-Geräte als Multi-App-Kiosks in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.openlocfilehash: 353c18affa41e56501a76bf695f95cbe95796e99
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203466"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-dedicated-kiosk-using-intune"></a>Geräteeinstellungen bei Windows 10 (und höher) zur Ausführung als dedizierter Kiosk mit Intune

Verwenden Sie Intune, um Geräte mit Windows 10 als Kiosk auszuführen. Diese werden manchmal auch als dedizierte Geräte bezeichnet. Auf einem Gerät im Kioskmodus können eine oder mehrere Apps ausgeführt werden. Sie können ein Startmenü anzeigen und anpassen, verschiedene Apps hinzufügen, einschließlich Win32-Anwendungen, einem Webbrowser eine bestimmte Startseite hinzufügen und vieles mehr. 

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie auf Geräten mit Windows 10 und höher festlegen können. Als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) verwenden Sie diese Einstellungen, um Ihre Geräte mit Windows 10 für die Ausführung im Kioskmodus zu konfigurieren.

Intune unterstützt ein Kioskprofil pro Gerät. Wenn Sie mehrere Kioskprofile auf einem einzelnen Gerät benötigen, können Sie einen [benutzerdefinierten OMA-URI](custom-settings-windows-10.md) verwenden.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](device-profile-create.md)

## <a name="kiosk-settings"></a>Kioskeinstellungen

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

   - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
   - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
   - **Plattform**: Wählen Sie **Windows 10 und höher** aus.
   - **Profiltyp**: Wählen Sie **Kiosk** aus.

4. Wählen Sie einen **Kioskmodus** aus. **Kioskmodus:** Gibt den Typ des Kioskmodus an, der von der Richtlinie unterstützt wird. Zu den Optionen gehören:

    - **Nicht konfiguriert** (Standardeinstellung): Durch die Richtlinie kann der Kioskmodus nicht aktiviert werden.
    - **Einzelne App, Vollbildkiosk:** Das Gerät wird mit einem einzelnen Benutzerkonto ausgeführt und kann nur auf eine einzige Store-App zugreifen. Wenn sich der Benutzer anmeldet, wird so eine bestimmte App gestartet. Dieser Modus hindert den Benutzer auch daran, neue Apps zu öffnen oder die App zu ändern, die ausgeführt wird.
    - **Kiosk mit mehreren Apps:** Das Gerät führt mehrere Store-Apps, Win32-Apps oder Windows-Posteingangs-Apps unter Verwendung der Anwendungsbenutzermodell-ID (AUMID) aus. Nur die von Ihnen hinzugefügten Apps sind auf dem Gerät verfügbar.

        Der Vorteil eines Kiosks mit mehreren Apps oder eines Geräts mit festem Zweck ist ein leicht verständlicher Prozess für die Benutzer, da diese nur auf die Apps zugreifen, die sie benötigen. Apps, die sie nicht benötigen, werden aus der Ansicht entfernt.

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
    - **Anwendungsbenutzermodell-ID (AUMID):** Geben Sie die AUMID der Win32-App ein. Diese Einstellung bestimmt das Startlayout der Kachel auf dem Desktop. Weitere Informationen zum Abrufen dieser ID finden Sie unter [Ermitteln der Anwendungsbenutzermodell-ID einer installierten App](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).
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

- **Windows-Taskleiste:** Sie können die Taskleiste **einblenden** oder **ausblenden**. Standardmäßig wird sie ausgeblendet.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Sie können Windows Holographic for Business-Geräte so konfigurieren, dass sie im Single-App- oder im Multi-App-Kioskmodus ausgeführt werden. Einige Funktionen werden unter Windows Holographic for Business nicht unterstützt.

#### <a name="single-full-screen-app-kiosks"></a>Kiosk mit einzelner Vollbild-App
Wenn Sie den Einzel-App-Kioskmodus auswählen, nehmen Sie die folgenden Einstellungen vor:

- **Typ der Benutzeranmeldung:** Wählen Sie **Lokales Benutzerkonto** aus, um das lokale Benutzerkonto (auf dem Gerät) oder ein Microsoft-Konto (MSA) einzugeben, das der Kiosk-App zugeordnet ist. Der Typ **Autologon** wird unter Windows Holographic for Business nicht unterstützt.

- **Anwendungstyp:** Wählen Sie **Store-App** aus.

- **App zur Ausführung im Kioskmodus:** Klicken Sie auf **Store-App hinzufügen**, und wählen Sie eine App aus der Liste aus.

    Es sind keine Apps aufgelistet? Fügen Sie einige mithilfe der Schritte unter [Client-Apps](apps-add.md) hinzu.

    Klicken Sie auf **OK**, um die Änderungen zu speichern.

#### <a name="multi-app-kiosks"></a>Kiosks für mehrere Apps
Apps, die sich in diesem Modus befinden, sind über das Startmenü verfügbar. Diese Apps sind die einzigen Apps, die der Benutzer öffnen kann. Wenn Sie den Multi-App-Kioskmodus auswählen, nehmen Sie die folgenden Einstellungen vor:

- **Geräte unter Windows 10 im S Modus als Ziel verwenden:** Wählen Sie **Nein** aus. Der S Modus wird unter Windows Holographic for Business nicht unterstützt.

- **Typ der Benutzeranmeldung:** Fügen Sie mindestens ein Benutzerkonto hinzu, das die von Ihnen hinzugefügten Apps verwenden kann. Folgende Optionen sind verfügbar: 

  - **Auto logon** (Automatische Anmeldung): Wird unter Windows Holographic for Business nicht unterstützt.
  - **Lokale Benutzerkonten:** **Fügen Sie das lokale Benutzerkonto (auf dem Gerät) hinzu**. Das von Ihnen eingegebene Konto wird zum Anmelden im Kiosk verwendet.
  - **Azure AD-Benutzer oder Gruppe (Windows 10, Version 1803 und höher):** Bei dieser Option sind Benutzeranmeldeinformationen für die Anmeldung auf dem Gerät erforderlich. Wählen Sie **Hinzufügen** aus, um Azure AD-Benutzer oder Gruppen aus der Liste auszuwählen. Sie können mehrere Benutzer und Gruppen auswählen. Wählen Sie **OK** aus, um die Änderungen zu speichern.
  - **HoloLens-Besucher:** Beim Besucherkonto handelt es sich um ein Gastkonto, für das keine Anmeldeinformationen oder Authentifizierung erforderlich ist. Weitere Informationen dazu finden Sie unter [shared PC mode concepts (Konzepte für den Modus „Freigegebener Computer“)](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Anwendungen:** Wählen Sie die Apps aus, die auf dem Kioskgerät ausgeführt werden sollen. Denken Sie daran, dass Sie mehrere Apps hinzufügen können.

  - **Store-App hinzufügen:** Wählen Sie eine vorhandene App aus, die Sie mit [Client-Apps](apps-add.md) hinzugefügt haben. Wenn keine Apps aufgelistet sind, können Sie Apps abrufen und [Intune hinzufügen](store-apps-windows.md).
  - **Win32-App hinzufügen:** Wird unter Windows Holographic for Business nicht unterstützt.
  - **Nach AUMID hinzufügen:** Fügen Sie mit dieser Option Windows-Apps für den Posteingang hinzu. Geben Sie die folgenden Eigenschaften ein: 

    - **Anwendungsname:** Erforderlich. Geben Sie einen Namen für die Anwendung ein.
    - **Anwendungsbenutzermodell-ID (AUMID):** Erforderlich. Geben Sie die AUMID der Windows-App ein. Weitere Informationen zum Abrufen dieser ID finden Sie unter [Ermitteln der Anwendungsbenutzermodell-ID einer installierten App](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Kachelgröße:** Erforderlich. Wählen Sie eine der folgenden App-Kachelgrößen aus: „Klein“, „Mittelgroß“, „Breit“ oder „Groß“.

- **Einstellungen für Kioskbrowser:** Wird unter Windows Holographic for Business nicht unterstützt.

- **Alternatives Startlayout verwenden:** Wählen Sie **Ja** aus, um eine XML-Datei einzufügen, die beschreibt, wie die Apps im Startmenü dargestellt werden (u. a. die Reihenfolge der Apps). Verwenden Sie diese Option, wenn Sie in Ihrem Startmenü weitere Anpassungen vornehmen möchten. [Startlayout anpassen und exportieren](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens): Diese Option umfasst eine Anleitung und eine XML-Datei für Windows Holographic for Business-Geräte.

- **Windows-Taskleiste:** Wird unter Windows Holographic for Business nicht unterstützt.

## <a name="next-steps"></a>Nächste Schritte
[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Außerdem können Sie Kioskmodusprofile auch für [Android](device-restrictions-android.md#kiosk)- und [Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings)-Geräte erstellen.
