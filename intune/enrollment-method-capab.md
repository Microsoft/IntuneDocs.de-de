---
title: Intune-Funktionen nach Registrierungsmethode für Windows-Geräte
titlesuffix: Microsoft Intune
description: Erfahren Sie, welche Funktionen jede Registrierungsmethode für Windows-Geräte unterstützt.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c9e440aef7f434cbe675506fd6f22a9bd26b2c31
ms.sourcegitcommit: 528d2bc70bfd25803a2d9f0fe9372c8a5f5e7dad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446819"
---
# <a name="capabilities-by-enrollment-method-for-windows-devices"></a>Funktionen nach Registrierungsmethode für Windows-Geräte
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune ermöglicht es Ihnen, die Geräte und Apps Ihrer Mitarbeiter sowie deren Zugriff auf Ihre Unternehmensdaten zu verwalten. Die Geräte müssen zunächst beim Intune-Dienst registriert werden. Es gibt verschiedene Methoden, um die Geräte Ihrer Mitarbeiter zu registrieren. Für jede Methode gelten andere bewährte Methoden und Funktionen, wie in den Tabellen unten dargestellt.

## <a name="best-practices-by-enrollment-method"></a>Bewährte Methoden nach Registrierungsmethode
| **Empfohlene Methoden** | **[In Azure AD eingebunden](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD verknüpft mit Autopilot](enrollment-autopilot.md)** |**[Massenregistrierung](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **GPO** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Häufig verwendet in EDU|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Geräte können als freigegebene Geräte verwendet werden|![X](media/xmark.png)|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Persönliche Geräte müssen auf Unternehmensressourcen zugreifen|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|
|Self-Service von Apps|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Funktionen nach Registrierungsmethode

| **Funktionen** | **[In Azure AD eingebunden](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD verknüpft mit Autopilot](enrollment-autopilot.md)** |**[Massenregistrierung](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **GPO** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Bedingter Zugriff                                      |![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|
|Benutzer wird dem Gerät zugeordnet                    |![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|
|Erfordert Azure AD Premium                               |![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|
|Gerät kann von einer Zertifizierungsstelle geschützte Ressourcen bewerten             |![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|
|Benutzer dürfen auf ihren Geräten nicht über Administratorrechte verfügen               |![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Möglichkeit zur Konfiguration der Geräteeinrichtungsumgebung        |![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Möglichkeit zur Registrierung von Geräten ohne Interaktion des Benutzers      |![X](media/xmark.png)|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|
|Möglichkeit zur Ausführung von PowerShell-Skripts                       |![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)| 
|Unterstützt die automatische Registrierung nach dem AD-Domänenbeitritt      |![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|
|Unterstützt die automatische Registrierung nach der Hybrid-Azure AD-Einbindung|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|
|Unterstützt die automatische Registrierung nach der Azure AD-Einbindung       |![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|

## <a name="next-steps"></a>Nächste Schritte

[Optionen für die Registrierung](enrollment-options.md)

