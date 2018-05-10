---
title: Early Edition
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d6a06326fbb60d910aef0411fc666b82a5f22078
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2018
---
# <a name="the-early-edition-for-microsoft-intune---april-2018"></a>Die Early Edition für Microsoft Intune (April 2018)

Die **Early Edition** enthält eine Liste der Funktionen, die in späteren Versionen von Microsoft Intune zur Verfügung stehen werden. Diese Informationen werden auf einer begrenzten Basis bereitgestellt, und Änderungen sind vorbehalten. Geben Sie diese Informationen nicht außerhalb Ihres Unternehmens weiter. Einige der hier aufgeführten Features werden möglicherweise bis zum Stichtag nicht fertig und werden erst in eine spätere Version aufgenommen. Andere Features werden in einer Pilotphase getestet (Test-Flighting), um sicherzustellen, dass sie für Kunden bereit sind. Wenden Sie sich mit Fragen oder Bedenken an den Ansprechpartner für Ihre Microsoft-Produktgruppe.

Diese Seite wird regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.

> [!Note]
>Die folgenden Änderungen sind in der Entwicklung für Intune. Weitere Informationen zu neuen Hybridfeatures finden Sie auf unserer [Seite mit neuen Hybridfeatures](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune im Azure-Portal

<!-- 1804 start -->




### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Ergänzungen zu den Einstellungen der Sicherheitsoptionen für lokale Geräte <!-- 1403702 -->
Sie können zusätzliche Einstellungen für Sicherheitsoptionen für lokale Geräte für Windows 10-Geräte konfigurieren. Zusätzliche Einstellungen sind zukünftig in den Bereichen Microsoft Netzwerk (Client), Microsoft-Netzwerk (Server), Netzwerkzugriff und -sicherheit und interaktive Anmeldung verfügbar. Diese Einstellungen finden Sie in der Endpoint Protection-Kategorie, wenn Sie eine Gerätekonfigurationsrichtlinie für Windows 10 erstellen.

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Erforderliche Installation von Richtlinien, Apps, Zertifikaten und Netzwerkprofilen <!-- 1553555 -->
Administratoren können Endbenutzern den Zugriff auf Windows 10 RS4 Desktop verwehren, bis Richtlinien, Apps, Zertifikate und Netzwerkprofile während der Bereitstellung von AutoPilot-Geräten von Intune installiert wurden.

### <a name="rules-for-removing-devices----1609459---"></a>Regeln für das Entfernen von Geräten <!-- 1609459 -->
Neue Regeln, mit denen Sie Geräte automatisch entfernen können, die über einen festgelegten Zeitraum nicht mehr eingecheckt waren, sind zukünftig verfügbar. Um die neue Regel anzuzeigen, wechseln Sie in den Bereich **Intune**, und wählen Sie **Geräte** und anschließend **Device removal rules** (Regeln zur Geräteentfernung) aus.

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Verhindern von Verbraucher-Apps und -Umgebungen auf dem Windows 10 Enterprise RS4 AutoPilot-Gerät<!-- 1621980 -->
Sie können die Installation von Verbraucher-Apps und -Umgebungen auf Ihren Windows 10 Enterprise RS4 AutoPilot-Geräten verhindern. Um dieses Feature anzuzeigen, wechseln Sie in **Intune** zu **Geräteregistrierung** > **Windows-Registrierung** > **Windows AutoPilot-Profile** > **Neu erstellen** > **Registrierungseinstellungen**. 


<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>Unterstützen von mehreren Exchange-Connectors <!-- 2070451 -->

Sie werden nicht länger auf einen Microsoft Intune Exchange-Connector pro Mandant beschränkt. Intune unterstützt mehrere Exchange-Connectors, sodass Sie Intune mithilfe von mehreren lokalen Exchange-Organisationen für bedingten Zugriff einrichten können.

Mit einem lokalen Exchange-Connector von Intune können Sie den Zugriff von Geräten auf Ihre lokalen Exchange-Postfächer verwalten. Dies ist abhängig davon, ob ein Gerät bei Intune registriert ist, und ob es den Gerätekompatibilitätsrichtlinien von Intune entspricht. Um einen Connector einzurichten, müssen Sie den lokalen Exchange-Connector von Intune aus dem Azure-Portal herunterladen und ihn auf einem Server in Ihrer Exchange-Organisation installieren. Klicken Sie im Microsoft Intune-Dashboard auf **Lokaler Zugriff** und dann unter **Setup** auf **Exchange ActiveSync-Connector**. Laden Sie den lokalen Exchange-Connector herunter, und installieren Sie ihn auf einem Server in Ihrer Exchange-Organisation. Da Sie nun nicht länger auf einen Exchange-Connector pro Mandant beschränkt werden, wenn Sie weitere Exchange-Organisationen haben, können Sie anhand des gleichen Durchgangs einen Connector für jede weitere Exchange-Organisation herunterladen und installieren.

### <a name="support-coming-for-new-cisco-anyconnect-client-for-ios----1333708---"></a>Unterstützung für den neuen Cisco AnyConnect-Client für iOS <!-- 1333708 -->

Neue VPN-Profile, die für Cisco AnyConnect für iOS erstellt wurden, funktionieren mit Cisco AnyConnect 4.0.7x oder höher. Bereits existierende iOS Cisco AnyConnect VPN-Profile werden als **Cisco Legacy AnyConnect** bezeichnet und werden auch weiterhin mit Cisco AnyConnect 4.0.5x funktionieren.

> [!NOTE]
> Diese Änderung gilt nur für iOS. Es wird weiterhin nur eine Option von Cisco AnyConnect für Android, Android for Work und macOS geben.

#### <a name="more-information"></a>Weitere Informationen

Zur Unterstützung der neuen App müssen Sie ein neues iOS Cisco AnyConnect VPN-Profil erstellen, da die neue Cisco AnyConnect-App und die Cisco Legacy AnyConnect-App unterschiedliche Apps sind. Wenn Sie den AnyConnect-Client in Ihrer Umgebung verwalten, müssen Sie die neue Cisco AnyConnect-App ebenfalls bereitstellen. Um ein Upgrade auszuführen, müssen Sie Ihr Cisco Legacy AnyConnect VPN-Profil löschen und die Cisco Legacy AnyConnect-App entfernen.

Die NAC-Integration (Network Access Control, Netzwerk-Zugriffssteuerung) funktioniert für das erste Release des neuen AnyConnect-Clients nicht. Zusammen mit Cisco wird versucht, eine NAC-Integration in einem zukünftigen Intune-Release bereitzustellen.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Die Möglichkeit, erforderliche branchenspezifische Apps (LOB) für alle Benutzer von Windows 10 Desktop-Geräten bereitzustellen <!-- 1627835 RS4 -->.
Kunden können erforderliche branchenspezifische Apps unter Windows 10 bereitstellen, um in Gerätekontexte zu installieren. Dadurch können diese Apps für alle Benutzer auf dem Gerät verfügbar sein. Dies gilt nur für Windows 10 Desktop-Geräte.

### <a name="company-portal-enrollment-improved----1874230--"></a>Verbesserte Unternehmensportal-Registrierung <!-- 1874230-->
Benutzer, die mithilfe des Unternehmensportals unter Windows 10 Version 1703 oder höher ein Gerät registrieren, können den ersten Schritt der Registrierung ausführen, ohne die App verlassen zu müssen.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Aktualisieren der „Hilfe und Feedback“-Oberfläche in der Unternehmensportal-App für Android <!--1631531 -->

Die „Hilfe und Feedback“-Benutzeroberfläche in der Unternehmensportal-App für Android wird aktualisiert, um Android-Apps nach bewährten Methoden auszurichten. Die Unternehmensportal-App für Android wird in den nächsten Monaten aktualisiert. Das **Hilfe und Feedback**-Menüelement wird in die Menüelemente **Hilfe** und **Feedback senden** unterteilt. Auf der **Hilfe**-Seite wird es einen **Häufig gestellte Fragen**-Abschnitt und eine **E-Mail-Support**-Schaltfläche zum Hochladen von Protokollen an Microsoft und Senden von E-Mails an die Supportabteilung Ihres Unternehmens geben, in denen die Probleme beschrieben werden. Die Option **Feedback senden** führt den Benutzer durch den Standardprozess zur Feedbackübermittlung von Microsoft, in dem der Benutzer angeben kann, ob ihm etwas gefällt, nicht gefällt und Vorschläge machen kann.


<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>App-Schutzrichtlinien <!-- 679615 -->
Mit den Intune-App-Schutzrichtlinien können Sie globale Standardrichtlinien erstellen und damit den Schutz für alle Benutzer im gesamten Mandanten schnell aktivieren.

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory-Websites können die App „Intune Managed Browser“ erfordern und unterstützen die einmalige Anmeldung für diese (öffentliche Vorschau) <!-- 710595 -->   
Mithilfe von Azure Active Directory (Azure AD) können Sie den Zugriff auf Websites durch mobile Geräte auf die App „Intune Managed Browser“ beschränken. Im verwalteten Browser bleiben die Websitedaten sicher und getrennt von den persönlichen Daten des Benutzers. Zusätzlich unterstützt der Managed Browser die Funktionen für einmaliges Anmelden für Websites, die von Azure AD geschützt werden. Das Anmelden beim Managed Browser oder das Verwenden desselben auf einem Gerät mit einer anderen App, die von Intune verwaltet wird, ermöglicht es dem Managed Browser, auf Unternehmenswebsites zuzugreifen, die von Azure AD geschützt werden, ohne dass der Benutzer seine Anmeldeinformationen eingeben muss. Diese Funktion gilt für Websites wie Outlook Web Access (OWA) und SharePoint Online sowie für andere Unternehmenswebsites wie Intranetressourcen, auf die über den Azure-App-Proxy zugegriffen wird.




## <a name="notices"></a>Benachrichtigungen

Derzeit gibt es keine aktiven Benachrichtigungen.


### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).


