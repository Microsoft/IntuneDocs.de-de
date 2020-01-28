---
title: Problembehandlung bei der App-Installation
titleSuffix: Microsoft Intune
description: Weitere Informationen zur Problembehandlung bei der App-Installation mithilfe des Microsoft Intune-Bereichs zur Problembehandlung
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/14/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0786174ebb90352fa1a41923f9cfce305aece49f
ms.sourcegitcommit: de663ef5f3e82e0d983899082a7f5b62c63f24ef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "75956316"
---
# <a name="troubleshoot-app-installation-issues"></a>Problembehandlung bei der App-Installation

Auf Geräten, die mit Microsoft Intune MDM verwaltet werden, können App-Installationen manchmal fehlschlagen. In diesen Fällen kann es schwierig sein, die Fehlerursache zu verstehen oder das Problem zu beheben. Microsoft Intune stellt Details zu fehlgeschlagenen App-Installationen bereit. So können Helpdeskmitarbeiter und Intune-Administratoren App-Informationen nutzen, um Benutzern bei ihren Anliegen zu helfen. Der Intune-Bereich „Problembehandlung“ stellt Fehlerdetails bereit, einschließlich Informationen zu verwalteten Apps auf Benutzergeräten. Details zum End-to-End-Lebenszyklus einer App finden Sie unter dem jeweiligen Gerät im Bereich **Verwaltete Apps**. Sie können Installationsprobleme ansehen, z. B. wann die App erstellt, geändert, ausgerichtet und auf einem Gerät bereitgestellt wurde. 

## <a name="app-troubleshooting-details"></a>Details zur Problembehandlung von Apps

Intune stellt anhand von Apps, die auf dem jeweiligen Benutzergerät installiert sind, App-Informationen zur Problembehandlung bereit.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
3. Wählen Sie **Support und Problembehandlung** aus.
4. Klicken Sie auf **Benutzer auswählen**, um einen Benutzer auszuwählen, für den ein Problem behoben werden muss. Der Bereich **Benutzer auswählen** wird angezeigt.
5. Wählen Sie einen Benutzer aus, indem Sie den Namen oder die E-Mail-Adresse eingeben. Klicken Sie unten im Bereich auf **Auswählen**. Die Informationen zur Problembehandlung für den Benutzer werden im Bereich **Problembehandlung** angezeigt. 
6. Wählen Sie aus der Liste **Geräte** ein Gerät zur Problembehandlung aus.
    ![Intune Bereich zur Problembehandlung](./media/troubleshoot-app-install/troubleshoot-app-install-01.png)
7. Wählen Sie im ausgewählten Gerätebereich **Verwaltete Apps** aus. Eine Liste der verwalteten Apps wird angezeigt.
    ![Details zu einem bestimmten Gerät, das von Intune verwaltet wird.](./media/troubleshoot-app-install/troubleshoot-app-install-02.png)
8. Wählen Sie aus der Liste eine App aus. Der **Installationsstatus** zeigt an, ob ein Fehler aufgetreten ist.
    ![Eine ausgewählte App, die Details zur fehlgeschlagenen Installation anzeigt.](./media/troubleshoot-app-install/troubleshoot-app-install-03.png)

    > [!Note]  
    > Eine App kann mehreren Gruppen zugewiesen werden – jedoch mit unterschiedlichen beabsichtigten Aktionen (Absichten) für die App. Beispielsweise zeigt eine aufgelöste Absicht für eine App **Ausgeschlossen** an, wenn die App bei der App-Zuweisung für einen Benutzer ausgeschlossen wird. Weitere Informationen finden Sie unter [Auflösung von Konflikten zwischen App-Absichten](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Wenn ein Installationsfehler bei einer erforderlichen App auftritt, können entweder Sie oder Ihr Helpdesk das Gerät synchronisieren und die App-Installation erneut versuchen.

Die Details zum App-Installationsfehler weisen auf das Problem hin. Anhand dieser Informationen können Sie ermitteln, welche Maßnahmen sich am besten zur Problembehandlung eignen. Weitere Informationen zur Problembehandlung bei der App-Installation finden Sie unter [Installationsfehler bei Android-Apps](troubleshoot-app-install.md#android-app-installation-errors) und [Installationsfehler bei iOS-Apps](troubleshoot-app-install.md#ios-app-installation-errors).

> [!Note]  
> Sie können auch auf den Bereich **Problembehandlung** zugreifen, indem Sie in Ihrem Browser zu [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting) navigieren.

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>App-Installation für die Benutzergruppe auf dem Gerät nicht möglich
Wenn es bei der Installation von Apps zu Problemen kommt, sollten Sie die folgenden Aktionen in Erwägung ziehen:
- Wenn die App nicht im Unternehmensportal angezeigt wird, überprüfen Sie mithilfe der Absicht **Verfügbar**, ob die App bereitgestellt ist und ob der Benutzer mit einem von dem Gerät unterstützten Gerätetyp auf das Unternehmensportal zugreift.
- Bei BYOD-Geräten von Windows müssen Benutzer auf dem Gerät ein Geschäftskonto hinzufügen.
- Überprüfen Sie, ob der Benutzer das Gerätelimit für AAD überschritten hat:
  1. Navigieren Sie in Azure Active Directory zu [Geräteeinstellungen](https://portal.azure.com/#pane/Microsoft_AAD_IAM/DevicesMenupane/DeviceSettings/menuId).
  2. Notieren Sie sich den Wert für die **Maximale Anzahl der Geräte pro Benutzer**.
  3. Navigieren Sie zu [Azure Active Directory-Benutzer](https://portal.azure.com/#pane/Microsoft_AAD_IAM/UsersManagementMenupane/AllUsers).
  4. Wählen Sie den betroffenen Benutzer aus, und klicken Sie auf **Geräte**.
  5. Wenn der Benutzer das festgelegte Limit überschritten hat, löschen Sie abgelaufene Einträge, die nicht mehr benötigt werden.
- Überprüfen Sie bei iOS-DEP-Geräten, ob der Benutzer im Geräteübersichtsbereich in Intune als **Vom Benutzer registriert** aufgeführt ist. Wenn „NA“ angezeigt wird, stellen Sie eine Konfigurationsrichtlinie für das Intune-Unternehmensportal bereit. Weitere Informationen finden Sie unter [Konfigurieren der Unternehmensportal-App zur Unterstützung von iOS-DEP-Geräten](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Problembehandlung bei der Installation von Win32-Apps

Wählen Sie die Win32-App aus, die über die Intune-Verwaltungserweiterung bereitgestellt wurde. Wenn die Installation Ihrer Win32-App fehlschlägt, können Sie die Option **Protokolle sammeln** auswählen. 

> [!IMPORTANT]
> Die Option **Protokolle sammeln** wird nicht aktiviert, wenn die Win32-App erfolgreich auf dem Gerät installiert wurde.<p>Bevor Sie Protokollinformationen für eine Win32-App sammeln können, muss die Intune-Verwaltungserweiterung auf dem Windows-Client installiert werden. Die Intune-Verwaltungserweiterung wird installiert, wenn ein PowerShell-Skript oder eine Win32-App für eine Benutzer- oder Gerätesicherheitsgruppe bereitgestellt wird. Weitere Informationen finden Sie unter [Intune-Verwaltungserweiterung – Voraussetzungen](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Sammeln von Protokollen

Wenn Sie Ihre Win32-App-Installationsprotokolle sammeln möchten, führen Sie zunächst die Schritte aus, die im Abschnitt [Details zur Problembehandlung von Apps](troubleshoot-app-install.md#app-troubleshooting-details) beschrieben sind. Fahren Sie anschließend mit den folgenden Schritten fort:

1. Klicken Sie im Bereich **Installationsdetails** auf **Protokolle sammeln**.

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. Geben Sie Dateipfade mit Protokolldateinamen an, um die Protokolldateierfassung zu starten, und klicken Sie auf **OK**.

    > [!NOTE]
    > Die Protokollsammlung dauert weniger als zwei Stunden. Unterstützte Dateitypen: *.log, .txt, .dmp, .cab, .zip, .xml, .evtx und .evtl*. Maximal 25 Dateipfade sind zulässig.

3. Nachdem die Protokolldateien gesammelt wurden, können Sie auf den Link **Protokolle** klicken, um die Protokolldateien herunterzuladen.

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

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

## <a name="android-app-installation-errors"></a>Installationsfehler bei Android-Apps

In diesem Abschnitt werden die Geräteadministratorregistrierung und die Samsung Knox-Registrierung erwähnt. Weitere Informationen dazu finden Sie unter [Android-Geräteadministratorregistrierung](../enrollment/android-enroll-device-administrator.md) und [Automatisches Registrieren von Android-Geräten mit Samsung Knox Mobile Enrollment](../enrollment/android-samsung-knox-mobile-enroll.md). 

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
| Der Dienst zum Herunterladen der Datei wurde unerwartet beendet. Die Anwendung der Richtlinie wird bei der nächsten Gerätesynchronisierung wiederholt. (0xC7D1507C) | Der Download wurde vom Betriebssystem beendet, bevor dieser abgeschlossen war. Dieser Fehler kann auftreten, wenn das Gerät eine niedrige Akkukapazität aufweist oder der Download zu lange dauert. Diese Fehlermeldung wird nur für DA-Szenarien zurückgegeben. Bei KNOX-Szenarien wird der Benutzer nicht zur Installation aufgefordert. Diese kann im Hintergrund erfolgen. Synchronisieren Sie das Gerät manuell, oder warten Sie 24 Stunden, und überprüfen Sie dann den Status. |
| Fehler beim Deinstallieren der App. (0xc7d14fb8) | Dieser Fehler ist ein generischer Deinstallationsfehler. Das Betriebssystem gibt nicht an, warum die Deinstallation der App fehlgeschlagen ist. Einige Administrator-Apps können nicht ohne Weiteres deinstalliert werden. Überprüfen Sie, ob die App manuell deinstalliert werden kann, und sehen Sie sich die Protokolle im Unternehmensportal an, wenn die Deinstallation fehlschlägt. |
| Die zum Upgrade verwendete App-Installationsdatei (APK) entspricht nicht der Signatur für die aktuelle App auf dem Gerät. (0xc7d14fb7) | Auf dem Android-Betriebssystem muss das Signaturzertifikat, das für eine Upgradeversion angefordert wird, identisch mit dem Zertifikat sein, das für die Signierung der vorhandenen Version verwendet wurde. Wenn ein Entwickler nicht dasselbe Zertifikat verwenden kann, um die neue Version zu signieren, müssen Sie die vorhandene App deinstallieren und die neue App noch mal bereitstellen, anstatt ein Upgrade für die vorhandene App durchzuführen. |
| Der Benutzer hat die App-Installation abgebrochen. (0xc7d14fb9) | Bitten Sie den Benutzer, die in Intune bereitgestellte App zu akzeptieren und bei Aufforderung zu installieren. |
| Die App-Deinstallation wurde abgebrochen, weil der Prozess während der Installation neu gestartet wurde. (0xc7d14fbc) | Der Installationsprozess der App wurde vom Betriebssystem beendet, oder das Gerät wurde neu gestartet. Wiederholen Sie die Installation, und sehen Sie sich die Protokolle im Unternehmensportal an, wenn der Fehler noch mal auftritt. |
| Die App-Installationsdatei (APK) kann nicht installiert werden, weil sie nicht signiert war. (0xc7d14fb6) | Standardmäßig müssen Apps für das Android-Betriebssystem signiert sein. Überprüfen Sie vor der Bereitstellung, ob die App signiert ist. |

## <a name="ios-app-installation-errors"></a>Installationsfehler bei iOS-Apps

In den folgenden Fehlermeldungen und -beschreibungen finden Sie weitere Informationen zu iOS-Installationsfehlern. 

| Fehlermeldung/-code | Beschreibung/Tipps zur Problembehandlung |
|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (0x87D12906) | Der Apple-MDM-Agent hat einen Fehler beim Installationsbefehl gemeldet. |
| (0x87D1313C) | Die Netzwerkverbindung wurde unterbrochen, während die aktualisierte URL des Downloaddiensts an das Gerät gesendet wurde. Insbesondere wurde kein Server mit dem angegebenen Hostnamen gefunden. |
| Das iOS-Gerät ist derzeit ausgelastet. (0x87D11388) | Das iOS-Gerät war ausgelastet, was zu einem Fehler führte. Das Gerät war gesperrt. Der Benutzer muss das Gerät entsperren, damit die App installiert werden kann. |
| Fehler bei der App-Installation. (0x87D13B64) | Es ist ein Fehler bei der App-Installation aufgetreten. Zur Behebung dieses Fehlers werden Protokolle der iOS-Konsole benötigt. |
| Die App wird verwaltet, ist jedoch abgelaufen oder wurde vom Benutzer entfernt. (0x87D13B66) | Entweder hat der Benutzer die App explizit deinstalliert, die App ist abgelaufen und es war kein Download möglich, oder die App-Erkennung führt zu keiner Übereinstimmung mit der Antwort des Geräts. Darüber hinaus kann dieser Fehler aufgrund eines Plattformfehlers von iOS 9.2.2 auftreten. |
| Die App ist für die Installation geplant, benötigt jedoch einen Einlösecode, um die Transaktion abschließen zu können. (0x87D13B60) | Dieser Fehler tritt in der Regel bei iOS Store-Apps auf, bei denen es sich um bezahlte Apps handelt. |
| Die Anwendung wurde nach erfolgreicher Installation nicht erkannt. (0x87D1041C) | Die App-Erkennung stimmte nicht mit der Antwort des Geräts überein. |
| Der Benutzer hat die angebotene Installation der App abgelehnt. (0x87D13B62) | Während der ersten App-Installation hat der Benutzer auf „Abbrechen“ geklickt. Bitten Sie den Benutzer, die Installationsanforderung das nächste Mal zu akzeptieren. |
| Der Benutzer hat das angebotene Update für die App abgelehnt. (0x87D13B63) | Der Benutzer hat während des Updates auf „Abbrechen“ geklickt. Stellen Sie gemäß den Vorgaben alle Komponenten bereit, oder bitten Sie den Benutzer, die Upgradeaufforderung zu akzeptieren. |
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
| Fehler bei der Lizenzzuweisung mit Apple-Fehler „Keine weiteren VPP-Lizenzen“. (0x87d13b7e) | Dieses Verhalten ist beabsichtigt. Den Fehler können Sie beheben, indem Sie zusätzliche VPP-Lizenzen erwerben, oder Lizenzen von Benutzern freigeben, für die sie nicht mehr benötigt werden. |
| App-Installationsfehler 12024: Unknown cause. (Grund unbekannt) (0x87d13b6e) | Apple hat uns nicht mit genügend Informationen versorgt, um ermitteln zu können, warum die Installation fehlgeschlagen ist. Es kann kein Bericht erstellt werden. |
| Needed app configuration policy not present, ensure policy is targeted to same groups. (Die erforderliche App-Konfigurationsrichtlinie ist nicht vorhanden. Sorgen Sie dafür, dass die Richtlinie für dieselben Gruppen gilt.) (0x87d13b7f) | Für die App ist eine App-Konfiguration erforderlich, es ist jedoch keine entsprechende App-Konfiguration vorhanden. Der Administrator sollte sicherstellen, dass die erforderliche App-Konfiguration für die Gruppen gilt, für die die App bereitgestellt werden soll. |
| Die VPP-Gerätelizenzierung gilt nur für Geräte unter iOS 9.0 und höher. (0x87d13b69) | Aktualisieren Sie betroffene iOS-Geräte auf mindestens iOS 9.0. |
| The application is installed on the device but is unmanaged. (Die Anwendung ist auf dem Gerät installiert, wird aber nicht verwaltet.) (0x87d13b8f) | Dieser Fehler tritt nur bei branchenspezifischen Apps auf. Die App wurde außerhalb von Intune installiert. Deinstallieren Sie die App auf dem Gerät, um diesen Fehler zu beheben. Bei der nächsten Gerätesynchronisierung sollte das Gerät die App in Intune installieren. |
| Der Benutzer hat die App-Verwaltung abgelehnt. (0x87d13b68) | Bitten Sie den Benutzer, die App-Verwaltung zu akzeptieren. |
| Unbekannter Fehler. (0x87d1279d) | Dieser Fehler tritt bei Apps aus dem iOS Store auf, das Fehlerszenario ist jedoch nicht bekannt. |
| Die App konnte nicht von einer früheren Version auf die neueste Version aktualisiert werden. (0x87D13B9D) | Diese Fehlermeldung wird angezeigt, wenn die App installiert ist und verwaltet wird, auf dem Gerät aber die falsche Version benutzt wird. Zu diesem Szenario gehört auch die Situation, in der ein Gerät den Befehl zum Aktualisieren einer App erhalten hat, die neue Version jedoch noch nicht installiert wurde, und der Fehler zurückgegeben wird. Dieser Fehler wird beim ersten Check-In eines Geräts gemeldet, nachdem das Upgrade bereitgestellt wurde, und er tritt solange auf, bis das Gerät meldet, dass die neue Version installiert ist, oder er von einem anderen Fehler abgelöst wird.  |


## <a name="other-installation-errors"></a>Andere Installationsfehler

|  Fehlermeldung/-code  |  Beschreibung  |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  0x80073CFF, 0x80CF201C (Clientfehler)  |  Zur Installation der Anwendung müssen Sie über ein zum Querladen fähiges System verfügen. Stellen Sie sicher, dass das App-Paket mit einer vertrauenswürdigen Signatur signiert und auf einem zur Domäne gehörenden Gerät mit aktivierter Richtlinie **AllowAllTrustedApps** oder auf einem Gerät mit einer Windows-Lizenz für das Querladen und aktivierter Richtlinie **AllowAllTrustedApps** installiert ist. Weitere Informationen finden Sie unter [Problembehandlung beim Packen, Bereitstellen und Abfragen von Windows Store-Apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).   |
|  0x80073CF0  |  Das Paket konnte nicht geöffnet werden. Mögliche Ursachen:<ul><li> Das Paket ist nicht signiert.</li><li> Der Name des Verlegers stimmt nicht mit dem des Signaturzertifikatantragstellers überein.</li></ul> Informationen dazu finden Sie im Ereignisprotokoll **AppxPackagingOM**. Weitere Informationen finden Sie unter [Problembehandlung beim Packen, Bereitstellen und Abfragen von Windows Store-Apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x80073CF3  |  Fehler bei Updates, Abhängigkeiten oder Konfliktüberprüfung des Pakets. Mögliche Ursachen:<ul><li> Das eingehende Paket steht mit einem installierten Paket in Konflikt.</li><li> Eine angegebene Paketabhängigkeit wurde nicht gefunden.</li><li> Das Paket unterstützt nicht die richtige Prozessorarchitektur.</li></ul> Informationen dazu finden Sie im Ereignisprotokoll **AppXDeployment-Server**. Weitere Informationen finden Sie unter [Problembehandlung beim Packen, Bereitstellen und Abfragen von Windows Store-Apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x80073CFB  |  Das bereitgestellte Paket ist bereits installiert, und eine erneute Installation des Pakets wird blockiert. Dieser Fehler kann auftreten, wenn Sie ein Paket installieren, das nicht mit dem bereits installierten Paket identisch ist. Überprüfen Sie, ob die digitale Signatur auch Teil des Pakets ist. Wenn ein Paket erneut erstellt oder signiert wird, ist das Paket nicht mehr bitweise identisch mit dem zuvor installierten Paket. Es gibt zwei Möglichkeiten, diesen Fehler zu beheben:<ul><li> Erhöhen Sie die Versionsnummer der Anwendung, und erstellen und signieren Sie das Paket dann noch mal.</li><li> Entfernen Sie das alte Paket für alle Benutzer im System, bevor Sie das neue Paket installieren.</li></ul> Weitere Informationen finden Sie unter [Problembehandlung beim Packen, Bereitstellen und Abfragen von Windows Store-Apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).  |
|  0x87D1041C  |  Die Anwendung wurde erfolgreich installiert, wird jedoch nicht erkannt. Die App wurde erfolgreich von Intune bereitgestellt und später deinstalliert. Für das Deinstallieren der App können folgende Gründe vorliegen:<ul><li> Der Endbenutzer hat die App deinstalliert.</li><li> Die Identitätsinformationen im Paket stimmen nicht mit Informationen im Gerätebericht für fehlerhafte Apps überein.</li><li>Bei MSIs, die sich eigenständig aktualisieren, stimmt die Produktversion nicht mit den Informationen der App überein, nachdem diese außerhalb von Intune aktualisiert wurde.</li></ul> Weisen Sie den Benutzer an, die App aus dem Unternehmensportal neu zu installieren. Beachten Sie, dass erforderliche Apps beim nächsten Einchecken des Geräts automatisch neu installiert werden.  |
|  0x8000FFFF  |  Unerwarteter Fehler bei der Installation. Weitere Informationen finden Sie in den Installationsprotokollen.  |

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Problembehandlung bei Apps aus dem Microsoft Store

Mithilfe der Informationen im Artikel [Problembehandlung beim Packen, Bereitstellen und Abfragen von Microsoft Store-Apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) können Sie allgemeine Probleme beheben, die bei der Installation von Apps aus dem Microsoft Store (mit Intune oder mittels anderer Tools) auftreten können.

## <a name="app-troubleshooting-resources"></a>Ressourcen zur Problembehandlung für Apps
- [Bereitstellen von Visio und Project als Teil Ihrer Office Pro Plus-Bereitstellung](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Maßnahmen ergreifen, um sicherzustellen, dass über Intune bereitgestellte Microsoft Store for Business-Apps mit der Windows 10-Version 1903 installiert werden](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Fehlerbehebung bei Bereitstellungen von MSI-Apps in Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Best Practices für die Verteilung von Intune-Software auf Windows-Computer](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zur Intune-Problembehandlung finden Sie unter [Verwenden des Problembehandlungsportals zur Unterstützung von Benutzern Ihres Unternehmens](../fundamentals/help-desk-operators.md). 
- Erfahren Sie mehr über bekannte Probleme in Microsoft Intune. Weitere Informationen finden Sie unter [Mit Intune zum Kundenerfolg](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- Benötigen Sie zusätzliche Hilfe? Weitere Informationen finden Sie unter [Anfordern von Support für Microsoft Intune](../fundamentals/get-support.md).
