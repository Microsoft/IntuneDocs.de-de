---
title: Bei der Apple-Benutzerregistrierung unterstützte Intune-Aktionen und -Optionen
titleSuffix: Microsoft Intune
description: Erfahren Sie, welche Intune-Aktionen und -Optionen bei der Apple-Benutzerregistrierung unterstützt werden.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e23e582a853f0b424296d8fb42f6c7d8fdd2984c
ms.sourcegitcommit: 0d9e1452fcf5f15a80230838f80a427b9951cdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2019
ms.locfileid: "75324864"
---
# <a name="intune-actions-and-options-supported-with-apple-user-enrollment"></a>Bei der Apple-Benutzerregistrierung unterstützte Intune-Aktionen und -Optionen

Die Benutzerregistrierung unterstützt eine Teilmenge der Optionen für die Geräteverwaltung. Wenn ein bereits bestehendes Konfigurationsprofil auf ein Benutzerregistrierungsgerät angewendet wird, werden nur die von der Benutzerregistrierung unterstützten Einstellungen auf dieses Gerät angewendet.

> [!NOTE]
> Die Unterstützung für die Apple-Benutzerregistrierung in Intune befindet sich derzeit in der Vorschauphase.

## <a name="password-settings"></a>Kennworteinstellungen

Wenn Sie auf Geräten zur Benutzerregistrierung eine Kennworteinstellung konfigurieren, wird die Einstellung **Einfache Kennwörter** automatisch auf **Blockieren** festgelegt und eine sechsstellige PIN erzwungen.

Sie konfigurieren beispielsweise die Einstellung **Kennwortablauf** und übertragen diese Richtlinie per Push auf vom Benutzer registrierte Geräte. Auf diesen Geräten geschieht Folgendes:
- Die Einstellung **Kennwortablauf** wird ignoriert.
- Einfache Passwörter wie `111111` oder `123456` sind nicht zulässig.
- Eine sechsstellige PIN wird erzwungen.

## <a name="administrator-remote-device-actions-and-options"></a>Aktionen und Optionen für Administratoren auf Remotegeräten
Für Administratoren sind auf Geräten zur Benutzerregistrierung die folgenden Aktionen und Optionen möglich:
- Außerkraftsetzen
- Löschen
- Remotesperre
- Sync

Alle anderen Aktionen werden nicht unterstützt.

## <a name="end-user-actions"></a>Endbenutzeraktionen
Auf Geräten zur Benutzerregistrierung können Endbenutzer über die Anwendung und Website „Unternehmensportal“ diese Aktionen auf ihren Geräten durchführen:
- Umbenennen. Diese Aktion gilt nur innerhalb des Unternehmensportals für den dem Benutzer angezeigten Namen. Das Gerät wird außerhalb dieses Kontexts nicht vollständig umbenannt.
- Entfernen
- Remotesperre
- Status überprüfen

## <a name="app-deployment-options"></a>App-Bereitstellungsoptionen
Folgende App-Typen können auf Geräten mit Benutzerregistrierung bereitgestellt werden:
- Vom Benutzer lizenzierte VPP-Apps (Volume Purchase Plan) einschließlich benutzerdefinierter Apps
- Branchenspezifische Apps
- Web-Apps

## <a name="other-supported-options"></a>Weitere unterstützte Optionen

Die folgenden Optionen werden in Intune für Geräte unterstützt, die mit der Apple-Benutzerregistrierung registriert wurden:
- VPN für App. Diese Unterstützung schließt Safari-Domänen aus, da die Benutzerregistrierung die Konfiguration von Safari-Einstellungen nicht unterstützt.
- WLAN 
- Entfernen von Unternehmens-Apps bei Aufhebung der Registrierung
- Erkennung von Jailbreaks

Die folgenden Einschränkungen werden unterstützt:
- Anzeigen von Unternehmensdokumenten in nicht verwalteten Apps
- Anzeigen nicht unternehmenseigener Dokumente in Unternehmens-Apps
- Lesen aus verwalteten Kontaktkonten für nicht verwaltete Apps zulassen
- AirDrop als nicht verwaltetes Ziel behandeln
- Verschlüsselte Sicherung erforderlich
- Synchronisierung verwalteter Apps mit der Cloud
- Kontrollcenterzugriff bei gesperrtem Gerät
- Zugriff auf Mitteilungszentrale bei gesperrtem Gerät
- Ansicht „Heute“ bei Gerätesperre
- Screenshots blockieren
- Enterprise Book-Sicherung blockieren
- Synchronisierung von Enterprise Book-Metadaten blockieren
- Verschlüsselte Sicherung erforderlich
- Handgelenkerkennung für Apple Watch erforderlich
- Siri blockieren
- Siri bei gesperrtem Gerät blockieren
- Safari-Betrugswarnungen erforderlich
- Diagnoseübermittlung an Apple blockieren


## <a name="options-not-supported"></a>Nicht unterstützte Optionen
Die folgenden Optionen werden auf Geräten, die bei der Benutzerregistrierung registriert sind, nicht unterstützt. Wenn Sie diese Optionen benötigen, informieren Sie sich über die Geräteregistrierung für benutzereigene Geräte oder die automatisierte Geräteregistrierung für Unternehmensgeräte.
- Erfassen Sie den Bestand an Apps außerhalb des verwalteten APFS-Volumes.
- Erfassen Sie den Bestand an Zertifikaten und Bereitstellungsprofilen außerhalb des verwalteten APFS-Volumes.
- Erfassen Sie die UDID und andere persistente Gerätebezeichner.
- Die Benutzerregistrierung unterstützt für jedes registrierte Gerät eine eindeutige Registrierungs-ID, die jedoch nach Aufhebung der Registrierung nicht beibehalten wird.
- Die folgenden Intune-Features werden aufgrund dieser Einschränkung nicht unterstützt:
- SCEP-Benutzerprofile mit „Seriennummer“ als „Format des Antragstellernamens“.
- VPN auf Geräteebene.
- Für Geräte lizenzierte VPP-App-Bereitstellung.
- Installieren Sie App Store-Apps als verwaltete Apps.
- MDM-Steuerung von Anwendungen außerhalb des verwalteten APFS-Volumes.
- Für diese Apps gelten weiterhin Anwendungsschutzrichtlinien. Sie können jedoch nicht die Verwaltung oder Bereitstellung einer verwalteten Version dieser Anwendungen übernehmen, es sei denn, der Benutzer löscht sie von seinem Gerät.
- Aktionen, Konfigurationen, Einstellungen und Befehle, die eine Überwachung erfordern. 

## <a name="options-not-supported-in-preview"></a>In der Vorschauversion nicht unterstützte Optionen
- Registrierungsbeschränkungen von Gerätetypen zum Zulassen/Blockieren von persönlichen Geräten 

## <a name="known-issues-in-preview"></a>Bekannte Probleme in der Vorschauversion
- VPP-Lizenzsperrung: Es wird keine Benachrichtigung angezeigt, dass die Lizenz widerrufen wurde. Das aktuelle Verhalten ist, dass die Sperrung erfolgreich war, der Endbenutzer aber nicht benachrichtigt wird. 
- VPP-Anwendungsberichterstattung: Im Bericht unter Client-Apps > Apps > [App-Name] > Geräteinstallationsstatus wird für VPP-Anwendungen, die auf von Benutzern registrierten Geräten bereitgestellt werden, eine Fehlermeldung generiert, selbst wenn die Anwendung erfolgreich auf dem Gerät bereitgestellt wurde. 
- Anwendungsberichterstattung: Bei App-Typen, die bei der Benutzerregistrierung nicht unterstützt werden, können in Berichten irrelevante Fehlermeldungen auftreten. 
- Benutzeroberfläche der Unternehmensportal-App: Benutzern werden alle ihre Apps angezeigt, unabhängig davon, ob diese Anwendungstypen für von Benutzern registrierte Geräte unterstützt werden. 
- Benutzeroberfläche der Unternehmensportal-App: Benutzern wird derselbe Text angezeigt, der angibt, was Organisationen bei der Benutzer- und Geräteregistrierung sehen können.
- Wenn ein Benutzer während der Registrierung „My organization owns this device“ (Meine Organisation besitzt dieses Gerät) auswählt, wird das Gerät in Intune weiterhin als „Persönlich“ gekennzeichnet, es sei denn, es wurde in der Verwaltungskonsole oder über einen Graphen anderweitig geändert. 
- Registrierungsziel: iPadOS ist nicht in der Plattformauswahl aufgeführt. iPadOS wird in der Vorschauversion unterstützt, aber nicht explizit in der Verwaltungskonsole angegeben. 


## <a name="next-steps"></a>Nächste Schritte

[Einrichten der iOS- und iPadOS-Benutzerregistrierung](ios-user-enrollment.md)
