---
title: Einstellungen für gemeinsam genutzte Windows 10-Geräte – Microsoft Intune (Azure) | Microsoft-Dokumentation
description: Fügen Sie Windows 10 hinzu, um Geräte zu konfigurieren, die gemeinsam genutzt oder von mehreren Benutzern in Microsoft Intune verwendet werden. Hier finden Sie eine Liste mit allen Einstellungen und ihren Auswirkungen auf die Geräte (einschließlich Microsoft Surface). Verwalten Sie Gastkonten und sonstige Konten, löschen Sie inaktive Konten, aktivieren oder deaktivieren Sie das Speichern auf lokalen Speichermedien, legen Sie Energieoptionen und den Zeitpunkt für die Installation fest und verwenden Sie Geräte, die im Bildungsbereich eingesetzt werden, in einem Gerätekonfigurationsprofil.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/01/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 535f66c68b066454ce9706b1dd1d7a4fce5c265c
ms.sourcegitcommit: e63e3debb5f4d9a757f767913e72e39742137b17
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2019
ms.locfileid: "58788486"
---
# <a name="windows-10-and-later-settings-to-manage-shared-devices-using-intune"></a>Einstellungen für Windows 10 (und höher) für die Verwaltung von gemeinsam genutzten Geräten mithilfe von Intune

Geräte mit Windows 10 und höher (z. B. Microsoft Surface-Geräte) können von vielen Benutzern verwendet werden. Geräte mit mehreren Benutzern werden als „gemeinsam genutzte Geräte“ bezeichnet und sind in den Lösungen für die mobile Geräteverwaltung (Mobile Device Management, MDM) enthalten.

Mithilfe von Microsoft Intune können Endbenutzer sich bei gemeinsam genutzten Geräten mit einem Gastkonto anmelden. Bei der Verwendung des Geräts erhalten diese Benutzer dann nur Zugriff auf von Ihnen ausgewählte Features. Als Intune-Administrator können Sie unter anderem den Zugriff für gemeinsam genutzte Windows 10-Geräte konfigurieren, festlegen, wann Konten gelöscht werden, und Einstellungen für die Energieverwaltung vornehmen.

In diesem Artikel werden die Einstellungen aufgeführt und beschrieben, die in einem Gerätekonfigurationsprofil für Windows 10 (und höher) verwendet werden können. Wenn das Profil in Intune erstellt wird, stellen Sie das Profil für die Gerätegruppen in Ihrer Organisation bereit oder weisen es diesen zu. Sie können dieses Profil ebenfalls zu Gerätegruppen mit gemischten Gerätetypen und Betriebssystemversionen zuweisen.

Weitere Informationen zu diesem Intune-Feature finden Sie unter [Control access, accounts, and power features on shared PC or multi-user devices (Features für das Steuern von Zugriff, Konten und Energieeinstellungen auf gemeinsam genutzten Computern oder Geräten mit mehreren Benutzern)](shared-user-device-settings.md). Weitere Informationen zum Windows-Konfigurationsdienstanbieter (Configuration Service Provider, CSP) finden Sie unter [SharedPC CSP (Konfigurationsdienstanbieter „SharedPC“)](https://docs.microsoft.com/windows/client-management/mdm/sharedpc-csp).

## <a name="before-your-begin"></a>Vorbereitungen

[Erstellen Sie das Profil.](shared-user-device-settings.md)

## <a name="shared-multi-user-device-settings"></a>Einstellungen für von mehreren Benutzern gemeinsam genutzte Geräte

- **Freigegebene PC-Modus**: Wählen Sie **aktivieren** um freigegebene PC-Modus zu aktivieren. In diesem Modus kann sich nur jeweils ein Benutzer auf dem Gerät anmelden. Ein anderer Benutzer kann sich erst anmelden, nachdem der aktuelle Benutzer sich abgemeldet hat. **Nicht konfiguriert** (Standard):Diese Einstellung wird von Intune nicht verwaltet und nicht mithilfe von Richtlinien auf den Geräten kontrolliert.
- **Gastkonto**: Aktivieren Sie diese Einstellung, damit die Option „Gast“ auf dem Anmeldebildschirm verfügbar ist. Für Gastkonten sind keine Anmeldeinformationen und keine Authentifizierung erforderlich. Für diese Einstellung wird bei jeder Verwendung ein neues lokales Konto erstellt. Folgende Optionen sind verfügbar:
  - **Gast**: Erstellt ein lokales Gastkonto auf dem Gerät.
  - **Domäne**: Erstellt ein Gastkonto in Azure Active Directory (AD).
  - **Gast und Domäne**: Erstellt ein lokales Gastkonto auf dem Gerät und ein Gastkonto in Azure Active Directory (AD).
- **Kontoverwaltung**: Bei Festlegung auf **Aktivieren** werden lokale Gastkonten und Konten in AD und Azure AD automatisch gelöscht. Wenn ein Benutzer sich von einem Gerät abmeldet oder die Systemwartung ausgeführt wird, werden diese Konten gelöscht. Wenn diese Option aktiviert ist, sollten sie auch die folgenden festlegen:
  - **Konto löschen**: auswählen, wenn Konten gelöscht werden: **auf Storage Space Schwellenwert**, **speicherplatzschwellenwert für Speicher und inaktive Schwellenwert**, oder **unmittelbar nach der Abmeldung** . Geben Sie außerdem Folgendes ein:
    - **Start löschen threshold(%)**: Geben Sie einen Prozentwert (0 – 100) der Speicherplatz auf dem Datenträger. Wenn der gesamte Speicherplatz unter den eingegebenen Wert fällt, werden die zwischengespeicherten Konten gelöscht. Es werden fortlaufend Konten gelöscht, um Speicherplatz freizugeben. Die Konten, die am längsten inaktiv sind, werden zuerst gelöscht.
    - **Beenden Sie die Delete-threshold(%)**: Geben Sie einen Prozentwert (0 – 100) der Speicherplatz auf dem Datenträger. Wenn der gesamte Speicherplatz dem eingegebenen Wert entspricht, werden keine Konten mehr gelöscht.

  Legen Sie die Option auf **Deaktivieren** fest, um die lokalen, AD- und Azure AD-Gastkonten beizubehalten.

- **Lokaler Speicher**: Bei Festlegung auf **Aktiviert** wird verhindert, dass Benutzer Dateien auf der Festplatte des Geräts speichern und anzeigen. Wählen Sie **Deaktiviert** aus, wenn Sie Benutzern das Aufrufen von Dateien und das lokale Speichern von Dateien über den Datei-Explorer ermöglichen möchten. **Nicht konfiguriert** (Standard):Diese Einstellung wird von Intune nicht verwaltet und nicht mithilfe von Richtlinien auf den Geräten kontrolliert.
- **Energieverwaltungsrichtlinien**: Bei Festlegung auf **Aktiviert** können Benutzer den Ruhezustand nicht deaktivieren, die Aktionen für den Energiesparmodus nicht überschreiben (wie das Zuklappen des Geräts) und die Energieeinstellungen nicht ändern. Wenn Sie diese Option auf **Deaktiviert** festlegen, können Benutzer das Gerät in den Ruhezustand versetzen, das Gerät schließen, um den Energiesparmodus zu aktivieren und die Energieeinstellungen ändern. **Nicht konfiguriert** (Standard):Diese Einstellung wird von Intune nicht verwaltet und nicht mithilfe von Richtlinien auf den Geräten kontrolliert.
- **Timeout (in Sekunden) Standbymodus**: Geben Sie die Anzahl der inaktiven Sekunden (0 – 100), bevor das Gerät in den Energiesparmodus wechselt. Wenn Sie keine Zeit festlegen, wird das Gerät nach 60 Minuten in den Energiesparmodus versetzt.
- **Anmeldung bei PC-Reaktivierung**: Bei Festlegung auf **Aktiviert** müssen sich Benutzer mit einem Kennwort anmelden, wenn das Gerät aus dem Energiesparmodus reaktiviert wird. Legen Sie die Option auf **Deaktiviert** fest, damit die Benutzer keinen Benutzernamen und kein Kennwort eingeben müssen. **Nicht konfiguriert** (Standard):Diese Einstellung wird von Intune nicht verwaltet und nicht mithilfe von Richtlinien auf den Geräten kontrolliert.
- **Starten der Wartung (in Minuten nach Mitternacht)**: Geben Sie die Zeit in Minuten (0-1440) automatische Wartungstasks, z. B. Windows Update, wenn ausführen. Die Standardzeit für den Start ist auf Mitternacht bzw. null (`0`) Minuten festgelegt. Ändern Sie die Startzeit, indem Sie eine Startzeit in Minuten (von Mitternacht aus) eingeben. Wenn Sie die Wartung beispielsweise um 2 Uhr morgens durchführen möchten, geben Sie `120` ein. Wenn Sie die Wartung um 20 Uhr durchführen möchten, geben Sie `1200` ein.
- **Education-Richtlinien**: Bei Festlegung auf **Aktiviert** werden die empfohlenen (eingeschränkteren) Einstellungen für Geräte in Bildungseinrichtungen verwendet. Wählen Sie **Deaktiviert** aus, damit die empfohlenen Standardrichtlinien für Geräte in Bildungseinrichtungen nicht verwendet werden. **Nicht konfiguriert** (Standard):Diese Einstellung wird von Intune nicht verwaltet und nicht mithilfe von Richtlinien auf den Geräten kontrolliert.

  Weitere Informationen zu den Bildungsrichtlinien finden Sie unter [Windows 10 configuration recommendations for education customers (Empfehlungen für die Konfiguration von Windows 10 für Kunden im Bildungsbereich)](https://docs.microsoft.com/education/windows/configure-windows-for-education).

> [!TIP]
> [Richten Sie einen freigegebenen oder Gastkonten PC](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc) (öffnet eine andere Docs-Website) ist eine hervorragende Ressource für Windows 10-Feature, einschließlich Konzepten und Gruppenrichtlinien, die im freigegebenen Modus festgelegt werden können.

## <a name="next-steps"></a>Nächste Schritte

- [Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)
- Einstellungen für [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md)
