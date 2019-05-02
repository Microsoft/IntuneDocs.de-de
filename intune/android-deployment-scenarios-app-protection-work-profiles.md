---
title: 'App-Schutzrichtlinien und Arbeitsprofile in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Erfahren Sie mehr über die Unterschiede und Vor- und Nachteile bei der Entscheidung, App-Schutzrichtlinien oder Arbeitsprofile für persönliche oder BYOD Android Enterprise-Geräte in Microsoft Intune zu verwenden. Vergleichen Sie die Unterschiede und Funktionen, die Sie mit App-Schutzrichtlinien ohne Registrierung (APP-WE) und Android Enterprise-Arbeitsprofilen erhalten.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/13/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cbd3b13215a58a831a15884bfe451f00a35ba379
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61490194"
---
# <a name="application-protection-policies-and-work-profiles-on-android-enterprise-devices-in-intune"></a>Anwendungsschutzrichtlinien und Arbeitsprofile für Android Enterprise-Geräte in Intune

In vielen Organisationen stehen Administratoren vor der Herausforderung, Ressourcen und Daten auf verschiedenen Geräten zu schützen. Eine Schwierigkeit ist der Schutz von Ressourcen für Benutzer mit persönlichen Android Enterprise-Geräten, auch bekannt als Bring-Your-Own-Device (BYOD). Microsoft Intune unterstützt zwei Android-Bereitstellungsszenarien für BYOD:

- App-Schutzrichtlinien ohne Registrierung (APP-WE)
- Android Enterprise-Arbeitsprofile

Die Bereitstellungsszenarien für APP-WE und das Android-Arbeitsprofil beinhalten die folgenden Hauptfunktionen, die für BYOD-Umgebungen wichtig sind:

1. **Schutz und Trennung von unternehmensverwalteten Daten**: Beide Lösungen schützen Unternehmensdaten, indem sie DLP-Kontrollen (Data Loss Prevention) für unternehmensverwaltete Daten durchsetzen. Diese Schutzmaßnahmen verhindern die unbeabsichtigte Offenlegung geschützter Daten, z.B. die versehentliche Weitergabe an eine persönliche Anwendung oder ein Konto durch einen Endbenutzer. Sie dienen auch der Sicherstellung, dass ein Gerät, das auf die Daten zugreift, integer und nicht gefährdet ist.

2. **Endbenutzerdatenschutz**: Die Arbeitsprofile von APP-WE und Android Enterprise trennen Endbenutzerinhalte auf dem Gerät und Daten, die vom Administrator für die mobile Geräteverwaltung (MDM-Administrator) verwaltet werden. In beiden Szenarien setzen IT-Administratoren Richtlinien durch, z.B. die ausschließliche PIN-Authentifizierung für unternehmensverwaltete Apps oder Identitäten. IT-Administratoren können keine Daten, die sich im Besitz oder unter der Kontrolle von Endbenutzern befinden, lesen, darauf zugreifen oder löschen.

Ob Sie sich für APP-WE oder Android Enterprise Arbeitsprofile für Ihre BYOD-Bereitstellung entscheiden, hängt von Ihren Anforderungen und Geschäftsbedürfnissen ab. Das Ziel dieses Artikels ist es, eine Anleitung bereitzustellen, die Ihnen bei der Entscheidung hilft.

## <a name="about-intune-app-protection-policies"></a>Informationen zu Intune-App-Schutzrichtlinien

Intune-App-Schutzrichtlinien (APP) sind Datenschutzrichtlinien, die für Benutzer gelten. Die Richtlinien wenden Schutz vor Datenverlust auf Anwendungsebene an. Intune APP erfordert, dass App-Entwickler APP-Funktionen für die von ihnen erstellten Apps aktivieren.

Einzelne Android-Apps werden auf verschiedene Weise für APP aktiviert:

1. **Nativ in Microsoft-Erstanbieter-Apps integriert**: In Microsoft Office-Apps für Android und eine Auswahl anderer Microsoft Apps ist Intune APP integriert. Diese Office-Apps (z.B. Word, OneDrive, Outlook usw.) benötigen keine weitere Anpassung, um Richtlinien anzuwenden. Diese Apps können von Endbenutzern direkt aus dem Google Play Store installiert werden.

2. **Integriert in App-Builds durch Entwickler mit dem Intune SDK**: App-Entwickler können das Intune SDK in ihren Quellcode integrieren und ihre Apps zur Unterstützung von Intune-APP-Richtlinienfunktionen erneut kompilieren.

3. **Umschlossen durch Verwenden des Intune App Wrapping Tools**: Einige Kunden kompilieren Android-Apps (APK-Dateien) ohne Zugriff auf den Quellcode. Ohne den Quellcode kann der Entwickler keine Integration mit dem Intune SDK erreichen. Ohne das SDK können Entwickler ihre App nicht für APP-Richtlinien aktivieren. Der Entwickler muss die App ändern oder neu codieren, um APP-Richtlinien zu unterstützen.

    Zur Unterstützung beinhaltet Intune das **App Wrapping Tool** für vorhandene Android-Anwendungen (APK-Dateien) und erstellt eine App, die APP-Richtlinien erkennt.

    Weitere Informationen zu diesem Tool finden Sie unter [Prepare line-of-business apps for app protection policies (Vorbereiten von branchenspezifischen Apps für App-Schutzrichtlinien)](apps-prepare-mobile-application-management.md).

Eine Liste der mit APP aktivierten Anwendungen finden Sie unter [Verwaltete Anwendungen mit einer umfangreichen Sammlung von Schutzrichtlinien für mobile Anwendungen](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

## <a name="deployment-scenarios"></a>Bereitstellungsszenarios

Dieser Abschnitt beschreibt die wichtigsten Merkmale von APP-WE- und Android Enterprise-Arbeitsprofil-Bereitstellungsszenarien.

#### <a name="app-we"></a>APP-WE

Eine APP-WE-Bereitstellung (App Schutzrichtlinien ohne Registrierung) definiert Richtlinien für Apps, nicht für Geräte. In diesem Szenario werden Geräte in der Regel nicht von einer MDM-Autorität (beispielsweise Intune) registriert oder verwaltet. Um Apps und den Zugriff auf Unternehmensdaten zu schützen, verwenden Administratoren APP-verwaltbare Apps und wenden Datenschutzrichtlinien auf diese Apps an.

Diese Funktion gilt für:

- Android 4.4 und höher

> [!TIP]
> Weitere Informationen finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

APP-WE-Szenarien sind für Endbenutzer gedacht, die einen kleinen unternehmensspezifischen Fußabdruck auf ihren Geräten wünschen und sich nicht in MDM registrieren möchten. Als Administrator müssen Sie Ihre Daten immer noch schützen. Diese Geräte sind nicht verwaltet. Daher sind gängige MDM-Aufgaben und -Funktionen wie WLAN, Geräte-VPN und Zertifikatverwaltung nicht Teil dieses Bereitstellungsszenarios.

#### <a name="android-enterprise-work-profiles"></a>Android Enterprise-Arbeitsprofile

Arbeitsprofile sind das Android Enterprise-Kernbereitstellungsszenario und das einzige Szenario, das für BYOD-Anwendungsfälle geeignet ist. Das Arbeitsprofil ist eine separate Partition, die auf der Ebene des Android-Betriebssystems erstellt wird und von Intune verwaltet werden kann.

Diese Funktion gilt für:

- Android 5.0-Geräte und höher mit Google Mobile Services

Ein Arbeitsprofil umfasst die folgenden Features:

- **Traditionelle MDM-Funktionen**: Wichtige MDM-Funktionen (z.B. App-Lebenszyklusverwaltung mit verwaltetem Google Play) sind in jedem Android Enterprise-Szenario verfügbar. Verwaltetes Google Play bietet eine stabile Benutzeroberfläche zum Installieren und Aktualisieren von Apps ohne Benutzereingriffe. Die IT-Abteilung kann auch App-Konfigurationseinstellungen in Organisations-Apps pushen. Es ist auch nicht erforderlich, dass Endbenutzer Installationen von unbekannten Quellen zulassen. Andere gängige MDM-Aktivitäten (z.B. das Bereitstellen von Zertifikaten, das Konfigurieren von WLAN/VPNs und das Festlegen von Gerätepasscodes) sind über Arbeitsprofile verfügbar.

- **DLP für die Arbeitsprofilgrenze**: Wie bei APP-WE kann die IT-Abteilung Datenschutzrichtlinien erzwingen. Mit einem Arbeitsprofil werden DLP-Richtlinien auf Arbeitsprofilebene erzwungen, nicht auf App-Ebene. So wird beispielsweise der Kopier-/Einfügeschutz durch die APP-Einstellungen erzwungen, die auf eine App angewendet werden, oder durch das Arbeitsprofil. Wenn die App in einem Arbeitsprofil bereitgestellt wird, können Administratoren den Kopier-/Einfügeschutz für das Arbeitsprofil vorübergehend aufheben, indem sie diese Richtlinie auf APP-Ebene deaktivieren.

## <a name="tips-to-optimize-the-work-profile-experience"></a>Tipps zur Optimierung des Arbeitsprofils

### <a name="when-to-use-app-within-work-profiles"></a>Verwenden von APP in Arbeitsprofilen

Intune APP und Arbeitsprofile sind sich ergänzende Technologien, die zusammen oder getrennt eingesetzt werden können. Unter architektonischen Gesichtspunkten erzwingen beide Lösungen Richtlinien auf verschiedenen Ebenen: APP auf der Ebene der einzelnen App und Arbeitsprofile auf der Profilebene. Die Bereitstellung von Apps, die mit einer APP-Richtlinie verwaltet werden, in einer App in einem Arbeitsprofil ist ein gültiges und unterstütztes Szenario. Die Verwendung von APP, Arbeitsprofilen oder einer Kombination hängt von Ihren DLP-Anforderungen ab.

Arbeitsprofile und APP ergänzen sich gegenseitig, indem sie zusätzlichen Schutz bieten, wenn ein Profil nicht den Datenschutzanforderungen Ihres Unternehmens entspricht. Beispielsweise bieten Arbeitsprofile keine nativen Steuerelemente, um eine App vom Speichern an einem nicht vertrauenswürdigen Cloudspeicherort abzuhalten. APP enthält diese Funktion. Sie können beschließen, dass ausschließlich durch das Arbeitsprofil bereitgestellte DLP-Funktionen ausreichend sind, und sich dafür entscheiden, APP nicht zu verwenden. Möglicherweise benötigen Sie aber auch den Schutz aus einer Kombination der beiden Technologien.

### <a name="suppress-app-policy-for-work-profiles"></a>Unterdrücken der APP-Richtlinie für Arbeitsprofile

Möglicherweise müssen Sie einzelne Benutzer mit mehreren Geräten unterstützen – nicht verwaltete Geräte in einem APP-WE-Szenario und verwaltete Geräte mit Arbeitsprofilen. 

Beispielsweise müssen Endbenutzer beim Öffnen einer Arbeits-App eine PIN eingeben. Je nach Gerät werden die PIN-Funktionen durch APP oder durch das Arbeitsprofil behandelt. Bei den APP-WE-Geräten wird das PIN-Eingabeverhalten zum Starten durch APP erzwungen. Für Arbeitsprofilgeräte können Sie eine vom Betriebssystem erzwungene Geräte- oder Arbeitsprofil-PIN verwenden. Um dieses Szenario zu erreichen, konfigurieren Sie die APP-Einstellungen so, dass sie nicht angewendet werden, *wenn* eine App in einem Arbeitsprofil bereitgestellt wird. Wenn die Konfiguration nicht auf diese Weise erfolgt, wird der Endbenutzer vom Gerät und erneut auf der APP-Ebene zur Eingabe einer PIN aufgefordert.

### <a name="control-multi-identity-behavior-in-work-profiles"></a>Steuern des Verhaltens mit mehreren Identitäten in Arbeitsprofilen

Office-Anwendungen wie Outlook und OneDrive weisen Verhalten mit „mehreren Identitäten“ auf. Innerhalb einer Instanz der Anwendung kann der Endbenutzer Verbindungen mit mehreren verschiedenen Konten oder Cloudspeicherorten hinzufügen. Innerhalb der Anwendung können die Daten, die von diesen Speicherorten abgerufen werden, getrennt oder zusammengeführt werden. Und der Benutzer kann einen Kontextwechsel zwischen persönlichen Identitäten (user@outlook.com) und Unternehmensidentitäten (user@contoso.com) vornehmen.

Wenn Sie Arbeitsprofile verwenden, möchten Sie dieses Verhalten mit mehreren Identitäten ggf. deaktivieren. Wenn Sie es deaktivieren, können Badgeinstanzen der App im Arbeitsprofil nur mit einer Organisationsidentität konfiguriert werden. Verwenden Sie die App-Konfigurationseinstellung „Zulässige Konten“ für die Unterstützung von Office Android-Apps.

Weitere Informationen finden Sie unter [Bereitstellen von Outlook für iOS und Android App-Konfigurationseinstellungen](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="when-to-use-intune-app"></a>Verwenden von Intune APP

Es gibt mehrere Szenarien für Enterprise Mobility, in denen die Verwendung von Intune APP die beste Empfehlung ist.

#### <a name="older-devices-running-android-44-51-are-being-used"></a>Ältere Geräte mit Android 4.4 bis 5.1 werden verwendet

Offiziell unterstützt jedes Android-Gerät der Version 5.0 oder höher mit Google Mobile Services Arbeitsprofile und kann auf diese Weise verwaltet werden. Einige Android 5.0- und 5.1-Geräte von einigen OEMs unterstützen allerdings keine Arbeitsprofile.

Wenn Sie Versionen verwenden, die keine Arbeitsprofile unterstützen, und DLP für Organisationsdaten auf Geräten sichergestellt werden soll, müssen Sie Intune APP-Funktionen verwenden.

#### <a name="no-mdm-no-enrollment-google-services-are-unavailable"></a>Kein MDM, keine Registrierung, Google-Dienste sind nicht verfügbar

Einige Kunden wünschen aus verschiedenen Gründen keine Form der Geräteverwaltung, einschließlich der Verwaltung von Arbeitsprofilen:

- Rechts- und Haftungsgründe
- Einheitliche Benutzererfahrung
- Die Android-Geräteumgebung ist ausgesprochen heterogen.
- Es besteht keine Verbindung mit Google-Diensten, die für die Verwaltung von Arbeitsprofilen erforderlich ist.

Beispielsweise können Kunden in China oder mit Benutzern in China die Android-Geräteverwaltung nicht verwenden, da die Google-Dienste blockiert sind. In diesem Fall verwenden Sie Intune APP für DLP.

## <a name="summary"></a>Zusammenfassung

Mit Intune stehen sowohl APP-WE als auch Android Enterprise-Arbeitsprofile für Ihr Android BYOD-Programm zur Verfügung. Die Entscheidung für APP-WE oder Arbeitsprofile hängt von Ihren Geschäfts- und Nutzungsanforderungen ab. Zusammenfassend lässt sich sagen, dass Sie Arbeitsprofile verwenden sollten, wenn Sie MDM-Aktivitäten auf verwalteten Geräten benötigen, z.B. Zertifikatbereitstellung, App-Push usw. Verwenden Sie APP-WE, wenn Sie Geräte nicht verwalten möchten oder können und nur Intune APP-fähige Apps verwenden.

## <a name="next-steps"></a>Nächste Schritte
[Starten der Verwendung von App-Schutzrichtlinien](app-protection-policy.md) oder [Registrieren Ihrer Geräte](android-enroll.md).
