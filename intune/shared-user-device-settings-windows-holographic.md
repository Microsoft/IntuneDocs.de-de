---
title: 'Einstellungen für gemeinsam genutzte Windows Holographic for Business-Geräte – Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Fügen Sie Windows Holographic for Business hinzu, um Geräte zu konfigurieren, die gemeinsam genutzt oder von mehreren Benutzern in Microsoft Intune verwendet werden. Hier finden Sie die Einstellungen für die Kontoverwaltung und ihren Auswirkungen auf die Geräte (einschließlich Microsoft HoloLens).
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 428025e5e56450fd859f6bf2c9a990cbdca4f263
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835111"
---
# <a name="windows-holographic-for-business-settings-to-manage-shared-devices-using-intune"></a>Windows Holographic for Business-Einstellungen zum Verwalten gemeinsam genutzter Geräte in Intune

Windows Holographic for Business-Geräte, z.B. Microsoft HoloLens, können von mehreren Benutzern verwendet werden. Geräte mit mehreren Benutzern werden als „gemeinsam genutzte Geräte“ bezeichnet und sind in den Lösungen für die mobile Geräteverwaltung (Mobile Device Management, MDM) enthalten.

Mithilfe von Microsoft Intune können Benutzer sich bei gemeinsam genutzten Geräten mit einem Gastkonto anmelden. Bei der Verwendung des Geräts erhalten diese Benutzer dann nur Zugriff auf von Ihnen ausgewählte Features.

In diesem Artikel werden die Einstellungen aufgeführt und beschrieben, die in einem Gerätekonfigurationsprofil für Windows Holographic for Business verwendet werden können. Nach dem Erstellen des Profils in Intune stellen Sie das Profil für die Gerätegruppen in Ihrer Organisation bereit oder weisen es diesen zu. Sie können dieses Profil ebenfalls zu Gerätegruppen mit gemischten Gerätetypen und Betriebssystemversionen zuweisen.

Weitere Informationen zu diesem Intune-Feature finden Sie unter [Control access, accounts, and power features on shared PC or multi-user devices (Features für das Steuern von Zugriff, Konten und Energieeinstellungen auf gemeinsam genutzten Computern oder Geräten mit mehreren Benutzern)](shared-user-device-settings.md). Weitere Informationen zum Windows-Konfigurationsdienstanbieter (Configuration Service Provider, CSP) finden Sie unter [AccountManagement CSP (Konfigurationsdienstanbieter „AccountManagement“)](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp).

## <a name="before-your-begin"></a>Vorbereitungen

[Erstellen Sie das Profil.](shared-user-device-settings.md)

## <a name="shared-multi-user-device-settings"></a>Einstellungen für von mehreren Benutzern gemeinsam genutzte Geräte

> [!NOTE]
> Unter Windows Holographic for Business ausgeführte Geräte, z.B. Microsoft HoloLens, unterstützen ausschließlich die Einstellungen der **Kontoverwaltung**. Wenn Sie eine der anderen in Intune angezeigten Einstellungen konfigurieren (wie z.B. **Modus für die gemeinsame PC-Nutzung**), hat dies keine Auswirkungen auf diese Geräte.

- **Kontoverwaltung:** Legen Sie diese Option auf **Aktivieren** fest, damit lokale Gastkonten und Konten in AD und Azure AD automatisch gelöscht werden. Wenn ein Benutzer sich von einem Gerät abmeldet oder die Systemwartung ausgeführt wird, werden diese Konten gelöscht. Wenn diese Option aktiviert ist, sollten sie auch die folgenden festlegen:
  - **Kontolöschung:** Legen Sie fest, wann Konten gelöscht werden sollen: **Bei Erreichen des Schwellenwerts für Speicherplatz**, **Bei Erreichen des Schwellenwerts für Speicherplatz und inaktive Konten** oder **Sofort nach der Abmeldung**. Geben Sie außerdem Folgendes ein:
    - **Schwellenwert (%) für das Starten von Löschungen:** Geben Sie einen Prozentsatz (0 – 100) für den Speicherplatz ein. Wenn der gesamte Speicherplatz unter den eingegebenen Wert fällt, werden die zwischengespeicherten Konten gelöscht. Es werden fortlaufend Konten gelöscht, um Speicherplatz freizugeben. Die Konten, die am längsten inaktiv sind, werden zuerst gelöscht.
    - **Schwellenwert (%) für das Beenden von Löschungen:** Geben Sie einen Prozentsatz (0 – 100) für den Speicherplatz ein. Wenn der gesamte Speicherplatz dem eingegebenen Wert entspricht, werden keine Konten mehr gelöscht.

  Legen Sie die Option auf **Deaktivieren** fest, um die lokalen, AD- und Azure AD-Gastkonten beizubehalten.

  > [!NOTE]
  > Microsoft HoloLens-Geräte unterstützen ausschließlich die Einstellungen der **Kontoverwaltung**.

## <a name="next-steps"></a>Nächste Schritte

- [Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
- Sehen Sie sich die Einstellungen für [Windows 10 und höher](shared-user-device-settings-windows.md) an.
