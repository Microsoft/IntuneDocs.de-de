---
title: Verhindern von Kompromittierungen im Unternehmen durch mobile Office 365-Apps
description: Verwenden Sie Intune, um die Daten Ihres Unternehmens mithilfe von MAM-Richtlinien (mobile Anwendungsverwaltung) zu schützen, die dabei helfen, Verluste von Unternehmensdaten aus mobilen Office 365-Apps oder anderen branchenspezifischen Apps zu verhindern.
keywords: ''
author: jeffgilb
ms.author: jeffgilb
manager: dougeby
ms.date: 11/22/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 19be3de7-539c-49f5-8c46-5363b987fef9
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: pchacon
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b0117ef734a8549593992108105192ce1c4de5b0
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="quick-start-guide-prevent-company-data-leaks-from-office-365-mobile-apps"></a>Erste Schritte: Verhindern von Kompromittierungen im Unternehmen durch mobile Office 365-Apps

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune kann Sie dabei unterstützen, die Daten im Unternehmen mithilfe von MAM-Richtlinien (mobile Anwendungsverwaltung) zu schützen, die dabei helfen, die Kompromittierung von Daten im Unternehmen durch mobile Office 365-Apps oder andere branchenspezifische Apps zu verhindern. Für die Verwendung der MAM-Richtlinien von Intune ist keine Registrierung der Geräte der Benutzer in MDM (mobile Geräteverwaltung) erforderlich. Wenn daher Benutzer vorhanden sind, die Ihre privaten mobilen iOS- oder Android-Geräte nicht in einer Microsoft MDM-Lösung (Intune, Configuration Manager oder EAS) registrieren möchten, kann Intune Ihnen dabei helfen, die Datensicherheit im Unternehmen zu erhöhen, wenn Sie die Unternehmensdaten ohne Verwaltung der Endbenutzergeräte schützen möchten oder Sie bereits eine nicht von Microsoft stammende MDM-Lösung verwenden.   

## <a name="is-this-quick-start-guide-right-for-me"></a>Ist dieses Schnellstarthandbuch für mich geeignet?
Möchten Sie Ihren Endbenutzern den Zugriff auf Ihre Office 365-Daten und Daten branchenspezifischer Apps auf ihren iOS- und Android-Geräten gestatten, ohne eine Registrierung in einer MDM-Lösung (mobile Geräteverwaltung) zu erfordern, wobei Sie dennoch kontrollieren können, welche Aktionen die Benutzer mit diesen Daten durchführen können (z. B. Daten kopieren und in privaten Apps einfügen)?

Wenn dies der Fall ist, können Sie mit Microsoft Intune entsprechende MAM-Richtlinien für mobile Office 365-Apps auf iOS- und Android-Geräten festlegen (einschließlich der Einschränkungen zum Ausschneiden/Kopieren/Einfügen, der Verhinderung von „Speichern unter“, dem Festlegen von PIN-Anforderungen sowie die Möglichkeit zur Remotezurücksetzung von Daten, die MAM-geschützt sind.  Dadurch werden Unternehmensdaten geschützt, ohne dass Benutzer ihre Geräte in einer MDM-Lösung registrieren müssen, wobei gleichzeitig eine hervorragende Endbenutzererfahrung mit mobilen Office-Apps bewahrt wird.

## <a name="how-do-i-do-it"></a>Wie gehe ich dabei vor?
1.  Erhalten Sie grundlegende Kenntnisse zur [Funktionsweise der mobilen Anwendungsverwaltung (MAM) mit Intune](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune).
2.  Erhalten Sie weitere Informationen dazu, [welche Schritte Sie ausführen müssen, bevor Sie im Azure-Portal Richtlinien für die Verwaltung von mobilen Apps (MAM, Mobile App Management) erstellen können](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune).
3.  [Erstellen und Bereitstellen von MAM-Richtlinien](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) mit Intune.

### <a name="additional-information"></a>Zusätzliche Informationen:
- [Endbenutzererfahrung](/intune-classic/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune) mit MAM-fähigen Apps
- [Vorbereiten von branchenspezifischen Apps für MAM mit Intune](/intune/apps-prepare-mobile-application-management)
- <a href="https://www.microsoft.com/cloud-platform/microsoft-intune-partners" target="_blank">Liste der Microsoft Intune-Anwendungspartner&rarr;</a>, die MAM-fähige Apps bereitstellen

## <a name="what-should-i-do-next"></a>Wie sollte ich als nächstes vorgehen?
[Migration von einer Nicht-Microsoft-MDM-Lösung zu Microsoft Intune](/intune-classic/deploy-use/migrate-to-intune)

[Registrieren von Geräten bei Intune MDM](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)
