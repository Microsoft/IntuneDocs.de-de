---
title: "Remote-Sperren von verwalteten Geräten durch Intune"
titlesuffix: Azure portal
description: "In diesem Artikel erfahren Sie, wie Sie die von Ihnen verwalteten Geräte mit Intune remote sperren."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 01/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a8f3c93507cde4363570a9a39f8b3b1f69c07df
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="remotely-lock-managed-devices-with-intune"></a>Remote-Sperren von verwalteten Geräten durch Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Mit der Geräteaktion **Remote sperren** wird das ausgewählte Gerät gesperrt. Der Eigentümer des Geräts muss zum Entsperren seine Kennung verwenden. Sie können nur Remotesperrungen von Geräten durchführen, für die eine PIN oder ein Kennwort festgelegt wurde.

## <a name="supported-platforms"></a>Unterstützte Plattformen

Die Remote-Sperre wird für folgende Plattformen unterstützt:

|Plattform|Unterstützungsstatus|
|---|---|
|Android|Ja |
|iOS|Ja |
|macOS|Ja |
|Windows 10 Desktop|Nein|
|Windows 10 Mobile|Ja |
|Windows Phone|Ja für Windows Phone 8.1 und höher|

> [!NOTE]  
> Bei macOS-Geräten legen Sie eine Wiederherstellungs-PIN aus 6 Ziffern fest. Wenn das Gerät gesperrt ist, wird im Blatt **Device overview** (Geräteübersicht) die PIN solange angezeigt, bis eine andere Geräteaktion gesendet wurde.

## <a name="how-to-remote-lock-a-device"></a>So sperren Sie ein Gerät aus der Ferne

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie auf dem Blatt **Intune** die Option **Geräte** aus.
4. Wählen Sie auf dem Blatt **Geräte** die Option **Alle Geräte** aus.
5. Wählen Sie aus der Liste der verwalteten Geräte ein Gerät aus, und wählen Sie dann die Remotegeräteaktion **Remote sperren**.

## <a name="next-steps"></a>Nächste Schritte

Wählen Sie auf dem Blatt **Geräte** die Option **Geräteaktionen** aus, um den Status der gerade ausgeführten Aktion anzuzeigen.
