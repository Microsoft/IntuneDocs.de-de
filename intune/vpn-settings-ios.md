---
title: VPN-Einstellungen für iOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Darstellung der verfügbaren Konfigurationseinstellungen für virtuelle private Netzwerke (VPNs), einschließlich der Verbindungsdetails, Authentifizierungsmethoden und dem getrennten Tunneln in den Grundeinstellungen; der benutzerdefinierten VPN-Einstellungen mit dem Bezeichner und den Schlüssel-Wert-Paaren; der App-bezogenen VPN-Einstellungen, die Safari-URLs und bedarfsgesteuerten VPNs mit SSIDs oder DNS-Suchdomänen enthalten; und der Proxyeinstellungen zum Einschließen von einem Konfigurationsskript, einer IP-Adresse oder FQDN-Adresse und einem TCP-Port in Microsoft Intune auf Geräten mit iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3ce970f942d8ea20eb9ea593c23160757122926e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>Konfigurieren von VPN-Einstellungen für iOS-Geräte in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel werden die Intune-Einstellungen veranschaulicht, die Sie verwenden können, um VPN-Verbindungen auf iOS-Geräten zu konfigurieren.

Je nach den ausgewählten Einstellungen können nicht alle Werte in der folgenden Liste konfiguriert werden.

## <a name="base-vpn-settings"></a>Grundlegende VPN-Einstellungen

- **Verbindungsname**: Geben Sie einen Namen für diese Verbindung ein. Endbenutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät eine Liste der verfügbaren VPN-Verbindungen durchsuchen.
- **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen (FQDN) des VPN-Servers ein, mit dem Geräte eine Verbindung herstellen. Geben Sie beispielsweise **192.168.1.1** oder **vpn.contoso.com** ein.
- **Authentifizierungsmethode:** Wählen Sie unter folgenden Optionen aus, wie sich Geräte beim VPN-Server authentifizieren:
  - **Zertifikate:** Wählen Sie unter **Authentifizierungszertifikat** ein vorhandenes SCEP- oder PKCS-Zertifikatprofil zum Authentifizieren der Verbindung aus. Informationen zu Zertifikatprofilen finden Sie unter [Konfigurieren von Zertifikaten](certificates-configure.md).
  - **Benutzername und Kennwort:** Benutzer müssen einen Benutzernamen und ein Kennwort für die Anmeldung beim VPN-Server eingeben.
- **Verbindungstyp**: Wählen Sie den VPN-Verbindungstyp aus der folgenden Liste von Anbietern aus:
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Cisco (IPsec)**
  - **Citrix**
  - **Benutzerdefiniertes VPN**

- **Tunneling teilen**: **Aktivieren** oder **deaktivieren** Sie diese Option, damit die Geräte anhand des Datenverkehrs selbst entscheiden können, welche Verbindung verwendet werden soll. Beispiel: Ein Benutzer in einem Hotel verwendet die VPN-Verbindung zum Zugreifen auf Arbeitsdateien, jedoch das Standardnetzwerk des Hotels für normales Webbrowsen.

## <a name="custom-vpn-settings"></a>Benutzerdefinierte VPN-Einstellungen

Wenn Sie **Benutzerdefiniertes VPN** als Verbindungstyp ausgewählt haben, konfigurieren Sie auch die folgenden Einstellungen:

- **VPN-Bezeichner:** Ein Bezeichner für die verwendete VPN-App, die von Ihrem VPN-Anbieter bereitgestellt wird.
- **Geben Sie Schlüssel-Wert-Paare für die benutzerdefinierten VPN-Attribute ein:** Fügen Sie **Schlüssel** und **Werte** zum Anpassen der VPN-Verbindung hinzu, oder importieren Sie sie. Auch diese Werte werden in der Regel von Ihrem VPN-Anbieter bereitgestellt.

## <a name="apps-per-app-vpn-settings"></a>App-Einstellungen (VPN für App)

- **VPN für App:** Aktivieren Sie diese Option, wenn Sie URLs verwenden möchten, über die im Safari-Browser die VPN-Verbindung aktiviert werden kann. Zum Konfigurieren von VPN pro App müssen Sie in den grundlegenden VPN-Einstellungen **Zertifikate** als Authentifizierungsmethode auswählen.
  - **Safari URLs, die dieses VPN auslösen:** Wählen Sie mindestens eine Website-URL aus, oder fügen Sie diese hinzu. Wenn diese URLs aufgerufen werden, wird die VPN-Verbindung aktiviert.

- **Bedarfsgesteuertes VPN:** Konfigurieren Sie bedingte Regeln, die steuern, wann die VPN-Verbindung initiiert wird. Erstellen Sie beispielsweise eine Bedingung, in der die VPN-Verbindung nur verwendet wird, wenn ein Gerät nicht mit einem Drahtlosnetzwerk des Unternehmens verbunden ist. Erstellen Sie alternativ eine Bedingung, in der die VPN-Verbindung nicht initiiert wird, wenn ein Gerät nicht auf eine angegebene DNS-Suchdomäne zugreifen kann.

  - **SSIDs oder DNS-Suchdomänen:** Wählen Sie aus, ob diese Bedingung **SSIDs** des Drahtlosnetzwerks oder **DNS-Suchdomänen** verwenden soll. Klicken Sie auf **Hinzufügen**, um SSIDs oder Suchdomänen zu konfigurieren.
  - **URL-Zeichenfolgentest:** Optional. Geben Sie eine URL ein, die die Regel als Test verwenden soll. Wenn das Gerät, auf dem dieses Profil installiert wird, auf diese URL ohne Umleitung zugreifen kann, wird die VPN-Verbindung initiiert, und das Gerät stellt eine Verbindung mit der Ziel-URL her. Der Standort des URL-Zeichenfolgentests wird dem Benutzer nicht angezeigt. Ein Beispiel für einen URL-Zeichenfolgentest ist die Adresse eines Überwachungswebservers, der die Gerätekonformität prüft, bevor die VPN-Verbindung hergestellt wird. Eine andere Möglichkeit besteht darin, mit der URL zu testen, ob das VPN eine Verbindung mit einem Standort herstellen kann, bevor das Gerät über das VPN mit der Ziel-URL verbunden wird.
  - **Domänenaktion:** Wählen Sie eine der folgenden Optionen aus:
    - Bei Bedarf verbinden
    - Nie verbinden
  - **Aktion:** Wählen Sie eine der folgenden Optionen aus:
    - Verbinden
    - Verbindung auswerten
    - Ignorieren
    - Trennen

## <a name="proxy-settings"></a>Proxyeinstellungen

- **Automatisches Konfigurationsskript**: Verwenden Sie eine Datei zum Konfigurieren des Proxyservers. Geben Sie die **Proxyserver-URL** ein (z.B. **http://proxy.contoso.com**), unter der die Konfigurationsdatei zu finden ist.
- **Adresse:** Geben Sie die IP-Adresse des vollständig qualifizierten Hostnamens des Proxyservers ein.
- **Portnummer:** Geben Sie die Portnummer ein, die dem Proxyserver zugeordnet ist.
