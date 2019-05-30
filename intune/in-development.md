---
title: 'In der Entwicklung: Microsoft Intune'
titleSuffix: ''
description: In der Entwicklung befindliche Microsoft Intune-Features
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca66a2fa331fe4dcc30c32d369db32a57ba9999c
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047314"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>In der Entwicklung befindliche Microsoft Intune-Features: Mai 2019

Um Ihnen bei Ihrer Vorbereitung und Planung zu helfen, sind auf dieser Seite Updates und Features der Intune-Benutzeroberfläche aufgeführt, die sich in der Entwicklung befinden, aber noch nicht freigegeben wurden. Zusätzlich:

- Wenn wir davon ausgehen, dass Sie vor einer Änderung Maßnahmen ergreifen müssen, werden wir einen ergänzenden Beitrag im Office 365-Nachrichtencenter veröffentlichen.
- Wenn ein Feature in die Produktion überführt wird, entweder als Vorschau- oder allgemein verfügbare Version, wird die Featurebeschreibung von dieser Seite auf die Seite [Neuerungen in Microsoft Intune](whats-new.md) verschoben.
- Diese Seite und die Seite [Neuerungen](whats-new.md) werden regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.
- In der [Roadmap für Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) finden Sie strategische Ziele und Zeitrahmen.

> [!Note]
> Diese Punkte spiegeln die aktuellen Erwartungen von Microsoft an die Möglichkeiten mit Intune in einer künftigen Version wider. Termine und einzelne Features können sich ändern. Nicht für alle Elemente in der Entwicklung gibt es auf dieser Seite eine Featurebeschreibung.

**RSS-Feed**: Lassen Sie sich benachrichtigen, wenn diese Seite aktualisiert wird, indem Sie die folgende URL kopieren und in Ihren Feedreader einfügen: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune im Azure-Portal


<!-- 1905 start-->


### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Baseline-Unterstützung für Stichwortsuche  <!-- 3082036         -->
Wenn Sie ein Baselineprofil für Sicherheit erstellen oder bearbeiten, können Sie bald mithilfe der *Suche* die Einstellungen filtern, die in der Konsole angezeigt werden.   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Zurücksetzen von Geräten in einem Massenvorgang mithilfe der Graph-API <!-- 3295288 -->
Mithilfe der Graph-API können Sie in einem Massenvorgang bis zu 100 Geräte zurücksetzen.

<!-- 1904 start-->

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Gerätebenutzer können alle verwalteten Anwendungen anzeigen, die sie installiert bzw. zu installieren versucht haben <!-- 2352913 -->
Im Unternehmensportal für Windows werden alle verwalteten &ndash;(sowohl erforderlichen als auch verfügbaren)&ndash; Apps aufgelistet, die auf dem Gerät eines Benutzers installiert sind. Benutzer können versuchte und ausstehende App-Installationen sowie deren aktuellen Status einsehen. Wenn Ihr Unternehmen keine erforderlichen oder verfügbaren Anwendungen zur Verfügung stellt, erhalten die Benutzer die Meldung, dass keine Unternehmensanwendungen installiert wurden. Benutzer können ihre Apps auch nach Installationsstatus sortieren oder filtern.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Verwenden von „Anwendbarkeitsregeln“ beim Erstellen von Windows 10-Gerätekonfigurationsprofilen <!-- 2549910 -->
Sie können Windows 10-Gerätekonfigurationsprofile einrichten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10** als Plattform). Sie können eine **Anwendbarkeitsregel** so erstellen, dass das Profil nur für eine bestimmte Edition oder Version gilt. Sie können beispielsweise ein Profil erstellen, das einige BitLocker-Einstellungen aktiviert. Sobald Sie das Profil hinzugefügt haben, aktivieren Sie eine Anwendbarkeitsregel, damit das Profil nur für Geräte mit Windows 10 Enterprise gilt.

Gilt für: 
- Windows 10 und höher



## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).


