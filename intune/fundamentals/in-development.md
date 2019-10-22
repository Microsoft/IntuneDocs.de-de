---
title: 'In der Entwicklung: Microsoft Intune'
titleSuffix: ''
description: In der Entwicklung befindliche Microsoft Intune-Features
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea5fae72f6e2057ef0b03a7bd295085ed1ac3bbd
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601546"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>In der Entwicklung befindliche Microsoft Intune-Features: Oktober 2019

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

### <a name="apply-dark-mode-in-ios-company-portal----4911422----"></a>Anwenden des dunklen Modus in ios-Unternehmensportal <!-- 4911422  -->
Der dunkle Modus ist für IOS-Unternehmensportal geplant. Sie werden in der Lage sein, Unternehmens-apps herunterzuladen, Ihre Geräte zu verwalten und Sie in dem Farbschema Ihrer Wahl zu unterstützen. Weitere Informationen zum iOS-Unternehmensportal finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](../apps/company-portal-app.md).

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

### <a name="assign-the-microsoft-edge-beta-for-macos----4678761----"></a>Zuweisen der Microsoft Edge-Beta Version für macOS <!-- 4678761  -->
Sie können die neueste Version von Microsoft Edge Beta in InTune für macOS-Geräte hinzufügen und zuweisen. 

So weisen Sie die Microsoft Edge-Beta Version für macOS-Geräte zu:
1. Wählen Sie in InTune die Option **Client-apps**  > **apps**  >  App  > **Microsoft Edge-macOS** **Hinzufügen** aus. 
1. Weisen Sie die Microsoft Edge-Beta Version den vorgesehenen Gruppen zu. Microsoft Auto Update (Mau) hält Microsoft Edge auf dem neuesten Stand. 
 
Weitere Informationen zu Microsoft Edge finden Sie unter [Verwalten des Webzugriffs mithilfe von Microsoft Edge mit Microsoft InTune](../apps/manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurieren von App-Benachrichtigungs Inhalten für Organisations Konten <!-- 2576686 -->
Mit der InTune-App auf Android-und IOS-Geräten können Sie App-Benachrichtigungs Inhalte für Organisations Konten steuern. Diese Funktion erfordert Unterstützung von Anwendungen und ist möglicherweise nicht für alle App-fähigen Anwendungen verfügbar. Weitere Informationen über App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>Gerätekonfiguration

### <a name="new-device-firmware-configuration-interface-profile-for-devices-that-run-windows-10-and-later----2266073----"></a>Neues Geräte-Firmware-Konfigurations Schnittstellen Profil für Geräte, auf denen Windows 10 und höher ausgeführt wird <!-- 2266073  -->
Unter Windows 10 und höher können Sie ein Geräte Konfigurations Profil erstellen, um Einstellungen und Features zu steuern: 

1. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
1. Wählen Sie **Windows 10 und höher** als Plattform aus. 
 
Mit einem neuen geräteregistrierungs-Schnittstellen Profiltyp kann InTune UEFI-Einstellungen (BIOS) verwalten.

Informationen zu den aktuellen Einstellungen, die Sie konfigurieren können, finden Sie unter [Anwenden von Features und Einstellungen auf Ihren Geräten mithilfe von Geräte Profilen in Microsoft InTune](../configuration/device-profiles.md).

Diese Funktion gilt für Windows 10 RS5 (1809) und höher auf ausgewählten Geräten.
 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Geräteregistrierung

### <a name="for-ios-devices-customize-the-enrollment-privacy-window-of-company-portal----4394993----"></a>Passen Sie für IOS-Geräte das Fenster Datenschutz für die Anmeldung von Unternehmensportal <!-- 4394993  -->
Mithilfe von Markdown können Sie das Datenschutzfenster im Unternehmensportal anpassen, das den Endbenutzern während der iOS-Registrierung angezeigt wird. Insbesondere können Sie die Liste der Elemente und Vorgänge anpassen, die Ihre Organisation auf dem Gerät nicht anzeigen bzw. ausführen kann.

<!-- ***********************************************-->
## <a name="device-management"></a>Geräteverwaltung


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Bearbeiten des Gruppentag Werts für Autopilot-Geräte<!-- 4816775 -->
Sie können den **gruppentagwert** für Autopilot-Geräte bearbeiten:

1. Wählen Sie **InTune**  > **Geräte** Registrierung  > **Windows** -Registrierung  > **Windows Autopilot**  > **Geräte**aus.
1. Wählen Sie das Gerät aus.
1. Ändern Sie im rechten Bereich den **gruppentagwert** .
1. Wählen Sie **Speichern** aus.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>MacOS-Benutzergruppen als Ziel für die JAMF-Verwaltung <!-- 4061739 -->
Sie sind in der Lage, bestimmte Benutzergruppen als Ziel festzulegen, damit Ihre macOS-Geräte von JAMF verwaltet werden. Mit dieser Zielgruppe können Sie die JAMF-Kompatibilitäts Integration auf eine Teilmenge von macOS-Geräten anwenden, während andere Geräte weiterhin von InTune verwaltet werden. Mit der Zielgruppe können Sie die Benutzer Geräte nach und nach von einem MDM-System (Mobile Device Management, Verwaltung mobiler Geräte) zum anderen migrieren.

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Bereitstellen von Software Updates für macOS-Geräte <!-- 3194876 -->
Sie können Software Updates für Gruppen von macOS-Geräten bereitstellen. Diese Funktion umfasst kritische, Firmware-und Konfigurationsdateien sowie andere Updates. Sie können beim nächsten Einchecken von Geräten Updates senden. Oder Sie können einen wöchentlichen Zeitplan auswählen, um Updates in oder außerhalb der von Ihnen festgelegten Zeiträume bereitzustellen. 

Diese Funktion ist hilfreich, wenn Sie Geräte außerhalb der Standard Arbeitszeiten oder außerhalb der Geschäftszeiten aktualisieren möchten, wenn Ihr Helpdesk vollständig besetzt ist. Außerdem erhalten Sie einen ausführlichen Bericht zu allen macOS-Geräten, für die Updates bereitgestellt wurden. Sie können einen Drilldown in den Bericht nach Gerät durchführen, um den Status eines bestimmten Updates anzuzeigen.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Überwachung und Problembehandlung

### <a name="android-report-on-the-devices-overview-page----2984353----"></a>Android-Bericht auf der Seite "Geräte Übersicht" <!-- 2984353  -->
Wir fügen der Seite " **Geräte Übersicht** " einen neuen Bericht hinzu. Im Bericht wird angezeigt, wie viele Android-Geräte in jeder Geräte Verwaltungs Lösung registriert wurden. Das Diagramm zeigt die Anzahl der Geräte, die für das Arbeitsprofil, vollständig verwaltet, dediziert und Geräte Administrator registriert sind. 

Um den Bericht anzuzeigen, klicken Sie auf **InTune**- > **Geräte** > **Übersicht**.

### <a name="updated-support-experience-------5012398------"></a>Aktualisierter Support   <!--  5012398    -->
Im Rahmen der fortlaufenden Verbesserungen aktualisieren wir die Konsolen interne Unterstützung für InTune.  Wir werden die Konsolen interne Suche und das Feedback zu häufigen Problemen verbessern. Wir optimieren den Workflow, um sich an den Support zu wenden.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuerungen in Microsoft Intune](whats-new.md).
