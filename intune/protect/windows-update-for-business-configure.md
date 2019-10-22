---
title: Konfigurieren von Windows Update for Business in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Aktualisieren der Softwareupdateeinstellungen in einem Profil zum Erstellen eines Updaterings, Überprüfen der Konformität und Pausieren von Updates in den Einstellungen von Windows Update for Business auf Windows 10-Geräten mithilfe von Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa8cc396c05150006799c1e9b86ecb63351cdb36
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314715"
---
# <a name="manage-software-updates-in-intune"></a>Verwalten von Softwareupdates in Intune

Verwenden Sie Intune, um Updateringe zu definieren, die festlegen, wann und wie Windows Ihre Windows 10-Geräte aktualisiert. Bei Updateringen handelt es sich um Richtlinien, die Sie Gerätegruppen zuweisen. Mithilfe von Updateringen können Sie eine auf Ihre Unternehmensanforderungen ausgerichtete Updatestrategie erstellen. Weitere Informationen finden Sie unter [Verwalten von Updates mit Windows Update for Business](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

Ab Windows 10 enthalten neue Feature- und Qualitätsupdates die Inhalte aller früheren Updates. Sie können sich also sicher sein, dass Ihre Windows 10-Geräte auf dem neuesten Stand sind, wenn Sie das neueste Update installiert haben. Im Gegensatz zu früheren Versionen von Windows müssen Sie nun anstelle eines Teilupdates das gesamte Update installieren.


Vereinfachen Sie die Updateverwaltung mithilfe von Windows Update for Business. Sie müssen einzelne Updates für Gerätegruppen nicht genehmigen. Sie können das Risiko in Ihren Umgebungen verwalten, indem Sie eine Updaterolloutstrategie konfigurieren. Mit Intune können Sie [Updateeinstellungen auf Geräten konfigurieren](../windows-update-settings.md) und die Installation von Updates zurückstellen. Intune speichert nur die Updaterichtlinienzuweisung, nicht die Updates. Geräte greifen für Updates direkt auf Windows Update zu. Diese Einstellungen, über die konfiguriert wird, wann Windows 10-Updates installiert werden, werden als *Windows 10-Updatering* bezeichnet.

In Windows 10-Updateringen werden [Bereichstags](../fundamentals/scope-tags.md) unterstützt. Sie können Bereichstags für Updateringe verwenden, um das Filtern und Verwalten der verwendeten Konfigurationen zu erleichtern.

## <a name="prerequisites"></a>Voraussetzungen  

Die folgenden Voraussetzungen müssen erfüllt sein, um Windows-Updates für Windows 10-Geräte in Intune zu verwenden.  

- Auf Windows 10-Computern muss mindestens Windows 10 Pro mit dem Windows Anniversary Update oder höher ausgeführt werden (Version 1607 oder höher)
- Windows Update unterstützt folgende Windows 10-Editionen:
  - Windows 10
  - Windows 10 Team (für Surface Hub-Geräte)
  - Windows Holographic for Business  

    Windows Holographic for Business unterstützt unter anderem folgende Einstellungen für Windows-Updates:
    - **Automatisches Updateverhalten**
    - **Microsoft-Produktupdates**
    - **Wartungskanal**: Unterstützt die Optionen **Halbjährlicher Kanal** und **Halbjährlicher Kanal (gezielt)** . Weitere Informationen finden Sie unter [Verwalten von Windows Holographic-Geräten](../fundamentals/windows-holographic-for-business.md).  

    > [!NOTE]  
    > **Nicht unterstützte Versionen und Editionen**:
    > - Windows 10 Mobile  
    > - Windows 10 Enterprise LTSC: Windows Update for Business (WUfB) unterstützt derzeit keine Releases von *Long-Term Servicing Channel*. Planen Sie, alternative Patchmethoden wie WSUS oder Configuration Manager zu verwenden.  

- Auf Windows-Geräten muss **Feedback und Diagnose** > **Diagnose- und Nutzungsdaten** auf **Standard**, **Erweitert** oder **Vollständig** festgelegt sein.  

  Sie können die Einstellung *Diagnose- und Nutzungsdaten* für Windows 10-Geräte entweder manuell konfigurieren oder ein Intune-Geräteeinschränkungsprofil für Windows 10 und höher verwenden. Wenn Sie ein Geräteeinschränkungsprofil verwenden, stellen Sie die Funktion [Geräteeinschränkung](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry) bei **Nutzungsdaten freigeben** auf mindestens **Standard** ein. Diese Einstellung befindet sich in der Kategorie **Berichterstellung und Telemetrie**, wenn Sie eine Richtlinie für Geräteeinschränkungen für Windows 10 oder höher konfigurieren.

  Weitere Informationen zu Geräteprofilen finden Sie unter [Konfigurieren von Einstellungen für Geräteeinschränkungen](../configuration/device-restrictions-configure.md).  

- Wenn Sie das klassische Azure-Portal verwenden, können Sie [Ihre Einstellungen in das Azure-Portal migrieren](#migrate-update-settings-to-the-azure-portal).  


## <a name="create-and-assign-update-rings"></a>Erstellen und Zuweisen von Updateringen

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie **Softwareupdates** > **Windows 10-Updateringe** > **Erstellen** aus.
4. Geben Sie einen Namen und (optional) eine Beschreibung ein, und klicken Sie dann auf **Konfigurieren**.
5. Passen Sie die Einstellungen unter **Einstellungen** an Ihre Geschäftsanforderungen an. Weitere Informationen über die verfügbaren Einstellungen finden Sie unter [Windows-Updateeinstellungen für Intune](../windows-update-settings.md).  
6. Klicken Sie auf **OK**, wenn Sie fertig sind. Klicken Sie unter **Updatering erstellen** auf **Erstellen**. Der neue Updatering wird in der Liste mit den Updateringen angezeigt.
7. Wählen Sie in der Liste mit den Updateringen einen Ring aus, und klicken Sie auf der Registerkarte mit dem \<Namen des Rings> auf **Zuweisungen**, um den Ring zuzuweisen.
8. Verwenden Sie die Registerkarten **Einschließen** und **Ausschließen**, um festzulegen, welcher Gruppe der Ring zugewiesen wird. Klicken Sie dann auf **Speichern**, um die Zuweisung abzuschließen.

## <a name="manage-your-windows-10-update-rings"></a>Verwalten Ihrer Windows 10-Updateringe
Sie können im Portal auf einen Windows 10-Updatering klicken, um dessen **Übersicht** zu öffnen. In diesem Bereich wird der Zuweisungsstatus der Ringe angezeigt, und Sie können weitere Aktionen durchführen, um den Ring zu verwalten. 
### <a name="to-view-an-updates-rings-overview-pane"></a>So rufen Sie die Übersicht eines Updaterings auf: 
1. Melden Sie sich im Azure-Portal an.
2. Navigieren Sie zu **Intune** > **Softwareupdates** > **Windows 10-Updateringe**.
3. Klicken Sie auf den Updatering, den Sie anzeigen oder verwalten möchten.  

Dort wird nicht nur der Zuweisungsstatus angezeigt, sondern Sie können folgende Verwaltungsaktionen im oberen Bereich der Übersicht auswählen:  
- [Löschen](#delete)  
- [Anhalten](#pause)  
- [Fortsetzen](#resume)  
- [Erweitern](#extend)  
- [Deinstallieren](#uninstall)  

![Verfügbare Aktionen](./media/windows-update-for-business-configure/overview-actions.png)

### <a name="delete"></a>Löschen  
Klicken Sie auf **Löschen**, um die Einstellungen des ausgewählten Windows 10-Updaterings aufzuheben. Durch das Löschen eines Rings wird die Konfiguration aus Intune entfernt, sodass Intune diese Einstellungen nicht mehr anwendet und erzwingt.  

Wenn Sie einen Ring aus Intune löschen, werden dadurch nicht die Einstellungen auf Geräten geändert, denen der Updatering zugewiesen wurde.  Diese Geräte behalten ihre aktuellen Einstellungen bei. Geräte behalten keine Verlaufsaufzeichnung der zuvor gespeicherten Einstellungen bei. Geräte können auch Einstellungen von zusätzlichen Updateringen empfangen, die aktiv bleiben.  

#### <a name="to-delete-a-ring"></a>So löschen Sie einen Ring  
1. Klicken Sie auf der Übersichtsseite eines Updaterings auf **Löschen**.  
2. Wählen Sie **OK** aus.  

### <a name="pause"></a>Anhalten  
Wählen Sie **Anhalten** aus, damit zugewiesene Geräte für einen Zeitraum von bis zu 35 Tagen (ab dem Zeitpunkt, zu dem der Ring ausgesetzt wurde) keine Feature- oder Qualitätsupdates mehr empfangen. Nach Verstreichen der maximalen Anzahl von Tagen wird die Aussetzung automatisch aufgehoben, und das Gerät sucht bei Windows Update nach geeigneten Updates. Danach können Sie die Updates erneut aussetzen. Wenn Sie einen angehaltenen Updatering fortsetzen und anschließend erneut anhalten, wird die Anhaltedauer auf 35 Tage zurückgesetzt.  

#### <a name="to-pause-a-ring"></a>So halten Sie einen Ring an  
1. Klicken Sie auf der Übersichtsseite eines Updaterings auf **Anhalten**.  
2. Wählen Sie **Feature** oder **Qualität** aus, um diesen Updatetyp anzuhalten, und klicken Sie dann auf **OK**.  
3. Wenn Sie einen Updatetyp angehalten haben, können Sie den anderen Updatetyp anhalten, indem Sie erneut auf „Anhalten“ klicken.  

Wenn ein Updatetyp angehalten wird, zeigt die Übersicht für diesen Ring an, wie viele Tage verbleiben, bis der Updatetyp fortgesetzt wird.

> [!IMPORTANT]  
> Wenn Sie den Befehl zum Anhalten ausführen, geht dieser bei den Geräten ein, wenn sie das nächste Mal mit dem Dienst kommunizieren. Es kann vorkommen, dass die Geräte vor der Kommunikation ein geplantes Update installieren. Außerdem gilt: Wenn ein Zielgerät bei Erteilung des Aussetzungsbefehls ausgeschaltet ist, lädt es nach dem Einschalten unter Umständen geplante Updates herunter und installiert sie, bevor es mit Intune kommuniziert.

### <a name="resume"></a>Fortsetzen  
Während ein Updatering angehalten ist, können Sie auf **Fortsetzen** klicken, um Feature- und Qualitätsupdates für diesen Ring wieder zu aktivieren. Sie können einen Updatering nach dem Aktivieren erneut anhalten.  

#### <a name="to-resume-a-ring"></a>So setzen Sie einen Ring fort  
1. Klicken Sie auf der Übersichtsseite eines angehaltenen Updaterings auf **Fortsetzen**.  
2. Wählen Sie aus den fortsetzbaren Updatetypen entweder **Feature** oder **Qualität** aus, und klicken Sie auf **OK**.  
3. Wenn Sie einen Updatetyp fortgesetzt haben, können Sie den anderen Updatetyp fortsetzen, indem Sie erneut auf „Fortsetzen“ klicken.  

### <a name="extend"></a>Extend  
Während ein Updatering angehalten ist, können Sie auf **Erweitern** klicken, um die Anhaltedauer für Feature- und Qualitätsupdates für diesen Updatering auf 35 Tage zurückzusetzen.  

#### <a name="to-extend-the-pause-period-for-a-ring"></a>So erweitern Sie die Anhaltedauer für einen Ring  
1. Klicken Sie auf der Übersichtsseite eines angehaltenen Updaterings auf **Erweitern**. 
2. Wählen Sie aus den fortsetzbaren Updatetypen entweder **Feature** oder **Qualität** aus, und klicken Sie auf **OK**.  
3. Nachdem Sie die Anhaltedauer für einen Updatetyp erweitert haben, können Sie erneut auf „Erweitern“ klicken, um auch die Dauer für den anderen Updatetyp zu erweitern.  

### <a name="uninstall"></a>Deinstallieren  
Ein Intune-Administrator kann das neuste *Feature-* oder *Qualitätsupdate* eines aktiven oder angehaltenen Updaterings über die Option **Deinstallieren** deinstallieren bzw. ein Rollback ausführen. Nachdem Sie einen Updatetyp deinstalliert haben, können Sie auch den anderen deinstallieren. Benutzer haben in Intune nicht die Möglichkeit, Updates zu deinstallieren.  

> [!IMPORTANT] 
> Wenn Sie die Option *Deinstallieren* verwenden, übergibt Intune die Deinstallationsanforderung sofort an Geräte. 
> - Windows-Geräte starten das Entfernen von Updates, sobald sie die Änderung der Intune-Richtlinie erhalten. Das Entfernen von Updates ist nicht auf Wartungszeitpläne beschränkt, auch wenn diese als Teil des Updaterings konfiguriert sind. 
> - Wenn beim Entfernen des Updates ein Geräteneustart erforderlich ist, wird das Gerät neu gestartet, ohne dass Gerätebenutzern eine Option zur Verzögerung angeboten wird.


Diese Voraussetzungen sind für eine erfolgreiche Deinstallation erforderlich:  
- Auf dem Gerät muss das Windows 10 April 2018-Update (Version 1803) oder höher ausgeführt werden.  

Auf dem Gerät muss das aktuelle Update installiert sein. Da Updates kumulativ sind, werden auf Geräten, auf denen das neueste Update installiert wird, auch die neuesten Feature- und Qualitätsupdates installiert. Sie können diese Option beispielsweise verwenden, um ein Rollback auf das letzte Update durchzuführen, falls auf Ihren Windows 10-Computern schwerwiegende Probleme auftreten.  

Beachten Sie bei der Deinstallation Folgendes:  
- Die Deinstallation eines Feature- oder Qualitätsupdates ist für den Wartungskanal nur möglich, wenn das Gerät eingeschaltet ist.  

- Durch die Deinstallation von Feature- oder Qualitätsupdates wird eine Richtlinie ausgelöst, die das vorherige Update auf Ihren Windows 10-Computern wiederherstellt.  

- Nachdem ein erfolgreiches Rollback für ein Qualitätsupdate auf Windows 10-Computern ausgeführt wurde, wird das Update weiterhin für Endbenutzer sichtbar unter **Windows-Einstellungen** > **Updates** > **Updateverlauf** aufgeführt.  

- Für Featureupdates ist der Zeitraum für die Deinstallation auf 2 bis 60 Tage beschränkt. Dieser wird über die Einstellungen für den Updatering unter **Set feature update uninstall period (2 – 60 days)** (Deinstallationszeitraum für Featureupdates festlegen (2–60 Tage)) festgelegt. Sie können kein Rollback für ein Featureupdate ausführen, das länger als der konfigurierte Deinstallationszeitraum auf dem Gerät installiert ist.  

  Stellen Sie sich beispielsweise einen Updatering mit einer Deinstallationsfrist von 20 Tagen vor. Nach 25 Tagen beschließen Sie, ein Rollback des letzten Featureupdates durchzuführen und die Option „Deinstallieren“ zu verwenden.  Geräte, die das Featureupdate vor mehr als 20 Tagen installiert haben, können es nicht deinstallieren, da die erforderlichen Bits im Rahmen ihrer Wartung entfernt wurden. Geräte, die das Featureupdate erst vor 19 Tagen installiert haben, können das Update jedoch deinstallieren, wenn sie sich erfolgreich einchecken, um den Deinstallationsbefehl zu erhalten, bevor sie die 20-tägige Deinstallationsfrist überschreiten.  

Weitere Informationen zu den Windows Update-Richtlinien finden Sie unter [Update CSP (Update-Konfigurationsdienstanbieter)](https://docs.microsoft.com/windows/client-management/mdm/update-csp) in der Dokumentation zur Verwaltung von Windows-Clients.  

#### <a name="to-uninstall-the-latest-windows-10-update"></a>So deinstallieren Sie das aktuelle Windows 10-Update  
1. Klicken Sie auf der Übersichtsseite eines angehaltenen Updaterings auf **Deinstallieren**.  
2. Wählen Sie aus den deinstallierbaren Updatetypen entweder **Feature** oder **Qualität** aus, und klicken Sie auf **OK**.  
3. Nachdem Sie die Deinstallation für einen Updatetyp gestartet haben, können Sie erneut auf „Deinstallieren“ klicken, um auch den anderen Updatetyp zu deinstallieren.  

## <a name="migrate-update-settings-to-the-azure-portal"></a>Migrieren von Updateeinstellungen in das Azure-Portal  
Im klassischen Azure-Portal steht auch eine begrenzte Anzahl anderer Windows 10-Updateeinstellungen im Gerätekonfigurationsprofil zur Verfügung. Falls Sie eine dieser Einstellungen konfiguriert haben und zum Azure-Portal migrieren möchten, sollten Sie unbedingt die folgenden Aktionen ausführen:  

1. Erstellen Sie im Azure-Portal Windows 10-Updateringe mit den erforderlichen Einstellungen. Die Einstellung **Vorabfeatures zulassen** wird im Azure-Portal nicht unterstützt, da sie für die neuesten Windows 10-Builds nicht mehr relevant ist. Die drei anderen Einstellungen können zusammen mit anderen Windows 10-Updateeinstellungen beim Erstellen von Updateringen konfiguriert werden.  

   > [!NOTE]  
   > Im klassischen Portal erstellte Windows 10-Updateeinstellungen werden nach der Migration nicht im Azure-Portal angezeigt. Allerdings werden diese Einstellungen angewendet. Wenn Sie diese Einstellungen migrieren und die migrierte Richtlinie über das Azure-Portal bearbeiten, werden die Einstellungen aus der Richtlinie entfernt.  

2. Löschen Sie die Updateeinstellungen im klassischen Portal. Wenn Sie zum Azure-Portal migriert sind und die gleichen Einstellungen einem Updatering hinzufügen, müssen Sie die Einstellungen im klassischen Portal löschen, um potenzielle Richtlinienkonflikte zu vermeiden. Zum Beispiel kommt es zu einem Konflikt, wenn die gleiche Einstellung mit verschiedenen Werten konfiguriert wird. Dies ist nicht einfach zu ermitteln, da die im klassischen Portal konfigurierte Einstellung nicht im Azure-Portal angezeigt wird.  

## <a name="next-steps"></a>Nächste Schritte
[Windows-Updateeinstellungen für Intune](../windows-update-settings.md)  

[Berichte zur Updatekonformität für Intune](../windows-update-compliance-reports.md)

[Problembehandlung bei Windows 10-Updateringen](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)

