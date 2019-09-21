---
title: Problembehandlung bei der App-Installation
titleSuffix: Microsoft Intune
description: Weitere Informationen zur Problembehandlung bei der App-Installation mithilfe des Microsoft Intune-Bereichs zur Problembehandlung
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/04/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 850c7a28c4df1638e9f635713695dcf2e914ffce
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166930"
---
# <a name="troubleshoot-app-installation-issues"></a>Problembehandlung bei der App-Installation

Auf Geräten, die mit Microsoft Intune MDM verwaltet werden, können App-Installationen manchmal fehlschlagen. In diesen Fällen kann es schwierig sein, die Fehlerursache zu verstehen oder das Problem zu beheben. Microsoft Intune stellt Details zu fehlgeschlagenen App-Installationen bereit. So können Helpdeskmitarbeiter und Intune-Administratoren App-Informationen nutzen, um Benutzern bei ihren Anliegen zu helfen. Der Intune-Bereich „Problembehandlung“ stellt Fehlerdetails bereit, einschließlich Informationen zu verwalteten Apps auf Benutzergeräten. Details zum End-to-End-Lebenszyklus einer App finden Sie unter dem jeweiligen Gerät im Bereich **Verwaltete Apps**. Sie können Installationsprobleme ansehen, z. B. wann die App erstellt, geändert, ausgerichtet und auf einem Gerät bereitgestellt wurde. 

## <a name="app-troubleshooting-details"></a>Details zur Problembehandlung von Apps

Intune stellt anhand von Apps, die auf dem jeweiligen Benutzergerät installiert sind, App-Informationen zur Problembehandlung bereit.

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Wählen Sie im Bereich **Intune** die Option **Problembehandlung** aus.
4. Klicken Sie auf **Benutzer auswählen**, um einen Benutzer auszuwählen, für den ein Problem behoben werden muss. Der Bereich **Benutzer auswählen** wird angezeigt.
5. Wählen Sie einen Benutzer aus, indem Sie den Namen oder die E-Mail-Adresse eingeben. Klicken Sie unten im Bereich auf **Auswählen**. Die Informationen zur Problembehandlung für den Benutzer werden im Bereich **Problembehandlung** angezeigt. 
6. Wählen Sie aus der Liste **Geräte** ein Gerät zur Problembehandlung aus.
    ![Intune Bereich zur Problembehandlung](media/troubleshoot-app-install-01.png)
7. Wählen Sie im ausgewählten Gerätebereich **Verwaltete Apps** aus. Eine Liste der verwalteten Apps wird angezeigt.
    ![Details zu einem bestimmten Gerät, das von Intune verwaltet wird.](media/troubleshoot-app-install-02.png)
8. Wählen Sie aus der Liste eine App aus. Der **Installationsstatus** zeigt an, ob ein Fehler aufgetreten ist.
    ![Eine ausgewählte App, die Details zur fehlgeschlagenen Installation anzeigt.](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > Eine App kann mehreren Gruppen zugewiesen werden – jedoch mit unterschiedlichen beabsichtigten Aktionen (Absichten) für die App. Beispielsweise zeigt eine aufgelöste Absicht für eine App **Ausgeschlossen** an, wenn die App bei der App-Zuweisung für einen Benutzer ausgeschlossen wird. Weitere Informationen finden Sie unter [Auflösung von Konflikten zwischen App-Absichten](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Wenn ein Installationsfehler bei einer erforderlichen App auftritt, können entweder Sie oder Ihr Helpdesk das Gerät synchronisieren und die App-Installation erneut versuchen.

Die Details zum App-Installationsfehler weisen auf das Problem hin. Anhand dieser Informationen können Sie ermitteln, welche Maßnahmen sich am besten zur Problembehandlung eignen. Weitere Informationen zur Problembehandlung bei der App-Installation finden Sie unter [App-Installationsfehler](troubleshoot-app-install.md#app-installation-errors).

> [!Note]  
> Sie können auch auf den Bereich **Problembehandlung** zugreifen, indem Sie in Ihrem Browser zu [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) navigieren.

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>Die Benutzergruppen gezielte App-Installation erreicht das Gerät nicht.
Die folgenden Aktionen sollten bei der Installation von apps in Erwägung gezogen werden:
- Wenn die APP nicht im Unternehmensportal angezeigt wird, stellen Sie sicher, dass die APP mit der **verfügbaren Absicht bereit** gestellt wird und dass der Benutzer mit dem Gerätetyp, der von der App unterstützt wird, auf die Unternehmensportal zugreift
- Bei Windows BYOD-Geräten muss der Benutzer dem Gerät ein Geschäftskonto hinzufügen.
- Überprüfen Sie, ob der Benutzer über das Aad-Geräte Limit verfügt:
  1. Navigieren Sie zu [Azure Active Directory Geräteeinstellungen](https://portal.azure.com/#blade/Microsoft_AAD_IAM/DevicesMenuBlade/DeviceSettings/menuId).
  2. Notieren Sie sich den Wert für maximale Anzahl von **Geräten pro Benutzer**.
  3. Navigieren Sie zu [Azure Active Directory Benutzer](https://portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/AllUsers).
  4. Wählen Sie den betroffenen Benutzer aus, und klicken Sie auf **Geräte**
  5. Wenn sich der Benutzer über dem festgelegten Grenzwert befindet, löschen Sie veraltete Datensätze, die nicht mehr benötigt werden.
- Für IOS-DEP-Geräte müssen Sie sicherstellen, dass der Benutzer im Blatt mit der InTune-Geräte Übersicht als **von Benutzer angemeldet** aufgeführt wird. Wenn na angezeigt wird, stellen Sie eine Konfigurationsrichtlinie für die Intune-Unternehmensportal bereit. Weitere Informationen finden Sie unter [Konfigurieren der Unternehmensportal-App](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Problembehandlung bei der Installation von Win32-Apps

Wählen Sie die Win32-App aus, die über die Intune-Verwaltungserweiterung bereitgestellt wurde. Wenn die Installation Ihrer Win32-App fehlschlägt, können Sie die Option **Protokolle sammeln** auswählen. 

> [!IMPORTANT]
> Die Option **Protokolle sammeln** wird nicht aktiviert, wenn die Win32-App erfolgreich auf dem Gerät installiert wurde.<p>Bevor Sie Protokollinformationen für eine Win32-App sammeln können, muss die Intune-Verwaltungserweiterung auf dem Windows-Client installiert werden. Die Intune-Verwaltungserweiterung wird installiert, wenn ein PowerShell-Skript oder eine Win32-App für eine Benutzer- oder Gerätesicherheitsgruppe bereitgestellt wird. Weitere Informationen finden Sie unter [Intune-Verwaltungserweiterung – Voraussetzungen](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Sammeln von Protokollen

Wenn Sie Ihre Win32-App-Installationsprotokolle sammeln möchten, führen Sie zunächst die Schritte aus, die im Abschnitt [Details zur Problembehandlung von Apps](troubleshoot-app-install.md#app-troubleshooting-details) beschrieben sind. Fahren Sie anschließend mit den folgenden Schritten fort:

1. Klicken Sie auf dem Blatt **Installationsdetails** auf **Protokolle sammeln**.

    <image alt="Win32 app installation details - Collect log option" src="media/troubleshoot-app-install-04.png" width="500" />

2. Geben Sie Dateipfade mit Protokolldateinamen an, um die Protokolldateierfassung zu starten, und klicken Sie auf **OK**.
    
    > [!NOTE]
    > Die Protokollsammlung dauert weniger als zwei Stunden. Unterstützte Dateitypen: *.log, .txt, .dmp, .cab, .zip, .xml, .evtx und .evtl*. Maximal 25 Dateipfade sind zulässig.

3. Nachdem die Protokolldateien gesammelt wurden, können Sie auf den Link **Protokolle** klicken, um die Protokolldateien herunterzuladen.

    <image alt="Win32 app log details - Download logs" src="media/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Eine Benachrichtigung über den Erfolg der App-Protokollsammlung wird angezeigt.

#### <a name="win32-log-collection-requirements"></a>Anforderungen für die Sammlung von Win32-Protokollen

Es gelten besondere Anforderungen, die beim Sammeln von Protokolldateien zu beachten sind:

- Sie müssen den vollständigen Protokolldateipfad angeben. 
- Sie können für die Protokollsammlung Umgebungsvariablen angeben, wie z.B. die folgenden:<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP%*
- Nur exakte Dateierweiterungen sind zulässig wie z.B.:<br>
  *.log, .txt, .dmp, .cab, .zip, .xml*
- Es können maximal 60 MB oder 25 Dateien hochgeladen werden, je nachdem, was zuerst der Fall ist. 
- Die Sammlung von Win32-App-Installationsprotokollen ist für Apps aktiviert, die die App-Zuweisungsabsicht (Erforderlich, Verfügbar und Deinstallieren) erfüllen.
- Gespeicherte Protokolle werden verschlüsselt, um alle personenbezogenen Informationen zu schützen, die in den Protokollen enthalten sind.
- Wenn Sie Supporttickets für Win32-App-Fehler öffnen, fügen Sie die zugehörigen Fehlerprotokolle wie vorstehend beschrieben hinzu.

## <a name="app-installation-errors"></a>App-Installationsfehler

Die folgenden Fehlermeldungen und Beschreibungen bieten weitere Informationen zu Installationsfehlern unter Android und iOS. 

### <a name="android-errors"></a>Android-Fehler

In diesem Abschnitt werden sowohl Geräte Administrator (da) als auch Samsung Knox-Registrierung erwähnt. Weitere Informationen finden Sie unter Registrierung von [Android-Geräte Administratoren](android-enroll-device-administrator.md) und [Automatisches Registrieren von Android-Geräten mithilfe der Knox Mobile-Registrierung von Samsung](android-samsung-knox-mobile-enroll.md). 

| Fehlermeldung/-code | Beschreibung |
|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Fehler beim Installieren der App. (0xC7D14FB5) | Diese Fehlermeldung wird angezeigt, wenn Intune die Grundursache des Fehlers bei der App-Installation unter Android nicht ermitteln kann. Während des Fehlers wurden von Android keine Informationen zur Verfügung gestellt. Dieser Fehler wird zurückgegeben, wenn der APK-Download erfolgreich war, die App jedoch nicht installiert werden konnte. Dieser Fehler wird häufig durch eine fehlerhafte APK-Datei verursacht, die nicht auf dem Gerät installiert werden kann. Möglicherweise wird die App-Installation auch aus Sicherheitsgründen durch Google Play Protect blockiert. Es kann auch zu diesem Fehler kommen, wenn ein Gerät die App nicht unterstützt. Dies ist etwa der Fall, wenn die App die API-Version 21 oder höher erfordert und das Gerät derzeit über die API-Version 19 verfügt. Intune gibt diese Fehlermeldung sowohl für DA- als auch für KNOX-Geräte zurück. Auch wenn möglicherweise eine Benachrichtigung ausgegeben wird, dass Benutzer den Versuch durch Klicken wiederholen können, ist eine Fortsetzung des Vorgangs bei einem APK-Fehler nicht möglich. Handelt es sich um eine verfügbare App, kann die Benachrichtigung geschlossen werden. Wenn die App jedoch erforderlich ist, kann die Benachrichtigung nicht verworfen werden. |
| Die App-Installation wurde abgebrochen, weil die Installationsdatei (APK) nach dem Download, aber vor der Installation gelöscht wurde. (0xC7D14FBA) | Der Download der APK-Datei war erfolgreich, aber die Datei wurde vor der Installation der App durch den Benutzer vom Gerät entfernt. Dies kann der Fall sein, wenn zwischen dem Herunterladen und dem Installieren ein großer Zeitabstand liegt. Beispielsweise hat der Benutzer die ursprüngliche Installation abgebrochen, gewartet und dann auf die Benachrichtigung geklickt, um es noch einmal zu versuchen. Diese Fehlermeldung wird nur für DA-Szenarien zurückgegeben. Bei KNOX-Szenarien kann die Ausführung im Hintergrund erfolgen. Es wird eine Benachrichtigung zum Wiederholen des Vorgangs angezeigt, damit der Benutzer zustimmen kann, anstatt den Vorgang abzubrechen. Handelt es sich um eine verfügbare App, kann die Benachrichtigung geschlossen werden. Wenn die App jedoch erforderlich ist, kann die Benachrichtigung nicht verworfen werden. |
| Die App-Installation wurde abgebrochen, weil der Prozess während der Installation neu gestartet wurde. (0xC7D14FBB) | Das Gerät wurde während des APK-Installationsprozesses neu gestartet, wodurch die Installation abgebrochen wurde. Diese Fehlermeldung wird sowohl für DA- als auch für KNOX-Geräte zurückgegeben. Intune zeigt eine Benachrichtigung an, auf die Benutzer klicken können, um den Vorgang zu wiederholen. Handelt es sich um eine verfügbare App, kann die Benachrichtigung geschlossen werden. Wenn die App jedoch erforderlich ist, kann die Benachrichtigung nicht verworfen werden. |
| Die Anwendung wurde nach erfolgreicher Installation nicht erkannt. (0x87D1041C) | Die App wurde vom Benutzer explizit deinstalliert. Diese Fehlermeldung wird nicht vom Client zurückgegeben. Der Fehler wird verursacht, wenn die App zu einem bestimmten Zeitpunkt installiert war, aber dann vom Benutzer deinstalliert wurde. Dieser Fehler sollte nur bei erforderlichen Apps auftreten. Benutzer können nicht benötigte Apps deinstallieren. Dieser Fehler kann nur bei DA auftreten. KNOX blockiert die Deinstallation von verwalteten Apps. Bei der nächsten Synchronisierung wird die Benutzerbenachrichtigung zur Installation auf dem Gerät erneut angezeigt. Der Benutzer kann die Benachrichtigung ignorieren. Dieser Fehler wird so lange gemeldet, bis der Benutzer die App installiert. |
| Der Download war aufgrund eines unbekannten Fehlers nicht erfolgreich. (0xC7D14FB2) | Dieser Fehler tritt auf, wenn das Herunterladen nicht erfolgreich war. Häufig wird dieser Fehler durch Probleme mit dem WLAN oder zu langsamen Verbindungen verursacht. Diese Fehlermeldung wird nur für DA-Szenarien zurückgegeben. Bei KNOX-Szenarien wird der Benutzer nicht zur Installation aufgefordert. Diese kann im Hintergrund erfolgen. Intune zeigt eine Benachrichtigung an, auf die Benutzer klicken können, um den Vorgang zu wiederholen. Handelt es sich um eine verfügbare App, kann die Benachrichtigung geschlossen werden. Wenn die App jedoch erforderlich ist, kann die Benachrichtigung nicht verworfen werden. |
| Der Download war aufgrund eines unbekannten Fehlers nicht erfolgreich. Die Anwendung der Richtlinie wird bei der nächsten Gerätesynchronisierung wiederholt. (0xC7D15078) | Dieser Fehler tritt auf, wenn das Herunterladen nicht erfolgreich war. Häufig wird dieser Fehler durch Probleme mit dem WLAN oder zu langsamen Verbindungen verursacht. Diese Fehlermeldung wird nur für DA-Szenarien zurückgegeben. Bei KNOX-Szenarien wird der Benutzer nicht zur Installation aufgefordert. Diese kann im Hintergrund erfolgen. |
| Der Benutzer hat die App-Installation abgebrochen. (0xC7D14FB1) | Die App wurde vom Benutzer explizit deinstalliert. Diese Fehlermeldung wird zurückgegeben, wenn die Installation durch das Android-Betriebssystem vom Benutzer abgebrochen wurde. Als die Eingabeaufforderung zur Betriebssysteminstallation angezeigt wurde, hat der Benutzer auf die Schaltfläche „Abbrechen“ geklickt oder die Eingabeaufforderung geschlossen. Diese Fehlermeldung wird nur für DA-Szenarien zurückgegeben. Bei KNOX-Szenarien wird der Benutzer nicht zur Installation aufgefordert. Diese kann im Hintergrund erfolgen. Intune zeigt eine Benachrichtigung an, auf die Benutzer klicken können, um den Vorgang zu wiederholen. Handelt es sich um eine verfügbare App, kann die Benachrichtigung geschlossen werden. Wenn die App jedoch erforderlich ist, kann die Benachrichtigung nicht verworfen werden. Bitten Sie den Benutzer, die Installation nicht abzubrechen. |
| Der Prozess zum Herunterladen der Datei wurde unerwartet beendet. (0xC7D15015) | Der Download wurde vom Betriebssystem beendet, bevor dieser abgeschlossen war. Dieser Fehler kann auftreten, wenn das Gerät eine niedrige Akkukapazität aufweist oder der Download zu lange dauert. Diese Fehlermeldung wird nur für DA-Szenarien zurückgegeben. Bei KNOX-Szenarien wird der Benutzer nicht zur Installation aufgefordert. Diese kann im Hintergrund erfolgen. Intune zeigt eine Benachrichtigung an, auf die Benutzer klicken können, um den Vorgang zu wiederholen. Handelt es sich um eine verfügbare App, kann die Benachrichtigung geschlossen werden. Wenn die App jedoch erforderlich ist, kann die Benachrichtigung nicht verworfen werden. Stellen Sie sicher, dass das Gerät über eine zuverlässige Netzwerkverbindung verfügt.  |
| Der Dienst zum Herunterladen der Datei wurde unerwartet beendet. Die Anwendung der Richtlinie wird bei der nächsten Gerätesynchronisierung wiederholt. (0xC7D1507C) | Der Download wurde vom Betriebssystem beendet, bevor dieser abgeschlossen war. Dieser Fehler kann auftreten, wenn das Gerät eine niedrige Akkukapazität aufweist oder der Download zu lange dauert. Diese Fehlermeldung wird nur für DA-Szenarien zurückgegeben. Bei KNOX-Szenarien wird der Benutzer nicht zur Installation aufgefordert. Diese kann im Hintergrund erfolgen. Synchronisieren Sie das Gerät manuell, oder warten Sie 24 Stunden, und überprüfen Sie den Status. |
| Fehler beim Deinstallieren der app. (0xc7d14b8) | Dieser Fehler ist ein generischer Deinstallations Fehler. Das Betriebssystem hat nicht angegeben, warum die APP nicht deinstalliert werden konnte. Einige admin-Apps können nicht einfach deinstalliert werden. Stellen Sie sicher, dass die APP manuell deinstalliert werden kann, und erfassen Sie die Unternehmensportal Protokolle, wenn die Deinstallation fehlschlägt. |
| Die APK-Datei für die APP-Installation, die für das Upgrade verwendet wird, entspricht nicht der Signatur für die aktuelle App auf dem Gerät. (0xc7d14b7) | Das Android-Betriebssystem unterliegt der Einschränkung, dass das Signaturzertifikat für die Upgradeversion exakt dem Zertifikat entspricht, das zum Signieren der vorhandenen Version verwendet wurde. Wenn der Entwickler das gleiche Zertifikat nicht zum Signieren der neuen Version verwenden kann, müssen Sie die vorhandene APP deinstallieren und die neue APP erneut bereitstellen, anstatt die vorhandene APP zu aktualisieren. |
| Der Benutzer hat die App-Installation abgebrochen. (0xc7d14b9) | Informieren Sie den Benutzer, dass die bereitgestellte InTune-App akzeptiert wird, und installieren Sie die APP, wenn Sie |
| Die App-Deinstallation wurde abgebrochen, weil der Prozess während der Installation neu gestartet wurde. (0xc7d14bbc) | Der APP-Installationsprozess wurde vom Betriebssystem beendet, oder das Gerät wurde neu gestartet. Wiederholen Sie die Installations-und Sammlungs Unternehmensportal Protokolle, wenn dieser Fehler erneut auftritt. |
| Die APK-Datei für die APP-Installation kann nicht installiert werden, da Sie nicht signiert wurde. (0xc7d14b6) | Standardmäßig erfordert Android OS, dass apps signiert sind. Stellen Sie sicher, dass die APP vor der Bereitstellung signiert |

### <a name="ios-errors"></a>iOS-Fehler

| Fehlermeldung/-code | Beschreibung/Tipps zur Problembehandlung |
|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (0x87D12906) | Der Apple-MDM-Agent hat einen Fehler beim Installationsbefehl gemeldet. |
| (0x87D1313C) | Die Netzwerkverbindung wurde unterbrochen, während die aktualisierte URL des Downloaddiensts an das Gerät gesendet wurde. Insbesondere wurde kein Server mit dem angegebenen Hostnamen gefunden. |
| Das iOS-Gerät ist derzeit ausgelastet. (0x87D11388) | Das iOS-Gerät war ausgelastet, was zu einem Fehler führte. Das Gerät wurde gesperrt. Der Benutzer muss das Gerät Entsperren, um die APP zu installieren. |
| Fehler bei der App-Installation. (0x87D13B64) | Es ist ein Fehler bei der App-Installation aufgetreten. Zur Behebung dieses Fehlers werden Protokolle der iOS-Konsole benötigt. |
| Die App wird verwaltet, ist jedoch abgelaufen oder wurde vom Benutzer entfernt. (0x87D13B66) | Der Benutzer hat die APP explizit deinstalliert, oder die APP ist abgelaufen, konnte jedoch nicht heruntergeladen werden, oder die APP-Erkennung entspricht nicht der Antwort des Geräts. Darüber hinaus kann dieser Fehler aufgrund eines Plattformfehlers von iOS 9.2.2 auftreten. |
| Die App ist für die Installation geplant, benötigt jedoch einen Einlösecode, um die Transaktion abschließen zu können. (0x87D13B60) | Dieser Fehler tritt in der Regel bei iOS Store-Apps auf, bei denen es sich um bezahlte Apps handelt. |
| Die Anwendung wurde nach erfolgreicher Installation nicht erkannt. (0x87D1041C) | Die App-Erkennung stimmte nicht mit der Antwort des Geräts überein. |
| Der Benutzer hat die angebotene Installation der App abgelehnt. (0x87D13B62) | Während der ersten App-Installation hat der Benutzer auf „Abbrechen“ geklickt. Bitten Sie den Benutzer, die Installations Anforderung beim nächsten Mal zu akzeptieren. |
| Der Benutzer hat das angebotene Update für die App abgelehnt. (0x87D13B63) | Der Benutzer hat während des Updates auf „Abbrechen“ geklickt. Stellen Sie nach Bedarf bereit, oder informieren Sie den Benutzer, dass er die upgradeaufforderung annimmt |
| Unbekannter Fehler (0x87D103E8) | Bei der App-Installation ist ein unbekannter Fehler aufgetreten. Dieser Fehler ergibt sich, wenn kein anderer Fehler aufgetreten ist. |
| VPP-Apps können nur auf einem freigegebenen iPad installiert werden (-2016330861). | Die Apps müssen über das Apple Volume Purchase Program bezogen werden, damit sie auf einem freigegebenen iPad installiert werden können. |
| Wenn der App Store deaktiviert ist, können keine Apps installiert werden (-2016330860). | Der App Store muss aktiviert sein, damit der Benutzer die App installieren kann. |
| Es wurde keine VPP-Lizenz für die App gefunden (-2016330859). | Versuchen Sie, die App-Lizenz zu widerrufen und neu zuzuweisen. |
| System-Apps können nicht mit Ihrem MDM-Anbieter installiert werden (-2016330858). | Die Installation von Apps, die vom iOS-Betriebssystem vorinstalliert wurden, wird nicht unterstützt. |
| Wenn sich das Gerät im Modus für verlorene Geräte befindet, können keine Apps installiert werden (-2016330857). | Im Modus für verlorene Geräte wird jegliche Nutzung des Geräts blockiert. Deaktivieren Sie den Modus für verlorene Geräte, um Apps installieren zu können. |
| Wenn sich das Gerät im Kioskmodus befindet, können keine Apps installiert werden (-2016330856). | Versuchen Sie, dieses Gerät zu einer Ausschlussgruppe für die Konfigurationsrichtlinie für den Kioskmodus hinzuzufügen, um Apps zu installieren. |
| Auf diesem Gerät können keine 32-Bit-Apps installiert werden (-2016330852). | Das Gerät unterstützt nicht die Installation von 32-Bit-Apps. Versuchen Sie, die 64-Bit-Version der App bereitzustellen. |
| Der Benutzer muss sich beim App Store anmelden (-2016330855). | Der Benutzer muss sich beim App Store anmelden, bevor die App installiert werden kann. |
| Unbekanntes Problem. Wiederholen Sie den Vorgang (-2016330854). | Die Installation der App ist aus einem unbekannten Grund fehlgeschlagen. Versuchen Sie es später erneut. |
| Fehler bei der App-Installation. Der Versuch wird von Intune bei der nächsten Gerätesynchronisierung wiederholt (-2016330853). | Bei der App-Installation ist ein Gerätefehler aufgetreten. Synchronisieren Sie das Gerät, und versuchen Sie, die App erneut zu installieren. |
| Fehler bei der Lizenz Zuweisung mit dem Apple-Fehler "keine VPP-Lizenzen verbleiben" (0x87d13b7e). | Dieses Verhalten ist entwurfsbedingt. Um dies zu beheben, erwerben Sie zusätzliche VPP-Lizenzen, oder fordern Sie Lizenzen von Benutzern, die nicht mehr als Ziel |
| Fehler bei der App-Installation 12024: Unbekannte Ursache. (0x87d13b6e) | Apple hat uns nicht genügend Informationen gegeben, um zu ermitteln, warum die Installation fehlgeschlagen ist. Nichts zu melden. |
| Die erforderliche App-Konfigurationsrichtlinie ist nicht vorhanden. Stellen Sie sicher, dass die Richtlinie für dieselben Gruppen gilt (0x87d13b7f) | Die APP erfordert die APP-Konfiguration, aber keine app-Konfiguration. Der Administrator sollte sicherstellen, dass für die Gruppen, für die die APP bestimmt ist, auch die erforderliche App-Konfiguration für die Gruppen bestimmt ist. |
| Die Geräte-VPP-Lizenzierung gilt nur für IOS 9.0 und höher. (0x87d13b69) | Aktualisieren Sie betroffene IOS-Geräte auf IOS 9.0 und höher. |
| Die Anwendung ist auf dem Gerät installiert, aber nicht verwaltet. (0x87d13b8f) | Dieser Fehler tritt nur bei Branchen-apps auf. Die APP wurde außerhalb von InTune installiert. Um diesen Fehler zu beheben, deinstallieren Sie die APP auf dem Gerät. Bei der nächsten Geräte Synchronisierung sollte das Gerät die APP von InTune installieren. |
| Benutzer hat die APP-Verwaltung abgelehnt (0x87d13b68) | Bitten Sie den Benutzer, die APP-Verwaltung zu akzeptieren. |
| Unbekannter Fehler. (0x87d1279d) | Dieser Fehler tritt bei IOS Store-Apps auf, aber das Fehlerszenario ist unbekannt. |
| Die neueste Version der APP konnte nicht von einer früheren Version aktualisiert werden. (0x87d13b9d) | Diese Fehlermeldung wird angezeigt, wenn die APP installiert und verwaltet wird, aber mit der falschen Version auf dem Gerät. Diese Situation umfasst auch, wenn ein Gerät einen Befehl zum Aktualisieren einer APP erhalten hat, die neue Version jedoch noch nicht installiert und zurückgegeben wurde. Dieser Fehler wird für den ersten Check-in eines Geräts gemeldet, nachdem das Upgrade bereitgestellt wurde, und tritt auf, bis das Gerät meldet, dass die neue Version installiert ist oder aufgrund eines anderen Fehlers fehlschlägt.  |


### <a name="other-installation-errors"></a>Andere Installationsfehler

|  Fehlermeldung/-code  |  Beschreibung  |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  0x80073CFF, 0x80CF201C (Clientfehler)  |  Zur Installation der Anwendung müssen Sie über ein zum Querladen fähiges System verfügen. Stellen Sie sicher, dass das App-Paket mit einer vertrauenswürdigen Signatur signiert und auf einem zur Domäne gehörenden Gerät mit aktivierter Richtlinie **AllowAllTrustedApps** oder auf einem Gerät mit einer Windows-Lizenz für das Querladen und aktivierter Richtlinie **AllowAllTrustedApps** installiert ist. Weitere Informationen finden Sie unter [Problembehandlung beim Packen, Bereitstellen und Abfragen von Windows Store-Apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).   |
|  0x80073CF0  |  Das Paket konnte nicht geöffnet werden. Mögliche Ursachen:<ul><li> Das Paket ist nicht signiert.</li><li> Der Namen des Herausgebers stimmt nicht mit dem Signaturzertifikat des Antragstellers überein.</li></ul> Informationen dazu finden Sie im Ereignisprotokoll **AppxPackagingOM**. Weitere Informationen finden Sie unter [Problembehandlung beim Packen, Bereitstellen und Abfragen von Windows Store-Apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x80073CF3  |  Fehler bei Updates, Abhängigkeiten oder Konfliktüberprüfung des Pakets. Mögliche Ursachen:<ul><li> Das eingehende Paket ist mit einem installierten Paket nicht vereinbar.</li><li> Eine angegebene Paketabhängigkeit wurde nicht gefunden.</li><li> Das Paket unterstützt nicht die richtige Prozessorarchitektur.</li></ul> Informationen dazu finden Sie im Ereignisprotokoll **AppXDeployment-Server**. Weitere Informationen finden Sie unter [Problembehandlung beim Packen, Bereitstellen und Abfragen von Windows Store-Apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x80073CFB  |  Das bereitgestellte Paket ist bereits installiert, und eine erneute Installation des Pakets wird blockiert. Dieser Fehler kann auftreten, wenn Sie ein Paket installieren, das nicht mit dem bereits installierten Paket identisch ist. Überprüfen Sie, ob die digitale Signatur auch Teil des Pakets ist. Wenn ein Paket erneut erstellt oder signiert wird, ist das Paket nicht mehr bitweise identisch mit dem zuvor installierten Paket. Es gibt zwei Möglichkeiten, diesen Fehler zu beheben:<ul><li> Erhöhen Sie die Versionsnummer der Anwendung, und erstellen und signieren Sie das Paket dann erneut.</li><li> Entfernen Sie das alte Paket für jeden Benutzer des Systems, bevor Sie das neue Paket installieren.</li></ul> Weitere Informationen finden Sie unter [Problembehandlung beim Packen, Bereitstellen und Abfragen von Windows Store-Apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x87D1041C  |  Die Anwendung wurde erfolgreich installiert, wird jedoch nicht erkannt. Die App wurde erfolgreich von Intune bereitgestellt und später deinstalliert. Für das Deinstallieren der App können folgende Gründe vorliegen:<ul><li> Der Endbenutzer hat die App deinstalliert.</li><li> Die Identitätsinformationen im Paket stimmen nicht mit Informationen im Gerätebericht für fehlerhafte Apps überein.</li><li>Bei MSIs, die sich eigenständig aktualisieren, stimmt die Produktversion nicht mit den Informationen der App überein, nachdem diese außerhalb von Intune aktualisiert wurde.</li></ul> Weisen Sie den Benutzer an, die App aus dem Unternehmensportal neu zu installieren. Beachten Sie, dass erforderliche Apps beim nächsten Einchecken des Geräts automatisch neu installiert werden.  |
|  0x8000ffff  |  Unerwarteter Fehler bei der Installation. Weitere Informationen finden Sie in den Installations Protokollen.  |

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Problembehandlung bei Apps aus dem Microsoft Store

Mithilfe der Informationen im Artikel [Problembehandlung beim Packen, Bereitstellen und Abfragen von Microsoft Store-Apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) können Sie allgemeine Probleme beheben, die bei der Installation von Apps aus dem Microsoft Store (mit Intune oder mittels anderer Tools) auftreten können.

## <a name="app-troubleshooting-resources"></a>Ressourcen zur Problembehandlung für Apps
- [Bereitstellen von Visio und Project als Teil Ihrer Office Pro Plus-Bereitstellung](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Maßnahmen ergreifen, um sicherzustellen, dass msfb-Apps über die Intune-Installation unter Windows 10 1903](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Problembehandlung bei MSI-App-bereit Stellungen in Microsoft InTune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Bewährte Methoden für die Software Verteilung an den klassischen InTune-Windows-PC-Agent](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zur Intune-Problembehandlung finden Sie unter [Verwenden des Problembehandlungsportals zur Unterstützung von Benutzern Ihres Unternehmens](help-desk-operators.md). 
- Erfahren Sie mehr über bekannte Probleme in Microsoft Intune. Weitere Informationen finden Sie unter [InTune-Kunden Erfolg](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- Benötigen Sie zusätzliche Hilfe? Weitere Informationen finden Sie unter [Anfordern von Support für Microsoft Intune](get-support.md).
