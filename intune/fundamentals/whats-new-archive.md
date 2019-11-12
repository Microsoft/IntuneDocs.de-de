---
title: Neuerungen in den vorherigen Monaten in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Überprüfen Sie ältere Ankündigungen auf der Intune-Seite mit den Neuerungen
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/5/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6a6b5585501851bb52db70ca222f8cfff7ad0597
ms.sourcegitcommit: 2c8a41ee95a3fde150667a377770e51b621ead65
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73635463"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Neuerungen in Microsoft Intune (vorherige Monate)

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

<!-- ########################## -->
## <a name="april-2019"></a>April 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung
#### <a name="user-experience-update-for-the-company-portal-app-for-ios---2536024---"></a>Update für die Benutzeroberfläche für die Unternehmensportal-App für iOS<!-- 2536024 -->
Die Startseite der Unternehmensportal-App für iOS-Geräte wurde neu gestaltet. Sie entspricht nun mehr dem Muster der iOS-Benutzeroberfläche, und zudem können Apps und E-Books besser gefunden werden.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users--3448635---"></a>Änderungen der Unternehmensportal-Registrierung für Benutzer von iOS 12-Geräten<!--3448635 -->
Die Anzeigen und Schritte bei der Registrierung im Unternehmensportal für iOS wurden aktualisiert und entsprechen nun den Änderungen der MDM-Registrierung, die mit Apple iOS 12.2 veröffentlicht wurden. Der aktualisierte Workflow fordert Benutzer zu Folgendem auf:  

* Zulassen, dass Safari die Unternehmensportal-Website öffnet, das Verwaltungsprofil herunterlädt und dann zur Unternehmensportal-App zurückkehrt.  
* Öffnen der App „Settings“ (Einstellungen), um das Verwaltungsprofil auf dem Gerät zu installieren.
* Rückkehr zur Unternehmensportal-App, um die Registrierung abzuschließen.  

Die aktualisierten Registrierungsschritte und -anzeigen finden Sie unter [Enroll iOS device in Intune (Registrieren eines iOS-Geräts in Intune)](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).

#### <a name="openssl-encryption-for-android-app-protection-policies---3747362---"></a>OpenSSL-Verschlüsselung für Android-App-Schutzrichtlinien<!-- 3747362 -->
Intune-App-Schutzrichtlinien für Android-Geräte nutzen nun eine OpenSSL-Verschlüsselungsbibliothek, die FIPS 140-2-konform ist. Weitere Informationen finden Sie im Abschnitt [Verschlüsselung](../apps/app-protection-policy-settings-android.md#encryption) unter [Einstellungen für App-Schutzrichtlinien in Microsoft Intune](../apps/app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies---2617348----"></a>Aktivieren von Win32-App-Abhängigkeiten<!-- 2617348  -->
Als Administrator können Sie voraussetzen, dass Apps als Abhängigkeiten installiert werden, bevor Ihre Win32-App installiert wird. Das heißt, das Gerät muss die abhängige(n) App(s) installieren, bevor die Win32-App installiert wird. Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**, um das Blatt **App hinzufügen** anzuzeigen. Wählen Sie **Windows-App (Win32)** als **App-Typ** aus. Nachdem Sie die App hinzugefügt haben, können Sie auf **Abhängigkeiten** klicken, um die abhängigen Apps hinzuzufügen, die installiert werden müssen, bevor die Win32-App installiert werden kann. Weitere Informationen finden Sie unter [Eigenständiges Intune – Win32-App-Verwaltung](./../apps/app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps---3537391-----"></a>Installationsinformationen zur App-Version für Apps im Microsoft Store für Unternehmen<!-- 3537391   -->
Berichte zur App-Installation enthalten Informationen zur App-Version für Apps im Microsoft Store für Unternehmen. Klicken Sie in Intune auf **Client-Apps** > **Apps**. Wählen Sie eine **App im Microsoft Store für Unternehmen** aus, und klicken Sie dann im Abschnitt **Überwachen** auf **Geräteinstallationsstatus**.

#### <a name="additions-to-win32-apps-requirement-rules---3676883-----"></a>Ergänzungen zu Anforderungsregeln für Win32-Apps<!-- 3676883   -->
Sie können Anforderungsregeln mithilfe von PowerShell-Skripts, Registrierungswerten und Dateisysteminformationen erstellen. Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie dann **Windows-App (Win32)** als **App-Typ** auf dem Blatt **App hinzufügen** aus.  Klicken Sie auf **Anforderungen** > **Hinzufügen**, um zusätzliche Anforderungsregeln zu konfigurieren. Wählen Sie dann entweder **Dateityp**, **Registrierung** oder **Skript** als **Anforderungstyp** aus. Weitere Informationen finden Sie unter [Eigenständiges Intune – Win32-App-Verwaltung](./../apps/app-management.md).

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices---3695227----"></a>Konfigurieren von Win32-Apps für die Installation auf in Intune registrierten, in Azure AD eingebundenen Geräten<!-- 3695227  -->
Sie können Ihre Win32-Apps für die Installation auf in Intune registrierten, in Azure AD eingebundenen Geräten zuweisen. Weitere Informationen zu Win32-Apps in Intune finden Sie unter [Eigenständiges Intune – Win32-App-Verwaltung](./../apps/app-management.md).

#### <a name="device-overview-shows-primary-user--3794259----"></a>Primärer Benutzer in der Geräteübersicht<!--3794259  -->
Die Seite „Geräteübersicht“ zeigt den primären Benutzer (Affinität zwischen Benutzer und Gerät) an. Klicken Sie auf **Intune** > **Geräte** > **Alle Geräte**, und wählen Sie dann ein Gerät aus, um den primären Benutzer eines Geräts anzuzeigen. Der primäre Benutzer wird außerdem oben auf der Seite **Übersicht** angezeigt.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices---4105925----"></a>Zusätzliche Berichterstellung für verwaltete Google Play-Apps für Android Enterprise-Arbeitsprofilgeräte<!-- 4105925  -->
Sie können die Versionsnummer von auf Android Enterprise-Arbeitsprofilgeräten bereitgestellten, verwalteten Google Play-Apps anzeigen. Dies gilt nur für erforderliche Apps.  

#### <a name="ios-third-party-keyboards---4111843-----"></a>Tastaturen von Drittanbietern für iOS<!-- 4111843   -->
Die Intune APP-Unterstützung (App Protection Policy, App-Schutzrichtlinie) für die Einstellung **Tastaturen von Drittanbietern** für iOS wird aufgrund einer Änderung an der iOS-Plattform beendet. Sie können diese Einstellung in der Intune-Verwaltungskonsole nicht mehr konfigurieren, und sie wird auf dem Client im Intune App SDK nicht mehr erzwungen.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="updated-certificate-connectors---icm-113304612---"></a>Update für Zertifikatconnectors<!-- ICM 113304612 -->
Wir haben Updates für den [Intune-Zertifikatconnector und den PFX-Zertifikatconnector für Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) veröffentlicht. Mit diesen neuen Releases wurden einige bekannte Probleme behoben.

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices---1210083----"></a>Festlegen der Anmeldeeinstellungen und Steuern der Neustartoptionen für macOS-Geräte<!-- 1210083  -->
Sie können auf macOS-Geräten ein Gerätekonfigurationsprofil erstellen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > Plattform **macOS** auswählen > **Gerätefunktionen**). Dieses Update umfasst neue Einstellungen im Fenster „Anmelden“, z. B. die Anzeige eines benutzerdefinierten Banners, die Auswahl der Anmeldemethode für Benutzer, das Anzeigen oder Ausblenden von Energieeinstellungen und mehr.

Informationen zu diesen Einstellungen finden Sie unter [macOS device feature settings in Intune (Einstellungen von macOS-Gerätefeatures)](../configuration/macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode--3041940----"></a>Konfigurieren von WLAN auf dedizierten Geräten im Multi-App-Kioskmodus für Android Enterprise-Gerätebesitzer<!--3041940  -->
Sie können die Einstellungen für Android Enterprise-Gerätebesitzer aktivieren, wenn das Gerät als dediziertes Gerät im Multi-App-Kioskmodus ausgeführt wird. Mit diesem Update können Sie Benutzern ermöglichen, WLAN-Netzwerke zu konfigurieren und Verbindungen mit diesen herzustellen (**Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform) > **Nur Gerätebesitzer > Geräteeinschränkungen** (Profiltyp) > **Dedizierte Geräte** > **Kioskmodus**: **Multi-App** > **WLAN-Konfiguration**).

Eine Liste aller konfigurierbaren Einstellungen finden Sie unter [Android Enterprise device settings to allow or restrict features (Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features)](../configuration/device-restrictions-android-for-work.md).

Gilt für: Dedizierte Android Enterprise-Geräte im Multi-App-Kioskmodus

#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041941----"></a>Konfigurieren von Bluetooth und Kopplung auf dedizierten Geräten im Multi-App-Kioskmodus für Android Enterprise-Gerätebesitzer<!-- 3041941  -->
Sie können die Einstellungen für Android Enterprise-Gerätebesitzer aktivieren, wenn das Gerät als dediziertes Gerät im Multi-App-Kioskmodus ausgeführt wird. Mit diesem Update können Sie Benutzern ermöglichen, Bluetooth zu aktivieren und Geräte per Bluetooth zu koppeln (**Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform) > **Nur Gerätebesitzer > Geräteeinschränkungen** (Profiltyp) > **Dedizierte Geräte** > **Kioskmodus**: **Multi-App** > **Bluetooth-Konfiguration**).

Eine Liste aller konfigurierbaren Einstellungen finden Sie unter [Android Enterprise device settings to allow or restrict features (Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features)](../configuration/device-restrictions-android-for-work.md).

Gilt für: Dedizierte Android Enterprise-Geräte im Multi-App-Kioskmodus

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune---3305883----"></a>Erstellen und Verwenden von OEMConfig-Gerätekonfigurationsprofilen in Intune<!-- 3305883  -->
Mit diesem Update unterstützt Intune die Konfiguration von Android Enterprise-Geräten mit OEMConfig. Das heißt, Sie können ein Gerätekonfigurationsprofil erstellen und Einstellungen auf Android Enterprise-Geräte mit OEMConfig anwenden (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform)).

Die Unterstützung wird derzeit auf einer pro-OEM-Basis bereitgestellt. Wenden Sie sich an `IntuneOEMConfig@microsoft.com`, wenn eine OEMConfig-App, die Sie benötigen, nicht in der Liste von OEMConfig-Apps verfügbar ist.

Weitere Informationen zu diesem Feature finden Sie unter [Use and manage Android Enterprise devices with OEMConfig in Microsoft Intune (Verwenden und Verwalten von Android Enterprise-Geräten mit OEMConfig in Microsoft Intune)](../configuration/android-oem-configuration-overview.md).

Gilt für: Android Enterprise

#### <a name="windows-update-notifications---3316758-3316782----"></a>Windows Update-Benachrichtigungen<!-- 3316758, 3316782  -->
Wir haben den Windows Update-Ringkonfigurationen zwei *Einstellungen für die Benutzeroberfläche* hinzugefügt, die Sie über die Intune-Konsole verwalten können. Sie können nun:
- Benutzern erlauben oder verweigern, [nach Windows-Updates zu suchen](../protect/windows-update-settings.md).
- die [Windows Update-Benachrichtigungsebene](../protect/windows-update-settings.md) verwalten, die Benutzern angezeigt wird.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner---3574254----"></a>Neue Einstellungen zur Geräteeinschränkung für Android Enterprise-Gerätebesitzer<!-- 3574254  -->
Sie können ein Geräteeinschränkungsprofil auf Android Enterprise-Geräten erstellen, um Features zuzulassen oder einzuschränken, Kennwortregeln festzulegen und mehr (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform) > **Nur Gerätebesitzer > Geräteeinschränkungen** (Profiltyp)). 

Dieses Update umfasst neue Kennworteinstellungen, ermöglicht Vollzugriff auf Apps im Google Play Store für vollständig verwaltete Geräte und mehr. Die aktuelle Liste der Einstellungen finden Sie unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features](../configuration/device-restrictions-android-for-work.md). 

Gilt für: Vollständig verwaltete Android Enterprise-Geräte

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---"></a>Prüfen nach einem TPM-Chipsatz in einer Windows 10-Gerätekonformitätsrichtlinie<!-- 3617671 -->

Die Bereitstellung dieses Features verzögert sich und ist in einem zukünftigen Release geplant.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices---3775833-----"></a>Änderungen der Benutzeroberfläche für den Microsoft Edge-Browser auf Geräten mit Windows 10 und höher<!-- 3775833   -->
Wenn Sie ein Gerätekonfigurationsprofil erstellen, können Sie Microsoft Edge-Features auf Geräten mit Windows 10 und höher zulassen oder einschränken (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **Microsoft Edge-Browser**). Die Microsoft Edge-Einstellungen werden in diesem Update besser beschrieben und sind einfacher zu verstehen.

Diese Features finden Sie unter [Einstellungen für Geräteeinschränkungen in Microsoft Edge](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser).

Gilt für: Windows 10 und höher

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-----3903241-3903244-3903246-----"></a>Erweiterte Unterstützung für vollständig verwaltete Android Enterprise-Geräte (Preview)<!--   3903241, 3903244, 3903246   -->
Die sich noch in der Public Preview befindende Unterstützung vollständig verwalteter Android Enterprise-Geräte (erstmals im Januar 2019 angekündigt) wurde wie folgt erweitert:

- Auf vollständig verwalteten und dedizierten Geräten können Sie [Konformitätsrichtlinien](../protect/compliance-policy-create-android-for-work.md) erstellen, die Kennwortregeln und Betriebssystemanforderungen enthalten (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Android Enterprise** (Plattform) > **Gerätebesitzer** (Profiltyp)).

  Auf dedizierten Geräten wird das Gerät möglicherweise als **nicht konform** angezeigt. Der bedingte Zugriff ist auf dedizierten Geräten nicht verfügbar. Stellen Sie sicher, dass Sie alle Aufgaben und Aktionen fertig stellen, damit dedizierte Geräte Ihre zugewiesenen Richtlinien einhalten.

- [Bedingter Zugriff](../protect/conditional-access.md): Richtlinien für den bedingten Zugriff, die für Android gelten, gelten auch für vollständig verwaltete Android Enterprise-Geräte. Benutzer können ihre vollständig verwalteten Geräte nun mithilfe der **Microsoft Intune-App** in Azure Active Directory registrieren. Anschließend können sie Kompatibilitätsprobleme anzeigen und beheben, um auf Unternehmensressourcen zuzugreifen.

- Neue Endbenutzer-App (Microsoft Intune-App): Für vollständig verwaltete Android-Geräte gibt es die neue Endbenutzer-App **Microsoft Intune**. Diese neue App ist besonders schlank und modern. Sie bietet ähnliche Funktionen wie die Unternehmensportal-App, aber für vollständig verwaltete Geräte. Weitere Informationen finden Sie unter der [Microsoft Intune-App auf Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

Um vollständig verwaltete Android-Geräte einzurichten, wechseln Sie zu **Geräteregistrierung** > **Android-Registrierung** > **Unternehmenseigene, vollständig verwaltete Geräte**. Die Unterstützung für vollständig verwaltete Android-Geräte befindet sich weiterhin in der Vorschau, und einige Intune-Features sind möglicherweise noch nicht voll funktionsfähig.  

Weitere Informationen zu dieser Public Preview finden Sie im Blog unter [Microsoft Intune – Preview 2 for Android Enterprise Fully Managed devices (Microsoft Intune: Preview 2 für vollständig verwaltete Android Enterprise-Geräte)](https://aka.ms/preview2_AE_fullymanaged).

#### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Verwenden des Compliance-Managers zum Erstellen von Bewertungen für Microsoft Intune<!-- 4404750 -->

Der [Compliance-Manager](https://servicetrust.microsoft.com/ComplianceManager) (Link öffnet eine andere Microsoft-Website) ist ein Workflow-basiertes Tool für die Risikobewertung in Microsoft Service Trust Portal. Mit dem Tool können Sie die Aktivitäten zur Einhaltung behördlicher Bestimmung Ihres Unternehmens im Bezug auf Microsoft-Diensten überwachen, zuweisen und überprüfen. Sie können Ihre eigene Bewertung der Konformität mit Office 365, Azure, Dynamics, Professional Services und Intune erstellen. Zwei Bewertungen sind in Intune verfügbar: FFIEC und DSGVO.

Der Compliance-Manager unterstützt Sie beim Aufteilen der Kontrollen: Kontrollen, die von Microsoft verwaltet werden und Kontrollen, die von Ihrer Organisation verwaltet werden. Sie können die Bewertungen abschließen und anschließend extrahieren und drucken.

Die Konformität mit [FFIEC (Federal Financial Institutions Examination Council)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (Link öffnet eine andere Microsoft-Website) umfasst mehrere Standards für Onlinebanking, die vom FFIEC erlassen wurden. Diese Bewertung ist die am häufigsten angeforderte Bewertung von Finanzinstituten, die Intune verwenden. Sie interpretiert, wie Intune die Konformität mit Cybersicherheitsrichtlinien des FFIEC für öffentliche Cloud-Workloads unterstützt. Die FFIEC-Bewertung von Intune ist die zweite FFIEC-Bewertung im Compliance-Manager.

Im folgenden Beispiel werden die FFIEC-Kontrollen aufgeschlüsselt. 64 Kontrollen werden von Microsoft verwaltet. Ihre Organisation ist für die restlichen 12 Kontrollen zuständig.

![Beispielbewertung für die FFIEC-Bewertung in Intune, einschließlich Kundenaktionen und Microsoft-Aktionen](./media/whats-new/intune-ffiec-assessment-status.png)

Die [DSGVO (Datenschutz-Grundverordnung)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (Link öffnet eine andere Microsoft-Website) ist ein Gesetz der Europäischen Union (EU), das die Rechte von Personen und ihren Daten schützt. Die DSGVO-Bewertung ist die am häufigsten angeforderte Bewertung zur Unterstützung der Konformität mit Datenschutzbestimmungen. 

Im folgenden Beispiel werden die DSGVO-Kontrollen aufgeschlüsselt. 49 Kontrollen werden von Microsoft verwaltet. Ihre Organisation ist für die restlichen 66 Kontrollen zuständig.

![Beispielbewertung für die DSGVO-Bewertung in Intune, einschließlich Kundenaktionen und Microsoft-Aktionen](./media/whats-new/intune-assessment-status.png)


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant---2276470----"></a>Konfigurieren des Profils zum Überspringen einiger Bildschirme während des Setup-Assistenten<!-- 2276470  -->
Wenn Sie ein macOS-Registrierungsprofil erstellen, können Sie dieses konfigurieren, um die folgenden Anzeigen zu überspringen, wenn ein Benutzer den Setup-Assistenten durchläuft:
- Darstellung
- Anzeigefarbton
- iCloudStorage: Wenn Sie ein neues Profil erstellen oder ein Profil bearbeiten, müssen die ausgewählten zu überspringenden Bildschirme mit dem Apple MDM-Server synchronisiert werden.  Benutzer können eine manuelle Synchronisierung der Geräte durchführen, sodass es keine Verzögerung bei der Auswahl der Profiländerungen gibt.
Weitere Informationen finden Sie unter [Automatisches Registrieren von macOS-Geräten mit dem Programm zur Geräteregistrierung oder Apple School Manager](../enrollment/device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Massengerätebenennung beim Registrieren unternehmenseigener iOS-Geräte<!--3566569  -->
Wenn Sie eine der Unternehmensbereitstellungsmethoden (DEP/ABM/ASM) von Apple verwenden, können Sie ein Format für Gerätenamen festlegen, um eingehende iOS-Geräte automatisch zu benennen. Sie können ein Format festlegen, das den Gerätetyp und die Seriennummer in der Vorlage enthält. Klicken Sie hierzu auf **Intune** > **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** > **Token auswählen** >**Profil erstellen** > **Device naming format** (Format für die Gerätebenennung). Sie können vorhandene Profile bearbeiten, der Name wird jedoch nur auf neu synchronisierte Geräte angewendet.

#### <a name="updated-default-timeout-message-on-enrollment-status-page---3959331---"></a>Update der Standardtimeoutnachricht für die Registrierungsstatusseite<!-- 3959331 -->
Die Standardtimeoutnachricht, die Benutzern angezeigt wird, wenn der im Profil für die Registrierungsstatusseite festgelegte Timeoutwert überschritten wird, wurde aktualisiert. Die neue Standardnachricht soll Benutzern dabei helfen, die nächsten Schritte für die Bereitstellung der Registrierungsstatusseite zu verstehen.  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Geräteverwaltung

#### <a name="retire-noncompliant-devices---1827291-----"></a>Ausmustern nicht konformer Geräte<!-- 1827291   -->
Die Bereitstellung dieses Features verzögert sich und ist in einem zukünftigen Release geplant.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta---4403765---"></a>Übernahme der Änderungen an Intune Data Warehouse V1.0 in die Betaversion<!-- 4403765 -->
Als V1.0 in Version 1808 erstmals eingeführt wurde, gab es wichtige Unterschiede zur Beta-API. Diese Änderungen werden mit Version 1903 in der Betaversion der API berücksichtigt. Wenn Sie über wichtige Berichte verfügen, die die Betaversion der API nutzen, wird dringend empfohlen, dass Sie diese Berichte in V1.0 konvertieren, um Breaking Changes zu vermeiden. Weitere Informationen finden Sie im [Änderungsprotokoll für die Intune Data Warehouse-API](../developer/reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Überwachen des Status der Sicherheitsbaseline (Public Preview) <!-- 3082047 --> 
Der Überwachung von Sicherheitsbaselines wurde eine [Ansicht für einzelne Kategorien](../protect/security-baselines-monitor.md#per-category-view) hinzugefügt. (Sicherheitsbaselines befinden sich weiterhin in Preview). Die Ansicht für einzelne Kategorien zeigt jede Kategorie der Baseline mit dem Prozentsatz der Geräte an, die in jede Statusgruppe dieser Kategorie fallen. Sie können nun anzeigen, wie viele Geräte nicht mit den individuellen Kategorien übereinstimmen und falsch konfiguriert oder nicht anwendbar sind.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="scope-tags-for-apple-vpp-tokens--2371886----"></a>Bereichsmarkierungen für Apple-VPP-Token<!--2371886  -->
Sie können nun Bereichsmarkierungen zu Apple-VPP-Token hinzufügen. Nur Benutzer, denen die gleiche Bereichsmarkierung zugewiesen ist, können auf das Apple-VPP-Token mit dieser Markierung zugreifen. VPP-Apps und E-Books, die mit diesem Token erworben werden, erben seine Bereichsmarkierungen. Weitere Informationen zu Bereichsmarkierungen finden Sie unter [Use RBAC and scope tags (Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen)](scope-tags.md).

<!-- ########################## -->
## <a name="march-2019"></a>März 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung
#### <a name="deploy-microsoft-visio-and-microsoft-project---3725386----"></a>Bereitstellen von Microsoft Visio und Microsoft Project<!-- 3725386  -->
Sie können nun Microsoft Visio Pro für Office 365 und den Microsoft Project Online-Desktopclient mithilfe von Microsoft Intune als unabhängige Apps auf Windows 10-Geräten bereitstellen, wenn Sie die Lizenzen für diese Apps besitzen. Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**, um das Blatt **App hinzufügen** anzuzeigen. Wählen Sie auf dem Blatt **App hinzufügen** den **App-Typ** **Windows 10** aus. Klicken Sie dann auf **App-Suite konfigurieren**, um zu installierende Apps auszuwählen. Weitere Informationen über Office 365-Apps für Windows 10-Geräte finden Sie unter [Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune](../apps/apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change---3593653----"></a>Änderung des Produktnamens von Microsoft Visio Pro für Office 365<!-- 3593653  -->
**Microsoft Visio Pro für Office 365** heißt jetzt **Microsoft Visio Online Plan 2**.  Weitere Informationen zu Microsoft Visio finden Sie unter [Visio Online Plan 2](https://products.office.com/visio/visio-online-plan-2). Weitere Informationen über Office 365-Apps für Windows 10-Geräte finden Sie unter [Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune](../apps/apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting---3291302----"></a>Einstellung für die Zeichenbeschränkung für Intune-App-Schutzrichtlinien<!-- 3291302  -->
Intune-Administratoren können eine Ausnahme für die Intune-App-Richtlinieneinstellung zum **Einschränken des Ausschneidens, Kopierens und Einfügens bei anderen Apps** festlegen.  Als Administrator können Sie die Anzahl von Zeichen festlegen, die aus einer verwalteten App ausgeschnitten oder kopiert werden können. Mit dieser Einstellungen kann die festgelegte Zeichenanzahl, unabhängig von der Einstellung für das Einschränken von Ausschneiden, Kopieren und Einfügen bei anderen Apps, mit einer beliebigen App geteilt werden. Beachten Sie, dass die Version der Intune-Unternehmensportal-App für Android Version 5.0.4364.0 oder höher erfordert. Weitere Informationen finden Sie unter [iOS-Datenschutz](../apps/app-protection-policy-settings-ios.md#data-protection), [Android-Datenschutz](../apps/app-protection-policy-settings-android.md#data-protection) und [Überprüfen der Schutzprotokolle für Client-Apps](../apps/app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment---3192477-----"></a>Office-Bereitstellungstool-XML für die Bereitstellung von Office ProPlus<!-- 3192477   -->
Sie können das Office-Bereitstellungstool-XML bereitstellen, wenn Sie eine Instanz von Office ProPlus in der Intune-Verwaltungskonsole erstellen. Dadurch wird die Anpassbarkeit erweitert, wenn die vorhandenen Benutzeroberflächenoptionen von Intune nicht Ihre Anforderungen erfüllen. Weitere Informationen finden Sie unter [Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune](../apps/apps-add-office365.md) und [Konfigurationsoptionen für das Office-Bereitstellungstool](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background---1429026----"></a>App-Symbole werden nun mit einem automatisch generierten Hintergrund angezeigt<!-- 1429026  -->
App-Symbole werden nun in der Windows-Unternehmensportal-App mit einem automatisch generierten Hintergrund basierend auf der dominanten Farbe des Symbols angezeigt (sofern diese ermittelt werden kann). Wenn möglich, ersetzt dieser Hintergrund den grauen Rahmen, der zuvor auf App-Kacheln sichtbar war. Diese Änderung wird ab Version 10.3.3451.0 des Unternehmensportals angezeigt.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment---2751523-----"></a>Installieren verfügbarer Apps mithilfe der Unternehmensportal-App nach der Windows-Massenregistrierung<!-- 2751523   -->
Windows-Geräte, die mit der [Windows-Massenregistrierung](../enrollment/windows-bulk-enroll.md) (Bereitstellungspakete) in Intune registriert wurden, können die Unternehmensportal-App nutzen, um verfügbare Apps zu installieren. Weitere Informationen über die Unternehmensportal-App finden Sie unter [Manuelles Hinzufügen der Windows 10-Unternehmensportal-App mithilfe von Microsoft Intune](../apps/store-apps-company-portal-app.md) und [Konfigurieren der Microsoft Intune-Unternehmensportal-App](../apps/company-portal-app.md).

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite---3828932----"></a>Die Microsoft Teams-App kann als Teil der Office-App-Suite ausgewählt werden<!-- 3828932  -->
Die Microsoft Teams-App kann als Teil der Office ProPlus-App-Suite enthalten oder ausgeschlossen werden. Dieses Feature funktioniert ab Buildnummer 16.0.11328.20116 von Office ProPlus. Der Benutzer muss sich vom Gerät abmelden und neu anmelden, damit die Installation abgeschlossen werden kann. Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie einen **Office 365 Suite**-App-Typ aus, und klicken Sie dann auf **App-Suite konfigurieren**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices---2351390---"></a>Automatisches Starten einer App, wenn mehrere Apps auf Geräten mit Windows 10 oder höher im Kioskmodus ausgeführt werden<!-- 2351390 -->

Auf Geräten mit Windows 10 und höher können Sie viele Apps im Kioskmodus ausführen. Dieses Update umfasst eine **AutoLaunch**-Einstellung (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** (Plattform) > **Kiosk** (Profiltyp) > **Multi-App-Kiosk**). Verwenden Sie diese Einstellung, um eine App automatisch zu starten, wenn der Benutzer sich auf dem Gerät anmeldet.

Eine Liste und Beschreibungen aller Kioskeinstellungen finden Sie unter [Windows 10 and later device settings to run as a kiosk in Intune (Geräteeinstellungen unter Windows 10 und höher für die Ausführung als Kiosk in Intune)](../configuration/kiosk-settings-windows.md).

Gilt für: Windows 10 und höher

#### <a name="operational-logs-also-show-details-on-non-compliant-devices---4063755----"></a>Betriebsprotokolle enthalten Details zu nicht konformen Geräten<!-- 4063755  -->
Beim Weiterleiten von Intune-Protokollen an Azure-Überwachungsfeatures können Sie auch Betriebsprotokolle weiterleiten. In diesem Update stellen Betriebsprotokolle auch Informationen zu nicht konformen Geräten bereit.

Weitere Informationen zu diesem Feature finden Sie unter [Senden von Daten an den Speicher, an Event Hubs oder Log Analytics in Intune](../review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads---3804627---"></a>Weiterleiten von Protokollen an Azure Monitor in mehreren Intune-Workloads<!-- 3804627 -->
In Intune können Sie Überwachungs- und Betriebsprotokolle an Event Hubs, Speicher und Log Analytics in Azure Monitor weiterleiten (**Intune** > **Überwachung** > **Diagnoseeinstellungen**). In diesem Update können Sie diese Protokolle in mehreren Intune-Workloads weiterleiten, einschließlich Konformität, Konfigurationen, Client-Apps und mehr.

Weitere Informationen zum Weiterleiten von Protokollen an Azure Monitor finden Sie unter [Senden von Daten an den Speicher, an Event Hubs oder Log Analytics in Intune](../review-logs-using-azure-monitor.md).

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune---3305880-----"></a>Erstellen und Verwenden von Mobility Extensions für Android Zebra-Geräte in Intune<!-- 3305880   -->
Mit diesem Update unterstützt Intune die Konfiguration von Android Zebra-Geräten. Das heißt, Sie können ein Gerätekonfigurationsprofil erstellen und Einstellungen mithilfe von mit StageNow generierten MX-Profilen (Mobility Extensions) auf Android Zebra-Geräte anwenden (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android** (Plattform) > **MX-Profil (nur Zebra)** (Profiltyp)).

Weitere Informationen zu diesem Feature finden Sie unter [Use and manage Zebra devices with mobility extensions in Intune (Verwenden und Verwalten von Zebra-Geräten mit Mobility Extensions in Intune)](../configuration/android-zebra-mx-overview.md).

Gilt für: Android

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Geräteverwaltung
#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Verschlüsselungsbericht für Windows 10-Geräte (Public Preview)<!-- 2351538 -->
Verwenden Sie den neuen [Verschlüsselungsbericht (Vorschau)](../protect/encryption-monitor.md), um Details zum Verschlüsselungsstatus Ihrer Windows 10-Geräte anzuzeigen. Die verfügbaren Details umfassen die TPM-Version des Geräts, die Verschlüsselungsbereitschaft und den -status, die Fehlerberichterstattung und mehr.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview---2351547-----"></a>Zugriff auf BitLocker-Wiederherstellungsschlüssel über das Intune-Portal (Public Preview)<!-- 2351547   -->
Sie können nun Intune zum [Anzeigen von Details](../protect/encryption-monitor.md) zur BitLocker-Schlüssel-ID und den BitLocker-Wiederherstellungsschlüsseln in Azure Active Directory verwenden.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices---3411007---"></a>Microsoft Edge-Unterstützung für Intune-Szenarios auf iOS- und Android-Geräten<!-- 3411007 -->
Microsoft Edge unterstützt alle Verwaltungsszenarios, die Intune Managed Browser unterstützt, und enthält Verbesserungen für die Benutzerfreundlichkeit. Zu den von Intune-Richtlinien aktivierten Microsoft Edge-Unternehmensfeatures gehören doppelte Identitäten, die Integration von App-Schutzrichtlinien, die Integration von Azure-Anwendungsproxys sowie verwaltete Favoriten und Verknüpfungen auf der Startseite. Weitere Informationen finden Sie unter [Microsoft Edge support (Microsoft Edge-Unterstützung)](../apps/app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices--3105122----"></a>Exchange Online/Intune-Connector unterstützen Geräte mit nur Exchange Active Sync nicht mehr<!--3105122  -->
Die Intune-Konsole unterstützt das Anzeigen und Verwalten von Geräten mit nur EAS, die über den Intune-Connector mit Exchange Online verbunden sind, nicht mehr. Stattdessen stehen Ihnen folgende Optionen zur Verfügung:
- Registrieren von Geräten in der mobilen Geräteverwaltung (Mobile Device Management, MDM)
- Verwenden von App-Schutzrichtlinien zum Verwalten Ihrer Geräte
- Verwenden von Exchange-Steuerelementen gemäß den Anweisungen unter [Clients and mobile in Exchange Online (Clients und Mobilgeräte in Exchange Online)](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)

#### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name--4254930---"></a>Suchen eines bestimmten Geräts auf der Seite „Alle Geräte“ mithilfe von [Name]<!--4254930 -->
Sie können nun nach exakten Gerätenamen suchen. Wechseln Sie zu **Intune** > **Geräte** > **Alle Geräte**, und umschließen Sie den gesuchten Gerätenamen im Suchfeld mit {}, um nach einer genauen Übereinstimmung zu suchen. Zum Beispiel: **{Gerät12345}**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="support-for-additional-connectors-on-the-tenant-status-page---3617202----"></a>Unterstützung für zusätzliche Connectors auf der Seite „Mandantenstatus“<!-- 3617202  -->
Auf der [Mandantenstatusseite](../tenant-status.md) werden nun Statusinformationen zu zusätzlichen Connectors, einschließlich *Windows Defender Advanced Threat Protection* (ATP) und anderen Mobile Threat Defense-Connectors, angezeigt.

#### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune---4260871---"></a>Unterstützung der Power BI-Compliance-App über das Data Warehouse-Blatt in Microsoft Intune<!-- 4260871 -->
Zuvor wurde mit dem Link **Power BI-Datei herunterladen** auf dem Blatt **Intune Data Warehouse** ein Intune Data Warehouse-Bericht heruntergeladen (PBIX-Datei). Dieser Bericht wurde nun durch die Power BI-Compliance-App ersetzt. Die Power BI-Compliance-App erfordert kein gesondertes Laden oder Setup. Sie wird direkt im Power BI-Onlineportal geöffnet und zeigt Daten spezifisch für Ihren Intune-Mandanten basierend auf Ihren Anmeldeinformationen an. Klicken Sie in Intune auf der rechten Seite des Intune-Blatts auf den Link **Intune Data Warehouse einrichten**. Klicken Sie dann auf **Power BI-App abrufen**. Weitere Informationen finden Sie unter [Connect to the Data Warehouse with Power BI (Verbinden von Data Warehouse mit Power BI)](../developer/reports-proc-get-a-link-powerbi.md).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles---3637917----"></a>Gewähren des schreibgeschützten Zugriffs auf Intune für einige Azure Active Directory-Rollen<!-- 3637917  -->
Den folgenden Azure AD-Rollen wurde schreibgeschützter Zugriff auf Intune gewährt. Berechtigungen, die mit Azure AD-Rollen gewährt werden, haben Vorrang vor der rollenbasierten Zugriffssteuerung von Intune.

Schreibgeschützter Zugriff auf Intune-Überwachungsdaten:

- Complianceadministrator
- Administrator für Konformitätsdaten

Schreibgeschützter Zugriff auf alle Intune-Daten:

- Sicherheitsadministrator
- Sicherheitsoperator
- Sicherheitsleseberechtigter

Weitere Informationen finden Sie unter [Rollenbasierte Zugriffssteuerung mit Microsoft Intune](role-based-access-control.md).

#### <a name="scope-tags-for-ios-app-provisioning-profiles--2934430-----"></a>Bereichsmarkierungen für iOS-App-Bereitstellungsprofile<!--2934430   -->
Sie können einem iOS-App-Bereitstellungsprofil eine Bereichsmarkierung hinzufügen, sodass nur Benutzer mit der gleichen Bereichsmarkierung wie das iOS-App-Bereitstellungsprofil auf diese zugreifen können. Weitere Informationen finden Sie unter [Use RBAC and scope tags (Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen)](scope-tags.md).

#### <a name="scope-tags-for-app-configuration-policies--2371891-----"></a>Bereichsmarkierungen für App-Konfigurationsrichtlinien<!--2371891   -->
Sie können einer App-Konfigurationsrichtlinie eine Bereichsmarkierung hinzufügen, sodass nur Benutzer mit der gleichen Bereichsmarkierung wie die App-Konfigurationsrichtlinie auf diese zugreifen können. Die App-Konfigurationsrichtlinie kann nur den Apps zugeordnet werden, denen dieselben Bereichsmarkierungen zugewiesen sind. Weitere Informationen finden Sie unter [Use RBAC and scope tags (Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen)](scope-tags.md).

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices---3411007---"></a>Microsoft Edge-Unterstützung für Intune-Szenarios auf iOS- und Android-Geräten<!-- 3411007 -->
Microsoft Edge unterstützt alle Verwaltungsszenarios, die Intune Managed Browser unterstützt, und enthält Verbesserungen für die Benutzerfreundlichkeit. Zu den von Intune-Richtlinien aktivierten Microsoft Edge-Unternehmensfeatures gehören doppelte Identitäten, die Integration von App-Schutzrichtlinien, die Integration von Azure-Anwendungsproxys sowie verwaltete Favoriten und Verknüpfungen auf der Startseite. Weitere Informationen finden Sie unter [Microsoft Edge support (Microsoft Edge-Unterstützung)](../apps/app-configuration-managed-browser.md#microsoft-edge-support).




<!-- ########################## -->
## <a name="february-2019"></a>Februar 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung
#### <a name="intune-macos-company-portal-dark-mode---3300524----"></a>Dunkler Modus für Intune-Unternehmensportal für macOS<!-- 3300524  -->
Das Intune macOS-Unternehmensportal unterstützt ab sofort den dunklen Modus für macOS. Wenn Sie den dunklen Modus auf einem Gerät mit macOS 10.14 und höher aktivieren, wird das Unternehmensportal an die Farben dieses Modus angepasst.

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices---2577355-----"></a>Verwendung von Google Play Protect-APIs für Android-Geräte in Intune<!-- 2577355   -->
Manche IT-Administratoren arbeiten in einer Bring Your Own Device-Umgebung (BYOD), in der manche Endbenutzer ihre Mobiltelefone möglicherweise rooten oder jailbreaken. Die meisten Benutzer handeln zwar nicht in schlechter Absicht, dennoch kann dieses Verhalten dazu führen, dass viele Intune-Richtlinien umgangen werden, die zum Schutz der Organisationsdaten auf den Endbenutzergeräten eingerichtet wurden. Deshalb enthält Intune eine Erkennung von Rooting und Jailbreaks für registrierte und nicht registrierte Geräte. Ab diesem Release verwendet Intune die Google Play Protect-APIs, um die bisherigen Überprüfungen auf Rooting für nicht registrierte Geräte zu ergänzen. Google stellt zwar nicht alle Überprüfungsmechanismen für Rooting zur Verfügung, aber diese APIs sollten dennoch Benutzer ermitteln können, die Ihre Geräte abweichend von der Gerätekonfiguration gerootet haben, um neuere Betriebssystemupdates für ältere Geräte zu erhalten. Diesen Benutzern kann der Zugriff auf Unternehmensdaten verwehrt werden, oder ihre Unternehmenskonten können aus den Apps entfernt werden, für die Richtlinien aktiviert sind. Es wurden zudem einige Updates für die Berichterstellung auf dem Blatt „Intune-App-Schutz“ vorgenommen, um IT-Administratoren die Arbeit zu erleichtern: Der Bericht „Gekennzeichnete Benutzer“ enthält die Benutzer, die durch eine Überprüfung mit der SafetyNet-API von Google Play Protect ermittelt wurden, und der Bericht „Potentially Harmful Apps“ (Potenziell schädliche Apps) enthält die Apps, die durch eine Überprüfung mit der Verify Apps-API von Google ermittelt wurden. Dieses Feature ist unter Android verfügbar.

#### <a name="win32-app-information-available-in-troubleshooting-blade---2617342-----"></a>Informationen zu Win32-Apps auf dem Blatt „Problembehandlung“<!-- 2617342   -->
Sie können nun Protokolldateien zu Fehlern bei der Installation von Win32-Apps über das Blatt **Problembehandlung** der Intune-App abrufen. Weitere Informationen zur Behandlung von Problemen mit der App-Installation finden Sie unter [Troubleshoot app installation issues (Problembehandlung bei der App-Installation)](./../apps/troubleshoot-app-install.md) und [Behandeln von Win32-App-Problemen](./../apps/troubleshoot-app-install.md#win32-app-installation-troubleshooting).

#### <a name="app-status-details-for-ios-apps---3761235-----"></a>Details zum Status von iOS-Apps<!-- 3761235   -->
Es wurden neue Fehlermeldungen eingeführt, die bei folgenden Problemen bei der Installation von Apps ausgelöst werden:
- Fehler beim Installieren von VPP-Apps auf gemeinsam genutzten iPads
- Fehler bei deaktiviertem App Store
- Fehler beim Suchen von VPP-Lizenzen für Apps
- Fehler beim Installieren von System-Apps mit MDM-Anbietern
- Fehler beim Installieren von Apps, wenn das Gerät sich im Kioskmodus oder im Modus für verlorene Geräte befindet
- Fehler beim Installieren von Apps wenn der Benutzer nicht im App Store angemeldet ist

Navigieren Sie in Intune zu **Client-Apps** > **Apps** > Name der App > **Geräteinstallationsstatus**. Die neuen Fehlermeldungen werden in der Spalte **Statusdetails** angezeigt.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Neue Anzeige „App-Kategorien“ in der Unternehmensportal-App für Windows 10<!-- 3834780  -->
Eine neue Anzeige namens **App-Kategorien** wurde hinzugefügt, um das Durchsuchen und Auswählen von Apps im Unternehmensportal für Windows 10 zu verbessern. Für Benutzer werden Apps nun sortiert nach Kategorien wie **Empfohlen**, **Bildung** und **Produktivität** angezeigt. Diese Änderung ist im Unternehmensportal ab Version 10.3.3451.0 vorhanden. Informationen zu dieser neuen Anzeige finden Sie unter [Updates der Benutzeroberfläche für Endbenutzer-Apps in Intune](whats-new-app-ui.md). Weitere Informationen zu den Apps im Unternehmensportal finden Sie unter [Install and share apps on your device (Installieren und Freigeben von Apps auf Ihrem Gerät)](https://docs.microsoft.com/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app---1455231-doc-work-item---"></a>Power BI-Compliance-App<!-- 1455231 doc-work-item -->
Sie können über die App [Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) in Power BI auf Ihre Intune Data Warehouse-Instanz zugreifen. Mit dieser Power BI-App können Sie nun auf vorab erstellte Berichte zugreifen und diese freigeben, ohne dafür ein Setup durchzuführen und ohne Ihren Webbrowser zu verlassen. Weitere Informationen finden Sie im [Änderungsprotokoll für die Intune Data Warehouse-API](../developer/reports-changelog.md#power-bi-compliance-app).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices---1862675-----"></a>Ausführung von PowerShell-Skripts auf einem 64-Bit-Host auf 64-Bit-Geräten<!-- 1862675   -->
Wenn Sie ein PowerShell-Skript zu einem Gerätekonfigurationsprofil hinzufügen, wird das Skript immer im 32-Bit-Modus ausgeführt, auch auf einem 64-Bit-Betriebssystem. Seit diesem Update kann ein Administrator das Skript auf einem 64-Bit-Gerät auf einem 64-Bit-Host von PowerShell ausführen (**Gerätekonfiguration** > **PowerShell-Skripts** > **Hinzufügen** > **Konfigurieren** > **Skript in 64-Bit-PowerShell-Host ausführen**).

Weitere Informationen zur Verwendung von PowerShell finden Sie unter [Verwalten von PowerShell-Skripts in Intune für Windows 10-Geräte](../apps/intune-management-extension.md).

Gilt für: Windows 10 und höher

#### <a name="macos-users-are-prompted-to-update-their-password---1873216---"></a>macOS-Benutzer werden aufgefordert, ihr Kennwort zu aktualisieren<!-- 1873216 -->
Intune erzwingt die Einstellung **ChangeAtNextAuth** für macOS-Geräte. Diese Einstellung wirkt sich auf Benutzer und Geräte aus, die über Konformitätskennwortrichtlinien oder Geräteeinschränkungsprofile für Kennwörter verfügen. Benutzer werden einmal aufgefordert, ihr Kennwort zu aktualisieren. Diese Aufforderung wird angezeigt, wenn ein Benutzer zum ersten Mal eine Aufgabe ausführt, für die Authentifizierung erforderlich ist, z. B. die Anmeldung auf dem Gerät. Benutzer können ebenfalls dazu aufgefordert werden, ihre Kennwörter zu aktualisieren, wenn sie etwas tun, für das Administratorberechtigungen erforderlich sind, z. B. das Anfordern des Keychain-Zugriffs.

Auch bei Änderungen an neuen oder vorhandenen Kennwortrichtlinien durch den Administrator werden Benutzer dazu aufgefordert, ihre Kennwörter zu aktualisieren.

Gilt für:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device---2340521------"></a>Zuweisen von SCEP-Zertifikaten zu einem macOS-Gerät ohne Benutzer<!-- 2340521    -->
Sie können SCEP-Zertifikate (Simple Certificate Enrollment-Protokoll) mit Geräteattributen zu macOS-Geräten hinzufügen (dies gilt auch für Geräte ohne Benutzeraffinität) und die Zertifikatprofile zu WLAN- oder VPN-Profilen zuordnen. Dadurch wird die bereits vorhandene Unterstützung erweitert, sodass [SCEP-Zertifikate zu Geräten mit und ohne Benutzeraffinität zugewiesen werden können](../protect/certificates-profile-scep.md), auf denen Windows, iOS oder Android ausgeführt wird.  Mit diesem Update wurde die Option hinzugefügt, den Zertifikattyp *Gerät* beim Konfigurieren eines SCEP-Zertifikatprofils für macOS auszuwählen.

Gilt für:
- macOS

#### <a name="intune-conditional-access-ui-update---2432313-----"></a>Update der Intune-Benutzeroberfläche für den bedingten Zugriff<!-- 2432313   -->
Wir haben die Benutzeroberfläche für den bedingten Zugriff in der Intune-Konsole verbessert. Dazu gehören:
- Das Intune-Blatt *Bedingter Zugriff* wurde durch das entsprechende Blatt aus Azure Active Directory ersetzt. Dadurch wird sichergestellt, dass Sie alle Einstellungen und Konfigurationen für den [bedingten Zugriff](../protect/conditional-access.md) (eine Technologie von Azure AD) innerhalb der Intune-Konsole nutzen können. 
- Das Blatt *Lokaler Zugriff* wurde in *Exchange-Zugriff* umbenannt, und das Setup für den *Exchange-Dienstconnector* wurde auf dieses Blatt verschoben.  Dadurch ändert sich der Ort, an dem Sie [Details zu Exchange (online und lokal) konfigurieren und überwachen](../protect/exchange-connector-install.md).  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode---2935135-----"></a>Ausführung von Kioskbrowsern und Microsoft Edge-Browser-Apps auf Windows 10-Geräten im Kioskmodus<!-- 2935135   -->
Sie können Windows 10-Geräte im Kioskmodus verwenden, um eine oder mehrere Apps auszuführen. Durch dieses Update wurden unter anderem folgende Änderungen an der Verwendung von Browser-Apps im Kioskmodus vorgenommen:

- Der Microsoft Edge-Browser und der Kioskbrowser können nun als ausführbare Apps zu Kioskgeräten hinzugefügt werden (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **Windows 10 und höher** (Plattform) bzw. **Kiosk** (Profiltyp)).
- Es stehen neue Features und Einstellungen zum Zulassen oder Gewähren zur Verfügung (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **Windows 10 und höher** (Plattform) > **Geräteeinschränkungen** (Profiltyp)), einschließlich:

- Microsoft Edge-Browser:
  - Verwenden des Microsoft Edge-Kioskmodus
  - Aktualisieren des Browsers nach einer Leerlaufzeit

- Favoriten und Suche:
  - Zulassen von Änderungen an der Suchmaschine

Eine Liste dieser Einstellungen finden Sie unter:

- [Geräteeinstellungen bei Windows 10 (und höher) zur Ausführung als Kiosk in Intune](../configuration/kiosk-settings-windows.md)
- [Microsoft Edge-Browser](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)
- [Einstellungen für Windows 10-Geräte (und höher) zum Zulassen oder Einschränken von Features mit Intune](../configuration/device-restrictions-windows-10.md##favorites-and-search)

Gilt für: Windows 10 und höher

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices---3448774-----"></a>Neue Einstellungen für Einschränkungen für iOS- und macOS-Geräte<!-- 3448774   -->
Sie können einige Einstellungen und Features auf iOS- und macOS-Geräten einschränken (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **iOS** bzw. **macOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp)). Mit diesem Update werden weitere Features und Einstellungen hinzugefügt, die Sie steuern können. Sie können auf iOS-Geräten beispielsweise die Bildschirmzeit festlegen, eSIM-Einstellungen und Mobilfunktarife ändern und mehr. Außerdem können Sie Softwareupdates später für Benutzer bereitstellen oder das Content Caching auf macOS-Geräten blockieren.

Weitere Informationen zu den einschränkbaren Features und Einstellungen finden Sie unter:

- [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](../configuration/device-restrictions-ios.md)
- [Einstellungen für Geräteeinschränkungen für macOS-Geräte in Microsoft Intune](../configuration/device-restrictions-macos.md)

Gilt für:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices---3598402-----"></a>„Kioskgeräte“ heißen bei Android Enterprise-Geräten jetzt „Dedizierte Geräte“<!-- 3598402   -->
Zur Anpassung an die Android-Terminologie wurde **Kiosk** für Android Enterprise-Geräte in **dedizierte Geräte** umbenannt (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform) > **Nur Gerätebesitzer** > **Geräteeinschränkungen** > **Dedizierte Geräte**).

Eine Liste der verfügbaren Einstellungen finden Sie unter [Device settings to allow or restrict features (Geräteeinstellungen zum Zulassen oder Einschränken von Features)](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

Gilt für:  
Android Enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui---3640850-3803313-----"></a>Verschiebung der iOS-Einstellungen von Safari und zum Verzögern der Sichtbarkeit von Updates für Benutzer auf der Benutzeroberfläche von Intune<!-- 3640850, 3803313   -->
Für iOS-Geräte können Sie Safari-Einstellungen festlegen und Softwareupdates konfigurieren. Mit diesem Update werden diese Einstellungen auf der Intune-Benutzeroberfläche verschoben:

- Die Safari-Einstellungen wurden von **Safari** (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp)) zu **[Integrierte Apps](../configuration/device-restrictions-ios.md#built-in-apps)** verschoben.
- Die Einstellung **Delaying user software update visibility for supervised iOS devices** (Sichtbarkeit von Updates für Benutzer von überwachten iOS-Geräten verzögern) (**Softwareupdates** > **Richtlinien für iOS aktualisieren**) wurde zu **Geräteeinschränkungen** > **[Allgemein](../configuration/device-restrictions-ios.md#general)** verschoben.  Weitere Informationen zu den Auswirkungen auf vorhandene Richtlinien finden Sie unter [Konfigurieren von iOS-Updaterichtlinien in Intune](../protect/software-updates-ios.md#configure-the-policy).

Eine Liste der Einstellungen finden Sie unter:

- [iOS-Geräteeinschränkungen](../configuration/device-restrictions-ios.md) 
- [iOS-Softwareupdates](../protect/software-updates-ios.md)

Diese Funktion gilt für:

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices---3699164-----"></a>Umbenennung von „Aktivieren von Einschränkungen in den Geräteeinstellungen (nur überwacht)“ auf iOS-Geräten in „Bildschirmzeit“<!-- 3699164   -->
Sie können die Einstellung **Aktivieren von Einschränkungen in den Geräteeinstellungen (nur überwacht)** für überwachte iOS-Geräte (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **Allgemein**) konfigurieren. Mit diesem Update wurde die Einstellung in **Bildschirmzeit (nur überwacht)** umbenannt.

Das Verhalten ändert sich nicht. Genauer gesagt:

- iOS 11.4.1 und früher: **Blockieren** verhindert, dass Endbenutzer die für sie geltenden Einschränkungen der Geräteeinstellungen bearbeiten. 
- iOS 12.0 und höher: Durch die Option **Blockieren** kann verhindert werden, dass Endbenutzer die für sie geltende **Bildschirmzeit** (einschließlich Einschränkungen von Inhalt und Datenschutz) in den Geräteeinstellungen bearbeiten. Auf Geräten, auf denen mindestens iOS 12.0 ausgeführt wird, wird die Registerkarte „Einschränkungen“ in den Geräteeinstellungen nicht mehr angezeigt. Diese Einstellungen befinden sich unter **Bildschirmzeit**. 

Eine Liste der Einstellungen finden Sie in den [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](../configuration/device-restrictions-ios.md#general).

Gilt für:
- iOS


#### <a name="intune-powershell-module---951068----"></a>Intune PowerShell-Modul<!-- 951068  -->
Das Intune PowerShell-Modul, das Unterstützung für die Intune-API über Microsoft Graph bereitstellt, ist jetzt im [PowerShell-Katalog](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10) verfügbar.

- [Informationen zur Verwendung dieses Moduls](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Beispielszenarios für die Verwendung dieses Moduls](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization--3183757----"></a>Verbesserte Unterstützung für die Übermittlungsoptimierung<!--3183757  -->
Die Unterstützung für die Konfiguration der Übermittlungsoptimierung in Intune wurde erweitert. Sie können nun eine erweiterte Liste von [Einstellungen für die Übermittlungsoptimierung](../configuration/delivery-optimization-settings.md) konfigurieren und direkt über die Intune-Konsole auf Ihre Geräte abstimmen.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Geräteverwaltung

#### <a name="rename-an-enrolled-windows-device---1911112----"></a>Umbenennen eines registrierten Windows-Geräts<!-- 1911112  -->
Sie können registrierte Windows 10-Geräte (RS4 oder höher) jetzt umbenennen. Navigieren Sie hierfür zu **Intune** > **Geräte** > **Alle Geräte**, wählen Sie ein Gerät aus, und klicken Sie auf **Gerät umbenennen**. Dieses Feature unterstützt derzeit nicht das Umbenennen von Windows-Geräten mit Azure AD Hybrid.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope---3173823----"></a>Automatische Zuweisung von Bereichsmarkierungen zu Ressourcen, die von einem Administrator für diesen Bereich erstellt wurden<!-- 3173823  -->
Wenn ein Administrator eine Ressource erstellt, werden alle Bereichstags, die dem Administrator zugewiesen sind, automatisch auch den neuen Ressourcen zugewiesen.

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade---3560202----"></a>Bericht für fehlgeschlagene Registrierungen wurde auf das Blatt „Geräteregistrierung“ verschoben<!-- 3560202  -->
Der Bericht zu **fehlgeschlagenen Registrierungen** wurde in den Abschnitt **Überwachen** des Blatts **Geräteregistrierung** verschoben. Zwei neue Spalten („Registrierungsmethode“ und „Betriebssystemversion“) wurden hinzugefügt.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments--3815076-eemiss---"></a>Umbenennung des Berichts „Unternehmensportalabbruch“ in „Unvollständige Benutzerregistrierungen“<!--3815076 eemiss -->
Der Bericht **Unternehmensportalabbruch** wurde in **Unvollständige Benutzerregistrierungen** umbenannt.






<!-- ########################## -->
## <a name="january-2019"></a>Januar 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung

#### <a name="intune-app-pin---2298397---"></a>Intune-App-PIN<!-- 2298397 -->
Als IT-Administrator können Sie die Anzahl der Tage konfigurieren, die ein Endbenutzer warten kann, bis seine Intune-App-PIN geändert werden muss. Die neue Einstellung *Anzahl von Tagen für PIN-Zurücksetzung* steht im Azure-Portal unter **Intune** > **Client-Apps** > **App-Schutzrichtlinien** > **Richtlinie erstellen** > **Einstellungen** > **Zugriffsanforderungen** zur Verfügung. Dieses Feature kann auf [iOS](../apps/app-protection-policy-settings-ios.md)- und [Android](../apps/app-protection-policy-settings-android.md)-Geräten verwendet werden und unterstützt positive ganze Zahlen als Wert.

#### <a name="intune-device-reporting-fields---2748738---"></a>Felder zur Geräteberichterstellung in Intune<!-- 2748738 -->
Intune bietet zusätzliche Felder zur Geräteberichtserstellung, einschließlich Feldern für App-Registrierungs-ID, Android-Hersteller, Modell und Sicherheitspatchversion sowie iOS-Modell. In Intune sind diese Felder unter **Client-Apps** > **Status des App-Schutzes** und **Bericht zum App-Schutz: iOS, Android** verfügbar. Darüber hinaus werden diese Parameter Sie bei der Konfiguration der **Zulassen**-Liste für den Gerätehersteller (Android), der **Zulassen**-Liste für das Gerätemodell (Android und iOS) sowie der Einstellung der mindestens erforderlichen Android-Sicherheitspatchversion unterstützen.

#### <a name="toast-notifications-for-win32-apps---3136566-----"></a>Popupbenachrichtigungen für Win32-Apps<!-- 3136566   -->
Sie können die Anzeige von Popupbenachrichtigungen für die Benutzer per App-Zuweisung unterdrücken. Wählen Sie in Intune **Client-Apps** > **Apps** > App-Auswahl > **Zuweisungen** > **Gruppen einschließen**.

#### <a name="intune-app-protection-policies-ui-update---3251427----"></a>Update der Benutzeroberfläche für Intune-App-Schutzrichtlinien<!-- 3251427  -->
Wir haben die Bezeichnungen für Einstellungen und Schaltflächen für den Intune-App-Schutz geändert, um die Verständlichkeit zu erleichtern. Einige Änderungen sind:  
- Die Steuerelemente **Ja** / **Nein** wurden in erster Linie in die Steuerelemente **Blockieren** / **Zulassen** und **Deaktivieren** / **Aktivieren** geändert. Die Bezeichnungen wurden ebenfalls aktualisiert.  
- Einstellungen wurden darüber hinaus neu formatiert, um die Einstellungen und ihre Bezeichnungen im Steuerelement nebeneinander anzuzeigen und eine bessere Navigation zu ermöglichen.

Die Standardeinstellungen und die Anzahl von Einstellungen bleiben gleich, aber durch die oben genannten Änderungen werden Verständlichkeit, Navigation und Verwendung der Einstellungen verbessert, um dem Benutzer eine einfachere Anwendung der ausgewählten App-Schutzrichtlinien zu ermöglichen. Weitere Informationen finden Sie unter [iOS-Einstellungen](../apps/app-protection-policy-settings-ios.md) und [Android-Einstellungen](../apps/app-protection-policy-settings-android.md).

#### <a name="additional-settings-for-outlook---3301182----"></a>Zusätzliche Einstellungen für Outlook<!-- 3301182  -->
Sie können nun die folgenden zusätzlichen Einstellungen für Outlook für iOS und Android mit Intune konfigurieren:

- Lassen Sie nur die Verwendung von Geschäfts-, Schul- oder Unikonten in Outlook in iOS und Android zu.
- Stellen sie eine moderne Authentifizierung für Office 365 und eine hybride moderne Authentifizierung für lokale Konten bereit.
- Verwenden Sie `SAMAccountName` für das Feld „Benutzername“ im E-Mail-Profil, wenn die Basisauthentifizierung aktiviert ist.
- Ermöglichen Sie das Speichern von Kontakten.
- Konfigurieren von E-Mail-Infos externer Empfänger
- Konfigurieren Sie **Posteingang mit Relevanz**.
- Erfordern Sie biometrische Daten für den Zugriff auf Outlook für iOS.
- Blockieren Sie externe Bilder.

> [!NOTE]
> Wenn Sie die Richtlinien für den Intune-App-Schutz zur Verwaltung des Zugriffs auf Unternehmensidentitäten verwenden, sollten Sie ggf. nicht aktivieren, dass **biometrische Daten erforderlich** sind. Weitere Informationen finden Sie unter **Unternehmensanmeldeinformationen für Zugriff erforderlich** für [iOS-Zugriffseinstellungen](../apps/app-protection-policy-settings-ios.md#access-requirements) und [Android-Zugriffseinstellungen](../apps/app-protection-policy-settings-android.md#access-requirements).

Weitere Informationen finden Sie unter [Microsoft Outlook-Konfigurationseinstellungen](../apps/app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps---1352553---"></a>Löschen von Android Enterprise-Apps<!-- 1352553 -->
Sie können verwaltete Google Play-Apps aus Microsoft Intune löschen. Um eine verwaltete Google Play-App zu löschen, öffnen Sie Microsoft Intune im Azure-Portal und wählen **Client-Apps** > **Apps** aus. Klicken Sie in der App-Liste auf die Auslassungspunkte (...) rechts neben der verwalteten Google Play-App, und wählen Sie dann in der angezeigten Liste die Option **Löschen** aus. Wenn Sie eine verwaltete Google Play-App aus der App-Liste löschen, wird die Genehmigung für die Google Play-App automatisch aufgehoben.

#### <a name="managed-google-play-app-type---1352580---"></a>App-Typ „Verwaltetes Google Play“<!-- 1352580 -->
Der App-Typ **Verwaltetes Google Play** ermöglicht es Ihnen, [verwaltete Google Play-Apps](https://play.google.com/work/search?q=microsoft&c=apps) gezielt zu Intune hinzuzufügen. Als Intune-Administrator können Sie verwaltete Google Play-Apps ab sofort in Intune suchen, genehmigen, synchronisieren und genehmigte verwaltete Google Play-Anwendungen zuweisen.  Sie müssen nicht mehr separat zur verwalteten Google Play-Konsole navigieren, und es ist keine erneute Authentifizierung mehr erforderlich.  Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie in der Liste **App-Typ** als App-Typ **Verwaltetes Google Play** aus.

#### <a name="default-android-pin-keyboard---3802457---"></a>Android-Standardtastatur für die PIN<!-- 3802457 -->
Endbenutzer, die eine Intune-App-Schutzrichtlinien-PIN auf ihren Android-Geräten vom Typ „Numerisch“ festgelegt haben, wird nun die Android-Standardtastatur anstelle der zuvor entworfenen, festen Android-Tastaturbenutzeroberfläche angezeigt. Diese Änderung wurde implementiert, damit die Standardtastaturen für die PIN-Typen „Numerisch“ und/oder „Passcode“ auf Android- und iOS-Geräten konsistent sind. Weitere Informationen über die Zugriffseinstellungen für Endbenutzer unter Android, z.B. APP-PIN, finden Sie unter [Android-Zugriffsanforderungen](../apps/app-protection-policy-settings-android.md#access-requirements).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrative Vorlagen stehen als Public Preview zur Verfügung und wurden in ihr eigenes Konfigurationsprofil verschoben <!-- 3322847 -->

Administrative Vorlagen in Intune (**Gerätekonfiguration** > **Administrative Vorlagen**) stehen derzeit als Public Preview zur Verfügung. Mit diesem Update:

- Administrative Vorlagen umfassen über 300 Einstellungen, die in Intune verwaltet werden können. Diese Einstellungen waren zuvor nur im Gruppenrichtlinien-Editor vorhanden.
- Administrative Vorlagen befinden sich in der öffentlichen Vorschauphase.
- Administrative Vorlagen werden von **Gerätekonfiguration** > **Administrative Vorlagen** verschoben. Gehen Sie zukünftig wie folgt vor, um administrative Vorlagen aufzurufen: **Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie für **Plattform** **Windows 10 und höher** und für **Profiltyp** **Administrative Vorlagen** aus.
- Die Berichterstellung ist aktiviert.

Unter [Windows 10 templates to configure group policy settings (Windows 10-Vorlagen zur Konfiguration von Gruppenrichtlinieneinstellungen)](../configuration/administrative-templates-windows.md) erfahren Sie mehr zu diesem Feature.

Gilt für: Windows 10 und höher

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user---1333642---"></a>Verwenden von S/MIME zum Verschlüsseln und Signieren von mehreren Geräten für einen Benutzer<!-- 1333642 -->
Mit diesem Update wird die E-Mail-Verschlüsselung mit S/MIME mittels eines neuen Profils für importierte Zertifikate eingeführt. Navigieren Sie zu deren Verwendung zu **Gerätekonfiguration** > **Profile** > **Profil erstellen**, und wählen Sie zuerst die Plattform und dann den Profiltyp **Importiertes PKCS-Zertifikat** aus. In Intune können Sie Zertifikate im PFX-Format importieren. Intune kann dann genau diese Zertifikate an mehrere Geräte übergeben, die durch einen einzelnen Benutzer registriert wurden. Außerdem enthalten:
- Das native iOS-E-Mail-Profil unterstützt die Aktivierung der S/MIME-Verschlüsselung mithilfe importierter Zertifikate im PFX-Format.
- Die native E-Mail-App auf Windows Phone 10-Geräten verwendet automatisch das S/MIME-Zertifikat.
- Die privaten Zertifikate können über mehrere Plattformen übermittelt werden. Jedoch unterstützen nicht alle E-Mail-Apps S/MIME.
- Auf anderen Plattformen müssen Sie möglicherweise die E-Mail so konfigurieren, dass Sie S/MIME zulässt.  
- E-Mail-Apps, die die S/MIME-Verschlüsselung unterstützen, behandeln das Abrufen von Zertifikaten für die S/MIME-E-Mail-Verschlüsselung womöglich in einer Art und Weise, die von MDM nicht unterstützt werden kann, z.B. durch Lesen über den Zertifikatspeicher des Verlegers.
Weitere Informationen zu diesem Feature finden Sie unter [S/MIME für die Signierung und Verschlüsselung von E-Mails in Intune](../protect/certificates-s-mime-encryption-sign.md).
Unterstützt unter: Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices---1333665-2999078---"></a>Neue Optionen zum automatischen Herstellen einer Verbindung und Beibehalten von Regeln bei der Verwendung von DNS-Einstellungen unter Windows 10 und höher<!-- 1333665, 2999078 -->
Auf Geräten unter Windows 10 und höher können Sie ein VPN-Konfigurationsprofil erstellen, das eine Liste von DNS-Servern zum Auflösen von Domänen enthält, z. B. „contoso.com“. Dieses Update enthält neue Einstellungen für die Namensauflösung (Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**. Wählen Sie **Windows 10 und höher** als Plattform und **VPN** als Profiltyp aus, und wählen Sie **DNS-Einstellungen** >**Hinzufügen** aus): 
- **Automatisch verbinden**: Wenn **Aktiviert**, stellt das Gerät automatisch eine Verbindung mit dem VPN her, wenn ein Gerät mit einer Domäne Kontakt aufnimmt, die Sie eingeben, z.B. „contoso.com“.
- **Persistent**: Standardmäßig sind alle Regeln der Namensauflösungsrichtlinie-Tabelle (Name Resolution Policy Table, NRPT) aktiv, solange das Gerät über dieses VPN-Profil verbunden ist. Wenn diese Einstellung für eine NRPT-Regel **aktiviert** ist, bleibt die Regel auch dann auf dem Gerät aktiv, wenn das VPN getrennt ist. Die Regel bleibt in Kraft, bis das VPN-Profil entfernt wird oder bis die Regel manuell entfernt wird – dies kann über PowerShell erfolgen.
In [VPN-Einstellungen für Windows 10](../configuration/vpn-settings-windows-10.md) werden die Einstellungen beschrieben.

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices---1500165---"></a>Verwenden vertrauenswürdiger Netzwerkerkennung für VPN-Profile auf Windows 10-Geräten<!-- 1500165 -->
Wenn Sie die Erkennung vertrauenswürdiger Netzwerke verwenden, können Sie verhindern, dass VPN-Profile automatisch eine VPN-Verbindung herstellen, wenn der Benutzer sich bereits in einem vertrauenswürdigen Netzwerk befindet. Sie können DNS-Suffixe zum Aktivieren der Erkennung vertrauenswürdiger Netzwerke auf Geräten mit Windows 10 und höher hinzufügen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** als Plattform und **VPN** als Profiltyp).
In [VPN-Einstellungen für Windows 10](../configuration/vpn-settings-windows-10.md) sind die aktuellen VPN-Einstellungen aufgeführt.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users---1907917-1063203---"></a>Verwalten von Windows Holographic for Business-Geräten, die von mehreren Benutzern verwendet werden<!-- 1907917, 1063203 -->
Derzeit können Sie gemeinsame PC-Einstellungen auf Windows 10- und Windows Holographic for Business-Geräten mithilfe einer benutzerdefinierten OMA-URI-Einstellung konfigurieren. Mit diesem Update wird ein neues Profil zum Konfigurieren gemeinsamer PC-Einstellungen hinzugefügt (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** > **Freigegebenes, von mehreren Benutzern verwendetes Gerät**).
Im Artikel zu [Intune-Einstellungen zum Verwalten gemeinsam verwendeter Geräte](../configuration/shared-user-device-settings.md) erfahren Sie mehr zu diesem Feature.
Gilt für: Windows 10 und höher, Windows Holographic for Business

#### <a name="new-windows-10-update-settings--2626030--2512994----"></a>Neue Windows 10-Updateeinstellungen<!--2626030  2512994  -->
Für Ihre [Windows 10-Updateringe](../protect/windows-update-for-business-configure.md) können Sie folgende Konfigurationen vornehmen:
- **Verhalten bei automatischen Updates**: Verwenden Sie die neue Option *Standard wiederherstellen* zum Wiederherstellen der ursprünglichen Einstellungen für automatische Updates auf einem Windows 10-Computer auf Computern, die das *Oktober 2018-Update* ausführen
- **Verweigern des Anhalten eines Updates**: Konfigurieren Sie eine neuen Softwareupdateseinstellung, mit der Sie blockieren oder zulassen können, dass Ihre Benutzer Updateinstallationen über die *Einstellungen* ihrer Computer anhalten.

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption---2662949---"></a>iOS-E-Mail-Profile können S/MIME-Signatur und -Verschlüsselung verwenden<!-- 2662949 -->
Sie können ein E-Mail-Profil erstellen, das unterschiedliche Einstellungen enthält. Dieses Update umfasst S/MIME-Einstellungen, die zum Signieren und Verschlüsseln der E-Mail-Kommunikation auf iOS-Geräten verwendet werden können (**Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie **iOS** als Plattform und **E-Mail** als Profiltyp aus).
Unter [iOS-E-Mail-Konfigurationseinstellungen](../configuration/email-settings-ios.md) werden die Einstellungen aufgelistet.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Einige BitLocker-Einstellungen unterstützen die Windows 10 Pro-Edition<!-- 2727036 -->
Sie können ein Konfigurationsprofil erstellen, das die Endpunktschutzeinstellungen auf Windows 10-Geräten einschließlich BitLocker festlegt. Mit diesem Update wird die Unterstützung für Windows 10 Professional für einige BitLocker-Einstellungen hinzugefügt.
Diese Schutzeinstellungen finden Sie unter [Endpoint protection settings for Windows 10 (Endpunktschutzeinstellungen für Windows 10)](../protect/endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>„Konfiguration freigegebener Geräte“ wurde für iOS-Geräte im Azure-Portal in „Nachricht auf Sperrbildschirm“ umbenannt<!-- 2809362 -->
Bei der Erstellung eines Konfigurationsprofils für iOS-Geräte können Sie **Konfigurationen für gemeinsam verwendete Geräte** vornehmen, um einem bestimmten Text auf dem Sperrbildschirm anzuzeigen. Dieses Update umfasst folgende Änderungen: 
- Die **Konfiguration freigegebener Geräte**-Einstellungen im Azure-Portal werden umbenannt in „Nachricht auf Sperrbildschirm (nur überwacht)“ (**Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie **iOS** als Plattform und **Gerätefunktionen** als Profiltyp aus, wählen Sie **Nachricht auf Sperrbildschirm** aus).
- Beim Hinzufügen von Sperrbildschirmnachrichten können Sie eine Seriennummer, einen Gerätenamen oder einen anderen gerätespezifischen Wert als Variable in **Bestandskennzeicheninformationen** und einer **Fußnote im Sperrbildschirm** einfügen. Sie können z.B. `Device name: {{devicename}}` oder `Serial number is {{serialnumber}}` mit geschweiften Klammern eingeben. [iOS-Token](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) listet die verfügbaren Token auf, die verwendet werden können.
In den [Einstellungen zur Anzeige von Nachrichten auf dem Sperrbildschirm](../configuration/ios-device-features-settings.md#lock-screen-message) werden die aktuellen Einstellungen aufgelistet.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices---2827760--"></a>Neue Einstellungen für App Store, Dokumentanzeige, Gaminggeräteeinschränkungen auf iOS-Geräten<!-- 2827760-->
In **Device Configuration** > **profiles** > **Create** profile > **IOS** for Platform > **Device Restrictions** for Profile Type > **App Store, doc View, Gaming**werden die folgenden Einstellungen hinzugefügt: verwaltete apps das Schreiben von Kontakten für nicht verwaltete Kontakt Konten erlauben, dass nicht verwaltete apps von verwalteten Kontakt Konten lesen können, um diese Einstellungen anzuzeigen, finden Sie unter [IOS-Geräte Einschränkungen](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices---3201839-3201843---"></a>Neue Benachrichtigungen, Hinweise und Keyguard-Einstellungen für Geräte von Android Enterprise-Gerätebesitzern<!-- 3201839 3201843 -->
Dieses Update umfasst mehrere neue Features für Android Enterprise-Geräte bei Ausführung als Gerätebesitzer. Um diese Features zu verwenden, wechseln Sie zu **Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie als **Plattform** **Android Enterprise** und als **Profiltyp** **Nur Gerätebesitzer** > **Geräteeinschränkungen** aus.

Neue verfügbare Funktionen:

- Deaktivieren der Anzeige von Systembenachrichtigungen einschließlich eingehender Anrufe, Systemwarnungen, Systemfehler und mehr.
- Das Überspringen des Startens von Tutorials und von Hinweisen für Apps, die erstmals geöffnet werden, wird vorgeschlagen.
- Deaktivieren erweiterter Keyguard-Einstellungen, z.B. Kamera, Benachrichtigungen, Fingerabdruckentsperrung und mehr.

Weitere Informationen finden Sie unter [Android Enterprise-Geräteeinstellungen](../configuration/device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections---3202194---"></a>Geräte von Android Enterprise-Gerätebesitzern können Always On-VPN-Verbindungen verwenden<!-- 3202194 -->
In diesem Update können Sie Always On-VPN-Verbindungen mit Geräten von Android Enterprise-Gerätebesitzern verwenden. Always On-VPN-Verbindungen bleiben erhalten oder werden sofort wieder hergestellt, wenn der Benutzer sein Gerät entsperrt, wenn das Gerät neu gestartet wird oder das drahtlose Netzwerk sich ändert. Sie können die Verbindung auch in den „Sperrmodus“ setzen, der den gesamten Netzwerkdatenverkehr blockiert, bis die VPN-Verbindung aktiv ist.
Sie können Always On-VPN wie folgt aktivieren: Wählen Sie in **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** als Plattform, **Geräteeinschränkungen** für „Nur Gerätebesitzer“ und die Einstellungen für **Konnektivität** aus. Weitere Informationen finden Sie unter [Android Enterprise-Geräteeinstellungen](../configuration/device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices---3285177---"></a>Neue Einstellung zum Beenden von Prozessen im Task-Manager auf Windows 10-Geräten<!-- 3285177 --> 
Dieses Update umfasst eine neue Einstellung für Endprozesse im Task-Manager auf Windows 10-Geräten. Mithilfe eines Gerätekonfigurationsprofils (**Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie für **Plattform** **Windows 10** und für **Profiltyp** **Geräteeinschränkungen** > **Allgemein** aus) lassen Sie diese Einstellung zu oder verhindern sie.
Weitere Informationen finden Sie unter [Einstellungen für Geräteeinschränkungen für Windows 10](../configuration/device-restrictions-windows-10.md).
Gilt für: Windows 10 und höher

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview---2055484-----"></a>Verwenden der von Microsoft empfohlenen Einstellungen mit Sicherheitsbaselines (Public Preview)<!-- 2055484   -->

Intune lässt sich mit anderen Diensten integrieren, die sich auf Sicherheit konzentrieren, einschließlich Windows Defender ATP und Office 365 ATP. Die Kunden fordern eine gemeinsame Strategie und einen einheitlichen Satz von End-to-End-Sicherheitsworkflows für die Microsoft 365-Dienste. Unser Ziel ist es, Strategien aufeinander abzustimmen, um Lösungen zu entwickeln, die Sicherheitsvorgänge und allgemeine Administratoraufgaben miteinander verbinden. In Intune beabsichtigen wir, dieses Ziel zu erreichen, indem wir eine Reihe der von Microsoft empfohlenen „Sicherheitsbaselines“ (**Intune** > **Sicherheitsbaselines**) veröffentlichen.  Ein Administrator kann Sicherheitsrichtlinien direkt aus diesen Baselines erstellen und diese dann für seine Benutzer bereitstellen. Sie können auch die Empfehlungen für bewährte Methoden anpassen, um die Anforderungen ihres Unternehmens zu erfüllen. Intune stellt sicher, dass die Geräte den Anforderungen dieser Baselines entsprechen, und benachrichtigt die Administratoren von Benutzern oder Geräten, die nicht den Anforderungen entsprechen.

Dieses Feature befindet sich in der Public Preview, d.h. Profile, die in dieser Version erstellt werden, werden nicht in die allgemein verfügbaren Vorlagen für Sicherheitsbaselines übernommen. Es wird davon abgeraten, diese Preview-Vorlagen in Produktionsumgebungen zu verwenden.

Weitere Informationen zu Sicherheitsbaselines finden Sie unter [Erstellen einer Windows 10-Sicherheitsbaseline in Intune](../protect/security-baselines-monitor.md).

Dieses Feature ist für Geräte unter Windows 10 und höher gültig.

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Nicht-Administratoren können BitLocker auf Windows 10-Geräten aktivieren, die in Azure AD eingebunden sind<!-- 2147379   -->
Beim Aktivieren der BitLocker-Einstellungen auf Windows 10-Geräten (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **Windows 10 und höher** als Plattform > **Endpunktschutz** als Profiltyp > **Windows-Verschlüsselung**) fügen Sie BitLocker-Einstellungen hinzu.

Dieses Update enthält eine neue BitLocker-Einstellung, um Standardbenutzern (Nicht-Administratoren), die Verschlüsselung zu ermöglichen.

Diese Einstellungen finden Sie unter [Endpunktschutzeinstellungen für Windows 10](../protect/endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance---2192052--eepublished----"></a>Überprüfen der Konformität von Configuration Manager<!-- 2192052  eepublished  -->
Dieses Update enthält eine neue Einstellung für die System Center Configuration Manager-Konformität (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Windows 10 und höher** > **Configuration Manager-Konformität**). Der Configuration Manager sendet Signale an die Intune-Konformität. Über diese Einstellung können Sie alle Configuration Manager-Signale auffordern, „konform“ zurückzugeben.

Beispielsweise sollen alle Softwareupdates auf Geräten installiert werden. Im Configuration Manager hat diese Anforderung den Zustand „Installiert“. Falls sich Programme auf dem Gerät in einem unbekannten Zustand befinden, so ist das Gerät in Intune nicht konform.

[Configuration Manager-Konformität](../protect/compliance-policy-create-windows.md#configuration-manager-compliance) beschreibt diese Einstellung.

Gilt für: Windows 10 und höher

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile---2809324-----"></a>Anpassen des Hintergrundbilds auf überwachten iOS-Geräten mithilfe eines Gerätekonfigurationsprofils<!-- 2809324   -->
Wenn Sie ein Gerätekonfigurationsprofil für iOS-Geräte erstellen, können Sie einige Features in **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** für die Plattform > **Gerätefeatures** anpassen. Dieses Update enthält neue **Hintergrundbildeinstellungen**, die es einem Administrator ermöglichen, ein.png-,.jpg- oder.jpeg-Bild auf dem Startbildschirm oder Sperrbildschirm zu verwenden. Die Einstellungen für das Hintergrundbild gelten nur für überwachte Geräte. 

Eine Liste dieser Einstellungen finden Sie [unter iOS-Einstellungen für Gerätefeatures](../configuration/ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available---3594661----"></a>Windows 10-Kiosk ist allgemein verfügbar<!-- 3594661  -->
In diesem Update wird das Kiosk-Feature auf Windows 10 und höher allgemein verfügbar (GA) gemacht. Alle Einstellungen, die Sie hinzufügen und konfigurieren können, finden Sie unter [Kioskeinstellungen für Windows 10 (und höher)](../configuration/kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise---3598396-----"></a>Die Kontaktfreigabe über Bluetooth in „Geräteeinschränkungen“ > „Gerätebesitzer für Android Enterprise“ wurde entfernt<!-- 3598396   -->
Wenn Sie ein Geräteeinschränkungsprofil für Android Enterprise-Geräte erstellen, gibt es die Einstellung **Kontaktfreigabe über Bluetooth**. In diesem Update wird die Einstellung **Kontaktfreigabe über Bluetooth** entfernt (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** für Plattform > **Geräteeinschränkungen > Gerätebesitzer** für Profiltyp > **Allgemein**).

Die Einstellung **Kontaktfreigabe über Bluetooth** wird für die Verwaltung von Android Enterprise-Gerätebesitzern nicht unterstützt. Die Entfernung dieser Einstellung hat deshalb keine Auswirkungen auf Geräte oder Mandanten – selbst dann, wenn diese Einstellung in Ihrer Umgebung aktiviert und konfiguriert ist.

Die aktuelle Liste der Einstellungen finden Sie unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features](../configuration/device-restrictions-android-for-work.md).

Gilt für: Android Enterprise-Gerätebesitzer


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="more-detailed-enrollment-restriction-failure-messaging---3111564---"></a>Ausführlicheres Messaging zu Registrierungseinschränkungsfehlern<!-- 3111564 -->
Wenn die Einschränkungen für die Registrierung nicht erfüllt werden, werden nun aussagekräftigere Fehlermeldungen ausgegeben. Um diese Meldungen anzuzeigen, wechseln Sie zu **Intune** > **Problembehandlung**, und überprüfen Sie die Tabelle „Registrierungsfehler“. Weitere Informationen finden Sie in der Liste mit den [Registrierungsfehlern](help-desk-operators.md#enrollment-failure-reference).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>-Geräteverwaltung
#### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices---1574342----"></a>Vorschau der Unterstützung für vollständig verwaltete Android-Unternehmensgeräte<!-- 1574342  -->
Intune unterstützt jetzt vollständig verwaltete Android-Geräte in einem „Gerätebesitzer“-Szenario, in dem das Unternehmen Besitzer ist und die Geräte konsequent von der IT-Abteilung verwaltet und einzelnen Benutzern zugewiesen werden. So können Administratoren das gesamte Gerät verwalten, einen erweiterten Bereich von Richtlinienkontrollen erzwingen, die Arbeitsprofilen nicht zur Verfügung stehen, und Benutzer werden derart eingeschränkt, dass sie nur Apps von verwaltetem Google Play installieren können. Weitere Informationen finden Sie unter [Einrichten der Intune-Registrierung von vollständig verwalteten Android-Geräten](../enrollment/android-fully-managed-enroll.md) und [Registrieren Ihrer dedizierten Geräte oder vollständig verwalteten Geräte](../enrollment/android-dedicated-devices-fully-managed-enroll.md).  Hinweis: Dieses Feature befindet sich in der Vorschau. Einige Intune-Funktionen, wie z.B. Zertifikate, Konformität und bedingter Zugriff, stehen momentan für vollständig verwaltete Android-Benutzergeräte nicht zur Verfügung.

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices---1434452---"></a>Unterstützung für selektives Zurücksetzen für WIP-Geräte ohne Registrierung<!-- 1434452 -->
Windows Information Protection Without Enrollment (WIP-WE) ermöglicht es Kunden, ihre Unternehmensdaten auf Windows 10-Geräten zu schützen, ohne dass eine vollständige MDM-Registrierung erforderlich ist. Sobald Dokumente durch eine WIP-WE-Richtlinie geschützt sind, können die geschützten Daten von einem Intune-Administrator selektiv zurückgesetzt werden. Durch die Auswahl von Benutzer und Gerät und das Senden einer Anforderung zum Zurücksetzen werden alle Daten, die durch die WIP-WE-Richtlinie geschützt waren, unbrauchbar. Wählen Sie über Intune im Azure-Portal die Option **Mobile App** > **Selektive App-Zurücksetzung** aus.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="tenant-status-dashboard---1124854---"></a>Dashboard zum Mandantenstatus<!-- 1124854 -->
Auf der neuen Seite mit dem [Mandantenstatus](tenant-status.md) können Sie auf einen Blick den Status Ihres Mandanten und damit verbundene Informationen sehen.  Dieses Dashboard ist in vier Bereiche unterteilt:
- **Tenant Details** (Mandantendetails): Hier werden z. B. Ihre MDM-Autorität, die insgesamt bei Ihrem Mandanten angemeldeten Geräte und die Anzahl Ihrer Lizenzen angezeigt. In diesem Abschnitt wird auch die aktuelle Dienstversion für Ihren Mandanten angezeigt.
- **Connector Status** (Connectorstatus): Hier werden Informationen zu verfügbaren konfigurierten Connectors angezeigt und deaktivierte Connectors aufgelistet.  
   Basierend auf ihrem aktuellen Status werden die Connectors als „Healthy“ (Fehlerfrei), „Warning“ (Warnung) oder „Unhealthy“ (Fehlerhaft) gekennzeichnet. Wählen Sie einen Connector aus, den Sie sich genauer ansehen möchten, und zeigen Sie weitere Details an, oder konfigurieren Sie zusätzliche Informationen.
- **Intune Service Health** (Intune-Dienstintegrität): Hier werden aktive Vorfälle oder Ausfälle für Ihren Mandanten angezeigt. Die Informationen in diesem Abschnitt werden direkt über das Office-Nachrichtencenter abgerufen.
- **Intune News** (Neuigkeiten zu Intune): Hier werden aktive Meldungen Ihres Mandanten angezeigt. Dazu zählen u. a. Benachrichtigungen zu den neuesten Intune-Features.  Die Informationen in diesem Abschnitt werden direkt über das Office-Nachrichtencenter abgerufen.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10---1488939--"></a>Neue Hilfe- und Supportbenutzeroberfläche im Unternehmensportal für Windows 10<!-- 1488939-->
Über die neue Seite für Hilfe und Support im Intune-Unternehmensportal können Benutzer Probleme beheben und Hilfe zu App- und Zugriffsproblemen erhalten. Über die neue Seite können sie Informationen zu Fehler- und Diagnoseprotokollen per E-Mail versenden und Informationen zum Helpdesk ihrer Organisation erhalten. Zudem gibt es einen Bereich mit häufig gestellten Fragen und Links zu relevanten Intune-Dokumentationsartikeln.

#### <a name="new-help-and-support-experience-for-intune---3307080---"></a>Neue Benutzeroberfläche für Hilfe und Support für Intune<!-- #3307080 -->
Innerhalb der nächsten Tage wird diese neue Hilfe- und Supportbenutzeroberfläche für alle Mandanten verfügbar gemacht. Diese neue Benutzeroberfläche ist für Intune verfügbar und kann über das Blatt „Intune“ im [Azure-Portal](https://portal.azure.com/) verwendet werden.
Über die neue Benutzeroberfläche können Sie Ihr Problem in eigenen Worten beschreiben und erhalten Einblicke in die Problembehandlung sowie webbasierte Anleitungen zur Selbsthilfe. Diese Lösungen werden über einen regelbasierten Algorithmus für maschinelles Lernen angeboten, der auf Benutzeranfragen basiert. Zusätzlich zur themenspezifischen Anleitung können Sie auch den neuen Workflow zur Anfragestellung nutzen, um eine Supportanfrage per E-Mail oder Telefon zu stellen. Diese neue Benutzeroberfläche ersetzt die alte Benutzeroberfläche für Hilfe und Support, die statische, vorab ausgewählte Optionen enthielt. Diese basieren auf dem Bereich der Konsole, in dem Sie sich befinden, wenn Sie „Hilfe und Support“ öffnen.
Weitere Informationen finden Sie unter [Anfordern von Support für Microsoft Intune](get-support.md).

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services---3762211----"></a>Neue Betriebsprotokolle und Möglichkeit zum Senden von Protokollen an Azure Monitor-Dienste<!-- 3762211  -->
Intune bietet eine integrierte Überwachungsprotokollierung, die Ereignisse bei Änderungen verfolgt. Dieses Update enthält neue Protokollierungsfeatures, darunter: 
- Betriebsprotokolle (Vorschau), die Details für Benutzer und Geräte anzeigen, die registriert sind, einschließlich der erfolgreichen und fehlerhaften Versuche.
- Die Überwachungs- und Betriebsprotokolle können an Azure Monitor gesendet werden, einschließlich Speicherkonten, Event Hubs und Log Analytics. Diese Dienste ermöglichen es Ihnen, Analysen wie Splunk und QRadar zu speichern, zu nutzen und Visualisierungen Ihrer Protokolldaten zu erhalten.

In [Senden von Daten an den Speicher, Event Hubs oder Log Analytics in Intune](../review-logs-using-azure-monitor.md) finden Sie weitere Informationen zu diesem Feature.

#### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device---2687509----"></a>Überspringen weiterer Setup-Assistent-Anzeigen auf einem iOS-DEP-Gerät<!-- 2687509  -->
Zusätzlich zu den Bildschirmen, die Sie derzeit überspringen können, können Sie iOS-DEP-Geräte so einzustellen, dass die folgenden Bildschirme des Setup-Assistenten übersprungen werden, wenn ein Benutzer das Gerät registriert: „Displayton“, „Datenschutz“, „Android-Migration“, „Home-Taste“, „iMessage & FaceTime“, „Onboarding“, „Watch-Migration“, „Darstellung“, „Bildschirmzeit“, „Softwareupdate“, „SIM-Setup“.
Um die zu überspringenden Bildschirme auszuwählen, wechseln Sie zu **Geräteregistrierung** > **Apple-Registrierung** > **Token für Registrierungsprogramm**, wählen Sie das Token und unter **Profile** das Profil aus, wählen Sie **Eigenschaften** > **Anpassung des Setup-Assistenten** und **Ausblenden** für alle Bildschirme aus, die Sie überspringen möchten, und wählen Sie **OK** aus.
Wenn Sie ein neues Profil erstellen oder ein Profil bearbeiten, müssen die ausgewählten zu überspringenden Bildschirme mit dem Apple MDM-Server synchronisiert werden. Benutzer können eine manuelle Synchronisierung der Geräte durchführen, sodass es keine Verzögerung bei der Auswahl der Profiländerungen gibt.

#### <a name="android-enterprise-app-we-app-deployment---1171203---"></a>Android Enterprise APP-WE-App-Bereitstellung<!-- 1171203 -->
Für Android-Geräte in einem Bereitstellungsszenario mit einer nicht registrierten App-Schutzrichtlinie ohne Registrierung (App Protection Policy Without Enrollment, APP-WE) können Sie jetzt verwaltetes Google Play zum Bereitstellen von Store-Apps und branchenspezifischen Apps für Benutzer verwenden. Insbesondere können Sie Endbenutzern einen App-Katalog bieten und für einen Installationsvorgang sorgen, in dem Endbenutzer nicht mehr den Sicherheitsstatus ihrer Geräte gefährden müssen, indem sie Installationen aus unbekannten Quellen zulassen. Darüber hinaus sorgt dieses Bereitstellungsszenario für höhere Benutzerfreundlichkeit.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="scope-tags-for-apps---1081941---"></a>Bereichsmarkierungen für Apps<!-- 1081941 -->
Sie können Bereichsmarkierungen erstellen, um den Zugriff für Rollen und Apps einzuschränken. Sie können einer App eine Bereichsmarkierung hinzufügen, sodass nur Benutzer mit der gleichen Bereichsmarkierung wie die App auf diese zugreifen können. Derzeit können Apps, die Intune über den verwalteten Google Play Store hinzugefügt wurden oder die mithilfe des Apple Volume Purchase Program (VPP) erworben wurden, keine Bereichsmarkierungen hinzugefügt werden (zukünftige Unterstützung dafür ist geplant). Weitere Informationen finden Sie unter [Use scope tags to filter policies (Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien)](scope-tags.md).




<!-- ########################## -->
## <a name="december-2018"></a>Dezember 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="updates-for-application-transport-security---748318---"></a>Updates der Application Transport Security-Technologie<!-- 748318 -->

Microsoft Intune unterstützt Version 1.2 und höher des TLS-Protokolls (Transport Layer Security). Dieses Protokoll bietet erstklassige Verschlüsselungsfunktionen, um eine höhere standardmäßige Sicherheit von Intune zu gewährleisten und Intune auf andere Microsoft-Dienste wie Microsoft Office 365 abzustimmen. Um diese Anforderung zu erfüllen, erzwingen die iOS- und macOS-Unternehmensportale die aktualisierte ATS-Technologie (Application Transport Security) von Apple, die ebenfalls die Verwendung von TLS 1.2 und höher erfordert. ATS wird verwendet, um eine strengere Sicherheit in allen App-Kommunikationen über HTTPS zu erzwingen. Diese Änderung hat Auswirkungen für Intune-Kunden, die Unternehmensportal-Apps unter iOS und macOS verwenden. Weitere Informationen finden Sie im [Intune-Supportblog](https://aka.ms/compportalats).

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys---1832174---"></a>Das Intune App SDK unterstützt 256-Bit-Verschlüsselungsschlüssel<!-- 1832174 -->
Das Intune App SDK für Android verwendet jetzt 256-Bit-Verschlüsselungsschlüssel, wenn die Verschlüsselung durch App-Schutzrichtlinien aktiviert wird. Das SDK bietet zur Kompatibilität mit Inhalten und Apps, die ältere SDK-Versionen verwenden, weiterhin Unterstützung der 128-Bit-Schlüssel.

#### <a name="microsoft-auto-update-version-450-required-for-macos-devices---3503442---"></a>Microsoft AutoUpdate Version 4.5.0 für macOS-Geräte erforderlich<!-- 3503442 -->
Von Intune verwaltete macOS-Geräte müssen auf Microsoft AutoUpdate 4.5.0 upgegradet werden, um weiterhin Updates für das Unternehmensportal und andere Office-Anwendungen zu erhalten. Benutzer verfügen möglicherweise bereits über diese Version für ihre Office-Apps.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="intune-requires-macos-1012-or-later---2827778---"></a>Für Intune ist macOS 10.12 oder höher erforderlich<!-- 2827778 -->
Für Intune ist jetzt macOS Version 10.12 oder höher erforderlich. Geräte mit früheren macOS-Versionen können sich nicht über das Unternehmensportal in Intune registrieren. Wenn Benutzer Unterstützung und neue Features erhalten möchten, müssen sie für ihr Gerät ein Upgrade auf macOS 10.12 oder höher und für das Unternehmensportal ein Upgrade auf die neueste Version durchführen.

<!-- ########################## -->
## <a name="november-2018"></a>November 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices---1281677---"></a>Deinstallieren von Apps auf unternehmenseigenen überwachten iOS-Geräten<!-- 1281677 -->
Sie können beliebige unternehmenseigene überwachte iOS-Geräte entfernen. Sie können eine beliebige App entfernen, indem Sie entweder Benutzer- oder Gerätegruppen mit dem Zuweisungstyp **Deinstallieren** als Ziel verwenden. Für persönliche oder nicht überwachte iOS-Geräte können weiterhin nur Apps entfernt werden, die mit Intune installiert wurden.

#### <a name="downloading-intune-win32-app-content---2617320---"></a>Herunterladen von Intune Win32-App-Inhalten<!-- 2617320 -->
Clients von Windows 10 RS3 und höher laden Intune Win32-App-Inhalte mit einer Komponente zur Übermittlungsoptimierung auf den Windows 10-Client herunter. Die Übermittlungsoptimierung bietet Peer-zu-Peer-Funktionen, die standardmäßig eingeschaltet sind. Die Übermittlungsoptimierung kann derzeit mit einer Gruppenrichtlinie konfiguriert werden. Weitere Informationen finden Sie unter [Übermittlungsoptimierung für Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization).

#### <a name="end-user-device-and-app-content-menu---2771453---"></a>Endbenutzergerät und App-Inhaltsmenü<!-- 2771453 -->
Endbenutzer können jetzt über das Kontextmenü auf Geräten und in Apps häufig verwendete Aktionen auslösen, z.B. das Umbenennen eines Geräts oder die Prüfung der Konformität.

#### <a name="set-custom-background-in-managed-home-screen-app----3041945---"></a>Festlegen eines benutzerdefinierten Hintergrunds in der Managed Home Screen-App <!-- 3041945 -->
Es wird eine Einstellung hinzugefügt, mit der Sie den Hintergrund der Managed Home Screen-App auf Android Enterprise-, Multi-App- und Kioskmodusgeräten anpassen können.  Um eine **URL für einen benutzerdefinierten Hintergrund** zu konfigurieren, wechseln Sie im Azure-Portal zu Intune und dann zur Gerätekonfiguration. Wählen Sie ein aktuelles Gerätekonfigurationsprofil aus, oder erstellen Sie ein neues Profil, um die zugehörigen Kioskeinstellungen zu bearbeiten.
Informationen zu den Kioskeinstellungen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android Enterprise](../configuration/device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply---3104570---"></a>Speichern und Anwenden von App-Schutzrichtlinienzuweisungen<!-- 3104570 -->
Sie erhalten jetzt eine bessere Kontrolle über Ihre [App-Schutzrichtlinienzuweisungen](../apps/app-protection-policies.md). Wenn Sie *Zuweisungen* auswählen, um die Zuweisungen einer Richtlinie festzulegen oder zu bearbeiten, müssen Sie Ihre Konfiguration **speichern**, bevor die Änderung angewendet wird. Löschen Sie mit **Verwerfen** alle Änderungen, die Sie vornehmen, ohne Änderungen in den Listen zum Einschließen oder Ausschließen zu speichern.  Wenn Speichern oder Verwerfen erforderlich ist, werden nur die von Ihnen vorgesehenen Benutzer einer App-Schutzrichtlinie zugewiesen.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later---3174639---"></a>Neue Microsoft Edge-Browsereinstellungen für Windows 10 und höher<!-- 3174639 -->
Dieses Update enthält neue Einstellungen, die Sie dabei unterstützen, den Microsoft Edge-Browser auf Ihren Geräten zu steuern und zu verwalten. Eine Liste dieser Einstellungen finden Sie in den [Geräteeinschränkungen für Windows 10 (und höher)](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies---3330037---"></a>Unterstützung neuer Apps mit App-Schutzrichtlinien<!-- 3330037 -->
Sie können jetzt die folgenden Apps mit [Intune-App-Schutzrichtlinien](../apps/app-protection-policies.md) verwalten:
- Stream (iOS)
- To DO (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Verwenden Sie App-Schutzrichtlinien, um für diese Apps Unternehmensdaten zu schützen und die Datenübertragung zu steuern, wie andere richtlinienverwaltete Intune-Apps. Hinweis: Wenn Flow noch nicht in der Konsole sichtbar ist, fügen Sie Flow beim Erstellen oder Bearbeiten von App-Schutzrichtlinien hinzu. Verwenden Sie hierzu die Option **+ Weitere Apps**, und geben Sie dann die *App-ID* für Flow in das Eingabefeld ein. Verwenden Sie für Android *com.microsoft.flow* und für iOS *com.microsoft.procsimo*.


### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="support-for-ios-12-oauth-in-ios-email-profiles--2155106---"></a>Unterstützung von iOS 12 OAuth in iOS-E-Mail-Profilen<!--2155106 -->
Die iOS-E-Mail-Profile in Intune unterstützen nun Open Authorization (OAuth) für iOS 12. Wenn Sie dieses Feature verwenden möchten, erstellen Sie ein neues Profil (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **E-Mail** (Profiltyp)), oder aktualisieren Sie ein vorhandenes iOS-E-Mail-Profil. Wenn Sie OAuth in einem Profil aktivieren, das bereits für Benutzer bereitgestellt wurde, werden die Benutzer zur erneuten Authentifizierung und zum Erneuten Herunterladen ihrer E-Mails aufgefordert.

Unter [Einstellungen für E-Mail-Profile für iOS-Geräte](../configuration/email-settings-ios.md) finden Sie weitere Informationen zur Verwendung von OAuth für E-Mail-Profile.

#### <a name="network-access-control-nac-support-for-citrix-sso-for-ios---3259404---"></a>Unterstützung der Netzwerkzugriffssteuerung für Citrix SSO für iOS<!-- 3259404 -->
Citrix hat ein Update für Citrix Gateway veröffentlicht, um die Netzwerkzugriffssteuerung (Network Access Control, NAC) für Citrix SSO für iOS in Intune zu ermöglichen. Sie können eine Geräte-ID in einem VPN-Profil in Intune einschließen und dieses Profil dann mithilfe von Push an Ihre iOS-Geräte übertragen. Sie müssen das neueste Update für Citrix Gateway installieren, um diese Funktion nutzen zu können.

Der Artikel [Konfigurieren von VPN-Einstellungen auf iOS-Geräten in Microsoft Intune](../configuration/vpn-settings-ios.md#base-vpn-settings) enthält weitere Informationen zur Verwendung der NAC sowie einige zusätzliche Anforderungen. 

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown---1892471---"></a>Anzeige der Versionsnummern und Buildnummern von iOS und macOS<!-- 1892471 -->
Unter **Gerätekonformität** > **Gerätekonformität** wird die iOS-und macOS-Betriebssystemversion angezeigt, für die Konformitätsrichtlinien verwendet werden können. Dieses zukünftige Update umfasst auch die Buildnummer, die für beide Plattformen konfigurierbar ist.
Wenn Sicherheitsupdates veröffentlicht werden, bleibt die Versionsnummer von Apple in der Regel unverändert bestehen, die Buildnummer wird jedoch aktualisiert. Wenn Sie die Buildnummer in einer Konformitätsrichtlinie verwenden, können Sie einfach überprüfen, ob ein Sicherheitsupdate installiert wurde.
Wie Sie dieses Feature verwenden, erfahren Sie in den [iOS](../protect/compliance-policy-create-ios.md#device-health)- und [macOS](../protect/compliance-policy-create-mac-os.md#device-properties)-Konformitätsrichtlinien.

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later---2753807---"></a>Updateringe wurden durch Einstellungen zur Übermittlungsoptimierung für Windows 10 und höher ersetzt<!-- 2753807 -->
Die Übermittlungsoptimierung ist ein neues Konfigurationsprofil für Windows 10 und höher. Diese Funktion bietet eine optimierte Benutzeroberfläche zum Übermitteln von Softwareupdates an Geräte in Ihrer Organisation. Mit diesem Update können Sie die Einstellungen auch mithilfe eines Konfigurationsprofils an neue und vorhandene Updateringe übermitteln.
Wie Sie ein Konfigurationsprofil für die Übermittlungsoptimierung konfigurieren, erfahren Sie unter [Einstellungen zur Übermittlungsoptimierung in Microsoft Intune in Windows 10 (und höher)](../configuration/delivery-optimization-windows.md).

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices---2827760---"></a>Neue Einstellungen für Geräteeinschränkungen wurden für iOS- und macOS-Geräte hinzugefügt<!-- 2827760 -->
Dieses Update enthält neue Einstellungen für Ihre iOS- und macOS-Geräte, die mit iOS 12 veröffentlicht werden:

**iOS-Einstellungen**: 
- Allgemein: Entfernen von Apps blockieren (nur überwacht)
- Allgemein: Eingeschränkten USB-Modus blockieren (nur überwacht)
- Allgemein: Automatische Datums- und Uhrzeiteinstellung erzwingen (nur überwacht)
- Kennwort: AutoAusfüllen für Kennwörter blockieren (nur überwacht)
- Kennwort: Kennwortanforderungen durch Näherung blockieren (nur überwacht)
- Kennwort: Kennwortfreigabe blockieren (nur überwacht)

**macOS-Einstellungen**: 
- Kennwort: Automatische Füllung des Kennworts blockieren
- Kennwort: Kennwortanforderungen durch Näherung blockieren
- Kennwort: Kenn Wort Freigabe blockieren

Mehr über diese Einstellungen finden Sie in den Einstellungen für Geräteeinschränkungen unter [iOS](../configuration/device-restrictions-ios.md) und [macOS](../configuration/device-restrictions-macos.md).

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview---1048100--"></a>Autopilot-Unterstützung für in Azure Active Directory Hybrid eingebundene Geräte (Preview)<!-- 1048100-->
Sie können ab sofort in Azure Active Directory Hybrid eingebundene Geräte mithilfe von Autopilot einrichten. Geräte müssen mit dem Netzwerk Ihres Unternehmens verbunden sein, um das Hybrid-Autopilot-Feature nutzen zu können. Weitere Informationen finden Sie unter [Bereitstellen von in Azure AD Hybrid eingebundenen Geräten mit Intune und Windows Autopilot](../enrollment/windows-autopilot-hybrid.md).
Dieses Feature wird in den nächsten Tagen für Benutzer eingeführt. Daher können Sie diese Schritte möglicherweise erst ausführen, wenn es für Ihr Konto eingeführt wurde.

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Auswählen von Apps zur Nachverfolgung auf der Registrierungsstatusseite<!-- 2531007 -->
Sie können auswählen, welche Apps auf der Registrierungsstatusseite nachverfolgt werden. Solange diese Apps nicht installiert sind, kann der Benutzer das Gerät nicht verwenden. Weitere Informationen finden Sie unter [Einrichten einer Statusseite für die Registrierung](../enrollment/windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number--2595788---"></a>Suchen nach dem Autopilot-Gerät mithilfe der Seriennummer<!--2595788 -->
Sie können jetzt mithilfe der Seriennummer nach dem Autopilot-Gerät suchen. Wählen Sie zu diesem Zweck **Geräteregistrierung** > **Windows-Registrierung** > **Geräte** aus, geben Sie die Seriennummer in das Feld **Nach Seriennummer suchen** ein, und drücken Sie die EINGABETASTE.

#### <a name="track-installation-of-office-proplus--2620217---"></a>Nachverfolgen der Installation von Office ProPlus<!--2620217 -->
Benutzer können den Installationsfortschritt von [Office ProPlus](../apps/apps-add-office365.md) mithilfe der [Seite zum Registrierungsstatus](../enrollment/windows-enrollment-status.md) nachverfolgen. Weitere Informationen finden Sie unter [Einrichten einer Statusseite für die Registrierung](../enrollment/windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low---2237572---"></a>Warnungen für ablaufende VPP-Token oder Ausreizung der Unternehmensportal-Lizenz<!-- 2237572 -->
Wenn Sie das Volume Purchase Programm (VPP) zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung verwenden, warnt Intune Sie, wenn das VPP-Token vor dem Ablauf steht und die Lizenzen für das Unternehmensportal knapp werden.

#### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts--3006133---"></a>Unterstützung des Programms zur macOS-Geräteregistrierung für Apple School Manager-Konten<!--3006133 -->
Intune unterstützt jetzt die Verwendung des Programms zur Geräteregistrierung für macOS-Geräte für Apple School Manager-Konten.  Weitere Informationen finden Sie unter [Automatisches Registrieren von macOS-Geräten mit dem Programm zur Geräteregistrierung von Apple](../enrollment/device-enrollment-program-enroll-macos.md).

#### <a name="new-intune-device-subscription-sku--3312071--"></a>Neue Abonnement-SKU für Intune-Geräte<!--3312071-->
Eine neue gerätebasierte Abonnement-SKU ist nun verfügbar, mit der die Kosten für die Geräteverwaltung in Unternehmen reduziert werden können. Diese SKU für Intune-Geräte wird monatlich pro Gerät lizenziert. Der Preis hängt vom Lizenzierungsprogramm ab. Dieses ist direkt im Microsoft 365 Admin Center sowie über das [Enterprise Agreement](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA), das [Microsoft Products and Services Agreement](https://www.microsoft.com/licensing/mpsa/default) (MPSA), [Microsoft Open Agreements](https://partner.microsoft.com/licensing/licensing-agreements) und [Cloud Solution Provider](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP) verfügbar.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes---3041935---"></a>Temporäres Anhalten des Kioskmodus auf Android-Geräten zum Durchführen von Änderungen<!-- 3041935 -->
Bei Verwendung von Android-Geräten im Multi-App-Kioskmodus kann es erforderlich werden, dass ein IT-Administrator Änderungen am Gerät vornimmt. Dieses Update beinhaltet eine neue Multi-App-Kioskeinstellung, die dem IT-Administrator erlaubt, den Kioskmodus unter Verwendung einer PIN temporär anzuhalten und Zugriff auf das gesamte Gerät zu erhalten.
Informationen zu den Kioskeinstellungen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android Enterprise](../configuration/device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices----3042021---"></a>Aktivieren einer virtuellen Startschaltfläche auf Android Enterprise-Kioskgeräten <!-- 3042021 -->
Eine neue Einstellung erlaubt es den Benutzern, auf ihrem Gerät auf einen Softkey zu tippen, um auf ihrem Multi-App-Kioskgerät zwischen der Managed Home Screen-App und anderen zugewiesenen Apps zu wechseln. Diese Einstellung ist insbesondere dann nützlich, wenn eine Kiosk-App des Benutzers nicht ordnungsgemäß auf die ZURÜCK-Taste reagiert. Sie können diese Einstellung für unternehmenseigene, einzeln genutzte Android-Geräte konfigurieren. Wechseln Sie im Azure-Portal zu Intune und anschließend zur Gerätekonfiguration, um die Einstellung **Virtuelle Startschaltfläche** zu aktivieren oder zu deaktivieren. Wählen Sie ein aktuelles Gerätekonfigurationsprofil aus, oder erstellen Sie ein neues Profil, um die zugehörigen Kioskeinstellungen zu bearbeiten.
Informationen zu den Kioskeinstellungen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android Enterprise](../configuration/device-restrictions-android-for-work.md).




<!-- ########################## -->
## <a name="october-2018"></a>Oktober 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="access-to-key-profile-properties-using-the-company-portal-app---772203---"></a>Zugriff auf wichtige Profileigenschaften über die Unternehmensportal-App<!-- 772203 -->
Endbenutzer können ab jetzt auf wichtige Eigenschaften und Aktionen über die Unternehmensportal-App zugreifen, z.B. die Kennwortzurücksetzung. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios---1248481---"></a>Sperren von Drittanbietertastaturen auf iOS-Geräten mithilfe der App-Einstellungen<!-- 1248481 -->
Intune-Administratoren können auf iOS-Geräten beim Zugriff auf Organisationsdaten, die in durch Richtlinien geschützten Apps hinterlegt sind, Tastaturen von Drittanbietern sperren. Wenn die Anwendungsschutzrichtlinie (Application Protection Policy, APP) zur Sperrung von Drittanbietertastaturen konfiguriert ist, wird dem Gerätebenutzer eine Nachricht angezeigt, wenn dieser zum ersten Mal mit einer solchen Tastatur auf Unternehmensdaten zugreifen möchte. Dabei wird dem Benutzer nur die native Tastatur angezeigt. Alle anderen Tastaturen werden gesperrt und sind nicht sichtbar. Die Dialogmeldung wird dem Gerätebenutzer nur einmal angezeigt. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices---1248496---"></a>Benutzerkontozugriff von Intune-Apps auf verwalteten Android- und iOS-Geräten<!-- 1248496 -->
Wie der Microsoft Intune-Administrator können Sie steuern, welche Benutzerkonten Microsoft Office-Anwendungen auf verwalteten Geräten hinzugefügt werden. Sie können den Zugriff auf zulässige Organisationsbenutzerkonten beschränken und persönliche Konten auf registrierten Geräten blockieren. 

#### <a name="outlook-ios-and-android-app-configuration-policy--1828527---"></a>Konfigurationsrichtlinie für die Outlook-App für iOS und Android<!--1828527 -->
Ab sofort können Sie für lokale Benutzer, die die grundlegende Authentifizierung mit dem ActiveSync-Protokoll nutzen, eine Konfigurationsrichtlinie für die Outlook-App für iOS und Android erstellen. Zusätzliche Konfigurationseinstellungen werden hinzugefügt, sobald sie für Outlook für iOS und Android aktiviert werden.

#### <a name="office-365-pro-plus-language-packs---1833450---"></a>Office 365 ProPlus-Sprachpakete<!-- 1833450 -->
Als Intune-Administrator können Sie zukünftig zusätzliche Sprachen für Office 365 Pro Plus-Apps bereitstellen, die über Intune verwaltet werden. In der Liste der verfügbaren Sprachpakete ist auch der **Typ** der Sprachpakete angegeben (grundlegende Sprachunterstützung, Sprache teilweise unterstützt und Sprachkorrekturhilfen). Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie auf dem Blatt **App hinzufügen** in der Liste **App-Typ** unter **Office 365 Suite** den Eintrag **Windows 10** aus. Klicken Sie auf dem Blatt **Einstellungen der App-Suite** auf **Sprachen**.

#### <a name="windows-line-of-business-lob-apps-file-extensions---1884873---"></a>Erweiterung für Dateien von branchenspezifischen Windows-Apps (LOB-Apps)<!-- 1884873 -->
Die Dateierweiterungen für Windows-LOB-Apps umfassen jetzt *.msi*, *.appx*, *.appxbundle*, *.msix* und *.msixbundle*. Sie können eine App in Microsoft Intune hinzufügen, indem Sie **Client-Apps** > **Apps** > **Hinzufügen** auswählen. Der Bereich **App hinzufügen** wird geöffnet. Dort können Sie den **App-Typ** auswählen. Wählen Sie für Windows-LOB-Apps **Branchenspezifische App** als App-Typ aus, wählen Sie **App-Paketdatei** aus, und geben Sie dann eine Installationsdatei mit der entsprechenden Erweiterung ein.

#### <a name="windows-10-app-deployment-using-intune---2309001---"></a>Windows 10-App-Bereitstellung mit Intune<!-- 2309001 -->
Basierend auf der bestehenden Unterstützung für Branchenanwendungen (LOB) und Microsoft Store for Business-Apps können Administratoren mit Intune die meisten der vorhandenen Anwendungen ihres Unternehmens für Endbenutzer auf Windows 10-Geräten bereitstellen. Administratoren können Anwendungen für Windows 10-Benutzer in einer Vielzahl von Formaten wie MSI, Setup.exe oder MSP hinzufügen, installieren und deinstallieren. Intune wertet vor dem Herunterladen und Installieren, dem Benachrichtigen von Endbenutzern über den Status oder Neustartanforderungen die Anforderungsregeln über das Info-Center von Windows 10 aus. Diese Funktionalität wird Unternehmen, die daran interessiert sind, diesen Workload auf Intune und die Cloud zu verlagern, effektiv entlasten. Dieses Feature befindet sich derzeit in der öffentlichen Vorschauversion und wir erwarten, dass es in den nächsten Monaten um bedeutende neue Funktionen erweitert wird. 

#### <a name="app-protection-policy-app-settings-for-web-data---2662995---"></a>App-Schutzrichtlinieneinstellungen für Webdaten<!-- 2662995 -->
App-Richtlinieneinstellungen für Webinhalte auf Android- und iOS-Geräten werden aktualisiert, um sowohl HTTP- und HTTPS-Weblinks als auch Datenübertragungen über universelle iOS-Links und Android-App-Links besser zu verarbeiten. 

#### <a name="end-user-device-and-app-content-menu---2771453---"></a>Endbenutzergerät und App-Inhaltsmenü<!-- 2771453 -->
Endbenutzer können nun das Kontextmenü für Geräte und Apps verwenden, um häufig verwendete Aktionen auszulösen, z.B. das Umbenennen eines Geräts oder die Überprüfung der Konformität. 

#### <a name="windows-company-portal-keyboard-shortcuts---2771518---"></a>Tastenkombinationen für die Windows-Unternehmensportal-App<!-- 2771518 -->
Endbenutzer können ab sofort mithilfe von Tastenkombinationen (Tastenkombinations-Editor) App- und Geräteaktionen in der Windows-Unternehmensportal-App auslösen.

#### <a name="require-non-biometric-pin-after-a-specified-timeout---1506985---"></a>Anfordern der nicht biometrischen PIN nach festgelegtem Timeout<!-- 1506985 -->
Durch die erzwungene Verwendung einer nicht biometrischen PIN nach einem vom Administrator festgelegten Zeitraum wird die Sicherheit von MAM-fähigen Apps (Mobile Application Management, Verwaltung mobiler Anwendungen) durch Intune erhöht, indem die Nutzung einer biometrischen Kennung für den Zugriff auf Unternehmensdaten beschränkt wird. Die Einstellungen betreffen Benutzer, die Touch ID (iOS), Face ID (iOS), Android Biometric oder andere biometrische Authentifizierungsmethoden für den Zugriff auf ihre APP-/MAM-fähigen Anwendungen verwenden. Intune-Administratoren bieten die Einstellungen mehr Kontrolle über den Benutzerzugriff. So können Szenarios vermieden werden, in denen ein Gerät, für das mehrere Fingerabdrücke oder andere biometrische Zugriffsmethoden verwendet werden, dem falschen Benutzer Zugriff auf Unternehmensdaten gestattet. Öffnen Sie im Azure-Portal **Microsoft Intune**. Klicken Sie auf **Client-Apps** > **App-Schutzrichtlinien** > **Richtlinie hinzufügen** > **Einstellungen**. Im Abschnitt **Zugriff** können Sie die entsprechenden Einstellungen vornehmen. Weitere Informationen zu den Zugriffseinstellungen finden Sie unter [iOS-Einstellungen](../apps/app-protection-policy-settings-ios.md#access-requirements) und [Android-Einstellungen](../apps/app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices---2244713---"></a>Intune-App-Datenübertragungseinstellungen auf iOS-MDM-registrierten Geräten<!-- 2244713 -->
Sie können die Steuerung der Intune-App-Datenübertragungseinstellungen auf iOS-MDM-registrierten Geräten von der Angabe der Identität des registrierten Benutzers (auch als Benutzerprinzipalname (UPN) bekannt) trennen. Administratoren, die IntuneMAMUPN nicht verwenden, werden keine Verhaltensänderung feststellen. Wenn diese Funktion verfügbar ist, sollten Administratoren, die mit IntuneMAMUPN das Datenübertragungsverhalten auf registrierten Geräten steuern, die neuen Einstellungen überprüfen und ihre APP-Einstellungen nach Bedarf aktualisieren.

#### <a name="windows-10-win32-apps---2617325---"></a>Windows 10-Win32-Apps<!-- 2617325 -->
Sie können die Win32-Apps kontextbezogen für einzelne Benutzer konfigurieren, anstatt die App für alle Benutzer des Geräts zu installieren.

#### <a name="windows-win32-apps-and-powershell-scripts---2617330---"></a>Windows-Win32-Apps und PowerShell-Skripts<!-- 2617330 -->
Endbenutzer müssen nicht mehr beim Gerät angemeldet sein, um Win32-Apps zu installieren und PowerShell-Skripts auszuführen. 

#### <a name="troubleshooting-client-app-installation---1363711---"></a>Problembehandlung bei der Installation von Client-Apps<!-- 1363711 -->
Sehen Sie sich im Blatt **Problembehandlung** die Spalte **App-Installation** an, um bei Problemen Client-Apps erfolgreich zu installieren. Um das Blatt **Problembehandlung** anzuzeigen, wählen Sie im Intune-Portal unter **Hilfe und Support** die Option **Problembehandlung**.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Erstellen von DNS-Suffixen in VPN-Konfigurationsprofilen auf Geräten mit Windows 10<!-- 1333668 -->
Beim Erstellen eines VPN-Gerätekonfigurationsprofils (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **Windows 10 und höher** Plattform > **VPN**-Profiltyp) geben Sie DNS-Einstellungen ein. Mit diesem Update können Sie auch mehrere **DNS-Suffixe** in Intune eingeben. Wenn Sie DNS-Suffixe verwenden, können Sie nach einer Netzwerkressource mithilfe ihres Kurznamens anstelle des vollqualifizierten Domänennamens (Fully Qualified Domain Name, FQDN) suchen. Mit diesem Update können Sie auch die Reihenfolge der DNS-Suffixe in Intune ändern.
In [VPN-Einstellungen für Windows 10](../configuration/vpn-settings-windows-10.md#dns-settings) sind die aktuellen DNS-Einstellungen aufgeführt.
Gilt für: Windows 10-Geräte

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles---1333705---"></a>Unterstützung für Always On-VPN für Android-Enterprise-Arbeitsprofile<!-- 1333705 -->
In diesem Update können Sie Always On-VPN-Verbindungen auf Android Enterprise-Geräten mit verwalteten Arbeitsprofilen verwenden. Always On-VPN-Verbindungen bleiben erhalten oder werden sofort wieder hergestellt, wenn der Benutzer sein Gerät entsperrt, wenn das Gerät neu gestartet wird oder das drahtlose Netzwerk sich ändert. Sie können die Verbindung auch in den „Sperrmodus“ setzen, der den gesamten Netzwerkdatenverkehr blockiert, bis die VPN-Verbindung aktiv ist.
Sie können Always On-VPN in **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** für Plattform > **Geräteeinschränkungen** > **Konnektivitätseinstellungen** aktivieren.

#### <a name="issue-scep-certificates-to-user-less-devices---1744554---"></a>Ausstellen von SCEP-Zertifikaten für Geräte ohne Benutzer<!-- 1744554 -->
Derzeit werden Zertifikate an Benutzer ausgegeben. Mit diesem Update können SCEP-Zertifikate für Geräte ausgestellt werden, einschließlich benutzerloser Geräte wie Kioske (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** für Plattform > **SCEP-Zertifikat** für Profil). Weitere Updates enthalten:
- Die **Betreff**-Eigenschaft in einem SCEP-Profil ist nun ein benutzerdefiniertes Textfeld und kann neue Variablen enthalten. 
- Die **Alternativer Antragstellername**-Eigenschaft (Subject Alternative Name, SAN) in einem SCEP-Profil ist nun ein Tabellenformat und kann neue Variablen enthalten. In der Tabelle kann ein Administrator ein Attribut hinzufügen und den Wert in einem benutzerdefinierten Textfeld ausfüllen. Der SAN unterstützt die folgenden Attribute: 
  - DNS
  - E-Mail-Adresse
  - UPN

  Diese neuen Variablen können mit statischem Text in einem benutzerdefinierten Werttextfeld hinzugefügt werden. Beispielsweise kann das DNS-Attribut als `DNS = {{AzureADDeviceId}}.domain.com` hinzugefügt werden.

  > [!NOTE]
  > Geschweifte Klammern, Semikolons und Pipesymbole „{}; |“ funktionieren nicht im statischen SAN-Text. Geschweifte Klammern dürfen nur eine der neuen Gerätezertifikatvariablen umschließen, die entweder für `Subject` oder `Subject alternative name` akzeptiert werden. 

Neue Gerätezertifikatvariablen:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
> - `{{FullyQualifiedDomainName}}` funktioniert nur für Windows und in die Domäne eingebundene Geräte. 
> - Bei der Angabe von Geräteeigenschaften wie IMEI, Seriennummer und vollständig qualifiziertem Domänennamen im Betreff oder SAN für ein Gerätezertifikat achten Sie unbedingt darauf, dass diese Eigenschaften von einer Person mit Zugriff auf das Gerät gespooft sein könnten. 

[SCEP-Zertifikatprofil erstellen](../protect/certificates-profile-scep.md#create-a-scep-certificate-profile) listet beim Erstellen eines SCEP-Konfigurationsprofils die aktuellen Variablen auf. 

Gilt für: Windows 10 und höher sowie iOS, für WLAN unterstützt

#### <a name="remotely-lock-uncompliant-devices---2064495---"></a>Remotesperren nicht konformer Geräte<!-- 2064495 -->
Wenn ein Gerät nicht konform ist, können Sie eine Aktion in der Konformitätsrichtlinie erstellen, die das Gerät remote sperrt. Erstellen Sie in Intune > **Gerätekonformität** eine neue Richtlinie, oder wählen Sie eine vorhandene Richtlinie > **Eigenschaften** aus. Wählen Sie **Aktionen bei Inkompatibilität** > **Hinzufügen** und dann das Remotesperren des Geräts aus.
Unterstützt auf: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 und höher 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal---2748224---"></a>Verbesserungen des Kioskprofils im Azure-Portal für Windows 10 und höher<!-- 2748224 -->
Dieses Update umfasst die folgenden Verbesserungen am Windows 10-Kiosk-Gerätekonfigurationsprofil (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **Windows 10 und höher** für Plattform > **Kioskvorschau** für Profiltyp): 
- Derzeit können Sie mehrere Kioskprofile auf demselben Gerät erstellen. Ab diesem Update unterstützt Intune nur ein Kioskprofil pro Gerät. Wenn Sie noch mehrere Kioskprofile auf einem einzelnen Gerät benötigen, können Sie einen benutzerdefinierten URI verwenden.
- In einem **Multi-App-Kioskprofil** können Sie die Anwendungskachelgröße und Reihenfolge für das **Startmenülayout** im Raster der Anwendung auswählen. Wenn Sie eine umfassendere Anpassung bevorzugen, können Sie weiterhin eine XML-Datei hochladen.
- Die Kioskbrowsereinstellungen werden in die **Kiosk**-Einstellungen verschoben. Derzeit haben die **Kioskwebbrowser**-Einstellungen ihre eigene Kategorie im Azure-Portal.
Gilt für: Windows 10 und höher

#### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device----2637704----"></a>PIN-Eingabeaufforderung beim Ändern von Fingerabdrücken oder der Gesichts-ID auf einem iOS-Gerät <!-- 2637704  -->
Benutzer werden jetzt zur Eingabe einer PIN aufgefordert, nachdem sie Änderungen an biometrischen Daten auf ihrem iOS-Gerät vorgenommen haben. Hierzu zählen Änderungen an registrierten Fingerabdrücken oder Gesichts-IDs. Die Zeitplanung für die Aufforderung hängt von der Konfiguration des Timeouts *Zugriffsanforderungen erneut prüfen nach (Minuten)* ab.  Wenn keine PIN festgelegt ist, wird der Benutzer aufgefordert, eine festzulegen. 
 
Dieses Feature ist nur für iOS verfügbar und erfordert, dass das Intune App SDK für iOS, Version 9.0.1 oder höher in betreffende Anwendungen integriert wird. Die Integration des SDK ist erforderlich, damit das Verhalten für die Zielanwendungen erzwungen werden kann. Diese Integration erfolgt kontinuierlich und ist abhängig von den jeweiligen Anwendungsteams. Zu den betreffenden Apps zählen z.B. WXP, Outlook, Managed Browser und Yammer.

#### <a name="network-access-control-support-on-ios-vpn-clients---1333693---"></a>Unterstützung der Netzwerkzugriffssteuerung auf iOS-VPN-Clients<!-- 1333693 -->
Mit diesem Update gibt es eine neue Einstellung zum Aktivieren der Netzwerkzugriffssteuerung (Network Access Control, NAC), wenn Sie ein VPN-Konfigurationsprofil für Cisco AnyConnect, F5 Access und Citrix SSO für iOS erstellen. Über diese Einstellung kann die NAC-ID des Geräts in das VPN-Profil aufgenommen werden. Derzeit gibt es keine VPN-Clients oder NAC-Partnerlösungen, die diese neue NAC-ID unterstützen, aber wir werden Sie über unseren [Supportblogbeitrag](ttps://aka.ms/iOS12_and_vpn) auf dem Laufenden halten.

Zur Nutzung der Netzwerkzugriffssteuerung ist Folgendes erforderlich:
1. Aktivieren Sie diese Option, damit Intune Geräte-IDs in VPN-Profile aufnehmen kann.
2. Aktualisieren Sie Ihre NAC-Anbietersoftware bzw. -Firmware entsprechend der Anleitungen direkt von Ihrem NAC-Anbieter.

Informationen zu dieser Einstellung innerhalb eines iOS-VPN-Profils finden Sie unter [Konfigurieren von VPN-Einstellungen für iOS-Geräte in Microsoft Intune](../configuration/vpn-settings-ios.md). Weitere Informationen zur Netzwerkzugriffssteuerung finden Sie unter [Integrieren der Netzwerkzugriffssteuerung (NAC) mit Intune](../protect/network-access-control-integrate.md). 

Gilt für: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile---1818139---"></a>Entfernen eines E-Mail-Profils von einem Gerät, wenn nur ein solches Profil vorhanden ist<!-- 1818139 -->
Zuvor konnte ein E-Mail-Profil nicht von einem Gerät entfernt werden, *wenn* es das einzige E-Mail-Profil war. Dies wurde mit dem vorliegenden Update geändert. Nun können Sie ein E-Mail-Profil entfernen, auch wenn es das einzige E-Mail-Profil auf dem Gerät ist. Weitere Informationen finden Sie unter [Konfigurieren von E-Mail-Einstellungen in Microsoft Intune](../configuration/email-settings-configure.md).

#### <a name="powershell-scripts-and-aad---2309469---"></a>PowerShell-Skripts und AAD<!-- 2309469 -->
PowerShell-Skripts in Intune können auf AAD-Gerätesicherheitsgruppen ausgerichtet werden.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Neue Standardeinstellung „Erforderlicher Kennworttyp“ für Android und Android Enterprise<!-- 2649963 -->
Wenn Sie eine neue Konformitätsrichtlinie erstellen (**Intune** > **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Android** oder **Android Enterprise** für Plattform > Systemsicherheit), ändert sich der Standardwert für **Erforderlicher Kennworttyp**:

Von: Standardeinstellung für das Gerät – In: Mindestens numerisch

Gilt für: Android, Android Enterprise

Um diese Einstellungen anzuzeigen, wechseln Sie zu [Android](../protect/compliance-policy-create-android.md) bzw. [Android Enterprise](../protect/compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile---2662938---"></a>Verwenden eines vorinstallierten Schlüssels in einem Windows 10-WLAN-Profil<!-- 2662938 -->
Mit diesem Update können Sie einen vorinstallierten Schlüssel (Pre-Shared Key, PSK) mit dem WPA/WPA2-Personal-Sicherheitsprotokoll verwenden, um ein WLAN-Konfigurationsprofil für Windows 10 zu authentifizieren. Sie können auch die Kostenkonfiguration für ein getaktetes Netzwerk für Geräte unter Windows 10 mit dem Update von Oktober 2018 angeben.

Derzeit müssen Sie ein WLAN-Profil importieren oder ein benutzerdefiniertes Profil erstellen, um einen vorinstallierten Schlüssel zu verwenden. [WLAN-Einstellungen für Geräte mit Windows 10 und höher in Intune](../configuration/wi-fi-settings-windows.md) werden die aktuellen Einstellungen aufgeführt. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices---3218390---"></a>Entfernen von PKCS- und SCEP-Zertifikaten von Ihren Geräten<!-- 3218390 -->
In einigen Szenarios waren PKCS- und SCEP-Zertifikate weiterhin auf Geräten vorhanden, auch wenn eine Richtlinie aus einer Gruppe entfernt, eine Konfiguration oder eine Konformitätsbereitstellung gelöscht wurde oder ein Administrator ein vorhandenes SCEP- oder PKCS-Profil aktualisiert hat. Dies wurde mit dem vorliegenden Update geändert. In einigen Szenarios werden PKCS- und SCEP-Zertifikate von Geräten entfernt, in anderen verbleiben diese Zertifikat auf dem Gerät. Einen Überblick über diese Szenarios finden Sie unter [Remove SCEP and PKCS certificates in Microsoft Intune (Entfernen von SCEP- und PKCS-Zertifikaten in Microsoft Intune)](../protect/remove-certificates.md).

#### <a name="use-gatekeeper-on-macos-devices-for-compliance---2504381---"></a>Verwenden von Gatekeeper auf macOS-Geräten für Konformität<!-- 2504381 -->
Dieses Update beinhaltet die macOS-Gatekeeper-Anwendung, um Geräte auf Konformität zu prüfen. Um die Gatekeeper-Eigenschaft festzulegen, [fügen Sie eine Gerätekonformitätsrichtlinie für macOS-Geräte hinzu](../protect/compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot---1558983---"></a>Anwenden des Autopilot-Profils auf Win 10-Geräte, die noch nicht für Autopilot registriert sind<!-- 1558983 -->
Sie können Autopilot-Profile auf registrierte Win 10-Geräte anwenden, die noch nicht für Autopilot registriert sind. Wählen Sie im Autopilot-Profil die Option **Alle Zielgeräte in Autopilot-Geräte konvertieren** aus, um Nicht-Autopilot-Geräte automatisch mit dem Autopilot-Bereitstellungsdienst zu registrieren. Die Verarbeitung der Registrierung kann 48 Stunden dauern. Wenn die Registrierung des Geräts aufgehoben und es zurückgesetzt ist, stellt Autopilot es bereit.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups---2526564---"></a>Erstellen und Zuweisen mehrerer Profile für Registrierungsstatusseiten für Azure AD-Gruppen<!-- 2526564 -->
Sie haben jetzt folgende Möglichkeit: [Erstellen und Zuweisen](../enrollment/windows-enrollment-status.md) mehrerer Registrierungsstatus-Seitenprofile für Azure ADD-Gruppen.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune--2748613--"></a>Migration vom Programm zur Geräteregistrierung zum Apple Business Manager in Intune<!--2748613-->
Der Apple Business Manager (ABM) ist mit Intune konform, und Sie können ein Upgrade für Ihr Konto vom Programm zur Geräteregistrierung (Device Enrollment Program, DEP) zum ABM durchführen. Der Prozess in Intune ist identisch. Wenn Sie ein Upgrade für Ihr Apple-Konto vom DEP zum ABM durchführen möchten, rufen Sie [https://support.apple.com/HT208817]( https://support.apple.com/HT208817) auf.

#### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page--2748656--"></a>Registerkarten für Warnungen und Registrierungsstatus auf der Übersichtsseite der Geräteregistrierung<!--2748656-->
Warnungs- und Registrierungsfehler werden jetzt auf separaten Registerkarten auf der Übersichtsseite für die Geräteregistrierung angezeigt.

#### <a name="enrollment-abandonment-report---1382924---"></a>Bericht zum Registrierungsabbruch<!-- 1382924 -->
Ein neuer Bericht, der Details zu abgebrochenen Registrierungen enthält, ist unter **Geräteregistrierung** > **Überwachen** verfügbar. Weitere Informationen finden Sie unter [Abbruchbericht des Unternehmensportals](../enrollment/enrollment-report-company-portal-abandon.md).

#### <a name="new-azure-active-directory-terms-of-use-feature---2870393---"></a>Neues Feature zu Azure Active Directory-Nutzungsbedingungen<!-- 2870393 -->
Azure Active Directory verfügt über ein Feature für Nutzungsbedingungen, das Sie anstelle der bestehenden Intune-Nutzungsbedingungen verwenden können. Die Azure AD Nutzungsbedingungen bieten mehr Flexibilität bei der Anzeige von Bedingungen (Umfang und Zeitpunkt), eine bessere Lokalisierungsunterstützung, mehr Kontrolle über die Darstellung von Nutzungsbedingungen und eine verbesserte Berichterstellung. Die Azure AD-Nutzungsbedingungen erfordern Azure Active Directory Premium P1, das ebenfalls Teil der Enterprise Mobility + Security E3 Suite ist. Weitere Informationen finden Sie im Artikel [Verwalten der Geschäftsbedingungen Ihres Unternehmens für den Benutzerzugriff](../enrollment/terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support--3188762--"></a>Unterstützung des Modus für Android-Gerätebesitzer<!--3188762-->
Für die Samsung Knox Mobile-Registrierung unterstützt Intune jetzt die Registrierung von Geräten im Verwaltungsmodus für Android-Geräteeigentümer. Benutzer mit einer WLAN- oder Mobilfunknetzverbindung können die Registrierung mit nur wenigen Tippbewegungen ausführen, wenn sie ihre Geräte zum ersten Mal einschalten. Weitere Informationen finden Sie unter [Automatisches Registrieren von Android-Geräten mit Samsung Knox Mobile Enrollment](../enrollment/android-samsung-knox-mobile-enroll.md).

### <a name="device-management"></a>Geräteverwaltung
#### <a name="new-settings-for-software-updates-----1907869---"></a>Neue Einstellungen für Softwareupdates  <!-- 1907869 -->  
- Sie können jetzt einige Benachrichtigungen konfigurieren, um Endbenutzer vor Neustarts zu warnen, die erforderlich sind, um die Installation der neuesten Softwareupdates abzuschließen.   
- Sie können jetzt eine Warnmeldung für Neustarts konfigurieren, die außerhalb der Arbeitszeit stattfinden, wodurch BYOD-Szenarios unterstützt werden.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id---2075110---"></a>Gruppieren von mit Windows Autopilot registrierten Geräten nach Korrelator-ID<!-- 2075110 -->
Intune unterstützt nun die Gruppierung von Windows-Geräten nach einer Korrelator-ID, wenn sie mit [Autopilot für bestehende Geräte](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) über den Configuration Manager registriert werden. Die Korrelator-ID ist ein Parameter der Autopilot-Konfigurationsdatei. Intune legt das [Azure AD-Geräteattribut „enrollmentProfileName“](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) automatisch auf „OfflineAutopilotprofile-<correlator ID>“ fest. Dadurch können beliebige dynamische Azure AD-Gruppen basierend auf der Korrelator-ID über das Attribut „enrollmentprofileName“ für Offlineregistrierungen von Autopilot erstellt werden. Weitere Informationen finden Sie unter [Windows Autopilot für vorhandene Geräte](../enrollment/enrollment-autopilot.md#windows-autopilot-for-existing-devices).

#### <a name="intune-app-protection-policies---2984657---"></a>Intune-App-Schutzrichtlinien<!-- 2984657 -->
Mithilfe von Intune-App-Schutzrichtlinien können Sie verschiedene Einstellungen zum Schutz von Daten für mit Intune geschützte Apps konfigurieren, zum Beispiel Microsoft Outlook und Microsoft Word. Aussehen und Verhalten dieser Einstellungen wurden sowohl für [iOS](../apps/app-protection-policy-settings-ios.md) als auch für [Android](../apps/app-protection-policy-settings-android.md) geändert, um das Auffinden individueller Einstellungen zu erleichtern. Es gibt drei Kategorien von Richtlinieneinstellungen:
- **Datenverschiebung**: Diese Gruppe umfasst Steuerelemente zum Verhindern von Datenverlust, wie z.B. Einschränkungen für Ausschneiden, Kopieren, Einfügen und „Speichern unter“. Diese Einstellungen bestimmen, wie Benutzer mit Daten in den Apps interagieren können.
- **Zugriffsanforderungen**: Diese Gruppe enthält die PIN-Optionen pro App. Sie bestimmen, wie der Endbenutzer in einem Arbeitskontext auf die Apps zugreifen kann.  
- **Bedingter Start**: Diese Gruppe enthält Einstellungen wie z.B. die mindestens erforderliche Betriebssystemversion, Einstellungen zur Erkennung von Jailbreak und entfernten Nutzungsbeschränkungen und die Offlinetoleranzperiode.  
  
Die Funktionalität der Einstellungen ändert sich nicht, aber es wird einfacher sein, sie bei der Richtlinienerstellung zu finden.

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices---2451462----"></a>Einschränken von Apps und Blockieren des Zugriffs auf Unternehmensressourcen auf Android-Geräten<!-- 2451462  -->  
In **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Android** > **Systemsicherheit** gibt es eine neue Einstellung unter dem Abschnitt *Gerätesicherheit* namens **Eingeschränkte Apps**. Die Einstellung **Eingeschränkte Apps** verwendet eine Konformitätsrichtlinie, um den Zugriff auf Unternehmensressourcen zu blockieren, wenn bestimmte Apps auf dem Gerät erstellt werden. Das Gerät wird so lange als nicht kompatibel betrachtet, bis die eingeschränkten Apps von diesem Gerät entfernt werden.
Gilt für: 
- Android

### <a name="intune-apps"></a>Intune-Apps

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps---1727158---"></a>Intune-Unterstützung für eine maximale Paketgröße von 8 GB für LOB-Anwendungen<!-- 1727158 -->
Intune erhöht die maximale Paketgröße auf 8 GB für LOB-Anwendungen. Weitere Informationen finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](../apps/apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app---1916266---"></a>Hinzufügen eines benutzerdefinierten Markenbilds für die Unternehmensportal-App<!-- 1916266 -->
Als Microsoft Intune-Administrator können Sie ein benutzerdefiniertes Markenbild hochladen, das als Hintergrundbild auf der Profilseite des Benutzers in der iOS-Unternehmensportal-App angezeigt wird. Weitere Informationen zum Konfigurieren der Unternehmensportal-App finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](../apps/company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines---2971030---"></a>Intune behält die lokalisierte Sprache für Office bei, wenn Office auf den Computern der Endbenutzer aktualisiert wird<!-- 2971030 -->
Wenn Intune Office auf den Computern Ihrer Endbenutzer installiert, erhalten sie automatisch dieselben Sprachpakete wie bei früheren MSI-Office-Installationen. Weitere Informationen finden Sie unter [Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune](../apps/apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal---3076965---"></a>Neue Benutzeroberfläche für Intune-Support im Portal für die Microsoft 365-Geräteverwaltung<!-- 3076965 -->
Im [Portal für die Microsoft 365-Geräteverwaltung]( https://devicemanagement.microsoft.com) wird eine neue Benutzeroberfläche für „Hilfe und Support“ in Intune eingeführt. Über die neue Benutzeroberfläche können Sie Ihr Problem in eigenen Worten beschreiben und erhalten Einblicke in die Problembehandlung sowie webbasierte Anleitungen zur Selbsthilfe. Diese Lösungen werden über einen regelbasierten Algorithmus für maschinelles Lernen angeboten, der auf Benutzeranfragen basiert.  

Zusätzlich zur themenspezifischen Anleitung können Sie auch den neuen Workflow zur Fallerstellung nutzen, um einen Supportfall per E-Mail oder Telefon zu öffnen.  

Für Kunden, die am Rollout teilnehmen, ersetzt diese neue Benutzeroberfläche die aktuelle Ansicht für Hilfe und Support, die einen statischen Satz an vorab ausgewählten Optionen enthält. Diese basieren auf dem Bereich der Konsole, in dem Sie sich befinden, wenn Sie „Hilfe und Support“ öffnen.  

*Diese neue Benutzeroberfläche für Hilfe und Support steht derzeit ausgewählten Mandanten über das Portal für die Geräteverwaltung zur Verfügung. Die Teilnehmer für diese neue Benutzeroberfläche werden nach dem Zufallsprinzip aus den verfügbaren Intune-Mandanten ausgewählt. Neue Mandanten werden bei Erweiterung des Rollouts hinzukommen.*  

Weitere Informationen finden Sie in „Anfordern von Support für Microsoft Intune“ unter [Neue Benutzeroberfläche für Hilfe und Support](get-support.md#help-and-support-experience).  

#### <a name="powershell-module-for-intune--preview-available---951068---"></a>Vorschauversion für das PowerShell-Modul für Intune<!-- 951068 -->
Ein neues PowerShell-Modul, das über Microsoft Graph eine Unterstützung für die Intune-API bietet, ist nun als Vorschauversion auf [GitHub](https://aka.ms/intunepowershell) verfügbar. Weitere Informationen zur Verwendung dieses Moduls finden Sie dort unter README.

<!-- ########################## -->
## <a name="september-2018"></a>September 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="remove-duplication-of-app-protection-status-tiles---3083391---"></a>Doppelte Kacheln zum Status des App-Schutzes entfernt<!-- 3083391 -->
Die Kacheln **Benutzerstatus für iOS** und **Benutzerstatus für Android** waren sowohl auf der Seite **Client-Apps (Übersicht)** als auch auf der Seite **Client-Apps > Status des App-Schutzes** vorhanden. Die Statuskacheln wurden von der Seite **Client-Apps (Übersicht)** entfernt, um das doppelte Vorhandensein zu vermeiden. 

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="support-for-more-third-party-certification-authorities-ca---3093107---"></a>Unterstützung für mehr Drittanbieterzertifizierungsstellen<!-- 3093107 -->
Mit dem Simple Certificate Enrollment-Protokoll (SCEP) können Sie jetzt neue Zertifikate auf mobilen Geräten mit Windows, iOS, Android und macOS ausstellen und vorhandene Zertifikate verlängern.

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="intune-moves-to-support-ios-10-and-later---2454656---"></a>Intune unterstützt iOS 10 und höher<!-- 2454656 -->  
Die Intune-Registrierung, das Unternehmensportal und der verwaltete Browser unterstützen jetzt nur noch iOS-Geräte mit iOS 10 und höher. Um nach Geräten oder Benutzern zu suchen, die in Ihrem Unternehmen betroffen sind, wechseln Sie zu Intune im Azure-Portal > **Geräte** > **Alle Geräte**. Filtern Sie nach Betriebssystem und klicken Sie dann auf **Spalten**, um Details zur Betriebssystemversion anzuzeigen. Fordern Sie diese Benutzer auf, ihre Geräte auf eine unterstützte Betriebssystemversion zu aktualisieren.  

Wenn Sie über eines der unten aufgelisteten Geräte verfügen oder eines der unten aufgelisteten Geräte registrieren möchten, sollten Sie beachten, dass diese nur iOS 9 und früher unterstützen.  Wenn Sie mit diesen Geräten weiter auf das Intune-Unternehmensportal zugreifen möchten, müssen Sie für diese Geräte ein Upgrade auf Geräte mit Unterstützung für iOS 10 oder höher durchführen:  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (3. Generation) 
* iPad Mini (1. Generation)  

### <a name="device-management"></a>Geräteverwaltung

#### <a name="microsoft-365-device-management-administration-center---3078424---"></a>Admin Center für die Microsoft 365-Geräteverwaltung<!-- 3078424 -->
Microsoft 365 verspricht unkomplizierte Verwaltung. Im Laufe der Zeit wurden die Microsoft 365-Back-End-Dienste integriert, um End-to-End-Szenarios wie den bedingten Zugriff in Intune und Azure AD zu ermöglichen. Im neuen [Microsoft 365-Admin Center](https://devicemanagement.microsoft.com) können Sie Verwaltungsvorgänge vereinen, vereinfachen und integrieren. Über diesen Arbeitsbereich für die Geräteverwaltung können Sie schnell auf alle Informationen und Aufgaben zur Geräte- und App-Verwaltung zugreifen, die für Ihre Organisation relevant sind. Dieser Bereich soll der primäre Arbeitsbereich für Computingteams von geschäftliche Endbenutzer werden.


<!-- ########################## -->
## <a name="august-2018"></a>August 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types---1520957---"></a>Pakettunnelunterstützung für Pro-App-VPN-Profile für iOS für die benutzerdefinierten und Pulse Secure-Verbindungstypen<!-- 1520957 -->
Wenn Sie Pro-App-VPN-Profile für iOS verwenden, können Sie das Tunneln entweder auf App-Ebene (app-proxy) oder auf Paketebene (packet-tunnel) nutzen. Diese Optionen stehen mit den folgenden Verbindungstypen zur Verfügung:
- Benutzerdefiniertes VPN
- Pulse Secure: Wenn Sie sich nicht sicher sind, welcher Wert benutzt werden soll, sehen Sie sich die Dokumentation Ihres VPN-Anbieters an.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device---1949583---"></a>Verzögerung, wenn iOS-Softwareupdates auf dem Gerät angezeigt werden<!-- 1949583 -->
Sie können in Intune unter **Softwareupdates** > **Update policies for iOS** (Updaterichtlinien für iOS) die Tage und Uhrzeiten konfigurieren, an denen die Geräte keine Updates installieren sollen. In einem zukünftigen Update können Sie einen Zeitraum von 1 bis 90 Tagen einstellen, in dem ein Softwareupdate auf dem Gerät angezeigt wird. 
Unter [Configure iOS update policies in Microsoft Intune (Konfigurieren von iOS-Updaterichtlinien in Microsoft Intune)](../protect/software-updates-ios.md) sind die aktuellen Einstellungen aufgeführt.

#### <a name="office-365-proplus-version---2213968---"></a>Office 365 ProPlus-Version<!-- 2213968 -->
Wenn Sie Ihren Windows 10-Geräten Office 365 ProPlus-Apps über Intune hinzufügen, können Sie die Office-Version auswählen. Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Apps** > **App hinzufügen**. Wählen Sie dann in der **Typ**-Dropdownliste die Option **Office 365 ProPlus-Suite (Windows 10)** aus. Klicken Sie auf **Einstellungen der App-Suite**, um das entsprechende Blatt anzuzeigen. Legen Sie den **Updatekanal** auf einen Wert fest, z.B. **Monatlich**. Entfernen Sie optional andere Office-Versionen (msi) von den Endbenutzergeräten, indem Sie auf **Yes** (Ja) klicken. Wählen Sie **Specific** (Spezifisch) aus, um eine bestimmte Office-Version für den ausgewählten Kanal oder die Endbenutzergeräte zu installieren. Zu diesem Zeitpunkt können Sie die **spezifische Version** von Office auswählen, die verwendet werden soll. Die verfügbaren Versionen werden im Laufe der Zeit geändert. Wenn Sie eine neue Bereitstellung erstellen, können deshalb die verfügbaren Versionen aktueller sein, und bestimmte ältere Versionen sind möglicherweise nicht mehr verfügbar. Für aktuelle Bereitstellungen sind weiterhin die älteren Versionen verfügbar, jedoch wird die Liste mit den Versionen nicht ständig pro Kanal aktualisiert. Weitere Informationen finden Sie unter [Übersicht über die Updatekanäle für Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn---2282852---"></a>Unterstützung für das Registrieren von DNS-Einstellungen für Windows 10-VPN<!-- 2282852 -->
Mit diesem Update können Sie VPN-Profile für Windows 10 konfigurieren, um die IP-Adressen dynamisch zu registrieren, die der VPN-Schnittstelle mit internem DNS zugewiesen sind, ohne benutzerdefinierte Profile verwenden zu müssen.
Informationen zu den aktuell verfügbaren VPN-Profileinstellungen finden Sie unter [VPN-Einstellungen für Windows 10](../configuration/vpn-settings-windows-10.md).

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name--2652728--"></a>Im Dateinamen des Installationsprogramms für das macOS-Unternehmensportal ist nun die Versionsnummer des Installationsprogramms enthalten<!--2652728-->

#### <a name="ios-automatic-app-updates---2729759---"></a>Automatische App-Updates unter iOS<!-- 2729759 -->
Für iOS-Version 11.0 und höher können nun automatische App-Updates für Apps ausgeführt werden, die für Geräte und Benutzer lizenziert sind.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="windows-hello-will-target-users-and-devices---1106609---"></a>Windows Hello ist für Benutzer und Geräte konzipiert<!-- 1106609 -->
Wenn Sie eine [Windows Hello for Business](../protect/windows-hello.md)-Richtlinie erstellen, gilt diese für alle Benutzer innerhalb der Organisation (mandantenweit). Mit diesem Update kann die Richtlinie mithilfe einer Gerätekonfigurationsrichtlinie (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Identity Protection** > **Windows Hello for Business**) auch auf bestimmte Benutzer oder Geräte angewendet werden.
In Intune im Azure-Portal sind die Windows Hello-Konfiguration und die zugehörigen Einstellungen jetzt jeweils unter **Geräteregistrierung** und **Gerätekonfiguration** verfügbar. Die **Geräteregistrierung** ist für die gesamte Organisation (mandantenweit) konzipiert und unterstützt Windows AutoPilot (OOBE). Die **Gerätekonfiguration** ist für Geräte und Benutzer konzipiert, die eine Richtlinie verwenden, die während des Check-In angewendet wird.
Diese Funktion gilt für:  
- Windows 10 und höher
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios---1769858---"></a>Zscaler ist eine verfügbare Verbindung für VPN-Profile unter iOS<!-- 1769858 -->
Wenn Sie ein VPN-Gerätekonfigurationsprofil für iOS erstellen (unter **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS**, wechseln Sie zu Plattform und dann zum Profiltyp **VPN**), sind mehrere Verbindungstypen vorhanden, einschließlich Cisco, Citrix usw. Dieses Update wird Zscaler als Verbindungstyp hinzugefügt. 
Unter [VPN settings for devices running iOS (VPN-Einstellungen für Geräte unter iOS)](../configuration/vpn-settings-ios.md) sind die verfügbaren Verbindungstypen aufgeführt.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10---1879077---"></a>FIPS-Modus für Unternehmens-WLAN-Profile für Windows 10<!-- 1879077 -->
Sie können nun im Azure-Portal für Intune den FIPS-Modus (Federal Information Processing Standards) für Unternehmens-WLAN-Profile für Windows 10 aktivieren. Achten Sie darauf, dass der FIPS-Modus in Ihrer WLAN-Infrastruktur aktiviert ist, wenn Sie ihn in Ihren WLAN-Profilen aktiviert haben.
Im Artikel [WLAN-Einstellungen für Geräte mit Windows 10 und höher in Intune](../configuration/wi-fi-settings-windows.md) erfahren Sie, wie Sie ein WLAN-Profil erstellen können.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview---1958649---"></a>Steuern des S Modus für Geräte unter Windows 10 und höher – Public Preview<!-- 1958649 -->
Mit diesem Funktionsupdate können Sie ein Gerätekonfigurationsprofil erstellen, das den S Modus auf einem Windows 10-Gerät deaktiviert oder den Benutzer davon abhält, den S Modus eines Geräts zu deaktivieren. Dieses Feature ist in Intune verfügbar. Navigieren Sie zu **Gerätekonfiguration** > **Profile** >  **Windows 10 und höher** > **Edition upgrade and mode switch** (Editionsupgrade und Moduswechsel).
Auf der Seite [Willkommen bei Windows 10 im S Modus](https://www.microsoft.com/windows/s-mode) finden Sie weitere Informationen zum S Modus.
Gilt für: den aktuellen [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-Build (während der Vorschauversion).

#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile---2144658---"></a>Windows Defender ATP-Konfigurationspaket wird automatisch dem Konfigurationsprofil zugewiesen<!-- 2144658 -->
Wenn Sie [Advanced Threat Protection verwenden und Geräte in Intune onboarden](../protect/advanced-threat-protection.md#onboard-devices-by-using-a-configuration-profile), mussten Sie zuvor ein Konfigurationspaket herunterladen und es Ihrem Konfigurationsprofil hinzufügen. Mit diesem Update ruft Intune das Paket automatisch aus dem Windows Defender Security Center ab und fügt es Ihrem Profil hinzu.
Gilt für Windows 10 und höher.

#### <a name="require-users-to-connect-during-device-setup--2311457--"></a>Benutzer müssen während der Geräteeinrichtung eine Verbindung herstellen<!--2311457-->
Sie können nun Geräteprofile so einrichten, dass das Gerät eine Verbindung zu einem Netzwerk herstellen muss, bevor es während der Einrichtung von Windows 10 mit dem Prozess nach der Seite „Netzwerk“ fortfährt. Solange sich diese Funktion in der Vorschau befindet, ist für die Verwendung dieser Einstellung der Windows-Insider-Build 1809 oder höher erforderlich.
Gilt für: den aktuellen [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-Build (während der Vorschauversion).

#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices---2451462---"></a>Einschränken von Apps und Blockieren des Zugriffs auf Unternehmensressourcen auf iOS- und Android Enterprise-Geräten<!-- 2451462 -->
Unter **Gerätekompatibilität** > **Richtlinien** > **Richtlinie erstellen** > **iOS** > **Systemsicherheit** ist eine neue Einstellung verfügbar: **Restricted applications** (Eingeschränkte Anwendungen). Diese neue Einstellung verwendet eine Konformitätsrichtlinie, um den Zugriff auf Unternehmensressourcen zu blockieren, wenn bestimmte Apps auf dem Gerät erstellt werden. Das Gerät wird so lange als nicht kompatibel betrachtet, bis die eingeschränkten Apps von diesem Gerät entfernt werden.
Gilt für: iOS

#### <a name="modern-vpn-support-updates-for-ios---2459928-1819876-and-2650856---"></a>Updates für die Unterstützung für modernes VPN für iOS<!-- 2459928, 1819876, and 2650856 -->
Dieses Update unterstützt die folgenden iOS-VPN-Clients:
- F5 Access (Version 3.0.1 und höher)
- Citrix SSO
- Palo Alto Networks GlobalProtect (Version 5.0 und höher). Ebenso in diesem Update:
- Vorhandener **F5 Access**-Verbindungstyp wird in **F5 Access Legacy** für iOS umbenannt.
- Vorhandener **Palo Alto Networks GlobalProtect**-Verbindungstyp wird in **Palo Alto Networks GlobalProtect (legacy)** für iOS umbenannt.
Vorhandene Profile mit diesen Verbindungstypen funktionieren weiterhin mit ihren jeweiligen Legacy-VPN-Clients. Wenn Sie Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN oder Palo Alto Networks GlobalProtect-Version 4.1 oder eine ältere Version davon mit iOS verwenden, sollten Sie zu den neuen Apps wechseln. Führen Sie diesen Wechsel so früh wie möglich aus, um sicherzustellen, dass der VPN-Zugriff für iOS-Geräte zugänglich ist, sobald diese ein Update auf iOS 12 durchführen.
Weitere Informationen zu iOS 12 und VPN-Profilen finden Sie im [Blog des Supportteams für Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806).

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal---2469637---"></a>Exportieren von klassischen Azure-Portal-Konformitätsrichtlinien zur Neuerstellung dieser Richtlinien im Azure-Portal für Intune<!-- 2469637 -->
Konformitätsrichtlinien, die im klassischen Azure-Portal erstellt wurden, werden als veraltet markiert. Sie können vorhandene Konformitätsrichtlinien überprüfen und löschen, aber nicht aktualisieren. Wenn Sie Konformitätsrichtlinien zum aktuellen Azure-Portal für Intune migrieren müssen, können Sie die Richtlinien als durch Trennzeichen getrennte Datei (*CSV*-Datei) exportieren. Verwenden Sie anschließend die Informationen in der Datei, um die Richtlinien im Azure-Portal für Intune neu zu erstellen.

> [!IMPORTANT]
> Sobald das klassische Azure-Portal eingestellt wird, haben Sie keinen Zugriff mehr auf Ihre Konformitätsrichtlinien und können diese nicht mehr einsehen. Exportieren Sie Ihre Richtlinien deshalb auf jeden Fall, und erstellen Sie sie im Azure-Portal neu, bevor das klassische Azure-Portal eingestellt wird.

#### <a name="better-mobile---new-mobile-threat-defense-partner---22662717---"></a>Better Mobile: neuer Mobile Threat Defense-Partner<!-- 22662717 -->
Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen mit bedingtem Zugriff basierend auf Risikobewertungen steuern, die von Better Mobile vorgenommen werden, einer Multi Threat Defense-Lösung, die in Microsoft Intune integriert werden kann.

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in--1067692---"></a>Sperren des Unternehmensportals im Einzelanwendungsmodus, bis sich Benutzer anmelden<!--1067692 --> 
Sie haben nun die Möglichkeit, das Unternehmensportal im Einzelanwendungsmodus auszuführen, wenn Sie einen Benutzer über das Unternehmensportal statt über den Setup-Assistenten während der DEP-Registrierung authentifizieren. Durch diese Option wird das Gerät sofort nach dem Abschluss des Setup-Assistenten gesperrt, sodass sich ein Benutzer anmelden muss, um auf das Gerät zuzugreifen. Durch diese Methode wird sichergestellt, dass das Gerät den Onboardingprozess abschließt und nicht in einem verwaisten Zustand ohne verknüpften Benutzer verbleibt.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device--1346521---"></a>Zuweisen eines Benutzer- und Anzeigenamens zu einem Autopilot-Gerät<!--1346521 -->
Sie können jetzt [einen Benutzer zu einem einzelnen Autopilot-Gerät zuweisen](../enrollment/enrollment-autopilot.md). Administratoren können Anzeigenamen auch vergeben, um den Benutzer zu begrüßen, wenn dieser sein Gerät mit AutoPilot einrichtet.
Gilt für: den aktuellen [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-Build (während der Vorschauversion).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment---1608345---"></a>Verwendung von VPP-Gerätelizenzen zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung<!-- 1608345 -->
Sie können jetzt Gerätelizenzen des Volume Purchase Program (VPP) verwenden, um das Unternehmensportal während der Registrierungsvorgänge des Programms zur Geräteregistrierung (Device Enrollment Program, DEP) vorab bereitzustellen. Geben Sie dazu bei der [Erstellung oder Bearbeitung eines Registrierungsprofils](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) das VPP-Token an, das Sie zum Installieren des Unternehmensportals verwenden möchten. Stellen Sie sicher, dass Ihr Token nicht abläuft, und dass Sie über genügend Lizenzen für die Unternehmensportal-App verfügen. In Fällen, in denen das Token abläuft oder über keine Lizenzen mehr verfügt, überträgt Intune stattdessen das App Store-Unternehmensportal mithilfe von Push (dafür ist die Eingabe eine Apple-ID erforderlich).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning---2237634---"></a>Erforderliche Bestätigung zur Löschung von VPP-Token, die für die Vorabbereitstellung des Unternehmensportals verwendet werden<!-- 2237634 -->
Für die Löschung eines VPP-Tokens (Volume Purchase Program) ist jetzt eine Bestätigung notwendig, falls das Token zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung verwendet wird.

#### <a name="block-windows-personal-device-enrollments---1849498---"></a>Blockieren von Registrierungen persönlicher Windows-Geräte<!-- 1849498 -->
Sie können die Registrierung [persönlicher Windows-Geräte](../enrollment/enrollment-restrictions-set.md) mit der [mobilen Geräteverwaltung](../enrollment/windows-enroll.md) in Intune blockieren. Geräte, die mit dem [Intune-PC-Agent](../manage-windows-pcs-with-microsoft-intune.md) registriert sind, können nicht über dieses Feature blockiert werden. Dieses Feature wird in den nächsten Wochen eingeführt, sodass es nicht sofort in der Benutzeroberfläche zu finden ist.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile--1849855--"></a>Angeben von Computernamensmustern in einem Autopilot-Profil<!--1849855-->
Sie können eine [Vorlage für einen Computernamen angeben](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile), um den [Computernamen](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) während der Autopilot-Registrierung zu generieren und festzulegen. Gilt für: den aktuellen [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-Build (während der Vorschauversion).

#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page--1901669---"></a>Ausblenden der Kontoänderungsoptionen für Windows Autopilot-Profile auf der Anmeldeseite und der Domänenfehlerseite des Unternehmens<!--1901669 -->
Es gibt [neue Windows Autopilot-Profiloptionen](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile), mit denen Administratoren Kontoänderungsoptionen auf der Anmeldeseite und der Domänenfehlerseite des Unternehmens ausblenden können. Für das Ausblenden dieser Optionen muss das Unternehmensbranding in Azure Active Directory konfiguriert sein. Gilt für: den aktuellen [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-Build (während der Vorschauversion).

### <a name="macos-support-for-apple-device-enrollment-program---747651---"></a>macOS-Unterstützung für das Apple-Programm zur Geräteregistrierung<!-- 747651 -->
Intune unterstützt jetzt die Registrierung von macOS-Geräten über das Apple-Programm zur Geräteregistrierung. Weitere Informationen finden Sie unter [Automatisches Registrieren von macOS-Geräten mit dem Programm zur Geräteregistrierung von Apple](../enrollment/device-enrollment-program-enroll-macos.md).

### <a name="device-management"></a>Geräteverwaltung

#### <a name="delete-jamf-devices---2653306--"></a>Löschen von JAMF-Geräten<!-- 2653306-->
Sie können Geräte löschen, die mit JAMF verwaltet werden, indem Sie zu **Geräte** navigieren, das JAMF-Gerät auswählen und auf **Löschen** klicken.

#### <a name="change-terminology-to-retire-and-wipe---2175759---"></a>Änderung der Terminologie in „Außer Betrieb nehmen“ und „Zurücksetzen“<!-- 2175759 -->
Um Konsistenz mit der Graph-API herzustellen, wurden auf der Benutzeroberfläche und in der Dokumentation von Intune folgende Begriffe geändert:
- **Unternehmensdaten entfernen** heißt nun „Außer Betrieb nehmen“.
- **Auf Werkseinstellungen zurücksetzen** wird zu **Zurücksetzen**.

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate---297909500--"></a>Bestätigungsdialog vor dem Löschen des MDM-Push-Zertifikats durch den Administrator<!-- 297909500-->
Beim Versuch, ein Apple-MDM-Push-Zertifikat zu löschen, wird in einem Bestätigungsdialogfeld die Anzahl der zugehörigen iOS- und macOS-Geräte angezeigt. Wenn das Zertifikat gelöscht ist, müssen diese Geräte erneut registriert werden.

#### <a name="additional-security-settings-for-windows-installer---2282430---"></a>Zusätzliche Sicherheitseinstellungen für Windows Installer<!-- 2282430 -->
Sie können Benutzern erlauben, App-Installationen zu steuern. Wenn diese Option aktiviert ist, werden Installationen, die normalerweise wegen Sicherheitsverstößen unterbrochen werden würden, weiterhin ausgeführt. Sie können festlegen, dass Windows Installer bei der Installation eines beliebigen Programms auf einem System erhöhte Berechtigungen verwendet. Zusätzlich können Sie festlegen, dass Windows Information Protection-Elemente (WIP) indiziert und die zugehörigen Metadaten an einem nicht verschlüsselten Speicherort gespeichert werden. Wenn die Richtlinie deaktiviert ist, werden WIP-geschützte Elemente nicht indiziert und sie werden nicht in den Ergebnissen in Cortana oder im Datei-Explorer angezeigt. Diese Funktionalität für diese Optionen ist standardmäßig deaktiviert. 

#### <a name="new-user-experience-update-for-the-company-portal-website--2000968---"></a>Neues Update für die Benutzeroberfläche für die Unternehmensportal-Website<!--2000968 -->
Die Unternehmensportalwebsite wurde auf der Grundlage von Kundenfeedback um neue Features ergänzt. Sie werden eine erhebliche Verbesserung der vorhandenen Funktionen und Benutzerfreundlichkeit Ihrer Geräte feststellen können. Bestimmte Bereiche der Website – &ndash;z.B. Gerätedetails, Feedback und Support sowie die Geräteübersicht&ndash; – wurden mit einem neuen, modernen und dynamischen Design ausgestattet. Weiterhin sind enthalten:

- optimierte Workflows auf allen Geräteplattformen
- eine verbesserte Geräteidentifikation und optimierte Registrierungsworkflows
- aussagekräftigere Fehlermeldungen
- Benutzerfreundlichere Sprache, weniger technischer Jargon
- Möglichkeit zur Freigabe direkter Links für Apps
- Verbesserte Leistung bei großen App-Katalogen
- verbesserte Barrierefreiheit für alle Benutzer  

Die [Dokumentation zur Intune-Unternehmensportalwebsite](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) wurde entsprechend dieser Änderungen aktualisiert. Ein Beispiel für die App-Verbesserungen finden Sie unter [Updates der Benutzeroberfläche für Endbenutzer-Apps in Intune](../whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Verbesserte Erkennung von Jailbreaks in Konformitätsberichten<!-- 2198738 -->
Die Einstellungen für eine verbesserte Erkennung von Jailbreaks werden nun in allen Konformitätsberichten in der Administratorkonsole angezeigt.

### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="scope-tags-for-policies--1081974---"></a>Bereichsmarkierungen für Richtlinien<!--1081974 -->
Sie können [Bereichsmarkierungen erstellen](scope-tags.md), um den Zugriff auf Intune-Ressourcen einzuschränken. Fügen Sie einer Rollenzuweisung eine Bereichsmarkierung hinzu, und fügen Sie diese anschließend einem Konfigurationsprofil hinzu. Die Rolle hat nur Zugriff auf Ressourcen mit Konfigurationsprofilen, die über übereinstimmende Bereichsmarkierungen (oder keine Bereichsmarkierung) verfügen.





<!-- ########################## -->
## <a name="july-2018"></a>Juli 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="line-of-business-lob-app-support-for-macos---1895847---"></a>Unterstützung von branchenspezifischen Apps für macOS<!-- 1895847 -->
Mit Microsoft Intune können Sie branchenspezifische macOS-Apps als **Required** (Erforderlich) oder **Available with enrollment** (Mit Registrierung verfügbar) bereitstellen. Sie können Endbenutzern Apps als **Available** (Verfügbar) über das Unternehmensportal für macOS oder über die [Website des Unternehmensportals](https://portal.manage.microsoft.com) bereitstellen.

#### <a name="ios-built-in-app-support-for-kiosk-mode---2051098---"></a>Unterstützung von integrierten, im Kioskmodus ausführbaren iOS-Apps<!-- 2051098 -->
Zusätzlich zu Store-Apps und verwalteten Apps können Sie nun auf einem iOS-Gerät eine integrierte App (beispielsweise Safari) auswählen, die sich im Kioskmodus ausführen lässt.

#### <a name="edit-your-office-365-pro-plus-app-deployments---2150145---"></a>Bearbeiten von Office 365 Pro Plus-App-Bereitstellungen<!-- 2150145 -->
Als Microsoft Intune-Administrator haben Sie mehr Möglichkeiten, Ihre Office 365 Pro Plus-App-Bereitstellungen zu bearbeiten. Darüber hinaus müssen Sie Ihre Bereitstellungen nicht mehr löschen, um Eigenschaften der Suite zu ändern. Wählen Sie im Azure-Portal die Option **Microsoft Intune** > **Client-Apps** > **Apps** aus. Wählen Sie aus der Liste der Apps Ihre Office 365 Pro Plus-Suite aus.  

#### <a name="updated-intune-app-sdk-for-android-is-now-available---2744271--"></a>Aktualisiertes Intune App SDK für Android jetzt verfügbar<!-- 2744271-->
Zur Unterstützung der Android P-Version ist eine aktualisierte Version des Intune App SDK für Android verfügbar. Wenn Sie App-Entwickler sind und das Intune SDK für Android verwenden, müssen Sie die aktualisierte Version des Intune App SDK installieren, um sicherzustellen, dass die Intune-Funktionen in Ihren Android-Apps auch auf Android P-Geräten wie erwartet ausgeführt werden. Diese Version des Intune App SDK stellt ein integriertes Plug-In bereit, das die SDK-Updates ausführt. Sie müssen keinerlei integrierten Code neu schreiben. Weitere Details finden Sie unter [Intune SDK für Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Wenn Sie das alte Kennzeichenformat für Intune verwenden, empfehlen wir die Verwendung des Aktenkoffersymbols. Informationen zum Branding finden Sie in [diesem GitHub-Repository](https://github.com/msintuneappsdk/intune-app-partner-badge).

#### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Weitere Synchronisierungsoptionen in der Unternehmensportal-App für Windows  
Mit der Unternehmensportal-App für Windows können Sie nun direkt über die Windows-Taskleiste und das Startmenü eine Synchronisierung starten. Dieses Feature ist besonders hilfreich, wenn Sie nur Geräte synchronisieren und auf Unternehmensressourcen zugreifen müssen. Klicken Sie mit der rechten Maustaste auf das Unternehmensportalsymbol, das an die Taskleiste oder das Startmenü angeheftet ist, um das neue Feature zu verwenden. Klicken Sie in den Menüoptionen (auch als Sprungliste bezeichnet) auf **Dieses Gerät synchronisieren**. Die Unternehmensportal-App wird geöffnet und zeigt die Seite **Einstellungen** an. Außerdem wird die Synchronisierung gestartet. Einen Überblick über dieses neue Feature erhalten Sie unter [Updates der Benutzeroberfläche](../whats-new-app-ui.md).   

#### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Geänderte Durchsuchen-Funktion in der Unternehmensportal-App für Windows  
Beim Durchsuchen von oder Suchen nach Apps in der Unternehmensportal-App für Windows können Sie zwischen der Ansicht **Kacheln** und der neu hinzugefügten Ansicht **Details** wechseln. In der neuen Ansicht werden Anwendungsdetails wie Namen, Herausgeber, Veröffentlichungsdatum und Installationsstatus angezeigt.  

Auf der Seite **Apps** können Sie sich in der Ansicht **Installiert** Details zu abgeschlossenen und laufenden App-Installationen anzeigen lassen. Unter [Updates der Benutzeroberfläche](../whats-new-app-ui.md) können Sie sich einen Eindruck von der neuen Ansicht verschaffen.  

#### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Verbesserte Funktionen der Unternehmensportal-App für Geräteregistrierungs-Manager  
Wenn ein Geräteregistrierungs-Manager (DEM) sich bei der Unternehmensportal-App für Windows anmeldet, listet die App nun nur das aktuell ausgeführte Gerät des DEM auf. Durch diese Verbesserung wird die Anzahl der Timeouts verringert, die in der Vergangenheit aufgetreten sind, wenn die App versucht hat, alle durch den DEM registrierten Geräte anzuzeigen.  

#### <a name="block-app-access-based-on-unapproved-device-vendors-and-models----1425689----"></a>Blockieren des App-Zugriffs basierend auf nicht genehmigten Geräteherstellern und Modellen <!-- 1425689 ! -->
Der Intune-IT-Administrator kann über Intune-App-Schutzrichtlinien die Umsetzung einer festgelegten Liste von Android-Herstellern und/oder iOS-Modellen erzwingen. Der IT-Administrator kann eine durch Semikolon getrennte Liste von Herstellern für Android-Richtlinien und Gerätemodelle für iOS-Richtlinien bereitstellen. Intune-App-Schutzrichtlinien gelten nur für Android und iOS. Für diese festgelegte Liste können zwei verschiedene Aktionen ausgeführt werden:
- Blockieren des App-Zugriffs auf Geräten, die nicht angegeben sind.
- Selektives Zurücksetzen von Unternehmensdaten auf Geräten, die nicht angegeben sind. 

Der Benutzer kann nicht auf die Zielanwendung zugreifen, wenn die Anforderungen der Richtlinie nicht erfüllt sind. Anhand von Einstellungen werden Benutzer entweder blockiert oder Unternehmensdaten innerhalb der App selektiv zurückgesetzt. Für dieses Feature ist auf iOS-Geräten die Beteiligung von Anwendungen erforderlich (wie z.B. WXP, Outlook, Managed Browser, Yammer), um das Intune App SDK für dieses Feature für die Zielanwendungen zu erzwingen. Diese Integration erfolgt fortlaufend und ist von den jeweiligen Anwendungsteams abhängig. Unter Android ist für dieses Feature das neueste Unternehmensportal erforderlich. 

Auf Endbenutzergeräten führt der Intune-Client Aktionen auf Grundlage eines einfachen Abgleichs der Zeichenfolgen aus, die auf dem Blatt „Intune“ für Anwendungsschutzrichtlinien angegeben sind. Dies hängt ausschließlich von dem Wert ab, den das Gerät meldet. Daher sollte der IT-Administrator sicherstellen, dass das beabsichtigte Verhalten korrekt ist. Dazu kann diese Einstellung basierend auf einer Vielzahl von Geräteherstellern und Modellen für eine kleine Benutzergruppe getestet werden. Wählen Sie in Microsoft Intune **Client-Apps** > **App-Schutzrichtlinien** aus, um App-Schutzrichtlinien anzuzeigen und hinzuzufügen. Weiter Informationen zu App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](../apps/app-protection-policy.md) und [Selektives Löschen von Daten mithilfe von Zugriffsaktionen für App-Schutzrichtlinien in Intune](../apps/app-protection-policies-access-actions.md).

#### <a name="access-to-macos-company-portal-pre-release-build---1734766---"></a>Zugriff auf das Vorabreleasebuild der macOS-Unternehmensportal-App<!-- 1734766 -->
Sie können sich mithilfe von Microsoft AutoUpdate registrieren, um nach einem Beitritt zum Insider-Programm frühzeitig Builds zu erhalten. Durch eine Registrierung können Sie das aktualisierte Unternehmensportal verwenden, bevor sie Ihren Endbenutzern zur Verfügung steht. Weitere Informationen finden Sie im [Microsoft Intune-Blog](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices---1497640---"></a>Erstellen von Konformitätsrichtlinien für macOS-Geräte über Firewalleinstellungen<!-- 1497640 -->
Beim Erstellen einer neuen macOS-Konformitätsrichtlinie (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Plattform: macOS** > **Systemsicherheit**) sind einige neue **Firewall**-Einstellungen verfügbar: 

- **Firewall:** Hier konfigurieren Sie, wie eingehende Verbindungen in Ihrer Umgebung behandelt werden.
- **Eingehende Verbindungen:** Mit dieser Einstellung können Sie eingehende Verbindungen für grundlegende Internetdienste wie DHCP, Bonjour und IPSec zulassen und alle anderen eingehenden Verbindungen **blockieren**. Alle Freigabedienste werden durch diese Einstellung blockiert.
- **Geschützter Modus:** Durch die **Aktivierung** dieser Einstellung hindern Sie das Gerät daran, auf Suchanforderungen zu antworten. Das Gerät antwortet weiterhin auf eingehende Anforderungen für autorisierte Apps.

Gilt für: macOS 10.12 und höher

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later---1879077---"></a>Neues WLAN-Gerätekonfigurationsprofil für Windows 10 und höher<!-- 1879077 -->
Aktuell können Sie WLAN-Profile mithilfe von XML-Dateien importieren und exportieren. Durch dieses Update können Sie ein WLAN-Gerätekonfigurationsprofil genau wie für andere Plattformen auch direkt in Intune erstellen.

Um ein Profil zu erstellen, öffnen Sie **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** > **WLAN**. 

Gilt für Windows 10 und höher.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed---2149998---"></a>„Kiosk – veraltet“ ist ausgegraut und kann nicht verändert werden<!-- 2149998 -->
Das Kiosk-Feature (Vorschauversion) (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** > **Geräteeinschränkungen**) ist veraltet und wurde durch [Kiosk-Einstellungen für Windows 10 und höher](../configuration/kiosk-settings.md) ersetzt. Durch dieses Update wird das Feature **Kiosk - Obsolete** (Kiosk – veraltet) ausgegraut, und die Benutzeroberfläche kann nicht verändert oder aktualisiert werden. 

Informationen zum Aktivieren des Kioskmodus finden Sie unter [Kioskeinstellungen für Windows 10 und höher in Intune](../configuration/kiosk-settings.md).

Gilt für Windows 10 und höher, Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities---2184013---"></a>APIs für die Verwendung von Zertifizierungsstellen von Drittanbietern<!-- 2184013 -->
Mit diesem Update wird eine Java-API eingeführt, mit der sich Drittanbieter-Zertifizierungsstellen in Intune und SCEP integrieren lassen. Benutzer können so das SCEP-Zertifikat einem Profil hinzufügen und es über MDM auf Geräte anwenden.

Derzeit unterstützt Intune [SCEP-Anforderungen über Active Directory-Zertifikatdienste](../protect/certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser---2455253---"></a>Umschaltfläche zum Anzeigen oder Ausblenden der Schaltfläche „Sitzung beenden“ auf einem Kioskbrowser<!-- 2455253 -->
Sie können nun konfigurieren, ob Kioskbrowser die Schaltfläche „Sitzung beenden“ anzeigen. Sie finden das Steuerelement unter **Gerätekonfiguration** > **Kiosk (Vorschauversion)** > **Kioskwebbrowser**. Wenn die Schaltfläche aktiviert ist und ein Benutzer darauf klickt, fordert die App eine Bestätigung zum Beenden der Sitzung an. Wenn dies bestätigt wird, löscht der Browser alle Browserdaten und navigiert zurück zur Standard-URL.

#### <a name="create-an-esim-cellular-configuration-profile---2564077---"></a>Erstellen eines eSIM-Mobilfunkkonfigurationsprofils<!-- 2564077 -->
Unter **Gerätekonfiguration** können Sie ein eSIM-Mobilfunkprofil erstellen. Sie können eine Datei importieren, die Mobilfunk-Aktivierungscodes enthält, die von Ihrem Mobilfunkanbieter bereitgestellt werden. Diese Profile können daraufhin für Ihre mit eSIM-LTE aktivierten Windows 10-Geräte bereitgestellt werden, z.B. für das Surface Pro LTE und andere eSIM-fähigen Geräte.

Überprüfen Sie, ob Ihre [Geräte eSIM-Profile unterstützen](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Gilt für Windows 10 und höher.

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings---1058963-eenotready---"></a>Wählen Sie unter den Einstellungen „Auf Arbeits-, Schul- oder Unikonto zugreifen“ die Gerätekategorien aus.<!-- 1058963 eenotready --> 
Wenn Sie die [Gerätegruppenzuordnung](../enrollment/device-group-mapping.md) aktiviert haben, werden Benutzer unter Windows 10 aufgefordert, eine Gerätekategorie auszuwählen, nachdem sie sich unter **Einstellungen** > **Konten** > **Auf Geschäfts-, Schul- oder Unikonto zugreifen** mit der Schaltfläche **Verbinden** angemeldet haben. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles---1500307---"></a>Verwenden von „sAMAccountName“ als Kontobenutzername für E-Mail-Profile<!-- 1500307 -->
Sie können das lokal vorhandene Attribut **sAMAccountName** als Kontobenutzername für Android-, iOS- und Windows 10-E-Mail-Profile verwenden. Mit den Attributen `domain` oder `ntdomain` können Sie in Azure Active Directory (Azure AD) außerdem die Domain abrufen. Alternativ können Sie auch eine benutzerdefinierte statische Domäne eingeben.

Zur Nutzung dieses Features müssen Sie das `sAMAccountName`-Attribut Ihrer lokalen Active Directory-Umgebung mit Azure AD synchronisieren.

Gilt für: [Android](../configuration/email-settings-android.md), [iOS](../configuration/email-settings-ios.md), [Windows 10 und höher](../configuration/email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict---1556983---"></a>Anzeigen von in Konflikt stehenden Gerätekonfigurationsprofilen<!-- 1556983 -->
Unter **Gerätekonfiguration** wird eine Liste der vorhandenen Profile angezeigt. Mit diesem Update wird eine neue Spalte hinzugefügt, die Details zu Profilen enthält, die in Konflikt stehen. Sie können eine in Konflikt stehende Zeile anklicken, um die Einstellung und das Profil anzuzeigen, bei denen der Konflikt vorhanden ist. 

Weitere Informationen zum [Verwalten von Konfigurationsprofilen](../configuration/device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance---2308882---"></a>Neue Status für Geräte unter „Gerätekonformität“<!-- 2308882 -->
Wählen Sie unter **Gerätekonformität** > **Richtlinien** eine Richtlinie aus. Dort wurden unter **Übersicht** folgende neue Status hinzugefügt:
- Erfolgreich
- Fehler
- Konflikt
- pending
- Nicht anwendbar. Außerdem wird eine Grafik angezeigt, in der die Anzahl der Geräte für andere Plattformen zu sehen ist. Beim Aufruf eines iOS-Profils wird beispielsweise auf der neuen Kachel die Anzahl der Nicht-iOS-Geräte angezeigt, die diesem Profil ebenfalls zugewiesen sind. Weitere Informationen finden Sie im Artikel zu [Gerätekonformitätsrichtlinien](../protect/compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions---2325484---"></a>Unterstützung von Drittanbieter-Antivirenlösungen in Gerätekonformitätsrichtlinien<!-- 2325484 -->
Beim Erstellen einer Gerätekonformitätsrichtlinie (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Plattform: Windows 10 und höher** > **Einstellungen** > **Systemsicherheit**) sind neue Optionen für **[Gerätesicherheit](../protect/compliance-policy-create-windows.md)** verfügbar: 
- **Antivirus:** Wenn für diese Einstellung **Require** (Erforderlich) festgelegt ist, können Sie die Konformität mit Antivirenlösungen (beispielsweise Symantec und Windows Defender) überprüfen, die beim Windows-Sicherheitscenter registriert sind. 
- **Antispyware:** Wenn für diese Einstellung **Require** (Erforderlich) festgelegt ist, können Sie die Konformität mit Antispyware-Lösungen (beispielsweise Symantec und Windows Defender) überprüfen, die beim Windows Security Center registriert sind. 

Gilt für: Windows 10 und höher 

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate---2404851---"></a>Automatisches Markieren von Android-Geräten als „Geschäftlich“ über Samsung Knox Mobile Enrollment<!-- 2404851 -->
In der Standardeinstellung werden Android-Geräte, die über Samsung Knox Mobile Enrollment registriert sind, nun unter **Gerätebesitz** als **Geschäftlich** markiert. Sie müssen also Unternehmensgeräte vor der Registrierung bei Knox Mobile Enrollment nicht manuell über IMEI oder Seriennummern identifizieren.

#### <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens---1853904---"></a>Geräte ohne die Spalte „Profiles“ (Profile) in der Liste der Registrierungsprogrammtoken<!-- 1853904 -->
In der Liste der Registrierungprogrammtoken gibt es eine neue Spalte, in der die Anzahl der Geräte ohne zugewiesenes Profil angezeigt werden. So können Administratoren diesen Geräten leichter Profile zuweisen, bevor sie sie Benutzern zuweisen. Navigieren Sie zu **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken**, um die neue Spalte anzuzeigen.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="bulk-delete-devices-on-devices-blade---1793693---"></a>Massenlöschung von Geräten auf dem Blatt „Geräte“<!-- 1793693 -->
Sie können nun mehrere Geräte gleichzeitig über das Blatt „Geräte“ löschen. Wählen Sie **Geräte** > **Alle Geräte** aus, wählen Sie die Geräte aus, die Sie löschen möchten, und klicken Sie auf **Löschen**. Es wird eine Warnung für die Geräte ausgegeben, die nicht gelöscht werden können.

#### <a name="google-name-changes-for-android-for-work-and-play-for-work--842873---"></a>Google-Namensänderungen für Android for Work und Play for Work<!--842873 -->
In Intune wurde die Android for Work-Terminologie aktualisiert, um die Änderungen von Google-Markennamen widerzuspiegeln. Die Benennungen „Android for Work“ und „Play for Work“ werden nicht mehr verwendet. Die Terminologie wurde je nach Kontext angepasst:
- „Android Enterprise“ bezieht sich auf den allgemeinen modernen Android-Verwaltungsstapel.
- „Arbeitsprofil“ oder „Profilbesitzer“ bezieht sich auf BYOD-Geräte, die mit Arbeitsprofilen verwaltet werden.
- „Managed Google Play“ bezieht sich auf den App Store von Google.

#### <a name="rules-for-removing-devices---1609459---"></a>Regeln für das Entfernen von Geräten<!-- 1609459 -->
Neue Regeln, mit denen Sie Geräte automatisch entfernen können, die über einen festgelegten Zeitraum nicht mehr eingecheckt waren, sind verfügbar. Um die neue Regel anzuzeigen, wechseln Sie in den Bereich **Intune**, und wählen Sie **Geräte** und anschließend **Device removal rules** (Regeln zur Gerätebereinigung) aus.

#### <a name="corporate-owned-single-use-support-for-android-devices---1630973---"></a>COSU-Unterstützung (corporate-owned, single use, Unternehmensgeräte für spezifische Anwendungsfälle) für Android-Geräte<!-- 1630973 -->

Intune unterstützt jetzt kioskartige, stringent verwaltete Android-Geräte, deren Einsatzbereich stark eingeschränkt ist. Dadurch können Administratoren festlegen, dass auf einem Gerät nur eine oder einige wenige Apps und Aktionen von Benutzern verwendet werden dürfen. Navigieren Sie in Intune zu **Geräteregistrierung** > **Android-Registrierung** > **Kiosk und Taskgeräteregistrierungen**, um einen Android-Kiosk einzurichten. Weitere Informationen finden Sie unter [Set up enrollment of Android enterprise kiosk devices (Einrichten der Registrierung von Android-Kioskgeräte des Unternehmens)](../enrollment/android-kiosk-enroll.md).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded---2203794--"></a>Duplikatprüfung auf Zeilenbasis beim Hochladen unternehmensspezifischer Gerätebezeichner<!-- 2203794-->
Beim Hochladen von Unternehmens-IDs stellt Intune jetzt eine Liste mit mehrfach vorhandenen IDs bereit und bietet Ihnen die Möglichkeit, die vorhandenen Informationen zu ersetzen oder beizubehalten. Der Bericht wird angezeigt, wenn nach dem Klicken auf **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten** > **Bezeichner hinzufügen** Duplikate vorhanden sind. 

#### <a name="manually-add-corporate-device-identifiers---2203803---"></a>Manuelles Hinzufügen von Unternehmensgerätebezeichnern<!-- 2203803 -->
Sie können Unternehmensgeräte-IDs jetzt manuell hinzufügen. Klicken Sie auf **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten** > **Hinzufügen**. 


<!-- ########################## -->
## <a name="june-2018"></a>Juni 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies---1817882---"></a>Unterstützung von Microsoft Edge für mobile Geräte für die App-Schutzrichtlinien von Intune<!-- 1817882 -->
Microsoft Edge für mobile Geräte unterstützt nun die App-Schutzrichtlinien, die in Intune definiert sind.

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode---1560077----"></a>Abrufen der zugeordneten App-Benutzermodell-ID (AUMID) für Apps im Microsoft Store für Unternehmen im Kioskmodus<!-- 1560077 ! -->
Intune kann jetzt die Modell-IDs der Anwendungsbenutzer (AUMIDs) für Apps im Microsoft Store für Unternehmen abrufen, um eine verbesserte Konfiguration des Kioskprofils bereitzustellen.

Weitere Informationen zu Apps im Microsoft Store für Unternehmen finden Sie unter [Verwalten von Apps aus dem Microsoft Store für Unternehmen](../apps/windows-store-for-business.md).

#### <a name="new-company-portal-branding-page---1916370---"></a>Neue Seite für das Branding des Unternehmensportals<!-- 1916370 -->
Die Seite für das Branding des Unternehmensportals hat ein neues Layout, neue Meldungen und neue QuickInfos.


### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="pradeo---new-mobile-threat-defense-partner---1169249---"></a>Pradeo: neuer Mobile Threat Defense-Partner<!-- 1169249 -->
Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen mit bedingtem Zugriff basierend auf Risikobewertungen steuern, die von Pradeo vorgenommen werden, einer Mobile Threat Defense-Lösung, die mit Microsoft Intune zusammenarbeitet.

#### <a name="use-fips-mode-with-the-ndes-certificate-connector---1333688---"></a>Verwenden des FIPS-Modus mit dem NDES-Certificate Connector<!-- 1333688 -->
Wenn Sie den NDES-Certificate Connector auf einem Computer mit aktiviertem FIPS-Modus (Federal Information Processing Standard) installieren, funktionierte das Ausstellen und Widerrufen von Zertifikaten nicht wie erwartet. Mit diesem Update ist die Unterstützung für FIPS im NDES-Certificate Connector enthalten. 

Dieses Update enthält ebenfalls Folgendes:

- Der NDES-Certificate Connector erfordert .NET Framework 4.5. Dieses Framework ist automatisch in Windows Server 2016 und Windows Server 2012 R2 enthalten. Zuvor war .NET Framework 3.5 die mindestens erforderliche Version.
- Die Unterstützung für TLS 1.2 ist im NDES-Certificate Connector enthalten. Wenn der Server, auf dem NDES-Certificate Connector installiert ist, TLS 1.2 unterstützt, wird TLS 1.2 verwendet. Wenn der Server TLS 1.2 nicht unterstützt, wird TLS 1.1 verwendet. Derzeit wird TLS 1.1 für die Authentifizierung zwischen den Geräten und dem Server verwendet.

Weitere Informationen finden Sie unter [Konfigurieren und Verwenden von SCEP-Zertifikaten](../protect/certificates-scep-configure.md) und [Konfigurieren und Verwenden von PKCS-Zertifikaten](../protect/certficates-pfx-configure.md).

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles---1333680----"></a>Unterstützung für VPN-Profile für Palo Alto Networks GlobalProtect<!-- 1333680 ! -->
Mit diesem Update können Sie Palo Alto Networks GlobalProtect als VPN-Verbindungstyp für VPN-Profile in Intune auswählen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Profiltyp** > **VPN**). Für dieses Release werden die folgenden Plattformen unterstützt: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings---1403702---"></a>Ergänzungen zu den Einstellungen der Sicherheitsoptionen für lokale Geräte<!-- 1403702 -->
Sie können jetzt für Windows 10-Geräte zusätzliche Einstellungen für Sicherheitsoptionen für lokale Geräte konfigurieren. Zusätzliche Einstellungen sind bei Microsoft-Netzwerkclients, Microsoft-Netzwerkservern, bei der Netzwerkzugriff und -sicherheit und bei der interaktiven Anmeldung verfügbar. Diese Einstellungen finden Sie in der Endpoint Protection-Kategorie, wenn Sie eine Gerätekonfigurationsrichtlinie für Windows 10 erstellen.

#### <a name="enable-kiosk-mode-on-windows-10-devices---1560072----"></a>Aktivieren des Kioskmodus auf Windows 10-Geräten<!-- 1560072 ! -->
Auf Windows 10-Geräten können Sie ein Konfigurationsprofil erstellen und den Kioskmodus aktivieren (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10** > **Geräteeinschränkungen** > **Kiosk**). Bei diesem Update wurde die Einstellung **Kiosk (Vorschau)** in **Kiosk (veraltet)** umbenannt. **Kiosk (veraltet)** wird nicht mehr empfohlen, ist jedoch bis zum Juli-Update weiterhin funktionsfähig. **Kiosk (veraltet)** wird durch den neuen **Kiosk**-Profiltyp ersetzt (**Profil erstellen** > **Windows 10**  >  **Kiosk (Vorschau)**), der die Einstellungen zum Konfigurieren von Kiosks unter Windows 10 RS4 und höher enthält.

Gilt für Windows 10 und höher.

#### <a name="device-profile-graphical-user-chart-is-back---2160133---"></a>Benutzerdiagramm des Geräteprofils wieder vorhanden<!-- 2160133 -->
Während der Verbesserung der numerischen Werte, die im Diagramm des Geräteprofils dargestellt werden (**Gerätekonfiguration** > **Profile** > vorhandenes Profil auswählen > **(Übersicht)**), wurde das Benutzerdiagramm vorübergehend entfernt.

Bei diesem Update ist das Benutzerdiagramm wieder enthalten und wird im Azure-Portal angezeigt.

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication---1165118---"></a>Unterstützung für die Registrierung mit Windows Autopilot ohne Benutzerauthentifizierung<!-- 1165118 -->
Intune unterstützt jetzt die Registrierung mit Windows Autopilot ohne Benutzerauthentifizierung. Dies ist eine neue Option im Windows Autopilot-Bereitstellungsprofil („Autopilot Deployment mode“ (Autopilot-Bereitstellungsmodus) kann auf „Self-Deploying“ (Selbstbereitstellung) festgelegt werden).  Auf dem Gerät muss Windows 10 Insider Preview Build 17672 oder höher ausgeführt werden, außerdem muss ein TPM 2.0-Chip eingebaut sein, um diese Art der Registrierung erfolgreich abzuschließen. Da keine Benutzerauthentifizierung erforderlich ist, sollten Sie diese Option nur Geräte zuweisen, zu denen Sie physisch Zugang haben.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot---1821766---"></a>Neue Einstellung für Sprache/Region beim Konfigurieren von OOBE für Autopilot<!-- 1821766 -->
Es steht eine neue Konfigurationseinstellung zur Verfügung, mit der die Sprache und Region für Autopilot-Profile während der Out-of-Box-Experience festgelegt werden kann. Klicken Sie auf **Geräteregistrierung** > **Windows-Registrierung** > **Bereitstellungsprofile** > **Profil erstellen** > **Bereitstellungsmodus** = **Selbstbereitstellung** > **Standardwerte konfiguriert**, um die neuen Einstellungen anzuzeigen.

#### <a name="new-setting-for-configuring-device-keyboard---1821768---"></a>Neue Einstellung zum Konfigurieren der Gerätetastatur<!-- 1821768 -->
Es steht eine neue Einstellung zur Verfügung, mit der die Tastatur für AutoPilot-Profile während der Out-of-Box-Experience konfiguriert werden kann. Klicken Sie auf **Geräteregistrierung** > **Windows-Registrierung** > **Bereitstellungsprofile** > **Profil erstellen** > **Bereitstellungsmodus** = **Selbstbereitstellung** > **Standardwerte konfiguriert**, um die neuen Einstellungen anzuzeigen.

#### <a name="autopilot-profiles-moving-to-group-targeting---1877935---"></a>Autopilot-Profile können bald Gruppenziele verwenden<!-- 1877935 -->
Autopilot-Bereitstellungsprofile können Azure AD-Gruppen zugewiesen werden, die Autopilot-Geräte enthalten.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="set-compliance-by-device-location---851881----"></a>Festlegen der Kompatibilität nach Gerätestandort<!-- 851881 ! -->
In einigen Situationen empfiehlt es sich, den Zugriff auf Unternehmensressourcen auf einen bestimmten Standort zu beschränken, der durch eine Netzwerkverbindung definiert ist. Sie können jetzt eine Kompatibilitätsrichtlinie (**Gerätekompatibilität** > **Standorte**) basierend auf der IP-Adresse des Geräts erstellen. Wird das Gerät außerhalb des IP-Bereichs bewegt, kann damit nicht auf Unternehmensressourcen zugegriffen werden.

Gilt für Android-Geräte 6.0 und höher mit der aktualisierten Unternehmensportal-App

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Verhindern von Verbraucher-Apps und -Umgebungen auf dem Windows 10 Enterprise RS4 Autopilot-Gerät<!-- 1621980 -->
Sie können die Installation von Verbraucher-Apps und -Umgebungen auf Ihren Windows 10 Enterprise RS4 AutoPilot-Geräten verhindern. Navigieren Sie zu **Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Plattform** = **Windows 10 oder höher** > **Profiltyp** = **Geräteeinschränkungen** > **Konfigurieren** > **Windows-Blickpunkt** > **Endbenutzerfeatures**, um dieses Feature anzuzeigen. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates---1732948---"></a>Deinstallieren der letzten Softwareupdates von Windows 10<!-- 1732948 -->
Wenn Sie Probleme mit Unterbrechungen auf Ihren Windows 10-Computern feststellen, können Sie das neueste Featureupdate bzw. Qualitätsupdate deinstallieren (einen Rollback ausführen). Die Deinstallation eines Feature- oder Qualitätsupdates ist für den Wartungskanal nur möglich, wenn das Gerät eingeschaltet ist. Durch die Deinstallation wird eine Richtlinie ausgelöst, die das vorherige Update auf Ihren Windows 10-Computern wiederherstellt. Sie können insbesondere für Featureupdates den Zeitraum, in dem eine Deinstallation für die neueste Version durchgeführt werden kann, auf 2–60 Tage einschränken. Um die Deinstallationsoptionen für das Softwareupdate festzulegen, wählen Sie im Azure-Portal auf dem Blatt **Microsoft Intune** die Option **Softwareupdates** aus. Klicken Sie auf dem Blatt **Softwareupdates** auf **Windows 10-Updateringe**. Sie können dann die Option **Deinstallieren** im Bereich **Übersicht** auswählen.

#### <a name="search-all-devices-for-imei-and-serial-number---1793685---"></a>Durchsuchen aller Geräte nach IMEI und Seriennummer<!-- 1793685 -->
Sie können jetzt auf dem Blatt „Alle Geräte“ nach IMEI und Seriennummern suchen (E-Mail, UPN, Gerätename und Verwaltungsname sind weiterhin verfügbar). Klicken Sie in Intune auf **Geräte** > **Alle Geräte**, und geben Sie dann ein Suchwort in das Suchfeld ein.

#### <a name="management-name-field-will-be-editable---1875989---"></a>Feld für Verwaltungsname kann bearbeitet werden<!-- 1875989 -->
Sie können das Feld für den Verwaltungsnamen auf dem Blatt **Eigenschaften** eines Geräts bearbeiten. Zum Bearbeiten dieses Felds wählen Sie **Geräte** > **Alle Geräte** > Gerät auswählen > **Eigenschaften** aus. Sie können das Feld für den Verwaltungsnamen zur eindeutigen Identifizierung eines Geräts verwenden.

#### <a name="new-all-devices-filter-device-category---1878520---"></a>Neue Filter für „Alle Geräte“: Gerätekategorie<!-- 1878520 -->
Sie können jetzt die Liste **Alle Geräte** nach Gerätekategorie filtern. Klicken Sie dafür auf **Geräte** > **Alle Geräte** > **Filter** > **Gerätekategorie**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices---1985547---"></a>Verwenden von TeamViewer zur Bildschirmübertragung zwischen iOS- und macOS-Geräten<!-- 1985547 -->
Administratoren können jetzt eine Verbindung mit [TeamViewer](../remote-actions/teamviewer-support.md) herstellen und eine Bildschirmübertragungssitzung mit iOS- und macOS-Geräten starten. iPhone, iPad und macOS-Benutzer können ihre Bildschirme live an andere Desktops oder mobile Geräte übertragen. 

#### <a name="multiple-exchange-connector-support---2070451---"></a>Unterstützen mehrerer Exchange Connectors<!-- 2070451 -->
Sie sind nicht mehr auf einen Microsoft Intune Exchange Connector pro Mandant beschränkt. Intune unterstützt mehrere Exchange Connectors, sodass Sie Intune mithilfe von mehreren lokalen Exchange-Organisationen für bedingten Zugriff einrichten können.

Mit einem lokalen Exchange-Connector von Intune können Sie den Zugriff von Geräten auf Ihre lokalen Exchange-Postfächer verwalten. Dies ist abhängig davon, ob ein Gerät bei Intune registriert ist, und ob es den Gerätekompatibilitätsrichtlinien von Intune entspricht. Um einen Connector einzurichten, müssen Sie den lokalen Exchange-Connector von Intune aus dem Azure-Portal herunterladen und ihn auf einem Server in Ihrer Exchange-Organisation installieren. Klicken Sie im Microsoft Intune-Dashboard auf **Lokaler Zugriff** und dann unter **Setup** auf **Exchange ActiveSync-Connector**. Laden Sie den lokalen Exchange-Connector herunter, und installieren Sie ihn auf einem Server in Ihrer Exchange-Organisation. Da Sie nun nicht länger auf einen Exchange-Connector pro Mandant beschränkt werden, wenn Sie weitere Exchange-Organisationen haben, können Sie anhand des gleichen Durchgangs einen Connector für jede weitere Exchange-Organisation herunterladen und installieren.

#### <a name="new-device-hardware-detail-ccid---2156657---"></a>Neues Gerätehardwaredetail: CCID<!-- 2156657 -->
Für jedes Gerät sind jetzt auch die CCID-Informationen (Chip Card Interface Device) verfügbar. Klicken Sie auf **Geräte** > **Alle Geräte**, wählen Sie ein Gerät aus, und klicken Sie dann auf **Hardware**, und sehen Sie sich die **Netzwerkdetails**> an, um diese anzuzeigen.

#### <a name="assign-all-users-and-all-devices-as-scope-groups---2196803---"></a>Zuweisen aller Benutzer und aller Geräte als Bereichsgruppen<!-- 2196803 -->
Sie können alle Benutzer, alle Geräte sowie alle Benutzer und alle Geräte in Bereichsgruppen zuweisen. Klicken Sie hierzu auf **Intune-Rollen** > **Alle Rollen** > **Policy and profile manage** (Richtlinien- und Profil-Manager) > **Zuweisungen**, wählen Sie eine Zuweisung aus, und klicken Sie dann auf **Bereich (Gruppen)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices---2219806---"></a>UDID-Informationen jetzt für iOS- und macOS-Geräte enthalten<!-- 2219806 -->
Navigieren Sie zu **Geräte** > **Alle Geräte**, wählen Sie ein Gerät aus, und klicken Sie auf **Hardware**, um die UDID (eindeutiger Gerätebezeichner) für iOS- und macOS-Geräte anzuzeigen. Die UDID ist nur für Unternehmensgeräte verfügbar (wie unter **Geräte** > **Ale Geräte**, Gerät auswählen, **Eigenschaften** > **Gerätebesitz** festgelegt).

### <a name="intune-apps"></a>Intune-Apps

#### <a name="improved-troubleshooting-for-app-installation---928990---"></a>Verbesserte Problembehandlung für App-Installation<!-- 928990 -->
Auf Geräten, die mit Microsoft Intune MDM verwaltet werden, können App-Installationen manchmal fehlschlagen. In diesen Fällen kann es schwierig sein, die Fehlerursache zu verstehen oder das Problem zu beheben. Wir versenden eine öffentliche Vorschau unserer Features zur App-Problembehandlung. Unter jedem einzelnen Gerät wird ein neuer Knoten mit der Bezeichnung **Verwaltete Apps** angezeigt. Hier sind die Apps aufgelistet, die über Intune MDM übermittelt wurden. Innerhalb des Knotens wird eine Liste mit App-Installationsstatus angezeigt. Bei Auswahl einer einzelnen App wird die Problembehandlungsansicht für diese bestimmte App angezeigt. In der Problembehandlungsansicht sehen Sie den End-to-End-Lebenszyklus der App, z. B. wann die App erstellt, geändert, festgelegt und an ein Gerät übermittelt wurde. Darüber hinaus wird bei einer nicht erfolgreichen App-Installation der Fehlercode und eine hilfreiche Nachricht zur Ursache des Fehlers angezeigt. 

#### <a name="intune-app-protection-policies-and-microsoft-edge---1818968---"></a>Intune-App-Schutzrichtlinien und Microsoft Edge<!-- 1818968 -->
Der Browser Microsoft Edge für Mobilgeräte (iOS und Android) unterstützt nun Microsoft Intune-App-Schutzrichtlinien. Benutzer von iOS- und Android-Geräten, die sich mit ihren Azure AD-Unternehmenskonten bei Microsoft Edge anmelden, werden von Intune geschützt. Auf iOS-Geräten lässt die Richtlinie **Require managed browser for web content** (Managed Browser für Webinhalt erforderlich) zu, dass Benutzer Links in Microsoft Edge öffnen können, wenn der Browser verwaltet wird.

<!-- ########################## -->
## <a name="may-2018"></a>Mai 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="configuring-your-app-protection-policies---2144597-part-2---"></a>Konfigurieren von App-Schutzrichtlinien<!-- 2144597 Part 2 -->

Sie müssen jetzt im Azure-Portal nicht mehr auf das Dienstblatt Intune-App-Schutz gehen, sondern können einfach zu Intune navigieren. Es gibt derzeit nur einen Speicherort für App-Schutzrichtlinien in Intune. Beachten Sie, dass Sie bereits alle Ihre App-Schutzrichtlinien auf dem Blatt **Mobile App** in Intune unter **App-Schutzrichtlinien** finden. Diese Integration soll Ihre Cloudverwaltung vereinfachen. Beachten Sie, dass alle Richtlinien zum App-Schutz bereits in Intune verschoben wurden und Sie Ihre Richtlinien für den bedingten Zugriff ändern können. Sie finden die Intune App-Schutzrichtlinien (Intune App Policy Protection, APP) und die Richtlinien für bedingten Zugriff (Conditional Access, CA) jetzt unter **Bedingter Zugriff** im Abschnitt **Verwalten** auf dem Blatt **Microsoft Intune** oder im Abschnitt **Sicherheit** auf dem Blatt **Azure Active Directory**. Weitere Informationen zum Ändern von Richtlinien für bedingten Zugriff finden Sie unter [Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Weitere Informationen finden Sie unter [Was sind App-Schutzrichtlinien?](../apps/app-protection-policy.md)

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles---1553555---"></a>Erforderliche Installation von Richtlinien, Apps, Zertifikaten und Netzwerkprofilen<!-- 1553555 -->
Administratoren können Endbenutzern den Zugriff auf den Windows 10 RS4-Desktop verwehren, bis während der Bereitstellung von Autopilot-Geräten Richtlinien, Apps, Zertifikate und Netzwerkprofile von Intune installiert wurden. Weitere Informationen finden Sie unter [Set up an enrollment status page (Einrichten einer Statusseite für die Registrierung)](../enrollment/windows-enrollment-status.md).

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="samsung-knox-mobile-enrollment-support--1112863--"></a>Unterstützung von Samsung Knox Mobile Enrollment (KME)<!--1112863-->
Wenn Sie Intune mit Samsung Knox Mobile Enrollment (KME) verwenden, können Sie eine große Anzahl unternehmenseigener Android-Geräte registrieren. Benutzer mit einer WLAN- oder Mobilfunknetzverbindung können die Registrierung mit nur wenigen Tippbewegungen ausführen, wenn sie ihre Geräte zum ersten Mal einschalten. Bei Verwendung der Knox Deployment App können Geräte über Bluetooth oder NFC registriert werden. Weitere Informationen finden Sie unter [Automatisches Registrieren von Android-Geräten mit Samsung Knox Mobile Enrollment](../enrollment/android-samsung-knox-mobile-enroll.md).

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung 

#### <a name="requesting-help-in-the-company-portal-for-windows-10---1874137---"></a>Anfordern von Unterstützung im Unternehmensportal für Windows 10<!-- 1874137 -->
Das Unternehmensportal für Windows 10 sendet App-Protokolle jetzt direkt an Microsoft, wenn der Benutzer den Workflow zum Abrufen von Hilfe zu einem Problem startet. So können Probleme, die Microsoft gemeldet werden, einfacher behoben und gelöst werden.

<!-- ########################## -->
## <a name="april-2018"></a>April 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Passcode-Unterstützung für MAM-PIN unter Android<!-- 1438086 -->

Intune-Administratoren können zukünftig eine Anforderung für den Anwendungsstart festlegen, um eine Kennung anstatt einer numerischen MAM-PIN zu erzwingen. Wenn dies konfiguriert ist, muss der Benutzer eine Kennung festlegen und verwenden, wenn er dazu aufgefordert wird, bevor der Zugriff auf MAM-aktivierte Apps gewährt wird. Eine Kennung ist als numerische PIN mit mindestens einem Sonderzeichen oder einem Groß-/Kleinbuchstaben definiert. Intune unterstützt Kennungen auf ähnliche Weise wie die vorhandene numerische PIN. Es kann eine Mindestlänge über die Administratorkonsole festgelegt werden, sodass wiederholte Zeichen und Sequenzen möglich sind. Für dieses Feature ist die neueste Unternehmensportalversion unter Android erforderlich. Dieses Feature ist bereits für iOS verfügbar.

#### <a name="line-of-business-lob-app-support-for-macos---1473977---"></a>Unterstützung von branchenspezifischen Apps für macOS<!-- 1473977 -->
Microsoft Intune stellt eine Funktion zur Installation von macOS-LOB-Apps aus dem Azure-Portal bereit. Sie können eine macOS-LOB-App zu Intune hinzufügen, nachdem sie von dem in GitHub verfügbaren Tool vorab verarbeitet wurde. Wählen Sie im Azure-Portal auf dem Blatt **Intune** die Option **Client-Apps** aus. Wählen Sie auf dem Blatt **Client-Apps** die Option **Apps** > **Hinzufügen** aus. Wählen Sie auf dem Blatt **App hinzufügen** die Option **Branchen-App** aus. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment---1813073---"></a>Integrierte App-Zuweisung im Android Enterprise-Arbeitsprofil für die Gruppen „Alle Benutzer“ und „Alle Geräte“<!-- 1813073 -->
Sie können die integrierten Gruppen **Alle Benutzer** und **Alle Geräte** für die App-Zuweisung zum Android Enterprise-Arbeitsprofil nutzen. Weitere Informationen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](../apps/apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users---1947010---"></a>Intune installiert benötigte Apps neu, die von Benutzern deinstalliert wurden<!-- 1947010 -->
Wenn ein Endbenutzer eine benötigte App deinstalliert, installiert Intune die App automatisch innerhalb von 24 Stunden neu, anstatt auf die Beendigung des siebentägigen Neuauswertungszyklus zu warten.

#### <a name="update-where-to-configure-your-app-protection-policies---2144597---"></a>Aktualisieren, wo Ihre App-Schutzrichtlinien konfiguriert werden<!-- 2144597 -->

Sie werden in Microsoft Intune im Azure-Portal kurzzeitig von dem Dienstblatt **Intune-Schutz für Apps** auf das Blatt **Mobile App** umgeleitet. Beachten Sie, dass alle Ihre App-Schutzrichtlinien bereits auf dem Blatt **Mobile App** in Intune unter der App-Konfiguration vorhanden sind. Statt Intune-App-Schutz aufzurufen, verwenden Sie einfach Intune. Im April 2018 beenden wir die Umleitung und entfernen das Dienstblatt **Intune-App-Schutz** vollständig, sodass es nur einen Ort für App-Richtlinien in Intune gibt. 

**Wie wirkt sich das auf mich aus?**
Sowohl eigenständige Intune-Kunden als auch hybride Kunden (die Intune mit Configuration Manager verwenden) sind von dieser Änderung betroffen. Diese Integration soll Ihre Cloudverwaltung vereinfachen.

**Was muss ich als Vorbereitung auf diese Änderung tun?**
Markieren Sie **Intune** und nicht das Dienstblatt **Intune-Schutz für Apps** als Favorit, und machen Sie sich in Intune mit dem Richtlinienworkflow für den App-Schutz auf der Blatt **Mobile App** vertraut. Es wird zwar für einen kurzen Zeitraum eine Umleitung eingerichtet, aber danach wird das Blatt **Intune-Schutz für App** entfernt. Beachten Sie, dass alle Richtlinien zum App-Schutz bereits in Intune verschoben wurden und Sie Ihre Richtlinien für bedingten Zugriff ändern können. Weitere Informationen zum Ändern von Richtlinien für bedingten Zugriff finden Sie unter [Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Weitere Informationen finden Sie unter [Was sind App-Schutzrichtlinien?](../apps/app-protection-policy.md) 

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group---1449153---"></a>Geräteprofildiagramm und Statusliste zeigen alle Geräte in einer Gruppe<!-- 1449153 -->
Wenn Sie ein Geräteprofil konfigurieren (**Gerätekonfiguration** > **Profile**), wählen Sie das Geräteprofil aus, z.B. iOS. Sie weisen dieses Profil einer Gruppe zu, die iOS-Geräte und Nicht-iOS-Geräte enthält. Im Grafikdiagramm ist zu sehen, dass das Profil dem iOS-Gerät *und* dem Nicht-iOS-Gerät zugewiesen wird (**Gerätekonfiguration** > **Profile** > vorhandenes Profil auswählen > **Übersicht**). Wenn Sie das Grafikdiagramm auf der Registerkarte **Übersicht** auswählen, werden unter **Gerätestatus** alle Geräte der Gruppe aufgeführt, nicht nur iOS-Geräte. 

Nach diesem Update wird im Grafikdiagramm (**Gerätekonfiguration** > **Profile** > vorhandenes Profil auswählen > **Übersicht**) nur die Anzahl für das spezifische Geräteprofil angezeigt. Wenn z.B. das Gerätekonfigurationsprofil für iOS-Geräte gilt, wird im Diagramm nur die Anzahl der iOS-Geräte aufgelistet. Wenn Sie das Grafikdiagramm auswählen und **Gerätestatus** öffnen, werden nur iOS-Geräte aufgelistet.

Während dieses Updates wird das Benutzerdiagramm vorübergehend entfernt. 

#### <a name="always-on-vpn-for-windows-10--1333666---"></a>Always On-VPN für Windows 10<!--1333666 -->

Derzeit kann [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) auf Windows 10-Geräten mit einem benutzerdefinierten VPN (virtuelles privates Netzwerk), das über den OMA-URI erstellt wurde, verwendet werden.

Mit diesem Update können Administratoren Always On für VPN-Profile auf Windows 10 direkt in Intune im Azure-Portal aktivieren. Always On-VPN-Profile stellen automatisch eine Verbindung her, wenn Folgendes passiert:

- Benutzer melden sich an ihren Geräten an.
- Das Netzwerk auf dem Gerät ändert sich.
- Der Bildschirm wird auf dem Gerät wieder eingeschaltet, nachdem er ausgeschaltet war.

#### <a name="new-printer-settings-for-education-profiles---1308900---"></a>Neue Druckereinstellungen für Education-Profile<!-- 1308900 -->

Für Education-Profile sind neue Einstellungen in der Kategorie **Drucker** unter **Drucker** > **Standarddrucker** > **Neue Drucker hinzufügen** verfügbar.

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile--1098984---"></a>Anzeigen der Anrufer-ID im persönlichen Profil – Android Enterprise-Arbeitsprofil<!--1098984 -->
Wenn Sie ein persönliches Profil auf einem Gerät verwenden, sehen Endbenutzer möglicherweise nicht die Anrufer-ID-Details eines Arbeitskontakts. 

Seit diesem Update gibt es eine neue Einstellung unter **Android Enterprise** > **Geräteeinschränkungen** > **Arbeitsprofileinstellungen**:
- Anrufer-ID des Arbeitskontakts im persönlichen Profil anzeigen

Wenn aktiviert (nicht konfiguriert), werden die Anruferdetails des Arbeitskontakts im persönlichen Profil angezeigt. Wenn blockiert, wird die Anrufernummer des Arbeitskontakts im persönlichen Profil nicht angezeigt. 

Gilt für: Android-Arbeitsprofilgeräte unter Android OS 6.0 und höher.

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings--1102252-----from-1802-and-1804--"></a>Neue Einstellungen für Windows Defender Credential Guard in den Endpoint Protection-Einstellungen<!--1102252 --><!--from 1802 and 1804-->

Mit diesem Update enthält [Windows Defender Central Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Gerätekonfiguration** > **Profile** > **Endpoint Protection**) die folgenden Einstellungen: 

- **Windows Defender Credential Guard**: Aktivieren des Credential Guards mit virtualisierungsbasierter Sicherheit. Wenn Sie dieses Feature aktivieren, können Sie Anmeldeinformationen beim nächsten Neustart schützen, wenn **Platform Security Level with Secure Boot** (Plattformsicherheitsstufe mit sicherem Start) und **Virtualization Based Security** (Virtualisierungsbasierte Sicherheit) aktiviert sind. Zu den Optionen gehören:
  - **Deaktiviert:** Wenn Credential Guard aktiviert war, mit aktivierter Option **Ohne Sperre aktiviert**, wird Credential Guard remote deaktiviert.

  - **Mit UEFI-Sperre aktivieren**: Gewährleistet, dass Credential Guard nicht mit einem Registrierungsschlüssel oder über eine Gruppenrichtlinie deaktiviert werden kann. Wenn Sie Credential Guard nach dem Aktivieren dieser Einstellung deaktivieren möchten, müssen Sie die Gruppenrichtlinie auf „Deaktiviert“ setzen. Entfernen Sie dann die Sicherheitsfunktionen von jedem Computer mit einem anwesenden Benutzer. Durch diese Schritte werden die in der UEFI vorgenommenen Konfigurationen gelöscht. Solange die UEFI-Konfiguration bestehen bleibt, ist Credential Guard weiter aktiviert.

  - **Ohne Sperre aktivieren**: Ermöglicht, Credential Guard über eine Remoteverbindung mithilfe einer Gruppenrichtlinie zu deaktivieren. Die Geräte, die diese Einstellung verwenden, müssen Windows 10 (Version 1511) oder höher ausführen.

Die folgenden, abhängigen Technologien werden automatisch aktiviert, wenn Sie Credential Guard konfigurieren: 

- **Aktivieren der virtualisierungsbasierten Sicherheit (VBS:)** VBS wird beim nächsten Neustart aktiviert. Die virtualisierungsbasierte Sicherheit verwendet Windows Hypervisor, um die Sicherheitsdienste zu unterstützen, und erfordert einen sicheren Start.
- **Sicherer Start mit direktem Speicherzugriff (Direct Memory Access, DMA)**: Aktiviert VBS mit Schutzmaßnahmen wie sicherem Start und direktem Speicherzugriff. Für die DMA-Schutzfunktion ist Hardwaresupport erforderlich. Außerdem ist sie nur auf ordnungsgemäß konfigurierten Geräten aktiviert. 

#### <a name="use-a-custom-subject-name-on-scep-certificate---2064190---"></a>Verwenden eines benutzerdefinierten Antragstellernamens auf dem SCEP-Zertifikat<!-- 2064190 -->
Sie können den allgemeinen Namen **OnPremisesSamAccountName** für einen benutzerdefinierten Antragsteller auf einem SCEP-Zertifikatprofil verwenden. Sie können z. B. `CN={OnPremisesSamAccountName})` verwenden.

#### <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles---1098977---"></a>Blockieren von Kamera und Bildschirmaufnahmen in Android Enterprise-Arbeitsprofilen<!-- 1098977 -->
Es werden zwei neue Eigenschaften zum Blockieren beim Konfigurieren der Geräteeinschränkungen für Android-Geräte hinzugefügt: 
- Kamera: Der Zugriff auf alle Kameras auf dem Gerät wird blockiert.
- Bildschirmaufnahme: Die Bildschirmaufnahme wird blockiert,. Zudem wird verhindert, dass der Inhalt auf Anzeigegeräten angezeigt wird, die über keine sichere Videoausgabe verfügen.

Gilt für Android Enterprise-Arbeitsprofile.

#### <a name="use-cisco-anyconnect-client-for-ios---1333708---"></a>Verwenden des Cisco AnyConnect-Clients für iOS<!-- 1333708 -->

Wenn Sie ein neues VPN-Profil für iOS erstellen, stehen Ihnen jetzt zwei Optionen zur Verfügung: **Cisco AnyConnect** und **Cisco Legacy AnyConnect**. Die Cisco AnyConnect-Profile unterstützen 4.0.7x und neuere Versionen. Bereits existierende iOS Cisco AnyConnect VPN-Profile werden als **Cisco Legacy AnyConnect** bezeichnet und auch weiterhin mit Cisco AnyConnect 4.0.5x und älteren Versionen funktionieren.

> [!NOTE]
> Diese Änderung gilt nur für iOS. Es wird weiterhin nur eine Option von Cisco AnyConnect für Android- und macOS-Plattformen sowie Android Enterprise-Arbeitsprofile geben.


### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132--1734567---"></a>Neue Registrierungsschritte für Benutzer auf Geräten mit macOS High Sierra 10.13.2 und höher<!--1734567 -->
Mit macOS high Sierra 10.13.2 wurde das Konzept der „vom Benutzer genehmigten“ MDM-Registrierung eingeführt. Intune kann mithilfe genehmigter Registrierungen einige sicherheitsrelevante Einstellungen verwalten. Weitere Informationen finden Sie in der Dokumentation zur Apple-Unterstützung: https://support.apple.com/HT208019.

Geräte, die mithilfe des macOS-Unternehmensportals registriert wurden, werden so lange als „nicht vom Benutzer genehmigt“ angesehen, bis der Endbenutzer sie in den Systemeinstellungen manuell genehmigt. Dafür werden Benutzer im macOS-Unternehmensportal unter macOS 10.13.2 und höher nun direkt aufgefordert, ihre Registrierung am Ende des Registrierungsprozesses manuell zu genehmigen. Die Intune-Administratorkonsole meldet, ob ein registriertes Gerät vom Benutzer genehmigt wurde.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune---2370684---"></a>Jamf-registrierte macOS-Geräte können jetzt bei Intune registriert werden<!-- 2370684 -->
Die Versionen 1.3 und 1.4 des macOS-Unternehmensportals konnten nicht erfolgreich Jamf-Geräte bei Intune registrieren. Version 1.4.2 des macOS-Portals behebt dieses Problem.

#### <a name="updated-help-experience-in-company-portal-app-for-android---1631531---"></a>Aktualisierter Hilfebereich der Unternehmensportal-App für Android<!-- 1631531 -->
Wir haben den Hilfebereich der Unternehmensportal-App für Android aktualisiert, sodass er den Best Practices der Android-Plattform entspricht. Wenn Benutzer jetzt ein Problem in der App haben, können sie auf **Menü** > **Hilfe** tippen und Folgendes tun:
- Diagnoseprotokolle an Microsoft senden
- E-Mail, die das Problem beschreibt, und die Incident-ID an einen Supportmitarbeiter des Unternehmens senden  

Unter [Senden von Protokollen an den Support Ihres Unternehmens per E-Mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android) und [Senden von Protokollen an Unternehmensportalentwickler für Android-Geräte](/intune-user-help/send-logs-to-microsoft-android) können Sie den aktualisierten Hilfebereich kennenlernen.


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table---1471783---"></a>Neues Diagramm zum Trend von fehlgeschlagenen Registrierungen und Tabelle mit Gründen für das Fehlschlagen<!-- 1471783 -->
Auf der Seite „Enrollment Overview“ (Registrierungsübersicht) können Sie sich den Trend bei fehlgeschlagenen Registrierungen und die fünf häufigsten Gründe für das Fehlschlagen anzeigen lassen. Wenn Sie auf das Diagramm oder die Tabelle klicken, können Sie sich im Detail Informationen zu den Fehlern ansehen und erhalten Ratschläge zur Fehlerbehebung und zur Wartung.


### <a name="device-management"></a>Geräteverwaltung

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated---1629303---"></a>Advanced Threat Protection (ATP) und Intune sind vollständig integriert<!-- 1629303 -->

[Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) zeigt die Risikostufe von Windows 10-Geräten an. In Windows Defender Security Center (ATP-Portal) können Sie eine Verbindung mit Microsoft Intune herstellen. Nach der Erstellung wird mit einer Konformitätsrichtlinie von Intune eine akzeptable Bedrohungsstufe bestimmt. Wenn die Bedrohungsstufe überschritten wird, kann eine Azure Active Directory-Richtlinie (AD) für bedingten Zugriff den Zugriff auf andere Apps in Ihrer Organisation blockieren.

Dieses Feature ermöglicht ATP, Dateien zu überprüfen, Bedrohungen zu erkennen und jedes Risiko auf Ihren Windows 10-Geräten zu melden.

Weitere Informationen finden Sie unter [Aktivieren von ATP mit bedingtem Zugriff in Intune](../protect/advanced-threat-protection.md).

#### <a name="support-for-user-less-devices---1637553---"></a>Unterstützung für Geräte ohne Benutzer<!-- 1637553 -->
Intune unterstützt die Möglichkeit, Konformität auf einem benutzerlosen Gerät zu bewerten, z.B. einem Microsoft Surface Hub-Gerät. Die Konformitätsrichtlinie kann sich auf bestimmte Geräte beziehen. Die Konformität (und auch Nichtkonformität) kann für Geräte festgelegt werden, die über keinen zugewiesenen Benutzer verfügen.

#### <a name="delete-autopilot-devices---1713650---"></a>Löschen von Autopilot-Geräten<!-- 1713650 -->
Intune-Administratoren können [AutoPilot-Geräte löschen](../enrollment/enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience--1832333---"></a>Verbesserte Oberfläche für die Gerätelöschung<!--1832333 -->
Sie müssen nicht länger Unternehmensdaten entfernen oder das Gerät auf Werkseinstellungen zurücksetzen, bevor sie es [aus Intune löschen](../remote-actions/devices-wipe.md#delete-devices-from-the-intune-portal).

Melden Sie sich für die neue Benutzererfahrung in Intune an, und wählen Sie **Geräte** > **Alle Geräte** > Name des Geräts > **Löschen** aus.

Wenn Sie die Bestätigung zum Zurücksetzen bzw. der Deaktivierung beibehalten möchten, können Sie die Standardvorgehensweise für den Gerätelebenszyklus verwenden, indem Sie vor der Option **Löschen** die Optionen **Entfernen von Unternehmensdaten** und **Auf Werkseinstellungen zurücksetzen** ausgeben. 

#### <a name="play-sounds-on-ios-when-in-lost-mode---1947769---"></a>Wiedergeben von Sound im Modus für verlorene Geräte unter iOS<!-- 1947769 -->
Wenn sich überwachte iOS-Geräte im [Modus für verlorene Geräte](../remote-actions/device-lost-mode.md) in MDM (Mobile Device Management, Verwaltung mobiler Geräte) befinden, können Sie [einen Sound wiedergeben](../remote-actions/device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Geräte** > **Alle Geräte** > iOS-Gerät auswählen > **Übersicht** > **More** (Mehr)). Der Sound wird so lange wiedergegeben, bis der Modus für verlorene Geräte beendet wird, oder bis der Benutzer den Sound auf dem Gerät deaktiviert. Gilt für Geräte unter iOS 9.3 und höher.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device--1972804--"></a>Blockieren und Zulassen von Webergebnissen in auf einem Intune-Gerät durchgeführten Suchvorgängen<!--1972804-->

Administratoren können jetzt Webergebnisse bei Suchvorgängen auf Geräten blockieren.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure---2172331---"></a>Verbesserte Fehlermeldungen bei Uploadfehlern für Apple-MDM-Push-Zertifikate<!-- 2172331 -->

In der Fehlermeldung wird erklärt, dass dieselbe Apple-ID beim Erneuern eines vorhandenen MDM-Zertifikats verwendet werden muss.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines---2216679---"></a>Testen des Unternehmensportals für macOS auf virtuellen Computern<!-- 2216679 -->

Wir haben einen Leitfaden veröffentlicht, der IT-Administratoren beim Testen der Unternehmensportal-App für macOS auf VMs in Parallels Desktop und VMware Fusion unterstützt. Weitere Informationen finden Sie unter [Registrieren von virtuellen macOS-Computern zu Testzwecken](../enrollment/macos-enroll.md#enroll-virtual-macos-machines-for-testing).

### <a name="intune-apps"></a>Intune-Apps

#### <a name="user-experience-update-for-the-company-portal-app-for-ios--1412866---"></a>Update für die Benutzeroberfläche für die Unternehmensportal-App für iOS<!--1412866 -->
Für die Unternehmensportal-App für iOS wurde ein großes Update für die Benutzeroberfläche veröffentlicht. Das Update enthält eine vollständige visuelle Überarbeitung, einschließlich eines moderneren Designs und einer verbesserten Handhabung. Wir haben die Funktion der App beibehalten, haben jedoch die Benutzerfreundlichkeit und Barrierefreiheit verbessert.  

Weiterhin sind enthalten:
- Support für iPhone X
- Schnellerer App-Start und Reaktionszeiten, damit Benutzer Zeit sparen
- Zusätzliche Statusanzeigen, damit Benutzer stets mit den neuesten Statusinformationen versorgt sind
- Verbesserungen beim Uploadprozess von Protokollen. Wenn Sie also auf ein Problem stoßen, können Sie es viel einfacher melden.  

Wenn Sie sehen möchten, wie die aktualisierte Benutzeroberfläche aussieht, wechseln Sie zur Seite [Updates der Benutzeroberfläche für Benutzer-Apps in Intune](../whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca---1056954---"></a>Schützen lokaler Exchange-Daten mit Intune-App-Schutzrichtlinien und bedingtem Zugriff<!-- 1056954 -->
Sie können jetzt lokale Exchange-Daten mit Outlook Mobile mithilfe von Intune App-Schutzrichtlinien (App Policy Protection, APP) und dem bedingten Zugriff (Conditional Access, CA) schützen. Um eine App-Schutzrichtlinie im Azure-Portal hinzuzufügen oder zu ändern, wählen Sie die Option **Microsoft Intune** > **Client-Apps** > **App-Schutzrichtlinien** aus. Bevor Sie dieses Feature verwenden, sollten Sie sicherstellen, dass Sie die [Anforderungen für Outlook für iOS und Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) erfüllen.


### <a name="user-interface"></a>Benutzeroberfläche

#### <a name="improved-device-tiles-in-the-windows-10-company-portal--2213364---"></a>Verbesserte Gerätekacheln im Windows 10-Unternehmensportal<!--2213364 -->

Die Kacheln wurden aktualisiert und sind jetzt zugänglicher für Benutzer mit eingeschränktem Sehvermögen. Die Leistung wurde für Bildschirmlesetools wurde verbessert.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos---2216677---"></a>Senden von Diagnoseberichten in der Unternehmensportal-App für macOS<!-- 2216677 -->
Die Unternehmensportal-App für macOS-Geräte wurde aktualisiert, um zu verbessern, wie Benutzer mit Intune verknüpfte Fehler melden können. Ihre Mitarbeiter können über die Unternehmensportal-App folgende Aktionen durchführen:

- Hochladen von Diagnoseberichten direkt an das Microsoft-Entwicklerteam
- Die ID eines Vorfalls per E-Mail an das IT-Supportteams Ihres Unternehmens senden

Weitere Informationen finden Sie unter [Melden von macOS-Fehlern](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10---1195010---"></a>Intune passt Fluent Design System in der Unternehmensportal-App für Windows 10 an<!-- 1195010 -->
Die Intune-Unternehmensportal-App für Windows 10 wurde mit der [Navigationsansicht von Fluent Design System](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics) aktualisiert. An der Seite der App befindet sich eine statische, vertikale Liste aller Seiten der obersten Ebene. Klicken Sie auf einen beliebigen Link, um Seiten schnell anzuzeigen und zwischen ihnen zu wechseln. Dies ist das erste von mehreren Updates, die wir Ihnen im Rahmen unserer fortlaufenden Bestrebungen präsentieren werden, die Intune-Benutzeroberfläche zu optimieren. Wenn Sie sehen möchten, wie die aktualisierte Benutzeroberfläche aussieht, wechseln Sie zur Seite [Updates der Benutzeroberfläche für Benutzer-Apps in Intune](../whats-new-app-ui.md).

<!-- ########################## -->
## <a name="march-2018"></a>März 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune---748789---"></a>Benachrichtigungen zu ablaufenden branchenspezifischen iOS-Apps für Microsoft Intune<!-- 748789 -->

Im Azure-Portal werden Sie von Intune über ablaufende branchenspezifische iOS-Apps benachrichtigt. Beim Hochladen einer neuen Version der branchenspezifischen iOS-App entfernt Intune die Ablaufbenachrichtigung aus der Liste. Diese Ablaufbenachrichtigung ist nur für neu hochgeladene branchenspezifische iOS-Apps aktiviert und wird 30 Tage vor Ablauf des Bereitstellungsprofils der branchenspezifischen iOS-App angezeigt. Wenn es abgelaufen ist, ändert sich die Benachrichtigung in „Abgelaufen“.

#### <a name="customize-your-company-portal-themes-with-hex-codes--1049561---"></a>Anpassen des Unternehmensportaldesigns mit Hexadezimalcode<!--1049561 -->

Die Designfarben lassen sich in den Unternehmensportal-Apps mithilfe von Hexadezimalcode anpassen. Wenn Sie Ihren Hexadezimalcode eingeben, legt Intune fest, welche Textfarbe den stärksten Kontrast zur Hintergrundfarbe bildet. In einer Vorschau können Sie die Textfarbe und Ihr Unternehmenslogo mit den Farben unter **Client-Apps** > **Unternehmensportal** abgleichen.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise---1813081---"></a>Ein- und Ausschließen von App-Zuweisungen basierend auf Gruppen für Android Enterprise<!-- 1813081 -->

Android Enterprise (zuvor Android for Work) unterstützt das Einschließen und Ausschließen von Gruppen, jedoch nicht die vorab erstellte Gruppe **Alle Benutzer** und die integrierte Gruppe **Alle Geräte**. Weitere Informationen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](../apps/apps-inc-exl-assignments.md).


### <a name="device-management"></a>Geräteverwaltung

### <a name="export-all-devices-into-csv-files-in-ie-microsoft-edge-or-chrome---2258071---"></a>Exportieren aller Geräte in CSV-Dateien in Internet Explorer, Microsoft Edge oder Chrome<!-- 2258071 -->
Unter **Geräte** > **Alle Geräte** können Sie die Geräte mithilfe der Option **Exportieren** in eine CSV-formatierte Liste exportieren. Internet Explorer-Benutzer mit mehr als 10.000 Geräten können ihre Geräte in mehrere Dateien exportieren. Jede Datei verfügt über bis zu 10.000 Geräte.

Microsoft Edge- und Chrome-Benutzer mit mehr als 30.000 Geräten können ihre Geräte ebenfalls in mehrere Dateien exportieren. Jede Datei verfügt dann über bis zu 30.000 Geräte.

Über die Option [Geräte verwalten](../remote-actions/device-management.md) erhalten Sie weitere Informationen dazu, wie Sie die verwalteten Geräte verwenden können.

#### <a name="new-security-enhancements-in-the-intune-service----1637539---"></a>Neue Sicherheitserweiterungen für den Intune-Dienst <!-- 1637539 -->   

Wir haben in Intune in Azure eine Umschaltfläche eingeführt, mit der eigenständige Intune-Kunden Geräte ohne zugewiesene Richtlinien als **Konform** (Sicherheitsfeature deaktiviert) oder **Nicht konform** (Sicherheitsfeature aktiviert) einstufen können. So wird sichergestellt, dass erst nach der Auswertung der Gerätekonformität Zugriff auf Ressourcen besteht.

Die Auswirkungen dieses Features auf Sie sind davon abhängig, ob Sie bereits Konformitätsrichtlinien zugewiesen haben oder nicht.

- Wenn Sie über ein neues oder bereits bestehendes Konto verfügen und Ihren Geräten bislang noch keine Konformitätsrichtlinien zugewiesen sind, wird die Umschaltfläche automatisch auf **Konform** festgelegt. Das Feature ist in der Konsole standardmäßig deaktiviert. Daher hat es keine Auswirkungen auf Benutzer.
- Wenn Sie bereits ein vorhandenes Konto haben und über Geräte verfügen, denen eine Konformitätsrichtlinie zugewiesen ist, wird die Umschaltfläche automatisch auf **Nicht konform** festgelegt. Ab der Bereitstellung des März-Updates ist dieses Feature standardmäßig aktiviert.

Wenn Sie Konformitätsrichtlinien mit bedingtem Zugriff verwenden und das Feature aktiviert ist, wird jedes Gerät blockiert, dem nicht mindestens eine Konformitätsrichtlinie zugewiesen ist. Benutzern, die diesen Geräten zugeordnet sind und zuvor auf E-Mails zugreifen konnten, können dies nicht mehr, wenn Sie nicht allen Geräten mindestens eine Konformitätsrichtlinie zuweisen.   

Beachten Sie, dass der Standardstatus der Umschaltfläche ab dem Update vom März für Intune zwar in der Benutzeroberfläche angezeigt wird, jedoch nicht sofort durchgesetzt wird. Alle Änderungen, die Sie an der Einstellung der Umschaltfläche vornehmen, wirken sich nicht auf die Gerätekonformität aus, bis die Umschaltfläche für Ihr Konto aktiviert wird. Wir informieren Sie über das Nachrichtencenter, wenn dieser Vorgang abgeschlossen ist. Dies kann nach dem Update des Intune-Diensts vom März ein paar Tage dauern.

**Weitere Informationen**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection---846515---"></a>Verbesserte Erkennung von Jailbreaks<!-- 846515 -->

Die verbesserte Erkennung von Jailbreaks ist eine neue Konformitätseinstellung, die in Intune die Auswertung von Geräten mit Jailbreaks verbessert. Durch die Einstellung verbindet sich das Gerät häufiger mit Intune. Dazu wird der Ortungsdienst des Geräts benötigt, was Auswirkungen auf den Akkuverbrauch hat.

#### <a name="reset-passwords-for-android-o-devices---1238299---"></a>Zurücksetzen von Kennwörtern für Android O-Geräte<!-- 1238299 -->
Sie können die Kennwörter für registrierte Android 8.0-Geräte mit Arbeitsprofilen zurücksetzen. Wenn Sie die Anforderung „Kennwort zurücksetzen“ an ein Android 8.0-Gerät senden, legt dieses ein neues Kennwort zum Entsperren des Geräts oder eine verwaltete Profilabfrage für den aktuellen Benutzer fest. Das Kennwort oder die Abfrage wird gesendet und wird sofort wirksam.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups--1307012---"></a>Ausrichten von Konformitätsrichtlinien auf Geräte in Gerätegruppen<!--1307012 -->

Sie können Konformitätsrichtlinien gezielt für Benutzer in Benutzergruppen erstellen. Mit diesem Update können Sie auch Konformitätsrichtlinien gezielt für Geräte in Gerätegruppen erstellen. Geräte in solchen Gerätegruppen empfangen keine Konformitätsaktionen.

#### <a name="new-management-name-column---1333586---"></a>Neue Spalte „Verwaltungsname“<!-- 1333586 -->
 Im Blatt „Geräte“ ist eine neu Spalte namens **Verwaltungsname** verfügbar. Dies ist ein automatisch generierter und nicht bearbeitbarer Name, der basierend auf der folgenden Formel vom Gerät zugewiesen wird:
- Standardname für alle Geräte: <username><em><devicetype></em><enrollmenttimestamp>
- Für Geräte, die durch Massenhinzufügen hinzugefügt wurden: <PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

Dies ist eine optionale Spalte im Blatt „Geräte“. Sie ist nicht standardmäßig, sondern nur über die Spaltenauswahl verfügbar. Diese neue Spalte hat keine Auswirkungen auf den Gerätenamen.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes--1550837---"></a>Auf iOS-Geräten wird alle 15 Minuten zur Eingabe einer PIN aufgefordert<!--1550837 -->
Nachdem einem iOS-Gerät eine Konformitäts- oder Konfigurationsrichtlinie hinzugefügt wurde, werden Benutzer alle 15 Minuten dazu aufgefordert, eine PIN festzulegen. Diese Aufforderung erhalten Benutzer regelmäßig, bis sie eine PIN festlegen.

#### <a name="schedule-your-automatic-updates--1805514---"></a>Planen von automatischen Updates<!--1805514 -->
Mit Intune können Sie die Installation von automatischen Updates mithilfe von [Einstellungen für Windows-Updateringe](../protect/windows-update-for-business-configure.md) steuern. Seit diesem Update können Sie sich wiederholende Updates planen, einschließlich der Woche, dem Tag und der Uhrzeit.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate--2221763---"></a>Verwenden eines vollständig definierten Namens als Antragsteller für das SCEP-Zertifikat<!--2221763 -->
Wenn Sie ein SCEP-Zertifikatsprofil erstellen, geben Sie den Antragstellernamen ein. Seit diesem Update können Sie den vollständig definierten Namen als Antragstellernamen verwenden. Wählen Sie für **Antragstellername** die Option **benutzerdefiniert** aus, und geben Sie dann `CN={{OnPrem_Distinguished_Name}}` ein. Damit Sie die `{{OnPrem_Distinguished_Name}}`-Variable verwenden können, stellen Sie sicher, dass das `onpremisesdistingishedname`-Benutzerattribut mithilfe von [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) mit Azure AD synchronisiert ist.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="enable-bluetooth-contact-sharing---android-for-work--1098983---"></a>Aktivieren der Kontaktfreigabe über Bluetooth: Android for Work<!--1098983 -->
In der Standardeinstellung verhindert Android, dass Kontakte im Arbeitsprofil mit Bluetooth-Geräten synchronisiert werden. Das Ergebnis ist, dass Arbeitsprofilkontakte nicht auf der Anrufer-ID für Bluetooth-Geräte angezeigt werden.

Seit diesem Update gibt es eine neue Einstellung unter **Android for Work** > **Geräteeinschränkungen** > **Arbeitsprofileinstellungen**:
- Kontaktfreigabe über Bluetooth

Der Intune-Administrator kann diese Einstellungen konfigurieren, um die Freigabe zu aktivieren. Dieses Feature ist nützlich, wenn Sie ein Gerät mit einem Bluetooth-Gerät in einem Fahrzeug koppeln möchten, das die Anrufer-ID für Freisprechgeräte anzeigt. Wenn das Feature aktiviert ist, werden Arbeitsprofilkontakte angezeigt. Wenn das Feature nicht aktiviert ist, werden Arbeitsprofilkontakte nicht angezeigt.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source---1690459---"></a>Konfigurieren von Gatekeeper zum Steuern der Downloadquelle der macOS-App<!-- 1690459 -->

Sie können Gatekeeper konfigurieren und Ihre Geräte schützen, indem Sie steuern, von wo die Apps heruntergeladen werden können. Sie können die folgenden Downloadquellen konfigurieren: **Mac App Store**, **Mac App Store und verifizierte Entwickler** und **Anywhere** (Alle Quellen). Außerdem können Sie konfigurieren, dass Benutzer eine App mithilfe von STRG+Klick installieren können, um diese Gatekeeper-Steuerelemente außer Kraft zu setzen.

Diese Einstellungen finden Sie unter **Gerätekonfiguration** -> **Profil erstellen** -> **macOS** -> **Endpoint Protection**.

#### <a name="configure-the-mac-application-firewall---1690461---"></a>Konfigurieren der Firewall der Mac-Anwendung<!-- 1690461 -->

Sie können die Firewall der Mac-Anwendung konfigurieren. Damit können Sie Verbindungen auf einer „pro Anwendung“-Basis anstatt einer „per Port“-Basis steuern. Dies erleichtert es Ihnen, die Vorteile des Firewall-Schutzes zu nutzen und zu verhindern, dass unerwünschte Apps die Kontrolle über für zulässige Apps offenen Netzwerk-Ports übernehmen.

Dieses Feature kann unter **Gerätekonfiguration** -> **Profil erstellen** -> **macOS** -> **Endpoint Protection**.

Nachdem Sie die Firewall-Einstellung aktivieren, können Sie die Firewall mithilfe von zwei Strategien konfigurieren:

- Blockieren von allen eingehenden Verbindungen

   Sie können alle eingehenden Verbindungen für die Zielgeräte blockieren. Wenn Sie sich dazu entscheiden, werden eingehende Verbindungen für alle Apps blockiert.

- Zulassen oder Blockieren von bestimmten Apps

   Sie können den Empfang von eingehenden Verbindungen für bestimmte Apps zulassen oder blockieren. Sie können auch den geschützten Modus aktivieren, um zu verhindern, dass der Computer auf Suchanforderungen reagiert.

#### <a name="detailed-error-codes-and-messages---1376342---"></a>Detaillierte Fehlercodes und Meldungen<!-- 1376342 -->

In Ihrer Gerätekonfiguration werden jetzt ausführlichere Fehlercodes und Fehlermeldungen angezeigt. Diese verbesserte Berichterstellung zeigt die Einstellungen, den Status dieser Einstellungen und Details zur Problembehandlung an.

##### <a name="more-information"></a>Weitere Informationen

- Blockieren von allen eingehenden Verbindungen

   Dadurch wird verhindert, dass alle Freigabedienste (z.B. Dateifreigabe und Bildschirmfreigabe) eingehende Verbindungen empfangen. Die folgenden Systemdienste sind noch zum Empfangen von eingehenden Verbindungen zugelassen:
  - configd - implementiert DHCP und andere Netzwerkkonfigurationsservices
  - mDNSResponder - implementiert Bonjour
  - racoon: implementiert IPSec

    Stellen Sie sicher, dass **Eingehende Verbindungen** auf **Nicht konfiguriert** (und nicht auf **Block** (Blockieren)) festgelegt ist, um Freigabedienste zu verwenden.

- Geschützter Modus

   Aktivieren Sie diese Option, um den Computer daran zu hindern, auf Suchanforderungen zu reagieren. Der Computer antwortet weiterhin auf eingehende Anforderungen von autorisierten Apps. Unerwartete Anforderungen, wie z.B. ICMP (Ping), werden ignoriert.

#### <a name="disable-checks-on-device-restart--1805490---"></a>Deaktivieren von Prüfungen bei Geräteneustart<!--1805490 -->
Mit Intune können Sie die [Verwaltung von Softwareupdates](../protect/windows-update-for-business-configure.md) steuern. Seit diesem Update ist die Eigenschaft <strong>Neustartüberprüfungen</strong> verfügbar und standardmäßig aktiviert. Wählen Sie <strong>Überspringen</strong> aus, um die üblichen Überprüfungen zu überspringen, wenn Sie ein Gerät neu starten (z.B. aktive Benutzer, Akkustand usw.).

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings---1746293---"></a>Neue Windows 10-Insider-Preview-Kanäle für Bereitstellungsringe verfügbar<!-- 1746293 -->
Sie haben von nun an die Möglichkeit, zwischen den folgenden Windows 10 Insider Preview-Wartungskanälen zu wählen, wenn Sie einen Windows 10-Bereitstellungsring erstellen:
- Windows-Insider-Build: schnell
- Windows-Insider-Build: langsam
- Windows-Insider-Build veröffentlichen 

Weitere Informationen zu diesen Kanälen finden Sie unter [Verwalten von Insider Preview-Builds](https://insider.windows.com/for-business-organization-admin/).   
Weitere Informationen zum Erstellen von Bereitstellungskanälen in Intune finden Sie unter [Verwalten von Softwareupdates](../protect/windows-update-for-business-configure.md).

### <a name="new-windows-defender-exploit-guard-settings---1631893---"></a>Neue Einstellungen für Windows Defender Exploit Guard<!-- 1631893 -->

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

### <a name="intune-apps"></a>Intune-Apps

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview---710595---"></a>Azure Active Directory-Websites können die App „Intune Managed Browser“ erfordern und unterstützen das einmalige Anmelden dafür (Public Preview)<!-- 710595 -->

Mithilfe von Azure Active Directory (Azure AD) können Sie jetzt den Zugriff auf Websites auf mobilen Geräten auf die Intune Managed Browser-App beschränken. In Managed Browser bleiben die Websitedaten sicher und getrennt von den persönlichen Daten des Benutzers. Zusätzlich unterstützt der Managed Browser die Funktionen für einmaliges Anmelden für Websites, die von Azure AD geschützt werden. Das Anmelden beim Managed Browser oder das Verwenden desselben auf einem Gerät mit einer anderen App, die von Intune verwaltet wird, ermöglicht es dem Managed Browser, auf Unternehmenswebsites zuzugreifen, die von Azure AD geschützt werden, ohne dass der Benutzer seine Anmeldeinformationen eingeben muss. Diese Funktion gilt für Websites wie Outlook Web Access (OWA) und SharePoint Online sowie für andere Unternehmenswebsites wie Intranetressourcen, auf die über den Azure-App-Proxy zugegriffen wird. Weitere Informationen finden Sie unter [Zugriffsteuerung über bedingten Zugriff für Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates--976944---"></a>Unternehmensportal-App für visuelle Android-Updates<!--976944 -->

Die Unternehmensportal-App wird für Android aktualisiert, um den [Material Design](https://material.io/)-Richtlinien von Android zu entsprechen. Bilder der neuen Symbole finden Sie im Artikel zu den [Neuerungen der App-Benutzeroberfläche](../whats-new-app-ui.md).

#### <a name="company-portal-enrollment-improved---1874230-eeready--"></a>Verbesserte Unternehmensportal-Registrierung<!-- 1874230 eeready-->
Benutzer, die ein Gerät mithilfe des Unternehmensportals unter Windows 10-Version 1703 oder höher registrieren, können den ersten Registrierungsschritt jetzt innerhalb der App ausführen.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists--1725868---"></a>HoloLens und Surface Hub erscheinen nun in Gerätelisten<!--1725868 -->
Die Anzeige von über Intune registrierten HoloLens- und Surface Hub-Geräten in der Unternehmensportal-App wird jetzt unter Android unterstützt.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks---1488911---"></a>Benutzerdefinierte Buchkategorien für eBooks im Volume Purchase Program (VPP)<!-- 1488911 -->
Sie können benutzerdefinierte eBook-Kategorien erstellen und diesen dann per Volumenlizenz erworbene eBooks zuweisen. Endbenutzer können dann die neu erstellten eBook-Kategorien und den Kategorien zugewiesene Bücher sehen. Weitere Informationen finden Sie unter [Verwalten von per Volumenlizenz erworbenen Apps und Büchern mit Microsoft Intune](../apps/vpp-apps.md).  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option---2070166---"></a>Änderungen der Unterstützung der Option „Feedback senden“ in der Unternehmensportal-App für Windows<!-- 2070166 -->
Ab dem 30. April 2018 funktioniert die Option **Feedback senden** in der Unternehmensportal-App für Windows nur noch auf Geräten, auf denen das Windows 10 Anniversary Update (1607) und höher ausgeführt wird. Die Option zum Senden von Feedback wird bei Verwendung der Unternehmensportal-App für Windows unter folgenden Versionen nicht mehr unterstützt:  
- Windows 10, Version 1507  
- Windows 10, Version 1511  
- Windows Phone 8.1 

Wenn Ihr Gerät unter Windows 10 RS1 oder höher ausgeführt wird, können Sie die neueste Version der Windows-Unternehmensportal-App aus dem Store herunterladen. Bei Ausführung einer nicht unterstützten Version können Sie uns über die folgenden Kanäle weiterhin Feedback senden: 
- Die Feedback-Hub-App unter Windows 10
- E-Mail an WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings---1631890---"></a>Neue Einstellungen für Windows Defender Application Guard<!-- 1631890 -->

- **Enable graphics acceleration** (Grafikbeschleunigung aktivieren): Administratoren können einen virtuellen Grafikprozessor für Windows Defender Application Guard aktivieren. Über diese Einstellung kann die CPU Grafiken auslagern, die an die vGPU rendern. Dadurch kann die Leistung verbessert werden, wenn Sie mit grafikintensiven Websites arbeiten oder ein Video im Container ansehen.

- **SaveFilestoHost**: Administratoren können konfigurieren, dass Dateien des Browsers „Microsoft Edge“, der im Container ausgeführt wird, an das Hostdateisystem übergeben werden. Wenn Sie diese Einstellung aktivieren, können Benutzer Dateien von Microsoft Edge im Container auf das Hostdateisystem herunterladen.

#### <a name="mam-protection-policies-targeted-based-on-management-state---1665993---"></a>Anwenden von MAM-Schutzrichtlinien je nach Verwaltungsstatus<!-- 1665993 -->
Sie können MAM-Richtlinien je nach Verwaltungsstatus des Geräts anwenden:
- **Android-Geräte:** Sie können Richtlinien auf nicht verwaltete Geräte, mit Intune verwaltete Geräte und mit Intune verwaltete Android Enterprise-Profile (früher Android for Work) anwenden.
- **iOS-Geräte:** Sie können Richtlinien auf nicht verwaltete Geräte (nur MAM) oder von Intune verwaltete Geräte anwenden.

    > [!NOTE]
    > - iOS-Unterstützung für diese Funktion wird im April 2018 eingeführt.

Weitere Informationen finden Sie unter [Erstellen und Zuweisen von App-Schutzrichtlinien](../apps/app-protection-policies.md).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows---1683758---"></a>Sprachverbesserungen in der Unternehmensportal-App für Windows<!-- 1683758 -->
Die Sprache im Unternehmensportal für Windows 10 wurde verbessert und ist nun benutzerfreundlicher und unternehmensspezifischer. Unter [Updates der Benutzeroberfläche für Benutzer-Apps in Intune](../whats-new-app-ui.md) finden Sie einige Beispielabbildungen der Neuerungen.

#### <a name="new-additions-to-our-docs-about-user-privacy---1440709---"></a>Neue Ergänzungen unserer Dokumente zum Datenschutz<!-- 1440709 -->
Wir arbeiten daran, Benutzern mehr Kontrolle über ihre Daten und den Datenschutz zu geben. Daher haben wir Updates für unsere Dokumente veröffentlicht, in denen erklärt wird, wie Sie von den Unternehmensportal-Apps lokal gespeicherte Daten anzeigen und entfernen. Sie finden diese Updates in den folgenden Quellen:

- **Android:** [Entfernen der Registrierung Ihres Android-Geräts bei Intune](/intune-user-help/unenroll-your-device-from-intune-android)
- **Android, wenn der Benutzer die Nutzungsbedingungen abgelehnt hat:** [Remove your device management if you declined „Terms of Use“ (Entfernen der Geräteverwaltung, wenn die Nutzungsbedingungen abgelehnt wurden)](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android)
- **iOS:** [Entfernen Ihres iOS-Geräts aus Intune](/intune-user-help/unenroll-your-device-from-intune-ios)
- **Windows:** [Entfernen Ihres Windows-Geräts aus Intune](/intune-user-help/unenroll-your-device-from-intune-windows)

<!-- ########################## -->
## <a name="february-2018"></a>Februar 2018

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts---747685---"></a>Intune-Unterstützung für mehrere Apple DEP-/Apple School Manager-Konten<!-- 747685 -->

Intune unterstützt jetzt die Registrierung von Geräten mit bis zu 100 verschiedenen [Apple DEP-Konten](../enrollment/device-enrollment-program-enroll-ios.md) (Device Enrollment Program = Programm zur Geräteregistrierung) oder [Apple School Manager](../enrollment/apple-school-manager-set-up-ios.md)-Konten. Jedes Token kann separat für Registrierungsprofile und Geräte hochgeladen und verwaltet werden. Jedem hochgeladenen DEP-/School Manager-Token kann automatisch ein separates Registrierungsprofil zugewiesen werden. Wenn mehrere School Manager-Token hochgeladen werden, kann mit der Microsoft-Synchronisierung von Schul-/Unidaten jeweils nur ein Token freigegeben werden.

Nach der Migration funktionieren die Betaversionen der Graph-APIs und veröffentlichten Skripts zur Verwaltung von Apple DEP oder ASM über Graph nicht mehr. Neue Betaversionen der Graph-APIs sind in der Entwicklung und werden nach der Migration veröffentlicht.

#### <a name="see-enrollment-restrictions-per-user---1634444-eeready-wnready---"></a>Anzeigen von Registrierungseinschränkungen pro Benutzer<!-- 1634444 eeready wnready -->
Auf dem Blatt **Problembehandlung** sehen Sie nun die [Registrierungseinschränkungen](../enrollment/enrollment-restrictions-set.md), die für jeden Benutzer gelten, wenn Sie in der Liste **Zuweisungen** auf **Registrierungseinschränkungen** klicken.

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment---747625-eeready---"></a>Neue Option zur Benutzerauthentifizierung für die Apple-Massenregistrierung<!-- 747625 eeready -->

> [!NOTE]
> Neue Mandanten erkennen diese neue Option sofort. Für bereits vorhandene Mandanten wird dieses Feature im April eingeführt. Bis zur vollständigen Durchführung der Bereitstellung kann es sein, dass Sie noch keinen Zugriff auf diese neuen Features haben.

Mit Intune können Sie jetzt Geräte über folgende Registrierungsmethoden mit der Unternehmensportal-App authentifizieren:

- Apple-Programm zur Geräteregistrierung
- Apple School Manager
- Apple Configurator-Registrierung

Wenn Sie die Unternehmensportaloption verwenden, kann die mehrstufige Authentifizierung von Azure Active Directory erzwungen werden, ohne dass hierdurch diese Registrierungsmethoden blockiert werden.

Bei Verwendung der Unternehmensportaloption überspringt Intune die Benutzerauthentifizierung im iOS-Einrichtungsassistenten für die Registrierung mit der Benutzeraffinität. Das bedeutet, dass das Gerät zunächst als Gerät ohne Benutzer registriert wird und somit keine Konfigurationen oder Richtlinien von Benutzergruppen erhält. Es erhält nur Konfigurationen und Richtlinien für Gerätegruppen. Allerdings installiert Intune automatisch die Unternehmensportal-App auf dem Gerät. Der erste Benutzer, der die Unternehmensportal-App startet und sich bei dieser anmeldet, wird mit dem Gerät in Intune verbunden. An dieser Stelle erhält der Benutzer Konfigurationen und Richtlinien seiner Benutzergruppen. Die Benutzerzuordnung kann nur durch erneute Registrierung geändert werden.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts---747685-eeready---"></a>Intune-Unterstützung für mehrere Apple DEP-/Apple School Manager-Konten<!-- 747685 eeready -->

Intune unterstützt jetzt die Registrierung von Geräten mit bis zu 100 verschiedenen Apple DEP-Konten (Device Enrollment Program = Programm zur Geräteregistrierung) oder Apple School Manager-Konten. Jedes Token kann separat für Registrierungsprofile und Geräte hochgeladen und verwaltet werden. Jedem hochgeladenen DEP-/School Manager-Token kann automatisch ein separates Registrierungsprofil zugewiesen werden. Wenn mehrere School Manager-Token hochgeladen werden, kann mit der Microsoft-Synchronisierung von Schul-/Unidaten jeweils nur ein Token freigegeben werden.

Nach der Migration funktionieren die Betaversionen der Graph-APIs und veröffentlichten Skripts zur Verwaltung von Apple DEP oder ASM über Graph nicht mehr. Neue Betaversionen der Graph-APIs sind in der Entwicklung und werden nach der Migration veröffentlicht.

### <a name="remote-printing-over-a-secure-network---1709994----"></a>Remotedrucken über ein sicheres Netzwerk<!-- 1709994  -->
Mobile drahtlose PrinterOn-Drucklösungen ermöglichen es Benutzern, jederzeit von einem beliebigen Ort aus Druckvorgänge remote über ein sicheres Netzwerk durchzuführen. PrinterOn wird in das Intune APP SDK für iOS und Android integriert. Über das Intune-Blatt **App-Schutzrichtlinien** in der Administratorkonsole können Sie gezielt die App-Schutzrichtlinien für diese App steuern. Endbenutzer können die App „PrinterOn for Microsoft“ über den Play Store oder iTunes herunterladen, um sie innerhalb ihres Intune-Ökosystems zu nutzen.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager---1352411---"></a>Unterstützung von Registrierungen im macOS-Unternehmensportal mithilfe des Geräteregistrierungs-Managers<!-- 1352411 -->

Benutzer können jetzt den Geräteregistrierungs-Manager verwenden, wenn sie sich im macOS-Unternehmensportal registrieren.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="windows-defender-health-status-and-threat-status-reports--854704---"></a>Berichte zum Integritäts- und Bedrohungsstatus von Windows Defender<!--854704 -->

Ein grundlegendes Verständnis zur Integrität und zum Status von Windows Defender ist wichtig, damit Sie Windows-Computer verwalten können.  Mit diesem Update fügt Intune dem Status und der Integrität des Windows Defender-Agents neue Berichte und Aktionen hinzu. Wenn Sie einen Bericht zum Status des Rollups in der [Workload „Gerätekonformität“](../protect/compliance-policy-monitor.md) verwenden, werden Ihnen Geräte angezeigt, für die einer der folgenden Vorgänge erforderlich ist:
- Signaturupdate
- Neu starten
- Benutzereingriff
- vollständige Überprüfung
- andere Agent-Status, die einen Eingriff erfordern

In einem Drillthroughbericht für sämtliche Statuskategorien werden sowohl die einzelnen Computer aufgeführt, die überprüft werden sollten, als auch die, die als **Clean** (Bereinigt) eingestuft werden.

#### <a name="new-privacy-settings-for-device-restrictions--1308926---"></a>Neue Datenschutzeinstellungen für Geräteeinschränkungen<!--1308926 -->
Es sind jetzt [zwei neue Datenschutzeinstellungen](../configuration/device-restrictions-windows-10.md#privacy) für Geräte verfügbar:
- **Benutzeraktivitäten veröffentlichen:** Legen Sie diese Einstellung auf **Blockieren** fest, um geteilte Aktivitäten und die Ermittlungen von kürzlich verwendeten Ressourcen in der Programmumschaltung zu vermeiden.
- **Nur lokale Aktivitäten:** Legen Sie diese Einstellungen auf **Blockieren** fest, um geteilte Aktivitäten und Ermittlungen von kürzlich in der Programmumschaltung verwendeten Ressourcen anhand von ausschließlich lokalen Aktivitäten zu vermeiden.

#### <a name="new-settings-for-the-microsoft-edge-browser--1469166---"></a>Neue Einstellungen für den Microsoft Edge-Browser<!--1469166 -->
Für Geräte, auf denen Microsoft Edge installiert ist, sind [zwei neue Einstellungen](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser) verfügbar: **Path to favorites file** (Pfad zu häufig verwendeten Dateien) und **Changes to Favorites** (Änderungen an Favoriten).

### <a name="app-management"></a>App-Verwaltung

#### <a name="protocol-exceptions-for-applications--1035509---"></a>Protokollausnahmen für Anwendungen<!--1035509 -->

Sie können Ausnahmen für die Richtlinie zur Datenübertragung über die Verwaltung mobiler Anwendungen (MAM) mit Intune erstellen, um bestimmte nicht verwaltete Anwendungen zu öffnen. Diese Anwendungen müssen von der IT-Abteilung als vertrauenswürdig eingestuft werden. Entgegen der von Ihnen erstellten Ausnahmen ist die Datenübertragung immer noch auf Anwendungen beschränkt, die von Intune verwaltet werden, wenn Ihre Richtlinie zur Datenübertragung immer noch auf **managed apps only** (nur verwaltete Apps) festgelegt ist. Sie können die Einschränkungen mithilfe von Protokollen (unter iOS) oder Paketen (unter Android) erstellen.

Sie können beispielsweise das Webex-Paket als Ausnahme für die Richtlinie zur MAM-Datenübertragung hinzufügen. Dann ist es erlaubt, Webex-Links in einer verwalteten Outlook-E-Mail direkt über die Webex-Anwendung zu öffnen. In anderen nicht verwalteten Anwendungen ist die Datenübertragung dann aber immer noch eingeschränkt. Weitere Informationen finden Sie unter [Ausnahmen von der Datenübertragungsrichtlinie für Apps](../apps/app-protection-policies-exception.md).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results---1469193---"></a>Mit Windows Information Protection (WIP) verschlüsselte Daten in Windows-Suchergebnissen<!-- 1469193 -->
Mit einer neuen Einstellung in der WIP-Richtlinie (Windows Information Protection) können Sie nun steuern, ob mit WIP verschlüsselte Daten in den Windows-Suchergebnissen enthalten sind. Legen Sie diese App-Schutzrichtlinienoption auf **Der Windows Search-Indexerstellung die Suche nach verschlüsselten Elementen gestatten** in den **Erweiterten Einstellungen** der Windows Information Protection-Richtlinie fest. Die App-Schutzrichtlinie muss auf die *Windows 10*-Plattform und die App-Richtlinie **Registrierungsstatus** auf **Mit Registrierung** festgelegt werden. Weitere Informationen finden Sie unter [Der Windows Search-Indexerstellung die Suche nach verschlüsselten Elementen gestatten](../apps/windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app---1740840---"></a>Konfigurieren einer mobilen MSI-App, die sich selbst aktualisiert<!-- 1740840 -->
Sie können eine bekannte mobile MSI-App konfigurieren, die sich selbst aktualisiert, um den Prozess der Versionsüberprüfung zu ignorieren. Diese Einstellung ist nützlich, um Racebedingungen zu vermeiden. Diese Art von Racebedingungen kann z.B. auftreten, wenn die App vom Entwickler automatisch aktualisiert wird, gleichzeitig aber auch von Intune ein Update ausgeführt wird. Beide könnten dann eine Version der App auf dem Windows-Client erzwingen, was einen Konflikt auslösen kann. Für diese automatisch aktualisierten MSI-Apps können Sie die Einstellung **App-Version ignorieren** auf dem Blatt **App-Informationen** konfigurieren. Wenn diese Einstellung auf **Ja** festgelegt wird, ignoriert Microsoft Intune die App-Version, die auf dem Windows-Client installiert ist.

#### <a name="related-sets-of-app-licenses-supported-in-intune---1864117---"></a>Verwandte App-Lizenzen, die in Intune unterstützt werden<!-- 1864117 -->
Intune im App-Portal unterstützt nun verwandte App-Lizenzen als einzelne App-Elemente auf der Benutzeroberfläche. Außerdem werden alle offline lizenzierten Apps, die aus dem Microsoft Store für Unternehmen synchronisiert werden, in einem einzelnen App-Eintrag konsolidiert, und jegliche Bereitstellungsdetails aus den einzelnen Paketen werden in einen einzelnen Eintrag migriert. Wenn Sie verwandte App-Lizenzen im Azure-Portal abrufen möchten, klicken Sie im Azure-Portal auf der Seite **Client-Apps** auf **App-Lizenzen**.

### <a name="device-configuration"></a>Gerätekonfiguration
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption---1463582---"></a>Dateierweiterungen für die automatische Verschlüsselung in Windows Informationen Protection (WIP)<!-- 1463582 -->
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

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies--1704133--"></a>Ergänzungen zu den Konformitätsrichtlinien für die Systemsicherheitseinstellungen für Windows 10 und höher<!--1704133-->

Es sind nun Ergänzungen zu den Konformitätsrichtlinien für Windows 10 verfügbar. Z.B. sind eine Firewall und Windows Defender Antivirus erforderlich.

### <a name="intune-apps"></a>Intune-Apps

#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business--1222672--"></a>Unterstützung für Offline-Apps aus dem Microsoft Store für Unternehmen<!--1222672-->
Offline-Apps, die Sie über den Microsoft Store für Unternehmen erworben haben, werden nun mit dem Azure-Portal synchronisiert. Sie können diese Apps für Geräte- oder Benutzergruppen bereitstellen. Offline-Apps werden durch Intune und nicht durch den Store installiert.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile---1728700---"></a>Verhindern, dass Endbenutzer manuell Konten zum Arbeitsprofil hinzufügen oder daraus entfernen<!-- 1728700 -->

Wenn Sie die Gmail-App in einem Android for Work-Profil bereitstellen, können Sie mit der Einstellung **Konten hinzufügen und entfernen** im Android for Work-Geräteeinschränkungsprofil verhindern, dass Benutzer Konten im Arbeitsprofil manuell hinzufügen oder daraus entfernen.

<!-- ########################## -->
## <a name="january-2018"></a>Januar 2018

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire---1639263---"></a>Warnungen für abgelaufene und in Kürze ablaufende Token<!-- 1639263 -->
Auf der Übersichtsseite werden jetzt Warnungen für abgelaufene und in Kürze ablaufende Token angezeigt. Wenn Sie auf eine Warnung für ein einzelnes Token klicken, navigieren Sie zur Detailseite des Tokens.  Wenn Sie auf eine Warnung mit mehreren Token klicken, werden Sie zu einer Liste aller Token mit dem jeweiligen Status weitergeleitet. Administratoren sollten ihre Token vor dem Ablaufdatum verlängern.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="remote-erase-command-support-for-macos-devices---1438084---"></a>Unterstützung des Remotebefehls „Löschen“ für macOS-Geräte<!-- 1438084 -->

Administratoren können remote den Befehl „Löschen“ für macOS-Geräte auslösen.

> [!IMPORTANT]
> Der Löschbefehl kann nicht zurückgesetzt werden und sollte mit Bedacht angewendet werden.

Der Löschbefehl entfernt alle Daten von einem Gerät, einschließlich des Betriebssystems. Zusätzlich wird dabei auch das Gerät aus der Intune-Verwaltung entfernt. Es erfolgt keine Warnung gegenüber dem Benutzer und die Löschung erfolgt unmittelbar nach Ausgabe des Befehls.

Sie müssen eine 6-stellige PIN für die Wiederherstellung konfigurieren. Mit dieser PIN kann das gelöschte Gerät entsperrt werden, woraufhin die erneute Installation des Betriebssystems beginnt. Nach dem Starten des Löschvorgangs wird die PIN in einer Statusleiste auf dem Übersichtsblatt des Geräts in Intune angezeigt. Die PIN bleibt für die Dauer der Löschung bestehen. Nach der Löschung verschwindet das Gerät vollständig aus der Intune-Verwaltung. Dokumentieren Sie die Wiederherstellungs-PIN, damit sie jedem, der das Gerät wiederherstellt, zur Verfügung steht.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token---820870---"></a>Widerrufen von Lizenzen für ein iOS Volume Purchase Program-Token<!-- 820870 -->
Sie können die Lizenz für alle iOS VPP-Apps (Volume Purchase Program) für ein bestimmtes VPP-Token widerrufen.

### <a name="app-management"></a>App-Verwaltung

#### <a name="revoking-ios-volume-purchase-program-apps----820863---"></a>Widerrufen von Apps aus dem iOS Volume Purchase Program <!-- 820863 -->
Für ein bestimmtes Gerät, das mindestens eine iOS VPP-App (Volume Purchase Program) enthält, können Sie die zugehörige gerätebasierte App-Lizenz für das Gerät widerrufen. Durch das Widerrufen einer App-Lizenz wird die zugehörige VPP-App nicht vom Gerät deinstalliert. Zum Deinstallieren einer VPP-App müssen Sie die Zuweisungsaktion in **Deinstallieren** ändern. Weitere Informationen finden Sie unter [Verwalten von iOS-Apps, die über ein Volumenprogramm mit Microsoft Intune erworben wurden](../apps/vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type---1332318---"></a>Zuweisen von mobilen Office 365-Apps an iOS- und Android-Geräte mithilfe des integrierten App-Typs<!-- 1332318 -->
Der **integrierte** App-Typ erleichtert, Office 365-Apps für die iOS- und Android-Geräte, die Sie verwalten, zu erstellen und sie diesen zuzuweisen. Zu diesen Apps gehören Office 365-Apps wie Word, Excel, PowerPoint und OneDrive. Sie können bestimmte Apps dem App-Typen zuweisen und die Konfiguration der App-Informationen bearbeiten.

#### <a name="including-and-excluding-app-assignment-based-on-groups---1406920---"></a>Ein- und Ausschließen von App-Zuweisungen basierend auf Gruppen<!-- 1406920 -->

Bei der App-Zuweisung und nach der Auswahl eines Zuweisungstyps können Sie die ein- und auszuschließenden Gruppen auswählen.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments----1480316---"></a>Sie können eine Anwendungskonfigurationsrichtlinie Gruppen zuweisen, indem Sie Zuweisungen ein- und ausschließen. <!-- 1480316 -->

Sie können einer Gruppe von Benutzern und Geräten mithilfe einer Kombination von Ein- und Ausschlusszuweisungen eine Anwendungskonfigurationsrichtlinie zuweisen. Zuweisungen können entweder als eine benutzerdefinierte Auswahl von Gruppen oder virtuelle Gruppe ausgewählt werden. Eine virtuelle Gruppe kann entweder **Alle Benutzer**, **Alle Geräte** oder **Alle Benutzer und alle Geräte** einschließen.

#### <a name="support-for-windows-10-edition-upgrade-policy-----903672archived-1119689---"></a>Unterstützung für die Windows 10-Editionsupgrade-Richtlinie  <!-- 903672(archived), 1119689 -->  
Durch das Erstellen einer Windows 10-Editionsupgraderichtlinie können Sie für Windows 10-Geräte ein Upgrade auf folgende Betriebssysteme durchführen: Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education und Windows 10 Professional Education N. Weitere Informationen zu Windows 10-Editionsupgrades finden Sie unter [Konfigurieren von Windows 10-Editionsupgrades](../configuration/edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal----1737088-1634311---"></a>Ausschließliche Verfügbarkeit von Richtlinien für den bedingten Zugriff für Intune über das Azure-Portal <!-- 1737088 1634311 -->

Ab diesem Release müssen Sie Ihre Richtlinien für den bedingten Zugriff über das [Azure-Portal](https://portal.azure.com) unter **Azure Active Directory** > **Bedingter Zugriff** konfigurieren und verwalten. Der Einfachheit halber können Sie dieses Blatt auch über **Intune** > **Bedingter Zugriff** im Azure-Portal aufrufen.

#### <a name="updates-to-compliance-emails--1637547---"></a>Updates für Konformitäts-E-Mails<!--1637547 -->

Wenn eine E-Mail zur Meldung eines nicht konformen Geräts gesendet wird, werden Details über das nicht konforme Gerät einbezogen.

### <a name="intune-apps"></a>Intune-Apps

#### <a name="new-functionality-for-the-resolve-action-for-android-devices--1583480--"></a>Neue Funktionen für die Aktion „Auflösen“ für Android-Geräte<!--1583480-->

Die Unternehmensportal-App für Android erweitert die Aktion „Lösung“ für **Geräteeinstellungen aktualisieren**, um [Verschlüsselungsprobleme bei Geräten](/intune-user-help/encrypt-your-device-android) zu lösen.

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10--676506--"></a>Remote-Sperre in der Unternehmensportal-App für Windows 10 verfügbar<!--676506-->
Endbenutzer können Ihre Geräte jetzt über die Unternehmensportal-App für Windows 10 über eine Remoteverbindung sperren. Dies wird nicht für das lokale Gerät angezeigt, dass sie aktiv verwenden.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10--676546--"></a>Einfachere Behebung von Konformitätsfehlern für die Unternehmensportal-App für Windows 10<!--676546-->
Endbenutzer mit Windows-Geräten können in der Unternehmensportal-App auf den Grund der Nichtkonformität tippen. Wenn möglich werden sie direkt an den korrekten Ort in der Einstellungs-App geleitet, um das Problem zu beheben.

<!-- ########################## -->
## <a name="december-2017"></a>Dezember 2017

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="new-automatic-redeployment-setting---1469168---"></a>Neue Einstellung für die automatische erneute Bereitstellung<!-- 1469168 -->
Die Einstellung **Automatische erneute Bereitstellung** ermöglicht es Benutzern mit Administratorrechten, alle Benutzerdaten und -einstellungen über **STRG+Windows+R** vom Sperrbildschirm des Geräts aus zu löschen. Das Gerät wird automatisch neu konfiguriert und bei der Verwaltung neu registriert. Diese Einstellung finden Sie unter „Windows 10“ > „Geräteeinschränkungen“ > „Allgemein“ > „Automatische erneute Bereitstellung“. Weitere Informationen finden Sie unter [Einstellungen für Geräteeinschränkungen für Windows 10 in Intune](../configuration/device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy----903672--1119689---"></a>Unterstützung für zusätzliche Quelleditionen in der Windows 10-Editionsupgrade-Richtlinie <!-- 903672,  1119689 -->
Sie können jetzt die Windows 10-Editionsupgraderichtlinie verwenden, um ein Upgrade von zusätzlichen Windows 10-Editionen (Windows 10 Pro, Windows 10 Pro for Education, Windows 10 Cloud, usw.) durchzuführen. Vor dieser Version waren die Upgradepfade für die unterstützten Editionen stärker eingeschränkt. Einzelheiten finden Sie unter [Konfigurieren von Windows 10-Editionsupgrades in Microsoft Intune](../configuration/edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings---1335507---"></a>Neue Einstellungen des WDSC-Gerätekonfigurationsprofils (Windows Defender Security Center)<!-- 1335507 -->

Unter dem Endpunktschutz namens **Windows Defender Security Center** fügt Intune einen neuen Abschnitt mit Einstellungen des Gerätekonfigurationsprofils hinzu. IT-Administratoren können konfigurieren, welche Komponenten der Windows Defender Security Center-App für Endbenutzer zugänglich sind. Wenn ein IT-Administrator eine Komponente in der Windows Defender Security Center-App ausblendet, werden Benachrichtigungen in Zusammenhang mit der ausgeblendeten Komponente nicht auf dem Gerät des Benutzers angezeigt.

Folgende Komponenten können von Administratoren aus den Einstellungen des Gerätekonfigurationsprofils von Windows Defender Security Center ausgeblendet werden:
- Viren- und Bedrohungsschutz
- Geräteleistung und -integrität
- Firewall- und Netzwerkschutz
- App- und Browsersteuerung
- Familienoptionen

IT-Administratoren können auch anpassen, welche Benutzer Benachrichtigungen empfangen können. Beispielsweise können Sie konfigurieren, ob Benutzer alle von sichtbaren Komponenten in WDSC generierten Benachrichtigungen oder nur kritische Benachrichtigungen erhalten. Zu nicht kritischen Benachrichtigungen gehören regelmäßige Zusammenfassungen von Windows Defender Antivirus-Aktivitäten und Benachrichtigungen bei Abschluss von Überprüfungen. Alle übrigen Benachrichtigungen gelten als kritisch. Darüber hinaus können Sie auch den Inhalt der Benachrichtigung anpassen. Beispielsweise können Sie die IT-Kontaktinformationen angeben, um sie in die Benachrichtigungen einzubetten, die auf den Geräten der Benutzer angezeigt werden.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling---1361755---"></a>Unterstützung für mehrere Connectors für die Behandlung von SCEP- und PFX-Zertifikaten<!-- 1361755 -->

Kunden, die den lokalen NDES-Connector zum Übermitteln von Zertifikaten an Geräte verwenden, können ab sofort mehrere Connectors in einem einzelnen Mandanten konfigurieren.

Diese neue Funktion unterstützt das folgende Szenario:

- **Hochverfügbarkeit**

Jeder NDES-Connector bezieht Zertifikatanforderungen mithilfe von Pull von Intune.  Wenn ein NDES-Connector offline geschaltet wird, kann der andere Connector weiterhin Anforderungen verarbeiten.

#### <a name="customer-subject-name-can-use-aad_device_id-variable----1468599---"></a>Möglichkeit zur Verwendung der Variable AAD_DEVICE_ID im benutzerdefinierten Antragstellernamen <!-- 1468599 -->

Wenn Sie ein SCEP-Zertifikatprofil in Intune erstellen, können Sie beim Erstellen des benutzerdefinierten Antragstellernamens ab sofort die Variable AAD_DEVICE_ID verwenden.   Wenn das Zertifikat mithilfe dieses SCEP-Profils angefordert wird, wird die Variable durch die AAD-Geräte-ID des Geräts ersetzt, das die Zertifikatsanforderung ausführt.


### <a name="device-management"></a>Geräteverwaltung

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine---1592747---"></a>Verwalten von über Jamf registrierten macOS-Geräten mit der Gerätekonformitäts-Engine von Intune<!-- 1592747 -->
Ab sofort können Sie mit Jamf Informationen über den macOS-Gerätezustand an Intune senden. Dort werden sie im Hinblick auf Konformität mit den Richtlinien ausgewertet, die in der Intune-Konsole definiert sind. Basierend auf dem Konformitätszustand des Geräts und anderen Bedingungen (z. B. Standort, Benutzerrisiko usw.) wird die Konformität für macOS-Geräte, die auf mit Azure AD verbundene Cloudanwendungen und lokale Anwendungen zugreifen (einschließlich Office 365) mithilfe des bedingten Zugriffs erzwungen. Erfahren Sie mehr über die [Einrichtung der Jamf-Integration](../protect/conditional-access-integrate-jamf.md) und [Erzwingung der Konformität für Jamf-verwaltete Geräte](../protect/conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action-----1424701---"></a>Neue iOS-Geräteaktion  <!-- 1424701 -->

Sie können nun überwachte iOS 10.3-Geräte herunterfahren. Diese Aktion fährt das Gerät sofort und ohne Warnung für den Endbenutzer herunter. Die Aktion **Herunterfahren (nur überwacht)** finden Sie in den Geräteeigenschaften bei der Auswahl eines Geräts in der Workload **Gerät**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices---1468103---"></a>Verhindern von Änderungen an Datum/Uhrzeit bei Samsung KNOX-Geräten<!-- 1468103 -->

Wir haben ein neues Feature hinzugefügt, mit dem Sie Datums- und Zeitänderungen auf Samsung KNOX-Geräten blockieren können. Sie finden dieses unter **Gerätekonfigurationsprofile** > **Geräteeinschränkungen (Android)** > **Allgemein**.

#### <a name="surface-hub-resource-account-supported---1566442----"></a>Unterstützung für Surface Hub-Ressourcenkonto<!-- 1566442  -->

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

#### <a name="install-office-apps-on-macos-devices---1494311---"></a>Installieren von Office-Apps auf macOS-Geräten<!-- 1494311 -->
Sie können nun Office-Apps auf macOS-Geräten installieren. Dieser neue App-Typ ermöglicht Ihnen die Installation von Word, Excel, PowerPoint, Outlook und OneNote. Diese Apps sind auch im Lieferumfang von Microsoft AutoUpdate (MAU) enthalten, um Ihre Apps sicher und auf dem neuesten Stand zu halten.

### <a name="app-management"></a>App-Verwaltung

#### <a name="delete-an-ios--volume-purchasing-program-token---820879---"></a>Löschen eines iOS Volume Purchase Program-Tokens<!-- 820879 -->
Sie können das iOS-VPP-Token (Volume Purchase Program) über die Konsole löschen. Dies kann erforderlich sein, wenn doppelte Instanzen eines VPP-Tokens vorliegen.

### <a name="intune-apps"></a>Intune-Apps


### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data---1667026---"></a>Eine neue Entitätssammlung namens „Aktueller Benutzer“ ist auf die Daten der momentan aktiven Benutzer beschränkt<!-- 1667026 -->

Die Entitätssammlung **Benutzer** listet alle Benutzer von Azure Active Directory (Azure AD) mit zugewiesenen Lizenzen in Ihrem Unternehmen auf. Beispielsweise kann ein Benutzer in Intune hinzugefügt und dann im Verlauf des letzten Monats entfernt worden sein. Auch wenn dieser Benutzer zum Zeitpunkt der Berichterstellung nicht vorhanden ist, liegen Angaben zu Benutzer und Zustand in den Daten vor. Sie können einen Bericht erstellen, der die Dauer der Präsenz des Benutzers in Ihren Daten zeigt.

Im Gegensatz dazu enthält die neue Entitätssammlung **Aktueller Benutzer** nur Benutzer, die nicht entfernt wurden. Die Entitätssammlung **Aktueller Benutzer** enthält nur die derzeit aktiven Benutzer. Informationen zur Entitätssammlung **Aktueller Benutzer** finden Sie unter [Referenz für die Entität „Aktueller Benutzer“](../developer/reports-ref-data-model.md).

### <a name="updated-graph-apis---1736360---"></a>Aktualisierte Graph-APIs<!-- 1736360 -->

In diesem Release haben wir einige der Graph-APIs für Intune aktualisiert, die sich in der Betaphase befinden. Weitere Informationen finden Sie im monatlichen [Graph-API-Änderungsprotokoll](https://developer.microsoft.com/graph/docs/concepts/changelog).

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="intune-supports-windows-information-protection-wip-denied-apps---1479103---"></a>Intune unterstützt WIP-abgelehnte Apps (Windows Information Protection)<!-- 1479103 -->
Sie können abgelehnte Apps in Intune festlegen. Wenn eine App abgelehnt wird, wird ihr der Zugriff auf Unternehmensinformationen verweigert. Sie ist also genau das Gegenteil einer zugelassenen App. Weitere Informationen finden Sie unter [AppLocker-CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection).

<!-- ########################## -->
## <a name="november-2017"></a>November 2017

### <a name="troubleshoot-enrollment-issues----746324---"></a>Behandlung von Problemen bei der Registrierung <!-- 746324 -->

Im Arbeitsbereich **Problembehandlung** werden nun Probleme der Benutzer bei der Registrierung angezeigt. Die Details zum Problem und die vorgeschlagenen Abhilfemaßnahmen können Administratoren und Helpdeskmitarbeiter bei der Behandlung von Problemen unterstützen. Bestimmte Probleme bei der Registrierung werden nicht erfasst, und für einige Fehler liegen möglicherweise keine Wiederherstellungsvorschläge vor.

### <a name="group-assigned-enrollment-restrictions---747598---"></a>Gruppen zugeordnete Registrierungseinschränkungen<!-- 747598 -->

Als Intune-Administrator können Sie nun [benutzerdefinierte Registrierungsbeschränkungen für Gerätetypen und -limits für Benutzergruppen erstellen](../enrollment/enrollment-restrictions-set.md).

Im Intune Azure-Portal können Sie bis zu 25 Instanzen für jeden Beschränkungstyp erstellen, die Sie anschließend Benutzergruppen zuordnen können. Gruppen zugeordnete Beschränkungen setzen die Standardbeschränkungen außer Kraft.

Sämtliche Instanzen eines Beschränkungstypen werden in einer Liste mit einer strengen Reihenfolge verwaltet. Diese Reihenfolge definiert einen Prioritätswert für die Lösung von Konflikten. Ein Benutzer, der von mehr als einer Beschränkungsinstanz betroffen ist, wird nur von der Instanz mit dem höchsten Prioritätswert eingeschränkt. Sie können die Priorität einer vorhandenen Instanz ändern, indem Sie sie an eine andere Stelle in der Liste ziehen.

Diese Funktion wird mit der Migration von Android for Work-Einstellungen aus dem Android for Work-Registrierungsmenü in das Registrierungsmenü freigegeben. Da diese Migration einige Tage in Anspruch nehmen kann, wird Ihr Konto möglicherweise auf andere Teile des Releases im November aktualisiert, bevor die Gruppenzuweisung für Registrierungsbeschränkungen aktiviert ist.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors---1528104---"></a>Unterstützung mehrerer Connectors für den Registrierungsdienst für Netzwerkgeräte (NDES)<!-- 1528104 -->

Über den Registrierungsdienst für Netzwerkgeräte (Network Device Enrollment Service NDES) können Mobilgeräte, die ohne Domänen-Anmeldeinformationen ausgeführt werden, Zertifikate auf Basis des Simple Certificate Enrollment-Protokolls (SCEP) abrufen.
Mit diesem Update werden mehrere NDES-Connectors unterstützt.

### <a name="manage-android-for-work-devices-independently-from-android-devices---1490731-eeready--"></a>Verwalten von Android for Work-Geräten unabhängig von Android-Geräten<!-- 1490731 EEready-->

Intune unterstützt das Verwalten von Registrierungen von Android for Work-Geräten unabhängig von der Android-Plattform. Diese Einstellungen werden unter **Geräteregistrierung** > **Registrierungsbeschränkungen** > **Gerätetypbeschränkungen** verwaltet. (Zuvor waren sie unter **Geräteregistrierung** > **Android for Work-Registrierung** > **Android for Work-Registrierungseinstellungen** zu finden.)

Standardmäßig ändern sich die Android for Work-Geräteeinstellungen gegenüber Ihren Android-Geräteeinstellungen nicht. Dies ändert sich allerdings, nachdem Sie ihre Android for Work-Einstellungen geändert haben.

Wenn Sie die private Android for Work-Registrierung blockieren, können sich nur unternehmenseigene Android-Geräte als Android for Work-Geräte registrieren.

Ziehen Sie Folgendes in Betracht, wenn Sie mit den neuen Einstellungen arbeiten:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Wenn Sie die Android for Work-Registrierung zuvor noch nie integriert haben

Die neue Android for Work Plattform wird in den Standardgerätetypbeschränkungen blockiert. Nachdem Sie die Funktion integriert haben, können Sie zulassen, dass sich Geräte mit Android for Work registrieren. Ändern Sie dafür die Standardeinstellungen, oder erstellen Sie eine neue Gerätetypbeschränkung, um die Standardgerätetypbeschränkungen zu ersetzen.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Wenn Sie die Android for Work-Registrierung bereits integriert haben

Wenn Sie zuvor bereits eine Integration vorgenommen haben, hängt Ihre Situation von den von Ihnen ausgewählten Einstellungen ab:

| Einstellung | Android for Work-Status in den Standardgerätetypbeschränkungen | Hinweise |
| --- | --- | --- |
| **Alle Geräte als Android-Geräte verwalten** | Gesperrt | Alle Android-Geräte müssen sich ohne Android for Work registrieren. |
| **Unterstützte Geräte als Android for Work-Geräte verwalten** | Zugelassen | Alle Android-Geräte, die Android for Work unterstützen, müssen sich mit Android for Work registrieren. |
| **Nur unterstützte Geräte für Benutzer in diesen Gruppen als Android for Work-Geräte verwalten** | Gesperrt | Eine separate Richtlinie für Gerätetypbeschränkungen wurde erstellt, um die Standareinstellungen außer Kraft zu setzen. Diese Richtlinie definiert die Gruppen, für die Sie zuvor die Android for Work-Registrierung zugelassen haben. Benutzer der ausgewählten Gruppen dürfen ihre Android for Work-Geräte weiterhin registrieren. Alle anderen Benutzer können sich nicht mit Android for Work registrieren. |

In beiden Fällen wird die von Ihnen vorgesehene Regulierung beibehalten. Von Ihrer Seite ist kein weiterer Vorgang erforderlich, um die globalen oder gruppenbedingten Zulassungen von Android for Work in Ihrer Umgebung zu verwalten.

### <a name="google-play-protect-support-on-android---908720---"></a>Unterstützung für Google Play Protect unter Android<!-- 908720 -->

Mit der Version Android Oreo führt Google eine Suite von Sicherheitsfunktionen namens „Google Play Protect“ ein, mit denen Benutzer und Organisationen Apps und Android-Images sicher ausführen können. Intune unterstützt jetzt Google Play Protect-Features, einschließlich des SafetyNet-Remotenachweises. Administratoren können Konformitätsrichtlinienanforderungen festlegen, für die Google Play Protect konfiguriert sein und sich in einem fehlerfreien Zustand befinden muss.
Für die Verwendung der Einstellung **SafetyNet-Gerätenachweis** muss das Gerät eine Verbindung mit einem Google-Dienst herstellen, damit sichergestellt ist, dass sich das Gerät in einem fehlerfreien Zustand befindet und es nicht beeinträchtigt ist. Administratoren können zudem eine Konfigurationsprofileinstellung für Android for Work festlegen, um zu erfordern, dass installierte Apps von Google Play-Diensten überprüft werden. Wenn ein Gerät nicht mit den Anforderungen von Google Play Protect konform ist, können Benutzer durch den bedingten Zugriff daran gehindert werden, auf Unternehmensressourcen zuzugreifen.

- Siehe [Informationen zum Erstellen einer Gerätekonformitätsrichtlinie zum Aktivieren von Google Play Protect](../protect/compliance-policy-create-android.md).

### <a name="text-protocol-allowed-from-managed-apps---1414050----"></a>Zulässige Textprotokolle verwalteter Apps<!-- 1414050  -->

Apps, die über das Intune App SDK verwaltet werden, können SMS-Nachrichten versenden.


### <a name="app-install-report-updated-to-include-install-pending-status---1249446---"></a>App-Installationsbericht mit dem Status „Installation steht aus“ aktualisiert<!-- 1249446 -->  

Der Bericht über den **Installationsstatus der App**, der in jeder App über die **App**-Liste in der Workload **Client-Apps** verfügbar ist, enthält nun für Benutzer und Geräte die Angabe **Installation steht aus** samt Anzahl.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection---1391759---"></a>App-Bestand-API zur Bedrohungserkennung auf Mobilgeräten unter iOS 11<!-- 1391759 -->

Intune erfasst sowohl von privaten als auch von unternehmenseigenen Geräten Informationen zum App-Bestand und stellt diese für Anbieter von Bedrohungserkennung auf Mobilgeräten (Mobile Thread Detection, MTD) wie Lookout for Work zur Verfügung. Sie können Informationen zum App-Bestand auf iOS 11-Geräten (oder höher) erfassen.

**App-Bestand**  
Die Bestände von sowohl unternehmenseigenen als auch privaten iOS 11-Geräten (oder höher) werden an Ihren MTD-Dienstanbieter übermittelt. Die Daten in den App-Beständen umfassen:

- App-ID
- App-Version
- Kurzversion der App
- App-Name
- Größe des App-Pakets
- Dynamische Größe der App
- App wird geprüft oder nicht
- App wird verwaltet oder nicht

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone---1463747-wnready---"></a>Migrieren von Benutzern und Geräten in einer MDM-Hybridlösung zu eigenständigem Intune<!-- 1463747 wnready -->
Der Prozess und die Tools zum Verschieben von Benutzern und deren zugehörigen Geräten aus hybridem MDM nach Intune im Azure-Portal sind jetzt verfügbar. Sie können daher jetzt folgende Aufgaben durchführen:
- Sie können Richtlinien und Profile aus der Configuration Manager-Konsole nach Intune im Azure-Portal verschieben.
- Sie können einen Teil der Benutzer nach Intune im Azure-Portal verschieben und den anderen Teil im hybriden MDM belassen.
- Sie können Geräte zu Intune im Azure-Portal migrieren, ohne erneut eine Registrierung durchführen zu müssen.

Ausführlichere Angaben finden Sie unter [Migrieren von Benutzern und Geräten in einer MDM-Hybridlösung zu eigenständigem Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

### <a name="on-premises-exchange-connector-high-availability-support----676614---"></a>Hochverfügbarkeitsunterstützung für lokalen Exchange Connector <!-- 676614 -->
Nachdem der Exchange Connector mit dem angegebenen Clientzugriffsserver (CAS) eine Verbindung mit Exchange hergestellt hat, weist der Connector nun die Möglichkeit zur Ermittlung anderer CAS auf. Wenn der primäre CAS nicht mehr verfügbar ist, wird für den Connector ggf. ein Failover auf einen anderen CAS durchgeführt, bis der primäre CAS verfügbar wird. Einzelheiten finden Sie unter [Hochverfügbarkeitsunterstützung für lokalen Exchange Connector](../protect/exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support).

### <a name="remotely-restart-ios-device-supervised-only---1424595---"></a>Remote-Neustart von iOS-Geräten (nur überwacht)<!-- 1424595 -->

Sie können nun bei einem überwachten iOS 10.3-Gerät (und höher) über eine Geräteaktion einen Neustart auslösen. Weitere Informationen zum Geräteneustart finden Sie unter [Remotely restart devices with Intune (Remote-Neustart von Geräten mit Intune)](../remote-actions/device-restart.md).

> [!Note]
> Für diesen Befehl wird ein überwachtes Gerät und das Zugriffsrecht **Gerätesperre** benötigt. Das Gerät wird sofort neu gestartet. Kennungsgeschützte iOS-Geräte verbinden Sie nach dem Neustart nicht wieder mit dem WLAN-Netzwerk und können unter Umständen nicht mehr mit dem Server kommunizieren.

### <a name="single-sign-on-support-for-ios---1333645---"></a>Unterstützen des einmaligen Anmeldens (Single Sign-On, SSO) für iOS<!-- 1333645 -->  

Sie können SSO für iOS-Benutzer verwenden. Die iOS-Apps, die so programmiert wurden, dass sie nach Benutzeranmeldeinformationen in der Payload für einmaliges Anmelden suchen, sind mit diesem Payload-Konfigurationsupdate weiterhin funktionsfähig. Sie können auch den UPN und die Intune-Geräte-ID verwenden, um den Prinzipalnamen und den Bereich zu identifizieren. Ausführlichere Angaben finden Sie unter [Configure Intune for iOS device single sign-on (Konfigurieren von Intune für SSO von iOS-Geräten)](../configuration/ios-device-features-settings.md#single-sign-on).

### <a name="add-find-my-iphone-for-personal-devices--1427287--"></a>Hinzufügen der Funktion „Mein iPhone suchen“ für private Geräte<!--1427287-->
Ihnen wird jetzt angezeigt, ob für iOS-Geräte eine Aktivierungssperre aktiviert ist. Diese Funktion konnten Sie zuvor im klassischen Intune-Portal finden.

### <a name="remotely-lock-managed-macos-device-with-intune---1437691---"></a>Remote-Sperren von verwalteten macOS-Geräten durch Intune<!-- 1437691 -->

Sie können ein verlorenes macOS-Gerät sperren und eine sechsstellige Wiederherstellungs-PIN festlegen. Wenn das Gerät gesperrt ist, wird im Blatt **Device overview** (Geräteübersicht) die PIN solange angezeigt, bis eine andere Geräteaktion gesendet wurde.

Weitere Informationen finden Sie unter [Remotely lock managed devices with Intune (Remote-Sperren von verwalteten Geräten durch Intune)](../remote-actions/device-remote-lock.md).

### <a name="new-scep-profile-details-supported---1559808---"></a>Unterstützen von neuen SCEP-Profildetails<!-- 1559808 -->

Administratoren können nun zusätzliche Einstellungen festlegen, wenn sie ein SCEP-Profil auf Windows-, iOS-, macOS- und Android-Plattformen erstellen.  Administratoren können die IMEI, die Seriennummer oder allgemeine Namen, einschließlich der E-Mail-Adresse im Format des Antragstellernamens, festlegen.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset---1588489---"></a>Beibehalten von Daten während einer Zurücksetzung auf Werkseinstellungen <!--1588489 -->
Beim Zurücksetzen der Windows 10-Version 1709 und höher auf die Werkseinstellungen steht eine neue Funktion zur Verfügung. Administratoren können angeben, ob die Geräteregistrierung und andere bereitgestellte Daten während einer Zurücksetzung auf Werkseinstellungen auf einem Gerät erhalten bleiben sollen.

Die folgenden Daten bleiben während der Zurücksetzung auf Werkseinstellungen erhalten:
- Dem Gerät zugeordnete Benutzerkonten
- Status des Computers (Domänenbeitritt, mit Azure Active Directory verknüpft)
- MDM-Registrierung
- Über OEM installierte Apps (Store- und Win32-Apps)
- Benutzerprofil
- Benutzerdaten außerhalb des Benutzerprofils
- Automatische Anmeldung des Benutzers

Die folgenden Daten bleiben nicht erhalten:
- Benutzerdateien
- Vom Benutzer installierte Apps (Store- und Win32-Apps)
- Geräteeinstellungen, die nicht dem Standard entsprechen


### <a name="window-10-update-ring-assignments-are-displayed---1621837---"></a>Zuweisungen des Windows 10-Updaterings werden angezeigt<!-- 1621837 -->
Wenn Sie für den angezeigten Benutzer **Probleme behandeln**, werden Ihnen sämtliche Zuweisungen des Windows 10-Updaterings angezeigt.  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings----1455974----"></a>Häufigkeitseinstellungen für Windows Defender Advanced Threat Protection-Berichte <!-- 1455974  -->
Der Dienst Windows Defender Advanced Threat Protection (WDETP) ermöglicht es Administratoren, zu verwalten, wie häufig für verwaltete Geräte Berichte erstellt werden sollen. Mit der neuen Option **Häufigkeit von Telemetrieberichten erhöhen** erfasst WDETP häufiger Daten und prüft Risiken. Die Standardeinstellung für die Berichterstellung optimiert Geschwindigkeit und Leistung. Für Geräte, die ein hohes Risiko darstellen,kann es sehr nützlich sein, häufiger Berichte zu erstellen. Diese Einstellung finden Sie in den **Gerätekonfigurationen** in dem Profil **Windows Defender ATP**.

### <a name="audit-updates---1412961---"></a>Überwachungsupdates<!-- 1412961 -->  
Die Intune-Überwachung stellt einen Datensatz mit Änderungsvorgängen im Zusammenhang mit Intune zur Verfügung.  Alle Vorgänge zum Erstellen, Aktualisieren und Löschen sowie Remoteaufgaben werden erfasst und für ein Jahr gespeichert.  Im Azure-Portal werden die Überwachungsdaten der letzten 30 Tage filterbar in sämtlichen Workloads dargestellt.  Eine dazugehörige Graph-API ermöglicht den Abruf von Überwachungsdaten, die über ein Jahr hinweg gespeichert wurden.

Die Überwachungsfunktion finden Sie unter der Gruppe **MONITOR**. Für jede Workload gibt es das Menüelement **Überwachungsprotokolle**.

### <a name="company-portal-app-for-macos-is-available--1541700--"></a>Unternehmensportal-App für macOS ist verfügbar<!--1541700-->
Das Intune-Unternehmensportal unter macOS besitzt eine aktualisierte Benutzeroberfläche, die für die saubere Darstellung aller Informationen und Konformitätsbenachrichtigungen optimiert wurde, die Ihre Benutzer für alle registrierten Geräte benötigen. Nachdem das Intune-Unternehmensportal auf einem Gerät bereitgestellt wurde, stellt Microsoft AutoUpdate für macOS Updates für sie bereit. Sie können das neue Intune-Unternehmensportal für macOS herunterladen, indem Sie sich von einem macOS-Gerät aus bei der Website des Intune-Unternehmensportals anmelden.

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps----1248473---"></a>Microsoft Planner ist jetzt Bestandteil der MAM-Liste (Mobile App-Verwaltung) genehmigter Apps <!-- 1248473 -->
Die Microsoft Planner-App für iOS und Android gehört jetzt zu den genehmigten Apps für die mobile App-Verwaltung (MAM). Im Azure-Portal kann die App über das Blatt „Intune-App-Schutz“ für alle Mandanten konfiguriert werden.
- Weitere Informationen zur [MAM-Liste genehmigter Apps](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices-----1547061---"></a>Aktualisierungshäufigkeit der Pro-App-VPN-Anforderung auf iOS-Geräten  <!-- 1547061 -->  
Administratoren können jetzt Pro-App-VPN-Anforderungen für Apps auf iOS-Geräten entfernen. Betroffene Geräte werden nach ihrem nächsten Intune-Check-In aktualisiert, das in der Regel innerhalb von 15 Minuten erfolgt.  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector---885457---"></a>Unterstützung für das System Center Operations Manager-Management Pack für den Exchange-Connector<!-- 885457 -->
Mit dem SCOM-Management Pack (System Center Operations Manager) für den Exchange-Connector können Sie jetzt die Exchange-Connectorprotokolle analysieren. Dieses Feature bietet Ihnen verschiedene Möglichkeiten zur Überwachung des Diensts bei der Problembehandlung.

### <a name="co-management-for-windows-10-devices----1243445---"></a>Co-Verwaltung für Windows 10-Geräte <!-- 1243445 -->
Bei der Co-Verwaltung handelt es sich um eine Lösung, die eine Brücke von der herkömmlichen zur modernen Verwaltung schlägt und Ihnen die Möglichkeit bietet, die Umstellung schrittweise durchzuführen. Bei der Co-Verwaltung handelt es sich im Grunde um eine Lösung, mit der Windows 10-Geräte gleichzeitig mit Configuration Manager und Intune verwaltet werden können. Außerdem können sie in Active Directory (AD) und Azure Active Directory (Azure AD) eingebunden werden.  Diese Konfiguration bietet Ihnen eine Möglichkeit, um nach und nach den Bedürfnissen Ihrer Organisation entsprechend eine Modernisierung durchzuführen, wenn Sie nicht alles auf einmal durchführen können.  

### <a name="restrict-windows-enrollment-by-os-version---245498---"></a>Einschränkung der Windows-Registrierung nach Betriebssystemversion<!-- 245498 -->
Als Intune-Administrator können Sie jetzt eine Mindest- und eine Höchstversion von Windows 10 für Geräteregistrierungen angeben. Sie können diese Einschränkungen auf dem Blatt **Plattformkonfigurationen** festlegen.

Intune unterstützt auch weiterhin die Registrierung von Windows 8.1-PCs und Smartphones. Allerdings können nur für Windows 10-Versionen Grenzwerte für die Mindest- und Höchstversion festgelegt werden. Um die Registrierung von 8.1-Geräten zu erlauben, lassen Sie die Angabe für die Mindestversion leer.

### <a name="alerts-for-windows-autopilot-unassigned-devices----1631236---"></a>Warnungen für nicht zugewiesene Windows Autopilot-Geräte <!-- 1631236 -->
Auf der Seite **Microsoft Intune** > **Geräteregistrierung** > **Übersicht** steht eine neue Warnung für nicht zugewiesene Windows AutoPilot-Geräte zur Verfügung. Diese Warnung zeigt, wie vielen Geräten aus dem AutoPilot-Programm keine AutoPilot-Bereitstellungsprofile zugewiesen wurden. Verwenden Sie die Informationen aus der Warnung, um Profile zu erstellen und sie den nicht zugeordneten Geräten zuzuweisen. Wenn Sie auf die Warnung klicken, sehen Sie die vollständige Liste der Windows AutoPilot-Geräte zusammen mit detaillierten Informationen. Weitere Informationen finden Sie unter [Enroll Windows devices using Windows AutoPilot Deployment Program (Registrieren von Windows-Geräten mithilfe des Windows AutoPilot Deployment-Programms)](../enrollment/enrollment-autopilot.md).


### <a name="refresh-button-for-devices-list------1333581---"></a>Schaltfläche „Aktualisieren“ für Geräteliste   <!-- 1333581 -->
Da die Geräteliste nicht automatisch aktualisiert wird, können Sie die neue Schaltfläche „Aktualisieren“ verwenden, um die in der Liste angezeigten Geräte zu aktualisieren.

### <a name="support-for-symantec-cloud-certification-authority-ca----1333638---"></a>Unterstützung für die Symantec-Cloud-Zertifizierungsstelle (ZS) <!-- 1333638 -->    
Intune unterstützt nun die Symantec-Cloud-ZS, die es dem Intune Certificate Connector ermöglicht, PKCS-Zertifikate von der Symantec-Cloud-ZS für von Intune verwaltete Geräte auszustellen. Wenn Sie den Intune Certificate Connector bereits mit der Microsoft-Zertifizierungsstelle (ZS) verwenden, können Sie das vorhandene Intune Certificate Connector-Setup nutzen, um die Unterstützung für die Symantec-ZS hinzuzufügen.

### <a name="new-items-added-to-device-inventory----1404455---"></a>Neue Elemente im Geräteinventar  <!--1404455 -->
Die folgenden neuen Elemente sind jetzt im [Inventar der registrierten Geräte](../remote-actions/device-inventory.md) enthalten:

- WLAN-MAC-Adresse
- Gesamtmenge des Speicherplatzes
- Gesamtmenge des freien Speicherplatzes
- MEID
- Netzbetreiber des Abonnenten

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Festlegen des Zugriffs für Apps durch einen mindestens erforderlichen Android-Sicherheitspatch auf dem Gerät<!-- 1278463 -->   
Ein Administrator kann den mindestens erforderlichen Android-Sicherheitspatch definieren, der auf dem Gerät installiert sein muss, um Zugriff auf eine verwaltete Anwendung mit einem verwalteten Konto zu erhalten.

> [!Note]  
> Dieses Feature schränkt nur Sicherheitspatches ein, die von Google für Android 6.0+-Geräte veröffentlicht wurden.

### <a name="app-conditional-launch-support---1193313---"></a>App-bedingte Startunterstützung<!-- 1193313 -->
IT-Administratoren können nun eine Anforderung über das Azure-Verwaltungsportal festlegen, um eine Kennung statt einer numerischen PIN über die mobile App-Verwaltung (Mobile App Management, MAM) zu erzwingen, wenn die Anwendung gestartet wird. Wenn dies konfiguriert ist, muss der Benutzer eine Kennung festlegen und verwenden, wenn er dazu aufgefordert wird, bevor der Zugriff auf MAM-aktivierte Apps gewährt wird. Eine Kennung ist als numerische PIN mit mindestens einem Sonderzeichen oder einem Groß-/Kleinbuchstaben definiert. In dieser Version von Intune wird dieses Feature **nur unter iOS** aktiviert. Intune unterstützt Kennungen auf ähnliche Weise wie numerische PINs, nämlich indem eine Mindestlänge festgelegt wird, sodass wiederholte Zeichen und Sequenzen möglich sind. Für dieses Feature ist die Beteiligung von Anwendungen erforderlich (d.h. WXP, Outlook, Managed Browser, Yammer), um das Intune App SDK in den Code für dieses Feature anstelle der Kennungseinstellungen zu integrieren und für die Zielanwendungen zu erzwingen.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report---1233999---"></a>App-Versionsnummer für branchenspezifische Apps im Statusbericht der Geräteinstallation<!-- 1233999 -->
Ab dieser Version zeigt der Statusbericht der Geräteinstallation die App-Versionsnummern der branchenspezifischen Apps für iOS und Android an. Sie können diese Informationen verwenden, um Probleme mit Ihren Apps zu beheben oder um Geräte zu suchen, auf denen veraltete App-Versionen ausgeführt werden.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile---951708---"></a>Administratoren können nun die Firewalleinstellungen auf einem Gerät mithilfe eines Profils für die Gerätekonfiguration konfigurieren<!-- 951708 -->   
Administratoren können die Firewall für Geräte einschalten sowie verschiedene Protokolle für Domänen sowie private und öffentliche Netzwerke konfigurieren.  Diese Firewall-Einstellungen können im Profil „Endpoint Protection“ gefunden werden.

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization---958257---"></a>Windows Defender Application Guard unterstützt den Schutz von Geräten vor nicht vertrauenswürdigen Websites gemäß den Definitionen Ihrer Organisation<!-- 958257 -->   
Administratoren können Websites mithilfe eines Windows Information Protection-Workflows oder des neuen Profils „Netzwerkgrenze“ in den Gerätekonfigurationen als „trusted“ (vertrauenswürdig) oder „corporate“ (geschäftlich) definieren. Alle Websites, die mit Microsoft Edge angezeigt werden und nicht in der vertrauenswürdigen Netzwerkgrenze eines Windows 10-Geräts (64 Bit) aufgelistet werden, werden stattdessen in einem Browser innerhalb eines virtuellen Hyper-V-Computers geöffnet.

Application Guard kann unter den Profilen für die Gerätekonfiguration im Profil „Endpoint Protection“ gefunden werden. Von dort aus können Administratoren die Interaktionen zwischen dem virtualisierten Browser und dem Hostcomputer, vertrauenswürdigen und nicht vertrauenswürdigen Websites sowie das Speichern von Daten konfigurieren, die im virtualisierten Browser generiert werden. Es muss zunächst eine Netzwerkgrenze konfiguriert werden, um Application Guard auf einem Gerät zu verwenden. Es ist wichtig, nur eine Netzwerkgrenze für ein Gerät zu definieren.  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps---1031096---"></a>Windows Defender Application Control unter Windows 10 Enterprise bietet einen Modus, um nur autorisierten Apps zu vertrauen<!-- 1031096 -->    
Durch Tausende von neuen, schädlichen Dateien, die jeden Tag erstellt werden, bietet das Verwenden von signaturbasierten Antivirenerkennungen zum Bekämpfen von Schadsoftware keine angemessene Verteidigung mehr gegen neue Angriffe. Indem Sie Windows Defender Application Control unter Windows 10 Enterprise verwenden, können Sie die Gerätekonfiguration von einem Modus, in dem Apps als vertrauenswürdig gelten, wenn Sie nicht von einem Antivirenprogramm oder einer anderen Sicherheitslösung blockiert werden, zu einem Modus ändern, in dem das Betriebssystem nur Apps vertraut, die von Ihrem Unternehmen autorisiert wurden. Sie weisen den Apps die Vertrauensstellung in Windows Defender Application Control zu.

Mithilfe von Intune können Sie die Anwendungssteuerungsrichtlinien entweder für den Modus „Nur überwachen“ oder „Erzwingen“ konfigurieren. Apps werden nicht blockiert, wenn diese im Modus „audit only“ (Nur überwachen) ausgeführt werden. Der Modus „Nur überwachen“ protokolliert alle Ereignisse in lokalen Clientprotokollen. Sie können ebenfalls konfigurieren, ob nur Windows-Komponenten und Microsoft Store-Apps ausgeführt werden können, oder ob zusätzliche Apps mit gutem Ruf gemäß der Definition von Intelligent Security Graph ausgeführt werden können.

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10---1063615---"></a>Windows Defender Exploit Guard bietet neue Eindringschutzfunktionen für Windows 10<!-- 1063615 -->   
Window Defender Exploit Guard enthält benutzerdefinierte Regeln, um die Angreifbarkeit von Anwendungen zu reduzieren, verhindert Bedrohungen durch Makros und Skripts, blockiert automatisch Netzwerkverbindungen zu IP-Adressen mit schlechtem Ruf und kann Daten vor Ransomware und unbekannten Bedrohungen schützen. Windows Defender Exploit Guard besteht aus folgenden Komponenten:

- **Verringerung der Angriffsfläche** stellt Regeln bereit, die es Ihnen ermöglichen, Bedrohungen durch Makros, Skripts und E-Mails zu verhindern.
- Der **gesteuerte Ordnerzugriff** blockiert automatisch den Zugriff auf Inhalte in geschützten Ordnern.
- Der **Netzwerkfilter** blockiert ausgehende Verbindungen von jeder App mit IPs/Domänen mit schlechtem Ruf.
- Der **Exploit-Schutz** stellt Einschränkungen für den Arbeitsspeicher, die Ablaufsteuerung und Richtlinien bereit, die für den Schutz einer Anwendung vor Exploits verwendet werden können.

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices---790537---"></a>Verwalten von PowerShell-Skripts in Intune für Windows 10-Geräte<!-- 790537 -->

Durch die Verwaltungserweiterung von Intune können Sie PowerShell-Skripts in Intune für die Ausführung auf Windows 10-Geräten hochladen. Die Erweiterungen ergänzen Funktionen für die mobile Geräteverwaltung (mobile device management, MDM) von Windows 10 und erleichtern Ihnen die Umstellung auf eine moderne Verwaltung. Details finden Sie unter [Verwalten von PowerShell-Skripts in Intune für Windows 10-Geräte](../apps/intune-management-extension.md).

### <a name="new-device-restriction-settings-for-windows-10--------1308850---"></a>Neue Einstellungen für Geräteeinschränkungen für Windows 10     <!-- 1308850 -->
- Messaging (nur mobil): Deaktivieren von Test- oder MMS-Nachrichten
- Kennwort: Einstellungen zum Aktivieren von FIPS und der Verwendung von sekundären Windows Hello-Geräten für die Authentifizierung 
- Anzeige: Einstellungen zum Aktivieren oder Deaktivieren der GDI-Skalierung für ältere Apps

### <a name="windows-10-kiosk-mode-device-restrictions---1308872---"></a>Geräteeinschränkungen beim Windows 10-Kioskmodus<!-- 1308872 -->   
Sie können die Benutzer von Windows 10-Geräten auf den Kioskmodus beschränken, der diese auf eine Reihe von vordefinierten Apps einschränkt.  Erstellen Sie dazu ein Einschränkungsprofil für Windows 10-Geräte und legen Sie die Kioskeinstellung fest.

Der Kioskmodus unterstützt zwei Modi: **einzelne App** (ermöglicht dem Benutzer nur das Ausführen einer einzigen App) oder **mehrere Apps** (ermöglicht den Zugriff auf verschiedene Apps).  Sie definieren das Benutzerkonto und den Gerätenamen, der die unterstützten Apps definiert.  Wenn der Benutzer angemeldet ist, ist dieser auf die definierten Apps beschränkt.  Weitere Informationen finden Sie unter [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp). 

Der Kioskmodus erfordert Folgendes:

- Intune muss die MDM-Autorität sein.
- Die Apps müssen bereits auf dem Zielgerät installiert sein.
- Das Gerät muss [ordnungsgemäß bereitgestellt](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions) sein.

### <a name="new-device-configuration-profile-for-creating-network-boundaries---1311967---"></a>Neues Gerätekonfigurationsprofil für das Erstellen von Netzwerkgrenzen<!-- 1311967 -->   
Ein neues Gerätekonfigurationsprofil namens **Netzwerkgrenze** ist jetzt neben Ihren anderen Gerätekonfigurationsprofilen verfügbar. Verwenden Sie dieses Profile, um Onlineressourcen zu definieren, die als „geschäftlich“ oder „vertrauenswürdig“ angesehen werden sollen. Sie müssen eine Netzwerkgrenze für ein Gerät definieren, *bevor* Features wie Windows Defender Application Guard und Windows Information Protection auf dem Gerät verwendet werden können. Es ist wichtig, nur eine Netzwerkgrenze für jedes Gerät zu definieren.

Sie können Unternehmenscloudressourcen, IP-Adressbereiche und interne Proxyserver definieren, die als vertrauenswürdig angesehen werden sollen. Sobald diese definiert sind, kann die Netzwerkgrenze von anderen Features wie Windows Defender Application Guard und Windows Information Protection verwendet werden.

### <a name="two-additional-settings-for-windows-defender-antivirus---1338409---"></a>Zwei zusätzliche Einstellungen für Windows Defender Antivirus<!-- 1338409 -->  
**Ebene der Dateiblockierung**

| | |
|---|---|
| Nicht konfiguriert | **Nicht konfiguriert** verwendet die Standardblockierungsebene von Windows Defender Antivirus und bietet eine starke Erkennung ohne das Risiko zu erhöhen, zulässige Dateien zu erkennen. |
| Hoch | **Hoch** wendet eine starke Erkennungsebene an.
| Hoch +  | **Hoch +** bietet die Ebene „Hoch“ mit zusätzlichen Schutzmaßnahmen, die sich auf die Clientleistung auswirken können.
| Keine Toleranz  | **Keine Toleranz** blockiert alle unbekannten ausführbaren Dateien. |

Es ist zwar unwahrscheinlich, aber dennoch können bei der Einstellung auf **Hoch** einige zulässige Dateien erkannt werden.
Es wird empfohlen, die Ebene der Datenblockierung auf den Standardwert, **Nicht konfiguriert**, festzulegen.

**Timeouterweiterung für die Dateiüberprüfung durch die Cloud**  

| | |
|--|--|
| Anzahl von Sekunden (0–50) | Geben Sie den maximalen Zeitraum an, für den Windows Defender Antivirus eine Datei blockieren soll, während auf ein Ergebnis von der Cloud gewartet wird. Der Standardzeitraum beträgt 10 Sekunden. Jede zusätzliche Zeit, die hier angegeben wird (bis zu 50 Sekunden), wird zu diesen 10 Sekunden addiert. In den meisten Fällen nimmt der Scan wesentlich weniger als den Maximalwert in Anspruch. Das Erweitern des Zeitraums ermöglicht es der Cloud, verdächtige Dateien gründlich zu überprüfen. Es wird empfohlen, diese Einstellung zu aktivieren und mindestens 20 zusätzliche Sekunden anzugeben. |

### <a name="citrix-vpn-added-for-windows-10-devices---1512457---"></a>Citrix-VPN wurde für Windows 10-Geräte hinzugefügt<!-- 1512457 -->  
Sie können Citrix-VPN für ihre Windows 10-Geräte konfigurieren. Sie können Citrix-VPN in der Liste *Verbindungstyp auswählen* im Blatt **Basis-VPN** auswählen, wenn Sie ein VPN für Windows 10 oder höher konfigurieren.

> [!Note]
> Die Citrix-Konfiguration ist bereits für iOS und Android vorhanden.

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios---1550823---"></a>WLAN-Verbindungen unterstützen vorinstallierte Schlüssel unter iOS<!-- 1550823 -->
Kunden können WLAN-Profile konfigurieren, um vordefinierte Schlüssel (pre-shared keys, PSK) für persönliche WPA/WPA2-Verbindungen auf iOS-Geräten zu verwenden. Diese Profile werden per Push an das Gerät des Benutzers übertragen, wenn das Gerät bei Intune registriert wird.

Wenn das Profil an das Gerät übertragen wurde, hängt der nächste Schritt von der Profilkonfiguration ab.  Wenn automatisches Herstellen einer Verbindung festgelegt ist, geschieht das bei der nächsten Gelegenheit, bei der das Netzwerk benötigt wird.  Wenn das Profil manuelles Herstellen der Verbindung festlegt, muss der Benutzer die Verbindung manuell aktivieren.  

### <a name="access-to-managed-app-logs-for-ios---1469920---"></a>Zugriff auf Protokolle von verwalteten Apps für iOS<!-- 1469920 -->
Endbenutzer, bei denen der Managed Browser installiert ist, können jetzt den Verwaltungsstatus aller von Microsoft veröffentlichten Apps anzeigen und Protokolle zur Problembehandlung ihrer verwalteten iOS-Apps senden.

Informationen zum Aktivieren des Problembehandlungsmodus im Managed Browser auf einem iOS-Gerät finden Sie unter [Zugreifen auf Protokolle von verwalteten Apps mithilfe des Managed Browsers unter iOS](../apps/app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290---1417174---"></a>Verbesserungen des Workflows für das Gerätesetup im Unternehmensportal für iOS in Version 2.9.0<!-- 1417174 -->

Der Workflow für die Geräteinstallation in der Unternehmensportal-App unter iOS wurde verbessert. Die Sprache ist nun benutzerfreundlicher. Zudem haben wir Bildschirme nach Möglichkeit zusammengefasst. Die Sprache wurde speziell für Ihr Unternehmen angepasst, indem der Name Ihres Unternehmens im gesamten Setuptext verwendet wird. Dieser aktualisierte Workflow ist auf der Seite mit den  [Aktualisierungen für die Benutzeroberfläche für Endbenutzer-Apps in Intune](../whats-new-app-ui.md) zu sehen.


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model---1544273---"></a>Benutzerentität enthält die aktuellen Benutzerdaten im Data Warehouse-Datenmodell<!-- 1544273 -->
Die erste Version des Intune Data Warehouse-Datenmodells enthielt lediglich aktuelle Verlaufsdaten für Intune. Berichtersteller konnten den aktuellen Status eines Benutzers nicht erfassen. In diesem Update wird die **Benutzerentität** mit den aktuellen Benutzerdaten voraufgefüllt.

<!-- ########################## -->
## <a name="october-2017"></a>Oktober 2017

### <a name="ios-and-android-line-of-business-app-version-number-is-visible---1380712---"></a>Versionsnummer der branchenspezifischen App für iOS und Android ist sichtbar<!-- 1380712 -->

Apps in Intune zeigen nun die Versionsnummer für branchenspezifische iOS- und Android-Apps an. Die Nummer wird im Azure-Portal in der App-Liste und im Übersichtsblatt der App angezeigt. Benutzer können die App-Nummer in der Unternehmensportal-App und im Webportal anzeigen.

__Vollständige Versionsnummer__: Die vollständige Versionsnummer identifiziert ein bestimmtes Release der App. Die Nummer wird als _Version_(_Build_) angezeigt. Beispielsweise 2.2(2.2.17560800)

Die vollständige Versionsnummer besteht aus zwei Komponenten:

- **Version**  
  Die Versionsnummer ist die von einem Menschen lesbare Releasenummer der App. Diese wird von Benutzern verwendet, um verschiedene Releases der App zu identifizieren.

- **Buildnummer**  
  Die Buildnummer ist eine interne Nummer, die in der App-Erkennung und zur programmgesteuerten Verwaltung der App verwendet werden kann. Die Buildnummer bezieht sich auf eine Iteration der App, die auf Änderungen im Code verweist.

Weitere Informationen zu Versionsnummern und dem Entwickeln von branchenspezifischen Apps finden Sie unter [Erste Schritte mit dem Microsoft Intune App SDK](../developer/app-sdk-get-started.md#line-of-business-app-version-numbers).

### <a name="device-and-app-management-integration---677972---"></a>Integration der Verwaltung von Geräten und Apps<!-- 677972 -->   
Da auf die mobile Geräteverwaltung (Mobile Device Management, MDM) und die mobile Anwendungsverwaltung (Mobile Application Management, MAM) nun über das Azure-Portal zugegriffen werden kann, hat Intune damit begonnen, die Vorteile für IT-Administratoren bei der Verwaltung von Anwendungen und Geräten zu integrieren. Diese Änderungen sind darauf ausgerichtet, das Verwalten von Geräten und Apps zu vereinfachen.

Weitere Informationen zu den angekündigten Änderungen an MDM und MAM finden Sie im [Blog des Intune-Supportteams](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices---1471790---"></a>Neue Warnungen für Apple-Geräte bei der Registrierung<!-- 1471790 -->
Die Übersichtsseite für die Registrierung zeigt nützliche Warnungen für IT-Administratoren für die Verwaltung von Apple-Geräten an. Warnungen werden auf der Seite „Übersicht“ angezeigt, wenn das Apple-MDM-Push-Zertifikat abläuft oder bereits abgelaufen ist, wenn das Token des Programms zur Geräteregistrierung abläuft oder bereits abgelaufen ist und wenn es nicht zugewiesene Geräte im Programm zur Geräteregistrierung gibt.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment---1080364---"></a>Unterstützung des Ersetzens von Tokens für die App-Konfiguration ohne Geräteregistrierung<!-- 1080364 -->

Sie können Tokens für dynamische Werte in App-Konfigurationen für nicht registrierte Geräte verwenden. Weitere Informationen finden Sie unter [Add app configuration policies for managed apps without device enrollment (Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Apps ohne Geräteregistrierung)](../apps/app-configuration-policies-managed-app.md).

### <a name="updates-to-the-company-portal-app-for-windows-10--1299474--"></a>Updates an der Unternehmensportal-App für Windows 10<!--1299474-->
Die Seite „Einstellungen“ in der Unternehmensportal-App für Windows 10 wurde aktualisiert, um die Einstellungen und beabsichtigten Benutzeraktionen für alle Einstellungen konsistenter zu gestalten. Sie wurde zudem an das Layout anderer Windows-Apps angepasst. Auf der Seite mit den [Neuheiten in der App-Benutzeroberfläche](../whats-new-app-ui.md) finden Sie Abbildungen von vor und nach der Aktualisierung.

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices--1337920--"></a>Informieren von Endbenutzern zu den für Windows 10-Geräte anzeigbaren Geräteinformationen<!--1337920-->
Wir haben dem Bildschirm „Gerätedetails“ den **Besitzertyp** für die Unternehmensportal-App für Windows 10 hinzugefügt. So können Benutzer direkt auf dieser Seite mehr über die Privatsphäre in der Dokumentation für Intune-Endbenutzer herausfinden. Diese Informationen sind außerdem auf dem Bildschirm **Info** zu finden.

### <a name="feedback-prompts-for-the-company-portal-app-for-android--1165249--"></a>Feedbackaufforderungen für die Unternehmensportal-App für Android<!--1165249-->
Die Unternehmensportal-App für Android bittet Endbenutzer jetzt um Feedback. Dieses Feedback wird direkt an Microsoft gesendet. So erhalten Endbenutzer die Möglichkeit, die App im öffentlichen Google Play Store zu rezensieren. Feedback ist nicht erforderlich, und die Meldung kann problemlos geschlossen werden, damit Benutzer die App weiterhin verwenden können.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android---1573324-1573150-1558616-1564878---"></a>Unterstützen Ihrer Benutzer bei der eigenständigen Problemlösung über die Unternehmensportal-App für Android<!-- 1573324, 1573150, 1558616, 1564878 -->

In der Unternehmensportal-App für Android wurden Anweisungen für Benutzer hinzugefügt, um ihnen Anwendungsfälle zu erläutern und ihnen nach Möglichkeit das eigenständige Lösen dieser Anwendungsfälle zu ermöglichen.
- Die Endbenutzer werden für das Entfernen eines Geräts zum [Azure Active Directory-Portal](https://account.activedirectory.windowsazure.com/r/#/profile) weitergeleitet, wenn sie die maximale Anzahl von Geräten, die hinzugefügt werden dürfen, überschritten haben.
- Endbenutzer erhalten schrittweise Anweisungen zum [Behandeln von Aktivierungsfehlern auf Samsung Knox-Geräten](https://go.microsoft.com/fwlink/?linkid=859718) oder zum [Ausschalten des Stromsparmodus](/intune-user-help/power-saving-mode-android). Wenn keine dieser Lösungen bei der Behebung des Problems hilft, werden wir eine Erklärung zur Verfügung stellen, in der beschrieben wird, [wie Protokolle an Microsoft übermittelt werden können](/intune-user-help/send-logs-to-microsoft-android).

### <a name="new-resolve-action-available-for-android-devices---1583480---"></a>Neue Aktion „Auflösen“ für Android-Geräte verfügbar<!-- 1583480 -->

In der Unternehmensportal-App für Android wird eine „Lösungs“-Aktion auf der Seite _Geräteeinstellungen aktualisieren_ eingeführt. Wenn der Benutzer diese Option auswählt, wird er direkt zu der Einstellung weitergeleitet, die dafür verantwortlich ist, dass das Gerät nicht kompatibel ist. Derzeit unterstützt die Unternehmensportal-App für Android diese Aktion für die Einstellungen [Gerätekennung](/intune-user-help/set-your-pin-or-password-android), [USB-Debuggen](/intune-user-help/you-need-to-turn-off-usb-debugging-android) und [Unbekannte Quellen](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

### <a name="device-setup-progress-indicator-in-android-company-portal---1565657---"></a>Statusanzeige für das Gerätesetup im Android-Unternehmensportal<!-- 1565657 -->
Die Unternehmensportal-App für Android zeigt eine Statusanzeige für das Gerätesetup an, wenn ein Benutzer sein Gerät registriert. Der Indikator zeigt neue Statusangaben an, beginnend bei „Ihr Gerät wird eingerichtet...“, dann „Das Gerät wird registriert...“, dann „Die Registrierung Ihres Geräts wird abgeschlossen...“ und schließlich „Die Einrichtung Ihres Geräts wird abgeschlossen...“.

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios--1029830--"></a>Unterstützung der zertifikatbasierten Authentifizierung auf dem Unternehmensportal für iOS<!--1029830-->
Es wurde eine Unterstützung für die zertifikatbasierte Authentifizierung in der Unternehmensportal-App für iOS hinzugefügt. Benutzer mit zertifikatbasierter Authentifizierung geben ihren Benutzernamen ein und tippen dann auf den Link „Sign in with a certificate“ (Mit einem Zertifikat anmelden). Die zertifikatbasierte Authentifizierung wird auf den Unternehmensportal-Apps für Android und Windows bereits unterstützt. Weitere Informationen finden Sie auf der Seite [Anmelden bei der Unternehmensportal-App](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment---1334712---"></a>Apps, die mit oder ohne Registrierung verfügbar sind, können nun installiert werden, ohne dass Sie zur Registrierung aufgefordert werden.<!-- 1334712 -->

Unternehmens-Apps, die mit oder ohne Registrierung in der Android-Unternehmensportal-App zur Verfügung gestellt wurden, können jetzt installiert werden, ohne dass Sie zur Registrierung aufgefordert werden.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune----747617----"></a>Unterstützung des Windows AutoPilot Deployment-Programms in Microsoft Intune <!-- 747617  -->
Sie können Microsoft Intune jetzt mit dem Windows AutoPilot Deployment-Programm verwenden, um es Ihren Benutzern zu ermöglichen, ihre Unternehmensgeräte bereitzustellen, ohne die IT-Abteilung kontaktieren zu müssen. Sie können die Windows-Willkommensseite anpassen und Benutzer dazu anleiten, ihre Geräte mit Azure AD zu verknüpfen und sich bei Intune zu registrieren. Da Microsoft Intune und Windows AutoPilot zusammenarbeiten, besteht keine Notwendigkeit, Betriebssystemabbilder bereitzustellen, zu aktualisieren und zu verwalten. Weitere Informationen finden Sie unter [Enroll Windows devices using Windows AutoPilot Deployment Program (Registrieren von Windows-Geräten mithilfe des Windows AutoPilot Deployment-Programms)](../enrollment/enrollment-autopilot.md).

### <a name="quickstart-for-device-enrollment----1425655---"></a>Schnellstart für die Geräteregistrierung <!-- 1425655 --> 
Die Schnellstartfunktion ist jetzt in der **Geräteregistrierung** verfügbar, und es wird eine Tabelle mit Verweisen zur Verfügung gestellt, mit denen Plattformen verwaltet und Registrierungsvorgänge konfiguriert werden. In Kurzbeschreibungen für jedes Element und über verschiedene Links zu Dokumentationen mit ausführlichen Anleitungen werden nützliche Informationen zur Verfügung gestellt, die die ersten Schritte vereinfachen.

### <a name="device-categorization---1427491---"></a>Gerätekategorisierung<!-- 1427491 -->
Über das Plattformdiagramm für registrierte Geräte auf dem Blatt **Geräte > Übersicht** werden Geräte nach Plattform, u.a. Android. iOS, macOS, Windows und Windows Mobile, angeordnet.  Geräte, auf denen andere Betriebssysteme installiert sind, werden der Gruppe „Andere“ zugeordnet.  Dies betrifft auch Geräte, die von Blackberry, NOKIA und anderen hergestellt werden.  

Um zu erfahren, welche Geräte in Ihrem Mandanten betroffen sind, klicken Sie auf **Verwalten > Alle Geräte**, und verwenden Sie anschließend die Funktion **Filtern**, um das Feld für die **Betriebssysteme** einzuschränken.

### <a name="zimperium---new-mobile-threat-defense-partner-----954681---"></a>Zimperium: neuer Mobile Threat Defense-Partner  <!-- 954681 -->  
Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen mit bedingtem Zugriff basierend auf Risikobewertungen steuern, die von Zimperium vorgenommen werden, einer Mobile Threat Defense-Lösung, die mit Microsoft Intune zusammenarbeitet.

#### <a name="how-integration-with-intune-works"></a>Funktionsweise der Integration mit Intune
Das Risiko wird basierend auf Telemetriedaten von Geräten bewertet, auf denen Zimperium ausgeführt wird. Sie können Richtlinien für bedingten EMS-Zugriff basierend auf der Zimperium-Risikobewertung konfigurieren, die über Intune-Gerätekompatibilitätsrichtlinien aktiviert werden, und so anhand der erkannten Bedrohungen nicht kompatible Geräte für den Zugriff auf Unternehmensressourcen zulassen oder blockieren.

### <a name="new-settings-for-windows-10-device-restriction-profile-----978575-1308849---"></a>Neue Einstellungen für das Windows 10-Geräteeinschränkungsprofil <!--- 978575, 1308849, -->  
Wir fügen neue Einstellungen zum Geräteeinschränkungsprofil für Windows 10 in der Kategorie „Windows Defender SmartScreen“ hinzu.

Details zum Geräteeinschränkungsprofil für Windows 10 finden Sie in den [Einstellungen für die Geräteeinschränkung für Windows 10 und höher](../configuration/device-restrictions-windows-10.md).

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Remoteunterstützung für Windows- und Windows Mobile-Geräte  <!-- 1070473 -->  
Intune kann jetzt die nicht im Lieferumfang inbegriffene [TeamViewer](https://www.teamviewer.com)-Software verwenden, damit Sie Ihren Benutzern, die Windows- und Windows Mobile-Geräte ausführen, Remote Support anbieten können.

### <a name="scan-devices-with-windows-defender---1280988--1280990-----"></a>Überprüfen von Geräten mit Windows Defender<!-- 1280988  1280990   -->
Auf verwalteten Windows 10-Geräten können Sie jetzt mithilfe von Windows Defender Antivirus eine **Schnellüberprüfung** und eine **vollständige Überprüfung** durchführen sowie **Signaturen aktualisieren**. Wählen Sie auf dem Übersichtsblatt des Geräts die Aktion aus, die auf dem Gerät ausgeführt werden soll. Sie werden dann aufgefordert, die Aktion zu bestätigen, bevor der Befehl an das Gerät gesendet wird. 

**Schnellüberprüfung**: Bei einer Schnellüberprüfung werden Speicherorte überprüft, an denen Schadsoftware bei Startvorgängen registriert werden (z.B. Registrierungsschlüssel und bekannte Windows-Startordner). Eine Schnellüberprüfung dauert durchschnittlich fünf Minuten. In Kombination mit der Einstellung **AlwaysOn-Echtzeitschutz**, die Dateien überprüft, wenn ein Benutzer diese öffnet, schließt und in einem Ordner navigiert, kann eine Schnellüberprüfung Schutz vor Schadsoftware bieten, die sich eventuell im System oder Kernel befinden. Die Überprüfungsergebnisse werden Benutzern nach Abschluss der Überprüfung angezeigt. 

**Vollständige Überprüfung**: Eine vollständige Überprüfung kann sich für Geräte als nützlich erweisen, bei denen eine Bedrohung durch eine Schadsoftware erkannt wurde. So kann festgestellt werden, ob inaktive Komponenten vorhanden sind, die eine gründlichere Bereinigung erfordern. Auch bei Bedarf können Überprüfungen ausgeführt werden. Die Ausführung einer vollständigen Überprüfung kann eine Stunde dauern. Die Überprüfungsergebnisse werden Benutzern nach Abschluss der Überprüfung angezeigt. 

**Aktualisieren von Signaturen**: Der Befehl zum Aktualisieren von Signaturen aktualisiert Definitionen von Schadsoftware und Signaturen von Windows Defender Antivirus. Dadurch wird eine effiziente Erkennung von Schadsoftware durch Windows Defender Antivirus sichergestellt. Diese Funktion gilt nur für Windows 10-Geräte bei bestehender Internetkonnektivität. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal----1400455---"></a>Aktivierungs- bzw. Deaktivierungsschaltfläche wurde von der Seite „Intune-Zertifizierungsstelle“ im Intune Azure-Portal entfernt <!-- 1400455 -->
 Dadurch wird ein zusätzlicher Schritt bei der Einrichtung des Zertifikatconnectors auf Intune entfernt. Derzeit laden Sie den Zertifikatconnector herunter und aktivieren ihn anschließend in der Intune-Konsole. Wenn Sie allerdings den Connector in der Intune-Konsole deaktivieren, gibt der Connector weiter Zertifikate aus.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Ab Oktober wird die Aktivierungs- bzw. Deaktivierungsschaltfläche nicht mehr auf der Seite „Intune-Zertifizierungsstelle“ im Azure-Portal angezeigt. Die Connector-Funktionalität ändert sich nicht. Zertifikate werden weiterhin für Geräte bereitgestellt, die in Intune registriert sind. Sie können ebenfalls weiterhin den Zertifikatconnector herunterladen und installieren. Wenn Sie verhindern wollen, dass Zertifikate ausgestellt werden, müssen Sie jetzt den Zertifikatorconnector deinstallieren anstatt ihn nur zu deaktivieren.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Wenn derzeit der Zertifikatconnector deaktiviert ist, müssen Sie ihn deinstallieren.

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838---"></a>Neue Einstellungen für das Windows 10 Team-Geräteeinschränkungsprofil  <!--- 1308838 -->
Zu dieser Version wurden viele neue Einstellungen für das Windows 10 Team-Geräteeinschränkungsprofil hinzugefügt, um Sie bei der Steuerung von Surface Hub-Geräten zu unterstützen.

Weitere Informationen zu diesem Profil finden Sie unter [Einstellungen für Windows 10 Team-Geräteeinschränkungen](../configuration/device-restrictions-windows-10-teams.md).

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time----1333292---"></a>Blockieren von Änderungen an Datums- und Uhrzeiteinstellungen von Android-Geräten durch Benutzer <!-- 1333292 -->
Durch [benutzerdefinierte Android-Geräterichtlinien](../configuration/custom-settings-android.md) können Sie Benutzer von Android-Geräten daran hindern, Datums- und Uhrzeiteinstellungen von Geräten zu ändern.

Hierfür konfigurieren Sie eine benutzerdefinierte Android-Richtlinie mit dem Einstellungs-URI „./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange“, legen diesen auf **TRUE** fest und weisen dann die erforderlichen Gruppen zu.

### <a name="bitlocker-device-configuration---1397398---"></a>BitLocker-Gerätekonfiguration<!-- 1397398 -->
Die Einstellungen unter **Windows-Verschlüsselung > Basiseinstellungen** umfassen die neue Einstellung **Warnung für andere Datenträgerverschlüsselung**, mit der Sie die [Eingabeaufforderung bei Warnungen](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowwarningforotherdiskencryption) für andere Datenträgerverschlüsselungen, die eventuell auf dem Gerät des Benutzers verwendet werden, deaktivieren können.  Für die Eingabeaufforderung bei Warnungen ist die Zustimmung des Endbenutzers erforderlich, bevor BitLocker auf dem Gerät eingerichtet wird. Zudem wird das BitLocker-Setup erst durchgeführt, wenn die Eingabeaufforderung vom Endbenutzer bestätigt wurde.  Die neue Einstellung deaktiviert die Warnung für Endbenutzer.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant---800882---"></a>Volume Purchase Program für Geschäftsanwendungen wird jetzt mit Ihrem Intune-Mandanten synchronisiert<!-- 800882 -->  
Drittentwickler können, wie in iTunes Connect angegeben, privat ihre Apps an autorisierte Mitglieder von VPP für Unternehmen verteilen. Diese Mitglieder des VPP für Unternehmen können sich im VPP-App Store registrieren und ihre Apps dort erwerben.

Mit dieser Version beginnt die VPP für Geschäftsanwendungen, die der Benutzer erworben hat, jetzt mit der Synchronisierung mit Ihren Intune-Mandanten.

### <a name="select-apple-countryregion-store-to-sync-vpp-apps----1332311---"></a>Auswählen des nationalen bzw. regionalen Apple App Store zum Synchronisieren von VPP-Apps <!-- 1332311 -->  
Beim Hochladen Ihres VPP-Tokens können Sie den nationalen bzw. regionalen VPP Store (Volume Purchase Program) konfigurieren. Intune synchronisiert VPP-Apps für alle Gebietsschemas aus dem jeweiligen nationalen bzw. regionalen VPP Store.

> [!NOTE]  
> Derzeit synchronisiert Intune nur VPP-Apps aus dem nationalen bzw. regionalen VPP Store mit dem Intune-Gebietsschema, in dem der Intune-Mandant erstellt wurde.


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work---1098994---"></a>Blockieren der Funktion zum Kopieren und Einfügen zwischen Arbeitsprofilen und persönlichen Profilen in Android for Work<!-- 1098994 -->
Mit dieser Version können Sie das Arbeitsprofil für Android for Work konfigurieren, um die Funktion zum Kopieren und Einfügen zwischen Arbeits- und persönlichen Apps zu blockieren. Sie finden diese neue Einstellung im Profil **Geräteeinschränkungen** für die **Android for Work**-Plattform unter **Arbeitsprofileinstellungen**.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores---1281692---"></a>Erstellen von auf bestimmte regionale Apple App Stores beschränkten iOS-Apps<!-- 1281692 -->
Bei der Erstellung einer verwalteten Apple App Store-App haben Sie die Möglichkeit, das Gebietsschema anzugeben.

> [!Note]  
> Derzeit können nur verwaltete Apple App Store-Apps erstellt werden, die im Store für die USA zur Verfügung gestellt werden.

### <a name="update-ios-vpp-user-and-device-licensed-apps----1305564---"></a>Aktualisieren von für Benutzer und Geräte lizenzierten iOS-VPP-Apps <!-- 1305564 -->  
Durch Konfigurieren des iOS-VPP-Tokens können Sie alle Apps aktualisieren, die für dieses Token über den Intune-Dienst erworben wurden. Intune erkennt Updates für VPP-Apps in App Store und überträgt diese beim Geräte-Check-In automatisch mithilfe von Push auf das Gerät.

Informationen über die einzelnen Schritte, wie Sie VPP-Token festlegen und automatische Updates aktivieren, finden Sie unter [Verwalten von iOS-Apps, die über ein Volumenprogramm mit Microsoft Intune erworben wurden] (/intune/vpp-apps-ios).


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model---1187917---"></a>Entitätssammlung von Benutzergerätezuordnungen zum Intune Data Warehouse-Datenmodell hinzugefügt<!-- 1187917 -->
Mithilfe von Informationen über Benutzergerätezuordnungen können Sie Berichte und Datenvisualisierungen erstellen, die Entitätssammlungen von Benutzern und Geräten zuordnet. Auf das Datenmodell kann über die Power BI-Datei (PBIX) zugegriffen werden, die über die Data Warehouse-Seite von Intune, den OData-Endpunkt oder durch die Entwicklung eines benutzerdefinierten Clients abgerufen wird.

### <a name="review-policy-compliance-for-windows-10-update-rings---1067886---"></a>Überprüfen der Richtlinienkonformität für Windows 10-Updateringe<!-- 1067886 -->
Unter „Softwareupdates > Bereitstellungsstatus pro Updatering“ können Sie einen Richtlinienbericht für Ihre Windows 10-Updateringe einsehen. Der Richtlinienbericht gibt den Bereitstellungsstatus für die Updateringe an, die Sie konfiguriert haben. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions-----1352223---"></a>Neuer Bericht, der iOS-Geräte mit älteren iOS-Versionen auflistet  <!-- 1352223 -->
Der Bericht **Out-of-date iOS Devices (Veraltete iOS-Geräte)** ist im Arbeitsbereich **Softwareupdates** verfügbar. Im Report sehen Sie eine Liste überwachter iOS-Geräte, die unter eine iOS-Updaterichtlinie fallen und mehrere verfügbare Updates besitzen. Für jedes Gerät können Sie einen Status anzeigen, warum das Gerät nicht automatisch aktualisiert wurde. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting----1475003---"></a>Anzeigen der Zuweisungen von App-Schutzrichtlinien für die Problembehandlung<!--  1475003 -->
In der kommenden Version wird auf dem Blatt „Problembehandlung“ die Option **App-Schutzrichtlinie** zur Dropdown-Liste **Zuweisungen** hinzugefügt. Nun können Sie App-Schutzrichtlinien auswählen, um die für ausgewählte Benutzer zugewiesenen App-Schutzrichtlinien anzuzeigen.



### <a name="improvements-to-device-setup-workflow-in-company-portal--1490692--"></a>Verbesserungen des Workflows für das Gerätesetup im Unternehmensportal<!--1490692-->
Der Workflow für die Geräteinstallation in der Unternehmensportal-App unter Android wurde verbessert. Die Sprache ist nun benutzerfreundlicher und spezifisch für Ihr Unternehmen. Zudem haben wir wo es möglich war Bildschirme vereint. Sie können diese auf der Seite [Was gibt es Neues auf der App-Benutzeroberfläche](whats-new-app-ui.md#week-of-october-2-2017) anzeigen.

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices--1484985--"></a>Verbesserter Leitfaden bezüglich der Anforderung des Zugriffs auf Kontakte auf Android-Geräten<!--1484985-->

Die Unternehmensportal-App für Android erfordert oft, dass Benutzer die Kontaktberechtigungen akzeptieren. Wenn ein Endbenutzer diesen Zugriff verweigert, wird ihm eine In-App-Benachrichtigung angezeigt, die ihn anweist, diesen für den bedingten Zugriff zu gewähren. 

### <a name="secure-startup-remediation-for-android--1490712--"></a>Secure Startup-Wartung für Android<!--1490712-->

Benutzer von Android-Geräten können den Grund der Nichtkompatibilität in der Unternehmensportal-App wählen. Wenn möglich werden sie direkt an den korrekten Ort in der Einstellungs-App geleitet, um das Problem zu beheben. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo--1475932--"></a>Zusätzliche Pushbenachrichtigungen für Endbenutzer in der Unternehmensportal-App für Android Oreo<!--1475932-->

Benutzern werden zusätzliche Benachrichtigungen angezeigt, die ihnen mitteilen, wann die Unternehmensportal-App für Android Oreo Hintergrundaufgaben durchführt, z.B. Abrufen von Richtlinien aus dem Intune-Dienst. So sind Endbenutzer besser darüber informiert, wann die Unternehmensportal-App administrative Aufgaben auf ihren Geräten ausführt. Dies ist Teil der gesamten [Optimierung der Unternehmensportal-Benutzeroberfläche](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) für die Unternehmensportal-App für Android Oreo. 

Es gibt weitere Optimierungen für neue Benutzeroberflächenelemente, die in Android Oreo aktiviert sind.  Benutzern werden zusätzliche Benachrichtigungen angezeigt, die angeben, wann das Unternehmensportal Hintergrundaufgaben durchführt, z.B. Abrufen von Richtlinien aus dem Intune-Dienst.  Dadurch wird die Transparenz für Benutzer erhöht, für den Fall, dass das Unternehmensportal administrative Aufgaben auf dem Gerät ausführt.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles---1485783---"></a>Neue Verhalten für die Unternehmensportal-App für Android mit Arbeitsprofilen<!-- 1485783 -->

Wenn Sie ein Android for Work-Gerät mit einem Arbeitsprofil registrieren, werden Verwaltungsaufgaben auf dem Gerät von der Unternehmensportal-App im Arbeitsprofil ausgeführt. 

Wenn Sie eine MAM-fähige App im persönlichen Profil verwenden, kann die Unternehmensportal-App für Android nicht mehr verwendet werden. Um die Benutzererfahrung bezüglich des Arbeitsprofils zu verbessern, blendet Intune die persönliche Unternehmensportal-App nach erfolgreicher Registrierung eines Arbeitsprofils automatisch aus.

Die Unternehmensportal-App für Android kann jederzeit im persönlichen Profil aktiviert werden, indem Sie zum [Unternehmensportal im Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) navigieren und auf **Aktivieren** tippen.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode--1428681--"></a>Unternehmensportal für Windows 8.1 und Windows Phone 8.1 in den nachhaltigen Modus verschieben<!--1428681-->

Ab Oktober 2017 wird der Aufrechterhaltungsmodus für Unternehmensportal-Apps für Windows 8.1 und Windows Phone 8.1 aktiviert. Dies bedeutet, dass die Apps und vorhandenen Szenarien wie Registrierung und Konformität weiterhin für diese Plattformen unterstützt werden. Diese Apps werden weiterhin über vorhandene Veröffentlichungskanäle wie dem Microsoft Store zum Download zur Verfügung gestellt. 

Sobald sich diese Apps im Aufrechterhaltungsmodus befinden, werden nur kritische Sicherheitsupdates empfangen. Es werden keine weiteren Updates oder Funktionen für diese Apps veröffentlicht. Um von neuen Funktionen profitieren zu können, wird empfohlen, Geräte auf Windows 10 und Windows 10 Mobile zu aktualisieren. 


### <a name="block-unsupported-samsung-knox-device-enrollment----1490695---"></a>Blockieren der nicht unterstützten Samsung KNOX-Geräteregistrierung <!-- 1490695 -->

Die Unternehmensportal-App versucht, ausschließlich unterstützte Samsung KNOX-Geräte zu registrieren. Die Geräteregistrierung wird nur ausgeführt, wenn das Gerät in der [Liste der von Samsung veröffentlichten Geräte](https://www.samsungknox.com/knox-supported-devices/knox-workspace) erscheint, um Aktivierungsfehler von KNOX zu vermeiden, die die MDM-Registrierung verhindern. Samsung-Geräte können über Modellnummern verfügen, die KNOX unterstützen, während andere dies nicht tun. Überprüfen Sie vor dem Kauf und der Bereitstellung daher mithilfe des Wiederverkäufers Ihrer Geräte, ob diese mit KNOX kompatibel sind. Die vollständige Liste verifizierter Geräte finden Sie in den [Einstellungen für Android- und Samsung KNOX Standard-Richtlinien](supported-devices-browsers.md#intune-supported-web-browsers).

### <a name="end-of-support-for-android-43-and-lower---1171126-1326920---"></a>Ende des Supports für Android 4.3 und niedriger<!-- 1171126, 1326920 -->
Verwaltete Apps und die Unternehmensportal-App für Android benötigen Android 4.4 oder höher, um auf Unternehmensressourcen zugreifen zu können. Ab Dezember werden alle registrierten Geräte deaktiviert und können dann nicht mehr auf Unternehmensressourcen zugreifen. Bei Verwendung von App-Schutzrichtlinien ohne mobile Geräteverwaltung erhalten Apps keine Updates mehr, und die Qualität ihrer Benutzung wird mit der Zeit abnehmen.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices--1165314--"></a>Informieren von Endbenutzern, welche Geräteinformationen auf registrierten Geräten angezeigt werden können<!--1165314-->
Wir fügen dem Bildschirm „Gerätedetails“ den **Besitzertyp** auf allen Unternehmensportal-Apps hinzu. So können Benutzer direkt im Artikel [Welche Informationen erhält mein Unternehmen, wenn ich mein Gerät registriere?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) mehr über die Privatsphäre herausfinden. Dies wird in allen Unternehmensportal-Apps in Zukunft eingeführt. Für iOS haben wir dies im [September](#september-2017) angekündigt.

<!-- ########################## -->
## <a name="september-2017"></a>September 2017

### <a name="intune-supports-ios-11--1428975--"></a>Intune unterstützt iOS 11<!--1428975-->
Intune unterstützt iOS 11. Dies wurde zuvor auf dem [Blog zum Intune-Support](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/) angekündigt.

### <a name="end-of-support-for-ios-80---1164477---"></a>Ende der Unterstützung für iOS 8.0<!-- 1164477 -->
Verwaltete Apps und die Unternehmensportal-App für iOS benötigen iOS 9.0 und höher, um auf Unternehmensressourcen zugreifen zu können. Geräte, die nicht bis September aktualisiert werden, können nicht mehr auf das Unternehmensportal oder diese Apps zugreifen. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10--1132468--"></a>Hinzufügen der Aktualisierungsaktion zur Unternehmensportal-App für Windows 10<!--1132468-->
In der Unternehmensportal-App für Windows 10 können Benutzer die Daten nun aktualisieren, indem Sie sie aktualisieren (ziehen) oder indem Sie auf dem Desktop auf F5 drücken.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios--739894--"></a>Informieren von Endbenutzern, welche Geräteinformationen für iOS angezeigt werden können<!--739894-->

Wir haben dem Bildschirm „Gerätedetails“ den **Besitzertyp** auf der Unternehmensportal-App für iOS hinzugefügt. So können Benutzer direkt auf dieser Seite mehr über die Privatsphäre in der Dokumentation für Intune-Endbenutzer herausfinden. Sie finden diese Informationen ebenso auf dem Bildschirm „Info“.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment---1169910---"></a>Zugriff auf die Unternehmensportal-App für Android durch Endbenutzer ohne Registrierung<!---1169910--->

Endbenutzer müssen ihr Gerät bald nicht mehr registrieren, um auf die Unternehmensportal-App für Android zugreifen zu können. Endbenutzer innerhalb von Organisationen, die App-Schutzrichtlinien verwenden, werden beim Öffnen der Unternehmensportal-App nicht mehr aufgefordert, ihr Gerät zu registrieren. Zudem können Endbenutzer Apps vom Unternehmensportal installieren, ohne ihr Gerät zu registrieren. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android---1396349---"></a>Vereinfachung der Formulierung für die Unternehmensportal-App für Android<!---1396349--->  

Der Registrierungsvorgang für die Unternehmensportal-App für Android wurde durch einen neuen Text vereinfacht, um Endbenutzern eine einfachere Registrierung zu bieten. Wenn Sie eine benutzerdefinierte Registrierungsdokumentation verwenden, aktualisieren Sie sie gemäß der neuen Bildschirme. Sie können Beispielabbildungen auf unserer Seite [Aktualisierungen für die Benutzeroberfläche für Endbenutzer-Apps in Intune](whats-new-app-ui.md#week-of-september-11-2017) sehen.

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy---677129---"></a>Windows Information Protection-Zulassungsrichtlinie zur Windows 10-Unternehmensportal-App hinzugefügt<!-- 677129 -->

Die Unternehmensportal-App unter Windows 10 wurde aktualisiert, um Unterstützung für Windows Information Protection (WIP) bereitzustellen. Die App kann der WIP-Zulassungsrichtlinie hinzugefügt werden. Aufgrund dieser Änderung muss die App nicht mehr zur Liste **Ausnahme** hinzugefügt werden.


<!-- ########################## -->
## <a name="august-2017"></a>August 2017

### <a name="improvements-to-device-overview---1404453---"></a>Verbesserungen der Geräteübersicht<!-- 1404453 -->  
Die Verbesserungen an der Geräteübersicht zeigen nun registrierte Geräte an, jedoch keine Geräte, die von Exchange ActiveSync verwaltet werden. Exchange ActiveSync-Geräte verfügen nicht über die gleichen Verwaltungsoptionen wie registrierte Geräte. Um die Anzahl der registrierten Geräte und die Anzahl der registrierten Geräte nach Plattform in Intune im Azure-Portal anzuzeigen, navigieren Sie zu **Geräte** > **Übersicht**.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Verbesserungen am von Intune erfassten Gerätebestand
<!-- 961134, 1104426, 1281327, 1333543 -->
In diesem Release haben wir die folgenden Verbesserungen an den Bestandsinformationen vorgenommen, die von den von Ihnen verwalteten Geräten gesammelt werden:
 
- Bei Android-Geräten können Sie nun eine Spalte zum Gerätebestand hinzufügen, die die neueste Patchebene für jedes Gerät anzeigt. Fügen Sie die Spalte **Sicherheitspatchebene** zu Ihrer Geräteliste hinzu, um dies anzuzeigen.
- Wenn Sie in der Geräteansicht filtern, können Sie die Geräte nun nach ihrem Registrierungsdatum filtern. Beispielsweise könnten Sie nur Geräte anzeigen lassen, die nach einem von Ihnen angegebenen Datum registriert wurden.
- Wir haben Verbesserungen an dem Filter vorgenommen, der vom Element **Last Check-in Date** (Letztes Eincheckdatum) verwendet wird.
- In der Geräteliste können Sie jetzt die Telefonnummern von unternehmenseigenen Geräten anzeigen.
Darüber hinaus können Sie den Filterbereich verwenden, um Geräte nach Telefonnummer zu suchen.

Weitere Informationen zum Gerätebestand finden Sie unter [So zeigen Sie den Intune-Gerätebestand an](../remote-actions/device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Unterstützung des bedingten Zugriffs für macOS-Geräte 
<!-- 720172 -->
Sie können nun eine Richtlinie für bedingten Zugriff festlegen, durch die Mac-Geräte bei Intune registriert werden und die Gerätekompatibilitätsrichtlinien einhalten. Benutzer können z.B. die Intune-Unternehmensportal-App für macOS herunterladen und ihre Mac-Geräte bei Intune registrieren. Intune bewertet, ob das Mac-Gerät mit Anforderungen wie PIN, Verschlüsselung, Betriebssystemversion und Systemintegrität kompatibel ist.

- Weitere Informationen finden Sie unter [Unterstützung des bedingten Zugriffs für macOS-Geräte](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview---1484796---"></a>Unternehmensportal-App für macOS befindet sich in öffentlicher Vorschauversion<!---1484796--->
Die Unternehmensportal-App für macOS ist nun als Teil der öffentlichen Vorschauversion für bedingten Zugriff in Enterprise Mobility + Security verfügbar. Diese Version unterstützt macOS 10.11 und höher. Laden Sie sie unter [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal) herunter. 


### <a name="new-device-restriction-settings-for-windows-10"></a>Neue Einstellungen für Geräteeinschränkungen für Windows 10    
<!--1063965, 1308850  -->
In diesem Release haben wir neue Einstellungen für das [Windows 10-Geräteeinschränkungsprofil](/intune/device-restrictions-windows-10) in folgenden Kategorien hinzugefügt:

- Windows Defender SmartScreen
- App Store

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Updates für die Einstellungen des Windows 10 Endpoint Protection-Geräteprofils für BitLocker
<!--1459533 -->    
In diesem Release haben wir die folgenden Verbesserungen daran vorgenommen, wie die BitLocker-Einstellungen in einem Windows 10 Endpoint Protection-Geräteprofil funktionieren:
 
- Wenn Sie unter **BitLocker-Einstellungen für Betriebssystemlaufwerk** für die Einstellung **BitLocker für nicht kompatiblen TPM-Chip** **Blockieren** auswählen, hat dies bisher dazu geführt, dass BitLocker tatsächlich zugelassen ist. Wir haben dies nun behoben, sodass BitLocker blockiert wird, wenn dies ausgewählt wird.
- Unter **BitLocker-Einstellungen für Betriebssystemlaufwerk** können Sie nun für die Einstellung **Zertifikatbasierter Datenwiederherstellungs-Agent** explizit den Agent für zertifikatbasierte Datenwiederherstellung blockieren. Standardmäßig ist der Agent jedoch zulässig.
- Unter **BitLocker-Einstellungen für Festplattenlaufwerk** können Sie nun für die Einstellung **Datenwiederherstellungs-Agent** explizit den Datenwiederherstellungs-Agent blockieren.
Weitere Informationen finden Sie unter [Endpoint protection settings for Windows 10 and later (Endpoint Protection-Einstellungen für Windows 10 und höher)](../protect/endpoint-protection-windows-10.md).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users---621669---"></a>Neue Anmeldefunktion für Benutzer des Android-Unternehmensportals sowie für Benutzer der App-Schutzrichtlinien<!-- 621669 -->
Benutzer können jetzt mithilfe der App des Android-Unternehmensportals Apps durchsuchen, Geräte verwalten und IT-Kontaktinformationen anzeigen, ohne ihre Android-Geräte registrieren zu müssen. Wenn ein Benutzer, der bereits eine App verwendet, die durch Richtlinien zum Intune-App-Schutz geschützt ist, zusätzlich die Android-Unternehmensportal-App startet, dann enthält er zukünftig keine Aufforderung mehr, das Gerät zu registrieren.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization--1405990--"></a>Neue Einstellung in der Android-Unternehmensportal-App für die Akkuoptimierung<!--1405990-->
Auf der Seite **Einstellungen** in der Unternehmensportal-App für Android ist eine neue Einstellung verfügbar, mit der Benutzer die Akkuoptimierung einfach für Unternehmensportal- und Microsoft Authenticator-Apps ausschalten können. Der in der Einstellung dargestellte Name der App hängt davon ab, welche App das Geschäftskonto verwaltet. Benutzern wird empfohlen, die Akkuoptimierung zugunsten besserer Leistung von Work-Apps auszuschalten, die E-Mails und Daten synchronisieren. 

### <a name="multi-identity-support-for-onenote-for-ios--------1234281---"></a>Unterstützung mehrerer Identitäten für OneNote für iOS     <!-- 1234281 -->
Benutzer können jetzt verschiedene Konten (geschäftlich und privat) mit Microsoft OneNote für iOS verwenden. App-Schutzrichtlinien können auf Unternehmensdaten in Arbeitsnotizbüchern angewendet werden, ohne dass persönliche Notizbücher betroffen sind. Beispielsweise kann eine Richtlinie einem Benutzer erlauben, Informationen in Arbeitsnotizbüchern zu suchen, verhindert jedoch, dass der Benutzer Unternehmensdaten aus dem Arbeitsnotizbuch in ein persönliches Notizbuch kopiert.
 
- Erfahren Sie mehr über die Apps, die [App-Schutz und mehrere Identitäten](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) mit Intune unterstützen.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Neue Einstellungen zum Zulassen und Blockieren von Apps auf Samsung KNOX Standard-Geräten
<!-- 1305423 822899-->  
In dieser Version werden neue [Einstellungen für Geräteeinschränkungen](../configuration/device-restrictions-android.md) hinzugefügt, mit denen Sie die folgenden App-Listen angeben können:
 
- Apps, die Benutzer installieren dürfen
- Apps, für deren Ausführung Benutzer blockiert sind
- Apps, die vor dem Benutzer auf dem Gerät verborgen werden
 
Sie können die Apps mithilfe der URL, des Paketnamens oder der Liste der Apps, die Sie verwalten, angeben.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Neue App-basierte Benutzeroberflächenverknüpfung für Azure AD-Richtlinien für bedingten Zugriff in Intune
<!-- 1016201 -->
IT-Administratoren können nun App-basierte Richtlinien für bedingten Zugriff über die neue Benutzeroberfläche für Richtlinien für bedingten Zugriff in der Azure AD-Workload festlegen. Der App-basierte bedingte Zugriff, der sich im Bereich „Intune-App-Schutz“ im Azure-Portal befindet, bleibt dort vorläufig und wird parallel erzwungen. Es ist zudem ein praktischer Link zur neuen Benutzeroberfläche der Richtlinie für bedingten Zugriff in der Intune-Workload verfügbar.

- Weitere Informationen zum [App-basierten bedingten Zugriff in Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).

<!-- ########################## -->
## <a name="july-2017"></a>Juli 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version-----1333256--1245463----"></a>Einschränken von Registrierungseinschränkungen für Android- und iOS-Geräte nach Betriebssystemversion <!--- 1333256,  1245463 --->
Intune unterstützt jetzt die Einschränkung der iOS- und Android-Registrierung nach der Versionsnummer des Betriebssystems. Der IT-Administrator kann jetzt unter **Gerätetypeinschränkung** eine Plattformkonfiguration festlegen, um die Registrierung zwischen einem minimalen und maximalen Betriebssystemwert festzulegen. Android-Betriebssystemversionen müssen als „Major.Minor.Build.Rev“ angegeben werden, wobei „Minor“, „Build“ und „Rev“ optional sind. iOS-Versionen müssen als „Major.Minor.Build“ angegeben werden, wobei „Minor“ und „Build“ optional sind. Weitere Informationen zu [Geräteregistrierungseinschränkungen](../enrollment/enrollment-restrictions-set.md).

>[!NOTE]
>Schränkt nicht die Registrierung mit Apple-Registrierungsprogrammen oder Apple Configurator ein.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment-----1333272--1333275-1245709----"></a>Einschränken von Geräteregistrierungen persönlicher Geräte mit Android, iOS und macOS <!--- 1333272,  1333275, 1245709 --->
Intune kann die Registrierung persönlicher Geräte einschränken, indem es IMEI-Nummern von Unternehmensgeräten auf eine Positivliste setzt. Diese Funktion von Intune wurde nun auf iOS, Android und macOS mit Geräteseriennummern erweitert. Durch Hochladen der Seriennummern in Intune können Sie Geräte vorab als unternehmenseigen deklarieren. Persönliche Geräte können mit Registrierungseinschränkungen blockiert werden, indem die Registrierung nur für unternehmenseigene Geräte zugelassen wird. Weitere Informationen zu [Geräteregistrierungseinschränkungen](../enrollment/enrollment-restrictions-set.md).

Zum Importieren von Seriennummern gehen Sie zu **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten**, und klicken Sie auf **Hinzufügen**. Laden Sie dann eine CSV-Datei hoch (ohne Kopfzeile, zwei Spalten für Seriennummer und Details wie IMEI-Nummern). Zur Einschränkung von privaten Geräten gehen Sie zu **Geräteregistrierung** > **Registrierungseinschränkungen**. Klicken Sie unter **Gerätetypbeschränkungen** auf die Option **Standard** und anschließend auf **Plattformkonfigurationen**. Sie können private Geräte für iOS, Android und macOS **Zulassen** oder **Blockieren**.


### <a name="new-device-action-to-force-devices-to-sync-with-intune---711369---"></a>Neue Geräteaktion zur erzwungenen Synchronisierung von Geräten mit Intune<!-- 711369 -->
In dieser Version haben wir eine neue Geräteaktion hinzugefügt, die das ausgewählte Gerät zwingt, sofort bei Intune einzuchecken. Checkt ein Gerät ein, empfängt es sofort alle ihm zugewiesenen ausstehenden Aktionen oder Richtlinien.  Dadurch können Sie sofort zugewiesene Richtlinien überprüfen und Probleme beheben, ohne den nächsten geplanten Check-In abwarten zu müssen.
Mehr Informationen finden Sie unter [Synchronisieren von Geräten](../remote-actions/device-sync.md).

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update---777100---"></a>Erzwingen der automatischen Installation des neuesten Softwareupdates bei überwachten iOS-Geräten<!-- 777100 -->
Eine neue Richtlinie aus dem Softwareupdate-Arbeitsbereich ist verfügbar, die für überwachte iOS-Geräte die automatische Installation des neuesten Softwareupdates erzwingt. Weitere Informationen finden Sie unter [Konfigurieren von iOS-Aktualisierungsrichtlinien](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner----954651-1172027---"></a>Check Point SandBlast Mobile: neuer Mobile Threat Defense-Partner <!-- 954651, 1172027 -->
Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen mit bedingtem Zugriff basierend auf Risikobewertungen steuern, die von Check Point SandBlast Mobile vorgenommen werden, einer Mobile Threat Defense-Lösung, die in Microsoft Intune integriert ist.

#### <a name="how-integration-with-intune-works"></a>Funktionsweise der Integration mit Intune
Das Risiko wird basierend auf Telemetriedaten von Geräten bewertet, auf denen Check Point SandBlast Mobile ausgeführt wird. Sie können Richtlinien für bedingten EMS-Zugriff basierend auf Risikobewertungen von Check Point SandBlast Mobile konfigurieren, die mithilfe von Intune-Gerätekompatibilitätsrichtlinien aktiviert werden. Sie können den Zugriff nicht kompatibler Geräte auf Unternehmensressourcen anhand der erkannten Bedrohungen zulassen oder blockieren.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business---748101---"></a>Bereitstellen einer im Microsoft Store für Unternehmen verfügbaren App<!-- 748101 -->
Ab dieser Version können Administratoren Apps zuweisen, sobald sie im Microsoft Store für Unternehmen verfügbar werden. Wenn eine App als verfügbar markiert wird, können Benutzer diese aus der Unternehmensportal-App oder von der Website installieren, ohne vom Microsoft Store eingeschränkt zu werden.

### <a name="ui-updates-to-the-company-portal-website--1313244-part-1--"></a>Updates für die Benutzeroberfläche der Unternehmensportalwebsite<!--1313244 part 1-->
Wir haben mehre Updates für die Benutzeroberfläche der [Unternehmensportal-Website](https://portal.manage.microsoft.com) durchgeführt, um die Endbenutzererfahrung zu verbessern.

- __Verbesserungen der App-Kacheln__: App-Symbole werden nun mit einem automatisch generierten Hintergrund basierend auf der dominanten Farbe des Symbols angezeigt (falls diese erkannt wird). Wenn möglich, ersetzt dieser Hintergrund die graue Trennlinie, die zuvor auf App-Kacheln sichtbar war.

    Die Unternehmensportalwebsite zeigt in einer kommenden Version wenn möglich große Symbole an. Es wird empfohlen, dass Administratoren Apps mithilfe von hochauflösenden Symbolen mit einer Mindestgröße von 120x120 Pixeln bereitstellen. 

- __Änderungen in der Navigation__: Elemente auf der Navigationsleiste wurden in das Hamburger-Menü oben links verschoben. Die Seite „Kategorien“ wurde entfernt. Benutzer können nun Inhalt beim Durchsuchen nach Kategorie filtern.

- __Updates an empfohlenen Apps__: Wir haben der Website eine dedizierte Seite hinzugefügt, auf der Benutzer Apps durchsuchen können, die Sie präsentieren, und haben einige Optimierungen auf der Benutzeroberfläche für den Abschnitt „Featured“ (Empfohlen) auf der Homepage vorgenommen.

### <a name="ibooks-support-for-the-company-portal-website--1231841--"></a>Unterstützung für iBooks auf der Unternehmensportalwebsite<!--1231841-->
Wir haben eine dedizierte Seite im Unternehmensportal hinzugefügt, über die Benutzer iBooks durchsuchen und herunterladen können. 


### <a name="additional-help-desk-troubleshooting-details-----applies-to-1263399-1326964-1341642----"></a>Zusätzliche Informationen für die Problembehandlung im Helpdesk<!---  Applies to 1263399, 1326964, 1341642 --->
In Intune wurde die Anzeige für die Problembehandlung und die Informationen aktualisiert, die dort für Administratoren und Helpdesk-Personal bereitstellt werden. Sie finden dort nun eine **Zuweisungstabelle**, die alle Zuweisungen für den Benutzer auf Grundlage der Gruppenmitgliedschaft zusammenfasst. Diese Liste enthält:
- Mobile Apps
- Konformitätsrichtlinien
- Konfigurationsprofile

Darüber hinaus enthält die Tabelle **Geräte** jetzt die Spalten **Azure AD-Verknüpfungstyp** und **Azure AD-konform**. Weitere Informationen finden Sie unter [Verwenden des Problembehandlungsportals, um Benutzern zu helfen](../help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Intune Data Warehouse (Öffentliche Vorschau)
Intune Data Warehouse prüft täglich die Daten, um eine Verlaufsansicht Ihres Mandanten bereitzustellen. Sie können mit einer Power BI-Datei (PBIX), einem OData-Link, der mit vielen Analysetools kompatibel ist, oder durch die Interaktion mit der REST-API auf die Daten zugreifen. Weitere Informationen finden Sie unter [Verwenden des Data Warehouse von Intune](../developer/reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10---676547---"></a>Verfügbarkeit heller und dunkler Modi für die Unternehmensportal-App für Windows 10<!---676547--->
Endbenutzer können den Farbmodus für die Unternehmensportal-App für Windows 10 anpassen. Benutzer können die Änderung im Abschnitt „Einstellungen“ der Unternehmensportal-App durchführen. Die Änderung wird nach einem Neustart der App vorgenommen. Bei Windows 10 Version 1607 und höher ist der App-Modus standardmäßig Teil der Systemeinstellung. Für Windows 10 Version 1511 und früher ist der App-Modus standardmäßig auf „Hell“ festgelegt.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10---807046--"></a>Kennzeichnen ihrer Gerätegruppe in der Unternehmensportal-App für Windows 10 durch Endbenutzer<!---807046-->
Endbenutzer können nun wählen, zu welcher Gruppe ihr Gerät gehört, indem sie es direkt innerhalb der Unternehmensportal-App für Windows 10 kennzeichnen.

<!-- ########################## -->
## <a name="june-2017"></a>Juni 2017

### <a name="new-role-based-administration-access-for-intune-admins-----1099990---"></a>Neuer rollenbasierter Administratorenzugriff für Intune-Administratoren  <!-- 1099990 -->  
Eine neue Administratorrolle für bedingten Zugriff wird hinzugefügt, um Azure AD-Richtlinien für bedingten Zugriff zu erstellen, zu ändern und zu löschen. Vorher besaßen nur globale Administratoren und Sicherheitsadministratoren diese Berechtigung. Diese Rollenberechtigung kann Intune-Administratoren erteilt werden, damit diese Zugriff auf Richtlinien für bedingten Zugriff haben.


### <a name="tag-corporate-owned-devices-with-serial-number---1215070---"></a>Markieren von unternehmenseigenen Geräten mit Seriennummer<!-- 1215070 -->  
Intune unterstützt nun das Hochladen von iOS-, macOS- und Android-Seriennummern als IDs für unternehmenseigene Geräte. Sie können anhand von Seriennummern derzeit keine persönlichen Geräte für die Registrierung blockieren, da Seriennummern bei der Registrierung nicht überprüft werden. Die Funktion zum Blockieren persönlicher Geräte durch Seriennummer wird in Kürze veröffentlicht.


### <a name="new-remote-actions-for-ios-devices---854689---"></a>Neue Remoteaktionen für iOS-Geräte<!-- 854689 -->
In dieser Version haben wir zwei neue remote Geräteaktionen für freigegebene iPad-Geräte hinzugefügt, die die Apple Classroom-App verwalten:

- [Aktuellen Benutzer abmelden](../remote-actions/device-logout-user.md): Meldet den aktuellen Benutzer eines von Ihnen gewählten iOS-Geräts ab.
- [Benutzer entfernen](../remote-actions/device-remove-user.md): Löscht einen von Ihnen ausgewählten Benutzer aus dem lokalen Cache eines iOS-Geräts.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app---1044681---"></a>Unterstützung für gemeinsam genutzte iPads mit der Classroom-App für iOS<!-- 1044681 -->
In diesem Release haben wir die Unterstützung für die Verwaltung der Classroom-App (iOS) erweitert, um Schüler und Studenten einzubeziehen, die sich mithilfe ihrer verwalteten Apple-ID auf gemeinsam genutzten iPads anmelden.


### <a name="changes-to-intune-built-in-apps---1332306---"></a>Änderungen an integrierten Intune-Apps<!-- 1332306 -->
Zuvor enthielt Intune eine Reihe integrierter Apps, die Sie rasch zuweisen konnten. Auf Grundlage Ihrer Feedbacks haben wir diese Liste entfernt, und es werden keine integrierten Apps mehr angezeigt.
Wenn Sie jedoch schon integrierte Apps zugewiesen haben, werden sie noch immer auf der App-Liste angezeigt. Sie können diese Apps weiter nach Bedarf zuweisen.
Es ist geplant, in einer späteren Version eine einfachere Methode hinzuzufügen, um integrierte Apps über das Azure-Portal auszuwählen und zuzuweisen.

### <a name="easier-installation-of-office-365-apps----1121362----"></a>Einfachere Installation von Office 365-Apps<!--- 1121362 --->
Der neue App-Typ von **Office 365 ProPlus** erleichtert Ihnen die Zuweisung von Office 365 ProPlus-2016-Apps zu von Ihnen verwalteten Geräten, die mit der neuesten Version von Windows 10 ausgeführt werden. Darüber hinaus erhalten Sie die Möglichkeit, Microsoft Project und Microsoft Visio zu installieren, wenn Sie über die entsprechenden Lizenzen verfügen. Die gewünschten Apps werden gebündelt und in der Intune-Konsole als einzelne App in der App-Liste angezeigt.
Weitere Informationen finden Sie unter [How to add Office 365 apps for Windows 10 (Hinzufügen von Office 365-Apps für Windows 10)](../apps/apps-add-office365.md).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business----777044----"></a>Unterstützung für Offline-Apps aus dem Microsoft Store für Unternehmen<!--- 777044 --->
Offline-Apps, die Sie über den Microsoft Store für Unternehmen erworben haben, werden nun mit dem Azure-Portal synchronisiert. Sie können diese Apps dann für Geräte- oder Benutzergruppen bereitstellen. Offline-Apps werden durch Intune und nicht durch den Store installiert.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps-----1257019---"></a>Microsoft Teams befindet sich jetzt auf der App-basierten Zertifizierungsstellenliste der genehmigten Apps  <!-- 1257019 -->
Die Microsoft Teams-App für iOS und Android ist nun Bestandteil der genehmigten Apps für Richtlinien für App-basierten bedingten Zugriff für Exchange und SharePoint Online. Im Azure-Portal kann die App über das Blatt „Intune-App-Schutz“ für alle Mandanten konfiguriert werden, die derzeit auf den App-basierten bedingten Zugriff zurückgreifen.

### <a name="managed-browser-and-app-proxy-integration---1287310---"></a>Verwaltete Browser- und App-Proxy-Integration<!-- 1287310 -->
Der Intune Managed Browser kann nun mit dem Azure AD-Anwendungsproxydienst integriert werden, damit Benutzer auf interne Websites zugreifen können, auch wenn Sie remote arbeiten. Benutzer des Browsers geben einfach wie gewohnt die Website-URL ein, und der Managed Browser leitet die Anfrage über das Anwendungsproxy-Webgateway weiter. Weitere Informationen finden Sie unter [Verwalten des Internetzugriffs mittels Richtlinien für verwaltete Browser](../apps/app-configuration-managed-browser.md).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser---682951---"></a>Neue App-Konfigurationseinstellungen für Intune Managed Browser<!-- 682951 -->
In dieser Version haben wir weitere Konfigurationen für die Intune Managed Browser-App für iOS und Android hinzugefügt. Die Standardhomepage und -lesezeichen für den Browser können mit einer App-Konfigurationsrichtlinie konfiguriert werden.
Weitere Informationen finden Sie unter [Verwalten des Internetzugriffs mittels Richtlinien für verwaltete Browser](../apps/app-configuration-managed-browser.md).

### <a name="bitlocker-settings-for-windows-10----951707---"></a>Einstellungen für BitLocker für Windows 10 <!-- 951707 -->
Sie können jetzt die BitLocker-Einstellungen für Windows 10-Geräte, mithilfe eines neuen Intune Geräteprofils konfigurieren. Sie können z.B. anfordern, dass Geräte verschlüsselt werden und auch weitere Einstellungen konfigurieren, die angewendet werden, wenn BitLocker aktiviert wird.
Weitere Informationen finden Sie unter [Endpoint protection settings for Windows 10 and later (Endpoint Protection-Einstellungen für Windows 10 und höher)](../protect/endpoint-protection-windows-10.md).

### <a name="new-settings-for-windows-10-device-restriction-profile----978527--978550-978569-1050031-1058611-----"></a>Neue Einstellungen für das Windows 10-Geräteeinschränkungsprofil<!--- 978527,  978550, 978569, 1050031, 1058611,  --->
In dieser Version haben wir neue Einstellungen für das Windows 10-Geräteeinschränkungsprofil in folgenden Kategorien hinzugefügt:

- Windows Defender
- Mobilfunk und Konnektivität
- Gesperrter Bildschirm
- Datenschutz
- Suchen
- Windows-Blickpunkt
- Microsoft Edge

Weitere Informationen zu Einstellungen für Windows 10 finden Sie unter [Einstellungen für Geräteeinschränkungen für Windows 10 und höher in Microsoft Intune](../configuration/device-restrictions-windows-10.md).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies--1305217--"></a>Unternehmensportal-App für Android verfügt nun über neue Endbenutzeroberfläche für App-Schutzrichtlinien<!--1305217-->
Auf Grundlage von Benutzerfeedback haben wir die Unternehmensportal-App für Android modifiziert, sodass sie nun die Schaltfläche **Auf Unternehmensinhalte zugreifen** besitzt. Zweck ist das Verhindern, dass Endbenutzer unnötigerweise den Registrierungsprozess durchlaufen, wenn sie lediglich auf Apps zugreifen müssen, die App-Schutzrichtlinien unterstützen, eine Funktion zur Verwaltung mobiler Anwendungen durch Intune. Sie können diese Änderungen auf der Seite [Was gibt es Neues auf der App-Benutzeroberfläche](whats-new-app-ui.md) anzeigen.

### <a name="new-menu-action-to-easily-remove-company-portal--1164569--"></a>Neue Menüaktion zum mühelosen Entfernen des Unternehmensportals<!--1164569-->
Basierend auf Benutzerfeedback wurde der Unternehmensportal-App für Android eine neue Menüaktion hinzugefügt, über die das Entfernen des Unternehmensportals von Ihrem Gerät eingeleitet werden kann. Über diese Aktion wird das Gerät aus der Intune-Verwaltung entfernt, damit die App vom Benutzer vom Gerät entfernt werden kann. Sie sehen diese Änderungen auf der Seite zu den [Neuerungen auf der Benutzeroberfläche der App](whats-new-app-ui.md) und in der [Android-Endbenutzerdokumentation](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update--676505--"></a>Verbesserungen bei der App-Synchronisierung mit dem Windows 10 Creators Update<!--676505-->
Die Unternehmensportal-App für Windows 10 löst nun automatisch eine Synchronisierung für App-Installationsanforderungen für Geräte mit dem Windows 10 Creators Update (Version 1703) aus. Dadurch wird das Problem beseitigt, dass App-Installationen während des Zustands „Synchronisierung ausstehend“ verzögert reagieren. Darüber hinaus können Benutzer in der App manuell eine Synchronisierung auslösen. Sie können diese Änderungen auf der Seite [Was gibt es Neues auf der App-Benutzeroberfläche](whats-new-app-ui.md) anzeigen.

### <a name="new-guided-experience-for-windows-10-company-portal---1058938---"></a>Neues benutzerfreundlicheres Windows 10-Unternehmensportal<!---1058938--->
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

<!-- ########################## -->
## <a name="may-2017"></a>Mai 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices--1103950--"></a>Ändern der MDM-Autorität ohne Aufhebung der Registrierung für verwaltete Geräte<!--1103950-->
Sie können nun Ihre MDM-Autorität ändern, ohne sich an den Microsoft-Support wenden und die Aufhebung der Registrierung sowie die erneute Registrierung vorhandener verwalteten Geräte durchführen zu müssen. In der Configuration Manager-Konsole können Sie Ihre [MDM-Autorität ändern](/sccm/mdm/deploy-use/change-mdm-authority), und zwar von der Festlegung auf Configuration Manager (hybrid) in Microsoft Intune (eigenständig) oder umgekehrt.


### <a name="improved-notification-for-samsung-knox-startup-pins--1087143--"></a>Verbesserte Benachrichtigung für Samsung KNOX-Systemstart-PINs<!--1087143-->
Wenn Endbenutzer eine Systemstart-PIN für Samsung KNOX-Geräte festlegen müssen, um Konformität hinsichtlich der Verschlüsselung zu erzielen, führt die für Endbenutzer angezeigte Benachrichtigung diese beim Tippen auf die Benachrichtigung genau zu der Stelle in der App „Einstellungen“.  Zuvor hat die Benachrichtigung den Endbenutzer zum Bildschirm für die Kennwortänderung geführt.

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="apple-school-manager-asm-support-with-shared-ipad---748864-770395--"></a>Unterstützung für Apple School Manager (ASM) auf gemeinsam genutztem iPad<!-- 748864, 770395-->

Intune unterstützt jetzt die Verwendung von Apple Schule Manager (ASM) anstelle des Apple-Programms zur Geräteregistrierung, um die integrierte Registrierung von iOS-Geräten zu ermöglichen. ASM-Onboarding ist erforderlich, um die Classroom-App für gemeinsam genutzte iPads zu verwenden. Zudem ist es erforderlich, um das Synchronisieren von Daten von ASM zu Azure Active Directory über SDS (Microsoft School Data Sync) zu aktivieren. Weitere Informationen finden Sie unter [Aktivieren der iOS-Geräteregistrierung mit Apple School Manager](../enrollment/apple-school-manager-set-up-ios.md).

> [!NOTE]
> Das Konfigurieren gemeinsam genutzter iPads für die Nutzung der App „Classroom“ erfordert iOS Education-Konfigurationen in Azure, die noch nicht verfügbar sind.  Diese Funktionalität wird bald hinzugefügt.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer---675418---"></a>Bereitstellen von Remoteunterstützung auf Android-Geräten mithilfe von TeamViewer<!-- 675418 -->

Intune kann nun die nicht im Lieferumfang inbegriffene [TeamViewer](https://www.teamviewer.com)-Software nutzen, damit Sie Ihren Benutzern mit Android-Geräten Remoteunterstützung bieten können. Weitere Informationen finden Sie unter [Bereitstellen von Remoteunterstützung für von Intune verwaltete Android-Geräte](../remote-actions/teamviewer-support.md).

### <a name="app-management"></a>App-Verwaltung

#### <a name="new-app-protection-policies-conditions-for-mam---679864---"></a>Neue Bedingungen für App-Schutzrichtlinien für MAM<!-- 679864 -->

Sie können nun eine Anforderung für MAM ohne Registrierung von Benutzern festlegen, die die folgenden Richtlinien erzwingt:

- Minimale Anwendungsversion
- Minimale Betriebssystemversion
- Mindestversion für Intune App SDK für die Zielanwendung (nur iOS)

Diese Funktion ist für Android und iOS verfügbar. Intune unterstützt die Durchsetzung einer Mindestversion für Betriebssystemplattformen, Anwendungen und das Intune App SDK. Unter iOS können Anwendungen mit integriertem SDK auch eine Durchsetzung einer Mindestversion auf SDK-Ebene festlegen. Der Benutzer kann nicht auf die Zielanwendung zugreifen, wenn die Mindestanforderungen der App-Schutzrichtlinie auf den drei oben aufgeführten verschiedenen Ebenen nicht erfüllt werden. An diesem Punkt kann der Benutzer entweder sein Konto entfernen (für Anwendungen mit mehreren Identitäten), die Anwendung schließen oder seine Betriebssystem- bzw. Anwendungsversion aktualisieren.

Sie können zusätzliche Einstellungen konfigurieren, um eine nicht blockierende Benachrichtigung bereitzustellen, die ein Upgrade des Betriebssystems oder der Anwendung empfiehlt. Diese Benachrichtigung kann geschlossen und die Anwendung wie gewohnt verwendet werden.

Weitere Informationen finden Sie unter [Einstellungen für App-Schutzrichtlinien für iOS](../apps/app-protection-policy-settings-ios.md) und [Einstellungen für App-Schutzrichtlinien für Android](../apps/app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work---621621---"></a>Konfigurieren von App-Konfigurationen für Android for Work<!-- 621621 -->
Einige Android-Apps aus dem Store unterstützen verwaltete Konfigurationsoptionen, mit denen ein IT-Administrator steuern kann, wie eine App im Arbeitsprofil ausgeführt wird. Mit Intune können Sie jetzt die von einer App unterstützten Konfigurationen anzeigen und sie im Azure-Portal mithilfe eines Konfigurations-Designers oder JSON-Editors konfigurieren. Weitere Informationen finden Sie unter [Verwenden von App-Konfigurationen für Android for Work](../apps/app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment---677969---"></a>Neue App-Konfigurationsfunktion für MAM ohne Registrierung<!-- 677969 -->
Sie können jetzt App-Konfigurationsrichtlinien über die Verwaltung mobiler Anwendungen (MAM) ohne Registrierungskanal erstellen. Dieses Feature entspricht den App-Konfigurationsrichtlinien, die in der App-Konfiguration für die mobile Geräteverwaltung (MDM) verfügbar sind. Ein Beispiel für die App-Konfiguration mit MAM ohne Registrierung finden Sie unter [Verwalten des Internetzugriffs mittels Richtlinien für Managed Browser mit Microsoft Intune](../apps/app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser---682960---"></a>Konfigurieren von Listen zugelassener und blockierter URLs für den Managed Browser<!-- 682960 -->
Sie können jetzt eine Liste zulässiger und blockierter Domänen und URLs für den Intune Managed Browser mithilfe von App-Konfigurationseinstellungen im Azure-Portal konfigurieren. Diese Einstellungen können unabhängig davon verwaltet werden, ob der Browser auf einem verwalteten oder nicht verwalteten Gerät verwendet wird. Weitere Informationen finden Sie unter [Verwalten des Internetzugriffs mittels Richtlinien für Managed Browser mit Microsoft Intune](../apps/app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view---1069473---"></a>Helpdeskansicht der App-Schutzrichtlinie<!-- 1069473 -->
IT-Helpdeskbenutzer können nun den Benutzerlizenzstatus und Status von App-Schutzrichtlinien, die Benutzern zugewiesen sind, auf dem Blatt „Problembehandlung“ überprüfen. Weitere Informationen finden Sie unter [Problembehandlung](./help-desk-operators.md).

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="control-website-visits-on-ios-devices---723832---"></a>Steuern von Websitebesuchen auf iOS-Geräten<!-- 723832 -->
Sie können nun mithilfe einer der beiden folgenden Methoden steuern, welche Websites Benutzer von iOS-Geräten besuchen können:

- Zulässige und blockierte URLs mit dem integrierten Webinhaltsfilter von Apple hinzufügen

- Erlauben, dass nur auf bestimmte Websites vom Safari-Browser aus zugegriffen werden darf. Lesezeichen werden in Safari für jede Website erstellt, die Sie angeben.

Weitere Informationen finden Sie im Artikel zu [Filtereinstellungen für Webinhalte auf iOS-Geräten](../configuration/ios-device-features-settings.md#web-content-filter).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps---621614---"></a>Vorkonfigurieren von Geräteberechtigungen für Android for Work-Apps<!-- 621614 -->
Für Apps, die für Android for Work-Gerätearbeitsprofile bereitgestellt werden, können Sie nun den Berechtigungszustand für einzelne Apps konfigurieren.  Standardmäßig fordern Android-Apps, die Geräteberechtigungen erfordern (z. B. Zugriff auf den Standort oder die Gerätekamera), die Benutzer zum Annehmen oder Ablehnen der Berechtigungen auf.  Wenn eine App z. B. das Gerätemikrofon verwendet, wird der Endbenutzer aufgefordert, der App die Berechtigung zur Verwendung des Mikrofons zu erteilen. Dieses Feature gestattet Ihnen, die Berechtigungen im Namen des Endbenutzers zu definieren.  Sie können Berechtigungen konfigurieren, um diese a) automatisch ohne Benachrichtigung des Benutzers zu verweigern, b) automatisch ohne Benachrichtigung des Benutzers zu genehmigen oder c) den Benutzer zum Genehmigen oder Verweigern auffordern. Weitere Informationen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android for Work-Geräte in Microsoft Intune](../configuration/device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices---728976-1102534---"></a>Definieren einer App-spezifischen PIN für Android for Work-Geräte<!-- 728976, 1102534 -->
Android-Geräte ab Version 7.0 mit einem als Android for Work-Gerät verwalteten Arbeitsprofil ermöglichen dem Administrator das Definieren einer Kennungsrichtlinie, die nur für Apps im Arbeitsprofil gilt.  Zu den Optionen gehören:

- Definieren einer geräteweiten Kennungsrichtline: Dies ist die vom Endbenutzer zu verwendende Kennung, um sein gesamtes Gerät zu entsperren.
- Definieren einer Kennungsrichtlinie für das Arbeitsprofil: Benutzer werden zur Eingabe einer Kennung aufgefordert, sobald eine App im Arbeitsprofil geöffnet wird.
- Definieren einer Geräterichtlinie und einer Arbeitsprofilrichtlinie: Die IT-Abteilung hat die Möglichkeit, eine gerätebezogene und eine arbeitsprofilbezogene Kennungsrichtlinie mit unterschiedlicher Stärken zu erstellen (z.B. eine vierstellige PIN zum Entsperren des Geräts, aber eine sechsstellige PIN zum Öffnen einer arbeitsbezogenen App).

Weitere Informationen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android for Work-Geräte in Microsoft Intune](../configuration/device-restrictions-android-for-work.md).

> [!NOTE]
> Dies ist nur unter Android 7.0 und höher möglich.  Standardmäßig kann der Endbenutzer die beiden separat definierten PINs verwenden oder diese zu einer PIN kombinieren, die die Stärke der jeweils stärkeren PIN übernimmt.

#### <a name="new-settings-for-windows-10-devices---978585---"></a>Neue Einstellungen für Windows 10-Geräte<!-- 978585 -->
Wir haben neue [Einstellungen zur Windows-Geräteeinschränkung](../configuration/device-restrictions-windows-10.md) hinzugefügt, die Features wie drahtlose Anzeigen, Geräteerkennung, Programmumschaltung und Fehlermeldungen von SIM-Karten steuern.

#### <a name="updates-to-certificate-configuration---918991-and-823198---"></a>Updates der Zertifikatkonfiguration<!-- 918991 and 823198 -->
Beim Erstellen eines SCEP-Zertifikatprofils für <strong>Format des Antragstellernamens</strong> steht die Option <strong>Benutzerdefiniert</strong> für iOS-, Android- und Windows-Geräte zur Verfügung. Vor dieser Aktualisierung war das Feld <strong>Benutzerdefiniert</strong> nur für iOS-Geräte verfügbar. Weitere Informationen finden Sie unter [Erstellen eines SCEP-Zertifikatprofils](../protect/certificates-profile-scep.md).

Beim Erstellen eines SCEP-Zertifikatprofils für **Alternativer Antragstellername** steht die Option **Benutzerdefiniertes Azure AD-Attribut** zur Verfügung. Die Option **Abteilung** ist verfügbar, wenn Sie **Benutzerdefiniertes Azure AD-Attribut** auswählen. Weitere Informationen finden Sie unter [Erstellen eines PKCS-Zertifikatprofils](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode---662059---"></a>Konfigurieren mehrerer Apps, die ausgeführt werden können, wenn sich ein Android-Gerät im Kioskmodus befindet<!-- 662059 -->
Wenn sich ein Android-Gerät im Kioskmodus befindet, konnte zuvor nur eine App konfiguriert werden, die ausgeführt werden durfte. Sie können jetzt mehrere Apps unter Verwendung der App-ID, der Speicher-URL oder durch Auswahl einer Android-App konfigurieren, die Sie bereits verwalten. Weitere Informationen finden Sie unter [Kioskmoduseinstellungen](../configuration/device-restrictions-android.md#kiosk).

<!-- ########################## -->
## <a name="april-2017"></a>April 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Unterstützung der Verwaltung der Apple-App Classroom
Sie können jetzt die iOS-App Classroom auf iPad-Geräten verwalten. Richten Sie die Classroom-App auf dem iPad der Lehrkraft mit den ordnungsgemäßen Schulungsraums- und Schüler-/Studentendaten ein. Konfigurieren Sie anschließend die iPads der Schüler/Studenten, die für einen Schulungsraum registriert sind, damit Sie deren Nutzung der App steuern können.
Einzelheiten finden Sie unter [Konfigurieren von iOS-Einstellungen für Bildungseinrichtungen](education-settings-configure-ios.md)

### <a name="support-for-managed-configuration-options-for-android-apps---621621---"></a>Unterstützung für verwaltete Konfigurationsoptionen für Android-Apps<!-- 621621 -->
Android-Apps im Play Store, die verwaltete Konfigurationsoptionen unterstützen, können jetzt von Intune konfiguriert werden.  Mit dieser Funktion kann die IT die Liste der Konfigurationswerte sehen, die von einer App unterstützt werden, und es wird eine übersichtliche, hochwertige Benutzeroberfläche bereitgestellt, damit die IT diese Werte konfigurieren kann.

### <a name="new-android-policy-for-complex-pins---722069---"></a>Neue Android-Richtlinie für komplexe PINs<!-- 722069 -->
Sie können jetzt einen erforderlichen numerisch-komplexen [Kennworttyp](../configuration/device-restrictions-android.md#password) in einem Android-Geräteprofil für Geräte festlegen, auf denen Android 5.0 und höher ausgeführt wird.  Verwenden Sie diese Einstellung, um zu verhindern, dass Benutzer eine PIN erstellen, die sich wiederholende oder aufeinanderfolgende Zahlen enthält, z.B. 1111 oder 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Zusätzliche Unterstützung für Android for Work-Geräte
- **Verwalten von Kennwort- und Arbeitsprofileinstellungen**<!-- 612808 -->

  Mit dieser neuen Einschränkungsrichtlinie für Android for Work-Geräte können Sie jetzt Kennwort- und Arbeitsprofileinstellungen auf von Ihnen verwalteten Android for Work-Geräten verwalten.

- **Datenaustausch zwischen Arbeitsprofilen und persönlichen Profilen zulassen**<!-- 1045102 -->

Dieses Profil zur Einschränkung von Android for Work-Geräten weist jetzt neue Optionen auf, mit denen Sie die gemeinsame Datennutzung von Arbeits- und persönlichen Profilen konfigurieren können.

- **Beschränken von Kopieren und Einfügen zwischen Arbeitsprofilen und persönlichen Profilen**<!-- 1046094 -->

  Mit einem neuen benutzerdefinierten Geräteprofil für Android for Work-Geräte können Sie einschränken, ob Kopier- und Einfügeaktionen zwischen Arbeits- und persönlichen Apps zulässig sind oder nicht.

Weitere Informationen finden Sie unter [Geräteeinschränkungen für Android for Work](../configuration/device-restrictions-android-for-work.md).

### <a name="assign-lob-apps-to-ios-and-android-devices---1057568---"></a>Zuweisen von branchenspezifischen Apps zu iOS- und Android-Geräten<!-- 1057568 -->
Sie können Benutzern oder Geräten branchenspezifische Apps für [iOS](../apps/lob-apps-ios.md) (IPA-Dateien) und [Android](../apps/lob-apps-android.md) (APK-Dateien) zuweisen.


### <a name="new-device-policies-for-ios---723774-723815-723826-723830---"></a>Neue Geräterichtlinien für iOS<!-- 723774, 723815, 723826, 723830 -->
- **Apps auf dem Startbildschirm**: Steuert, welche Apps Benutzer auf dem [Startbildschirm ihres iOS-Geräts](../configuration/ios-device-features-settings.md#home-screen-layout) sehen. Diese Richtlinie wirkt sich auf das Layout des Startbildschirms aus, stellt aber keine Apps bereit.

- **Verbindungen mit AirPrint-Geräten**: Steuert, mit welchen [AirPrint-Geräten](../configuration/ios-device-features-settings.md#airprint) (Netzwerkdruckern) Endbenutzer eines iOS-Geräts eine Verbindung herstellen können.

- **Verbindungen zu AirPlay-Geräten**: Steuert, mit welchen [AirPlay-Geräten](../configuration/ios-device-features-settings.md) (z.B. Apple TV) Endbenutzer eines iOS-Geräts eine Verbindung herstellen können.

- **Benutzerdefinierte Sperrbildschirmnachricht**: Konfiguriert eine benutzerdefinierte Nachricht, die Benutzern auf dem Sperrbildschirm ihres iOS-Geräts angezeigt wird und die Standardnachricht des Sperrbildschirms ersetzt. Weitere Informationen finden Sie unter [Aktivieren des Modus für verlorene Geräte auf iOS-Geräten](../remote-actions/device-lost-mode.md).

### <a name="restrict-push-notifications-for-ios-apps---723767---"></a>Einschränken von Pushbenachrichtigungen für iOS-Apps<!-- 723767 -->
In einem Intune-Geräteeinschränkungsprofil können Sie jetzt die folgenden [Benachrichtigungseinstellungen](../configuration/ios-device-features-settings.md#app-notifications) für iOS-Geräte konfigurieren:

- Aktivieren oder deaktivieren Sie die Benachrichtigungen für eine bestimmte App vollständig.
- Aktivieren oder deaktivieren Sie die Benachrichtigung für eine bestimmte App in der Mitteilungszentrale.
- Geben Sie den Warnungstyp an, entweder **Keinen**, **Banner** oder **modale Warnung**.
- Geben Sie an, ob die Badges für diese App zulässig sind.
- Geben Sie an, ob die Benachrichtigungssounds zulässig sind.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously---737837---"></a>Konfigurieren von iOS-Apps für die autonome Ausführung im Einzelanwendungsmodus<!-- 737837 -->
Sie können jetzt ein Intune-Geräteprofil verwenden, um iOS-Geräte so zu konfigurieren, dass bestimmte Apps im [autonomen Einzelanwendungsmodus](../configuration/device-restrictions-ios.md#autonomous-single-app-mode) ausgeführt werden. Wenn dieser Modus konfiguriert ist und die App ausgeführt wird, wird das Gerät gesperrt, sodass es nur die App ausführen kann. Ein Beispiel hierfür ist, wenn Sie eine App konfigurieren, mit der Benutzer einen Test auf dem Gerät ausführen können. Wenn die Aktionen der App abgeschlossen sind oder Sie diese Richtlinie entfernen, kehrt das Gerät in seinen normalen Zustand zurück.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices---723765---"></a>Konfigurieren vertrauenswürdiger Domänen für das Durchsuchen von E-Mails und das Webbrowsen auf iOS-Geräten<!-- 723765 -->
Sie können in einem iOS-Geräteeinschränkungsprofil jetzt die folgenden [Domäneneinstellungen](../configuration/device-restrictions-ios.md#domains) konfigurieren:

- **Nicht gekennzeichnete E-Mail-Domänen**: Vom Benutzer gesendete oder empfangene E-Mails, die nicht den hier angegebenen Domänen entsprechen, werden als nicht vertrauenswürdig markiert.

- **Verwaltete Webdomänen**: Dokumente, die von den hier angegebenen URLs heruntergeladen werden, gelten als verwaltet (nur Safari).  

- **AutoAusfüllen-Domänen für Safari-Kennwörter**: Benutzer können Kennwörter in Safari nur aus URLs speichern, die mit den von Ihnen hier angegebenen Mustern übereinstimmen. Um diese Einstellung verwenden, muss sich das Gerät im überwachten Modus befinden und darf nicht für mehrere Benutzer konfiguriert sein. (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal---748782---"></a>Im iOS-Unternehmensportal verfügbare VPP-Apps<!-- 748782 -->
Sie können per Volumenlizenz erworbene iOS-Apps (VPP-Apps) Endbenutzern jetzt als **verfügbare** Installationen zuweisen. Endbenutzer benötigen ein Apple Store-Konto, um die App zu installieren.

### <a name="synchronize-ebooks-from-apple-vpp-store---800878---"></a>Synchronisieren von eBooks vom Apple-VPP-Store<!-- 800878 -->
Sie können jetzt [Bücher synchronisieren](../apps/vpp-apps-ios.md), die Sie im Apple-VPP-Store mit Intune erworben haben, und diese Bücher Benutzern zuweisen.

### <a name="multi-user-management-for-samsung-knox-standard-devices---971988---"></a>Mehrbenutzerverwaltung für Samsung KNOX Standard-Geräte<!-- 971988 -->
Geräte, auf denen Samsung KNOX Standard ausgeführt wird, werden jetzt für die [Mehrbenutzerverwaltung](../enrollment/android-enroll.md) von Intune unterstützt. Das bedeutet, dass sich Endbenutzer auf dem Gerät mit ihren Azure Active Directory-Anmeldeinformationen an- und wieder abmelden können, und dass das Gerät zentral verwaltet wird, egal ob es sich in Gebrauch befindet oder nicht.  Wenn sich Endbenutzer anmelden, verfügen Sie über Zugriff auf Apps und erhalten alle Richtlinien, die ihnen zugewiesen sind. Wenn sich Benutzer abmelden, werden alle App-Daten gelöscht.

### <a name="additional-windows-device-restriction-settings---818566---"></a>Zusätzliche Einschränkungseinstellungen für Windows-Geräte<!-- 818566 -->
Wir haben Unterstützung für zusätzliche [Einschränkungseinstellungen für Windows-Geräte](../configuration/device-restrictions-windows-10.md) hinzugefügt, z.B. zusätzliche Unterstützung für den Browser Microsoft Edge, Anpassung des Gerätesperrbildschirms, Anpassungen des Startmenüs, festgelegtes Hintergrundbild der Windows Spotlight-Suche und Proxyeinstellungen.

### <a name="multi-user-support-for-windows-10-creators-update---822547---"></a>Unterstützung für Windows 10 Creators Update für mehrere Benutzer<!-- 822547 -->
Wir haben Unterstützung für die [Mehrbenutzerverwaltung](../enrollment/windows-enroll.md) für Geräte hinzugefügt, die das Windows 10 Creators Update ausführen und in die Azure Active Directory-Domäne eingebunden sind. Das bedeutet Folgendes: Wenn sich unterschiedliche Standardbenutzer mit ihren Azure AD-Anmeldeinformationen auf dem Gerät anmelden, erhalten sie alle Apps und Richtlinien, die ihrem jeweiligen Benutzernamen zugewiesen sind. Benutzer können das Unternehmensportal derzeit nicht für Self-Service-Szenarien beispielsweise zum Installieren von Apps verwenden.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Neustart für Windows 10-PCs<!-- 1004830 -->
Eine neue [Fresh Start-Geräteaktion](../remote-actions/device-fresh-start.md) für Windows 10-PCs ist jetzt verfügbar.  Wenn Sie diese Aktion ausführen, werden alle installierten Apps auf dem PC entfernt, und der PC wird automatisch auf die neueste Windows-Version aktualisiert. Damit können vorinstallierte OEM-Apps entfernt werden, die oft mit einem neuen PC geliefert werden. Sie können konfigurieren, ob Benutzerdaten beibehalten werden, wenn diese Geräteaktion ausgegeben wird.

### <a name="additional-windows-10-upgrade-paths---903672---"></a>Zusätzliche Windows 10-Upgradepfade<!-- 903672 -->
Sie können jetzt eine [Richtlinie für Editionsupgrades](../configuration/edition-upgrade-configure-windows-10.md) erstellen, um Geräte auf die folgenden zusätzlichen Windows 10-Editionen zu aktualisieren:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices---747607---"></a>Massenregistrierung von Windows 10-Geräten<!-- 747607 -->
Sie können jetzt eine große Anzahl von Geräten, auf denen das Windows 10 Creators Update ausgeführt wird, mit Windows Configuration Designer (WCD) in Azure Active Directory und Intune einbinden. Um die [MDM-Massenregistrierung](../enrollment/windows-bulk-enroll.md) für Ihren Azure AD-Mandanten zu aktivieren, erstellen Sie ein Bereitstellungspaket, das Geräte mithilfe von Windows Configuration Designer in Ihren Azure AD-Mandanten einbindet. Sie können das Paket auf alle unternehmenseigenen Geräte anwenden, die Sie per Massenvorgang registrieren und verwalten möchten. Nachdem das Paket auf Ihre Geräte angewendet wurde, werden die Geräte in Azure AD eingebunden sowie bei Intune registriert und sind dann bereit für die Anmeldung durch Ihre Azure AD-Benutzer.  Azure AD-Benutzer sind auf diesen Geräten Standardbenutzer und erhalten zugewiesene Richtlinien sowie erforderliche Apps. Die Verwendung von Self-Service-Funktionen und Unternehmensportalen wird derzeit nicht unterstützt.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations---581122-736644---"></a>Neue MAM-Einstellungen für die PIN und verwaltete Speicherorte<!-- 581122, 736644 -->
Es sind zwei neue App-Einstellungen verfügbar, die Sie in MAM-Szenarien (Mobile Application Management, Verwaltung mobiler Anwendungen) unterstützen:

- **App-PIN deaktivieren, wenn die Geräte-PIN verwaltet wird**: Erkennt, ob eine Geräte-PIN auf dem registrierten Gerät vorhanden ist. Falls ja, wird die App-PIN umgangen, was durch die App-Schutzrichtlinien ausgelöst wird. Diese Einstellung ermöglicht eine Verminderung der Häufigkeit, wann immer Benutzern eine Aufforderung zur PIN-Eingabe angezeigt wird, wenn sie eine MAM-fähige Anwendung auf einem registrierten Gerät öffnen. Diese Funktion ist für Android und iOS verfügbar.

- **Wählen, welche Speicherdienste Unternehmensdaten speichern können**: Damit können Sie angeben, an welchen Speicherorten Unternehmensdaten gespeichert werden sollen. Benutzer können in ausgewählten Speicherortdiensten speichern, das heißt, dass alle anderen Speicherortdienste, die nicht aufgelistet sind, blockiert werden.

  Liste der unterstützten Speicherortdienste:

  - OneDrive
  - Business SharePoint Online
  - Lokaler Speicher

### <a name="help-desk-troubleshooting-portal---907448---"></a>Helpdeskportal zur Problembehandlung<!-- 907448 -->
Im neuen [Portal zur Problembehandlung](../help-desk-operators.md) können Helpdeskmitarbeiter und Intune-Administratoren Benutzer und Geräte anzeigen und Aufgaben ausführen, um technische Intune-Probleme zu lösen.

<!-- ########################## -->
## <a name="march-2017"></a>März 2017

### <a name="support-for-ios-lost-mode--431695--"></a>Unterstützung des iOS-Modus für verlorene Geräte<!--431695-->
Für Geräte unter iOS 9.3 (oder höher) wurde von Intune die Unterstützung des **Modus für verlorene Geräte** hinzugefügt. Nun können Sie ein Gerät sperren, um zu dessen Verwendung vollständig zu unterbinden, und auf dem Sperrbildschirm des Geräts eine Meldung und eine Kontakttelefonnummer anzeigen.

Der Endbenutzer kann das Gerät erst wieder entsperren, wenn ein Administrator den Modus für verlorene Geräte deaktiviert. Bei aktivierten Modus für verlorene Geräte können Sie mithilfe der Aktion **Gerät suchen** den geografischen Standort des Geräts auf einer Karte in der Intune-Konsole anzeigen.

Bei dem Gerät muss es sich um ein firmeneigenes, über DEP registriertes iOS-Gerät im überwachten Modus handeln.

Weitere Informationen finden Sie unter [Was ist die Microsoft Intune-Geräteverwaltung?](../remote-actions/device-management.md).

### <a name="improvements-to-device-actions-report--677150--"></a>Verbesserungen des Geräteaktionenberichts<!--677150-->
Wir haben die Leistung des Geräteaktionenberichts verbessert. Darüber hinaus können Sie jetzt den Bericht nach Status filtern. Beispielsweise könnten Sie den Bericht so filtern, dass nur Geräteaktionen angezeigt werden, die abgeschlossen wurden.

### <a name="custom-app-categories--748805--"></a>Benutzerdefinierte App-Kategorien<!--748805-->
Sie können jetzt Kategorien für in Intune hinzugefügte Apps erstellen, bearbeiten und zuweisen. Zurzeit können Kategorien nur auf Englisch angegeben werden.
Weitere Informationen finden Sie unter [How to add an app to Intune (Hinzufügen einer App zu Intune)](../apps/apps-add.md).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices--748823--"></a>Zuweisen branchenspezifischer Apps für Benutzer nicht registrierter Geräte<!--748823-->
Sie können Benutzern jetzt Branchen-Apps aus dem Store zuweisen, unabhängig davon, ob die Benutzergeräte bei Intune registriert sind oder nicht. Wenn das Gerät eines Benutzers nicht bei Intune registriert ist, muss der Benutzer die App über die Unternehmensportal-Website statt über die Unternehmensportal-App installieren.

### <a name="new-compliance-reports--846671--"></a>Neue Kompatibilitätsberichte<!--846671-->
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

### <a name="direct-access-to-apple-enrollment-scenarios--951869--"></a>Direkter Zugriff auf Apple-Registrierungsszenarios<!--951869-->
Für Intune-Konten, die nach Januar 2017 erstellt wurden, hat Intune direkten Zugriff auf Apple-Registrierungsszenarien mithilfe der Workload „Geräte registrieren“ im Azure-Portal aktiviert. Bisher konnte nur über Links im Azure-Portal auf die Apple-Registrierungsvorschau zugegriffen werden. Vor Januar 2017 erstellte Intune-Konten erfordern eine einmalige Migration, bevor diese Features in Azure verfügbar sind. Der Zeitplan für die Migration wurde noch nicht angekündigt, aber Sie erfahren so bald wie möglich Näheres. Wir empfehlen Ihnen dringend, ein Testkonto zu erstellen, um die neue Oberfläche zu testen, wenn Sie mit Ihrem vorhandenen Konto nicht auf die Vorschau zugreifen können.


<!-- ########################## -->
## <a name="february-2017"></a>Februar 2017

### <a name="ability-to-restrict-mobile-device-enrollment--747600-795782--"></a>Einschränken der Registrierung von Mobilgeräten<!--747600, 795782-->
Es wurden neue Registrierungseinschränkungen zu Intune hinzugefügt, mit denen sich kontrollieren lässt, welche Mobilgeräteplattformen für die Registrierung zugelassen werden. Intune unterscheidet dabei zwischen den Mobilgeräteplattformen iOS, macOS, Android, Windows und Windows Mobile.

- Durch das Einschränken der Registrierung von Mobilgeräten wird die Registrierung von PC-Clients nicht eingeschränkt.  
- Für iOS und Android gibt es eine zusätzliche Option, mit der die Registrierung persönlicher Geräte blockiert werden kann.

Intune kennzeichnet alle neuen Geräte als persönlich, es sei denn, der IT-Administrator kennzeichnet sie als unternehmenseigen – wie in [diesem Artikel](../enrollment/device-enrollment.md) beschrieben.

### <a name="view-all-actions-on-managed-devices--677150--"></a>Anzeigen aller Aktionen auf verwalteten Geräten<!--677150-->
Ein neuer Bericht über __Geräteaktionen__ zeigt, wer Remoteaktionen wie das Zurücksetzen auf Werkseinstellungen auf Geräten ausgeführt hat sowie den Status dieser Aktion. Weitere Informationen finden Sie unter [Was ist die Geräteverwaltung?](../remote-actions/device-management.md)

### <a name="non-managed-devices-can-access-assigned-apps--664691--"></a>Nicht verwaltete Geräte können auf zugewiesene Apps zugreifen<!--664691-->
Als Teil der Designänderungen auf der Unternehmensportal-Website können iOS- und Android-Benutzer Apps installieren, die ihnen als „Verfügbar ohne Registrierung“ auf Ihren nicht verwalteten Geräten zugewiesen sind. Benutzer können sich mit ihren Intune-Anmeldeinformationen auf der Unternehmensportal-Website anmelden und die Liste der ihnen zugewiesenen Apps anzeigen. Die App-Pakete der Apps des Typs „Verfügbar ohne Registrierung“ werden zum Download über die Unternehmensportal-Website verfügbar gemacht. Apps, für die die Registrierung für die Installation erforderlich ist, sind durch diese Änderung nicht betroffen, da Benutzer aufgefordert werden, ihr Gerät zu registrieren, wenn sie diese Apps installieren möchten.

### <a name="custom-app-categories--748805--"></a>Benutzerdefinierte App-Kategorien<!--748805-->
Sie können jetzt Kategorien für in Intune hinzugefügte Apps erstellen, bearbeiten und zuweisen. Zurzeit können Kategorien nur auf Englisch angegeben werden.
Weitere Informationen finden Sie unter [How to add an app to Intune (Hinzufügen einer App zu Intune)](../apps/apps-add.md).

### <a name="display-device-categories--814654--"></a>Anzeigen von Gerätekategorien<!--814654-->
Sie können nun die Gerätekategorie als Spalte in der Geräteliste anzeigen. Sie können die Kategorie auch im Abschnitt „Eigenschaften“ des Blatts „Geräteeigenschaften“ bearbeiten. Weitere Informationen finden Sie unter [How to add an app to Intune (Hinzufügen einer App zu Intune)](../apps/apps-add.md).

### <a name="configure-windows-update-for-business-settings--776716--"></a>Konfigurieren von Einstellungen für Windows Update for Business<!--776716-->

Windows als Dienst ist die neue Methode zur Bereitstellung von Updates für Windows 10. Ab Windows 10 enthalten neue Funktions- und Qualitätsupdates die Inhalte aller früheren Updates. Das bedeutet, dass Ihre Windows 10-Geräte nach der Installation des neuesten Updates vollständig auf dem neuesten Stand sind. Im Gegensatz zu früheren Versionen von Windows müssen Sie nun anstelle eines Teilupdates das gesamte Update installieren.

Mithilfe von Windows Update for Business können Sie die Updateverwaltung vereinfachen, sodass Sie für Gruppen von Geräten keine einzelnen Updates genehmigen müssen. Sie können weiterhin eine Updaterolloutstrategie konfigurieren, um das Risiko in Ihren Umgebungen zu managen und sicherzustellen, dass Updates zur richtigen Zeit installiert werden. Mit Microsoft Intune können Sie Updateeinstellungen auf Geräten konfigurieren und die Updateinstallation zurückstellen. Intune speichert nur die Updaterichtlinienzuweisung, nicht die Updates. Geräte greifen direkt auf Windows Update zu, um die Updates zu beziehen. Intune dient zum Konfigurieren und Verwalten der **Windows 10-Updateringe**. Ein Updatering enthält eine Reihe von Einstellungen, die festlegen, wann und wie Updates für Windows 10 installiert werden. Ausführlichere Informationen finden Sie unter [Konfigurieren von Einstellungen für Windows Update for Business](../protect/windows-update-for-business-configure.md).
