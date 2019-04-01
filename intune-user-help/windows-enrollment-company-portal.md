---
title: Windows-geräteregistrierung im Intune-Unternehmensportal | Microsoft-Dokumentation
description: Erste Schritte beim Registrieren eines Windows-Geräts im Unternehmensportal
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/12/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: a637b6eed162243d2be81ac08fbcc055e1fd5816
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2019
ms.locfileid: "58069178"
---
# <a name="windows-device-enrollment-in-intune-company-portal"></a>Windows-geräteregistrierung im Intune-Unternehmensportal  

Registrieren Sie Ihres Windows-Geräts bei Intune-Unternehmensportal-app zum sicheren Zugriff auf Geschäfts- und UNI-apps, e-Mails und Dateien. Wenn Ihre Organisation erforderlich sind oder bestimmte apps empfiehlt, z. B. Office oder OneDrive, Sie entweder erhalten sie während der Registrierung oder werden nach der Registrierung im Unternehmensportal zur Verfügung.  

Sie können Windows 10-Geräte über die Unternehmensportal-Website registrieren *oder* app. Wenn Sie ein Gerät mit einer früheren Version von Windows registrieren, müssen Sie das Gerät über die Unternehmensportal-Website registrieren.  

## <a name="install-company-portal-app"></a>Install-Unternehmensportal-app  
Sie haben möglicherweise bereits die Unternehmensportal-app auf Ihrem Gerät installiert. Überprüfen Sie für die app in Ihrem __alle apps__ Liste.  Wenn das Unternehmensportal nicht in der Liste der Apps angezeigt wird, gehen Sie folgendermaßen vor, um es zu installieren.  

1. Open **Microsoft Store** auf Ihrem Gerät.

2. In der **Suche** Feld **Unternehmensportal**.

3. Wählen Sie in der Liste der Ergebnisse **Unternehmensportal** > **Installieren** aus.

4. Wählen Sie **Installieren** oder **Kostenlos** aus. Es ist kein Unterschied zwischen diesen beiden Optionen aus. die Wörter angezeigt, basierend auf der app wie Ihre Organisation eingerichtet.  

## <a name="find-windows-10-version-number"></a>Suchen Sie die Versionsnummer für Windows 10  
Schritte zur Registrierung für verschiedene Versionen von Windows 10-Geräten unterscheiden. Die folgenden Schritte beschreiben, wie Sie die Versionsnummer für Windows 10 Desktop- und mobile Geräte. Nachdem Sie Ihre Version kennen, weiterhin die empfohlene Registrierungsschritte.  

### <a name="windows-10-desktop-devices"></a>Windows 10 Desktop-Geräte  

1. Öffnen Sie das **Startmenü**.

2. Geben Sie in der Suchleiste den Ausdruck "PC-Infos." Wählen Sie __über Ihren PC__ aus den Ergebnissen.  


   ![Sucheinstellungen für „PC-Infos“](media/searching_for_about_your_pc.png)  

3. Führen Sie einen Bildlauf nach unten zum **Windows-Spezifikationen** finden die **Version** von Windows 10, die auf Ihrem PC installiert ist.  


   ![Windows 10 Desktop „PC-Infos“](media/settings_about_pc.png)  

4. Wenn Ihre version  

    *  __1607 oder höher__: Registrieren Ihres Geräts über die [ **Einstellungen** > **Konto** > **Zugriff auf Geschäfts-, Schul- oder unikonto**Route](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device).   
    * __1511 oder früher__: Registrieren Ihres Geräts über die [ **Einstellungen** > **Konto** > **Ihre Konten** Route](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

### <a name="windows-10-mobile-devices"></a>Windows 10 Mobile-Geräte       

1.  Wechseln Sie zu __alle apps__ , und wählen Sie die __Einstellungen__ app.  
2.  Klicken Sie auf __System__ > __Info__.      
3.  Klicken Sie unter __Geräteinformationen__, finden Sie die __Version__.  
4. Wenn Ihre version  

    *  __1607 oder höher__: Registrieren Ihrer Geräte mithilfe der [ **Einstellungen** > **Zugriff auf Geschäfts-, Schul- oder unikonto** Route](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device).   
    * __1511 oder früher__: Registrieren Ihrer Geräte mithilfe der [ **Einstellungen** > **Konten** Route](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

## <a name="enroll-non-windows-10-devices"></a>Registrieren Sie Geräte ohne Windows 10  
Verwenden Sie die folgenden Artikeln, um die anderen unterstützten Windows-Geräte über die Unternehmensportal-Website zu registrieren:   
* [Windows 8.1- oder Windows RT 8.1-Gerät](enroll-your-W81-or-rt81-windows.md)  
* [Windows Phone 8.1-Gerät](enroll-your-wp81-windows.md)    

## <a name="next-steps"></a>Nächste Schritte  
Nun, dass Sie die unterstützten Geräte und die Nummer Ihrer Windows 10-Version kennen, fahren Sie mit der empfohlenen Registrierung Artikel fort.  
 
Weitere Informationen zur geräteverwaltung finden Sie unter Unternehmensportal-App, und wie beide in Schulen und bei der Arbeit verwendet werden in den folgenden Artikeln:  
* [Verwenden verwalteter Geräte für den Zugriff auf Geschäfts-, Schul- und Uniressourcen](use-managed-devices-to-get-work-done.md)  
* [Was geschieht, wenn Sie Ihr Gerät bei Intune registrieren?](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)  
* [Welche Informationen erhält meine Organisation, wenn ich mein Gerät registriere?](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)  

Benötigen Sie Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. [Wechseln Sie zur Website Unternehmensportals](https://go.microsoft.com/fwlink/?linkid=2010980) Ihrer Organisation finden IT wenden Sie sich an Informationen.  
