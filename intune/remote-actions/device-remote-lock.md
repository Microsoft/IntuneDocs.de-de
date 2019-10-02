---
title: Sperren von Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie die Aktion „Remotesperre“ in Microsoft Intune, um ein Gerät zu sperren, das durch eine PIN oder ein Kennwort geschützt ist.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8637e5333ae96fcaf69cb772bcce23193f85ae50
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728558"
---
# <a name="remotely-lock-devices-with-intune"></a>Remotesperren von Geräten mit Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Mit der Geräteaktion **Remotesperre** wird ein Gerät gesperrt. Zum Entsperren des Geräts muss der Eigentümer des Geräts die entsprechende Kennung verwenden. Sie können Geräte remote sperren, für die eine PIN oder ein Kennwort festgelegt ist. Geräte, die nicht über eine PIN oder ein Kennwort verfügen, können nicht remote gesperrt werden.

## <a name="supported-platforms"></a>Unterstützte Plattformen

Die **Remotesperre** wird für folgende Plattformen unterstützt:

- Android
- Android Enterprise-Kioskgeräte
- Android Enterprise-Arbeitsprofilgeräte
- iOS
- macOS
- Windows 10 Mobile
- Windows Phone 8.1 und höher

Die **Remotesperre** wird für folgende Plattformen nicht unterstützt:
- Windows 10 Desktop

> [!NOTE]
> Bei macOS-Geräten legen Sie eine Wiederherstellungs-PIN aus 6 Ziffern fest. Wenn das Gerät gesperrt ist, wird in der **Geräteübersicht** die PIN angezeigt, bis eine andere Geräteaktion gesendet wird.

## <a name="remote-lock-a-device"></a>Remotesperre für Gerät aktivieren

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Klicken Sie auf **Geräte** > **Alle Geräte**.
4. Wählen Sie aus der Geräteliste ein Gerät aus, und klicken Sie dann auf die Aktion **Remotesperre**.

## <a name="next-steps"></a>Nächste Schritte

- Klicken Sie auf **Microsoft Intune** > **Geräte** > **Geräteaktionen**, um den Status dieser Aktion anzuzeigen. 
- Weitere Aktionen zum Verwalten Ihrer Geräte finden Sie unter [Verfügbare Aktionen](device-management.md).
