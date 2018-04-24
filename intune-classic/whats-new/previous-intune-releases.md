---
title: Vorgängerversionen
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/13/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: NOINDEX,NOFOLLOW
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 57b2ab83f356eac27f668908a9a14b4f9310da19
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="previous-intune-releases"></a>Vorherige Versionen von Intune

Diese Seite ist eine Liste der Ankündigungen in [Neues in Microsoft Intune ](whats-new-in-microsoft-intune.md).

[!INCLUDE [wit_nextref](../includes/whats-new-last-six-months.md)]

## <a name="july-2016"></a>Juli 2016

### <a name="app-management"></a>App-Verwaltung

__Verbessern der Benutzererfahrung beim Update des App-Bereitstellungsprofils__ Die Apple iOS-Reihe mobiler Geschäfts-Apps wird mit einem integrierten Bereitstellungsprofil erstellt und mit Code, der mit einem Zertifikat signiert wurde. Beim Ausführen der App auf einem iOS-Gerät bestätigt iOS die Integrität der iOS-App und erzwingt Richtlinien, die durch das Bereitstellungsprofil definiert werden.

Das Unternehmenssignaturzertifikat, das Sie zum Signieren von Apps verwenden, ist in der Regel 3 Jahre lang gültig. Allerdings läuft das Bereitstellungsprofil nach 1 Jahr ab. Mit diesem Update stellt Intune Ihnen die Tools zum proaktiven Bereitstellen einer neuen Richtlinie für Bereitstellungsprofile auf Geräten zur Verfügung, auf denen Apps installiert sind, die bald ablaufen, während das Zertifikat noch gültig ist. Weitere Informationen finden Sie unter [Use iOS mobile provisioning profile policies to keep your line of business apps up to date](/intune-classic/deploy-use/ios-mobile-app-provisioning-profiles) (Verwenden von Richtlinien für iOS-Mobilbereitstellungsprofile, um Ihre Business-Apps aktuell zu halten).
<!--- TFS 1280247--->

__Xamarin SDK für Intune-Apps ist verfügbar__ Mit der Intune-App SDK-Xamarin-Komponente können Sie die Intune-Verwaltungsfeatures für mobile Apps in Ihren mit Xamarin erstellten mobilen iOS- und Android-Apps aktivieren. Sie finden die Komponente im [Xamarin Store](https://components.xamarin.com/view/Microsoft.Intune.MAM) oder auf der [Microsoft Intune-Github-Seite](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

### <a name="device-management"></a>Geräteverwaltung
__Höhere Limits bei der Geräteregistrierung__ Intune erhöhte das maximal konfigurierbare Limit für die Geräteregistrierung von 5 auf 15 Geräte pro Benutzer.
<!---TFS 1289896 --->

__TeamViewer-Integration für Windows-PCs, auf denen die Intune-Clientsoftware ausgeführt wird__
[TeamViewer](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).
<!---TFS 1284856--->

### <a name="company-portal-updates"></a>Aktualisierungen am Unternehmensportal

__Unternehmensportal-Website__
- **Verbesserte Endbenutzererfahrung bei der Registrierung von Windows-Geräten**<br/>
Wenn Sie den bedingten Zugriff verwenden, werden die Registrierungsschritte für Windows 8.1, Windows 10 Desktop und Windows 10 Mobile in der Unternehmensportal-Website erklärt. Benutzer sehen jetzt die separaten Schritte „Geräteregistrierung“ und „Workplace Join“, mit denen sie leichter den Status ihres Geräts anzeigen und den Prozess abschließen können, wenn ein Fehler beim Workplace Join (WPJ) auftritt. Die separaten Schritte sollten auch die Problembehandlung für IT-Administratoren vereinfachen. Wenn Endbenutzer versuchten, das Gerät zu registrieren, und alle Registrierungsschritte außer dem WPJ erfolgreich verliefen, wurde das registrierte Gerät bisher nicht in der Liste der Geräte angezeigt, die Benutzer identifizieren konnten, und dies verwirrte die Benutzer.

__Android__
- **Android-Unternehmensportal-App**<br/>
Wenn Android-Endbenutzer von einer Fehlermeldung darüber informiert werden, dass ein erforderliches Zertifikat auf ihrem Gerät fehlt, können Sie auf die Schaltfläche „Problembehebung“ tippen, um mit [Schritte](/intune-classic/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues) zu erhalten, die IT-Administratoren verwenden können, um das Zertifikatproblem zu beheben.

- **Einschränken der Installationen quergeladener Apps auf registrierten Geräten**<br/>
Auf Android-Geräten können nicht mehr Apps über die Unternehmensportal-Website installiert werden, es sei denn, die Geräte wurden mithilfe der Intune-Unternehmensportal-App für Android in Intune registriert.
<!---TFS 1299082--->

__iOS__
- **Änderungen an den Geräteregistrierungs-Manager-Konten in der iOS-Unternehmensportal-App**<br/>
Zum Verbessern der Leistung und Skalierung zeigt Intune nicht mehr alle Geräte des Geräteregistrierungs-Managers (Device Enrollment Manager, DEM) im Bereich **Meine Geräte** der Unternehmensportal-App für iOS an. Nur das lokale Gerät, das die App ausführt, wird angezeigt, und dies nur, wenn es über die Unternehmensportal-App registriert wurde.

Der DEM-Benutzer kann Aktionen auf dem lokalen Gerät ausführen, aber die Remoteverwaltung der anderen registrierten Geräte kann nur über die Intune-Verwaltungskonsole durchgeführt werden. Darüber hinaus verwirft Intune die Verwendung von DEM-Konten mit dem Apple-Programm zur Geräteregistrierung oder dem Apple Configurator Tool als veraltet. Die beiden Registrierungsmethoden unterstützen bereits die Registrierung ohne Benutzer für freigegebene iOS-Geräte.

Verwenden Sie DEM-Konten nur, wenn die Registrierung ohne Benutzer für gemeinsam genutzte Geräte nicht verfügbar ist. Weitere Informationen siehe [Registrieren von firmeneigenen Geräten mit dem Geräteregistrierungs-Manager in Microsoft Intune](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

### <a name="change-of-names-for-windows-features"></a>Ändern von Namen für Windows-Features
- [Microsoft Passport für Windows](/intune-classic/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) heißt jetzt **Windows Hello for Business**.
- [Unternehmensdatenschutz](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) heißt jetzt **Windows Information Protection**.


## <a name="june-2016"></a>Juni 2016
### <a name="intune-service-health"></a>Status des Intune-Diensts
Informationen zum Status des Intune-Diensts wurden wie für andere Microsoft-Dienste an einen zentralen Speicherort verschoben. Sie finden diese Informationen jetzt im Verwaltungsportal von Office 365 unter „Dienststatus“. Weitere Informationen finden Sie in [diesem Blogbeitrag](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### <a name="app-management"></a>App-Verwaltung
- **Höhere Benutzerfreundlichkeit bei der Richtlinienkonfiguration für Unternehmensdaten in Windows 10.** Wir haben die Benutzerfreundlichkeit bei der Richtlinienkonfiguration für den Windows 10-Unternehmensdatenschutz verbessert. Dabei wurden Aufgaben wie das Erstellen von App-Regeln, das Festlegen von Definitionen für Netzwerkgrenzen und andere Einstellungen für den Unternehmensdatenschutz vereinfacht. Weitere Informationen finden Sie unter [Create an enterprise data protection (EDP) policy using Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) (Erstellen einer Enterprise Data Protection-Richtlinie (EDP) mithilfe von Microsoft Intune).


### <a name="device-management"></a>Geräteverwaltung
- **Windows Defender-Richtlinieneinstellung zum Schutz gegen potenziell unerwünschte Apps.** Die allgemeine Konfigurationsrichtlinie für Windows 10 Desktop und Mobile wurde um die neue Windows Defender-Einstellung **Erkennung möglicherweise unerwünschter Anwendungen** erweitert. Mit dieser Einstellung können registrierte Windows-Desktopcomputer gegen Software geschützt werden, die von Windows Defender als möglicherweise unerwünscht eingestuft wird. Sie können verhindern, dass diese Anwendungen ausgeführt werden, oder den Überwachungsmodus verwenden, um zu melden, wenn eine möglicherweise unerwünschte Anwendung installiert wird. Weitere Informationen finden Sie unter [Einstellungen für Windows 10-Richtlinien in Microsoft Intune](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

### <a name="conditional-access"></a>Bedingter Zugriff
- **Cisco ISE-Netzwerkzugriffssteuerungs-Richtlinie für Intune.**  Kunden, die Cisco Identity Service Engine (ISE) 2.1 und Microsoft Intune verwenden, können eine Netzwerkzugriffssteuerungs-Richtlinie in ISE festlegen.

    Bei Verwendung dieser Richtlinie müssen Geräte, die sich über WLAN oder VPN verbinden müssen, die folgenden Voraussetzungen erfüllen, bevor sie Zugriff erhalten:

    * Die Geräte müssen über Intune verwaltet werden
    * Kompatibilität mit allen bereitgestellten Intune-Konformitätsrichtlinien

  Endbenutzer mit nicht konformen Geräten werden aufgefordert, sich zu registrieren und jegliche Konformitätsprobleme zu beheben, um Zugriff zu erhalten.
- **Bedingter Zugriff für Browser.** Sie können eine Richtlinie für bedingten Zugriff für [Exchange Online](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) festlegen, sodass nur von unterstützten Webbrowsern auf verwalteten und kompatiblen IOS- und Android-Geräten aus auf sie zugegriffen werden kann. Endbenutzer, die versuchen, sich bei Outlook Web Access- (OWA) und SharePoint-Standorten mit iOS- und Android-Geräten anzumelden, werden aufgefordert, ihr Gerät bei Intune zu registrieren und alle Nichtkompatibilitätsprobleme zu beheben, bevor eine vollständige Anmeldung möglich ist.
  <!---TFS 1175844--->

- **Dynamics CRM Online unterstützt den bedingten Zugriff.** Sie können eine Richtlinie für den bedingten Zugriff für [Dynamics CRM Online](/intune-classic/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune) festlegen, sodass nur der Zugriff durch verwaltete und konforme iOS- und Android-Geräte möglich ist. Endbenutzer, die versuchen, sich bei der mobilen Dynamics CRM-App für iOS und Android anzumelden, werden aufgefordert, sich bei Intune zu registrieren und alle Konformitätsprobleme zu beheben, bevor die Anmeldung abgeschlossen werden kann.
  <!---TFS1295358--->

### <a name="intune-company-portal-updates"></a>Aktualisierungen des Intune-Unternehmensportals

__Android-Unternehmensportal-App__

- Wenn IT-Administratoren die neue Richtlinie „Require that devices disallow installation of apps from unknown sources (Android 4.0+)“ (Geräte dürfen die Installation von Apps aus unbekannten Quellen nicht erlauben (Android 4.0 und höher)) anwenden, wird Endbenutzern mit Geräten mit Android 4.0 oder höher die Meldung „Die Installation von unbekannten Quellen muss deaktiviert sein.“ angezeigt. Benutzer müssen zu **Einstellungen** > **Sicherheit** wechseln und **Unbekannte Quellen** deaktivieren. Durch einen Link in der Konformitätsmeldung erhalten Benutzer mehr [Informationen](/intune-user-help/you-are-asked-to-turn-off-unknown-sources-android) zu der Meldung und zu dem Grund, aus dem sie dazu aufgefordert werden, die Einstellung zu deaktivieren.

- Wenn IT-Administratoren die neue Richtlinie „Require that devices have enabled scanning of apps for security threats (Android 4.0+)“ (Bei Geräten muss die Option zum Überprüfen von Apps auf Sicherheitsbedrohungen aktiviert sein (Android 4.0 und höher)) anwenden, wird Endbenutzern mit Geräten mit Android 4.0 oder höher die Meldung „Gerät auf Sicherheitsbedrohungen überprüfen.“ angezeigt. Benutzer müssen zu **Einstellungen** > **Google** > **Sicherheit** wechseln und **Gerät auf Sicherheitsbedrohungen überprüfen** aktivieren. Durch einen Link in der Konformitätsmeldung erhalten Benutzer mehr [Informationen](/intune-user-help/you-are-asked-to-turn-on-scan-device-for-security-threats-android) zu der Meldung und zu dem Grund, aus dem sie dazu aufgefordert werden, die Einstellung zu aktivieren.

- Wenn IT-Administratoren die neue Richtlinie „USB-Debuggen muss deaktiviert sein (Android 4.2 und höher)“ anwenden, wird Endbenutzern mit Geräten mit Android 4.2 oder höher die Meldung „USB-Debuggen muss deaktiviert sein.“ angezeigt. Benutzer müssen zu **Einstellungen** > **Entwickleroptionen** wechseln und **USB-Debuggen** deaktivieren. Durch einen Link in der Konformitätsmeldung erhalten Benutzer mehr [Informationen](/intune-user-help/you-are-asked-to-turn-off-usb-debugging-android) zu der Meldung und zu dem Grund, aus dem sie dazu aufgefordert werden, die Einstellung zu deaktivieren.

- Wenn IT-Administratoren die neue Richtlinie „Niedrigste zulässige Android-Sicherheitspatchebene (Android 6.0 und höher)“ anwenden, wird Endbenutzern mit Geräten mit Android 6.0 oder höher die Meldung „Dieses Gerät weist nicht die mindestens erforderliche Ebene für Android-Sicherheitspatches auf.“ angezeigt. Benutzer müssen den erforderlichen Sicherheitspatch installieren. Durch einen Link in der Konformitätsmeldung erhalten Benutzer mehr [Informationen](/intune-user-help/you-are-asked-to-turn-on-scan-device-for-security-threats-android) dazu, wie der erforderliche Sicherheitspatch installiert wird und wie Sie sehen können, welcher Sicherheitspatch aktuell installiert ist.

__iOS-Unternehmensportal-App__

- Wenn Endbenutzer branchenspezifische Apps installieren, sehen sie jetzt eine verbesserte Benutzeroberfläche für die App-Installation. Wenn die App-Installation sehr lange dauert, können Benutzer das Gerät manuell synchronisieren, um eine Fortsetzung des Synchronisierungsprozesses zu erzwingen. Die Anweisungen für Endbenutzer finden Sie unter [Manuelles Synchronisieren des Geräts](/intune-user-help/sync-your-device-manually-ios).

- Die Microsoft Windows Intune-Unternehmensportal-App für iOS wurde aktualisiert, um die iOS-Version 8.0 und höher zu unterstützen. Dieses Update bedeutet, dass Endbenutzer die Unternehmensportal-App nur installieren und neue Geräte in Intune nur registrieren können, wenn auf dem Gerät iOS Version 8.0 oder höher ausgeführt wird. Benutzer, die bereits Geräte registriert haben, auf denen eine nicht unterstützte Version von iOS ausgeführt wird, können weiterhin die auf ihrem Gerät vorhandene Unternehmensportal-App verwenden.

## <a name="may-2016"></a>Mai 2016
Alle diese Features werden auch für hybride Bereitstellungen (Configuration Manager mit Intune) unterstützt. Weitere Informationen zu neuen Hybridfeatures finden Sie auf unserer [Seite mit neuen Hybridfeatures](https://technet.microsoft.com/library/mt718155.aspx).

### <a name="documentation"></a>Dokumentation
Willkommen bei der Preview-Version von [docs.microsoft.com](https://docs.microsoft.com/intune)!
Dies ist eine vollständig neue, moderne Inhaltsplattform, die Ihnen, unseren Kunden, helfen soll, Intune zu verstehen und zu nutzen.
Weitere Informationen zu allen neuen Features finden Sie unter [docs.microsoft.com: Einführung](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/).

### <a name="intune-service-health"></a>Status des Intune-Diensts
Informationen zum Status des Intune-Diensts wurden wie für andere Microsoft-Dienste an einen zentralen Speicherort verschoben. Sie finden diese Informationen jetzt im [Verwaltungsportal von Office 365](https://portal.office.com/Admin/Default.aspx) unter **Dienststatus**.
Weitere Informationen finden Sie in [diesem Blogbeitrag](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### <a name="app-management"></a>App-Verwaltung
- **MAM SDK: Unterstützung für die Konfiguration der PIN-Länge.** Sie können die Länge der PIN für MAM-Apps angeben, ähnlich wie eine Geräte-PIN. Dazu müssen Endbenutzer die neuen Einschränkungen einhalten, die Sie festlegen. Sie sehen einen leicht abgewandelten PIN-Bildschirm, mit dem längere Eingaben möglich sind. Weitere Informationen finden Sie unter [MAM policy settings for Android (MAM-Richtlinieneinstellungen für Android)](/intune-classic/deploy-use/ios-mam-policy-settings).

- **Skype for Business für iOS und Android.** Sie können jetzt Skype for Business mit [MAM ohne Registrierungsrichtlinien](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune) einrichten. Sobald Benutzer angemeldet sind, werden die MAM-Richtlinien angewendet.

- **Neue Apps für die Verwaltung mit MAM-Richtlinien verfügbar.** Die Apps Microsoft Word, Excel und PowerPoint für Android können jetzt MAM-Richtlinien auf Geräten zugeordnet werden, die nicht bei Intune registriert sind. Die vollständige Liste der unterstützten Apps finden Sie im Microsoft Intune-Katalog mit mobilen Anwendungen auf der Seite mit den [Microsoft Intune-Anwendungspartnern](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx).


### <a name="company-portal-updates"></a>Aktualisierungen am Unternehmensportal

#### <a name="android-company-portal-app"></a>Android-Unternehmensportal-App
- **Popupbenachrichtigungen für Endbenutzer**: Endbenutzer sehen jetzt Popupbenachrichtigungen in der Android-Unternehmensportal-App, wenn Sie ihre Geräte im Unternehmensportal registrieren oder sie daraus entfernen.

- **Änderungen an den Geräteregistrierungs-Manager-Konten in der Android-Unternehmensportal-App.** Zum Verbessern der Leistung und Skalierung zeigt Intune nicht mehr alle Geräte des Geräteregistrierungs-Managers (Device Enrollment Manager, DEM) im Bereich „Meine Geräte“ der Android-Unternehmensportal-App an. Nur das lokale Gerät, das die App ausführt, wird angezeigt, und dies nur, wenn es über die Unternehmensportal-App registriert wurde. Der DEM-Benutzer kann Aktionen auf dem lokalen Gerät ausführen, aber die Remoteverwaltung der anderen registrierten Geräte kann nur über die Intune-Verwaltungskonsole ausgeführt werden.

#### <a name="company-portal-website"></a>Unternehmensportal-Website
- **Unternehmensportal-Website: Banner für die Geräteidentifikation stellt zusätzliche Informationen für Endbenutzer bereit.** Benutzer können das ausgewählte Gerät nun leichter identifizieren, wenn sie die Unternehmensportal-Website verwenden. Wenn das falsche Gerät ausgewählt wird, können sie das richtige Gerät auswählen, indem sie auf den Link **Hier tippen** im Banner auf der Startseite tippen.

### <a name="service-deprecation"></a>Veraltete Dienste
- **Intune Viewer-Apps.** Mit der Veröffentlichung der neuen RMS-Freigabe-App werden wir ab August 2016 die folgenden Intune Viewer-Apps entfernen:
    - Intune AV Viewer
    - Intune PDF Viewer
    - Intune Image Viewer für Android aus Google Play

  Anstatt die Intune-Viewer-Apps zu verwenden, empfehlen wir die Nutzung der neuen Rights Management-App (RMS-Freigabe) für Android, die Ihnen das Bereitstellen einer App anstelle von drei getrennten Apps ermöglicht, um Unternehmensdateien sicher auf Android-Geräten anzuzeigen. Weitere Informationen zur RMS-Freigabe-App (mit Link zur Dokumentation).

- **Entfernung der Zielgruppenadressierung benutzerdefinierter Gruppen bei Benachrichtigungsregeln.**
Intune-Benachrichtigungsregeln definieren, an wen aus Intune eine E-Mail-Benachrichtigung gesendet wird. Derzeit können Sie Benachrichtigungsregeln zum Senden von E-Mails an alle Benutzer von Geräten in einer Intune-Gerätegruppe konfigurieren, die Sie erstellt haben. Ab Anfang Juni 2016 wird die Adressierung von Gruppen, die von Benutzern erstellt wurden, nicht mehr unterstützt.

    Mittlerweile müssen Sie eine Benachrichtigungsregel einer Gruppe, die Sie in der Microsoft Intune-Verwaltungskonsole erstellt haben, wie folgt zuordnen:

    Klicken Sie im Arbeitsbereich **Verwaltung** auf **Benachrichtigungsregeln** > **Neue Regel erstellen**.

    In Schritt 2 des Assistenten zum Erstellen von Benachrichtigungsregeln wählen Sie die Gerätegruppen aus, für die die Regel gelten soll. Der Schritt „Gerätegruppen auswählen“ wurde aus der Intune-Konsole entfernt.

    Der vorläufige Zeitplan für diese Änderung ist wie folgt:
    - Im Juni 2016 wird neuen Mandanten Schritt 2 im Assistenten zum Erstellen von Benachrichtigungsregeln nicht mehr angezeigt. Vorhandene Mandanten sind nicht betroffen.
    - Ab August 2016 wird einigen vorhandenen Mandanten der Schritt „Gerätegruppen auswählen“ im Assistenten nicht angezeigt.
    - Ab Oktober 2016 wird für alle Mandanten der Schritt „Gerätegruppen auswählen“ im Assistenten nicht mehr angezeigt.


- **Änderungen bei der Unterstützung der iOS-Unternehmensportal-App**. In den kommenden Monaten erfolgt ein Update für die Microsoft Intune-Unternehmensportal-App für iOS, die nur Geräte mit mindestens iOS 8.0 unterstützt. Benutzer können neue Geräte mit Versionen unter iOS 8.0 nicht registrieren. Registrierte Geräte mit Versionen unter iOS 8.0 werden weiterhin verwaltet und können für einen begrenzten Zeitraum die Unternehmensportal-App weiter nutzen. Für den Zugriff auf die neuesten Versionen der Unternehmensportal-App benötigen Geräte mindestens die iOS-Version 8.0. Wir empfehlen Ihnen, Benutzer zum Update auf iOS 8.0 oder höher aufzufordern, damit sie in den vollen Genuss der neuen Intune-Features kommen.  


## <a name="april-2016"></a>April 2016
Alle diese Features werden auch für hybride Kundenbereitstellungen (Configuration Manager integriert in Intune) unterstützt.

### <a name="app-management"></a>App-Verwaltung
- **MAM-Benutzerkompatibilität.**
  Sie können nun den [Status](/intune-classic/deploy-use/monitor-mobile-app-management-policies-with-Microsoft-Intune) von Anwendungsverwaltungsrichtlinien für alle Benutzer in Ihrem Azure Active Directory-Mandanten (AAD) anzeigen. Dies umfasst u. a.:
  - Geräte
  - Apps auf dem Gerät

    Statuswerte:

    **Eingecheckt**: Gibt an, dass die Richtlinie dem Benutzer bereitgestellt wurde, dass die App im Kontext verwendet wurde und dass sie die Richtlinie erfolgreich empfangen hat.

    **Nicht eingecheckt**: Gibt an, dass die Richtlinie dem Benutzer bereitgestellt wurde, die App seitdem aber nicht im Arbeitskontext verwendet wurde.


- **MAM-Steuerelemente, um die Synchronisierung von Outlook-Kontakten zu verhindern (Android).**
  Es ist eine neue Einstellung für die [mobile Anwendungsverwaltung](/intune-classic/deploy-use/wipe-managed-company-app-data-with-Microsoft-Intune) verfügbar; Kontakte, die schon im nativen Adressbuch gespeichert wurden, werden entfernt. Diese neue Einstellung wird anfänglich von der Outlook-Anwendung auf Android-Geräten unterstützt.

### <a name="device-management"></a>Geräteverwaltung
- **Telefonnummeridentifikation für unternehmenseigene Geräte.** Telefone, die als „Unternehmen“ eingestuft sind, werden jetzt mit der vollständigen Telefonnummer identifiziert, wenn Sie beispielsweise einen Inventurbericht für mobile Geräte ausführen. BYOD-Telefonnummern werden weiterhin mit *** maskiert, und nur die letzten vier Ziffern werden angezeigt.


### <a name="company-portal-updates"></a>Aktualisierungen am Unternehmensportal
**Android-Unternehmensportal-App** Benutzer, die ihre Geräte nicht bei Intune registriert haben und die nicht das richtige Zertifikat installiert haben, können sich nicht bei der Android-Unternehmensportal-App anmelden. Ihnen wird die Meldung angezeigt, dass eine Anmeldung nicht möglich sei, da ein erforderliches Zertifikat auf dem Gerät nicht vorhanden sei. Die Meldung enthält einen Link zum Beheben dieses Problems, den Benutzer nutzen können, um eine Anleitung zum Installieren des Zertifikats zu erhalten. Die Schritte, denen die Endbenutzer folgen, um das Problem zu beheben, finden Sie unter [Auf Ihrem Gerät ist ein erforderliches Zertifikat nicht vorhanden](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**iOS-Unternehmensportal-App** Unterstützung für die Aktion „Zum Aktualisieren ziehen“ wurde hinzugefügt, um den Inhalt auf dem Startbildschirm zu aktualisieren, einschließlich der aufgelisteten Apps und Geräte sowie der IT-Kontaktinformationen. Mit der Aktion „Zum Aktualisieren ziehen“ werden Kompatibilitäts- oder Richtlinieninformationen nicht überprüft. Sie erreichen dies, indem Sie die Kachel für das aktuelle Gerät auswählen und auf die Schaltfläche **Synchronisieren** tippen.

**Windows 10 Mobile- und Windows Phone 8.1-Unternehmensportal-App** Wenn Endbenutzer branchenspezifische Apps installieren, sehen sie jetzt eine verbesserte Benutzeroberfläche für die App-Installation. Wenn die App-Installation sehr lange dauert, können Benutzer das Gerät manuell synchronisieren, um eine Fortsetzung des Synchronisierungsprozesses zu erzwingen. Die Anweisungen für Endbenutzer finden Sie unter [Manuelles Synchronisieren des Geräts, um Anwendungsinstallationen zu beschleunigen](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Unternehmensportal-Website** Wenn Windows 10 Mobile- und Windows Phone 8.1-Benutzer branchenspezifische Apps installieren, sehen sie jetzt die folgenden neuen Status, die ihnen weitere Details zum Status ihrer Installation zur Verfügung zu stellen:

* **Gerätesynchronisierung ausstehend**: Der Benutzer hat auf „Installieren“ getippt hat, und das Gerät versucht nun, eine Synchronisierung mit der Intune-Infrastruktur durchzuführen. Die Synchronisierung ist erforderlich, bevor die Installation abgeschlossen werden kann. Die Meldung „Gerätesynchronisierung ausstehend“ ist außerdem ein Link, auf den Benutzer tippen können, um die [Anweisungen](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) zum manuellen Synchronisieren ihres Geräts mit Intune anzuzeigen, wenn die Synchronisierung sehr lange dauert oder unterbrochen wird.
* **Wird heruntergeladen**: Die Downloadanforderung des Benutzers wird verarbeitet, und das Gerät lädt die App herunter und installiert sie.

Bevor diese Statusangaben hinzugefügt wurden, waren die Benutzer verunsichert, wenn die Installation einer App sehr lange dauerte, da nur ein Status „Wird installiert“ angezeigt wurde – und das möglicherweise für Stunden. Das Hinzufügen der neuen Statusangaben bedeutet, dass sich Benutzer nicht an den Support wenden müssen, sondern auf den Link „Gerätesynchronisierung ausstehend“ tippen und den Anweisungen folgen können, um die Fortsetzung des Synchronisierungsprozesses zu erzwingen.

> [!div class="step-by-step"]
> 
> [&larr; **Neuheiten in Intune**](whats-new-in-microsoft-intune.md)    
