---
title: Erstellen einer Konformitätsrichtlinie für Android-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen oder Konfigurieren einer Microsoft Intune-Gerätekonformitätsrichtlinie für Android-Geräte. Wählen Sie, dass per Jailbreak manipulierte Geräte zulässig sind, legen Sie die zulässige Bedrohungsstufe fest, prüfen Sie auf Google Play, geben die minimale und maximale Betriebssystemversion an, wählen die Kennwortanforderungen, und lassen Sie Sideloading von Anwendungen zu.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2277da45ad1404269571f36dec0c16443409b39f
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744702"
---
# <a name="add-a-device-compliance-policy-for-android-devices-in-intune"></a>Hinzufügen einer Gerätekonformitätsrichtlinie für Android-Geräte in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Eine Intune-Konformitätsrichtlinie für Android-Geräte gibt die Regeln und Einstellungen an, die Android-Geräte erfüllen müssen, um als konform angesehen zu werden. Sie können diese Richtlinien mit bedingtem Zugriff verwenden, um den Zugriff auf Unternehmensressourcen zuzulassen oder zu blockieren. Außerdem können Sie Geräteberichte abrufen und bei Nichtkonformität Aktionen durchführen. Erstellen Sie Gerätekonformitätsrichtlinien für jede Plattform im Intune Azure-Portal. Weitere Informationen über Konformitätsrichtlinien und alle Voraussetzungen finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

In der folgenden Tabelle wird beschrieben, wie nicht konforme Einstellungen verwaltet werden, wenn eine Konformitätsrichtlinie mit einer Richtlinie für bedingten Zugriff verwendet wird.

--------------------

|**Richtlinieneinstellung**| **Android 4.0 und höher, Samsung KNOX Standard 4.0 und höher** |
| --- | ----|
| **PIN- oder Kennwortkonfiguration** |  Isoliert |
| **Geräteverschlüsselung** | Isoliert |
| **Per Jailbreak oder Rootzugriff manipuliertes Gerät** | Unter Quarantäne gestellt (keine Einstellung) |
| **E-Mail-Profil** | Nicht verfügbar |
| **Minimale Version des Betriebssystems** | Isoliert |
| **Maximale Version des Betriebssystems** |   Isoliert |
| **Windows-Integritätsnachweis** | Nicht verfügbar |

--------------------------

**Wiederhergestellt** = Das Betriebssystem des Geräts erzwingt die Kompatibilität. (Beispiel: Der Benutzer ist gezwungen, eine PIN festzulegen.)

**Isoliert** = Das Betriebssystem des Geräts erzwingt keine Kompatibilität. (Beispiel: Android-Geräte zwingen den Benutzer nicht, das Gerät zu verschlüsseln.) Wenn das Gerät nicht kompatibel ist, erfolgen die folgenden Aktionen:

- Das Gerät wird blockiert, wenn eine Richtlinie für bedingten Zugriff für den Benutzer gilt.
- Das Unternehmensportal benachrichtigt den Benutzer über Kompatibilitätsprobleme.

## <a name="create-a-device-compliance-policy"></a>Erstellen einer Gerätekonformitätsrichtlinie

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Wählen Sie als **Plattform** die Option **Android** aus. Wählen Sie **Einstellungen konfigurieren**, um die Einstellungen zu **Geräteintegrität**, **Geräteeigenschaften** und **Systemsicherheit** anzugeben. Wenn Sie fertig sind, wählen Sie **OK** und dann **Erstellen**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant based on the configured settings in this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **OK** when you are finished creating all the actions.--->

<!---##  Compliance policy settings--->

## <a name="device-health"></a>Device health

- **Geräte mit entfernten Nutzungsbeschränkungen**: Wenn Sie diese Einstellung aktivieren, werden Geräte mit Jailbreak als nicht konform bewertet.
- **Anfordern, dass das Gerät höchstens der angegebenen Gerätebedrohungsstufe entspricht**: Verwenden Sie diese Einstellung, um die Risikobewertung mit der Lookout MTP-Lösung als Konformitätsvoraussetzung zu fordern. Wählen Sie die maximal zulässige Bedrohungsstufe:
  - **Gesichert**: Diese Option ist die sicherste, da auf dem Gerät keine Bedrohungen vorhanden sein können. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als kompatibel bewertet, wenn nur Bedrohungen niedriger Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als kompatibel bewertet, wenn die auf dem Gerät vorhandenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht kompatibel bewertet.
  - **Hoch**: Dies ist die am wenigsten sichere Option, die alle Bedrohungsebenen zulässt. Es ist möglicherweise hilfreich, diese Lösung nur zu Berichtszwecken zu verwenden.
- **Google Play Services ist konfiguriert**: Erfordert, dass die Google Play Services-App installiert und aktiviert ist. Google Play Services ermöglicht Sicherheitsupdates und stellt eine grundlegende Abhängigkeit für viele Sicherheitsfunktionen auf zertifizierten Google-Geräten dar.
- **Aktueller Sicherheitsanbieter**: Erfordert, dass ein aktueller Sicherheitsanbieter ein Gerät vor bekannten Sicherheitslücken schützen kann.
- **Bedrohungsüberprüfung für Apps**: Erfordert, dass die Android-Funktion **Apps überprüfen** aktiviert wird.

  > [!NOTE]
  > Auf der älteren Android-Plattform ist diese Funktion eine Konformitätseinstellung. Intune kann nur prüfen, ob diese Einstellung auf Geräteebene aktiviert ist. Auf Geräten mit Arbeitsprofilen (Android for Work) ist diese Einstellung als Konfigurationsrichtlinieneinstellung zu finden. Dies ermöglicht Administratoren, die Einstellung für ein Gerät zu aktivieren.

  Wenn Ihr Unternehmen Android-Arbeitsprofile verwendet, können Sie **Bedrohungsüberprüfung für Apps** für Ihre registrierten Geräte aktivieren. Richten Sie ein Geräteprofil ein, und fordern Sie die Systemsicherheitseinstellung an. Weitere Informationen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android for Work-Geräte in Intune](device-restrictions-android-for-work.md).

- **SafetyNet-Gerätenachweis**: Legen Sie die Integritätsstufe des [SafetyNet-Nachweises](https://developer.android.com/training/safetynet/attestation.html) fest, die eingehalten werden muss. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert**
  - **Grundlegende Integrität prüfen**
  - **Grundlegende Integrität und zertifizierte Geräte prüfen**

## <a name="device-property-settings"></a>Einstellungen für Geräteeigenschaften

- **Minimale Betriebssystemversion:** Wenn ein Gerät die Anforderungen an die erforderliche Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht konform gemeldet. Ein Link mit Informationen zum Durchführen von Upgrades wird gezeigt. Der Endbenutzer kann ein Upgrade seines Geräts durchführen, und anschließend auf die Unternehmensressourcen zugreifen.
- **Maximale Version des Betriebssystems:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt. Der Benutzer wird dazu aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

## <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit

### <a name="password"></a>Kennwort

- **Kennwort zum Entsperren mobiler Geräte anfordern:** Klicken Sie auf **Erforderlich**, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können.
- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Benutzerkennwort enthalten muss.
- **Erforderlicher Kennworttyp**: Wählen Sie, ob ein Kennwort nur aus numerischen Zeichen oder aus einer Kombination aus Zahlen und anderen Zeichen bestehen soll. Es stehen die folgenden Optionen zur Auswahl:
  - **Gerätestandard**
  - **Biometrie auf niedriger Sicherheitsstufe**
  - **Mindestens numerisch**
  - **Numerisch komplex**: Sich wiederholende oder fortlaufende Ziffern wie „1111“ oder „1234“ sind nicht zulässig.
  - **Mindestens alphabetisch**
  - **Mindestens alphanumerisch**
  - **Mindestens alphanumerisch mit Symbolen**
- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.
- **Kennwortablauf (Tage)**: Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort des Benutzers abläuft und ein neues erstellen werden muss.
- **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl von zuletzt genutzten Kennwörtern an, die nicht erneut verwendet werden dürfen. Verwenden Sie diese Einstellung, um zu verhindern, dass der Benutzer zuvor verwendete Kennwörter erstellt.

### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung des Datenspeichers auf einem Gerät**: (Android 4.0 und höher, oder KNOX 4.0 und höher): Wählen Sie **Erforderlich**, um den Datenspeicher auf Ihren Geräten zu verschlüsseln. Wenn Sie die Einstellung **Kennwort zum Entsperren mobiler Geräte anfordern** auswählen, werden Geräte verschlüsselt.

### <a name="device-security"></a>Gerätesicherheit

- **Apps von unbekannten Quellen blockieren**: Wählen Sie diese Option, um Geräte mit Quellen zu blockieren, für die „Sicherheit > Unbekannte Quellen“ aktiviert ist (Android 4.0 - Android 7.x. Nicht von Android 8.0 und höher unterstützt). Für das Sideloading von Apps müssen unbekannte Quellen zugelassen werden. Wenn Sie kein Sideloading von Android-Apps durchführen, aktivieren Sie diese Konformitätsrichtlinie.

  > [!IMPORTANT]
  > Das Sideloading von Anwendungen erfordert, dass die Einstellung **Apps von unbekannten Quellen blockieren** aktiviert ist. Erzwingen Sie diese Kompatibilitätsrichtlinie nur, wenn Sie kein Sideloading von Android-Apps auf Geräten durchführen.

- **Laufzeitintegrität der Unternehmensportal-App**: Überprüft, ob die Unternehmensportal-App die Standard-Laufzeitumgebung installiert hat, ordnungsgemäß signiert ist, sich nicht im Debug-Modus befindet und von einer bekannten Quelle installiert wurde.
- **USB-Debugging auf Gerät blockieren** (Android 4.2 oder höher): Wählen Sie diese Option, um zu verhindern, dass Geräte die USB-Debuggingfunktion verwenden.
- **Mindestens erforderliche Sicherheitspatchebene** (Android 6.0 oder höher): Wählen Sie die älteste Sicherheitspatchebene, die ein Gerät haben kann. Geräte, die nicht mindestens diese Patchebene aufweisen, sind nicht kompatibel. Das Datum muss im Format „`YYYY-MM-DD`“ eingegeben werden.

## <a name="locations"></a>Pfade

Sie können in Ihrer Richtlinie vorhandene Standorte auswählen. Haben Sie noch keine Standorte? Unter [Use Locations (network fence) in Intune (Verwenden von Standorten in Intune)](use-network-locations.md) erhalten Sie weitere Informationen.

1. Klicken Sie auf **Select locations** (Standorte auswählen).
2. Wählen Sie aus Ihrer Liste Ihren Standort aus, und klicken Sie auf **Select** (Auswählen).
3. **Speichern** Sie die Richtlinie.
4. Klicken Sie auf **Actions for noncompliance** (Aktionen bei Nichtkonformität). Die Standardaktion markiert das Gerät umgehend als nicht konform. Diese Aktion wird ausgeführt, wenn Sie mindestens einen Standort auswählen und wenn das Gerät nicht mit dem ausgewählten Standort verbunden ist.

  Sie können diese Aktion anpassen, sodass der Zeitplan aktualisiert wird, wenn das Gerät als nicht konform markiert wird, z.B. nach einem Tag. Sie können auch eine zweite Aktion konfigurieren, durch die E-Mails an Benutzer gesendet werden, wenn das Gerät nicht mehr mit dem Standort konform ist.

## <a name="assign-user-groups"></a>Zuweisen von Benutzergruppen

1. Wählen Sie eine Richtlinie, die Sie konfiguriert haben. Vorhandene Richtlinien befinden sich unter **Gerätekompatibilität** > **Richtlinien**.
2. Wählen Sie die Richtlinie und dann **Zuweisungen** aus. Sie können Azure Active Directory (AD)-Sicherheitsgruppen ein- oder ausschließen.
3. Wählen Sie **Ausgewählte Gruppen**, um Ihre Azure AD-Sicherheitsgruppen anzuzeigen. Wählen Sie die Benutzergruppen aus, auf die diese Richtlinie angewendet werden soll, und dann wählen Sie **Speichern**, um die Richtlinie für die Benutzer bereitzustellen.

Sie haben die Richtlinie auf Benutzer angewendet. Die von den Benutzern verwendeten Geräte, denen die Richtlinie zugewiesen wurde, werden auf Konformität überprüft.

## <a name="next-steps"></a>Nächste Schritte
[Automatisieren von E-Mails und Hinzufügen von Aktionen für nicht konforme Geräte](actions-for-noncompliance.md)  
[Überwachen von Intune-Richtlinien zur Gerätekompatibilität](compliance-policy-monitor.md)