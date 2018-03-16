---
title: Konfigurieren von VPN-Einstellungen in Microsoft Intune
titleSuffix: 
description: "Erfahren Sie, wie Sie mit Microsoft Intune VPN-Einstellungen (virtuelles privates Netzwerk) auf Geräten konfigurieren, die Sie verwalten."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/25/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: feba7e7dc3e88d7d9beefc548c20bf19fbba662d
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-configure-vpn-settings-in-microsoft-intune"></a>Konfigurieren von VPN-Einstellungen in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Virtuelle private Netzwerke (virtual private networks, VPNs) bieten Ihren Benutzern sicheren Remotezugriff auf Ihr Unternehmensnetzwerk. Geräte verwenden ein VPN-Verbindungsprofil, um eine Verbindung mit dem VPN-Server zu initiieren. **VPN-Profile** in Microsoft Intune ermöglichen Ihnen die Zuweisung von VPN-Einstellungen für Benutzer und Geräte in Ihrer Organisation, damit diese leicht eine sichere Verbindung zum Netzwerk herstellen können.

Nehmen Sie z. B. an, Sie möchten allen iOS-Geräten die Einstellungen zur Verfügung stellen, die zum Verbinden mit einer Dateifreigabe im Unternehmensnetzwerk erforderlich sind. Sie erstellen ein VPN-Profil mit den Einstellungen, die zum Herstellen einer Verbindung mit dem Unternehmensnetzwerk erforderlich sind, und weisen dieses Profil dann allen Benutzern mit iOS-Geräten zu. Die Benutzer sehen die VPN-Verbindung in der Liste der verfügbaren Netzwerke und können mit geringem Aufwand eine Verbindung herstellen.

## <a name="vpn-connection-types"></a>VPN-Verbindungstypen

Sie können VPN-Profile mit den folgenden Verbindungstypen erstellen:

|Verbindungstyp|Android<br>Android for Work|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|Pulse Secure|Ja |Ja |Ja |Ja |Ja |Ja |
|Cisco (IPsec)|Nein|Ja |Nein|Nein|Nein|Nein|
|Citrix|Ja |Ja |Nein|Nein|Nein|Ja |
|F5 Edge Client|Ja |Ja |Ja |Ja |Ja |Ja |
|Dell SonicWALL Mobile Connect|Ja |Ja |Ja |Ja |Ja |Ja |
|Check Point Capsule VPN|Ja |Ja |Ja |Ja |Ja |Ja |
|Cisco AnyConnect|Ja |Ja |Ja |Nein|Nein|Nein|
|Automatisch|Nein|Nein|Nein|Nein|Nein|Ja |
|IKEv2|Nein|Nein|Nein|Nein|Nein|Ja |
|L2TP|Nein|Nein|Nein|Nein|Nein|Ja |
|PPTP|Nein|Nein|Nein|Nein|Nein|Ja |
|Benutzerdefiniert|Nein|Ja |Ja |Nein|Nein|Nein|


> [!IMPORTANT]
> Vor der Verwendung von VPN-Profilen, die auf einem Gerät zugewiesen werden, müssen Sie die entsprechende VPN-App für das Profil installieren. Die Informationen im Artikel [Was ist die App-Verwaltung in Microsoft Intune?](app-management.md) unterstützen Sie beim Zuweisen der App mit Intune.  

Informationen zum Erstellen benutzerdefinierter VPN-Profile mithilfe von URI-Einstellungen finden Sie unter [Erstellen benutzerdefinierter VPN-Profile](custom-vpn-profiles-create.md).     

## <a name="create-a-device-profile-containing-vpn-settings"></a>Erstellen eines Geräteprofils mit VPN-Einstellungen

1. Melden Sie sich beim Azure-Portal an.
2. Wählen Sie **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus.
3. Wählen Sie auf dem Blatt **Intune** die Option **Gerätekonfiguration** aus.
2. Wählen Sie auf dem Blatt **Gerätekonfiguration** die Option **Verwalten** > **Profile** aus.
3. Wählen Sie auf dem Blatt „Profile“ die Option **Profil erstellen** aus.
4. Geben Sie auf dem Blatt **Profil erstellen** einen **Namen** und eine **Beschreibung** für das VPN-Profil ein.
5. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform aus, auf die Sie VPN-Einstellungen anwenden möchten. Derzeit können Sie eine der folgenden Plattformen für die VPN-Geräteeinstellungen auswählen:
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 und höher**
    - **Windows 10 und höher**
6. Wählen Sie in der Dropdownliste **Profiltyp** die Option **VPN** aus.
7. Die konfigurierbaren Einstellungen variieren je nach der ausgewählten Plattform. In den folgenden Themen finden Sie ausführliche Informationen zu den Einstellungen für die einzelnen Plattformen:
    - [Einstellungen für Android und Android for Work](vpn-settings-android.md)
    - [Einstellungen für iOS](vpn-settings-ios.md)
    - [Einstellungen für macOS](vpn-settings-macos.md)
    - [Einstellungen für Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
    - [Einstellungen für Windows 8.1](vpn-settings-windows-8-1.md)
    - [Einstellungen für Windows 10](vpn-settings-windows-10.md) (einschließlich Windows Holographic for Business)
8. Navigieren Sie anschließend zurück zum Blatt **Profil erstellen**, und klicken Sie auf **Erstellen**.

Das Profil wird erstellt und auf dem Blatt mit der Profilliste angezeigt.
Wenn Sie fortfahren und dieses Profil Gruppen zuweisen möchten, lesen Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md) nach.


## <a name="methods-of-securing-vpn-profiles"></a>Methoden zum Schützen von VPN-Profilen

VPN-Profile können eine Reihe verschiedener Verbindungstypen und Protokolle von unterschiedlichen Herstellern verwenden. Diese Verbindungen werden in der Regel mit einer von zwei Methoden gesichert.

### <a name="certificates"></a>Zertifikate

Beim Erstellen des VPN-Profils wählen Sie ein SCEP- oder PKCS-Zertifikatprofil aus, das Sie zuvor in Intune erstellt haben. Dieses Profil wird als Identitätszertifikat bezeichnet. Es dient zur Authentifizierung anhand eines von Ihnen erstellten vertrauenswürdigen Zertifikatprofils (oder eines *Stammzertifikats*), mit dem überprüft wird, ob das Gerät des Benutzers eine Verbindung herstellen darf. Das vertrauenswürdige Zertifikat wird auf dem Computer zugewiesen, der die VPN-Verbindung authentifiziert, in der Regel ist dies der VPN-Server.

Weitere Informationen zum Erstellen und Verwenden von Zertifikatprofilen in Intune finden Sie unter [Konfigurieren von Zertifikaten mit Microsoft Intune](certificates-configure.md).

### <a name="user-name-and-password"></a>Benutzername und Kennwort

Der Benutzer authentifiziert sich beim VPN-Server durch Angabe seines Benutzernamens und Kennworts.
