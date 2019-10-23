---
title: Fördern der Akzeptanz durch Endbenutzer mit bedingtem Zugriff
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie den bedingten Zugriff verwenden können, um die Registrierung in Microsoft Intune zu unterstützen.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 115313816542fd642e6a0c67900abd48b7146e42
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72510065"
---
# <a name="drive-end-user-adoption-with-conditional-access-in-microsoft-intune"></a>Fördern der Akzeptanz durch Endbenutzer mit bedingtem Zugriff in Microsoft Intune

Die Aktivierung von Funktionen für den bedingten Zugriff mit Intune – wie z.B. das Blockieren von E-Mails für nicht registrierte Geräte – kann die Registrierung und Konformität fördern, ist aber keine Voraussetzung für eine erfolgreiche Migration. Ihre Ziele bei der Einführung der Migration und die Sicherheitsanforderungen sollten den Erfolg bestimmen.

## <a name="migration-campaign-with-conditional-access"></a>Migrationskampagne mit bedingtem Zugriff

Im Folgenden sehen Sie einen typischen Ansatz, wie eine Migrationskampagne mit bedingtem Zugriff erweitert werden kann:

1. Legen Sie Regeln für den bedingten Zugriff fest, die für alle Benutzer erzwungen werden, schließen Sie aber explizit die Benutzer aus, die vom alten MDM-Anbieter migrieren müssen. Sie können eine Azure AD-Benutzergruppe mit allen Benutzern erstellen, die vom bedingten Zugriff ausgeschlossen sind.

2. Entfernen Sie Benutzer aus dieser Gruppe, nachdem diese die Migration durchgeführt haben.

3. Konfigurieren Sie nach dem Abschluss der Migration alle Richtlinien für bedingten Zugriff so, dass der Zugriff standardmäßig blockiert wird, wenn Intune diesen nicht explizit erlaubt.

### <a name="advantages"></a>Vorteile

- Bietet Zugriffsteuerung für neue Benutzerkonten oder Benutzerkonten, die von der vorherigen Lösung nicht verwaltet wurden.

- Bietet Benutzern der vorherigen Lösung einen Toleranzzeitraum für die Migration.

- Produktivitätsverluste werden minimiert

### <a name="disadvantages"></a>Nachteile

- Benutzer der vorherigen Lösung können möglicherweise über nicht verwaltete Geräte auf Ressourcen zugreifen, bis der bedingte Zugriff für diese Benutzer aktiviert ist.


Dies ist ein Ansatz unter vielen. Sie können auch einen einfacheren Prozess auswählen, der jeglichen bedingten Zugriff aufschiebt, bis die Benutzer nach jeder Phase zur Registrierung aufgefordert wurden. Oder Sie entscheiden sich für einen strikteren Prozess, der den bedingten Zugriff von Anfang an erzwingt und für jeden Zugriff vollständige Konformität erfordert.

- Weitere Informationen zum [bedingten Zugriff](../protect/conditional-access.md).

## <a name="task-list-for-conditional-access"></a>Aufgabenliste für den bedingten Zugriff

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>Aufgabe 1: Entscheiden Sie, wie Sie den bedingten Zugriff implementieren.

[Gängige Möglichkeiten für die Verwendung des bedingten Zugriffs](../protect/conditional-access-intune-common-ways-use.md)

### <a name="task-2-set-up-intune-conditional-access"></a>Aufgabe 2: Richten Sie den bedingten Zugriff für Intune ein.

Wählen Sie eine der folgenden Optionen aus:

- [Konfigurieren des bedingten Zugriffs in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

- [Installieren des lokalen Exchange Connectors für Intune](../protect/exchange-connector-install.md)

- [Einrichten App-basierter Richtlinien für bedingten Zugriff für Exchange Online](../protect/app-based-conditional-access-intune-create.md)

- [Einrichten App-basierter Richtlinien für bedingten Zugriff für SharePoint Online](../protect/app-based-conditional-access-intune-create.md)

- [Blockieren von Apps, die keine moderne Authentifizierung verwenden (ADAL)](../protect/app-modern-authentication-block.md)

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über den [typischen Migrationszyklus](../migration-guide-cycle.md).
