---
title: Early Edition | Microsoft-Dokumentation
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 5f172290d493717308446c4f9e2313a03ba8f3aa
ms.openlocfilehash: d7f25657fc7cfb9298809f76f198810718e58c39
ms.lasthandoff: 04/27/2017


---


# <a name="the-early-edition-for-microsoft-intune---april-2017"></a>Die Early Edition für Microsoft Intune – April 2017

Die **Early Edition** enthält eine Liste der Funktionen, die in späteren Versionen von Microsoft Intune zur Verfügung stehen werden. Diese Informationen werden unter dem Geheimhaltungsvertrag auf einer sehr begrenzten Basis bereitgestellt und Änderungen sind vorbehalten. Einige der hier aufgeführten Features werden möglicherweise bis zum Stichtag nicht fertig und werden erst in eine spätere Version aufgenommen. Andere Features werden in einer Pilotphase getestet (Test-Flighting), um sicherzustellen, dass sie für Kunden bereit sind. Wenden Sie sich an Ihren Intune-/PM-Kontakt, wenn Sie Fragen oder Bedenken haben.

Diese Seite wird regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen. 

> [!Note]
> Die folgenden Änderungen sind in der Entwicklung für Intune. Alle diese Features werden letztlich auch für hybride Kundenbereitstellungen (Configuration Manager mit Intune) unterstützt. Weitere Informationen zu neuen hybriden Features finden Sie auf unserer [Seite mit neuen hybriden Funktionen](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Neue Funktionen

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Verbesserter App-Installationsstatus für die Windows 10-Unternehmensportal-App <!--676495-->

Die Windows 10-Unternehmensportal-App bietet jetzt eine Statusanzeige zur Installation der App für alle modernen App-Installationen aus dem Unternehmensportal. Die neuen Statusmeldungen für die Unternehmensportal-App für Windows 10 finden Sie auf der Seite [Aktualisierungen für die Benutzeroberfläche der Intune-App](whats-new-in-intune-app-ui.md).

### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>Verbesserte Statusnachrichten in der Unternehmensportal-App für iOS <!--744866-->

Neue, genauere Fehlermeldungen werden nun in der Unternehmensportal-App für iOS angezeigt, um einfacher Informationen darüber zu erhalten, was gerade auf Geräten geschieht. Diese Fehlerfälle waren zuvor in einer allgemeinen Fehlermeldung enthalten: „Unternehmensportal vorübergehend nicht verfügbar“. Wenn ein Benutzer darüber hinaus das Unternehmensportal unter iOS startet, wenn keine Internetverbindung vorhanden ist, wird keine beständige Statusleiste auf der Startseite angezeigt, die angibt: „Keine Internetverbindung“.

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps verfügbar für Managed Browser <!--822308, 822303-->

Microsoft MyApps verfügen jetzt über eine bessere Unterstützung innerhalb von Managed Browser. Managed Browser-Benutzer, die nicht für die Verwaltung vorgesehen sind, werden direkt an den MyApps-Dienst weitergeleitet, wo sie auf ihre durch den Administrator bereitgestellte SaaS-Apps zugreifen können. Benutzer, die für die Verwendung für die Intune-Verwaltung ausgelegt sind, können weiterhin auf MyApps vom integrierten Managed Browser-Lesezeichen aus zugreifen.

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Neue Symbole für Managed Browser und das Unternehmensportal <!--918433, 918431-->

Managed Browser erhält aktualisierte Symbole für die Android- und iOS-Versionen der App. Das neue Symbol enthält den aktualisierten Intune-Badge, damit es konsistenter mit anderen Apps in Enterprise Mobility + Security (EM+S) wird. Sie können das neue Symbol für Managed Browser auf der Seite [Aktualisierungen für die Benutzeroberfläche für Endbenutzer-Apps in Intune](whats-new-in-intune-app-ui.md) finden.

Das Unternehmensportal erhält auch aktualisierte Symbole für die Android-, iOS- und Windows-Versionen der App, um die Konsistenz mit anderen Apps in EM+S zu verbessern. Diese Symbole werden schrittweise auf Plattformen von April bis Ende Mai veröffentlicht.

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Unterstützung für einmaliges Anmelden über das Unternehmensportal für iOS zu Outlook für iOS <!--834012-->

Benutzer müssen sich nicht mehr in der Outlook-App anmelden, wenn sie in der Unternehmensportal-App für iOS auf dem gleichen Gerät mit dem gleichen Konto angemeldet sind. Wenn Benutzer die Outlook-App starten, können sie ihr Konto auswählen und sich automatisch anmelden. Wir arbeiten auch daran, diese Funktion für andere Microsoft-Apps hinzuzufügen.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Statusanzeige zur Anmeldung im Android-Unternehmensportal <!--953374-->

Ein Update auf die Android-Unternehmensportal-App zeigt eine Statusanzeige der Anmeldung an, wenn der Benutzer die App startet oder fortsetzt. Der Indikator durchläuft neue Status, beginnend mit „Verbinden...“, „Anmelden...“, dann „Checking for security requirements...“ (Suche nach Sicherheitsanforderungen...), bevor dem Benutzer erlaubt wird, auf die App zuzugreifen. Sie können die neuen Bildschirme für die Unternehmensportal-App auf der Seite [Aktualisierungen für die Benutzeroberfläche für Endbenutzer-Apps in Intune](whats-new-in-intune-app-ui.md) finden.


## <a name="notices"></a>Benachrichtigungen

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple erfordert Updates für die Transportsicherheit für Anwendungen <!--748318-->

Apple hat angekündigt, dass sie ab Frühjahr 2017 bestimmte Anforderungen für die Transportsicherheit für Anwendungen (Application Transport Security, ATS) erzwingen werden. ATS wird verwendet, um eine strengere Sicherheit in allen App-Kommunikationen über HTTPS zu erzwingen. Diese Änderung wirkt sich auf Intune-Kunden aus, die die iOS-Unternehmensportal-App verwenden. Unter [Intune support blog (Intune-Supportblog)](https://aka.ms/compportalats) finden Sie weitere Informationen.

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkter Zugriff auf Apple-Registrierungsszenarien <!--951869-->

Für Intune-Konten, die nach Januar 2017 erstellt wurden, hat Intune direkten Zugriff auf Apple-Registrierungsszenarien mithilfe der Workload „Geräte registrieren“ im Azure-Vorschauportal aktiviert. Bisher konnte nur über Links im klassischen Intune-Portal auf die Apple-Registrierungsvorschau zugegriffen werden. Vor Januar 2017 erstellte Intune-Konten erfordern eine einmalige Migration, bevor diese Features in Azure verfügbar sind. Der Zeitplan für die Migration wurde noch nicht angekündigt, aber Sie erfahren so bald wie möglich Näheres. Wir empfehlen Ihnen dringend, ein Testkonto zu erstellen, um die neue Oberfläche zu testen, wenn Sie mit Ihrem vorhandenen Konto nicht auf die Vorschau zugreifen können.

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Was für APPX in Intune unter Azure bereitsteht <!-- 1000270 -->

Als Teil der Migration zu Intune unter Azure werden wir drei APPX-Änderungen vornehmen:

1. Einen neuen APPX-App-Typ in der klassischen Intune-Verwaltungskonsole hinzufügen, der nur für MDM-registrierte Geräte bereitgestellt werden kann
2. Den vorhandenen APPX-App-Typ nur für PCs wiederverwenden, die über den Intune PC-Agent verwaltet werden
3. Alle vorhandenen APPX-Formate in MDM-Formate mit der Migration konvertieren

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?

Diese Änderungen werden keine Ihrer vorhandenen Bereitstellungen auf Geräte beeinflussen, die über den Intune PC-Agent verwaltet werden. Nach der Migration können Sie diese migrierten APPX-Formate auf allen neuen Geräten bereitstellen, die über den Intune PC-Agent verwaltet wird und die zuvor noch nicht zugewiesen wurden.

#### <a name="what-action-do-i-need-to-take"></a>Was muss ich tun?

Nach der Migration müssen Sie die APPX erneut als PC-APPX hochladen, wenn Sie neue PC-Bereitstellungen machen möchten. Weitere Informationen finden Sie unter [Appx changes in Intune on Azure (APPX-Änderungen in Intune unter Azure)](https://aka.ms/appxchange) im Intune-Support-Teamblog.  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Öffentliche Vorschau der neuen Intune-Administratoroberfläche in Azure <!--736542-->

Anfang 2017 erfolgt die Migration der gesamten Administratoroberfläche zu Azure. Dies ermöglicht die leistungsstarke und integrierte Verwaltung von EMS-Kernworkflows in einer modernen, mit Grafik-APIs erweiterbaren Dienstplattform.

Neue Testmandanten sehen die öffentliche Vorschau der neuen Administratoroberfläche im Azure-Portal bereits in diesem Monat. Die Umgebung ist zwar noch in der Previewphase, schrittweise werden aber Funktionen und Parität zur vorhandenen Intune-Konsole bereitgestellt.

Die Administratoroberfläche im Azure-Portal verwendet die bereits angekündigten neuen Gruppierungs- und Zielgruppenadressierungsfunktionen. Bei der Migration eines vorhandenen Mandanten zur neuen Gruppierungsoberfläche erfolgt gleichzeitig die Migration zur Vorschau der neuen Administratoroberfläche auf Ihrem Mandanten. Wenn Sie in der Zwischenzeit bis zur Migration Ihres Mandanten einzelne neue Funktionen testen oder anschauen möchten, melden Sie sich für ein neues Intune-Testkonto an, oder sehen Sie sich die [neue Dokumentation](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune) an.

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Unterstützung für verwaltete Konfigurationsoptionen für Android-Apps <!-- 621621 -->

Android-Apps im Play Store, die verwaltete Konfigurationsoptionen unterstützen, können von Intune konfiguriert werden.  Mit dieser Funktion kann die IT die Liste der Konfigurationswerte sehen, die von einer App unterstützt werden, und es wird eine übersichtliche, hochwertige Benutzeroberfläche bereitgestellt, damit die IT diese Werte konfigurieren kann.

### <a name="remote-assistance-for-android-devices----675418---"></a>Remoteunterstützung für Android-Geräte <!-- 675418 -->

In Intune wird die nicht im Lieferumfang inbegriffene [TeamViewer](https://www.teamviewer.com)-Software verwendet, damit Sie Ihren Benutzern, die Android-Geräte ausführen, Remoteunterstützung bieten können.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Neue Android-Richtlinie für komplexe PINs <!-- 722069 -->

Sie können einen erforderlichen numerisch, komplexen Kennworttyp in einem Android-Geräteprofil für Geräte festlegen, die unter Android 5.0 und höher ausgeführt werden.  Verwenden Sie diese Einstellung, um zu verhindern, dass Benutzer eine PIN erstellen, die sich wiederholende oder aufeinanderfolgende Zahlen enthält, z.B. 1111 oder 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Zusätzliche Unterstützung für Android for Work-Geräte

- **Verwalten von Kennwort- und Arbeitsprofileinstellungen** <!-- 612808 -->

  Wir haben eine neue Einschränkungsrichtlinie für Android for Work-Geräte hinzugefügt, mit der Sie Kennwort- und Arbeitsprofileinstellungen auf von Ihnen verwalteten Android for Work-Geräten verwalten können.

- **Datenaustausch zwischen Arbeitsprofilen und persönlichen Profilen zulassen** <!-- 1045102 -->

  Wir haben die Einstellung **Datenaustausch zwischen Arbeitsprofilen und persönlichen Profilen zulassen** in einem Android for Work-Geräteeinschränkungsprofil mit neuen Optionen aktualisiert, damit Sie Daten zwischen Arbeitsprofilen und persönlichen Profilen freigeben können.

- **Beschränken von Kopieren und Einfügen zwischen Arbeitsprofilen und persönlichen Profilen** <!-- 1046094 -->

  Wenn Sie Android for Work-Geräte mit Intune verwalten, sind Aktionen zum Kopieren und Einfügen zwischen Arbeits- und persönliche Apps nicht zulässig. Wir haben nun ein benutzerdefiniertes Geräteprofil für Android for Work-Geräte hinzugefügt, mit dem Sie einschränken können, ob Kopieren und Einfügen zwischen Arbeits- und persönlichen Apps zulässig ist oder nicht.

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Zuweisen von branchenspezifischen Apps zu iOS- und Android-Geräten <!-- 1057568 -->

Sie können branchenspezifischen Apps für iOS (IPA-Dateien) und Android (APK-Dateien) Benutzern oder Geräten zuweisen.

###  <a name="new-policies-for-ios-devices----723774-723815-723826-723830-723832---"></a>Neue Richtlinien für iOS-Geräte <!-- 723774, 723815, 723826, 723830, 723832 -->

- **Apps auf dem Startbildschirm**: Sie können eine Geräterichtlinie verwenden, um zu steuern, welche Apps Benutzer auf dem Startbildschirm ihres iOS-Geräts sehen. Diese Richtlinie ändert das Layout des Startbildschirms, jedoch werden keine von Ihnen angegebenen Apps bereitgestellt, die nicht installiert sind.

- **Verbindungen zu AirPrint-Geräten**: Sie können eine Intune-Geräterichtlinie benutzen, um zu steuern, mit welchen AirPrint-Geräten (Netzwerkdrucker) sich ein Endbenutzer eines iOS-Geräts verbinden kann.

- **Verbindungen zu AirPlay-Geräten**: Sie können eine Intune-Geräterichtlinie benutzen, um zu steuern, mit welchen AirPlay-Geräten (wie Apple TV) sich ein Endbenutzer eines iOS-Geräts verbinden kann.

- **Benutzerdefinierte Sperrbildschirmnachricht**: Sie können eine benutzerdefinierte Nachricht konfigurieren, die Benutzern auf dem Sperrbildschirm ihres iOS-Geräts angezeigt wird und die die Standardnachricht des Sperrbildschirms ersetzt.

- **Webinhaltsfilter**: Sie können steuern, welche Websites Benutzer von iOS-Geräten mithilfe einer der folgenden zwei Methoden besuchen können:

  - Zulässige und blockierte URLs mit dem integrierten Webinhaltsfilter von Apple hinzufügen
  - Erlauben, dass nur auf bestimmte Websites vom Safari-Browser aus zugegriffen werden darf. Lesezeichen werden in Safari für jede Website erstellt, die Sie angeben.


### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Einschränken von Pushbenachrichtigungen für iOS-Apps <!-- 723767 -->

In einem Intune-Geräteeinschränkungsprofil können Sie die folgenden Benachrichtigungseinstellungen für iOS-Geräte konfigurieren:

- Aktivieren oder deaktivieren Sie die Benachrichtigungen für eine bestimmte App vollständig.
- Aktivieren oder deaktivieren Sie die Benachrichtigung für eine bestimmte App in der Mitteilungszentrale.
- Geben Sie den Warnungstyp an, entweder **Keinen**, **Banner** oder **modale Warnung**.
- Geben Sie an, ob die Badges für diese App zulässig sind.
- Geben Sie an, ob die Benachrichtigungssounds zulässig sind.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Konfigurieren von iOS-Apps, damit sie autonom im Einzelanwendungsmodus ausgeführt werden sollen <!-- 737837 -->

Sie können ein Intune-Geräteprofil verwenden, um zu konfigurieren, dass iOS-Geräte bestimmte Apps im autonomen Einzelanwendungsmodus ausführen sollen. Wenn dieser Modus konfiguriert ist und die App ausgeführt wird, wird das Gerät gesperrt, sodass es nur die App ausführen kann. Ein Beispiel hierfür ist, wenn Sie eine App konfigurieren, mit der Benutzer einen Test auf dem Gerät ausführen können. Wenn die Aktionen der App abgeschlossen sind oder Sie diese Richtlinie entfernen, kehrt das Gerät in seinen normalen Zustand zurück.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Konfigurieren von vertrauenswürdigen Domänen für das Durchsuchen von E-Mails und das Webbrowsen auf iOS-Geräten <!-- 723765 -->

Sie können in einem iOS-Geräteeinschränkungsprofil die folgenden Domäneneinstellungen konfigurieren:

- **Nicht gekennzeichnete E-Mail-Domänen**: Vom Benutzer gesendete oder empfangene E-Mails, die nicht den hier angegebenen Domänen entsprechen, werden als nicht vertrauenswürdig markiert.

- **Verwaltete Webdomänen**: Dokumente, die von den hier angegebenen URLs heruntergeladen werden, gelten als verwaltet (nur Safari).  

- **AutoAusfüllen-Domänen für Safari-Kennwörter**: Benutzer können Kennwörter in Safari nur aus URLs speichern, die mit den von Ihnen hier angegebenen Mustern übereinstimmen. Um diese Einstellung verwenden, muss sich das Gerät im überwachten Modus befinden und darf nicht für mehrere Benutzer konfiguriert sein. (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>Im iOS-Unternehmensportal verfügbare VPP-Apps als <!-- 748782 -->

Sie können per Volumenlizenz erworbene iOS-Apps (VPP-Apps) Endbenutzern als **Verfügbar**-Installationen zuweisen. Endbenutzer benötigen ein Apple Store-Konto, um die App zu installieren.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Synchronisieren von eBooks vom Apple-VPP-Store <!-- 800878 -->

Sie können Bücher, die Sie aus dem Apple-VPP-Store mit Intune gekauft haben, synchronisieren und Benutzern zuweisen.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Mehrbenutzerverwaltung für Samsung KNOW Standard-Geräte <!-- 971988 -->

Geräte, die unter Samsung KNOX Standard ausgeführt werden, werden nun von Intune für die Mehrbenutzerverwaltung unterstützt. Das bedeutet, dass sich Endbenutzer auf dem Gerät mit ihren Azure Active Directory-Anmeldeinformationen an- und wieder abmelden können, und dass das Gerät zentral verwaltet wird, egal ob es sich in Gebrauch befindet oder nicht.  Wenn sich Endbenutzer anmelden, verfügen Sie über Zugriff auf Apps und erhalten zusätzlich alle Richtlinien, die ihnen zugewiesen sind. Wenn sich Benutzer abmelden, werden alle App-Daten gelöscht.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Zusätzliche Einstellungen zur Einschränkung für Windows-Geräte <!-- 818566 -->

Wir haben Unterstützung für zusätzliche Einschränkungseinstellungen für Windows-Geräte hinzugefügt, z.B. zusätzliche Unterstützung für den Edge-Browser, Anpassung des Gerätesperrbildschirms, Anpassungen des Startmenüs, festgelegtes Hintergrundbild der Windows Spotlight-Suche und Proxyeinstellungen.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Unterstützung für Windows 10 Creators Update für mehrere Benutzer <!-- 822547 -->

Wir haben Unterstützung für die Mehrbenutzerverwaltung für Geräte hinzugefügt, die das Windows 10 Creators Update ausführen und in die Azure Active Directory-Domäne eingebunden sind. Das bedeutet Folgendes: Wenn sich unterschiedliche Standardbenutzer mit ihren Azure AD-Anmeldeinformationen auf dem Gerät anmelden, erhalten sie alle Apps und Richtlinien, die ihrem jeweiligen Benutzernamen zugewiesen sind. Benutzer können das Unternehmensportal derzeit nicht für Self-Service-Szenarien beispielsweise zum Installieren von Apps verwenden.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start für Windows 10-PCs <!-- 1004830 -->

In dieser Version haben wir eine neue Fresh Start-Geräteaktion für Windows 10 PCs hinzugefügt.  Wenn Sie diese Aktion ausführen, werden alle installierten Apps auf dem PC entfernt, und der PC wird automatisch auf die neueste Windows-Version aktualisiert. Damit können vorinstallierte OEM-Apps entfernt werden, die oft mit einem neuen PC geliefert werden. Sie können konfigurieren, ob Benutzerdaten beibehalten werden, wenn diese Geräteaktion ausgegeben wird.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Zusätzliche Windows 10-Upgradepfade <!-- 903672 -->

Sie können jetzt eine Richtlinie für die Editionsaktualisierung zum Aktualisieren von Geräten auf die folgenden zusätzlichen Windows 10-Editionen erstellen:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Massenregistrierung von Windows 10-Geräten <!-- 747607 -->

Sie können eine große Anzahl von Geräten, auf denen das Windows 10 Creators Update ausgeführt wird, mit Windows Configuration Designer (WCD) in Azure Active Directory und Intune einbinden. Um die automatische MDM-Registrierung für Ihren Azure AD-Mandanten zu aktivieren, erstellen Sie ein Bereitstellungspaket, das Geräte mithilfe von Windows Configuration Designer in Ihren Azure AD-Mandanten einbindet. Sie können das Paket auf alle unternehmenseigenen Geräte anwenden, die Sie per Massenvorgang registrieren und verwalten möchten. Nachdem das Paket auf Ihre Geräte angewendet wurde, werden die Geräte in Azure AD eingebunden und bei Intune registriert und sind dann bereit für die Anmeldung durch Ihre Azure AD-Benutzer.  Azure AD-Benutzer sind auf diesen Geräten Standardbenutzer und erhalten zugewiesene Richtlinien sowie erforderliche Apps. Die Verwendung von Self-Service-Funktionen und Unternehmensportalen wird derzeit nicht unterstützt.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----58112-736644---"></a>Neue MAM-Einstellungen für die PIN und verwaltete Speicherorte <!-- 58112, 736644 -->

Es sind zwei neue App-Einstellungen verfügbar, die Ihnen bei MAM-Szenarios (Mobile Application Management, Mobile Anwendungsverwaltung) helfen:

- **App-PIN deaktivieren, wenn die Geräte-PIN verwaltet wird**: Erkennt, ob eine Geräte-PIN auf dem registrierten Gerät vorhanden ist. Falls ja, wird die App-PIN umgangen, was durch die App-Schutzrichtlinien ausgelöst wird. Diese Einstellung ermöglicht eine Verminderung der Häufigkeit, wann immer Benutzern eine Aufforderung zur PIN-Eingabe angezeigt wird, wenn sie eine MAM-fähige Anwendung auf einem registrierten Gerät öffnen. Diese Funktion ist für Android und iOS verfügbar.

- **Wählen, welche Speicherdienste Unternehmensdaten speichern können**: Damit können Sie angeben, an welchen Speicherorten Unternehmensdaten gespeichert werden sollen. Benutzer können in ausgewählten Speicherortdiensten speichern, das heißt, dass alle anderen Speicherortdienste, die nicht aufgelistet sind, blockiert werden.

  Liste der unterstützten Speicherortdienste:

  - OneDrive
  - Business SharePoint Online
  - Lokaler Speicher


### <a name="see-also"></a>Weitere Informationen:
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new-in-microsoft-intune.md).

