---
title: Verwenden von VPN-Einstellungen für Android-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Lernen Sie alle Einstellungen kennen, die Sie zum Erstellen von VPN-Verbindungen auf Android-Geräten in Microsoft Intune benötigen. Geben Sie den Namen der Verbindung und die IP-Adresse oder FQDN des VPN-Servers ein. Wählen Sie die Art der Authentifizierung von Benutzern sowie die Verbindungstypen Citrix, SonicWall, Check Point Capsule und Pulse Secure aus.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3f82cc74aa2e351ee63ffba2629e9ddddb57fc76
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512516"
---
# <a name="android-device-settings-to-configure-vpn-in-intune"></a>Android-Geräteeinstellungen zur VPN-Konfiguration in Intune

In diesem Artikel werden die verschiedenen VPN-Verbindungseinstellungen aufgeführt und beschrieben, die Sie auf Android-Geräten steuern können. Verwenden Sie diese Einstellungen als Teil Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte), um etwa eine VPN-Verbindung zu erstellen und die Art der Authentifizierung sowie den VPN-Servertyp auszuwählen.

Als Intune-Administrator können Sie für Ihre Android-Geräte diese VPN-Einstellungen erstellen und ihnen zuweisen. 

Weitere Informationen zu VPN-Profilen in Intune finden Sie unter [VPN-Profile](vpn-settings-configure.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Gerätekonfigurationsprofil](vpn-settings-configure.md#create-a-device-profile), und klicken Sie auf **Android**.

## <a name="base-vpn"></a>Basis-VPN

- **Verbindungsname:** Geben Sie einen Namen für diese Verbindung ein. Benutzern wird dieser Name angezeigt, wenn sie auf ihrem Gerät die verfügbaren VPN-Verbindungen durchsuchen. Geben Sie beispielsweise `Contoso VPN` ein.
- **IP-Adresse oder FQDN:** Geben Sie die IP-Adresse oder den vollqualifizierten Domänennamen (FQDN) des VPN-Servers ein, mit dem Geräte eine Verbindung herstellen. Geben Sie beispielsweise **192.168.1.1** oder **vpn.contoso.com** ein.

  - **Authentifizierungsmethode**: Wählen Sie aus, wie sich Geräte beim VPN-Server authentifizieren. Folgende Optionen sind verfügbar:

    - **Zertifikate:** Wählen Sie ein vorhandenes SCEP- oder PKCS-Zertifikatprofil zum Authentifizieren der Verbindung aus. Unter [Konfigurieren eines Zertifikatprofils](../protect/certificates-configure.md) werden die Schritte aufgeführt, die zum Erstellen eines Zertifikatprofils erforderlich sind.
    - **Benutzername und Kennwort**: Endbenutzer werden bei der Anmeldung beim VPN-Server dazu aufgefordert, ihren Benutzernamen und ihr Kennwort einzugeben.

- **Verbindungstyp:** Wählen Sie den VPN-Verbindungstyp aus. Folgende Optionen sind verfügbar:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**
  - **Citrix SSO**

- **Fingerabdruck** (Nur Check Point Capsule VPN): Geben Sie eine Zeichenfolge (z.B. **Contoso-Fingerabdruckcode**) ein, um zu überprüfen, ob der VPN-Server vertrauenswürdig ist. Ein Fingerabdruck wird an den Client gesendet, damit dieser weiß, dass alle Server vertrauenswürdig sind, die den gleichen Fingerabdruck vorweisen. Wenn das Gerät nicht über den Fingerabdruck verfügt, wird der Benutzer dazu aufgefordert, dem VPN-Server zu vertrauen, während der Fingerabdruck angezeigt wird. Der Benutzer überprüft den Fingerabdruck manuell und wählt „Vertrauen“ aus, um die Verbindung herzustellen.
- **Geben Sie Schlüssel-Wert-Paare für die Citrix-VPN-Attribute ein** (nur Citrix): Geben Sie von Citrix bereitgestellte Schlüssel-Wert-Paare ein. Durch diese Werte werden die Eigenschaften der VPN-Verbindung konfiguriert. 

  Sie können auch eine durch Trennzeichen getrennte Datei (.csv) mit Schlüssel-Wert-Paaren **importieren**. Überprüfen Sie die Eigenschaften **Meine Daten haben Überschriften** und **Schlüssel**.

  Nachdem Sie die Schlüssel-Wert-Paare hinzugefügt haben, sichern Sie Ihre Daten mithilfe von **Exportieren** in einer CSV-Datei.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Sie können VPN-Profile auch für Geräte erstellen, die unter [Android Enterprise](vpn-settings-android-enterprise.md), [iOS/iPadOS](vpn-settings-ios.md), [macOS](vpn-settings-macos.md), [Windows 10 und höher](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md) sowie [Windows Phone 8.1](vpn-settings-windows-phone-8-1.md) ausgeführt werden.
