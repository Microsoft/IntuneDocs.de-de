---
title: "Überwachen von App-Informationen und -Zuweisungen"
titlesuffix: Microsoft Intune
description: "Nachdem Sie Benutzern oder Geräten eine App zugewiesen haben, können Sie mithilfe dieser Informationen den Status der App überwachen."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6bd915093ae45ff0fc3d51a2d7279493bc783d43
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Überwachen von App-Informationen und -Zuweisungen mit Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune bietet eine Reihe von Möglichkeiten, mit denen Sie die Eigenschaften von verwalteten Apps sowie deren Zuweisungsstatus überwachen können.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Wählen Sie **Alle Dienste** > **Intune** aus. Intune befindet sich im Abschnitt **Monitoring + Management**.
3. Wählen Sie **Mobile Apps** und anschließend in der Gruppe **Verwalten** die Option **Apps** aus.
5. Wählen Sie in der Liste auf dem Blatt „Apps“ eine App aus. Ihnen wird dann das Blatt <*App-Name*> **Geräteinstallationsstatus** angezeigt.

## <a name="app-overview-blade"></a>Übersicht über das Blatt „App“

Auf dem Blatt <*App-Name*> **Geräteinstallationsstatus** können Sie Details zum Status einer App in Ihrer Umgebung überprüfen.

### <a name="essentials"></a>Essentials

Der Abschnitt **Zusammenfassung** enthält die folgenden Informationen zur App:

 - **Herausgeber**  
Herausgeber der App
 - **Betriebssystem**  
Das Betriebssystem der App (Windows, iOS, Android usw.)
 - **Erstellen**  
Die Uhrzeit, zu der diese Revision erstellt wurde
 - **Zugewiesen**  
**Nein** oder **Ja**, wenn die App zugewiesen wurde.

### <a name="status"></a>Status
Jedes Diagramm zeigt die Zähler für die folgenden Status:

 - **Installiert**  
Die Anzahl der installierten Apps.
 - **Nicht installiert**  
Die Anzahl der nicht installierten Apps.
 - **Installation steht aus**  
Die Anzahl der Apps, deren Installation bevorsteht.
 - **Fehlgeschlagen**  
Die Anzahl nicht erfolgreicher Installationen.
 - **Unbekannt**  
Die Anzahl der Apps mit unbekanntem Status.

### <a name="device-status"></a>Gerätestatus

Der Gerätestatus. Ein Ringdiagramm, in dem den Installationsstatus der App auf Geräten angezeigt wird. Klicken Sie auf das Diagramm, um eine Liste mit Details zum Gerätestatus zu öffnen. Die Tabelle mit den Details enthält die folgenden Spalten:

 - **Gerätename**  
Der Name des Geräts auf Plattformen, die das Benennen von Geräten ermöglichen. Auf anderen Plattformen wird von Intune einen Namen aus anderen Eigenschaften erstellt. Dieses Attribut kann nicht für alle Geräte zur Verfügung stehen.
 - **Benutzername**  
Der Name des Benutzers.
 - **Plattform**  
Das Betriebssystem des Geräts (Windows, iOS, Android usw.)
 - **Version**  
Die Versionsnummer der App. Für branchenspezifische Apps wird die vollständige Versionsnummer der App angezeigt. Die vollständige Versionsnummer identifiziert ein bestimmtes Release der App. Die Nummer wird als _Version_(_Build_) angezeigt. Beispielsweise 2.2(2.2.17560800)
 - **Status**  
Der Status der App.
 - **Statusdetails**  
Details zum Status.
 - **Letztes Einchecken**  
Datum der letzten Synchronisierung mit Intune des Geräts.


### <a name="user-status"></a>Benutzerstatus

Der Status des Benutzers. Ein Ringdiagramm, in dem den Installationsstatus der App für Benutzer angezeigt wird. Klicken Sie auf das Diagramm, um eine Liste mit Details zum Gerätestatus zu öffnen. Die Tabelle mit den Details enthält die folgenden Spalten:
 - **Name**  
Der Name des Benutzers in Azure AD.
 - **Benutzername**  
Der eindeutige Name des Benutzers.
 - **Installationen**  
Anzahl der installierten Apps, die vom Benutzer verwendet werden.
 - **Fehler**  
Anzahl der nicht erfolgreichen Installationen des Benutzers.
 - **Nicht installiert**  
Anzahl der nicht vom Benutzer installierten Apps.


## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Arbeiten mit Ihren Intune-Daten finden Sie unter [Verwenden des Data Warehouse von Intune](reports-nav-create-intune-reports.md).