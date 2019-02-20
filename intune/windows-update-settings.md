---
title: 'Windows for Business Update-Einstellungen für Microsoft Intune: Azure | Microsoft-Dokumentation'
description: WUfB-Einstellungen für Windows 10-Geräte, die Sie mit Intune bereitstellen können.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 98c3425c58b6039c8a1c3b5750f9473c74a78634
ms.sourcegitcommit: 93de3423d2d8f0019e676a63784edeb3daf47cb7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/16/2019
ms.locfileid: "56325468"
---
# <a name="windows-update-settings-for-intune"></a>Windows-Updateeinstellungen für Intune  

Zeigen Sie die Windows 10 Update-Einstellungen an, die Sie mit Microsoft Intune [konfigurieren und verwalten](windows-update-for-business-configure.md) können.  

Wenn Sie Einstellungen für Windows 10-Updateringe in Intune konfigurieren, konfigurieren Sie die Windows Update-Einstellungen.  Wenn eine Windows-Updateeinstellung eine Windows 10-Versionsabhängigkeit aufweist, wird die Versionsabhängigkeit in den Einstellungsdetails vermerkt.  

## <a name="update-settings"></a>Updateeinstellungen  

Updateeinstellungen steuern, welche Bits ein Gerät herunterlädt und wann dies geschieht. Weitere Informationen zum Verhalten der einzelnen Einstellungen finden Sie in der Windows-Referenzdokumentation.  

### <a name="servicing-channel"></a>Wartungskanal  

- **Standardeinstellung:** Halbjährlicher Kanal (gezielt)  
- **Windows-Referenzdokumentation**: [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  
Legen Sie den Kanal (Branch) fest, von dem das Gerät Windows-Updates erhält. Verschiedene Kanäle können verschiedene Verzögerungszeiträume aufweisen, bevor Updates bereitgestellt werden.  

Der *Halbjährliche Kanal* weist z.B. eine Verzögerung von sechs Monaten auf. Das bedeutet, wenn Sie diesen Kanal ohne zusätzliche Verzögerungen aus diesem Einstellbereich nutzen, installiert das Gerät das Update sechs Monate nach seinem Release.  

Unterstützte Updatekanäle:  

- Halbjährlicher Kanal  
- Halbjähriger Kanal (gezielt)  
- Windows-Insider: schnell  
- Windows-Insider: langsam  
- Windows-Insider-Release  

Wenn Sie einen Insider-Kanal auswählen, konfiguriert Intune automatisch die Windows-Updateeinstellung [Update/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds), damit der Insider-Build funktioniert.  


> [!IMPORTANT]  
> Ab Windows-Version 1903 wird die Nutzung des *Halbjährlichen Kanals (gezielt)* (SAC-T) eingestellt. Durch diese Änderung wird SAC-T mit dem *Halbjährlichen Kanal* zusammengeführt. Weitere Informationen zu dieser Änderung und ihren Auswirkungen auf Windows Update for Business finden Sie im Windows IT Pro Blog-Beitrag [Windows Update for Business and the retirement of SAC-T](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523) (Windows Update for Business und die Einstellung von SAC-T).
 


### <a name="microsoft-product-updates"></a>Microsoft-Produktupdates  

- **Standardeinstellung:**  Zulassen
- **Windows-Referenzdokumentation**: [Update/AllowMUUpdateService](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

Wählen Sie *Zulassen* aus, um nach App-Updates von Microsoft Update zu suchen.    

### <a name="windows-drivers"></a>Windows-Treiber  

- **Standardeinstellung:**  Zulassen
- **Windows-Referenzdokumentation**: [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)

Wählen Sie *Zulassen* aus, um Windows Update-Treiber bei Updates einzuschließen.

### <a name="quality-update-deferral-period-days"></a>Zeitraum für die Zurückstellung von Qualitätsupdates in Tagen  

- **Standardeinstellung:** 0  
- **Windows-Referenzdokumentation**: [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

Geben Sie die Anzahl von Tagen (0 bis 30) an, für die Qualitätsupdates zurückgestellt werden. Dieser Zeitraum wird zusätzlich zu jedem Verzögerungszeitraum gewährt, der Teil des von Ihnen gewählten Dienstkanals ist. Der Verzögerungszeitraum beginnt mit dem Empfang der Richtlinie durch das Gerät.  

Bei Qualitätsupdates handelt es sich in der Regel um Korrekturen und Verbesserungen für bereits vorhandene Windows-Funktionen.  

### <a name="feature-update-deferral-period-days"></a>Zeitraum für die Zurückstellung von Featureupdates in Tagen  

- **Standardeinstellung:** 0  
- **Windows-Referenzdokumentation**: [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

Geben Sie die Anzahl von Tagen an, für die Featureupdates zurückgestellt werden. Dieser Zeitraum wird zusätzlich zu jedem Verzögerungszeitraum gewährt, der Teil des von Ihnen gewählten Dienstkanals ist. Der Verzögerungszeitraum beginnt mit dem Empfang der Richtlinie durch das Gerät.  
Unterstützter Zurückstellungszeitraum:  

- *Windows, Version 1709 oder höher*: 0 bis 365 Tage  
- *Windows, Version 1703*:  0 bis 180 Tage  

Bei Featureupdates handelt es sich in der Regel um neue Features für Windows.  

### <a name="set-feature-update-uninstall-period-2--60-days"></a>Zeitraum für das Deinstallieren von Featureupdates (2 bis 60 Tage)  

- **Standardeinstellung:** 10  
- **Windows-Referenzdokumentation**:  [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

Konfigurieren Sie einen Zeitpunkt, nach dem Featureupdates nicht mehr deinstalliert werden können.  

Nach Ablauf dieser Frist werden die vorherigen Updatebits vom Gerät entfernt, und es kann keine Deinstallation mehr auf eine vorherige Updateversion erfolgen.  

Stellen Sie sich beispielsweise einen Updatering mit einer Deinstallationsfrist von 20 Tagen vor. Nach 25 Tagen beschließen Sie, ein Rollback des letzten Featureupdates durchzuführen und die Option „Deinstallieren“ zu verwenden.  Geräte, die das Featureupdate vor mehr als 20 Tagen installiert haben, können es nicht deinstallieren, da sie die erforderlichen Bits im Rahmen ihrer Wartung entfernt haben. Geräte, die das Featureupdate erst vor 19 Tagen installiert haben, können das Update jedoch deinstallieren, wenn sie sich erfolgreich einchecken, um den Deinstallationsbefehl zu erhalten, bevor sie die 20-tägige Deinstallationsfrist überschreiten.  


## <a name="user-experience-settings"></a>Einstellungen für die Benutzererfahrung  

Einstellungen für die Benutzererfahrung steuern die Endbenutzererfahrung für den Geräteneustart und Erinnerungen. Weitere Informationen zum Verhalten der einzelnen Einstellungen finden Sie in der Windows-Referenzdokumentation.  

### <a name="automatic-update-behavior"></a>Verhalten automatischer Updates  

- **Standardeinstellung:** Automatische Installation und Neustart zu einer geplanten Zeit  
- **Windows-Referenzdokumentation**: [Update/AllowAutoUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

Wählen Sie aus, wie automatische Updates installiert und wann Neustarts des Geräts (wenn erforderlich) ausgeführt werden.  

In der Windows-Referenzdokumentation finden Sie die vollständige Beschreibung der folgenden unterstützten Optionen:  

- **Downloadbenachrichtigung**: Benutzer benachrichtigen, bevor das Update heruntergeladen wird. Benutzer entscheiden über das Herunterladen und Installieren von Updates.  

- **Automatische Installation während der Wartungszeit**: Updates werden automatisch heruntergeladen und dann während der automatischen Wartung installiert, wenn das Gerät nicht verwendet und auch nicht im Akkubetrieb ausgeführt wird. Wenn ein Neustart erforderlich ist, werden die Benutzer bis zu sieben Tage lang zum Neustart aufgefordert, anschließend wird ein Neustart erzwungen.  

  Diese Option kann ein Gerät automatisch neu starten, nachdem das Update installiert wurde. Verwenden Sie die Einstellungen **Nutzungszeit**, um einen Zeitraum zu definieren, in dem automatische Neustarts blockiert werden:  

  - **Beginn der Nutzungszeit**: Geben Sie eine Startzeit für die Unterdrückung von Neustarts aufgrund von Updateinstallationen an.  
    **Windows-Referenzdokumentation**:  [Update/ActiveHoursStart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Standardeinstellung:** 8:00 Uhr  
  
  - **Ende der Nutzungszeit**: Geben Sie eine Endzeit für die Unterdrückung von Neustarts aufgrund von Updateinstallationen an.  
    **Windows-Referenzdokumentation**:  [Update/ActiveHoursEnd](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Standardeinstellung:** 17:00 Uhr  

- **Automatische Installation und Neustart während der Wartungszeit**: Updates werden automatisch heruntergeladen und dann während der automatischen Wartung installiert, wenn das Gerät nicht verwendet und auch nicht im Akkubetrieb ausgeführt wird. Wenn ein Neustart erforderlich ist, wird das Gerät neu gestartet, wenn es nicht verwendet wird. (Dies ist die Standardeinstellung für nicht verwaltete Geräte.)  

  Diese Option kann ein Gerät automatisch neu starten, nachdem das Update installiert wurde. Die Verwendung der Einstellungen **Nutzungszeit** wird in den Windows Update-Einstellungen nicht beschrieben. Sie werden aber von Intune verwendet, um einen Zeitraum zu definieren, in dem automatische Neustarts blockiert werden:  

  - **Beginn der Nutzungszeit**: Geben Sie eine Startzeit für die Unterdrückung von Neustarts aufgrund von Updateinstallationen an.  
    **Windows-Referenzdokumentation**:  [Update/ActiveHoursStart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Standardeinstellung:** 8:00 Uhr  

  - **Ende der Nutzungszeit**: Geben Sie eine Endzeit für die Unterdrückung von Neustarts aufgrund von Updateinstallationen an.  
    **Windows-Referenzdokumentation**:  [Update/ActiveHoursEnd](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Standardeinstellung:** 17:00 Uhr  

- **Automatische Installation und Neustart zur geplanten Zeit**: Geben Sie einen Installationstag und eine -uhrzeit an. Wenn keine Angabe erfolgt, wird die Installation täglich um 3:00 Uhr ausgeführt, gefolgt von einem 15-minütigen Countdown bis zum Neustart. Angemeldete Benutzer können den Countdown und den Neustart verzögern.  
  
  Diese Option unterstützt zusätzliche Einstellungen.  
  **Windows-Referenzdokumentation**:  [Update/AllowAutoUpdate](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  - **Häufigkeit für automatisches Verhalten**: Verwenden Sie diese Einstellung zum Planen, wann Updates installiert werden, einschließlich der Woche, des Tags und der Uhrzeit.  
    **Standardeinstellung:** Jede Woche

  - **Geplanter Installationstag**:  Geben Sie an, an welchem Wochentag Updates installiert werden sollen.  
    **Standardeinstellung:** Beliebiger Tag  

  - **Geplante Installationszeit**:  Geben Sie die Uhrzeit an, zu der Updates installiert werden sollen.  
    **Standardeinstellung:** 3:00 Uhr  

- **Automatische Installation und Neustart ohne Endbenutzersteuerung**: Updates werden automatisch heruntergeladen und dann während der automatischen Wartung installiert, wenn das Gerät nicht verwendet und auch nicht im Akkubetrieb ausgeführt wird. Wenn ein Neustart erforderlich ist, wird das Gerät neu gestartet, wenn es nicht verwendet wird. Durch diese Option wird für den Steuerungsbereich des Endbenutzers der schreibgeschützte Modus festgelegt.  

- **Standard wiederherstellen**: Stellt die ursprünglichen Einstellungen für automatische Updates auf Windows 10-Computern wieder her, auf denen das Update von Oktober 2018 oder höher ausgeführt wird.  


### <a name="restart-checks"></a>Neustartüberprüfungen  

- **Standardeinstellung:** Zulassen  
- **Windows-Referenzdokumentation**: [Update/SetEDURestart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

Diese Einstellung hat unterschiedliche Auswirkungen abhängig von der Geräteversion von Windows:  

- Windows, Version 1703 und früher: Wenn Sie ein Gerät neustarten, treten einige Überprüfungen auf, einschließlich der Überprüfung der aktiven Benutzer, dem Akkustand, der ausgeführten Spiele und mehr. Klicken Sie auf **Überspringen**, um diese Überprüfungen beim Neustart eines Geräts zu überspringen.  
- Ab Windows-Version 1709: Während der Nutzungszeit werden die folgenden Prozesse nicht für Updates ausgeführt: Überprüfen, Herunterladen, Installieren und Neustart. Nach der Nutzungszeit werden die Updateprozesse ausgeführt und können das Gerät aus dem Ruhezustand aktivieren, nach Updates suchen, diese herunterladen und installieren und das Gerät neu starten, solange die Akku- und Stromversorgungsüberprüfungen bestanden wurden. Weitere Informationen finden Sie unter [Update/SetEDURestart](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setedurestart).  

### <a name="block-user-from-pausing-windows-updates"></a>Anhalten von Windows-Updates durch Benutzer blockieren  

- **Standardeinstellung:** Zulassen  
- **Windows-Referenzdokumentation**: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

Zulassen oder Blockieren des Anhaltens der Installation eines Updates durch einen Gerätebenutzer.  

### <a name="require-users-approval-to-restart-outside-of-work-hours"></a>Genehmigung des Benutzers für Neustart außerhalb der Nutzungszeiten erfordern  

- **Standardeinstellung:** Nicht konfiguriert  
- **Windows-Referenzdokumentation**: [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
Wählen Sie *Erforderlich* aus, wenn ein Geräteneustart außerhalb der Nutzungszeiten durch den Benutzer genehmigt werden muss.  
   
### <a name="remind-user-prior-to-required-auto-restart-with-dismissible-reminder-hours"></a>Benutzer vor erforderlichem automatischen Neustart mit ablehnbarer Erinnerung erinnern (Stunden)  

- **Standardeinstellung:** *Dies ist nicht standardmäßig konfiguriert, und Benutzern wird keine Erinnerung angezeigt*.  
- **Windows-Referenzdokumentation**: [Update/ScheduleRestartWarning](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

Geben Sie an, wie lange vor einem automatischen Neustart einem Gerätebenutzer eine ablehnbare Benachrichtigung zu diesem Neustart angezeigt werden soll. Werte von **2**, **4**, **8**, **12** und **24** Stunden werden unterstützt.  

### <a name="remind-user-prior-to-required-auto-restart-with-permanent-reminder-minutes"></a>Benutzer vor erforderlichem automatischen Neustart mit permanenter Erinnerung erinnern (Minuten)  

- **Standardeinstellung:** *Dies ist nicht standardmäßig konfiguriert, und Benutzern wird keine Erinnerung angezeigt*.  
- **Windows-Referenzdokumentation**: [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning) 

Geben Sie an, wie lange vor einem automatischen Neustart eine nicht ablehnbare Warnung zu diesem Neustart für einen Gerätebenutzer angezeigt werden soll. Werte von **15**, **30** und **60** Minuten werden unterstützt.  
 
### <a name="allow-user-to-restart-engaged-restart"></a>Benutzer Neustart erlauben (erzwungener Neustart)  

- **Standardeinstellung:** Nicht konfiguriert  
- **Windows-Referenzdokumentation**: *Nicht verfügbar*  
- **Windows-Version**: Unterstützt für Windows 10, Version 1803 und höher  

  > [!NOTE]  
  > Windows 10 (Version 1809) führt zusätzliche erzwungene Neustarteinstellungen ein, die es ermöglichen, separate Einstellungen für Feature- und Qualitätsupdates anzuwenden. Die von Intune verwalteten Einstellungen gelten jedoch nicht separat für die verschiedenen Updatetypen. Stattdessen wendet Intune die gleichen Werte auf Feature- und Qualitätsupdates an.  

Wenn die Option auf **Erforderlich** festgelegt ist, aktivieren Sie die Verwendung der Optionen für erzwungenen Neustart für Windows 10-Updates. Diese Optionen ermöglichen dem Benutzer eines Geräts die Verwaltung des Zeitpunkts für den Neustart eines Geräts nach der Installation eines Updates, das einen Neustart erfordert.  

Weitere Informationen zu dieser Option finden Sie unter [Erzwungener Neustart](https://docs.microsoft.com/en-us/windows/deployment/update/waas-restart#engaged-restart) in der Windows 10-Dokumentation zur Bereitstellung von Updates.  

Die folgenden Einstellungen werden zum Steuern verwendet, wann erzwungene Neustartaktionen auftreten.  

- **Benutzer nach automatischem Neustart auf erzwungenen Neustart umstellen (Tage)**  
  - **Standardeinstellung:**  Diese Option ist standardmäßig nicht konfiguriert, unterstützt aber Werte von **2** bis **30**.  
  - **Windows-Referenzdokumentation**: [Update/EngagedRestartTransitionSchedule](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
  Geben Sie an, wie lange es nach der Installation der Updates dauert, bis das Gerät in das erzwungene Neustartverhalten wechselt. Nach der konfigurierten Anzahl von Tagen erhalten Benutzer eine Aufforderung zum Neustarten des Geräts.  

- **Erneut erinnern bei erzwungener Neustarterinnerung (Tage)**  
  - **Standardeinstellung:**  Diese Option ist standardmäßig nicht konfiguriert, unterstützt aber Werte von **1** bis **3**.  
  - **Windows-Referenzdokumentation**: [Update/EngagedRestartSnoozeSchedule](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
  Geben Sie an, wie lange eine Neustartaufforderung als erneute Erinnerung festgelegt werden kann.  Nach Ablauf des Zeitraums für erneutes Erinnern wird die Neustartaufforderung erneut angeboten. Der Benutzer kann die Erinnerung weiterhin auf „Erneut erinnern“ festlegen, bis der Stichtag für die Installation erreicht ist.  

- **Stichtag für ausstehende Neustarts festlegen (Tage)**  
  - **Standardeinstellung:**  Diese Option ist standardmäßig nicht konfiguriert, unterstützt aber Werte von **2** bis **30**.  
  - **Windows-Referenzdokumentation**: [Update/EngagedRestartDeadline](https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  Geben Sie eine maximale Anzahl der Tage an, die nach Beginn des erzwungenen Neustartverhaltens gewartet wird, bis ein Gerät einen erforderlichen Neustart erzwingt. Dieser Neustart fordert Benutzer zum Speichern ihrer Arbeit auf.

### <a name="delivery-optimization-download-mode"></a>Downloadmodus für die Übermittlungsoptimierung  

- **Standardeinstellung:**  Nicht verfügbar
- **Windows-Referenzdokumentation**: *Nicht verfügbar*

Die Übermittlungsoptimierung wird nicht mehr als Teil eines Windows 10-Updaterings unter „Softwareupdates“ konfiguriert. Sie wird nun über die Gerätekonfiguration festgelegt. Frühere Konfigurationen bleiben jedoch in der Konsole verfügbar. Sie können diese vorherigen Konfigurationen entfernen, indem Sie sie auf *Nicht konfiguriert* setzen. Anderweitig können sie jedoch nicht geändert werden. 

Um Konflikte zwischen neuer und alter Richtlinie zu vermeiden, lesen Sie [Wechsel von vorhandenen Updateringen zur Übermittlungsoptimierung](https://docs.microsoft.com/en-us/intune/delivery-optimization-windows#move-from-existing-update-rings-to-delivery-optimization) und verschieben Ihre Einstellungen dann in ein Profil für die Übermittlungsoptimierung.


