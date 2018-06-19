---
title: Schützen von Apps und Daten
description: Dieses Thema beschreibt die verschiedenen Intune-Features und -Funktionen, die Ihnen zum Schutz Ihrer Unternehmens-Apps und Daten zur Verfügung stehen.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2a05444c757b8e99ca0b897acfcd6238d960aeb2
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31017545"
---
# <a name="protect-apps-and-data-with-microsoft-intune"></a>Schützen von Apps und Daten mit Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune schützt Unternehmensdaten auf verschiedenen Technologieebenen. Auf Ebene der Identität wird Schutz über das Konzept des bedingten Zugriffs implementiert: Der Zugriff auf Dienste ist nur über verwaltete und kompatible Geräte gestattet. Auf Ebene der Clientanwendung schützt die Verwaltung mobiler Anwendungen (Mobile App Management, MAM) vor Datenverlusten: Daten werden nicht an ungeschützte Apps oder Speicherorte verschoben, und bei Verlust oder Diebstahl eines Geräts werden Daten gelöscht. Es empfiehlt sich, diese beiden Schutzebenen zusammen zu verwenden, um den Schutz der Daten zu gewährleisten und gleichzeitig dafür zu sorgen, dass mobile Mitarbeiter produktiv arbeiten können.

Ein wichtiger erster Schritt zum Schutz von Unternehmensdaten ist die Implementierung von bedingtem Zugriff. Hierzu müssen Sie sicherstellen, dass die für den Zugriff auf diese Daten verwendeten Geräte Sicherheitsmaßnahmen wie starke Kennwörter und Verschlüsselung verwenden und nicht gehackt wurden. Mithilfe von Intune können Sie Bedingungen festlegen, denen die Geräte entsprechen müssen, bevor über sie auf geschäftliche E-Mails und Daten zugegriffen werden kann.

[Bedingter Zugriff](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) wird durch zwei Arten von Richtlinien bestimmt, die Sie in Intune festlegen können:
- Sie verwenden [Kompatibilitätsrichtlinien](introduction-to-device-compliance-policies-in-microsoft-intune.md), um die Kompatibilität eines Geräts festzulegen. Damit werden zum Beispiel folgende Einstellungen und Bedingungen ausgewertet:
  - PIN und Kennwörter: Sie können Regeln erstellen, die Kennwörter zum Entsperren eines Geräts erforderlich machen, die Komplexitätsanforderungen für Kennwörter festlegen sowie weitere Kennworteinstellungen vorgeben.
  - Verschlüsselung: Sie können den Zugriff auf Geräte einschränken, die verschlüsselt sind.
  - Ein Gerät wurde nicht per Jailbreak oder Rooting manipuliert: Intune kann erkennen, wenn ein Gerät per Jailbreak manipuliert wurde. Sie können die Richtlinie so festlegen, dass der Zugriff auf solchen Geräten blockiert wird.
- Sie konfigurieren [bedingte Zugriffsrichtlinien](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) für einen bestimmten Dienst wie Exchange Online oder SharePoint Online. Für jeden Dienst können Sie definieren, auf welche Gruppen von Benutzern diese Richtlinien angewendet werden sollen. Beispielsweise können Sie sicherstellen, dass jeder Mitarbeiter der Finanzabteilung nur über registrierte und konforme Geräte auf Unternehmens-E-Mail zugreifen kann.

Die Sicherung des Zugriffs auf Unternehmensressourcen ist nur der erste Schritt hin zum Schutz der Unternehmensdaten. Sie benötigen außerdem die Möglichkeit, die Daten zu schützen, nachdem der Zugriff über das Gerät erfolgt ist. Die Daten können jetzt kopiert, verschoben, an einem anderen Speicherort gespeichert oder mit anderen Benutzern gemeinsam verwendet werden. Intune löst dieses Problem, indem Sie durch Erstellen eines Satzes von Regeln Datenverschiebungen beschränken können. Folgende Regeln können Sie festlegen:
- Blockieren von Kopier-/Einfügevorgängen oder Verhindern einer Datenübertragung außerhalb des Arbeitskontexts.
- Verhindern der Sicherung im persönlichen Cloudspeicher und Verhindern von „Speichern unter“.
- Schützen des App-Zugriffs durch Anfordern von PIN/Kennung oder Unternehmensanmeldeinformationen.
- Festlegen, dass alle Weblinks in Intune Managed Browser geöffnet werden.

Dieser Regelsatz wird als [Richtlinien zur Verwaltung mobiler Anwendungen (Mobile App Management, MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md) bezeichnet . Sie können MAM-Richtlinien auf Apps anwenden, die auf Geräten ausgeführt werden, die von Ihnen verwaltet werden oder die von Ihnen nicht verwaltet werden.  

Sie können Ihre Unternehmensdaten mithilfe von MAM-Richtlinien auf Geräten schützen, die **bei Intune registriert sind**, die **bei einer Drittanbieter-MDM-Lösung registriert sind und dort verwaltet werden**, oder die **bei keiner MDM-Lösung registriert sind** (z. B. Privatgeräte von Mitarbeitern).

Um eine App mit einer MAM-Richtlinie zu verknüpfen, muss die App das Microsoft Intune App Software Development Kit (SDK) umfassen, oder Sie können das App Wrapping Tool verwenden.

In Microsoft Office-Apps beispielsweise ist das Intune App SDK integriert. Die vollständige Liste der unterstützten Apps finden Sie im [Microsoft Intune-Katalog mit mobilen Anwendungen](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) auf der Seite mit den Microsoft Intune-Anwendungspartnern. Wählen Sie eine App aus, um die unterstützten Szenarien, Plattformen und Informationen dazu anzuzeigen, ob die App mehrere Identitäten unterstützt.

Sie können auch [Ihre eigenen, individuellen branchenspezifischen Apps](/intune/apps-prepare-mobile-application-management) für die Verwendung mit MAM-Richtlinien aktivieren.

Wenn ein Gerät verloren geht oder gestohlen wird oder der Benutzer nicht mehr für Ihr Unternehmen arbeitet, können Sie [Unternehmensdaten selektiv löschen](wipe-managed-company-app-data-with-microsoft-intune.md) und nur persönliche Daten auf dem Gerät belassen.
