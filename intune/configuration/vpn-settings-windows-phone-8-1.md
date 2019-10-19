---
title: VPN-Einstellungen für Windows Phone 8.1-Geräte in Microsoft Intune
titleSuffix: ''
description: Erfahren Sie mehr über die Intune-Einstellungen, die Sie zum Konfigurieren von VPN-Verbindungen auf Windows Phone 8.1-Geräten verwenden können.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69de660e65ed2a0f3b6c9c7e4ce774a6fcde2676
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506517"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Konfigurieren von VPN-Einstellungen für Windows Phone 8.1-Geräte in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In diesem Artikel werden die Intune-Einstellungen veranschaulicht, die Sie verwenden können, um VPN-Verbindungen auf Windows Phone 8.1-Geräten zu konfigurieren.


Je nach den ausgewählten Einstellungen können nicht alle Werte in der folgenden Liste konfiguriert werden.

## <a name="base-vpn-settings"></a>Grundlegende VPN-Einstellungen

- **Alle Einstellungen nur auf Windows Phone 8.1 anwenden:** Diese Einstellung können Sie im klassischen Intune-Portal konfigurieren. Im Azure-Portal kann diese Einstellung nicht geändert werden. Wenn hierfür **Konfiguriert** festgelegt wird, werden sämtliche Einstellungen nur auf Windows Phone 8.1-Geräten angewendet. Wenn hierfür **Nicht konfiguriert** festgelegt wird, gelten diese Einstellungen auch für mobile Windows 10-Geräte.
- **Verbindungsname:** Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die Liste der verfügbaren VPN-Verbindungen durchsuchen.
- **Authentifizierungsmethode:** Wählen Sie unter folgenden Optionen aus, wie sich Geräte beim VPN-Server authentifizieren:
  - **Zertifikate:** Wählen Sie unter **Authentifizierungszertifikat** ein zuvor erstelltes SCEP- oder PKCS-Zertifikatprofil zum Authentifizieren der Verbindung aus. Ausführliche Informationen zu Zertifikatprofilen finden Sie unter [Konfigurieren von Zertifikaten](../protect/certificates-configure.md).
  - **Benutzername und Kennwort:** Endbenutzer müssen einen Benutzernamen und ein Kennwort für die Anmeldung beim VPN-Server angeben.
- **Server:** Fügen Sie einen oder mehrere VPN-Server hinzu, mit denen Geräte eine Verbindung herstellen.
  - **Hinzufügen:** öffnet das Blatt **Zeile hinzufügen**, auf dem Sie die folgende Informationen angeben können:
    - **Beschreibung:** Geben Sie einen beschreibenden Namen für den Server ein, z.B. **Contoso-VPN-Server**.
    - **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen des VPN-Servers an, mit dem Geräte eine Verbindung herstellen. Beispiele: **192.168.1.1**, **vpn.contoso.com**.
    - **Standardserver:** Aktiviert diesen Server als Standardserver, über den Geräte die Verbindung herstellen. Achten Sie darauf, nur einen Server als Standard festzulegen.
  - **Importieren:** Suchen Sie nach einer Datei, die eine durch Trennzeichen getrennte Liste von Servern im Format „Beschreibung, IP-Adresse oder FQDN, Standardserver“ enthält. Wählen Sie **OK** aus, um diese in die Liste **Server** zu importieren.
  - **Exportieren:** exportiert die Liste der Server in eine CSV-Datei (Comma-Separated Values, durch Trennzeichen getrennte Werte).

- **VPN bei Verbindung mit Unternehmens-WLAN umgehen:** Aktivieren Sie diese Option, um anzugeben, dass keine VPN-Verbindung verwendet wird, wenn das Gerät mit dem WLAN-Netzwerk des Unternehmens verbunden ist.
- **VPN bei Verbindung mit Heim-WLAN umgehen**: Aktivieren Sie diese Option, um anzugeben, dass die VPN-Verbindung nicht verwendet wird, wenn das Gerät mit einem Heim-WLAN-Netzwerk verbunden ist.

- **Verbindungstyp:** Wählen Sie den VPN-Verbindungstyp in der folgenden Liste von Anbietern aus:
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

- **Anmeldegruppe oder -domäne** (nur SonicWall Mobile Connect): Geben Sie den Namen der Anmeldegruppe oder -domäne an, mit der Sie eine Verbindung herstellen möchten.
- **Rolle** (nur Pulse Secure): Geben Sie den Namen der Benutzerrolle an, die Zugriff auf diese Verbindung hat. Eine Benutzerrolle definiert persönliche Einstellungen und Optionen und aktiviert oder deaktiviert bestimmte Zugriffsfeatures.
- **Bereich** (nur Pulse Secure): Geben Sie den Namen des gewünschten Authentifizierungsbereichs an. Ein Authentifizierungsbereich ist eine Gruppe von Authentifizierungsressourcen, die vom Verbindungstyp „Pulse Secure“ verwendet werden.

- **DNS-Suffixsuchliste** - **Fügen** Sie DNS-Suffixe hinzu. Jedes angegebene DNS-Suffix wird beim Verbinden mit einer Website unter Verwendung eines Kurznamens gesucht. Geben Sie beispielsweise die DNS-Suffixe **domain1.contoso.com** und **domain2.contoso.com** an, und öffnen Sie die URL `http://mywebsite`, und die URLs `http://mywebsite.domain1.contoso.com` und `http://mywebsite.domain2.contoso.com` werden durchsucht.

- **Benutzerdefiniertes XML:** Geben Sie benutzerdefinierte XML-Befehle zum Konfigurieren der VPN-Verbindung an.

    **Beispiel für Pulse Secure:**

```xml
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Beispiel für CheckPoint Mobile VPN:**

```xml
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Beispiel für SonicWall Mobile Connect:**

```xml
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Beispiel für F5 Edge Client:**

```xml
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Weitere Informationen zum Erstellen von benutzerdefinierten XML-Befehlen finden Sie in der VPN-Dokumentation des jeweiligen Herstellers.

- **Tunneling teilen** - **Aktivieren** oder **Deaktivieren** Sie diese Option, mit der Geräte anhand des Datenverkehrs selbst entscheiden können, welche Verbindung verwendet werden soll. Beispiel: Ein Benutzer in einem Hotel verwendet die VPN-Verbindung zum Zugreifen auf Arbeitsdateien, jedoch das Standardnetzwerk des Hotels für normales Webbrowsen.




## <a name="proxy-settings"></a>Proxyeinstellungen

- **Proxyeinstellungen automatisch erkennen:** Wenn der VPN-Server einen Proxyserver für die Verbindung erfordert, geben Sie an, ob Geräte die Verbindungseinstellungen automatisch erkennen können sollen. Weitere Informationen finden Sie in der Windows Server-Dokumentation.
- **Automatisches Konfigurationsskript:** Verwenden Sie eine Datei zum Konfigurieren des Proxyservers. Geben Sie die **Proxyserver-URL** ein (z.B. `http://proxy.contoso.com`), unter der die Konfigurationsdatei zu finden ist.
- **Proxyserver verwenden:** Aktivieren Sie diese Option, wenn Sie die Proxyeinstellungen für den Server manuell eingeben möchten.
  - **Adresse:** Geben Sie die Adresse des Proxyservers (als IP-Adresse) ein.
  - **Portnummer:** Geben Sie die Portnummer ein, die dem Proxyserver zugeordnet ist.
- **Proxy für lokale Adressen umgehen:** Wenn der VPN-Server einen Proxyserver für die Verbindung erfordert, aktivieren Sie diese Option, wenn der Proxyserver für von Ihnen angegebene lokale Adressen nicht verwendet werden soll. Weitere Informationen finden Sie in der Windows Server-Dokumentation.
