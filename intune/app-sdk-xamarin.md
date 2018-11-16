---
title: Microsoft Intune App SDK-Xamarin-Bindungen
description: Mit den Intune App SDK-Xamarin-Bindungen können Sie die Intune-App-Schutzrichtlinie in Ihren mit Xamarin erstellten iOS- und Android-Apps aktivieren.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune
ms.openlocfilehash: d2531cc203c5c2b255378e836099feb0a9216d45
ms.sourcegitcommit: cfce9318b5b5a3005929be6eab632038a12379c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51298121"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK-Xamarin-Bindungen

> [!NOTE]
> Lesen Sie am besten zuerst den Leitfaden [Erste Schritte mit dem Microsoft Intune App SDK](app-sdk-get-started.md). Dort finden Sie Informationen zu den Vorbereitungen, die Sie auf den verschiedenen unterstützten Plattformen für die Integration treffen müssen.

## <a name="overview"></a>Übersicht
Mit den [Intune App SDK-Xamarin-Bindungen](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) können Sie die [Intune-App-Schutzrichtlinie](app-protection-policy.md) in Ihren mit Xamarin erstellten iOS- und Android-Apps aktivieren. Die Bindungen ermöglichen es Entwicklern, App-Schutzfunktionen von Intune auf einfache Weise in ihre auf Xamarin basierenden Apps zu integrieren.

Mit den Microsoft Intune App SDK Xamarin-Bindungen können Sie die Intune-App-Schutzrichtlinien (auch als APP- oder MAM-Richtlinien bezeichnet) in Ihre mit Xamarin entwickelten Apps integrieren. MAM-fähige Anwendungen sind in das Intune App SDK integrierte Anwendungen. Sie ermöglichen IT-Administratoren, App-Schutzrichtlinien für Ihre mobile App bereitzustellen, wenn diese aktiv von Intune verwaltet wird.

## <a name="whats-supported"></a>Was wird unterstützt?

### <a name="developer-machines"></a>Entwicklercomputer
* Windows (Visual Studio-Version 15.7 und höher)
* macOS

### <a name="mobile-app-platforms"></a>Mobile App-Plattformen
* Android
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Intune MAM-Szenarien

* Intune-APP-WE (ohne Geräteregistrierung)
* Mit Intune MDM registrierte Geräte
* Mit EMM registrierte Geräte von Drittanbietern

Xamarin-Apps, die mit den Intune App SDK Xamarin-Bindungen erstellt wurden, können jetzt sowohl auf registrierten als auch auf nicht registrierten Geräten mit mobiler Intune-Geräteverwaltung (Mobile Device Management, MDM) Intune-App-Schutzrichtlinien empfangen.

## <a name="prerequisites"></a>Voraussetzungen

Lesen Sie die [Lizenzbedingungen](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf). Drucken Sie die Lizenzbedingungen aus, und heben Sie eine Kopie für Ihre Unterlagen auf. Indem Sie die Intune App SDK-Xamarin-Bindungen herunterladen und verwenden, stimmen Sie diesen Lizenzbestimmungen zu. Wenn Sie sie nicht akzeptieren, dürfen Sie die Software nicht verwenden.

Das SDK ist für seine Szenarien, die die [Authentifizierung](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) und den bedingten Start betreffen, auf [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) angewiesen. Dazu müssen Apps mit [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) konfiguriert sein. Die Konfigurationswerte werden dem SDK über AndroidManifest-Metadaten übermittelt. Informationen hierzu finden Sie unter [Konfigurieren der Active Directory-Authentifizierungsbibliothek für Ihre App](https://docs.microsoft.com/intune/app-sdk-android#configure-azure-active-directory-authentication-library-adal).

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Aktivieren der Intune-App-Schutzrichtlinien in Ihrer mobilen iOS-App
1. Fügen Sie das NuGet-Paket [Microsoft.Intune.MAM.Xamarin.iOS](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) zu Ihrem Xamarin.iOS-Projekt hinzu.
2.  Führen Sie die allgemeinen Schritte zur Integration des Intune App SDK in eine mobile iOS-App durch. Sie können mit Schritt 3 der Integrationsanweisungen aus dem [Entwicklerleitfaden zum Intune App SDK für iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app) beginnen. Sie können den letzten Schritt im Abschnitt über das Ausführen von IntuneMAMConfigurator überspringen, da dieses Tool im Microsoft.Intune.MAM.Xamarin.iOS-Paket enthalten ist und automatisch zur Erstellungszeit ausgeführt wird.
    **Wichtig**: Das Aktivieren der Schlüsselbundfreigabe für eine App unterscheidet sich in Visual Studio geringfügig von Xcode. Öffnen Sie die Datei „Entitlements.plist“ der App, und vergewissern Sie sich, dass die Option „Keychain aktivieren“ aktiviert ist und die entsprechenden Schlüsselbundfreigabegruppen in diesem Abschnitt hinzugefügt werden. Vergewissern Sie sich dann, dass im Feld „Benutzerdefinierte Berechtigungen“ der „iOS-Bündelsignierung “-Optionen des Projekts für alle entsprechenden Konfigurations-/Plattformkombinationen „Entitlements.plist“ angegeben ist.
3.  Sobald die Bindungen hinzugefügt sind und die App richtig konfiguriert ist, kann Ihre App mit der Verwendung der APIs des Intune SDK beginnen. Dazu müssen Sie den folgenden Namespace einbinden:

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. Um App-Schutzrichtlinien zu erhalten, muss sich Ihre App beim Intune MAM-Dienst registrieren. Wenn Ihre App keine [Azure Active Directory-Authentifizierungsbibliothek](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) oder [Microsoft-Authentifizierungsbibliothek](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) zum Authentifizieren von Benutzern verwendet und das Intune SDK die Authentifizierung durchführen soll, sollte Ihre App der LoginAndEnrollAccount-Methode von IntuneMAMEnrollmentManager den Benutzerprinzipalnamen mitteilen:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```
      Apps übergeben ggf. den Wert NULL, wenn der Benutzerprinzipalname zum Zeitpunkt des Aufrufs unbekannt ist. In diesem Fall werden Benutzer dazu aufgefordert, ihre E-Mail-Adresse und das Kennwort einzugeben.
      
      Wenn Ihre App bereits eine ADAL oder MSAL zum Authentifizieren von Benutzern verwendet, können Sie Single Sign-On zwischen Ihrer App und dem Intune SDK konfigurieren. Zunächst müssen Sie die ADAL bzw. MSAL so konfigurieren, dass alle Token in derselben Zugriffsgruppe für Keychain gespeichert werden, die von den Intune-Xamarin-Bindungen für iOS verwendet werden. Legen Sie bei ADALs [die Eigenschaft KeychainSecurityGroup von AuthenticationContext fest](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/Token-cache-serialization#enable-token-cache-sharing-across-ios-applications). Bei MSALs müssen Sie hingegen [die KeychainSecurityGroup-Eigenschaft von PublicClientApplication festlegen](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/msal-net-2-released#you-can-now-enable-sso-between-adal-and-msal-apps-on-xamarinios). Anschließend müssen Sie die Standardeinstellungen für Azure AD außer Kraft setzen, die vom Intune SDK mit dieser App verwendet werden. Sie können dies über das IntuneMAMSettings-Wörterbuch in der Datei „Info.plist“ der App tun, wie im [Entwicklerleitfaden zum Intune App SDK für iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk) erwähnt wird, oder die AAD-Überschreibungseigenschaften der IntuneMAMPolicyManager-Instanz verwenden. Der Ansatz mit „Info.plist“ wird für Anwendungen empfohlen, deren ADAL-Einstellungen statisch sind, wohingegen die Überschreibungseigenschaften für Anwendungen empfohlen werden, die diese Werte zur Runtime ermitteln. Sobald alle SSO-Einstellungen konfiguriert sind, sollte Ihre App der RegisterAndEnrollAccount-Methode von IntuneMAMEnrollmentManager den Benutzerprinzipalnamen bereitstellen, wenn dieser erfolgreich authentifiziert wurde:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      Apps können das Ergebnis eines Registrierungsversuchs bestimmen, indem sie die EnrollmentRequestWithStatus-Methode in einer Unterklasse von IntuneMAMEnrollmentDelegate implementieren und die Delegateigenschaft von IntuneMAMEnrollmentManager auf eine Instanz dieser Klasse festlegen. Ein Beispiel dazu finden Sie in unserer [Beispielanwendung für Xamarin.iOS](https://github.com/msintuneappsdk/sample-intune-xamarin-ios).

      Wenn die Registrierung erfolgreich ist, können Apps den Benutzerprinzipalnamen des registrierten Kontos bestimmen, wenn dieser zuvor unbekannt war, indem sie die folgende Eigenschaft abfragen: 
      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
> [!NOTE] 
> Es gibt keinen Remapper für iOS. Die Integration in eine Xamarin.Forms-App sollte identisch mit der Integration in ein herkömmliches Xamarin.iOS-Projekt sein. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Aktivieren der Intune-App-Schutzrichtlinien in Ihrer mobilen Android-App

Für Xamarin-basierte Android-Apps, die kein Benutzeroberflächenframework verwenden, lesen und befolgen Sie das [Entwicklerhandbuch zum Microsoft Intune App SDK für Android](app-sdk-android.md). Für Xamarin-basierte Android-Apps müssen die Klasse, Methoden und Aktivitäten basierend auf der im Handbuch enthaltenen [Tabelle](app-sdk-android.md#class-and-method-replacements) durch das MAM-Äquivalent ersetzt werden. Wenn Ihre App keine `android.app.Application`-Klasse definiert, müssen Sie eine erstellen. Es muss sichergestellt werden, dass Sie von `MAMApplication` erben.

### <a name="xamarinandroid-integration"></a>Xamarin.Android-Integration

1. Fügen Sie Ihrem Xamarin.Android-Projekt die neueste Version des NuGet-Pakets [Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) hinzu. Dadurch werden die für Ihre Anwendung erforderlichen Verweise auf Intune festgelegt.

2. Lesen Sie sich das [Entwicklerhandbuch zum Intune App SDK für Android](app-sdk-android.md) vollständig durch, und führen Sie die darin enthaltenen Schritte aus. Beachten Sie dabei insbesondere folgende Abschnitte:
    1. den gesamten Abschnitt zum [Ersetzen von Klassen und Methoden](app-sdk-android.md#class-and-method-replacements). 
    2. den Abschnitt [MAMApplication](app-sdk-android.md#mamapplication). Achten Sie darauf, dass die Unterklasse mit dem `[Application]`-Attribut versehen ist und den `(IntPtr, JniHandleOwnership)`-Konstruktor überschreibt.
    3. den Abschnitt zur [ADAL-Integration](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal), wenn Ihre App sich bei AAD authentifiziert.
    4. den Abschnitt zur [MAM-WE-Registrierung](app-sdk-android.md#app-protection-policy-without-device-enrollment), wenn Sie beabsichtigen, eine Richtlinie über den MAM-Dienst in Ihrer Anwendung zu beziehen.

> [!NOTE]
> Wenn Sie versuchen, entsprechende APIs im [Entwicklerhandbuch zum Intune App SDK für Android](app-sdk-android.md) in den `Microsoft.Intune.MAM.Xamarin.Android`-Bindungen zu suchen oder Codeausschnitte aus dem Handbuch zu konvertieren, sollten Sie beachten, dass der Generator für Xamarin-Bindungen die folgenden relevanten Änderungen an den Android-APIs durchführt:
> * Alle Bezeichner werden in die Pascal-Schreibweise konvertiert („com.foo.bar“ wird beispielsweise zu „Com.Foo.Bar“).
> * Alle get/set-Vorgänge werden in Eigenschaftenvorgänge konvertiert (z.B. „Foo.getBar()“ in „Foo.Bar“ oder „Foo.setBar("zap")“ in „Foo.Bar = "zap"“)
> * Dem Namen aller Schnittstellen wird das Zeichen „I“ vorangestellt (z.B. wird „FooInterface“ zu „IFooInterface“)

### <a name="xamarinforms-integration"></a>Xamarin.Forms-Integration

**Zusätzlich zum Ausführen aller oben beschriebenen Schritte** ist für `Xamarin.Forms`-Anwendungen das bereitgestellte `Microsoft.Intune.MAM.Remapper`-Paket erforderlich. Mit diesem werden Klassen automatisch ersetzt, indem `MAM`-Klassen in die Hierarchie häufig verwendeter `Xamarin.Forms`-Klassen wie `FormsAppCompatActivity` und `FormsApplicationActivity` eingefügt werden. Sie können die letztgenannten Klassen dadurch weiterhin verwenden, indem Sie entsprechende MAM-Funktionen wie `OnMAMCreate` und `OnMAMResume` überschreiben. Führen Sie Folgendes durch, um es zu verwenden:

1.  Fügen Sie das NuGet-Paket [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) zu Ihrem Projekt hinzu. Dadurch werden Intune APP SDK-Xamarin-Bindungen automatisch hinzugefügt, wenn Sie diese nicht bereits eingebunden haben.

2.  Ergänzen Sie die `OnMAMCreate`-Funktion der in Schritt 2.b erstellten `MAMApplication`-Klasse um einen Aufruf von `Xamarin.Forms.Forms.Init(Context, Bundle)`. Dies ist erforderlich, da Ihre Anwendung mit der Intune-Verwaltung im Hintergrund gestartet werden kann.

> [!NOTE]
> Bei diesem Vorgang wird eine Abhängigkeit geändert, die Visual Studio zur IntelliSense-Autovervollständigung verwendet. Nach der ersten Ausführung des Remappers müssen Sie Visual Studio daher möglicherweise neu starten, damit die Änderungen von IntelliSense erkannt werden. 


## <a name="support"></a>Unterstützung

Sie haben die grundlegenden Schritte zum Erstellen der Komponente auf Ihrer App abgeschlossen. Jetzt können die Schritte ausgeführt werden, die in der Xamarin Android-Beispiel-App zu finden sind. Wir haben zwei Beispiele bereit gestellt, eine für Xamarin.Forms und eine weitere für Android.

## <a name="requiring-intune-app-protection-policies-in-order-to-use-your-xamarin-based-android-lob-app-optional"></a>Intune-App-Schutzrichtlinien für die Verwendung einer auf Xamarin basierenden branchenspezifischen Android-App erforderlich (optional) 

Mithilfe der folgenden Anweisungen können Sie sicherstellen, dass auf Xamarin basierende branchenspezifische Android-Apps nur von durch Intune geschützte Benutzer auf deren Gerät verwendet werden können. 

### <a name="general-requirements"></a>Allgemeine Anforderungen
* Registrierung der Anwendungs-ID Ihrer App. Sie können diese ID im [Azure-Portal](https://portal.azure.com/) unter **Alle Anwendungen** in der Spalte **Anwendungs-ID** finden. Im Azure-Portal:
1.  Navigieren Sie zum Blatt **Azure Active Directory**.
2.  Wählen Sie die Einrichtung **App-Registrierung** für die Anwendung aus.
3.  Klicken Sie in den **Einstellungen** unter der Überschrift **API-Zugriff** auf **Erforderliche Berechtigung**. 
4.  Klicken Sie auf **+ Hinzufügen**.
5.  Klicken Sie auf **Hiermit wählen Sie eine API aus**. 
6.  Geben Sie in das Suchfeld **Microsoft Mobile Application Management** (Verwaltung mobiler Microsoft-Anwendungen) ein.
7.  Wählen Sie in der API-Liste **Microsoft Mobile Application Management** (Verwaltung mobiler Microsoft-Anwendungen) aus, und klicken Sie auf „Auswählen“.
8.  Klicken Sie auf **Read and Write the User’s App Management Data** (Lese- und Schreibberechtigungen für die App-Verwaltungsdaten des Benutzers).
9.  Klicken Sie auf **Fertig**.
10. Klicken Sie auf **Berechtigungen erteilen**, und klicken Sie anschließend auf **Ja**. 
    
### <a name="working-with-the-intune-sdk"></a>Arbeiten mit dem Intune SDK
Diese Anweisungen beziehen sich auf alle Android- und Xamarin-Apps, für die eine App-Schutzrichtlinie von Intune für die Verwendung auf einem Benutzergerät erforderlich sein soll.

1. Konfigurieren Sie ADAL, indem Sie die in der [Intune SDK für Android-Anleitung](https://docs.microsoft.com/intune/app-sdk-android#configure-azure-active-directory-authentication-library-adal) beschriebenen Schritte ausführen.
> [!NOTE] 
> Die Benennung „client id“ entspricht der Benennung „application id“ aus dem Azure Portal, das mit Ihrer App verbunden ist. 
* Zur Aktivierung von SSO benötigen Sie die im Abschnitt „Häufig verwendete ADAL-Konfigurationen“ #2 beschriebenen Informationen.

2. Aktivieren Sie die Standardregistrierung, indem Sie den folgenden Wert in das Manifest einfügen: ```xml <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />```.
> [!NOTE] 
> Dabei muss es sich um die einzige MAM-WE-Integration in der App handeln. Wenn es zu weiteren Versuchen kommt, MAMEnrollmentManager-APIs aufzurufen, können Konflikte entstehen.

3. Aktivieren Sie die erforderliche MAM-Richtlinie, indem Sie den folgenden Wert in das Manifest einfügen: ```xml <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />```.
> [!NOTE] 
> Dann sind Apps gezwungen, das Unternehmensportal auf dem Gerät herunterzuladen und den Vorgang der Standardregistrierung vor der Nutzung abzuschließen.

### <a name="working-with-adal"></a>Arbeiten mit ADAL
Diese Anweisungen sind für .NET/Xamarin-Apps erforderlich, für die eine App-Schutzrichtlinie von Intune für die Verwendung auf einem Benutzergerät erforderlich sein soll.

1. Befolgen Sie alle Schritte, die in der ADAL-Dokumentation unter [Brokered Authentication for Android (Im Broker gespeicherte Authentifizierung für Android)](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/tree/dev/adal#brokered-authentication-for-android) definiert sind.
> [!NOTE] 
> Die Version, die von .NET ADAL als Nächstes veröffentlicht wird (3.17.4), wird vermutlich die erforderliche Fehlerbehebung enthalten, damit dies funktioniert.

Wenn Ihre Organisation ein bestehender Kunde von Intune ist, arbeiten Sie mit Ihrem Microsoft-Supportmitarbeiter zusammen, um ein Supportticket zu öffnen und ein Problem auf der [GitHub-Seite für Probleme](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) zu erstellen. Sie erhalten so bald wie möglich Hilfe. 

