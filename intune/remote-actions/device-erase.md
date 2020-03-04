---
title: Löschen eines macOS-Geräts
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie alle Daten einschließlich des Betriebssystems von einem macOS-Gerät löschen.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 446c88dabb070c42e47e2bb2d2ac87d6acecdedc
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781949"
---
# <a name="erase-all-data-from-a-macos-device"></a>Löschen aller Daten von einem macOS-Gerät

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Sie können alle Daten einschließlich des Betriebssystems von einem macOS-Gerät löschen. Das Gerät wird auch aus der Intune-Verwaltung entfernt. Der Endbenutzer erhält keine Warnung.

1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräte** > **Alle Geräte**, und wählen Sie das Gerät aus, das Sie löschen möchten.
2. Klicken Sie auf **Weitere** > **Löschen**, und geben Sie eine sechsstellige Nummer für die **PIN für Wiederherstellung** ein. Dies ist die Pin, die Sie dem Benutzer zur Verfügung stellen müssen, damit er das Betriebssystem auf seinem Gerät installieren kann. Achten Sie darauf, dass Sie sich diese Pin notieren, da sie nach der Löschaktion nicht sichtbar ist.
![Screenshot](./media/device-erase/providepin.png)
3. Klicken Sie auf **OK**, um das Gerät zu löschen.
