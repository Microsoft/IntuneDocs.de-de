---
title: Registrieren von Android Enterprise-Arbeitsprofilgeräten in Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Android Enterprise-Arbeitsprofilgeräte in Intune registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c447b6b21021573d95a5ece3297e548f216b7a0
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723527"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Einrichten der Registrierung von Android Enterprise-Arbeitsprofilgeräten

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune unterstützt Sie bei der Bereitstellung von Apps und Einstellungen auf Android Enterprise-Arbeitsprofilgeräten und stellt so sicher, dass geschäftliche und private Informationen immer getrennt bleiben. Ausführliche Informationen über Android Enterprise finden Sie in den [Voraussetzungen für Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Führen Sie die folgenden Schritte aus, um die Android Enterprise-Arbeitsprofilverwaltung einzurichten:

1. [Verknüpfen Sie Ihr Intune-Mandantenkonto mit Ihrem Android Enterprise-Konto](connect-intune-android-enterprise.md).
2. Geben Sie die Registrierungseinstellungen für Android Enterprise-Arbeitsprofilen an. Android Enterprise-Arbeitsprofile werden [nur auf bestimmten Android-Geräten unterstützt](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Jedes Gerät, das Android Enterprise-Arbeitsprofile unterstützt, unterstützt auch die Android-Geräteadministratorverwaltung. Mit Intune können Sie angeben, wie Geräte, die Android Enterprise-Arbeitsprofile unterstützen, mithilfe von [Registrierungseinschränkungen](enrollment-restrictions-set.md) verwaltet werden sollen.
    - **Blockieren:**  Alle Android-Geräte, einschließlich Geräte, die Android Enterprise-Arbeitsprofile unterstützen, werden als Android-Geräteadministratorgeräte registriert, es sei denn, die Registrierung als Android-Geräteadministrator wird ebenfalls blockiert. 
    - **Zulassen (Standardeinstellung)** : Alle Geräte, die Android Enterprise-Arbeitsprofile unterstützen, werden als Android Enterprise-Arbeitsprofilgeräte registriert. Alle Android-Geräte, die Android Enterprise-Arbeitsprofile nicht unterstützen, werden als Android-Administratorgeräte registriert, es sei denn, die Registrierung als Android-Geräteadministrator wird ebenfalls blockiert. 
> [!NOTE]
> Die Standardeinstellung auf **Zulassen** ist für neue Mandanten ab Juli 2019 gültig. Alle vorherigen Mandanten werden keine Änderungen an ihren Registrierungseinschränkungen erfahren und sehen, welche Richtlinien sie in den Registrierungsbeschränkungen festgelegt haben. Für frühere Mandanten, die nie Änderungen an den Registrierungseinschränkungen hatten, ist **Blockieren** weiterhin der Standard für Android Enterprise-Arbeitsprofile.

3. [Informieren Sie Ihre Benutzer darüber, wie sie ihre Geräte registrieren sollen.](/intune-user-help/create-a-work-profile-and-enroll-your-device-in-intune-android)  

Wenn Sie Geräte mit Android Enterprise-Arbeitsprofilen registrieren möchten, die bereits als reguläre Android-Geräte registriert wurden, müssen Sie die Registrierung der Geräte aufheben und die Geräte anschließend erneut registrieren.
> [!NOTE]
> Als Administrator können Sie dies mit der Funktion **Retire** (Außer Kraft setzen) remote durchführen. Diese Funktion finden Sie im Aktionsmenü, nachdem Sie das Gerät auf dem Blatt **Alle Geräte** ausgewählt haben.

Wenn Sie Android Enterprise-Arbeitsprofilgeräte über das Konto eines [Geräteregistrierungs-Managers](device-enrollment-manager-enroll.md) registrieren, besteht pro Konto ein Grenzwert von 10 registrierbaren Geräten.

Weitere Informationen finden Sie unter [Von Intune an Google gesendete Daten](../protect/data-intune-sends-to-google.md).

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Weiterführende Schritte für Android Enterprise-Arbeitsprofile
- [Hinzufügen von verwalteten Google Play-Apps für Android Enterprise-Geräte mit Intune](../apps/apps-add-android-for-work.md)
- [Apply features and settings on your devices using device profiles in Microsoft Intune (Anwenden von Features und Einstellungen für Ihre Geräte mithilfe von Geräteprofilen in Microsoft Intune)](../configuration/device-profiles.md)

## <a name="see-also"></a>Siehe auch

[Konfigurieren und Problembehandlung von Android Enterprise-Geräten in Microsoft Intune](https://support.microsoft.com/help/4476974)
