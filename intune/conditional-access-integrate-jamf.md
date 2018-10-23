---
title: Integrieren von Jamf Pro in Microsoft Intune zu Konformitätszwecken
titlesuffix: ''
description: Verwenden Sie die Konformitätsrichtlinien für Microsoft Intune zusammen mit dem bedingten Zugriff auf Azure Active Directory, um mit Jamf verwaltete Geräte zu sichern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0b4af0a638d86d32b244c3a34f8039e466394736
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2018
ms.locfileid: "49424933"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrieren von Jamf Pro in Intune zu Konformitätszwecken

Gilt für: Intune im Azure-Portal

Wenn Ihre Organisation [Jamf Pro](https://www.jamf.com) zur Verwaltung der Macs Ihrer Endbenutzer verwendet, können Sie Microsoft Intune-Konformitätsrichtlinien zusammen mit dem bedingten Zugriff in Azure Active Directory verwenden, um die Konformität von Geräten in Ihrer Organisation zu gewährleisten.

## <a name="prerequisites"></a>Voraussetzungen

Zur Konfiguration des bedingten Zugriffs mit Jamf Pro benötigen Sie Folgendes:

- Jamf Pro 10.1.0 oder höher
- [Die Unternehmensportal-App für macOS](https://aka.ms/macoscompanyportal)
- macOS-Geräte mit OS X 10.11 Yosemite oder höher

## <a name="connecting-intune-to-jamf-pro"></a>Herstellen einer Verbindung zwischen Intune und Jamf Pro

Eine Verbindung zwischen Intune und Jamf Pro können Sie folgendermaßen herstellen:

1. Erstellen einer neuen Anwendung in Azure
2. Ermöglichen einer Integration von Intune in Jamf Pro
3. Konfigurieren des bedingten Zugriffs in Jamf Pro

## <a name="create-a-new-application-in-azure-active-directory"></a>Erstellen einer neuen Anwendung in Azure Active Directory

1. Öffnen Sie **Azure Active Directory** > **App-Registrierungen**.
2. Klicken Sie auf **+Registrierung einer neuen Anwendung**.
3. Geben Sie einen **Anzeigenamen** ein, z.B. **Bedingter Zugriff in Jamf**.
4. Wählen Sie **Web-App/API**.
5. Geben Sie die **Anmelde-URL** in Form Ihrer Jamf Pro-Instanz-URL an.
6. Klicken Sie auf **Anwendung erstellen**.
7. Speichern Sie die neu erstellte **Anwendungs-ID**. Öffnen Sie dann **Einstellungen**, und navigieren Sie zu **API-Zugriff** > **Schlüssel**, um einen neuen Anwendungsschlüssel zu erstellen. Geben Sie eine **Beschreibung** und eine **Ablaufzeit** ein, und speichern Sie dann den Anwendungsschlüssel.

   > [!IMPORTANT]
   > Der Anwendungsschlüssel wird während dieses Vorgangs nur einmal angezeigt. Achten Sie darauf, dass Sie ihn an einer Stelle speichern, an der Sie ihn problemlos abrufen können.

8. Öffnen Sie **Einstellungen**, und navigieren Sie dann zu **API-Zugriff** > **Erforderliche Berechtigungen**, und löschen Sie alle Berechtigungen.

   > [!NOTE]
   > Fügen Sie eine neue erforderliche Berechtigung hinzu. Die Anwendung kann nur ordnungsgemäß funktionieren, wenn sie die einzelne erforderliche Berechtigung aufweist.

9. Wählen Sie **Microsoft Intune-API**, und klicken Sie auf **Auswählen**.
10. Wählen Sie **Geräteattribute an Microsoft Intune senden**, und klicken Sie auf **Auswählen**.
11. Klicken Sie auf die Schaltfläche **Berechtigungen erteilen**, nachdem Sie die erforderlichen Berechtigungen für die Anwendung gespeichert haben.

    > [!NOTE]
    > Wenn der Anwendungsschlüssel abläuft, müssen Sie einen neuen Anwendungsschlüssel in Microsoft Azure erstellen und dann die Daten für den bedingten Zugriff in Jamf Pro aktualisieren. In Azure kann sowohl der alte als auch der neue Schlüssel aktiv sein, um Dienstunterbrechungen zu verhindern.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Ermöglichen einer Integration von Intune in Jamf Pro

1. Öffnen Sie im Microsoft Azure-Portal **Microsoft Intune** > **Gerätekonformität** > **Partner > Geräteverwaltung**.
2. Aktivieren Sie den Konformitätsconnector für Jamf durch Einfügen der Anwendungs-ID in das Feld **Azure Active Directory-App-ID für Jamf**.
3. Klicken Sie auf **Speichern**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Konfigurieren der Microsoft Intune-Integration in Jamf Pro

1. Navigieren Sie in Jamf Pro zu **Global Management** > **Conditional Access** (Globale Verwaltung > Bedingter Zugriff). Klicken Sie auf der Registerkarte **Integration von Intune** auf die Schaltfläche **Bearbeiten**.
2. Aktivieren Sie das Kontrollkästchen **Integration von Microsoft Intune aktivieren**.
3. Geben Sie die erforderlichen Informationen zu Ihrem Azure-Mandanten ein, einschließlich **Location** (Standort) und **Domain name** (Domänenname) sowie die Angaben zu **Application ID** (Anwendungs-ID) und **Application Key** (Anwendungsschlüssel), die Sie in den vorherigen Schritten gespeichert haben.
4. Klicken Sie auf **Speichern**. Jamf Pro testet Ihre Einstellungen und überprüft den Erfolg des Vorgangs.

## <a name="set-up-compliance-policies-and-register-devices"></a>Einrichten von Konformitätsrichtlinien und Registrieren von Geräten

Nachdem Sie die Konfiguration der Integration zwischen Intune und Jamf abgeschlossen haben, müssen Sie [Konformitätsrichtlinien zu von Jamf verwalteten Geräten ](conditional-access-assign-jamf.md) zuordnen.

## <a name="information-shared-from-jamf-pro-to-intune"></a>Von Jamf Pro für Intune freigegebene Informationen

Jamf Pro erfasst Inventurinformationen zu verwalteten macOS-Geräten. Jamf Pro meldet die folgenden Informationen an Intune:

* Azure AD-Geräte-ID
* JAMF-Inventurstatus (Inventurstatus eines Computers, der sich innerhalb der letzten 24 Stunden bei Jamf Pro eingecheckt hat)
* Betriebssystemversion
* Azure AD-Benutzer-ID
* Verschlüsselt (FileVault 2)
* Gatekeeperstatus
* Kennwort: Mindestanzahl von Zeichensätzen
* Kennwortablauf (Tage)
* Kennworttyp: einfach, alphanumerisch oder unbekannt
* Automatische Anmeldung verhindern
* Erforderliche Kennungslänge
* Kennwort: Anzahl vorheriger Kennwörter zum Verhindern der Wiederverwendung
* Systemintegritätsschutz
* Zeitpunkt des letzten Check-Ins
* Architekturtyp
* Verfügbare Speichersteckplätze
* Akkukapazität
* Start-ROM
* Busgeschwindigkeit
* Cachegröße
* Gerätename
* Domäne beitreten
* Jamf-ID
* MAC-Adresse
* Automarke
* Modell
* Modellbezeichnung
* NIC-Geschwindigkeit
* Anzahl der Kerne
* Prozessoranzahl
* Betriebssystem
* Plattform
* Prozessorgeschwindigkeit
* Prozessortyp
* Sekundäre MAC-Adresse
* Seriennummer
* SMC-Version
* RAM gesamt
* UDID
* Benutzer-E-Mail-Adresse

## <a name="next-steps"></a>Nächste Schritte

- [Anwenden von Konformitätsrichtlinien auf mit Jamf verwaltete Geräte](conditional-access-assign-jamf.md)
