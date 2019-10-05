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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 45e2985bcf01d635e964ee8785938c0d5df4e4af
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727609"
---
# <a name="special-migration-considerations"></a>Besondere Überlegungen bei der Migration

Es gibt spezielle Aspekte bei der Migration, die je nach vorhandener Umgebung des MDM-Anbieters zu berücksichtigen sind.

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>Zurücksetzen des Apple-Programms zur Geräteregistrierung (DEP)

Das Apple-Programm zur Geräteregistrierung (Device Enrollment Program, DEP) legt Gerätekonfigurationen fest, die vom Endbenutzer nicht entfernt werden können. Wenn Sie die erweiterten Verwaltungsfunktionen von DEP beibehalten möchten, muss das Gerät für die Registrierung bei Intune auf die Werkseinstellungen zurückgesetzt werden.

Um die Geräte in Intune weiter mit dem Programm zur Geräteregistrierung zu verwalten, [richten Sie die iOS-Geräteregistrierung mit dem Programm zur Geräteregistrierung ein](../enrollment/device-enrollment-program-enroll-ios.md).


## <a name="next-steps"></a>Nächste Schritte

[Phase 2: Migrationskampagne](../migration-guide-campaign.md)