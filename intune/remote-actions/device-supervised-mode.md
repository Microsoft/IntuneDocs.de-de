---
title: Aktivieren des überwachten iOS-Modus mit Microsoft Intune
titleSuffix: ''
description: Informationen zum Aktivieren des überwachten iOS-Modus mit Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8190814-07f0-42d8-9b3a-87c67dd2b7ed
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 79e6ba1541a516b36ae4bd02cf9f60f1a12c8896
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728441"
---
# <a name="turn-on-ios-supervised-mode"></a>Aktivieren des überwachten iOS-Modus


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Der überwachte Apple iOS-Modus stellt mehr Optionen zum Verwalten von Apple-Geräten dar, weshalb er sich besonders im Zusammenhang mit unternehmenseigenen Geräten als nützlich erweist, die im großen Umfang bereitgestellt werden. Beispielsweise können Sie AirDrop einschränken oder es verbieten, dass Benutzer den Gerätenamen ändern können. Eine Liste mit Einstellungen, für die der überwachte Modus erforderlich ist, finden Sie unter [Einstellungen für Geräteeinschränkungen für iOS-Geräte in Microsoft Intune](../configuration/device-restrictions-ios.md).

Intune unterstützt den überwachten Modus als Teil des [Apple-Programms zur Geräteregistrierung (Device Enrollment Program, DEP)](../enrollment/device-enrollment-program-enroll-ios.md).

Eine Liste mit Steuerelementen von Apple, die überwacht werden müssen, finden Sie in der [Übersicht über die Payload-Einstellungen](http://help.apple.com/configurator/mac/2.4/#/cad5370d089) von Apple.

## <a name="turn-on-supervised-mode-during-enrollment"></a>Aktivieren des überwachten Modus bei der Registrierung

In Intune können Sie den überwachten Modus für Geräte aktivieren, wenn Sie [ein Apple-Registrierungsprofil in DEP erstellen](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile). Aktivieren Sie unter **Geräteverwaltungseinstellungen** das Feld **Überwacht**.

## <a name="turn-on-supervised-mode-after-enrollment"></a>Aktivieren des überwachten Modus nach der Registrierung

Nach der Registrierung kann der überwachte Modus nur aktiviert werden, indem Sie ein iOS-Gerät mit einem Mac verbinden und den [Apple Configurator verwenden](../enrollment/apple-configurator-enroll-ios.md), der das Gerät zurücksetzt. Sie können nach der Registrierung in Intune kein Gerät für den überwachten Modus registrieren.

## <a name="identify-a-supervised-device"></a>Ermitteln eines überwachten Geräts

Sie können über den Sperrbildschirm oder die Seite **Info** überprüfen, ob das jeweilige Gerät überwacht wird:
- Auf dem Sperrbildschirm des Geräts steht dann **This iPhone is managed by "Company Name"** (Dieses iPhone wird von [Name des Unternehmens] verwaltet).
- Auf der Seite **Info** des Geräts steht dann:  **This iPhone is supervised. Contoso can monitor your Internet traffic and locate this device.** (Dieses iPhone wird überwacht. Contoso kann Ihren Internetdatenverkehr überwachen und den Standort dieses Geräts ermitteln.)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie unter [Was ist die Microsoft Intune Geräteverwaltung?](device-management.md)