---
title: Tipps zum Troubleshooting für BitLocker-Richtlinien in Microsoft Intune
titleSuffix: Microsoft Intune
description: In diesem Artikel wird beschrieben, wie Sie die BitLocker-Verschlüsselung auf einem Gerät mithilfe der Intune-Richtlinie aktivieren und überprüfen, ob die Richtlinie erfolgreich auf einem Gerät bereitgestellt wurde.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3b32268d0b04dee84a737b9a1c768bc4fab7202
ms.sourcegitcommit: 3964e6697b4d43e2c69a15e97c8d16f8c838645b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77556498"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Troubleshooting für BitLocker-Richtlinien in Microsoft Intune

Dieser Artikel hilft Intune-Administratoren dabei, zu verstehen, wie Windows 10-Geräte BitLocker basierend auf der Intune-Richtlinie konfigurieren. Außerdem finden Sie in diesem Artikel Anleitungen zum Troubleshooting von Problemen mit BitLocker-Einstellungen auf Geräten, die Sie mit Intune verwalten.  

## <a name="understanding-bitlocker"></a>Grundlegendes zu BitLocker

Die BitLocker-Laufwerkverschlüsselung ist ein Microsoft-Dienst, der von Windows-Betriebssystemen angeboten wird, und der es Benutzern ermöglicht, Daten auf ihren Festplatten zu verschlüsseln. BitLocker unterstützt die Verschlüsselung von Betriebssystem-, Wechselmedien- und Festplattenlaufwerken. BitLocker unterstützt auch die Verwendung der 256-Bit-Verschlüsselung für einen besseren Schutz sensibler Daten.  

Mit Microsoft Intune verfügen Sie über die folgenden Methoden zum Verwalten von BitLocker auf Windows 10-Geräten:

- **Gerätekonfigurationsrichtlinien:** In Intune sind für das Erstellen eines Gerätekonfigurationsprofils zur Verwaltung von Endpoint Protection bestimmte integrierte Richtlinienoptionen verfügbar. [Erstellen Sie ein Geräteprofil für Endpoint Protection](endpoint-protection-configure.md#create-a-device-profile-containing-endpoint-protection-settings), klicken Sie unter *Plattform* auf **Windows 10 und höher**, und klicken Sie dann unter *Einstellungen* auf die Option **Windows-Verschlüsselung**, damit diese Optionen angezeigt werden. 

   Informationen zu den verfügbaren Optionen und Funktionen finden Sie unter [Windows-Verschlüsselung](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption).

- **Sicherheitsbaselines**: [Sicherheitsbaselines](security-baselines.md) sind bekannte Einstellungsgruppen und Standardwerte, die vom relevanten Sicherheitsteam für den Schutz von Windows-Geräten empfohlen werden. Unterschiedliche Baselinequellen, z. B. die *MDM-Sicherheitsbaseline* oder die *Microsoft Defender ATP-Baseline*, können prinzipiell dieselben Einstellungen verwalten. Außerdem gibt es Baseline-spezifische Einstellungen. Mit ihnen können auch dieselben Einstellungen verwaltet werden, die Sie mit den Gerätekonfigurationsrichtlinien verwalten. 

Sobald der Benutzer ein Gerät zu Azure AD hinzufügt, wird die BitLocker-Geräteverschlüsselung zusätzlich zu Intune für Hardware automatisch aktiviert, die mit modernem Standby und HSTI kompatibel ist und eine der beiden Funktionen verwendet. Azure AD bietet ein Portal, in dem Wiederherstellungsschlüssel ebenfalls gesichert werden, sodass Benutzer bei Bedarf ihren eigenen Wiederherstellungsschlüssel für Self-Service abrufen können.

Zudem können BitLocker-Einstellungen auf andere Weise verwaltet, z. B. per Gruppenrichtlinie, oder manuell von einem Gerätebenutzer festgelegt werden.

Unabhängig davon, wie Einstellungen auf ein Gerät angewendet werden, verwenden BitLocker-Richtlinien den [BitLocker-Konfigurationsdienstanbieter (Configuration Service Provider, CSP)](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp), um die Verschlüsselung auf dem Gerät zu konfigurieren. Der BitLocker-CSP ist in Windows integriert, und wenn Intune eine BitLocker-Richtlinie für ein zugewiesenes Gerät bereitstellt, schreibt der BitLocker-CSP auf dem Gerät die entsprechenden Werte in die Windows-Registrierung, sodass die Einstellungen dieser Richtlinie übernommen werden können.

Weitere Informationen zu BitLocker finden Sie in den folgenden Ressourcen:

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Übersicht über BitLocker und häufig gestellte Fragen zu den Anforderungen](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

Nachdem Sie jetzt ein allgemeines Verständnis der Aufgabe und Funktionsweise dieser Richtlinien erlangt haben, können Sie sich nun ansehen, wie Sie überprüfen können, ob die BitLocker-Einstellungen erfolgreich auf einen Windows-Client angewendet wurden.

## <a name="verify-the-source-of-bitlocker-settings"></a>Überprüfen der Quelle von BitLocker-Einstellungen

Wenn Sie ein BitLocker-Problem auf einem Windows 10-Gerät untersuchen, müssen Sie zunächst überprüfen, ob es sich um ein Intune-oder Windows-bezogenes Problem handelt. Sobald die vermutliche Fehlerquelle bekannt ist, können Sie das Troubleshooting entsprechend ausrichten und dann – falls erforderlich – Support vom richtigen Team anfordern.  

Bestimmen Sie zunächst, ob die Intune-Richtlinie erfolgreich auf dem Zielgerät bereitgestellt wurde. Im folgenden Beispiel sehen Sie, wie eine Gerätekonfigurationsrichtlinie die Einstellungen für die Windows-Verschlüsselung (BitLocker) bereitstellt:

![Gerätekonfigurationsrichtlinie mit Einstellungen für die Windows-Verschlüsselung](./media/troubleshooting-bitlocker-policies/settings.png)

Wie überprüfen Sie, ob die Einstellungen auf das Zielgerät angewendet wurden? Im Folgenden werden einige Möglichkeiten erläutert, wie Sie das überprüfen können.

### <a name="device-configuration-policy-device-status"></a>Gerätestatus der Gerätekonfigurationsrichtlinie  

Wenn Sie BitLocker mit der Gerätekonfigurationsrichtlinie konfigurieren, können Sie den Status der Richtlinie im Intune-Portal überprüfen.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Klicken Sie auf **Geräte** > **Konfigurationsprofile**, und wählen Sie dann das Profil aus, das BitLocker-Einstellungen enthält.

3. Nachdem Sie das Profil ausgewählt haben, das Sie anzeigen möchten, klicken Sie auf **Gerätestatus**. Dem Profil zugewiesene Geräte werden aufgelistet, und die Spalte *Gerätestatus* zeigt an, ob ein Gerät das Profil erfolgreich bereitgestellt hat.

Beachten Sie, dass es eine Verzögerung zwischen einem Gerät, das eine BitLocker-Richtlinie empfängt, und der vollständigen Verschlüsselung des Laufwerks geben kann.  

### <a name="use-control-panel-on-the-client"></a>Verwenden der Systemsteuerung auf dem Client  

Auf einem Gerät mit aktiviertem BitLocker-Feature und verschlüsseltem Laufwerk können Sie sich den BitLocker-Status in der Systemsteuerung für Geräte ansehen. Öffnen Sie auf dem Gerät **Systemsteuerung** > **System und Sicherheit** > **BitLocker-Laufwerkverschlüsselung**. Die Bestätigung wird wie in der folgenden Abbildung dargestellt angezeigt.  

![BitLocker ist in der Systemsteuerung aktiviert](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>Verwenden Sie eine Eingabeaufforderung.  

Starten Sie auf einem Gerät mit aktiviertem BitLocker-Feature und verschlüsseltem Laufwerk die Eingabeaufforderung mit den Anmeldeinformationen eines Administrators, und führen Sie dann `manage-bde -status` aus. Die Ergebnisse entsprechen in etwa dem folgenden Beispiel:  
![Ein Ergebnis des Befehls zum Anzeigen des Status](./media/troubleshooting-bitlocker-policies/command.png)

Im Beispiel gilt:

- Der **BitLocker-Schutz** ist **aktiviert**.
- **Verschlüsselt (Prozent)** sind **100 %** .
- Die **Verschlüsselungsmethode** ist **XTS-AES 256**.

Sie können auch die **Schlüsselschutzvorrichtung** überprüfen, indem Sie den folgenden Befehl ausführen:

```cmd
Manage-bde -protectors -get c:
```

Oder mit PowerShell:

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>Überprüfen der Registrierungsschlüsselkonfiguration für Geräte

Nachdem die BitLocker-Richtlinie erfolgreich auf einem Gerät bereitgestellt wurde, können Sie den folgenden Registrierungsschlüssel auf dem Gerät anzeigen. Dort können Sie die Konfiguration der BitLocker-Einstellungen überprüfen:  *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker*. Beispiel:

![BitLocker-Registrierungsschlüssel](./media/troubleshooting-bitlocker-policies/registry.png)

Diese Werte werden vom BitLocker-CSP konfiguriert. Überprüfen Sie, ob die Werte der Schlüssel mit den Einstellungen übereinstimmen, die in der Quelle Ihrer Windows-Verschlüsselungsrichtlinie für Intune angegeben sind. Weitere Informationen zu den einzelnen Einstellungen finden Sie unter [BitLocker-CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

> [!NOTE]
> Die Windows-Ereignisanzeige enthält außerdem verschiedene Informationen zu BitLocker. Diese Informationen sind zu umfangreich, um sie hier auflisten zu können. Wenn Sie jedoch nach **BitLocker-API** suchen, erhalten Sie viele hilfreiche Informationen.

### <a name="check-the-mdm-diagnostics-report"></a>Überprüfen des MDM-Diagnoseberichts

Auf einem Gerät, auf dem das BitLocker-Feature aktiviert ist, können Sie einen MDM-Diagnosebericht für das Zielgerät generieren und anzeigen lassen, um zu überprüfen, ob die BitLocker-Richtlinie auf dem Gerät erfolgreich bereitgestellt wurde. Wenn die Richtlinieneinstellungen im Bericht angezeigt werden, ist dies ein weiterer Hinweis darauf, dass die Richtlinie erfolgreich bereitgestellt wurde. Im *Hilfevideo von Microsoft* hinter folgendem Link wird erläutert, wie ein MDM-Diagnosebericht für ein Windows-Gerät generiert wird.

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

Wenn Sie den MDM-Diagnosebericht analysieren, kann der Inhalt zuerst etwas verwirrend erscheinen. Im folgenden Beispiel sehen Sie, wie Sie die Informationen im Bericht den entsprechenden Einstellungen einer Richtlinie zuordnen:

![Beispiel für MDM-Diagnosebericht](./media/troubleshooting-bitlocker-policies/report.png)

Das Ausgabeergebnis zeigt die Werte, die den Werten aus der BitLocker-Richtlinie entsprechen:

![Ausgabeergebnis zeigt die Werte ](./media/troubleshooting-bitlocker-policies/output.png)

Unten sehen Sie Ausgabeergebnisse einer MDM-Diagnose:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

Sie können die [Dokumentation zu BitLocker-CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) als Referenz verwenden, um zu erfahren, was die einzelnen Werte bedeuten. Sehen Sie sich für dieses Beispiel folgenden Ausschnitt an:

![Zwecke von Werten](./media/troubleshooting-bitlocker-policies/shared-example.png)

Ebenso werden alle Werte angezeigt, und Sie können Sie über den BitLocker-CSP-Link überprüfen.

> [!TIP]
> Der primäre Zweck des MDM-Diagnoseberichts besteht darin, den Microsoft-Support beim Troubleshooting von Problemen zu unterstützen. Wenn Sie eine Supportanfrage für Intune eröffnen und Ihr Problem mit Windows-Clients zusammenhängt, ist es immer hilfreich, diesen Bericht generieren zu lassen und in Ihre Supportanfrage einzubeziehen.

## <a name="troubleshooting-bitlocker-policy"></a>Troubleshooting für die BitLocker-Richtlinie

Sie sollten nun gut darüber informiert sein, wie Sie überprüfen, ob die BitLocker-Richtlinie erfolgreich von Intune bereitgestellt wurde und die Konfiguration von BitLocker unter Windows somit vom BitLocker-CSP übernommen wird.

**Die Richtlinie wird auf dem Gerät nicht bereitgestellt:** Überprüfen Sie Folgendes, wenn Sie das Vorhandensein der Intune-Richtlinie über keine der genannten Möglichkeiten bestätigen können:

- **Ist das Gerät ordnungsgemäß bei Microsoft Intune registriert?** Falls nicht, müssen Sie dies tun, bevor Sie ein zielgerichtetes Troubleshooting für die Richtlinie durchführen können. Hilfe zum Troubleshooting bei Problemen mit der Windows-Registrierung finden Sie [hier](../enrollment/troubleshoot-windows-enrollment-errors.md).

- **Ist auf dem Gerät eine aktive Netzwerkverbindung vorhanden?** Wenn sich das Gerät im Flugzeugmodus befindet oder ausgeschaltet ist, oder wenn sich der Gerätebenutzer an einem Standort ohne Empfang befindet, wird die Richtlinie erst übermittelt und angewendet, wenn die Netzwerkverbindung wieder hergestellt ist.

- **Wurde die BitLocker-Richtlinie für den richtigen Benutzer oder die richtige Gerätegruppe bereitgestellt?** Überprüfen Sie, ob der richtige Benutzer oder das richtige Gerät Mitglied der Gruppen ist, für die die Richtlinie bereitgestellt werden sollte.

**Die Richtlinie ist vorhanden, jedoch wurden nicht alle Einstellungen erfolgreich konfiguriert:** Überprüfen Sie Folgendes, wenn die Intune-Richtlinie auf dem Gerät vorhanden ist, jedoch nicht alle Konfigurationen festgelegt sind:

- **Tritt bei der Bereitstellung der gesamten Richtlinie ein Fehler auf, oder handelt es sich nur um bestimmte Einstellungen, die nicht angewendet werden?** Wenn bei Ihnen nicht alle Richtlinieneinstellungen angewendet werden, überprüfen Sie, ob einer der folgenden Hinweise Ihr konkretes Problem erklärt:

  1. **Nicht alle BitLocker-Einstellungen werden für alle Windows-Versionen unterstützt.**
     Die Richtlinie wird als Einheit auf ein Gerät angewendet. Wenn also nur einige Einstellungen nicht angewendet werden, können Sie dennoch sicher sein, dass die Richtlinie selbst für Ihr Gerät bereitgestellt wurde. In diesem Szenario ist es möglich, dass die Windows-Version auf dem Gerät die problematischen Einstellungen nicht unterstützt. Ausführliche Informationen zu den Versionsanforderungen für die einzelnen Einstellungen finden Sie in der Windows-Dokumentation zum [BitLocker-CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

  2. **BitLocker wird nicht auf jeder Hardware unterstützt.**
     Selbst wenn Sie eine geeignete Windows-Version verwenden, kann es sein, dass die zugrunde liegende Gerätehardware die Anforderungen für die BitLocker-Verschlüsselung nicht erfüllt. Die [Systemanforderungen für BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) finden Sie in der Windows-Dokumentation. Sie sollten aber insbesondere überprüfen, ob das Gerät über einen kompatiblen TPM-Chip (1.2 oder höher) und eine TCG-konforme BIOS- oder UEFI-Firmware (Trusted Computing Group) verfügt.
     
**Die BitLocker-Verschlüsselung wird nicht automatisch ausgeführt**: Sie haben eine Richtlinie für Endpoint Protection konfiguriert und die Einstellung „Warnung zu anderer Datenträgerverschlüsselung“ auf „Blockieren“ festgelegt, doch der Verschlüsselungsassistent wird weiterhin angezeigt:

- **Bestätigen Sie, dass die Windows-Version die automatische Verschlüsselung unterstützt**: Die dafür erforderliche Mindestversion ist 1803. Ist der Benutzer kein Administrator auf dem Gerät, lautet die Mindestversion 1809. Darüber hinaus wurde bei Version 1809 Unterstützung für Geräte hinzugefügt, die modernen Standby nicht unterstützen.

**Ein mit BitLocker verschlüsseltes Gerät wird als nicht kompatibel mit den Konformitätsrichtlinien von Intune angezeigt**: Dieses Problem tritt auf, wenn die BitLocker-Verschlüsselung noch nicht abgeschlossen ist. Je nach Faktoren wie der Größe des Datenträgers, der Anzahl von Dateien und den BitLocker-Einstellungen, kann die BitLocker-Verschlüsselung einige Zeit in Anspruch nehmen. Sobald die Verschlüsselung abgeschlossen ist, wird das Gerät als kompatibel angezeigt. Auch direkt nach der Installation von Windows-Updates können Geräte vorübergehend als nicht kompatibel angezeigt werden.

**Geräte werden mithilfe eines 128-Bit-Algorithmus verschlüsselt, obwohl in der Richtlinie 256 Bit angegeben sind**: Die Standardverschlüsselung eines Laufwerks erfolgt in Windows 10 über XTS-AES mit 128 Bit. Informationen zum Festlegen einer 256-Bit-Verschlüsselung für BitLocker im Autopilot-Modus finden Sie in [diesem Handbuch](https://techcommunity.microsoft.com/t5/intune-customer-success/setting-256-bit-encryption-for-bitlocker-during-autopilot-with/ba-p/323791#).


**Beispieluntersuchung**

- Sie stellen eine BitLocker-Richtlinie auf einem Windows 10-Gerät bereit, und die Einstellung **Geräte verschlüsseln** zeigt im Portal den Status **Fehler** an.

- Wie der Name bereits vermuten lässt, kann ein Administrator mit dieser Einstellung die Aktivierung der Verschlüsselung über *BitLocker > Geräteverschlüsselung* erzwingen. Mithilfe der zuvor erwähnten Tipps zum Troubleshooting sehen Sie sich zuerst den MDM-Diagnosebericht an. Mithilfe dieses Berichts können Sie bestätigen, dass die richtige Richtlinie auf dem Gerät bereitgestellt wurde:

  ![Im Bericht wird bestätigt, dass die richtige Richtlinie auf dem Gerät bereitgestellt wurde](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- Alternativ können Sie sich zur Bestätigung auch die Registrierung ansehen:

  ![Der Registrierungswert RequiredDeviceEncryption zeigt den Wert 1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- Als nächsten Schritt überprüfen Sie den TPM-Status mithilfe von PowerShell und stellen fest, dass TPM auf dem Gerät nicht verfügbar ist:

  ![Mithilfe von PowerShell überprüfter TPM-Status](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- Da BitLocker auf TPM basiert, können Sie darauf schließen, dass der BitLocker-Fehler nicht einem Problem mit Intune oder der Richtlinie geschuldet ist, sondern dass das Gerät selbst keinen TPM-Chip hat oder dass TPM im BIOS deaktiviert ist.

  Ein zusätzlicher Tipp: Sie können dieselbe Überprüfung auch mithilfe der Windows-Ereignisanzeige über **Anwendungs- und Dienstprotokolle** > **Microsoft** > **Windows** > **BitLocker-API** durchführen. Im Ereignisprotokoll der **BitLocker-API** finden Sie die Ereignis-ID 853, die darauf hinweist, dass TPM nicht verfügbar ist:

  ![Ereignis-ID 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > Sie können auch den TPM-Status überprüfen, indem Sie **tpm.msc** auf dem Gerät ausführen.

## <a name="summary"></a>Zusammenfassung

Wenn Sie beim Troubleshooting von Problemen im Zusammenhang mit der BitLocker-Richtlinie in Intune bestätigen können, dass die Richtlinie auf dem gewünschten Gerät bereitgestellt wurde, können Sie sicher sein, dass es sich um kein Intune-spezifisches Problem handelt. Das Problem hat sehr wahrscheinlich mit dem Windows-Betriebssystem oder der Hardware zu tun. In diesem Fall sollten Sie in anderen Bereichen wie der TPM-Konfiguration oder UEFI und dem sicheren Start suchen.

## <a name="next-steps"></a>Nächste Schritte  

Unten finden Sie weitere Ressourcen, die Sie beim Arbeiten mit BitLocker unterstützen könnten:

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Systemanforderungen](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [BitLocker: Häufig gestellte Fragen](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [BitLocker-CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Windows-Verschlüsselung](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [Hardwareunabhängige automatische BitLocker-Verschlüsselung mit AAD/MDM](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [CSP-Richtlinie für die BitLocker-Verschlüsselung auf Autopilotgeräten](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [BitLocker-Verwaltung mit Microsoft Intune unter Windows 10](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)
