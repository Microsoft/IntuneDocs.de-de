---
title: Vergleichen von Verwaltungsoptionen für Windows-PCs
description: Registrieren firmeneigener iOS-Geräte mithilfe des Apple Device Enrollment Program (DEP) oder Apple Configurator
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/27/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e2e341e8b8befa43106673607bd5c5264dd18db0
ms.sourcegitcommit: 2162ed46d939b4a9b85fa4e7e9943f2fb5948f1e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
ms.locfileid: "31617265"
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>Vergleichen der Verwaltung von Windows-PCs als Computer oder mobile Geräte

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Organisationen können mit Microsoft Intune Windows-PCs entweder mithilfe der Verwaltung mobiler Geräte (Mobile Device Management, MDM) als mobile Geräte oder mithilfe des Intune-Softwareclients als Computer verwalten.  Microsoft empfiehlt, dass Kunden nach Möglichkeit die MDM-Verwaltungslösung nutzen. Damit Sie die Unterschiede zwischen diesen Optionen besser verstehen, werden die beiden Verwaltungsoptionen im folgenden Diagramm verglichen.

|**Funktionalität/Szenario** |**Windows-PC als Computer**<br>Intune-Softwareclient | **Windows-PC als Mobilgerät**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**Betriebssysteme** |Windows 10, Windows 8+, Windows 7, Windows Vista | Windows 10+ |
|**Unterstützung des Intune-Portals** |[Silverlight-Konsole](https://manage.microsoft.com)|[Azure-Portal](https://portal.azure.com) |
|**Bedingter Zugriff**|Nicht verfügbar|Verfügbar <br>[Was ist der bedingte Zugriff?](https://docs.microsoft.com/intune-azure/conditional-access/what-is-conditional-access)|
|**Massenregistrierung**|Nicht verfügbar|Verfügbar <br>[Massenregistrierung für Windows-Geräte](https://docs.microsoft.com/intune-azure/enroll-devices/bulk-enroll-windows)|
|**Geräteprofile**|Nicht verfügbar|Verfügbar <br>[Was sind Microsoft Intune-Geräteprofile?](https://docs.microsoft.com/intune-azure/configure-devices/what-are-device-profiles)|
|**Registrierung ohne Agents**|Nicht verfügbar |Verfügbar<br>[Registrieren von Windows-Geräten](https://docs.microsoft.com/intune-azure/enroll-devices/enroll-windows-devices)|
|**Softwareupdateverwaltung**| Windows-Updates und Microsoft-App-Updates<br>[Aktualisieren Ihrer Windows-PCs mit Softwareupdates](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)|Microsoft-Store für Unternehmen für Windows 10 und Microsoft-Apps-Updates<br> [Konfigurieren von Einstellungen für Windows Update for Business](https://docs.microsoft.com/intune-azure/configure-devices/how-to-configure-windows-update-for-business) |
|**Softwarelizenzverwaltung**|Verfügbar <br>[Verwalten von Lizenzverträgen für Windows-PC-Software](https://docs.microsoft.com/intune/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)|Microsoft Store für Unternehmen (nur APPX-Apps)<br>[Verwalten von Apps, die im Microsoft Store für Unternehmen erworben wurden](https://docs.microsoft.com/intune-azure/manage-apps/wsfb-apps)|
|**Inventur**|Verfügbar <br>[Anzeigen des Hardware- und Softwarebestands für Windows-PCs](https://docs.microsoft.com/intune/deploy-use/view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune)|Verfügbar <br>[Überwachen von App-Informationen](https://docs.microsoft.com/intune/apps-monitor)<br>[Was ist die Geräteverwaltung?](https://docs.microsoft.com/intune/device-management)|
|**Windows-Firewall-Richtlinie**|Verfügbar <br>[Unterstützen des Schutzes von Windows-PCs mithilfe von Windows-Firewall-Richtlinien](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune) |Verfügbar <br>[Windows Defender Firewall](https://docs.microsoft.com/en-us/intune/endpoint-protection-windows-10#windows-defender-firewall)|
|**Schutz vor Schadsoftware**|Endpoint Protection<br>[Schützen von Windows-PCs mit Endpoint Protection](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)|Windows Defender<br>[Windows Defender-Einstellungen](https://docs.microsoft.com/intune-azure/configure-devices/custom-for-windows-10#windows-defender-settings)|
|**Remoteunterstützung** |TeamViewer<br>[Anfordern und Bereitstellen von Remoteunterstützung für Windows-PCs](https://docs.microsoft.com/intune/deploy-use/request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune)|TeamViewer<br> [Verwenden von TeamViewer für die Remoteverwaltung von Intune-Geräten](https://docs.microsoft.com/en-us/intune/device-profile-android-teamviewer) |
|**App-Bereitstellung** | Für Microsoft Store für Unternehmen nicht verfügbar.<br>Nur EXE- und APPX-Dateien sowie aus mehreren Dateien bestehende MSI-Pakete<br>[Hinzufügen von Apps für Windows-PCs, auf denen der Intune-Softwareclient ausgeführt wird](https://docs.microsoft.com/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)|Für Microsoft Store-Apps und branchenspezifische Apps verfügbar<br>[Hinzufügen von Windows Store-Apps](https://docs.microsoft.com/intune/store-apps-windows)<br>[How to add Windows line-of-business (LOB) apps (Informationen zum Hinzufügen branchenspezifischer Apps)](https://docs.microsoft.com/intune/lob-apps-windows)|
|**App-Schutz**|Nicht verfügbar|Verfügbar <br>[Was sind App-Schutzrichtlinien?](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-protection-policy)|
|**Integritätsnachweis**|Nicht verfügbar|Verfügbar|


### <a name="advantages-of-mdm-windows-pc-management"></a>Vorteile der Verwaltung von Windows-PCs mit MDM
Die Verwaltung von Windows-PCs mithilfe der modernen Verwaltung mobiler Geräte (MDM) bietet folgende Vorteile:
- **Skalierbarkeit**: Die MDM-Verwaltung wird mit der Intune-Cloudverwaltung skaliert. Die Intune-Softwareclient ist auf 7.000 PCs beschränkt.
- **Einfachheit**: Die MDM-Lösung verwendet moderne Verwaltungsfunktionen, die im Betriebssystem enthalten ist, ohne Rückgriff auf einen heruntergeladenen Softwareclient.
- **Einheitlichkeit**: Ihre Windows-PCs werden wie alle anderen mobilen Geräte in Ihrer Organisation verwaltet.
<!-- - **Cloud optimization** - -->
