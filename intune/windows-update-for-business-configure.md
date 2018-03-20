---
title: "Konfigurieren von Einstellungen für Windows Update for Business in Intune"
titleSuffix: Azure portal
description: "Erfahren Sie, wie Sie in Intune die Einstellungen von Windows Update for Business konfigurieren, um Updates für Windows 10-Geräte zu steuern."
keywords: 
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: coryfe
ms.suite: ems
ms.openlocfilehash: d6ccda2aba0b1383de6c38b7a2fdcfdc742d0e15
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="manage-software-updates"></a>Verwalten von Softwareupdates

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Windows 10-Geräte werden mit Windows-as-a-Service aktualisiert. Ab Windows 10 enthalten neue Funktions- und Qualitätsupdates die Inhalte aller früheren Updates. Das bedeutet, dass Ihre Windows 10-Geräte nach der Installation des neuesten Updates auf dem neuesten Stand sind. Im Gegensatz zu früheren Versionen von Windows müssen Sie nun anstelle eines Teilupdates das gesamte Update installieren.

Mithilfe von Windows Update for Business können Sie die Updateverwaltung vereinfachen, sodass Sie für Gruppen von Geräten keine einzelnen Updates genehmigen müssen. Sie können weiterhin eine Updaterolloutstrategie konfigurieren, um das Risiko in Ihren Umgebungen zu managen und sicherzustellen, dass Updates zur richtigen Zeit installiert werden. Mit Microsoft Intune können Sie Updateeinstellungen auf Geräten konfigurieren und die Updateinstallation zurückstellen. Intune speichert nur die Updaterichtlinienzuweisung, nicht die Updates. Geräte greifen für Updates direkt auf Windows Update zu. Verwenden Sie Intune, um **Windows 10-Updateringe** zu konfigurieren und zu verwalten. Ein Updatering enthält eine Reihe von Einstellungen, die festlegen, wann und wie Updates für Windows 10 installiert werden. So können Sie beispielsweise Folgendes konfigurieren:

- **Windows 10-Wartungskanal**: Wählen Sie aus, ob Gerätegruppen Updates über den halbjährlichen Kanal (gezielt) oder über den halbjährlichen Kanal erhalten sollen.  
- **Zurückstellungseinstellungen:** Konfigurieren Sie Einstellungen für die Zurückstellung von Updates, um Updateinstallationen für Gruppen von Geräten zu verzögern. Verwenden Sie diese Einstellungen, um ein gestaffeltes Updaterollout zu erhalten, dessen Fortschritt Sie verfolgen können.
- **Aussetzung:** Verschieben Sie die Installation von Updates, falls im Rahmen des Updaterollouts ein Problem auftreten sollte.
- **Wartungsfenster:** Konfigurieren Sie die Zeiten, in denen Updates installiert werden können.
- **Aktualisierungstyp:** Wählen Sie aus, welche Arten von Updates installiert werden. Beispiele wären etwa Qualitätsupdates, Funktionsupdates oder Treiber.
- **Installationsverhalten:** Konfiguriert, wie das Update installiert wird. Hier können Sie beispielsweise festlegen, ob das Gerät nach der Installation automatisch neu gestartet werden soll.
- **Peerdownloads:** Sie können angeben, ob Sie Peerdownloads konfigurieren möchten. Falls ja, können Geräte das Update von einem anderen Gerät herunterladen, das den Downloadvorgang bereits abgeschlossen hat. Dadurch lässt sich der Downloadprozess beschleunigen.

Die erstellten Updateringe werden Gerätegruppen zugewiesen. Mithilfe von Updateringen können Sie eine auf Ihre Unternehmensanforderungen ausgerichtete Updatestrategie erstellen. Weitere Informationen finden Sie unter [Verwalten von Updates mit Windows Update for Business](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="before-you-start"></a>Vorbereitung

- Wenn Sie PCs unter Windows 10 aktualisieren möchten, muss auf diesen mindestens Windows 10 Pro mit dem Windows Anniversary-Update ausgeführt werden.

- Windows Update unterstützt folgende Windows 10-Versionen:
    - Windows 10
    - Windows 10 Team (für Surface Hub-Geräte)
    - [Windows Holographic for Business](#windows-holographic-for-business-support)

 Geräte unter Windows 10 Mobile werden nicht unterstützt.

- Auf Windows-Geräten muss **Feedback und Diagnose** > **Diagnose- und Nutzungsdaten** mindestens auf **Basic** festgelegt sein.

    ![Windows-Einstellung für Diagnose- und Nutzungsdaten](./media/telemetry-basic.png)

    Sie können diese Einstellung entweder manuell konfigurieren oder ein Intune-Geräteeinschränkungsprofil für Windows 10 und höher verwenden. Legen Sie hierzu die Einstellung **Allgemein** > **Übermittlung von Diagnosedaten** mindestens auf **Basic** fest. Weitere Informationen zu Geräteprofilen finden Sie unter [So konfigurieren Sie Einstellungen für Geräteeinschränkungen in Microsoft Intune](device-restrictions-configure.md).

- In der Intune-Verwaltungskonsole stehen vier Einstellungen zum Steuern des Verhaltens von Softwareupdates zur Verfügung. Diese Einstellungen sind Teil der allgemeinen Konfigurationsrichtlinie für Desktop- und Mobilgeräte unter Windows 10:
    - **Automatische Updates zulassen**
    - **Vorabfeatures zulassen**
    - **Geplanter Installationstag**
    - **Geplante Installationszeit**

  Im klassischen Portal steht auch eine begrenzte Anzahl anderer Windows 10-Updateeinstellungen im Gerätekonfigurationsprofil zur Verfügung. Falls Sie diese Einstellungen in der Intune-Verwaltungskonsole konfiguriert haben und zum Azure-Portal migrieren, sollten Sie unbedingt die folgenden Schritte ausführen:

1. Erstellen Sie im Azure-Portal Windows 10-Updateringe mit den erforderlichen Einstellungen. Die Einstellung **Vorabfeatures zulassen** wird im Azure-Portal nicht unterstützt, da sie für die neuesten Windows 10-Builds nicht mehr relevant ist. Die drei anderen Einstellungen können zusammen mit anderen Windows 10-Updateeinstellungen beim Erstellen von Updateringen konfiguriert werden.

  > [!NOTE]
  > Im klassischen Portal erstellte Windows 10-Updateeinstellungen werden nach der Migration nicht im Azure-Portal angezeigt. Die Einstellungen werden jedoch weiterhin angewendet. Wenn Sie diese Einstellungen migriert haben und die migrierte Richtlinie über das Azure-Portal bearbeiten, werden die Einstellungen aus der Richtlinie entfernt.

2. Löschen Sie die Updateeinstellungen im klassischen Portal. Wenn Sie zum Azure-Portal migriert sind und die gleichen Einstellungen einem Updatering hinzufügen, müssen Sie die Einstellungen im klassischen Portal löschen, um potenzielle Richtlinienkonflikte zu vermeiden. Ein Beispiel: Falls die gleiche Einstellung mit unterschiedlichen Werten konfiguriert ist, entsteht ein Konflikt, der sich nicht ohne Weiteres diagnostizieren lässt, da die Einstellung, die im klassischen Portal konfiguriert wurde, im Azure-Portal nicht angezeigt wird.

## <a name="how-to-create-and-assign-update-rings"></a>Erstellen und Zuweisen von Updateringen

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Softwareupdates**.
4. Klicken Sie auf dem Blatt **Softwareupdates** auf **Verwalten** > **Windows 10-Updateringe**.
5. Klicken Sie auf dem Blatt mit der Updateringliste auf die Option **Erstellen**.
6. Geben Sie auf dem Blatt **Create Update Ring** (Updatering erstellen) einen Namen und eine optionale Beschreibung für den Updatering an, und klicken Sie anschließend auf **Einstellungen – Konfigurieren**.
7. Konfigurieren Sie im Bereich **Einstellungen** folgende Informationen:
    - **Wartungskanal**: Legen Sie den Kanal fest, für den das Gerät Windows-Updates erhält (halbjährlicher Kanal (gezielt) oder halbjährlicher Kanal).
    - **Microsoft-Produktupdates**: Wählen Sie aus, ob nach App-Updates von Microsoft Update gesucht werden soll.
    - **Windows drivers** (Windows-Treiber): Wählen Sie aus, ob Windows Update-Treiber bei Updates ausgeschlossen werden sollen.
    - **Automatic update behavior** (Verhalten bei automatischen Updates): Wählen Sie aus, wie das Verhalten bei automatischen Updates verwaltet werden soll, um Updates zu suchen, herunterzuladen und zu installieren. Ausführliche Informationen finden Sie unter [Update/AllowAutoUpdate](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#update-allowautoupdate).
    - **Rückstellungszeitraum für Qualitätsupdates (Tage)**: Geben Sie an, für wie viele Tage Qualitätsupdates zurückgestellt werden. Der Bezug dieser Qualitätsupdates kann für bis zu 30 Tage (ab Veröffentlichung) zurückgestellt werden.  

    Bei Qualitätsupdates handelt es sich in der Regel um Korrekturen und Verbesserungen für bereits vorhandene Windows-Funktionen. Sie werden üblicherweise am ersten Dienstag jedes Monats veröffentlicht, können von Microsoft jedoch auch zu einem anderen Zeitpunkt veröffentlicht werden. Sie können definieren, ob und wie lange der Bezug von Qualitätsupdates zurückgestellt werden soll, nachdem sie verfügbar geworden sind.

    - **Rückstellungszeitraum für Funktionsupdates (Tage)**: Geben Sie an, für wie viele Tage Funktionsupdates zurückgestellt werden. Der Bezug dieser Funktionsupdates kann für bis zu 180 Tage (ab Veröffentlichung) zurückgestellt werden.

    Bei Funktionsupdates handelt es sich in der Regel um neue Features für Windows. Nach dem Konfigurieren der Einstellung **Wartungskanal** (halbjährlicher Kanal (gezielt) oder halbjährlicher Kanal) können Sie definieren, ob und wie lange der Bezug von Funktionsupdates zurückgestellt werden soll, nachdem sie von Microsoft über Windows Update verfügbar gemacht wurden.

    Beispiel: **Wenn der Wartungskanal auf „Halbjährlicher Kanal (gezielt)“ festgelegt ist und der Zurückstellungszeitraum 30 Tage beträgt**: Nehmen wir an, dass das Funktionsupdate X auf Windows-Update im halbjährlichen Kanal (gezielt) erstmals im Januar öffentlich verfügbar ist. In diesem Fall erhält das Gerät das Update erst im Februar (also 30 Tage später).

    **Wenn der Wartungskanal auf „Halbjährlicher Kanal (gezielt)“ festgelegt ist und der Zurückstellungszeitraum 30 Tage beträgt**: Nehmen wir an, dass das Funktionsupdate X im halbjährlichen Kanal (gezielt) auf Windows-Update erstmals im Januar öffentlich verfügbar ist. Vier Monate später, im April, wird das Funktionsupdate X dann im halbjährlichen Kanal veröffentlicht. In diesem Fall erhält das Gerät das Funktionsupdate 30 Tage nach dieser Veröffentlichung im halbjährlichen Kanal (also im Mai).

    - **Downloadmodus „Übermittlungsoptimierung“**: Wählen Sie die Methode aus, für welche Geräte Windows-Updates heruntergeladen werden sollen. Ausführliche Informationen finden Sie unter [DeliveryOptimization/DODownloadMode](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode).
1. Klicken Sie abschließend auf **OK** und dann auf dem Blatt **Create Update Ring** (Updatering erstellen) auf **Erstellen**.

Der neue Updatering wird in der Liste mit den Updateringen angezeigt.

1. Wählen Sie zum Zuweisen des Rings in der Liste mit den Updateringen einen Ring aus, und klicken Sie anschließend auf der Registerkarte mit dem *Namen des Rings* auf **Zuweisungen**.
2. Klicken Sie auf der nächsten Registerkarte auf **Select groups to include** (Einzuschließende Gruppen auswählen), und wählen Sie anschließend die Gruppen aus, denen Sie diesen Ring zuweisen möchten.
3. Wählen Sie abschließend **Auswählen** aus, um die Zuweisung abzuschließen.

## <a name="update-compliance-reporting"></a>Updateüberwachungsberichte
Sie können die Updatekompatibilität in Intune anzeigen oder die kostenlose Lösung „Updatekompatibilität“ in Microsoft Operations Management Suite (OMS) verwenden.

### <a name="review-update-compliance-in-intune"></a>Prüfen der Updatekompatibilität in Intune 
<!-- 1352223 -->
Überprüfen Sie einen Richtlinienbericht, um den Bereitstellungsstatus für die Windows 10-Updateringe anzuzeigen, die Sie konfiguriert haben. 
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Softwareupdates**.
4. Klicken Sie auf dem Blatt **Softwareupdates** auf **Übersicht**. Hier finden Sie allgemeine Informationen zum Status der Updateringe, die Sie zugewiesen haben.
5. Öffnen Sie einen der folgenden Berichte: 
     
   **Für alle Bereitstellungsringe**:
   1. Auf dem Blatt **Softwareupdates** > **Windows 10-Updateringe**. 
   2. Wählen Sie **Bereitstellungsstatus pro Updatering** im Abschnitt **Überwachen** aus.
                   
   **Für bestimmte Bereitstellungsringe**: 
   1. Klicken Sie auf dem Blatt **Softwareupdates** > **Windows 10-Updateringe** auf den zu überprüfenden Bereitstellungsring.
   2. Wählen Sie im Abschnitt **Überwachen** einen der folgenden Berichte aus, um weitere Informationen zum Updatering anzuzeigen:
      - **Gerätestatus**
      - **Benutzerstatus**

### <a name="review-update-compliance-using-oms"></a>Prüfen der Updatekompatibilität mithilfe von OMS
Windows 10-Updaterollouts können in der Operations Management Suite (OMS) mithilfe der kostenlosen Updateüberwachung überwacht werden. Ausführliche Informationen finden Sie unter [Monitor Windows Updates with Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor) (Überwachen von Windows-Updates mithilfe der Updateüberwachung). Bei Verwendung dieser Lösung können Sie eine Organisations-ID für jedes Ihrer mit Intune verwalteten Windows 10-Geräte bereitstellen, für das Sie Updateüberwachungsberichte verwenden möchten.

Die Organisations-ID können Sie in der Intune-Konsole mithilfe der OMA-URI-Einstellungen einer benutzerdefinierten Richtlinie konfigurieren. Ausführliche Informationen finden Sie unter [Intune-Richtlinieneinstellungen für Windows 10-Geräte in Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).   

Der OMA-URI-Pfad zum Konfigurieren der Organisations-ID lautet „./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID“. (Hierbei muss die Groß-/Kleinschreibung beachtet werden.)

Unter **OMA-URI-Einstellung hinzufügen oder bearbeiten** können Sie beispielsweise folgende Werte verwenden:

- **Name**: Organisations-ID für die Windows-Analyse
- **Beschreibung**: Konfigurieren der Organisations-ID für Windows Analytics-Lösungen
- **OMA-URI** (Groß-/Kleinschreibung beachten): ./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID
- **Datentyp**: Zeichenfolge
- **Wert**: <*Verwenden Sie die GUID, die in Ihrem OMS-Arbeitsbereich auf der Registerkarte „Windows-Telemetrie“ angezeigt wird.*>

![Windows-Einstellung für Diagnose- und Nutzungsdaten](./media/commID.png)

## <a name="how-to-pause-updates"></a>Aussetzen von Updates
Sie können für ein Gerät den Bezug von Funktions- oder Qualitätsupdates für einen Zeitraum von bis zu 35 Tagen aussetzen (ab dem Zeitpunkt, ab dem die Updates ausgesetzt wurden). Nach Verstreichen der maximalen Anzahl von Tagen wird die Aussetzung automatisch aufgehoben, und das Gerät sucht bei Windows Update nach geeigneten Updates. Danach können Sie die Updates erneut aussetzen.
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Softwareupdates**.
4. Klicken Sie auf dem Blatt **Softwareupdates** auf **Verwalten** > **Windows 10-Updateringe**.
5. Klicken Sie auf dem Blatt mit der Updateringliste auf den anzuhaltenden Ring und anschließend auf **...** > **Qualitätsupdate anhalten** > oder **Funktionsupdate anhalten** (je nachdem, welche Art von Updates Sie anhalten möchten).

> [!IMPORTANT]
> Wenn Sie einen Aussetzungsbefehl erteilen, geht dieser bei den Geräten ein, wenn sie das nächste Mal mit dem Dienst kommunizieren. Es kann vorkommen, dass die Geräte vor der Kommunikation ein geplantes Update installieren.
> Außerdem gilt: Wenn ein Zielgerät bei Erteilung des Aussetzungsbefehls ausgeschaltet ist, lädt es nach dem Einschalten unter Umständen geplante Updates herunter und installiert sie, bevor es mit Intune kommuniziert.

## <a name="windows-holographic-for-business-support"></a>Unterstützung durch Windows Holographic for Business

Windows Holographic for Business unterstützt die folgenden Einstellungen:

- **Automatisches Updateverhalten**
- **Microsoft-Produktupdates**
- **Wartungskanal**