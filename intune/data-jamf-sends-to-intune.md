---
title: Von Jamf Pro an Intune übermittelte Daten
titleSuffix: Microsoft Intune
description: Eine Liste der Daten, die Jamf Pro an Microsoft Intune übermittelt
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 287ed06ddab0b98117aa4a75942087f360e4656d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048547"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Von Jamf Pro an Intune gesendete Daten

Wenn Sie [Jamf Pro](https://www.jamf.com) mit Intune zum Verwalten der Mac-Geräte Ihrer Endbenutzer verwenden, erfasst Jamf Pro Informationen zum Bestand verwalteter macOS-Geräte. Jamf Pro meldet die folgenden Informationen an Intune:

* Azure AD-Geräte-ID
* JAMF-Inventurstatus (Inventurstatus eines Computers, der sich innerhalb der letzten 24 Stunden bei Jamf Pro eingecheckt hat)
* Betriebssystemversion
* Azure AD-Benutzer-ID
* Verschlüsselt (FileVault 2)
* Gatekeeperstatus
* Kennwort: Mindestanzahl von Zeichensätzen
* Kennwortablauf (Tage)
* Kennworttyp: einfach, alphanumerisch oder unbekannt
* Automatische Anmeldung verhindern
* Erforderliche Kennungslänge
* Kennwort: Anzahl vorheriger Kennwörter zum Verhindern der Wiederverwendung
* Systemintegritätsschutz
* Zeitpunkt des letzten Check-Ins
* Architekturtyp
* Verfügbare Speichersteckplätze
* Akkukapazität
* Start-ROM
* Busgeschwindigkeit
* Cachegröße
* Gerätename
* Domäne beitreten
* Jamf-ID
* MAC-Adresse
* Automarke
* Modell
* Modellbezeichnung
* NIC-Geschwindigkeit
* Anzahl der Kerne
* Prozessoranzahl
* Betriebssystem
* Plattform
* Prozessorgeschwindigkeit
* Prozessortyp
* Sekundäre MAC-Adresse
* Seriennummer
* SMC-Version
* RAM gesamt
* UDID
* Benutzer-E-Mail-Adresse


Sie können ein von Jamf verwaltetes Gerät aus der Intune-Konsole entfernen, indem Sie **Löschen** in der Ansicht **Alle Geräte** auswählen. Die Massenlöschung von Geräten kann aktiviert werden, indem Sie mehrere Geräte auswählen und auf **Löschen** klicken.

Erfahren Sie, wie Sie [ein mit Jamf verwaltetes Gerät in den Jamf Pro-Dokumenten entfernen](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Sie können auch ein Supportticket beim [Jamf-Support](https://www.jamf.com/support/) einreichen, wenn Sie zusätzliche Hilfe benötigen. 

