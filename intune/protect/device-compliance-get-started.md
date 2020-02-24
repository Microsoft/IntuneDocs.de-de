---
title: Gerätekonformitätsrichtlinien in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie Gerätekonformitätsrichtlinien, erhalten Sie eine Übersicht über Status- und Sicherheitsebenen, verwenden Sie den InGracePeriod-Status, arbeiten Sie mit bedingtem Zugriff, und verwalten Sie Geräte ohne zugewiesene Richtlinie.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/13/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 867873c78b34d5573084a3a6e44d7d4d67846423
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413643"
---
# <a name="set-rules-on-devices-to-allow-access-to-resources-in-your-organization-using-intune"></a>Legen Sie mit Intune Regeln auf Geräten fest, um Zugriff auf Ressourcen in Ihrer Organisation zu gewähren

Viele MDM-Lösungen (Mobile Device Management) tragen zum Schutz von Unternehmensdaten bei, da Benutzer und Geräte bestimmte Anforderungen erfüllen müssen. In Intune wird dieses Feature „Konformitätsrichtlinien“ genannt. Konformitätsrichtlinien definieren Regeln und Einstellungen, die Benutzer und Geräte erfüllen müssen, um als „konform“ zu gelten. In Kombination mit dem bedingten Zugriff können Administratoren Benutzer und Geräte blockieren, die die Regeln nicht erfüllen.

Beispielsweise kann der Intune-Administrator anfordern, dass:

- Endbenutzer zum Zugriff auf Organisationsdaten über mobile Geräte ein Kennwort verwenden.
- Das Gerät nicht mit Jailbreak oder Rootzugriff manipuliert wurde.
- Das Gerät eine minimale oder maximale Betriebssystemversion hat.
- Das Gerät höchstens einer angegebenen Gerätebedrohungsstufe entspricht

Außerdem können Sie diese Funktion verwenden, um den Konformitätsstatus von Geräten in Ihrer Organisation zu überwachen.

> [!IMPORTANT]
> Intune folgt bei allen Konformitätsauswertungen auf dem Gerät dem Zeitplan für das Einchecken von Geräten. Unter [Richtlinien- und Profilaktualisierungszyklen](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) werden die geschätzten Aktualisierungszeiten aufgeführt.

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

- When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

- 3 days after initial noncompliance state, a follow up reminder is sent to the user.

- 5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

- 7 days after initial noncompliance state, access to company resources is blocked. This requires that you have Conditional Access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement Conditional Access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="device-compliance-policies-work-with-azure-ad"></a>Gerätekonformitätsrichtlinien mit Azure AD

Intune verwendet den [bedingten Zugriff](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) von Azure Active Directory, um die Konformität zu erzwingen. Wenn ein Gerät in Intune registriert wird, beginnt der Azure AD-Registrierungsprozess, wodurch die Geräteinformationen in Azure AD aktualisiert werden. Ein wichtiger Teil der Information ist der Gerätekonformitätsstatus. Dieser Gerätekonformitätsstatus wird von Richtlinien für den bedingten Zugriff zum Blockieren oder Zulassen des Zugriffs auf E-Mails und andere Organisationsressourcen verwendet.

- Unter [Worum handelt es sich bei der Geräteverwaltung in Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/device-management-introduction) erhalten Sie weitere Informationen zur Registrierung von Geräten in Azure AD.

- Dieses Feature wird in den Artikeln zum [bedingten Zugriff](conditional-access.md) und zu [gängigen Vorgehensweisen zur Verwendung des bedingten Zugriffs](conditional-access-intune-common-ways-use.md) im Zusammenhang mit Intune beschrieben.

## <a name="ways-to-use-device-compliance-policies"></a>Möglichkeiten, die Gerätekonformitätsrichtlinien zu verwalten

### <a name="with-conditional-access"></a>Mit bedingtem Zugriff

Geräten, welche die Richtlinienregeln einhalten, können Sie Zugriff auf E-Mail- und andere Organisationsressourcen gewähren. Wenn die Geräte die Richtlinienregeln nicht einhalten, erhalten sie keinen Zugriff auf Organisationsressourcen. Dies ist der bedingte Zugriff.

### <a name="without-conditional-access"></a>Ohne bedingten Zugriff

Sie können Gerätekonformitätsrichtlinien auch ohne bedingten Zugriff verwenden. Bei unabhängiger Nutzung von Kompatibilitätsrichtlinien werden die Zielgeräte ausgewertet und mit ihrem Kompatibilitätsstatus gemeldet. So können Sie beispielsweise einen Bericht dazu erstellen, wie viele Geräte nicht verschlüsselt sind oder mit Jailbreak oder Rootzugriff manipuliert wurden. Wenn Sie Kompatibilitätsrichtlinien ohne bedingten Zugriff nutzen, gelten keine Einschränkungen für den Zugriff auf Unternehmensressourcen.

## <a name="ways-to-deploy-device-compliance-policies"></a>Möglichkeiten, die Gerätekonformitätsrichtlinien bereitzustellen

Sie können Benutzern die Konformitätsrichtlinie in Benutzergruppen oder Geräten in Gerätegruppen bereitstellen. Wenn Sie eine Konformitätsrichtlinie für einen Benutzer bereitstellen, wird die Konformität aller Geräte des Benutzers überprüft. Auf Windows 10-Geräten mit Version 1803 und höher wird empfohlen, die Bereitstellung für Gerätegruppen vorzunehmen, *falls* der primärer Benutzer das Gerät nicht registriert hat. Die Verwendung von Gerätegruppen in diesem Szenario hilft beim Erstellen von Konformitätsberichten.

Intune umfasst zudem einige integrierte Konformitätsrichtlinieneinstellungen. Die folgenden integrierten Richtlinien werden auf allen Geräten ausgewertet, die in Intune registriert wurden:

- **Geräte ohne zugewiesene Konformitätsrichtlinie kennzeichnen als**: Diese Eigenschaft verfügt über zwei Werte:

  - **Konform** (*Standard*): Das Sicherheitsfeature ist nicht aktiviert
  - **Nicht konform:** Das Sicherheitsfeature ist aktiviert

  Ist einem Gerät keine Konformitätsrichtlinie zugewiesen, dann wird dieses Gerät standardmäßig als konform erachtet. Wenn Sie den bedingten Zugriff mit Konformitätsrichtlinien verwenden, sollten Sie die Standardeinstellung auf **Nicht konform** festlegen. Falls ein Benutzer nicht konform ist, weil ihm keine Richtlinie zugewiesen ist, zeigt die [Unternehmensportal-App](../apps/company-portal-app.md)`No compliance policies have been assigned` an.


> [!NOTE]
> Die erweiterte Jailbreakerkennung für iOS-Geräte wurde in Intune vorübergehend deaktiviert.

- **Verbesserte Erkennung von Jailbreaks**: Ist diese Einstellung aktiviert, werden iOS-Geräte bei Intune regelmäßiger eingecheckt. Durch die Aktivierung dieser Eigenschaft werden die Ortungsdienste des Gerätes verwendet und der Akkuverbrauch wird beeinflusst. Die Standortdaten des Benutzers werden nicht in Intune gespeichert.

  Für die Aktivierung dieser Einstellung müssen Geräte:
  - Ortungsdienste auf Betriebssystemebene aktivieren
  - dem Unternehmensportal erlauben, die Ortungsdienste zu nutzen
  - den Jailbreak-Status mindestens alle 72 Stunden bewerten und Intune melden. Andernfalls wird das Gerät als nicht konform gekennzeichnet. Sie können den Auswertungsvorgang auslösen, indem Sie die Unternehmensportal-App öffnen oder indem Sie das Gerät an einem anderen Ort positionieren, der mindestens 500 m entfernt ist. Wenn das Gerät nicht innerhalb von 72 Stunden um 500 Meter verlagert wird, muss der Benutzer die Unternehmensportal-App für eine erweiterte Bewertung des Jailbreak-Status öffnen.

- **Gültigkeitszeitraum des Konformitätsstatus (Tage)** : Geben Sie den Zeitraum an, in dem Geräte den Status für alle empfangenen Konformitätsrichtlinien melden müssen. Geräte, die innerhalb dieses Zeitraums keine Statusmeldung abgeben, werden als nicht konform behandelt. Der Standardwert beträgt 30 Tage. Der Mindestwert ist 1 Tag.

  Diese Einstellung wird als Standardkompatibilitäts-Richtlinie **Ist aktiv** (**Geräte** > **Überwachen** > **Einstellungskompatibilität**) angezeigt. Die Hintergrundaufgabe für diese Richtlinie wird einmal täglich ausgeführt.

Sie können die integrierten Richtlinien verwenden, um diese Einstellungen zu überwachen. Intune wird außerdem je nach Geräteplattform in regelmäßigen Abständen [aktualisiert oder sucht nach Updates](create-compliance-policy.md#refresh-cycle-times). Unter [Häufig auftretende Probleme und Lösungen für Geräteprofile in Microsoft Intune](../configuration/device-profile-troubleshoot.md) finden Sie weitere Informationen.

Mit Konformitätsberichten können Sie den Status von Geräten überprüfen. Weitere Informationen finden Sie unter [Überwachen von Intune-Richtlinien zur Gerätekompatibilität](compliance-policy-monitor.md).

## <a name="non-compliance-and-conditional-access-on-the-different-platforms"></a>Nichtkonformität und bedingter Zugriff auf unterschiedlichen Plattformen

In der folgenden Tabelle wird beschrieben, wie nicht konforme Einstellungen verwaltet werden, wenn eine Konformitätsrichtlinie mit einer Richtlinie für bedingten Zugriff verwendet wird.

---------------------------

|**Richtlinieneinstellung**| **Plattform** |
| --- | ----|
| **PIN- oder Kennwortkonfiguration** | - **Android 4.0 und höher:** Isoliert<br>- **Samsung Knox Standard 4.0 und höher:** Isoliert<br>- **Android Enterprise:** Isoliert  <br>  <br>- **iOS 8.0 oder höher:** Wiederhergestellt<br>- **macOS 10.11 und höher:** Wiederhergestellt  <br>  <br>- **Windows 8.1 und höher:** Wiederhergestellt<br>- **Windows Phone 8.1 oder höher:** Wiederhergestellt|
| **Geräteverschlüsselung** | - **Android 4.0 und höher:** Isoliert<br>- **Samsung Knox Standard 4.0 und höher:** Isoliert<br>- **Android Enterprise:** Isoliert<br><br>- **iOS 8.0 oder höher:** Wiederhergestellt (durch Festlegen der PIN)<br>- **macOS 10.11 und höher:** Wiederhergestellt (durch Festlegen der PIN)<br><br>- **Windows 8.1 und höher:** Nicht zutreffend<br>- **Windows Phone 8.1 oder höher:** Wiederhergestellt |
| **Per Jailbreak oder Rootzugriff manipuliertes Gerät** | - **Android 4.0 und höher:** Unter Quarantäne gestellt (keine Einstellung)<br>- **Samsung Knox Standard 4.0 und höher:** Unter Quarantäne gestellt (keine Einstellung)<br>- **Android Enterprise:** Unter Quarantäne gestellt (keine Einstellung)<br><br>- **iOS 8.0 oder höher:** Unter Quarantäne gestellt (keine Einstellung)<br>- **macOS 10.11 und höher:** Nicht zutreffend<br><br>- **Windows 8.1 und höher:** Nicht zutreffend<br>- **Windows Phone 8.1 oder höher:** Nicht zutreffend |
| **E-Mail-Profil** | - **Android 4.0 und höher:** Nicht zutreffend<br>- **Samsung Knox Standard 4.0 und höher:** Nicht zutreffend<br>- **Android Enterprise:** Nicht zutreffend<br><br>- **iOS 8.0 oder höher:** Isoliert<br>- **macOS 10.11 und höher:** Isoliert<br><br>- **Windows 8.1 und höher:** Nicht zutreffend<br>- **Windows Phone 8.1 oder höher:** Nicht zutreffend |
| **Minimales Release des Betriebssystems** | - **Android 4.0 und höher:** Isoliert<br>- **Samsung Knox Standard 4.0 und höher:** Isoliert<br>- **Android Enterprise:** Isoliert<br><br>- **iOS 8.0 oder höher:** Isoliert<br>- **macOS 10.11 und höher:** Isoliert<br><br>- **Windows 8.1 und höher:** Isoliert<br>- **Windows Phone 8.1 oder höher:** Isoliert |
| **Maximales Release des Betriebssystems** | - **Android 4.0 und höher:** Isoliert<br>- **Samsung Knox Standard 4.0 und höher:** Isoliert<br>- **Android Enterprise:** Isoliert<br><br>- **iOS 8.0 oder höher:** Isoliert<br>- **macOS 10.11 und höher:** Isoliert<br><br>- **Windows 8.1 und höher:** Isoliert<br>- **Windows Phone 8.1 oder höher:** Isoliert |
| **Windows-Integritätsnachweis** | - **Android 4.0 und höher:** Nicht zutreffend<br>- **Samsung Knox Standard 4.0 und höher:** Nicht zutreffend<br>- **Android Enterprise:** Nicht zutreffend<br><br>- **iOS 8.0 oder höher:** Nicht zutreffend<br>- **macOS 10.11 und höher:** Nicht zutreffend<br><br>- **Windows 10 und Windows 10 Mobile:** Isoliert<br>- **Windows 8.1 und höher:** Isoliert<br>- **Windows Phone 8.1 oder höher:** Nicht zutreffend |

---------------------------

**Bereinigt:** Das Betriebssystem des Geräts erzwingt die Konformität. Es ist z.B. erforderlich, dass der Benutzer eine PIN festlegt.

**In Quarantäne:** Das Betriebssystem des Geräts erzwingt keine Konformität. Android- und Android Enterprise-Geräte zwingen den Benutzer z. B. nicht dazu, das Gerät zu verschlüsseln. Wenn das Gerät nicht kompatibel ist, erfolgen die folgenden Aktionen:

- Wenn eine Richtlinie für bedingten Zugriff für den Benutzer gilt, wird das Gerät blockiert.
- Die Unternehmensportal-App benachrichtigt den Benutzer über Konformitätsprobleme.

## <a name="next-steps"></a>Nächste Schritte

- [Erstellen Sie eine Richtlinie](create-compliance-policy.md), und sehen Sie sich die Anforderungen an.
- In den Konformitätseinstellungen für die unterschiedlichen Geräteplattformen finden Sie weitere Informationen:

  - [Android](compliance-policy-create-android.md)
  - [Android Enterprise](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows Holographic for Business](compliance-policy-create-windows.md#windows-holographic-for-business)
  - [Windows Phone 8.1](compliance-policy-create-windows-8-1.md)
  - [Windows 8.1 und höher](compliance-policy-create-windows-8-1.md)
  - [Windows 10 und höher](compliance-policy-create-windows.md)

- Weitere Informationen zu den Intune-Richtlinienentitäten für Data Warehouses finden Sie unter [Reference for policy entities (Referenz für Richtlinienentitäten)](../reports-ref-policy.md).
