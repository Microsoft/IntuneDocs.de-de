---
title: Neues in Microsoft Intune – Azure | Microsoft-Dokumentation
titlesuffix: ''
description: Erfahren Sie, welche Neuerungen es im Intune-Azure-Portal gibt
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/14/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: 41c5af504bb65a661e55d09d735a78df780deb84
ms.sourcegitcommit: 698af815f6de2c4f003f6da428bbfb0680daafa0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43092174"
---
# <a name="whats-new-in-microsoft-intune"></a>Neuerungen in Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Erfahren Sie jede Woche, welche Neuerungen Microsoft Intune zu bieten hat. Sie erhalten auch Informationen zu [bevorstehenden Änderungen](#whats-coming), [wichtige Hinweise](#notices) zum Dienst und Informationen zu [vorherigen Versionen](whats-new-archive.md). Einige Features werden im Laufe mehrerer Wochen bereitgestellt und sind in der ersten Woche möglicherweise nicht für alle Kunden verfügbar.

> [!Note]
> Informationen zu neuen Funktionen der hybriden Verwaltung mobiler Geräte (MDM) finden Sie auf der Seite [Neuheiten bei der hybriden Verwaltung mobiler Geräte](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->   


## <a name="week-of-august-27-2018"></a>Woche vom 27. August 2018

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Verwendung von VPP-Gerätelizenzen, zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung <!-- 1608345 -->
Sie können jetzt Gerätelizenzen des Volume Purchase Program (VPP) verwenden, um das Unternehmensportal während der Registrierungsvorgänge des Programms zur Geräteregistrierung (Device Enrollment Program, DEP) vorab bereitzustellen. Geben Sie dazu bei der [Erstellung oder Bearbeitung eines Registrierungsprofils](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) das VPP-Token an, das Sie zum Installieren des Unternehmensportals verwenden möchten. Stellen Sie sicher, dass Ihr Token nicht abläuft, und dass Sie über genügend Lizenzen für die Unternehmensportal-App verfügen. In Fällen, in denen das Token abläuft oder über keine Lizenzen mehr verfügt, überträgt Intune stattdessen das App Store-Unternehmensportal mithilfe von Push (dafür ist die Eingabe eine Apple-ID erforderlich).


## <a name="week-of-august-14-2018"></a>Woche vom 14. August 2018

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>macOS-Unterstützung für das Programm zur Geräteregistrierung von Apple<!-- 747651 -->
Intune unterstützt jetzt die Registrierung von macOS-Geräten über das Apple-Programm zur Geräteregistrierung. Weitere Informationen finden Sie unter [Automatisches Registrieren von macOS-Geräten mit dem Programm zur Geräteregistrierung von Apple](device-enrollment-program-enroll-macos.md).

## <a name="week-of-july-23-2018"></a>Woche vom 23. Juli 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>Unterstützung von branchenspezifischen Apps für macOS <!-- 1895847 -->
Mit Microsoft Intune können Sie branchenspezifische macOS-Apps als **Required** (Erforderlich) oder **Available with enrollment** (Mit Registrierung verfügbar) bereitstellen. Sie können Endbenutzern Apps als **Available** (Verfügbar) über das Unternehmensportal für macOS oder über die [Website des Unternehmensportals](https://portal.manage.microsoft.com) bereitstellen.

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>Unterstützung von integrierten, im Kioskmodus ausführbaren iOS-Apps <!-- 2051098 -->
Zusätzlich zu Store-Apps und verwalteten Apps können Sie nun auf einem iOS-Gerät eine integrierte App (beispielsweise Safari) auswählen, die sich im Kioskmodus ausführen lässt.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Bearbeiten von Office 365 Pro Plus-App-Bereitstellungen <!-- 2150145 -->
Als Microsoft Intune-Administrator haben Sie mehr Möglichkeiten, Ihre Office 365 Pro Plus-App-Bereitstellungen zu bearbeiten. Darüber hinaus müssen Sie Ihre Bereitstellungen nicht mehr löschen, um Eigenschaften der Suite zu ändern. Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Mobile Apps** > **Apps**. Wählen Sie aus der Liste der Apps Ihre Office 365 Pro Plus-Suite aus.  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>Aktuelles Intune App SDK für Android jetzt verfügbar <!-- 2744271-->

Zur Unterstützung der Android P-Version ist eine aktualisierte Version des Intune App SDK für Android verfügbar. Wenn Sie App-Entwickler sind und das Intune SDK für Android verwenden, müssen Sie die aktualisierte Version des Intune App SDK installieren, um sicherzustellen, dass die Intune-Funktionen in Ihren Android-Apps auch auf Android P-Geräten wie erwartet ausgeführt werden. Diese Version des Intune App SDK stellt ein integriertes Plug-In bereit, das die SDK-Updates ausführt. Sie müssen keinerlei integrierten Code neu schreiben. Weitere Details finden Sie unter [Intune SDK für Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Wenn Sie das alte Kennzeichenformat für Intune verwenden, empfehlen wir die Verwendung des Aktenkoffersymbols. Informationen zum Branding finden Sie in [diesem GitHub-Repository](https://github.com/msintuneappsdk/intune-app-partner-badge).


### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>Verwenden von S/MIME zum Verschlüsseln und Signieren von mehreren Geräten eines Benutzers <!-- 1333642 -->
Mit diesem Update wird die E-Mail-Verschlüsselung mit S/MIME mittels eines neuen Profils für importierte Zertifikate eingeführt. Navigieren Sie zu deren Verwendung zu **Gerätekonfiguration** > **Profile** > **Profil erstellen**, und wählen Sie zuerst die Plattform und dann den Profiltyp **Importiertes PKCS-Zertifikat** aus. In Intune können Sie Zertifikate im PFX-Format importieren. Intune kann dann genau diese Zertifikate an mehrere Geräte übergeben, die durch einen einzelnen Benutzer registriert wurden. Außerdem enthalten:

- Das native iOS-E-Mail-Profil unterstützt die Aktivierung der S/MIME-Verschlüsselung mithilfe importierter Zertifikate im PFX-Format.
- Die native E-Mail-App auf Windows Phone 10-Geräten verwendet automatisch das S/MIME-Zertifikat.
- Die privaten Zertifikate können über mehrere Plattformen übermittelt werden. Jedoch unterstützen nicht alle E-Mail-Apps S/MIME.
- Auf anderen Plattformen müssen Sie möglicherweise die E-Mail so konfigurieren, dass Sie S/MIME zulässt.  
- E-Mail-Apps, die die S/MIME-Verschlüsselung unterstützen, behandeln das Abrufen von Zertifikaten für die S/MIME-E-Mail-Verschlüsselung womöglich in einer Art und Weise, die von MDM nicht unterstützt werden kann, z.B. durch Lesen über den Zertifikatspeicher des Verlegers.

Unterstützt unter: Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Erstellen von Konformitätsrichtlinien für macOS-Geräte über Firewalleinstellungen <!-- 1497640 -->
Beim Erstellen einer neuen macOS-Konformitätsrichtlinie (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Plattform: macOS** > **Systemsicherheit**) sind einige neue **Firewall**-Einstellungen verfügbar: 

- **Firewall:** Hier konfigurieren Sie, wie eingehende Verbindungen in Ihrer Umgebung behandelt werden.
- **Eingehende Verbindungen:** Mit dieser Einstellung können Sie eingehende Verbindungen für grundlegende Internetdienste wie DHCP, Bonjour und IPSec zulassen und alle anderen eingehenden Verbindungen **blockieren**. Alle Freigabedienste werden durch diese Einstellung blockiert.
- **Geschützter Modus:** Durch die **Aktivierung** dieser Einstellung hindern Sie das Gerät daran, auf Suchanforderungen zu antworten. Das Gerät antwortet weiterhin auf eingehende Anforderungen für autorisierte Apps.

Gilt für: macOS 10.12 und höher

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Neues WLAN-Gerätekonfigurationsprofil für Windows 10 und höher <!-- 1879077 -->
Aktuell können Sie WLAN-Profile mithilfe von XML-Dateien importieren und exportieren. Durch dieses Update können Sie ein WLAN-Gerätekonfigurationsprofil genau wie für andere Plattformen auch direkt in Intune erstellen.

Um ein Profil zu erstellen, öffnen Sie **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** > **WLAN**. 

Gilt für Windows 10 und höher.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998-eeready---"></a>„Kiosk – Veraltet“ ist ausgegraut und kann nicht verändert werden <!-- 2149998 eeready -->
Das [Kiosk-Feature](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** > **Geräteeinschränkungen**) ist veraltet und wurde durch [Kiosk-Einstellungen für Windows 10 und höher](kiosk-settings.md) ersetzt. Durch dieses Update wird das Feature **Kiosk - Obsolete** (Kiosk – veraltet) ausgegraut, und die Benutzeroberfläche kann nicht verändert oder aktualisiert werden. 

Informationen zum Aktivieren des Kioskmodus finden Sie unter [Kioskeinstellungen für Windows 10 und höher in Intune](kiosk-settings.md).

Gilt für Windows 10 und höher, Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>APIs für die Verwendung von Zertifizierungsstellen von Drittanbietern <!-- 2184013 -->
Mit diesem Update wird eine Java-API eingeführt, mit der sich Drittanbieter-Zertifizierungsstellen in Intune und SCEP integrieren lassen. Benutzer können so das SCEP-Zertifikat einem Profil hinzufügen und es über MDM auf Geräte anwenden.

Derzeit unterstützt Intune [SCEP-Anforderungen über Active Directory-Zertifikatdienste](certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Umschaltfläche zum Anzeigen oder Ausblenden der Schaltfläche „Sitzung beenden“ auf einem Kioskbrowser <!-- 2455253 -->
Sie können nun konfigurieren, ob Kioskbrowser die Schaltfläche „Sitzung beenden“ anzeigen. Sie finden das Steuerelement unter **Gerätekonfiguration** > **Kiosk (Vorschauversion)** > **Kioskwebbrowser**. Wenn die Schaltfläche aktiviert ist und ein Benutzer darauf klickt, fordert die App eine Bestätigung zum Beenden der Sitzung an. Wenn dies bestätigt wird, löscht der Browser alle Browserdaten und navigiert zurück zur Standard-URL.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Erstellen eines eSIM-Mobilfunkkonfigurationsprofils <!-- 2564077 -->
Unter **Gerätekonfiguration** können Sie ein eSIM-Mobilfunkprofil erstellen. Sie können eine Datei importieren, die Mobilfunk-Aktivierungscodes enthält, die von Ihrem Mobilfunkanbieter bereitgestellt werden. Diese Profile können daraufhin für Ihre mit eSIM-LTE aktivierten Windows 10-Geräte bereitgestellt werden, z.B. für das Surface Pro LTE und andere eSIM-fähigen Geräte.

Überprüfen Sie, ob Ihre [Geräte eSIM-Profile unterstützen](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Gilt für Windows 10 und höher. 




### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Automatisches Markieren von Android-Geräten als „Geschäftlich“ über Samsung Knox Mobile Enrollment <!-- 2404851 -->
In der Standardeinstellung werden Android-Geräte, die über Samsung Knox Mobile Enrollment registriert sind, nun unter **Gerätebesitz** als **Geschäftlich** markiert. Sie müssen also Unternehmensgeräte vor der Registrierung bei Knox Mobile Enrollment nicht manuell über IMEI oder Seriennummern identifizieren.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Massenlöschung von Geräten auf dem Blatt „Geräte“ <!-- 1793693 -->

Sie können nun mehrere Geräte gleichzeitig über das Blatt „Geräte“ löschen. Wählen Sie **Geräte** > **Alle Geräte** aus, wählen Sie die Geräte aus, die Sie löschen möchten, und klicken Sie auf **Löschen**. Es wird eine Warnung für die Geräte ausgegeben, die nicht gelöscht werden können.

## <a name="week-of-july-16-2018"></a>Woche vom 16. Juli 2018  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Weitere Synchronisierungsoptionen in der Unternehmensportal-App für Windows  
Mit der Unternehmensportal-App für Windows können Sie nun direkt über die Windows-Taskleiste und das Startmenü eine Synchronisierung starten. Dieses Feature ist besonders hilfreich, wenn Sie nur Geräte synchronisieren und auf Unternehmensressourcen zugreifen müssen. Klicken Sie mit der rechten Maustaste auf das Unternehmensportalsymbol, das an die Taskleiste oder das Startmenü angeheftet ist, um das neue Feature zu verwenden. Klicken Sie in den Menüoptionen (auch als Sprungliste bezeichnet) auf **Dieses Gerät synchronisieren**. Die Unternehmensportal-App wird geöffnet und zeigt die Seite **Einstellungen** an. Außerdem wird die Synchronisierung gestartet. Einen Überblick über dieses neue Feature erhalten Sie unter [Updates der Benutzeroberfläche](whats-new-app-ui.md).   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Geänderte Durchsuchen-Funktion in der Unternehmensportal-App für Windows  

Beim Durchsuchen von oder Suchen nach Apps in der Unternehmensportal-App für Windows können Sie zwischen der Ansicht **Kacheln** und der neu hinzugefügten Ansicht **Details** wechseln. In der neuen Ansicht werden Anwendungsdetails wie Namen, Herausgeber, Veröffentlichungsdatum und Installationsstatus angezeigt.  

Auf der Seite **Apps** können Sie sich in der Ansicht **Installiert** Details zu abgeschlossenen und laufenden App-Installationen anzeigen lassen. Unter [Updates der Benutzeroberfläche](whats-new-app-ui.md) können Sie sich einen Eindruck von der neuen Ansicht verschaffen.  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Verbesserte Funktionen der Unternehmensportal-App für Geräteregistrierungs-Manager  
Wenn ein Geräteregistrierungs-Manager (DEM) sich bei der Unternehmensportal-App für Windows anmeldet, listet die App nun nur das aktuell ausgeführte Gerät des DEM auf. Durch diese Verbesserung wird die Anzahl der Timeouts verringert, die in der Vergangenheit aufgetreten sind, wenn die App versucht hat, alle durch den DEM registrierten Geräte anzuzeigen.  


## <a name="week-of-july-9-2018"></a>Woche vom 9. Juli 2018

### <a name="app-management"></a>App-Verwaltung

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Blockieren des App-Zugriffs basierend auf nicht genehmigten Geräteherstellern und Modellen <!-- 1425689 ! -->
Der Intune-IT-Administrator kann über Intune-App-Schutzrichtlinien die Umsetzung einer festgelegten Liste von Android-Herstellern und/oder iOS-Modellen erzwingen. Der IT-Administrator kann eine durch Semikolon getrennte Liste von Herstellern für Android-Richtlinien und Gerätemodelle für iOS-Richtlinien bereitstellen. Intune-App-Schutzrichtlinien gelten nur für Android und iOS. Für diese festgelegte Liste können zwei verschiedene Aktionen ausgeführt werden:
- Blockieren des App-Zugriffs auf Geräten, die nicht angegeben sind.
- Selektives Zurücksetzen von Unternehmensdaten auf Geräten, die nicht angegeben sind. 

Der Benutzer kann nicht auf die Zielanwendung zugreifen, wenn die Anforderungen der Richtlinie nicht erfüllt sind. Anhand von Einstellungen werden Benutzer entweder blockiert oder Unternehmensdaten innerhalb der App selektiv zurückgesetzt. Für dieses Feature ist auf iOS-Geräten die Beteiligung von Anwendungen erforderlich (wie z.B. WXP, Outlook, Managed Browser, Yammer), um das Intune App SDK für dieses Feature für die Zielanwendungen zu erzwingen. Diese Integration erfolgt fortlaufend und ist von den jeweiligen Anwendungsteams abhängig. Unter Android ist für dieses Feature das neueste Unternehmensportal erforderlich. 

Auf Endbenutzergeräten führt der Intune-Client Aktionen auf Grundlage eines einfachen Abgleichs der Zeichenfolgen aus, die auf dem Blatt „Intune“ für Anwendungsschutzrichtlinien angegeben sind. Dies hängt ausschließlich von dem Wert ab, den das Gerät meldet. Daher sollte der IT-Administrator sicherstellen, dass das beabsichtigte Verhalten korrekt ist. Dazu kann diese Einstellung basierend auf einer Vielzahl von Geräteherstellern und Modellen für eine kleine Benutzergruppe getestet werden. Wählen Sie in Microsoft Intune nacheinander **Mobile Apps** > **App-Schutzrichtlinien** aus, um App-Schutzrichtlinien anzuzeigen und hinzuzufügen. Weiter Informationen zu App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md) und [Selektives Löschen von Daten mithilfe von Zugriffsaktionen für App-Schutzrichtlinien in Intune](app-protection-policies-access-actions.md).

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>Zugriff auf das Vorabreleasebuild der macOS-Unternehmensportal-App <!-- 1734766 -->
Sie können sich mithilfe von Microsoft AutoUpdate registrieren, um nach einem Beitritt zum Insider-Programm frühzeitig Builds zu erhalten. Durch eine Registrierung können Sie das aktualisierte Unternehmensportal verwenden, bevor sie Ihren Endbenutzern zur Verfügung steht. Weitere Informationen finden Sie im [Microsoft Intune-Blog](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

## <a name="week-of-july-2-2018"></a>Woche vom 2. Juli 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>Überwachen des Konfigurationsstatus von iOS-Apps auf allen Geräten <!-- 880037 -->
Als Microsoft Intune-Administrator können Sie auf jedem verwalteten Gerät den Konfigurationsstatus von iOS-Apps überwachen. Klicken Sie im Azure-Portal unter **Microsoft Intune** auf **Geräte** > **Alle Geräte**. Wählen Sie aus der Liste der verwalteten Geräte ein Gerät aus, für das ein Blatt angezeigt werden soll. Klicken Sie auf dem Geräteblatt auf **App-Konfiguration**.

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>Zugriff auf Aktionen für App-Schutzrichtlinien <!-- 1483510 -->
Sie können App-Schutzrichtlinien so konfigurieren, dass nicht kompatible Geräte explizit zurückgesetzt, blockiert oder gewarnt werden. Mit der Aktion *Zurücksetzen* werden Ihre Unternehmensdaten von einem Gerät entfernt. Im Falle eines Zurücksetzens wird der Gerätebenutzer über den Grund für das Zurücksetzen und Schritte zur Wiederherstellung benachrichtigt. Für einige Einstellungen, wie z. B. die Mindestversion des Betriebssystems, können Sie mehrere Aktionen anwenden, z. B. das Blockieren und Zurücksetzen. Beachten Sie, dass diese Aktionen ausgelöst werden, wenn die App gestartet wird.

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Zurücksetzen ausgewählter App-Daten einer Organisation <!-- 1507030 -->
Wenn die in den APP-Zugriffseinstellungen festgelegten Bedingungen nicht erfüllt sind, können Administratoren durch eine neue Aktion ausgewählte Organisationsdaten zurücksetzen.  Dieses Feature hilft Administratoren dabei, vertrauliche Organisationsdaten mithilfe festgelegter Kriterien automatisch zu schützen und aus Anwendungen zu entfernen.

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Widerrufen einer Lizenz für iOS-Apps, die über VPP erworben wurden <!-- 1777384 -->
Als Microsoft Intune-Administrator haben Sie die Möglichkeit, alle Lizenzen für eine bestimmte iOS-App zu widerrufen, die über das Volume Purchase Program (VPP) erworben wurde. Sie können Benutzer benachrichtigen, wenn ihnen eine App-Benutzerlizenz entzogen wurde. Durch das Widerrufen einer App-Lizenz wird die zugehörige VPP-App nicht vom Gerät deinstalliert. Zum Deinstallieren einer VPP-App müssen Sie die Zuweisungsaktion in **Deinstallieren** ändern. Die Anzahl der widerrufenen Lizenzen wird innerhalb der Intune-**App**-Workload im Knoten **Lizenzierte Apps** angezeigt. Weitere Informationen zu iOS-VPP-Apps finden Sie unter [Verwalten von iOS-Apps, die über ein Volumenprogramm mit Microsoft Intune erworben wurden](vpp-apps-ios.md).

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Updates für nicht konforme Meldungen in der Unternehmensportal-App <!-- 1832222 -->
Die Meldung, die Benutzern angezeigt wird, wenn ein Gerät nicht konform ist, wurde überarbeitet. Die Meldungen behalten ihre ursprünglichen Bedeutungen bei, wurden jedoch mit benutzerfreundlicherer Sprache und weniger Fachbegriffen aktualisiert. Auch Links zur Dokumentation und zu Wartungsschritten wurden auf den neuesten Stand gebracht.
Die folgenden Texte (vorher und nachher) sind ein Beispiel für die Verbesserungen an den angezeigten Meldungen:
- **Vorher:** *Dieses Gerät hat nicht innerhalb des von Ihrem IT-Administrator festgelegten Zeitraums eine Verbindung mit dem Intune-Dienst hergestellt. Um dieses Problem zu beheben, öffnen Sie die Unternehmensportal-App auf Ihrem Gerät, und klicken Sie auf die Schaltfläche „Konformität überprüfen“.*
- **Nachher:** *Your device has not checked in with your organization in a while. To reestablish a connection, open the Company Portal app on your device and tap Check Settings for your device. (Ihr Gerät wurde länger nicht mehr bei Ihrer Organisation eingecheckt. Öffnen Sie die Unternehmensportal-App auf Ihrem Gerät, und tippen Sie für Ihr Gerät auf „Einstellungen überprüfen“, um die Verbindung wiederherzustellen.)*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>Widerrufen einer iOS-VPP-App-Lizenz <!-- 1863797 -->
Als Administrator haben Sie die Möglichkeit, eine iOS-VPP-App-Lizenz zu widerrufen, die einem Benutzer oder Gerät zugewiesen ist. Dasselbe erreichen Sie mit der Deinstallation einer iOS-VPP-App. Bevor Sie die App deinstallieren, müssen der Benutzer oder das Gerät aus der Gruppe entfernt werden, die von der App als Ziel verwendet wird. Wenn Sie den Benutzer oder das Gerät aus der Gruppe entfernen, verhindern Sie, dass die App erneut installiert wird. Sobald diese Schritte durchgeführt wurden, können Sie die App-Lizenz einem anderen Benutzer oder Gerät zuweisen. Weitere Informationen zu iOS-VPP-App-Lizenzen, finden Sie unter [Verwalten von iOS-Apps, die über ein Volumenprogramm mit Microsoft Intune erworben wurden](vpp-apps-ios.md).

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>Auswählen von Gerätekategorien durch den Zugriff auf die Einstellungen für Geschäfts-, Schul- oder Unikonten <!-- 1058963 eenotready --> 
Wenn Sie die [Gerätegruppenzuordnung](https://docs.microsoft.com/en-us/intune/device-group-mapping) aktiviert haben, werden Benutzer unter Windows 10 aufgefordert, eine Gerätekategorie auszuwählen, nachdem sie sich unter **Einstellungen** > **Konten** > **Auf Geschäfts-, Schul- oder Unikonto zugreifen** mit der Schaltfläche **Verbinden** angemeldet haben. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Verwenden von „sAMAccountName“ als Kontobenutzername für E-Mail-Profile <!-- 1500307 -->
Sie können das lokal vorhandene Attribut **sAMAccountName** als Kontobenutzername für Android-, iOS- und Windows 10-E-Mail-Profile verwenden. Mit den Attributen `domain` oder `ntdomain` können Sie in Azure Active Directory (Azure AD) außerdem die Domain abrufen. Alternativ können Sie auch eine benutzerdefinierte statische Domäne eingeben.

Zur Nutzung dieses Features müssen Sie das `sAMAccountName`-Attribut Ihrer lokalen Active Directory-Umgebung mit Azure AD synchronisieren.

Gilt für: [Android](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 und höher](email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Anzeigen von in Konflikt stehenden Gerätekonfigurationsprofilen <!-- 1556983 -->
Unter **Gerätekonfiguration** wird eine Liste der vorhandenen Profile angezeigt. Mit diesem Update wird eine neue Spalte hinzugefügt, die Details zu Profilen enthält, die in Konflikt stehen. Sie können eine in Konflikt stehende Zeile anklicken, um die Einstellung und das Profil anzuzeigen, bei denen der Konflikt vorhanden ist. 

Weitere Informationen zum [Verwalten von Konfigurationsprofilen](device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Neue Status für Geräte in der Gerätekonfiguration <!-- 2308882 -->
Wählen Sie unter **Gerätekonformität** > **Richtlinien** eine Richtlinie aus. Dort wurden unter **Übersicht** folgende neue Status hinzugefügt:
- Erfolgreich
- Fehler
- Konflikt
- Ausstehend
- Nicht anwendbar. Außerdem wird eine Grafik angezeigt, in der die Anzahl der Geräte für andere Plattformen zu sehen ist. Beim Aufruf eines iOS-Profils wird beispielsweise auf der neuen Kachel die Anzahl der Nicht-iOS-Geräte angezeigt, die diesem Profil ebenfalls zugewiesen sind. Weitere Informationen finden Sie im Artikel zu [Gerätekonformitätsrichtlinien](compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>Unterstützung von Drittanbieter-Antivirenlösungen in Gerätekonformitätsrichtlinien <!-- 2325484 -->
Beim Erstellen einer Gerätekonformitätsrichtlinie (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Plattform: Windows 10 und höher** > **Einstellungen** > **Systemsicherheit**) sind neue Optionen für **[Gerätesicherheit](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)** verfügbar: 
- **Antivirus:** Wenn für diese Einstellung **Require** (Erforderlich) festgelegt ist, können Sie die Konformität mit Antivirenlösungen (beispielsweise Symantec und Windows Defender) überprüfen, die beim Windows-Sicherheitscenter registriert sind. 
- **Antispyware:** Wenn für diese Einstellung **Require** (Erforderlich) festgelegt ist, können Sie die Konformität mit Antispyware-Lösungen (beispielsweise Symantec und Windows Defender) überprüfen, die beim Windows Security Center registriert sind. 

Gilt für: Windows 10 und höher 

### <a name="device-enrollment"></a>Geräteregistrierung

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>Geräte ohne die Spalte „Profiles“ (Profile) in der Liste der Registrierungsprogrammtoken <!-- 1853904 -->
In der Liste der Registrierungprogrammtoken gibt es eine neue Spalte, in der die Anzahl der Geräte ohne zugewiesenes Profil angezeigt werden. So können Administratoren diesen Geräten leichter Profile zuweisen, bevor sie sie Benutzern zuweisen. Navigieren Sie zu **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken**, um die neue Spalte anzuzeigen.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Google-Namensänderungen für Android for Work und Play for Work <!--842873 -->
In Intune wurde die Android for Work-Terminologie aktualisiert, um die Änderungen von Google-Markennamen widerzuspiegeln. Die Benennungen „Android for Work“ und „Play for Work“ werden nicht mehr verwendet. Die Terminologie wurde je nach Kontext angepasst:
- „Android Enterprise“ bezieht sich auf den allgemeinen modernen Android-Verwaltungsstapel.
- „Arbeitsprofil“ oder „Profilbesitzer“ bezieht sich auf BYOD-Geräte, die mit Arbeitsprofilen verwaltet werden.
- „Managed Google Play“ bezieht sich auf den App Store von Google.

#### <a name="rules-for-removing-devices----1609459---"></a>Regeln für das Entfernen von Geräten <!-- 1609459 -->
Neue Regeln, mit denen Sie Geräte automatisch entfernen können, die über einen festgelegten Zeitraum nicht mehr eingecheckt waren, sind verfügbar. Um die neue Regel anzuzeigen, wechseln Sie in den Bereich **Intune**, und wählen Sie **Geräte** und anschließend **Device removal rules** (Regeln zur Gerätebereinigung) aus.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>COSU-Unterstützung (corporate-owned, single use, Unternehmensgeräte für spezifische Anwendungsfälle) für Android-Geräte <!-- 1630973 -->

Intune unterstützt jetzt kioskartige, stringent verwaltete Android-Geräte, deren Einsatzbereich stark eingeschränkt ist. Dadurch können Administratoren festlegen, dass auf einem Gerät nur eine oder einige wenige Apps und Aktionen von Benutzern verwendet werden dürfen. Navigieren Sie in Intune zu **Geräteregistrierung** > **Android-Registrierung** > **Kiosk und Taskgeräteregistrierungen**, um einen Android-Kiosk einzurichten. Weitere Informationen finden Sie unter [Set up enrollment of Android enterprise kiosk devices (Einrichten der Registrierung von Android-Kioskgeräte des Unternehmens)](android-kiosk-enroll.md).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>Duplikatprüfung auf Zeilenbasis beim Hochladen unternehmensspezifischer Gerätebezeichner <!-- 2203794-->
Beim Hochladen von Unternehmens-IDs stellt Intune jetzt eine Liste mit mehrfach vorhandenen IDs bereit und bietet Ihnen die Möglichkeit, die vorhandenen Informationen zu ersetzen oder beizubehalten. Der Bericht wird angezeigt, wenn nach dem Klicken auf **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten** > **Bezeichner hinzufügen** Duplikate vorhanden sind. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Manuelles Hinzufügen von Unternehmensgerätebezeichnern <!-- 2203803 -->
Sie können Unternehmensgeräte-IDs jetzt manuell hinzufügen. Klicken Sie auf **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten** > **Hinzufügen**. 

## <a name="week-of-june-25-2018"></a>Woche vom 25. Juni 2018

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo: neuer Mobile Threat Defense-Partner <!-- 1169249 -->

Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen mit bedingtem Zugriff basierend auf Risikobewertungen steuern, die von Pradeo vorgenommen werden, einer Mobile Threat Defense-Lösung, die mit Microsoft Intune zusammenarbeitet.

## <a name="week-of-june-18-2018"></a>Woche vom 18. Juni 2018

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Unterstützung des Edge-Browsers für mobile Geräte für die App-Schutzrichtlinien von Intune <!-- 1817882 -->

Microsoft Edge für mobile Geräte unterstützt nun die App-Schutzrichtlinien, die in Intune definiert sind.

## <a name="week-of-june-11-2018"></a>Woche vom 11. Juni 2018

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>Verwenden des FIPS-Modus mit dem NDES-Certificate Connector <!-- 1333688 -->
Wenn Sie den NDES-Certificate Connector auf einem Computer mit aktiviertem FIPS-Modus (Federal Information Processing Standard) installieren, funktionierte das Ausstellen und Widerrufen von Zertifikaten nicht wie erwartet. Mit diesem Update ist die Unterstützung für FIPS im NDES-Certificate Connector enthalten. 

Dieses Update enthält ebenfalls Folgendes:

- Der NDES-Certificate Connector erfordert .NET Framework 4.5. Dieses Framework ist automatisch in Windows Server 2016 und Windows Server 2012 R2 enthalten. Zuvor war .NET Framework 3.5 die mindestens erforderliche Version.
- Die Unterstützung für TLS 1.2 ist im NDES-Certificate Connector enthalten. Wenn der Server, auf dem NDES-Certificate Connector installiert ist, TLS 1.2 unterstützt, wird TLS 1.2 verwendet. Wenn der Server TLS 1.2 nicht unterstützt, wird TLS 1.1 verwendet. Derzeit wird TLS 1.1 für die Authentifizierung zwischen den Geräten und dem Server verwendet.

Weitere Informationen finden Sie unter [Konfigurieren und Verwenden von SCEP-Zertifikaten](certificates-scep-configure.md) und [Konfigurieren und Verwenden von PKCS-Zertifikaten](certficates-pfx-configure.md).

## <a name="week-of-june-4-2018"></a>Woche vom 4. Juni 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Abrufen der zugeordneten App-Benutzermodell-ID (AUMID) für Apps im Microsoft Store für Unternehmen im Kioskmodus <!-- 1560077 ! -->
Intune kann jetzt die Modell-IDs der Anwendungsbenutzer (AUMIDs) für Apps im Microsoft Store für Unternehmen abrufen, um eine verbesserte Konfiguration des Kioskprofils bereitzustellen.

Weitere Informationen zu Apps im Microsoft Store für Unternehmen finden Sie unter [Verwalten von Apps aus dem Microsoft Store für Unternehmen](windows-store-for-business.md).

#### <a name="new-company-portal-branding-page----1916370---"></a>Neue Seite für das Branding des Unternehmensportals <!-- 1916370 -->
Die Seite für das Branding des Unternehmensportals hat ein neues Layout, neue Meldungen und neue QuickInfos.


### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Unterstützung für VPN-Profile für Palo Alto Networks GlobalProtect <!-- 1333680 eeready ! -->
Mit diesem Update können Sie Palo Alto Networks GlobalProtect als VPN-Verbindungstyp für VPN-Profile in Intune auswählen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Profiltyp** > **VPN**). Für dieses Release werden die folgenden Plattformen unterstützt: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Ergänzungen zu den Einstellungen der Sicherheitsoptionen für lokale Geräte <!-- 1403702 -->
Sie können jetzt für Windows 10-Geräte zusätzliche Einstellungen für Sicherheitsoptionen für lokale Geräte konfigurieren. Zusätzliche Einstellungen sind bei Microsoft-Netzwerkclients, Microsoft-Netzwerkservern, bei der Netzwerkzugriff und -sicherheit und bei der interaktiven Anmeldung verfügbar. Diese Einstellungen finden Sie in der Endpoint Protection-Kategorie, wenn Sie eine Gerätekonfigurationsrichtlinie für Windows 10 erstellen.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Aktivieren des Kioskmodus auf Windows 10-Geräten <!-- 1560072 ! -->
Auf Windows 10-Geräten können Sie ein Konfigurationsprofil erstellen und den Kioskmodus aktivieren (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10** > **Geräteeinschränkungen** > **Kiosk**). Bei diesem Update wurde die Einstellung **Kiosk (Vorschau)** in **Kiosk (veraltet)** umbenannt. **Kiosk (veraltet)** wird nicht mehr empfohlen, ist jedoch bis zum Juli-Update weiterhin funktionsfähig. **Kiosk (veraltet)** wird durch den neuen **Kiosk**-Profiltyp ersetzt (**Profil erstellen** > **Windows 10**  >  **Kiosk (Vorschau)**), der die Einstellungen zum Konfigurieren von Kiosks unter Windows 10 RS4 und höher enthält.

Gilt für Windows 10 und höher.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Benutzerdiagramm des Geräteprofils wieder vorhanden <!-- 2160133 -->
Während der Verbesserung der numerischen Werte, die im Diagramm des Geräteprofils dargestellt werden (**Gerätekonfiguration** > **Profile** > vorhandenes Profil auswählen > **(Übersicht)** ), wurde das Benutzerdiagramm vorübergehend entfernt.

Bei diesem Update ist das Benutzerdiagramm wieder enthalten und wird im Azure-Portal angezeigt.

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118-wnready---"></a>Unterstützung für die Registrierung mit Windows Autopilot ohne Benutzerauthentifizierung <!-- 1165118 wnready -->
Intune unterstützt jetzt die Registrierung mit Windows Autopilot ohne Benutzerauthentifizierung. Dies ist eine neue Option im Windows Autopilot-Bereitstellungsprofil („Autopilot Deployment mode“ (Autopilot-Bereitstellungsmodus) kann auf „Self-Deploying“ (Selbstbereitstellung) festgelegt werden).  Auf dem Gerät muss Windows 10 Insider Preview Build 17672 oder höher ausgeführt werden, außerdem muss ein TPM 2.0-Chip eingebaut sein, um diese Art der Registrierung erfolgreich abzuschließen. Da keine Benutzerauthentifizierung erforderlich ist, sollten Sie diese Option nur Geräte zuweisen, zu denen Sie physisch Zugang haben.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766-eeready---"></a>Neue Einstellung für Sprache/Region beim Konfigurieren von OOBE für AutoPilot <!-- 1821766 eeready -->
Es steht eine neue Konfigurationseinstellung zur Verfügung, mit der die Sprache und Region für Autopilot-Profile während der Out-of-Box-Experience festgelegt werden kann. Klicken Sie auf **Geräteregistrierung** > **Windows-Registrierung** > **Bereitstellungsprofile** > **Profil erstellen** > **Bereitstellungsmodus** = **Selbstbereitstellung** > **Standardwerte konfiguriert**, um die neuen Einstellungen anzuzeigen.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Neue Einstellung zum Konfigurieren der Gerätetastatur <!-- 1821768 -->
Es steht eine neue Einstellung zur Verfügung, mit der die Tastatur für AutoPilot-Profile während der Out-of-Box-Experience konfiguriert werden kann. Klicken Sie auf **Geräteregistrierung** > **Windows-Registrierung** > **Bereitstellungsprofile** > **Profil erstellen** > **Bereitstellungsmodus** = **Selbstbereitstellung** > **Standardwerte konfiguriert**, um die neuen Einstellungen anzuzeigen.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>AutoPilot-Profile können bald Gruppenziele verwenden <!-- 1877935 -->
Autopilot-Bereitstellungsprofile können Azure AD-Gruppen zugewiesen werden, die Autopilot-Geräte enthalten.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="set-compliance-by-device-location----851881----"></a>Festlegen der Kompatibilität nach Gerätestandort <!-- 851881 ! -->
In einigen Situationen empfiehlt es sich, den Zugriff auf Unternehmensressourcen auf einen bestimmten Standort zu beschränken, der durch eine Netzwerkverbindung definiert ist. Sie können jetzt eine Kompatibilitätsrichtlinie (**Gerätekompatibilität** > **Standorte**) basierend auf der IP-Adresse des Geräts erstellen. Wird das Gerät außerhalb des IP-Bereichs bewegt, kann damit nicht auf Unternehmensressourcen zugegriffen werden.

Gilt für Android-Geräte 6.0 und höher mit der aktualisierten Unternehmensportal-App

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Verhindern von Verbraucher-Apps und -Umgebungen auf dem Windows 10 Enterprise RS4 AutoPilot-Gerät<!-- 1621980 -->
Sie können die Installation von Verbraucher-Apps und -Umgebungen auf Ihren Windows 10 Enterprise RS4 AutoPilot-Geräten verhindern. Navigieren Sie zu **Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Plattform** = **Windows 10 oder höher** > **Profiltyp** = **Geräteeinschränkungen** > **Konfigurieren** > **Windows-Blickpunkt** > **Endbenutzerfeatures**, um dieses Feature anzuzeigen. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948-eeready---"></a>Deinstallieren der letzten Softwareupdates von Windows 10 <!-- 1732948 eeready -->
Wenn Sie Probleme mit Unterbrechungen auf Ihren Windows 10-Computern feststellen, können Sie das neueste Featureupdate bzw. Qualitätsupdate deinstallieren (einen Rollback ausführen). Die Deinstallation eines Feature- oder Qualitätsupdates ist für den Wartungskanal nur möglich, wenn das Gerät eingeschaltet ist. Durch die Deinstallation wird eine Richtlinie ausgelöst, die das vorherige Update auf Ihren Windows 10-Computern wiederherstellt. Sie können insbesondere für Featureupdates den Zeitraum, in dem eine Deinstallation für die neueste Version durchgeführt werden kann, auf 2–60 Tage einschränken. Um die Deinstallationsoptionen für das Softwareupdate festzulegen, wählen Sie im Azure-Portal auf dem Blatt **Microsoft Intune** die Option **Softwareupdates** aus. Klicken Sie auf dem Blatt **Softwareupdates** auf **Windows 10-Updateringe**. Sie können dann die Option **Deinstallieren** im Bereich **Übersicht** auswählen.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Durchsuchen aller Geräte nach IMEI und Seriennummer <!-- 1793685 -->
Sie können jetzt auf dem Blatt „Alle Geräte“ nach IMEI und Seriennummern suchen (E-Mail, UPN, Gerätename und Verwaltungsname sind weiterhin verfügbar). Klicken Sie in Intune auf **Geräte** > **Alle Geräte**, und geben Sie dann ein Suchwort in das Suchfeld ein.

#### <a name="management-name-field-will-be-editable----1875989---"></a>Feld für Verwaltungsname kann bearbeitet werden <!-- 1875989 -->
Sie können das Feld für den Verwaltungsnamen auf dem Blatt **Eigenschaften** eines Geräts bearbeiten. Zum Bearbeiten dieses Felds wählen Sie **Geräte** > **Alle Geräte** > Gerät auswählen > **Eigenschaften** aus. Sie können das Feld für den Verwaltungsnamen zur eindeutigen Identifizierung eines Geräts verwenden.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Neue Filter für „Alle Geräte“: Gerätekategorie <!-- 1878520 -->
Sie können jetzt die Liste **Alle Geräte** nach Gerätekategorie filtern. Klicken Sie dafür auf **Geräte** > **Alle Geräte** > **Filter** > **Gerätekategorie**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Verwenden von TeamViewer zur Bildschirmübertragung zwischen iOS- und macOS-Geräten <!-- 1985547 -->
Administratoren können jetzt eine Verbindung mit [TeamViewer](device-profile-android-teamviewer.md) herstellen und eine Bildschirmübertragungssitzung mit iOS- und macOS-Geräten starten. iPhone, iPad und macOS-Benutzer können ihre Bildschirme live an andere Desktops oder mobile Geräte übertragen. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Unterstützen von mehreren Exchange-Connectors <!-- 2070451 -->
Sie sind nicht mehr auf einen Microsoft Intune Exchange Connector pro Mandant beschränkt. Intune unterstützt mehrere Exchange Connectors, sodass Sie Intune mithilfe von mehreren lokalen Exchange-Organisationen für bedingten Zugriff einrichten können.

Mit einem lokalen Exchange-Connector von Intune können Sie den Zugriff von Geräten auf Ihre lokalen Exchange-Postfächer verwalten. Dies ist abhängig davon, ob ein Gerät bei Intune registriert ist, und ob es den Gerätekompatibilitätsrichtlinien von Intune entspricht. Um einen Connector einzurichten, müssen Sie den lokalen Exchange-Connector von Intune aus dem Azure-Portal herunterladen und ihn auf einem Server in Ihrer Exchange-Organisation installieren. Klicken Sie im Microsoft Intune-Dashboard auf **Lokaler Zugriff** und dann unter **Setup** auf **Exchange ActiveSync-Connector**. Laden Sie den lokalen Exchange-Connector herunter, und installieren Sie ihn auf einem Server in Ihrer Exchange-Organisation. Da Sie nun nicht länger auf einen Exchange-Connector pro Mandant beschränkt werden, wenn Sie weitere Exchange-Organisationen haben, können Sie anhand des gleichen Durchgangs einen Connector für jede weitere Exchange-Organisation herunterladen und installieren.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Neues Gerätehardwaredetail: CCID <!-- 2156657 -->
Für jedes Gerät sind jetzt auch die CCID-Informationen (Chip Card Interface Device) verfügbar. Klicken Sie auf **Geräte** > **Alle Geräte**, wählen Sie ein Gerät aus, und klicken Sie dann auf **Hardware**, und sehen Sie sich die **Netzwerkdetails**> an, um diese anzuzeigen.

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Zuweisen aller Benutzer und aller Geräte als Bereichsgruppen <!-- 2196803 -->
Sie können alle Benutzer, alle Geräte sowie alle Benutzer und alle Geräte in Bereichsgruppen zuweisen. Klicken Sie hierzu auf **Intune-Rollen** > **Alle Rollen** > **Policy and profile manage** (Richtlinien- und Profil-Manager) > **Zuweisungen**, wählen Sie eine Zuweisung aus, und klicken Sie dann auf **Bereich (Gruppen)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806-wnready--"></a>UDID-Informationen für iOS- und macOS-Geräte <!-- 2219806 wnready-->
Navigieren Sie zu **Geräte** > **Alle Geräte**, wählen Sie ein Gerät aus, und klicken Sie auf **Hardware**, um die UDID (eindeutiger Gerätebezeichner) für iOS- und macOS-Geräte anzuzeigen. Die UDID ist nur für Unternehmensgeräte verfügbar (wie unter **Geräte** > **Ale Geräte**, Gerät auswählen, **Eigenschaften** > **Gerätebesitz** festgelegt).

### <a name="intune-apps"></a>Intune-Apps

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Verbesserte Problembehandlung für App-Installation <!-- 928990 -->
Auf Geräten, die mit Microsoft Intune MDM verwaltet werden, können App-Installationen manchmal fehlschlagen. In diesen Fällen kann es schwierig sein, die Fehlerursache zu verstehen oder das Problem zu beheben. Wir versenden eine öffentliche Vorschau unserer Features zur App-Problembehandlung. Unter jedem einzelnen Gerät wird ein neuer Knoten mit der Bezeichnung **Verwaltete Apps** angezeigt. Hier sind die Apps aufgelistet, die über Intune MDM übermittelt wurden. Innerhalb des Knotens wird eine Liste mit App-Installationsstatus angezeigt. Bei Auswahl einer einzelnen App wird die Problembehandlungsansicht für diese bestimmte App angezeigt. In der Problembehandlungsansicht sehen Sie den End-to-End-Lebenszyklus der App, z. B. wann die App erstellt, geändert, festgelegt und an ein Gerät übermittelt wurde. Darüber hinaus wird bei einer nicht erfolgreichen App-Installation der Fehlercode und eine hilfreiche Nachricht zur Ursache des Fehlers angezeigt. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Intune-App-Schutzrichtlinien und Microsoft Edge <!-- 1818968 -->
Der Browser Microsoft Edge für mobile Geräte (iOS und Android) unterstützt nun Microsoft Intune-App-Schutzrichtlinien. Benutzer von iOS- und Android-Geräten, die sich mit ihren Azure AD-Unternehmenskonten bei der Edge-App anmelden, werden von Intune geschützt. Auf iOS-Geräten lässt die Richtlinie **Require managed browser for web content** (Managed Browser für Webinhalt erforderlich) zu, dass Benutzer Links in Edge öffnen können, wenn der Browser verwaltet wird.

## <a name="week-of-may-14-2018"></a>Woche vom 14. Mai 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Erforderliche Installation von Richtlinien, Apps, Zertifikaten und Netzwerkprofilen <!-- 1553555 -->

Administratoren können Endbenutzern den Zugriff auf Windows 10 RS4 Desktop verwehren, bis Richtlinien, Apps, Zertifikate und Netzwerkprofile während der Bereitstellung von AutoPilot-Geräten von Intune installiert wurden. Weitere Informationen finden Sie unter [Set up an enrollment status page (Einrichten einer Statusseite für die Registrierung)](windows-enrollment-status.md).

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>Konfigurieren von App-Schutzrichtlinien <!-- 2144597 Part 2 -->

Sie müssen jetzt im Azure-Portal nicht mehr auf das Dienstblatt Intune-App-Schutz gehen, sondern können einfach zu Intune navigieren. Es gibt derzeit nur einen Speicherort für App-Schutzrichtlinien in Intune. Beachten Sie, dass Sie bereits alle Ihre App-Schutzrichtlinien auf dem Blatt **Mobile App** in Intune unter **App-Schutzrichtlinien** finden. Diese Integration soll Ihre Cloudverwaltung vereinfachen. Beachten Sie, dass alle Richtlinien zum App-Schutz bereits in Intune verschoben wurden und Sie Ihre Richtlinien für den bedingten Zugriff ändern können. Sie finden die Intune App-Schutzrichtlinien (Intune App Policy Protection, APP) und die Richtlinien für den bedingten Zugriff (Conditional Access, CA) jetzt unter **Bedingter Zugriff** im Abschnitt **Verwalten** auf dem Blatt **Microsoft Intune** oder im Abschnitt **Sicherheit** auf dem Blatt **Azure Active Directory**. Weitere Informationen zum Ändern von Richtlinien für bedingten Zugriff finden Sie unter [Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Weitere Informationen finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>Woche vom 7. Mai 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Unterstützung von Samsung Knox Mobile Enrollment (KME) <!--1112863-->

Wenn Sie Intune mit Samsung Knox Mobile Enrollment (KME) verwenden, können Sie eine große Anzahl unternehmenseigener Android-Geräte registrieren. Benutzer mit einer WLAN- oder Mobilfunknetzverbindung können die Registrierung mit nur wenigen Tippbewegungen ausführen, wenn sie ihre Geräte zum ersten Mal einschalten. Bei Verwendung der Knox Deployment App können Geräte über Bluetooth oder NFC registriert werden. Weitere Informationen finden Sie unter [Automatisches Registrieren von Android-Geräten mit Samsung Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md).

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Anfordern von Hilfe im Unternehmensportal für Windows 10 <!-- 1874137 -->

Das Unternehmensportal für Windows 10 sendet App-Protokolle jetzt direkt an Microsoft, wenn der Benutzer den Workflow zum Abrufen von Hilfe zu einem Problem startet. So können Probleme, die Microsoft gemeldet werden, einfacher behoben und gelöst werden.

## <a name="week-of-april-23-2018"></a>Woche vom 23. April 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Kennungsunterstützung für die MAM-PIN unter Android<!-- 1438086 -->

Intune-Administratoren können zukünftig eine Anforderung für den Anwendungsstart festlegen, um eine Kennung anstatt einer numerischen MAM-PIN zu erzwingen. Wenn dies konfiguriert ist, muss der Benutzer eine Kennung festlegen und verwenden, wenn er dazu aufgefordert wird, bevor der Zugriff auf MAM-aktivierte Apps gewährt wird. Eine Kennung ist als numerische PIN mit mindestens einem Sonderzeichen oder einem Groß-/Kleinbuchstaben definiert. Intune unterstützt Kennungen auf ähnliche Weise wie die vorhandene numerische PIN. Es kann eine Mindestlänge über die Administratorkonsole festgelegt werden, sodass wiederholte Zeichen und Sequenzen möglich sind. Für dieses Feature ist die neueste Unternehmensportalversion unter Android erforderlich. Dieses Feature ist bereits für iOS verfügbar.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Unterstützung von branchenspezifischen Apps für macOS <!-- 1473977 -->
Microsoft Intune stellt eine Funktion zur Installation von macOS-LOB-Apps aus dem Azure-Portal bereit. Sie können eine macOS-LOB-App zu Intune hinzufügen, nachdem sie von dem in GitHub verfügbaren Tool vorab verarbeitet wurde. Wählen Sie im Azure-Portal auf dem Blatt **Intune** die Option **Mobile Apps** aus. Wählen Sie auf dem Blatt **Mobile Apps** die Option **Apps** > **Hinzufügen** aus. Wählen Sie auf dem Blatt **App hinzufügen** die Option **Branchen-App** aus. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Integrierte App-Zuweisung in Android for Work (AFW) für die Gruppen „Alle Benutzer“ und „Alle Geräte“ <!-- 1813073 -->
Sie können die integrierten Gruppen **Alle Benutzer** und **Alle Geräte** für die AFW-App-Zuweisung nutzen. Weitere Informationen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune installiert benötigte Apps, die von Benutzern deinstalliert werden. <!-- 1947010 -->
Wenn ein Endbenutzer eine benötigte App deinstalliert, installiert Intune die App automatisch innerhalb von 24 Stunden neu, anstatt auf die Beendigung des siebentägigen Neuauswertungszyklus zu warten.

### <a name="device-configuration"></a>Gerätekonfiguration

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>Geräteprofildiagramm und Statusliste zeigen alle Geräte in einer Gruppe <!-- 1449153 eeready -->
Wenn Sie ein Geräteprofil konfigurieren (**Gerätekonfiguration** > **Profile**), wählen Sie das Geräteprofil aus, z.B. iOS. Sie weisen dieses Profil einer Gruppe zu, die iOS-Geräte und Nicht-iOS-Geräte enthält. Im Grafikdiagramm ist zu sehen, dass das Profil dem iOS-Gerät *und* dem Nicht-iOS-Gerät zugewiesen wird (**Gerätekonfiguration** > **Profile** > vorhandenes Profil auswählen > **Übersicht**). Wenn Sie das Grafikdiagramm auf der Registerkarte **Übersicht** auswählen, werden unter **Gerätestatus** alle Geräte der Gruppe aufgeführt, nicht nur iOS-Geräte. 

Nach diesem Update wird im Grafikdiagramm (**Gerätekonfiguration** > **Profile** > vorhandenes Profil auswählen > **Übersicht**) nur die Anzahl für das spezifische Geräteprofil angezeigt. Wenn z.B. das Gerätekonfigurationsprofil für iOS-Geräte gilt, wird im Diagramm nur die Anzahl der iOS-Geräte aufgelistet. Wenn Sie das Grafikdiagramm auswählen und **Gerätestatus** öffnen, werden nur iOS-Geräte aufgelistet.

Während dieses Updates wird das Benutzerdiagramm vorübergehend entfernt. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>Always On-VPN für Windows 10 <!--1333666 -->

Derzeit kann [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) auf Windows 10-Geräten mit einem benutzerdefinierten VPN (virtuelles privates Netzwerk), das über den OMA-URI erstellt wurde, verwendet werden.

Mit diesem Update können Administratoren Always On für VPN-Profile auf Windows 10 direkt in Intune im Azure-Portal aktivieren. Always On-VPN-Profile stellen automatisch eine Verbindung her, wenn Folgendes passiert:

- Benutzer melden sich an ihren Geräten an.
- Das Netzwerk auf dem Gerät ändert sich.
- Der Bildschirm wird auf dem Gerät wieder eingeschaltet, nachdem er ausgeschaltet war.

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Neue Druckereinstellungen für Education-Profile <!-- 1308900 -->

Für Education-Profile sind neue Einstellungen in der Kategorie **Drucker** unter **Drucker** > **Standarddrucker** > **Neue Drucker hinzufügen** verfügbar.

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>Anzeigen der Anrufer-ID im persönlichen Profil – Android for Work <!--1098984 -->
Wenn Sie ein persönliches Profil auf einem Gerät verwenden, sehen Endbenutzer möglicherweise nicht die Anrufer-ID-Details eines Arbeitskontakts. 

Seit diesem Update gibt es eine neue Einstellung unter **Android for Work** > **Geräteeinschränkungen** > **Arbeitsprofileinstellungen**:
- Anrufer-ID des Arbeitskontakts im persönlichen Profil anzeigen

Wenn aktiviert (nicht konfiguriert), werden die Anruferdetails des Arbeitskontakts im persönlichen Profil angezeigt. Wenn blockiert, wird die Anrufernummer des Arbeitskontakts im persönlichen Profil nicht angezeigt. 

Gilt für: Android-Arbeitsprofilgeräte unter Android OS 6.0 und höher.

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Neue Einstellungen für Windows Defender Credential Guard in den Endpoint Protection-Einstellungen <!--1102252 --><!--from 1802 and 1804-->

Mit diesem Update enthält [Windows Defender Central Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Gerätekonfiguration** > **Profile** > **Endpoint Protection**) die folgenden Einstellungen: 

- **Windows Defender Credential Guard**: Aktivieren des Credential Guards mit virtualisierungsbasierter Sicherheit. Wenn Sie dieses Feature aktivieren, können Sie Anmeldeinformationen beim nächsten Neustart schützen, wenn **Platform Security Level with Secure Boot** (Plattformsicherheitsstufe mit sicherem Start) und **Virtualization Based Security** (Virtualisierungsbasierte Sicherheit) aktiviert sind. Zu den Optionen gehören:
  - **Deaktiviert:** Wenn Credential Guard aktiviert war, mit aktivierter Option **Ohne Sperre aktiviert**, wird Credential Guard remote deaktiviert.

  - **Mit UEFI-Sperre aktivieren**: Gewährleistet, dass Credential Guard nicht mit einem Registrierungsschlüssel oder über eine Gruppenrichtlinie deaktiviert werden kann. Wenn Sie Credential Guard nach dem Aktivieren dieser Einstellung deaktivieren möchten, müssen Sie die Gruppenrichtlinie auf „Deaktiviert“ setzen. Entfernen Sie dann die Sicherheitsfunktionen von jedem Computer mit einem anwesenden Benutzer. Durch diese Schritte werden die in der UEFI vorgenommenen Konfigurationen gelöscht. Solange die UEFI-Konfiguration bestehen bleibt, ist Credential Guard weiter aktiviert.

  - **Ohne Sperre aktivieren**: Ermöglicht, Credential Guard über eine Remoteverbindung mithilfe einer Gruppenrichtlinie zu deaktivieren. Die Geräte, die diese Einstellung verwenden, müssen Windows 10 (Version 1511) oder höher ausführen.

Die folgenden, abhängigen Technologien werden automatisch aktiviert, wenn Sie Credential Guard konfigurieren: 

  - **Aktivieren der virtualisierungsbasierten Sicherheit (VBS:)** VBS wird beim nächsten Neustart aktiviert. Die virtualisierungsbasierte Sicherheit verwendet Windows Hypervisor, um die Sicherheitsdienste zu unterstützen, und erfordert einen sicheren Start.
  - **Sicherer Start mit direktem Speicherzugriff (Direct Memory Access, DMA)**: Aktiviert VBS mit Schutzmaßnahmen wie sicherem Start und direktem Speicherzugriff. Für die DMA-Schutzfunktion ist Hardwaresupport erforderlich. Außerdem ist sie nur auf ordnungsgemäß konfigurierten Geräten aktiviert. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Verwenden eines benutzerdefinierten Antragstellernames auf dem SCEP-Zertifikat <!-- 2064190 -->
Sie können den allgemeinen Namen **OnPremisesSamAccountName** für einen benutzerdefinierten Antragsteller auf einem SCEP-Zertifikatprofil verwenden. Sie können z. B. `CN={OnPremisesSamAccountName})` verwenden.

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Blockieren von Kamera und Bildschirmaufnahmen unter Android for Work <!-- 1098977 eeready-->
Es werden zwei neue Eigenschaften zum Blockieren beim Konfigurieren der Geräteeinschränkungen für Android-Geräte hinzugefügt: 
- Kamera: Der Zugriff auf alle Kameras auf dem Gerät wird blockiert.
- Bildschirmaufnahme: Die Bildschirmaufnahme wird blockiert,. Zudem wird verhindert, dass der Inhalt auf Anzeigegeräten angezeigt wird, die über keine sichere Videoausgabe verfügen.

Gilt für Android for Work.


### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Neue Schritte für die Registrierung für Benutzer auf Geräten mit macOS High Sierra 10.13.2 und höher <!--1734567 -->
Mit macOS high Sierra 10.13.2 wurde das Konzept der „vom Benutzer genehmigten“ MDM-Registrierung eingeführt. Intune kann mithilfe genehmigter Registrierungen einige sicherheitsrelevante Einstellungen verwalten. Weitere Informationen finden Sie in der Dokumentation zur Apple-Unterstützung: https://support.apple.com/HT208019.

Geräte, die mithilfe des macOS-Unternehmensportals registriert wurden, werden so lange als „nicht vom Benutzer genehmigt“ angesehen, bis der Endbenutzer sie in den Systemeinstellungen manuell genehmigt. Dafür werden Benutzer im macOS-Unternehmensportal unter macOS 10.13.2 und höher nun direkt aufgefordert, ihre Registrierung am Ende des Registrierungsprozesses manuell zu genehmigen. Die Intune-Administratorkonsole meldet, ob ein registriertes Gerät vom Benutzer genehmigt wurde.



### <a name="device-management"></a>Geräteverwaltung

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----eeready-1629303---"></a>Advanced Threat Protection (ATP) und Intune sind vollständig integriert <!-- EEready 1629303 -->

[Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) zeigt die Risikostufe von Windows 10-Geräten an. In Windows Defender Security Center (ATP-Portal) können Sie eine Verbindung mit Microsoft Intune herstellen. Nach der Erstellung wird mit einer Konformitätsrichtlinie von Intune eine akzeptable Bedrohungsstufe bestimmt. Wenn die Bedrohungsstufe überschritten wird, kann eine Azure Active Directory-Richtlinie (AD) für bedingten Zugriff den Zugriff auf andere Apps in Ihrer Organisation blockieren.

Dieses Feature ermöglicht ATP, Dateien zu überprüfen, Bedrohungen zu erkennen und jedes Risiko auf Ihren Windows 10-Geräten zu melden.

Siehe [Aktivieren von Windows Defender ATP mit bedingtem Zugriff in Intune](advanced-threat-protection.md).

#### <a name="support-for-user-less-devices----1637553---"></a>Unterstützung für Geräte ohne Benutzer <!-- 1637553 -->
Intune unterstützt die Möglichkeit, Konformität auf einem benutzerlosen Gerät zu bewerten, z.B. einem Microsoft Surface Hub-Gerät. Die Konformitätsrichtlinie kann sich auf bestimmte Geräte beziehen. Die Konformität (und auch Nichtkonformität) kann für Geräte festgelegt werden, die über keinen zugewiesenen Benutzer verfügen.

#### <a name="delete-autopilot-devices----1713650---"></a>Löschen von AutoPilot-Geräten <!-- 1713650 -->
Intune-Administratoren können [AutoPilot-Geräte löschen](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Verbesserte Erfahrung bei der Gerätelöschung <!--1832333 -->
Sie müssen nicht länger Unternehmensdaten entfernen oder das Gerät auf Werkseinstellungen zurücksetzen, bevor sie es [aus Intune löschen](devices-wipe.md#delete-devices-from-the-intune-portal).

Melden Sie sich für die neue Benutzererfahrung in Intune an, und wählen Sie **Geräte** > **Alle Geräte** > Name des Geräts > **Löschen** aus.

Wenn Sie die Bestätigung zum Zurücksetzen bzw. der Deaktivierung beibehalten möchten, können Sie die Standardvorgehensweise für den Gerätelebenszyklus verwenden, indem Sie vor der Option **Löschen** die Optionen **Entfernen von Unternehmensdaten** und **Auf Werkseinstellungen zurücksetzen** ausgeben. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Wiedergeben von Sound im Modus für verlorene Geräte <!-- 1947769 -->
Wenn sich überwachte iOS-Geräte im [Modus für verlorene Geräte](device-lost-mode.md) in MDM (Mobile Device Management, Verwaltung mobiler Geräte) befinden, können Sie [einen Sound wiedergeben](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Geräte** > **Alle Geräte** > iOS-Gerät auswählen > **Übersicht** > **More** (Mehr)). Der Sound wird so lange wiedergegeben, bis der Modus für verlorene Geräte beendet wird, oder bis der Benutzer den Sound auf dem Gerät deaktiviert. Gilt für Geräte unter iOS 9.3 und höher.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Blockieren und Zulassen von Webergebnissen in auf einem Intune-Gerät durchgeführten Suchvorgängen <!--1972804-->

Administratoren können jetzt Webergebnisse bei Suchvorgängen auf Geräten blockieren.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Verbesserte Fehlermeldungen bei Uploadfehlern für MDM-Pushzertifikate <!-- 2172331 -->

In der Fehlermeldung wird erklärt, dass dieselbe Apple-ID beim Erneuern eines vorhandenen MDM-Zertifikats verwendet werden muss.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Testen des Unternehmensportals für macOS auf virtuellen Computern <!-- 2216679 -->

Wir haben einen Leitfaden veröffentlicht, der IT-Administratoren beim Testen der Unternehmensportal-App für macOS auf VMs in Parallels Desktop und VMware Fusion unterstützt. Weitere Informationen finden Sie unter [Registrieren von virtuellen macOS-Computern zu Testzwecken](macos-enroll.md#enroll-virtual-macos-machines-for-testing).


### <a name="user-interface"></a>Benutzeroberfläche

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Die Gerätekacheln im Windows 10-Unternehmensportal wurden verbessert <!--2213364 -->

Die Kacheln wurden aktualisiert und sind jetzt zugänglicher für Benutzer mit eingeschränktem Sehvermögen. Die Leistung wurde für Bildschirmlesetools wurde verbessert.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Senden von Diagnoseberichten in der Unternehmensportal-App für macOS <!-- 2216677 -->
Die Unternehmensportal-App für macOS-Geräte wurde aktualisiert, um die Kundenerfahrung beim Melden von auf Intune bezogene Fehler zu verbessern. Ihre Mitarbeiter können über die Unternehmensportal-App folgende Aktionen durchführen:

- Hochladen von Diagnoseberichten direkt an das Microsoft-Entwicklerteam
- Die ID eines Vorfalls per E-Mail an das IT-Supportteams Ihres Unternehmens senden

Weitere Informationen finden Sie unter [Melden von macOS-Fehlern](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune wird an Fluent Design System in der Unternehmensportal-App für Windows 10 angepasst <!-- 1195010 WNready -->
Die Intune-Unternehmensportal-App für Windows 10 wurde mit der [Navigationsansicht von Fluent Design System](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics) aktualisiert. An der Seite der App befindet sich eine statische, vertikale Liste aller Seiten der obersten Ebene. Klicken Sie auf einen beliebigen Link, um Seiten schnell anzuzeigen und zwischen ihnen zu wechseln. Dies ist das erste von mehreren Updates, die wir Ihnen im Rahmen unserer fortlaufenden Bestrebungen präsentieren werden, die Intune-Benutzeroberfläche zu optimieren. Wenn Sie sehen möchten, wie die aktualisierte Benutzeroberfläche aussieht, wechseln Sie zur Seite [Updates der Benutzeroberfläche für Benutzer-Apps in Intune](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Woche vom 16. April 2018

#### <a name="use-cisco-anyconnect-client-for-ios----eeready-1333708---"></a>Verwenden des Cisco AnyConnect-Clients für iOS <!-- EEready 1333708 -->

Wenn Sie ein neues VPN-Profil für iOS erstellen, stehen Ihnen jetzt zwei Optionen zur Verfügung: **Cisco AnyConnect** und **Cisco Legacy AnyConnect**. Die Cisco AnyConnect-Profile unterstützen 4.0.7x und neuere Versionen. Bereits existierende iOS Cisco AnyConnect VPN-Profile werden als **Cisco Legacy AnyConnect** bezeichnet und auch weiterhin mit Cisco AnyConnect 4.0.5x und älteren Versionen funktionieren.

> [!NOTE]
> Diese Änderung gilt nur für iOS. Es wird weiterhin nur eine Option von Cisco AnyConnect für Android-, Android for Work- und macOS-Plattformen geben.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Jamf-registrierte macOS-Geräte können jetzt bei Intune registriert werden <!-- 2370684 -->

Die Versionen 1.3 und 1.4 des macOS-Unternehmensportals konnten nicht erfolgreich Jamf-Geräte bei Intune registrieren. Version 1.4.2 des macOS-Portals behebt dieses Problem.


## <a name="week-of-april-9-2018"></a>Woche vom 9. April 2018  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Aktualisierter Hilfebereich der Unternehmensportal-App für Android <!-- 1631531 -->

Wir haben den Hilfebereich der Unternehmensportal-App für Android aktualisiert, sodass er den Best Practices der Android-Plattform entspricht. Wenn Benutzer jetzt ein Problem in der App haben, können sie auf **Menü** > **Hilfe** tippen und Folgendes tun:
- Diagnoseprotokolle an Microsoft senden
- E-Mail, die das Problem beschreibt, und die Incident-ID an einen Supportmitarbeiter des Unternehmens senden  

Unter [Senden von Protokollen an den Support Ihres Unternehmens per E-Mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android) und [Senden von Protokollen an Unternehmensportalentwickler für Android-Geräte](/intune-user-help/send-logs-to-microsoft-android) können Sie den aktualisierten Hilfebereich kennenlernen.


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Neues Diagramm zum Trend von fehlgeschlagenen Registrierungen und Tabelle mit Gründen für das Fehlschlagen <!-- 1471783 -->

Auf der Seite „Enrollment Overview“ (Registrierungsübersicht) können Sie sich den Trend bei fehlgeschlagenen Registrierungen und die fünf häufigsten Gründe für das Fehlschlagen anzeigen lassen. Wenn Sie auf das Diagramm oder die Tabelle klicken, können Sie sich im Detail Informationen zu den Fehlern ansehen und erhalten Ratschläge zur Fehlerbehebung und zur Wartung.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Update zum Konfigurieren der App-Schutzrichtlinien <!-- 2144597 -->

Sie werden in Microsoft Intune im Azure-Portal kurzzeitig von dem Dienstblatt **Intune-Schutz für Apps** auf das Blatt **Mobile App** umgeleitet. Beachten Sie, dass alle Ihre App-Schutzrichtlinien bereits auf dem Blatt **Mobile App** in Intune unter der App-Konfiguration vorhanden sind. Statt Intune-App-Schutz aufzurufen, verwenden Sie einfach Intune. Im April 2018 beenden wir die Umleitung und entfernen das Dienstblatt **Intune-App-Schutz** vollständig, sodass es nur einen Ort für App-Richtlinien in Intune gibt. 

**Wie wirkt sich das auf mich aus?**
Sowohl eigenständige Intune-Kunden als auch hybride Kunden (die Intune mit Configuration Manager verwenden) sind von dieser Änderung betroffen. Diese Integration soll Ihre Cloudverwaltung vereinfachen.

**Was muss ich als Vorbereitung auf diese Änderung tun?**
Markieren Sie **Intune** und nicht das Dienstblatt **Intune-Schutz für Apps** als Favorit, und machen Sie sich in Intune mit dem Richtlinienworkflow für den App-Schutz auf der Blatt **Mobile App** vertraut. Es wird zwar für einen kurzen Zeitraum eine Umleitung eingerichtet, aber danach wird das Blatt **Intune-Schutz für App** entfernt. Beachten Sie, dass alle Richtlinien zum App-Schutz bereits in Intune verschoben wurden und Sie Ihre Richtlinien für den bedingten Zugriff ändern können. Weitere Informationen zum Ändern von Richtlinien für bedingten Zugriff finden Sie unter [Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Weitere Informationen finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>Woche vom 2. April 2018

### <a name="intune-apps"></a>Intune-Apps

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Update der Benutzeroberfläche für die Unternehmensportal-App für iOS <!--1412866 -->
Für die Unternehmensportal-App für iOS wurde ein großes Update für die Benutzeroberfläche veröffentlicht. Das Update enthält eine vollständige visuelle Überarbeitung, einschließlich eines moderneren Designs und einer verbesserten Handhabung. Wir haben die Funktion der App beibehalten, haben jedoch die Benutzerfreundlichkeit und Barrierefreiheit verbessert.  

Weiterhin sind enthalten:
- Support für iPhone X
- Schnellerer App-Start und Reaktionszeiten, damit Benutzer Zeit sparen
- Zusätzliche Statusanzeigen, damit Benutzer stets mit den neuesten Statusinformationen versorgt sind
- Verbesserungen beim Uploadprozess von Protokollen. Wenn Sie also auf ein Problem stoßen, können Sie es viel einfacher melden.  

Wenn Sie sehen möchten, wie die aktualisierte Benutzeroberfläche aussieht, wechseln Sie zur Seite [Updates der Benutzeroberfläche für Benutzer-Apps in Intune](whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Schützen der lokalen Exchange-Daten mithilfe von Intune-App-Schutzrichtlinien und dem bedingten Zugriff <!-- 1056954 -->
Sie können jetzt lokale Exchange-Daten mit Outlook Mobile mithilfe von Intune App-Schutzrichtlinien (App Policy Protection, APP) und dem bedingten Zugriff (Conditional Access, CA) schützen. Um eine App-Schutzrichtlinie im Azure-Portal hinzuzufügen oder zu ändern, klicken Sie auf **Microsoft Intune** > **Mobile Apps** > **App-Schutzrichtlinien**. Bevor Sie dieses Feature verwenden, sollten Sie sicherstellen, dass Sie die [Anforderungen für Outlook für iOS und Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx) erfüllen.

## <a name="week-of-march-26-2018"></a>Woche vom 26. März 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Benachrichtigungen zu ablaufenden branchenspezifischen iOS-Apps für Microsoft Intune <!-- 748789 -->

Im Azure-Portal werden Sie von Intune über ablaufende branchenspezifische iOS-Apps benachrichtigt. Beim Hochladen einer neuen Version der branchenspezifischen iOS-App entfernt Intune die Ablaufbenachrichtigung aus der Liste. Diese Ablaufbenachrichtigung ist nur für neu hochgeladene branchenspezifische iOS-Apps aktiviert und wird 30 Tage vor Ablauf des Bereitstellungsprofils der branchenspezifischen iOS-App angezeigt. Wenn es abgelaufen ist, ändert sich die Benachrichtigung in „Abgelaufen“.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Anpassen des Unternehmsportaldesigns mit Hexadezimalcode <!--1049561 -->

Die Designfarben lassen sich in den Unternehmensportal-Apps mithilfe von Hexadezimalcode anpassen. Wenn Sie Ihren Hexadezimalcode eingeben, legt Intune fest, welche Textfarbe den stärksten Kontrast zur Hintergrundfarbe bildet. In einer Vorschau können Sie die Textfarbe und das Unternehmenslogo mit den Farben unter **Mobile Apps** > **Unternehmensportal** abgleichen.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Ein- und Ausschließen von App-Zuweisungen basierend auf Gruppen für Android Enterprise <!-- 1813081 -->

Android Enterprise (zuvor Android for Work) unterstützt das Einschließen und Ausschließen von Gruppen, jedoch nicht die vorab erstellte Gruppe **Alle Benutzer** und die integrierte Gruppe **Alle Geräte**. Weitere Informationen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](apps-inc-exl-assignments.md).


### <a name="device-management"></a>Geräteverwaltung

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Neue Sicherheitserweiterungen für Intune <!-- 1637539 -->   

Wir haben in Intune in Azure eine Umschaltfläche eingeführt, mit der eigenständige Intune-Kunden Geräte ohne zugewiesene Richtlinien als **Konform** (Sicherheitsfeature deaktiviert) oder **Nicht konform** (Sicherheitsfeature aktiviert) einstufen können. So wird sichergestellt, dass erst nach der Auswertung der Gerätekonformität Zugriff auf Ressourcen besteht.

Die Auswirkungen dieses Features auf Sie sind davon abhängig, ob Sie bereits Konformitätsrichtlinien zugewiesen haben oder nicht.

- Wenn Sie über ein neues oder bereits bestehendes Konto verfügen und Ihren Geräten bislang noch keine Konformitätsrichtlinien zugewiesen sind, wird die Umschaltfläche automatisch auf **Konform** festgelegt. Das Feature ist in der Konsole standardmäßig deaktiviert. Daher hat es keine Auswirkungen auf Benutzer.
- Wenn Sie bereits ein vorhandenes Konto haben und über Geräte verfügen, denen eine Konformitätsrichtlinie zugewiesen ist, wird die Umschaltfläche automatisch auf **Nicht konform** festgelegt. Ab der Bereitstellung des März-Updates ist dieses Feature standardmäßig aktiviert.

Wenn Sie Konformitätsrichtlinien mit bedingtem Zugriff verwenden und das Feature aktiviert ist, wird jedes Gerät blockiert, dem nicht mindestens eine Konformitätsrichtlinie zugewiesen ist. Benutzern, die diesen Geräten zugeordnet sind und zuvor auf E-Mails zugreifen konnten, können dies nicht mehr, wenn Sie nicht allen Geräten mindestens eine Konformitätsrichtlinie zuweisen.   

Beachten Sie, dass der Standardstatus der Umschaltfläche ab dem Update vom März für Intune zwar in der Benutzeroberfläche angezeigt wird, jedoch nicht sofort durchgesetzt wird. Alle Änderungen, die Sie an der Einstellung der Umschaltfläche vornehmen, wirken sich nicht auf die Gerätekonformität aus, bis die Umschaltfläche für Ihr Konto aktiviert wird. Wir informieren Sie über das Nachrichtencenter, wenn dieser Vorgang abgeschlossen ist. Dies kann nach dem Update des Intune-Diensts vom März ein paar Tage dauern.

**Weitere Informationen**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>Verbesserte Erkennung von Jailbreaks <!-- 846515 -->

Die verbesserte Erkennung von Jailbreaks ist eine neue Konformitätseinstellung, die in Intune die Auswertung von Geräten mit Jailbreaks verbessert. Durch die Einstellung verbindet sich das Gerät häufiger mit Intune. Dazu wird der Ortungsdienst des Geräts benötigt, was Auswirkungen auf den Akkuverbrauch hat.

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Zurücksetzen von Kennwörtern für Android O-Geräte <!-- 1238299 -->
Sie können die Kennwörter für registrierte Android 8.0-Geräte mit Arbeitsprofilen zurücksetzen. Wenn Sie die Anforderung „Kennwort zurücksetzen“ an ein Android 8.0-Gerät senden, legt dieses ein neues Kennwort zum Entsperren des Geräts oder eine verwaltete Profilabfrage für den aktuellen Benutzer fest. Das Kennwort oder die Abfrage wird gesendet und wird sofort wirksam.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Ausrichten von Konformitätsrichtlinien auf Geräte in Gerätegruppen <!--1307012 -->

Sie können Konformitätsrichtlinien gezielt für Benutzer in Benutzergruppen erstellen. Mit diesem Update können Sie auch Konformitätsrichtlinien gezielt für Geräte in Gerätegruppen erstellen. Geräte in solchen Gerätegruppen empfangen keine Konformitätsaktionen.

#### <a name="new-management-name-column----1333586---"></a>Namensspalte „New Management“ <!-- 1333586 -->
 Im Blatt „Geräte“ ist eine neu Spalte namens **Verwaltungsname** verfügbar. Dies ist ein automatisch generierter und nicht bearbeitbarer Name, der basierend auf der folgenden Formel vom Gerät zugewiesen wird:
- Standardname für alle Geräte: <username><em><devicetype></em><enrollmenttimestamp>
- Für Geräte, die durch Massenhinzufügen hinzugefügt wurden: <PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

Dies ist eine optionale Spalte im Blatt „Geräte“. Sie ist nicht standardmäßig, sondern nur über die Spaltenauswahl verfügbar. Diese neue Spalte hat keine Auswirkungen auf den Gerätenamen.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>iOS-Geräte werden alle 15 Minuten zur Eingabe einer PIN aufgefordert <!--1550837 -->
Nachdem einem iOS-Gerät eine Konformitäts- oder Konfigurationsrichtlinie hinzugefügt wurde, werden Benutzer alle 15 Minuten dazu aufgefordert, eine PIN festzulegen. Diese Aufforderung erhalten Benutzer regelmäßig, bis sie eine PIN festlegen.

#### <a name="schedule-your-automatic-updates---1805514---"></a>Planen von automatischen Updates <!--1805514 -->
Mit Intune können Sie die Installation von automatischen Updates mithilfe von [Einstellungen für Windows-Updateringe](windows-update-for-business-configure.md) steuern. Seit diesem Update können Sie sich wiederholende Updates planen, einschließlich der Woche, dem Tag und der Uhrzeit.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>Verwenden eines vollständig definierten Namens als Antragsteller für das SCEP-Zertifikat <!--2221763 -->
Wenn Sie ein SCEP-Zertifikatsprofil erstellen, geben Sie den Antragstellernamen ein. Seit diesem Update können Sie den vollständig definierten Namen als Antragstellernamen verwenden. Wählen Sie für **Antragstellername** die Option **benutzerdefiniert** aus, und geben Sie dann `CN={{OnPrem_Distinguished_Name}}` ein. Damit Sie die `{{OnPrem_Distinguished_Name}}`-Variable verwenden können, stellen Sie sicher, dass das `onpremisesdistingishedname`-Benutzerattribut mithilfe von [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) mit Azure AD synchronisiert ist.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Aktivieren der Kontaktfreigabe über Bluetooth: Android for Work <!--1098983 -->
In der Standardeinstellung verhindert Android, dass Kontakte im Arbeitsprofil mit Bluetooth-Geräten synchronisiert werden. Das Ergebnis ist, dass Arbeitsprofilkontakte nicht auf der Anrufer-ID für Bluetooth-Geräte angezeigt werden.

Seit diesem Update gibt es eine neue Einstellung unter **Android for Work** > **Geräteeinschränkungen** > **Arbeitsprofileinstellungen**:
- Kontaktfreigabe über Bluetooth

Der Intune-Administrator kann diese Einstellungen konfigurieren, um die Freigabe zu aktivieren. Dieses Feature ist nützlich, wenn Sie ein Gerät mit einem Bluetooth-Gerät in einem Fahrzeug koppeln möchten, das die Anrufer-ID für Freisprechgeräte anzeigt. Wenn das Feature aktiviert ist, werden Arbeitsprofilkontakte angezeigt. Wenn das Feature nicht aktiviert ist, werden Arbeitsprofilkontakte nicht angezeigt.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>Konfigurieren von Gatekeeper zum Steuern der Downloadquelle der macOS-App <!-- 1690459 -->

Sie können Gatekeeper konfigurieren und Ihre Geräte schützen, indem Sie steuern, von wo die Apps heruntergeladen werden können. Sie können die folgenden Downloadquellen konfigurieren: **Mac App Store**, **Mac App Store und verifizierte Entwickler** und **Anywhere** (Alle Quellen). Außerdem können Sie konfigurieren, dass Benutzer eine App mithilfe von STRG+Klick installieren können, um diese Gatekeeper-Steuerelemente außer Kraft zu setzen.

Diese Einstellungen finden Sie unter **Gerätekonfiguration** -> **Profil erstellen** -> **macOS** -> **Endpoint Protection**.

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Konfigurieren der Firewall der Mac-Anwendung <!-- 1690461 -->

Sie können die Firewall der Mac-Anwendung konfigurieren. Damit können Sie Verbindungen auf einer „pro Anwendung“-Basis anstatt einer „per Port“-Basis steuern. Dies erleichtert es Ihnen, die Vorteile des Firewall-Schutzes zu nutzen und zu verhindern, dass unerwünschte Apps die Kontrolle über für zulässige Apps offenen Netzwerk-Ports übernehmen.

Dieses Feature kann unter **Gerätekonfiguration** -> **Profil erstellen** -> **macOS** -> **Endpoint Protection**.

Nachdem Sie die Firewall-Einstellung aktivieren, können Sie die Firewall mithilfe von zwei Strategien konfigurieren:

- Blockieren von allen eingehenden Verbindungen

   Sie können alle eingehenden Verbindungen für die Zielgeräte blockieren. Wenn Sie sich dazu entscheiden, werden eingehende Verbindungen für alle Apps blockiert.

- Zulassen oder Blockieren von bestimmten Apps

   Sie können den Empfang von eingehenden Verbindungen für bestimmte Apps zulassen oder blockieren. Sie können auch den geschützten Modus aktivieren, um zu verhindern, dass der Computer auf Suchanforderungen reagiert.

####  <a name="detailed-error-codes-and-messages----1376342---"></a>Detaillierte Fehlercodes und Meldungen <!-- 1376342 -->

In Ihrer Gerätekonfiguration werden jetzt ausführlichere Fehlercodes und Fehlermeldungen angezeigt. Diese verbesserte Berichterstellung zeigt die Einstellungen, den Status dieser Einstellungen und Details zur Problembehandlung an.

##### <a name="more-information"></a>Weitere Informationen

- Blockieren von allen eingehenden Verbindungen

   Dadurch wird verhindert, dass alle Freigabedienste (z.B. Dateifreigabe und Bildschirmfreigabe) eingehende Verbindungen empfangen. Die folgenden Systemdienste sind noch zum Empfangen von eingehenden Verbindungen zugelassen:
  - configd - implementiert DHCP und andere Netzwerkkonfigurationsservices
  - mDNSResponder - implementiert Bonjour
  - racoon -  implementiert IPSec

    Stellen Sie sicher, dass **Eingehende Verbindungen** auf **Nicht konfiguriert** (und nicht auf **Block** (Blockieren)) festgelegt ist, um Freigabedienste zu verwenden.

- Geschützter Modus

   Aktivieren Sie diese Option, um den Computer daran zu hindern, auf Suchanforderungen zu reagieren. Der Computer antwortet weiterhin auf eingehende Anforderungen von autorisierten Apps. Unerwartete Anforderungen, wie z.B. ICMP (Ping), werden ignoriert.

#### <a name="disable-checks-on-device-restart---1805490---"></a>Deaktivieren von Prüfungen bei Geräteneustart <!--1805490 -->
Mit Intune können Sie die [Verwaltung von Softwareupdates]](windows-update-for-business-configure.md) steuern. Seit diesem Update ist die Eigenschaft <strong>Neustartüberprüfungen</strong> verfügbar und standardmäßig aktiviert. Wählen Sie <strong>Überspringen</strong> aus, um die üblichen Überprüfungen zu überspringen, wenn Sie ein Gerät neu starten (z.B. aktive Benutzer, Akkustand usw.).

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>Neue Windows 10 Insider Preview-Kanäle für Bereitstellungsringe verfügbar <!-- 1746293 -->
Sie haben von nun an die Möglichkeit, zwischen den folgenden Windows 10 Insider Preview-Wartungskanälen zu wählen, wenn Sie einen Windows 10-Bereitstellungsring erstellen:
- Windows-Insider-Build: schnell
- Windows-Insider-Build: langsam
- Windows-Insider-Build veröffentlichen 

Weitere Informationen zu diesen Kanälen finden Sie unter [Verwalten von Insider Preview-Builds](https://insider.windows.com/en-us/for-business-organization-admin/).   
Weitere Informationen zum Erstellen von Bereitstellungskanälen in Intune finden Sie unter [Verwalten von Softwareupdates](windows-update-for-business-configure.md).

### <a name="intune-apps"></a>Intune-Apps

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>Verbesserte Unternehmensportal-Registrierung <!-- 1874230 eeready-->
Benutzer, die ein Gerät mithilfe des Unternehmensportals unter Windows 10-Version 1703 oder höher registrieren, können den ersten Registrierungsschritt jetzt innerhalb der App ausführen.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens und Surface Hub erscheinen nun in Gerätelisten <!--1725868 -->
Die Anzeige von über Intune registrierten HoloLens- und Surface Hub-Geräten in der Unternehmensportal-App wird jetzt unter Android unterstützt.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>Benutzerdefinierte Buchkategorien für eBooks im Volume Purchase Program (VPP) <!-- 1488911 -->
Sie können benutzerdefinierte eBook-Kategorien erstellen und diesen dann per Volumenlizenz erworbene eBooks zuweisen. Endbenutzer können dann die neu erstellten eBook-Kategorien und den Kategorien zugewiesene Bücher sehen. Weitere Informationen finden Sie unter [Verwalten von per Volumenlizenz erworbenen Apps und Büchern mit Microsoft Intune](vpp-apps.md).  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>Änderungen der Unterstützung der Option „Feedback senden“ in der Unternehmensportal-App für Windows <!-- 2070166 -->
Ab dem 30. April 2018 funktioniert die Option **Feedback senden** in der Unternehmensportal-App für Windows nur noch auf Geräten, auf denen das Windows 10 Anniversary Update (1607) und höher ausgeführt wird. Die Option zum Senden von Feedback wird bei Verwendung der Unternehmensportal-App für Windows unter folgenden Versionen nicht mehr unterstützt:  
- Windows 10, Version 1507  
- Windows 10, Version 1511  
- Windows Phone 8.1 

Wenn Ihr Gerät unter Windows 10 RS1 oder höher ausgeführt wird, können Sie die neueste Version der Windows-Unternehmensportal-App aus dem Store herunterladen. Bei Ausführung einer nicht unterstützten Version können Sie uns über die folgenden Kanäle weiterhin Feedback senden: 
- Die Feedback-Hub-App unter Windows 10
- E-Mail an WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Neue Einstellungen für Windows Defender Application Guard <!-- 1631890 -->

- **Enable graphics acceleration** (Grafikbeschleunigung aktivieren): Administratoren können einen virtuellen Grafikprozessor für Windows Defender Application Guard aktivieren. Über diese Einstellung kann die CPU Grafiken auslagern, die an die vGPU rendern. Dadurch kann die Leistung verbessert werden, wenn Sie mit grafikintensiven Websites arbeiten oder ein Video im Container ansehen.

- **SaveFilestoHost**: Administratoren können konfigurieren, dass Dateien des Browsers „Microsoft Edge“, der im Container ausgeführt wird, an das Hostdateisystem übergeben werden. Wenn Sie diese Einstellung aktivieren, können Benutzer Dateien von Microsoft Edge im Container auf das Hostdateisystem herunterladen.

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>Anwenden von MAM-Richtlinien je nach Verwaltungsstatus <!-- 1665993 -->
Sie können MAM-Richtlinien je nach Verwaltungsstatus des Geräts anwenden:
- **Android-Geräte:** Sie können Richtlinien auf nicht verwaltete Geräte, mit Intune verwaltete Geräte und mit Intune verwaltete Android Enterprise-Profile (früher Android for Work) anwenden.
- **iOS-Geräte:** Sie können Richtlinien auf nicht verwaltete Geräte (nur MAM) oder von Intune verwaltete Geräte anwenden.

    > [!NOTE]
    > - iOS-Unterstützung für diese Funktion wird im April 2018 eingeführt.

Weitere Informationen finden Sie unter [Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Sprachverbesserungen in der Unternehmensportal-App für Windows <!-- 1683758 -->
Die Sprache im Unternehmensportal für Windows 10 wurde verbessert und ist nun benutzerfreundlicher und unternehmensspezifischer. Unter [Updates der Benutzeroberfläche für Benutzer-Apps in Intune](whats-new-app-ui.md) finden Sie einige Beispielabbildungen der Neuerungen.

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>Neue Datenschutzfunktionen in Dokumenten für Benutzer <!-- 1440709 -->
Wir arbeiten daran, Benutzern mehr Kontrolle über ihre Daten und den Datenschutz zu geben. Daher haben wir Updates für unsere Dokumente veröffentlicht, in denen erklärt wird, wie Sie von den Unternehmensportal-Apps lokal gespeicherte Daten anzeigen und entfernen. Sie finden diese Updates in den folgenden Quellen:

- **Android:** [Entfernen der Registrierung Ihres Android-Geräts bei Intune](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **Android, wenn der Benutzer die Nutzungsbedingungen abgelehnt hat:** [Remove your device management if you declined „Terms of Use“ (Entfernen der Geräteverwaltung, wenn die Nutzungsbedingungen abgelehnt wurden)](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS:** [Entfernen Ihres iOS-Geräts aus Intune](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows:** [Entfernen Ihres Windows-Geräts aus Intune](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## <a name="week-of-march-19-2018"></a>Woche vom 19. März 2018

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>Exportieren aller Geräte in CSV-Dateien in Internet Explorer, Edge oder Chrome <!-- 2258071 -->
Unter **Geräte** > **Alle Geräte** können Sie die Geräte mithilfe der Option **Exportieren** in eine CSV-formatierte Liste exportieren. Internet Explorer-Benutzer mit mehr als 10.000 Geräten können ihre Geräte in mehrere Dateien exportieren. Jede Datei verfügt über bis zu 10.000 Geräte.

Edge- und Chrome-Benutzer mit mehr als 30.000 Geräten können ihre Geräte ebenfalls in mehrere Dateien exportieren. Jede Datei verfügt dann über bis zu 30.000 Geräte.

Über die Option [Geräte verwalten](device-management.md) erhalten Sie weitere Informationen dazu, wie Sie die verwalteten Geräte verwenden können.

## <a name="week-of-march-12-2018"></a>Woche vom 12. März 2018

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory-Websites können die App „Intune Managed Browser“ erfordern und unterstützen das einmalige Anmelden dafür (Public Preview) <!-- 710595 -->

Mithilfe von Azure Active Directory (Azure AD) können Sie jetzt den Zugriff auf Websites auf mobilen Geräten auf die Intune Managed Browser-App beschränken. In Managed Browser bleiben die Websitedaten sicher und getrennt von den persönlichen Daten des Benutzers. Zusätzlich unterstützt der Managed Browser die Funktionen für einmaliges Anmelden für Websites, die von Azure AD geschützt werden. Das Anmelden beim Managed Browser oder das Verwenden desselben auf einem Gerät mit einer anderen App, die von Intune verwaltet wird, ermöglicht es dem Managed Browser, auf Unternehmenswebsites zuzugreifen, die von Azure AD geschützt werden, ohne dass der Benutzer seine Anmeldeinformationen eingeben muss. Diese Funktion gilt für Websites wie Outlook Web Access (OWA) und SharePoint Online sowie für andere Unternehmenswebsites wie Intranetressourcen, auf die über den Azure-App-Proxy zugegriffen wird. Weitere Informationen finden Sie unter [Access controls in Azure Active Directory conditional access (Zugriffsteuerung über den bedingten Zugriff für Azure Active Directory)](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Unternehmensportal-App für visuelle Android-Updates <!--976944 -->

Die Unternehmensportal-App wird für Android aktualisiert, um den [Material Design](https://material.io/)-Richtlinien von Android zu entsprechen. Bilder der neuen Symbole finden Sie im Artikel zu den [Neuerungen der App-Benutzeroberfläche](whats-new-app-ui.md).

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>Neue Einstellungen für Windows Defender Exploit Guard <!-- 1631893 -->

Es sind jetzt sechs neue Einstellungen zur <strong>Verringerung der Angriffsfläche</strong> und erweiterte Funktionen zum <strong>Überwachten Ordnerzugriff: Ordnerschutz</strong> verfügbar. Diese Einstellungen finden Sie unter: Gerätekonfiguration\Profiles\
Erstellen Sie profile\Endpoint Protection\Windows Defender Exploit Guard.

#### <a name="attack-surface-reduction"></a>Verringerung der Angriffsfläche

|Name der Einstellung  |Einstellungsoptionen  |Beschreibung  |
|---------|---------|---------|
|Erweiterter Schutz vor Ransomware|Enabled, Audit, Not configured (Aktiviert, Überwachung, Nicht konfiguriert)|Verwendung eines offensiven Schutzes vor Ransomware.|
|Flag credential stealing from the Windows local security authority subsystem (Abgreifen von Anmeldeinformationen über das Subsystem der lokalen Sicherheitsautorität von Windows kennzeichnen)|Aktiviert, Überwachung, Nicht konfiguriert|Flag credential stealing from the Windows local security authority subsystem (lsass.exe) (Abgreifen von Anmeldeinformationen über das Subsystem zur lokalen Sicherheitsautorität von Windows kennzeichnen (lsass.exe)).|
|Process creation from PSExec and WMI commands (Prozesserstellung über die Befehle „PSExec“ und „WMI“)|Blockieren, Überwachung, Nicht konfiguriert|Blockiert Prozesserstellungen über die Befehle „PSExec“ und „WMI“.|
|Untrusted and unsigned processes that run from USB (Nicht vertrauenswürdige und nicht signierte Prozesse, die über USB ausgeführt werden)|Blockieren, Überwachung, Nicht konfiguriert|Blockiert nicht vertrauenswürdige und nicht signierte Prozesse, die über USB ausgeführt werden.|
|Executables that don’t meet a prevalence, age, or trusted list criteria (Ausführbare Dateien, die keinem Listenkriterium zur Verbreitung, zum Alter oder zur Vertrauenswürdigkeit entsprechen)|Blockieren, Überwachung, Nicht konfiguriert|Blockiert das Ausführen ausführbarer Dateien, wenn sie keinem Listenkriterium zur Verbreitung, zum Alter oder zur Vertrauenswürdigkeit entsprechen.|

#### <a name="controlled-folder-access"></a>Überwachter Ordnerzugriff

|              Name der Einstellung               |                                                              Einstellungsoptionen                                                              | Beschreibung |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Ordnerschutz (bereits implementiert) | Nicht konfiguriert, Aktivieren, Nur Überwachung (bereits implementiert)<br><br> <strong>Neu</strong><br>Blockieren der Änderung des Datenträgers, Überwachung der Änderung des Datenträgers |             |

Hiermit schützen Sie Dateien und Ordner vor unbefugten Änderungen durch bösartige Apps.<br><br>**Aktivieren:** Vermeiden Sie, dass nicht vertrauenswürdige Apps Dateien in geschützten Ordnern verändern oder löschen und in Datenträgersektoren schreiben.<br><br>
**Nur die Änderung des Datenträgers blockieren**:<br>Blockiert, dass nicht vertrauenswürdige Apps in Datenträgersektoren schreiben. Nicht vertrauenswürdige Apps können weiterhin Dateien in geschützten Ordnern verändern oder löschen.

## <a name="week-of-february-19-2018"></a>Woche vom 19. Februar 2018

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune-Unterstützung für mehrere Apple DEP-/Apple School Manager-Konten <!-- 747685 -->

Intune unterstützt jetzt die Registrierung von Geräten mit bis zu 100 verschiedenen [Apple DEP-Konten](device-enrollment-program-enroll-ios.md) (Device Enrollment Program = Programm zur Geräteregistrierung) oder [Apple School Manager](apple-school-manager-set-up-ios.md)-Konten. Jedes Token kann separat für Registrierungsprofile und Geräte hochgeladen und verwaltet werden. Jedem hochgeladenen DEP-/School Manager-Token kann automatisch ein separates Registrierungsprofil zugewiesen werden. Wenn mehrere School Manager-Token hochgeladen werden, kann mit der Microsoft-Synchronisierung von Schul-/Unidaten jeweils nur ein Token freigegeben werden.

Nach der Migration funktionieren die Betaversionen der Graph-APIs und veröffentlichten Skripts zur Verwaltung von Apple DEP oder ASM über Graph nicht mehr. Neue Betaversionen der Graph-APIs sind in der Entwicklung und werden nach der Migration veröffentlicht.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Anzeigen von Registrierungseinschränkungen pro Benutzer <!-- 1634444 eeready wnready -->
Auf dem Blatt **Problembehandlung** sehen Sie nun die [Registrierungseinschränkungen](enrollment-restrictions-set.md), die für jeden Benutzer gelten, wenn Sie in der Liste **Zuweisungen** auf **Registrierungseinschränkungen** klicken.

### <a name="device-management"></a>Geräteverwaltung
#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Berichte zum Integritäts- und Bedrohungsstatus von Windows Defender <!--854704 -->

Ein grundlegendes Verständnis zur Integrität und zum Status von Windows Defender ist wichtig, damit Sie Windows-Computer verwalten können.  Mit diesem Update fügt Intune dem Status und der Integrität des Windows Defender-Agents neue Berichte und Aktionen hinzu. Wenn Sie einen Bericht zum Status des Rollups in der [Workload „Gerätekonformität“](compliance-policy-monitor.md) verwenden, werden Ihnen Geräte angezeigt, für die einer der folgenden Vorgänge erforderlich ist:
- Signaturupdate
- Neu starten
- Benutzereingriff
- vollständige Überprüfung
- andere Agent-Status, die einen Eingriff erfordern

In einem Drillthroughbericht für sämtliche Statuskategorien werden sowohl die einzelnen Computer aufgeführt, die überprüft werden sollten, als auch die, die als **Clean** (Bereinigt) eingestuft werden.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Neue Datenschutzeinstellungen für Gerätebeschränkungen <!--1308926 -->
Es sind jetzt [zwei neue Datenschutzeinstellungen](device-restrictions-windows-10.md#privacy) für Geräte verfügbar:
- **Benutzeraktivitäten veröffentlichen:** Legen Sie diese Einstellung auf **Blockieren** fest, um geteilte Aktivitäten und die Ermittlungen von kürzlich verwendeten Ressourcen in der Programmumschaltung zu vermeiden.
- **Nur lokale Aktivitäten:** Legen Sie diese Einstellungen auf **Blockieren** fest, um geteilte Aktivitäten und Ermittlungen von kürzlich in der Programmumschaltung verwendeten Ressourcen anhand von ausschließlich lokalen Aktivitäten zu vermeiden.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Neue Einstellungen für den Browser Microsoft Edge <!--1469166 -->
Für Geräte, auf denen Microsoft Edge installiert ist, sind [zwei neue Einstellungen](device-restrictions-windows-10.md#edge-browser) verfügbar: **Path to favorites file** (Pfad zu häufig verwendeten Dateien) und **Changes to Favorites** (Änderungen an Favoriten).

### <a name="app-management"></a>App-Verwaltung
#### <a name="protocol-exceptions-for-applications---1035509---"></a>Protokollausnahmen für Anwendungen <!--1035509 -->

Sie können Ausnahmen für die Richtlinie zur Datenübertragung über die Verwaltung mobiler Anwendungen (MAM) mit Intune erstellen, um bestimmte nicht verwaltete Anwendungen zu öffnen. Diese Anwendungen müssen von der IT-Abteilung als vertrauenswürdig eingestuft werden. Entgegen der von Ihnen erstellten Ausnahmen ist die Datenübertragung immer noch auf Anwendungen beschränkt, die von Intune verwaltet werden, wenn Ihre Richtlinie zur Datenübertragung immer noch auf **managed apps only** (nur verwaltete Apps) festgelegt ist. Sie können die Einschränkungen mithilfe von Protokollen (unter iOS) oder Paketen (unter Android) erstellen.

Sie können beispielsweise das Webex-Paket als Ausnahme für die Richtlinie zur MAM-Datenübertragung hinzufügen. Dann ist es erlaubt, Webex-Links in einer verwalteten Outlook-E-Mail direkt über die Webex-Anwendung zu öffnen. In anderen nicht verwalteten Anwendungen ist die Datenübertragung dann aber immer noch eingeschränkt. Weitere Informationen finden Sie unter [Ausnahmen von der Datenübertragungsrichtlinie für Apps](app-protection-policies-exception.md).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Mit Windows Information Protection (WIP) verschlüsselte Daten in Windows-Suchergebnissen <!-- 1469193 -->
Mit einer neuen Einstellung in der WIP-Richtlinie (Windows Information Protection) können Sie nun steuern, ob mit WIP verschlüsselte Daten in den Windows-Suchergebnissen enthalten sind. Legen Sie diese App-Schutzrichtlinienoption auf **Der Windows Search-Indexerstellung die Suche nach verschlüsselten Elementen gestatten** in den **Erweiterten Einstellungen** der Windows Information Protection-Richtlinie fest. Die App-Schutzrichtlinie muss auf die *Windows 10*-Plattform und die App-Richtlinie **Registrierungsstatus** auf **Mit Registrierung** festgelegt werden. Weitere Informationen finden Sie unter [Der Windows Search-Indexerstellung die Suche nach verschlüsselten Elementen gestatten](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Konfigurieren einer mobilen MSI-App, die sich selbst aktualisiert <!-- 1740840 -->
Sie können eine bekannte mobile MSI-App konfigurieren, die sich selbst aktualisiert, um den Prozess der Versionsüberprüfung zu ignorieren. Diese Einstellung ist nützlich, um Racebedingungen zu vermeiden. Diese Art von Racebedingungen kann z.B. auftreten, wenn die App vom Entwickler automatisch aktualisiert wird, gleichzeitig aber auch von Intune ein Update ausgeführt wird. Beide könnten dann eine Version der App auf dem Windows-Client erzwingen, was einen Konflikt auslösen kann. Für diese automatisch aktualisierten MSI-Apps können Sie die Einstellung **App-Version ignorieren** auf dem Blatt **App-Informationen** konfigurieren. Wenn diese Einstellung auf **Ja** festgelegt wird, ignoriert Microsoft Intune die App-Version, die auf dem Windows-Client installiert ist.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Verwandte App-Lizenzen, die in Intune unterstützt werden <!-- 1864117 -->
Intune im App-Portal unterstützt nun verwandte App-Lizenzen als einzelne App-Elemente auf der Benutzeroberfläche. Außerdem werden alle offline lizenzierten Apps, die aus dem Microsoft Store für Unternehmen synchronisiert werden, in einem einzelnen App-Eintrag konsolidiert, und jegliche Bereitstellungsdetails aus den einzelnen Paketen werden in einen einzelnen Eintrag migriert. Wenn Sie verwandte App-Lizenzen im Azure-Portal abrufen möchten, klicken Sie im Azure-Portal auf der Seite **Mobile Apps** auf **App-Lizenzen**.

### <a name="device-configuration"></a>Gerätekonfiguration
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Dateierweiterungen für die automatische Verschlüsselung in Windows Informationen Protection (WIP) <!-- 1463582 -->
Mit einer Einstellung in Windows Informationen Protection (WIP) können Sie nun angeben, welche Dateierweiterungen automatisch verschlüsselt werden, wenn aus einer Server Message Block-Freigabe (SMB) innerhalb der Begrenzung des Unternehmens, wie in der WIP-Richtlinie definiert, kopiert wird.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Konfiguration der Einstellungen des Ressourcenkontos für Surface Hubs

Sie können nun Einstellungen des Ressourcenkontos für Surface Hubs über eine Remoteverbindung konfigurieren.

Das Ressourcenkonto wird von einem Surface Hub für die Authentifizierung bei Skype bzw. Exchange verwendet, um dessen Teilnahme an einer Besprechung zu ermöglichen.
Sie können ein eindeutiges Ressourcenkonto erstellen, damit der Surface Hub in der Besprechung als Konferenzraum angezeigt werden kann.
Dieses Ressourcenkonto können Sie dann beispielsweise **Konferenzraum B41/6233** nennen.

> [!NOTE]
> - Wenn Sie Felder leer lassen, setzen Sie bereits auf dem Gerät konfigurierte Attribute außer Kraft.
>
> - Die Eigenschaften des Ressourcenkontos auf dem Surface Hub können sich dynamisch verändern. Dies passiert z.B., wenn die Kennwortrotation aktiviert ist. Das bedeutet, dass es einige Zeit dauert, bis die Werte in der Azure-Konsole die aktuellen Gegebenheiten auf dem Gerät widerspiegeln.
>
>   Um ein grundlegendes Verständnis darüber zu erlangen, welche Optionen derzeit auf dem Surface Hub konfiguriert sind, können die Informationen zum Ressourcenkonto in der Hardwareinventur (die bereits alle sieben Tage durchgeführt wird) oder als schreibgeschützte Eigenschaften enthalten sein. Wenn Sie nach der Durchführung der Remoteaktion die Genauigkeit vergrößern möchten, können Sie den Status der Parameter unmittelbar nach der Ausführung dieser Aktion abrufen, um ein Update für das Konto bzw. die Parameter auf dem Surface Hub auszuführen.


##### <a name="attack-surface-reduction"></a>Verringerung der Angriffsfläche


|Name der Einstellung  |Einstellungsoptionen  |Beschreibung  |
|---------|---------|---------|
|Execution of password-protected executable content from email (Ausführung der kennwortgeschützten ausführbaren Inhalte aus der E-Mail)|Blockieren, Überwachung, Nicht konfiguriert|Prevent password-protected executable files downloaded over email from running (Ausführung der von der E-Mail heruntergeladenen, kennwortgeschützten ausführbaren Inhalte verhindern).|
|Erweiterter Schutz vor Ransomware|Enabled, Audit, Not configured (Aktiviert, Überwachung, Nicht konfiguriert)|Verwendung eines offensiven Schutzes vor Ransomware.|
|Flag credential stealing from the Windows local security authority subsystem (Abgreifen von Anmeldeinformationen über das Subsystem der lokalen Sicherheitsautorität von Windows kennzeichnen)|Aktiviert, Überwachung, Nicht konfiguriert|Flag credential stealing from the Windows local security authority subsystem (lsass.exe) (Abgreifen von Anmeldeinformationen über das Subsystem zur lokalen Sicherheitsautorität von Windows kennzeichnen (lsass.exe)).|
|Process creation from PSExec and WMI commands (Prozesserstellung über die Befehle „PSExec“ und „WMI“)|Blockieren, Überwachung, Nicht konfiguriert|Blockiert Prozesserstellungen über die Befehle „PSExec“ und „WMI“.|
|Untrusted and unsigned processes that run from USB (Nicht vertrauenswürdige und nicht signierte Prozesse, die über USB ausgeführt werden)|Blockieren, Überwachung, Nicht konfiguriert|Blockiert nicht vertrauenswürdige und nicht signierte Prozesse, die über USB ausgeführt werden.|
|Executables that don’t meet a prevalence, age, or trusted list criteria (Ausführbare Dateien, die keinem Listenkriterium zur Verbreitung, zum Alter oder zur Vertrauenswürdigkeit entsprechen)|Blockieren, Überwachung, Nicht konfiguriert|Blockiert das Ausführen ausführbarer Dateien, wenn sie keinem Listenkriterium zur Verbreitung, zum Alter oder zur Vertrauenswürdigkeit entsprechen.|

##### <a name="controlled-folder-access"></a>Überwachter Ordnerzugriff

|              Name der Einstellung               |                                                              Einstellungsoptionen                                                              | Beschreibung |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Ordnerschutz (bereits implementiert) | Nicht konfiguriert, Aktivieren, Nur Überwachung (bereits implementiert)<br><br> <strong>Neu</strong><br>Blockieren der Änderung des Datenträgers, Überwachung der Änderung des Datenträgers |             |

Hiermit schützen Sie Dateien und Ordner vor unbefugten Änderungen durch bösartige Apps.<br><br>**Aktivieren:** Vermeiden Sie, dass nicht vertrauenswürdige Apps Dateien in geschützten Ordnern verändern oder löschen und in Datenträgersektoren schreiben.<br><br>
**Nur die Änderung des Datenträgers blockieren**:<br>Blockiert, dass nicht vertrauenswürdige Apps in Datenträgersektoren schreiben. Nicht vertrauenswürdige Apps können weiterhin Dateien in geschützten Ordnern verändern oder löschen.

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Ergänzungen zu den Konformitätsrichtlinien für die Systemsicherheitseinstellungen für Windows 10 und höher <!--1704133-->

Es sind nun Ergänzungen zu den Konformitätsrichtlinien für Windows 10 verfügbar. Z.B. sind eine Firewall und Windows Defender Antivirus erforderlich.


### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung
### <a name="intune-apps"></a>Intune-Apps
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Unterstützung für Offline-Apps aus dem Microsoft Store für Unternehmen <!--1222672-->
Offline-Apps, die Sie über den Microsoft Store für Unternehmen erworben haben, werden nun mit dem Azure-Portal synchronisiert. Sie können diese Apps für Geräte- oder Benutzergruppen bereitstellen. Offline-Apps werden durch Intune und nicht durch den Store installiert.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Verhindern, dass Benutzer Konten im Arbeitsprofil hinzufügen oder daraus entfernen <!-- 1728700 -->

Wenn Sie die Gmail-App in einem Android for Work-Profil bereitstellen, können Sie mit der Einstellung **Konten hinzufügen und entfernen** im Android for Work-Geräteeinschränkungsprofil verhindern, dass Benutzer Konten im Arbeitsprofil manuell hinzufügen oder daraus entfernen.

## <a name="week-of-february-5-2018"></a>Woche vom 5. Februar 2018

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Neue Option zur Benutzerauthentifizierung für die Apple-Massenregistrierung<!-- 747625 eeready -->

> [!NOTE]
> Neue Mandanten erkennen diese neue Option sofort. Für bereits vorhandene Mandanten wird dieses Feature im April eingeführt. Bis zur vollständigen Durchführung der Bereitstellung kann es sein, dass Sie noch keinen Zugriff auf diese neuen Features haben.

Mit Intune können Sie jetzt Geräte über folgende Registrierungsmethoden mit der Unternehmensportal-App authentifizieren:

- Apple-Programm zur Geräteregistrierung
- Apple School Manager
- Apple Configurator-Registrierung

Wenn Sie die Unternehmensportaloption verwenden, kann die mehrstufige Authentifizierung von Azure Active Directory erzwungen werden, ohne dass hierdurch diese Registrierungsmethoden blockiert werden.

Bei Verwendung der Unternehmensportaloption überspringt Intune die Benutzerauthentifizierung im iOS-Einrichtungsassistenten für die Registrierung mit der Benutzeraffinität. Das bedeutet, dass das Gerät zunächst als Gerät ohne Benutzer registriert wird und somit keine Konfigurationen oder Richtlinien von Benutzergruppen erhält. Es erhält nur Konfigurationen und Richtlinien für Gerätegruppen. Allerdings installiert Intune automatisch die Unternehmensportal-App auf dem Gerät. Der erste Benutzer, der die Unternehmensportal-App startet und sich bei dieser anmeldet, wird mit dem Gerät in Intune verbunden. An dieser Stelle erhält der Benutzer Konfigurationen und Richtlinien seiner Benutzergruppen. Die Benutzerzuordnung kann nur durch erneute Registrierung geändert werden.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Intune-Unterstützung für mehrere Apple DEP-/Apple School Manager-Konten <!-- 747685 eeready -->

Intune unterstützt jetzt die Registrierung von Geräten mit bis zu 100 verschiedenen Apple DEP-Konten (Device Enrollment Program = Programm zur Geräteregistrierung) oder Apple School Manager-Konten. Jedes Token kann separat für Registrierungsprofile und Geräte hochgeladen und verwaltet werden. Jedem hochgeladenen DEP-/School Manager-Token kann automatisch ein separates Registrierungsprofil zugewiesen werden. Wenn mehrere School Manager-Token hochgeladen werden, kann mit der Microsoft-Synchronisierung von Schul-/Unidaten jeweils nur ein Token freigegeben werden.

Nach der Migration funktionieren die Betaversionen der Graph-APIs und veröffentlichten Skripts zur Verwaltung von Apple DEP oder ASM über Graph nicht mehr. Neue Betaversionen der Graph-APIs sind in der Entwicklung und werden nach der Migration veröffentlicht.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Remotedrucken über ein sicheres Netzwerk <!-- 1709994  -->
Mobile drahtlose PrinterOn-Drucklösungen ermöglichen es Benutzern, jederzeit von einem beliebigen Ort aus Druckvorgänge remote über ein sicheres Netzwerk durchzuführen. PrinterOn wird in das Intune APP SDK für iOS und Android integriert. Über das Intune-Blatt **App-Schutzrichtlinien** in der Administratorkonsole können Sie gezielt die App-Schutzrichtlinien für diese App steuern. Endbenutzer können die App „PrinterOn for Microsoft“ über den Play Store oder iTunes herunterladen, um sie innerhalb ihres Intune-Ökosystems zu nutzen.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Unterstützung von Registrierungen durch das macOS-Unternehmensportal über den Geräteregistrierungs-Manager <!-- 1352411 -->

Benutzer können jetzt den Geräteregistrierungs-Manager verwenden, wenn sie sich im macOS-Unternehmensportal registrieren.

## <a name="week-of-january-29-2018"></a>Woche vom 29. Januar 2018

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Warnungen für abgelaufene und in Kürze ablaufende Token <!-- 1639263 -->
Auf der Übersichtsseite werden jetzt Warnungen für abgelaufene und in Kürze ablaufende Token angezeigt. Wenn Sie auf eine Warnung für ein einzelnes Token klicken, navigieren Sie zur Detailseite des Tokens.  Wenn Sie auf eine Warnung mit mehreren Token klicken, werden Sie zu einer Liste aller Token mit dem jeweiligen Status weitergeleitet. Administratoren sollten ihre Token vor dem Ablaufdatum verlängern.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>Remoteunterstützung für den Befehl „Löschen“ für macOS-Geräte<!-- 1438084 -->

Administratoren können remote den Befehl „Löschen“ für macOS-Geräte auslösen.

> [!IMPORTANT]
> Der Löschbefehl kann nicht zurückgesetzt werden und sollte mit Bedacht angewendet werden.

Der Löschbefehl entfernt alle Daten von einem Gerät, einschließlich des Betriebssystems. Zusätzlich wird dabei auch das Gerät aus der Intune-Verwaltung entfernt. Es erfolgt keine Warnung gegenüber dem Benutzer und die Löschung erfolgt unmittelbar nach Ausgabe des Befehls.

Sie müssen eine 6-stellige PIN für die Wiederherstellung konfigurieren. Mit dieser PIN kann das gelöschte Gerät entsperrt werden, woraufhin die erneute Installation des Betriebssystems beginnt. Nach dem Starten des Löschvorgangs wird die PIN in einer Statusleiste auf dem Übersichtsblatt des Geräts in Intune angezeigt. Die PIN bleibt für die Dauer der Löschung bestehen. Nach der Löschung verschwindet das Gerät vollständig aus der Intune-Verwaltung. Dokumentieren Sie die Wiederherstellungs-PIN, damit sie jedem, der das Gerät wiederherstellt, zur Verfügung steht.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Widerrufen von Lizenzen für ein iOS Volume Purchase Program-Token <!-- 820870 -->
Sie können die Lizenz für alle iOS VPP-Apps (Volume Purchase Program) für ein bestimmtes VPP-Token widerrufen.

### <a name="app-management"></a>App-Verwaltung

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Widerrufen von Apps aus dem iOS Volume Purchase Program <!-- 820863 -->
Für ein bestimmtes Gerät, das mindestens eine iOS VPP-App (Volume Purchase Program) enthält, können Sie die zugehörige gerätebasierte App-Lizenz für das Gerät widerrufen. Durch das Widerrufen einer App-Lizenz wird die zugehörige VPP-App nicht vom Gerät deinstalliert. Zum Deinstallieren einer VPP-App müssen Sie die Zuweisungsaktion in **Deinstallieren** ändern. Weitere Informationen finden Sie unter [Verwalten von iOS-Apps, die über ein Volumenprogramm mit Microsoft Intune erworben wurden](vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Zuweisen von mobilen Office 365-Apps an iOS- und Android-Geräte mithilfe des integrierten App-Typs <!-- 1332318 -->
Der **integrierte** App-Typ erleichtert, Office 365-Apps für die iOS- und Android-Geräte, die Sie verwalten, zu erstellen und sie diesen zuzuweisen. Zu diesen Apps gehören Office 365-Apps wie Word, Excel, PowerPoint und OneDrive. Sie können bestimmte Apps dem App-Typen zuweisen und die Konfiguration der App-Informationen bearbeiten.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Ein- und Ausschließen von App-Zuweisungen basierend auf Gruppen<!-- 1406920 -->

Bei der App-Zuweisung und nach der Auswahl eines Zuweisungstyps können Sie die ein- und auszuschließenden Gruppen auswählen.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>Sie können eine Anwendungskonfigurationsrichtlinie Gruppen zuweisen, indem Sie Zuweisungen ein- und ausschließen  <!-- 1480316 -->

Sie können einer Gruppe von Benutzern und Geräten mithilfe einer Kombination von Ein- und Ausschlusszuweisungen eine Anwendungskonfigurationsrichtlinie zuweisen. Zuweisungen können entweder als eine benutzerdefinierte Auswahl von Gruppen oder virtuelle Gruppe ausgewählt werden. Eine virtuelle Gruppe kann entweder **Alle Benutzer**, **Alle Geräte** oder **Alle Benutzer und alle Geräte** einschließen.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Unterstützung für die Windows 10-Editionsupgraderichtlinie <!-- 903672(archived), 1119689 -->  
Durch das Erstellen einer Windows 10-Editionsupgraderichtlinie können Sie für Windows 10-Geräte ein Upgrade auf folgende Betriebssysteme durchführen: Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education und Windows 10 Professional Education N. Weitere Informationen zu Windows 10-Editionsupgrades finden Sie unter [Konfigurieren von Windows 10-Editionsupgrades](edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Ausschließliche Verfügbarkeit von Richtlinien für den bedingten Zugriff für Intune über das Azure-Portal  <!-- 1737088 1634311 -->

Ab diesem Release müssen Sie Ihre Richtlinien für den bedingten Zugriff über das [Azure-Portal](https://portal.azure.com) unter **Azure Active Directory** > **Bedingter Zugriff** konfigurieren und verwalten. Der Einfachheit halber können Sie dieses Blatt auch über **Intune** > **Bedingter Zugriff** im Azure-Portal aufrufen.

#### <a name="updates-to-compliance-emails---1637547---"></a>Updates für Konformitäts-E-Mails<!--1637547 -->

Wenn eine E-Mail zur Meldung eines nicht konformen Geräts gesendet wird, werden Details über das nicht konforme Gerät einbezogen.


## <a name="week-of-january-22-2018"></a>Woche vom 22. Januar 2018

### <a name="intune-apps"></a>Intune-Apps

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Neue Funktionen für die Aktion „Lösung“ für Android-Geräte <!--1583480-->

Die Unternehmensportal-App für Android erweitert die Aktion „Lösung“ für **Geräteeinstellungen aktualisieren**, um [Verschlüsselungsprobleme bei Geräten](/intune-user-help/encrypt-your-device-android) zu lösen.

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Remote-Sperre in der Unternehmensportal-App für Windows 10 verfügbar <!--676506-->
Endbenutzer können Ihre Geräte jetzt über die Unternehmensportal-App für Windows 10 über eine Remoteverbindung sperren. Dies wird nicht für das lokale Gerät angezeigt, dass sie aktiv verwenden.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Einfachere Lösung von Konformitätsfehlern für die Unternehmensportal-App für Windows 10 <!--676546-->
Endbenutzer mit Windows-Geräten können in der Unternehmensportal-App auf den Grund der Nichtkonformität tippen. Wenn möglich werden sie direkt an den korrekten Ort in der Einstellungs-App geleitet, um das Problem zu beheben.

## <a name="week-of-december-11-2017"></a>Woche des 11. Dezember 2017

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="new-automatic-redeployment-setting----1469168---"></a>Neue Einstellung für die automatische erneute Bereitstellung <!-- 1469168 -->
Die Einstellung **Automatische erneute Bereitstellung** ermöglicht es Benutzern mit Administratorrechten, alle Benutzerdaten und -einstellungen über **STRG+Windows+R** vom Sperrbildschirm des Geräts aus zu löschen. Das Gerät wird automatisch neu konfiguriert und bei der Verwaltung neu registriert. Diese Einstellung finden Sie unter „Windows 10“ > „Geräteeinschränkungen“ > „Allgemein“ > „Automatische erneute Bereitstellung“. Weitere Informationen finden Sie unter [Einstellungen für Geräteeinschränkungen für Windows 10 in Intune](device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Unterstützung für zusätzliche Quelleditionen in der Windows 10-Editionsupgraderichtlinie<!-- 903672,  1119689 -->
Sie können jetzt die Windows 10-Editionsupgraderichtlinie verwenden, um ein Upgrade von zusätzlichen Windows 10-Editionen (Windows 10 Pro, Windows 10 Pro for Education, Windows 10 Cloud, usw.) durchzuführen. Vor dieser Version waren die Upgradepfade für die unterstützten Editionen stärker eingeschränkt. Einzelheiten finden Sie unter [Konfigurieren von Windows 10-Editionsupgrades in Microsoft Intune](edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Neue Einstellungen des WDSC-Gerätekonfigurationsprofils (Windows Defender Security Center) <!-- 1335507 -->

Unter dem Endpunktschutz namens **Windows Defender Security Center** fügt Intune einen neuen Abschnitt mit Einstellungen des Gerätekonfigurationsprofils hinzu. IT-Administratoren können konfigurieren, welche Komponenten der Windows Defender Security Center-App für Endbenutzer zugänglich sind. Wenn ein IT-Administrator eine Komponente in der Windows Defender Security Center-App ausblendet, werden Benachrichtigungen in Zusammenhang mit der ausgeblendeten Komponente nicht auf dem Gerät des Benutzers angezeigt.

Folgende Komponenten können von Administratoren aus den Einstellungen des Gerätekonfigurationsprofils von Windows Defender Security Center ausgeblendet werden:
- Viren- und Bedrohungsschutz
- Geräteleistung und -integrität
- Firewall- und Netzwerkschutz
- App- und Browsersteuerung
- Familienoptionen

IT-Administratoren können auch anpassen, welche Benutzer Benachrichtigungen empfangen können. Beispielsweise können Sie konfigurieren, ob Benutzer alle von sichtbaren Komponenten in WDSC generierten Benachrichtigungen oder nur kritische Benachrichtigungen erhalten. Zu nicht kritischen Benachrichtigungen gehören regelmäßige Zusammenfassungen von Windows Defender Antivirus-Aktivitäten und Benachrichtigungen bei Abschluss von Überprüfungen. Alle übrigen Benachrichtigungen gelten als kritisch. Darüber hinaus können Sie auch den Inhalt der Benachrichtigung anpassen. Beispielsweise können Sie die IT-Kontaktinformationen angeben, um sie in die Benachrichtigungen einzubetten, die auf den Geräten der Benutzer angezeigt werden.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>Unterstützung für mehrere Connectors für die Behandlung von SCEP- und PFX-Zertifikaten <!-- 1361755 -->

Kunden, die den lokalen NDES-Connector zum Übermitteln von Zertifikaten an Geräte verwenden, können ab sofort mehrere Connectors in einem einzelnen Mandanten konfigurieren.

Diese neue Funktion unterstützt das folgende Szenario:

- **Hochverfügbarkeit**

Jeder NDES-Connector bezieht Zertifikatanforderungen mithilfe von Pull von Intune.  Wenn ein NDES-Connector offline geschaltet wird, kann der andere Connector weiterhin Anforderungen verarbeiten.

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>Möglichkeit zur Verwendung der Variable AAD_DEVICE_ID im benutzerdefinierten Antragstellernamen <!-- 1468599 -->

Wenn Sie ein SCEP-Zertifikatprofil in Intune erstellen, können Sie beim Erstellen des benutzerdefinierten Antragstellernamens ab sofort die Variable AAD_DEVICE_ID verwenden.   Wenn das Zertifikat mithilfe dieses SCEP-Profils angefordert wird, wird die Variable durch die AAD-Geräte-ID des Geräts ersetzt, das die Zertifikatsanforderung ausführt.


### <a name="device-management"></a>Geräteverwaltung

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Verwalten von über Jamf registrierten macOS-Geräten mit der Gerätekonformitäts-Engine von Intune <!-- 1592747 -->
Ab sofort können Sie mit Jamf Informationen über den macOS-Gerätezustand an Intune senden. Dort werden sie im Hinblick auf Konformität mit den Richtlinien ausgewertet, die in der Intune-Konsole definiert sind. Basierend auf dem Konformitätszustand des Geräts und anderen Bedingungen (z.B. Standort, Benutzerrisiko usw.) wird die Konformität für macOS-Geräte, die auf mit Azure AD verbundene Cloud- und lokale Anwendungen zugreifen (einschließlich Office 365) mithilfe des bedingten Zugriffs erzwungen. Erfahren Sie mehr über die [Einrichtung der Jamf-Integration](conditional-access-integrate-jamf.md) und [Erzwingung der Konformität für Jamf-verwaltete Geräte](conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action------1424701---"></a>Neue iOS-Geräteaktion <!-- 1424701 -->

Sie können nun überwachte iOS 10.3-Geräte herunterfahren. Diese Aktion fährt das Gerät sofort und ohne Warnung für den Endbenutzer herunter. Die Aktion **Herunterfahren (nur überwacht)** finden Sie in den Geräteeigenschaften bei der Auswahl eines Geräts in der Workload **Gerät**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Verhindern von Änderungen an Datum/Uhrzeit bei Samsung KNOX-Geräten <!-- 1468103 -->

Wir haben ein neues Feature hinzugefügt, mit dem Sie Datums- und Zeitänderungen auf Samsung KNOX-Geräten blockieren können. Sie finden dieses unter **Gerätekonfigurationsprofile** > **Geräteeinschränkungen (Android)** > **Allgemein**.

#### <a name="surface-hub-resource-account-supported----1566442----"></a>Unterstützung für Surface Hub-Ressourcenkonto <!-- 1566442  -->

Eine neue Geräteaktion wurde hinzugefügt, damit Administratoren das einem Surface Hub zugeordnete Ressourcenkonto definieren und aktualisieren können.

Das Ressourcenkonto wird von einem Surface Hub für die Authentifizierung bei Skype/Exchange verwendet, um seine Teilnahme an einer Besprechung zu ermöglichen. Sie können ein eindeutiges Ressourcenkonto erstellen, damit der Surface Hub in der Besprechung als Konferenzraum angezeigt wird. Beispielsweise kann das Ressourcenkonto als *Konferenzraum B41/6233* angezeigt werden. Das Ressourcenkonto (auch als Gerätekonto bezeichnet) für den Surface Hub muss in der Regel für den Standort des Konferenzraums konfiguriert werden, wenn andere Parameter des Ressourcenkontos geändert werden müssen.

Wenn Administratoren das Ressourcenkonto auf einem Gerät aktualisieren möchten, müssen sie die aktuellen Active Directory-/Azure Active Directory-Anmeldeinformationen angeben, die dem Gerät zugeordnet sind. Wenn die Kennwortrotation für das Gerät aktiviert ist, müssen Administratoren zu Azure Active Directory wechseln, um das Kennwort zu finden.

> [!NOTE]
> Alle Felder werden im Paket nach unten gesendet und überschreiben alle Felder, die zuvor konfiguriert wurden. Leere Felder überschreiben auch vorhandene Felder.

Administratoren können folgende Einstellungen konfigurieren:

- **Ressourcenkonto**
   - **Active Directory-Benutzer**

      Domänenname\Benutzername oder Benutzerprinzipalname (UPN): user@domainname.com

   - **Passwort**

- **Optionaler Ressourcenkontoparameter** (muss über das angegebene Ressourcenkonto festgelegt werden)

   - **Zeitraum für Kennwortrotation**

     Stellt sicher, dass das Kontokennwort aus Sicherheitsgründen jede Woche automatisch durch den Surface Hub aktualisiert wird. Um nach dem Aktivieren dieser Option Parameter zu konfigurieren, muss das Kennwort für das Konto in Azure Active Directory zuerst zurückgesetzt werden.

   - **SIP-Adresse (Session Initiation-Protokoll)**

     Wird nur verwendet, wenn die AutoErmittlung nicht möglich ist.

   - **E-Mail**

     E-Mail-Adresse des Geräte-/Ressourcenkontos.

   - **Exchange-Server**

     Nur erforderlich, wenn die AutoErmittlung nicht möglich ist.

   - **Kalendersynchronisierung**

     Gibt an, ob die Kalendersynchronisierung und andere Exchange-Serverdienste aktiviert sind. Beispiel: die Besprechungssynchronisierung.

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>Installieren von Office-Apps auf macOS-Geräten <!-- 1494311 -->
Sie können nun Office-Apps auf macOS-Geräten installieren. Dieser neue App-Typ ermöglicht Ihnen die Installation von Word, Excel, PowerPoint, Outlook und OneNote. Diese Apps sind auch im Lieferumfang von Microsoft AutoUpdate (MAU) enthalten, um Ihre Apps sicher und auf dem neuesten Stand zu halten.

### <a name="app-management"></a>App-Verwaltung

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>Löschen eines iOS Volume Purchase Program-Tokens <!-- 820879 -->
Sie können das iOS-VPP-Token (Volume Purchase Program) über die Konsole löschen. Dies kann erforderlich sein, wenn doppelte Instanzen eines VPP-Tokens vorliegen.

### <a name="intune-apps"></a>Intune-Apps


### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>Eine neue Entitätssammlung namens „Aktueller Benutzer“ ist auf die Daten der momentan aktiven Benutzer beschränkt.<!-- 1667026 -->

Die Entitätssammlung **Benutzer** listet alle Benutzer von Azure Active Directory (Azure AD) mit zugewiesenen Lizenzen in Ihrem Unternehmen auf. Beispielsweise kann ein Benutzer in Intune hinzugefügt und dann im Verlauf des letzten Monats entfernt worden sein. Auch wenn dieser Benutzer zum Zeitpunkt der Berichterstellung nicht vorhanden ist, liegen Angaben zu Benutzer und Zustand in den Daten vor. Sie können einen Bericht erstellen, der die Dauer der Präsenz des Benutzers in Ihren Daten zeigt.

Im Gegensatz dazu enthält die neue Entitätssammlung **Aktueller Benutzer** nur Benutzer, die nicht entfernt wurden. Die Entitätssammlung **Aktueller Benutzer** enthält nur die derzeit aktiven Benutzer. Informationen zur Entitätssammlung **Aktueller Benutzer** finden Sie unter [Referenz für die Entität „Aktueller Benutzer“](reports-ref-current-user.md).


### <a name="updated-graph-apis----1736360---"></a>Aktualisierte Graph-APIs<!-- 1736360 -->

In diesem Release haben wir einige der Graph-APIs für Intune aktualisiert, die sich in der Betaphase befinden. Weitere Informationen finden Sie im monatlichen [Graph-API-Änderungsprotokoll](https://developer.microsoft.com/graph/docs/concepts/changelog).

## <a name="week-of-december-4-2017"></a>Woche des 4. Dezember 2017

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune unterstützt WIP-abgelehnte Apps (Windows Information Protection) <!-- 1479103 -->
Sie können abgelehnte Apps in Intune festlegen. Wenn eine App abgelehnt wird, wird ihr der Zugriff auf Unternehmensinformationen verweigert. Sie ist also genau das Gegenteil einer zugelassenen App. Weitere Informationen finden Sie unter [AppLocker-CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection).



## <a name="notices"></a>Benachrichtigungen

### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>Maßnahme erforderlich: Bitte aktualisieren Sie Ihre Android-Gerätebeschränkungen oder die Kennworteinstellungen für die Konformitätsrichtlinie in Intune
Intune wird für Geräte mit Android 4.4 und höher den Kennworttyp „Gerätestandard“ entfernen. Aufgrund von unterschiedlichen Android-Plattformen und Gerätestandards wird diese Richtlinie häufig von dem Gerät als optional behandelt. Wir entfernen in einem der nächsten Releases diese Einstellung von der Benutzeroberfläche, um Unklarheiten dazu zu beseitigen, wann diese Einstellung für Android erzwungen wird. 
#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
- Wenn Sie ein Kennwort für die Geräte erforderlich machen möchten, wird empfohlen, dass Sie anstelle des „Gerätestandards“ Ihre Android-Plattformprofile bearbeiten, um den erforderlichen Kennworttypen deutlich hervorzuheben.
- Wenn Sie möchten, dass der Endbenutzer entscheidet, ob er ein Kennwort erstellen möchte, klicken Sie auf die Schaltfläche „Nicht konfiguriert“. Wenn wir diese Einstellung von der Benutzeroberfläche entfernen, sie aber immer noch festgelegt ist, werden Sie aufgefordert, einen anderen Wert als den „Gerätestandard“ auszuwählen, wenn Sie das nächste Mal das Profil bearbeiten.
Wie sollte ich mich für die Änderung vorbereiten?
Prüfen Sie die Kennworteinstellungen für die Einschränkungen und Konformitätsrichtlinien für Android- und Android Enterprise-Geräte. Diese sind unter „System security for Compliance policies“ (Systemsicherheit für Konformitätsrichtlinien) und entweder unter „Gerätekennwort“ oder unter „Work profile settings for Device restrictions“ (Arbeitsprofileinstellungen für Geräteeinschränkungen) aufgeführt. Unter „zusätzliche Informationen“ finden Sie einen Link zu weiteren Informationen und Screenshots zur Konfiguration dieser Einstellungen.
####<a name="additional-information"></a>Zusätzliche Informationen
https://aka.ms/PasswordSettings 

### <a name="plan-for-change-change-password-at-next-auth-added-to-intune---1873216---"></a>Planen der Änderung: „Change Password at Next Auth“ (Kennwort bei der nächsten Authentifizierung ändern) zu Intune hinzugefügt<!-- 1873216 -->
Für das Service Release im September plant Intune, die von Apple neu veröffentlichte Einstellung **Change Password at Next Auth** (Kennwort bei der nächsten Authentifizierung ändern) für Geräte mit MacOS-Version 10.13 und höher zu integrieren. Vor dieser Einstellung können MDM-Anbieter nicht überprüfen, ob das Gerätekennwort geändert wurde, um kompatibel zu sein. Die Konfigurations- und Konformitätsrichtlinien von Intune validieren nur, dass bei der nächsten Änderung eines Gerätekennworts dieses als konform gekennzeichnet ist. Wenn diese neue Apple-Funktion hinzugefügt wird, erhalten Ihre MacOS-Benutzer eine Aufforderung, ihr Kennwort zu aktualisieren, selbst wenn ihr Kennwort konform ist.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Dies wirkt sich auf Umgebungen mit einer MacOS-Geräterichtlinie unter Verwendung von Intune oder einer hybriden MDM aus. Mit der neuen Apple-Einstellung **Change Password at Next Auth** (Kennwort bei der nächsten Authentifizierung ändern) kann Intune Benutzer zwingen, ihr Kennwort zu aktualisieren, wenn eine Passwortrichtlinie durchgesetzt wird. Wenn Sie Unternehmensressourcen blockieren, bis das Gerät als konform gekennzeichnet ist, werden Ihre Endbenutzer möglicherweise für den Zugriff auf Unternehmensressourcen wie E-Mail- oder SharePoint-Websites gesperrt, bis sie ihr Kennwort zurücksetzen. Künftig zwingen alle Aktualisierungen der Konfigurations- und Konformitätskennwortrichtlinien Benutzer gezielt dazu, ihre Kennwörter zu aktualisieren.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Setzen Sie sich mit Ihrem Helpdesk in Verbindung. Wenn Sie diese MacOS-Geräterichtlinie nicht durchsetzen wollen, empfehlen wir Ihnen, Ihre bestehende MacOS-Richtlinie aufzuheben oder zu löschen. Kundenbefragungen zeigen, dass die meisten Kunden von dieser Änderung nicht betroffen sind. Die meisten Endbenutzer aktualisieren ihr Kennwort, nachdem sie eine Aufforderung erhalten haben, sich mit einem Kennwort anzumelden, oder setzen ihr Kennwort zurück, um konform zu bleiben.


### <a name="plan-for-change-intune-moving-to-support-ios-10-and-later-in-september----2454656---"></a>Änderungen einplanen: Intune unterstützt ab September iOS 10 und höher <!-- 2454656 -->
Es wird davon ausgegangen, dass Apple im September iOS 12 veröffentlicht. Sobald die neue Version veröffentlicht wurde, wird die Unterstützung von iOS 10 und höher für die Registrierung bei Intune, das Unternehmensportal und den verwalteten Browser eingeführt.  

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?  
Mobile Office 365-Apps werden unter iOS 10 und höher unterstützt. Deshalb ist es möglich, dass Sie für Ihr Betriebssystem oder Ihr Gerät bereits ein Upgrade durchgeführt haben. Sollte dies der Fall sein, sind Sie von dieser Änderung nicht betroffen.  

Wenn Sie über eines der unten aufgelisteten Geräte verfügen oder eines der unten aufgelisteten Geräte registrieren möchten, sollten Sie beachten, dass diese nur iOS 9 und früher unterstützen.  Wenn Sie mit diesen Geräten weiter auf das Intune-Unternehmensportal zugreifen möchten, müssen Sie für diese Geräte bis September ein Upgrade auf Geräte mit Unterstützung für iOS 10 oder höher durchführen:  

* iPhone 4S  
* iPod Touch  
* iPad 2  
* iPad (3. Generation)  
* iPad Mini (1. Generation)  

Ab Juli erhalten mit MDM registrierte Geräte mit iOS 9 und dem Unternehmensportal eine Aufforderung, ein Upgrade für das Betriebssystem oder das Gerät durchzuführen. Wenn Sie App-Schutzrichtlinien verwenden, können Sie auch die Zugriffseinstellung „iOS-Mindestbetriebssystem anfordern (nur Warnung)“ festlegen.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?   
Prüfen Sie, welche Geräte und Benutzer in Ihrer Organisation von dieser Änderung betroffen sind. Navigieren Sie in Intune im Azure-Portal zu Geräte > Alle Geräte, und filtern Sie diese nach Betriebssystem.  Klicken Sie auf „Spalten“, um weitere Angaben wie die Betriebssystemversion anzuzeigen. Fordern Sie Ihre Benutzer dazu auf, Ihr Gerät vor September auf eine unterstützte Betriebssystemversion upzugraden.  

### <a name="plan-for-change-intune-moving-to-tls-12"></a>Geplante Änderung: Umstellung von Intune auf TLS 1.2
Ab dem 31. Oktober 2018 unterstützt Intune die Version 1.2 des Transport Layer Security-Protokolls (TLS), um die beste Verschlüsselung bereitzustellen und den Dienst standardmäßig sicherer zu gestalten und auf andere Microsoft-Dienste wie Microsoft Office 365 auszurichten. Für Office wurde diese Änderung in MC128929 bekannt gegeben.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Ab dem 31. Oktober 2018 unterstützt Intune die Versionen 1.0 oder 1.1 des TLS-Protokolls nicht mehr. Alle Client-Server- und Browser-Server-Kombinationen sollten TLS 1.2 verwenden, um eine problemlose Verbindung mit Intune zu gewährleisten. Beachten Sie, dass diese Änderung sich auf Endbenutzergeräte auswirkt, die TLS 1.2 nicht verwenden können und nicht mehr von Intune unterstützt werden, aber weiterhin Richtlinien über Intune erhalten. Dazu zählen Geräte, auf denen Android 4.3 oder früher ausgeführt wird. Eine Liste der betroffenen Geräte und Browser finden Sie im Folgenden unter „Weitere Informationen“.

Wenn ab dem 31. Oktober 2018 Probleme in Zusammenhang mit der Verwendung einer älteren Version von TLS auftreten, müssen Sie auf TLS 1.2 aktualisieren oder sich ein Gerät zulegen, das TLS 1.2 unterstützt, um diese zu lösen.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Es wird empfohlen, Abhängigkeiten von TLS 1.0 und 1.1 proaktiv aus Ihren Umgebungen zu entfernen und TLS 1.0 und 1.1 nach Möglichkeit auf Betriebssystemebene zu deaktivieren. Beginnen Sie schon heute mit der Planung der Migration zu TLS 1.2. Im Blogbeitrag unten finden Sie eine Liste der Geräte, die derzeit nicht von Intune unterstützt werden, aber weiterhin Richtlinien erhalten, und bei denen keine Kommunikation mithilfe von TLS 1.2 möglich ist. Sie müssen diese Endbenutzer möglicherweise darüber benachrichtigen, dass sie den Zugriff auf Unternehmensressourcen verlieren.

**Weitere Informationen:** [Umstellung von Intune auf TLS 1.2 für die Verschlüsselung](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/)


### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>Planen der Änderung: Änderung in der Unterstützung für das Microsoft Intune App SDK-Cordova-Plug-In
Intune beendet die Unterstützung des [Microsoft Intune App SDK-Cordova-Plug-Ins](app-sdk-cordova.md) am 1. Mai 2018. Sie sollten stattdessen das Intune App Wrapping Tool verwenden, um Ihre auf Cordova basierenden Apps auf die Verwaltbarkeit und Verfügbarkeit in Intune vorzubereiten. Wenn diese Änderung wirksam wird, wird das Microsoft Intune APP SDK-Cordova-Plug-In jedoch weder beibehalten, noch werden Updates empfangen. App-Entwickler werden dieses Plug-In nicht verwenden können. Intune plant, weiterhin mit Cordova erstellte Apps zu unterstützen. Allerdings wird die Funktionalität mit dem Microsoft Intune APP SDK-Cordova-Plug-In erstellter Apps in Intune eingeschränkt sein. Nach Wrapping mit dem Intune App Wrapping Tool können Apps Endbenutzern normal bereitgestellt werden. Für auf Cordova basierende Android-Apps, die im Google Play Store veröffentlicht werden, gilt:
- Endbenutzer werden beim ersten Start aufgefordert, Anmeldeinformationen zum Empfangen der Intune-Richtlinie einzugeben.
- Apps sollten im App-Store für Intune-Benutzer veröffentlicht werden, z.B. „Contoso App for Intune“.

Weitere Informationen zum App Wrapping Tool finden Sie unter [Vorbereiten von iOS-Apps für App-Schutzrichtlinien mit dem Intune App Wrapping Tool](app-wrapper-prepare-ios.md) und [Vorbereiten von Android-Apps für App-Schutzrichtlinien mit dem Intune App Wrapping Tool](app-wrapper-prepare-android.md). Sollten Probleme auftreten oder Sie Fragen haben, kontaktieren Sie [msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com).

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Planen von Änderungen: Verwenden von Intune in Azure für die Verwaltung Ihrer mobilen Geräte jetzt möglich <!-- 1227338 -->
Vor über einem Jahr wurde eine [öffentlich zugängliche Vorschau von Intune in Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) angekündigt. Sechs Monate später wurde [die neue Benutzeroberfläche für Administratoren allgemein zugänglich gemacht](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/). Ab 31. August 2018 wird die Verwaltung mobiler Geräte (MDM) in der klassischen Silverlight-Konsole für Kunden deaktiviert, die eine eigenständige Intune-Version verwenden. Stattdessen können Sie [Intune in Azure](https://aka.ms/Intune_on_Azure) verwenden, wenn Sie Ihre Geräte mobil verwalten möchten. Wenn Sie immer noch die klassische Konsole für die Verwaltung mobiler Geräte verwenden, sollten Sie sich nun mit Intune in Azure vertraut machen. Diese Änderungen sollten keine Auswirkungen auf die Benutzer haben. Die klassische PC-Verwaltung bleibt in Silverlight erhalten. Erfahren Sie [hier](https://aka.ms/Intune_on_Azure_mdm) mehr über diese Änderungen und deren Folgen für Sie.

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkter Zugriff auf Apple-Registrierungsszenarien <!--951869-->
Für Intune-Konten, die nach Januar 2017 erstellt wurden, hat Intune direkten Zugriff auf Apple-Registrierungsszenarien mithilfe der Workload „Geräte registrieren“ im Azure-Portal aktiviert. Bisher konnte nur über Links im klassischen Intune-Portal auf die Apple-Registrierungsvorschau zugegriffen werden. Vor Januar 2017 erstellte Intune-Konten erfordern eine einmalige Migration, bevor diese Features in Azure verfügbar sind. Der Zeitplan für die Migration wurde noch nicht angekündigt, aber Sie erfahren so bald wie möglich Näheres. Es wird dringend empfohlen, ein Testkonto zu erstellen, um die neue Oberfläche zu testen, wenn Sie mit Ihrem vorhandenen Konto nicht auf das Azure-Portal zugreifen können.

## <a name="whats-coming"></a>Was steht an?

### <a name="local-device-security-option-settings----1251887---"></a>Einstellungen der Sicherheitsoptionen für lokale Geräte <!-- 1251887 -->
Mithilfe der neuen Einstellungen der Sicherheitsoptionen für lokale Geräte können Sie Sicherheitseinstellungen auf Windows 10-Geräten aktivieren. Diese Einstellungen finden Sie in der Endpoint Protection-Kategorie, wenn Sie eine Gerätekonfigurationsrichtlinie für Windows 10 erstellen.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968--"></a>Neues Update zur Verbesserung der Benutzerfreundlichkeit der Unternehmensportalwebsite <!--2000968-->

Ab August soll die Benutzerfreundlichkeit der Unternehmensportalwebsite verbessert werden. Dafür werden Updates für die Benutzeroberfläche ausgeführt, Workflows optimiert und die Barrierefreiheit verbessert. Diese Änderungen umfassen auf den Kunden ausgerichtete Verbesserungen wie das Freigeben von Apps. Außerdem wurde die Gesamtleistung verbessert, um die Servicequalität zu optimieren.
Es wurden auf der Grundlage von Feedback von Kunden wie Ihnen neue Features hinzugefügt, die die bereits vorhandenen Funktionen und die Benutzerfreundlichkeit um ein Vielfaches verbessern sollen:

* Verbesserungen der Benutzeroberfläche auf der gesamten Website
* Möglichkeit, direkte Links zu Apps zu teilen
* Verbesserte Leistung bei großen App-Katalogen

Sie müssen nichts tun, um sich auf diese Änderungen vorzubereiten. Sie werden informiert, sobald die aktualisierte Unternehmensportalwebsite für Sie verfügbar gemacht wird. Es kann jedoch sein, dass Sie danach die Dokumentation für die Endbenutzer aktualisieren und neue Screenshots hinzufügen müssen. Beachten Sie außerdem, dass Sie möglicherweise die Dokumentation für die Unternehmensportal-App unter iOS aktualisieren müssen, da die Website auf dem Abschnitt **Apps** der iOS-App basiert. Eine Beispielabbildung finden Sie auf der Seite zu den [Neuerungen der App-Benutzeroberfläche](whats-new-app-ui.md).

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple erfordert Updates für die Transportsicherheit für Anwendungen <!--748318-->
Apple hat angekündigt, dass bestimmte Anforderungen für die Transportsicherheit für Anwendungen (Application Transport Security, ATS) erzwungen werden. ATS wird verwendet, um eine strengere Sicherheit in allen App-Kommunikationen über HTTPS zu erzwingen. Diese Änderung wirkt sich auf Intune-Kunden aus, die die iOS-Unternehmensportal-App verwenden. Die aktuellen Informationen finden Sie auf dem [Intune-Support-Blog](https://aka.ms/compportalats).



## <a name="see-also"></a>Siehe auch
* [Microsoft Intune-Blog](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roadmap für die Cloudplattform](https://www.microsoft.com/cloud-platform/roadmap)
* [What‘s new in the Intune App UI (Neues auf der Intune-App-Benutzeroberfläche)](whats-new-app-ui.md)
* [Neuerungen in den vorherigen Monaten](whats-new-archive.md)
