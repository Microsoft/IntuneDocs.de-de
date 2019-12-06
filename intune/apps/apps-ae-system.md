---
title: Hinzufügen von Android Enterprise-System-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie Android Enterprise-System-Apps zu Microsoft Intune hinzufügen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d45455a97f8016527dce49839b5493f16b173d43
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563657"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Hinzufügen von Android Enterprise-System-Apps zu Microsoft Intune

Bevor Sie einem Gerät oder einer Gruppe von Benutzern eine App zuweisen, müssen Sie diese zunächst zu Microsoft-Intune hinzufügen. System-Apps werden auf Android Enterprise-Geräten unterstützt. Sie können eine System-App für [dedizierte Android Enterprise-Geräte](../enrollment/android-kiosk-enroll.md) oder [vollständig verwaltete Geräte](../enrollment/android-fully-managed-enroll.md) aktivieren.

## <a name="add-the-app"></a>Hinzufügen der App

Mit den folgenden Schritten können Sie eine Android Enterprise-System-App aus dem Azure-Portal zu Intune hinzufügen:

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus.
3. Wählen Sie im Bereich **App hinzufügen** aus den verfügbaren **anderen** Typen den Typ **Android Enterprise-System-App** aus.
4. Klicken Sie auf **Konfigurieren**, und geben Sie dann die folgenden Informationen an, um die App-Informationen zu konfigurieren:
    - **App-Name:** Geben Sie den Namen der App ein.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.  
    - **Paketname:** Geben Sie einen Paketnamen ein. Intune überprüft, ob der Paketname gültig ist.
5. Wählen Sie **OK** aus.
6. Wählen Sie **Hinzufügen** aus.

> [!NOTE]
> Sie müssen mit dem OEM Ihres Geräts zusammenarbeiten, um den Paketnamen der App zu finden, die Sie aktivieren/deaktivieren möchten.

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können. 

Android Enterprise-System-Apps aktivieren oder deaktivieren Apps, die bereits Teil der Plattform sind. Weisen Sie die System-App als **Erforderlich** zu, um eine App zu aktivieren. Weisen Sie die System-App als **Deinstallieren** zu, um eine App zu deaktivieren. System-Apps können einem Benutzer nicht als verfügbar zugeordnet werden.


## <a name="next-steps"></a>Nächste Schritte

- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md)
