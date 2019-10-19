---
title: Referenz für Richtlinienentitäten
titleSuffix: Microsoft Intune
description: Referenzthema für die Kategorie „Richtlinien“ der Entitätsauflistungen in der Intune Data Warehouse-API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 64fc1bab596715be80fd3a91c003cac1176fe787
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490275"
---
# <a name="reference-for-policy-entities"></a>Referenz für Richtlinienentitäten

Die Kategorie **policies** enthält Entitäten für mobile Geräte, die folgende Informationen nachverfolgen:

- Inventar der Gerätekonfigurationsprofile, Appkonfigurationsprofile und Kompatibilitätsrichtlinien  
- Anzahl der Geräte mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag  
- Anzahl der Benutzer mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag  
- Gesamtzahl der Geräte mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“  

## <a name="policies"></a>Richtlinien

Die Entität **policy** listet Gerätekonfigurationsprofile, Appkonfigurationsprofile und Kompatibilitätsrichtlinien auf. Sie können die Richtlinien mit der mobilen Geräteverwaltung (MDM) zu einer Gruppe in Ihrem Unternehmen zuweisen.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| policyKey |Eindeutiger Schlüssel, der die Richtlinie im Data Warehouse darstellen soll |123 |
| policyId |Eindeutiger Bezeichner der Richtlinie im Data Warehouse |b66bc706-ffff-7437-0340-032819502773 |
| policyName |Name der Richtlinie |"Windows 10-Baseline" |
| policyVersion |Version der Richtlinie Wenn die Richtlinie bearbeitet oder geändert wird, wird eine neuere Version erstellt. |1, 2, 3 |
| isDeleted |Gibt an, ob der Richtliniendatensatz aktualisiert wurde.  <br>Wahr: Richtlinie verfügt über einen neuen Datensatz mit aktualisierten Feldern. <br>Falsch: der neueste Datensatz für diese Richtlinie. |Wahr/falsch |
| startDateInclusiveUTC |Datum und Uhrzeit in UTC, als diese Richtlinie im Data Warehouse erstellt wurde |23.11.2016 12:00:00 Uhr |
| deletedDateUTC |Datum und Uhrzeit in UTC, als IsDeleted in TRUE geändert wurde |23.11.2016 12:00:00 Uhr |
| rowLastModifiedDateTimeUTC |Datum und Uhrzeit in UTC, als diese Richtlinie zuletzt im Data Warehouse geändert wurde |23.11.2016 12:00:00 Uhr |

## <a name="policytypes"></a>policyTypes

Die Entität **policyType** listet Gerätekonfigurationsprofile, Appkonfigurationsprofile und Kompatibilitätsrichtlinien auf. Sie können die Richtlinien mit der mobilen Geräteverwaltung (MDM) zu einer Gruppe in Ihrem Unternehmen zuweisen.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| policyTypeId |Eindeutiger Bezeichner der Richtlinie im Quellsystem |123 |
| policyTypeKey |Eindeutiger Bezeichner der Richtlinie im Data Warehouse |1 |
| policyTypeName |Name des Richtlinientyps |Windows 10-Kompatibilitätsrichtlinie |

## <a name="device-configuration"></a>Gerätekonfiguration

Die Entität **deviceConfigurationProfileDeviceActivity** listet die Anzahl der **Geräte** mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag auf. Die Anzahl gibt die Gerätekonfigurationsprofile an, die der Entität zugewiesen sind. Wenn ein **Gerät** beispielsweise den Zustand „erfolgreich“ für alle zugewiesenen Richtlinien aufweist, wird der Zähler für „erfolgreich“ für diesen Tag um eins erhöht. Wenn einem Gerät zwei Profile zugewiesen sind, von denen eines den Zustand „erfolgreich“ und eines den Zustand „Fehler“ aufweist, erhöht die Entität den Zähler für „erfolgreich“ und versetzt das Gerät in den Zustand „Fehler“. Die Entität listet für die letzten 30 Tage auf, wie viele Geräte an einem bestimmten Tag in welchem Zustand waren.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| dateKey |Date Key für den Zeitpunkt als das Einchecken der Gerätekonfigurationsprofile im Data Warehouse aufgezeichnet wurde |20160703 |
| pending |Anzahl eindeutiger Geräte im Zustand „ausstehend“ |123 |
| Erfolgreich |Anzahl eindeutiger Geräte im Zustand „erfolgreich“ |12 |
| Fehler |Anzahl eindeutiger Geräte im Zustand „Fehler“ |10 |
| Gescheitert |Anzahl eindeutiger Geräte im Zustand „fehlerhaft“ |2 |

Die Entität **deviceConfigurationProfileUserActivity** listet die Anzahl der **Benutzer** mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag auf. Die Anzahl gibt die Gerätekonfigurationsprofile an, die der Entität zugewiesen sind. Wenn ein **Benutzer** beispielsweise den Zustand „erfolgreich“ für alle zugewiesenen Richtlinien aufweist, wird der Zähler für „erfolgreich“ für diesen Tag um eins erhöht. Wenn einem Benutzer zwei Profile zugewiesen sind, von denen eines den Zustand „erfolgreich“ und eines den Zustand „Fehler“ aufweist, wird der Benutzer für den Zustand „Fehler“ gezählt.  Die Entität **deviceConfigurationProfileUserActivity** listet für die letzten 30 Tage auf, wie viele Benutzer an einem bestimmten Tag in welchem Zustand waren.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| dateKey |Date Key für den Zeitpunkt als das Einchecken der Gerätekonfigurationsprofile im Data Warehouse aufgezeichnet wurde |20160703 |
| pending |Anzahl eindeutiger Benutzer im Zustand „ausstehend“ |123 |
| Erfolgreich |Anzahl eindeutiger Benutzer im Zustand „erfolgreich“ |12 |
| Fehler |Anzahl eindeutiger Benutzer im Zustand „Fehler“ |10 |
| Gescheitert |Anzahl eindeutiger Benutzer im Zustand „fehlerhaft“ |2 |

## <a name="policytypeactivities"></a>policyTypeActivities

Die Entität **policyTypeActivity** listet die Gesamtzahl der Geräte im Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ auf. Diese Zustände werden im Bezug auf ein Gerätekonfigurationsprofil, ein Appkonfigurationsprofil oder eine Kompatibiliätsrichtlinie pro Tag aufgelistet.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| dateKey |„dateKey“ für den Zeitpunkt, zu dem das Einchecken des Gerätekonfigurationsprofils im Data Warehouse aufgezeichnet wurde. |20160703 |
| policyKey |„policyKey“ kann mit „policy“ verknüpft werden, um den „policyName“ zu erhalten. |Windows 10-Baseline |
| policyTypeKey |Der Typ des Richtlinienschlüssels kann mit dem Richtlinientyp verknüpft werden, um den Namen des Richtlinientyps zu erhalten. |Windows 10-Kompatibilitätsrichtlinien |
| pending |Anzahl eindeutiger Geräte im Zustand „ausstehend“ |123 |
| Erfolgreich |Anzahl eindeutiger Geräte im Zustand „erfolgreich“ |12 |
| Fehler |Anzahl eindeutiger Geräte im Zustand „Fehler“ |10 |
| Gescheitert |Anzahl eindeutiger Geräte im Zustand „fehlerhaft“ |2 |

## <a name="compliance-policy"></a>Kompatibilitätsrichtlinie

Die API-Referenz der Konformitätsrichtlinie enthält Entitäten, die Statusinformationen über Konformitätsrichtlinien bereitstellen, die Geräten zugewiesen sind.

### <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities

In der folgenden Tabelle sind die Zuweisungsstatus der Konformitätsrichtlinien von Geräten zusammengefasst. Es ist die Anzahl der Geräte aufgeführt, die in jedem Konformitätszustand zu finden sind.


|Eigenschaft     |Beschreibung  |Beispiel  |
|---------|---------|---------|
|dateKey  |Datumsschlüssel, der angibt, wann die Zusammenfassung für die Konformitätsrichtlinie erstellt wurde|20161204 |
|unknown  |Anzahl der Geräte, die offline sind oder aus einem anderen Grund nicht mit Intune oder Azure AD kommunizieren können |5|
|notApplicable      |Anzahl der Geräte, auf denen vom Administrator festgelegte Gerätekonformitätsrichtlinien nicht angewendet werden|201 |
|compliant      |Anzahl der Geräte, für die mindestens eine vom Administrator festgelegte Gerätekompatibilitätsrichtlinie angewendet wurde |4083 |
|inGracePeriod      |Anzahl der Geräte, die nicht konform sind, sich aber in der vom Administrator definierten Toleranzperiode befinden |57|
|nonCompliant      |Anzahl der Geräte, die mindestens eine vom Administrator festgelegte Einstellung der Gerätekompatibilitätsrichtlinie nicht anwenden konnten, oder bei denen der Benutzer gegen die vom Administrator festgelegten Richtlinien verstößt|43 |
|Fehler      |Anzahl der Geräte, die nicht mit Intune oder Azure AD kommunizieren können und eine Fehlermeldung ausgeben |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities 

In der folgenden Tabelle sind die Zuweisungsstatus der Konformitätsrichtlinien von Geräten auf der Basis von Richtlinien und Richtlinientyp zusammengefasst. Es ist die Anzahl der Geräte aufgeführt, die in jedem Konformitätszustand für jede zugewiesene Konformitätsrichtlinie zu finden sind.



|Eigenschaft  |Beschreibung  |Beispiel  |
|---------|---------|---------|
|dateKey  |Datumsschlüssel, der angibt, wann die Zusammenfassung für die Konformitätsrichtlinie erstellt wurde|20161219|
|policyKey     |Schlüssel für die Konformitätsrichtlinie, für die die Zusammenfassung erstellt wurde |10178 |
|policyPlatformKey      |Schlüssel für den Plattformtyp der Konformitätsrichtlinie, für den die Zusammenfassung erstellt wurde|5|
|unknown     |Anzahl der Geräte, die offline sind oder aus einem anderen Grund nicht mit Intune oder Azure AD kommunizieren können|13|
|notApplicable     |Anzahl der Geräte, auf denen vom Administrator festgelegte Gerätekonformitätsrichtlinien nicht angewendet werden|3|
|compliant      |Anzahl der Geräte, für die mindestens eine vom Administrator festgelegte Gerätekompatibilitätsrichtlinie angewendet wurde |45|
|inGracePeriod      |Anzahl der Geräte, die nicht konform sind, sich aber in der vom Administrator definierten Toleranzperiode befinden |3|
|nonCompliant      |Anzahl der Geräte, die mindestens eine vom Administrator festgelegte Einstellung der Gerätekompatibilitätsrichtlinie nicht anwenden konnten, oder bei denen der Benutzer gegen die vom Administrator festgelegten Richtlinien verstößt|7|
|Fehler      |Anzahl der Geräte, die nicht mit Intune oder Azure AD kommunizieren können und eine Fehlermeldung ausgeben |3|

### <a name="policyplatformtypes"></a>policyPlatformTypes

Die folgende Tabelle enthält die Plattformtypen aller zugewiesenen Richtlinien. Plattformtypen von Richtlinien, die noch nie Geräten zugewiesen waren, sind in dieser Tabelle nicht aufgeführt.


|Eigenschaft  |Beschreibung  |Beispiel  |
|---------|---------|---------|
|policyPlatformTypeKey      |Der eindeutige Schlüssel für den Plattformtyp der Richtlinie |20170519 |
|policyPlatformTypeId      |Der eindeutige Bezeichner für den Plattformtyp der Richtlinie|1|
|policyPlatformTypeName      |Der Name für den Plattformtyp der Richtlinie|AndroidForWork |

### <a name="policydeviceactivities"></a>policyDeviceActivities

In der folgenden Tabelle ist die Anzahl der Geräte mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag aufgeführt. Die Anzahl spiegelt die Daten pro Richtlinientypprofil wider. Wenn ein Gerät beispielsweise den Zustand „erfolgreich“ für alle zugewiesenen Richtlinien aufweist, wird der Zähler für „erfolgreich“ für diesen Tag um eins erhöht. Wenn einem Gerät zwei Profile zugewiesen sind, von denen eines den Zustand „erfolgreich“ und eines den Zustand „Fehler“ aufweist, erhöht die Entität den Zähler für „erfolgreich“ und versetzt das Gerät in den Zustand „Fehler“. Die Entität „policyDeviceActivity“ listet für die letzten 30 Tage auf, wie viele Geräte an einem bestimmten Tag in welchem Zustand waren.

|Eigenschaft  |Beschreibung  |Beispiel  |
|---------|---------|---------|
|dateKey|Date Key für den Zeitpunkt als das Einchecken der Gerätekonfigurationsprofile im Data Warehouse aufgezeichnet wurde|20160703|
|pending|Anzahl eindeutiger Geräte im Zustand „ausstehend“|123|
|Succeeded|Anzahl eindeutiger Geräte im Zustand „erfolgreich“|12|
|policyKey|„policyKey“ kann mit „policy“ verknüpft werden, um den „policyName“ zu erhalten.|Windows 10-Baseline|
|Fehler|Anzahl eindeutiger Geräte im Zustand „Fehler“|10|
|Gescheitert|Anzahl eindeutiger Geräte im Zustand „fehlerhaft“|2|

### <a name="policyuseractivities"></a>policyUserActivities

In der folgenden Tabelle ist die Anzahl der Benutzer mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag aufgeführt. Die Anzahl spiegelt die Daten pro Richtlinientypprofil wider. Wenn ein Benutzer beispielsweise den Zustand „erfolgreich“ für alle zugewiesenen Richtlinien aufweist, wird der Zähler für „erfolgreich“ für diesen Tag um eins erhöht. Wenn einem Benutzer zwei Profile zugewiesen sind, von denen eines den Zustand „erfolgreich“ und eines den Zustand „Fehler“ aufweist, wird der Benutzer für den Zustand „Fehler“ gezählt. Die Entität PolicyUserActivity listet für die letzten 30 Tage auf, wie viele Benutzer an einem bestimmten Tag in welchem Zustand waren.


| Eigenschaft  |                                         Beschreibung                                         |       Beispiel       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  dateKey  | Date Key für den Zeitpunkt als das Einchecken der Gerätekonfigurationsprofile im Data Warehouse aufgezeichnet wurde |      20160703       |
|  pending  |                         Anzahl eindeutiger Geräte im Zustand „ausstehend“                          |         123         |
| Erfolgreich |                         Anzahl eindeutiger Geräte im Zustand „erfolgreich“                          |         12          |
| policyKey |                 „policyKey“ kann mit „policy“ verknüpft werden, um den „policyName“ zu erhalten.                 | Windows 10-Baseline |
|   Fehler   |                          Anzahl eindeutiger Geräte im Zustand „Fehler“                           |         10          |

