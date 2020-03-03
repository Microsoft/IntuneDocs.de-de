---
title: Überwachen von App-Schutzrichtlinien
titleSuffix: Microsoft Intune
description: In diesem Thema wird beschrieben, wie Sie App-Schutzrichtlinien in Intune überwachen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/13/2019
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
ms.openlocfilehash: 317f39b28909196d03ef5e7c68c7980f5fdfea3f
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512210"
---
# <a name="how-to-monitor-app-protection-policies"></a>Überwachen von App-Schutzrichtlinien
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Sie können den Status der App-Schutzrichtlinien überwachen, die Sie im Bereich „Intune-App-Schutz“ für Benutzer im [Azure-Portal](https://portal.azure.com) angewendet haben. Darüber hinaus finden Sie hier Informationen über die Benutzer, die von den App-Schutzrichtlinien betroffenen sind, deren Konformitätsstatus sowie Probleme, die möglicherweise bei den Benutzern auftreten.

Es gibt drei verschiedenen Stellen, an denen App-Schutzrichtlinien überwacht werden können:
- Zusammenfassungsansicht
- Detailansicht
- Berichterstellung

Die Beibehaltungsdauer für den Schutz von App-Daten beträgt 90 Tage. Alle App-Instanzen, die sich in den letzten 90 Tagen beim Intune-Dienst eingecheckt haben, werden in den Statusbericht zum App-Schutz aufgenommen. Eine *App-Instanz* besteht aus einer eindeutigen Kombination aus Benutzer, App und Gerät. 

> [!NOTE]
> Weitere Informationen finden Sie unter [Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md).

## <a name="summary-view"></a>Zusammenfassungsansicht

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
3. Wählen Sie **Apps** > **Überwachen** > **Status des App-Schutzes** aus.

   ![Screenshot der Zusammenfassungskachel des Bereichs der mobilen Anwendungsverwaltung mit Intune](./media/app-protection-policies-monitor/app-protection-user-status-summary.png)

- **Zugewiesene Benutzer:** Die Gesamtzahl von zugewiesenen Benutzern in Ihrem Unternehmen, die eine App verwenden, die einer Richtlinie in einem geschäftlichen Kontext zugeordnet ist, und geschützt und lizenziert sind, sowie die zugewiesenen Benutzer, die nicht geschützt und lizenziert sind.
- **Gekennzeichnete Benutzer:** Die Anzahl von Benutzern, bei deren Geräten Probleme auftreten. Geräte mit Jailbreak (iOS/iPadOS) oder Rootzugriff (Android) werden unter **Gekennzeichnete Benutzer** gemeldet. Hier werden auch Benutzer gemeldet, deren Geräte von der Google-SafetyNet-Überprüfung beim Gerätenachweis gekennzeichnet wurden (wenn diese vom IT-Administrator aktiviert wurde). 
- **Benutzer mit potenziell schädlichen Apps**: Die Anzahl der Benutzer, die eine schädliche App auf ihrem Android-Gerät haben könnten, wird von Google Play Protect erkannt. 
- **Benutzerstatus für iOS** und **Benutzerstatus für Android**: Die Anzahl von Benutzern, die eine App verwendet haben und denen eine Richtlinie in einem geschäftlichen Kontext für die entsprechende Plattform zugewiesen ist. Diese Informationen zeigen die Anzahl der von der Richtlinie verwalteten Benutzer sowie die Anzahl der Benutzer an, die eine App verwenden, die von keiner Richtlinie in einem geschäftlichen Kontext erfasst wird. Sie sollten erwägen, diese Benutzer zur Richtlinie hinzuzufügen.
- **Beliebteste geschützte iOS-/iPadOS-Apps** und **Beliebteste geschützte Android-Apps**: Auf Grundlage der am meisten verwendeten iOS-/iPadOS- und Android-Apps wird hier die Anzahl von geschützten und nicht geschützten Apps nach Plattform angezeigt.
- **Meistverwendete konfigurierte iOS-/iPadOS-Apps ohne Registrierung** und **Meistverwendete konfigurierte Android-Apps ohne Registrierung**: Auf Grundlage der am meisten verwendeten iOS-/iPadOS- und Android-Apps für Geräte ohne Registrierung wird hier die Anzahl von konfigurierten Apps nach Plattform angezeigt (wie bei Verwendung einer App-Konfigurationsrichtlinie).

    > [!NOTE]
    > Wenn Sie über mehrere Richtlinien pro Plattform verfügen, gilt ein Benutzer als durch eine Richtlinie verwaltet, wenn ihm mindestens eine Richtlinie zugewiesen ist.

## <a name="detailed-view"></a>Detailansicht
Sie gelangen zu einer detaillierten Ansicht der Zusammenfassung, indem Sie auf die Kachel **Gekennzeichnete Benutzer** und dann auf die Kachel **Benutzer mit potenziell schädlichen Apps** klicken.

### <a name="flagged-users"></a>Gekennzeichnete Benutzer
In der Detailansicht werden die Fehlermeldung, die App, auf die bei Auftreten des Fehlers zugegriffen wurde, die betroffene Betriebssystemplattform des Geräts und ein Zeitstempel angezeigt. Der Fehler tritt in der Regel bei Geräten mit Jailbreak (iOS/iPadOS) oder Rootzugriff (Android) auf. Hier werden auch Benutzer gemeldet, deren Geräte bei der bedingten Startüberprüfung vom „SafetyNet-Gerätenachweis“ gekennzeichnet wurden. Außerdem werden die von Google angegebenen Gründe aufgeführt. Damit ein Benutzer aus dem Bericht entfernt werden kann, muss der Status des Geräts selbst geändert werden. Dies geschieht nach der nächsten Stammerkennungsüberprüfung (bzw. Jailbreak-/SafetyNet-Überprüfung), die ein positives Ergebnis melden muss. Wenn das Gerät tatsächlich wiederhergestellt wird, wird die Aktualisierung des Berichts über gekennzeichnete Benutzer durchgeführt, wenn der Bereich erneut geladen wird.

### <a name="users-with-potentially-harmful-apps"></a>Benutzer mit potenziell schädlichen Apps
Hier werden Benutzer gemeldet, deren Geräte bei der bedingten Startüberprüfung mit **Bedrohungsüberprüfung für Apps erzwingen** gekennzeichnet wurden. Außerdem werden die von Google angegebenen Bedrohungskategorien aufgeführt. Wenn in diesem Bericht Apps aufgeführt sind, die über Intune bereitgestellt werden, wenden Sie sich bezüglich der App an den App-Entwickler, oder entfernen Sie die App aus der Zuweisung an Ihre Benutzer. Die ausführliche Ansicht zeigt Folgendes:

- **Benutzer:** Der Name des Benutzers.
- **App-Paket-ID**: Hiermit wird eine App gegenüber dem Android-Betriebssystem eindeutig gekennzeichnet.
- **App ist MAM-fähig**: Gibt an, ob die App über Microsoft Intune bereitgestellt wird oder nicht. 
- **Bedrohungskategorie**: Gibt an, unter welche von Google bestimmte Bedrohungskategorie diese App fällt. 
- **E-Mail:** Die E-Mail-Adresse des Benutzers.
- **Gerätename:** Die Namen von Geräten, die dem Benutzerkonto zugeordnet sind.
- **Zeitstempel**: Dies ist das Datum der letzten Synchronisierung, die Google mit Microsoft Intune bezüglich potenziell schädlicher Apps durchgeführt hat.

## <a name="reporting-view"></a>Berichterstellung

Dieselben Berichte finden Sie auch oben im Bereich **Status des App-Schutzes**. Wählen Sie zum Anzeigen dieser Berichte **Apps** > **Status des App-Schutzes** > **Berichte** aus. Der Bereich **Berichte** bietet mehrere Berichte zu Benutzern und Apps, z.B.:

### <a name="user-report"></a>Benutzerbericht
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
> Die Spalte **Letzte Synchronisierung** stellt sowohl im Benutzerstatusbericht in der Konsole als auch im [exportierbaren CSV-Bericht](https://docs.microsoft.com/intune/app-protection-policies-monitor#export-app-protection-activities) der App-Schutzrichtlinie den gleichen Wert dar. Der Unterschied besteht in einer kurzen Verzögerung bei der Synchronisierung der Werte in den beiden Berichten. 
>
> Die in „Letzte Synchronisierung“ angegebene Uhrzeit ist der Zeitpunkt, zu dem Intune die App-Instanz zuletzt gesehen hat. Wenn ein Benutzer eine App startet, könnte diese abhängig vom letzten Eincheckzeitpunkt zu diesem Startzeitpunkt mit dem Intune-App-Schutz-Dienst kommunizieren. Informieren Sie sich über [die Wiederholungsintervallzeiten für den Eincheckvorgang der App-Schutzrichtlinie](~/apps/app-protection-policy-delivery.md). Wenn ein Benutzer diese spezielle App also im letzten Eincheckintervall (in der Regel 30 Minuten für die aktive Verwendung) nicht verwendet hat und die App gestartet wird, dann gilt Folgendes:
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

### <a name="app-report"></a>App-Bericht
Neben der Auswahl von Plattform und App werden zwei verschiedene Status zum App-Schutz bereitgestellt, die Sie auswählen können, bevor Sie den Bericht generieren. Der Status kann **Protected** (Geschützt) oder **Unprotected** (Nicht geschützt) sein.

  - Benutzerstatus für verwaltete MAM-Aktivität (**Protected** (Geschützt)): Dieser Bericht veranschaulicht die Aktivität jeder verwalteten MAM-App pro Benutzer. Er zeigt alle Apps an, die auf MAM-Richtlinien für jeden Benutzer abzielen, und den Status jeder App, die mit MAM-Richtlinien eingecheckt wird. Der Bericht enthält auch den Status jeder App, die auf eine MAM-Richtlinie ausgerichtet, jedoch nie eingecheckt wurde.
  - Benutzerstatus für verwaltete MAM-Aktivität (**Unprotected** (Nicht geschützt)): Dieser Bericht veranschaulicht je Benutzer die Aktivitäten von MAM-fähigen Apps, die derzeit nicht verwaltet werden. Dies kann folgende Ursache haben:
    - Diese Apps werden entweder von einem Benutzer oder von einer App verwendet, der bzw. die derzeit nicht unter eine MAM-Richtlinie fällt.
    - Alle Apps sind eingecheckt, erhalten jedoch keine MAM-Richtlinien.

    ![Screenshot des Bereichs „App-Berichterstellung“ eines Benutzers mit Informationen zu drei Apps](./media/app-protection-policies-monitor/MAM-reporting-4.png)

### <a name="user-configuration-report"></a>**Benutzerkonfigurationsbericht**
Abhängig vom ausgewählten Benutzer enthält dieser Bericht Details zu App-Konfigurationen, die der Benutzer erhalten hat.

### <a name="app-configuration-report"></a>**App-Konfigurationsbericht**
Abhängig von der ausgewählten Plattform und App enthält dieser Bericht Details zu den Benutzern, die Konfigurationen für die ausgewählte App erhalten haben.

### <a name="app-learning-report-for-windows-information-protection"></a>Bericht zum App-Learning für Windows Information Protection
In diesem Bericht wird angegeben, welche Apps versuchen, App-Grenzen zu überschreiten.

### <a name="website-learning-for-windows-information-protection"></a>Website-Learning für Windows Information Protection
In diesem Bericht wird angegeben, welche Websites versuchen, App-Grenzen zu überschreiten.

## <a name="export-app-protection-activities"></a>Exportieren von App-Schutzaktivitäten
Sie können alle Aktivitäten im Zusammenhang mit Ihren App-Schutzrichtlinien in eine CSV-Datei exportieren. Dies kann hilfreich sein, um alle App-Schutzstatus zu analysieren, die von den Benutzern gemeldeten wurden. Die **CSV-Datei für den App-Schutz zeigt folgende Informationen an**:
- **Benutzer:** Der Name des Benutzers.
- **E-Mail:** Die E-Mail-Adresse des Benutzers.
- **App:** Der Name der App.
- **App-Version:** Die Version der App.
- **Gerätename:** Die Namen von Geräten, die dem Benutzerkonto zugeordnet sind.
- **Gerätehersteller:** Listet den Hersteller des Geräts auf (nur Android). 
- **Gerätemodell:** Listet den Hersteller des Geräts auf (nur Android). 
- **Version des Android-Patches:** Das Datum des neuesten Android-Sicherheitspatches.
- **AAD Geräte-ID:** Diese Spalte wird aufgefüllt, wenn das Gerät in AAD eingebunden ist.
- **MDM-Geräte-ID:** Diese Spalte wird aufgefüllt, wenn das Gerät in der mobilen Geräteverwaltung von Microsoft Intune (MDM) registriert ist.
- **Plattform**: Das Betriebssystem.
- **Plattformversion:** Die Betriebssystemversion.
- **Verwaltungstyp:** Typ der Verwaltung auf dem Gerät. Beispielsweise „Android Enterprise“, „Nicht verwaltet“ oder „MDM“.  
- **Status des App-Schutzes:** „Nicht geschützt“ oder „Geschützt“.
- **Richtlinie:** Die App-Schutzrichtlinien, die der App zugeordnet sind.
- **Letzte Synchronisierung:** Zeitpunkt der letzten Synchronisierung der App mit Microsoft Intune. 
- **Konformitätszustand:** Gibt an, ob die App auf dem Benutzergerät mit App-basierten Richtlinien für bedingten Zugriff konform ist.  

Führen Sie diese Schritte aus, um eine App-Schutzdatei (CSV) oder eine App-Konfigurationsdatei (CSV) zu erstellen:

1. Wählen Sie im Bereich Verwaltung mobiler Anwendungen mit Intune den **App-Schutzbericht** aus.

    ![Screenshot vom Link zum Herunterladen des App-Schutzes](./media/app-protection-policies-monitor/app-protection-report-csv-2.png)

2. Wählen Sie **Ja**, um den Bericht zu speichern, und dann **Speichern unter** aus. Wählen Sie den Ordner zum Speichern des Berichts aus.

    ![Screenshot des Dialogfelds „Bericht speichern“ zur Bestätigung](./media/app-protection-policies-monitor/app-protection-report-csv-1.png)
   
> [!NOTE]
> Intune bietet zusätzliche Felder zur Geräteberichtserstellung, einschließlich Feldern für App-Registrierungs-ID, Android-Hersteller, Modell und Sicherheitspatchversion sowie iOS-/iPadOS-Modell. In Intune greifen Sie auf diese Felder zu, indem Sie **Apps** > **Status des App-Schutzes** > **Bericht zum App-Schutz: iOS/iPadOS, Android** auswählen. Darüber hinaus bieten diese Parameter Unterstützung bei der Konfiguration der Liste **Zulassen** für den Gerätehersteller (Android), der Liste **Zulassen** für das Gerätemodell (Android und iOS/iPadOS) sowie der Einstellung **minimum Android security patch version** (Niedrigste zulässige Android-Sicherheitsversion).   
 
## <a name="see-also"></a>Weitere Informationen:
- [Verwalten der Datenübertragung zwischen iOS-/iPadOS-Apps](data-transfer-between-apps-manage-ios.md)
- [Was Sie erwartet, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird](../fundamentals/end-user-mam-apps-android.md)
- [Was Sie erwartet, wenn Ihre iOS-/iPadOS-App von App-Schutzrichtlinien verwaltet wird](../fundamentals/end-user-mam-apps-ios.md)
