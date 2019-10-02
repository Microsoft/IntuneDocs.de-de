---
title: Vorbereitung von Intune für die Verwaltung mobiler Geräte (MDM)
titleSuffix: Microsoft Intune
description: Wägen Sie Ihre geschäftlichen und technischen Anforderungen ab, bevor Sie zu Microsoft Intune migrieren.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 29ae889e99a843a8569782bad2b1303c7bb4304c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727479"
---
# <a name="phase-1-prepare-microsoft-intune-for-mobile-device-management-mdm"></a>Phase 1: Vorbereitung von Microsoft Intune für die mobile Geräteverwaltung (MDM)

Bevor wir uns mit den Details zum Einrichten von Intune befassen, werfen wir einen Blick auf die Anforderungen Ihres Unternehmens an die Verwaltung mobiler Geräte. Es kann hilfreich sein, Berichte aktiver Benutzer in Ihrem aktuellen MDM-Anbieter auszuführen, um die wichtigen Benutzergruppen zu identifizieren. Dann können Sie beginnen, die Fragen im Abschnitt [Einschätzen von MDM-Anforderungen](migration-guide-prepare.md#assess-mdm-requirements) zu beantworten.

## <a name="assess-mdm-requirements"></a>Einschätzen von MDM-Anforderungen

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>Welche Arten von Geräten müssen Sie verwalten?

- Welche [Plattformen](supported-devices-browsers.md) müssen Sie unterstützen?

- Handelt es sich bei den Geräten, die unterstützt werden müssen, um unternehmenseigene oder BYOD-Geräte?

- Welche Art von Verbindung verwenden Sie? WLAN, Mobiltelefone, VPN?

### <a name="what-do-your-users-need-to-do-on-managed-devices"></a>Was müssen die Benutzer auf den verwalteten Geräten tun?

- Müssen Sie den Endbenutzern Apps bereitstellen?

- Verwenden Sie benutzerdefinierte, branchenspezifische Apps? Oder benötigen Sie nur öffentliche Store-Apps?

- Müssen Sie E-Mail-Konten bereitstellen?

### <a name="what-kinds-of-users"></a>Um welche Arten von Benutzern handelt es sich?

- Wie viele Benutzer werden ein einzelnes Gerät verwenden?

- Welche Nutzungsbedingungen benötigen Sie?

  - Stellen Sie sicher, dass Sie Ihre Rechtsabteilung frühzeitig heranziehen.
  - Welche Lokalisierung ist erforderlich?

- Sind die Benutzer mit Technologie und IT im Allgemeinen vertraut?

### <a name="what-is-your-device-security-policy"></a>Welche Sicherheitsrichtlinie für Geräte haben Sie?

- Ist Verschlüsselung auf Geräteebene erforderlich?

- Wie ist die Länge Ihres aktuellen Kennworts/PIN-Codes?

- Müssen Sie Gerätefunktionen deaktivieren oder bestimmtes Geräteverhalten einschränken? Sie können eine Reihe von plattformspezifischen Einstellungen mit Konfigurationsprofilen für Geräte steuern, z.B.:
  - Deaktivieren der Kamera
  - Einzelanwendungsmodus zulassen<br/>

- Welche Arten von Authentifizierung müssen Sie unterstützen? Welche Zertifikate müssen bereitgestellt werden, wenn Sie zertifikatbasierte Authentifizierung benötigen?
  - Intune kann Zertifikate mit Ressourcenzugriffsprofilen für registrierte Geräte bereitstellen.
  - Welche Art von Public Key-Infrastruktur (PKI) müssen Sie unterstützen?
  <br></br>
- Müssen Sie virtuelles privates Netzwerk (VPN) auf Geräte- oder App-Ebene unterstützen?

  - Intune kann VPN-Konfigurationen für VPN-Drittanbieter bereitstellen.
  <br/><br/>
- Können vorübergehende Ausnahmen für bestimmte Anforderungen gemacht werden, um Ausfallzeiten zu vermeiden? Oder müssen Geräte mit Zugriff immer alle Sicherheitsanforderungen erfüllen?

## <a name="next-steps"></a>Nächste Schritte
Lesen Sie diese [Fallstudien](https://customers.microsoft.com/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune) aus verschiedenen Branchen, die Ihnen zeigen, wie Organisationen ihre Anforderungen an die Verwaltung mobiler Geräte eingeschätzt haben.

Überprüfen Sie die [einfache Einrichtung von Intune](migration-guide-setup.md).
