---
title: Vergleichen von Verwaltungsoptionen für Windows-PCs
titleSuffix: Microsoft Intune
description: Registrieren firmeneigener iOS-Geräte mithilfe des Apple-Programms zur Geräteregistrierung (DEP) oder Apple Configurator.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0dbd89a2a281f3a4d80737c284fb1a1ca5004616
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799421"
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>Vergleichen der Verwaltung von Windows-PCs als Computer oder mobile Geräte

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Organisationen können mit Microsoft Intune Windows-PCs entweder mithilfe der Verwaltung mobiler Geräte (Mobile Device Management, MDM) als mobile Geräte oder mithilfe des Intune-Softwareclients als Computer verwalten.  Microsoft empfiehlt, dass Kunden nach Möglichkeit die MDM-Verwaltungslösung nutzen. Damit Sie die Unterschiede zwischen diesen Optionen besser verstehen, werden die beiden Verwaltungsoptionen im folgenden Diagramm verglichen.

|**Funktionalität/Szenario** |**Windows-PC als Computer**<br>Intune-Softwareclient | **Windows-PC als Mobilgerät**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**Betriebssysteme** |Windows 10, Windows 8+, Windows 7, Windows Vista | Windows 10+ |
|**Unterstützung des Intune-Portals** |[Silverlight-Konsole](https://manage.microsoft.com)|[Azure-Portal](https://portal.azure.com) |
|**Bedingter Zugriff**|Nicht verfügbar|Verfügbar <br>[Was ist der bedingte Zugriff?](conditional-access.md)|
|**Massenregistrierung**|Nicht verfügbar|Verfügbar <br>[Massenregistrierung für Windows-Geräte](windows-bulk-enroll.md)|
|**Geräteprofile**|Nicht verfügbar|Verfügbar <br>[Was sind Microsoft Intune-Geräteprofile?](device-profiles.md)|
|**Registrierung ohne Agents**|Nicht verfügbar |Verfügbar<br>[Registrieren von Windows-Geräten](windows-enroll.md)|
|**Softwareupdateverwaltung**| Windows-Updates und Microsoft-App-Updates<br>[Aktualisieren Ihrer Windows-PCs mit Softwareupdates](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)|Microsoft-Store für Unternehmen für Windows 10 und Microsoft-Apps-Updates<br> [Konfigurieren von Einstellungen für Windows Update for Business](windows-update-for-business-configure.md) |
|**Softwarelizenzverwaltung**|Verfügbar <br>[Verwalten von Lizenzverträgen für Windows-PC-Software](manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)|Microsoft Store für Unternehmen (nur APPX-Apps)<br>[Verwalten von Apps, die im Microsoft Store für Unternehmen erworben wurden](windows-store-for-business.md)|
|**Inventur**|Verfügbar <br>[Anzeigen des Hardware- und Softwarebestands für Windows-PCs](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md)|Verfügbar <br>[Überwachen von App-Informationen](apps-monitor.md)<br>[Was ist die Geräteverwaltung?](device-management.md)|
|**Windows-Firewall-Richtlinie**|Verfügbar <br>[Unterstützen des Schutzes von Windows-PCs mithilfe von Windows-Firewall-Richtlinien](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) |Verfügbar <br>[Windows Defender Firewall](endpoint-protection-windows-10.md#windows-defender-firewall)|
|**Schutz vor Schadsoftware**|Endpoint Protection<br>[Schützen von Windows-PCs mit Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)|Windows Defender<br>[Aktivieren von Windows Defender](advanced-threat-protection.md)|
|**Remoteunterstützung** |TeamViewer<br>[Anfordern und Bereitstellen von Remoteunterstützung für Windows-PCs](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md)|TeamViewer<br> [Verwenden von TeamViewer für die Remoteverwaltung von Intune-Geräten](device-profile-android-teamviewer.md) |
|**App-Bereitstellung** | Für Microsoft Store für Unternehmen nicht verfügbar.<br>Nur EXE- und APPX-Dateien sowie aus mehreren Dateien bestehende MSI-Pakete<br>[Hinzufügen von Apps für Windows-PCs, auf denen der Intune-Softwareclient ausgeführt wird](add-apps-for-windows-pcs-in-microsoft-intune.md)|Für Microsoft Store-Apps und branchenspezifische Apps verfügbar<br>[Hinzufügen von Windows Store-Apps](store-apps-windows.md)<br>[How to add Windows line-of-business (LOB) apps (Informationen zum Hinzufügen branchenspezifischer Apps)](lob-apps-windows.md)|
|**App-Schutz**|Nicht verfügbar|Verfügbar <br>[Was sind App-Schutzrichtlinien?](app-protection-policy.md)|
|**Integritätsnachweis**|Nicht verfügbar|Verfügbar|


### <a name="advantages-of-mdm-windows-pc-management"></a>Vorteile der Verwaltung von Windows-PCs mit MDM
Die Verwaltung von Windows-PCs mithilfe der modernen Verwaltung mobiler Geräte (MDM) bietet folgende Vorteile:
- **Skalierbarkeit**: Die MDM-Verwaltung wird mit der Intune-Cloudverwaltung skaliert. Die Intune-Softwareclient ist auf 7.000 PCs beschränkt.
- **Einfachheit**: Die MDM-Lösung verwendet moderne Verwaltungsfunktionen, die im Betriebssystem enthalten ist, ohne Rückgriff auf einen heruntergeladenen Softwareclient.
- **Einheitlichkeit**: Ihre Windows-PCs werden wie alle anderen mobilen Geräte in Ihrer Organisation verwaltet.
<!-- - **Cloud optimization** - -->
