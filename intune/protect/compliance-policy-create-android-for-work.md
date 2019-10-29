---
title: Android Enterprise-Konformitätseinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Liste aller Einstellungen, die Sie verwenden können, um Konformität für Ihre Android Enterprise-Geräte in Microsoft Intune festzulegen. Sie können Kennwortregeln festlegen, eine minimale oder maximale Betriebssystemversion auswählen, bestimmte Anwendungen einschränken, die Wiederverwendung von Kennwörtern verhindern und vieles mehr.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/16/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be1fbb72821b61566da84d6f98094c9a2f6ffef2
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810262"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Android Enterprise-Einstellungen, um Geräte mit Intune als konform oder nicht konform zu kennzeichnen

In diesem Artikel werden die verschiedenen Konformitätseinstellungen aufgeführt und beschrieben, die Sie in Intune für Android Enterprise-Geräte festlegen können. Im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) verwenden Sie diese Einstellungen, um Geräte des Typs „Rooted“ (mit Jailbreak) als nicht konform zu markieren, eine zulässige Bedrohungsstufe festzulegen, Google Play Protect zu aktivieren und vieles mehr.

Diese Funktion gilt für:

- Android Enterprise

Als Intune-Administrator verwenden Sie diese Konformitätseinstellungen, um die Ressourcen Ihrer Organisation zu schützen. Weitere Informationen zu Konformitätsrichtlinien und ihren Aufgaben finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

> [!IMPORTANT]
> Konformitäts Richtlinien wenden auch Android Enterprise Dedicated-Geräte an. Wenn eine Konformitäts Richtlinie einem dedizierten Gerät zugewiesen ist, wird das Gerät möglicherweise als **nicht kompatibel**angezeigt. Bedingter Zugriff und Erzwingung der Konformität sind auf dedizierten Geräten nicht verfügbar. Stellen Sie sicher, dass Sie alle Aufgaben und Aktionen fertig stellen, damit dedizierte Geräte Ihre zugewiesenen Richtlinien einhalten.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen einer Konformitätsrichtlinie](create-compliance-policy.md#create-the-policy) Wählen Sie **Android Enterprise** als **Plattform** aus.

## <a name="device-owner"></a>Geräteeigentümer

### <a name="device-health"></a>Geräteintegrität

- Festlegen **, dass das Gerät höchstens der Geräte Bedrohungsstufe entspricht**: Wählen Sie die maximal zulässige Geräte Bedrohungsstufe aus, die von Ihrem [Mobile Threat Defense-Dienst](mobile-threat-defense.md)ausgewertet wurde. Geräte, die diese Bedrohungsstufe überschreiten, werden als nicht konform gekennzeichnet. Wählen Sie die zulässige Bedrohungsstufe aus, um diese Einstellung zu verwenden:

  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Gesichert**: Diese Option ist die sicherste und bedeutet, dass auf dem Gerät keine Bedrohungen vorhanden sein können. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als konform bewertet, wenn nur Bedrohungen auf niedrigen Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als konform bewertet, wenn auf dem Gerät Bedrohungen auf niedriger oder mittlerer Stufe gefunden werden. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Hoch**: Dies ist die am wenigsten sichere Option, die alle Bedrohungsebenen zulässt. Es ist möglicherweise hilfreich, diese Lösung nur zu Berichtszwecken zu verwenden.
  
> [!NOTE] 
> Die folgenden Anbieter von Mobile Threat Defense (MTD) unterstützen die Bereitstellung von Android-Unternehmens Geräte Besitzern mithilfe der APP-Konfiguration:
> - Better Mobile 
> - Pradeo
> - Sophos Mobile
> - Zimperium 
>  
>  Wenden Sie sich an Ihren MTD-Anbieter, um genau die erforderliche Konfiguration für die Unterstützung von Android-Plattformen für Gerätebesitzer in InTune Diese Liste wird aktualisiert, wenn MTD-Parser Android-Szenarios für Unternehmens Gerätebesitzer unterstützen. 

#### <a name="google-play-protect"></a>Google Play Protect

- **SafetyNet-Gerätenachweis**: Legen Sie die Integritätsstufe des [SafetyNet-Nachweises](https://developer.android.com/training/safetynet/attestation.html) fest, die eingehalten werden muss. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (*Standardeinstellung*): Die Einstellung wird bei der Konformitätsprüfung nicht ausgewertet.
  - **Grundlegende Integrität prüfen**
  - **Grundlegende Integrität und zertifizierte Geräte prüfen**

### <a name="device-properties"></a>Geräteeigenschaften

#### <a name="operating-system-version"></a>Version des Betriebssystems

- **Mindestens erforderliche Betriebssystemversion:** Wenn ein Gerät nicht die Anforderungen an die mindestens erforderliche Betriebssystemversion erfüllt, gilt es als nicht konform. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann sein Gerät aktualisieren und dann auf Organisations Ressourcen zugreifen.

  *Standardmäßig ist keine Version konfiguriert*.

- **Maximal zulässige Betriebssystemversion:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf die Ressourcen der Organisation gesperrt. Der Benutzer wird aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann solange nicht auf Ressourcen der Organisation zugreifen, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

  *Standardmäßig ist keine Version konfiguriert*.

- **Mindestens erforderliche Sicherheitspatchebene**: Wählen Sie die älteste Sicherheitspatchebene, die ein Gerät haben kann. Geräte, die nicht mindestens diese Patchebene aufweisen, sind nicht konform. Das Datum muss im Format JJJJ-MM-TT eingegeben werden.

  *Standardmäßig ist kein Datum konfiguriert*.


### <a name="system-security"></a>Systemsicherheit

- **Anfordern eines Kennworts zum Entsperren mobiler Geräte:** 
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Erforderlich**: Benutzer müssen ein Kennwort eingeben, bevor sie auf ihr Gerät zugreifen können. 

  Diese Einstellung gilt für die Geräteebene. Wenn Sie nur ein Kennwort auf Arbeitsprofilebene anfordern müssen, verwenden Sie eine Konfigurationsrichtlinie. Siehe [Gerätekonfigurationseinstellungen für Android Enterprise](../configuration/device-restrictions-android-for-work.md).

  - **Erforderlicher Kennworttyp:** Wählen Sie aus, ob ein Kennwort nur aus numerischen Zeichen oder aus einer Kombination aus Zahlen und anderen Zeichen bestehen soll. Folgende Optionen sind verfügbar:
    - **Standardgerät** : Wenn Sie die Kenn Wort Konformität auswerten möchten, achten Sie darauf, dass Sie die Kenn Wort Sicherheit außer der **Standardeinstellung des Geräts**  
    - **Kennwort erforderlich, keine Einschränkungen**
    - **Schwach biometrisch** - [ Vergleich von stark und schwach biometrisch](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (öffnet Android-Website)
    - **Numerisch** (*Standardeinstellung*): Kennwort darf nur aus Zahlen bestehen, z.B. `123456789`. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
    - **Numerisch komplex**: Sich wiederholende oder fortlaufende Ziffern wie „1111“ oder „1234“ sind nicht zulässig. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
    - **Alphabetisch**: Buchstaben des Alphabets sind erforderlich. Zahlen und Symbole sind nicht erforderlich. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
    - **Alphanumerisch**: Schließt Großbuchstaben, Kleinbuchstaben und Ziffern ein. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
    - **Alphanumerisch mit Symbolen**: Schließt Großbuchstaben, Kleinbuchstaben, Ziffern, Interpunktionszeichen und Symbole ein. Geben Sie außerdem Folgendes ein:
    
    Je nach ausgewähltem Kenn *Worttyp* sind folgende Einstellungen verfügbar:  
    - **Minimale Kennwortlänge**: Geben Sie die Mindestlänge des Kennworts ein (4 bis 16 Zeichen).  

    - **Erforderliche Anzahl von Zeichen**: Geben Sie die erforderliche Anzahl von Zeichen des Kennworts ein (0 bis 16 Zeichen).

    - **Erforderliche Anzahl von Kleinbuchstaben**: Geben Sie die erforderliche Anzahl von Kleinbuchstaben des Kennworts ein (0 bis 16 Zeichen).

    - **Erforderliche Anzahl von Großbuchstaben**: Geben Sie die erforderliche Anzahl von Großbuchstaben des Kennworts ein (0 bis 16 Zeichen).

    - **Erforderliche Anzahl anderer Zeichen als Buchstaben**: Geben Sie die erforderliche Anzahl anderer Zeichen als Buchstaben (alles außer Buchstaben im Alphabet) des Kennworts ein (0 bis 16 Zeichen).

    - **Erforderliche Anzahl numerischer Zeichen**: Geben Sie die erforderliche Anzahl numerischer Zeichen (`1`, `2`, `3` usw.) des Kennworts ein (0 bis 16 Zeichen).
    
    - **Erforderliche Anzahl von Symbolen**: Geben Sie die erforderliche Anzahl von Symbolen (`&`, `#`, `%` usw.) des Kennworts ein (0 bis 16 Zeichen).
 
- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss. Zu den Optionen gehören der Standardwert *nicht konfiguriert*und *eine Minute* bis zu *8 Stunden*.

- **Anzahl von Tagen bis zum Kennwortablauf**: Geben Sie die Anzahl der Tage (1-365) an, nach denen das Gerätekennwort geändert werden muss. Geben Sie beispielsweise zum Ändern des Kennworts nach 60 Tagen `60` ein. Wenn das Kennwort abläuft, werden Benutzer aufgefordert, ein neues Kennwort zu erstellen.

   *Standardmäßig ist kein Wert konfiguriert*.

- **Anzahl erforderlicher Kennwörter, bevor ein Benutzer ein Kennwort wiederverwenden kann:** Geben Sie die Anzahl der letzten Kennwörter ein, die nicht wiederverwendet werden können (1–24). Verwenden Sie diese Einstellung, um zu verhindern, dass der Benutzer zuvor verwendete Kennwörter erstellt.  

    *Standardmäßig ist keine Version konfiguriert*.

#### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung des Datenspeichers auf dem Gerät**: 
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Erfordern** : Verschlüsseln Sie die Datenspeicherung auf Ihren Geräten.  

  Diese Einstellung muss nicht konfiguriert werden, da Android Enterprise-Arbeitsprofilgeräte eine Verschlüsselung erzwingen.

## <a name="work-profile"></a>Arbeitsprofil

### <a name="device-health"></a>Geräteintegrität

- **Geräte mit entfernten Nutzungsbeschränkungen**: 
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Blockieren**: Geräte mit Jailbreak oder entfernten Nutzungsbeschränkungen werden als nicht konform gekennzeichnet.  

- Festlegen **, dass das Gerät höchstens der Geräte Bedrohungsstufe entspricht**: Wählen Sie die maximal zulässige Geräte Bedrohungsstufe aus, die von Ihrem [Mobile Threat Defense-Dienst](mobile-threat-defense.md)ausgewertet wurde. Geräte, die diese Bedrohungsstufe überschreiten, werden als nicht konform gekennzeichnet. Wählen Sie die zulässige Bedrohungsstufe aus, um diese Einstellung zu verwenden:

  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Gesichert**: Diese Option ist die sicherste und bedeutet, dass auf dem Gerät keine Bedrohungen vorhanden sein können. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als konform bewertet, wenn nur Bedrohungen auf niedrigen Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als konform bewertet, wenn auf dem Gerät Bedrohungen auf niedriger oder mittlerer Stufe gefunden werden. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Hoch**: Dies ist die am wenigsten sichere Option, die alle Bedrohungsebenen zulässt. Es ist möglicherweise hilfreich, diese Lösung nur zu Berichtszwecken zu verwenden.

#### <a name="google-play-protect"></a>Google Play Protect

- **Google Play Services ist konfiguriert**: 
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Erforderlich**: Erzwingt, dass die Google Play Services-App installiert und aktiviert ist. Google Play Services ermöglicht Sicherheitsupdates und stellt eine grundlegende Abhängigkeit für viele Sicherheitsfunktionen auf zertifizierten Google-Geräten dar. 
  
- **Aktueller Sicherheitsanbieter**: 
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Erforderlich**: Erzwingt, dass ein aktueller Sicherheitsanbieter ein Gerät vor bekannten Sicherheitslücken schützen kann. 
  
- **SafetyNet-Gerätenachweis**: Legen Sie die Integritätsstufe des [SafetyNet-Nachweises](https://developer.android.com/training/safetynet/attestation.html) fest, die eingehalten werden muss. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (*Standardeinstellung*): Die Einstellung wird bei der Konformitätsprüfung nicht ausgewertet.
  - **Grundlegende Integrität prüfen**
  - **Grundlegende Integrität und zertifizierte Geräte prüfen**

> [!NOTE]
> Auf Android Enterprise-Geräten ist die Einstellung **Bedrohungsüberprüfung für Apps** eine Gerätekonfigurationsrichtlinie. Administratoren können mithilfe einer Richtlinie die Einstellung auf einem Gerät aktivieren. Siehe [Einstellungen für Geräteeinschränkungen für Android Enterprise](../configuration/device-restrictions-android-for-work.md).

### <a name="device-properties"></a>Geräteeigenschaften

#### <a name="operating-system-version"></a>Version des Betriebssystems

- **Mindestens erforderliche Betriebssystemversion:** Wenn ein Gerät nicht die Anforderungen an die mindestens erforderliche Betriebssystemversion erfüllt, gilt es als nicht konform. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann sein Gerät aktualisieren und dann auf Organisations Ressourcen zugreifen.

  *Standardmäßig ist keine Version konfiguriert*.

- **Maximal zulässige Betriebssystemversion:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf die Ressourcen der Organisation gesperrt. Der Benutzer wird aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann solange nicht auf Ressourcen der Organisation zugreifen, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

  *Standardmäßig ist keine Version konfiguriert*.

### <a name="system-security"></a>Systemsicherheit

- **Anfordern eines Kennworts zum Entsperren mobiler Geräte:** 
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet. 
  - **Erforderlich**: Benutzer müssen ein Kennwort eingeben, bevor sie auf ihr Gerät zugreifen können.  

  Diese Einstellung gilt für die Geräteebene. Wenn Sie nur ein Kennwort auf Arbeitsprofilebene anfordern müssen, verwenden Sie eine Konfigurationsrichtlinie. Siehe [Gerätekonfigurationseinstellungen für Android Enterprise](../configuration/device-restrictions-android-for-work.md).

- **Erforderlicher Kennworttyp:** Wählen Sie aus, ob ein Kennwort nur aus numerischen Zeichen oder aus einer Kombination aus Zahlen und anderen Zeichen bestehen soll. Folgende Optionen sind verfügbar:
  - **Gerätestandard**
  - **Biometrie auf niedriger Sicherheitsstufe**
  - **Mindestens numerisch** (*Standardeinstellung*): Geben Sie die **minimale Kennwortlänge** ein, die ein Benutzer eingeben muss (4–16 Zeichen).
  - **Numerisch komplex:** Geben Sie die **minimale Kennwortlänge** ein, die ein Benutzer eingeben muss (4–16 Zeichen).
  - **Mindestens alphabetisch:** Geben Sie die **minimale Kennwortlänge** ein, die ein Benutzer eingeben muss (4–16 Zeichen).
  - **Mindestens alphanumerisch:** Geben Sie die **minimale Kennwortlänge** ein, die ein Benutzer eingeben muss (4–16 Zeichen).
  - **Mindestens alphanumerisch mit Symbolen**: Geben Sie die **minimale Kennwortlänge** ein, die ein Benutzer eingeben muss (zwischen 4 und 16 Zeichen).

  Je nach ausgewähltem Kenn *Worttyp* sind folgende Einstellungen verfügbar:  
  - **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss. Zu den Optionen gehören der Standardwert *nicht konfiguriert*und *eine Minute* bis zu *8 Stunden*.

  - **Anzahl von Tagen bis zum Kennwortablauf**: Geben Sie die Anzahl der Tage (1-365) an, nach denen das Gerätekennwort geändert werden muss. Geben Sie beispielsweise zum Ändern des Kennworts nach 60 Tagen `60` ein. Wenn das Kennwort abläuft, werden Benutzer aufgefordert, ein neues Kennwort zu erstellen.

  - **Minimale Kennwortlänge**: Geben Sie die Mindestlänge des Kennworts ein (4 bis 16 Zeichen). 
  
  - **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl von zuletzt genutzten Kennwörtern an, die nicht erneut verwendet werden dürfen. Verwenden Sie diese Einstellung, um zu verhindern, dass der Benutzer zuvor verwendete Kennwörter erstellt.

#### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung des Datenspeichers auf dem Gerät**: 
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Erfordern** : Verschlüsseln Sie die Datenspeicherung auf Ihren Geräten.  

  Diese Einstellung muss nicht konfiguriert werden, da Android Enterprise-Arbeitsprofilgeräte eine Verschlüsselung erzwingen.

#### <a name="device-security"></a>Gerätesicherheit

- **Apps von unbekannten Quellen blockieren**: 
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Blockieren** von Geräten mit **Sicherheits** > **unbekannten Quellen** (*unter Android 4,0 über Android 7. x unterstützt. Nicht von Android 8.0 und höher unterstützt*).  

  Für das Sideloading von Apps müssen unbekannte Quellen zugelassen werden. Wenn Sie kein Sideloading von Android-Apps durchführen, legen Sie für dieses Feature **Blockieren** fest, um diese Konformitätsrichtlinie zu aktivieren.

  > [!IMPORTANT]
  > Das Sideloading von Anwendungen erfordert, dass die Einstellung **Apps von unbekannten Quellen blockieren** aktiviert ist. Erzwingen Sie diese Konformitätsrichtlinie nur, wenn Sie kein Sideloading von Android-Apps auf Geräten durchführen.

  Sie müssen diese Einstellung nicht konfigurieren, da Android Enterprise-Arbeitsprofilgeräte die Installation aus unbekannten Quellen stets einschränken.

- **Laufzeitintegrität der Unternehmensportal-App**: 
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Erforderlich**: Wählen Sie diese Einstellung aus, um sicherzustellen, dass die Unternehmensportal-App alle folgenden Anforderungen erfüllt:
    - Die Standardlaufzeitumgebung ist installiert.
    - Die App ist ordnungsgemäß signiert.
    - Die App befindet sich nicht im Debug-Modus.
    - Die App wurde aus einer bekannten Quelle installiert.

- **USB-Debugging auf Gerät blockieren**: 
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Blockieren**: Mit dieser Einstellung wird verhindert, dass Geräte das USB-Debuggingfeature verwenden.  

  Sie müssen diese Einstellungen nicht konfigurieren, da USB-Debuggen auf Android Enterprise-Geräten bereits deaktiviert ist.

- **Mindestens erforderliche Sicherheitspatchebene**: Wählen Sie die älteste Sicherheitspatchebene, die ein Gerät haben kann. Geräte, die nicht mindestens diese Patchebene aufweisen, sind nicht konform. Das Datum muss im Format JJJJ-MM-TT eingegeben werden.

  *Standardmäßig ist kein Datum konfiguriert*.

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von Aktionen für nicht kompatible Geräte](actions-for-noncompliance.md) und [Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien](../fundamentals/scope-tags.md).
- [Überwachen Ihrer Konformitätsrichtlinien](compliance-policy-monitor.md).
- Siehe die [Einstellungen für Kompatibilitätsrichtlinien für Android](compliance-policy-create-android.md)-Geräte.
