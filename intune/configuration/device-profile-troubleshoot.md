---
title: Behandeln von Problemen mit Geräteprofilen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: 'Häufige Fragen und deren Antworten bezüglich Geräterichtlinien und -profilen in Microsoft Intune: z. B. Profiländerungen, die für bestimmte Benutzer und Geräte nicht gelten, wie lange es dauert, bis neue Richtlinien an Geräte gepusht werden, welche Einstellungen angewendet werden, wenn es mehrere Richtlinien gibt, was passiert, wenn Profile gelöscht oder entfernt werden.'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/04/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 95186e4d1e54737ffeaa5e4c9728d188c2f867d6
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206634"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>Häufige Fragen, Probleme und entsprechende Behebungen mit Geräterichtlinien und -profilen in Microsoft Intune



Erhalten Sie Antworten auf häufige Fragen zur Arbeit mit Geräteprofilen und -richtlinien in Intune. In diesem Artikel werden u. a. Check-In-Zeitintervalle und weitere Informationen aufgelistet.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Warum erhält ein Benutzer kein neues Profil, wenn er ein Kennwort oder eine Passphrase für ein vorhandenes WLAN-Profil ändert?

Sie erstellen ein WLAN-Unternehmensprofil, stellen das Profil für eine Gruppe bereit, ändern das Kennwort und speichern das Profil. Wenn sich das Profil ändert, erhalten einige Benutzer das neue Profil nicht.

Sie können dieses Problem beheben, indem Sie einen WLAN-Gastzugang einrichten. Bei einem Ausfall des Unternehmens-WLANs können die Benutzer auf das Gast-WLAN zurückgreifen. Dazu muss die Einstellung zum automatischen Herstellen einer Verbindung aktiviert sein. Ferner muss das WLAN-Gastprofil allen Benutzer bereitgestellt werden.

Einige weitere Empfehlungen:  

- Wenn das WLAN-Netzwerk, mit dem Sie die Verbindung herstellen, ein Kennwort oder eine Passphrase verwendet, müssen Sie eine direkte Verbindung mit dem Router herstellen können. Sie können das mit einem iOS-Gerät testen.
- Nachdem Sie erfolgreich eine Verbindung mit dem WLAN-Endpunkt (WLAN-Router) hergestellt haben, notieren Sie die verwendete SSID und die verwendete Anmeldeinformation (dieser Wert stellt das Kennwort oder die Passphrase dar).
- Geben Sie die SSID und die Anmeldeinformation (Kennwort oder Passphrase) im Feld für den vorinstallierten Schlüssel ein. 
- Führen Sie die Bereitstellung an eine Testgruppe mit eingeschränkter Benutzeranzahl aus, vorzugsweise nur das IT-Team. 
- Synchronisieren Sie Ihr iOS-Gerät mit Intune. Registrieren Sie sich, wenn Sie noch nicht registriert sind. 
- Probieren Sie, erneut eine Verbindung mit dem gleichen WLAN-Endpunkt (wie im ersten Schritt erwähnt) herzustellen.
- Nehmen Sie das Rollout an größere Gruppen und zu gegebener Zeit an alle erwarteten Benutzer in Ihrer Organisation durch. 

## <a name="how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned"></a>Wie lange dauert es, bis Geräte Richtlinien, Profile oder Apps nach ihrer Zuweisung abrufen?

Intune fordert das Gerät auf, beim Intune-Dienst einzuchecken. Der Zeitpunkt der Benachrichtigung kann zwischen unmittelbar nach der Zuweisung und einigen Stunden liegen. Unterschiede bestehen dabei auch zwischen den einzelnen Plattformen.

Checkt ein Gerät nach der ersten Benachrichtigung nicht zum Abrufen der Richtlinie oder des Profils ein, unternimmt Intune drei weitere Versuche. Wenn das Gerät offline ist – z. B. ausgeschaltet oder nicht mit einem Netzwerk verbunden –, erhält es die Benachrichtigungen möglicherweise nicht. In diesem Fall ruft das Gerät die Richtlinie oder das Profil beim nächsten geplanten Check-In beim Intune-Dienst ab. Das gleiche gilt für die Überprüfung auf Nichtkonformität, einschließlich der Geräte, die von einem kompatiblen auf einen nicht konformen Zustand wechseln.

**Geschätzte** Häufigkeiten:

| Plattform | Aktualisierungszyklus|
| --- | --- |
| iOS | Etwa alle 8 Stunden |
| macOS | Etwa alle 8 Stunden |
| Android | Etwa alle 8 Stunden |
| Windows 10-PCs, die als Geräte registriert sind | Etwa alle 8 Stunden |
| Windows Phone | Etwa alle 8 Stunden |
| Windows 8.1 | Etwa alle 8 Stunden |

Wenn das Gerät erst kürzlich registriert wurde, wird der Eincheckvorgang aus Konformitäts-, Nichtkonformitäts- und Konfigurationsgründen häufiger durchgeführt, **etwa** in folgendem Rhythmus:

| Plattform | Häufigkeit |
| --- | --- |
| iOS | Für 1 Stunde alle 15 Minuten und dann etwa alle 8 Stunden |  
| macOS | Für 1 Stunde alle 15 Minuten und dann etwa alle 8 Stunden | 
| Android | Für 15 Minuten alle 3 Minuten, dann für 2 Stunden alle 15 Minuten und dann etwa alle 8 Stunden | 
| Windows 10-PCs, die als Geräte registriert sind | Für 15 Minuten alle 3 Minuten, dann für 2 Stunden alle 15 Minuten und dann etwa alle 8 Stunden | 
| Windows Phone | Für 15 Minuten alle 5 Minuten, dann für 2 Stunden alle 15 Minuten und dann etwa alle 8 Stunden | 
| Windows 8.1 | Für 15 Minuten alle 5 Minuten, dann für 2 Stunden alle 15 Minuten und dann etwa alle 8 Stunden | 

Benutzer können jederzeit die Unternehmensportal-App, **Einstellungen** > **Synchronisieren** öffnen, um sofort zu überprüfen, ob Richtlinien- oder Profilupdates verfügbar sind.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Bei welchen Aktionen sendet Intune sofort eine Benachrichtigung an ein Gerät?

Verschiedene Aktionen können eine Benachrichtigung auslösen, z. B. das Zuweisen, Aktualisieren oder Löschen einer Richtlinie, eines Profils oder einer App. Das gleiche gilt für das Aufheben einer Zuweisung. Die Zeiträume variieren je nach Plattform.

Geräte checken bei Intune entweder beim Erhalt einer Benachrichtigung zum Einchecken oder während ihres geplanten Eincheckvorgangs ein. Wenn Sie für ein Gerät oder einen Benutzer ausdrücklich eine Aktion durchführen, z. B. Sperren, Zurücksetzen der Kennung, App-, Profil- oder Richtlinienzuweisung, fordert Intune das Gerät sofort zum Einchecken auf, um die Updates zu empfangen.

Andere Änderungen, wie etwa die Überarbeitung der Kontaktinformationen in der Unternehmensportal-App, führen nicht zu einer sofortigen Benachrichtigung der Geräte.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Wie finde ich heraus, welche Einstellungen angewendet werden, wenn für denselben Benutzer oder dasselbe Gerät mehrere Richtlinien zugewiesen werden?

Bei Zuweisung mehrerer Richtlinien an denselben Benutzer oder dasselbe Gerät gilt die Einstellung auf der Ebene der einzelnen Einstellungen:

- Konformitätsrichtlinieneinstellungen haben immer Vorrang vor Konfigurationsprofileinstellungen.

- Die restriktivste Konformitätsrichtlinie wird angewendet, wenn sie anhand derselben Einstellung in einer anderen Konformitätsrichtlinie ausgewertet wird.

- Falls eine Konfigurationsrichtlinieneinstellung im Konflikt mit einer Einstellung in einer anderen Konfigurationsrichtlinie steht, wird dieser Konflikt in Intune angezeigt. Konflikte dieser Art müssen Sie manuell auflösen.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>Was geschieht, wenn App-Schutzrichtlinien in Konflikt stehen? Welche wird auf die App angewendet?

Konfliktwerte sind die restriktivsten Einstellungen, die in einer App-Schutzrichtlinie zur Verfügung stehen, *außer* für die Zahleneingabefelder (z. B. PIN-Versuche vor dem Zurücksetzen). Die Zahleneingabefelder werden auf dieselben Werte festgelegt, die auch verwendet werden, wenn Sie eine MAM-Richtlinie erstellen und die empfohlenen Einstellungen verwenden.

Konflikte treten auf, wenn zwei Profileinstellungen identisch sind. Beispielsweise haben Sie zwei MAM-Richtlinien konfiguriert, die mit Ausnahme der Einstellung für Kopieren/Einfügen identisch sind. In diesem Szenario wird die Einstellung zum Kopieren und Einfügen auf den restriktivsten Wert festgelegt, die übrigen Einstellungen werden jedoch wie konfiguriert angewendet.

Eine Richtlinie wird in der App bereitgestellt und tritt in Kraft. Eine zweite Richtlinie wird bereitgestellt. In diesem Szenario hat die erste Richtlinie Vorrang und gilt weiterhin. Die zweite Richtlinie wird als in Konflikt stehend angezeigt. Wenn beide Richtlinien gleichzeitig angewendet werden, also keine vorherige Richtlinie vorhanden ist, stehen beide in Konflikt. Alle in Konflikt stehenden Einstellungen werden auf die restriktivsten Werte festgelegt.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>Was geschieht, wenn Sie benutzerdefinierte iOS-Richtlinien in Konflikt stehen?

Intune bewertet nicht die Nutzlast von Apple-Konfigurationsdateien oder einer benutzerdefinierten OMA-URI-Richtlinie (Open Mobile Alliance Uniform Resource Identifier). Es dient lediglich als Übermittlungsmechanismus.

Wenn Sie eine benutzerdefinierte Richtlinie zuweisen, bestätigen Sie, dass die konfigurierten Einstellungen nicht mit Konformitäts-, Konfigurations- oder anderen benutzerdefinierten Richtlinien in Konflikt stehen. Bei einer benutzerdefinierten Richtlinie mit Einstellungskonflikten werden die Einstellungen in zufälliger Reihenfolge angewendet.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>Was geschieht, wenn ein Profil gelöscht wird oder nicht mehr gilt?

Wenn Sie ein Profil löschen oder ein Gerät aus einer Gruppe mit diesem Profil entfernen, werden das Profil und die Einstellungen folgendermaßen vom Gerät entfernt:

- WLAN-, VPN-, Zertifikat- und E-Mail-Profile Diese Profile werden von allen unterstützten registrierten Geräten entfernt.
- Alle anderen Profiltypen:  

  - **Windows- und Android-Geräte:** Einstellungen werden nicht vom Gerät entfernt
  - **Windows Phone 8.1-Geräte:** Die folgenden Einstellungen werden entfernt:  
  
    - Anfordern eines Kennworts zum Entsperren mobiler Geräte
    - Einfache Kennwörter zulassen
    - Minimale Kennwortlänge
    - Erforderlicher Kennworttyp
    - Kennwortablauf (Tage)
    - Kennwortverlauf speichern
    - Anzahl zulässiger wiederholter Anmeldefehler, bevor das Gerät zurückgesetzt wird
    - Minuten der Inaktivität, bevor ein Kennwort erforderlich ist
    - Erforderlicher Kennworttyp – Mindestanzahl von Zeichensätzen
    - Kamera zulassen
    - Verschlüsselung auf mobilem Gerät anfordern
    - Wechselspeichermedien zulassen
    - Webbrowser zulassen
    - App Store zulassen
    - Bildschirmaufnahme zulassen
    - Geolocation zulassen
    - Microsoft-Konto erlauben
    - Kopieren und Einfügen zulassen
    - WLAN-Tethering zulassen
    - Automatische Verbindung mit unverschlüsselten WLAN-Hotspots zulassen
    - Berichterstellung für WLAN-Hotspots zulassen
    - Zurücksetzen zulassen
    - Bluetooth zulassen
    - NFC zulassen
    - WLAN zulassen

  - **iOS**: Alle Einstellungen werden entfernt, außer:
  
    - Sprachroaming zulassen
    - Datenroaming zulassen
    - Automatische Synchronisierung beim Roaming zulassen

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Ich habe ein Profil für Geräteeinschränkungen geändert, aber die Änderungen wurden nicht übernommen

Windows Phone-Geräte lassen keine Verringerung der Sicherheitsstufe in Sicherheitsrichtlinien zu, die mittels MDM oder EAS festgelegt wurden, nachdem diese festgelegt wurden. Angenommen, Sie legen ein **Kennwort mit Mindestanzahl von Zeichen** auf 8 fest und versuchen dann, diesen Wert auf 4 zu verringern. Das restriktivere Profil wurde bereits auf das Gerät angewendet.

Wenn Sie das Profil auf einen niedrigeren Sicherheitswert ändern möchten, müssen Sie die Sicherheitsrichtlinien zurücksetzen. Wischen Sie beispielsweise unter Windows 8.1 auf dem Desktop von rechts nach innen. Wählen Sie anschließend **Einstellungen** > **Systemsteuerung** aus. Wählen Sie das Applet **Benutzerkonten** aus. Im Navigationsmenü auf der linken Seite befindet sich im unteren Bereich der Link **Reset Security Policies** (Sicherheitsrichtlinien zurücksetzen). Wählen Sie ihn aus. Wählen Sie anschließend **Richtlinien zurücksetzen** aus.

Andere MDM-Geräte, wie Android, Windows Phone 8.1 und höher, iOS sowie Windows 10, müssen möglicherweise entfernt und bei Intune neu registriert werden, damit Sie ein weniger restriktives Profil anwenden können.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Einige Einstellungen in einem Windows 10-Profil werden als „Nicht verfügbar“ zurückgegeben

Einige Einstellungen auf Windows 10-Geräten werden möglicherweise als „Nicht verfügbar“ angezeigt. In diesen Fällen werden die Einstellungen von der auf Ihrem Gerät ausgeführten Windows-Version oder -Edition nicht unterstützt. Diese Meldung kann aus folgenden Gründen angezeigt werden:

- Die Einstellung ist nur auf neueren Windows-Versionen und nicht auf der aktuellen Betriebssystemversion verfügbar.
- Die Einstellung ist nur für bestimmte Windows-Editionen oder bestimmte SKUs, z. B. Home, Professional, Education und Enterprise, verfügbar.

Weitere Informationen zu den Anforderungen an Version und SKU für die verschiedenen Einstellungen finden Sie in der [Configuration Service Provider (CSP) reference (Referenz zu Konfigurationsdienstanbietern)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="next-steps"></a>Nächste Schritte

Benötigen Sie zusätzliche Hilfe? Weitere Informationen finden Sie unter [Anfordern von Support für Microsoft Intune](../fundamentals/get-support.md).
