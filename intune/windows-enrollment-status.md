---
title: Einrichten einer Statusseite für die Registrierung
titleSuffix: Microsoft Intune
description: Begrüßen Sie Ihre Benutzer, die Windows 10-Geräte registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/17/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c6604c35cebdad4341f27a51db1a4c735f9a9818
ms.sourcegitcommit: 6bd5867c41fb5288fde114dbfcc127dd206f7148
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235615"
---
# <a name="set-up-an-enrollment-status-page"></a>Einrichten einer Statusseite für die Registrierung
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
Bei der Geräteeinrichtung wird auf der Statusseite für die Registrierung der Installationsstatus auf dem Gerät des Endbenutzers angezeigt. Einige Anwendungen, Profile und Zertifikate sind möglicherweise noch nicht vollständig installiert, nachdem die Registrierung des Benutzers abgeschlossen wurde. Mithilfe der Statusseite können Benutzer besser den Status Ihres Geräts während und nach der Registrierung nachvollziehen. Sie können die Statusseite für alle Benutzer aktivieren sowie Benutzer daran hindern, das Gerät zu verwenden, solange noch nicht alle zugewiesenen Anwendungen und Profile installiert sind.
 
Führen Sie die folgenden Schritte aus, um die Statusseite für die Registrierung für alle Endbenutzer zu aktivieren.
 
1.  Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Geräteregistrierung** > **Windows-Registrierung** > **Seite zum Registrierungsstatus (Vorschau)**.
2.  Klicken Sie auf dem Blatt **Seite zum Registrierungsstatus** auf **Standard** > **Einstellungen**.
3.  Klicken Sie für **Show app and profile installation progress** (Installationsfortschritt für die App und das Profil anzeigen) auf **Ja**.
4.  Wählen Sie die anderen Einstellungen aus, die Sie aktivieren wollen, und klicken Sie anschließend auf **Speichern**.
 
## <a name="enrollment-status-page-tracking-information"></a>Statusseite für die Registrierung, auf der Informationen nachverfolgt werden

Auf der Statusseite werden Informationen für die Gerätevorbereitung sowie die Geräte- und Kontoeinrichtung nachverfolgt.

### <a name="device-preparation"></a>Gerätevorbereitung

Für die Gerätevorbereitung werden folgende Vorgänge auf der Statusseite für die Registrierung nachverfolgt: ggf. Schlüsselnachweise für das Trusted Platform Module, der Fortschritt der Verknüpfung mit Azure Active Directory und die Registrierung bei Intune.

### <a name="device-setup"></a>Geräteeinrichtung

Für die Geräteeinrichtung werden die folgenden Elemente auf der Statusseite für die Registrierung nachverfolgt, wenn diese allen Geräten zugewiesen sind:
- Sicherheitsrichtlinien
    - Ein Konfigurationsanbieter für alle Registrierungen
    - Echte CSPs, die von Intune konfiguriert wurden, werden an dieser Stelle nicht nachverfolgt.
- Applications
    - Branchenspezifische MSI-Apps („pro Computer“)
    - Branchenspezifische Store-Apps mit dem Installationskontext „Gerät“
    - Branchenspezifische und Offline Store-Apps mit dem Installationskontext „Gerät“
- Konnektivitätsprofile (VPN und WLAN) werden noch nicht nachverfolgt. Für diese wird immer „0 von 0“ angezeigt.
- Zertifikate werden derzeit noch nicht nachverfolgt. Für diese wird immer „0 von 0“ angezeigt.

### <a name="account-setup"></a>Kontoeinrichtung
Für die Kontoeinrichtung werden auf der Statusseite für die Registrierung die folgenden Elemente angezeigt:
- Sicherheitsrichtlinien
    - Ein CSP für alle Registrierungen
    - Echte CSPs, die von Intune konfiguriert wurden, werden an dieser Stelle nicht nachverfolgt.
- Applications
    - Branchenspezifische MSI-Apps („pro Benutzer“), die „Allen Geräten“, „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört
    - Branchenspezifische MSI-Apps („pro Computer“), die „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört
    - Branchenspezifische Store-Apps mit dem Installationskontext „Benutzer“, die „Allen Geräten“, „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört
    - Online Store-Apps mit dem Installationskontext „Benutzer“, die „Allen Geräten“, „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört
    - Offline Store-Apps mit dem Installationskontext „Benutzer“, die „Allen Geräten“, „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört
- Konnektivitätsprofile
    - VPN- oder WLAN-Profile, die „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört
- Zertifikate
    - Zertifikatprofile, die „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie die Windows-Registrierungsseiten eingerichtet haben, sollten Sie sich informieren, wie Sie Windows-Geräte verwalten. Weitere Informationen finden Sie unter [Was ist die Microsoft Intune-Geräteverwaltung?](https://docs.microsoft.com/intune/device-management).