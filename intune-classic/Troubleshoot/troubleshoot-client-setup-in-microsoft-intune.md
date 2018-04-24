---
title: Behandlung von Problemen bei der Clienteinrichtung
description: Problembehandlung bei allgemeinen Problemen bei der Clienteinrichtung.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 02/22/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e46d292b-1d16-46db-a87f-d53eefa4d22a
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 39c0b0997bdbf229064e6b5ef25ab559b9252f83
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshoot-client-setup-in-microsoft-intune"></a>Behandlung von Problemen bei der Clienteinrichtung in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Die folgenden Abschnitte enthalten Informationen zu gängigen Problemen bei der Clienteinrichtung. Wenn sich das Problem mit diesen Informationen nicht beheben lässt, finden Sie unter [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Anfordern von Support für Microsoft Intune) weitere Möglichkeiten, Hilfe zu erhalten.

## <a name="client-installation-fails"></a>Fehler bei Clientinstallation

-   Wenn in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) für den Computer keine Warnungen zur Softwarebereitstellung angezeigt werden, überprüfen Sie die Internetverbindung und die Proxykonfiguration des Computers, und stellen Sie sicher, dass der Computer mit der Dienst-URL [https://manage.microsoft.com](https://manage.microsoft.com/) kommunizieren kann. Wiederholen Sie anschließend die Installation der Clientsoftware.

-   Sie können eine E-Mail-Nachricht an ausgewählte Empfänger versenden lassen, wenn eine Fehlerwarnung bei der Bereitstellung von Clientsoftware auftritt. Konfigurieren Sie dazu eine Benachrichtigungsregel im Arbeitsbereich **Admin** . Weitere Informationen finden Sie unter [Benachrichtigungen durch Microsoft Intune-Warnungen](/intune-classic/deploy-use/get-notified-by-alerts).

-   Intune zeigt die kritische Warnung **Fehler bei der Bereitstellung der Clientsoftware** an, wenn die Bereitstellung der Clientsoftware nicht gelingt. Diese Warnung wird auf den Seiten **Systemübersicht** und **Warnungen** in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) angezeigt. So überprüfen Sie, ob Warnungen vorliegen:

1.  Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) auf **Warnungen** &gt; **Übersicht**.

2.  Auf der Seite **Warnungsübersicht** finden Sie die folgenden Informationen:

    -   die drei wichtigsten Warnungen, sortierbar nach Datum, Kategorie oder Schweregrad

    -   die Gesamtzahl der aktiven Warnungen

3.  Klicken Sie auf **Alle Warnungen**, um die folgenden Informationen auf der Seite **Warnungen** anzuzeigen. Kritische Warnungen werden zuerst angezeigt:

    -   **Name** : Dies ist der Name des Warnungstyps, von dem die Warnung generiert wurde.

    -   **Quelle** : Dies ist ein Link zur Quelle der Warnung.  Wenn der Anzeigeschwellenwert des Warnungstyps auf **Alle**festgelegt ist, wird über diesen Link ein einzelnes betroffenes Gerät angezeigt.  Wenn der Anzeigeschwellenwert des Warnungstyps auf einen Wert festgelegt ist, wird über diesen Link eine Liste aller Geräte angezeigt, die von dieser Warnung betroffen sind.

    -   **Zuletzt aktualisiert** : Hier wird angegeben, wann die Warnung zuletzt geändert wurde. Wenn eine Warnung geschlossen ist, wird hier die Uhrzeit angezeigt, zu der die Warnung geschlossen wurde.

    -   **Schweregrad** : Gibt den Schweregrad der Warnung an

## <a name="computer-enrollment-package-doesnt-download"></a>Computerregistrierungspaket lässt sich nicht herunterladen
**Problem:** Beim Versuch, einen Computer zu registrieren, geschieht Folgendes:
-  Das Registrierungspaket lässt sich nicht herunterladen.
-  Das Dialogfeld zum Herunterladen wird angezeigt, aber ein Timeout tritt auf.

**Lösung:** Stellen Sie sicher, dass in dem Browser, den Sie für den Download verwenden, für den Zeitraum, in dem der Download erfolgt, Downloads aktiviert sind, und dass verschlüsselte Dateien auf Ihrem lokalen Datenträger gespeichert werden können.

## <a name="client-installation-hangs-with-error-code-0x80040154"></a>Clientinstallation reagiert nicht mehr – Fehlercode 0x80040154
**Problem:**

-  Clientinstallation reagiert bei Registrierung nicht mehr

-  Registrierung des Geräts unmöglich

-  Fehler 0x80040154 in WindowsUpdate.log

Das Fehlen kritischer Softwareupdates auf dem PC kommt als Ursache infrage.

**Lösung:** Stellen Sie sicher, dass Ihre Softwareupdaterichtlinie die Installation wichtiger Updates ermöglicht, wie in [Windows-PCs mit Softwareupdates in Microsoft Intune auf aktuellem Stand halten](/intune-classic/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune) beschrieben.


## <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Fehler in „policyplatform.log“ im Zusammenhang mit der Microsoft Intune-Richtlinie
Bei Windows-Geräten ohne MDM können Richtlinienfehler in der Datei „policyplatform.log“ das Ergebnis nicht standardmäßiger Einstellungen in der Windows-Benutzerkontensteuerung (UAC) auf dem Gerät sein. Einige nicht standardmäßige UAC-Einstellungen können Microsoft Intune-Clientinstallationen und Richtlinienausführungen beeinträchtigen.

### <a name="to-resolve-uac-issues"></a>So beheben Sie UAC-Probleme

1.  Koppeln Sie den Computer ab, wie unter [Retire data and devices from Microsoft Intune management](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management) (Abkoppeln von Daten und Geräten in der Microsoft Intune-Verwaltung) beschrieben.

2.  Warten Sie 20 Minuten, bis die Clientsoftware entfernt wurde.

    > [!NOTE]
    > Versuchen Sie nicht, den Client über „Programme und Funktionen“ zu entfernen.

3.  Geben Sie im Startmenü **UAC** ein, um die Einstellungen der Benutzerkontensteuerung zu öffnen.

4.  Verschieben Sie den Schieberegler für Benachrichtigungen auf die Standardeinstellung.

## <a name="what-to-do-if-the-client-will-not-uninstall-from-the-microsoft-intune-administrator-console"></a>Vorgehensweise, wenn sich der Client nicht in der Microsoft Intune-Administratorkonsole deinstallieren lässt

### <a name="to-remove-the-client-software-by-using-the-microsoft-intune-command-line-tool"></a>So entfernen Sie die Clientsoftware unter Verwendung des Microsoft Intune-Befehlszeilentools

1.  Öffnen Sie eine Eingabeaufforderung im Administratormodus.

2.  Navigieren Sie zum Ordner *%programfiles%\Microsoft\OnlineManagement\Common*.

3.  Führen Sie den folgenden Befehl aus: ``ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune``

## <a name="client-installation-error-codes"></a>Fehlercodes bei der Clientinstallation
In der folgenden Tabelle werden Fehlercodes erläutert, die in **Warnungen** angezeigt werden, wenn die Installation der Clientsoftware fehlschlägt. Gleichzeitig werden Vorschläge zur Behebung der Probleme vorgestellt, für die die Fehlercodes stehen.


|                                                                   Fehlercode                                                                    |                                                          Mögliches Problem                                                          |                                                                                                                                                                                                Lösungsvorschlag                                                                                                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                           <strong>0x80CF0437</strong>                                                           |                                  Die Uhr des Clientcomputers ist nicht auf die richtige Uhrzeit eingestellt.                                  |                                                                                                                                                    Stellen Sie sicher, dass die Uhr und die Zeitzone des Clientcomputers richtig eingestellt sind.                                                                                                                                                     |
|                              <strong>0x80240438</strong>, <strong>0x80CF0438</strong>, <strong>0x80CF401B</strong>                              |                               Verbindung mit dem Intune-Dienst ist nicht möglich. Überprüfen Sie die Proxy-Einstellungen des Clients.                               |                   Überprüfen Sie, ob die Proxykonfiguration des Clientcomputers von Intune unterstützt wird, und ob der Clientcomputer Zugang zum Internet hat. Weitere Informationen zu unterstützten Proxykonfigurationen finden Sie unter [Schützen von Windows-PCs mit Endpoint Protection für Microsoft Intune](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).                    |
|                                                           <strong>0x80CF402C</strong>                                                           |                                 Verbindung mit dem Intune-Dienst ist nicht möglich. Überprüfen Sie die Netzwerkverbindungen.                                  |                                                                                                                                                   Überprüfen Sie, ob der Computer über eine Netzwerkverbindung verfügt. Stellen Sie sicher, dass das Netzwerkkabel verbunden bzw. das Funknetzwerk aktiv ist.                                                                                                                                                    |
|                                                     <strong>0x80240438, 0x80CF0438</strong>                                                     |                              Proxyeinstellungen in Internet Explorer und im lokalen System sind nicht konfiguriert.                              | Überprüfen Sie die Proxyeinstellungen des Clients, und vergewissern Sie sich, dass die Proxykonfiguration des Clientcomputers von Intune unterstützt wird, und der Clientcomputer mit dem Internet verbunden ist. Weitere Informationen zu unterstützten Proxykonfigurationen finden Sie unter [Schützen von Windows-PCs mit Endpoint Protection für Microsoft Intune](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune). |
|                                                           <strong>0x80043001</strong>                                                           |                                                 Das Registrierungspaket ist nicht mehr aktuell.                                                 |                                                                     Laden Sie das aktuellste Clientsoftwarepaket vom Arbeitsbereich <strong>Admin</strong> herunter, und installieren Sie es. Anweisungen finden Sie im Thema [Install the Windows PC client with Microsoft Intune](/intune-classic/deploy-use/install-the-windows-pc-client-with-microsoft-intune) (Installieren des Windows-PC-Clients mit Microsoft Intune).                                                                      |
|                                                           <strong>0x80043004</strong>                                                           |                                            Das Abonnement ist nicht vorhanden oder wurde deaktiviert.                                            |                                                                                                   Prüfen Sie, ob Ihr Konto und Ihr Abonnement für Intune noch aktiv sind. Melden Sie sich zum Anzeigen Ihrer Kontoeinstellungen bei Ihrem Konto im [Office 365 Admin Center](http://go.microsoft.com/fwlink/?LinkId=698854%20) an.                                                                                                   |
|                                                           <strong>0x80043002</strong>                                                           |                                                  Das Konto befindet sich im Wartungsmodus.                                                   |                                                                                             Wenn sich das Konto im Wartungsmodus befindet, können Sie keine neuen Clientcomputer registrieren. Melden Sie sich zum Anzeigen Ihrer Kontoeinstellungen bei Ihrem Konto im [Office 365 Admin Center](http://go.microsoft.com/fwlink/?LinkId=698854%20) an.                                                                                              |
|                                                           <strong>0x80043003</strong>                                                           |                                                        Das Konto wurde gelöscht.                                                         |                                                                                                                                            Prüfen Sie, ob Ihr Konto und Ihr Abonnement für Intune noch aktiv sind. Melden Sie sich zum Anzeigen Ihrer Kontoeinstellungen bei Ihrem Konto an.                                                                                                                                             |
|                                                           <strong>0x80043005</strong>                                                           |                                                  Der Clientcomputer wurde abgekoppelt.                                                   |                                                                  Warten Sie einige Stunden, entfernen Sie ältere Versionen der Clientsoftware von dem Computer, und versuchen Sie dann erneut, die Clientsoftware auf dem Computer zu installieren. Weitere Anweisungen finden Sie weiter oben unter <strong>Vorgehensweise, wenn sich der Client nicht in der Microsoft Intune-Administratorkonsole deinstallieren lässt</strong>.                                                                  |
|                                                           <strong>0x80043006</strong>                                                           |                                  Die maximal zulässige Anzahl von Arbeitsplätzen für das Konto wurde erreicht.                                   |                                                                                                                                                    Ihr Unternehmen muss zusätzliche Arbeitsplätze erwerben, bevor Sie weitere Clientcomputer bei dem Dienst registrieren können.                                                                                                                                                     |
|                                                           <strong>0x80043007</strong>                                                           |                          Zertifikatsdatei wurde im Ordner des Installationsprogramms nicht gefunden.                          |                                 Extrahieren Sie alle Dateien, bevor Sie die Installation starten. Die extrahierten Dateien dürfen nicht umbenannt oder verschoben werden: Alle Dateien müssen im selben Ordner vorhanden sein, da die Installation sonst fehlschlägt. Weitere Informationen finden Sie unter [Installieren des Windows-PC-Clients mit Microsoft Intune](/intune-classic/deploy-use/install-the-windows-pc-client-with-microsoft-intune).                                  |
| <strong>0x8024D015</strong>, <strong>0x00240005</strong>, <strong>0x80070BC2</strong>, <strong>0x80070BC9</strong>, <strong>0x80CFD015</strong> |                       Die Software kann nicht installiert werden, weil ein Neustart des Clientcomputers aussteht.                        |                                                                                                                                                                        Starten Sie den Computer neu, und wiederholen Sie dann die Installation der Clientsoftware.                                                                                                                                                                        |
|                                                           <strong>0x80070032</strong>                                                           |                Eine oder mehrere Voraussetzungen, die für die Installation der Clientsoftware erforderlich sind, wurden auf dem Clientcomputer nicht gefunden.                 |                            Stellen Sie sicher, dass alle erforderlichen Updates auf dem Clientcomputer installiert sind, und versuchen Sie dann erneut, die Clientsoftware zu installieren. Weitere Informationen zu den Voraussetzungen für die Installation der Clientsoftware finden Sie unter [Anforderungen an die Netzwerkinfrastruktur für Microsoft Intune](/intune-classic/get-started/network-infrastructure-requirements-for-microsoft-intune).                             |
|                                                           <strong>0x80043008</strong>                                                           |                                  Der Dienst „Updates für Microsoft Online Management“ konnte nicht gestartet werden.                                  |                                                                                                                                               Wenden Sie sich dazu an den Microsoft Support, wie unter [Anfordern von Support für Microsoft Intune](how-to-get-support-for-microsoft-intune.md) beschrieben.                                                                                                                                                |
|                                                           <strong>0x80043009</strong>                                                           |                                     Der Clientcomputer ist bereits für den Dienst registriert.                                      |                                                                                        Sie müssen den Clientcomputer abkoppeln, bevor sie ihn erneut für den Dienst registrieren können. Anweisungen finden Sie unter [Abkoppeln von Geräten in der Microsoft Intune-Verwaltung](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management).                                                                                         |
|                                                           <strong>0x8004300A</strong>                                                           |  (Phase 21) Beim Bereitstellen des Registrierungspakets ins GPO zur Installation auf der Benutzer- und nicht auf der Computerebene tritt ein Fehler auf.   |                                                               Stellen Sie sicher, dass das GPO auf der Computerebene über GPSI korrekt anvisiert wird. Forumsbeiträge zu diesem Thema finden Sie im [TechNet-Forum](https://social.technet.microsoft.com/Forums/en-US/bb9fa71c-c132-4954-abb0-70be8acbd925/failed-to-install-windows-intune?forum=microsoftintuneprod).                                                                |
|                                                           <strong>0x8004300B</strong>                                                           | Das Installationspaket für die Clientsoftware kann nicht ausgeführt werden, da die Windows-Version auf dem Client nicht unterstützt wird. |                                                               Die auf dem Client ausgeführte Windows-Version wird von Intune nicht unterstützt. Eine Liste der unterstützten Betriebssysteme finden Sie unter [Network infrastructure requirements for Microsoft Intune](/intune-classic/get-started/network-infrastructure-requirements-for-microsoft-intune) (Anforderungen an die Netzwerkinfrastruktur für Microsoft Intune).                                                               |
|                                                             <strong>0xAB2</strong>                                                              |                           Fehler beim Zugriff auf die VBScript-Laufzeit für die benutzerdefinierte Aktion.                            |                                                      Dieser Fehler wird von einer benutzerdefinierten Aktion verursacht, die auf DLLs (Dynamic-Link Libraries) aufbaut. Um den DLL-Fehler zu ermitteln, benötigen Sie möglicherweise die Tools, die im Artikel 198038 der [Microsoft Support-KB: Hilfreiche Tools bei Problemen mit der Paketerstellung und Weitergabe](http://go.microsoft.com/fwlink/?LinkID=234255) erläutert werden.                                                       |
|                                                           <strong>0x8004300f</strong>                                                           |           Die Software kann nicht installiert werden, da der System Center Configuration Manager-Client bereits installiert ist.            |                                                                                                                                                              Entfernen Sie den Configuration Manager-Client, und wiederholen Sie dann die Installation der Clientsoftware.                                                                                                                                                               |
|                                                           <strong>0x80043010</strong>                                                           |      Die Software kann nicht installiert werden, da der OMADM-Client (Open Mobile Alliance Device Management) bereits installiert ist.      |                                                                                                                                                                     Heben Sie die Registrierung des OMADM-Clients auf, und wiederholen Sie dann die Installation der Clientsoftware.                                                                                                                                                                     |

Wenn weiterhin Installationsprobleme auftreten, wenden Sie sich wie unter [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Anfordern von Support für Microsoft Intune) beschrieben an den Support. Halten Sie das Registrierungsprotokoll des Clientcomputers (dieses befindet sich unter %*programfiles*%\Microsoft\OnlineManagement\Logs\Enrollment.log und %*userprofile*%\AppData\Local\Microsoft\OnlineManagement\Logs\Enrollement.log) und das Windows Update-Protokoll (%*windir*%\windowsupdate.log) für die Supportmitarbeiter bereit.

## <a name="what-to-do-if-endpoint-protection-is-not-uninstalled-when-you-uninstall-the-client"></a>Was Sie machen können, wenn Endpoint Protection bei der Deinstallation des Clients nicht deinstalliert ist

Manchmal bleibt der Agent für Host Protection (Endpoint Protection) möglicherweise zurück, nachdem Sie die obenstehenden Befehle ausgeführt haben. Sollte dies so sein, führen Sie folgenden Befehl mit erhöhten Benutzerrechten aus:

    ```
    "C:\Program Files\Managed Defender\Setup.exe" /x /q /s
    ```


### <a name="next-steps"></a>Nächste Schritte
Wenn diese Informationen zur Problembehandlung für Sie nicht hilfreich waren, wenden Sie sich wie in [Anfordern von Support für Microsoft Intune](how-to-get-support-for-microsoft-intune.md) beschrieben an den Microsoft Support.
