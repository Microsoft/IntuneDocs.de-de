---
title: Bereitstellen von Richtlinien und Apps
description: Sie können Richtlinieneinstellungen aktivieren und Apps bereitstellen, die angewendet werden, sobald die Geräte für die Verwaltung registriert wurden.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 02/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3da91a23a3aaa7da4f914bb04eda9a2f640db733
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="create-policies-and-publish-apps"></a>Erstellen von Richtlinien und Veröffentlichen von Apps

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

In diesem Thema erfahren Administratoren, wie Sie Richtlinien erstellen und Apps veröffentlichen können, die sie für verwaltetet Geräte bereitstellen können.

Bevor Sie Apps in Intune registrieren, können Sie Richtlinieneinstellungen und Apps aktivieren, die bereitgestellt werden, sobald diese Geräte der Verwaltung hinzugefügt werden. Mit Intune-Richtlinien stehen Einstellungen bereit, mit deren Hilfe Sie die Sicherheitseinstellungen auf mobilen Geräten steuern, die Windows-Firewall- und Endpoint Protection-Einstellungen für Computer warten und Anwendungen bereitstellen können. Sie können Richtlinien konfigurieren, Apps hinzufügen und diese Apps bereitstellen, damit Geräte die Einstellungen und Apps empfangen, sobald sie in Intune registriert werden.

Richtlinien und Apps sind plattformspezifisch.

## <a name="manage-device-settings"></a>Verwalten von Geräteeinstellungen

 Richtlinieneinstellungen für Geräte werden plattformbasiert konfiguriert und verwaltet. Die folgenden Links enthalten Listen der verfügbaren Einstellungen für deren jeweilige Plattformen:

- [iOS](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)
- [Android und Samsung KNOX Standard](/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune)
- [Android for Work](/intune-classic/deploy-use/android-for-work-policy-settings-in-microsoft-intune)
- [Windows 10 (PC und mobil)](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)
- [Windows 8.1](/intune-classic/deploy-use/windows-configuration-policy-settings-in-microsoft-intune)
- [Windows Phone 8.1](/intune-classic/deploy-use/windows-phone-8-1-policy-settings-in-microsoft-intune)
- [Windows Team](/intune-classic/deploy-use/windows-team-configuration-policy-settings-in-microsoft-intune)
- [Windows-PCs, auf denen die Intune-Clientsoftware ausgeführt wird](/intune-classic/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)

Weitere Informationen finden Sie unter [Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies).

## <a name="add-and-deploy-apps"></a>Hinzufügen und Bereitstellen von Apps

Sie können Apps zu Intune hinzufügen und sie dann auf zwei Arten auf verwalteten Geräten bereitstellen:
- **Erforderliche Installation**: Die Apps werden automatisch auf den verwalteten Geräten installiert.
- **Verfügbare Installation**: Die Apps werden im Intune-Unternehmensportal angezeigt und die Benutzer können auswählen, ob sie die Apps auf ihren Geräten installieren möchten.

### <a name="add-apps"></a>Hinzufügen von Apps

Zunächst müssen Sie die Apps mithilfe einer der folgenden Methoden in Intune verfügbar machen:
- [Hinzufügen von Apps für registrierte Geräte](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)
- [Hinzufügen von Apps für Intune-Softwareclient-PCs](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)

### <a name="deploy-apps"></a>Bereitstellen von Apps

Sobald die App in Intune zur Verfügung steht, können Sie sie auf verwalteten Geräten bereitstellen:
- [Bereitstellen von Apps auf Geräten](/intune-classic/deploy-use/deploy-use/deploy-apps-in-microsoft-intune)
- Bereitstellen von Apps aus einem Volumenprogramm:
    - [iOS: Volume Purchase Program (VPP)](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)
    - [Microsoft Store für Unternehmen](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)
    - [Android for Work](/intune-classic/deploy-use/android-for-work-apps)

    Nachdem Sie die Apps für die Bereitstellung konfiguriert haben, können Sie [Apps konfigurieren](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune).

>[!div class="step-by-step"]

>[&larr; **Organisieren von Benutzern und Geräten**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)[**Anpassen des Unternehmensportals** &rarr;](/intune/company-portal-customize)  
