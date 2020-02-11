---
title: Hinzufügen von Android Enterprise-System-Apps zu Microsoft Intune
titleSuffix: ''
description: Erfahren Sie, wie Sie Android Enterprise-System-Apps zu Microsoft Intune hinzufügen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
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
ms.openlocfilehash: 613369070d847265f371a7b228a2b6d81bf813fe
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755254"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Hinzufügen von Android Enterprise-System-Apps zu Microsoft Intune

Bevor Sie einem Gerät oder einer Gruppe von Benutzern eine App zuweisen, müssen Sie diese zunächst zu Microsoft-Intune hinzufügen. System-Apps werden auf Android Enterprise-Geräten unterstützt. Sie können eine System-App für [dedizierte Android Enterprise-Geräte](../enrollment/android-kiosk-enroll.md) oder [vollständig verwaltete Geräte](../enrollment/android-fully-managed-enroll.md) aktivieren.

## <a name="add-the-app"></a>Hinzufügen der App

Mit den folgenden Schritten können Sie eine Android Enterprise-System-App aus dem Azure-Portal zu Intune hinzufügen:

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** > **Hinzufügen** aus.
3. Wählen Sie im Bereich **App-Typ auswählen** aus den verfügbaren **Sonstigen** Typen **Android Enterprise-System-App** aus.
4. Klicken Sie auf **Auswählen**. Die **App hinzufügen**-Schritte werden angezeigt.
Fügen Sie auf der Seite **App-Informationen** die App-Details hinzu:
    - **App-Name:** Geben Sie den Namen der App ein.
    - **Herausgeber**: Geben Sie den Namen des Herausgebers der App ein.  
    - **Paketname:** Geben Sie einen Paketnamen ein. Intune überprüft, ob der Paketname gültig ist.
5. Klicken Sie auf **Weiter**, um die Seite **Bereichsmarkierungen** anzuzeigen.
8. Klicken Sie auf **Bereichstags auswählen**, um optional Bereichsmarkierungen für die App hinzuzufügen. Weitere Informationen dazu finden Sie unter [Verwenden der rollenbasierten Zugriffssteuerung und Bereichsmarkierungen für verteilte IT](~/fundamentals/scope-tags.md).
9. Klicken Sie auf **Weiter**, um die Seite **Zuweisungen** anzuzeigen.
10. Wählen Sie die Gruppenzuweisungen für die App aus. Weitere Informationen finden Sie unter [Hinzufügen von Gruppen zum Organisieren von Benutzern und Geräten](~/fundamentals/groups-add.md). 
11. Klicken Sie auf **Weiter**, um die Seite **Überprüfen + erstellen** anzuzeigen. Überprüfen Sie die Werte und Einstellungen, die Sie für die App eingegeben haben.
12. Klicken Sie abschließend auf **Erstellen**, um Intune die App hinzuzufügen.

Die von Ihnen erstellte App wird im Blatt **Übersicht** angezeigt.

> [!NOTE]
> Sie müssen mit dem OEM Ihres Geräts zusammenarbeiten, um den Paketnamen der App zu finden, die Sie aktivieren/deaktivieren möchten.

Die von Ihnen erstellte App wird in der Liste der Apps angezeigt, in der Sie sie den ausgewählten Gruppen zuweisen können. 

Android Enterprise-System-Apps aktivieren oder deaktivieren Apps, die bereits Teil der Plattform sind. Weisen Sie die System-App als **Erforderlich** zu, um eine App zu aktivieren. Weisen Sie die System-App als **Deinstallieren** zu, um eine App zu deaktivieren. System-Apps können einem Benutzer nicht als verfügbar zugeordnet werden.


## <a name="next-steps"></a>Nächste Schritte

- [Das Zuweisen von Apps zu Gruppen](apps-deploy.md)
