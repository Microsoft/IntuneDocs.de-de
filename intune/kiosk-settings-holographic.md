---
title: Kioskeinstellungen für Windows Holographic for Business in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Konfigurieren Sie Ihre Windows Holographic for Business-Geräte als Kiosks mit einer App oder mehreren Apps, und passen Sie das Startmenü an, fügen Sie Apps hinzu, zeigen Sie die Taskleiste an und konfigurieren Sie einen Webbrowser in Microsoft Intune.
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
ms.openlocfilehash: 8c5fd9998a4816775b3fc1d7803dc26e223b1e39
ms.sourcegitcommit: e5f501b396cb8743a8a9dea33381a16caadc51a9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2019
ms.locfileid: "56742431"
---
# <a name="windows-holographic-for-business-device-settings-to-run-as-a-kiosk-in-intune"></a>Geräteeinstellungen bei Windows Holographic for Business zur Ausführung als Kiosk in Intune

Sie können Windows Holographic for Business-Geräte so konfigurieren, dass sie im Single-App- oder im Multi-App-Kioskmodus ausgeführt werden. Einige Funktionen werden unter Windows Holographic for Business nicht unterstützt.

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie für Windows Holographic for Business-Geräte steuern können. Als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) verwenden Sie diese Einstellungen, um Ihre Geräte mit Windows Holographic for Business für die Ausführung im Kioskmodus zu konfigurieren.

Als Intune-Administrator können Sie für Ihre Geräte diese Einstellungen erstellen und ihnen zuweisen.

Weitere Informationen zur Windows-Kioskfunktion in Intune finden Sie unter [Konfigurieren der Kiosk-Einstellungen](kiosk-settings.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie das Profil.](kiosk-settings.md#create-the-profile)

## <a name="single-full-screen-app-kiosks"></a>Kiosk mit einzelner Vollbild-App

Wenn Sie den Einzel-App-Kioskmodus auswählen, nehmen Sie die folgenden Einstellungen vor:

- **Typ der Benutzeranmeldung:** Wählen Sie **Lokales Benutzerkonto** aus, um das lokale Benutzerkonto (auf dem Gerät) oder ein Microsoft-Konto (MSA) einzugeben, das der Kiosk-App zugeordnet ist. Der Typ **Autologon** wird unter Windows Holographic for Business nicht unterstützt.

- **Anwendungstyp:** Wählen Sie **Store-App** aus.

- **App zur Ausführung im Kioskmodus:** Klicken Sie auf **Store-App hinzufügen**, und wählen Sie eine App aus der Liste aus.

    Es sind keine Apps aufgelistet? Fügen Sie einige mithilfe der Schritte unter [Client-Apps](apps-add.md) hinzu.

    Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="multi-app-kiosks"></a>Kiosks für mehrere Apps

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

Außerdem können Sie Kioskprofile für [Android](device-restrictions-android.md#kiosk)-, [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)- und [Windows 10](kiosk-settings-windows.md)-Geräte erstellen.
