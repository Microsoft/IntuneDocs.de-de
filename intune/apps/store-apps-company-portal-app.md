---
title: Manuelles Hinzufügen der Windows 10-Unternehmensportal-App
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Ihre Mitarbeiter die Windows 10-Unternehmensportal-App manuell aus dem Microsoft Store zu ihrem PC hinzufügen können.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c2083d6f259b62b2856e08fec5ebcb696cbc0df
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576450"
---
# <a name="add-the-windows-10-company-portal-app-by-using-microsoft-intune"></a>Hinzufügen der Windows 10-Unternehmensportal-App mithilfe von Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Benutzer können die Unternehmensportal-App selbst über den Microsoft Store installieren, um Geräte zu verwalten und Apps zu installieren. Wenn Sie allerdings in Ihrem Unternehmen den Benutzern die Windows 10-Unternehmensportal-App zuweisen müssen, können Sie diesen Vorgang direkt über Intune durchführen. Dies ist selbst dann möglich, wenn Sie Intune nicht in den Microsoft Store für Unternehmen integriert haben.

 > [!IMPORTANT]
 > Wenn Sie beim Herunterladen der Unternehmensportal-App wie in diesem Artikel beschrieben vorgehen möchten, müssen Sie bei jeder Veröffentlichung eines App-Updates manuelle Updates zuweisen. Informationen zur Bereitstellung der Unternehmensportal-App für Autopilot-Geräte unter Windows 10 finden Sie unter [Hinzufügen der Unternehmensportal-App für Autopilot-Geräte unter Windows 10](~/apps/store-apps-company-portal-autopilot.md).

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
6. Klicken Sie unter **Paketdetails** auf **Download**, um die Datei auf Ihrem lokalen Computer zu speichern.

    ![Windows 10-Geräte mit x86-Architektur sind ausgewählt.](./media/app-sideload-windows/Win10CP-all-devices.png)

7. Laden Sie alle Pakete unter „Required Frameworks“ (Erforderliche Frameworks) herunter, indem Sie auf **Download** (Herunterladen) klicken.  

    Diese Aktion muss für die x86-, x64- und ARM-Architektur ausgeführt werden:<br> 
    *Es gibt 9 erforderliche Frameworkpakete, wenn Sie Version 1507 als Mindestversion für das Betriebssystem auswählen, 12 Pakete für Version 1511 und 15 Pakete für Version 1607.* .

8. Laden Sie im Azure-Portal die Unternehmensportal-App als neue App in Microsoft Intune hoch. Fügen Sie die Anwendung hinzu, indem Sie „Branchenspezifische App“ als **App-Typ** in dem Bereich **App-Typ auswählen** auswählen. Wählen Sie dann die App-Paketdatei (mit der Erweiterung „.AppxBundle“) aus.

9. Wählen Sie unter **App-Abhängigkeitsdateien auswählen** alle Abhängigkeiten aus, die Sie in Schritt 7 durch Klicken bei gedrückter UMSCHALTTASTE heruntergeladen haben, und stellen Sie sicher, dass die Spalte **Hinzugefügt** für die von Ihnen benötigten Architekturen **Ja** anzeigt.

     > [!NOTE]
     > Wenn die Abhängigkeiten nicht hinzugefügt werden, wird die App möglicherweise nicht auf den festgelegten Gerätetypen installiert.

10. Klicken Sie auf **OK**, geben Sie eine beliebige **App-Information** ein, und klicken Sie auf **Hinzufügen**.

11. Weisen Sie den Zielbenutzern oder Gerätegruppen die Unternehmensportal-App als erforderliche App zu.  

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

