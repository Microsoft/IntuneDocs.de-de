---
title: Verstehen, wann Schutzrichtlinien für Apps ausgelöst werden
titleSuffix: Microsoft Intune
description: Lernen Sie die verschiedenen Bereitstellungsfenster für App-Schutzrichtlinien kennen, um zu verstehen, wann auf Ihren Endbenutzergeräten Änderungen vorgenommen werden sollten.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/12/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ec111319-7e02-434f-946b-88647726bf1a
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 879ccc890a727ddbd911a2b42266d205a1a293c5
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61501271"
---
# <a name="understand-app-protection-policy-delivery-timing"></a>Verstehen, wann Schutzrichtlinien für Apps ausgelöst werden

Lernen Sie die verschiedenen Bereitstellungsfenster für App-Schutzrichtlinien kennen, um zu verstehen, wann auf Ihren Endbenutzergeräten Änderungen vorgenommen werden sollten.

## <a name="delivery-timing-summary"></a>Zeitpunkt der Auslösung einer Schutzrichtlinie – Zusammenfassung

Die Auslösung einer App-Schutzrichtlinie hängt für Ihre Benutzer vom Lizenzstatus und der Registrierung beim Intune-Dienst ab.  

|    Benutzerzustand    |    Verhalten des App-Schutzes     |    Wiederholungsintervall (siehe Hinweis)    |    Grund    |
|-----------------------------------------------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
|    Tenant Not Onboarded (Mandant nicht integriert)    |    Wartet bis zur nächsten Wiederholung.  Der App-Schutz ist für den Benutzer nicht aktiv.    |    24 Stunden    |    Tritt auf, wenn Sie Ihren Mandanten nicht für Intune eingerichtet haben.    |
|    User not Licensed (Benutzer nicht lizenziert)     |    Wartet bis zur nächsten Wiederholung.  Der App-Schutz ist für den Benutzer nicht aktiv.     |    12 Stunden. Für Android-Geräte benötigt dieses Intervall jedoch mindestens die Intune App SDK-Version 5.6.0. Andernfalls beträgt das Intervall für Android-Geräte 24 Stunden.   |    Tritt auf, wenn Sie dem Benutzer keine Lizenz für Intune zugewiesen haben.    |
|    User Not Assigned App Protection Policies (Dem Benutzer wurden keine App-Schutzrichtlinien zugewiesen)    |    Wartet bis zur nächsten Wiederholung.  Der App-Schutz ist für den Benutzer nicht aktiv.    |    12 Stunden        |    Tritt auf, wenn Sie dem Benutzer keine App-Schutzrichtlinieneinstellungen zugewiesen haben.    |
|    User Successfully Registered for Intune MAM (Der Benutzer wurde erfolgreich für Intune MAM registriert)    |    Der App-Schutz ist entsprechend der Richtlinieneinstellungen aktiv.    Updates werden auf Grundlage des Wiederholungsintervalls durchgeführt.    |    Wird auf Grundlage der Benutzerlast vom Intune-Dienst bestimmt.    Normalerweise 30 Minuten.     |    Tritt auf, wenn sich der Benutzer erfolgreich beim Intune-Dienst für die MAM-Konfiguration registriert hat.    |

> [!NOTE]
> Damit die Wiederholungsintervalle ausgeführt werden, muss die App aktiv verwendet werden, d. h. die App muss gestartet und verwendet werden.  Wenn das Wiederholungsintervall 24 Stunden beträgt, und der Benutzer erst nach 48 Stunden die App startet, führt der Client für den App-Schutz die Wiederholung nach 48 Stunden durch.

## <a name="handling-network-connectivity-issues"></a>Umgehen mit Netzwerkverbindungsproblemen

Wenn die Benutzerregistrierung aufgrund von Netzwerkverbindungsproblemen fehlschlägt, wird ein kürzeres Wiederholungsintervall verwendet.  Der Client des App-Schutzes führt dann so lange Wiederholungen mit höheren Intervallen durch, bis das Intervall 60 Minuten beträgt oder erfolgreich eine Verbindung hergestellt werden konnte.  Der Client wird dann so lange Wiederholungen in einem Intervall von 60 Minuten durchführen, bis erfolgreich eine Verbindung hergestellt werden kann. Danach verwendet der Client wieder das auf Grundlage des Benutzerstatus festgesetzte Standardwiederholungsintervall.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Lizenzen zu Benutzern, damit sie ihre Geräte bei Intune registrieren können](licenses-assign.md)

