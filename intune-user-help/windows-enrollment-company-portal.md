---
title: Registrieren von Windows-Geräten im Intune-Unternehmensportal | Microsoft-Dokumentation
description: Erste Schritte beim Registrieren eines Windows-Geräts im Unternehmensportal
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86aeb2b54d45f111864d71e65b8c90fce7205868
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508027"
---
# <a name="windows-device-enrollment-in-intune-company-portal"></a>Registrieren von Windows-Geräten im Intune-Unternehmensportal  

Registrieren Sie Ihr Windows-Gerät in der Intune-Unternehmensportal-App, um sicheren Zugriff auf Schul- und Uni-Apps, E-Mails und Dateien zu erhalten. Wenn für die Tätigkeit in Ihrer Organisation bestimmte Apps erforderlich sind oder empfohlen werden (z. B. Office oder OneDrive), erhalten Sie diese entweder während der Registrierung, oder sie stehen nach der Registrierung im Unternehmensportal zur Verfügung.  

Sie können Windows 10-Geräte entweder über die Website *oder* die App des Unternehmensportals registrieren. Wenn Sie ein Gerät mit einer früheren Version von Windows registrieren, müssen Sie das Gerät über die Website des Unternehmensportals registrieren.  

## <a name="install-company-portal-app"></a>Installieren der Unternehmensportal-App  
Sie haben möglicherweise bereits die Unternehmensportal-App auf Ihrem Gerät installiert. Überprüfen Sie, ob die App in der Liste __Alle Apps__ aufgelistet wird.  Wenn das Unternehmensportal nicht in der Liste der Apps angezeigt wird, gehen Sie folgendermaßen vor, um es zu installieren.  

1. Öffnen Sie auf Ihrem Gerät den **Microsoft Store**.

2. Geben Sie im Feld **Suchen** **Unternehmensportal** ein.

3. Wählen Sie in der Liste der Ergebnisse **Unternehmensportal** > **Installieren** aus.

4. Wählen Sie **Installieren** oder **Kostenlos** aus. Zwischen diesen beiden Optionen gibt es keinen Unterschied. Die Anzeige der Wörter hängt davon ab, wie Ihre Organisation die App eingerichtet hat.  

## <a name="find-windows-10-version-number"></a>Suchen von Windows 10-Versionsnummern  
Die Schritte zur Registrierung unterscheiden sich je nach Version der Windows 10-Geräte. In den folgenden Schritten wird beschrieben, wie Sie in Desktop- und mobilen Geräten mit Windows 10 die Versionsnummer ermitteln. Wenn Sie die Version ermittelt haben, können Sie mit den empfohlenen Schritten zur Registrierung fortfahren.  

### <a name="windows-10-desktop-devices"></a>Windows 10 Desktop-Geräte  

1. Öffnen Sie das **Startmenü**.

2. Geben Sie in der Suchleiste „PC-Infos“ ein. Wählen Sie aus den Ergebnissen __PC-Infos__ aus.  


   ![Sucheinstellungen für „PC-Infos“](media/searching_for_about_your_pc.png)  

3. Scrollen Sie nach unten zu **Windows-Spezifikationen**, um die **Version** von Windows 10 zu ermitteln, die auf Ihrem PC installiert ist.  


   ![Windows 10 Desktop „PC-Infos“](media/settings_about_pc.png)  

4. Bei Version  

    * __1607 oder höher:__ Registrieren Sie Ihr Gerät über die Route [**Einstellungen** > **Konto** > **Access work or school** (Zugriff auf Geschäft, Schule oder Uni)](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device).   
    * __1511 oder früher:__ Registrieren Sie Ihr Gerät über die Route [**Einstellungen** > **Konto** > **Your Accounts** (Ihre Konten)](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

### <a name="windows-10-mobile-devices"></a>Windows 10 Mobile-Geräte

1. Wechseln Sie zu __Alle Apps__, und wählen Sie die App __Einstellungen__ aus.
2. Klicken Sie auf __System__ > __Info__.
3. Unter __Device information__ (Geräteinformationen) wird die __Version__ angezeigt.  
4. Bei Version  

    * __1607 oder höher:__ Registrieren Sie Ihr Gerät über die Navigation [**Einstellungen** > **Access work or school** (Zugriff auf Geschäft, Schule oder Uni)](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device).   
    * __1511 oder früher:__ Registrieren Sie Ihr Gerät mithilfe der [Route **Einstellungen** > **Konten**](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

## <a name="enroll-non-windows-10-devices"></a>Registrieren von nicht-Windows 10-basierten Geräten  
In den folgenden Artikeln erfahren Sie, wie Sie über die Website des Unternehmensportals andere von Windows unterstützte Geräte registrieren:   
* [Windows 8.1- oder Windows RT 8.1-Gerät](enroll-your-W81-or-rt81-windows.md)  
* [Windows Phone 8.1-Gerät](enroll-your-wp81-windows.md)    

## <a name="it-administrator-support"></a>Unterstützung für IT-Administratoren  
Wenn Sie IT-Administrator sind und Probleme bei der Registrierung von Geräten haben, lesen Sie [Troubleshooting Windows device enrollment problems in Microsoft Intune (Behandeln von Problemen bei der Registrierung von Windows-Geräten in Microsoft Intune)](https://support.microsoft.com/help/4469913). In diesem Artikel werden häufige Fehler, ihre Ursachen und Schritte zur Behebung aufgelistet.  

## <a name="next-steps"></a>Nächste Schritte  
Da Sie nun wissen, welche Geräte unterstützt werden und die Versionsnummer von Windows 10 kennen, können Sie mit den empfohlenen Artikeln zur Registrierung fortfahren.  
 
Weitere Informationen zur Geräteverwaltung, dem Unternehmensportal und der Verwendung der beiden in Schulen und Unternehmen finden Sie in den folgenden Artikeln:  
* [Verwenden verwalteter Geräte für den Zugriff auf Geschäfts-, Schul- und Uniressourcen](use-managed-devices-to-get-work-done.md)  
* [Was geschieht, wenn Sie Ihr Gerät bei Intune registrieren?](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)  
* [Welche Informationen erhält meine Organisation, wenn ich mein Gerät registriere?](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)  

Benötigen Sie Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. [Besuchen Sie die Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980), um die Kontaktinformationen für die IT-Abteilung Ihrer Organisation zu erhalten.  
