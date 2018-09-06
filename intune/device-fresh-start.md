---
title: Zurücksetzen von Windows 10-Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie den sauberen Start, um Apps mithilfe von Microsoft Intune von Windows 10 PCs zu entfernen oder zu deinstallieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6b66cd00f734cab3ca85f6d87f056f8c482a377d
ms.sourcegitcommit: 2811df0f851ca6b08f6ae8c926fb2e6971c41690
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "40251732"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Verwenden der Aktion „Sauberer Start“ zum Zurücksetzen von Windows 10-Geräten mit Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Die Geräteaktion **Sauberer Start** entfernt alle Apps, die auf einem PC unter Windows 10, Version 1703 oder höher, installiert wurden. „Sauberer Start“ hilft dabei, Apps (von OEMs) zu entfernen, die auf einem neuen PC häufig vorinstalliert sind.  

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an, und wechseln Sie zu > **Microsoft Intune** > **Geräte** > **Alle Geräte**.
2. Wählen Sie aus der Liste der verwalteten Geräte ein Windows 10-Desktopgerät aus.
3. Klicken Sie auf **Sauberer Start**. 
4. Wählen Sie **Benutzerdaten auf diesem Gerät beibehalten** aus, um Folgendes zu ermöglichen:
   * Azure AD für das Gerät bleibt eingebunden.
    * Das Gerät bleibt bei der mobilen Geräteverwaltung registriert. 
    * Die Inhalte des Basisordners des Gerätebenutzers werden beibehalten, und Apps und Einstellungen werden entfernt.  
  > [!IMPORTANT]
 > Wenn Sie die Benutzerdaten nicht beibehalten, wird das Gerät auf seinen standardmäßigen Zustand wiederhergestellt. Seine Registrierung bei Azure AD und der mobilen Geräteverwaltung wird aufgehoben. 
 
5. Klicken Sie auf **OK**.   
6. Wenn Sie den Status dieser Aktion anzeigen möchten, wechseln Sie zu **Geräte**, und klicken Sie auf **Geräteaktionen**.  
