---
title: Verwenden von VPN-Einstellungen für Android-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Sehen Sie sich alle Einstellungen zum Erstellen von VPN-Verbindungen auf Android-Geräten in Microsoft InTune an. Geben Sie den Verbindungs Namen, die IP-Adresse oder den FQDN des VPN-Servers ein, wählen Sie aus, wie sich Benutzer authentifizieren, und wählen Sie Citrix, SonicWALL, Check Point Capsule und Pulse Secure-Verbindungstypen aus.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7f9945198f8ed575b26762c1f8f356885d5b9dc5
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734179"
---
# <a name="android-device-settings-to-configure-vpn-in-intune"></a>Android-Geräteeinstellungen zum Konfigurieren von VPN in InTune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In diesem Artikel werden die verschiedenen VPN-Verbindungseinstellungen aufgeführt und beschrieben, die Sie auf Android-Geräten steuern können. Verwenden Sie diese Einstellungen als Teil ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte), um eine VPN-Verbindung zu erstellen, auszuwählen, wie das VPN authentifiziert wird, und wählen einen VPN-Servertyp aus.

Als Intune-Administrator können Sie für Ihre Android-Geräte diese VPN-Einstellungen erstellen und ihnen zuweisen. 

Weitere Informationen zu VPN-Profilen in InTune finden Sie unter [VPN-profile](vpn-settings-configure.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Gerätekonfigurationsprofil](vpn-settings-configure.md#create-a-device-profile), und klicken Sie auf **Android**.

## <a name="base-vpn"></a>Basis-VPN

- **Verbindungsname**: Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die verfügbaren VPN-Verbindungen durchsuchen. Geben Sie beispielsweise `Contoso VPN` ein.
- **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen (FQDN) des VPN-Servers ein, mit dem Geräte eine Verbindung herstellen. Geben Sie beispielsweise **192.168.1.1** oder **vpn.contoso.com** ein.

  - **Authentifizierungsmethode:** Wählen Sie aus, wie sich Geräte beim VPN-Server authentifizieren. Folgende Optionen sind verfügbar:

    - **Zertifikate:** Wählen ein vorhandenes SCEP- oder PKCS-Zertifikatprofil zum Authentifizieren der Verbindung aus. Unter [Konfigurieren eines Zertifikatprofils](../protect/certificates-configure.md) werden die Schritte aufgeführt, die zum Erstellen eines Zertifikatprofils erforderlich sind.
    - **Benutzername und Kennwort:** Endbenutzer werden bei der Anmeldung beim VPN-Server dazu aufgefordert, ihren Benutzernamen und ein Kennwort einzugeben.

- **Verbindungstyp:** Wählen Sie den VPN-Verbindungstyp aus. Folgende Optionen sind verfügbar:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**
  - **Citrix SSO**

- **Fingerabdruck** (nur Check Point Capsule-VPN): Geben Sie eine Zeichenfolge (z.B. **Contoso-Fingerabdruckcode**) ein, um zu überprüfen, ob der VPN-Server vertrauenswürdig ist. Ein Fingerabdruck wird an den Client gesendet, sodass der Client weiß, dass jeder Server mit dem gleichen Fingerabdruck vertraut werden kann. Wenn das Gerät nicht über den Fingerabdruck verfügt, wird der Benutzer dazu aufgefordert, dem VPN-Server zu vertrauen, während der Fingerabdruck angezeigt wird. Der Benutzer überprüft den Fingerabdruck manuell und wählt „Vertrauen“ aus, um die Verbindung herzustellen.
- **Geben Sie Schlüssel-Wert-Paare für die Citrix-VPN-Attribute ein** (nur Citrix): Geben Sie von Citrix bereitgestellte Schlüssel-Wert-Paare ein. Durch diese Werte werden die Eigenschaften der VPN-Verbindung konfiguriert. 

  Sie können auch eine durch Trennzeichen getrennte Datei (CSV-Datei) mit Schlüssel-Wert-Paaren **importieren** . Überprüfen Sie, ob **meine Daten über Header** und **Schlüssel** Eigenschaften verfügen.

  Nachdem Sie die Schlüssel-und Wertepaare hinzugefügt haben, verwenden Sie **exportieren** , um Ihre Daten in einer CSV-Datei zu sichern.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Sie können auch VPN-Profile für [Android Enterprise](vpn-settings-android-enterprise.md)-, [IOS](vpn-settings-ios.md)-, [macOS](vpn-settings-macos.md)-, [Windows 10-und spätere](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md)-und [Windows Phone 8,1](vpn-settings-windows-phone-8-1.md) -Geräte erstellen.
