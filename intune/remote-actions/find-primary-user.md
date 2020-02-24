---
title: Suchen Sie den primären Benutzer eines Microsoft Intune-Geräts.
titleSuffix: ''
description: Suchen Sie den primären Benutzer (oder die Affinität zwischen Benutzer und Gerät) eines Intune-Geräts.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fbafca746c43dada6281ffbfe1e34f01afa8ab91
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413681"
---
# <a name="find-the-primary-user-of-an-intune-device"></a>Suchen des primären Benutzers eines Intune-Geräts

Der primäre Benutzer – auch als Affinität zwischen Benutzer und Gerät bezeichnet – ist eine Eigenschaft jedes Intune-Geräts. Einem Intune-Gerät kann einer oder kein primärer Benutzer zugewiesen sein. Wenn kein primärer Benutzer zugewiesen ist, wird das Gerät als „gemeinsam genutztes Gerät“ bezeichnet.

## <a name="how-to-find-a-devices-primary-user"></a>So suchen Sie den primären Benutzer eines Geräts

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Klicken Sie auf **Geräte**, und wählen Sie ein Gerät aus.
3. Klicken Sie auf der Seite **Übersicht** auf **Mehr anzeigen**. Der primäre Benutzer wird aufgelistet.

## <a name="what-is-the-primary-user"></a>Was ist der primäre Benutzer?
Die Eigenschaft des primären Benutzers wird verwendet, um einen lizenzierten Intune-Benutzer an folgenden Stellen seinen Geräten zuzuordnen:
- Unternehmensportal-App.
- Endbenutzer-Website.
- Benutzeroberflächen für IT-Experten, z.B. Seiten für die Problembehandlung im Azure-Portal. Auf diesen Seiten werden Benutzerkonten mithilfe des primären Benutzers zu Geräten zugeordnet.    

### <a name="company-portal-app"></a>Unternehmensportal-App
Die Unternehmensportal-App erwartet, dass das am Unternehmensportal angemeldete Benutzerkonto der primäre Benutzer dieses Geräts ist. Wenn ein anderer Benutzer als primärer Benutzer zugewiesen wurde, zeigt das Unternehmensportal eine Warnung an:

„Das Gerät ist bereits einem anderen Benutzer innerhalb Ihrer Organisation zugewiesen. Wenden Sie sich an den Unternehmenssupport, um als primärer Benutzer des Geräts eingetragen zu werden. Sie können das Unternehmensportal weiterhin nutzen, aber einige Funktionen sind eingeschränkt.“

Wenn einem Intune-Gerät kein primärer Benutzer zugewiesen ist, erkennt die Unternehmensportal-App dieses Gerät als gemeinsam genutztes Gerät. Gemeinsam genutzte Geräte lassen sich an der Bezeichnung „gemeinsam genutzt“ auf der Kachel des Geräts erkennen. In diesem Modus kann das Unternehmensportal weiterhin verwendet werden, um verfügbare Apps anzufordern und zu installieren. Self-Service-Aktionen (Zurücksetzen/Umbenennen/Außer Betrieb nehmen) sind jedoch nicht verfügbar.  

Damit verfügbare Apps im Unternehmensportal auf gemeinsam genutzten Geräten angezeigt werden, müssen die Apps einer Benutzergruppe zugewiesen sein. Sie werden im System- oder Benutzerkontext installiert, je nachdem, wie sie vom IT-Administrator konfiguriert wurden. Weitere Informationen zum App-Kontext finden Sie unter [Installieren von Apps auf Windows 10-Geräten](../apps/apps-windows-10-app-deploy.md). Zur Verwendung dieses Features ist die Unternehmensportalversion 10.3.4651.0 oder höher erforderlich.


## <a name="who-is-assigned-as-the-primary-user"></a>Wer ist als primärer Benutzer zugewiesen?
Intune fügt den primären Benutzer während oder kurz nach der Registrierung automatisch zu Geräten hinzu. Die Registrierungsmethode bestimmt, wann der primäre Benutzer zu einem Gerät hinzugefügt wird.

| Plattform | Registrierungsmethode | Zugewiesener primärer Benutzer | Primärer Benutzer ist zugewiesen |
| ---- | ---- | ---- | ---- |
| Windows | Hinzufügen von Geschäfts-, Schul- oder Unikonto (benutzergesteuert) | Registrierender Benutzer | Während der Registrierung |   
| Windows | Moderne App-Anmeldung (benutzergesteuert) | Registrierender Benutzer | Während der Registrierung | 
| Windows | Registrierung nur in MDM (benutzergesteuert) | Registrierender Benutzer | Während der Registrierung | 
| Windows | Beitritt zu Azure AD (sofort einsetzbar) | Registrierender Benutzer | Während der Registrierung | 
| Windows | Beitritt zu Azure AD (sofort einsetzbar per Autopilot) | Registrierender Benutzer | Während der Registrierung | 
| Windows | Registrierung nur in MDM | Registrierender Benutzer | Während der Registrierung | 
| Windows | Hybrid AADJ und GPO für automatische Registrierung | Erster Benutzer, der sich bei Windows anmeldet | Wenn der erste Benutzer sich bei Windows anmeldet| 
| Windows | Co-Verwaltung | Erster Benutzer, der sich bei Windows anmeldet | Wenn der erste Benutzer sich bei Windows anmeldet | 
| Windows | Beitritt zu Azure AD (Token für Massenregistrierung) | Keine | Nicht zutreffend | 
| Windows | Beitritt zu Azure AD (Selbstbereitstellungsmodus mit Autopilot) | Keine | Nicht zutreffend | 
| Plattformübergreifend | Benutzergesteuerte Registrierung mit Unternehmensportal-App | Registrierender Benutzer | Während der Registrierung |
| Plattformübergreifend | Geräteregistrierungs-Manager (Device Enrollment Manager, DEM) | Registrierender DEM-Benutzer | Während der Registrierung |
| iOS/iPadOS, macOS | Automatisierte Apple-Geräteregistrierung (DEP mit Benutzeraffinität) | Registrierender Benutzer | Während der Registrierung |
| iOS/iPadOS, macOS | Automatisierte Apple-Geräteregistrierung (DEP ohne Benutzeraffinität) | Keine | Nicht zutreffend |
| Android | Unternehmenseigene, dedizierte Android-Geräte | Keine | Nicht zutreffend |

## <a name="primary-user-and-azure-ad-device-owner"></a>Primärer Benutzer und Azure AD-Gerätebesitzer
In einigen Fällen kann sich der primäre Benutzer in Intune von der Eigenschaft **Besitzer** des Azure AD-Geräts unterscheiden (kann unter **Geräte** > **Azure AD-Geräte** angezeigt werden). Der Azure AD-Gerätebesitzer wird während der Registrierung eines Geräts bei Azure Active Directory hinzugefügt.

## <a name="next-steps"></a>Nächste Schritte
[Verwalten von Geräten mit Microsoft Intune](device-management.md)
