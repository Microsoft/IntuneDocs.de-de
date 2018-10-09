---
title: Datenverwaltung von Office 365-Apps in Microsoft Intune
titlesuffix: ''
description: Erfahren Sie mehr über die Datenverwaltung von Office 365-Apps in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 852612ac-f146-4372-a900-3f6fdebd05ad
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ayesham
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d90ede39ab9daeb24cc1545dda93054550ed1152
ms.sourcegitcommit: 28262384ec94e43970cc7a33e5d9063972bdf468
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "48799607"
---
# <a name="how-your-users-will-experience-basic-protection-on-managed-office-365-apps-in-microsoft-intune"></a>Was der grundlegende Schutz in verwalteten Office 365-Apps in Microsoft Intune beinhaltet umfasst.

Der Assistent zum **Verwalten von Office 365-Apps** erstellt eine App-Schutzrichtlinie für jede Geräteplattform.

Der Assistent aktiviert die folgenden Richtlinien:

**iOS**
* App-Daten verschlüsseln

**Android**
* App-Daten verschlüsseln
* Einfache PIN für Zugriff erforderlich

Diese Richtlinien stellen sicher, dass Sie die Office 365-Apps verwalten können. Außerdem bietet Sie Ihnen die Möglichkeit, Arbeitsdaten bei Bedarf aus Office-Apps zu löschen. Sie sorgen auch für einen Basisschutz, wenn ein Gerät verloren geht oder gestohlen wird, indem sie sicherstellen, dass Ihre Arbeitsdaten verschlüsselt werden und eine PIN eingegeben werden muss, um die Daten in Office 365-Apps anzuzeigen.


In diesem Artikel wird OneDrive for Business als Beispiel verwendet, um die Benutzererfahrung in einer von Intune verwalteten Anwendung zu veranschaulichen.


>[!NOTE]
>Auf einem privaten Gerät würde der Endbenutzer normalerweise die App herunterladen. Wenn das Gerät jedoch mit einer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) verwaltet wird, können Sie die App auf dem Gerät bereitstellen.

## <a name="user-experience-on-an-ios-device"></a>Benutzererfahrung auf einem iOS-Gerät

1. Starten Sie die OneDrive for Business-App, um die Anmeldeseite zu öffnen.  
2. Geben Sie den Benutzernamen Ihres Geschäftskontos ein. Sie werden zur Seite „Office 365-Authentifizierung“ umgeleitet, auf der Sie Ihre Unternehmensanmeldeinformationen eingeben können. 
3. Nach der erfolgreichen Authentifizierung Ihrer Anmeldeinformationen durch Azure Active Directory werden die App-Schutzrichtlinien angewendet, und Sie werden aufgefordert, die OneDrive for Business-App neu zu starten. 

   > [!NOTE]
   > Die Meldung „Neustart erforderlich“ wird nur auf Geräten angezeigt, die nicht bei Intune registriert sind.

4. Starten Sie die OneDrive for Business-App neu. Die Anwendung wird mit aktivierten App-Schutzrichtlinien gestartet, und Sie werden aufgefordert, eine PIN für das Gerät festzulegen (sofern Sie noch keine PIN für das Gerät konfiguriert haben).  

   > [!NOTE]
   > Den meisten Benutzern wird diese Aufforderung nicht angezeigt. Nur Benutzer, die auf ihrem iOS-Gerät keine PIN aktiviert haben, werden diese Meldung sehen.

5. Nachdem Sie die PIN festgelegt und bestätigt haben, kehren Sie zur OneDrive for Business-App zurück. Sie sehen eine einmalige Benachrichtigung, dass der IT-Administrator Arbeitsdaten in OneDrive jetzt schützt. 
6. Bestätigen Sie diese Mitteilung, um auf die Dateien in OneDrive for Business zuzugreifen. 

>[!NOTE]
>Wenn Sie eine schon bereitgestellte Richtlinie ändern, werden die Änderungen beim nächsten Öffnen der App angewendet.

## <a name="user-experience-on-an-android-device"></a>Benutzererfahrung auf einem Android-Gerät

1. Starten Sie die OneDrive for Business-App, um die Anmeldeseite zu öffnen.  <br/> ![Abbildung des Begrüßungsbildschirms der OneDrive-App](./media/onedrive-android-welcome.png)
2. Geben Sie den Benutzernamen Ihres Geschäftskontos ein. Sie werden zur Seite „Office 365-Authentifizierung“ umgeleitet, auf der Sie Ihre Unternehmensanmeldeinformationen eingeben können. <br/> ![Abbildung der Office 365-Anmeldung unter Android](./media/o365-sign-in-android.png)
3. Nach der erfolgreichen Authentifizierung Ihrer Anmeldeinformationen durch Azure Active Directory wird eine Meldung mit Anweisungen zur Installation der Unternehmensportal-App angezeigt, sofern diese auf dem Gerät noch nicht installiert ist. Tippen Sie auf **Zum Store gehen**, um den Vorgang fortzusetzen. <br/> ![Abbildung der Benachrichtigung zur Installation der Unternehmensportal-App](./media/get-company-portal-android.png) <br/>Wenn Sie die Unternehmensportal-App bereits auf Ihrem Telefon installiert haben, wird die OneDrive for Business-App automatisch gestartet, und Sie können bis zum Ende des Hinweises überspringen.   

   > [!IMPORTANT]
   > Wenn Sie unter Android einmal die Verwaltung von Office-Apps durch eine App-Schutzrichtlinie festgelegt haben, **müssen** Benutzer des Geräts die Unternehmensportal-App installieren, um Zugriff auf Arbeits-E-Mails und -dokumente zu erhalten, obwohl der Endbenutzer die App nicht öffnen oder sich in dieser anmelden muss, um E-Mails oder Dokumente zu lesen.

4. Sie befinden sich nun im Google Play Store, von wo Sie die Unternehmensportal-App herunterladen und installieren können. Die App hilft Ihnen, Ihre Daten zu schützen. <br/> ![Abbildung der App im Google Play Store](./media/google-play-get-app-android.png)
5. Wählen Sie nach Abschluss der App-Installation **Annehmen** aus, um die Bedingungen zu akzeptieren. Die OneDrive for Business-App wird automatisch gestartet.


>[!NOTE]
>Beim nächsten Öffnen von OneDrive for Business werden Sie möglicherweise aufgefordert, eine PIN festzulegen, wenn die IT-Abteilung dies vorschreibt. Nachdem Sie die PIN festgelegt und bestätigt haben, können Sie OneDrive for Business weiter verwenden.

![Abbildung der Aufforderung für die PIN](./media/pin-prompt-android.png)


<!--- Original steps: 6. The next time you open OneDrive for Business, you may be asked to set a PIN, if your IT requires one to use the OneDrive for Business app. ART 7. After you set and confirm the PIN, you can continue on to OneDrive for Business. -->

## <a name="what-policies-does-this-wizard-set"></a>Welche Richtlinien legt dieser Assistent fest?

|     |       | |
|----|--------|-|
|**Name**|Verwalten von Office 365-Apps| |
| **Beschreibung**|Erstellt vom Assistenten zum Verwalten von Office 365-Apps| |
| |  | |
| **Einstellungsname** |**iOS-Richtlinienwert** | **Android-Richtlinienwert** |
|iTunes- und iCloud-Datensicherungen verhindern| Nein | N/V |
|Android-Datensicherungen verhindern |N/V | Nein|
|App Übertragung von Daten an andere Apps erlauben | Alle Apps | Alle Apps|
|App Empfang von Daten aus anderen Apps erlauben| Alle Apps | Alle Apps|
|"Speichern unter" verhindern | Nein | Nein|
|Ausschneiden, Kopieren und Einfügen mit anderen Apps einschränken | Jede App | Jede App |
|Einschränken von anzuzeigenden Webinhalten in einem unternehmensverwalteten Browser | Nein| Nein|
|App-Daten verschlüsseln | Wenn das Gerät gesperrt ist | Ja |
|Kontaktsynchronisierung deaktivieren | Nein| Nein|
|Drucken deaktivieren | Nein | Nein|
|PIN für Zugriff anfordern | Nein | Ja |
|Anzahl der Versuche vor dem Zurücksetzen der PIN | N/V |5|
|Einfache PIN zulassen | N/V |Ja |
|PIN-Länge | N/V | 4|
|Fingerabdruck anstelle von PIN zulassen | N/V | Ja  |
|Unternehmensanmeldeinformationen für Zugriff erforderlich | Nein | Nein|
|Blockieren der Ausführung von verwalteten Apps auf per Jailbreak oder Rooting manipulierten Geräten | Nein | Nein|
|Zugriffsanforderungen nach (Minuten) erneut überprüfen – Timeout | 30 | 30|
|Zugriffsanforderungen nach (Minuten) erneut überprüfen – Offline-Toleranzperiode | 720 |720|
|Offline-Intervall (in Tagen), bevor App-Daten zurückgesetzt werden | 90 | 90|
|Bildschirmaufnahme blockieren (nur Android-Geräte) | N/V | Nein |

### <a name="why-is-an-app-pin-policy-only-configured-for-android-devices"></a>Warum nur für Android-Geräte eine App-PIN-Richtlinie konfiguriert?
Die Verschlüsselung funktioniert unter iOS und Android unterschiedlich.

Für Apps unter iOS, die einer Intune-App-Schutzrichtlinie zugeordnet sind, werden ruhende Daten mit vom Betriebssystem bereitgestellter Verschlüsselung auf Geräteebene verschlüsselt. Wenn Sie die App-Verschlüsselungsrichtlinie aktivieren, muss der Benutzer auch automatisch eine Geräte-PIN besitzen und eingeben, um auf Arbeitsdaten zugreifen zu können. Benutzer, die auf dem Gerät noch keine Geräte-PIN konfiguriert haben, werden zum Erstellen einer Geräte-PIN aufgefordert.

Unter Android werden für Daten für Apps, die einer Intune-App-Schutzrichtlinie zugeordnet sind, während der E/A-Dateivorgänge synchron verschlüsselt. Inhalt im Gerätespeicher wird immer verschlüsselt. Auf Geräten, die nicht MDM-verwaltet sind, kann die App-Schutzrichtlinie die Anforderung einer Geräte-PIN auch nicht erzwingen. Um sicherzustellen, dass Benutzer einige PIN für den Zugriff auf Arbeitsdaten verwenden müssen, aktiviert der Assistent die App-PIN-Richtlinie.

Sie können diese Richtlinieneinstellungen jederzeit an die Anforderungen Ihrer Organisation anpassen.

### <a name="how-can-i-view-and-edit-the-policies-created-by-the-wizard"></a>Wie kann ich die vom Assistenten erstellten Richtlinien anzeigen und bearbeiten?
Wenn Sie diese Richtlinien oder andere Richtlinien, die Sie im Intune-Azure-Portal erstellt haben, anzeigen oder aktualisieren möchten, wählen Sie im Dashboard **Apps verwalten** > **App-Schutzrichtlinien** aus. Die Liste der Richtlinien wird auf der rechten Seite geöffnet. Wählen Sie die gewünschte Richtlinie aus, um die Einstellungen anzuzeigen und zu bearbeiten. <br/>
![Abbildung des Benutzeroberflächenpfads zum Anzeigen von Richtlinien](./media/image-for-faq.png)

## <a name="next-steps"></a>Nächste Schritte
- Erfahren Sie mehr über [App-Schutzrichtlinien](app-protection-policy.md).
