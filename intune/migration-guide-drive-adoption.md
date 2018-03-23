---
title: Fördern der Akzeptanz durch Endbenutzer mit bedingtem Zugriff
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie den bedingten Zugriff verwenden können, um die Registrierung in Microsoft Intune zu unterstützen.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 31e2a79e5506666cc5ebe655536600b57a429802
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2018
---
# <a name="drive-end-user-adoption-with-conditional-access-in-microsoft-intune"></a>Vorantreiben der Einführung mit bedingtem Zugriff für Endbenutzer in Microsoft Intune

Funktionen für bedingten Zugriff wie das Blockieren von E-Mails für nicht registrierte Geräte mit Intune zu aktivieren, kann die Registrierung und Kompatibilität fördern, ist aber keine Voraussetzung für eine erfolgreiche Migration. Ihre Ziele bei der Einführung der Migration und die Sicherheitsanforderungen sollten den Erfolg bestimmen.

## <a name="migration-campaign-with-conditional-access"></a>Migrationskampagne mit bedingtem Zugriff

Hier ist ein typischer Ansatz, wie eine Migrationskampagne durch bedingten Zugriff erweitert werden kann:

1.  Legen Sie Regeln für bedingten Zugriff fest, der für alle Benutzer erzwungen wird, aber schließen Sie speziell die Benutzer aus, die vom alten MDM-Anbieter migrieren müssen. Sie können eine Azure AD-Benutzergruppe mit allen Benutzern erstellen, die vom bedingten Zugriff ausgeschlossen sind.

2.  Entfernen Sie die Benutzer aus dieser Gruppe, wenn sie migriert haben.

3.  Konfigurieren Sie nach dem Abschluss der Migration alle Richtlinien für bedingten Zugriff so, dass sie standardmäßig blockieren, wenn Intune den Zugriff nicht erlaubt.

### <a name="advantages"></a>Vorteile

-   Bietet Zugriffsteuerung für neue Benutzerkonten oder Benutzerkonten, die von der vorherigen Lösung nicht verwaltet wurden.

-   Bietet Benutzern der vorherigen Lösung einen Toleranzzeitraum für die Migration.

-   Produktivitätsverluste werden minimiert

### <a name="disadvantages"></a>Nachteile

-   Benutzer der vorherigen Lösung können möglicherweise über nicht verwaltete Geräte auf Ressourcen zugreifen, bis der bedingte Zugriff für diese Benutzer aktiviert ist.


Dies ist ein Ansatz unter vielen. Sie können auch einen einfacheren Prozess auswählen, der jeglichen bedingten Zugriff aufschiebt, bis in jeder Phase die Registrierung angewiesen wurde, oder einen strengeren Prozess, der bedingten Zugriff von Anfang an erzwingt und für jeden Zugriff vollständige Kompatibilität erfordert.

-   Weitere Informationen zum [bedingten Zugriff](conditional-access.md).

## <a name="task-list-for-conditional-access"></a>Aufgabenliste für bedingten Zugriff

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>Aufgabe 1: Entscheiden Sie, wie Sie den bedingten Zugriff implementieren möchten.

[Gängige Möglichkeiten der Nutzung des bedingten Zugriffs](conditional-access-intune-common-ways-use.md)

### <a name="task-2-set-up-intune-conditional-access"></a>Aufgabe 2: Richten Sie den bedingten Zugriff für Intune ein.

Wählen Sie eine der folgenden Optionen aus:

-   [Konfigurieren des bedingten Zugriffs in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

-   [Installieren des lokalen Exchange Connectors für Intune](exchange-connector-install.md)

-   [Einrichten von App-basierten bedingten Zugriffsrichtlinien für Exchange Online](app-based-conditional-access-intune-create.md)

-   [Einrichten von App-basierten bedingten Zugriffsrichtlinien für SharePoint Online](app-based-conditional-access-intune-create.md)

-   [Blockieren von Apps, die keine moderne Authentifizierung verwenden (ADAL)](app-modern-authentication-block.md)

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über den [typischen Migrationszyklus](migration-guide-cycle.md).
