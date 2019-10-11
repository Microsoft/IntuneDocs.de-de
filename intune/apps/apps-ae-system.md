---
title: Hinzufügen von Android Enterprise-System-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie Android Enterprise-System-Apps zu Microsoft Intune hinzufügen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ffc99b34016eba6511f63d1df2184abc3cae858
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725165"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Hinzufügen von Android Enterprise-System-Apps zu Microsoft Intune

Bevor Sie einem Gerät oder einer Gruppe von Benutzern eine App zuweisen, müssen Sie diese zunächst zu Microsoft-Intune hinzufügen. System-Apps werden auf Android Enterprise-Geräten unterstützt. Sie können eine System-App für [dedizierte Android Enterprise-Geräte](../enrollment/android-kiosk-enroll.md) oder [vollständig verwaltete Geräte](../enrollment/android-fully-managed-enroll.md) aktivieren.

## <a name="add-the-app"></a>Hinzufügen der App

Mit den folgenden Schritten können Sie eine Android Enterprise-System-App aus dem Azure-Portal zu Intune hinzufügen:

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie im **Intune**-Bereich die Option **Client-Apps** > **Apps** > **Hinzufügen** aus.
3. Wählen Sie im Bereich **App hinzufügen** aus den verfügbaren **anderen** Typen den Typ **Android Enterprise-System-App** aus.
4. Wählen Sie zum Konfigurieren der App-Informationen die Option **Konfigurieren** aus, und geben Sie die folgenden Informationen an:
    - **App-Name:** Geben Sie den Namen der App ein.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.  
    - **Paketname:** Geben Sie einen Paketnamen ein. Intune überprüft, ob der Paketname gültig ist.
5. Wählen Sie **OK** aus.
6. Wählen Sie **Hinzufügen** aus.

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können. 

Android Enterprise-System-Apps aktivieren oder deaktivieren Apps, die bereits Teil der Plattform sind. Weisen Sie die System-App als **Erforderlich** zu, um eine App zu aktivieren. Weisen Sie die System-App als **Deinstallieren** zu, um eine App zu deaktivieren. System-Apps können einem Benutzer nicht als verfügbar zugeordnet werden.

## <a name="next-steps"></a>Nächste Schritte

- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md)
