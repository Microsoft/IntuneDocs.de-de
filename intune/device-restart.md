---
title: "Remoteneustart von Geräten mit Intune"
titlesuffix: Azure portal
description: "In diesem Artikel erfahren Sie, wie Geräte über die Aktion zum Neustarten des Geräts remote neu gestartet werden."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8ab2bf622211c1a81ca9732aabebea43b5b0dcc4
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="remotely-restart-devices-with-intune"></a>Remoteneustart von Geräten mit Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Die Geräteaktion **Neu starten** führt dazu, dass das von Ihnen gewählte Gerät neu gestartet wird. Der Eigentümer des Geräts wird nicht automatisch über den Neustart benachrichtigt und kann daher Daten verlieren.

## <a name="supported-platforms"></a>Unterstützte Plattformen

- Windows – unter Windows 8.1 und höher unterstützt
- Windows Phone – Unterstützt auf Windows Phone 8.1 und später
- iOS – Unterstützt

    > [!Note]  
    > Für diesen Befehl wird ein überwachtes Gerät und das Zugriffsrecht **Gerätesperre** benötigt. Das Gerät wird sofort neu gestartet. Kennungsgeschützte iOS-Geräte verbinden Sie nach dem Neustart nicht wieder mit dem WLAN-Netzwerk und können unter Umständen nicht mehr mit dem Server kommunizieren.
- macOS – Nicht unterstützt
- Android – Nicht unterstützt

## <a name="how-to-restart-a-device"></a>So starten Sie einen Auftrags neu

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie auf dem Blatt **Intune** die Option **Geräte** aus.
4. Wählen Sie auf dem Blatt **Geräte** die Option **Alle Geräte** aus.
5. Wählen Sie aus der Liste der verwalteten Geräte ein Gerät aus, klicken Sie auf **...Weitere**, und wählen Sie dann die Remotegeräteaktion **Neu starten**.

## <a name="next-steps"></a>Nächste Schritte

Um den Status der gerade ausgeführten Aktion anzuzeigen, wählen Sie auf dem Blatt **Geräte** die Option **Geräteaktionen** aus.
