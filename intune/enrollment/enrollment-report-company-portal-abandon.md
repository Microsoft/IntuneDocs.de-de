---
title: Unvollständige Berichte zu Benutzerregistrierungen in Intune
titleSuffix: Microsoft Intune
description: Informationen zu unvollständigen Berichten zu Benutzerregistrierungen
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 2/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: ae3c2380aa27096be2490d2404858179ea9d222e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503175"
---
# <a name="incomplete-user-enrollments-report"></a>Unvollständige Berichte zu Benutzerregistrierungen

In diesem Bericht wird festgehalten, an welcher Stelle Benutzer im Unternehmensportal den Registrierungsprozess abbrechen.

Wenn Sie den Bericht abrufen möchten, klicken Sie auf **Intune** > **Geräteregistrierung** > **Unvollständige Benutzerregistrierungen**.

Mithilfe dieser Informationen können Sie Ihre Onboardingdokumente aktualisieren, um Benutzer so besser beim Registrierungsprozess zu unterstützen. Wenn beispielsweise viele Benutzer den Prozess bereits bei den Nutzungsbedingungen abbrechen, können Sie überlegen, wie Sie diesen Bereich für Benutzer intuitiver gestalten.

## <a name="what-is-an-incomplete-enrollment"></a>Was ist eine unvollständige Registrierung?

Folgende Benutzeraktionen gelten als unvollständige Registrierungen:

- Der Benutzer wählt explizit eine Aktion aus, um die Registrierung zu stoppen.
- Der Benutzer schließt das Firmenportal während der Registrierung.
- Der Benutzer lässt mehr als 30 Minuten zwischen den Registrierungsabschnitten verstreichen.

Wenn sich ein Benutzer dafür entscheidet, die Registrierung mehrmals zu stoppen und neu zu starten, liegen mehrere Versuche und mehrere unvollständige Registrierungen vor. Wenn ein Benutzer 30 Minuten lang zwischen verschiedenen Registrierungsbildschirmen wartet, liegen mehrere unvollständige Registrierungen vor.

## <a name="what-does-the-report-show"></a>Was ist im Bericht enthalten?

Die Berichte enthalten Daten für iOS- und Android-Geräte.

Die Berichte zeigen Daten der letzten beiden Wochen an, aber sie können so gefiltert werden, dass ein beliebiger Zeitraum der letzten 30 Tagen angezeigt wird.

Sie können nach Datumsbereich, Betriebssystem und Registrierungsbereich filtern, indem Sie **Filter** auswählen.

### <a name="number-and-percentage-tiles"></a>Kacheln mit Anzahl und Prozentsatz

Im oberen Teil des Berichts sehen Sie die Anzahl und den Anteil (in Prozent) der unvollständigen Registrierungen im Verhältnis zu allen Registrierungen.

- Initiierte Registrierungen: die Anzahl der versuchten Registrierungen
- Unvollständige Registrierungen: die Anzahl der versuchten Registrierungen, die nicht zu einem vollständig registrierten und konformen Gerät geführt haben
- Unvollständigkeitsrate: der Anteil (in Prozent) der Registrierungsversuche, die abgebrochen wurden (abgebrochene Registrierungen bzw. initiierte Registrierungen)

### <a name="line-graph"></a>Liniendiagramm

Das Liniendiagramm zeigt die täglichen unvollständigen Registrierungen für jeden der vier Hauptregistrierungsabschnitte:

- Prüfliste für das Setup
- Plattformbildschirme
- Nutzungsbedingungen
- Konformität/Aktivierung

### <a name="user-abandonment-actions"></a>Abbruchaktionen von Benutzern

Die folgende Tabelle enthält die Liste der Benutzeraktionen, die als Aufforderung für eine unvollständige Registrierung gewertet werden. Beispiele zu Registrierungsbildschirmen finden Sie in den Registrierungsvideos für [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) und [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment). 


#### <a name="setup-checklist-section"></a>Abschnitt „Prüfliste für das Setup“

| Name der Aktion | Bildschirm oder Workflow | Plattform | Aktion |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | Aufforderung zum Öffnen einer Seite im Unternehmensportal | iOS/Android | **Abbrechen** |
| EnrollmentWrapUp | Bildschirm „Gerät wird registriert“ bis zum Ende von **Unternehmensressourcen werden geladen** | iOS/Android | Dauerte länger als 30 Minuten |
| DeviceCategory | Auswahl der Gerätekategorie (sofern der Administrator konfiguriert ist) bis zum Klicken auf **Fertig** | iOS/Android | Dauerte länger als 30 Minuten |
| PreEnrollmentWizard | Bildschirm für das Einrichten des Zugriffs nach Beginn des Registrierungsprozesses, aber Wechsel zurück zum Einrichten des Zugriffs | iOS/Android| **Verschieben** |
| PreEnrollmentWizard | Bildschirm für das Einrichten des Zugriffs bis zum Klicken auf **Weiter** auf dem Bildschirm **Wie geht es weiter?** | iOS/Android | Dauerte länger als 30 Minuten |

#### <a name="platform-screens-section"></a>Abschnitt „Plattformbildschirme“

| Name der Aktion | Bildschirm oder Workflow | Plattform | Aktion |
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

| Name der Aktion | Bildschirm oder Workflow | Plattform | Aktion |
| ---- |---- |---- |---- |
| TermsofUse | Nutzungsbedingungen (sofern der Administrator konfiguriert ist) | iOS/Android | **Alle ablehnen** |
| TermsofUse | Nutzungsbedingungen bis **Alle akzeptieren** | iOS/Android | Dauerte länger als 30 Minuten |

#### <a name="complianceactivation-section"></a>Abschnitt „Konformität/Aktivierung“

| Name der Aktion | Bildschirm oder Workflow | Plattform | Aktion |
| ---- |---- |---- |---- |
| Konformität | Gerätekonformität (sofern der Administrator konfiguriert ist) wird beim Zugriff auf das Setup nach der Registrierung nicht grün angezeigt.| iOS/Android | **Verschieben** |
| Konformität | Gerätekonformität wird nicht grün angezeigt; erst nach dem Aktualisieren wird sie grün angezeigt. | iOS/Android | Dauerte länger als 30 Minuten |
| Aktivierung | Registrierungsaktivierung (sofern der Administrator konfiguriert ist) wird beim Zugriff auf das Setup nicht grün angezeigt. | iOS/Android | **Verschieben** |
| Konformität | Geräteaktivierung wird nicht grün angezeigt; erst nach dem Aktualisieren wird sie grün angezeigt. | iOS/Android | Dauerte länger als 30 Minuten |

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie die Raten der unvollständigen Registrierungen überprüft haben, können Sie die [Registrierungsoptionen](enrollment-options.md) durchgehen, um mögliche Änderungen zur Verbesserung des Registrierungsprozesses vorzunehmen.
