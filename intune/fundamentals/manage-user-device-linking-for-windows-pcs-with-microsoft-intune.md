---
title: Verwalten von Verknüpfungen zwischen Benutzern und Geräten für Windows-PCs
titleSuffix: Microsoft Intune
description: Verknüpfen eines Benutzers mit einem vom Intune verwalteten Windows-PC.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.assetid: 53c99d63-c312-442a-8a71-de1b10fcd39b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: b21ee66139cb37aba80d6f1b2e3f40b5ab3c77a3
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502677"
---
# <a name="manage-user-device-linking-for-windows-pcs"></a>Verwalten von Verknüpfungen zwischen Benutzern und Geräten für Windows-PCs

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Die Informationen in diesem Thema gelten nur für Windows-Desktops, die Sie als PCs mithilfe des Intune-Softwareclients verwalten. 

Damit Sie Software für einen Benutzer bereitstellen können, müssen Sie diesen zunächst mit einem PC verknüpfen. Sie können einen Benutzer mit mehreren PCs verknüpfen, aber einzelne PCs nur mit jeweils einem Benutzer. Benutzer werden automatisch mit den PCs verknüpft, die sie über das Unternehmensportal in Intune registrieren.

Weitere Informationen zum primären Benutzer eines Geräts finden Sie unter [Suchen des primären Benutzers](../remote-actions/find-primary-user.md).

So verknüpfen Sie einen Benutzer mit einem PC

1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com/) die Option **Gruppen** &gt; **Alle Geräte** aus (oder eine andere Gruppe, in der der PC enthalten ist, den Sie mit einem Benutzer verknüpfen möchten).

2. Wählen Sie den PC aus, den Sie mit einem Benutzer verknüpfen möchten, und dann **Benutzer verknüpfen** aus.

   Im Dialogfeld **Benutzer verknüpfen** wird eine Liste verfügbarer Benutzer mit ihren Anzeigenamen, Benutzer-IDs und der Anzahl von PCs angezeigt, mit denen die Benutzer jeweils aktuell verknüpft sind. Wenn ein Benutzer bereits mit dem ausgewählten PC verknüpft ist, werden Name und Benutzer-ID des Benutzers unter **Aktueller Benutzer**angezeigt. Wenn der PC mit keinem Benutzer verknüpft ist, wird unter **Aktueller Benutzer** der Wert **Kein Benutzer**angezeigt.

3. Führen Sie eines der folgenden Verfahren aus:

   - Wählen Sie **Abbrechen** aus, um die Verknüpfung des PC mit einem ggf. vorhandenen aktuellen Benutzer beizubehalten.

   - Klicken Sie zum Entfernen der Verknüpfung mit dem aktuellen Benutzer ggf. auf <strong>Verknüpfung entfernen **&gt;** OK</strong>.

   - Zum Verknüpfen des PC mit einem neuen Benutzer wählen Sie diesen in der Liste **Alle Benutzer** aus. Überprüfen Sie, ob die Benutzerdaten korrekt sind, und wählen Sie **OK** aus.

> [!TIP]
> Wenn Sie die Fähigkeit der Endbenutzer, sich mit PCs zu verknüpfen, einschränken möchten, aktivieren Sie die Option **Fähigkeit der Benutzer einschränken, sich mit PCs zu verknüpfen** in der Richtlinie **-Microsoft Intune-Agent-Einstellungen**.

## <a name="see-also"></a>Siehe auch

[Allgemeine Aufgaben zur Verwaltung von Windows-PCs mit dem Intune-Softwareclient](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
