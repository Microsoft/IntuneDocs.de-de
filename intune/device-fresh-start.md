---
title: "Zurücksetzen von Windows 10-Geräten mit Intune"
titlesuffix: Azure portal
description: "Erfahren Sie, wie Sie die Aktion „Sauberer Start“ verwenden, um Windows 10-PCs zurückzusetzen, auf denen Intune ausgeführt wird.\""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c45d3e47c90ca7739b3aa6eee1bf31d787a82264
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2018
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Verwenden der Aktion „Sauberer Start“ zum Zurücksetzen von Windows 10-Geräten mit Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Die Geräteaktion **Sauberer Start** entfernt alle Apps, die auf einem Windows 10-PC mit Creators Update installiert wurden, und aktualisiert den PC dann automatisch auf die neueste Windows-Version.
Mit dieser Aktion können vorinstallierte OEM-Apps entfernt werden, die oft mit einem neuen PC geliefert werden. Sie können konfigurieren, ob Benutzerdaten beibehalten werden, wenn diese Geräteaktion ausgegeben wird. In diesem Fall werden alle Apps und Einstellungen entfernt, die Inhalte des Basisordners des Benutzers bleiben jedoch erhalten.

## <a name="how-to-use-fresh-start"></a>So verwenden Sie Fresh Start

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie im Bereich **Intune** die Option **Geräte** aus.
4. Wählen Sie im Bereich **Geräte** die Option **Alle Geräte** aus.
5. Wählen Sie aus der Liste der verwalteten Geräte ein Windows 10-Desktopgerät aus, und wählen Sie dann die Remotegeräteaktion **Sauberer Start**.

## <a name="next-steps"></a>Nächste Schritte

Um den Status der gerade ausgeführten Aktion anzuzeigen, wählen Sie im Bereich **Geräte und Gruppen** die Option **Geräteaktionen** aus.

