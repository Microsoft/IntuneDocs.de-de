---
title: Bereitstellen von Apps
description: In diesem Thema werden Grundlagen erläutert, die Sie kennen müssen, bevor Sie mit dem Bereitstellen von Apps mit Intune beginnen.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9762c20abb9e4eedded50c92fb10ffb6119be63e
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="deploy-apps-with-microsoft-intune"></a>Bereitstellen von Apps mit Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

In diesem Thema werden einige Grundlagen erläutert, die Sie kennen müssen, bevor Sie mit dem Bereitstellen von Apps mit Microsoft Intune beginnen.


## <a name="app-deployment-actions"></a>App-Bereitstellungsaktionen
Wenn Sie Apps bereitstellen, können Sie eine der folgenden Bereitstellungsaktionen auswählen:

-   **Erforderliche Installation** – Die App wird auf dem Gerät installiert, ohne dass ein Benutzereingriff erforderlich ist.

    > [!TIP]
    > Bei iOS-Geräten, die nicht betreut werden, und bei allen Android-Geräten muss der Benutzer das App-Angebot vor der Installation akzeptieren.
    >
    >  Wenn ein Benutzer eine App deinstalliert, die Sie als erforderliche Installation bereitgestellt haben, installiert Intune diese App nach dem nächsten Inventurzyklus (in der Regel nach sieben Tagen) automatisch erneut.

-   **Verfügbare Installation** – Die App wird im Unternehmensportal angezeigt, und Benutzer können sie bei Bedarf installieren.

-   **Deinstallieren** : Die App wird vom Gerät deinstalliert.

-   **Nicht verfügbar** – Die App wird nicht im Unternehmensportal angezeigt und wird auf keinem Gerät installiert.

#### <a name="understand-which-deployment-actions-are-available-for-each-installer-type"></a>Verfügbare Bereitstellungsaktionen für die verschiedenen Installationsprogrammtypen

|Typ des Installationsprogramms|Erforderliche Installation|Verfügbare Installation|Deinstallieren|Nicht verfügbar|
|------------------|--------------------|---------------------|-------------|------------------|
|Windows-App-Paket (für eine Benutzergruppe bereitgestellt)|Ja |Ja |Ja |Ja |
|Windows-App-Paket (auf einer Gerätegruppe bereitgestellt)|Ja |Nein|Ja |Ja |
|App-Paket für mobile Geräte (für eine Benutzergruppe bereitgestellt)|Ja |Ja |Ja |Ja |
|App-Paket für mobile Geräte (auf einer Gerätegruppe bereitgestellt)|Ja |Nein|Ja |Ja |
|Windows Installer (für eine Benutzergruppe bereitgestellt)|Nein|Ja |Nein|Ja |
|Windows Installer (auf einer Gerätegruppe bereitgestellt)|Ja |Nein|Ja |Ja |
|Externer Link (für eine Benutzergruppe bereitgestellt)|Nein|Ja |Nein|Ja |
|Externer Link (auf einer Gerätegruppe bereitgestellt)|Nein|Nein|Nein|Nein|
|Verwaltete iOS-App aus dem App Store (für eine Benutzergruppe bereitgestellt)|Ja |Ja |Ja |Ja |
|Verwaltete iOS-App aus dem App Store (auf einer Gerätegruppe bereitgestellt)|Ja |Nein|Ja |Ja |
> [!TIP]
> Wenn Sie beim Bereitstellen von Apps sowohl Benutzer- als auch Gerätegruppen auswählen, können Sie die App nur als **verfügbare Installation** bereitstellen.

## <a name="deployment-conflicts"></a>Bereitstellungskonflikte
Wenn zwei Bereitstellungen mit der gleichen Bereitstellungsaktion von einem Gerät empfangen werden, gelten die folgenden Regeln:

-   Bereitstellungen auf einer Gerätegruppe haben Vorrang vor Bereitstellung für eine Benutzergruppe. Wenn jedoch eine App für eine Benutzergruppe mit der Bereitstellungsaktion **Verfügbar** bereitgestellt wird und dieselbe App auf einer Gerätegruppe mit der Bereitstellungsaktion **Nicht verfügbar** bereitgestellt wird, wird die App im Unternehmensportal Benutzern zur Installation zur Verfügung gestellt.

-   Eine Installationsaktion hat Vorrang vor einer Deinstallationsaktion.

-   Wenn eine erforderliche Installation und eine verfügbare Installation von einem Gerät empfangen werden, werden die Aktionen zusammengefasst. Das bedeutet, dass der Benutzer die App aus dem Unternehmensportal installieren kann, bevor die erforderliche Installation beginnt.


## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr zum [Bereitstellen von Apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md).
