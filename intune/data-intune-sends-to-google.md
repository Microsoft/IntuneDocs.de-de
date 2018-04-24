---
title: Von Intune an Google gesendete Daten
titleSuffix: Microsoft Intune
description: Liste der Daten, die von Intune an Google gesendet werden.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 78fef57849b8742bb10ece1717234af5cce3f4ba
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="data-intune-sends-to-google"></a>Von Intune an Google gesendete Daten

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Wenn die Android-Geräteverwaltung auf einem Gerät installiert ist, richtet Microsoft Intune eine Verbindung mit Google ein und versendet Benutzer- und Geräteinformationen an Google. Damit Microsoft Intune eine Verbindung einrichten kann, müssen Sie zunächst ein Google-Konto erstellen.

In der folgenden Tabelle sind die Daten aufgeführt, die Microsoft Intune an Google versendet, wenn auf einem Gerät die Geräteverwaltung aktiviert ist:


| An Google versendete Daten | Details | Verwendung | Beispiel |
|:---:|:---:|:---:|:---:|
| EnterpriseId | Wird beim Binden Ihres Gmail-Kontos an Intune in Google erzeugt. | Primärer Bezeichner für die Kommunikation zwischen Intune und Google.  Kommunikation bezieht sich hier auf das Erstellen von Richtlinien, das Verwalten von Geräten sowie die Bindung bzw. das Aufheben der Bindung zwischen Android Enterprise und Intune. | Eindeutiger Bezeichner, Beispiel für das Format: LC04eik8a6 |
| Richtlinientext | Wird in Intune beim Speichern einer neuen App- oder Konfigurationsrichtlinie erzeugt. | Anwendung von Richtlinien auf Geräte. | Hierbei handelt es sich um eine Sammlung aller konfigurierter Einstellungen für eine Anwendungs- oder Konfigurationsrichtlinie. Diese kann Kundeninformationen wie Netzwerknamen, Anwendungsnamen sowie anwendungsspezifische Einstellungen enthalten, sofern diese im Rahmen einer Richtlinie bereitgestellt werden. |
| Gerätedaten | Bei Geräten für Arbeitsprofilszenarios muss zunächst die Registrierung bei Intune durchgeführt werden. Bei Geräten für Szenarios mit verwalteten Geräten muss zunächst die Registrierung bei Google durchgeführt werden. | Gerätedaten werden für verschiedene Aktionen wie Anwenden von Richtlinien, Verwalten des Geräts und allgemeine Berichterstellungsaktionen zwischen Intune und Google versendet. | **Eindeutiger Bezeichner zur Darstellung des Gerätenamens.** Beispiel: enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**Eindeutiger Bezeichner zur Darstellung des Benutzernamens.** Beispiel: Enterprises/LC04ebru7b/users/116838519924207449711<br>**Gerätezustand.** Beispiele: Aktiv, deaktiviert, Bereitstellung.<br>**Konformitätszustände.** Beispiele: Einstellung wird nicht unterstützt, fehlende erforderliche Apps<br>**Softwareinformationen.** Beispiele: Softwareversionen und Patchebene.<br>**Netzwerkinformationen.** Beispiele: IMEI, MEID, WifiMacAddress<br>**Geräteeinstellungen.** Beispiele: Informationen zu Verschlüsselungsstufen und Informationen dazu, ob das Gerät unbekannte Apps zulässt.<br> Ein Beispiel einer JSON-Meldung finden Sie weiter unten. |
| newPassword | Wird in Intune erzeugt. | Zurücksetzen der Gerätekennung. | Zeichenfolge, die ein neues Kennwort darstellt. |
| Google-Benutzer | Google | Verwalten des Arbeitsprofils für Arbeitsprofilszenarios (BYOD). | Eindeutiger Bezeichner zur Darstellung des verknüpften Gmail-Kontos. Beispiel: 114223373813435875042 |
| Anwendungsdaten | Wird beim Speichern einer Anwendungsrichtlinie in Intune erzeugt. |  | Zeichenfolge eines Anwendungsnamens. Beispiel: app:com.microsoft.windowsintune.companyportal |
| Unternehmensdienstkonto | Wird auf Anforderung von Intune in Google erzeugt. | Wird zur Authentifizierung zwischen Intune und Google bei Transaktionen im Zusammenhang mit diesem Kunden verwendet. | Setzt sich aus verschiedenen Teilen zusammen:<br> **Unternehmens-ID**: bereits dokumentiert.<br>**UPN**: Generierter UPN, wird bei der Authentifizierung im Namen des Kunden verwendet.<br>Beispiel: w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**Schlüssel**: Base64-codierter Blob verwendet in Authentifizierungsanforderungen, verschlüsselt gespeichert im Dienst; der Blob sieht jedoch folgendermaßen aus:<br> Eindeutiger Bezeichner zur Darstellung des Schlüssels des Kunden<br>Beispiel: a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |

**Beispiel für Gerätedaten**

Im Folgenden finden Sie ein Beispiel für eine JSON-Gerätemeldung von Google:



```
'{
  "name": "enterprises/LC02dhxx1r/devices/3195483be017acdc",
  "userId": "114223373813435875042",
  "adminType": "DEVICE_OWNER",
  "state": "ACTIVE",
  "appliedState": "ACTIVE",
  "policyCompliant": true,
  "enrollmentTime": "2017-10-06T15:17:41.702Z",
  "lastStatusReportTime": "2017-10-06T15:18:10.325Z",
  "lastPolicyComplianceReportTime": "2017-10-06T15:18:11.665Z",
  "lastPolicySyncTime": "2017-10-06T15:18:07.852Z",
  "appliedPolicyVersion": "2",
  "apiLevel": 26,
  "enrollmentTokenData": "brew 30 day token",
  "enrollmentTokenId": "yXdtW0_0L7c7Yo9DtRhEfPi3PcMqTorF3V1bTAw_eRs",
  "softwareInfo": {
    "androidVersion": "8.0.0",
    "cloudDpcVersionCode": 55314,
    "cloudDpcVersionName": "bv00553-rc14",
    "androidBuildNumber": "OPR4.170623.009",
    "deviceKernelVersion": "3.10.73-ga51b1600b7f8",
    "bootloaderVersion": "BHZ21c",
    "androidBuildTime": "2017-08-28T18:57:48Z",
    "securityPatchLevel": "2017-10-05",
    "androidBuildType": "user",
    "buildUser": "android-build"
  },
  "hardwareInfo": {
    "brand": "google",
    "hardware": "bullhead",
    "deviceBasebandVersion": "M8994F-2.6.39.3.03",
    "manufacturer": "LGE",
    "serialNumber": "01ed07873b3c20cd",
    "model": "Nexus 5X",
    "batteryShutdownTemperatures": [60.0],
    "batteryThrottlingTemperatures": [-3.4028235E38],
    "cpuShutdownTemperatures": [115.0, 115.0, 115.0, 115.0, 115.0, 115.0],
    "cpuThrottlingTemperatures": [60.0, 60.0, 60.0, 60.0, 60.0, 60.0],
    "gpuShutdownTemperatures": [-3.4028235E38],
    "gpuThrottlingTemperatures": [-3.4028235E38],
    "skinShutdownTemperatures": [-3.4028235E38],
    "skinThrottlingTemperatures": [37.0]
  },
  "displays": [{
    "name": "Built-in Screen",
    "refreshRate": 60,
    "state": "ON",
    "width": 1080,
    "height": 1920,
    "density": 420
  }],
  "appliedPolicyName": "enterprises/LC02dhxx1r/policies/default",
  "networkInfo": {
    "imei": "353626070676775",
    "wifiMacAddress": "02:00:00:00:00:00"
  },
  "memoryInfo": {
    "totalRam": "1902936064",
    "totalInternalStorage": "3169611776"
  },
  "memoryEvents": [{
    "eventType": "EXTERNAL_STORAGE_DETECTED",
    "createTime": "2017-10-06T15:18:09.959Z",
    "byteCount": "26720919552"
  }],
  "powerManagementEvents": [{
    "eventType": "BATTERY_LEVEL_COLLECTED",
    "createTime": "2017-10-06T15:18:09.939Z",
    "batteryLevel": 95.0
  }],
  "userName": "enterprises/LC02dhxx1r/users/114223373813435875042",
  "enrollmentTokenName": "enterprises/LC02dhxx1r/enrollmentTokens/yXdtW0_0L7c7Yo9DtRhEfPi3PcMqTorF3V1bTAw_eRs"
}'
```

Wenn Sie die Android-Geräteverwaltung mit Microsoft Intune nicht mehr verwenden und die Daten löschen möchten, müssen Sie die Microsoft Intune Android-Geräteverwaltung und das Google-Konto löschen. Informationen zur Kontenverwaltung in der Dokumentation zum Google-Konto.


