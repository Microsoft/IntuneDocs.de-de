---
title: Neustarten von Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Neustarten von Windows- und iOS-Geräten mit Microsoft Intune im Azure-Portal mithilfe der Remoteaktion „Neu starten“.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d1e13801e3235831081be76ddfe5c8f5872e2077
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728519"
---
# <a name="remotely-restart-devices-with-intune"></a>Remoteneustart von Geräten mit Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

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

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Klicken Sie auf **Geräte** > **Alle Geräte**.
4. Wählen Sie in der Liste der von Ihnen verwalteten Geräte ein Gerät aus, klicken Sie auf **Mehr** und dann auf die Remotegeräteaktion **Neu starten**.

## <a name="next-steps"></a>Nächste Schritte

- Klicken Sie auf **Geräte** > **Geräteaktionen**, um den Status der Geräteaktion **Neu starten** anzuzeigen.
