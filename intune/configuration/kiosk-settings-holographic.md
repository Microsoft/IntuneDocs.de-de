---
title: Kioskeinstellungen für Windows Holographic for Business in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Konfigurieren Sie Ihre Windows Holographic for Business-Geräte als Kiosks mit einer App oder mehreren Apps, und passen Sie das Startmenü an, fügen Sie Apps hinzu, zeigen Sie die Taskleiste an und konfigurieren Sie einen Webbrowser in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e555c62030cede57e98e34034367831c298c0ced
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72492396"
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

- **Typ der Benutzeranmeldung**: Wählen Sie **Lokales Benutzerkonto** aus, um das lokale Benutzerkonto (auf dem Gerät) oder ein Microsoft-(MSA)-Konto einzugeben, das der Kiosk-App zugeordnet ist. Der Typ **Autologon** wird unter Windows Holographic for Business nicht unterstützt.

- **Anwendungstyp**: Wählen Sie **Store-App** aus.

- **App zur Ausführung im Kioskmodus**: Wählen Sie **Store-App hinzufügen** und eine App aus der Liste aus.

    Es sind keine Apps aufgelistet? Fügen Sie einige mithilfe der Schritte unter [Client-Apps](../apps/apps-add.md) hinzu.

    Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="multi-app-kiosks"></a>Kiosks für mehrere Apps

Apps, die sich in diesem Modus befinden, sind über das Startmenü verfügbar. Diese Apps sind die einzigen Apps, die der Benutzer öffnen kann. Wenn Sie den Multi-App-Kioskmodus auswählen, nehmen Sie die folgenden Einstellungen vor:

- **Geräte unter Windows 10 im S Modus als Ziel verwenden**: Wählen Sie **Nein** aus. Der S Modus wird unter Windows Holographic for Business nicht unterstützt.

- **Typ der Benutzeranmeldung**: Fügen Sie mindestens ein Benutzerkonto hinzu, das die von Ihnen hinzugefügten Apps verwenden kann. Folgende Optionen sind verfügbar: 

  - **Automatische Anmeldung**: Diese Option wird unter Windows Holographic for Business nicht unterstützt.
  - **Lokale Benutzerkonten**: **Fügen** Sie das lokale Benutzerkonto (auf dem Gerät) hinzu. Das von Ihnen eingegebene Konto wird zum Anmelden im Kiosk verwendet.
  - **Azure AD-Benutzer oder Gruppe (Windows 10, Version 1803 und höher)** : Benutzer müssen ihre Anmeldeinformationen angeben, um sich auf dem Gerät anzumelden. Wählen Sie **Hinzufügen** aus, um Azure AD-Benutzer oder Gruppen aus der Liste auszuwählen. Sie können mehrere Benutzer und Gruppen auswählen. Wählen Sie **OK** aus, um die Änderungen zu speichern.
  - **HoloLens-Besucher**: Beim Besucherkonto handelt es sich um ein Gastkonto, für das weder Anmeldeinformationen noch eine Authentifizierung erforderlich sind. Weitere Informationen dazu finden Sie unter [shared PC mode concepts (Konzepte für den Modus freigegebener Computer)](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Anwendungen**: Wählen Sie die Apps aus, die auf dem Kioskgerät ausgeführt werden sollen. Denken Sie daran, dass Sie mehrere Apps hinzufügen können.

  - **Hinzufügen von Store-Apps**: Wählen Sie eine vorhandene App aus, die Sie als [Client-apps](../apps/apps-add.md)in InTune hinzugefügt oder bereitgestellt haben. Wenn Sie keine apps aufgelistet haben, unterstützt InTune viele [App-Typen](../apps/apps-add.md) , die Sie [zu InTune hinzufügen](../apps/store-apps-windows.md).
  - **Win32-App hinzufügen**: Diese Option wird unter Windows Holographic for Business nicht unterstützt.
  - **Nach AUMID hinzufügen**: Fügen Sie mit dieser Option Windows-Posteingangs-Apps hinzu. Geben Sie die folgenden Eigenschaften ein: 

    - **Anwendungsname**: Pflichtfeld. Geben Sie einen Namen für die Anwendung ein.
    - **Anwendungsbenutzermodell-ID (AUMID)** : Pflichtfeld. Geben Sie die AUMID der Windows-App ein. Weitere Informationen zum Abrufen dieser ID finden Sie unter [Ermitteln der Anwendungsbenutzermodell-ID einer installierten App](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Kachelgröße**: Pflichtfeld. Wählen Sie eine der folgenden App-Kachelgrößen aus: „Klein“, „Mittelgroß“, „Breit“ oder „Groß“.

- **Einstellungen für Kioskbrowser**: Diese Option wird unter Windows Holographic for Business nicht unterstützt.

- **Alternatives Startlayout verwenden**: Wählen Sie **Ja** aus, um eine XML-Datei einzugeben, die beschreibt, wie die Apps im Startmenü angezeigt werden, einschließlich der Reihenfolge. Verwenden Sie diese Option, wenn Sie in Ihrem Startmenü weitere Anpassungen vornehmen möchten. [Startlayout anpassen und exportieren](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens): Diese Option umfasst eine Anleitung und eine XML-Datei für Windows Holographic for Business-Geräte.

- **Windows-Taskleiste**: Diese Option wird unter Windows Holographic for Business nicht unterstützt.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Außerdem können Sie Kioskprofile für [Android](device-restrictions-android.md#kiosk)-, [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)- und [Windows 10](kiosk-settings-windows.md)-Geräte erstellen.
