---
title: Erstellen einer benutzerdefinierten Rolle in Intune
description: Erfahren Sie, wie Sie eine benutzerdefinierte Rolle in Microsoft Intune erstellen.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68c2dc7df123593513c14e16e2626c7426f50b01
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207416"
---
# <a name="create-a-custom-role-in-intune"></a>Erstellen einer benutzerdefinierten Rolle in Intune

Sie können eine benutzerdefinierte Intune-Rolle erstellen, die alle für einen bestimmten Aufgabenbereich erforderlichen Berechtigungen enthält. Wenn beispielsweise eine IT-Abteilungsgruppe Anwendungen, Richtlinien und Konfigurationsprofile verwaltet, können Sie alle diese Berechtigungen gemeinsam einer benutzerdefinierten Rolle hinzufügen. Nachdem Sie eine benutzerdefinierte Rolle erstellt haben, können Sie sie allen Benutzern [zuweisen](assign-role.md), die diese Berechtigungen benötigen.

Für das Erstellen, Bearbeiten oder Zuweisen von Rollen muss das Konto in Azure AD über eine der folgenden Berechtigungen verfügen:
- **Globaler Administrator**
- **Intune-Dienstadministrator**

## <a name="to-create-a-custom-role"></a>So erstellen Sie eine benutzerdefinierte Rolle

1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Rollen** > **Alle Rollen** > **Hinzufügen** aus.

2. Geben Sie auf dem Blatt **Benutzerdefinierte Rolle hinzufügen** einen Namen und eine Beschreibung für die neue Rolle ein, und klicken Sie dann auf **Berechtigungen**.

3. Wählen Sie auf dem Blatt **Berechtigungen** die Berechtigungen aus, die Sie mit dieser Rolle verwenden möchten.

4. Wählen Sie auf dem Blatt **Bereich (Markierungen)** die Markierungen für diese Rolle aus. Diese Rolle kann auf Ressourcen zugreifen, die ebenfalls diese Markierungen aufweisen.

5. Wenn Sie fertig sind, klicken Sie auf **OK**.

6. Klicken Sie auf dem Blatt **Benutzerdefinierte Rolle hinzufügen** auf **Erstellen**. Die neue Rolle wird in der Liste auf dem Blatt **Intune-Rollen – Alle Rollen** angezeigt.


## <a name="copy-a-role"></a>Kopieren einer Rolle

Sie können auch eine vorhandene Rolle kopieren.

1. Klicken Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) auf **Rollen** > **Alle Rollen**, wählen Sie eine Rolle in der Liste aus, und klicken Sie auf **Duplizieren**.

2. Geben Sie unter **Duplicate role** (Rolle duplizieren) einen Namen ein. Stellen Sie sicher, dass Sie einen eindeutigen Namen verwenden.

3. Alle Berechtigungen und Bereichstags der ursprünglichen Rolle werden bereits ausgewählt. Anschließend können Sie **Name**, **Beschreibung** **Berechtigungen** und **Scope (Tags)** (Bereich (Tags)) der duplizierten Rolle ändern.

4. Wählen Sie **Erstellen** aus. 

## <a name="next-steps"></a>Nächste Schritte
- [Zuweisen einer Rolle an einen Benutzer](assign-role.md)
- [Erfahren Sie mehr über die rollenbasierte Zugriffssteuerung in Intune](role-based-access-control.md)
