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
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 38bb88015261aa50d6c27aec026614f1205aebe8
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189808"
---
# <a name="capabilities-by-enrollment-method-for-windows-devices"></a>Funktionen nach Registrierungsmethode für Windows-Geräte
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune ermöglicht es Ihnen, die Geräte und Apps Ihrer Mitarbeiter sowie deren Zugriff auf Ihre Unternehmensdaten zu verwalten. Die Geräte müssen zunächst beim Intune-Dienst registriert werden. Es gibt verschiedene Methoden, um die Geräte Ihrer Mitarbeiter zu registrieren. Für jede Methode gelten andere bewährte Methoden und Funktionen, wie in den Tabellen unten dargestellt.

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

