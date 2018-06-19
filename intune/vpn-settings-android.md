---
title: VPN-Einstellungen für Android-Geräte in Microsoft Intune
titlesuffix: ''
description: In diesem Artikel lernen Sie die Intune-Einstellungen kennen, mit denen Sie VPN-Verbindungen auf Android-Geräten konfigurieren können.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6753e0232548d862b46a273f1be0105ad7f16d63
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31831944"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-android"></a>Konfigurieren von VPN-Einstellungen für Android-Geräte in Microsoft Intune 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Dieser Artikel veranschaulicht die Intune-Einstellungen, die Sie verwenden können, um VPN-Verbindungen auf Android-Geräten zu konfigurieren.


Sie können VPN-Einstellungen für die folgenden Plattformen konfigurieren:

- [Android](#android-vpn-settings)
- [Android for Work](#android-for-work-vpn-settings)

Je nach den ausgewählten Einstellungen können nicht alle der folgenden Werte konfiguriert werden.

## <a name="android-vpn-settings"></a>Android-VPN-Einstellungen
**Verbindungsname:** Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die Liste der verfügbaren VPN-Verbindungen durchsuchen.
- **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen des VPN-Servers an, mit dem Geräte eine Verbindung herstellen. Beispiele: **192.168.1.1**, **vpn.contoso.com**.
- **Authentifizierungsmethode:** Wählen Sie unter folgenden Optionen aus, wie sich Geräte beim VPN-Server authentifizieren:
    - **Zertifikate:** Wählen Sie ein zuvor erstelltes SCEP- oder PKCS-Zertifikatprofil zum Authentifizieren der Verbindung aus. Ausführliche Informationen zu Zertifikatprofilen finden Sie unter [Konfigurieren von Zertifikaten](certificates-configure.md).
    - **Benutzername und Kennwort:** Endbenutzer müssen einen Benutzernamen und ein Kennwort für die Anmeldung beim VPN-Server angeben.
- **Verbindungstyp:** Wählen Sie den VPN-Verbindungstyp in der folgenden Liste von Anbietern aus:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Citrix**

- **Fingerabdruck** (nur Check Point Capsule-VPN): Geben Sie eine Zeichenfolge (z.B. „Contoso-Fingerabdruckcode“) an, mit der überprüft wird, ob der VPN-Server vertrauenswürdig ist. Ein Fingerabdruck kann an den Client gesendet werden, damit dieser weiß, dass alle Server vertrauenswürdig sind, die beim Verbinden den betreffenden Fingerabdruck vorweisen. Wenn das Gerät noch nicht über den Fingerabdruck verfügt, wird der Benutzer aufgefordert, dem VPN-Server zu vertrauen, zu dem eine Verbindung hergestellt wird, während der Fingerabdruck angezeigt wird (der Benutzer überprüft den Fingerabdruck manuell und klickt auf „Vertrauen“, um die Verbindung herzustellen).
- **Geben Sie Schlüssel-Wert-Paare für die Citrix-VPN-Attribute ein** (nur Citrix): Geben Sie von Citrix bereitgestellte Schlüssel-Wert-Paare ein, um die Eigenschaften der VPN-Verbindung zu konfigurieren.

## <a name="android-for-work-vpn-settings"></a>VPN-Einstellungen für Android for Work

**Verbindungsname:** Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die Liste der verfügbaren VPN-Verbindungen durchsuchen.
- **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen des VPN-Servers an, mit dem Geräte eine Verbindung herstellen. Beispiele: **192.168.1.1**, **vpn.contoso.com**.
- **Authentifizierungsmethode:** Wählen Sie unter folgenden Optionen aus, wie sich Geräte beim VPN-Server authentifizieren:
    - **Zertifikate:** Wählen Sie ein zuvor erstelltes SCEP- oder PKCS-Zertifikatprofil zum Authentifizieren der Verbindung aus. Ausführliche Informationen zu Zertifikatprofilen finden Sie unter [Konfigurieren von Zertifikaten](certificates-configure.md).
    - **Benutzername und Kennwort:** Endbenutzer müssen einen Benutzernamen und ein Kennwort für die Anmeldung beim VPN-Server angeben.
- **Verbindungstyp:** Wählen Sie den VPN-Verbindungstyp in der folgenden Liste von Anbietern aus:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

