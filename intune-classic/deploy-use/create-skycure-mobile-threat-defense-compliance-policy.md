---
title: Erstellen der Skycure Mobile Threat Defense-Kompatibilitätsrichtlinie
description: Erstellen Sie die Skycure Mobile Threat Defense-Kompatibilitätsrichtlinie im klassischen Intune-Portal.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 56ff1728-1119-4e8a-aae6-ed5c7fafa052
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a2c194e7741c8ce79d87ad68eb408508b2929167
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="create-skycure-mobile-threat-defense-compliance-policy"></a>Erstellen der Skycure Mobile Threat Defense-Kompatibilitätsrichtlinie

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Dank Intune mit Skycure Mobile Threat Defense können Sie Bedrohungen auf mobilen Geräten erkennen und das Risiko auf solchen Geräten bewerten. Sie können eine Regel für eine Intune-Kompatibilitätsrichtlinie erstellen, mit der das Risiko bewertet wird, um zu ermitteln, ob das Gerät kompatibel ist. Anschließend können Sie die Richtlinie für bedingten Zugriff verwenden, um den Zugriff auf Dienste basierend auf der Gerätekompatibilität zuzulassen oder zu blockieren.

## <a name="before-you-begin"></a>Vorbereitung

Voraussetzungen für die Kompatibilitätsrichtlinie mit dem Skycure-Schutz vor Gerätebedrohungen:

-   [Einrichten der Skycure-Integration in Intune](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)

-   [Aktivieren der Skycure-Verbindung in Intune](/intune-classic/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

Beim Einrichten von Skycure Mobile Threat Defense haben Sie in der Skycure-Konsole eine Richtlinie erstellt, die verschiedene Bedrohungen als hoch, mittel und niedrig klassifiziert. Nun müssen Sie die maximal zulässige Bedrohungsstufe in der Intune-Kompatibilitätsrichtlinie festlegen.

## <a name="to-create-skycure-compliance-policy"></a>Erstellen der Skycure-Kompatibilitätsrichtlinie

1.  Wechseln Sie zum [klassischen Intune-Portal](https://manage.microsoft.com/), und geben Sie Ihre Anmeldeinformationen ein.

2.  Wählen Sie **Richtlinie** &gt; **Kompatibilitätsrichtlinien** aus. Sie können entweder eine vorhandene Kompatibilitätsrichtlinie verwenden oder eine neue erstellen.

3.  Wählen Sie **Hinzufügen** &gt; **Device Health** (Integrität für Geräte), und aktivieren Sie **Schutz vor Gerätebedrohungen**.

4.  Wählen Sie die Option **Maximal zulässige Bedrohungsstufe**:

    ein.  **Keine (geschützt)**: Dies ist die sicherste Einstellung. Solange auf einem Gerät Bedrohungen vorhanden sind, ist kein Zugriff auf Unternehmensressourcen möglich. Wenn Bedrohungen gefunden werden, wird das Gerät als nicht kompatibel bewertet.

    b.  **Niedrig**: Das Gerät ist kompatibel, wenn nur Bedrohungen auf niedriger Stufe vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.

    c.  **Mittel**: Das Gerät ist kompatibel, wenn die auf dem Gerät gefundenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht kompatibel bewertet.

    d.  **Hoch**: Dies ist die am wenigsten sichere Option. Diese Option lässt alle Bedrohungsstufen zu und verwendet Skycure Mobile Threat Defense nur zu Berichtszwecken.

> [!IMPORTANT]
> Wenn Sie für Office 365 oder andere Dienste Richtlinien für den bedingten Zugriff erstellen, wird diese Kompatibilitätsbewertung ausgewertet, und auf nicht kompatiblen Geräten wird der Zugriff auf Unternehmensressourcen gesperrt, bis die Bedrohung beseitigt ist.

## <a name="span-idmonitor-device-threats-classanchorspan-idnext-steps-classanchorspan-idtoc477360344-classanchorspanspanspannext-steps"></a><span id="monitor-device-threats" class="anchor"><span id="next-steps" class="anchor"><span id="_Toc477360344" class="anchor"></span></span></span>Nächste Schritte

-   Erstellen einer Richtlinie für bedingten Zugriff für:

    -   [Exchange Online](/intune-classic/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
    -   [Exchange lokal](/intune-classic/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
    -   [SharePoint Online](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)
    -   [Skype for Business Online](/intune-classic/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)
    -   [Dynamics CRM](/intune-classic/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)
