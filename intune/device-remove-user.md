---
title: Entfernen eines Benutzers von einem iOS-Gerät mit Microsoft Intune
titlesuffix: ''
description: Erfahren Sie, wie Sie einen Benutzer von einem gemeinsam genutzten iOS-Gerät mit Intune entfernen.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 67a5f60e0877ebc8994ed7d3191a81f51d19c40a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31020774"
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>Entfernen eines Benutzers von einem gemeinsam genutzten iOS-Gerät


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Die Aktion **Benutzer entfernen** löscht einen von Ihnen ausgewählten Benutzer aus dem lokalen Cache eines freigegebenen iPads. Das iPad muss mithilfe eines [iOS-Bildungsprofils](education-settings-configure-ios.md) zum Verwalten der iOS-App „Classroom“ eingerichtet sein. 

## <a name="supported-platforms"></a>Unterstützte Plattformen

- Windows – Nicht unterstützt
- Windows Phone – Nicht unterstützt
- iOS – Unterstützt auf iOS 9.3 und höher (nur freigegebene iPad-Geräte)
- macOS – Nicht unterstützt
- Android – Nicht unterstützt

## <a name="remove-a-user"></a>Entfernen eines Benutzers

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie im Bereich **Intune** auf die Option **Geräte**.
4. Klicken Sie im Bereich **Intune** auf die Option **Alle Geräte**.
5. Wählen Sie aus der Liste der von Ihnen verwalteten Geräten ein iOS-Gerät aus.
6. Klicken Sie im Bereich des Geräts auf **Benutzer**.
7. Klicken Sie in der Liste mit der rechten Maustaste auf den Benutzer, den Sie entfernen möchten, und wählen Sie dann **Benutzer entfernen** aus.

## <a name="next-steps"></a>Nächste Schritte

- Klicken Sie auf **Geräte** > **Geräteaktionen**, um den Status der Aktion **Benutzer entfernen** anzuzeigen.
