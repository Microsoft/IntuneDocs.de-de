---
title: "Hinzufügen von Windows Store-Apps in Microsoft Intune"
titleSuffix: 
description: "Erfahren Sie mehr über das Hinzufügen von Windows Store-Apps in Microsoft Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 815f780ef9f04870f19e75481ed74f0a1c3601f3
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="how-to-add-windows-store-apps-to-microsoft-intune"></a>Hinzufügen von Windows Store-Apps in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Bevor Sie Apps zuweisen, überwachen, konfigurieren oder schützen können, müssen Sie sie zu Intune hinzufügen. Mit den folgenden Schritte können Sie eine Windows Store-App zu Microsoft Intune hinzufügen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.
3. Wählen Sie auf dem Blatt **Intune** die Option **Apps verwalten** aus.
4. Wählen Sie in der Workload **Mobile Apps** im Abschnitt **Verwalten** die Option **Apps** aus.
5. Wählen Sie über der Liste **Hinzufügen** aus.
6. Wählen Sie aus der Liste der verfügbaren Typen von **Store-Apps** den Eintrag **Windows** aus.
7. Wählen Sie **App-Informationen** aus, um die App-Informationen zu konfigurieren.
8. Konfigurieren Sie auf dem Blatt **App-Informationen** die folgenden Informationen: Je nachdem, welche App Sie ausgewählt haben, werden einige der Werte automatisch in diesem Bereich eingetragen:
    - **App-Name:** Geben Sie den Namen der App ein, wie er im Unternehmensportal angezeigt werden soll. Stellen Sie sicher, dass alle App-Namen eindeutig sind. Wenn ein App-Name zweimal vergeben wird, wird den Benutzern im Unternehmensportal nur eine der Apps angezeigt.
    - **Beschreibung:** Geben Sie eine Beschreibung für die App ein. Diese Beschreibung wird den Benutzern im Unternehmensportal angezeigt.
    - **Herausgeber:** Geben Sie den Namen des Herausgebers der App ein.
    - **App Store-URL:** Geben Sie die App Store-URL der App an, die Sie erstellen möchten. 
    - **Kategorie (optional)**: Wählen Sie mindestens eine der App-Kategorien oder eine von Ihnen erstellte Kategorie aus. Durch das Hinzufügen dieser Informationen wird es für die Benutzer leichter, die App im Unternehmensportal zu finden.
    - **Diese App als ausgewählte App im Unternehmensportal anzeigen:** Zeigen Sie die App auf der Hauptseite des Unternehmensportal hervorgehoben an, wenn Benutzer nach Apps suchen.
    - **Informations-URL** (optional): Geben Sie eine URL zu einer Website ein, die Informationen über diese App enthält. Diese URL wird den Benutzern im Unternehmensportal angezeigt.
    - **URL zu den Datenschutzbestimmungen** (optional): Geben Sie eine URL zu einer Website ein, die Datenschutzinformationen für diese App enthält. Diese URL wird den Benutzern im Unternehmensportal angezeigt.
    - **Entwickler** (optional): Geben Sie optional den Namen des App-Entwicklers ein.
    - **Besitzer** (optional): Geben Sie optional einen Namen für den Besitzer dieser App ein, z.B. **Personalabteilung**.
    - **Anmerkungen** (optional): Geben Sie Anmerkungen ein, die dieser App zugewiesen werden sollen.
    - **Symbol hochladen:** Laden Sie ein Symbol hoch, das der App zugeordnet wird. Dieses Symbol wird mit der App angezeigt, wenn Benutzer das Unternehmensportal durchsuchen.
1. Klicken Sie auf **OK**, wenn Sie alle erforderlichen App-Informationen eingegeben haben.
2. Klicken Sie auf dem Blatt **App hinzufügen** auf **Hinzufügen**.

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie ausgewählten Gruppen zuweisen können. Hilfe finden Sie unter [Zuweisen von Apps zu Gruppen](apps-deploy.md).

## <a name="manually-assign-windows-10-company-portal-app"></a>Manuelles Zuweisen der Windows 10-Unternehmensportal-App
Benutzer können die Unternehmensportal-App aus dem Microsoft Store installieren, um Geräte zu verwalten und Apps zu installieren. Wenn Ihr Unternehmen allerdings erfordert, dass Sie die Unternehmensportal-App zuweisen, können Sie die Windows 10-Unternehmensportal-App manuell direkt über Intune zuweisen, auch wenn Intune nicht in den Microsoft Store für Unternehmen integriert wurde.

 > [!NOTE]
 > Bei dieser Option müssen ggf. veröffentlichte App-Updates manuell zugewiesen werden.

1. Melden Sie sich bei Ihrem Konto im [Microsoft Store für Unternehmen](https://www.microsoft.com/business-store) an, und beziehen Sie die **Offlinelizenzversion** der Unternehmensportal-App.  
2. Wenn Sie über die App verfügen, wählen Sie sie auf der Seite **Inventory** (Bestand) aus.  
3. Wählen Sie unter **Plattform** die Option **Windows 10 all devices** (Windows 10: alle Geräte) sowie die passende **Architektur** aus, und starten Sie den Downloadvorgang. Für diese App wird keine App-Lizenzdatei benötigt.

    ![Abbildung mit Details zum Downloadpaket für „Windows 10 all devices“ (Windows 10: alle Geräte) und x86-Architektur](./media/Win10CP-all-devices.png)

4. Laden Sie alle Pakete unter „Erforderliche Frameworks“ herunter. Dieser Schritt muss für die x86-, x64- und ARM-Architektur ausgeführt werden. Dadurch ergeben sich insgesamt neun Pakete, wie im Anschluss zu sehen.

    ![Abbildung mit den herunterzuladenden Abhängigkeitsdateien](./media/Win10CP-dependent-files.png)

5. Erstellen Sie einen Ordner (beispielsweise „C:&#92;Company Portal“), bevor Sie die Unternehmensportal-App in Intune hochladen, und strukturieren Sie die Pakete wie folgt:
  - Platzieren Sie das Unternehmensportal-Paket im Ordner „C:\Company Portal“. Erstellen Sie dort auch einen Unterordner namens „Dependencies“.  
  
    ![Abbildung mit dem Ordner „Dependencies“ und der APPXBUN-Datei](./media/Win10CP-Dependencies-save.png)

  - Platzieren Sie die neun Abhängigkeitspakete im Ordner „Dependencies“. Sind die Abhängigkeiten nicht wie hier beschrieben strukturiert, werden sie von Intune nicht erkannt und nicht hochgeladen. In diesem Fall tritt der folgende Fehler auf: 

      ![Die Windows App-Abhängigkeit für dieses Softwareinstallationsprogramm wurde im Anwendungsordner nicht gefunden. Sie können diese Anwendung weiterhin erstellen und zuweisen. Sie können sie jedoch nicht ausführen, bis die fehlende Windows-App-Abhängigkeit bereitgestellt wird.](./media/Win10CP-error-message.png)

6. Kehren Sie zu Intune zurück, und laden Sie die Unternehmensportal-App als neue App hoch. Weisen Sie sie für die gewünschte Gruppe von Zielbenutzern als erforderliche App zu.  

Weitere Informationen zur Behandlung von Abhängigkeiten für universelle Apps durch Intune finden Sie unter [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Bereitstellen einer APPXBUNDLE-Datei mit Abhängigkeiten über Microsoft Intune MDM).  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Wie aktualisiere ich das Unternehmensportal auf den Geräten meiner Benutzer, wenn diese bereits die älteren Apps aus dem Store installiert haben?
Falls Ihre Benutzer bereits die Unternehmensportal-App für Windows 8.1 oder Windows Phone 8.1 aus dem Store installiert haben, sollte diese automatisch auf die neue Version aktualisiert werden, ohne dass Sie oder Ihre Benutzer dazu aktiv werden müssen. Sollte die Aktualisierung nicht erfolgen, fordern Sie die Benutzer auf, sich zu vergewissern, dass sie auf ihren Geräten automatische Updates für Store-Apps aktiviert haben.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Wie führe ich ein Upgrade meiner quergeladenen Windows 8.1-Unternehmensportal-App auf die Windows 10-Unternehmensportal-App durch?
Wir empfehlen für die Migration die folgende Vorgehensweise: Legen Sie die Zuweisungsaktion auf „Deinstallieren“ fest, um die Zuweisung der Windows 8.1-Unternehmensportal-App zu löschen. Anschließend kann die Windows 10-Unternehmensportal-App mit einer der oben genannten Optionen zugewiesen werden.  

Wenn Sie die App querladen möchten und das Windows 8.1-Unternehmensportal zugewiesen haben, ohne es mit dem Symantec-Zertifikat zu signieren, führen Sie zur Durchführung des Upgrades die Schritte aus, die weiter oben im Abschnitt zur direkten Zuweisung über Intune beschrieben sind.

Wenn Sie die App querladen möchten und das Windows 8.1-Unternehmensportal mit dem Symantec-Codesignaturzertifikat zugewiesen und signiert haben, führen Sie die Schritte des folgenden Abschnitts aus.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Wie führe ich ein Upgrade meiner signierten quergeladenen Windows Phone 8.1-Unternehmensportal-App oder Windows 8.1-Unternehmensportal-App auf die Windows 10-Unternehmensportal-App durch?
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
