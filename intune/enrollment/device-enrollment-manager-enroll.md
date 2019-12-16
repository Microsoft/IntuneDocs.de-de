---
title: Registrieren von Geräten mithilfe eines Geräteregistrierungs-Manager-Kontos
titleSuffix: Microsoft Intune
description: Verwenden Sie das Konto „Geräteregistrierungs-Manager“, um Geräte in Intune zu registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30191aea892e8409bb6165034256a99f6f32a502
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955404"
---
# <a name="enroll-devices-in-intune-by-using-a-device-enrollment-manager-account"></a>Registrieren von Geräten in Intune mithilfe eines Geräteregistrierungs-Manager-Kontos

Sie können bis zu 1.000 mobile Geräte mit einem einzigen Azure Active Directory-Konto registrieren, indem Sie ein Geräteregistrierungs-Manager-Konto (Device Enrollment Manager, DEM) verwenden. Dabei handelt es sich um eine Intune-Berechtigung, die AAD-Benutzerkonten gewährt werden kann, mit der Benutzer bis zu 1.000 Geräte registrieren können. Ein DEM-Konto eignet sich für Szenarios, in denen Geräte registriert und vorbereitet werden, bevor Sie den Benutzern übergeben werden. Grundsätzlich gibt es in Microsoft Intune eine Beschränkung von 150 Geräteregistrierungs-Manager-Konten (Device Enrollment Manager, DEM).

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Einschränkungen der Geräte, die mit dem DEM Konto angemeldet sind

DEM-Benutzerkonten und Geräte, die mit einem DEM-Benutzerkonto registriert werden, unterliegen den folgenden Einschränkungen:

- Einem DEM-Kontobenutzer muss eine Intune-Lizenz zugewiesen werden.
- Die Zurücksetzung kann nicht über das Unternehmensportal erfolgen. Die Zurücksetzung eines Geräts, das über ein DEM-Benutzerkonto registriert wurde, kann über Intune im Azure-Portal erfolgen.
- Nur das lokale Gerät erscheint in der Unternehmensportal-App oder -Website.
- DEM-Benutzerkonten können Apps aus dem Apple Volume Purchase Program (VPP) nicht mit Apple VPP-Benutzerlizenzen verwenden, weil benutzerspezifische Apple-IDs für die Verwaltung dieser Apps erforderlich sind.
- DEM-Konten können nicht verwendet werden, wenn Geräte über das Programm zur Geräteregistrierung (DEP) von Apple registriert wurden.
- Geräte können VPP-Apps installieren, wenn sie über Apple VPP-Gerätelizenzen verfügen.
- Geräte werden für den bedingten Zugriff mit Ausnahme von Windows 10-Version 1803 und höher blockiert.
- Jedes Gerät, das bei DEM-Konten registriert ist, muss für die Verwaltung durch Intune korrekt lizenziert sein. Bei der Lizenz kann es sich um eine Intune-Benutzerlizenz oder um eine Intune-Gerätelizenz handeln.
- Wenn Sie [Android Enterprise-Arbeitsprofilgeräte über ein DEM-Konto registrieren](android-work-profile-enroll.md), besteht pro Konto ein Grenzwert von 10 registrierbaren Geräten.


## <a name="add-a-device-enrollment-manager"></a>Hinzufügen eines Geräteregistrierungs-Managers

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an, und navigieren Sie zu **Geräte** > **Geräte registrieren** > **Geräteregistrierungs-Manager**.

2. Wählen Sie **Hinzufügen** aus.

3. Geben Sie auf dem Blatt **Benutzer hinzufügen** einen Benutzerprinzipalnamen für den Geräteregistrierungs-Manager-Benutzer ein, und wählen Sie **Hinzufügen** aus. Der Geräteregistrierungs-Manager-Benutzer wird der Liste der Geräteregistrierungs-Manager-Benutzer hinzugefügt.

## <a name="permissions-for-dem"></a>Berechtigungen für DEM

Die Azure AD-Rollen globaler Administrator oder Intune-Dienstadministrator sind erforderlich, um
- einem Azure AD-Benutzerkonto die DEM-Berechtigung zu gewähren
- alle DEM-Benutzer anzuzeigen

Wenn einem Benutzer keine globale Administratorrolle oder Intune-Dienstadministratorrolle zugewiesen ist, aber Leseberechtigungen für die ihm zugewiesene Rolle „Geräteregistrierungs-Manager“ aktiviert sind, kann dieser nur die von ihm erstellten DEM-Benutzer sehen.


## <a name="remove-device-enrollment-manager-permissions"></a>Entfernen der DEM-Berechtigungen

Wenn Sie einen Geräteregistrierungs-Manager entfernen, wirkt sich dies nicht auf registrierte Geräte aus.

**So entfernen Sie einen Geräteregistrierungs-Manager**

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an, und navigieren Sie zu **Geräte** > **Geräte registrieren** > **Geräteregistrierungs-Manager**.
2. Wählen Sie auf dem Blatt **Geräteregistrierungs-Manager** den DEM-Benutzer aus, und klicken Sie auf **Löschen**.

