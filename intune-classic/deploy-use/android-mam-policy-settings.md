---
title: Android-MAM-Richtlinieneinstellungen
description: In diesem Thema werden die Richtlinieneinstellungen für die Verwaltung mobiler Apps für Android-Geräte beschrieben.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 04/18/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: dc65dd5ef170bff4cb1d1c126fa1549b7a357276
ms.sourcegitcommit: 54fc806036f84a8667cf8f74086358bccd30aa7d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2018
---
# <a name="android-app-protection-policy-settings-in-microsoft-intune"></a>Einstellungen für App-Schutzrichtlinien in Microsoft Intune

> [!IMPORTANT]
Der Inhalt auf dieser Seite ist zum größten Teil veraltet, da die App-Schutzrichtlinien von Intune vollständig zum Azure-Portal migriert wurden. Weitere Informationen finden Sie unter [Intune app protection policies for Android in the Azure portal (Intune-App-Schutzrichtlinien für Android im Azure-Portal)](https://docs.microsoft.com/intune/app-protection-policy-settings-android).

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Die in diesem Thema beschriebenen App-Richtlinieneinstellungen können im Azure-Portal auf dem Blatt **Einstellungen** [konfiguriert](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) werden.
Es gibt zwei Kategorien von Richtlinieneinstellungen: Datenverlagerungs- und Zugriffseinstellungen. In diesem Thema bezieht sich der Begriff _**richtlinienverwaltete Apps**_ auf Apps, die mit App-Schutzrichtlinien konfiguriert sind.

##  <a name="data-relocation-settings"></a>Einstellungen für die Datenverlagerung

| Einstellung | Verwendung | Standardwert(e) |
|------|------|------|
| **Android-Sicherungen verhindern** | Wählen Sie **Ja**, um zu verhindern, dass diese App Geschäfts-, Schul- oder Unidaten im [Android-Sicherungsdienst](https://developer.android.com/google/backup/index.html) sichert. Wählen Sie **Nein**, um der App zu erlauben, Geschäfts-, Schul- oder Unidaten zu sichern.| Ja  |
| **App Übertragung von Daten an andere Apps erlauben** | Geben Sie an, welche Apps Daten von dieser App empfangen können: <ul><li> **Richtlinienverwaltete Apps**: Datenübertragung nur an andere richtlinienverwaltete Apps zulassen</li> <li>**Alle Apps**: Datenübertragung an beliebige Apps zulassen </li> <li>**Keine**: Keine Datenübertragung an beliebige Apps zulassen, auch nicht an andere richtlinienverwaltete Apps.</li></ul> <p>Es gibt einige ausgenommene Apps und Dienste für die Intune möglicherweise die Datenübertragung zulässt. Unter [Data transfer exemptions (Ausnahmen bei der Datenübertragung)](#Data-transfer-exemptions) finden Sie eine vollständige Liste der Apps und Dienste.| Alle Apps |
| **App Empfang von Daten aus anderen Apps erlauben** | Geben Sie an, welche Apps Daten an diese App übertragen können: <ul><li>**Richtlinienverwaltete Apps**: Datenübertragung nur von anderen richtlinienverwalteten Apps zulassen</li><li>**Alle Apps**: Datenübertragung von beliebigen Apps zulassen</li><li>**Keine**: Keine Datenübertragung von beliebigen Apps zulassen, auch nicht von anderen richtlinienverwalteten Apps </li></ul> <p>Es gibt einige ausgenommene Apps und Dienste von denen Intune möglicherweise die Datenübertragung zulässt. Unter [Data transfer exemptions (Ausnahmen bei der Datenübertragung)](#Data-transfer-exemptions) finden Sie eine vollständige Liste der Apps und Dienste. | Alle Apps |
| **„Speichern unter“ verhindern** | Wählen Sie **Ja** aus, um die Verwendung der Option „Speichern unter“ in dieser App zu deaktivieren. Wählen Sie **Nein** aus, wenn die Verwendung von „Speichern unter“ zulässig sein soll. <p><br>**Speicherdienste zum Speichern von Unternehmensdaten auswählen** <br>Benutzer können Speichervorgänge in den ausgewählten Diensten (OneDrive for Business, SharePoint und lokaler Speicher) durchführen. Alle anderen Dienste werden blockiert.</p> | Nein <br><br> 0 ausgewählt |
| **Beschränken von Ausschneiden, Kopieren und Einfügen mit anderen Apps** | Geben Sie an, wann Ausschneide-, Kopier- und Einfügeaktionen in dieser App erlaubt sind. Es stehen die folgenden Optionen zur Auswahl: <ul><li>**Blockiert**: Ausschneide-, Kopier- und Einfügeaktionen zwischen dieser App und anderen Apps nicht zulassen.</li><li>**Richtlinienverwaltete Apps**: Nur Ausschneide-, Kopier- und Einfügeaktionen zwischen dieser App und anderen richtlinienverwalteten Apps zulassen.</li><li>**Richtlinienverwaltete Apps mit Einfügen**: Ausschneiden oder Kopieren zwischen dieser App und anderen richtlinienverwalteten Apps zulassen. Einfügen von Daten aus beliebigen Apps in diese App zulassen.</li><li>**Jede App**: Keine Einschränkungen für das Ausschneiden, Kopieren und Einfügen in und aus dieser App. | Jede App |
|**Anzeige von Webinhalten auf den Managed Browser beschränken** | Wählen Sie **Ja**, um zu erzwingen, dass Weblinks in der App in der Managed Browser-App geöffnet werden. <br><br> Auf Geräten, die nicht bei Intune registriert sind, können Weblinks in richtlinienverwalteten Apps nur in der Managed Browser-App geöffnet werden. <br><br> Wenn Sie Intune zum Verwalten Ihrer Geräte verwenden, lesen Sie [Verwalten des Internetzugriffs mittels Richtlinien für Managed Browser mit Microsoft Intune](manage-internet-access-using-managed-browser-policies.md). | Nein |
| **App-Daten verschlüsseln** | Wählen Sie **Ja**, um die Verschlüsselung von Geschäfts-, Schul- oder Unidaten in dieser App zu aktivieren. Intune verwendet ein OpenSSL-128-Bit-AES-Verschlüsselungsschema sowie das Android Keystore-System, um App-Daten sicher zu verschlüsseln. Daten werden während der Datei-E/A-Tasks synchron verschlüsselt. Inhalt im Gerätespeicher wird immer verschlüsselt. <br><br> Die Verschlüsselungsmethode ist **nicht** FIPS 140-2-zertifiziert.  | Ja  |
| **Kontaktsynchronisierung deaktivieren** | Wählen Sie **Ja**, um zu verhindern, dass die App Daten in der nativen App „Kontakte“ auf dem Gerät speichert. Wenn Sie **Nein** wählen, darf die App Daten in der nativen App „Kontakte“ auf dem Gerät speichern. <br><br>Bei Ausführung eines selektiven Zurücksetzens zum Entfernen von Geschäfts-, Schul- oder Unidaten aus der App werden Kontakte entfernt, die direkt aus der App in die native App „Kontakte“ synchronisiert wurden. Kontakte, die aus dem nativen Adressbuch mit einer anderen externen Quelle synchronisiert werden, können nicht zurückgesetzt werden. Dies gilt derzeit nur für die Microsoft Outlook-App. | Nein |
| **Drucken deaktivieren** | Wählen Sie **Ja**, um zu verhindern, dass die App Geschäfts-, Schul- oder Unidaten druckt. | Nein |

  >[!NOTE]
  >Die Verschlüsselungsmethode für die Einstellung **App-Daten verschlüsseln** ist **nicht** FIPS 140-2-zertifiziert.


  ## <a name="data-transfer-exemptions"></a>Datenübertragungsausnahmen

  Die App-Schutzrichtlinie von Intune erlaubt die Datenübertragung zu und von einigen ausgenommenen Apps und Plattformdiensten. Beispielsweise müssen alle über Intune verwaltete Apps unter Android in der Lage sein, Daten zu und vom Google-Programm für die Sprachwiedergabe von Text zu übertragen, sodass Text vom Bildschirm Ihres mobilen Geräts laut vorgelesen werden kann. Diese Liste unterliegt Änderungen und gibt die Dienste und Apps wieder, die als nützlich für die sichere Produktivität gelten.

  ### <a name="full-exemptions"></a>Vollständige Ausnahmen

  Diese Apps und Dienste sind für die Datenübertragung zu und von verwalteten Apps durch Intune vollständig zugelassen.

  |Name der App / des Diensts | Beschreibung |
  | ------ | ---- |
  | com.android.phone | Native Phone-App
  | com.android.vending | Google Play Store |
  | com.android.documentsui | Android-Dokumentauswahl|
  | com.google.android.webview | [WebView](https://developer.android.com/reference/android/webkit/WebView.html): erforderlich für viele Apps, einschließlich Outlook |
  | com.android.webview |[WebView](https://developer.android.com/reference/android/webkit/WebView.html): erforderlich für viele Apps, einschließlich Outlook|
  | com.google.android.tts | Google-Text-zu-Sprache |
  | com.android.providers.settings | Android-Systemeinstellungen |
  | com.azure.authenticator | Azure-Authentifikator-App, die in vielen Szenarios für die erfolgreiche Authentifizierung erforderlich ist |
  | com.microsoft.windowsintune.companyportal | Intune Unternehmensportal|

  ### <a name="conditional-exemptions"></a>Bedingte Ausnahmen
  Diese Apps und Dienste sind für die Datenübertragung zu und von verwalteten Apps durch Intune unter bestimmten Bedingungen zugelassen.

  |Name der App / des Diensts | Beschreibung | Ausnahmebedingung|
  | ------ | ---- | --- |
  | com.android.chrome | Google Chrome-Browser | Chrome wird für einige WebView-Komponenten unter Android 7.0 und höher verwendet und wird nie ausgeblendet. Der Datenfluss zu und von der App ist jedoch immer eingeschränkt.
  | com.skype.raider | Skype | Die Skype-App ist nur für bestimmte Aktionen zulässig, die zu einem Anruf führen. |
  | com.android.providers.media | Android-Medieninhaltsanbieter | Dieser Inhaltsanbieter für Medien ist nur für die Aktion zum Auswählen von Klingeltönen zulässig. |
  | com.google.android.gms; com.google.android.gsf | Google Play Services-Pakete | Diese Pakete sind für Google Cloud Messaging-Aktionen zulässig, z.B. Pushbenachrichtigungen. |



##  <a name="access-settings"></a>Zugriffseinstellungen

| Einstellung | Verwendung | Standardwert(e) |
|------|------|------|
| **PIN für Zugriff anfordern** | Wählen Sie **Ja**, um zum Verwenden dieser App eine PIN anzufordern. Benutzer werden beim ersten Ausführen der App in einem Geschäfts-, Schul- oder Unikontext aufgefordert, diese PIN einzurichten. Standardwert = **Ja**<br><br> Konfigurieren Sie die folgenden Einstellungen für die PIN: <ul><li>**Anzahl der Versuche vor dem Zurücksetzen der PIN**: Geben Sie die Anzahl der Versuche an, die der Benutzer zum erfolgreichen Eingeben seiner PIN hat, ehe diese zurückgesetzt werden muss. Standardwert = **5**.</li><li> **Einfache PIN zulassen:** Wählen Sie **Ja**, um Benutzern das Verwenden einfacher PIN-Sequenzen wie z.B. 1234 oder 1111 zu erlauben. Wählen Sie **Nein**, um zu verhindern, dass einfache Sequenzen verwendet werden. Standardwert = **Ja** </li><li> **PIN-Länge:** Geben Sie die Mindestanzahl von Ziffern in einer PIN-Sequenz an. Standardwert = **4** </li><li> **Fingerabdruck anstelle von PIN zulassen (Android 6.0+):** Wählen Sie **Ja**, um Benutzern für den Zugriff auf die App das Verwenden der [Authentifizierung per Fingerabdruck](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) anstelle einer PIN zu erlauben. Standardwert = **Ja**</li></ul> Auf Android-Geräten können Sie es Benutzern ermöglichen, ihre Identität durch Verwendung der [Android-Fingerabdruckauthentifizierung](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) anstatt mit einer PIN nachzuweisen. Wenn der Benutzer versucht, diese App mit seinem Geschäfts-, Schul- oder Unikonto zu nutzen, wird er aufgefordert, seine Identität per Fingerabdruck und nicht durch Eingabe einer PIN zu bestätigen. </li></ul>| PIN anfordern: Ja <br><br> Versuche zum Zurücksetzen der PIN: 5 <br><br> Einfache PIN zulassen: Ja <br><br> PIN-Länge: 4 <br><br> Fingerabdruckentsperrung zulassen: Ja |
| **Unternehmensanmeldeinformationen für Zugriff erforderlich** | Wählen Sie **Ja**, um anzufordern, dass sich der Benutzer für den Zugriff auf die App mit seinem Geschäfts-, Schul- oder Unikonto anmeldet, anstatt eine PIN einzugeben. Wenn Sie diese Einstellung auf **Ja** festlegen, sind PIN oder Fingerabdruckidentifizierung damit hinfällig.  | Nein |
| **Ausführen verwalteter Apps auf Geräten mit Jailbreak oder Rootzugriff blockieren** |Wählen Sie **Ja** aus, um die Ausführung dieser App auf per Jailbreak oder Rootzugriff manipulierten Geräten zu verhindern. Der Benutzer kann diese App weiterhin für private Zwecke verwenden, muss jedoch für den Zugriff auf Geschäfts-, Schul- oder Unidaten ein anderes Gerät verwenden. | Ja  |
| **Überprüfen der Zugriffsanforderungen nach (Minuten)** | Konfigurieren Sie die folgenden Einstellungen: <ul><li>**Timeout**: Dies ist die Anzahl der Minuten, bis die (zuvor in der Richtlinie definierten) Zugriffsanforderungen erneut überprüft worden sind. Beispielsweise ein Administrator aktiviert die PIN in der Richtlinie, und ein Benutzer öffnet eine MAP-App und muss eine PIN eingeben. Wenn Sie diese Einstellung verwenden, muss der Benutzer für weitere **30 Minuten** (Standardwert) keine PIN bei MAM-Apps eingeben.</li><li>**Offline-Toleranzperiode**: Dies ist die Anzahl der Minuten, in den MAM-Apps offline sind. Geben Sie die Zeit (in Minuten) an, bevor die Zugriffsanforderungen für die App erneut geprüft werden. Standardwert = **720** Minuten (12 Stunden). Nachdem dieser Zeitraum abgelaufen ist, erfordert die App Benutzerauthentifizierung für AAD, sodass die App weiterhin ausgeführt werden kann.</li></ul>| Timeout: 30 <br><br> Offline: 720 |
| **Offline-Intervall (in Tagen), bevor App-Daten zurückgesetzt werden** | Nach diesem Zeitraum (durch den Administrator definiert) im Offline-Modus, führt die App selbst ein selektives Zurücksetzen aus. Dieses selektive Zurücksetzen ist dasselbe Zurücksetzen wie das, das durch den Administrator im Workflow zum selektiven Zurücksetzen für MAM initiiert werden kann. <br><br> | 90 Tage |
| **Bildschirmaufnahme und Android-Assistent blockieren (Android 6.0+)** | Wählen Sie **Ja** aus, um die Bildschirmaufnahme und den **Android-Assistenten** des Geräts zu blockieren, wenn diese App verwendet wird. Bei der Auswahl von **Ja** wird auch das Vorschaubild für den App-Schnellzugriff unscharf, wenn diese App mit einem Geschäfts-, Schul- oder Unikonto verwendet wird. | Nein |
| **App-PIN deaktivieren, wenn die Geräte-PIN verwaltet wird** | Wählen Sie **Ja**, um die App-PIN zu deaktivieren, wenn eine Gerätesperre auf einem registrierten Gerät erkannt wird. | Nein |
