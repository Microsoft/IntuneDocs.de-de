---
title: Registrieren von Geräten mithilfe eines Geräteregistrierungs-Manager-Kontos
titlesuffix: Microsoft Intune
description: Verwenden Sie das Konto „Geräteregistrierungs-Manager“, um Geräte in Intune zu registrieren. "
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 1d3e01cdbc7c9e30034e83e9609c0df5f031c18a
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184912"
---
# <a name="enroll-devices-by-using-a-device-enrollment-manager-account"></a>Registrieren von Geräten mithilfe eines Geräteregistrierungs-Manager-Kontos

Sie können bis zu 1.000 mobile Geräte mit einem einzigen Azure Active Directory-Konto registrieren, indem Sie ein Geräteregistrierungs-Manager-Konto (Device Enrollment Manager, DEM) verwenden. Dabei handelt es sich um eine Intune-Berechtigung, die AAD-Benutzerkonten gewährt werden kann, mit der Benutzer bis zu 1.000 Geräte registrieren können. Ein DEM-Konto eignet sich für Szenarios, in denen Geräte registriert und vorbereitet werden, bevor Sie den Benutzern übergeben werden.

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Einschränkungen der Geräte, die mit dem DEM Konto angemeldet sind

DEM-Benutzerkonten und Geräte, die mit einem DEM-Benutzerkonto registriert werden, unterliegen den folgenden Einschränkungen:

  - Die Zurücksetzung kann nicht über das Unternehmensportal erfolgen. Die Zurücksetzung eines Geräts, das über ein DEM-Benutzerkonto registriert wurde, kann über Intune im Azure-Portal erfolgen.
  - Nur das lokale Gerät erscheint in der Unternehmensportal-App oder -Website.
  - DEM-Benutzerkonten können Apps aus dem Apple Volume Purchase Program (VPP) nicht mit Apple VPP-Benutzerlizenzen verwenden, weil benutzerspezifische Apple-IDs für die Verwaltung dieser Apps erforderlich sind.
  - Geräte können VPP-Apps installieren, wenn sie über Apple VPP-Gerätelizenzen verfügen.
  - Geräte werden für den bedingten Zugriff mit Ausnahme von Windows 10-Version 1803 und höher blockiert.


## <a name="add-a-device-enrollment-manager"></a>Hinzufügen eines Geräteregistrierungs-Managers

1.  Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) die Option **Geräteregistrierung** > **Geräteregistrierungs-Manager** aus.

2.  Wählen Sie **Hinzufügen** aus.

3.  Geben Sie auf dem Blatt **Benutzer hinzufügen** einen Benutzerprinzipalnamen für den Geräteregistrierungs-Manager-Benutzer ein, und wählen Sie **Hinzufügen** aus. Der Geräteregistrierungs-Manager-Benutzer wird der Liste der Geräteregistrierungs-Manager-Benutzer hinzugefügt.

## <a name="permissions-for-dem"></a>Berechtigungen für DEM

Die Azure AD-Rollen globaler Administrator oder Intune-Dienstadministrator sind erforderlich, um
- einem Azure AD-Benutzerkonto die DEM-Berechtigung zu gewähren
- alle DEM-Benutzer anzuzeigen

Wenn einem Benutzer keine globale Administratorrolle oder Intune-Dienstadministratorrolle zugewiesen ist, aber Leseberechtigungen für die ihm zugewiesene Rolle „Geräteregistrierungs-Manager“ aktiviert sind, kann dieser nur die von ihm erstellten DEM-Benutzer sehen.


## <a name="remove-device-enrollment-manager-permissions"></a>Entfernen der DEM-Berechtigungen

Wenn Sie einen Geräteregistrierungs-Manager entfernen, wirkt sich dies nicht auf registrierte Geräte aus.

**So entfernen Sie einen Geräteregistrierungs-Manager**

1. Wählen Sie in [Intune im Azure-Portal](https://aka.ms/intuneportal) zuerst **Geräteregistrierung** und dann **Geräteregistrierungs-Manager** aus.
2. Wählen Sie auf dem Blatt **Geräteregistrierungs-Manager** den DEM-Benutzer aus, und klicken Sie auf **Löschen**.

