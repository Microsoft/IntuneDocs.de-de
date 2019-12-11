---
title: Hinzufügen von VPN-Einstellungen für Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie für Android-, Android Enterprise-, iOS-, macOS- und Windows-Geräte integrierte Einstellungen zum Erstellen von VPN-Verbindungen (virtuelles privates Netzwerk) in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9fab50e0aefd926b4dc7a2b3559576642d5d6b79
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059308"
---
# <a name="create-vpn-profiles-to-connect-to-vpn-servers-in-intune"></a>Erstellen von VPN-Profilen zum Herstellen einer Verbindung mit VPN-Servern in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Über virtuelle private Netzwerke (VPNs) erhalten Ihre Benutzer sicheren Remotezugriff auf Ihr Organisationsnetzwerk. Mithilfe eines VPN-Verbindungsprofils stellen Geräte eine Verbindung mit dem VPN-Server her. **VPN-Profile** in Microsoft Intune ermöglichen Ihnen die Zuweisung von VPN-Einstellungen für Benutzer und Geräte in Ihrer Organisation, damit diese leicht eine sichere Verbindung zu Ihrem Organisationsnetzwerk herstellen können.

Angenommen, Sie möchten z. B. alle iOS-Geräte mit den Einstellungen konfigurieren, die zum Herstellen einer Verbindung mit einer Dateifreigabe im Organisationsnetzwerk erforderlich sind. Erstellen Sie zunächst ein VPN-Profil, das diese Einstellungen enthält. Weisen Sie dieses Profil anschließend allen Benutzern zu, die über iOS-Geräte verfügen. Die Benutzer sehen die VPN-Verbindung in der Liste der verfügbaren Netzwerke und können mit geringem Aufwand eine Verbindung herstellen.

> [!NOTE]
> Sie können [benutzerdefinierte Intune-Konfigurationsrichtlinien](custom-settings-configure.md) verwenden, um VPN-Profile für die folgenden Plattformen zu erstellen:
>
> * Android 4 und höher
> * Registrierte Geräte unter Windows 8.1 und höher
> * Windows Phone 8.1 und höher
> * Registrierte Geräte unter Windows 10 Desktop
> * Windows 10 Mobile
> * Windows Holographic for Business

## <a name="vpn-connection-types"></a>VPN-Verbindungstypen

Sie können VPN-Profile mit den folgenden Verbindungstypen erstellen:

|Verbindungstyp|Plattform|
|-|-|
|Automatisch|Windows 10|
|Check Point Capsule VPN|– Android<br/>– Android Enterprise-Arbeitsprofile<br/>– iOS<br/>– macOS<br/>– Windows 10<br/>– Windows 8.1<br/>– Windows Phone 8.1|
|Cisco AnyConnect|– Android<br/>– Android Enterprise-Arbeitsprofile<br/>– Android Enterprise-Gerätebesitzer (vollständig verwaltet)<br/>– iOS<br/>– macOS|
|Cisco (IPsec)|iOS|
|Citrix SSO|– Android<br/>– Android Enterprise-Arbeitsprofile: Verwenden von [App-Konfigurationsrichtlinien](../apps/app-configuration-policies-use-android.md)<br/>– Android Enterprise-Gerätebesitzer (vollständig verwaltet): Verwenden von [App-Konfigurationsrichtlinien](../apps/app-configuration-policies-use-android.md)<br/>– iOS<br/>– Windows 10|
|Benutzerdefiniertes VPN|– iOS<br/>– macOS|
|F5 Access|– Android<br/>– Android Enterprise-Arbeitsprofile<br/>– Android Enterprise-Gerätebesitzer (vollständig verwaltet)<br/>– iOS<br/>– macOS<br/>– Windows 10<br/>– Windows 8.1<br/>– Windows Phone 8.1|
|IKEv2| – iOS<br/>– Windows 10|
|L2TP|Windows 10|
|Palo Alto Networks GlobalProtect|– Android Enterprise-Arbeitsprofile: Verwenden von [App-Konfigurationsrichtlinien](../apps/app-configuration-policies-use-android.md)<br/>– iOS<br/>– Windows 10|
|PPTP|Windows 10|
|Pulse Secure|– Android<br/>– Android Enterprise-Arbeitsprofile<br/>– Android Enterprise-Gerätebesitzer (vollständig verwaltet)<br/>– iOS<br/>– macOS<br/>– Windows 10<br/>– Windows 8.1<br/>– Windows Phone 8.1|
|SonicWall Mobile Connect|– Android<br/>– Android Enterprise-Arbeitsprofile<br/>– iOS<br/>– macOS<br/>– Windows 10<br/>– Windows 8.1<br/>– Windows Phone 8.1|
|Zscaler|– Android Enterprise-Arbeitsprofile: Verwenden von [App-Konfigurationsrichtlinien](../apps/app-configuration-policies-use-android.md)<br/>– iOS|

> [!IMPORTANT]
> Vor der Verwendung von VPN-Profilen, die auf einem Gerät zugewiesen werden, müssen Sie die entsprechende VPN-App für das Profil installieren. Die Informationen im Artikel [Was ist die App-Verwaltung in Microsoft Intune?](../apps/app-management.md) unterstützen Sie beim Zuweisen der App mit Intune.  

Informationen zum Erstellen benutzerdefinierter VPN-Profile mithilfe von URI-Einstellungen finden Sie unter [Erstellen eines Profils mit benutzerdefinierten Einstellungen in Intune](custom-settings-configure.md).

## <a name="create-a-device-profile"></a>Erstellen eines Geräteprofils

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für das Profil ein. Benennen Sie Ihre Profile, damit Sie diese später leicht wiedererkennen. Ein geeigneter Profilname ist beispielsweise **VPN-Profil für das gesamte Unternehmen**.
    - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie die Plattform Ihrer Geräte aus. Folgende Optionen sind verfügbar:

      - **Android**
      - **Android Enterprise** > **Nur Gerätebesitzer**
      - **Android Enterprise** > **Nur Arbeitsprofil**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows Phone 8.1**
      - **Windows 8.1 und höher**
      - **Windows 10 und höher**

    - **Profiltyp**: Wählen Sie **VPN** aus.

4. Die konfigurierbaren Einstellungen variieren je nach der ausgewählten Plattform. In den folgenden Artikeln finden Sie ausführliche Informationen zu den Einstellungen auf den jeweiligen Plattformen:

    - [Einstellungen für Android](vpn-settings-android.md)
    - [Android Enterprise-Einstellungen](vpn-settings-android-enterprise.md)
    - [iOS/iPadOS-Einstellungen](vpn-settings-ios.md)
    - [Einstellungen für macOS](vpn-settings-macos.md)
    - [Einstellungen für Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
    - [Einstellungen für Windows 8.1](vpn-settings-windows-8-1.md)
    - [Einstellungen für Windows 10](vpn-settings-windows-10.md) (einschließlich Windows Holographic for Business)

5. Wenn Sie fertig sind, wählen Sie **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern.

Das Profil wird erstellt und in der Profilliste angezeigt. Informationen zur Zuweisung dieses Profils zu Gruppen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).

## <a name="secure-your-vpn-profiles"></a>Sichern der VPN-Profile

VPN-Profile können eine Reihe verschiedener Verbindungstypen und Protokolle von unterschiedlichen Herstellern verwenden. Diese Verbindungen werden in der Regel mit den folgenden Methoden gesichert.

### <a name="certificates"></a>Zertifikate

Beim Erstellen des VPN-Profils wählen Sie ein SCEP- oder PKCS-Zertifikatprofil aus, das Sie zuvor in Intune erstellt haben. Dieses Profil wird als Identitätszertifikat bezeichnet. Es dient zur Authentifizierung anhand eines von Ihnen erstellten vertrauenswürdigen Zertifikatprofils (oder eines *Stammzertifikats*), das Sie erstellen, damit das Gerät des Benutzers eine Verbindung herstellen kann. Das vertrauenswürdige Zertifikat wird auf dem Computer zugewiesen, der die VPN-Verbindung authentifiziert, in der Regel ist dies der VPN-Server.

Weitere Informationen zum Erstellen und Verwenden von Zertifikatprofilen in Intune finden Sie unter [Konfigurieren von Zertifikaten mit Microsoft Intune](../protect/certificates-configure.md).

### <a name="user-name-and-password"></a>Benutzername und Kennwort

Der Benutzer authentifiziert sich beim VPN-Server durch Angabe seines Benutzernamens und Kennworts.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Im nächsten Schritt können Sie [das Profil einigen Geräten zuweisen](device-profile-assign.md).

Sie können auch Pro-App-VPNs für [Android](android-pulse-secure-per-app-vpn.md)- und [iOS](vpn-setting-configure-per-app.md)-Geräte erstellen und verwenden.
