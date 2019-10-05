---
title: Kioskeinstellungen für Windows- und Holographic-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Konfigurieren Sie Ihre Windows 10- (und höher) sowie Windows Holographic for Business-Geräte als Kiosks mit einer App oder mehreren Apps, und passen Sie das Startmenü an, fügen Sie Apps hinzu, zeigen Sie die Taskleiste an und konfigurieren Sie einen Webbrowser in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19641a36cf429773a8c0e06a90ee279d2baa06f7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723917"
---
# <a name="windows-10-and-windows-holographic-for-business-device-settings-to-run-as-a-dedicated-kiosk-using-intune"></a>Geräteeinstellungen bei Windows 10 und Windows Holographic for Business zur Ausführung als dedizierter Kiosk mit Intune

Verwenden Sie Intune, um Geräte mit Windows 10 als Kiosk auszuführen. Diese werden manchmal auch als dedizierte Geräte bezeichnet. Auf einem Gerät im Kioskmodus können eine oder mehrere Apps ausgeführt werden. Sie können ein Startmenü anzeigen und anpassen, verschiedene Apps hinzufügen, einschließlich Win32-Anwendungen, einem Webbrowser eine bestimmte Startseite hinzufügen und vieles mehr. 

Dieses Feature gilt für Geräte, die ausgeführt werden unter:

- Windows 10 und höher
- Windows Holographic for Business

Intune unterstützt ein Kioskprofil pro Gerät. Wenn Sie mehrere Kioskprofile auf einem einzelnen Gerät benötigen, können Sie einen [benutzerdefinierten OMA-URI](custom-settings-windows-10.md) verwenden.

Intune verwendet „Konfigurationsprofile“ zum Erstellen und Anpassen dieser Einstellungen für die Anforderungen Ihrer Organisation. Nachdem Sie diese Funktionen in einem Profil hinzugefügt haben, übertragen Sie diese Einstellungen mithilfe von Push auf Gruppen in Ihrer Organisation, oder stellen Sie sie für Gruppen bereit.

In diesem Artikel erfahren Sie, wie Sie ein Gerätekonfigurationsprofil erstellen. Eine Liste mit allen Einstellungen und ihren Funktionen finden Sie unter [Windows 10-Kioskeinstellungen](kiosk-settings-windows.md) und [Windows Holographic for Business-Geräteinstellungen zur Ausführung als Kiosk](kiosk-settings-holographic.md).

## <a name="create-the-profile"></a>Erstellen des Profils

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

   - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
   - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
   - **Plattform**: Wählen Sie **Windows 10 und höher** aus.
   - **Profiltyp**: Wählen Sie **Kiosk** aus.

4. Wählen Sie in **Einstellungen** einen **Kioskmodus** aus. **Kioskmodus:** Gibt den Typ des Kioskmodus an, der von der Richtlinie unterstützt wird. Zu den Optionen gehören:

    - **Nicht konfiguriert** (Standardeinstellung): Durch die Richtlinie kann der Kioskmodus nicht aktiviert werden.
    - **Einzelne App, Vollbildkiosk:** Das Gerät wird mit einem einzelnen Benutzerkonto ausgeführt und kann nur auf eine einzige Store-App zugreifen. Wenn sich der Benutzer anmeldet, wird so eine bestimmte App gestartet. Dieser Modus hindert den Benutzer auch daran, neue Apps zu öffnen oder die App zu ändern, die ausgeführt wird.
    - **Kiosk mit mehreren Apps:** Das Gerät führt mehrere Store-Apps, Win32-Apps oder Windows-Posteingangs-Apps unter Verwendung der Anwendungsbenutzermodell-ID (AUMID) aus. Nur die von Ihnen hinzugefügten Apps sind auf dem Gerät verfügbar.

        Der Vorteil eines Kiosks mit mehreren Apps oder eines Geräts mit festem Zweck ist ein leicht verständlicher Prozess für die Benutzer, da diese nur auf die Apps zugreifen, die sie benötigen. Apps, die sie nicht benötigen, werden aus der Ansicht entfernt.

    Eine Liste aller Einstellungen und ihrer Funktionen finden Sie unter:
      - [Windows 10-Kioskeinstellungen](kiosk-settings-windows.md)
      - [Windows Holographic for Business-Geräteinstellungen zur Ausführung als Kiosk](kiosk-settings-holographic.md)

5. Wenn Sie fertig sind, wählen Sie **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern. 

Das Profil wird erstellt und in der Profilliste angezeigt. [Weisen](device-profile-assign.md) Sie anschließend das Profil zu.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Sie können Kioskprofile für Geräte erstellen, die die folgenden Plattformen ausführen:
- [Android](device-restrictions-android.md#kiosk)
- [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)
- [Windows 10 und höher](kiosk-settings-windows.md)
- [Windows Holographic for Business](kiosk-settings-holographic.md)