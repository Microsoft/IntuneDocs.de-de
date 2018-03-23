---
title: Geräte – Intune Data Warehouse
titlesuffix: Microsoft Intune
description: Referenzthema für die Kategorie „Geräte“ der Entitätsauflistungen in der Intune Data Warehouse-API
keywords: Intune Data Warehouse
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d8a7aeba4170bf6640083b95562d644299693f31
ms.sourcegitcommit: 21db583d6a9d3c15a8a8ee5579309dff1cfe1f8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2018
---
# <a name="reference-for-devices-entities"></a>Referenz für Geräteentitäten

Die Kategorie **Geräte** (Devices) enthält Entitäten für mobile Geräte, die folgende Informationen nachverfolgen:

  -  Gerätetyp
  -  Status der Geräteregistrierung
  -  Gerätebesitz
  -  Status der Geräteverwaltung
  -  Status der Gerätemitgliedschaft bei Azure AD
  -  Anmeldungsstatus
  -  Informationen zur Geschichte des Geräts
  -  App-Inventar auf dem Gerät

## <a name="devicetypes"></a>DeviceTypes

Die Entität **DeviceTypes** stellt den Gerätetyp dar, auf den von anderen Data Warehouse-Entitäten verwiesen wird. Der Gerätetyp beschreibt in der Regel entweder das Gerätemodell, den Hersteller oder eine Kombination aus beidem.

| Eigenschaft  | Beschreibung |
|---------|------------|
| DeviceTypeID |Der eindeutige Bezeichner des Gerätetyps |
| DeviceTypeKey |Der eindeutige Bezeichner des Gerätetyps im Data Warehouse – Ersatzschlüssel |
| DeviceTypeName |Gerätetyp |

## <a name="example"></a>Beispiel

| deviceTypeID  | Name | Beschreibung |
|---------|------------|--------|
| 0 |desktop- |Windows Desktop-Gerät |
| 1 |WindowsRT |WindowsRT-Gerät |
| 2 |WinMO6 |Windows Mobile 6.0-Gerät |
| 3 |Nokia |Nokia-Gerät |
| 4 |WindowsPhone |Windows Phone-Gerät |
| 5 |Mac |Mac-Gerät |
| 6 |WinCE |Windows CE-Gerät |
| 7 |WinEmbedded |Windows Embedded-Gerät |
| 8 |IPhone |iPhone-Gerät |
| 9 |IPad |iPad-Gerät |
| 10 |IPod |iPod-Gerät |
| 11 |Android |Mit dem Geräteadministrator verwaltetes Android-Gerät |
| 12 |ISocConsumer |iSoc Consumer-Gerät |
| 14 |MacMDM |Mac OS X-Gerät, das mit dem integrierten MDM-Agent verwaltet wird |
| 15 |HoloLens |HoloLens-Gerät |
| 16 |SurfaceHub |Surface Hub-Gerät |
| 17 |AndroidForWork |Android-Gerät, das mit dem Android for Work-Profilbesitzer verwaltet wird |
| 100 |BlackBerry |Blackberry Device |
| 101 |Palm |Palm-Gerät |
| 255 |Unbekannt |Unbekannter Gerätetyp |

## <a name="clientregistrationstatetypes"></a>ClientRegistrationStateTypes

Die Entität **ClientRegistrationStateTypes** stellt den Registrierungstyp dar, auf den von anderen Data Warehouse-Tabellen verwiesen wird.

| Eigenschaft  | Beschreibung |
|---------|------------|
| clientRegisterationStateID |Der eindeutige Bezeichner für den Registrierungsstatus |
| clientRegisterationStateKey |Der eindeutige Bezeichner des Registrierungsstatus im Data Warehouse – Ersatzschlüssel |
| clientRegisterationStateName |Registrierungsstatus |

## <a name="example"></a>Beispiel

| ClientRegisterationStateID  | Name | Beschreibung |
|---------|------------|--------|
| 0 |NotRegistered |Nicht registriert |
| 1 |SMSIDConflict |SMS-ID-Konflikt |
| 2 |Registriert |Registriert |
| 3 |Revoked |Der Status bedeutet, dass der IT-Administrator den Client blockiert hat und der Client wieder freigegeben werden kann. Wenn ein Gerät zurückgesetzt oder außer Kraft gesetzt wurde, kann es auch den Status „Revoked“ anzeigen. |
| 4 |KeyConflict |Schlüsselkonflikt |
| 5 |ApprovalPending |Ausstehende Genehmigung |
| 6 |ResetCert |Zertifikat zurücksetzen |
| 7 |NotRegisteredPendingEnrollment |Nicht registriert, Registrierung ausstehend |
| 8 |Unbekannt |Unbekannter Status |

## <a name="enrollmenttypes"></a>EnrollmentTypes

Die Entität **EnrollmentTypes** gibt an, wie ein Gerät registriert wurde. Der Registrierungstyp erfasst die Registrierungsmethode. In den Beispielen werden die verschiedenen Registrierungstypen und ihre Bedeutung aufgelistet.

| Eigenschaft  | Beschreibung |
|---------|------------|
| managementStateID |Der eindeutige Bezeichner des Verwaltungsstatus |
| managementStateKey |Der eindeutige Bezeichner des Verwaltungsstatus im Data Warehouse – Ersatzschlüssel |
| managementStateName |Gibt den Status der Remoteaktion an, die auf dieses Gerät angewendet wurde |

## <a name="example"></a>Beispiel

| enrollmentTypeID  | Name | Beschreibung |
|---------|------------|--------|
| 0 |Unbekannt |Registrierungstyp wurde nicht gesammelt |
| 1 |UserEnrollment |Benutzer hat Registrierung initiiert |
| 2 |DeviceEnrollment |Geräteregistrierung mit Profil ohne Benutzer |
| 3 |DeviceEnrollmentWithUDA |Geräteregistrierung mit UDA-Profil |
| 4 |AzureDomainJoined |Benutzerinitiierte hat Geräteregistrierung über Azure Active Directory initiiert |
| 5 |UserEnrollmentWithServiceAccount |Benutzer hat Registrierung über Dienstkonto initiiert |
| 6 |DepDeviceEnrollment |DEP-Geräteregistrierung mit Profil ohne Benutzer initiiert |
| 7 |DepDeviceEnrollmentWithUDA |DEP-Geräteregistrierung mit UDA-Profil |
| 8 |AutoEnrollment |Kombinierte DRS- und MDM-Registrierung für BYOD-Szenario |

## <a name="ownertypes"></a>OwnerTypes

Die Entität **EnrollmentTypes** gibt an, ob ein Gerät einem Unternehmen oder einer Privatperson gehört oder ob der Besitzer unbekannt ist.

| Eigenschaft  | Beschreibung | Beispiel |
|---------|------------|--------|
| ownerTypeID |Eindeutiger Bezeichner des Besitzertyps | |
| ownerTypeKey |Eindeutige Bezeichner des Besitzertyps im Data Warehouse – Ersatzschlüssel | |
| ownerTypeName |Stellt den Besitzertypen der Geräte dar:  <br>Company (Unternehmen): das Gerät gehört einem Unternehmen <br>Personal (Privat): Das Gerät befindet sich im Privatbesitz (BYOD).  <br>Unknown (Unbekannt): Es liegen keine Informationen zu diesem Gerät vor. |Company, Personal, Unknown |

## <a name="mdmstatuses"></a>MdmStatuses

Die Entität **MdmStatuses** gibt den Konformitätszustand des Geräts an.

| Eigenschaft  | Beschreibung |
|---------|------------|
| MdmStatusID |Eindeutiger Bezeichner des Kompatibilitätszustands |
| MdmStatusKey |Der eindeutige Bezeichner des Konformitätszustands im Data Warehouse – Ersatzschlüssel | 
| ComplianceStatus |Der Kompatibilitätszustand des Geräts sollte einem der Werte aus der untenstehenden Tabelle entsprechen. | 


## <a name="example"></a>Beispiel

| MdmStatusID  | ComplianceStatus | Beschreibung |
|---------|------------|--------|
| 0 |Unbekannt |Der Kompatibilitätszustand des Geräts ist „Unbekannt“. |
| 1 |Kompatibel |Das Gerät ist kompatibel. |
| 2 |Nicht richtlinienkonform |Das Gerät ist nicht richtlinienkonform. |
| 3 |Conflict |Die Kompatibilität des Geräts hat einen Konflikt ausgelöst. |
| 4 |Fehler |Beim Lesen des Kompatibilitätszustands des Geräts ist ein Fehler aufgetreten. |


## <a name="managementstates"></a>ManagementStates

Die Entität **ManagementStates** stellt Details zum Status des Geräts bereit. Details können nützlich sein, wenn Remoteaktionen angewendet werden, das Gerät per Jailbreak oder Rootzugriff manipuliert wurde.

| Eigenschaft  | Beschreibung |
|---------|------------|
| managementStateID | Der eindeutige Bezeichner des Verwaltungsstatus |
| managementStateKey | Der eindeutige Bezeichner des Verwaltungsstatus im Data Warehouse – Ersatzschlüssel |
| managementStateName | Gibt den Status der Remoteaktion an, die auf dieses Gerät angewendet wurde |

## <a name="example"></a>Beispiel

| managementStateID  | Name | Beschreibung |
|---------|------------|--------|
| 0 |Verwaltet | Verwaltet, ohne ausstehende Remoteaktionen |
| 1 |RetirePending | Für das Gerät steht ein Befehl zum Außerkraftsetzen aus. |
| 2 |RetireFailed | Der Befehl zum Außerkraftsetzen konnte auf dem Gerät nicht ausgeführt werden. |
| 3 |WipePending | Für das Gerät steht ein Zurücksetzungsbefehl aus. |
| 4 |WipeFailed | Der Zurücksetzungsbefehl konnte auf dem Gerät nicht ausgeführt werden. |
| 5 |Unhealthy | Fehlerhafter Zustand |
| 6 |DeletePending | Für das Gerät steht ein Löschungsbefehl aus. |
| 7 |RetireIssued | Ein Befehl zum Außerkraftsetzen wurde an das Gerät ausgegeben. |
| 8 |WipeIssued | Ein Zurücksetzungsbefehl wurde ausgestellt. |
| 9 |WipeCanceled | Ein Zurücksetzungsbefehl wurde abgebrochen. |
| 10 |RetireCanceled | Ein Befehl zum Außerkraftsetzen wurde abgebrochen. |
| 11 |Discovered | Das Gerät wird von Intune neu ermittelt und erhält beim ersten Einchecken den Status „Managed“ (Verwaltet) |

## <a name="workplacejoinstatetypes"></a>WorkPlaceJoinStateTypes

Die Entität **WorkPlaceJoinStateTypes** stellt den Status des Azure Active Directory-Workplace Joins für das Gerät dar.  Der Registrierungsworkflow kann mit mindestens einem Zertifikat überprüfen oder authentifizieren. Wenn ein Gerät sich für einen Beitritt zum Arbeitsplatz registriert, werden diese Zertifikate verwendet, um das Gerät und den Benutzer zu überprüfen. Die Ausstellung von Zertifikaten wird über einen SCEP-Server (Simple Certificate Enrollment Point) bereitgestellt. Die Werte in der Entität geben verschiedene Zustände an, in denen sich ein Gerät während dieses Prozesses befinden kann. Diese Zustände gehören ein Fehlschlagen des Beitritts zum Arbeitsplatz aufgrund der Ausstellung eines erforderlichen Zertifikats (von einem SCEP-Server). Wenn ein Gerät diesen Workflow nie durchlaufen hat, wird der Wert zu auf „Unknown“ (Unbekannt) festgelegt.

| Eigenschaft  | Beschreibung |
|---------|------------|
| WorkPlaceJoinStateID | Der eindeutige Bezeichner des Status des Beitritts zum Arbeitsplatz |
| WorkPlaceJoinStateKey | Der eindeutige Bezeichner des Status des Beitritts zum Arbeitsplatz im Data Warehouse – Ersatzschlüssel |
| WorkPlaceJoinStateName | Status des Beitritts zum Arbeitsplatz |

## <a name="example"></a>Beispiel

| workPlaceJoinStateID  | Name | Beschreibung |
|---------|------------|--------|
| 0 |Unbekannt |Wenn ein Gerät nicht dem Arbeitsplatz beigetreten ist, ist sein Status „Unknown“. |
| 1 |Succeeded |Gerät wurde dem Arbeitsplatz erfolgreich hinzugefügt |
| 2 |FailureToGetScepMetadata |Fehler beim Abrufen der SCEP-Metadaten |
| 3 |FailureToGetScepChallenge |Fehler beim Abrufen der SCEP-Abfrage |
| 4 |DeviceFailureToInstallScepCommand |Fehler beim Installieren des SCEP-Befehls auf dem Gerät |
| 5 |DeviceFailureToGetCertificate |Gerät konnte das Zertifikat nicht über SCEP abrufen |
| 6 |DeviceScepPending |Status „Ausstehend“; Gerät führt noch SCEP aus |
| 7 |DeviceScepFailed |Gerät konnte das Zertifikat nicht über SCEP installieren |
| 8 |AADValidationFailed |Fehler beim Überprüfen, dass das Gerät auf AAD vorhanden ist |

## <a name="managementagenttypes"></a>ManagementAgentTypes

Die Entität **ManagementAgentTypes** stellt die Agents dar, die zum Verwalten von Geräten verwendet.

| Eigenschaft  | Beschreibung |
|---------|------------|
| ManagementAgentTypeID | Eindeutige Bezeichner des Verwaltungs-Agent-Typen |
| ManagementAgentTypeKey | Eindeutiger Bezeichner des Verwaltungs-Agent-Typen im Data Warehouse – Ersatzschlüssel |
| ManagementAgentTypeName |Gibt an, welche Art von Agent zum Verwalten des Geräts verwendet wird |

## <a name="example"></a>Beispiel

| ManagementAgentTypeID  | Name | Beschreibung |
|---------|------------|--------|
| 1 |EAS | Das Gerät wird mithilfe von Exchange Active Sync verwaltet. |
| 2 |MDM | Das Gerät wird mit einem MDM-Agent verwaltet. |
| 3 |EasMdm | Das Gerät wird sowohl von Exchange Active Sync als auch einem MDM-Agent verwaltet. |
| 4 |IntuneClient | Das Gerät wird vom Intune-PC-Agent verwaltet. |
| 5 |EasIntuneClient | Das Gerät wird sowohl von Exchange ActiveSync als auch vom Intune-PC-Agent verwaltet. |
| 8 |ConfigManagerClient | Das Gerät wird vom System Center Configuration Manager-Agent verwaltet. |
| 16 |Unbekannt | Unbekannter Typ von Verwaltungs-Agent |

## <a name="devices"></a>Geräte

In der Entität **Devices** werden alle für die Verwaltung registrierten Geräte und ihre entsprechenden Eigenschaften aufgelistet.

| Eigenschaft  | Beschreibung |
|---------|------------|
| DeviceKey | Der eindeutige Bezeichner des Geräts im Data Warehouse – Ersatzschlüssel. |
| DeviceId | Eindeutiger Bezeichner des Geräts |
| DeviceName | Der Name des Geräts auf Plattformen, die das Benennen von Geräten ermöglichen. Auf anderen Plattformen wird von Intune einen Namen aus anderen Eigenschaften erstellt. Dieses Attribut kann nicht für alle Geräte zur Verfügung stehen. |
| DeviceTypeKey | Schlüssel des Gerätetyp-Attributs für dieses Gerät |
| ClientRegisterationStateKey | Schlüssel des Attributs für den Clientregistrierungsstatus dieses Geräts |
| OwnerTypeKey | Schlüssel des Besitzertyp-Attributs für dieses Gerät: corporate (Unternehmen), personal (persönlich) oder unknown (unbekannt) |
| objectSourceKey | Ignorieren Sie diese Spalte. |
| CreatedDate | Datum, an dem das Gerät registriert wurde |
| LastContact | Letztes bekanntes Einchecken des Geräts mit Intune |
| LastContactNotification | Der letzte Zeitpunkt, zu dem Intune das Gerät aufgefordert hat, sich anzumelden |
| LastContactWorkplaceJoin | Der Zeitstempel, der den letzten bekannten Status des Beitritts zum Arbeitsplatz für dieses Gerät angibt |
| ManagementAgentKey | Der Schlüssel des Verwaltungs-Agents, der mit diesem Gerät verknüpft ist |
| ManagementStateKey | Der Schlüssel des Verwaltungsstatus, der mit diesem Gerät verknüpft ist und den neuesten Zustand einer Remoteaktion angibt oder anzeigt, ob das Gerät per Jailbreak oder Rootzugriff manipuliert wurde |
| ReferenceId | Die ID des Geräts in Azure Active Directory |
| WorkPlaceJoinStateKey | Der Schlüssel des Status des Beitritts zum Arbeitsplatz, der mit diesem Gerät verknüpft ist |
| CategoryId | Ignorieren Sie diese Spalte. |
| EnrollmentTypeKey | Der Schlüssel des der Registrierungstyps, der mit diesem Gerät verknüpft ist und die Registrierungsmethode angibt. |
| CertExpirationDate | Das Ablaufdatum des MDM-Verwaltungszertifikats |
| MdmStatusKey | Ein Schlüssel zum MdmStatus |
| OSFamily | Familie des Betriebssystems (Windows, iOS, Android usw.) |
| OSVersion | BS-Version |
| OSMajorVersion | Komponente der Hauptversion der Betriebssystemversion (major.minor.build.revision) |
| OSMinorVersion | Komponente der Nebenversion der Betriebssystemversion (major.minor.build.revision) |
| OSBuildNumber | Komponente der Buildversion der Betriebssystemversion (major.minor.build.revision) |
| OSRevisionNumber | Komponente der Revisionsversion der Betriebssystemversion (major.minor.build.revision) |
| EasID | Diese EAS-ID des Geräts, wenn das Gerät von Exchange Active Sync verwaltet wird |
| GraphDeviceIsManaged | Der letzte Verwaltungsstatus, den Intune in Azure AD festgelegt hat |
| GraphDeviceIsCompliant | Der letzte Konformitätszustand, den Intune in Azure AD festgelegt hat |
| SerialNumber | Die Seriennummer des Geräts, falls verfügbar |
| EnrolledByUser | Die ID des Benutzers, der dieses Gerät registriert hat, das auf die „userId“-Spalte in der „User“-Tabelle verweist |
| RowLastModifiedDateTimeUTC | Der letzte Zeitpunkt, an dem der Datensatz geändert wurde |
| ProcessorArchitecture | Prozessorarchitektur |
| DeviceAction | Die letzte ausgestellte Geräteaktion, vorläufig ignorieren |
| Hersteller | Hersteller des Geräts |
| Modell | Gerätemodell |
| LastPolicyUpdateUtc | Der letzte Zeitpunkt, zu dem die Richtlinie auf dem Gerät aktualisiert wurde |
| LastExchangeStatusUtc | Der letzte Zeitpunkt, an dem das Gerät mit Exchange synchronisiert wurde |
| isDeleted | Legen Sie diesen Wert auf TRUE fest, wenn das Gerät nicht mehr von Intune verwaltet wird. Dadurch wird der letzte bekannte Zustand beibehalten. |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

Die Entität **DevicePropertyHistory** hat die gleichen Eigenschaften wie die Gerätetabellen und die täglichen Momentaufnahmen der einzelnen Gerätedatensätze pro Tag für die letzten 90 Tage. Die DateKey-Spalte gibt den Tag für jede Zeile an.

| Eigenschaft  | Beschreibung |
|---------|------------|
| DateKey |Verweis auf die Datumstabelle, die den Tag angibt |
| DeviceKey |Der eindeutige Bezeichner des Geräts im Data Warehouse – Ersatzschlüssel. Dies ist ein Verweis auf die Gerätetabelle, die die Intune-Geräte-ID enthält. |
| DeviceName |Der Name des Geräts auf Plattformen, die das Benennen von Geräten ermöglichen. Auf anderen Plattformen wird von Intune einen Namen aus anderen Eigenschaften erstellt. Dieses Attribut kann nicht für alle Geräte zur Verfügung stehen. |
| DeviceTypeKey |Schlüssel des Gerätetyp-Attributs für dieses Gerät |
| ClientRegisterationStateKey |Schlüssel des Attributs für den Clientregistrierungsstatus dieses Geräts |
| OwnerTypeKey |Schlüssel des Besitzertyp-Attributs für dieses Gerät: corporate (Unternehmen), personal (persönlich) oder unknown (unbekannt) |
| objectSourceKey |Ignorieren Sie diese Spalte. |
| CreatedDate |Datum, an dem das Gerät registriert wurde |
| LastContact |Letztes bekanntes Einchecken des Geräts mit Intune |
| LastContactNotification |Der letzte Zeitpunkt, zu dem Intune das Gerät aufgefordert hat, sich anzumelden |
| LastContactWorkplaceJoin |Der Zeitstempel, der den letzten bekannten Status des Beitritts zum Arbeitsplatz für dieses Gerät angibt |
| ManagementAgentKey |Der Schlüssel des Verwaltungs-Agents, der mit diesem Gerät verknüpft ist |
| ManagementStateKey |Der Schlüssel des Verwaltungsstatus, der mit diesem Gerät verknüpft ist und den neuesten Zustand einer Remoteaktion angibt oder anzeigt, ob das Gerät per Jailbreak oder Rootzugriff manipuliert wurde |
| ReferenceId |Die ID des Geräts in Azure Active Directory |
| WorkPlaceJoinStateKey |Der Schlüssel des Status des Beitritts zum Arbeitsplatz, der mit diesem Gerät verknüpft ist |
| CategoryId |Ignorieren Sie diese Spalte. |
| EnrollmentTypeKey |Der Schlüssel des der Registrierungstyps, der mit diesem Gerät verknüpft ist und die Registrierungsmethode angibt. |
| CertExpirationDate |Das Ablaufdatum des MDM-Verwaltungszertifikats |
| MdmStatusKey |Ein Schlüssel zum MdmStatus |
| OSFamily |Familie des Betriebssystems (Windows, iOS, Android usw.) |
| OSVersion |Betriebssystemversion |
| OSMajorVersion |Komponente der Hauptversion der Betriebssystemversion (major.minor.build.revision) |
| OSMinorVersion |Komponente der Nebenversion der Betriebssystemversion (major.minor.build.revision) |
| OSBuildNumber |Komponente der Buildversion der Betriebssystemversion (major.minor.build.revision) |
| OSRevisionNumber |Komponente der Revisionsversion der Betriebssystemversion (major.minor.build.revision) |
| EasID |Diese EAS-ID des Geräts, wenn das Gerät von Exchange Active Sync verwaltet wird |
| GraphDeviceIsManaged |Der letzte Verwaltungsstatus, den Intune in Azure AD festgelegt hat |
| GraphDeviceIsCompliant |Der letzte Konformitätszustand, den Intune in Azure AD festgelegt hat |
| SerialNumber |Die Seriennummer des Geräts, falls verfügbar |
| EnrolledByUser |Die ID des Benutzers, der dieses Gerät registriert hat, das auf die „userId“-Spalte in der „User“-Tabelle verweist |
| RowLastModifiedDateTimeUTC |Der letzte Zeitpunkt, an dem der Datensatz geändert wurde |
| ProcessorArchitecture |Prozessorarchitektur |
| DeviceAction |Die letzte ausgestellte Geräteaktion, vorläufig ignorieren |
| Hersteller |Hersteller des Geräts |
| Modell |Gerätemodell |
| LastPolicyUpdateUtc |Der letzte Zeitpunkt, zu dem die Richtlinie auf dem Gerät aktualisiert wurde |
| LastExchangeStatusUtc |Der letzte Zeitpunkt, an dem das Gerät mit Exchange synchronisiert wurde |

## <a name="mdmdeviceinventoryhistories"></a>MdmDeviceInventoryHistories

Die Entität **MdmDeviceInventoryHistories** enthält tägliche Momentaufnahmen von Inventardaten für mit MDM-verwaltete Geräte für die letzten 90 Tage. Die Spalte „DateKey“ gibt den Tag für die Zeile an. Einige Eigenschaften gelten möglicherweise nicht für alle Geräte oder werden nicht für alle Geräte befüllt. Lesen Sie daher diese Seite, wenn Sie weitere Informationen suchen. Weitere Informationen finden Sie unter [Verstehen Sie Ihre Geräte mithilfe des Inventars in Microsoft Intune](https://docs.microsoft.com/Intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-Intune).

| Eigenschaft  | Beschreibung |
|---------|------------|
| DateKey | Verweis auf die Datumstabelle, die den Tag angibt |
| DeviceKey |Der eindeutige Bezeichner des Geräts im Data Warehouse – Ersatzschlüssel. Dies ist ein Verweis auf die Gerätetabelle, die die Intune-Geräte-ID enthält. |
| DeviceModel |Gerätemodell |
| Betriebssystem |Betriebssystem des Geräts |
| DeviceName |Der Name des Geräts auf Plattformen, die das Benennen von Geräten ermöglichen. Auf anderen Plattformen wird von Intune einen Namen aus anderen Eigenschaften erstellt. Dieses Attribut kann nicht für alle Geräte zur Verfügung stehen. |
| SoftwareVersion |In den meisten Fällen ist dies die Betriebssystemversoin, außer auf Apple-Plattformen, die eine andere BS-Version haben. |
| Imei |IMEI-Nummer |
| HardwareInventoryTimeUtc |Das erste Mal, dass ein Inventar für dieses Gerät gemeldet wurde |
| InventoryModifiedTimeUtc |Das letzte Mal, als Inventar gespeichert wurde, als diese Momentaufnahme erstellt wurde |
| InventoryReportingTimeUtc |Das letzte Mal, dass ein Inventar für dieses Gerät erfasst wurde |
| ExchangeActiveSyncId |Geräte-ID von Exchange Active Sync |
| ComputerSystemDescription |Systembeschreibung |
| ComputerSystemName |Systemname |
| ComputerSystemManufacturer |Systemhersteller |
| ComputerSystemModel |Systemmodell |
| UserName |Benutzername |
| OSType |Betriebssystemtyp |
| OSCaption |Beschriftung des Betriebssystems |
| OSName |Name des Betriebssystems |
| OSManufacturer |Hersteller des Betriebssystems |
| OSProductSuite |Produktsuite des Betriebssystems |
| OSProductType |Produkttyp des Betriebssystems |
| Gebietsschema |Gebietsschema des Betriebssystems |
| PhysicalMemoryCapacity |Physische Speicherkapazität (in Byte) |
| PhysicalMemoryRemovable |Physischer Wechselspeicher (in Byte) |
| SystemEnclosureChassisTypesInnerText |Definiert den Typ des Systemchassis für dieses Gerät. Die Zahlen weisen auf die folgenden Werte hin:  <br>0 oder leer = unbekannt   <br>1 = Es handelt sich um einen Desktop   <br>2 = Es handelt sich um einen Laptop  <br>3 = Es handelt sich um eine Arbeitsstation  <br>4 = Es handelt sich um einen Enterprise Server  <br>100 = Es handelt sich um ein Smartphone  <br>101 = Es handelt sich um ein Tablet  <br>102/103 = Anderer unbekannter Typ eines Mobilgeräts |
| SystemEnclosureModel |Modell des Systemgehäuses |
| SystemEnclosureSerialNumber |Seriennummer des Systemgehäuses |
| NetworkAdapterConfigurationText |Konfigurationstext vom Netzwerkadapter |
| MacAddress |MAC-Adresse |
| SmsID |Intune-Geräte-ID |
| CertExpiry |Das Ablaufdatum des MDM-Verwaltungszertifikats |
| DeviceClientAgentVersion |Client-Agent-Version |
| DeviceClientID |Geräte-Client-ID |
| SerialNumber |Seriennummer |
| DeviceManufacturer |Gerätehersteller |
| DMVersion |DM-Version |
| FirmwareVersion |Firmwareversion |
| HardwareVersion |Hardwareversion |
| PlatformType |Plattformtyp |
| ProcessorLevel |Prozessorstufe |
| ProcessorRevision |Prozessorrevision |
| Produkt |Produkt |
| ProductVersion |Produktversion |
| OEM |Originalgerätehersteller |
| DeviceBuildVersion |Version des Gerätebuilds |
| Meid |Mobile Equipment Identifier |
| PhoneNumber |Telefonnummer |
| SubscriberCarrierNetwork |Netzwerkname des Telefonanbieters |
| CellularTechnology |Netzwerktyp des Telefonanbieters (CDMA/GSM) |
| Imsi |IMSI-Nummer |
| JailBroken |TRUE, wenn das Gerät per Jailbreak oder Rootzugriff manipuliert wurde |
| IsActivationLockEnabled |TRUE, wenn die Aktivierungssperre aktiviert ist |
| DeviceType |Gerätetyp |
| IsSupervised |Wird überwacht |
| DeviceDisplayNumberOfColors |Geräteanzeige, Anzahl von Farben |
| HorizontalResolution |Horizontale Bildschirmauflösung des Geräts |
| VerticalResolution |Vertikale Bildschirmauflösung des Geräts |
| StorageFree |Freier Speicherplatz (in Byte) |
| StorageTotal |Speicherplatz insgesamt (in Byte) |
| ProgramFree |Freier Programmspeicher (in Bytes) |
| ProgramTotal |Programmspeicher insgesamt (in Bytes) |
| RemovableStorageFree |Freien Speicherplatz auf Wechselmedien (in Bytes) |
| RemovableStorageTotal |Speicherplatz auf Wechselmedien insgesamt (in Bytes) |
| DeviceMemoryDeviceCapacity |Gerätespeicherkapazität |
| DeviceMemoryAvailableDeviceCapacity |Gerätespeicher, verfügbare Kapazität |
| DeviceOSVersion |Betriebssystemversion |
| DeviceOSPlatform |Betriebssystemplattform |
| DeviceOSLanguage |Sprache des Betriebssystems |
| PasswordMaxAttemptsBeforeWipe |Maximal zulässige Kennworteingaben, bevor das Gerät zurückgesetzt wird |
| PasswordMinComplexChars |Minimale Anzahl komplexer Zeichen, die das Kennwort enthalten muss |
| PasswordMinLength |Erforderliche Mindestlänge des Kennworts |
| PasswordHistory |Kennwort – Minimum vergangener Kennwörter, die nicht akzeptiert wurden |
| PasswordEnabled |Kennwort – aktiviert? |
| PasswordExpiration |Kennwort – Ablaufdatum |
| AllowRecoveryPassword |Kennwortwiederherstellung zulassen |
| PasswordAutoLockTimeout |Kennwort – automatisches Sperrtimeout |
| PasswordType |Kennworttyp |
| BacklightACTimeout |Timeout für das Gegenlicht, wenn es an die Stromquelle angeschlossen ist |
| BacklightBatTimeout |Timeout für das Gegenlicht bei Akkubetrieb |
| PowerBackupPercent |Stromsicherung in Prozent |
| BatteryPercent |Restlaufzeit des Akkus in Prozent |
| PlatformID |Plattform-ID |
| ExchangeDeviceID |Exchange-Geräte-ID |
| SmsProcessorDescription |Prozessorbeschreibung |
| OwnerEmailAddress |E-Mail-Adresse des Besitzers |
| DeviceOSName |Name des Betriebssystems |
| WifiMac |WLAN-MAC-Adresse |
| EthernetMac |Ethernet-MAC-Adresse |
| RequireEncryption |Gibt an, ob das Gerät verschlüsselt ist |
| ActivationLockBypassCode |Code zur Umgehung der Aktivierungssperre |

## <a name="applicationinventory"></a>ApplicationInventory

Die Entität **ApplicationInventory** listet die Apps auf, die zum Zeitpunkt der Inventursammlung auf dem Gerät gefunden wurden.

| Eigenschaft  | Beschreibung |
|---------|------------|
| DeviceKey |Ein Verweis auf die Gerätetabelle |
| ApplicationKey |? (kopiert aus ExchangeDeviceService\DeviceApplication) |
| ApplicationName |? (kopiert aus ExchangeDeviceService\DeviceApplication) |
| ApplicationVersion |? (kopiert aus ExchangeDeviceService\DeviceApplication) |
| BundleSize |? (kopiert aus ExchangeDeviceService\DeviceApplication) |
