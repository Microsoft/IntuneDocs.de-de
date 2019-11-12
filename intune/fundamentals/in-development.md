---
title: 'In der Entwicklung: Microsoft Intune'
titleSuffix: ''
description: In der Entwicklung befindliche Microsoft Intune-Features
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3720b0b9a67f0c3462993feef4162ef35f7f3f92
ms.sourcegitcommit: d1b36501186e867355843ddd67c795ade800b76a
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182927"
---
# <a name="in-development-for-microsoft-intune---november-2019"></a>In der Entwicklung befindliche Microsoft Intune-Features: November 2019

Um Ihnen bei Ihrer Vorbereitung und Planung zu helfen, sind auf dieser Seite Updates und Features der Intune-Benutzeroberfläche aufgeführt, die sich in der Entwicklung befinden, aber noch nicht freigegeben wurden. Zusätzlich zu den Informationen auf dieser Seite:

- Wenn wir davon ausgehen, dass Sie vor einer Änderung Maßnahmen ergreifen müssen, werden wir einen ergänzenden Beitrag im Office-Nachrichtencenter veröffentlichen.
- Wenn eine Funktion in die Produktionsumgebung wechselt, egal ob es sich um eine Vorschauversion handelt oder allgemein verfügbar ist, wird die Funktionsbeschreibung von dieser Seite zu den [Neuerungen](whats-new.md)verschoben.
- Diese Seite und die Seite [Neuerungen](whats-new.md) werden regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.
- In der [Roadmap für Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) finden Sie strategische Ziele und Zeitpläne.

> [!NOTE]
> Diese Seite spiegelt unsere aktuellen Erwartungen an die Intune-Funktionen in einer zukünftigen Version wider. Termine und einzelne Features können sich ändern. Auf dieser Seite werden nicht alle Features in der Entwicklung beschrieben.

**RSS-Feed**: Bleiben Sie auf dem Laufenden, wenn diese Seite aktualisiert wird, indem Sie die folgende URL kopieren und in Ihren Feedreader einfügen: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`.

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

### <a name="smime-support-for-microsoft-outlook-mobile----2669398----"></a>S/MIME-Unterstützung für Microsoft Outlook Mobile <!-- 2669398  -->
InTune unterstützt die Bereitstellung von S/MIME-Signatur-und Verschlüsselungs Zertifikaten, die mit Outlook Mobile unter IOS und Android verwendet werden können. Weitere Informationen finden Sie unter [e-Mail-Einstellungen für IOS-Geräte](~/configuration/email-settings-ios.md) und [e-Mail-Einstellungen für Android-Geräte](~/configuration/email-settings-android.md)

### <a name="custom-settings-support-for-macos-applications----4736278----"></a>Unterstützung für benutzerdefinierte Einstellungen für macOS-Anwendungen <!-- 4736278  -->
InTune unterstützt benutzerdefinierte Einstellungen, mit denen Sie einer vorhandenen Einstellungs Liste (plist-Datei) bestimmte Schlüssel und Werte hinzufügen können, um macOS-apps und das Gerät zu konfigurieren. Nicht alle apps unterstützen verwaltete Einstellungen, und in einigen Fällen können nur bestimmte Einstellungen verwaltet werden. Die Einstellungen werden nur über den Geräte Kanal bereitgestellt. Sie sollten nur Eigenschaften Listen Dateien oder XML-Dateien hochladen, die auf Geräte Kanaleinstellungen abzielen.

### <a name="assignment-type-value-in-windows-company-portal----5459950----"></a>Wert des Zuweisungs Typs in Windows Unternehmensportal <!-- 5459950  -->
Die Seite **installierte apps** der Windows Unternehmensportal-APP wird aktualisiert. Die Spalte " **Zuweisungstyp** " der Seite " **installierte apps** " wurde so aktualisiert, dass Sie "von Ihrer Organisation benötigt" aufgerufen wird. Mögliche Werte sind " **Yes** " oder " **No** ", um erforderliche und verfügbare apps festzulegen. Diese Änderung wird als Reaktion auf einige Endbenutzer Verwirrung vorgenommen. Weitere Informationen zum Windows-Unternehmensportal finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](~/apps/company-portal-app.md).

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Ausführen von Win32-apps auf Geräten im Windows 10-Modus <!-- 3747604  --> 
Sie können Win32-apps auf Geräten installieren und ausführen, die im Windows 10 S-Modus verwaltet werden. Erstellen Sie eine oder mehrere ergänzende Richtlinien für den S-Modus, indem Sie die PowerShell-Tools von Windows Defender Application Control (WDac) verwenden. Verwenden Sie das Device Guard-Signatur Portal, um die ergänzenden Richtlinien zu signieren. Anschließend laden Sie die Richtlinien hoch und verteilen Sie über InTune. 

In InTune finden Sie diese Funktion, indem Sie **Client-apps**  > **ergänzenden Windows 10 S-Richtlinien**auswählen. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Festlegen der APP-Verfügbarkeit basierend auf einem Datum und einer Uhrzeit <!-- 3510685  -->
Als Administrator können Sie die Startzeit und den Stichtag für eine erforderliche App konfigurieren. Zum Startzeitpunkt lädt die Intune-Verwaltungs Erweiterung den App-Inhalt herunter und speichert ihn zwischen. Die APP wird zum Stichtag installiert. Für verfügbare apps wird durch die Startzeit vorgegeben, wann die app in Unternehmensportal sichtbar ist. 

So legen Sie die APP-Verfügbarkeit basierend auf Datum und Uhrzeit fest:

1. Klicken Sie in Intune auf **Client-Apps** > **Apps**. 
1. Wählen Sie eine APP aus der Liste aus, oder fügen Sie einen neuen hinzu, indem **Sie hinzufügen**auswählen. 
1. Wählen Sie auf dem App-Blatt **Zuweisungen** > **Gruppe hinzufügen**aus. 
1. Legen Sie den **Zuweisungstyp** auf **erforderlich** und dann auf **enthaltene Gruppen**fest. 
1. Legen Sie **diese APP für alle Benutzer erforderlich** auf **Ja**fest. 
1. Wählen Sie **Bearbeiten** aus, um die Optionen für **Endbenutzer** Optionen zu ändern. 
1. Legen Sie auf dem Blatt **Endbenutzer** Darstellung die **verfügbare Software Zeit** nach Bedarf fest. 

Weitere Informationen finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Neustarten von Win32-apps erforderlich <!-- 3136567  -->
Nach einer erfolgreichen Installation ist es möglich, eine Win32-APP neu zu starten. Sie können die Zeitspanne (die Toleranz Periode) vor dem Neustart auswählen.

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>Anzeigen von Benachrichtigungen für die Unternehmensportal-app unter Windows <!-- 1808082  -->
Wir werden die Unternehmensportal-App auf Windows-Geräten aktualisieren, um Benutzern Popup Benachrichtigungen anzuzeigen, auch wenn die Anwendung geschlossen wird. Das Update zeigt nur dann Benachrichtigungen für verfügbare apps an, wenn der Installationsstatus "abgeschlossen" oder "Fehler" lautet. Die Unternehmensportal-APP zeigt keine Benachrichtigungen für erforderliche Anwendungen an.

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>Anzeigen der Installationsstatus Meldungen für die Unternehmensportal-App <!-- 2514416  -->
Die Unternehmensportal-APP zeigt den Endbenutzern zusätzliche APP-Installationsstatus Meldungen an. Die folgenden Bedingungen gelten für neue Win32-Abhängigkeits Features:
- Die App konnte nicht installiert werden. Vom Administrator definierte Abhängigkeiten wurden nicht erfüllt.
- Die APP wurde erfolgreich installiert, erfordert aber einen Neustart.
- Die APP wird gerade installiert, aber es ist ein Neustart erforderlich, um den Vorgang fortzusetzen.

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurieren von App-Benachrichtigungs Inhalten für Organisations Konten <!-- 2576686 -->
Mit der InTune-App auf Android-und IOS-Geräten können Sie App-Benachrichtigungs Inhalte für Organisations Konten steuern. Diese Funktion erfordert Unterstützung von Anwendungen und ist möglicherweise nicht für alle App-fähigen Anwendungen verfügbar. Weitere Informationen über App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>Gerätekonfiguration

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices----3246388----"></a>Verwenden von PKCS-Zertifikaten mit WLAN-Profilen auf Geräten mit Windows 10 und höher <!-- 3246388  -->
Derzeit können Sie Windows-WLAN-Profile mit SCEP-Zertifikaten authentifizieren (**Gerätekonfiguration** > **profile** > **Profil erstellen** > **Windows 10 und** höher für die Plattform > **Wi-Fi** für Profiltyp > **Enterprise** > **EAP-Typ**). Sie können PKCS-Zertifikate mit Ihren Windows Wi-Fi-Profilen verwenden. Diese Funktion ermöglicht Benutzern das Authentifizieren von WLAN-Profilen mithilfe neuer oder vorhandener PKCS-Zertifikat Profile in Ihrem Mandanten. 

Weitere Informationen zu WLAN-Profilen finden [Sie unter Hinzufügen von WLAN-Einstellungen für Windows 10-und spätere Geräte in InTune](../configuration/wi-fi-settings-windows.md).

Gilt für:
- Windows 10 und höher

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices----4892824----"></a>Neue ExchangeActiveSync-Einstellungen beim Erstellen eines e-Mail-Geräte Konfigurations Profils auf IOS-Geräten <!-- 4892824  --> 
Auf IOS/ipados-Geräten können Sie e-Mail-Konnektivität in einem Geräte Konfigurations Profil konfigurieren (**Gerätekonfiguration** > **profile** > **Erstellen eines Profils** > **IOS/ipados** für die Plattform > **e-Mail** . für Profiltyp). 

Es sind neue ExchangeActiveSync-Einstellungen verfügbar, einschließlich:
- Wählen Sie die zu synchronisierenden Dienste (oder die Synchronisierung blockieren) aus, z. b. e-Mail, Kalender und Kontakte.
- Hiermit wird Benutzern das Ändern der Synchronisierungs Einstellungen für diese Dienste auf Ihren Geräten gestattet (oder blockiert). 

Informationen zu den aktuellen Einstellungen finden Sie unter [e-Mail-Profileinstellungen für IOS-Geräte in InTune](../configuration/email-settings-ios.md).

Gilt für:
- iOS 13.0 und neuer
- iOS 13.0 und höher

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices----5353228----"></a>Verhindern, dass Benutzer persönliche Google-Konten zu Android-Unternehmens Geräte Besitzern und dedizierten Geräten hinzufügen <!-- 5353228  -->
Sie können verhindern, dass Benutzer persönliche Google-Konten auf Android-Unternehmens Geräte Besitzern und dedizierten Geräten erstellen (**Gerätekonfiguration** > **profile** > **Profil erstellen** > **Android Enterprise** nur für Platt Form > **Gerätebesitzer > Geräte Einschränkungen** für den Profiltyp > **Benutzer-und Kontoeinstellungen**).

Sie finden die aktuellen konfigurierbaren Einstellungen unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune](../configuration/device-restrictions-android-for-work.md).

Gilt für:
- Android Enterprise-Gerätebesitzer
- Dedizierte Android Enterprise-Geräte

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile----5468501----"></a>Die Server seitige Protokollierung für die Siri-Befehls Einstellung wird im IOS-Geräte Einschränkungs Profil entfernt. <!-- 5468501  -->
Auf IOS-Geräten können Sie ein Geräte Einschränkungs Profil erstellen, das die serverseitige Protokollierung für Siri-Befehle konfiguriert (**Geräte Konfigurations** > **profile** > **Profil** > **IOS/ipados** für die Plattform erstellen). > **Geräte Einschränkungen** für den Profiltyp > **integrierten Apps**). Die Einstellung **Server seitige Protokollierung für Siri-Befehle** wird entfernt.

Diese Einstellung wird aus der InTune-Verwaltungskonsole entfernt. Diese Einstellung hat keine Auswirkung auf das Gerät, auch wenn vorhandene Richtlinien, bei denen diese Einstellung konfiguriert ist, die Einstellung weiterhin anzeigen. Wenn Sie die Einstellung aus vorhandenen Richtlinien entfernen möchten, klicken Sie auf die Richtlinie, nehmen Sie eine kleine Bearbeitung vor, speichern Sie Sie, und die Richtlinie wird aktualisiert.

Sie finden die konfigurierbaren Einstellungen unter [iOS- und iPadOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](../configuration/device-restrictions-ios.md).

Gilt für:
- iOS


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>Geräteverwaltung

### <a name="edit-device-name-value-for-autopilot-devices---2640074----"></a>Bearbeiten des Geräte namens Werts für Autopilot-Geräte<!-- 2640074  -->
Sie können den Wert für den Gerätenamen für Azure AD verbundenen Autopilot-Geräten bearbeiten. Wechseln Sie hierzu zu **InTune** > **Geräte** Registrierung > **Windows** -Registrierung > **Windows Autopilot** > **Geräte** > Wählen Sie das Gerät aus, um den Wert des **Geräte namens** im rechten Bereich zu ändern. > **Speichern**.


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Bearbeiten des Gruppentag Werts für Autopilot-Geräte<!-- 4816775 -->
Sie können den **gruppentagwert** für Autopilot-Geräte bearbeiten:

1. Wählen Sie **InTune**  > **Geräte** Registrierung  > **Windows** -Registrierung  > **Windows Autopilot**  > **Geräte**aus.
1. Wählen Sie das Gerät aus.
1. Ändern Sie im rechten Bereich den **gruppentagwert** .
1. Wählen Sie **Speichern** aus.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>MacOS-Benutzergruppen als Ziel für die JAMF-Verwaltung <!-- 4061739 -->
Sie sind in der Lage, bestimmte Benutzergruppen als Ziel festzulegen, damit Ihre macOS-Geräte von JAMF verwaltet werden. Mit dieser Zielgruppe können Sie die JAMF-Kompatibilitäts Integration auf eine Teilmenge von macOS-Geräten anwenden, während andere Geräte weiterhin von InTune verwaltet werden. Mit der Zielgruppe können Sie die Benutzer Geräte nach und nach von einem MDM-System (Mobile Device Management, Verwaltung mobiler Geräte) zum anderen migrieren.

<!-- ***********************************************-->
## <a name="intune-apps"></a>Intune-Apps

### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>Verbesserte macOS-Registrierungs Umgebung in Unternehmensportal <!-- 5074349  -->
Der Unternehmensportal für die macOS-Registrierungs Umgebung wird einen einfacheren Registrierungsvorgang haben, der sich stärker mit dem Unternehmensportal für die IOS-Registrierung ausgleicht. Geräte Benutzern wird Folgendes angezeigt:  

* Eine sleeker-Benutzeroberfläche.  
* Eine verbesserte Registrierungs Checkliste.  
* Deutlichere Anweisungen zum Registrieren Ihrer Geräte.  
* Verbesserte Optionen zur Problembehandlung.  

### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857----"></a>Verbessertes Prüfliste-Design in Unternehmensportal-App für Android<!-- 5550857  -->
Die Setup Checkliste in der Unternehmensportal-App für Android wird mit einem vereinfachten Design und neuen Symbolen aktualisiert. Die Änderungen richten sich an die aktuellen Updates, die an der Unternehmensportal-App für IOS vorgenommen wurden.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Überwachung und Problembehandlung

### <a name="updated-support-experience-------5012398------"></a>Aktualisierter Support   <!--  5012398    -->
Im Rahmen der fortlaufenden Verbesserungen aktualisieren wir die Konsolen interne Unterstützung für InTune.  Wir werden die Konsolen interne Suche und das Feedback zu häufigen Problemen verbessern. Wir optimieren den Workflow, um sich an den Support zu wenden.     

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

### <a name="duplicate-custom-or-built-in-roles----1081938---"></a>Doppelte benutzerdefinierte oder integrierte Rollen <!-- 1081938 -->
Sie können integrierte und benutzerdefinierte Rollen kopieren. Wechseln Sie zu diesem Zweck zu **InTune** > **Rollen** > **alle Rollen** , > Wählen Sie eine Rolle in der Liste > **Duplizieren**aus. Stellen Sie sicher, dass Sie einen neuen eindeutigen Namen eingeben.

<!-- ***********************************************-->

## <a name="security"></a>Sicherheit

### <a name="bitlocker-key-rotation--------2564951--------"></a>BitLocker-Schlüssel Rotation     <!-- 2564951      -->
Sie können InTune zum Rotieren der BitLocker-Wiederherstellungs Schlüssel für verwaltete Geräte verwenden, auf denen Windows-Version 1909 oder höher ausgeführt wird. 

<!-- ***********************************************-->
## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuerungen in Microsoft Intune](whats-new.md).
