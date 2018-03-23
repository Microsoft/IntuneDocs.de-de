---
title: Löschen eines macOS-Geräts
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie alle Daten einschließlich des Betriebssystems von einem macOS-Gerät löschen.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d6ae04abda7f026bcbc02e325274712a386147b8
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
---
# <a name="erase-all-data-from-a-macos-device"></a>Löschen aller Daten von einem macOS-Gerät

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Sie können alle Daten einschließlich des Betriebssystems von einem macOS-Gerät löschen. Das Gerät wird auch aus der Intune-Verwaltung entfernt. Der Endbenutzer erhält keine Warnung.

1. Navigieren Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) zu **Geräte** > **Alle Geräte**, und wählen Sie das Gerät aus, das Sie löschen möchten.
![Screenshot](./media/device-erase/choosedevice.png)
2. Klicken Sie auf **Weitere** > **Löschen**, und geben Sie eine sechsstellige Nummer für die **PIN für Wiederherstellung** ein. Dies ist die Pin, die Sie dem Benutzer zur Verfügung stellen müssen, damit er das Betriebssystem auf seinem Gerät installieren kann. Achten Sie darauf, dass Sie sich diese Pin notieren, da sie nach der Löschaktion nicht sichtbar ist.
![Screenshot](./media/device-erase/providepin.png)
3. Klicken Sie auf **OK**, um das Gerät zu löschen.
