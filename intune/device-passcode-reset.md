---
title: Zurücksetzen von Gerätekennungen mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Mit der Aktion „Kennung entfernen“ können Sie die Kennung von Geräten entfernen oder zurücksetzen, die Sie mit Intune überwachen oder verwalten.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a233c62b76901d9bad00aa6d8b2a8a4dd45dea96
ms.sourcegitcommit: 024cce10a99b12a13f32d3995b69c290743cafb8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2018
ms.locfileid: "39039300"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Zurücksetzen oder Entfernen einer Gerätekennung in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Um eine neue Kennung für ein Gerät zu erstellen, verwenden Sie die Aktion **Kennung entfernen**. Diese Aktion erfordert nur für das Arbeitsprofil eine PIN-Zurücksetzung. Die PIN-Zurücksetzungen werden für Android-Arbeitsprofile nicht unterstützt.

## <a name="work-profile-pin-reset-supported-platforms"></a>Für die PIN-Zurücksetzung für Arbeitsprofile unterstützte Plattformen

- Android-Geräte, die mit einem Arbeitsprofil registriert sind (Version 8.0 und höher) 
- Geräte unter Android Version 6.0 oder früher
- Android Enterprise-Kioskgeräte
- iOS 
     
## <a name="unsupported-platforms"></a>Nicht unterstützte Plattformen

- Android-Geräte, die mit einem Arbeitsprofil registriert sind (Version 7.0 und früher)
- Geräte unter Android 7.0 und höher
- macOS
- Windows

## <a name="reset-a-passcode"></a>Zurücksetzen einer Kennung

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte** und dann auf **Alle Geräte**.
4. Wählen Sie aus der Liste der von Ihnen verwalteten Geräten ein Gerät aus, und klicken Sie auf **...Weitere**. Wählen Sie dann die Remotegeräteaktion **Kennung entfernen** aus.

## <a name="resetting-android-work-profile-passcodes"></a>Zurücksetzen von Kennungen für Android-Arbeitsprofile

Unterstützte Android-Arbeitsprofilgeräte erhalten ein neues Kennwort zum Entsperren des verwalteten Profils oder eine verwaltete Profilabfrage für den Endbenutzer. 

Für Android 8.0-Arbeitsprofilgeräte erhalten Endbenutzer eine Benachrichtigung, dass die zurückgesetzte Kennung nach Abschluss der Registrierung aktiviert werden muss. Die Benachrichtigung wird angezeigt, wenn das Kennwort für ein Arbeitsprofil erforderlich ist und festgelegt wurde. Sobald die Kennung eingegeben wurde, wird die Benachrichtigung verworfen.

## <a name="resetting-ios-passcodes"></a>Zurücksetzen von iOS-Kennungen

Kennungen werden von iOS-Geräten entfernt. Wenn eine Konformitätsrichtlinie für Kennungen festgelegt wurde, fordert das Gerät den Benutzer dazu auf, in den Einstellungen eine neue Kennung festzulegen. 

## <a name="next-steps"></a>Nächste Schritte

Um den Status der gerade ausgeführten Aktion anzuzeigen, wählen Sie im Bereich **Geräte** die Option **Geräteaktionen** aus.
