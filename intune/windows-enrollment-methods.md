---
title: Intune-Registrierungsmethoden für Windows-Geräte
titleSuffix: Microsoft Intune
description: Lernen Sie verschiedene Methoden für die Registrierung von Windows-Geräten in Intune kennen
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: ''
ms.openlocfilehash: a0d77ab53db473f44c307e3796721c94839e86b5
ms.sourcegitcommit: d2989b9992d10d133573d9bc31479659fb7e242c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71080000"
---
# <a name="intune-enrollment-methods-for-windows-devices"></a>Intune-Registrierungsmethoden für Windows-Geräte

Damit Geräte in Intune verwaltet werden können, müssen sie zunächst beim Intune-Dienst registriert werden. Sowohl private als auch unternehmenseigene Geräte können für die Intune-Verwaltung registriert werden. 

Es gibt zwei Möglichkeiten, um Geräte in Intune zu registrieren:
- Benutzer können ihre Windows-Computer selbst registrieren 
- Administratoren können Richtlinien so konfigurieren, dass eine automatische Registrierung erzwungen wird, ohne dass die Benutzer involviert werden müssen

## <a name="user-self-enrollment-in-intune"></a>Selbstregistrierung für Benutzer in Intune

Benutzer können ihre Windows-Geräte mit einer dieser Methoden selbst registrieren:

- [Bring Your Own Device (BYOD):](https://docs.microsoft.com/intune-user-help/enroll-windows-10-device) Benutzer registrieren Ihre privaten Geräte, indem sie eine Verbindung mit einem **Work and School**-Konto (Arbeit und Schule) in den **Einstellungen** des Geräts herstellen. Durch diesen Prozess geschieht Folgendes:
  - Das Gerät wird in Azure Active Directory registriert, um Zugriff auf Unternehmensressourcen wie E-Mails zu erhalten.
  - Das Gerät wird in Intune als privates Gerät (Bring Your Own Device, BYOD) registriert.
Wenn ein Administrator die automatische Registrierung, die in Azure AD Premium-Abonnements verfügbar ist, konfiguriert hat, muss der Benutzer lediglich einmal seine Anmeldeinformationen eingeben. Andernfalls müssen sie sich extra über eine reine MDM-Registrierung registrieren und ihre Anmeldeinformationen erneut eingeben.  
- **MDM only enrollment** (Reine MDM-Registrierung): Diese Methode ermöglicht Benutzern, eine bestehende Arbeitsgruppe, Active Directory oder einen mit Azure Active Directory verknüpften Computer in Intune zu registrieren. Benutzer führen die Registrierung über die Einstellungen des bestehenden Windows-Computers durch. Diese Methode wird nicht empfohlen, da so das Gerät nicht in Azure Active Directory registriert wird. Außerdem können Features wie der bedingte Zugriff nicht verwendet werden.
- [Azure Active Directory-Verknüpfung](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network): Verknüpft das Gerät mit Azure Active Directory und ermöglicht es Benutzern, sich mit ihren Azure AD-Anmeldeinformationen bei Windows anzumelden. Wenn die automatische Registrierung aktiviert ist, wird das Gerät automatisch in Intune registriert. Der Vorteil der automatischen Registrierung ist, dass der Prozess für den Benutzer aus nur einem Schritt besteht. Andernfalls müssen sie sich extra über eine reine MDM-Registrierung registrieren und ihre Anmeldeinformationen erneut eingeben. Benutzer verwenden diese Registrierungsmethode entweder während der ersten Windows-Einrichtung oder über die Einstellungen ihres PCs. Das Gerät wird als unternehmenseigenes Gerät in Intune gekennzeichnet.
- [Autopilot:](enrollment-autopilot.md) Automatisiert die Azure Active Directory-Verknüpfung und registriert neue unternehmenseigene Geräte in Intune. Diese Methode vereinfacht die erste Einrichtung und macht es überflüssig, benutzerdefinierte Betriebssystemimages auf den Geräten anzuwenden. Wenn Administratoren Intune zum Verwalten von Autopilot-Geräten verwenden, können sie z. B. Richtlinien, Profile und Apps verwalten, nachdem diese registriert sind.  Es gibt vier Arten der Autopilot-Bereitstellung: [Self-Deployment-Modus](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) (für Kioske, digitale Beschilderung oder ein freigegebenes Gerät), [User Driven Mode](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) (benutzergesteuerter Modus für herkömmliche Benutzer), [White Glove] (https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) unterstützt Partner oder IT-Mitarbeiter dabei, einen Windows 10-Computer vorab bereitzustellen, damit dieser vollständig konfiguriert und betriebsbereit ist) und [Autopilot für vorhandene Geräte] (mit https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) können Sie die neueste Version von Windows 10 mühelos auf Ihren vorhandenen Geräten bereitstellen).

## <a name="administrator-based-enrollment-in-intune"></a>Administratorbasierte Registrierung in Intune

Administratoren können die folgenden Registrierungsmethoden einrichten, die keine Benutzerinteraktion erfordern:

- [Azure AD Hybrid Join:](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) Diese Methode ermöglicht Administratoren, die Active Directory-Gruppenrichtlinie so zu konfigurieren, dass Geräte automatisch verknüpft werden, wenn sie hybrid in Azure AD eingebunden sind. 
- [Configuration Manager Co-management](https://docs.microsoft.com/sccm/comanage/overview) (Configuration Manager-Co-Verwaltung): Diese Methode ermöglicht Administratoren, ihre vorhandenen verwalteten Configuration Manager-Geräte in Intune zu registrieren, um sowohl von den Vorteilen von Intune als auch von Configuration Manager zu profitieren. 
- Der [Geräteregistrierungs-Manager](device-enrollment-manager-enroll.md) (Device Enrollment Manager, DEM) ist ein spezielles Dienstkonto. DEM-Konten haben Berechtigungen, mit denen autorisierte Benutzer mehrere unternehmenseigene Geräte registrieren und verwalten können. Diese Gerätetypen eignen sich z.B. für POS- oder Hilfsprogramm-Apps, nicht aber für Benutzer, die Zugriff auf E-Mails oder Unternehmensressourcen benötigen. Diese Methode ermöglicht nicht, Features wie den bedingten Zugriff zu verwenden. 
- [Bulk enroll](windows-bulk-enroll.md) (Massenregistrierung): Diese Methode ermöglicht einem autorisierten Benutzer, sehr viele neue unternehmenseigene Geräte mit Azure Active Directory und Intune zu verknüpfen. Sie erstellen mit der Windows Configuration Designer-App (WCD) ein Bereitstellungspaket. Dann installieren Sie mithilfe von USB-Medien während der ersten Windows-Einrichtung oder mithilfe von Medien von vorhandenen Windows-Computern das Bereitstellungspaket, sodass Geräte automatisch in Intune registriert werden. Diese Methode ermöglicht nicht die Verwendung von bedingtem Zugriff. 
- Beim [Registrieren von Windows IoT Core-Geräten in Microsoft Intune](https://docs.microsoft.com/windows/iot-core/manage-your-device/intunedeviceenrollment) erfolgt die Vorbereitung des Geräts auf dem Windows IoT Core-Dashboard. Danach wird der Windows-Konfigurations-Designer verwendet, um ein Bereitstellungspaket zu erstellen. Anschließend wird das Bereitstellungspaket beim ersten Systemstart über eine SD-Karte installiert, um die Geräte automatisch bei Intune zu registrieren.

## <a name="next-steps"></a>Nächste Schritte

[Funktionen der Intune-Registrierungsmethoden für Windows-Geräte](enrollment-method-capab.md).
