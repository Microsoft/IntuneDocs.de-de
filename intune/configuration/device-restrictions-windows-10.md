---
title: Intune-Einstellungen für Geräteeinschränkungen für Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Eine Liste mit allen Einstellungen und ihren Beschreibungen zum Erstellen von Geräteeinschränkungen für Windows 10 und höher wird angezeigt. Verwenden Sie diese Einstellungen in einem Konfigurationsprofil zum Steuern von Screenshots, Kennwortanforderungen, Kioskeinstellungen, Apps im Store, Microsoft Edge-Browser, Microsoft Defender, des Cloudzugriffs, Startmenüs und mehr in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f0cf7d6f18b0d345a8c491984987b9ffa234d66e
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059479"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Einstellungen für Windows 10-Geräte (und höher) zum Zulassen oder Einschränken von Features mit Intune

In diesem Artikel werden die verschiedenen Einstellungen aufgeführt und beschrieben, die Sie auf Geräten mit Windows 10 und höher festlegen können. Verwenden Sie diese Einstellungen im Rahmen Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM), um Features zuzulassen oder zu deaktivieren, Kennwortregeln festzulegen, den Sperrbildschirm anzupassen, Microsoft Defender zu verwenden und vieles mehr.

Diese Einstellungen werden erst einem Gerätekonfigurationsprofil in Intune hinzugefügt und dann Ihren Windows 10-Geräten zugewiesen oder für diese bereitgestellt.

> [!Note]
> Nicht alle Optionen sind in allen Windows-Editionen verfügbar. Die unterstützten Editionen finden Sie in unter [Konfigurationsdienstanbieter für Richtlinien](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (öffnet eine andere Microsoft-Website).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](device-restrictions-configure.md#create-the-profile)

## <a name="app-store"></a>App Store

Diese Einstellungen verwenden den [ApplicationManagement-Richtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement), der auch die unterstützten Windows-Editionen auflistet.

- **App Store** (nur Mobilgeräte): **Nicht konfiguriert** (Standard) ermöglicht Endbenutzern Zugriff auf den App Store auf mobilen Geräte. **Blockieren** verhindert die Verwendung von App Store.
- **Apps aus Store automatisch aktualisieren**: **Nicht konfiguriert** (Standard) ermöglicht die automatische Aktualisierung von Apps, die aus dem Microsoft Store installiert wurden. **Blockieren** verhindert, dass Updates automatisch installiert werden.
- **Installation vertrauenswürdiger Apps**: Wählen Sie diese Option aus, wenn Apps installiert werden können, die nicht aus dem Microsoft Store stammen. Dies wird auch als Querladen bezeichnet. Querladen bedeutet Installieren und anschließendes Ausführen oder Testen einer App, die nicht durch den Microsoft Store zertifiziert ist. Beispielsweise kann es sich um eine App handeln, die nur für Ihr Unternehmen intern ist. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Verwendet die Betriebssystem-Standardeinstellung.
  - **Blockieren**: Verhindert Querladen. Apps, die nicht auf dem Microsoft Store stammen, können nicht installiert werden.
  - **Zulassen**: Ermöglicht Querladen. Apps, die nicht auf dem Microsoft Store stammen, können installiert werden.
- **Entwicklersperre aufheben**: Ermöglicht Endbenutzern, Windows-Entwicklereinstellungen (z.B. das Zulassen quergeladener Apps) zu ändern. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Verwendet die Betriebssystem-Standardeinstellung.
  - **Blockieren**: Verhindert den Entwicklermodus und das Querladen von Apps.
  - **Zulassen**: Erlaubt den Entwicklermodus und das Querladen von Apps.

  Unter [Aktivieren des Geräts für die Entwicklung](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) finden Sie weitere Informationen zu dieser Funktion.

- **Gemeinsam genutzte App-Benutzerdaten**: Wählen Sie **Zulassen** aus, um Anwendungsdaten für verschiedene Benutzer auf dem gleichen Gerät und andere Instanzen dieser App freizugeben. **Nicht konfiguriert** (Standard) verhindert das Freigeben von Daten für andere Benutzer und andere Instanzen der gleichen App.
- **Nur privaten Store verwenden**: **Zulassen** erlaubt nur das Herunterladen von Apps aus einem privaten Store und nicht aus dem öffentlichen Store (einschließlich eines Einzelhandelskatalogs). **Nicht konfiguriert** (Standard) ermöglicht das Herunterladen von Apps aus einem privaten und einem öffentlichen Store.
- **Store-App starten**: **Blockieren** deaktiviert alle Apps, die bereits auf dem Gerät installiert waren oder aus dem Microsoft Store heruntergeladen wurden. **Nicht konfiguriert** (Standard) erlaubt das Öffnen dieser Apps.
- **App-Daten in Systemvolume installieren**: **Blockieren** hindert Apps daran, Daten auf dem Systemvolume des Geräts zu speichern. **Nicht konfiguriert** (Standard) erlaubt Apps das Speichern von Daten auf dem Systemvolume.
- **Apps auf Systemlaufwerk installieren**: **Blockieren** hindert Apps daran, eine Installation auf dem Systemlaufwerk des Geräts auszuführen. **Nicht konfiguriert** (Standard) erlaubt Apps Installationen auf dem Systemlaufwerk.
- **Game DVR** (nur Desktop): **Blockieren** deaktiviert die Windows-Spieleaufzeichnung und -übertragung. **Nicht konfiguriert** (Standard) lässt die Aufzeichnung und Übertragung von Spielen zu.
- **Nur apps aus dem Store**: Diese Einstellung bestimmt die Benutzerumgebung, wenn Benutzer apps von anderen Orten als der Microsoft Store installieren. Folgende Optionen sind verfügbar:

  - **Nicht konfiguriert** (Standardeinstellung): ermöglicht Endbenutzern die Installation von apps von anderen Orten als der Microsoft Store, einschließlich apps, die in anderen Richtlinien Einstellungen definiert sind.  
  - **Anywhere**: deaktiviert App-Empfehlungen und ermöglicht Benutzern die Installation von apps von einem beliebigen Standort aus.  
  - **Nur Store**: erzwingt Endbenutzer, nur apps aus dem Microsoft Store zu installieren.
  - **Empfehlungen**: bei der Installation einer App aus dem Internet, die im Microsoft Store verfügbar ist, wird Benutzern eine Meldung angezeigt, die Sie aus dem Store herunterlädt.  
  - **Store bevorzugen**: warnt Benutzer, wenn Sie apps von anderen Orten als der Microsoft Store installieren.

  [SmartScreen/enableappinstallcontrol-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen#smartscreen-enableappinstallcontrol)

- **Benutzerkontrolle über Installationen**: Bei Festlegung auf **Nicht konfiguriert** (Standard) verhindert der Windows Installer, dass Benutzer die Installationsoptionen ändern, die in der Regel für Systemadministratoren reserviert sind, etwa durch Eingeben des Installationsverzeichnisses. **Blockieren** ermöglicht es Benutzern, diese Installationsoptionen zu ändern, und einige der Sicherheitsfeatures des Windows Installers werden umgangen.

  [ApplicationManagement/MSIAllowUserControlOverInstall CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msiallowusercontroloverinstall)

- **Apps mit erhöhten Rechten installieren**: Bei Festlegung auf **Nicht konfiguriert** (Standard) wendet das System bei der Installation von Programmen die Berechtigungen des aktuellen Benutzers an, die nicht von einem Systemadministrator bereitgestellt oder angeboten werden. **Blockieren** weist den Windows Installer an, bei der Installation von Programmen auf dem System erhöhte Rechte anzuwenden. Diese Berechtigungen werden auf alle Programme ausgeweitet.

  [ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msialwaysinstallwithelevatedprivileges)

- **Start-Apps**: Geben Sie eine Liste der Apps ein, die nach der Anmeldung eines Benutzers beim Gerät gestartet werden sollen. Achten Sie darauf, eine durch Semikolons getrennte Liste von Paketfamiliennamen (PFN) von Windows-Anwendungen zu verwenden. Damit diese Richtlinie funktioniert, muss das Manifest in den Windows-Apps eine Startaufgabe verwenden.

  [ApplicationManagement/LaunchAppAfterLogOn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-launchappafterlogon)

## <a name="cellular-and-connectivity"></a>Mobilfunk und Konnektivität

Diese Einstellungen verwenden die [Konnektivitätsrichtlinien](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity)- und [WLAN-Richtlinien](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)-CSPs, die auch die unterstützten Windows-Editionen auflisten.

- [WLAN-Richtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)

- **Mobilfunkdatenkanal**: Ermöglicht, dass Endbenutzer Daten verbrauchen (wie z.B. beim Browsen im Web), wenn sie mit einem Mobilfunknetz verbunden sind. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Verwendet die Betriebssystem-Standardeinstellung, die den Mobilfunkdatenkanal erlauben kann. Endbenutzer können diese Funktion deaktivieren.
  - **Blockieren**: Der Mobilfunkdatenkanal ist unzulässig. Endbenutzer können diese Funktion nicht aktivieren.
  - **Zulassen (Bearbeitung nicht möglich)** : Ermöglicht den Mobilfunkdatenkanal. Endbenutzer können diese Funktion nicht deaktivieren.

- **Datenroaming**: **Blockieren** verhindert Mobilfunkdatenroaming auf dem Gerät. **Nicht konfiguriert** (Standard) erlaubt beim Zugriff auf Daten das Roaming zwischen Netzwerken.
- **VPN über Mobilfunknetz**: **Blockieren** verhindert, dass das Gerät auf VPN-Verbindungen zugreifen kann, wenn es mit einem Mobilfunknetz verbunden ist. **Nicht konfiguriert** (Standard) ermöglicht dem VPN das Verwenden einer beliebigen Verbindung einschließlich Mobilfunk.
- **VPN-Roaming über Mobilfunknetz**: **Blockieren** verhindert, dass das Gerät beim Roaming in einem Mobilfunknetz auf VPN-Verbindungen zugreifen kann. **Nicht konfiguriert** (Standard) ermöglicht VPN-Verbindungen beim Roaming.
- **Dienst für verbundene Geräte**: **Blockieren** deaktiviert die CDP-Komponente (Connected Devices Platform, Plattform für verbundene Geräte). CDP ermöglicht die Erkennung von und die Verbindung mit anderen Geräten (über Bluetooth/LAN oder die Cloud), um den Start von Remote-Apps, Remotemessaging, App-Remotesitzungen und andere geräteübergreifende Funktionen zu unterstützen. **Nicht konfiguriert** (Standard) ermöglicht die Entscheidung, ob dem Dienst für verbundene Geräte die Ermittlung von und Verbindung mit anderen Bluetooth-Geräten erlaubt wird.
- **NFC**: **Blockieren** verhindert NFC-Funktionen. **Nicht konfiguriert** (Standard) ermöglicht Benutzern das Aktivieren und Konfigurieren von NFC-Funktionen auf dem Gerät.
- **WLAN**: **Blockieren** verhindert, dass Benutzer WLAN-Verbindungen auf dem Gerät aktivieren, konfigurieren und verwenden können. **Nicht konfiguriert** (Standard) lässt WLAN-Verbindungen zu.
- **Automatisch mit WLAN-Hotspots verbinden**: **Blockieren** verhindert, dass Geräte automatisch eine Verbindung mit WLAN-Hotspots herstellen. **Nicht konfiguriert** (Standard) ermöglicht automatische Verbindungen des Geräts mit unverschlüsselten WLAN-Hotspots und das automatische Akzeptieren der Geschäftsbedingungen für die Verbindung.
- **Manuelle WLAN-Konfiguration**: **Blockieren** verhindert, dass Geräte mit eine Verbindung mit einem WLAN außerhalb der MDM-serverinstallierten Netzwerke herstellen können. **Nicht konfiguriert** (Standard) ermöglicht Benutzern das Hinzufügen und Konfigurieren ihrer eigenen WLAN-Verbindungsnetzwerk-SSIDs.
- **Intervall für WLAN-Suche:** Geben Sie ein, wie oft Geräte nach WLAN-Netzwerken suchen. Geben Sie einen Wert zwischen 1 (am häufigsten) und 500 (am seltensten) ein. Der Standardwert ist `0` (null).

### <a name="bluetooth"></a>Bluetooth

Diese Einstellungen verwenden den [Bluetooth-Richtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth), der auch die unterstützten Windows-Editionen auflistet.

- **Bluetooth**: **Blockieren** verhindert, dass Benutzer Bluetooth aktivieren können. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung von Bluetooth auf dem Gerät.
- **Bluetooth-Erkennbarkeit**: **Blockieren** verhindert die Erkennung dieses Geräts durch andere für Bluetooth aktivierte Geräte. **Nicht konfiguriert** (Standard) ermöglicht anderen Bluetooth Geräten (z.B. einem Kopfhörer) das Erkennen des Geräts.
- **Bluetooth-Vorabkopplung**: **Blockieren** verhindert Konfigurieren spezifischer Bluetooth-Geräte für automatische Koppelung mit einem Hostgerät. **Nicht konfiguriert** (Standard) ermöglicht die automatische Koppelung mit dem Hostgerät.
- **Bluetooth-Ankündigung**: **Blockieren** verhindert, dass das Gerät Bluetooth-Ankündigungen senden kann. **Nicht konfiguriert** (Standard) erlaubt dem Gerät das Senden von Bluetooth-Ankündigungen.
- **Zulässige Bluetooth-Dienste:** **Hinzufügen** einer Liste zulässiger Bluetooth-Dienste und -Profile in Form von hexadezimalen Zeichenfolgen, z.B. `{782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}`.

  [Im Leitfaden zu ServicesAllowedList](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide) finden Sie weitere Informationen zur Liste der Dienste.

## <a name="cloud-and-storage"></a>Cloud und Speicher

Diese Einstellungen verwenden den [Kontenrichtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-accounts), der auch die unterstützten Windows-Editionen auflistet.

- **Microsoft-Konto**: **Blockieren** verhindert, dass Endbenutzer dem Gerät einem Microsoft-Konto zuordnen können. **Nicht konfiguriert** (Standard) ermöglicht das Hinzufügen und Verwenden eines Microsoft-Kontos.
- **Nicht-Microsoft-Konto**: **Block** verhindert, dass Endbenutzer Nicht-Microsoft-Konten über die Benutzeroberfläche hinzufügen können. **Nicht konfiguriert** (Standard) erlaubt dem Benutzer, E-Mail-Konten hinzuzufügen, die nicht mit einem Microsoft-Konto verknüpft sind.
- **Synchronisierung der Einstellungen für Microsoft-Konto**: **Nicht konfiguriert** (Standard) erlaubt das Synchronisieren der mit einem Microsoft-Konto verknüpften Geräte- und App-Einstellungen zwischen Geräten. **Blockieren** verhindert diese Synchronisierung.
- **Anmelde-Assistent für Microsoft-Konten**: Bei Festlegung auf **Nicht konfiguriert** (Standard) können Benutzer den **Anmelde-Assistenten für Microsoft-Konten** (wlidsvc-Dienst) starten und beenden. Dieser Betriebssystemdienst ermöglicht Benutzern die Anmeldung bei ihrem Microsoft-Konto. **Deaktivieren** verhindert, dass Endbenutzer den Anmelde-Assistenten für Microsoft-Konten (wlidsvc-Dienst) steuern können.

## <a name="cloud-printer"></a>Clouddrucker

Diese Einstellungen verwenden den [EnterpriseCloudPrint-Richtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint), der auch die unterstützten Windows-Editionen auflistet.

- **URL für Druckerermittlung**: Geben Sie die URL zum Finden von Clouddruckern ein. Geben Sie beispielsweise `https://cloudprinterdiscovery.contoso.com` ein.
- **Autoritäts-URL für Druckerzugriff**: Geben Sie die Authentifizierungsendpunkt-URL zum Abrufen von OAuth-Token ein. Geben Sie beispielsweise `https://azuretenant.contoso.com/adfs` ein.
- **GUID für native Azure-Client-App**: Geben Sie die GUID einer Clientanwendung ein, die OAuth-Tokens von der OAuthAuthority abrufen darf. Geben Sie beispielsweise `E1CF1107-FF90-4228-93BF-26052DD2C714` ein.
- **Druckdienstressourcen-URI**: Geben Sie den OAuth-Ressourcen-URI für den im Azure-Portal konfigurierten Druckdienst ein. Geben Sie beispielsweise `http://MicrosoftEnterpriseCloudPrint/CloudPrint` ein.
- **Maximal abgefragte Drucker**: Geben Sie die maximale Anzahl von Druckern ein, die abgefragt werden sollen. Der Standardwert lautet `20`.
- **Ressourcen-URI für Druckerermittlungsdienst**: Geben Sie den OAuth-Ressourcen-URI für den im Azure-Portal konfigurierten Druckererkennungsdienst ein. Geben Sie beispielsweise `http://MopriaDiscoveryService/CloudPrint` ein.

> [!TIP]
> Nachdem Sie [Windows Server Hybrid Cloud Print](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview) eingerichtet haben, können Sie diese Einstellungen konfigurieren und auf Ihren Windows-Geräten bereitstellen.

## <a name="control-panel-and-settings"></a>Systemsteuerung und Einstellungen

- **Einstellungen-App**: **Blockieren** verhindert, dass Endbenutzer Zugriff auf die Windows-Einstellungen-App besitzen. Die Standardeinstellung **Nicht konfiguriert** ermöglicht es Benutzern, die Einstellungen-App auf dem Gerät zu öffnen.
  - **System**: **Blockieren**  verhindert den Zugriff auf den Systembereich der Einstellungen-App. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.
    - **Änderung der Energie- und Energiesparmoduseinstellungen (nur Desktop)** : **Blockieren** verhindert, dass der Endbenutzer Energie- und Energiesparmoduseinstellungen auf dem Gerät ändert. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, die Energie- und Energiesparmoduseinstellungen zu ändern.
  - **Geräte**: **Blockieren** verhindert den Zugriff auf den Gerätebereich der Einstellungen-App auf dem Gerät. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.
  - **Netzwerk/Internet**: **Blockieren** verhindert den Zugriff auf den Netzwerk- und Internetbereich der Einstellungen-App auf dem Gerät. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.
  - **Personalisierung**: **Blockieren** verhindert den Zugriff auf den Personalisierungsbereich der Einstellungen-App auf dem Gerät. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.
  - **Apps**: **Blockieren** verhindert den Zugriff auf den Apps-Bereich der Einstellungen-App auf dem Gerät. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.
  - **Konten**: **Blockieren** verhindert den Zugriff auf den Kontenbereich der Einstellungen-App auf dem Gerät. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.
  - **Uhrzeit und Sprache**: **Blockieren** verhindert den Zugriff auf den Uhrzeit- und Sprachbereich der Einstellungen-App auf dem Gerät. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.
    - **Änderung der Systemzeit**: **Blockieren** verhindert, dass der Endbenutzer auf dem Gerät die Datums- und Uhrzeiteinstellungen ändert. **Nicht konfiguriert** ermöglicht dem Benutzer, diese Einstellungen zu ändern.
    - **Änderung von Regionseinstellungen (nur Desktop)** : **Blockieren** verhindert, dass der Endbenutzer Regionseinstellungen auf dem Gerät ändert. **Nicht konfiguriert** ermöglicht dem Benutzer, diese Einstellungen zu ändern.
    - **Änderung von Spracheinstellungen (nur Desktop)** : **Blockieren** verhindert, dass der Endbenutzer Spracheinstellungen auf dem Gerät ändert. **Nicht konfiguriert** ermöglicht dem Benutzer, diese Einstellungen zu ändern.

      [Einstellungsrichtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings)

  - **Gaming**: **Blockieren** verhindert den Zugriff auf den Gamingbereich der Einstellungen-App auf dem Gerät. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.
  - **Erleichterte Bedienung**: **Blockieren** verhindert den Zugriff auf den Bereich für erleichterte Bedienung der Einstellungen-App auf dem Gerät. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.
  - **Datenschutz**: **Blockieren** verhindert den Zugriff auf den Datenschutzbereich der Einstellungen-App auf dem Gerät. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.
  - **Update und Sicherheit**: **Blockieren** verhindert den Zugriff auf den Bereich für Update und Sicherheit der Einstellungen-App auf dem Gerät. **Nicht konfiguriert** (Standard) erlaubt den Zugriff.

## <a name="display"></a>Anzeige

Diese Einstellungen verwenden den [Anzeigerichtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-display), der auch die unterstützten Windows-Editionen auflistet.

Mit der GDI-DPI-Skalierung können Anwendungen, die nicht mit DPI-Werten kompatibel sind, mit monitorspezifischen DPI-Werten kompatibel sein.

- **GDI-Skalierung für Apps aktivieren**: **Hinzufügen** von Legacy-Apps, für die GDI-DPI-Skalierung aktiviert werden soll. Geben Sie beispielsweise `filename.exe` oder `%ProgramFiles%\Path\Filename.exe` ein.

  GDI-DPI-Skalierung ist für alle Legacyanwendungen in der Liste aktiviert.

- **GDI-Skalierung für Apps deaktivieren**: **Hinzufügen** von Legacy-Apps, für die GDI-DPI-Skalierung deaktiviert werden soll. Geben Sie beispielsweise `filename.exe` oder `%ProgramFiles%\Path\Filename.exe` ein.

  GDI-DPI-Skalierung ist für alle Legacyanwendungen in der Liste deaktiviert.

Sie können auch eine CSV-Datei mit der Liste der Apps **importieren**.

## <a name="general"></a>Allgemein

Diese Einstellungen verwenden den [Benutzeroberflächenrichtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience), der auch die unterstützten Windows-Editionen auflistet. 

- **Bildschirmaufnahme** (nur Mobilgeräte): **Blockieren** verhindert, dass Benutzer Screenshots auf dem Gerät abrufen können. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **Kopieren und einfügen (nur Mobilgeräte)** : **Blockieren** verhindert, dass Endbenutzer Kopieren und Einfügen für Apps auf dem Gerät verwenden können. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **Manuelles Aufhebung der Registrierung**: **Blockieren** verhindert, dass Benutzer das Arbeitsplatzkonto über die Arbeitsplatz-Systemsteuerung auf dem Gerät löschen können. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.

  Diese Richtlinieneinstellung wird nicht angewendet, wenn der Computer mit Azure Active Directory (Azure AD) verknüpft ist und die automatische Registrierung aktiviert ist.

- **Manuelle Installation von Stammzertifikaten (nur Mobilgeräte)** : **Blockieren** hindert den Benutzer daran, Stammzertifikate und CAP-Zwischenzertifikate manuell zu installieren. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **Kamera**: **Blockieren** verhindert, dass Endbenutzer die Kamera auf dem Gerät verwenden können. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **OneDrive-Dateisynchronisierung**: **Blockieren** hindert den Endbenutzer daran, Dateien vom Gerät mit OneDrive zu synchronisieren. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **Wechselmedien**: **Blockieren** verhindert, dass Benutzer externe Speichergeräte wie SD-Karten mit dem Gerät verwenden können. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **GeoLocation**: **Blockieren** verhindert, dass Endbenutzer Ortungsdienste auf dem Gerät aktivieren können. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **Internetfreigabe**: **Blockieren** verhindert die gemeinsame Nutzung der Internetverbindung auf dem Gerät. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **Zurücksetzung des Telefons**: **Blockieren** verhindert, dass Benutzer das Gerät zurücksetzen oder eine Zurücksetzung auf die Werkseinstellungen ausführen können. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **USB-Verbindung**: **Blockieren** verhindert den Zugriff auf externe Speichergeräte über eine USB-Verbindung des Geräts. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig. Der Ladevorgang über USB ist von dieser Einstellung nicht betroffen.
- **AntiTheft-Modus** (nur Mobilgeräte): **Blockieren** verhindert, dass Endbenutzer die Einstellung für den AntiTheft-Modus auf dem Gerät auswählen können. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **Cortana**: **Blockieren** deaktiviert den Sprach-Assistenten Cortana auf dem Gerät. Wenn Cortana deaktiviert ist, können Benutzer trotzdem suchen, um Elemente auf dem Gerät zu finden. **Nicht konfiguriert** (Standard) lässt Cortana zu.
- **Sprachaufzeichnung** (nur Mobilgeräte): **Blockieren** verhindert, dass Endbenutzer die Sprachaufzeichnung auf dem Gerät verwenden können. **Nicht konfiguriert** (Standard) ermöglicht die Verwendung der Sprachaufzeichnung für Apps.
- **Änderung des Gerätenamens** (nur Mobilgeräte): **Blockieren** verhindert, dass Benutzer den Namen des Geräts ändern können. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **Bereitstellungspakete hinzufügen**: **Blockieren** verhindert, dass der Laufzeitkonfigurations-Agent Bereitstellungspakete auf dem Gerät installieren kann. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **Bereitstellungspakete entfernen**: **Blockieren** verhindert, dass der Laufzeitkonfigurations-Agent Bereitstellungspakete vom Gerät entfernen kann. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **Geräteerkennung**: **Blockieren** verhindert, dass ein Gerät von anderen Geräten erkannt wird. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **Programmumschaltung** (nur mobile Geräte): **Blockieren** verhindert die Programmumschaltung auf dem Gerät. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature zulässig.
- **Dialogfeld bei SIM-Kartenfehler (nur mobile Geräte)** : **Blockiert** die Anzeige einer Fehlermeldung auf dem Gerät, wenn keine SIM-Karte erkannt wird. **Nicht konfiguriert** (Standard) zeigt die Fehlermeldungen an.
- **Ink-Arbeitsbereich**: Wählen Sie aus, ob und wie Benutzer Zugriff auf den Ink-Arbeitsbereich besitzen. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Sperre): Aktiviert den Ink-Arbeitsbereich, und der Benutzer kann ihn über den Sperrbildschirm verwenden.
  - **Für Sperrbildschirm deaktiviert**: Der Ink-Arbeitsbereich ist aktiviert, und die Funktion ist aktiviert. Aber der Benutzer kann nicht über den Sperrbildschirm darauf zugreifen.
  - **Deaktiviert**: Der Zugriff auf den Ink-Arbeitsbereich ist deaktiviert. Die Funktion ist deaktiviert.

  [WindowsInkWorkspace-Richtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)

- **Automatische erneute Bereitstellung**: Wählen Sie **Zulassen** aus, damit Benutzer mit Administratorrechten alle Benutzerdaten und -einstellungen über **STRG+Windows+R** vom Sperrbildschirm des Geräts aus löschen können. Das Gerät wird automatisch neu konfiguriert und bei der Verwaltung erneut registriert. In der Standardeinstellung **Nicht konfiguriert** ist dieses Feature deaktiviert.
- **Benutzer müssen während der Geräteeinrichtung eine Netzwerkverbindung herstellen**: Wählen Sie **Erforderlich** aus, damit das Gerät eine Verbindung mit einem Netzwerk herstellt, bevor das Setup von Windows über die Seite „Netzwerk“ hinaus fortgesetzt werden kann. **Nicht konfiguriert** (Standard) ermöglicht Benutzern das Hinausgehen über die Seite „Netzwerk“ auch dann, wenn keine Verbindung mit einem Netzwerk besteht.

  Die Einstellung wird beim nächsten Zurücksetzen des Geräts wirksam. Wie jede andere Intune-Konfiguration muss das Gerät von Intune registriert und verwaltet werden, um Konfigurationseinstellungen zu empfangen. Sobald es jedoch registriert ist und Richtlinien empfängt, erzwingt das Zurücksetzen des Geräts die Einstellung während des nächsten Setups von Windows.

- **Direkter Speicherzugriff**: Bei Festlegung auf **Blockieren** wird der direkte Speicherzugriff (Direct Memory Access, DMA) für alle Hot-Plug-PCI-Downstreamanschlüsse verhindert, bis sich ein Benutzer bei Windows anmeldet. **Aktiviert** (Standardeinstellung) ermöglicht den Zugriff auf DMA selbst dann, wenn ein Benutzer nicht angemeldet ist.

  CSP: [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **Prozesse über den Task-Manager beenden**: Diese Einstellung bestimmt, ob der Task-Manager von anderen Benutzern als Administratoren zum Beenden von Tasks verwendet werden darf. Die Option **Blockieren** verhindert, dass Standardbenutzer (also keine Administratoren) den Task-Manager zum Beenden von Prozessen oder Tasks auf dem Gerät verwenden. Über die Option **Nicht konfiguriert** (Standard) erhalten Standardbenutzer die Erlaubnis, Prozesse oder Tasks mithilfe des Task-Managers zu beenden.

## <a name="locked-screen-experience"></a>Gesperrter Bildschirm

- **Info-Center-Benachrichtigungen (nur Mobilgeräte)** : **Blockieren** verhindert die Anzeige von Info-Center-Benachrichtigungen auf dem Gerätesperrbildschirm. **Nicht konfiguriert** (Standard) ermöglicht dem Benutzer die Auswahl, welche Apps Benachrichtigungen auf dem Sperrbildschirm anzeigen können.

  [AboveLock/AllowActionCenterNotifications-CSP](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#AboveLock_AllowActionCenterNotifications)

- **URL zu Bild für gesperrten Bildschirm (nur Desktop)** : Geben Sie die URL zu einem Bild im JPG-, JPEG oder PNG-Format ein, das als Hintergrund für den Windows-Sperrbildschirm verwendet wird. Geben Sie beispielsweise `https://contoso.com/image.png` ein. Diese Einstellung sperrt das Bild und kann nicht nachträglich geändert werden.
- **Vom Benutzer konfigurierbares Bildschirmtimeout (nur Mobilgeräte)** : **Zulassen** ermöglicht Benutzern das Konfigurieren des Bildschirmtimeouts. **Nicht konfiguriert** (Standard) stellt Benutzern diese Option nicht zur Verfügung.

  [DeviceLock/AllowScreenTimeoutWhileLockedUserConfig-CSP](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#DeviceLock_AllowScreenTimeoutWhileLockedUserConfig)

- **Cortana auf Sperrbildschirm (nur Desktop)** : **Blockieren** verhindert, dass der Benutzer mit Cortana interagiert, wenn auf dem Gerät der Sperrbildschirm zu sehen ist. **Nicht konfiguriert** (Standard) lässt die Interaktion mit Cortana zu.

  [AboveLock/AllowCortanaAboveLock-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowcortanaabovelock)

- **Popupbenachrichtigungen auf Sperrbildschirm**: **Blockieren** verhindert, dass Popupbenachrichtigungen auf dem Gerätesperrbildschirm des Geräts angezeigt werden. **Nicht konfiguriert** (Standard) lässt diese Benachrichtigungen zu.

  [AboveLock/AllowToasts-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowtoasts)

- **Bildschirmtimeout (nur Mobilgeräte)** : Legt die Dauer (in Sekunden) zwischen der Bildschirmsperre und dem Abschalten des Bildschirms fest. Die Werte 11 bis 1.800 werden unterstützt. Geben Sie z.B. `300` ein, um diesen Timeoutwert auf 5 Minuten festzulegen.

  [DeviceLock/ScreenTimeoutWhileLocked-CSP](https://msdn.microsoft.com/ie/dn904962(v=vs.94)#DeviceLock_ScreenTimeoutWhileLocked)

## <a name="messaging"></a>Messaging

Diese Einstellungen verwenden den [Messagingrichtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-messaging), der auch die unterstützten Windows-Editionen auflistet.

- **Nachrichtensynchronisierung (nur Mobilgeräte)** : **Blockieren** deaktiviert die Sicherung und Wiederherstellung von SMS-Nachrichten sowie die Synchronisierung zwischen Windows-Geräten. Die Deaktivierung verhindert, dass Informationen auf Servern gespeichert werden, deren Kontrolle außerhalb der Organisation liegt. **Nicht konfiguriert** (Standard) ermöglicht es Benutzern, diese Einstellungen zu ändern und ihre Nachrichten zu synchronisieren.
- **MMS (nur mobil)** : **Blockieren** deaktiviert die Funktion zum Senden/Empfangen von MMS auf dem Gerät. Verwenden Sie diese Richtlinie für Unternehmen, um MMS im Rahmen der Überwachungs- oder Verwaltungsanforderungen auf Geräten zu deaktivieren. **Nicht konfiguriert** (Standard) lässt das Senden und Empfangen von MMS zu.
- **RCS (nur mobil)** : **Blockieren** deaktiviert die Funktion für RCS-Sendevorgänge/Empfangsvorgänge (Rich Communication Services) auf dem Gerät. Verwenden Sie diese Richtlinie für Unternehmen, um RCS im Rahmen der Überwachungs- oder Verwaltungsanforderungen auf Geräten zu deaktivieren. **Nicht konfiguriert** (Standard) lässt das Senden und Empfangen von RCS zu.

## <a name="microsoft-edge-browser"></a>Microsoft Edge-Browser

Diese Einstellungen verwenden den [Browserrichtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser), der auch die unterstützten Windows-Editionen auflistet.

### <a name="use-microsoft-edge-kiosk-mode"></a>Verwenden des Microsoft Edge-Kioskmodus

Die verfügbaren Einstellungen hängen davon ab, was Sie wählen. Folgende Optionen sind verfügbar:

- **Nein** (Standard): Microsoft Edge wird nicht im Kioskmodus ausgeführt. Sie können alle Microsoft Edge-Einstellungen ändern und konfigurieren.
- **Digitale/interaktive Beschilderung (Kiosk mit einzelner App)** : Filtert Microsoft Edge-Einstellungen, die für „Digitale/interaktive Beschilderung“ in Frage kommen. Der Kioskmodus von Microsoft Edge ist nur für die Verwendung auf Windows 10-Kiosks mit einzelner App vorgesehen. Wählen Sie diese Einstellung, um eine URL im Vollbildmodus zu öffnen und nur den Inhalt dieser Website anzuzeigen. Unter [Einrichten digitaler Beschilderungen](https://docs.microsoft.com/windows/configuration/setup-digital-signage) finden weitere Informationen zu dieser Funktion.
- **Öffentliches Browsen (InPrivate, Kiosk mit einzelner App)** : Filtert Microsoft Edge-Einstellungen, die für „Öffentliches Browsen (InPrivate)“ in Frage kommen. Der Kioskmodus von Microsoft Edge ist für die Verwendung auf Windows 10-Kiosks mit einzelner App vorgesehen. Führt eine Version von Microsoft Edge mit mehreren Registerkarten aus.
- **Normalmodus (Kiosk mit mehreren Apps)** : Filtert Microsoft Edge-Einstellungen, die für den normalen Kioskmodus von Microsoft Edge gelten. Führt eine Vollversion von Microsoft Edge mit sämtlichen Funktionen für das Browsen aus.
- **Öffentliches Browsen (Kiosk mit mehreren Apps)** : Filtert Microsoft Edge-Einstellungen, die für das öffentliche Browsen auf einem Windows 10-Kiosk mit mehreren Apps gelten.  Führt eine Version von Microsoft Edge-InPrivate mit mehreren Registerkarten aus.

> [!TIP]
> Weitere Informationen zur Aufgabe dieser Optionen finden Sie unter [Konfigurationstypen für den Microsoft Edge-Kioskmodus](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

Dieses Geräteeinschränkungsprofil steht in direktem Zusammenhang mit dem Kioskprofil, das Sie mithilfe der [Windows-Kioskeinstellungen](kiosk-settings-windows.md) erstellen. Zusammenfassung:

1. Erstellen Sie das Profil [Windows-Kioskeinstellungen](kiosk-settings-windows.md), um das Gerät im Kioskmodus auszuführen. Wählen Sie Microsoft Edge als Anwendung aus, und legen Sie den Microsoft Edge-Kioskmodus im Profil „Kiosk“ fest.
2. Erstellen Sie das in diesem Artikel beschriebene Profil für Geräteeinschränkungen, und konfigurieren Sie spezifische Funktionen und Einstellungen, die in Microsoft Edge zulässig sind. Stellen Sie sicher, dass Sie den gleichen Microsoft Edge-Kioskmodustyp wie in Ihrem Kioskprofil wählen ([Windows-Kioskeinstellungen](kiosk-settings-windows.md)). 

    Unter [Unterstützte Einstellungen für den Kioskmodus ](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode) finden Sie hilfreiche Informationen.

> [!IMPORTANT] 
> Achten Sie darauf, dass dieses Microsoft Edge-Profil den gleichen Geräten wie Ihr Kioskprofil zugewiesen wird ([Windows-Kioskeinstellungen](kiosk-settings-windows.md)).

[CSP: ConfigureKioskMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>Startoberfläche

- **Microsoft Edge starten mit**: Wählen Sie aus, welche Seiten beim Starten von Microsoft Edge geöffnet werden. Folgende Optionen sind verfügbar:
  - **Benutzerdefinierte Startseiten**: Geben Sie die Startseiten ein, z.B. `http://www.contoso.com`. Microsoft Edge lädt die Startseiten, die Sie eingeben.
  - **Neue Registerkartenseite**: Microsoft Edge lädt, was in der Einstellung **URL für neue Registerkartenseite** eingegeben wird.
  - **Seite der letzten Sitzung**: Microsoft Edge lädt die Seite der letzten Sitzung.
  - **Startseiten in lokalen App-Einstellungen**: Microsoft Edge beginnt mit der vom Betriebssystem definierten Standardstartseite.

- **Benutzer kann die Startseiten ändern**: **Ja** (Standard) ermöglicht Benutzern das Ändern der Startseiten. Administratoren können mithilfe der `EdgeHomepageUrls` die Startseiten eingeben, die Benutzern standardmäßig beim Öffnen von Microsoft Edge angezeigt werden. **Nein** hindert Benutzer daran, Änderungen an den Startseiten vorzunehmen.
- **Webinhalte auf neuer Registerkarte zulassen**: Bei Festlegung auf **Ja** (Standard) öffnet Microsoft Edge die URL, die in der Einstellung **URL der neuen Registerkarte** eingegeben wurde. Wenn die Einstellung **URL der neuen Registerkarte** leer ist, öffnet Microsoft Edge die neue Registerkartenseite, die in den Microsoft Edge-Einstellungen aufgeführt wird. Benutzer können diese Angabe ändern. Bei Festlegung auf **Nein** öffnet Microsoft Edge eine neue Registerkarte mit einer leeren Seite. Benutzer können dies nicht ändern.
- **URL der neuen Registerkarte**: Geben Sie die URL ein, die auf der neuen Registerkartenseite geöffnet werden soll. Geben Sie beispielsweise `https://www.bing.com` oder `https://www.contoso.com` ein.

- **Startschaltfläche**: Wählen Sie aus, was geschieht, wenn die Startschaltfläche ausgewählt wird. Folgende Optionen sind verfügbar:
  - **Startseiten**: Öffnet die Option, die Sie für die Einstellung **Microsoft Edge starten mit** ausgewählt haben.
  - **Neue Registerkartenseite**: Öffnet die URL, die Sie in der Einstellung **URL der neuen Registerkarte** eingegeben haben.
  - **URL der Startschaltfläche**: Geben Sie die zu öffnende URL ein. Geben Sie beispielsweise `https://www.bing.com` oder `https://www.contoso.com` ein.
  - **Startschaltfläche ausblenden**: Blendet die Startschaltfläche aus.
- **Benutzer das Ändern der Startschaltfläche gestatten**: **Ja** ermöglicht Benutzern das Ändern der Startschaltfläche. Die Änderungen des Benutzers setzen Administratoreinstellungen für die Startschaltfläche außer Kraft. **Nein** (Standard) verhindert, dass Benutzer ändern können, wie der Administrator die Startschaltfläche konfiguriert hat.
- **Willkommensseite anzeigen (nur Mobilgeräte)** : **Ja** (Standard) zeigt die Willkommensseite zur ersten Verwendung in Microsoft Edge an. **Nein** verhindert, dass die Einführungsseite bei der ersten Ausführung von Microsoft Edge angezeigt wird. Diese Funktion ermöglicht Unternehmen (z.B. Organisationen, die in Nullemissionskonfigurationen registriert sind), diese Seite zu blockieren.
- **Speicherort für URL-Liste für Windows-Willkommensseite** (nur Windows 10 Mobile): Geben Sie die URL ein, die auf die XML-Datei verweist, die die URL(s) für die Seite enthält, die bei der ersten Ausführung angezeigt wird. Geben Sie beispielsweise `https://www.contoso.com/sites.xml` ein.

- **Browser nach Leerlaufzeit aktualisieren:** : Geben Sie die Anzahl der Leerlaufminuten bis zur Aktualisierung des Browsers ein (von 0-1440 Minuten). Der Standardwert ist `5` Minuten. Bei Festlegung auf `0` wird der Browser nach einem Leerlauf nicht aktualisiert.

  Diese Einstellung ist nur bei Ausführung im Modus [Öffentliches Browsen (InPrivate, Kiosk mit einzelner App)](#use-microsoft-edge-kiosk-mode) verfügbar.

- **Popups zulassen** (nur Desktop): **Ja** (Standard) lässt Popups im Webbrowser zu. **Nein** verhindert Popupfenster im Browser.
- **Datenverkehr im Intranet an Internet Explorer senden** (nur Desktop): **Ja** erlaubt Benutzern, Intranetsites in Internet Explorer anstatt in Microsoft Edge zu öffnen. Diese Einstellung dient der Abwärtskompatibilität. **Nein** ermöglicht Benutzern die Verwendung von Microsoft Edge.
- **Speicherort der Websiteliste für den Unternehmensmodus** (nur Desktop):Geben Sie die URL ein, die auf die XML-Datei verweist, die eine Liste der Websites enthält, die im Unternehmensmodus geöffnet werden. Benutzer können diese Liste nicht ändern. Geben Sie beispielsweise `https://www.contoso.com/sites.xml` ein.
- **Meldung beim Öffnen von Websites in Internet Explorer**: Verwenden Sie diese Einstellung, um zu konfigurieren, dass Microsoft Edge eine Benachrichtigung anzeigt, bevor eine Website in Internet Explorer 11 geöffnet wird. Folgende Optionen sind verfügbar:
  - **Meldung nicht anzeigen**: Das Standardverhalten des Betriebssystems wird verwendet, d.h. möglicherweise wird keine Meldung angezeigt.
  - **Meldung anzeigen, dass Website in Internet Explorer 11 geöffnet wird** : Die Meldung beim Öffnen von Websites in Internet Explorer anzeigen. Websites werden im Internet Explorer geöffnet. 
  - **Meldung mit Option zum Öffnen von Websites in Microsoft Edge anzeigen**: Die Meldung beim Öffnen von Websites in Microsoft Edge anzeigen. Die Meldung enthält einen Link **Weiter in Microsoft Edge**, damit Benutzer Microsoft Edge anstelle von Internet Explorer auswählen können.

  > [!IMPORTANT]
  > Für diese Einstellung müssen Sie die Einstellung **Unternehmensmodus-Websiteliste** konfigurieren, die Einstellung **Intranetdatenverkehr an Internet Explorer senden** oder beide Einstellungen aktivieren.

- **Microsoft-Kompatibilitätsliste zulassen**: **Ja** (Standard) ermöglicht die Verwendung einer Microsoft-Kompatibilitätsliste. **Nein** verhindert die Microsoft-Kompatibilitätsliste in Microsoft Edge. Mithilfe dieser Liste von Microsoft kann Microsoft Edge Websites mit bekannten Kompatibilitätsproblemen ordnungsgemäß anzeigen.
- **Startseiten und neue Registerkartenseite vorab laden**: **Ja** (Standard) verwendet das Standardverhalten des Betriebssystems, das diese Seiten möglicherweise vorab lädt. Das Vorabladen minimiert die Zeit zum Starten von Microsoft Edge und Laden neuer Registerkarten. **Nein** verhindert, dass Microsoft Edge Startseiten und die neue Registerkartenseite vorab lädt.
- **Startseiten und neue Registerkartenseite vorab starten**: **Ja** (Standard) verwendet das Standardverhalten des Betriebssystems, das diese Seiten möglicherweise vorab startet. Vorabstarten steigert die Leistung von Microsoft Edge und minimiert die zum Starten von Microsoft Edge erforderliche Zeit. **Nein** verhindert, dass Microsoft Edge Startseiten und die neue Registerkartenseite vorab startet.

### <a name="favorites-and-search"></a>Favoriten und Suche

- **Favoritenleiste anzeigen**: Wählen Sie aus, was mit der Favoritenleiste auf einer beliebigen Seite von Microsoft Edge geschehen soll. Folgende Optionen sind verfügbar:
  - **Auf Start- und neuen Registerkartenseiten**: Zeigt die Favoritenleiste beim Starten von Microsoft Edge und auf allen Registerkartenseiten an. Endbenutzer können diese Einstellung ändern.
  - **Auf allen Seiten**: Zeigt die Favoritenleiste auf allen Seiten an. Endbenutzer können diese Einstellung nicht ändern.
  - **Ausgeblendet**: Blendet die Favoritenleiste auf allen Seiten aus. Endbenutzer können diese Einstellung nicht ändern.
- **Änderungen an Favoriten zulassen**: **Ja** (Standard) verwendet die Standardeinstellung des Betriebssystems, die Benutzern das Ändern der Liste ermöglicht. **Nein** verhindert, dass Benutzer die Favoritenliste hinzufügen, importieren, sortieren oder bearbeiten können.
  - **Favoritenliste**: Fügt eine Liste von URLs der Favoritendatei hinzu. Fügen Sie z.B. `http://contoso.com/favorites.html` hinzu.
- **Favoriten zwischen Microsoft-Browsern synchronisieren (nur Desktop)** : **Ja** erzwingt, dass Windows die Favoriten zwischen Internet Explorer und Microsoft Edge synchronisiert. Favoriten betreffende Hinzufügungen, Löschungen, Änderungen und Anordnungsänderungen werden zwischen Browsern freigegeben.  **Nein** (Standard) verwendet den Betriebssystemstandard, sodass Benutzer möglicherweise die Synchronisierung von Favoriten zwischen den Browsern auswählen können.
- **Standardsuch-Engine**: Wählen Sie die auf dem Gerät zu verwendende Standardsuch-Engine aus. Endbenutzer können diesen Wert jederzeit ändern. Folgende Optionen sind verfügbar:
  - Suchmodul in Microsoft Edge-Clienteinstellungen
  - Bing
  - Google
  - Yahoo
  - Benutzerdefinierter Wert: Geben Sie in **OpenSearch-XML-URL** eine HTTPS-URL mit der XML-Datei ein, die mindestens den Kurznamen und die URL für das Suchmodul enthält. Geben Sie beispielsweise `https://www.contoso.com/opensearch.xml` ein.
- **Suchvorschläge anzeigen**: **Ja** (Standard) ermöglicht dem Suchmodul, Websites während der Eingabe von Suchausdrücken in der Adressleiste vorzuschlagen. **Nein** verhindert die Verwendung dieser Funktion.
- **Änderungen an der Suchmaschine zulassen**: **Ja** (Standard) ermöglicht es Benutzern, neue Suchmaschinen hinzuzufügen oder die Standardsuchmaschine in Microsoft Edge zu ändern. Wählen Sie **Nein**, um zu verhindern, dass Benutzer die Suchmaschine anpassen.

  Diese Einstellung ist nur bei Ausführung im [Normalmodus (Kiosk mit mehreren Apps)](#use-microsoft-edge-kiosk-mode) verfügbar.

### <a name="privacy-and-security"></a>Datenschutz und Sicherheit

- **InPrivate-Browsen zulassen**: **Ja** (Standard) ermöglicht das InPrivate-Browsen in Microsoft Edge. Nach dem Schließen alle InPrivate-Registerkarten löscht Microsoft Edge die Browserdaten vom Gerät. **Nein** hindert den Endbenutzer daran, InPrivate-Browsersitzungen zu öffnen.
- **Browserverlauf speichern**: **Ja** (Standard) lässt zu, dass der Browserverlauf in Microsoft Edge gespeichert wird. **Nein** verhindert, dass der Browserverlauf gespeichert wird.
- **Browserdaten beim Beenden löschen (nur Desktop)** : **Ja** löscht den Verlauf und die Browserdaten, wenn der Benutzer Microsoft Edge beendet. **Nein** (Standard) verwendet den Betriebssystemstandard, d.h. die Browserdaten werden möglicherweise zwischengespeichert.
- **Browsereinstellungen zwischen Benutzergeräten synchronisieren**: Wählen Sie aus, wie die Browsereinstellungen zwischen Geräten synchronisiert werden sollen. Folgende Optionen sind verfügbar:
  - **Zulassen**: Zulassen der Synchronisierung von Microsoft Edge-Browsereinstellungen zwischen Geräten des Benutzers.
  - **Außerkraftsetzung durch Benutzer blockieren und aktivieren**: Blockieren der Synchronisierung von Microsoft Edge-Browsereinstellungen zwischen Geräten des Benutzers. Benutzer können diese Einstellung überschreiben.
  - **Blockieren**: Blockieren der Synchronisierung von Microsoft Edge-Browsereinstellungen zwischen Geräten von Benutzern. Benutzer können diese Einstellung nicht überschreiben.

Wenn „Außerkraftsetzung durch Benutzer blockieren und aktivieren“ ausgewählt ist, kann der Benutzer die Administratorfestlegung überschreiben.

- **Kennwort-Manager zulassen**: **Ja** (Standard) ermöglicht es, dass Microsoft Edge automatisch den Kennwort-Manager verwendet. Dies ermöglicht es Benutzern, Kennwörter auf dem Gerät zu speichern und zu verwalten. **Nein** verhindert, dass Microsoft Edge den Kennwort-Manager verwendet.
- **Cookies**: Wählen Sie aus, wie Cookies im Webbrowser behandelt werden. Folgende Optionen sind verfügbar:
  - **Zulassen**: Ermöglicht das Speichern von Cookies auf dem Gerät.
  - **Alle Cookies blockieren**: Cookies werden nicht auf dem Gerät gespeichert.
  - **Nur Cookies von Drittanbietern blockieren**: Cookies von Drittanbietern oder Partnern werden nicht auf dem Gerät gespeichert.
- **AutoAusfüllen in Formularen zulassen**: **Ja** (Standard) ermöglicht Benutzern das Ändern der Einstellungen für automatische Vervollständigung im Browser und automatisches Auffüllen der Felder eines Formulars mit Daten. **Nein** deaktiviert das Feature „AutoAusfüllen“ in Microsoft Edge.
- **DNT-Kopfzeilen senden**: **Ja** sendet DNT-Kopfzeilen an Websites, die Nachverfolgungsinformationen anfordern (empfohlen). **Nein** (Standard) sendet keine Header, die Websites das Nachverfolgen von Benutzern ermöglichen. Benutzer können diese Einstellung konfigurieren.
- **WebRTC-LocalHost-IP-Adresse anzeigen**: **Ja** (Standard) ermöglicht die Anzeige der Localhost-IP-Adressen von Benutzern bei Telefonaten mit diesem Protokoll. **Nein** verhindert, dass die Localhost-IP-Adresse des Benutzers angezeigt wird. 
- **Datensammlung für Livekacheln zulassen**: **Ja** (Standard) ermöglicht es Microsoft Edge, Informationen von Livekacheln zu erfassen, die an das Startmenü angeheftet sind. **Nein** verhindert, dass diese Informationen erfasst werden. Dies kann für Benutzer zu eingeschränkten Funktionen führen.
- **Benutzer kann Zertifikatfehler außer Kraft setzen**: **Ja** (Standard) ermöglicht Benutzern den Zugriff auf Websites, die SSL-/TLS-Fehler (Secure Sockets Layer/Transport Layer Security) enthalten. **Nein** (für erhöhte Sicherheit empfohlen) verhindert, dass Benutzer auf Websites mit SSL- oder TLS-Fehlern zugreifen können.

### <a name="additional"></a>Zusätzliche Informationen

- **Microsoft Edge-Browser zulassen** (nur Mobilgeräte): **Ja** lässt die Verwendung des Microsoft Edge-Webbrowsers auf dem Gerät zu. **Nein** verhindert die Verwendung von Microsoft Edge auf dem Gerät. Wenn Sie **Nein** auswählen, gelten die anderen individuellen Einstellungen nur für den Desktop.
- **Adressleisten-Dropdownliste zulassen**: **Ja** (Standard) ermöglicht es Microsoft Edge, die Adressleisten-Dropdownliste mit einer Liste der Vorschläge anzuzeigen. **Nein** verhindert, dass Microsoft Edge bei der Eingabe weiterhin eine Liste mit Vorschlägen in einer Dropdownliste anzeigt. Wenn Sie diese Einstellung auf **Nein** festlegen:
  - Kann die zwischen Microsoft Edge und Microsoft-Diensten genutzte Netzwerkbandbreite minimiert werden.
  - Deaktivieren Sie die **Such- und Websitevorschläge während der Eingabe anzeigen** in „Microsoft Edge > Einstellungen“.
- **Vollbildmodus zulassen**: **Ja** (Standard) ermöglicht es Microsoft Edge, den Vollbildmodus zu verwenden, der nur die Webinhalte anzeigt und die Benutzeroberfläche von Microsoft Edge ausblendet. **Nein** verhindert den Vollbildmodus in Microsoft Edge.
- **Seite „Informationen zu Flags“ zulassen**: **Ja** (Standard) verwendet den Betriebssystemstandard, sodass Benutzer auf die `about:flags`-Seite zugreifen können. Die `about:flags`-Seite ermöglicht Benutzern das Ändern der Entwicklereinstellungen und das Aktivieren experimenteller Features. **Nein** verhindert, dass Benutzer auf die `about:flags`-Seite in Microsoft Edge zugreifen können.
- **Entwicklertools zulassen**: **Ja** (Standard) ermöglicht Benutzern standardmäßig die Verwendung der F12-Entwicklertools zum Erstellen und Debuggen von Webseiten. **Nein** verhindert, dass Benutzer die F12-Entwicklertools verwenden können.
- **Javascript zulassen**: **Ja** (Standard) lässt die Ausführung von Skripts (z.B. JavaScript) im Microsoft Edge-Browser zu. **Nein** verhindert, dass Java-Skripts im Browser ausgeführt werden.
- **Benutzer kann Erweiterungen installieren**: **Ja** (Standard) lässt zu, dass Endbenutzer Microsoft Edge-Erweiterungen auf dem Gerät installieren. **Nein** verhindert die Installation.
- **Querladen von Entwicklererweiterungen zulassen**: **Ja** (Standard) verwendet den Betriebssystemtandard, der Querladen möglicherweise zulässt. Das Querladen installiert nicht überprüfte Erweiterungen und führt sie aus. **Nein** verhindert, dass Microsoft Edge mit dem Feature **Erweiterungen laden** Erweiterungen querladen kann. Die Angabe „Nein“ verhindert nicht das Querladen von Erweiterungen mit anderen Methoden, z.B. mit PowerShell.
- **Erforderliche Erweiterungen**: Wählen Sie aus, welche Erweiterungen in Microsoft Edge nicht von Endbenutzern deaktiviert werden können. Geben Sie die Paketfamiliennamen ein, und wählen Sie **Hinzufügen** aus. [Paketfamiliennamen (PFN) suchen](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) stellt einige hilfreiche Informationen bereit.

  Sie können auch eine CSV-Datei **Importieren**, die die Paketfamiliennamen enthält. Oder **exportieren** Sie die Paketfamiliennamen, die Sie eingeben.

## <a name="network-proxy"></a>Netzwerkproxy

Diese Einstellungen verwenden den [NetworkProxy-Richtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp), der auch die unterstützten Windows-Editionen auflistet.

- **Proxyeinstellungen automatisch erkennen**: **Blockieren** deaktiviert, dass das Gerät ein Skript für die automatische Proxykonfiguration (PAC-Skript) erkennt. **Nicht konfiguriert** (Standard) aktiviert diese Einstellung. Bei Aktivierung versucht das Gerät, den Pfad zu einem PAC-Skript zu finden.
- **Proxyskript verwenden**: Wählen Sie **Zulassen** aus, um einen Pfad zu Ihrem PAC-Skript zum Konfigurieren des Proxyservers anzugeben. **Nicht konfiguriert** (Standard) lässt nicht zu, dass Sie die URL zu einem PAC-Skript eingeben.
  - **Adress-URL für Setupskript**: Geben Sie die URL eines PAC-Skripts an, das Sie verwenden möchten, um den Proxyserver zu konfigurieren.
- **Manuellen Proxyserver verwenden**: Wählen Sie **Zulassen** aus, um den Namen oder die IP-Adresse und die TCP-Portnummer eines Proxyservers manuell einzugeben. **Nicht konfiguriert** (Standard) lässt die manuelle Eingabe von Details des Proxyservers nicht zu.
  - **Adresse**: Geben Sie den Namen oder die IP-Adresse des Proxyservers an.
  - **Portnummer**: Geben Sie die Portnummer Ihres Proxyservers ein.
  - **Proxyausnahmen**: Geben Sie URLs an, die den Proxyserver nicht verwenden dürfen. Trennen Sie die einzelnen Elemente durch Semikola.
  - **Proxyserver für lokale Adresse umgehen**: **Nicht konfiguriert** (Standard) verhindert die Verwendung eines Proxyservers für lokale Adressen in Ihrem Intranet. **Zulassen** verwendet einen Proxyserver für lokale Adressen.

## <a name="password"></a>Kennwort

Diese Einstellungen verwenden den [DeviceLock-Richtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock), der auch die unterstützten Windows-Editionen auflistet.

- **Kennwort**: **Anfordern** der Eingabe eines Kennworts durch den Endbenutzer, um auf das Gerät zugreifen zu können. **Nicht konfiguriert** (Standard) ermöglicht den Zugriff auf das Gerät ohne ein Kennwort. Gilt nur für lokale Konten. Domänen Konto Kennwörter bleiben durch Active Directory (AD) und Azure AD konfiguriert.

  - **Erforderlicher Kennworttyp**: Wählen Sie den Kennworttyp aus. Folgende Optionen sind verfügbar:
    - **Nicht konfiguriert**: Das Kennwort kann Zahlen und Buchstaben enthalten.
    - **Numerisch**: Kennwort darf nur aus Zahlen bestehen.
    - **Alphanumerisch**: Das Kennwort muss aus einer Kombination aus Ziffern und Buchstaben bestehen.
  - **Minimale Kennwortlänge**: Geben Sie die minimale Anzahl der erforderlichen Zeichen ein (zwischen 4 und 16). Geben Sie z.B. `6` ein, um ein mindestens sechs Zeichen langes Kennwort zu verlangen.
  
    > [!IMPORTANT]
    > Wenn die Kennwortanforderung auf einem Windows-Desktop geändert wird, wirkt sich das auf die nächste Anmeldung der Benutzer aus, da das Gerät in diesem Moment aus dem Leerlauf in den aktiven Zustand wechselt. Benutzer mit Kennwörtern, die die Anforderungen erfüllen, werden trotzdem aufgefordert, ihre Kennwörter ändern.
    
  - **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird**: Geben Sie die Anzahl von Authentifizierungsfehlern ein, die zulässig sind, bevor das Gerät zurückgesetzt werden kann (bis zu 11). Die gültige Zahl, die Sie eingeben, hängt von der-Edition ab. [DeviceLock/maxde vicepasswordfailedattempts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts) listet die unterstützten Werte auf. Durch `0` (null) kann die Funktion zum Zurücksetzen des Geräts deaktiviert werden.

    Diese Einstellung besitzt zudem je nach Edition unterschiedliche Auswirkungen. Spezifische Details zu dieser Einstellung finden Sie im [DeviceLock/MaxDevicePasswordFailedAttempts-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts).

  - **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung**: Gebe Sie den Zeitraum der Inaktivität für ein Gerät ein, bevor der Bildschirm gesperrt wird.
  - **Kennwortablauf (Tage)** : Geben Sie den Zeitraum an, nach dem das Kennwort für das Gerät geändert werden muss (zwischen 1 und 365). Geben Sie beispielsweise `90` an, damit das Kennwort nach 90 Tagen abläuft.
  - **Wiederverwendung vorheriger Kennwörter verhindern**: Geben Sie die Anzahl von vorherigen Kennwörtern an, die nicht erneut verwendet werden dürfen (zwischen 1 und 24). Geben Sie z.B. `5` an, damit ein Benutzer sein neues Kennwort nicht auf sein aktuelles Kennwort oder eines seiner vorherigen vier Kennwörter festlegen kann.
  - **Kennwort anfordern, wenn Gerät aus Leerlaufzustand zurückkehrt (Mobile und Holographic)** : Wählen Sie **Erforderlich** aus, damit Benutzer ein Kennwort zum Entsperren des Geräts eingeben müssen, wenn sich dieses im Leerlauf befand. **Nicht konfiguriert** (Standard) erfordert keine PIN bzw. kein Kennwort, wenn das Gerät aus dem Leerlauf fortgesetzt wird.
  - **Einfache Kennwörter:** Legen Sie **Blockieren** fest, damit Benutzer kein einfaches Kennwort wie `1234` oder `1111` erstellen können. Legen Sie diese Option auf **Nicht konfiguriert** (Standard) fest, damit Benutzer Kennwörter wie `1234` oder `1111` erstellen können. Diese Einstellung ermöglicht es auch, die Verwendung von Windows-Bildcodes zu blockieren.
- **Automatische Verschlüsselung bei AADJ**: Die Wahl von **Blockieren** verhindert die automatische BitLocker-Geräteverschlüsselung bei der Vorbereitung des Geräts für die erste Verwendung, wenn das Gerät Azure AD beitritt. **Nicht konfiguriert** (Standard) verwendet die Standardeinstellung des Betriebssystems, die ggf. die Verschlüsselung aktiviert. Weitere Informationen zur [Geräteverschlüsselung mit BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption).

  [CSP: Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **FIPS-Richtlinie (Federal Information Processing Standard)** : Bei Wahl von **Zulassen** wird die FIPS-Richtlinie (Federal Information Processing Standard) verwendet, die in den USA ein bundesgesetzlicher Standard für Verschlüsselung, Hashing und Signatur ist. Bei Wahl von **Nicht konfiguriert** (Standard) gilt die Standardeinstellung des Betriebssystems, die FIPS nicht verwendet.

  [CSP: Cryptography/AllowFipsAlgorithmPolicy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Windows Hello-Geräteauthentifizierung**: Bei Wahl von **Zulassen** wird Benutzern ermöglicht, sich mit einem Windows Hello-Begleitgerät, wie beispielsweise einem Smartphone, Fitnessband oder IoT-Gerät, bei einem Windows 10-Computer anzumelden. Bei Wahl von **Nicht konfiguriert** (Standard) gilt die Standardeinstellung des Betriebssystems, die Windows Hello-Begleitgeräte an der Authentifizierung bei Windows hindern kann.

  [CSP: Authentication/AllowSecondaryAuthenticationDevice](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **Webanmeldung**: Ermöglicht die Unterstützung der Windows-Anmeldung für nicht zu AD FS (Active Directory-Verbunddienste) gehörige Verbundanbieter, wie beispielsweise SAML (Security Assertion Markup Language). SAML verwendet sichere Token, die Benutzern in Webbrowsern einmaliges Anmelden (SSO) ermöglichen. Folgende Optionen sind verfügbar:

  - Bei Wahl von **Nicht konfiguriert** (Standard) wird die Standardeinstellung des Betriebssystems auf dem Gerätverwendet.
  - **Aktiviert**: Der Anbieter für Webanmeldeinformationen ist für die Anmeldung aktiviert.
  - **Deaktiviert**: Der Anbieter für Webanmeldeinformationen ist für die Anmeldung deaktiviert.

  [CSP: Authentifizierung/EnableWebSignIn](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **Bevorzugte Azure AD-Mandantendomäne**: Geben Sie einen in Ihrer Azure AD-Organisation vorhandenen Domänennamen ein. Wenn sich Benutzer bei dieser Domäne anmelden, müssen sie den Domänennamen nicht eingeben. Geben Sie beispielsweise `contoso.com` ein. Benutzer in der Domäne `contoso.com` können sich mit ihrem Benutzernamen (beispielsweise „`abby`“) anstatt mit „`abby@contoso.com`“ anmelden.

  [CSP: Authentication/PreferredAadTenantDomainName](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

## <a name="per-app-privacy-exceptions"></a>App-bezogene Datenschutzausnahmen

Sie können Apps hinzufügen, die ein anderes Datenschutzverhalten aufweisen als das unter „Standarddatenschutz“ definierte Verhalten.

- **Paketname**: App-Paketfamilienname.
- **Name**: Der Name der App.

### <a name="exceptions"></a>Ausnahmen

- **Kontoinformationen**: Legen Sie fest, ob diese App auf den Benutzernamen, das Bild und andere Kontaktinformationen zugreifen darf.
- **Hintergrund-Apps**: Legen Sie fest, ob diese App im Hintergrund ausgeführt werden darf.
- **Kalender**: Legen Sie fest, ob diese App auf den Kalender zugreifen darf.
- **Anrufliste**: Legen Sie fest, ob diese App auf Ihre Anrufliste zugreifen darf.
- **Kamera**: Legen Sie fest, ob diese App auf die Kamera zugreifen darf.
- **Kontakte**: Legen Sie fest, ob diese App auf Kontakte zugreifen darf.
- **E-Mail**: Legen Sie fest, ob diese App auf E-Mails zugreifen und diese versenden darf.
- **Standort**: Legen Sie fest, ob diese App auf Standortinformationen zugreifen darf.
- **Nachrichten**: Legen Sie fest, ob diese App SMS oder MMS-Nachrichten lesen oder senden darf.
- **Mikrofon**: Legen Sie fest, ob diese App das Mikrofon verwenden darf.
- **Bewegung**: Legen Sie fest, ob diese App auf die Gerätebewegungsinformationen zugreifen darf.
- **Benachrichtigungen**: Legen Sie fest, ob diese App auf Benachrichtigungen zugreifen darf.
- **Telefon**: Legen Sie fest, ob diese App auf das Telefon zugreifen darf.
- **Radios**: Einige Apps verwenden Radios (z.B. Bluetooth) auf Ihrem Gerät, um Daten zu senden und zu empfangen, und müssen diese Radios ein- oder ausschalten. Legen Sie fest, ob diese App diese Radios steuern kann.
- **Aufgaben**: Legen Sie fest, ob diese App auf Ihre Aufgaben zugreifen darf.
- **Vertrauenswürdige Geräte:** Legen Sie fest, ob diese App vertrauenswürdige Geräte verwenden kann. Als vertrauenswürdige Geräte wird Hardware angesehen, mit der Sie bereits eine Verbindung hergestellt haben oder die in das Gerät integriert ist. Verwenden Sie z. B. Fernsehgeräte oder Projektoren als vertrauenswürdige Geräte.
- **Feedback und Diagnose**: Legen Sie fest, ob diese App auf Diagnoseinformationen zugreifen darf.
- **Mit Geräten synchronisieren**: Legen Sie fest, ob diese App automatisch Informationen mit Drahtlosgeräten teilen und synchronisieren darf, die nicht explizit mit dem Gerät gekoppelt sind.

## <a name="personalization"></a>Personalization

Diese Einstellungen verwenden den [Personalisierungsrichtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/personalization-csp), der auch die unterstützten Windows-Editionen auflistet.

- **URL zu Desktophintergrundbild (nur Desktop)** : Geben Sie die URL zu einem Bild im JPG-, JPEG oder PNG-Format an, das Sie als Windows-Desktophintergrund verwenden möchten. Benutzer können das Bild nicht ändern. Geben Sie beispielsweise `https://contoso.com/logo.png` ein.

## <a name="printer"></a>Drucker

- **Drucker**: Liste der lokalen Drucker, die hinzugefügt wurden.
- **Standarddrucker**: Festlegen als Standarddrucker.
- **Benutzerzugriff für das Hinzufügen neuer Drucker**: Zulassen oder Blockieren der Verwendung von lokalen Druckern.

## <a name="privacy"></a>Datenschutz

Diese Einstellungen verwenden den [Datenschutzrichtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy), der auch die unterstützten Windows-Editionen auflistet.

- **Eingabepersonalisierung**: **Blockieren** verhindert, dass Benutzer Sprache zum Diktieren verwenden und mit Cortana und anderen Apps sprechen können, die cloudbasierte Microsoft -Spracherkennung verwenden. Die Option ist deaktiviert, und Benutzer können Onlinespracherkennung mithilfe von Einstellungen nicht aktivieren. **Nicht konfiguriert** (Standard) ermöglicht Benutzern die Auswahl. Wenn Sie diese Dienste zulassen, kann Microsoft Sprachdaten erfassen, um den Dienst zu verbessern.
- **Automatisches Akzeptieren der Zustimmungsaufforderung des Benutzers zu Kopplung und Datenschutz**: Wählen Sie **Zulassen** aus, damit Windows beim Ausführen von Apps Benachrichtigungen zur Zustimmung zu Kopplung und Datenschutz automatisch akzeptieren kann. **Nicht konfiguriert** (Standard) verhindert das automatische Akzeptieren des Fensters für die Zustimmung zu Kopplung und Datenschutz beim Öffnen von Apps.
- **Benutzeraktivitäten veröffentlichen**: **Blockieren** Sie diese Einstellung, um geteilte Aktivitäten und die Ermittlungen von kürzlich verwendeten Ressourcen im Aktivitätsfeed zu vermeiden. **Nicht konfiguriert** (Standard) aktiviert dieses Feature, damit Apps Endbenutzeraktivitäten veröffentlichen können.
- **Nur lokale Aktivitäten**: **Blockieren** Sie diese Einstellung, um geteilte Aktivitäten und Ermittlungen von kürzlich in der Programmumschaltung verwendeten Ressourcen anhand von ausschließlich lokalen Aktivitäten zu vermeiden. **Nicht konfiguriert** (Standard) aktiviert diese Einstellung.

Sie können Informationen definieren, auf die alle Apps auf dem Gerät zugreifen können. Definieren Sie ebenfalls Ausnahmen für jede App mithilfe von **App-bezogenen Datenschutzausnahmen**.

### <a name="exceptions"></a>Ausnahmen

- **Kontoinformationen**: Legen Sie fest, ob diese App auf den Benutzernamen, das Bild und andere Kontaktinformationen zugreifen darf.
- **Hintergrund-Apps**: Legen Sie fest, ob diese App im Hintergrund ausgeführt werden darf.
- **Kalender**: Legen Sie fest, ob diese App auf den Kalender zugreifen darf.
- **Anrufliste**: Legen Sie fest, ob diese App auf Ihre Anrufliste zugreifen darf.
- **Kamera**: Legen Sie fest, ob diese App auf die Kamera zugreifen darf.
- **Kontakte**: Legen Sie fest, ob diese App auf Kontakte zugreifen darf.
- **E-Mail**: Legen Sie fest, ob diese App auf E-Mails zugreifen und diese versenden darf.
- **Standort**: Legen Sie fest, ob diese App auf Standortinformationen zugreifen darf.
- **Nachrichten**: Legen Sie fest, ob diese App SMS oder MMS-Nachrichten lesen oder senden darf.
- **Mikrofon**: Legen Sie fest, ob diese App das Mikrofon verwenden darf.
- **Bewegung**: Legen Sie fest, ob diese App auf die Gerätebewegungsinformationen zugreifen darf.
- **Benachrichtigungen**: Legen Sie fest, ob diese App auf Benachrichtigungen zugreifen darf.
- **Telefon**: Legen Sie fest, ob diese App auf das Telefon zugreifen darf.
- **Radios**: Einige Apps verwenden Radios (z.B. Bluetooth) auf Ihrem Gerät, um Daten zu senden und zu empfangen, und müssen diese Radios ein- oder ausschalten. Legen Sie fest, ob diese App diese Radios steuern kann.
- **Aufgaben**: Legen Sie fest, ob diese App auf Ihre Aufgaben zugreifen darf.
- **Vertrauenswürdige Geräte:** Legen Sie fest, ob diese App vertrauenswürdige Geräte verwenden kann. Als vertrauenswürdige Geräte wird Hardware angesehen, mit der Sie bereits eine Verbindung hergestellt haben oder die in das Gerät integriert ist. Verwenden Sie z. B. Fernsehgeräte oder Projektoren als vertrauenswürdige Geräte.
- **Feedback und Diagnose**: Legen Sie diese Einstellung fest, wenn diese App auf Diagnoseinformationen zugreifen soll.
- **Mit Geräten synchronisieren**: Legen Sie fest, ob diese App automatisch Informationen mit Drahtlosgeräten teilen und synchronisieren darf, die nicht explizit mit Ihrem PC, Tablet oder Telefon gekoppelt sind.

## <a name="projection"></a>Projektion

Diese Einstellungen verwenden den [WirelessDisplay-Richtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wirelessdisplay), der auch die unterstützten Windows-Editionen auflistet.

- **Benutzereingabe über Empfänger der drahtlosen Anzeige**: **Blockieren** verhindert Benutzereingaben über Empfänger der drahtlosen Anzeige. **Nicht konfiguriert** (Standard) ermöglicht es, dass eine drahtlose Anzeige Tastatur-, Maus-, Stift- und Toucheingaben zurück an das Quellgerät sendet.
- **Projektion auf diesem PC**: **Blockieren** verhindert, dass andere Geräte das Gerät für die Projektion finden. **Nicht konfiguriert** (Standard) erlaubt, dass das Gerät erkannt wird, und kann eine Projektion auf das Gerät über den Sperrbildschirm durchführen.
- **PIN für Kopplung erforderlich**: Wählen Sie **Erforderlich** aus, um immer zur Eingabe einer PIN beim Herstellen der Verbindung mit einem Projektionsgerät aufzufordern. **Nicht konfiguriert** (Standard) erfordert keine PIN, um das Gerät an ein Projektionsgerät zu koppeln.

## <a name="reporting-and-telemetry"></a>Berichterstellung und Telemetrie

- **Nutzungsdaten freigeben**: Wählen Sie die Ebene der Diagnosedaten, die gesendet werden. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert**: Es werden keine Daten freigegeben.
  - **Sicherheit**: Informationen, die erforderlich sind, um Windows sicherer zu machen, einschließlich Daten zu den Einstellungen der Komponente „Benutzererfahrung und Telemetrie im verbundenen Modus“, zum Tool zum Entfernen bösartiger Software und zu Microsoft Defender.
  - **Standard**: Grundlegende Geräteinformationen, z.B. qualitätsbezogene Daten, App-Kompatibilität, App-Nutzungsdaten und Daten aus der Sicherheitsebene.
  - **Erweitert**: Zusätzliche Informationen, etwa wie Windows, Windows Server, System Center und Anwendungen verwendet werden, wie sie leistungsmäßig abschneiden, erweiterte Zuverlässigkeitsdaten und Standarddaten sowie Daten der Sicherheitsstufen.
  - **Vollständig**: Alle Daten, die zur Identifizierung und Behebung von Problemen erforderlich sind, sowie Daten aus den Bereichen „Sicherheit“, „Standard“ und „Erweitert“.

  [System/AllowTelemetry-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)

- **Microsoft Edge-Browserdaten an Microsoft 365 Analytics senden**: Um dieses Feature verwenden zu können, legen Sie für die Einstellung **Nutzungsdaten freigeben** **Erweitert** oder **Vollständig** fest. Dieses Feature steuert, welche Daten Microsoft Edge an Microsoft 365 Analytics für Unternehmensgeräte mit einer konfigurierten kommerziellen ID sendet. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert**: Verwendung des Betriebssystemstandards, d.h. Browserverlaufsdaten werden möglicherweise nicht gesendet.
  - **Nur Intranetdaten senden**: Ermöglicht dem Administrator, den Intranetdatenverlauf zu senden.
  - **Nur Internetdaten senden**: Ermöglicht dem Administrator, den Internetdatenverlauf zu senden.
  - **Intranet- und Internetdaten senden**: Ermöglicht dem Administrator, den Intranet- und Internetdatenverlauf zu senden.

  [Browser/ConfigureTelemetryForMicrosoft365Analytics-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configuretelemetryformicrosoft365analytics)

- **Telemetrieproxyserver**: Geben Sie den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) oder die IP-Adresse eines Proxyservers an, um Anforderungen zu Benutzererfahrung und Telemetrie im verbundenen Modus über eine SSL-Verbindung (Secure Sockets Layer) weiterzuleiten. Das Format dieser Einstellung lautet *Server*:*Port*. Wenn beim benannten Proxy ein Fehler auftritt oder kein Proxy angegeben wurde, obwohl diese Richtlinie aktiviert ist, werden die Daten zu Benutzererfahrung und Telemetrie im verbundenen Modus nicht gesendet und verbleiben auf dem lokalen Gerät.

  Beispiele für das Format:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

  [System/TelemetryProxy-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-telemetryproxy)

Klicken Sie auf **OK**, um die Änderungen zu speichern.

## <a name="search"></a>Suchen

Diese Einstellungen verwenden den [Suchrichtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search), der auch die unterstützten Windows-Editionen auflistet. 

- **SafeSearch (nur Mobilgeräte)** : Steuert, wie Cortana nicht jugendfreie Inhalte in den Suchergebnissen filtert. Folgende Optionen sind verfügbar:
  - **Benutzerdefiniert**: Zulassen, dass Endbenutzer ihre eigenen Einstellungen auswählen.
  - **Streng**: Höchste Filterung nicht jugendfreier Inhalte.
  - **Mittel**: Mittlere Filterung nicht jugendfreier Inhalte. Gültige Suchergebnisse werden nicht gefiltert.
- **Webergebnisse in der Suche anzeigen**: Bei Festlegung auf **Blockieren** können Benutzer nicht suchen, und Webergebnisse werden nicht in der Suche angezeigt. **Nicht konfiguriert** (Standard) ermöglicht Benutzern die Suche im Web, und die Ergebnisse werden auf dem Gerät angezeigt.

## <a name="start"></a>Starten

Diese Einstellungen verwenden den [Startrichtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start), der auch die unterstützten Windows-Editionen auflistet.  

- **Layout des Startmenüs**: Außerkraftsetzen des Standardlayouts für das Starten und Anpassen des Startmenüs auf Desktopgeräten. Sie können eine XML-Datei hochladen, die Ihre Anpassungen einschließlich der Reihenfolge der aufgeführten Apps und vieles mehr enthält. Benutzer können das von Ihnen festgelegte Startmenülayout nicht ändern.
- **Websites an Kacheln im Startmenü anheften**: Importieren Sie Bilder von Microsoft Edge, die im Windows-Startmenü von Desktopgeräten als Links angezeigt werden.
- **Apps von der Taskleiste lösen**: **Blockieren** verhindert, dass Benutzer Apps von der Taskleiste lösen können. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, Apps von der Taskleiste zu lösen.
- **Schneller Wechsel zwischen Benutzern**: **Blockieren** verhindert das Wechseln zwischen zwei gleichzeitig angemeldeten Benutzern ohne Abmeldung. **Nicht konfiguriert** (Standard) zeigt **Benutzer wechseln** auf der Kachel „Benutzer“ an.
- **Meistverwendete Apps**: **Blockieren** blendet die Anzeige der meistverwendeten Apps im Startmenü aus. Damit wird auch der entsprechende Schalter in der App „Einstellungen“ deaktiviert. **Nicht konfiguriert** (Standard) zeigt die am häufigsten verwendeten Apps an.
- **Zuletzt hinzugefügte Apps**: **Blockieren** blendet die Anzeige der zuletzt hinzugefügten Apps im Startmenü aus. Damit wird auch der entsprechende Schalter in der App „Einstellungen“ deaktiviert. **Nicht konfiguriert** (Standard) zeigt die zuletzt hinzugefügten Apps im Startmenü an.
- **Startbildschirmmodus**: Wählen Sie aus, wie der Startbildschirm angezeigt werden soll. Folgende Optionen sind verfügbar:
  - **Benutzerdefiniert**: Erzwingt die Größe des Startbildschirms nicht. Benutzer können die Größe festlegen.
  - **Vollbild**: Erzwingt das Vollbild des Startbildschirms.
  - **Kein Vollbild**: Erzwingt, dass kein Vollbild des Startbildschirms angezeigt wird.
- **Zuletzt geöffnete Elemente in Sprunglisten**: **Blockieren** blendet die Anzeige zuletzt verwendeter Sprunglisten im Startmenü aus. Damit wird auch der entsprechende Schalter in der App „Einstellungen“ deaktiviert. **Nicht konfiguriert** (Standard) zeigt die zuletzt geöffneten Elemente in den Sprunglisten an.
- **App-Liste**: Wählen Sie aus, wie die App-Listen angezeigt werden. Folgende Optionen sind verfügbar:
  - **Benutzerdefiniert**: Es wird keine Einstellung erzwungen. Benutzer wählen aus, wie die App-Liste auf dem Gerät angezeigt wird.
  - **Reduzieren**: Alle App-Listen ausblenden.
  - **Reduzieren und Einstellungen-App deaktivieren**: Alle App-Listen ausblenden und **App-Liste im Startmenü anzeigen** in der Einstellungen-App deaktivieren.
  - **Entfernt und deaktiviert die Einstellungen-App**: Alle App-Listen ausblenden, alle Apps-Schaltflächen entfernen und **App-Liste im Startmenü anzeigen** in der Einstellungen-App deaktivieren.
- **Netzschaltersymbol**: **Blockieren** blendet das Netzschaltersymbol im Startmenü aus. **Nicht konfiguriert** (Standard) zeigt das Netzschaltersymbol an.
- **Benutzerkachel**: **Blockieren** blendet die Anzeige der Benutzerkachel im Startmenü aus. **Nicht konfiguriert** (Standard) zeigt die Benutzerkachel an und legt auch die folgenden Einstellungen fest:
  - **Sperre**: **Blockieren** blendet die Option **Sperre** in der Benutzerkachel im Startmenü aus. **Nicht konfiguriert** (Standard) zeigt die Option **Sperre** an.
  - **Abmelden**: **Blockieren** blendet die Option **Abmelden** in der Benutzerkachel im Startmenü aus. **Nicht konfiguriert** (Standard) zeigt die Option **Abmelden** an.
- **Herunterfahren**: **Blockieren** blendet die Optionen **Aktualisieren und herunterfahren** und **Herunterfahren** im Netzschaltersymbol im Startmenü aus. **Nicht konfiguriert** (Standard) zeigt diese Optionen an.
- **Energiesparmodus**: **Blockieren** blendet die Option **Energiesparmodus** im Netzschaltersymbol im Startmenü aus. **Nicht konfiguriert** (Standard) zeigt diese Option an.
- **Ruhezustand**: **Blockieren** blendet die Option **Ruhezustand** im Netzschaltersymbol im Startmenü aus. **Nicht konfiguriert** (Standard) zeigt diese Option an.
- **Konto wechseln**: **Blockieren** blendet die Option **Konto wechseln** in der Benutzerkachel im Startmenü aus. **Nicht konfiguriert** (Standard) zeigt diese Option an.
- **Neustartoptionen**: **Blockieren** blendet die Optionen **Aktualisieren und neu starten** und **Neu starten** im Netzschaltersymbol im Startmenü aus. **Nicht konfiguriert** (Standard) zeigt diese Optionen an.
- **Dokumente im Startmenü**: Blendet den Ordner „Dokumente“ im Windows-Startmenü aus oder ein. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Keine Einstellung wird erzwungen. Benutzer können auswählen, ob die Verknüpfung ein- oder ausgeblendet werden soll.
  - **Ausblenden**: Die Verknüpfung wird ausgeblendet, und die Einstellung wird in der Einstellungen-App deaktiviert.
  - **Anzeigen**: Die Verknüpfung wird angezeigt, und die Einstellung wird in der Einstellungen-App deaktiviert.
- **Downloads im Startmenü**: Blendet den Ordner „Downloads“ im Windows-Startmenü aus oder ein. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Keine Einstellung wird erzwungen. Benutzer können auswählen, ob die Verknüpfung ein- oder ausgeblendet werden soll.
  - **Ausblenden**: Die Verknüpfung wird ausgeblendet, und die Einstellung wird in der Einstellungen-App deaktiviert.
  - **Anzeigen**: Die Verknüpfung wird angezeigt, und die Einstellung wird in der Einstellungen-App deaktiviert.
- **Datei-Explorer im Startmenü**: Blendet den Datei-Explorer im Windows-Startmenü aus oder ein. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Keine Einstellung wird erzwungen. Benutzer können auswählen, ob die Verknüpfung ein- oder ausgeblendet werden soll.
  - **Ausblenden**: Die Verknüpfung wird ausgeblendet, und die Einstellung wird in der Einstellungen-App deaktiviert.
  - **Anzeigen**: Die Verknüpfung wird angezeigt, und die Einstellung wird in der Einstellungen-App deaktiviert.
- **Heimnetzgruppe im Startmenü**: Blendet die Verknüpfung „Heimnetzgruppe“ im Windows-Startmenü aus oder ein. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Keine Einstellung wird erzwungen. Benutzer können auswählen, ob die Verknüpfung ein- oder ausgeblendet werden soll.
  - **Ausblenden**: Die Verknüpfung wird ausgeblendet, und die Einstellung wird in der Einstellungen-App deaktiviert.
  - **Anzeigen**: Die Verknüpfung wird angezeigt, und die Einstellung wird in der Einstellungen-App deaktiviert.
- **Musik im Startmenü**: Blendet den Ordner „Musik“ im Windows-Startmenü aus oder ein. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Keine Einstellung wird erzwungen. Benutzer können auswählen, ob die Verknüpfung ein- oder ausgeblendet werden soll.
  - **Ausblenden**: Die Verknüpfung wird ausgeblendet, und die Einstellung wird in der Einstellungen-App deaktiviert.
  - **Anzeigen**: Die Verknüpfung wird angezeigt, und die Einstellung wird in der Einstellungen-App deaktiviert.
- **Netzwerk im Startmenü**: Blendet „Netzwerk“ im Windows-Startmenü aus oder ein. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Keine Einstellung wird erzwungen. Benutzer können auswählen, ob die Verknüpfung ein- oder ausgeblendet werden soll.
  - **Ausblenden**: Die Verknüpfung wird ausgeblendet, und die Einstellung wird in der Einstellungen-App deaktiviert.
  - **Anzeigen**: Die Verknüpfung wird angezeigt, und die Einstellung wird in der Einstellungen-App deaktiviert.
- **Persönlicher Ordner im Startmenü**: Blendet den persönlichen Ordner im Windows-Startmenü aus oder ein. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Keine Einstellung wird erzwungen. Benutzer können auswählen, ob die Verknüpfung ein- oder ausgeblendet werden soll.
  - **Ausblenden**: Die Verknüpfung wird ausgeblendet, und die Einstellung wird in der Einstellungen-App deaktiviert.
  - **Anzeigen**: Die Verknüpfung wird angezeigt, und die Einstellung wird in der Einstellungen-App deaktiviert.
- **Bilder im Startmenü**: Blendet den Ordner für Bilder im Windows-Startmenü aus oder ein. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Keine Einstellung wird erzwungen. Benutzer können auswählen, ob die Verknüpfung ein- oder ausgeblendet werden soll.
  - **Ausblenden**: Die Verknüpfung wird ausgeblendet, und die Einstellung wird in der Einstellungen-App deaktiviert.
  - **Anzeigen**: Die Verknüpfung wird angezeigt, und die Einstellung wird in der Einstellungen-App deaktiviert.
- **Einstellungen im Startmenü**: Blendet die Verknüpfung „Einstellungen“ im Windows-Startmenü aus oder ein. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Keine Einstellung wird erzwungen. Benutzer können auswählen, ob die Verknüpfung ein- oder ausgeblendet werden soll.
  - **Ausblenden**: Die Verknüpfung wird ausgeblendet, und die Einstellung wird in der Einstellungen-App deaktiviert.
  - **Anzeigen**: Die Verknüpfung wird angezeigt, und die Einstellung wird in der Einstellungen-App deaktiviert.
- **Videos im Startmenü**: Blendet den Ordner für Videos im Windows-Startmenü aus oder ein. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Keine Einstellung wird erzwungen. Benutzer können auswählen, ob die Verknüpfung ein- oder ausgeblendet werden soll.
  - **Ausblenden**: Die Verknüpfung wird ausgeblendet, und die Einstellung wird in der Einstellungen-App deaktiviert.
  - **Anzeigen**: Die Verknüpfung wird angezeigt, und die Einstellung wird in der Einstellungen-App deaktiviert.

## <a name="microsoft-defender-smart-screen"></a>Microsoft Defender-SmartScreen

- **SmartScreen für Microsoft Edge**: **Erforderlich** deaktiviert Microsoft Defender SmartScreen, und SmartScreen kann von Benutzern nicht mehr aktiviert werden. **Nicht konfiguriert** (Standard) aktiviert SmartScreen. Schützt Benutzer vor potenziellen Bedrohungen und verhindert, dass Benutzer diese Einstellung deaktivieren.

  Microsoft Edge verwendet Microsoft Defender SmartScreen (aktiviert), um Benutzer vor potenziellen Phishingangriffen und Schadsoftware zu schützen.

  [Browser/AllowSmartScreen-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

- **Zugriff auf schädliche Websites**: **Blockieren** hindert Benutzer daran, die Warnungen des Microsoft Defender SmartScreen-Filters zu ignorieren, und blockiert den Besuch der Website. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, die Warnungen zu ignorieren und die Website zu besuchen.

  [Browser/PreventSmartScreenPromptOverride-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

- **Download nicht überprüfter Dateien**: **Blockieren** hindert Benutzer daran, die Warnungen des Microsoft Defender SmartScreen-Filters zu ignorieren, und blockiert das Herunterladen nicht überprüfter Dateien. **Nicht konfiguriert** (Standard) ermöglicht Benutzern, die Warnungen zu ignorieren und die nicht überprüften Dateien herunterzuladen.

  [Browser/PreventSmartScreenPromptOverrideForFiles-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

## <a name="windows-spotlight"></a>Windows-Blickpunkt

Diese Einstellungen verwenden den [Benutzeroberflächenrichtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience), der auch die unterstützten Windows-Editionen auflistet.

- **Windows-Blickpunkt**: **Blockieren** deaktiviert Windows-Blickpunkt auf dem Sperrbildschirm, Windows-Tipps, Microsoft-Features für Endbenutzer und weitere ähnliche Features. Wenn es Ihr Ziel ist, den Netzwerkdatenverkehr von Geräten zu minimieren, legen Sie diese Option auf **Blockieren** fest. **Nicht konfiguriert** (Standard) lässt Features von Windows-Blickpunkt zu und kann vom Endbenutzer gesteuert werden. Wenn diese Option aktiviert ist, können Sie auch die folgenden Einstellungen zulassen oder blockieren:

  - **Windows-Blickpunkt auf dem Sperrbildschirm**: **Blockieren** verhindert, dass Windows-Blickpunkt Informationen auf dem Gerätesperrbildschirm anzeigt. **Nicht konfiguriert** (Standard) aktiviert diese Einstellung.
  - **Drittanbietervorschläge in Windows-Blickpunkt**: **Blockieren** verhindert, dass Windows-Blickpunkt Inhalte vorschlägt, die nicht von Microsoft stammen. **Nicht konfiguriert** (Standard) lässt App- und Inhaltsvorschläge durch Herausgeber von Partnersoftware in Features von Windows-Blickpunkt (z.B. Windows-Blickpunkt auf dem Sperrbildschirm, vorgeschlagene Apps im Startmenü oder Windows-Tipps) zu.
  - **Endbenutzerfeatures**: **Blockieren** deaktiviert Funktionen, die normalerweise nur für Endbenutzer bestimmt sind, beispielsweise Startvorschläge, Mitgliedschaftsbenachrichtigungen, App-Installation nach Anzeige der Windows-Willkommensseite und Kachelumleitungen. **Nicht konfiguriert** (Standard) lässt diese Funktionen zu.
  - **Windows-Tipps**: **Blockieren** deaktiviert Windows-Tipps in Popupfenstern. **Nicht konfiguriert** (Standard) lässt die Anzeige von Windows-Tipps zu.
  - **Windows-Blickpunkt im Info-Center**: **Blockieren** verhindert, dass Benachrichtigungen von Windows-Blickpunkt im Info-Center angezeigt werden. **Nicht konfiguriert** (Standard) kann Benachrichtigungen im Info-Center anzeigen, die Apps oder Features vorschlagen, mit denen Benutzer unter Windows produktiver werden können.
  - **Personalisierung von Windows-Blickpunkt**: **Blockieren** verhindert, dass Windows Diagnosedaten verwendet, um angepasste Funktionen für Benutzer bereitzustellen. **Nicht konfiguriert** (Standard) ermöglicht es Microsoft, Diagnosedaten zu verwenden, um personalisierte Empfehlungen, Tipps und Angebote bereitzustellen und Windows an die Anforderungen des Benutzers anzupassen.
  - **Windows-Begrüßungsseite**: **Blockieren** deaktiviert die Windows-Willkommensfunktion von Windows-Blickpunkt. Der Windows-Willkommensseite wird nicht angezeigt, wenn Updates und Änderungen an Windows und den zugehörigen Apps vorgenommen werden. **Nicht konfiguriert** (Standard) lässt die Windows-Begrüßungsseite zu, die dem Benutzer Informationen zu neuen oder aktualisierten Features anzeigt.

## <a name="microsoft-defender-antivirus"></a>Microsoft Defender Antivirus

Diese Einstellungen verwenden den [Defender-Richtlinien-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender), der auch die unterstützten Windows-Editionen auflistet.

- **Echtzeitüberwachung**: **Aktivieren** schaltet die Echtzeitüberwachung auf Schadsoftware, Spyware und andere unerwünschte Software ein. Benutzer können diese Funktion nicht deaktivieren. 

  Wenn diese Einstellung auf **nicht konfiguriert** (Standardeinstellung) festgelegt ist, wird diese Einstellung von InTune nicht berührt. Wenn Sie die Einstellung aktivieren und dann wieder in **nicht konfiguriert**ändern, behält InTune die Einstellung im zuvor konfigurierten Zustand bei. Standardmäßig aktiviert das Betriebssystem diese Funktion und ermöglicht es Benutzern, Sie zu ändern.

  InTune deaktiviert dieses Feature nicht. Verwenden Sie einen benutzerdefinierten URI, um ihn zu deaktivieren.

  [Defender/allowrealtimemonitoring-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

- **Verhaltensüberwachung**: **Aktivieren** schaltet auf Geräten die Verhaltensüberwachung ein und prüft auf bestimmte bekannte Muster verdächtiger Aktivitäten. Benutzer können die Verhaltens Überwachung nicht deaktivieren. 

  Wenn diese Einstellung auf **nicht konfiguriert** (Standardeinstellung) festgelegt ist, wird diese Einstellung von InTune nicht berührt. Wenn Sie die Einstellung aktivieren und dann wieder in **nicht konfiguriert**ändern, behält InTune die Einstellung im zuvor konfigurierten Zustand bei. Standardmäßig aktiviert das Betriebssystem die Verhaltens Überwachung und ermöglicht es Benutzern, Sie zu ändern.

  InTune deaktiviert dieses Feature nicht. Verwenden Sie einen benutzerdefinierten URI, um ihn zu deaktivieren.

  [Defender/allowverhalormonitoring-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring)

- **Netzwerkinspektionssystem (NIS)** : NIS trägt zum Schutz von Geräten vor netzwerkbasierten Exploits bei. Es verwendet die Signaturen bekannter Sicherheitsrisiken aus dem Microsoft Endpoint Protection Center, um schädlichen Datenverkehr zu erkennen und zu blockieren.

  **Aktivieren aktiviert** Netzwerk Schutz und Netzwerk Blockierung. Benutzer können diese Funktion nicht deaktivieren. Wenn diese Option aktiviert ist, wird verhindert, dass Benutzer eine Verbindung mit bekannten Sicherheitsrisiken herstellen

  Wenn diese Einstellung auf **nicht konfiguriert** (Standardeinstellung) festgelegt ist, wird diese Einstellung von InTune nicht berührt. Wenn Sie die Einstellung aktivieren und dann wieder in **nicht konfiguriert**ändern, behält InTune die Einstellung im zuvor konfigurierten Zustand bei. Standardmäßig schaltet das Betriebssystem NIS ein und ermöglicht es Benutzern, es zu ändern.

  InTune deaktiviert dieses Feature nicht. Verwenden Sie einen benutzerdefinierten URI, um ihn zu deaktivieren.

  [Defender/enablenetworkprotection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)

- **Alle Downloads**überprüfen: **aktivieren** Sie diese Einstellung, und Defender scannt alle Dateien, die aus dem Internet heruntergeladen wurden. Die Benutzer können diese Einstellung nicht deaktivieren. 

  Wenn diese Einstellung auf **nicht konfiguriert** (Standardeinstellung) festgelegt ist, wird diese Einstellung von InTune nicht berührt. Wenn Sie die Einstellung aktivieren und dann wieder in **nicht konfiguriert**ändern, behält InTune die Einstellung im zuvor konfigurierten Zustand bei. Standardmäßig aktiviert das Betriebssystem diese Einstellung und ermöglicht es Benutzern, diese Einstellung zu ändern.

  InTune deaktiviert dieses Feature nicht. Verwenden Sie einen benutzerdefinierten URI, um ihn zu deaktivieren.

  [Defender/zugewiesene Software-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection)

- **In Microsoft-Webbrowsern geladene Skripts überprüfen**: **Aktivieren** ermöglicht Defender die Überprüfung von Skripts, die in Internet Explorer verwendet werden. Die Benutzer können diese Einstellung nicht deaktivieren. 

  Wenn diese Einstellung auf **nicht konfiguriert** (Standardeinstellung) festgelegt ist, wird diese Einstellung von InTune nicht berührt. Wenn Sie die Einstellung aktivieren und dann wieder in **nicht konfiguriert**ändern, behält InTune die Einstellung im zuvor konfigurierten Zustand bei. Standardmäßig aktiviert das Betriebssystem diese Einstellung und ermöglicht es Benutzern, diese Einstellung zu ändern.

  InTune deaktiviert dieses Feature nicht. Verwenden Sie einen benutzerdefinierten URI, um ihn zu deaktivieren.

  [Defender/allowscriptscan-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning)

- **Endbenutzerzugriff auf Defender**: **Blockieren** blendet die Benutzeroberfläche von Microsoft Defender für Endbenutzer aus. Alle Benachrichtigungen von Microsoft Defender werden ebenfalls unterdrückt.

  Wenn diese Einstellung auf **nicht konfiguriert** (Standardeinstellung) festgelegt ist, wird diese Einstellung von InTune nicht berührt. Wenn Sie die Einstellung blockieren und dann wieder in **nicht konfiguriert**ändern, behält InTune die Einstellung im zuvor konfigurierten Zustand bei. Standardmäßig ermöglicht das Betriebssystem den Benutzer Zugriff auf die Microsoft Defender-Benutzeroberfläche und ermöglicht es Benutzern, Sie zu ändern.

  InTune deaktiviert dieses Feature nicht. Verwenden Sie einen benutzerdefinierten URI, um ihn zu deaktivieren.

  Wenn diese Einstellung geändert wird, wird die Änderung wirksam, wenn der Endbenutzer-PC das nächste Mal neu gestartet wird.

  [Defender/zugriffsuiaccess-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess)

- **Sicherheits Intelligence-Aktualisierungs Intervall (in Stunden)** : Geben Sie das Intervall an, in dem Defender auf neue Sicherheits Intelligenz prüft, von 0-24. Folgende Optionen sind verfügbar:

  - **Nicht konfiguriert** (Standardeinstellung): Suchen Sie alle 8 Stunden nach Updates.
  - **Nicht überprüfen**: Defender prüft nicht, ob neue Sicherheitsinformationen angezeigt werden.
  - **1 – 24**: `1` überprüft ein Mal pro Stunde, `2` überprüft alle zwei Stunden, `24` überprüft täglich und so weiter.
  
  [Defender/signatureupdateingeterval CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval)
  
- **Datei- und Programmaktivität überwachen**: Ermöglicht Defender die Überwachung der Datei- und Programmaktivität auf Geräten. Folgende Optionen sind verfügbar:

  - **Nicht konfiguriert** (Standard): alle Dateien werden überwacht.
  - **Überwachung deaktiviert**
  - **Alle Dateien überwachen**
  - **Nur eingehende Dateien überwachen**
  - **Nur ausgehende Dateien überwachen**

  [Defender/realtimescandirection-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)

- **Tage bis zum Löschen von in Quarantäne befindlicher Schadsoftware**: Ermöglicht die fortgesetzte Nachverfolgung behandelter Schadsoftware für die eingegebene Anzahl von Tagen, damit Sie zuvor betroffene Geräte manuell überprüfen können. Wenn Sie die Anzahl von Tagen auf `0` festlegen, bleibt Schadsoftware im Quarantäneordner und wird nicht automatisch entfernt. Bei Festlegung auf `90` werden Quarantäneelemente 90 Tage lang im System gespeichert und anschließend entfernt.

  [Defender/daystoretaincleanedmalware-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware)

- **CPU-Nutzungslimit während einer Überprüfung**: Begrenzen Sie die CPU-Nutzung, die bei Überprüfungen genutzt werden darf (von `0` bis `100`).
- **Archivdateien**überprüfen: **aktiviert aktiviert** , damit Archivdateien wie ZIP-oder CAB-Dateien gescannt werden. Die Benutzer können diese Einstellung nicht deaktivieren.

  Wenn diese Einstellung auf **nicht konfiguriert** (Standardeinstellung) festgelegt ist, wird diese Einstellung von InTune nicht berührt. Wenn Sie die Einstellung aktivieren und dann wieder in **nicht konfiguriert**ändern, behält InTune die Einstellung im zuvor konfigurierten Zustand bei. Standardmäßig aktiviert das Betriebssystem diese Überprüfung und ermöglicht es Benutzern, Sie zu ändern.

  InTune deaktiviert dieses Feature nicht. Verwenden Sie einen benutzerdefinierten URI, um ihn zu deaktivieren.

  [Defender/Zuweisung von Software-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning)

- **Eingehende E-Mail überprüfen**: **Aktivieren** ermöglicht Defender das Überprüfen von E-Mail-Nachrichten beim Eingang auf dem Gerät. Wenn diese Option aktiviert ist, analysiert die Engine die Post Fach-und e-Mail-Dateien, um den e-Mail-Nachrichtentext Sie können die Formate ". PST (Outlook)", ". dbx", ". mbx", "MIME (Outlook Express)" und "BinHex (Mac)" Scannen.

  Wenn diese Einstellung auf **nicht konfiguriert** (Standardeinstellung) festgelegt ist, wird diese Einstellung von InTune nicht berührt. Wenn Sie die Einstellung aktivieren und dann wieder in **nicht konfiguriert**ändern, behält InTune die Einstellung im zuvor konfigurierten Zustand bei. Standardmäßig deaktiviert das Betriebssystem diese Überprüfung und ermöglicht es Benutzern, Sie zu ändern.

  InTune deaktiviert dieses Feature nicht. Verwenden Sie einen benutzerdefinierten URI, um ihn zu deaktivieren.

  [Defender/zugegtwemailscan-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning)

- Wechsel Datenträger **während einer vollständigen**Überprüfung überprüfen: **aktivieren** Sie während einer vollständigen Überprüfung das Überprüfen von Defender- Die Benutzer können diese Einstellung nicht deaktivieren.

  Wenn diese Einstellung auf **nicht konfiguriert** (Standardeinstellung) festgelegt ist, wird diese Einstellung von InTune nicht berührt. Wenn Sie die Einstellung aktivieren und dann wieder in **nicht konfiguriert**ändern, behält InTune die Einstellung im zuvor konfigurierten Zustand bei. Standardmäßig ermöglicht das Betriebssystem Defender das Überprüfen von Wechsel Datenträgern wie USB-Sticks und ermöglicht es Benutzern, diese Einstellung zu ändern.

  Während einer schnell Überprüfung können Wechsel Datenträger weiterhin gescannt werden.

  InTune deaktiviert dieses Feature nicht. Verwenden Sie einen benutzerdefinierten URI, um ihn zu deaktivieren.

  [Defender/allowfullscanremovabledrivescanning-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning)

- **Bei einer vollständigen Überprüfung zugeordnete Netzlaufwerke überprüfen**: **Aktivieren** sorgt dafür, dass Defender Dateien auf zugeordneten Netzwerklaufwerken überprüft. Wenn die Dateien auf dem Laufwerk schreibgeschützt sind, kann Defender gefundene Schadsoftware nicht entfernen. Die Benutzer können diese Einstellung nicht deaktivieren.

  Wenn diese Einstellung auf **nicht konfiguriert** (Standardeinstellung) festgelegt ist, wird diese Einstellung von InTune nicht berührt. Wenn Sie die Einstellung aktivieren und dann wieder in **nicht konfiguriert**ändern, behält InTune die Einstellung im zuvor konfigurierten Zustand bei. Standardmäßig aktiviert das Betriebssystem diese Funktion und ermöglicht es Benutzern, Sie zu ändern.

  Während einer schnell Überprüfung werden zugeordnete Netzwerklaufwerke möglicherweise noch gescannt.

  InTune deaktiviert dieses Feature nicht. Verwenden Sie einen benutzerdefinierten URI, um ihn zu deaktivieren.

  [Defender/allowfullscanonmappednetworkdrives CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives)

- Dateien überprüfen, die in **Netzwerk Ordnern geöffnet**wurden: **aktivieren** Sie hat Defender das Überprüfen von Dateien, die in Netzwerk Ordnern oder freigegebenen Netzlaufwerken geöffnet wurden Die Benutzer können diese Einstellung nicht deaktivieren. Wenn die Dateien auf dem Laufwerk schreibgeschützt sind, kann Defender gefundene Schadsoftware nicht entfernen.

  Wenn diese Einstellung auf **nicht konfiguriert** (Standardeinstellung) festgelegt ist, wird diese Einstellung von InTune nicht berührt. Wenn Sie die Einstellung aktivieren und dann wieder in **nicht konfiguriert**ändern, behält InTune die Einstellung im zuvor konfigurierten Zustand bei. Standardmäßig scannt das Betriebssystemdateien, die in Netzwerk Ordnern geöffnet wurden, und ermöglicht es Benutzern, Sie zu ändern.

  InTune deaktiviert dieses Feature nicht. Verwenden Sie einen benutzerdefinierten URI, um ihn zu deaktivieren.

  [Defender/allowscanningnetworkfiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles)

- **Cloudschutz**: **Aktivieren** lässt den Empfang von Informationen über Schadsoftwareaktivitäten der von Ihnen verwalteten Geräte durch Microsoft Active Protection Service zu. Benutzer können diese Einstellung nicht ändern. 

  Wenn diese Einstellung auf **nicht konfiguriert** (Standardeinstellung) festgelegt ist, wird diese Einstellung von InTune nicht berührt. Wenn Sie die Einstellung aktivieren und dann wieder in **nicht konfiguriert**ändern, behält InTune die Einstellung im zuvor konfigurierten Zustand bei. Standardmäßig ermöglicht das Betriebssystem dem Microsoft Active Protection Service, Informationen zu erhalten, und ermöglicht es Benutzern, diese Einstellung zu ändern.

  InTune deaktiviert dieses Feature nicht. Verwenden Sie einen benutzerdefinierten URI, um ihn zu deaktivieren.

  [Defender/allowcloudprotection-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)

- **Vor dem Senden von Beispielen bei Benutzern nachfragen**: Steuert, ob potenziell schädliche Dateien, die möglicherweise genauer analysiert werden müssen, automatisch an Microsoft gesendet werden. Folgende Optionen sind verfügbar:

  - **Nicht konfiguriert** (Standard): sichere Beispiele automatisch senden.
  - **Immer bestätigen**
  - **Vor dem Senden persönlicher Daten nachfragen**
  - **Nie Daten senden**
  - **Alle Daten ohne Nachfrage senden**: Daten werden automatisch gesendet.

  [Defender/submitsamplesconsent-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent)

- **Uhrzeit für die Durchführung einer täglichen Schnellüberprüfung**: Wählen Sie die Uhrzeit der Ausführung einer täglichen Schnellüberprüfung. Bei Wahl von **Nicht konfiguriert** erfolgt keine tägliche Überprüfung. Wenn Sie eine weitere Anpassung wünschen, konfigurieren Sie die Einstellung **Art der durchzuführenden Systemüberprüfung**.

  [Defender/ScheduleQuickScanTime (CSP)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)

- **Art der durchzuführenden Systemüberprüfung**: Planen Sie eine Systemüberprüfung, einschließlich des Grads der Überprüfung, sowie Tag und Uhrzeit der Ausführung der Überprüfung. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert**: Es erfolgt keine Planung einer Systemüberprüfung auf dem Gerät. Endbenutzer können Überprüfungen nach Bedarf oder Wunsch manuell auf ihren Geräten durchführen.
  - **Deaktivieren**: Deaktiviert die Systemüberprüfung auf dem Gerät. Wählen Sie diese Option, wenn Sie eine Antivirenlösung eines Partners verwenden, die Geräte überprüft.
  - **Schnellüberprüfung**: Dient zum Überprüfen gängiger Speicherorte, an denen Schadsoftware registriert sein kann (z.B. Registrierungsschlüssel und bekannte Windows-Startordner).
    - **Geplanter Tag**: Wählen Sie den Tag der Ausführung der Überprüfung.
    - **Geplante Zeit**: Wählen Sie die Uhrzeit der Ausführung der Überprüfung.
  - **Vollständige Überprüfung**: Dient zum Überprüfen gängiger Speicherorte, an denen Schadsoftware registriert sein kann sowie aller Dateien und Ordner auf dem Gerät.
    - **Geplanter Tag**: Wählen Sie den Tag der Ausführung der Überprüfung.
    - **Geplante Zeit**: Wählen Sie die Uhrzeit der Ausführung der Überprüfung.

  > [!TIP]
  > Diese Einstellung steht ggf. in Konflikt mit der Einstellung **Uhrzeit für die Durchführung einer täglichen Schnellüberprüfung**. Empfehlungen:  
  >
  > - Wenn Sie eine tägliche schnell Überprüfung und eine wöchentliche vollständige Überprüfung planen möchten, dann:
  >   1. Konfigurieren **Sie die Zeit für die Durchführung einer täglichen schnell** Überprüfung.
  >   2. Konfigurieren Sie den **Typ des System Scans,** der für eine vollständige Überprüfung durchgeführt werden soll.
  > 
  > - Wenn Sie nur eine schnell Überprüfung täglich (keine vollständige Überprüfung) wünschen, verwenden Sie entweder Einstellung: **Zeit, um eine tägliche schnell Überprüfung auszuführen** , oder führen Sie einen **Systemscan Vorgang aus**. Um beispielsweise jeden Dienstag um 6 Uhr eine Schnellüberprüfung durchzuführen, konfigurieren Sie die Einstellung **Art der durchzuführenden Systemüberprüfung**.
  > 
  > - Konfigurieren Sie **Uhrzeit für die Durchführung einer täglichen Schnellüberprüfung** nicht parallel mit auf **Schnellüberprüfung** festgelegter Einstellung **Art der durchzuführenden Systemüberprüfung**. Diese Einstellungen können in Konflikt stehen und eine Überprüfung möglicherweise verhindern.

  [CSP: Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [CSP: Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [CSP: Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **Möglicherweise unerwünschte Software erkennen**: Ermöglicht die Auswahl einer der folgenden Schutzebenen, wenn Windows potenziell unerwünschte Software erkennt. Folgende Optionen sind verfügbar:
  - **Nicht konfiguriert** (Standard): Der Microsoft Defender-Schutz vor möglicherweise unerwünschten Anwendungen ist deaktiviert.
  - **Blockieren**: Microsoft Defender erkennt potenziell unerwünschte Anwendungen, und erkannte Elemente werden blockiert. Diese Elemente werden Im Verlauf zusammen mit anderen Bedrohungen angezeigt.
  - **Überwachung**: Microsoft Defender erkennt potenziell unerwünschte Anwendungen, ergreift aber keine Maßnahmen. Sie können Informationen zu den Anwendungen überprüfen, gegen die Microsoft Defender Maßnahmen einleiten würde. Suchen Sie z. B. in der Ereignisanzeige nach durch Microsoft Defender erstellten Ereignissen.

  Weitere Informationen zu potenziell unerwünschten Apps finden Sie unter [Erkennen und Blockieren möglicherweise unerwünschter Anwendungen](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).

  [Defender/puaprotection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)

- **Aktionen bei erkannten schadsoftwarebedrohungen**: Wählen Sie aus, wie Malware-Threads behandelt werden sollen. **Nicht konfiguriert** (Standardeinstellung): Microsoft Defender kann die beste Option auswählen. Wenn diese Option auf **Aktivieren** festgelegt ist, können Sie die Aktionen auswählen, die Defender bei den einzelnen erkannten Bedrohungsstufen durchführen soll: niedrig, mittel, hoch und schwerwiegend. Folgende Optionen sind verfügbar:
  
  - **Bereinigen**
  - **Quarantäne**
  - **Entfernen**
  - **Zulassen**
  - **Benutzerdefiniert**
  - **Blockieren**

  Wenn Ihre Aktion nicht möglich ist, wählt Microsoft Defender die beste Option aus, um sicherzustellen, dass die Bedrohung wieder hergestellt wird. 

  [Defender/teriseveritydefaultaction-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-threatseveritydefaultaction)

### <a name="microsoft-defender-antivirus-exclusions"></a>Microsoft Defender Antivirus-Ausschlüsse

- **Dateien und Ordner, die bei Überprüfungen und Echtzeitschutz ausgeschlossen werden sollen**: Fügt Dateien und Ordner wie **C:\Pfad** oder **%ProgramFiles%\Pfad\Dateiname.exe** der Ausschlussliste hinzu. Diese Dateien und Ordner werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.
- **Dateierweiterungen, die bei Überprüfungen und Echtzeitschutz ausgeschlossen werden sollen**: Fügt der Ausschlussliste eine oder mehrere Erweiterungen wie **jpg** oder **txt** hinzu. Dateien mit diesen Erweiterungen werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.
- **Prozesse, die von Überprüfungen und Echtzeitschutz ausgenommen werden sollen**: Fügt der Ausschlussliste einen oder mehrere Prozesse vom Typ **.exe**, **.com** oder **.scr** hinzu. Diese Prozesse werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.

## <a name="next-steps"></a>Nächste Schritte

Weitere technische Details zu den einzelnen Einstellungen und den unterstützten Windows-Editionen finden Sie in der Referenz zum [Richtlinien-Konfigurationsdienstanbieter für Windows 10](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider).
