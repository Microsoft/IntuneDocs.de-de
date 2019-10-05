---
title: Konformitätseinstellungen für Android-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Liste aller Einstellungen, die Sie verwenden können, um Konformität für Ihre Android-Geräte in Microsoft Intune festzulegen. Sie können Kennwortregeln festlegen, eine minimale oder maximale Betriebssystemversion auswählen, bestimmte Anwendungen einschränken, die Wiederverwendung von Kennwörtern verhindern und vieles mehr.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 80ed21c0831eb92a8e18596e7ab5f09848362b3a
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733061"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Android-Einstellungen, um Geräte mit Intune als konform oder nicht konform zu kennzeichnen

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In diesem Artikel werden die verschiedenen Konformitätseinstellungen aufgeführt und beschrieben, die Sie in Intune für Android-Geräte festlegen können. Im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) verwenden Sie diese Einstellungen, um Geräte des Typs „Rooted“ (mit Jailbreak) als nicht konform zu markieren, eine zulässige Bedrohungsstufe festzulegen, Google Play Protect zu aktivieren und vieles mehr.

Diese Funktion gilt für:

- Android

Als Intune-Administrator verwenden Sie diese Konformitätseinstellungen, um die Ressourcen Ihrer Organisation zu schützen. Weitere Informationen zu Konformitätsrichtlinien und ihren Aufgaben finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen einer Konformitätsrichtlinie](create-compliance-policy.md#create-the-policy) Wählen Sie als **Plattform** die Option **Android** aus.

## <a name="device-health"></a>Device health

- **Geräte mit entfernten Nutzungsbeschränkungen:** Klicken Sie auf **Blockieren**, um Geräte mit Jailbreak oder entfernten Nutzungsbeschränkungen als nicht konform zu kennzeichnen. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Anfordern, dass das Gerät höchstens der angegebenen Gerätebedrohungsstufe entspricht:** Verwenden Sie diese Einstellung, um die Risikobewertung mit der Lookout Mobile Endpoint Security-Lösung als Konformitätsvoraussetzung zu verlangen. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet. Wählen Sie die zulässige Bedrohungsstufe aus, um diese Einstellung zu verwenden:
  - **Gesichert**: Diese Option ist die sicherste, da auf dem Gerät keine Bedrohungen vorhanden sein können. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als kompatibel bewertet, wenn nur Bedrohungen niedriger Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als kompatibel bewertet, wenn die auf dem Gerät vorhandenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Hoch**: Dies ist die am wenigsten sichere Option, die alle Bedrohungsebenen zulässt. Es ist möglicherweise hilfreich, diese Lösung nur zu Berichtszwecken zu verwenden.

### <a name="google-play-protect"></a>Google Play Protect

- **Google Play Services ist konfiguriert:** **Erfordert**, dass die Google Play Services-App installiert und aktiviert ist. Google Play Services ermöglicht Sicherheitsupdates und stellt eine grundlegende Abhängigkeit für viele Sicherheitsfunktionen auf zertifizierten Google-Geräten dar. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Aktueller Sicherheitsanbieter:** **Erfordert**, dass ein aktueller Sicherheitsanbieter ein Gerät vor bekannten Sicherheitslücken schützen kann. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Bedrohungsüberprüfung für Apps:** **Erfordert**, dass das Android-Feature **Apps überprüfen** aktiviert wird. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

  > [!NOTE]
  > Auf der älteren Android-Plattform ist diese Funktion eine Konformitätseinstellung. Intune kann nur prüfen, ob diese Einstellung auf Geräteebene aktiviert ist.

- **SafetyNet-Gerätenachweis**: Legen Sie die Integritätsstufe des [SafetyNet-Nachweises](https://developer.android.com/training/safetynet/attestation.html) fest, die eingehalten werden muss. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standardeinstellung): Die Einstellung wird bei der Konformitätsprüfung nicht ausgewertet.
  - **Grundlegende Integrität prüfen**
  - **Grundlegende Integrität und zertifizierte Geräte prüfen**

> [!NOTE]
> Informationen zum Konfigurieren der Google Play Protect-Einstellungen mithilfe von App-Schutzrichtlinien finden Sie unter [Intune App-Schutzrichtlinieneinstellungen](../apps/app-protection-policy-settings-android.md#conditional-launch) für Android.

## <a name="device-property-settings"></a>Einstellungen für Geräteeigenschaften

- **Minimale Betriebssystemversion:** Wenn ein Gerät die Anforderungen an die erforderliche Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht konform gemeldet. Ein Link mit Informationen zum Durchführen von Upgrades wird gezeigt. Der Endbenutzer kann ein Upgrade seines Geräts durchführen, und anschließend auf die Unternehmensressourcen zugreifen.
- **Maximale Version des Betriebssystems:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt. Der Benutzer wird dazu aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

## <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit

### <a name="password"></a>Kennwort

- **Kennwort zum Entsperren mobiler Geräte anfordern:** Klicken Sie auf **Erforderlich**, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Benutzerkennwort enthalten muss.
- **Erforderlicher Kennworttyp:** Wählen Sie aus, ob ein Kennwort nur aus numerischen Zeichen oder aus einer Kombination aus Zahlen und anderen Zeichen bestehen soll. Folgende Optionen sind verfügbar:
  - **Standard des Geräts**: um die Kenn Wort Konformität auszuwerten, achten Sie darauf, dass Sie eine andere Kenn Wort Sicherheit als die **Geräte Standard**
  - **Biometrie auf niedriger Sicherheitsstufe**
  - **Mindestens numerisch** (Standard)
  - **Numerisch, komplex:** Sich wiederholende oder fortlaufende Ziffern wie `1111` oder `1234` sind nicht zulässig.
  - **Mindestens alphabetisch** 
  - **Mindestens alphanumerisch**
  - **Mindestens alphanumerisch mit Symbolen**

- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Kennwortablauf (Tage)** : Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort des Benutzers abläuft und ein neues erstellen werden muss.
- **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl von zuletzt genutzten Kennwörtern an, die nicht erneut verwendet werden dürfen. Verwenden Sie diese Einstellung, um zu verhindern, dass der Benutzer zuvor verwendete Kennwörter erstellt.

### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung des Datenspeichers auf einem Gerät**: (Android 4.0 und höher, oder KNOX 4.0 und höher): Wählen Sie **Erforderlich**, um den Datenspeicher auf Ihren Geräten zu verschlüsseln. Wenn Sie die Einstellung **Kennwort zum Entsperren mobiler Geräte anfordern** auswählen, werden Geräte verschlüsselt. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

### <a name="device-security"></a>Gerätesicherheit

- **Apps von unbekannten Quellen blockieren:** Wählen Sie diese Option aus, um Geräte mit Quellen zu **blockieren**, für die „Sicherheit > Unbekannte Quellen“ aktiviert ist (dies wird für Android 4.0 bis Android 7.x unterstützt, ab Android 8.0 jedoch nicht mehr). Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

  Für das Sideloading von Apps müssen unbekannte Quellen zugelassen werden. Wenn Sie kein Sideloading von Android-Apps durchführen, legen Sie für dieses Feature **Blockieren** fest, um diese Konformitätsrichtlinie zu aktivieren. 

  > [!IMPORTANT]
  > Das Sideloading von Anwendungen erfordert, dass die Einstellung **Apps von unbekannten Quellen blockieren** aktiviert ist. Erzwingen Sie diese Konformitätsrichtlinie nur, wenn Sie kein Sideloading von Android-Apps auf Geräten durchführen.

- **Laufzeitintegrität der Unternehmensportal-App:** Legen Sie **Erforderlich** fest, um zu überprüfen, ob die Unternehmensportal-App alle der folgenden Anforderungen erfüllt:

  - Die Standardlaufzeitumgebung ist installiert.
  - Die App ist ordnungsgemäß signiert.
  - Die App befindet sich nicht im Debug-Modus.
  - Die App wurde aus einer bekannten Quelle installiert.

  Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

- **USB-Debugging auf dem Gerät blockieren** (Android 4.2 oder höher): Wählen Sie **Blockieren** aus, um zu verhindern, dass Geräte das USB-Debuggingfeature verwenden. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Mindestens erforderliche Sicherheitspatchebene** (Android 6.0 oder höher): Wählen Sie die älteste Sicherheitspatchebene, die ein Gerät haben kann. Geräte, die nicht mindestens diese Patchebene aufweisen, sind nicht konform. Das Datum muss im Format „`YYYY-MM-DD`“ eingegeben werden.
- **Eingeschränkte Apps:** Geben Sie den **App-Namen** und die **App Bundle-ID** für Apps ein, die eingeschränkt werden sollen. Wählen Sie **Hinzufügen** aus. Geräte mit mindestens einer installierten, eingeschränkten App werden als nicht konform gekennzeichnet.

Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern.

## <a name="locations"></a>Pfade

In Ihrer Richtlinie können Sie Konformität durch den Standort des Geräts erzwingen. Sie können vorhandene Standorte auswählen. Haben Sie noch keine Standorte? Unter [Verwenden von Standorten (Netzwerk-Fencing) in Intune](use-network-locations.md) erhalten Sie weitere Informationen.

1. Wählen Sie **Standorte** > **Standorte auswählen**.
2. Wählen Sie in der Liste Ihren Standort aus, und klicken Sie auf **Auswählen**.
3. **Speichern** Sie die Richtlinie.

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von Aktionen für nicht kompatible Geräte](actions-for-noncompliance.md) und [Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien](../fundamentals/scope-tags.md).
- [Überwachen Ihrer Konformitätsrichtlinien](compliance-policy-monitor.md).
- Siehe [Konformitätsrichtlinieneinstellungen für Android Enterprise](compliance-policy-create-android-for-work.md)-Geräte.
