---
title: Überwachen von MAM-Richtlinien mit Microsoft Intune
description: Finden Sie heraus, für wie viele Benutzer die Richtlinie gilt, und zeigen Sie weitere Details an.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: de26b7614578b275802ca048ed17bfa5969f0387
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="monitor-app-protection-policies-with-microsoft-intune"></a>Überprüfen von App-Schutzrichtlinien mit Microsoft Intune
Sie können den Konformitätsstatus der App-Schutzrichtlinien überwachen, die Sie auf Benutzer angewendet haben. Sie können Informationen über die Benutzer finden, die von den App-Schutzrichtlinien betroffen sind, deren Konformitätsstatus sowie Probleme, die bei den Benutzern möglicherweise auftreten.

Es gibt drei verschiedenen Stellen, an denen der Konformitätsstatus überwacht werden kann:

-   Zusammenfassungsansicht

-   Detailansicht

-   Berichterstellung

## <a name="summary-view"></a>Zusammenfassungsansicht

Führen Sie die folgenden drei Schritte aus,um die Ansicht „Zusammenfassung“ zu öffnen:

1. Navigieren Sie zum [Azure-Portal](https://portal.azure.com), und geben Sie Ihre-Anmeldeinformationen ein.
2. Wählen Sie **Weitere Dienste** aus, und geben Sie in das Filtertextfeld **Intune** ein.
3. Wählen Sie **Intune-Schutz für Apps** aus.

Auf dem Blatt **Mobile Anwendungsverwaltung mit Intune** sehen Sie eine Zusammenfassung des Kompatibilitätsstatus:

![Kachel „Zusammenfassung“ auf dem Blatt „Mobile Anwendungsverwaltung mit Intune“](../media/mam-azure-portal-user-status-summary.png)

-   **Benutzer:** Die Gesamtzahl von Benutzern in Ihrem Unternehmen, die die eine App verwenden, die einer Richtlinie in einem geschäftlichen Kontext zugeordnet ist.

-   **VERWALTET DURCH RICHTLINIE**: Die Anzahl von Benutzern, die eine App verwendet haben und denen eine Richtlinie in einem geschäftlichen Kontext zugeordnet ist.

-   **KEINE RICHTLINIE**: Die Anzahl von Benutzern, die eine App verwenden, die unter keine Richtlinie in einem geschäftlichen Kontext fallen. Sie sollten erwägen, diese Benutzer zur Richtlinie hinzuzufügen.
    > [!NOTE]
    > Wenn Sie über mehrere Richtlinien pro Plattform verfügen, gilt ein Benutzer als durch eine Richtlinie verwaltet, wenn ihm mindestens eine Richtlinie zugewiesen ist.

- **Gekennzeichnete Benutzer:** Die Anzahl von Benutzern, die Probleme feststellen. Derzeit werden nur Benutzer mit per Jailbreak manipulierten Geräten unter **Gekennzeichnete Benutzer** gemeldet.


## <a name="detailed-view"></a>Detailansicht
Sie können zur detaillierten Ansicht der Zusammenfassung gelangen, indem Sie auf die Kachel **Benutzerstatus** (basierend auf der Betriebssystemplattform des Geräts) und dann auf die Kachel **Gekennzeichnete Benutzer** klicken.

### <a name="user-status"></a>Benutzerstatus
Sie können nach einem einzelnen Benutzer suchen und den Kompatibilitätsstatus für diesen Benutzer überprüfen. Auf dem Blatt **App-Berichterstellung** werden für einen ausgewählten Benutzer die folgenden Informationen angezeigt:
- Geräte, die dem Benutzerkonto zugeordnet sind

- Apps mit einer App-Schutzrichtlinie auf dem Gerät

- Status:

  - **Eingecheckt:** Die Richtlinie wurde für den Benutzer bereitgestellt, und die App wurde mindestens einmal im Arbeitskontext verwendet.

  - **Nicht eingecheckt:** Die Richtlinie wurde für den Benutzer bereitgestellt, die App seitdem aber nicht im Arbeitskontext verwendet.

>[!NOTE]
> Wenn für den gesuchten Benutzer keine App-Schutzrichtlinie bereitgestellt wurde, wird Ihnen eine Meldung angezeigt, dass auf den Benutzer keine App-Schutzrichtlinien angewendet werden.

Um die Berichterstattung für einen Benutzer anzuzeigen, gehen Sie folgendermaßen vor:

1.  Wählen Sie die Kachel **Zusammenfassung** aus, um einen Benutzer auszuwählen.

    ![Screenshot 3](../media/MAM-reporting-6.png)

2. Wählen Sie auf dem Blatt **App-Berichterstellung**, das geöffnet wird, **Benutzer auswählen**, um nach einem Azure Active Directory-Benutzer zu suchen.

    ![Option „Benutzer auswählen“ auf dem Blatt „App-Berichterstellung“](../media/MAM-reporting-2.png)

3. Wählen Sie den Benutzer in der Liste aus. Es werden Details zum Kompatibilitätsstatus für diesen Benutzer angezeigt.

### <a name="flagged-users"></a>Gekennzeichnete Benutzer
In der Detailansicht werden die Fehlermeldung, die App, auf die bei Auftreten des Fehlers zugegriffen wurde, die betroffene Betriebssystemplattform des Geräts und ein Zeitstempel angezeigt.

## <a name="reporting-view"></a>Berichterstellung

Sie können die gleichen Berichte in der Detailansicht finden sowie zusätzliche Berichte, die Ihnen mit dem Konformitätsstatus der App-Schutzrichtlinie weiterhelfen:

![Screenshot 4](../media/MAM-reporting-7.png)

-   **App protection user report** (Benutzerbericht App-Schutz): Darin werden dieselben Informationen dargestellt, die Sie auch im **Benutzerstatus**-Bericht im Abschnitt „Detailansicht“ weiter hoben sehen können.

-   **App protection app report** (App-Bericht App-Schutz): Es werden zwei verschiedene Status zum App-Schutz bereitgestellt, die Administratoren auswählen können, bevor sie den Bericht generieren. Der Status kann geschützt oder nicht geschützt sein.

    -   Benutzerstatus für verwaltete MAM-Aktivität (Geschützt): Dieser Bericht zeigt die Aktivität von jeder verwalteten MAM-App auf Benutzerebene.

        -   Er zeigt alle Apps, die unter App-Schutzrichtlinien für jeden Benutzer fallen, und schlüsselt den Status jeder App auf, die unter den App-Schutzrichtlinien eingecheckt sind oder die unter eine App-Schutzrichtlinie fallen, doch nie eingecheckt waren.
<br></br>
    -   Benutzerstatus für nicht verwaltete MAM-Aktivität (nicht geschützt): Dieser Bericht beschreibt die Aktivitäten auf Benutzerbasis von mit MAM aktivierten Apps, die derzeit nicht verwaltet sind. Dies kann entsprechend der folgenden Gründe auftreten:

        -   Diese Apps werden entweder von einem Benutzer oder einer App verwendet, die derzeit nicht unter eine App-Schutzrichtlinie fällt.

        -   Alle Apps sind eingecheckt, erhalten jedoch keine App-Schutzrichtlinien.

![Screenshot 2](../media/MAM-reporting-4.png)

## <a name="table-grouping"></a>Tabellengruppierung

Sobald die Daten im **Benutzerbericht zum App-Schutz** angezeigt werden, können Sie Daten folgendermaßen aggregieren:

- **Überprüfungsergebnis:** Die Daten werden nach dem App-Schutzstatus – Fehler, Warnung oder Erfolg – gruppiert.
- **App-Name:** Die Daten werden nach Apps (tatsächlicher App-Name) mit Fehlern, Warnungen oder Erfolgen gruppiert.

## <a name="export-app-protection-activities-to-csv"></a>Exportieren von App-Schutzaktivitäten in eine CSV-Datei

Sie können alle Aktivitäten im Zusammenhang mit Ihren App-Schutzrichtlinien in eine CSV-Datei exportieren. Dies kann hilfreich sein, um alle App-Schutzstatus zu analysieren, die von den Benutzern gemeldeten wurden.

Gehen Sie zum Generieren des App-Schutzberichts wie folgt vor:

1. Wählen Sie auf dem Blatt „Mobile Anwendungsverwaltung mit Intune“ den App-Schutzbericht aus.

    ![Screenshot 6](../media/app-protection-report-csv-2.png)

2. Wählen Sie „Ja“ aus, um den Bericht zu speichern, und wählen Sie dann „Speichern unter“ und den Ordner aus, in dem der Bericht gespeichert werden soll.

    ![Screenshot 7](../media/app-protection-report-csv-1.png)

## <a name="see-also"></a>Siehe auch
[Verwalten der Datenübertragung zwischen iOS-Apps](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

* [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](/intune/end-user-mam-apps-android)
* [Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird](/intune/end-user-mam-apps-ios)
