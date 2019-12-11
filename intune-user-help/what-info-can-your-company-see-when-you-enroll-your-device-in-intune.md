---
title: Auf welche Informationen kann Ihr Unternehmen zugreifen, wenn Sie Ihr Gerät registrieren?
description: Erläutert, auf was die IT-Abteilung zugreifen kann und auf was nicht.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.collection: M365-identity-device-management
ms.openlocfilehash: fc50f48afbd527f3c6d82cc0c71a166b0356ab9e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73801479"
---
# <a name="what-information-can-my-organization-see-when-i-enroll-my-device"></a>Welche Informationen erhält meine Organisation, wenn ich mein Gerät registriere?

Ihre Organisation kann Ihre privaten Informationen nicht einsehen, wenn Sie ein Gerät für Microsoft Intune registrieren. Wenn Sie ein Gerät registrieren, erhält Ihre Organisation die Berechtigung zum Anzeigen bestimmter Arten von Informationen auf Ihrem Gerät, z.B. das Gerätemodell und die Seriennummer. Ihre Organisation verwendet diese Informationen, um die Unternehmensdaten auf dem Gerät zu schützen.

**Folgendes kann nicht von Ihrer Organisation eingesehen werden:**

- Ihren Anrufs- und Browserverlauf
- E-Mail-Nachrichten und SMS
- Kontakte
- Kalender
- Kennwörter
- Ihre Bilder, einschließlich dem, was sich in der Fotos- und Kamera-App befindet
- Dateien

**Folgendes kann von Ihrer Organisation eingesehen werden:**

- Gerätemodell, z.B. Google Pixel
- Gerätehersteller, z.B. Microsoft
- Betriebssystem und Version, z.B. iOS 12.0.1
- App-Bestand und App-Namen, z.B. „Microsoft Word“. Auf persönlichen Geräten kann Ihre Organisation nur sehen, welche verwalteten Apps installiert sind. Auf unternehmenseigenen Geräten kann Ihre Organisation alle installierten Apps sehen.
- Geräteeigentümer
- Gerätename
- Seriennummer des Geräts
- IMEI

**Was Ihre Organisation möglicherweise außerdem sehen kann:**

- Telefonnummer: Bei unternehmenseigenen Geräten wird möglicherweise Ihre vollständige Telefonnummer angezeigt. Bei Geräten, die persönliches Eigentum sind, werden der Organisation nur die letzten vier Ziffern Ihrer Telefonnummer angezeigt. Auf der Seite mit den **Geräte Details** können Sie den besitztyp für jedes einzelne Gerät sehen.
- Speicherplatz auf dem Gerät: Wenn Sie eine erforderliche App installieren, prüft Ihre Organisation möglicherweise den freien Speicherplatz auf Ihrem Gerät, um festzustellen, ob genügend Speicherplatz vorhanden ist.  
- Standort: Ihre Organisation kann den Standort Ihres Geräts niemals anzeigen, sofern Sie nicht ein überwachtes iOS-Gerät auffinden müssen, das verloren gegangen ist. In der [Dokumentation zu Apple iOS](https://go.microsoft.com/fwlink/?linkid=853816) erhalten Sie weitere Informationen zu überwachten Geräten.  
- App-Bestandsinformationen: Wenn Ihr Unternehmen Mobile Threat Defense verwendet, können Informationen zu den Apps auf Ihrem iOS-Gerät eingesehen werden. Erfahren Sie mehr über [Mobile Threat Defense](you-are-prompted-to-install-mtd-ios.md). Auf Ihrem persönlichen Gerät kann Ihre Organisation nur sehen, welche verwalteten Apps installiert sind. Auf Ihrem unternehmenseigenen Gerät kann Ihre Organisation alle installierten Apps sehen.
- Netzwerkinformationen: Möglicherweise sind einige Informationen über Netzwerkverbindungen für Android-Geräte für den Support Ihrer Organisation verfügbar. Wenn Ihre Organisation beispielsweise verlangt, dass Geräte in einem bestimmten Gebäude bleiben, identifiziert Ihr Gerät das Netzwerk, mit dem es verbunden ist. 
