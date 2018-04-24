---
title: Aktivieren von Skycure Mobile Threat Defense in Intune
description: Aktivieren Sie Skycure Mobile Threat Defense im klassischen Intune-Portal.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0cc4e59d-819a-47a2-a26f-4f8d0f8df7bf
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: da4197a41798f4e47ff35d2dfab36c5317f92e21
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>Aktivieren von Skycure Mobile Threat Defense in Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Um die Verbindung mit Skycure Mobile Threat Defense zu aktivieren, muss der [Intune-Connector in der Skycure-Konsole](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune) bereits konfiguriert sein.

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>So aktivieren Sie die Skycure MTD-Verbindung in Intune

1.  Wechseln Sie zum [klassischen Intune-Portal](https://manage.microsoft.com/), und geben Sie Ihre Anmeldeinformationen ein.

2.  Wählen Sie **Admin** &gt; **Third Party Service Integration** (Integration von Drittanbieterdiensten), wählen Sie dann **Skycure-Status**, und aktivieren Sie mithilfe der Umschaltfläche **Synchronisierung mit MTD**.

    ![Aktivieren der Skycure-Umschaltfläche im klassischen Intune-Portal](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> Sie müssen die Skycure-Apps konfigurieren, bevor Sie die Regeln der Kompatibilitätsrichtlinie erstellen und den bedingten Zugriff konfigurieren. Dadurch wird sichergestellt, dass die App für die Installation durch Endbenutzer bereit und verfügbar ist, bevor sie Zugriff auf E-Mail oder andere Unternehmensressourcen erhalten.

Damit wird das Einrichten der Skycure- und Intune-Integration in der Intune-Administratorkonsole abgeschlossen. Die nächsten Schritte zum Implementieren dieser Lösung umfassen die Bereitstellung der Skycure for Work-Apps und das Einrichten der Kompatibilitätsrichtlinie.

## <a name="next-steps"></a>Nächste Schritte

[Erstellen der Mobile Threat Defense-Kompatibilitätsrichtlinie](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
