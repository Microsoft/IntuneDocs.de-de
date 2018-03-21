---
title: "Zurücksetzen von Windows 10-Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation"
description: "Verwenden Sie den sauberen Start, um Apps mithilfe von Microsoft Intune von Windows 10 PCs zu entfernen oder zu deinstallieren. Dies umfasst auch vorinstallierte Apps von OEMs. Die Inhalte des Basisordners können beibehalten werden, wenn die Benutzerdaten beibehalten werden sollen."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d17c9dc11791f32f0c2c1e7faa88966c112fc6a5
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2018
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Verwenden der Aktion „Sauberer Start“ zum Zurücksetzen von Windows 10-Geräten mit Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Die Geräteaktion **Sauberer Start** entfernt alle Apps, die auf einem Windows 10-PC mit Creators Update installiert sind. Danach wird der PC automatisch auf die neueste Windows-Version aktualisiert.

Diese Aktion hilft dabei, Apps (von OEMs) zu entfernen, die auf einem neuen PC häufig vorinstalliert sind. Um die Inhalte des Basisordners des Benutzers beizubehalten und nur Apps und Einstellungen zu entfernen, verwenden Sie die Einstellung `if user data is retained`.

> [!IMPORTANT]
> Der saubere Start hebt die Registrierung des Geräts bei Intune auf, das Gerät ist jedoch weiterhin in Azure Active Directory eingebunden.

## <a name="use-fresh-start"></a>Verwenden des sauberen Starts

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte** und dann auf **Alle Geräte**.
4. Wählen Sie aus der Liste der verwalteten Geräte ein Windows 10-Desktopgerät aus, und wählen Sie dann die Option **Sauberer Start** aus.

## <a name="next-steps"></a>Nächste Schritte

Um den Status dieser Aktion anzuzeigen, wählen Sie **Geräteaktionen** (**Microsoft Intune** > **Geräte**) aus.