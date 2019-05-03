---
title: Geräteverwaltung in Microsoft 365
description: Microsoft 365 Enterprise umfasst Microsoft Intune. Sehen Sie, wie Intune die Verwaltung mobiler Geräte und Verwaltung von mobilen Anwendungen für Ihre Organisation bereitstellt. Lesen Sie allgemeine Szenarien, und verwenden Sie Intune zum Bereitstellen von Microsoft 365 in Ihrer Umgebung.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/29/2019
ms.topic: conceptual
audience: ITPro
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 15f908a34f0a9315552acfad56cbf560a23fa26d
ms.sourcegitcommit: e63e3debb5f4d9a757f767913e72e39742137b17
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2019
ms.locfileid: "58788444"
---
# <a name="what-is-device-management"></a>Was ist die Geräteverwaltung? 

Eine Hauptaufgabe eines jeden Administrators ist der Schutz und die Sicherung der Ressourcen und Daten eines Unternehmens. Diese Aufgabe ist die *Geräteverwaltung*. Benutzer verfügen über viele Geräte, von denen aus sie persönliche Dateien öffnen und freigeben, Websites besuchen und Apps und Spiele installieren. Diese Benutzer sind auch an Mitarbeiter und Studenten. Sie möchten ihre Geräte zu verwenden, um den Zugriff auf Geschäfts- und schulressourcen wie z. B. e-Mail-Adresse und OneNote. Die Geräteverwaltung ermöglicht es Unternehmen, ihre Ressourcen und Daten zu schützen und zu sichern. 

Mithilfe eines Anbieters für die Geräteverwaltung können Unternehmen sicherstellen, dass nur autorisierte Personen und Geräte Zugriff auf geschützte Informationen erhalten. Ebenso können sich Gerätebenutzer beim Zugriff auf Unternehmensdaten von ihrem Telefon aus sicher fühlen, da sie wissen, dass ihr Gerät den Sicherheitsanforderungen ihres Unternehmens entspricht. Als Unternehmen könnten Sie sich fragen: **Womit können wir unsere Ressourcen schützen?**

Die Antwort ist [Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune). Intune bietet die Verwaltung mobiler Geräte (MDM) und mobiler Anwendungen (MAM). Zu den Hauptaufgaben einer jeden MDM- oder MAM-Lösung gehören:

- Unterstützen einer vielseitigen mobilen UmgebungSicheres Verwalten von iOS-, Android-, Windows- und macOS-Geräten
- Sicherstellen, dass Geräte und Apps mit den Sicherheitsanforderungen des Unternehmens konform sind
- Erstellen von Richtlinien, um die Daten Ihres Unternehmens auf firmeneigenen und privaten Geräten zu schützen
- Verwenden einer einzelnen, einheitlichen mobilen Lösung zur Durchsetzung dieser Richtlinien und zur Verwaltung von Geräten, Anwendungen, Benutzern und Gruppen

Intune ist in Microsoft 365 enthalten und lässt sich in Azure Active Directory (Azure AD) integrieren. Azure AD hilft bei der Kontrolle, welche Personen auf welche Daten Zugriff haben.

## <a name="hello-intune"></a>Hallo Intune!
Viele Unternehmen wie Microsoft verwenden Intune, um proprietäre Daten zu schützen, auf die Benutzer von ihren unternehmenseigenen und privaten mobilen Geräten aus zugreifen können. Intune enthält Features wie Konfigurationsrichtlinien für Geräte und Apps, Richtlinien für Softwareupdates und Installationsstatus (sowie Diagramme, Tabellen und Berichte), die Ihnen helfen, den Datenzugriff zu sichern und zu überwachen.

Es ist üblich, dass Benutzer über mehrere Geräte verfügen, die unterschiedliche Plattformen verwenden. So kann ein Mitarbeiter z. B. Surface Pro für die Arbeit und ein mobiles Android-Gerät für den privaten Gebrauch nutzen. Außerdem ist es üblich, dass eine Person von diesen verschiedenen Geräten aus auf Unternehmensressourcen wie Microsoft Outlook und SharePoint zugreift.

Mit Intune können Sie mehrere Geräte pro Person und die darauf ausgeführten verschiedenen Plattformen verwalten, einschließlich iOS, macOS, Android und Windows. Intune unterscheidet dabei zwischen Richtlinien und Einstellungen nach Geräteplattform. Daher ist es einfach zu verwalten und Geräte, die von einer bestimmten Plattform anzeigen.

**[Allgemeine Szenarien](https://docs.microsoft.com/intune/common-scenarios)** ist eine hervorragende Ressource, um zu sehen, wie Intune häufige Fragen beim Arbeiten mit mobilen Geräten beantwortet. Sie finden Szenarien zu den folgenden Themen:  
- Schützen von E-Mails mit lokalem Exchange
- Sicherer und geschützter Zugriff auf Office 365
- Verwenden privater Geräte für den Zugriff auf Unternehmensressourcen

## <a name="integration-with-secure-and-protect-services"></a>Integration mit Diensten für Sicherheit und Schutz
Eine Hauptaufgabe einer jeden Lösung für die Geräteverwaltung ist es, Sicherheit und Schutz zu bieten. Intune leistet bei der Integration mit anderen Diensten hervorragende Arbeit, um diese Aufgabe zu erfüllen. Zum Beispiel:

- **Microsoft 365** ist eine Schlüsselkomponente zur Vereinfachung gängiger IT-Aufgaben. Im Microsoft 365 Administrationscenter Sie Benutzer erstellen und Verwalten von Gruppen. Außerdem erhalten Sie Zugang zu anderen Diensten, z.B. Intune, Azure AD und vieles mehr. 

  Sie können z. B. eine iOS-Gerätegruppe in Microsoft 365 erstellen. Verwenden Sie dann Intune, um Richtlinien an die iOS-Gerätegruppe weiterzugeben, die sich auf iOS-Features konzentrieren, z. B. Zugriff auf den App Store, Verwendung von AirDrop, Sicherung in iCloud, Verwendung des Webfilters von Apple und mehr.

- **Windows Defender** enthält viele Sicherheitsfeatures zum Schutz von Windows 10-Geräten. Wenn Sie z. B. Intune und Windows Defender zusammen verwenden, haben Sie die folgenden Möglichkeiten: 

    - Aktivieren Sie [Windows Defender SmartScreen](https://docs.microsoft.com/intune/endpoint-protection-windows-10), um nach verdächtigen Aktivitäten in Dateien und Apps auf mobilen Geräten zu suchen. 
    - Verwendung [Windows Defender Advanced Threat Protection (ATP)](https://docs.microsoft.com/intune/advanced-threat-protection) zur Verhinderung von sicherheitsverletzungen auf mobilen Geräten. Und die Auswirkungen von sicherheitsverletzungen begrenzt werden, indem ein Benutzer auf Unternehmensressourcen blockiert.

- **Bedingter Zugriff** ist ein Feature von Azure Active Directory und lässt sich gut mit Intune integrieren. Mithilfe des [bedingten Zugriffs](https://docs.microsoft.com/intune/conditional-access) können Sie sicherstellen, dass nur konforme Geräte auf E-Mail, SharePoint und andere Apps zugreifen dürfen. 

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Wählen Sie die Geräteverwaltungslösung aus, die für Sie geeignet ist

Es gibt mehrere Möglichkeiten, die Geräteverwaltung anzugehen. Erstens können Sie verschiedene Aspekte der Geräte, die mithilfe der Funktionen, die in Intune integriert verwalten. Dies wird als **Verwaltung mobiler Geräte (MDM)** bezeichnet. Bei diesem Ansatz „registrieren“ die Benutzer ihre Geräte und verwenden Zertifikate, um mit Intune zu kommunizieren. Als IT-Administrator können Sie Anwendungen auf Geräte verteilen, Geräte auf ein bestimmtes Betriebssystem beschränken, private Geräte blockieren und vieles mehr. Wenn ein Gerät einmal verloren geht oder gestohlen wird, können Sie auch alle Daten von dem Gerät entfernen. 

Im zweiten Ansatz verwalten Sie Apps auf Geräten. Dies wird als **Verwaltung mobiler Anwendungen (MAM)** bezeichnet. Bei diesem Ansatz können Benutzer mit ihren privaten Geräten auf Unternehmensressourcen zugreifen. Beim Öffnen einer App, wie E-Mail oder SharePoint, werden die Benutzer zur zusätzlichen Authentifizierung aufgefordert. Wenn ein Gerät einmal verloren geht oder gestohlen wird, können Sie alle Unternehmensdaten von dem Gerät entfernen. 

Sie können auch eine Kombination aus [MDM und MAM](https://docs.microsoft.com/intune/byod-technology-decisions) verwenden.

Wenn Sie Intune einrichten, können Sie Geräte auch ausschließlich im Azure-Portal verwalten oder dazu Intune und Microsoft 365 gemeinsam verwenden. [Migrieren von Verwaltung von Mobilgeräten in Intune im Azure-Portal](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) ist eine Microsoft-IT-Fallstudie. In diesem Fall zu untersuchen Sie, sehen Sie, wie Microsoft IT eine verwaltungslösung für moderne Geräte auswählen, und Lesen Sie die Lektionen gelernt.

## <a name="simplify-it-tasks-using-the-device-management-dashboard"></a>Vereinfachen von IT-Aufgaben mit dem Device Management Dashboard

Das [Device Management Dashboard](https://devicemanagement.portal.azure.com/) ist eine zentrale Anlaufstelle für die Verwaltung und Durchführung von Aufgaben für Ihre mobilen Geräte. Dieses Dashboard enthält die Dienste für die Geräteverwaltung, einschließlich Intune und Azure Active Directory, sowie für die Verwaltung von Clientanwendungen. 

Auf dem Device Management Dashboard haben Sie folgende Optionen:

- [Registrieren von Geräten](https://docs.microsoft.com/intune/device-enrollment)
- [Festlegen der Gerätekonformität](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Verwalten von Geräten](https://docs.microsoft.com/intune/device-management)
- [Verwalten von Apps](https://docs.microsoft.com/intune/app-management)  
- [iOS-E-Books](https://docs.microsoft.com/intune/vpp-ebooks-ios)  
- [Installieren des Connectors für Exchange lokal](https://docs.microsoft.com/intune/exchange-connector-install)  
- [Verwalten von Rollen](https://docs.microsoft.com/intune/role-based-access-control)  
- Verwalten von Softwareupdates
  - [Verwalten von Windows 10-Updates](https://docs.microsoft.com/intune/windows-update-for-business-configure)  
  - [Verwalten von iOS-Updates](https://docs.microsoft.com/intune/software-updates-ios)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [Verwalten von Benutzern](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Verwalten von Gruppen und Mitglieder](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Problembehandlung](https://docs.microsoft.com/intune/help-desk-operators)

## <a name="next-step"></a>Nächste Schritte
Wenn Sie bereit sind, mit einer MDM- oder MAM-Lösung einzusteigen, führen Sie die verschiedenen Schritte durch, um Intune einzurichten, Geräte zu registrieren und Richtlinien zu erstellen. Weitere Informationen finden Sie unter Mobile Geräteverwaltung für Microsoft 365. [Verwaltung mobiler Geräte für Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure) ist ebenfalls eine gute Ressource.
