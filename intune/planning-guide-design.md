---
title: Erstellen eines Entwurfs
titlesuffix: Microsoft Intune
description: Dieser Artikel unterstützt Sie beim Erstellen eines Entwurfs für einen Microsoft Intune-Cloudentwurf und seine Implementierung.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: ''
ms.openlocfilehash: fd6c80c022f13b892d396768439e2c503d5425d9
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
ms.locfileid: "29962529"
---
# <a name="create-a-design"></a>Erstellen eines Entwurfs

Ihr Intune-Entwurf basiert auf den Informationen und Entscheidungen, die Sie beim Bearbeiten anderer [Abschnitte dieses Handbuchs](planning-guide.md) sammeln bzw. treffen. Darin werden folgende Themen vereint:

-   Die aktuelle Umgebung

-   Intune-Bereitstellungsoptionen

-   Identitätsanforderungen für externe Abhängigkeiten

-   Aspekte zur Geräteplattform

-   Anforderungen an die Zustellung  

Die Anforderungen an die lokale Infrastruktur sind überschaubar. Ein Entwurfsplan ist dennoch hilfreich, um sicherzustellen, dass Sie eine Verwaltungslösung für Mobilgeräte verwenden, die Ihren Zielen und Anforderungen gerecht wird.

Betrachten wir jeden dieser Bereiche im Detail. 

## <a name="record-your-current-environment"></a>Erfassen der aktuellen Umgebung
Es ist außerdem üblich, Designänderungen während der Implementierung und der Testphase durchzuführen. Anhand Ihres Entwurfsplans können Sie diese Änderungen und die Motivation dahinter während der Durchführung dokumentieren.

Ihre aktuelle Umgebung kann Entwurfsentscheidungen beeinflussen. Sie sollte dokumentiert und bei anderen Intune-Entwurfsentscheidungen als Referenz verwendet werden. Im Folgenden finden Sie einige Beispiele für das Erfassen der aktuellen Umgebung:

-   **Identität in der Cloud**

    -   Verwenden Sie DirSync oder Azure Active Directory (Azure AD) Connect?

    -   Ist Ihre Umgebung im Verbund zusammengefasst?

    -   Ist Multi-Factor Authentication (MFA) aktiviert?

-   **E-Mail-Umgebung**

    -   Verwenden Sie Exchange? Ist es eine lokale Installation oder eine Cloudversion?

    -   Befinden Sie sich mitten in einem Projekt zur Migration von Exchange zur Cloud?

-   **Aktuelle Lösung für die mobile Geräteverwaltung (MDM)**

    -   Verwenden Sie zurzeit andere MDM-Lösungen?

    -   Welche MDM-Lösungen verwenden Sie für Unternehmens- und BYOD-Anwendungsszenarios?

    -   Welche Funktionen verwenden Sie (z.B. App-Geräteeinstellungen und WLAN-Konfigurationen)?

    -   Welche Geräteplattformen werden unterstützt?

    -   Welche Gruppen und wie viele Benutzer verwenden die MDM-Lösung?

-   **Zertifikatlösung**

    -   Haben Sie eine Zertifikatlösung implementiert?

    -   Welche Art von Zertifikaten verwenden Sie?

-   **Systemverwaltung**

    -   Wie verwalten Sie Ihre PC- und Serverumgebung?

    -   Verwenden Sie System Center Configuration Manager? Verwenden Sie eine Drittanbieterplattform zur Systemverwaltung?

-   **VPN-Lösung**

    -   Was ist Ihre VPN-Lösung?

    -   Verwenden Sie sie sowohl für Unternehmens- als auch für BYOD-Anwendungsszenarios?

Stellen Sie beim Erfassen der aktuellen MDM-Umgebung sicher, dass Sie alle Projekte oder andere Pläne berücksichtigen, Auswirkungen auf Ihre Umgebung haben könnten. Im Folgenden sehen Sie ein Beispiel für eine Möglichkeit zum Erfassen der aktuellen Umgebung beim Erstellen Ihres Intune-Entwurfs:

| **Lösungsbereich** | **Aktuelle Umgebung** | **Kommentare** |
|---|---|---|
| **Identität** | Azure AD, Azure AD Connect, kein Verbund, keine MFA | Vorgesehenes Projekt zum Aktivieren der MFA bis zum Ende des Jahres |                 
| **E-Mail-Umgebung** | Exchange lokal, Exchange Online | Derzeit erfolgt die Migration von Exchange lokal zu Exchange Online. 75% der Postfächer migriert. Die letzten 25% werden vor Beginn des Intune-Pilotprojekts migriert. |                
| **SharePoint** | SharePoint lokal | Keine Pläne zur Onlineverwendung von SharePoint |  
| **Aktuelle MDM** | Exchange ActiveSync |  |
| **Zertifikatlösung** | Microsoft Server 2012 R2, Active Directory-Zertifikatdienste | PKI wird nur für Websiteserver verwendet |
| **Systemverwaltung** | System Center Configuration Manager CB 1606 | Die Intune-Hybridlösung soll näher untersucht werden |
| **VPN-Lösung** | Cisco AnyConnect |  |


Sie können eine [Vorlage der oben stehenden Tabelle herunterladen](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), um Ihren Intune-Entwurfsplan zu entwickeln.

## <a name="choose-an-intune-deployment-option"></a>Wählen einer Intune-Bereitstellungsoption

Intune bietet zwei Bereitstellungsoptionen: eigenständig und hybrid. Eigenständig bezieht sich darauf, dass der Intune-Dienst in der Cloud ausgeführt wird. Hybrid bezieht sich auf die Integration von Intune in System Center Configuration Manager. Dieses Handbuch ist in erster Linie auf die Verwendung der eigenständigen Option ausgerichtet. [Entscheiden Sie, welche Option Ihren geschäftlichen Anforderungen am meisten entspricht.](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)

## <a name="intune-tenant-location"></a>Standort des Intune-Mandanten

Wenn Ihre Organisation weltweit tätig ist, berücksichtigen Sie bei der Planung den Standort Ihres Mandanten, wenn den Dienst abonnieren. Das Land/die Region wird definiert, wenn Sie sich erstmals für ein Intune-Abonnement registrieren. Anschließend erfolgt die Zuordnung zu Regionen rund um die Welt, die unten aufgeführt sind:

-   Nordamerika

-   Europa, Naher Osten und Afrika

-   Asien und pazifischer Raum

>[!IMPORTANT]
> Land/die Region und Standort des Mandanten können später nicht mehr geändert werden.

## <a name="external-dependencies"></a>Externe Abhängigkeiten

Externe Abhängigkeiten sind Dienste und Produkte, die separat von Intune ausgeführt werden, aber entweder für Intune erforderlich sind oder in Intune integriert werden können. Die Anforderungen an externe Abhängigkeiten und deren Konfiguration müssen unbedingt abgeklärt werden. Einige Beispiele für gängige externe Abhängigkeiten sind unten aufgeführt:

-   Identität

-   Benutzer- und Gerätegruppen

-   Public Key-Infrastruktur (PKI)

Betrachten wir diese gängigen externen Abhängigkeiten unten im Detail.

### <a name="identity"></a>Identität

Mit der Identität identifizieren wir die Benutzer, die Ihrer Organisation angehören und ein Gerät registrieren. Intune erfordert Azure Active Directory (Azure AD) als Benutzeridentitätsanbieter. Wenn Sie diesen Dienst bereits verwenden, können Sie Ihre bereits in der Cloud vorhandene Identität nutzen. Azure AD Connect ist außerdem das empfohlene Tool zum Synchronisieren Ihrer lokalen Benutzeridentitäten mit Microsoft Cloud Services. Wenn in Ihrer Organisation bereits Office 365 verwendet wird, muss Intune unbedingt dieselbe Azure Active Directory-Umgebung verwenden.

Erfahren Sie mehr über die folgenden Anforderungen der Intune-Identität:

- [Identitätsanforderungen](https://docs.microsoft.com/azure/active-directory/understand-azure-identity-solutions)

- [Anforderungen für die Verzeichnissynchronisierung](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

- [Anforderungen für mehrstufige Authentifizierung](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)

### <a name="user-and-device-groups"></a>Benutzer- und Gerätegruppen

Benutzer- und Gerätegruppen bestimmen das Ziel einer Bereitstellung, einschließlich der Richtlinien, Anwendungen und Profile. Sie müssen ermitteln, welche Benutzer- und Gerätegruppen benötigt werden.

Es wird empfohlen, dass Sie alle Gruppen im lokalen Active Directory erstellen und anschließend mit Azure AD synchronisieren. Weitere Informationen zur Planung und Erstellung von Benutzer- und Gerätegruppen:

-   [Planen von Benutzer- und Gerätegruppen](users-add.md)

-   [Erstellen von Benutzer- und Gerätegruppen](groups-add.md)

### <a name="public-key-infrastructure-pki"></a>Public Key-Infrastruktur (PKI)
Die Public Key-Infrastruktur stellt Zertifikate für Geräte oder Benutzer bereit, damit diese sich sicher bei einem Dienst authentifizieren können. Intune unterstützt eine Microsoft PKI-Infrastruktur. Geräte- und Benutzerzertifikate können für ein mobiles Gerät ausgestellt werden, um die Anforderungen an die zertifikatbasierte Authentifizierung zu erfüllen. Vor der Verwendung von Zertifikaten müssen Sie ermitteln, ob sie erforderlich sind, ob die Netzwerkinfrastruktur die zertifikatbasierte Authentifizierung unterstützt und ob Zertifikate in der vorhandenen Umgebung derzeit verwendet werden.

Wenn Sie planen, Zertifikate mit VPN-, WLAN- oder E-Mail-Profilen mit Intune zu verwenden, müssen Sie sicherstellen, dass eine unterstützte [PKI-Infrastruktur vorhanden ist](certificates-configure.md), in der Zertifikatprofile erstellt und bereitgestellt werden können.

Wenn SCEP-Zertifikate ausgegeben werden sollen, müssen Sie darüber hinaus festlegen, auf welchem Server der Registrierungsdienst für Netzwerkgeräte gehostet wird und wie die Kommunikation erfolgen soll.

Weitere Informationen:

-   [Konfigurieren von Zertifikaten in Microsoft Intune](certificates-configure.md)

-   [Konfigurieren der Zertifikatinfrastruktur für SCEP](certificates-scep-configure.md)

-   [Konfigurieren und Verwalten von PKCS-Zertifikaten mit Intune](certficates-pfx-configure.md)




## <a name="device-platform-considerations"></a>Aspekte zur Geräteplattform

Werfen Sie einen genaueren Blick auf die folgenden Geräteaspekte, um zu verstehen, wie Sie sie vorschriftsmäßig verwalten.

-   Unterstützte Geräteplattformen

-   Geräte

-   Gerätebesitz

-   Massenregistrierung

Betrachten wir diese Bereiche im Detail.

### <a name="determine-supported-device-platforms"></a>Ermitteln unterstützter Geräteplattformen

Sie müssen beim Erstellen des Entwurfs wissen, welche Geräte sich in der Umgebung befinden werden, und überprüfen, ob diese von Intune unterstützt werden oder nicht. Intune unterstützt die Plattformen iOS, Android und Windows.

[Vollständige Liste der von Intune unterstützten Geräte](supported-devices-browsers.md)

### <a name="devices"></a>Geräte

Intune verwaltet mobile Geräte, um Unternehmensdaten zu schützen und Endbenutzern die Arbeit an mehreren Standorten zu ermöglichen. Intune unterstützt alle Geräteplattformen. Deshalb wird empfohlen, die Geräte und die Betriebssystemplattformen und -versionen zu dokumentieren, die im Entwurf Ihrer Organisation unterstützt werden. Beispiel:

| **Geräteplattform** | **Betriebssystemversionen** |
|:---:|:---:|
| iOS – iPhone | 9.0+ |                
| iOS – iPad | 8.0+ |               
| Android – Samsung Knox Standard | 4.0+ |
| Windows 10-Tablet | 10+ |


Sie können eine [Vorlage der oben stehenden Tabelle herunterladen](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), um Ihre Geräteliste zu entwickeln.
### <a name="device-ownership"></a>Gerätebesitz

Intune unterstützt sowohl unternehmenseigene als auch persönliche Geräte. Ein Gerät wird als unternehmenseigen betrachtet, wenn Sie es über einen Geräteregistrierungs-Manager oder ein Programm zur Geräteregistrierung registrieren. Beispielsweise kann ein Gerät über das Programm zur Geräteregistrierung von Apple (Device Enrollment Program, DEP) registriert, als unternehmenseigen markiert und in eine Gerätegruppe aufgenommen werden, die gezielte Unternehmensrichtlinien und Apps empfängt.

Weitere Informationen zu Unternehmens- und BYOD-Anwendungsfällen finden Sie unter [Abschnitt 3: Bestimmen von Anwendungsfallanforderungen](planning-guide-requirements.md).

### <a name="bulk-enrollment"></a>Massenregistrierung

 Je nach Plattform haben Sie verschiedene Möglichkeiten, Geräte in einer Massenoperation zu registrieren. Wenn die Massenregistrierung benötigt wird, legen Sie zunächst die [Methode zur Massenregistrierung](device-enrollment.md) fest, und integrieren Sie sie in Ihren Entwurf.

## <a name="feature-requirements"></a>Featureanforderungen

In den folgenden Abschnitten betrachten wir die folgenden Features und Funktionen, die auf die Anforderungen Ihres Anwendungsfalls ausgerichtet werden:

-   Richtlinien für Geschäftsbedingungen

-   Konfigurationsrichtlinien

-   Ressourcenprofile

-   Apps

-   Kompatibilitätsrichtlinie

-   Bedingter Zugriff

Betrachten wir jeden dieser Bereiche im Detail.

### <a name="terms-and-conditions-policies"></a>Richtlinien für Geschäftsbedingungen

Anhand von [Geschäftsbedingungen](terms-and-conditions-create.md) können Richtlinien oder Bedingungen erläutert werden, denen ein Benutzer zustimmen muss, bevor er sein Gerät registrieren kann. Intune unterstützt die Möglichkeit, Benutzergruppen mehrere Richtlinien für Geschäftsbedingungen hinzuzufügen und bereitzustellen.

Sie müssen festlegen, ob Richtlinien für Geschäftsbedingungen erforderlich sind. Falls ja, muss festgelegt werden, wer für die Bereitstellung dieser Informationen in der Organisation verantwortlich ist. Im Folgenden finden Sie ein Beispiel für das Dokumentieren der Richtlinie für Geschäftsbedingungen.

| **Name der Geschäftsbedingungen** | **Anwendungsfall** | **Zielgruppe** |
|:---:|:---:|:---:|
| Bedingungen für Unternehmensgeräte | Unternehmen | Unternehmensbenutzer |                 
| BYOD-Bedingungen | BYOD | BYOD-Benutzer |                


Sie können eine [Vorlage aus der obigen Tabelle herunterladen](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), um Benutzergruppen Ihre Geschäftsbedingungen zuzuordnen.

### <a name="configuration-policies"></a>Konfigurationsrichtlinien

Über Konfigurationsrichtlinien werden Sicherheitseinstellungen und -features auf einem Geräten verwaltet. Beim Entwerfen Ihrer Konfigurationsrichtlinien finden Sie Informationen im Abschnitt mit den Anforderungen des Anwendungsfalls. Anhand dieser Informationen können Sie die für Intune-Geräte erforderlichen Konfigurationen ermitteln. Dokumentieren Sie die Einstellungen und wie diese konfiguriert werden sollen. Dokumentieren Sie auch, auf welche Benutzer- oder Gerätegruppen sie angewendet werden sollen.

Erstellen Sie mindestens eine Konfigurationsrichtlinie pro Plattform. Sie können bei Bedarf mehrere Konfigurationsrichtlinien pro Plattform erstellen. Im Folgenden finden Sie ein Beispiel für das Entwerfen von vier verschiedenen Konfigurationsrichtlinien für verschiedene Plattformen und Anwendungsszenarios.

| **Name der Richtlinie** | **Geräteplattform** | **Einstellungen** | **Zielgruppe** |   
|:---:|:---:|:---:|:---:|
| Unternehmen – iOS | iOS | PIN ist erforderlich, Länge: 6, Cloudsicherung einschränken | Unternehmensgeräte |                                                           
| Unternehmen – Android | Android | PIN ist erforderlich, Länge: 6, Cloudsicherung einschränken | Unternehmensgeräte |                                                           
| BYOD – iOS  | iOS | PIN ist erforderlich, Länge: 4 | BYOD-Geräte |
| BYOD – Android  | Android | PIN ist erforderlich, Länge: 4 | BYOD-Geräte |


Sie können eine [Vorlage der oben stehenden Tabelle herunterladen](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), um die Anforderungen an Ihre Konfigurationsrichtlinien zu ermitteln.

### <a name="profiles"></a>Profile

Anhand von Profilen kann der Benutzer eine Verbindung mit Unternehmensdaten herstellen. Intune unterstützt zahlreiche Typen von Profilen. Anhand der Anwendungsfälle und Anforderungen können Sie bestimmen, wann die Profile konfiguriert werden. Alle Geräteprofile werden nach Plattformtyp kategorisiert und sollten in der Entwurfsdokumentation berücksichtigt werden.

-   Zertifikatprofile

-   Wi-Fi-Profil

-   VPN-Profil

-   E-Mail-Profil

Betrachten wir die einzelnen Profiltypen im Detail.

#### <a name="certificate-profiles"></a>Zertifikatprofile

Mit Zertifikatprofilen kann Intune ein Zertifikat für einen Benutzer oder ein Gerät ausstellen. Intune unterstützt folgende Optionen:

-   Simple Certificate Enrollment-Protokoll (SCEP)

-   Vertrauenswürdiges Stammzertifikat

-   PFX-Zertifikat

Es wird empfohlen zu dokumentieren, welche Benutzergruppe ein Zertifikat benötigt, wie viele Zertifikatprofile benötigt werden und welchen Benutzergruppen sie bereitgestellt werden.

>[!NOTE]
> Denken Sie daran, dass das vertrauenswürdige Stammzertifikat für das SCEP-Zertifikat erforderlich ist. Stellen Sie daher sicher, dass alle Benutzer, die ein SCEP-Zertifikat erhalten sollen, außerdem ein vertrauenswürdiges Stammzertifikat erhalten. Wenn SCEP-Zertifikate erforderlich sind, entwerfen und dokumentieren Sie, welche SCEP-Zertifikatvorlagen benötigt werden.

Im folgenden Beispiel wird gezeigt, wie Zertifikate während des Entwurfs dokumentiert werden können:

| **Typ** | **Profilname** | **Geräteplattform** | **Anwendungsfälle** |   
|:---:|:---:|:---:|:---:|
| Stamm-CA | Stamm-CA für Unternehmensgeräte | Android, iOS, Windows Mobile | Unternehmen, BYOD  |                                                           
| SCEP | Benutzerzertifikat | Android, iOS, Windows Mobile | Unternehmen, BYOD |                                                           


Sie können eine [Vorlage der oben stehenden Tabelle herunterladen](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), um die Anforderungen an Ihr Zertifikatprofil zu ermitteln.

#### <a name="wi-fi-profile"></a>Wi-Fi-Profil

WLAN-Profile werden verwendet, um automatisch ein mobiles Gerät mit einem drahtlosen Netzwerk zu verbinden. Intune unterstützt die Bereitstellung von WLAN-Profilen auf allen unterstützten Plattformen. Weitere Informationen zur [Unterstützung von WLAN-Profilen in Intune](wi-fi-settings-configure.md).

Im Folgenden sehen Sie ein Beispiel eines Entwurfs für ein WLAN-Profil:

| **Typ** | **Profilname** | **Geräteplattform** | **Anwendungsfälle** |   
|:---:|:---:|:---:|:---:|
| WLAN | WLAN-Profil Asien | Android | Unternehmen, BYOD Region Asien|                                                           
| WLAN | WLAN-Profil Nordamerika | Android, iOS, Windows 10 Mobile | Unternehmen, BYOD Region Nordamerika |                                                           


Sie können eine [Vorlage der oben stehenden Tabelle herunterladen](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), um die Anforderungen an Ihr WLAN-Profil zu ermitteln.

#### <a name="vpn-profile"></a>VPN-Profil

Anhand von VPN-Profilen können Benutzer von Remotestandorten aus sicher auf Ihr Netzwerk zugreifen. Intune unterstützt VPN-Profile von nativen mobilen VPN-Verbindungen und Drittanbietern. Weitere Informationen zu [von Intune unterstützten VPN-Profilen und Anbietern](vpn-settings-configure.md).

Es folgt ein Beispiel für das Dokumentieren des Entwurfs eines VPN-Profils.

| **Typ** | **Profilname** | **Geräteplattform** | **Anwendungsfälle** |   
|:---:|:---:|:---:|:---:|
| VPN | VPN Cisco beliebiges Verbindungsprofil | Android, iOS, Windows 10 Mobile | Unternehmen, BYOD Nordamerika und Deutschland|                                                           
| VPN | Pulse Secure | Android | Unternehmen, BYOD Region Asien |                                                           


Sie können eine [Vorlage der oben stehenden Tabelle herunterladen](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), um die Anforderungen an Ihr VPN-Profil zu ermitteln.
#### <a name="email-profile"></a>E-Mail-Profil

E-Mail-Profile ermöglichen die automatische Einrichtung eines E-Mail-Clients mit Verbindungsinformationen und der E-Mail-Konfiguration. Intune unterstützt E-Mail-Profile auf einigen Geräten. Weitere Informationen zu [E-Mail-Profilen und den unterstützten Plattformen](email-settings-configure.md).

Unten sehen Sie ein Beispiel für das Dokumentieren des Entwurfs von E-Mail-Profilen:

| **Typ** | **Profilname** | **Geräteplattform** | **Anwendungsfälle** |   
|:---:|:---:|:---:|:---:|
| E-Mail-Profil | iOS-E-Mail-Profil | iOS | Unternehmen – Information Worker BYOD |                                                           
| E-Mail-Profil | Android Knox-E-Mail-Profil | Android Knox | BYOD |


Sie können eine [Vorlage der oben stehenden Tabelle herunterladen](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), um die Anforderungen an Ihr E-Mail-Profil zu ermitteln.
### <a name="apps"></a>Apps

Mithilfe von Intune können Sie Apps auf verschiedene Weise für Benutzer oder auf Geräten bereitstellen. Typen bereitgestellter Anwendungen enthalten Softwareinstallations-Apps, Apps aus einem öffentlichen App Store, externe Links oder verwaltete iOS-Apps. Zusätzlich zu einzelnen App-Bereitstellungen können per Volumenlizenz erworbene Apps über die VPPs (Volume Purchase Program) für iOS und Windows verwaltet und bereitgestellt werden. Weitere Informationen:

-   [Die App-Typen, die Sie bereitstellen](app-management.md)

-   [Das iOS Volume Purchase Program für Unternehmen (VPP)](vpp-apps-ios.md)

-   [Apps im Microsoft Store für Unternehmen](windows-store-for-business.md)

#### <a name="app-type-requirements"></a>Anforderungen an App-Typen

Da Apps für Benutzer und Geräte bereitgestellt werden können, empfiehlt es sich zu entscheiden, welche Anwendungen von Intune verwaltet werden sollen. Versuchen Sie beim Zusammenstellen der Liste folgende Fragen zu beantworten:

-   Ist für die Apps eine Integration mit Cloud-Diensten erforderlich?

-   Sind alle Apps für BYOD-Benutzer verfügbar?

-   Welche Bereitstellungsoptionen stehen für diese Apps zur Verfügung?

-   Muss Ihr Unternehmen seinen Partnern Zugriff auf Daten von SaaS-Apps (Software-as-a-Service) ermöglichen?

-   Ist für die Apps Internetzugriff von den Benutzergeräten aus erforderlich?

-   Sind die Apps in einem App Store öffentlich verfügbar, oder handelt es sich um benutzerdefinierte branchenspezifische Apps (Line-of-Business Apps, LOB Apps)?


#### <a name="app-protection-policies"></a>App-Schutzrichtlinien

Durch App-Schutzrichtlinien werden Datenverluste auf ein Minimum reduziert, indem sie definieren, wie Unternehmensdaten von der Anwendung verwaltet werden. Intune unterstützt App-Schutzrichtlinien für jede Anwendung, die mit der Verwaltung mobiler Apps funktionieren soll. Beim Entwerfen der App-Schutzrichtlinie müssen Sie entscheiden, welche Einschränkungen für Unternehmensdaten in einer bestimmten App gelten sollen. Es wird empfohlen, sich über die Funktionsweise von [App-Schutzrichtlinien](app-protection-policy.md) zu informieren. Im Folgenden finden Sie ein Beispiel für das Dokumentieren der vorhandenen Anwendungen und der entsprechenden Schutzmaßnahmen.

| **Anwendung** | **Zweck** | **Plattformen** | **Anwendungsfall** | **App-Schutzrichtlinie** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | Verfügbar | iOS | Unternehmen – Führungskräfte | Jailbreak nicht möglich, Verschlüsseln von Dateien |                                                         
| Word | Verfügbar | iOS, Android – Samsung Knox, andere als Knox, Windows 10 Mobile | Unternehmen, BYOD | Jailbreak nicht möglich, Verschlüsseln von Dateien |                                                         


Sie können eine [Vorlage der oben stehenden Tabelle herunterladen](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), um die Anforderungen an Ihre App-Schutzrichtlinien zu ermitteln.
#### <a name="compliance-policies"></a>Konformitätsrichtlinien

Konformitätsrichtlinien bestimmen, ob ein Gerät bestimmten Anforderungen entspricht. Intune ermittelt anhand von Konformitätsrichtlinien, ob ein Gerät als konform oder als nicht konform betrachtet wird. Der Konformitätsstatus kann dann dazu verwendet werden, den Zugriff auf Unternehmensressourcen einzuschränken oder zuzulassen. Wenn bedingter Zugriff erforderlich ist, wird empfohlen, eine [Gerätekonformitätsrichtlinie](device-compliance.md) zu entwerfen.

Bestimmen Sie anhand der Anforderungen und Anwendungsfälle, wie viele Gerätekonformitätsrichtlinien Sie benötigen und welche Benutzergruppen als Zielbenutzergruppen verwendet werden sollen. Darüber hinaus müssen Sie entscheiden, wie lange ein Gerät ohne Einchecken offline sein kann, bevor es als nicht konform betrachtet wird.

Es folgt ein Beispiel zum Entwerfen einer Konformitätsrichtlinie:

| **Name der Richtlinie** | **Geräteplattform** | **Einstellungen** | **Zielgruppe** |   
|:---:|:---:|:---:|:---:|
| Kompatibilitätsrichtlinie | iOS, Android – Samsung Knox, andere als Knox, Windows 10 Mobile | PIN – erforderlich, Jailbreak nicht möglich | Unternehmen, BYOD |


Sie können eine [Vorlage der oben stehenden Tabelle herunterladen](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), um die Anforderungen an Ihre Konformitätsrichtlinien zu ermitteln.
#### <a name="conditional-access-policies"></a>Bedingte Zugriffsrichtlinien

Bedingter Zugriff wird verwendet, um nur konformen Geräten den Zugriff auf E-Mails und andere Unternehmensressourcen zu erlauben. Intune kann mit EMS (Enterprise Mobility + Security) zum Steuern des Zugriffs auf Unternehmensressourcen eingesetzt werden. Sie müssen entscheiden, ob der bedingte Zugriff erforderlich ist und was gesichert werden muss. Weitere Informationen zum [bedingten Zugriff](conditional-access.md).

Entscheiden Sie hinsichtlich des Onlinezugriffs für welche Plattformen und Benutzergruppen die Richtlinien für bedingten Zugriff vorgesehen sind. Darüber hinaus entscheiden Sie, ob Sie den dienstübergreifenden Intune-Connector für Exchange Online oder Exchange lokal installieren/konfigurieren müssen. Weitere Informationen zum Installieren und Konfigurieren von dienstübergreifenden Intune-Connectors: <!---these links are correct--->

-   [Exchange Online](/intune-classic/deploy-use/intune-service-to-service-exchange-connector)

-   [Exchange lokal](exchange-connector-install.md)

Hier sehen Sie ein Beispiel für das Dokumentieren von Richtlinien für den bedingten Zugriff:

| **Dienst** | **Plattformen für moderne Authentifizierung** | **Standardauthentifizierung** | **Anwendungsfälle** |   
|:---:|:---:|:---:|:---:|
| Exchange Online | iOS, Android | Nicht konforme Geräte auf von Intune unterstützten Plattformen blockieren | Unternehmen, BYOD |
| SharePoint Online | iOS, Android |  | Unternehmen, BYOD |

Sie können eine [Vorlage der oben stehenden Tabelle herunterladen](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0), um die Anforderungen an Ihre Richtlinien für den bedingten Zugriff zu ermitteln.

## <a name="next-steps"></a>Nächste Schritte

Der nächste Abschnitt enthält Hinweise zum [Intune-Implementierungsprozess](planning-guide-onboarding.md).
