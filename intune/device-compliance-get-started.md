---
title: Gerätekonformitätsrichtlinien in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Anforderungen für die Nutzung von Gerätekonformitätsrichtlinien, Übersicht über den Status und die Sicherheitsebenen, Verwendung des InGracePeriod-Status, Arbeiten mit bedingtem Zugriff, Handhabung von Geräten ohne zugewiesene Richtlinie und die Unterschiede bei der Konformität im Azure-Portal und im klassischen Portal in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2f599f168c1b4ae9aa94324b69ed11e6d426c86d
ms.sourcegitcommit: 4c18352d5b3b30080f7c7257fa63d852b1894850
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
---
# <a name="get-started-with-device-compliance-policies-in-intune"></a>Erste Schritte mit den Gerätekonformitätsrichtlinien in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Konformitätsanforderungen gehören zu den wesentlichen Regeln, wie die Notwendigkeit eines Geräte-PINs oder die Verschlüsselung. Gerätekonformitätsrichtlinien definieren diese Regeln und Einstellungen, die ein Gerät erfüllen muss, damit es als konform eingestuft wird. Diese Regeln beinhalten:

- Verwendung eines Kennworts für den Gerätezugriff

- Verschlüsselung

- Ermittlung, ob das Gerät mit Jailbreak oder Rooting manipuliert wurde

- Mindestens erforderliche Betriebssystemversion

- Maximal zulässige Betriebssystemversion

- Vorgabe, dass das Gerät höchstens die Mobile Threat Defense-Stufe aufweisen darf

Mithilfe von Kompatibilitätsrichtlinien können Sie den Kompatibilitätsstatus auf Ihren Geräten überwachen.

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="prerequisites"></a>Voraussetzungen
Folgendes ist erforderlich, um die Gerätekonformitätsrichtlinien zu verwenden:

- Verwenden Sie folgende Abonnements:

  - Intune
  - Azure Active Directory (AD) Premium

- Verwenden Sie eine unterstützte Plattform:

  - Android
  - iOS
  - macOS (Vorschau)
  - Windows 8.1
  - Windows Phone 8.1
  - Windows 10

- Geräte müssen in Intune registriert werden, um deren Konformitätsstatus melden zu können.

- Geräte, die für einen Benutzer oder ein Gerät ohne primären Benutzer registriert sind, werden unterstützt. Mehrere Benutzerkontexte werden nicht unterstützt.

## <a name="how-intune-device-compliance-policies-work-with-azure-ad"></a>So funktionieren Intune-Gerätekonformitätsrichtlinien mit Azure AD

Wenn ein Gerät in Intune registriert wird, beginnt der Azure AD-Registrierungsprozess, wodurch die Geräteattribute in Azure AD aktualisiert werden. Ein wichtiger Teil der Information ist der Gerätekonformitätsstatus. Dieser Gerätekonformitätsstatus wird von bedingten Zugriffsrichtlinien zum Blockieren oder Zulassen des Zugriffs auf E-Mails und andere Unternehmensressourcen verwendet.

Der [Azure AD-Registrierungsprozess](https://docs.microsoft.com/en-us/azure/active-directory/device-management-introduction) bietet mehr Informationen.

### <a name="assign-a-resulting-device-configuration-profile-status"></a>Zuweisen eines resultierenden Profilstatus für die Gerätekonfiguration

Wenn ein Gerät mehrere Konfigurationsprofile hat und es über verschiedene Konformitätsstatus für mindestens zwei zugeordnete Konfigurationsprofile verfügt, wird genau ein resultierender Konformitätsstaus zugewiesen. Diese Zuweisung basiert auf einem konzeptuellen Schweregrad, der den einzelnen Konformitätsstatus zugewiesen ist. Jeder Konformitätsstatus verfügt über den folgenden Schweregrad:

|Status  |Schweregrad  |
|---------|---------|
|Pending     |1|
|Succeeded     |2|
|Failed     |3|
|Fehler     |4|

Hat ein Gerät mehrere Konfigurationsprofile, so wird dem Gerät der höchste Schweregrad aller Profile zugewiesen.

Angenommen, ein Gerät verfügt z.B. über drei ihm zugewiesene Profile: einen Status „Ausstehend“ (Schweregrad = 1), einen Status „Erfolgreich“ (Schweregrad = 2) und einen Status „Fehler“ (Schweregrad = 4). Der Status „Fehler“ hat den höchsten Schweregrad, sodass alle drei Profile über den Konformitätsstatus „Fehler“ verfügen.

### <a name="assign-an-ingraceperiod-status"></a>Zuweisung eines InGracePeriod-Status

Der InGracePeriod-Status für eine Konformitätsrichtlinie ist ein Wert. Der Wert wird durch die Kombination der Toleranzzeit eines Geräts und dem tatsächlichen Status eines Geräts für diese Konformitätsrichtlinie ermittelt.

Im Detail bedeutet das: Wenn ein Gerät den Status „NonCompliant“ für eine zugewiesene Richtlinie aufweist und:

- dem Gerät keine Toleranzperiode zugewiesen ist, lautet der zugewiesene Wert für die Konformitätsrichtlinie „NonCompliant“.
- die Toleranzperiode des Geräts abgelaufen ist, lautet der zugewiesene Wert für die Konformitätsrichtlinie „NonCompliant“.
- die Toleranzperiode des Geräts erst in der Zukunft abläuft, lautet der zugewiesene Wert für die Konformitätsrichtlinie „InGracePeriod“.

In der folgenden Tabelle werden diese Punkte zusammengefasst:

|Tatsächlicher Konformitätsstatus|Wert der zugewiesenen Toleranzperiode|Effektiver Konformitätsstatus|
|---------|---------|---------|
|NonCompliant |Keine Toleranzperiode zugewiesen |NonCompliant |
|NonCompliant |Datum vom Vortag|NonCompliant|
|NonCompliant |Datum des folgenden Tages|InGracePeriod|

Weitere Informationen zum Überwachen der Richtlinien zur Gerätekonformität finden Sie unter [Überwachen von Intune-Richtlinien zur Gerätekonformität](compliance-policy-monitor.md).

### <a name="assign-a-resulting-compliance-policy-status"></a>Zuweisen eines resultierenden Konformitätsrichtlinienstatus

Wenn ein Gerät mehrere Konfigurationsprofile hat und es über verschiedene Konformitätsstatus für mindestens zwei zugeordnete Konformitätsprofile verfügt, wird genau ein resultierender Konformitätsstaus zugewiesen. Diese Zuweisung basiert auf einem konzeptuellen Schweregrad, der den einzelnen Konformitätsstatus zugewiesen ist. Jeder Konformitätsstatus verfügt über den folgenden Schweregrad:

|Status  |Schweregrad  |
|---------|---------|
|Unbekannt     |1|
|NotApplicable     |2|
|Kompatibel|3|
|InGracePeriod|4|
|NonCompliant|5|
|Fehler|6|

Hat ein Gerät mehrere Konformitätsrichtlinien, so wird dem Gerät der höchste Schweregrad aller Richtlinien zugewiesen.

Angenommen, einem Gerät sind z.B. drei Konformitätsrichtlinien zugewiesen: ein Status „Unbekannt“ (Schweregrad = 1), ein Status „Konform“ (Schweregrad = 3) und ein Status „InGracePeriod“ (Schweregrad = 4). Der Status „InGracePeriod“ hat den höchsten Schweregrad, sodass alle drei Richtlinien über den Konformitätsstatus „InGracePeriod“ verfügen.

## <a name="ways-to-use-device-compliance-policies"></a>Möglichkeiten, die Gerätekonformitätsrichtlinien zu verwalten

#### <a name="with-conditional-access"></a>Mit bedingten Zugriff
Geräten, welche die Richtlinienregeln einhalten, können Sie Zugriff auf E-Mail- und andere Unternehmensressourcen gewähren. Wenn die Geräte die Richtlinienregeln nicht einhalten, erhalten sie keinen Zugriff auf Unternehmensressourcen. Dies ist der bedingte Zugriff.

#### <a name="without-conditional-access"></a>Ohne bedingten Zugriff
Gerätekonformitätsrichtlinien können auch ohne einen bedingten Zugriff verwendet werden. Bei unabhängiger Nutzung von Kompatibilitätsrichtlinien werden die Zielgeräte ausgewertet und mit ihrem Kompatibilitätsstatus gemeldet. So können Sie beispielsweise einen Bericht dazu erstellen, wie viele Geräte nicht verschlüsselt sind oder mit Jailbreak oder Rootzugriff manipuliert wurden. Wenn Sie Kompatibilitätsrichtlinien ohne bedingten Zugriff nutzen, gelten keine Zugriffsbeschränkungen für Unternehmensressourcen.

## <a name="ways-to-deploy-device-compliance-policies"></a>Möglichkeiten, die Gerätekonformitätsrichtlinien bereitzustellen
Sie können Benutzern die Konformitätsrichtlinie in Benutzergruppen oder Geräten in Gerätegruppen bereitstellen. Wenn Sie eine Konformitätsrichtlinie für einen Benutzer bereitstellen, wird die Konformität aller Geräte des Benutzers überprüft.

Die **Einstellungen zur Konformitätsrichtlinie** (Azure-Portal > Gerätekonformität) enthalten Folgendes:

- **Kennzeichnen von Geräten, die keine Konformitätsrichtlinie zugewiesen haben, als:** Diese Eigenschaft verfügt über zwei Werte:

  - **Konform:** Sicherheitsfeature ist ausgeschaltet
  - **Nicht konform** (Standard): Sicherheitsfeature ist eingeschaltet

  Ist einem Gerät keine Konformitätsrichtlinie zugewiesen, dann wird dieses Gerät als nicht konform erachtet. Standardmäßig werden Geräte als **Nicht konform** gekennzeichnet. Wenn Sie den bedingten Zugriff verwenden, sollten Sie die Standardeinstellung **Nicht konform** beibehalten. Falls ein Benutzer nicht konform ist, da keine Richtlinie zugewiesen ist, führt das Unternehmensportal `No compliance policies have been assigned` auf.

- **Verbesserte Erkennung von Jailbreaks:** Ist diese Einstellung aktiviert, werden iOS-Geräte bei Intune regelmäßiger eingecheckt. Durch die Aktivierung dieser Eigenschaft werden die Ortungsdienste des Gerätes verwendet und der Akkuverbrauch wird beeinflusst. Die Ortungsdaten des Benutzers werden nicht bei Intune gespeichert.

  Für die Aktivierung dieser Einstellung müssen Geräte:
  - Ortungsdienste auf OS-Ebene aktivieren
  - dem Unternehmensportal erlauben, die Ortungsdienste zu nutzen
  - den Jailbreak-Status mindestens alle 72 Stunden bewerten und Intune melden. Andernfalls wird das Gerät als nicht konform gekennzeichnet.

- **Gültigkeitszeitraum des Kompatibilitätsstatus (in Tagen):** Geben Sie den Zeitraum ein, in dem die Geräte den Status für alle empfangenen Konformitätsrichtlinien meldet. Geräte, die innerhalb dieses Zeitraums keine Statusmeldung abgeben, werden als nicht konform behandelt. Der Standardwert ist 30 Tage.

Alle Geräte verfügen über eine **Standardrichtlinie für Gerätekonformität** (Azure-Portal > Gerätekonformität > Richtlinienkonformität). Verwenden Sie diese Standardrichtlinie, um diese Einstellungen zu überwachen.

Informationen darüber, wie lange es dauert, bis eine Richtlinie für mobile Geräte nach der Bereitstellung der Richtlinie abgerufen wird, finden Sie unter [Beheben von Problemen mit Profilen](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

Mit Konformitätsberichten können Sie den Status von Geräten überprüfen. Weitere Informationen finden Sie unter [Überwachen von Intune-Richtlinien zur Gerätekompatibilität](compliance-policy-monitor.md).

### <a name="actions-for-noncompliance"></a>Aktionen bei Inkompatibilität
Sie können eine zeitlich strukturierte Aktionsfolge für Geräte konfigurieren, die die Kriterien der Konformitätsrichtlinie nicht erfüllen. Diese Aktionen für Nichtkonformität können wie unter [Automatisieren von E-Mails und Hinzufügen von Aktionen für nicht konforme Geräte in Intune](actions-for-noncompliance.md) automatisiert werden.

## <a name="azure-classic-portal-vs-azure-portal"></a>Klassisches Azure-Portal im Vergleich mit dem Azure-Portal

Der Hauptunterschied bei der Verwendung von Gerätekonformitätsrichtlinien im Azure-Portal:

- Im Azure-Portal werden die Konformitätsrichtlinien separat für jede unterstützte Plattform erstellt.
- Im klassischen Azure-Portal wird eine Gerätekonformitätsrichtlinie für alle unterstützten Plattformen verwendet.

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

## <a name="device-compliance-policies-in-the-classic-portal-and-azure-portal"></a>Gerätekonformitätsrichtlinien im klassischen Portal und im Azure-Portal

Gerätekonformitätsrichtlinien, die im [klassischen Portal](https://manage.microsoft.com) erstellt wurden, erscheinen nicht im [Azure-Portal](https://portal.azure.com). Sie sind jedoch weiterhin für Benutzer bestimmt und können mithilfe des klassischen Portals verwaltet werden.

Sie müssen eine neue Gerätekonformitätsrichtlinien im Azure-Portal erstellen, um die Features für Gerätekonformität im Azure-Portal zu nutzen. Wenn Sie eine Gerätekonformitätsrichtlinie im Azure-Portal einem Benutzer zuweisen, dem auch eine Gerätekonformitätsrichtlinie aus dem klassischen Portal zugewiesen wurde, haben die Gerätekonformitätsrichtlinien aus dem Azure-Portal Vorrang vor denen, die im klassischen Portal erstellt wurden.

## <a name="next-steps"></a>Nächste Schritte

- Plattformspezifische Informationen zum Erstellen einer Gerätekonformitätsrichtlinie finden Sie hier:

  - [Android](compliance-policy-create-android.md)
  - [Android for Work](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Weitere Informationen zu den Richtlinienentitäten für Intune-Data Warehouse finden Sie unter [Reference for policy entities (Referenz für Richtlinienentitäten)](reports-ref-policy.md).
