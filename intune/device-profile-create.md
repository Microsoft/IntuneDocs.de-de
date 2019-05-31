---
title: Erstellen von Geräteprofilen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Fügen Sie ein Gerätekonfigurationsprofil in Microsoft Intune hinzu, oder konfigurieren Sie eines. Wählen Sie den Plattformtyp aus, konfigurieren Sie die Einstellungen, und fügen Sie eine Bereichsmarkierung hinzu.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08c6ece37a4ff6eceaa4df735f365453a4bc7d88
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570402"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Erstellen eines Geräteprofils in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Mit Geräteprofilen können Sie Einstellungen hinzufügen und konfigurieren und diese anschließend mithilfe von Push an Geräte in Ihrer Organisation übertragen. Im Artikel [Apply features and settings on your devices using device profiles (Anwenden von Funktionen und Einstellungen auf Ihren Geräten mithilfe von Geräteprofilen in Microsoft Intune)](device-profiles.md) ist dies ausführlicher beschrieben. Sie erfahren dort u. a. mehr über die Möglichkeiten, die Sie dabei haben.

Inhalt dieses Artikels

- Schritte zum Erstellen eines Profils
- Hinzufügen einer Bereichsmarkierung zum „Filtern“ im Profil
- Check-In-Aktualisierungszykluszeiten, wenn Geräte Profile und Profilupdates erhalten

## <a name="create-the-profile"></a>Erstellen des Profils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.

2. Wählen Sie **Gerätekonfiguration** aus. Hierzu stehen Ihnen folgende Optionen zur Verfügung:

    - **Übersicht:** Hier werden die Status Ihrer Profile sowie weitere Details zu den Profilen angezeigt, die Sie Benutzern und Geräten zugewiesen haben.
    - **Verwalten:** Erstellen Sie Geräteprofile, und laden Sie benutzerdefinierte [PowerShell-Skripts](intune-management-extension.md) zur Ausführung im Profil hoch. Fügen Sie mit [eSIM](esim-device-configuration.md) Datenpläne zu Geräten hinzu.
    - **Überwachen:** Prüfen Sie den Status eines Profils, und zeigen Sie Protokolle zu Ihren Profilen an.
    - **Setup:** Fügen Sie eine Zertifizierungsstelle (SCEP oder PFX) hinzu, oder aktivieren Sie [Telecom Expense Management](telecom-expenses-monitor.md) für das Profil.

3. Wählen Sie **Profile** > **Profil erstellen** aus. Geben Sie die folgenden Eigenschaften ein:

   - **Name**: Geben Sie einen aussagekräftigen Namen für das Profil ein. Benennen Sie Ihre Profile, damit Sie diese später leicht wiedererkennen. Ein angemessener Profilname ist beispielsweise **WP email profile for entire company** (WP-E-Mail-Profil für das gesamte Unternehmen).
   - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
   - **Plattform**: Wählen Sie die Plattform Ihrer Geräte aus. Folgende Optionen sind verfügbar:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 und höher**
       - **Windows 10 und höher**

   - **Profiltyp**: Wählen Sie den Typ der Einstellungen aus, den Sie erstellen möchten. Die angezeigte Liste variiert je nach ausgewählter **Plattform**.
   - **Einstellungen:** Die folgenden Artikel beschreiben die Einstellungen für die einzelnen Profiltypen:

       - [Administrative Vorlagen](administrative-templates-windows.md)
       - [Benutzerdefiniert](custom-settings-configure.md)
       - [Übermittlungsoptimierung](delivery-optimization-windows.md)
       - [Gerätefeatures](device-features-configure.md)
       - [Geräteeinschränkungen](device-restrictions-configure.md)
       - [Editionsupgrade und Moduswechsel](edition-upgrade-configure-windows-10.md)
       - [Bildungswesen](education-settings-configure.md)
       - [E-Mail](email-settings-configure.md)
       - [Endpoint Protection](endpoint-protection-configure.md)
       - [Identity Protection](identity-protection-configure.md)  
       - [Kiosk](kiosk-settings.md)
       - [PKCS-Zertifikat](certficates-pfx-configure.md)
       - [SCEP-Zertifikat](certificates-scep-configure.md)
       - [ Vertrauenswürdiges Zertifikat](certificates-configure.md)
       - [Updaterichtlinien](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [WLAN](wi-fi-settings-configure.md)
       - [Windows Defender ATP](advanced-threat-protection.md)
       - [Windows Information Protection](windows-information-protection-configure.md)

     Wenn Sie beispielsweise **iOS** für die Plattform auswählen, werden Ihre Optionen für den Profiltyp wie folgt angezeigt:

     ![Erstellen eines iOS-Profils in Intune](./media/create-device-profile.png)

4. Wählen Sie anschließend **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern. Das Profil wird erstellt und in der Liste angezeigt.

## <a name="scope-tags"></a>Festlegen von Tags

Nachdem Sie die Einstellungen hinzugefügt haben, können Sie dem Profil ebenfalls eine Bereichsmarkierung hinzufügen. Bereichsmarkierungen weisen Richtlinien bestimmten Gruppen (wie der Personalabteilung oder Alle Mitarbeiter aus North Carolina (US)) zu und filtern diese Richtlinien.

Weitere Informationen zu Bereichsmarkierungen und Ihren Möglichkeiten finden Sie unter [Use role-based access control (RBAC) and scope tags for distributed IT (Verwenden der rollenbasierten Zugriffssteuerung sowie Bereichsmarkierungen für verteilte IT)](scope-tags.md).

### <a name="add-a-scope-tag"></a>Hinzufügen einer Bereichsmarkierung

1. Wählen Sie **Scope (Tags)** (Bereich (Markierungen)) aus.
2. Klicken Sie auf **Hinzufügen**, um eine neue Bereichsmarkierung zu erstellen. Wählen Sie alternativ eine Bereichsmarkierung aus der Liste aus.
3. Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="refresh-cycle-times"></a>Aktualisierungszykluszeit

Intune verwendet die folgenden Aktualisierungszyklen zur Prüfung auf Updates für Konfigurationsprofile:

| Plattform | Aktualisierungszyklus|
| --- | --- |
| iOS | Alle 6 Stunden |
| macOS | Alle 6 Stunden |
| Android | Alle 8 Stunden |
| Windows 10-PCs, die als Geräte registriert sind | Alle 8 Stunden |
| Windows Phone | Alle 8 Stunden |
| Windows 8.1 | Alle 8 Stunden |

Wenn das Gerät gerade registriert wurde, wird der Check-In häufiger durchgeführt:

| Plattform | Häufigkeit |
| --- | --- |
| iOS | Alle 15 Minuten für 6 Stunden und dann alle 6 Stunden |  
| macOS | Alle 15 Minuten für 6 Stunden und dann alle 6 Stunden | 
| Android | Alle 3 Minuten für 15 Minuten, dann alle 15 Minuten für 2 Stunden und dann alle 8 Stunden | 
| Windows 10-PCs, die als Geräte registriert sind | Alle 3 Minuten für 30 Minuten und dann alle 8 Stunden | 
| Windows Phone | Alle 5 Minuten für 15 Minuten, dann alle 15 Minuten für 2 Stunden und dann alle 8 Stunden | 
| Windows 8.1 | Alle 5 Minuten für 15 Minuten, dann alle 15 Minuten für 2 Stunden und dann alle 8 Stunden | 

Benutzer können jederzeit die Unternehmensportal-App öffnen und das Gerät synchronisieren, um sofort zu prüfen, ob neue Profilupdates verfügbar sind.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
