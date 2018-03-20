---
title: Von Intune an Apple gesendete Daten
titleSuffix: Microsoft Intune
description: Liste der Daten, die von Intune an Apple gesendet werden.
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b204a956-18ec-11e8-accf-0ed5f89f718b
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c247cfbd715368f65dfb1ba2ce8b5e88a491d302
ms.sourcegitcommit: 54fc806036f84a8667cf8f74086358bccd30aa7d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2018
---
# <a name="data-intune-sends-to-apple"></a>Von Intune an Apple gesendete Daten

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Wenn einer der folgenden Apple-Dienste auf einem Gerät aktiviert ist, richtet Microsoft Intune eine Verbindung mit Apple ein und versendet Benutzer- und Geräteinformationen an Apple: 

- [Apple Device Enrollment Program (DEP)](device-enrollment-program-enroll-ios.md)
- [Apple-MDM-Push-Zertifikat (APNS)](apple-mdm-push-certificate-get.md)
- [Apple School Manager (ASM)](https://docs.microsoft.com/schooldatasync/apple-school-manager-integration-with-intune-for-education-and-school-data-sync)
- [Apple Volume Purchase Program (VPP)](vpp-apps-ios.md)

Damit Microsoft Intune eine Verbindung einrichten kann, müssen Sie zunächst für jeden Apple-Dienst ein Apple-Konto erstellen.

In der folgenden Tabelle sind die Daten aufgeführt, die Microsoft Intune von einem Gerät an den aktivierten Apple-Dienst sendet. 

| Dienst | An Apple versendete Daten | Verwendung |
|---|---| ---|
| [APNS](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Token, PushMagic | Wenn der Server das Gerät akzeptiert, stellt das Gerät sein Gerätetoken für Pushbenachrichtigungen für den Server bereit. Der Server verwendet dieses Token zum Versenden von Pushbenachrichtigungen an das Gerät. Diese Meldung zum Eincheckvorgang enthält auch eine also PushMagic-Zeichenfolge. Der Server speichert diese Zeichenfolge und fügt sie in alle Pushbenachrichtigungen ein, die er an das Gerät sendet. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Servertoken | Gerätetoken für Pushbenachrichtigungen zur Authentifizierung beim Apple-Dienst. |
| ASM/DEP | Servername | Ein identifizierbarer Name für den MDM-Server. |
| ASM/DEP | server_uuid | Ein vom System generierter Serverbezeichner. |
| ASM/DEP | admin_id | Apple-ID der Person, die die aktuell verwendeten Token erzeugt hat. |
| ASM/DEP | org_name | Der Name der Organisation. |
| ASM/DEP | org_email | Die E-Mail-Adresse der Organisation. |
| ASM/DEP | org_phone | Die Telefonnummer der Organisation. |
| ASM/DEP | org_address | Die Adresse der Organisation. |
| ASM/DEP | org_id | ID des DEP-Kunden. Dieser Schlüssel ist erst ab der Protokollversion 3 verfügbar. |
| ASM/DEP | serial_number | Die Seriennummer des Geräts (Zeichenfolge). |
| ASM/DEP | model | Der Modellname (Zeichenfolge). |
| ASM/DEP | description | Eine Beschreibung des Geräts (Zeichenfolge). |
| ASM/DEP | asset_tag | Das Bestandskennzeichen des Geräts (Zeichenfolge). |
| ASM/DEP | profile_status | Der Status der Profilinstallation. Mögliche Werte: **empty**, **assigned**, **pushed** oder **removed**. |
| ASM/DEP | profile_uuid | Die eindeutige ID des zugewiesenen Profils. |
| ASM/DEP | device_assigned_by | Die E-Mail-Adresse der Person, die das Gerät zugewiesen hat. |
| ASM/DEP | os | Das Betriebssystem des Geräts: iOS, OSX oder tvOS. Dieser Schlüssel ist ab X-Server-Protocol-Version 2 gültig. |
| ASM/DEP | device_family | Die Apple-Produktfamilie des Geräts: iPad, iPhone, iPod, Mac oder AppleTV. Dieser Schlüssel ist ab X-Server-Protocol-Version 2 gültig. |
| ASM/DEP | profile_name | Zeichenfolge. Ein lesbarer Name für das Profil. |
| ASM/DEP | support_phone_number | (Optional) Zeichenfolge. Eine Supportrufnummer für die Organisation. |
| ASM/DEP | support_email_address | (Optional) Zeichenfolge. Eine Support-E-Mail-Adresse für die Organisation. Dieser Schlüssel ist ab X-Server-Protocol-Version 2 gültig. |
| ASM/DEP | Abteilung | (Optional) Zeichenfolge. Der benutzerdefinierte Abteilungs- oder Standortname. |
| ASM/DEP | Geräte | Zeichenfolgenarrays, die die Seriennummer des Geräts enthalten. (Kann leer sein.) |
| VPP | Intune UserId guid | Von Intune generierte GUID. |
| VPP | Managed AppleId UPN | AppleID, die vom Administrator beim Konfigurieren der VPP-Tokenverbindung mit Apple angegeben wurde. |
| VPP | Seriennummer | Seriennummer des verwalteten Geräts. |

Wenn Sie die Apple-Dienste mit Microsoft Intune nicht mehr verwenden und die Daten löschen möchten, müssen Sie das Microsoft Intune Apple-Token und das Apple-Konto löschen. Informationen zur Kontenverwaltung in der Dokumentation zum Apple-Konto.


