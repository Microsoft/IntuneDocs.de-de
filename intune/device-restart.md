---
title: Neustarten von Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Neustarten von Windows- und iOS-Geräten mit Microsoft Intune im Azure-Portal mithilfe der Remoteaktion „Neu starten“.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: f814abc4d47517c17e24a188c7efb5da771bc328
ms.sourcegitcommit: 06f62ae989da6c60bac4a52ccd41b429f7367d8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55068270"
---
# <a name="remotely-restart-devices-with-intune"></a>Remoteneustart von Geräten mit Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Die Geräteaktion **Neu starten** führt dazu, dass das von Ihnen gewählte Gerät neu gestartet wird. Der Eigentümer des Geräts wird nicht automatisch über den Neustart benachrichtigt und kann Daten verlieren.

## <a name="supported-platforms"></a>Unterstützte Plattformen

- Windows – unter Windows 8.1 und höher unterstützt
- Windows Phone – Unterstützt auf Windows Phone 8.1 und später
- Android-Kioskgeräte – unterstützt unter Android 7.0 und höher
- iOS – Unterstützt

    > [!Note]  
    > Für diesen Befehl wird ein überwachtes Gerät und das Zugriffsrecht **Gerätesperre** benötigt. Das Gerät wird sofort neu gestartet. Kennungsgeschützte iOS-Geräte verbinden sich nach dem Neustart nicht wieder mit einem WLAN-Netzwerk. Nach dem Neustart kann das Gerät möglicherweise nicht mehr mit dem Server kommunizieren.
- macOS – Nicht unterstützt
- Android- und Android-Arbeitsprofilgeräte: Nicht unterstützt

## <a name="restart-a-device"></a>Neustart eines Geräts

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte** > **Alle Geräte**.
4. Wählen Sie in der Liste der von Ihnen verwalteten Geräte ein Gerät aus, klicken Sie auf **Mehr** und dann auf die Remotegeräteaktion **Neu starten**.

## <a name="next-steps"></a>Nächste Schritte

- Klicken Sie auf **Geräte** > **Geräteaktionen**, um den Status der Geräteaktion **Neu starten** anzuzeigen.
