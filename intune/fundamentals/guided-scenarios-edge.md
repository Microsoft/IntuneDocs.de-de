---
title: 'Geführtes Szenario: Bereitstellen von Microsoft Edge für Mobilgeräte'
titleSuffix: Microsoft Intune
description: Erfahren Sie mehr über das geführte Szenario, um Microsoft Edge für Mobilgeräte über das Microsoft 365-Geräteverwaltungsportal bereitzustellen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e86f3a469169e7a805cb3f56e570ba4d3a90e925
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585695"
---
# <a name="guided-scenario---deploy-microsoft-edge-for-mobile"></a>Geführtes Szenario: Bereitstellen von Microsoft Edge für Mobilgeräte 

Indem Sie diesem [geführten Szenario](~/fundamentals/guided-scenarios-overview.md) folgen, können Sie die Microsoft Edge-App Ihren Benutzern auf iOS- oder Android-Geräten in Ihrer Organisation zuweisen. Die Zuweisung dieser App ermöglicht es Ihren Benutzern, Inhalte über ihre Unternehmensgeräte nahtlos zu durchsuchen. 

Dank der integrierten Features von Microsoft Edge ist es für die Benutzer ein Leichtes, sich im Dschungel des Internets zurechtzufinden und ihre Arbeitsinhalte zu konsolidieren, zu strukturieren und zu verwalten. Für Benutzer von iOS- und Android-Geräten, die sich mit ihren Azure AD-Unternehmenskonten bei der Microsoft Edge-App anmelden, wird der Browser mit allen **Arbeitsbereichsfavoriten** und Websitefiltern vorinstalliert, die Sie definieren.

> [!NOTE]
> Wenn Sie die Registrierung von iOS- oder Android-Geräten für Benutzer blockiert haben, wird die Registrierung durch dieses Szenario nicht aktiviert, und die Benutzer müssen Microsoft Edge selbst installieren.
Die folgenden durch Intune-Richtlinien aktivierten Microsoft Edge-Unternehmensfeatures sind verfügbar: 

- **Doppelte Identitäten:** Benutzer können sowohl Geschäftskonten als auch persönliche Konten zum Browsen hinzufügen. Die beiden Identitäten sind vollständig voneinander getrennt, ähnlich wie bei Office 365 und Outlook. Intune-Administratoren können die gewünschten Richtlinien für geschütztes Browsen im Geschäftskonto festlegen. 
- **Integration von Intune-App-Schutzrichtlinien:** Administratoren können jetzt App-Schutzrichtlinien für Microsoft Edge erstellen. U. a. können sie in diesem Rahmen festlegen, wie und ob Benutzer Inhalte ausschneiden, kopieren und einfügen können, ob Bildschirmaufnahmen zulässig sind, und sie können sicherstellen, dass von Benutzern ausgewählte Links nur in anderen verwalteten Apps geöffnet werden.
- **Azure-Anwendungspoxyintegration:** Administratoren können den Zugriff auf SaaS-Apps und Web-App festlegen, um sicherzustellen, dass browserbasierte Apps nur im sicheren Microsoft Edge-Browser ausgeführt werden, egal ob Endbenutzer eine Verbindung über ein Unternehmensnetzwerk oder über das Internet herstellen. 
- **Verknüpfungen zu Favoriten und der Startseite:** Für einen einfacheren Zugriff können Administratoren URLs festlegen, die unter Favoriten angezeigt werden, wenn sich Benutzer im Unternehmenskontext befinden. Administratoren können auch eine Verknüpfung zur Startseite hinzufügen, die als primäre Verknüpfung angezeigt wird, wenn der Unternehmensbenutzer eine neue Seite oder eine neue Registerkarte in Microsoft Edge öffnet.

## <a name="prerequisites"></a>Voraussetzungen

- [Legen Sie die MDM-Autorität auf Intune fest](mdm-authority-set.md#set-mdm-authority-to-intune) – Die Einstellung für die Autorität für die Verwaltung mobiler Geräte (Mobile Device Management, MDM) bestimmt, wie Sie Ihre Geräte verwalten. Als IT-Administrator müssen Sie eine MDM-Autorität festlegen, damit Benutzer Geräte zur Verwaltung registrieren können.
- Erforderliche Intune-Administratorberechtigungen:
    - Verwaltete Apps: Lesen, Erstellen, Löschen und Zuweisen von Berechtigungen
    - Berechtigungen für mobile Apps: Lesen, Erstellen, Zuweisen
    - Richtliniensätze: Lesen, Erstellen und Zuweisen von Berechtigungen
    - Organisationsberechtigungen: Lesen, Aktualisieren

## <a name="step-1---introduction"></a>Schritt 1: Einführung

Indem Sie dem geführten Szenario **Bereitstellen von Microsoft Edge für Mobilgeräte** folgen, richten Sie eine einfache Bereitstellung von Microsoft Edge für eine ausgewählte Gruppe von iOS-und Android-Benutzern ein. Diese Bereitstellung implementiert **doppelte Identitäten** und **Verknüpfungen zu Favoriten und der Startseite**. Außerdem wird bei Geräten, die von den ausgewählten Benutzern registriert werden, automatisch die Microsoft Edge-App von Intune installiert. Diese automatische Installation erfolgt bei allen benutzergesteuerten Registrierungstypen, dazu gehören: 
- iOS-Registrierung über die Unternehmensportal-App 
- iOS-Benutzeraffinitätsregistrierung über Apple Business Manager 
- Android Legacy-Registrierung über die Unternehmensportal-App 

Dieses geführte Szenario ermöglicht automatisch, dass **MyApps** in den Microsoft Edge-Favoriten angezeigt wird, und konfiguriert den Browser mit dem gleichen Branding, das Sie für die Intune-Unternehmensportal-App festgelegt haben. 

### <a name="what-you-will-need-to-continue"></a>Voraussetzungen zum Fortfahren
Wir fragen Sie nach den für die Benutzer benötigten Arbeitsbereichsfavoriten und den Filtern, die für das Browsen im Web erforderlich sind. Stellen Sie sicher, dass Sie die folgenden Aufgaben ausführen, bevor Sie fortfahren:

- Fügen Sie Benutzer zu Azure AD-Gruppen hinzu. Weitere Informationen finden Sie unter [Erstellen einer Basisgruppe und Hinzufügen von Mitgliedern mit Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=2102458).
- Registrieren Sie iOS- oder Android-Geräte in Intune. Weitere Informationen finden Sie unter [Geräteregistrierung](https://go.microsoft.com/fwlink/?linkid=2102547).
- Stellen Sie eine Liste der Arbeitsbereichsfavoriten zusammen, die in Microsoft Edge hinzugefügt werden sollen.
- Stellen Sie eine Liste der Websitefilter zusammen, die in Microsoft Edge erzwungen werden sollen.

## <a name="step-2---basics"></a>Schritt 2: Grundlagen

In diesem Schritt müssen Sie einen Namen und eine Beschreibung für Ihre neuen Microsoft Edge-Richtlinien eingeben. Wenn Sie die Zuweisungen und Konfigurationen später ändern müssen, kann auf diese Richtlinien verwiesen werden. Das geführte Szenario fügt sowohl eine Microsoft Edge-iOS-App für Ihre iOS-Geräte als auch eine Microsoft Edge-Android-App für Ihre Android-Geräte hinzu und weist diese zu. Außerdem werden mit diesem Schritt Konfigurationsrichtlinien für diese Apps erstellt.

## <a name="step-3---configuration"></a>Schritt 3: Konfiguration

In diesem Schritt konfiguriert das geführte Szenario Microsoft Edge so, dass alle anderen Apps angezeigt werden, die Benutzern über Intune zugewiesen sind, und das gleiche Branding wie in der Microsoft Intune Unternehmensportal-App verwendet wird. Sie können Microsoft Edge weiter mit einer **URL-Verknüpfung zur Startseite**, einer Liste von **Verwalteten Lesezeichen** und einer Liste von **Blockierten URLs** konfigurieren. Die **URL-Verknüpfung zur Startseite** wird Benutzern als erstes Symbol unter der Suchleiste angezeigt, wenn sie auf ihrem Gerät eine neue Registerkarte in Microsoft Edge öffnen. Die **Verwalteten Lesezeichen** sind eine Liste der bevorzugten URLs, die Ihren Benutzern bei der Verwendung von Microsoft Edge in ihrem Arbeitskontext zur Verfügung stehen sollen. Die **Blockierten URLs** geben die Websites an, die für Ihre Benutzer in ihrem Arbeitskontexts gesperrt sind. Alle anderen Websites sind zulässig. 

## <a name="step-4---assignments"></a>Schritt 4: Zuweisungen

In diesem Schritt können Sie die Benutzergruppen auswählen, für die Microsoft Edge für Mobilgeräte konfiguriert werden soll. Microsoft Edge wird auch auf allen iOS-und Android-Geräten installiert, die von diesen Benutzern registriert wurden.

## <a name="step-5---review--create"></a>Schritt 5: Überprüfen und Erstellen

Im letzten Schritt können Sie eine Zusammenfassung der von Ihnen konfigurierten Einstellungen einsehen. Nachdem Sie Ihre Auswahl überprüft haben, klicken Sie auf **Erstellen**, um das geführte Szenario abzuschließen. 

> [!NOTE]
> Der Empfangsvorgang der Konfiguration in Edge kann bis zu 12 Stunden dauern. Weitere Informationen finden Sie unter [App-Konfigurationsrichtlinien für Microsoft Intune](~/apps/app-configuration-policies-overview.md).

> [!IMPORTANT]
> Sobald das geführte Szenario abgeschlossen ist, wird eine Zusammenfassung angezeigt. Sie können die in der Zusammenfassung aufgeführten Ressourcen später ändern, jedoch wird die Tabelle mit diesen Ressourcen nicht gespeichert.

## <a name="next-steps"></a>Nächste Schritte

- Verbessern Sie die Sicherheit von Microsoft Edge, indem Sie die Integration der Intune-App-Schutzrichtlinie einrichten. Weitere Informationen finden Sie unter [Anwendungsschutzrichtlinien für Microsoft Edge](~/apps/manage-microsoft-edge.md#application-protection-policies-for-microsoft-edge).
- Wenn Sie Intranetsites einschließen möchten, informieren Sie sich darüber, wie Sie den Zugriff mit der Integration des Azure-Anwendungsproxys schützen können. Weitere Informationen finden Sie unter [Konfigurieren von Anwendungsproxyeinstellungen für Microsoft Edge](~/apps/manage-microsoft-edge.md#configure-application-proxy-settings-for-microsoft-edge).

