---
title: Integrieren von Jamf Pro in Microsoft Intune zu Konformitätszwecken | Microsoft Intune
description: Verwenden Sie die Konformitätsrichtlinien für Microsoft Intune zusammen mit dem bedingten Zugriff auf Azure Active Directory, um mit Jamf verwaltete Geräte zu sichern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/12/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 8e607dc612f71cdf72322b9fa7ecf14abb5fd809
ms.sourcegitcommit: d54a12a836503f7e8b90346f16b7ad2d83b710dc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "54270587"
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

## <a name="create-an-application-in-azure-active-directory"></a>Registrieren einer Anwendung in Azure Active Directory

1. Navigieren Sie im [Azure-Portal](https://portal.azure.com) zu **Azure Active Directory** > **App-Registrierungen**.
2. Wählen Sie anschließend **Neue Anwendungsregistrierung** aus.
3. Geben Sie einen **Anzeigenamen** ein, z.B. **Bedingter Zugriff in Jamf**.
4. Wählen Sie **Web-App/API**.
5. Geben Sie die **Anmelde-URL** in Form Ihrer Jamf Pro-Instanz-URL an.
6. Wählen Sie **Erstellen** aus. Die Anwendung wird erstellt, und im Portal werden die Anwendungsdetails angezeigt.
7. Speichern Sie eine Kopie der **Anwendungs-ID** für die neue Anwendung. Sie geben die ID zu einem späteren Zeitpunkt in einer Prozedur an. Wählen Sie als Nächstes **Einstellungen** aus, und wechseln Sie zu **API-Zugriff** > **Schlüssel**.
8. Geben Sie im Bereich *Schlüssel* eine **Beschreibung** ein, wie lange gewartet werden soll, bevor er **abläuft**. Wählen Sie dann **Speichern** aus, um den Anwendungsschlüssel (Wert) zu generieren.

   > [!IMPORTANT]
   > Der Anwendungsschlüssel wird während dieses Vorgangs nur einmal angezeigt. Achten Sie darauf, dass Sie ihn an einer Stelle speichern, an der Sie ihn problemlos abrufen können.

8. Navigieren Sie im Bereich *Einstellungen* für die App zu **API-Zugriff** > **Erforderliche Berechtigungen**. Wählen Sie alle vorhandenen Berechtigungen aus, und klicken Sie dann auf **Löschen**, um alle Berechtigungen zu löschen. Das Löschen vorhandener Berechtigungen ist notwendig, wenn Sie eine neue Berechtigung hinzufügen, und die Anwendung funktioniert nur, wenn sie ausschließlich über die erforderliche Berechtigung verfügt.  
9. Um eine neue Berechtigung zuzuweisen, wählen Sie **+ Hinzufügen** > **Hiermit wählen Sie eine API aus** > **Microsoft Intune-API** aus und klicken dann auf **Auswählen**.
10. Wählen Sie im Bereich *Zugriff aktivieren* die Option **Geräteattribute an Microsoft Intune senden** aus. Klicken Sie auf **Auswählen** und dann auf **Fertig**.
11. Wählen Sie im Bereich *Erforderliche Berechtigungen* die Option **Berechtigungen erteilen** und dann **Ja** aus, um die erforderlichen Berechtigungen auf die Anwendung anzuwenden.

    > [!NOTE]
    > Wenn der Anwendungsschlüssel abläuft, müssen Sie einen neuen Anwendungsschlüssel in Microsoft Azure erstellen und dann die Daten für den bedingten Zugriff in Jamf Pro aktualisieren. In Azure kann sowohl der alte als auch der neue Schlüssel aktiv sein, um Dienstunterbrechungen zu verhindern.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Ermöglichen einer Integration von Intune in Jamf Pro

1. Wechseln Sie im [Azure-Portal](https://portal.azure.com) zu **Microsoft Intune** > **Gerätekonformität** > **Partnergeräteverwaltung**.
2. Aktivieren Sie den Konformitätsconnector für Jamf durch Einfügen der zuvor gespeicherten Anwendungs-ID in das Feld **Azure Active Directory-App-ID für Jamf**.
3. Wählen Sie **Speichern** aus.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Konfigurieren der Microsoft Intune-Integration in Jamf Pro

1. Navigieren Sie in Jamf Pro zu **Global Management** > **Conditional Access** (Globale Verwaltung > Bedingter Zugriff). Klicken Sie auf der Registerkarte **Integration von Intune** auf die Schaltfläche **Bearbeiten**.
2. Aktivieren Sie das Kontrollkästchen **Integration von Microsoft Intune aktivieren**.
3. Geben Sie die erforderlichen Informationen zu Ihrem Azure-Mandanten ein, einschließlich **Location** (Standort) und **Domain name** (Domänenname) sowie die Angaben zu **Application ID** (Anwendungs-ID) und **Application Key** (Anwendungsschlüssel), die Sie in den vorherigen Schritten gespeichert haben.
4. Wählen Sie **Speichern** aus. Jamf Pro testet Ihre Einstellungen und überprüft den Erfolg des Vorgangs.

## <a name="set-up-compliance-policies-and-register-devices"></a>Einrichten von Konformitätsrichtlinien und Registrieren von Geräten

Nach dem Konfigurieren der Integration zwischen Intune und Jamf verwenden Sie die Option [Anwenden von Konformitätsrichtlinien auf mit Jamf verwaltete Geräte](conditional-access-assign-jamf.md).

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
