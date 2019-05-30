---
title: Intune-Registrierungsmethoden für Windows-Geräte
titleSuffix: Microsoft Intune
description: Lernen Sie verschiedene Methoden für die Registrierung von Windows-Geräten in Intune kennen
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: ''
ms.openlocfilehash: c3f5f3b39efd33e8dbd3dd84f9a5f2abaf347216
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66046702"
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
- [Azure Active Directory-Verknüpfung:](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) Verknüpft das Gerät mit Azure Active Directory und ermöglicht Benutzern, sich bei Windows mit ihren Azure AD-Anmeldeinformationen anzumelden. Wenn die automatische Registrierung aktiviert ist, wird das Gerät automatisch in Intune registriert. Der Vorteil der automatischen Registrierung ist, dass der Prozess für den Benutzer aus nur einem Schritt besteht. Andernfalls müssen sie sich extra über eine reine MDM-Registrierung registrieren und ihre Anmeldeinformationen erneut eingeben. Benutzer verwenden diese Registrierungsmethode entweder während der ersten Windows-Einrichtung oder über die Einstellungen ihres PCs. Das Gerät wird als unternehmenseigenes Gerät in Intune gekennzeichnet.
- [Autopilot:](enrollment-autopilot.md) Automatisiert die Azure Active Directory-Verknüpfung und registriert neue unternehmenseigene Geräte in Intune. Diese Methode vereinfacht die erste Einrichtung und macht es überflüssig, benutzerdefinierte Betriebssystemimages auf den Geräten anzuwenden. Wenn Administratoren Intune zum Verwalten von Autopilot-Geräten verwenden, können sie z. B. Richtlinien, Profile und Apps verwalten, nachdem diese registriert sind.  Es gibt zwei Arten der Autopilot-Bereitstellung: Einen Selbstbereitstellungsmodus ([Self Deploying Mode](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying)) für Kiosks, digitale Signaturen oder für ein freigegebenes Gerät und einen benutzergesteuerten Modus ([User Driven Mode](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven)) für herkömmliche Benutzer. 

## <a name="administrator-based-enrollment-in-intune"></a>Administratorbasierte Registrierung in Intune

Administratoren können die folgenden Registrierungsmethoden einrichten, die keine Benutzerinteraktion erfordern:

- [Azure AD Hybrid Join:](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) Diese Methode ermöglicht Administratoren, die Active Directory-Gruppenrichtlinie so zu konfigurieren, dass Geräte automatisch verknüpft werden, wenn sie hybrid in Azure AD eingebunden sind. 
- [Configuration Manager Co-management](https://docs.microsoft.com/sccm/comanage/overview) (Configuration Manager-Co-Verwaltung): Diese Methode ermöglicht Administratoren, ihre vorhandenen verwalteten Configuration Manager-Geräte in Intune zu registrieren, um sowohl von den Vorteilen von Intune als auch von Configuration Manager zu profitieren. 
- Der [Geräteregistrierungs-Manager](device-enrollment-manager-enroll.md) (Device Enrollment Manager, DEM) ist ein spezielles Dienstkonto. DEM-Konten haben Berechtigungen, mit denen autorisierte Benutzer mehrere unternehmenseigene Geräte registrieren und verwalten können. Diese Gerätetypen eignen sich z.B. für POS- oder Hilfsprogramm-Apps, nicht aber für Benutzer, die Zugriff auf E-Mails oder Unternehmensressourcen benötigen. Außerdem ermöglicht diese Methode nicht, Features wie den bedingten Zugriff zu verwenden. 
- [Bulk enroll](windows-bulk-enroll.md) (Massenregistrierung): Diese Methode ermöglicht einem autorisierten Benutzer, sehr viele neue unternehmenseigene Geräte mit Azure Active Directory und Intune zu verknüpfen. Sie erstellen mit der Windows Configuration Designer-App (WCD) ein Bereitstellungspaket. Dann installieren Sie mithilfe von USB-Medien während der ersten Windows-Einrichtung oder mithilfe von Medien von vorhandenen Windows-Computern das Bereitstellungspaket, sodass Geräte automatisch in Intune registriert werden. 

## <a name="next-steps"></a>Nächste Schritte

[Funktionen der Intune-Registrierungsmethoden für Windows-Geräte](enrollment-method-capab.md).
