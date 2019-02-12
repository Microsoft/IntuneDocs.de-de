---
title: Konfigurieren von VPN-Einstellungen für Android-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Wenn Sie ein VPN-Konfigurationsprofil für Android und Android for Work-Geräte erstellen, geben Sie den Verbindungsnamen, die IP-Adresse oder den vollqualifizierten Domänennamen des VPN-Servers ein, wählen Sie aus, wie Benutzer mit dem VPN-Server authentifiziert werden sollen, und wählen Sie dann die Citrix-, SonicWall-, Check Point Capsule-, Pulse Secure- und Microsoft Edge-Verbindungstypen aus.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f37d19beddd96fdad63c61d83b0012869a7f9cd3
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55843713"
---
# <a name="configure-vpn-settings-for-devices-running-android-in-intune"></a>Konfigurieren von VPN-Einstellungen für Android-Geräte in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Dieser Artikel veranschaulicht die Intune-Einstellungen, die Sie verwenden können, um VPN-Verbindungen auf Android-Geräten zu konfigurieren.

Sie können VPN-Einstellungen für die folgenden Plattformen konfigurieren:

- [Android](#android-vpn-settings)
- [Android Enterprise](#android-enterprise-vpn-settings)

Je nach den ausgewählten Einstellungen können nicht alle der folgenden Werte konfiguriert werden.

## <a name="android-vpn-settings"></a>Android-VPN-Einstellungen

- **Verbindungsname:** Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die verfügbaren VPN-Verbindungen durchsuchen.
- **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen (FQDN) des VPN-Servers ein, mit dem Geräte eine Verbindung herstellen. Geben Sie beispielsweise **192.168.1.1** oder **vpn.contoso.com** ein.

  - **Authentifizierungsmethode**: Wählen Sie aus, wie sich Geräte beim VPN-Server authentifizieren. Folgende Optionen sind verfügbar:

    - **Zertifikate**: Wählen Sie ein vorhandenes SCEP- oder PKCS-Zertifikatprofil zum Authentifizieren der Verbindung aus. Unter [Konfigurieren eines Zertifikatprofils](certificates-configure.md) werden die Schritte aufgeführt, die zum Erstellen eines Zertifikatprofils erforderlich sind.
    - **Benutzername und Kennwort**: Endbenutzer werden bei der Anmeldung beim VPN-Server dazu aufgefordert, einen Benutzernamen und ein Kennwort einzugeben.

- **Verbindungstyp:** Wählen Sie den VPN-Verbindungstyp aus. Folgende Optionen sind verfügbar:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Citrix**

- **Fingerabdruck** (Nur Check Point Capsule VPN): Geben Sie eine Zeichenfolge (z.B. **Contoso-Fingerabdruckcode**) ein, um zu überprüfen, ob der VPN-Server vertrauenswürdig ist. Ein Fingerabdruck kann an den Client gesendet werden, damit dieser weiß, dass alle Server vertrauenswürdig sind, die beim Verbinden den gleichen Fingerabdruck vorweisen. Wenn das Gerät nicht über den Fingerabdruck verfügt, wird der Benutzer dazu aufgefordert, dem VPN-Server zu vertrauen, während der Fingerabdruck angezeigt wird. (Der Benutzer überprüft den Fingerabdruck manuell und wählt „Vertrauen“ aus, um die Verbindung herzustellen.)
- **Geben Sie Schlüssel-Wert-Paare für die Citrix-VPN-Attribute ein** (nur Citrix): Geben Sie von Citrix bereitgestellte Schlüssel-Wert-Paare ein. Durch diese Werte werden die Eigenschaften der VPN-Verbindung konfiguriert.

## <a name="android-enterprise-vpn-settings"></a>Android-VPN-Einstellungen für Unternehmen

- **Verbindungsname:** Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die verfügbaren VPN-Verbindungen durchsuchen.
- **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen (FQDN) des VPN-Servers ein, mit dem Geräte eine Verbindung herstellen. Geben Sie beispielsweise **192.168.1.1** oder **vpn.contoso.com** ein.

  - **Authentifizierungsmethode**: Wählen Sie aus, wie sich Geräte beim VPN-Server authentifizieren. Folgende Optionen sind verfügbar:
  
    - **Zertifikate**: Wählen Sie ein vorhandenes SCEP- oder PKCS-Zertifikatprofil zum Authentifizieren der Verbindung aus. Unter [Konfigurieren eines Zertifikatprofils](certificates-configure.md) werden die Schritte aufgeführt, die zum Erstellen eines Zertifikatprofils erforderlich sind.
    - **Benutzername und Kennwort**: Endbenutzer werden bei der Anmeldung beim VPN-Server dazu aufgefordert, einen Benutzernamen und ein Kennwort einzugeben.

- **Verbindungstyp:** Wählen Sie den VPN-Verbindungstyp aus. Folgende Optionen sind verfügbar:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="next-steps"></a>Nächste Schritte
[VPN-Profile in Intune](vpn-settings-configure.md)
