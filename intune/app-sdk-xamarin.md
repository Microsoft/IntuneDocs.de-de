---
title: Microsoft Intune App SDK-Xamarin-Bindungen
description: Mit den Intune App SDK-Xamarin-Bindungen können Sie die Intune-App-Schutzrichtlinie in Ihren mit Xamarin erstellten iOS- und Android-Apps aktivieren.
keywords: sdk, Xamarin, intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 06/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f8f5e397c314088c7b26edba486f9cbaf9718096
ms.sourcegitcommit: 1eddded65ae9e442dd3bebd16b9428af76a67f34
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2018
ms.locfileid: "35250943"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Microsoft Intune App SDK-Xamarin-Bindungen

> [!NOTE]
> Lesen Sie am besten zuerst den Leitfaden [Erste Schritte mit dem Microsoft Intune App SDK](app-sdk-get-started.md). Dort finden Sie Informationen zu den Vorbereitungen, die Sie auf den verschiedenen unterstützten Plattformen für die Integration treffen müssen.

## <a name="overview"></a>Übersicht
Mit den [Intune App SDK-Xamarin-Bindungen](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) können Sie die [Intune-App-Schutzrichtlinie](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) in Ihren mit Xamarin erstellten iOS- und Android-Apps aktivieren. Die Bindungen ermöglichen es Entwicklern, App-Schutzfunktionen von Intune auf einfache Weise in ihre auf Xamarin basierenden Apps zu integrieren.

Mit den Microsoft Intune App SDK Xamarin-Bindungen können Sie die Intune-App-Schutzrichtlinien (auch als APP- oder MAM-Richtlinien bezeichnet) in Ihre mit Xamarin entwickelten Apps integrieren. MAM-fähige Anwendungen sind in das Intune App SDK integrierte Anwendungen. Sie ermöglichen IT-Administratoren, App-Schutzrichtlinien für Ihre mobile App bereitzustellen, wenn diese aktiv von Intune verwaltet wird.

## <a name="whats-supported"></a>Was wird unterstützt?

### <a name="developer-machines"></a>Entwicklercomputer
* Windows
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

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Aktivieren der Intune-App-Schutzrichtlinien in Ihrer mobilen iOS-App
1. Fügen Sie das NuGet-Paket [Microsoft.Intune.MAM.Xamarin.iOS](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) zu Ihrem Xamarin.iOS-Projekt hinzu.
2.  Führen Sie die allgemeinen Schritte zur Integration des Intune App SDK in eine mobile iOS-App durch. Sie können mit Schritt 3 der Integrationsanweisungen aus dem [Entwicklerleitfaden zum Intune App SDK für iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app) beginnen. Sie können den letzten Schritt im Abschnitt über das Ausführen von IntuneMAMConfigurator überspringen, da dieses Tool im Microsoft.Intune.MAM.Xamarin.iOS-Paket enthalten ist und automatisch zur Erstellungszeit ausgeführt wird.
    **Wichtig**: Das Aktivieren der Schlüsselbundfreigabe für eine App unterscheidet sich in Visual Studio geringfügig von Xcode. Öffnen Sie die Datei „Entitlements.plist“ der App, und vergewissern Sie sich, dass die Option „Keychain aktivieren“ aktiviert ist und die entsprechenden Schlüsselbundfreigabegruppen in diesem Abschnitt hinzugefügt werden. Vergewissern Sie sich dann, dass im Feld „Benutzerdefinierte Berechtigungen“ der „iOS-Bündelsignierung “-Optionen des Projekts für alle entsprechenden Konfigurations-/Plattformkombinationen „Entitlements.plist“ angegeben ist.
3.  Sobald die Bindungen hinzugefügt sind und die App richtig konfiguriert ist, kann Ihre App mit der Verwendung der APIs des Intune SDK beginnen. Dazu müssen Sie den folgenden Namespace einbinden:

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. Um App-Schutzrichtlinien zu erhalten, muss sich Ihre App beim Intune MAM-Dienst registrieren. Wenn Ihre App bereits die Azure Active Directory Authentication Library (ADAL) verwendet, um Benutzer zu authentifizieren, sollte Ihre App nach erfolgreicher Authentifizierung die UPN des Benutzers an die registerAndEnrollAccount-Methode von IntuneMAMEnrollmentManager weitergeben:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **Wichtig**: Achten Sie darauf, dass Sie die ADAL-Standardeinstellungen des Intune App SDK mit denen Ihre App überschreiben. Sie können dies über das IntuneMAMSettings-Wörterbuch in der Datei „Info.plist“ der App tun, wie im [Entwicklerleitfaden zum Intune App SDK für iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk) erwähnt wird, oder die AAD-Überschreibungseigenschaften der IntuneMAMPolicyManager-Instanz verwenden. Der Ansatz mit „Info.plist“ wird für Anwendungen empfohlen, deren ADAL-Einstellungen statisch sind, wohingegen die Überschreibungseigenschaften für Anwendungen empfohlen werden, die diese Werte zur Runtime ermitteln. 
      
      Wenn Ihre App nicht ADAL verwendet und Sie möchten, dass das Intune SDK die Authentifizierung übernimmt, sollte Ihre App die loginAndEnrollAccount-Methode der IntuneMAMEnrollmentManager-Instanz aufrufen:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```
      
> [!NOTE] 
> Es gibt keinen Remapper für iOS. Die Integration in eine Xamarin.Forms-App sollte identisch mit der Integration in ein herkömmliches Xamarin.iOS-Projekt sein. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Aktivieren der Intune-App-Schutzrichtlinien in Ihrer mobilen Android-App

### <a name="xamarinandroid-integration"></a>Xamarin.Android-Integration

1. Fügen Sie Ihrem Xamarin.Android-Projekt die neueste Version des NuGet-Pakets [Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) hinzu. Dadurch werden die für Ihre Anwendung erforderlichen Verweise auf Intune festgelegt.

2. Lesen Sie sich das [Entwicklerhandbuch zum Intune App SDK für Android](app-sdk-android.md) vollständig durch, und führen Sie die darin enthaltenen Schritte aus. Beachten Sie dabei insbesondere folgende Abschnitte:
    1. den gesamten Abschnitt zum [Ersetzen von Klassen und Methoden](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent). 
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

Wenn Ihre Organisation ein bestehender Kunde von Intune ist, arbeiten Sie mit Ihrem Microsoft-Supportmitarbeiter zusammen, um ein Supportticket zu öffnen und ein Problem auf der [GitHub-Seite für Probleme](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) zu erstellen. Sie erhalten so bald wie möglich Hilfe. 
