---
title: Entfernen eines Benutzers von einem iOS-Gerät mit Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie einen Benutzer von einem gemeinsam genutzten iOS-Gerät mit Intune entfernen.
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
ms.openlocfilehash: 772cdbe203b0489a9b2312a1cc10ea1b3182b35d
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713157"
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>Entfernen eines Benutzers von einem gemeinsam genutzten iOS-Gerät


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Die Aktion **Benutzer entfernen** löscht einen von Ihnen ausgewählten Benutzer aus dem lokalen Cache eines freigegebenen iPads. Das iPad muss mithilfe eines [iOS-Bildungsprofils](../fundamentals/education-settings-configure-ios.md) zum Verwalten der iOS-App „Classroom“ eingerichtet sein. 

## <a name="supported-platforms"></a>Unterstützte Plattformen

- Windows – Nicht unterstützt
- Windows Phone – Nicht unterstützt
- iOS – Unterstützt auf iOS 9.3 und höher (nur freigegebene iPad-Geräte)
- macOS – Nicht unterstützt
- Android – Nicht unterstützt

## <a name="remove-a-user"></a>Entfernen eines Benutzers

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Klicken Sie auf **Geräte** > **Alle Geräte**.
3. Wählen Sie aus der Liste der von Ihnen verwalteten Geräten ein iOS-Gerät aus.
4. Klicken Sie im Bereich des Geräts auf **Benutzer**.
5. Klicken Sie in der Liste mit der rechten Maustaste auf den Benutzer, den Sie entfernen möchten, und wählen Sie dann **Benutzer entfernen** aus.

## <a name="next-steps"></a>Nächste Schritte

- Klicken Sie auf **Geräte** > **Geräteaktionen**, um den Status der Aktion **Benutzer entfernen** anzuzeigen.
