---
title: 'Upgraden von Windows 10-Geräten mit Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Erstellen eines Geräteprofils in Microsoft Intune zum Upgraden von Windows 10-Geräten auf neuere Versionen Sie erhalten auch Informationen zu unterstützten Upgradepfaden für Windows 10 Pro, N Edition, Education, Cloud, Enterprise, Core, Holographic und Mobile.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 994ab8e7d955d18b293e4d9e9661e0c44baaaa1f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025432"
---
# <a name="configure-windows-10-edition-upgrade-profile-in-intune"></a>Konfigurieren des Windows 10-Editionsupgradeprofils in Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Konfigurieren Sie ein Upgradeprofil in Intune, um automatisch für Windows 10-Geräte ein Upgrade auf eine andere Edition durchzuführen. Vgl. außerdem die unterstützten Upgradepfade.

## <a name="before-you-begin"></a>Vorbereitung
Bevor Sie Geräte auf die neueste Version aktualisieren, benötigen Sie eines der folgenden Dinge:

- Einen gültigen Product Key für die Installation der aktualisierten Version von Windows auf allen Geräten, die das Ziel dieser Richtlinie sind (für Windows 10-Desktopeditionen). Sie können entweder Mehrfachaktivierungsschlüssel (Multiple Activation Keys, MAK) oder KMS-Schlüssel (Key Management Server) oder eine Lizenzdatei von Microsoft verwenden, die die Lizenzierungsinformationen zum Installieren der aktualisierten Version von Windows auf allen Geräten enthält, die das Ziel dieser Richtlinie sind (für Windows 10 Mobile- und Windows 10 Holographic-Editionen).
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

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Erstellen von Geräteprofilen mit Einstellungen für Geräteeinschränkungen
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
4. Geben Sie für das Editionsupgradeprofil einen **Namen** und eine **Beschreibung** ein.
5. Wählen Sie in der Dropdownliste **Plattform** die Option **Windows 10 und höher** aus.
6. Wählen Sie in der Dropdownliste **Profiltyp** die Option **Editionsupgrade** aus.
7. Geben Sie in den Eigenschaften **Editionsupgrade** die folgenden Einstellungen an:
   - **Edition, auf die ein Upgrade durchgeführt wird:** Wählen Sie aus der Dropdownliste die Version von Windows 10 Desktop, Windows 10 Holographic oder Windows 10 Mobile aus, auf die die als Ziel angegebenen Geräte upgegradet werden sollen.
   - **Product Key:** Geben Sie den Product Key ein, den Sie von Microsoft erhalten haben, und der für das Upgrade aller als Ziel festgelegten Windows 10 Desktop-Geräte verwendet werden kann. 
    Nach dem Erstellen einer Richtlinie mit einem Product Key kann dieser nicht aktualisiert werden und wird aus Sicherheitsgründen ausgeblendet. Geben Sie den gesamten Schlüssel erneut ein, um den Product Key zu ändern.
   - **Lizenzdatei:** Klicken Sie auf **Durchsuchen**, um die Lizenzdatei auszuwählen, die Sie von Microsoft erhalten haben. Diese Lizenzdatei enthält Lizenzinformationen zu den Editionen Windows Holographic oder Windows 10 Mobile, auf die die als Ziel angegebenen Geräte upgegradet werden sollen.
8. Wenn Sie diese Vorgänge abgeschlossen haben, klicken Sie auf **Erstellen**, um die Änderungen zu speichern.

Das Profil wird erstellt und in der Profilliste aufgeführt.

## <a name="next-steps"></a>Nächste Schritte

Informationen zum Zuweisen dieses Profils an Gruppen finden Sie unter [Zuweisen von Microsoft Intune-Geräteprofilen](device-profile-assign.md).

>[!NOTE]
>Wenn Sie später die Richtlinienzuweisung entfernen, wird die Windows-Version auf dem Gerät nicht wiederhergestellt und wird weiterhin normal ausgeführt.