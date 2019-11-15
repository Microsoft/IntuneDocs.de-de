---
title: Integrieren von Jamf Pro in Microsoft Intune zu Konformitätszwecken
titleSuffix: Microsoft Intune
description: Verwenden Sie die Konformitätsrichtlinien von Microsoft Intune zusammen mit dem bedingten Zugriff von Azure Active Directory, um mit Jamf verwaltete Geräte zu integrieren und zu sichern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 39d687c8c9b75182ba0e7d4020c6b840c753a231
ms.sourcegitcommit: a4c7339ec9ff5b1b846cb3cca887cf91b5cd4baa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627659"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrieren von Jamf Pro in Intune zu Konformitätszwecken

Gilt für: Intune im Azure-Portal

Wenn Ihre Organisation [Jamf Pro](https://www.jamf.com) zur Verwaltung von macOS-Geräten verwendet, können Sie Microsoft Intune-Konformitätsrichtlinien zusammen mit dem bedingten Zugriff von Azure Active Directory (Azure AD) verwenden, um sicherzustellen, dass Geräte in Ihrer Organisation konform sind, ehe sie auf Unternehmensressourcen zugreifen dürfen. In diesem Artikel erfahren Sie, wie Sie die Jamf-Integration in Intune konfigurieren.

Wenn Jamf Pro in Intune integriert ist, können Sie die Bestandsdaten von macOS-Geräten über Azure AD mit Intune synchronisieren. Das Konformitätsmodul von Intune analysiert anschließend die Bestandsdaten, um einen Bericht zu erstellen. Die Analyse von Intune wird mit Informationen zur Azure AD-Identität des Gerätebenutzers kombiniert, um die Erzwingung über bedingten Zugriff zu steuern. Geräte, die mit den Richtlinien für bedingten Zugriff kompatibel sind, können Zugriff auf geschützte Unternehmensressourcen erhalten.

Nach der Konfiguration der Integration [konfigurieren Sie dann Jamf und Intune, um die Konformität mithilfe des bedingten Zugriffs](conditional-access-assign-jamf.md) auf von Jamf verwalteten Geräten zu erzwingen.  


## <a name="prerequisites"></a>Voraussetzungen

### <a name="products-and-services"></a>Produkte und Dienste
Zur Konfiguration des bedingten Zugriffs mit Jamf Pro benötigen Sie Folgendes:

- Jamf Pro 10.1.0 oder höher
- [Die Unternehmensportal-App für macOS](https://aka.ms/macoscompanyportal)
- macOS-Geräte mit OS X 10.11 Yosemite oder höher

### <a name="network-ports"></a>Netzwerkports
<!-- source: https://support.microsoft.com/en-us/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune -->
Jamf und Intune müssen auf die folgenden Ports zugreifen können, um eine einwandfreie Integration zu gewährleisten: 
- **Intune**: Port 443
- **Apple**: Ports 2195, 2196 und 5223 (Pushbenachrichtigungen an Intune)
- **Jamf**: Ports 80 und 5223

Damit APNS im Netzwerk ordnungsgemäß funktioniert, müssen Sie auch ausgehende Verbindungen zu und Umleitungen von folgenden Ports aktivieren:
- den Apple-Block 17.0.0.0/8 über die TCP-Ports 5223 und 443 aus allen Clientnetzwerken.   
- Ports 2195 und 2196 von Jamf Pro-Servern.  

Weitere Informationen zu diesen Ports finden Sie in den folgenden Artikeln:  
- [Bandbreiten- und andere Anforderungen an die Netzwerkkonfiguration für Intune](../fundamentals/network-bandwidth-use.md)
- [Network Ports Used by Jamf Pro](https://www.jamf.com/jamf-nation/articles/34/network-ports-used-by-jamf-pro) (von Jamf Pro verwendete Netzwerkports) auf jamf.com
- [Von Apple-Softwareprodukten verwendete TCP- und UDP-Ports](https://support.apple.com/HT202944) auf support.apple.com


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

8. Wählen Sie auf der Seite **API-Berechtigungen** die Option **Administratorzustimmung für _\<Ihren Mandanten>_ erteilen** aus, und klicken Sie dann auf **Ja**.  Nachdem die App erfolgreich registriert wurde, sollten die API-Berechtigungen folgendermaßen aussehen: ![Erfolgreiche Berechtigungen](./media/conditional-access-integrate-jamf/sucessfull-app-registration.png)

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
