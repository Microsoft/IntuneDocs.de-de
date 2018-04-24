---
title: Benutzerdefinierte Microsoft Intune-Einstellungen für macOS-Geräte
titleSuffix: ''
description: Erfahren Sie etwas über die Einstellungen, die Sie in einem benutzerdefinierten macOS-Profil in Microsoft Intune verwenden können.
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
ms.openlocfilehash: 66a935b96b802a05831118cd9dc0adbc62bb4bae
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-macos"></a>Benutzerdefinierte Microsoft Intune-Geräteeinstellungen für macOS-Geräte

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Verwenden Sie das benutzerdefinierte macOS-Profil von Microsoft Intune, um macOS-Geräten Einstellungen zuzuweisen, die Sie mit dem [Apple Configurator-Tool](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) erstellt haben. Mit diesem Tool können Sie zahlreiche Einstellungen zur Betriebssteuerung dieser Geräte erstellen und in ein Konfigurationsprofil exportieren. Sie können dieses Konfigurationsprofil anschließend in ein benutzerdefiniertes macOS-Profil von Intune importieren und die Einstellungen Benutzern und Geräten in Ihrer Organisation zuweisen.

Diese Funktion ermöglicht die Zuweisung von macOS-Einstellungen, die nicht mit anderen Intune-Profiltypen konfigurierbar sind.


1. Anweisungen zu den ersten Schritten finden Sie unter [Konfigurieren von benutzerdefinierten Geräteeinstellungen in Microsoft Intune](custom-settings-configure.md).
2. Konfigurieren Sie im Bereich **Benutzerdefiniertes Konfigurationsprofil** die folgenden Einstellungen:

- **Name des benutzerdefinierten Konfigurationsprofils:** Geben Sie einen Namen für die Richtlinie an, der auf dem Gerät und im Intune-Status angezeigt wird.
- **Konfigurationsprofildatei:** Suchen Sie das mit Apple Configurator erstellte Konfigurationsprofil.
Stellen Sie sicher, dass die Einstellungen, die Sie aus dem Apple Configurator-Tool exportieren, mit der macOS-Version auf den Geräten kompatibel sind, denen Sie die benutzerdefinierte macOS-Richtlinie zuweisen. Um Informationen zum Korrigieren inkompatibler Einstellungen zu erhalten, suchen Sie auf der [Apple Developer-Website](https://developer.apple.com/) nach der **Referenz zu Konfigurationsprofilen** und der **Referenz zum Protokoll für die Verwaltung mobiler Geräte**.

Die importierte Datei wird in diesem Bereich unter **Dateiinhalt** angezeigt.
