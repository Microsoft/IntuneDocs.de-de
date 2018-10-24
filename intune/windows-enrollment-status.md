---
title: Einrichten einer Statusseite für die Registrierung
titleSuffix: Microsoft Intune
description: Begrüßen Sie Ihre Benutzer, die Windows 10-Geräte registrieren.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f5460db2d646d8bd417baa50d8188acbf69a251d
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2018
ms.locfileid: "48827988"
---
# <a name="set-up-an-enrollment-status-page"></a>Einrichten einer Statusseite für die Registrierung
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
Bei der Geräteeinrichtung werden auf der Statusseite für die Registrierung Installationsinformationen zum Gerät angezeigt. Einige Anwendungen, Profile und Zertifikate sind möglicherweise noch nicht vollständig installiert, nachdem die Registrierung des Benutzers abgeschlossen wurde. Mithilfe der Statusseite können Benutzer besser den Status Ihres Geräts während und nach der Registrierung nachvollziehen. Sie können die Statusseite für alle Ihre Benutzer aktivieren oder Profile für bestimmte Benutzergruppen erstellen.  Sie haben die Möglichkeit, Profile so einzustellen, dass sie den Fortschritt der Installation anzeigen, die Nutzung bis zum Abschluss der Installation blockieren, ein Zurücksetzen zulassen usw.
 
## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Aktivieren der standardmäßigen Statusseite für die Registrierung für alle Benutzer

Führen Sie die folgenden Schritte aus, um die Statusseite für die Registrierung für alle Endbenutzer zu aktivieren.
 
1.  Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Geräteregistrierung** > **Windows-Registrierung** > **Seite zum Registrierungsstatus (Vorschau)**.
2.  Klicken Sie auf dem Blatt **Seite zum Registrierungsstatus** auf **Standard** > **Einstellungen**.
3.  Klicken Sie für **Show app and profile installation progress** (Installationsfortschritt für die App und das Profil anzeigen) auf **Ja**.
4.  Wählen Sie die anderen Einstellungen aus, die Sie aktivieren wollen, und klicken Sie anschließend auf **Speichern**.

## <a name="create-enrollment-status-page-profile-to-target-specific-users"></a>Erstellen eines Profils der Statusseite für die Registrierung mit Ausrichtung auf bestimmte Benutzer

1.  Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Geräteregistrierung** > **Windows-Registrierung** > **Seite zum Registrierungsstatus (Vorschau)** > **Profil erstellen**.
2. Geben Sie einen **Namen** und eine **Beschreibung** an.
3. Wählen Sie **Erstellen** aus.
4. Wählen Sie das neue Profil in der Liste der **Seite zum Registrierungsstatus** aus.
5. Klicken Sie auf **Zuweisungen** > **Gruppen auswählen**. Wählen Sie dann die Gruppen aus, für die dieses Profil übernommen werden soll, und klicken Sie abschließend auf **Auswählen** > **Speichern**.
6. Wählen Sie **Einstellungen** und dann die Einstellungen aus, die Sie auf dieses Profil anwenden möchten. Klicken Sie auf **Speichern** aus.


## <a name="enrollment-status-page-tracking-information"></a>Statusseite für die Registrierung, auf der Informationen nachverfolgt werden

Auf der Statusseite werden Informationen für die Gerätevorbereitung sowie die Geräte- und Kontoeinrichtung nachverfolgt.

### <a name="device-preparation"></a>Gerätevorbereitung

Für die Gerätevorbereitung werden folgende Vorgänge auf der Statusseite für die Registrierung nachverfolgt: ggf. Schlüsselnachweise für das Trusted Platform Module, der Fortschritt der Verknüpfung mit Azure Active Directory und die Registrierung bei Intune.

### <a name="device-setup"></a>Geräteeinrichtung

Für die Geräteeinrichtung werden die folgenden Elemente auf der Statusseite für die Registrierung nachverfolgt, wenn diese allen Geräten zugewiesen sind:
- Sicherheitsrichtlinien
    - Ein Konfigurationsanbieter für alle Registrierungen
    - Tatsächliche CSPs, die von Intune konfiguriert wurden, werden an dieser Stelle nicht nachverfolgt.
- Applications
    - Branchenspezifische MSI-Apps („pro Computer“)
    - Branchenspezifische Store-Apps mit dem Installationskontext „Gerät“
    - Branchenspezifische und Offline Store-Apps mit dem Installationskontext „Gerät“
- Konnektivitätsprofile (VPN und WLAN) werden noch nicht nachverfolgt. Diese sind immer „0 von 0“.
- Zertifikate werden noch nicht nachverfolgt. Diese sind immer „0 von 0“.

### <a name="account-setup"></a>Kontoeinrichtung
Für die Kontoeinrichtung werden auf der Statusseite für die Registrierung die folgenden Elemente angezeigt:
- Sicherheitsrichtlinien
    - Ein CSP für alle Registrierungen
    - Tatsächliche CSPs, die von Intune konfiguriert wurden, werden an dieser Stelle nicht nachverfolgt.
- Applications
    - Branchenspezifische MSI-Apps („pro Benutzer“), die „Allen Geräten“, „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört
    - Branchenspezifische MSI-Apps („pro Computer“), die „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört
    - LOB-Store-Apps, Onlinestore-Apps und Offlinestore-Apps, die einer der folgenden Kategorien zugeordnet sind:
        - Alle Geräte
        - Allen Benutzern
        - eine Benutzergruppe, in der der Benutzer ein Mitglied ist, der das Gerät registriert, dessen Installationskontext auf „Benutzer“ eingestellt ist.
- Konnektivitätsprofile
    - VPN- oder WLAN-Profile, die „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört
- Zertifikate
    - Zertifikatprofile, die „Allen Benutzern“ oder einer „Benutzergruppe“ zugewiesen sind, der der sich registrierende Benutzer angehört

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie die Windows-Registrierungsseiten eingerichtet haben, sollten Sie sich informieren, wie Sie Windows-Geräte verwalten. Weitere Informationen finden Sie unter [Was ist die Microsoft Intune-Geräteverwaltung?](https://docs.microsoft.com/intune/device-management).