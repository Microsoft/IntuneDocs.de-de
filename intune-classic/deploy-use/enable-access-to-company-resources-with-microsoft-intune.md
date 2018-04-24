---
title: Aktivieren des Zugriffs auf Unternehmensressourcen
description: Die WLAN-, VPN- und E-Mail-Profile greifen ineinander, um Ihre Benutzer beim Zugriff auf die Dateien und Ressourcen, die sie benötigen, zu unterstützen.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/02/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3dd8dd4e-e165-4d0c-97b7-b3e86ebab909
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5bfc02f5f10ce88b992d0ea250d7b36fdf3f66dc
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="enable-access-to-company-resources-with-microsoft-intune"></a>Aktivieren des Zugriffs auf Unternehmensressourcen mit Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Die WLAN-, VPN- und E-Mail-Profile von Microsoft Intune greifen ineinander, um Ihre Benutzer beim Zugriff auf die Dateien und Ressourcen, die sie für ihre Arbeit benötigen, zu unterstützen, unabhängig davon, wo sie gespeichert sind. Dieser Zugriff wird mithilfe von Zertifikatprofilen gesichert.

## <a name="wi-fi-profileswi-fi-connections-in-microsoft-intunemd-and-supported-platforms"></a>[WLAN-Profile](wi-fi-connections-in-microsoft-intune.md) und unterstützte Plattformen

Bereitstellen von Einstellungen für drahtlose Netzwerke für Ihre Benutzer. Diese Einstellungen erleichtern Ihren Benutzern die Verbindung mit dem Unternehmensnetzwerk.
#### <a name="supported-platforms"></a>Unterstützte Plattformen

|Windows 8.1 und höher|Windows Phone 8.1 und höher|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|Ja (Sie können ein Windows-WLAN-Profil importieren.)|Ja (Sie können OMA-URI konfigurieren.) |Ja |Ja |Ja |

## <a name="vpn-profilesvpn-connections-in-microsoft-intunemd-and-supported-platforms"></a>[VPN-Profile](vpn-connections-in-microsoft-intune.md) und unterstützte Plattformen
Stellen Sie Einstellungen für ein virtuelles privates Netzwerk (VPN) für Ihre Benutzer bereit. Diese Einstellungen erleichtern Ihren Benutzern die Verbindung mit Ressourcen im Unternehmensnetzwerk.

|Windows 8.1 und höher|Windows Phone 8.1 und höher|iOS|Android|Samsung KNOX Standard|
|---------------------|---------------------------|---|-------|------------|
|Ja |Ja |Ja |Ja |Ja |

## <a name="email-profilesconfigure-access-to-corporate-email-using-email-profiles-with-microsoft-intunemd-and-supported-platforms"></a>[E-Mail-Profile](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md) und unterstützte Plattformen
Erstellen, Bereitstellen und Überwachen von nativen E-Mail-Clienteinstellungen auf den Geräten in Ihrer Organisation.


| Windows 8.1 und höher | Windows Phone 8.1 und höher | iOS | Android | Samsung KNOX Standard |
|-----------------------|-----------------------------|-----|---------|-----------------------|
|          Nein           |             Ja              | Ja  |   Nein    |          Ja           |

> [!NOTE]
> [Dieser Beitrag im Intune-Teamblog](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/19/using-oma-uri-to-create-custom-wi-fi-profiles-for-windows-phone-8-1/) enthält Informationen zum Konfigurieren von Windows Phone 8.1-WLAN-Profilen mithilfe von OMA-URI.

## <a name="certificate-profilessecure-resource-access-with-certificate-profilesmd-and-supported-platforms"></a>[Zertifikatprofile](secure-resource-access-with-certificate-profiles.md) und unterstützte Plattformen
Ermöglichen den sicheren Zugriff auf Unternehmensressourcen einschließlich Drahtlosnetzwerken und VPN-Verbindungen.


| Windows 8.1 und höher | Windows Phone 8.1 und höher | iOS | Android | Samsung KNOX Standard |
|-----------------------|-----------------------------|-----|---------|-----------------------|
|          Ja           |             Ja              | Ja  |   Ja    |          Ja           |

