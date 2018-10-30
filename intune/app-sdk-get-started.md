---
title: Erste Schritte mit dem Microsoft Intune App SDK
description: Richten Sie Ihre mobile App schnell für die Verwaltung mobiler Anwendungen (Mobile Application Management, MAM) mit Microsoft Intune ein.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune
ms.openlocfilehash: 5cb90b7f1dc72a67f48ba40db8a6ab4ffe598243
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2018
ms.locfileid: "49425035"
---
# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Erste Schritte mit dem Microsoft Intune App SDK

Dieser Leitfaden unterstützt Sie dabei, Ihre mobile App schnell für App-Schutzrichtlinien mit Microsoft Intune einzurichten. Unter Umständen ist es ratsam, sich zuerst in der [Übersicht über das Intune App SDK](app-sdk.md) mit den Vorteilen des Intune App SDK vertraut machen.

Das Intune App SDK unterstützt ähnliche Szenarien auf ios- und Android-Plattformen und bietet dem IT-Administrator eine plattformübergreifend konsistente Umgebung. Bei der Unterstützung bestimmter Funktionen gibt es jedoch geringfügige Unterschiede, die auf Einschränkungen der jeweiligen Plattform zurückzuführen sind.

## <a name="register-your-store-app-with-microsoft"></a>Registrieren Ihrer Store-App bei Microsoft

### <a name="if-your-app-is-internal-to-your-organization-and-will-not-be-publicly-available"></a>Wenn Ihre App für Ihre Organisation intern ist und nicht öffentlich verfügbar sein wird:

Dann muss die App *nicht* registriert werden. Branchenspezifische Apps werden vom IT-Administrator intern bereitgestellt. Intune erkennt, dass die App mit dem SDK erstellt wurde, und ermöglicht dem IT-Administrator das Anwenden von App-Schutzrichtlinien auf die App. Sie können zum Abschnitt [Aktivieren Ihrer iOS- oder Android-App für die App-Schutzrichtlinie](#enable-your-iOS-or-Android-app-for-app-protection-policy) wechseln.

### <a name="if-your-app-will-be-released-to-a-public-app-store-like-the-apple-app-store-or-google-play"></a>Wenn Ihre App in einem öffentlichen App Store (z.B. Apple App Store oder Google Play) freigegeben wird, gilt Folgendes:

Sie _**müssen**_ Ihre App zuerst bei Microsoft Intune registrieren und den Registrierungsbedingungen zustimmen. Danach können IT-Administratoren die App-Schutzrichtlinie auf die verwaltete App anwenden, die als Intune-Partner-App aufgelistet wird.

Solange die Registrierung nicht abgeschlossen ist und vom Microsoft Intune-Team bestätigt wurde, können Intune-Administratoren dem Deep-Link der App keine App-Schutzrichtlinie zuweisen. Microsoft fügt Ihre App auch zur Seite der [Microsoft Intune-Partner](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) hinzu. Dort wird das Symbol der App angezeigt, um anzugeben, dass sie die App-Schutzrichtlinien von Intune unterstützt.

Zu Beginn des Registrierungsvorgangs müssen Sie den [Fragebogen für Microsoft Intune-App-Partner](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u) ausfüllen.

Die auf dem ausgefüllten Fragebogen angegebenen E-Mail-Adressen werden verwendet, um sich mit Ihnen in Verbindung zu setzen und damit den Registrierungsprozess fortzusetzen. Über diese E-Mail-Adresse nehmen wir bei Fragen oder Problemen auch Kontakt mit Ihnen auf.

> [!NOTE]
> Alle Daten, die in diesem Fragebogen oder in der E-Mail-Korrespondenz mit dem Microsoft Intune-Team erfasst werden, unterliegen der [Microsoft-Datenschutzrichtlinie](https://www.microsoft.com/privacystatement/default.aspx).

**Informationen zum Registrierungsvorgang**:

1. Nachdem Sie den Fragebogen gesendet haben, setzen wir uns über die dort angegebene E-Mail-Adresse mit Ihnen in Verbindung, um den erfolgreichen Eingang zu bestätigen oder zusätzliche Informationen anzufordern, damit die Registrierung abgeschlossen werden kann.

2. Nachdem wir alle erforderlichen Informationen von Ihnen erhalten haben, senden wir Ihnen die Vereinbarung für Microsoft Intune-App-Partner zum Unterschreiben zu. Diese Vereinbarung enthält die Bedingungen, denen Ihr Unternehmen zustimmen muss, bevor es Microsoft Intune-App-Partner werden kann.

3. Sie werden ebenso benachrichtigt, wenn Ihre App erfolgreich beim Microsoft Intune-Dienst registriert wurde und auf der [Microsoft Intune-Partnerwebsite](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) empfohlen wird.

4. Schließlich wird der Deep-Link Ihrer App zum nächsten monatlichen Intune-Dienstupdate hinzugefügt. Wenn die Registrierung mit allen Informationen beispielsweise im Juli abgeschlossen ist, wird der Deep-Link ab Mitte August unterstützt.

Wenn sich der Deep-Link Ihrer App zu einem späteren Zeitpunkt ändert, müssen Sie Ihre App neu registrieren.

> [!NOTE]
> Außerdem müssen Sie uns informieren, wenn Sie Ihre App mit einer neuen Intune App SDK-Version aktualisieren.

## <a name="download-the-sdk-files"></a>Herunterladen der SDK-Dateien

Die Intune App SDKs für natives iOS und Android werden auf einem Microsoft-GitHub-Konto gehostet. Die folgenden öffentlichen Repositorys enthalten die SDK-Dateien für natives iOS und Android:

* [Intune App SDK für iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [Intune App SDK für Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

Wenn Ihre App eine Xamarin-App ist, verwenden Sie diese SDK-Variante:

* [Microsoft Intune App SDK Xamarin Bindings (Microsoft Intune-App SDK-Xamarin-Bindungen)](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)

Es wird empfohlen, sich für ein GitHub-Konto zu registrieren, mit dem Sie Fork- und Pullfunktionen für unsere Repositorys verwenden können. GitHub bietet Entwicklern die Möglichkeit, mit unserem Produktteam zu kommunizieren, Probleme zu melden und schnelle Antworten zu erhalten, Versionshinweise anzuzeigen und Feedback an Microsoft zu senden. Bei Fragen zu Intune App SDK GitHub wenden Sie sich an msintuneappsdk@microsoft.com.

## <a name="enable-your-ios-or-android-app-for-app-protection-policy"></a>Aktivieren Ihrer iOS- oder Android-App für die App-Schutzrichtlinie

Sie benötigen einen der folgenden Entwicklerleitfäden zum Integrieren des Intune App SDK in Ihre App:

* **[Entwicklerleitfaden zum Intune App SDK für iOS](app-sdk-ios.md)**: In diesem Dokument wird Schritt für Schritt erläutert, wie Sie Ihre native iOS-App für das Intune App SDK einrichten.

* **[Entwicklerleitfaden zum Intune App SDK für Android](app-sdk-android.md)**: In diesem Dokument wird Schritt für Schritt erläutert, wie Sie Ihre native Android-App für das Intune App SDK einrichten.

* **[Leitfaden für Intune App SDK-Xamarin-Komponenten:](app-sdk-xamarin.md)** Dieses Dokument hilft Ihnen beim Erstellen von iOS- und Android-Apps mithilfe von Xamarin für Intune-App-Schutzrichtlinien.



## <a name="enable-your-ios-or-android-app-for-app-based-conditional-access"></a>Aktivieren Ihrer iOS- oder Android-App für den App-basierten bedingten Zugriff
 
 Folgendes ist zusätzlich zum Aktivieren Ihrer App für die App-Schutzrichtlinie erforderlich, damit diese ordnungsgemäß mit dem auf der AAD-App (Azure ActiveDirectory) basierenden bedingten Zugriff funktioniert.
 
 * Die App wird mithilfe der [Azure Active Directory-Authentifizierungsbibliothek](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) erstellt und für die AAD-Brokerauthentifizierung aktiviert.
 
 * Die [AAD-Client-ID](https://docs.microsoft.com/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#optional-configure-a-native-client-application) für Ihre App muss für iOS- und Android-Plattformen eindeutig sein.
 
## <a name="configure-telemetry-for-your-app"></a>Konfigurieren der Telemetrie für Ihre App

Microsoft Intune sammelt Daten zu Nutzungsstatistiken für Ihre App.

* **Intune App SDK für iOS**: Das SDK protokolliert standardmäßig SDK-Telemetriedaten zu Verwendungsereignissen. Diese Daten werden an Microsoft Intune gesendet.

    * Wenn von Ihrer App keine SDK-Telemetriedaten an Microsoft Intune gesendet werden sollen, müssen Sie die Telemetrieübertragung deaktivieren, indem Sie im Wörterbuch „IntuneMAMSettings“ die Eigenschaft `MAMTelemetryDisabled` auf„JA“ festlegen.

* **Intune App SDK für Android:** Das Intune App SDK für Android kontrolliert nicht die Datensammlung über Ihre App. Standardmäßig protokolliert die Unternehmensportal-Anwendung Telemetriedaten. Diese Daten werden an Microsoft Intune gesendet. Gemäß der Microsoft-Richtlinie sammeln wir keine personenbezogenen Informationen (PII). 

    * Wenn Benutzer sich dazu entschließen, diese Daten nicht zu senden, müssen sie die Telemetrie unter „Einstellungen“ in der Unternehmensportal-App deaktivieren. Weitere Informationen finden Sie unter [Deaktivieren der Erfassung von Nutzungsdaten durch Microsoft](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android). 


 Die branchenspezifische App-Versionsnummer für iOS und Android ist sichtbar <!-- 1380712 -->.

## <a name="line-of-business-app-version-numbers"></a>Branchenspezifische App-Versionsnummern

Branchenspezifische Apps in Intune zeigen nun die Versionsnummer für iOS- und Android-Apps an. Die Nummer wird im Azure-Portal in der App-Liste und im Übersichtsblatt der App angezeigt. Benutzer können die App-Nummer in der Unternehmensportal-App und im Webportal anzeigen.

### <a name="full-version-number"></a>Vollständige Versionsnummer

Die vollständige Versionsnummer identifiziert ein bestimmtes Release der App. Die Nummer wird als _Version_(_Build_) angezeigt. Beispielsweise 2.2(2.2.17560800). 

Die vollständige Versionsnummer besteht aus zwei Komponenten:

 - **Version**  
   Die Versionsnummer ist die von einem Menschen lesbare Releasenummer der App. Diese wird von Benutzern verwendet, um verschiedene Releases der App zu identifizieren.

 - **Buildnummer**  
    Die Buildnummer ist eine interne Nummer, die in der App-Erkennung und zur programmgesteuerten Verwaltung der App verwendet werden kann. Die Buildnummer bezieht sich auf eine Iteration der App, die auf Änderungen im Code verweist.

### <a name="version-and-build-number-in-android-and-ios"></a>Versions- und Buildnummer unter Android und iOS

Android und iOS verwenden Versions- und Buildnummern, um auf Apps zu verweisen. Beide Betriebssysteme verwenden jedoch betriebssystemspezifische Begriffe. In der folgenden Tabelle wird erklärt, wie diese Begriffe zueinander in Bezug stehen.

Wenn Sie eine branchenspezifische Apps für die Verwendung in Intune entwickeln, denken Sie daran, die Versions- und die Buildnummer zu verwenden. Die Intune-Features für die App-Verwaltung sind abhängig von einer aussagekräftigen **CFBundleVersion** (für iOS) und einem aussagekräftigen **PackageVersionCode** (für Android). Diese Nummern sind im App-Manifest enthalten. 

Intune|iOS|Android|Beschreibung|
|---|---|---|---|
Versionsnummer|CFBundleShortVersionString|PackageVersionName |Diese Nummer gibt ein bestimmtes Release der App für Benutzer an.|
Buildnummer|CFBundleVersion|PackageVersionCode |Diese Nummer gibt eine Iteration im App-Code an.|

#### <a name="ios"></a>iOS

- **CFBundleShortVersionString**  
    Gibt die Nummer der Releaseversion des Pakets an. Diese Nummer gibt eine veröffentlichte Version der App an. Die Nummer wird von Benutzern verwendet, um auf die App zu verweisen.
  - **CFBundleVersion**  
    Die Buildversion des Pakets, die eine Iteration desselben angibt. Die Nummer kann verwendet werden, um ein Release oder ein nicht veröffentlichtes Paket zu identifizieren. Die Nummer wird für die App-Erkennung verwendet.

#### <a name="android"></a>Android

 - **PackageVersionName**  
    Die Versionsnummer, die Benutzern angezeigt wird. Dieses Attribut kann als Rohzeichenfolge oder als Verweis auf eine Zeichenfolgenressource festgelegt werden. Die Zeichenfolge dient lediglich dem Zweck, Benutzern angezeigt zu werden.
 - **PackageVersionCode**  
    Eine interne Versionsnummer. Diese Nummer wird lediglich verwendet, um zu bestimmen, ob eine Version aktueller als eine andere ist. Eine höhere Nummer gibt dabei eine aktuellere Version an. Dies ist nicht die Version. 

## <a name="next-steps-after-integration"></a>Nächste Schritte nach der Integration

### <a name="test-your-app"></a>Testen Ihrer App
Nachdem Sie die notwendigen Schritte zur Integration des Intune App SDK in Ihre iOS- oder Android-App abgeschlossen haben, müssen Sie sicherstellen, dass alle App-Schutzrichtlinien für den Benutzer und den IT-Administrator aktiviert und funktionsfähig sind. Zum Testen Ihrer integrierten App benötigen Sie Folgendes:

* **Microsoft Intune-Testkonto**: Um Ihre mit Intune verwaltete App und die Intune-App-Schutzfeatures zu testen, benötigen Sie ein Microsoft Intune-Konto.

    * ISVs, die ihre iOS- oder Android-Store-Apps für die Intune-App-Schutzrichtlinie aktivieren, erhalten nach Abschluss der Registrierung bei Microsoft Intune (wie im Registrierungsschritt beschrieben) einen Angebotscode. Mit diesem Angebotscode können Sie sich für eine Microsoft Intune-Testversion mit einem Jahr erweiterter Nutzung anmelden.

    * Wenn Sie eine branchenspezifische App entwickeln, die nicht in den Store übertragen wird, sollten Sie über Ihre Organisation auf Microsoft Intune zugreifen können. Sie können sich auch bei [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) für eine kostenlose einmonatige Testversion registrieren.

* **Intune-App-Schutzrichtlinien**: Um Ihre App für alle Intune-App-Schutzrichtlinien zu testen, müssen Sie das erwartete Verhalten bei jeder Richtlinieneinstellung kennen. Siehe die Beschreibungen der [iOS-App-Schutzrichtlinien](app-protection-policy-settings-ios.md) und [Android-App-Schutzrichtlinien](app-protection-policy-settings-android.md).

* **Problembehandlung**: Wenn Sie beim manuellen Testen der Benutzerumgebung Ihrer App-Installation auf Probleme stoßen, lesen Sie [Problembehandlung bei der App-Installation](troubleshoot-app-install.md). 

### <a name="badge-your-app-optional"></a>Anzeigen eines Badges auf Ihrem App-Symbol (optional)

Nachdem Sie bestätigt haben, dass Ihre Intune-App-Schutzrichtlinien in Ihrer App funktionieren, können Sie Ihr App-Symbol mit einem Badge in Form des Intune-App-Schutzlogos versehen.

Dieses Badge informiert IT-Administratoren, Endbenutzer und potenzielle Intune-Kunden, das Ihre App mit Intune-App-Schutzrichtlinien funktioniert. Es fördert die Verwendung und Akzeptanz Ihrer App bei Intune-Kunden.

Das Badge ist ein Aktentaschensymbol (siehe die folgenden Beispiele):

![Badge-Beispiel 1](./media/badge-example-1.png) ![Badge-Beispiel 2](./media/badge-example-2.png)

**Voraussetzungen für das Versehen Ihrer App mit einem Badge**:

* Eine Bildbearbeitungsanwendung, die **EPS**-Dateien lesen kann, oder eine Adobe-Anwendung, die **AI**-Dateien lesen kann.

* Auf der GitHub-Website von Microsoft Intune finden Sie die [Ressourcen und Anleitungen für Intune-App-Badges](https://github.com/msintuneappsdk/intune-app-partner-badge).
