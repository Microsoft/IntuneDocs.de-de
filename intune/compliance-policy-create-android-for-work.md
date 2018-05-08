---
title: Erstellen einer Android for Work-Konformitätsrichtlinie in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen oder konfigurieren Sie eine Microsoft Intune-Gerätekonformitätsrichtlinie für Android for Work-Geräte. Wählen Sie, dass per Jailbreak manipulierte Geräte zulässig sind, legen Sie die zulässige Bedrohungsstufe fest, prüfen Sie auf Google Play, geben die minimale und maximale Betriebssystemversion an, wählen die Kennwortanforderungen, und lassen Sie Sideloading von Anwendungen zu.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 74fe0897764957e84e5a13944305221cc85bd8c7
ms.sourcegitcommit: 2773f388f50654366197a95a6838306f70fc18b8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="add-a-device-compliance-policy-for-android-for-work-devices-in-intune"></a>Hinzufügen einer Gerätekonformitätsrichtlinie für Android for Work-Geräte in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Eine Konformitätsrichtlinie für Android for Work-Geräte in Intune gibt die Regeln und Einstellungen an, die diese Geräte erfüllen müssen, um als konform angesehen zu werden. Sie können diese Richtlinien mit bedingtem Zugriff verwenden, um den Zugriff auf Unternehmensressourcen zuzulassen oder zu blockieren. Außerdem können Sie Geräteberichte abrufen und bei Nichtkonformität Aktionen durchführen. Erstellen Sie Gerätekonformitätsrichtlinien für unterschiedliche Plattformen im Intune Azure-Portal. Weitere Informationen über Konformitätsrichtlinien und alle Voraussetzungen finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

In der folgenden Tabelle wird beschrieben, wie nicht konforme Einstellungen verwaltet werden, wenn eine Konformitätsrichtlinie mit einer Richtlinie für bedingten Zugriff verwendet wird.

--------------------------

|**Richtlinieneinstellung**| **Android for Work** |
| --- | --- |
| **PIN- oder Kennwortkonfiguration** |  Isoliert |
| **Geräteverschlüsselung** |  Isoliert |
| **Per Jailbreak oder Rootzugriff manipuliertes Gerät** | Unter Quarantäne gestellt (keine Einstellung) |
| **E-Mail-Profil** | Nicht verfügbar |
| **Minimale Version des Betriebssystems** | Isoliert |
| **Maximale Version des Betriebssystems** | Isoliert |
| **Windows-Integritätsnachweis** |Nicht verfügbar |

**Wiederhergestellt** = Das Betriebssystem des Geräts erzwingt die Kompatibilität. (Beispiel: Der Benutzer ist gezwungen, eine PIN festzulegen.)+

**Isoliert** = Das Betriebssystem des Geräts erzwingt keine Kompatibilität. (Beispiel: Android-Geräte zwingen den Benutzer nicht, das Gerät zu verschlüsseln.) Wenn das Gerät nicht kompatibel ist, erfolgen die folgenden Aktionen:

- Wenn eine Richtlinie für bedingten Zugriff für den Benutzer gilt, wird das Gerät blockiert.
- Das Unternehmensportal benachrichtigt den Benutzer über Kompatibilitätsprobleme.

## <a name="create-a-device-compliance-policy"></a>Erstellen einer Gerätekonformitätsrichtlinie

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Wählen Sie **Android for Work** als **Plattform** aus. Wählen Sie **Einstellungen konfigurieren**, um die Einstellungen zu **Geräteintegrität**, **Geräteeigenschaften** und **Systemsicherheit** anzugeben. Wenn Sie fertig sind, wählen Sie **OK** und dann **Erstellen**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="device-health"></a>Device health

- **Geräte mit entfernten Nutzungsbeschränkungen**: Wenn Sie diese Einstellung aktivieren, werden Geräte mit Jailbreak als nicht konform bewertet.
- **Anfordern, dass das Gerät höchstens der angegebenen Gerätebedrohungsstufe entspricht**: Verwenden Sie diese Einstellung, um die Risikobewertung mit der Lookout MTP-Lösung als Konformitätsvoraussetzung zu fordern. Wählen Sie die maximal zulässige Bedrohungsstufe:
  - **Gesichert**: Diese Option ist die sicherste und bedeutet, dass auf dem Gerät keine Bedrohungen vorhanden sein können. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als kompatibel bewertet, wenn nur Bedrohungen niedriger Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als kompatibel bewertet, wenn die auf dem Gerät gefundenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht kompatibel bewertet.
  - **Hoch**: Dies ist die am wenigsten sichere Option, die alle Bedrohungsebenen zulässt. Es ist möglicherweise hilfreich, diese Lösung nur zu Berichtszwecken zu verwenden.
- **Google Play Services ist konfiguriert**: Erfordert, dass die Google Play Services-App installiert und aktiviert ist. Google Play Services ermöglicht Sicherheitsupdates und stellt eine grundlegende Abhängigkeit für viele Sicherheitsfunktionen auf zertifizierten Google-Geräten dar.
- **Aktueller Sicherheitsanbieter**: Erfordert, dass ein aktueller Sicherheitsanbieter ein Gerät vor bekannten Sicherheitslücken schützen kann.
- **SafetyNet-Gerätenachweis**: Legen Sie die Integritätsstufe des [SafetyNet-Nachweises](https://developer.android.com/training/safetynet/attestation.html) fest, die eingehalten werden muss. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert**
  - **Grundlegende Integrität prüfen**
  - **Grundlegende Integrität und zertifizierte Geräte prüfen**

#### <a name="threat-scan-on-apps"></a>Bedrohungsüberprüfung für Apps

Auf Geräten mit Arbeitsprofilen (Android for Work) ist die Einstellung **Bedrohungsüberprüfung für Apps** als Konfigurationsrichtlinieneinstellung zu finden. Administratoren können die Einstellung für ein Gerät aktivieren.

Wenn Ihr Unternehmen Android-Arbeitsprofile verwendet, können Sie **Bedrohungsüberprüfung für Apps** für Ihre registrierten Geräte aktivieren. Richten Sie ein Geräteprofil ein, und fordern Sie die Systemsicherheitseinstellung an. Weitere Informationen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android for Work-Geräte in Intune](device-restrictions-android-for-work.md).

## <a name="device-property-settings"></a>Einstellungen für Geräteeigenschaften

- **Minimale Betriebssystemversion:** Wenn ein Gerät die Anforderungen an die erforderliche Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht konform gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann ein Upgrade des Geräts ausführen, und anschließend auf die Unternehmensressourcen zugreifen.
- **Maximale Version des Betriebssystems:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt. Zudem wird der Benutzer dazu aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

## <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit

### <a name="password"></a>Kennwort

- **Kennwort zum Entsperren mobiler Geräte anfordern:** Klicken Sie auf **Erforderlich**, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können.
- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Benutzerkennwort enthalten muss.
- **Erforderlicher Kennworttyp**: Wählen Sie diese Option, wenn ein Kennwort nur aus numerischen Zeichen bestehen soll, oder wenn eine Kombination aus Zahlen und anderen Zeichen verwendet werden soll. Es stehen die folgenden Optionen zur Auswahl:
  - **Gerätestandard**
  - **Biometrie auf niedriger Sicherheitsstufe**
  - **Mindestens numerisch**
  - **Numerisch, komplex**
  - **Mindestens alphabetisch**
  - **Mindestens alphanumerisch**
  - **Mindestens alphanumerisch mit Symbolen**
- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.
- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort abläuft und ein neues erstellt werden muss.
- **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl von zuletzt genutzten Kennwörtern an, die nicht erneut verwendet werden dürfen. Verwenden Sie diese Einstellung, um zu verhindern, dass der Benutzer zuvor verwendete Kennwörter erstellt.

### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung auf mobilen Geräten erforderlich:** Diese Einstellung muss nicht konfiguriert werden, da Android for Work-Geräte eine Verschlüsselung erzwingen.

### <a name="device-security"></a>Gerätesicherheit

- **Apps von unbekannten Quellen blockieren**: Sie müssen diese Einstellung nicht konfigurieren, da Android for Work-Geräte die Installation aus unbekannten Quellen stets einschränken.
- **Laufzeitintegrität der Unternehmensportal-App**: Überprüft, ob die Unternehmensportal-App die Standard-Laufzeitumgebung installiert hat, ordnungsgemäß signiert ist, sich nicht im Debug-Modus befindet und von einer bekannten Quelle installiert wurde.
- **USB-Debugging auf Gerät blockieren**: Sie müssen diese Einstellungen nicht konfigurieren, da USB-Debuggen auf Android for Work-Geräten bereits deaktiviert ist.
- **Mindestens erforderliche Sicherheitspatchebene**: Wählen Sie die älteste Sicherheitspatchebene, die ein Gerät haben kann. Geräte, die nicht mindestens diese Patchebene aufweisen, sind nicht kompatibel. Das Datum muss im Format „`YYYY-MM-DD`“ eingegeben werden.

## <a name="assign-user-groups"></a>Zuweisen von Benutzergruppen

1. Wählen Sie eine Richtlinie, die Sie konfiguriert haben. Vorhandene Richtlinien befinden sich unter **Gerätekompatibilität** > **Richtlinien**.
2. Wählen Sie die Richtlinie und dann **Zuweisungen** aus. Sie können Azure Active Directory (AD)-Sicherheitsgruppen ein- oder ausschließen.
3. Wählen Sie **Ausgewählte Gruppen**, um Ihre Azure AD-Sicherheitsgruppen anzuzeigen. Wählen Sie die Benutzergruppen aus, auf die diese Richtlinie angewendet werden soll, und dann wählen Sie **Speichern**, um die Richtlinie für die Benutzer bereitzustellen.

Sie haben die Richtlinie auf Benutzer angewendet. Die von den Benutzern verwendeten Geräte, denen die Richtlinie zugewiesen wurde, werden auf Konformität überprüft.

## <a name="next-steps"></a>Nächste Schritte
[Automatisieren von E-Mails und Hinzufügen von Aktionen für nicht konforme Geräte](actions-for-noncompliance.md)  
[Überwachen von Intune-Richtlinien zur Gerätekompatibilität](compliance-policy-monitor.md)