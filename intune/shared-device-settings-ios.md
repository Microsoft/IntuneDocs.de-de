---
title: Microsoft Intune-Konfigurationseinstellungen für freigegebene iOS-Geräte
titlesuffix: ''
description: Erfahren Sie mehr über die Microsoft Intune-Einstellungen zur Anzeige von Informationen auf dem Sperrbildschirm von iOS-Geräten.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 73c4f96e3057227bc601175c4e8f42802eb322bc
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>Konfigurationseinstellungen für freigegebene Geräte zum Anzeigen von Nachrichten auf dem iOS-Geräte-Sperrbildschirm

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel erfahren Sie mehr über die Microsoft Intune-Einstellungen zur Anzeige von Informationen auf dem Sperrbildschirm von iOS-Geräten.

Mit Konfigurationseinstellungen für freigegebene Geräte können Sie optionalen Text angeben, der im Anmeldefenster und auf dem Sperrbildschirm angezeigt wird. So können Sie z.B. eine „Wenn verloren, zurück an“-Nachricht und Bestandskennzeicheninformationen eingeben. 

>[!IMPORTANT]
> Diese Funktion wird auf überwachten Geräten mit iOS 9.3 und höher unterstützt.

## <a name="create-shared-device-settings"></a>Erstellen von freigegebenen Geräteeinstellungen

1. Navigieren Sie in [Intune im Azure-Portal](https://portal.azure.com) [im Gerätekonfigurationsbereich zu **Gerätefunktionen**](device-features-configure.md). 
1. Klicken Sie im Bereich **Gerätefeatures** auf die Option **Shared Device Configuration (supervised only)** (Konfiguration freigegebener Geräte (nur überwacht)).
2. Konfigurieren Sie im Bereich **Shared Device Configuration (supervised only)** (Konfiguration freigegebener Geräte (nur überwacht)) die folgenden Einstellungen:
    - **Bestandskennzeicheninformationen**: Geben Sie Informationen zum Bestandskennzeichen des Geräts ein. Beispiel: **Im Besitz von Contoso Corp**. Die von Ihnen eingegebenen Informationen werden auf alle Geräte angewendet, denen Sie dieses Profil zuweisen.
    - **Fußnote zum Sperrbildschirm**: Geben Sie einen Hinweis ein, der Ihnen helfen könnte, das Gerät zurückzubekommen, wenn es verloren geht oder gestohlen wird. Beispiel: **Wenn Sie dieses Gerät gefunden haben, rufen Sie bitte „Nummer“ an**.
3. Wenn Sie fertig sind, klicken Sie auf **OK**, bis Sie zum Bereich **Profil erstellen** zurückkehren, und klicken Sie dann auf **Erstellen**. 


## <a name="next-steps"></a>Nächste Schritte

Sie können nun das Geräteprofil den von Ihnen ausgewählten Gruppen zuweisen. Weitere Informationen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).
