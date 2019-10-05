---
title: Integrieren von Jamf Pro in Microsoft Intune zu Konformitätszwecken
titleSuffix: Microsoft Intune
description: Verwenden Sie die Konformitätsrichtlinien von Microsoft Intune zusammen mit dem bedingten Zugriff von Azure Active Directory, um mit Jamf verwaltete Geräte zu sichern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b439067d06cf49a4ff83288e109d1fccd3801106
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722721"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrieren von Jamf Pro in Intune zu Konformitätszwecken

Gilt für: Intune im Azure-Portal

Wenn Ihre Organisation [Jamf Pro](https://www.jamf.com) zur Verwaltung der Mac-Geräte Ihrer Endbenutzer verwendet, können Sie Microsoft Intune-Konformitätsrichtlinien zusammen mit dem bedingten Zugriff von Azure Active Directory verwenden, um die Konformität von Geräten in Ihrer Organisation zu gewährleisten.

## <a name="prerequisites"></a>Voraussetzungen

Zur Konfiguration des bedingten Zugriffs mit Jamf Pro benötigen Sie Folgendes:

- Jamf Pro 10.1.0 oder höher
- [Die Unternehmensportal-App für macOS](https://aka.ms/macoscompanyportal)
- macOS-Geräte mit OS X 10.11 Yosemite oder höher

## <a name="connect-intune-to-jamf-pro"></a>Herstellen einer Verbindung zwischen Intune und Jamf Pro

So stellen Sie eine Verbindung zwischen Intune und Jamf Pro her:

1. Erstellen Sie eine neue Anwendung in Azure.
2. Ermöglichen Sie eine Integration von Intune in Jamf Pro.
3. Konfigurieren Sie den bedingten Zugriff in Jamf Pro.

## <a name="create-an-application-in-azure-active-directory"></a>Registrieren einer Anwendung in Azure Active Directory

1. Navigieren Sie im [Azure-Portal](https://portal.azure.com) zu **Azure Active Directory** > **App-Registrierungen**, und wählen Sie dann **Neue Registrierung** aus. 

2. Geben Sie auf der Seite **Anwendung registrieren** folgende Details an:
   - Geben Sie im Abschnitt **Name** einen aussagekräftigen Anwendungsnamen ein, z. B. **Bedingter Jamf-Zugriff**.
   - Wählen Sie im Abschnitt **Unterstützte Kontotypen** die Option **Konten in einem Organisationsverzeichnis** aus. 
   - Für den **Umleitungs-URI** übernehmen Sie den Standardwert „Web“, und geben Sie dann die URL für Ihre Jamf Pro-Instanz an.  

3. Wählen Sie **Registrieren** aus, um die Anwendung zu erstellen und die Seite **Übersicht** für die neue App zu öffnen.  

4. Kopieren Sie auf der App-Seite **Übersicht** den Wert der **Anwendungs-ID (Client)** , und notieren Sie ihn zur späteren Verwendung. Sie benötigen diesen Wert bei späteren Prozeduren.  

5. Wählen Sie unter **Verwalten** **Zertifikate und Geheimnisse** aus. Wählen Sie die Schaltfläche **Neuer geheimer Clientschlüssel** aus. Geben Sie einen Wert in **Beschreibung** ein, wählen Sie eine Option für **Gültig bis** aus, und wählen Sie **Hinzufügen** aus.

   > [!IMPORTANT]  
   > Bevor Sie diese Seite verlassen, kopieren Sie den Wert für den geheimen Clientschlüssel, und notieren Sie ihn zur späteren Verwendung. Sie benötigen diesen Wert bei späteren Prozeduren. Dieser Wert ist nicht noch mal verfügbar, ohne die App-Registrierung neu zu erstellen.  

6. Wählen Sie unter **Verwalten** die Option **API-Berechtigungen** aus. Wählen Sie die vorhandenen Berechtigungen aus, und wählen Sie dann **Berechtigung entfernen** aus, um diese Berechtigungen zu löschen. Das Entfernen aller vorhandenen Berechtigungen ist notwendig, wenn Sie eine neue Berechtigung hinzufügen, und die Anwendung funktioniert nur, wenn sie ausschließlich über die erforderliche Berechtigung verfügt.  

7. Um eine neue Berechtigung hinzuzufügen, wählen Sie **Berechtigung hinzufügen** aus. Wählen Sie auf der Seite **API-Berechtigungen anfordern** den Eintrag **Intune** aus, und wählen Sie dann **Anwendungsberechtigungen** aus. Aktivieren Sie nur das Kontrollkästchen für **update_device_attributes**.  

   Wählen Sie **Berechtigung hinzufügen** aus, um diese Konfiguration zu speichern.  

8. Wählen Sie auf der Seite **API-Berechtigungen** die Option **Administratoreinwilligung für Microsoft gewähren** aus, und klicken Sie dann auf **Ja**.  

   Der Prozess der App-Registrierung in Azure AD ist abgeschlossen.


    > [!NOTE]
    > Wenn der geheime Clientschlüssel abläuft, müssen Sie in Azure einen neuen geheimen Clientschlüssel erstellen und dann die Daten für den bedingten Zugriff in Jamf Pro aktualisieren. In Azure kann sowohl das alte als auch das neue Geheimnis aktiv sein, um Dienstunterbrechungen zu verhindern.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Ermöglichen einer Integration von Intune in Jamf Pro

1. Melden Sie sich bei Intune an, und wechseln Sie im [Azure-Portal](https://go.microsoft.com/fwlink/?linkid=2090973) zu **Microsoft Intune** > **Gerätekonformität** > **Partnergeräteverwaltung**.

2. Aktivieren Sie den Konformitätsconnector für Jamf durch Einfügen der zuvor gespeicherten Anwendungs-ID in das Feld **Azure Active Directory-App-ID für Jamf**.

3. Wählen Sie **Speichern** aus.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Konfigurieren der Microsoft Intune-Integration in Jamf Pro

1. Navigieren Sie in Jamf Pro zu **Global Management** > **Conditional Access** (Globale Verwaltung > Bedingter Zugriff). Klicken Sie auf der Registerkarte **macOS Intune Integration** (Intune-Integration in macOS) auf die Schaltfläche **Edit** (Bearbeiten).

2. Aktivieren Sie das Kontrollkästchen **Enable Intune Integration for macOS** (Integration von Intune für macOS aktivieren).

3. Geben Sie die erforderlichen Informationen zu Ihrem Azure-Mandanten ein, einschließlich **Location** (Standort), **Domain name** (Domänenname), der **Application ID** (Anwendungs-ID) und dem Wert für den *Client Secret* (Geheimer Clientschlüssel), den gespeichert haben, als Sie die App in Azure AD erstellt haben.  

4. Wählen Sie **Speichern** aus. Jamf Pro testet Ihre Einstellungen und überprüft den Erfolg des Vorgangs.

## <a name="set-up-compliance-policies-and-register-devices"></a>Einrichten von Konformitätsrichtlinien und Registrieren von Geräten

Nach dem Konfigurieren der Integration zwischen Intune und Jamf verwenden Sie die Option [Anwenden von Konformitätsrichtlinien auf mit Jamf verwaltete Geräte](conditional-access-assign-jamf.md).

## <a name="disconnect-jamf-pro-and-intune"></a>Trennen von Jamf Pro und Intune 

Wenn Sie Jamf Pro nicht mehr zum Verwalten von Macs in Ihrer Organisation verwenden und Benutzer in Intune verwaltet werden sollen, müssen Sie die Verbindung zwischen Jamf Pro und Intune entfernen. Entfernen Sie die Verbindung über die Jamf Pro-Konsole. 

1. Navigieren Sie in Jamf Pro zu **Global Management** > **Conditional Access** (Globale Verwaltung > Bedingter Zugriff). Klicken Sie auf der Registerkarte **macOS Intune Integration** (Intune-Integration in macOS) auf **Edit** (Bearbeiten).
2. Deaktivieren Sie das Kontrollkästchen **Enable Intune Integration for macOS** (Integration von Intune für macOS aktivieren).
3. Wählen Sie **Speichern** aus. Jamf Pro sendet Ihre Konfiguration an Intune, und die Integration wird beendet.
4. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an. Wechseln Sie zu **Microsoft Intune** > **Gerätekonformität** > **Partnergeräteverwaltung**, um zu überprüfen, ob der Status jetzt **Beendet** lautet. 

   > [!NOTE]
   > Die Mac-Geräte Ihrer Organisation werden an dem Datum (3 Monate) entfernt, das in der Konsole angezeigt wird. 

## <a name="next-steps"></a>Nächste Schritte

- [Anwenden von Konformitätsrichtlinien auf mit Jamf verwaltete Geräte](conditional-access-assign-jamf.md)
- [Von Jamf Pro an Intune gesendete Daten](data-jamf-sends-to-intune.md)