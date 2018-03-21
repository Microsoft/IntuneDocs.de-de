---
title: "Sperren von Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation"
description: "Verwenden Sie die Aktion „Remotesperre“ in Microsoft Intune, um ein Gerät zu sperren, das durch eine PIN oder ein Kennwort geschützt ist."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 59a55de54a5a18f5fd1080fefa15c0e4801a1456
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2018
---
# <a name="remotely-lock-devices-with-intune"></a>Remotesperren von Geräten mit Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Mit der Geräteaktion **Remotesperre** wird ein Gerät gesperrt. Um das Gerät zu entsperren, muss der Eigentümer des Geräts die entsprechende Kennung verwenden. Sie können Geräte remote sperren, für die eine PIN oder ein Kennwort festgelegt ist. Geräte, die nicht über eine PIN oder eine Kennung verfügen, können nicht remote gesperrt werden.

## <a name="supported-platforms"></a>Unterstützte Plattformen

Die Remote-Sperre wird für folgende Plattformen unterstützt:

- Android
- iOS
- macOS
- Windows 10 Mobile
- Windows Phone 8.1 und höher

Sie wird **nicht** unterstützt für:
- Windows 10 Desktop

> [!NOTE]
> Bei macOS-Geräten legen Sie eine Wiederherstellungs-PIN aus 6 Ziffern fest. Wenn das Gerät gesperrt ist, wird in der **Geräteübersicht** die PIN angezeigt, bis eine andere Geräteaktion gesendet wird.

## <a name="remote-lock-a-device"></a>Remotesperre für Gerät aktivieren

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte** und dann auf **Alle Geräte**.
4. Wählen Sie aus der Geräteliste ein Gerät aus, und wählen Sie dann die Aktion **Remotesperre** aus.

## <a name="next-steps"></a>Nächste Schritte

Um den Status dieser Aktion anzuzeigen, öffnen Sie **Geräteaktionen** („Microsoft Intune > Geräte“). Weitere Aktionen zum Verwalten Ihrer Geräte finden Sie unter [Verfügbare Aktionen](device-management.md).