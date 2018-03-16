---
title: "Microsoft Intune App SDK für iOS –Entwicklerhandbuch"
description: "Mit dem Microsoft Intune App SDK für iOS können Sie die Intune-App-Schutzrichtlinien (auch als APP- oder MAM-Richtlinien bezeichnet) in Ihre native iOS-App integrieren."
keywords: 
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 01/10/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 49ffac609ec24917b8490c535ebd74c6d2729ccd
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Microsoft Intune App SDK für iOS –Entwicklerhandbuch

> [!NOTE]
> Lesen Sie am besten zuerst den Artikel [Erste Schritte mit dem Intune App SDK](app-sdk-get-started.md). Darin finden Sie Informationen, welche Vorbereitungen Sie für die Integration auf jeder unterstützten Plattform treffen müssen.

Mit dem Microsoft Intune App SDK für iOS können Sie die Intune-App-Schutzrichtlinien (auch als **APP**- oder **MAM-Richtlinien** bezeichnet) in Ihre native iOS-App integrieren. Als MAM-fähige App wird eine App bezeichnet, die in das Intune App SDK integriert ist. Sie ermöglichen IT-Administratoren, App-Schutzrichtlinien für Ihre mobile App bereitzustellen, wenn diese aktiv von Intune verwaltet wird.

## <a name="prerequisites"></a>Voraussetzungen

* Sie benötigen einen macOS-Computer, auf dem OS X 10.8.5 oder höher ausgeführt wird und auf dem Xcode 9 oder höher installiert ist.

* Ihre App muss für iOS 9.3.5 oder höher vorgesehen sein.

* Lesen Sie [die Lizenzbedingungen für das Intune App SDK für iOS (in englischer Sprache)](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS%20.pdf). Drucken Sie sich eine Kopie der Lizenzbedingungen aus und bewahren Sie diese in Ihren Unterlagen auf. Indem Sie das Intune App SDK für iOS herunterladen und verwenden, stimmen Sie diesen Lizenzbestimmungen zu.  Wenn Sie den Lizenzbedingungen nicht zustimmen, verwenden Sie die Software nicht.

* Laden Sie die Dateien für das Intune App SDK für iOS von [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) herunter.

## <a name="whats-in-the-sdk"></a>Inhalt des SDK

Das Intune App SDK für iOS enthält eine statische Bibliothek, Ressourcendateien, API-Header, eine PLIST-Datei Liste mit Debug-Einstellungen sowie ein Konfigurationstool. Mobile Apps können einfach nur die Ressourcendateien enthalten und statisch mit den Bibliotheken verknüpft sein, um die meisten Richtlinien durchzusetzen. Erweiterte Intune-MAM-Funktionen werden mithilfe von APIs erzwungen.

Dieses Handbuch befasst sich mit der Verwendung der folgenden Komponenten des Intune App SDK für iOS:

* **libIntuneMAM.a**: Die statische Intune App SDK-Bibliothek. Wenn Ihre App keine Extensions verwendet, können Sie diese Bibliothek mit Ihrem Projekt verknüpfen, um die App für die mobile Anwendungsverwaltung mit Intune zu aktivieren.

* **IntuneMAM.framework**: Das Intune App SDK-Framework. Verknüpfen Sie dieses Framework mit Ihrem Projekt, um die App für die mobile Anwendungsverwaltung mit Intune zu aktivieren. Verwenden Sie das Framework anstelle der statischen Bibliothek, wenn in Ihrer App Erweiterungen verwendet werden, damit Ihr Projekt nicht mehrere Kopien der statischen Bibliothek erstellt.

* **IntuneMAMResources.Bundle**: Ein Ressourcenpaket, das die Ressourcen für das SDK enthält.

* **Headers**: Stellt die Intune App SDK-APIs bereit. Wenn Sie eine API verwenden, müssen Sie die Headerdatei einschließen, die die API enthält. Die folgenden Headerdateien enthalten die APIs, die Datentypen und die Protokolle, die vom Intune App SDK für Entwickler zur Verfügung gestellt wurden:

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

Führen Sie die folgenden Schritte aus, um das Intune App SDK zu aktivieren:

1. **Option 1 (empfohlen)**: Verknüpfen Sie `IntuneMAM.framework` mit Ihrem Projekt. Ziehen Sie `IntuneMAM.framework` in die Liste für **eingebettete Binärdateien** des Projektziels.

    > [!NOTE]
    > Bei Verwendung des Frameworks müssen Sie die Simulatorarchitekturen manuell aus dem universellen Framework entfernen, bevor Sie Ihre App an den App Store übermitteln. Weitere Informationen siehe [Übermitteln Ihrer App an den App Store](#Submit-your-app-to-the-App-Store).

2. **Option 2**: Stellen Sie eine Verknüpfung zur `libIntuneMAM.a`-Bibliothek her. Ziehen Sie die `libIntuneMAM.a`-Bibliothek in die Liste **Verknüpfte Frameworks und Bibliotheken** des Projektziels.

    ![Intune App SDK iOS – verknüpfte Frameworks und Bibliotheken](./media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    Fügen Sie `-force_load {PATH_TO_LIB}/libIntuneMAM.a` einem der folgenden Pfade hinzu, wobei Sie `{PATH_TO_LIB}` durch den Speicherort des Intune App SDK ersetzen:
      * Der Buildkonfigurationseinstellung `OTHER_LDFLAGS` des Projekts
      * Benutzeroberflächenoption **Other Linker Flags** (Andere Linker-Flags) von Xcode

        > [!NOTE]
        > Um den `PATH_TO_LIB` zu suchen, wählen Sie die Datei `libIntuneMAM.a` und dann im Menü **Datei** die Option **Informationen abrufen** aus. Kopieren Sie den **Pfad** aus dem Abschnitt **Allgemein** im Fenster **Info**.

    Fügen Sie das Ressourcenpaket `IntuneMAMResources.bundle` zum Projekt hinzu, indem Sie es in **Buildphasen** unter **Paketressourcen kopieren** ziehen.

    ![Intune App SDK iOS: Paketressourcen kopieren](./media/intune-app-sdk-ios-copy-bundle-resources.png)

    Fügen Sie diese iOS-Frameworks zum Projekt hinzu:  
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
    ```xml
    <key>keychain-access-groups</key>
    <array>
    <string>YOURBUNDLESEEDID.*</string>
    </array>
    ```

4. Nachdem Sie die Freigabe des Schlüsselbunds aktiviert haben, folgen Sie den nachstehenden Schritten, um eine separate Zugriffsgruppe zu erstellen, in der das Intune App SDK seine Daten speichert. Sie können eine Zugriffsgruppe für den Schlüsselbund über die Benutzeroberfläche oder mithilfe der Berechtigungsdatei erstellen. Wenn Sie die Benutzeroberfläche zum Erstellen der Zugriffsgruppe für den Schlüsselbund verwenden, führen Sie unbedingt die folgenden Schritte aus:

    1. Wenn in Ihrer mobilen App keine Zugriffsgruppen für den Schlüsselbund definiert sind, fügen Sie die Paket-ID der App als erste Gruppe hinzu.

    2. Fügen Sie die freigegebene Zugriffsgruppe für den Schlüsselbund `com.microsoft.intune.mam` Ihren vorhandenen Zugriffsgruppen hinzu. Diese Zugriffsgruppe wird vom Intune App SDK zum Speichern von Daten verwendet.

    3. Fügen Sie `com.microsoft.adalcache` zu Ihren vorhandenen Zugriffsgruppen hinzu.

        ![Intune App SDK für iOS: Schlüsselbund gemeinsam nutzen](./media/intune-app-sdk-ios-keychain-sharing.png)

    4. Wenn Sie die Berechtigungsdatei direkt bearbeiten, anstatt die oben gezeigte Xcode-Benutzeroberfläche zum Erstellen der Schlüsselbund-Zugriffsgruppen zu verwenden, setzen Sie `$(AppIdentifierPrefix)` vor die Schlüsselbund-Zugriffsgruppen (Xcode verarbeitet dies automatisch). Beispiel:

            * `$(AppIdentifierPrefix)com.microsoft.intune.mam`
            * `$(AppIdentifierPrefix)com.microsoft.adalcache`

    > [!NOTE]
    > Eine Berechtigungsdatei ist eine XML-Datei, die Ihrer App eindeutig zugeordnet werden kann. Sie wird zum Festlegen spezieller Berechtigungen und Funktionen in Ihrer iOS-App verwendet. Wenn Ihre App vorher noch keine Berechtigungsdatei hatte, sollte die Aktivierung der Schlüsselbundfreigabe (Schritt 3) dazu geführt haben, dass Xcode eine für Ihre App generiert hat.

5. Nehmen Sie jedes Protokoll, das Ihre App an `UIApplication canOpenURL` übergibt, in das `LSApplicationQueriesSchemes`-Array der Datei „Info.plist“ Ihrer App auf. Speichern Sie Ihre Änderungen, bevor Sie mit dem nächsten Schritt fortfahren.

6. Verwenden Sie das im [SDK-Repository](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) enthaltene IntuneMAMConfigurator-Tool, um die Konfiguration der Datei „Info.plist“ Ihrer App abzuschließen. Das Tool weist 3 Parameter auf:
|Eigenschaft|Verwendung|
|---------------|--------------------------------|
|- i |  `<Path to the input plist>` |
|- e | `<Path to the entitlements file>` |
|- o |  (Optional) `<Path to the output plist>` |

Wenn der Parameter „-o“ nicht angegeben ist, wird die Eingabedatei direkt geändert. Das Tool ist idempotent und sollte immer dann erneut ausgeführt werden, wenn Änderungen an der Datei „Info.plist“ der App oder den Berechtigungen vorgenommen wurden. Bei der Aktualisierung des Intune-SDK sollten Sie auch die neueste Version des Tools herunterladen und ausführen, für den Fall, dass sich die Konfigurationsanforderungen von „Info.plist“ im letzten Release geändert haben.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Konfigurieren der Authentifizierungsbibliothek von Azure Active Directory (Active Directory Authentication Library, ADAL)

Das Intune App SDK verwendet die [Authentifizierungsbibliothek von Azure Active Directory](https://github.com/AzureAD/azure-activedirectory-library-for-objc) für die Authentifizierung und bedingte Startszenarien. Außerdem ist es davon abhängig, dass ADAL die Benutzeridentität im MAM-Dienst für das Verwalten registriert, ohne dafür Geräteregistrierungsszenarios zu benötigen.

Normalerweise setzt ADAL voraus, dass Apps sich bei Azure Active Directory (AAD) registrieren und eine eindeutige ID (Client-ID) sowie weitere Bezeichner abrufen, um die Sicherheit der Token zu gewährleisten, die an die Anwendung übermittelt werden. Sofern nicht anders angegeben, verwendet das Intune App SDK bei der Kontaktaufnahme mit Azure AD standardmäßige Registrierungswerte.  

Wenn Ihre App bereits ADAL zum Authentifizieren von Benutzern verwendet, muss sie ihre vorhandenen Registrierungswerte verwenden und die Standardwerte des Intune App SDK überschreiben. So wird sichergestellt, dass Benutzer nicht zweimal aufgefordert werden, sich zu authentifizieren (jeweils einmal vom Intune App SDK und einmal von der App).

### <a name="recommendations"></a>Empfehlungen

Ihre App sollte mit der [aktuellen Version von ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) auf deren Hauptverzweigung verknüpft sein. Das Intune App SDK verwendet derzeit den Brokerbranch von ADAL, um Apps zu unterstützen, für die bedingter Zugriff erforderlich ist. (Deshalb hängen diese Apps von der Microsoft Authenticator-App ab.) Das SDK ist trotzdem mit dem Hauptbranch von ADAL kompatibel. Verwenden Sie den Branch, der am besten zu Ihrer App passt.

### <a name="link-to-adal-binaries"></a>Verknüpfung mit ADAL-Binärdateien

Gehen Sie folgendermaßen vor, um Ihre App mit den ADAL-Binärdateien zu verknüpfen:

1. Laden Sie die [Authentifizierungsbibliothek von Azure Active Directory (ADAL) für Objective-C](https://github.com/AzureAD/azure-activedirectory-library-for-objc) von GitHub herunter, und befolgen Sie dann die [Anweisungen](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download) zum Herunterladen von ADAL mithilfe von Git-Submodulen oder CocoaPods.

2. Fügen Sie das ADAL-Framework (Option 1) oder die statische Bibliothek (Option 2) zu Ihrem Projekt hinzu:
    
    **Option 1 (empfohlen)**: Ziehen Sie `ADAL.framework` in die Liste **Eingebettete Binärdateien** des Projektziels.
    
    **Option 2**: Ziehen Sie die `libADALiOS.a`-Bibliothek in die Liste **Verknüpfte Frameworks und Bibliotheken** des Projektziels. Fügen Sie `-force_load {PATH_TO_LIB}/libADALiOS.a` der `OTHER_LDFLAGS`-Buildkonfigurationseinstellung des Projekts hinzu, oder legen Sie auf der Xcode-Benutzeroberfläche **Other Linker Flags** (Andere Linker-Flags) fest. `PATH_TO_LIB` sollte durch den Speicherort der ADAL-Binärdateien ersetzt werden.



### <a name="share-the-adal-token-cache-with-other-apps-signed-with-the-same-provisioning-profile"></a>Freigeben des ADAL-Tokencaches für andere Apps, die mit dem gleichen Bereitstellungsprofil signiert wurden?**

Befolgen Sie die unten stehenden Anweisungen, wenn Sie ADAL-Token für Apps freigeben möchten, die mit dem gleichen Bereitstellungsprofil signiert wurden:

1. Wenn in Ihrer App keine Zugriffsgruppen für den Schlüsselbund definiert sind, fügen Sie die Paket-ID der App als erste Gruppe hinzu.

2. Aktivieren Sie ADAL-SSO (einmaliges Anmelden), indem Sie den Schlüsselbundzugriffsgruppen `com.microsoft.adalcache` hinzufügen.

3. Wenn Sie eine benutzerdefinierte Schlüsselbundgruppe angeben möchten, die `com.microsoft.adalcache` ersetzt, geben Sie sie in der Datei „Info.plist“ mithilfe des Schlüssels `ADALCacheKeychainGroupOverride` unter „IntuneMAMSettings“ an.

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

> [!NOTE]
    > Der Ansatz mit „Info.plist“ empfiehlt sich für alle Einstellungen, die statisch sind und nicht zur Runtime ermittelt werden müssen. Die den `IntuneMAMPolicyManager`-Eigenschaften zugewiesenen Werte haben Vorrang vor den entsprechenden in „Info.plist“ angegebenen Werten und werden auch nach dem Neustart der App beibehalten. Das SDK verwendet diese weiterhin für das Einchecken von Richtlinien, bis die Registrierung des Benutzers aufgehoben wird oder die Werte gelöscht oder geändert werden.

### <a name="if-your-app-does-not-use-adal"></a>Wenn Ihre Anwendung ADAL nicht verwendet

Wenn Ihre App ADAL nicht verwendet, stellt das Intune App SDK Standardwerte für ADAL-Parameter und behandelt die Authentifizierung in Azure AD. Sie müssen keine Werte für die oben aufgeführten ADAL-Einstellungen angeben.

## <a name="receiving-app-protection-policy"></a>Erhalten der App-Schutzrichtlinie

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

Apps, die den Benutzer nicht mit ADAL anmelden, können trotzdem App-Schutzrichtlinien vom Intune-MAM-Dienst empfangen, indem sie die API aufrufen, um die Authentifizierung vom SDK ausführen zu lassen. Apps sollten diese Technik verwenden, wenn zwar keine Benutzer mit Azure AD authentifiziert wurden, aber trotzdem App-Schutzrichtlinien zum Schutz der Daten abgerufen werden müssen. Beispielsweise, wenn ein anderer Authentifizierungsdienst für die App-Anmeldung verwendet wird oder wenn die App überhaupt kein Anmelden unterstützt. Zu diesem Zweck sollte die Anwendung die `loginAndEnrollAccount`-Methode auf der `IntuneMAMEnrollmentManager`-Instanz aufrufen:

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
 *  until the Intune MAM AAD token is acquired, then return.  This method must be called before  
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

 - Registrierungsanforderungen
 - Anforderungen zur Richtlinienaktualisierung
 - Anfragen zur Aufhebung der Registrierung

Die Benachrichtigungen werden über Stellvertretermethoden in `Headers/IntuneMAMEnrollmentDelegate.h` angezeigt:

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

- Die Identität der Kontos, dem die Anforderung zugeordnet ist
- Ein Statuscode, der das Ergebnis der Anforderung anzeigt
- Eine Fehlerzeichenfolge mit einer Beschreibung des Statuscodes
- Ein `NSError`-Objekt

Dieses Objekt ist in `IntuneMAMEnrollmentStatus.h` zusammen mit den spezifischen Statuscodes definiert, die zurückgegeben werden können.


### <a name="sample-code"></a>Beispielcode

Die folgenden Beispiele zeigen Implementierungen der Stellvertretermethoden:

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}


- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

```

## <a name="app-restart"></a>App-Neustart

Wenn eine Anwendung zum ersten Mal App-Schutzrichtlinien empfängt, muss sie neu gestartet werden, um die erforderlichen Hooks anzuwenden. Das SDK stellt eine Delegatmethode unter Header/IntuneMAMEnrollment.h bereit, um die App zu informieren, dass sie neu gestartet werden muss.

```objc
 - (BOOL) restartApplication
```
Der Rückgabewert dieser Methode teilt dem SDK mit, ob die Anwendung den erforderlichen Neustart übernehmen muss:   

 - Wenn „true“ zurückgegeben wird, muss die Anwendung den Neustart ausführen.   

 - Wenn „FALSE“ zurückgegeben wird, startet das SDK die App neu, nachdem die Methode zurückkehrt. Das SDK zeigt sofort im Anschluss ein Dialogfeld an, dass den Benutzer informiert, dass er die App neu starten muss.

## <a name="customize-your-apps-behavior"></a>Passen Sie das Verhalten Ihrer App an

Das Intune App SDK hat mehrere APIs, die Sie aufrufen können, um Informationen über die App-Schutzrichtlinie in Intune zu erhalten, die der App bereitgestellt wurde. Diese Daten können Sie benutzen, um das Verhalten Ihrer App anzupassen. Die meisten Einstellungen für App-Schutzrichtlinien werden automatisch vom SDK und nicht von der Anwendung erzwungen. Die einzige Einstellung, die die App implementieren sollte, ist das Steuerelement „Speichern unter“.

### <a name="get-app-protection-policy"></a>Abrufen der App-Schutzrichtlinie

#### <a name="intunemampolicymanagerh"></a>IntuneMAMPolicyManager.h
Die Klasse „IntuneMAMPolicyManager“ stellt die App-Schutzrichtlinie für Intune, die für die App bereitgestellt wurde, bereit. Sie stellt besonders APIs bereit, die beim [Aktivieren mehrerer Identitäten](#-enable-multi-identity-optional) nützlich sind.

#### <a name="intunemampolicyh"></a>IntuneMAMPolicy.h
Die „IntuneMAMPolicy“-Klasse stellt die App-Schutzrichtlinie für Intune, die für die App bereitgestellt wurde, bereit. Die meisten der in dieser Klasse bereitgestellten Richtlinieneinstellungen werden vom SDK erzwungen, aber Sie haben immer die Möglichkeit, das Verhalten Ihrer App anzupassen, je nachdem, wie Richtlinieneinstellungen erzwungen werden.

Diese Klasse stellt einige APIs bereit, die für die Implementierung von „Speichern unter“-Steuerelementen benötigt werden; Details dazu finden Sie im nächsten Abschnitt.

### <a name="implement-save-as-controls"></a>Implementieren von „Speichern unter“-Steuerelementen

Mit Intune können IT-Administratoren auswählen, an welchem Speicherort eine verwaltete App Daten speichern kann. Mit der **isSaveToAllowedForLocation**-API können Apps das Intune-App SDK nach zulässigen Speicherorten abfragen, wie in **IntuneMAMPolicy.h** definiert.

Bevor Apps verwaltete Daten in einem Cloudspeicher oder einem lokalen Pfad speichern können, müssen sie mit der **isSaveToAllowedForLocation**-API überprüfen, ob der IT-Administrator erlaubt hat, die Daten dort zu speichern.

Bei Verwendung der **isSaveToAllowedForLocation**-API müssen Apps den UPN für den Speicherort einreichen, falls er verfügbar ist.

#### <a name="supported-save-locations"></a>Unterstützte Speicherorte

Die **isSaveToAllowedForLocation**-API stellt Konstanten bereit, um zu prüfen, ob der IT-Administrator das Speichern von Daten an folgenden Orten erlaubt, wie in IntuneMAMPolicy.h definiert:

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

Apps sollten die Konstanten in der **isSaveToAllowedForLocation**-API verwenden, um zu überprüfen, ob Daten an Speicherorten gespeichert werden können, die als „verwaltet“ (z. B. OneDrive for Business) oder „privat“ gelten. Darüber hinaus sollte die API verwendet werden, wenn die App nicht ermitteln kann, ob es sich um „verwaltete“ oder „private“ Speicherorte handelt.

Persönliche Speicherorte werden durch die Konstante `IntuneMAMSaveLocationOther` repräsentiert.

Die Konstante `IntuneMAMSaveLocationLocalDrive` sollte verwendet werden, wenn die App Daten an einem beliebigen Speicherort auf dem lokalen Gerät speichert.

## <a name="configure-settings-for-the-intune-app-sdk"></a>Konfigurieren der Einstellungen für Intune App SDK

Sie können das Wörterbuch **IntuneMAMSettings** in der Datei „info.plist“ der Anwendung verwenden, um das Intune App SDK einzurichten und zu konfigurieren. Wenn das IntuneMAMSettings-Wörterbuch in der Datei „Info.plist“ nicht angezeigt wird, sollten Sie ein Wörterbuch in der „Info.plist“ Ihrer App mit dem Feldnamen „IntuneMAMSettings.“ erstellen.

Im IntuneMAMSettings-Wörterbuch können Sie Schlüssel-Wert-Zeilen mit Konfigurationseinstellungen zum Konfigurieren des SDK hinzufügen. Die folgende Tabelle enthält eine Liste aller unterstützten Einstellungen.

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
DebugSettingsEnabled| Boolesch | Bei der Einstellung JA können innerhalb des Einstellungspakets Testrichtlinien angewendet werden. Diese Einstellungen sollte bei ausgelieferten Anwendungen *nicht* aktiviert sein. | (Optional) |
MainNibFile<br>MainNibFile~ipad  | Zeichenfolge  | Diese Einstellung sollte den Namen der Haupt-NIB-Datei der Anwendung enthalten.  | Erforderlich, wenn MainNibFile für die Anwendung in der Datei „Info.plist“ definiert ist. |
MainStoryboardFile<br>MainStoryboardFile~ipad  | Zeichenfolge  | Diese Einstellung sollte den Namen der Haupt-Storyboard-Datei der Anwendung enthalten. | Erforderlich, wenn UIMainStoryboardFile für die Anwendung in der Datei „Info.plist“ definiert ist. |
AutoEnrollOnLaunch| Boolesch| Gibt an, ob die App versuchen soll, sich beim Start automatisch zu registrieren, wenn eine vorhandene verwaltete Identität erkannt wurde und dies noch nicht passiert ist. Standardwert ist "NO". <br><br> Hinweise: Wenn keine verwaltete Identität gefunden wird oder kein gültiges Token für die Identität im ADAL-Cache verfügbar ist, schlägt die Registrierung ohne die Anforderung nach Anmeldeinformationen im Hintergrund fehl, es sei denn, MAMPolicyRequired ist auf JA festgelegt. | (Optional) |
MAMPolicyRequired| Boolesch| Gibt an, ob das Starten der App blockiert ist, wenn die App über keine Intune App-Schutzrichtlinie verfügt. Standardwert ist "NO". <br><br> Hinweise: Apps, bei denen die MAMPolicyRequired-Einstellung auf „JA“ festgelegt ist, können nicht im App Store eingereicht werden. Wenn MAMPolicyRequired auf JA festgelegt wird, muss auch AutoEnrollOnLaunch auf JA festgelegt werden. | (Optional) |
MAMPolicyWarnAbsent | Boolesch| Gibt an, ob die App den Benutzer beim Start warnt, wenn die App keine App-Schutzrichtlinie für Intune hat. <br><br> Hinweis: Benutzer dürfen noch immer die App ohne Richtlinie verwenden, nachdem die Warnung verworfen wurde. | (Optional) |
MultiIdentity | Boolesch| Gibt an, ob die App den Umgang mit mehreren Identitäten beherrscht. | (Optional) |
SplashIconFile <br>SplashIconFile~ipad | Zeichenfolge  | Gibt die Datei für das Intune-Begrüßungssymbol (Startsymbol) an. | (Optional) |
SplashDuration | Zahl | Mindestdauer in Sekunden, für die der Intune Startbildschirm beim Anwendungsstart angezeigt wird. Standardwert ist 1,5. | (Optional) |
BackgroundColor| Zeichenfolge| Gibt die Hintergrundfarbe für den Start- und den PIN-Bildschirm an. Akzeptiert eine hexadezimale RGB-Zeichenfolge im Format „#XXXXXX“, wobei X Werte von 0-9 bzw. A-F annehmen kann. Das Gatterzeichen kann ausgelassen werden.   | (Optional) Der Standardwert ist „Hellgrau“. |
ForegroundColor| Zeichenfolge| Gibt die Vordergrundfarbe für den Start- und den PIN-Bildschirm an, etwa die Textfarbe. Nimmt eine hexadezimale RGB-Zeichenfolge der Form #XXXXXX an, wobei X zwischen 0 und 9 oder A und F liegen kann. Das Gatterzeichen kann ausgelassen werden.  | (Optional) Der Standardwert ist „Schwarz“. |
AccentColor | Zeichenfolge| Gibt die Akzentfarbe für den PIN-Bildschirm an, etwa die Textfarbe einer Schaltfläche oder die Hervorhebungsfarbe für ein Feld. Akzeptiert eine hexadezimale RGB-Zeichenfolge im Format „#XXXXXX“, wobei X Werte von 0-9 bzw. A-F annehmen kann. Das Gatterzeichen kann ausgelassen werden.| (Optional) Der Standardwert ist „Blau“ (Systemfarbe). |
MAMTelemetryDisabled| Boolesch| Gibt an, ob das SDK keine Telemetriedaten an sein Back-End sendet.| (Optional) |
WebViewHandledURLSchemes | Array von Zeichenfolgen | Gibt die URL-Schemas an, die WebView für Ihre App verarbeitet. | Erforderlich, wenn Ihre App WebView verwendet, das URLs über Verknüpfungen und/oder JavaScript verarbeitet. |  

> [!NOTE]
> Gemäß den App Store-Standards muss `MAMPolicyRequired` auf „NO“ festgelegt sein, wenn Ihre App im App Store veröffentlicht werden soll.

## <a name="enabling-mam-targeted-configuration-for-your-ios-applications"></a>Aktivieren der MAM-Zielkonfiguration für Ihre iOS-Anwendungen
Die MAM-Zielkonfiguration ermöglicht, dass eine App Konfigurationsdaten über das Intune App SDK erhalten kann. Das Format und die Varianten dieser Daten müssen definiert und Intune-Kunden vom Besitzer oder Entwickler der Anwendung mitgeteilt werden. Intune-Administratoren können Konfigurationsdaten über das Intune Azure-Portal als Ziel festlegen und bereitstellen. Ab Version 7.0.1 des Intune App SDK für iOS können Apps, die zur MAM-Zielkonfiguration gehören, über den MAM-Dienst mit Konfigurationsdaten für MAM versorgt werden. Die Anwendungskonfigurationsdaten werden durch unseren MAM-Dienst direkt an die App übertragen, und nicht über den MDM-Kanal. Das Intune App SDK stellt eine Klasse für den Zugriff auf die Daten bereit, die aus diesen Konsolen abgerufen wurden. Folgende Voraussetzungen sind erforderlich: <br>
* Die App muss beim Intune-MAM-Dienst registriert werden, bevor Sie auf die Konfigurationsschnittstelle für MAM zugreifen. Weitere Informationen finden Sie unter [Erhalten der App-Schutzrichtlinie](#receiving-app-protection-policy).
* In der Quelldatei der App muss ```IntuneMAMAppConfigManager.h``` enthalten sein.
* Rufen Sie ```[[IntuneMAMAppConfigManager instance] appConfigForIdentity:]``` auf, um das App-Konfigurationsobjekt zu erhalten.
* Rufen Sie den entsprechenden Selektor auf dem Objekt ```IntuneMAMAppConfig``` auf. Wenn es sich zum Beispiel beim Schlüssel Ihrer Anwendung um eine Zeichenfolge handeln, könnten Sie ```stringValueForKey``` oder ```allStringsForKey``` verwenden. Die Datei ```IntuneMAMAppConfig.h header``` enthält Rückgabewerte und Fehlerbedingungen.

Weitere Informationen zu den Funktionen der Graph-API in Bezug auf die MAM-Zielkonfigurationswerte finden Sie unter [Graph API Reference MAM Targeted Config (Graph-API-Referenz für MAM-Zielkonfigurationen)](https://developer.microsoft.com/graph/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create). <br>

Weitere Informationen zum Erstellen einer MAM-Zielkonfigurationsrichtlinie für Apps in iOS finden Sie im Abschnitt zu MAM-Zielkonfiguration für Apps unter [How to use Microsoft Intune app configuration policies for iOS (Verwenden von Microsoft Intune-App-Konfigurationsrichtlinien für iOS)](https://docs.microsoft.com/intune/app-configuration-policies-use-ios).

## <a name="telemetry"></a>Telemetrie

Standardmäßig protokolliert das Intune App SDK für iOS Telemetriedaten zu den folgenden Nutzungsereignissen. Diese Daten werden an Microsoft Intune gesendet.

* **Start der App**: Übermittelt an Microsoft Intune Daten zur Nutzung von MAM-aktivierten Apps nach Verwaltungsart (MAM mit MDM, MAM ohne MDM-Registrierung usw.).

* **Registrierungsaufruf**: Übermittelt die Erfolgsquote und andere Leistungsindikatoren von Registrierungsaufrufen, die von der Clientseite initiiert wurden,an Microsoft Intune.

> [!NOTE]
> Wenn von Ihrer mobilen Anwendung keine Intune App SDK-Telemetriedaten an Microsoft Intune gesendet werden sollen, müssen Sie die Intune App SDK-Telemetrieerfassung deaktivieren. Legen Sie die Eigenschaft `MAMTelemetryDisabled` im IntuneMAMSettings-Wörterbuch auf „YES“ fest.

## <a name="enable-multi-identity-optional"></a>Aktivieren von Multi-Identity (optional)

Standardmäßig wird eine Richtlinie vom SDK auf die gesamte App angewendet. Die Unterstützung für mehrere Identitäten ist ein MAM-Feature, das Sie aktivieren können, um eine Richtlinie auf der Ebene einzelner Identitäten anzuwenden. Dies erfordert eine stärkere Beteiligung der App als andere MAM-Features.

Die App muss das App-SDK informieren, wenn sie die Änderung der aktiven Identität beabsichtigt. Das SDK benachrichtigt seinerseits die App, wenn eine Änderung der Identität erforderlich ist. Aktuell wird nur eine verwaltete Identität unterstützt. Nachdem der Benutzer das Gerät oder die App registriert hat, verwendet das SDK die dabei verwendete Identität und betrachtet sie als die primäre verwaltete Identität. Andere Benutzer der App werden als nicht verwaltet mit uneingeschränkten Richtlinieneinstellungen behandelt.

Beachten Sie, dass eine Identität einfach nur als Zeichenfolge definiert ist. Bei Identitäten werden Groß- und Kleinschreibung nicht unterschieden. Anforderungen einer Identität beim SDK werden möglicherweise nicht mit der gleichen Groß-/Kleinschreibung zurückgegeben, die ursprünglich beim Festlegen der Identität verwendet wurde.

### <a name="identity-overview"></a>Überblick: Identität

Eine Identität ist einfach der Benutzername eines Kontos (z.B. user@contoso.com). Entwickler können die Identität der App auf folgenden Ebenen festlegen:

* **Prozessidentität**: Legt die prozessweite Identität fest und wird in der Hauptsache für Anwendungen mit nur einer Identität verwendet. Diese Identität wirkt sich auf alle Aufgaben, Dateien und Benutzeroberflächen aus.

* **UI-Identität**: Legt fest, welche Richtlinien auf Benutzeroberflächenaufgaben im Hauptthread angewendet werden, z. B. Ausschneiden/Kopieren/Einfügen, PIN, Authentifizierung und Datenfreigabe. Die UI-Identität wirkt sich nicht auf Dateiaufgaben wie Verschlüsselung und Sicherung aus.

* **Threadidentität**: Wirkt sich darauf aus, welche Richtlinien auf den aktuellen Thread angewendet werden. Diese Identität betrifft alle Aufgaben, Dateien und die Benutzeroberfläche.

Es ist Aufgabe der App, die Identitäten passend für verwaltete und nicht verwaltete Benutzer festzulegen.

Jeder Thread weist jederzeit eine effektive Identität für Benutzeroberflächen- und Dateiaufgaben auf. Dies ist die Identität, mit der überprüft wird, welche Richtlinien, sofern zutreffend, angewendet werden sollen. Wenn die Identität „no identity“ ist oder der Benutzer nicht verwaltet ist, werden keine Richtlinien angewendet. Die unten stehenden Diagramme zeigen, wie effektive Identitäten bestimmt werden.

  ![Intune App SDK iOS – verknüpfte Frameworks und Bibliotheken](./media/ios-thread-identities.png)

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

### <a name="turning-on-multi-identity"></a>Aktivieren der Unterstützung für mehrere Identitäten

Standardmäßig werden Apps als Einzelidentitäts-Apps betrachtet. Das SDK legt die Prozessidentität auf den registrierten Benutzer fest. Um die Unterstützung für mehrere Identitäten zu aktivieren, fügen Sie dem Wörterbuch „IntuneMAMSettings“ in der Datei „Info.plist“ der App eine boolesche Einstellung mit dem Namen `MultiIdentity` und dem Wert „YES“ hinzu.

> [!NOTE]
> Wenn die Unterstützung für mehrere Identitäten aktiviert ist, werden die Prozessidentität, die Benutzeroberflächenidentität und die Threadidentitäten auf „nil“ festgelegt. Es ist Aufgabe der App, die entsprechenden Einstellungen vorzunehmen.

### <a name="switching-identities"></a>Wechseln von Identitäten

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


**Sind alle APIs über natives Swift oder über gleichzeitiges Objective-C und Swift zu erreichen?**

Die Intune App SDK-APIs arbeiten ausschließlich in der Objective-C-Programmiersprache und unterstützen nicht die **native** Sprache Swift. Swift-Interoperabilität mit Objective-C ist erforderlich.


**Müssen alle Benutzer meiner Anwendung beim APP-WE-Dienst registriert werden?**

Nein. Nur Arbeits-, Schul- oder Unikonten sollten beim Intune App SDK registriert werden. Die Apps sind dafür zuständig, zu bestimmen, ob ein Konto in einem Arbeits-, Schul- oder Unikontext verwendet wird.   

**Was ist mit Benutzern, die bereits bei der Anwendung angemeldet sind? Müssen sie registriert sein?**

Es ist Aufgabe der Anwendung, Benutzer zu registrieren, nachdem sie erfolgreich authentifiziert wurden. Die Anwendung muss außerdem alle vorhandenen Konten registrieren, die bereits vorhanden waren, bevor die Anwendung über MAM-Funktionalität ohne MDM-Registrierung verfügte.   

Dies kann die App mit der `registeredAccounts:`-Methode machen. Diese Methode gibt ein NSDictionary zurück, das sämtliche beim Intune MAM-Dienst registrierten Konten enthält. Wenn in der Anwendung bestehende Konten in der Liste nicht vorhanden sind, sollte die Anwendung diese Konten mithilfe von `registerAndEnrollAccount:` registrieren.

**Wie oft wiederholt das SDK Registrierungsversuche?**

Das SDK wiederholt alle zuvor mit einem Fehler abgebrochenen Registrierungsversuche in einem 24-Stunden-Intervall. Das SDK geht so vor, um sicherzustellen, dass ein Benutzer erfolgreich registriert wird und Richtlinien auf sein Konto angewendet werden, wenn die Organisation MAM erst nach der Anmeldung des Benutzers bei der Anwendung aktiviert hat.

Das SDK stellt die Wiederholungsversuche ein, wenn es feststellt, dass ein Benutzer die Anwendung erfolgreich registriert hat. Dies hat den Grund, dass immer nur ein Benutzer eine Anwendung registrieren kann. Wenn die Registrierung des Benutzers aufgehoben wird, beginnen die Registrierungsversuche wieder mit dem gleichen 24-Stunden-Intervall.

**Warum muss die Registrierung des Benutzers aufgehoben werden?**

Das SDK führt im Hintergrund in regelmäßigen Abständen die folgenden Aktionen aus:

 - Wenn die App noch nicht registriert wurde, versucht es, alle registrierten Konten in einem Abstand von 24 Stunden zu registrieren.
 - Wenn die Anwendung registriert ist, prüft das SDK alle 8 Stunden auf App-Schutzrichtlinienaktualisierungen.

Bei der Aufhebung der Registrierung eines Benutzers wird das SDK darüber informiert, dass der Benutzer die App nicht mehr verwendet, und dass alle regelmäßigen Aktionen für dieses Benutzerkonto beendet werden können. Dadurch werden außerdem das Aufheben der Registrierung und ggf. das selektive Zurücksetzen ausgelöst.

**Soll das doWipe-Flag in der deregister-Methode auf „YES“ festgelegt werden?**

Diese Methode sollte aufgerufen werden, bevor der Benutzer aus der App abgemeldet wird.  Wenn die Daten des Benutzers im Rahmen der Abmeldung aus der Anwendung gelöscht werden, kann `doWipe` auf „false“ festgelegt werden. Wenn die Anwendung die Daten des Benutzers jedoch nicht entfernt, sollte `doWipe` auf „true“ festgelegt werden, damit das SDK die Daten löschen kann.

**Gibt es andere Möglichkeiten zum Aufheben der Registrierung einer Anwendung?**

Ja, der IT-Administrator kann einen Befehl zum selektiven Zurücksetzen an die Anwendung senden. Dadurch wird die Registrierung aufgehoben und der Benutzer abgemeldet, und die Daten des Benutzers werden zurückgesetzt. Das SDK wickelt dieses Szenario automatisch ab und sendet mithilfe der Stellvertretermethode zum Aufheben der Registrierung eine Benachrichtigung.



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
