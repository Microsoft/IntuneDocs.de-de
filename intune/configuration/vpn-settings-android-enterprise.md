---
title: Verwenden von VPN-Einstellungen für Android Enterprise in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Weitere Informationen finden Sie unter alle Einstellungen zum Erstellen von VPN-Verbindungen auf Android-Unternehmens Geräten in Microsoft InTune. Geben Sie den Verbindungs Namen, die IP-Adresse oder den FQDN des VPN-Servers ein, wählen Sie aus, wie sich Benutzer authentifizieren, und wählen Sie Citrix, SonicWALL, Check Point Capsule und Pulse Secure-Verbindungstypen aus.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a0c11be374e36ec32feb9540f6cfd4f1bc794e9c
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206311"
---
# <a name="android-enterprise-device-settings-to-configure-vpn-in-intune"></a>Android Enterprise-Geräteeinstellungen zum Konfigurieren von VPN in InTune



In diesem Artikel werden die verschiedenen VPN-Verbindungseinstellungen aufgeführt und beschrieben, die Sie auf Android Enterprise-Geräten steuern können. Verwenden Sie diese Einstellungen als Teil ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte), um eine VPN-Verbindung zu erstellen, auszuwählen, wie das VPN authentifiziert wird, und wählen einen VPN-Servertyp aus.

Als Intune-Administrator können Sie für Ihre Android Enterprise-Geräte VPN-Einstellungen erstellen und ihnen zuweisen. 

Weitere Informationen zu VPN-Profilen in InTune finden Sie unter [VPN-profile](vpn-settings-configure.md).

> [!NOTE]
> Zum Konfigurieren des Always on-VPN müssen Sie ein VPN-Profil erstellen und außerdem ein [Geräte Einschränkungs](device-restrictions-android-for-work.md#connectivity) Profil mit der konfigurierten Always on-VPN-Einstellung erstellen.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Gerätekonfigurationsprofil](vpn-settings-configure.md#create-a-device-profile), und klicken Sie auf **Android Enterprise**.

## <a name="device-owner-only"></a>Nur Gerätebesitzer

- **Verbindungsname:** Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die verfügbaren VPN-Verbindungen durchsuchen. Geben Sie beispielsweise `Contoso VPN` ein.
- **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen (FQDN) des VPN-Servers ein, mit dem Geräte eine Verbindung herstellen. Geben Sie beispielsweise **192.168.1.1** oder **vpn.contoso.com** ein.

  - **Authentifizierungsmethode**: Wählen Sie aus, wie sich Geräte beim VPN-Server authentifizieren. Folgende Optionen sind verfügbar:
  
    - **Zertifikate:** Wählen Sie ein vorhandenes SCEP- oder PKCS-Zertifikatprofil zum Authentifizieren der Verbindung aus. Unter [Konfigurieren eines Zertifikatprofils](../protect/certificates-configure.md) werden die Schritte aufgeführt, die zum Erstellen eines Zertifikatprofils erforderlich sind.
    - **Benutzername und Kennwort**: Endbenutzer werden bei der Anmeldung beim VPN-Server dazu aufgefordert, ihren Benutzernamen und ihr Kennwort einzugeben.

- **Verbindungstyp:** Wählen Sie den VPN-Verbindungstyp aus. Folgende Optionen sind verfügbar:

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="work-profile-only"></a>Nur Arbeitsprofil

- **Verbindungsname:** Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die verfügbaren VPN-Verbindungen durchsuchen. Geben Sie beispielsweise `Contoso VPN` ein.
- **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen (FQDN) des VPN-Servers ein, mit dem Geräte eine Verbindung herstellen. Geben Sie beispielsweise **192.168.1.1** oder **vpn.contoso.com** ein.

  - **Authentifizierungsmethode**: Wählen Sie aus, wie sich Geräte beim VPN-Server authentifizieren. Folgende Optionen sind verfügbar:
  
    - **Zertifikate:** Wählen Sie ein vorhandenes SCEP- oder PKCS-Zertifikatprofil zum Authentifizieren der Verbindung aus. Unter [Konfigurieren eines Zertifikatprofils](../protect/certificates-configure.md) werden die Schritte aufgeführt, die zum Erstellen eines Zertifikatprofils erforderlich sind.
    - **Benutzername und Kennwort**: Endbenutzer werden bei der Anmeldung beim VPN-Server dazu aufgefordert, ihren Benutzernamen und ihr Kennwort einzugeben.

- **Verbindungstyp:** Wählen Sie den VPN-Verbindungstyp aus. Folgende Optionen sind verfügbar:

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**
  - **SonicWall Mobile Connect**
  - **Check Point Capsule VPN**

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Sie können auch VPN-Profile für [Android](vpn-settings-android.md)-, [IOS](vpn-settings-ios.md)-, [macOS](vpn-settings-macos.md)-, [Windows 10-und spätere](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md)-und [Windows Phone 8,1](vpn-settings-windows-phone-8-1.md) -Geräte erstellen.
