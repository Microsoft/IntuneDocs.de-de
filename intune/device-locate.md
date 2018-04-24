---
title: Auffinden von verlorenen iOS-Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Finden Sie verloren gegangene oder gestohlene iOS-Geräte, indem Sie das Feature „Gerät suchen“ in Microsoft Intune verwenden. Hier erhalten Sie weitere Informationen zu Sicherheit und Datenschutz bei Verwendung der Aktion „Gerät suchen“.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bc3d46800087b33c6cebcbb50f7c16eb4a056c18
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Suchen nach verlorenen oder gestohlenen iOS-Geräten mit Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Verwenden Sie die Aktion **Gerät suchen**, um den Standort eines verloren gegangenen oder gestohlenen iOS-Geräts auf einer Karte anzuzeigen. Bei dem Gerät muss es sich um ein unternehmenseigenes, über ein Programm zur Geräteregistrierung registriertes iOS-Gerät im überwachten Modus handeln. Bevor Sie diese Aktion verwenden, stellen Sie sicher, dass sich das Gerät im [Modus für verlorene Geräte](device-lost-mode.md) befindet.

## <a name="supported-platforms"></a>Unterstützte Plattformen

- iOS 9.3 und höher

Dieses Feature wird für die folgenden Betriebssysteme nicht unterstützt: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>Suchen eines verloren gegangenen oder gestohlenen Geräts

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte** und dann auf **Alle Geräte**.
4. Wählen Sie aus der Liste der von Ihnen verwalteten Geräten ein iOS-Gerät aus, und klicken Sie auf **...Weitere**. Wählen Sie dann die Remotegeräteaktion **Gerät suchen** aus.
5. Wenn das Gerät gefunden wurde, wird der Standort unter **Gerät suchen** angezeigt.
    ![Screenshot von „Gerät suchen“ mithilfe von Intune in Azure](./media/locate-device.png)

>[!NOTE]
>Aus Datenschutzgründen können Sie nur begrenzt in die Karte hineinzoomen.

## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>Sicherheits- und Datenschutzinformationen im Zusammenhang mit dem Modus für verlorene Geräte und Aktionen zum Suchen von Geräten
- Vor der Aktivierung dieser Aktion werden keinerlei Informationen zum Standort des Geräts an Intune gesendet.
- Bei Verwendung der Aktion „Gerät suchen“ werden die Koordinaten des Geräts in Form von Breiten- und Längengrad an Intune gesendet und im Azure-Portal angezeigt.
- Die Daten werden 24 Stunden lang gespeichert und dann entfernt. Die Standortdaten können nicht manuell entfernt werden.
- Die Standortdaten werden sowohl im gespeicherten Zustand als auch bei der Übertragung verschlüsselt.
- Wenn Sie den Modus für verlorene Geräte konfigurieren, können Sie eine Meldung erstellen, die auf dem Sperrbildschirm angezeigt wird. Geben Sie in dieser Meldung Informationen zur Rückgabe des Geräts an, damit die Person, die das Gerät findet, weiß, was zu tun ist.

## <a name="next-steps"></a>Nächste Schritte

Öffnen Sie **Geräte**, und klicken Sie auf **Geräteaktionen**, um den Aktivierungsstatus des Features „Gerät suchen“ anzuzeigen.
