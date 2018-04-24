---
title: Benutzerdefinierte Microsoft Intune-Einstellungen für iOS-Geräte
titleSuffix: ''
description: Erfahren Sie mehr über die Einstellungen, die Sie in einem benutzerdefinierten iOS-Profil in Microsoft Intune verwenden können.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ada36b11489adbbcaf67db9192c7dd66caadb525
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-ios"></a>Benutzerdefinierte Microsoft Intune-Geräteeinstellungen für iOS-Geräte

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Verwenden Sie das benutzerdefinierte iOS-Profil von Microsoft Intune, um Einstellungen, die Sie mit dem [Apple Configurator-Tool](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) erstellt haben, auf iOS-Geräten zuzuweisen. Mit diesem Tool können Sie zahlreiche Einstellungen zur Betriebssteuerung dieser Geräte erstellen und in ein Konfigurationsprofil exportieren. Sie können dieses Konfigurationsprofil anschließend in ein benutzerdefiniertes iOS-Profil von Intune importieren und die Einstellungen Benutzern und Geräten in Ihrer Organisation zuweisen.

Diese Funktion ermöglicht die Zuweisung von iOS-Einstellungen, die nicht mit anderen Intune-Profiltypen konfigurierbar sind.


1. Anweisungen zu den ersten Schritten finden Sie unter [Konfigurieren von benutzerdefinierten Geräteeinstellungen in Microsoft Intune](custom-settings-configure.md).
2. Konfigurieren Sie im Bereich **Benutzerdefiniertes Konfigurationsprofil** die folgenden Einstellungen:

- **Name des benutzerdefinierten Konfigurationsprofils:** Geben Sie einen Namen für die Richtlinie an, der auf dem Gerät und im Intune-Status angezeigt wird.
- **Konfigurationsprofildatei:** Suchen Sie das mit Apple Configurator erstellte Konfigurationsprofil.
Stellen Sie sicher, dass die Einstellungen, die Sie aus dem Apple Configurator-Tool exportieren, mit der iOS-Version auf den Geräten kompatibel sind, denen Sie die benutzerdefinierte iOS-Richtlinie zuweisen. Um Informationen zum Korrigieren inkompatibler Einstellungen zu erhalten, suchen Sie auf der [Apple Developer-Website](https://developer.apple.com/) nach der **Referenz zu Konfigurationsprofilen** und der **Referenz zum Protokoll für die Verwaltung mobiler Geräte**.

Die importierte Datei wird in diesem Bereich unter **Dateiinhalt** angezeigt.
