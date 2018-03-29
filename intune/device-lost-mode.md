---
title: Aktivieren des Modus für verlorene iOS-Geräte mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Aktivieren oder starten Sie den Modus für verlorene Geräte, um mithilfe von Microsoft Intune eine Meldung zu erstellen, die auf dem Sperrbildschirm eines verloren gegangenen oder gestohlenen iOS-Geräts angezeigt wird. Hier erhalten Sie auch weitere Informationen zu Sicherheit und Datenschutz bei Verwendung der Aktion „Modus für verlorene Geräte“.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2da88a6146080014b79fbdc1b8c553eae5705195
ms.sourcegitcommit: e6319ff186d969da34bd19c9730ba003d6cce353
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2018
---
# <a name="enable-lost-mode-on-ios-devices-with-intune"></a>Aktivieren des Modus für verlorene Geräte auf iOS-Geräten mit Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Durch die Geräteaktion **Modus für verlorene Geräte** können Sie den Modus für verlorene Geräte auf verlorenen oder gestohlenen iOS-Geräten aktivieren. In diesem Modus können Sie eine Meldung und eine Telefonnummer angeben, die auf dem Sperrbildschirm des Geräts angezeigt werden. Um den Modus für verlorene Geräte nutzen zu können, muss es sich bei dem Gerät um ein firmeneigenes iOS-Gerät im überwachten Modus handeln.

## <a name="supported-platforms"></a>Unterstützte Plattformen

- iOS 9.3 und höher

Dieses Feature wird für die folgenden Betriebssysteme nicht unterstützt: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>Aktivieren des Modus für verlorene Geräte

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Geräte** und dann auf **Alle Geräte**.
4. Wählen Sie aus der Liste der von Ihnen verwalteten Geräten ein iOS-Gerät aus, und klicken Sie auf **...Weitere**. Wählen Sie dann die Remotegeräteaktion **Modus für verlorene Geräte** aus.
5. Aktivieren Sie dieses Feature unter **Modus für verlorene Geräte**. Geben Sie dann eine Meldung und eine Kontakttelefonnummer ein, die angezeigt werden sollen.
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