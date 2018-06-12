---
title: Erstellen von Geräteprofilen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hinzufügen oder Konfigurieren eines Geräteprofils in Microsoft Intune sowie Auswahl des Plattformtyps und der Konfiguration der Einstellungen innerhalb des Azure-Portals
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3f62e306574606ffa1eb1e6f242c3cb30b1a9c1b
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744651"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Erstellen eines Geräteprofils in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>Erstellen des Profils
1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, und suchen Sie nach **Microsoft Intune**.

2. Wählen Sie in **Microsoft Intune** die Option **Gerätekonfiguration** und anschließend **Profile** aus. Klicken Sie dann auf **Profil erstellen**.

3. Geben Sie die folgenden Eigenschaften ein:

   - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
   - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. (Optional, jedoch empfohlen)
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

       -  [Gerätefeatures](device-features-configure.md)
       -  [Geräteeinschränkungen](device-restrictions-configure.md)
       -  [Endpoint Protection](endpoint-protection-configure.md)
       -  [Kiosk](kiosk-settings.md)
       -  [E-Mail](email-settings-configure.md)
       -  [VPN](vpn-settings-configure.md)
       -  [WLAN](wi-fi-settings-configure.md)
       -  Education für [Windows 10](education-settings-configure.md) und [iOS](wi-fi-settings-ios.md)
       -  [Windows 10-Editionsupgrade](edition-upgrade-configure-windows-10.md)
       -  [iOS Update-Richtlinien](software-updates-ios.md)
       -  [Zertifikate](certificates-configure.md)
       -  [Windows Information Protection](windows-information-protection-configure.md)
       -  [Benutzerdefiniert](custom-settings-configure.md)

     ![Screenshot „Profil erstellen“](./media/create-device-profile.png)

4. Wählen Sie **Erstellen** aus, wenn Sie fertig sind.

Das Profil wird erstellt und in der Liste angezeigt.

## <a name="next-steps"></a>Nächste Schritte
[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
