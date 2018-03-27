---
title: Richtlinieneinstellungen für Windows-Editionsupgrades
description: Erfahren Sie, wie Sie Windows 10-Geräte mit Intune automatisch auf eine andere Version aktualisieren.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 04/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 005f8cf2e769b1b007424e55867160a0f5828f7a
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="windows-edition-upgrade-policy-settings-in-microsoft-intune"></a>Einstellungen der Richtlinie für Windows-Editionsupgrades in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Mithilfe der Microsoft Intune-**Richtlinie für Editionsupgrades** können Sie für Geräte, die eine der folgenden Windows 10-Versionen ausführen, automatisch Upgrades auf eine andere Edition vornehmen:
* Windows 10 Desktop
* Windows 10 Holographic
* Windows 10 Mobile

Die folgenden Upgradepfade werden unterstützt:
- Von Windows 10 Pro auf Windows 10 Enterprise
- Von Windows 10 Home auf Windows 10 Education
- Von Windows 10 Mobile auf Windows 10 Mobile Enterprise
- Von Windows 10 Holographic Pro auf Windows 10 Holographic Enterprise

## <a name="before-you-start"></a>Vorbereitung
Bevor Sie beginnen, Geräte auf die neueste Version zu aktualisieren, benötigen Sie eines der folgenden Dinge:
* Einen gültigen Product Key für die Installation der neuen Version von Windows auf allen Geräten, die das Ziel dieser Richtlinie sind (für Windows 10-Desktopeditionen) Sie können entweder Mehrfachaktivierungsschlüssel (Multiple Activation Keys, MAK) oder KMS-Schlüssel (Key Management Server, Schlüsselverwaltungsserver) verwenden.
**Alternativ** verwenden Sie eine Lizenzdatei von Microsoft, die die Lizenzierungsinformationen zum Installieren der neuen Version von Windows auf allen Geräten enthält, die das Ziel dieser Richtlinie sind (für Windows 10 Mobile- und Windows 10 Holographic-Editionen).
* Die Windows 10-Geräte, die als Ziel vorgesehen sind, müssen bei Microsoft Intune registriert sein. Die Editionsupgraderichtlinie kann nicht für PCs verwendet werden, auf denen die Intune-PC-Clientsoftware ausgeführt wird.

## <a name="edition-upgrade-policy-settings"></a>Einstellungen der Richtlinie für Editionsupgrades

|Name der Einstellung|Details|
|-|-|
|**Name**|Geben Sie einen Namen für die Richtlinie für Editionsupgrades ein.|
|**Beschreibung**|Geben Sie optional eine Beschreibung für die Richtlinie ein, damit Sie sie in der Intune-Konsole besser identifizieren können.
|**Edition, auf die das Upgrade erfolgen soll**|Wählen Sie aus der Dropdownliste die Version von Windows 10 Desktop, Windows 10 Holographic oder Windows 10 Mobile aus, auf die ein Upgrade für die als Ziel angegebenen Geräte erfolgen soll.
|**Product Key**|Geben Sie den Product Key an, den Sie von Microsoft erhalten haben, und der für das Upgrade aller als Ziel festgelegten Windows 10 Desktop-Geräte verwendet werden kann.<br>Nach der Erstellung einer Richtlinie, die einen Product Key enthält, können Sie den Product Key später nicht mehr bearbeiten. Grund hierfür ist, dass der Schlüssel aus Sicherheitsgründen verborgen wird. Um den Product Key zu ändern, müssen Sie den gesamten Schlüssel erneut eingeben.
|**Lizenzdatei**|Klicken Sie auf **Durchsuchen**, um die von Microsoft erhaltene Lizenzdatei auszuwählen, die Lizenzinformationen für die Windows Holographic-Edition oder für die Windows 10 Mobile-Edition enthält, auf die das Upgrade bei den als Ziel festgelegten Geräten erfolgen soll.

### <a name="see-also"></a>Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
