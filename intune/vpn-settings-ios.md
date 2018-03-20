---
title: "VPN-Einstellungen für iOS-Geräte in Microsoft Intune"
titlesuffix: 
description: "Erfahren Sie mehr über die Intune-Einstellungen, die Sie zum Konfigurieren von VPN-Verbindungen auf iOS-Geräten verwenden können."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 70721d1d2f360527af0e269a93d6243b6a42431b
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>Konfigurieren von VPN-Einstellungen für iOS-Geräte in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

In diesem Artikel werden die Intune-Einstellungen veranschaulicht, die Sie verwenden können, um VPN-Verbindungen auf iOS-Geräten zu konfigurieren.

Je nach den ausgewählten Einstellungen können nicht alle Werte in der folgenden Liste konfiguriert werden.

## <a name="base-vpn-settings"></a>Grundlegende VPN-Einstellungen


**Verbindungsname:** Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die Liste der verfügbaren VPN-Verbindungen durchsuchen.
- **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen des VPN-Servers an, mit dem Geräte eine Verbindung herstellen. Beispiele: **192.168.1.1**, **vpn.contoso.com**.
- **Authentifizierungsmethode:** Wählen Sie unter folgenden Optionen aus, wie sich Geräte beim VPN-Server authentifizieren:
    - **Zertifikate:** Wählen Sie unter **Authentifizierungszertifikat** ein zuvor erstelltes SCEP- oder PKCS-Zertifikatprofil zum Authentifizieren der Verbindung aus. Weitere Informationen zu Zertifikatprofilen finden Sie unter [Konfigurieren von Zertifikaten in Microsoft Intune](certificates-configure.md).
    - **Benutzername und Kennwort:** Benutzer müssen einen Benutzernamen und ein Kennwort für die Anmeldung beim VPN-Server angeben.
- **Verbindungstyp:** Wählen Sie den VPN-Verbindungstyp in der folgenden Liste von Anbietern aus:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Cisco (IPsec)**
    - **Citrix**
    - **Benutzerdefiniertes VPN**
- **Tunneling teilen:** **Aktivieren** oder **deaktivieren** Sie diese Option, mit der Geräte anhand des Datenverkehrs selbst entscheiden können, welche Verbindung verwendet werden soll. Beispiel: Ein Benutzer in einem Hotel verwendet die VPN-Verbindung zum Zugreifen auf Arbeitsdateien, jedoch das Standardnetzwerk des Hotels für normales Webbrowsen.


## <a name="custom-vpn-settings"></a>Benutzerdefinierte VPN-Einstellungen

Wenn Sie **Benutzerdefiniertes VPN** als Verbindungstyp ausgewählt haben, konfigurieren Sie diese weiteren Einstellungen:

- **VPN-Bezeichner:** Dies ist ein Bezeichner für die verwendete VPN-App und wird von Ihrem VPN-Anbieter bereitgestellt.
- **Geben Sie Schlüssel-Wert-Paare für die benutzerdefinierten VPN-Attribute ein:** Fügen Sie **Schlüssel** und **Werte** zum Anpassen der VPN-Verbindung hinzu, oder importieren Sie sie. Auch diese Werte werden in der Regel von Ihrem VPN-Anbieter bereitgestellt.

## <a name="apps-per-app-vpn-settings"></a>App-Einstellungen (VPN für App)

- **VPN für App:** Aktivieren Sie diese Option, wenn Sie über URLs verfügen möchten, über die im Safari-Browser die VPN-Verbindung aktiviert werden kann. Für diese Konfiguration müssen Sie in den grundlegenden VPN-Einstellungen **Zertifikate** als Authentifizierungsmethode ausgewählt haben.
- **Hiermit geben Sie URLs zum Aktivieren der VPN-Verbindung bei Verwendung des Safari-Browsers an:** Klicken Sie hierauf, um Website-URLs hinzuzufügen. Wenn diese URLs aufgerufen werden, wird die VPN-Verbindung aktiviert.

- **Bedarfsgesteuerte Regeln:** Hier können Sie bedingte Regeln konfigurieren, die steuern, wann die VPN-Verbindung initiiert wird. Beispielsweise können Sie eine Bedingung erstellen, in der die VPN-Verbindung nur verwendet wird, wenn ein Gerät nicht mit einem Ihrer Unternehmens-WLAN-Netzwerke verbunden ist. Alternativ können Sie eine Bedingung erstellen, in der die VPN-Verbindung nicht initiiert wird, wenn ein Gerät nicht auf eine angegebene DNS-Suchdomäne zugreifen kann.

    - **SSIDs oder DNS-Suchdomänen:** Wählen Sie aus, ob diese Bedingung **SSIDs** des Drahtlosnetzwerks oder **DNS-Suchdomänen** verwenden soll. Wählen Sie „Hinzufügen“ aus, um SSIDs oder Suchdomänen zu konfigurieren.
    - **URL-Zeichenfolgentest:** Geben Sie optional eine URL an, die von der Regel als Test verwendet wird. Wenn das Gerät, auf dem dieses Profil installiert wird, auf diese URL ohne Umleitung zugreifen kann, wird die VPN-Verbindung initiiert, und das Gerät stellt eine Verbindung mit der Ziel-URL her. Der Standort des URL-Zeichenfolgentests wird dem Benutzer nicht angezeigt. Ein Beispiel für einen URL-Zeichenfolgentest ist die Adresse eines Überwachungswebservers, der die Gerätekompatibilität prüft, bevor die VPN-Verbindung hergestellt wird. Eine andere Möglichkeit besteht darin, mit der URL zu testen, ob das VPN eine Verbindung mit einem Standort herstellen kann, bevor das Gerät über das VPN mit der Ziel-URL verbunden wird.
    - **Domänenaktion:** Wählen Sie eine der folgenden Optionen aus:
        - Bei Bedarf verbinden 
        - Nie verbinden 
    - **Aktion:** Wählen Sie eine der folgenden Optionen aus:
        - Verbinden 
        - Verbindung auswerten 
        - Ignorieren 
        - Trennen 


## <a name="proxy-settings"></a>Proxyeinstellungen

- **Automatisches Konfigurationsskript:** Verwenden Sie eine Datei zum Konfigurieren des Proxyservers. Geben Sie die **Proxyserver-URL** ein (z.B. **http://proxy.contoso.com**), unter der die Konfigurationsdatei zu finden ist.
- **Adresse:** Geben Sie die Adresse des Proxyservers (als IP-Adresse) ein.
- **Portnummer:** Geben Sie die Portnummer ein, die dem Proxyserver zugeordnet ist.
