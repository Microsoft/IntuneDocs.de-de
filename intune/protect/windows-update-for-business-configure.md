---
title: Konfigurieren von Windows Update for Business in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwalten Sie Windows 10-Softwareupdates mithilfe von Updateringen und Richtlinien für Featureupdates. Sie können die Konformität überprüfen und die Updateinstallation mit Einstellungen für Windows Update for Business mithilfe von Microsoft Intune anhalten.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 01866bba0ef47ac807b24a66f773e212c76ff7df
ms.sourcegitcommit: 1cf063c98e1caae00a6e6fab821cc3254562bca9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291097"
---
# <a name="manage-windows-10-software-updates-in-intune"></a>Verwalten von Windows 10-Softwareupdates in Intune

Verwenden Sie Intune, um die Installation von Windows 10-Softwareupdates für Windows Update for Business zu verwalten.

Vereinfachen Sie die Updateverwaltung mithilfe von Windows Update for Business. Sie müssen einzelne Updates für Gerätegruppen nicht genehmigen. Sie können das Risiko in Ihren Umgebungen verwalten, indem Sie eine Updaterolloutstrategie konfigurieren. Mit Intune können Sie [Updateeinstellungen auf Geräten konfigurieren](windows-update-settings.md) und die Installation von Updates zurückstellen. Sie können auch verhindern, dass Geräte Funktionen von neuen Windows-Versionen installieren, um diese stabil zu halten, und gleichzeitig zulassen, dass diese Geräte weiterhin Qualitäts- und Sicherheitsupdates installieren.

In Intune werden nur die Updaterichtlinienzuweisungen und nicht die Updates selbst gespeichert. Geräte greifen für Updates direkt auf Windows Update zu.

Intune stellt die folgenden Richtlinientypen zum Verwalten von Updates bereit:

- **Windows 10-Updatering**: Bei dieser Richtlinie handelt es sich um eine Sammlung von Einstellungen, über die konfiguriert wird, wenn Windows 10-Updates installiert werden.

- **Windows 10-Featureupdates (öffentliche Vorschau)** : Diese Richtlinie aktualisiert die Geräte auf die von Ihnen angegebene Windows-Version und friert die Funktionsgruppe auf diesen Geräten ein, bis Sie sie auf eine höhere Windows-Version aktualisieren.  Während die Funktionsversion statisch bleibt, können Geräte weiterhin Qualitäts- und Sicherheitsupdates installieren, die für ihre Funktionsversion verfügbar sind.

Weisen Sie Gerätegruppen Richtlinien für Windows 10-Updateringe und Windows 10-Featureupdates zu. Sie können beide Richtlinientypen in der gleichen Intune-Umgebung verwenden, um Softwareupdates für Ihre Windows 10-Geräte zu verwalten und eine auf Ihre Geschäftsanforderungen ausgerichtete Updatestrategie zu erstellen.

Weitere Informationen finden Sie unter [Verwalten von Updates mit Windows Update for Business](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="prerequisites"></a>Voraussetzungen

Die folgenden Voraussetzungen müssen erfüllt sein, um Windows-Updates für Windows 10-Geräte in Intune zu verwenden.

- Auf Windows 10-PCs müssen die folgenden Windows 10-Versionen ausgeführt werden:
  - **Windows 10-Updateringe**: Version 1607 oder höher
  - **Windows 10-Featureupdates**: Version 1703 oder höher

- Windows Update unterstützt folgende Windows 10-Editionen:
  - Windows 10
  - Windows 10 Team: für Surface Hub-Geräte (*Windows 10-Featureupdates* werden nicht unterstützt)
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


## <a name="windows-10-update-rings"></a>Windows 10-Updateringe

Erstellen Sie Updateringe, die festlegen, wann und wie Windows Ihre Windows 10-Geräte mit Feature- und Qualitätsupdates aktualisiert. Ab Windows 10 enthalten neue Feature- und Qualitätsupdates die Inhalte aller früheren Updates. Sie können sich also sicher sein, dass Ihre Windows 10-Geräte auf dem neuesten Stand sind, wenn Sie das neueste Update installiert haben. Im Gegensatz zu früheren Versionen von Windows müssen Sie nun anstelle eines Teilupdates das gesamte Update installieren.

In Windows 10-Updateringen werden [Bereichstags](../fundamentals/scope-tags.md) unterstützt. Sie können Bereichstags für Updateringe verwenden, um das Filtern und Verwalten der verwendeten Konfigurationen zu erleichtern.

### <a name="create-and-assign-update-rings"></a>Erstellen und Zuweisen von Updateringen

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center]( https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Windows** > **Windows 10-Updateringe** > **Erstellen** aus.

3. Geben Sie unter *Grundeinstellungen* einen Namen und eine Beschreibung (optional) an, und klicken Sie dann auf **Weiter**.
  ![Erstellen eines Updaterings]( ./media/windows-update-for-business-configure/basics-tab.png)
  
4. Konfigurieren Sie die Einstellungen unter **Einstellungen für Updatering** gemäß Ihrer Geschäftsanforderungen. Weitere Informationen über die verfügbaren Einstellungen finden Sie unter den Windows-Updateeinstellungen. Klicken Sie auf **Weiter**, nachdem Sie die Einstellungen für *Update und Benutzeroberfläche* konfiguriert haben.

5. Klicken Sie unter **Bereichstags** auf **Bereichstags auswählen**, um den Bereich *Tags auswählen* zu öffnen, wenn Sie sie auf den Updatering anwenden möchten. Wählen Sie mindestens einen Tag aus, und klicken Sie dann auf **Auswählen**, um sie zum Updatering hinzuzufügen und zum Bereich *Bereichstags* zurückzukehren.

   Klicken Sie auf **Weiter**, um mit *Zuweisungen* fortzufahren, wenn Sie bereit sind.

6. Klicken Sie unter **Zuweisungen** auf **Wählen Sie die Gruppen aus, die eingeschlossen werden sollen.** , und weisen Sie dann den Updatering mindestens einer Gruppe zu. Klicken Sie auf **+ Auszuschließende Gruppen auswählen**, um die Zuweisung anzupassen. Wählen Sie **Weiter** aus, um den Vorgang fortzusetzen.

7. Überprüfen Sie die Einstellungen unter **Überprüfen + erstellen**, und klicken Sie dann auf **Erstellen**, um Ihren Windows 10-Updatering zu speichern. Ihr neuer Updatering wird in der Liste mit den Updateringen angezeigt.

### <a name="manage-your-windows-10-update-rings"></a>Verwalten Ihrer Windows 10-Updateringe

Navigieren Sie im Portal zu **Geräte** > **Windows** > **Windows 10-Updatering**, und wählen Sie die Richtlinie aus, die Sie verwalten möchten.  Die Richtlinie wird auf der Seite **Übersicht** geöffnet.

In diesem Bereich wird der Zuweisungsstatus der Ringe angezeigt, und Sie können folgende Verwaltungsaktionen im oberen Bereich der Übersicht auswählen:

- [Löschen](#delete)
- [Anhalten](#pause)
- [Fortsetzen](#resume)
- [Erweitern](#extend)
- [Deinstallieren](#uninstall)

![Verfügbare Aktionen](./media/windows-update-for-business-configure/overview-actions.png)

#### <a name="delete"></a>Löschen

Klicken Sie auf **Löschen**, um die Einstellungen des ausgewählten Windows 10-Updaterings aufzuheben. Durch das Löschen eines Rings wird die Konfiguration aus Intune entfernt, sodass Intune diese Einstellungen nicht mehr anwendet und erzwingt.

Wenn Sie einen Ring aus Intune löschen, werden dadurch nicht die Einstellungen auf Geräten geändert, denen der Updatering zugewiesen wurde.  Diese Geräte behalten ihre aktuellen Einstellungen bei. Geräte behalten keine Verlaufsaufzeichnung der zuvor gespeicherten Einstellungen bei. Geräte können auch Einstellungen von zusätzlichen Updateringen empfangen, die aktiv bleiben.

##### <a name="to-delete-a-ring"></a>So löschen Sie einen Ring

1. Klicken Sie auf der Übersichtsseite eines Updaterings auf **Löschen**.
2. Wählen Sie **OK** aus.

#### <a name="pause"></a>Anhalten

Wählen Sie **Anhalten** aus, damit zugewiesene Geräte für einen Zeitraum von bis zu 35 Tagen (ab dem Zeitpunkt, zu dem der Ring ausgesetzt wurde) keine Feature- oder Qualitätsupdates mehr empfangen. Nach Verstreichen der maximalen Anzahl von Tagen wird die Aussetzung automatisch aufgehoben, und das Gerät sucht bei Windows Update nach geeigneten Updates. Danach können Sie die Updates erneut aussetzen.
Wenn Sie einen angehaltenen Updatering fortsetzen und anschließend erneut anhalten, wird die Anhaltedauer auf 35 Tage zurückgesetzt.

##### <a name="to-pause-a-ring"></a>So halten Sie einen Ring an

1. Klicken Sie auf der Übersichtsseite eines Updaterings auf **Anhalten**.
2. Wählen Sie **Feature** oder **Qualität** aus, um diesen Updatetyp anzuhalten, und klicken Sie dann auf **OK**.
3. Wenn Sie einen Updatetyp angehalten haben, können Sie den anderen Updatetyp anhalten, indem Sie erneut auf „Anhalten“ klicken.

Wenn ein Updatetyp angehalten wird, zeigt die Übersicht für diesen Ring an, wie viele Tage verbleiben, bis der Updatetyp fortgesetzt wird.

> [!IMPORTANT]
> Wenn Sie den Befehl zum Anhalten ausführen, geht dieser bei den Geräten ein, wenn sie das nächste Mal mit dem Dienst kommunizieren. Es kann vorkommen, dass die Geräte vor der Kommunikation ein geplantes Update installieren. Außerdem gilt: Wenn ein Zielgerät bei Erteilung des Aussetzungsbefehls ausgeschaltet ist, lädt es nach dem Einschalten unter Umständen geplante Updates herunter und installiert sie, bevor es mit Intune kommuniziert.

#### <a name="resume"></a>Fortsetzen

Während ein Updatering angehalten ist, können Sie auf **Fortsetzen** klicken, um Feature- und Qualitätsupdates für diesen Ring wieder zu aktivieren. Sie können einen Updatering nach dem Aktivieren erneut anhalten.

##### <a name="to-resume-a-ring"></a>So setzen Sie einen Ring fort

1. Klicken Sie auf der Übersichtsseite eines angehaltenen Updaterings auf **Fortsetzen**.
2. Wählen Sie aus den fortsetzbaren Updatetypen entweder **Feature** oder **Qualität** aus, und klicken Sie auf **OK**.
3. Wenn Sie einen Updatetyp fortgesetzt haben, können Sie den anderen Updatetyp fortsetzen, indem Sie erneut auf „Fortsetzen“ klicken.

#### <a name="extend"></a>Extend  

Während ein Updatering angehalten ist, können Sie auf **Erweitern** klicken, um die Anhaltedauer für Feature- und Qualitätsupdates für diesen Updatering auf 35 Tage zurückzusetzen.

##### <a name="to-extend-the-pause-period-for-a-ring"></a>So erweitern Sie die Anhaltedauer für einen Ring

1. Klicken Sie auf der Übersichtsseite eines angehaltenen Updaterings auf **Erweitern**.
2. Wählen Sie aus den fortsetzbaren Updatetypen entweder **Feature** oder **Qualität** aus, und klicken Sie auf **OK**.
3. Nachdem Sie die Anhaltedauer für einen Updatetyp erweitert haben, können Sie erneut auf „Erweitern“ klicken, um auch die Dauer für den anderen Updatetyp zu erweitern.

#### <a name="uninstall"></a>Deinstallieren  

Ein Intune-Administrator kann das neuste *Feature-* oder *Qualitätsupdate* eines aktiven oder angehaltenen Updaterings über die Option **Deinstallieren** deinstallieren bzw. ein Rollback ausführen. Nachdem Sie einen Updatetyp deinstalliert haben, können Sie auch den anderen deinstallieren. Benutzer haben in Intune nicht die Möglichkeit, Updates zu deinstallieren.  

> [!IMPORTANT]
> Wenn Sie die Option *Deinstallieren* verwenden, übergibt Intune die Deinstallationsanforderung sofort an Geräte.
>
> - Windows-Geräte starten das Entfernen von Updates, sobald sie die Änderung der Intune-Richtlinie erhalten. Das Entfernen von Updates ist nicht auf Wartungszeitpläne beschränkt, auch wenn diese als Teil des Updaterings konfiguriert sind.
> - Wenn beim Entfernen des Updates ein Geräteneustart erforderlich ist, wird das Gerät neu gestartet, ohne dass Gerätebenutzern eine Option zur Verzögerung angeboten wird.

Diese Voraussetzungen sind für eine erfolgreiche Deinstallation erforderlich:

- Auf dem Gerät muss das Windows 10 April 2018-Update (Version 1803) oder höher ausgeführt werden.

Auf dem Gerät muss das aktuelle Update installiert sein. Da Updates kumulativ sind, werden auf Geräten, auf denen das neueste Update installiert wird, auch die neuesten Feature- und Qualitätsupdates installiert. Sie können diese Option beispielsweise verwenden, um ein Rollback auf das letzte Update durchzuführen, falls auf Ihren Windows 10-Computern schwerwiegende Probleme auftreten.

Beachten Sie bei der Deinstallation Folgendes:

- Die Deinstallation eines Feature- oder Qualitätsupdates ist für den Wartungskanal nur möglich, wenn das Gerät eingeschaltet ist.

- Durch die Deinstallation von Feature- oder Qualitätsupdates wird eine Richtlinie ausgelöst, die das vorherige Update auf Ihren Windows 10-Computern wiederherstellt.

- Nachdem ein erfolgreiches Rollback für ein Qualitätsupdate auf Windows 10-Computern ausgeführt wurde, wird das Update weiterhin für Gerätebenutzer sichtbar unter **Windows-Einstellungen** > **Updates** > **Updateverlauf** aufgeführt.

- Bei Featureupdates ist die Zeit, in der Sie das Update deinstallieren können, auf 2-60 Tage begrenzt. Dieser Zeitraum wird von der entsprechenden Einstellung für die Updateringe **Hiermit wird der Zeitraum für das Deinstallieren von Featureupdates festgelegt. (2 bis 60 Tage).** konfiguriert. Sie können kein Rollback für ein Featureupdate ausführen, das länger als der konfigurierte Deinstallationszeitraum auf dem Gerät installiert ist.

  Stellen Sie sich beispielsweise einen Updatering mit einer Deinstallationsfrist von 20 Tagen vor. Nach 25 Tagen beschließen Sie, ein Rollback des letzten Featureupdates durchzuführen und die Option „Deinstallieren“ zu verwenden.  Geräte, die das Featureupdate vor mehr als 20 Tagen installiert haben, können es nicht deinstallieren, da sie die erforderlichen Bits im Rahmen ihrer Wartung entfernt haben. Auf Geräten, auf denen das Featureupdate erst vor 19 Tagen installiert wurde, kann das Update jedoch deinstalliert werden, wenn sie erfolgreich eingecheckt werden, um den Deinstallationsbefehl zu erhalten, bevor die 20-tägige Deinstallationsfrist abläuft.

Weitere Informationen zu den Windows Update-Richtlinien finden Sie unter [Update CSP (Update-Konfigurationsdienstanbieter)](https://docs.microsoft.com/windows/client-management/mdm/update-csp) in der Dokumentation zur Verwaltung von Windows-Clients.

##### <a name="to-uninstall-the-latest-windows-10-update"></a>So deinstallieren Sie das aktuelle Windows 10-Update

1. Klicken Sie auf der Übersichtsseite eines angehaltenen Updaterings auf **Deinstallieren**.
2. Wählen Sie aus den deinstallierbaren Updatetypen entweder **Feature** oder **Qualität** aus, und klicken Sie auf **OK**.
3. Nachdem Sie die Deinstallation für einen Updatetyp gestartet haben, können Sie erneut auf „Deinstallieren“ klicken, um auch den anderen Updatetyp zu deinstallieren.

## <a name="windows-10-feature-updates"></a>Windows 10-Featureupdates

*Diese Funktion befindet sich in einem öffentlichen Vorschauzustand.*

Mit *Windows 10-Featureupdates* wählen Sie die Windows-Funktionsversion aus, die die Geräte beibehalten sollen, z. B. Windows 10 Version 1803 oder 1809. Sie können eine Funktionsebene von 1803 oder höher festlegen.

Wenn ein Gerät eine Richtlinie für Windows 10-Featureupdates erhält, geschieht Folgendes:

- Das Gerät wird auf die Windows-Version aktualisiert, die in der Richtlinie angegeben ist. Ein Gerät, auf dem bereits eine höhere Version von Windows ausgeführt wird, bleibt in der aktuellen Version. Durch das Einfrieren der Version bleibt die Gerätefunktionsgruppe für die Dauer der Richtlinie stabil.

- Während die installierte Version von Windows weiterhin festgelegt ist, können Geräte weiterhin Qualitäts- und Sicherheitsupdates für ihre Windows-Version erhalten und installieren, solange diese Version unterstützt wird. Dadurch bleiben Ihre Geräte aktualisiert und sicher.

- Anders als bei der Verwendung der Funktion *Anhalten* mit einem Updatering, der nach 35 Tagen abläuft, bleibt die Richtlinie des Windows 10-Featureupdates weiterhin aktiv. Geräte installieren erst dann eine neue Windows-Version, wenn Sie die Richtlinie für Windows 10-Featureupdates ändern oder entfernen. Wenn Sie die Richtlinie bearbeiten, um eine neuere Version anzugeben, können Geräte die Features von dieser Windows-Version installieren.

### <a name="limitations-for-windows-10-feature-updates"></a>Einschränkungen für Windows 10-Featureupdates

- Wenn Sie eine *Windows 10-Featureupdate*-Richtlinie auf einem Gerät bereitstellen, das auch eine *Windows 10-Updatering*-Richtlinie empfängt, überprüfen Sie den Updatering für die folgenden Konfigurationen:
  - Der **Rückstellungszeitraum für Funktionsupdates (Tage)** muss auf **0** festgelegt werden.
  - Featureupdates für den Updatering müssen *ausgeführt werden*. Sie dürfen nicht angehalten werden.

- Die *Windows 10-Featureupdates*-Richtlinie wird nicht von Autopilot unterstützt. Intune wird die Richtlinie für folgende Geräte nicht bereitstellen:
  - Geräte, die von Autopilot bereitgestellt werden.
  - Geräte, die zuvor mit Autopilot bereitgestellt wurden.

  Diese Einschränkung wird untersucht, um festzustellen, ob sie in Zukunft unterstützt werden kann.


### <a name="create-and-assign-windows-10-feature-updates"></a>Erstellen und Zuweisen von Windows 10-Featureupdates

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Windows** > **Windows 10-Featureupdates** > **Erstellen** aus.

3. Geben Sie unter **Grundeinstellungen** einen Namen und eine Beschreibung (optional) an, und wählen Sie für **Bereitzustellendes Featureupdate** die Windows-Version mit der gewünschten Funktionsgruppe aus. Klicken Sie dann auf **Weiter**.

4. Klicken Sie unter **Zuweisungen** auf **Wählen Sie die Gruppen aus, die eingeschlossen werden sollen.** , und weisen Sie dann den Updatering mindestens einer Gruppe zu. Wählen Sie **Weiter** aus, um den Vorgang fortzusetzen.

5. Überprüfen Sie die Einstellungen unter **Überprüfen + erstellen**, und klicken Sie auf **Erstellen**, um die Richtlinie des Windows 10-Featureupdates zu speichern.  

### <a name="manage-windows-10-feature-updates"></a>Verwalten von Windows 10-Featureupdates

Wechseln Sie im Admin Center zu **Geräte** > **Windows** > **Windows 10-Featureupdates**, und wählen Sie die Richtlinie aus, die Sie verwalten möchten. Die Richtlinie wird auf der Seite **Übersicht** geöffnet.

In diesem Bereich können Sie folgende Aktionen ausführen:

- Wählen Sie **Löschen** aus, um die Richtlinie aus Intune zu löschen und sie von den Geräten zu entfernen.
- Wählen Sie **Eigenschaften** aus, um die Bereitstellung zu ändern.  Wählen Sie im Bereich *Eigenschaften* die Option **Bearbeiten** aus, um die *Bereitstellungseinstellungen und Zuweisungen* zu öffnen, wo Sie dann die Bereitstellung ändern können.
- Wählen Sie **Endbenutzer-Updatestatus** aus, um Informationen zur Richtlinie anzuzeigen.

## <a name="migrate-update-settings-to-the-azure-portal"></a>Migrieren von Updateeinstellungen in das Azure-Portal

Im klassischen Azure-Portal steht auch eine begrenzte Anzahl anderer Windows 10-Updateeinstellungen im Gerätekonfigurationsprofil zur Verfügung. Falls eine dieser Einstellungen konfiguriert ist, wenn Sie zum Azure-Portal migrieren, sollten Sie unbedingt die folgenden Aktionen ausführen:

1. Erstellen Sie im Azure-Portal Windows 10-Updateringe mit den erforderlichen Einstellungen. Die Einstellung **Vorabfeatures zulassen** wird im Azure-Portal nicht unterstützt, da sie für die neuesten Windows 10-Builds nicht mehr relevant ist. Sie können die anderen drei Einstellungen und die anderen Windows 10-Updateeinstellungen konfigurieren, wenn Sie Updateringe erstellen.

   > [!NOTE]
   > Im klassischen Portal erstellte Windows 10-Updateeinstellungen werden nach der Migration nicht im Azure-Portal angezeigt. Allerdings werden diese Einstellungen angewendet. Wenn Sie diese Einstellungen migrieren und die migrierte Richtlinie über das Azure-Portal bearbeiten, werden die Einstellungen aus der Richtlinie entfernt.

2. Löschen Sie die Updateeinstellungen im klassischen Portal. Wenn Sie zum Azure-Portal migriert sind und die gleichen Einstellungen einem Updatering hinzufügen, müssen Sie die Einstellungen im klassischen Portal löschen, um potenzielle Richtlinienkonflikte zu vermeiden. Zum Beispiel kommt es zu einem Konflikt, wenn die gleiche Einstellung mit verschiedenen Werten konfiguriert wird. Dies ist nicht einfach zu ermitteln, da die im klassischen Portal konfigurierte Einstellung nicht im Azure-Portal angezeigt wird.

## <a name="next-steps"></a>Nächste Schritte

[Windows-Updateeinstellungen für Intune](../windows-update-settings.md)

[Berichte zur Updatekonformität für Intune](../windows-update-compliance-reports.md)

[Problembehandlung bei Windows 10-Updateringen](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)

