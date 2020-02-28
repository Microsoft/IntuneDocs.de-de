---
title: Geräteverwaltung in Microsoft 365
description: Microsoft 365 Enterprise umfasst Microsoft Intune. Erfahren Sie, wie Intune Ihrer Organisation die Verwaltung mobiler Geräte und Anwendungen ermöglicht. Machen Sie sich mit den gängigen Szenarien vertraut, und nutzen Sie Intune, um Microsoft 365 in Ihrer Umgebung bereitzustellen.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
audience: ITPro
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3a15bf0bd8ed0a46f330b159e45d0a5d5a4c7059
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510383"
---
# <a name="device-management-overview"></a>Übersicht über die Geräteverwaltung

Eine Hauptaufgabe eines jeden Administrators ist der Schutz und die Sicherung der Ressourcen und Daten eines Unternehmens. Diese Aufgabe ist die *Geräteverwaltung*. Benutzer verfügen über viele Geräte, auf denen sie persönliche Dateien öffnen und freigeben, Websites besuchen sowie Apps und Spiele installieren. Dieselben Benutzer sind zugleich Mitarbeiter und Schüler bzw. Studenten. Sie möchten auf ihren Geräten auf Arbeits-, Uni- und Schulressourcen wie E-Mail und OneNote zugreifen.

Die Geräteverwaltung ermöglicht es Unternehmen, ihre Ressourcen und Daten auf unterschiedlichen Geräten zu schützen und zu sichern.

Mithilfe eines Anbieters für die Geräteverwaltung können Unternehmen sicherstellen, dass nur autorisierte Personen und Geräte Zugriff auf geschützte Informationen erhalten. Ebenso können sich Gerätebenutzer beim Zugriff auf Unternehmensdaten auf ihrem Smartphone sicher fühlen, da sie wissen, dass ihr Gerät den Sicherheitsanforderungen ihrer Organisation entspricht. Als Unternehmen könnten Sie sich fragen: **Womit können wir unsere Ressourcen schützen?**

Die Antwort ist [Microsoft Intune](what-is-intune.md). Intune bietet die Verwaltung mobiler Geräte (MDM) und mobiler Anwendungen (MAM). Zu den Hauptaufgaben einer jeden MDM- oder MAM-Lösung gehören:

- Unterstützen einer vielseitigen mobilen Umgebung und sicheres Verwalten von iOS-/iPadOS-, Android-, Windows- und macOS-Geräten
- Sicherstellen, dass Geräte und Apps die Sicherheitsanforderungen der Organisation erfüllen
- Erstellen von Richtlinien, um die Daten Ihrer Organisation auf organisationseigenen und privaten Geräten zu schützen
- Verwenden einer einzelnen, einheitlichen mobilen Lösung zur Durchsetzung dieser Richtlinien und zur Verwaltung von Geräten, Anwendungen, Benutzern und Gruppen
- Schützen Ihrer Unternehmensinformationen, indem Sie steuern, wie Ihre Mitarbeiter auf Daten zugreifen und diese freigeben

Intune ist in Microsoft Azure und Microsoft 365 enthalten und lässt sich in Azure Active Directory (Azure AD) integrieren. Azure AD hilft bei der Kontrolle, welche Personen auf welche Daten Zugriff haben.

## <a name="microsoft-intune"></a>Microsoft Intune

Viele Unternehmen wie Microsoft verwenden Intune, um proprietäre Daten zu schützen, auf die Benutzer von ihren unternehmenseigenen und privaten mobilen Geräten aus zugreifen können. Intune enthält Konfigurationsrichtlinien für Geräte und Apps, Richtlinien für Softwareupdates und Installationsstatus (Diagramme, Tabellen und Berichte), die Ihnen helfen, den Datenzugriff zu schützen und zu überwachen.

Es ist üblich, dass Benutzer über mehrere Geräte verfügen, die unterschiedliche Plattformen verwenden. So kann ein Mitarbeiter z. B. Surface Pro für die Arbeit und ein mobiles Android-Gerät für den privaten Gebrauch nutzen. Außerdem ist es üblich, dass eine Person von diesen verschiedenen Geräten aus auf Unternehmensressourcen wie Microsoft Outlook und SharePoint zugreift.

Mit Intune können Sie mehrere Geräte pro Person und die darauf ausgeführten verschiedenen Plattformen verwalten, einschließlich iOS/iPadOS, macOS, Android und Windows. Intune unterscheidet dabei zwischen Richtlinien und Einstellungen nach Geräteplattform. Dadurch ist es einfach, Geräte einer bestimmten Plattform zu verwalten und anzuzeigen.

**[Allgemeine Szenarien](common-scenarios.md)** ist eine hervorragende Ressource, um zu sehen, wie Intune häufige Fragen beim Arbeiten mit mobilen Geräten beantwortet. Sie finden Szenarien zu den folgenden Themen:  

- Schützen von E-Mails mit lokalem Exchange
- Sicherer und geschützter Zugriff auf Office 365
- Verwenden privater Geräte für den Zugriff auf Unternehmensressourcen

Weitere Informationen zu Intune finden Sie unter [Was ist Microsoft Intune?](what-is-intune.md).

## <a name="integration-with-secure-and-protect-services"></a>Integration mit Diensten für Sicherheit und Schutz

Eine Hauptaufgabe einer jeden Lösung für die Geräteverwaltung ist es, Sicherheit und Schutz zu bieten. Intune leistet bei der Integration mit anderen Diensten hervorragende Arbeit, um diese Aufgabe zu erfüllen. Beispiel:

- **Microsoft 365** ist eine Schlüsselkomponente zur Vereinfachung gängiger IT-Aufgaben. Im Microsoft 365 Admin Center können Sie Benutzer erstellen und Gruppen verwalten. Außerdem erhalten Sie Zugriff auf andere Dienste wie z.B. Intune und Azure AD.

  Erstellen Sie z. B. in Microsoft 365 eine iOS-/iPadOS-Gerätegruppe. Verwenden Sie dann Intune, um Richtlinien an die iOS-/iPadOS-Gerätegruppe weiterzugeben, die sich auf iOS-/iPadOS-Funktionen konzentrieren, z. B. den Zugriff auf den App Store, die Verwendung von AirDrop, die Sicherung in iCloud, die Verwendung des Webfilters von Apple und mehr.

- **Windows Defender** enthält viele Sicherheitsfeatures zum Schutz von Windows 10-Geräten. Wenn Sie z. B. Intune und Windows Defender zusammen verwenden, haben Sie die folgenden Möglichkeiten:

  - Aktivieren Sie [Windows Defender SmartScreen](../protect/endpoint-protection-windows-10.md), um nach verdächtigen Aktivitäten in Dateien und Apps auf mobilen Geräten zu suchen.
  - Verwenden Sie [Microsoft Defender Advanced Threat Protection (ATP)](../protect/advanced-threat-protection.md), um Sicherheitsverletzungen auf mobilen Geräten zu verhindern. Und helfen Sie, die Auswirkungen eines Sicherheitsverstoßes zu begrenzen, indem Sie einen Benutzer von Unternehmensressourcen ausschließen.

- **Bedingter Zugriff** ist ein Feature von Azure Active Directory, das gut in Intune integriert werden kann. Mithilfe des [bedingten Zugriffs](../protect/conditional-access.md) können Sie sicherstellen, dass nur konforme Geräte auf E-Mail, SharePoint und andere Apps zugreifen dürfen.

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Wählen Sie die Geräteverwaltungslösung aus, die für Sie geeignet ist

Es gibt mehrere Möglichkeiten, die Geräteverwaltung anzugehen. Zunächst können Sie verschiedene Aspekte von Geräten verwalten, indem Sie alle in Intune integrierten Features nutzen. Dieser Ansatz wird als **Verwaltung mobiler Geräte (Mobile Device Management, MDM)** bezeichnet. Benutzer „registrieren“ ihre Geräte und verwenden Zertifikate, um mit Intune zu kommunizieren. Als IT-Administrator können Sie Anwendungen per Push auf Geräte verteilen, Geräte auf ein bestimmtes Betriebssystem beschränken, private Geräte blockieren und vieles mehr. Wenn ein Gerät einmal verloren geht oder gestohlen wird, können Sie auch alle Daten von dem Gerät entfernen.

Im zweiten Ansatz verwalten Sie Apps auf Geräten. Dieser Ansatz wird als **Verwaltung mobiler Anwendungen (Mobile Device Management, MAM)** bezeichnet. Benutzer können mit ihren privaten Geräten auf Organisationsressourcen zugreifen. Beim Öffnen einer App, wie E-Mail oder SharePoint, werden die Benutzer zur zusätzlichen Authentifizierung aufgefordert. Wenn ein Gerät einmal verloren geht oder gestohlen wird, können Sie alle Unternehmensdaten von dem Gerät entfernen.

Sie können auch eine Kombination aus [MDM und MAM](byod-technology-decisions.md) verwenden.

Wenn Sie Intune einrichten, können Sie Geräte auch ausschließlich im Azure-Portal verwalten oder dazu Intune und Microsoft 365 gemeinsam verwenden. [Migrating mobile device management to Intune in the Azure portal](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) (Migrieren der Verwaltung mobiler Geräte zu Intune im Azure-Portal) ist eine Fallstudie der Microsoft-IT. In dieser Fallstudie erfahren Sie, wie Microsoft IT einen modernen Ansatz zur Geräteverwaltung gewählt hat und welche Erkenntnisse daraus gewonnen wurden.

## <a name="simplify-it-tasks-using-the-device-management-admin-center"></a>Vereinfachen von IT-Aufgaben mit dem Device Management Admin Center

Das [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) ist eine zentrale Anlaufstelle für die Verwaltung und Durchführung von Aufgaben für Ihre mobilen Geräte. Dieser Arbeitsbereich enthält die Dienste für die Geräteverwaltung, einschließlich Intune und Azure Active Directory, sowie für die Verwaltung von Clientanwendungen.

Im Admin Center für die Geräteverwaltung haben Sie folgende Optionen:

- [Registrieren von Geräten](../enrollment/device-enrollment.md)
- [Festlegen der Gerätekonformität](../protect/device-compliance-get-started.md)
- [Verwalten von Geräten](../remote-actions/device-management.md)
- [Verwalten von Apps](../apps/app-management.md)  
- [iOS-E-Books](../apps/vpp-ebooks-ios.md)  
- [Installieren des Connectors für Exchange lokal](../protect/exchange-connector-install.md)  
- [Verwalten von Rollen](role-based-access-control.md)  
- Verwalten von Softwareupdates
  - [Verwalten von Windows 10-Updates](../protect/windows-update-for-business-configure.md)  
  - [Verwalten von iOS-/iPadOS-Updates](../protect/software-updates-ios.md)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [Verwalten von Benutzern](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Verwalten von Gruppen und Mitglieder](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Problembehandlung](help-desk-operators.md)

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie bereit sind, in eine MDM- oder MAM-Lösung einzusteigen, führen Sie die verschiedenen Schritte durch, um Intune einzurichten, Geräte zu registrieren und Richtlinien zu erstellen. [Verwaltung mobiler Geräte für Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure) ist ebenfalls eine gute Ressource.
