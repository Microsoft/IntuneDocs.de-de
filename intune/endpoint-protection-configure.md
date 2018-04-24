---
title: Konfigurieren von Endpoint Protection-Einstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie Endpoint Protection-Einstellungen, wenn Sie in Microsoft Intune ein macOS- oder Windows 10-Geräteprofil erstellen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b960b837cef5941fac829eeb878eb520b0274fba
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Hinzufügen der Endpoint Protection-Einstellungen in Intune

Mithilfe von Endpoint Protection können Sie verschiedene Sicherheitsfeatures auf Ihren Geräten steuern – z.B. die Firewall, BitLocker, das Zulassen und Blockieren von Apps, Windows Defender und die Verschlüsselung. Sie können diese Einstellungen in Microsoft Intune mithilfe von Geräteprofilen konfigurieren.

Beispielsweise können Sie ein Endpoint Protection-Profil erstellen, über das nur macOS-Benutzer Apps aus dem Mac App Store installieren können. Stattdessen können Sie auch Windows SmartScreen aktivieren, wenn Sie Apps auf Windows 10-Geräten ausführen.

In diesem Artikel wird erläutert, wie Sie ein Profil erstellen können. Für weitere Informationen zu den verfügbaren Einstellungen können Sie auf Ihre Geräteplattform klicken.

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Erstellen von Geräteprofilen mit Endpoint Protection-Einstellungen

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
4. Geben Sie einen **Namen** und eine **Beschreibung** für das Endpoint Protection-Profil ein.
5. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform aus, auf die Sie benutzerdefinierte Einstellungen anwenden möchten. Derzeit können Sie eine der folgenden Plattformen für die Einstellungen für Geräteeinschränkungen auswählen:
   - **macOS**
   - **Windows 10 und höher**
6. Wählen Sie in der Dropdownliste **Profiltyp** die Option **Endpoint Protection** aus. 
7. Die konfigurierbaren Einstellungen variieren je nach der ausgewählten Plattform. In den folgenden Themen finden Sie ausführliche Informationen zu den Einstellungen für die einzelnen Plattformen:
   - [Einstellungen für macOS](endpoint-protection-macos.md)
   - [Einstellungen für Windows 10](endpoint-protection-windows-10.md)
8. Navigieren Sie anschließend zurück zur Seite **Profil erstellen**, und klicken Sie auf **Erstellen**.

Das Profil wird erstellt und auf der Seite mit der Profilliste angezeigt. Informationen zur Zuweisung dieses Profils zu Gruppen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).

## <a name="next-steps"></a>Nächste Schritte
Informationen zur Zuweisung dieses Profils an Gruppen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).
