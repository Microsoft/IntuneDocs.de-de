---
title: Manuelles Hinzufügen der Windows 10-Unternehmensportal-App
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie die Windows 10-Unternehmensportal-App manuell hinzufügen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 169d0a32fdc86b5cd3f36421e6057cdeae1a078f
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="manually-add-the-windows-10-company-portal-app-by-using-microsoft-intune"></a>Manuelles Hinzufügen der Windows 10-Unternehmensportal-App mithilfe von Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Benutzer können die Unternehmensportal-App selbst über den Microsoft Store installieren, um Geräte zu verwalten und Apps zu installieren. Wenn Sie allerdings in Ihrem Unternehmen den Benutzern die Windows 10-Unternehmensportal-App zuweisen müssen, können Sie diesen Vorgang direkt über Intune durchführen. Dies ist selbst dann möglich, wenn Sie Intune nicht in den Microsoft Store für Unternehmen integriert haben.

 > [!NOTE]
 > Wenn Sie die in diesem Artikel beschriebene Option nutzen möchten, müssen Sie bei jedem Release eines App-Updates das Update manuell zuweisen.

## <a name="configure-settings-to-show-offline-apps"></a>Konfigurieren der Einstellungen zum Anzeigen von Offline-Apps
1. Melden Sie sich beim [Microsoft Store für Unternehmen](https://www.microsoft.com/business-store) mit Ihrem Administratorkonto an.
2. Klicken Sie auf die Registerkarte **Verwalten** am oberen Rand des Fensters.
3. Klicken Sie im linken Bereich auf **Settings** (Einstellungen).
4. Legen Sie unter **Shopping experience** (Einkaufserlebnis) die Option **Show offline apps** (Offline-Apps anzeigen) auf **On** (Aktiv) fest.  
    Dadurch werden die lizenzierten Offline-Apps angezeigt.

## <a name="download-the-offline-company-portal-app"></a>Herunterladen der Offline-Unternehmensportal-App
1. Suchen Sie die **Unternehmensportal**-App, und wählen Sie diese aus.
2. Legen Sie den **Lizenztyp** auf **Offline** fest.
3. Klicken Sie auf **App nutzen**, um die Offline-Unternehmensportal-App Ihrem Inventar hinzuzufügen.
4. Klicken Sie auf der Seite der **Unternehmensportal**-App auf **Manage** (Verwalten).
5. Wählen Sie **Windows 10 all devices** (Alle Windows 10-Geräte) als **Platform** (Plattform) aus. Legen Sie anschließend für **Minimum version** (Mindestversion), **Architecture** (Architektur) und **Download app metadata** (App-Metadaten herunterladen) die entsprechenden Werte fest. 
6. Klicken Sie auf **Download** (Herunterladen), um die Datei auf Ihrem lokalen Computer zu speichern.

    ![Details zum Downloadpaket für „Windows 10 all devices“ (Alle Windows 10-Geräte) und für die x86-Architektur](./media/Win10CP-all-devices.png)

7. Laden Sie alle Pakete unter „Required Frameworks“ (Erforderliche Frameworks) herunter, indem Sie auf **Download** (Herunterladen) klicken.  
    Diese Aktion muss für die x86-, x64- und ARM-Architektur ausgeführt werden. Dadurch ergeben sich insgesamt 12 Pakete.
8. Erstellen Sie einen Ordner (beispielsweise „C:\Company Portal“), bevor Sie die Unternehmensportal-App in Intune hochladen, und strukturieren Sie die Pakete wie folgt:
   - Platzieren Sie das Unternehmensportal-Paket im Ordner „C:\Company Portal“. Erstellen Sie dort auch einen Unterordner mit dem Namen *Dependencies*.  

     ![Ordner „Dependencies“ und APPXBUN-Datei](./media/Win10CP-Dependencies-save.png)

   - Platzieren Sie die Abhängigkeitspakete im Ordner *Abhängigkeiten*. 

     > [!NOTE]
     > Wenn die Abhängigkeiten nicht im richtigen Format angegeben sind, kann Intune sie nicht erkennen und lädt die Dateien während des Paketuploads nicht hoch. Dadurch schlägt der Upload fehl, und es wird eine Fehlermeldung angezeigt.

9. Laden Sie im Azure-Portal die Unternehmensportal-App als neue App in Microsoft Intune hoch. 
10. Weisen Sie die Unternehmensportal-App als erforderliche App den Zielbenutzern zu.  

Weitere Informationen zur Verarbeitung von Abhängigkeiten für universelle Apps durch Intune finden Sie unter [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Bereitstellen einer APPXBUNDLE-Datei mit Abhängigkeiten über Microsoft Intune MDM).  

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen 
### <a name="how-do-i-update-the-company-portal-app-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Wie aktualisiere ich die Unternehmensportal-App auf den Geräten meiner Benutzer, wenn diese bereits die älteren Apps aus dem Store installiert haben?
Falls Ihre Benutzer bereits die Unternehmensportal-App für Windows 8.1 oder Windows Phone 8.1 aus dem Microsoft Store installiert haben, sollte diese automatisch auf die neue Version aktualisiert werden, ohne dass Sie oder Ihre Benutzer dazu aktiv werden müssen. Sollte das Update nicht durchgeführt werden, fordern Sie die Benutzer auf, sich zu vergewissern, dass sie auf ihren Geräten automatische Updates für Store-Apps aktiviert haben.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Wie führe ich ein Upgrade meiner quergeladenen Windows 8.1-Unternehmensportal-App auf die Windows 10-Unternehmensportal-App durch?
Für die Migration wird folgende Vorgehensweise empfohlen: Legen Sie die Zuweisungsaktion auf **Uninstall** (Deinstallieren) fest, um die Zuweisung der Windows 8.1-Unternehmensportal-App zu löschen. Nach dem Durchführen dieser Einstellung können Sie die Windows 10-Unternehmensportal-App mithilfe der oben beschriebenen Optionen zuweisen.  

Wenn Sie die App querladen müssen und das Windows 8.1-Unternehmensportal zugewiesen haben, ohne es mit dem Symantec-Zertifikat zu signieren, führen Sie zur Durchführung des Upgrades die Schritte aus, die in den vorherigen Abschnitten dieses Artikels genannt wurden.

Wenn Sie die App querladen müssen und die Windows 8.1-Unternehmensportal-App mit dem Symantec-Codesignaturzertifikat zugewiesen und signiert haben, führen Sie die Schritte im folgenden Abschnitt aus.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Wie führe ich ein Upgrade meiner signierten quergeladenen Windows Phone 8.1-Unternehmensportal-App oder Windows 8.1-Unternehmensportal-App auf die Windows 10-Unternehmensportal-App durch?
Wir empfehlen für die Migration die folgende Vorgehensweise: Legen Sie die Zuweisungsaktion auf **Uninstall** (Deinstallieren) fest, um die vorhandene Zuweisung der Windows Phone 8.1-Unternehmensportal-App oder Windows 8.1-Unternehmensportal-App zu löschen. Nach dem Durchführen dieser Einstellung können Sie die Windows 10-Unternehmensportal-App normal zuweisen.  

Ansonsten muss die Windows 10-Unternehmensportal-App entsprechend aktualisiert und signiert werden, um sicherzustellen, dass der Upgradepfad berücksichtigt wird.  

Wenn Sie die Windows 10-Unternehmensportal-App auf diese Weise signieren und zuweisen, müssen Sie diesen Vorgang für jedes neue App-Update wiederholen, das im Store verfügbar wird. Die App wird nicht automatisch aktualisiert, wenn der Store aktualisiert wird.  

Im Anschluss erfahren Sie, wie Sie die App auf diese Weise signieren und zuweisen:

1. Laden Sie das [Microsoft Intune-Signierungsskript für die Windows 10-Unternehmensportal-App](https://aka.ms/win10cpscript) herunter.  
    Für dieses Skript muss das Windows SDK für Windows 10 auf dem Hostcomputer installiert sein. [Windows SDK für Windows 10 herunterladen](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Laden Sie die Windows 10-Unternehmensportal-App wie weiter oben beschrieben aus dem Microsoft Store für Unternehmen herunter.  
3. Führen Sie das Skript mit den im Skriptheader angegebenen Eingabeparametern (s. Tabelle unten) aus, um die Windows 10-Unternehmensportal-App zu signieren.  
    An das Skript müssen keine Abhängigkeiten übergeben werden. Diese sind nur erforderlich, wenn die App in die Intune-Verwaltungskonsole hochgeladen wird.

| Parameter |  Beschreibung  |
|---|---|
| InputWin10AppxBundle  |  Der Pfad der APPXBUNDLE-Quelldatei. |
| OutputWin10AppxBundle | Der Ausgabepfad für die signierte APPXBUNDLE-Datei. 
| Win81Appx  | Der Pfad der APPX-Datei des Windows 8.1- oder Windows Phone 8.1-Unternehmensportals. |
| PfxFilePath  |  Der Pfad der PFX-Datei für das Symantec Enterprise Mobile-Codesignaturzertifikat.  |
| PfxPassword  | Das Kennwort des Symantec Enterprise Mobile-Codesignaturzertifikats. |
| PublisherId | Die Herausgeber-ID des Unternehmens. Wenn sie nicht vorhanden ist, wird das Feld „Subject“ (Zertifikatinhaber) vom Symantec Enterprise Mobile-Codesignaturzertifikat verwendet. |
| SdkPath | Der Pfad des Stammordners für das Windows SDK für Windows 10. Dieses Argument ist optional und wird standardmäßig auf „${env:Programme (x86)}\Windows Kits\10“ festgelegt.  |

Das Skript gibt nach der Ausführung die signierte Version der Windows 10-Unternehmensportal-App aus. Anschließend können Sie die signierte Version der App über Intune als branchenspezifische App zuweisen. Dadurch wird für die derzeit zugewiesenen Versionen ein Upgrade auf die neue App durchgeführt.  

## <a name="next-steps"></a>Nächste Schritte

- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md)

