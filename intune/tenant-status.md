---
title: Seite des Microsoft Intune-Mandantenstatus
titleSuffix: Microsoft Intune
description: Verwenden Sie die Seite des Intune-Mandantenstatus, um wichtige Mandantendetails anzuzeigen, ohne das Intune-Portal verlassen zu müssen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 98b3180bc90c7b54213781ddf8b6668918b22dd3
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54205024"
---
# <a name="intune-tenant-status-page"></a>Seite des Intune-Mandantenstatus
Verwenden Sie die Seite des Mandantenstatus als zentralen Hub, um immer die neuesten Informationen über wichtige Details zu Ihren Mandanten, die Lizenzverfügbarkeit und -verwendung, den Connectorstatus sowie wichtige Kommunikation bezüglich des Intune-Diensts zu erhalten.  

Wechseln Sie im Azure-Portal zu **Intune > Mandantenstatus**, um das Dashboard anzuzeigen.  Der Mandantenstatus wird unter der Gruppe **Hilfe und Support** angezeigt.  

Diese Seite ist in vier Bereiche unterteilt:

## <a name="tenant-details"></a>Mandantendetails
In den Mandantendetails erhalten Sie auf einem Blick Informationen über Ihren Mandanten. Zeigen Sie Details wie Ihren Mandantennamen und den Speicherort sowie Ihre MDM-Autorität und Ihre Dienstfreigabenummer für den Mandanten an. Diese Dienstfreigabenummer ist als Link dargestellt, mit dem Sie den Artikel *Neuheiten in Intune* in der Microsoft-Dokumentation öffnen können. In diesem Artikel erhalten Sie Informationen zu den neuesten Features und Updates für Intune.  

In diesem Abschnitt sind auch die grundlegenden Informationen zu Ihren verfügbaren Lizenzen angegeben und wie viele Lizenzen Benutzern zugewiesen sind. Lizenzen für Geräte werden nicht angezeigt.

## <a name="connector-status"></a>Connectorstatus
Der Connectorstatus ist ein praktischer Anlaufpunkt, wenn Sie den Status aller verfügbaren Connectors für Intune überprüfen möchten.  

Connectors können wie folgt aussehen:
- **Von Ihnen konfigurierte Verbindungen zu externen Diensten.** Beispiele hierfür sind die Dienste *Apple Volume Purchase Program* oder der *Windows Autopilot*.  Der Status für diesen Connectortyp basiert auf dem Zeitpunkt der letzten erfolgreichen Synchronisierung.
- **Zertifikate oder Anmeldeinformationen, die für die Verbindung zu einem externen nicht verwalteten Dienst erforderlich sind.** Das Beispiel hierfür sind *Apple Push Notification Service*-Zertifikate (APNS). Der Status dieses Connectortyps basiert auf dem Zeitstempel des Ablaufdatums für das Zertifikat oder die Anmeldeinformationen.  

In der Standardeinstellung werden nur fünf Connectors angezeigt. Sie können die Option **Alle Connectors anzeigen** auswählen, um diese Liste zu erweitern. So sehen Sie alle verfügbaren Connectors, einschließlich der Connectors, die Sie für die Verwendung noch nicht konfiguriert haben.  

Wenn es für einen dieser Typen mehr als einen Connector gibt, ist der Status eine Zusammenfassung von all diesen Connectors. Der letzte Integritätsstatus jedes Connectors wird als Integrität für die Gruppe verwendet.  

Fehlerhafte Connectors werden immer am Anfang der Liste angezeigt. Darauf folgen Connectors mit Warnungen und anschließend fehlerfreie Connectors. Connectors, die Sie noch nicht konfiguriert haben, stehen ganz unten.

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

Wenn Sie einen Connector aus der Liste auswählen, wird im Portal die Portalseite angezeigt, die für die Erstellung oder Konfiguration des Connectors relevant ist.  Wenn Sie beispielsweise den Connector **VPP Expiry Date** (VPP-Ablaufdatum) auswählen, wird die Seite **Per Volumenlizenz erworbene iOS-Programmtoken** geöffnet, auf der Sie nähere Informationen zu diesem Connector erhalten. Anschließend können Sie eine neue Konfiguration erstellen oder Probleme mit einer vorhandenen Konfiguration bearbeiten und beheben.  

## <a name="intune-service-health"></a>Intune Service Health  
Sie können Details zu aktiven Incidents und Empfehlungen anzeigen, ohne zum Service Health-Dashboard oder dem Nachrichtencenter von Microsoft 365 navigieren zu müssen. Sie finden diese jeweils im Microsoft 365 Admin Center unter https://portal.office.com. Es werden nur Incidents angezeigt, die nachweislich Auswirkungen auf Ihren Mandanten haben.  

Wenn Sie einen Incident auswählen, werden die jeweiligen Details direkt auf der Seite des Mandantenstatus angezeigt. Wählen Sie **Letzte Incidents/Beratungen anzeigen** auswählen, können Sie die neuesten Empfehlungen und Incidents anzeigen. Wenn das Microsoft 365 Admin Center geöffnet wird, können Sie die Empfehlungen und Incidents Ihres Mandanten für die letzten 30 Tage anzeigen.  

Ihr Konto muss die Rolle **globaler Administrator** oder **Dienstadministrator** in Azure Active Directory oder dem Office-Verwaltungsportal besitzen, damit Sie Informationen für *Intune Service Health* anzeigen können. Melden Sie sich am [Microsoft 365 Admin Center](https://portal.officeppe.com/AdminPortal/Home#/homepage) mit den globalen Administratorberechtigungen an, um diese Berechtigungen zuzuweisen. Klicken Sie auf **Benutzer > Aktive Rollen**, und wählen Sie dann das Konto aus, auf das der Zugriff erforderlich ist. Klicken Sie für Rollen auf **Bearbeiten**, wählen Sie *Dienstadministrator* oder *Globaler Administrator* aus, und **speichern** Sie anschließend Ihre Änderung, um die Berechtigungen zuzuweisen.  

Sie können Ihre Kommunikationseinstellungen für Intune Service Health nur über das Microsoft 365 Admin Center einrichten.

## <a name="intune-news"></a>Neuigkeiten zu Intune  
Zeigen Sie informative Mitteilungen vom Team des Intune-Diensts an, ohne durch das gesamte Office-Nachrichtencenter navigieren zu müssen. Diese Mitteilungen sind beispielsweise Benachrichtigungen zu Änderungen, die zuletzt im Intune-Dienst vorgenommen wurden oder die demnächst für Ihren Mandanten vorgesehen sind.  

In der Standardeinstellung werden die letzten 10 aktiven Nachrichten angezeigt. Wenn Sie ältere Nachrichten anzeigen möchten, klicken Sie auf **Frühere Nachrichten anzeigen**, um das *Nachrichtencenter* im Microsoft 365 Admin Center-Portal zu öffnen.  

Ihr Konto muss die Rolle **globaler Administrator** oder **Dienstadministrator** in Azure Active Directory besitzen, um Informationen zu Neuigkeiten zu Intune anzeigen zu können. Alternativ muss die Rolle **Nachrichtencenter-Leser** im Office-Verwaltungsportal zugewiesen sein.  Melden Sie sich am [Microsoft 365 Admin Center](https://portal.officeppe.com/AdminPortal/Home#/homepage) mit den Administratorberechtigungen an, um diese Berechtigung zuzuweisen. Klicken Sie auf **Benutzer > Aktive Rollen**, und wählen Sie dann das Konto aus, auf das der Zugriff erforderlich ist. Klicken Sie für *Rollen* auf **Bearbeiten**, wählen Sie *Teams-Kommunikationsadministrator* aus, und **speichern** Sie anschließend Ihre Änderung, um die Berechtigungen zuzuweisen.  

Sie können Ihre Kommunikationseinstellungen für Neuigkeiten zu Intune nur über das Microsoft 365 Admin Center einrichten.
