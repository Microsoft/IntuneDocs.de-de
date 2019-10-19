---
title: Entfernen Ihres Windows-Geräts aus der Intune-Verwaltung
description: Beschreibt das Entfernen eines Windows-Geräts aus der Intune-Verwaltung
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: e64911ea9b1b1d3c619a82eac9dc78e4e78a53e9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508130"
---
# <a name="remove-your-windows-device-from-management"></a>Entfernen Ihres Windows-Geräts aus der Verwaltung

Entfernen Sie ein registriertes Windows-Gerät aus der Verwaltung, wenn Sie es für folgende Zwecke nicht mehr wünschen oder benötigen:  
* Verwenden Ihres Geräts für geschäftliche oder schulische Aufgaben 
* Zugreifen auf geschäftliche oder schulische E-Mail, Apps oder andere Ressourcen

Nachdem Sie die Registrierung für das Gerät aufgehoben haben, verfügen Sie nicht mehr über die Berechtigungen für den Zugriff auf Schul-, Uni- oder Geschäftsressourcen. Sie können die folgenden Windows-Geräte aus der Verwaltung entfernen.  
* Windows 10-Geräte 
* Windows 8.1-Computer
* Windows 8.1-Smartphone
 
Weitere Informationen dazu, was beim Entfernen Ihres Geräts aus der Verwaltung geschieht, finden Sie unter [Was geschieht, wenn Sie Ihr Gerät aus Intune entfernen?](what-happens-if-you-unenroll-your-device-from-intune-windows.md).  

## <a name="remove-your-windows-10-device"></a>Entfernen Ihres Windows 10-Geräts
Führen Sie die folgenden Schritte zum Entfernen eines Windows 10-Geräts aus der Verwaltung aus.

### <a name="remove-in-company-portal-app-home-page"></a>Entfernen in der Unternehmensportal-App, **Startseite**  

1. Öffnen Sie die Unternehmensportal-App.
2. Wechseln Sie auf der **Startseite** nach unten zum Abschnitt **Meine Geräte**.
3. Wählen Sie das Gerät aus, das Sie entfernen möchten.
3. Wählen Sie rechts oben in der App das Symbol **Mehr anzeigen** aus.
4. Wählen Sie **Entfernen** aus. 
5. Wählen Sie zur Bestätigung des Vorgangs **Gerät entfernen** aus.  

### <a name="remove-in-company-portal-app-device-context-menu"></a>Entfernen in der Unternehmensportal-App, Kontextmenü für das Gerät  

1. Öffnen Sie die Unternehmensportal-App, und wechseln Sie zu **Meine Geräte**.

    ![Beispielscreenshot der Unternehmensportal-App für Windows, Startseite mit hervorgehobenem Abschnitt „Meine Geräte“](./media/1809_CheckAccess_Context_Select_Device.png)

2. Klicken Sie mit der rechten Maustaste, oder tippen Sie auf ein Gerät, und halten Sie es gedrückt, um das [Kontextmenü](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus) zu öffnen.  

3. Wählen Sie **Entfernen** aus.  

    ![Beispielscreenshot der Unternehmensportal-App für Windows, Startseite Das Kontextmenü für das Gerät wird im Abschnitt **Meine Geräte** auf der Seite angezeigt und enthält die Aktionen „Umbenennen“, „Entfernen“ und „Zugriff prüfen“.](./media/1809_DeviceContextMenu_Windows_CP.png)  

5. Klicken Sie im Bestätigungsdialogfeld auf **Weitere Informationen**, um mehr darüber zu erfahren, wie sich Ihr Zugriff auf Geschäfts-, Schul- oder Uniressourcen ändern kann. Wählen Sie zur Bestätigung des Vorgangs **Gerät entfernen** aus.   

     ![Beispielscreenshot der Unternehmensportal-App für Windows, Startseite Das Feld „Umbenennen“ erscheint über dem Gerät, in das der Benutzer einen neuen Namen eingeben und auf „Umbenennen“ oder „Abbrechen“ klicken kann.](./media/1808_RemoveDevice_Popup.png)  


### <a name="remove-in-device-settings-app"></a>„Umbenennen“ in der App „Einstellungen“ des Geräts
1. Öffnen Sie die App „Einstellungen“. 
2. Wechseln Sie zu **Konten** > **Auf Arbeits- oder Schulkonto zugreifen**.
3. Wählen Sie das verbundene Konto, das Sie entfernen möchten, und dann **Trennen** aus.
4. Wählen Sie zum Bestätigen des Entfernens des Geräts **Ja** aus.

## <a name="remove-your-windows-81-computer"></a>Entfernen Ihres Windows 8.1-Computers
Führen Sie die folgenden Schritte zum Entfernen eines Windows 8.1-Computers aus Intune aus.

1. Navigieren Sie zu **PC-Einstellungen** > **Netzwerk** > **Arbeitsplatz**.
2. Wählen Sie unter **Arbeitsplatzeinbindung** **Leave** (Verlassen) aus.
3. Wählen Sie unter **Turn on device management** (Geräteverwaltung aktivieren) **Turn off** (Deaktivieren) aus.
4. Wählen Sie im sich öffnenden Popupfenster **Turn off** (Deaktivieren) aus.

## <a name="remove-your-windows-81-phone"></a>Entfernen Ihres Windows 8.1-Smartphones
Führen Sie die folgenden Schritte zum Entfernen eines Windows 8.1-Smartphones aus Intune aus.

1. Wechseln Sie zu **Einstellungen** > **Arbeitsplatz**.
2. Tippen Sie auf das Arbeitsplatzkonto, für das Sie die Registrierung aufheben möchten.
3. Tippen Sie am unteren Bildschirmrand auf **Löschen**.
4. Tippen Sie im Dialogfeld **Konto löschen** auf **Löschen**.  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Entfernen Ihrer persönlichen Informationen nach dem Entfernen des Unternehmensportals  

Es gibt zwei Arten von Daten, die das Unternehmensportal auf Ihrem Windows-Gerät speichert:

- **Diagnoseprotokolle:** von Microsoft erfasste Aktivitätsdaten der Standard-App. Die Daten werden automatisch gelöscht, wenn Sie die Unternehmensportal-App deinstallieren. App-Aktivitätsdaten enthalten z.B. Informationen dazu, wie lange die App geöffnet war oder sie abgestürzt ist.
- **Anwendungscache:** Unterstützungsdateien, die erforderlich sind, damit die App funktioniert, z.B. Symbole und Einstellungen.

Führen Sie einen der folgenden Schritte aus, um die gespeicherten Protokolle und Caches zu löschen:

* [Deinstallieren der Unternehmensportal-App](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) 

* Setzen Sie die Unternehmensportal-App zurück. Öffnen Sie die App **Einstellungen**, und klicken Sie auf **Apps** > **Unternehmensportal** > **Erweiterte Optionen** > **Zurücksetzen**. 

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).
