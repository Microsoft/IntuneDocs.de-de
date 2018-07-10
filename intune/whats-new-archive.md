---
title: Neuerungen in den vorherigen Monaten in Microsoft Intune – Azure | Microsoft-Dokumentation
titlesuffix: ''
description: Überprüfen Sie ältere Ankündigungen auf der Intune-Seite mit den Neuerungen
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5f6e44c083e08e4b4d34e6f8f60365e0511fa148
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31837213"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Neuerungen in Microsoft Intune (vorherige Monate)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="october-2017"></a>Oktober 2017

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>Die branchenspezifische App-Versionsnummer für iOS und Android ist sichtbar <!-- 1380712 -->.

Apps in Intune zeigen nun die Versionsnummer für branchenspezifische iOS- und Android-Apps an. Die Nummer wird im Azure-Portal in der App-Liste und im Übersichtsblatt der App angezeigt. Benutzer können die App-Nummer in der Unternehmensportal-App und im Webportal anzeigen.

__Vollständige Versionsnummer__: Die vollständige Versionsnummer identifiziert ein bestimmtes Release der App. Die Nummer wird als _Version_(_Build_) angezeigt. Beispielsweise 2.2(2.2.17560800)

Die vollständige Versionsnummer besteht aus zwei Komponenten:

 - **Version**  
   Die Versionsnummer ist die von einem Menschen lesbare Releasenummer der App. Diese wird von Benutzern verwendet, um verschiedene Releases der App zu identifizieren.

 - **Buildnummer**  
    Die Buildnummer ist eine interne Nummer, die in der App-Erkennung und zur programmgesteuerten Verwaltung der App verwendet werden kann. Die Buildnummer bezieht sich auf eine Iteration der App, die auf Änderungen im Code verweist.

Weitere Informationen zu Versionsnummern und dem Entwickeln von branchenspezifischen Apps finden Sie unter [Erste Schritte mit dem Microsoft Intune App SDK](app-sdk-get-started.md#line-of-business-app-version-numbers).

### <a name="device-and-app-management-integration----677972---"></a>Integration der Verwaltung von Geräten und Apps <!-- 677972 -->   
Da auf die mobile Geräteverwaltung (Mobile Device Management, MDM) und die mobile Anwendungsverwaltung (Mobile Application Management, MAM) nun über das Azure-Portal zugegriffen werden kann, hat Intune damit begonnen, die Vorteile für IT-Administratoren bei der Verwaltung von Anwendungen und Geräten zu integrieren. Diese Änderungen sind darauf ausgerichtet, das Verwalten von Geräten und Apps zu vereinfachen.

Weitere Informationen zu den angekündigten Änderungen an MDM und MAM finden Sie im [Blog des Intune-Supportteams](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Neue Warnungen für Apple-Geräte bei der Registrierung <!-- 1471790 -->
Die Übersichtsseite für die Registrierung zeigt nützliche Warnungen für IT-Administratoren für die Verwaltung von Apple-Geräten an. Warnungen werden auf der Seite „Übersicht“ angezeigt, wenn das Apple-MDM-Push-Zertifikat abläuft oder bereits abgelaufen ist, wenn das Token des Programms zur Geräteregistrierung abläuft oder bereits abgelaufen ist und wenn es nicht zugewiesene Geräte im Programm zur Geräteregistrierung gibt.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>Unterstützung des Ersetzens von Tokens für die App-Konfiguration ohne Geräteregistrierung <!-- 1080364 -->

Sie können Tokens für dynamische Werte in App-Konfigurationen für nicht registrierte Geräte verwenden. Weitere Informationen finden Sie unter [Add app configuration policies for managed apps without device enrollment (Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Apps ohne Geräteregistrierung)](app-configuration-policies-managed-app.md).

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Updates an der Unternehmensportal-App für Windows 10 <!--1299474-->
Die Seite „Einstellungen“ in der Unternehmensportal-App für Windows 10 wurde aktualisiert, um die Einstellungen und beabsichtigten Benutzeraktionen für alle Einstellungen konsistenter zu gestalten. Sie wurde zudem an das Layout anderer Windows-Apps angepasst. Auf der Seite mit den [Neuheiten in der App-Benutzeroberfläche](whats-new-app-ui.md) finden Sie Abbildungen von vor und nach der Aktualisierung.

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>Informieren von Endbenutzern zu den für Windows 10-Geräte sichtbaren Geräteinformationen<!--1337920-->
Wir haben dem Bildschirm „Gerätedetails“ den **Besitzertyp** für die Unternehmensportal-App für Windows 10 hinzugefügt. So können Benutzer direkt auf dieser Seite mehr über die Privatsphäre in der Dokumentation für Intune-Endbenutzer herausfinden. Diese Informationen sind außerdem auf dem Bildschirm **Info** zu finden.

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Feedbackaufforderungen für die Unternehmensportal-App für Android <!--1165249-->
Die Unternehmensportal-App für Android bittet Endbenutzer jetzt um Feedback. Dieses Feedback wird direkt an Microsoft gesendet. So erhalten Endbenutzer die Möglichkeit, die App im öffentlichen Google Play Store zu rezensieren. Feedback ist nicht erforderlich, und die Meldung kann problemlos geschlossen werden, damit Benutzer die App weiterhin verwenden können.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Unterstützen Ihrer Benutzer bei der eigenständigen Problemlösung über die Unternehmensportal-App für Android <!-- 1573324, 1573150, 1558616, 1564878 -->

In der Unternehmensportal-App für Android wurden Anweisungen für Benutzer hinzugefügt, um ihnen Anwendungsfälle zu erläutern und ihnen nach Möglichkeit das eigenständige Lösen dieser Anwendungsfälle zu ermöglichen.
- Die Endbenutzer werden für das Entfernen eines Geräts zum [Azure Active Directory-Portal](https://account.activedirectory.windowsazure.com/r/#/profile) weitergeleitet, wenn sie die maximale Anzahl von Geräten, die hinzugefügt werden dürfen, überschritten haben.
- Endbenutzer erhalten schrittweise Anweisungen zum [Behandeln von Aktivierungsfehlern auf Samsung Knox-Geräten](https://go.microsoft.com/fwlink/?linkid=859718) oder zum [Ausschalten des Stromsparmodus](/intune-user-help/power-saving-mode-android). Wenn keine dieser Lösungen bei der Behebung des Problems hilft, werden wir eine Erklärung zur Verfügung stellen, in der beschrieben wird, [wie Protokolle an Microsoft übermittelt werden können](/intune-user-help/send-logs-to-microsoft-android).

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Neue „Lösungs“-Aktion für Android-Geräte verfügbar <!-- 1583480 -->

In der Unternehmensportal-App für Android wird eine „Lösungs“-Aktion auf der Seite _Geräteeinstellungen aktualisieren_ eingeführt. Wenn der Benutzer diese Option auswählt, wird er direkt zu der Einstellung weitergeleitet, die dafür verantwortlich ist, dass das Gerät nicht kompatibel ist. Derzeit unterstützt die Unternehmensportal-App für Android diese Aktion für die Einstellungen [Gerätekennung](/intune-user-help/set-your-pin-or-password-android), [USB-Debuggen](/intune-user-help/you-need-to-turn-off-usb-debugging-android) und [Unbekannte Quellen](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Statusanzeige für das Gerätesetup im Android-Unternehmensportal <!-- 1565657 -->
Die Unternehmensportal-App für Android zeigt eine Statusanzeige für das Gerätesetup an, wenn ein Benutzer sein Gerät registriert. Der Indikator zeigt neue Statusangaben an, beginnend bei „Ihr Gerät wird eingerichtet...“, dann „Das Gerät wird registriert...“, dann „Die Registrierung Ihres Geräts wird abgeschlossen...“ und schließlich „Die Einrichtung Ihres Geräts wird abgeschlossen...“.

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Unterstützung der zertifikatbasierten Authentifizierung auf dem Unternehmensportal für iOS <!--1029830-->
Es wurde eine Unterstützung für die zertifikatbasierte Authentifizierung in der Unternehmensportal-App für iOS hinzugefügt. Benutzer mit zertifikatbasierter Authentifizierung geben ihren Benutzernamen ein und tippen dann auf den Link „Sign in with a certificate“ (Mit einem Zertifikat anmelden). Die zertifikatbasierte Authentifizierung wird auf den Unternehmensportal-Apps für Android und Windows bereits unterstützt. Weitere Informationen finden Sie auf der Seite [Anmelden bei der Unternehmensportal-App](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Apps, die mit oder ohne Registrierung verfügbar sind, können nun installiert werden, ohne dass Sie zur Registrierung aufgefordert werden. <!-- 1334712 -->

Unternehmens-Apps, die mit oder ohne Registrierung in der Android-Unternehmensportal-App zur Verfügung gestellt wurden, können jetzt installiert werden, ohne dass Sie zur Registrierung aufgefordert werden.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Unterstützung des Windows AutoPilot Deployment-Programms in Microsoft Intune <!-- 747617  -->
Sie können Microsoft Intune jetzt mit dem Windows AutoPilot Deployment-Programm verwenden, um es Ihren Benutzern zu ermöglichen, ihre Unternehmensgeräte bereitzustellen, ohne die IT-Abteilung kontaktieren zu müssen. Sie können die Windows-Willkommensseite anpassen und Benutzer dazu anleiten, ihre Geräte mit Azure AD zu verknüpfen und sich bei Intune zu registrieren. Da Microsoft Intune und Windows AutoPilot zusammenarbeiten, besteht keine Notwendigkeit, Betriebssystemabbilder bereitzustellen, zu aktualisieren und zu verwalten. Weitere Informationen finden Sie unter [Enroll Windows devices using Windows AutoPilot Deployment Program (Registrieren von Windows-Geräten mithilfe des Windows AutoPilot Deployment-Programms)](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="quick-start-for-device-enrollment-----1425655---"></a>Schnellstart für die Geräteregistrierung <!-- 1425655 --> 
Die Schnellstart-Funktion ist jetzt in der **Geräteregistrierung** verfügbar, und es wird eine Tabelle mit Verweisen zur Verfügung gestellt, mit denen Plattformen verwaltet und Registrierungsvorgänge konfiguriert werden. In Kurzbeschreibungen für jedes Element und über verschiedene Links zu Dokumentationen mit ausführlichen Anleitungen werden nützliche Informationen zur Verfügung gestellt, die die ersten Schritte vereinfachen.

### <a name="device-categorization----1427491---"></a>Gerätekategorisierung <!-- 1427491 -->
Über das Plattformdiagramm für registrierte Geräte auf dem Blatt **Geräte > Übersicht** werden Geräte nach Plattform, u.a. Android. iOS, macOS, Windows und Windows Mobile, angeordnet.  Geräte, auf denen andere Betriebssysteme installiert sind, werden der Gruppe „Andere“ zugeordnet.  Dies betrifft auch Geräte, die von Blackberry, NOKIA und anderen hergestellt werden.  

Um zu erfahren, welche Geräte in Ihrem Mandanten betroffen sind, klicken Sie auf **Verwalten > Alle Geräte**, und verwenden Sie anschließend die Funktion **Filtern**, um das Feld für die **Betriebssysteme** einzuschränken.

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium: neuer Mobile Threat Defense-Partner <!-- 954681 -->  
Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen mit bedingtem Zugriff basierend auf Risikobewertungen steuern, die von Zimperium vorgenommen werden, einer Mobile Threat Defense-Lösung, die mit Microsoft Intune zusammenarbeitet.

#### <a name="how-integration-with-intune-works"></a>Funktionsweise der Integration mit Intune
Das Risiko wird basierend auf Telemetriedaten von Geräten bewertet, auf denen Zimperium ausgeführt wird. Sie können Richtlinien für bedingten EMS-Zugriff basierend auf der Zimperium-Risikobewertung konfigurieren, die über Intune-Gerätekompatibilitätsrichtlinien aktiviert werden, und so anhand der erkannten Bedrohungen nicht kompatible Geräte für den Zugriff auf Unternehmensressourcen zulassen oder blockieren.

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Neue Einstellungen für das Windows 10-Geräteeinschränkungsprofil <!--- 978575, 1308849, -->  
Wir fügen neue Einstellungen zum Geräteeinschränkungsprofil für Windows 10 in der Kategorie „Windows Defender SmartScreen“ hinzu.

Details zum Geräteeinschränkungsprofil für Windows 10 finden Sie in den [Einstellungen für die Geräteeinschränkung für Windows 10 und höher]( device-restrictions-windows-10.md).

### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Remote Support für Windows- und Windows Mobile-Geräte <!-- 1070473 -->  
Intune kann jetzt die nicht im Lieferumfang inbegriffene [TeamViewer](https://www.teamviewer.com)-Software verwenden, damit Sie Ihren Benutzern, die Windows- und Windows Mobile-Geräte ausführen, Remote Support anbieten können.

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Überprüfen von Geräten mit Windows Defender <!-- 1280988  1280990   -->
Auf verwalteten Windows 10-Geräten können Sie jetzt mithilfe von Windows Defender Antivirus eine **Schnellüberprüfung** und eine **vollständige Überprüfung** durchführen sowie **Signaturen aktualisieren**. Wählen Sie auf dem Übersichtsblatt des Geräts die Aktion aus, die auf dem Gerät ausgeführt werden soll. Sie werden dann aufgefordert, die Aktion zu bestätigen, bevor der Befehl an das Gerät gesendet wird. 

**Schnellüberprüfung**: Bei einer Schnellüberprüfung werden Speicherorte überprüft, an denen Schadsoftware bei Startvorgängen registriert werden (z.B. Registrierungsschlüssel und bekannte Windows-Startordner). Eine Schnellüberprüfung dauert durchschnittlich fünf Minuten. In Kombination mit der Einstellung **AlwaysOn-Echtzeitschutz**, die Dateien überprüft, wenn ein Benutzer diese öffnet, schließt und in einem Ordner navigiert, kann eine Schnellüberprüfung Schutz vor Schadsoftware bieten, die sich eventuell im System oder Kernel befinden. Die Überprüfungsergebnisse werden Benutzern nach Abschluss der Überprüfung angezeigt. 

**Vollständige Überprüfung**: Eine vollständige Überprüfung kann sich für Geräte als nützlich erweisen, bei denen eine Bedrohung durch eine Schadsoftware erkannt wurde. So kann festgestellt werden, ob inaktive Komponenten vorhanden sind, die eine gründlichere Bereinigung erfordern. Auch bei Bedarf können Überprüfungen ausgeführt werden. Die Ausführung einer vollständigen Überprüfung kann eine Stunde dauern. Die Überprüfungsergebnisse werden Benutzern nach Abschluss der Überprüfung angezeigt. 

**Aktualisieren von Signaturen**: Der Befehl zum Aktualisieren von Signaturen aktualisiert Definitionen von Schadsoftware und Signaturen von Windows Defender Antivirus. Dadurch wird eine effiziente Erkennung von Schadsoftware durch Windows Defender Antivirus sichergestellt. Diese Funktion gilt nur für Windows 10-Geräte bei bestehender Internetkonnektivität. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>Die Aktivierungs- bzw. Deaktivierungsschaltfläche wurde von der Seite „Intune-Zertifizierungsstelle“ im Azure-Portal für Intune entfernt <!-- 1400455 -->
 Dadurch wird ein zusätzlicher Schritt bei der Einrichtung des Zertifikatconnectors auf Intune entfernt. Derzeit laden Sie den Zertifikatconnector herunter und aktivieren ihn anschließend in der Intune-Konsole. Wenn Sie allerdings den Connector in der Intune-Konsole deaktivieren, gibt der Connector weiter Zertifikate aus.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Ab Oktober wird die Aktivierungs- bzw. Deaktivierungsschaltfläche nicht mehr auf der Seite „Intune-Zertifizierungsstelle“ im Azure-Portal angezeigt. Die Connector-Funktionalität ändert sich nicht. Zertifikate werden weiterhin für Geräte bereitgestellt, die in Intune registriert sind. Sie können ebenfalls weiterhin den Zertifikatconnector herunterladen und installieren. Wenn Sie verhindern wollen, dass Zertifikate ausgestellt werden, müssen Sie jetzt den Zertifikatorconnector deinstallieren anstatt ihn nur zu deaktivieren.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Wenn derzeit der Zertifikatconnector deaktiviert ist, müssen Sie ihn deinstallieren.

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Neue Einstellungen für das Windows 10 Team-Geräteeinschränkungsprofil <!--- 1308838 -->
Zu dieser Version wurden viele neue Einstellungen für das Windows 10 Team-Geräteeinschränkungsprofil hinzugefügt, um Sie bei der Steuerung von Surface Hub-Geräten zu unterstützen.

Weitere Informationen zu diesem Profil finden Sie unter [Einstellungen für Windows 10 Team-Geräteeinschränkungen](device-restrictions-windows-10-teams.md).

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Blockieren von Änderungen an Datums- und Uhrzeiteinstellungen von Android-Geräten durch Benutzer <!-- 1333292 -->
Durch [benutzerdefinierte Android-Geräterichtlinien](custom-settings-android.md) können Sie Benutzer von Android-Geräten daran hindern, Datums- und Uhrzeiteinstellungen von Geräten zu ändern.

Hierfür konfigurieren Sie eine benutzerdefinierte Android-Richtlinie mit dem Einstellungs-URI „./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange“, legen diesen auf **TRUE** fest und weisen dann die erforderlichen Gruppen zu.

### <a name="bitlocker-device-configuration----1397398---"></a>BitLocker-Gerätekonfiguration <!-- 1397398 -->
Die Einstellungen unter **Windows-Verschlüsselung > Basiseinstellungen** umfassen die neue Einstellung **Warnung für andere Datenträgerverschlüsselung**, mit der Sie die [Eingabeaufforderung bei Warnungen](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) für andere Datenträgerverschlüsselungen, die eventuell auf dem Gerät des Benutzers verwendet werden, deaktivieren können.  Für die Eingabeaufforderung bei Warnungen ist die Zustimmung des Endbenutzers erforderlich, bevor BitLocker auf dem Gerät eingerichtet wird. Zudem wird das BitLocker-Setup erst durchgeführt, wenn die Eingabeaufforderung vom Endbenutzer bestätigt wurde.  Die neue Einstellung deaktiviert die Warnung für Endbenutzer.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>Volume Purchase Program für Geschäftsanwendungen werden jetzt mit Ihrem Intune-Mandanten synchronisiert <!-- 800882 -->  
Drittentwickler können, wie in iTunes Connect angegeben, privat ihre Apps an autorisierte Mitglieder von VPP für Unternehmen verteilen. Diese Mitglieder des VPP für Unternehmen können sich im VPP-App Store registrieren und ihre Apps dort erwerben.

Mit dieser Version beginnt die VPP für Geschäftsanwendungen, die der Benutzer erworben hat, jetzt mit der Synchronisierung mit Ihren Intune-Mandanten.

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Auswählen des regionalen Apple App Store zum Synchronisieren von VPP-Apps <!-- 1332311 -->  
Beim Hochladen Ihres VPP-Tokens können Sie den regionalen VPP Store (Volume Purchase Program) konfigurieren. Intune synchronisiert VPP-Apps für alle Gebietsschemas aus dem jeweiligen regionalen VPP Store.

> [!NOTE]  
> Derzeit synchronisiert Intune nur VPP-Apps aus dem regionalen VPP Store mit dem Intune-Gebietsschema, in dem der Intune-Mandant erstellt wurde.


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Blockieren der Funktion zum Kopieren und Einfügen zwischen Arbeitsprofilen und persönlichen Profilen in Android for Work <!-- 1098994 -->
Mit dieser Version können Sie das Arbeitsprofil für Android for Work konfigurieren, um die Funktion zum Kopieren und Einfügen zwischen Arbeits- und persönlichen Apps zu blockieren. Sie finden diese neue Einstellung im Profil **Geräteeinschränkungen** für die **Android for Work**-Plattform unter **Arbeitsprofileinstellungen**.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Erstellen von auf bestimmten regionalen Apple App Stores beschränkten iOS-Apps <!-- 1281692 -->
Bei der Erstellung einer verwalteten Apple App Store-App haben Sie die Möglichkeit, das Gebietsschema anzugeben.

> [!Note]  
> Derzeit können nur verwaltete Apple App Store-Apps erstellt werden, die im Store für die USA zur Verfügung gestellt werden.

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Aktualisieren von für Benutzer und Geräte lizenzierten iOS-VPP-Apps <!-- 1305564 -->  
Durch Konfigurieren des iOS-VPP-Tokens können Sie alle Apps aktualisieren, die für dieses Token über den Intune-Dienst erworben wurden. Intune erkennt Updates für VPP-Apps in App Store und überträgt diese beim Geräte-Check-In automatisch mithilfe von Push auf das Gerät.

Informationen über die einzelnen Schritte, wie Sie VPP-Token festlegen und automatische Updates aktivieren, finden Sie unter [Verwalten von iOS-Apps, die über ein Volumenprogramm mit Microsoft Intune erworben wurden] (/intune/vpp-apps-ios).


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Hinzufügen der Entitätssammlung von Benutzergerätezuordnungen zum Intune Data Warehouse-Datenmodell <!-- 1187917 -->
Mithilfe von Informationen über Benutzergerätezuordnungen können Sie Berichte und Datenvisualisierungen erstellen, die Entitätssammlungen von Benutzern und Geräten zuordnet. Auf das Datenmodell kann über die Power BI-Datei (PBIX) zugegriffen werden, die über die Data Warehouse-Seite von Intune, den OData-Endpunkt oder durch die Entwicklung eines benutzerdefinierten Clients abgerufen wird.

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Überprüfen der Richtlinienkonformität für Windows 10-Updateringe <!-- 1067886 -->
Unter „Softwareupdates > Bereitstellungsstatus pro Updatering“ können Sie einen Richtlinienbericht für Ihre Windows 10-Updateringe einsehen. Der Richtlinienbericht gibt den Bereitstellungsstatus für die Updateringe an, die Sie konfiguriert haben. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Neuer Bericht, der iOS-Geräte mit älteren iOS-Versionen auflistet <!-- 1352223 -->
Der Bericht **Out-of-date iOS Devices (Veraltete iOS-Geräte)** ist im Arbeitsbereich **Softwareupdates** verfügbar. Im Report sehen Sie eine Liste überwachter iOS-Geräte, die unter eine iOS-Updaterichtlinie fallen und mehrere verfügbare Updates besitzen. Für jedes Gerät können Sie einen Status anzeigen, warum das Gerät nicht automatisch aktualisiert wurde. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Anzeigen der Zuweisungen von App-Schutzrichtlinien für die Problembehandlung <!--  1475003 -->
In der kommenden Version wird auf dem Blatt „Problembehandlung“ die Option **App-Schutzrichtlinie** zur Dropdown-Liste **Zuweisungen** hinzugefügt. Nun können Sie App-Schutzrichtlinien auswählen, um die für ausgewählte Benutzer zugewiesenen App-Schutzrichtlinien anzuzeigen.



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Verbesserungen des Workflows für die Geräteinstallation im Unternehmensportal <!--1490692-->
Der Workflow für die Geräteinstallation in der Unternehmensportal-App unter Android wurde verbessert. Die Sprache ist nun benutzerfreundlicher und spezifisch für Ihr Unternehmen. Zudem haben wir wo es möglich war Bildschirme vereint. Sie können diese auf der Seite [Was gibt es Neues auf der App-Benutzeroberfläche](whats-new-app-ui.md#week-of-october-2-2017) anzeigen.

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Verbesserter Leitfaden bezüglich der Anforderung des Zugriffs auf Kontakte auf Android-Geräten <!--1484985-->

Die Unternehmensportal-App für Android erfordert oft, dass Benutzer die Kontaktberechtigungen akzeptieren. Wenn ein Benutzer diesen Zugriff verweigert, wird ihm eine In-App-Benachrichtigung angezeigt, die ihn anweist, diesen für den bedingten Zugriff zu gewähren. 

### <a name="secure-startup-remediation-for-android---1490712--"></a>Secure Startup-Wartung für Android <!--1490712-->

Benutzer von Android-Geräten können den Grund der Nichtkompatibilität in der Unternehmensportal-App wählen. Wenn möglich werden sie direkt an den korrekten Ort in der Einstellungs-App geleitet, um das Problem zu beheben. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Zusätzliche Pushbenachrichtigungen für Benutzer in der Unternehmensportal-App für Android Oreo <!--1475932-->

Benutzern werden zusätzliche Benachrichtigungen angezeigt, die ihnen mitteilen, wann die Unternehmensportal-App für Android Oreo Hintergrundaufgaben durchführt, z.B. Abrufen von Richtlinien aus dem Intune-Dienst. So sind Endbenutzer besser darüber informiert, wann die Unternehmensportal-App administrative Aufgaben auf ihren Geräten ausführt. Dies ist Teil der gesamten [Optimierung der Unternehmensportal-Benutzeroberfläche](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) für die Unternehmensportal-App für Android Oreo. 

Es gibt weitere Optimierungen für neue Benutzeroberflächenelemente, die in Android Oreo aktiviert sind.  Benutzern werden zusätzliche Benachrichtigungen angezeigt, die angeben, wann das Unternehmensportal Hintergrundaufgaben durchführt, z.B. Abrufen von Richtlinien aus dem Intune-Dienst.  Dadurch wird die Transparenz für Benutzer erhöht, für den Fall, dass das Unternehmensportal administrative Aufgaben auf dem Gerät ausführt.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Neue Verhalten für die Unternehmensportal-App für Android mit Arbeitsprofilen<!-- 1485783 -->

Wenn Sie ein Android for Work-Gerät mit einem Arbeitsprofil registrieren, werden Verwaltungsaufgaben auf dem Gerät von der Unternehmensportal-App im Arbeitsprofil ausgeführt. 

Wenn Sie eine MAM-fähige App im persönlichen Profil verwenden, kann die Unternehmensportal-App für Android nicht mehr verwendet werden. Um die Benutzererfahrung bezüglich des Arbeitsprofils zu verbessern, blendet Intune die persönliche Unternehmensportal-App nach erfolgreicher Registrierung eines Arbeitsprofils automatisch aus.

Die Unternehmensportal-App für Android kann jederzeit im persönlichen Profil aktiviert werden, indem Sie zum [Unternehmensportal im Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) navigieren und auf **Aktivieren** tippen.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Aktivieren des Aufrechterhaltungsmodus für das Unternehmensportal für Windows 8.1 und Windows Phone 8.1 <!--1428681-->

Ab Oktober 2017 wird der Aufrechterhaltungsmodus für Unternehmensportal-Apps für Windows 8.1 und Windows Phone 8.1 aktiviert. Dies bedeutet, dass die Apps und vorhandenen Szenarien wie Registrierung und Konformität weiterhin für diese Plattformen unterstützt werden. Diese Apps werden weiterhin über vorhandene Veröffentlichungskanäle wie dem Microsoft Store zum Download zur Verfügung gestellt. 

Sobald sich diese Apps im Aufrechterhaltungsmodus befinden, werden nur kritische Sicherheitsupdates empfangen. Es werden keine weiteren Updates oder Funktionen für diese Apps veröffentlicht. Um von neuen Funktionen profitieren zu können, wird empfohlen, Geräte auf Windows 10 und Windows 10 Mobile zu aktualisieren. 


### <a name="block-unsupported-samsung-knox-device-enrollment-----1490695---"></a>Blockieren der nicht unterstützten Samsung KNOX-Geräteregistrierung <!-- 1490695 -->

Die Unternehmensportal-App versucht, ausschließlich unterstützte Samsung KNOX-Geräte zu registrieren. Die Geräteregistrierung wird nur ausgeführt, wenn das Gerät in der [Liste der von Samsung veröffentlichten Geräte](https://www.samsungknox.com/knox-supported-devices/knox-workspace) erscheint, um Aktivierungsfehler von KNOX zu vermeiden, die die MDM-Registrierung verhindern. Samsung-Geräte können über Modellnummern verfügen, die KNOX unterstützen, während andere dies nicht tun. Überprüfen Sie vor dem Kauf und der Bereitstellung daher mithilfe des Wiederverkäufers Ihrer Geräte, ob diese mit KNOX kompatibel sind. Die vollständige Liste verifizierter Geräte finden Sie in den [Einstellungen für Android- und Samsung KNOX Standard-Richtlinien](/intune/supported-devices-browsers.md#intune-supported-web-browsers).

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>Ablauf des Supports für Android 4.3 und niedriger <!-- 1171126, 1326920 -->
Verwaltete Apps und die Unternehmensportal-App für Android benötigen Android 4.4 oder höher, um auf Unternehmensressourcen zugreifen zu können. Ab Dezember werden alle registrierten Geräte deaktiviert und können dann nicht mehr auf Unternehmensressourcen zugreifen. Bei Verwendung von App-Schutzrichtlinien ohne mobile Geräteverwaltung erhalten Apps keine Updates mehr, und die Qualität ihrer Benutzung wird mit der Zeit abnehmen.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>Informieren von Endbenutzern, welche Geräteinformation auf registrierten Geräten angezeigt werden kann <!--1165314-->
Wir fügen dem Bildschirm „Gerätedetails“ den **Besitzertyp** auf allen Unternehmensportal-Apps hinzu. So können Benutzer direkt im Artikel [Welche Informationen erhält mein Unternehmen, wenn ich mein Gerät registriere?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) mehr über die Privatsphäre herausfinden. Dies wird in allen Unternehmensportal-Apps in Zukunft eingeführt. Für iOS haben wir dies im [September](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017) angekündigt.

## <a name="september-2017"></a>September 2017

### <a name="intune-supports-ios-11---1428975--"></a>Intune unterstützt iOS 11 <!--1428975-->
Intune unterstützt iOS 11. Dies wurde zuvor auf dem [Blog zum Intune-Support](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/) angekündigt.

### <a name="end-of-support-for-ios-80----1164477---"></a>Ablauf des Supports für iOS 8.0 <!-- 1164477 -->
Verwaltete Apps und die Unternehmensportal-App für iOS benötigen iOS 9.0 und höher, um auf Unternehmensressourcen zugreifen zu können. Geräte, die nicht bis September aktualisiert werden, können nicht mehr auf das Unternehmensportal oder diese Apps zugreifen. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Hinzufügen der Aktualisierungsaktion zur Unternehmensportal-App für Windows 10 <!--1132468-->
In der Unternehmensportal-App für Windows 10 können Benutzer die Daten nun aktualisieren, indem Sie sie aktualisieren (ziehen) oder indem Sie auf dem Desktop auf F5 drücken.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Informieren von Endbenutzern, welche Geräteinformation für iOS angezeigt werden kann <!--739894-->

Wir haben dem Bildschirm „Gerätedetails“ den **Besitzertyp** auf der Unternehmensportal-App für iOS hinzugefügt. So können Benutzer weitere Informationen zum Datenschutz direkt von dieser Seite aus der Intune-Endbenutzerdokumentation erhalten. Sie finden diese Informationen ebenso auf dem Bildschirm „Info“.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Zugriff auf die Unternehmensportal-App für Android durch Endbenutzer ohne Registrierung <!---1169910--->

Endbenutzer müssen ihr Gerät bald nicht mehr registrieren, um auf die Unternehmensportal-App für Android zugreifen zu können. Endbenutzer innerhalb von Organisationen, die App-Schutzrichtlinien verwenden, werden beim Öffnen der Unternehmensportal-App nicht mehr aufgefordert, ihr Gerät zu registrieren. Zudem können Endbenutzer Apps vom Unternehmensportal installieren, ohne ihr Gerät zu registrieren. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Vereinfachung der Formulierung für die Unternehmensportal-App für Android <!---1396349--->  

Der Registrierungsvorgang für die Unternehmensportal-App für Android wurde durch einen neuen Text vereinfacht, um Endbenutzern eine einfachere Registrierung zu bieten. Wenn Sie eine benutzerdefinierte Registrierungsdokumentation verwenden, aktualisieren Sie sie gemäß der neuen Bildschirme. Sie können Beispielabbildungen auf unserer Seite [Aktualisierungen für die Benutzeroberfläche für Endbenutzer-Apps in Intune](whats-new-app-ui.md#week-of-september-11-2017) sehen.

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Hinzufügen der Windows Information Protection-Zulassungsrichtlinie zur Windows 10-Unternehmensportal-App <!-- 677129 -->

Die Unternehmensportal-App unter Windows 10 wurde aktualisiert, um Unterstützung für Windows Information Protection (WIP) bereitzustellen. Die App kann der WIP-Zulassungsrichtlinie hinzugefügt werden. Aufgrund dieser Änderung muss die App nicht mehr zur Liste **Ausnahme** hinzugefügt werden.


## <a name="august-2017"></a>August 2017

### <a name="improvements-to-device-overview----1404453---"></a>Verbesserungen an der Geräteübersicht <!-- 1404453 -->  
Die Verbesserungen an der Geräteübersicht zeigen nun registrierte Geräte an, jedoch keine Geräte, die von Exchange ActiveSync verwaltet werden. Exchange ActiveSync-Geräte verfügen nicht über die gleichen Verwaltungsoptionen wie registrierte Geräte. Um die Anzahl der registrierten Geräte und die Anzahl der registrierten Geräte nach Plattform in Intune im Azure-Portal anzuzeigen, navigieren Sie zu **Geräte** > **Übersicht**.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Verbesserungen am von Intune erfassten Gerätebestand
<!-- 961134, 1104426, 1281327, 1333543 -->
In diesem Release haben wir die folgenden Verbesserungen an den Bestandsinformationen vorgenommen, die von den von Ihnen verwalteten Geräten gesammelt werden:
 
-   Bei Android-Geräten können Sie nun eine Spalte zum Gerätebestand hinzufügen, die die neueste Patchebene für jedes Gerät anzeigt. Fügen Sie die Spalte **Sicherheitspatchebene** zu Ihrer Geräteliste hinzu, um dies anzuzeigen.
-   Wenn Sie in der Geräteansicht filtern, können Sie die Geräte nun nach ihrem Registrierungsdatum filtern. Beispielsweise könnten Sie nur Geräte anzeigen lassen, die nach einem von Ihnen angegebenen Datum registriert wurden.
-   Wir haben Verbesserungen an dem Filter vorgenommen, der vom Element **Last Check-in Date** (Letztes Eincheckdatum) verwendet wird.
-   In der Geräteliste können Sie jetzt die Telefonnummern von unternehmenseigenen Geräten anzeigen.
Darüber hinaus können Sie den Filterbereich verwenden, um Geräte nach Telefonnummer zu suchen.
 
Weitere Informationen zum Gerätebestand finden Sie unter [So zeigen Sie den Intune-Gerätebestand an](device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Unterstützung des bedingten Zugriffs für macOS-Geräte 
<!-- 720172 -->
Sie können nun eine Richtlinie für bedingten Zugriff festlegen, durch die Mac-Geräte bei Intune registriert werden und den Gerätekompatibilitätsrichtlinien entsprechen müssen. Benutzer können z.B. die Intune-Unternehmensportal-App für macOS herunterladen und ihre Mac-Geräte bei Intune registrieren. Intune bewertet, ob das Mac-Gerät mit Anforderungen wie PIN, Verschlüsselung, Betriebssystemversion und Systemintegrität kompatibel ist.

- Erfahren Sie mehr über die [conditional access support for macOS devices (Unterstützung des bedingten Zugriffs für macOS-Geräte)](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>Die Unternehmensportal-App für macOS befindet sich in der öffentlichen Vorschauversion <!---1484796--->.
Die Unternehmensportal-App für macOS ist nun als Teil der öffentlichen Vorschauversion für bedingten Zugriff in Enterprise Mobility + Security verfügbar. Diese Version unterstützt macOS 10.11 und höher. Laden Sie sie unter [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal) herunter. 


### <a name="new-device-restriction-settings-for-windows-10"></a>Neue Einstellungen für Geräteeinschränkungen für Windows 10    
<!--1063965, 1308850  -->
In diesem Release haben wir neue Einstellungen für das [Windows 10-Geräteeinschränkungsprofil](/intune/device-restrictions-windows-10) in folgenden Kategorien hinzugefügt:

-   Windows Defender SmartScreen
-   App Store

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Updates für die Einstellungen des Windows 10 Endpoint Protection-Geräteprofils für BitLocker
<!--1459533 -->    
In diesem Release haben wir die folgenden Verbesserungen daran vorgenommen, wie die BitLocker-Einstellungen in einem Windows 10 Endpoint Protection-Geräteprofil funktionieren:
 
Wenn Sie unter **BitLocker-Einstellungen für Betriebssystemlaufwerk** für die Einstellung **BitLocker für nicht kompatiblen TPM-Chip** **Blockieren** auswählen, hat dies bisher dazu geführt, dass BitLocker tatsächlich zugelassen ist. Wir haben dies nun behoben, sodass BitLocker blockiert wird, wenn dies ausgewählt wird.
Unter **BitLocker-Einstellungen für Betriebssystemlaufwerk** können Sie nun für die Einstellung **Agent für zertifikatbasierte Datenwiederherstellung** explizit den Agent für zertifikatbasierte Datenwiederherstellung blockieren. Standardmäßig ist der Agent jedoch zulässig.
Unter **BitLocker-Einstellungen für Festplattenlaufwerk** können Sie nun für die Einstellung **Datenwiederherstellungs-Agent** explizit den Datenwiederherstellungs-Agent blockieren.
Weitere Informationen finden Sie unter [Endpoint protection settings for Windows 10 and later (Endpoint Protection-Einstellungen für Windows 10 und höher)](endpoint-protection-windows-10.md).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Neue Anmeldeerfahrung für Benutzer des Android-Unternehmensportals sowie für Benutzer der App-Schutz-Richtlinien <!-- 621669 -->
Endbenutzer können jetzt in der Android-Unternehmensportal-App nach Apps suchen, Geräte verwalten und IT-Kontaktinformationen anzeigen, ohne ihre Android-Geräte registrieren zu müssen. Wenn ein Benutzer, der bereits eine App verwendet, die durch Richtlinien zum Intune-App-Schutz geschützt ist, zusätzlich die Android-Unternehmensportal-App startet, dann enthält er zukünftig keine Aufforderung mehr, das Gerät zu registrieren.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Neue Einstellung in der Android-Unternehmensportal-App für die Akkuoptimierung <!--1405990-->
Auf der Seite **Einstellungen** in der Unternehmensportal-App für Android ist eine neue Einstellung verfügbar, mit der Benutzer die Akkuoptimierung einfach für Unternehmensportal- und Microsoft Authenticator-Apps ausschalten können. Der in der Einstellung dargestellte Name der App hängt davon ab, welche App das Geschäftskonto verwaltet. Benutzern wird empfohlen, die Akkuoptimierung zugunsten besserer Leistung von Work-Apps auszuschalten, die E-Mails und Daten synchronisieren. 

### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>Unterstützung mehrerer Identitäten für OneNote für iOS <!-- 1234281 -->
Benutzer können jetzt verschiedene Konten (geschäftlich und privat) mit Microsoft OneNote für iOS verwenden. App-Schutzrichtlinien können auf Unternehmensdaten in Arbeitsnotizbüchern angewendet werden, ohne dass persönliche Notizbücher betroffen sind. Beispielsweise kann eine Richtlinie einem Benutzer erlauben, Informationen in Arbeitsnotizbüchern zu suchen, verhindert jedoch, dass der Benutzer Unternehmensdaten aus dem Arbeitsnotizbuch in ein persönliches Notizbuch kopiert.
 
- Erfahren Sie mehr über die Apps, die [App-Schutz und mehrere Identitäten](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) mit Intune unterstützen.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Neue Einstellungen zum Zulassen und Blockieren von Apps auf Samsung KNOX Standard-Geräten
<!-- 1305423 822899-->  
In dieser Version werden neue [Einstellungen für Geräteeinschränkungen](device-restrictions-android.md) hinzugefügt, mit denen Sie die folgenden App-Listen angeben können:
 
- Apps, die Benutzer installieren dürfen
- Apps, für deren Ausführung Benutzer blockiert sind
- Apps, die vor dem Benutzer auf dem Gerät verborgen werden
 
Sie können die Apps mithilfe der URL, des Paketnamens oder der Liste der Apps, die Sie verwalten, angeben.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Neue App-basierte Benutzeroberflächenverknüpfung für Azure AD-Richtlinien für den bedingten Zugriff in Intune
<!-- 1016201 -->
IT-Administratoren können nun App-basierte Richtlinien für den bedingten Zugriff über die neue Benutzeroberfläche für Richtlinien für den bedingten Zugriff in der Azure AD-Workload festlegen. Der App-basierte bedingte Zugriff, der sich im Bereich Intune-App-Schutz im Azure-Portal befindet, bleibt dort vorläufig und wird parallel erzwungen. Es ist auch ein praktischer Link zur neuen Benutzeroberfläche der Richtlinie für den bedingten Zugriff im Intune-Workload vorhanden.

- Erfahren Sie mehr über den [app-based conditional access on Azure AD (App-basierten bedingten Zugriff für Azure AD)](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).



## <a name="july-2017"></a>Juli 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Einschränken von Registrierungseinschränkungen für Android- und iOS-Geräte nach Betriebssystemversion <!--- 1333256,  1245463 --->
Intune unterstützt jetzt die Einschränkung der iOS- und Android-Registrierung nach der Versionsnummer des Betriebssystems. Der IT-Administrator kann jetzt unter **Gerätetypeinschränkung** eine Plattformkonfiguration festlegen, um die Registrierung zwischen einem minimalen und maximalen Betriebssystemwert festzulegen. Android-Betriebssystemversionen müssen als „Major.Minor.Build.Rev“ angegeben werden, wobei „Minor“, „Build“ und „Rev“ optional sind. iOS-Versionen müssen als „Major.Minor.Build“ angegeben werden, wobei „Minor“ und „Build“ optional sind. Weitere Informationen zu [Geräteregistrierungseinschränkungen](enrollment-restrictions-set.md).

>[!NOTE]
>Schränkt nicht die Registrierung mit Apple-Registrierungsprogrammen oder Apple Configurator ein.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Einschränken von Geräteregistrierungen persönlicher Geräte mit Android, iOS und macOS <!--- 1333272,  1333275, 1245709 --->
Intune kann die Registrierung persönlicher Geräte einschränken, indem es IMEI-Nummern von Unternehmensgeräten auf eine Positivliste setzt. Diese Funktion von Intune wurde nun auf iOS, Android und macOS mit Geräteseriennummern erweitert. Durch Hochladen der Seriennummern in Intune können Sie Geräte vorab als unternehmenseigen deklarieren. Persönliche Geräte können mit Registrierungseinschränkungen blockiert werden, indem die Registrierung nur für unternehmenseigene Geräte zugelassen wird. Weitere Informationen zu [Geräteregistrierungseinschränkungen](enrollment-restrictions-set.md).

Zum Importieren von Seriennummern gehen Sie zu **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten**, und klicken Sie auf **Hinzufügen**. Laden Sie dann eine CSV-Datei hoch (ohne Kopfzeile, zwei Spalten für Seriennummer und Details wie IMEI-Nummern).  Zur Einschränkung von privaten Geräten gehen Sie zu **Geräteregistrierung** > **Registrierungseinschränkungen**. Klicken Sie unter **Gerätetypbeschränkungen** auf die Option **Standard** und anschließend auf **Plattformkonfigurationen**. Sie können private Geräte für iOS, Android und macOS **Zulassen** oder **Blockieren**. 


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Neue Geräteaktion zur erzwungenen Synchronisierung von Geräten mit Intune <!-- 711369 -->
In dieser Version haben wir eine neue Geräteaktion hinzugefügt, die das ausgewählte Gerät zwingt, sofort bei Intune einzuchecken. Checkt ein Gerät ein, empfängt es sofort alle ihm zugewiesenen ausstehenden Aktionen oder Richtlinien.  Dadurch können Sie sofort zugewiesene Richtlinien überprüfen und Probleme beheben, ohne den nächsten geplanten Check-In abwarten zu müssen.
Mehr Informationen finden Sie unter [Synchronisieren von Geräten](device-sync.md).

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Erzwingen der automatischen Installation des neuesten Softwareupdates bei überwachten iOS-Geräten <!-- 777100 -->
Eine neue Richtlinie aus dem Softwareupdate-Arbeitsbereich ist verfügbar, die für überwachte iOS-Geräte die automatische Installation des neuesten Softwareupdates erzwingt. Weitere Informationen finden Sie unter [Konfigurieren von iOS-Aktualisierungsrichtlinien](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Check Point SandBlast Mobile: neuer Mobile Threat Defense-Partner <!-- 954651, 1172027 -->
Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen mit bedingtem Zugriff basierend auf Risikobewertungen steuern, die von Check Point SandBlast Mobile vorgenommen werden, einer Mobile Threat Defense-Lösung, die in Microsoft Intune integriert ist.

#### <a name="how-integration-with-intune-works"></a>Funktionsweise der Integration mit Intune
Das Risiko wird basierend auf Telemetriedaten von Geräten bewertet, auf denen Check Point SandBlast Mobile ausgeführt wird. Sie können Richtlinien für bedingten EMS-Zugriff basierend auf Risikobewertungen von Check Point SandBlast Mobile konfigurieren, die mithilfe von Intune-Gerätekompatibilitätsrichtlinien aktiviert werden. Sie können den Zugriff nicht kompatibler Geräte auf Unternehmensressourcen anhand der erkannten Bedrohungen zulassen oder blockieren.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>Bereitstellen einer im Microsoft Store für Unternehmen verfügbaren App <!-- 748101 -->
Ab dieser Version können Administratoren Apps zuweisen, sobald sie im Microsoft Store für Unternehmen verfügbar werden. Wenn eine App als verfügbar markiert wird, können Benutzer diese aus der Unternehmensportal-App oder von der Website installieren, ohne vom Microsoft Store eingeschränkt zu werden.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>Updates für die Benutzeroberfläche der Unternehmensportal-Website<!--1313244 part 1-->
Wir haben mehre Updates für die Benutzeroberfläche der [Unternehmensportal-Website](https://portal.manage.microsoft.com) durchgeführt, um die Endbenutzererfahrung zu verbessern.

- __Verbesserungen der App-Kacheln__: App-Symbole werden nun mit einem automatisch generierten Hintergrund basierend auf der dominanten Farbe des Symbols angezeigt (falls diese erkannt wird). Wenn möglich, ersetzt dieser Hintergrund die graue Trennlinie, die zuvor auf App-Kacheln sichtbar war.

    Die Unternehmensportalwebsite zeigt in einer kommenden Version wenn möglich große Symbole an. Es wird empfohlen, dass Administratoren Apps mithilfe von hochauflösenden Symbolen mit einer Mindestgröße von 120x120 Pixeln bereitstellen. 

- __Änderungen in der Navigation__: Elemente auf der Navigationsleiste wurden in das Hamburger-Menü oben links verschoben. Die Seite „Kategorien“ wurde entfernt. Benutzer können nun Inhalt beim Durchsuchen nach Kategorie filtern.

- __Updates an empfohlenen Apps__: Wir haben der Website eine dedizierte Seite hinzugefügt, auf der Benutzer Apps durchsuchen können, die Sie präsentieren, und haben einige Optimierungen auf der Benutzeroberfläche für den Abschnitt „Featured“ (Empfohlen) auf der Homepage vorgenommen.

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>Unterstützung für iBooks auf der Unternehmensportalwebsite <!--1231841-->
Wir haben eine dedizierte Seite im Unternehmensportal hinzugefügt, über die Benutzer iBooks durchsuchen und herunterladen können. 


### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>Zusätzliche Informationen für die Problembehandlung im Helpdesk <!---  Applies to 1263399, 1326964, 1341642 --->
In Intune wurde die Anzeige für die Problembehandlung und die Informationen aktualisiert, die dort für Administratoren und Helpdesk-Personal bereitstellt werden. Sie finden dort nun eine **Zuweisungstabelle**, die alle Zuweisungen für den Benutzer auf Grundlage der Gruppenmitgliedschaft zusammenfasst. Diese Liste enthält:
- Mobile Apps
- Konformitätsrichtlinien
- Konfigurationsprofile
 
Darüber hinaus enthält die Tabelle **Geräte** jetzt die Spalten **Azure AD-Verknüpfungstyp** und **Azure AD-konform**. Weitere Informationen finden Sie unter [Verwenden des Problembehandlungsportals, um Benutzern zu helfen](help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Intune Data Warehouse (Öffentliche Vorschau)
Intune Data Warehouse prüft täglich die Daten, um eine Verlaufsansicht Ihres Mandanten bereitzustellen. Sie können mit einer Power BI-Datei (PBIX), einem OData-Link, der mit vielen Analysetools kompatibel ist, oder durch die Interaktion mit der REST-API auf die Daten zugreifen. Weitere Informationen finden Sie unter [Verwenden des Data Warehouse von Intune](reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Verfügbarkeit heller und dunkler Modi für die Unternehmensportal-App für Windows 10 <!---676547--->
Endbenutzer können den Farbmodus für die Unternehmensportal-App für Windows 10 anpassen. Benutzer können die Änderung im Abschnitt „Einstellungen“ der Unternehmensportal-App durchführen. Die Änderung wird nach einem Neustart der App vorgenommen. Bei Windows 10 Version 1607 und höher ist der App-Modus standardmäßig Teil der Systemeinstellung. Für Windows 10 Version 1511 und früher ist der App-Modus standardmäßig auf „Hell“ festgelegt.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Kennzeichnen ihrer Gerätegruppe in der Unternehmensportal-App für Windows 10 durch Endbenutzer <!---807046-->
Endbenutzer können nun wählen, zu welcher Gruppe ihr Gerät gehört, indem sie es direkt innerhalb der Unternehmensportal-App für Windows 10 kennzeichnen.



## <a name="june-2017"></a>Juni 2017

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Neuer rollenbasierter Administratorenzugriff für Intune-Administratoren <!-- 1099990 -->  
Eine neue Administratorrolle für den bedingten Zugriff wird hinzugefügt, um Azure AD-Richtlinien für den bedingten Zugriff zu erstellen, zu ändern und zu löschen. Vorher besaßen nur globale Administratoren und Sicherheitsadministratoren diese Berechtigung. Diese Rollenberechtigung kann Intune-Administratoren erteilt werden, damit sie Zugriff auf Richtlinien für den bedingten Zugriff haben.


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>Markieren von unternehmenseigenen Geräten mit Seriennummer <!-- 1215070 -->  
Intune unterstützt nun das Hochladen von iOS-, macOS- und Android-Seriennummern als IDs für unternehmenseigene Geräte. Sie können anhand von Seriennummern derzeit keine persönlichen Geräte für die Registrierung blockieren, da Seriennummern bei der Registrierung nicht überprüft werden. Die Funktion zum Blockieren persönlicher Geräte durch Seriennummer wird in Kürze veröffentlicht.


### <a name="new-remote-actions-for-ios-devices----854689---"></a>Neue Remoteaktionen für iOS-Geräte <!-- 854689 -->
In dieser Version haben wir zwei neue remote Geräteaktionen für freigegebene iPad-Geräte hinzugefügt, die die Apple Classroom-App verwalten:

-   [Aktuellen Benutzer abmelden](device-logout-user.md): Meldet den aktuellen Benutzer eines von Ihnen ausgewählten iOS-Geräts aus.
-   [Benutzer entfernen](device-remove-user.md): Löscht einen von Ihnen ausgewählten Benutzer aus dem lokalen Cache eines iOS-Geräts.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>Unterstützung für gemeinsam genutzte iPads mit der Classroom-App für iOS <!-- 1044681 -->
In diesem Release haben wir die Unterstützung für die Verwaltung der Classroom-App (iOS) erweitert, um Schüler und Studenten einzubeziehen, die sich mithilfe ihrer verwalteten Apple-ID auf gemeinsam genutzten iPads anmelden.


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Änderungen an Integrierten Intune-Apps <!-- 1332306 -->
Zuvor enthielt Intune eine Reihe integrierter Apps, die Sie rasch zuweisen konnten. Auf Grundlage Ihrer Feedbacks haben wir diese Liste entfernt, und es werden keine integrierten Apps mehr angezeigt.
Wenn Sie jedoch schon integrierte Apps zugewiesen haben, werden sie noch immer auf der App-Liste angezeigt. Sie können diese Apps weiter nach Bedarf zuweisen.
Es ist geplant, in einer späteren Version eine einfachere Methode hinzuzufügen, um integrierte Apps über das Azure-Portal auszuwählen und zuzuweisen.

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Einfachere Installation von Office 365-Apps <!--- 1121362 --->
Der neue App-Typ von **Office 365 ProPlus** erleichtert Ihnen die Zuweisung von Office 365 ProPlus-2016-Apps zu von Ihnen verwalteten Geräten, die mit der neuesten Version von Windows 10 ausgeführt werden. Darüber hinaus erhalten Sie die Möglichkeit, Microsoft Project und Microsoft Visio zu installieren, wenn Sie über die entsprechenden Lizenzen verfügen. Die gewünschten Apps werden gebündelt und in der Intune-Konsole als einzelne App in der App-Liste angezeigt.
Weitere Informationen finden Sie unter [How to add Office 365 apps for Windows 10 (Hinzufügen von Office 365-Apps für Windows 10)](apps-add-office365.md).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>Unterstützung für Offline-Apps aus dem Microsoft Store für Unternehmen <!--- 777044 --->
Offline-Apps, die Sie über den Microsoft Store für Unternehmen erworben haben, werden nun mit dem Azure-Portal synchronisiert. Sie können diese Apps dann für Geräte- oder Benutzergruppen bereitstellen. Offline-Apps werden durch Intune und nicht durch den Store installiert.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>Microsoft Teams ist jetzt Teil der App-basierten CA-Liste der genehmigten Apps <!-- 1257019 -->
Die Microsoft Teams-App für iOS und Android ist nun Bestandteil der genehmigten Apps für Richtlinien für den app-basierten bedingten Zugriff für Exchange und SharePoint Online. Im Azure-Portal kann die App über das Blatt „Intune-App-Schutz“ für alle Mandanten konfiguriert werden, die derzeit auf den app-basierten bedingten Zugriff zurückgreifen.

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Verwaltete Browser- und App-Proxy-Integration <!-- 1287310 -->
Der Intune Managed Browser kann nun mit dem Azure AD-Anwendungsproxydienst integriert werden, damit Benutzer auf interne Websites zugreifen können, auch wenn Sie remote arbeiten. Benutzer des Browsers geben einfach wie gewohnt die Website-URL ein, und der Managed Browser leitet die Anfrage über das Anwendungsproxy-Webgateway weiter. Weitere Informationen finden Sie unter [Verwalten des Internetzugriffs mittels Richtlinien für verwaltete Browser](app-configuration-managed-browser.md).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Neue App-Konfigurationseinstellungen für Intune Managed Browser <!-- 682951 -->
In dieser Version haben wir weitere Konfigurationen für die Intune Managed Browser-App für iOS und Android hinzugefügt. Die Standardhomepage und -lesezeichen für den Browser können mit einer App-Konfigurationsrichtlinie konfiguriert werden.
Weitere Informationen finden Sie unter [Verwalten des Internetzugriffs mittels Richtlinien für verwaltete Browser](app-configuration-managed-browser.md).

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Einstellungen für BitLocker für Windows 10 <!-- 951707 -->
Sie können jetzt die BitLocker-Einstellungen für Windows 10-Geräte, mithilfe eines neuen Intune Geräteprofils konfigurieren. Sie können z.B. anfordern, dass Geräte verschlüsselt werden und auch weitere Einstellungen konfigurieren, die angewendet werden, wenn BitLocker aktiviert wird.
Weitere Informationen finden Sie unter [Endpoint protection settings for Windows 10 and later (Endpoint Protection-Einstellungen für Windows 10 und höher)](endpoint-protection-windows-10.md).

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Neue Einstellungen für das Windows 10-Geräteeinschränkungsprofil <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
In dieser Version haben wir neue Einstellungen für das Windows 10-Geräteeinschränkungsprofil in folgenden Kategorien hinzugefügt:

-  Windows Defender
-  Mobilfunk und Konnektivität
-  Gesperrter Bildschirm
-  Datenschutz
-  Suchen
-  Windows-Blickpunkt
-  Edgebrowser

Weitere Informationen zu Einstellungen für Windows 10 finden Sie unter [Einstellungen für Geräteeinschränkungen für Windows 10 und höher in Microsoft Intune](device-restrictions-windows-10.md).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>Die Unternehmensportal-App für Android verfügt nun über eine neue Endbenutzererfahrung für App-Schutzrichtlinien <!--1305217-->
Auf Grundlage von Benutzerfeedback haben wir die Unternehmensportal-App für Android modifiziert, sodass sie nun die Schaltfläche **Auf Unternehmensinhalte zugreifen** besitzt. Zweck ist das Verhindern, dass Endbenutzer unnötigerweise den Registrierungsprozess durchlaufen, wenn sie lediglich auf Apps zugreifen müssen, die App-Schutzrichtlinien unterstützen, eine Funktion zur Verwaltung mobiler Anwendungen durch Intune. Sie können diese Änderungen auf der Seite [Was gibt es Neues auf der App-Benutzeroberfläche](whats-new-app-ui.md) anzeigen.

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Neue Menüaktion zum mühelosen Entfernen des Unternehmensportals <!--1164569-->
Basierend auf Benutzerfeedback wurde der Unternehmensportal-App für Android eine neue Menüaktion hinzugefügt, über die das Entfernen des Unternehmensportals von Ihrem Gerät eingeleitet werden kann. Über diese Aktion wird das Gerät aus der Intune-Verwaltung entfernt, damit die App vom Benutzer vom Gerät entfernt werden kann. Sie sehen diese Änderungen auf der Seite zu den [Neuerungen auf der Benutzeroberfläche der App](whats-new-app-ui.md) und in der [Android-Endbenutzerdokumentation](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Verbesserungen bei der App-Synchronisierung mit dem Windows 10 Creators Update <!--676505-->
Die Unternehmensportal-App für Windows 10 löst nun automatisch eine Synchronisierung für App-Installationsanforderungen für Geräte mit dem Windows 10 Creators Update (Version 1703) aus. Dadurch wird das Problem beseitigt, dass App-Installationen während des Zustands „Synchronisierung ausstehend“ verzögert reagieren. Darüber hinaus können Benutzer in der App manuell eine Synchronisierung auslösen. Sie können diese Änderungen auf der Seite [Was gibt es Neues auf der App-Benutzeroberfläche](whats-new-app-ui.md) anzeigen.

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Neue Anleitung für das Windows 10-Unternehmensportal <!---1058938--->
Die Unternehmensportal-App für Windows 10 bietet eine geführte Intune-Anleitung für Geräte, die nicht identifiziert oder registriert wurden. Die neue Anleitung umfasst Schritt-für-Schritt-Anweisungen, mit denen die Registrierung bei Azure Active Directory (erforderlich für Funktionen zum bedingten Zugriff) und die MDM-Registrierung (erforderlich für Funktionen zur Geräteverwaltung) durch den Benutzer erläutert werden. Auf die geführte Anleitung kann über die Hauptseite des Unternehmensportals zugegriffen werden. Benutzer können die App weiter verwenden, auch wenn sie die Registrierung nicht abgeschlossen haben, erhalten aber eingeschränkte Funktionalität.

Dieses Update ist nur auf Geräten unter Windows 10 Anniversary Update (Build 1607) oder höher sichtbar. Sie können diese Änderungen auf der Seite [Was gibt es Neues auf der App-Benutzeroberfläche](whats-new-app-ui.md) anzeigen.


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Verwaltungskonsolen für Microsoft Intune und bedingten Zugriff allgemein verfügbar
Wir kündigen die allgemeine Verfügbarkeit der neuen Intune-Konsole in der Verwaltungskonsole des Azure-Portals und der Verwaltungskonsole für den bedingten Zugriff an. Über Intune im Azure-Portal können Sie jetzt alle Intune-Funktionen für die Verwaltung mobiler Anwendungen (Mobile Application Management, MAM) und mobiler Geräte (Mobile Device Management, MDM) zentral verwalten und die Azure AD-Zielgruppenbestimmung nutzen. Das Feature „Bedingter Zugriff“ in Azure führt umfassende Funktionen in Azure AD und Intune in einer einheitlichen Konsole zusammen. Aus administrativer Sicht ermöglicht Ihnen der Wechsel zur Azure-Plattform den Einsatz moderner Browser.

Intune wird im Azure-Portal auf „portal.azure.com“ jetzt ohne die Bezeichnung **Vorschau** angezeigt.

Bestandskunden müssen derzeit keine Aktion ausführen, es sei denn, Sie haben im Nachrichtencenter eine Nachricht aus einer Reihe von Nachrichten erhalten, in der Sie aufgefordert werden, Maßnahmen zu ergreifen, damit wir Ihre Gruppen migrieren können. Sie haben möglicherweise im Nachrichtencenter auch den Hinweis erhalten, dass die Migration aufgrund von Fehlern unsererseits länger dauert. Wir arbeiten mit Volldampf daran, alle betroffenen Kunden zu migrieren.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Verbesserungen an den App-Kacheln in der Unternehmensportal-App für iOS
Wir haben das Design der App-Kacheln auf der Startseite entsprechend der Brandingfarbe geändert, die Sie für das Unternehmensportal festgelegt haben. Weitere Informationen finden Sie unter [Neuerungen auf der Benutzeroberfläche der App](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Kontoauswahl nun für die Unternehmensportal-App für iOS verfügbar
Benutzern von iOS-Geräten wird ggf. bei der Anmeldung beim Unternehmensportal unsere neue Kontoauswahl angezeigt, wenn sie für die Anmeldung bei anderen Microsoft-Anwendungen ihr Geschäfts-, Schul- oder Unikonto verwenden. Weitere Informationen finden Sie unter [Neuerungen auf der Benutzeroberfläche der App](whats-new-app-ui.md).

## <a name="may-2017"></a>Mai 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Ändern der MDM-Autorität ohne Aufhebung der Registrierung für verwaltete Geräte <!--1103950-->
Sie können nun Ihre MDM-Autorität ändern, ohne sich an den Microsoft-Support wenden und die Aufhebung der Registrierung sowie die erneute Registrierung vorhandener verwalteten Geräte durchführen zu müssen. In der Configuration Manager-Konsole können Sie Ihre [MDM-Autorität ändern](/sccm/mdm/deploy-use/change-mdm-authority), und zwar von der Festlegung auf Configuration Manager (hybrid) in Microsoft Intune (eigenständig) oder umgekehrt.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Verbesserte Benachrichtigung für Samsung KNOX-Systemstart-PINs <!--1087143-->
Wenn Endbenutzer eine Systemstart-PIN für Samsung KNOX-Geräte festlegen müssen, um Konformität hinsichtlich der Verschlüsselung zu erzielen, führt die für Endbenutzer angezeigte Benachrichtigung diese beim Tippen auf die Benachrichtigung genau zu der Stelle in der App „Einstellungen“.  Zuvor hat die Benachrichtigung den Endbenutzer zum Bildschirm für die Kennwortänderung geführt.

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>Unterstützung für Apple School Manager (ASM) auf gemeinsam genutztem iPad<!-- 748864, 770395-->

Intune unterstützt jetzt die Verwendung von Apple Schule Manager (ASM) anstelle des Apple-Programms zur Geräteregistrierung, um die integrierte Registrierung von iOS-Geräten zu ermöglichen. ASM-Onboarding ist erforderlich, um die Classroom-App für gemeinsam genutzte iPads zu verwenden. Zudem ist es erforderlich, um das Synchronisieren von Daten von ASM zu Azure Active Directory über SDS (Microsoft School Data Sync) zu aktivieren. Weitere Informationen finden Sie unter [Aktivieren der iOS-Geräteregistrierung mit Apple School Manager](apple-school-manager-set-up-ios.md).

> [!NOTE]
> Das Konfigurieren gemeinsam genutzter iPads für die Nutzung der App „Classroom“ erfordert iOS Education-Konfigurationen in Azure, die noch nicht verfügbar sind.  Diese Funktionalität wird bald hinzugefügt.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>Bereitstellen von Remoteunterstützung auf Android-Geräten mithilfe von TeamViewer <!-- 675418 -->

Intune kann nun die nicht im Lieferumfang inbegriffene [TeamViewer](https://www.teamviewer.com)-Software nutzen, damit Sie Ihren Benutzern mit Android-Geräten Remoteunterstützung bieten können. Weitere Informationen finden Sie unter [Bereitstellen von Remoteunterstützung für von Intune verwaltete Android-Geräte](device-profile-android-teamviewer.md).

### <a name="app-management"></a>App-Verwaltung

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>Neue Bedingungen für App-Schutzrichtlinien für MAM <!-- 679864 -->

Sie können nun eine Anforderung für MAM ohne Registrierung von Benutzern festlegen, die die folgenden Richtlinien erzwingt:

- Minimale Anwendungsversion
- Minimale Betriebssystemversion
- Mindestversion für Intune App SDK für die Zielanwendung (nur iOS)

Diese Funktion ist für Android und iOS verfügbar. Intune unterstützt die Durchsetzung einer Mindestversion für Betriebssystemplattformen, Anwendungen und das Intune App SDK. Unter iOS können Anwendungen mit integriertem SDK auch eine Durchsetzung einer Mindestversion auf SDK-Ebene festlegen. Der Benutzer kann nicht auf die Zielanwendung zugreifen, wenn die Mindestanforderungen der App-Schutzrichtlinie auf den drei oben aufgeführten verschiedenen Ebenen nicht erfüllt werden. An diesem Punkt kann der Benutzer entweder sein Konto entfernen (für Anwendungen mit mehreren Identitäten), die Anwendung schließen oder seine Betriebssystem- bzw. Anwendungsversion aktualisieren.

Sie können zusätzliche Einstellungen konfigurieren, um eine nicht blockierende Benachrichtigung bereitzustellen, die ein Upgrade des Betriebssystems oder der Anwendung empfiehlt. Diese Benachrichtigung kann geschlossen und die Anwendung wie gewohnt verwendet werden.

Weitere Informationen finden Sie unter [Einstellungen für App-Schutzrichtlinien für iOS](app-protection-policy-settings-ios.md) und [Einstellungen für App-Schutzrichtlinien für Android](app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Konfigurieren von App-Konfigurationen für Android for Work <!-- 621621 -->
Einige Android-Apps aus dem Store unterstützen verwaltete Konfigurationsoptionen, mit denen ein IT-Administrator steuern kann, wie eine App im Arbeitsprofil ausgeführt wird. Mit Intune können Sie jetzt die von einer App unterstützten Konfigurationen anzeigen und sie im Azure-Portal mithilfe eines Konfigurations-Designers oder JSON-Editors konfigurieren. Weitere Informationen finden Sie unter [Verwenden von App-Konfigurationen für Android for Work](app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>Neuen App-Konfigurationsfunktion für MAM ohne Registrierung <!-- 677969 -->
Sie können jetzt App-Konfigurationsrichtlinien über die Verwaltung mobiler Anwendungen (MAM) ohne Registrierungskanal erstellen. Dieses Feature entspricht den App-Konfigurationsrichtlinien, die in der App-Konfiguration für die mobile Geräteverwaltung (MDM) verfügbar sind. Ein Beispiel für die App-Konfiguration mit MAM ohne Registrierung finden Sie unter [Verwalten des Internetzugriffs mittels Richtlinien für Managed Browser mit Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Konfigurieren von Listen mit zugelassenen und blockierten URLs für den Managed Browser <!-- 682960 -->
Sie können jetzt eine Liste zulässiger und blockierter Domänen und URLs für den Intune Managed Browser mithilfe von App-Konfigurationseinstellungen im Azure-Portal konfigurieren. Diese Einstellungen können unabhängig davon verwaltet werden, ob der Browser auf einem verwalteten oder nicht verwalteten Gerät verwendet wird. Weitere Informationen finden Sie unter [Verwalten des Internetzugriffs mittels Richtlinien für Managed Browser mit Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>Helpdeskansicht der App-Schutzrichtlinie <!-- 1069473 -->
IT-Helpdeskbenutzer können nun den Benutzerlizenzstatus und Status von App-Schutzrichtlinien, die Benutzern zugewiesen sind, auf dem Blatt „Problembehandlung“ überprüfen. Weitere Informationen finden Sie unter [Problembehandlung](./help-desk-operators.md).

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="control-website-visits-on-ios-devices----723832---"></a>Steuern von Websitebesuchen auf iOS-Geräten <!-- 723832 -->
Sie können nun mithilfe einer der beiden folgenden Methoden steuern, welche Websites Benutzer von iOS-Geräten besuchen können:

- Zulässige und blockierte URLs mit dem integrierten Webinhaltsfilter von Apple hinzufügen

- Erlauben, dass nur auf bestimmte Websites vom Safari-Browser aus zugegriffen werden darf. Lesezeichen werden in Safari für jede Website erstellt, die Sie angeben.

Weitere Informationen finden Sie im Artikel zu [Filtereinstellungen für Webinhalte auf iOS-Geräten](web-content-filter-settings-ios.md).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Vorkonfigurieren von Geräteberechtigungen für Android for Work-Apps <!-- 621614 -->
Für Apps, die für Android for Work-Gerätearbeitsprofile bereitgestellt werden, können Sie nun den Berechtigungszustand für einzelne Apps konfigurieren.  Standardmäßig fordern Android-Apps, die Geräteberechtigungen erfordern (z. B. Zugriff auf den Standort oder die Gerätekamera), die Benutzer zum Annehmen oder Ablehnen der Berechtigungen auf.  Wenn eine App z. B. das Gerätemikrofon verwendet, wird der Endbenutzer aufgefordert, der App die Berechtigung zur Verwendung des Mikrofons zu erteilen. Dieses Feature gestattet Ihnen, die Berechtigungen im Namen des Endbenutzers zu definieren.  Sie können Berechtigungen konfigurieren, um diese a) automatisch ohne Benachrichtigung des Benutzers zu verweigern, b) automatisch ohne Benachrichtigung des Benutzers zu genehmigen oder c) den Benutzer zum Genehmigen oder Verweigern auffordern. Weitere Informationen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android for Work-Geräte in Microsoft Intune](device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Definieren einer App-spezifischen PIN für Android for Work-Geräte <!-- 728976, 1102534 -->
Android-Geräte ab Version 7.0 mit einem als Android for Work-Gerät verwalteten Arbeitsprofil ermöglichen dem Administrator das Definieren einer Kennungsrichtlinie, die nur für Apps im Arbeitsprofil gilt.  Zu den Optionen gehören:

- Definieren einer geräteweiten Kennungsrichtline: Dies ist die vom Endbenutzer zu verwendende Kennung, um sein gesamtes Gerät zu entsperren.
- Definieren einer Kennungsrichtlinie für das Arbeitsprofil: Benutzer werden zur Eingabe einer Kennung aufgefordert, sobald eine App im Arbeitsprofil geöffnet wird.
- Definieren einer Geräterichtlinie und einer Arbeitsprofilrichtlinie: Die IT-Abteilung hat die Möglichkeit, eine gerätebezogene und eine arbeitsprofilbezogene Kennungsrichtlinie mit unterschiedlicher Stärken zu erstellen (z.B. eine vierstellige PIN zum Entsperren des Geräts, aber eine sechsstellige PIN zum Öffnen einer arbeitsbezogenen App).

Weitere Informationen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android for Work-Geräte in Microsoft Intune](device-restrictions-android-for-work.md).

> [!NOTE]
> Dies ist nur unter Android 7.0 und höher möglich.  Standardmäßig kann der Endbenutzer die beiden separat definierten PINs verwenden oder diese zu einer PIN kombinieren, die die Stärke der jeweils stärkeren PIN übernimmt.

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Neue Einstellungen für Windows 10-Geräte <!-- 978585 -->
Wir haben neue [Einstellungen zur Windows-Geräteeinschränkung](device-restrictions-windows-10.md) hinzugefügt, die Features wie drahtlose Anzeigen, Geräteerkennung, Programmumschaltung und Fehlermeldungen von SIM-Karten steuern.

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>Änderungen an der Zertifikatkonfiguration <!-- 918991 and 823198 -->
Beim Erstellen eines SCEP-Zertifikatprofils für <strong>Format des Antragstellernamens</strong> steht die Option <strong>Benutzerdefiniert</strong> für iOS-, Android- und Windows-Geräte zur Verfügung. Vor dieser Aktualisierung war das Feld <strong>Benutzerdefiniert</strong> nur für iOS-Geräte verfügbar. Weitere Informationen finden Sie unter [Erstellen eines SCEP-Zertifikatprofils](certificates-scep-configure.md#create-a-scep-certificate-profile).

Beim Erstellen eines SCEP-Zertifikatprofils für **Alternativer Antragstellername** steht die Option **Benutzerdefiniertes Azure AD-Attribut** zur Verfügung. Die Option **Abteilung** ist verfügbar, wenn Sie **Benutzerdefiniertes Azure AD-Attribut** auswählen. Weitere Informationen finden Sie unter [Erstellen eines PKCS-Zertifikatprofils](certficates-pfx-configure.md#create-a-device-configuration-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Konfigurieren mehrerer Apps, die ausgeführt werden können, wenn sich ein Android-Gerät im Kioskmodus befindet <!-- 662059 -->
Wenn sich ein Android-Gerät im Kioskmodus befindet, konnte zuvor nur eine App konfiguriert werden, die ausgeführt werden durfte. Sie können jetzt mehrere Apps unter Verwendung der App-ID, der Speicher-URL oder durch Auswahl einer Android-App konfigurieren, die Sie bereits verwalten. Weitere Informationen finden Sie unter [Kioskmoduseinstellungen](device-restrictions-android.md#kiosk).



## <a name="april-2017"></a>April 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Unterstützung der Verwaltung der Apple-App Classroom
Sie können jetzt die iOS-App Classroom auf iPad-Geräten verwalten. Richten Sie die Classroom-App auf dem iPad der Lehrkraft mit den ordnungsgemäßen Schulungsraums- und Schüler-/Studentendaten ein. Konfigurieren Sie anschließend die iPads der Schüler/Studenten, die für einen Schulungsraum registriert sind, damit Sie deren Nutzung der App steuern können.
Einzelheiten finden Sie unter [Konfigurieren von iOS-Einstellungen für Bildungseinrichtungen](education-settings-configure-ios.md)

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Unterstützung für verwaltete Konfigurationsoptionen für Android-Apps <!-- 621621 -->
Android-Apps im Play Store, die verwaltete Konfigurationsoptionen unterstützen, können jetzt von Intune konfiguriert werden.  Mit dieser Funktion kann die IT die Liste der Konfigurationswerte sehen, die von einer App unterstützt werden, und es wird eine übersichtliche, hochwertige Benutzeroberfläche bereitgestellt, damit die IT diese Werte konfigurieren kann.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Neue Android-Richtlinie für komplexe PINs <!-- 722069 -->
Sie können jetzt einen erforderlichen numerisch-komplexen [Kennworttyp](device-restrictions-android.md#password) in einem Android-Geräteprofil für Geräte festlegen, auf denen Android 5.0 und höher ausgeführt wird.  Verwenden Sie diese Einstellung, um zu verhindern, dass Benutzer eine PIN erstellen, die sich wiederholende oder aufeinanderfolgende Zahlen enthält, z.B. 1111 oder 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Zusätzliche Unterstützung für Android for Work-Geräte
- **Verwalten von Kennwort- und Arbeitsprofileinstellungen** <!-- 612808 -->

  Mit dieser neuen Einschränkungsrichtlinie für Android for Work-Geräte können Sie jetzt Kennwort- und Arbeitsprofileinstellungen auf von Ihnen verwalteten Android for Work-Geräten verwalten.

- **Datenaustausch zwischen Arbeitsprofilen und persönlichen Profilen zulassen** <!-- 1045102 -->

Dieses Profil zur Einschränkung von Android for Work-Geräten weist jetzt neue Optionen auf, mit denen Sie die gemeinsame Datennutzung von Arbeits- und persönlichen Profilen konfigurieren können.

- **Beschränken von Kopieren und Einfügen zwischen Arbeitsprofilen und persönlichen Profilen** <!-- 1046094 -->

  Mit einem neuen benutzerdefinierten Geräteprofil für Android for Work-Geräte können Sie einschränken, ob Kopier- und Einfügeaktionen zwischen Arbeits- und persönlichen Apps zulässig sind oder nicht.

Weitere Informationen finden Sie unter [Geräteeinschränkungen für Android for Work](device-restrictions-android-for-work.md).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Zuweisen von branchenspezifischen Apps zu iOS- und Android-Geräten <!-- 1057568 -->
Sie können Benutzern oder Geräten branchenspezifische Apps für [iOS](lob-apps-ios.md) (IPA-Dateien) und [Android](lob-apps-android.md) (APK-Dateien) zuweisen.


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Neue Geräterichtlinien für iOS <!-- 723774, 723815, 723826, 723830 -->
- **Apps auf dem Startbildschirm**: Steuert, welche Apps Benutzer auf dem [Startbildschirm ihres iOS-Geräts](home-screen-settings-ios.md) sehen. Diese Richtlinie wirkt sich auf das Layout des Startbildschirms aus, stellt aber keine Apps bereit.

- **Verbindungen mit AirPrint-Geräten**: Steuert, mit welchen [AirPrint-Geräten](air-print-settings-ios-macos.md) (Netzwerkdruckern) Endbenutzer eines iOS-Geräts eine Verbindung herstellen können.

- **Verbindungen zu AirPlay-Geräten**: Steuert, mit welchen [AirPlay-Geräten](airplay-settings-ios.md) (z.B. Apple TV) Endbenutzer eines iOS-Geräts eine Verbindung herstellen können.

- **Benutzerdefinierte Sperrbildschirmnachricht**: Konfiguriert eine benutzerdefinierte Nachricht, die Benutzern auf dem Sperrbildschirm ihres iOS-Geräts angezeigt wird und die Standardnachricht des Sperrbildschirms ersetzt. Weitere Informationen finden Sie unter [Aktivieren des Modus für verlorene Geräte auf iOS-Geräten](device-lost-mode.md).

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Einschränken von Pushbenachrichtigungen für iOS-Apps <!-- 723767 -->
In einem Intune-Geräteeinschränkungsprofil können Sie jetzt die folgenden [Benachrichtigungseinstellungen](app-notification-settings-ios.md) für iOS-Geräte konfigurieren:

- Aktivieren oder deaktivieren Sie die Benachrichtigungen für eine bestimmte App vollständig.
- Aktivieren oder deaktivieren Sie die Benachrichtigung für eine bestimmte App in der Mitteilungszentrale.
- Geben Sie den Warnungstyp an, entweder **Keinen**, **Banner** oder **modale Warnung**.
- Geben Sie an, ob die Badges für diese App zulässig sind.
- Geben Sie an, ob die Benachrichtigungssounds zulässig sind.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Konfigurieren von iOS-Apps, damit sie autonom im Einzelanwendungsmodus ausgeführt werden sollen <!-- 737837 -->
Sie können jetzt ein Intune-Geräteprofil verwenden, um iOS-Geräte so zu konfigurieren, dass bestimmte Apps im [autonomen Einzelanwendungsmodus](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only) ausgeführt werden. Wenn dieser Modus konfiguriert ist und die App ausgeführt wird, wird das Gerät gesperrt, sodass es nur die App ausführen kann. Ein Beispiel hierfür ist, wenn Sie eine App konfigurieren, mit der Benutzer einen Test auf dem Gerät ausführen können. Wenn die Aktionen der App abgeschlossen sind oder Sie diese Richtlinie entfernen, kehrt das Gerät in seinen normalen Zustand zurück.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Konfigurieren von vertrauenswürdigen Domänen für das Durchsuchen von E-Mails und das Webbrowsen auf iOS-Geräten <!-- 723765 -->
Sie können in einem iOS-Geräteeinschränkungsprofil jetzt die folgenden [Domäneneinstellungen](device-restrictions-ios.md#domains) konfigurieren:

- **Nicht gekennzeichnete E-Mail-Domänen**: Vom Benutzer gesendete oder empfangene E-Mails, die nicht den hier angegebenen Domänen entsprechen, werden als nicht vertrauenswürdig markiert.

- **Verwaltete Webdomänen**: Dokumente, die von den hier angegebenen URLs heruntergeladen werden, gelten als verwaltet (nur Safari).  

- **AutoAusfüllen-Domänen für Safari-Kennwörter**: Benutzer können Kennwörter in Safari nur aus URLs speichern, die mit den von Ihnen hier angegebenen Mustern übereinstimmen. Um diese Einstellung verwenden, muss sich das Gerät im überwachten Modus befinden und darf nicht für mehrere Benutzer konfiguriert sein. (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>Im iOS-Unternehmensportal verfügbare VPP-Apps als <!-- 748782 -->
Sie können per Volumenlizenz erworbene iOS-Apps (VPP-Apps) Endbenutzern jetzt als **verfügbare** Installationen zuweisen. Endbenutzer benötigen ein Apple Store-Konto, um die App zu installieren.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Synchronisieren von eBooks vom Apple-VPP-Store <!-- 800878 -->
Sie können jetzt [Bücher synchronisieren](vpp-apps-ios.md), die Sie im Apple-VPP-Store mit Intune erworben haben, und diese Bücher Benutzern zuweisen.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Mehrbenutzerverwaltung für Samsung KNOX Standard-Geräte <!-- 971988 -->
Geräte, auf denen Samsung KNOX Standard ausgeführt wird, werden jetzt für die [Mehrbenutzerverwaltung](android-enroll.md) von Intune unterstützt. Das bedeutet, dass sich Endbenutzer auf dem Gerät mit ihren Azure Active Directory-Anmeldeinformationen an- und wieder abmelden können, und dass das Gerät zentral verwaltet wird, egal ob es sich in Gebrauch befindet oder nicht.  Wenn sich Endbenutzer anmelden, verfügen Sie über Zugriff auf Apps und erhalten alle Richtlinien, die ihnen zugewiesen sind. Wenn sich Benutzer abmelden, werden alle App-Daten gelöscht.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Zusätzliche Einstellungen zur Einschränkung für Windows-Geräte <!-- 818566 -->
Wir haben Unterstützung für zusätzliche [Einschränkungseinstellungen für Windows-Geräte](device-restrictions-windows-10.md) hinzugefügt, z.B. zusätzliche Unterstützung für den Microsoft Edge-Browser, Anpassung des Gerätesperrbildschirms, Anpassungen des Startmenüs, festgelegtes Hintergrundbild der Windows Spotlight-Suche und Proxyeinstellungen.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Unterstützung für Windows 10 Creators Update für mehrere Benutzer <!-- 822547 -->
Wir haben Unterstützung für die [Mehrbenutzerverwaltung](windows-enroll.md) für Geräte hinzugefügt, die das Windows 10 Creators Update ausführen und in die Azure Active Directory-Domäne eingebunden sind. Das bedeutet Folgendes: Wenn sich unterschiedliche Standardbenutzer mit ihren Azure AD-Anmeldeinformationen auf dem Gerät anmelden, erhalten sie alle Apps und Richtlinien, die ihrem jeweiligen Benutzernamen zugewiesen sind. Benutzer können das Unternehmensportal derzeit nicht für Self-Service-Szenarien beispielsweise zum Installieren von Apps verwenden.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start für Windows 10-PCs <!-- 1004830 -->
Eine neue [Fresh Start-Geräteaktion](device-fresh-start.md) für Windows 10-PCs ist jetzt verfügbar.  Wenn Sie diese Aktion ausführen, werden alle installierten Apps auf dem PC entfernt, und der PC wird automatisch auf die neueste Windows-Version aktualisiert. Damit können vorinstallierte OEM-Apps entfernt werden, die oft mit einem neuen PC geliefert werden. Sie können konfigurieren, ob Benutzerdaten beibehalten werden, wenn diese Geräteaktion ausgegeben wird.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Zusätzliche Windows 10-Upgradepfade <!-- 903672 -->
Sie können jetzt eine [Richtlinie für Editionsupgrades](edition-upgrade-configure-windows-10.md) erstellen, um Geräte auf die folgenden zusätzlichen Windows 10-Editionen zu aktualisieren:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Massenregistrierung von Windows 10-Geräten <!-- 747607 -->
Sie können jetzt eine große Anzahl von Geräten, auf denen das Windows 10 Creators Update ausgeführt wird, mit Windows Configuration Designer (WCD) in Azure Active Directory und Intune einbinden. Um die [MDM-Massenregistrierung](windows-bulk-enroll.md) für Ihren Azure AD-Mandanten zu aktivieren, erstellen Sie ein Bereitstellungspaket, das Geräte mithilfe von Windows Configuration Designer in Ihren Azure AD-Mandanten einbindet. Sie können das Paket auf alle unternehmenseigenen Geräte anwenden, die Sie per Massenvorgang registrieren und verwalten möchten. Nachdem das Paket auf Ihre Geräte angewendet wurde, werden die Geräte in Azure AD eingebunden sowie bei Intune registriert und sind dann bereit für die Anmeldung durch Ihre Azure AD-Benutzer.  Azure AD-Benutzer sind auf diesen Geräten Standardbenutzer und erhalten zugewiesene Richtlinien sowie erforderliche Apps. Die Verwendung von Self-Service-Funktionen und Unternehmensportalen wird derzeit nicht unterstützt.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Neue MAM-Einstellungen für die PIN und verwaltete Speicherorte <!-- 581122, 736644 -->
Es sind zwei neue App-Einstellungen verfügbar, die Sie in MAM-Szenarien (Mobile Application Management, Verwaltung mobiler Anwendungen) unterstützen:

- **App-PIN deaktivieren, wenn die Geräte-PIN verwaltet wird**: Erkennt, ob eine Geräte-PIN auf dem registrierten Gerät vorhanden ist. Falls ja, wird die App-PIN umgangen, was durch die App-Schutzrichtlinien ausgelöst wird. Diese Einstellung ermöglicht eine Verminderung der Häufigkeit, wann immer Benutzern eine Aufforderung zur PIN-Eingabe angezeigt wird, wenn sie eine MAM-fähige Anwendung auf einem registrierten Gerät öffnen. Diese Funktion ist für Android und iOS verfügbar.

- **Wählen, welche Speicherdienste Unternehmensdaten speichern können**: Damit können Sie angeben, an welchen Speicherorten Unternehmensdaten gespeichert werden sollen. Benutzer können in ausgewählten Speicherortdiensten speichern, das heißt, dass alle anderen Speicherortdienste, die nicht aufgelistet sind, blockiert werden.

  Liste der unterstützten Speicherortdienste:

  - OneDrive
  - Business SharePoint Online
  - Lokaler Speicher

### <a name="help-desk-troubleshooting-portal----907448---"></a>Helpdeskportal zur Problembehandlung <!-- 907448 -->
Im neuen [Portal zur Problembehandlung](help-desk-operators.md) können Helpdeskmitarbeiter und Intune-Administratoren Benutzer und Geräte anzeigen und Aufgaben ausführen, um technische Intune-Probleme zu lösen.

## <a name="march-2017"></a>März 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Unterstützung des iOS-Modus für verlorene Geräte <!--431695-->
Für Geräte unter iOS 9.3 (oder höher) wurde von Intune die Unterstützung des **Modus für verlorene Geräte** hinzugefügt. Nun können Sie ein Gerät sperren, um zu dessen Verwendung vollständig zu unterbinden, und auf dem Sperrbildschirm des Geräts eine Meldung und eine Kontakttelefonnummer anzeigen.

Der Endbenutzer kann das Gerät erst wieder entsperren, wenn ein Administrator den Modus für verlorene Geräte deaktiviert. Bei aktivierten Modus für verlorene Geräte können Sie mithilfe der Aktion **Gerät suchen** den geografischen Standort des Geräts auf einer Karte in der Intune-Konsole anzeigen.

Bei dem Gerät muss es sich um ein firmeneigenes, über DEP registriertes iOS-Gerät im überwachten Modus handeln.

Weitere Informationen finden Sie unter [Was ist die Microsoft Intune-Geräteverwaltung?](device-management.md).

### <a name="improvements-to-device-actions-report---677150--"></a>Verbesserungen des Geräteaktionenberichts<!--677150-->
Wir haben die Leistung des Geräteaktionenberichts verbessert. Darüber hinaus können Sie jetzt den Bericht nach Status filtern. Beispielsweise könnten Sie den Bericht so filtern, dass nur Geräteaktionen angezeigt werden, die abgeschlossen wurden.

### <a name="custom-app-categories---748805--"></a>Benutzerdefinierte App-Kategorien <!--748805-->
Sie können jetzt Kategorien für in Intune hinzugefügte Apps erstellen, bearbeiten und zuweisen. Zurzeit können Kategorien nur auf Englisch angegeben werden.
Weitere Informationen finden Sie unter [How to add an app to Intune (Hinzufügen einer App zu Intune)](apps-add.md).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Zuweisen von Branchen-Apps für Benutzer nicht registrierter Geräte <!--748823-->
Sie können Benutzern jetzt Branchen-Apps aus dem Store zuweisen, unabhängig davon, ob die Benutzergeräte bei Intune registriert sind oder nicht. Wenn das Gerät eines Benutzers nicht bei Intune registriert ist, muss der Benutzer die App über die Unternehmensportal-Website statt über die Unternehmensportal-App installieren.

### <a name="new-compliance-reports---846671--"></a>Neue Kompatibilitätsberichte <!--846671-->
Jetzt informieren Kompatibilitätsberichte Sie über die Kompatibilitätsstellung von Geräten in Ihrem Unternehmen, sodass sie schnell kompatibilitätsbezogene Probleme beheben können, von denen Ihre Benutzer betroffen sind. Sie können Informationen anzeigen zu:

- Gesamter Kompatibilitätsstatus von Geräten
- Kompatibilitätsstatus für eine einzelne Einstellung
- Kompatibilitätsstatus für eine einzelne Richtlinie

Sie können mit diesen Berichten auch Detailinformationen zu einzelnen Geräten erhalten, um bestimmte Einstellungen und Richtlinien anzuzeigen, die sich auf das Gerät auswirken.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkter Zugriff auf Apple-Registrierungsszenarien <!--951869-->
Für Intune-Konten, die nach Januar 2017 erstellt wurden, hat Intune direkten Zugriff auf Apple-Registrierungsszenarien mithilfe der Workload „Geräte registrieren“ im Azure-Portal aktiviert. Bisher konnte nur über Links im Azure-Portal auf die Apple-Registrierungsvorschau zugegriffen werden. Vor Januar 2017 erstellte Intune-Konten erfordern eine einmalige Migration, bevor diese Features in Azure verfügbar sind. Der Zeitplan für die Migration wurde noch nicht angekündigt, aber Sie erfahren so bald wie möglich Näheres. Wir empfehlen Ihnen dringend, ein Testkonto zu erstellen, um die neue Oberfläche zu testen, wenn Sie mit Ihrem vorhandenen Konto nicht auf die Vorschau zugreifen können.


## <a name="february-2017"></a>Februar 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Einschränken der Registrierung von Mobilgeräten <!--747600, 795782-->
Es wurden neue Registrierungseinschränkungen zu Intune hinzugefügt, mit denen sich kontrollieren lässt, welche Mobilgeräteplattformen für die Registrierung zugelassen werden. Intune unterscheidet dabei zwischen den Mobilgeräteplattformen iOS, macOS, Android, Windows und Windows Mobile.

* Durch das Einschränken der Registrierung von Mobilgeräten wird die Registrierung von PC-Clients nicht eingeschränkt.  
* Für iOS und Android gibt es eine zusätzliche Option, mit der die Registrierung persönlicher Geräte blockiert werden kann.

Intune kennzeichnet alle neuen Geräte als persönlich, es sei denn, der IT-Administrator kennzeichnet sie als unternehmenseigen – wie in [diesem Artikel](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices) beschrieben.

### <a name="view-all-actions-on-managed-devices---677150--"></a>Anzeigen aller Aktionen auf verwalteten Geräten <!--677150-->
Ein neuer Bericht über __Geräteaktionen__ zeigt, wer Remoteaktionen wie das Zurücksetzen auf Werkseinstellungen auf Geräten ausgeführt hat sowie den Status dieser Aktion. Weitere Informationen finden Sie unter [Was ist die Geräteverwaltung?](device-management.md)

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Nicht verwaltete Geräte können auf zugewiesene Apps zugreifen <!--664691-->
Als Teil der Designänderungen auf der Unternehmensportal-Website können iOS- und Android-Benutzer Apps installieren, die ihnen als „Verfügbar ohne Registrierung“ auf Ihren nicht verwalteten Geräten zugewiesen sind. Benutzer können sich mit ihren Intune-Anmeldeinformationen auf der Unternehmensportal-Website anmelden und die Liste der ihnen zugewiesenen Apps anzeigen. Die App-Pakete der Apps des Typs „Verfügbar ohne Registrierung“ werden zum Download über die Unternehmensportal-Website verfügbar gemacht. Apps, für die die Registrierung für die Installation erforderlich ist, sind durch diese Änderung nicht betroffen, da Benutzer aufgefordert werden, ihr Gerät zu registrieren, wenn sie diese Apps installieren möchten.

### <a name="custom-app-categories---748805--"></a>Benutzerdefinierte App-Kategorien <!--748805-->
Sie können jetzt Kategorien für in Intune hinzugefügte Apps erstellen, bearbeiten und zuweisen. Zurzeit können Kategorien nur auf Englisch angegeben werden.
Weitere Informationen finden Sie unter [How to add an app to Intune (Hinzufügen einer App zu Intune)](apps-add.md).

### <a name="display-device-categories---814654--"></a>Anzeigen von Gerätekategoriern <!--814654-->
Sie können nun die Gerätekategorie als Spalte in der Geräteliste anzeigen. Sie können die Kategorie auch im Abschnitt „Eigenschaften“ des Blatts „Geräteeigenschaften“ bearbeiten. Weitere Informationen finden Sie unter [How to add an app to Intune (Hinzufügen einer App zu Intune)](apps-add.md).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Konfigurieren von Einstellungen für Windows Update for Business <!--776716-->

Windows als Dienst ist die neue Methode zur Bereitstellung von Updates für Windows 10. Ab Windows 10 enthalten neue Funktions- und Qualitätsupdates die Inhalte aller früheren Updates. Das bedeutet, dass Ihre Windows 10-Geräte nach der Installation des neuesten Updates vollständig auf dem neuesten Stand sind. Im Gegensatz zu früheren Versionen von Windows müssen Sie nun anstelle eines Teilupdates das gesamte Update installieren.

Mithilfe von Windows Update for Business können Sie die Updateverwaltung vereinfachen, sodass Sie für Gruppen von Geräten keine einzelnen Updates genehmigen müssen. Sie können weiterhin eine Updaterolloutstrategie konfigurieren, um das Risiko in Ihren Umgebungen zu managen und sicherzustellen, dass Updates zur richtigen Zeit installiert werden. Mit Microsoft Intune können Sie Updateeinstellungen auf Geräten konfigurieren und die Updateinstallation zurückstellen. Intune speichert nur die Updaterichtlinienzuweisung, nicht die Updates. Geräte greifen direkt auf Windows Update zu, um die Updates zu beziehen. Intune dient zum Konfigurieren und Verwalten der **Windows 10-Updateringe**. Ein Updatering enthält eine Reihe von Einstellungen, die festlegen, wann und wie Updates für Windows 10 installiert werden. Ausführlichere Informationen finden Sie unter [Konfigurieren von Einstellungen für Windows Update for Business](windows-update-for-business-configure.md).
