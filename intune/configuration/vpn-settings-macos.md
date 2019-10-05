---
title: Konfigurieren von VPN-Einstellungen für macOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Fügen Sie ein virtuelles privates Netzwerk (VPN)-Konfigurations Profil hinzu, oder erstellen Sie ein virtuelles privates Netzwerk (VPN), einschließlich Verbindungsdetails, geteiltes Tunneln, benutzerdefinierte VPN-Einstellungen mit dem Bezeichner, Schlüssel-/Wert-Paaren, Proxy Einstellungen mit einem Konfigurationsskript, IP-Adresse oder voll qualifizierten IP-Adresse Microsoft InTune auf macOS-Geräten.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a088407ec456c6b1a1ff3df7fa17976089f6fc4f
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734140"
---
# <a name="add-vpn-settings-on-macos-devices-in-microsoft-intune"></a>Hinzufügen von VPN-Einstellungen für macOS-Geräte in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In diesem Artikel werden die Intune-Einstellungen veranschaulicht, die Sie verwenden können, um VPN-Verbindungen auf macOS-Geräten zu konfigurieren.

Je nach den ausgewählten Einstellungen können nicht alle Werte in der folgenden Liste konfiguriert werden.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](vpn-settings-configure.md)

> [!NOTE]
> Diese Einstellungen sind für alle Registrierungs Typen verfügbar. Weitere Informationen zu den Registrierungs Typen finden Sie unter [macOS](../enrollment/macos-enroll.md)-Registrierung.

## <a name="base-vpn-settings"></a>Grundlegende VPN-Einstellungen

**Verbindungsname**: Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die Liste der verfügbaren VPN-Verbindungen durchsuchen.
- **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen des VPN-Servers an, mit dem Geräte eine Verbindung herstellen. Beispiele: **192.168.1.1**, **vpn.contoso.com**.
- **Authentifizierungsmethode:** Wählen Sie unter folgenden Optionen aus, wie sich Geräte beim VPN-Server authentifizieren:
  - **Zertifikate:** Wählen Sie unter **Authentifizierungszertifikat** ein zuvor erstelltes SCEP- oder PKCS-Zertifikatprofil zum Authentifizieren der Verbindung aus. Weitere Informationen zu Zertifikatprofilen finden Sie unter [Konfigurieren von Zertifikaten in Microsoft Intune](../protect/certificates-configure.md).
  - **Benutzername und Kennwort:** Endbenutzer müssen einen Benutzernamen und ein Kennwort für die Anmeldung beim VPN-Server angeben.
- **Verbindungstyp**: Wählen Sie den VPN-Verbindungstyp aus der folgenden Liste von Anbietern aus:
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Benutzerdefiniertes VPN**
- **Tunneling teilen**: **Aktivieren** oder **Deaktivieren** Sie diese Option, mit der Geräte anhand des Datenverkehrs selbst entscheiden können, welche Verbindung verwendet werden soll. Beispiel: Ein Benutzer in einem Hotel verwendet die VPN-Verbindung zum Zugreifen auf Arbeitsdateien, jedoch das Standardnetzwerk des Hotels für normales Webbrowsen.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](../apps/apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>Benutzerdefinierte VPN-Einstellungen

Wenn Sie **Benutzerdefiniertes VPN** ausgewählt haben, konfigurieren Sie diese weiteren Einstellungen:

- **VPN-Bezeichner**: Geben Sie einen Bezeichner für die verwendete VPN-App ein. Dieser Bezeichner wird von Ihrem VPN-Anbieter bereitgestellt.
- **Geben Sie Schlüssel-Wert-Paare für die benutzerdefinierten VPN-Attribute ein:** Fügen Sie **Schlüssel** und **Werte** zum Anpassen der VPN-Verbindung hinzu, oder importieren Sie sie. Diese Werte werden in der Regel von Ihrem VPN-Anbieter bereitgestellt.

## <a name="proxy-settings"></a>Proxyeinstellungen

- **Automatisches Konfigurationsskript**: Verwenden Sie eine Datei zum Konfigurieren des Proxyservers. Geben Sie die **Proxyserver-URL** ein, die die Konfigurationsdatei enthält. Geben Sie beispielsweise `http://proxy.contoso.com` ein.
- **Adresse:** Geben Sie die Adresse des Proxyservers (als IP-Adresse) ein.
- **Portnummer:** Geben Sie die Portnummer ein, die dem Proxyserver zugeordnet ist.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).

Konfigurieren Sie VPN-Einstellungen auf [Android](vpn-settings-android.md)-, [Android Enterprise](vpn-settings-android-enterprise.md)-, [IOS](vpn-settings-ios.md)-und [Windows 10](vpn-settings-windows-10.md) -Geräten.
