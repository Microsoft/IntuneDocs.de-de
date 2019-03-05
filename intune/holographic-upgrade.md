---
title: Upgrade auf Windows Holographic for Business
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Geräte, die Windows Holographic ausführen, auf Windows Holographic for Business aktualisieren
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2176eda7ce54906c6af5b34cc3db49e21ecda274
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231960"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Aktualisieren von Geräten, die Windows Holographic ausführen, auf Windows Holographic for Business

In Microsoft Intune gibt es viele Einstellungen, die dazu dienen, Ihre Geräte zu verwalten und zu schützen. In diesem Artikel werden die Einstellungen zum Upgraden von Windows Holographic-Geräten auf Windows Holographic for Business aufgelistet und beschrieben. Diese Einstellungen werden in Intune in einem Upgradekonfigurationsprofil erstellt, das auf Geräte übertragen oder für sie bereitgestellt wird.

Als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) verwenden Sie diese Einstellungen, um Ihre Windows Holographic-Geräte zu aktualisieren. Für Microsoft HoloLens können Sie die Commercial Suite erwerben, um die erforderliche Lizenz für das Upgrade zu erhalten. Weitere Informationen finden Sie unter [Entsperren der Features von Windows Holographic für Unternehmen](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise).

Weitere Informationen zu diesem Feature finden Sie unter [Verwenden eines Konfigurationsprofils zum Upgraden von Windows 10 oder Verlassen des S Modus in Intune](edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](edition-upgrade-configure-windows-10.md#create-the-profile)

## <a name="edition-upgrade"></a>Upgrade der Edition

- **Edition, auf die das Upgrade erfolgen soll**: Wählen Sie **Windows 10 Holographic for Business** aus.
- **Lizenzdatei**: Navigieren Sie zu der XML-Lizenzdatei, die für Sie bereitgestellt wurde, und wählen Sie sie aus.

  ![Geben Sie den Namen der XML-Datei ein, die die Holographic for Business-Lizenzinformationen enthält.](media/Holographic-edition-upgrade.png)
 
## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber vielleicht noch keine Aktionen durch. Denken Sie daran, das [Profil zuzuweisen](device-profile-assign.md) und [seinen Status zu überwachen](device-profile-monitor.md).

Sie können auch Editionsupgradeprofile für [Windows 10-Geräte und höher](edition-upgrade-windows-settings.md) erstellen.
