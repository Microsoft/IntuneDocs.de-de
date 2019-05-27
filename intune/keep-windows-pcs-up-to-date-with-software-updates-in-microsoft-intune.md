---
title: Softwareupdates für Windows-PCs
titleSuffix: Microsoft Intune
description: Intune unterstützt Sie dabei, Ihre verwalteten Computer auf dem neuesten Stand zu halten, indem sichergestellt wird, dass aktuelle Patches und Softwareupdates ohne Verzögerung installiert werden.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 48e9c41a-d2de-424e-9610-cfd1ad514210
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 56bbe6d8af43693814a90351acb2f400cff92025
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66046990"
---
# <a name="keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune"></a>Aktualisieren Ihrer Windows-PCs mit Softwareupdates in Microsoft Intune

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Microsoft Intune unterstützt Sie auf vielfältige Weise beim Schutz Ihrer verwalteten Computer, z.B. durch die Verwaltung von Softwareupdates. Dadurch ist sichergestellt, dass die neuesten Patches und Softwareupdates schnell installiert werden, sodass Ihre Computer immer auf dem neuesten Stand sind.

Falls Sie den Intune-Client noch nicht auf Ihren Computern installiert haben, finden Sie unter [Installieren des Windows-PC-Clients mit Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md) weitere Informationen.

Wenn neue Updates bei Microsoft Update verfügbar sind oder Sie ein Drittanbieterupdate erstellt haben und diese Updates auf die von Ihnen verwalteten Computer anwendbar sind, wird eine Benachrichtigung auf der Seite **Übersicht** des Arbeitsbereichs **Updates** angezeigt. Nachdem Sie auf diesen Benachrichtigungslink geklickt haben, können Sie verschiedene Vorgänge durchführen. Sie können beispielsweise weitere Informationen zum Update anzeigen, das Update genehmigen oder ablehnen und die Computer anzeigen, auf denen das Update im Fall der Genehmigung installiert wird.

> [!IMPORTANT]
> Der Arbeitsbereich **Updates** wird in der Administratorkonsole erst angezeigt, wenn Sie den Client installiert haben und Sie mindestens einen Computerclient erfolgreich verwalten.

Wenn Updates genehmigt und installiert werden, können Sie den Erfolg oder Misserfolg der Installation im Arbeitsbereich **Updates** der Intune-Konsole untersuchen.

Verwenden Sie die Informationen in den folgenden Abschnitten, um die Software auf den von Ihnen verwalteten Computern auf dem aktuellen Stand zu halten.

## <a name="before-you-start"></a>Vorbereitung
Bevor Sie mit dem Erstellen und Genehmigen von Softwareupdates beginnen, konfigurieren Sie Richtlinien, mit denen gesteuert wird, wann und wie die Updates installiert werden, und stellen Sie diese auf Ihren Computern bereit.

### <a name="to-configure-update-policy-settings"></a>So konfigurieren Sie Einstellungen für Updaterichtlinien

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) die Optionen **Richtlinie** &gt; **Übersicht** &gt; **Richtlinie hinzufügen**.

2.  Konfigurieren Sie eine Richtlinie für **Microsoft Intune-Agent-Einstellungen** für die Update-Einstellungen, und stellen Sie sie bereit. Sie können die empfohlenen Einstellungen verwenden oder die Einstellungen anpassen. Weitere Informationen zum Erstellen und Bereitstellen von Richtlinien finden Sie unter [Allgemeine Aufgaben zur Verwaltung von Windows-PCs mit dem Microsoft Intune-Computerclient](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

In den folgenden Tabellen sind die Werte, die Sie in der Richtlinie konfigurieren können, sowie die empfohlenen Werte aufgeführt, die verwendet werden, wenn Sie die Richtlinie nicht anpassen. Sie finden diese Einstellungen im Bereich **Updates** .

  |Richtlinieneinstellung|Details|
    |------------------|--------------------|
    |**Häufigkeit der Suche nach Updates und Anwendungen (Stunden)** |Gibt an, wie häufig (8 bis 22 Stunden) Intune Überprüfungen auf neue Updates und Anwendungen ausführt.<br /><br />Empfohlener Wert: **8** Stunden.|
    |**Automatische Installation von Updates und Anwendungen oder Installation auf Aufforderung** |Hiermit wird festgelegt, ob Updates automatisch installiert werden, oder ob vor der Installation eine Benutzeraufforderung angezeigt wird. Darüber hinaus können Sie mit dieser Einstellung die Installation von Updates und Anwendungen planen.<br /><br />**Mit der automatischen Installation von Updates und Anwendungen nach Plan** werden Updates und Anwendungen unter Berücksichtigung des angegebenen Zeitplans installiert.<br /><br />**Automatische Wartung für Windows-Computer verwenden** ist eine abhängige Richtlinieneinstellung und gibt an, dass Updates und Anwendungen während des automatischen Wartungsfensters von Windows installiert werden.<br /><br />Mit **Benutzer zur Installation auffordern** wird der Benutzer zur Installation aufgefordert, wenn Updates bereitstehen.<br /><br />Empfohlene Werte:<br /><br />**Updates und Anwendungen automatisch wie geplant installieren** aktiviert<br /><br />**Geplant am: Täglich**<br /><br />**Geplante Zeit: 03:00 Uhr**<br /><br />**Automatische Wartung für Windows-Computer verwenden** aktiviert|
    |**Sofortige Installation von Updates zulassen, die Windows nicht unterbrechen** |**Zulassen** installiert Updates sofort nach dem Herunterladen, außer Updates, die Windows unterbrechen oder neu starten würden. Diese Updates werden entsprechend der Konfiguration der Einstellung **Automatische Installation oder Updateinstallation nach Aufforderung** installiert.<br /><br />Durch **Nicht zulassen** werden Updates entsprechend der Konfiguration der Einstellung **Automatische Installation von Updates oder Installation auf Aufforderung** installiert.<br /><br />Empfohlener Wert: **Allow** |
    |**Verzögerung des Windows-Neustarts nach der Installation geplanter Updates und Anwendungen (in Minuten)** |Hiermit wird angegeben, wie lange nach der Installation geplanter Updates und Anwendungen gewartet werden soll, bevor Windows neu gestartet wird. Der Wertebereich liegt zwischen 1 und 30 Minuten.<br /><br />Empfohlener Wert: **15 Minuten** |
    |**Verzögerung nach einem Windows-Neustart bis zum Beginn der Installation verpasster geplanter Updates und Anwendungen (Minuten)** |Hiermit wird festgelegt, wie viel Zeit nach einem Windows-Neustart verstreichen darf, bis mit der Installation von Updates und Anwendungen begonnen wird, wenn ein geplantes Update verpasst wurde. Der Wertebereich liegt zwischen 1 und 60 Minuten.<br /><br />Empfohlener Wert: **5 Minuten**|
    |**Angemeldetem Benutzer die Steuerung des Windows-Neustarts nach der Installation geplanter Updates und Anwendungen gestatten** |Hiermit wird angegeben, ob der angemeldete Benutzer den Neustart von Windows verzögern kann (Einstellung **Ja**) oder über den automatischen Neustart von Windows benachrichtigt wird (Einstellung **Nein**). Wenn zum Zeitpunkt der Installation geplanter Updates und Anwendungen kein Benutzer angemeldet ist, wird Windows bei Bedarf automatisch neu gestartet. Bei der Einstellung **Nein**ist die Zeit bis zum Windows-Neustart standardmäßig auf 5 Minuten festgelegt.<br /><br />Empfohlener Wert: **Ja**|
    |**Benutzer zum Neustarten von Windows während obligatorischer Updates des Client-Agents von Microsoft Intune auffordern** |Hiermit wird festgelegt, ob angemeldete Benutzer zum Neustart von Windows aufgefordert werden, wenn ein obligatorisches Update des Intune-Clients einen Windows-Neustart erfordert.<br /><br />Empfohlener Wert: **Ja**|
    |**Zeitplan für die Installation von obligatorischen Updates des Client-Agents von Microsoft Intune** |Hiermit wird geplant, wann die Installation von Clientupdates stattfindet.<br /><br />Empfohlener Wert: "nicht konfiguriert"|
    |**Verzögerung zwischen Aufforderungen zum Neustart von Windows nach Installation geplanter Updates und Anwendungen (in Minuten)** |Hiermit wird angegeben, wie häufig der Benutzer aufgefordert wird, Windows neu zu starten, wenn nach der Installation eines Updates oder eine Anwendung ein Windows-Neustart erforderlich ist und der Benutzer diesen Neustart verzögert. Der Wertebereich liegt zwischen 1 und 1440 Minuten.<br /><br />Empfohlener Wert: **30 Minuten** |

## <a name="update-software-made-by-microsoft"></a>Aktualisieren von Microsoft-Software
Das Aktualisieren von Microsoft-Software ist sehr unkompliziert. Bevor Sie jedoch beginnen, müssen Sie zweierlei konfigurieren:

-   **Produktkategorien und Updateklassifizierungen:** Hiermit werden die Kategorien und Klassifizierungen der Updates definiert, die Sie auf Computern verfügbar machen möchten. Sie können beispielsweise festlegen, dass nur kritische Updates für Microsoft Office installiert werden.

-   **Automatische Genehmigungsregeln:** Mit diesen Regeln werden bestimmte Arten von Updates automatisch genehmigt, wodurch der Verwaltungsaufwand verringert wird. Sie sollten beispielsweise automatisch alle kritischen Softwareupdates genehmigen.

Bereiten Sie die Verwendung von Softwareupdates mithilfe der folgenden beiden Verfahren vor:

### <a name="configure-the-product-categories-and-update-classifications-you-want-to-make-available-to-managed-computers"></a>Konfigurieren Sie die Produktkategorien und Updateklassifizierungen, die Sie auf verwalteten Computern verfügbar machen möchten.

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) die Option **Admin** &gt; **Updates** aus.

2.  Wählen Sie auf der Seite **Diensteinstellungen: Updates** in der Liste **Produktkategorie** die Updatekategorien aus, die Sie auf Computern verfügbar machen möchten. Beachten Sie, dass die am häufigsten verwendeten Updates standardmäßig aktiviert sind.

    > [!IMPORTANT]
    > Damit sichergestellt ist, dass Computer die vom Administrator genehmigten Updates erhalten, darf die Windows Server Update Services-Gruppenrichtlinieneinstellung **Internen Pfad für den Microsoft Updatedienst angeben** auf die bei Intune registrierten Computer nicht angewendet werden.

3.  Wählen Sie in der Liste **Updateklassifizierung** die Updateklassen aus, die Sie auf verwalteten Computern verfügbar machen möchten. Auch hier sind die am häufigsten verwendeten Optionen standardmäßig aktiviert.

4.  Klicken Sie auf **Speichern**, um Ihre Auswahl zu speichern.

### <a name="to-configure-automatic-approval-rules-for-software-updates"></a>So konfigurieren Sie automatische Genehmigungsregeln für Softwareupdates

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) die Option **Admin** &gt; **Updates** aus.

2.  Wählen Sie im Abschnitt **Automatische Genehmigungsregeln** der Seite **Servereinstellungen: Updates** **Neu** aus.

3.  Geben Sie auf der Seite **Allgemein** des Assistenten zum Erstellen von automatischen Genehmigungsregeln einen Namen und optional eine Beschreibung für die Regeln an.

4.  Wählen Sie auf der Seite **Produktkategorien** alle Produkte aus, für die Updates automatisch genehmigt werden sollen.

5.  Geben Sie auf der Seite **Updateklassifizierungen** die Updateklassifizierungen an, die automatisch genehmigt werden sollen.

6.  Gehen Sie auf der Seite **Bereitstellung** folgendermaßen vor:

    -   Wählen Sie die Computergruppen aus, für die die neue Regel bereitgestellt werden soll, und wählen Sie anschließend **Hinzufügen** aus.

    -   Aktivieren Sie zum Angeben eines Installationszeitlimits für die Updates das Kontrollkästchen **Erzwingen Sie ein Installationszeitlimit für diese Updates** , und wählen Sie aus der Liste **Installationszeitlimit** ein Installationszeitlimit aus.

        > [!NOTE]
        > Wenn Sie ein Installationszeitlimit angeben, muss der verwaltete Computer nach Ablauf des entsprechenden Intervalls möglicherweise einmal oder mehrmals neu gestartet werden.

    -   Wählen Sie anschließend **Weiter** aus.

7.  Überprüfen Sie auf der Seite **Zusammenfassung** die Einstellungen für die neue Regel, und wählen Sie anschließend **Fertig stellen** aus.

Die neue Regel wird im Bereich **Automatische Genehmigungsregeln** auf der Seite **Diensteinstellungen: Updates** angezeigt.

> [!NOTE]
> Wenn Sie eine automatische Genehmigungsregel erstellen, gilt diese nur für künftige Updates. In Intune bereits vorhandene Updates werden nicht automatisch genehmigt. Zum Genehmigen dieser Updates müssen Sie die automatische Genehmigungsregel ausführen.


### <a name="to-edit-run-or-delete-an-automatically-approved-update-rule"></a>So können Sie eine Regel für die automatische Genehmigung von Updates bearbeiten, ausführen oder löschen

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) die Option **Admin** &gt; **Updates** aus.

2.  Wählen Sie im Bereich **Automatische Genehmigungsregeln** eine Regel aus, und führen Sie dann einen der folgenden Schritte aus:

    -   Wählen Sie zum Bearbeiten der Regel **Bearbeiten** aus, und ändern Sie anschließend im **Assistenten für automatische Update-Genehmigungsregeln** die Parameter der Regel.

    -   Wählen Sie **Ausgewählten Satz ausführen** aus, um die Regel auszuführen.

    -   Wählen Sie **Löschen** aus, um die Regel zu löschen.

        > [!NOTE]
        > Das Löschen einer Regel hat keine Auswirkungen auf vorherige Updates, die durch diese Regel genehmigt wurden.

## <a name="update-software-not-made-by-microsoft"></a>Aktualisieren von Software, die nicht von Microsoft herausgegeben wird
Sie können Updates für Software bereitstellen, die nicht von Microsoft stammt. Hierzu verwenden Sie den **Assistenten zum Hochladen von Updates** , mit dem Sie das Update in Ihren Cloud Speicher hochladen; danach können Sie das Update ebenso wie bei Microsoft-Software genehmigen oder ablehnen.

### <a name="to-upload-and-configure-a-third-party-update"></a>So laden Sie ein Drittanbieterupdate hoch und konfigurieren es

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) **Updates** &gt; **Übersicht** &gt; **Hochladen** aus.

2.  Klicken Sie auf der Seite **Updatedateien** auf **Durchsuchen**, um die Setupdateien auszuwählen, die zur Installation des Updatepakets benötigt werden. Hierbei kann es sich um eine Windows Installer-Datei (MSI), eine Windows Installer-Patchdatei (MSP) oder eine Programmdatei (EXE) handeln. Außerdem können Sie ggf. zusätzliche Dateien oder Ordner einschließen, die sich im selben Ordner wie die Setupdatei befinden.

    Die Gesamtgröße der ausgewählten hochzuladenden Dateien wird angezeigt. Beachten Sie, dass diese Größe nicht die unkomprimierten Größen der Installationsdateien beinhaltet.

3.  Nachdem Sie die Setupdateien angegeben haben, werden auf der Seite **Updatebeschreibung** der Name, die Beschreibung und die Klassifizierung für Softwareinformationen angezeigt, die von Intune aus den Softwaresetupdateien extrahiert wurden. Sie können eine Klassifizierung auswählen, um den Typ des bereitzustellenden Updates zu markieren (Updates, Kritische Updates, Sicherheitsupdates, Updaterollups oder Service Packs). Klicken Sie auf **Weiter**, wenn Sie fertig sind.

4.  Wählen Sie auf der Seite **Anforderungen** des Assistenten die Architektur (32 und/oder 64 Bit) und die Betriebssysteme der verwalteten Computer aus, auf die das Update anwendbar sein soll.

5.  Geben Sie auf der Seite **Erkennungsregeln** an, wie von Intune bestimmt wird, ob ein Update bereits auf verwalteten Computern vorhanden ist. Wenn Sie die Standardoption **Standarderkennungsregeln verwenden** nutzen, wird das Updatepaket von Intune auf jedem Zielcomputer genau einmal installiert.

    > [!NOTE]
    > Wenn es sich bei der von Ihnen angegebenen Updatesetupdatei um eine Windows Installer- oder MSP-Datei handelt, wird die Seite **Erkennungsregeln** des Assistenten nicht angezeigt. Dies liegt daran, dass Windows Installer- und MSP-Dateien über eigene Anweisungen zum Erkennen vorheriger Updateinstallationen verfügen.

    Wählen Sie mindestens eine der folgenden Regeln aus, um festzustellen, ob das Update bereits auf verwalteten Computern installiert ist:

    -   **Die Datei ist vorhanden**

    -   **Der MSI-Produktcode ist vorhanden**

    -   **Der Registrierungsschlüssel ist vorhanden**

6.  Geben Sie alle weiteren, für die Konfiguration der Erkennungsregel erforderlichen Informationen an – beispielsweise einen Dateipfad und -namen, den Windows Installer-Produktcode oder einen Registrierungsschlüssel – und wählen Sie anschließend **Weiter** aus.

7.  Auf der Seite **Erforderliche Komponenten** des Assistenten geben Sie an, welche Software bereits installiert sein muss, damit dieses Update installiert werden kann. Sie können **Keine**angeben, ein bereits hinzugefügtes und von Intune verwaltetes Softwarepaket auswählen oder eine der folgenden Regeln zur Beschreibung der Software angeben:

    -   **Die Datei ist vorhanden**

    -   **Der MSI-Produktcode ist vorhanden**

    -   **Der Registrierungsschlüssel ist vorhanden**

8.  Geben Sie alle weiteren, für die Konfiguration der Erkennungsregel erforderlichen Informationen an – beispielsweise einen Dateipfad und -namen, den Windows Installer-Produktcode oder einen Registrierungsschlüssel – und wählen Sie anschließend **Weiter** aus.

9. Auf der Seite **Befehlszeilenargumente** des Assistenten können Sie erforderliche Installationseigenschaften zur Installationsbefehlszeile hinzufügen, um das Verhalten der Setupdatei zu ändern. Beispielsweise unterstützen verschiedene Softwareprogramme die Eigenschaft **/q** zum Ermöglichen einer automatischen Installation. Weitere Informationen zu unterstützten Befehlszeilenargumenten finden Sie in der Dokumentation zu Ihrem Softwarepaket. Geben Sie die ggf. erforderlichen Befehlszeilenargumente an, und wählen Sie anschließend **Weiter** aus.

    > [!NOTE]
    > Wird vom Update keine automatische Installation unterstützt, können Sie es nicht mithilfe von Intune installieren.

10. Auf der Seite **Rückgabecodes** des Assistenten können Sie angeben, wie Rückgabecodes der Updateinstallation interpretiert werden. Standardmäßig werden in Intune die branchenüblichen Rückgabecodes verwendet, um eine fehlerhafte oder erfolgreiche Installation eines Updatepakets zu melden. Die bereitgestellten Rückgabecodes sind:

|Rückgabecode|Details|
|---------------|------------------|
|**0**|Erfolgreich|
|**3010**|Erfolg mit Neustart|

11. Alle nicht aufgeführten Rückgabecodes weisen auf Fehler bei der Installation hin.
Bei einigen Updates gelten die Standardinterpretationen für Rückgabecodes nicht. In diesem Fall können Sie eigene Interpretationen für die Rückgabecodes angeben.

12. Geben Sie die erforderlichen Rückgabecodes an, oder bearbeiten Sie sie, und klicken Sie anschließend auf **Weiter**.

13. Überprüfen Sie auf der Seite **Zusammenfassung** des Assistenten die Aktionen, die ausgeführt werden, und klicken Sie dann auf **Hochladen**, um den Assistenten abzuschließen.

Das hochgeladene Update wird in Ihrem Intune-Cloudspeicher gespeichert. Wenn nicht mehr ausreichend freier Speicherplatz zur Verfügung steht, um das Updatepaket hochzuladen, werden Sie während des Uploadprozesses darauf hingewiesen. Intune kann erst nach dem Start des Hochladens des Updates ermitteln, ob genügend Speicherplatz vorhanden ist, da für komprimierte Setup- und Installationsdateien mehr Speicherplatz benötigt wird, sobald sie entpackt sind.

Nach dem Hochladen in Intune wird ein Drittanbieterupdate im Fensterbereich **Alle Updates** des Arbeitsbereichs **Updates** angezeigt. Sie können das Update dann genehmigen und bereitstellen. Weitere Informationen finden Sie im folgenden Abschnitt „Genehmigen und Ablehnen von Updates“.

## <a name="approve-and-decline-updates"></a>Genehmigen und Ablehnen von Updates
Wenn Updates zur Installation bereit sind, wird auf der Seite **Updateübersicht** des Arbeitsbereichs **Updates** unter **Updatestatus**eine Meldung angezeigt. Klicken Sie auf diese Meldung, um die Seite **Alle Updates** zu öffnen und die Updates anzuzeigen, die zur Genehmigung bereit sind.

Mithilfe der Liste **Filter** können Sie das Suchen nach Updates erleichtern. Beispielsweise können Sie nur fehlgeschlagene oder aber nur solche Updates auflisten, die abgelöst werden.

Wenn Sie ein Update aus der Liste auswählen, werden weitere Befehle verfügbar, mit denen Sie Updates verwalten können. Diese sind in der folgenden Tabelle aufgeführt:

|Aufgabe|Details|
|--------|--------------------|
|**Eigenschaften anzeigen**|Hiermit werden ausführliche Informationen zum Update einschließlich der Anzahl der Computer angezeigt, auf die dieses Update angewendet werden kann.|
|**Bearbeiten**|Nur für nicht von Microsoft stammende Updates. Hiermit können Sie die Eigenschaften des Updates bearbeiten.|
|**Genehmigen**|Hiermit wird das ausgewählte Update genehmigt und Ihnen ermöglicht, die Gruppen zu konfigurieren, in denen es bereitgestellt wird. Weitere Informationen finden Sie im Verfahren **So genehmigen Sie Updates** in diesem Thema.|
|**Ablehnen**|Hiermit werden alle früheren Genehmigungen für das Update zurückgezogen, und das Update wird in den Standardansichten ausgeblendet. Darüber hinaus werden alle Berichtsdaten für das Update entfernt.<br /><br />Wenn Sie zu einem späteren Zeitpunkt nach einem abgelehnten Updates suchen möchten, legen Sie für den Filter auf der Seite **Alle Updates** die Einstellung **Abgelehnt**fest. Sie können das Update dann erforderlichenfalls genehmigen.<br /><br />Wenn ein Update abgelehnt wurde, weil es in Microsoft Update abgelaufen war, kann dieses Update in der Intune-Verwaltungskonsole nicht genehmigt werden.<br /><br />Wenn Sie eine Richtlinie für Updates löschen, die auf Computern bereitgestellt wurde, werden die Werte dieser Updateeinstellungen auf den Standardstatus für das installierte Betriebssystem zurückgesetzt.|
|**Löschen**|Nur für nicht von Microsoft stammende Updates. Hiermit wird das ausgewählte Update gelöscht.|
|**Hochladen**|Hiermit wird der **Assistent zum Hochladen von Updates** gestartet, mit dem Sie bereitzustellende Nicht-Microsoft-Updates hochladen können.|

### <a name="to-approve-updates"></a>So genehmigen Sie Updates

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) **Updates** &gt; **Übersicht** &gt; **Neue zu genehmigende Updates** aus.

    Wählen Sie im Arbeitsbereich **Updates** **Übersicht** &gt; **Neue zu genehmigende Updates** aus.

    > [!NOTE]
    > Der Link **Neue zu genehmigende Updates** wird nur dann im Bereich **Updatestatus** angezeigt, wenn mindestens ein verwalteter Computer vorhanden ist, für den ein Update genehmigt werden muss.

2.  Wählen Sie ein Update aus, überprüfen Sie unten auf der Seite die Updateeigenschaften, um sich zu vergewissern, dass Sie das Update genehmigen möchten, und klicken Sie dann auf **Genehmigen**. Sie können bei gedrückter **STRG**-Taste auch mehrere Updates auswählen.

3.  Wählen Sie auf der Seite **Gruppen auswählen** eine Gruppe aus, für die Sie die Updates bereitstellen möchten, und klicken Sie auf **Hinzufügen**. Wenn Sie alle Gruppen angegeben haben, wählen Sie **Weiter** aus.

4.  Führen Sie auf der Seite **Bereitstellungsaktion** folgende Schritte für jede Gruppe in der Liste aus:

    -   Wählen Sie in der Liste **Genehmigung** eine der folgenden Optionen aus:

        -   **Erforderliche Installation**: Das Update wird auf Computern in der angegebenen Gruppe installiert.

        -   **Nicht installieren**: Hiermit wird nur gemeldet, dass das Update anwendbar ist, ohne dass es installiert wird.

        -   **Verfügbare Installation:** Der Benutzer kann die Anwendung bei Bedarf über das Unternehmensportal installieren.

        -   **Deinstallieren**: Hiermit werden Updates von Computern in der Zielgruppe entfernt.

            > [!IMPORTANT]
            > Das Update wird auch dann entfernt, wenn es nicht von Intune installiert wurde.

    -   Wählen Sie in der Liste **Stichtag** eine der folgenden Optionen aus:

        -   **Keine**: Es wird kein Stichtag für die Installation des Updates erzwungen, und die Benutzer können das Update immer wieder ablehnen.

        -   **So bald wie möglich**: Das Update wird bei nächster Gelegenheit auf allen Zielcomputern installiert.

        -   **Benutzerdefiniert**: Hiermit wird der Zeitpunkt (Datum und Uhrzeit) festgelegt, zu dem genehmigte Updates installiert werden.

        -   **Eine Woche**, **Zwei Wochen**, **Ein Monat** : Hiermit wird das Update innerhalb des angegebenen Zeitraums installiert.

5.  Klicken Sie auf **Fertig stellen**, um die Einstellungen zu speichern, oder auf **Abbrechen**, um die Einstellungen zu verwerfen und zur Updateliste zurückzukehren.

    > [!IMPORTANT]
    > Wenn die Aktion **Nicht installieren**, **Erforderliche Installation**oder **Deinstallieren** nicht explizit für eine untergeordnete Gruppe konfiguriert wurde, wird eine Aktion, die für eine übergeordnete Gruppe konfiguriert wurde, von allen dieser Gruppe untergeordneten Gruppen geerbt.

6.  Sie können unten auf der Seite **Alle Updates** im Detailbereich überprüfen, ob Erinnerungsmeldungen zu dem Update vorhanden sind.


### <a name="see-also"></a>Siehe auch
[Richtlinien zum Schutz von Windows-PCs](policies-to-protect-windows-pcs-in-microsoft-intune.md)
