---
title: Geräterichtlinien, Profile und häufig gestellte Fragen in Intune – Azure | Microsoft-Dokumentation
description: Lesen Sie mehr über die verschiedenen Richtlinien und Profile, die Sie in Microsoft Intune verwenden können, einschließlich Richtlinien zur Konfiguration von Geräten, für den Zugriff auf Unternehmensressourcen, zur Aktivierung von bedingtem Zugriff und zur Registrierung von Unternehmensgeräten. Außerdem erhalten Sie Antworten auf häufig gestellte Fragen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ROBOTS: ''
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e8a7a7405fe40d3568e736c244d9fcb308350709
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43317959"
---
# <a name="manage-settings-and-features-on-your-devices-with-intune-policies"></a>Verwalten von Einstellungen und Features auf Ihren Geräten mit Intune-Richtlinien

Microsoft Intune-*Richtlinien* sind Gruppen von Einstellungen zur Steuerung der Features auf mobilen Geräten und Computern. Sie erstellen Richtlinien, indem Sie Vorlagen verwenden, die empfohlene oder benutzerdefinierte Einstellungen enthalten. Anschließend stellen Sie diese für Geräte- oder Benutzergruppen bereit.

## <a name="types-of-policies"></a>Richtlinientypen

Intune-Richtlinien lassen sich in die folgenden Kategorien einteilen: Die von Ihnen verwendete Kategorie bestimmt, wie Sie die Richtlinie erstellen und bereitstellen können.

- **Konfigurationsrichtlinien**: Werden häufig zum Verwalten von Sicherheitseinstellungen und -features, wie Zugriff auf Unternehmensressourcen, auf Ihren Geräten verwendet. Erste Schritte bei den [Intune-Geräteprofilen](device-profiles.md).
- **Konformitätsrichtlinien für Geräte**: Definieren die Regeln und Einstellungen, die ein Gerät erfüllen muss, damit es als mit bedingten Zugriffsrichtlinien konform eingestuft wird. Kompatibilitätsrichtlinien ermöglichen Ihnen auch, die Kompatibilität von Geräten unabhängig von bedingten Zugriffsrechten zu überwachen und zu beheben. Erste Schritte bei den [Gerätekonformitätsrichtlinien](device-compliance-get-started.md).
- **Richtlinien für bedingten Zugriff**: Können E-Mail- und andere Dienste basierend auf Bedingungen schützen, die Sie festlegen. Als Einstieg sind die Artikel [Was ist bedingter Zugriff?](conditional-access.md) und [Welche gängigen Möglichkeiten gibt es für die Verwendung des bedingten Zugriffs in Intune?](conditional-access-intune-common-ways-use.md) zu empfehlen.
- **Richtlinien zum Registrieren unternehmenseigener Geräte**: Informationen über Richtlinien zum Registrieren unternehmenseigener Geräte finden Sie unter [Registrieren von iOS-Geräten in Intune](ios-enroll.md).

## <a name="frequently-asked-questions-about-intune-policies"></a>Häufig gestellte Fragen zu Intune-Richtlinien

### <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-being-deployed"></a>Wie lange dauert es, bis mobile Geräte Richtlinien oder Apps nach ihrer Bereitstellung abrufen können?
Wenn eine Richtlinie oder App bereitgestellt wird, beginnt Intune sofort damit, das Gerät zu benachrichtigen und zum Einchecken beim Intune-Dienst zu veranlassen. Dieser Schritt dauert normalerweise weniger als fünf Minuten.

Wenn ein Gerät sich nach der ersten Benachrichtigung nicht zum Abrufen der Richtlinie eincheckt, unternimmt Intune drei weitere Versuche.  Wenn das Gerät offline ist (z.B. ausgeschaltet oder nicht mit einem Netzwerk verbunden), erhält es die Benachrichtigungen möglicherweise nicht. In diesem Fall ruft das Gerät die Richtlinie beim nächsten geplanten Check-In beim Intune-Dienst wie folgt ab:

| Plattform | Check-In-Häufigkeit |
| --- | --- |
| iOS | Alle 6 Stunden | 
| Mac OS X | Alle 6 Stunden |
| Android | Alle 8 Stunden | 
| Windows Phone | Alle 8 Stunden | 
| Windows 8.1  | Alle 8 Stunden |  
| Windows 10-PCs, die als Geräte registriert sind | Alle 8 Stunden | 

Wenn das Gerät gerade registriert wurde, ist die Check-In-Häufigkeit höher:

| Plattform | Häufigkeit |
| --- | --- |
| iOS | Alle 15 Minuten für 6 Stunden und dann alle 6 Stunden |  
| Mac OS X | Alle 15 Minuten für 6 Stunden und dann alle 6 Stunden | 
| Android | Alle 3 Minuten für 15 Minuten, dann alle 15 Minuten für 2 Stunden und dann alle 8 Stunden | 
| Windows Phone | Alle 5 Minuten für 15 Minuten, dann alle 15 Minuten für 2 Stunden und dann alle 8 Stunden | 
| Windows-PCs, die als Geräte registriert sind | Alle 3 Minuten für 30 Minuten und dann alle 8 Stunden | 

Benutzer können auch jederzeit die Unternehmensportal-App öffnen und das Gerät synchronisieren, um sofort auf Richtlinien zu prüfen.

### <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Bei welchen Aktionen sendet Intune sofort eine Benachrichtigung an ein Gerät?
Geräte checken bei Intune beim Erhalt einer Benachrichtigung ein, die sie dazu auffordert, oder während ihres regelmäßigen geplanten Eincheckvorgangs.  Wenn Sie für ein Gerät oder einen Benutzer eine Aktion durchführen, wie z. B. Zurücksetzen, Sperren, Zurücksetzen der Kennung, App-Bereitstellung, Profilbereitstellung (WLAN, VPN, E-Mail) oder Bereitstellung der Richtlinie, versucht Intune sofort, das Gerät zu benachrichtigen, dass es sich beim Intune-Dienst einchecken soll.

Andere Änderungen, wie z.B. die Überarbeitung der Kontaktinformationen im Unternehmensportal, führen nicht zu einer sofortigen Benachrichtigung von Geräten.

### <a name="if-multiple-policies-are-deployed-to-the-same-user-or-device-how-do-i-know-which-settings-are-applied"></a>Wie finde ich heraus, welche Einstellungen angewendet werden, wenn für denselben Benutzer oder dasselbe Gerät mehrere Richtlinien bereitgestellt wurden?
Bei Bereitstellung mehrerer Richtlinien für denselben Benutzer oder dasselbe Gerät erfolgt die Auswertung, welche Einstellung angewendet werden soll, auf der Ebene der einzelnen Einstellungen:

- Kompatibilitätsrichtlinieneinstellungen haben immer Vorrang vor Konfigurationsrichtlinieneinstellungen.

- Die restriktivste Konformitätsrichtlinie wird angewendet, wenn sie gegen dieselbe Einstellung in einer anderen Konformitätsrichtlinie ausgewertet wird.

- Falls eine Konfigurationsrichtlinieneinstellung im Konflikt mit einer Einstellung in einer anderen Konfigurationsrichtlinie steht, wird dieser Konflikt in Intune angezeigt. Konflikte dieser Art müssen Sie manuell auflösen.

### <a name="what-happens-when-mobile-application-management-policies-conflict-with-each-other-which-one-applies-to-the-app"></a>Was geschieht, wenn Richtlinien für die Verwaltung mobiler Anwendungen miteinander in Konflikt stehen? Welche gilt für die App?
Konfliktwerte sind die restriktivsten Einstellungen, die in einer MAM-Richtlinie zur Verfügung stehen, außer für die Zahleneingabefelder (wie PIN-Versuche vor dem Zurücksetzen).  Die Zahleneingabefelder werden auf dieselben Werte gesetzt, die auch verwendet werden, wenn Sie in der Konsole eine MAM-Richtlinie erstellen und die empfohlenen Einstellungen verwenden.

Konflikte treten auf, wenn zwei Richtlinieneinstellungen identisch sind.  Beispielsweise haben Sie zwei MAM-Richtlinien konfiguriert, die mit Ausnahme der Einstellung für Kopieren/Einfügen identisch sind.  In diesem Szenario wird die Einstellung zum Kopieren und Einfügen auf den restriktivsten Wert festgelegt, die übrigen Einstellungen werden jedoch wie konfiguriert angewendet.

Wenn eine Richtlinie für die App bereitgestellt wird und in Kraft tritt und anschließend eine weitere bereitgestellt wird, erhält die zuerst angewendete Richtlinie Vorrang und bleibt wirksam. Die zweite Richtlinie wird als in Konflikt stehend angezeigt. Wenn beide Richtlinien gleichzeitig angewendet werden, also keine vorherige Richtlinie vorhanden ist, stehen beide in Konflikt. Alle in Konflikt stehenden Einstellungen werden auf die restriktivsten Werte festgelegt.

### <a name="what-happens-when-ios-custom-policies-conflict"></a>Was geschieht, wenn Sie benutzerdefinierte iOS-Richtlinien in Konflikt stehen?
Intune bewertet nicht die Nutzlast von Apple-Konfigurationsdateien oder einer benutzerdefinierten OMA-URI-Richtlinie (Open Mobile Alliance Uniform Resource Identifier). Es dient lediglich als Übermittlungsmechanismus.

Wenn Sie eine benutzerdefinierte Richtlinie bereitstellen, bestätigen Sie, dass die konfigurierten Einstellungen nicht mit Konformitäts-, Konfigurations- oder anderen benutzerdefinierten Richtlinien in Konflikt stehen. Bei einer benutzerdefinierten Richtlinie mit Einstellungskonflikten werden die Einstellungen in zufälliger Reihenfolge angewendet.

### <a name="what-happens-when-a-policy-is-deleted-or-no-longer-applicable"></a>Was geschieht, wenn eine Richtlinie gelöscht wird oder nicht mehr gilt?
Wenn Sie eine Richtlinie löschen oder ein Gerät aus einer Gruppe mit einer bereitgestellten Richtlinie entfernen, werden die Richtlinie und die Einstellungen gemäß den folgenden Listen von dem Gerät entfernt.

#### <a name="enrolled-devices"></a>Angemeldete Geräte

- WLAN-, VPN-, Zertifikat- und E-Mail-Profile: Diese Profile werden von allen unterstützten registrierten Geräten entfernt.
- Alle anderen Richtlinientypen:
  - **Windows- und Android-Geräte**: Einstellungen werden nicht vom Gerät entfernt.
  - **Windows Phone 8.1-Geräte**: Die folgenden Einstellungen werden entfernt:
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

### <a name="where-can-i-find-help-troubleshooting-policies"></a>Wo finde ich Hilfe zur Problembehandlung bei Richtlinien?

Siehe [Behandlung von Problemen mit Richtlinien](troubleshoot-policies-in-microsoft-intune.md)
