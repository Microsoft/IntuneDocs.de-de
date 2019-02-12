---
title: Funktionen der Intune-Registrierungsmethoden für Windows-Geräte
titlesuffix: Microsoft Intune
description: Funktionen jeder Registrierungsmethode für Windows-Geräte
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
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa71461b136243262146502adc0f7b925b345a0b
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55839327"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Funktionen der Intune-Registrierungsmethoden für Windows-Geräte
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Es gibt verschiedene Methoden, um die Geräte Ihrer Mitarbeiter in Intune zu registrieren. Für jede Methode gelten andere bewährte Methoden und Funktionen, wie in den Tabellen unten dargestellt.

## <a name="best-practices-by-enrollment-method"></a>Bewährte Methoden nach Registrierungsmethode
| **Empfohlene Methoden** | **[In Azure AD eingebunden](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD verknüpft mit Autopilot](enrollment-autopilot.md)** |**[Massenregistrierung](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Häufig verwendet in EDU|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Geräte können als freigegebene Geräte verwendet werden|![X](media/xmark.png)|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Persönliche Geräte müssen auf Unternehmensressourcen zugreifen|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|
|Self-Service von Apps|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Häkchen](media/checkmark.png)|![Häkchen](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Funktionen nach Registrierungsmethode

| **Funktionen** | **[In Azure AD eingebunden](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD verknüpft mit Autopilot](enrollment-autopilot.md)** |**[Massenregistrierung](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** |
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

[Einrichten der Registrierung für Windows-Geräte](windows-enroll.md)

