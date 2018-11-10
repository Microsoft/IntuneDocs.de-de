---
title: Abbruch der Registrierung beim Unternehmensportal in Intune
titlesuffix: Microsoft Intune
description: Erfahren Sie mehr über den Abbruchbericht des Unternehmensportals.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: ba1ee5a6811457b8c6e7343de7355261a2fcecdb
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236749"
---
# <a name="company-portal-abandonment-report"></a>Abbruchbericht des Unternehmensportals

Dieser Bericht zeigt auf, wo Benutzer im Unternehmensportal den Registrierungsprozess abbrechen.

Um den Bericht anzuzeigen, wählen Sie **Intune** > **Geräteregistrierung** > **Unternehmensportalabbruch**.

Mithilfe dieser Abbruchinformationen können Sie Ihre Onboardingdokumente aktualisieren, um Benutzer so besser beim Registrierungsprozess zu unterstützen. Wenn beispielsweise viele Benutzer den Prozess bereits bei den Nutzungsbedingungen abbrechen, können Sie überlegen, wie Sie diesen Bereich für Benutzer intuitiver gestalten.

## <a name="what-is-abandonment"></a>Was ist ein Abbruch?

Als Abbruch wird eine der folgenden Benutzeraktionen bezeichnet:

-   Der Benutzer wählt explizit eine Aktion aus, um die Registrierung zu stoppen.
-   Der Benutzer schließt das Firmenportal während der Registrierung.
-   Der Benutzer lässt mehr als 30 Minuten zwischen den Registrierungsabschnitten verstreichen.

Wenn ein Benutzer sich dafür entscheidet, die Registrierung zu stoppen und mehrmals neu zu starten, wird dies als mehrere Versuche und mehrere Abbrüche angezeigt. Wenn ein Benutzer 30 Minuten lang zwischen verschiedenen Registrierungsbildschirmen wartet, wird dies als mehrfacher Abbruch betrachtet.

## <a name="what-does-the-report-show"></a>Was ist im Bericht enthalten?

Die Registrierungsberichte enthalten Daten für iOS- und Android-Geräte.

Die Berichte zeigen Daten der letzten beiden Wochen an, aber sie können so gefiltert werden, dass ein beliebiger Zeitraum der letzten 30 Tagen angezeigt wird.

Sie können nach Datumsbereich, Betriebssystem und Registrierungsbereich filtern, indem Sie **Filter** auswählen.

### <a name="number-and-percentage-tiles"></a>Kacheln mit Anzahl und Prozentsatz

Am oberen Rand des Berichts sehen Sie die Anzahl und den Prozentsatz der Abbruchberichte in Bezug auf alle Registrierungen.

-   Initiierte Registrierungen: Die Anzahl der versuchten Registrierungen.
-   Abgebrochene Registrierungen: Die Anzahl der versuchten Registrierungen, die nicht zu einem vollständig registrierten und konformen Gerät geführt haben.
-   Abbruchrate: Der Prozentsatz der Registrierungsversuche, die abgebrochen wurden (abgebrochene Registrierungen bzw. initiierte Registrierungen).

### <a name="line-graph"></a>Liniendiagramm

Das Liniendiagramm zeigt die täglichen Abbrüche für jeden der vier Hauptregistrierungsabschnitte:

-   Prüfliste für das Setup
-   Plattformbildschirme
-   Nutzungsbedingungen
-   Konformität/Aktivierung

### <a name="user-abandonment-actions"></a>Abbruchaktionen von Benutzern

Die folgende Tabelle enthält die Liste der Benutzeraktionen, die als Abbruch gewertet werden. Beispiele zu Registrierungsbildschirmen finden Sie in den Registrierungsvideos für [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) und [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment). 


#### <a name="setup-checklist-section"></a>Abschnitt „Prüfliste für das Setup“

| Abbruchbezeichnung | Bildschirm oder Workflow | Plattform | Aktion |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | Aufforderung zum Öffnen einer Seite im Unternehmensportal | iOS/Android | **Abbrechen** |
| EnrollmentWrapUp | Bildschirm „Gerät wird registriert“ bis zum Ende von **Unternehmensressourcen werden geladen** | iOS/Android | Dauerte länger als 30 Minuten |
| DeviceCategory | Auswahl der Gerätekategorie (sofern der Administrator konfiguriert ist) bis zum Klicken auf **Fertig** | iOS/Android | Dauerte länger als 30 Minuten |
| PreEnrollmentWizard | Bildschirm für das Einrichten des Zugriffs nach Beginn des Registrierungsprozesses, aber Wechsel zurück zum Einrichten des Zugriffs | iOS/Android| **Verschieben** |
| PreEnrollmentWizard | Bildschirm für das Einrichten des Zugriffs bis zum Klicken auf **Weiter** auf dem Bildschirm **Wie geht es weiter?** | iOS/Android | Dauerte länger als 30 Minuten |

#### <a name="platform-screens-section"></a>Abschnitt „Plattformbildschirme“

| Abbruchbezeichnung | Bildschirm oder Workflow | Plattform | Aktion |
| ---- |---- |---- |---- |
| iOSProfileLaunch | Aufforderung zum Anzeigen eines Konfigurationsprofils | iOS | **Ignorieren** |
| iOSProfileLaunch | Bildschirm „Profil wird installiert“ | iOS | **Abbrechen** |
| iOSProfileLaunch | Aufforderung zum Bestätigen der vertrauenswürdigen Quelle des Profils zum Registrieren des Geräts | iOS | **Abbrechen** |
| iOSProfileLaunch | Bildschirm „Profil wird installiert“ bis zum fertig installierten Profil | iOS | Dauerte länger als 30 Minuten |
| AndroidPermissions | Bildschirm für die Aktivierung des Geräteadministrators | Android | **Abbrechen** |
| AndroidPermissions | Aufforderung für die Genehmigung zum Tätigen und Verwalten von Telefonanrufen bis zum **Aktivieren** des Geräteadministrators | Android | Dauerte länger als 30 Minuten |
| KnoxActivation | Aktivierung des KLMS-Agents (nur Samsung) | Android| **Abbrechen** |
| KnoxActivation | Aktivierung des KLMS-Agents bis **Bestätigen** | Android | Dauerte länger als 30 Minuten|

#### <a name="terms-of-use-section"></a>Abschnitt „Nutzungsbedingungen“

| Abbruchbezeichnung | Bildschirm oder Workflow | Plattform | Aktion |
| ---- |---- |---- |---- |
| TermsofUse | Nutzungsbedingungen (sofern der Administrator konfiguriert ist) | iOS/Android | **Alle ablehnen** |
| TermsofUse | Nutzungsbedingungen bis **Alle akzeptieren** | iOS/Android | Dauerte länger als 30 Minuten |

#### <a name="complianceactivation-section"></a>Abschnitt „Konformität/Aktivierung“

| Abbruchbezeichnung | Bildschirm oder Workflow | Plattform | Aktion |
| ---- |---- |---- |---- |
| Konformität | Gerätekonformität (sofern der Administrator konfiguriert ist) wird beim Zugriff auf das Setup nach der Registrierung nicht grün angezeigt.| iOS/Android | **Verschieben** |
| Konformität | Gerätekonformität wird nicht grün angezeigt; erst nach dem Aktualisieren wird sie grün angezeigt. | iOS/Android | Dauerte länger als 30 Minuten |
| Aktivierung | Registrierungsaktivierung (sofern der Administrator konfiguriert ist) wird beim Zugriff auf das Setup nicht grün angezeigt. | iOS/Android | **Verschieben** |
| Konformität | Geräteaktivierung wird nicht grün angezeigt; erst nach dem Aktualisieren wird sie grün angezeigt. | iOS/Android | Dauerte länger als 30 Minuten |

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie die Abbruchraten überprüft haben, können Sie die [Registrierungsoptionen](enrollment-options.md) durchgehen, um mögliche Änderungen zur Verbesserung des Registrierungsprozesses vorzunehmen.