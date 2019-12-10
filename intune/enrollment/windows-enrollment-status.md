---
title: Einrichten einer Seite zum Registrierungsstatus
titleSuffix: Microsoft Intune
description: Richten Sie eine Begrüßungsseite für Benutzer ein, die Windows 10-Geräte registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: ericor
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e81b8dc4938ea080018efae97093bb5e70dbcde8
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74548015"
---
# <a name="set-up-an-enrollment-status-page"></a>Einrichten einer Seite zum Registrierungsstatus
 
[!INCLUDE [azure_portal](../includes/azure_portal.md)]
 
Auf der Seite zum Registrierungsstatus (Enrollment Status Page, ESP) werden während der erstmaligen Geräteregistrierung Installationsinformationen zu Windows 10-Geräten (ab Version 1803) angezeigt. Beispiel:
- Bei Verwenden von [Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/) 
- oder jedes Mal, wenn ein verwaltetes Gerät zum ersten Mal gestartet wird, nachdem eine Richtlinie des Typs „Seite zum Registrierungsstatus“ angewendet wurde. 

Mithilfe der Seite zum Registrierungsstatus können Benutzer den Status Ihres Geräts während der Geräteeinrichtung besser nachvollziehen. Sie können mehrere Profile des Typs „Seite zum Registrierungsstatus“ erstellen und auf verschiedene Benutzergruppen anwenden. Folgendes kann für Profile festgelegt werden:
- Installationsstatus anzeigen
- Nutzung blockieren, bis die Installation abgeschlossen ist
- Angeben, wie ein Benutzer vorgehen kann, wenn die Geräteeinrichtung fehlschlägt.

Außerdem können Sie die Reihenfolge anhand der Priorität der Profile festlegen, um in Konflikt stehende Profilzuweisungen zum gleichen Benutzer zu vermeiden.

> [!NOTE]
> Die Seite zum Registrierungsstatus kann nur auf einen Benutzer abgestimmt werden, der zu einer zugewiesenen Gruppe gehört. Die Richtlinie wird zum Zeitpunkt der Registrierung auf dem Gerät für alle seine Benutzer festgelegt.  

## <a name="available-settings"></a>Verfügbare Einstellungen

 Die folgenden Einstellungen können konfiguriert werden, um das Verhalten der Seite zum Registrierungsstatus anzupassen:

<table>
<th align="left">Einstellung<th align="left">Ja<th align="left">Nein
<tr><td>Installationsfortschritt für Apps und Profile anzeigen<td>Die Seite zum Registrierungsstatus wird angezeigt.<td>Die Seite zum Registrierungsstatus wird nicht angezeigt.
<tr><td>Geräteverwendung blockieren, bis alle Apps und Profile installiert sind<td>Die Einstellungen in dieser Tabelle werden zur Verfügung gestellt, um das Verhalten der Seite zum Registrierungsstatus anzupassen, sodass der Benutzer mögliche Installationsprobleme beheben kann.
<td>Die Seite zum Registrierungsstatus wird ohne zusätzliche Optionen zum Beheben von Installationsproblemen angezeigt.
<tr><td>Benutzern bei Installationsfehlern das Zurücksetzen des Geräts erlauben<td>Bei einem Installationsfehler wird die Schaltfläche <b>Gerät zurücksetzen</b> angezeigt.<td>Bei einem Installationsfehler wird die Schaltfläche <b>Gerät zurücksetzen</b> nicht angezeigt.
<tr><td>Benutzern bei Installationsfehlern Geräteverwendung erlauben<td>Bei einem Installationsfehler wird die Schaltfläche <b>Trotzdem fortfahren</b> angezeigt.<td>Bei einem Installationsfehler wird die Schaltfläche <b>Trotzdem fortfahren</b> nicht angezeigt.
<tr><td>Timeoutfehler anzeigen, wenn die Installation länger als die angegebene Anzahl von Minuten dauert<td colspan="2">Geben Sie die Anzahl der Minuten an, die auf den Abschluss der Installation gewartet werden soll. 60 Minuten ist als Standardwert vorgegeben.
<tr><td>Bei einem Fehler benutzerdefinierte Meldung anzeigen<td>Ein Textfeld steht bereit, in das Sie eine benutzerdefinierte Meldung eingeben können, die angezeigt wird, sobald ein Installationsfehler auftritt.<td>Die Standardmeldung wird angezeigt: <br><b>Die Installation hat das von Ihrer Organisation festgelegte Zeitlimit überschritten. Versuchen Sie es nochmals, oder wenden Sie sich an Ihren IT-Support.<b>
<tr><td>Benutzern das Erfassen von Protokollen zu Installationsfehlern erlauben<td>Bei einem Installationsfehler wird die Schaltfläche <b>Protokolle sammeln</b> angezeigt. <br>Wenn der Benutzer auf diese Schaltfläche klickt, wird er aufgefordert, einen Speicherort für die Protokolldatei <b>MDMDiagReport.cab</b> auszuwählen.<td>Bei einem Installationsfehler wird die Schaltfläche <b>Protokolle sammeln</b> nicht angezeigt.
<tr><td>Geräteverwendung blockieren, bis diese erforderlichen Apps installiert sind, wenn sie dem Benutzer/Gerät zugewiesen sind<td colspan="2">Wählen Sie <b>Alle</b> oder <b>Ausgewählt</b> aus. <br><br>Bei Wahl von <b>Ausgewählt</b> wird die Schaltfläche <b>Anwendungen auswählen</b> eingeblendet, über die Sie bestimmen können, welche Apps vor der Aktivierung des Geräts installiert werden müssen.
</table>

## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Aktivieren der standardmäßigen Seite zum Registrierungsstatus für alle Benutzer

Führen Sie die folgenden Schritte aus, um die Seite zum Registrierungsstatus zu aktivieren.
 
1. Klicken Sie in [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) auf **Geräte** > **Windows** > **Windows-Registrierung** > **Seite zum Registrierungsstatus**.
2. Klicken Sie auf dem Blatt **Seite zum Registrierungsstatus** auf **Standard** > **Einstellungen**.
3. Klicken Sie für **Show app and profile installation progress** (Installationsfortschritt für die App und das Profil anzeigen) auf **Ja**.
4. Wählen Sie die anderen Einstellungen aus, die Sie aktivieren wollen, und klicken Sie anschließend auf **Speichern**.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>Erstellen eines Profils des Typs „Seite zum Registrierungsstatus“ und Zuweisen zu einer Gruppe

1. Klicken Sie in [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) auf **Geräte** > **Windows** > **Windows-Registrierung** > **Seite zum Registrierungsstatus** > **Profil erstellen**.
2. Geben Sie einen **Namen** und eine **Beschreibung** an.
3. Wählen Sie **Erstellen** aus.
4. Wählen Sie das neue Profil in der Liste der **Seite zum Registrierungsstatus** aus.
5. Klicken Sie auf **Zuweisungen** > **Gruppen auswählen**. Wählen Sie dann die Gruppen aus, für die dieses Profil übernommen werden soll, und klicken Sie abschließend auf **Auswählen** > **Speichern**.
6. Wählen Sie **Einstellungen** und dann die Einstellungen aus, die Sie auf dieses Profil anwenden möchten. Klicken Sie auf **Speichern** aus.

## <a name="set-the-enrollment-status-page-priority"></a>Festlegen der Priorität von Registrierungsstatusseiten

Ein Benutzer kann vielen Gruppen angehören und viele Profile des Typs „Seite zum Registrierungsstatus“ haben. Um solche Konflikte zu handhaben, können Sie für jedes Profil die Priorität festlegen. Wenn jemand während der Registrierung mehr als ein Profil für „Seite zum Registrierungsstatus“ hat, wird nur das Profil mit der höchsten Priorität auf das zu registrierende Gerät angewendet.

1. Klicken Sie in [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) auf **Geräte** > **Windows** > **Windows-Registrierung** > **Seite zum Registrierungsstatus**.
2. Zeigen Sie auf das Profil in der Liste.
3. Ziehen Sie mithilfe der drei vertikalen Punkte das Profil an die gewünschte Position in der Liste.

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>Blockieren des Zugriffs auf ein Gerät, bis eine bestimmte Anwendung installiert ist

Sie können angeben, welche Apps installiert sein müssen, bevor der Benutzer auf den Desktop zugreifen kann.

1. Klicken Sie in [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) auf **Geräte** > **Windows** > **Windows-Registrierung** > **Seite zum Registrierungsstatus**.
2. Wählen Sie ein Profil und dann **Einstellungen** aus.
3. Wählen Sie **Ja** für **Installationsfortschritt für Apps und Profile anzeigen** aus.
4. Wählen Sie **Ja** für **Geräteverwendung blockieren, bis alle Apps und Profile installiert sind** aus.
5. Wählen Sie **Ausgewählt** für **Geräteverwendung blockieren, bis diese erforderlichen Apps installiert sind, wenn sie dem Benutzer/Gerät zugewiesen sind** aus.
6. Wählen Sie **Apps auswählen**, wählen Sie die Apps und dann **Auswählen** > **Speichern** aus.

## <a name="enrollment-status-page-tracking-information"></a>Auf der Seite zum Registrierungsstatus nachverfolgte Informationen

Auf der Seite zum Registrierungsstatus werden Informationen in drei Phasen nachverfolgt: Gerätevorbereitung, Geräteeinrichtung und Kontoeinrichtung.

### <a name="device-preparation"></a>Gerätevorbereitung

Zur Vorbereitung des Geräts wird auf der Seite zum Registrierungsstatus Folgendes nachverfolgt:
- TPM-Schlüsselnachweise (Trusted Platform Module) (falls zutreffend)
- Fortschritt beim Beitritt zu Azure Active Directory
- Registrierung bei Intune
- Installation von Intune-Verwaltungserweiterungen

### <a name="device-setup"></a>Geräteeinrichtung

Auf der Seite zum Registrierungsstatus werden die folgenden Geräteeinrichtungselemente nachverfolgt (wenn sie „Alle Geräte“ oder einer Gerätegruppe zugeordnet sind, zu der das zu registrierende Gerät gehört):
- Sicherheitsrichtlinien
  - Ein Konfigurationsanbieter für alle Registrierungen
  - Tatsächliche CSPs, die von Intune konfiguriert wurden, werden an dieser Stelle nicht nachverfolgt.
- Applications
  - Branchenspezifische MSI-Apps („pro Computer“)
  - Branchenspezifische Store-Apps mit dem Installationskontext „Gerät“
  - Branchenspezifische und Offline Store-Apps mit dem Installationskontext „Gerät“
  - Win32-Anwendungen (ab Windows 10, Version 1903) 
- Konnektivitätsprofile
  - VPN- oder WLAN-Profile, die **allen Geräten** oder einer Gerätegruppe zugewiesen sind, in der das zu registrierende Gerät ein Mitglied ist, jedoch nur für Autopilot-Geräte
- Zertifikat-Profile, die **allen Geräten** oder einer Gerätegruppe zugewiesen sind, in der das zu registrierende Gerät ein Mitglied ist, jedoch nur für Autopilot-Geräte

### <a name="account-setup"></a>Kontoeinrichtung
Für die Kontoeinrichtung werden die folgenden Elemente auf der Seite zum Registrierungsstatus nachverfolgt, wenn diese dem derzeit angemeldeten Benutzer zugewiesen sind:
- Sicherheitsrichtlinien
  - Ein CSP für alle Registrierungen
  - Tatsächliche CSPs, die von Intune konfiguriert wurden, werden an dieser Stelle nicht nachverfolgt.
- Applications
  - Branchenspezifische MSI-Apps („pro Benutzer“), die „Allen Geräten“, „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört
  - Branchenspezifische MSI-Apps („pro Computer“), die „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört
  - Branchenspezifische Store-, Onlinestore- und Offlinestore-Apps, die einem der folgenden Objekte zugewiesen sind:
    - Alle Geräte
    - Allen Benutzern
    - Eine Benutzergruppe, zu der der Benutzer gehört, der das Gerät registriert, wobei der Installationskontext auf „Benutzer“ festgelegt ist.
  - Win32-Anwendungen (ab Windows 10, Version 1903) 
- Konnektivitätsprofile
  - VPN- oder WLAN-Profile, die „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört
- Zertifikate
  - Zertifikatprofile, die „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört

### <a name="troubleshooting"></a>Problembehandlung
Die wichtigsten Fragen zur Problembehandlung

- Warum wurden meine Anwendungen während der Autopilot-Bereitstellungsphase „Geräteeinrichtung“ auf der Seite zum Registrierungsstatus nicht installiert?
  - Um dafür zu sorgen, dass Anwendungen während der Autopilot-Phase „Geräteeinrichtung“ installiert werden, stellen Sie Folgendes sicher: 
        1. Die Anwendung ist so eingerichtet, dass der Zugriff auf die Liste „Ausgewählte Apps“ blockiert ist.
        2. Sie weisen die Anwendungen derselben Azure AD-Gerätegruppe zu, der auch Ihr Autopilot-Profil zugewiesen ist. 

- Warum wird die Seite zum Registrierungsstatus für Bereitstellungen ohne Autopilot angezeigt, z. B. wenn sich ein Benutzer zum ersten Mal auf einem registrierten Gerät anmeldet, das gemeinsam mit Configuration Manager verwaltet wird?  
  - Auf der Seite zum Registrierungsstatus wird der Installationsstatus für alle Registrierungsmethoden angezeigt, einschließlich
      - Autopilot
      - Co-Verwaltung mit Configuration Manager
      - wenn sich ein neuer Benutzer bei dem Gerät anmeldet, auf dem die Richtlinie „Seite zum Registrierungsstatus“ zum ersten Mal angewendet wird

- Wie kann ich die Seite zum Registrierungsstatus deaktivieren, wenn sie auf dem Gerät konfiguriert wurde?
  - Die Richtlinie „Seite zum Registrierungsstatus“ wird zum Zeitpunkt der Registrierung auf einem Gerät festgelegt. Um die Seite zum Registrierungsstatus zu deaktivieren, müssen Sie deren Abschnitte „Benutzer“ und „Gerät“ deaktivieren. Sie deaktivieren die Abschnitte, indem Sie benutzerdefinierte OMA-URI-Einstellungen mit den folgenden Konfigurationen erstellen.

      Deaktivieren der Seite zum Registrierungsstatus für Benutzer:

      ```
      Name:  Disable User ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipUserStatusPage
      Data type:  Boolean
      Value:  True 
      ```
      Deaktivieren der Seite zum Registrierungsstatus für Geräte:

      ```
      Name:  Disable Device ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipDeviceStatusPage
      Data type:  Boolean
      Value:  True 
      ```
- Wie kann ich Protokolldateien sammeln?
  - Es gibt zwei Möglichkeiten zur Erfassung von Protokolldateien zur Seite zum Registrierungsstatus (Enrollment Status Page, ESP):
      - Aktivieren Sie in der ESP-Richtlinie, dass Benutzer Protokolle sammeln dürfen. Wenn auf der Seite zum Registrierungsstatus ein Timeout auftritt, kann der Endbenutzer die Option **Protokolle sammeln** wählen. Nach Herstellen einer Verbindung mit einem USB-Laufwerk können die Protokolldateien darauf kopiert werden.
      - Öffnen Sie eine Eingabeaufforderung, indem Sie UMSCHALTTASTE+F10 drücken und dann die folgende Befehlszeile eingeben, um die Protokolldateien zu generieren: 

      ```
      mdmdiagnosticstool.exe -area Autopilot -cab <pathToOutputCabFile>.cab 
      ```

### <a name="known-issues"></a>Bekannte Probleme
Nachstehend sind bekannte Probleme aufgeführt. 
- Durch das Deaktivieren des ESP-Profils wird die zugehörige Richtlinie nicht von den Geräten entfernt, und den Benutzern wird weiterhin die Seite zum Registrierungsstatus angezeigt, wenn sie sich zum ersten Mal am Gerät anmelden. Die Richtlinie wird nicht entfernt, wenn das ESP-Profil deaktiviert wird. Sie müssen den OMA-URI bereitstellen, um die Seite zum Registrierungsstatus zu deaktivieren. Weitere Informationen zum Deaktivieren der Seite zum Registrierungsstatus mithilfe des OMA-URI finden Sie weiter oben. 
- Ein ausstehender Neustart führt immer zu einem Timeout. Das Timeout tritt auf, weil das Gerät neu gestartet werden muss. Der Neustart ist erforderlich, um dem Element, das auf der Seite zum Registrierungsstatus nachverfolgt wird, Zeit bis zum Vorgangsabschluss einzuräumen. Ein Neustart führt dazu, dass die Seite zum Registrierungsstatus beendet wird. Nach einem Neustart wird die Seite während der Kontoeinrichtung nach dem Neustart nicht mehr aufgerufen.  Erwägen Sie, bei der Anwendungsinstallation keinen Neustart anzufordern. 
- Ein Neustart während der Geräteeinrichtung zwingt den Benutzer vor dem Übergang zur Phase „Kontoeinrichtung“ zur Eingabe seiner Anmeldeinformationen. Benutzeranmeldeinformationen werden während des Neustarts nicht beibehalten. Lassen Sie den Benutzer seine Anmeldeinformationen eingeben, damit die Seite zum Registrierungsstatus fortgesetzt werden kann. 
- Für die Seite zum Registrierungsstatus unter Windows 10-Versionen vor 1903 erfolgt während einer Registrierung des Typs „Geschäfts-, Schul- oder Unikonto hinzufügen“ immer ein Timeout. Die Seite zum Registrierungsstatus wartet auf den Abschluss der Azure AD Registrierung. Das Problem wurde für Windows 10 ab Version 1903 behoben.  
- Azure AD Hybrid-Autopilot-Bereitstellung mit Seite zum Registrierungsstatus dauert länger als die Timeoutdauer, die im ESP-Profil angegeben ist. Bei Azure AD Hybrid-Autopilot-Bereitstellungen benötigt die Seite zum Registrierungsstatus 40 Minuten länger als der im ESP-Profil festgelegte Wert. Diese Verzögerung gibt dem lokalen AD-Connector Zeit zum Erstellen des neuen Gerätedatensatzes für Azure AD. 
- Windows-Anmeldeseite wird im benutzergesteuerten Autopilot-Modus nicht mit dem Benutzernamen vorausgefüllt. Bei einem Neustart in der Phase „Geräteeinrichtung“ der Seite zum Registrierungsstatus gilt Folgendes:
    - Benutzeranmeldeinformationen werden nicht beibehalten.
    - Der Benutzer muss die Anmeldeinformationen vor dem Wechsel von der Phase „Geräteeinrichtung“ zur Phase „Kontoeinrichtung“ erneut eingeben.
- Die Seite zum Registrierungsstatus ist lange im Stillstand oder beendet nie die Phase „Identifizierung“. Intune berechnet die ESP-Richtlinien in der Phase „Identifizierung“. Ein Gerät schließt das Berechnungen der ESP-Richtlinien ggf. nie ab, wenn dem aktuellen Benutzer keine Intune-Lizenz zugewiesen ist.  
- Die Konfiguration der Microsoft Defender-Anwendungssteuerung bewirkt eine Aufforderung zum Neustart im Autopilot-Modus. Das Konfigurieren der Microsoft Defender-Anwendung (mit AppLocker als Kryptografiedienstanbieter) erfordert einen Neustart. Wenn diese Richtlinie konfiguriert ist, kann dies dazu führen, dass ein Gerät im Autopilot-Modus neu gestartet wird. Derzeit gibt es keine Möglichkeit, den Neustart zu unterdrücken oder zu verschieben.
- Wenn die DeviceLock-Richtlinie (https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) als Teil eines ESP-Profils aktiviert ist, kann die Windows-Willkommensseite oder automatische Anmeldung am Benutzerdesktop aus zwei Gründen unerwartet fehlschlagen.
  - Wenn das Gerät nicht neu gestartet wurde, bevor die ESP-Phase „Geräteeinrichtung“ beendet wurde, wird der Benutzer möglicherweise aufgefordert, seine Azure AD-Anmeldeinformationen einzugeben. Diese Eingabeaufforderung erfolgt anstelle einer erfolgreichen automatischen Anmeldung, bei der der Benutzer die Animation zur ersten Anmeldung unter Windows sieht.
  - Die automatische Anmeldung schlägt fehl, wenn das Gerät neu gestartet wird, nachdem der Benutzer seine Azure AD-Anmeldeinformationen eingegeben hat, aber bevor er die ESP-Phase „Geräteeinrichtung“ beendet hat. Dieser Fehler tritt auf, weil die ESP-Phase „Geräteeinrichtung“ nie abgeschlossen wurde. Die Problemumgehung besteht im Zurücksetzen des Geräts.

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie die Windows-Registrierungsseiten eingerichtet haben, sollten Sie sich informieren, wie Sie Windows-Geräte verwalten. Weitere Informationen finden Sie unter [Was ist die Microsoft Intune-Geräteverwaltung?](../remote-actions/device-management.md).
