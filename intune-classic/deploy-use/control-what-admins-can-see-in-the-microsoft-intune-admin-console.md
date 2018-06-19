---
title: Anpassen von Konsolenansichten für Administratorrollen
description: Filtern Sie wie in diesem Thema beschrieben die Intune-Verwaltungskonsolenansicht, damit Administratoren nur die Elemente anzeigen können, die sie für ihre Rolle benötigen.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bdc248689f586a44f4c84568b9d9f9c1fa3e059a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31013635"
---
# <a name="customize-intune-console-views-according-to-admin-roles"></a>Anpassen von Intune-Konsolenansichten an Administratorrollen

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Sie können die Microsoft Intune-Verwaltungskonsolenansicht filtern, damit Administratoren nur die Elemente anzeigen können, die sie für ihre Rolle benötigen. Beispielsweise empfiehlt es sich, nur den Operatoren der Verwaltungskonsole die Erlaubnis zu erteilen, Malwaredefinitionen zu aktualisieren oder die Kennung auf Geräten zurückzusetzen. Dies erfolgt mithilfe der vorab festgelegten **Bezeichnungen**, die Sie bestimmten Benutzern zuweisen. Wenn diese Benutzer auf die Verwaltungskonsole zugreifen, sehen sie nur die für ihre Bezeichnung bestimmten Elemente.

## <a name="to-create-a-custom-view"></a>So erstellen Sie eine benutzerdefinierte Ansicht

1. Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) die Option **Admin** &gt; **Dienstadministratoren** aus.

2. Wählen Sie aus der Liste der Dienstadministratoren den Benutzer aus, dessen Bezeichnung Sie ändern möchten, und wählen Sie anschließend **Zugriff verwalten** aus.

3. Wählen Sie im Dialogfeld **Zugriff verwalten** die Zugriffsebene, die dem ausgewählten Benutzer zugewiesen werden soll. Es gibt folgende Auswahlmöglichkeiten:

   -   **Vollzugriff**
   -   **Schreibgeschützter Zugriff**
   -   **Helpdesk – Gruppenknoten**

   „Vollzugriff“ und „schreibgeschützter Zugriff“ sind selbsterklärend. <!--- **Helpdesk - Groups Node** allows users to choose from one of the following designations that provide custom levels of access to the Intune admin console:--->

   **Helpdesk – Gruppenknoten** beschränkt die Möglichkeiten, was der Administrator anzeigen und ausführen kann auf Folgendes:

   -   Anzeigen der Listen von Benutzern und Geräten. Der Administrator kann die Ansicht nicht mithilfe von Filtern ändern. Sie können jedoch mithilfe der Gruppenfilterung definieren, was dem Administrator angezeigt wird. Weitere Informationen finden Sie unter [Verwenden von Gruppen zum Verwalten von Benutzern und Geräten in Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

   -   Drucken der Liste der Benutzer und Geräte

   -   Exportieren der Liste der Benutzer und Geräte

   -   Anzeigen der Eigenschaften eines Benutzers oder Geräts

   -   Führen Sie die folgenden Remoteaufgaben aus:

       -   Vollständige Malwareüberprüfung ausführen

       -   Malwareschnellüberprüfung ausführen

       -   Computer neu starten

       -   Update für Malwaredefinitionen ausführen

       -   Richtlinien aktualisieren

       -   Inventur aktualisieren

       -   Remotesperrung eines Geräts

       -   Zurücksetzen einer Kennung

Wenn der von Ihnen konfigurierte Administrator das nächste Mal die Intune-Verwaltungskonsole öffnet, wird ihm die von Ihnen festgelegte Zugriffsebene zugewiesen.
