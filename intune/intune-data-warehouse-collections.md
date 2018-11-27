---
title: Sammlungen von Intune Date Warehouse
titlesuffix: Microsoft Intune
description: Die Intune Data Warehouse-Sammlungen bieten Details im Zusammenhang mit der Data Warehouse-API.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 29f09230-dc56-43db-b599-d961967bda49
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: d290fadf92ee112a1f663c6894861b393b81f74d
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190318"
---
#  <a name="intune-data-warehouse-collections"></a>Intune Data Warehouse-Sammlungen

Die folgenden Intune Data Warehouse-Sammlungen bieten die Eigenschaften, Beschreibungen und Beispiele für v1.0-Sammlungen der Data Warehouse-API-Entitäten. 

## <a name="apprevisions"></a>appRevisions
Die **appRevision**-Entität listet alle Versionen von Apps auf.

|          Eigenschaft          |                                      Beschreibung                                      |                Beispiel               |
|:--------------------------:|:-------------------------------------------------------------------------------------:|:------------------------------------:|
| AppKey                     | Eindeutiger Bezeichner der App                                                         | 123                                  |
| ApplicationId              | Eindeutiger Bezeichner einer App – ähnlich wie AppKey, dieser Schlüssel ist jedoch ein natürlicher Schlüssel.        | b66bc706-ffff-7437-0340-032819502773 |
| Revision                   | Die Version, die vom Administrator beim Upload der Binärdatei erwähnt wurde.                   | 2                                    |
| Titel                      | Titel der App                                                                     | Excel                                |
| Herausgeber                  | Herausgeber der App                                                                 | Microsoft                            |
| UploadState                | Hochladestatus der App                                                              | 1                                    |
| AppTypeKey                 | Der Verweis zu AppType wird im folgenden Abschnitt beschrieben.                            | 1                                    |
| VppProgramTypeKey          | Der Verweis zu VppProgramType wird weiter unten beschrieben.                                        | 30876                                |
| CreationTime               | Der Zeitpunkt, zu dem diese Revision erstellt wurde.                                            | 23.11.2016 0:00                      |
| ModifiedTime               | Der letzte Zeitpunkt, zu dem eine Änderung an einem mit dieser Revision verknüpften Element vorgenommen wurde.                            | 23.11.2016 0:00                      |
| Size                       | Größe der Binärdatei in Bytes.                                                          | 120.392.000                          |
| StartDateInclusiveUTC      | UTC-Zeitpunkt der Erstellung dieser App-Revision in Data Warehouse.      | 23.11.2016 0:00                      |
| EndDateExclusiveUTC        | UTC-Zeitpunkt, zu dem diese App-Revision als veraltet gekennzeichnet wurde.                        | 23.11.2016 0:00                      |
| IsCurrent                  | Gibt an, ob diese App-Version in Data Warehouse aktuell ist.         | Wahr/falsch                           |
| RowLastModifiedDateTimeUTC | UTC-Zeitpunkt, zu dem diese App-Version zuletzt in Data Warehouse geändert wurde. | 23.11.2016 0:00                      |

## <a name="apptypes"></a>appTypes
Die Entität **appType** führt die Installationsquelle einer App auf.

|   Eigenschaft  |        Beschreibung        |
|:-----------:|:-------------------------:|
| AppTypeID   | ID für den Typ           |
| AppTypeKey  | Untergeordneter Schlüssel für den Schlüssel |
| AppTypeName | App-Typ                  |

### <a name="example"></a>Beispiel

| AppTypeID |                Name               |                     Beschreibung                     |
|:---------:|:---------------------------------:|:---------------------------------------------------:|
| 0         | Android Store-App               | Eine Android Store-App.                             |
| 1         | Android-Branchen-App                 | Eine branchenspezifische Android-App.                  |
| 2         | Verwaltete Android Store-App (MAM) | Eine Android Store-App, für die die Verwaltung aktiviert ist. |
| 3         | iOS Store-App                   | Eine iOS Store-App.                                 |
| 4         | Branchenspezifische iOS-App                     | Eine branchenspezifische iOS-App.                      |
| 5         | Verwaltete iOS Store-App (MAM)     | Eine iOS Store-App, die für die Verwaltung aktiviert ist.       |
| 6         | O365 Pro Plus Suite             | Die Office 365 Pro Plus Suite für Windows 10.     |
| 7         | Web-App                         | Eine Web-App.                                        |
| 8         | Windows Phone 8.1 Store-App     | Eine Windows Phone 8.1 Store-App.                    |
| 9         | Windows Store-App               | Eine Windows Store-App.                              |
| 10        | Branchenspezifische Windows-Apps                | Eine branchenspezifische Windows-APPX-App.              |
| 11        | Windows Mobile MSI              | Eine branchenspezifische MSI-App.                      |
| 12        | Branchenspezifische Windows Phone-App           | Eine branchenspezifische Windows Phone-App.             |

## <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities
In der folgenden Tabelle sind die Zuweisungsstatus der Konformitätsrichtlinien von Geräten zusammengefasst. Es ist die Anzahl der Geräte aufgeführt, die in jedem Konformitätszustand zu finden sind.

|    Eigenschaft   |                                                                                      Beschreibung                                                                                     |  Beispiel |
|:-------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey       | Datumsschlüssel, der angibt, wann die Zusammenfassung für die Konformitätsrichtlinie erstellt wurde.                                                                                                                   | 20161204 |
| Unbekannt       | Anzahl der Geräte, die offline sind oder aus einem anderen Grund nicht mit Intune oder Azure AD kommunizieren können.                                                                           | 5        |
| NotApplicable | Anzahl der Geräte, auf denen vom Administrator festgelegte Gerätekonformitätsrichtlinien nicht angewendet werden.                                                                                     | 201      |
| Kompatibel     | Anzahl der Geräte, für die mindestens eine vom Administrator festgelegte Gerätekompatibilitätsrichtlinie angewendet wurde.                                                                        | 4083     |
| InGracePeriod | Anzahl der Geräte, die nicht konform sind, sich aber in der vom Administrator definierten Toleranzperiode befinden.                                                                                  | 57       |
| NonCompliant  | Anzahl der Geräte, die mindestens eine vom Administrator festgelegte Einstellung der Gerätekompatibilitätsrichtlinie nicht anwenden konnten, oder bei denen der Benutzer gegen die vom Administrator festgelegten Richtlinien verstößt. | 43       |
|    Fehler      |    Anzahl der Geräte, die nicht mit Intune oder Azure AD kommunizieren können und eine Fehlermeldung ausgeben.                                                                          |    3     |

## <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities
In der folgenden Tabelle sind die Zuweisungsstatus der Konformitätsrichtlinien von Geräten auf der Basis von Richtlinien und Richtlinientyp zusammengefasst. Es ist die Anzahl der Geräte aufgeführt, die in jedem Konformitätszustand für jede zugewiesene Konformitätsrichtlinie zu finden sind.

|      Eigenschaft     |                                                                                      Beschreibung                                                                                     |  Beispiel |
|:-----------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey           | Datumsschlüssel, der angibt, wann die Zusammenfassung für die Konformitätsrichtlinie erstellt wurde.                                                                                                                   | 20161219 |
| PolicyKey         | Schlüssel für die Konformitätsrichtlinie, für die die Zusammenfassung erstellt wurde.                                                                                                                   | 10178    |
| PolicyPlatformKey | Schlüssel für den Plattformtyp der Konformitätsrichtlinie, für den die Zusammenfassung erstellt wurde.                                                                                            | 5        |
| Unbekannt           | Anzahl der Geräte, die offline sind oder aus einem anderen Grund nicht mit Intune oder Azure AD kommunizieren können.                                                                           | 13       |
| NotApplicable     | Anzahl der Geräte, auf denen vom Administrator festgelegte Gerätekonformitätsrichtlinien nicht angewendet werden.                                                                                     | 3        |
| Kompatibel         | Anzahl der Geräte, für die mindestens eine vom Administrator festgelegte Gerätekompatibilitätsrichtlinie angewendet wurde.                                                                        | 45       |
| InGracePeriod     | Anzahl der Geräte, die nicht konform sind, sich aber in der vom Administrator definierten Toleranzperiode befinden.                                                                                  | 3        |
| NonCompliant      | Anzahl der Geräte, die mindestens eine vom Administrator festgelegte Einstellung der Gerätekompatibilitätsrichtlinie nicht anwenden konnten, oder bei denen der Benutzer gegen die vom Administrator festgelegten Richtlinien verstößt. | 7        |
| Fehler             | Anzahl der Geräte, die nicht mit Intune oder Azure AD kommunizieren können und eine Fehlermeldung ausgeben.                                                                             | 3        |
## <a name="compliancestates"></a>complianceStates

|      Eigenschaft      |                       Beschreibung                      |
|:------------------:|:------------------------------------------------------:|
| complianceStatus   | Konformitätsstatus von Geräten mit mdmStatusKey       |
| complianceStateKey | Konformitätsschlüssel gemäß des Geräte- und Konformitätsstatus |
| complianceStateID  | Die ID, die mit diesem Konformitätsstatus übereinstimmt                |

### <a name="example"></a>Beispiel

|  complianceStatus  |                       Beschreibung                      |
|:------------------:|:------------------------------------------------------:|
|    Unbekannt         |    Unbekannt                                                                        |
|    Kompatibel       |    Kompatibel.                                                                      |
|    Nicht richtlinienkonform    |       Gerät ist nicht konform und wird nicht in die Unternehmensressourcen einbezogen.             |
|    Conflict        |    Konflikt mit anderen Regeln.                                                      |
|    Fehler           |       Fehler                                                                       |
|    ConfigManager   |    Vom Configuration Manager verwaltet.                                                      |
|    InGracePeriod   |       Gerät ist nicht konform, hat aber immer noch Zugriff auf Unternehmensressourcen.          |

## <a name="dates"></a>Daten
Die **date**-Entität stellt Datumsangaben dar, die auf mehrere Data Warehouse-Entitäten verweisen.

|     Eigenschaft    |                       Beschreibung                      |    Beispiel    |
|:---------------:|:------------------------------------------------------:|:-------------:|
| DateKey         | Eindeutiger Bezeichner für dieses Datum im Data Warehouse | 20160703      |
| FullDate        | Dieses Datum wird im vollständigen Datums- und Uhrzeitformat dargestellt        | 3.7.2016 0:00 |
| DayOfWeek       | Wochentag                                            | 1             |
| DayOfMonth      | Tag des Monats                                           | 3             |
| DayOfYear       | Tag des Jahres                                            | 185           |
| WeekOfYear      | Woche des Jahres                                           | 28            |
| MonthOfYear     | Monat des Jahres                                      | 7             |
| CalendarQuarter | Kalenderquartal                                       | 3             |
| CalendarYear    | Kalenderjahr                                          | 2016          |
| DateKey         | Eindeutiger Bezeichner für dieses Datum im Data Warehouse | 20160703      |
| FullDate        | Dieses Datum wird im vollständigen Datums- und Uhrzeitformat dargestellt        | 3.7.2016 0:00 |
| DayOfWeek       | Wochentag                                            | 1             |
| DayOfMonth      | Tag des Monats                                           | 3             |
| DayOfYear       | Tag des Jahres                                            | 185           |
| WeekOfYear      | Woche des Jahres                                           | 28            |
| MonthOfYear     | Monat des Jahres                                      | 7             |
| CalendarQuarter | Kalenderquartal                                       | 3             |
| CalendarYear    | Kalenderjahr                                          | 2016          |

## <a name="devicecategories"></a>deviceCategories

|      Eigenschaft      |                                    Beschreibung                                   |                Beispiel               |
|:------------------:|:--------------------------------------------------------------------------------:|:------------------------------------:|
| deviceCategoryID   | Der eindeutige Bezeichner für die Gerätekategorie.                                       | fb415ba2-7c08-41f6-a5e5-685b50da2c4c |
| deviceCategoryKey  | Der eindeutige Bezeichner der Gerätekategorie im Data Warehouse – Ersatzschlüssel. | 1                                    |
| deviceCategoryName | Der Anzeigename für die Gerätekategorie.                                            | Smartphones                          |

## <a name="deviceconfigurationprofiledeviceactivities"></a>deviceConfigurationProfileDeviceActivities
Die Entität **DeviceConfigurationProfileDeviceActivity** listet die Anzahl der Geräte mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag auf. Die Anzahl gibt die Gerätekonfigurationsprofile an, die der Entität zugewiesen sind. Wenn ein Gerät beispielsweise den Zustand „erfolgreich“ für alle zugewiesenen Richtlinien aufweist, wird der Zähler für „erfolgreich“ für diesen Tag um eins erhöht. Wenn einem Gerät zwei Profile zugewiesen sind, von denen eines den Zustand „erfolgreich“ und eines den Zustand „Fehler“ aufweist, erhöht die Entität den Zähler für „erfolgreich“ und versetzt das Gerät in den Zustand „Fehler“. Die Entität listet für die letzten 30 Tage auf, wie viele Geräte an einem bestimmten Tag in welchem Zustand waren.

|  Eigenschaft |                                          Beschreibung                                          |  Beispiel |
|:---------:|:---------------------------------------------------------------------------------------------:|:--------:|
| DateKey   | Datumsschlüssel für den Zeitpunkt, zu dem das Einchecken des Gerätekonfigurationsprofils im Data Warehouse aufgezeichnet wurde. | 20160703 |
| Pending   | Anzahl eindeutiger Geräte im Zustand „ausstehend“                                                    | 123      |
| Succeeded | Anzahl eindeutiger Geräte im Zustand „erfolgreich“                                                    | 12       |
| Fehler     | Anzahl eindeutiger Geräte im Zustand „Fehler“                                                      | 10       |
| Failed    | Anzahl eindeutiger Geräte im Zustand „fehlerhaft“                                                     | 2        |

## <a name="deviceconfigurationprofileuseractivities"></a>deviceConfigurationProfileUserActivities 
Die Entität **DeviceConfigurationProfileUserActivity** listet die Anzahl der Benutzer mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag auf. Die Anzahl gibt die Gerätekonfigurationsprofile an, die der Entität zugewiesen sind. Wenn ein Benutzer beispielsweise den Zustand „erfolgreich“ für alle zugewiesenen Richtlinien aufweist, wird der Zähler für „erfolgreich“ für diesen Tag um eins erhöht. Wenn einem Benutzer zwei Profile zugewiesen sind, von denen eines den Zustand „erfolgreich“ und eines den Zustand „Fehler“ aufweist, wird der Benutzer für den Zustand „Fehler“ gezählt. Die Entität **DeviceConfigurationProfileUserActivity** listet für die letzten 30 Tage auf, wie viele Benutzer an einem bestimmten Tag in welchem Zustand waren. 

| Eigenschaft  | Beschreibung  | Beispiel  |
|------------|----------------------------------------------------------------------------------------------|-----------|
| DateKey  | Date Key für den Zeitpunkt als das Einchecken der Gerätekonfigurationsprofile im Data Warehouse aufgezeichnet wurde  | 20160703  |
| Pending  | Anzahl eindeutiger Benutzer im Zustand „ausstehend“  | 123  |
| Succeeded  | Anzahl eindeutiger Benutzer im Zustand „erfolgreich“  | 12  |
| Fehler  | Anzahl eindeutiger Benutzer im Zustand „Fehler“  | 10  |
| Failed  | Anzahl eindeutiger Benutzer im Zustand „fehlerhaft“  | 2  |

## <a name="devicepropertyhistories"></a>devicePropertyHistories

|          Eigenschaft          |                                                                                      Beschreibung                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DateKey                    | Verweis auf die Datumstabelle, die den Tag angibt                                                                                                                                          |
| DeviceKey                  | Der eindeutige Bezeichner des Geräts im Data Warehouse – Ersatzschlüssel. Dies ist ein Verweis auf die Gerätetabelle, die die Intune-Geräte-ID enthält.                               |
| DeviceName                 | Der Name des Geräts auf Plattformen, die das Benennen von Geräten ermöglichen. Auf anderen Plattformen wird von Intune einen Namen aus anderen Eigenschaften erstellt. Dieses Attribut kann nicht für alle Geräte zur Verfügung stehen. |
| DeviceRegistrationStateKey | Schlüssel des Attributs für den Geräteregistrierungsstatus dieses Geräts.                                                                                                                    |
| OwnerTypeKey               | Schlüssel des Besitzertypattributs für dieses Gerät: Unternehmen, persönlich oder unbekannt.                                                                                                  |
| ManagementStateKey         | Der Schlüssel des Verwaltungsstatus, der mit diesem Gerät verknüpft ist und den neuesten Zustand einer Remoteaktion angibt oder anzeigt, ob das Gerät per Jailbreak oder Rootzugriff manipuliert wurde.                                                |
| AzureADRegistered          | Gibt an, ob das Gerät in Azure Active Directory registriert ist.                                                                                                                             |
| ComplianceStateKey         | Ein Schlüssel zum Konformitätsstatus.                                                                                                                                                            |
| OSVersion                  | Betriebssystemversion                                                                                                                                                                          |
| JailBroken                 | Gibt an, ob das Gerät mit Jailbreak oder Rooting manipuliert wurde.                                                                                                                                         |
| DeviceCategoryKey          | Schlüssel des Gerätekategorieattributs für dieses Gerät.                                                                                                                                    |
## <a name="deviceregistrationstates"></a>deviceRegistrationStates
Die Entität **DeviceRegistrationState** stellt den Registrierungstyp dar, auf den von anderen Data Warehouse-Sammlungen verwiesen wird. 

|           Eigenschaft          |                                     Beschreibung                                     |
|:---------------------------:|:-----------------------------------------------------------------------------------:|
| deviceRegistrationStateID   | Der eindeutige Bezeichner für den Registrierungsstatus                                            |
| deviceRegistrationStateKey  | Der eindeutige Bezeichner des Registrierungsstatus im Data Warehouse – Ersatzschlüssel |
| deviceRegistrationStateName | Registrierungsstatus                                                                  |
|    NotRegistered                     |    Nicht registriert                                                                                                                                                                  |
|    Registriert                        |       Registriert                                                                                                                                                                   |
|    Revoked                           |       Der Status bedeutet, dass der IT-Administrator den Client blockiert hat und der Client wieder freigegeben werden kann. Wenn ein Gerät zurückgesetzt oder außer Kraft gesetzt wurde, kann es auch den Status „Revoked“ anzeigen.        |
|    KeyConflict                       |    Schlüsselkonflikt                                                                                                                                                                    |
|    ApprovalPending                   |    Ausstehende Genehmigung                                                                                                                                                                |
|    CertificateReset                  |    Zertifikat zurücksetzen                                                                                                                                                               |
|    NotRegisteredPendingEnrollment    |    Nicht registriert, Registrierung ausstehend                                                                                                                                               |
|    Unbekannt                           |    Unbekannter Status                                                                                                                                                                   |

## <a name="devices"></a>Geräte
In der Entität **device** werden alle für die Verwaltung registrierten Geräte und ihre entsprechenden Eigenschaften aufgelistet.

|          Eigenschaft          |                                                                                       Beschreibung                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DeviceKey                  | Der eindeutige Bezeichner des Geräts im Data Warehouse – Ersatzschlüssel.                                                                                                               |
| DeviceId                   | Eindeutiger Bezeichner des Geräts.                                                                                                                                                     |
| DeviceName                 | Der Name des Geräts auf Plattformen, die das Benennen von Geräten ermöglichen. Auf anderen Plattformen wird von Intune ein Name anhand anderer Eigenschaften erstellt. Dieses Attribut kann nicht für alle Geräte zur Verfügung stehen. |
| DeviceTypeKey              | Schlüssel des Gerätetypattributs für dieses Gerät.                                                                                                                                    |
| DeviceRegistrationState    | Schlüssel des Clientregistrierungsstatus-Attributs für dieses Gerät.                                                                                                                      |
| OwnerTypeKey               | Schlüssel des Besitzertypattributs für dieses Gerät: Unternehmen, persönlich oder unbekannt.                                                                                                    |
| EnrolledDateTime           | Zeitpunkt der Registrierung dieses Geräts.                                                                                                                                         |
| LastSyncDateTime           | Letztes bekanntes Einchecken des Geräts mit Intune.                                                                                                                                              |
| ManagementAgentKey         | Der Schlüssel des Verwaltungs-Agents, der mit diesem Gerät verknüpft ist.                                                                                                                             |
| ManagementStateKey         | Der Schlüssel des Verwaltungsstatus, der mit diesem Gerät verknüpft ist und den neuesten Zustand einer Remoteaktion angibt oder anzeigt, ob das Gerät per Jailbreak oder Rootzugriff manipuliert wurde.                                                |
| AzureADDeviceId            | Die Azure-Geräte-ID für dieses Gerät.                                                                                                                                                  |
| AzureADRegistered          | Gibt an, ob das Gerät in Azure Active Directory registriert ist.                                                                                                                             |
| DeviceCategoryKey          | Der Schlüssel der Kategorie, die mit diesem Gerät verknüpft ist.                                                                                                                                     |
| DeviceEnrollmentType       | Der Schlüssel des Registrierungstyps, der mit diesem Gerät verknüpft ist und die Registrierungsmethode angibt.                                                                                             |
| ComplianceStateKey         | Der Schlüssel des Konformitätsstatus, der mit diesem Gerät verknüpft ist.                                                                                                                             |
| OSVersion                  | Betriebssystemversion des Geräts                                                                                                                                                |
| EasDeviceId                | Die Exchange ActiveSync-ID des Geräts.                                                                                                                                                  |
| SerialNumber               | SerialNumber                                                                                                                                                                           |
| UserId                     | Eindeutiger Bezeichner für den Benutzer, der dem Gerät zugeordnet ist.                                                                                                                           |
| RowLastModifiedDateTimeUTC | UTC-Zeitpunkt, zu dem dieses Gerät zuletzt in Data Warehouse geändert wurde.                                                                                                       |
| Hersteller               | Der Hersteller der CPU                                                                                                                                                             |
| Modell                      | Gerätemodell                                                                                                                                                                    |
| OperatingSystem            | Betriebssystem des Geräts. Windows, iOS usw.                                                                                                                                   |
| isDeleted                  | Binärwert, der anzeigt, ob das Gerät gelöscht wurde oder nicht.                                                                                                                                 |
| AndroidSecurityPatchLevel  | Android-Sicherheitspatchebene                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| isSupervised               | Gibt an, ob das Gerät überwacht wird.                                                                                                                                                               |
| FreeStorageSpaceInBytes    | Freier Speicherplatz in Bytes.                                                                                                                                                                 |
| TotalStorageSpaceInBytes   | Speicherplatz insgesamt in Bytes.                                                                                                                                                                |
| EncryptionState            | In diesem Feld wird der Verschlüsselungsstatus des Geräts angezeigt.                                                                                                                                                      |
| SubscriberCarrier          | Netzbetreiber des Abonnenten des Geräts                                                                                                                                                       |
| PhoneNumber                | Telefonnummer des Geräts                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| CellularTechnology         | Mobilfunktechnologie des Geräts                                                                                                                                                    |
| WiFiMacAddress             | WiFi-MAC                                                                                                                                                                              |


## <a name="devicetypes"></a>deviceTypes
Die Entität **deviceType** stellt den Gerätetyp dar, auf den von anderen Data Warehouse-Entitäten verwiesen wird. Der Gerätetyp beschreibt in der Regel entweder das Gerätemodell, den Hersteller oder eine Kombination aus beidem.

|    Eigenschaft    |                                  Beschreibung                                 |
|:--------------:|:----------------------------------------------------------------------------:|
| DeviceTypeID   | Eindeutiger Bezeichner des Gerätetyps                                       |
| DeviceTypeKey  | Der eindeutige Bezeichner des Gerätetyps im Data Warehouse – Ersatzschlüssel. |
| DeviceTypeName | Gerätetyp                                                                |

### <a name="example"></a>Beispiel

| deviceTypeID |        Name       |                      Beschreibung                      |
|:------------:|:-----------------:|:-----------------------------------------------------:|
| -1           | Nicht verfügbar   | Der Gerätetyp ist nicht verfügbar.                     |
| 0            | desktop-           | Windows Desktop-Gerät                              |
| 1            | Windows           | Windows-Gerät                                      |
| 2            | WinMO6            | Windows Mobile 6.0-Gerät                           |
| 3            | Nokia             | Nokia-Gerät                                        |
| 4            | WindowsPhone      | Windows Phone-Gerät                                |
| 5            | Mac               | Mac-Gerät                                          |
| 6            | WinCE             | Windows CE-Gerät                                   |
| 7            | WinEmbedded       | Windows Embedded-Gerät                             |
| 8            | IPhone            | iPhone-Gerät                                       |
| 9            | IPad              | iPad-Gerät                                         |
| 10           | IPod              | iPod-Gerät                                         |
| 11           | Android           | Mit dem Geräteadministrator verwaltetes Android-Gerät   |
| 12           | ISocConsumer      | iSoc Consumer-Gerät                                |
| 13           | Unix              | Unix-Gerät                                         |
| 14           | MacMDM            | Mac OS X-Gerät, das mit dem integrierten MDM-Agent verwaltet wird |
| 15           | HoloLens          | HoloLens-Gerät                                    |
| 16           | SurfaceHub        | Surface Hub-Gerät                                  |
| 17           | AndroidForWork    | Android-Gerät, das mit dem Android-Profilbesitzer verwaltet wird  |
| 18           | AndroidEnterprise | Android Enterprise-Gerät.                          |
| 100          | BlackBerry        | Blackberry-Gerät                                   |
| 101          | Palm              | Palm-Gerät                                         |
| 255          | Unbekannt           | Unbekannter Gerätetyp                                 |

## <a name="deviceenrollmenttypes"></a>deviceEnrollmentTypes
Die Entität **deviceEnrollmentType** gibt an, wie ein Gerät registriert wurde. Der Registrierungstyp erfasst die Registrierungsmethode. In den Beispielen werden die verschiedenen Registrierungstypen und ihre Bedeutung aufgelistet.

|         Eigenschaft         |                                    Beschreibung                                    |
|:------------------------:|:---------------------------------------------------------------------------------:|
| deviceEnrollmentTypeID   | Der eindeutige Bezeichner des Registrierungstyps.                                       |
| deviceEnrollmentTypeKey  | Eindeutiger Bezeichner des Registrierungstyps im Data Warehouse – Ersatzschlüssel. |
| deviceEnrollmentTypeName | Registrierungstypname.                                                           |

### <a name="example"></a>Beispiel

| enrollmentTypeID |                Name                |                                        Beschreibung                                       |
|:----------------:|:----------------------------------:|:----------------------------------------------------------------------------------------:|
| 0                | Unbekannt                            | Registrierungstyp wurde nicht gesammelt                                                      |
| 1                | UserEnrollment                     | Benutzergesteuerte Registrierung über BYOD-Kanal.                                           |
| 2                | DeviceEnrollmentManager            | Benutzerregistrierung mit einem Geräteregistrierungs-Manager-Konto.                              |
| 3                | AppleBulkWithUser                  | Apple-Massenregistrierung mit Benutzer-Captcha. (DEP, Apple Configurator)                   |
| 4                | AppleBulkWithoutUser               | Apple-Massenregistrierung ohne Benutzer-Captcha.   (DEP, Apple Configurator, Mobile Config) |
| 5                | WindowsAzureADJoin                 | Windows 10-Azure AD-Join.                                                                |
| 6                | WindowsBulkUserless                | Windows 10-Massenregistrierung über ICD mit Zertifikat.                               |
| 7                | WindowsAutoEnrollment              | Automatische Windows 10-Registrierung.   (Geschäftskonto hinzufügen)                                    |
| 8                | WindowsBulkAzureDomainJoin         | Windows 10-Massen-Azure AD-Join.                                                           |
| 9                | WindowsCoManagement                | Von AutoPilot oder Gruppenrichtlinie ausgelöste Windows 10 Co-Verwaltung.                       |
| 10               | WindowsAzureADJoinsUsingDeviceAuth | Windows 10-Azure AD-Join mit Geräteauthentifizierung.                                            |


## <a name="intunemanagementextensions"></a>intuneManagementExtensions
Die **intuneManagementExtension** listet täglich den Integritätsstatus von **intuneManagementExtension** auf jedem Windows 10-Gerät auf. Die Daten der letzten 60 Tage werden aufbewahrt.

|       Eigenschaft      |                          Beschreibung                          | Beispiel |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| DateKey             | Eindeutiger Datumsbezeichner                                | 123     |
| TenantKey           | Eindeutiger Mandantenbezeichner                              | 456     |
| DeviceKey           | Eindeutiger Bezeichner des Geräts                              | 789     |
| ExtensionVersionKey | Eindeutiger Bezeichner für die IntuneManagementExtension-Version. | 1       |
| ExtensionStateKey   | Eindeutiger Bezeichner des Integritätszustands                            | 2       |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates
**intuneManagementExtensionHealthState** listet alle möglichen Status der **IntuneManagementExtension** auf.

|      Eigenschaft     |                   Beschreibung                  | Beispiel |
|:-----------------:|:----------------------------------------------:|:-------:|
| ExtensionStateKey | Eindeutiger Bezeichner des Integritätszustands.           | 2       |
| ExtensionState    | Der Integritätsstatus einer IntuneManagementExtension. | Healthy |

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions
Die Entität **IntuneManagementExtensionVersion** listet alle von **IntuneManagementExtension** verwendeten Versionen auf.

|       Eigenschaft      |                          Beschreibung                          | Beispiel |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| ExtensionVersionKey | Eindeutiger Bezeichner für die IntuneManagementExtension-Version. | 1       |
| ExtensionVersion    | Die vierstellige Versionsnummer                                   | 1.0.2.0 |

## <a name="managementagenttypes"></a>managementAgentTypes
Die Entität **managementAgentType** stellt die Agents dar, die zum Verwalten von Geräten verwendet werden.

|         Eigenschaft        |                                       Beschreibung                                       |
|:-----------------------:|:---------------------------------------------------------------------------------------:|
| ManagementAgentTypeID   | Eindeutige Bezeichner des Verwaltungs-Agent-Typen                                         |
| ManagementAgentTypeKey  | Eindeutiger Bezeichner des Verwaltungs-Agent-Typen im Data Warehouse – Ersatzschlüssel. |
| ManagementAgentTypeName | Gibt an, welche Art von Agent zum Verwalten des Geräts verwendet wird                              |

### <a name="example"></a>Beispiel

| ManagementAgentTypeID |                Name               |                                  Beschreibung                                 |
|:---------------------:|:---------------------------------:|:----------------------------------------------------------------------------:|
| 1                     | EAS                               | Das Gerät wird mithilfe von Exchange Active Sync verwaltet.                         |
| 2                     | MDM                               | Das Gerät wird mit einem MDM-Agent verwaltet.                                   |
| 3                     | EasMdm                            | Das Gerät wird sowohl von Exchange Active Sync als auch einem MDM-Agent verwaltet.        |
| 4                     | IntuneClient                      | Das Gerät wird vom Intune-PC-Agent verwaltet.                               |
| 5                     | EasIntuneClient                   | Das Gerät wird sowohl von Exchange ActiveSync als auch vom Intune-PC-Agent verwaltet. |
| 8                     | ConfigManagerClient               | Das Gerät wird vom System Center Configuration Manager-Agent verwaltet.     |
| 10                    | ConfigurationManagerClientMdm     | Das Gerät wird vom Configuration Manager und MDM verwaltet.                    |
| 11                    | ConfigurationManagerCLientMdmEas  | Das Gerät wird von Configuration Manager, MDM und Eas verwaltet.               |
| 16                    | Unbekannt                           | Unbekannter Verwaltungs-Agent-Typ                                              |
| 32                    | Jamf                              | Die Geräteattribute werden von Jamf abgerufen.                               |
| 64                    | GoogleCloudDevicePolicyController |  Das Gerät wird von CloudDPC von Google verwaltet.                                 |

## <a name="managementstates"></a>managementStates
Die Entität **managementState** stellt Details zum Status des Geräts bereit. Details können nützlich sein, wenn Remoteaktionen angewendet werden, das Gerät per Jailbreak oder Rootzugriff manipuliert wurde.

|       Eigenschaft      |                                     Beschreibung                                    |
|:-------------------:|:----------------------------------------------------------------------------------:|
| managementStateID   | Der eindeutige Bezeichner des Verwaltungsstatus.                                       |
| managementStateKey  | Der eindeutige Bezeichner des Verwaltungsstatus im Data Warehouse – Ersatzschlüssel. |
| managementStateName | Gibt den Status der Remoteaktion an, die auf dieses Gerät angewendet wurde.                 |

### <a name="example"></a>Beispiel

| managementStateID |      Name      |                                                   Beschreibung                                                   |
|:-----------------:|:--------------:|:---------------------------------------------------------------------------------------------------------------:|
| 0                 | Verwaltet        | Verwaltet ohne ausstehende Remoteaktionen.                                                                       |
| 1                 | RetirePending  | Für das Gerät steht ein Befehl zum Außerkraftsetzen aus.                                                             |
| 2                 | RetireFailed   | Der Befehl zum Außerkraftsetzen konnte auf dem Gerät nicht ausgeführt werden.                                                                      |
| 3                 | WipePending    | Für das Gerät steht ein Zurücksetzungsbefehl aus.                                                               |
| 4                 | WipeFailed     | Der Zurücksetzungsbefehl konnte auf dem Gerät nicht ausgeführt werden.                                                                        |
| 5                 | Unhealthy      | Fehlerhafter Zustand.                                                                                              |
| 6                 | DeletePending  | Für das Gerät steht ein Löschungsbefehl aus.                                                             |
| 7                 | RetireIssued   | Ein Befehl zum Außerkraftsetzen wurde an das Gerät ausgegeben.                                                               |
| 8                 | WipeIssued     | Ein Zurücksetzungsbefehl wurde ausgegeben.                                                                               |
| 9                 | WipeCanceled   | Ein Zurücksetzungsbefehl wurde abgebrochen.                                                                               |
| 10                | RetireCanceled | Ein Befehl zum Außerkraftsetzen wurde abgebrochen.                                                                             |
| 11                | Discovered     | Das Gerät wird von Intune neu ermittelt und erhält beim ersten Einchecken den Status „Verwaltet“. |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates
Die Entität MobileAppInstallState stellt den Installationsstatus für eine mobile Anwendung dar, nachdem sie einer Gruppe, die Geräte und/oder Benutzer enthält, zugewiesen wurde.

|       Eigenschaft      |                        Beschreibung                       |
|:-------------------:|:--------------------------------------------------------:|
| AppInstallStateKey  | Die eindeutige ID des App-Installationsstatus für Ihr Konto |
| AppInstallState     | Enumerationswert des App-Installationsstatus                     |
| AppInstallStateName | Name des App-Installationsstatus                           |

## <a name="mobileappinstallstatuscounts"></a>mobileAppInstallStatusCounts
Stellt den Installationsstatus einer mobilen App für einen bestimmten Gerätetyp unter Verwendung der mobilen Anwendungsverwaltung mit Microsoft Intune dar.

|      Eigenschaft      |                                                          Beschreibung                                                          |
|:------------------:|:-----------------------------------------------------------------------------------------------------------------------------:|
| DateKey            | Schlüssel des Datums, an dem der App-Installationsstatus erfasst wurde                                                                     |
| AppKey             | Schlüssel der mobilen App, mit der eine Instanz von AppRevision identifiziert wird.                                                          |
| DeviceTypeKey      | Schlüssel des Gerätetyps, der der mobilen Anwendung zugeordnet ist.                                                              |
| AppInstallStateKey | Schlüssel des App-Installationsstatus, der zur Identifizierung einer Instanz von MobileAppInstallState verwendet wird.                                         |
| ErrorCode          | Der vom App-Installer zurückgegebene Fehlercode, die mobile Plattform oder der Dienst zur Installation der App. |
| Anzahl              | Gesamtanzahl.                                                                                                                  |

## <a name="ownertypes"></a>ownerTypes
Die Entität **ownerType** gibt an, ob ein Gerät einem Unternehmen oder einer Privatperson gehört, oder ob der Besitzer unbekannt ist.

|    Eigenschaft   |                                                                                     Beschreibung                                                                                    |           Beispiel          |
|:-------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------:|
| ownerTypeID   | Eindeutiger Bezeichner des Besitzertyps                                                                                                                                               |                            |
| ownerTypeKey  | Eindeutiger Bezeichner des Besitzertyps im Data Warehouse – Ersatzschlüssel.                                                                                                       |                            |
| ownerTypeName | Stellt den Besitzertyp des Geräts dar: Unternehmen: Das Gerät gehört einem Unternehmen.  Persönlich: Das Gerät befindet sich im Privatbesitz (BYOD).   Unbekannt: Es liegen keine Informationen zu diesem Gerät vor. | Unternehmen, Persönlich, Unbekannt |

## <a name="policies"></a>Richtlinien
Die Entität **Policy** (Richtlinie) listet Gerätekonfigurationsprofile, Appkonfigurationsprofile und Kompatibilitätsrichtlinien auf. Sie können die Richtlinien mit der mobilen Geräteverwaltung (MDM) zu einer Gruppe in Ihrem Unternehmen zuweisen.

|          Eigenschaft          |                                                                       Beschreibung                                                                      |                Beispiel               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| PolicyKey                  | Eindeutiger Schlüssel, der die Richtlinie im Data Warehouse darstellen soll                                                                                              | 123                                  |
| PolicyId                   | Eindeutiger Bezeichner der Richtlinie im Data Warehouse                                                                                                 | b66bc706-ffff-7437-0340-032819502773 |
| PolicyName                 | Name der Richtlinie                                                                                                                                    | "Windows 10-Baseline"                |
| PolicyVersion              | Version der Richtlinie Wenn die Richtlinie bearbeitet oder geändert wird, wird eine neuere Version erstellt.                                                             | 1, 2, 3                              |
| isDeleted                  | Gibt an, ob der Richtliniendatensatz aktualisiert wurde.  Wahr: Richtlinie verfügt über einen neuen Datensatz mit aktualisierten Feldern.  Falsch: Der neueste Datensatz für die Richtlinie. | Wahr/falsch                           |
| StartDateInclusiveUTC      | UTC-Zeitpunkt, zu dem diese Richtlinie im Data Warehouse erstellt wurde.                                                                              | 23.11.2016 0:00                      |
| DeletedDateUTC             | Datum und Uhrzeit in UTC, als IsDeleted in TRUE geändert wurde                                                                                                   | 23.11.2016 0:00                      |
| RowLastModifiedDateTimeUTC | UTC-Zeitpunkt, zu dem die Richtlinie zuletzt im Data Warehouse geändert wurde.                                                                        | 23.11.2016 0:00                      |

## <a name="policydeviceactivities"></a>policyDeviceActivities
In der folgenden Tabelle ist die Anzahl der Geräte mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag aufgeführt. Die Anzahl spiegelt die Daten pro Richtlinientypprofil wider. Wenn ein Gerät beispielsweise den Zustand „erfolgreich“ für alle zugewiesenen Richtlinien aufweist, wird der Zähler für „erfolgreich“ für diesen Tag um eins erhöht. Wenn einem Gerät zwei Profile zugewiesen sind, von denen eines den Zustand „erfolgreich“ und eines den Zustand „Fehler“ aufweist, erhöht die Entität den Zähler für „erfolgreich“ und versetzt das Gerät in den Zustand „Fehler“. Die Entität **policyDeviceActivity** listet für die letzten 30 Tage auf, wie viele Geräte an einem bestimmten Tag in welchem Zustand waren.

|  Eigenschaft |                                           Beschreibung                                           |        Beispiel        |
|:---------:|:-----------------------------------------------------------------------------------------------:|:---------------------:|
| DateKey   | Datumsschlüssel für den Zeitpunkt, zu dem das Einchecken des Gerätekonfigurationsprofils im Data Warehouse aufgezeichnet wurde. | 20160703              |
| Pending   | Anzahl eindeutiger Geräte im Zustand „ausstehend“.                                                    | 123                   |
| Succeeded | Anzahl eindeutiger Geräte im Zustand „erfolgreich“.                                                    | 12                    |
| PolicyKey | Der Richtlinienschlüssel kann mit der Richtlinie verknüpft werden, um den Richtliniennamen zu erhalten.                                  | Windows 10-Baseline |
| Fehler     | Anzahl eindeutiger Geräte im Zustand „Fehler“.                                                      | 10                    |
| Failed    | Anzahl eindeutiger Geräte im Zustand „fehlerhaft“.                                                     | 2                     |

## <a name="policyplatformtypes"></a>policyPlatformTypes

|        Eigenschaft        |                      Beschreibung                      |     Beispiel    |
|:----------------------:|:-----------------------------------------------------:|:--------------:|
| PolicyPlatformTypeKey  | Der eindeutige Schlüssel für den Plattformtyp der Richtlinie.        | 20170519       |
| PolicyPlatformTypeId   | Der eindeutige Bezeichner für den Plattformtyp der Richtlinie. | 1              |
| PolicyPlatformTypeName | Der Name für den Plattformtyp der Richtlinie.              | AndroidForWork |

## <a name="policytypeactivities"></a>policyTypeActivities
Die Entität **PolicyTypeActivity** listet die Gesamtzahl der Geräte im Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ auf. Diese Zustände werden im Bezug auf ein Gerätekonfigurationsprofil, ein Appkonfigurationsprofil oder eine Kompatibiliätsrichtlinie pro Tag aufgelistet.

|    Eigenschaft   |                                          Beschreibung                                          |           Beispiel           |
|:-------------:|:---------------------------------------------------------------------------------------------:|:---------------------------:|
| DateKey       | Datumsschlüssel für den Zeitpunkt, zu dem das Einchecken des Gerätekonfigurationsprofils im Data Warehouse aufgezeichnet wurde. | 20160703                    |
| PolicyKey     | Der Richtlinienschlüssel kann mit der Richtlinie verknüpft werden, um den Richtliniennamen zu erhalten.                                | Windows 10-Baseline         |
| PolicyTypeKey | Der Typ des Richtlinienschlüssels kann mit dem Richtlinientyp verknüpft werden, um den Namen des Richtlinientyps zu erhalten.             | Windows 10-Kompatibilitätsrichtlinien |
| Pending       | Anzahl eindeutiger Geräte im Zustand „ausstehend“                                                    | 123                         |
| Succeeded     | Anzahl eindeutiger Geräte im Zustand „erfolgreich“                                                    | 12                          |
| Fehler         | Anzahl eindeutiger Geräte im Zustand „Fehler“                                                      | 10                          |
| Failed        | Anzahl eindeutiger Geräte im Zustand „fehlerhaft“                                                     | 2                           |

## <a name="policytypes"></a>policyTypes
Die Entität **PolicyType** listet Gerätekonfigurationsprofile, Appkonfigurationsprofile und Kompatibilitätsrichtlinien auf. Sie können die Richtlinien mit der mobilen Geräteverwaltung (MDM) zu einer Gruppe in Ihrem Unternehmen zuweisen.

|    Eigenschaft    |                       Beschreibung                      |            Beispiel            |
|:--------------:|:------------------------------------------------------:|:-----------------------------:|
| PolicyTypeId   | Eindeutiger Bezeichner der Richtlinie im Quellsystem  | 123                           |
| PolicyTypeKey  | Eindeutiger Bezeichner der Richtlinie im Data Warehouse | 1                             |
| PolicyTypeName | Name des Richtlinientyps                               | Windows 10-Kompatibilitätsrichtlinie |

## <a name="policyuseractivities"></a>policyUserActivities
In der folgenden Tabelle ist die Anzahl der Benutzer mit dem Zustand „erfolgreich“, „ausstehend“, „fehlerhaft“ oder „Fehler“ pro Tag aufgeführt. Die Anzahl spiegelt die Daten pro Richtlinientypprofil wider. Wenn ein Benutzer beispielsweise den Zustand „erfolgreich“ für alle zugewiesenen Richtlinien aufweist, wird der Zähler für „erfolgreich“ für diesen Tag um eins erhöht. Wenn einem Benutzer zwei Profile zugewiesen sind, von denen eines den Zustand „erfolgreich“ und eines den Zustand „Fehler“ aufweist, wird der Benutzer für den Zustand „Fehler“ gezählt. Die Entität **PolicyUserActivity** listet für die letzten 30 Tage auf, wie viele Benutzer an einem bestimmten Tag in welchem Zustand waren.

|  Eigenschaft |                                          Beschreibung                                          |       Beispiel       |
|:---------:|:---------------------------------------------------------------------------------------------:|:-------------------:|
| DateKey   | Datumsschlüssel für den Zeitpunkt, zu dem das Einchecken des Gerätekonfigurationsprofils im Data Warehouse aufgezeichnet wurde. | 20160703            |
| Pending   | Anzahl eindeutiger Geräte im Zustand „ausstehend“                                                    | 123                 |
| Succeeded | Anzahl eindeutiger Geräte im Zustand „erfolgreich“                                                    | 12                  |
| PolicyKey | Der Richtlinienschlüssel kann mit der Richtlinie verknüpft werden, um den Richtliniennamen zu erhalten.                                | Windows 10-Baseline |
| Fehler     | Anzahl eindeutiger Geräte im Zustand „Fehler“                                                      | 10                  |

## <a name="termsandconditions"></a>termsAndConditions
Eine **termsAndConditions**-Entität stellt Metadaten und Inhalt einer bestimmten Richtlinie für Geschäftsbedingungen (T&C, Terms and Conditions) dar. Die Inhalte der T&C-Richtlinien werden Benutzern bei ihrem ersten Versuch angezeigt, sich bei Intune zu registrieren, und in der Folge bei Änderungen, zu denen ein Administrator eine erneute Zustimmung anfordert. Mit ihnen können Administratoren die Bedingungen kommunizieren, denen ein Benutzer zustimmen muss, um Geräte in Intune registrieren zu lassen.

|    Eigenschaft        |    Beschreibung    |    Beispiel        |
|----------------------------------|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------|
|    termsAndConditionsKey    |    Ein Schlüssel, der einem Eintrag in der Sammlung „userTermsAndConditionsAcceptances“ entspricht.    |    123    |
|    termsAndCondidionsId    |    Die ID für diesen termsAndConditions-Eintrag.    |    276edcb7-7440-4339-b6c5-8b6fc556fee6    |
|    termsAndConditionsVersion    |    Die Version dieses termsAndConditions-Eintrags.    |    1    |
|    Name    |    Der Name dieses termsAndConditions-Eintrags.        |    Intune-Nutzungsbedingungen     |
|    description    |    Die Beschreibung dieser Geschäftsbedingungen.     |         |
|    title    |    Der Titel dieser Geschäftsbedingungen.     |    Unternehmensrichtlinie zur Geräteverwaltung        |
|    summaryOfTerms    |    Die Zusammenfassung der Nutzungsbedingungen, die dem Benutzer übergeben wird.     |    Ich stimme den Geschäftsbedingungen zu.    |
|    termsAndConditionsBodyText    |    Der Text dieser Geschäftsbedingungen.       |    *Geräteverschlüsselung:* Durchsetzung einer 6-stelligen PIN    |
|    isDeleted    |    „True“ oder „False“, je nachdem, ob dieser Wert gelöscht ist.     |    False    |
|    startDateInclusiveUTC    |    Das Startdatum dieser Geschäftsbedingungen.     |    23.8.2018 4:01:34 Uhr    |
|    endDateEclusiveUTC    |    Das Enddatum dieser Geschäftsbedingungen.     |    31.12.9999 0:00:00 Uhr    |

## <a name="userdeviceassociations"></a>userDeviceAssociations
Die Entität **UserDeviceAssociation** enthält Zuweisungen von Benutzergeräten in Ihrer Organisation.

|        Name        |                                             Beschreibung                                            |     Beispiel     |
|:------------------:|:--------------------------------------------------------------------------------------------------:|:---------------:|
| UserKey            | Eindeutiger Bezeichner für den Benutzer im Data Warehouse   (Ersatzschlüssel)                            | 123             |
| DeviceKey          | Eindeutiger Bezeichner für das Gerät im Data Warehouse                                             | 123             |
| CreatedDateTimeUTC | Zeitpunkt, zu dem die Benutzergerätezuordnung erstellt wurde. Verwendet UTC-Format                     | 23.11.2016 0:00 |
| isDeleted          | Gibt an, dass der Benutzer dieses Geräts die Registrierung aufgehoben hat und die Zuordnung nicht mehr aktuell ist. | Wahr/falsch      |
| EndedDateTimeUTC   | Datum und Uhrzeit in UTC, als IsDeleted in TRUE geändert wurde                                               | 23.6.2017 0:00 Uhr  |

## <a name="users"></a>Benutzer
Die Entität **user** listet alle Benutzer von Azure Active Directory (Azure AD) mit zugewiesenen Lizenzen in Ihrem Unternehmen auf.

Die Entitätssammlung **user** enthält Benutzerdaten. Zu diesen Datensätzen gehören Benutzerzustände während der Datensammlung, selbst wenn der Benutzer entfernt wurde. Beispielsweise kann ein Benutzer in Intune hinzugefügt und dann im Verlauf des letzten Monats entfernt worden sein. Auch wenn dieser Benutzer zum Zeitpunkt der Berichterstellung nicht vorhanden ist, liegen Angaben zu Benutzer und Zustand in den Daten aus dem vorherigen Monat vor. Sie können einen Bericht erstellen, der die Dauer der Präsenz des Benutzers in Ihren Daten zeigt.

|          Eigenschaft          |                                                                                                           Beschreibung                                                                                                          |                Beispiel               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| UserKey                    | Eindeutiger Bezeichner des Benutzers im Data Warehouse – Ersatzschlüssel.                                                                                                                                                         | 123                                  |
| UserId                     | Eindeutiger Bezeichner des Benutzers – ähnlich wie UserKey, ist jedoch ein natürlicher Schlüssel.                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| UserEmail                  | E-Mail-Adresse des Benutzers                                                                                                                                                                                                     | John@constoso.com                    |
| UPN                        | Der Prinzipalname des Benutzers.                                                                                                                                                                                               | John@constoso.com                    |
| DisplayName                | Anzeigename des Benutzers                                                                                                                                                                                                      | John                                 |
| IntuneLicensed             | Gibt an, ob dieser Benutzer über Intune lizenziert ist oder nicht.                                                                                                                                                                              | Wahr/falsch                           |
| isDeleted                  | Gibt an, ob alle Lizenzen des Benutzers abgelaufen sind und ob der Benutzer daher aus Intune entfernt wurde. Dieses Flag wird für einen einzelnen Datensatz nicht geändert. Stattdessen wird ein neuer Datensatz für einen neuen Benutzerzustand erstellt. | Wahr/falsch                           |
| RowLastModifiedDateTimeUTC | UTC-Zeitpunkt, zu dem der Datensatz im Data Warehouse zuletzt geändert wurde.                                                                                                                                                 | 23.11.2016 0:00                      |

## <a name="usertermsandconditionsacceptances"></a>userTermsAndConditionsAcceptances
Eine **userTermsAndConditionsAcceptance**-Entität stellt den Akzeptanzstatus einer bestimmten Richtlinie von Geschäftsbedingungen (T&C) von einem bestimmten Benutzer dar. Benutzer müssen die aktuelle Version der Nutzungsbedingungen akzeptieren, um den Zugriff auf das Unternehmensportal zu behalten.

|    Eigenschaft    |    Beschreibung    |    Beispiel    |
|-------------------------------|--------------------------------------------------------------------------------|----------------------------|
|    dateKey    |    Ein Schlüssel, der einem Datumswert in der Sammlung „dates“ entspricht.     |    20180823    |
|    userKey    |    Zuordnung eines Benutzerschlüssels zu einem Benutzer in der Sammlung „users“.     |    20000    |
|    termsAndConditionsKey    |    Ein Schlüssel, der einem Eintrag in der Sammlung „termsAndConditions“ entspricht.    |    1    |
|    acceptedDateTimeUTC    |    Der Zeitpunkt, zu dem der Benutzer diese Geschäftsbedingungen akzeptiert hat.    |    23.8.2018 4:01:34 Uhr    |
|    lastModifiedDateTimeUTC    |    Der Zeitpunkt, zu dem dieser Eintrag zuletzt geändert wurde.     |    23.8.2018 4:01:34 Uhr    |

## <a name="vppprogramtypes"></a>vppProgramTypes 
Die Entität **vppProgramType** führt mögliche VPP-Programmtypen für eine App auf.

|      Eigenschaft      |          Beschreibung         |
|:------------------:|:----------------------------:|
| VppProgramTypeID   | ID für den Typen.           |
| VppProgramTypeKey  | Ersatzschlüssel für den Schlüssel. |
| VppProgramTypeName | VPP-Programmtyp.          |

### <a name="example"></a>Beispiel

|             VppProgramID             |         Name        | Beschreibung                |
|:------------------------------------:|:-------------------:|----------------------------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft           | VPP-Programm von Microsoft. |
| 00000000-0000-0000-0000-000000000000 | Noch nicht verfügbar | Standardwert, kein VPP.   |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple               | VPP-Programm von Apple.     |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über das Intune Data Warehouse finden Sie unter [Datenmodell von Data Warehouse](https://docs.microsoft.com/intune/reports-ref-data-model).

