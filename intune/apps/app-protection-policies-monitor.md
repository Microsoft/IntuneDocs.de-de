---
title: Überwachen von App-Schutzrichtlinien
titleSuffix: Microsoft Intune
description: In diesem Thema wird beschrieben, wie Sie App-Schutzrichtlinien in Intune überwachen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9d82813f1292c99cf248c56a102503413d2cb8fb
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507453"
---
# <a name="how-to-monitor-app-protection-policies"></a>Überwachen von App-Schutzrichtlinien
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Sie können den Konformitätsstatus der Verwaltungsrichtlinien für mobile Apps (Mobile App Management, MAM) überwachen, die Sie im Bereich „Intune-Schutz für Apps“ für Benutzer im [Azure-Portal](https://portal.azure.com) angewendet haben. Sie können darüber hinaus Informationen über die Benutzer finden, die von der MAM-Richtlinie betroffen sind, deren Konformitätsstatus sowie Probleme, die bei den Benutzern möglicherweise auftreten.

Es gibt drei verschiedenen Stellen, an denen App-Schutzrichtlinien überwacht werden können:
- Zusammenfassungsansicht
- Detailansicht
- Berichterstellung

> [!NOTE]
> Weitere Informationen finden Sie unter [Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md).

Die Beibehaltungsdauer für den Schutz von App-Daten beträgt 90 Tage. Alle App-Instanzen, die sich in den letzten 90 Tagen beim MAM-Dienst angemeldet haben, werden in den Statusbericht zum App-Schutz aufgenommen. Eine *App-Instanz* besteht aus einer eindeutigen Kombination aus Benutzer, App und Gerät. 

## <a name="summary-view"></a>Zusammenfassungsansicht

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** die Option **Client-Apps** aus.
4. Um die Zusammenfassungsansicht anzuzeigen, wählen Sie in der Workload **Client-Apps** unter **Überwachen** die Option **Status des App-Schutzes** aus.

   ![Screenshot der Zusammenfassungskachel des Bereichs der mobilen Anwendungsverwaltung mit Intune](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Zugewiesene Benutzer:** Die Gesamtzahl von zugewiesenen Benutzern in Ihrem Unternehmen, die eine App verwenden, die einer Richtlinie in einem geschäftlichen Kontext zugeordnet ist, und geschützt und lizenziert sind, sowie die zugewiesenen Benutzer, die nicht geschützt und lizenziert sind.
- **Gekennzeichnete Benutzer:** Die Anzahl von Benutzern, bei deren Geräten Probleme auftreten. Geräte mit Jailbreak (iOS) oder Rooting (Android) werden unter **Gekennzeichnete Benutzer** gemeldet. Hier werden auch Benutzer gemeldet, deren Geräte von der Google-SafetyNet-Überprüfung beim Gerätenachweis gekennzeichnet wurden (wenn diese vom IT-Administrator aktiviert wurde). 
- **Benutzer mit potenziell schädlichen Apps**: Die Anzahl der Benutzer, die eine schädliche App auf ihrem Android-Gerät haben könnten, wird von Google Play Protect erkannt. 
- **Benutzerstatus für iOS** und **Benutzerstatus für Android**: Die Anzahl von Benutzern, die eine App verwendet haben und denen eine Richtlinie in einem geschäftlichen Kontext für die entsprechende Plattform zugewiesen ist. Diese Informationen zeigen die Anzahl der von der Richtlinie verwalteten Benutzer sowie die Anzahl der Benutzer an, die eine App verwenden, die von keiner Richtlinie in einem geschäftlichen Kontext erfasst wird. Sie sollten erwägen, diese Benutzer zur Richtlinie hinzuzufügen.
- **Beliebteste geschützte iOS-Apps:** Auf Grundlage der am meisten verwendeten iOS-Apps wird hier die Anzahl der geschützten und nicht geschützten iOS-Apps angezeigt.
- **Beliebteste geschützte Android-Apps:** Auf Grundlage der am meisten verwendeten Android-Apps wird hier die Anzahl der geschützten und nicht geschützten Android-Apps angezeigt.
- **Meistverwendete konfigurierte iOS-Apps ohne Registrierung:** Auf Grundlage der am meisten verwendeten iOS-Apps für Geräte ohne Registrierung wird hier die Anzahl der konfigurierten iOS-Apps angezeigt.
- **Meistverwendete konfigurierte Android-Apps ohne Registrierung:** Auf Grundlage der am meisten verwendeten Android-Apps für Geräte ohne Registrierung wird hier die Anzahl der konfigurierten Android-Apps angezeigt.

    > [!NOTE]
    > Wenn Sie über mehrere Richtlinien pro Plattform verfügen, gilt ein Benutzer als durch eine Richtlinie verwaltet, wenn ihm mindestens eine Richtlinie zugewiesen ist.

## <a name="detailed-view"></a>Detailansicht
Sie können zur detaillierten Ansicht der Zusammenfassung gelangen, indem Sie die Kachel **Benutzerstatus** (basierend auf der Betriebssystemplattform des Geräts), die Kachel **Benutzer mit potenziell schädlichen Apps** und dann die Kachel **Gekennzeichnete Benutzer** auswählen.

### <a name="user-status"></a>Benutzerstatus
Sie können nach einem einzelnen Benutzer suchen und den Kompatibilitätsstatus für diesen Benutzer überprüfen. Im Bereich **App-Berichterstellung** werden für einen ausgewählten Benutzer die folgenden Informationen angezeigt:
- **Symbol:** Gibt an, ob der App-Status aktuell ist.
- **App-Name:** Der Name der App.
- **Gerätename:** Geräte, die dem Benutzerkonto zugeordnet sind.
- **Gerätetyp:** Der Gerätetyp oder das Betriebssystem des Geräts.
- **Richtlinien:** Die Richtlinien, die der App zugeordnet sind.
- **Status:**
  - **Eingecheckt:** Die Richtlinie wurde für den Benutzer bereitgestellt, und die App wurde mindestens einmal im Arbeitskontext verwendet.
  - **Nicht eingecheckt:** Die Richtlinie wurde für den Benutzer bereitgestellt, die App seitdem aber nicht im Arbeitskontext verwendet.
- **Letzte Synchronisierung:** Zeitpunkt der letzten Synchronisierung der App mit Intune. 

>[!NOTE]
> Die Spalte **Letzte Synchronisierung** stellt sowohl im Benutzerstatusbericht in der Konsole als auch im [exportierbaren CSV-Bericht](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities-to-csv) der App-Schutzrichtlinie den gleichen Wert dar. Der Unterschied besteht in einer kurzen Verzögerung bei der Synchronisierung der Werte in den beiden Berichten. 
>
> Die in „Letzte Synchronisierung“ angegebene Uhrzeit ist der Zeitpunkt, zu dem Intune die App-Instanz zuletzt gesehen hat. Wenn ein Benutzer eine App startet, könnte diese abhängig vom letzten Eincheckzeitpunkt zu diesem Startzeitpunkt mit dem Intune-App-Schutz-Dienst kommunizieren. Informieren Sie sich über [die Wiederholungsintervallzeiten für den Eincheckvorgang der App-Schutzrichtlinie](https://docs.microsoft.com/en-us/intune/app-protection-policy-delivery). Wenn ein Benutzer diese spezielle App also im letzten Eincheckintervall (in der Regel 30 Minuten für die aktive Verwendung) nicht verwendet hat und die App gestartet wird, dann gilt Folgendes:
>
> - Der exportierbare CSV-Bericht der App-Schutzrichtlinie hat im Rahmen von 1 Minute (mindestens) bis 30 Minuten (Maximum) die neueste Zeit.
> - Der Benutzerstatusbericht erhält sofort die neueste Zeit.
>
> Betrachten Sie z. B. einen lizenzierten Zielendbenutzer, der eine geschützte App um 12:00 Uhr startet:
> - Wenn dies eine erste Anmeldung ist, bedeutet das, dass der Benutzer zuvor abgemeldet wurde und über keine App-Instanzregistrierung bei Intune verfügt. Nachdem sich der Benutzer angemeldet hat, erhält er eine neue App-Instanzregistrierung und kann sofort eingecheckt werden (mit denselben Zeitverzögerungen, die zuvor für künftige Eincheckvorgänge aufgelistet wurden). Daher lautet die Uhrzeit der letzten Synchronisierung im Benutzerstatusbericht „12:00 Uhr“ und im Bericht der App-Schutzrichtlinie „12:01 Uhr“ (oder spätestens „12:30 Uhr“). 
> - Wenn der Benutzer die App gerade startet, hängt die Uhrzeit der letzten Synchronisierung im Bericht vom letzten Eincheckzeitpunkt des Benutzers ab.


Um die Berichterstattung für einen Benutzer anzuzeigen, gehen Sie folgendermaßen vor:

1. Wählen Sie die Kachel **Benutzerstatus** aus, um einen Benutzer auszuwählen.

    ![Screenshot der Kachel „Zusammenfassung“ der mobilen Anwendungsverwaltung mit Intune](./media/app-protection-policies-monitor/MAM-reporting-6.png)

2. Wählen Sie im Bereich **App-Berichterstellung** die Option **Benutzer auswählen** aus, um nach einem Azure Active Directory-Benutzer zu suchen.

    ![Screenshot der Option „Benutzer auswählen“ im Bereich „App-Berichterstellung“](./media/app-protection-policies-monitor/MAM-reporting-2.png)

3. Wählen Sie den Benutzer in der Liste aus. Es werden Details zum Kompatibilitätsstatus für diesen Benutzer angezeigt.

>[!NOTE]
> Wenn für den gesuchten Benutzer keine MAM-Richtlinie bereitgestellt wurde, wird Ihnen eine Meldung angezeigt, dass auf den Benutzer keine MAM-Richtlinien angewendet werden.

### <a name="flagged-users"></a>Gekennzeichnete Benutzer
In der Detailansicht werden die Fehlermeldung, die App, auf die bei Auftreten des Fehlers zugegriffen wurde, die betroffene Betriebssystemplattform des Geräts und ein Zeitstempel angezeigt. Der Fehler tritt in der Regel bei Geräten mit Jailbreak (iOS) oder Rootzugriff (Android) auf. Hier werden auch Benutzer gemeldet, deren Geräte bei der bedingten Startüberprüfung vom „SafetyNet-Gerätenachweis“ gekennzeichnet wurden. Außerdem werden die von Google angegebenen Gründe aufgeführt. Damit ein Benutzer aus dem Bericht entfernt werden kann, muss der Status des Geräts selbst geändert werden. Dies geschieht nach der nächsten Stammerkennungsüberprüfung (bzw. Jailbreak-/SafetyNet-Überprüfung), die ein positives Ergebnis melden muss. Wenn das Gerät tatsächlich wiederhergestellt wird, wird die Aktualisierung des Berichts über gekennzeichnete Benutzer durchgeführt, wenn das Blatt erneut geladen wird.

### <a name="users-with-potentially-harmful-apps"></a>Benutzer mit potenziell schädlichen Apps
Die ausführliche Ansicht zeigt Folgendes:

- Den Benutzer.
- Die App-Paket-ID.
- Ob die App MAM-aktiviert ist.
- Die Bedrohungskategorie.
- Die E-Mail.
- Den Gerätenamen.
- Einen Zeitstempel.

Hier werden Benutzer gemeldet, deren Geräte bei der bedingten Startüberprüfung mit **Bedrohungsüberprüfung für Apps erzwingen** gekennzeichnet wurden. Außerdem werden die von Google angegebenen Bedrohungskategorien aufgeführt. Wenn in diesem Bericht Apps aufgeführt sind, die über Intune bereitgestellt werden, wenden Sie sich bezüglich der App an den App-Entwickler, oder entfernen Sie die App aus der Zuweisung an Ihre Benutzer. 

## <a name="reporting-view"></a>Berichterstellung

Dieselben Berichte finden Sie auch oben auf dem Blatt **Status des App-Schutzes**.

> [!NOTE]
> Intune bietet zusätzliche Felder zur Geräteberichtserstellung, einschließlich Feldern für App-Registrierungs-ID, Android-Hersteller, Modell und Sicherheitspatchversion sowie iOS-Modell. In Intune greifen Sie auf diese Felder durch Auswahl von **Client-Apps** > **Status des App-Schutzes** > **Bericht zum App-Schutz: iOS, Android** zu. Darüber hinaus werden diese Parameter Sie bei der Konfiguration der **Zulassen**-Liste für den Gerätehersteller (Android), der **Zulassen**-Liste für das Gerätemodell (Android und iOS) sowie der Einstellung der mindestens erforderlichen Android-Sicherheitspatchversion unterstützen. 

Als Unterstützung für den Konformitätsstatus der MAM-Richtlinie stehen weitere Berichte zur Verfügung. Wählen Sie zum Anzeigen dieser Berichte **Client-Apps** > **Status des App-Schutzes** > **Berichte** aus. 

Das Blatt **Berichte** bietet mehrere Berichte zu Benutzern und Apps, z.B.:

- **Benutzerbericht:** Darin werden dieselben Informationen dargestellt, die auch im obigen Abschnitt [Detailansicht](app-protection-policies-monitor.md#detailed-view) im Bericht **Benutzerstatus** angezeigt werden.

- **App-Bericht:** Neben der Auswahl der Plattform und App werden zwei verschiedene Status zum App-Schutz bereitgestellt, die Sie auswählen können, bevor Sie den Bericht generieren. Der Status kann **Protected** (Geschützt) oder **Unprotected** (Nicht geschützt) sein.

  - Benutzerstatus für verwaltete MAM-Aktivität (**Protected** (Geschützt)): Dieser Bericht veranschaulicht die Aktivität jeder verwalteten MAM-App pro Benutzer. Er zeigt alle Apps an, die auf MAM-Richtlinien für jeden Benutzer abzielen, und den Status jeder App, die mit MAM-Richtlinien eingecheckt wird. Der Bericht enthält auch den Status jeder App, die auf eine MAM-Richtlinie ausgerichtet, jedoch nie eingecheckt wurde.
  - Benutzerstatus für verwaltete MAM-Aktivität (**Unprotected** (Nicht geschützt)): Dieser Bericht veranschaulicht je Benutzer die Aktivitäten von MAM-fähigen Apps, die derzeit nicht verwaltet werden. Dies kann folgende Ursache haben:
    - Diese Apps werden entweder von einem Benutzer oder von einer App verwendet, der bzw. die derzeit nicht unter eine MAM-Richtlinie fällt.
    - Alle Apps sind eingecheckt, erhalten jedoch keine MAM-Richtlinien.

    ![Screenshot vom Blatt „App-Berichterstellung“ eines Benutzers mit Informationen zu drei Apps](./media/app-protection-policies-monitor/MAM-reporting-4.png)

- **Benutzerkonfigurationsbericht:** Abhängig vom ausgewählten Benutzer enthält dieser Bericht Details zu App-Konfigurationen, die der Benutzer erhalten hat.
- **Bericht zur App-Konfiguration:** Abhängig von der ausgewählten Plattform und App enthält dieser Bericht Details zu den Benutzern, die Konfigurationen für die ausgewählte App erhalten haben.
- **Bericht zum App-Learning für Windows Information Protection:** In diesem Bericht wird angegeben, welche Apps versuchen, App-Grenzen zu überschreiten.
- **Website-Learning für Windows Information Protection:** In diesem Bericht wird angegeben, welche Websites versuchen, App-Grenzen zu überschreiten.

## <a name="table-grouping"></a>Tabellengruppierung

Sobald die Daten im **Benutzerbericht zum App-Schutz** angezeigt werden, können Sie Daten folgendermaßen aggregieren:

- **Überprüfungsergebnis**: Die Daten werden nach dem App-Schutzstatus („Fehler“, „Warnung“ oder „Erfolg“) gruppiert.
- **App-Name:** Die Daten werden nach dem tatsächlichen App-Namen gruppiert. Auch hier kann der Status „Fehler“, „Warnung“ oder „Erfolg“ lauten.

## <a name="export-app-protection-activities"></a>Exportieren von App-Schutzaktivitäten

Sie können alle Aktivitäten im Zusammenhang mit Ihren App-Schutzrichtlinien in eine CSV-Datei exportieren. Dies kann hilfreich sein, um alle App-Schutzstatus zu analysieren, die von den Benutzern gemeldeten wurden.

Gehen Sie zum Generieren des App-Schutzberichts wie folgt vor:

1. Wählen Sie im Bereich Verwaltung mobiler Anwendungen mit Intune den **App-Schutzbericht** aus.

    ![Screenshot vom Link zum Herunterladen des App-Schutzes](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Wählen Sie **Ja**, um den Bericht zu speichern, und dann **Speichern unter** aus. Wählen Sie den Ordner zum Speichern des Berichts aus.

    ![Screenshot des Dialogfelds „Bericht speichern“ zur Bestätigung](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)

## <a name="see-also"></a>Siehe auch
- [Verwalten der Datenübertragung zwischen iOS-Apps](data-transfer-between-apps-manage-ios.md)
- [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](../fundamentals/end-user-mam-apps-android.md)
- [Was Sie erwartet, wenn Ihre iOS-App von App-Schutzrichtlinien verwaltet wird](../fundamentals/end-user-mam-apps-ios.md)
