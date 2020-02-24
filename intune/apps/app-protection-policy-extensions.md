---
title: App-Schutzrichtlinien für Erweiterungen
titleSuffix: Microsoft Intune
description: In diesem Thema sind die App-Schutzrichtlinien (App Protection Policies, APP) für Erweiterungen beschrieben.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e568bb5520b4f8cc242cb58a1ee48e8729f4e387
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414592"
---
# <a name="protecting-application-extensions"></a>Schützen von Anwendungserweiterungen

In diesem Artikel sind die App-Schutzrichtlinien für Erweiterungen in Microsoft Intune beschrieben.

## <a name="add-ins-for-outlook-app"></a>Add-Ins für die Outlook-App

Über Outlook-Add-Ins können Sie beliebte Apps in den E-Mail-Client integrieren. Add-Ins für Outlook sind im Web, unter Windows, Mac und Outlook für Android und iOS/iPadOS verfügbar. Die Intune APP SDK- und Intune-App-Schutzrichtlinien umfassen keine Unterstützung für die Verwaltung von Add-Ins für Outlook, es gibt jedoch andere Möglichkeiten, die Verwendung einzuschränken. Da Add-Ins über Microsoft Exchange verwaltet werden, können die Benutzer Daten und Nachrichten über Outlook und nicht verwaltete Add-In-Anwendungen freigeben, sofern diese Add-Ins von Exchange nicht für den Benutzer deaktiviert wurden.

Wenn Sie verhindern möchten, dass Endbenutzer auf Outlook-Add-Ins zugreifen und diese installieren (dies hat Auswirkungen auf alle Outlook-Clients), nehmen Sie im Exchange Admin Center die folgenden Änderungen an den Rollen vor:

- Um zu verhindern, dass Benutzer Office Store-Add-Ins installieren, entfernen Sie die Rolle My Marketplace.
- Um zu verhindern, dass Benutzer ein Sideloading von Add-Ins durchführen können, entfernen Sie die Rolle My Custom Apps.
- Um zu verhindern, dass Benutzer alle Add-Ins installieren, entfernen Sie beide Rollen – My Custom Apps und My Marketplace.

Diese Anweisungen gelten für Office 365, Exchange 2016, Exchange 2013 für Outlook im Web, unter Windows, auf Mac-PCs und mobil.

- Weitere Informationen finden Sie unter [Add-Ins für Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Weitere Informationen finden Sie unter [Angeben der Administratoren und Benutzer, die Add-Ins für die Outlook-App installieren und verwalten können](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).

## <a name="linkedin-account-connections-for-microsoft-apps"></a>LinkedIn-Kontoverbindungen für Microsoft-Apps

LinkedIn-Kontoverbindungen ermöglichen Benutzern öffentliche LinkedIn-Profilinformationen in bestimmten Microsoft-Apps anzuzeigen. Standardmäßig können Ihre Benutzer auswählen, ob sie ihre LinkedIn- und Microsoft-Arbeits- oder Schulkonten verbinden möchten, um zusätzliche LinkedIn-Profilinformationen anzuzeigen. 

> [!NOTE]
> Die Integration von LinkedIn ist derzeit für Kunden der US-Regierung und Organisationen mit Exchange Online-Postfächern nicht verfügbar, die in Australien, Kanada, China, Frankreich, Deutschland, Indien, Südkorea, Japan, Südafrika und dem Vereinigten Königreich gehostet werden.

Die Richtlinien für Intune SDK und Intune-App-Schutz umfassen keine Unterstützung für die Verwaltung von LinkedIn-Kontoverbindungen, es gibt jedoch andere Möglichkeiten, diese zu verwalten. Sie können LinkedIn-Kontoverbindungen für Ihre gesamte Organisation deaktivieren. Sie können LinkedIn-Kontoverbindungen auch für ausgewählte Benutzergruppen in Ihrer Organisation aktivieren. Diese Einstellungen betreffen LinkedIn-Verbindungen über Office 365-Apps auf allen Plattformen (Web, Mobil und Desktop). Sie können:

- LinkedIn-Kontoverbindungen für Ihren Mandanten im Azure-Portal aktivieren oder deaktivieren. 
- LinkedIn-Kontoverbindungen für die Office 2016-Apps Ihrer Organisation aktivieren oder deaktivieren, die Gruppenrichtlinien verwenden.

Wenn die LinkedIn-Integration für Ihren Mandanten aktiviert ist und Benutzer Ihrer Organisation Ihre Arbeits- oder Schulkonten von LinkedIn oder Microsoft verknüpfen, verfügen sie über zwei Optionen: 

- Sie können die Berechtigungen zum Freigeben von Daten zwischen beiden Konten erteilen. Das bedeutet, dass sie ihr LinkedIn-Konto dazu berechtigen, Daten mit ihrem Microsoft-Arbeits- oder Schulkonto und umgekehrt zu teilen. Über LinkedIn freigegebene Daten verlassen die Onlinedienste. 
- Benutzer können die Berechtigung erteilen, Daten nur aus ihrem LinkedIn-Konto an ihr Microsoft-Arbeits- oder Schulkonto freizugeben.

Wenn ein Benutzer seine Zustimmung gibt, seine Daten zwischen den Konten zu teilen, werden vorhandene Microsoft Graph-APIs wie bei Office-Add-Ins für die LinkedIn-Integration verwendet. Bei der LinkedIn-Integration wird nur ein Teil der APIs verwendet, die für Office-Add-Ins verfügbar sind, und verschiedene Ausnahmen werden unterstützt.


|Microsoft Graph-Berechtigungen  |Beschreibung  |
|---------|---------|
|Liest Berechtigungen für [Personen](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#people-permissions)     |Ermöglicht der App, eine bewertete Liste von Personen zu lesen, die für den angemeldeten Benutzer relevant sind. Diese Liste kann lokale Kontakte, Kontakte aus sozialen Netzwerken oder dem Verzeichnis Ihrer Organisation und Personen aus aktuellen Kommunikationen (z.B. E-Mail und Skype) enthalten.         |
|Liest Berechtigungen für [Kalender](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#calendars-permissions)     |Ermöglicht der App, Ereignisse in Benutzerkalendern zu lesen. Enthält die Besprechungen in angemeldeten Benutzerkalendern, ihre Uhrzeiten, Orte und Teilnehmer.         |
|Liest Berechtigungen für [Benutzerprofile](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#user-permissions)     |Ermöglicht Benutzern, sich bei der App anzumelden, und ermöglicht der App, das Profil von angemeldeten Benutzern zu lesen. Darüber hinaus wird der App ermöglicht, grundlegende Unternehmensinformationen von angemeldeten Benutzern zu lesen.         |
|Subscriptions     |Dieser Bereich ist nicht verfügbar und wird noch nicht verwendet. Darin sind Abonnements enthalten, die von der Organisation des Benutzers für Microsoft-Apps und -Dienste bereitgestellt werden, z.B. Office 365.         |
|Einblicke     |Dieser Bereich ist nicht verfügbar und wird noch nicht verwendet. Darin sind Interessen enthalten, die dem angemeldeten Benutzerkonto basierend auf der Verwendung von Microsoft-Diensten zugeordnet werden können.         |

### <a name="learn-more"></a>Erfahren Sie mehr

- Erfahren Sie mehr über [LinkedIn-Informationen und -Features in Ihren Microsoft-Apps](https://go.microsoft.com/fwlink/?linkid=850740).
- Erfahren Sie mehr über die Veröffentlichung von LinkedIn-Kontoverbindungen über die [Office 365-Roadmap](https://products.office.com/en-US/business/office-365-roadmap?filters=%26freeformsearch=linkedin#abc). 
- Erfahren Sie mehr über das [Konfigurieren von LinkedIn-Kontoverbindungen](https://docs.microsoft.com/azure/active-directory/linkedin-integration).
- Weitere Informationen über Daten, die zwischen den LinkedIn- und Microsoft-Arbeits- oder Schulkonten freigegeben werden, finden Sie unter [LinkedIn in Microsoft-Anwendungen bei Ihrer Arbeit oder Schule](https://www.linkedin.com/help/linkedin/answer/84077).

