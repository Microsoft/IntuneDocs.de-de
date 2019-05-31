---
title: Umbenennen eines Windows-Geräts mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Benennen Sie ein Windows-Gerät mithilfe von Microsoft Intune um.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8dfdc3641d583fc045346034ee8543feff1e7cbf
ms.sourcegitcommit: 1144247aa7f042eb1b99d8fd8dd17b909eae38c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2019
ms.locfileid: "59567100"
---
# <a name="rename-a-windows-device-in-intune"></a>Umbenennen eines Windows-Geräts in Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Mithilfe der Aktion **Gerät umbenennen** können Sie ein unternehmenseigenes Windows-Gerät umbenennen, das bei Intune registriert ist. Der Name des Geräts wird sowohl in Intune als auch auf dem Gerät geändert. 

Dieses Feature unterstützt derzeit nicht das Umbenennen von Windows-Geräten mit Azure AD Hybrid.

## <a name="rename-a-device"></a>Umbenennen eines Geräts

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte** > **Alle Geräte**, und wählen Sie ein Windows-Gerät aus. Klicken Sie dann auf **Mehr** > **Gerät umbenennen**.
4. Geben Sie auf dem Blatt **Gerät umbenennen** den neuen Namen in das Textfeld ein. Sie können Buchstaben, Zahlen und Bindestriche verwenden. Der Name muss mindestens einen Buchstaben oder Bindestrich enthalten.
5. Wenn Sie das Gerät nach dem Umbenennen neu starten möchten, wählen Sie neben **Restart after rename** (Nach Umbenennung neu starten) die Option **Ja** aus.
6. Klicken Sie auf **Umbenennen**.



## <a name="next-steps"></a>Nächste Schritte

Der Status der Aktion **Umbenennen** des Geräts wird auf dessen **Übersichtsseite** angezeigt.
