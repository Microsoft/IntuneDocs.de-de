---
title: Umbenennen eines Geräts mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Benennen Sie ein Gerät mithilfe von Microsoft Intune um.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35fae5ea1b3294772db4f4db51179892e08ed5d1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728506"
---
# <a name="rename-a-device-in-intune"></a>Umbenennen eines Geräts in Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Mithilfe der Aktion **Gerät umbenennen** können Sie ein Gerät umbenennen, das bei Intune registriert ist. Der Name des Geräts wird sowohl in Intune als auch auf dem Gerät geändert.

Sie können die folgenden Gerätetypen umbenennen:
- Unternehmenseigene Windows-Geräte 
- Überwachte iOS-Geräte
- Unternehmenseigene macOS 10-Geräte

Dieses Feature unterstützt derzeit nicht das Umbenennen von Windows-Geräten mit Azure AD Hybrid.

## <a name="rename-a-device"></a>Umbenennen eines Geräts

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Klicken Sie auf **Geräte** > **Alle Geräte**, und wählen Sie ein Gerät aus. Klicken Sie dann auf **Mehr** > **Gerät umbenennen**.
4. Geben Sie auf dem Blatt **Gerät umbenennen** den neuen Namen in das Textfeld ein. Sie können Buchstaben, Zahlen und Bindestriche verwenden. Der Name muss mindestens einen Buchstaben oder Bindestrich enthalten.
5. Wenn Sie das Gerät nach dem Umbenennen neu starten möchten, wählen Sie neben **Restart after rename** (Nach Umbenennung neu starten) die Option **Ja** aus.
6. Klicken Sie auf **Umbenennen**.



## <a name="next-steps"></a>Nächste Schritte

Der Status der Aktion **Umbenennen** des Geräts wird auf dessen **Übersichtsseite** angezeigt.
