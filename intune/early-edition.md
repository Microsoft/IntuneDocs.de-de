---
title: Early Edition
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d7c2ec47a163c16de91d3004a6204c1c00feb801
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2018
---
# <a name="the-early-edition-for-microsoft-intune---february-2018"></a>Die Early Edition für Microsoft Intune – Februar 2018

Die **Early Edition** enthält eine Liste der Funktionen, die in späteren Versionen von Microsoft Intune zur Verfügung stehen werden. Diese Informationen werden auf einer begrenzten Basis bereitgestellt, und Änderungen sind vorbehalten. Geben Sie diese Informationen nicht außerhalb Ihres Unternehmens weiter. Einige der hier aufgeführten Features werden möglicherweise bis zum Stichtag nicht fertig und werden erst in eine spätere Version aufgenommen. Andere Features werden in einer Pilotphase getestet (Test-Flighting), um sicherzustellen, dass sie für Kunden bereit sind. Wenden Sie sich mit Fragen oder Bedenken an den Ansprechpartner für Ihre Microsoft-Produktgruppe.

Diese Seite wird regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.

> [!Note]
>Die folgenden Änderungen sind in der Entwicklung für Intune. Weitere Informationen zu neuen Hybridfeatures finden Sie auf unserer [Seite mit neuen Hybridfeatures](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->

## <a name="intune-in-the-azure-portal"></a>Intune im Azure-Portal


<!-- 1802 start -->

### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Neues Diagramm zum Trend von fehlgeschlagenen Registrierungen und Tabelle mit Gründen für das Fehlschlagen <!-- 1471783 -->

Auf der Seite „Registrierungsübersicht“ können Sie den Trend von fehlgeschlagenen Registrierungen und die fünf häufigsten Gründe für das Fehlschlagen anzeigen lassen. Wenn Sie auf das Diagramm oder die Tabelle klicken, können Sie sich im Detail Informationen zu den Fehlern ansehen und erhalten Ratschläge zur Fehlerbehebung und zur Wiederherstellung.

### <a name="prevent-end-users-from-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Verhindern, dass Benutzer Konten im Arbeitsprofil hinzufügen oder daraus entfernen <!-- 1728700 -->    
Wenn Sie die Gmail-App in einem Android for Work-Profil bereitstellen, können Sie mit der Einstellung **Konten hinzufügen und entfernen** im Android for Work-Geräteeinschränkungenprofil verhindern, dass Benutzer Konten im Arbeitsprofil hinzufügen oder daraus entfernen.

### <a name="app-protection-policies-----679615---"></a>App-Schutzrichtlinien <!-- 679615 -->
Mit den Intune-App-Schutzrichtlinien können Sie globale Standardrichtlinien erstellen und damit den Schutz für alle Benutzer im gesamten Mandanten schnell aktivieren.

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune-Unterstützung für mehrere Apple DEP-/Apple School Manager-Konten <!-- 747685 -->

Intune unterstützt die Registrierung von Geräten mit bis zu 100 verschiedenen Apple DEP-Konten (Device Enrollment Program) oder Apple School Manager-Konten. Jedes Token kann separat für Registrierungsprofile und Geräte hochgeladen und verwaltet werden. Jedem hochgeladenen DEP-/School Manager-Token kann automatisch ein separates Registrierungsprofil zugewiesen werden. Wenn mehrere School Manager-Token hochgeladen werden, kann mit der Microsoft-Synchronisierung von Schul-/Unidaten jeweils nur ein Token freigegeben werden.

Nach der Migration funktionieren die Betaversionen der Graph-APIs und veröffentlichten Skripts zur Verwaltung von Apple DEP oder ASM über Graph nicht mehr. Neue Betaversionen der Graph-APIs sind in der Entwicklung und werden nach der Migration veröffentlicht.

### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Berichte zum Integritäts- und Bedrohungsstatus von Windows Defender <!--854704 -->

Ein grundlegendes Verständnis zur Integrität und zum Status von Windows Defender ist wichtig, damit Sie Windows-Computer verwalten können.  Intune fügt dem Status und der Integrität des Windows Defender-Agents neue Berichte und Aktionen hinzu. Wenn Sie einen Statusrollupbericht in der Gerätekonformitätsworkload verwenden, werden Ihnen Geräte angezeigt, für die einer der folgenden Vorgänge erforderlich ist:

- Signaturupdate
- Neustart
- Benutzereingriff
- vollständige Überprüfung
- andere Agent-Status, die einen Eingriff erfordern

Manchmal können Remotewiederherstellungsaktionen wie das Auslösen eines Signaturupdates durchgeführt werden.  In dem Bericht finden Sie außerdem die Anzahl von Computern, die als **Clean** (Bereinigt) eingestuft werden.

In einem Drillthroughbericht für sämtliche Statuskategorien werden sowohl die einzelnen Computer aufgeführt, die überprüft werden sollten, als auch die, die als **Clean** (Bereinigt) eingestuft werden.

### <a name="protocol-exceptions-for-applications---1035509-eeready--"></a>Protokollausnahmen für Anwendungen <!--1035509 eeready-->

Sie können Ausnahmen für die Richtlinie zur Datenübertragung über die Verwaltung mobiler Anwendungen (MAM) mit Intune erstellen, um bestimmte nicht verwaltete Anwendungen zu öffnen. Diese Anwendungen müssen von der IT-Abteilung als vertrauenswürdig eingestuft werden. Entgegen der von Ihnen erstellten Ausnahmen ist die Datenübertragung immer noch auf Anwendungen beschränkt, die von Intune verwaltet werden, wenn Ihre Richtlinie zur Datenübertragung immer noch auf **managed apps only** (nur verwaltete Apps) festgelegt ist. Sie können die Einschränkungen mithilfe von Protokollen (unter iOS) oder Paketen (unter Android) erstellen.

Sie können beispielsweise das Webex-Paket als Ausnahme für die Richtlinie zur MAM-Datenübertragung hinzufügen. Dann ist es erlaubt, Webex-Links in einer verwalteten Outlook-E-Mail direkt über die Webex-Anwendung zu öffnen. In anderen nicht verwalteten Anwendungen ist die Datenübertragung dann aber immer noch eingeschränkt.

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561-eeready--"></a>Anpassen des Unternehmsportaldesigns mit Hexadezimalcode <!--1049561 eeready-->

Sie können die Designfarben in den Unternehmensportal-Apps mithilfe von Hexadezimalcode anpassen. Wenn Sie Ihren Hexadezimalcode eingeben, legt Intune fest, welche Textfarbe [gemäß den WCAG 2.0-Standards](http://www.w3.org/TR/WCAG20) den stärksten Kontrast zur Hintergrundfarbe bildet. In einer Vorschau können Sie die Textfarbe und das Unternehmenslogo mit den Farben unter **Mobile Apps** > **Unternehmensportal** abgleichen. 

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>Neue Einstellungen für Windows Defender Credential Guard in den Endpoint Protection-Einstellungen <!--1102252 --> 

Unter **Gerätekonfiguration** > **Profile** > **Endpoint Protection** werden neue Einstellungen für [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard] hinzugefügt. Die folgenden Einstellungen werden hinzugefügt: 

- Plattformsicherheitsstufe: Legen Sie fest, welche Plattformsicherheitsstufe beim nächsten Neustart aktiviert wird. Für die virtualisierungsbasierte Sicherheit ist ein sicherer Start erforderlich. Falls gewünscht kann die virtualisierungsbasierte Sicherheit auch zusammen mit der Verwendung der Schutzfunktionen des direkten Remotezugriffs (Direct Memory Access, DMA) aktiviert werden. Für die DMA-Schutzfunktionen ist Hardwaresupport erforderlich. Außerdem werden sie nur auf richtig konfigurierten Geräten aktiviert.
- Virtualisierungsbasierte Sicherheit: Legen Sie fest, dass beim nächsten Neustart die virtualisierungsbasierte Sicherheit aktiviert wird. 
- Windows Defender Credential Guard: Aktivieren Sie Credential Guard gemeinsam mit der virtualisierungsbasierten Sicherheit, um beim nächsten Neustart die Anmeldeinformationen besser zu schützen, wenn die Plattformsicherheitsstufe sowohl mit dem sicheren Start als auch mit der virtualisierungsbasierten Sicherheit aktiviert ist. U.a. sind folgende Optionen verfügbar: **Disabled**, **Enabled with UEFI lock**, **Enabled without lock** und **Not configured** (Deaktiviert, Mit UEFI-Sperre aktiviert, Ohne Sperre aktiviert, Nicht konfiguriert). 
  - Über die Option „Deaktiviert“ wird Credential Guard per Remoteverbindung deaktiviert, wenn das Programm zuvor über die Aktion „Ohne Sperre aktiviert“ aktiviert wurde.

  - Über die Option „Mit UEFI-Sperre aktiviert“ wird gewährleistet, dass Credential Guard nicht mit einem Registrierungsschlüssel oder über eine Gruppenrichtlinie deaktiviert werden kann. Wenn Sie Credential Guard deaktivieren möchten, nachdem Sie diese Einstellung verwendet haben, müssen Sie die Gruppenrichtlinie auf „Deaktiviert“ festlegen und die Sicherheitsfunktion von jedem Computer mit einem anwesenden Benutzer entfernen, um die in der UEFI gespeicherte Konfiguration zu bereinigen. Solange die UEFI-Konfiguration bestehen bleibt, ist Credential Guard weiter aktiviert.

  - Über die Option „Ohne Sperre aktiviert“ kann Credential Guard über eine Remoteverbindung mithilfe einer Gruppenrichtlinie deaktiviert werden. Die Geräte, die diese Einstellung verwenden, müssen Windows 10 (Version 1511) oder höher ausführen.

  - Mit der Option „Nicht konfiguriert“ bleibt die Richtlinieneinstellung nicht definiert. Die Richtlinieneinstellung wird von der Gruppenrichtlinie nicht in die Registrierung geschrieben und hat so keinerlei Auswirkungen auf Computer oder Benutzer. Wenn es eine aktuellen Einstellung in der Registrierung gibt, wird diese nicht verändert.

### <a name="synchronize-and-deploy-sparsely-bundled-windows-store-for-business-apps---1222672---"></a>Synchronisieren und Bereitstellen von schlecht gebündelten Windows Store für Unternehmen-Apps <!--1222672 -->
Offline-Apps, die über den Windows Store für Unternehmen erworben werden, werden mit dem Intune-Portal synchronisiert. Sie können diese Apps dann für Geräte- oder Benutzergruppen bereitstellen. Offline-Apps werden durch Intune und nicht durch den Store installiert.

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Zurücksetzen von Kennwörtern für Android O-Geräte <!-- 1238299 -->
Sie können die Passwörter für registrierte Android O-Geräte zurücksetzen. Wenn Sie eine „Passwort zurücksetzen“-Anforderung an ein Android O-Gerät senden, legt dieses ein neues Passwort zum Entsperren des Geräts oder eine verwaltete Profilabfrage für den aktuellen Benutzer fest. Ein Passwort oder eine Abfrage wird dann gesendet, wenn das Gerät über einen Profilbesitzer oder einen Gerätebesitzer verfügt. Sie treten umgehend in Kraft.

### <a name="local-device-security-option-settings----1251887---"></a>Einstellungen der Sicherheitsoptionen für lokale Geräte <!-- 1251887 -->
Mithilfe der neuen Einstellungen der Sicherheitsoptionen für lokale Geräte können Sie Sicherheitseinstellungen auf Windows 10-Geräten aktivieren. Diese Einstellungen finden Sie in der Endpoint Protection-Kategorie, wenn Sie eine Gerätekonfigurationsrichtlinie für Windows 10 erstellen.

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Neue Druckereinstellungen für Education-Profile <!-- 1308900 -->

Für Education-Profile sind neue Einstellungen in der Kategorie **Drucker** unter **Drucker** > **Standarddrucker** > **Neue Drucker hinzufügen** verfügbar. 

### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Neue Datenschutzeinstellungen für Gerätebeschränkungen <!--1308926 -->

Es sind zwei neue Datenschutzeinstellungen für Geräte verfügbar:

- **Benutzeraktivitäten veröffentlichen:** Legen Sie diese Einstellung auf **Blockieren** fest, um geteilte Aktivitäten und die Ermittlungen von kürzlich verwendeten Ressourcen in der Programmumschaltung zu vermeiden.

- **Nur lokale Aktivitäten:** Legen Sie diese Einstellungen auf **Blockieren** fest, um geteilte Aktivitäten und Ermittlungen von kürzlich in der Programmumschaltung verwendeten Ressourcen anhand von ausschließlich lokalen Aktivitäten zu vermeiden.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Unterstützung von Registrierungen durch das macOS-Unternehmensportal über den Geräteregistrierungs-Manager <!-- 1352411 -->

Benutzer können den Geräteregistrierungs-Manager verwenden, wenn sie sich im macOS-Unternehmensportal registrieren.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Neue Einstellungen für den Browser Edge <!--1469166 -->

Für Geräte, auf denen Edge installiert ist, sind zwei neue Einstellungen verfügbar: **Path to favorites file** (Pfad zu häufig verwendeten Dateien) und **Changes to Favorites** (Änderungen an Favoriten). 

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Mit Windows Information Protection (WIP) verschlüsselte Daten in Windows-Suchergebnissen <!-- 1469193 -->

Mit einer neuen Einstellung in der WIP-Richtlinie (Windows Information Protection) können Sie steuern, ob mit WIP verschlüsselte Daten in den Windows-Suchergebnissen enthalten sind.

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Unterstützung von branchenspezifischen Apps für macOS <!-- 1473977 -->
Über Intune können Sie branchenspezifische macOS-Apps installieren. Bei branchenspezifischen Apps handelt es sich um Apps, für die Sie die Installationsdatei bereitstellen und Intune verwenden, um die App auf dem Gerät zu installieren. Als Bestandteil der Unterstützung von branchenspezifische macOS-Apps müssen Sie das Microsoft Intune App Wrapping Tool für macOS verwenden, um branchenspezifische macOS-Apps vorab zu verarbeiten.

### <a name="configure-resource-account-settings-for-surface-hubs----1475674---"></a>Konfigurieren von Einstellungen des Ressourcenkontos für Surface Hubs <!-- 1475674 -->

Sie können Einstellungen des Ressourcenkontos für Surface Hubs über eine Remoteverbindung konfigurieren.

Das Ressourcenkonto wird von einem Surface Hub für die Authentifizierung bei Skype bzw. Exchange verwendet, um dessen Teilnahme an einer Besprechung zu ermöglichen. Sie können ein eindeutiges Ressourcenkonto erstellen, damit der Surface Hub in der Besprechung als Konferenzraum angezeigt werden kann. Dieses Ressourcenkonto können Sie dann beispielsweise **Konferenzraum B41/6233** nennen.

> [!NOTE]
> - Wenn Sie Felder leer lassen, setzen Sie bereits auf dem Gerät konfigurierte Attribute außer Kraft.
>
> - Die Eigenschaften des Ressourcenkontos auf dem Surface Hub können sich dynamisch verändern. Dies passiert z.B., wenn die Kennwortrotation aktiviert ist. Das bedeutet, dass es einige Zeit dauert, bis die Werte in der Azure-Konsole die aktuellen Gegebenheiten auf dem Gerät widerspiegeln. 
>
>   Um ein grundlegendes Verständnis darüber zu erlangen, welche Optionen derzeit auf dem Surface Hub konfiguriert sind, können die Informationen zum Ressourcenkonto in der Hardwareinventur (die bereits alle sieben Tage durchgeführt wird) oder als schreibgeschützte Eigenschaften enthalten sein. Wenn Sie nach der Durchführung der Remoteaktion die Genauigkeit vergrößern möchten, können Sie den Status der Parameter unmittelbar nach der Ausführung dieser Aktion abrufen, um ein Update für das Konto bzw. die Parameter auf dem Surface Hub auszuführen.

### <a name="ios-app-provisioning-configuration----1581650---"></a>Bereitstellungskonfiguration für iOS-Apps <!-- 1581650 -->
Sie können Bereitstellungskonfigurationen für iOS-Apps zuweisen, um zu vermeiden, dass Ihre Apps ablaufen, indem Sie Sicherheitsgruppen ein- bzw. ausschließen.

### <a name="new-windows-defender-exploit-guard-settings----631893---"></a>Neue Einstellungen für Windows Defender Exploit Guard <!-- 631893 -->

Es sind sechs neue Einstellungen zur **Verringerung der Angriffsfläche** und erweiterte Funktionen von **Überwachter Ordnerzugriff: Ordnerschutz** verfügbar. Diese Einstellungen finden Sie unter: Gerätekonfiguration\Profiles\
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

|Name der Einstellung  |Einstellungsoptionen  |Beschreibung  |
|---------|---------|---------|
|Ordnerschutz (bereits implementiert)|Nicht konfiguriert, Aktivieren, Nur Überwachung (bereits implementiert)<br><br> **Neu**<br>Blockieren der Änderung des Datenträgers, Überwachung der Änderung des Datenträgers|
Hiermit schützen Sie Dateien und Ordner vor unbefugten Änderungen durch bösartige Apps.<br><br>**Aktivieren:** Vermeiden Sie, dass nicht vertrauenswürdige Apps Dateien in geschützten Ordnern verändern oder löschen und in Datenträgersektoren schreiben.<br><br>
**Nur die Änderung des Datenträgers blockieren**:<br>Blockiert, dass nicht vertrauenswürdige Apps in Datenträgersektoren schreiben. Nicht vertrauenswürdige Apps können weiterhin Dateien in geschützten Ordnern verändern oder löschen.

### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Neue Einstellungen für Windows Defender Application Guard <!-- 1631890 -->

- **Enable graphics acceleration** (Grafikbeschleunigung aktivieren)

Administratoren können einen virtuellen Grafikprozessor für Windows Defender Application Guard aktivieren. Über diese Einstellung kann die CPU Grafiken auslagern, die an die vGPU rendern. Dadurch kann die Leistung verbessert werden, wenn Sie mit grafikintensiven Websites arbeiten oder ein Video im Container ansehen.

- **SaveFilestoHost**

Administratoren können aktivieren, dass Dateien von Microsoft Edge, das im Container ausgeführt wird, an das Hostdateisystem übergeben werden. Wenn Sie diese Einstellung aktivieren, können Benutzer Dateien von Microsoft Edge in den Container auf dem Hostdateisystem herunterladen.

### <a name="see-enrollment-restrictions-per-user----1634444---"></a>Anzeigen von Registrierungseinschränkungen pro Benutzer <!-- 1634444 -->
Sie können unter „Problembehandlung“ die Registrierungseinschränkungen sehen, die für jeden Benutzer gelten.

### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Konfigurieren einer mobilen MSI-App, die sich selbst aktualisiert <!-- 1740840 -->
Sie können eine bekannte mobile MSI-App konfigurieren, die sich selbst aktualisiert, um den Prozess der Versionsüberprüfung zu ignorieren. Diese Einstellung ist nützlich, um Racebedingungen zu vermeiden. Dies kann z.B. passieren, wenn die App vom Entwickler automatisch aktualisiert wird, gleichzeitig aber auch von Intune ein Update ausgeführt wird. Beide könnten dann eine Version der App auf dem Windows-Client erzwingen, was einen Konflikt auslösen kann.

### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133---"></a>Ergänzungen zu den Konformitätsrichtlinien für die Systemsicherheitseinstellungen für Windows 10 und höher <!--1704133 -->

Es sind Ergänzungen zu den Konformitätsrichtlinien für Windows 10 verfügbar. Z.B. sind eine Firewall und Windows Defender Antivirus erforderlich.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Ein- und Ausschließen von App-Zuweisungen basierend auf Gruppen für Android Enterprise <!-- 1813081 -->
Android Enterprise (ehemals Android for Work) unterstützt bei der App-Zuweisung und nach dem Auswählen eines Zuweisungstyps die Exclude-Funktion.


### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Verwandte App-Lizenzen, die in Intune unterstützt werden <!-- 1864117 -->
Intune im App-Portal unterstützt verwandte App-Lizenzen als einzelne App-Elemente auf der Benutzeroberfläche. Außerdem werden alle offline lizenzierten Apps, die aus dem Microsoft Store für Unternehmen synchronisiert werden, in einem einzelnen App-Eintrag konsolidiert, und jegliche Bereitstellungsdetails aus den einzelnen Paketen werden in einen einzelnen Eintrag migriert. Wenn Sie verwandte App-Lizenzen im Azure-Portal abrufen möchten, klicken Sie im Azure-Portal auf der Seite **Mobile Apps** auf **App-Lizenzen**.

<!-- the following are present prior to 1802 -->

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>Neue Option zur Benutzerauthentifizierung für die Apple-Massenregistrierung<!-- 747625 -->
Mit Intune können Sie Geräte über folgende Registrierungsmethoden mit der Unternehmensportal-App authentifizieren:

- Apple-Programm zur Geräteregistrierung
- Apple School Manager
- Apple Configurator-Registrierung

Wenn Sie die Unternehmensportaloption verwenden, kann die mehrstufige Authentifizierung von Azure Active Directory erzwungen werden, ohne dass hierdurch diese Registrierungsmethoden blockiert werden.

Bei Verwendung der Unternehmensportaloption überspringt Intune die Benutzerauthentifizierung im iOS-Einrichtungsassistenten für die Registrierung mit der Benutzeraffinität. Das bedeutet, dass das Gerät zunächst als Gerät ohne Benutzer registriert wird und somit keine Konfigurationen oder Richtlinien von Benutzergruppen erhält. Es erhält nur Konfigurationen und Richtlinien für Gerätegruppen. Allerdings installiert Intune automatisch die Unternehmensportal-App auf dem Gerät. Der erste Benutzer, der die Unternehmensportal-App startet und sich bei dieser anmeldet, wird mit dem Gerät in Intune verbunden. An dieser Stelle erhält der Benutzer Konfigurationen und Richtlinien seiner Benutzergruppen. Die Benutzerzuordnung kann nur durch erneute Registrierung geändert werden.

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune-Unterstützung für mehrere Apple DEP-/Apple School Manager-Konten <!-- 747685 -->
Intune unterstützt die Registrierung von Geräten mit bis zu 100 verschiedenen Apple DEP-Konten (Device Enrollment Program) oder Apple School Manager-Konten. Jedes Token kann separat für Registrierungsprofile und Geräte hochgeladen und verwaltet werden. Jedem hochgeladenen DEP-/School Manager-Token kann automatisch ein separates Registrierungsprofil zugewiesen werden. Wenn mehrere School Manager-Token hochgeladen werden, kann mit der Microsoft-Synchronisierung von Schul-/Unidaten jeweils nur ein Token freigegeben werden.

Nach der Migration funktionieren die Betaversionen der Graph-APIs und veröffentlichten Skripts zur Verwaltung von Apple DEP oder ASM über Graph nicht mehr. Neue Betaversionen der Graph-APIs sind in der Entwicklung und werden nach der Migration veröffentlicht.

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Ausrichten von Konformitätsrichtlinien auf Geräte in Gerätegruppen <!--1307012 -->

Sie können Konformitätsrichtlinien gezielt auf Benutzer in Benutzergruppen ausrichten. Sie können Konformitätsrichtlinien gezielt auf Benutzer in Benutzergruppen ausrichten.

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Mit Windows Information Protection (WIP) verschlüsselte Daten in Windows-Suchergebnissen <!-- 1469193 -->

Mit einer neuen Einstellung in der WIP-Richtlinie (Windows Information Protection) können Sie steuern, ob mit WIP verschlüsselte Daten in den Windows-Suchergebnissen enthalten sind.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Remotedrucken über ein sicheres Netzwerk <!-- 1709994  -->
Mobile drahtlose PrinterOn-Drucklösungen ermöglichen es Benutzern, jederzeit von einem beliebigen Ort aus Druckvorgänge remote über ein sicheres Netzwerk durchzuführen. PrinterOn wird in das Intune APP SDK für iOS und Android integriert. Über das Intune-Blatt **App-Schutzrichtlinien** in der Administratorkonsole können Sie gezielt die App-Schutzrichtlinien für diese App steuern. Endbenutzer können die App „PrinterOn for Microsoft“ über den Play Store oder iTunes herunterladen, um sie innerhalb ihres Intune-Ökosystems zu nutzen.



### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>Microsoft Graph-API für Intune – Allgemeine Verfügbarkeit <!-- 1833289 -->
Intune-APIs in Microsoft Graph bieten programmgesteuerten Zugriff auf Daten und Methoden zur Automatisierung administrativer Aktionen für den Intune-Dienst.  Dank der **allgemeinen Verfügbarkeit** dieser APIs können Kunden, Partner und Entwickler die APIs nutzen, um sie in interne oder kommerzielle Lösungen zu integrieren, die die Unterstützung von Intune oder anderen über Microsoft Graph verfügbaren Microsoft-Diensten erfordern.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>App-Schutzrichtlinien <!-- 679615 -->
Mit den Intune-App-Schutzrichtlinien können Sie globale Standardrichtlinien erstellen und damit den Schutz für alle Benutzer im gesamten Mandanten schnell aktivieren.

### <a name="new-ios-device-action------1244701---"></a>Neue iOS-Geräteaktion <!-- 1244701 -->
Sie können überwachte iOS 10.3-Geräte herunterfahren. Diese Aktion fährt das Gerät sofort und ohne Warnung für den Endbenutzer herunter. Die Aktion **Herunterfahren (nur überwacht)** finden Sie in den Geräteeigenschaften bei der Auswahl eines Geräts in der Workload **Gerät**.

### <a name="intune-provides-the-account-move-operation-----1573558-1579830---"></a>Intune stellt den Vorgang zur Kontoverschiebung bereit <!-- 1573558, 1579830 -->
Bei der **Kontoverschiebung** wird ein Mandant von einer Azure-Skalierungseinheit (ASU) zu einer anderen migriert. Die **Kontoverschiebung** kann für vom Kunden eingeleitete Szenarien verwendet werden, wenn Sie sie vom Intune-Supportteam anfordern. Sie kann auch ein von Microsoft gesteuertes Szenario sein, wenn Microsoft Anpassungen am Dienst im Back-End vornehmen muss. Während der **Kontoverschiebung** wechselt der Mandant zum schreibgeschützten Modus (ROM). Dienstvorgänge wie die Registrierung, das Umbenennen von Geräten oder das Aktualisieren des Kompatibilitätsstatus sind während des ROM-Zeitraums nicht möglich.

Die Änderung wurde vorgenommen, um die Verwirrung anzugehen, die entsteht, wenn eine App mehreren Gruppen zugewiesen ist, die verschiedene App-Absichten haben.

Wenn Sie Ihre App vor dem Service Release im November im Informationsportal für Mitarbeiter und dem Unternehmensportal zur Verfügung stellen wollen, haben Sie zwei Möglichkeiten:

1. Entfernen Sie die Zuweisung **Nicht verfügbar** für Ihre Gruppe.
2. Erstellen Sie eine neue Gruppe, die keine Mitglieder enthält, denen die Absicht **Required and Available** zugewiesen wurde, und weisen Sie diese Gruppe als **Nicht verfügbar** zu.

Weitere Informationen finden Sie unter [Zuweisen von Apps zu Gruppen mit Microsoft Intune](apps-deploy.md).

> [!Note]
> Nach dem Release werden keine MDM-App-Zuweisungen mehr in der klassischen Intune-Konsole angezeigt, und Sie können sie nicht mehr bearbeiten. Allerdings können Sie die Azure-Konsole oder die Intune-Graph-API verwenden, um Ihre App-Zuweisungen festzulegen.

### <a name="configure-an-ios-app-pin----1586774---"></a>Konfigurieren einer PIN für eine iOS-App <!-- 1586774 -->
Bald erhalten Sie eine PIN für angesteuerte iOS-Apps. Sie können die Anforderungen für die PIN und das Ablaufdatum in Tagen im Azure-Portal konfigurieren. Falls erforderlich wird von dem Benutzer verlangt, eine neue PIN festzulegen und zu verwenden, bevor er Zugriff auf eine iOS-App erhält. Nur iOS-Apps, die einen App-Schutz mit dem Intune App SDK aktiviert haben, unterstützen diese Funktion.

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>Update der Benutzeroberfläche für die Unternehmensportal-App für iOS <!--1412866-->

Ein größeres Update der Benutzeroberfläche soll in der Unternehmensportal-App für iOS veröffentlicht werden. In dem Update soll das Design vollständig umgestaltet werden. Das bedeutet, die Ansicht soll modernisiert und die Benutzerfreundlichkeit und Barrierefreiheit verbessert werden. Alle aktuellen Funktionen des iOS-Unternehmensportals sollen erhalten bleiben.

Sie können über das Apple TestFlight-Programm der aktualisierten Unternehmensportal-App für iOS eine Vorschauversion verwenden und Feedback übermitteln. Registrieren Sie sich unter „https://aka.ms/intune_ios_cp_testflight“, um Zugriff auf TestFlight zu erhalten. 

![Erste Bilder zur neuen Unternehmensportal-App unter iOS](./media/ios-cp-app-redesign-1801-teaser.png)

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory-Websites können die App „Intune Managed Browser“ erfordern und unterstützen die einmalige Anmeldung für diese (öffentliche Vorschau) <!-- 710595 -->   
Mithilfe von Azure Active Directory (Azure AD) können Sie den Zugriff auf Websites durch mobile Geräte auf die App „Intune Managed Browser“ beschränken. Im verwalteten Browser bleiben die Websitedaten sicher und getrennt von den persönlichen Daten des Benutzers. Zusätzlich unterstützt der Managed Browser die Funktionen für einmaliges Anmelden für Websites, die von Azure AD geschützt werden. Das Anmelden beim Managed Browser oder das Verwenden desselben auf einem Gerät mit einer anderen App, die von Intune verwaltet wird, ermöglicht es dem Managed Browser, auf Unternehmenswebsites zuzugreifen, die von Azure AD geschützt werden, ohne dass der Benutzer seine Anmeldeinformationen eingeben muss. Diese Funktion gilt für Websites wie Outlook Web Access (OWA) und SharePoint Online sowie für andere Unternehmenswebsites wie Intranetressourcen, auf die über den Azure-App-Proxy zugegriffen wird.

<!-- the following are present prior to 1709 -->
### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune-App-Schutz und Citrix MDX-Entwicklungstools <!-- 709185 -->
Sie können Geräte und Apps mit einer Kombination aus Citrix XenMobile MDX und Microsoft Intune verwalten. Dadurch können Sie Apps mit der Intune-App-Schutzrichtlinie verwalten, während Sie die mVPN-Technologie von Citrix verwenden.

Sie können ein Coderepository suchen, das das App Wrapping Tool von Intune und des Intune App SDK für iOS und Android enthält, das von der Citrix MDX mVPN-Technologie integriert wird.

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-the-new-company-portal-app---1380728--"></a>Umleiten von macOS-Benutzern zur neuen Unternehmensportal-App <!--1380728-->   
Wenn ein Benutzer sich bei der Website des Unternehmensportals anmeldet, um sein macOS-Gerät zu registrieren, wird dieser zum Download der neuen Unternehmensportal-App für macOS umgeleitet, um den Vorgang abzuschließen. Dies tritt bei macOS-Geräten auf, die OS X El Capitan 10.11 oder höher verwenden. 

<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Unterstützung für Intune Managed Browser von iOS und Android <!-- 1374196 -->
Ab Oktober 2017 unterstützt die Intune Managed Browser-App für Android nur noch Geräte mit Android 4.4 oder höher. Die Intune Managed Browser-App unter iOS unterstützt nur noch Geräte mit iOS 9.0 oder höher. Frühere Versionen von Android und iOS können Managed Browser weiterhin verwenden, allerdings können keine neuen Versionen der App installiert werden, und einige App-Funktionen sind möglicherweise nicht verfügbar. Es wird empfohlen, dass Sie diese Geräte auf eine unterstützte Betriebssystemversion aktualisieren.

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Verbesserte Fehlermeldungen für den Fall, wenn ein Benutzer die Höchstzahl von zur Registrierung erlaubten Geräten erreicht <!-- 1270370 -->
Statt einer generischen Fehlermeldung sehen Benutzer mit Android-Geräten eine an Benutzer gerichtete, handlungsrelevante Fehlermeldung: „You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin.“ (Sie haben die maximale Anzahl an Geräten registriert, die von Ihrem IT-Administrator erlaubt wurden. Bitte entfernen Sie ein registriertes Gerät, oder wenden Sie sich an Ihren IT-Administrator.“)



## <a name="notices"></a>Benachrichtigungen

Derzeit gibt es keine aktiven Benachrichtigungen.



### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).


