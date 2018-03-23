---
title: Mobile App-Verwaltung (MAM)
titlesuffix: Microsoft Intune
description: Referenzthema für die Kategorie „Verwaltung mobiler Anwendungen“ der Entitätsauflistungen in der Intune Data Warehouse-API.
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 084F11AD-F7BA-45A4-8424-45E6E4564930
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: eb9f63199063db34361c7d463b8cef37bb8bfa1f
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2018
---
# <a name="reference-for-mobile-app-management-mam-entities"></a>Verweis für MAM-Entitäten (Verwaltung mobiler Apps)

Die Kategorie **Verwaltung mobiler Apps (MAM)** enthält Entitäten für mobile Apps, z.B.:

  -  Apps
  -  Instanzen
  -  Eincheckstatus
  -  Integritätsstatus
  -  Richtlinienstatus
  -  Anmeldungsstatus
  -  Plattformtypen

## <a name="mamapplication"></a>MamApplication

Die Entität **MamApplication** führt branchenspezifische Apps (LOB, Line-of-Business) auf, die über die Verwaltung mobiler Geräte (MAM) ohne Registrierung in Ihrem Unternehmen verwaltet werden.

| Eigenschaft | Beschreibung | Beispiel |
|---------|------------|--------|
| ApplicationKey |Eindeutiger Bezeichner für die MAM-App im Data Warehouse |123 |
| ApplicationName |Name der MAM-App |„Word“ |
| ApplicationId |Anwendungs-ID der MAM-App |b66bc706-ffff-7437-0340-032819502773 |
| IsDeleted |Gibt an, ob dieser MAM-App-Datensatz aktualisiert wurde <br>Wahr: MAM-App verfügt über einen neuen Datensatz mit aktualisierten Feldern in dieser Tabelle. <br>Falsch: der neueste Datensatz für diese MAM-App. |Wahr/falsch |
| StartDateInclusiveUTC |Datum und Uhrzeit in UTC, als diese MAM-App im Data Warehouse erstellt wurde |23.11.2016 12:00:00 Uhr |
| DeletedDateUTC |Datum und Uhrzeit in UTC, als IsDeleted in TRUE geändert wurde |23.11.2016 12:00:00 Uhr |
| RowLastModifiedDateTimeUTC |Datum und Uhrzeit in UTC, als diese MAM-App zuletzt im Data Warehouse geändert wurde |23.11.2016 12:00:00 Uhr |

## <a name="mamapplicationinstance"></a>MamApplicationInstance

Die Entität **MamApplicationInstance** führt verwaltete MAM-Apps (Mobile Application Management, Verwaltung von mobilen Anwendungen) als Singularinstanz pro Benutzer pro Gerät auf. Alle aufgeführten Benutzer und Geräte in der Entität sind geschützt, d.h., ihnen wurde mindestens eine MAM-Richtlinie zugewiesen.

| Eigenschaft | Beschreibung | Beispiel |
|---------|------------|--------|
| ApplicationInstanceKey |Eindeutiger Bezeichner für die MAM-App-Instanz im Data Warehouse – Ersatzschlüssel |123 |
| UserId |Benutzer-ID des Benutzers, der diese MAM-App installiert hat |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationInstanceId |Eindeutiger Bezeichner der MAM-App-Instanz – ähnlich wie ApplicationInstanceKey, jedoch ist der Bezeichner ein natürlicher Schlüssel |b66bc706-ffff-7437-0340-032819502773 |
| ApplicationId |Anwendungs-ID dieser MAM-App |com.microsoft.groupies-daily.<IOS> |
| ApplicationVersion |Anwendungsversion dieser MAM-App |2 |
| CreatedDate |Datum, als dieser Datensatz der MAM-App-Instanz erstellt wurde. Der Wert kann NULL sein. |23.11.2016 12:00:00 |
| Plattform |Plattform des Geräts, auf dem diese MAM-App installiert wurde |2 |
| PlatformVersion |Plattformversion des Geräts, auf dem diese MAM-App installiert wurde |2.2 |
| SdkVersion |Die Version des MAM SDKs, mit der diese MAM-App umschlossen wurde |3.2 |
| DeviceId |Geräte-ID des Geräts, auf dem diese MAM-App installiert wurde |b66bc706-ffff-7437-0340-032819502773 |
| DeviceName |Gerätename des Geräts, auf dem diese MAM-App installiert wurde |„MyDevice“ |
| isDeleted |Gibt an, ob dieser Datensatz der MAM-App-Instanz aktualisiert wurde <br>Wahr: Diese MAM-App-Instanz verfügt über einen neuen Datensatz mit aktualisierten Feldern in dieser Tabelle. <br>Falsch: der neueste Datensatz für diese MAM-App-Instanz. |Wahr/falsch |
| StartDateInclusiveUtc |Datum und Uhrzeit in UTC, als diese MAM-App-Instanz im Data Warehouse erstellt wurde |23.11.2016 12:00:00 Uhr |
| DeletedDateUtc |Datum und Uhrzeit in UTC, als IsDeleted in TRUE geändert wurde |23.11.2016 12:00:00 Uhr |
| RowLastModifiedDateTimeUtc |Datum und Uhrzeit in UTC, als diese MAM-App-Instanz im Data Warehouse zuletzt geändert wurde |23.11.2016 12:00:00 Uhr |

## <a name="mamcheckin"></a>MamCheckin

Die Entität **MamCheckin** stellt Daten dar, die gesammelt wurden, als eine MAM-App-Instanz sich bei Intune Service gemeldet hat. 

> [!Note]  
> Wenn eine App-Instanz sich mehrmals pro Tag meldet, speichert das Data Warehouse dies als einmalige Anmeldung.

| Eigenschaft | Beschreibung | Beispiel |
|---------|------------|--------|
| DateKey |Date Key für den Zeitpunkt als das Einchecken der MAM-App im Data Warehouse aufgezeichnet wurde | 20160703 |
| ApplicationInstanceKey |Schlüssel der App-Instanz, der diesem Eincheckvorgang der MAM-App zugeordnet wird |02.5.1900 12:00:00 |
| UserKey |Schlüssel des Benutzers, der diesem Eincheckvorgang der MAM-App zugeordnet wird |12.01.1900 12:00:00 |
| ApplicationKey |Schlüssel der MAM-App, der eingecheckt wurde |10.01.1900 12:00:00 |
| DeviceHealthKey |Schlüssel von DeviceHealth, der diesem Eincheckvorgang der MAM-App zugeordnet wird |02.01.1900 12:00:00 |
| PlatformKey |Stellt die Plattform des Geräts dar, die diesem Eincheckvorgang der MAM-App zugeordnet wird |01.01.1900 12:00:00 |
| EffectiveAppliedPolicyKey |Stellt die effektiv angewendete Richtlinie dar, die mit der MAM-App in Verbindung gebracht wird, die eingecheckt wurde. Eine effektiv angewendete Richtlinie stammt vom Zusammenfügen aller Richtlinien, die für eine bestimmte App und einen Benutzer relevant sind. |02.5.1900 12:00:00 |
| LastCheckInDate |Datum und Uhrzeit, wann diese MAM-App zuletzt eingecheckt wurde. Der Wert kann NULL sein. |23.11.2016 12:00:00 Uhr |

## <a name="mamdevicehealth"></a>MamDeviceHealth

Die Entität **MamDeviceHealth** stellt Geräte dar, die bereitgestellte MAM-Richtlinien besitzen, auch wenn sie per Jailbreak manipuliert wurden.

| Eigenschaft | Beschreibung | Beispiel |
|---------|------------|--------|
| DeviceHealthKey |Eindeutiger Bezeichner des Geräts, der der Integrität im Data Warehouse zugeordnet wird – Ersatzschlüssel |01.01.1900 12:00:00 |
| DeviceHealth |Eindeutiger Bezeichner des Geräts und dessen Integrität – ähnlich wie DeviceHealthKey, allerdings ist der Bezeichner ein natürlicher Schlüssel |01.01.1900 12:00:00 |
| DeviceHealthName |Stellt den Status des Geräts dar. <br>Nicht verfügbar – keine Informationen zu diesem Gerät. <br>Fehlerfrei: Gerät wurde nicht per Jailbreak manipuliert. <br>Nicht Fehlerfrei: Gerät wurde per Jailbreak manipuliert. |Nicht verfügbar fehlerfrei nicht fehlerfrei |
| RowLastModifiedDateTimeUtc |Datum und Uhrzeit in UTC, als diese bestimmte MAM-Geräteintegrität im Data Warehouse zuletzt geändert wurde |23.11.2016 12:00:00 Uhr |

## <a name="mameffectivepolicy"></a>MamEffectivePolicy

Die Entität **MamEffectivePolicy** führt alle effektiven MAM-Richtlinien auf, die in Ihrer Organisation angewendet werden. Eine effektiv angewendete Richtlinie stammt vom Zusammenfügen aller Richtlinien, die für eine bestimmte App und einen Benutzer relevant sind.

| Eigenschaft | Beschreibung | Beispiel |
|---------|------------|--------|
| EffectivePolicyKey |Eindeutiger Bezeichner für die effektive MAM-Richtlinie im Data Warehouse |2 |
| RealPolicyKey |Eindeutiger Bezeichner der MAM-Richtlinie, die vom IT-Profi erstellt wurde. |1 |
| RowCreatedDateTimeUtc |Datum und Uhrzeit in UTC, als diese effektive MAM-Richtlinie im Data Warehouse erstellt wurde. |23.11.2016 12:00:00 Uhr |

## <a name="mamglobalapplication"></a>MamGlobalApplication

Die Entität **MamGlobalApplication** führt Store-Apps auf, die über die Verwaltung mobiler Geräte (MAM) ohne Registrierung in Ihrem Unternehmen verwaltet werden.

| Eigenschaft | Beschreibung | Beispiel |
|---------|------------|--------|
| ApplicationKey |Eindeutiger Bezeichner für die Store-App im Data Warehouse – auch als Ersatzschlüssel bekannt. |123 |
| ApplicationId |Eindeutiger Bezeichner der Store-App. Der Bezeichner ähnelt ApplicationKey, ist jedoch ein natürlicher Schlüssel. |com.microsoft.skydrive.<ios> |
| ApplicationName |Name der globalen MAM-Anwendung |Skydrive |
| RowLastModifiedDateTimeUtc |Datum und Uhrzeit in UTC, als diese bestimmte globale MAM-Anwendung im Data Warehouse zuletzt geändert wurde. |23.11.2016 12:00:00 Uhr |

## <a name="mamplatform"></a>MamPlatform

Die Entität **MamPlatform** führt Plattformnamen und -typen auf, auf denen eine MAM-App installiert wurde.

| Eigenschaft | Beschreibung | Beispiel |
|---------|------------|--------|
| PlatformKey |Eindeutiger Bezeichner für die Plattform im Data Warehouse – Ersatzschlüssel |123 |
| Plattform |Eindeutiger Bezeichner der Plattform – ähnlich wie PlatformKey, es handelt sich allerdings um einen natürlichen Schlüssel |123 |
| PlatformName |Plattformname |Nicht verfügbar <br>Keine <br>Windows <br>iOS <br>Android: |
| RowLastModifiedDateTimeUtc |Datum und Uhrzeit in UTC, als diese Plattform zuletzt im Data Warehouse geändert wurde |23.11.2016 12:00:00 Uhr |
