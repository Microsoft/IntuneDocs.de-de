---
title: Erfassen von Geräteprotokollen
description: Erfahren Sie, wie Sie Protokolle Ihrer verwalteten Geräte sammeln können.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f07947a4064cbd6852edb93ea8d6d17e2c6d9101
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025568"
---
# <a name="device-logs"></a>Geräteprotokolle

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Im Rahmen der Problembehandlung empfiehlt es sich, die Protokolle der Benutzergeräte zu erfassen und zu sammeln. Im Folgenden finden Sie Anleitungen zum Sammeln dieser Protokolle. In der Regel benötigen Sie Zugriff auf das Gerät, um diese Protokolle abzurufen, oder Sie müssen die Benutzer bitten, dass sie die Protokolle sammeln und Ihnen senden.

### <a name="android-logs"></a>Android-Protokolle
Android-Protokolle befinden sich unter *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*.

Manchmal – insbesondere bei neueren Android-Geräten – werden die Dateien nicht angezeigt. In diesem Fall bitten Sie die Benutzer, die Unternehmensportal-App für Android zu öffnen. Anschließend sollen sie **Einstellungen**>**Protokolle kopieren** auswählen und ihr Gerät neu starten.

Weitere Informationen dazu, wie Ihre Benutzer Ihnen Datenprotokolle senden können, finden Sie in folgenden Artikeln:

- [Verwenden der ausführlichen Protokollierung zur Unterstützung Ihres IT-Administrators bei der Behebung von Geräteproblemen](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android): Beschreibt, wie Benutzer die ausführliche Protokollierung aktivieren, die Ihnen automatisch ihre sämtlichen Datenprotokolle sendet. Die ausführliche Protokollierung ist standardmäßig aktiviert.

- [Senden von Diagnosedatenprotokollen an Ihren IT-Administrator per E-Mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android)

- [Senden von Diagnosedatenprotokollen an Ihren IT-Administrator über ein USB-Kabel](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>iOS-Protokolle

Benutzer können Ihnen Fehler beim Registrieren senden. Die entsprechende Vorgehensweise finden Sie unter [Senden von iOS-Registrierungsfehlern an Ihren IT-Administrator](/intune-user-help/send-errors-to-your-it-admin-ios).

Benutzer können wie unter [Send iOS Device Logs (Senden von iOS-Geräteprotokollen)](/intune-user-help/send-logs-to-microsoft-ios) beschrieben, Geräteprotokolle senden.

### <a name="mac-os-x-logs"></a>Mac OS X-Protokolle

1. Öffnen Sie die App **Konsole**.
2. Wählen Sie unter **DATEIEN** die Datei **system.log** aus.
3. Wählen Sie oben auf der Menüleiste **Datei** > **Kopie speichern unter…** aus. Speichern Sie die Datei dann.

### <a name="windows-phone"></a>Windows Phone

In der Windows Phone-Unternehmensportal-App klicken Benutzer auf die drei Punkte (**...**), um das Menü zu öffnen, und wählen dann **Protokolle senden** aus. Diese Option steht vor und nach der Anmeldung bei der Unternehmensportal-App zur Verfügung.

### <a name="windows"></a>Windows

Für das Windows-Unternehmensportal befinden sich die Protokolle unter *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.
