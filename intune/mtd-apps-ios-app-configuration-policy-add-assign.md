---
title: Hinzufügen und Zuweisen von MTD-Apps mit Microsoft Intune
titleSuffix: Microsoft Intune
description: Hinzufügen von Mobile Threat Defense-Apps (MTD), der Microsoft Authenticator-App und der iOS-Konfigurationsrichtlinie im Azure-Portal mit Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6065fda71688909dd7fcbc6ef1909e3d3ab36b8
ms.sourcegitcommit: 6bba9f2ef4d1ec699f5713a4da4f960e7317f1cd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67407115"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Hinzufügen und Zuweisen von Mobile Threat Defense-Apps (MTD) mit Intune  

> [!NOTE] 
> Dieser Artikel gilt für alle Mobile Threat Defense-Partner.

Sie können Intune verwenden, um MTD-Apps hinzuzufügen und bereitzustellen, damit Endbenutzer Benachrichtigungen über auf ihren mobilen Geräten erkannte Bedrohungen sowie eine Anleitung zur Behebung der Bedrohungen erhalten können.

## <a name="before-you-begin"></a>Vorbereitung    
Die unten beschriebenen Schritte müssen in der [Azure-Portal](https://portal.azure.com/) durchgeführt werden. Stellen Sie sicher, dass Sie mit den folgenden Prozessen vertraut sind:

-   [Hinzufügen von Apps in Microsoft Intune](apps-add.md)
-   [Hinzufügen von iOS-Apps mit Konfigurationsrichtlinien in Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)
-   [Zuweisen einer App mit Intune](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune)

> [!TIP]
> Das Intune-Unternehmensportal arbeitet als Broker auf Android-Geräten, damit Benutzer ihre Identitäten von Azure AD überprüfen lassen können.

## <a name="configure-microsoft-authenticator-for-ios"></a>Konfigurieren von Microsoft Authenticator für iOS  
Für iOS-Geräte benötigen Sie [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to), damit Benutzer ihre Identitäten von Azure AD überprüfen lassen können. Außerdem benötigen Sie eine iOS-App-Konfigurationsrichtlinie, die die MTD-iOS-App festlegt, die mit Intune verwendet werden soll.

Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](store-apps-ios.md) an. Verwenden Sie diese [Store-URL der Microsoft Authenticator-App](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) für **Schritt 12** im Abschnitt **Konfigurieren von App-Informationen**.

## <a name="configure-mtd-applications"></a>Konfigurieren von MTD-Anwendungen  
Wählen Sie den Abschnitt aus, der Ihrem MTD-Anbieter entspricht:

- [Lookout for Work](#configure-lookout-for-work-apps)
- [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
- [Check Point SandBlast Mobile](#configure-check-point-sandblast-mobile-apps)
- [Zimperium](#configure-zimperium-apps)
- [Pradeo](#configure-pradeo-apps)
- [Better Mobile](#configure-better-mobile-apps)
- [Sophos Mobile](#configure-sophos-apps)
- [Wandera](#configure-wandera-apps)

### <a name="configure-lookout-for-work-apps"></a>Konfigurieren von Lookout for Work-Apps  
- **Android**  
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von Android Store-Apps zu Microsoft Intune](store-apps-android.md) an. Verwenden Sie diese [Store-URL der Lookout for Work-Google-App](https://play.google.com/store/apps/details?id=com.lookout.enterprise) in **Schritt 7**.

- **iOS**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](store-apps-ios.md) an. Verwenden Sie diese [App-Store-URL zu Lookout for Work für iOS](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) in **Schritt 11** als **App-Store-URL**.

- **Lookout for Work-App außerhalb des Apple Stores**  
  - Sie müssen nun die Lookout for Work-App für iOS erneut signieren. Lookout verteilt die Lookout for Work-App für iOS außerhalb von iOS App Store. Bevor Sie die App verteilen, müssen Sie die App mit Ihrem iOS Enterprise Developer Certificate neu signieren.  
  - Ausführliche Anweisungen zum erneuten Signieren der Lookout for Work-Apps für iOS finden Sie unter [iOS App Re-Signing Process (Erneute Signatur bei iOS-Apps)](https://personal.support.lookout.com/hc/articles/114094038714) auf der Lookout-Website.

  - **Aktivieren der Azure AD-Authentifizierung für Benutzer der Lookout for Work-iOS-App**

    1. Wechseln Sie zum [Azure-Portal](https://portal.azure.com), melden Sie sich mit Ihren Anmeldeinformationen an, und navigieren Sie zur Seite „Anwendungen“.

    2. Fügen Sie die **Lookout for Work iOS-App** als eine **native Clientanwendung** hinzu.

    3. Ersetzen Sie **com.lookout.enterprise.yourcompanyname** mit der Kundenbundle-ID, die Sie beim Unterzeichnen der IPA ausgewählt haben.

    4. Hinzufügen von zusätzlichen Umleitungs-URI: **&lt;companyportal://code/>** gefolgt von einer URL-codierten Version Ihrer ursprünglichen URI-Umleitung.

    5. Fügen Sie **Delegierte Berechtigungen** zu Ihrer App hinzu.

    > [!NOTE] 
    > Weitere Informationen finden Sie unter [Konfigurieren Sie eine native Clientanwendung](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).

  - **Hinzufügen der IPA-Datei für Lookout for Work**

    - Laden Sie die neu signierte IPA-Datei hoch, wie im Artikel [Hinzufügen von branchenspezifischen iOS-Apps in Microsoft Intune](lob-apps-ios.md) beschrieben. Sie müssen auch iOS 8.0 oder höher als die mindestens erforderliche Betriebssystemversion festlegen.

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>Konfigurieren von Symantec Endpoint Protection Mobile-Apps  
- **Android**
   - Sehen Sie sich die Anleitungen für [das Hinzufügen von Android Store-Apps zu Microsoft Intune](store-apps-android.md) an. Verwenden Sie in **Schritt 7** diese [SEP Mobile-App-Store-URL](https://play.google.com/store/apps/details?id=com.skycure.skycure).  Wählen Sie für **Mindestens erforderliches Betriebssystem** die Option **Android 4.0 (Ice Cream Sandwich)** aus.

- **iOS**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](store-apps-ios.md) an. Verwenden Sie diese [App-Store-URL zu SEP Mobile](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) in **Schritt 11** als **App-Store-URL**.

### <a name="configure-check-point-sandblast-mobile-apps"></a>Konfigurieren von Check Point SandBlast Mobile-Apps  
- **Android**  
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von Android Store-Apps zu Microsoft Intune](store-apps-android.md) an. Verwenden Sie diese [Store-URL der Check Point SandBlast Mobile-App](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) in **Schritt 7**.

- **iOS**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](store-apps-ios.md) an. Verwenden Sie diese [App-Store-URL zu Check Point SandBlast Mobile](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) in **Schritt 11** als **App-Store-URL**.  

### <a name="configure-zimperium-apps"></a>Konfigurieren von Zimperium-Apps  
- **Android**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von Android Store-Apps zu Microsoft Intune](store-apps-android.md) an. Verwenden Sie diese [URL des Zimperium-App Stores](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) in **Schritt 7**.

- **iOS**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](store-apps-ios.md) an. Verwenden Sie diese [App-Store-URL zu Zimperium](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) in **Schritt 11** als **App-Store-URL**.  
 
### <a name="configure-pradeo-apps"></a>Konfigurieren von Pradeo-Apps  
- **Android**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von Android Store-Apps zu Microsoft Intune](store-apps-android.md) an. Verwenden Sie diese [URL des Pradeo-App Stores](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) in **Schritt 7**.

- **iOS**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](store-apps-ios.md) an. Verwenden Sie diese [App-Store-URL zu Pradeo](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) in **Schritt 11** als **App-Store-URL**.

### <a name="configure-better-mobile-apps"></a>Konfigurieren von Better Mobile-Apps  
- **Android**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von Android Store-Apps zu Microsoft Intune](store-apps-android.md) an. Verwenden Sie diese [URL des Active Shield-App Stores](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) in **Schritt 7**.

- **iOS**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](store-apps-ios.md) an. Verwenden Sie diese [App-Store-URL zu ActiveShield](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) in **Schritt 11** als **App-Store-URL**.

### <a name="configure-sophos-apps"></a>Konfigurieren von Sophos-Apps  
- **Android**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von Android Store-Apps zu Microsoft Intune](store-apps-android.md) an. Verwenden Sie diese [Store-URL der Sophos-App](https://play.google.com/store/apps/details?id=com.sophos.smsec) in **Schritt 7**.

- **iOS**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](store-apps-ios.md) an. Verwenden Sie diese [App-Store-URL zu ActiveShield](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) in **Schritt 11** als **App-Store-URL**.

### <a name="configure-wandera-apps"></a>Konfigurieren von Wandera-Apps  
 
- **Android**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von Android Store-Apps zu Microsoft Intune](store-apps-android.md) an. Verwenden Sie diese [Google Play-URL zu Wandera](https://play.google.com/store/apps/details?id=com.wandera.android) für **Schritt 7**. Wählen Sie für **Mindestens erforderliches Betriebssystem** die Option **Android 5.0** aus.

- **iOS**
  - Sehen Sie sich die Anleitungen für [das Hinzufügen von iOS Store-Apps zu Microsoft Intune](https://docs.microsoft.com/intune/store-apps-ios) an. Verwenden Sie diese [App Store-URL zu Wandera](https://itunes.apple.com/app/wandera/id605469330) in **Schritt 11** als **App-Store-URL**.

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>Konfigurieren der MTD-Apps mit einer iOS-App-Konfigurationsrichtlinie  

### <a name="lookout-for-work-app-configuration-policy"></a>Konfigurationsrichtlinie für Lookout for Work-Apps  
- Erstellen Sie die iOS-App-Konfigurationsrichtlinie wie im Artikel [zur Verwendung der iOS-App-Konfigurationsrichtlinie](app-configuration-policies-use-ios.md) beschrieben.

### <a name="sep-mobile-app-configuration-policy"></a>Konfigurationsrichtlinie für SEP Mobile-Apps  
- Verwenden Sie dasselbe Azure AD-Konto, das zuvor in der [Symantec Endpoint Protection-Verwaltungskonsole](https://aad.skycure.com) konfiguriert wurde. Dabei sollte es sich um das Konto handeln, mit dem Sie sich beim klassischen Intune-Portal anmelden.

- **Herunterladen** der iOS-App-Konfigurationsrichtliniendatei: 
  - Wechseln Sie zur [Symantec Endpoint Protection-Verwaltungskonsole](https://aad.skycure.com), und melden Sie sich mit Ihren Anmeldeinformationen an.

  - Wechseln Sie zu **Einstellungen**, und wählen Sie unter **Integrationen** die Option **Intune** aus. Wählen Sie **EMM Integration Selection** (EMM-Integrationsauswahl) aus. Wählen Sie **Microsoft** aus, und speichern Sie Ihre Auswahl.

  - Klicken Sie auf den Link **Integration setup files** (Integrationssetupdateien), und speichern Sie die generierte \*.zip-Datei. Die ZIP-Datei enthält die Datei „* **.plist**“, die zum Erstellen der iOS-App-Konfigurationsrichtlinie in Intune verwendet wird.

  - In den Anweisungen für [die Verwendung der iOS-App-Konfigurationsrichtlinien von Microsoft Intune](app-configuration-policies-use-ios.md) erfahren Sie, wie Sie die iOS-App-Konfigurationsrichtlinie für SEP Mobile hinzufügen.

  - Verwenden Sie in **Schritt 8** die Option **XML-Daten eingeben**, kopieren Sie den Inhalt aus der Datei „* **.plist**“, und fügen Sie den Inhalt in den Text der Konfigurationsrichtlinie ein.

> [!NOTE]  
> Wenn Sie die Dateien nicht abrufen können, wenden Sie sich an den [Symantec Endpoint Protection Mobile Enterprise Support](https://support.symantec.com/en_US/contact-support.html).

### <a name="check-point-sandblast-mobile-app-configuration-policy"></a>Konfigurationsrichtlinie für Check Point SandBlast Mobile-Apps  
- In den Anweisungen für [die Verwendung der iOS-App-Konfigurationsrichtlinien von Microsoft Intune](app-configuration-policies-use-ios.md) erfahren Sie, wie Sie die iOS-App-Konfigurationsrichtlinie für Check Point SandBlast Mobile hinzufügen.
    - Verwenden Sie in **Schritt 8** die Option **XML-Daten eingeben**, kopieren Sie den nachstehenden Inhalt, und fügen Sie den diesen in den Text der Konfigurationsrichtlinie ein.

```
<dict><key>MDM</key><string>INTUNE</string></dict>
```

### <a name="zimperium-app-configuration-policy"></a>Konfigurationsrichtlinie für Zimperium-Apps  
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

### <a name="pradeo-app-configuration-policy"></a>Pradeo-App-Konfigurationsrichtlinie  
Pradeo unterstützt keine App-Konfigurationsrichtlinie für iOS.  Wenn Sie eine konfigurierte App erhalten möchten, arbeiten Sie stattdessen mit Pradeo zusammen, um benutzerdefinierte IPA- und APK-Dateien zu implementieren, die mit den gewünschten Einstellungen vorkonfiguriert sind.

### <a name="better-mobile-app-configuration-policy"></a>Konfigurationsrichtlinie für Better Mobile-Apps  
- In den Anweisungen für [die Verwendung der iOS-App-Konfigurationsrichtlinien von Microsoft Intune](app-configuration-policies-use-ios.md) erfahren Sie, wie Sie die iOS-App-Konfigurationsrichtlinie für Better Mobile hinzufügen.
  - Verwenden Sie in **Schritt 8** die Option **XML-Daten eingeben**, kopieren Sie den nachstehenden Inhalt, und fügen Sie den diesen in den Text der Konfigurationsrichtlinie ein. Ersetzen Sie die URL für `https://client.bmobi.net` durch die URL für die entsprechende Konsole.

```
<dict>
<key>better_server_url</key>
<string>https://client.bmobi.net</string>
<key>better_udid</key>
<string>{{aaddeviceid}}</string>
<key>better_user</key>
<string>{{userprincipalname}}</string>
</dict>
```

### <a name="sophos-mobile-app-configuration-policy"></a>Konfigurationsrichtlinie für Sophos Mobile-Apps  
Erstellen Sie die iOS-App-Konfigurationsrichtlinie wie im Artikel [zur Verwendung der iOS-App-Konfigurationsrichtlinie](app-configuration-policies-use-ios.md) beschrieben.

### <a name="wandera-app-configuration-policy"></a>Wandera-App-Konfigurationsrichtlinie  
In den Anweisungen für [die Verwendung der iOS-App-Konfigurationsrichtlinien von Microsoft Intune](app-configuration-policies-use-ios.md) erfahren Sie, wie Sie die iOS-App-Konfigurationsrichtlinie für Wandera hinzufügen.
- Verwenden Sie in **Schritt 8** die Option **XML-Daten eingeben**. Melden Sie sich beim RADAR Wandera-Portal an, und navigieren Sie zu **Settings** > **EMM Integration** > **App Push** (Einstellungen > EMM-Integration > App-Push). Wählen Sie **Intune** aus, und kopieren Sie dann den folgenden Inhalt in den Text für die Konfigurationsrichtlinie.  

  ```
  <dict><key>secretKey</key>
  <string>SeeRADAR</string>
  <key>apiKey</key>
  <string> SeeRADAR </string>
  <key>customerId</key>
  <string> SeeRADAR </string>
  <key>email</key>
  <string>{{mail}}</string>
  <key>firstName</key>
  <string>{{username}}</string>
  <key>lastName</key>
  <string></string>
  <key>activationType</key>
  <string>PROVISION_THEN_AWP</string></dict>  
  ```

## <a name="assign-apps-to-groups"></a>Zuweisen von Apps zu Gruppen  
- Dieser Schritt gilt für alle MTD-Partner. Anweisungen hierzu finden Sie im Thema [Zuweisen von Apps zu Gruppen mit Microsoft Intune](apps-deploy.md).

## <a name="next-steps"></a>Nächste Schritte  
- [Konfigurieren einer Mobile Threat Defense-Gerätekompatibilitätsrichtlinie (MTD) mit Intune](mtd-device-compliance-policy-create.md)
