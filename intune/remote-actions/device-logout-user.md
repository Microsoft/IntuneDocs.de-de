---
title: Abmelden eines Benutzers eines iOS-Geräts
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie den aktuellen Benutzer eines iOS-Geräts mit Intune abmelden.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ccb072ac24dafca4f9b2fa6e3fb77445578c0f3a
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727908"
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Abmelden des aktuellen Benutzers eines mit Intune verwalteten iOS-Geräts


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Mit der Aktion **Aktiven Benutzer abmelden** wird der aktuelle Benutzer auf einem freigegebenen iPad abgemeldet. 

## <a name="supported-platforms"></a>Unterstützte Plattformen

- Windows – Nicht unterstützt
- Windows Phone – Nicht unterstützt
- iOS – Unterstützt auf iOS 9.3 und höher (nur freigegebene iPad-Geräte)
- macOS – Nicht unterstützt
- Android – Nicht unterstützt

## <a name="how-to-log-out-the-current-user"></a>So melden Sie den aktuellen Benutzer ab

1. Melden Sie sich beim Azure-Portal an.
2. Wählen Sie **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.
3. Wählen Sie auf dem Blatt **Intune** die Option **Geräte** aus.
4. Wählen Sie auf dem Blatt **Geräte und Gruppen** die Option **Alle Geräte** aus.
5. Wählen Sie aus der Liste der von Ihnen verwalteten Geräte ein iOS-Gerät und dann den Geräteremotevorgang **Aktiven Benutzer abmelden** aus.

## <a name="next-steps"></a>Nächste Schritte

Um den Status der gerade ausgeführten Aktion anzuzeigen, wählen Sie auf dem Blatt **Geräte und Gruppen** die Option **Geräteaktionen** aus.