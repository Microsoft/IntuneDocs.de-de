---
title: Zuweisen einer Rolle an einen Intune-Benutzer
description: Erfahren Sie, wie Sie einem Benutzer in Microsoft Intune eine integrierte oder benutzerdefinierte Rolle zuweisen.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 83e321e932fa2214612836ec994a9a0aa8174dd7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722201"
---
# <a name="assign-a-role-to-an-intune-user"></a>Zuweisen einer Rolle an einen Intune-Benutzer

Sie können einem Intune-Benutzer eine [integrierte](role-based-access-control.md#built-in-roles) oder [benutzerdefinierte](create-custom-role.md) Rolle zuweisen.

Für das Erstellen, Bearbeiten oder Zuweisen von Rollen muss das Konto in Azure AD über eine der folgenden Berechtigungen verfügen:
- **Globaler Administrator**
- **Intune-Dienstadministrator**

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.

3. Wählen Sie auf dem Blatt **Intune** die Option **Rollen** > **Alle Rollen** aus.

4. Klicken Sie auf dem Blatt **Intune-Rollen – Alle Rollen** auf die integrierte Rolle, die Sie zuweisen möchten.

5. Wählen Sie auf dem Blatt <*Rollenname*> – **Übersicht** die Option **Verwalten** > **Zuweisungen** aus.

6. Wählen Sie auf dem Blatt „Benutzerdefinierte Rolle“ **Zuweisen** aus.

7. Geben Sie auf dem Blatt **Rollenzuweisungen** einen **Zuweisungsnamen** und eine optionale **Zuweisungsbeschreibung** für die Zuweisung ein.

8. Wählen Sie für **Mitglieder (Gruppe)** eine Gruppe aus, die den Benutzer enthält, dem Sie die Berechtigungen erteilen möchten.

9. Wählen Sie für **Bereich (Gruppen)** eine Gruppe aus, die die Benutzer/Geräte enthält, die das oben ausgewählte Mitglied verwalten können soll.

10. Wählen Sie für **Bereich (Markierungen)** die Markierungen aus, bei denen diese Rollenzuweisung angewendet wird.

11. Wenn Sie fertig sind, klicken Sie auf **OK**. Die neue Zuweisung wird in der Liste der Zuweisungen angezeigt.


## <a name="next-steps"></a>Nächste Schritte
- [Erfahren Sie mehr über die rollenbasierte Zugriffssteuerung in Intune](role-based-access-control.md)
- [Erstellen einer benutzerdefinierten Rolle](create-custom-role.md)