---
title: 'Windows 10: Upgrade- und S-Moduseinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation'
description: Hier finden Sie eine Liste aller Einstellungen und ihrer Funktionen beim Upgrade einer Windows 10-Edition auf einem Gerät oder Aktivieren des S-Modus auf einem Gerät mithilfe eines Gerätekonfigurationsprofils in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2a8c234c305744c48785763c87913c2635276ad
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565603"
---
# <a name="windows-10-and-newer-device-settings-to-upgrade-editions-or-enable-s-mode-in-intune"></a>Windows 10-Geräteeinstellungen (und höher) zum Upgrade von Editionen oder Aktivieren des S-Modus in Intune

In Microsoft Intune gibt es viele Einstellungen, die dazu dienen, Ihre Geräte zu verwalten und zu schützen. In diesem Artikel werden die Einstellungen zum Aktualisieren von Editionen oder Aktivieren des S-Modus auf Windows 10-Geräten aufgelistet und beschrieben. Diese Einstellungen werden in Intune in einem Upgradekonfigurationsprofil erstellt, das auf Geräte übertragen oder für sie bereitgestellt wird.

Als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) verwenden Sie diese Einstellungen, um die Editions- und S-Modusoptionen für Ihre Geräte mit Windows 10 zu konfigurieren.

Weitere Informationen zu diesem Feature finden Sie unter [Verwenden eines Konfigurationsprofils zum Upgraden von Windows 10 oder Verlassen des S Modus in Intune](edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie das Profil.](edition-upgrade-configure-windows-10.md#create-the-profile)

## <a name="edition-upgrade"></a>Upgrade der Edition

- **Edition, auf die upgegradet werden soll:** Wählen Sie die Windows 10-Edition aus, auf die Sie das Upgrade durchführen. Für die Geräte, die das Ziel dieser Richtlinie sind, wird ein Upgrade auf die von Ihnen gewählte Edition durchgeführt.
- **Product Key:** Geben Sie den Product Key ein, den Sie von Microsoft erhalten haben. Nach dem Erstellen der Richtlinie mit dem Product Key kann dieser nicht aktualisiert werden und wird aus Sicherheitsgründen ausgeblendet. Geben Sie den gesamten Schlüssel erneut ein, um den Product Key zu ändern.
- **Lizenzdatei:** Wählen Sie für **Windows 10 Holographic for Business** oder die **Windows 10 Mobile**-Edition **Durchsuchen** aus, um die Lizenzdatei auszuwählen, die Sie von Microsoft erhalten haben. Diese Lizenzdatei enthält Lizenzinformationen für die Editionen, auf die Sie die Geräte upgraden.

## <a name="mode-switch"></a>Moduswechsel

- **Keine Konfiguration**: Ein Gerät im S-Modus bleibt im S-Modus. Ein Endbenutzer kann das Gerät aus dem S Modus holen.
- **Keep in S mode** (Im S Modus lassen): Der Endbenutzer kann das Gerät nicht aus dem S Modus holen.
- **Switch** (Verlassen): Das Gerät wird aus dem S Modus geholt.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber vielleicht noch keine Aktionen durch. Denken Sie daran, das [Profil zuzuweisen](device-profile-assign.md) und [seinen Status zu überwachen](device-profile-monitor.md).

Sie können auch Editionsupgradeprofile für [Windows Holographic for Business](holographic-upgrade.md)-Geräte erstellen.
