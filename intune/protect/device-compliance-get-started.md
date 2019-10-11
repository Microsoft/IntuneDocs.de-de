---
title: Gerätekonformitätsrichtlinien in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie Gerätekonformitätsrichtlinien, erhalten Sie eine Übersicht über Status- und die Sicherheitsebenen, verwenden Sie den InGracePeriod-Status, arbeiten Sie mit bedingtem Zugriff, verwalten Sie Geräte ohne zugewiesene Richtlinie, und erfahren Sie mehr zu den Unterschieden bei der Konformität im Azure-Portal und im klassischen Portal in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a743bb3b2003b1dbdf8088aca19bce898c8e40a8
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721421"
---
# <a name="set-rules-on-devices-to-allow-access-to-resources-in-your-organization-using-intune"></a>Legen Sie mit Intune Regeln auf Geräten fest, um Zugriff auf Ressourcen in Ihrer Organisation zu gewähren

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Viele MDM-Lösungen (Mobile Device Management) tragen zum Schutz von Unternehmensdaten bei, da Benutzer und Geräte bestimmte Anforderungen erfüllen müssen. In Intune wird dieses Feature „Konformitätsrichtlinien“ genannt. Konformitätsrichtlinien definieren Regeln und Einstellungen, die Benutzer und Geräte erfüllen müssen, um als „konform“ zu gelten. In Kombination mit dem bedingten Zugriff können Administratoren Benutzer und Geräte, die die Regeln nicht erfüllen, blockieren.

Beispielsweise kann die Intune-Administrator anfordern, dass:

- Endbenutzer zum Zugriff auf Organisationsdaten über mobile Geräte ein Kennwort verwenden.
- Das Gerät nicht mit Jailbreak oder Rootzugriff manipuliert wurde.
- Das Gerät eine minimale oder maximale Betriebssystemversion hat.
- Das Gerät höchstens einer angegebenen Gerätebedrohungsstufe entspricht

Außerdem können Sie diese Funktion verwenden, um den Konformitätsstatus von Geräten in Ihrer Organisation zu überwachen.

> [!IMPORTANT]
> Intune folgt bei allen Konformitätsauswertungen auf dem Gerät dem Zeitplan für das Einchecken von Geräten. [Richtlinien- und Profilaktualisierungszyklen](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) listet die geschätzten Aktualisierungszeiten auf.

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

Intune verwendet den [bedingten Zugriff](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) von Azure Active Directory (Azure AD), um Konformität zu erzwingen. Wenn ein Gerät in Intune registriert wird, beginnt der Azure AD-Registrierungsprozess, wodurch die Geräteinformationen in Azure AD aktualisiert werden. Ein wichtiger Teil der Information ist der Gerätekonformitätsstatus. Dieser Gerätekonformitätsstatus wird von Richtlinien für den bedingten Zugriff zum Blockieren oder Zulassen des Zugriffs auf E-Mails und andere Organisationsressourcen verwendet.

- Unter [Worum handelt es sich bei der Geräteverwaltung in Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/device-management-introduction) erhalten Sie weitere Informationen zur Registrierung von Geräten in Azure AD.

- Dieses Feature wird in den Artikeln zum [bedingten Zugriff](conditional-access.md) und zu [gängigen Vorgehensweisen zur Verwendung des bedingten Zugriffs](conditional-access-intune-common-ways-use.md) im Zusammenhang mit Intune beschrieben.

## <a name="ways-to-use-device-compliance-policies"></a>Möglichkeiten, die Gerätekonformitätsrichtlinien zu verwalten

### <a name="with-conditional-access"></a>Mit bedingtem Zugriff

Geräten, welche die Richtlinienregeln einhalten, können Sie Zugriff auf E-Mail- und andere Organisationsressourcen gewähren. Wenn die Geräte die Richtlinienregeln nicht einhalten, erhalten sie keinen Zugriff auf Organisationsressourcen. Dies ist der bedingte Zugriff.

### <a name="without-conditional-access"></a>Ohne bedingten Zugriff

Gerätekonformitätsrichtlinien können auch ohne einen bedingten Zugriff verwendet werden. Bei unabhängiger Nutzung von Kompatibilitätsrichtlinien werden die Zielgeräte ausgewertet und mit ihrem Kompatibilitätsstatus gemeldet. So können Sie beispielsweise einen Bericht dazu erstellen, wie viele Geräte nicht verschlüsselt sind oder mit Jailbreak oder Rootzugriff manipuliert wurden. Wenn Sie Kompatibilitätsrichtlinien ohne bedingten Zugriff nutzen, gelten keine Zugriffsbeschränkungen für Unternehmensressourcen.

## <a name="ways-to-deploy-device-compliance-policies"></a>Möglichkeiten, die Gerätekonformitätsrichtlinien bereitzustellen

Sie können Benutzern die Konformitätsrichtlinie in Benutzergruppen oder Geräten in Gerätegruppen bereitstellen. Wenn Sie eine Konformitätsrichtlinie für einen Benutzer bereitstellen, wird die Konformität aller Geräte des Benutzers überprüft. Auf Windows 10-Geräten mit Version 1803 und höher wird empfohlen, die Bereitstellung für Gerätegruppen vorzunehmen, *falls* der primärer Benutzer das Gerät nicht registriert hat. Die Verwendung von Gerätegruppen in diesem Szenario hilft beim Erstellen von Konformitätsberichten.

Intune umfasst zudem einige integrierte Konformitätsrichtlinieneinstellungen. Die folgenden integrierten Richtlinien werden auf allen Geräten ausgewertet, die in Intune registriert wurden:

- **Geräte ohne zugewiesene Konformitätsrichtlinie kennzeichnen als**: Diese Eigenschaft verfügt über zwei Werte:

  - **Konform** (Standard): Das Sicherheitsfeature ist deaktiviert.
  - **Nicht konform:** Das Sicherheitsfeature ist aktiviert

  Ist einem Gerät keine Konformitätsrichtlinie zugewiesen, dann wird dieses Gerät als standardmäßig konform erachtet. Wenn Sie den bedingten Zugriff mit Konformitätsrichtlinien verwenden, sollten Sie die Standardeinstellung auf **Nicht konform** festlegen. Falls ein Benutzer nicht konform ist, weil ihm keine Richtlinie zugewiesen ist, zeigt die [Unternehmensportal-App](../apps/company-portal-app.md) `No compliance policies have been assigned` an.

- **Verbesserte Erkennung von Jailbreaks**: Ist diese Einstellung aktiviert, werden iOS-Geräte bei Intune regelmäßiger eingecheckt. Durch die Aktivierung dieser Eigenschaft werden die Ortungsdienste des Gerätes verwendet und der Akkuverbrauch wird beeinflusst. Die Standortdaten des Benutzers werden nicht in Intune gespeichert.

  Für die Aktivierung dieser Einstellung müssen Geräte:
  - Ortungsdienste auf Betriebssystemebene aktivieren
  - dem Unternehmensportal erlauben, die Ortungsdienste zu nutzen
  - den Jailbreak-Status mindestens alle 72 Stunden bewerten und Intune melden. Andernfalls wird das Gerät als nicht konform gekennzeichnet. Sie können den Auswertungsvorgang auslösen, indem Sie die Unternehmensportal-App öffnen oder indem Sie das Gerät an einem anderen Ort positionieren, der mindestens 500 m entfernt ist. Wenn das Gerät nicht innerhalb von 72 Stunden um 500 Meter verlagert wird, muss der Benutzer die Unternehmensportal-App für eine erweiterte Bewertung des Jailbreak-Status öffnen.

- **Gültigkeitszeitraum des Konformitätsstatus (Tage)** : Geben Sie den Zeitraum an, in dem Geräte den Status für alle empfangenen Konformitätsrichtlinien melden müssen. Geräte, die innerhalb dieses Zeitraums keine Statusmeldung abgeben, werden als nicht konform behandelt. Der Standardwert beträgt 30 Tage.

Sie können die integrierten Richtlinien verwenden, um diese Einstellungen zu überwachen. Intune wird außerdem je nach Geräteplattform in regelmäßigen Abständen [aktualisiert oder sucht nach Updates](create-compliance-policy.md#refresh-cycle-times). Unter [Häufig auftretende Probleme und Lösungen für Geräteprofile in Microsoft Intune](../configuration/device-profile-troubleshoot.md) finden Sie weitere Informationen.

Mit Konformitätsberichten können Sie den Status von Geräten überprüfen. Weitere Informationen finden Sie unter [Überwachen von Intune-Richtlinien zur Gerätekompatibilität](compliance-policy-monitor.md).

## <a name="non-compliance-and-conditional-access-on-the-different-platforms"></a>Nichtkonformität und bedingter Zugriff auf unterschiedlichen Plattformen

In der folgenden Tabelle wird beschrieben, wie nicht konforme Einstellungen verwaltet werden, wenn eine Konformitätsrichtlinie mit einer Richtlinie für bedingten Zugriff verwendet wird.

---------------------------

|**Richtlinieneinstellung**| **Plattform** |
| --- | ----|
| **PIN- oder Kennwortkonfiguration** | - **Android 4.0 und höher:** Isoliert</br>- **Samsung Knox Standard 4.0 und höher:** Isoliert</br>- **Android Enterprise:** Isoliert</br></br>- **iOS 8.0 oder höher:** Wiederhergestellt</br>- **macOS 10.11 und höher:** Wiederhergestellt</br></br>- **Windows 8.1 und höher:** Wiederhergestellt</br>- **Windows Phone 8.1 oder höher:** Wiederhergestellt|
| **Geräteverschlüsselung** | - **Android 4.0 und höher:** Isoliert</br>- **Samsung Knox Standard 4.0 und höher:** Isoliert</br>- **Android Enterprise:** Isoliert</br></br>- **iOS 8.0 oder höher:** Wiederhergestellt (durch Festlegen der PIN)</br>- **macOS 10.11 und höher:** Wiederhergestellt (durch Festlegen der PIN)</br></br>- **Windows 8.1 und höher:** Nicht verfügbar</br>- **Windows Phone 8.1 oder höher:** Wiederhergestellt |
| **Per Jailbreak oder Rootzugriff manipuliertes Gerät** | - **Android 4.0 und höher:** Unter Quarantäne gestellt (keine Einstellung)</br>- **Samsung Knox Standard 4.0 und höher:** Unter Quarantäne gestellt (keine Einstellung)</br>- **Android Enterprise:** Unter Quarantäne gestellt (keine Einstellung)</br></br>- **iOS 8.0 oder höher:** Unter Quarantäne gestellt (keine Einstellung)</br>- **macOS 10.11 und höher:** Nicht verfügbar</br></br>- **Windows 8.1 und höher:** Nicht verfügbar</br>- **Windows Phone 8.1 oder höher:** Nicht verfügbar |
| **E-Mail-Profil** | - **Android 4.0 und höher:** Nicht verfügbar</br>- **Samsung Knox Standard 4.0 und höher:** Nicht verfügbar</br>- **Android Enterprise:** Nicht verfügbar</br></br>- **iOS 8.0 oder höher:** Isoliert</br>- **macOS 10.11 und höher:** Isoliert</br></br>- **Windows 8.1 und höher:** Nicht verfügbar</br>- **Windows Phone 8.1 oder höher:** Nicht verfügbar |
| **Minimale Version des Betriebssystems** | - **Android 4.0 und höher:** Isoliert</br>- **Samsung Knox Standard 4.0 und höher:** Isoliert</br>- **Android Enterprise:** Isoliert</br></br>- **iOS 8.0 oder höher:** Isoliert</br>- **macOS 10.11 und höher:** Isoliert</br></br>- **Windows 8.1 und höher:** Isoliert</br>- **Windows Phone 8.1 oder höher:** Isoliert |
| **Maximale Version des Betriebssystems** | - **Android 4.0 und höher:** Isoliert</br>- **Samsung Knox Standard 4.0 und höher:** Isoliert</br>- **Android Enterprise:** Isoliert</br></br>- **iOS 8.0 oder höher:** Isoliert</br>- **macOS 10.11 und höher:** Isoliert</br></br>- **Windows 8.1 und höher:** Isoliert</br>- **Windows Phone 8.1 oder höher:** Isoliert |
| **Windows-Integritätsnachweis** | - **Android 4.0 und höher:** Nicht verfügbar</br>- **Samsung Knox Standard 4.0 und höher:** Nicht verfügbar</br>- **Android Enterprise:** Nicht verfügbar</br></br>- **iOS 8.0 oder höher:** Nicht verfügbar</br>- **macOS 10.11 und höher:** Nicht verfügbar</br></br>- **Windows 10 und Windows 10 Mobile:** Isoliert</br>- **Windows 8.1 und höher:** Isoliert</br>- **Windows Phone 8.1 oder höher:** Nicht verfügbar |

---------------------------

**Bereinigt:** Das Betriebssystem des Geräts erzwingt die Konformität. Beispiel: Der Benutzer ist gezwungen, eine PIN festzulegen.

**In Quarantäne:** Das Betriebssystem des Geräts erzwingt keine Konformität. Android- und Android Enterprise-Geräte zwingen den Benutzer z. B. nicht dazu, das Gerät zu verschlüsseln. Wenn das Gerät nicht kompatibel ist, erfolgen die folgenden Aktionen:

- Wenn eine Richtlinie für bedingten Zugriff für den Benutzer gilt, wird das Gerät blockiert.
- Die Unternehmensportal-App benachrichtigt den Benutzer über Konformitätsprobleme.

## <a name="azure-classic-portal-vs-azure-portal"></a>Klassisches Azure-Portal im Vergleich mit dem Azure-Portal

Der Hauptunterschied bei der Verwendung von Gerätekonformitätsrichtlinien im Azure-Portal:

- Im Azure-Portal werden die Konformitätsrichtlinien separat für jede unterstützte Plattform erstellt.
- Im klassischen Azure-Portal wird eine Gerätekonformitätsrichtlinie für alle unterstützten Plattformen verwendet.

<!--- - In the Azure portal, you have the ability to specify actions and notifications that are initiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

- In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

Gerätekonformitätsrichtlinien, die im [klassischen Portal](https://manage.microsoft.com) erstellt wurden, erscheinen nicht im [Azure-Portal](https://portal.azure.com). Sie sind jedoch weiterhin für Benutzer bestimmt und können mithilfe des klassischen Portals verwaltet werden.

Sie müssen eine neue Gerätekonformitätsrichtlinien im Azure-Portal erstellen, um die Features für Gerätekonformität im Azure-Portal zu nutzen. Wenn Sie eine Gerätekonformitätsrichtlinie im Azure-Portal einem Benutzer zuweisen, dem auch eine Gerätekonformitätsrichtlinie aus dem klassischen Portal zugewiesen wurde, haben die Gerätekonformitätsrichtlinien aus dem Azure-Portal Vorrang vor denen, die im klassischen Portal erstellt wurden.

## <a name="next-steps"></a>Nächste Schritte

- [Erstellen Sie eine Richtlinie](create-compliance-policy.md), und sehen Sie sich die Anforderungen an.
- In den Konformitätseinstellungen für die unterschiedlichen Geräteplattformen finden Sie weitere Informationen:

  - [Android](compliance-policy-create-android.md)
  - [Android Enterprise](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows 10 und höher](compliance-policy-create-windows.md)
  - [Windows Holographic for Business](compliance-policy-create-windows.md#windows-holographic-for-business)
  - [Windows 8.1 und Windows Phone 8.1](compliance-policy-create-windows-8-1.md)

- Weitere Informationen zu den Intune-Richtlinienentitäten für Data Warehouses finden Sie unter [Reference for policy entities (Referenz für Richtlinienentitäten)](../reports-ref-policy.md).
