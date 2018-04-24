---
title: Zurücksetzen von Windows 10-Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie den sauberen Start, um Apps mithilfe von Microsoft Intune von Windows 10 PCs zu entfernen oder zu deinstallieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5658bf2e1ee250ef9fd405b3f7ec1772b166f338
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Verwenden der Aktion „Sauberer Start“ zum Zurücksetzen von Windows 10-Geräten mit Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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