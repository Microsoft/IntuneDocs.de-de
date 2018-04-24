---
title: Microsoft Intune App SDK-Xamarin-Bindungen
description: Mit den Intune App SDK-Xamarin-Bindungen können Sie die Intune-App-Schutzrichtlinie in Ihren mit Xamarin erstellten iOS- und Android-Apps aktivieren.
keywords: sdk, Xamarin, intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9f9cc117925f59c9fb7c55d0ff10aedf09d26f93
ms.sourcegitcommit: b727b6bd6f138c5def7ac7bf1658068db30a0ec3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2018
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

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>Aktivieren der App-Schutzrichtlinien in Ihrer mobilen Android-App
Fügen Sie das NuGet-Paket [Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) zu Ihrem Xamarin.Android-Projekt hinzu.

Für Xamarin.Android-Apps müssen Sie das [Entwicklerhandbuch des Intune App SDK für Android](app-sdk-android.md) vollständig lesen und befolgen, einschließlich des Ersetzens von Klassen, Methoden und Aktivitäten mit Ihren MAM-Äquivalenten basierend auf der [Tabelle](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent) im Handbuch. 

> [!NOTE]
> Wenn Ihre App keine `android.app.Application`-Klasse definiert, müssen Sie eine erstellen. Es muss sichergestellt werden, dass Sie von `MAMApplication` erben.

> [!NOTE]
> Wenn Sie versuchen, entsprechende APIs im [Entwicklerhandbuch des Intune App SDK für Android](app-sdk-android.md) in den `Microsoft.Intune.MAM.Xamarin.Android`-Bindungen zu suchen oder Codeausschnitte aus dem Handbuch zu konvertieren, beachten Sie, dass der Generator für Xamarin-Bindungen die folgende relevante Änderungen an den Android-APIs durchführt:
> * Alle Bezeichner werden in die Groß-/Kleinschreibung von Pascale konvertiert (z.B. „com.microsoft.foo“ in „Com.Microsoft.Foo“).
> * Alle Get/Set-Vorgänge werden in Eigenschaftenvorgänge konvertiert (z.B. „Foo.getBar()“ in „Foo.Bar“ oder „Foo.setBar("zap")“ in „Foo.Bar = "zap"“)
> * Dem Namen aller Schnittstellen wird das Zeichen „I“ vorangestellt (z.B. wird „FooInterface“ zu „IFooInterface“)

Für Apps, die Xamarin.Forms und andere Frameworks für Benutzeroberflächen verwenden, wird ein Tool namens `Microsoft.Intune.MAM.Remapper` bereitgestellt. Das Tool nimmt den Klassentausch für Sie vor. Führen Sie Folgendes durch, um es zu verwenden:

1.  Fügen Sie das NuGet-Paket [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) zu Ihrem Projekt hinzu.

2.  Legen Sie die Buildaktion der `remapping-config.json`-Datei, die im NuGet-Paket enthalten ist, auf **RemappingConfigFile** fest. Die integrierte `remapping-config.json`-Datei funktioniert nur mit Xamarin.Forms. Greifen Sie für andere Benutzeroberflächenframeworks auf das Readme im Remapper-NuGet-Paket zurück.

3.  Fügen Sie der OnMAMCreate-Funktion Ihrer MAM-Anwendung einen Aufruf von „Xamarin.Forms.Forms.Init(Context, Bundle)“ hinzu, da Ihre Anwendung mithilfe der Intune-Verwaltung im Hintergrund gestartet werden kann.

4.  Führen Sie die restlichen Schritte im [Entwicklerhandbuch des Intune App SDK für Android](app-sdk-android.md) durch, die auf Ihre App anwendbar sind.

> [!NOTE]
> Die Buildaktion von „remapping-config.json“ kann in manchen Fällen zurückgesetzt werden, wenn Sie das Paket „Microsoft.Intune.MAM.Remapper.Tasks“ aktualisieren. Dadurch können Ihre Builds fehlschlagen.

## <a name="next-steps"></a>Nächste Schritte

Sie haben die grundlegenden Schritte für das Einrichten Ihrer App für die Intune-Verwaltung abgeschlossen. Sie können nun die Schritte durchführen, die in den Integrationshandbüchern für jede oben aufgeführte Plattform enthalten sind.

Wenn Ihre Organisation ein bestehender Kunde von Intune ist, arbeiten Sie mit Ihrem Microsoft-Supportmitarbeiter zusammen, um ein Supportticket zu öffnen und ein Problem auf der [GitHub-Seite für Probleme](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues) zu erstellen. Sie erhalten so bald wie möglich Hilfe. 