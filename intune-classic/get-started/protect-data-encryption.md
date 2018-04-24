---
title: Schützen von Unternehmensdaten durch Datenverschlüsselung
description: Dieser Leitfaden hilft Ihnen dabei, Ihr Unternehmen vor Datenverlust zu schützen, indem durch die Verwendung einer Richtlinie in mobilen Apps eine Kennung sowie die Datenverschlüsselung erzwungen wird.
keywords: Verschlüsselung, PIN, Daten
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 11/22/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b1e84ef8-a260-4e3d-aaf1-8b3facfecafa
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: pchacon
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 084da36e9b417e4faee87f33bbd42e0e5f5fa7e2
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="quick-start-guide-protect-company-data-with-data-encryption"></a>Erste Schritte: Schützen von Unternehmensdaten durch Datenverschlüsselung

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune kann Ihnen dabei helfen, den Verlust von Daten aus mobilen Office-Apps auf unterschiedlichste Weise zu verhindern, z.B.:
- Durch Verschlüsseln von Unternehmensdaten mit der höchsten Geräteverschlüsselungsstufe, die von iOS und Android bereitgestellt wird.
- Auf iOS- und Android-Geräten, die aufgrund von Datenschutzanforderungen oder rechtlichen Anforderungen nicht bei einer Lösung für die Verwaltung mobiler Geräte registriert werden können.

Microsoft Intune kann Ihnen auch dabei helfen, den Verlust von Daten aus mobilen Office-Apps zu verhindern, sowie Office 365-Daten (O365) zu sichern, ohne mobile iOS- oder Android-Geräte bei einer vollständigen Verwaltung mobiler Geräte registrieren zu müssen. Dies gilt auch, wenn Sie für die verwalteten mobilen Geräte eine Drittanbieterlösung für die Verwaltung mobiler Geräte verwenden.

## <a name="is-this-quick-start-guide-right-for-me"></a>Ist dieses Schnellstarthandbuch für mich geeignet?
Dieses Schnellstarthandbuch stellt eine gute Ressource für Sie dar, wenn Sie die folgenden Voraussetzungen erfüllen:
- Sie verwenden bzw. verfügen bereits über O365-Lizenzen, die Sie verwenden möchten, und Sie verwalten mobile Office-Apps.
- Sie planen, mobile Office-Apps unter iOS oder Android zu verwenden.
- Sie verwenden eine beliebige Lösung für die Verwaltung mobiler Geräte (von Microsoft oder einem Drittanbieter). Wenn Sie aufgrund gesetzlicher Vorschriften keine Lösung für die Verwaltung mobiler Geräte verwenden können, können Sie diesen Leitfaden verwenden.

> [!NOTE]
> Windows stellt für mobile Office-Apps noch keine unterstützte Plattform dar. Die Verwaltung mobiler Anwendungen ohne Registrierung ist bisher nicht kompatibel mit Exchange oder lokalem SharePoint. Sie können nur Daten schützen, die in Online-Versionen gehostet werden.

Dieser Leitfaden hilft Ihnen dabei, Ihr Unternehmen vor Datenverlust zu schützen, indem eine Kennung sowie die Datenverschlüsselung erzwungen wird. Dies erfolgt durch die Verwendung von Richtlinien in mobilen Apps, die Ihre Mitarbeiter für den Zugriff auf sensible Daten verwenden, ohne dass eine vollständige Registrierung bei einer Geräteverwaltungslösung erforderlich ist. Microsoft Intune ermöglicht Ihnen das Festlegen von MAM-Richtlinien (mobile application management, Verwaltung mobiler Anwendungen) in mobilen Office-Apps für [iOS](https://products.office.com/mobile/office-mobile-apps-for-ios) und [Android](https://products.office.com/mobile/office-mobile-apps-for-android). Dadurch werden O365-Daten geschützt, ohne dass Benutzer ihre Geräte in einer MDM-Lösung (mobile device management, Verwaltung mobiler Geräte) registrieren müssen, wobei zudem gleichzeitig eine hervorragende Endbenutzerfreundlichkeit der mobilen Office-Apps bewahrt wird.

## <a name="how-do-i-do-it"></a>Wie gehe ich dabei vor?
1.  [Lesen Sie, wie Sie App-Daten schützen können](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
2.  [Vorbereiten der Konfiguration von Verwaltungsrichtlinien für mobile Apps](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)
3.  [Erstellen und Bereitstellen von Verwaltungsrichtlinien für mobile Apps](/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)

## <a name="additional-information"></a>Zusätzliche Informationen:
- [Erfahren Sie mehr über die Endbenutzererfahrung für MAM-fähige Apps mit Microsoft Intune.](/intune-classic/eploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune)
- [Entscheiden Sie, wie Sie Apps für die mobile Anwendungsverwaltung mit Microsoft Intune vorbereiten.](/intune/apps-prepare-mobile-application-management)
- [Zeigen Sie die Liste der Microsoft Intune-Anwendungspartner an.](https://www.microsoft.com/cloud-platform/microsoft-intune-partners)
