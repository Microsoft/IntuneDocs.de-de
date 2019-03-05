---
title: Sperren von Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie die Aktion „Remotesperre“ in Microsoft Intune, um ein Gerät zu sperren, das durch eine PIN oder ein Kennwort geschützt ist.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 328f196a61f26fa787495e515fb5de3e0d32f7b2
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231280"
---
# <a name="remotely-lock-devices-with-intune"></a>Remotesperren von Geräten mit Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte** > **Alle Geräte**.
4. Wählen Sie aus der Geräteliste ein Gerät aus, und klicken Sie dann auf die Aktion **Remotesperre**.

## <a name="next-steps"></a>Nächste Schritte

- Klicken Sie auf **Microsoft Intune** > **Geräte** > **Geräteaktionen**, um den Status dieser Aktion anzuzeigen. 
- Weitere Aktionen zum Verwalten Ihrer Geräte finden Sie unter [Verfügbare Aktionen](device-management.md).
