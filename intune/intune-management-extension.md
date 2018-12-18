---
title: Verwalten von PowerShell-Skripts in Microsoft Intune für Windows 10-Geräte – Azure | Microsoft-Dokumentation
description: Fügen Sie PowerShell-Skripts hinzu, weisen Sie Azure Active Directory-Gruppen Skriptrichtlinien zu, überwachen Sie Skripts mit Berichten, und erfahren Sie, wie Sie hinzugefügte Skripte auf Windows 10-Geräten in Microsoft Intune löschen. Außerdem finden Sie einige häufige Probleme und Lösungen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 063a5cbbe18efc5c406c9dc7f2fa40d614b2e48a
ms.sourcegitcommit: d3b1e3fffd3e0229292768c7ef634be71e4736ae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2018
ms.locfileid: "52860961"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Verwalten von PowerShell-Skripts in Intune für Windows 10-Geräte

Verwenden Sie die Verwaltungserweiterung von Intune, um PowerShell-Skripts in Intune für die Ausführung auf Windows 10-Geräten hochzuladen. Die Verwaltungserweiterung verbessert die mobile Geräteverwaltung (Mobile Device Management, MDM) von Windows 10 und erleichtert den Wechsel zu einer modernen Verwaltung.

## <a name="moving-to-modern-management"></a>Wechsel zu moderner Verwaltung

Die individuelle Datenverarbeitung durchläuft eine digitale Transformation. Die klassische, traditionelle IT konzentriert sich auf eine einzelne Geräteplattform, unternehmenseigene Geräte, Benutzer, die vom Büro aus arbeiten und eine Vielzahl von manuellen, reaktiven IT-Prozessen. Am modernen Arbeitsplatz werden viele benutzer- und unternehmenseigene Plattformen verwendet. Dadurch können Benutzer von überall aus arbeiten, und automatisierte und proaktive IT-Prozesse werden ermöglicht.

MDM-Dienste wie Microsoft Intune können mobile Geräte und Desktopgeräte verwalten, die Windows 10 ausführen. Der integrierte Windows 10-Verwaltungsclient kommuniziert mit Intune, um Aufgaben für die Unternehmensverwaltung auszuführen. Einige Funktionen, die Sie möglicherweise benötigen, wie die erweiterte Gerätekonfiguration, die Problembehandlung und eine ältere Win32-App-Verwaltung sind derzeit nicht für die mobile Geräteverwaltung für Windows 10 verfügbar. Für diese Funktionen können Sie den Intune-Softwareclient auf Ihren Windows 10-Geräten ausführen. Das [Vergleichen der Verwaltung von Windows-PCs als Computer oder mobile Geräte](pc-management-comparison.md) ist eine großartige Ressource.

Die Intune-Verwaltungserweiterung ergänzt die integrierten MDM-Features für Windows 10. Sie können PowerShell-Skripts für die Ausführung auf Windows 10-Geräten erstellen. Sie können beispielsweise ein PowerShell-Skript erstellen, das eine ältere Win32-App installiert, das Skript in Intune hochlädt, es einer Azure Active Directory-Gruppe (AD) zuweist und ausführt. Sie können dann den Ausführungsstatus des Skripts von Anfang bis Ende überwachen.

## <a name="prerequisites"></a>Voraussetzungen

Für die Intune-Verwaltungserweiterung sind folgende Voraussetzungen erforderlich:

- Geräte müssen mit Azure AD verknüpft und [automatisch registriert](windows-enroll.md#enable-windows-10-automatic-enrollment) werden. Die Intune-Verwaltungserweiterung unterstützt Geräte, die mit Azure AD und hybriden Domänen verknüpft sind, sowie gemeinsam verwaltete registrierte Windows-Geräte. GPO-registrierte Geräte werden nicht unterstützt.
- Geräte müssen Windows 10 Version 1607 oder höher ausführen.
- Der Agent für die Intune-Verwaltungserweiterung wird installiert, wenn ein PowerShell-Skript oder eine Win32-App an einen Benutzer oder eine Gerätesicherheitsgruppe bereitgestellt wird.

## <a name="create-a-powershell-script-policy"></a>Erstellen einer PowerShell-Skriptrichtlinie 

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **PowerShell-Skripts** > **Hinzufügen**.
3. Geben Sie einen **Namen** und eine **Beschreibung** für das PowerShell-Skript ein. Navigieren Sie zum PowerShell-Skript für den **Skriptstandort**. Das Skript muss kleiner als 200 KB (ASCII) oder 100 KB (Unicode) sein.
4. Wählen Sie **Konfigurieren** aus. Wählen Sie dann aus, ob das Skript mit den Anmeldeinformationen des Benutzers auf dem Gerät (**Ja**) oder im Systemkontext (**Nein**) ausgeführt werden soll. Standardmäßig werden die Skripts im Systemkontext ausgeführt. Wählen Sie **Ja** aus, wenn das Skript nicht im Systemkontext ausgeführt werden muss. 
  ![Bereich „PowerShell-Skript hinzufügen“](./media/mgmt-extension-add-script.png)
5. Wählen Sie aus, ob das Skript von einem vertrauenswürdigen Herausgeber signiert werden muss (**Ja**). Standardmäßig muss das Skript nicht signiert werden. 
6. Klicken Sie auf **OK** und dann auf **Erstellen**, um Ihr Skript zu speichern.

## <a name="assign-a-powershell-script-policy"></a>Zuweisen einer PowerShell-Skriptrichtlinie

1. Wählen Sie unter **PowerShell-Skripts** das zuzuweisende Skript aus, und klicken Sie dann auf **Verwalten** > **Zuweisungen**.

    ![Bereich „PowerShell-Skript hinzufügen“](./media/mgmt-extension-assignments.png)

2. Klicken Sie auf **Gruppen auswählen**, um verfügbare Azure AD-Gruppen aufzulisten. 
3. Wählen Sie mindestens eine Gruppe aus, die die Benutzer enthält, deren Geräte das Skript erhalten sollen. Klicken Sie auf **Auswählen**, um die Richtlinie den ausgewählten Gruppen zuzuweisen.

> [!NOTE]
> - PowerShell-Skripts können nicht auf Computergruppen angewendet werden.
> - Endbenutzer müssen sich nicht beim Gerät anmelden, um PowerShell-Skripts auszuführen.
> - PowerShell-Skripts in Intune können auf Azure AD-Gerätesicherheitsgruppen ausgerichtet werden.

Der Intune-Verwaltungserweiterungsclient wird einmal pro Stunde mit Intune abgeglichen. Nachdem Sie die Richtlinie den Azure AD-Gruppen zugewiesen haben, wird das PowerShell-Skript ausgeführt, und die Ausführungsergebnisse werden berichtet.

## <a name="monitor-run-status-for-powershell-scripts"></a>Überwachen des Ausführungsstatus für PowerShell-Skripts

Sie können den Ausführungsstatus von PowerShell-Skripts für Benutzer und Geräte im Azure-Portal überwachen.

Wählen Sie unter **PowerShell-Skripts** das zu überwachende Skript aus, klicken Sie auf **Überwachen**, und wählen Sie anschließend einen der folgenden Berichte aus:

- **Gerätestatus**
- **Benutzerstatus**

## <a name="troubleshoot-powershell-scripts"></a>Problembehandlung bei PowerShell-Skripts

Agentprotokolle auf dem Clientcomputer befinden sich in der Regel unter `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Sie können mit [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) diese Protokolldateien anzeigen. 

![Screenshot zu den Agentprotokollen](./media/apps-win32-app-10.png)  

## <a name="delete-a-powershell-script"></a>Löschen eines PowerShell-Skripts

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

#### <a name="issue-the-powershell-scripts-do-not-run"></a>Problem: Die PowerShell-Skripts werden nicht ausgeführt

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
