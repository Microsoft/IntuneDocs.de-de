---
title: Anwendung
titlesuffix: Microsoft Intune
description: Referenzthema für die Kategorie „Anwendung“ der Entitätsauflistungen in der Intune Data Warehouse-API
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e27b07b18991ebd930bac6ed70fa489d27aa22ba
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34224867"
---
# <a name="reference-for-application-entities"></a>Verweis für Anwendungsentitäten

Die Kategorie **Anwendung** (Application) enthält Entitäten für mobile Geräte, die folgende Informationen nachverfolgen:

  -  Version einer App
  -  Installationsquelle einer App
  -  Typ der Entwickler, die eine App entwickelt haben
  -  Typen verwalteter Software für eine App, z.B. **sidecar** oder **desktop**
  -  Volume Purchasing Program (VPP) – Status einer App

## <a name="apprevision"></a>AppRevision

Die Entität **AppRevision** führt alle Versionen einer App auf.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| AppKey |Eindeutiger Bezeichner der App |123 |
| ApplicationId |Eindeutiger Bezeichner einer App. Ähnlich wie AppKey, dieser Schlüssel ist jedoch ein natürlicher Schlüssel. |b66bc706-ffff-7437-0340-032819502773 |
| Revision |Die Version, die vom Administrator beim Upload der Binärdatei erwähnt wurde |2 |
| Titel |Titel der App |Excel |
| Herausgeber |Herausgeber der App |Microsoft |
| UploadState |Hochladestatus der App |1 |
| AppTypeKey |Der Verweis zu AppType wird im folgenden Abschnitt beschrieben. | |
| VppProgramTypeKey |Der Verweis zu VppProgramType wird weiter unten beschrieben. | |
| CreationTime |Die Uhrzeit, zu der diese Revision erstellt wurde |23.11.2016 12:00:00 Uhr |
| ModifiedTime |Der letzte Zeitpunkt, zu dem eine Änderung an einem mit dieser Revision verknüpften Element vorgenommen wurde |23.11.2016 12:00:00 Uhr |
| Size |Größe der Binärdatei | |
| StartDateInclusiveUTC |Datum und Uhrzeit in UTC, als diese App-Revision im Data Warehouse erstellt wurde |23.11.2016 12:00:00 Uhr |
| EndDateExclusiveUTC |Datum und Uhrzeit in UTC, als diese App-Revision als veraltet gekennzeichnet wurde |23.11.2016 12:00:00 Uhr |
| IsCurrent |Gibt an, ob diese App-Version im Data Warehouse aktuell ist |Wahr/falsch |
| RowLastModifiedDateTimeUTC |Datum und Uhrzeit in UTC, als diese App-Version zuletzt im Data Warehouse geändert wurde |23.11.2016 12:00:00 Uhr |

## <a name="apptypes"></a>AppTypes

Die Entität **AppTypes** führt die Installationsquelle einer App auf.

| Eigenschaft  | Beschreibung |
|---------|------------|
| AppTypeID |ID für den Typ |
| AppTypeKey |Untergeordneter Schlüssel für den Schlüssel |
| AppTypeName |App-Typ |

### <a name="example"></a>Beispiel

| AppTypeID  | Name | Beschreibung |
|---------|------------|--------|
| 0 |Android Store-App | Eine Android Store-App |
| 1 |Android-Branchen-App | Eine branchenspezifische Android-App |
| 2 |Verwaltete Android Store-App (MAM) | Eine Android Store-App, für die die Verwaltung aktiviert ist |
| 3 |iOS Store-App | Eine iOS Store-App |
| 4 |Branchenspezifische iOS-App | Eine branchenspezifische iOS-App |
| 5 |Verwaltete iOS Store-App (MAM?) | Eine iOS Store-App, die für die Verwaltung aktiviert ist |
| 6 |O365 Pro Plus Suite | Die Office 365 Pro Plus Suite für Windows 10 |
| 7 |Web-App | Eine Web-App |
| 8 |Windows Phone 8.1 Store-App | Eine Windows Phone 8.1 Store-App |
| 9 |Windows Store-App | Eine Windows Store-App |
| 10 |Branchenspezifische Windows-Apps | Eine branchenspezifische Windows-APPX-App |
| 11 |Windows Mobile MSI | Eine branchenspezifische MSI-App |
| 12 |Branchenspezifische Windows Phone-App | Eine branchenspezifische Windows Phone-App |


## <a name="vppprogramtypes"></a>VppProgramTypes

Die Entität **VppProgramTypes** führt mögliche VPP-Programmtypen für eine App auf.

| Eigenschaft  | Beschreibung |
|---------|------------|
| VppProgramTypeID | ID für den Typen |
| VppProgramTypeKey | Ersatzschlüssel für den Schlüssel |
| VppProgramTypeName | VPP-Programmtyp |

### <a name="example"></a>Beispiel

| VppProgramID  | Name | Beschreibung |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | VPP-Programm von Microsoft |
| 00000000-0000-0000-0000-000000000000 | Noch nicht verfügbar. | Standardwert, kein VPP |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | VPP-Programm von Apple |



## <a name="applicationinventory"></a>ApplicationInventory

Die Entität **ApplicationInventory** listet die Anwendungen auf, die zum Zeitpunkt der Inventursammlung auf dem Gerät gefunden wurden.

| Eigenschaft  | Beschreibung |
|---------|------------|
| DeviceKey | Dies ist ein Verweis auf die Gerätetabelle, die die Intune-Geräte-ID enthält. |
| DateKey | Verweis auf die Datumstabelle, die den Tag der Inventur angibt |
| ApplicationName | Der Anwendungsname. |
| ApplicationVersion | Anwendungsversion |
| BundleSize | Größe der App in Byte |

## <a name="mobileappinstallstate"></a>MobileAppInstallState

Die Entität **MobileAppInstallState** stellt den Installationsstatus für eine mobile Anwendung dar, nachdem sie einer Gruppe, die Geräte und/oder Benutzer enthält, zugewiesen haben.

| Eigenschaft | Beschreibung |
|---|---|
| AppInstallStateKey | Die eindeutige ID des App-Installationsstatus für Ihr Konto |
| AppInstallState | Enumerationswert des App-Installationsstatus |
| AppInstallStateName | Name des App-Installationsstatus |

## <a name="mobileappdeviceuserinstallstatus"></a>MobileAppDeviceUserInstallStatus

**MobileAppDeviceUserInstallStatus** stellt einen mobilen App-Installationsstatus für ein bestimmtes Gerät und einen bestimmten Benutzer dar.


|      Eigenschaft      |                                                         Beschreibung                                                         |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------|
|      DateKey       |                                  Schlüssel des Datums, an dem der App-Installationsstatus erfasst wurde                                  |
|       AppKey       |                             Schlüssel der mobilen App, mit der eine Instanz von AppRevision identifiziert wird                              |
|     DeviceKey      |                              Schlüssel eines Zielgeräts, das zur Identifizierung einer Instanz von Device verwendet wird                               |
|      UserKey       |                                Schlüssel eines Zielbenutzers, der zur Identifizierung einer Instanz von User verwendet wird                                 |
| AppInstallStateKey |                     Schlüssel des App-Installationsstatus, der zur Identifizierung einer Instanz von MobileAppInstallState verwendet wird                     |
|     ErrorCode      | Der vom App-Installer zurückgegebene Fehlercode, die mobile Plattform oder der Dienst zur Installation der App. |

