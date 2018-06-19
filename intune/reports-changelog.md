---
title: Änderungsprotokoll für Intune Data Warehouse
titlesuffix: Microsoft Intune
description: Eine Liste der Änderungen in der Intune Data Warehouse-API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: dd9fb36bb1b8c5e66d104f530690c5d236ea25e4
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34223695"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Änderungsprotokoll für die Intune Data Warehouse-API

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Bleiben Sie auf dem neuesten Stand bezüglich Updates für Intune Data Warehouse.

## <a name="1805"></a>1805
_Veröffentlicht: Mai 2018_

### <a name="correction-to-device-count-in-devices-collection"></a>Korrektur der Anzahl der Geräte in der Sammlung **Geräte** 

Die Sammlung **Geräte** wurde korrigiert, wodurch sich möglicherweise die Gesamtzahl der Geräte verringert, die durch das Attribut `isDeleted` gefiltert werden. Diese Verringerung tritt aufgrund der Korrektur auf, es ist kein Fehler. Weitere Informationen zur Sammlung **Geräte** finden Sie unter [Referenz für Geräteentitäten](reports-ref-devices.md). 


## <a name="1801"></a>1801
_Veröffentlichung im Januar 2018_

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>Nur-Anwendung-Authentifizierung von Intune Data Warehouse <!-- 1867540 -->

Sie können eine Anwendung mithilfe von Azure Active Directory (Azure AD) einrichten und bei Intune Data Warehouse authentifizieren. Weitere Informationen finden Sie unter [Nur-Anwendung-Authentifizierung von Intune Data Warehouse](data-warehouse-app-only-auth.md).

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Anforderungen an die Anmeldeinformationen für Azure AD und Intune <!-- 2077525 -->

- Für die Zuweisung zu einem Benutzer beim Zugriff auf Intune Data Warehouse (und die API) ist keine Intune-Lizenz mehr erforderlich.
- Der Intune-Rollenname wurde von **Berichte** in **Intune Data Warehouse** geändert. 

    Weitere Informationen finden Sie unter [Anforderungen an die Anmeldeinformationen für Azure AD und Intune](reports-api-url.md#azure-ad-and-intune-credential-requirements).

### <a name="odata-query-options----2077711---"></a>OData-Abfrageoptionen <!-- 2077711 -->

Sie können <code>$select</code> als OData-Abfrageparameter verwenden. Die aktuelle Version unterstützt die OData-Abfrageparameter <code>$filter</code>, <code>$orderby</code>, <code>$select</code>, <code>$skip</code> und <code>$top</code>. Weitere Informationen hierzu finden Sie unter [OData-Abfrageoptionen](reports-api-url.md#odata-query-options).

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>Neue Entitäten im Data Warehouse-Datenmodell <!-- 2077804 -->

 - Die Entität [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md#mobileappdeviceuserinstallstatus) wurde hinzugefügt. **MobileAppDeviceUserInstallStatus** stellt einen mobilen App-Installationsstatus für ein bestimmtes Gerät und einen bestimmten Benutzer dar.
 - Die Entität [**MobileAppInstallState**](reports-ref-application.md#mobileappinstallstate) wurde hinzugefügt. Die Entität **MobileAppInstallState** stellt den Installationsstatus für eine mobile Anwendung dar, nachdem sie einer Gruppe, die Geräte und/oder Benutzer enthält, zugewiesen haben. 

## <a name="1710"></a>1710
_Veröffentlicht im November 2017_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>Eine neue Entitätssammlung namens „Aktueller Benutzer“ ist auf die Daten der momentan aktiven Benutzer beschränkt.<!-- 1544273 -->

Die Entitätssammlung **Benutzer** listet alle Benutzer von Azure Active Directory (Azure AD) mit zugewiesenen Lizenzen in Ihrem Unternehmen auf. Zu diesen Datensätzen gehören Benutzerzustände während der Datensammlung, selbst wenn der Benutzer entfernt wurde. Beispielsweise kann ein Benutzer in Intune hinzugefügt und dann im Verlauf des letzten Monats entfernt worden sein. Auch wenn dieser Benutzer zum Zeitpunkt der Berichterstellung nicht vorhanden ist, liegen Angaben zu Benutzer und Zustand in den Daten vor. Sie können einen Bericht erstellen, der die Dauer der Präsenz des Benutzers in Ihren Daten zeigt.

Im Gegensatz dazu enthält die neue Entitätssammlung **Aktueller Benutzer** nur Benutzer, die nicht entfernt wurden. Die Entitätssammlung **Aktueller Benutzer** enthält nur die derzeit aktiven Benutzer. Informationen zur Entitätssammlung **Aktueller Benutzer** finden Sie unter [Referenz für die Entität „Aktueller Benutzer“](reports-ref-current-user.md).

## <a name="1709"></a>1709
_Veröffentlicht im Oktober 2017_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Hinzufügen der Entitätssammlung von Benutzergerätezuordnungen zum Intune Data Warehouse-Datenmodell <!-- 1187917 -->

Mithilfe von Informationen über Benutzergerätezuordnungen können Sie Berichte und Datenvisualisierungen erstellen, die Entitätssammlungen von Benutzern und Geräten zuordnet. Auf das Datenmodell kann über die Power BI-Datei (PBIX) zugegriffen werden, die über die Data Warehouse-Seite von Intune, den OData-Endpunkt oder durch die Entwicklung eines benutzerdefinierten Clients abgerufen wird. Weitere Informationen finden Sie unter [Zuordnung der Benutzergeräte](reports-ref-user-device.md).

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>Neue Entitäten im Data Warehouse-Datenmodell<!-- 1479526 --><!-- -->

 - Die Entität [**UserDeviceAssociation**](reports-ref-user-device.md) wurde hinzugefügt. **UserDeviceAssociation** enthält Zuweisungen von Benutzergeräten in Ihrer Organisation. Mithilfe von Informationen über Benutzergerätezuordnungen können Sie Berichte und Datenvisualisierungen erstellen, die Entitätssammlungen von Benutzern und Geräten zuordnet.  
 - Die Entität [ **IntuneManagementExtension**](reports-ref-intunemanagementextension.md) wurde hinzugefügt. **IntuneManagementExtension** enthält Entitäten für mobile Geräte zur Nachverfolgung von Informationen, wie z. B. Version und Installationsstatus.

## <a name="next-steps"></a>Nächste Schritte
 - Erfahren Sie [jede Woche die Neuerungen in Intune](whats-new.md). Sie erhalten auch Informationen zu bevorstehenden Änderungen, wichtige Hinweise zum Dienst und Informationen zu vorherigen Releases.
 - Lesen Sie den [Microsoft Intune-Blog](http://go.microsoft.com/fwlink/?LinkID=273882).
