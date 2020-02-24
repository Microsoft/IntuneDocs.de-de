---
title: Entfernen eines Benutzers von einem iOS-/iPadOS-Gerät mit Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie einen Benutzer von einem gemeinsam genutzten iOS-/iPadOS-Gerät mit Intune entfernen.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b6b2b3492b9edece6b69e4b302741c0443c0a3e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415565"
---
# <a name="remove-a-user-from-a-shared-iosipados-device"></a>Entfernen eines Benutzers von einem gemeinsam genutzten iOS-/iPadOS-Gerät


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Die Aktion **Benutzer entfernen** löscht einen von Ihnen ausgewählten Benutzer aus dem lokalen Cache eines freigegebenen iPads. Das iPad muss mithilfe eines [iOS-/iPadOS-Bildungsprofils](../fundamentals/education-settings-configure-ios.md) zum Verwalten der iOS-/iPadOS-App „Classroom“ eingerichtet sein. 

## <a name="supported-platforms"></a>Unterstützte Plattformen

- Windows – Nicht unterstützt
- Windows Phone – Nicht unterstützt
- iOS/iPadOS – Unterstützt auf iOS/iPadOS 9.3 und höher (nur freigegebene iPad-Geräte)
- macOS – Nicht unterstützt
- Android – Nicht unterstützt

## <a name="remove-a-user"></a>Entfernen eines Benutzers

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Klicken Sie auf **Geräte** > **Alle Geräte**.
3. Wählen Sie aus der Liste der von Ihnen verwalteten Geräte ein iOS-/iPadOS-Gerät aus.
4. Klicken Sie im Bereich des Geräts auf **Benutzer**.
5. Klicken Sie in der Liste mit der rechten Maustaste auf den Benutzer, den Sie entfernen möchten, und wählen Sie dann **Benutzer entfernen** aus.

## <a name="next-steps"></a>Nächste Schritte

- Klicken Sie auf **Geräte** > **Geräteaktionen**, um den Status der Aktion **Benutzer entfernen** anzuzeigen.
