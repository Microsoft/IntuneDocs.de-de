---
title: 'Windows for Business Update-Einstellungen für Microsoft Intune: Azure | Microsoft-Dokumentation'
description: WUfB-Einstellungen für Windows 10-Geräte, die Sie mit Intune bereitstellen können.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 06982bdf0aff1870f1a759f68bc6cdd48227a3cf
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124995"
---
# <a name="windows-update-settings-for-intune"></a>Windows-Updateeinstellungen für Intune  

Zeigen Sie die Windows 10 Update-Einstellungen an, die Sie mit Microsoft Intune [konfigurieren und verwalten](windows-update-for-business-configure.md) können.  

Wenn Sie Einstellungen für Windows 10-Updateringe in Intune konfigurieren, konfigurieren Sie die Windows Update-Einstellungen. Wenn eine Windows-Updateeinstellung eine Windows 10-Versionsabhängigkeit aufweist, wird die Versionsabhängigkeit in den Einstellungsdetails vermerkt.  

## <a name="update-settings"></a>Updateeinstellungen  

Updateeinstellungen steuern, welche Bits ein Gerät herunterlädt und wann dies geschieht. Weitere Informationen zum Verhalten der einzelnen Einstellungen finden Sie in der Windows-Referenzdokumentation.  

- **Wartungskanal**  
  **Standardeinstellung:** Halbjährlicher Kanal  
  Windows Update-CSP: [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  

  Legen Sie den Kanal (Branch) fest, von dem das Gerät Windows-Updates erhält. Verschiedene Kanäle können verschiedene Verzögerungszeiträume aufweisen, bevor Updates bereitgestellt werden.  

  Der *Halbjährliche Kanal* weist z.B. eine Verzögerung von sechs Monaten auf. Wenn Sie diesen Kanal ohne zusätzliche Verzögerungen über diese Einstellungen nutzen, installiert das Gerät das Update sechs Monate nach seiner Veröffentlichung.  

  Unterstützte Updatekanäle:  

  - Halbjährlicher Kanal  
  - Halbjähriger Kanal (gezielt)  
  - Windows-Insider: schnell  
  - Windows-Insider: langsam  
  - Windows-Insider-Release  

  Wenn Sie einen Insider-Kanal auswählen, konfiguriert Intune automatisch die Windows-Updateeinstellung [Update/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds), damit der Insider-Build funktioniert.  


  > [!IMPORTANT]  
  > Ab Windows-Version 1903 wird die Nutzung des *Halbjährlichen Kanals (gezielt)* (SAC-T) eingestellt. Durch diese Änderung wird SAC-T mit dem *Halbjährlichen Kanal* zusammengeführt. Weitere Informationen zu dieser Änderung und ihren Auswirkungen auf Windows Update for Business finden Sie im Windows IT Pro Blog-Beitrag [Windows Update for Business and the retirement of SAC-T](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523) (Windows Update for Business und die Einstellung von SAC-T).  
 
- **Microsoft-Produktupdates**  
  **Standardeinstellung:**  Zulassen  
  Windows Update-CSP: [Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

  - **Zulassen**: Wählen Sie *Zulassen* aus, um nach App-Updates von Windows Update zu suchen.  
  - **Blockieren**: Wählen Sie „Blockieren“ aus, um die Suche nach App-Updates zu blockieren.  

- **Windows-Treiber**  
  **Standardeinstellung:**  Zulassen  
  Windows Update-CSP: [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)  

  - **Zulassen**: Wählen Sie *Zulassen* aus, um Windows Update-Treiber während Updates einzuschließen.  
  - **Blockieren**: Wählen Sie „Blockieren“ aus, um die Suche nach Treibern zu verhindern.  

- **Zeitraum für die Zurückstellung von Qualitätsupdates in Tagen**  
  **Standardeinstellung:** 0  
  Windows Update-CSP: [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

  Geben Sie die Anzahl von Tagen (0 bis 30) an, für die Qualitätsupdates zurückgestellt werden. Dieser Zeitraum wird zusätzlich zu jedem Verzögerungszeitraum gewährt, der Teil des von Ihnen gewählten Dienstkanals ist. Der Verzögerungszeitraum beginnt mit dem Empfang der Richtlinie durch das Gerät.  

  Bei Qualitätsupdates handelt es sich in der Regel um Korrekturen und Verbesserungen für bereits vorhandene Windows-Funktionen.  

- **Zeitraum für die Zurückstellung von Featureupdates in Tagen**  
  **Standardeinstellung:** 0  
  Windows Update-CSP: [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

  Geben Sie die Anzahl von Tagen an, für die Featureupdates zurückgestellt werden. Dieser Zeitraum wird zusätzlich zu jedem Verzögerungszeitraum gewährt, der Teil des von Ihnen gewählten Dienstkanals ist. Der Verzögerungszeitraum beginnt mit dem Empfang der Richtlinie durch das Gerät.  

  Unterstützter Zurückstellungszeitraum:  

  - *Windows-Version 1709 und höher*: 0 bis 365 Tage  
  - *Windows, Version 1703*: 0 bis 180 Tage  

  Bei Featureupdates handelt es sich in der Regel um neue Features für Windows.  

- **Zeitraum für das Deinstallieren von Featureupdates (2 bis 60 Tage)**  
  **Standardeinstellung:** 10  
  Windows Update-CSP: [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

  Konfigurieren Sie einen Zeitpunkt, nach dem Featureupdates nicht mehr deinstalliert werden können.  

  Nach Ablauf dieser Frist werden die vorherigen Updatebits vom Gerät entfernt, und es kann keine Deinstallation mehr auf eine vorherige Updateversion erfolgen.  

  Stellen Sie sich beispielsweise einen Updatering mit einer Deinstallationsfrist von 20 Tagen vor. Nach 25 Tagen beschließen Sie, ein Rollback des letzten Featureupdates durchzuführen und die Option „Deinstallieren“ zu verwenden.  Geräte, die das Featureupdate vor mehr als 20 Tagen installiert haben, können es nicht deinstallieren, da sie die erforderlichen Bits im Rahmen ihrer Wartung entfernt haben. Auf Geräten, auf denen das Featureupdate erst vor 19 Tagen installiert wurde, kann das Update jedoch deinstalliert werden, wenn sie erfolgreich eingecheckt werden, um den Deinstallationsbefehl zu erhalten, bevor die 20-tägige Deinstallationsfrist abläuft.  

## <a name="user-experience-settings"></a>Einstellungen für die Benutzererfahrung  

Einstellungen für die Benutzererfahrung steuern die Endbenutzererfahrung für den Geräteneustart und Erinnerungen. Weitere Informationen zum Verhalten der einzelnen Einstellungen finden Sie in der Windows Update CSP-Dokumentation.  

- **Automatisches Updateverhalten**  
  **Standardeinstellung:** Automatische Installation während der Wartung  
  Windows Update-CSP: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  Wählen Sie aus, wie automatische Updates installiert und wann Neustarts des Geräts (wenn erforderlich) ausgeführt werden.  

  Unterstützte Optionen:  

  - **Downloadbenachrichtigung**: Benutzer benachrichtigen, bevor das Update heruntergeladen wird. Benutzer entscheiden über das Herunterladen und Installieren von Updates.  

  - **Zur Wartungszeit automatisch installieren**: Updates werden automatisch heruntergeladen und dann während der automatischen Wartung installiert, wenn das Gerät nicht verwendet und auch nicht im Akkubetrieb ausgeführt wird. Wenn ein Neustart erforderlich ist, werden die Benutzer bis zu sieben Tage lang zum Neustart aufgefordert, anschließend wird ein Neustart erzwungen.  

    Diese Option kann ein Gerät automatisch neu starten, nachdem das Update installiert wurde. Verwenden Sie die Einstellungen **Nutzungszeit**, um einen Zeitraum zu definieren, in dem automatische Neustarts blockiert werden:  

    - **Beginn der Nutzungszeit**: Geben Sie eine Startzeit für die Unterdrückung von Neustarts aufgrund von Updateinstallationen an.  
      **Standardeinstellung:** 8:00 Uhr  
      Windows Update-CSP: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Ende der Nutzungszeit**: Geben Sie eine Endzeit für die Unterdrückung von Neustarts aufgrund von Updateinstallationen an.  
      **Standardeinstellung:** 17:00 Uhr  
      Windows Update-CSP: [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Automatische Installation und Neustart während der Wartungszeit**: Updates werden automatisch heruntergeladen und dann während der automatischen Wartung installiert, wenn das Gerät nicht verwendet und auch nicht im Akkubetrieb ausgeführt wird. Wenn ein Neustart erforderlich ist, wird das Gerät neu gestartet, wenn es nicht verwendet wird. (Dies ist die Standardeinstellung für nicht verwaltete Geräte.)  

    Diese Option kann ein Gerät automatisch neu starten, nachdem das Update installiert wurde. Die Verwendung der Einstellungen **Nutzungszeit** wird in den Windows Update-Einstellungen nicht beschrieben. Sie werden aber von Intune verwendet, um einen Zeitraum zu definieren, in dem automatische Neustarts blockiert werden:  

    - **Beginn der Nutzungszeit**: Geben Sie eine Startzeit für die Unterdrückung von Neustarts aufgrund von Updateinstallationen an.  
      **Standardeinstellung:** 8:00 Uhr  
      Windows Update-CSP: [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Ende der Nutzungszeit**: Geben Sie eine Endzeit für die Unterdrückung von Neustarts aufgrund von Updateinstallationen an.  
      **Standardeinstellung:** 17:00 Uhr  
      Windows Update-CSP: [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Automatische Installation und Neustart zur geplanten Zeit**: Geben Sie einen Installationstag und eine -uhrzeit an. Wenn keine Angabe erfolgt, wird die Installation täglich um 3:00 Uhr ausgeführt, gefolgt von einem 15-minütigen Countdown bis zum Neustart. Angemeldete Benutzer können den Countdown und den Neustart verzögern.   
  Windows Update-CSP: [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

    Diese Option unterstützt zusätzliche Einstellungen.  

    - **Häufigkeit für automatisches Verhalten**: Verwenden Sie diese Einstellung zum Planen, wann Updates installiert werden, einschließlich der Woche, des Tags und der Uhrzeit.  
      **Standardeinstellung:** Jede Woche

    - **Tag für geplante Installation:** : Geben Sie an, an welchem Wochentag Updates installiert werden sollen.  
      **Standardeinstellung:** Beliebiger Tag  

    - **Zeitpunkt für geplante Installation**: Geben Sie die Tageszeit an, zu der Updates installiert werden sollen.  
      **Standardeinstellung:** 3:00 Uhr  

  - **Automatische Installation und Neustart ohne Endbenutzersteuerung**: Updates werden automatisch heruntergeladen und dann während der automatischen Wartung installiert, wenn das Gerät nicht verwendet und auch nicht im Akkubetrieb ausgeführt wird. Wenn ein Neustart erforderlich ist, wird das Gerät neu gestartet, wenn es nicht verwendet wird. Durch diese Option wird für den Steuerungsbereich des Endbenutzers der schreibgeschützte Modus festgelegt.  

  - **Standard wiederherstellen**: Stellt die ursprünglichen Einstellungen für automatische Updates auf Windows 10-Computern wieder her, auf denen das Update von Oktober 2018 oder höher ausgeführt wird.  


- **Neustartüberprüfungen**  
  **Standardeinstellung:** Zulassen  
  Windows Update-CSP: [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

  Klicken Sie auf **Überspringen**, um diese Überprüfungen beim Neustart eines Geräts zu überspringen. 
  
  Diese Einstellung hat unterschiedliche Auswirkungen abhängig von der Geräteversion von Windows:  
 
  - *Windows-Version 1703 und früher*: Wenn Sie ein Gerät neu starten, werden einige Überprüfungen ausgeführt, einschließlich der Überprüfung der aktiven Benutzer, des Akkustands, der ausgeführten Spiele und weitere.  
  
  - *Ab Windows-Version 1709*: Während der Nutzungszeit werden die folgenden Prozesse nicht für Updates ausgeführt: Überprüfen, Herunterladen, Installieren und Neustart. Nach der Nutzungszeit werden die Updateprozesse ausgeführt und können das Gerät aus dem Ruhezustand aktivieren, nach Updates suchen, diese herunterladen und installieren und das Gerät neu starten, solange die Akku- und Stromversorgungsüberprüfungen bestanden wurden. 

- **Anhalten von Windows-Updates durch Benutzer blockieren**  
  **Standardeinstellung:** Zulassen  
  Windows Update-CSP: [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

  - **Zulassen**: Gerätebenutzern gestatten, die Installation eines Updates anzuhalten  
  - **Blockieren**: Gerätebenutzer daran hintern, die Installation eines Updates anzuhalten  

- **Überprüfung auf Windows-Updates durch Benutzer blockieren**  
  **Standardeinstellung:** Zulassen  
  Windows Update-CSP: [Update/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

  - **Zulassen**: Zulassen, dass Gerätebenutzer die Windows Update-Überprüfung verwenden, um Updates und Features zu suchen und zu installieren.
  - **Blockieren**: Verhindern, dass Gerätebenutzer auf die Windows Update-Überprüfung zugreifen, Updates herunterladen und Features installieren  

- **Genehmigung des Benutzers für Neustart außerhalb der Nutzungszeiten erfordern**  
  **Standardeinstellung:** Nicht konfiguriert  
  Windows Update-CSP: [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
  - **Nicht konfiguriert**  
  - **Erforderlich**: Der Benutzer muss einen Geräteneustart außerhalb der Nutzungszeiten genehmigen.  
   
- **Benutzer vor erforderlichem automatischen Neustart mit ablehnbarer Erinnerung erinnern (Stunden)**  
  **Standardeinstellung:** 4  
  Windows Update-CSP: [Update/ScheduleRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

  Geben Sie an, wie lange vor einem automatischen Neustart einem Gerätebenutzer eine ablehnbare Benachrichtigung zu diesem Neustart angezeigt werden soll. Werte von **2**, **4**, **8**, **12** und **24** Stunden werden unterstützt.  
  
  Wenn Sie den Standardwert löschen, wird diese Einstellung *nicht konfiguriert*.  

- **Benutzer vor erforderlichem automatischen Neustart mit permanenter Erinnerung erinnern (Minuten)**  
  **Standardeinstellung:** 15  
  Windows Update-CSP: [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning)  

  Geben Sie an, wie lange vor einem automatischen Neustart eine nicht ablehnbare Warnung zu diesem Neustart für einen Gerätebenutzer angezeigt werden soll. Werte von **15**, **30** und **60** Minuten werden unterstützt.  

  Wenn Sie den Standardwert löschen, wird diese Einstellung *nicht konfiguriert*.  

- **Update-Benachrichtigungsstufe ändern**  
  **Standardeinstellung:** Windows Update-Standardbenachrichtigungen verwenden  
  Windows Update-CSP: [Update/UpdateNotificationLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)
  
  Geben Sie an, welche Art von Windows Update-Benachrichtigungen Benutzern angezeigt werden sollen. Diese Einstellung steuert nicht, wie und wann Updates heruntergeladen und installiert werden.  

  Unterstützte Optionen:
  - **Nicht konfiguriert**
  - **Windows Update-Standardbenachrichtigungen verwenden**
  - **Alle Benachrichtigungen mit Ausnahme von Neustartwarnungen deaktivieren**
  - **Alle Benachrichtigungen einschließlich Neustartwarnungen deaktivieren**  

- **Stichtagseinstellungen verwenden**  
  **Standardeinstellung:** Nicht konfiguriert  
 
  Ermöglicht Benutzern die Verwendung von Stichtageinstellungen  

  - **Nicht konfiguriert**
  - **Zulassen**

  Wenn diese Option auf *Zulassen*festgelegt ist, können Sie die folgenden Einstellungen für Stichtage konfigurieren:

  - **Stichtag für Featureupdates**  
    **Standardeinstellung:** *Nicht konfiguriert*  
    Windows Update-CSP: [Update/ConfigureDeadlineForFeatureUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)  

    Gibt an, nach wie viel Tagen Featureupdates automatisch auf den Benutzergeräten installiert werden (2–30)

  - **Stichtag für Qualitätsupdates**  
    **Standardeinstellung:** *Nicht konfiguriert*  
    Windows Update-CSP: [Update/ConfigureDeadlineForQualityUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)

    Gibt an, nach wie viel Tagen Qualitätsupdates automatisch auf den Benutzergeräten installiert werden (2–30)

  - **Karenzzeit**  
    **Standard**: *Nicht konfiguriert* Windows Update: CSP – [Update/ConfigureDeadlineGracePeriod]( https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod)

    Gibt eine Mindestanzahl von Tagen nach dem Stichtag an, bis der Neustart automatisch erfolgt (2–7)

  - **Automatischer Neustart vor Stichtag**  
    **Standard**: Ja, Windows Update-CSP: [Update/ConfigureDeadlineNoAutoReboot](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinenoautoreboot)

    Gibt an, ob das Gerät vor Stichtag automatisch neu gestartet werden soll
    - **Ja**
    - **No**

### <a name="delivery-optimization-download-mode"></a>Downloadmodus für die Übermittlungsoptimierung  

Die Übermittlungsoptimierung wird nicht mehr als Teil eines Windows 10-Updaterings unter „Softwareupdates“ konfiguriert. Sie wird nun über die Gerätekonfiguration festgelegt. Frühere Konfigurationen bleiben jedoch in der Konsole verfügbar. Sie können diese vorherigen Konfigurationen entfernen, indem Sie sie auf *Nicht konfiguriert* festlegen. Anderweitig können sie jedoch nicht geändert werden. 

Um Konflikte zwischen neuer und alter Richtlinie zu vermeiden, lesen Sie [Entfernen der Übermittlungsoptimierung aus den Windows 10-Updateringen](../configuration/delivery-optimization-windows.md#remove-delivery-optimization-from-windows-10-update-rings), und verschieben Sie Ihre Einstellungen dann in ein Profil für die Übermittlungsoptimierung.
