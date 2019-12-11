---
title: Von Intune an Google gesendete Daten
titleSuffix: Microsoft Intune
description: Liste der Daten, die von Intune an Google gesendet werden.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f6ab8a4e8e46373a536949c13ceaebb267f34cd
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504452"
---
# <a name="data-intune-sends-to-google"></a>Von Intune an Google gesendete Daten

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Wenn die Android-Geräteverwaltung für Unternehmen auf einem Gerät installiert ist, richtet Microsoft Intune eine Verbindung mit Google ein und versendet Benutzer- und Geräteinformationen an Google. Damit Microsoft Intune eine Verbindung einrichten kann, müssen Sie zunächst ein Google-Konto erstellen.

In der folgenden Tabelle sind die Daten aufgeführt, die Microsoft Intune an Google versendet, wenn auf einem Gerät die Geräteverwaltung aktiviert ist:


| An Google versendete Daten | Details | Verwendet für | Beispiel |
|:---:|:---:|:---:|:---:|
| EnterpriseId | Wird beim Binden Ihres Gmail-Kontos an Intune in Google erzeugt. | Primärer Bezeichner für die Kommunikation zwischen Intune und Google.  Kommunikation bezieht sich hier auf das Erstellen von Richtlinien, das Verwalten von Geräten sowie die Bindung bzw. das Aufheben der Bindung zwischen Android Enterprise und Intune. | Eindeutiger Bezeichner, Beispiel für das Format: LC04eik8a6 |
| Richtlinientext | Wird in Intune beim Speichern einer neuen App- oder Konfigurationsrichtlinie erzeugt. | Anwendung von Richtlinien auf Geräte. | Hierbei handelt es sich um eine Sammlung aller konfigurierter Einstellungen für eine Anwendungs- oder Konfigurationsrichtlinie. Diese kann Kundeninformationen wie Netzwerknamen, Anwendungsnamen sowie anwendungsspezifische Einstellungen enthalten, sofern diese im Rahmen einer Richtlinie bereitgestellt werden. |
| Gerätedaten | Bei Geräten für Arbeitsprofilszenarios muss zunächst die Registrierung bei Intune durchgeführt werden. Bei Geräten für Szenarios mit verwalteten Geräten muss zunächst die Registrierung bei Google durchgeführt werden. | Gerätedaten werden für verschiedene Aktionen wie Anwenden von Richtlinien, Verwalten des Geräts und allgemeine Berichterstellungsaktionen zwischen Intune und Google versendet. | **Eindeutiger Bezeichner zur Darstellung des Gerätenamens.** Beispiel: enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**Eindeutiger Bezeichner zur Darstellung des Benutzernamens.** Beispiel: Enterprises/LC04ebru7b/users/116838519924207449711<br>**Gerätezustand.** Beispiele: Aktiv, deaktiviert, Bereitstellung.<br>**Konformitätszustände.** Beispiele: Einstellung wird nicht unterstützt, fehlende erforderliche Apps<br>**Softwareinformationen.** Beispiele: Softwareversionen und Patchebene.<br>**Netzwerkinformationen.** Beispiele: IMEI, MEID, WifiMacAddress<br>**Geräteeinstellungen.** Beispiele: Informationen zu Verschlüsselungsstufen und Informationen dazu, ob das Gerät unbekannte Apps zulässt.<br> Ein Beispiel einer JSON-Meldung finden Sie weiter unten. |
| newPassword | Wird in Intune erzeugt. | Zurücksetzen der Gerätekennung. | Zeichenfolge, die ein neues Kennwort darstellt. |
| Google-Benutzer | Google | Verwalten des Arbeitsprofils für Arbeitsprofilszenarios (BYOD). | Eindeutiger Bezeichner zur Darstellung des verknüpften Gmail-Kontos. Beispiel: 114223373813435875042 |
| Anwendungsdaten | Wird beim Speichern einer Anwendungsrichtlinie in Intune erzeugt. |  | Zeichenfolge eines Anwendungsnamens. Beispiel: app:com.microsoft.windowsintune.companyportal |
| Unternehmensdienstkonto | Wird auf Anforderung von Intune in Google erzeugt. | Wird zur Authentifizierung zwischen Intune und Google bei Transaktionen im Zusammenhang mit diesem Kunden verwendet. | Setzt sich aus verschiedenen Teilen zusammen:<br> **Unternehmens-ID**: bereits dokumentiert.<br>**UPN**: Generierter UPN, wird bei der Authentifizierung im Namen des Kunden verwendet.<br>Beispiel: w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**Schlüssel:** Base64-codierter Blob verwendet in Authentifizierungsanforderungen, verschlüsselt gespeichert im Dienst; der Blob sieht jedoch folgendermaßen aus:<br> Eindeutiger Bezeichner zur Darstellung des Schlüssels des Kunden<br>Beispiel: a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |


Wenn Sie die Android-Geräteverwaltung für Unternehmen mit Microsoft Intune nicht mehr verwenden und die Daten löschen möchten, müssen Sie die Microsoft Intune Android-Geräteverwaltung für Unternehmen und das Google-Konto löschen. Informationen zur Kontenverwaltung in der Dokumentation zum Google-Konto.


