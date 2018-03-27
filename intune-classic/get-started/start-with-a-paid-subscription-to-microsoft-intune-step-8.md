---
title: Aktivieren der Geräteregistrierung
description: Legen Sie die MDM-Autorität fest, und aktivieren Sie die Registrierung für iOS-, Windows-, Android- und Mac-Geräte.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 02/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e9572181fb15ec97e7ae4c11a8ab2e4fe4cc9b30
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="enable-enrollment-for-mobile-devices"></a>Aktivieren der Registrierung für mobile Geräte

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

In diesem Thema wird beschrieben, wie ein Intune-Administrator die Registrierung mobiler Geräte aktivieren kann. Hilfe zur Verwendung von Intune auf Ihrem Telefon finden Sie unter [Verwenden verwalteter Geräte zum Erledigen von Aufgaben](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions).

Um die Verwaltung mobiler Geräte mit Intune einzurichten, müssen Sie zunächst die *Autorität für die Verwaltung mobiler Geräte* (Mobile Device Management, MDM) festlegen, die den Dienst identifiziert, der Ihrem Konto zugeordnete Geräte verwalten kann. In diesem Leitfaden wird vorausgesetzt, dass Sie nicht den System Center Configuration Manager, sondern den Intune-Dienst verwenden. Nachdem die MDM-Autorität festgelegt wurde, können Sie die Verwaltung für Geräteplattformen aktivieren und Ihre Geräte mit der Unternehmensportal-App registrieren.

## <a name="enable-device-enrollment"></a>Aktivieren der Geräteregistrierung

1. **Festlegen von Intune als Verwaltungsstelle für mobile Geräte**: Klicken Sie in der [Intune-Verwaltungskonsole](https://manage.microsoft.com/) auf **Verwaltung** > **Verwaltung mobiler Geräte**. Wählen Sie anschließend unter **Aufgaben** die Option **MDM-Autorität festlegen** aus.  

2. Klicken Sie im Dialogfeld „MDM-Autorität“ auf **Ja**.

    ![Verwaltungskonsole – MDM auf „Intune“ festlegen](../media/intune-mdm-authority.png)

## <a name="choose-how-to-enroll-devices"></a>Auswählen der Registrierungsmethode für Geräte

Intune kann je nach Unternehmensanforderungen Geräte in unterschiedlicher Weise verwalten. Zu den verfügbaren Registrierungsszenarien gehören beispielsweise BYOD (Bring Your Own Device), unternehmenseigene Geräte, CYOD (Choose Your Own Device) und Geräte im Kioskmodus.

Führen Sie diese Schritte zum [Auswählen der Registrierungsmethode für Geräte](choose-how-to-enroll-devices1.md) aus.

## <a name="enable-mdm-for-your-device-platform"></a>Aktivieren von MDM für Ihre Geräteplattform
Die Registrierung muss für iOS-, Mac- und Android for Work-Geräte aktiviert werden, indem eine Beziehung zwischen dem Plattformanbieter und Ihrem Intune-Mandanten eingerichtet wird. Für Windows- und Android-Geräte sind keine zusätzlichen Schritte erforderlich, aber für Windows-Geräte können Sie die Geräteregistrierung für Ihre Benutzer vereinfachen, indem Sie einen besonderen DNS-Registrierungseintrag erstellen.

Aktivieren Sie die Geräteregistrierung für die Geräteplattform, die Sie verwalten möchten. Je nach Plattform sind andere Anforderungen relevant:

- [iOS und Mac OS](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
- [Windows 10 und Windows Phone](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune)
- [Windows-PC](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) (Intune-Software-Client)
- [Android for Work](/intune-classic/deploy-use/set-up-android-for-work)

Sobald die Registrierung aktiviert wurde, können Benutzer die Unternehmensportal-App auf ihr Gerät herunterladen und den Vorgang zur Geräteregistrierung durchführen.

### <a name="enable-company-owned-device-enrollment"></a>Aktivieren der Registrierung für unternehmenseigene Geräte
Sie können auch verschiedene Szenarien für die [Registrierung unternehmenseigener Geräte](/intune-classic/deploy-use/manage-corporate-owned-devices) unterstützen, darunter:
- [Apple-Geräteregistrierungsprogramm](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
- [Registrierung über den Setup-Assistenten für Apple Configurator](/intune-classic/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
- [Apple Configurator – Direkte Registrierung](/intune-classic/deploy-use/ios-direct-enrollment-in-microsoft-intune)
- [Geräteregistrierungs-Manager](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

### <a name="next-steps"></a>Nächste Schritte
Gratulation! Sie haben den letzten Schritt der Kurzanleitung *Erste Schritte mit Intune* abgeschlossen. Ihre anfängliche Konfiguration ist jetzt abgeschlossen, und Sie können in Betracht ziehen, weitere MDM-Funktionen zu aktivieren.

>[!div class="step-by-step"]
>[&larr; **Registrieren von Geräten**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)     [**Aufgaben nach der Konfiguration** &rarr;](.\post-configuration-tasks.md)  
