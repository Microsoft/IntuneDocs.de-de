---
title: Seite des Microsoft Intune-Mandantenstatus
titleSuffix: Microsoft Intune
description: Verwenden Sie die Seite des Intune-Mandantenstatus, um wichtige Mandantendetails anzuzeigen, ohne das Intune-Portal verlassen zu müssen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 7954a686-25dc-4fce-b395-324816f46d3b
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c79f24d44ad0aed78ed0ae6fce0873a080b2904d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504848"
---
# <a name="use-the-intune-tenant-status-page"></a>Verwenden der Seite des Intune-Mandantenstatus
Bei der Mandantenstatusseite von Microsoft Intune handelt es sich um einen zentralen Hub, auf dem Sie aktuelle und wichtige Details zu Ihrem Mandanten abrufen können. Diese Details umfassen u. a. die Lizenzverfügbarkeit und -verwendung, den Connectorstatus und wichtige Mitteilungen zum Intune-Dienst.  

Melden Sie sich zum Anzeigen des Dashboards bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an, und wählen Sie dann **Mandantenstatus** aus.  Der *Mandantenstatus* wird unter **Hilfe und Support** angezeigt.  

Diese Seite ist in drei Bereiche unterteilt:

## <a name="tenant-details"></a>Mandantendetails
In den Mandantendetails erhalten Sie auf einem Blick Informationen über Ihren Mandanten. Zeigen Sie Details wie Ihren Mandantennamen und den Speicherort sowie Ihre MDM-Autorität und Ihre Dienstfreigabenummer für den Mandanten an. Bei der Dienstfreigabenummer handelt es sich um einen Link zum Artikel *Neuerungen in Microsoft Intune* in der Microsoft-Dokumentation. In diesem Artikel werden Sie über die neusten Features und Updates des Intune-Diensts informiert.  

Auf dieser Registerkarte sind auch die grundlegenden Informationen zu Ihren verfügbaren Lizenzen angegeben, und wie viele Lizenzen Benutzern zugewiesen sind. Lizenzen für Geräte werden nicht angezeigt.

## <a name="connector-status"></a>Connectorstatus
Der Connectorstatus ist ein praktischer Anlaufpunkt, wenn Sie den Status aller verfügbaren Connectors für Intune überprüfen möchten.  

Connectors können wie folgt aussehen:
- **Von Ihnen konfigurierte Verbindungen zu externen Diensten.** Beispiele hierfür sind die Dienste *Apple Volume Purchase Program* oder der *Windows Autopilot*.  Der Status für diesen Connectortyp basiert auf dem Zeitpunkt der letzten erfolgreichen Synchronisierung.
- **Zertifikate oder Anmeldeinformationen, die für die Verbindung zu einem externen nicht verwalteten Dienst erforderlich sind.** Das Beispiel hierfür sind *Apple Push Notification Service*-Zertifikate (APNS). Der Status dieses Connectortyps basiert auf dem Zeitstempel des Ablaufdatums für das Zertifikat oder die Anmeldeinformationen.  

Wenn Sie die Registerkarte *Connectorstatus* öffnen, werden alle fehlerhaften Connectors oben in der Liste angezeigt. Darauf folgen Connectors mit Warnungen und anschließend fehlerfreie Connectors. Connectors, die Sie noch nicht konfiguriert haben, werden am Ende als *Nicht aktiviert* angezeigt.

Wenn es für einen dieser Typen mehr als einen Connector gibt, ist der Status eine Zusammenfassung von all diesen Connectors. Der letzte Integritätsstatus jedes Connectors wird als Integrität für die Gruppe verwendet.  

**Connectorstatus:**
- **Fehlerhaft:**
  - Das Zertifikat oder die Anmeldeinformation ist abgelaufen.
  - Die letzte Synchronisierung wurde vor mindestens drei Tagen durchgeführt.
- **Warnung:**
  - Das Zertifikat oder die Anmeldeinformation läuft innerhalb von sieben Tagen ab.
  - Die letzte Synchronisierung liegt mehr als einen Tag zurück.
- **Fehlerfrei:**
  - Das Zertifikat oder die Anmeldeinformation läuft nicht innerhalb der nächsten sieben Tage ab.
  - Die letzte Synchronisierung liegt nicht länger als einen Tag zurück.  

Wenn Sie einen Connector aus der Liste auswählen, wird im Portal die Portalseite angezeigt, die für diesen Connector relevant ist. Auf der Connectorseite können Sie den Status für zuvor konfigurierte Connectors anzeigen oder Optionen auswählen, um einen neuen Connector dieses Typs hinzuzufügen oder zu erstellen.

Wenn Sie beispielsweise den Connector **VPP-Ablaufdatum** auswählen, wird die Seite **Per Volumenlizenz erworbene iOS-Programmtoken** geöffnet, auf der Sie nähere Informationen zu diesem Connector erhalten. Sie können auch eine neue Konfiguration erstellen oder bearbeiten und Probleme mit einer vorhandenen Konfiguration beheben.

## <a name="service-health-dashboard"></a>Dashboard zur Dienstintegrität  
Auf dem Dashboard zur Dienstintegrität können Sie Details zu *Dienstvorfällen* anzeigen, die sich auf Ihren Mandanten auswirken, und *Neuigkeiten zu Intune*, die Informationen zu Updates und geplanten Änderungen bereitstellen.

### <a name="intune-service-health"></a>Intune Service Health
Sie können Details zu aktiven Vorfällen und Empfehlungen anzeigen, ohne zum Dashboard zur Dienstintegrität von Microsoft 365 oder dem Nachrichtencenter navigieren zu müssen. Sie finden diese jeweils im [Microsoft 365 Admin Center](https://admin.microsoft.com). Es werden nur Vorfälle angezeigt, die sich auf ihren Mandanten auswirken.  

Wenn Sie einen Incident auswählen, werden die jeweiligen Details direkt auf der Seite des Mandantenstatus angezeigt. Wählen Sie **Letzte Incidents/Beratungen anzeigen** auswählen, können Sie die neuesten Empfehlungen und Incidents anzeigen. Wenn das Microsoft 365 Admin Center geöffnet wird, können Sie die Empfehlungen und Incidents Ihres Mandanten für die letzten 30 Tage anzeigen.  

Ihr Konto muss die Rolle **Globaler Administrator** oder **Dienstadministrator** in Azure Active Directory oder im Microsoft 365 Admin Center besitzen, damit Sie Informationen für *Intune Service Health* anzeigen können. Melden Sie sich am [Microsoft 365 Admin Center](https://admin.microsoft.com) mit den globalen Administratorberechtigungen an, um diese Berechtigungen zuzuweisen. Klicken Sie auf **Benutzer > Aktive Rollen**, und wählen Sie dann das Konto aus, auf das der Zugriff erforderlich ist. Klicken Sie für Rollen auf **Bearbeiten**, wählen Sie *Dienstadministrator* oder *Globaler Administrator* aus, und **speichern** Sie anschließend Ihre Änderung, um die Berechtigungen zuzuweisen.  

Sie können Ihre Kommunikationseinstellungen für Intune Service Health nur über das Microsoft 365 Admin Center einrichten.

### <a name="intune-news"></a>Neuerungen für Intune  
Zeigen Sie informative Mitteilungen vom Team des Intune-Diensts an, ohne durch das gesamte Office-Nachrichtencenter navigieren zu müssen. Diese Mitteilungen sind beispielsweise Benachrichtigungen zu Änderungen, die zuletzt im Intune-Dienst vorgenommen wurden oder die demnächst für Ihren Mandanten vorgesehen sind.  

Standardmäßig werden die 10 aktuellsten und aktiven Meldungen angezeigt. Wenn Sie ältere Nachrichten abrufen möchten, klicken Sie auf **Frühere Nachrichten anzeigen**, um das *Nachrichtencenter* im Microsoft 365 Admin Center zu öffnen.  

Ihr Konto muss die Rolle **globaler Administrator** oder **Dienstadministrator** in Azure Active Directory besitzen, um Informationen zu Neuigkeiten zu Intune abrufen zu können. Alternativ muss die Rolle **Nachrichtencenter-Leseberechtigter** im Microsoft 365 Admin Center zugewiesen sein.  Melden Sie sich am [Microsoft 365 Admin Center](https://admin.microsoft.com) mit den Administratorberechtigungen an, um diese Berechtigung zuzuweisen. Klicken Sie auf **Benutzer > Aktive Rollen**, und wählen Sie dann das Konto aus, auf das der Zugriff erforderlich ist. Klicken Sie für *Rollen* auf **Bearbeiten**, wählen Sie *Teams-Kommunikationsadministrator* aus, und **speichern** Sie anschließend Ihre Änderung, um die Berechtigungen zuzuweisen.  

Sie können Ihre Kommunikationseinstellungen für Neuigkeiten zu Intune nur über das Microsoft 365 Admin Center einrichten.
