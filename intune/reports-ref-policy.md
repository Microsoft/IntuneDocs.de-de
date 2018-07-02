---
title: Richtlinie
titlesuffix: Microsoft Intune
description: Referenzthema für die Kategorie „Richtlinien“ der Entitätsauflistungen in der Intune Data Warehouse-API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 81fc62505d125195b07b80f7a52d9f2515fc2d3d
ms.sourcegitcommit: b47fad133ef8ef1eb65484463431c6c53f6a638a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35291562"
---
# <a name="reference-for-policy-entities"></a>Verweis für Richtlinienentitäten

Die Kategorie **Policy** (Richtlinien) enthält Entitäten für mobile Geräte, die folgende Informationen nachverfolgen:

  -  Inventar der Gerätekonfigurationsprofile, Appkonfigurationsprofile und Kompatibilitätsrichtlinien  
  -  Anzahl der Geräte mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag  
  -  Anzahl der Benutzer mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag  
  -  Gesamtzahl der Geräte mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“  

## <a name="policy"></a>Richtlinie

Die Entität **Policy** (Richtlinie) listet Gerätekonfigurationsprofile, Appkonfigurationsprofile und Kompatibilitätsrichtlinien auf. Sie können die Richtlinien mit der mobilen Geräteverwaltung (MDM) zu einer Gruppe in Ihrem Unternehmen zuweisen.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| PolicyKey |Eindeutiger Schlüssel, der die Richtlinie im Data Warehouse darstellen soll |123 |
| PolicyId |Eindeutiger Bezeichner der Richtlinie im Data Warehouse |b66bc706-ffff-7437-0340-032819502773 |
| PolicyName |Name der Richtlinie |"Windows 10-Baseline" |
| PolicyVersion |Version der Richtlinie Wenn die Richtlinie bearbeitet oder geändert wird, wird eine neuere Version erstellt. |1, 2, 3 |
| isDeleted |Gibt an, ob der Richtliniendatensatz aktualisiert wurde.  <br>Wahr: Richtlinie verfügt über einen neuen Datensatz mit aktualisierten Feldern. <br>Falsch: der neueste Datensatz für diese Richtlinie. |Wahr/falsch |
| StartDateInclusiveUTC |Datum und Uhrzeit in UTC, als diese Richtlinie im Data Warehouse erstellt wurde |23.11.2016 12:00:00 Uhr |
| DeletedDateUTC |Datum und Uhrzeit in UTC, als IsDeleted in TRUE geändert wurde |23.11.2016 12:00:00 Uhr |
| RowLastModifiedDateTimeUTC |Datum und Uhrzeit in UTC, als diese Richtlinie zuletzt im Data Warehouse geändert wurde |23.11.2016 12:00:00 Uhr |

## <a name="policytype"></a>PolicyType

Die Entität **PolicyType** listet Gerätekonfigurationsprofile, Appkonfigurationsprofile und Kompatibilitätsrichtlinien auf. Sie können die Richtlinien mit der mobilen Geräteverwaltung (MDM) zu einer Gruppe in Ihrem Unternehmen zuweisen.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| PolicyTypeId |Eindeutiger Bezeichner der Richtlinie im Quellsystem |123 |
| PolicyTypeKey |Eindeutiger Bezeichner der Richtlinie im Data Warehouse |1 |
| PolicyTypeName |Name des Richtlinientyps |Windows 10-Kompatibilitätsrichtlinie |

## <a name="deviceconfiguration"></a>DeviceConfiguration

Die Entität **DeviceConfigurationProfileDeviceActivity** listet die Anzahl der Geräte mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag auf. Die Anzahl gibt die Gerätekonfigurationsprofile an, die der Entität zugewiesen sind. Wenn ein Gerät beispielsweise den Zustand „erfolgreich“ für alle zugewiesenen Richtlinien aufweist, wird der Zähler für „erfolgreich“ für diesen Tag um eins erhöht. Wenn einem Gerät zwei Profile zugewiesen sind, von denen eines den Zustand „erfolgreich“ und eines den Zustand „Fehler“ aufweist, erhöht die Entität den Zähler für „erfolgreich“ und versetzt das Gerät in den Zustand „Fehler“. Die Entität listet für die letzten 30 Tage auf, wie viele Geräte an einem bestimmten Tag in welchem Zustand waren.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| DateKey |Date Key für den Zeitpunkt als das Einchecken der Gerätekonfigurationsprofile im Data Warehouse aufgezeichnet wurde |20160703 |
| Pending |Anzahl eindeutiger Geräte im Zustand „ausstehend“ |123 |
| Succeeded |Anzahl eindeutiger Geräte im Zustand „erfolgreich“ |12 |
| Fehler |Anzahl eindeutiger Geräte im Zustand „Fehler“ |10 |
| Failed |Anzahl eindeutiger Geräte im Zustand „fehlerhaft“ |2 |



Die Entität **DeviceConfigurationProfileUserActivity** listet die Anzahl der Benutzer mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag auf. Die Anzahl gibt die Gerätekonfigurationsprofile an, die der Entität zugewiesen sind. Wenn ein Benutzer beispielsweise den Zustand „erfolgreich“ für alle zugewiesenen Richtlinien aufweist, wird der Zähler für „erfolgreich“ für diesen Tag um eins erhöht. Wenn einem Benutzer zwei Profile zugewiesen sind, von denen eines den Zustand „erfolgreich“ und eines den Zustand „Fehler“ aufweist, wird der Benutzer für den Zustand „Fehler“ gezählt.  Die Entität **DeviceConfigurationProfileUserActivity** listet für die letzten 30 Tage auf, wie viele Benutzer an einem bestimmten Tag in welchem Zustand waren.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| DateKey |Date Key für den Zeitpunkt als das Einchecken der Gerätekonfigurationsprofile im Data Warehouse aufgezeichnet wurde |20160703 |
| Pending |Anzahl eindeutiger Benutzer im Zustand „ausstehend“ |123 |
| Succeeded |Anzahl eindeutiger Benutzer im Zustand „erfolgreich“ |12 |
| Fehler |Anzahl eindeutiger Benutzer im Zustand „Fehler“ |10 |
| Failed |Anzahl eindeutiger Benutzer im Zustand „fehlerhaft“ |2 |

## <a name="policytypeactivity"></a>PolicyTypeActivity

Die Entität **PolicyTypeActivity** listet die Gesamtzahl der Geräte im Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ auf. Diese Zustände werden im Bezug auf ein Gerätekonfigurationsprofil, ein Appkonfigurationsprofil oder eine Kompatibiliätsrichtlinie pro Tag aufgelistet.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| DateKey |Date Key für den Zeitpunkt, als das Einchecken der Gerätekonfigurationsprofile im Data Warehouse aufgezeichnet wurde |20160703 |
| PolicyKey |Der Richtlinienschlüssel kann mit der Richtlinie verknüpft werden, um den Richtliniennamen zu erhalten. |Windows 10-Baseline |
| PolicyTypeKey |Der Typ des Richtlinienschlüssels kann mit dem Richtlinientyp verknüpft werden, um den Namen des Richtlinientyps zu erhalten. |Windows 10-Kompatibilitätsrichtlinien |
| Pending |Anzahl eindeutiger Geräte im Zustand „ausstehend“ |123 |
| Succeeded |Anzahl eindeutiger Geräte im Zustand „erfolgreich“ |12 |
| Fehler |Anzahl eindeutiger Geräte im Zustand „Fehler“ |10 |
| Failed |Anzahl eindeutiger Geräte im Zustand „fehlerhaft“ |2 |

## <a name="compliance-policy"></a>Kompatibilitätsrichtlinie

Die API-Referenz der Konformitätsrichtlinie enthält Entitäten, die Statusinformationen über Konformitätsrichtlinien bereitstellen, die Geräten zugewiesen sind.

### <a name="compliancepolicystatusdeviceactivities"></a>CompliancePolicyStatusDeviceActivities

In der folgenden Tabelle sind die Zuweisungsstatus der Konformitätsrichtlinien von Geräten zusammengefasst. Es ist die Anzahl der Geräte aufgeführt, die in jedem Konformitätszustand zu finden sind.


|Eigenschaft     |Beschreibung  |Beispiel  |
|---------|---------|---------|
|DateKey  |Datumsschlüssel, der angibt, wann die Zusammenfassung für die Konformitätsrichtlinie erstellt wurde|20161204 |
|Unbekannt  |Anzahl der Geräte, die offline sind oder aus einem anderen Grund nicht mit Intune oder Azure AD kommunizieren können |5|
|NotApplicable      |Anzahl der Geräte, auf denen vom Administrator festgelegte Gerätekonformitätsrichtlinien nicht angewendet werden|201 |
|Kompatibel      |Anzahl der Geräte, für die mindestens eine vom Administrator festgelegte Gerätekompatibilitätsrichtlinie angewendet wurde |4083 |
|InGracePeriod      |Anzahl der Geräte, die nicht konform sind, sich aber in der vom Administrator definierten Toleranzperiode befinden |57|
|NonCompliant      |Anzahl der Geräte, die mindestens eine vom Administrator festgelegte Einstellung der Gerätekompatibilitätsrichtlinie nicht anwenden konnten, oder bei denen der Benutzer gegen die vom Administrator festgelegten Richtlinien verstößt|43 |
|Fehler      |Anzahl der Geräte, die nicht mit Intune oder Azure AD kommunizieren können und eine Fehlermeldung ausgeben |3|

### <a name="compliancepolicystatusdeviceperpolicyactivities"></a>CompliancePolicyStatusDevicePerPolicyActivities 

In der folgenden Tabelle sind die Zuweisungsstatus der Konformitätsrichtlinien von Geräten auf der Basis von Richtlinien und Richtlinientyp zusammengefasst. Es ist die Anzahl der Geräte aufgeführt, die in jedem Konformitätszustand für jede zugewiesene Konformitätsrichtlinie zu finden sind.



|Eigenschaft  |Beschreibung  |Beispiel  |
|---------|---------|---------|
|DateKey  |Datumsschlüssel, der angibt, wann die Zusammenfassung für die Konformitätsrichtlinie erstellt wurde|20161219|
|PolicyKey     |Schlüssel für die Konformitätsrichtlinie, für die die Zusammenfassung erstellt wurde |10178 |
|PolicyPlatformKey      |Schlüssel für den Plattformtyp der Konformitätsrichtlinie, für den die Zusammenfassung erstellt wurde|5|
|Unbekannt     |Anzahl der Geräte, die offline sind oder aus einem anderen Grund nicht mit Intune oder Azure AD kommunizieren können|13|
|NotApplicable     |Anzahl der Geräte, auf denen vom Administrator festgelegte Gerätekonformitätsrichtlinien nicht angewendet werden|3|
|Kompatibel      |Anzahl der Geräte, für die mindestens eine vom Administrator festgelegte Gerätekompatibilitätsrichtlinie angewendet wurde |45|
|InGracePeriod      |Anzahl der Geräte, die nicht konform sind, sich aber in der vom Administrator definierten Toleranzperiode befinden |3|
|NonCompliant      |Anzahl der Geräte, die mindestens eine vom Administrator festgelegte Einstellung der Gerätekompatibilitätsrichtlinie nicht anwenden konnten, oder bei denen der Benutzer gegen die vom Administrator festgelegten Richtlinien verstößt|7|
|Fehler      |Anzahl der Geräte, die nicht mit Intune oder Azure AD kommunizieren können und eine Fehlermeldung ausgeben |3|

### <a name="policyplatformtypes"></a>PolicyPlatformTypes

Die folgende Tabelle enthält die Plattformtypen aller zugewiesenen Richtlinien. Plattformtypen von Richtlinien, die noch nie Geräten zugewiesen waren, sind in dieser Tabelle nicht aufgeführt.


|Eigenschaft  |Beschreibung  |Beispiel  |
|---------|---------|---------|
|PolicyPlatformTypeKey      |Der eindeutige Schlüssel für den Plattformtyp der Richtlinie |20170519 |
|PolicyPlatformTypeId      |Der eindeutige Bezeichner für den Plattformtyp der Richtlinie|1|
|PolicyPlatformTypeName      |Der Name für den Plattformtyp der Richtlinie|AndroidForWork |

### <a name="policydeviceactivity"></a>PolicyDeviceActivity

In der folgenden Tabelle ist die Anzahl der Geräte mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag aufgeführt. Die Anzahl spiegelt die Daten pro Richtlinientypprofil wider. Wenn ein Gerät beispielsweise den Zustand „erfolgreich“ für alle zugewiesenen Richtlinien aufweist, wird der Zähler für „erfolgreich“ für diesen Tag um eins erhöht. Wenn einem Gerät zwei Profile zugewiesen sind, von denen eines den Zustand „erfolgreich“ und eines den Zustand „Fehler“ aufweist, erhöht die Entität den Zähler für „erfolgreich“ und versetzt das Gerät in den Zustand „Fehler“. Die Entität PolicyDeviceActivity listet für die letzten 30 Tage auf, wie viele Geräte an einem bestimmten Tag in welchem Zustand waren.

|Eigenschaft  |Beschreibung  |Beispiel  |
|---------|---------|---------|
|DateKey|Date Key für den Zeitpunkt als das Einchecken der Gerätekonfigurationsprofile im Data Warehouse aufgezeichnet wurde|20160703|
|Pending|Anzahl eindeutiger Geräte im Zustand „ausstehend“|123|
|Succeeded|Anzahl eindeutiger Geräte im Zustand „erfolgreich“|12|
PolicyKey|Der Richtlinienschlüssel kann mit der Richtlinie verknüpft werden, um den Richtliniennamen zu erhalten.|Windows 10-Baseline|
|Fehler|Anzahl eindeutiger Geräte im Zustand „Fehler“|10|
|Failed|Anzahl eindeutiger Geräte im Zustand „fehlerhaft“|2|

### <a name="policyuseractivity"></a>PolicyUserActivity 

In der folgenden Tabelle ist die Anzahl der Benutzer mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag aufgeführt. Die Anzahl spiegelt die Daten pro Richtlinientypprofil wider. Wenn ein Benutzer beispielsweise den Zustand „erfolgreich“ für alle zugewiesenen Richtlinien aufweist, wird der Zähler für „erfolgreich“ für diesen Tag um eins erhöht. Wenn einem Benutzer zwei Profile zugewiesen sind, von denen eines den Zustand „erfolgreich“ und eines den Zustand „Fehler“ aufweist, wird der Benutzer für den Zustand „Fehler“ gezählt. Die Entität PolicyUserActivity listet für die letzten 30 Tage auf, wie viele Benutzer an einem bestimmten Tag in welchem Zustand waren.


| Eigenschaft  |                                         Beschreibung                                         |       Beispiel       |
|-----------|---------------------------------------------------------------------------------------------|---------------------|
|  DateKey  | Date Key für den Zeitpunkt als das Einchecken der Gerätekonfigurationsprofile im Data Warehouse aufgezeichnet wurde |      20160703       |
|  Pending  |                         Anzahl eindeutiger Geräte im Zustand „ausstehend“                          |         123         |
| Succeeded |                         Anzahl eindeutiger Geräte im Zustand „erfolgreich“                          |         12          |
| PolicyKey |                Der Richtlinienschlüssel kann mit der Richtlinie verknüpft werden, um den Richtliniennamen zu erhalten.                 | Windows 10-Baseline |
|   Fehler   |                          Anzahl eindeutiger Geräte im Zustand „Fehler“                           |         10          |

