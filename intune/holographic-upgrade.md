---
title: Aktualisieren von Windows Holographic auf Windows Holographic for Business
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Geräte, die Windows Holographic ausführen, auf Windows Holographic for Business aktualisieren
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 735cd658e78a68156957d54be02f32b41812495e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179200"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Aktualisieren von Geräten, die Windows Holographic ausführen, auf Windows Holographic for Business


Zum Verwalten von Geräten, die Windows Holographic mit Microsoft Intune ausführen, müssen Sie die Geräte von Windows Holographic auf Windows Holographic for Business zu upgraden. Sie können ein Editionsupgradeprofil erstellen, um das Upgrade auszuführen. Für Microsoft HoloLens können Sie die Commercial Suite erwerben, um die erforderliche Lizenz für das Upgrade zu erhalten. Weitere Informationen finden Sie unter [Entsperren der Features von Windows Holographic für Unternehmen](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise).

## <a name="to-set-up-an-edition-upgrade-device-configuration-profile"></a>So richten Sie ein Editionsupgrade- Gerätekonfigurationsprofil ein

1. Melden Sie sich mit Ihrem Administratorkonto beim [Azure-Portal](https://portal.azure.com) an.


2.  Klicken Sie auf **Gerätekonfiguration**, **Profile** und dann auf **Profil erstellen**.

    ![Profil erstellen](media/Holographic-create-profile.png)

3.  Geben Sie auf der Seite **Profil erstellen** einen Namen für das Profil ein, wählen Sie **Windows 10 und höher** für die Plattform aus, und klicken Sie für den Profiltyp auf **Editionsupgrade**. Klicken Sie auf **Einstellungen konfigurieren**.

5. Klicken Sie auf der Seite **Editionsupgrade** unter **Edition to upgrade to** (Edition, auf die ein Upgrade ausgeführt werden soll) auf die Option **Windows 10 Holographic for Business**. Navigieren Sie unter **Lizenzdatei** zu der XML-Lizenzdatei, die für Sie bereitgestellt wurde, und wählen Sie sie aus.

    ![Geben Sie den XML-Dateinamen ein.](media/Holographic-edition-upgrade.png)
 
5.  Klicken Sie auf **OK** und dann auf **Erstellen**, um das Profil zu erstellen.


## <a name="deploy-the-edition-upgrade-policy"></a>Bereitstellen der Editionsaktualisierungsrichtlinie

Als Nächstes weisen Sie das Editionsupgradeprofil ausgewählten Gruppen oder Geräten zu.

1. Klicken Sie auf dem Profil, das Sie in den vorherigen Schritten erstellt haben, auf **Zuweisungen**.

2. Wählen Sie auf der Seite **Zuweisungen** die Benutzergruppen und Geräte aus, die Sie in Richtlinie einschließen bzw. von ihr ausschließen möchten.

![Ein- und Ausschließen von Gruppen](media/Holographic-groups.PNG)

Wenn diese Benutzer oder Geräte in Intune registriert sind, wird das Editionsupgradeprofil angewendet. 

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Gruppen finden Sie unter [Erste Schritte mit Gruppen](get-started-groups.md).


