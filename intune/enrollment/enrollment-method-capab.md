---
title: Funktionen der Intune-Registrierungsmethoden für Windows-Geräte
titleSuffix: Microsoft Intune
description: Funktionen jeder Registrierungsmethode für Windows-Geräte
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6b12bb0066c37eb470065a169a3ad7866c69a17
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503264"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Funktionen der Intune-Registrierungsmethoden für Windows-Geräte
[!INCLUDE[azure_portal](../includes/azure_portal.md)]

Es gibt verschiedene Methoden, um die Geräte Ihrer Mitarbeiter in Intune zu registrieren. Für jede Methode gelten andere bewährte Methoden und Funktionen, wie in den Tabellen unten dargestellt.

## <a name="best-practices-by-enrollment-method"></a>Bewährte Methoden nach Registrierungsmethode
| **Empfohlene Methoden** | **[In Azure AD eingebunden](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD verknüpft mit Autopilot (benutzergesteuerter Modus)](enrollment-autopilot.md)** |**[Azure AD verknüpft mit Autopilot (Selbstbereitstellungsmodus)](enrollment-autopilot.md)** |**[Massenregistrierung](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Co-Verwaltung](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Häufig verwendet in EDU|![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Geräte können als freigegebene Geräte verwendet werden|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Persönliche Geräte müssen auf Unternehmensressourcen zugreifen|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Self-Service von Apps|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Funktionen nach Registrierungsmethode

| **Funktionen** | **[In Azure AD eingebunden](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD verknüpft mit Autopilot (benutzergesteuerter Modus)](enrollment-autopilot.md)** |**[Azure AD verknüpft mit Autopilot (Selbstbereitstellungsmodus)](enrollment-autopilot.md)** |**[Massenregistrierung](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Co-Verwaltung](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Bedingter Zugriff                                      |![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|
|Benutzer wird dem Gerät zugeordnet                    |![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|
|Erfordert Azure AD Premium                               |![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|
|Gerät kann von einer Zertifizierungsstelle geschützte Ressourcen bewerten             |![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|
|Benutzer dürfen auf ihren Geräten nicht über Administratorrechte verfügen               |![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Möglichkeit zur Konfiguration der Geräteeinrichtungsumgebung        |![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Möglichkeit zur Registrierung von Geräten ohne Interaktion des Benutzers      |![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|
|Möglichkeit zur Ausführung von PowerShell-Skripts                       |![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/checkmark.png)\*| 
|Unterstützt die automatische Registrierung nach dem AD-Domänenbeitritt      |![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|
|Unterstützt die automatische Registrierung nach der Hybrid-Azure AD-Einbindung|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|
|Unterstützt die automatische Registrierung nach der Azure AD-Einbindung       |![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![Häkchen](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|

\* Workloads von Client-Apps im Configuration Manager müssen in den Intune-Pilot oder Intune verschoben werden.

## <a name="next-steps"></a>Nächste Schritte

[Einrichten der Registrierung für Windows-Geräte](windows-enroll.md)

