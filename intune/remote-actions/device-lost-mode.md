---
title: Aktivieren des Modus für verlorene iOS-Geräte mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Aktivieren oder starten Sie den Modus für verlorene Geräte, um mithilfe von Microsoft Intune eine Meldung zu erstellen, die auf dem Sperrbildschirm eines verloren gegangenen oder gestohlenen iOS-Geräts angezeigt wird. Hier erhalten Sie auch weitere Informationen zu Sicherheit und Datenschutz bei Verwendung der Aktion „Modus für verlorene Geräte“.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/25/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2956be9e32587c3bf86ce009a6927269c11ffced
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712234"
---
# <a name="enable-lost-mode-on-ios-devices-with-intune"></a>Aktivieren des Modus für verlorene Geräte auf iOS-Geräten mit Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Durch die Geräteaktion **Modus für verlorene Geräte** können Sie den Modus für verlorene Geräte auf verlorenen oder gestohlenen iOS-Geräten aktivieren. In diesem Modus können Sie eine Meldung und eine Telefonnummer angeben, die auf dem Sperrbildschirm des Geräts angezeigt werden. Um den Modus für verlorene Geräte nutzen zu können, muss es sich bei dem Gerät um ein firmeneigenes iOS-Gerät im überwachten Modus handeln.

## <a name="supported-platforms"></a>Unterstützte Plattformen

- iOS 9.3 und höher

Dieses Feature wird für die folgenden Betriebssysteme nicht unterstützt: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>Aktivieren des Modus für verlorene Geräte

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
3. Klicken Sie auf **Geräte** und dann auf **Alle Geräte**.
4. Wählen Sie aus der Liste der von Ihnen verwalteten Geräte ein iOS-Gerät aus, und wählen Sie dann **Modus für verlorene Geräte (nur überwacht)** aus.
5. Wählen Sie unter **Modus für verlorene Geräte** die Option **Aktivieren** aus.
6. Geben Sie unter **Auf dem Sperrbildschirm anzuzeigende Meldung** eine Meldung ein, die auf dem Sperrbildschirm des Geräts angezeigt werden soll.
7. Optional können Sie auch im Feld **Anzuzeigende Telefonnummer** eine Telefonnummer eingeben.
6. Klicken Sie auf **OK**, um die Änderungen zu speichern.

Wenn Sie den Modus für verlorene Geräte aktivieren, wird jegliche Nutzung des Geräts blockiert. Der Benutzer kann erst wieder auf das Gerät zugreifen, wenn Sie den Modus für verlorene Geräte wieder deaktivieren. Verwenden Sie bei aktiviertem Modus für verlorene Geräte die Aktion [Gerät suchen](device-locate.md), um zu ermitteln, wo sich das Gerät befindet.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Sicherheit und Datenschutz im Zusammenhang mit dem Modus für verlorene Geräte und der Aktion „Gerät suchen“
- Vor der Aktivierung dieser Aktion werden keinerlei Informationen zum Standort des Geräts an Intune gesendet.
- Bei Verwendung der Aktion „Gerät suchen“ werden die Koordinaten des Geräts in Form von Breiten- und Längengrad an Intune gesendet und im Azure-Portal angezeigt.
- Die Daten werden 24 Stunden lang gespeichert und dann entfernt. Die Standortdaten können nicht manuell entfernt werden.
- Die Standortdaten werden sowohl im gespeicherten Zustand als auch bei der Übertragung verschlüsselt.
- Geben Sie in der Meldung, die auf dem Sperrbildschirm angezeigt werden soll, Informationen zur Rückgabe des verloren gegangenen Geräts an.

## <a name="next-steps"></a>Nächste Schritte

Öffnen Sie **Geräte**, und klicken Sie auf **Geräteaktionen**, um den Aktivierungsstatus des Modus für verlorene Geräte anzuzeigen.
