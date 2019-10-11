---
title: Querladen von Windows- und Windows Phone-Apps
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie branchenspezifische Apps signieren, um sie mit Intune bereitstellen zu können.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 09/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c1d039d5be449d1c1b8cc13e69b84e1bd7f7dd2b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725282"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Signieren Sie branchenspezifische Apps, damit sie mit Intune auf Windows-Geräten bereitgestellt werden können

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Als Intune-Administrator können Sie universelle branchenspezifische Apps – einschließlich der Unternehmensportal-App – auf Windows 8.1 Desktop- oder Windows 10 Desktop- und Mobile-Geräten bereitstellen. Zum Bereitstellen von APPX-Apps auf Windows 8.1 Desktop- oder Windows 10 Desktop- und Mobile-Geräten können Sie ein codesignierendes Zertifikat einer öffentlichen Zertifizierungsstelle verwenden, der Ihre Windows-Geräte bereits vertrauen. Sie können auch Ihre eigene Zertifizierungsstelle verwenden.

 > [!NOTE]
 > Windows 8.1 Desktop erfordert entweder eine Unternehmensrichtlinie zum Aktivieren des Querladens oder die Nutzung von Schlüsseln zum Querladen (für in die Domäne eingebundene Geräte automatisch aktiviert). Weitere Informationen finden Sie unter [Windows 8 Sideloading Requirements](https://blogs.technet.microsoft.com/scd-odtsp/2012/09/27/windows-8-sideloading-requirements-from-technet/) (Anforderungen für das Querladen von Windows 8).

## <a name="windows-10-sideloading"></a>Querladen von Windows 10

Unter Windows 10 funktioniert das Querladen anders als in früheren Windows-Versionen:

- Sie können ein Gerät mithilfe einer Unternehmensrichtlinie für das Querladen entsperren. Intune bietet eine Gerätekonfigurationsrichtlinie namens „Installation vertrauenswürdiger Apps“. Bei Geräten, die dem zum Signieren der APPX-App verwendeten Zertifikat bereits vertrauen, muss diese Richtlinie einfach nur auf <allow> festgelegt werden. Das ist alles.

- Symantec Phone-Zertifikate und Lizenzschlüssel für das Querladen sind nicht erforderlich. Wenn jedoch keine lokale Zertifizierungsstelle verfügbar ist, müssen Sie möglicherweise ein codesignierendes Zertifikat von einer öffentlichen Zertifizierungsstelle abrufen. Weitere Informationen finden Sie unter [Einführung in das Codesignieren](https://docs.microsoft.com/windows/desktop/SecCrypto/cryptography-tools#introduction-to-code-signing).

### <a name="code-sign-your-app"></a>Codesignieren Ihrer App

Fügen Sie zunächst eine Codesignatur zu Ihrem APPX-Paket hinzu. Weitere Informationen dazu finden Sie unter [Signieren von App-Paketen mit SignTool](https://docs.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool).

### <a name="upload-your-app"></a>Hochladen Ihrer App

Als Nächstes müssen Sie die signierte APPX-Datei hochladen. Weitere Informationen dazu finden Sie unter [Hinzufügen von branchenspezifischen Windows-Apps zu Microsoft Intune](lob-apps-windows.md).

Wenn Sie die App für Benutzer und Geräte als erforderlich bereitstellen, benötigen Sie die Intune-Unternehmensportal-App nicht. Wenn Sie die App jedoch Benutzern als verfügbar bereitstellen, können Sie entweder die Unternehmensportal-App aus dem öffentlichen Microsoft Store oder die Unternehmensportal-App aus dem privaten Microsoft Store für Unternehmen verwenden. Sie können die Intune-Unternehmensportal-App auch signieren und manuell bereitstellen.

### <a name="upload-the-code-signing-certificate"></a>Hochladen des codesignierenden Zertifikats

Wenn Ihr Windows 10-Gerät der Zertifizierungsstelle nicht bereits vertraut, müssen Sie das codesignierende Zertifikat in das Intune-Portal hochladen, nachdem Sie Ihr APPX-Paket signiert und in den Intune-Dienst hochgeladen haben:
1. Klicken Sie auf „Client-Apps“.
2. Klicken Sie auf „Windows Enterprise-Zertifikate“.
3. Klicken Sie unter „Codesignierendes Zertifikat“ auf „Datei auswählen“.
4. Wählen Sie Ihre CER-Datei aus, und klicken Sie auf „Hochladen“.

Jetzt lädt jedes Windows 10 Desktop- und Mobile-Gerät mit einer APPX-Bereitstellung durch den Intune-Dienst automatisch das entsprechende Unternehmenszertifikat herunter, und die Anwendung kann nach der Installation gestartet werden.

Intune stellt nur die neueste hochgeladene CER-Datei bereit. Wenn Sie über mehrere APPX-Dateien von verschiedenen Entwicklern verfügen, die nicht zu Ihrer Organisation gehören, müssen diese entweder nicht signierte APPX-Dateien bereitstellen, die Sie mit Ihrem Zertifikat signieren können, oder Sie müssen den Entwicklern das von Ihrer Organisation verwendete codesignierende Zertifikat zur Verfügung stellen.

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>So wird das Symantec-Codesignaturzertifikat erneuert

Das zum Bereitstellen von mobilen Windows Phone 8.1-Apps verwendete Zertifikat wurde am 28. Februar 2019 eingestellt und steht nicht mehr zur Verlängerung durch Symantec zur Verfügung. Wenn Sie eine App für Windows 10 Mobile bereitstellen, können Sie weiterhin Symantec Desktop Enterprise-Zertifikate verwenden, die Codesignaturen hinzufügen, indem Sie die unter [Querladen von Windows 10](app-sideload-windows.md#windows-10-sideloading) beschriebenen Anweisungen befolgen.

## <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Installieren des aktualisierten Zertifikats für branchenspezifische Apps

Windows Phone 8.1

Der Intune-Dienst kann keine branchenspezifischen Apps mehr für diese Plattform bereitstellen, wenn das vorhandene codesignierende Symantec Mobile Enterprise-Zertifikat abgelaufen ist. Sie können weiterhin nicht signierte XAP/APPX-Dateien querladen, indem Sie eine SD-Karte nutzen oder die Datei auf das Gerät herunterladen. Weitere Informationen finden Sie unter [How to install XAP files on Windows Phone](https://answers.microsoft.com/en-us/mobiledevices/forum/mdlumia-mdapps/how-to-install-xap-file-in-windows-phone-8/da09ee72-51ae-407c-9b85-bc148df89280) (Installieren von XAP-Dateien unter Windows Phone).

Windows 8.1 Desktop/Windows 10 Desktop und Mobile

Wenn der Zertifizierungszeitraum abgelaufen ist, werden APPX-Dateien möglicherweise nicht mehr gestartet. Sie müssen eine neue CER-Datei abrufen und die entsprechenden Anweisungen befolgen, um die Codesignierung für jede bereitgestellte APPX-Datei durchzuführen und alle APPX-Dateien sowie die aktualisierte CER-Datei erneut im Intune-Portal in den Abschnitt „Windows Enterprise-Zertifikate“ hochzuladen.

## <a name="manually-deploy-windows-10-company-portal-app"></a>Manuelles Bereitstellen der Windows 10-Unternehmensportal-App
Wenn Sie keinen Zugriff auf den Microsoft Store ermöglichen möchten, können Sie die Windows 10-Unternehmensportal-App manuell direkt über Intune bereitstellen. Das funktioniert auch, wenn Intune nicht in den Microsoft Store für Unternehmen integriert wurde. Wenn eine solche Integration vorhanden ist, können Sie die Unternehmensportal-App alternativ auch gemäß den Informationen unter [Hinzufügen von Microsoft Store-Apps zu Microsoft Intune](store-apps-windows.md) bereitstellen.

 > [!NOTE]
 > Bei dieser Option müssen ggf. veröffentlichte App-Updates manuell bereitgestellt werden.

1. Melden Sie sich bei Ihrem Konto im [Microsoft Store für Unternehmen](https://www.microsoft.com/business-store) an, und beziehen Sie die **Offlinelizenzversion** der Unternehmensportal-App.  
2. Wenn Sie über die App verfügen, wählen Sie sie auf der Seite **Inventory** (Bestand) aus.  
3. Wählen Sie unter **Plattform** die Option **Windows 10 all devices** (Windows 10: alle Geräte) sowie die passende **Architektur** aus, und starten Sie den Downloadvorgang. Für diese App wird keine App-Lizenzdatei benötigt.
   ![Abbildung der Informationen für Windows 10-X86-Pakete für den Download](./media/app-sideload-windows/Win10CP-all-devices.png)
4. Laden Sie alle Pakete unter „Erforderliche Frameworks“ herunter. Dieser Schritt muss für die x86-, x64- und ARM-Architektur ausgeführt werden. Dadurch ergeben sich insgesamt neun Pakete, wie im Anschluss zu sehen.

   ![Abbildung mit den herunterzuladenden Abhängigkeitsdateien ](./media/app-sideload-windows/Win10CP-dependent-files.png)
5. Erstellen Sie einen Ordner (beispielsweise „C:&#92;Company Portal“), bevor Sie die Unternehmensportal-App in Intune hochladen, und strukturieren Sie die Pakete wie folgt:
   1. Platzieren Sie das Unternehmensportal-Paket im Ordner „C:\Company Portal“. Erstellen Sie dort auch einen Unterordner namens „Dependencies“.  
      ![Abbildung mit dem Ordner „Dependencies“ und der APPXBUN-Datei](./media/app-sideload-windows/Win10CP-Dependencies-save.png)
   2. Platzieren Sie die neun Abhängigkeitspakete im Ordner „Dependencies“.  
      Sind die Abhängigkeiten nicht wie hier beschrieben strukturiert, werden sie von Intune nicht erkannt und nicht hochgeladen. In diesem Fall tritt der folgende Fehler auf:  
      ![Fehlermeldung: Die Windows-App-Abhängigkeit muss angegeben werden.](./media/app-sideload-windows/Win10CP-error-message.png)
6. Kehren Sie zu Intune zurück, und laden Sie die Unternehmensportal-App als neue App hoch. Stellen Sie sie als erforderliche App für die gewünschte Gruppe von Zielbenutzern bereit.  

Weitere Informationen zur Behandlung von Abhängigkeiten für universelle Apps durch Intune finden Sie unter [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Bereitstellen einer APPXBUNDLE-Datei mit Abhängigkeiten über Microsoft Intune MDM).  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Wie aktualisiere ich das Unternehmensportal auf den Geräten meiner Benutzer, wenn diese bereits die älteren Apps aus dem Store installiert haben?
Falls Ihre Benutzer bereits die Unternehmensportal-App für Windows 8.1 oder Windows Phone 8.1 aus dem Store installiert haben, sollte diese automatisch auf die neue Version aktualisiert werden, ohne dass Sie oder Ihre Benutzer dazu aktiv werden müssen. Sollte die Aktualisierung nicht erfolgen, fordern Sie die Benutzer auf, sich zu vergewissern, dass sie auf ihren Geräten automatische Updates für Store-Apps aktiviert haben.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Wie führe ich ein Upgrade meiner quergeladenen Windows 8.1-Unternehmensportal-App auf die Windows 10-Unternehmensportal-App durch?
Wir empfehlen für die Migration die folgende Vorgehensweise: Legen Sie die Bereitstellungsaktion auf „Deinstallieren“ fest, um die Bereitstellung der Windows 8.1-Unternehmensportal-App zu löschen. Anschließend kann die Windows 10-Unternehmensportal-App mit einer der oben genannten Optionen bereitgestellt werden.  

Wenn Sie die App querladen möchten und das Windows 8.1-Unternehmensportal bereitgestellt haben, ohne es mit dem Symantec-Zertifikat zu signieren, führen Sie zur Durchführung des Upgrades die Schritte aus, die weiter oben im Abschnitt zur direkten Bereitstellung über Intune beschrieben sind.

Wenn Sie die App querladen möchten und das Windows 8.1-Unternehmensportal mit dem Symantec-Codesignaturzertifikat bereitgestellt und signiert haben, führen Sie die Schritte des folgenden Abschnitts aus.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Wie führe ich ein Upgrade meiner signierten quergeladenen Windows Phone 8.1-Unternehmensportal-App oder Windows 8.1-Unternehmensportal-App auf die Windows 10-Unternehmensportal-App durch?
Wir empfehlen für die Migration die folgende Vorgehensweise: Legen Sie die Bereitstellungsaktion auf „Deinstallieren“ fest, um die vorhandene Bereitstellung der Windows Phone 8.1-Unternehmensportal-App oder Windows 8.1-Unternehmensportal-App zu löschen. Anschließend kann die Windows 10-Unternehmensportal-App ganz normal bereitgestellt werden.  

Andernfalls muss die Windows 10-Unternehmensportal-App entsprechend aktualisiert und signiert werden, um sicherzustellen, dass der Upgradepfad eingehalten wird.  

Wenn die Windows 10-Unternehmensportal-App auf diese Weise signiert und bereitgestellt wird, müssen Sie diesen Prozess für jedes neue App-Update wiederholen, das im Store verfügbar wird. Die App wird nicht automatisch aktualisiert, wenn der Store aktualisiert wird.  

Im Anschluss erfahren Sie, wie Sie die App auf diese Weise signieren und bereitstellen:

1. Laden Sie unter [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript) das Microsoft Intune-Signierungsskript für die Windows 10-Unternehmensportal-App herunter.  Für dieses Skript muss das Windows SDK für Windows 10 auf dem Hostcomputer installiert sein. Besuchen Sie die Seite [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296), um das Windows SDK für Windows 10 herunterzuladen.
2. Laden Sie die Windows 10-Unternehmensportal-App wie weiter oben beschrieben aus dem Microsoft Store für Unternehmen herunter.  
3. Führen Sie das Skript mit den im Skriptheader angegebenen Eingabeparametern aus, um die Windows 10-Unternehmensportal-App zu signieren (siehe Auszug weiter unten). An das Skript müssen keine Abhängigkeiten übergeben werden. Diese sind nur erforderlich, wenn die App in die Intune-Verwaltungskonsole hochgeladen wird.

|       Parameter       |                                                                    Beschreibung                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             Der Pfad, an dem sich die APPXBUNDLE-Quelldatei befindet.                                              |
| OutputWin10AppxBundle |                                                  Der Ausgabepfad für die signierte APPXBUNDLE-Datei.                                                  |
|       Win81Appx       |                          Der Pfad, an dem sich die APPX-Datei des Windows 8.1- oder Windows Phone 8.1-Unternehmensportals befindet.                           |
|      PfxFilePath      |                                   Der Pfad der PFX-Datei für das Symantec Enterprise Mobile-Codesignaturzertifikat.                                    |
|      PfxPassword      |                                     Das Kennwort des Symantec Enterprise Mobile-Codesignaturzertifikats.                                      |
|      PublisherId      |      Die Herausgeber-ID des Unternehmens. Wenn sie nicht vorhanden ist, wird das Feld "Subject" von Symantec Enterprise Mobile Code Signing Certificate verwendet.       |
|        SdkPath        | Der Pfad des Stammordners für das Windows SDK für Windows 10. Dieses Argument ist optional und wird standardmäßig auf „${env:ProgramFiles(x86)}\Windows Kits\10“ festgelegt. |

Das Skript gibt nach der Ausführung die signierte Version der Windows 10-Unternehmensportal-App aus. Anschließend können Sie die signierte Version der Anwendung über Intune als branchenspezifische App bereitstellen. Dadurch wird für die derzeit bereitstellten Versionen ein Upgrade auf die neue App durchgeführt.  
