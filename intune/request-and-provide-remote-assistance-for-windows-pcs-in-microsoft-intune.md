---
title: Anfordern und Bereitstellen von Remoteunterstützung für Windows-PCs
titlesuffix: Microsoft Intune
description: Beschreibt Schritte für Endbenutzer und IT-Administratoren zur Bereitstellung von Remoteunterstützung für Windows-Desktops, die als PCs verwaltet werden, und zum Remotestarten eines PCs.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: c2654491-5144-408a-a45a-644eb91ac1bb
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0b57bae0c0e7a734071be79318286714a97d0fbf
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57460596"
---
# <a name="request-and-provide-remote-assistance-for-windows-pcs"></a>Anfordern und Bereitstellen von Remoteunterstützung für Windows-PCs

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Die Informationen in diesem Thema gelten nur für Windows-Desktops, die Sie als PCs mithilfe des Intune-Softwareclients verwalten.

In Intune können Sie die nicht im Lieferumfang inbegriffene [TeamViewer](https://www.teamviewer.com)-Software verwenden, um Ihre Benutzer, bei denen der Intune-Softwareclient ausgeführt wird, remote zu unterstützen. Sobald ein Benutzer Hilfe über das Microsoft Intune Center anfordert, werden Sie durch eine Warnung benachrichtigt, können die Anforderung annehmen und Unterstützung leisten. Diese Funktion ersetzt die vorhandene Funktion „Windows-Remoteunterstützung“ in Intune.


## <a name="before-you-start"></a>Vorbereitung

Bevor Sie entsprechende Einrichtungsschritte ausführen und auf Anforderungen für Remoteunterstützung reagieren können, stellen Sie sicher, dass folgende Voraussetzungen erfüllt sind:

- Sie müssen sich für ein [TeamViewer-Konto registriert haben](https://login.teamviewer.com/LogOn#register), um sich bei der TeamViewer-Website anzumelden.
- Die Windows-PCs, die auf denen Sie Administrationsaufgaben ausführen möchten, müssen [durch den Windows-Softwareclient verwaltet werden](manage-windows-pcs-with-microsoft-intune.md).
- Auf allen von Intune unterstützten Windows-PC-Betriebssystemen können Administrationsaufgaben ausgeführt werden.

## <a name="configure-the-teamviewer-connector"></a>Konfigurieren des TeamViewer Connectors

1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Option **Verwaltung** aus.
2. Wählen Sie im Arbeitsbereich **Verwaltung** die Option **TeamViewer** aus.
3. Wählen Sie auf der Seite **TeamViewer** unter **TeamViewer Connector** die Option **Aktivieren**.
4. Lesen Sie im Dialogfeld **TeamViewer aktivieren** die Lizenzbedingungen, und klicken Sie auf **Annehmen**, um sie zu akzeptieren. Wenn Sie noch keine TeamViewer-Lizenz besitzen, wählen Sie **TeamViewer-Lizenz erwerben** aus.
5. Wenn das TeamViewer-Browserfenster angezeigt wird, melden Sie sich mit Ihren TeamViewer-Anmeldeinformationen bei der Website an.
6. Lesen Sie auf der TeamViewer-Website die Optionen, um das Herstellen einer Verbindung zwischen Intune und TeamViewer zuzulassen, und akzeptieren Sie sie.
7. Vergewissern Sie sich in der Intune-Konsole, dass das Element **TeamViewer Connector** als **Aktiviert** angezeigt wird.


## <a name="open-a-remote-assistance-request-end-user"></a>Öffnen einer Remoteunterstützungsanforderung (Endbenutzer)

1. Öffnen Sie auf einem Windows-Client-PC das **Microsoft Intune Center**.
2. Wählen Sie unter **Remoteunterstützung** die Option **Remoteunterstützung anfordern** aus.
3. Nach der Genehmigung der Anforderung (siehe unten) wird TeamViewer auf dem Client geöffnet. Der Benutzer muss alle Meldungen akzeptieren, die darauf hinweisen, dass der Webbrowser die TeamViewer-Anwendung zu öffnen versucht.
4. Der Benutzer wird in einer Meldung gebeten zuzulassen, dass Sie die Kontrolle über seinen PC übernehmen. Er muss diese Meldung akzeptieren, damit weitere Schritte möglich sind.
5. Während der Remoteunterstützungssitzung sieht der Benutzer ein Fenster, das anzeigt, dass Sie mit dem Computer des Benutzers verbunden sind. Wenn der Benutzer das Fenster schließt, wird die Remotesitzung beendet.

## <a name="respond-to-a-remote-assistance-request"></a>Reagieren auf eine Remoteunterstützungsanforderung

1. Wenn ein Benutzer eine Remoteunterstützungsanforderung übermittelt, können Sie sie im Arbeitsbereich **Warnungen** unter **Überwachung** > **Remoteunterstützung** anzeigen. Beispiel:
   > ![Screenshot einer Remoteunterstützungsanforderung](/intune/media/team-viewer.png)

<br>Wenn die Anforderung länger als 4 Stunden unbeantwortet bleibt, wird sie entfernt.
2. Um die Anforderung anzunehmen, wählen Sie **Anforderung genehmigen und Remoteunterstützung starten** aus.
3. Wählen Sie im Dialogfeld **Eine neue Remoteunterstützungsanforderung steht aus** die Option **Remoteunterstützungsanforderung annehmen** aus. Falls sie noch nicht vorhanden sind, installiert TeamViewer alle nötigen Apps auf Ihrem PC.
4. Anschließend benachrichtigt TeamViewer den Endbenutzer, dass Sie die Kontrolle seinen PC übernehmen möchten. Nachdem der Benutzer dies akzeptiert hat, wird das TeamViewer-Fenster geöffnet, und Sie können den PC steuern.

Während einer Remoteunterstützungssitzung können Sie in alle verfügbaren TeamViewer-Befehle nutzen, um den Remote-PC zu steuern. Weitere Informationen und Hilfe zu diesen Befehlen finden Sie auf der TeamViewer-Website im [Handbuch für Fernsteuerung](http://www.teamviewer.com/en/support/documents/).

## <a name="close-the-remote-assistance-session"></a>Beenden der Remoteunterstützungssitzung

Wählen Sie im **TeamViewer**-Fenster im Menü **Aktionen** den Befehl **Sitzung beenden** aus.

## <a name="remotely-restart-a-windows-pc"></a>Remoteneustart eines Windows-PCs
Wenn Sie Ihre Benutzer bei Problemen unterstützen, müssen Sie deren PC möglicherweise von Zeit zu Zeit remote neu starten. Gehen Sie folgendermaßen vor, um einen Remoteneustart für einen Windows-PC auszuführen.

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) die Option **Gruppen** &gt; **Alle Geräte** aus (oder eine andere Gruppe, in der der PC enthalten ist, den Sie erneut starten möchten).

2.  Wählen Sie mindestens einen PC aus, und wählen Sie dann **Remoteaufgaben** &gt; **Computer neu starten**.

3.  Zur Anzeige des Aufgabenstatus wählen Sie **Remoteaufgaben** unten rechts auf der Seite aus.

4.  Überprüfen Sie im Dialogfeld **Taskstatus** die aktuellen Remoteaufgaben, den Aufgabenstatus, den Gerätenamen und etwaige gemeldete Fehler.

### <a name="see-also"></a>Siehe auch

[Allgemeine Aufgaben zur Verwaltung von Windows-PCs mit dem Intune-Softwareclient](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
