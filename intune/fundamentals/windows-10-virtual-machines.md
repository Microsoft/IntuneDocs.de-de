---
title: Verwenden von virtuellen Windows 10-Computern mit Microsoft Intune
titleSuffix: ''
description: Richtlinien für die Verwendung von virtuellen Windows 10-Computern mit Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9afaf2c8a63bfaed1fdb593baf42c8fa258d7893
ms.sourcegitcommit: 1a22b8b31424847d3c86590f00f56c5bc3de2eb5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74263116"
---
# <a name="using-windows-10-virtual-machines-with-intune"></a>Verwenden von virtuellen Windows 10-Computern mit Intune

Intune unterstützt das Verwalten virtueller Windows 10 Enterprise-Computer mit bestimmten Einschränkungen. Die Intune-Verwaltung ist nicht abhängig von der Windows Virtual Desktop-Verwaltung desselben virtuellen Computers oder beeinträchtigt diese.

Beachten Sie bei der Verwaltung von virtuellen Windows 10-Computern mit Intune die folgenden Punkte:

## <a name="enrollment"></a>Anmeldung
- Eine bedarfsgesteuerte, sitzungshostbasierte Verwaltung von virtuellen Computern mit Intune wird nicht empfohlen. Jeder virtuelle Computer muss registriert werden, wenn er erstellt wird. Außerdem bleiben beim regelmäßigen Löschen von virtuellen Computern verwaiste Gerätedaten in Intune zurück, bis diese [bereinigt werden](../remote-actions/devices-wipe.md#automatically-delete-devices-with-cleanup-rules). 
- Der Windows-Selbstbereitstellungsmodus mit Autopilot wird nicht unterstützt, da hierfür ein Trusted Platform Module (TPM) erforderlich ist. 
- Die OOBE-Registrierung (Out of Box Experience) wird auf virtuellen Computern nicht unterstützt, auf die nur über RDP (Remotedesktopprotokoll) zugegriffen werden kann (z. B. in Azure gehostete Computer). Diese Einschränkung bedeutet Folgendes:
    - Der Windows-Selbstbereitstellungsmodus mit Autopilot und die kommerzielle OOBE-Registrierung werden nicht unterstützt.
    - Die Optionen auf der Seite zum Registrierungsstatus für gerätebezogene Richtlinien werden nicht unterstützt.

## <a name="configuration"></a>Konfiguration
Intune unterstützt keine Konfiguration, die ein TPM oder eine Hardwareverwaltung verwendet einschließlich:
- [BitLocker-Einstellungen](../configuration/device-profiles.md#endpoint-protection)
- [Einstellungen für die Schnittstelle zur Konfiguration der Gerätefirmware](../configuration/device-profiles.md#device-firmware-configuration-interface)

## <a name="reporting"></a>Berichterstellung
Intune erkennt virtuelle Computer automatisch und meldet sie im Feld **Geräte** > **Alle Geräte** > Gerät auswählen > **Übersicht** > **Modell** als „virtuellen Computer“. 

Virtuelle Computer, deren Zuordnung aufgehoben wurde, können zu Berichten zu nicht konforme Geräte beitragen, da sie sich [nicht beim Intune-Dienst einchecken können](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

## <a name="retirement"></a>Deaktivierung
Wenn Sie nur über RDP-Zugriff verfügen, sollten Sie die Aktion zum [Zurücksetzen](../remote-actions/devices-wipe.md#wipe) nicht verwenden. Durch die Aktion zum Zurücksetzen werden die RDP-Einstellungen des virtuellen Computers gelöscht, und es wird verhindert, dass erneut eine Verbindung gestellt wird.


