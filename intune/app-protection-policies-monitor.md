---
title: Überwachen von App-Schutzrichtlinien
titleSuffix: Microsoft Intune
description: Überwachen Sie den Kompatibilitätsstatus der Verwaltungsrichtlinien für mobile Apps in Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7efa888344b91c74672563730bbdea6c7424214b
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835094"
---
# <a name="how-to-monitor-app-protection-policies"></a>Überwachen von App-Schutzrichtlinien
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Überwachen Sie den Kompatibilitätsstatus der Verwaltungsrichtlinien für mobile Apps (MAM), die Sie auf Benutzer im Bereich „Intune-App-Schutz“ im [Azure-Portal](https://portal.azure.com) angewendet haben. Hier finden Sie Informationen über die Benutzer, die von der MAM-Richtlinie betroffen sind, deren Kompatibilitätsstatus sowie Probleme, die bei den Benutzern möglicherweise auftreten.

Es gibt drei verschiedenen Stellen, an denen der Konformitätsstatus überwacht werden kann:

-   Zusammenfassungsansicht

-   Detailansicht

-   Berichterstellung

> [!NOTE]
> Weitere Informationen zum Erstellen von App-Schutzrichtlinien finden Sie unter [Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md).

## <a name="summary-view"></a>Zusammenfassungsansicht

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** die Option **Client-Apps** aus.
4. Wählen Sie in der Workload **Client-Apps** im Abschnitt **Überwachen** die Option **Status des App-Schutzes** aus, um die Zusammenfassungsansicht anzuzeigen:

![Kachel „Zusammenfassung“ im Bereich „Verwaltung mobiler Anwendungen mit Intune“](./media/app-protection-user-status-summary.png)

-   **Zugewiesene Benutzer:** Die Gesamtzahl von zugewiesenen Benutzern in Ihrem Unternehmen, die eine App verwenden, die einer Richtlinie in einem geschäftlichen Kontext zugeordnet ist, und geschützt und lizenziert sind, sowie die zugewiesenen Benutzer, die nicht geschützt und lizenziert sind.
-   **Gekennzeichnete Benutzer:** Die Anzahl von Benutzern, bei denen Probleme auftreten. Per Jailbreak manipulierte Geräte werden unter **Gekennzeichnete Benutzer** gemeldet.
-   **Benutzerstatus für iOS** und **Benutzerstatus für Android**: Die Anzahl von Benutzern, die eine App verwendet haben und denen eine Richtlinie in einem geschäftlichen Kontext für die entsprechende Plattform zugewiesen ist. Diese Informationen zeigen die Anzahl der von der Richtlinie verwalteten Benutzer sowie die Anzahl der Benutzer an, die eine App verwenden, die von keiner Richtlinie in einem geschäftlichen Kontext erfasst wird. Sie sollten erwägen, diese Benutzer zur Richtlinie hinzuzufügen.

    > [!NOTE]
    > Wenn Sie über mehrere Richtlinien pro Plattform verfügen, gilt ein Benutzer als durch eine Richtlinie verwaltet, wenn ihm mindestens eine Richtlinie zugewiesen ist.

## <a name="detailed-view"></a>Detailansicht
Sie können zur detaillierten Ansicht der Zusammenfassung gelangen, indem Sie auf die Kachel **Benutzerstatus** (basierend auf der Betriebssystemplattform des Geräts) und dann auf die Kachel **Gekennzeichnete Benutzer** klicken.

### <a name="user-status"></a>Benutzerstatus
Sie können nach einem einzelnen Benutzer suchen und den Kompatibilitätsstatus für diesen Benutzer überprüfen. Im Bereich **App-Berichterstellung** werden für einen ausgewählten Benutzer die folgenden Informationen angezeigt:
- Geräte, die dem Benutzerkonto zugeordnet sind

- Apps mit MAM-Richtlinie auf dem Gerät

- Status:

  - **Eingecheckt:** Die Richtlinie wurde für den Benutzer bereitgestellt, und die App wurde mindestens einmal im Arbeitskontext verwendet.

  - **Nicht eingecheckt:** Die Richtlinie wurde für den Benutzer bereitgestellt, die App seitdem aber nicht im Arbeitskontext verwendet.

>[!NOTE]
> Wenn für den gesuchten Benutzer keine MAM-Richtlinie bereitgestellt wurde, wird Ihnen eine Meldung angezeigt, dass auf den Benutzer keine MAM-Richtlinien angewendet werden.

Um die Berichterstattung für einen Benutzer anzuzeigen, gehen Sie folgendermaßen vor:

1.  Wählen Sie die Kachel **Benutzerstatus** aus, um einen Benutzer auszuwählen.

    ![Screenshot der Kachel „Zusammenfassung“ der mobilen Anwendungsverwaltung mit Intune](./media/MAM-reporting-6.png)

2. Wählen Sie im Bereich **App-Berichterstellung**, das geöffnet wird, **Benutzer auswählen**, um nach einem Azure Active Directory-Benutzer zu suchen.

    ![Screenshot der Option „Benutzer auswählen“ im Bereich „App-Berichterstellung“](./media/MAM-reporting-2.png)

3. Wählen Sie den Benutzer in der Liste aus. Es werden Details zum Kompatibilitätsstatus für diesen Benutzer angezeigt.

### <a name="flagged-users"></a>Gekennzeichnete Benutzer
In der Detailansicht werden die Fehlermeldung, die App, auf die bei Auftreten des Fehlers zugegriffen wurde, die betroffene Betriebssystemplattform des Geräts und ein Zeitstempel angezeigt.

## <a name="reporting-view"></a>Berichterstellung

Dieselben Berichte finden Sie auch über das Blatt **Status des App-Schutzes**.

> [!NOTE]
> Intune bietet zusätzliche Felder zur Geräteberichtserstellung, einschließlich Feldern für App-Registrierungs-ID, Android-Hersteller, Modell und Sicherheitspatchversion sowie iOS-Modell. In Intune sind diese Felder unter **Client-Apps** > **Status des App-Schutzes** und **Bericht zum App-Schutz: iOS, Android** verfügbar. Darüber hinaus werden diese Parameter Sie bei der Konfiguration der **Zulassen**-Liste für den Gerätehersteller (Android), der **Zulassen**-Liste für das Gerätemodell (Android und iOS) sowie der Einstellung der mindestens erforderlichen Android-Sicherheitspatchversion unterstützen. 

Als Unterstützung für den Konformitätsstatus der MAM-Richtlinie stehen weitere Berichte zur Verfügung. Wählen Sie zum Anzeigen dieser Berichte **Client-Apps** > **Status des App-Schutzes** > **Berichte** aus. 

Das Blatt **Berichte** bietet mehrere Berichte zu Benutzern und Apps, z.B.:


-   **Benutzerbericht:** Darin werden dieselben Informationen dargestellt, die auch im obigen Abschnitt „Detailansicht“ im Bericht **Benutzerstatus** angezeigt werden.

-   **App-Bericht:** Es werden zwei verschiedene Status zum App-Schutz bereitgestellt, die Administratoren auswählen können, bevor sie den Bericht generieren. Der Status kann geschützt oder nicht geschützt sein.

    -   Benutzerstatus für verwaltete MAM-Aktivität (geschützt): Dieser Bericht veranschaulicht die Aktivität von jeder verwalteten MAM-App pro Benutzer.

        -   Er zeigt alle Apps, die unter MAM-Richtlinien für jeden Benutzer fallen, und schlüsselt den Status jeder App, die unter MAM-Richtlinien eingecheckt sind oder die unter eine MAM-Richtlinie fallen, doch nie eingecheckt waren.
<br><br>
    -   Benutzerstatus für nicht verwaltete MAM-Aktivität (nicht geschützt): Dieser Bericht veranschaulicht pro Benutzer die Aktivitäten von MAM-fähigen Apps, die derzeit nicht verwaltet sind. Dies kann entsprechend der folgenden Gründe auftreten:

        -   Diese Apps werden entweder von einem Benutzer oder von einer App verwendet, die derzeit nicht unter eine MAM-Richtlinie fällt.

        -   Alle Apps sind eingecheckt, erhalten jedoch keine MAM-Richtlinien.

![Screenshot vom Blatt „App-Berichterstellung“ eines Benutzers mit Informationen zu drei Apps](./media/MAM-reporting-4.png)

## <a name="table-grouping"></a>Tabellengruppierung

Sobald die Daten im **Benutzerbericht zum App-Schutz** angezeigt werden, können Sie Daten folgendermaßen aggregieren:

- **Überprüfungsergebnis:** Die Daten werden nach dem App-Schutzstatus (Fehler, Warnung oder Erfolg) gruppiert.
- **App-Name:** Die Daten werden nach Apps (tatsächlicher App-Name) mit Fehlern, Warnungen oder Erfolgen gruppiert.

## <a name="export-app-protection-activities-to-csv"></a>Exportieren von App-Schutzaktivitäten in eine CSV-Datei

Sie können alle Aktivitäten im Zusammenhang mit Ihren App-Schutzrichtlinien in eine CSV-Datei exportieren. Dies kann hilfreich sein, um alle App-Schutzstatus zu analysieren, die von den Benutzern gemeldeten wurden.

Gehen Sie zum Generieren des App-Schutzberichts wie folgt vor:

1. Wählen Sie im Bereich Verwaltung mobiler Anwendungen mit Intune den **App-Schutzbericht** aus.

    ![Screenshot vom Link zum Herunterladen des App-Schutzes](./media/app-protection-report-csv-2.png)

2. Wählen Sie „Ja“ aus, um den Bericht zu speichern, und wählen Sie dann „Speichern unter“ und den Ordner aus, in dem der Bericht gespeichert werden soll.

    ![Screenshot des Dialogfelds „Bericht speichern“ zur Bestätigung](./media/app-protection-report-csv-1.png)

## <a name="see-also"></a>Siehe auch
[Verwalten der Datenübertragung zwischen iOS-Apps](data-transfer-between-apps-manage-ios.md)

* [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](app-protection-enabled-apps-android.md)
* [Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird](app-protection-enabled-apps-ios.md)
