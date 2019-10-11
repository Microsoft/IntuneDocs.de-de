---
title: Android Enterprise-Konformitätseinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Liste aller Einstellungen, die Sie verwenden können, um Konformität für Ihre Android Enterprise-Geräte in Microsoft Intune festzulegen. Sie können Kennwortregeln festlegen, eine minimale oder maximale Betriebssystemversion auswählen, bestimmte Anwendungen einschränken, die Wiederverwendung von Kennwörtern verhindern und vieles mehr.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f7d38d5c71b06587b593eef46eca46f3d32f1349
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733100"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Android Enterprise-Einstellungen, um Geräte mit Intune als konform oder nicht konform zu kennzeichnen

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

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

  - **Nicht konfiguriert** (Standard): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Gesichert**: Diese Option ist die sicherste und bedeutet, dass auf dem Gerät keine Bedrohungen vorhanden sein können. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als kompatibel bewertet, wenn nur Bedrohungen niedriger Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als kompatibel bewertet, wenn die auf dem Gerät gefundenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht konform bewertet.
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
  - **Nicht konfiguriert** (Standardeinstellung): Die Einstellung wird bei der Konformitätsprüfung nicht ausgewertet.
  - **Grundlegende Integrität prüfen**
  - **Grundlegende Integrität und zertifizierte Geräte prüfen**

### <a name="device-properties"></a>Geräteeigenschaften

- **Mindestens erforderliche Betriebssystemversion:** Wenn ein Gerät nicht die Anforderungen an die mindestens erforderliche Betriebssystemversion erfüllt, gilt es als nicht konform. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann sein Gerät aktualisieren und dann auf Organisations Ressourcen zugreifen.
- **Maximal zulässige Betriebssystemversion:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf die Ressourcen der Organisation gesperrt. Der Benutzer wird aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann solange nicht auf Ressourcen der Organisation zugreifen, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

### <a name="system-security"></a>Systemsicherheit

- **Kennwort zum Entsperren mobiler Geräte anfordern:** Klicken Sie auf **Erforderlich**, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

  Diese Einstellung wird auf Geräteebene angewendet. Wenn Sie nur ein Kennwort auf Arbeitsprofilebene anfordern müssen, verwenden Sie eine Konfigurationsrichtlinie. Siehe [Gerätekonfigurationseinstellungen für Android Enterprise](../configuration/device-restrictions-android-for-work.md).

  - **Erforderlicher Kennworttyp:** Wählen Sie aus, ob ein Kennwort nur aus numerischen Zeichen oder aus einer Kombination aus Zahlen und anderen Zeichen bestehen soll. Folgende Optionen sind verfügbar:
    - **Standard des Geräts**: um die Kenn Wort Konformität auszuwerten, achten Sie darauf, dass Sie eine andere Kenn Wort Sicherheit als die **Geräte Standard**  
    - **Kennwort erforderlich, keine Einschränkungen**
    - **Schwach biometrisch**: [Vergleich von stark und schwach biometrisch](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (öffnet Android-Website)
    - **Numerisch** (Standard): Kennwort darf nur aus Zahlen bestehen, z. B. `123456789`. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
    - **Numerisch komplex**: Sich wiederholende oder fortlaufende Ziffern wie „1111“ oder „1234“ sind nicht zulässig. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
    - **Alphabetisch**: Buchstaben des Alphabets sind erforderlich. Zahlen und Symbole sind nicht erforderlich. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
    - **Alphanumerisch**: Schließt Großbuchstaben, Kleinbuchstaben und Ziffern ein. Geben Sie die **minimale Kennwortlänge** ein, die Benutzer für das Kennwort eingeben müssen (4 bis 16 Zeichen).
    - **Alphanumerisch mit Symbolen**: Schließt Großbuchstaben, Kleinbuchstaben, Ziffern, Interpunktionszeichen und Symbole ein. Geben Sie außerdem Folgendes ein:

      - **Minimale Kennwortlänge**: Geben Sie die Mindestlänge des Kennworts ein (4 bis 16 Zeichen).
      - **Erforderliche Anzahl von Zeichen**: Geben Sie die erforderliche Anzahl von Zeichen des Kennworts ein (0 bis 16 Zeichen).
      - **Erforderliche Anzahl von Kleinbuchstaben**: Geben Sie die erforderliche Anzahl von Kleinbuchstaben des Kennworts ein (0 bis 16 Zeichen).
      - **Erforderliche Anzahl von Großbuchstaben**: Geben Sie die erforderliche Anzahl von Großbuchstaben des Kennworts ein (0 bis 16 Zeichen).
      - **Erforderliche Anzahl anderer Zeichen als Buchstaben**: Geben Sie die erforderliche Anzahl anderer Zeichen als Buchstaben (alles außer Buchstaben im Alphabet) des Kennworts ein (0 bis 16 Zeichen).
      - **Erforderliche Anzahl numerischer Zeichen**: Geben Sie die erforderliche Anzahl numerischer Zeichen (`1`, `2`, `3` usw.) des Kennworts ein (0 bis 16 Zeichen).
      - **Erforderliche Anzahl von Symbolen**: Geben Sie die erforderliche Anzahl von Symbolen (`&`, `#`, `%` usw.) des Kennworts ein (0 bis 16 Zeichen).

- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Anzahl von Tagen bis zum Kennwortablauf**: Geben Sie die Anzahl der Tage (1-365) an, nach denen das Gerätekennwort geändert werden muss. Geben Sie beispielsweise zum Ändern des Kennworts nach 60 Tagen `60` ein. Wenn das Kennwort abläuft, werden Benutzer aufgefordert, ein neues Kennwort zu erstellen.
- **Anzahl erforderlicher Kennwörter, bevor ein Benutzer ein Kennwort wiederverwenden kann:** Geben Sie die Anzahl der letzten Kennwörter ein, die nicht wiederverwendet werden können (1–24). Verwenden Sie diese Einstellung, um zu verhindern, dass der Benutzer zuvor verwendete Kennwörter erstellt.

- **Verschlüsselung des Datenspeichers auf einem Gerät**: Wählen Sie **Erforderlich**, um den Datenspeicher auf Ihren Geräten zu verschlüsseln. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

  Diese Einstellung muss nicht konfiguriert werden, da Android Enterprise-Arbeitsprofilgeräte eine Verschlüsselung erzwingen.

## <a name="work-profile"></a>Arbeitsprofil

### <a name="device-health"></a>Device health

- **Geräte mit entfernten Nutzungsbeschränkungen:** Klicken Sie auf **Blockieren**, um Geräte mit Jailbreak oder entfernten Nutzungsbeschränkungen als nicht konform zu kennzeichnen. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- Festlegen **, dass das Gerät höchstens der Geräte Bedrohungsstufe entspricht**: Wählen Sie die maximal zulässige Geräte Bedrohungsstufe aus, die von Ihrem [Mobile Threat Defense-Dienst](mobile-threat-defense.md)ausgewertet wurde. Geräte, die diese Bedrohungsstufe überschreiten, werden als nicht konform gekennzeichnet. Wählen Sie die zulässige Bedrohungsstufe aus, um diese Einstellung zu verwenden:

  - **Nicht konfiguriert** (Standard): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Gesichert**: Diese Option ist die sicherste und bedeutet, dass auf dem Gerät keine Bedrohungen vorhanden sein können. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als kompatibel bewertet, wenn nur Bedrohungen niedriger Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als kompatibel bewertet, wenn die auf dem Gerät gefundenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Hoch**: Dies ist die am wenigsten sichere Option, die alle Bedrohungsebenen zulässt. Es ist möglicherweise hilfreich, diese Lösung nur zu Berichtszwecken zu verwenden.

#### <a name="google-play-protect"></a>Google Play Protect

- **Google Play Services ist konfiguriert:** **Erfordert**, dass die Google Play Services-App installiert und aktiviert ist. Google Play Services ermöglicht Sicherheitsupdates und stellt eine grundlegende Abhängigkeit für viele Sicherheitsfunktionen auf zertifizierten Google-Geräten dar. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Aktueller Sicherheitsanbieter:** **Erfordert**, dass ein aktueller Sicherheitsanbieter ein Gerät vor bekannten Sicherheitslücken schützen kann. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **SafetyNet-Gerätenachweis**: Legen Sie die Integritätsstufe des [SafetyNet-Nachweises](https://developer.android.com/training/safetynet/attestation.html) fest, die eingehalten werden muss. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standardeinstellung): Die Einstellung wird bei der Konformitätsprüfung nicht ausgewertet.
  - **Grundlegende Integrität prüfen**
  - **Grundlegende Integrität und zertifizierte Geräte prüfen**

> [!NOTE]
> Auf Android Enterprise-Geräten ist die Einstellung **Bedrohungsüberprüfung für Apps** eine Gerätekonfigurationsrichtlinie. Administratoren können mithilfe einer Richtlinie die Einstellung auf einem Gerät aktivieren. Siehe [Einstellungen für Geräteeinschränkungen für Android Enterprise](../configuration/device-restrictions-android-for-work.md).

### <a name="device-properties"></a>Geräteeigenschaften

- **Mindestens erforderliche Betriebssystemversion:** Wenn ein Gerät nicht die Anforderungen an die mindestens erforderliche Betriebssystemversion erfüllt, gilt es als nicht konform. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann sein Gerät aktualisieren und dann auf Organisations Ressourcen zugreifen.
- **Maximal zulässige Betriebssystemversion:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf die Ressourcen der Organisation gesperrt. Der Benutzer wird aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann solange nicht auf Ressourcen der Organisation zugreifen, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

### <a name="system-security"></a>Systemsicherheit

- **Kennwort zum Entsperren mobiler Geräte anfordern:** Klicken Sie auf **Erforderlich**, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet. Diese Einstellung wird auf Geräteebene angewendet. Wenn Sie nur ein Kennwort auf Arbeitsprofilebene anfordern müssen, verwenden Sie eine Konfigurationsrichtlinie. Siehe [Gerätekonfigurationseinstellungen für Android Enterprise](../configuration/device-restrictions-android-for-work.md).
- **Erforderlicher Kennworttyp:** Wählen Sie aus, ob ein Kennwort nur aus numerischen Zeichen oder aus einer Kombination aus Zahlen und anderen Zeichen bestehen soll. Folgende Optionen sind verfügbar:
  - **Gerätestandard**
  - **Biometrie auf niedriger Sicherheitsstufe**
  - **Mindestens numerisch** (Standard): Geben Sie die **minimale Kennwortlänge** ein, die ein Benutzer eingeben muss (4–16 Zeichen).
  - **Numerisch komplex:** Geben Sie die **minimale Kennwortlänge** ein, die ein Benutzer eingeben muss (4–16 Zeichen).
  - **Mindestens alphabetisch:** Geben Sie die **minimale Kennwortlänge** ein, die ein Benutzer eingeben muss (4–16 Zeichen).
  - **Mindestens alphanumerisch:** Geben Sie die **minimale Kennwortlänge** ein, die ein Benutzer eingeben muss (4–16 Zeichen).
  - **Mindestens alphanumerisch mit Symbolen**: Geben Sie die **minimale Kennwortlänge** ein, die ein Benutzer eingeben muss (zwischen 4 und 16 Zeichen).

- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Anzahl von Tagen bis zum Kennwortablauf:** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort des Endbenutzers abläuft und ein neues erstellt werden muss.
- **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl von zuletzt genutzten Kennwörtern an, die nicht erneut verwendet werden dürfen. Verwenden Sie diese Einstellung, um zu verhindern, dass der Benutzer zuvor verwendete Kennwörter erstellt.

#### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung des Datenspeichers auf einem Gerät**: Wählen Sie **Erforderlich**, um den Datenspeicher auf Ihren Geräten zu verschlüsseln. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet. 

  Diese Einstellung muss nicht konfiguriert werden, da Android Enterprise-Arbeitsprofilgeräte eine Verschlüsselung erzwingen.

#### <a name="device-security"></a>Gerätesicherheit

- **Apps von unbekannten Quellen blockieren:** Wählen Sie diese Option aus, um Geräte mit Quellen zu **blockieren**, für die **Sicherheit** > **Unbekannte Quellen** aktiviert ist (dies wird unter Android 4.0 bis Android 7.x unterstützt, ab Android 8.0 jedoch nicht mehr). Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

  Für das Sideloading von Apps müssen unbekannte Quellen zugelassen werden. Wenn Sie kein Sideloading von Android-Apps durchführen, legen Sie für dieses Feature **Blockieren** fest, um diese Konformitätsrichtlinie zu aktivieren.

  > [!IMPORTANT]
  > Das Sideloading von Anwendungen erfordert, dass die Einstellung **Apps von unbekannten Quellen blockieren** aktiviert ist. Erzwingen Sie diese Konformitätsrichtlinie nur, wenn Sie kein Sideloading von Android-Apps auf Geräten durchführen.

  Sie müssen diese Einstellung nicht konfigurieren, da Android Enterprise-Arbeitsprofilgeräte die Installation aus unbekannten Quellen stets einschränken.

- **Laufzeitintegrität der Unternehmensportal-App:** Legen Sie **Erforderlich** fest, um zu überprüfen, ob die Unternehmensportal-App alle der folgenden Anforderungen erfüllt:

  - Die Standardlaufzeitumgebung ist installiert.
  - Die App ist ordnungsgemäß signiert.
  - Die App befindet sich nicht im Debug-Modus.
  - Die App wurde aus einer bekannten Quelle installiert.

  Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

- **USB-Debugging auf dem Gerät blockieren**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Geräte das USB-Debuggingfeature verwenden. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

  Sie müssen diese Einstellungen nicht konfigurieren, da USB-Debuggen auf Android Enterprise-Geräten bereits deaktiviert ist.

- **Mindestens erforderliche Sicherheitspatchebene**: Wählen Sie die älteste Sicherheitspatchebene, die ein Gerät haben kann. Geräte, die nicht mindestens diese Patchebene aufweisen, sind nicht konform. Das Datum muss im Format *JJJJ-MM-TT* eingegeben werden.

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von Aktionen für nicht kompatible Geräte](actions-for-noncompliance.md) und [Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien](../fundamentals/scope-tags.md).
- [Überwachen Ihrer Konformitätsrichtlinien](compliance-policy-monitor.md).
- Siehe die [Einstellungen für Kompatibilitätsrichtlinien für Android](compliance-policy-create-android.md)-Geräte.
