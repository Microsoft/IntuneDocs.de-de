---
title: Datensammlung in Intune
description: Erfahren Sie mehr darüber, wie personenbezogene Daten in Intune gesammelt werden.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1171740-936d-46a5-af37-f418bd6fa63e
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d96167eb37ac7c3c90bad82783e9ce06814f8c88
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67884777"
---
# <a name="data-collection-in-intune"></a>Datensammlung in Intune

Wenn Benutzer ihre geschäftlichen oder persönlichen Geräte mithilfe von Intune registrieren, sammelt Intune personenbezogene Daten und gibt diese frei. Intune sammelt personenbezogene Daten aus folgenden Quellen:

- Der Verwendung von Intune im Azure-Portal durch den Administrator.
- Endbenutzergeräten (wenn diese sich während der Verwendung in der Intune-Verwaltung registrieren).
- Kundenkonten bei Drittanbieterdiensten (auf Anweisung des Administrators).
- Diagnose-, Leistungs- und Nutzungsinformationen.

Aus diesen Quellen sammelt Intune Informationen, die in folgende drei Kategorien einsortiert werden: [Identifiziert](#identified-data), [pseudonymized](#pseudonymized-data) (Pseudonymisiert) und [Aggregiert](#aggregated-data).

## <a name="identified-data"></a>Identifizierte Daten

Bei den meisten personenbezogenen Daten, die von Intune gesammelt werden, handelt es sich um identifizierte Daten. Diese Daten werden an einen Benutzer, ein Gerät oder eine Anwendung gebunden und sind für die Verwaltung wichtig. Identifizierte Daten werden verwendet, um Geräte und Anwendungen eines Benutzers zu verwalten und den Intune-Dienst bereitzustellen.

Zu den identifizierten Daten, die von Intune gesammelt werden, zählen unter anderem Folgende: 

- Benutzerinformationen
  - Besitzername/Anzeigename des Benutzers (der in Azure registrierte Name des Benutzers, der von der Benutzer-ID identifiziert wird)
  - Benutzerprinzipalname oder E-Mail-Adresse
  - Benutzer-IDs von Drittanbietern (z.B. Apple-ID)
- Hardwareinventurinformationen
  - Gerätename
  - Hersteller
  - Betriebssystem
  - Seriennummer
  - IMEI-Nummer
  - IP-Adresse
  - WLAN-MAC-Adresse
  - ICCID
  - Telefonnummer
- Überwachungsprotokollinformationen, einschließlich Daten zu folgenden Aktivitäten:
  - Verwalten von
  - Erstellen
  - Aktualisieren (Bearbeiten)
  - Löschen
  - Zuweisen
  - Remoteaufgaben
- Supportinformationen
  - Kontaktinformationen (Name, Telefonnummer, E-Mail-Adresse)
  - E-Mail-Unterhaltungen mit Mitgliedern des Microsoft-Supportteams, -Produktteams oder des Teams für Benutzerzufriedenheit
- Informationen zur Zugriffssteuerung (Intune verwendet diese Daten, um den Zugriff auf administrative Rollen und Funktionen über Features wie die [rollenbasierte Zugriffssteuerung](role-based-access-control.md) zu verwalten.)
  - Statische Authentifikatoren (Kennwort des Kunden)
  - Datenschutzschlüssel für Zertifikate 
- Administrator- und Kontoinformationen
  - Vor- und Nachname des Administratorbenutzers
  - Administratorbenutzername
  - UPN (E-Mail)
  - Telefonnummer
  - E-Mail-Adresse des Kontobesitzers
  - Active Directory-ID jedes IT-Administrators des Kunden
  - Zahlungsdaten für die Kundenabrechnung
  - Abonnementschlüssel
- Anwendungsbestand, z.B.:
  - App-Name
  - -Version
  - App-ID
  - Größe
  - Installationspfad
  - Anwendungsbestandsdaten werden nur gesammelt, wenn das Gerät vom Administrator als unternehmenseigenes Gerät markiert wird oder das kompatible App-Feature aktiviert ist.  
- Mandanten-IDs von Drittanbietern des Kunden, z.B. die Apple-ID. 

## <a name="pseudonymized-data"></a>Pseudonymisierte Daten

Pseudonymisierte Daten werden einem eindeutigen Bezeichner zugeordnet. Dieser ist üblicherweise eine Zahl, die vom System generiert wird. Durch diese allein kann keine einzelne Person identifiziert werden, sie wird jedoch verwendet, um Benutzern die Unternehmensdienste bereitzustellen. 

Zu den pseudonymisierten Daten, die von Intune gesammelt werden, zählen unter anderem Folgende: 

- Diagnose-, Leistungs- und Nutzungsdaten, die an einen Benutzer oder an ein Gerät gebunden sind
  - Wie häufig ein Feature verwendet wird
  - Die vom Feature bereitgestellten Befehle
  - Die Antwortzeit eines Diensts
  - Erfolgsraten von Installationen und anderen Vorgängen
  - Fehler bei der Intune-Unternehmensportal-App
  - Benutzer- und Geräte-IDs
  - Bezeichner für Verweis-, Korrelations- und Verwaltungszwecke 
- Gerätedaten, die nicht an ein Gerät oder einen Benutzer gebunden sind (wenn die Daten an ein Gerät oder an einen Benutzer gebunden sind, behandelt Intune diese als identifizierte Daten)
  - Intune-Geräte-ID
  - Azure Active Directory-Geräte-ID
  - Intune-Geräteverwaltungs-ID
  - Mandanten-ID
  - Konto-ID
  - EAS-Geräte-ID
  - Plattformspezifische IDs
  - Apple-ID für iOS-Geräte
  - MAC-Adressen für Mac-Geräte
  - Windows-ID für Windows-Geräte
- Verwaltete Anwendungsinformationen
  - Verwaltete Anwendungs-ID
  - Gerätetag der verwalteten Anwendung
  - Intune-Geräteverwaltungs-ID
  - Azure Active Directory-Geräte-ID
  - Verschlüsselungsschlüssel

## <a name="aggregated-data"></a>Aggregierte Daten

Aggregierte Daten werden verwendet, um den Intune-Dienst bereitzustellen und zu verbessern. 

Zu den aggregierten Daten, die von Intune gesammelt werden, zählen unter anderem Folgende: 

- Administratornutzungsdaten aller Intune-Mandanten (z.B. ausgewählte Administrator-Steuerelemente, wenn mit der Administratorkonsole interagiert wird)
- Informationen zum Mandantenkonto (diese Daten sind im Blatt „Intune“ verfügbar)
  - Die Anzahl der registrierten Geräte oder Benutzer
  - Die Anzahl der identifizierten Geräteplattformen  
  - Die Anzahl der installierten Geräte
  - installedDeviceCount: die Anzahl der Geräte, auf denen die Anwendung installiert ist
  - notApplicableDeviceCount: die Anzahl der Geräte, für die die Anwendung nicht verfügbar ist
  - notInstalledDeviceCount: die Anzahl der Geräte, für die die Anwendung zwar verfügbar, auf denen sie jedoch nicht installiert ist
  - pendingInstallDeviceCount: die Anzahl der Geräte, für die die Anwendung verfügbar ist und bei denen die Installation noch aussteht

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr darüber, wie Intune personenbezogene Daten [sichert und verarbeitet](privacy-data-store-process.md) und [freigibt](privacy-data-secure-share.md). 
