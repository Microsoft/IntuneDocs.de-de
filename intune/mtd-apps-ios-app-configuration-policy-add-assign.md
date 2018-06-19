---
title: Hinzufügen und Zuweisen von MTD-Apps mit Microsoft Intune
titleSuffix: ''
description: Hinzufügen von Mobile Threat Defense-Apps (MTD), der Microsoft Authenticator-App und der iOS-Konfigurationsrichtlinie im Azure-Portal mit Intune
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 10502f82d94246f7a70af6b88c0704a4daa0372b
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2018
ms.locfileid: "32046382"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Hinzufügen und Zuweisen von Mobile Threat Defense-Apps (MTD) mit Intune

> [!NOTE] 
> Dieses Thema gilt für alle Mobile Threat Defense-Partner.

Sie können Intune verwenden, um MTD-Apps hinzuzufügen und bereitzustellen, damit Endbenutzer Benachrichtigungen über auf ihren mobilen Geräten erkannte Bedrohungen sowie eine Anleitung zur Behebung der Bedrohungen erhalten können.

Für iOS-Geräte benötigen Sie [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to), damit Benutzer ihre Identitäten von Azure AD überprüfen lassen können. Sie benötigen zusätzlich die iOS-App-Konfigurationsrichtlinie, die die MTD-iOS-App anweist, Intune zu verwenden.

> [!TIP]
> Das Intune-Unternehmensportal arbeitet als Broker auf Android-Geräten, damit Benutzer ihre Identitäten von Azure AD überprüfen lassen können.

## <a name="before-you-begin"></a>Vorbereitung

-   Die unten beschriebenen Schritte müssen in der [Azure-Portal](https://portal.azure.com/) durchgeführt werden.

-   Stellen Sie sicher, dass Sie mit den folgenden Prozessen vertraut sind:

    -   [Hinzufügen von Apps in Microsoft Intune](apps-add.md)

    -   [Hinzufügen von iOS-Apps mit Konfigurationsrichtlinien in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)

    -   [Zuweisen einer App mit Intune](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune)

    -   [Hinzufügen einer iOS-App-Konfigurationsrichtlinien](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)

## <a name="to-add-apps"></a>So fügen Sie Apps hinzu

### <a name="all-mtd-partners"></a>Alle MTD-Partner

#### <a name="microsoft-authenticator-app-for-ios"></a>Microsoft Authenticator-App für iOS

- Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](store-apps-ios.md) an. Verwenden Sie diese [Store-URL der Microsoft Authenticator-App](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) für **Schritt 12** im Abschnitt **Konfigurieren von App-Informationen**.

### <a name="lookout"></a>Lookout

#### <a name="android"></a>Android
- Sehen Sie sich die Anleitungen für [das Hinzufügen von Android Store-Apps zu Microsoft Intune](store-apps-android.md) an. Verwenden Sie diese [Store-URL der Lookout for Work-Google-App](https://play.google.com/store/apps/details?id=com.lookout.enterprise) in **Schritt 7**.

#### <a name="ios"></a>iOS

- Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](store-apps-ios.md) an. Verwenden Sie diese [Store-URL der Lookout for Work-iOS-App](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) für **Schritt 12** im Abschnitt **Konfigurieren von App-Informationen**.

#### <a name="lookout-for-work-app-outside-the-apple-store"></a>Lookout for Work-App außerhalb des Apple Store

Sie müssen nun die Lookout for Work-App für iOS erneut signieren. Lookout verteilt die Lookout for Work-App für iOS außerhalb von iOS App Store. Bevor Sie die App verteilen, müssen Sie die App mit Ihrem iOS Enterprise Developer Certificate neu signieren.

Ausführliche Anweisungen zum erneuten Signieren der Lookout for Work-Apps für iOS finden Sie unter [iOS App Re-Signing Process (Erneute Signatur bei iOS-Apps)](https://personal.support.lookout.com/hc/articles/114094038714) auf der Lookout-Website.

##### <a name="enable-azure-ad-authentication-for-lookout-for-work-ios-app"></a>Aktivieren der Azure AD-Authentifizierung für die Lookout for Work-iOS-App

Aktivieren Sie die Azure Active Directory-Authentifizierung für iOS-Benutzer, indem Sie folgendermaßen vorgehen:

1. Wechseln Sie zum [Azure-Portal](https://portal.azure.com), melden Sie sich mit Ihren Anmeldeinformationen an, und navigieren Sie zur Seite „Anwendungen“.

2. Fügen Sie die **Lookout for Work iOS-App** als eine **native Clientanwendung** hinzu.

3. Ersetzen Sie **com.lookout.enterprise.yourcompanyname** mit der Kundenbundle-ID, die Sie beim Unterzeichnen der IPA ausgewählt haben.

4.  Hinzufügen von zusätzlichen Umleitungs-URI: **&lt;companyportal://code/>** gefolgt von einer URL-codierten Version Ihrer ursprünglichen URI-Umleitung.

5.  Fügen Sie **Delegierte Berechtigungen** zu Ihrer App hinzu.

    > [!NOTE] 
    > Weitere Informationen finden Sie unter [Konfigurieren Sie eine native Clientanwendung](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).

##### <a name="add-the-lookout-for-work-ipa-file"></a>Hinzufügen der IPA-Datei für Lookout for Work

- Laden Sie die neu signierte IPA-Datei hoch, wie im Thema [Hinzufügen von branchenspezifischen iOS-Apps in Microsoft Intune](lob-apps-ios.md) beschrieben. Sie müssen auch iOS 8.0 oder höher als die mindestens erforderliche Betriebssystemversion festlegen.

### <a name="symantec-endpoint-protection-mobile-sep-mobile"></a>Symantec Endpoint Protection Mobile (SEP Mobile)

#### <a name="android"></a>Android

- Sehen Sie sich die Anleitungen für [das Hinzufügen von Android Store-Apps zu Microsoft Intune](store-apps-android.md) an. Verwenden Sie in **Schritt 7** diese [SEP Mobile-App-Store-URL](https://play.google.com/store/apps/details?id=com.skycure.skycure).  Wählen Sie für **Mindestens erforderliches Betriebssystem** die Option **Android 4.0 (Ice Cream Sandwich)** aus.

#### <a name="ios"></a>iOS

- Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](store-apps-ios.md) an. Verwenden Sie diese [SEP Mobile-App-Store-URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) in **Schritt 12** im Abschnitt **Konfigurieren von App-Informationen**.

### <a name="check-point-sandblast-mobile"></a>Check Point SandBlast Mobile

#### <a name="android"></a>Android

- Sehen Sie sich die Anleitungen für [das Hinzufügen von Android Store-Apps zu Microsoft Intune](store-apps-android.md) an. Verwenden Sie diese [Store-URL der Check Point SandBlast Mobile-App](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) in **Schritt 7**.

#### <a name="ios"></a>iOS

- Wenden Sie sich an [Check Point SandBlast Mobile](https://www.checkpoint.com/products/sandblast-mobile/), um die iOS-App zu erhalten. Sehen Sie sich die Anweisungen zum [Hinzufügen von iOS Store-Apps zu Microsoft Intune](store-apps-ios.md) an, und verwenden Sie anschließend die Apple Store-URL in **Schritt 12** im Abschnitt **Konfigurieren von App-Informationen**.

### <a name="zimperium"></a>Zimperium

#### <a name="android"></a>Android

- Sehen Sie sich die Anleitungen für [das Hinzufügen von Android Store-Apps zu Microsoft Intune](store-apps-android.md) an. Verwenden Sie diese [URL des Zimperium-App Stores](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) in **Schritt 7**.

#### <a name="ios"></a>iOS

- Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](store-apps-ios.md) an. Verwenden Sie diese [URL des Zimperium-App Stores](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) in **Schritt 12** im Abschnitt **Konfigurieren von App-Informationen**.

## <a name="to-associate-the-mtd-app-with-an-ios-app-configuration-policy"></a>So ordnen Sie die MTD-App einer iOS-App-Konfigurationsrichtlinie zu

### <a name="for-lookout"></a>Für Lookout

- Erstellen Sie die iOS-App-Konfigurationsrichtlinie wie im Thema [zur Verwendung der iOS-App-Konfigurationsrichtlinie](app-configuration-policies-use-ios.md) beschrieben.

### <a name="for-sep-mobile"></a>Für SEP Mobile

-   Verwenden Sie dasselbe Azure AD-Konto, das zuvor in der [Symantec Endpoint Protection-Verwaltungskonsole](https://aad.skycure.com) konfiguriert wurde. Dabei sollte es sich um das Konto handeln, mit dem Sie sich beim klassischen Intune-Portal anmelden.

-   Sie müssen die iOS-App-Konfigurationsrichtlinie **herunterladen**. 
    -   Wechseln Sie zur [Symantec Endpoint Protection-Verwaltungskonsole](https://aad.skycure.com), und melden Sie sich mit Ihren Anmeldeinformationen an.

    -   Wechseln Sie zu **Einstellungen**, und wählen Sie unter **Integrationen** die Option **Intune** aus. Wählen Sie **EMM Integration Selection** (EMM-Integrationsauswahl) aus. Wählen Sie **Microsoft** aus, und speichern Sie Ihre Auswahl.

    -   Klicken Sie auf den Link **Integration setup files** (Integrationssetupdateien), und speichern Sie die generierte \*.zip-Datei. Die ZIP-Datei enthält die Datei „***.plist**“, die zum Erstellen der iOS-App-Konfigurationsrichtlinie in Intune verwendet wird.

    -   In den Anweisungen für [die Verwendung der iOS-App-Konfigurationsrichtlinien von Microsoft Intune](app-configuration-policies-use-ios.md) erfahren Sie, wie Sie die iOS-App-Konfigurationsrichtlinie für SEP Mobile hinzufügen.

    - Verwenden Sie in **Schritt 8** die Option **XML-Daten eingeben**, kopieren Sie den Inhalt aus der Datei „***.plist**“, und fügen Sie den Inhalt in den Text der Konfigurationsrichtlinie ein.

> [!NOTE]
> Wenn Sie die Dateien nicht abrufen können, wenden Sie sich an den [Symantec Endpoint Protection Mobile Enterprise Support](https://support.symantec.com/en_US/contact-support.html).

### <a name="for-check-point-sandblast-mobile"></a>Für Check Point SandBlast Mobile

- In den Anweisungen für [die Verwendung der iOS-App-Konfigurationsrichtlinien von Microsoft Intune](app-configuration-policies-use-ios.md) erfahren Sie, wie Sie die iOS-App-Konfigurationsrichtlinie für Check Point SandBlast Mobile hinzufügen.
    - Verwenden Sie in **Schritt 8** die Option **XML-Daten eingeben**, kopieren Sie den nachstehenden Inhalt, und fügen Sie den diesen in den Text der Konfigurationsrichtlinie ein.

```
<dict><key>MDM</key><string>INTUNE</string></dict>
```

### <a name="for-zimperium"></a>Für Zimperium

- In den Anweisungen für [die Verwendung der iOS-App-Konfigurationsrichtlinien von Microsoft Intune](app-configuration-policies-use-ios.md) erfahren Sie, wie Sie die iOS-App-Konfigurationsrichtlinie für Zimperium hinzufügen.
    - Verwenden Sie in **Schritt 8** die Option **XML-Daten eingeben**, kopieren Sie den nachstehenden Inhalt, und fügen Sie den diesen in den Text der Konfigurationsrichtlinie ein.

```
<dict>
<key>provider</key><string>Intune</string>
<key>userprincipalname</key><string>{{userprincipalname}}</string>
<key>deviceid</key>
<string>{{deviceid}}</string>
<key>serialnumber</key>
<string>{{serialnumber}}</string>
<key>udidlast4digits</key>
<string>{{udidlast4digits}}</string>
</dict>
```

## <a name="to-assign-apps-all-mtd-partners"></a>So weisen Sie Apps zu (Alle MTD-Partner)

- Anweisungen hierzu finden Sie im Thema [Zuweisen von Apps zu Gruppen mit Microsoft Intune](apps-deploy.md).

## <a name="next-steps"></a>Nächste Schritte

- [Erstellen einer Mobile Threat Defense-Gerätekompatibilitätsrichtlinie (MTD) mit Intune](mtd-device-compliance-policy-create.md)
