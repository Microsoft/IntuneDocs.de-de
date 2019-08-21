---
title: 'Windows for Business Update-Einstellungen für Microsoft Intune: Azure | Microsoft-Dokumentation'
description: WUfB-Einstellungen für Windows 10-Geräte, die Sie mit Intune bereitstellen können.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e44f9d0848d449ef9131c76784ca8c7244b7c223
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550109"
---
# <a name="windows-update-settings-for-intune"></a>Windows-Updateeinstellungen für Intune  

Zeigen Sie die Windows 10 Update-Einstellungen an, die Sie mit Microsoft Intune [konfigurieren und verwalten](windows-update-for-business-configure.md) können.  

Wenn Sie Einstellungen für Windows 10-Updateringe in Intune konfigurieren, konfigurieren Sie die Windows Update-Einstellungen. Wenn eine Windows-Updateeinstellung eine Windows 10-Versionsabhängigkeit aufweist, wird die Versionsabhängigkeit in den Einstellungsdetails vermerkt.  

## <a name="update-settings"></a>Updateeinstellungen  

Updateeinstellungen steuern, welche Bits ein Gerät herunterlädt und wann dies geschieht. Weitere Informationen zum Verhalten der einzelnen Einstellungen finden Sie in der Windows-Referenzdokumentation.  

- **Wartungskanal**  
  **Standardeinstellung**: Halbjährlicher Kanal  
  Windows Update CSP: [Update/BranchInfo Iness Level](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  

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
  Windows Update CSP: [Update/allowmuupdateservice](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

  - **Zulassen** : Wählen Sie *zulassen* aus, um nach APP-Updates von Microsoft Update zu suchen.  
  - **Block** -SELECT-Block, um das Scannen von APP-Updates zu verhindern.  

- **Windows-Treiber**  
  **Standardeinstellung:**  Zulassen  
  Windows Update CSP: [Update/excluentwudriversinqualityupdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)  

  - **Zulassen** : aktivieren Sie die Option zum Einschließen von Windows Update Treibern bei Updates.  
  - **Block** -SELECT-Block, um das Überprüfen von Treibern zu verhindern.  

- **Zeitraum für die Zurückstellung von Qualitätsupdates in Tagen**  
  **Standardeinstellung**: 0  
  Windows Update CSP: [Update/deferqualityupdatesperiodindays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

  Geben Sie die Anzahl von Tagen (0 bis 30) an, für die Qualitätsupdates zurückgestellt werden. Dieser Zeitraum wird zusätzlich zu jedem Verzögerungszeitraum gewährt, der Teil des von Ihnen gewählten Dienstkanals ist. Der Verzögerungszeitraum beginnt mit dem Empfang der Richtlinie durch das Gerät.  

  Bei Qualitätsupdates handelt es sich in der Regel um Korrekturen und Verbesserungen für bereits vorhandene Windows-Funktionen.  

- **Zeitraum für die Zurückstellung von Featureupdates in Tagen**  
  **Standardeinstellung**: 0  
  Windows Update CSP: [Update/paucfeatureupdatesperiodindays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

  Geben Sie die Anzahl von Tagen an, für die Featureupdates zurückgestellt werden. Dieser Zeitraum wird zusätzlich zu jedem Verzögerungszeitraum gewährt, der Teil des von Ihnen gewählten Dienstkanals ist. Der Verzögerungszeitraum beginnt mit dem Empfang der Richtlinie durch das Gerät.  

  Unterstützter Zurückstellungszeitraum:  

  - *Windows-Version 1709 und* höher: 0 bis 365 Tage  
  - *Windows, Version 1703*: 0 bis 180 Tage  

  Bei Featureupdates handelt es sich in der Regel um neue Features für Windows.  

- **Zeitraum für das Deinstallieren von Featureupdates (2 bis 60 Tage)**  
  **Standard**: 10  
  Windows Update CSP: [Update/Konfiguration refeatureupdateuninstallperiod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

  Konfigurieren Sie einen Zeitpunkt, nach dem Featureupdates nicht mehr deinstalliert werden können.  

  Nach Ablauf dieser Frist werden die vorherigen Updatebits vom Gerät entfernt, und es kann keine Deinstallation mehr auf eine vorherige Updateversion erfolgen.  

  Stellen Sie sich beispielsweise einen Updatering mit einer Deinstallationsfrist von 20 Tagen vor. Nach 25 Tagen beschließen Sie, ein Rollback des letzten Featureupdates durchzuführen und die Option „Deinstallieren“ zu verwenden.  Geräte, die das Featureupdate vor mehr als 20 Tagen installiert haben, können es nicht deinstallieren, da sie die erforderlichen Bits im Rahmen ihrer Wartung entfernt haben. Auf Geräten, auf denen das Featureupdate erst vor 19 Tagen installiert wurde, kann das Update jedoch deinstalliert werden, wenn sie erfolgreich eingecheckt werden, um den Deinstallationsbefehl zu erhalten, bevor die 20-tägige Deinstallationsfrist abläuft.  

## <a name="user-experience-settings"></a>Einstellungen für die Benutzererfahrung  

Einstellungen für die Benutzererfahrung steuern die Endbenutzererfahrung für den Geräteneustart und Erinnerungen. Weitere Informationen zum Verhalten der einzelnen Einstellungen finden Sie in der Windows Update CSP-Dokumentation.  

- **Automatisches Updateverhalten**  
  **Standard**: Automatische Installation während der Wartung  
  Windows Update CSP: [Update/allowautoupdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  Wählen Sie aus, wie automatische Updates installiert und wann Neustarts des Geräts (wenn erforderlich) ausgeführt werden.  

  Unterstützte Optionen:  

  - **Downloadbenachrichtigung**: Benutzer benachrichtigen, bevor das Update heruntergeladen wird. Benutzer entscheiden über das Herunterladen und Installieren von Updates.  

  - **Zur Wartungszeit automatisch installieren**: Updates werden automatisch heruntergeladen und dann während der automatischen Wartung installiert, wenn das Gerät nicht verwendet und auch nicht im Akkubetrieb ausgeführt wird. Wenn ein Neustart erforderlich ist, werden die Benutzer bis zu sieben Tage lang zum Neustart aufgefordert, anschließend wird ein Neustart erzwungen.  

    Diese Option kann ein Gerät automatisch neu starten, nachdem das Update installiert wurde. Verwenden Sie die Einstellungen **Nutzungszeit**, um einen Zeitraum zu definieren, in dem automatische Neustarts blockiert werden:  

    - **Beginn der Nutzungszeit**: Geben Sie eine Startzeit für die Unterdrückung von Neustarts aufgrund von Updateinstallationen an.  
      **Standardeinstellung:** 08:00 Uhr  
      Windows Update CSP: [Update/activehoursstart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Ende der Nutzungszeit**: Geben Sie eine Endzeit für die Unterdrückung von Neustarts aufgrund von Updateinstallationen an.  
      **Standardeinstellung:** 17:00 Uhr  
      Windows Update CSP: [Update/activehoursend](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Automatische Installation und Neustart während der Wartungszeit**: Updates werden automatisch heruntergeladen und dann während der automatischen Wartung installiert, wenn das Gerät nicht verwendet und auch nicht im Akkubetrieb ausgeführt wird. Wenn ein Neustart erforderlich ist, wird das Gerät neu gestartet, wenn es nicht verwendet wird. (Dies ist die Standardeinstellung für nicht verwaltete Geräte.)  

    Diese Option kann ein Gerät automatisch neu starten, nachdem das Update installiert wurde. Die Verwendung der Einstellungen **Nutzungszeit** wird in den Windows Update-Einstellungen nicht beschrieben. Sie werden aber von Intune verwendet, um einen Zeitraum zu definieren, in dem automatische Neustarts blockiert werden:  

    - **Beginn der Nutzungszeit**: Geben Sie eine Startzeit für die Unterdrückung von Neustarts aufgrund von Updateinstallationen an.  
      **Standardeinstellung:** 08:00 Uhr  
      Windows Update CSP: [Update/activehoursstart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Ende der Nutzungszeit**: Geben Sie eine Endzeit für die Unterdrückung von Neustarts aufgrund von Updateinstallationen an.  
      **Standardeinstellung:** 17:00 Uhr  
      Windows Update CSP: [Update/activehoursend](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Automatische Installation und Neustart zur geplanten Zeit**: Geben Sie einen Installationstag und eine -uhrzeit an. Wenn keine Angabe erfolgt, wird die Installation täglich um 3:00 Uhr ausgeführt, gefolgt von einem 15-minütigen Countdown bis zum Neustart. Angemeldete Benutzer können den Countdown und den Neustart verzögern.   
  Windows Update CSP: [Update/allowautoupdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

    Diese Option unterstützt zusätzliche Einstellungen.  

    - **Häufigkeit für automatisches Verhalten**: Verwenden Sie diese Einstellung zum Planen, wann Updates installiert werden, einschließlich der Woche, des Tags und der Uhrzeit.  
      **Standardeinstellung:** Wöchentlich

    - **Tag für geplante Installation:**: Geben Sie an, an welchem Wochentag Updates installiert werden sollen.  
      **Standardeinstellung:** Täglich  

    - **Zeitpunkt für geplante Installation**: Geben Sie die Tageszeit an, zu der Updates installiert werden sollen.  
      **Standardeinstellung**: 03:00 Uhr  

  - **Automatische Installation und Neustart ohne Endbenutzersteuerung**: Updates werden automatisch heruntergeladen und dann während der automatischen Wartung installiert, wenn das Gerät nicht verwendet und auch nicht im Akkubetrieb ausgeführt wird. Wenn ein Neustart erforderlich ist, wird das Gerät neu gestartet, wenn es nicht verwendet wird. Durch diese Option wird für den Steuerungsbereich des Endbenutzers der schreibgeschützte Modus festgelegt.  

  - **Standard wiederherstellen**: Stellt die ursprünglichen Einstellungen für automatische Updates auf Windows 10-Computern wieder her, auf denen das Update von Oktober 2018 oder höher ausgeführt wird.  


- **Neustartüberprüfungen**  
  **Standardeinstellung:** Zulassen  
  Windows Update CSP: [Update/](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart) "".  

  Klicken Sie auf **Überspringen**, um diese Überprüfungen beim Neustart eines Geräts zu überspringen. 
  
  Diese Einstellung hat unterschiedliche Auswirkungen abhängig von der Geräteversion von Windows:  
 
  - *Windows-Version 1703 und früher*: Wenn Sie ein Gerät neu starten, werden einige Überprüfungen ausgeführt, einschließlich der Überprüfung der aktiven Benutzer, des Akkustands, der ausgeführten Spiele und weitere.  
  
  - *Ab Windows-Version 1709*: Während der Nutzungszeit werden die folgenden Prozesse nicht für Updates ausgeführt: Überprüfen, Herunterladen, Installieren und Neustart. Nach der Nutzungszeit werden die Updateprozesse ausgeführt und können das Gerät aus dem Ruhezustand aktivieren, nach Updates suchen, diese herunterladen und installieren und das Gerät neu starten, solange die Akku- und Stromversorgungsüberprüfungen bestanden wurden. 

- **Anhalten von Windows-Updates durch Benutzer blockieren**  
  **Standardeinstellung:** Zulassen  
  Windows Update CSP: [Update/setdisablepauseuxaccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

  - **Zulassen** : Geräte Benutzern gestatten, die Installation eines Updates anzuhalten.  
  - **Blockieren** : verhindert, dass Gerätebenutzer die Installation eines Updates anhalten.  

- **Überprüfung auf Windows-Updates durch Benutzer blockieren**  
  **Standardeinstellung:** Zulassen  
  Windows Update CSP: [Update/setdisableuxwuaccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

  - **Zulassen** : zulassen, dass Gerätebenutzer Windows Update Scan verwenden, um Updates zu suchen und herunterzuladen und Features zu installieren.
  - **Blockieren** : verhindern Sie, dass Gerätebenutzer auf den Windows Update Scan zugreifen, Updates herunterladen und Features installieren.  

- **Genehmigung des Benutzers für Neustart außerhalb der Nutzungszeiten erfordern**  
  **Standardeinstellung:** Nicht konfiguriert  
  Windows Update CSP: [Update/autorestartrequirednotificationentlassung](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
  - **Nicht konfiguriert**  
  - **Erforderlich**: Der Benutzer muss einen Geräteneustart außerhalb der Nutzungszeiten genehmigen.  
   
- **Benutzer vor erforderlichem automatischen Neustart mit ablehnbarer Erinnerung erinnern (Stunden)**  
  **Standard**: 4  
  Windows Update CSP: [Update/schedulerestartwarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

  Geben Sie an, wie lange vor einem automatischen Neustart einem Gerätebenutzer eine ablehnbare Benachrichtigung zu diesem Neustart angezeigt werden soll. Werte von **2**, **4**, **8**, **12** und **24** Stunden werden unterstützt.  
  
  Wenn Sie den Standardwert löschen, wird diese Einstellung *nicht konfiguriert*.  

- **Benutzer vor erforderlichem automatischen Neustart mit permanenter Erinnerung erinnern (Minuten)**  
  **Standard**: 15  
  Windows Update CSP: [Update/scheduleimminentrestartwarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning)  

  Geben Sie an, wie lange vor einem automatischen Neustart eine nicht ablehnbare Warnung zu diesem Neustart für einen Gerätebenutzer angezeigt werden soll. Werte von **15**, **30** und **60** Minuten werden unterstützt.  

  Wenn Sie den Standardwert löschen, wird diese Einstellung *nicht konfiguriert*.  

- **Update-Benachrichtigungsstufe ändern**  
  **Standardeinstellung:** Windows Update-Standardbenachrichtigungen verwenden  
  Windows Update CSP: [Update/updatenotificationlevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)
  
  Geben Sie an, welche Art von Windows Update-Benachrichtigungen Benutzern angezeigt werden sollen. Diese Einstellung steuert nicht, wie und wann Updates heruntergeladen und installiert werden.  

  Unterstützte Optionen:
  - **Nicht konfiguriert**
  - **Windows Update-Standardbenachrichtigungen verwenden**
  - **Alle Benachrichtigungen deaktivieren, ausgenommen Neustart Warnungen**
  - **Deaktivieren Sie alle Benachrichtigungen, einschließlich Neustart Warnungen.**  

- **Benutzer Neustart erlauben (erzwungener Neustart)**  
  **Standardeinstellung:** Nicht konfiguriert  
  > [!IMPORTANT]  
  > Es wird nicht mehr empfohlen, die Einstellungen für den *Neustart* von zu verwenden. Verwenden Sie stattdessen die neuen Einstellungen für den *Stichtag* , die die Einstellungen für den neuen *Neustart* ablösen. InTune unterstützt in einem zukünftigen Update die [Unterstützung für die Einstellungen für den *Neustart* ](whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-) .

  Ein unterstützter Neustart wird für Windows 10, Version 1803 und höher, unterstützt. 

  > [!NOTE]  
  > Windows 10 (Version 1809) führt zusätzliche erzwungene Neustarteinstellungen ein, die es ermöglichen, separate Einstellungen für Feature- und Qualitätsupdates anzuwenden. Die von Intune verwalteten Einstellungen gelten jedoch nicht separat für die verschiedenen Updatetypen. Stattdessen wendet Intune die gleichen Werte auf Feature- und Qualitätsupdates an.  
  
  - **Nicht konfiguriert**  
  - **Erforderlich**: Legen Sie *Erforderlich* fest, um die Verwendung der Optionen für erzwungenen Neustart für Windows 10-Updates zu aktivieren. Diese Optionen ermöglichen dem Benutzer eines Geräts die Verwaltung des Zeitpunkts für den Neustart eines Geräts nach der Installation eines Updates, das einen Neustart erfordert.  

  Weitere Informationen zu dieser Option finden Sie unter [Erzwungener Neustart](https://docs.microsoft.com/windows/deployment/update/waas-restart#engaged-restart) in der Windows 10-Dokumentation zur Bereitstellung von Updates.  

  Die folgenden Einstellungen werden zum Steuern verwendet, wann erzwungene Neustartaktionen auftreten.  

  - **Benutzer nach automatischem Neustart auf erzwungenen Neustart umstellen (Tage)**  
    **Standard**: nicht konfiguriert Windows Update CSP: [Update/engagedrestarttransitionschedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
    
    Geben Sie mit einem Wert von **2** bis **30** Tagen an, wie lange es nach der Installation der Updates dauert, bis das Gerät in das erzwungene Neustartverhalten wechselt. Nach der konfigurierten Anzahl von Tagen erhalten Benutzer eine Aufforderung zum Neustarten des Geräts.  

  - **Erneut erinnern bei erzwungener Neustarterinnerung (Tage)**  
    **Standardeinstellung:** Nicht konfiguriert    
    Windows Update CSP: [Update/engagedrestartnoozeschedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
    
    Geben Sie einen Wert zwischen **1** und **3** an, um zu bestimmen, wie lange eine Neustart Aufforderung wieder zurückgesetzt werden kann.  Nach Ablauf des Zeitraums für erneutes Erinnern wird die Neustartaufforderung erneut angeboten. Der Benutzer kann die Erinnerung weiterhin auf „Erneut erinnern“ festlegen, bis der Stichtag für die Installation erreicht ist.  

  - **Stichtag für ausstehende Neustarts festlegen (Tage)**  
    **Standardeinstellung:** Nicht konfiguriert  
    Windows Update CSP: [Update/engagedrestartstichtag](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  
    Geben Sie einen Wert von **2** bis **30** Tagen als maximale Anzahl der Tage an, die nach Beginn des erzwungenen Neustartverhaltens gewartet wird, bis ein Gerät einen erforderlichen Neustart erzwingt. Dieser Neustart fordert Benutzer zum Speichern ihrer Arbeit auf.

- **Frist Einstellungen verwenden**  
  **Standardeinstellung:** Nicht konfiguriert  
  > [!IMPORTANT]  
  > Ab dem August-Update für InTune empfiehlt es sich, die folgenden Einstellungen zu verwenden, die die Einstellungen des festgesetzten Neustarts ablösen. InTune unterstützt in einem zukünftigen Update von InTune die [Unterstützung für die Einstellungen für den *Neustart* ](whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-) .  

  Ermöglicht Benutzern die Verwendung von Stichtag Einstellungen.  

  - **Nicht konfiguriert**
  - **Zulassen**

  Wenn diese Option auf *zulassen*festgelegt ist, können Sie die folgenden Einstellungen für Stichtage konfigurieren:

  - **Stichtag für Featureupdates**  
    **Standardeinstellung**: 7  
    Windows Update CSP: [Update/Konfiguration redeadlineforfeatureupdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)  

    Gibt die Anzahl von Tagen an, die ein Benutzer vor der Installation von Featureupdates auf den Geräten automatisch (2-30) hat.

  - **Stichtag für Qualitäts Updates**  
    **Standardeinstellung**: 7  
    Windows Update CSP: [Update/Konfiguration redeadlineforqualityupdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)

    Gibt die Anzahl von Tagen an, die ein Benutzer vor der Installation von Qualitäts Updates auf den Geräten automatisch (2-30) hat.

  - **Karenzzeit**  
    **Standard**Wert: 2 Windows Update CSP: [Update/Konfiguration redeadlinegraceperiod]( https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod)

    Gibt eine Mindestanzahl von Tagen nach dem Stichtag an, bis die Neustarts automatisch erfolgen (0-7).

  - **Automatischer Neustart vor Stichtag**  
    **Standard**: Ja Windows Update CSP: [Update/Konfiguration redeadlinenoautoreboot](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinenoautoreboot)

    Gibt an, ob das Gerät vor Stichtag automatisch neu gestartet werden soll.
    - **Ja**
    - **No**




### <a name="delivery-optimization-download-mode"></a>Downloadmodus für die Übermittlungsoptimierung  

Die Übermittlungsoptimierung wird nicht mehr als Teil eines Windows 10-Updaterings unter „Softwareupdates“ konfiguriert. Sie wird nun über die Gerätekonfiguration festgelegt. Frühere Konfigurationen bleiben jedoch in der Konsole verfügbar. Sie können diese vorherigen Konfigurationen entfernen, indem Sie sie auf *Nicht konfiguriert* festlegen. Anderweitig können sie jedoch nicht geändert werden. 

Um Konflikte zwischen neuer und alter Richtlinie zu vermeiden, lesen Sie [Wechsel von vorhandenen Updateringen zur Übermittlungsoptimierung](delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization) und verschieben Ihre Einstellungen dann in ein Profil für die Übermittlungsoptimierung.
