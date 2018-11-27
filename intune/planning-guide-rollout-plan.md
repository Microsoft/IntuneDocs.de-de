---
title: Bestimmen von Gruppen für den Rollout und des Zeitrahmens
titlesuffix: Microsoft Intune
description: Dieser Artikel hilft Ihnen bei der Entscheidung, für welche Gruppen Microsoft Intune eingeführt werden und wie der Zeitrahmen dafür aussehen soll.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3a63f78f-a7e7-4f44-9288-16b28d5d58ca
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 5f651ea03c727f569b2bf8a82fb3f259ecdc0766
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184368"
---
# <a name="develop-a-rollout-plan"></a>Entwickeln eines Rolloutplans

In Ihrem Rolloutplan wird Folgendes bestimmt: die Gruppen in der Organisation, für die Intune eingeführt werden soll, der Zeitrahmen des Rollouts für jede Gruppe und die verwendeten Registrierungsmethoden.

## <a name="targeted-groups-and-timeframes"></a>Zielgruppen und Zeitrahmen

Überprüfen Sie zunächst die Zielgruppen für den Intune-Rollout, die Sie in Ihren [Anwendungsfallszenarien](planning-guide-scenarios.md) bestimmt haben.

Bestimmen Sie als Nächstes den Zeitrahmen für jede Zielgruppe. Für diese Aufgabe ist normalerweise eine Besprechung zwischen dem Intune-Bereitstellungsteam und den Zielgruppen erforderlich, um den am besten geeigneten Rolloutzeitrahmen für die einzelnen Gruppen zu ermitteln. Die folgenden Punkte müssen in einer Besprechung angesprochen werden:
* Bereitschaft der Gruppe zur Veränderung
* Anzahl der Benutzer und Geräte
* Typen von Geräteplattformen
* Anforderungen
* Geografischer Standort
* Geschäftsrisiken

## <a name="rollout-phases"></a>Rolloutphasen
Organisationen entscheiden sich häufig dafür, die Einführung von Intune mit einer Pilotphase zu beginnen, die auf eine kleine Gruppe von Benutzern in der IT-Abteilung ausgerichtet ist. Die Pilotphase kann dann auf eine größere Gruppe von IT-Benutzern und durch Teilnehmer aus anderen Gruppen der Organisation ergänzt werden.

### <a name="pilot"></a>Pilotphase
Die erste Phase des Rollouts sollte Pilotbenutzer umfassen. Die Pilotbenutzer müssen wissen, dass sie den ersten Benutzer einer neuen Lösung sind. Sie müssen willens sein, Feedback zur Verbesserung von Konfiguration, Dokumentation und Benachrichtigungen bereitzustellen, um den Weg für alle anderen Benutzer in späteren Rolloutphasen zu ebnen. Bei diesen Benutzern darf es sich nicht um Führungskräfte handeln.

Das Pilotprojekt ist eine gute Gelegenheit zum Testen der [Herausforderungen](planning-guide-deployment-goals.md) und verfeinern von [Anforderungen](planning-guide-requirements.md), die Sie zuvor gesammelt haben.

Fügen Sie Ihre Pläne für [Kommunikation](planning-guide-communication-plan.md),[Support](planning-guide-support-plan.md) sowie [Tests und Überprüfungen](planning-guide-test-validation.md) hinzu, um Probleme auszumachen, solange die Auswirkungen auf Benutzer noch gering sind.

### <a name="production-rollout"></a>Rollout in die Produktion
Nach einem erfolgreichen Pilotprojekt sind Sie bereit für den vollständigen Rollout in die Produktionsumgebung, bei der die restlichen Gruppen in Ihrer Organisation einbezogen werden. Es folgen einige Beispiele für unterschiedliche Rolloutgruppen und -phasen:

-   **Abteilungen** <br/>Für Abteilung kann es eine eigene Rolloutphase geben. Sie können dann eine gesamte Abteilung gleichzeitig als Zielgruppe festlegen. Bei dieser Art von Rollout nutzen Benutzer in den einzelnen Abteilungen meist das Mobilgerät auf dieselbe Weise und greifen auf dieselben Anwendungen zu. Für Benutzer gelten womöglich auch dieselben Arten von Richtlinien.

-   **Geografie** <br/>Diese Art der Bereitstellung erfolgt für alle Benutzer an einem bestimmten geografischen Ort, ob auf demselben Kontinent, in demselben Land, derselben Region oder demselben Unternehmensgebäude. Diese Art gestaffelter Bereitstellung ermöglicht, sich auf einen bestimmten Benutzerstandort zu konzentrieren. Hierdurch wird ein Ansatz mit mehr [Benutzerunterstützung](#user-assisted-enrollment) ermöglicht, weil Intune an einer geringeren Anzahl von Standorten gleichzeitig bereitgestellt wird. Da verschiedene Abteilungen oder Anwendungsfälle sich möglicherweise am selben Ort befinden, könnten verschiedene Anwendungsfälle gleichzeitig bereitgestellt werden.

-   **Plattform** <br/>Bei dieser Art der Bereitstellung werden ähnliche Plattformen gleichzeitig bereitgestellt. Beispielsweise werden im ersten Monat alle iOS-Geräte verwendet, gefolgt von Android und dann von Windows. Diese Art gestaffelter Bereitstellung vereinfacht die Unterstützung durch das Helpdesk, da das Helpdesk immer nur eine Plattform gleichzeitig unterstützen muss.

Dieses Beispiel zeigt einen Intune-Rolloutplan, der Zielgruppen und Zeitrahmen umfasst:

| **Rolloutphase** | **Juli** | **August** | **September** | **Oktober** |
|:---:|:---:|:---:|:---:|:---:|
| Begrenztes Pilotprojekt | IT (50 Benutzer) |  |  |  |                                                         
| Erweitertes Pilotprojekt | IT (200 Benutzer), IT-Führungskräfte (10 Benutzer) |  |  |  |                                                         
| Produktionsrolloutphase 1 |  | Vertrieb und Marketing (2.000 Benutzer) |  |  |
| Produktionsrolloutphase 2 |  |  | Einzelhandel (1.000 Benutzer) |  |
| Produktionsrolloutphase 3 |  |  |  | Personalabteilung (50 Benutzer), Finanzabteilung (40 Benutzer), Führungskräfte (30 Benutzer) |

Sie können [eine Vorlage der obigen Tabelle herunterladen](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), um die Rolloutphasen Ihrer Organisation einzutragen.
## <a name="match-rollout-groups-to-enrollment-approaches"></a>Abstimmen von Rolloutgruppen mit Registrierungsmethoden

Nachdem Sie die Zielgruppen und den Zeitrahmen für den Intune-Rollout festgelegt haben, besteht der nächste Schritt darin, für jede Gruppe die geeignete Methode für die Intune-Registrierung zu wählen. Es gibt verschiedene Registrierungsmethoden:
* Benutzer-Self-Service
* Registrierung mit Benutzerunterstützung
* IT-Hausmesse

### <a name="user-self-service"></a>Benutzer-Self-Service

In diesem Fall ist der Benutzer für das Registrieren des eigenen Geräts verantwortlich und befolgt in der Regel die von der IT-Organisation vorgegebenen Registrierungsanweisungen. Diese Methode wird in Organisationen am häufigsten verwendet und ist skalierbarer als die Registrierung mit Benutzerunterstützung.

### <a name="user-assisted-enrollment"></a>Registrierung mit Benutzerunterstützung

Bei diesem Ansatz werden Benutzer besonders intensiv unterstützt. Ein Mitglied des IT-Teams begleitet den Benutzer durch den Registrierungsprozess, persönlich oder per Skype. Dieser Ansatz wird häufig bei Führungskräften und anderen Gruppen befolgt, die während des Registrierungsvorgangs ggf. mehr Unterstützung benötigen.

### <a name="it-tech-fair"></a>IT-Hausmesse

Eine weitere Option für die Intune-Benutzerregistrierung besteht in der Veranstaltung einer IT-Hausmesse. Bei dieser Veranstaltung richtet die IT-Gruppe einen Stand zur Unterstützung bei der Intune-Registrierung ein, an dem Benutzer Informationen zur Intune-Registrierung erhalten, Fragen stellen und Unterstützung beim Registrierungsvorgang erhalten können. Diese Option kann sowohl für die IT-Gruppe als auch für den Benutzer von Vorteil sein, insbesondere in den frühen Phasen des Rollouts von Intune.

Hier ist ein mit Registrierungsmethoden aktualisiertes Beispiel des obigen Intune Rolloutplans:

| **Rolloutphase** | **Juli** | **August** | **September** | **Oktober** |
|:---:|:---:|:---:|:---:|:---:|
| Begrenztes Pilotprojekt |  |  |  |  |                                                         
| Self-Service | IT |  |  |  |
| Erweitertes Pilotprojekt |  |  |  |  |                                                         
| Self-Service | IT |  |  |  |
| Intensive Benutzerunterstützung | IT-Führungskräfte |  |  |  |
| Produktionsrolloutphase 1 |  | Vertrieb, Marketing |  |  |
| Self-Service |  | Vertrieb und Marketing |  |  |
| Produktionsrolloutphase 2 |  |  | Einzelhandel |  |
| Self-Service |  |  |  |  |
| Produktionsrolloutphase 3 |  |  | Einzelhandel |  |
| Self-Service |  |  |  | Personalabteilung, Finanzabteilung |
| Intensive Benutzerunterstützung |  |  |  | Führungskräfte |

## <a name="next-steps"></a>Nächste Schritte

Der nächste Abschnitt enthält Hinweise für das [Entwickeln eines Kommunikationsplans für den Intune-Rollout](planning-guide-communication-plan.md).
