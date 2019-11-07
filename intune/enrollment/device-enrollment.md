---
title: Was ist die Microsoft Intune Geräteregistrierung?
titleSuffix: Microsoft Intune
description: In diesem Artikel finden Sie Informationen zur Registrierung bei iOS-, Android- und Windows-Geräten.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 4/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: bb9aa6349a88f226c063703d6cb035b3c89636fd
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503254"
---
# <a name="what-is-device-enrollment"></a>Was ist die Geräteregistrierung?
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune ermöglicht es Ihnen, die Geräte und Apps Ihrer Mitarbeiter sowie deren Zugriff auf Ihre Unternehmensdaten zu verwalten. Damit diese mobile Geräteverwaltung (Mobile Device Management, MDM) genutzt werden kann, müssen die Geräte zunächst beim Intune-Dienst registriert werden. Wenn ein Gerät registriert ist, wird ein MDM-Zertifikat für das Gerät ausgestellt. Dieses Zertifikat wird für die Kommunikation mit dem Intune-Dienst verwendet.

Wie Sie in den folgenden Tabellen erkennen können, gibt es verschiedene Methoden, um die Geräte Ihrer Mitarbeiter zu registrieren. Die einzelnen Methoden hängen vom Gerätebesitz (persönlich oder unternehmenseigen), vom Gerätetyp (iOS, Windows, Android) und den Verwaltungsanforderungen (Zurücksetzungen, Affinität, Sperren) ab.

Standardmäßig dürfen Geräte für alle Plattformen in Intune registriert werden. Jedoch können Sie [Geräte nach Plattform einschränken](enrollment-restrictions-set.md#create-a-device-type-restriction).

## <a name="ios-enrollment-methods"></a>iOS-Registrierungsmethoden

| **Methode** | **Zurücksetzen erforderlich** | [**Benutzeraffinität**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) | **Gesperrt** | **Details** |
|:---:|:---:|:---:|:---:|:---:|
| | Geräte werden während der Registrierung auf die Werkseinstellungen zurückgesetzt. | Diese Methode ordnet jedes Gerät einem Benutzer zu.| Falls dies der Fall ist, können Benutzer die Registrierung von Geräten nicht aufheben. | |
|**[BYOD](#bring-your-own-device)** | Nein| Ja | Nein | [Weitere Informationen](apple-mdm-push-certificate-get.md)|
|**[DEM](#device-enrollment-manager)**| Nein |Nein |Nein | [Weitere Informationen](device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**| Ja | Optional | Optional|[Weitere Informationen](device-enrollment-program-enroll-ios.md)|
|**[USB (Setup-Assistent)](#usb-sa)**| Ja | Optional | Nein| [Weitere Informationen](apple-configurator-enroll-ios.md)|
|**[USB (direkt)](#usb-direct)**| Nein | Nein | Nein|[Weitere Informationen](apple-configurator-enroll-ios.md)|

## <a name="macos-enrollment-methods"></a>macOS-Registrierungsmethoden
| **Methode** |  **Zurücksetzen erforderlich** |  **Benutzeraffinität** | **Gesperrt** | **Details**|
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Nein| Ja | Nein | [Weitere Informationen](macos-enroll.md)|
|**[DEM](#device-enrollment-manager)**| Nein |Nein |Nein  | [Weitere Informationen](device-enrollment-manager-enroll.md)|
|**[DEP](#apple-device-enrollment-program)**| Ja | Optional | Optional|[Weitere Informationen](device-enrollment-program-enroll-macos.md)|

## <a name="windows-enrollment-methods"></a>Windows-Registrierungsmethoden

| **Methode** | **Zurücksetzen erforderlich** | **Benutzeraffinität** | **Gesperrt** | **Details**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Nein | Ja | Nein | [Weitere Informationen](windows-enroll.md)|
|**[DEM](#device-enrollment-manager)**| Nein |Nein |Nein |[Weitere Informationen](device-enrollment-manager-enroll.md)|
|**Automatische Registrierung** | Nein |Ja |Nein | [Weitere Informationen](windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Autopilot** |Ja |Ja |Nein | [Weitere Informationen](enrollment-autopilot.md)
|**Massenregistrierung** |Nein |Nein |Nein | [Weitere Informationen](windows-bulk-enroll.md) |
|**Co-Verwaltung** |Nein |Ja |Nein | [Weitere Informationen](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)
|**GPO** |Nein |Ja |Nein | [Weitere Informationen](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)

## <a name="android-enrollment-methods"></a>Android-Registrierungsmethoden

| **Privat** | **Registrierungsmethoden** | **Zurücksetzen erforderlich** | **Benutzeraffinität** | **Gesperrt** | **Details**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Android-Geräteadministrator**|**Benutzerinitiiert über Unternehmensportal** | Nein | Ja | Nein | [Weitere Informationen](https://docs.microsoft.com/intune-user-help/enroll-device-android-company-portal)|
|**Android Enterprise-Arbeitsprofil**|**Benutzerinitiiert über Unternehmensportal**| Nein | Ja | Nein | [Weitere Informationen](android-work-profile-enroll.md)|


| **Unternehmen** | **Registrierungsmethoden** | **Zurücksetzen erforderlich** | **Benutzeraffinität** | **Gesperrt** | **Details**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Android-Geräteadministrator**|**[DEM](#device-enrollment-manager)-initiiert über Unternehmensportal**| Nein | Nein | Nein |[Weitere Informationen](device-enrollment-manager-enroll.md)|
|**Android-Geräteadministrator**|**(Vordeklarierte IMEI oder SN) Benutzerinitiiert über Unternehmensportal**| Nein | Ja | Nein | [Weitere Informationen](./../corporate-identifiers-add.md)|
|**Android-Geräteadministrator mit Zebra Mobility-Erweiterungen**|**Benutzer- oder [DEM](#device-enrollment-manager)-initiiert über Unternehmensportal**| Nein | Ja, wenn benutzerinitiiert; Nein, wenn [DEM](#device-enrollment-manager)-initiiert | Nein | [Weitere Informationen](../configuration/android-zebra-mx-overview.md)|
|**Android Enterprise Dedicated**|**NFC, Token, QR-Code, Zero Touch**| Ja | Nein | Konfigurierbar über Richtlinie | [Weitere Informationen](android-kiosk-enroll.md)|
|**Vollständig verwaltetes Android Enterprise**|**NFC, Token, QR-Code, Zero Touch**| Ja | Ja | Konfigurierbar über Richtlinie | [Weitere Informationen](android-dedicated-devices-fully-managed-enroll.md)|


## <a name="bring-your-own-device"></a>Bring Your Own Device
Zu BYOD-Geräten (Bring Your Own Device) gehören Mobiltelefone, Tablets und PCs, die persönliches Eigentum der Benutzer sind. Benutzer installieren die Unternehmensportal-App und führen diese zur Registrierung ihrer Geräte aus. Dieses Programm ermöglicht Benutzern den Zugriff auf Unternehmensressourcen wie E-Mails.

## <a name="corporate-owned-device"></a>Unternehmenseigene Geräte
[Unternehmenseigene Geräte (Corporate-Owned Devices, COD)](corporate-identifiers-add.md) umfassen Mobiltelefone, Tablets und PCs, die das Eigentum der Organisation sind und an die Mitarbeiter ausgegeben werden. Die Registrierung von COD-Geräten unterstützt Szenarios wie die automatische Registrierung, freigegebene Geräte oder Anforderungen für eine vorab autorisierte Registrierung. Eine Methode zum Registrieren von COD-Geräten besteht darin, dass ein Administrator oder Vorgesetzter den Geräteregistrierungs-Manager verwendet. iOS-Geräte können direkt über die von Apple bereitgestellten Programme zur Geräteregistrierung (Device Enrollment Program, DEP) registriert werden. Geräte mit einer IMEI-Nummer können auch als unternehmenseigene Geräte identifiziert und gekennzeichnet werden.

### <a name="device-enrollment-manager"></a>Geräteregistrierungs-Manager
Der Geräteregistrierungs-Manager (DEM) ist ein besonderes Benutzerkonto, das zum Registrieren und Verwalten mehrerer firmeneigener Geräte verwendet wird. Manager können das Unternehmensportal installieren und viele benutzerlose Geräte registrieren. Diese Gerätetypen eignen sich z.B. für POS- oder Hilfsprogramm-Apps, nicht aber für Benutzer, die Zugriff auf E-Mails oder Unternehmensressourcen benötigen. Erfahren Sie mehr über den [DEM](device-enrollment-manager-enroll.md).

### <a name="apple-device-enrollment-program"></a>Apple-Programm zur Geräteregistrierung
Mit der Apple DEP-Verwaltung (Device Enrollment Program, Programm zur Geräteregistrierung) können Sie Richtlinien erstellen und „drahtlos“ auf iOS- und macOS-Geräten bereitstellen, die über DEP erworben wurden und verwaltet werden. Das Gerät wird registriert, wenn ein Benutzer es zum ersten Mal einschaltet und den Setup-Assistenten ausführt. Diese Methode unterstützt den überwachten Modus von iOS, der zulässt, dass ein Gerät mit bestimmten Funktionen konfiguriert wird.

Weitere Informationen zur iOS DEP-Registrierung finden Sie unter:

- [Auswählen der Registrierungsmethode für iOS-Geräte](ios-enroll.md)
- [Registrieren von iOS-Geräten mithilfe des Programms zur Geräteregistrierung](device-enrollment-program-enroll-ios.md)

### <a name="usb-sa"></a>USB (Setup-Assistent)
IT-Administratoren benutzen Apple Configurator über USB, um jedes unternehmenseigene Gerät manuell für die Registrierung mit dem Setup-Assistenten vorzubereiten. Der IT- Administrator erstellt ein Registrierungsprofil und exportiert dieses in Apple Configurator. Wenn die Benutzer ihre Geräte erhalten, werden sie aufgefordert, den Setup-Assistenten auszuführen, um das jeweilige Gerät zu registrieren. Diese Methode unterstützt den **überwachten iOS-Modus**, der wiederum folgende Funktionen ermöglicht:
- Gesperrte Registrierung
- Kioskmodus und andere erweiterte Konfigurationen und Einschränkungen

Weitere Informationen zur Registrierung über den Setup-Assistenten mit iOS Apple Configurator finden Sie unter:

- [Auswählen der Registrierungsmethode für iOS-Geräte](ios-enroll.md)
- [Registrieren von iOS-Geräten mithilfe von Configurator und Setup-Assistent](apple-configurator-enroll-ios.md)

### <a name="usb-direct"></a>USB (direkt)
Für die direkte Registrierung muss der Administrator jedes Gerät manuell registrieren, indem er eine Registrierungsrichtlinie erstellt und in Apple Configurator exportiert. Über USB angeschlossene, unternehmenseigene Geräte werden direkt registriert, ohne dass das Zurücksetzen auf Werkseinstellungen erforderlich ist. Geräte werden als benutzerlose Geräte verwaltet. Sie werden nicht gesperrt oder überwacht und unterstützen nicht den bedingten Zugriff, die Erkennung von Jailbreaks oder die Verwaltung mobiler Anwendungen.

Weitere Informationen zur iOS-Registrierung finden Sie unter:

- [Auswählen der Registrierungsmethode für iOS-Geräte](ios-enroll.md)
- [Registrieren von iOS-Geräten mithilfe von Configurator und direkter Registrierung](apple-configurator-enroll-ios.md)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Bereinigen mobiler Geräte nach Ablauf des MDM-Zertifikats

Das MDM-Zertifikat wird automatisch erneuert, wenn mobile Geräte mit dem Intune-Dienst kommunizieren. Wenn mobile Geräte zurückgesetzt werden oder für längere Zeit keine Kommunikation mit dem Intune-Dienst stattfindet, wird das MDM-Zertifikat nicht verlängert. Das Gerät wird 180 Tage nach Ablauf des MDM-Zertifikats aus dem Azure-Portal entfernt.
