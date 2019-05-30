---
title: Microsoft Intune App SDK-Xamarin-Bindungen
description: Mit den Intune App SDK-Xamarin-Bindungen können Sie die Intune-App-Schutzrichtlinie in Ihren mit Xamarin erstellten iOS- und Android-Apps aktivieren.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: d42fab929d6fa3e7fbaed8e9557573ebbaa1f3ad
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292349"
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

Das SDK ist für seine Szenarien, die die [Authentifizierung](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) und den bedingten Start betreffen, auf [Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) angewiesen. Dazu müssen Apps mit [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/) konfiguriert sein. 

Wenn für Ihre Anwendung bereits die Verwendung von ADAL oder MSAL konfiguriert ist und sie über eine eigene benutzerdefinierte Client-ID verfügt, die zur Authentifizierung bei Azure Active Directory verwendet wird, stellen Sie sicher, dass der Xamarin-Anwendung die erforderlichen Berechtigungen für den Intune MAM-Dienst (Mobile Application Management) gewährt werden. Verwenden Sie die Anweisungen unter [Erste Schritte mit dem Microsoft Intune App SDK](app-sdk-get-started.md) im Abschnitt [ Erteilen von Berechtigungen für den Zugriff auf den Intune-App-Schutzdienst durch Ihre App (optional)](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional).

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

1. Fügen Sie das NuGet-Paket [Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) zu Ihrem Xamarin.Android-Projekt hinzu.
    1. Für eine Xamarin.Forms-App fügen Sie das [NuGet-Paket Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) ebenfalls Ihrem Xamarin.Android-Projekt hinzu. 
2. Befolgen Sie die allgemeinen Schritte, die für die Integration des [Intune App SDK](app-sdk-android.md) in eine mobile Android-App erforderlich sind, und lesen Sie dieses Dokument, um weitere Details zu erfahren.

### <a name="xamarinandroid-integration"></a>Xamarin.Android-Integration

Eine vollständige Übersicht über die Integration des Intune App SDK finden Sie im [Leitfaden für Entwickler zum Microsoft Intune App SDK für Android](app-sdk-android.md). Während Sie den Leitfaden durchlesen und das Intune App SDK in Ihre Xamarin-App integrieren, sollen die folgenden Abschnitte die Unterschiede zwischen der Implementierung einer in Java entwickelten nativen Android-App und einer in C# entwickelten Xamarin-App aufzeigen. Diese Abschnitte dienen lediglich als Ergänzung und nicht als Ersatz für das Lesen des Leitfadens in seiner Gesamtheit.

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[Umbenannte Methoden](app-sdk-android.md#renamed-methods)
In vielen Fällen wurde eine in der Android-Klasse verfügbare Methode in der äquivalenten MAM-Klasse als abgeschlossen gekennzeichnet. In diesem Fall stellt die äquivalente MAM-Klasse eine Methode mit ähnlichem Namen (mit dem Suffix `MAM`) bereit, die stattdessen überschrieben werden sollte. Wenn z. B. von `MAMActivity` abgeleitet wird, anstatt `OnCreate()` zu überschreiben und `base.OnCreate()` aufzurufen, muss `Activity` `OnMAMCreate()` überschreiben und `base.OnMAMCreate()` aufrufen.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[MAM-Anwendung](app-sdk-android.md#mamapplication)
Ihre App muss eine `Android.App.Application`-Klasse definieren, die von `MAMApplication` erbt. Achten Sie darauf, dass die Unterklasse mit dem `[Application]`-Attribut versehen ist und den `(IntPtr, JniHandleOwnership)`-Konstruktor überschreibt.
```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```
> [!NOTE]
> Ein Problem mit den MAM-Xamarin-Bindungen kann dazu führen, dass die Anwendung im Debugmodus abstürzt. Als Abhilfemaßnahme muss das `Debuggable=false`-Attribut der `Application`-Klasse hinzugefügt werden, und das `android:debuggable="true"`-Flag muss aus dem Manifest entfernt werden, sofern es manuell festgelegt wurde.

#### <a name="enable-features-that-require-app-participationapp-sdk-androidmdenable-features-that-require-app-participation"></a>[Aktivieren von Funktionen, die App-Beteiligung erfordern](app-sdk-android.md#enable-features-that-require-app-participation)
Beispiel: Ermittlung, ob eine PIN für die App erforderlich ist
```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```
Beispiel: Ermitteln des primären Intune-Benutzers
```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```
Beispiel: Ermittlung, ob das Speichern auf dem Gerät oder im Cloudspeicher zulässig ist
```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdkapp-sdk-androidmdregister-for-notifications-from-the-sdk"></a>[Registrieren für Benachrichtigungen vom SDK](app-sdk-android.md#register-for-notifications-from-the-sdk)
Ihre App muss sich für Benachrichtigungen vom SDK registrieren, indem ein `MAMNotificationReceiver` erstellt und mit `MAMNotificationReceiverRegistry` registriert wird. Zu diesem Zweck werden der Empfänger und der Typ der gewünschten Benachrichtigung wie im folgenden Beispiel gezeigt in `App.OnMAMCreate` angegeben:
```csharp
public override void OnMAMCreate()
{
    // Register the notification receivers
    IMAMNotificationReceiverRegistry registry = MAMComponents.Get<IMAMNotificationReceiverRegistry>();
    foreach (MAMNotificationType notification in MAMNotificationType.Values())
    {
    registry.RegisterReceiver(new ToastNotificationReceiver(this), notification);
    }
    ...
```

#### <a name="mam-enrollment-managerapp-sdk-androidmdmamenrollmentmanager"></a>[MAM-Registrierungs-Manager](app-sdk-android.md#mamenrollmentmanager)
```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Xamarin.Forms-Integration

Für `Xamarin.Forms`-Anwendungen haben wir das `Microsoft.Intune.MAM.Remapper`-Paket bereitgestellt, um die automatische Ersetzung von MAM-Klassen durchzuführen, indem wir `MAM`-Klassen in die Klassenhierarchie häufig verwendeter `Xamarin.Forms`-Klassen einfügen. 

> [!NOTE]
> Die Xamarin.Forms-Integration muss zusätzlich zur oben beschriebenen Xamarin.Android-Integration erfolgen.

Sobald der Remapper zu Ihrem Projekt hinzugefügt wurde, müssen Sie die MAM entsprechenden Ersetzungen durchführen. Z. B. `FormsAppCompatActivity` und `FormsApplicationActivity` können weiterhin in Ihrer Anwendung zur Verfügung gestellt, überschreibungen, um zu verwendende `OnCreate` und `OnResume` werden durch die MAM-äquivalente ersetzt `OnMAMCreate` und `OnMAMResume` bzw.

```csharp
    public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsAppCompatActivity
    {
        protected override void OnMAMCreate(Bundle savedInstanceState)
        {
            base.OnMAMCreate(savedInstanceState);
            global::Xamarin.Forms.Forms.Init(this, savedInstanceState);
            LoadApplication(new App());
        }
```
Wenn die Ersetzungen nicht erfolgen, kann es zu folgenden Kompilierungsfehlern kommen, bis Sie die Ersetzungen vornehmen:
* [Compilerfehler CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239): Dieser Fehler wird häufig in dieser Form angezeigt``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
Dies entspricht dem erwarteten Verhalten, da bestimmte Funktionen in `sealed` geändert werden und stattdessen eine neue MAM-Variante zum Überschreiben hinzugefügt wird, wenn der Remapper die Vererbung von Xamarin-Klassen ändert.
* [Compilerfehler CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): Dieser Fehler wird häufig in dieser Form angezeigt: ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. Wenn der Remapper die Vererbung einiger der Xamarin-Klassen ändert, werden bestimmte Memberfunktionen in `public` geändert. Wenn Sie eine dieser Funktionen überschreiben, müssen Sie möglicherweise die Zugriffsmodifizierer für diese Überschreibungen so ändern, dass sie ebenfalls `public` sind.

> [!NOTE]
> Der Remapper schreibt eine Abhängigkeit neu, die Visual Studio für die Autovervollständigung von IntelliSense verwendet. Daher müssen Sie das Projekt möglicherweise neu laden und neu erstellen, wenn der Remapper hinzugefügt wird, damit IntelliSense die Änderungen ordnungsgemäß erkennt.

## <a name="support"></a>Unterstützung
Wenn Ihre Organisation ein bestehender Kunde von Intune ist, arbeiten Sie mit Ihrem Microsoft-Supportmitarbeiter zusammen, um ein Supportticket zu öffnen und ein Problem auf der [GitHub-Seite für Probleme](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) zu erstellen. Sie erhalten so bald wie möglich Hilfe. 
