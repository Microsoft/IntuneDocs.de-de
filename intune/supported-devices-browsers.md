---
title: "Von Microsoft Intune unterstützte Betriebssysteme und Browser"
titleSuffix: 
description: "Liste der unterstützten Geräteplattformen und Browser für die Intune-Geräteverwaltung"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/03/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1e58201620612118f0984a1c477b3fa3bc7e923a
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="supported-operating-systems-and-browsers"></a>Unterstützte Betriebssysteme und Browser

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Informieren Sie sich über die unterstützten Betriebssysteme und Browser, bevor Sie Microsoft Intune einrichten.

Hilfe zur Installation von Intune auf Ihrem Gerät finden Sie unter [Verwenden verwalteter Geräte zum Erledigen von Aufgaben](/intune-user-help/company-portal-frequently-asked-questions). Sie sollten sich auch mit der [Bandbreitennutzung von Intune](network-bandwidth-use.md) ([klassisches Portal](/intune-classic/get-started/network-bandwidth-use)) vertraut machen.

## <a name="intune-supported-operating-systems"></a>Von Intune unterstützte Betriebssysteme

Sie können die Geräte verwalten, die folgende Betriebssysteme verwenden:

[!INCLUDE[mdm-supported-devices](./includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>Unterstützte Samsung KNOX Standard-Geräte

Die Unternehmensportal-App führt während der MDM-Registrierung nur dann einen Aktivierungsversuch für Samsung KNOX durch, wenn das Gerät in der [Liste der unterstützten KNOX-Geräte](https://www.samsungknox.com/knox-supported-devices/knox-workspace) angezeigt wird. Dadurch werden bei KNOX Aktivierungsfehler vermieden, die eine MDM-Registrierung verhindern würden. Geräte, die die Samsung KNOX-Aktivierung nicht unterstützen, werden als Android-Standardgeräte registriert. Wenn für ein Samsung-Gerät mehrere Modellnummern vorhanden sind, wird KNOX möglicherweise nicht von allen Modellen unterstützt. Überprüfen Sie daher mithilfe des Wiederverkäufers Ihrer Geräte, ob diese mit KNOX kompatibel sind, bevor Sie Samsung-Geräte erwerben und bereitstellen.

> [!NOTE]
> Für die Registrierung von Samsung KNOX-Geräten müssen Sie möglicherweise [den Zugriff auf Samsung-Servern aktivieren](https://support.samsungknox.com/hc/articles/115013833108-Our-corporate-devices-are-behind-a-firewall-How-do-I-enable-Knox-Workspace-devices-to-contact-Samsung-servers). 

In der folgenden Liste werden Samsung-Gerätemodelle aufgeführt, die KNOX nicht unterstützen und von der Unternehmensportal-App für Android als native Android-Geräte registriert werden:

| **Gerätename** | **Gerätemodellnummern** |
| --- | --- |
| Galaxy Avant | SM-G386T |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W |
| Galaxy S6 Edge | 404SC |
| Galaxy Tab A 7.0&quot; | SM-T280<br>SM-T285 |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116<br>SM-T210<br>SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |


### <a name="windows-pc-software-client"></a>Softwareclient für Windows-PCs

Ein [Intune-Softwareclient](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) auf Windows-PCs als eine alternative Registrierungsmethode bereitgestellt und installiert werden. Diese Funktionalität ist nur im klassischen Intune-Portal verfügbar. Sie können den Intune-Softwareclient zum Verwalten von PCs mit Windows 7 und höher (mit Ausnahme der Windows 10 Home-Edition) verwenden.

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Von Intune unterstützte Webbrowser

Für verschiedene Verwaltungsaufgaben müssen Sie eine der folgenden Verwaltungswebsites verwenden.

- [Office 365-Portal](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Azure-Portal](https://portal.azure.com/)

Für diese Portale werden die folgenden Browser unterstützt:
- Microsoft Edge (neueste Version)
- Microsoft Internet Explorer 11
- Safari (neueste Version, nur auf Mac)
- Chrome (neueste Version)
- Mozilla Firefox mit aktiviertem Silverlight – [weitere Informationen (Versionen vor Version 52)](https://go.microsoft.com/fwlink/?linkid=836872)




### <a name="intune-classic-portal"></a>Klassisches Intune-Portal

Die klassischen Intune-Funktionen wie der Intune PC-Softwareclient und die Integration von Mobile Threat Defense-Partnern sind nur im klassischen Intune-Portal (https://manage.microsoft.com) verfügbar. Das klassische Intune-Portal erfordert Silverlight-Browserunterstützung.

Die folgenden Silverlight-Browser unterstützen die Intune-Konsole:
- Internet Explorer 10 oder höher
- Google Chrome (Versionen vor Version 42)
- Mozilla Firefox mit aktiviertem Silverlight – [weitere Informationen](https://go.microsoft.com/fwlink/?linkid=836872)

> [!Note]
> Microsoft Edge und mobile Browser werden im klassischen Intune-Portal nicht unterstützt, da sie [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx) nicht unterstützen.

Lediglich Benutzer mit Dienstadministratorrechten oder Mandantenadministratoren mit globaler Administratorrolle können sich bei diesem Portal anmelden. Für den Zugriff auf die Administratorkonsole sind für Ihr Konto eine Lizenz zur Verwendung von Intune und der Anmeldestatus **Zugelassen** erforderlich.
