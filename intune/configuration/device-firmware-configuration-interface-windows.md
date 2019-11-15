---
title: Aktualisieren von Windows BIOS-Features mithilfe von MDM-Richtlinien in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Fügen Sie ein DFCI-Profil (Device Firmware Configuration Interface) hinzu, um UEFI-Einstellungen wie die CPU, integrierte Hardware und Startoptionen auf Windows 10-Geräten in Microsoft Intune zu verwalten.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/31/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 899d667ca271ae5c3edced18fab8da987c49b2ca
ms.sourcegitcommit: 85c894cb4df34a5ff558e3b45e28a8b91054d9e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73432533"
---
# <a name="use-device-firmware-configuration-interface-profiles-on-windows-devices-in-microsoft-intune-public-preview"></a>Verwenden von DFCI-Profilen (Device Firmware Configuration Interface) auf Windows-Geräten in Microsoft Intune (Public Preview)

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Wenn Sie Intune zum Verwalten von Autopilot-Geräten verwenden, können Sie nach deren Registrierung mithilfe von DFCI (Firmware Configuration Interface) UEFI-Einstellungen (BIOS) verwalten. Eine Übersicht über die Vorteile, Szenarios und Voraussetzungen finden Sie in der [Übersicht zu DFCI](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Dfci_Feature/).

DFCI [ermöglicht Windows das Weitergeben von Verwaltungsbefehlen](https://docs.microsoft.com/windows/client-management/mdm/uefi-csp) von Intune an UEFI (Unified Extensible Firmware Interface).

Verwenden Sie dieses Feature in Intune zum Steuern von BIOS-Einstellungen. In der Regel ist Firmware resilienter gegen böswillige Angriffe. Dadurch wird die Kontrolle des Endbenutzers über das BIOS beschränkt, was in kompromittierten Situationen gut ist.

Sie verwenden beispielsweise Windows 10-Geräte in einer sicheren Umgebung und wollen die Kamera deaktivieren. Sie können diese also auf Firmwareebene deaktivieren, sodass es keine Rolle spielt, was der Endbenutzer tut. Selbst wenn das Betriebssystem neu installiert oder der Computer zurückgesetzt wird, wird die Kamera nicht wieder eingeschaltet. Ein anderes Beispiel besteht darin, die Startoptionen zu sperren, um zu verhindern, dass Benutzer ein anderes Betriebssystem oder eine ältere Version von Windows starten, die nicht über die gleichen Sicherheitsfeatures verfügt.

Wenn Sie eine ältere Windows-Version neu installieren und ein separates Betriebssystem installieren oder die Festplatte formatieren, können Sie die DFCI-Verwaltung nicht außer Kraft setzen. Dieses Feature kann verhindern, dass Malware mit Betriebssystemprozessen (einschließlich erhöhter Betriebssystemprozesse) kommuniziert. Die DFCI-Vertrauenskette verwendet die Kryptografie mit öffentlichem Schlüssel und ist nicht von der Sicherheit des lokalen UEFI-Kennworts (BIOS) abhängig. Diese Sicherheitsebene blockiert für lokale Benutzer den Zugriff auf verwaltete Einstellungen aus den UEFI-Menüs (BIOS) des Geräts.

Diese Funktion gilt für:

- Windows 10 RS5 (1809) und höher auf unterstützter UEFI

## <a name="before-you-begin"></a>Vorbereitung

- Der Gerätehersteller muss der UEFI-Firmware im Fertigungsprozess DFCI hinzufügen oder als Firmwareupdate bereitstellen, das Sie installieren. Arbeiten Sie mit Geräteanbietern zusammen, um [die Hersteller zu ermitteln, die DFCI unterstützen](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Scenarios/DfciScenarios/#oems-that-support-dfci) oder die Firmwareversion für die Verwendung von DFCI unterstützen.

- Das Gerät muss von einem [CSP-Partner (Microsoft Cloud Solution Provider)](https://partner.microsoft.com/cloud-solution-provider) oder direkt vom OEM für Windows Autopilot registriert werden. 

  Manuell für Autopilot registrierte Geräte, die beispielsweise [aus einer CSV-Datei importiert werden](../enrollment/enrollment-autopilot.md#add-devices), dürfen DFCI nicht verwenden. Die DFCI-Verwaltung erfordert standardmäßig den externen Nachweis der kommerziellen Beschaffung des Geräts über eine OEM- oder CSP-Partnerregistrierung bei Windows Autopilot.

  Nach der Registrierung des Geräts wird dessen Seriennummer in der Liste der Windows Autopilot-Geräte angezeigt.

  Weitere Informationen zu Autopilot einschließlich sämtlicher Anforderungen finden Sie unter [Registrieren von Windows-Geräten in Intune mithilfe von Windows Autopilot](../enrollment/enrollment-autopilot.md).

## <a name="create-your-azure-ad-security-groups"></a>Erstellen von Azure AD-Sicherheitsgruppen

Autopilot-Bereitstellungsprofile werden Azure AD-Sicherheitsgruppen zugewiesen. Stellen Sie sicher, dass Sie Gruppen erstellen, die Ihre von DFCI unterstützten Geräte enthalten. Die meisten Organisationen erstellen für DFCI-Geräte Gerätegruppen anstelle von Benutzergruppen. Bedenken Sie die folgenden Szenarien:

- Die Personalabteilung (HR) verfügt über unterschiedliche Windows-Geräte. Aus Sicherheitsgründen möchten Sie, dass niemand in dieser Abteilung die Kamera der Geräte verwendet. In diesem Szenario können Sie eine Benutzergruppe für die Mitarbeiter der Personalabteilung erstellen, sodass die Richtlinie unabhängig vom Gerätetyp für die Benutzer in der Personalabteilungsgruppe gilt.
- Im Produktionsbereich sind 10 Geräte vorhanden. Sie möchten auf allen Geräten das Starten über ein USB-Gerät verhindern. In diesem Szenario können Sie eine Gerätegruppe erstellen und der Gruppe diese 10 Geräte hinzufügen.

Weitere Informationen zum Erstellen von Gruppen in Intune finden Sie unter [Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten](../fundamentals/groups-add.md).

## <a name="create-the-profiles"></a>Erstellen der Profile

Erstellen Sie die folgenden Profile, und weisen Sie diese Ihrer Gruppe zu, um DFCI zu verwenden.

### <a name="create-an-autopilot-deployment-profile"></a>Erstellen eines Autopilot-Bereitstellungsprofils

Mit diesem Profil werden neue Geräte eingerichtet und vorab konfiguriert. Das [Autopilot-Bereitstellungsprofil](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile) listet die Schritte zum Erstellen des Profils auf.

### <a name="create-an-enrollment-state-page-profile"></a>Erstellen eines Seite zum Registrierungsstatus-Profils

Dieses Profil stellt sicher, dass Geräte während des Windows Setups überprüft und für DFCI aktiviert werden. Es wird dringend empfohlen, dieses Profil zu verwenden, um die Geräteverwendung zu blockieren, bis alle Apps und Profile installiert sind. Das Profil [Seite zum Registrierungsstatus](../enrollment/windows-enrollment-status.md) listet die Schritte zum Erstellen des Profils auf.

### <a name="create-the-dfci-profile"></a>Erstellen des DFCI-Profils

Dieses Profil enthält die von Ihnen konfigurierten DFCI-Einstellungen.

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das Profil ein. Benennen Sie Ihre Richtlinien so, dass Sie diese später leicht wiedererkennen. Ein guter Profilname ist beispielsweise **Windows: Konfigurieren von DFCI-Einstellungen auf Windows-Geräten**.
    - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie **Windows 10 und höher** aus.
    - **Profiltyp**: Wählen Sie **Device Firmware Configuration Interface** aus.

4. Konfigurieren Sie die Einstellungen:

    - **Lokalem Benutzer das Ändern von UEFI-Einstellungen erlauben (BIOS):** Folgende Optionen sind verfügbar:
      - **Nur nicht konfigurierte Einstellungen:** Der lokale Benutzer kann *abgesehen* von den von Intune explizit auf **Aktivieren** oder **Deaktivieren** festgelegten Einstellungen alle Einstellungen ändern.
      - **Keine**: Der lokale Benutzer darf keine UEFI-Einstellungen (BIOS) einschließlich der nicht im DFCI-Profil angezeigten Einstellungen ändern.

    - **CPU- und E/A-Virtualisierung:** Folgende Optionen sind verfügbar:
        - **Nicht konfiguriert:** Intune verändert nichts und behält alle Einstellungen bei.
        - **Aktiviert**: Das BIOS ermöglicht dem Betriebssystem die Verwendung der CPU- und E/A-Funktionen der Plattform. Virtualisierungsbasierte Sicherheit- und Device Guard-Technologien werden eingeschaltet.
        - **Deaktivieren:** Das BIOS deaktiviert die CPU- und E/A-Virtualisierungsfunktionen der Plattform und verhindert deren Verwendung.
    - **Kameras:** Folgende Optionen sind verfügbar:
        - **Nicht konfiguriert:** Intune verändert nichts und behält alle Einstellungen bei.
        - **Aktiviert**: Alle integrierten Kameras, die direkt von UEFI (BIOS) verwaltet werden, sind aktiviert. Peripheriegeräte wie USB-Kameras sind nicht betroffen.
        - **Deaktiviert:** Alle integrierten Kameras, die direkt von UEFI (BIOS) verwaltet werden, sind deaktiviert. Peripheriegeräte wie USB-Kameras sind nicht betroffen.
    - **Mikrofone und Lautsprecher:**  Folgende Optionen sind verfügbar:
        - **Nicht konfiguriert:** Intune verändert nichts und behält alle Einstellungen bei.
        - **Aktiviert**: Alle integrierten Mikrofone und Lautsprecher, die direkt von UEFI (BIOS) verwaltet werden, sind aktiviert. Peripheriegeräte wie USB-Geräte sind nicht betroffen.
        - **Deaktiviert:** Alle integrierten Mikrofone und Lautsprecher, die direkt von UEFI (BIOS) verwaltet werden, sind deaktiviert. Peripheriegeräte wie USB-Geräte sind nicht betroffen.
    - **Radios (Bluetooth, WLAN, NFC usw.):** Folgende Optionen sind verfügbar:
        - **Nicht konfiguriert:** Intune verändert nichts und behält alle Einstellungen bei.
        - **Aktiviert**: Alle integrierten Radios, die direkt von UEFI (BIOS) verwaltet werden, sind aktiviert. Peripheriegeräte wie USB-Geräte sind nicht betroffen.
        - **Deaktiviert:** Alle integrierten Radios, die direkt von UEFI (BIOS) verwaltet werden, sind deaktiviert. Peripheriegeräte wie USB-Geräte sind nicht betroffen.

        > [!WARNING]
        > Wenn Sie die Einstellung **Radios** deaktivieren, ist für das Gerät eine kabelgebundene Netzwerkverbindung erforderlich. Andernfalls kann das Gerät nicht verwaltet werden.

    - **Von externen Medien aus starten (USB, SD):** Folgende Optionen sind verfügbar:
        - **Nicht konfiguriert:** Intune verändert nichts und behält alle Einstellungen bei.
        - **Aktiviert**: UEFI (BIOS) ermöglicht das Starten von externen Medien aus (nicht über Festplattenspeicher).
        - **Deaktiviert:** UEFI (BIOS) lässt das Starten von externen Medien über Speicher, die keine Festplattenspeicher sind, nicht zu.
    - **Von Netzwerkadaptern aus starten:**  Folgende Optionen sind verfügbar:
        - **Nicht konfiguriert:** Intune verändert nichts und behält alle Einstellungen bei.
        - **Aktiviert**: UEFI (BIOS) ermöglicht das Starten von integrierten Netzwerkschnittstellen aus.
        - **Deaktiviert:** UEFI (BIOS) lässt das Starten von integrierten Netzwerkschnittstellen aus nicht zu.

5. Wenn Sie fertig sind, wählen Sie **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern. Das Profil wird erstellt und in der Liste angezeigt.

## <a name="assign-the-profiles-and-reboot"></a>Zuweisen der Profile und Neustarten

Nach dem Erstellen der Profile [können diese zugewiesen werden](../configuration/device-profile-assign.md). Stellen Sie sicher, dass Sie die Profile Ihren Azure AD-Sicherheitsgruppen zuweisen, die Ihre DFCI-Geräte enthalten.

Wenn das Gerät das nächste Mal synchronisiert oder neu gestartet wird, werden die DFCI-Profileinstellungen angewendet. Starten Sie das Gerät nach Anwenden der Richtlinie neu.

Wenn das Gerät das Windows-Gerätesetup ausführt, kann DFCI während „Seite zum Registrierungsstatus“ einen Neustart erzwingen. Nach Abschluss des Setups können Sie sich vergewissern, dass die DFCI-Einstellungen aktiv sind, indem Sie das Gerät neu starten. Befolgen Sie dann die Anweisungen des Geräteherstellers, um das UEFI-Menü zu öffnen.

## <a name="update-existing-dfci-settings"></a>Aktualisieren vorhandener DFCI-Einstellungen

Wenn Sie möchten, können Sie vorhandene DFCI-Einstellungen auf verwendeten Geräten ändern. Ändern Sie die Einstellungen in Ihrem vorhandenen DFCI-Profil, und speichern Sie Ihre Änderungen. Da das Profil bereits zugewiesen ist, werden die neuen DFCI-Einstellungen in folgenden Situationen wirksam:

1. Das Gerät wird beim Intune-Dienst eingecheckt, um Profilaktualisierungen zu überprüfen. Check-Ins erfolgen zu verschiedenen Zeitpunkten. Weitere Informationen finden Sie im Artikel, in dem erläutert wird, [wann Geräte eine Richtlinie, ein Profil oder App-Updates erhalten](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

2. Führen Sie [remote](../remote-actions/device-restart.md) oder lokal einen Neustart des Geräts durch, um die neuen Einstellungen zu erzwingen.

Sie können [Geräten auch signalisieren, dass diese einchecken sollen](../remote-actions/device-sync.md). Signalisieren Sie nach einer erfolgreichen Synchronisierung, dass das [Gerät neu gestartet werden soll](../remote-actions/device-restart.md).

>[!NOTE]
> Wenn Sie das DFCI-Profil löschen oder ein Gerät aus der Gruppe entfernen, die dem Profil zugewiesen ist, werden keine DFCI-Einstellungen entfernt oder UEFI-Menüs (BIOS) erneut aktiviert. Aktualisieren Sie Ihr vorhandenes DFCI-Profil, wenn Sie DFCI nicht mehr verwenden möchten. Weitere Informationen zu diesen Schritten finden Sie in diesem Artikel im Abschnitt [Deaktivieren](#retire).

## <a name="reuse-retire-or-recover-the-device"></a>Wiederverwenden, Deaktivieren oder Wiederherstellen des Geräts

### <a name="reuse"></a>Wiederverwenden

[Setzen Sie das Gerät zurück](../remote-actions/devices-wipe.md), wenn Sie Windows zurücksetzen möchten, um das Gerät wieder zu verwenden. Entfernen Sie den Autopilot-Gerätedatensatz **nicht**.

Verschieben Sie das Gerät nach dem Zurücksetzen des Geräts in die Gruppe, der die neuen DFCI- und Autopilot-Profile zugewiesen sind. Stellen Sie sicher, dass Sie das Gerät neu starten, um das Windows Setup erneut auszuführen.

### <a name="retire"></a>Außerkraftsetzen

Aktualisieren Sie das DFCI-Profil auf die gewünschten UEFI-Einstellungen (BIOS), wenn Sie das Gerät deaktivieren und bei der Verwaltung nicht mehr berücksichtigen möchten. In der Regel möchten Sie, dass alle Einstellungen aktiviert sind. Beispiel:

1. Öffnen Sie das DFCI-Profil (**Gerätekonfiguration** > **Profile**).
2. Ändern Sie die Einstellung **Lokalem Benutzer das Ändern von UEFI-Einstellungen erlauben (BIOS)** in **Nur nicht konfigurierte Einstellungen**.
3. Legen Sie alle anderen Einstellungen auf **Nicht konfiguriert** fest.
4. Speichern Sie die Einstellungen.

Mit diesen Schritten werden die UEFI-Menüs (BIOS) des Geräts entsperrt. Die Werte und das Profil bleiben identisch (**Aktiviert** oder **Deaktiviert**) und werden nicht auf die Standardwerte des Betriebssystems zurückgesetzt.

Sie können das Gerät jetzt zurücksetzen. Löschen Sie den Autopilot-Datensatz, wenn das Gerät zurückgesetzt wurde. Durch das Löschen des Datensatzes wird verhindert, dass das Gerät bei einem Neustart automatisch erneut registriert wird.

### <a name="recover"></a>Wiederherstellen

Wenn Sie ein Gerät zurücksetzen und den Autopilot-Datensatz vor dem Entsperren des UEFI-Menüs (BIOS) löschen, bleiben die Menüs gesperrt. Intune kann keine Profilupdates zum Entsperren senden.

Um das Gerät zu entsperren, öffnen Sie das UEFI-Menü (BIOS), und aktualisieren Sie die Verwaltung über das Netzwerk. Durch die Wiederherstellung werden die Menüs entsperrt, aber für alle UEFI-Einstellungen (BIOS) bleiben die im vorherigen Intune-DFCI-Profil festgelegten Werte erhalten.

## <a name="end-user-impact"></a>Auswirkungen auf den Endbenutzer

Wenn die DFCI-Richtlinie angewendet wird, können lokale Benutzer von DFCI konfigurierte Einstellungen nicht ändern, auch wenn das UEFI-Menü (BIOS) kennwortgeschützt ist. Abhängig von den von Ihnen konfigurierten Einstellungen erhalten Endbenutzer möglicherweise Fehlermeldungen, dass Hardwarekomponenten nicht gefunden werden oder nicht diagnostiziert werden können. Stellen Sie sicher, dass Endbenutzern eine Dokumentation bereitgestellt wird, in der die von Ihnen deaktivierten Optionen erläutert werden.  

## <a name="next-steps"></a>Nächste Schritte

[Überwachen Sie nach dem Zuweisen des Profils dessen Status](../device-profile-monitor.md).
