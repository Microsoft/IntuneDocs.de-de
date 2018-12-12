---
title: Übermittlungsoptimierungseinstellungen für Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Konfigurieren Sie, wie Softwareupdates mit den Clouddiensten zur Übermittlungsoptimierung, die für Geräte mit Windows 10 und höher zur Verfügung stehen, auf Ihre Geräte übermittelt werden. Erstellen Sie in Intune ein Gerätekonfigurationsprofil zum Installieren von Updates über das Internet. Erfahren Sie auch, wie vorhandene Updateringe mit einem Übermittlungsoptimierungsprofil ersetzt werden.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 36cfb5ac05b2d69b5c7349f4ebc6054848a08fc8
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2018
ms.locfileid: "52730401"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Übermittlungsoptimierungseinstellungen in Microsoft Intune für Windows 10 (und höher)

In diesem Artikel werden alle Übermittlungsoptimierungseinstellungen aufgelistet und beschrieben, die Sie für Windows 10-Geräte konfigurieren können. Diese Einstellungen werden einem Gerätekonfigurationsprofil hinzugefügt und dann Ihren Geräten mit Microsoft Intune zugewiesen oder bereitgestellt.

## <a name="settings"></a>Einstellung

**Downloadmodus für Bereitstellungsoptimierung**: Wählen Sie aus, wie Updates Ihren Geräten übermittelt werden. Folgende Optionen sind verfügbar:

- **Nicht konfiguriert**: Endbenutzer aktualisieren ihre Geräte mit ihren eigenen Methoden, möglicherweise mit Verwendung der Einstellungen für **Windows-Updates** oder **Übermittlungsoptimierung** im Betriebssystem.
- **Nur HTTP, kein Peering**: Updates nur aus dem Internet beziehen. Beziehen Sie Updates nicht von anderen Computern in Ihrem Netzwerk (als Peering oder Peer-zu-Peer bezeichnet).
- **HTTP kombiniert mit Peering hinter dem gleichen NAT-HTTP kombiniert mit Peering über eine private Gruppe**: Updates aus dem Internet und von anderen Computern in Ihrem Netzwerk beziehen. Peering bezieht sich auf Geräte am gleichen Active Directory-Standort (sofern vorhanden) oder in der gleichen Domäne. Wenn diese Option ausgewählt ist, erfolgt das Peering die IP-Adressen Ihrer Netzwerkadressenübersetzung (Network Address Translation, NAT) übergreifend.
- **HTTP kombiniert mit Internetpeering**: Updates aus dem Internet und von anderen Computern in Ihrem Netzwerk beziehen.
- **Einfacher Downloadmodus ohne Peering**: Updates aus dem Internet direkt vom Updatebesitzer wie z.B. Microsoft beziehen. Die Clouddienste zur Übermittlungsoptimierung werden nicht in Anspruch genommen.
- **Umgehungsmodus**: Verwenden Sie den intelligenten Hintergrundübertragungsdienst (Background Intelligent Transfer Service, BITS), um Updates zu beziehen. Verwenden Sie nicht die Übermittlungsoptimierung.

## <a name="move-from-existing-update-rings-to-delivery-optimization"></a>Wechsel von vorhandenen Updateringen zur Übermittlungsoptimierung

**Softwareupdates – Windows 10-Updateringe** wird durch die Einstellungen für **Übermittlungsoptimierung** ersetzt. Ihre vorhandenen Updateringe können problemlos zur Verwendung der Einstellungen für die **Übermittlungsoptimierung** geändert werden. Schritte:

1. Erstellen Sie ein Konfigurationsprofil für die Übermittlungsoptimierung:

    1. Wählen Sie in Intune **Gerätekonfiguration** > **Profile** > **Profil erstellen** aus.
    2. Geben Sie einen **Namen** und eine **Beschreibung** für das Profil ein.
    3. Wählen Sie für **Plattform** **Windows 10 und höher** aus. Wählen Sie für **Profiltyp** **Übermittlungsoptimierung** aus.
    4. Klicken Sie auf **Einstellungen**. Wählen Sie für **Downloadmodus für Bereitstellungsoptimierung** den gleichen Modus aus, der vom vorhandenen Softwareupdatering verwendet wird. Folgende Optionen sind verfügbar:
        - **Nicht konfiguriert**
        - **Nur HTTP, kein Peering**
        - **HTTP kombiniert mit Peering hinter dem gleichen NAT-HTTP kombiniert mit Peering über eine private Gruppe**
        - **HTTP kombiniert mit Internetpeering**
        - **Einfacher Downloadmodus ohne Peering**
        - **Umgehungsmodus**

2. Weisen Sie dieses neue Profil den gleichen Geräten und Benutzern zu, die zu dem vorhandenen Softwareupdatering gehören. In [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) sind die Schritte aufgeführt.

3. Heben Sie die Konfiguration des vorhandenen Softwarerings auf:
    1. Wechseln Sie in Intune zu **Softwareupdates** > Windows 10-Updateringe.
    2. Wählen Sie in der Liste Ihren Updatering aus.
    3. Legen Sie in den Einstellungen für den **Downloadmodus für Bereitstellungsoptimierung** **Nicht konfiguriert** fest.
    4. Wählen Sie zum Speichern der Änderungen **OK** > **Speichern** aus.

## <a name="next-steps"></a>Nächste Schritte

[Weisen Sie das Profil zu](device-profile-assign.md), und [überwachen Sie seinen Status](device-profile-monitor.md).