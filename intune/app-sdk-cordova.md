---
title: Microsoft Intune App SDK-Cordova-Plug-In
description: Das Intune App SDK-Cordova-Plug-In ermöglicht es Entwicklern, Features der Intune-App und Datenschutzfeatures in die Cordova-basierte App zu integrieren.
keywords: sdk, Cordova, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bb940cb9-d43f-45ca-b065-ac0adc61dc6f
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 84ff217361108ac3518567f31af8943d0b3032fe
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2018
---
# <a name="microsoft-intune-app-sdk-cordova-plugin"></a>Microsoft Intune App SDK-Cordova-Plug-In

> [!IMPORTANT]
> Intune beendet die Unterstützung des Microsoft Intune App SDK-Cordova-Plug-Ins am 1. Mai 2018. Sie sollten stattdessen das Intune App Wrapping Tool verwenden. Weitere Informationen zum App Wrapping Tool finden Sie unter [Vorbereiten von iOS-Apps für App-Schutzrichtlinien mit dem Intune App Wrapping Tool](app-wrapper-prepare-ios.md) und [Vorbereiten von Android-Apps für App-Schutzrichtlinien mit dem Intune App Wrapping Tool](app-wrapper-prepare-android.md). Weitere Informationen zu dieser Änderung finden Sie im Abschnitt [Hinweise](whats-new.md#notices) von [Neuerungen in Microsoft Intune](whats-new.md).

## <a name="overview"></a>Übersicht

Das [Intune App SDK-Cordova-Plug-In](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) in iOS- und Android-Apps, erstellt mit Cordova. Das Plug-In ermöglicht es Entwicklern, Funktionen der Intune-App und Datenschutzfunktionen in die Cordova-basierte App zu integrieren.

> [!NOTE]
> Lesen Sie am besten zuerst den Leitfaden [Erste Schritte mit dem Microsoft Intune App SDK](app-sdk-get-started.md). Dort finden Sie Informationen zu den Vorbereitungen, die Sie auf den verschiedenen unterstützten Plattformen für die Integration treffen müssen.

Sie werden feststellen, dass Sie die meisten SDK-Funktionen aktivieren können, ohne das Verhalten Ihrer App zu ändern. Nachdem Sie das Plug-In in Ihrer iOS- oder Android-App erstellt haben, kann der Microsoft Intune-Administrator die Intune-App-Schutzrichtlinie bereitstellen, die aus einer Vielzahl von Datenschutzfeatures besteht. Das Plug-In ist so programmiert, dass die meisten Schritte automatisch beim Cordova-Buildprozess ausgeführt werden. Dadurch sollten Sie Ihre App schnell für die Intune-App-Schutzrichtlinie aktivieren können. Um zu beginnen, befolgen Sie die nachstehenden Anweisungen basierend auf Ihrer Zielplattform.

## <a name="supported-platforms"></a>Unterstützte Plattformen

* Das Plug-In funktioniert unter Windows, Mac und Linux.
* Das Plug-In funktioniert für Android-Apps mit `minSdkVersion` >= 14 und `targetSdkVersion` <= 24.
* Das Plug-In funktioniert für iOS-Apps, die für iOS 9.0 und höher vorgesehen sind.

## <a name="intune-mobile-application-management-scenarios"></a>Intune MAM-Szenarien

* Mit Intune MDM registrierte Geräte
* Mit EMM registrierte Geräte von Drittanbietern
* Nicht verwaltete (bei keiner MDM-Lösung registrierte) Geräte

Cordova-Apps, die mit dem Intune App SDK Cordova Plug-In erstellt wurden, können jetzt sowohl auf registrierten als auch auf nicht registrierten Geräten mit mobiler Intune-Geräteverwaltung (Mobile Device Management, MDM) Intune-App-Schutzrichtlinien empfangen.

## <a name="prerequisites"></a>Voraussetzungen

### <a name="android"></a>Android

* Es muss immer die aktuelle Microsoft Intune-Unternehmensportal-App auf dem Gerät installiert sein.
* Wenn Sie bei Verwendung des Plug-Ins den Cordova-Build ausführen, ist mindestens Java 7 erforderlich.

### <a name="ios"></a>iOS

* Für MDM-Features muss die aktuelle Microsoft Intune-Unternehmensportal-App auf dem Gerät installiert sein. Sie ist *nicht* für die Intune-App-Schutzrichtlinie ohne Geräteregistrierungsfeatures erforderlich.

### <a name="both-platforms"></a>Beide Plattformen

* Es wird Version 0.8.0+ des [Azure Active Directory Authentifizierungsbibliothek Plug-Ins (ADAL) für Cordova](https://github.com/AzureAD/azure-activedirectory-library-for-cordova) benötigt.

> [!NOTE]
> Aufgrund eines Apache Cordova-Fehlers führen die [hier](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22) aufgelisteten Apps, die schon über die Plug-In-Abhängigkeit verfügen, das Upgrade auf die benötigte Version nicht automatisch aus.



## <a name="quickstart"></a>Schnellstart

1. Updaten Sie Ihre ADAL-Version:

  ```shell
  cordova plugin remove cordova-plugin-ms-adal
  cordova plugin add cordova-plugin-ms-adal@0.8.x
  ```

2. Fügen Sie das Intune App SDK für Cordova-Plug-In hinzu:

  ```shell
  cordova plugin add cordova-plugin-ms-intune-mam
  ```

## <a name="build-the-plugin-into-your-ios-app"></a>Erstellen des Plug-Ins in Ihrer iOS-App

Sie müssen einige Schritte abschließen, um Ihre App für die Intune-App-Schutzrichtlinie zu aktivieren. Der Einfachheit halber werden diese Schritte im Cordova-Buildprozess als Prebuild-Hook automatisch ausgeführt. Dadurch werden die automatisierten Schritte Ihre `*.pbxproj`- , `*-Info.plist`-, und `*.entitlements`-Dateien ändern, die einer Projektkonfiguration zugeordnet sind. Wenn das Projekt keine Berechtigungsdatei enthält, wird das Plug-In automatisch eine erstellen.

Dieses Setup unterstützt nur ein einziges Ziel. Wenn es mehrere Ziele gibt, führt es die Konfiguration auf dem Ziel aus, das als erstes gefunden wird. Wenn der Prozess fehlschlägt, überprüfen Sie, dass:

1. Das Xcode-Projekt Ihrer App `[name].xcodeproj` ist, wobei `[name]` der Wert wie definiert in `config.xml` ist.
2. Ihr Projekt verwendet die [Standardverzeichnisstruktur der Cordova-App](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure).

## <a name="build-the-plugin-into-your-android-app"></a>Erstellen des Plug-Ins in Ihrer Android-App

1. Importieren Sie dieses Plug-In mit den aktuellsten Cordova-Tools. Das Plug-In wird automatisch als ein `after_compile`-Schritt aufgerufen.

2. Das Plug-In erstellt am Ende des Erstellungsprozesses eine Intune-fähige Version einer erstellten APK-Datei (Android-API 14 und höher). Die Buildausgabe enthält `[Project]-intunewrapped-[Build_Configuration].apk` (z.B. `helloWorld-intunewrapped-debug.apk`).

> [!NOTE]
> Das Plug-In unterstützt nur Gradle-Builds.

Aufgrund eines Cordova-Fehlers, der [hier](https://issues.apache.org/jira/browse/CB-9434) aufgeführt ist, und verursacht, dass bestimmte Cordova-Hooks in `cordova run` ignoriert werden, müssen Sie Folgendes tun, um die umschlossene App aus der Befehlszeile auszuführen:

```shell
$ cordova build
$ cordova run --nobuild
```

## <a name="sign-your-android-app"></a>Signieren Ihrer Android-App

Das Plug-In erkennt automatisch Signierungsinformationen, die Sie an folgenden Speicherorten für Cordova angegeben haben:

* platforms/android/debug-signing.properties
* platforms/android/release-signing.properties
* res/native/android/ant.properties

Lesen Sie die [Cordova-Gradle-Signierungsinformationen](https://cordova.apache.org/docs/en/latest/guide/platforms/android/#using-gradle), um mehr über das erwartete Format zu erfahren.

Intune unterstützt derzeit nicht die Möglichkeit, Signierungsinformationen in `build.json` oder an beliebigen Speicherorten bereitzustellen, die dem Cordova-Build über Parameter bereitgestellt werden.

## <a name="debugging-from-visual-studio"></a>Debugging aus Visual Studio

Nachdem die App zum ersten Mal gestartet wurde, sollten Sie ein Dialogfeld sehen, das Sie darüber informiert, dass die App von Intune verwaltet wird. Klicken Sie auf „Nicht mehr anzeigen“. Klicken Sie dann in VS noch einmal auf die Schaltfläche Debuggen/Ausführen, damit Haltepunkte erreicht werden.

## <a name="known-limitations"></a>Bekannte Einschränkungen

### <a name="android"></a>Android

* Die MultiDex Unterstützung ist unvollständig.
* Die App muss `minSdkVersion` von 14 und `targetSdkVersion` von 24 oder niedriger haben. Intune unterstützt derzeit keine Apps für API 25.
* Intune kann keine Apps erneut signieren, die mit dem V2-Signaturschema signiert wurden. Wenn V2-signierte Apps von dem Plug-In umschlossen werden, ist die umschlossene Ausgabe-APK unsigniert.
*
  * Sie können die Cordova-Standard-V2-Signierung deaktivieren, indem Sie Ihrer `build-extras.gradle`-Datei Folgendes hinzufügen:

  ```gradle
  android {
      signingConfigs {
          release {
              v2SigningEnabled false
          }
          debug {
              v2SigningEnabled false
          }
      }
      buildTypes {
          release {
              signingConfig signingConfigs.release
          }
          debug {
              signingConfig signingConfigs.debug
          }
      }
  }
  ```

### <a name="ios"></a>iOS

* Wenn Sie die Liste der UTIs unter dem Knoten **CFBundleDocumentTypes** der **Info.plist**-Datei verändern, müssen Sie die Intune-UTIs im Bereich „Importierte-UTIs“ der gleichen PLIST-Datei löschen (Knoten **UTImportedTypeDeclarations**), bevor Sie mit der erneuten Erstellung fortfahren. Alle Intune-UTIs beginnen mit dem Präfix `com.microsoft.intune.mam`.

* Wenn Sie das Intune App SDK für Cordova-Plug-In aus Ihrem Cordova-Projekt entfernen möchten, müssen Sie auch die iOS-Plattform entfernen und sie erneut hinzufügen, um einige der Intune-Konfigurationen in den XCODEPROJ- und PLIST-Dateien rückgängig zu machen.
