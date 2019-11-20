---
title: Hinzufügen von PowerShell-Skripts zu Windows 10-Geräten in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie PowerShell-Skripts, und führen Sie diese aus, weisen Sie der Skriptrichtlinie Azure Active Directory-Gruppen zu, überwachen Sie Skripts mit Berichten, und erfahren Sie, wie Sie hinzugefügte Skripte von Windows 10-Geräten in Microsoft Intune löschen. Außerdem finden Sie einige häufige Probleme und Lösungen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d73d28f34258bce99199731579969604c0a3d97
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059721"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>Verwenden von PowerShell-Skripts auf Windows 10-Geräten in Intune

Verwenden Sie die Verwaltungserweiterung von Microsoft Intune, um PowerShell-Skripts in Intune für die Ausführung auf Windows 10-Geräten hochzuladen. Die Verwaltungserweiterung verbessert die mobile Geräteverwaltung (Mobile Device Management, MDM) von Windows 10 und erleichtert den Wechsel zu einer modernen Verwaltung.

Diese Funktion gilt für:

- Windows 10 und höher

## <a name="move-to-modern-management"></a>Wechseln zur modernen Verwaltung

Die individuelle Datenverarbeitung durchläuft eine digitale Transformation. Die klassische, traditionelle IT konzentriert sich auf eine einzelne Geräteplattform, unternehmenseigene Geräte, Benutzer, die vom Büro aus arbeiten und eine Vielzahl von manuellen, reaktiven IT-Prozessen. Am modernen Arbeitsplatz werden viele benutzer- und unternehmenseigene Plattformen verwendet. Dadurch können Benutzer von überall aus arbeiten, und automatisierte und proaktive IT-Prozesse werden ermöglicht.

MDM-Dienste wie Microsoft Intune können mobile Geräte und Desktopgeräte verwalten, die Windows 10 ausführen. Der integrierte Windows 10-Verwaltungsclient kommuniziert mit Intune, um Aufgaben für die Unternehmensverwaltung auszuführen. Es gibt einige Aufgaben, die Sie ggf. ausführen müssen, z.B. erweiterte Gerätekonfiguration und Problembehandlung. Für die Verwaltung von Win32-Apps können Sie das Feature [Win32-App-Verwaltung](app-management.md) auf Ihren Windows 10-Geräten verwenden.

Die Intune-Verwaltungserweiterung ergänzt die integrierten MDM-Features für Windows 10. Sie können PowerShell-Skripts für die Ausführung auf Windows 10-Geräten erstellen. Erstellen Sie z. B. ein PowerShell-Skript für erweiterte Gerätekonfigurationen. Laden Sie dann das Skript in Intune hoch, weisen Sie es einer Azure Active Directory-Gruppe zu, und führen Sie es anschließend aus. Sie können dann den Ausführungsstatus des Skripts von Anfang bis Ende überwachen.

## <a name="prerequisites"></a>Voraussetzungen

Für die Intune-Verwaltungserweiterung sind folgende Voraussetzungen erforderlich. Wenn diese Voraussetzungen erfüllt sind, wird die Intune-Verwaltungserweiterung automatisch installiert, sobald dem Benutzer oder Gerät ein PowerShell-Skript oder eine Win32-App zugewiesen ist.

- Geräte mit Windows 10, Version 1607 oder höher: Wenn das Gerät mithilfe der [automatischen Massenregistrierung](../enrollment/windows-bulk-enroll.md) registriert wurde, muss es mindestens Windows 10, Version 1703 ausführen. Die Intune-Verwaltungserweiterung wird unter Windows 10 im S Modus nicht unterstützt, da im S Modus keine Apps ausgeführt werden können, die nicht aus dem Store stammen. 
  
- Mit Azure Active Directory (Azure AD) verknüpfte Geräte, einschließlich:  
  
  - Mit Azure AD Hybrid verknüpfte Geräte: Geräte, die mit Azure Active Directory und einer lokalen Azure Active Directory-Instanz verknüpft sind. Weitere Informationen finden Sie unter [Anleitung: Planen der Implementierung einer Azure Active Directory-Hybrideinbindung](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan).

- Bei Intune registrierte Geräte, einschließlich:

  - Geräte, die in einer Gruppenrichtlinie registriert sind – weitere Informationen finden Sie unter [Enroll a Windows 10 device automatically using Group Policy (Automatische Registrierung von Windows 10-Geräten mithilfe von Gruppenrichtlinien)](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy).
  
  - Geräte, die folgendermaßen manuell in Intune registriert wurden:
  
    - Die [automatische Registrierung bei Intune](../enrollment/quickstart-setup-auto-enrollment.md) ist in Azure AD aktiviert. Ein Benutzer meldet sich mit einem lokalen Benutzerkonto beim Gerät an, bindet das Gerät manuell in Azure AD ein und meldet sich dann mit seinem Azure AD-Konto beim Gerät an.
    
    ODER  
    
    - Über die Anmeldung des Benutzers auf dem Gerät mithilfe seines Azure AD-Kontos und der anschließenden Registrierung bei Intune.

  - Gemeinsam verwaltete Geräte, die Configuration Manager und Intune verwenden – Stellen Sie sicher, dass die Workload **Client-Apps** auf **Pilot Intune** oder **Intune** festgelegt ist. Weitere Informationen finden Sie in den folgenden Artikeln: 
  
    - [Was ist Co-Verwaltung?](https://docs.microsoft.com/sccm/comanage/overview) 
    - [Client-Apps-Workload](https://docs.microsoft.com/sccm/comanage/workloads#client-apps)
    - [Verschieben von Configuration Manager-Workloads zu Intune](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads)
  
> [!TIP]
> Stellen Sie sicher, dass die Geräte in Azure AD [eingebunden](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) sind. Geräte, die bei Azure AD nur [registriert](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) sind, erhalten Ihre Skripts nicht.

## <a name="create-a-script-policy-and-assign-it"></a>Erstellen und Zuweisen einer Skriptrichtlinie

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonfiguration** > **PowerShell-Skripts** > **Hinzufügen**.

    ![Hinzufügen und Verwenden von PowerShell-Skripts in Microsoft Intune](./media/intune-management-extension/mgmt-extension-add-script.png)

3. Geben Sie unter **Basics** (Grundlegende Einstellungen) die folgenden Eigenschaften ein, und klicken Sie auf **Weiter**:
    - **Name**: Geben Sie einen Namen für das PowerShell-Skript ein. 
    - **Beschreibung**: Geben Sie eine Beschreibung für das PowerShell-Skript ein. Diese Einstellung ist optional, wird jedoch empfohlen.
4. Geben Sie unter **Skripteinstellungen** die folgenden Eigenschaften ein, und klicken Sie auf **Weiter**:
    - **Skriptspeicherort:** Wechseln Sie zum PowerShell-Skript. Das Skript muss kleiner als 200 KB (ASCII) sein.
    - **Dieses Skript mit den Anmeldeinformationen des angemeldeten Benutzers ausführen:** Klicken Sie auf **Ja**, um das Skript mit den Anmeldeinformationen des Benutzers auf dem Gerät auszuführen. Klicken Sie auf **Nein** (Standard), um das Skript im Systemkontext auszuführen. Viele Administratoren entscheiden sich für die Option **Ja**. Klicken Sie auf **Nein**, wenn das Skript nicht im Systemkontext ausgeführt werden muss.
    - **Skriptsignaturprüfung erzwingen:** Klicken Sie auf **Ja**, wenn das Skript von einem vertrauenswürdigen Herausgeber signiert werden muss. Klicken Sie auf **Nein** (Standard), wenn das Skript nicht signiert werden muss. 
    - **Skript in 64-Bit-Version des PowerShell-Hosts ausführen:** Klicken Sie auf **Ja**, um das Skript in einer 64-Bit-Version des PowerShell-Hosts auf einer 64-Bit-Clientarchitektur auszuführen. Wenn Sie auf **Nein** (Standard) klicken, wird das Skript in einer 32-Bit-Version des PowerShell-Hosts ausgeführt.

      Wenn Sie die Optionen **Ja** oder **Nein** auswählen, verwenden Sie die folgende Tabelle für neues und bereits bestehendes Richtlinienverhalten:

      | Skript in 64-Bit-Version des PowerShell-Hosts ausführen | Clientarchitektur | Neues PowerShell-Skript | Bereits bestehende PowerShell-Richtlinie |
      | --- | --- | --- | --- | 
      | Nein | 32 Bit  | 32-Bit-Version des PowerShell-Hosts unterstützt | Wird nur in einer 32-Bit-Version des PowerShell-Hosts ausgeführt, der sowohl auf 32-Bit- als auch auf 64-Bit-Architekturen funktioniert |
      | Ja | 64-Bit | Wird nur in einer 64-Bit-Version des PowerShell-Hosts für 64-Bit-Architekturen verwendet. Wenn das Skript auf einer 32-Bit-Version ausgeführt wird, passiert dies in einer 32-Bit-Version des PowerShell-Hosts. | Führt das Skript in einer 32-Bit-Version des PowerShell-Hosts aus. Wenn diese Einstellung in „64-Bit“ geändert wird, wird das Skript in einer 64-Bit-Version des PowerShell-Hosts geöffnet (aber nicht ausgeführt) und meldet die Ergebnisse. Wenn das Skript auf einer 32-Bit-Version ausgeführt wird, passiert dies in einer 32-Bit-Version des PowerShell-Hosts. |

5. Klicken Sie auf **Bereichstags**. Bereichstags sind optional. Weitere Informationen dazu finden Sie unter [Use role-based access control (RBAC) and scope tags for distributed IT (Verwenden der rollenbasierten Zugriffssteuerung und Bereichsmarkierungen für verteilte IT)](../fundamentals/scope-tags.md).

    So fügen Sie Bereichstags hinzu:

    1. Klicken Sie auf **Bereichstags auswählen**, wählen Sie ein bereits vorhandenes Bereichstag aus der Liste aus, und klicken Sie auf **Auswählen**.

    2. Klicken Sie anschließend auf **Weiter**.

6. Klicken Sie auf **Zuweisungen** > **Select groups to include** (Gruppen auswählen, die hinzugefügt werden sollen). Dann wird eine vorhandene Liste mit Azure AD Gruppen angezeigt.

    1. Wählen Sie mindestens eine Gruppe aus, die die Benutzer enthält, deren Geräte das Skript erhalten sollen. Klicken Sie auf **Auswählen**. Die Gruppen, die Sie ausgewählt haben, werden in der Liste angezeigt und Ihrer Richtlinie zugeordnet.

        > [!NOTE]
        > PowerShell-Skripts in Intune können auf Azure AD-Gerätesicherheitsgruppen oder Azure AD-Benutzersicherheitsgruppen ausgerichtet werden.

    2. Wählen Sie **Weiter** aus.

        ![Zuweisen oder Bereitstellen eines PowerShell-Skripts an/für Gerätegruppen in Microsoft Intune](./media/intune-management-extension/mgmt-extension-assignments.png)

7. Unter **Überprüfen + hinzufügen** wird eine Zusammenfassung der Einstellungen angezeigt, die Sie konfiguriert haben. Klicken Sie auf **Hinzufügen**, um das Skript zu speichern. Dann wird die Richtlinie für die ausgewählten Gruppen bereitgestellt.

## <a name="important-considerations"></a>Wichtige Überlegungen

- Wenn Skripts auf den Benutzerkontext festgelegt sind und der Endbenutzer über Administratorrechte verfügt, wird das PowerShell-Skript standardmäßig mit Administratorrechten ausgeführt.

- Endbenutzer müssen sich nicht beim Gerät anmelden, um PowerShell-Skripts auszuführen.

- Der Intune-Client für die Verwaltungserweiterung überprüft Intune einmal pro Stunde und nach jedem Neustart auf neue Skripts oder Änderungen. Nachdem Sie die Richtlinie den Azure AD-Gruppen zugewiesen haben, wird das PowerShell-Skript ausgeführt, und die Ausführungsergebnisse werden berichtet. Das Skript wird nur einmal ausgeführt. Eine erneute Ausführung erfolgt nur, wenn eine Änderung am Skript oder der Richtlinie vorgenommen wird.

## <a name="monitor-run-status"></a>Überwachen des Ausführungsstatus

Sie können den Ausführungsstatus von PowerShell-Skripts für Benutzer und Geräte im Azure-Portal überwachen.

Wählen Sie unter **PowerShell-Skripts** das zu überwachende Skript aus, klicken Sie auf **Überwachen**, und wählen Sie anschließend einen der folgenden Berichte aus:

- **Gerätestatus**
- **Benutzerstatus**

## <a name="intune-management-extension-logs"></a>Protokolle zur Intune-Verwaltungserweiterung

Agentprotokolle auf dem Clientcomputer befinden sich in der Regel unter `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Sie können mit [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) diese Protokolldateien anzeigen. 

![Screenshot oder Beispiel-Agent-Protokolle von CMTrace in Microsoft Intune](./media/apps-win32-app-management/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>Löschen eines Skripts

Klicken Sie unter **PowerShell-Skripts** mit der rechten Maustaste auf das Skript, und klicken Sie dann auf **Löschen**.

## <a name="common-issues-and-resolutions"></a>Häufige Probleme und Lösungen

### <a name="issue-intune-management-extension-doesnt-download"></a>Problem: Die Intune-Verwaltungserweiterung kann nicht heruntergeladen werden

**Mögliche Lösungen:**

- Das Gerät ist nicht mit Azure AD verknüpft. Stellen Sie sicher, dass die Geräte die in diesem Artikel beschriebenen [Voraussetzungen](#prerequisites) erfüllen. 
- Den Gruppen, denen der Benutzer oder das Gerät angehört, sind keine PowerShell-Skripts oder Win32-Apps zugewiesen.
- Das Gerät kann sich nicht beim Intune-Dienst einchecken, da z. B. keine Internetverbindung besteht oder kein Zugriff auf den Windows-Pushbenachrichtigungsdienst möglich ist.
- Das Gerät befindet sich im S Modus. Die Intune-Verwaltungserweiterung wird auf Geräten nicht unterstützt, die im S Modus ausgeführt werden. 

Folgendermaßen können Sie feststellen, ob das Gerät automatisch registriert wird:

  1. Navigieren Sie zu **Einstellungen** > **Konten** > **Access work or school** (Zugriff auf Geschäfts-, Schul- oder Unikonto).
  2. Wählen Sie das verknüpfte Konto aus, und klicken Sie auf **Info**.
  3. Wählen Sie unter **Advanced Diagnostic Report** (Erweiterter Diagnosebericht) **Create Report** (Bericht erstellen) aus.
  4. Öffnen Sie `MDMDiagReport` in einem Webbrowser.
  5. Suchen Sie nach der Eigenschaft **MDMDeviceWithAAD**. Wenn diese Eigenschaft vorhanden ist, wird das Gerät automatisch registriert. Wenn diese Eigenschaft nicht vorhanden ist, wird das Gerät nicht automatisch registriert.

Unter [Aktivieren der automatischen Registrierung von Windows 10](../enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment) sind die erforderlichen Schritte für die Einrichtung der automatischen Registrierung in Intune aufgeführt.

### <a name="issue-powershell-scripts-do-not-run"></a>Problem: PowerShell-Skripts werden nicht ausgeführt

**Mögliche Lösungen:**

- Die PowerShell-Skripts werden nicht bei jeder Anmeldung ausgeführt. Sie werden in folgenden Fällen ausgeführt:

  - Wenn das Skript einem Gerät zugewiesen ist
  - Wenn Sie das Skript ändern, es hochladen und einem Benutzer oder Gerät zuweisen
  
    > [!TIP]
    > Bei der **Microsoft Intune-Verwaltungserweiterung** handelt es sich um einen Dienst, der wie die anderen Dienste in der Dienst-App (services.msc) auf dem Gerät ausgeführt wird. Nach dem Neustart eines Geräts startet ggf. auch dieser Dienst neu und überprüft, ob dem Intune-Dienst PowerShell-Skripts zugewiesen sind. Wenn die **Microsoft Intune-Verwaltungserweiterung** auf „Manuell“ festgelegt ist, startet der Dienst nach einem Neustart des Geräts möglicherweise nicht neu.

- Stellen Sie sicher, dass die Geräte [in Azure AD eingebunden](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) sind. Geräte, die nur in Ihren Arbeitsplatz oder Ihre Organisation eingebunden (also in Azure AD [registriert](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)) sind, erhalten die Skripts nicht.
- Der Client der Intune-Verwaltungserweiterung überprüft einmal pro Stunde, ob Änderungen im Skript oder in der Richtlinie in Intune vorliegen.
- Vergewissern Sie sich, dass die Intune-Verwaltungserweiterung nach `%ProgramFiles(x86)%\Microsoft Intune Management Extension` heruntergeladen wurde.
- Skripts werden nicht auf Surface Hub-Geräten oder unter Windows 10 im S Modus ausgeführt.
- Überprüfen Sie die Protokolle auf Fehler. Weitere Informationen zu Protokollen zur Intune-Verwaltungserweiterung [finden Sie hier](#intune-management-extension-logs).
- Stellen Sie gegen mögliche Probleme mit Berechtigungen sicher, dass die Eigenschaften des PowerShell-Skripts auf `Run this script using the logged on credentials` festgelegt werden. Überprüfen Sie auch, ob der angemeldete Benutzer über die erforderlichen Berechtigungen zum Ausführen des Skripts verfügt.

- Sie können Skriptprobleme folgendermaßen eingrenzen:

  - Überprüfen Sie die Konfiguration für die Ausführung von PowerShell auf Ihren Geräten. Weitere Informationen finden Sie unter [Set-ExecutionPolicy](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6).
  - Führen Sie über die Intune-Verwaltungserweiterung ein Beispielskript aus. Erstellen Sie zum Beispiel das Verzeichnis `C:\Scripts`, und erteilen Sie jedem Vollzugriff. Führen Sie das folgende Skript aus:

    ```powershell
    write-output "Script worked" | out-file c:\Scripts\output.txt
    ```

    Wenn dies erfolgreich ist, sollte eine Datei mit dem Namen „output.txt“ erstellt werden, die den Text „Script worked“ (Skript hat funktioniert) enthält.

  - Führen Sie die Skripts zum Testen der Skriptausführung ohne Intune im Systemkonto aus, indem Sie das Tool [psexec](https://docs.microsoft.com/sysinternals/downloads/psexec) lokal verwenden:

    `psexec -i -s`  
    
  - Wenn das Skript fälschlicherweise meldet, dass es erfolgreich ausgeführt wurde, wird AgentExecutor möglicherweise von Ihrem Antivirendienst in einer Sandbox ausgeführt. Das folgende Skript meldet in Intune grundsätzlich einen Fehler. Als Test können Sie dieses Skript verwenden:
  
    ```powershell
    Write-Error -Message "Forced Fail" -Category OperationStopped
    mkdir "c:\temp" 
    echo "Forced Fail" | out-file c:\temp\Fail.txt
    ```

    Wenn das Skript einen Erfolg meldet, überprüfen Sie `AgentExecutor.log`, um die Fehlerausgabe zu bestätigen. Wenn das Skript ausgeführt wird, sollte die Länge > 2 sein.

  - Um die ERROR- und OUTPUT-Dateien zu erfassen, führt der folgende Codeausschnitt das Skript über AgentExecutor für PSx86 (`C:\Windows\SysWOW64\WindowsPowerShell\v1.0`) aus. Die Protokolle werden zur Überprüfung aufbewahrt. Beachten Sie, dass die Intune-Verwaltungserweiterung die Protokolle nach der Skriptausführung bereinigt:
  
    ```powershell
    $scriptPath = read-host "Enter the path to the script file to execute"
    $logFolder = read-host "Enter the path to a folder to output the logs to"
    $outputPath = $logFolder+"\output.output"
    $errorPath =  $logFolder+"\error.error"
    $timeoutPath =  $logFolder+"\timeout.timeout"
    $timeoutVal = 60000 
    $PSFolder = "C:\Windows\SysWOW64\WindowsPowerShell\v1.0"
    $AgentExec = "C:\Program Files (x86)\Microsoft Intune Management Extension\agentexecutor.exe"
    &$AgentExec -powershell  $scriptPath $outputPath $errorPath $timeoutPath $timeoutVal $PSFolder 0 0
    ```

## <a name="next-steps"></a>Nächste Schritte

[Überwachung](../device-profile-monitor.md) und [Problembehandlung](../device-profile-troubleshoot.md) Ihrer Profile.
