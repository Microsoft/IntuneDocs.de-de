---
title: 'In der Entwicklung: Microsoft Intune'
titleSuffix: ''
description: In der Entwicklung befindliche Microsoft Intune-Features
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 009b9cf22bcdd73eb563c772cc9995047f05a9c1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735765"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>In der Entwicklung befindliche Microsoft Intune-Features: Oktober 2019

Um Ihnen bei Ihrer Vorbereitung und Planung zu helfen, sind auf dieser Seite Updates und Features der Intune-Benutzeroberfläche aufgeführt, die sich in der Entwicklung befinden, aber noch nicht freigegeben wurden. Zusätzlich:

- Wenn wir davon ausgehen, dass Sie vor einer Änderung Maßnahmen ergreifen müssen, werden wir einen ergänzenden Beitrag im Office-Nachrichtencenter veröffentlichen.
- Wenn ein Feature in die Produktion überführt wird, entweder als Vorschau- oder allgemein verfügbare Version, wird die Featurebeschreibung von dieser Seite auf die Seite [Neuerungen in Microsoft Intune](whats-new.md) verschoben.
- Diese Seite und die Seite [Neuerungen](whats-new.md) werden regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.
- In der [Roadmap für Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) finden Sie strategische Ziele und Zeitrahmen.

> [!Note]
> Diese Punkte spiegeln die aktuellen Erwartungen von Microsoft an die Möglichkeiten mit Intune in einer künftigen Version wider. Termine und einzelne Features können sich ändern. Nicht für alle Elemente in der Entwicklung gibt es auf dieser Seite eine Featurebeschreibung.

**RSS-Feed**: Lassen Sie sich benachrichtigen, wenn diese Seite aktualisiert wird, indem Sie die folgende URL kopieren und in Ihren Feedreader einfügen: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>App-Verwaltung

### <a name="additional-app-configuration-variable-available----4969237----"></a>Zusätzliche APP-Konfigurationsvariable verfügbar <!-- 4969237  -->
Wenn Sie eine APP-Konfigurationsrichtlinie erstellen, können Sie die `AAD Device ID`-Konfigurationsvariable als Teil ihrer Konfigurationseinstellungen einschließen. Klicken Sie in Intune auf **Client-Apps** > **App-Konfigurationsrichtlinien** > **Hinzufügen**. Geben Sie die Konfigurationsrichtlinien Details ein, und wählen Sie **Konfigurationseinstellungen** aus, um das Blatt **Konfigurationseinstellungen** anzuzeigen.

### <a name="dark-mode-for-ios-company-portal----4911422----"></a>Dunkler Modus für IOS-Unternehmensportal <!-- 4911422  -->
Der dunkle Modus ist für die IOS-Unternehmensportal geplant. Laden Sie Unternehmens-apps herunter, verwalten Sie Ihre Geräte, und erhalten Sie Unterstützung im Farbschema Ihrer Wahl. Weitere Informationen zum iOS-Unternehmensportal finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](../apps/company-portal-app.md).

### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-devices----4760025----"></a>Verhindern der Installation von Apps aus unbekannten Quellen auf Android-Unternehmens Geräten <!-- 4760025  -->
Bei einem Android-Gerät für den Unternehmens Arbeitsprofil ist es für Endbenutzer nie möglich, Apps aus unbekannten Quellen in das Arbeitsprofil zu installieren. Sie können diese Einschränkung optional auch auf das persönliche Profil ausweiten. Wenn Sie diese Einschränkung aktivieren, werden Endbenutzer auf Android Enterprise-Arbeitsprofil Geräten auch daran gehindert, Apps aus unbekannten Quellen auf die persönliche Seite Ihres Geräts zu laden. 

### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029----"></a>Aktualisieren der Benutzeroberfläche des App-Schutzes und der IOS-App-Bereitstellung <!-- 4102027, 4102029  -->
Die Benutzeroberfläche zum Erstellen und Bearbeiten von App-Schutzrichtlinien und IOS-App-Bereitstellungs Profilen in InTune wird aktualisiert. Die Änderungen der Benutzeroberfläche umfassen:
- Ein vereinfachtes Verhalten durch die Verwendung eines Assistenten Formats, das auf einem Blatt komprimiert ist. 
- Ein Update von CREATE Flow, das Zuweisungen einschließt.
- Eine zusammengefasste Seite aller Dinge, die beim Anzeigen von Eigenschaften festgelegt werden, bevor eine neue Richtlinie erstellt oder eine Eigenschaft bearbeitet wird. Außerdem wird beim Bearbeiten von Eigenschaften in der Zusammenfassung nur eine Liste der Elemente aus der Kategorie der bearbeiteten Eigenschaften angezeigt.

### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>Erstellen Sie Gruppen von Verwaltungs Objekten Namensrichtlinien Sätze. <!-- 3762880  -->
Mit Richtlinien Sätzen können Sie ein Bündel von Verweisen auf bereits vorhandene Verwaltungs Entitäten erstellen, die als einzelne konzeptionelle Einheit identifiziert, gezielt und überwacht werden müssen. Durch Richtlinien Sätze werden vorhandene Konzepte oder Objekte nicht ersetzt. Ein Administrator kann weiterhin einzelne Objekte wie heute zuweisen. Auf einzelne Objekte wird durch einen Richtlinien Satz verwiesen. Aus diesem Grund werden alle Änderungen an den einzelnen Objekten in der Richtlinie festgelegt.  In InTune wählen Sie **Richtlinien Sätze** > **Erstellen** aus, um einen neuen Richtlinien Satz zu erstellen. 

### <a name="win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Win32-apps auf Geräten mit Windows 10 S-Modus <!-- 3747604  --> 
Sie sind in der Lage, Win32-apps auf Geräten mit Windows 10 S-Modus zu installieren und auszuführen. Mithilfe der Windows Defender Application Control (WDac) PowerShell-Tools können Sie eine oder mehrere ergänzende Richtlinien für den S-Modus erstellen. Signieren Sie die ergänzenden Richtlinien mit dem Device Guard-Signatur Portal, und laden Sie dann die Richtlinien über InTune hoch. In InTune finden Sie diese Funktion durch Auswählen von **Client-apps** > **ergänzende Richtlinien für Windows 10 S**. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Festlegen der APP-Verfügbarkeit basierend auf einem Datum und einer Uhrzeit <!-- 3510685  -->
Als Administrator können Sie die Startzeit und den Stichtag für eine erforderliche App konfigurieren. Zum Startzeitpunkt startet die Intune-Verwaltungs Erweiterung den Download der App-Inhalte und speichert Sie zwischen. Die APP wird zum Stichtag installiert. Für verfügbare apps wird durch die Startzeit vorgegeben, wann die app in Unternehmensportal sichtbar ist. Klicken Sie in Intune auf **Client-Apps** > **Apps**. Wählen Sie dann eine bestimmte App aus der Liste aus, oder wählen Sie **Hinzufügen** aus, um eine neue APP hinzuzufügen. Wählen Sie auf dem App-Blatt **Zuweisungen** > **Gruppe hinzufügen**aus. Legen Sie den **Zuweisungstyp** auf **erforderlich** und dann auf **enthaltene Gruppen**fest. Legen Sie **diese APP für alle Benutzer erforderlich** auf **Ja** fest, und wählen Sie **Bearbeiten** aus, um die Optionen für die **Endbenutzer** Optionen zu ändern. Legen Sie auf dem Blatt **Endbenutzer** Darstellung die **verfügbare Software Zeit** nach Bedarf fest. Weitere Informationen zum Hinzufügen von Apps finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Neustarten von Win32-apps erforderlich <!-- 3136567  -->
Sie können verlangen, dass eine Win32-App nach einer erfolgreichen Installation neu gestartet werden muss. Außerdem können Sie die Zeitspanne (die Toleranz Periode) auswählen, bevor der Neustart erfolgen muss.

### <a name="company-portal-app-on-windows----1808082----"></a>Unternehmensportal-app unter Windows <!-- 1808082  -->
Die Unternehmensportal-App auf Windows-Geräten wird aktualisiert, um den Benutzern Popup Benachrichtigungen anzuzeigen, auch wenn die Anwendung geschlossen wird. Das Update zeigt nur Benachrichtigungen für verfügbare apps an, wenn der Installationsstatus "abgeschlossen" oder "Fehler" lautet. Die Unternehmensportal-APP zeigt keine Benachrichtigungen für erforderliche Anwendungen an.

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Unternehmensportal App-Installationsstatus Meldungen <!-- 2514416  -->
Die Unternehmensportal-APP zeigt den Endbenutzern zusätzliche APP-Installationsstatus Meldungen an. Die folgenden Bedingungen gelten für neue Win32-Abhängigkeits Features:
- Die App konnte nicht installiert werden. Vom Administrator definierte Abhängigkeiten wurden nicht erfüllt.
- Die APP wurde erfolgreich installiert, erfordert aber einen Neustart.
- Die APP wird gerade installiert. es ist jedoch ein Neustart erforderlich, um den Vorgang fortzusetzen.

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>Zuweisen von Microsoft Edge Beta für macOS <!-- 4678761  -->
Sie können die neueste Version von Microsoft Edge Beta in InTune für macOS-Geräte hinzufügen und zuweisen. Wählen Sie in InTune die Option **Client-apps** > **apps**aus,  >  APP  > **Microsoft Edge-macOS** **Hinzufügen**. Weisen Sie dann Microsoft Edge Beta den vorgesehenen Gruppen zu. Microsoft Auto Update (Mau) hält Microsoft Edge auf dem neuesten Stand. Weitere Informationen zu Microsoft Edge finden Sie unter [Verwalten des Webzugriffs mithilfe von Microsoft Edge mit Microsoft InTune](../apps/manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurieren von App-Benachrichtigungs Inhalten für Organisations Konten <!-- 2576686 -->
Mit InTune-App-Schutzrichtlinien (app) auf Android-und IOS-Geräten können Sie App-Benachrichtigungs Inhalte für Organisations Konten steuern. Diese Funktion erfordert Unterstützung von Anwendungen und ist möglicherweise nicht für alle App-fähigen Anwendungen verfügbar. Weitere Informationen zu Intune-App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](../apps/app-protection-policy.md)

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Berichterstellung für verfügbare Google Play-Apps für Android-Arbeitsprofile <!-- 3041956  -->
Mit diesem Feature können Sie den App-Installationsstatus und die installierte Version verwalteter Google Play-Apps für verfügbare App-Installationen auf Android Arbeitsprofilgeräten anzeigen. Weitere Informationen finden Sie unter [Überwachen von App-Schutzrichtlinien](../apps/app-protection-policies-monitor.md), [Verwalten von Android-Arbeitsprofilgeräten mit Intune](../enrollment/android-enterprise-overview.md) und [App-Typ „Verwaltetes Google Play“](../apps/apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Gerätekonfiguration


### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328----"></a>Neue Geräte Konfigurationseinstellungen für überwachte IOS-und ipados-Geräte <!-- 5199328  -->
Auf IOS-und ipados-Geräten können Sie ein Profil zum Einschränken von Features und Einstellungen auf Geräten erstellen (**Device Configuration** > **profiles** > **Create profile** > **IOS/ipados** for Platform > **Device Einschränkungen** für den Profiltyp). Es gibt neue Einstellungen, die Sie steuern können: 
- Zugriff auf das Netzwerklaufwerk in der Datei-app  
- Zugriff auf USB-Laufwerk in der Datei-app 
- Wi-Fi immer eingeschaltet 

Die aktuellen Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](../configuration/device-restrictions-ios.md).

Gilt für:
- iOS 13.0 und neuer
- ipados 13,0 und höher

### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-and-android-enterprise----5021055----"></a>Die Einstellung "automatisch verbinden" wird in WLAN-Profilen unter Android und Android Enterprise entfernt. <!-- 5021055  -->
Auf Android-und Android-Unternehmens Geräten können Sie ein WLAN-Profil erstellen, um andere Einstellungen zu konfigurieren (**Gerätekonfiguration** > **profile** > **Create profile** > **Android** oder **Android Enterprise** für Platform > **Wi-Fi** für Profiltyp). Die Einstellung **automatisch verbinden** wird entfernt, da Sie [von Android nicht unterstützt](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29)wird. 

Wenn Sie diese Einstellung in einem WLAN-Profil verwenden, stellen Sie möglicherweise fest, dass **Connect automatisch** nicht funktioniert. Sie müssen keine Maßnahmen ergreifen, aber beachten Sie, dass diese Einstellung in der InTune-Benutzeroberfläche entfernt wird.

Um die aktuellen Einstellungen anzuzeigen, wechseln Sie zu [Android Wi-Fi Settings](../configuration/wi-fi-settings-android.md) oder [Android Enterprise Wi-Fi Settings](../configuration/wi-fi-settings-android-enterprise.md).

Gilt für:
- Android
- Android Enterprise

### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices----4816339----"></a>Erstellen eines globalen HTTP-Proxys auf Android-Geräten für Unternehmens Gerätebesitzer <!-- 4816339  -->
Auf Android-Unternehmens Geräten können Sie ein VPN-Profil mit unterschiedlichen VPN-Clients erstellen (**Device Configuration** > **profiles** > **Create profile** > **Android Enterprise** for Platform > **Gerätebesitzer > Geräte Einschränkungen** für den Profiltyp > **Konnektivität**). Sie können einen globalen http-Proxy so konfigurieren, dass er den webbrowserstandards Ihrer Organisation entspricht. Alle apps, die zu HTTP-Websites wechseln, verwenden diesen Proxy.

Gilt für:
- Android Enterprise-Gerätebesitzer

### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices----2266073----"></a>Neues Geräte-Firmware-Konfigurations Schnittstellen Profil für Geräte mit Windows 10 und höher <!-- 2266073  -->
Unter Windows 10 und höher können Sie ein Geräte Konfigurations Profil erstellen, um Einstellungen und Features zu steuern (**Gerätekonfiguration** > **profile** > **Profil erstellen** > **Windows 10 und** höher für die Plattform). Es gibt einen neuen Gerätetyp für die Konfiguration der Gerätefirmware, mit dem InTune UEFI-Einstellungen (BIOS) verwalten kann.

Eine Übersicht über alle Einstellungen, die Sie konfigurieren können, finden Sie unter [Anwenden von Features und Einstellungen auf Ihren Geräten mithilfe von Geräte Profilen in Microsoft InTune](../configuration/device-profiles.md).

Gilt für:
- Windows 10 RS5 (1809) und neuer auf einigen OEMs

### <a name="pkcs-certificates-for-macos-----1333650------------------"></a>PKCS-Zertifikate für macOS  <!-- 1333650                -->
Wir werden auf Geräten mit macOS vollständige Unterstützung für PKCS-Zertifikate hinzufügen. Benutzer können Benutzer-und Gerätezertifikate mit den Feldern Anpassungs Betreff und alternativer Antragsteller Name bereitstellen. Außerdem wird die neue Einstellung allen apps Zugriff erlauben zugewiesen. durch Aktivieren von wird allen zugeordneten apps der Zugriff auf den privaten Schlüssel gewährt. Weitere Informationen zu dieser Einstellung finden Sie in der folgenden Apple-Dokumentation: https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

###   <a name="derived-credentials-to-provision-mobile-devices-with-certificates----------1736036-1736037-1772050--------"></a>Abgeleitete Anmelde Informationen für die Bereitstellung mobiler Geräte mit Zertifikaten      <!--  1736036, 1736037, 1772050      --> 
Wir werden Unterstützung für abgeleitete Anmelde Informationen hinzufügen, die das *National Institute of Standards and Technology (NIST) 800-157-* Standard für die Bereitstellung von Zertifikaten für Geräte unterstützen.  Abgeleitete Anmelde Informationen basieren auf der Verwendung einer persönlichen Identitätsüberprüfung (PIV) oder der CAC-Karte (Common Access Card), wie z. b. eine Smartcard. Benutzer authentifizieren sich mit Ihrer Smartcard auf einem Computer und senden dann nach dem vom abgeleiteten Anmelde Informationsanbieter benötigten Prozess eine Anforderung für ein Zertifikat für das verwaltete Gerät.   

Der Vorgang zur Verwendung abgeleiteter Anmelde Informationen zum erhalten eines Zertifikats unterscheidet sich von der Verwendung von SCEP-oder PKCS-Zertifikat Profilen, aber das Endergebnis ist das gleiche – Mobile Geräte mit Zertifikaten für die Authentifizierung, die für die APP-Authentifizierung, VPN, WLAN oder e-Mail verwendet werden können. liert.   

Weitere Informationen finden Sie unter [abgeleitete PIV-Anmelde](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) Informationen unter www.nccoe.nist.gov.

Die erste Veröffentlichung abgeleiteter Anmelde Informationen unterstützt Entrust Datacard, Intercede und DISA purebred auf IOS. Zusätzliche Plattformen und abgeleitete Anmelde Informationsanbieter werden in späteren Versionen unterstützt.   

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Geräteregistrierung

### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment----4350697---"></a>Hiermit geben Sie an, welche Android-Geräte Betriebssystemversionen mit Arbeitsprofil-oder Geräte Administrator Registrierung registriert werden. <!-- 4350697 -->
Mithilfe der InTune-Gerätetyp Einschränkungen können Sie die Betriebssystemversion des Geräts verwenden, um anzugeben, welche Benutzer Geräte die Registrierung von Android Enterprise-Arbeits Profilen oder die Registrierung von Android-Geräte Administratoren verwenden werden. Wechseln Sie zu diesem Zweck zu **InTune** > **Geräte**Registrierung  >  Registrierungs**Einschränkungen** >  Create-**Einschränkung** > **Gerätetyp Einschränkung** > **Platt Form Einstellungen**.

### <a name="edit-device-name-value-for-autopilot-devices----4816775---"></a>Bearbeiten des Geräte namens Werts für Autopilot-Geräte <!-- 4816775 -->
Sie können den Wert für den Gerätenamen für Azure AD verbundenen Autopilot-Geräten bearbeiten. Wechseln Sie zu diesem Zweck zu **InTune** > **Geräte**Registrierung  > **Windows**-Registrierung  > **Windows Autopilot** > **Geräte** > Wählen Sie das Gerät aus, um den Wert des Geräte namens im rechten Bereich zu **ändern >** .

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Für iOS-Geräte: Anpassen des Datenschutzbildschirms für den Registrierungsvorgang im Unternehmensportal <!-- 4394993  -->
Mithilfe von Markdown können Sie den Datenschutzbildschirm im Unternehmensportal anpassen, der den Endbenutzern während der iOS-Registrierung angezeigt wird. Insbesondere können Sie die Liste der Elemente und Vorgänge anpassen, die Ihre Organisation auf dem Gerät nicht anzeigen bzw. ausführen kann.

<!-- ***********************************************-->
## <a name="device-management"></a>Geräteverwaltung


### <a name="edit-group-tag-value-for-autopilot-devices---4816775---"></a>Gruppentagwert für Autopilot-Geräte bearbeiten<!-- 4816775 -->
Sie können den gruppentagwert für Autopilot-Geräte bearbeiten. Wechseln Sie zu diesem Zweck zu **InTune** > **Geräte**Registrierung  > **Windows**-Registrierung  > **Windows Autopilot** > **Geräte** > Wählen Sie das Gerät aus, um den gruppentagwert im rechten Bereich zu **ändern >** .

### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089------------"></a>Aktualisierung der Benutzeroberfläche zum Erstellen und Bearbeiten von Windows 10-Update Ringen  <!-- 4099089          -->   
Wir werden eine aktualisierte Benutzeroberfläche zum Erstellen und Bearbeiten der Benutzeroberfläche für Windows 10-Update Ringe für InTune erstellen.  Änderungen an der Benutzeroberfläche umfassen Folgendes:  
- Vereinfachen Sie die vorhandene Darstellung, indem Sie ein im Assistenten formatierte Format verwenden, das auf einem Blatt komprimiert ist. Diese Aktualisierung der Benutzeroberfläche ist nicht mit der Blatt aufgliedern, bei der IT-Experten einen Drilldown in Deep Blade Journeys ausführen müssen.   
- Überarbeiten Sie den Erstellungs Fluss, um Zuweisungen einzuschließen  
- Das Hinzufügen einer zusammengefassten Seite aller Dinge, die beim Anzeigen von Eigenschaften festgelegt werden, vor dem Erstellen eines neuen Update Rings und beim Bearbeiten einer Eigenschaft. Beim Bearbeiten zeigt die Zusammenfassung nur die Liste der Elemente an, die in der einen Kategorie der zu bearbeitenden Eigenschaften festgelegt sind.

### <a name="ui-update-for-creating-and-editing-ios-software-updates-----4099090----------"></a>UI-Update zum Erstellen und Bearbeiten von IOS-Software Updates  <!-- 4099090        -->   
Wir führen eine aktualisierte Benutzeroberfläche für die Erstellung und Bearbeitung von IOS-Software Updates in InTune ein. Änderungen an der Benutzeroberfläche umfassen Folgendes:
- Vereinfachen Sie die vorhandene Darstellung, indem Sie ein im Assistenten formatierte Format verwenden, das auf einem Blatt komprimiert ist. Diese Aktualisierung der Benutzeroberfläche ist nicht mit der Blatt aufgliedern, bei der IT-Experten einen Drilldown in Deep Blade Journeys ausführen müssen.  
- Die Richtlinie zum Erstellen von IOS-Software Updates wird aktualisiert, um Zuweisungen einzuschließen. 
- Die Richtlinie für IOS-Software Updates enthält eine zusammengefasste Seite aller Elemente, die beim Anzeigen von Eigenschaften festgelegt werden, bevor eine neue Richtlinie erstellt und eine Eigenschaft bearbeitet wird. Beim Bearbeiten zeigt die Zusammenfassung nur die Liste der Elemente an, die in der einen Kategorie der zu bearbeitenden Eigenschaften festgelegt sind.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>MacOS-Benutzergruppen als Ziel für die JAMF-Verwaltung <!-- 4061739 -->
Sie sind in der Lage, bestimmte Benutzergruppen als Ziel festzulegen, damit Ihre macOS-Geräte von JAMF verwaltet werden. Mit dieser Zielgruppe können Sie die JAMF-Kompatibilitäts Integration auf eine Teilmenge von macOS-Geräten anwenden, während andere Geräte weiterhin von InTune verwaltet werden. Außerdem können Sie die Geräte der Benutzer schrittweise von einer MDM zum anderen migrieren.

### <a name="new-restrictions-for-renaming-windows-devices----3478938---"></a>Neue Einschränkungen beim Umbenennen von Windows-Geräten <!-- 3478938 -->
Gerätenamen müssen die folgenden Regeln einhalten:
- maximal 15 Zeichen (muss kleiner oder gleich 63 Bytes sein, ohne nachfolgende NULL)
- Nicht NULL und keine leere Zeichenfolge
- Zulässige ASCII: Buchstaben (a-z, a-z), Zahlen (0-9) und Bindestriche
- Zulässige Unicode: Zeichen > = 0x80, muss gültig sein, UTF8, muss "IDN-mappable" lauten (rtlidntonameprepunicode ist erfolgreich; siehe RFC 3492).
- Namen dürfen nicht nur Zahlen enthalten oder mit einer Zahl beginnen.
- Keine Leerzeichen im Namen
- Unzulässige Zeichen: {|} ~ [\] ^ ':; < = >? & @! " # $ % ` ( ) + / , . _ *)

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Bereitstellen von Software Updates für macOS-Geräte <!-- 3194876 -->
Sie können Software Updates für Gruppen von macOS-Geräten bereitstellen. Diese Funktion umfasst kritische, Firmware-und Konfigurationsdateien sowie andere Updates. Sie können beim nächsten Einchecken von Geräten Updates senden oder einen wöchentlichen Zeitplan auswählen, um Updates in oder außerhalb der von Ihnen festgelegten Zeitfenster bereitzustellen. Diese Funktion ist hilfreich, wenn Sie Geräte außerhalb der Standard Arbeitszeiten aktualisieren möchten oder wenn Ihr Helpdesk vollständig besetzt ist. Außerdem erhalten Sie einen ausführlichen Bericht zu allen macOS-Geräten, auf denen Updates bereitgestellt werden. Sie können einen Drilldown in den Bericht pro Gerät durchführen, um die Status bestimmter Updates anzuzeigen.

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

### <a name="new-android-report-on-devices-overview-page----2984353----"></a>Seite "neuer Android-Bericht auf Geräten (Übersicht)" <!-- 2984353  -->
Wir fügen der Seite Geräte Übersicht einen neuen Bericht hinzu, auf dem angezeigt wird, wie viele Android-Geräte in jeder Geräte Verwaltungs Lösung registriert wurden. Dieses Diagramm zeigt die Anzahl von Arbeits Profilen, vollständig verwalteten, dedizierten und Geräte Administratoren registrierten Geräte. Um den Bericht anzuzeigen, klicken Sie auf **InTune**- > **Geräte** > **Übersicht**.

### <a name="windows-autopilot-deployment-reports----3856172----"></a>Bereitstellungsberichte für Windows Autopilot <!-- 3856172  -->
Ein neuer Bericht enthält detaillierte Informationen zu jedem Gerät, das über Windows Autopilot bereitgestellt wird. Diese Daten sind 30 Tage nach der Bereitstellung verfügbar. Um den Bericht anzuzeigen, wechseln Sie zu **InTune** > **Geräte**Registrierung  > **Monitor** > **Autopilot**-bereit Stellungen.

### <a name="updated-support-experience-------5012398------"></a>Aktualisierter Support   <!--  5012398    -->
Im Rahmen der fortlaufenden Verbesserungen wird die Unterstützung der Konsolen internen Unterstützung für InTune aktualisiert.  Wir werden die Konsolen interne Suche und das Feedback zu häufigen Problemen verbessern und den Workflow optimieren, um den Support zu kontaktieren.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).




