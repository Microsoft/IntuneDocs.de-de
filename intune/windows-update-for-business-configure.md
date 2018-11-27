---
title: Konfigurieren von Windows Update for Business in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Aktualisieren der Softwareupdateeinstellungen in einem Profil zum Erstellen eines Updaterings, Überprüfen der Konformität und Pausieren von Updates in den Einstellungen von Windows Update for Business auf Windows 10-Geräten mithilfe von Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 11/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: a715fe518331d20b9a47d8374a37ce66ec59055d
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189281"
---
# <a name="manage-software-updates-in-intune"></a>Verwalten von Softwareupdates in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows 10-Geräte werden mit Windows-as-a-Service aktualisiert. Ab Windows 10 enthalten neue Feature- und Qualitätsupdates die Inhalte aller früheren Updates. Sie können sich also sicher sein, dass Ihre Windows 10-Geräte auf dem neuesten Stand sind, wenn Sie das neueste Update installiert haben. Im Gegensatz zu früheren Versionen von Windows müssen Sie nun anstelle eines Teilupdates das gesamte Update installieren.

Vereinfachen Sie die Updateverwaltung mithilfe von Windows Update for Business. Sie müssen einzelne Updates für Gerätegruppen nicht genehmigen. Sie können das Risiko in Ihren Umgebungen verwalten, indem Sie eine Updaterolloutstrategie konfigurieren. Windows Update stellt sicher, dass Updates zum richtigen Zeitpunkt installiert werden. Mit Microsoft Intune können Sie Updateeinstellungen auf Geräten konfigurieren und die Updateinstallation zurückstellen. Intune speichert nur die Updaterichtlinienzuweisung, nicht die Updates. Geräte greifen für Updates direkt auf Windows Update zu. Verwenden Sie Intune, um **Windows 10-Updateringe** zu konfigurieren und zu verwalten. Ein Updatering enthält eine Reihe von Einstellungen, die festlegen, wann und wie Updates für Windows 10 installiert werden. Sie können beispielsweise die folgenden Einstellungen konfigurieren:

- **Windows 10-Wartungskanal**: Wählen Sie den Wartungskanal aus, von dem Gerätegruppen Updates erhalten. Folgende Kanäle sind verfügbar: 
  - Halbjährlicher Kanal
  - Halbjähriger Kanal (gezielt)
  - Windows-Insider: schnell
  - Windows-Insider: langsam
  - Windows-Insider-Release 
      
  Weitere Informationen zu den verfügbaren Wartungskanälen finden Sie unter [Übersicht über Windows as a Service](https://docs.microsoft.com/windows/deployment/update/waas-overview#servicing-channels).
- **Zurückstellungseinstellungen:** Konfigurieren Sie Einstellungen für die Zurückstellung von Updates, um Updateinstallationen für Gruppen von Geräten zu verzögern. Verwenden Sie diese Einstellungen zum Staffeln Ihres Updaterollouts, damit Sie den Fortschritt verfolgen können.
- **Wird angehalten:** Wenn bei dem Rollout des Updates ein Fehler auftritt, können Sie die Installation des Updates verschieben. 
- **Wartungsfenster:** Konfigurieren Sie die Zeiten, in denen Updates installiert werden können.
- **Aktualisierungstyp:** Wählen Sie aus, welche Arten von Updates installiert werden. Beispiele wären etwa Qualitätsupdates, Funktionsupdates oder Treiber.
- **Installationsverhalten**: Konfiguriert, wie das Update installiert wird. Hier können Sie beispielsweise festlegen, ob das Gerät nach der Installation automatisch neu gestartet werden soll.
- **Peerdownloads**: Sie können Peerdownloads konfigurieren. Falls ja, können Geräte das Update von einem anderen Gerät herunterladen, das den Downloadvorgang bereits abgeschlossen hat. Durch diese Einstellung lässt sich der Downloadprozess beschleunigen.

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

    Sie können diese Einstellung manuell konfigurieren oder ein Intune-Profil für Windows 10 und höher verwenden (klicken Sie auf **Geräteeinschränkungen** > **Reporting and Telemetry** (Berichterstattung und Telemetrie), und legen Sie für **Share usage data** (Nutzungsdaten freigeben) mindestens **Basic** fest). Weitere Informationen zu Geräteprofilen finden Sie unter [Konfigurieren von Einstellungen für Geräteeinschränkungen](device-restrictions-configure.md).

- Im klassischen Azure-Portal steht auch eine begrenzte Anzahl anderer Windows 10-Updateeinstellungen im Gerätekonfigurationsprofil zur Verfügung. Falls Sie eine dieser Einstellungen konfiguriert haben und zum Azure-Portal migrieren, sollten Sie unbedingt die folgenden Schritte ausführen:

  1. Erstellen Sie im Azure-Portal Windows 10-Updateringe mit den erforderlichen Einstellungen. Die Einstellung **Vorabfeatures zulassen** wird im Azure-Portal nicht unterstützt, da sie für die neuesten Windows 10-Builds nicht mehr relevant ist. Die anderen Einstellungen können zusammen mit anderen Windows 10-Updateeinstellungen beim Erstellen von Updateringen konfiguriert werden.

   > [!NOTE]
   > Im klassischen Portal erstellte Windows 10-Updateeinstellungen werden nach der Migration nicht im Azure-Portal angezeigt. Allerdings werden diese Einstellungen angewendet. Wenn Sie diese Einstellungen migrieren und die migrierte Richtlinie über das Azure-Portal bearbeiten, werden die Einstellungen aus der Richtlinie entfernt.

  2. Löschen Sie die Updateeinstellungen im klassischen Portal. Wenn Sie zum Azure-Portal migriert sind und die gleichen Einstellungen einem Updatering hinzufügen, löschen Sie die Einstellungen im klassischen Portal, um potenzielle Richtlinienkonflikte zu vermeiden. Zum Beispiel kommt es zu einem Konflikt, wenn die gleiche Einstellung mit verschiedenen Werten konfiguriert wird. Dies ist nicht einfach zu ermitteln, da die im klassischen Portal konfigurierte Einstellung nicht im Azure-Portal angezeigt wird.

## <a name="create-and-assign-update-rings"></a>Erstellen und Zuweisen von Updateringen

1. Klicken Sie im [Azure-Portal](https://portal.azure.com) auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie anschließend auf **Microsoft Intune**.
2. Wählen Sie **Softwareupdates** > **Windows 10-Updateringe** > **Erstellen** aus.
3. Geben Sie einen Namen und (optional) eine Beschreibung ein, und klicken Sie dann auf **Konfigurieren**.
4. Geben Sie unter **Einstellungen** die folgenden Informationen ein:

   - **Wartungskanal**: Legen Sie den Kanal fest, von dem das Gerät Windows-Updates erhält.
   - **Microsoft-Produktupdates**: Wählen Sie aus, dass nach App-Updates von Microsoft Update gesucht werden soll.
   - **Windows-Treiber**: Wählen Sie aus, dass Windows Update-Treiber bei Updates ausgeschlossen werden sollen.
   - **Automatisches Updateverhalten**: Wählen Sie aus, wie automatische Updates installiert werden und wann Neustarts ausgeführt werden. Ausführliche Informationen finden Sie unter [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#update-allowautoupdate).
     - **Häufigkeit für automatisches Verhalten**: Wenn Sie **Auto install and restart at scheduled time** (Automatisch zur geplanten Zeit installieren und neustarten) für das Updateverhalten auswählen, wird diese Einstellung angezeigt. Verwenden Sie diese Einstellung zum Planen, wann Updates installiert werden, einschließlich der Woche, des Tags und der Uhrzeit.

   - **Neustartüberprüfungen**: Standardmäßig aktiviert. Wenn Sie ein Gerät neustarten, treten einige Überprüfungen auf, einschließlich der Überprüfung der aktiven Benutzer, dem Akkustand, der ausgeführten Spiele und mehr. Klicken Sie auf **Überspringen**, um diese Überprüfungen beim Neustart eines Geräts zu überspringen.

   - **Rückstellungszeitraum für Qualitätsupdates (Tage)**: Geben Sie die Anzahl der Tage ein, um die die Qualitätsupdates zurückgestellt werden. Sie können diese Qualitätsupdates um bis zu 30 Tage nach der Veröffentlichung zurückstellen.

     Bei Qualitätsupdates handelt es sich in der Regel um Korrekturen und Verbesserungen für bereits vorhandene Windows-Funktionen. Sie werden am zweiten Dienstag jedes Monats veröffentlicht. Dies Updates („B“-Releases) sind nur für Qualitätsupdates über Windows Update verfügbar, obwohl jederzeit weitere Updates von Microsoft veröffentlicht werden können. Sie können definieren, ob und wie lange Sie die Qualitätsupdates zurückstellen, sobald diese auf Windows Update verfügbar sind. Weitere Informationen finden Sie unter [Bereitstellen von Updates mit Windows Update for Business](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb).

   - **Rückstellungszeitraum für Featureupdates (Tage)**: Geben Sie die Anzahl der Tage ein, um die die Featureupdates zurückgestellt werden sollen. Sie können Featureupdates um bis zu 180 Tage nach der Veröffentlichung zurückstellen.

     Bei Featureupdates handelt es sich in der Regel um neue Features für Windows. Nachdem Sie die Einstellung **Wartungskanal** konfiguriert haben, können Sie bestimmen, ob und wie lange Sie die Featureupdates zurückstellen, sobald sie auf Windows Update verfügbar sind.

     Beispiel: **Wenn der Wartungskanal auf „Halbjährlicher Kanal (gezielt)“ festgelegt ist und der Zurückstellungszeitraum 30 Tage beträgt**: Angenommen, das Featureupdate X ist auf Windows Update im halbjährlichen Kanal (gezielt) erstmals im Januar öffentlich verfügbar. Dann erhält das Gerät das Update erst im Februar, also 30 Tage nach der Veröffentlichung.

     **Wenn der Wartungskanal auf „Halbjährlicher Kanal“ festgelegt ist und der Zurückstellungszeitraum 30 Tage beträgt**: Angenommen, das Featureupdate X ist auf Windows-Update erstmals im Januar als halbjährlicher Kanal (gezielt) öffentlich verfügbar. Vier Monate später, im April, wird das Funktionsupdate X dann im halbjährlichen Kanal veröffentlicht. In diesem Fall erhält das Gerät das Featureupdate 30 Tage nach dieser Veröffentlichung im halbjährlichen Kanal (also im Mai).

   - **Downloadmodus „Übermittlungsoptimierung“**: Wählen Sie die Methode aus, für welche Geräte Windows-Updates heruntergeladen werden sollen. Ausführliche Informationen finden Sie unter [DeliveryOptimization/DODownloadMode](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode).

5. Klicken Sie auf **OK**, wenn Sie fertig sind. Klicken Sie unter **Updatering erstellen** auf **Erstellen**.

Der neue Updatering wird in der Liste mit den Updateringen angezeigt.

1. Wählen Sie zum Zuweisen des Rings in der Liste mit den Updateringen einen Ring aus, und klicken Sie anschließend auf der Registerkarte mit dem *Namen des Rings* auf **Zuweisungen**.
2. Klicken Sie auf der nächsten Registerkarte auf **Select groups to include** (Einzuschließende Gruppen auswählen), und wählen Sie anschließend die Gruppen aus, denen Sie diesen Ring zuweisen möchten.
3. Klicken Sie abschließend auf **Auswählen**, um die Zuweisung abzuschließen.

## <a name="update-compliance-reporting"></a>Updateüberwachungsberichte
Sie können die Updatekompatibilität in Intune anzeigen oder die kostenlose Lösung „Updatekonformität“ verwenden.

### <a name="review-update-compliance-in-intune"></a>Prüfen der Updatekompatibilität in Intune 
<!-- 1352223 --> Überprüfen Sie einen Richtlinienbericht, um den Bereitstellungsstatus für die Windows 10-Updateringe anzuzeigen, die Sie konfiguriert haben.

1. Klicken Sie im [Azure-Portal](https://portal.azure.com) auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie anschließend auf **Microsoft Intune**.
2. Wählen Sie **Softwareupdates** > **Übersicht** aus. Hier finden Sie allgemeine Informationen zum Status der Updateringe, die Sie zugewiesen haben.
3. Öffnen Sie einen der folgenden Berichte:

   **Für alle Bereitstellungsringe**:  
   1. Unter **Softwareupdates** > **Windows 10-Updateringe**
   2. Wählen Sie **Bereitstellungsstatus pro Updatering** im Abschnitt **Überwachen** aus.

   **Für bestimmte Bereitstellungsringe**:  
   1. Klicken Sie unter **Softwareupdates** > **Windows 10-Updateringe** auf den zu überprüfenden Bereitstellungsring.
   2. Wählen Sie im Abschnitt **Überwachen** einen der folgenden Berichte aus, um weitere Informationen zum Updatering anzuzeigen:
      - **Gerätestatus**
      - **Benutzerstatus**

### <a name="review-update-compliance-using-oms"></a>Prüfen der Updatekompatibilität mithilfe von OMS
Windows 10-Updaterollouts können mithilfe der kostenlosen Lösung „Updatekonformität“ überwacht werden. Ausführliche Informationen finden Sie unter [Monitor Windows Updates with Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor) (Überwachen von Windows-Updates mithilfe der Updateüberwachung). Bei Verwendung dieser Lösung können Sie eine Organisations-ID für jedes Ihrer mit Intune verwalteten Windows 10-Geräte bereitstellen, für das Sie Updateüberwachungsberichte verwenden möchten.

Die Organisations-ID können Sie in Intune mithilfe der OMA-URI-Einstellungen einer benutzerdefinierten Richtlinie konfigurieren. Ausführliche Informationen finden Sie unter [Intune-Richtlinieneinstellungen für Windows 10-Geräte in Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).   

Der OMA-URI-Pfad (Groß-/Kleinschreibung beachten) zum Konfigurieren der Organisations-ID lautet „./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID“.

Unter **OMA-URI-Einstellung hinzufügen oder bearbeiten** können Sie beispielsweise folgende Werte verwenden:

- **Name**: Organisations-ID für die Windows-Analyse
- **Beschreibung**: Konfigurieren der Organisations-ID für Windows Analytics-Lösungen
- **OMA-URI** (Groß-/Kleinschreibung beachten): ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **Datentyp**: Zeichenfolge
- **Wert**: <*Verwenden Sie die GUID, die in Ihrem OMS-Arbeitsbereich auf der Registerkarte „Windows-Telemetrie“ angezeigt wird.*>

![OMA-URI-Einstellung – Zeile bearbeiten](./media/commID-edit.png)

> [!NOTE]
> Weitere Informationen über MS DM-Server finden Sie unter [DMClient configuration service provider (CSP) (DMClient-Konfigurationsdienstanbieter (CSP))](https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="pause-updates"></a>Pausieren von Updates
Sie können für ein Gerät den Bezug von Funktions- oder Qualitätsupdates für einen Zeitraum von bis zu 35 Tagen aussetzen (ab dem Zeitpunkt, ab dem die Updates ausgesetzt wurden). Nach Verstreichen der maximalen Anzahl von Tagen wird die Aussetzung automatisch aufgehoben, und das Gerät sucht bei Windows Update nach geeigneten Updates. Danach können Sie die Updates erneut aussetzen.

1. Klicken Sie im [Azure-Portal](https://portal.azure.com) auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie anschließend auf **Microsoft Intune**.
2. Wählen Sie **Softwareupdates** > **Windows 10-Updateringe** aus.
3. Klicken Sie in der Updateringliste auf den anzuhaltenden Ring und anschließend auf **...** > **Qualitätsupdate anhalten** > oder **Featureupdate anhalten** (je nachdem, welche Art von Updates Sie anhalten möchten).

> [!IMPORTANT]
> Wenn Sie einen Aussetzungsbefehl erteilen, geht dieser bei den Geräten ein, wenn sie das nächste Mal mit dem Dienst kommunizieren. Es kann vorkommen, dass die Geräte vor der Kommunikation ein geplantes Update installieren.
> Außerdem gilt: Wenn ein Zielgerät bei Erteilung des Aussetzungsbefehls ausgeschaltet ist, lädt es nach dem Einschalten unter Umständen geplante Updates herunter und installiert sie, bevor es mit Intune kommuniziert.

### <a name="uninstall-the-latest-from-windows-10-software-updates"></a>Deinstallieren der letzten Softwareupdates von Windows 10 
Wenn Sie Probleme mit Unterbrechungen auf Ihren Windows 10-Computern feststellen, können Sie das neueste Featureupdate bzw. Qualitätsupdate deinstallieren (einen Rollback ausführen). Die Deinstallation eines Feature- oder Qualitätsupdates ist für den Wartungskanal nur möglich, wenn das Gerät eingeschaltet ist. Durch die Deinstallation wird eine Richtlinie ausgelöst, die das vorherige Update auf Ihren Windows 10-Computern wiederherstellt. Sie können insbesondere für Featureupdates den Zeitraum, in dem eine Deinstallation für die neueste Version durchgeführt werden kann, auf 2–60 Tage einschränken. So legen Sie die Deinstallationsoptionen für Softwareupdates fest:

1. Klicken Sie in Intune auf **Softwareupdates**.
2. Wählen Sie **Windows 10-Updateringe** aus, wählen Sie einen vorhandenen Updatering aus, und klicken Sie auf **Deinstallieren**.

> [!NOTE]
> Nachdem ein erfolgreiches Rollback für das Qualitätsupdate auf Windows 10-Computern ausgeführt wurde, wird das Update weiterhin für Endbenutzer sichtbar unter **Windows-Einstellungen** > **Updates** > **Updateverlauf** aufgeführt.

## <a name="windows-holographic-for-business-support"></a>Unterstützung durch Windows Holographic for Business

Windows Holographic for Business unterstützt die folgenden Einstellungen:

- **Automatisches Updateverhalten**
- **Microsoft-Produktupdates**
- **Wartungskanal**: Unterstützt die Optionen **Halbjährlicher Kanal** und **Halbjährlicher Kanal (gezielt)**
