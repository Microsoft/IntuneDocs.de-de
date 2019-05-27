---
title: Konfigurieren von Endpoint Protection-Einstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie Endpoint Protection-Einstellungen, wenn Sie in Microsoft Intune ein macOS- oder Windows 10-Geräteprofil erstellen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 5/17/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: c13c5d71d1ff631d7a3c84cd3f62037569757917
ms.sourcegitcommit: bc5e4dff18f5f9b79077a888f8a58dcc490708c0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975778"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Hinzufügen der Endpoint Protection-Einstellungen in Intune

Mit Intune können Sie Gerätekonfigurationsprofile verwenden, um allgemeine Sicherheitsfunktionen für den Endpunktschutz auf Geräten zu verwalten, einschließlich:
- Firewall 
- BitLocker
- Zulassen und Sperren von Apps  
- Windows Defender und Verschlüsseln

Beispielsweise können Sie ein Endpoint Protection-Profil erstellen, über das nur macOS-Benutzer Apps aus dem Mac App Store installieren können. Stattdessen können Sie auch Windows SmartScreen aktivieren, wenn Sie Apps auf Windows 10-Geräten ausführen.

Bevor Sie ein Profil erstellen, lesen Sie die folgenden Artikel, in denen die Einstellungen für den Endpunktschutz dargelegt werden, die Intune für die jeweilige unterstützte Plattform verwalten kann: 
   - [Einstellungen für macOS](endpoint-protection-macos.md)
   - [Einstellungen für Windows 10](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Erstellen von Geräteprofilen mit Endpoint Protection-Einstellungen

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=20909) an.
3. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
4. Geben Sie einen **Namen** und eine **Beschreibung** für das Endpoint Protection-Profil ein.
5. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform aus, auf die Sie benutzerdefinierte Einstellungen anwenden möchten. Derzeit können Sie eine der folgenden Plattformen für die Einstellungen für Geräteeinschränkungen auswählen:
   - **macOS**
   - **Windows 10 und höher**
6. Wählen Sie in der Dropdownliste **Profiltyp** die Option **Endpoint Protection** aus. 
7. Die konfigurierbaren Einstellungen variieren je nach der ausgewählten Plattform. Weitere Informationen:
   - [Einstellungen für macOS](endpoint-protection-macos.md)
   - [Einstellungen für Windows 10](endpoint-protection-windows-10.md)  

8. Nachdem Sie die anwendbaren Einstellungen konfiguriert haben, wählen Sie auf der Seite **Profil erstellen** den Befehl **Erstellen** aus.

   Das Profil wird erstellt und auf der Seite mit der Profilliste angezeigt. Informationen zur Zuweisung dieses Profils zu Gruppen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).


## <a name="next-steps"></a>Nächste Schritte  

Informationen zur Zuweisung dieses Profils an Gruppen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).
