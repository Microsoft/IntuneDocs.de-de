---
title: Upgraden oder Verwenden des S Modus auf Windows 10-Geräten mit Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie ein Geräteprofil in Microsoft Intune zum Upgraden von Windows 10-Geräten auf andere Editionen. Sie können z.B. ein Upgrade von Windows 10 Professional auf Windows 10 Enterprise durchführen. Sie können auch den S Modus auf einem Gerät mit dem Konfigurationsprofil aktivieren oder verlassen. Sie erhalten auch Informationen zu unterstützten Upgradepfaden für Windows 10 Pro, N Edition, Education, Cloud, Enterprise, Core, Holographic und Mobile.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f0e4ba42559a068ebefb453aba18060803dc36e0
ms.sourcegitcommit: f3974c810e172f345853dacd7f2ca0abc11b1a5b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2018
ms.locfileid: "44389624"
---
# <a name="use-a-configuration-profile-to-upgrade-windows-10-or-switch-from-s-mode-in-intune"></a>Verwenden eines Konfigurationsprofils zum Upgraden von Windows 10 oder Verlassen des S Modus in Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Konfigurieren Sie ein Upgradeprofil in Intune, um automatisch für Windows 10-Geräte ein Upgrade auf eine andere Edition durchzuführen. Vgl. außerdem die unterstützten Upgradepfade.

## <a name="before-you-begin"></a>Vorbereitung
Bevor Sie Geräte auf die neueste Version upgraden, müssen folgende Voraussetzungen erfüllt sein:

- Einen gültigen Product Key für die Installation der aktualisierten Version von Windows auf allen Geräten, die das Ziel dieser Richtlinie sind (für Windows 10-Desktopeditionen). Sie können entweder Mehrfachaktivierungsschlüssel (Multiple Activation Keys, MAK) oder KMS-Schlüssel (Key Management Server, Schlüsselverwaltungsserver) verwenden. Für Windows 10 Mobile- und Windows 10 Holographic-Editionen können Sie eine Lizenzdatei von Microsoft verwenden, die die Lizenzierungsinformationen zum Installieren der aktualisierten Version von Windows auf allen Geräten enthält, die das Ziel dieser Richtlinie sind.
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


<!-- Testing a new table on 3/5/18 

The following lists provide the supported upgrade paths for the Windows 10 edition upgrade profile. The Windows 10 edition to upgrade to is in bold followed by the list of supported editions that you can upgrade from:

**Windows 10 Education**
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 10 Cloud
- Windows 10 Enterprise
- Windows 10 Core
    
**Windows 10 Education N edition**    
- Windows 10 Pro N edition
- Windows 10 Pro Education N edition
- Windows 10 Cloud N edition
- Windows 10 Enterprise N edition
- Windows 10 Core N edition
    
**Windows 10 Enterprise**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Enterprise N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition
    
**Windows 10 Pro**
- Windows 10 Cloud
    
**Windows 10 Pro N edition**
- Windows 10 Cloud N edition
    
**Windows 10 Pro Education**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Pro Education N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition

**Windows 10 Holographic for Business**
- Windows 10 Holographic

**Windows 10 Mobile Enterprise**
- Windows 10 Mobile -->

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

## <a name="upgrade-the-edition"></a>Upgraden der Edition

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie einen **Namen** und eine **Beschreibung** für das Profil ein. Geben Sie zum Beispiel etwas wie `Windows 10 edition upgrade` ein.
4. Wählen Sie unter **Plattform** die Option **Windows 10 und höher** aus.
5. Wählen Sie für **Profiltyp** **Edition upgrade** (Editionsupgrade) aus.
6. Geben Sie in den Eigenschaften **Editionsupgrade** die folgenden Einstellungen an:

   - **Edition, auf die upgegradet werden soll:** Wählen Sie die Windows 10-Edition aus, auf die Sie das Upgrade durchführen. Für die Geräte, die das Ziel dieser Richtlinie sind, wird ein Upgrade auf die von Ihnen gewählte Edition durchgeführt.
   - **Product Key:** Geben Sie den Product Key ein, den Sie von Microsoft erhalten haben. Nach dem Erstellen der Richtlinie mit dem Product Key kann dieser nicht aktualisiert werden und wird aus Sicherheitsgründen ausgeblendet. Geben Sie den gesamten Schlüssel erneut ein, um den Product Key zu ändern.
   - **Lizenzdatei:** Wählen Sie für **Windows 10 Holographic for Business** oder die **Windows 10 Mobile**-Edition **Durchsuchen** aus, um die Lizenzdatei auszuwählen, die Sie von Microsoft erhalten haben. Diese Lizenzdatei enthält Lizenzinformationen für die Editionen, auf die Sie die Zielgeräte upgraden.

7. Klicken Sie auf **OK**, um die Änderungen zu speichern. Klicken Sie auf **Erstellen**, um das Profil zu erstellen.

## <a name="switch-out-of-s-mode"></a>Verlassen des S Modus

Der [Windows 10 S Modus](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode) ist auf Sicherheit und Leistung ausgelegt. Wenn Ihre Geräte nur Apps aus dem Microsoft Store ausführen, können Sie den S Modus verwenden, um Ihre Geräte zu schützen. Wenn Ihre Geräte Apps benötigen, die im Microsoft Store nicht verfügbar sind, verlassen Sie den S Modus. Das Verlassen des S Modus ist eine Möglichkeit. Sobald Sie den S Modus verlassen haben, können Sie jedoch nicht in den Windows 10 S Modus zurückkehren.

In den folgenden Schritten wird gezeigt, wie Sie ein Profil erstellen, das den S Modus auf Windows 10 (1809 oder höher) kontrolliert.

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie einen **Namen** und eine **Beschreibung** für das Profil ein. Geben Sie zum Beispiel etwas wie `Windows 10 switch off S mode` ein.
4. Wählen Sie unter **Plattform** die Option **Windows 10 und höher** aus.
5. Wählen Sie für **Profiltyp** **Edition upgrade** (Editionsupgrade) aus.
6. Wählen Sie **Mode switch (Windows Insider only)** (Modus wechseln (nur Windows-Insider)) aus, und legen Sie die Eigenschaft **Switch out of S mode** (S Modus verlassen) fest. Folgende Optionen sind verfügbar:

    - **No configuration** (Keine Konfiguration): Ein Gerät im S Modus bleibt im S Modus. Ein Endbenutzer kann das Gerät aus dem S Modus holen.
    - **Keep in S mode** (Im S Modus lassen): Der Endbenutzer kann das Gerät nicht aus dem S Modus holen.
    - **Switch** (Verlassen): Das Gerät wird aus dem S Modus geholt.

7. Klicken Sie auf **OK**, um die Änderungen zu speichern. Klicken Sie auf **Erstellen**, um das Profil zu erstellen.

Das Profil wird erstellt und in der Profilliste aufgeführt.

## <a name="next-steps"></a>Nächste Schritte

Dieses Profil meinen Gruppen [zuweisen](device-profile-assign.md).

>[!NOTE]
>Wenn Sie später die Richtlinienzuweisung entfernen, wird die Windows-Version auf dem Gerät nicht wiederhergestellt und wird weiterhin normal ausgeführt.
