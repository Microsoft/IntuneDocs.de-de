---
title: Besondere Überlegungen bei der Migration
titleSuffix: Microsoft Intune
description: Dieser Artikel bietet spezielle Überlegungen bei der Migration, die Sie in Erwägung ziehen sollten, bevor Sie eine Migrationskampagne für Microsoft Intune starten.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 936e4836938ddddc8e795d85de5a449ee77edaa4
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514998"
---
# <a name="special-migration-considerations"></a>Besondere Überlegungen bei der Migration

Es gibt spezielle Aspekte bei der Migration, die je nach vorhandener Umgebung des MDM-Anbieters zu berücksichtigen sind.

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>Zurücksetzen des Apple-Programms zur Geräteregistrierung (DEP)

Das Apple-Programm zur Geräteregistrierung (Device Enrollment Program, DEP) legt Gerätekonfigurationen fest, die vom Endbenutzer nicht entfernt werden können. Wenn Sie die erweiterten Verwaltungsfunktionen von DEP beibehalten möchten, muss das Gerät für die Registrierung bei Intune auf die Werkseinstellungen zurückgesetzt werden.

Sie haben die Möglichkeit zum [automatischen Registrieren von iOS-/iPadOS-Geräten mit dem Programm zur Geräteregistrierung von Apple](../enrollment/device-enrollment-program-enroll-ios.md), um die Geräte in Intune weiter mit dem Programm zur Geräteregistrierung zu verwalten.


## <a name="next-steps"></a>Nächste Schritte

[Phase 2: Migrationskampagne](../migration-guide-campaign.md)
