---
title: Microsoft Intune App SDK für iOS –Entwicklerhandbuch
description: Mit dem Microsoft Intune App SDK für iOS können Sie die Intune-App-Schutzrichtlinien (auch als APP- oder MAM-Richtlinien bezeichnet) in Ihre native iOS-App integrieren.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: eaffed2af38e269000dd951cec536e1f80be705f
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841350"
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Microsoft Intune App SDK für iOS –Entwicklerhandbuch

> [!NOTE]
> Lesen Sie am besten zuerst den Artikel [Get Started with Intune App SDK Guide (Erste Schritte mit dem Leitfaden für das Intune App SDK)](app-sdk-get-started.md). Dort finden Sie Informationen zu den Vorbereitungen, die Sie auf den verschiedenen unterstützten Plattformen für die Integration treffen müssen.

Mit dem Microsoft Intune App SDK für iOS können Sie die Intune-App-Schutzrichtlinien (auch als **APP**- oder **MAM-Richtlinien** bezeichnet) in Ihre native iOS-App integrieren. Als MAM-fähige App wird eine App bezeichnet, die in das Intune App SDK integriert ist. Sie ermöglichen IT-Administratoren, App-Schutzrichtlinien für Ihre mobile App bereitzustellen, wenn diese aktiv von Intune verwaltet wird.

## <a name="prerequisites"></a>Voraussetzungen

* Sie benötigen einen macOS-Computer, auf dem OS X 10.8.5 oder höher ausgeführt wird und auf dem Xcode 9 oder höher installiert ist.

* Ihre App muss für iOS 10 oder höher vorgesehen sein.

* Lesen Sie [die Lizenzbedingungen für das Intune App SDK für iOS (in englischer Sprache)](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS.pdf). Drucken Sie sich eine Kopie der Lizenzbedingungen aus und bewahren Sie diese in Ihren Unterlagen auf. Indem Sie das Intune App SDK für iOS herunterladen und verwenden, stimmen Sie diesen Lizenzbestimmungen zu.  Wenn Sie den Lizenzbedingungen nicht zustimmen, verwenden Sie die Software nicht.

* Laden Sie die Dateien für das Intune App SDK für iOS von [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) herunter.

## <a name="whats-in-the-sdk"></a>Inhalt des SDK

Das Intune App SDK für iOS enthält eine statische Bibliothek, Ressourcendateien, API-Header, eine PLIST-Datei Liste mit Debug-Einstellungen sowie ein Konfigurationstool. Client-Apps können einfach nur die Ressourcendateien enthalten und statisch mit den Bibliotheken verknüpft sein, um die meisten Richtlinien durchzusetzen. Erweiterte Intune-APP-Funktionen werden mithilfe von APIs erzwungen.

Dieses Handbuch befasst sich mit der Verwendung der folgenden Komponenten des Intune App SDK für iOS:

* **libIntuneMAM.a**: Die statische Intune App SDK-Bibliothek. Wenn Ihre App keine Erweiterungen verwendet, können Sie diese Bibliothek mit Ihrem Projekt verknüpfen, um die App für die Verwaltung von Clientanwendungen mit Intune zu aktivieren.

* **IntuneMAM.framework**: Das Intune App-SDK-Framework. Verknüpfen Sie dieses Framework mit Ihrem Projekt, um die App für die Verwaltung von Clientanwendungen mit Intune zu aktivieren. Verwenden Sie das Framework anstelle der statischen Bibliothek, wenn Ihre App Extensions verwendet, damit vom Projekt nicht mehrere Kopien der statischen Bibliothek erstellt werden.

* **IntuneMAMResources.bundle**: Ein Ressourcenpaket, das Ressourcen für das SDK enthält.

* **Header**: Macht die Intune App SDK-APIs verfügbar. Wenn Sie eine API verwenden, müssen Sie die Headerdatei einschließen, die die API enthält. Die folgenden Headerdateien enthalten die APIs, die Datentypen und die Protokolle, die vom Intune App SDK für Entwickler zur Verfügung gestellt wurden:

    * IntuneMAMAppConfig.h
    * IntuneMAMAppConfigManager.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMDefs.h
    * IntuneMAMEnrollmentDelegate.h
    * IntuneMAMEnrollmentManager.h
    * IntuneMAMEnrollmentStatus.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMLogger.h
    * IntuneMAMPolicy.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMPolicyManager.h
    * IntuneMAMVersionInfo.h

Entwickler können die Inhalte aller oben stehenden Header verfügbar machen, indem sie nur IntuneMAM.h importieren.


## <a name="how-the-intune-app-sdk-works"></a>Funktionsweise des Intune App SDK

Ziel des Intune App SDK für iOS ist es, iOS-Anwendungen mit minimalen Codeänderungen mit Verwaltungsfunktionen zu versehen. Möglichst wenige Codeänderungen bedeuten kürzere Markteinführungszeiten, ohne die Konsistenz und Stabilität Ihrer mobilen Anwendung zu beeinträchtigen.


## <a name="build-the-sdk-into-your-mobile-app"></a>Integrieren des SDK in Ihre mobile App

Gehen Sie folgendermaßen vor, um das Intune App SDK zu aktivieren:

1. **Option 1 (empfohlen)**: Verknüpfen Sie `IntuneMAM.framework` mit Ihrem Projekt. Ziehen Sie `IntuneMAM.framework` in die Liste für **eingebettete Binärdateien** des Projektziels.

   > [!NOTE]
   > Bei Verwendung des Frameworks müssen Sie die Simulatorarchitekturen manuell aus dem universellen Framework entfernen, bevor Sie Ihre App an den App Store übermitteln. Weitere Informationen siehe [Übermitteln Ihrer App an den App Store](#Submit-your-app-to-the-App-Store).

   **Option 2**: Stellen Sie eine Verknüpfung mit der `libIntuneMAM.a`-Bibliothek her. Ziehen Sie die `libIntuneMAM.a`-Bibliothek in die Liste **Verknüpfte Frameworks und Bibliotheken** des Projektziels.

    ![Intune App SDK iOS – verknüpfte Frameworks und Bibliotheken](./media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    Fügen Sie `-force_load {PATH_TO_LIB}/libIntuneMAM.a` einem der folgenden Pfade hinzu, wobei Sie `{PATH_TO_LIB}` durch den Speicherort des Intune App SDK ersetzen:
   * Der Buildkonfigurationseinstellung `OTHER_LDFLAGS` des Projekts
   * Benutzeroberflächenoption **Other Linker Flags** (Andere Linker-Flags) von Xcode

     > [!NOTE]
     > Um den `PATH_TO_LIB` zu suchen, wählen Sie die Datei `libIntuneMAM.a` und dann im Menü **Datei** die Option **Informationen abrufen** aus. Kopieren Sie den **Pfad** aus dem Abschnitt **Allgemein** im Fenster **Info**.

     Fügen Sie das Ressourcenpaket `IntuneMAMResources.bundle` zum Projekt hinzu, indem Sie es in **Buildphasen** unter **Paketressourcen kopieren** ziehen.

     ![Intune App SDK iOS: Paketressourcen kopieren](./media/intune-app-sdk-ios-copy-bundle-resources.png)

2. Fügen Sie diese iOS-Frameworks zum Projekt hinzu:  
    * MessageUI.framework  
    * Security.framework  
    * MobileCoreServices.framework  
    * SystemConfiguration.framework  
    * libsqlite3.tbd  
    * libc++.tbd  
    * ImageIO.framework  
    * LocalAuthentication.framework  
    * AudioToolbox.framework  
    * QuartzCore.framework  
    * WebKit.framework

3. Aktivieren Sie die Freigabe des Schlüsselbunds (sofern noch nicht geschehen), indem Sie in jedem Projektziel **Capabilities** auswählen und den Schalter **Keychain Sharing** aktivieren. Die Freigabe des Schlüsselbunds ist erforderlich, damit Sie mit dem nächsten Schritt fortfahren können.

   > [!NOTE]
   > Ihr Bereitstellungsprofil muss neue Werte für die Freigabe des Schlüsselbunds unterstützen. Die Schlüsselbund-Zugriffsgruppen sollten ein Platzhalterzeichen unterstützen. Sie können dies überprüfen, indem Sie die Datei „.mobileprovision“ in einem Text-Editor öffnen, nach **keychain-access-groups** suchen und sich vergewissern, dass ein Platzhalter vorhanden ist. Beispiel:
   >  ```xml
   >  <key>keychain-access-groups</key>
   >  <array>
   >  <string>YOURBUNDLESEEDID.*</string>
   >  </array>
   >  ```

4. Nachdem Sie die Freigabe des Schlüsselbunds aktiviert haben, folgen Sie den nachstehenden Schritten, um eine separate Zugriffsgruppe zu erstellen, in der das Intune App SDK seine Daten speichert. Sie können eine Zugriffsgruppe für den Schlüsselbund über die Benutzeroberfläche oder mithilfe der Berechtigungsdatei erstellen. Wenn Sie die Benutzeroberfläche zum Erstellen der Zugriffsgruppe für den Schlüsselbund verwenden, führen Sie unbedingt die folgenden Schritte aus:

    1. Wenn in Ihrer mobilen App keine Keychain-Zugriffsgruppen definiert sind, fügen Sie die Paket-ID der App als **erste** Gruppe hinzu.
    
    2. Fügen Sie die freigegebene Zugriffsgruppe für den Schlüsselbund `com.microsoft.intune.mam` Ihren vorhandenen Zugriffsgruppen hinzu. Diese Zugriffsgruppe wird vom Intune App SDK zum Speichern von Daten verwendet.
    
    3. Fügen Sie `com.microsoft.adalcache` zu Ihren vorhandenen Zugriffsgruppen hinzu.
    
        ![Intune App SDK für iOS: Schlüsselbund gemeinsam nutzen](./media/intune-app-sdk-ios-keychain-sharing.png)
    
    4. Wenn Sie die Berechtigungsdatei direkt bearbeiten, anstatt die oben gezeigte Xcode-Benutzeroberfläche zum Erstellen der Schlüsselbund-Zugriffsgruppen zu verwenden, setzen Sie `$(AppIdentifierPrefix)` vor die Schlüsselbund-Zugriffsgruppen (Xcode verarbeitet dies automatisch). Beispiel:
    
        - `$(AppIdentifierPrefix)com.microsoft.intune.mam`
        - `$(AppIdentifierPrefix)com.microsoft.adalcache`
    
        > [!NOTE]
        > Eine Berechtigungsdatei ist eine für die mobile Anwendung eindeutige XML-Datei. Sie wird zum Festlegen spezieller Berechtigungen und Funktionen in Ihrer iOS-App verwendet. Wenn Ihre App vorher noch keine Berechtigungsdatei hatte, sollte die Aktivierung der Schlüsselbundfreigabe (Schritt 3) dazu geführt haben, dass Xcode eine für Ihre App generiert hat. Vergewissern Sie sich, dass die Paket-ID der App als erster Eintrag in der Liste aufgeführt ist.

5. Nehmen Sie jedes Protokoll, das Ihre App an `UIApplication canOpenURL` übergibt, in das `LSApplicationQueriesSchemes`-Array der Datei „Info.plist“ Ihrer App auf. Speichern Sie Ihre Änderungen, bevor Sie mit dem nächsten Schritt fortfahren.

6. Stellen Sie sicher, dass der info.plist-Schlüssel [NSFaceIDUsageDescription](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW75) mit einer Standardmeldung konfiguriert ist, wenn Ihre App FaceID noch nicht verwendet. Dies ist erforderlich, damit iOS den Benutzer darüber informieren kann, wie die App FaceID verwendet. Eine Intune-App-Schutzrichtlinieneinstellung ermöglicht die Verwendung von FaceID als Methode für den App-Zugriff, wenn dies vom IT-Administrator konfiguriert wurde.

7. Verwenden Sie das im [SDK-Repository](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) enthaltene IntuneMAMConfigurator-Tool, um die Konfiguration der Datei „Info.plist“ Ihrer App abzuschließen. Das Tool weist drei Parameter auf:

   |Eigenschaft|Verwendung|
   |---------------|--------------------------------|
   |- i |  `<Path to the input plist>` |
   |- e | `<Path to the entitlements file>` |
   |- o |  (Optional) `<Path to the output plist>` |

Wenn der Parameter „-o“ nicht angegeben ist, wird die Eingabedatei direkt geändert. Das Tool ist idempotent und sollte immer dann erneut ausgeführt werden, wenn Änderungen an der Datei „Info.plist“ der App oder den Berechtigungen vorgenommen wurden. Bei der Aktualisierung des Intune-SDK sollten Sie auch die neueste Version des Tools herunterladen und ausführen, für den Fall, dass sich die Konfigurationsanforderungen von „Info.plist“ im letzten Release geändert haben.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Konfigurieren der Authentifizierungsbibliothek von Azure Active Directory (Active Directory Authentication Library, ADAL)

Das Intune App SDK verwendet die [Authentifizierungsbibliothek von Azure Active Directory](https://github.com/AzureAD/azure-activedirectory-library-for-objc) für die Authentifizierung und bedingte Startszenarien. Außerdem ist es davon abhängig, dass ADAL die Benutzeridentität im MAM-Dienst für das Verwalten registriert, ohne dafür Geräteregistrierungsszenarios zu benötigen.

Normalerweise setzt ADAL voraus, dass Apps sich bei Azure Active Directory (AAD) registrieren und eine eindeutige ID (Client-ID) sowie weitere Bezeichner abrufen, um die Sicherheit der Token zu gewährleisten, die an die Anwendung übermittelt werden. Sofern nicht anders angegeben, verwendet das Intune App SDK bei der Kontaktaufnahme mit Azure AD standardmäßige Registrierungswerte.  

Wenn Ihre App bereits ADAL zum Authentifizieren von Benutzern verwendet, muss sie ihre vorhandenen Registrierungswerte verwenden und die Standardwerte des Intune App SDK überschreiben. Dadurch wird sichergestellt, dass Benutzer nicht zweimal zur Authentifizierung aufgefordert werden (einmal vom Intune App SDK und einmal von der App).

Ihre App sollte mit der [aktuellen Version von ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) auf deren Hauptverzweigung verknüpft sein. Das Intune App SDK verwendet derzeit den Brokerbranch von ADAL, um Apps zu unterstützen, für die bedingter Zugriff erforderlich ist. (Deshalb hängen diese Apps von der Microsoft Authenticator-App ab.) Das SDK ist trotzdem mit dem Hauptbranch von ADAL kompatibel. Verwenden Sie den Branch, der am besten zu Ihrer App passt.

### <a name="link-to-adal-binaries"></a>Verknüpfung mit ADAL-Binärdateien

Gehen Sie folgendermaßen vor, um Ihre App mit den ADAL-Binärdateien zu verknüpfen:

1. Laden Sie die [Authentifizierungsbibliothek von Azure Active Directory (ADAL) für Objective-C](https://github.com/AzureAD/azure-activedirectory-library-for-objc) von GitHub herunter, und befolgen Sie dann die [Anweisungen](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download) zum Herunterladen von ADAL mithilfe von Git-Submodulen oder CocoaPods.

2. Fügen Sie das ADAL-Framework (Option 1) oder die statische Bibliothek (Option 2) zu Ihrem Projekt hinzu.

3. Wenn in Ihrer App keine Zugriffsgruppen für den Schlüsselbund definiert sind, fügen Sie die Paket-ID der App als erste Gruppe hinzu.

4. Aktivieren Sie ADAL-SSO (einmaliges Anmelden), indem Sie den Schlüsselbundzugriffsgruppen `com.microsoft.adalcache` und `com.microsoft.workplacejoin` hinzufügen.

5. Falls Sie die Schlüsselbundgruppe für den freigegebenen ADAL-Cache explizit festlegen, achten Sie darauf, dass sie auf `<appidprefix>.com.microsoft.adalcache` festgelegt ist. ADAL legt dies für Sie fest, sofern Sie die Einstellung nicht außer Kraft setzen. Wenn Sie eine benutzerdefinierte Schlüsselbundgruppe als Ersatz für `com.microsoft.adalcache` festlegen möchten, können Sie dies in der info.plist-Datei unter IntuneMAMSettings mit dem Schlüssel `ADALCacheKeychainGroupOverride` tun.

### <a name="configure-adal-settings-for-the-intune-app-sdk"></a>Konfigurieren der ADAL-Einstellungen für das Intune App SDK

Wenn Ihre Anwendung bereits ADAL für die Authentifizierung verwendet und über eigene ADAL-Einstellungen verfügt, können Sie die Verwendung der gleichen Einstellungen durch das Intune App SDK während der Authentifizierung bei Azure Active Directory erzwingen. Dadurch wird sichergestellt, dass die App den Benutzer nicht zweimal zur Authentifizierung auffordert. Unter [Configure settings for the Intune App SDK](#configure-settings-for-the-intune-app-sdk) (Konfigurieren der Einstellungen für das Intune App SDK) finden Sie Informationen zum Auffüllen der folgenden Einstellungen:  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

Wenn Ihre App bereits ADAL verwendet, sind die folgenden Konfigurationen erforderlich:

1. Geben Sie in der Datei „Info.plist“ des Projekts unter dem **IntuneMAMSettings**-Wörterbuch mit dem Schlüsselnamen `ADALClientId` die für ADAL-Aufrufe zu verwendende Client-ID an.

2. Geben Sie außerdem im **IntuneMAMSettings**-Wörterbuch mit dem Schlüsselnamen `ADALAuthority` die Azure AD-Autorität an.

3. Geben Sie außerdem im **IntuneMAMSettings**-Wörterbuch mit dem Schlüsselnamen `ADALRedirectUri` den Umleitungs-URI an, mit dem ADAL-Aufrufe durchgeführt werden sollen. Alternativ können Sie stattdessen `ADALRedirectScheme` angeben, wenn der Umleitungs-URI der Anwendung das Format `scheme://bundle_id` aufweist.

Darüber hinaus können Apps diese Azure AD-Einstellungen zur Runtime überschreiben. Legen Sie zu diesem Zweck einfach die Eigenschaften `aadAuthorityUriOverride`, `aadClientIdOverride` und `aadRedirectUriOverride` auf der `IntuneMAMPolicyManager`-Instanz fest.

4. Stellen Sie sicher, dass die Schritte befolgt werden, um Ihrer iOS-App Berechtigungen für den Dienst der App-Schutzrichtlinie (App Protection Policy, APP) zu erteilen. Verwenden Sie die Anweisungen im [Leitfaden zu den ersten Schritten mit dem Intune SDK](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration) unter „Erteilen von Berechtigungen für den Zugriff auf den Intune-App-Schutzdienst durch Ihre App (optional)“.  

> [!NOTE]
> Der Ansatz mit „Info.plist“ empfiehlt sich für alle Einstellungen, die statisch sind und nicht zur Runtime ermittelt werden müssen. Die den `IntuneMAMPolicyManager`-Eigenschaften zugewiesenen Werte haben Vorrang vor den entsprechenden in „Info.plist“ angegebenen Werten und werden auch nach dem Neustart der App beibehalten. Das SDK verwendet diese weiterhin für das Einchecken von Richtlinien, bis die Registrierung des Benutzers aufgehoben wird oder die Werte gelöscht oder geändert werden.

### <a name="if-your-app-does-not-use-adal"></a>Wenn Ihre Anwendung ADAL nicht verwendet

Wie oben erwähnt, verwendet das Intune App SDK die [Authentifizierungsbibliothek von Azure Active Directory](https://github.com/AzureAD/azure-activedirectory-library-for-objc) für die Authentifizierung und bedingte Startszenarios. Es verwendet ADAL außerdem zum Registrieren der Benutzeridentität beim MAM-Dienst für Verwaltungsszenarien ohne Geräteregistrierung. Wenn **Ihre Anwendung ADAL für den eigenen Authentifizierungsmechanismus nicht verwendet**, stellt das Intune App SDK Standardwerte für ADAL-Parameter bereit und verarbeitet die Authentifizierung über Azure AD. Sie müssen keine Werte für die oben aufgeführten ADAL-Einstellungen angeben. Jeder Authentifizierungsmechanismus (falls vorhanden), der von Ihrer App verwendet wird, wird ganz oben in den ADAL-Anforderungen angezeigt. 

## <a name="configure-settings-for-the-intune-app-sdk"></a>Konfigurieren der Einstellungen für Intune App SDK

Sie können das Wörterbuch **IntuneMAMSettings** in der Datei „info.plist“ der Anwendung verwenden, um das Intune App SDK einzurichten und zu konfigurieren. Wenn das Wörterbuch „IntuneMAMSettings“ in der Datei „Info.plist“ nicht angezeigt wird, sollten Sie es erstellen.

In „IntuneMAMSettings“ können Sie mit den folgenden unterstützten Einstellungen das Intune App SDK konfigurieren.

Einige dieser Einstellungen wurden möglicherweise schon in vorherigen Abschnitten erörtert, und einige gelten nicht für alle Apps.

Einstellung  | Typ  | Definition | Erforderlich?
--       |  --   |   --       |  --
ADALClientId  | Zeichenfolge  | Die Azure AD-Client-ID der App. | Erforderlich, wenn die App ADAL verwendet |
ADALAuthority | Zeichenfolge | Die aktive Azure AD-Autorität. Dort wo AAD-Konten konfiguriert wurden, sollten Sie Ihre eigene Umgebung verwenden. | Erforderlich, wenn die App ADAL verwendet. Wenn dieser Wert nicht vorhanden ist, wird der Intune-Standard verwendet.|
ADALRedirectUri  | Zeichenfolge  | Der Azure AD-Umleitungs-URI der App. | ADALRedirectUri oder ADALRedirectScheme ist erforderlich, wenn die App ADAL verwendet.  |
ADALRedirectScheme  | Zeichenfolge  | Das Azure AD-Umleitungsschema der App. Dieses kann anstelle von ADALRedirectUri verwendet werden, wenn der Umleitungs-URI der App im `scheme://bundle_id`-Format ist. | ADALRedirectUri oder ADALRedirectScheme ist erforderlich, wenn die App ADAL verwendet. |
ADALLogOverrideDisabled | Boolesch  | Gibt an, ob das SDK alle ADAL-Protokolle (einschließlich ADAL-Aufrufe von der App, sofern zutreffend) in die eigene Protokolldatei einschließt. Standardwert ist "NO". Legen Sie den Wert auf „YES“ fest, wenn die App einen eigenen ADAL-Protokollrückruf festlegt. | (Optional) |
ADALCacheKeychainGroupOverride | Zeichenfolge  | Gibt die Schlüsselbundgruppe an, die für den ADAL-Cache anstelle von „com.microsoft.adalcache“ verwendet werden soll. Beachten Sie, dass diese das App-ID-Präfix nicht enthält. Dieses wird der gegebenen Zeichenfolge zur Laufzeit vorangestellt. | (Optional) |
AppGroupIdentifiers | Zeichenfolgenarray  | Ein Array mit App-Gruppen aus dem Berechtigungsabschnitt "com.apple.security.application-groups" der App. | Erforderlich, wenn die App Anwendungsgruppen verwendet. |
ContainingAppBundleId | Zeichenfolge | Gibt die Paket-ID der Anwendung an, die die Erweiterung enthält. | Erforderlich für iOS-Extensions. |
DebugSettingsEnabled| Boolesch | Bei der Einstellung JA können innerhalb des Einstellungspakets Testrichtlinien angewendet werden. Diese Einstellungen sollte bei ausgelieferten Anwendungen *nicht* aktiviert sein. | (Optional) Standardwert lautet „no“ (Nein)|
MainNibFile <br> MainNibFile~ipad  | Zeichenfolge  | Diese Einstellung sollte den Namen der Haupt-NIB-Datei der Anwendung enthalten.  | Erforderlich, wenn MainNibFile für die Anwendung in der Datei „Info.plist“ definiert ist. |
MainStoryboardFile <br> MainStoryboardFile~ipad  | Zeichenfolge  | Diese Einstellung sollte den Namen der Haupt-Storyboard-Datei der Anwendung enthalten. | Erforderlich, wenn UIMainStoryboardFile für die Anwendung in der Datei „Info.plist“ definiert ist. |
MAMPolicyRequired| Boolesch| Gibt an, ob das Starten der App blockiert wird, wenn die App über keine Intune APP-Richtlinie verfügt. Standardwert ist "NO". <br><br> Hinweis: Apps können nicht an den App-Store übermittelt werden, wenn „MAMPolicyRequired“ auf „Ja“ festgelegt ist. | (Optional) Standardwert lautet „no“ (Nein)|
MAMPolicyWarnAbsent | Boolesch| Gibt an, ob die App den Benutzer beim Starten warnt, wenn die App über keine Intune APP-Richtlinie verfügt. <br><br> Hinweis: Benutzer können die App ohne Richtlinie weiter verwenden, nachdem sie die Warnung geschlossen haben. | (Optional) Standardwert lautet „no“ (Nein) |
MultiIdentity | Boolesch| Gibt an, ob die App den Umgang mit mehreren Identitäten beherrscht. | (Optional) Standardwert lautet „no“ (Nein) |
SplashIconFile <br> SplashIconFile~ipad | Zeichenfolge  | Gibt die Datei für das Intune-Begrüßungssymbol (Startsymbol) an. | (Optional) |
SplashDuration | Zahl | Mindestdauer in Sekunden, für die der Intune Startbildschirm beim Anwendungsstart angezeigt wird. Standardwert ist 1,5. | (Optional) |
BackgroundColor| Zeichenfolge| Gibt die Hintergrundfarbe für den Start- und den PIN-Bildschirm an. Akzeptiert eine hexadezimale RGB-Zeichenfolge im Format „#XXXXXX“, wobei X Werte von 0-9 bzw. A-F annehmen kann. Das Gatterzeichen kann ausgelassen werden.   | (Optional) Der Standardwert ist „Hellgrau“. |
ForegroundColor| Zeichenfolge| Gibt die Vordergrundfarbe für den Start- und den PIN-Bildschirm an, etwa die Textfarbe. Nimmt eine hexadezimale RGB-Zeichenfolge der Form #XXXXXX an, wobei X zwischen 0 und 9 oder A und F liegen kann. Das Gatterzeichen kann ausgelassen werden.  | (Optional) Der Standardwert ist „Schwarz“. |
AccentColor | Zeichenfolge| Gibt die Akzentfarbe für den PIN-Bildschirm an, etwa die Textfarbe einer Schaltfläche oder die Hervorhebungsfarbe für ein Feld. Akzeptiert eine hexadezimale RGB-Zeichenfolge im Format „#XXXXXX“, wobei X Werte von 0-9 bzw. A-F annehmen kann. Das Gatterzeichen kann ausgelassen werden.| (Optional) Der Standardwert ist „Blau“ (Systemfarbe). |
MAMTelemetryDisabled| Boolesch| Gibt an, ob das SDK keine Telemetriedaten an sein Back-End sendet.| (Optional) Standardwert lautet „no“ (Nein) |
MAMTelemetryUsePPE | Boolesch | Gibt an, ob das MAM SDK Daten an das PPE-Telemetrie-Back-End sendet. Verwenden Sie diese Option beim Testen Ihrer Apps mit Intune-Richtlinien, damit Telemetriedaten aus dem Test getrennt von Kundendaten gehalten werden. | (Optional) Standardwert lautet „no“ (Nein) |
MaxFileProtectionLevel | Zeichenfolge | (Optional) Ermöglicht der App, das Maximum für `NSFileProtectionType` anzugeben, das sie unterstützen kann. Dieser Wert setzt die Richtlinie außer Kraft, die vom Dienst gesendet wird, wenn die Ebene die von der Anwendung unterstützte übersteigt. Mögliche Werte: `NSFileProtectionComplete`, `NSFileProtectionCompleteUnlessOpen`, `NSFileProtectionCompleteUntilFirstUserAuthentication`, `NSFileProtectionNone`.|
OpenInActionExtension | Boolesch | Legen Sie die Einstellung für „Open-In“-Aktionserweiterungen auf „YES“ fest. Weitere Informationen finden Sie im Abschnitt „Sharing Data via UIActivityViewController“ (Freigeben von Daten über UIActivityViewController). |
WebViewHandledURLSchemes | Array von Zeichenfolgen | Gibt die URL-Schemas an, die WebView für Ihre App verarbeitet. | Erforderlich, wenn Ihre App WebView verwendet, das URLs über Verknüpfungen und/oder JavaScript verarbeitet. |

## <a name="receive-app-protection-policy"></a>Erhalten einer App-Schutzrichtlinie

### <a name="overview"></a>Übersicht

Um eine Intune-App-Schutzrichtlinie zu erhalten, müssen Apps eine Registrierungsanforderung beim Intune-MAM-Dienst initiieren. Apps können in der Intune-Konsole so konfiguriert werden, dass sie App-Schutzrichtlinien mit oder ohne Geräteregistrierung empfangen. App-Schutzrichtlinien ohne Registrierung, auch bekannt als **APP-WE** oder MAM-WE – ermöglichen, dass Apps von Intune verwaltet werden können, ohne dass das Gerät bei der Verwaltung mobiler Geräte (MDM) von Intune registriert sein muss. In beiden Fällen ist eine Registrierung beim Intune-MAM-Dienst erforderlich, um Richtlinien zu erhalten.

### <a name="apps-that-use-adal"></a>Apps, die ADAL verwenden

Apps, die bereits ADAL verwenden, sollten die `registerAndEnrollAccount`-Methode auf der `IntuneMAMEnrollmentManager`-Instanz aufrufen, nachdem der Benutzer erfolgreich authentifiziert wurde:

```objc
/*
 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;
```

Durch Aufrufen der `registerAndEnrollAccount`-Methode registriert das SDK das Benutzerkonto und versucht, die App im Auftrag dieses Kontos zu registrieren. Wenn bei der Registrierung aus irgendeinem Grund ein Fehler auftritt, versucht das SDK die Registrierung 24 Stunden später automatisch erneut. Zu Debuggingzwecken kann die App über einen Delegaten [Benachrichtigungen](#Status-result-and-debug-notifications) zu den Ergebnissen von Registrierungsanforderungen empfangen.

Nachdem diese API aufgerufen wurde, kann die Anwendung anschließend normal funktionieren. Wenn die Registrierung erfolgreich ist, benachrichtigt das SDK den Benutzer, dass ein Neustart der App erforderlich ist. Zu diesen Zeitpunkt kann der Benutzer die App sofort neu starten.

```objc
[[IntuneMAMEnrollmentManager instance] registerAndEnrollAccount:@”user@foo.com”];
```

### <a name="apps-that-do-not-use-adal"></a>Apps, die nicht ADAL verwenden

Apps, die den Benutzer nicht mit ADAL anmelden, können trotzdem App-Schutzrichtlinien vom Intune-MAM-Dienst empfangen, indem sie die API aufrufen, um die Authentifizierung vom SDK ausführen zu lassen. Apps sollten diese Technik verwenden, wenn zwar keine Benutzer mit Azure AD authentifiziert wurden, aber trotzdem App-Schutzrichtlinien zum Schutz der Daten abgerufen werden müssen. Beispielsweise, wenn ein anderer Authentifizierungsdienst für die App-Anmeldung verwendet wird oder wenn die App überhaupt kein Anmelden unterstützt. Zu diesem Zweck kann die Anwendung die `loginAndEnrollAccount`-Methode auf der `IntuneMAMEnrollmentManager`-Instanz aufrufen:

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;
```

Durch Aufrufen dieser Methode wird der Benutzer vom SDK zur Eingabe von Anmeldeinformationen aufgefordert, wenn kein vorhandenes Token gefunden wird. Das SDK versucht dann, die App im Auftrag des angegebenen Benutzerkontos beim Intune-MAM-Dienst zu registrieren. Die Methode kann mit der Identität „nil“ aufgerufen werden. In diesem Fall nimmt das SDK die Registrierung mit dem vorhandenen verwalteten Benutzer auf dem Gerät (im Falle von MDM) vor oder fordert den Benutzer zur Eingabe eines Benutzernamens auf, wenn kein vorhandener Benutzer gefunden wird.

Bei einem Fehler bei der Registrierung sollte die App den erneuten Aufruf dieser API zu einem späteren Zeitpunkt vorsehen, je nach den Fehlerdetails. Die App kann über einen Stellvertreter [Benachrichtigungen](#Status-result-and-debug-notifications) zu den Ergebnissen von Registrierungsanforderungen empfangen.

Nachdem diese API aufgerufen wurde, kann die App anschließend normal funktionieren. Wenn die Registrierung erfolgreich ist, benachrichtigt das SDK den Benutzer, dass ein Neustart der App erforderlich ist.

Beispiel:
```objc
[[IntuneMAMEnrollmentManager instance] loginAndEnrollAccount:@”user@foo.com”];
```

### <a name="let-intune-handle-authentication-and-enrollment-at-launch"></a>Zulassen, dass Intune die Authentifizierung und Registrierung beim Start verarbeitet

Wenn das Intune SDK die gesamte Authentifizierung (über ADAL) und die Registrierung verarbeiten soll, bevor der Startvorgang Ihrer App abgeschlossen ist, und Ihre App immer die APP-Richtlinie erfordert, müssen Sie nicht die `loginAndEnrollAccount`-API verwenden. Sie können einfach die folgenden beiden Einstellungen auf im Wörterbuch „IntuneMAMSettings“ in der Datei „Info.plist“ der Datei auf „YES“ festlegen.

Einstellung  | Typ  | Definition |
--       |  --   |   --       |  
AutoEnrollOnLaunch| Boolesch| Gibt an, ob die App versuchen soll, sich beim Start automatisch zu registrieren, wenn eine vorhandene verwaltete Identität erkannt wurde und dies noch nicht passiert ist. Standardwert ist "NO". <br><br> Hinweis: Wenn keine verwaltete Identität gefunden wird oder kein gültiges Token für die Identität im ADAL-Cache verfügbar ist, tritt bei der Registrierung im Hintergrund ein Fehler auf, ohne dass Anmeldeinformationen angefordert werden. Dies gilt nicht, wenn „MAMPolicyRequired“ für die App auf „Ja“ festgelegt ist. |
MAMPolicyRequired| Boolesch| Gibt an, ob das Starten der App blockiert ist, wenn die App über keine Intune App-Schutzrichtlinie verfügt. Standardwert ist "NO". <br><br> Hinweis: Apps können nicht an den App-Store übermittelt werden, wenn „MAMPolicyRequired“ auf „Ja“ festgelegt ist. Wenn MAMPolicyRequired auf JA festgelegt wird, muss auch AutoEnrollOnLaunch auf JA festgelegt werden. |

Wenn Sie diese Option für Ihre App auswählen, müssen Sie sich nach der Registrierung nicht um den Neustart der Anwendung kümmern.

### <a name="deregister-user-accounts"></a>Aufheben der Registrierung von Benutzerkonten

Bevor ein Benutzer bei einer App abgemeldet wird, sollte die App die Registrierung des Benutzers beim SDK aufheben. So wird sichergestellt:

1. Für das Konto des Benutzers werden keine wiederholten Registrierungsversuche mehr ausgeführt.

2. Die App-Schutzrichtlinie wird entfernt.

3. Wenn die App ein selektives Zurücksetzen einleitet (optional), werden alle Unternehmensdaten gelöscht.

Bevor der Benutzer abgemeldet wird, sollte die App die folgende Methode auf der `IntuneMAMEnrollmentManager`-Instanz aufrufen:

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune APP AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */
(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

Diese Methode muss aufgerufen werden, bevor die Azure AD-Token des Benutzerkontos gelöscht werden. Das SDK benötigt die AAD-Token des Benutzerkontos, um im Auftrag des Benutzers spezielle Anforderungen an den Intune-MAM-Dienst zu senden.

Wenn die App die Unternehmensdaten des Benutzers aus eigenem Antrieb löscht, kann das `doWipe`-Flag auf FALSCH festgelegt werden. Andernfalls kann die App das SDK dazu veranlassen, einen Prozess zum selektiven Zurücksetzen zu initiieren. Dies führt zu einem Aufruf des Stellvertreters der App für das selektive Zurücksetzen.

Beispiel:
```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

## <a name="status-result-and-debug-notifications"></a>Status-, Ergebnis- und Debugbenachrichtigungen

Die App kann Status-, Ergebnis- und Debugbenachrichtigungen zu den folgenden Anforderungen an den Intune MAM-Dienst empfangen:

* Registrierungsanforderungen
* Anforderungen zur Richtlinienaktualisierung
* Anfragen zur Aufhebung der Registrierung

Die Benachrichtigungen werden über Stellvertretermethoden in `IntuneMAMEnrollmentDelegate.h` angezeigt:

```objc
/**
 *  Called when an enrollment request operation is completed.
 * @param status status object containing debug information
 */

(void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a MAM policy request operation is completed.
 *  @param status status object containing debug information
 */
(void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a un-enroll request operation is completed.
 *  @Note: when a user is un-enrolled, the user is also de-registered with the SDK
 *  @param status status object containing debug information
 */

(void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;
```

Diese Stellvertretermethoden geben ein `IntuneMAMEnrollmentStatus`-Objekt zurück, das die folgenden Informationen enthält:

* Die Identität der Kontos, dem die Anforderung zugeordnet ist
* Ein Statuscode, der das Ergebnis der Anforderung anzeigt
* Eine Fehlerzeichenfolge mit einer Beschreibung des Statuscodes
* Ein `NSError`-Objekt. Dieses Objekt ist in `IntuneMAMEnrollmentStatus.h` zusammen mit den spezifischen Statuscodes definiert, die zurückgegeben werden können.

> [!NOTE]
> Diese Informationen dienen nur Debugzwecken. Die Geschäftslogik Ihrer App sollte nie auf diesen Benachrichtigungen basieren. Die Informationen können zu Debug- und Überwachungszwecken an einen Telemetriedienst gesendet werden.

### <a name="sample-code"></a>Beispielcode

Die folgenden Beispiele zeigen Implementierungen der Stellvertretermethoden:

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}
```

## <a name="application-restart"></a>Anwendungsneustart

Wenn eine Anwendung zum ersten Mal MAM-Richtlinien empfängt, muss sie neu gestartet werden, um die erforderlichen Hooks anzuwenden. Um die App zu benachrichtigen, dass ein Neustart erfolgen muss, stellt das SDK eine Stellvertretermethode in `IntuneMAMPolicyDelegate.h` zur Verfügung.

```objc
 - (BOOL) restartApplication
```

Der Rückgabewert dieser Methode teilt dem SDK mit, ob die Anwendung den erforderlichen Neustart übernehmen muss:

* Wenn „true“ zurückgegeben wird, muss die Anwendung den Neustart ausführen.

* Wenn „FALSE“ zurückgegeben wird, startet das SDK die App neu, nachdem die Methode zurückkehrt. Das SDK zeigt sofort ein Dialogfeld an, in dem der Benutzer zum Neustarten der Anwendung aufgefordert wird.

## <a name="customize-your-apps-behavior-with-apis"></a>Anpassen des App-Verhalten mit APIs

Das Intune App SDK hat mehrere APIs, die Sie aufrufen können, um Informationen über die APP-Richtlinie in Intune zu erhalten, die für die App bereitgestellt wurde. Diese Daten können Sie benutzen, um das Verhalten Ihrer App anzupassen. In der folgenden Tabelle finden Sie Informationen zu einigen wichtigen Intune-Klassen, die Sie verwenden werden:

Klasse | Beschreibung
----- | -----------
IntuneMAMPolicyManager.h | Die Klasse „IntuneMAMPolicyManager“ stellt die APP-Richtlinie für Intune bereit, die für die App bereitgestellt wurde. Sie stellt besonders APIs bereit, die beim [Aktivieren mehrerer Identitäten](app-sdk-ios.md#enable-multi-identity-optional) nützlich sind. |
IntuneMAMPolicy.h | Die „IntuneMAMPolicy“-Klasse macht MAM-Richtlinieneinstellungen verfügbar, die für die App gelten. Diese Richtlinieneinstellungen werden verfügbar gemacht, damit die App die Benutzeroberfläche anpassen kann. Die meisten Richtlinieneinstellungen werden durch das SDK und nicht durch die App erzwungen. Die einzige Einstellung, die die App implementieren sollte, ist das Steuerelement „Speichern unter“. Diese Klasse stellt einige APIs bereit, die zum Implementieren von „Speichern unter“ erforderlich sind. |
IntuneMAMFileProtectionManager.h | Die IntuneMAMFileProtectionManager-Klasse stellt APIs bereit, mit denen die App Dateien und Verzeichnisse auf Grundlage einer angegebenen Identität explizit sichern kann. Die Identität kann von Intune verwaltet oder gar nicht verwaltet werden, und das SDK wendet die entsprechende MAM-Richtlinie an. Die Verwendung dieser Klasse ist optional. |
IntuneMAMDataProtectionManager.h | Die IntuneMAMDataProtectionManager-Klasse macht APIs verfügbar, mit denen die App Datenpuffer sichern kann, falls eine Identität angegeben wurde. Die Identität kann von Intune verwaltet oder gar nicht verwaltet werden, und das SDK wendet die Verschlüsselung entsprechend an. |

## <a name="implement-save-as-controls"></a>Implementieren von „Speichern unter“-Steuerelementen

Mit Intune können IT-Administratoren auswählen, an welchem Speicherort eine verwaltete App Daten speichern kann. Mit der in `IntuneMAMPolicy.h` definierten `isSaveToAllowedForLocation`-API können Apps das Intune App SDK nach zulässigen Speicherorten abfragen.

Bevor Apps verwaltete Daten in einem Cloudspeicher oder einem lokalen Pfad speichern können, müssen sie mit der `isSaveToAllowedForLocation`-API überprüfen, ob der IT-Administrator die Orte zum Speichern freigegeben hat.

Bei Verwendung der `isSaveToAllowedForLocation`-API müssen Apps den UPN für den Speicherort übergeben, falls er verfügbar ist.

### <a name="supported-save-locations"></a>Unterstützte Speicherorte

Die `isSaveToAllowedForLocation`-API stellt Konstanten bereit, um zu prüfen, ob der IT-Administrator das Speichern von Daten in folgenden in `IntuneMAMPolicy.h` definierten Orten erlaubt:

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

Apps sollten anhand der Konstanten in `isSaveToAllowedForLocation` überprüfen, ob Daten an Speicherorten gespeichert werden können, die als „verwaltet“ (z.B. OneDrive for Business) oder „privat“ gelten. Darüber hinaus sollte die API verwendet werden, wenn die App nicht ermitteln kann, ob es sich um „verwaltete“ oder „private“ Speicherorte handelt.

Persönliche Speicherorte werden durch die Konstante `IntuneMAMSaveLocationOther` repräsentiert.

Die Konstante `IntuneMAMSaveLocationLocalDrive` sollte verwendet werden, wenn die App Daten an einem beliebigen Speicherort auf dem lokalen Gerät speichert.

## <a name="share-data-via-uiactivityviewcontroller"></a>Datenfreigabe über UIActivityViewController

Ab Version 8.0.2 kann das Intune App SDK `UIActivityViewController`-Aktionen filtern, sodass nur von Intune verwaltete Freigabespeicherorte zur Auswahl stehen. Dieses Verhalten wird durch die Datenübertragungsrichtlinie der Anwendung gesteuert.

### <a name="copy-to-actions"></a>„Kopieren in“-Aktionen

Beim Freigeben von Dokumenten über `UIActivityViewController` und `UIDocumentInteractionController` zeigt iOS „Kopieren in“-Aktionen für jede Anwendung an, die das Öffnen des freigegeben Dokuments unterstützt. Anwendungen deklarieren die Dokumenttypen, die sie unterstützen, durch die `CFBundleDocumentTypes`-Einstellung in ihrer Datei „Info.plist“. Diese Art der Freigabe ist nicht mehr verfügbar, wenn die Richtlinie die Freigabe für nicht verwaltete Anwendungen untersagt. Als Ersatz muss der Benutzer eine Nicht-Benutzeroberflächen-Aktionserweiterung zur Anwendung hinzufügen. Außerdem muss sie mit dem Intune APP SDK für iOS verknüpft werden. Die Aktionserweiterung ist nur ein Stub. Das SDK implementiert das Dateifreigabeverhalten. Führen Sie diese Schritte aus:

1. Für die Anwendung muss unter `CFBundleURLTypes` in der Datei „Info.plist“ mindestens eine schemeURL definiert sein.

2. Die Anwendung und Aktionserweiterung müssen mindestens eine App-Gruppe freigeben, und die App-Gruppe muss im `AppGroupIdentifiers`-Array des IntuneMAMSettings-Wörterbuchs aufgelistet sein, das zur App und zur Erweiterung gehört.

3. Name der Aktionserweiterung „Öffnen in“ gefolgt vom Anwendungsnamen. Lokalisieren Sie die Datei „Info.plist“ nach Bedarf.

4. Stellen Sie wie in der [Apple-Entwicklerdokumentation](https://developer.apple.com/ios/human-interface-guidelines/extensions/sharing-and-actions/) beschrieben ein Vorlagensymbol für die Erweiterung bereit. Alternativ können Sie mit dem IntuneMAMConfigurator-Tool diese Images aus dem App-Verzeichnis der Anwendung generieren. Führen Sie dazu Folgendes aus:

    ```bash
    IntuneMAMConfigurator -generateOpenInIcons /path/to/app.app -o /path/to/output/directory
    ```

5. Fügen Sie unter „IntuneMAMSettings“ in der Datei „Info.plist“ der Erweiterung eine boolesche Einstellung namens `OpenInActionExtension` mit dem Wert „YES“ hinzu.

6. Konfigurieren Sie `NSExtensionActivationRule`, sodass es eine einzelne Datei und alle Typen aus `CFBundleDocumentTypes` der Anwendung unterstützt, die das Präfix `com.microsoft.intune.mam` aufweisen. Wenn die Anwendung z.B. „public.text“ und „public.image“ unterstützt, würde die Aktivierungsregel lauten:

    ```objc
    SUBQUERY (
        extensionItems,
        $extensionItem,
        SUBQUERY (
            $extensionItem.attachments,
            $attachment,
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.text” ||
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image”).@count == 1
    ).@count == 1
    ```

### <a name="update-existing-share-and-action-extensions"></a>Aktualisieren der vorhandenen Freigabe- und Aktionserweiterungen

Wenn die App bereits Freigabe- oder Aktionserweiterungen enthält, muss `NSExtensionActivationRule` geändert werden, um die Intune-Typen zuzulassen. Fügen Sie für jeden von der Erweiterung unterstützten Typ einen weiteren Typ mit dem Präfix `com.microsoft.intune.mam` hinzu. Wenn die vorhandene Aktivierungsregel z.B. lautet:  

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data"
    ).@count > 0
).@count > 0
```

Sollte sie geändert werden in:

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.data
    ).@count > 0
).@count > 0
```

> [!NOTE]
> Mit dem IntuneMAMConfigurator-Tool können die Intune-Typen der Aktivierungsregel hinzugefügt werden. Wenn die bestehende Aktivierungsregel die vordefinierten Zeichenfolgenkonstanten verwendet (z.B. NSExtensionActivationSupportsFileWithMaxCount, NSExtensionActivationSupportsText usw.), kann die Prädikatsyntax sehr komplex werden. Mit dem IntuneMAMConfigurator-Tool kann auch die Aktivierungsregel aus den Zeichenfolgenkonstanten in eine Prädikatzeichenfolge konvertiert werden, während die Intune-Typen hinzugefügt werden.

### <a name="what-the-ui-should-look-like"></a>So sollte die Benutzeroberfläche aussehen

Alte Benutzeroberfläche:

![Freigeben von Daten – alte iOS-Benutzeroberfläche für die Freigabe](./media/sharing-UI-old.png)

Neue Benutzeroberfläche:

![Freigeben von Daten – neue iOS-Benutzeroberfläche für die Freigabe](./media/sharing-UI-new.png)

## <a name="enable-targeted-configuration-appmam-app-config-for-your-ios-applications"></a>Aktivieren der Zielkonfiguration (APP/MAM-App-Konfiguration) für iOS-Anwendungen

Die MAM-Zielkonfiguration (auch MAM-App-Konfiguration) ermöglicht, dass eine App Konfigurationsdaten über das Intune SDK erhält. Das Format und die Varianten dieser Daten müssen definiert und Intune-Kunden vom Besitzer oder Entwickler der App mitgeteilt werden.

Intune-Administratoren können Konfigurationsdaten über das Intune Azure-Portal und die Intune Graph-API als Ziel festlegen und bereitstellen. Ab Version 7.0.1 des Intune App SDK für iOS können Apps, die zur MAM-Zielkonfiguration gehören, über den MAM-Dienst mit Konfigurationsdaten für MAM versorgt werden. Die Anwendungskonfigurationsdaten werden durch unseren MAM-Dienst direkt an die App übertragen, und nicht über den MDM-Kanal. Das Intune App SDK stellt eine Klasse für den Zugriff auf die Daten bereit, die aus diesen Konsolen abgerufen wurden. Die folgenden Elemente sind erforderlich:

* Die App muss beim Intune-MAM-Dienst registriert werden, bevor Sie auf die Konfigurationsschnittstelle für MAM zugreifen. Weitere Informationen finden Sie unter [Erhalten der App-Schutzrichtlinie](#receive-app-protection-policy).

* In der Quelldatei der App muss `IntuneMAMAppConfigManager.h` enthalten sein.

* Rufen Sie `[[IntuneMAMAppConfigManager instance] appConfigForIdentity:]` auf, um das App-Konfigurationsobjekt zu erhalten.

* Rufen Sie den entsprechenden Selektor auf dem Objekt `IntuneMAMAppConfig` auf. Wenn es sich zum Beispiel beim Schlüssel Ihrer Anwendung um eine Zeichenfolge handeln, könnten Sie `stringValueForKey` oder `allStringsForKey` verwenden. Eine ausführliche Beschreibung der Rückgabewerte und Fehlerbedingungen finden Sie in `IntuneMAMAppConfig.h`.

Weitere Informationen zu den Funktionen der Graph-API finden Sie in der zugehörigen [Referenz](https://developer.microsoft.com/graph/docs/concepts/overview).

Weitere Informationen zum Erstellen einer MAM-Zielkonfigurationsrichtlinie für Apps in iOS finden Sie im Abschnitt zu MAM-Zielkonfiguration für Apps unter [How to use Microsoft Intune app configuration policies for iOS (Verwenden von Microsoft Intune-App-Konfigurationsrichtlinien für iOS)](https://docs.microsoft.com/intune/app-configuration-policies-use-ios).

## <a name="telemetry"></a>Telemetrie

Standardmäßig sammelt das Intune App SDK für iOS Telemetriedaten zu den folgenden Ereignistypen:

* **App-Start**: Bietet Microsoft Intune Informationen zur Nutzung von MAM-aktivierten Apps nach Verwaltungsart (MAM mit MDM, MAM ohne MDM-Registrierung usw.).

* **Registrierungsaufrufe**: Bietet Microsoft Intune Informationen über die Erfolgsquote und andere Leistungsmetriken von Registrierungsaufrufen, die von der Clientseite initiiert wurden.

* **Intune-Aktionen**: Um Probleme diagnostizieren und die Funktion von Intune sicherstellen zu können, sammeln wir Informationen zu Intune SDK-Aktionen.

> [!NOTE]
> Wenn von Ihrer mobilen Anwendung keine Intune App SDK-Telemetriedaten an Microsoft Intune gesendet werden sollen, müssen Sie die Intune App SDK-Telemetrieerfassung deaktivieren. Legen Sie die Eigenschaft `MAMTelemetryDisabled` im IntuneMAMSettings-Wörterbuch auf „YES“ fest.

## <a name="enable-multi-identity-optional"></a>Aktivieren von Multi-Identity (optional)

Standardmäßig wird eine Richtlinie vom SDK auf die gesamte App angewendet. Die Unterstützung für mehrere Identitäten ist ein MAM-Feature, das Sie aktivieren können, um eine Richtlinie auf der Ebene einzelner Identitäten anzuwenden. Dies erfordert eine stärkere Beteiligung der App als andere MAM-Features.

Die App muss das App-SDK informieren, wenn sie die Änderung der aktiven Identität beabsichtigt. Das SDK benachrichtigt seinerseits die App, wenn eine Änderung der Identität erforderlich ist. Aktuell wird nur eine verwaltete Identität unterstützt. Nachdem der Benutzer das Gerät oder die App registriert hat, verwendet das SDK die dabei verwendete Identität und betrachtet sie als die primäre verwaltete Identität. Andere Benutzer der App werden als nicht verwaltet mit uneingeschränkten Richtlinieneinstellungen behandelt.

Beachten Sie, dass eine Identität einfach nur als Zeichenfolge definiert ist. Bei Identitäten werden Groß- und Kleinschreibung nicht unterschieden. Anforderungen einer Identität beim SDK werden möglicherweise nicht mit der gleichen Groß-/Kleinschreibung zurückgegeben, die ursprünglich beim Festlegen der Identität verwendet wurde.

### <a name="identity-overview"></a>Überblick: Identität

Eine Identität ist einfach der Benutzername eines Kontos (z.B. user@contoso.com). Entwickler können die Identität der App auf den folgenden Ebenen festlegen:

* **Prozessidentität**: Legt die prozessweite Identität fest und wird in der Hauptsache für Anwendungen mit nur einer Identität verwendet. Diese Identität betrifft alle Aufgaben, Dateien und die Benutzeroberfläche.

* **UI-Identität**: Legt fest, welche Richtlinien auf Benutzeroberflächenaufgaben im Hauptthread angewendet werden, z.B. Ausschneiden/Kopieren/Einfügen, PIN, Authentifizierung und Datenfreigabe. Die UI-Identität wirkt sich nicht auf Dateiaufgaben wie Verschlüsselung und Sicherung aus.

* **Threadidentität**: Wirkt sich darauf aus, welche Richtlinien auf den aktuellen Thread angewendet werden. Diese Identität betrifft alle Aufgaben, Dateien und die Benutzeroberfläche.

Es ist Aufgabe der App, die Identitäten passend für verwaltete und nicht verwaltete Benutzer festzulegen.

Jeder Thread weist jederzeit eine effektive Identität für Benutzeroberflächen- und Dateiaufgaben auf. Dies ist die Identität, mit der überprüft wird, welche Richtlinien, sofern zutreffend, angewendet werden sollen. Wenn die Identität „no identity“ ist oder der Benutzer nicht verwaltet ist, werden keine Richtlinien angewendet. Die unten stehenden Diagramme zeigen, wie effektive Identitäten bestimmt werden.

  ![Intune App SDK für iOS: Identitätsermittlungsprozess](./media/ios-thread-identities.png)

### <a name="thread-queues"></a>Thread-Warteschlangen

Apps senden oft asynchrone und synchrone Aufgaben an Threadwarteschlangen. Das SDK fängt Aufrufe von Grand Central Dispatch (GCD) ab und verknüpft die aktuelle Threadidentität mit den gesendeten Aufgaben. Wenn die Aufgaben abgeschlossen sind, ändert das SDK die Threadidentität vorübergehend in die den Aufgaben zugeordnete Identität, schließt die Aufgaben ab und stellt die ursprüngliche Threadidentität wieder her.


Da `NSOperationQueue` auf GCD basiert, wird `NSOperations` mit der Identität des Threads zu dem Zeitpunkt ausgeführt, als die Aufgaben zur `NSOperationQueue` hinzugefügt wurden. `NSOperations` oder direkt über GCD versendete Funktionen können die aktuelle Threadidentität ebenfalls bei ihrer Ausführung ändern. Diese Identität überschreibt die vom sendenden Thread geerbte Identität.

### <a name="file-owner"></a>Dateibesitzer

Das SDK verfolgt die Identitäten der lokalen Dateibesitzer und wendet Richtlinien entsprechend an. Ein Dateibesitzer wird beim Erstellen einer Datei oder beim Öffnen einer Datei im Kürzungsmodus (truncate mode) eingerichtet. Der Besitzer wird auf die effektive Identität für Dateiaufgaben des Threads festgelegt, der die Aufgabe ausführt.

Alternativ können Apps die Identität des Dateibesitzers mithilfe von `IntuneMAMFilePolicyManager` explizit festlegen. Apps können `IntuneMAMFilePolicyManager` verwenden, um den Dateibesitzer abzurufen und die Benutzeroberflächenidentität festzulegen, bevor der Dateiinhalt angezeigt wird.

### <a name="shared-data"></a>Geteilte Daten

Wenn die App Dateien erstellt, die Daten von verwalteten und nicht verwalteten Benutzern enthalten, ist es ihre Aufgabe, die Daten der verwalteten Benutzer zu verschlüsseln. Sie können Daten mithilfe der `protect`- und `unprotect`-APIs in `IntuneMAMDataProtectionManager` verschlüsseln.

Die `protect`-Methode akzeptiert eine Identität, bei der es sich um einen verwalteten oder nicht verwalteten Benutzer handeln kann. Wenn der Benutzer verwaltet ist, werden die Daten verschlüsselt. Wenn es sich um einen nicht verwalteten Benutzer handelt, wird den Daten ein Header hinzugefügt, der die Identität verschlüsselt, die Daten selbst werden jedoch nicht verschlüsselt. Sie können die `protectionInfo`-Methode verwenden, um den Besitzer der Daten abzurufen.

### <a name="share-extensions"></a>Freigabeerweiterungen

Wenn die App eine Freigabeerweiterungen enthält, kann der Besitzer des freigegebenen Elements mithilfe der `protectionInfoForItemProvider`-Methode in `IntuneMAMDataProtectionManager` abgerufen werden. Wenn es sich bei dem freigegebenen Element um eine Datei handelt, legt das SDK den Dateibesitzer fest. Wenn es sich bei dem freigegebenen Element um Daten handelt, muss die App den Besitzer der Datei festlegen, wenn diese Daten in einer Datei gespeichert werden, und die `setUIPolicyIdentity`-API aufrufen, bevor die Daten in der Benutzeroberfläche angezeigt werden.

### <a name="turn-on-multi-identity"></a>Aktivierung von mehreren Identitäten

Standardmäßig werden Apps als Einzelidentitäts-Apps betrachtet. Das SDK legt die Prozessidentität auf den registrierten Benutzer fest. Um die Unterstützung für mehrere Identitäten zu aktivieren, fügen Sie dem Wörterbuch „IntuneMAMSettings“ in der Datei „Info.plist“ der App eine boolesche Einstellung mit dem Namen `MultiIdentity` und dem Wert „YES“ hinzu.

> [!NOTE]
> Wenn die Unterstützung für mehrere Identitäten aktiviert ist, werden die Prozessidentität, die Benutzeroberflächenidentität und die Threadidentitäten auf „nil“ festgelegt. Es ist Aufgabe der App, die entsprechenden Einstellungen vorzunehmen.

### <a name="switch-identities"></a>Wechseln von Identitäten

* **Von der App eingeleiteter Identitätswechsel**:

    Beim Starten werden mehrere Identitäten als unter einem unbekannten, nicht verwalteten Konto angesehen. Die Benutzeroberfläche für einen bedingten Start wird nicht ausgeführt, und es werden keine Richtlinien auf die App angewendet. Die App muss das SDK bei jedem beabsichtigten Wechsel der Identität benachrichtigen. Normalerweise geschieht das, wenn die App im Begriff ist, Daten für ein bestimmtes Benutzerkonto anzuzeigen.

    Ein Beispiel dafür ist, wenn der Benutzer versucht, ein Dokument, ein Postfach oder eine Registerkarte in einem Notizbuch zu öffnen. Die App muss das SDK informieren, bevor diese Datei, dieses Postfach oder diese Registerkarte tatsächlich geöffnet wird. Dies erfolgt mithilfe der `setUIPolicyIdentity`-API in `IntuneMAMPolicyManager`. Diese API sollte aufgerufen werden, unabhängig davon, ob der Benutzer verwaltet ist. Wenn der Benutzer verwaltet ist, führt das SDK die Prüfungen für den bedingten Start aus (z. B. Jailbreakerkennung, PIN und Authentifizierung).

    Das Ergebnis des Identitätswechsels wird asynchron mithilfe eines Abschlusshandlers an die App zurückgegeben. Die App sollte mit dem Öffnen von Dokument, Postfach oder Registerkarte solange warten, bis ein Ergebniscode für den Erfolg zurückgegeben wird. Bei einem Fehler beim Identitätswechsel sollte die App die Aufgabe abbrechen.

* **Vom SDK initiierter Wechsel der Identität**:

    Manchmal muss das SDK die App bitten, zu einer bestimmten Identität zu wechseln. Apps mit mehreren Identitäten müssen die `identitySwitchRequired`-Methode in `IntuneMAMPolicyDelegate` implementieren, um dieser Aufforderung zu folgen.

    Wenn die App beim Aufruf der Methode imstande ist, die Anforderung des Wechselns zu einer angegebenen Identität auszuführen, sollte sie `IntuneMAMAddIdentityResultSuccess` im Abschlusshandler übergeben. Wenn sie den Identitätswechsel nicht vornehmen kann, sollte die App `IntuneMAMAddIdentityResultFailed` im Abschlusshandler übergeben.

    Als Reaktion auf diesen Aufruf muss die App nicht `setUIPolicyIdentity` aufrufen. Wenn das SDK bei der App den Wechsel zu einem nicht verwalteten Benutzerkonto anfordern muss, wird im Aufruf `identitySwitchRequired` eine leere Zeichenfolge übergeben.

* **Selektives Zurücksetzen**:

    Wenn die App selektiv zurückgesetzt wird, ruft das SDK die `wipeDataForAccount`-Methode in `IntuneMAMPolicyDelegate` auf. Es ist Aufgabe der App, das Konto des angegebenen Benutzers und alle ihm zugeordneten Daten zu entfernen. Das SDK ist imstande, alle Dateien im Besitz des Benutzer zu entfernen, und führt dies durch, wenn von der App auf den `wipeDataForAccount`-Aufruf „FALSE“ zurückgegeben wird.

    Beachten Sie, dass diese Methode aus einem Hintergrundthread aufgerufen wird. Die App sollte keinen Wert zurückgeben, bevor alle Daten für den Benutzer entfernt wurden (mit Ausnahme der Dateien, wenn die App „FALSE“ zurückgibt).

## <a name="ios-best-practices"></a>Empfohlene Methoden für iOS

Hier finden Sie empfohlene und bewährte Methoden für die Entwicklung für iOS:

* Beim iOS-Dateisystem werden Groß-/Kleinschreibung berücksichtigt. Vergewissern Sie sich, dass Dateinamen wie `libIntuneMAM.a` und `IntuneMAMResources.bundle` die richtige Groß-/Kleinschreibung aufweisen.

* Wenn Xcode Probleme beim Suchen nach `libIntuneMAM.a` hat, können Sie das Problem beheben, indem Sie den Pfad zu dieser Bibliothek den Linkersuchpfaden hinzufügen.

## <a name="faqs"></a>Häufig gestellte Fragen

### <a name="are-all-of-the-apis-addressable-through-native-swift-or-the-objective-c-and-swift-interoperability"></a>Sind alle APIs durch die native Swift- oder die Objective-C- und Swift-Interoperabilität erreichbar?

Die Intune App SDK-APIs arbeiten ausschließlich in der Objective-C-Programmiersprache und unterstützen nicht die **native** Sprache Swift. Swift-Interoperabilität mit Objective-C ist erforderlich.

### <a name="do-all-users-of-my-application-need-to-be-registered-with-the-app-we-service"></a>Müssen alle Benutzer meiner Anwendung beim APP-WE-Dienst registriert werden?

Nein. Nur Arbeits-, Schul- oder Unikonten sollten beim Intune App SDK registriert werden. Die Apps sind dafür zuständig, zu bestimmen, ob ein Konto in einem Arbeits-, Schul- oder Unikontext verwendet wird.

### <a name="what-about-users-that-have-already-signed-in-to-the-application-do-they-need-to-be-enrolled"></a>Was ist mit Benutzern, die bereits bei der Anwendung angemeldet sind? Müssen sie registriert werden?

Es ist Aufgabe der Anwendung, Benutzer zu registrieren, nachdem sie erfolgreich authentifiziert wurden. Die Anwendung muss außerdem alle vorhandenen Konten registrieren, die bereits vorhanden waren, bevor die Anwendung über MAM-Funktionalität ohne MDM-Registrierung verfügte.

Dies kann die App mit der `registeredAccounts:`-Methode machen. Diese Methode gibt ein NSDictionary zurück, das sämtliche beim Intune MAM-Dienst registrierten Konten enthält. Wenn in der Anwendung bestehende Konten in der Liste nicht vorhanden sind, sollte die Anwendung diese Konten mithilfe von `registerAndEnrollAccount:` registrieren.

### <a name="how-often-does-the-sdk-retry-enrollments"></a>Wie oft wiederholt das SDK Registrierungsversuche?

Das SDK wiederholt alle zuvor mit einem Fehler abgebrochenen Registrierungsversuche in einem 24-Stunden-Intervall. Das SDK geht so vor, um sicherzustellen, dass ein Benutzer erfolgreich registriert wird und Richtlinien auf sein Konto angewendet werden, wenn die Organisation MAM erst nach der Anmeldung des Benutzers bei der Anwendung aktiviert hat.

Das SDK stellt die Wiederholungsversuche ein, wenn es feststellt, dass ein Benutzer die Anwendung erfolgreich registriert hat. Dies hat den Grund, dass immer nur ein Benutzer eine Anwendung registrieren kann. Wenn die Registrierung des Benutzers aufgehoben wird, beginnen die Registrierungsversuche wieder mit dem gleichen 24-Stunden-Intervall.

### <a name="why-does-the-user-need-to-be-deregistered"></a>Warum muss die Registrierung des Benutzers aufgehoben werden?

Das SDK führt im Hintergrund in regelmäßigen Abständen die folgenden Aktionen aus:

* Wenn die Anwendung noch nicht registriert ist, versucht es, alle registrierten Konten alle 24 Stunden zu registrieren.
* Wenn die Anwendung registriert ist, prüft das SDK alle 8 Stunden auf MAM-Richtlinienaktualisierungen.

Durch Aufheben der Registrierung eines Benutzers teilt die Anwendung dem SDK mit, dass der Benutzer die Anwendung nicht mehr verwendet und alle regelmäßigen Aktionen für dieses Benutzerkonto vom SDK eingestellt werden können. Dadurch werden außerdem das Aufheben der Registrierung und ggf. das selektive Zurücksetzen ausgelöst.

### <a name="should-i-set-the-dowipe-flag-to-true-in-the-deregister-method"></a>Soll das doWipe-Flag in der Methode zum Aufheben der Registrierung auf WAHR festgelegt werden?

Diese Methode sollte aufgerufen werden, bevor der Benutzer bei der Anwendung abgemeldet wird.  Wenn die Daten des Benutzers im Rahmen der Abmeldung aus der Anwendung gelöscht werden, kann `doWipe` auf „false“ festgelegt werden. Wenn die Anwendung die Daten des Benutzers jedoch nicht entfernt, sollte `doWipe` auf „true“ festgelegt werden, damit das SDK die Daten löschen kann.

### <a name="are-there-any-other-ways-that-an-application-can-be-un-enrolled"></a>Gibt es andere Möglichkeiten zum Aufheben der Registrierung einer Anwendung?

Ja, der IT-Administrator kann einen Befehl zum selektiven Zurücksetzen an die Anwendung senden. Dadurch wird die Registrierung aufgehoben und der Benutzer abgemeldet, und die Daten des Benutzers werden zurückgesetzt. Das SDK wickelt dieses Szenario automatisch ab und sendet mithilfe der Stellvertretermethode zum Aufheben der Registrierung eine Benachrichtigung.

### <a name="is-there-a-sample-app-that-demonstrates-how-to-integrate-the-sdk"></a>Gibt es eine Beispiel-App, in der die Integration des SDK gezeigt wird?

Ja! Wir haben vor Kurzem die Open-Source-Beispiel-App [Wagr für iOS](https://github.com/Microsoft/Wagr-Sample-Intune-iOS-App) überarbeitet. Wagr ist jetzt auch für App-Schutzrichtlinien aktiviert, die mit dem Intune App SDK bereitgestellt werden.

## <a name="submit-your-app-to-the-app-store"></a>Übermitteln Ihrer App an den App Store

Sowohl die statische Bibliothek als auf Frameworkbuilds des Intune App SDK sind universelle Binärdateien. Das bedeutet, dass sie Code für alle Geräte- und Simulatorarchitekturen enthalten. Apple lehnt für den App Store eingereichte Apps ab, wenn sie Simulatorcode enthalten. Wenn mit der statischen Bibliothek für Builds nur für Geräte kompiliert wird, entfernt der Linker automatisch den Simulatorcode. Gehen Sie folgendermaßen vor, um sicherzustellen, dass der gesamte Simulatorcode entfernt wird, bevor Sie Ihre App in den App Store hochladen.

1. Stellen Sie sicher, dass sich `IntuneMAM.framework` auf dem Desktop befindet.

2. Führen Sie diese Befehle aus:

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```
    Der erste Befehl entfernt die Simulatorarchitekturen aus der DYLIB-Datei des Frameworks. Der zweite Befehl kopiert die nur für Geräte zuständige DYLIB-Datei wieder in das Frameworkverzeichnis.
