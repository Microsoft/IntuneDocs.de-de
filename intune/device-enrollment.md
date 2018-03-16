---
title: "Was ist die Microsoft Intune Geräteregistrierung?"
titlesuffix: Microsoft Intune
description: "In diesem Artikel finden Sie Informationen zur Registrierung bei iOS-, Android- und Windows-Geräten."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9f49178a2d8e8a73a693ed2f374b86b8e702680f
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="what-is-device-enrollment"></a>Was ist die Geräteregistrierung?
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune ermöglicht es Ihnen, die Geräte und Apps Ihrer Mitarbeiter sowie deren Zugriff auf Ihre Unternehmensdaten zu verwalten. Damit diese mobile Geräteverwaltung (Mobile Device Management, MDM) genutzt werden kann, müssen die Geräte zunächst beim Intune-Dienst registriert werden. Wenn ein Gerät registriert ist, wird ein MDM-Zertifikat für das Gerät ausgestellt. Dieses Zertifikat wird für die Kommunikation mit dem Intune-Dienst verwendet.

Wie Sie in den folgenden Tabellen erkennen können, gibt es verschiedene Methoden, um die Geräte Ihrer Mitarbeiter zu registrieren. Die einzelnen Methoden hängen vom Gerätebesitz (persönlich oder unternehmenseigen), vom Gerätetyp (iOS, Windows, Android) und den Verwaltungsanforderungen (Zurücksetzungen, Affinität, Sperren) ab.

## <a name="ios-enrollment-methods"></a>iOS-Registrierungsmethoden

| **Methode** |  **Zurücksetzen erforderlich** |    [**Benutzeraffinität**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) |   **Gesperrt** | **Details** |
|:---:|:---:|:---:|:---:|:---:|
| | Geräte werden bei der Registrierung auf die Werkseinstellungen zurückgesetzt. |  Diese Methode ordnet jedes Gerät einem Benutzer zu.| Benutzer können die Registrierung von Geräten nicht aufheben.  | |
|**[BYOD](#bring-your-own-device)** | Nein|   Ja  |   Nein | [Weitere Informationen](./apple-mdm-push-certificate-get.md)|
|**[DEM](#device-enrollment-manager)**| Nein |Nein |Nein  | [Weitere Informationen](./device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**|   Ja  |   Optional |  Optional|[Weitere Informationen](./device-enrollment-program-enroll-ios.md)|
|**[USB (Setup-Assistent)](#usb-sa)**| Ja  |   Optional |  Nein| [Weitere Informationen](./apple-configurator-setup-assistant-enroll-ios.md)|
|**[USB (direkt)](#usb-direct)**| Nein |    Nein  | Nein|[Weitere Informationen](./apple-configurator-direct-enroll-ios.md)|

## <a name="macos-enrollment-methods"></a>macOS-Registrierungsmethoden

| **Methode** |  **Zurücksetzen erforderlich** |  **Benutzeraffinität** | **Gesperrt** | **Details**|
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Nein| Ja  | Nein | [Weitere Informationen](./macos-enroll.md)|
|**[DEM](#device-enrollment-manager)**| Nein |Nein |Nein  | [Weitere Informationen](./device-enrollment-manager-enroll.md)|


## <a name="windows-enrollment-methods"></a>Windows-Registrierungsmethoden

| **Methode** |  **Zurücksetzen erforderlich** |    **Benutzeraffinität**   |   **Gesperrt** | **Details**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Nein |  Ja  |   Nein | [Weitere Informationen](windows-enroll.md)|
|**[DEM](#device-enrollment-manager)**| Nein |Nein |Nein  |[Weitere Informationen](device-enrollment-manager-enroll.md)|
|**Automatische Registrierung** | Nein |Ja  |Nein | [Weitere Informationen](./windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Massenregistrierung** |Nein |Nein |Nein | [Weitere Informationen](./windows-bulk-enroll.md) |

## <a name="android-enrollment-methods"></a>Android-Registrierungsmethoden

| **Methode** |  **Zurücksetzen erforderlich** |    **Benutzeraffinität**   |   **Gesperrt** | **Details**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Nein|   Ja  |   Nein | [Weitere Informationen](./android-enroll.md)|
|**[DEM](#device-enrollment-manager)**| Nein |Nein |Nein  |[Weitere Informationen](./device-enrollment-manager-enroll.md)|
|**Android for Work**| Nein | Ja  | Nein| [Weitere Informationen](./android-enroll.md#enable-enrollment-of-android-for-work-devices) |


## <a name="bring-your-own-device"></a>Bring Your Own Device
Zu BYOD-Geräten (Bring Your Own Device) gehören Mobiltelefone, Tablets und PCs, die persönliches Eigentum der Benutzer sind. Benutzer installieren die Unternehmensportal-App und führen diese zur Registrierung ihrer Geräte aus. Dieses Programm ermöglicht Benutzern den Zugriff auf Unternehmensressourcen wie E-Mails.

## <a name="corporate-owned-device"></a>Unternehmenseigene Geräte
Unternehmenseigene Geräte (Corporate-Owned Devices, COD) umfassen Mobiltelefone, Tablets und PCs, die Eigentum der Organisation sind und an die Mitarbeiter ausgegeben werden. Die Registrierung von COD-Geräten unterstützt Szenarios wie die automatische Registrierung, freigegebene Geräte oder Anforderungen für eine vorab autorisierte Registrierung. Eine Methode zum Registrieren von COD-Geräten besteht darin, dass ein Administrator oder Vorgesetzter den Geräteregistrierungs-Manager verwendet. iOS-Geräte können direkt über die von Apple bereitgestellten Programme zur Geräteregistrierung (Device Enrollment Program, DEP) registriert werden. Geräte mit einer IMEI-Nummer können auch als unternehmenseigene Geräte identifiziert und gekennzeichnet werden.

### <a name="device-enrollment-manager"></a>Geräteregistrierungs-Manager
Der Geräteregistrierungs-Manager (DEM) ist ein besonderes Benutzerkonto, das zum Registrieren und Verwalten mehrerer firmeneigener Geräte verwendet wird. Manager können das Unternehmensportal installieren und viele benutzerlose Geräte registrieren. Erfahren Sie mehr über den [DEM](./device-enrollment-manager-enroll.md).

### <a name="apple-device-enrollment-program"></a>Apple-Programm zur Geräteregistrierung
Mit der Apple DEP-Verwaltung (Device Enrollment Program, Programm zur Geräteregistrierung) können Sie Richtlinien erstellen und „drahtlos“ auf iOS-Geräten bereitstellen, die mit DEP erworben wurden und verwaltet werden. Das Gerät wird beim ersten Einschalten durch den Benutzer registriert und führt dann den iOS-Setup-Assistenten aus. Diese Methode unterstützt den überwachten Modus von iOS, der zulässt, dass ein Gerät mit bestimmten Funktionen konfiguriert wird.

Weitere Informationen zur iOS DEP-Registrierung finden Sie unter:

- [Auswählen der Registrierungsmethode für iOS-Geräte](ios-enroll.md)
- [Registrieren von iOS-Geräten mithilfe des Programms zur Geräteregistrierung](https://docs.microsoft.com/intune/device-restrictions-ios#device-enrollment-program)

### <a name="usb-sa"></a>USB (Setup-Assistent)
IT-Administratoren benutzen Apple Configurator über USB, um jedes unternehmenseigene Gerät manuell für die Registrierung mit dem Setup-Assistenten vorzubereiten. Der IT- Administrator erstellt ein Registrierungsprofil und exportiert dieses in Apple Configurator. Wenn die Benutzer ihre Geräte erhalten, werden sie aufgefordert, den Setup-Assistenten auszuführen. Diese Methode unterstützt den **überwachten iOS-Modus**, der wiederum folgende Funktionen ermöglicht:
  - Gesperrte Registrierung
  - Kioskmodus und andere erweiterte Konfigurationen und Einschränkungen

Weitere Informationen zur Registrierung über den Setup-Assistenten mit iOS Apple Configurator finden Sie unter:

- [Auswählen der Registrierungsmethode für iOS-Geräte](enrollment-method-choose-ios.md)
- [Registrieren von iOS-Geräten mithilfe von Configurator und Setup-Assistent](apple-configurator-setup-assistant-enroll-ios.md)

### <a name="usb-direct"></a>USB (direkt)
Für die direkte Registrierung muss der Administrator jedes Gerät manuell registrieren, indem er eine Registrierungsrichtlinie erstellt und in Apple Configurator exportiert. Über USB angeschlossene, unternehmenseigene Geräte werden direkt registriert, ohne dass ein Zurücksetzen auf Werkseinstellungen erforderlich ist. Geräte werden als benutzerlose Geräte verwaltet. Sie werden nicht gesperrt oder überwacht und unterstützen nicht den bedingten Zugriff, die Erkennung von Jailbreaks oder die Verwaltung mobiler Geräte.

Weitere Informationen zur iOS-Registrierung finden Sie unter:

- [Auswählen der Registrierungsmethode für iOS-Geräte](enrollment-method-choose-ios.md)
- [Registrieren von iOS-Geräten mithilfe von Configurator und direkter Registrierung](apple-configurator-direct-enroll-ios.md)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Verwaltung mobiler Geräte mit Exchange ActiveSync und Intune
Mobile Geräte, die nicht registriert, aber mit Exchange ActiveSync (EAS) verbunden sind, können von Intune mit der EAS-MDM-Richtlinie verwaltet werden. Intune verwendet Exchange Connector für die Kommunikation mit EAS, entweder lokal oder in der Cloud gehostet. Weitere Informationen folgen in Kürze.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Bereinigen mobiler Geräte nach Ablauf des MDM-Zertifikats

Das MDM-Zertifikat wird automatisch erneuert, wenn mobile Geräte mit dem Intune-Dienst kommunizieren. Wenn mobile Geräte zurückgesetzt werden oder für längere Zeit keine Kommunikation mit dem Intune-Dienst stattfindet, wird das MDM-Zertifikat nicht verlängert. Das Gerät wird 180 Tage nach Ablauf des MDM-Zertifikats aus dem Azure-Portal entfernt.
