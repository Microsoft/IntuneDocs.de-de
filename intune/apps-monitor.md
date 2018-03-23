---
title: Überwachen von App-Informationen und -Zuweisungen
titlesuffix: Microsoft Intune
description: Nachdem Sie Benutzern oder Geräten eine App zugewiesen haben, können Sie mithilfe dieser Informationen den Status der App überwachen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2d1ca013b7000282316a17e02dcb38b3d4f27958
ms.sourcegitcommit: 820f950d1fc80b1eb5db1b0cf77f44d92a969951
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Überwachen von App-Informationen und -Zuweisungen mit Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune bietet eine Reihe von Möglichkeiten, mit denen Sie die Eigenschaften von verwalteten Apps sowie deren Zuweisungsstatus überwachen können.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie **Mobile Apps** und anschließend in der Gruppe **Verwalten** die Option **Apps** aus.
5. Wählen Sie in der Liste der Apps eine App aus, die Sie überwachen möchten. Daraufhin wird das App-Blatt mit einer Übersicht des Gerätestatus und des Benutzerstatus angezeigt.

## <a name="app-overview-blade"></a>Übersicht über das Blatt „App“

Auf dem Blatt für die spezifische App können Sie sich Details zum Status einer App in Ihrer Umgebung ansehen.

### <a name="essentials"></a>Essentials
Der Abschnitt **Zusammenfassung** enthält die folgenden Informationen zur App:

 | **App-Details**            | **Beschreibung**                                                      |
|------------------------|------------------------------------------------------------------|
| **Herausgeber**          | Herausgeber der App                                            |
| **Betriebssystem**   | Das Betriebssystem der App (Windows, iOS, Android usw.) |
| **Erstellt**             | Das Datum und die Uhrzeit, als diese Version erstellt wurde                         |
| **Zugewiesen**           | **Nein** oder **Ja**, wenn die App zugewiesen wurde.                  |

### <a name="device-and-user-status-graphs"></a>Diagramme zum Geräte- und Benutzerstatus
Das Diagramm zeigt die Zahl für die folgenden Status an:

| **Gerätestatus**       | **Beschreibung**                                       |
|-----------------------|-------------------------------------------------------|
| **Installiert**         | Die Anzahl der installierten Apps.                         |
| **Nicht installiert**     | Die Anzahl der nicht installierten Apps.                     |
| **Fehlgeschlagen**            | Die Anzahl nicht erfolgreicher Installationen.                   |
| **Installation steht aus**   | Die Anzahl der Apps, deren Installation bevorsteht. |
| **Nicht verfügbar**           | Die Anzahl der Apps, deren Status nicht verfügbar ist.            |

### <a name="device-install-status"></a>Geräteinstallationsstatus

Eine Liste des Gerätestatus wird angezeigt, wenn Sie im Abschnitt **Überwachen** die Option **Geräteinstallationsstatus** auswählen. Die Tabelle mit den Details enthält die folgenden Spalten:

| **Gerätespalte**      | **Beschreibung**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Gerätename**      | Der Name des Geräts auf Plattformen, die das Benennen von Geräten ermöglichen. Auf anderen Plattformen wird von Intune ein Name anhand anderer Eigenschaften erstellt. Dieses Attribut kann nicht für alle Geräte zur Verfügung stehen.                                                                       |
| **Benutzername**        | Der Name des Benutzers.                                                                                                                                                                                                                                      |
| **Plattform**         | Das Betriebssystem des Geräts (Windows, iOS, Android usw.)                                                                                                                                                                                           |
| **Version**          | Die Versionsnummer der App. Für branchenspezifische Apps wird die vollständige Versionsnummer der App angezeigt. Die vollständige Versionsnummer gibt ein bestimmtes Release der App an. Die Nummer wird als _Version_(_Build_) angezeigt. Beispielsweise 2.2(2.2.17560800). |
| **Status**           | Der Status der App.                                                                                                                                                                                                                                     |
| **Statusdetails**   | Details zum Status.                                                                                                                                                                                                                                     |
| **Letztes Einchecken**    | Datum der letzten Synchronisierung mit Intune des Geräts.                                                                                                                                                                                                                  |


### <a name="user-install-status"></a>Benutzerinstallationsstatus

Eine Liste des Benutzerstatus wird angezeigt, wenn Sie im Abschnitt **Überwachen** die Option **Benutzerinstallationsstatus** auswählen. Die Tabelle mit den Details enthält die folgenden Spalten:

| **Benutzerspalte**     | **Beschreibung**                           |
|---------------------|-------------------------------------------|
| **Name**            | Der Name des Benutzers in Azure AD.         |
| **Benutzername**       | Der eindeutige Name des Benutzers.              |
| **Installationen**   | Anzahl der installierten Apps, die vom Benutzer verwendet werden. |
| **Fehler**        | Anzahl der nicht erfolgreichen Installationen des Benutzers.     |
| **Nicht installiert**   | Anzahl der nicht vom Benutzer installierten Apps. |


## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zum Arbeiten mit Ihren Intune-Daten finden Sie unter [Verwenden des Data Warehouse von Intune](reports-nav-create-intune-reports.md).
- Weitere Informationen zu App-Konfigurationsrichtlinien finden Sie unter [App-Konfigurationsrichtlinien für Intune](app-configuration-policies-overview.md).