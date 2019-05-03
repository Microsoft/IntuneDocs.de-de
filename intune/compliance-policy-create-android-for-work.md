---
title: Android Enterprise-Geräteeinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Eine Liste mit allen Einstellungen, mit denen Sie beim Festlegen von Kompatibilität für Ihre Android Enterprise-Geräte in Microsoft Intune angezeigt. Kennwortregeln festlegen, wählen Sie eine minimale oder maximale Betriebssystemversion, bestimmte apps beschränken, verhindert die Wiederverwendung von Kennwort und vieles mehr.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 16db0acab84a1095c40e9a92648c75c2581187cd
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423559"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>So markieren Geräte als kompatibel oder nicht kompatibel mit Intune Einstellungen für Android Enterprise

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Dieser Artikel enthält und beschreibt die verschiedenen Einstellungen, die Sie auf Android Enterprise-Geräte in Intune konfigurieren können. Verwenden Sie im Rahmen Ihrer Lösung für mobile Geräte (MDM) diese Einstellungen sind Geräte mit entfernten nutzungsbeschränkungen (mit jailbreak) als nicht kompatibel markieren, eine zulässige Bedrohungsstufe festlegen, das Aktivieren von Google Play Protect und vieles mehr.

Diese Funktion gilt für:

- Android Enterprise

Verwenden Sie als Intune-Administrator diesen Complianceeinstellungen zum Schutz der Ressourcen Ihrer Organisation ein. Weitere Informationen über Konformitätsrichtlinien und alle Voraussetzungen finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen einer Konformitätsrichtlinie](create-compliance-policy.md#create-the-policy) Wählen Sie **Android Enterprise** als **Plattform** aus.

## <a name="device-health"></a>Device health

- **Geräte mit entfernten Nutzungsbeschränkungen:** Klicken Sie auf **Blockieren**, um Geräte mit Jailbreak oder entfernten Nutzungsbeschränkungen als nicht konform zu kennzeichnen. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Anfordern, dass das Gerät höchstens der angegebenen Gerätebedrohungsstufe entspricht**: Verwenden Sie diese Einstellung, um die Risikobewertung mit der Lookout MTP-Lösung als Konformitätsvoraussetzung zu fordern. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet. Wählen Sie die zulässige Bedrohungsstufe aus, um diese Einstellung zu verwenden:
  - **Gesichert**: Diese Option ist die sicherste und bedeutet, dass auf dem Gerät keine Bedrohungen vorhanden sein können. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als kompatibel bewertet, wenn nur Bedrohungen niedriger Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als kompatibel bewertet, wenn die auf dem Gerät gefundenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Hoch**: Dies ist die am wenigsten sichere Option, die alle Bedrohungsebenen zulässt. Es ist möglicherweise hilfreich, diese Lösung nur zu Berichtszwecken zu verwenden.

### <a name="google-play-protect"></a>Google Play-Schutz

- **Google Play Services ist konfiguriert:** **Erfordert**, dass die Google Play Services-App installiert und aktiviert ist. Google Play Services ermöglicht Sicherheitsupdates und stellt eine grundlegende Abhängigkeit für viele Sicherheitsfunktionen auf zertifizierten Google-Geräten dar. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Aktueller Sicherheitsanbieter:** **Erfordert**, dass ein aktueller Sicherheitsanbieter ein Gerät vor bekannten Sicherheitslücken schützen kann. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **SafetyNet-Gerätenachweis**: Legen Sie die Integritätsstufe des [SafetyNet-Nachweises](https://developer.android.com/training/safetynet/attestation.html) fest, die eingehalten werden muss. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standardeinstellung): Die Einstellung wird bei der Konformitätsprüfung nicht ausgewertet.
  - **Grundlegende Integrität prüfen**
  - **Grundlegende Integrität und zertifizierte Geräte prüfen**

> [!NOTE]
> Auf Android Enterprise-Geräten **bedrohungsüberprüfung für apps** ist eine Richtlinie für die Gerätekonfiguration. Administratoren können mithilfe einer Richtlinie, die Einstellung auf einem Gerät aktivieren. Siehe [Einstellungen für Geräteeinschränkungen für Android Enterprise](device-restrictions-android-for-work.md).

## <a name="device-properties-settings"></a>Einstellungen für Geräteeigenschaften

- **Minimale Betriebssystemversion:** Wenn ein Gerät die Anforderungen an die erforderliche Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht konform gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann ein Upgrade des Geräts ausführen, und anschließend auf die Unternehmensressourcen zugreifen.
- **Maximale Version des Betriebssystems:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt. Zudem wird der Benutzer dazu aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

## <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit

### <a name="password"></a>Kennwort

- **Kennwort zum Entsperren mobiler Geräte anfordern:** Klicken Sie auf **Erforderlich**, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet. Diese Einstellung wird auf Geräteebene angewendet. Wenn Sie nur ein Kennwort auf Arbeitsprofilebene anfordern müssen, verwenden Sie eine Konfigurationsrichtlinie. Siehe [Gerätekonfigurationseinstellungen für Android Enterprise](device-restrictions-android-for-work.md).
- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Benutzerkennwort enthalten muss.
- **Erforderlicher Kennworttyp:** Wählen Sie aus, ob ein Kennwort nur aus numerischen Zeichen oder aus einer Kombination aus Zahlen und anderen Zeichen bestehen soll. Folgende Optionen sind verfügbar:
  - **Gerätestandard**
  - **Biometrie auf niedriger Sicherheitsstufe**
  - **Mindestens numerisch** (Standard)
  - **Numerisch, komplex**
  - **Mindestens alphabetisch**
  - **Mindestens alphanumerisch**
  - **Mindestens alphanumerisch mit Symbolen**

- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort abläuft und ein neues erstellt werden muss.
- **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl von zuletzt genutzten Kennwörtern an, die nicht erneut verwendet werden dürfen. Verwenden Sie diese Einstellung, um zu verhindern, dass der Benutzer zuvor verwendete Kennwörter erstellt.

### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung des Datenspeichers auf einem Gerät**: Wählen Sie **Erforderlich**, um den Datenspeicher auf Ihren Geräten zu verschlüsseln. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet. 

  Diese Einstellung muss nicht konfiguriert werden, da Android-Arbeitsprofilgeräte eine Verschlüsselung erzwingen.

### <a name="device-security"></a>Gerätesicherheit

- **Apps von unbekannten Quellen blockieren:** Wählen Sie diese Option aus, um Geräte mit Quellen zu **blockieren**, für die „Sicherheit > Unbekannte Quellen“ aktiviert ist (dies wird für Android 4.0 bis Android 7.x unterstützt, ab Android 8.0 jedoch nicht mehr). Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

  Für das Sideloading von Apps müssen unbekannte Quellen zugelassen werden. Wenn Sie kein Sideloading von Android-Apps durchführen, legen Sie für dieses Feature **Blockieren** fest, um diese Konformitätsrichtlinie zu aktivieren. 

  > [!IMPORTANT]
  > Das Sideloading von Anwendungen erfordert, dass die Einstellung **Apps von unbekannten Quellen blockieren** aktiviert ist. Erzwingen Sie diese Konformitätsrichtlinie nur, wenn Sie kein Sideloading von Android-Apps auf Geräten durchführen.

  Sie müssen diese Einstellung nicht konfigurieren, da Android-Arbeitsprofilgeräte die Installation aus unbekannten Quellen stets einschränken.

- **Laufzeitintegrität der Unternehmensportal-App:** Legen Sie **Erforderlich** fest, um zu überprüfen, ob die Unternehmensportal-App alle der folgenden Anforderungen erfüllt:

  - Die Standardlaufzeitumgebung ist installiert.
  - Die App ist ordnungsgemäß signiert.
  - Die App befindet sich nicht im Debug-Modus.
  - Die App wurde aus einer bekannten Quelle installiert.

  Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

- **USB-Debugging auf dem Gerät blockieren**: Wählen Sie **Blockieren** aus, um zu verhindern, dass Geräte das USB-Debuggingfeature verwenden. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

  Sie müssen diese Einstellungen nicht konfigurieren, da USB-Debuggen auf Android-Arbeitsprofilgeräten bereits deaktiviert ist.

- **Mindestens erforderliche Sicherheitspatchebene**: Wählen Sie die älteste Sicherheitspatchebene, die ein Gerät haben kann. Geräte, die nicht mindestens diese Patchebene aufweisen, sind nicht konform. Das Datum muss im Format *JJJJ-MM-TT* eingegeben werden.

Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern.

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von Aktionen für nicht kompatible Geräte](actions-for-noncompliance.md) und [bereichsmarkierungen Filter-Richtlinien verwenden](scope-tags.md).
- [Überwachen Sie Ihre Compliance-Richtlinien](compliance-policy-monitor.md).
- [Einstellungen für Kompatibilitätsrichtlinien für Android-Geräte](compliance-policy-create-android.md)
