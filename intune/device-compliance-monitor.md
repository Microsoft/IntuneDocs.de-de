---
title: Überwachen der Gerätekonformität
titlesuffix: Microsoft Intune
description: Erfahren Sie, wie Sie die Gerätekonformität überwachen."
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b6c86b8f365f5ac3e65e91725e9fcd29ccd9ef58
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187021"
---
# <a name="monitor-device-compliance-in-intune"></a>Überwachen der Gerätekompatibilität in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Sie können sich auf dem Blatt **Übersicht** eine Zusammenfassung des Status Ihrer **Konformitätsprofile** ansehen.
Sie können interaktiv einen Drilldown in den Diagrammen durchführen, um Details anzuzeigen. Wenn Sie mehrere Kompatibilitätsprofile konfiguriert haben, können Sie den Richtlinienstatus auf dem Richtlinienblatt unter **Verwalten** > **Berichte** anzeigen.

##  <a name="device-compliance"></a>Gerätekompatibilität

In der Zusammenfassung des Gerätekompatibilitätsberichts sind zusammengestellte Informationen zur Anzahl der Geräte aufgeführt, für die einer der folgenden Status gemeldet wurde:

- **Kompatibel**: Das Gerät wurde vor Kurzem überprüft und entspricht den angegebenen Einstellungen für das Kompatibilitätsprofil.
- **Nicht kompatibel:**: Das Gerät wurde überprüft und als nicht konform bewertet.  Wenn im Profil eine Karenzzeit angegeben wurde, ist diese abgelaufen, und das Gerät hat damit in einen nicht konformen Status.
- **Karenzzeit:** Das Gerät wurde überprüft und als nicht konform bewertet. Die Karenzzeit gilt jedoch immer noch, bis das Gerät als nicht konform gekennzeichnet wird.

Sie können in jedem Abschnitt einen Drilldown durchführen, um weitere Details zu den einzelnen Geräten und Benutzern anzuzeigen.

## <a name="setting-compliance"></a>Einstellungskonformität

Der Einstellungskompatibilitätsbericht enthält Einzelheiten zu jeder Kompatibilitätseinstellung. Beispiele:

- Anzahl der Geräte, die mit der Einstellung nicht konform sind
- Die Plattform, auf der die Einstellung angewendet wird

Sie können für jede Einstellung einen Drilldown durchführen, um weitere Informationen zu den Profilen, für die diese Einstellungen aktiviert wurden, und den Werten der Einstellungen zu erhalten.
