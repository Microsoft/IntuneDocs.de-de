---
title: Installieren der PC-Clientsoftware
description: Befolgen Sie diese Anleitung zum Verwalten Ihrer Windows-PCs durch die Microsoft Intune-Clientsoftware.
keywords: ''
author: ErikjeMS
ms.author: erikje
ms.date: 07/13/2017
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 44ba77609b3fafd5518378f3edcbbbace0f6a551
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68354080"
---
# <a name="install-the-intune-software-client-on-windows-pcs"></a>Installieren des Intune-Softwareclients auf Windows-PCs

[!INCLUDE [classic-portal](includes/classic-portal.md)]

> [!NOTE]
> Mit Microsoft Intune können Sie Windows-PCs wie unten beschrieben entweder mithilfe der [mobilen Geräteverwaltung (Mobile Device Management, MDM) als mobile Geräte](windows-enroll.md) oder mithilfe des Intune-Softwareclients als Computer verwalten. Allerdings wird Kunden empfohlen, wenn möglich die [MDM-Verwaltungslösung](windows-enroll.md) zu verwenden. Weitere Informationen finden Sie unter [Vergleichen der Verwaltung von Windows-PCs als Computer oder Mobilgeräte](pc-management-comparison.md). 


Windows-PCs können mithilfe der Installation der Intune-Clientsoftware registriert werden. Die Intune-Clientsoftware kann mithilfe der folgenden Methoden installiert werden:

- Vom IT-Administrator, mithilfe einer der folgenden Methoden: Manuelle Installation, Gruppenrichtlinie oder in einem Datenträgerimage enthaltene Installation

- Von Endbenutzern, die die Clientsoftware manuell installieren

Die Intune-Clientsoftware enthält die für die Registrierung des PCs in der Intune-Verwaltung mindestens erforderliche Software. Nach der Registrierung eines PCs lädt die Intune-Clientsoftware dann die vollständige Clientsoftware herunter, die für die Verwaltung des PC benötigt wird.

Diese Downloadserie verringert die Auswirkungen auf die Netzwerkbandbreite und reduziert die Zeit, die zur ersten Registrierung des PC in Intune erforderlich ist, auf ein Mindestmaß. Außerdem wird sichergestellt, dass auf dem Client die neueste verfügbare Software läuft, nachdem der zweite Download abgeschlossen ist.

Eine Lizenz für Intune ermöglicht die Installation der Intune-Clientsoftware auf bis zu fünf PCs.

## <a name="download-the-intune-client-software"></a>Herunterladen der Intune-Clientsoftware

Mit Ausnahme der Methode, bei denen Benutzer die Intune-Clientsoftware selbst installieren, erfordern alle Methoden, dass die Software zuerst von IT-Administratoren heruntergeladen wird, damit sie anschließend den Endbenutzern bereitgestellt werden kann.

1. Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) auf **Admin** &gt; **Download der Clientsoftware**.

   ![Herunterladen des Intune-PC-Clients](./media/https://docs.microsoft.com/intune/media/install-the-windows-pc-client/pc-sa-client-download.png)

2. Klicken Sie auf der Seite **Clientsoftwaredownload** auf **Clientsoftwaredownload**. Speichern Sie anschließend das Paket **Microsoft_Intune_Setup.zip**, das die Software enthält, an einem sicheren Speicherort in Ihrem Netzwerk.

   Das Installationspaket der Intune-Clientsoftware enthält eindeutige und spezifische Informationen zu Ihrem Konto, die über ein eingebettetes Zertifikat verfügbar sind. Wenn nicht autorisierte Benutzer Zugriff auf das Installationspaket erhalten, können sie PCs bei dem Konto registrieren, dem das eingebettete Zertifikat entspricht, und möglicherweise Zugriff auf Unternehmensressourcen erhalten.

3. Extrahieren Sie an dem sicheren Ort in Ihrem Netzwerk den Inhalt des Installationspakets.

    > [!IMPORTANT]
    > Sie dürfen die extrahierte Datei **ACCOUNTCERT** weder umbenennen noch entfernen, da sonst die Installation der Clientsoftware misslingt.

## <a name="deploy-the-client-software-manually"></a>Manuelles Bereitstellen der Clientsoftware

Auf den Computern, auf denen die Clientsoftware installiert werden soll, wechseln Sie zu dem Ordner, in dem sich die Installationsdateien der Clientsoftware befinden. Führen Sie dann **Microsoft_Intune_Setup.exe** aus, um die Clientsoftware zu installieren.

> [!NOTE]
> Der Installationsstatus wird angezeigt, wenn Sie mit dem Mauszeiger auf das Symbol in der Taskleiste des Client-PCs zeigen.

## <a name="deploy-the-client-software-by-using-group-policy"></a>Bereitstellen der Clientsoftware mithilfe von Gruppenrichtlinien

1. Führen Sie im Ordner, der die Dateien **Microsoft_Intune_Setup.exe** und **MicrosoftIntune.accountcert** enthält, den folgenden Befehl aus, um die Windows Installer-basierten Installationsprogramme für 32-Bit- und 64-Bit-Computer zu extrahieren:

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2. Kopieren Sie die Dateien **Microsoft_Intune_x86.msi**, **Microsoft_Intune_x64.msi** und **MicrosoftIntune.accountcert** in einen Netzwerkpfad, auf den alle Computer, auf denen die Clientsoftware installiert werden soll, zugreifen können.

    > [!IMPORTANT]
    > Benennen Sie die Dateien nicht um, und trennen sie sie nicht, da bei der Installation der Clientsoftware sonst ein Fehler auftritt.

3. Verwenden Sie Gruppenrichtlinien, um die Software auf Computern in Ihrem Netzwerk bereitzustellen.

    Weitere Informationen zum automatischen Bereitstellen von Software mithilfe von Gruppenrichtlinien finden Sie unter [Gruppenrichtlinien für Anfänger](https://technet.microsoft.com/library/hh147307.aspx).

## <a name="deploy-the-client-software-as-part-of-an-image"></a>Bereitstellen der Clientsoftware als Teil eines Images
Sie können die Intune-Clientsoftware als Teil eines Betriebssystemabbilds auf Computern installieren. Verwenden Sie dazu die folgende Vorgehensweise als Leitfaden:

1. Kopieren Sie die Clientinstallationsdateien **Microsoft_Intune_Setup.exe** und **MicrosoftIntune.accountcert** in den Ordner **%Systemdrive%\Temp\Microsoft_Intune_Setup** auf dem Referenzcomputer.

2. Erstellen Sie den Registrierungseintrag **WindowsIntuneEnrollPending** , indem Sie dem Skript **SetupComplete.cmd** den folgenden Befehl hinzufügen:

    ```cmd
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3. Fügen Sie **setupcomplete.cmd** den folgenden Befehl hinzu, um das Registrierungspaket mit dem Befehlszeilenargument „/PrepareEnroll“ auszuführen:

    ```cmd
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```

    > [!TIP]
    > Mithilfe des Skripts **SetupComplete.cmd** können von Windows Setup Veränderungen am System vorgenommen werden, bevor sich ein Benutzer anmeldet. Durch das Befehlszeilenargument **/PrepareEnroll** wird ein Zielcomputer auf die automatische Registrierung bei Intune nach Beenden von Windows Setup vorbereitet.

4. Legen Sie die Datei **SetupComplete.cmd** auf dem Referenzcomputer im Ordner **%Windir%\Setup\Scripts** ab.

5. Erstellen Sie ein Systemabbild des Referenzcomputers, und stellen sie es auf den Zielcomputern bereit.

    Wenn der Zielcomputer nach Beenden von Windows Setup neu gestartet wird, wird der Registrierungsschlüssel **WindowsIntuneEnrollPending** erstellt. Mit dem Registrierungspaket wird überprüft, ob der Computer registriert ist. Wenn der Computer registriert ist, ist keine weitere Aktion erforderlich. Wenn der Computer nicht registriert ist, wird vom Registrierungspaket eine Aufgabe zur automatischen Microsoft Intune-Registrierung erstellt.

    Bei der Ausführung dieser Aufgabe zur automatischen Registrierung zum nächsten geplanten Zeitpunkt prüft die Aufgabe das Vorhandensein des Registrierungswerts **WindowsIntuneEnrollPending** und versucht, den Ziel-PC bei Intune zu registrieren. Sollte die Registrierung aus einem beliebigen Grund fehlschlagen, wird die Registrierung beim nächsten Ausführen der Aufgabe erneut versucht. Die Wiederholungen werden für einen Monat ausgeführt.

    Die Aufgabe zur automatischen Intune-Registrierung, der Registrierungswert **WindowsIntuneEnrollPending** und das Kontozertifikat werden entweder vom Zielcomputer gelöscht, sobald die Registrierung erfolgreich war oder ein Monat vergangen ist (egal was zuerst kommt).

## <a name="instruct-users-to-self-enroll"></a>Einweisen von Benutzern in die eigenständige Registrierung

Benutzer können die Intune-Clientsoftware installieren, indem Sie auf die [Unternehmensportal-Website](https://portal.manage.microsoft.com) gehen. Die genauen Informationen, die den Benutzern im Webportal angezeigt werden, können je nach MDM-Autorität Ihres Kontos und je nach Betriebssystemplattform und Version des Benutzer-PCs variieren.

Wenn Benutzern keine Lizenz für Intune zugewiesen wurde oder die MDM-Autorität der Organisation nicht auf Intune festgelegt wurde, werden den Benutzern keine Optionen zum Registrieren angezeigt.

Wenn Benutzern eine Lizenz für Intune zugewiesen wurde und die MDM-Autorität der Organisation auf Intune festgelegt wurde:

- Windows 7- oder Windows 8-PC-Benutzern wird die Option zum Anmelden bei Intune NUR angezeigt, indem sie die PC-Clientsoftware, die in ihrer Organisation eindeutig ist, herunterladen und installieren.

- Windows 10- oder Windows 8.1-PC-Benutzern werden zwei Registrierungsoptionen angezeigt:

  - **PC als mobiles Gerät registrieren**: Benutzer wählen die Schaltfläche **ANLEITUNG ZUM REGISTRIEREN** und werden zu Anweisungen weitergeleitet, wie sie ihren PC als mobiles Gerät registrieren. Diese Schaltfläche wird hervorgehoben angezeigt, da die MDM-Registrierung die Standardeinstellung und die bevorzugte Registrierungsoption ist. Die MDM-Option ist jedoch nicht auf dieses Thema anwendbar, das nur die Installation der Clientsoftware behandelt.
  - **Registrieren des PCs mit Intune-Clientsoftware**: Ihre Benutzer müssen den Link **Zum Herunterladen hier klicken** auswählen, der sie durch die Installation der Clientsoftware führt.

In der folgende Tabelle werden die Optionen zusammengefasst.

  ![Standardregistrierungsoptionen pro Plattform](./media/install-the-windows-pc-client/default-enrollment-options-table.png)

Die folgenden Screenshots zeigen, was die Benutzer sehen, wenn sie mithilfe des Softwareclients ihre Geräte registrieren.

Benutzer werden zuerst aufgefordert, ihr Gerät zu identifizieren oder zu registrieren.

  ![Gerät identifizieren oder registrieren](./media/install-the-windows-pc-client/identify-device-or-enroll.png)

Damit Ihre Benutzer die PC-Clientsoftware installieren können, müssen Sie den Link **Zum Herunterladen hier klicken** auswählen, wodurch Benutzer die PC-Clientsoftware herunterzuladen können und sie durch den Installationsvorgang geführt werden. Die **ANLEITUNG ZUM REGISTRIEREN**-Schaltfläche führt Benutzer zur Dokumentation für die Registrierung mithilfe der MDM-Registrierung, die für diese Softwareclient-Anweisungen nicht relevant ist.

  ![Link „Zum Herunterladen hier klicken“ auswählen](./media/install-the-windows-pc-client/enroll-your-windows-device.png)

Wenn Benutzer auf den Link klicken, sehen sie eine **Software herunterladen**-Schaltfläche, die sie auswählen, um die Installation der PC-Clientsoftware zu starten.

  ![Schaltfläche „Software herunterladen“ auswählen](./media/install-the-windows-pc-client/download-pc-client-software.png)

Benutzer werden dann aufgefordert, sich mit ihren Unternehmensanmeldeinformationen anzumelden.

  ![Mit Ihren Anmeldeinformationen anmelden](./media/install-the-windows-pc-client/sign-in-to-intune.png)

Benutzer werden auf die Willkommensseite für die Installation geführt.

  ![Willkommensseite für die PC-Clientinstallation](./media/install-the-windows-pc-client/welcome-to-pc-agent-install-wizard.png)

Die Benutzer wählen **Weiter** aus, und die Installation wird gestartet.

  ![Willkommensseite für die PC-Clientinstallation](./media/install-the-windows-pc-client/welcome-to-pc-agent-install-wizard.png)

Wenn die Installation abgeschlossen ist, wählen die Benutzer **Fertig stellen** aus.

  ![Abschließen der PC-Clientinstallation](./media/install-the-windows-pc-client/completed-the-setup-wizard.png)

Wenn Benutzer versuchen, ihren PC als mobiles Gerät zu registrieren, nachdem sie ihn bereits mithilfe der Intune-PC-Clientsoftware registriert haben, wird ihnen der folgenden Fehlerbildschirm angezeigt.

  ![Bildschirm, der angezeigt wird, wenn der Computer bereits registriert ist](./media/install-the-windows-pc-client/page-shown-if-pc-already-enrolled.png)

## <a name="monitor-and-validate-successful-client-deployment"></a>Überwachen und Überprüfen der erfolgreichen Clientbereitstellung
Verwenden Sie eins der folgenden Verfahren, um die erfolgreiche Clientbereitstellung zu überwachen und zu überprüfen.

### <a name="to-verify-the-installation-of-the-client-software-from-the-microsoft-intune-administrator-console"></a>So überprüfen Sie die Installation der Clientsoftware mithilfe der Microsoft Intune-Administratorkonsole

1. Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) auf **Gruppen** &gt; **Alle Geräte** &gt; **Alle Computer**.

2. Suchen Sie in der Liste der Computer die verwalteten Computer, von denen mit Intune kommuniziert wird. Um nach einem bestimmten verwalteten Computer zu suchen, geben Sie den Computernamen oder einen Teil des Namens in das Textfeld **Geräte suchen** ein.

3. Überprüfen Sie den Status des Computers im unteren Bereich der Konsole. Beheben Sie alle Fehler.

### <a name="to-create-a-computer-inventory-report-to-display-all-enrolled-computers"></a>So erstellen Sie einen Computerinventurbericht zum Anzeigen aller registrierten Computer

1. Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) auf **Berichte** &gt; **Computerinventurberichte**.

2. Belassen Sie auf der Seite **Neuen Bericht erstellen** die Standardwerte in den Feldern (sofern Sie keine Filter anwenden möchten), und klicken Sie anschließend auf **Bericht anzeigen**.

3. In einem neuen Fenster wird die Seite **Computerinventurbericht** geöffnet, auf der alle erfolgreich bei Intune registrierten Computer angezeigt werden.

    > [!TIP]
    > Klicken Sie im Bericht auf beliebige Spaltenüberschriften, um die Liste nach dem Inhalt der betreffenden Spalte zu sortieren.

## <a name="uninstall-the-windows-client-software"></a>Deinstallieren der Windows-Clientsoftware

Es gibt zwei Möglichkeiten, die Registrierung der Clientsoftware von Windows aufzugeben:

- Über die Intune-Verwaltungskonsole aus (empfohlene Methode)
- Über eine Eingabeaufforderung auf dem Client

### <a name="unenroll-by-using-the-intune-admin-console"></a>Registrierung durch Verwendung der Intune-Verwaltungskonsole aufheben

Um die Registrierung des Softwareclients über die Intune-Verwaltungskonsole aufzuheben, navigieren sie zu **Gruppen** > **Alle Computer** > **Geräte**. Klicken Sie mit der rechten Maustaste auf den Client, und wählen Sie **Abkoppeln/Zurücksetzen** aus.

### <a name="unenroll-by-using-a-command-prompt-on-the-client"></a>Aufgeben der Registrierung durch Verwendung einer Eingabeaufforderung auf dem Client

Führen Sie mithilfe einer Eingabeaufforderung mit erhöhten Rechten die folgenden Befehle aus.

**Methode 1**

    "C:\Program Files\Microsoft\OnlineManagement\Common\ProvisioningUtil.exe" /UninstallAgents /MicrosoftIntune

**Methode 2** Beachten Sie, dass nicht alle diese Agents auf jeder Windows-SKU installiert sind:

    wmic product where name="Microsoft Endpoint Protection Management Components" call uninstall
    wmic product where name="Microsoft Intune Notification Service" call uninstall
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall
    wmic product where name="Microsoft Online Management Policy Agent" call uninstall
    wmic product where name="Microsoft Policy Platform" call uninstall
    wmic product where name="Microsoft Security Client" call uninstall
    wmic product where name="Microsoft Online Management Client" call uninstall
    wmic product where name="Microsoft Online Management Client Service" call uninstall
    wmic product where name="Microsoft Easy Assist v2" call uninstall
    wmic product where name="Microsoft Intune Monitoring Agent" call uninstall
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall
    wmic product where name="Windows Firewall Configuration Provider" call uninstall
    wmic product where name="Microsoft Intune Center" call uninstall
    wmic product where name="Microsoft Online Management Update Manager" call uninstall
    wmic product where name="Microsoft Online Management Agent Installer" call uninstall
    wmic product where name="Microsoft Intune" call uninstall
    wmic product where name="Windows Endpoint Protection Management Components" call uninstall
    wmic product where name="Windows Intune Notification Service" call uninstall
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall
    wmic product where name="Windows Online Management Policy Agent" call uninstall
    wmic product where name="Windows Policy Platform" call uninstall
    wmic product where name="Windows Security Client" call uninstall
    wmic product where name="Windows Online Management Client" call uninstall
    wmic product where name="Windows Online Management Client Service" call uninstall
    wmic product where name="Windows Easy Assist v2" call uninstall
    wmic product where name="Windows Intune Monitoring Agent" call uninstall
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall
    wmic product where name="Windows Firewall Configuration Provider" call uninstall
    wmic product where name="Windows Intune Center" call uninstall
    wmic product where name="Windows Online Management Update Manager" call uninstall
    wmic product where name="Windows Online Management Agent Installer" call uninstall
    wmic product where name="Windows Intune" call uninstall

> [!TIP]
> Durch die Aufhebung der Registrierung eines Clients verbleibt ein ungesicherter Bericht auf Serverseite für den betroffenen Client. Der Vorgang zur Aufhebung der Registrierung ist asynchron. Es gibt neun Agents, die gelöscht werden müssen, also dauert es bis zu 30 Minuten, bis der Vorgang abgeschlossen ist.

### <a name="check-the-unenrollment-status"></a>Überprüfen des Status der Aufhebung der Registrierung

Überprüfen Sie „%ProgramFiles%\Microsoft\OnlineManagement“, und stellen Sie sicher, dass ausschließlich die folgenden Verzeichnisse auf der linken Seite angezeigt werden:

- AgentInstaller
- Protokolle
- Updates
- Allgemein

### <a name="remove-the-onlinemanagement-folder"></a>Entfernen des Ordner „OnlineManagement“

Der Prozess zur Aufhebung der Registrierung entfernt nicht den OnlineManagement-Ordner. Warten Sie nach der Deinstallation 30 Minuten, und führen Sie dann diesen Befehl aus. Wenn Sie ihn zu früh ausführen, kann die Deinstallation in einem unbekannten Status verbleiben. Um den Ordner zu entfernen, starten Sie einen Befehl mit erhöhten Rechten, und führen Sie folgendes aus:

    "rd /s /q %ProgramFiles%\Microsoft\OnlineManagement".

## <a name="next-steps"></a>Nächste Schritte
[Allgemeine Aufgaben zur Verwaltung von Windows-PCs mit dem Intune-Softwareclient](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
