---
title: Tipps zur Problembehandlung für BitLocker-Richtlinien in Microsoft InTune
titleSuffix: Microsoft Intune
description: Hier wird beschrieben, wie Sie die BitLocker-Verschlüsselung auf einem Gerät mithilfe der InTune-Richtlinie aktivieren und überprüfen, ob Ihre Richtlinie erfolgreich auf einem Gerät bereitgestellt wurde.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
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
ms.openlocfilehash: 744277b0e49a4e3ca8b0fa3bac43c666110bb8a3
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74410353"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Behandeln von Problemen mit BitLocker-Richtlinien in Microsoft InTune

Dieser Artikel hilft InTune-Administratoren dabei, zu verstehen, wie Windows 10-Geräte BitLocker basierend auf der InTune-Richtlinie konfigurieren. Außerdem finden Sie in diesem Artikel Anleitungen zum Beheben von Problemen mit BitLocker-Einstellungen auf Geräten, die Sie mit InTune verwalten.  

## <a name="understanding-bitlocker"></a>Grundlegendes zu BitLocker

Die BitLocker-Laufwerk Verschlüsselung ist ein Dienst, der von Microsoft Windows-Betriebssystemen angeboten wird, die es Benutzern ermöglichen, Daten auf Ihren Festplatten zu verschlüsseln. BitLocker unterstützt die Verschlüsselung von Betriebssystem Laufwerken, Wechselmedien Laufwerken und Festplatten Laufwerken. BitLocker unterstützt auch die Verwendung der 256-Bit-Verschlüsselung für einen besseren Schutz sensibler Daten.  

Mit Microsoft InTune verfügen Sie über die folgenden Methoden zum Verwalten von BitLocker auf Windows 10-Geräten:

- **Geräte Konfigurationsrichtlinien** : bestimmte integrierte Richtlinien Optionen sind in InTune verfügbar, wenn Sie ein Geräte Konfigurations Profil zur Verwaltung von Endpoint Protection erstellen. Um diese Optionen zu finden [, erstellen Sie ein Geräte Profil für Endpoint Protection](endpoint-protection-configure.md#create-a-device-profile-containing-endpoint-protection-settings), wählen Sie **Windows 10 und** höher für die *Plattform*aus, und wählen Sie dann die Kategorie **Windows-Verschlüsselung** für *Einstellungen*aus. 

   Informationen zu den verfügbaren Optionen und Features finden Sie hier: [Windows-Verschlüsselung](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption).

- **Sicherheitsbaselines** - [Sicherheitsbaselines](security-baselines.md) sind bekannte Einstellungs Gruppen und Standardwerte, die vom relevanten Sicherheitsteam für die Sicherung von Windows-Geräten empfohlen werden. Mit unterschiedlichen Baseline-Quellen, wie z. b. der *MDM-Sicherheitsbaseline* oder der *Microsoft Defender ATP-Baseline* , können dieselben Einstellungen wie andere Einstellungen verwaltet werden. Sie können auch die gleichen Einstellungen verwalten, die Sie mit den Geräte Konfigurationsrichtlinien verwalten. 

Zusätzlich zu InTune ist es möglich, dass BitLocker-Einstellungen auf andere Weise verwaltet werden, wie z. b. Gruppenrichtlinie oder manuell von einem Gerätebenutzer festgelegt wird.

Unabhängig davon, wie Einstellungen auf ein Gerät angewendet werden, verwenden BitLocker-Richtlinien den [BitLocker-CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) , um die Verschlüsselung auf dem Gerät zu konfigurieren. Der BitLocker-CSP ist in Windows integriert, und wenn InTune eine BitLocker-Richtlinie für ein zugewiesenes Gerät bereitstellt, ist dies der BitLocker-CSP auf dem Gerät, der die entsprechenden Werte in die Windows-Registrierung schreibt, damit die Einstellungen der Richtlinie wirksam werden können.

Weitere Informationen zu BitLocker finden Sie in den folgenden Ressourcen:

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [FAQ zu BitLocker und Anforderungen](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

Nachdem Sie nun über ein allgemeines Verständnis der Funktionsweise dieser Richtlinien und ihrer Funktionsweise verfügen, sehen Sie sich an, wie Sie überprüfen können, ob die BitLocker-Einstellungen für einen Windows-Client erfolgreich angewendet wurden.

## <a name="verify-the-source-of-bitlocker-settings"></a>Überprüfen der Quelle von BitLocker-Einstellungen

Wenn Sie ein BitLocker-Problem auf einem Windows 10-Gerät untersuchen, müssen Sie zunächst feststellen, ob es sich um InTune-oder Windows-bezogene Probleme handelt. Nachdem die wahrscheinliche Fehlerquelle bekannt ist, können Sie die Problem Behandlungsbemühungen an der richtigen Stelle ausrichten und ggf. Support vom richtigen Team erhalten.  

Legen Sie als ersten Schritt fest, ob die Intune-Richtlinie erfolgreich auf dem Zielgerät bereitgestellt wurde. Im folgenden Beispiel verfügen Sie über eine Geräte Konfigurationsrichtlinie, die die Einstellungen für die Windows-Verschlüsselung (BitLocker) bereitstellt, wie hier gezeigt:

![Windows-Verschlüsselungsgeräte-Konfigurationsrichtlinie mit den Einstellungen](./media/troubleshooting-bitlocker-policies/settings.png)

Wie bestätigen Sie, dass die Einstellungen auf das Zielgerät angewendet wurden? Es folgen einige Möglichkeiten, dies zu tun.

### <a name="device-configuration-policy-device-status"></a>Gerätestatus Geräte-Konfigurationsrichtlinie  

Wenn Sie BitLocker mit der Geräte Konfigurationsrichtlinie konfigurieren, können Sie den Status der Richtlinie im InTune-Portal überprüfen.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Konfigurations profile** , und wählen Sie dann das Profil aus, das die BitLocker-Einstellungen enthält.

3. Nachdem Sie das Profil ausgewählt haben, das Sie anzeigen möchten, wählen Sie **Geräte Status**aus. Dem Profil zugewiesene Geräte werden aufgelistet, und die Spalte *Gerätestatus* zeigt an, ob ein Gerät das Profil erfolgreich bereitgestellt hat.

Beachten Sie, dass es eine Verzögerung zwischen einem Gerät, das eine BitLocker-Richtlinie empfängt, und dem vollständig verschlüsselten Laufwerk geben kann.  

### <a name="use-control-panel-on-the-client"></a>Verwenden der Systemsteuerung auf dem Client  

Auf einem Gerät mit aktiviertem BitLocker und verschlüsseltem Laufwerk können Sie den BitLocker-Status in der Systemsteuerung für Geräte anzeigen. Öffnen Sie auf dem Gerät die System **Steuerung** > **System-und Sicherheits** > **BitLocker-Laufwerkverschlüsselung**. Die Bestätigung wird angezeigt, wie in der folgenden Abbildung dargestellt.  

![BitLocker ist in der Systemsteuerung aktiviert.](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>Verwenden Sie eine Eingabeaufforderung.  

Starten Sie auf einem Gerät mit aktiviertem BitLocker und verschlüsseltem Laufwerk die Eingabeaufforderung mit Administrator Anmelde Informationen, und führen Sie dann `manage-bde -status`aus. Die Ergebnisse entsprechen in etwa dem folgenden Beispiel:  
![ein Ergebnis des Status Befehls](./media/troubleshooting-bitlocker-policies/command.png)

Im Beispiel gilt:

- **BitLocker-Schutz** ist **on**
- Der **verschlüsselte Prozentsatz** beträgt **100%** .
- Die **Verschlüsselungsmethode** ist **XTS-AES 256**

Sie können auch die **Schlüssel** Schutzvorrichtungen überprüfen, indem Sie den folgenden Befehl ausführen:

```cmd
Manage-bde -protectors -get c:
```

Oder mit PowerShell:

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>Überprüfen Sie die Konfiguration der Geräte Registrierungsschlüssel.

Nachdem die BitLocker-Richtlinie erfolgreich auf einem Gerät bereitgestellt wurde, können Sie den folgenden Registrierungsschlüssel auf dem Gerät anzeigen, auf dem Sie die Konfiguration der BitLocker-Einstellungen überprüfen können: *HKEY_LOCAL_MACHINE \software\microsoft\policymanager\current\device\bitlocker*. Beispiel:

![BitLocker-Registrierungsschlüssel](./media/troubleshooting-bitlocker-policies/registry.png)

Diese Werte werden vom BitLocker-CSP konfiguriert. Überprüfen Sie, ob die Werte der Schlüssel mit den Einstellungen übereinstimmen, die in der Quelle ihrer InTune-Windows-Verschlüsselungs Richtlinie angegeben sind. Weitere Informationen zu den einzelnen Einstellungen finden Sie unter [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

> [!NOTE]
> Der Windows-Ereignisanzeige enthält außerdem verschiedene Informationen zu BitLocker. Hier sind zu viele Auflistungs Möglichkeiten, aber durchsuchen nach **BitLocker-API** erhalten Sie viele nützliche Informationen.

### <a name="check-the-mdm-diagnostics-report"></a>Überprüfen des MDM-Diagnose Berichts

Auf einem Gerät, das BitLocker aktiviert hat, können Sie einen MDM-Diagnosebericht vom Zielgerät generieren und anzeigen, um zu bestätigen, dass die BitLocker-Richtlinie vorhanden ist. Wenn Sie die Richtlinien Einstellungen im Bericht sehen, ist dies ein weiterer Hinweis darauf, dass die Richtlinie erfolgreich bereitgestellt wurde. Das *Microsoft Hilfe* -Video unter folgendem Link erläutert, wie ein MDM-Diagnosebericht von einem Windows-Gerät erfasst wird.

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

Wenn Sie den MDM-Diagnosebericht analysieren, kann der Inhalt zuerst etwas verwirrend erscheinen. Es folgt ein Beispiel, das zeigt, wie Sie die im Bericht aufgeführten Einstellungen mit den Einstellungen in einer Richtlinie korrelieren:

![Beispiel für MDM-Diagnosebericht](./media/troubleshooting-bitlocker-policies/report.png)

Das Ausgabe Ergebnis zeigt die Werte, die den Werten aus der BitLocker-Richtlinie entsprechen:

![Ausgabe Ergebnis zeigt die Werte ](./media/troubleshooting-bitlocker-policies/output.png)

Ausgabe Ergebnisse der MDM-Diagnose:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

Sie können auf die [BitLocker-CSP-Dokumentation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) verweisen, um zu sehen, was jeder Wert bedeutet. In diesem Beispiel wird ein Ausschnitt in der folgenden Abbildung freigegeben.

![Zwecke von Werten](./media/troubleshooting-bitlocker-policies/shared-example.png)

Ebenso werden alle Werte angezeigt, und Sie können Sie über den BitLocker-CSP-Link überprüfen.

> [!TIP]
> Der primäre Zweck des MDM-Diagnose Berichts besteht darin, Microsoft-Support bei der Behebung von Problemen zu unterstützen. Wenn Sie eine Supportanfrage für InTune eröffnen und das Problem mit Windows-Clients verbunden ist, ist es immer ratsam, diesen Bericht zu erfassen und in Ihre Supportanfrage einzubeziehen.

## <a name="troubleshooting-bitlocker-policy"></a>Problembehandlung bei BitLocker

Sie sollten jetzt eine gute Idee haben, zu überprüfen, ob die BitLocker-Richtlinie erfolgreich von InTune bereitgestellt wurde. Dadurch wird die BitLocker-Konfiguration für den BitLocker-CSP in Windows durchgeführt.

**Die Richtlinie kann das Gerät nicht erreichen,** Wenn Ihre InTune-Richtlinie in keiner Kapazität vorhanden ist:

- **Ist das Gerät ordnungsgemäß bei Microsoft Intune registriert?** Falls nicht, müssen Sie dies beheben, bevor Sie eine Problembehandlung für bestimmte Richtlinien durchsetzen. Hilfe zur Problembehandlung bei Problemen mit der Windows-Registrierung finden Sie [hier](../enrollment/troubleshoot-windows-enrollment-errors.md).

- **Ist auf dem Gerät eine aktive Netzwerkverbindung vorhanden?** Wenn sich das Gerät im Flugzeug Modus befindet oder ausgeschaltet ist oder wenn der Benutzer das Gerät an einem Speicherort ohne Dienst hat, wird die Richtlinie erst übermittelt oder angewendet, wenn die Netzwerkverbindung wieder hergestellt ist.

- **Wurde die BitLocker-Richtlinie für den richtigen Benutzer oder die richtige Gerätegruppe bereitgestellt?** Überprüfen Sie, ob der richtige Benutzer oder das richtige Gerät Mitglied der Gruppen ist, die Sie als Ziel haben.

Die **Richtlinie ist vorhanden, aber nicht alle Einstellungen wurden erfolgreich konfiguriert** : Wenn Ihre InTune-Richtlinie das Gerät erreicht, aber nicht alle Konfigurationen festgelegt sind:

- **Tritt bei der Bereitstellung der gesamten Richtlinie ein Fehler auf, oder handelt es sich nur um bestimmte Einstellungen, die nicht zutreffen?** Wenn Sie ein Szenario haben, in dem nur einige Richtlinien Einstellungen zutreffen, überprüfen Sie die folgenden Überlegungen:

  1. **Nicht alle BitLocker-Einstellungen werden in allen Windows-Versionen unterstützt**.
     Die Richtlinie wird als einzelne Einheit auf ein Gerät Herunterskalieren. Wenn also einige Einstellungen zutreffen und andere nicht, können Sie sicher sein, dass die Richtlinie selbst empfangen wird. In diesem Szenario ist es möglich, dass die Windows-Version auf dem Gerät die problematischen Einstellungen nicht unterstützt. Ausführliche Informationen zu den Versions Anforderungen für die einzelnen Einstellungen finden Sie unter [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) in der Windows-Dokumentation.

  2. **BitLocker wird auf sämtlichen Hardware nicht unterstützt**.
     Auch wenn Sie über die richtige Version von Windows verfügen, ist es möglich, dass die zugrunde liegende Gerätehardware die Anforderungen für die BitLocker-Verschlüsselung nicht erfüllt. Die [Systemanforderungen für BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) finden Sie in der Windows-Dokumentation. die wichtigsten Aspekte, die überprüft werden müssen, ist, dass das Gerät über einen kompatiblen TPM-Chip (1,2 oder höher) und ein Trusted Computing Group (TCG)-kompatibles BIOS oder eine UEFI-Firmware verfügt.

**Beispieluntersuchung**

- Sie stellen eine BitLocker-Richtlinie auf einem Windows 10-Gerät bereit, und die Einstellung **Geräte verschlüsseln** zeigt den Status **Fehler** im Portal an.

- Wie der Name bereits vermuten lässt, kann ein Administrator mit dieser Einstellung festlegen, dass die Verschlüsselung mithilfe von *BitLocker > Geräteverschlüsselung*aktiviert werden muss. Mithilfe der zuvor erwähnten Tipps zur Problembehandlung überprüfen Sie zuerst den MDM-Diagnosebericht. Der Bericht bestätigt, dass die richtige Richtlinie auf dem Gerät bereitgestellt wurde:

  ![Bericht bestätigt, dass die richtige Richtlinie auf dem Gerät bereitgestellt wird](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- Außerdem überprüfen Sie, ob die Registrierung erfolgreich war:

  ![Der Registrierungs Wert "Requirements ddeviceencryption" zeigt 1 an.](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- Überprüfen Sie als nächstes den Status von TPM mithilfe von PowerShell, und stellen Sie fest, dass TPM auf dem Gerät nicht verfügbar ist:

  ![Überprüfen des TPM-Status mithilfe von PowerShell](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- Da BitLocker auf TPM basiert, können Sie feststellen, dass BitLocker aufgrund eines Problems mit InTune oder der Richtlinie nicht fehlschlägt, sondern dass das Gerät selbst keinen TPM-Chip hat oder dass TPM im BIOS deaktiviert ist.

  Als zusätzlichen Tipp können Sie das gleiche in den Windows-Ereignisanzeige unter **Anwendungs-und Dienst Protokoll** > **Windows** > **BitLocker-API**bestätigen. Im Ereignisprotokoll der **BitLocker-API** finden Sie die Ereignis-ID 853, die besagt, dass TPM nicht verfügbar ist:

  ![Ereignis-ID 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > Sie können auch den TPM-Status überprüfen, indem Sie **TPM. msc** auf dem Gerät ausführen.

## <a name="summary"></a>Zusammenfassung

Wenn Sie Probleme mit der BitLocker-Richtlinie in InTune beheben und sicherstellen können, dass die Richtlinie das gewünschte Gerät erreicht, ist sicherzustellen, dass das Problem nicht direkt mit InTune verknüpft ist. Das Problem ist wahrscheinlich ein Problem mit dem Windows-Betriebssystem oder der Hardware. In diesem Fall sollten Sie in anderen Bereichen wie der TPM-Konfiguration oder UEFI und dem sicheren Start suchen.

## <a name="next-steps"></a>Nächste Schritte  

Im folgenden finden Sie weitere Ressourcen, die Ihnen bei der Arbeit mit BitLocker helfen können:

- [BitLocker-Produktdokumentation](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker-Systemanforderungen](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [BitLocker: Häufig gestellte Fragen](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [BitLocker-CSP-Dokumentation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Richtlinien Einstellungen für die Windows-Verschlüsselung in InTune](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [Hardware unabhängige automatische BitLocker-Verschlüsselung mit Aad/MDM](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [CSP-Richtlinie für die BitLocker-Verschlüsselung auf automatischen Pilot Geräten](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Exemplarische Vorgehensweise zum Erstellen und Bereitstellen von BitLocker-Richtlinien mit](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)