---
title: 'Erstellen einer Konformitätsrichtlinie für Android Enterprise in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Erstellen oder konfigurieren Sie eine Microsoft Intune-Gerätekonformitätsrichtlinie für Geräte mit Android Enterprise oder Android-Arbeitsprofilgeräte. Wählen Sie, dass per Jailbreak manipulierte Geräte zulässig sind, legen Sie die zulässige Bedrohungsstufe fest, prüfen Sie auf Google Play, geben die minimale und maximale Betriebssystemversion an, wählen die Kennwortanforderungen, und lassen Sie Sideloading von Anwendungen zu.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a6f1f07c1cb7b5dbe81120fd678f429a996f230e
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566232"
---
# <a name="add-a-device-compliance-policy-for-android-enterprise-devices-in-intune"></a>Hinzufügen einer Gerätekonformitätsrichtlinie für Android Enterprise-Geräte in Intune

Konformitätsrichtlinien für Geräte sind ein wichtiges Feature bei der Verwendung von Intune, um die Ressourcen Ihrer Organisation zu schützen. In Intune können Sie Regeln und Einstellungen erstellen, die Geräte erfüllen müssen, um als konform angesehen zu werden, z.B. eine Kennwortlänge. Wenn das Gerät nicht konform ist, können Sie dann den Zugriff auf Daten und Ressourcen mit [bedingtem Zugriff](conditional-access.md) blockieren. 

Sie können auch Geräteberichte abrufen und Maßnahmen ergreifen, sollte das Gerät nicht konform sein, wie z.B. eine Benachrichtigungs-E-Mail an den Benutzer zu senden. Weitere Informationen über Konformitätsrichtlinien und alle Voraussetzungen finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

In diesem Artikel werden die Einstellungen aufgeführt, die Sie in einer Konformitätsrichtlinie für Geräte mit Android Enterprise verwenden können.

## <a name="non-compliance-and-conditional-access"></a>Nichtkonformität und bedingter Zugriff

In der folgenden Tabelle wird beschrieben, wie nicht konforme Einstellungen verwaltet werden, wenn eine Konformitätsrichtlinie mit einer Richtlinie für bedingten Zugriff verwendet wird.

--------------------------

|**Richtlinieneinstellung**| **Android Enterprise-Profil** |
| --- | --- |
| **PIN- oder Kennwortkonfiguration** |  Isoliert |
| **Geräteverschlüsselung** |  Isoliert |
| **Per Jailbreak oder Rootzugriff manipuliertes Gerät** | Unter Quarantäne gestellt (keine Einstellung) |
| **E-Mail-Profil** | Nicht verfügbar |
| **Minimale Version des Betriebssystems** | Isoliert |
| **Maximale Version des Betriebssystems** | Isoliert |
| **Windows-Integritätsnachweis** |Nicht verfügbar |

**Wiederhergestellt** = Das Betriebssystem des Geräts erzwingt die Kompatibilität. Beispiel: Der Benutzer ist gezwungen, eine PIN festzulegen.

**In Quarantäne**: Das Betriebssystem des Geräts erzwingt keine Konformität. Android-Geräte zwingen den Benutzer z.B. nicht dazu, das Gerät zu verschlüsseln. Wenn das Gerät nicht kompatibel ist, erfolgen die folgenden Aktionen:

  - Wenn eine Richtlinie für bedingten Zugriff für den Benutzer gilt, wird das Gerät blockiert.
  - Das Unternehmensportal benachrichtigt den Benutzer über Kompatibilitätsprobleme.

## <a name="create-a-device-compliance-policy"></a>Erstellen einer Gerätekonformitätsrichtlinie

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. Wählen Sie **Android Enterprise** als **Plattform** aus. 
5. Klicken Sie auf **Einstellungen konfigurieren**. Passen Sie die Einstellungen **Geräteintegrität**, **Geräteeigenschaften** und **Systemsicherheit** wie in diesem Artikel beschrieben an.

## <a name="device-health"></a>Device health

- **Geräte mit entfernten Nutzungsbeschränkungen:** Klicken Sie auf **Blockieren**, um Geräte mit Jailbreak oder entfernten Nutzungsbeschränkungen als nicht konform zu kennzeichnen. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Anfordern, dass das Gerät höchstens der angegebenen Gerätebedrohungsstufe entspricht**: Verwenden Sie diese Einstellung, um die Risikobewertung mit der Lookout MTP-Lösung als Konformitätsvoraussetzung zu fordern. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet. Wählen Sie die zulässige Bedrohungsstufe aus, um diese Einstellung zu verwenden:
  - **Gesichert**: Diese Option ist die sicherste und bedeutet, dass auf dem Gerät keine Bedrohungen vorhanden sein können. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als kompatibel bewertet, wenn nur Bedrohungen niedriger Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als kompatibel bewertet, wenn die auf dem Gerät gefundenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Hoch**: Dies ist die am wenigsten sichere Option, die alle Bedrohungsebenen zulässt. Es ist möglicherweise hilfreich, diese Lösung nur zu Berichtszwecken zu verwenden.
- **Google Play Services ist konfiguriert:** **Erfordert**, dass die Google Play Services-App installiert und aktiviert ist. Google Play Services ermöglicht Sicherheitsupdates und stellt eine grundlegende Abhängigkeit für viele Sicherheitsfunktionen auf zertifizierten Google-Geräten dar. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **Aktueller Sicherheitsanbieter:** **Erfordert**, dass ein aktueller Sicherheitsanbieter ein Gerät vor bekannten Sicherheitslücken schützen kann. Wenn Sie **Nicht konfiguriert** (Standardeinstellung) auswählen, wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.
- **SafetyNet-Gerätenachweis**: Legen Sie die Integritätsstufe des [SafetyNet-Nachweises](https://developer.android.com/training/safetynet/attestation.html) fest, die eingehalten werden muss. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standardeinstellung): Die Einstellung wird bei der Konformitätsprüfung nicht ausgewertet.
  - **Grundlegende Integrität prüfen**
  - **Grundlegende Integrität und zertifizierte Geräte prüfen**

#### <a name="threat-scan-on-apps"></a>Bedrohungsüberprüfung für Apps

Auf Android Enterprise-Geräten ist die Einstellung **Bedrohungsüberprüfung für Apps** eine Konfigurationsrichtlinie. Siehe [Einstellungen für Geräteeinschränkungen für Android Enterprise](device-restrictions-android-for-work.md).

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

Wenn Sie fertig sind, klicken Sie auf **OK** > **OK**, um die Änderungen zu speichern.

## <a name="actions-for-noncompliance"></a>Aktionen bei Inkompatibilität

Klicken Sie auf **Actions for noncompliance** (Aktionen bei Nichtkonformität). Die Standardaktion markiert das Gerät umgehend als nicht konform.

Sie können den Zeitplan anpassen, anhand dessen das Gerät als nicht konform markiert wird, z.B. nach einem Tag. Sie können auch eine zweite Aktion konfigurieren, durch die E-Mails an Benutzer gesendet werden, wenn das Gerät nicht mehr konform ist.

Weitere Informationen sowie Informationen zum Erstellen einer E-Mail-Benachrichtigung an Ihre Benutzer finden Sie unter [Hinzufügen von Aktionen für nicht konforme Geräte in Intune](actions-for-noncompliance.md).

## <a name="scope-tags"></a>Festlegen von Tags

Bereichsmarkierungen eignen sich zum Zuweisen von Richtlinien zu bestimmten Gruppen, z.B. Vertrieb, Engineering, Personalwesen usw. Sie können Bereichsmarkierungen zu Konformitätsrichtlinien hinzufügen. Weitere Informationen finden Sie unter [Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien](scope-tags.md). 

## <a name="assign-user-groups"></a>Zuweisen von Benutzergruppen

Eine erstellte Richtlinie bezweckt erst etwas, wenn Sie sie zuweisen. So weisen Sie die Richtlinie zu 

1. Wählen Sie eine Richtlinie, die Sie konfiguriert haben. Vorhandene Richtlinien befinden sich unter **Gerätekompatibilität** > **Richtlinien**.
2. Wählen Sie die Richtlinie und dann **Zuweisungen** aus. Sie können Azure Active Directory (AD)-Sicherheitsgruppen ein- oder ausschließen.
3. Wählen Sie **Ausgewählte Gruppen**, um Ihre Azure AD-Sicherheitsgruppen anzuzeigen. Wählen Sie die Benutzergruppen aus, auf die diese Richtlinie angewendet werden soll, und dann wählen Sie **Speichern**, um die Richtlinie für die Benutzer bereitzustellen.

Sie haben die Richtlinie auf Benutzer angewendet. Die von den Benutzern verwendeten Geräte, für die die Richtlinie gilt, werden auf Konformität überprüft.

## <a name="next-steps"></a>Nächste Schritte
[Automatisieren von E-Mails und Hinzufügen von Aktionen für nicht konforme Geräte](actions-for-noncompliance.md)  
[Überwachen von Intune-Richtlinien zur Gerätekompatibilität](compliance-policy-monitor.md)  
[Einstellungen für Kompatibilitätsrichtlinien für Android](compliance-policy-create-android.md)
