---
title: Intune App SDK-Xamarin-Komponente
description: "Mit der Intune App SDK-Xamarin-Komponente können Sie die Intune-App-Schutzrichtlinie in Ihren mit Xamarin erstellten iOS- und Android-Apps aktivieren."
keywords: sdk, Xamarin, intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9fa0d471f91eeeebd0058417aa437e5469f48e09
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Intune App SDK-Xamarin-Komponente

> [!NOTE]
> Lesen Sie am besten zuerst den Leitfaden [Erste Schritte mit dem Microsoft Intune App SDK](app-sdk-get-started.md). Dort finden Sie Informationen zu den Vorbereitungen, die Sie auf den verschiedenen unterstützten Plattformen für die Integration treffen müssen.

## <a name="overview"></a>Übersicht
Mit der [Intune App SDK-Xamarin-Komponente](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) können Sie die [Intune-App-Schutzrichtlinie](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) in Ihren mit Xamarin erstellten iOS- und Android-Apps aktivieren. Die Komponente erlaubt Entwicklern, App-Schutzfunktionen von Intune auf einfache Weise in ihre Xamarin-basierten App zu integrieren.

> [!NOTE]
> Die Unterstützung für das Intune SDK für Xamarin ist derzeit in der Vorschauversion verfügbar. 

Mit der Microsoft Intune App SDK Xamarin-Komponente können Sie die Intune-App-Schutzrichtlinien (auch als APP- oder MAM-Richtlinien bezeichnet) in Ihre mit Xamarin entwickelten Apps integrieren. MAM-fähige Anwendungen sind in das Intune App SDK integrierte Anwendungen. Sie ermöglichen IT-Administratoren, App-Schutzrichtlinien für Ihre mobile App bereitzustellen, wenn diese aktiv von Intune verwaltet wird.

## <a name="whats-supported"></a>Was wird unterstützt?

### <a name="developer-machines"></a>Entwicklercomputer
* macOS


### <a name="mobile-app-platforms"></a>Mobile App-Plattformen
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Intune MAM-Szenarien

* Mit Intune MDM registrierte Geräte
* Mit EMM registrierte Geräte von Drittanbietern
* Nicht verwaltete (bei keiner MDM-Lösung registrierte) Geräte

Xamarin-Apps, die mit der Intune App SDK Xamarin-Komponente erstellt wurden, können jetzt sowohl auf registrierten als auch auf nicht registrierten Geräten mit mobiler Intune-Geräteverwaltung (Mobile Device Management, MDM) Intune-App-Schutzrichtlinien empfangen.

## <a name="prerequisites"></a>Voraussetzungen

* **[Nur Android]** Die aktuelle Microsoft Intune-Unternehmensportal-App muss auf dem Gerät installiert sein.

## <a name="get-started"></a>Erste Schritte

1.  Laden Sie [hier](https://components.xamarin.com/submit/xpkg) die **Xamarin-component.exe** herunter, und extrahieren Sie diese.

2. Lesen Sie die [Lizenzbedingungen](https://components.xamarin.com/license/microsoft.intune.mam) für die Microsoft Intune MAM-Xamarin-Komponente.

3.  Laden Sie den Ordner der Xamarin-Komponente des Intune App SDK von [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) oder [Nuget.org](https://www.nuget.org/profiles/msintuneappsdk) herunter, und extrahieren Sie diesen. Die beiden in Schritt 1 und Schritt 3 heruntergeladenen Dateien müssen sich auf derselben Verzeichnisebene befinden.

4.  Führen Sie `mono Xamarin.Component.exe install <.xam> file` in der Befehlszeile als Administrator aus.

5.  Klicken Sie in Visual Studio mit der rechten Maustaste in Ihrem zuvor erstellten Xamarin-Projekt auf **Komponenten**.

6.  Wählen Sie **Komponenten bearbeiten** aus, und fügen Sie die Intune App SDK-Komponente hinzu, die Sie lokal auf Ihren Computer heruntergeladen haben.



## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Aktivieren der Intune-App-Schutzrichtlinien in Ihrer mobilen iOS-App
1.  Führen Sie die allgemeinen Schritte zur Integration des Intune App SDK in eine mobile iOS-App durch. Sie können mit Schritt 3 der Integrationsanweisungen aus dem [Entwicklerleitfaden zum Intune App SDK für iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app) beginnen.
    **Wichtig**: Das Aktivieren der Schlüsselbundfreigabe für eine App unterscheidet sich in Visual Studio geringfügig von Xcode. Öffnen Sie die Datei „Entitlements.plist“ der App, und vergewissern Sie sich, dass die Option „Keychain aktivieren“ aktiviert ist und die entsprechenden Schlüsselbundfreigabegruppen in diesem Abschnitt hinzugefügt werden. Vergewissern Sie sich dann, dass im Feld „Benutzerdefinierte Berechtigungen“ der „iOS-Bündelsignierung “-Optionen des Projekts für alle entsprechenden Konfigurations-/Plattformkombinationen „Entitlements.plist“ angegeben ist.
2.  Sobald die Komponente hinzugefügt und die App richtig konfiguriert ist, kann Ihre App mit der Verwendung der APIs des Intune-SDK beginnen. Dazu müssen Sie den folgenden Namespace einbinden:

      ```csharp
      using Microsoft.Intune.MAM;
      ```
3.    Um App-Schutzrichtlinien zu erhalten, muss sich Ihre App beim Intune MAM-Dienst registrieren. Wenn Ihre App bereits die Azure Active Directory Authentication Library (ADAL) verwendet, um Benutzer zu authentifizieren, sollte Ihre App nach erfolgreicher Authentifizierung die UPN des Benutzers an die registerAndEnrollAccount-Methode von IntuneMAMEnrollmentManager weitergeben:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **Wichtig**: Achten Sie darauf, dass Sie die ADAL-Standardeinstellungen des Intune App SDK mit denen Ihre App überschreiben. Sie können dies über das IntuneMAMSettings-Wörterbuch in der Datei „Info.plist“ der App tun, wie im [Entwicklerleitfaden zum Intune App SDK für iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk) erwähnt wird, oder die AAD-Überschreibungseigenschaften der IntuneMAMPolicyManager-Instanz verwenden. Der Ansatz mit „Info.plist“ wird für Anwendungen empfohlen, deren ADAL-Einstellungen statisch sind, wohingegen die Überschreibungseigenschaften für Anwendungen empfohlen werden, die diese Werte zur Runtime ermitteln. 
      
      Wenn Ihre App nicht ADAL verwendet und Sie möchten, dass das Intune SDK die Authentifizierung übernimmt, sollte Ihre App die loginAndEnrollAccount-Methode der IntuneMAMEnrollmentManager-Instanz aufrufen:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>Aktivieren der App-Schutzrichtlinien in Ihrer mobilen Android-App
Für Xamarin-basierte Android-Apps, die kein Benutzeroberflächenframework verwenden, lesen und befolgen Sie das [Entwicklerhandbuch zum Microsoft Intune App SDK für Android](app-sdk-android.md). Für Xamarin-basierte Android-Apps müssen die Klasse, Methoden und Aktivitäten basierend auf der im Handbuch enthaltenen [Tabelle](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent) durch das MAM-Äquivalent ersetzt werden. Wenn Ihre App keine `android.app.Application`-Klasse definiert, müssen Sie eine erstellen. Es muss sichergestellt werden, dass Sie von `MAMApplication` erben.

Für Xamarin.Forms und andere UI-Frameworks haben wir ein Tool bereit gestellt. Es heißt `MAM.Remapper`. Das Tool nimmt den Klassentausch für Sie vor. Folgende Schritte müssen Sie jedoch selbst durchführen:

1.  Fügen Sie der Version 0.1.0.0 oder höher des `Microsoft.Intune.MAM.Remapper.Tasks`-NuGet-Pakets einen Verweis hinzu.

2.  Fügen Sie Ihrer CSPROJ-Datei von Android die folgende Zeile hinzu:
  ```xml
  <Import
  Project="$(NugetPack)\\Microsoft.Intune.MAM.Remapper.Tasks.0.1.X.X\\build\\MonoAndroid10\\Microsoft.Intune.MAM.Remapper.targets" />
  ```

3.  Legen Sie die Buildaktion der hinzugefügten `remapping-config.json`-Datei mit **RemappingConfigFile** fest. Die integrierte `remapping-config.json`-Datei funktioniert nur mit Xamarin.Forms. Greifen Sie für andere Benutzeroberflächenframeworks auf das Readme im Remapper-NuGet-Paket zurück.

## <a name="next-steps"></a>Nächste Schritte

Sie haben die grundlegenden Schritte zum Erstellen der Komponente auf Ihrer App abgeschlossen. Jetzt können die Schritte ausgeführt werden, die in der Xamarin Android-Beispiel-App zu finden sind. Wir haben zwei Beispiele bereit gestellt, eine für Xamarin.Forms und eine weitere für Android.
