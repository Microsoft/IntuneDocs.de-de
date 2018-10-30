---
title: Kioskeinstellungen für Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Konfigurieren Sie Ihre Windows 10-Geräte (und höher) als Kiosk mit einer App oder mehreren Apps, und passen Sie das Startmenü an, indem Sie Apps und eine Taskleiste hinzufügen und einen Webbrowser konfigurieren. Konfigurieren Sie außerdem Windows Holographic for Business-Geräte als Multi-App-Kiosks in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 59e2ab4635c8488b99781ac123aacd0854967dc8
ms.sourcegitcommit: c3ac9e5f6240223cb5dfed8b44c7425066d6ea86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "49380030"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Kioskeinstellungen für Windows 10 und höher in Intune

Mit Intune können Sie Windows 10-Geräte als Kiosk verwenden. Der Kiosk kann eine App oder mehrere Apps ausführen. Sie können auch ein Startmenü anzeigen und anpassen, verschiedene Apps hinzufügen, einschließlich Win32-Anwendungen, einem Webbrowser eine bestimmte Startseite hinzufügen und vieles mehr. 

Befolgen Sie die Schritte in diesem Artikel, um einen Kiosk mit einer einzelnen App oder mit mehreren Apps in Intune zu erstellen.

Intune unterstützt ein Kioskprofil pro Gerät. Wenn Sie mehrere Kioskprofile auf einem einzelnen Gerät benötigen, können Sie einen [benutzerdefinierten OMA-URI](custom-settings-windows-10.md) verwenden.

## <a name="kiosk-settings"></a>Kioskeinstellungen

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Microsoft Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

   - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
   - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
   - **Plattform**: Wählen Sie **Windows 10 und höher** aus.
   - **Profiltyp**: Wählen Sie **Kiosk (Vorschauversion)** aus.

4. Wählen Sie einen **Kioskmodus** aus. **Kioskmodus:** Gibt den Typ des Kioskmodus an, der von der Richtlinie unterstützt wird. Zu den Optionen gehören:

    - **Nicht konfiguriert** (Standard): Die Richtlinie aktiviert den Kioskmodus nicht.
    - **Einzelne App, Vollbildkiosk**: Das Gerät wird mit einem einzelnen Benutzerkonto ausgeführt und kann nur auf einen einzigen Store-App zugreifen. Wenn sich der Benutzer anmeldet, wird so eine bestimmte App gestartet. Dieser Modus hindert den Benutzer auch daran, neue Apps zu öffnen oder die App zu ändern, die ausgeführt wird.
    - **Kiosk mit mehreren Apps**: Das Gerät führt mehrere Store-Apps, Win32-Apps oder Windows-Posteingangs-Apps unter Verwendung der Anwendungsbenutzermodell-ID (AUMID) aus. Nur die von Ihnen hinzugefügten Apps sind auf dem Gerät verfügbar.

        Der Vorteil eines Kiosks mit mehreren Apps oder eines Geräts mit festem Zweck ist ein leicht verständlicher Prozess für die Benutzer, da diese nur auf die Apps zugreifen, die sie benötigen. Apps, die sie nicht benötigen, werden aus der Ansicht entfernt.

## <a name="single-full-screen-app-kiosks"></a>Kiosk mit einzelner Vollbild-App
Wenn Sie den Einzel-App-Kioskmodus auswählen, nehmen Sie die folgenden Einstellungen vor:

- **Typ der Benutzeranmeldung**: Die Apps, die Sie hinzufügen, werden als das von Ihnen eingegebene Benutzerkonto ausgeführt. Folgende Optionen sind verfügbar:

  - **Automatische Anmeldung (Windows 10, Version 1803 und höher)**: Für Kioske in öffentlichen Umgebungen, die keine Benutzeranmeldung erfordern, ähnlich einem Gastkonto. Diese Einstellung verwendet [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Lokales Benutzerkonto**: Geben Sie das lokale Benutzerkonto (auf dem Gerät) an. Das von Ihnen eingegebene Konto wird zum Anmelden im Kiosk verwendet.

- **Anwendungstyp**: Wählen Sie **Store-App** aus.

- **App zur Ausführung im Kioskmodus**: Wählen Sie **Store-App hinzufügen** und eine App aus der Liste aus.

    Es sind keine Apps aufgelistet? Fügen Sie einige mithilfe der Schritte unter [Client-Apps](apps-add.md) hinzu.

    Klicken Sie auf **OK**, um die Änderungen zu speichern.

- **Einstellungen für Kioskbrowser**: Mit diesen Einstellungen können Sie die Webbrowser-App im Kiosk steuern. Laden Sie die [Kioskbrowser-App](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) aus dem Store herunter, fügen Sie sie Intune als [Client-App](apps-add.md) hinzu, und ordnen Sie sie dann den Kioskgeräten zu.

  Legen Sie folgende Einstellungen fest:

  - **URL der Standardhomepage**: Geben Sie die Standard-URL ein, die angezeigt wird, wenn der Kioskbrowser geöffnet oder neu gestartet wird. Geben Sie beispielsweise `http://bing.com` oder `http://www.contoso.com` ein.

  - **Startschaltfläche**: Sie haben die beiden Optionen, die Startschaltfläche des Kioskbrowsers **einzublenden** oder **auszublenden**. Standardmäßig wird die Schaltfläche ausgeblendet.

  - **Navigationsschaltflächen**: Sie können die Schaltflächen „Vorwärts“ und „Zurück“ **einblenden** oder **ausblenden**. Standardmäßig werden sie ausgeblendet.

  - **Schaltfläche „Sitzung beenden“**: Sie können diese Schaltfläche **einblenden** oder **ausblenden**. Wenn die Schaltfläche angezeigt wird, tippt der Benutzer darauf, und die App fragt, ob die Sitzung beendet werden soll. Wenn dies bestätigt wird, löscht der Browser alle Browserdaten (z.B. Cookies und Cache) und öffnet dann die Standard-URL. Standardmäßig wird die Schaltfläche ausgeblendet.

  - **Browser nach Leerlaufzeit aktualisieren**: Geben Sie die Leerlaufzeit ein (1–1.440 Minuten), nach der der Kioskbrowser im aktualisierten Zustand neu gestartet wird. Die Leerlaufzeit ist die Anzahl von Minuten seit der letzten Benutzerinteraktion. Standardmäßig ist der Wert leer, d.h., es gibt kein Leerlauftimeout.

  - **Zugelassene Websites**: Verwenden Sie diese Einstellung, um das Öffnen bestimmter Websites zu ermöglichen. Mithilfe dieser Funktion können Sie also auf dem Gerät den Zugriff auf bestimmte Websites einschränken oder verhindern. Sie können z.B. gewähren, dass alle Websites unter `http://contoso.com*` geöffnet werden. Standardmäßig sind alle Websites zulässig.

    Um den Zugriff auf bestimmte Websites zu erlauben, laden Sie eine CSV-Datei mit einer Liste der zulässigen Websites hoch. Wenn Sie keine CSV-Datei hinzufügen, können alle Websites aufgerufen werden. Intune unterstützt „*“ (Sternchen) als Platzhalter.

  Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="multi-app-kiosks"></a>Kiosks für mehrere Apps

Apps, die sich in diesem Modus befinden, sind über das Startmenü verfügbar. Diese Apps sind die einzigen Apps, die der Benutzer öffnen kann.

Wenn Sie den Multi-App-Kioskmodus auswählen, nehmen Sie die folgenden Einstellungen vor:

- **Geräte unter Windows 10 im S Modus als Ziel verwenden**: Wählen Sie **Ja** aus, um Store-Apps und AUMID-Apps (ausgenommen Win32-Apps) im Kioskprofil zuzulassen. Wählen Sie **Nein** aus, um Win32-Apps, Store-Apps und AUMID-Apps im Kioskprofil zu erlauben. Wenn Sie **Nein** auswählen, wird dieses Kioskprofil nicht für Geräte im S Modus bereitgestellt.

- **Typ der Benutzeranmeldung**: Die Apps, die Sie hinzufügen, werden als das von Ihnen eingegebene Benutzerkonto ausgeführt. Folgende Optionen sind verfügbar:

  - **Automatische Anmeldung (Windows 10, Version 1803 und höher)**: Für Kioske in öffentlichen Umgebungen, die keine Benutzeranmeldung erfordern, ähnlich einem Gastkonto. Diese Einstellung verwendet [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Lokales Benutzerkonto**: **Fügen** Sie das lokale Benutzerkonto (auf dem Gerät) hinzu. Das von Ihnen eingegebene Konto wird zum Anmelden im Kiosk verwendet.
  - **Azure AD-Benutzer oder Gruppe (Windows 10, Version 1803 und höher)**: Wählen Sie **Hinzufügen** aus, um Azure AD-Benutzer oder Gruppen aus der Liste auszuwählen. Sie können mehrere Benutzer und Gruppen auswählen. Wählen Sie **OK** aus, um die Änderungen zu speichern.
  - **HoloLens-Besucher**: Beim Besucherkonto handelt es sich um ein Gastkonto, für das weder Anmeldeinformationen noch eine Authentifizierung erforderlich sind. Weitere Informationen dazu finden Sie unter [shared PC mode concepts (Konzepte für den Modus freigegebener Computer)](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Anwendungen**: Wählen Sie die Apps aus, die auf dem Kioskgerät ausgeführt werden sollen. Denken Sie daran, dass Sie mehrere Apps hinzufügen können.

  - **Store-App hinzufügen**: Fügen Sie eine App aus dem Microsoft Store für Unternehmen hinzu. Wenn keine Apps aufgelistet sind, können Sie Apps abrufen und [Intune hinzufügen](store-apps-windows.md). Beispielsweise lassen sich der Kioskbrowser, Excel und OneNote hinzufügen.

  - **Win32-App hinzufügen**: Eine Win32-App ist eine klassische Desktop-App wie Visual Studio Code oder Google Chrome. Geben Sie die folgenden Eigenschaften ein:

    - **Anwendungsname**: Pflichtfeld. Geben Sie einen Namen für die Anwendung ein.
    - **Lokaler Pfad**: Pflichtfeld. Geben Sie den Pfad zur ausführbaren Datei ein, z.B. `C:\Program Files (x86)\Microsoft VS Code\Code.exe` oder `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
    - **Anwendungsbenutzermodell-ID (AUMID)**: Optional. Geben Sie die AUMID der Win32-App ein. Diese Einstellung bestimmt das Startlayout der Kachel auf dem Desktop. Weitere Informationen zum Abrufen dieser ID finden Sie unter [Ermitteln der Anwendungsbenutzermodell-ID einer installierten App](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Kachelgröße**: Pflichtfeld. Wählen Sie eine der folgenden App-Kachelgrößen aus: „Klein“, „Mittelgroß“, „Breit“ oder „Groß“.
  
  - **Nach AUMID hinzufügen**: Mit dieser Option können Sie Windows-Posteingangs-Apps wie Editor oder Rechner hinzufügen. Geben Sie die folgenden Eigenschaften ein: 

    - **Anwendungsname**: Pflichtfeld. Geben Sie einen Namen für die Anwendung ein.
    - **Anwendungsbenutzermodell-ID (AUMID)**: Pflichtfeld. Geben Sie die AUMID der Windows-App ein. Weitere Informationen zum Abrufen dieser ID finden Sie unter [Ermitteln der Anwendungsbenutzermodell-ID einer installierten App](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Kachelgröße**: Pflichtfeld. Wählen Sie eine der folgenden App-Kachelgrößen aus: „Klein“, „Mittelgroß“, „Breit“ oder „Groß“.

  > [!TIP]
  > Nachdem Sie alle Apps hinzugefügt haben, können Sie die Anzeigereihenfolge ändern, indem Sie auf die Apps in der Liste klicken und sie dann verschieben.  

  Klicken Sie auf **OK**, um die Änderungen zu speichern.

- **Einstellungen für Kioskbrowser**: Mit diesen Einstellungen können Sie die Webbrowser-App im Kiosk steuern. Achten Sie darauf, dass Sie eine Webbrowser-App auf dem Kioskgerät über [Client-Apps](apps-add.md) bereitstellen.

  Legen Sie folgende Einstellungen fest:

  - **URL der Standardhomepage**: Geben Sie die Standard-URL ein, die angezeigt wird, wenn der Kioskbrowser geöffnet oder neu gestartet wird. Geben Sie beispielsweise `http://bing.com` oder `http://www.contoso.com` ein.

  - **Startschaltfläche**: Sie haben die beiden Optionen, die Startschaltfläche des Kioskbrowsers **einzublenden** oder **auszublenden**. Standardmäßig wird die Schaltfläche ausgeblendet.

  - **Navigationsschaltflächen**: Sie können die Schaltflächen „Vorwärts“ und „Zurück“ **einblenden** oder **ausblenden**. Standardmäßig werden sie ausgeblendet.

  - **Schaltfläche „Sitzung beenden“**: Sie können diese Schaltfläche **einblenden** oder **ausblenden**. Wenn die Schaltfläche angezeigt wird, tippt der Benutzer darauf, und die App fragt, ob die Sitzung beendet werden soll. Wenn dies bestätigt wird, löscht der Browser alle Browserdaten (z.B. Cookies und Cache) und öffnet dann die Standard-URL. Standardmäßig wird die Schaltfläche ausgeblendet.

  - **Browser nach Leerlaufzeit aktualisieren**: Geben Sie die Leerlaufzeit ein (1–1.440 Minuten), nach der der Kioskbrowser im aktualisierten Zustand neu gestartet wird. Die Leerlaufzeit ist die Anzahl von Minuten seit der letzten Benutzerinteraktion. Standardmäßig ist der Wert leer, d.h., es gibt kein Leerlauftimeout.

  - **Zugelassene Websites**: Verwenden Sie diese Einstellung, um das Öffnen bestimmter Websites zu ermöglichen. Mithilfe dieser Funktion können Sie also auf dem Gerät den Zugriff auf bestimmte Websites einschränken oder verhindern. Sie können z.B. gewähren, dass alle Websites unter `contoso.com*` geöffnet werden. Standardmäßig sind alle Websites zulässig.

    Um den Zugriff auf bestimmte Websites zu erlauben, laden Sie eine CSV-Datei mit einer Liste der zulässigen Websites hoch. Wenn Sie keine CSV-Datei hinzufügen, können alle Websites aufgerufen werden.

  Klicken Sie auf **OK**, um die Änderungen zu speichern.

- **Alternatives Startlayout verwenden**: Wählen Sie **Ja** aus, um eine XML-Datei einzugeben, die beschreibt, wie die Apps im Startmenü angezeigt werden, einschließlich der Reihenfolge. Verwenden Sie diese Option, wenn Sie in Ihrem Startmenü weitere Anpassungen vornehmen möchten. [Anpassen und Exportieren des Startlayouts](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout): bietet Anweisungen und XML-Beispiele.

- **Windows-Taskleiste**: Sie können die Taskleiste **einblenden** oder **ausblenden**. Standardmäßig wird sie ausgeblendet.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Sie können Windows Holographic for Business-Geräte so konfigurieren, dass sie im Single-App- oder im Multi-App-Kioskmodus ausgeführt werden. Einige Funktionen werden unter Windows Holographic for Business nicht unterstützt.

#### <a name="single-full-screen-app-kiosks"></a>Kiosk mit einzelner Vollbild-App
Wenn Sie den Einzel-App-Kioskmodus auswählen, nehmen Sie die folgenden Einstellungen vor:

- **Typ der Benutzeranmeldung**: Wählen Sie **Lokales Benutzerkonto** aus, um das lokale Benutzerkonto (auf dem Gerät) oder ein Microsoft-(MSA)-Konto einzugeben, das der Kiosk-App zugeordnet ist. Der Typ **Autologon** wird unter Windows Holographic for Business nicht unterstützt.

- **Anwendungstyp**: Wählen Sie **Store-App** aus.

- **App zur Ausführung im Kioskmodus**: Wählen Sie **Store-App hinzufügen** und eine App aus der Liste aus.

    Es sind keine Apps aufgelistet? Fügen Sie einige mithilfe der Schritte unter [Client-Apps](apps-add.md) hinzu.

    Klicken Sie auf **OK**, um die Änderungen zu speichern.

#### <a name="multi-app-kiosks"></a>Kiosks für mehrere Apps
Apps, die sich in diesem Modus befinden, sind über das Startmenü verfügbar. Diese Apps sind die einzigen Apps, die der Benutzer öffnen kann. Wenn Sie den Multi-App-Kioskmodus auswählen, nehmen Sie die folgenden Einstellungen vor:

- **Geräte unter Windows 10 im S Modus als Ziel verwenden**: Wählen Sie **Nein** aus. Der S Modus wird unter Windows Holographic for Business nicht unterstützt.

- **Typ der Benutzeranmeldung**: Fügen Sie mindestens ein Benutzerkonto hinzu, das die von Ihnen hinzugefügten Apps verwenden kann. Folgende Optionen sind verfügbar: 

  - **Automatische Anmeldung**: Diese Option wird unter Windows Holographic for Business nicht unterstützt.
  - **Lokale Benutzerkonten**: **Fügen** Sie das lokale Benutzerkonto (auf dem Gerät) hinzu. Das von Ihnen eingegebene Konto wird zum Anmelden im Kiosk verwendet.
  - **Azure AD-Benutzer oder Gruppe (Windows 10, Version 1803 und höher)**: Benutzer müssen ihre Anmeldeinformationen angeben, um sich auf dem Gerät anzumelden. Wählen Sie **Hinzufügen** aus, um Azure AD-Benutzer oder Gruppen aus der Liste auszuwählen. Sie können mehrere Benutzer und Gruppen auswählen. Wählen Sie **OK** aus, um die Änderungen zu speichern.
  - **HoloLens-Besucher**: Beim Besucherkonto handelt es sich um ein Gastkonto, für das weder Anmeldeinformationen noch eine Authentifizierung erforderlich sind. Weitere Informationen dazu finden Sie unter [shared PC mode concepts (Konzepte für den Modus freigegebener Computer)](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Anwendungen**: Wählen Sie die Apps aus, die auf dem Kioskgerät ausgeführt werden sollen. Denken Sie daran, dass Sie mehrere Apps hinzufügen können.

  - **Store-App hinzufügen**: Wählen Sie eine vorhandene App aus, die Sie mit [Client-Apps](apps-add.md) hinzugefügt haben. Wenn keine Apps aufgelistet sind, können Sie Apps abrufen und [Intune hinzufügen](store-apps-windows.md).
  - **Win32-App hinzufügen**: Diese Option wird unter Windows Holographic for Business nicht unterstützt.
  - **Nach AUMID hinzufügen**: Fügen Sie mit dieser Option Windows-Posteingangs-Apps hinzu. Geben Sie die folgenden Eigenschaften ein: 

    - **Anwendungsname**: Pflichtfeld. Geben Sie einen Namen für die Anwendung ein.
    - **Anwendungsbenutzermodell-ID (AUMID)**: Pflichtfeld. Geben Sie die AUMID der Windows-App ein. Weitere Informationen zum Abrufen dieser ID finden Sie unter [Ermitteln der Anwendungsbenutzermodell-ID einer installierten App](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Kachelgröße**: Pflichtfeld. Wählen Sie eine der folgenden App-Kachelgrößen aus: „Klein“, „Mittelgroß“, „Breit“ oder „Groß“.

- **Einstellungen für Kioskbrowser**: Diese Option wird unter Windows Holographic for Business nicht unterstützt.

- **Alternatives Startlayout verwenden**: Wählen Sie **Ja** aus, um eine XML-Datei einzugeben, die beschreibt, wie die Apps im Startmenü angezeigt werden, einschließlich der Reihenfolge. Verwenden Sie diese Option, wenn Sie in Ihrem Startmenü weitere Anpassungen vornehmen möchten. [Startlayout anpassen und exportieren](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens): Diese Option umfasst eine Anleitung und eine XML-Datei für Windows Holographic for Business-Geräte.

- **Windows-Taskleiste**: Diese Option wird unter Windows Holographic for Business nicht unterstützt.



## <a name="next-steps"></a>Nächste Schritte
[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
