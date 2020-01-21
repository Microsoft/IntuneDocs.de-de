---
title: Konfigurieren von VPN-Einstellungen für Windows 8.1-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Fügen Sie ein VPN-Konfigurations Profil mithilfe von VPN-Konfigurationseinstellungen (Virtual Private Network, VPN) hinzu, einschließlich der Verbindungsdetails und der Proxy Einstellungen zum Einbeziehen der IP-Adresse oder FQDN-Adresse und des TCP-Ports in Microsoft InTune auf Geräten, auf denen Windows 8.1 ausgeführt wird.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f9a1399d5474d79ac8fd48a8aa3a844f20eb640
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207042"
---
# <a name="add-vpn-settings-on-windows-81-devices-in-microsoft-intune"></a>Hinzufügen von VPN-Einstellungen für Windows 8.1-Geräte in Microsoft Intune



In diesem Artikel werden die Intune-Einstellungen veranschaulicht, die Sie verwenden können, um VPN-Verbindungen auf Windows 8.1-Geräten zu konfigurieren.

Je nach den ausgewählten Einstellungen können nicht alle Werte in der folgenden Liste konfiguriert werden.

## <a name="base-vpn-settings"></a>Grundlegende VPN-Einstellungen

- **Alle Einstellungen auf Windows 8.1 anwenden**: Diese Einstellung können Sie im klassischen InTune-Portal konfigurieren. Diese Einstellung kann im Microsoft Endpoint Manager Admin Center nicht geändert werden. Wenn hierfür **Konfiguriert** festgelegt ist, werden sämtliche Einstellungen nur auf Windows 8.1-Geräte angewendet. Wenn **Nicht konfiguriert** festgelegt wird, gelten diese Einstellungen auch für Windows 10-Geräte.
- **Verbindungsname:** Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die Liste der verfügbaren VPN-Verbindungen durchsuchen.
- **Server:** Fügen Sie mindestens einen VPN-Server hinzu, mit dem Geräte eine Verbindung herstellen können.
  - **Hinzufügen**: Öffnet die Seite **Zeile hinzufügen**, auf der Sie die folgenden Informationen angeben können:
    - **Beschreibung:** Geben Sie einen beschreibenden Namen für den Server ein, z. B. **Contoso-VPN-Server**.
    - **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollständig qualifizierten Domänennamen des VPN-Servers an, mit dem Geräte eine Verbindung herstellen. Beispiele: **192.168.1.1**, **vpn.contoso.com**.
    - **Standardserver:** Aktiviert diesen Server als Standardserver, über den Geräte die Verbindung herstellen. Achten Sie darauf, nur einen Server als Standard festzulegen.
  - **Importieren:** Suchen Sie nach einer Datei, die eine durch Trennzeichen getrennte Liste von Servern im Format „Beschreibung, IP-Adresse oder FQDN, Standardserver“ enthält. Wählen Sie **OK** aus, um diese Server in die Liste **Server** zu importieren.
  - **Exportieren:** Exportiert die Liste der Server in eine CSV-Datei (Comma-Separated Values, durch Trennzeichen getrennte Werte).

- **Verbindungstyp:** Wählen Sie den VPN-Verbindungstyp aus der folgenden Liste von Anbietern aus:
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only): Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **Anmeldegruppe oder -domäne** (nur SonicWall Mobile Connect): Geben Sie den Namen der Anmeldegruppe oder Domäne an, mit der Sie eine Verbindung herstellen möchten.

- **Rolle** (nur Pulse Secure): Geben Sie den Namen der Benutzerrolle an, die Zugriff auf diese Verbindung hat. Eine Benutzerrolle definiert persönliche Einstellungen und Optionen und aktiviert oder deaktiviert bestimmte Zugriffsfeatures.

- **Bereich** (nur Pulse Secure): Geben Sie den Namen des gewünschten Authentifizierungsbereichs an. Ein Authentifizierungsbereich ist eine Gruppe von Authentifizierungsressourcen, die vom Verbindungstyp „Pulse Secure“ verwendet werden.

- **Benutzerdefiniertes XML:** Geben Sie benutzerdefinierte XML-Befehle zum Konfigurieren der VPN-Verbindung an.

  **Pulse Secure-Beispiel**:

  ```xml
  <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
  ```

  **CheckPoint Mobile VPN-Beispiel**:

  ```xml
  <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
  ```

  **SonicWall Mobile Connect-Beispiel**:

  ```xml
  <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
  ```

  **F5 Edge Client-Beispiel**:

  ```xml
  <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
  ```

  Weitere Informationen zum Erstellen von benutzerdefinierten XML-Befehlen finden Sie in der VPN-Dokumentation des Herstellers.

## <a name="proxy-settings"></a>Proxyeinstellungen

- **Proxyeinstellungen automatisch erkennen:** Wenn der VPN-Server einen Proxyserver für die Verbindung erfordert, geben Sie an, ob Geräte die Verbindungseinstellungen automatisch erkennen können sollen.
- **Automatisches Konfigurationsskript:** Verwenden Sie eine Datei, um den Proxyserver zu konfigurieren. Geben Sie die **Proxyserver-URL** ein, die die Konfigurationsdatei enthält. Geben Sie beispielsweise `http://proxy.contoso.com` ein.
- **Proxyserver verwenden**: Aktivieren Sie diese Option, wenn Sie die Proxyeinstellungen für den Server manuell eingeben möchten.
  - **Adresse**: Geben Sie die Adresse des Proxyservers (als IP-Adresse) ein.
  - **Portnummer:** Geben Sie die Portnummer ein, die dem Proxyserver zugeordnet ist.
- **Proxy für lokale Adressen umgehen:** Wenn der VPN-Server einen Proxyserver für die Verbindung erfordert, dieser aber für von Ihnen angegebene lokale Adressen nicht verwendet werden soll, aktivieren Sie diese Option.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).

Konfigurieren Sie VPN-Einstellungen auf [Android](vpn-settings-android.md)-, [Android Enterprise](vpn-settings-android-enterprise.md)-, [macOS](vpn-settings-macos.md)-und [Windows 10](vpn-settings-windows-10.md) -Geräten.
