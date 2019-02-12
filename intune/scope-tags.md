---
title: Filtern von Richtlinien mit Bereichsmarkierungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie Bereichsmarkierungen, um Konfigurationsprofile nach bestimmten Rollen zu filtern.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9441f1c69e3d445d6174521ad2c9ef5c7a6db2be
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835536"
---
# <a name="use-scope-tags-to-filter-policies"></a>Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien

Mithilfe von Bereichsmarkierungen können Sie Richtlinien mit benutzerdefinierten Markierungen filtern, die Sie erstellen. Auf Rollen und Apps können Sie Bereichsmarkierungen anwenden.

Erstellen Sie beispielsweise eine Bereichsmarkierung namens „Technikabteilung“, und ordnen Sie sie Konfigurationsprofilen zu, die sich auf die Technikabteilung beziehen. Weisen Sie die gleiche Markierung einer Rolle „Technikadministratoren“ zu. Sie werden dann lediglich die Richtlinien mit der Markierung „Technikabteilung“ sehen.

## <a name="to-create-a-scope-tag"></a>So erstellen Sie eine Bereichsmarkierung

Wählen Sie **Rollen** > **Bereich (Markierungen)** > **Erstellen** aus.

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>So fügen Sie eine Bereichsmarkierung einem Konfigurationsprofil hinzu

Wählen Sie **Gerätekonfiguration** > **Profile** aus, wählen Sie ein Profil aus, und klicken Sie auf **Eigenschaften** > **Bereich (Markierungen)**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>So weisen Sie einer Rolle eine Bereichsmarkierung zu

Wählen Sie **Rollen** > **Alle Rollen** > **Richtlinien- und Profil-Manager** > **Zuweisungen** > **Bereich (Markierungen)** aus.

## <a name="to-assign-a-scope-tag-to-an-app"></a>So weisen Sie einer App eine Bereichsmarkierung zu

Wählen Sie **Client-Apps** > **Apps** aus. Wählen Sie dann eine App und **Eigenschaften** > **Bereich (Markierungen)** > **Hinzufügen** aus. Anschließend klicken Sie auf die gewünschten Markierungen und auf **wählen** > **OK** > **Speichern**.


## <a name="next-steps"></a>Nächste Schritte

Verwalten Sie Ihre [Rollen](role-based-access-control.md) und [Profile](device-profile-assign.md).

