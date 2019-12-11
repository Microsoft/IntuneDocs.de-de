---
title: Hinzufügen von Mobile Threat Defense-Apps zu nicht registrierten Geräten
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Gerätebenutzer Mobile Threat Defense-Apps zu nicht registrierten Geräten hinzufügen können.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8dd7127594a0e23c85b9f8141ce6d398d9a447a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72794458"
---
# <a name="add-mobile-threat-defense-apps-to-unenrolled-devices"></a>Hinzufügen von Mobile Threat Defense-Apps zu nicht registrierten Geräten

Bei der Verwendung von Intune-App-Schutzrichtlinien mit Mobile Threat Defense führt Intune den Endbenutzer standardmäßig durch die Installation und Anmeldung bei allen erforderlichen Apps auf seinem Gerät, um die Verbindungen mit den relevanten Diensten zu ermöglichen.

Endbenutzer benötigen Microsoft Authenticator (iOS), um ihr Gerät zu registrieren, und Mobile Threat Defense (Android und iOS), um bei der Identifikation einer Bedrohung auf ihren mobilen Geräten eine Benachrichtigung und eine Anleitung zur Behebung der Bedrohungen zu erhalten.

Optional können Sie Intune auch zum Hinzufügen und Bereitstellen der Microsoft Authenticator- und Mobile Threat Defense-Apps (MTD) verwenden.

> [!NOTE] 
> Dieser Artikel gilt für alle Mobile Threat Defense-Partner, die App-Schutzrichtlinien unterstützen: Better Mobile (Android), Zimperium (iOS), Lookout for Work (Android/iOS).
> 
> Bei nicht registrierten Geräten **benötigen Sie keine iOS-App-Konfigurationsrichtlinie**, mit der die Mobile Threat Defense-App für iOS eingerichtet wird, die Sie mit Intune verwenden. Dies ist ein wichtiger Unterschied im Vergleich zu bei Intune-registrierten Geräten. 

## <a name="configure-microsoft-authenticator-for-ios-via-intune-optional"></a>Konfigurieren von Microsoft Authenticator für iOS über Intune (optional)
Bei der Verwendung von Intune-App-Schutzrichtlinien mit Mobile Threat Defense führt Intune den Endbenutzer durch die Installation, die Anmeldung und die Registrierung seines Geräts bei Microsoft Authenticator (iOS).

Wenn Sie die App jedoch über das Intune-Unternehmensportal für Endbenutzer verfügbar machen möchten, lesen Sie die Anweisungen unter [Hinzufügen von iOS Store-Apps zu Microsoft Intune](../apps/store-apps-ios.md). Verwenden Sie diese [iOS-App Store-URL der Microsoft Authenticator-App](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) wenn Sie den Abschnitt **Konfigurieren von App-Informationen** ausfüllen. Vergessen Sie als abschließenden Schritt nicht das [Zuweisen von Apps zu Gruppen mit Intune](../apps/apps-deploy.md).

> [!NOTE] 
> Für iOS-Geräte benötigen Sie [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to), damit Benutzer ihre Identitäten von Azure AD überprüfen lassen können. Das Intune-Unternehmensportal arbeitet als Broker auf Android-Geräten, damit Benutzer ihre Identitäten von Azure AD überprüfen lassen können.

## <a name="making-mobile-threat-defense-apps-available-via-intune-optional"></a>Verfügbarmachung von Mobile Threat Defense-Apps über Intune (optional)
Bei der Verwendung von Intune-App-Schutzrichtlinien mit Mobile Threat Defense führt Intune den Endbenutzer durch die Installation und die Anmeldung bei der erforderlichen Mobile Threat Defense-Client-App. 

Wenn Sie die App jedoch über das Intune-Unternehmensportal für Endbenutzer verfügbar machen möchten, können Sie die unten aufgeführten Schritte im [Azure-Portal](https://portal.azure.com/) ausführen. Stellen Sie sicher, dass Sie mit den folgenden Prozessen vertraut sind:

- [Hinzufügen von Apps in Microsoft Intune](../apps/apps-add.md)
- [Zuweisen einer App mit Intune](../apps/apps-deploy.md)

### <a name="making-lookout-for-work-available-to-end-users"></a>Verfügbarmachung von Lookout for Work für Endbenutzer
- **Android**  
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von Android Store-Apps zu Microsoft Intune](../apps/store-apps-android.md) an. Verwenden Sie diese [Play Store-URL der Lookout for Work-App](https://play.google.com/store/apps/details?id=com.lookout.enterprise), wenn Sie den Abschnitt **Konfigurieren von App-Informationen** ausfüllen.

- **iOS**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](../apps/store-apps-ios.md) an. Verwenden Sie diese [iOS-App Store-URL der Lookout for Work-App](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8), wenn Sie den Abschnitt **Konfigurieren von App-Informationen** ausfüllen.

<!-- ### Making Symantec Endpoint Protection Mobile available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). When completing the **Configure app information** section, use this [SEP Mobile app store URL](https://play.google.com/store/apps/details?id=com.skycure.skycure). For **Minimum operating system**, select **Android 4.0 (Ice Cream Sandwich)**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [SEP Mobile - App Store URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) when completing the **Configure app information** section.

### Making Check Point SandBlast Mobile available to end users
- **Android**  
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Check Point SandBlast Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) when completing the **Configure app information** section. 

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Check Point SandBlast Mobile - App Store URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) when completing the **Configure app information** section. -->

### <a name="making-zimperium-available-to-end-users"></a>Verfügbarmachung von Zimperium für Endbenutzer
<!-- - **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Zimperium - Play Store URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) when completing the **Configure app information** section. -->
- **iOS**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](../apps/store-apps-ios.md) an. Verwenden Sie diese [App Store-URL der Zimperium-App](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8), wenn Sie den Abschnitt **Konfigurieren von App-Informationen** ausfüllen.
 
<!-- ### Making Pradeo available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Pradeo - Play Store URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Pradeo - App Store URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) when completing the **Configure app information** section. -->

### <a name="making-better-mobile-available-to-end-users"></a>Verfügbarmachung von Better Mobile für Endbenutzer 
- **Android**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von Android Store-Apps zu Microsoft Intune](../apps/store-apps-android.md) an. Verwenden Sie diese [Play Store-URL der Active Shield-App](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise), wenn Sie den Abschnitt **Konfigurieren von App-Informationen** ausfüllen.
<!-- - **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) when completing the **Configure app information** section. -->

<!-- ### Making Sophos available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Sophos - Play Store URL](https://play.google.com/store/apps/details?id=com.sophos.smsec) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) when completing the **Configure app information** section.

### Making Wandera available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Wandera Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.wandera.android) when completing the **Configure app information** section. For **Minimum operating system**, select **Android 5.0**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Wandera Mobile - - App Store URL](https://itunes.apple.com/app/wandera/id605469330) when completing the **Configure app information** section. -->

## <a name="next-steps"></a>Nächste Schritte  

- [Aktivieren Sie den Mobile Threat Defense-Connector in Intune für nicht registrierte Geräte](~/protect/mtd-enable-unenrolled-devices.md)

