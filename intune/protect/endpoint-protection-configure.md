---
title: Konfigurieren von Endpoint Protection-Einstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie Endpoint Protection-Einstellungen, wenn Sie in Microsoft Intune ein macOS- oder Windows 10-Geräteprofil erstellen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: 45cdbfe98bca8f7b0e307ed47ad3f78193e6d04c
ms.sourcegitcommit: 15e099a9a1e18296580bb345610aee7cc4acd126
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164568"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Hinzufügen der Endpoint Protection-Einstellungen in Intune

Mit Intune können Sie Gerätekonfigurationsprofile verwenden, um allgemeine Sicherheitsfunktionen für den Endpunktschutz auf Geräten zu verwalten, einschließlich:

- Firewall
- BitLocker
- Zulassen und Sperren von Apps
- Microsoft Defender und Verschlüsselung

Beispielsweise können Sie ein Endpoint Protection-Profil erstellen, über das nur macOS-Benutzer Apps aus dem Mac App Store installieren können. Stattdessen können Sie auch Windows SmartScreen aktivieren, wenn Sie Apps auf Windows 10-Geräten ausführen.

Bevor Sie ein Profil erstellen, lesen Sie die folgenden Artikel, in denen die Einstellungen für den Endpunktschutz dargelegt werden, die Intune für die jeweilige unterstützte Plattform verwalten kann:

- [Einstellungen für macOS](endpoint-protection-macos.md)
- [Einstellungen für Windows 10](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Erstellen von Geräteprofilen mit Endpoint Protection-Einstellungen

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.

3. Geben Sie einen **Namen** und eine **Beschreibung** für das Endpoint Protection-Profil ein.

4. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform aus, auf die Sie benutzerdefinierte Einstellungen anwenden möchten. Derzeit können Sie eine der folgenden Plattformen für die Einstellungen für Geräteeinschränkungen auswählen:

   - **macOS**
   - **Windows 10 und höher**

5. Wählen Sie in der Dropdownliste **Profiltyp** die Option **Endpoint Protection** aus.

6. Die konfigurierbaren Einstellungen variieren je nach der ausgewählten Plattform. Weitere Informationen finden Sie unter:

   - [Einstellungen für macOS](endpoint-protection-macos.md)
   - [Einstellungen für Windows 10](endpoint-protection-windows-10.md)

7. Nachdem Sie die anwendbaren Einstellungen konfiguriert haben, wählen Sie auf der Seite **Profil erstellen** den Befehl **Erstellen** aus.

   Das Profil wird erstellt und auf der Seite mit der Profilliste angezeigt. Informationen zur Zuweisung dieses Profils zu Gruppen finden Sie unter [Zuweisen von Geräteprofilen](../configuration/device-profile-assign.md).

## <a name="add-custom-firewall-rules-for-windows-10-devices"></a>Hinzufügen benutzerdefinierter Firewallregeln für Windows 10-Geräte

Wenn Sie Microsoft Defender Firewall als Teil eines Profils konfigurieren, das Endpoint Protection-Regeln für Windows 10 umfasst, können Sie benutzerdefinierte Regeln für Firewalls konfigurieren. Benutzerdefinierte Regeln ermöglichen es Ihnen, die vordefinierten Firewallregeln zu erweitern, die für Windows 10 unterstützt werden.

Wenn Sie Profile mit benutzerdefinierten Firewallregeln planen, sollten Sie die folgenden Informationen berücksichtigen, die sich auf das Gruppieren von Firewallregeln in ihren Profilen auswirken können:

- Jedes Profil unterstützt bis zu 150 Firewallregeln. Wenn Sie mehr als 150 Regeln verwenden, sollten Sie zusätzliche Profile erstellen, die jeweils auf 150 Regeln beschränkt sind.

- Wenn eine einzelne Regel nicht angewendet werden kann, schlagen für alle Regeln sämtliche Profile fehl, und keine der Regeln wird auf das Gerät angewendet.

- Wenn eine Regel nicht angewendet werden kann, werden für alle Regeln im Profil ein Fehler gemeldet. Intune kann nicht feststellen, welche Regel fehlgeschlagen ist.  

Die Firewallregeln, die von Intune verwaltet werden können, werden im Artikel [Windows-Firewall-Konfigurationsdienstanbieter]( https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) ausführlich beschrieben. Die Liste der benutzerdefinierten Firewalleinstellungen für Windows 10-Geräte, die von Intune unterstützt werden, finden Sie unter [Custom Firewall rules (Benutzerdefinierte Firewallregeln)](endpoint-protection-windows-10.md#firewall-rules).

### <a name="to-add-custom-firewall-rules-to-an-endpoint-protection-profile"></a>So fügen Sie einem Endpoint Protection-Profil benutzerdefinierte Firewallregeln hinzu

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.

3. Wählen Sie unter *Plattform* die Option **Windows 10 und höher** und anschließend unter *Profiltyp* **Endpoint Protection** aus.

4. Klicken Sie erst auf **Microsoft Defender Firewall**, um die Konfigurationsseite zu öffnen, und anschließend unter *Firewallregeln* auf **Hinzufügen**, um die Seite **Regel erstellen** zu öffnen.

5. Legen Sie Einstellungen für die Firewallregel fest, und klicken Sie dann auf **OK**, um diese zu speichern. Informationen zu den verfügbaren Optionen für benutzerdefinierte Firewallregeln in der Dokumentation finden Sie unter [Custom Firewall rules (Benutzerdefinierte Firewallregeln)](endpoint-protection-windows-10.md#firewall-rules).

6. Sobald Sie die Regel gespeichert haben, wird sie auf der Seite *Microsoft Defender Firewall* in der Liste mit den Regeln aufgeführt.

7. Sie können Regeln ändern, indem Sie die gewünschte Regel aus der Liste auswählen, um die Seite **Regel bearbeiten** zu öffnen.

8. Wenn Sie eine Regel aus einem Profil löschen möchten, klicken Sie erst auf die Auslassungspunkte **(...)** und anschließend auf **Löschen**.

9. Sie können die Reihenfolge ändern, in der die Regeln angezeigt werden, indem Sie im oberen Bereich der Regelliste auf das Symbol mit den *Pfeilen nach oben und unten* klicken.

## <a name="next-steps"></a>Nächste Schritte

Informationen zur Zuweisung dieses Profils an Gruppen finden Sie unter [Zuweisen von Geräteprofilen](../configuration/device-profile-assign.md).
