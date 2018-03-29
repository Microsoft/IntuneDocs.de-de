---
title: Zurücksetzen von Gerätekennungen mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Mit der Aktion „Kennung entfernen“ können Sie die Kennung von Geräten entfernen oder zurücksetzen, die Sie mit Intune überwachen oder verwalten.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4cca5922f036711093469e71489e267af53f05a9
ms.sourcegitcommit: e6319ff186d969da34bd19c9730ba003d6cce353
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Zurücksetzen oder Entfernen einer Gerätekennung in Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Um eine neue Kennung für ein Gerät zu erstellen, verwenden Sie die Aktion **Kennung entfernen**.

## <a name="supported-platforms"></a>Unterstützte Plattformen

- Windows Phone 8.1 (nicht mit Azure Active Directory verknüpft), einschließlich Releases bis Windows 10 Creators Update
- Windows 10 Creators Update und höher
- iOS
- Android-Versionen vor Android 7

Dieses Feature wird für die folgenden Betriebssysteme nicht unterstützt:

- Windows
- macOS
- Android for Work

## <a name="reset-a-passcode"></a>Zurücksetzen einer Kennung

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte** und dann auf **Alle Geräte**.
4. Wählen Sie aus der Liste der von Ihnen verwalteten Geräten ein Gerät aus, und klicken Sie auf **...Weitere**. Wählen Sie dann die Remotegeräteaktion **Kennung entfernen** aus.

## <a name="next-steps"></a>Nächste Schritte

Um den Status der gerade ausgeführten Aktion anzuzeigen, wählen Sie im Bereich **Geräte** die Option **Geräteaktionen** aus.
