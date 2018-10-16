---
title: Überwachen von App-Informationen und -Zuweisungen
titlesuffix: Microsoft Intune
description: Nachdem Sie Benutzern oder Geräten eine App zugewiesen haben, können Sie mithilfe dieser Informationen den Status der App überwachen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 09e4cfc314ea21294cd3de62611a089ec724a683
ms.sourcegitcommit: f69f2663ebdd9c1def68423e8eadf30f86575f7e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "49075626"
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>Überwachen von App-Informationen und -Zuweisungen mit Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune bietet verschiedene Möglichkeiten, mit denen Sie die Eigenschaften von Apps überwachen, die Sie verwalten, sowie den App-Zuweisungsstatus verwalten können.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Menü **Intune** die Option **Client-Apps** aus.
4. Wählen Sie im Abschnitt **Verwalten** des Menüs **Apps** aus.
5. Wählen Sie in der Liste der Apps eine zu überwachende App aus. Daraufhin wird der App-Bereich mit einer Übersicht des Gerätestatus und des Benutzerstatus angezeigt.

> [!NOTE]
> Android Store-Apps, die als **Verfügbar** bereitgestellt werden, melden keinen Installationsstatus.

## <a name="app-overview-pane"></a>App-Übersichtsbereich

Im App-Bereich können Sie sich Details zum Status einer App in Ihrer Umgebung ansehen.

### <a name="essentials"></a>Essentials
Der Abschnitt **Zusammenfassung** enthält die folgenden Informationen zur App:

 | **App-Details**            | **Beschreibung**                                                      |
|------------------------|------------------------------------------------------------------|
| **Herausgeber**          | Der Herausgeber der App.                                            |
| **Betriebssystem**   | Das Betriebssystem der App (Windows, iOS, Android usw.). |
| **Erstellt**             | Das Datum und die Uhrzeit, als diese Version erstellt wurde                         |
| **Zugewiesen**           | Ob die App zugewiesen wurde (**Ja** oder **Nein**).                  |

### <a name="device-and-user-status-graphs"></a>Diagramme zum Geräte- und Benutzerstatus
Das Diagramm zeigt die Zahl der Apps für die folgenden Status an:

| **Gerätestatus**       | **Beschreibung**                                       |
|-----------------------|-------------------------------------------------------|
| **Installiert**         | Die Anzahl der installierten Apps.                         |
| **Nicht installiert**     | Die Anzahl der nicht installierten Apps.                     |
| **Fehlgeschlagen**            | Die Anzahl nicht erfolgreicher Installationen.                   |
| **Installation steht aus**   | Die Anzahl der Apps, deren Installation bevorsteht. |
| **Nicht verfügbar**           | Die Anzahl der Apps, deren Status nicht verfügbar ist.            |

> [!NOTE]
> Die Anzahl der ermittelten Apps stimmt mit der Statusanzahl von App-Installationen möglicherweise nicht überein. Es gibt folgende Möglichkeiten für Inkonsistenzen:
>    - Eine Zieländerung einer installierten verwalteten App kann dazu führen, dass die Installationsanzahl im Statusblade verringert, in den ermittelten Apps aber weiterhin berichtet wird.
>    - Die Zielgruppenadressierung mehrerer Instanzen derselben App in einem Mandanten führt zu einer unterschiedlichen Anzahl Infolge von potenzieller Überschneidung von Benutzern oder Geräten. Jede Instanz der App zählt sich überschneidende Benutzer, doch bei den ermittelten Apps wird die Anzahl dupliziert.
>    - Ermittelte Apps und App-Status werden zu unterschiedlichen Zeitintervallen gesammelt, und das könnte zu einer Abweichung bei der App-Anzahl führen.
 
### <a name="device-install-status"></a>Geräteinstallationsstatus

Eine Liste des Gerätestatus wird angezeigt, wenn Sie im Abschnitt **Überwachen** des Menüs die Option **Geräteinstallationsstatus** auswählen. Die Tabelle mit den Details enthält die folgenden Spalten:

| **Gerätespalte**      | **Beschreibung**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Gerätename**      | Der Name des Geräts auf Plattformen, die das Benennen von Geräten ermöglichen. Auf anderen Plattformen wird von Intune einen Namen aus anderen Eigenschaften erstellt. Dieses Attribut ist nicht für ein anderes Gerät verfügbar.                                                                       |
| **Benutzername**        | Der Name des Benutzers.                                                                                                                                                                                                                                      |
| **Plattform**         | Das Betriebssystem des Geräts (Windows, iOS, Android usw.).                                                                                                                                                                                           |
| **Version**          | Die Versionsnummer der App. Für branchenspezifische Apps wird die vollständige Versionsnummer der App angezeigt. Die vollständige Versionsnummer identifiziert ein bestimmtes Release der App. Die Nummer wird als _Version_(_Build_) angezeigt. Beispielsweise 2.2(2.2.17560800). |
| **Status**           | Der Status der App.                                                                                                                                                                                                                                     |
| **Statusdetails**   | Die Details des Status.                                                                                                                                                                                                                                     |
| **Letztes Einchecken**    | Das Datum der letzten Synchronisierung des Geräts mit Intune.                                                                                                                                                                                                                  |


### <a name="user-install-status"></a>Benutzerinstallationsstatus

Eine Liste des Benutzerstatus wird angezeigt, wenn Sie im Abschnitt **Überwachen** des Menüs die Option **Benutzerinstallationsstatus** auswählen. Die Tabelle mit den Details enthält die folgenden Spalten:

| **Benutzerspalte**     | **Beschreibung**                           |
|---------------------|-------------------------------------------|
| **Name**            | Der Name des Benutzers in Azure Active Directory.         |
| **Benutzername**       | Der eindeutige Name des Benutzers.              |
| **Installationen**   | Die Anzahl der vom Benutzer installierten Apps. |
| **Fehler**        | Die Anzahl der erfolglosen App-Installationsversuche des Benutzers.     |
| **Nicht installiert**   | Die Anzahl der nicht vom Benutzer installierten Apps. |


## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zum Arbeiten mit Ihren Intune-Daten finden Sie unter [Verwenden des Data Warehouse von Intune](reports-nav-create-intune-reports.md).
- Weitere Informationen zu App-Konfigurationsrichtlinien finden Sie unter [App-Konfigurationsrichtlinien für Intune](app-configuration-policies-overview.md).
