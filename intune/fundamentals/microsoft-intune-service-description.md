---
title: Microsoft Intune-Dienstbeschreibung
description: Microsoft Intune ist ein cloudbasierter Dienst, der Ihnen bei der Verwaltung von Windows-, iOS/iPadOS-, Mac OS X-, Android- und mobilen Windows-Geräten hilft.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 05/30/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b65276ed2da827017406c67838afd89a766b2dc
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515066"
---
# <a name="microsoft-intune-service-description"></a>Microsoft Intune-Dienstbeschreibung

Intune ist ein cloudbasierter Enterprise Mobility-Verwaltungsdienst (Enterprise Mobility Management; EMM), der die Produktivität Ihrer Mitarbeiter unterstützt und gleichzeitig Ihre Unternehmensdaten schützt. Mit Intune können Sie folgende Aktionen ausführen:
* Die mobilen Geräte verwalten, die Ihre Mitarbeiter verwenden, um auf Unternehmensdaten zuzugreifen
* Die Client-Apps verwalten, die Ihre Mitarbeiter verwenden
* Ihre Unternehmensinformationen schützen, indem Sie steuern, wie Ihre Mitarbeiter darauf zugreifen und diese freigeben
* Sicherstellen, dass Geräte und Apps kompatibel mit den Sicherheitsanforderungen des Unternehmens sind

Die Lösung lässt sich eng in Azure Active Directory (Azure AD) integrieren und bietet Identitäts- und Zugriffsteuerungsfunktionen sowie Azure Information Protection für den Datenschutz. Sie können auch eine Integration mit Configuration Manager durchführen, um die Verwaltungsfunktionen zu erweitern.

Weitere Informationen zum Verwalten von Geräten und Apps und zum Schützen von Unternehmensdaten mit Intune finden Sie in der [Intune-Dokumentation](../index.yml).

## <a name="30-day-free-trial"></a>30-tägige kostenlose Testversion
Sie können Intune zunächst mit einer 30-tägigen kostenlosen Testversion verwenden, die 100 Benutzerlizenzen enthält. Um Ihre kostenlose Testversion zu starten, [besuchen Sie die Anmeldeseite von Intune](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20). Wenn Ihre Organisation über ein Enterprise Agreement oder einen vergleichbaren Volumenlizenzvertrag verfügt, wenden Sie sich an Ihren Microsoft-Vertreter, um Ihre kostenlose Testversion einzurichten.

> [!NOTE]
> Wenn Ihre Organisation bereits über ein Geschäfts- oder Schulkonto für Microsoft Online Services verfügt und Sie dieses Intune-Abonnement nach Ende der Testphase möglicherweise in die Produktionsumgebung übernehmen möchten, wählen Sie die **Anmelden**-Option auf dieser Seite. Zur Authentifizierung verwenden Sie das globale Administratorenkonto Ihrer Organisation. Dadurch wird sichergestellt, dass Ihre Intune-Testversion mit Ihrem bestehenden Geschäfts-, Schul- oder Unikonto verknüpft wird.

<!--- For a list of settings that you can set up on mobile devices, see:

- [Enrolled device management capabilities of Microsoft Intune](introduction-intune.md)

--->
## <a name="intune-onboarding-benefit"></a>Intune Onboarding-Vorteil
Microsoft bietet den Vorteil des Intune Onboardings für zulässige Dienste in zulässigen Plänen. Das Onboarding ermöglichen Ihnen die Remotezusammenarbeit mit Microsoft-Spezialisten, um Ihre Intune-Umgebung einzurichten. Weitere Informationen zu den Vorteilen des Onboarding finden Sie unter der [Beschreibung des Angebots für das Microsoft Intune-Onboarding](https://go.microsoft.com/fwlink/?LinkId=619281).


## <a name="learn-how-intune-service-updates-affect-you"></a>Erfahren Sie, wie sich Intune-Dienstupdates auf Sie auswirken

Da sich das Ökosystem für die mobile Geräteverwaltung durch Updates von Betriebssystemen und Veröffentlichungen mobiler Apps häufig ändert, wird Intune von Microsoft regelmäßig aktualisiert. Es gibt drei Möglichkeiten, sich über Änderungen am Intune-Dienst zu informieren:

- [Neuerungen in Microsoft Intune](whats-new.md). Dieses Thema wird mit dem monatlichen Dienstupdate und zudem wöchentlich aktualisiert, wenn z.B. Apps wie die Unternehmensportal-App veröffentlicht werden.

- Wichtige Dienstupdates werden auch im [Microsoft 365 Admin Center](https://admin.microsoft.com/) im Nachrichtencenter angekündigt. Wenn Sie die begleitende [mobilen Office 365-Admin-App](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a) installieren, können Sie Benachrichtigungen auf Ihrem mobilen Gerät erhalten. Erfahren Sie mehr über das [Office 365-Nachrichtencenter](https://support.office.com/client/results?Shownav=true&ns=O365ENTADMIN&version=15&ver=15&HelpID=O365E_MCManageUpdates).

  Einige hilfreiche Tipps:

  - Die Nachrichten im Office 365-Nachrichtencenter sind zielgerichtet. Wenn Ihr Unternehmen z. B. nicht mit Intune for Education arbeitet, werden Sie zu Intune for Education nicht benachrichtigt.

  - Nachrichten laufen ab. Beispielsweise läuft die Benachrichtigung mit einem Link zur Seite „Neuerungen“, dass Ihr Dienst aktualisiert wurde, beispielsweise wahrscheinlich vor der Benachrichtigung zum nächsten Dienstupdate ab. Andernfalls hätten Sie einen großen Rückstand von Beiträgen, die möglicherweise nicht mehr relevant sind.

  - Die mobile App für die Office 365-Verwaltung ermöglicht Ihnen das Durchsuchen aller Nachrichten und Weiterleiten der Benachrichtigung, wenn Sie diese mit Kollegen in Ihrer Organisation teilen möchten.

  - Unter „Einstellungen für das Nachrichtencenter bearbeiten“ finden Sie nun eine Umschaltfläche für **Intune**, sodass Sie sich diese an ein Intune-Abonnement übermittelten Nachrichten ansehen können. Wenn „Verwaltung mobiler Geräte für Office 365“ angezeigt wird, handelt es sich um einen anderen Dienst und nicht um Intune.

- Außerdem bieten wir zwei Blogs zum Veröffentlichen der bewährten Methoden für den Support für Enterprise Mobility + Security (EMS) und Intune:

  - [Blog zu Enterprise Mobility + Security](https://blogs.technet.microsoft.com/enterprisemobility/)

  - [Blog zum Intune-Support](https://blogs.technet.microsoft.com/intunesupport/)

> [!Note]
> Sie können die Dienstintegrität von Intune im [Microsoft 365 Admin Center](https://admin.microsoft.com) überwachen. Wählen Sie im linken Bereich **Dienststatus** aus. Sie können auch die [mobile App für die Office 365-Verwaltung](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a) zum Anzeigen des Dienststatus nutzen.

## <a name="types-of-notices-microsoft-provides-about-the-intune-service"></a>Typen von Benachrichtigungen von Microsoft zum Intune-Dienst

Abhängig von den Auswirkungen der Änderung werden Sie mindestens 7 bis 90 Tage vor der Dienständerung benachrichtigt, damit Sie Dienständerungen planen können. Bei diesen Änderungen kann es sich um die folgenden Arten handeln:

- Änderungen an der Endbenutzeroberfläche, die Sie mit Ihren Helpdeskmitarbeitern oder Endbenutzern teilen möchten. Bei diesen Änderungen erfolgt in der Regel eine Benachrichtigung 7 bis 30 Tage zuvor, die im Artikel zu den [Neuerungen auf der Benutzeroberfläche der Intune-App](whats-new-app-ui.md) dokumentiert werden. Eine Korrektur eines Rechtschreibfehlers wird allerdings meist nicht dokumentiert. Doch bei einer wichtigen Änderung an der Oberfläche zur Benutzerregistrierung übermitteln wir über das Office 365-Nachrichtencenter eine Nachricht an unsere Kunden mit einem Link zum Artikel mit den Änderungen an der Intune App-Benutzeroberfläche. Sie werden also über die Änderungen benachrichtigt und haben Zeit, Ihre Anleitungen für Endbenutzer zu prüfen und zu aktualisieren, ehe die Änderungen in der Produktionsumgebung übernommen werden.

- Änderungen, die Maßnahmen Ihrerseits erfordern, heißen **Plan for Change** (Änderungen einplanen) und erfolgen in der Regel mit einer Vorlaufzeit von 30 Tagen. Im Office 365-Nachrichtencenter heißt die Kategorie explizit „Plan for Change“ (Änderungen einplanen). Sobald das exakte Datum vorliegt, an dem die Änderung in der Produktionsumgebung erfolgt, wird auch eine **Handlungsfrist** mit einer visuellen Warteschlange und einem Ausrufezeichen angegeben.

- Bei den meisten veralteten Funktionen erfolgt eine entsprechende Benachrichtigung 90 Tage zuvor. Wenn wir beispielsweise für eine bestimmte Version von Internet Explorer keinen Support mehr bieten, ist es unser Ziel, Sie 90 Tage vorher zu benachrichtigen. Bei veraltete Funktionen kann es kompliziert werden, wenn die Veraltung von einem anderen Unternehmen angekündigt wird. Angenommen, ein Browserhersteller hat angekündigt, dass Silverlight von seinem neuesten Build nicht mehr unterstützt wird. Daraufhin informieren wir Kunden, dass wir den Support für diesen Browser einstellen, wobei unsere Benachrichtigung der Kunden der 90-Tage-Frist unterliegt.

- Im Falle einer Deaktivierung des Intune-Diensts würden Sie 12 Monate im Voraus informiert.

Wenn schließlich im seltenen Fall, dass im Anschluss an einen Vorfall Maßnahmen zum Wiederherstellen Ihres Diensts oder eine umfassende Änderung mit nach Rückmeldungen von Kunden potenziellem Störpotenzial erforderlich sein sollten, werden basierend auf Ihren [Kommunikationseinstellungen für Office 365](https://support.office.com/article/Change-your-contact-preferences-for-communications-from-Microsoft-6f70de1b-a64d-4498-bfbd-be8c83a9c0fc) E-Mails an die Dienstadministratoren gesendet. Voraussetzung ist eine gültige (vorzugsweise geschäftliche) E-Mail-Adresse.  


<!--- ## Choose the management solution that’s right for you
You can set up Intune in several ways to manage and help protect your company's mobile devices and computers (referred to as **devices** in this article).

- **Intune stand-alone configuration.** Use the web-based admin console in Intune to manage devices in your organization. Intune can be used without any on-premises IT infrastructure. If you use Intune with Active Directory Domain Services, you can use domain user accounts that you manage with Domain Services with Intune.

--->

## <a name="language-support"></a>Sprachunterstützung
Intune wird im Azure-Portal ausgeführt, das folgende Sprachen unterstützt: Chinesisch (Vereinfacht), Chinesisch (Traditionell), Tschechisch, Niederländisch, Englisch, Deutsch, Ungarisch, Italienisch, Japanisch, Portugiesisch (Brasilien), Portugiesisch (Portugal), Russisch, Spanisch, Französisch, Koreanisch, Polnisch, Schwedisch und Türkisch.

Die Intune-Verwaltungskonsole und die mobilen Oberflächen für Benutzer unterstützen zusätzlich zu allen vom Azure-Portal unterstützten Sprachen außerdem Dänisch, Griechisch, Finnisch, Norwegisch und Rumänisch.

<!--- ## Learn more about Intune
Use these resources to learn more about Intune:

- The [Microsoft Intune Trust Center](https://www.microsoft.com/server-cloud/products/intune-trust-center/) provides information about the security, privacy, and compliance practices of Intune, and it describes some of Intune's certifications.

- [Enrolled device management capabilities of Microsoft Intune](introduction-intune.md)--->
