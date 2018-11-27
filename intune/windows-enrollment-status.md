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
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: ada9fee575824d27a6bfdd8f14d4845d228467db
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186076"
---
# <a name="set-up-an-enrollment-status-page"></a>Einrichten einer Statusseite für die Registrierung
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
Bei der Geräteeinrichtung werden auf der Statusseite für die Registrierung Installationsinformationen zum Gerät angezeigt. Einige Anwendungen, Profile und Zertifikate sind möglicherweise noch nicht installiert, wenn ein Benutzer die Standardregistrierung abschließt und sich am Gerät anmeldet. Mithilfe einer Registrierungsstatusseite können Benutzer den Status Ihres Geräts während der Geräteeinrichtung besser nachvollziehen. Sie können mehrere Profile für Registrierungsstatusseiten erstellen und auf verschiedene Gruppen anwenden. Folgendes kann für Profile festgelegt werden:
- Installationsstatus anzeigen
- Nutzung blockieren, bis die Installation abgeschlossen ist
- Angeben, wie ein Benutzer vorgehen kann, wenn die Geräteeinrichtung fehlschlägt.

Außerdem können Sie die Reihenfolge anhand der Priorität der Profile festlegen, um Konflikte durch Profilzuweisungen zum gleichen Benutzer oder Gerät zu vermeiden.

 
## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Aktivieren der standardmäßigen Statusseite für die Registrierung für alle Benutzer

Führen Sie die folgenden Schritte aus, um die Registrierungsstatusseite zu aktivieren.
 
1. Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Geräteregistrierung** > **Windows-Registrierung** > **Seite zum Registrierungsstatus (Vorschau)**.
2. Klicken Sie auf dem Blatt **Seite zum Registrierungsstatus** auf **Standard** > **Einstellungen**.
3. Klicken Sie für **Show app and profile installation progress** (Installationsfortschritt für die App und das Profil anzeigen) auf **Ja**.
4. Wählen Sie die anderen Einstellungen aus, die Sie aktivieren wollen, und klicken Sie anschließend auf **Speichern**.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>Erstellen eines Profils für Registrierungsstatusseiten und Zuweisen zu einer Gruppe

1. Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Geräteregistrierung** > **Windows-Registrierung** > **Seite zum Registrierungsstatus (Vorschau)** > **Profil erstellen**.
2. Geben Sie einen **Namen** und eine **Beschreibung** an.
3. Wählen Sie **Erstellen** aus.
4. Wählen Sie das neue Profil in der Liste der **Seite zum Registrierungsstatus** aus.
5. Klicken Sie auf **Zuweisungen** > **Gruppen auswählen**. Wählen Sie dann die Gruppen aus, für die dieses Profil übernommen werden soll, und klicken Sie abschließend auf **Auswählen** > **Speichern**.
6. Wählen Sie **Einstellungen** und dann die Einstellungen aus, die Sie auf dieses Profil anwenden möchten. Klicken Sie auf **Speichern** aus.

## <a name="set-the-enrollment-status-page-priority"></a>Festlegen der Priorität von Registrierungsstatusseiten

Ein Gerät oder Benutzer kann zu mehreren Gruppen gehören und über mehrere Profile für Registrierungsstatusseiten verfügen. Sie können die Priorität für jedes Profil festlegen, um solche Konflikte zu beheben. Wenn jemand über mehr als ein Profil für die Registrierungsstatusseite verfügt, wird nur das Profil mit der höchsten Priorität angewendet.

1. Klicken Sie in [Intune](https://aka.ms/intuneportal) auf **Geräteregistrierung** > **Windows-Registrierung** > **Seite zum Registrierungsstatus (Vorschau)**.
2. Zeigen Sie auf das Profil in der Liste.
3. Ziehen Sie mithilfe der drei vertikalen Punkte das Profil an die gewünschte Position in der Liste.


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
- Konnektivitätsprofile
    - VPN- oder WLAN-Profile, die **allen Geräten** oder einer Gerätegruppe zugewiesen sind, in der das zu registrierende Gerät ein Mitglied ist, jedoch nur für Autopilot-Geräte
- Zertifikat-Profile, die **allen Geräten** oder einer Gerätegruppe zugewiesen sind, in der das zu registrierende Gerät ein Mitglied ist, jedoch nur für Autopilot-Geräte

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
