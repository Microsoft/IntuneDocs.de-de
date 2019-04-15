---
title: Upgraden oder Verwenden des S Modus auf Windows 10-Geräten – Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie Microsoft Intune zum Upgraden von Windows 10-Geräten auf eine andere Edition oder zum Aktivieren des S Modus. Administratoren können ein Gerätekonfigurationsprofil verwenden, um ein Upgrade von Windows 10 Professional auf Windows 10 Enterprise durchzuführen und den S Modus zu aktivieren bzw. ihn zu verlassen. Sie erhalten Informationen zu unterstützten Upgradepfaden für Windows 10 Pro, N Edition, Education, Cloud, Enterprise, Core, Holographic und Mobile.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b206cfca048416b1e859e9230f037e1158d46ec
ms.sourcegitcommit: 25e17a1d002ee1faa49bb89648eb59373528539f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "59566632"
---
# <a name="upgrade-windows-10-editions-or-enable-s-mode-on-devices-using-microsoft-intune"></a>Upgraden von Windows 10-Editionen oder Aktivieren des S Modus auf Geräten mit Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) können Sie Ihre Windows 10-Geräte upgraden. Sie können z.B. ein Upgrade Ihrer Windows 10 Professional-Geräte auf Windows 10 Enterprise durchführen. Sie können auch S Mobile aktivieren, damit Geräte nur Apps aus dem Microsoft Store ausführen.

Der [Windows 10 S Modus](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) ist auf Sicherheit und Leistung ausgelegt. Wenn Ihre Geräte nur Apps aus dem Microsoft Store ausführen, können Sie den S Modus verwenden, um Ihre Geräte zu schützen. Wenn Ihre Geräte Apps verwenden, die im Microsoft Store nicht verfügbar sind, verlassen Sie den S Modus. Das Verlassen des S Modus ist eine Möglichkeit. Sobald Sie den S Modus verlassen haben, können Sie jedoch nicht in den Windows 10 S Modus zurückkehren.

Diese Funktion gilt für:

- Windows 10 und höher
- Windows 10 1809 oder höher für S Modus
- Windows Holographic for Business

Diese Features sind in Intune verfügbar und werden vom Administrator konfiguriert. Intune verwendet „Konfigurationsprofile“ zum Erstellen und Anpassen dieser Einstellungen für die Anforderungen Ihrer Organisation. Nachdem Sie diese Features in einem Profil hinzugefügt haben, können Sie das Profil auf Windows 10-Geräte in Ihrer Organisation übertragen oder für sie bereitstellen. Wenn Sie das Profil bereitstellen, aktualisiert Intune automatisch die Geräte oder aktiviert den S Modus.

Dieser Artikel listet die unterstützten Upgradepfade auf und zeigt Ihnen, wie Sie das Profil für die Gerätekonfiguration erstellen. Sie können auch alle verfügbaren Upgrade- und S Modus-Einstellungen für [Windows 10](edition-upgrade-windows-settings.md) sehen.

> [!NOTE]
> Wenn Sie später die Richtlinienzuweisung entfernen, wird die Windows-Version auf dem Gerät nicht wiederhergestellt. Das Gerät wird weiterhin wie gewohnt ausgeführt.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie Geräte upgraden, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Einen gültigen Product Key für die Installation der aktualisierten Version von Windows auf allen Geräten, die das Ziel dieser Richtlinie sind (für Windows 10-Desktopeditionen). Sie können entweder Mehrfachaktivierungsschlüssel (Multiple Activation Keys, MAK) oder KMS-Schlüssel (Key Management Server, Schlüsselverwaltungsserver) verwenden.
- Für Windows 10 Mobile- und Windows 10 Holographic-Editionen können Sie eine Lizenzdatei von Microsoft verwenden. Die Lizenzdatei enthält die Lizenzierungsinformationen zur Installation der aktualisierten Edition auf allen Geräten, die unter diese Richtlinie fallen.
- Die Windows 10-Geräte, denen Sie die Richtlinie zuweisen, müssen bei Microsoft Intune registriert sein. Die Editionsupgraderichtlinie kann nicht für PCs verwendet werden, auf denen die Intune-PC-Clientsoftware ausgeführt wird.

## <a name="supported-upgrade-paths"></a>Unterstützte Upgradepfade

Die folgenden Tabelle enthält die unterstützten Upgradepfade für das Windows 10-Editionsupgradeprofil.

| Upgrade von | Upgrade auf: |
|---|---|
| Windows 10 Pro | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education |
| Windows 10 Pro N-Edition | Windows 10 Education N-Edition <br/>Windows 10 Enterprise N-Edition <br/>Windows 10 Pro Education N-Edition | 
| Windows 10 Pro Education | Windows 10 Education | 
| Windows 10 Pro Education N-Edition | Windows 10 Education N-Edition |
| Windows 10 Cloud | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro <br/>Windows 10 Pro Education | 
| Windows 10 Cloud N-Edition | Windows 10 Education N-Edition <br/>Windows 10 Enterprise N-Edition <br/>Windows 10 Pro N-Edition <br/>Windows 10 Pro Education N-Edition | 
| Windows 10 Enterprise | Windows 10 Education | 
| Windows 10 Enterprise N-Edition | Windows 10 Education N-Edition | 
| Windows 10 Core | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education | 
| Windows 10 Core N-Edition | Windows 10 Education N-Edition <br/>Windows 10 Enterprise N-Edition <br/>Windows 10 Pro Education N-Edition | 
| Windows 10 Holographic | Windows 10 Holographic for Business |
| Windows 10 Mobile | Windows 10 Mobile Enterprise |

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/check_grn.png)  (X) = not supported    
![unsupported](./media/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)   |![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Mobile|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|
|Holographic|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png) -->

## <a name="create-the-profile"></a>Erstellen des Profils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das neue Profil ein. Geben Sie zum Beispiel `Windows 10 edition upgrade profile` oder `Windows 10 switch off S mode` ein.
    - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie die Plattform aus:  

        - **Windows 10 und höher**

    - **Profiltyp**: Wählen Sie **Upgrade der Edition** aus.
    - **Einstellungen:** Geben Sie die Einstellungen ein, die Sie konfigurieren möchten. Eine Liste aller Einstellungen und ihrer Funktionen finden Sie unter:

        - [Windows 10-Upgrade und S Modus](edition-upgrade-windows-settings.md)
        - [Windows Holographic for Business](holographic-upgrade.md)

4. Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern. 

Das Profil wird erstellt und in der Liste angezeigt. Denken Sie daran, das [Profil zuzuweisen](device-profile-assign.md) und [seinen Status zu überwachen](device-profile-monitor.md).

## <a name="next-steps"></a>Nächste Schritte

Nachdem das Profil erstellt wurde, kann es zugewiesen werden. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).

Sehen sie sich die Upgrade- und S Modus-Einstellungen für [Windows 10](edition-upgrade-windows-settings.md)- sowie [Windows Holographic for Business](holographic-upgrade.md)-Geräte an.
