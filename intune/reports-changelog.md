---
title: Änderungsprotokoll für Intune Data Warehouse
titleSuffix: Microsoft Intune
description: Dieses Thema enthält eine Liste der Änderungen für die Microsoft Intune-Data Warehouse-API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/11/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30f315f58a905e690a43ab3c44aee783bd0ef8c9
ms.sourcegitcommit: a2cd14c30949cef17bfc6576513e7660a8015669
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59571806"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Änderungsprotokoll für die Intune Data Warehouse-API

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Bleiben Sie auf dem neuesten Stand bezüglich Updates für Intune Data Warehouse.

## <a name="1903-part-2"></a>1903 (Teil 2)
_Veröffentlicht: April 2019_

### <a name="beta-changes"></a>Beta-Änderungen

Die folgende Tabelle enthält die in jüngster Zeit entfernten Sammlungen und deren Nachfolger im Intune Data Warehouse.

|    Sammlung                          |    Änderung     |    Zusätzliche Informationen                                                                                                                                                                                                                                                                                                                                                                 |
|----------------------------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    mobileAppDeviceUserInstallStatus    |    Entfernt    |    Verwenden Sie stattdessen [mobileAppInstallStatusCounts](intune-data-warehouse-collections.md#mobileappinstallstatuscounts).                                                                                                                                                                                                                                                                     |
|    enrollmentTypes                     |    Entfernt    |    Verwenden Sie stattdessen [deviceEnrollmentTypes](intune-data-warehouse-collections.md#deviceenrollmenttypes).                                                                                                                                                                                                                                                                                      |
|    mdmStatuses                         |    Entfernt    |    Verwenden Sie stattdessen [ComplianceStates](intune-data-warehouse-collections.md#compliancestates).                                                                                                                                                                                                                                                                                               |
|    workPlaceJoinStateTypes             |    Entfernt    |    Verwenden Sie stattdessen in den Sammlungen [devices](intune-data-warehouse-collections.md#devices) und [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) die `azureAdRegistered`-Eigenschaft.                                                                                                                                                                                                             |
|    clientRegistrationStateTypes        |    Entfernt    |    Verwenden Sie stattdessen [deviceRegistrationStates](intune-data-warehouse-collections.md#deviceregistrationstates).                                                                                                                                                                                                                                                                             |
|    currentUser                         |    Entfernt    |    Verwenden Sie stattdessen die Sammlung [users](intune-data-warehouse-collections.md#users).                                                                                                                                                                                                                                                                                                      |
|    mdmDeviceInventoryHistories         |    Entfernt    |    Viele der Eigenschaften waren unnötig oder befinden sich nun in den Sammlungen [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories) oder [devices](intune-data-warehouse-collections.md#devices). **mdmDeviceInventoryHistories**-Eigenschaften, die nicht bereits in diesen beiden Sammlungen aufgeführt sind, stehen nicht mehr zur Verfügung. Siehe die folgenden Details.    |

In der folgenden Tabelle sind die alten Eigenschaften aufgelistet, die sich früher in der Sammlung **mdmDeviceInventoryHistories** befanden, sowie die Änderung bzw. Nachfolger. Eigenschaften, die sich in **mdmDeviceInventoryHistories** befanden, aber unten nicht aufgeführt sind, wurden entfernt.

|    Alte Eigenschaft                |    Änderung/Nachfolger                                                           |
|--------------------------------|---------------------------------------------------------------------------------|
|    cellularTechnology          |    cellularTechnology in der „devices“-Sammlung                                     |
|    deviceClientId              |    deviceId in der „devices“-Sammlung                                               |
|    deviceManufacturer          |    „manufacturer“ in der „devices“-Sammlung                                           |
|    deviceModel                 |    „model“ in der „devices“-Sammlung                                                  |
|    deviceName                  |    deviceName in der „devices“-Sammlung                                             |
|    deviceOsPlatform            |    deviceTypeKey in der „devices“-Sammlung                                          |
|    deviceOsVersion             |    „osversion“ in der devicePropertyHistories-Sammlung                              |
|    deviceType                  |    deviceTypeKey in der „devices“-Sammlung mit Verweis auf die deviceTypes-Sammlung    |
|    encryptionState             |    encryptionState-Eigenschaft in der „devices“-Sammlung                           |
|    exchangeActiveSyncId        |    encryptionState-Eigenschaft in der „devices“-Sammlung                               |
|    exchangeDeviceId            |    easDeviceId in der „devices“-Sammlung                                            |
|    imei                        |    „imei“ in der „devices“-Sammlung                                                   |
|    isSupervised                |    isSupervised-Eigenschaft in der „devices“-Sammlung                              |
|    jailBroken                  |    jailBroken in der devicePropertyHistories-Sammlung                             |
|    meid                        |    „meid“-Eigenschaft in der „devices“-Sammlung                                      |
|    oem                         |    „manufacturer“ in der „devices“-Sammlung                                           |
|    osName                      |    deviceTypeKey in der „devices“-Sammlung mit Verweis auf die deviceTypes-Sammlung    |
|    phoneNumber                 |    phoneNumber in der „devices“-Sammlung                                            |
|    platformType                |    „model“ in der „devices“-Sammlung                                                  |
|    product                     |    deviceTypeKey in der „devices“-Sammlung                                          |
|    productVersion              |    „osversion“ in der devicePropertyHistories-Sammlung                              |
|    serialNumber                |    serialNumber in der „devices“-Sammlung                                           |
|    storageFree                 |    freeStorageSpaceInBytes-Eigenschaft in der „devices“-Sammlung                   |
|    storageTotal                |    totalStorageSpaceInBytes-Eigenschaft in der „devices“-Sammlung                |
|    subscriberCarrierNetwork    |    subscriberCarrier-Eigenschaft in der „devices“-Sammlung                         |
|    wifimac                     |    wiFiMacAddress in der „devices“-Sammlung                                         |

Die folgende Tabelle enthält Änderungen an Eigenschaften in der [DevicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories)-Sammlung: 

|    Alte Eigenschaft                  |    Änderung/Nachfolger                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey mit Verweis auf deviceCategories-Sammlung       |
|    certExpirationDate            |    Entfernt                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    enrolledDateTime in der „devices“-Sammlung                           |
|    deviceTypeKey                 |    deviceTypeKey in der „devices“-Sammlung                              |
|    easID                         |    easDeviceId in der „devices“-Sammlung                                |
|    enrolledByUser                |    userId in der „devices“-Sammlung                                     |
|    enrollmentTypeKey             |    deviceEnrollmentTypeKey in der „devices“-Sammlung                    |
|    graphDeviceIsCompliant        |    Entfernt                                                          |
|    graphDeviceIsManaged          |    Entfernt                                                          |
|    lastContact                   |    lastSyncDateTime in der „devices“-Sammlung                           |
|    lastContactNotification       |    Entfernt                                                          |
|    lastContactWorkplaceJoin      |    Entfernt                                                          |
|    lastExchangeStatusUtc         |    Entfernt                                                          |
|    lastModifiedDateTimeUTC       |    Entfernt                                                          |
|    lastPolicyUpdateUtc           |    Entfernt                                                          |
|    managementAgentKey            |    managementStateKey                                               |
|    Hersteller                  |    „manufacturer“ in der „devices“-Sammlung                               |
|    mdmStatusKey                  |    complianceStateKey mit Verweis auf die complianceStates-Sammlung    |
|    model                         |    „model“ in der „devices“-Sammlung                                      |
|    osFamily                      |    operatingSystem in der „devices“-Sammlung                            |
|    osRevisionNumber              |    osVersion in der „devices“-Sammlung                                  |
|    processorArchitecture         |    Entfernt                                                          |
|    referenceId                   |    azureAdDeviceId in der „devices“-Sammlung                            |
|    serialNumber                  |    serialNumber in der „devices“-Sammlung                               |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

Die folgende Tabelle enthält Änderungen an Eigenschaften in der [devices](intune-data-warehouse-collections.md#devices)-Sammlung: 

|    Alte Eigenschaft                  |    Änderung/Nachfolger                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey mit Verweis auf deviceCategories-Sammlung       |
|    certExpirationDate            |    Entfernt                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    enrolledDateTime                                                 |
|    easId                         |    easDeviceId                                                      |
|    enrolledByUser                |    userId                                                           |
|    enrollmentTypeKey             |    deviceEnrollmentTypeKey                                          |
|    graphDeviceIsCompliant        |    Entfernt                                                          |
|    graphDeviceIsManaged          |    Entfernt                                                          |
|    lastContact                   |    lastSyncDateTime                                                 |
|    lastContactNotification       |    Entfernt                                                          |
|    lastContactWorkplaceJoin      |    Entfernt                                                          |
|    lastExchangeStatusUtc         |    Entfernt                                                          |
|    lastPolicyUpdateUtc           |    Entfernt                                                          |
|    mdmStatusKey                  |    complianceStateKey mit Verweis auf die complianceStates-Sammlung    |
|    osFamily                      |    operatingSystem                                                  |
|    processorArchitecture         |    Entfernt                                                          |
|    referenceId                   |    azureAdDeviceId                                                  |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

Die folgende Tabelle enthält Änderungen an Eigenschaften in der [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities)-Sammlung: 

|    Alte Eigenschaft         |    Änderung/Nachfolger         |
|-------------------------|-------------------------------|
|    enrollmentTypeKey    |    deviceEnrollmentTypeKey    |

Die folgende Tabelle enthält Änderungen an Eigenschaften in der [mamApplications](intune-data-warehouse-collections.md#mamapplications)-Sammlung: 

|    Alte Eigenschaft       |    Änderung/Nachfolger    |
|-----------------------|--------------------------|
|    applicationKey     |    mamApplicationKey     |
|    applicationName    |    mamApplicationName    |
|    applicationId      |    mamApplicationId      |

Die folgende Tabelle enthält Änderungen an Eigenschaften in der [mamApplicationInstances](intune-data-warehouse-collections.md#mamapplicationinstances)-Sammlung: 

|    Alte Eigenschaft     |    Änderung/Nachfolger    |
|---------------------|--------------------------|
|    applicationId    |    mamApplicationId      |
|    deviceId         |    mamDeviceId           |
|    deviceType       |    mamDeviceType         |
|    deviceName       |    mamDeviceName         |

Die folgende Tabelle enthält Änderungen an Eigenschaften in der [mamCheckins](intune-data-warehouse-collections.md#mamcheckins)-Sammlung: 

|    Alte Eigenschaft      |    Änderung/Nachfolger    |
|----------------------|--------------------------|
|    applicationKey    |    mamApplicationKey     |

Die folgende Tabelle enthält Änderungen an Eigenschaften in der [users](intune-data-warehouse-collections.md#users)-Sammlung: 

|    Alte Eigenschaft             |    Änderung/Nachfolger    |
|-----------------------------|--------------------------|
|    startDateInclusiveUtc    |    Entfernt               |
|    endDateInclusiveUtc      |    Entfernt               |
|    isCurrent                |    Entfernt               |

## <a name="1903"></a>1903
_Veröffentlicht: März 2019_

### <a name="v10-changes-reflecting-back-to-beta"></a>Übernahme der Änderungen an V1.0 in die Betaversion
Als V1.0 in Version 1808 erstmals eingeführt wurde, gab es wichtige Unterschiede zur Beta-API. Diese Änderungen werden mit Version 1903 in der Betaversion der API berücksichtigt. Wenn Sie über wichtige Berichte verfügen, die die Betaversion der API nutzen, wird dringend empfohlen, dass Sie diese Berichte in V1.0 konvertieren, um Breaking Changes zu vermeiden. Weitere Informationen zu Data Warehouse-API-Versionen und Abwärtskompatibilität finden Sie unter [Informationen zur API-Version](reports-api-url.md). 

## <a name="1902"></a>1902 
_Veröffentlicht: Februar 2019_

### <a name="power-bi-compliance-app"></a>Power BI-Compliance-App 

Sie können über die App [Intune Compliance (Data Warehouse)](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance) in Power BI auf Ihre Intune Data Warehouse-Instanz zugreifen. Mit dieser Power BI-App können Sie nun auf vorab erstellte Berichte zugreifen und diese freigeben, ohne dafür ein Setup durchzuführen und ohne Ihren Webbrowser zu verlassen. 

> [!NOTE]
> Es gibt zwei zusätzliche Filter, die Sie auf die Intune-Kompatibilitäts-App anwenden können.

#### <a name="add-additional-filters-to-the-intune-compliance-app"></a>Hinzufügen zusätzlicher Filter zur Intune-Kompatibilitäts-App
1. Öffnen Sie die App [Intune-Kompatibilität (Data Warehouse)](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance) in Ihrem Webbrowser.
2. Klicken Sie auf **Nicht kompatible Geräte**, und wählen Sie **Nicht kompatibel** im Filter **ComplianceStatus** aus. 
3. Klicken Sie auf **Unbekannte Geräte**, und wählen Sie **Noch nicht verfügbar** im Filter **ComplianceStatus** aus. 

## <a name="1812"></a>1812 
_Im Dezember 2018 veröffentlicht_

### <a name="enrollment-activities-collection-released-to-v10"></a>Registrierungsaktivitätensammlung in Version v1.0 veröffentlicht 

Die Registrierungsaktivitätensammlung ist nun in der Version v1.0 verfügbar. Mithilfe dieser Sammlung können Sie die Volumen und Trends von Registrierungsfehlern in Ihrer Umgebung besser nachvollziehen. Weitere Informationen finden Sie unter [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities), [enrollmentEventStatuses](intune-data-warehouse-collections.md#enrollmenteventstatuses), [enrollmentFailureCategories](intune-data-warehouse-collections.md#enrollmentfailurecategories) und [enrollmentFailureReasons](intune-data-warehouse-collections.md#enrollmentfailurereasons).

## <a name="1808"></a>1808
_Veröffentlicht: August 2018_

### <a name="v10-collections"></a>v1.0-Sammlungen  

Jetzt können Sie die Version v1.0 von Intune Data Warehouse durch Festlegen des Abfrageparameters `api-version=v1.0`verwenden. Updates von Sammlungen in Data Warehouse bauen aufeinander auf und beschädigen keine vorhandenen Szenarios.

### <a name="enrollment-activities-collection-released-to-beta"></a>Registrierungsaktivitätensammlung in Betaversion veröffentlicht

Die neue `Enrollment Activities`-Sammlung ist für die Betaversion freigegeben. Diese Sammlung kann Ihnen helfen, den Verlauf Ihrer Registrierung zu verstehen, da hier die häufigsten Fehler aufgeführt werden. 


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

 - Die Entität [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md) wurde hinzugefügt. **MobileAppDeviceUserInstallStatus** stellt einen mobilen App-Installationsstatus für ein bestimmtes Gerät und einen bestimmten Benutzer dar.
 - Die Entität [**MobileAppInstallState**](reports-ref-application.md#mobileappinstallstate) wurde hinzugefügt. Die Entität **MobileAppInstallState** stellt den Installationsstatus für eine mobile Anwendung dar, nachdem sie einer Gruppe, die Geräte und/oder Benutzer enthält, zugewiesen haben. 

## <a name="1710"></a>1710
_Veröffentlicht im November 2017_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>Eine neue Entitätssammlung namens „Aktueller Benutzer“ ist auf die Daten der derzeit aktiven Benutzer beschränkt <!-- 1544273 -->

Die Entitätssammlung **Benutzer** listet alle Benutzer von Azure Active Directory (Azure AD) mit zugewiesenen Lizenzen in Ihrem Unternehmen auf. Zu diesen Datensätzen gehören Benutzerzustände während der Datensammlung, selbst wenn der Benutzer entfernt wurde. Beispielsweise kann ein Benutzer in Intune hinzugefügt und dann im Verlauf des letzten Monats entfernt worden sein. Auch wenn dieser Benutzer zum Zeitpunkt der Berichterstellung nicht vorhanden ist, liegen Angaben zu Benutzer und Zustand in den Daten vor. Sie können einen Bericht erstellen, der die Dauer der Präsenz des Benutzers in Ihren Daten zeigt.

Im Gegensatz dazu enthält die neue Entitätssammlung **Aktueller Benutzer** nur Benutzer, die nicht entfernt wurden. Die Entitätssammlung **Aktueller Benutzer** enthält nur die derzeit aktiven Benutzer. Informationen zur Entitätssammlung **Aktueller Benutzer** finden Sie unter [Referenz für die Entität „Aktueller Benutzer“](reports-ref-current-user.md).

## <a name="1709"></a>1709
_Veröffentlicht im Oktober 2017_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Eine Entitätssammlung von Benutzergerätezuordnungen wurde dem Intune Data Warehouse-Datenmodell hinzugefügt <!-- 1187917 -->

Mithilfe von Informationen über Benutzergerätezuordnungen können Sie Berichte und Datenvisualisierungen erstellen, die Entitätssammlungen von Benutzern und Geräten zuordnet. Auf das Datenmodell kann über die Power BI-Datei (PBIX) zugegriffen werden, die über die Data Warehouse-Seite von Intune, den OData-Endpunkt oder durch die Entwicklung eines benutzerdefinierten Clients abgerufen wird. Weitere Informationen finden Sie unter [Zuordnung der Benutzergeräte](reports-ref-user-device.md).

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>Neue Entitäten im Data Warehouse-Datenmodell <!-- 1479526 --><!-- -->

 - Die Entität [**UserDeviceAssociation**](reports-ref-user-device.md) wurde hinzugefügt. **UserDeviceAssociation** enthält Zuweisungen von Benutzergeräten in Ihrer Organisation. Mithilfe von Informationen über Benutzergerätezuordnungen können Sie Berichte und Datenvisualisierungen erstellen, die Entitätssammlungen von Benutzern und Geräten zuordnet.  
 - Die Entität [ **IntuneManagementExtension**](reports-ref-intunemanagementextension.md) wurde hinzugefügt. **IntuneManagementExtension** enthält Entitäten für mobile Geräte zur Nachverfolgung von Informationen, wie z. B. Version und Installationsstatus.

## <a name="next-steps"></a>Nächste Schritte
 - Erfahren Sie [jede Woche die Neuerungen in Intune](whats-new.md). Sie erhalten auch Informationen zu bevorstehenden Änderungen, wichtige Hinweise zum Dienst und Informationen zu vorherigen Releases.
 - Lesen Sie den [Microsoft Intune-Blog](https://go.microsoft.com/fwlink/?LinkID=273882).
