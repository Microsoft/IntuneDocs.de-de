---
title: Technologieentscheidungen für BYOD mit EMS
description: Wichtige Technologieentscheidungen zum Ermöglichen von BYOD und Schutz von Unternehmensdaten mit Microsoft Enterprise Mobility + Security
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/8/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c95ddce53b084fe5fc7adce577ccc80224ae1db8
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722214"
---
# <a name="technology-decisions-for-enabling-byod-with-microsoft-enterprise-mobility--security-ems"></a>Technologieentscheidungen zur Ermöglichung von BYOD mit Microsoft Enterprise Mobility + Security (EMS)

Bei der Entwicklung Ihrer Strategie, um Mitarbeitern das Arbeiten von einem externen Standort aus auf ihren eigenen Geräten (Bring Your Own Device, BYOD) zu ermöglichen, müssen Sie wichtige Entscheidungen treffen. Dies betrifft Szenarien, in denen BYOD ermöglicht werden soll, und die Art und Weise, wie Ihre Unternehmensdaten zu schützen sind. Erfreulicherweise bietet Ihnen EMS alle Funktionen, die Sie benötigen, in einem umfassenden Lösungspaket.  

In diesem Thema untersuchen wir den einfachen Anwendungsfall, BYOD-Zugriff auf Unternehmens-E-Mails zu ermöglichen. Wir befassen uns mit der Frage, ob Sie das gesamte Gerät oder lediglich die Anwendungen verwalten müssen, wobei beide Möglichkeiten vollkommen denkbare Optionen darstellen.

## <a name="assumptions"></a>Annahmen
* Sie besitzen Grundkenntnisse zu Azure Active Directory und Microsoft Intune.
* Ihre E-Mail-Konten werden in Exchange Online gehostet.

## <a name="common-reasons-to-manage-the-device-mdm"></a>Häufige Gründe für die Verwaltung von Geräten (MDM)
Sie können Benutzer ganz einfach dazu bringen, ihre Geräte bei der Geräteverwaltung zu registrieren, indem Sie eine [Richtlinie für bedingten Zugriff](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) in Exchange Online bereitstellen. Im Folgenden werden die Gründe aufgeführt, warum sich die Verwaltung persönlicher Geräte empfiehlt:

**WLAN/VPN** – Wenn Ihre Benutzer zur Produktivitätssteigerung ein Unternehmenskonnektivitätsprofil benötigen, so kann dieses nahtlos konfiguriert werden.

**Anwendungen** – Wenn Ihre Benutzer eine Reihe von Apps benötigen, die mithilfe von Push auf ihre Geräte übertragen werden sollen, können diese nahtlos bereitgestellt werden. Dazu gehören auch Anwendungen, die Sie für Sicherheitszwecke benötigen, wie eine Mobile Threat Defense-App.

**Compliance** – Einige Organisationen müssen gesetzliche Bestimmungen oder andere Richtlinien einhalten, die bestimmte MDM-Kontrollen vorschreiben. Beispielsweise müssen Sie mit MDM das gesamte Gerät verschlüsseln oder einen Bericht über alle Apps auf dem Gerät erstellen.

## <a name="common-reasons-to-only-manage-the-apps-mam"></a>Häufige Gründe für die ausschließliche Verwaltung von Apps (MAM)
MAM ohne MDM ist besonders bei Organisationen beliebt, die BYOD unterstützen. Sie können Benutzer dazu anhalten, über Outlook Mobile (mit Unterstützung für MAM-Schutz) auf E-Mails zuzugreifen, indem Sie eine Richtlinie für bedingten Zugriff in Exchange Online bereitstellen. Im Folgenden werden die Gründe aufgeführt, warum sich die Verwaltung von ausschließlich Apps auf persönlichen Geräten empfiehlt:

**Benutzerfreundlichkeit** – Die MDM-Registrierung beinhaltet viele Warnhinweise (die von der Plattform erzwungen werden), die oft dazu führen, dass der Benutzer seine E-Mails letztlich doch nicht mehr auf seinem persönlichen Gerät abrufen möchte. MAM sendet weitaus weniger Warnhinweise an Benutzer, da ihnen lediglich einmal ein Popupfenster angezeigt wird, das sie darüber informiert, dass der MAM-Schutz aktiv ist.

**Compliance** – Einige Organisationen müssen sich an Richtlinien halten, die weniger Verwaltungsfunktionen auf persönlichen Geräten erfordern. So kann MAM beispielsweise nur Unternehmensdaten aus den Apps entfernen, wohingegen MDM alle Daten vom Gerät entfernen kann.

![Abbildung zum Vergleich der Geräte- und App-Verwaltung auf mobilen Geräten](./media/byod-technology-decisions/byod-app-device-mgmt.png)

Weiterer Informationen finden Sie in der [Übersicht über die Lebenszyklen von Geräten und Apps](device-lifecycle.md).

## <a name="mdm-vs-mam-capability-comparison"></a>Vergleich der MDM- und MAM-Funktionen
Wie bereits erwähnt, kann der bedingte Zugriff Benutzer dazu bringen, ein Gerät zu registrieren oder eine verwaltete App wie Outlook Mobile zu verwenden. In beiden Fällen können viele andere Bedingungen angewendet werden. Hierzu gehören u.a. Folgende:

* Für das Zulassen des benutzerseitigen Zugriffs
* Für das Festlegen von vertrauenswürdigen oder nicht vertrauenswürdigen Speicherorten
* Für das Festlegen des Risikograds bei der Anmeldung
* Geräteplattform

Nach wie vor sind zahlreiche Organisationen oftmals mit besonderen Risiken konfrontiert.  In der folgenden Tabelle werden häufige Probleme und die entsprechenden Antworten bezüglich MDM und MAM aufgelistet.

| Problem   |   MDM  |   MAM  |
|------------|--------|--------|
|Nicht autorisierter Datenzugriff | Erzwingen von Gruppenmitgliedschaften | Erzwingen von Gruppenmitgliedschaften |
|Nicht autorisierter Datenzugriff | Erzwingen einer Geräteregistrierung | Erzwingen einer geschützten App |
|Nicht autorisierter Datenzugriff | Erzwingen eines speziellen Speicherorts | Erzwingen eines speziellen Speicherorts |
| | | |
|Gefährdetes Benutzerkonto| MFA erforderlich | MFA erforderlich|
|Gefährdetes Benutzerkonto | Blockieren von Benutzern mit hohem Risiko | Blockieren von Benutzern mit hohem Risiko |
|Gefährdetes Benutzerkonto | Geräte-PIN | App-PIN |
| | | |
| Gefährdetes Gerät oder gefährdete App | Erzwingen eines konformen Geräts | Prüfen auf Jailbreaks beim App-Start |
| Gefährdetes Gerät oder gefährdete App | Verschlüsseln von Gerätedaten | App-Daten verschlüsseln |
| | | |
|Verlust oder Diebstahl eines Geräts | Entfernen aller Gerätedaten | Entfernen aller App-Daten|
| | | |
| Versehentliche Datenfreigabe oder Speichern an unsicheren Speicherorten | Einschränken von Datensicherungen für Geräte | Einschränken von Vorgängen zum Ausschneiden, Kopieren bzw. Einfügen|
| Versehentliche Datenfreigabe oder Speichern an unsicheren Speicherorten | Einschränken der Speicherfunktion | Einschränken der Speicherfunktion |
|Versehentliche Datenfreigabe oder Speichern an unsicheren Speicherorten | Drucken deaktivieren | Nicht zutreffend|

## <a name="next-steps"></a>Nächste Schritte
Jetzt ist es an der Zeit zu entscheiden, ob BYOD in Ihrer Organisation ermöglicht und der Schwerpunkt dabei auf der Geräte- oder App-Verwaltung oder auf einer Kombination beider Optionen liegen soll. Die Wahl der Implementierung liegt bei Ihnen. Dabei können Sie darauf vertrauen, dass die Identitäts- und Sicherheitsfeatures von Azure AD in beiden Fällen verfügbar sind.  

Verwenden Sie das Intune-[Planungshandbuch](planning-guide.md), um Ihre nächste Planungsebene zu planen.
