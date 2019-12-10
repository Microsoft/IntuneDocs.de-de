---
title: Erstellen einer MTD-Konformitätsrichtlinie für Geräte mit Microsoft Intune
titleSuffix: Microsoft Intune
description: Erstellen Sie eine Intune-Konformitätsrichtlinie für Geräte, die die Bedrohungsstufen Ihres MTD-Partners verwendet, um zu ermitteln, ob ein mobiles Gerät auf Unternehmensressourcen zugreifen darf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 504c77fb56918cf97312e70f50b38356f9f7efef
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409695"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Erstellen einer Mobile Threat Defense-Gerätekompatibilitätsrichtlinie (MTD) mit Intune

Intune mit MTD hilft Ihnen dabei, Bedrohungen zu erkennen und Risiken auf mobilen Geräten zu bewerten. Sie können eine Regel für eine Intune-Gerätekompatibilitätsrichtlinie erstellen, mit der das Risiko bewertet wird, um zu ermitteln, ob das Gerät kompatibel ist oder nicht. Anschließend können Sie eine [Richtlinie für bedingten Zugriff](create-conditional-access-intune.md) verwenden, um den Zugriff auf Dienste basierend auf der Gerätekonformität zu blockieren.

> [!NOTE]
> Diese Informationen gelten für alle Mobile Threat Defense-Partner.

## <a name="before-you-begin"></a>Vorbereitung

Beim Einrichten von MTD haben Sie in der MTD-Partnerkonsole eine Richtlinie erstellt, die verschiedene Bedrohungen als hoch, mittel und niedrig klassifiziert. Nun müssen Sie Mobile Threat Defense-Stufe in der Intune-Gerätekompatibilitätsrichtlinie festlegen.

Voraussetzungen für die Gerätekompatibilitätsrichtlinie mit MTD:

- Einrichten der MTD-Integration in Intune

## <a name="to-create-an-mtd-device-compliance-policy"></a>So erstellen Sie eine MTD-Gerätekonformitätsrichtlinie

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Gerät** > **Konformitätsrichtlinien** > **Richtlinie erstellen** aus.

3. Geben Sie eine Richtlinie zur Gerätekonformität an **Name**, **Beschreibung**, wählen Sie die **Plattform** aus, und wählen Sie dann **Konfigurieren** unter dem Abschnitt **Einstellungen** aus.

4. Wählen Sie im Bereich **Konformitätsrichtlinie** die Option **Geräteintegrität** aus.

5. Wählen Sie im Bereich **Geräteintegrität** aus der Dropdownliste **Anfordern, dass das Gerät höchstens der angegebenen Gerätebedrohungsstufe entspricht** die gewünschte Bedrohungsstufe für mobile Geräte aus.

   - **Secured** (Geschützt): Diese Stufe ist die sicherste Einstellung. Solange auf einem Gerät Bedrohungen vorhanden sind, ist kein Zugriff auf Unternehmensressourcen möglich. Wenn Bedrohungen gefunden werden, wird das Gerät als nicht kompatibel bewertet.

   - **Niedrig:** Das Gerät ist konform, wenn nur Bedrohungen auf niedriger Stufe vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.

   - **Mittel:** Das Gerät ist konform, wenn auf dem Gerät Bedrohungen niedriger oder mittlerer Stufe gefunden werden. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht kompatibel bewertet.

   - **Hoch:** Diese Stufe gewährleistet das geringste Maß an Sicherheit. Sie lässt alle Bedrohungsstufen zu und verwendet Mobile Threat Defense nur zu Berichtszwecken. Auf Geräten muss mit dieser Einstellung die MTD-App aktiviert sein.

6. Klicken Sie zweimal auf **OK**, und wählen Sie zum Erstellen der Richtlinie **Erstellen** aus.

> [!IMPORTANT]
> Wenn Sie Richtlinien für bedingten Zugriff für Office 365 oder andere Dienste erstellen, wird die Konformitätsbewertung ausgewertet, und auf nicht konformen Geräten wird der Zugriff auf Unternehmensressourcen blockiert, bis die Bedrohung auf dem Gerät beseitigt ist.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>So weisen Sie eine MTD-Gerätekonformitätsrichtlinie zu

So weisen Sie eine Gerätekonformitätsrichtlinie Benutzern zu:

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Gerät** > **Konformitätsrichtlinien** aus.

3. Wählen Sie die Richtlinie aus, die Sie Benutzern zuweisen möchten, und wählen Sie danach **Zuweisungen** aus. Verwenden Sie die verfügbaren Optionen, um Gruppen *einzuschließen* oder *auszuschließen*, die diese Richtlinie erhalten sollen.  

4. Wählen Sie „Speichern“ aus, um die Zuweisung abzuschließen. Wenn Sie die Zuweisung speichern, wird die Richtlinie für die ausgewählten Benutzer bereitgestellt, und Ihre Geräte werden auf Konformität ausgewertet.

## <a name="next-steps"></a>Nächste Schritte

[Aktivieren von Mobile Threat Defense in Intune](mtd-connector-enable.md)
