---
title: "Manuelles Hinzufügen der Windows 10-Unternehmensportal-App"
titleSuffix: Microsoft Intune
description: "Erfahren Sie, wie Sie die Windows 10-Unternehmensportal-App manuell hinzufügen."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 06ed9395d06e2d64edcedcaadfe819ad03f1d495
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="manually-add-the-windows-10-company-portal-app-using-microsoft-intune"></a>Manuelles Hinzufügen der Windows 10-Unternehmensportal-App mithilfe von Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Benutzer können die Unternehmensportal-App aus dem Microsoft Store installieren, um Geräte zu verwalten und Apps zu installieren. Wenn Ihr Unternehmen allerdings erfordert, dass Sie die Unternehmensportal-App zuweisen, können Sie die Windows 10-Unternehmensportal-App manuell direkt über Intune zuweisen, auch wenn Intune nicht in den Microsoft Store für Unternehmen integriert wurde.

 > [!NOTE]
 > Bei dieser Option müssen ggf. veröffentlichte App-Updates manuell zugewiesen werden.

## <a name="configure-settings-to-show-offline-apps"></a>Konfigurieren der Einstellungen zum Anzeigen von Offline-Apps
1. Öffnen Sie den [Microsoft Store für Unternehmen](https://www.microsoft.com/business-store), und stellen Sie sicher, dass Sie mit Ihrem Administratorkonto angemeldet sind.
2. Klicken Sie auf die Registerkarte **Verwalten** am oberen Rand des Fensters.
3. Klicken Sie in der linken Navigationsspalte auf **Einstellungen**.
4. Legen Sie die Option **Show offline apps** (Offline-Apps anzeigen) im Abschnitt **Shopping experience** (Einkaufserlebnis) auf **On** (Aktiv) fest. Dadurch werden lizenzierte Offline-Apps im Microsoft Store für Unternehmen angezeigt.

## <a name="download-the-offline-company-portal-app"></a>Herunterladen der Offline-Unternehmensportal-App
1. Suchen Sie die **Unternehmensportal**-App, und wählen Sie diese aus.
2. Legen Sie den **Lizenztyp** auf **Offline** fest.
3. Klicken Sie auf **App nutzen**, um die Offline-Unternehmensportal-App zu Ihrem Inventar hinzuzufügen.
4. Klicken Sie auf der Seite der **Unternehmensportal**-App auf **Verwalten**.
5. Wählen Sie **Windows 10 all devices** (Alle Windows 10-Geräte) als **Plattform** aus, legen Sie dann die jeweilige **Mindestversion** und **Architektur** fest, und laden Sie die Metadatenwerte der App** herunter. 
6. Klicken Sie auf **Herunterladen**, um die Datei auf Ihrem lokalen Computer zu speichern.

    ![Abbildung mit Details zum Downloadpaket für „Windows 10 all devices“ (alle Windows 10-Geräte) und x86-Architektur](./media/Win10CP-all-devices.png)

7. Laden Sie alle Pakete unter „Erforderliche Frameworks“ herunter. Dieser Schritt muss für die x86-, x64- und ARM-Architektur ausgeführt werden. Dadurch ergeben sich insgesamt 12 Pakete.
8. Erstellen Sie einen Ordner (beispielsweise „C:&#92;Company Portal“), bevor Sie die Unternehmensportal-App in Intune hochladen, und strukturieren Sie die Pakete wie folgt:
  - Platzieren Sie das Unternehmensportal-Paket im Ordner „C:\Company Portal“. Erstellen Sie dort auch einen Unterordner namens „Dependencies“.  

    ![Abbildung mit dem Ordner „Dependencies“ und der APPXBUN-Datei](./media/Win10CP-Dependencies-save.png)

  - Platzieren Sie die Abhängigkeitspakete im Ordner *Abhängigkeiten*. 

     > [!NOTE]
     > Wenn die Abhängigkeiten nicht im richtigen Format angegeben sind, kann Intune sie nicht erkennen und lädt die Dateien nicht hoch, wodurch eine Fehlermeldung ausgelöst wird.

9. Kehren Sie zu Microsoft Intune im Azure-Portal zurück.
10. Laden Sie die Unternehmensportal-App als neue App hoch. Weisen Sie sie für die gewünschte Gruppe von Zielbenutzern als erforderliche App zu.  

Weitere Informationen zur Behandlung von Abhängigkeiten für universelle Apps durch Intune finden Sie unter [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Bereitstellen einer APPXBUNDLE-Datei mit Abhängigkeiten über Microsoft Intune MDM).  

## <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Wie aktualisiere ich das Unternehmensportal auf den Geräten meiner Benutzer, wenn diese bereits die älteren Apps aus dem Store installiert haben?
Falls Ihre Benutzer bereits die Unternehmensportal-App für Windows 8.1 oder Windows Phone 8.1 aus dem Store installiert haben, sollte diese automatisch auf die neue Version aktualisiert werden, ohne dass Sie oder Ihre Benutzer dazu aktiv werden müssen. Sollte die Aktualisierung nicht erfolgen, fordern Sie die Benutzer auf, sich zu vergewissern, dass sie auf ihren Geräten automatische Updates für Store-Apps aktiviert haben.   

## <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Wie führe ich ein Upgrade meiner quergeladenen Windows 8.1-Unternehmensportal-App auf die Windows 10-Unternehmensportal-App durch?
Für die Migration wird folgende Vorgehensweise empfohlen: Legen Sie die Zuweisungsaktion auf „Deinstallieren“ fest, um die Zuweisung der Windows 8.1-Unternehmensportal-App zu löschen. Anschließend kann die Windows 10-Unternehmensportal-App mit einer der oben genannten Optionen zugewiesen werden.  

Wenn Sie die App querladen möchten und das Windows 8.1-Unternehmensportal zugewiesen haben, ohne es mit dem Symantec-Zertifikat zu signieren, führen Sie zur Durchführung des Upgrades die Schritte aus, die weiter oben im Abschnitt zur direkten Zuweisung über Intune beschrieben sind.

Wenn Sie die App querladen möchten und das Windows 8.1-Unternehmensportal mit dem Symantec-Codesignaturzertifikat zugewiesen und signiert haben, führen Sie die Schritte des folgenden Abschnitts aus.  

## <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Wie führe ich ein Upgrade meiner signierten quergeladenen Windows Phone 8.1-Unternehmensportal-App oder Windows 8.1-Unternehmensportal-App auf die Windows 10-Unternehmensportal-App durch?
Wir empfehlen für die Migration die folgende Vorgehensweise: Legen Sie die Zuweisungsaktion auf „Deinstallieren“ fest, um die vorhandene Zuweisung der Windows Phone 8.1-Unternehmensportal-App oder Windows 8.1-Unternehmensportal-App zu löschen. Anschließend kann die Windows 10-Unternehmensportal-App ganz normal zugewiesen werden.  

Andernfalls muss die Windows 10-Unternehmensportal-App entsprechend aktualisiert und signiert werden, um sicherzustellen, dass der Upgradepfad eingehalten wird.  

Wenn die Windows 10-Unternehmensportal-App auf diese Weise signiert und zugewiesen wird, müssen Sie diesen Prozess für jedes neue App-Update wiederholen, das im Store verfügbar wird. Die App wird nicht automatisch aktualisiert, wenn der Store aktualisiert wird.  

Im Anschluss erfahren Sie, wie Sie die App auf diese Weise signieren und zuweisen:

1. Laden Sie unter [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript) das Microsoft Intune-Signierungsskript für die Windows 10-Unternehmensportal-App herunter.  Für dieses Skript muss das Windows SDK für Windows 10 auf dem Hostcomputer installiert sein. Das Windows SDK für Windows 10 können Sie unter [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296) herunterladen.
2. Laden Sie die Windows 10-Unternehmensportal-App wie weiter oben beschrieben aus dem Microsoft Store für Unternehmen herunter.  
3. Führen Sie das Skript mit den im Skriptheader angegebenen Eingabeparametern aus, um die Windows 10-Unternehmensportal-App zu signieren (siehe Auszug weiter unten). An das Skript müssen keine Abhängigkeiten übergeben werden. Diese sind nur erforderlich, wenn die App in die Intune-Verwaltungskonsole hochgeladen wird.

|Parameter | Beschreibung|
| ------------- | ------------- |
|InputWin10AppxBundle |Der Pfad, an dem sich die APPXBUNDLE-Quelldatei befindet. |
|OutputWin10AppxBundle |Der Ausgabepfad für die signierte APPXBUNDLE-Datei.  Win81Appx Der Pfad, an dem sich die APPX-Datei des Windows 8.1- oder Windows Phone 8.1-Unternehmensportals befindet.|
|PfxFilePath |Der Pfad der PFX-Datei für das Symantec Enterprise Mobile-Codesignaturzertifikat. |
|PfxPassword| Das Kennwort des Symantec Enterprise Mobile-Codesignaturzertifikats. |
|PublisherId |Die Herausgeber-ID des Unternehmens. Wenn sie nicht vorhanden ist, wird das Feld "Subject" von Symantec Enterprise Mobile Code Signing Certificate verwendet.|
|SdkPath | Der Pfad des Stammordners für das Windows SDK für Windows 10. Dieses Argument ist optional und wird standardmäßig auf „${env:ProgramFiles(x86)}\Windows Kits\10“ festgelegt.|
Das Skript gibt nach der Ausführung die signierte Version der Windows 10-Unternehmensportal-App aus. Anschließend können Sie die signierte Version der Anwendung über Intune als branchenspezifische App zuweisen. Dadurch wird für die derzeit zugewiesenen Versionen ein Upgrade auf die neue App durchgeführt.  

## <a name="next-steps"></a>Nächste Schritte

- [Zuweisen von Apps zu Gruppen](apps-deploy.md)

