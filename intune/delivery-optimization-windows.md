---
title: Übermittlungsoptimierungseinstellungen für Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Konfigurieren Sie, wie Softwareupdates mit den Clouddiensten zur Übermittlungsoptimierung, die für Geräte mit Windows 10 und höher zur Verfügung stehen, auf Ihre Geräte übermittelt werden. Erstellen Sie in Intune ein Gerätekonfigurationsprofil zum Installieren von Updates über das Internet. Erfahren Sie auch, wie vorhandene Updateringe mit einem Übermittlungsoptimierungsprofil ersetzt werden.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a59cab5f709897e064b315193b292cb46dc2f2e
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831546"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Übermittlungsoptimierungseinstellungen in Microsoft Intune für Windows 10 (und höher)

> [!NOTE]
> **Softwareupdates – Windows 10-Updateringe** wird durch die Einstellungen für **Übermittlungsoptimierung** ersetzt. Ihre vorhandenen Updateringe können zur Verwendung der Einstellungen für die **Übermittlungsoptimierung** geändert werden. In [Wechseln vorhandener Updateringe zur Übermittlungsoptimierung](#move-existing-update-rings-to-delivery-optimization) (in diesem Artikel) werden die Schritte aufgeführt. 


Diese Funktion gilt für die folgende Plattform:

- Windows 10 und höher

In diesem Artikel werden alle Übermittlungsoptimierungseinstellungen aufgelistet und beschrieben, die Sie für Windows 10-Geräte konfigurieren können. Diese Einstellungen werden einem Gerätekonfigurationsprofil hinzugefügt und dann Ihren Geräten mit Microsoft Intune zugewiesen oder bereitgestellt.

[Updates für die Übermittlungsoptimierung](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) sind eine hervorragende Ressource, um mehr über die Übermittlungsoptimierung unter Windows 10 zu erfahren.

## <a name="create-the-profile"></a>Erstellen des Profils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.

2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.

3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
    - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie die Plattform aus:  

        - **Windows 10 und höher**

    - **Profiltyp**: Wählen Sie **Übermittlungsoptimierung** aus.
    - **Einstellungen:** Wählen Sie aus, wie die Updates heruntergeladen werden sollen. Folgende Optionen sind verfügbar: 

        - **Nicht konfiguriert:** Endbenutzer aktualisieren ihre Geräte mit ihren eigenen Methoden, möglicherweise unter Verwendung der Einstellungen für **Windows-Updates** oder **Übermittlungsoptimierung** im Betriebssystem.
        - **Nur HTTP, kein Peering:** Updates nur aus dem Internet beziehen. Beziehen Sie Updates nicht von anderen Computern in Ihrem Netzwerk (als Peering oder Peer-zu-Peer bezeichnet).
        - **HTTP kombiniert mit Peering hinter derselben NAT**: Updates aus dem Internet und von anderen Computern in Ihrem Netzwerk beziehen. 
        - **HTTP kombiniert mit eine Privatgruppe übergreifendem Peering**: Peering bezieht sich auf Geräte am gleichen Active Directory-Standort (sofern vorhanden) oder in der gleichen Domäne. Wenn diese Option ausgewählt ist, erfolgt das Peering die IP-Adressen Ihrer Netzwerkadressenübersetzung (Network Address Translation, NAT) übergreifend.
        - **HTTP kombiniert mit Internetpeering:** Updates aus dem Internet und von anderen Computern in Ihrem Netzwerk beziehen.
        - **Einfacher Downloadmodus ohne Peering:** Updates aus dem Internet direkt vom Updatebesitzer wie z.B. Microsoft beziehen. Die Clouddienste zur Übermittlungsoptimierung werden nicht in Anspruch genommen.
        - **Umgehungsmodus:** Den intelligenten Hintergrundübertragungsdienst (Background Intelligent Transfer Service, BITS) verwenden, um Updates zu beziehen. Verwenden Sie nicht die Übermittlungsoptimierung.

4. Wählen Sie anschließend **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern.

Das Profil wird erstellt und in der Liste angezeigt. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).

## <a name="move-existing-update-rings-to-delivery-optimization"></a>Wechseln vorhandener Updateringe zur Übermittlungsoptimierung

**Softwareupdates – Windows 10-Updateringe** wird durch die Einstellungen für **Übermittlungsoptimierung** ersetzt. Ihre vorhandenen Updateringe können problemlos zur Verwendung der Einstellungen für die **Übermittlungsoptimierung** geändert werden. Schritte:

1. Erstellen Sie ein Konfigurationsprofil für die Übermittlungsoptimierung:

    1. Wählen Sie in Intune **Gerätekonfiguration** > **Profile** > **Profil erstellen** aus.
    2. Geben Sie die folgenden Eigenschaften ein:

        - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein.
        - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
        - **Plattform**: Wählen Sie **Windows 10 und höher** aus.
        - **Profiltyp**: Wählen Sie **Übermittlungsoptimierung** aus.
        - **Einstellungen:** Wählen Sie für **Downloadmodus für Bereitstellungsoptimierung** den gleichen Modus aus, der vom vorhandenen Softwareupdatering verwendet wird. Folgende Optionen sind verfügbar:
            - **Nicht konfiguriert**
            - **Nur HTTP, kein Peering**
            - **HTTP kombiniert mit Peering hinter derselben NAT**
            - **HTTP kombiniert mit eine Privatgruppe übergreifendem Peering**
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
