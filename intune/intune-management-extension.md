---
title: Hinzufügen von PowerShell-Skripts zu Windows 10-Geräten in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie PowerShell-Skripts, und führen Sie diese aus, weisen Sie der Skriptrichtlinie Azure Active Directory-Gruppen zu, überwachen Sie Skripts mit Berichten, und erfahren Sie, wie Sie hinzugefügte Skripte von Windows 10-Geräten in Microsoft Intune löschen. Außerdem finden Sie einige häufige Probleme und Lösungen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66a23b75913f6465064a988bd8f2ba9c2b4c36d6
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61514119"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>Verwenden von PowerShell-Skripts auf Windows 10-Geräten in Intune

Verwenden Sie die Verwaltungserweiterung von Microsoft Intune, um PowerShell-Skripts in Intune für die Ausführung auf Windows 10-Geräten hochzuladen. Die Verwaltungserweiterung verbessert die mobile Geräteverwaltung (Mobile Device Management, MDM) von Windows 10 und erleichtert den Wechsel zu einer modernen Verwaltung.

Diese Funktion gilt für:

- Windows 10 und höher

## <a name="move-to-modern-management"></a>Wechseln zur modernen Verwaltung

Die individuelle Datenverarbeitung durchläuft eine digitale Transformation. Die klassische, traditionelle IT konzentriert sich auf eine einzelne Geräteplattform, unternehmenseigene Geräte, Benutzer, die vom Büro aus arbeiten und eine Vielzahl von manuellen, reaktiven IT-Prozessen. Am modernen Arbeitsplatz werden viele benutzer- und unternehmenseigene Plattformen verwendet. Dadurch können Benutzer von überall aus arbeiten, und automatisierte und proaktive IT-Prozesse werden ermöglicht.

MDM-Dienste wie Microsoft Intune können mobile Geräte und Desktopgeräte verwalten, die Windows 10 ausführen. Der integrierte Windows 10-Verwaltungsclient kommuniziert mit Intune, um Aufgaben für die Unternehmensverwaltung auszuführen. Es gibt einige Aufgaben, die Sie ggf. ausführen müssen, z.B. erweiterte Gerätekonfiguration und Problembehandlung. Für die Verwaltung von Win32-Apps können Sie das Feature [Win32-App-Verwaltung](apps-win32-app-management.md) auf Ihren Windows 10-Geräten verwenden.

Die Intune-Verwaltungserweiterung ergänzt die integrierten MDM-Features für Windows 10. Sie können PowerShell-Skripts für die Ausführung auf Windows 10-Geräten erstellen. Sie können beispielsweise ein PowerShell-Skript erstellen, das erweiterte Gerätekonfigurationen ausführt, das Skript in Intune hochlädt, es einer Azure Active Directory-Gruppe (AD) zuweist und ausführt. Sie können dann den Ausführungsstatus des Skripts von Anfang bis Ende überwachen.

## <a name="prerequisites"></a>Voraussetzungen

Für die Intune-Verwaltungserweiterung sind folgende Voraussetzungen erforderlich:

- Die Geräte müssen mit Azure AD verknüpft oder für diesen Dienst registriert sowie für die [automatische Registrierung](quickstart-setup-auto-enrollment.md) bei Azure AD und Intune konfiguriert sein. Die Intune-Verwaltungserweiterung unterstützt Geräte, die mit Azure AD und hybriden Azure AD-Domänen verknüpft sind, sowie gemeinsam verwaltete registrierte Windows-Geräte.
- Geräte müssen Windows 10 Version 1607 oder höher ausführen.
- Der Agent für die Intune-Verwaltungserweiterung wird installiert, wenn ein PowerShell-Skript oder eine Win32-App an einen Benutzer oder eine Gerätesicherheitsgruppe bereitgestellt wird.

## <a name="create-a-script-policy"></a>Erstellen einer Skriptrichtlinie 

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **PowerShell-Skripts** > **Hinzufügen**.
3. Geben Sie die folgenden Eigenschaften ein:
    - **Name**: Geben Sie einen Namen für das PowerShell-Skript ein. 
    - **Beschreibung**: Geben Sie eine Beschreibung für das PowerShell-Skript ein. Diese Einstellung ist optional, wird jedoch empfohlen. 
    - **Skriptspeicherort:** Wechseln Sie zum PowerShell-Skript. Das Skript muss kleiner als 200 KB (ASCII) sein.
4. Klicken Sie auf **Konfigurieren**, und geben Sie die folgenden Eigenschaften ein:
    - **Dieses Skript mit den Anmeldeinformationen des angemeldeten Benutzers ausführen:** Klicken Sie auf **Ja**, um das Skript mit den Anmeldeinformationen des Benutzers auf dem Gerät auszuführen. Klicken Sie auf **Nein** (Standard), um das Skript im Systemkontext auszuführen. Viele Administratoren entscheiden sich für die Option **Ja**. Klicken Sie auf **Nein**, wenn das Skript nicht im Systemkontext ausgeführt werden muss.
    - **Skriptsignaturprüfung erzwingen:** Klicken Sie auf **Ja**, wenn das Skript von einem vertrauenswürdigen Herausgeber signiert werden muss. Klicken Sie auf **Nein** (Standard), wenn das Skript nicht signiert werden muss. 
    - **Skript in 64-Bit-Version des PowerShell-Hosts ausführen:** Klicken Sie auf **Ja**, um das Skript in einer 64-Bit-Version des PowerShell-Hosts auf einer 64-Bit-Clientarchitektur auszuführen. Wenn Sie auf **Nein** (Standard) klicken, wird das Skript in einer 32-Bit-Version des PowerShell-Hosts ausgeführt.

      Wenn Sie die Optionen **Ja** oder **Nein** auswählen, verwenden Sie die folgende Tabelle für neues und bereits bestehendes Richtlinienverhalten:

      | Skript in 64-Bit-Version des PowerShell-Hosts ausführen | Clientarchitektur | Neues PowerShell-Skript | Bereits bestehende PowerShell-Richtlinie |
      | --- | --- | --- | --- | 
      | Nein | 32 Bit  | 32-Bit-Version des PowerShell-Hosts unterstützt | Wird nur in einer 32-Bit-Version des PowerShell-Hosts ausgeführt, der sowohl auf 32-Bit- als auch auf 64-Bit-Architekturen funktioniert |
      | Ja | 64-Bit | Wird nur in einer 64-Bit-Version des PowerShell-Hosts für 64-Bit-Architekturen verwendet. Wenn das Skript auf einer 32-Bit-Version ausgeführt wird, passiert dies in einer 32-Bit-Version des PowerShell-Hosts. | Führt das Skript in einer 32-Bit-Version des PowerShell-Hosts aus. Wenn diese Einstellung in „64-Bit“ geändert wird, wird das Skript in einer 64-Bit-Version des PowerShell-Hosts geöffnet (aber nicht ausgeführt) und meldet die Ergebnisse. Wenn das Skript auf einer 32-Bit-Version ausgeführt wird, passiert dies in einer 32-Bit-Version des PowerShell-Hosts. |

    ![Hinzufügen und Verwenden von PowerShell-Skripts in Microsoft Intune](./media/mgmt-extension-add-script.png)
5. Klicken Sie auf **OK** > **Erstellen**, um das Skript zu speichern.

## <a name="assign-the-policy"></a>Zuweisen der Richtlinie

1. Wählen Sie unter **PowerShell-Skripts** das zuzuweisende Skript aus, und klicken Sie dann auf **Verwalten** > **Zuweisungen**.

    ![Zuweisen oder Bereitstellen eines PowerShell-Skripts an/für Gerätegruppen in Microsoft Intune](./media/mgmt-extension-assignments.png)

2. Klicken Sie auf **Gruppen auswählen**, um verfügbare Azure AD-Gruppen aufzulisten. 
3. Wählen Sie mindestens eine Gruppe aus, die die Benutzer enthält, deren Geräte das Skript erhalten sollen. Klicken Sie auf **Auswählen**, um die Richtlinie den ausgewählten Gruppen zuzuweisen.

> [!NOTE]
> - Endbenutzer müssen sich nicht beim Gerät anmelden, um PowerShell-Skripts auszuführen.
> - PowerShell-Skripts in Intune können auf Azure AD-Gerätesicherheitsgruppen ausgerichtet werden.
> - PowerShell-Skripts in Intune können auf Azure AD-Benutzersicherheitsgruppen ausgerichtet werden.

Der Intune-Verwaltungserweiterungsclient überprüft Intune einmal pro Stunde und nach jedem Neustart auf neue Skripts oder Änderungen. Nachdem Sie die Richtlinie den Azure AD-Gruppen zugewiesen haben, wird das PowerShell-Skript ausgeführt, und die Ausführungsergebnisse werden berichtet. Das Skript wird nur einmal ausgeführt. Eine erneute Ausführung erfolgt nur, wenn eine Änderung am Skript oder der Richtlinie vorgenommen wird.

## <a name="monitor-run-status"></a>Überwachen des Ausführungsstatus

Sie können den Ausführungsstatus von PowerShell-Skripts für Benutzer und Geräte im Azure-Portal überwachen.

Wählen Sie unter **PowerShell-Skripts** das zu überwachende Skript aus, klicken Sie auf **Überwachen**, und wählen Sie anschließend einen der folgenden Berichte aus:

- **Gerätestatus**
- **Benutzerstatus**

## <a name="troubleshoot-scripts"></a>Behandeln von Problemen mit Skripts

Agentprotokolle auf dem Clientcomputer befinden sich in der Regel unter `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Sie können mit [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) diese Protokolldateien anzeigen. 

![Screenshot oder Beispiel-Agent-Protokolle von CMTrace in Microsoft Intune](./media/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>Löschen eines Skripts

Klicken Sie unter **PowerShell-Skripts** mit der rechten Maustaste auf das Skript, und klicken Sie dann auf **Löschen**.

## <a name="common-issues-and-resolutions"></a>Häufige Probleme und Lösungen

Die PowerShell-Skripts werden nicht bei jeder Anmeldung ausgeführt. Sie werden nur nach Neustarts ausgeführt oder wenn der Dienst **Microsoft Intune-Verwaltungserweiterung** neu gestartet wird. Der Intune-Verwaltungserweiterungsclient überprüft einmal pro Stunde, ob es Änderungen im Skript oder in der Richtlinie in Intune gibt.

#### <a name="issue-intune-management-extension-doesnt-download"></a>Problem: Die Intune-Verwaltungserweiterung kann nicht heruntergeladen werden

**Mögliche Lösungen:**

- Stellen Sie sicher, dass die Geräte automatisch in Azure AD registriert werden. Gehen Sie dazu auf dem Gerät wie folgt vor: 

  1. Navigieren Sie zu **Einstellungen** > **Konten** > **Access work or school** (Zugriff auf Geschäfts-, Schul- oder Unikonto).
  2. Wählen Sie das verknüpfte Konto aus, und klicken Sie auf **Info**.
  3. Wählen Sie unter **Advanced Diagnostic Report** (Erweiterter Diagnosebericht) **Create Report** (Bericht erstellen) aus.
  4. Öffnen Sie den `MDMDiagReport` in einem Webbrowser, und navigieren Sie zum Abschnitt **Enrolled configuration sources** (Registrierte Konfigurationsquellen).
  5. Suchen Sie nach der Eigenschaft **MDMDeviceWithAAD**. Wenn diese Eigenschaft nicht vorhanden ist, wird Ihr Gerät nicht automatisch registriert.

    Das [Aktivieren der automatischen Registrierung von Windows 10](windows-enroll.md#enable-windows-10-automatic-enrollment) umfasst diese Schritte.

#### <a name="issue-powershell-scripts-do-not-run"></a>Problem: PowerShell-Skripts werden nicht ausgeführt

**Mögliche Lösungen:**

- Vergewissern Sie sich, dass die Intune-Verwaltungserweiterung nach `%ProgramFiles(x86)%\Microsoft Intune Management Extension` heruntergeladen wurde.
- Skripts werden nicht auf Surface Hubs ausgeführt.
- Überprüfen Sie die Protokolle unter `\ProgramData\Microsoft\IntuneManagementExtension\Logs` auf Fehler.
- Stellen Sie gegen mögliche Probleme mit Berechtigungen sicher, dass die Eigenschaften des PowerShell-Skripts auf `Run this script using the logged on credentials` festgelegt werden. Überprüfen Sie auch, ob der angemeldete Benutzer über die erforderlichen Berechtigungen zum Ausführen des Skripts verfügt.
- Führen Sie ein Beispielskript aus, um Skriptprobleme zu isolieren. Erstellen Sie zum Beispiel das Verzeichnis `C:\Scripts`, und erteilen Sie jedem Vollzugriff. Führen Sie das folgende Skript aus:

  ```powershell
  write-output "Script worked" | out-file c:\Scripts\output.txt
  ```

  Wenn dies erfolgreich ist, sollte eine Datei mit dem Namen „output.txt“ erstellt werden, die den Text „Script worked“ (Skript hat funktioniert) enthält.

- Führen Sie zum Testen der Skriptausführung ohne Intune die Skripts im Systemkontext aus, indem Sie das Tool [psexec](https://docs.microsoft.com/sysinternals/downloads/psexec) lokal verwenden:

  `psexec -i -s`

## <a name="next-steps"></a>Nächste Schritte

[Überwachung](device-profile-monitor.md) und [Problembehandlung](device-profile-troubleshoot.md) Ihrer Profile.
