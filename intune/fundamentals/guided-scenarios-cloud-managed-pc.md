---
title: 'Geführtes Szenario: Über die Cloud verwalteter moderner Desktop'
titleSuffix: Microsoft Intune
description: Erfahren Sie mehr über das geführte Szenario zum Einrichten und Konfigurieren eines modernen Standarddesktops über das Microsoft 365-Geräteverwaltungsportal.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f78f3696827ebd50084f0e4b012c5f94427eeb35
ms.sourcegitcommit: 15e099a9a1e18296580bb345610aee7cc4acd126
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164562"
---
# <a name="guided-scenario---cloud-managed-modern-desktop"></a>Geführtes Szenario: Über die Cloud verwalteter moderner Desktop

Der moderne Desktop ist die hochmoderne Produktivitätsplattform für den Information-Worker. Office 365 ProPlus und Windows 10 sind zusammen mit den neuesten Sicherheitsbaselines für Windows 10 und Microsoft Defender Advanced Threat Protection die Kernkomponenten des modernen Desktops. 

Die Verwaltung des modernen Desktops aus der Cloud bringt zusätzlichen Nutzen internetweiter Remoteaktionen. Die Cloudverwaltung nutzt die integrierten Richtlinien der Verwaltung mobiler Geräte für Windows und entfernt Abhängigkeiten von lokalen Active Directory-Gruppenrichtlinien. 

Wenn Sie einen über die Cloud verwalteten modernen Desktop in Ihrem eigenen Unternehmen evaluieren möchten, definiert dieses geführte Szenario alle notwendigen Konfigurationen für eine Standardbereitstellung vor. In diesem geführten Szenario erstellen Sie eine sichere Umgebung, in der Sie die Funktionen der Geräteverwaltung von Intune ausprobieren können. 

## <a name="prerequisites"></a>Voraussetzungen
- [Legen Sie die MDM-Autorität auf Intune fest](~/fundamentals/mdm-authority-set.md#set-mdm-authority-to-intune) – Die Einstellung für die Autorität für die Verwaltung mobiler Geräte (Mobile Device Management, MDM) bestimmt, wie Sie Ihre Geräte verwalten. Als IT-Administrator müssen Sie eine MDM-Autorität festlegen, damit Benutzer Geräte zur Verwaltung registrieren können.
- Mindestens Microsoft 365 E3 (oder Microsoft 365 E5 für beste Sicherheit)
- Windows 10 1903-Gerät (registriert mit Windows Autopilot für eine optimale Endbenutzererfahrung)
- Intune-Administratorrechte sind erforderlich, um dieses geführte Szenario abzuschließen:
  - Gerätekonfiguration: Lesen, Erstellen, Löschen, Zuweisen und Aktualisieren
  - Registrierungsprogramme: Gerät lesen, Profil lesen, Profil erstellen, Profil zuweisen, Profil löschen
  - Mobile Apps: Lesen, Erstellen, Löschen, Zuweisen und Aktualisieren
  - Organisationsberechtigungen: Lesen und Aktualisieren
  - Sicherheitsbaselines: Lesen, Erstellen, Löschen, Zuweisen und Aktualisieren
  - Richtliniensätze: Lesen, Erstellen, Löschen, Zuweisen und Aktualisieren

## <a name="step-1---introduction"></a>Schritt 1: Einführung

In diesem Szenario richten Sie einen Testbenutzer ein, registrieren ein Gerät in Intune und stellen das Gerät mit den von Intune empfohlenen Einstellungen sowie Windows 10 und Office ProPlus bereit. Ihr Gerät wird auch für Microsoft Defender Advanced Threat Protection konfiguriert, wenn Sie [diesen Schutz in Intune aktivieren](~/protect/advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune). Der von Ihnen eingerichtete Benutzer und das Gerät, das Sie registrieren, werden zu einer neuen Sicherheitsgruppe hinzugefügt und mit den empfohlenen Einstellungen für Sicherheit und Produktivität konfiguriert. 

### <a name="what-you-will-need-to-continue"></a>Voraussetzungen zum Fortfahren

In diesem geführten Szenario müssen Sie Ihr Testgerät und Ihren Testbenutzer bereitstellen. Dazu führen Sie die folgenden Aufgaben aus:
- Erstellen eines Testbenutzerkontos in Azure Active Directory.
- Erstellen eines Testgeräts mit Windows 10, Version 1903 oder höher.
- (Optional) [Registrieren des Testgeräts mit Windows Autopilot](~/enrollment/enrollment-autopilot.md#add-devices)
- (Optional) Aktivieren von [Hinzufügen von Branding zur Azure Active Directory-Anmeldeliste Ihrer Organisation](https://go.microsoft.com/fwlink/?linkid=2102455).

## <a name="step-2---user"></a>Schritt 2: Benutzer

Wählen Sie einen Benutzer aus, der auf dem Gerät eingerichtet werden soll. Diese Person ist der primäre Benutzer des Geräts.

Wenn Sie weitere Benutzer oder Geräte zu dieser Konfiguration hinzufügen möchten, fügen Sie die Benutzer und Geräte einfach zu den vom Assistenten erstellten AAD-Sicherheitsgruppen hinzu. Im Gegensatz zu anderen geführten Szenarios müssen Sie den Assistenten nicht mehr als einmal ausführen, da die Konfiguration nicht anpassbar ist. Fügen Sie einfach weitere Benutzer und Geräte zu den erstellten AAD-Gruppen hinzu. Nach Abschluss des Assistenten können Sie die Gruppe anzeigen, die mit den bereitgestellten Richtlinien erstellt wurde. 

## <a name="step-3---device"></a>Schritt 3: Gerät

Stellen Sie sicher, dass auf Ihrem Gerät Windows 10, Version 1903 oder höher, ausgeführt wird.  Der primäre Benutzer muss das Gerät einrichten, wenn er es erhält. Dem Benutzer stehen zwei Einrichtungsoptionen zur Verfügung. 

### <a name="option-a--windows-autopilot"></a>Option A: Windows Autopilot
Windows Autopilot automatisiert die Konfiguration neuer Geräte, sodass Benutzer sie sofort und ohne IT-Unterstützung einrichten können. Wenn Ihr Gerät bereits bei Windows Autopilot registriert ist, wählen Sie es nach seiner Seriennummer aus. Weitere Informationen zur Verwendung von Windows Autopilot finden Sie unter [Registrieren des Geräts mit Windows Autopilot (optional)](~/fundamentals/guided-scenarios-cloud-managed-pc.md#register-device-with-windows-autopilot-optional).

### <a name="option-b--manual-device-enrollment"></a>Option B: Manuelle Geräteregistrierung
Die Benutzer werden ihre neuen Geräte manuell einrichten und in der Verwaltung mobiler Geräte registrieren. Nachdem Sie dieses Szenario abgeschlossen haben, setzen Sie das Gerät zurück, und geben Sie dem primären Benutzer die Registrierungsanweisungen für Windows-Geräte. Weitere Informationen finden Sie unter [Einbinden eines neuen Windows 10-Geräts in Azure AD auf der Windows-Willkommensseite](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

## <a name="step-4---review--create"></a>Schritt 4: Überprüfen und Erstellen

Im letzten Schritt können Sie eine Zusammenfassung der von Ihnen konfigurierten Einstellungen einsehen. Nachdem Sie Ihre Auswahl überprüft haben, klicken Sie auf **Bereitstellen**, um das geführte Szenario abzuschließen. Sobald das geführte Szenario abgeschlossen ist, wird eine Tabelle der Ressourcen angezeigt. Sie können diese Ressourcen später bearbeiten, aber sobald Sie die Ansicht der Zusammenfassung verlassen, wird die Tabelle nicht gespeichert.

> [!IMPORTANT]
> Sobald das geführte Szenario abgeschlossen ist, wird eine Zusammenfassung angezeigt. Sie können die in der Zusammenfassung aufgeführten Ressourcen später ändern, jedoch wird die Tabelle mit diesen Ressourcen nicht gespeichert.

### <a name="verification"></a>Überprüfung
1. Stellen Sie sicher, dass dem ausgewählten Benutzer ein MDM-Benutzerbereich zugewiesen ist.
    - Stellen Sie sicher, dass der [MDM-Benutzerbereich](~/enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment) auf:
        - **Alle** für die **Microsoft Intune-App** oder
        - auf **Einige** festgelegt ist. Fügen Sie außerdem die Benutzergruppe hinzu, die durch dieses geführte Szenario erstellt wurde.
2. Stellen Sie sicher, dass der ausgewählte Benutzer in der Lage ist, Geräte mit Azure Active Directory zu verknüpfen.
    - Stellen Sie sicher, dass die AAD-Verknüpfung auf:
        - **Alle** oder
        - auf **Einige** festgelegt ist. Fügen Sie auch die Benutzergruppe hinzu, die durch dieses geführte Szenario erstellt wurde.
3. Befolgen Sie die entsprechenden Schritte auf dem Gerät, um es wie in den folgenden Schritten mit Azure AD zu verknüpfen:
    - Mit Windows Autopilot: Weitere Informationen finden Sie unter [Windows Autopilot-Benutzergesteuerter Modus](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven).
    - Ohne Windows Autopilot: Weitere Informationen finden Sie unter [Einbinden eines neuen Windows 10-Geräts in Azure AD auf der Windows-Willkommensseite](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

### <a name="what-happens-when-i-click-deploy"></a>Was passiert, wenn Sie auf „Bereitstellen“ klicken?
Der Benutzer und das Gerät werden zu neuen Sicherheitsgruppen hinzugefügt. Diese werden auch mit von Intune empfohlenen Einstellungen für Sicherheit und Produktivität am Arbeitsplatz oder in der Schule/Universität konfiguriert. Nachdem der Benutzer das Gerät mit Azure AD verknüpft hat, werden dem Gerät weitere Apps und Einstellungen hinzugefügt. Erfahren Sie mehr zu diesen weiteren Konfigurationen unter [Schnellstart: Registrierung Ihres Windows 10-Geräts](~/enrollment/quickstart-enroll-windows-device.md).

## <a name="additional-information"></a>Zusätzliche Informationen

### <a name="register-device-with-windows-autopilot-optional"></a>Registrieren des Geräts mit Windows Autopilot (Optional)

Sie können optional ein mit Windows Autopilot registriertes Gerät verwenden. Für Windows Autopilot weist dieses geführte Szenario ein Autopilot-Bereitstellungsprofil und ein Profil für Registrierungsstatusseiten zu. Das Autopilot-Bereitstellungsprofil wird wie folgt konfiguriert:
- Benutzergesteuerter Modus – d. h. der Endbenutzer muss während des Windows Setups den Benutzernamen und ein Kennwort eingeben.
- Azure AD-Verknüpfung.
- Anpassen des Windows Setups:
  - Den Bildschirm mit den Lizenzbedingungen für Microsoft Software ausblenden.
  - Datenschutzeinstellungen ausblenden. 
  - Das lokale Profil des Benutzers ohne lokale Administratorrechte erstellen.
  - Die Optionen zur Kontoänderung auf der Anmeldeseite des Unternehmens ausblenden.

Die Seite zum Registrierungsstatus wird so konfiguriert, dass sie nur für Geräte mit Autopilot aktiviert wird und das Warten auf die Installation aller Apps nicht blockiert.

Das geführte Szenario weist den Benutzer auch dem ausgewählten Gerät mit Autopilot zu, um ein personalisiertes Setup zu ermöglichen.

#### <a name="post-requisites"></a>Nachfolgende Voraussetzungen
Sobald der Benutzer das Gerät mit Azure Active Directory verknüpft, werden die folgenden Konfigurationen auf das Gerät angewendet:
1. Office 365 ProPlus wird automatisch auf dem über eine Cloud verwalteten PC installiert. Es enthält die Anwendungen, mit denen Sie vertraut sind, einschließlich Access, Excel, OneNote, Outlook, PowerPoint, Publisher, Skype for Business und Word. Mit diesen Anwendungen können Sie sich mit Office 365-Diensten wie SharePoint Online, Exchange Online und Skype for Business Online verbinden. Office 365 ProPlus wird im Gegensatz zu Versionen von Office, die kein Abonnement erfordern, regelmäßig mit neuen Features aktualisiert. Eine Liste mit neuen Features finden Sie unter „Neuerungen in Office 365“.
2. Die Windows-Sicherheitsbaselines werden auf dem über eine Cloud verwalteten PC installiert. Wenn Sie Microsoft Defender Advanced Threat Protection eingerichtet haben, konfiguriert das geführte Szenario auch die Baselineeinstellungen für Defender. Defender Advanced Threat Protection bietet eine neue Schutzebene für Windows 10-Sicherheitsfeatures. Mit einer Kombination aus Clienttechnologie, die in Windows 10 integriert ist, und einem robusten Clouddienst werden Bedrohungen besser erkannt, die es über andere Abwehrsysteme hinaus geschafft haben. 

## <a name="next-steps"></a>Nächste Schritte

- Wenn Sie Microsoft Defender Advanced Threat Detection verwenden, erstellen Sie eine [Intune-Konformitätsrichtlinie](~/protect/advanced-threat-protection.md#create-and-assign-the-compliance-policy), um eine Defender-Bedrohungsanalyse zur Erfüllung der Konformität zu verlangen.
- Erstellen Sie eine [gerätebasierte Richtlinie für bedingten Zugriff](~/protect/advanced-threat-protection.md#create-a-conditional-access-policy), um den Zugriff zu blockieren, wenn das Gerät die Konformität von Intune nicht erfüllt.
