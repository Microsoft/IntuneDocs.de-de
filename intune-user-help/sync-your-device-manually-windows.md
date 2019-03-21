---
title: Manuelles Synchronisieren Ihres Windows-Geräts | Microsoft-Dokumentation
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30135c69b95ba9731682af52ad0da3bb9df193e9
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57335070"
---
# <a name="sync-your-windows-device-manually"></a>Manuelles Synchronisieren des Windows-Geräts

Wenn die Geschwindigkeit der App-Installation nicht optimal ist, können Sie eine manuelle Gerätesynchronisierung initiieren. Bei manuellen Synchronisierungen wird erzwungen, dass Ihr Gerät eine Verbindung mit Intune herstellt, um die neuesten Updates und die aktuelle Kommunikation zu erhalten. Die Installationsgeschwindigkeit kann sich nach Abschluss der Gerätesynchronisierung erhöhen.

Intune unterstützt die manuelle Synchronisierung über die Unternehmensportal-App, die Desktoptaskleiste oder das Startmenü und über die Geräte-App „Einstellungen“. Die Funktionen der Unternehmensportal-App werden auf Windows 10-Geräten unterstützt, auf denen Creators Update (1703) oder höher ausgeführt wird. 

Über die Geräte-App „Einstellungen“ können alle Windows-Geräte synchronisiert werden, einschließlich:

* [Windows 10 Desktop](#windows-10-desktop)  
* [Microsoft HoloLens](#microsoft-hololens)   
* [Windows 10 Mobile](#windows-10-mobile)  
* [Windows Phone 8.1](#windows-phone-81)    

## <a name="sync-directly-from-company-portal-app-for-windows"></a>Direktes Synchronisieren über die Unternehmensportal-App für Windows
Führen Sie die folgenden Schritte aus, um Windows 10-Geräte, auf denen Creators Update (Version 1703) oder höher ausgeführt wird, manuell zu synchronisieren.

1.  Öffnen Sie die Unternehmensportal-App auf Ihrem Gerät.

2.  Wählen Sie **Einstellungen** > **Synchronisierung** aus.

    ![Screenshot der Startseite der Unternehmensportal-App, „Einstellungen“ hervorgehoben](./media/RS1_homePage_settings_04.png)  
    
    ![Screenshot der Seite „Einstellungen“ der Unternehmensportal-App, Schaltfläche „Synchronisierung“ hervorgehoben](./media/RS1_settingspage_sync05.png)  

## <a name="sync-from-device-taskbar-or-start-menu"></a>Synchronisieren über die Gerätetaskleiste oder das Startmenü   

Sie können über den Desktop Ihres Geräts auch außerhalb der App auf die Synchronisierungssteuerung zugreifen. Dies ist nützlich, wenn Sie die App direkt an Ihre Taskleiste oder das Startmenü angeheftet haben und eine schnelle Synchronisierung durchführen möchten.  

1. Suchen Sie das Symbol der Unternehmensportal-App auf Ihrer Taskleiste oder in Ihrem Startmenü.  
2. Klicken Sie mit der rechten Maustaste auf das Symbol der App, sodass deren Menü (das sogenannte Kontextmenü) angezeigt wird.  

    ![Screenshot der Windows-Taskleiste auf dem Desktop eines Geräts Es wurde auf das Symbol der Unternehmensportal-App geklickt, um ein Menü mit den Optionen „An Taskleiste anheften“, „Fenster schließen“ und „Dieses Gerät synchronisieren“ anzuzeigen.](./media/sync-device-from-start-menu-1807.png)  

3. Wählen Sie **Dieses Gerät synchronisieren** aus. Die Unternehmensportal-App wird geöffnet und zeigt die Seite **Einstellungen** an. Außerdem wird die Synchronisierung gestartet.  

## <a name="sync-from-settings-app"></a>Synchronisieren über die App „Einstellungen“ 
Führen Sie die folgenden Schritte aus, um Ihre Microsoft HoloLens-, Windows 10 Desktop-, Windows 10 Mobile- oder Windows Phone 8.1-Geräte über die App „Einstellungen“ manuell zu synchronisieren.  

### <a name="windows-10-desktop"></a>Windows 10 Desktop
1. Wählen Sie auf Ihrem Gerät die Optionen **Start** > **Einstellungen** aus.

2. Wählen Sie **Konten** aus.

    ![Auswählen von Konten auf der Seite „Einstellungen“](./media/win10pc-sync-2-settings-accounts.png)  

3. Für Desktops gibt es mehrere Versionen von Windows 10. Vergleichen Sie Ihren Bildschirm mit den nachstehenden Screenshots, um zu bestimmen, welche Schritte Sie ausführen müssen. 

    * Wenn auf Ihrem Bildschirm die Option **Zugriff auf Geschäfts-, Schul- oder Unikonto** angezeigt wird, fahren Sie mit den Schritten unter [Zugriff auf Geschäfts-, Schul- oder Unikonto](#access-work-or-school-steps) fort.

    ![Option „Zugriff auf Geschäfts-, Schul- oder Unikonto“ in der App „Einstellungen“](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

    * Wenn auf Ihrem Bildschirm die Option **Arbeitsplatzzugriff** angezeigt wird, fahren Sie mit den Schritten unter [Arbeitsplatzzugriff](#work-access-steps) fort.  

    ![Auswählen des Arbeitsplatzzugriffs als den Kontotyp](./media/win10pc-sync-3-work-access.png)

#### <a name="access-work-or-school-steps"></a>Auszuführende Schritte bei Anzeige von „Zugriff auf Geschäfts-, Schul- oder Unikonto“

1. Klicken Sie auf **Zugriff auf Geschäfts-, Schul- oder Unikonto**.

    ![Screenshot mit der Option „Zugriff auf Geschäfts-, Schul- oder Unikonto“](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

2. Wählen Sie das Konto aus, neben dem ein Aktentaschensymbol angezeigt wird. Wenn dieses Konto nicht angezeigt wird, hat Ihr Unternehmen Ihre Einstellungen möglicherweise anders konfiguriert. Klicken Sie dann stattdessen auf das Konto, neben dem ein Microsoft-Logo angezeigt wird.

     ![Auswählen Ihres Kontonamens neben der Aktentasche oder dem Microsoft-Logo](./media/win10pc-rs1-sync-info-button.png)

3. Klicken Sie auf **Info**. 

4. Klicken Sie auf **Synchronisierung**. 

#### <a name="work-access-steps"></a>Auszuführende Schritte bei Anzeige von „Arbeitsplatzzugriff“

1.  Klicken Sie auf **Arbeitsplatzzugriff**.

    ![Auswählen des Arbeitsplatzzugriffs als den Kontotyp](./media/win10pc-sync-3-work-access.png)

2. Wählen Sie unter **Bei Geräteverwaltung registrieren** den Namen Ihres Unternehmens aus.

    ![Auswählen des Firmennamens für die Geräteverwaltung aus](./media/win10pc-sync-4-tap-com-name.png)

3. Klicken Sie auf **Synchronisierung**. Die Schaltfläche bleibt bis zum Abschluss der Synchronisierung deaktiviert.

    ![Auswählen der Schaltfläche „Synchronisieren“](./media/win10pc-sync-5-tap-sync.png)  


### <a name="windows-10-mobile"></a>Windows 10 Mobile

   1. Wechseln Sie auf Ihrem Gerät zu **Alle Apps** > **Einstellungen** > **Konten**.

       ![Auswählen von Konten auf dem Bildschirm „Einstellungen“](./media/win10m-sync-1-settings-accounts.png)

   2. Wählen Sie **Arbeitsplatzzugriff** aus.

       ![Auswählen des Arbeitsplatzzugriffs als den Kontotyp](./media/win10m-sync-2-work-access.png)

   3. Wählen Sie unter **Für Geräteverwaltung registrieren** den Namen Ihres Unternehmens aus.

       ![Auswählen des Firmennamens für die Geräteverwaltung aus](./media/win10m-sync-3-tap-comp-name.png)

   4. Wählen Sie das Symbol **Synchronisierung** aus. Die Schaltfläche bleibt bis zum Abschluss der Synchronisierung deaktiviert.

       ![Auswählen des „Sync“-Symbols](./media/win10m-sync-4-tap-sync.png)  
### <a name="microsoft-hololens"></a>Microsoft HoloLens  
Diese Anweisungen gelten für HoloLens-Geräte, auf denen das Windows 10 Anniversary Update (auch bekannt als RS1) ausgeführt wird. 
1.  Öffnen Sie die App „Einstellungen“ auf Ihrem Gerät.  

2.  Wählen Sie **Konten** > **Arbeitsplatzzugriff** aus.  
    ![Screenshot der HoloLens-App „Einstellungen“, Link „Konten“ hervorgehoben](./media/RS1_holoLens_SettingsRS1_Accounts_06.png)  

3.  Wählen Sie Ihr verbundenes Konto > **Synchronisierung** aus. ![Screenshot der HoloLens-App „Einstellungen“, Schaltfläche „Synchronisierung“ hervorgehoben](./media/RS1_holoLens_SyncRS1_Sync_08.png)  

### <a name="windows-phone-81"></a>Windows Phone 8.1

1. Wechseln Sie zu **Alle Apps** > **Einstellungen** > **Arbeitsplatz**.

    ![Liste der Einstellungen](./media/wp81-1-sync-settings-workplace.png)

2. Wählen Sie den Namen Ihres Unternehmens aus.

    ![Auswählen des Namens des Unternehmens für das Unternehmensbereichskonto](./media/wp81-2-sync-tap-compname.png)

3. Wählen Sie das Symbol **Synchronisierung** aus.

    ![Auswählen des „Sync“-Symbols](./media/wp81-3-sync-tap-sync-button.png)

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).
