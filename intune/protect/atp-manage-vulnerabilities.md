---
title: Verwenden von Intune zum Korrigieren von mit Microsoft Defender ATP aufgefundenen Sicherheitsrisiken – Azure | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Sicherheitsaufgaben aus der Bedrohungs- und Sicherheitsrisikenverwaltung heraus verwalten, einem Teil von Microsoft Defender Advanced Threat Protection (ATP) in der Intune-Konsole.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a9529f5b3047a8d4ca2a1e9c22d2c4427761078c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73754900"
---
# <a name="use-intune-to-remediate-vulnerabilities-identified-by-microsoft-defender-atp"></a>Verwenden von Intune zum Korrigieren von mit Microsoft Defender ATP identifizierten Sicherheitsrisiken

Wenn Sie Intune mit Microsoft Defender Advanced Threat Protection (ATP) integrieren, können Sie die Bedrohungs- und Sicherheitsrisikenverwaltung von ATP (Thread & Vulnerability Management, TVM) nutzen und Intune verwenden, um mittels TVM identifizierte Schwachstellen von Endpunkten zu beheben. Diese Integration bietet einen risikobasierten Ansatz für die Ermittlung und Priorisierung von Sicherheitsrisiken, der die Korrekturreaktionszeiten in Ihrer gesamten Umgebung verbessern kann.

[Bedrohungs- und Sicherheitsrisikenverwaltung](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/next-gen-threat-and-vuln-mgt) ist Teil von [Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection).

## <a name="how-integration-works"></a>Funktionsweise der Integration

Nachdem Sie Intune mit Microsoft Defender Advanced Threat Protection verbunden haben, empfängt ATP Details zu Bedrohungen und Sicherheitsrisiken Informationen von verwalteten Geräten.

In der Microsoft Defender Security Center-Konsole überprüfen ATP-Sicherheitsadministratoren Daten auf Sicherheitsrisiken bei Endpunkten. Die Administratoren erstellen dann mit einem einzigen Klick Sicherheitsaufgaben, mit denen die anfälligen Geräte für die Korrektur gekennzeichnet werden. Die Sicherheitsaufgaben werden sofort an die Intune-Konsole übergeben, wo Intune-Administratoren diese anzeigen können. Die Sicherheitsaufgabe identifiziert den Typ des Sicherheitsrisikos, seine Priorität, den Status und die zu unternehmenden Schritte, um das Sicherheitsrisiko zu beheben. Der Intune-Administrator entscheidet, ob die Aufgabe akzeptiert oder abgelehnt wird.

Wenn eine Aufgabe akzeptiert wird, ergreift der Intune-Administrator Maßnahmen, um das Sicherheitsrisiko mittels Intune zu beheben, wobei er die Anleitung nutzt, die als Teil der Sicherheitsaufgabe bereitgestellt wird.

Gängige Korrekturmaßnahmen umfassen:

- **Blockieren** der Ausführung einer Anwendung.
- **Bereitstellen** eines Betriebssystemupdates, um das Sicherheitsrisiko zu mindern.
- **Ändern** eines Registrierungswerts.
- **Deaktivieren** oder **Aktivieren** einer Konfiguration, um das Sicherheitsrisiko zu beeinflussen.
- **Eingreifen erforderlich**-Benachrichtigungen an den Administrator wegen der Bedrohung, wenn keine geeignete Empfehlung bereitgestellt werden kann.

Ein Beispielworkflow:

- In Microsoft Defender ATP wird ein Sicherheitsrisiko für eine App namens „Contoso Media Player v4“ entdeckt, und ein Administrator erstellt eine Sicherheitsaufgabe, um diese App zu aktualisieren. Der Contoso Media Player ist eine nicht verwaltete App, die mit Intune bereitgestellt wurde.

  Diese Sicherheitsaufgabe wird in der Intune-Konsole mit dem Status „Ausstehend“ angezeigt:

  ![Anzeigen der Liste mit Sicherheitsaufgaben in der Intune-Konsole](./media/atp-manage-vulnerabilities/temp-security-tasks.png)

- Der Intune-Administrator wählt die Sicherheitsaufgabe aus, um Details zur Aufgabe anzuzeigen.  Dann wählt der Administrator **Akzeptieren** aus, wodurch der Status in Intune und in ATP auf *Akzeptiert* aktualisiert wird.

  ![Akzeptieren oder Ablehnen einer Sicherheitsaufgabe](./media/atp-manage-vulnerabilities/temp-accept-task.png)

- Der Administrator korrigiert dann die Aufgabe gemäß der bereitgestellten Anleitung. Die Anleitung variiert je nach Art der erforderlichen Korrektur. Sofern verfügbar, enthält eine Anleitung für Abhilfemaßnahmen Links, über die relevante Bereiche für Konfigurationen in Intune geöffnet werden.

  Da der Media Player in diesem Beispiel keine verwaltete App ist, kann Intune nur Textanweisungen bereitstellen. Wenn die App verwaltet wäre, könnte Intune Anweisungen zum Herunterladen einer aktualisierten Version bereitstellen sowie einen Link, um die Bereitstellung für die App zu öffnen, damit die aktualisierten Dateien der Bereitstellung hinzugefügt werden können.

- Nach Abschluss der Korrektur öffnet der Intune-Administrator die Sicherheitsaufgabe, und wählt **Aufgabe abschließen** aus.  Der Korrekturstatus wird für Intune und in ATP aktualisiert, wo Sicherheitsadministratoren den überarbeiteten Status für das Sicherheitsrisiko bestätigen.

## <a name="prerequisites"></a>Voraussetzungen  

**Abonnements**:

- Microsoft Intune  
- Microsoft Defender Advanced Threat Protection ([Für eine kostenlose Testversion registrieren](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-main-abovefoldlink).)

**Intune-Konfigurationen für ATP**:

- Konfigurieren Sie eine Dienst-zu-Dienst-Verbindung mit Microsoft Defender ATP.
- Stellen Sie eine Richtlinie für die Gerätekonfiguration mit dem Profiltyp **Microsoft Defender ATP (Windows 10 Desktop)** auf Geräten bereit, deren Risiken von ATP bewertet werden.

  Informationen zum Einrichten von Intune für die Zusammenarbeit mit ATP finden Sie unter [Erzwingen der Konformität für Windows Defender ATM mit bedingtem Zugriff in Intune](advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune).

## <a name="work-with-security-tasks"></a>Arbeiten mit Sicherheitsaufgaben

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Endpunktsicherheit** > **Sicherheitsaufgaben** aus.

3. Wählen Sie eine Aufgabe aus der Liste aus, um ein Ressourcenfenster zu öffnen, in dem weitere Details für diese Sicherheitsaufgabe angezeigt werden.

   Während Sie das Ressourcenfenster für die Sicherheitsaufgabe anzeigen, können Sie zusätzliche Links auswählen:

   - VERWALTETE APPS: Anzeigen der anfälligen App. Wenn das Sicherheitsrisiko für mehrere Apps gilt, wird eine gefilterte Liste von Apps angezeigt.
   - GERÄTE: Anzeigen einer Liste *Anfälliger Geräte*, über die Sie mittels Links zu einem Eintrag mit weiteren Details zu der Sicherheitslücke auf dem Gerät wechseln können.
   - ANFORDERER: Verwenden Sie den Link zum Senden einer E-Mail an den Administrator, der diese Sicherheitsaufgabe übermittelt hat.
   - HINWEISE: Lesen benutzerdefinierter Nachrichten, die vom Anforderer übermittelt werden, wenn Sie die Sicherheitsaufgabe öffnen.

4. Wählen Sie **Akzeptieren** oder **Ablehnen** aus, um eine Benachrichtigung an ATP über Ihre geplante Aktion zu senden. Wenn Sie eine Aufgabe akzeptieren oder ablehnen, können Sie Hinweise übermitteln, die an ATP gesendet werden.

5. Öffnen Sie nach dem Akzeptieren einer Aufgabe die Sicherheitsaufgabe erneut (wenn sie geschlossen wurde), und befolgen Sie die WARTUNG-Details, um das Sicherheitsrisiko zu beheben. Die von ATP in den Details der Sicherheitsaufgabe bereitgestellten Anleitungen hängen von dem beteiligten Sicherheitsrisiko ab.

   Nach Möglichkeit enthalten die Korrekturanweisungen Links, die die relevanten Konfigurationsobjekte in der Intune-Konsole öffnen.

6. Nach Abschluss der Korrekturschritte öffnen Sie die Sicherheitsaufgabe, und wählen Sie **Aufgabe abschließen** aus.  Diese Aktion aktualisiert den Status der Sicherheitsaufgabe in Intune und ATP.

Nach erfolgreicher Korrektur kann die Bewertung des Gefahrenpotenzials durch Risiken in ATP sinken, basierend auf neuen Informationen von den korrigierten Geräten.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu Intune und [Microsoft Defender ATP](advanced-threat-protection.md).

Lesen Sie Intune [Mobile Threat Defense](mobile-threat-defense.md).

Schauen Sie sich das [Dashboard für die Bedrohungs- und Sicherheitsrisikenverwaltung](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/tvm-dashboard-insights) in Microsoft Defender ATP an.
