---
title: Auswählen der Vorbereitung von Apps für die mobile Anwendungsverwaltung mit Microsoft Intune
description: Die Informationen in diesem Thema unterstützen Sie bei der Entscheidung, wann Sie das App Wrapping Tool und das App SDK verwenden sollten, um Ihrer benutzerdefinierten Reihe von Branchen-Apps die Verwendung der Verwaltungsrichtlinien für mobile Apps zu ermöglichen.
keywords: ''
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 05/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 89a8f29e2e31cf59ed237cbfae5c557f60bd8dfa
ms.sourcegitcommit: 698bd1488be3a269bb88c077eb8d99df6e552a9a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="prepare-line-of-business-apps-for-app-protection-policies"></a>Vorbereiten von branchenspezifischen Apps für App-Schutzrichtlinien

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Sie können die Verwendung von App-Schutzrichtlinien bei Ihren Apps mit dem Intune App Wrapping Tool oder dem Intune App SDK aktivieren. Verwenden Sie diese Informationen, um diese beiden Methoden und den Zeitpunkt für ihre Verwendung kennenzulernen.

## <a name="intune-app-wrapping-tool"></a>Intune App Wrapping Tool
Das App Wrapping Tool wird in erster Linie für interne Line-of-Business-Apps (LOB) verwendet. Das Tool ist eine Befehlszeilenanwendung, die einen Wrapper für die App erstellt, der es der App anschließend ermöglicht, von einer Intune-App-Schutzrichtlinie verwaltet zu werden.

Der Quellcode ist für die Verwendung des Tools nicht erforderlich, aber Sie benötigen entsprechende Anmeldeinformationen. Weitere Informationen zu Anmeldeinformationen finden Sie im [Intune-Blog](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/). Die Dokumentation zum App Wrapping Tool finden Sie unter [Android App Wrapping Tool ](app-wrapper-prepare-android.md) und [iOS App Wrapping Tool](app-wrapper-prepare-ios.md).

Das App Wrapping Tool unterstützt **keine** Apps im Apple App Store oder Google Play Store. Es unterstützt auch keine bestimmten Features, die Entwicklerintegration erfordern (siehe die folgende Featurevergleichstabelle).

Weitere Informationen zum App Wrapping Tool für App-Schutzrichtlinien auf Geräten, die nicht bei Intune registriert sind, finden Sie unter [Schützen von branchenspezifischen Apps und Daten auf nicht in Microsoft Intune registrierten Geräten](/intune-classic/deploy-use/protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune).

### <a name="reasons-to-use-the-app-wrapping-tool"></a>Gründe für die Verwendung des App Wrapping Tools
* Ihre App verfügt nicht über integrierte Datenschutzfunktionen.
* Ihre App ist einfach aufgebaut.
* Ihre App wird intern bereitgestellt.
* Sie haben keinen Zugriff auf den Quellcode der App.
* Sie haben die App nicht entwickelt.
* Die Benutzerauthentifizierung ist bei Ihrer App auf ein Minimum beschränkt.

### <a name="supported-app-development-platforms"></a>Unterstützte App-Entwicklungsplattformen

|**App Wrapping Tool** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |Ja |Ja |
|**Android**| In der Vorschau |Ja |

## <a name="intune-app-sdk"></a>Intune App SDK
Das App SDK ist in erster Linie für Kunden konzipiert, die über Apps im Apple App Store oder Google Play Store verfügen und diese Apps mit Intune verwalten möchten. Das SDK kann jedoch in jede App integriert werden, auch in branchenspezifische Apps.

Weitere Informationen zum SDK finden Sie unter [Übersicht](app-sdk.md). Ein Einführung in das SDK finden Sie unter [Erste Schritte mit dem Microsoft Intune App SDK](app-sdk-get-started.md).

### <a name="reasons-to-use-the-sdk"></a>Gründe für die Verwendung des SDKs
* Ihre App verfügt nicht über integrierte Datenschutzfunktionen.
* Ihre App ist komplex und enthält viele Oberflächen.
* Ihre App wird in einem öffentlichen App Store wie Google Play oder Apple App Store bereitgestellt.
* Sie sind ein App-Entwickler mit dem entsprechenden technischen Hintergrund zur Verwendung des SDKs.
* Ihre App verfügt über andere SDK-Integrationen.
* Ihre App wird regelmäßig aktualisiert.

### <a name="supported-app-development-platforms"></a>Unterstützte App-Entwicklungsplattformen

|**Intune App SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|Ja – [Intune App SDK-Xamarin-Bindungen](app-sdk-xamarin.md) verwenden|Nein|
|**Android**| Ja – [Intune App SDK-Xamarin-Bindungen](app-sdk-xamarin.md) verwenden|Nein|

## <a name="feature-comparison"></a>Funktionsvergleich
In dieser Tabelle sind die Einstellungen aufgeführt, die Sie für das App SDK und App Wrapping Tool verwenden können.

> [!NOTE]
> Das App Wrapping Tool kann mit eigenständigen Intune-Bereitstellungen oder mit Intune mit Configuration Manager verwendet werden.

|Komponente|App SDK|App Wrapping Tool|
|-----------|---------------------|-----------|
|Einschränken von anzuzeigenden Webinhalten in einem unternehmensverwalteten Browser|X|X|
|Verhindern von Android-, iTunes- oder iCloud-Sicherungen|X|X|
|App Übertragung von Daten an andere Apps erlauben|X|X|
|App Empfang von Daten aus anderen Apps erlauben|X|X|
|Ausschneiden, Kopieren und Einfügen mit anderen Apps einschränken|X|X|
|Einfache PIN für Zugriff erforderlich|X|X|
|Ersetzen der integrierten App-PIN durch die Intune-PIN|X||
|Angeben der Anzahl von Versuchen vor dem Zurücksetzen der PIN|X|X|
|Fingerabdruck anstelle von PIN zulassen|X|X|
|Gesichtserkennung anstelle von PIN zulassen (nur iOS)|X|X|
|Unternehmensanmeldeinformationen für Zugriff erforderlich|X|X|
|Blockieren der Ausführung von verwalteten Apps auf per Jailbreak oder Rooting manipulierten Geräten|X|X|
|App-Daten verschlüsseln|X|X|
|Erneutes Überprüfen der Zugriffsanforderungen nach einer angegebenen Anzahl von Minuten|X|X|
|Angeben der Offlinetoleranzperiode|X|X|
|Blockieren von Bildschirmaufnahmen (nur Android)|X|X|
|Unterstützung von MAM ohne Geräteregistrierung|X|X|
|Vollständiges Zurücksetzen|X|X|
|Selektives Zurücksetzen <br></br>**Hinweis:** Für iOS wird die App auch entfernt, wenn das Verwaltungsprofil entfernt wird.|X||
|Verhindern von „Speichern unter“|X||
|Angestrebte Anwendungskonfiguration|X||
|Unterstützung von mehreren Identitäten|X||
|Anpassbarer Stil |X|||
|Bedarfsgesteuerte VPN-Verbindungen mit Anwendungen mit Citrix mVPN|X|X| 
|Kontaktsynchronisierung deaktivieren|X|X|
|Drucken deaktivieren|X|X|
|App-Mindestversion erfordern|X|X|
|Mindestbetriebssystem erfordern (iOS und Android)|X|X|
|Mindestversion für das Android-Sicherheitspatch erfordern (nur Android)|X|X|
|Mindestversion des Intune SDK für iOS erfordern (nur iOS)|X|X|

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu App-Schutzrichtlinien und Intune finden Sie in den folgenden Themen:

  - [Android App Wrapping Tool](app-wrapper-prepare-android.md)</br>
  - [Vorbereiten von iOS-Apps für die Verwaltung mobiler Anwendungen mit dem Intune App Wrapping Tool](app-wrapper-prepare-ios.md)</br>
  - [Verwenden des SDK zum Aktivieren von Apps für die Verwaltung von mobilen Anwendungen](/intune-classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management)
