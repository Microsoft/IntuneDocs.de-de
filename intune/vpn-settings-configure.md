---
title: Erstellen von VPN-Geräteprofilen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Rufen Sie für iOS-Geräte die Verbindungstypen für virtuelle private Netzwerke (VPN) ab, erstellen Sie ein VPN-Geräteprofil im Azure-Portal, und rufen Sie Ihre Optionen ab, um Ihr VPN-Profil mit Zertifikaten bzw. mit einem Benutzernamen und einem Kennwort in Microsoft Intune zu sichern.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0588d3e01994092ca48a8a3bb4844883f7a5b100
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57235343"
---
# <a name="create-vpn-profiles-in-intune"></a>Erstellen von VPN-Profilen in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Virtuelle private Netzwerke (virtual private networks, VPNs) bieten Ihren Benutzern sicheren Remotezugriff auf Ihr Unternehmensnetzwerk. Geräte verwenden ein VPN-Verbindungsprofil, um eine Verbindung mit dem VPN-Server zu initiieren. **VPN-Profile** in Microsoft Intune ermöglichen Ihnen die Zuweisung von VPN-Einstellungen für Benutzer und Geräte in Ihrer Organisation, damit diese leicht eine sichere Verbindung zum Netzwerk herstellen können.

Nehmen Sie z. B. an, Sie möchten allen iOS-Geräten die Einstellungen zur Verfügung stellen, die zum Verbinden mit einer Dateifreigabe im Unternehmensnetzwerk erforderlich sind. Erstellen Sie ein VPN-Profil mit den Einstellungen, die zum Herstellen einer Verbindung mit dem Unternehmensnetzwerk erforderlich sind. Weisen Sie dieses Profil anschließend allen Benutzern zu, die über iOS-Geräte verfügen. Die Benutzer sehen die VPN-Verbindung in der Liste der verfügbaren Netzwerke und können mit geringem Aufwand eine Verbindung herstellen.

Sie können benutzerdefinierte Intune-Konfigurationsrichtlinien verwenden, um VPN-Profile für die folgenden Plattformen zu erstellen:

* Android 4 und höher
* Registrierte Geräte unter Windows 8.1 und höher
* Windows Phone 8.1 und höher
* Registrierte Geräte unter Windows 10 Desktop
* Windows 10 Mobile
* Windows Holographic for Business

## <a name="vpn-connection-types"></a>VPN-Verbindungstypen

Sie können VPN-Profile mit den folgenden Verbindungstypen erstellen:

|Verbindungstyp|Android<br>Android-Arbeitsprofile|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|Automatisch|Nein|Nein|Nein|Nein|Nein|Ja|
|Check Point Capsule VPN|Ja|Ja|Ja|Ja|Ja|Ja|
|Cisco AnyConnect|Ja|Ja|Ja|Nein|Nein|Nein|
|SonicWall Mobile Connect|Ja|Ja|Ja|Ja|Ja|Ja|
|F5 Edge Client|Ja|Ja|Ja|Ja|Ja|Ja|
|Palo Alto Networks GlobalProtect|Nein|Ja|Nein|Nein|Nein|Ja|
|Pulse Secure|Ja|Ja|Ja|Ja|Ja|Ja|
|Cisco (IPsec)|Nein|Ja|Nein|Nein|Nein|Nein|
|Citrix|Ja (nur Android)|Ja|Nein|Nein|Nein|Ja|
|IKEv2|Nein|Nein|Nein|Nein|Nein|Ja|
|L2TP|Nein|Nein|Nein|Nein|Nein|Ja|
|PPTP|Nein|Nein|Nein|Nein|Nein|Ja|
|Zscaler|Nein|Ja|Nein|Nein|Nein|Nein|
|Benutzerdefiniertes VPN|Nein|Ja|Ja|Nein|Nein|Nein|

> [!IMPORTANT]
> Vor der Verwendung von VPN-Profilen, die auf einem Gerät zugewiesen werden, müssen Sie die entsprechende VPN-App für das Profil installieren. Die Informationen im Artikel [Was ist die App-Verwaltung in Microsoft Intune?](app-management.md) unterstützen Sie beim Zuweisen der App mit Intune.  

Informationen zum Erstellen benutzerdefinierter VPN-Profile mithilfe von URI-Einstellungen finden Sie unter [Erstellen eines Profils mit benutzerdefinierten Einstellungen in Intune](custom-settings-configure.md).

## <a name="create-a-device-profile-containing-vpn-settings"></a>Erstellen eines Geräteprofils mit VPN-Einstellungen

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
4. Geben Sie einen **Namen** und eine **Beschreibung** für das VPN-Profil ein.
5. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform aus, auf die Sie VPN-Einstellungen anwenden möchten. Derzeit können Sie eine der folgenden Plattformen für die VPN-Geräteeinstellungen auswählen:
   - **Android**
   - **Android Enterprise**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 und höher**
   - **Windows 10 und höher**
6. Wählen Sie in der Dropdownliste **Profiltyp** die Option **VPN** aus.
7. Die konfigurierbaren Einstellungen variieren je nach der ausgewählten Plattform. In den folgenden Themen finden Sie ausführliche Informationen zu den Einstellungen für die einzelnen Plattformen:
   - [Einstellungen für Android und das Android-Arbeitsprofil](vpn-settings-android.md)
   - [Einstellungen für iOS](vpn-settings-ios.md)
   - [Einstellungen für macOS](vpn-settings-macos.md)
   - [Einstellungen für Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
   - [Einstellungen für Windows 8.1](vpn-settings-windows-8-1.md)
   - [Einstellungen für Windows 10](vpn-settings-windows-10.md) (einschließlich Windows Holographic for Business)
8. Wenn Sie fertig sind, **erstellen** Sie Ihr Profil.

Das Profil wird erstellt und in der Profilliste angezeigt. Informationen zur Zuweisung dieses Profils zu Gruppen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).

## <a name="methods-of-securing-vpn-profiles"></a>Methoden zum Schützen von VPN-Profilen

VPN-Profile können eine Reihe verschiedener Verbindungstypen und Protokolle von unterschiedlichen Herstellern verwenden. Diese Verbindungen werden in der Regel mit einer von zwei Methoden gesichert.

### <a name="certificates"></a>Zertifikate

Beim Erstellen des VPN-Profils wählen Sie ein SCEP- oder PKCS-Zertifikatprofil aus, das Sie zuvor in Intune erstellt haben. Dieses Profil wird als Identitätszertifikat bezeichnet. Es dient zur Authentifizierung anhand eines von Ihnen erstellten vertrauenswürdigen Zertifikatprofils (oder eines *Stammzertifikats*), das Sie erstellen, damit das Gerät des Benutzers eine Verbindung herstellen kann. Das vertrauenswürdige Zertifikat wird auf dem Computer zugewiesen, der die VPN-Verbindung authentifiziert, in der Regel ist dies der VPN-Server.

Weitere Informationen zum Erstellen und Verwenden von Zertifikatprofilen in Intune finden Sie unter [Konfigurieren von Zertifikaten mit Microsoft Intune](certificates-configure.md).

### <a name="user-name-and-password"></a>Benutzername und Kennwort

Der Benutzer authentifiziert sich beim VPN-Server durch Angabe seines Benutzernamens und Kennworts.
