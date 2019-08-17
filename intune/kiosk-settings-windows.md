---
title: Kioskeinstellungen für Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Konfigurieren Sie Ihre Geräte mit Windows 10 (und höher) als Kiosks mit einer App oder mehreren Apps, und passen Sie das Startmenü an, fügen Sie Apps hinzu, zeigen Sie die Taskleiste an und konfigurieren Sie einen Webbrowser in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6fb1111a7f660e8c59f45fb1893364dcadd34dca
ms.sourcegitcommit: 6a8de7bb4870ea19aa08db1f188ea7b5e8a387dd
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "69487753"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Geräteeinstellungen bei Windows 10 (und höher) zur Ausführung als Kiosk in Intune

Sie können Geräte mit Windows 10 und höher so konfigurieren, dass sie im Single-App- oder im Multi-App-Kioskmodus ausgeführt werden.

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie auf Geräten mit Windows 10 und höher festlegen können. Als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) verwenden Sie diese Einstellungen, um Ihre Geräte mit Windows 10 und höher für die Ausführung im Kioskmodus zu konfigurieren.

Als Intune-Administrator können Sie Ihre Geräte diese Einstellungen erstellen und zuweisen.

Weitere Informationen zur Windows-Kioskfunktion in Intune finden Sie unter [Konfigurieren der Kiosk-Einstellungen](kiosk-settings.md).

## <a name="before-you-begin"></a>Vorbereitung

- [Erstellen Sie das Profil.](kiosk-settings.md#create-the-profile)

- Dieses Kioskprofil steht in direktem Zusammenhang mit dem Geräteeinschränkungsprofil, das Sie mithilfe der [Microsoft Edge-Kioskeinstellungen](device-restrictions-windows-10.md#microsoft-edge-browser) erstellen. Zusammenfassung:

  1. Erstellen Sie das Kioskprofil, um das Gerät im Kioskmodus auszuführen.
  2. Erstellen Sie das [Geräteeinschränkungsprofil](device-restrictions-windows-10.md#microsoft-edge-browser), und konfigurieren Sie spezifische Features und Einstellungen, die in Microsoft Edge zulässig sind.

> [!IMPORTANT] 
> Achten Sie darauf, dass Sie dieses Kioskprofil den gleichen Geräten wie Ihr [Microsoft Edge-Profil](device-restrictions-windows-10.md#microsoft-edge-browser) zuweisen.

## <a name="single-full-screen-app-kiosks"></a>Kiosk mit einzelner Vollbild-App

Hiermit wird nur eine App auf dem Gerät ausgeführt.

- **Auswahl des Kioskmodus:** Wählen Sie die Option **Einzelne App, Vollbildkiosk**.

- **Typ der Benutzeranmeldung**: Die Apps, die Sie hinzufügen, werden als das von Ihnen eingegebene Benutzerkonto ausgeführt. Folgende Optionen sind verfügbar:

  - **Automatische Anmeldung (Windows 10, Version 1803 und höher)** : Für Kioske in öffentlichen Umgebungen, die keine Benutzeranmeldung erfordern, ähnlich einem Gastkonto. Diese Einstellung verwendet [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Lokales Benutzerkonto**: Geben Sie das lokale Benutzerkonto (auf dem Gerät) an. Das von Ihnen eingegebene Konto wird zum Anmelden im Kiosk verwendet.

- **Anwendungstyp:** Wählen Sie den Anwendungstyp aus. Folgende Optionen sind verfügbar:

  - **Microsoft Edge-Browser hinzufügen:** Klicken Sie auf **Microsoft Edge-Browser**, und wählen Sie den **Microsoft Edge-Kioskmodustyp** aus:

    - **Digitale/interaktive Beschilderung:** Öffnet eine URL im Vollbildmodus und zeigt nur den Inhalt dieser Website an. Weitere Informationen zu diesem Feature finden Sie unter [Einrichten digitaler Beschilderungen](https://docs.microsoft.com/windows/configuration/setup-digital-signage).
    - **Öffentliches Browsing (InPrivate):** Führt eine Version von Microsoft Edge mit mehreren Registerkarten aus. Benutzer können öffentlich browsen oder ihre Sitzung beenden.

    Weitere Informationen zu diesen Optionen finden Sie unter [Bereitstellen des Microsoft Edge-Kioskmodus](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

    > [!NOTE]
    > Mit dieser Einstellung wird der Microsoft Edge-Browser auf dem Gerät aktiviert. Erstellen Sie zum Konfigurieren spezifischer Microsoft Edge-Einstellungen ein Gerätekonfigurationsprofil (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10** (Plattform) > **Geräteeinschränkungen** >  **Microsoft Edge-Browser**). Der [Microsoft Edge-Browser](device-restrictions-windows-10.md#microsoft-edge-browser) führt alle Einstellungen und Beschreibungen dieser auf.

  - **Kioskbrowser hinzufügen:** Klicken Sie auf **Einstellungen für Kioskbrowser**. Mit diesen Einstellungen können Sie die Webbrowser-App im Kiosk steuern. Stellen Sie sicher, dass Sie die [Kiosk Browser-App](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) aus dem Store erhalten, und fügen Sie Sie als [Client-App](apps-add.md)zu InTune hinzu. Anschließend können Sie die APP den Kiosk Geräten zuweisen.

    Legen Sie folgende Einstellungen fest:

    - **URL der Standardhomepage**: Geben Sie die Standard-URL ein, die angezeigt wird, wenn der Kioskbrowser geöffnet oder neu gestartet wird. Geben Sie beispielsweise `http://bing.com` oder `http://www.contoso.com` ein.

    - **Startschaltfläche**: Sie haben die beiden Optionen, die Startschaltfläche des Kioskbrowsers **einzublenden** oder **auszublenden**. Standardmäßig wird die Schaltfläche ausgeblendet.

    - **Navigationsschaltflächen**: Sie können die Schaltflächen „Vorwärts“ und „Zurück“ **einblenden** oder **ausblenden**. Standardmäßig werden sie ausgeblendet.

    - **Schaltfläche „Sitzung beenden“** : Sie können diese Schaltfläche **einblenden** oder **ausblenden**. Wenn die Schaltfläche angezeigt wird, tippt der Benutzer darauf, und die App fragt, ob die Sitzung beendet werden soll. Wenn dies bestätigt wird, löscht der Browser alle Browserdaten (z.B. Cookies und Cache) und öffnet dann die Standard-URL. Standardmäßig wird die Schaltfläche ausgeblendet.

    - **Browser nach Leerlaufzeit aktualisieren**: Geben Sie die Leerlaufzeit ein (1–1.440 Minuten), nach der der Kioskbrowser im aktualisierten Zustand neu gestartet wird. Die Leerlaufzeit ist die Anzahl von Minuten seit der letzten Benutzerinteraktion. Standardmäßig ist der Wert leer, d.h., es gibt kein Leerlauftimeout.

    - **Zugelassene Websites**: Verwenden Sie diese Einstellung, um das Öffnen bestimmter Websites zu ermöglichen. Mithilfe dieser Funktion können Sie also auf dem Gerät den Zugriff auf bestimmte Websites einschränken oder verhindern. Sie können z.B. gewähren, dass alle Websites unter `http://contoso.com*` geöffnet werden. Standardmäßig sind alle Websites zulässig.

      Um den Zugriff auf bestimmte Websites zu erlauben, laden Sie eine Datei mit einer in Zeilen unterteilten Liste der zulässigen Websites hoch. Wenn Sie keine Datei hinzufügen, können alle Websites aufgerufen werden. Intune unterstützt „`*`“ (Sternchen) als Platzhalter.

      Die Beispieldatei sollte der folgenden Beispielliste ähnlich sein:

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`

    > [!NOTE]
    > Bei Windows 10-Kiosken, die mit dem Microsoft Kiosk-Browser aktiviert sind, muss eine Offline Lizenz aus der Microsoft Store für Unternehmen verwendet werden. Diese Anforderung liegt daran, dass bei der automatischen Anmeldung ein lokales Benutzerkonto ohne Azure Active Directory (AD)-Anmelde Informationen verwendet wird. Online Lizenzen können daher nicht ausgewertet werden. Weitere Informationen finden Sie unter [Verteilen von Offline-Apps](https://docs.microsoft.com/microsoft-store/distribute-offline-apps).

  - **Store-App hinzufügen:** Klicken Sie auf **Store-App hinzufügen**, und wählen Sie eine App aus der Liste aus.

    Es sind keine Apps aufgelistet? Fügen Sie einige mithilfe der Schritte unter [Client-Apps](apps-add.md) hinzu.

## <a name="multi-app-kiosks"></a>Kiosks für mehrere Apps

Apps, die sich in diesem Modus befinden, sind über das Startmenü verfügbar. Diese Apps sind die einzigen Apps, die der Benutzer öffnen kann. Wenn bei einer App eine Abhängigkeit von einer anderen App vorliegt, müssen beide in der Liste zulässiger Apps enthalten sein. Internet Explorer (64-Bit) weist beispielsweise eine Abhängigkeit von Internet Explorer (32-Bit) auf, d. h., Sie müssen sowohl „C:\Programme\internet explorer\iexplore.exe“ als auch „C:\Programme (x86)\Internet Explorer\iexplore.exe“ zulassen. 

- **Kioskmodus auswählen:** Wählen Sie die Option **Kiosk mit mehreren Apps** aus.

- **Geräte unter Windows 10 im S Modus als Ziel verwenden:**
  - **Ja**: Store-Apps und AUMID-Apps werden im Kioskprofil erlaubt (ausgenommen Win32-Apps).
  - **Nein**: Store-Apps, Win32-Apps und AUMID-Apps werden im Kioskprofil erlaubt. Dieses Kioskprofil wird auf Geräten im S-Modus nicht bereitgestellt.

- **Typ der Benutzeranmeldung**: Die Apps, die Sie hinzufügen, werden als das von Ihnen eingegebene Benutzerkonto ausgeführt. Folgende Optionen sind verfügbar:

  - **Automatische Anmeldung (Windows 10, Version 1803 und höher)** : Für Kioske in öffentlichen Umgebungen, die keine Benutzeranmeldung erfordern, ähnlich einem Gastkonto. Diese Einstellung verwendet [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Lokales Benutzerkonto**: **Fügen** Sie das lokale Benutzerkonto (auf dem Gerät) hinzu. Das von Ihnen eingegebene Konto wird zum Anmelden im Kiosk verwendet.
  - **Azure AD-Benutzer oder -Gruppe (Windows 10, Version 1803 und höher)** : Wählen Sie **Hinzufügen** und anschließend Azure AD-Benutzer oder -Gruppen aus der Liste aus. Sie können mehrere Benutzer und Gruppen auswählen. Wählen Sie **OK** aus, um die Änderungen zu speichern.
  - **HoloLens-Besucher**: Beim Besucherkonto handelt es sich um ein Gastkonto, für das weder Anmeldeinformationen noch eine Authentifizierung erforderlich sind. Weitere Informationen dazu finden Sie unter [shared PC mode concepts (Konzepte für den Modus freigegebener Computer)](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Browser und Anwendungen**: Fügen Sie die Apps hinzu, die auf dem Kioskgerät ausgeführt werden sollen. Denken Sie daran, dass Sie mehrere Apps hinzufügen können.

  - **Browser**

    - **Microsoft Edge hinzufügen:** Microsoft Edge wird dem App-Raster hinzugefügt, und alle Anwendungen können in diesem Kiosk ausgeführt werden. Wählen Sie den **Microsoft Edge-Kioskmodustyp** aus:

      - **Normalmodus (Vollversion von Microsoft Edge):** Führt eine Vollversion von Microsoft Edge mit allen Browsingfeatures aus. Benutzerdaten und -zustand werden zwischen Sitzungen beibehalten.
      - **Öffentliches Browsing (InPrivate):** Führt eine Version von Microsoft Edge InPrivate mit mehreren Registerkarten mit einer für Kioske ausgelegten Benutzeroberfläche im Vollbildmodus aus.

      Weitere Informationen zu diesen Optionen finden Sie unter [Bereitstellen des Microsoft Edge-Kioskmodus](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

      > [!NOTE]
      > Mit dieser Einstellung wird der Microsoft Edge-Browser auf dem Gerät aktiviert. Erstellen Sie zum Konfigurieren spezifischer Microsoft Edge-Einstellungen ein Gerätekonfigurationsprofil (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10** (Plattform) > **Geräteeinschränkungen** >  **Microsoft Edge-Browser**). Der [Microsoft Edge-Browser](device-restrictions-windows-10.md#microsoft-edge-browser) führt alle Einstellungen und Beschreibungen dieser auf.

    - **Kioskbrowser hinzufügen**: Mit diesen Einstellungen können Sie eine Webbrowser-App im Kiosk steuern. Achten Sie darauf, dass Sie eine Webbrowser-App auf dem Kioskgerät über [Client-Apps](apps-add.md) bereitstellen.

      Legen Sie folgende Einstellungen fest:

      - **URL der Standardhomepage**: Geben Sie die Standard-URL ein, die angezeigt wird, wenn der Kioskbrowser geöffnet oder neu gestartet wird. Geben Sie beispielsweise `http://bing.com` oder `http://www.contoso.com` ein.

      - **Startschaltfläche**: Sie haben die beiden Optionen, die Startschaltfläche des Kioskbrowsers **einzublenden** oder **auszublenden**. Standardmäßig wird die Schaltfläche ausgeblendet.

      - **Navigationsschaltflächen**: Sie können die Schaltflächen „Vorwärts“ und „Zurück“ **einblenden** oder **ausblenden**. Standardmäßig werden sie ausgeblendet.

      - **Schaltfläche „Sitzung beenden“** : Sie können diese Schaltfläche **einblenden** oder **ausblenden**. Wenn die Schaltfläche angezeigt wird, tippt der Benutzer darauf, und die App fragt, ob die Sitzung beendet werden soll. Wenn dies bestätigt wird, löscht der Browser alle Browserdaten (z.B. Cookies und Cache) und öffnet dann die Standard-URL. Standardmäßig wird die Schaltfläche ausgeblendet.

      - **Browser nach Leerlaufzeit aktualisieren**: Geben Sie die Leerlaufzeit ein (1–1.440 Minuten), nach der der Kioskbrowser im aktualisierten Zustand neu gestartet wird. Die Leerlaufzeit ist die Anzahl von Minuten seit der letzten Benutzerinteraktion. Standardmäßig ist der Wert leer, d.h., es gibt kein Leerlauftimeout.

      - **Zugelassene Websites**: Verwenden Sie diese Einstellung, um das Öffnen bestimmter Websites zu ermöglichen. Mithilfe dieser Funktion können Sie also auf dem Gerät den Zugriff auf bestimmte Websites einschränken oder verhindern. Sie können z.B. gewähren, dass alle Websites unter `contoso.com*` geöffnet werden. Standardmäßig sind alle Websites zulässig.

        Um den Zugriff auf bestimmte Websites zu erlauben, laden Sie eine CSV-Datei mit einer Liste der zulässigen Websites hoch. Wenn Sie keine CSV-Datei hinzufügen, können alle Websites aufgerufen werden.

      > [!NOTE]
      > Bei Windows 10-Kiosken, die mit dem Microsoft Kiosk-Browser aktiviert sind, muss eine Offline Lizenz aus der Microsoft Store für Unternehmen verwendet werden. Diese Anforderung liegt daran, dass bei der automatischen Anmeldung ein lokales Benutzerkonto ohne Azure Active Directory (AD)-Anmelde Informationen verwendet wird. Online Lizenzen können daher nicht ausgewertet werden. Weitere Informationen finden Sie unter [Verteilen von Offline-Apps](https://docs.microsoft.com/microsoft-store/distribute-offline-apps).

  - **Anwendungen**

    - **Store-App hinzufügen**: Fügen Sie eine App aus dem Microsoft Store für Unternehmen hinzu. Wenn keine Apps aufgelistet sind, können Sie Apps abrufen und [Intune hinzufügen](store-apps-windows.md). Beispielsweise lassen sich der Kioskbrowser, Excel und OneNote hinzufügen.

    - **Win32-App hinzufügen**: Eine Win32-App ist eine klassische Desktop-App wie Visual Studio Code oder Google Chrome. Geben Sie die folgenden Eigenschaften ein:

      - **Anwendungsname**: Pflichtfeld. Geben Sie einen Namen für die Anwendung ein.
      - **Lokaler Pfad**: Pflichtfeld. Geben Sie den Pfad zur ausführbaren Datei ein, z.B. `C:\Program Files (x86)\Microsoft VS Code\Code.exe` oder `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
      - **Anwendungsbenutzermodell-ID (AUMID):** Geben Sie die AUMID der Win32-App ein. Diese Einstellung bestimmt das Startlayout der Kachel auf dem Desktop. Informationen zum Abrufen dieser ID finden Sie unter [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).

    - **Nach AUMID hinzufügen**: Mit dieser Option können Sie Windows-Posteingangs-Apps wie Editor oder Rechner hinzufügen. Geben Sie die folgenden Eigenschaften ein:

      - **Anwendungsname**: Pflichtfeld. Geben Sie einen Namen für die Anwendung ein.
      - **Anwendungsbenutzermodell-ID (AUMID)** : Pflichtfeld. Geben Sie die AUMID der Windows-App ein. Weitere Informationen zum Abrufen dieser ID finden Sie unter [Ermitteln der Anwendungsbenutzermodell-ID einer installierten App](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

    - **AutoLaunch:** Optional. Wählen Sie eine Anwendung aus, die automatisch gestartet werden soll, wenn der Benutzer sich anmeldet. Nur eine App kann mit AutoLaunch automatisch gestartet werden.
    - **Kachelgröße**: Pflichtfeld. Wählen Sie eine der folgenden App-Kachelgrößen aus: „Klein“, „Mittelgroß“, „Breit“ oder „Groß“.

  > [!TIP]
  > Nachdem Sie alle Apps hinzugefügt haben, können Sie die Anzeigereihenfolge ändern, indem Sie auf die Apps in der Liste klicken und sie dann verschieben.  

- **Alternatives Startlayout verwenden**: Wählen Sie **Ja** aus, um eine XML-Datei einzugeben, die beschreibt, wie die Apps im Startmenü angezeigt werden, einschließlich der Reihenfolge. Verwenden Sie diese Option, wenn Sie in Ihrem Startmenü weitere Anpassungen vornehmen möchten. [Anpassen und Exportieren des Startlayouts](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout): bietet Anweisungen und XML-Beispiele.

- **Windows-Taskleiste**: Sie können die Taskleiste **einblenden** oder **ausblenden**. Standardmäßig wird sie ausgeblendet. Symbole, z.B. das WLAN-Symbol werden dargestellt, die Einstellungen können jedoch nicht vom Endbenutzer geändert werden.

- **Zugriff auf Downloadordner zulassen:** Klicken Sie auf **Ja**, um Benutzern den Zugriff auf den Downloadordner in Windows Explorer zu gewähren. Der Zugriff auf den Downloadordner ist standardmäßig deaktiviert. Dieses Feature wird häufig verwenden, um Endbenutzern den Zugriff auf Elemente zu gewähren, die über einen Browser heruntergeladen wurden.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Außerdem können Sie Kioskprofile für Geräte mit [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings), and [Windows Holographic for Business](kiosk-settings-holographic.md) erstellen.
