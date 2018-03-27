---
title: Aktivieren der Geräteschutzregel
description: Aktivieren der Regel zum Schutz vor Bedrohungen von mobilen Geräten in der Gerätekompatibilitätsrichtlinie.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8f19318256dc4480207097d2f4ab393b799e207a
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="create-lookout-device-compliance-policy-in-intune"></a>Erstellen einer Lookout-Kompatibilitätsrichtlinie in Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Dank Intune mit Lookout Mobile Threat Defense können Sie Bedrohungen auf mobilen Geräten erkennen und das Risiko auf solchen Geräten bewerten. Sie können eine Regel für die Kompatibilitätsrichtlinie erstellen, mit der das Risiko bewertet wird, um zu ermitteln, ob das Gerät kompatibel ist. Anschließend können Sie die Richtlinie für bedingten Zugriff verwenden, um den Zugriff auf Dienste basierend auf der Gerätekompatibilität zuzulassen oder zu blockieren.

Voraussetzungen für die Kompatibilitätsrichtlinie mit Lookout Mobile Threat Defense:

- [Einrichten des Lookout Mobile Thread Defense-Abonnements](setup-your-lookout-mtd-subscription.md)
- [Aktivieren der Lookout Verbindung in Intune](enable-lookout-mtd-connection.md)
- [Konfigurieren und Bereitstellen der Lookout for Work-App](configure-deploy-lookout-for-work-app.md)

Beim Einrichten von Lookout Mobile Threat Defense haben Sie in der [Lookout-Konsole](https://aad.lookout.com) eine Richtlinie erstellt, die verschiedene Bedrohungen als hoch, mittel und niedrig klassifiziert. In der Intune-Kompatibilitätsrichtlinie legen Sie die maximal zulässige Bedrohungsstufe fest.

1. Wechseln Sie in der [Intune-Administratorkonsole](https://manage.microsoft.com) zur Seite **Kompatibilitätsrichtlinien**. Sie können entweder eine vorhandene Kompatibilitätsrichtlinie verwenden oder eine neue erstellen. Wechseln Sie zu **Geräteintegrität**, und aktivieren Sie **Schutz vor Gerätebedrohungen**.
  ![Screenshot mit der Einstellung der Regel zum Schutz vor Gerätebedrohungen in ](../media/mtp/mtp-compliance-policy-rule.png)

2. Wählen Sie die Option **Maximal zulässige Bedrohungsstufe**:
  * **Keine (geschützt)**: Dies ist die sicherste Einstellung.  Solange auf einem Gerät Bedrohungen vorhanden sind, ist kein Zugriff auf Unternehmensressourcen möglich.  Wenn Bedrohungen gefunden werden, wird das Gerät als nicht kompatibel bewertet.  
  * **Niedrig**: Das Gerät ist kompatibel, wenn nur Bedrohungen auf niedriger Stufe vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  * **Mittel**: Das Gerät ist kompatibel, wenn die auf dem Gerät gefundenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht kompatibel bewertet.
  * **Hoch**: Dies ist die am wenigsten sichere Option. Diese Option lässt alle Bedrohungsstufen zu und verwendet den Lookout-Schutz vor Bedrohungen von mobilen Geräten nur zu Berichtszwecken.

![Screenshot der Option für die Bedrohungsstufe für die Einstellung der Regel zum Schutz vor Gerätebedrohungen](../media/mtp/mtp-compliance-policy-setting.png)

Wenn Sie für Office 365 oder andere Dienste Richtlinien für den bedingten Zugriff erstellen, wird diese Kompatibilitätsbewertung ausgewertet, und auf nicht kompatiblen Geräten wird der Zugriff auf Unternehmensressourcen gesperrt, bis die Bedrohung beseitigt ist.

## <a name="monitor-device-threats"></a>Überwachen von Gerätebedrohungen
Sie können den Kompatibilitätszustand eines Geräts in der **Intune-Verwaltungskonsole** auf der Seite [Alle Geräte](https://manage.microsoft.com) anzeigen.

![Screenshot der Seite für Geräte in der Intune-Verwaltungskonsole mit Kompatibilitätsstatus eines Geräts](../media/mtp/mtp-device-status-intune-console.png)

## <a name="next-steps"></a>Nächste Schritte
* Erstellen einer Richtlinie für bedingten Zugriff
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange lokal](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype for Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)
