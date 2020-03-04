---
title: Auffinden von verlorenen iOS-/iPadOS-Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Finden Sie verloren gegangene oder gestohlene iOS-/iPadOS-Geräte, indem Sie das Feature „Gerät suchen“ in Microsoft Intune verwenden. Hier erhalten Sie weitere Informationen zu Sicherheit und Datenschutz bei Verwendung der Aktion „Gerät suchen“.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7285ba1d8df5b53411bf6462fc165beeee66172f
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782204"
---
# <a name="locate-lost-or-stolen-iosipados-devices-with-intune"></a>Suchen nach verlorenen oder gestohlenen iOS-/iPadOS-Geräten mit Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Verwenden Sie die Aktion **Gerät suchen**, um den Standort eines verloren gegangenen oder gestohlenen iOS-/iPadOS-Geräts auf einer Karte anzuzeigen. Das Gerät muss sich im überwachten Modus befinden. Bevor Sie diese Aktion verwenden, stellen Sie sicher, dass sich das Gerät im [Modus für verlorene Geräte](device-lost-mode.md) befindet.

## <a name="supported-platforms"></a>Unterstützte Plattformen

- iOS/iPadOS 9.3 und höher

Dieses Feature wird für die folgenden Betriebssysteme nicht unterstützt: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>Suchen eines verloren gegangenen oder gestohlenen Geräts

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
3. Klicken Sie auf **Geräte** und dann auf **Alle Geräte**.
4. Wählen Sie aus der Liste der von Ihnen verwalteten Geräten ein iOS-/iPadOS-Gerät aus, und klicken Sie auf **...Weitere**. Wählen Sie dann die Remotegeräteaktion **Gerät suchen** aus.
5. Wenn das Gerät gefunden wurde, wird der Standort unter **Gerät suchen** angezeigt.
    ![Screenshot von „Gerät suchen“ mithilfe von Intune in Azure](./media/device-locate/locate-device.png)


## <a name="activate-lost-mode-sound-alert-on-an-ios-device"></a>Aktivieren der Akustikwarnung des Modus für verlorene Geräte auf einem iOS-Gerät

Wenn eine Person ihr unter iOS/iPadOS 9.3 oder höher verwendetes Gerät verloren hat, können Sie das Gerät remote auslösen, um eine Akustikwarnung auszugeben, damit der Benutzer es finden kann. Das Gerät muss sich im [Modus für verlorene Geräte](device-lost-mode.md) befinden.

Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Option **Geräte** > **Alle Geräte**, dann ein iOS-/iPadOS-Gerät und anschließend **Übersicht** > **Weitere** > **Klang für den Modus für verlorene Geräte wiedergeben (nur überwachen)** aus.

Der Sound wird so lange wiedergegeben, bis der Benutzer den Sound auf dem Gerät deaktiviert oder der Modus für verlorene Geräte für das Gerät beendet wird.


## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>Sicherheits- und Datenschutzinformationen im Zusammenhang mit dem Modus für verlorene Geräte und Aktionen zum Suchen von Geräten
- Vor der Aktivierung dieser Aktion werden keinerlei Informationen zum Standort des Geräts an Intune gesendet.
- Bei Verwendung der Aktion „Gerät suchen“ können die Koordinaten des Geräts mithilfe der Graph-API abgerufen werden.
- Die Daten werden 24 Stunden lang gespeichert und dann entfernt. Die Standortdaten können nicht manuell entfernt werden.
- Die Standortdaten werden sowohl im gespeicherten Zustand als auch bei der Übertragung verschlüsselt.
- Wenn Sie den Modus für verlorene Geräte konfigurieren, können Sie eine Meldung erstellen, die auf dem Sperrbildschirm angezeigt wird. Geben Sie in dieser Meldung Informationen zur Rückgabe des Geräts an, damit die Person, die das Gerät findet, weiß, was zu tun ist.

## <a name="next-steps"></a>Nächste Schritte

Öffnen Sie **Geräte**, und klicken Sie auf **Geräteaktionen**, um den Aktivierungsstatus des Features „Gerät suchen“ anzuzeigen.
