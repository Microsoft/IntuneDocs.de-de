---
title: Erstellen von Geräteprofilen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hinzufügen oder Konfigurieren eines Geräteprofils in Microsoft Intune sowie Auswahl des Plattformtyps und der Konfiguration der Einstellungen innerhalb des Azure-Portals
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aaa8692a17e7e78378905e79b4046727d91c7c92
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238879"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Erstellen eines Geräteprofils in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>Erstellen des Profils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.

2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.

3. Geben Sie die folgenden Eigenschaften ein:

   - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
   - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
   - **Plattform**: Wählen Sie den Plattformtyp aus:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 und höher**
       - **Windows 10 und höher**

   - **Profiltyp**: Wählen Sie den Typ aus, den Sie erstellen möchten. Die Liste variiert je nach ausgewählter Plattform.
   - **Einstellungen:** Die folgenden Artikel beschreiben die Einstellungen für die einzelnen Profiltypen:

       -  [Gerätefeatures](device-features-configure.md)
       -  [Geräteeinschränkungen](device-restrictions-configure.md)
       -  [Endpoint Protection](endpoint-protection-configure.md)
       -  [Identity Protection](identity-protection-configure.md)  
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
