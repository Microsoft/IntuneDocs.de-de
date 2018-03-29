---
title: Erstellen von Geräteprofilen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hinzufügen oder Konfigurieren eines Geräteprofils in Microsoft Intune sowie Auswahl des Plattformtyps und der Konfiguration der Einstellungen innerhalb des Azure-Portals
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e5070052c0d4cce3cfd81a7bae259bc7dfb22e7f
ms.sourcegitcommit: e6319ff186d969da34bd19c9730ba003d6cce353
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2018
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Erstellen eines Geräteprofils in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>Erstellen des Profils
1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, und suchen Sie nach **Microsoft Intune**.

2. Wählen Sie in **Microsoft Intune** die Option **Gerätekonfiguration** und anschließend **Profile** aus. Klicken Sie dann auf **Profil erstellen**.

3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
    - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein (Optional, jedoch empfohlen).
    - **Plattform**: Wählen Sie den Plattformtyp aus:  

        - **Android**
        - **Android for Work**
        - **iOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 und höher**
        - **Windows 10 und höher**

    - **Profiltyp:** Wählen Sie den Typ aus, den Sie erstellen möchten. Die Liste variiert je nach ausgewählter Plattform.
    - **Einstellungen:** In den folgenden Themen werden die Einstellungen für die einzelnen Profiltypen beschrieben:

        -  [Gerätefunktionseinstellungen](device-features-configure.md)
        -  [Einstellungen für Geräteeinschränkungen](device-restrictions-configure.md)
        -  [E-Mail-Einstellungen](email-settings-configure.md)
        -  [VPN-Einstellungen](vpn-settings-configure.md)
        -  [WLAN-Einstellungen](wi-fi-settings-configure.md)
        -  [Einstellungen für Windows 10-Editionsupgrades](edition-upgrade-configure-windows-10.md)
        -  [Zertifikateinstellungen](certificates-configure.md)
        -  [Windows Information Protection-Einstellungen](windows-information-protection-configure.md)
        -  [Education-Einstellungen](education-settings-configure.md)
        -  [Benutzerdefinierte Einstellungen](custom-settings-configure.md)

    ![Screenshot „Profil erstellen“](./media/create-device-profile.png)

4. Wählen Sie **Erstellen** aus, wenn Sie fertig sind.

Das Profil wird erstellt und in der Liste angezeigt.


## <a name="next-steps"></a>Nächste Schritte
Informationen zum Zuweisen von Geräteprofilen finden Sie unter [Zuweisen von Geräteprofilen mit Microsoft Intune](device-profile-assign.md).
