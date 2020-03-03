---
title: Überwachen von App-Informationen und -Zuweisungen
titleSuffix: Microsoft Intune
description: Nachdem Sie Benutzern oder Geräten eine App zugewiesen haben, können Sie mithilfe dieser Informationen den Status der App überwachen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2bd5b26073611d9ff974d4a53f7794919e8672c7
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77513536"
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>Überwachen von App-Informationen und -Zuweisungen mit Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune bietet verschiedene Möglichkeiten, mit denen Sie die Eigenschaften von Apps überwachen, die Sie verwalten, sowie den App-Zuweisungsstatus verwalten können.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** aus.
3. Wählen Sie in der Liste der Apps eine zu überwachende App aus. Daraufhin wird der App-Bereich mit einer Übersicht des Gerätestatus und des Benutzerstatus angezeigt.

> [!NOTE]
> Android Store-Apps, die als **Verfügbar** bereitgestellt werden, melden keinen Installationsstatus.
>
> Für auf Android Enterprise-Arbeitsprofilgeräten bereitgestellte verwaltete Google Play-Apps können Sie den Status und die Versionsnummer der auf einem Gerät installierten App abrufen, das Intune verwendet. 

## <a name="app-overview-pane"></a>App-Übersichtsbereich

Im App-Bereich können Sie sich Details zum Status einer App in Ihrer Umgebung ansehen.

### <a name="essentials"></a>Essentials
Der Abschnitt **Zusammenfassung** enthält die folgenden Informationen zur App:

 | **App-Details**            | **Beschreibung**                                                      |
|------------------------|------------------------------------------------------------------|
| **Herausgeber**          | Der Herausgeber der App.                                            |
| **Betriebssystem**   | Das Betriebssystem der App (Windows, iOS/iPadOS, Android usw.). |
| **Erstellt**             | Das Datum und die Uhrzeit, als diese Version erstellt wurde <b>**Hinweis:** Dieser Date-Wert wird aktualisiert, wenn ein IT-Administrator App-Metadaten ändert (wie z. B. die App-Kategorie oder die App-Beschreibung).                        |
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
> Beachten Sie, dass branchenspezifische Android-Apps (.APK), die als **Verfügbar mit oder ohne Registrierung** bereitgestellt werden, nur für registrierte Geräte den Installationsstatus der App melden. Der App-Installationsstatus ist nicht für Geräte verfügbar, die nicht für Intune registriert sind.

### <a name="device-install-status"></a>Geräteinstallationsstatus

Eine Liste des Gerätestatus wird angezeigt, wenn Sie im Abschnitt **Überwachen** des Menüs die Option **Geräteinstallationsstatus** auswählen. Die Tabelle mit den Details enthält die folgenden Spalten:

| **Gerätespalte**      | **Beschreibung**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Gerätename**      | Der Name des Geräts auf Plattformen, die das Benennen von Geräten ermöglichen. Auf anderen Plattformen wird von Intune einen Namen aus anderen Eigenschaften erstellt. Dieses Attribut ist nicht für ein anderes Gerät verfügbar.                                                                       |
| **Benutzername**        | Der Name des Benutzers.                                                                                                                                                                                                                                      |
| **Plattform**         | Das Betriebssystem des Geräts (Windows, iOS/iPadOS, Android usw.).                                                                                                                                                                                           |
| **Version**          | Die Versionsnummer der App. Für branchenspezifische Apps (LOB) und Microsoft Store für Geschäftsanwendungen wird die vollständige Versionsnummer der App angezeigt. Die vollständige Versionsnummer identifiziert ein bestimmtes Release der App. Die Nummer wird als _Version_(_Build_) angezeigt. Beispielsweise 2.2(2.2.17560800). Für standardmäßige Store-Apps werden keine Versionen angezeigt. |
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

- Weitere Informationen zum Arbeiten mit Ihren Intune-Daten finden Sie unter [Verwenden des Data Warehouse von Intune](../reports-nav-create-intune-reports.md).
- Weitere Informationen zu App-Konfigurationsrichtlinien finden Sie unter [App-Konfigurationsrichtlinien für Intune](app-configuration-policies-overview.md).
