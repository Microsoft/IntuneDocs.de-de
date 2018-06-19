---
title: Registrieren von Geräten
description: Die Registrierung durch die Verwaltung mobiler Geräte (MDM) dient dazu, Geräte in die Verwaltung aufzunehmen und den Zugriff auf Ressourcen zu ermöglichen.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 09/22/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3cae9bc1b76dba3b896957f60ca08cca53423267
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31026980"
---
# <a name="enroll-devices-for-management-in-intune"></a>Registrieren von Geräten für die Verwaltung in Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Sie können Geräte, einschließlich Windows PCs, registrieren, um die Verwaltung mobiler Geräte (MDM, Mobile Device Management) mit Microsoft Intune zu aktivieren. Dieses Thema beschreibt die verschiedenen Methoden zum Registrieren von mobilen Geräten in der Intune-Verwaltung. Auf welche Weise Sie Ihre Geräte registrieren, hängt von Gerätetyp, Besitz und benötigtem Verwaltungsniveau ab. Bei der BYOD-Registrierung (Bring Your Own Device, private Geräte der Mitarbeiter) können die Benutzer ihre privaten Smartphones, Tablets oder PCs selbst registrieren. Die Registrierung von unternehmenseigenen Geräten (corporate-owned devices, COD) macht Verwaltungsszenarios wie die automatische Registrierung, freigegebene Geräte oder Anforderungen für eine vorautorisierte Registrierung möglich.

Wenn Sie [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune) entweder lokal oder in der Cloud gehostet verwenden, können Sie eine einfache Intune-Verwaltung ohne Registrierung aktivieren. Auch Windows-PCs können mit [Intune-Clientsoftware](#windows-pc-management-with-intune) verwaltet werden.

Standardmäßig dürfen Geräte für alle Plattformen in Intune registriert werden. Um Geräte für die Registrierung zu blockieren, melden Sie sich mit Ihren Administratoranmeldeinformationen im [Microsoft Intune-Verwaltungsportal](https://manage.microsoft.com) an. Wählen Sie **Admin**(Administrator) > **Verwaltung mobiler Geräte** > **Registrierungsregeln** aus, und deaktivieren Sie die entsprechenden Kontrollkästchen, die Sie blockieren möchten.

## <a name="overview-of-device-enrollment-methods"></a>Übersicht über die Geräteregistrierungsmethoden

Die folgende Tabelle zeigt Intune-Registrierungsmethoden und die unterstützten Funktionen und Anforderungen der einzelnen Methoden. Die Funktionen und Anforderungen werden nachfolgend beschrieben.

- **Zurücksetzen** – Gibt an, ob das Gerät zurückgesetzt werden muss, bevor Benutzer das Gerät registrieren können. Der Begriff „Zurücksetzen“ bedeutet die Zurücksetzung des Geräts auf Werkseinstellungen, wobei alle Daten entfernt werden. Weitere Informationen finden Sie auf der Seite [Abkoppeln von Geräten von der Intune-Verwaltung](retire-devices-from-microsoft-intune-management.md).
- **Affinität** – Ordnet Geräte Benutzern zu. Für die Verwaltung mobiler Geräte (MAM, Mobile Application Management) und den bedingten Zugriff auf Unternehmensdaten erforderlich. Weitere Informationen finden Sie auf der Seite [Registrieren firmeneigener iOS-Geräte in Microsoft Intune](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices).
- **Sperren**: Zeigt an, wenn Benutzer daran gehindert werden, die Registrierung ihrer Geräte mit nativen Betriebssystemsmenüs aufzuheben. Benutzer können die Registrierung ihrer Geräte auf allen Plattformen mithilfe ihrer Unternehmensportal-App aufheben.

**iOS-Registrierungsmethoden**

| **Methode** |  **Zurücksetzen erforderlich?** |    **Affinität**    |   **Sperren** | **Details** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nein|    Ja  |   Nein | [Weitere Informationen](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   Nein |Nein |Nein  | [Weitere Informationen](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   Ja  |   Optional |  Optional|[Weitere Informationen](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB (Setup-Assistent)](#usb-sa)**| Ja  |   Optional |  Nein| [Weitere Informationen](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB (direkt)](#usb-direct)**| Nein |    Nein  | Nein|[Weitere Informationen](ios-direct-enrollment-in-microsoft-intune.md)|

**Windows-Registrierungsmethoden**

| **Methode** |  **Zurücksetzen erforderlich?** |    **Affinität**    |   **Sperren** | **Details**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nein|    Ja  |   Nein | [Weitere Informationen](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   Nein |Nein |Nein  |[Weitere Informationen](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Android-Registrierungsmethoden**

| **Methode** |  **Zurücksetzen erforderlich?** |    **Affinität**    |   **Sperren** | **Details**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nein|    Ja  |   Nein | [Weitere Informationen](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   Nein |Nein |Nein  |[Weitere Informationen](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Android for Work-Registrierungsmethoden**

| **Methode** |  **Zurücksetzen erforderlich?** |    **Affinität**    |   **Sperren** | **Details**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nein|    Ja  |   Nein | [Weitere Informationen](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   Nein |Nein |Nein  |[Weitere Informationen](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**macOS-Registrierungsmethoden**

| **Methode** |  **Zurücksetzen erforderlich?** |    **Affinität**    |   **Sperren** | **Details**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nein|    Ja  |   Nein | [Weitere Informationen](prerequisites-for-enrollment.md)|


Eine Reihe von Fragen, die Sie beim Ermitteln der richtigen Methode unterstützen, finden Sie unter [Auswählen der Registrierungsart von Geräten](/intune-classic/get-started/choose-how-to-enroll-devices1).

## <a name="byod"></a>BYOD
BYOD-Benutzer installieren die Unternehmensportal-App und registrieren ihr Gerät. Dadurch können Benutzer Verbindungen mit dem Unternehmensnetzwerk herstellen und zur Domäne oder zu Azure Active Directory beitreten. Für die meisten Plattformen müssen Sie BYOD-Registrierung für viele COD-Szenarios ermöglichen. Weitere Informationen finden Sie unter [Voraussetzungen für die Verwaltung von mobilen Geräten in Intune](prerequisites-for-enrollment.md). ([Zurück zur Tabelle](#overview-of-device-enrollment-methods))

## <a name="corporate-owned-devices"></a>Firmeneigene Geräte
Firmeneigene Geräte (Corporate-owned devices, COD) können mithilfe der Intune-Konsole verwaltet werden. iOS-Geräte können direkt über die von Apple bereitgestellten Tools registriert werden. Alle Gerätetypen können von einem Administrator oder Manager die unter Verwendung des Geräteregistrierungs-Managers registriert werden. Geräte mit einer IMEI-Nummer können auch als firmeneigene Geräte identifiziert und gekennzeichnet werden, um COD-Szenarien zu unterstützen.

Weitere Informationen finden Sie unter [Registrieren firmeneigener Geräte bei Microsoft Intune](manage-corporate-owned-devices.md).

### <a name="dem"></a>Geräteregistrierungs-Manager (DEM)
Der Geräteregistrierungs-Manager ist ein besonderes Intune-Konto, das zum Registrieren und Verwalten mehrere firmeneigener Geräte verwendet wird. Manager können das Unternehmensportal installieren und viele benutzerlose Geräte registrieren. Erfahren Sie mehr über den [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Zurück zur Tabelle](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP (Device Enrollment Program)
Mit der Apple DEP-Verwaltung (Device Enrollment Program, Programm zur Geräteregistrierung) können Sie Richtlinien erstellen und „drahtlos“ auf iOS-Geräten bereitstellen, die mit DEP erworben wurden und verwaltet werden. Das Gerät wird beim ersten Einschalten durch den Benutzer registriert und führt dann den iOS-Setup-Assistenten aus. Diese Methode unterstützt den iOS-Modus **Überwacht**, der wiederum Folgendes ermöglicht:
  - Gesperrte Registrierung
  - Kioskmodus und andere erweiterte Konfigurationen und Einschränkungen

Erfahren Sie mehr über das [Geräteregistrierungsprogramm](ios-device-enrollment-program-in-microsoft-intune.md). ([Zurück zur Tabelle](#overview-of-device-enrollment-methods))

### <a name="usb-sa"></a>USB (Setup-Assistent)
IT-Administratoren benutzen den Apple Configurator über USB, um jedes unternehmenseigene Gerät manuell für die Registrierung mit dem Setup-Assistenten vorzubereiten. Der IT- Administrator erstellt ein Registrierungsprofil und exportiert dieses in Apple Configurator. Wenn die Benutzer ihre Geräte erhalten, werden sie aufgefordert, den Setup-Assistenten auszuführen. Diese Methode unterstützt den iOS-Modus **Überwacht**, der wiederum Folgendes ermöglicht:
  - Gesperrte Registrierung
  - Kioskmodus und andere erweiterte Konfigurationen und Einschränkungen

Erfahren Sie mehr über die [Registrierung über den Setup-Assistenten mit Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Zurück zur Tabelle](#overview-of-device-enrollment-methods))

### <a name="usb-direct"></a>USB (direkt)
Für die direkte Registrierung muss der Administrator jedes Gerät manuell registrieren, indem er eine Registrierungsrichtlinie erstellt und in Apple Configurator exportiert. Über USB angeschlossene, unternehmenseigene Geräte werden direkt registriert, ohne dass ein Zurücksetzen auf Werkseinstellungen erforderlich ist. Geräte werden als benutzerlose Geräte verwaltet. Sie werden nicht gesperrt oder überwacht und unterstützen nicht den bedingten Zugriff, die Erkennung von Jailbreaks oder die Verwaltung mobiler Geräte.  Erfahren Sie mehr über die [direkte Registrierung mit Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Zurück zur Tabelle](#overview-of-device-enrollment-methods))

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Verwaltung mobiler Geräte mit Exchange ActiveSync und Intune
Mobile Geräte, die nicht registriert, aber mit Exchange ActiveSync (EAS) verbunden sind, können von Intune mit der MDM EAS-Richtlinie verwaltet werden. Intune verwendet Exchange Connector für die Kommunikation mit EAS, entweder lokal oder in der Cloud gehostet. Weitere Informationen finden Sie unter [Verwaltung mobiler Geräte mit Exchange ActiveSync und Microsoft Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md).


## <a name="windows-pc-management-with-intune"></a>Aktivieren der Windows PC-Verwaltung mit Intune  
Sie können Microsoft Intune auch verwenden, um Windows-PCs mit der Intune-Clientsoftware zu verwalten. Mit dem Intune-Client verwaltete PCs können:

 - Software- und Hardwareinventurberichte erstellen
 - Desktopanwendung installieren (z. B. EXE- und MSI-Dateien)
 - Verwalten von Firewall-Einstellungen

PCs, die mit der Intune-Clientsoftware verwaltet werden, können nicht vollständig zurückgesetzt werden, obwohl das selektive Zurücksetzen verfügbar ist. Mit dem Intune-Softwareclient verwaltete PCs können viele der Intune Verwaltungsfunktionen wie z.B. den bedingten Zugriff, VPN- und WLAN-Einstellungen oder die Bereitstellung von Zertifikaten und E-Mail-Konfigurationen nicht nutzen. Weitere Informationen finden Sie unter [Verwalten von Windows-PCs mit der Intune-PC-Clientsoftware](manage-windows-pcs-with-microsoft-intune.md).

## <a name="supported-device-platforms"></a>Unterstützte Geräteplattformen

Intune kann folgende Geräteplattformen verwalten:

[!INCLUDE [mdm-supported-devices](../includes/mdm-supported-devices.md)]

## <a name="next-steps"></a>Nächste Schritte
- [Prerequisites for device enrollment( Voraussetzungen für die Geräteregistrierung)](prerequisites-for-enrollment.md)
- [Verwalten firmeneigener Geräte](manage-corporate-owned-devices.md)
- [Unterstützte mobile Geräte und Computer](/intune/supported-devices-browsers#intune-supported-devices)
