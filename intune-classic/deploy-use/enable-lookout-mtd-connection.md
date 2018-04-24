---
title: Aktivieren von Lookout MTP in Intune
description: Aktivieren von Lookout Mobile Threat Protection in der Intune-Verwaltungskonsole.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4814bc053a27cf9fdf2694b6ae78884544b50c27
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="enable-lookout-mtd-connection-in-the-intune-classic-portal"></a>Aktivieren der Lookout MTD-Verbindung im klassischen Intune-Portal

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Um die Verbindung mit Lookout Mobile Threat Defense (MTD) in Intune zu aktivieren, muss der Intune-Connector in der Lookout-Konsole bereits konfiguriert sein.  Wenn dies noch nicht erfolgt ist, führen Sie die in [Einrichten Ihres Lookout Mobile Threat Defense-Abonnements](setup-your-lookout-mtd-subscription.md) beschriebenen Schritte aus.

Um die Lookout MTP-Verbindung in Intune zu aktivieren, wählen Sie auf der Seite **Verwaltung** der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Option **Integration von Drittanbieterdiensten** aus. Wählen Sie **Lookout-Status** aus, und aktivieren Sie **Synchronisierung mit MTP** mithilfe der Umschaltfläche.

![Screenshot der Lookout-Synchronisierungsseite mit hervorgehobener Umschaltfläche „Aktivieren“](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> Sie **müssen** die Lookout for Work-App konfigurieren, bevor Sie die Regeln der Kompatibilitätsrichtlinie erstellen und den bedingten Zugriff konfigurieren. Dadurch wird sichergestellt, dass die App für die Installation durch Endbenutzer bereit und verfügbar ist, bevor sie Zugriff auf E-Mail oder andere Unternehmensressourcen erhalten.

Damit wird das Setup der Lookout- und Intune-Integration in der Intune-Administratorkonsole abgeschlossen.  Die nächsten Schritte zum Implementieren dieser Lösung umfassen die Bereitstellung der [Lookout for Work-Apps](/intune-classic/deploy-use/device-threat-protection-policy)-Richtlinie.


## <a name="next-steps"></a>Nächste Schritte
[Konfigurieren der Lookout for Work-App](/intune-classic/deploy-use/device-threat-protection-apps)
