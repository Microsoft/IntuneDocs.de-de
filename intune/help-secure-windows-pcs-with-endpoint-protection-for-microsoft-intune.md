---
title: Endpoint Protection für Windows PCs
titleSuffix: Microsoft Intune
description: Sichern Sie Ihre verwalteten Computer mit Endpoint Protection, einer Lösung, die Echtzeitschutz vor Malwarebedrohungen bietet.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 002241bf-6cd0-4c75-a4f0-891ac7e6721a
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: c19c02c8d4c9ece66d03b3510071bb90e7f35ad3
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047515"
---
# <a name="help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune"></a>Schützen von Windows-PCs mit Endpoint Protection für Microsoft Intune

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Microsoft Intune kann Sie unterstützen, Ihre verwalteten Computer mit Endpoint Protection zu schützen, das Echtzeitschutz gegen Bedrohungen durch Schadsoftware bietet, Schadsoftwaredefinitionen auf dem neuesten Stand hält und Computer automatisch überprüft. Endpoint Protection bietet außerdem Tools, mit denen Sie Angriffe durch Schadsoftware kontrollieren und überwachen können.

Falls Sie den Intune-Client noch nicht auf Ihren Computern installiert haben, finden Sie unter [Installieren des Windows-PC-Clients mit Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md) weitere Informationen.

Verwenden Sie die Informationen in den folgenden Abschnitten zum Konfigurieren, Bereitstellen und Überwachen von Endpoint Protection.

## <a name="choose-when-to-use-endpoint-protection"></a>Wann eignet sich Endpoint Protection?
Eine ihrer wichtigsten Aufgaben als IT-Administrator besteht darin, die von Ihnen verwalteten Computer frei von Schadsoftware und Viren zu halten. Bevor Sie Intune auf Windows-PCs in Ihrer Organisation bereitstellen, sollten Sie entscheiden, wie Sie Ihre Computer schützen. Hierzu wählen Sie eine der folgenden Optionen aus und konfigurieren die zugehörigen Richtlinieneinstellungen:


|                                                                                                                                                                       Zweck:                                                                                                                                                                        |                                                                                                       Richtlinieneinstellungen für Endpoint Protection                                                                                                        |                                                                                                                                                  Weitere Informationen                                                                                                                                                  |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                             Microsoft Endpoint Protection nur verwenden, wenn keine Endpunktschutzanwendung von Drittanbietern installiert ist.<br /><br />Sie können Microsoft Intune Endpoint Protection auf allen Computern verwenden, auf denen keine Endpunktschutzanwendung eines Drittanbieters installiert ist.                                              | Endpoint Protection installieren = <strong>Ja</strong><br /><br />Endpoint Protection aktivieren = <strong>Ja</strong><br /><br />Endpoint Protection auch dann installieren, wenn eine Endpunktschutzanwendung von Drittanbietern installiert ist = <strong>Nein</strong>  |                                                                      Wenn die Endpunktschutzanwendung eines Drittanbieters erkannt wird, wird Microsoft Intune Endpoint Protection nicht installiert bzw. deinstalliert, wenn es zuvor installiert war.                                                                       |
| Microsoft Endpoint Protection verwenden, auch wenn eine Endpunktschutzanwendung von Drittanbietern installiert ist.<br /><br />Bei dieser Vorgehensweise führen Sie Microsoft Intune Endpoint Protection und die Endpunktschutzanwendung des Drittanbieters gleichzeitig aus. Von einer solchen Konfiguration wird aufgrund möglicher Leistungsprobleme abgeraten. | Endpoint Protection installieren = <strong>Ja</strong><br /><br />Endpoint Protection aktivieren = <strong>Ja</strong><br /><br />Endpoint Protection auch dann installieren, wenn eine Endpunktschutzanwendung von Drittanbietern installiert ist = <strong>Ja</strong> |                        Zu verwenden in folgenden Fällen:<br /><br />– Sie möchten zur Verwendung von Microsoft Intune Endpoint Protection wechseln.<br />– Sie stellen einen neuen Client bereit, der Microsoft Intune Endpoint Protection verwendet.<br />– Sie aktualisieren einen Client, der Microsoft Intune Endpoint Protection verwendet.                         |
|                                                                                                             Microsoft Intune Endpoint Protection ohne Intune verwenden. Stattdessen greifen Sie auf die Endpunktschutzanwendung eines Drittanbieters zurück.                                                                                                             |                                                                                                Endpoint Protection installieren = <strong>Nein</strong>                                                                                                 | Wenn Sie keine Endpunktschutzanwendung eines Drittanbieters verwenden, wird von dieser Konfiguration abgeraten, denn in diesem Fall wären die Computer in Ihrer Organisation anfällig für Malware oder andere Angriffe.<br /><br />Microsoft Intune Endpoint Protection wird nicht installiert. Eine bereits installierte Instanz wird deinstalliert. |

Führen Sie folgende Schritte aus, um von Ihrer aktuellen Endpunktschutzanwendung zu Microsoft Intune Endpoint Protection zu wechseln:

1.  Beenden Sie Ihre aktuelle Endpunktschutzanwendung nicht, während Sie die Intune-Clientsoftware auf den betreffenden Computern bereitstellen.

2.  Vergewissern Sie sich, dass Microsoft Intune Endpoint Protection installiert ist und die Clientcomputer auf diese Weise geschützt werden.

3.  Entfernen Sie die Endpunktschutzsoftware des Drittanbieters auf folgende Weise:

    -   Stellen Sie über die Intune-Softwareverteilung ein Tool des Herstellers der Endpunktschutzanwendung bereit, mit dessen Hilfe diese entfernt werden kann. Weitere Informationen finden Sie unter [Bereitstellen von Apps in Microsoft Intune](apps-deploy.md).

    -   Entfernen Sie die von einem Drittanbieter stammende Endpunktschutzanwendung manuell.

> [!NOTE]
> Endpunktschutzanwendungen von Drittanbietern werden von Intune nicht automatisch deinstalliert.

## <a name="configure-microsoft-intune-endpoint-protection"></a>Konfigurieren von Microsoft Intune Endpoint Protection
Über die folgenden Schritte können Sie Microsoft Intune Endpoint Protection konfigurieren.

1.  Klicken Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) auf **Richtlinie** > **Richtlinie hinzufügen**.

2.  Erweitern Sie **Computerverwaltung**, und wählen Sie dann **Microsoft Intune-Agent-Einstellungen** aus. Wählen Sie **Benutzerdefinierte Richtlinie erstellen und bereitstellen** aus, um eine Richtlinie für Endpoint Protection-Einstellungen anzugeben. Wählen Sie dann die Schaltfläche **Richtlinie erstellen** aus.

Sie können die empfohlenen Einstellungen verwenden oder die Einstellungen anpassen. Weitere Informationen zum Erstellen und Bereitstellen von Richtlinien finden Sie im Thema [Allgemeine Aufgaben zur Verwaltung von Windows-PCs mit dem Microsoft Intune-Computerclient](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

  ![Endpoint Protection-Einstellungen](media/pol-sa-pc-endpoint-policy.png)

Sie können die bereitgestellte Endpoint Protection-Richtlinie auf der Seite **Alle Richtlinien** des Arbeitsbereichs **Richtlinie** anzeigen.

## <a name="specify-endpoint-protection-service-settings"></a>Festlegen von Endpoint Protection-Diensteinstellungen

|                                                 Richtlinieneinstellung                                                  |                                                                                                                                                                                                                                                                                                                                                                                                             Details                                                                                                                                                                                                                                                                                                                                                                                                             |
|-----------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                  <strong>Endpoint Protection installieren</strong>                                   | Legen Sie hier <strong>Ja</strong> fest, um Endpoint Protection auf verwalteten Computern zu installieren. Wird bei der Installation eine Endpunktschutzanwendung eines Drittanbieters erkannt, wird Endpoint Protection nur installiert, falls die Einstellung <strong>Endpoint Protection auch dann installieren, wenn eine Endpunktschutzanwendung von Drittanbietern installiert ist</strong> auf <strong>Ja</strong> festgelegt ist. <strong>Hinweis:</strong> Intune Endpoint Protection ist auf verwalteten Computern standardmäßig installiert. Wenn Sie nicht möchten, dass Endpoint Protection auf Ihren verwalteten Computern installiert wird, müssen Sie diese Richtlinie explizit auf <strong>Nein</strong> festlegen. Wenn Endpoint Protection zuvor installiert war und die Richtlinie in <strong>Nein</strong> geändert wird, wird der Endpoint Protection-Client deinstalliert.<br />Empfohlener Wert: <strong>Ja</strong> |
| <strong>Endpoint Protection auch dann installieren, wenn eine Endpunktschutzanwendung von Drittanbietern installiert ist</strong> |                                                                                                                                                                                                                                                                                                                Legen Sie diese Option auf <strong>Ja</strong> fest, um Microsoft Endpoint Protection zu installieren, auch wenn eine Endpunktschutzanwendung eines Drittanbieters erkannt wird.<br /><br />Empfohlener Wert: <strong>Ja</strong>                                                                                                                                                                                                                                                                                                                |
|                                   <strong>Endpoint Protection aktivieren</strong>                                   |                                                                                                                                                                                                            Legen Sie diese Option auf <strong>Ja</strong> fest, um Microsoft Intune Endpoint Protection auf Computern zu aktivieren, die über den Endpoint Protection-Client verfügen.<br /><br />Wenn Sie diese Option auf <strong>Nein</strong> festlegen und Endpoint Protection installiert ist, wird den Benutzern die Benutzeroberfläche des Endpoint Protection-Clients nicht angezeigt, und alle Schutzfunktionen sind inaktiv.<br /><br />Empfohlener Wert: <strong>Ja</strong>                                                                                                                                                                                                             |
|                                       <strong>Clientbenutzeroberfläche deaktivieren</strong>                                        |                                                                                                                                                                                                                                                                                                      Legen Sie diese Option auf <strong>Ja</strong> fest, um die Benutzeroberfläche des Microsoft Intune Endpoint Protection-Clients für Benutzer auszublenden. Damit die Einstellung wirksam wird, ist ein Neustart des Clientcomputers erforderlich.<br /><br />Empfohlener Wert: <strong>Nein</strong>                                                                                                                                                                                                                                                                                                       |
| <strong>Endpoint Protection auch dann installieren, wenn eine Endpunktschutzanwendung von Drittanbietern installiert ist</strong> |                                                                                                                                                                                                                                                                                                       Legen Sie diese Option auf <strong>Ja</strong> fest, um die Installation von Microsoft Endpoint Protection zu erzwingen, auch wenn eine Endpunktschutzanwendung eines Drittanbieters erkannt wird.<br /><br />Empfohlener Wert: <strong>Nein</strong>                                                                                                                                                                                                                                                                                                       |
|                    <strong>Vor der Entfernung von Malware einen Systemwiederherstellungspunkt erstellen</strong>                    |                                                                                                                                                                                                                                                                                                                                 Legen Sie hier <strong>Ja</strong> fest, um vor dem Entfernen von Malware einen Windows-Systemwiederherstellungspunkt zu erstellen.<br /><br />Empfohlener Wert: <strong>Ja</strong>                                                                                                                                                                                                                                                                                                                                  |
|                                 <strong>Behandelte Malware nachverfolgen (Tage)</strong>                                  |                                                                                                                                                                                                                                                                                      Ermöglicht Endpoint Protection, erkannte Schadsoftware für einen festgelegten Zeitraum nachzuverfolgen, damit Sie vormals infizierte verwaltete Computer manuell überprüfen können.<br /><br />Sie können einen Wert zwischen 0 und 30 Tagen angeben.<br /><br />Empfohlener Wert: <strong>7 Tage</strong>                                                                                                                                                                                                                                                                                       |

Wenn Sie die Richtlinienwerte für die Einstellungen **Endpoint Protection installieren** und **Endpoint Protection aktivieren** auf **Ja** und den Richtlinienwert für **Endpoint Protection auch dann installieren, wenn eine Endpunktschutzanwendung von Drittanbietern installiert ist** auf **Nein** festgelegt haben, erkennt Microsoft Intune Endpoint Protection, dass eine andere Endpunktschutzanwendung installiert ist. Dies bedeutet, dass Endpoint Protection nicht installiert oder deinstalliert wird, wenn es bereits vorhanden ist. Allerdings meldet Microsoft Intune Endpoint Protection in Intune keine Informationen über die Integrität der anderen Endpunktschutzanwendung.

  Microsoft Security Essentials warnt Sie aufgrund seines Echtzeitschutzes, wenn potenzielle Bedrohungen wie Viren oder Spyware versuchen, sich auf Ihrem PC zu installieren oder auszuführen. In dem Moment, in dem dies passiert, wird ganz rechts auf der Taskleiste eine Meldung im Infobereich angezeigt.

### <a name="specify-real-time-protection-settings"></a>Festlegen von Einstellungen für den Echtzeitschutz

|Richtlinieneinstellung|Details|
|------------------|--------------------|
|**Echtzeitschutz aktivieren**|Hiermit werden Überwachung und Überprüfung aller Dateien und Anwendungen aktiviert, auf die zugegriffen wird. Zudem werden schädliche Dateien oder Anwendungen blockiert, bevor sie auf Computern ausgeführt werden können.<br /><br />Empfohlener Wert: **Ja**|
|**Alle Downloads überprüfen**|Hiermit wird die Überprüfung aller Dateien und Anhänge aktiviert, die aus dem Internet auf Clientcomputer heruntergeladen werden.<br /><br />Empfohlener Wert: **Ja**|
|**Datei- und Programmaktivität auf Computern überwachen**|Hiermit wird die Überwachung eingehender und ausgehender Dateien sowie von Programmaktivitäten auf Computern aktiviert. Mit dieser Einstellung kann Endpoint Protection überwachen, wann die Ausführung von Dateien und Programmen beginnt, und Sie werden über alle Aktionen informiert, die von bzw. an ihnen durchgeführt werden.<br /><br />Empfohlener Wert: **Ja**|
|**Überwachte Dateien**|Ermöglicht Ihnen anzugeben, ob nur eingehende, nur ausgehende oder alle Dateien überwacht werden.<br /><br />Empfohlener Wert: **Alle Dateien überwachen**|
|**Aktivieren der Verhaltensüberwachung**|Mit dieser Richtlinieneinstellung kann Microsoft Intune Endpoint Protection Clientcomputer auf bestimmte verdächtige Aktivitätsmuster prüfen.<br /><br />Empfohlener Wert: **Ja**|
|**Netzwerkinspektionssystem aktivieren**|Hiermit wird das Netzwerkinspektionssystem (NIS) auf Clientcomputern aktiviert. Im NIS werden Signaturen bekannter Sicherheitsrisiken aus dem [Microsoft Malware Protection Center (Microsoft Center zum Schutz vor Malware)](https://go.microsoft.com/fwlink/?LinkId=234249) verwendet, um schädlichen Netzwerkdatenverkehr zu erkennen und zu blockieren.<br /><br />Empfohlener Wert: **Ja**|

  ![Echtzeiteinstellungen für Endpoint Protection](media/pol-sa-pc-policy-realtime.png)

### <a name="specify-scan-schedule-settings"></a>Einstellungen für den Überprüfungszeitplan

|Richtlinieneinstellung|Weitere Informationen|
|------------------|--------------------|
|**Tägliche Schnellüberprüfung planen**|Hiermit wird eine tägliche Schnellüberprüfung von häufig verwendeten Dateien und wichtigen Systemdateien auf verwalteten Computern geplant. Diese Schnellüberprüfung wirkt sich geringfügig auf die Leistung aus.<br /><br />Empfohlener Wert: **Ja**|
|**Schnellüberprüfung ausführen, wenn zwei aufeinanderfolgende Schnellüberprüfungen verpasst wurden**|Hiermit wird Endpoint Protection so konfiguriert, dass automatisch eine Schnellüberprüfung auf Computern ausgeführt wird, wenn bei diesen zwei aufeinanderfolgende Schnellüberprüfungen verpasst wurden.<br /><br />Empfohlener Wert: **Ja**|
|**Vollständige Überprüfung planen**|Hiermit wird eine vollständige Überprüfung aller Dateien und Ressourcen auf den lokalen Computerfestplatten konfiguriert. Diese Überprüfung kann einige Zeit in Anspruch nehmen und sich auf die Computerleistung auswirken (die erforderliche Zeit hängt von der Anzahl der überprüften Dateien und Ressourcen ab).<br /><br />Empfohlener Wert: **Nein**|
|**Vollständige Überprüfung ausführen, wenn zwei aufeinanderfolgende vollständige Überprüfungen verpasst wurden**|Hiermit wird Endpoint Protection so konfiguriert, dass automatisch eine vollständige Überprüfung auf Computern ausgeführt wird, wenn bei diesen zwei aufeinanderfolgende Überprüfungen verpasst wurden.<br /><br />Empfohlener Wert: Nicht konfiguriert|

### <a name="specify-scan-options-settings"></a>Festlegen von Einstellungen für Überprüfungsoptionen

|Richtlinieneinstellung|Details|
|------------------|--------------------|
|**Nach der Installation von Endpoint Protection eine vollständige Überprüfung ausführen**|Auf **Ja** festlegen, um nach der Installation auf Computern automatisch eine vollständige Systemüberprüfung ausführen zu lassen. Um Auswirkungen auf die Benutzerproduktivität zu minimieren, wird diese Überprüfung nur ausgeführt, wenn sich die entsprechenden Computer im Leerlauf befinden.<br /><br />Empfohlener Wert: **Ja**|
|**Bei Bedarf automatisch eine vollständige Überprüfung nach der Beseitigung von Malware ausführen**|Legen Sie diese Option auf **Ja** fest, damit von Endpoint Protection nach dem Entfernen von Schadsoftware automatisch eine vollständige Systemüberprüfung auf Computern durchgeführt wird, um zu bestätigen, dass andere Dateien nicht betroffen waren.<br /><br />Empfohlener Wert: **Ja**|
|**Geplante Überprüfung nur starten, wenn sich der Computer im Leerlauf befindet**|Legen Sie hier **Ja** fest, um zu verhindern, dass geplante Überprüfungen auf Computern gestartet werden, während diese benutzt werden, und so eine Beeinträchtigung der Benutzerproduktivität zu vermeiden.<br /><br />Empfohlener Wert: **Ja**|
|**Vor dem Start der Überprüfung die aktuellsten Malwaredefinitionen abrufen**|Legen Sie diese Option auf **Ja** fest, um Endpoint Protection so zu konfigurieren, dass vor einer Überprüfung von Clientcomputern automatisch nach den neuesten Schadsoftwaredefinitionen gesucht wird.<br /><br />Empfohlener Wert: **Ja**|
|**Archivdateien überprüfen**|Legen Sie hier **Ja** fest, um Endpoint Protection so zu konfigurieren, dass Archivdateien wie ZIP- oder CAB-Dateien auf Computern auf Schadsoftware überprüft werden.<br /><br />Empfohlener Wert: **Nein**|
|**E-Mail-Nachrichten überprüfen**|Legen Sie diese Option auf **Ja** fest, um Endpoint Protection so zu konfigurieren, dass auf Computern eingehende E-Mail-Nachrichten überprüft werden.<br /><br />Empfohlener Wert: **Ja**|
|**Dateien überprüfen, die in freigegebenen Netzwerkordnern geöffnet wurden**|Legen Sie diese Option auf **Ja** fest, um Endpoint Protection zum Überprüfen von Dateien zu konfigurieren, die in freigegebenen Netzwerkordnern geöffnet werden. In der Regel sind dies Dateien, auf die über einen UNC-Pfad (Universal Naming Convention) zugegriffen wird. Die Aktivierung dieser Funktion kann Benutzern Probleme bereiten, die nur über Lesezugriff verfügen, da sie Malware nicht entfernen können.<br /><br />Empfohlener Wert: **Nein**|
|**Zugeordnete Netzwerklaufwerke überprüfen**|Legen Sie diese Option auf **Ja** fest, um Endpoint Protection für das Überprüfen von Dateien auf zugeordneten Netzwerklaufwerken zu konfigurieren. Die Aktivierung dieser Funktion kann Benutzern Probleme bereiten, die nur über Lesezugriff verfügen, da sie Malware nicht entfernen können.<br /><br />Empfohlener Wert: **Nein**|
|**Wechseldatenträger überprüfen**|Legen Sie diese Option auf **Ja** fest, um Endpoint Protection für das Überprüfen von Wechseldatenträgern (z. B. USB-Sticks) auf Schadsoftware und unerwünschte Software beim Ausführen einer vollständigen Überprüfung auf Computern zu konfigurieren.<br /><br />Empfohlener Wert: **Ja**|
|**CPU-Auslastung während einer Überprüfung begrenzen**|Legt den maximalen Prozentsatz der Prozessornutzung fest, der bei geplanten Überprüfungen auf Clientcomputern beansprucht werden darf. Sie können hierfür einen Wert zwischen 1 und 100 Prozent festlegen.<br /><br />Empfohlener Wert: **50 %**|

### <a name="choose-default-actions-settings"></a>Auswählen der Standardeinstellungen für Aktionen

Die Einstellung **Auswählen, wie von Endpoint Protection mit Malware der folgenden Warnstufen verfahren werden soll** gibt die Standardaktion an, die Endpoint Protection ausführt, wenn Schadsoftware mit verschiedenen Warnstufen erkannt wird. Sie können für jede Warnstufe festlegen, dass die Malware entfernt oder in Quarantäne versetzt oder die von Microsoft empfohlene Aktion ausgeführt wird.

Empfohlener Wert: **Empfohlene Aktion** ermöglicht Endpoint Protection das Empfehlen einer Aktion.   

### <a name="decide-whether-to-choose-the-excluded-files-and-folders-settings"></a>Entscheiden, ob die Einstellungen für ausgeschlossene Dateien und Ordner verwendet werden sollen

Die Einstellung **Von der Überprüfung oder dem Echtzeitschutz auszuschließende Dateien und Ordner** schließt bestimmte Dateien und Ordner aus, wenn eine Überprüfung ausgeführt wird oder Echtzeitschutz auf Computern aktiv ist.

### <a name="decide-whether-to-choose-the-excluded-processes-settings"></a>Entscheiden, ob die Einstellungen für ausgeschlossene Prozesse verwendet werden sollen

Die Einstellung **Prozesse, die beim Ausführen einer Überprüfung oder bei Verwendung des Echtzeitschutzes auszuschließen sind** schließt bestimmte Prozesse aus, wenn eine Überprüfung ausgeführt wird oder Echtzeitschutz auf Computern aktiv ist. Sie können nur Dateien mit der Erweiterung **.exe**, **.com** und **.scr** ausschließen.

### <a name="decide-whether-to-choose-the-excluded-file-types-settings"></a>Entscheiden, ob die Einstellungen für ausgeschlossene Dateitypen verwendet werden sollen

Die Einstellung **Dateierweiterungen, die beim Ausführen einer Überprüfung oder bei Verwendung des Echtzeitschutzes auszuschließen sind** schließt bestimmte Dateinamenerweiterungen aus, wenn eine Überprüfung ausgeführt wird oder Echtzeitschutz auf Computern aktiv ist.

### <a name="specify-microsoft-active-protection-service-settings"></a>Einstellungen für Microsoft Active Protection Service angeben
Microsoft Active Protection Service ist eine Online-Community, die Ihnen hilft zu entscheiden, wie Sie auf potenzielle Bedrohungen reagieren. Diese Community trägt auch dazu bei, die Weiterverbreitung neuer Infektionen mit Malware zu unterbinden. Sie können **Microsoft Active Protection Service beitreten**, indem Sie **Ja** auswählen und dann Ihre **Mitgliedschaftsstufe** angeben:
  - **Standard**: Hierbei werden grundlegende Informationen zu erkannter Schadsoftware an Microsoft gesendet. Hierzu gehören Angaben dazu, woher die Software stammt, welche Aktionen Sie anwenden oder von Endpoint Protection automatisch angewendet werden und ob diese Aktionen erfolgreich waren.
  - **Premium**: Hierbei werden zusätzliche Informationen über Schadsoftware, Spyware oder möglicherweise unerwünschte Software an Microsoft gesendet. Hierzu gehören Informationen zum Speicherort der Software, den Dateinamen, der Funktionsweise der Software und der Auswirkung der Software auf Ihren Computer.

Sie können auch **Dynamische Definitionen auf Basis von Microsoft Active Protection Service-Berichten empfangen**.

## <a name="choose-management-tasks-for-endpoint-protection"></a>Auswählen von Verwaltungsaufgaben für Endpoint Protection
Mithilfe der folgenden Aufgaben können Sie verschiedene Verwaltungsaufgaben auf verwalteten Computern ausführen, auf denen Endpoint Protection ausgeführt wird:
- Update für Malwaredefinitionen ausführen
  - Intune-Konsole: Wählen Sie im Arbeitsbereich **Gruppen** die zu aktualisierenden Computer aus. Wählen Sie **Remoteaufgaben** &gt; **Update für Malwaredefinitionen ausführen** aus.
  - Verwaltete Computer: Starten Sie die Endpoint Protection-Clientsoftware über den Benachrichtigungsbereich von Windows. Wählen Sie die Registerkarte **Aktualisieren** und dann **Aktualisieren** aus.
- Malwareüberprüfung ausführen:
  - Intune-Konsole: Wählen Sie im Arbeitsbereich **Gruppen** die zu überprüfenden Computer aus. Wählen Sie **Vollständige Malwareüberprüfung ausführen** oder **Malwareschnellüberprüfung ausführen** aus.
  - Verwaltete Computer: Starten Sie die Endpoint Protection-Clientsoftware über den Benachrichtigungsbereich von Windows. Wählen Sie **Schnell**, **Vollständig**oder **Benutzerdefiniert** und dann **Jetzt überprüfen** aus.

Zur Anzeige des Status einer Remoteaufgabe wählen Sie rechts unten in der Intune-Konsole den Link **Remoteaufgaben** aus. Im Dialogfeld **Taskstatus** werden die aktuellen Remoteaufgaben, der Aufgabenstatus, der Gerätename und etwaige gemeldete Fehler aufgelistet. Es enthält außerdem einen Link zu Informationen zur Problembehandlung, sollte er benötigt werden.

## <a name="monitor-endpoint-protection"></a>Überwachen von Endpoint Protection
Sie können den Malwarestatus Ihrer Computer mithilfe des Arbeitsbereichs **Schutz** der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/)überwachen. Dieser Arbeitsbereich enthält zwei Seiten:
- **Übersicht über Endpoint Protection**: Hier werden wichtige Probleme als Links angezeigt, die Sie auswählen können, um weitere Informationen zu erhalten. Die folgenden Arten von Problemen können angezeigt werden:
  - **Instanzen von Schadsoftware, die Nachverfolgung erfordern**: Klicken Sie auf den Link, um eine Liste mit Schadsoftwareproblemen sowie den zur Lösung des jeweiligen Problems erforderlichen Folgemaßnahmen anzuzeigen. Sie können diese Liste weiter durchsuchen, um festzustellen, welche Computer betroffen sind.
  - **Computer mit Schadsoftware, die Nachverfolgung erfordern**: Klicken Sie auf den Link, um alle Computer mit ungelösten Schadsoftwareproblemen sowie den zur Lösung des jeweiligen Problems erforderlichen Folgemaßnahmen anzuzeigen.
  - **Ungeschützte Geräte**: Klicken Sie auf den Link, um Computer anzuzeigen, die von keiner Endpunktschutzsoftware geschützt sind, weil eine solche Software entweder nicht installiert ist, oder weil ein Fehler aufgetreten ist. Wählen Sie einen Computer aus, um weitere Details anzuzeigen.
  - **Geräte, auf denen eine andere Endpunktschutzanwendung ausgeführt wird**: Klicken Sie auf den Link, um Computer anzuzeigen, auf denen die Endpunktschutzanwendung eines Drittanbieters ausgeführt wird.
- **Sämtliche Malware**: Hiermit wird eine Liste der gesamten auf Ihren Computern gefundenen aktiven Schadsoftware angezeigt. Sie können diese Liste durchsuchen, um alle Computer anzuzeigen, die von einer bestimmten Schadsoftware betroffen sind, oder eine der folgenden Aufgaben auswählen:
  - **Eigenschaften anzeigen**: Es wird eine Seite mit weiteren Informationen zur ausgewählten Schadsoftware geöffnet.
  - **Informationen zu dieser Schadsoftware**: Es wird ein Thema aus dem Microsoft Malware Protection Center mit weiteren Informationen zur Schadsoftware geöffnet.

> [!IMPORTANT]
> Der Arbeitsbereich **Schutz** wird in der Verwaltungskonsole erst angezeigt, wenn Sie den Client installiert haben und mindestens einen Computerclient verwalten.

  ![Überwachen von Endpoint Protection](media/pol-sa-ep-monitor.png)

### <a name="how-to-view-recent-detection-paths-for-malware-on-computers"></a>Anzeigen der letzten Erkennungspfade für Malware auf Computern
Intune kann die Pfade von bis zu 10 der zuletzt erkannten Instanzen von Malware auf einem Gerät anzeigen. Die Option **Letzter Erkennungspfad** ist standardmäßig deaktiviert. So aktivieren Sie diese Anzeige:

1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) **Gruppen** > **Alle Geräte** > **Alle Computer**.
2. Klicken Sie mit der rechten Maustaste auf den Computer, dessen aktuelle Erkennungspfade Sie anzeigen möchten, und wählen Sie **Eigenschaften**.
3. Wählen Sie **Malware** aus den Registerkarten am oberen Rand.

   ![Wählen Sie die Registerkarte „Malware“, und klicken Sie dann auf das Kontrollkästchen „Aktuelle Erkennungspfade“.](media/malware-path-column.png)
4. Klicken Sie mit der rechten Maustaste auf die Spaltenüberschrift. Eine Liste der verfügbaren Spalten wird angezeigt. Aktivieren Sie das Kontrollkästchen **Letzte Erkennungspfade** in der Liste. Die Spalte **Letzte Erkennungspfade** wird angezeigt. Sie enthält bis zu 10 der zuletzt auf dem Gerät überwachten Malwareinstanzen.

## <a name="run-a-malware-scan-or-update-malware-definitions-on-a-computer"></a>Ausführen einer Malwareüberprüfung oder Aktualisieren von Malwaredefinitionen auf einem Computer
Intune kann auf einem remoteverwalteten PC, auf dem der Intune-Client installiert wurde, entweder eine vollständige oder schnelle Malwareüberprüfung mithilfe von Endpoint Protection oder Windows Defender ausführen.

1. Gehen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) zu **Gruppen** > **Übersicht** > **Alle Geräte** > **Alle Computer**, und wählen Sie dann den Computer aus, der verwendet werden soll.

2. Wählen Sie die Dropdownliste **Remoteaufgaben** und anschließend die Aufgabe aus, die auf dem Remotecomputer ausgeführt werden soll.

## <a name="need-more-help"></a>Benötigen Sie weitere Hilfe?
Weitere Hilfe und Unterstützung erhalten Sie unter [Troubleshoot Endpoint Protection in Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md) (Problembehandlung für Endpoint Protection in Microsoft Intune).

### <a name="see-also"></a>Weitere Informationen
[Richtlinien zum Schutz von Windows-PCs](policies-to-protect-windows-pcs-in-microsoft-intune.md)
