---
title: Referenz für Anwendungsentitäten
titleSuffix: Microsoft Intune
description: Referenzthema für die Kategorie „Anwendung“ der Entitätsauflistungen in der Intune Data Warehouse-API
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A92DEF30-5D01-4774-9917-E26F5F0E2E68
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4a8fa34673340e4adca7b64707d8c79d4808460
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74290951"
---
# <a name="reference-for-application-entities"></a>Verweis für Anwendungsentitäten

Die Kategorie **Anwendung** enthält Entitäten für Geräte, die folgende Informationen nachverfolgen:

- Version einer App
- Installationsquelle einer App
- Typ der Entwickler, die eine App entwickelt haben
- Typen verwalteter Software für eine App, z.B. **sidecar** oder **desktop**
- Volume Purchasing Program (VPP) – Status einer App

## <a name="apprevisions"></a>appRevisions

Die **appRevision**-Entität listet alle Versionen von Apps auf.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| appKey |Eindeutiger Bezeichner der App |123 |
| applicationId |Eindeutiger Bezeichner einer App. Ähnlich wie AppKey, dieser Schlüssel ist jedoch ein natürlicher Schlüssel. |b66bc706-ffff-7437-0340-032819502773 |
| revision |Die Version, die vom Administrator beim Upload der Binärdatei erwähnt wurde |2 |
| title |Titel der App |Excel |
| publisher |Herausgeber der App |Microsoft |
| uploadState |Hochladestatus der App |1 |
| appTypeKey |Der Verweis zu AppType wird im folgenden Abschnitt beschrieben. | |
| vppProgramTypeKey |Der Verweis zu VppProgramType wird weiter unten beschrieben. | |
| creationTime |Die Uhrzeit, zu der diese Revision erstellt wurde |23.11.2016 12:00:00 Uhr |
| modifiedTime |Der letzte Zeitpunkt, zu dem eine Änderung an einem mit dieser Revision verknüpften Element vorgenommen wurde |23.11.2016 12:00:00 Uhr |
| Größe |Größe der Binärdatei | |
| startDateInclusiveUTC |Datum und Uhrzeit in UTC, als diese App-Revision im Data Warehouse erstellt wurde |23.11.2016 12:00:00 Uhr |
| endDateExclusiveUTC |Datum und Uhrzeit in UTC, als diese App-Revision als veraltet gekennzeichnet wurde |23.11.2016 12:00:00 Uhr |
| isCurrent |Gibt an, ob diese App-Version im Data Warehouse aktuell ist |Wahr/falsch |
| rowLastModifiedDateTimeUTC |Datum und Uhrzeit in UTC, als diese App-Version zuletzt im Data Warehouse geändert wurde |23.11.2016 12:00:00 Uhr |

## <a name="apptypes"></a>appTypes

Die Entität **appType** führt die Installationsquelle einer App auf.

| Eigenschaft  | Beschreibung |
|---------|------------|
| appTypeID |ID für den Typ |
| appTypeKey |Untergeordneter Schlüssel für den Schlüssel |
| appTypeName |App-Typ |

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


## <a name="vppprogramtypes"></a>vppProgramTypes

Die Entität **vppProgramType** führt mögliche VPP-Programmtypen für eine App auf.

| Eigenschaft  | Beschreibung |
|---------|------------|
| vppProgramTypeID | ID für den Typen |
| vppProgramTypeKey | Ersatzschlüssel für den Schlüssel |
| vppProgramTypeName | VPP-Programmtyp |

### <a name="example"></a>Beispiel

| VppProgramID  | Name | Beschreibung |
|---------|------------|--------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft | VPP-Programm von Microsoft |
| 00000000-0000-0000-0000-000000000000 | Noch nicht verfügbar. | Standardwert, kein VPP |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple | VPP-Programm von Apple |



## <a name="applicationinventories"></a>applicationinventuren

Die Entität **ApplicationInventory** listet die Anwendungen auf, die zum Zeitpunkt der Inventursammlung auf dem Gerät gefunden wurden.

| Eigenschaft  | Beschreibung |
|---------|------------|
| deviceKey | Dies ist ein Verweis auf die Gerätetabelle, die die Intune-Geräte-ID enthält. |
| dateKey | Verweis auf die Datumstabelle, die den Tag der Inventur angibt |
| applicationName | Der Anwendungsname. |
| applicationVersion | Anwendungsversion |
| bundleSize | Größe der App in Byte |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates

Die Entität **mobileAppInstallState** stellt den Installationsstatus für eine mobile Anwendung dar, nachdem sie einer Gruppe, die Geräte und/oder Benutzer enthält, zugewiesen wurde.

| Eigenschaft | Beschreibung |
|---|---|
| appInstallStateKey | Die eindeutige ID des App-Installationsstatus für Ihr Konto |
| appInstallState | Enumerationswert des App-Installationsstatus |
| appInstallStateName | Name des App-Installationsstatus |



