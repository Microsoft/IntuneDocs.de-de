---
title: VPN-Einstellungen für iOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Darstellung der verfügbaren Konfigurationseinstellungen für virtuelle private Netzwerke (VPNs), einschließlich der Verbindungsdetails, Authentifizierungsmethoden und dem getrennten Tunneln in den Grundeinstellungen; der benutzerdefinierten VPN-Einstellungen mit dem Bezeichner und den Schlüssel-Wert-Paaren; der App-bezogenen VPN-Einstellungen, die Safari-URLs und bedarfsgesteuerten VPNs mit SSIDs oder DNS-Suchdomänen enthalten; und der Proxyeinstellungen zum Einschließen von einem Konfigurationsskript, einer IP-Adresse oder FQDN-Adresse und einem TCP-Port in Microsoft Intune auf Geräten mit iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d35c9e32b7a0720d5d84a93a7edde6f2bd51911f
ms.sourcegitcommit: 08e1b0d45c84eb9525a0a59f5540d41434da2814
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39146627"
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

    > [!NOTE]
    > Wenn Benutzername und Kennwort als Authentifizierungsmethode für Cisco IPsec VPN verwendet werden, müssen sie das SharedSecret über ein benutzerdefiniertes Apple Configurator-Profil bereitstellen.
  
- **Verbindungstyp**: Wählen Sie den VPN-Verbindungstyp aus der folgenden Liste von Anbietern aus:
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **Cisco Legacy AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Palo Alto Networks GlobalProtect**
  - **Pulse Secure**
  - **Cisco (IPsec)**
  - **Citrix**
  - **Benutzerdefiniertes VPN**

    > [!NOTE]
    > - **Cisco Legacy AnyConnect VPN**-Profile eignen sich für die [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924)-App-Version 4.0.5x und ältere Versionen
    > - **Cisco AnyConnect VPN**-Profile eignen sich für die [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690)-App-Version 4.0.7x und neuere Versionen

- **Tunneling teilen**: **Aktivieren** oder **deaktivieren** Sie diese Option, damit die Geräte anhand des Datenverkehrs selbst entscheiden können, welche Verbindung verwendet werden soll. Zum Beispiel verwendet ein Benutzer in einem Hotel die VPN-Verbindung zum Zugreifen auf Arbeitsdateien, das Standardnetzwerk des Hotels jedoch für normales Webbrowsen.

## <a name="custom-vpn-settings"></a>Benutzerdefinierte VPN-Einstellungen

Wenn Sie **Benutzerdefiniertes VPN** als Verbindungstyp ausgewählt haben, konfigurieren Sie auch die folgenden Einstellungen:

- **VPN-Bezeichner:** Ein Bezeichner für die verwendete VPN-App, die von Ihrem VPN-Anbieter bereitgestellt wird.
- **Geben Sie Schlüssel-Wert-Paare für die benutzerdefinierten VPN-Attribute ein:** Fügen Sie **Schlüssel** und **Werte** zum Anpassen der VPN-Verbindung hinzu, oder importieren Sie sie. Auch diese Werte werden in der Regel von Ihrem VPN-Anbieter bereitgestellt.

## <a name="automatic-vpn-settings"></a>Automatische VPN-Einstellungen

- **VPN pro App**: Wenn Sie diese Option wählen, wird das VPN pro App aktiviert, sodass die VPN-Verbindung automatisch hergestellt wird, wenn bestimmte Apps geöffnet werden. Zusätzlich zu dieser Option müssen Sie die Apps mit diesem VPN-Profil verknüpfen. Weitere Informationen finden Sie in [Die Einrichtung des Pro-App-VPN in Intune für iOS-Geräte](vpn-setting-configure-per-app.md). 
  - **Safari URLs, die dieses VPN auslösen:** Wählen Sie mindestens eine Website-URL aus, oder fügen Sie diese hinzu. Wenn diese URLs mit dem Safari-Browser auf dem Gerät aufgerufen werden, wird die VPN-Verbindung automatisch aufgebaut.

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

## <a name="next-step"></a>Nächster Schritt
[Erstellen von VPN-Profilen in Intune](vpn-settings-configure.md)
