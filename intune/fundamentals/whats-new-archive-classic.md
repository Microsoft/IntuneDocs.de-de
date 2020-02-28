---
title: Neuerungen des klassischen Portalarchivs von Microsoft Intune
description: Archiv für Ankündigungen von Neuheiten für Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/08/2017
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94ff28cf36457d2d8b20e173508b7c9894a7d5bc
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510536"
---
# <a name="whats-new-in-the-intune-classic-portal---previous-months"></a>Neuerungen im klassischen Intune-Portal – vorherige Monate

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Diese Seite enthält neue Funktionen und Benachrichtigungen, die zuvor auf der Seite [Was gibt es Neues?](whats-new.md) für das klassische Intune-Portal angekündigt waren.

## <a name="april-2017"></a>April 2017

### <a name="new-capabilities"></a>Neue Funktionen

#### <a name="myapps-available-for-managed-browser---822308-822303--"></a>„Meine Apps“ für Managed Browser verfügbar <!--822308, 822303-->

Microsoft MyApps verfügen jetzt über eine bessere Unterstützung innerhalb von Managed Browser. Managed Browser-Benutzer, die nicht für die Verwaltung vorgesehen sind, werden direkt an den MyApps-Dienst weitergeleitet, wo sie auf ihre durch den Administrator bereitgestellte SaaS-Apps zugreifen können. Benutzer, die für die Verwendung für die Intune-Verwaltung ausgelegt sind, können weiterhin auf MyApps vom integrierten Managed Browser-Lesezeichen aus zugreifen.

#### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Neue Symbole für Managed Browser und das Unternehmensportal <!--918433, 918431, 971473-->

Managed Browser erhält aktualisierte Symbole für die Android- und iOS-Versionen der App. Das neue Symbol enthält den aktualisierten Intune-Badge, damit es konsistenter mit anderen Apps in Enterprise Mobility + Security (EM+S) wird. Sie können das neue Symbol für Managed Browser auf der Seite [Aktualisierungen für die Benutzeroberfläche für Endbenutzer-Apps in Intune](whats-new-app-ui.md) finden.

Die Symbole für die Android-, iOS- und Windows-Versionen der App werden im Unternehmensportal ebenfalls aktualisiert, um die Konsistenz mit anderen Apps im EM+S zu verbessern. Diese Symbole werden von April bis Ende Mai schrittweise auf den Plattformen veröffentlicht.

#### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Statusanzeige zur Anmeldung im Android-Unternehmensportal <!--953374-->

Ein Update auf die Android-Unternehmensportal-App zeigt eine Statusanzeige der Anmeldung an, wenn der Benutzer die App startet oder fortsetzt. Die Statusanzeige durchläuft die neuen Phasen, beginnend mit „Verbindung wird aufgebaut“, „Anmeldung“ und dann „Suchen nach Sicherheitsanforderungen“, bevor dem Benutzer der Zugriff auf die App gewährt wird. Screenshots der neuen Bildschirme für die Unternehmensportal-App finden Sie auf der Seite mit den [Neuerungen der Intune-App-Benutzeroberfläche](whats-new-app-ui.md).

#### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>Verhindern, dass Apps auf SharePoint Online zugreifen <!-- 679339 -->

Sie können jetzt eine Richtlinie für den App-basierten bedingten Zugriff erstellen, um Apps, auf die keine Schutzrichtlinien angewendet wurden, am Zugriff auf [SharePoint Online](../protect/app-based-conditional-access-intune-create.md) zu hindern. Im Szenario des App-basierten bedingten Zugriffs können Sie Apps festlegen, denen der Zugriff auf SharePoint Online über das Azure-Portal gestattet werden soll.

#### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Unterstützung für einmaliges Anmelden in Outlook für iOS über das Unternehmensportal für iOS <!--834012-->
Benutzer müssen sich nicht mehr in der Outlook-App anmelden, wenn sie in der Unternehmensportal-App für iOS auf dem gleichen Gerät mit dem gleichen Konto angemeldet sind. Wenn Benutzer die Outlook-App starten, können sie ihr Konto auswählen und sich automatisch anmelden. Wir arbeiten auch daran, diese Funktion für andere Microsoft-Apps hinzuzufügen.

#### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>Verbesserte Statusnachrichten in der Unternehmensportal-App für iOS <!--744866-->
Neue, genauere Fehlermeldungen werden nun in der Unternehmensportal-App für iOS angezeigt, um einfacher Informationen darüber zu erhalten, was gerade auf Geräten geschieht. Diese Fehlerfälle waren zuvor in einer allgemeinen Fehlermeldung enthalten: „Unternehmensportal vorübergehend nicht verfügbar“. Wenn ein Benutzer darüber hinaus das Unternehmensportal unter iOS startet, wenn keine Internetverbindung vorhanden ist, wird keine beständige Statusanzeige auf der Startseite angezeigt, die angibt: „Keine Internetverbindung“.

#### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Verbesserter App-Installationsstatus für die Windows 10-Unternehmensportal-App <!--676495-->

Dies sind die neuen Verbesserungen für die Installation von Apps in der Windows 10-Unternehmensportal-App:
- Schnellere Meldung des Installationsstatus für MSI-Pakete
- Schnellere Meldung des Installationsstatus für moderne Apps auf Geräten mit Windows 10 Anniversary Update und höher
- Neue Statusanzeige für die Installation moderner Apps auf Geräten mit Windows 10 Anniversary Update und höher

Sie können die neue Statusanzeige auf der Seite [Aktualisierungen für die Benutzeroberfläche für Endbenutzer-Apps in Intune](whats-new-app-ui.md) finden.

#### <a name="bulk-enroll-windows-10-devices----747607---"></a>Massenregistrierung von Windows 10-Geräten <!-- 747607 -->

Sie können jetzt eine große Anzahl von Geräten, auf denen das Windows 10 Creators Update ausgeführt wird, mit Windows Configuration Designer (WCD) in Azure Active Directory und Intune einbinden. Um die [MDM-Massenregistrierung](../enrollment/windows-bulk-enroll.md) für Ihren Azure AD-Mandanten zu aktivieren, erstellen Sie ein Bereitstellungspaket, das Geräte mithilfe von Windows Configuration Designer in Ihren Azure AD-Mandanten einbindet. Sie können das Paket auf alle unternehmenseigenen Geräte anwenden, die Sie per Massenvorgang registrieren und verwalten möchten. Nachdem das Paket auf Ihre Geräte angewendet wurde, werden die Geräte in Azure AD eingebunden und bei Intune registriert und sind dann bereit für die Anmeldung durch Ihre Azure AD-Benutzer.  Azure AD-Benutzer sind auf diesen Geräten Standardbenutzer und erhalten zugewiesene Richtlinien sowie erforderliche Apps. Die Verwendung von Self-Service-Funktionen und Unternehmensportalen wird derzeit nicht unterstützt.

### <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal--736542--"></a>Neuigkeiten in der öffentlichen Vorschau von Intune im Azure-Portal<!--736542-->

Anfang 2017 erfolgt die Migration der gesamten Administratoroberfläche zu Azure. Dies ermöglicht die leistungsstarke und integrierte Verwaltung von EMS-Kernworkflows in einer modernen, mit Grafik-APIs erweiterbaren Dienstplattform.

Neue Testmandanten sehen die öffentliche Vorschau der neuen Administratoroberfläche im Azure-Portal bereits in diesem Monat. Die Umgebung ist zwar noch in der Previewphase, schrittweise werden aber Funktionen und Parität zur vorhandenen Intune-Konsole bereitgestellt.

Die Administratoroberfläche im Azure-Portal verwendet die bereits angekündigten neuen Gruppierungs- und Zielgruppenadressierungsfunktionen. Bei der Migration eines vorhandenen Mandanten zur neuen Gruppierungsoberfläche erfolgt gleichzeitig die Migration zur Vorschau der neuen Administratoroberfläche auf Ihrem Mandanten. Wenn Sie in der Zwischenzeit bis zur Migration Ihres Mandanten einzelne neue Funktionen testen oder anschauen möchten, melden Sie sich für ein neues Intune-Testkonto an, oder sehen Sie sich die [neue Dokumentation](whats-new.md) an.

Neuigkeiten in der Intune-Vorschau in Azure finden Sie [hier](whats-new.md).

### <a name="notices"></a>Benachrichtigungen

#### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkter Zugriff auf Apple-Registrierungsszenarios <!--951869-->

Für Intune-Konten, die nach Januar 2017 erstellt wurden, hat Intune direkten Zugriff auf Apple-Registrierungsszenarien mithilfe der Workload „Geräte registrieren“ im Azure-Vorschauportal aktiviert. Bisher konnte nur über Links im Azure-Portal auf die Apple-Registrierungsvorschau zugegriffen werden. Vor Januar 2017 erstellte Intune-Konten erfordern eine einmalige Migration, bevor diese Features in Azure verfügbar sind. Der Zeitplan für die Migration wurde noch nicht angekündigt, aber Sie erfahren so bald wie möglich Näheres. Wir empfehlen Ihnen dringend, ein Testkonto zu erstellen, um die neue Oberfläche zu testen, wenn Sie mit Ihrem vorhandenen Konto nicht auf die Vorschau zugreifen können.

#### <a name="whats-coming-for-appx-in-intune-in-the-azure-portal----1000270---"></a>Anstehende Neuerungen bei APPX in Intune im Azure-Portal <!-- 1000270 -->

Im Rahmen der Migration zu Intune im Azure-Portal werden wir drei APPX-Änderungen vornehmen:

1. Einen neuen APPX-App-Typ in der Intune-Konsole hinzufügen, der nur für MDM-registrierte Geräte bereitgestellt werden kann
2. Den vorhandenen APPX-App-Typ nur für PCs wiederverwenden, die über den Intune PC-Agent verwaltet werden
3. Alle vorhandenen APPX-Formate in MDM-Formate mit der Migration konvertieren

##### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?

Diese Änderungen werden keine Ihrer vorhandenen Bereitstellungen auf Geräte beeinflussen, die über den Intune PC-Agent verwaltet werden. Nach der Migration können Sie diese migrierten APPX-Formate auf allen neuen Geräten bereitstellen, die über den Intune PC-Agent verwaltet wird und die zuvor noch nicht zugewiesen wurden.

##### <a name="what-action-do-i-need-to-take"></a>Was muss ich tun?

Nach der Migration müssen Sie die APPX erneut als PC-APPX hochladen, wenn Sie neue PC-Bereitstellungen machen möchten. Weitere Informationen finden Sie unter [APPX-Änderungen in Intune im Azure-Portal](https://aka.ms/appxchange) im Teamblog des Intune-Supports.  

#### <a name="administration-roles-being-replaced-in-azure-portal"></a>Administratorrollen werden im Azure-Portal ersetzt

Die in der Verwaltung mobiler Anwendungen (Mobile Application Management, MAM) vorhandenen Administratorrollen (Mitwirkender, Besitzer und Schreibgeschützt), die im klassischen Intune-Portal (Silverlight) verwendet werden, werden im Intune-Azure-Portal durch einen vollständigen Satz neuer rollenbasierter Zugriffssteuerung (Role-Based Access Control, RBAC) ersetzt. Nach der Migration zum Azure-Portal müssen Sie die Administratoren diesen neuen Administratorrollen neu zuweisen. Weitere Informationen zu RBAC und den neuen Rollen finden Sie unter [Rollenbasierte Zugriffssteuerung für Microsoft Intune](role-based-access-control.md).

### <a name="whats-coming"></a>Was steht an?

#### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Verbesserte Anmeldefunktion für alle Unternehmensportal-Apps auf allen Plattformen <!--User Story 1132123-->

Wir kündigen eine in den nächsten Monaten kommende Änderung an, durch die der Anmeldevorgang für die Intune-Unternehmensportal-Apps für Android, iOS und Windows verbessert wird. Die neue Benutzeroberfläche wird für die Unternehmensportal-App automatisch auf allen Plattformen eingeführt, sobald Azure AD die Änderung umsetzt. Darüber hinaus können Benutzer sich jetzt mithilfe eines generierten Codes zur einmaligen Verwendung von einem anderen Gerät aus beim Unternehmensportal anmelden. Dies ist besonders nützlich, wenn Benutzer sich ohne Anmeldeinformationen anmelden müssen.

Screenshots der vorherigen Anmeldeoberfläche, der neuen Anmeldeoberfläche mit Anmeldeinformationen und der neuen Anmeldeoberfläche zur Anmeldung von einem anderen Gerät aus finden Sie auf der Seite mit den [Neuerungen der App-Benutzeroberfläche](whats-new-app-ui.md).

#### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Stellen Sie sich auf eine Änderung ein: Intune ändert die Oberfläche des Intune-Partnerportals <!-- 1050016 -->

Ab dem Dienstupdate Mitte Mai 2017 entfernen wir die Intune-Partnerseite von manage.microsoft.com.  

Wenn Sie ein Partneradministrator sind, können Sie über die Intune-Partnerseite nicht mehr im Namen Ihrer Kunden Elemente anzeigen und Aktionen durchführen. Stattdessen müssen Sie sich bei einer der beiden anderen Partnerportale von Microsoft anmelden.

Sie können sich sowohl über das [Microsoft Partner Center](https://partnercenter.microsoft.com/) als auch über das [Microsoft 365 Admin Center](https://admin.microsoft.com/) bei den von Ihnen verwalteten Kundenkonten anmelden. Verwenden Sie als Partner künftig eine dieser Websites für die Verwaltung Ihrer Kunden.


#### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple erfordert Updates für die Transportsicherheit für Anwendungen <!--748318-->

Apple hat angekündigt, dass bestimmte Anforderungen für die Transportsicherheit für Anwendungen (Application Transport Security, ATS) erzwungen werden. ATS wird verwendet, um mehr Sicherheit für die gesamte App-Kommunikation über HTTPS zu erzwingen. Diese Änderung wirkt sich auf Intune-Kunden aus, die die iOS-Unternehmensportal-App verwenden.

Wir haben im Apple TestFlight-Programm eine Version der Unternehmensportal-App für iOS zur Verfügung gestellt, die die neuen ATS-Anforderungen erzwingt. Wenn Sie sie ausprobieren möchten, um Ihre ATS-Konformität zu testen, senden Sie eine E-Mail mit Angaben zu Vorname, Nachname, E-Mail-Adresse und Firmenname an <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a>. Unter [Intune support blog (Intune-Supportblog)](https://aka.ms/compportalats) finden Sie weitere Informationen.

## <a name="march-2017"></a>März 2017

### <a name="new-capabilities"></a>Neue Funktionen

#### <a name="support-for-skycure"></a>Unterstützung für Skycure

Sie können jetzt den Zugriff mobiler Geräte auf Unternehmensressourcen mit bedingtem Zugriff basierend auf Risikobewertungen steuern, die von Skycure vorgenommen werden, einer Mobile Threat Defense-Lösung, die mit Microsoft Intune zusammenarbeitet. Das Risiko wird basierend auf Telemetriedaten von Geräten bewertet, auf denen Skycure ausgeführt wird, wie z.B.:

- Physische Verteidigung
- Netzwerkverteidigung
- Anwendungsverteidigung
- Verteidigung gegen Sicherheitsrisiken

Sie können Richtlinien für bedingten EMS-Zugriff basierend auf Risikobewertungen von Symantec Endpoint Protection Mobile (Skycure) konfigurieren, die mithilfe von Intune-Gerätekonformitätsrichtlinien aktiviert werden. Sie können diese Richtlinien verwenden, um den Zugriff nicht kompatibler Geräte auf Unternehmensressourcen anhand der erkannten Bedrohungen zuzulassen oder zu blockieren. Weitere Informationen finden Sie unter [Symantec Endpoint Protection Mobile-Connector](../protect/skycure-mobile-threat-defense-connector.md).

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Neue Benutzeroberfläche für die Unternehmensportal-App für Android <!--621622-->

Die Unternehmensportal-App für Android aktualisiert ihre Benutzeroberfläche für ein moderneres Erscheinungsbild und höhere Benutzerfreundlichkeit. Wichtige Updates sind:

- Farben: Die IT-Abteilung kann die Färbung der Kopfzeilen der Registerkarte „Unternehmensportal“ dem Branding gemäß festlegen.
- Apps: Auf der Registerkarte **Apps** wurden die Schaltflächen **Empfohlene Apps** und **Alle Apps** aktualisiert.
- Suche: Auf der Registerkarte **Apps** ist die Schaltfläche **Suche** nun eine unverankerte interaktive Schaltfläche.
- Navigation in Apps: Die Ansicht **Alle Apps** enthält die Registerkartenansicht **Highlights**, **Alle** und **Kategorien**, um die Navigation zu vereinfachen.
- Unterstützung: Die Registerkarten **Meine Geräte** und **IT kontaktieren** werden aktualisiert, um die Lesbarkeit zu verbessern.

Ausführlichere Informationen zu diesen Änderungen finden Sie unter [Aktualisierungen für die Benutzeroberfläche für Endbenutzer-Apps in Intune](whats-new-app-ui.md).

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Nicht verwaltete Geräte können auf zugewiesene Apps zugreifen <!--664691-->

Als Teil der Designänderungen auf der Unternehmensportal-Website können iOS- und Android-Benutzer Apps installieren, die ihnen als „Verfügbar ohne Registrierung“ auf Ihren nicht verwalteten Geräten zugewiesen sind. Benutzer können sich mit ihren Intune-Anmeldeinformationen auf der Unternehmensportal-Website anmelden und die Liste der ihnen zugewiesenen Apps anzeigen. Die App-Pakete der Apps des Typs „Verfügbar ohne Registrierung“ werden zum Download über die Unternehmensportal-Website verfügbar gemacht. Apps, für die die Registrierung für die Installation erforderlich ist, sind durch diese Änderung nicht betroffen, da Benutzer aufgefordert werden, ihr Gerät zu registrieren, wenn sie diese Apps installieren möchten.

#### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Signierungsskript für das Windows 10-Unternehmensportal <!--941642-->

Wenn Sie die Windows 10-Unternehmensportal-App herunterladen und querladen möchten, steht Ihnen nun ein Skript zur Vereinfachung und Optimierung des App-Signierungsprozesses für Ihre Organisation zur Verfügung.   Das herunterladbare Skript sowie Informationen zu dessen Verwendung finden Sie bei TechNet unter [Microsoft Intune Signing Script for Windows 10 Company Portal](https://aka.ms/win10cpscript) (Microsoft Intune-Signierungsskript für das Windows 10-Unternehmensportal). Weitere Informationen zu dieser Ankündigung finden Sie im Blog des Intune-Supportteams unter [Updating your Windows 10 Company Portal app](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) (Aktualisieren Ihrer Windows 10-Unternehmensportal-App).


### <a name="notices"></a>Benachrichtigungen

#### <a name="support-for-ios-103"></a>Unterstützung für iOS 10.3

Die Version iOS 10.3 wurde am 27. März 2017 für iOS-Benutzer eingeführt. Alle vorhandenen Intune-MDM- und -MAM-Szenarios sind mit der neuesten Version des Apple-Betriebssystems kompatibel. Wir gehen davon aus, dass alle vorhandenen Intune-Features, die derzeit für die Verwaltung von iOS-Geräten verfügbar sind, weiterhin funktionieren werden, wenn Ihre Benutzer ihre Geräte und Apps auf iOS 10.3 aktualisieren.

Es gibt derzeit keine bekannten Probleme. Wenn Probleme mit iOS 10.3 auftreten, können Sie sich gerne an das [Intune-Supportteam](get-support.md) wenden.

#### <a name="improved-support-for-android-users-based-in-china---720444--"></a>Verbesserte Unterstützung für Android-Benutzer in China <!--720444-->

Da der Google Play Store in China nicht verfügbar ist, müssen Android-Geräte Apps von chinesischen Marktplätzen beziehen. Das Unternehmensportal unterstützt diesen Workflow durch Umleiten von Android-Benutzern in China, damit sie das Unternehmensportal und Outlook-Apps von lokalen App-Stores herunterladen können. Dies verbessert die Benutzerfreundlichkeit, wenn Richtlinien für bedingten Zugriff aktiviert sind, sowohl für die mobile Geräteverwaltung als auch die mobile Anwendungsverwaltung. Das Unternehmensportal und Outlook-Apps für Android sind in den folgenden chinesischen App-Stores verfügbar:

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

#### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>Bewährte Methode: Sicherstellen, dass die Unternehmensportal-Apps auf dem neuesten Stand sind <!--879465-->

Im Dezember 2016 haben wir ein Update veröffentlicht, das die Erzwingung der mehrstufigen Authentifizierung (multi-factor authentication, MFA) für eine Gruppe von Benutzern ermöglicht, wenn diese ein Gerät unter iOS, Android, Windows 8.1 (oder höher) oder Windows Phone 8.1 (oder höher) registrieren. Für dieses Feature werden bestimmte Basisversionen der Unternehmensportal-App für Android (ab v5.0.3419.0) und iOS (ab v2.1.17) benötigt.

Intune wird von Microsoft kontinuierlich verbessert, indem die Konsole und die Unternehmensportal-Apps für alle unterstützten Plattformen um neue Funktionen erweitert werden. Microsoft veröffentlicht deshalb nur Korrekturen für Probleme, die in der jeweils aktuellen Version der Unternehmensportal-App vorliegen. Wir empfehlen daher die Verwendung der jeweils neuesten Version der Unternehmensportal-Apps, um optimale Ergebnisse zu erzielen.

>[!Tip]
> Stellen Sie sicher, dass die Benutzer auf ihren Geräten die automatische Aktualisierung von Apps über den entsprechenden App Store konfiguriert haben. Wenn Sie die Android-Unternehmensportal-App über eine Netzwerkfreigabe bereitgestellt haben, können Sie die neueste Version aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=49140) herunterladen.

#### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>Microsoft Teams nun für MAM unter iOS und Android verfügbar

Microsoft hat die allgemeine Verfügbarkeit von Microsoft Teams angekündigt. Die aktualisierten Microsoft Teams-Apps für iOS und Android verfügen nun über Funktionen für die mobile App-Verwaltung (Mobile App Management, MAM) mit Intune. Ihre Teams profitieren dadurch von einer flexiblen geräteübergreifenden Arbeitsweise, und Gespräche sowie Unternehmensdaten sind in jeder Phase bestens geschützt. Ausführlichere Informationen finden Sie in der [Microsoft-Teams-Ankündigung](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) des Enterprise Mobility and Security-Blogs.


## <a name="february-2017"></a>Februar 2017

### <a name="new-capabilities"></a>Neue Funktionen

### <a name="modernizing-the-company-portal-website---753980--"></a>Modernisieren der Unternehmensportal-Website <!--753980-->
Die Unternehmensportal-Website wird Apps unterstützen, die für Benutzer bestimmt sind, die über keine verwalteten Geräte verfügen. Die Website wird an andere Microsoft-Produkte und -Dienste mithilfe eines neuen Farbschemas, dynamischen Illustrationen und einem „Hamburger-Menü“ ausgerichtet, ![Miniaturansicht des Hamburger-Menüs, das nun in der linken oberen Ecke der Unternehmensportal-App zu sehen ist,](./media/whats-new-archive-classic/CP_hamburger_menu.png).

### <a name="notices"></a>Benachrichtigungen

#### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>Die Gruppenmigration erfordert keine Updates für Gruppen oder Richtlinien für iOS-Geräte <!--898837-->
Es wird während der Migration auf Azure Active Directory-Gerätegruppen für jede Intune-Gerätegruppe, die durch ein Profil für die Unternehmensgeräteregistrierung vorab zugewiesen ist, eine entsprechende dynamische Gerätegruppe in AAD auf Grundlage des Profilnamens der Unternehmensgeräteregistrierung erstellt. Dadurch wird sichergestellt, dass während der Registrierung der Geräte diese automatisch gruppiert werden und die gleichen Richtlinien und Apps wie die ursprüngliche Intune-Gruppe erhalten.

Sobald ein Mandant den Migrationsprozess zur Gruppierung und Adressierung beitritt, erstellt Intune automatisch eine dynamische AAD-Gruppe, die einer Intune-Gruppe entspricht, die das Ziel eines Profils für die Unternehmensgeräteregistrierung ist. Wenn der Intune-Administrator die Intune-Gruppe löscht, auf die abgezielt wurde, wird die entsprechende dynamische AAD-Gruppe nicht gelöscht. Die Mitglieder der Gruppe sowie die dynamische Abfrage werden deaktiviert, jedoch wird die Gruppe selbst so lange beibehalten, bis der IT-Administrator diese über das AAD-Portal entfernt.

Genauso wird Intune eine dynamische Gruppe erstellen, wenn der IT-Administrator die Einstellung ändert, auf welche Gruppe durch das Profil für die Unternehmensgeräteregistrierung abgezielt wird, die die neue Profilzuweisung widerspiegelt, jedoch nicht die für die alte Zuweisung erstellte dynamische Gruppe entfernen.

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Standardverwaltung von Windows-Desktopgeräten über Windows-Einstellungen <!--663050-->
Das Standardverhalten für die Registrierung von Windows 10-Geräten ändert sich. Neue Registrierungen erfolgen gemäß dem typischen Registrierungsprozess über den MDM-Agent, nicht mehr über den PC-Agent. Windows 10-Desktopbenutzer erhalten auf der Unternehmensportal-Website Registrierungsanweisungen, die sie durch den Prozess zum Hinzufügen von Windows 10-Desktopcomputern als mobile Geräte leiten. Dies wirkt sich nicht auf aktuell bereits registrierte PCs aus, und Ihre Organisation kann [auf Wunsch](../manage-windows-pcs-with-microsoft-intune.md) Windows 10-Desktops weiterhin über den PC-Agent verwalten.

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Verbesserte Unterstützung der Verwaltung mobiler Apps für das selektive Zurücksetzen <!--581242-->
Benutzer erhalten zusätzliche Anleitungen, um erneut Zugriff auf Geschäfts-, Schul- oder Unidaten zu erhalten, wenn diese Daten aufgrund der Richtlinie „Offline-Intervall, bevor App-Daten zurückgesetzt werden“ automatisch entfernt wurden.<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Links im Unternehmensportal für iOS werden innerhalb der App geöffnet <!--665954-->
Links in der Unternehmensportal-App für iOS, einschließlich Links zu Dokumentationen und Apps, werden über eine In-App-Ansicht von Safari direkt in der Unternehmensportal-App geöffnet. Dieses Update wird getrennt vom Dienstupdate im Januar ausgeliefert.

#### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Neue MDM-Serveradresse für Windows-Geräte <!--893007-->
Windows- und Windows Phone-Benutzer sind beim Versuch, ein Gerät zu registrieren, nicht erfolgreich, wenn Sie als MDM-Serveradresse __manage.microsoft.com__ eingeben (wenn Sie dazu aufgefordert werden). Die MDM-Serveradresse ändert sich von __manage.microsoft.com__ zu __enrollment.manage.microsoft.com__. Informieren Sie Ihre Benutzer, dass Sie nun als MDM-Serveradresse __enrollment.manage.microsoft.com__ verwenden sollen, wenn Sie zur Eingabe während der Registrierung eines Windows- oder Windows Phone-Geräts aufgefordert werden. Für das CNAME-Setup sind keine Änderungen erforderlich. Weitere Informationen zu dieser Änderung finden Sie unter [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Neue Benutzeroberfläche für die Unternehmensportal-App für Android <!--621622-->
Ab März befolgt die Unternehmensportal-App für Android die [material design guidelines (Richtlinien für Materialdesign)](https://material.io/guidelines/material-design/introduction.html), um ein moderneres Erscheinungsbild zu vermitteln. Diese verbesserte Benutzeroberfläche enthält Folgendes:

* __Farben__: Die Farben der Registerkartentitel können mithilfe Ihrer benutzerdefinierten Farbpalette angepasst werden.
* __Schnittstelle__: Die Schaltflächen „Empfohlene Apps“ und „Alle Apps“ wurden in der Registerkarte „Apps“ aktualisiert. Die Schaltfläche „Suche“ ist nun eine unverankerte interaktive Schaltfläche.
* __Navigation__: Alle Apps zeigen die Registerkartenansicht „Highlights“, „Alle“ und „Kategorien“ für die einfachere Navigation an.
* __Dienst__: Für die Registerkarten „Meine Geräte“ und „IT kontaktieren“ wurde die Lesbarkeit verbessert.

Sie finden Vorher- und Nachherbilder auf der Seite [Änderungen an der Intune App-Benutzeroberfläche](whats-new-app-ui.md).

### <a name="associate-multiple-management-tools-with-the-microsoft-store-for-business---926135--"></a>Zuordnen mehrerer Verwaltungstools zum Microsoft Store für Unternehmen <!--926135-->
Wenn Sie mehr als ein Verwaltungstool zum Bereitstellen des Microsoft Store für Unternehmen-Apps verwenden, konnten Sie vorher nur eine App dem Microsoft Store für Unternehmen zuordnen. Nun können Sie mehrere Verwaltungstools dem Store zuordnen, z.B. Intune und Configuration Manager. Einzelheiten finden Sie unter [Manage apps you purchased from the Microsoft Store for Business with Microsoft Intune](../apps/windows-store-for-business.md) (Verwalten von Apps, die im Microsoft Store für Unternehmen erworben wurden, mit Microsoft Intune).

## <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal---736542--"></a>Neuigkeiten in der öffentlichen Vorschau von Intune im Azure-Portal <!--736542-->

Anfang 2017 erfolgt die Migration der gesamten Administratoroberfläche zu Azure. Dies ermöglicht die leistungsstarke und integrierte Verwaltung von EMS-Kernworkflows in einer modernen, mit Grafik-APIs erweiterbaren Dienstplattform.

Neue Testmandanten sehen die öffentliche Vorschau der neuen Administratoroberfläche im Azure-Portal bereits in diesem Monat. Die Umgebung ist zwar noch in der Previewphase, schrittweise werden aber Funktionen und Parität zur vorhandenen Intune-Konsole bereitgestellt.

Die Administratoroberfläche im Azure-Portal verwendet die bereits angekündigten neuen Gruppierungs- und Zielgruppenadressierungsfunktionen. Bei der Migration eines vorhandenen Mandanten zur neuen Gruppierungsoberfläche erfolgt gleichzeitig die Migration zur Vorschau der neuen Administratoroberfläche auf Ihrem Mandanten. Wenn Sie in der Zwischenzeit bis zur Migration Ihres Mandanten einzelne neue Funktionen testen oder anschauen möchten, melden Sie sich für ein neues Intune-Testkonto an, oder sehen Sie sich die [neue Dokumentation](whats-new.md) an.

Neuigkeiten in der Intune-Vorschau in Azure finden Sie [hier](whats-new.md).

## <a name="january-2017"></a>Januar 2017

### <a name="new-capabilities"></a>Neue Funktionen

#### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>Konsoleninterne Berichte für MAM ohne Registrierung <!--677961-->
Es wurden neue App-Schutzberichte sowohl für registrierte als auch nicht registrierte Geräte hinzugefügt. Erfahren Sie mehr über das [Überwachen von Verwaltungsrichtlinien für mobile Apps mit Intune](../apps/app-protection-policies-monitor.md).

#### <a name="android-711-support---694397--"></a>Android 7.1.1-Unterstützung <!--694397-->
Intune unterstützt und verwaltet Android 7.1.1 jetzt vollständig.

#### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>Lösen von Problemen, wenn iOS-Geräte inaktiv sind oder die Verwaltungskonsole nicht mit ihnen kommunizieren kann <!--unknown-->
Wenn Geräte von Benutzern keinen Kontakt mehr mit Intune haben, können Sie neue Schritte zur Problembehandlung bereitstellen, damit sie erneuten Zugriff auf Unternehmensressourcen gewinnen können. Weitere Informationen finden Sie unter [Geräte sind inaktiv oder die Verwaltungskonsole kann nicht mit ihnen kommunizieren](../enrollment/troubleshoot-device-enrollment-in-intune.md#devices-are-inactive-or-the-admin-console-cant-communicate-with-them).

### <a name="notices"></a>Benachrichtigungen

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Standardverwaltung von Windows-Desktopgeräten über Windows-Einstellungen <!--663050-->
Das Standardverhalten für die Registrierung von Windows 10-Geräten ändert sich. Neue Registrierungen erfolgen gemäß dem typischen Registrierungsprozess über den MDM-Agent, nicht mehr über den PC-Agent.

Windows 10-Desktopbenutzer erhalten auf der Unternehmensportal-Website Registrierungsanweisungen, die sie durch den Prozess zum Hinzufügen von Windows 10-Desktopcomputern als mobile Geräte leiten. Dies wirkt sich nicht auf aktuell bereits registrierte PCs aus, und Ihre Organisation kann [auf Wunsch](../manage-windows-pcs-with-microsoft-intune.md) Windows 10-Desktops weiterhin über den PC-Agent verwalten.

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Verbesserte Unterstützung der Verwaltung mobiler Apps für das selektive Zurücksetzen <!--581242-->
Benutzer erhalten zusätzliche Anleitungen, um erneut Zugriff auf Geschäfts-, Schul- oder Unidaten zu erhalten, wenn diese Daten aufgrund der Richtlinie „Offline-Intervall, bevor App-Daten zurückgesetzt werden“ automatisch entfernt wurden.<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Links im Unternehmensportal für iOS werden innerhalb der App geöffnet <!--665954-->
Links in der Unternehmensportal-App für iOS, einschließlich Links zu Dokumentationen und Apps, werden über eine In-App-Ansicht von Safari direkt in der Unternehmensportal-App geöffnet. Dieses Update wird getrennt vom Dienstupdate im Januar ausgeliefert.

#### <a name="modernizing-the-company-portal-website---753980--"></a>Modernisieren der Unternehmensportal-Website <!--753980-->
Ab Februar unterstützt die Unternehmensportal-Website Apps, die für Benutzer bestimmt sind, die über keine verwalteten Geräte verfügen. Die Website wird an andere Microsoft-Produkte und -Dienste mithilfe eines neuen Farbschemas, dynamischen Illustrationen und einem „Hamburger-Menü“ ausgerichtet, ![Hamburger-Menü der Unternehmensportal-Website](./media/whats-new-archive-classic/CP_hamburger_menu.png).

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>Neue Dokumentation für App-Schutzrichtlinien <!--583398-->
Wir haben unsere Dokumentation für Administratoren und App-Entwickler aktualisiert, die App-Schutzrichtlinien (so genannte MAM-Richtlinien) mit dem Intune App Wrapping Tool oder dem Intune App SDK in ihren iOS- und Android-Apps aktivieren möchten.

Die folgenden Artikel wurden aktualisiert:

* [Auswählen der Vorbereitung von Apps für die mobile Anwendungsverwaltung mit Microsoft Intune](../developer/apps-prepare-mobile-application-management.md)
* [Vorbereiten von iOS-Apps für die Verwaltung mobiler Anwendungen mit dem Intune App Wrapping Tool](../developer/app-wrapper-prepare-ios.md)
* [Erste Schritte mit dem Microsoft Intune App SDK](../developer/app-sdk-get-started.md)
* [Intune App SDK für iOS – Entwicklerhandbuch](../developer/app-sdk-ios.md)

Folgende Artikel wurden der Dokumentbibliothek neu hinzugefügt:

* [Intune App SDK-Cordova-Plug-In](../developer/app-sdk.md)
* [Intune App SDK-Xamarin-Komponente](../developer/app-sdk-xamarin.md)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>Statusanzeige beim Starten des Unternehmensportals in iOS <!--665978-->
Für das Unternehmensportal für iOS wurde eine Statusanzeige auf dem Startbildschirm eingeführt, um den Benutzer über die Prozesse zu informieren, die gerade geladen werden. Die Einführung der Statusanzeige, die das Drehfeld ersetzt, wird in mehreren Phasen erfolgen. Dies bedeutet, dass einige Ihrer Benutzer bereits die neue Statusanzeige sehen, andere dagegen noch das Drehfeld.

## <a name="december-2016"></a>Dezember 2016

### <a name="public-preview-of-intune-in-the-azure-portal--736542--"></a>Öffentliche Vorschau von Intune im Azure-Portal<!--736542-->
Anfang 2017 erfolgt die Migration der gesamten Administratoroberfläche zu Azure. Dies ermöglicht die leistungsstarke und integrierte Verwaltung von EMS-Kernworkflows in einer modernen, mit Grafik-APIs erweiterbaren Dienstplattform. Im Vorfeld der allgemeinen Verfügbarkeit dieses Portals für alle Intune-Mandanten freuen wir uns, bekannt geben zu können, dass noch in diesem Monat mit dem Rollout einer Vorschau dieser neuen Verwaltungsoberfläche für ausgewählte Mandanten begonnen wird.

Die Administratoroberfläche im Azure-Portal verwendet die bereits angekündigten neuen Gruppierungs- und Zielgruppenadressierungsfunktionen. Bei der Migration eines vorhandenen Mandanten zur neuen Gruppierungsoberfläche erfolgt gleichzeitig die Migration zur Vorschau der neuen Administratoroberfläche auf Ihrem Mandanten. In der Zwischenzeit erfahren Sie im Azure-Portal in der [neuen Dokumentation](what-is-intune.md) mehr über die Neuigkeiten zu Microsoft Intune.

__Integration der Verwaltung der Telekommunikationsausgaben in der öffentlichen Vorschau des Azure-Portals__ <!--747605-->
Aktuell beginnt die Vorschau der Integration mit TEM-Diensten (Telecom Expense Management) von Drittanbietern im Azure-Portal. Mit Intune können Sie Beschränkungen für das Datenroaming im In- und Ausland erzwingen. Diese Integrationen starten mit [Saaswedo](http://www.saaswedo.com/). Wenn Sie dieses Feature in Ihrem Testmandanten aktivieren möchten, [wenden Sie sich bitte an den Microsoft-Support](get-support.md).

### <a name="new-capabilities"></a>Neue Funktionen

__Mehrstufige Authentifizierung auf allen Plattformen__ <!--747590-->
Sie können die mehrstufige Authentifizierung jetzt für eine ausgewählte Gruppe von Benutzern erzwingen, wenn diese ein iOS- oder Android-Gerät bzw. ein Gerät mit Windows 8.1 und höher oder Windows Phone 8.1 und höher über das Azure-Verwaltungsportal registrieren möchten. Dazu konfigurieren Sie MFA in der Microsoft Intune-Registrierungsanwendung in Azure Active Directory.

__Einschränken der Registrierung von mobilen Geräten__ <!--747596-->
Es wurden neue Registrierungseinschränkungen zu Intune hinzugefügt, mit denen sich kontrollieren lässt, welche Mobilgeräteplattformen für die Registrierung zugelassen werden. Intune unterscheidet dabei zwischen den Mobilgeräteplattformen iOS, macOS, Android, Windows und Windows Mobile.
* Durch das Einschränken der Registrierung von Mobilgeräten wird die Registrierung von PC-Clients nicht eingeschränkt.
* Für iOS gibt es eine zusätzliche Option, mit der die Registrierung persönlicher Geräte blockiert werden kann.

Intune kennzeichnet alle neuen Geräte als persönlich, es sei denn, der IT-Administrator kennzeichnet sie als unternehmenseigen – wie in [diesem Artikel](../enrollment/device-enrollment.md) beschrieben.

### <a name="notices"></a>Benachrichtigungen

__Die mehrstufige Authentifizierung bei der Registrierung wechselt zum Azure-Portal__ <!--VSO 750545-->
Bisher mussten sich Administratoren entweder bei der Intune-Konsole oder der Configuration Manager-Konsole (vor der Version von Oktober 2016) anmelden, um MFA für Intune-Registrierungen festzulegen. Mit diesem aktualisierten Feature melden Sie sich jetzt mit Ihren Intune-Anmeldeinformationen beim [Microsoft Azure-Portal](https://manage.windowsazure.com) an und konfigurieren die MFA-Einstellungen über Azure AD. Weitere Informationen dazu finden Sie [hier](https://aka.ms/mfa_ad).

__Die Unternehmensportal-App für Android ist jetzt in China verfügbar__ <!--VSO 658093-->
Die Unternehmensportal-App für Android wird jetzt zum Download in China veröffentlicht. Da der Google Play Store in China nicht zur Verfügung steht, müssen Apps für Android-Geräte von chinesischen App-Marktplätzen abgerufen werden. Die Unternehmensportal-App für Android wird in den folgenden Stores zum Download zur Verfügung stehen:
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

In der Unternehmensportal-App für Android erfolgt die Kommunikation mit dem Microsoft Intune-Dienst über Google Play-Dienste. Da Google Play Services in China noch nicht verfügbar sind, kann die Ausführung der folgenden Aufgaben bis zu 8 Stunden dauern.

|Intune-Administratorkonsole| Intune-Unternehmensportal-App für Android |Intune Unternehmensportalwebsite|
|---|---|---|
|Vollständiges Zurücksetzen| Entfernen eines Remotegeräts| Entfernen eines Geräts (lokal und remote)|
|Selektives Zurücksetzen| Zurücksetzen eines Geräts| Zurücksetzen eines Geräts|
|Neue oder aktualisierte App-Bereitstellungen| Installieren verfügbarer branchenspezifischer Apps| Zurücksetzen der Gerätekennung|
|Remotesperre|||
|Zurücksetzen der Kennung|||

### <a name="deprecations"></a>Veraltete Funktionen

__Silverlight wird von Firefox nicht mehr unterstützt__ <!--VSO TBA-->
Mozilla entfernt die Unterstützung für Silverlight in Version 52 des [Firefox-Browsers](https://www.mozilla.org/firefox) ab März 2017. Bei der vorhandenen Intune-Konsole Daher werden Sie sich mit Firefox-Versionen nach Version 51 nicht mehr anmelden können. Wir empfehlen, für den Zugriff auf die Verwaltungskonsole Internet Explorer 10 oder 11 oder eine [Firefox-Version vor Version 52](https://ftp.mozilla.org/pub/firefox/releases/) zu verwenden. Durch den Übergang von Intune zum Azure-Portal wird die Unterstützung einer Reihe von [modernen Browsern](/azure/azure-preview-portal-supported-browsers-devices) ohne Abhängigkeit von Silverlight möglich.

__Entfernen von Richtlinien für das mobile Exchange Online-Postfach__ <!--770687-->
Seit Dezember können Administratoren Richtlinien für das mobile Exchange Online-Postfach (EAS) nicht mehr in der Intune-Konsole anzeigen oder konfigurieren. Das Rollout dieser Änderung erfolgt für alle Intune-Mandanten im Laufe des Dezembers und Januars. Die Konfiguration aller vorhandenen Richtlinien bleibt unverändert. Verwenden Sie zum Konfigurieren neuer Richtlinien die Exchange-Verwaltungsshell. Weitere Informationen finden Sie [hier](https://technet.microsoft.com/library/bb123783%28v=exchg.150%29.aspx).

__Intune AV Player-, Image Viewer- und PDF Viewer-Apps werden unter Android nicht mehr unterstützt__ <!--747553-->
Ab Mitte Dezember 2016 können Benutzer die Intune AV-Player-, Image Viewer- und PDF Viewer-Apps nicht mehr verwenden. Diese Apps wurden durch die Azure Information Protection-App ersetzt. [Hier](/information-protection/rms-client/mobile-app-faq) erfahren Sie mehr über die Azure Information Protection-App.

## <a name="november-2016"></a>November 2016

### <a name="new-capabilities"></a>Neue Funktionen

__Neues Microsoft Intune-Unternehmensportal für Windows 10-Geräte__ Microsoft hat eine neue [Microsoft Intune-Unternehmensportal-App für Windows 10-Geräte](https://www.microsoft.com/store/apps/9wzdncrfj3pz) veröffentlicht. Diese App, die das neue universelle Windows 10-Format nutzt, bietet dem Benutzer eine aktualisierte Benutzeroberfläche innerhalb der App und identische Oberflächen auf allen Windows 10-Geräten – sowohl PCs als auch mobilen Geräten – sowie all die Funktionen, die er heute bereits verwendet.

Mit der neuen App können Benutzer auch zusätzliche Plattformfunktionen wie einmaliges Anmelden (SSO) und die zertifikatbasierte Authentifizierung auf Windows 10-Geräten nutzen. Die App wird als Upgrade der vorhandenen Windows 8.1- und Windows Phone 8.1-Unternehmensportalinstallationen im Microsoft Store zur Verfügung gestellt. Weitere Informationen finden Sie unter [aka.ms/intunecp_universalapp](https://aka.ms/intunecp_universalapp).

> [!IMPORTANT]
> __Neues in Intune und Android for Work__ Wenn Ihre Intune-Gruppen zur neuen Azure AD-Gruppenoberfläche migriert wurden, können Sie Apps nur als __Verfügbar__ bereitstellen, während Sie Android for Work-Apps mit der Aktion __Erforderlich__ bereitstellen können.

__Das Intune App SDK Cordova-Plug-In unterstützt nun MAM ohne Registrierung__ App-Entwickler können das Intune App SDK Cordova-Plug-In jetzt verwenden, um MAM-Funktionen ohne Geräteregistrierung in ihren auf Cordova basierenden Apps für Android und iOS/iPadOS zu aktivieren. Sie finden das Intune App SDK Cordova-Plug-in [hier](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam).

__Die Intune App SDK Xamarin-Komponente unterstützt nun MAM ohne Registrierung__ App-Entwickler können die Intune App SDK Xamarin-Komponente jetzt verwenden, um MAM-Funktionen ohne Geräteregistrierung in ihren auf Xamarin basierenden Apps für Android und iOS/iPadOS zu aktivieren. Sie finden die Intune App SDK Xamarin-Komponente [hier](https://github.com/msintuneappsdk/intune-app-sdk-xamarin).

### <a name="notices"></a>Benachrichtigungen

__Kein signiertes Windows Phone 8-Unternehmensportal zum Hochladen des Symantec-Signaturzertifikats mehr erforderlich__ Zum Hochladen des Symantec-Signaturzertifikats ist keine signierte Windows Phone 8-Unternehmensportal-App mehr erforderlich. Das Zertifikat kann einzeln hochgeladen werden.

### <a name="deprecations"></a>Veraltete Funktionen

__Unterstützung für das Windows Phone 8-Unternehmensportal__ Die Unterstützung für das Windows Phone 8-Unternehmensportal wird jetzt beendet. Die Unterstützung für Windows Phone 8- und WinRT-Plattformen wurde im Oktober 2016 beendet. Die Unterstützung für das Windows Phone 8-Unternehmensportal wurde ebenfalls im Oktober 2016 beendet.


## <a name="see-also"></a>Weitere Informationen:
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).
