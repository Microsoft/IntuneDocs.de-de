---
title: Bedingter Zugriff mit Microsoft Intune
titlesuffix: ''
description: Erfahren Sie, wie der bedingte Zugriff von Intune im Allgemeinen für den gerätebasierten und den App-basierten bedingten Zugriff verwendet wird.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: db63d79a81de03a459a910a23fb9f999f33f0251
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231656"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>Welche gängigen Möglichkeiten gibt es für die Verwendung des bedingten Zugriffs in Intune?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Es gibt zwei Arten des bedingten Zugriffs in Intune: den gerätebasierten bedingten Zugriff und den App-basierten bedingten Zugriff. Sie müssen die entsprechenden Konformitätsrichtlinien konfigurieren, um die Konformität mit bedingtem Zugriff in Ihrer Organisation zu unterstützen. Der bedingte Zugriff wird häufig verwendet, um Aktionen wie die folgenden auszuführen: Zulassen oder Blockieren des Zugriffs auf Exchange lokal, Steuern des Zugriffs auf das Netzwerk oder Integrieren in eine Mobile Threat Defense-Lösung.

Im Folgenden finden Sie Informationen zur Verwendung der Intune-Funktionen für die Konformität von mobilen *Geräten* und der Intune-Funktionen für die Verwaltung mobiler *Anwendungen*. 

> [!NOTE]
> Bei bedingtem Zugriff handelt es sich um eine Azure Active Directory-Funktion, die in einer Azure Active Directory Premium-Lizenz enthalten ist. Intune erweitert diese Funktion, indem es der Lösung Konformität der mobilen Geräte und Mobile App-Verwaltung hinzufügt.

## <a name="device-based-conditional-access"></a>Gerätebasierter bedingter Zugriff

Intune und Azure Active Directory stellen gemeinsam sicher, dass nur verwaltete und konforme Geräte Zugriff auf E-Mails, Office 365-Dienste, SaaS-Apps (Software-as-a-Service) und [lokale Apps](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) erhalten. Zusätzlich können Sie in Azure Active Directory eine Richtlinie festlegen, die nur Computern, die der Domäne angehören, oder mobilen Geräten, die in Intune registriert sind, den Zugriff auf Office 365-Dienste erlaubt.

Intune stellt Funktionen für Gerätekonformitätsrichtlinien bereit, die den Konformitätsstatus der Geräte bewerten. Der Konformitätsstatus wird an Azure Active Directory gemeldet, um die in Azure Active Directory erstellte Richtlinie für den bedingten Zugriff zu erzwingen, wenn der Benutzer versucht, auf Unternehmensressourcen zuzugreifen.

Gerätebasierte Richtlinien für den bedingten Zugriff für Exchange Online und andere Office 365-Produkte werden über das [Azure-Portal](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune) konfiguriert.

-   Erfahren Sie mehr über den [bedingten Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

-   Erfahren Sie mehr über die [Gerätekonformität in Intune](device-compliance.md).

-   Erfahren Sie mehr über den [Schutz von E-Mail-, Office 365- und anderen Diensten mithilfe des bedingen Zugriffs in Intune](https://docs.microsoft.com/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

> [!NOTE]
> Wenn Sie den gerätebasierten Zugriff für Sharepoint Online auf Android-Geräten aktivieren, müssen Benutzer die Option **Browserzugriff aktivieren** auf dem Gerät wie folgt aktivieren:
> 1. Starten Sie die **Unternehmensportal-App**.
> 2. Rufen Sie die Seite **Einstellungen** über die Schaltfläche mit den drei Punkten (…) oder über die physische Menütaste auf.
> 3. Drücken Sie die Schaltfläche **Browserzugriff aktivieren** . 
> 4. Melden Sie sich im Chrome-Browser aus Office 365 ab, und starten Sie Chrome neu.

### <a name="conditional-access-for-exchange-on-premises"></a>Bedingter Zugriff für Exchange lokal

Der bedingte Zugriff kann zum Zulassen oder Sperren des Zugriffs auf **Exchange lokal** basierend auf den Konformitätsrichtlinien für Geräte und dem Registrierungsstatus verwendet werden. Wenn der bedingte Zugriff zusammen mit einer Gerätekonformitätsrichtlinie verwendet wird, ist nur konformen Geräten der Zugriff auf Exchange lokal gestattet.

Sie können erweiterte Einstellungen wie die folgenden für den bedingten Zugriff konfigurieren, um eine präzisere Steuerung zu erzielen:

-   Zulassen oder Blockieren bestimmter Plattformen

-   Sofortiges Blockieren von nicht über Intune verwalteten Geräten

Jedes Gerät, mit dem auf Exchange lokal zugegriffen wird, wird auf Konformität überprüft, wenn Richtlinien für Gerätekonformität und bedingten Zugriff angewendet werden.

Wenn Geräte die Bedingungen nicht erfüllen, erhält der Benutzer Anweisungen zum Registrieren des Geräts und zum Beheben des Problems, das die Konformität des Geräts verhindert.

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Funktionsweise des bedingten Zugriffs für Exchange lokal

Der Intune Exchange-Connector ruft alle EAS-Datensätze (Exchange Active Sync) ab, die auf dem Exchange-Server vorhanden sind, damit Intune diese Datensätze verwenden und den Intune-Gerätedatensätzen zuordnen kann. Bei diesen Datensätzen handelt es sich um Geräte, die bei Intune registriert sind und von Intune erkannt werden. Dieser Prozess erlaubt oder blockiert den E-Mail-Zugriff.

Wenn ein EAS-Datensatz neu und Intune noch nicht bekannt ist, gibt Intune ein Cmdlet aus, das den Zugriff auf E-Mails blockiert. Im Folgenden finden Sie weitere Details zur Funktionsweise dieses Prozesses:

![Flussdiagramm: Exchange lokal mit bedingtem Zugriff](./media/ca-intune-common-ways-1.png)

1.  Ein Benutzer versucht, auf Unternehmens-E-Mails zuzugreifen, die in Exchange lokal 2010 SP1 oder höher gehostet werden.

2.  Wenn das Gerät nicht durch Intune verwaltet wird, wird der E-Mail-Zugriff blockiert. Intune senden eine Benachrichtigung zur Blockierung an den EAS-Client.

3.  EAS empfängt die Benachrichtigung, verschiebt das Gerät in die Quarantäne und sendet eine Quarantäne-E-Mail mit Schritten zur Behebung und entsprechenden Links, sodass der Benutzer das Gerät registrieren kann.

4.  Der Prozess für den Arbeitsplatzbeitritt wird ausgeführt. Dies ist der erste Schritt, mit dem ein Gerät zur Verwaltung in Intune eingebunden wird.

5.  Das Gerät wird in Intune registriert.

6.  Intune ordnet den EAS-Datensatz einem Gerätedatensatz zu und speichert den Konformitätszustand des Geräts.

7.  Die EAS-Client-ID wird vom Azure AD Device Registration-Prozess registriert, der eine Beziehung zwischen dem Intune-Gerätedatensatz und der EAS-Client-ID erstellt.

8.  Der Azure AD Device Registration-Prozess speichert die Informationen zum Gerätezustand.

9.  Wenn der Benutzer die Richtlinien für den bedingten Zugriff erfüllt, gibt Intune ein Cmdlet über den Intune Exchange-Connector aus, mit dem das Postfach synchronisiert werden kann.

10. Der Exchange-Server sendet eine Benachrichtigung an den EAS-Client, damit der Benachrichtigung auf die E-Mails zugreifen kann.

#### <a name="whats-the-intune-role"></a>Was ist die Intune-Rolle?

Intune bewertet und verwaltet den Gerätezustand.

#### <a name="whats-the-exchange-server-role"></a>Was ist die Exchange-Server-Rolle?

Der Exchange-Server stellt die API und die Infrastruktur bereit, um Geräte in die Quarantäne zu verschieben.

> [!IMPORTANT]
> Denken Sie daran, dass dem Benutzer, der das Gerät verwendet, ein Konformitätsprofil zugewiesen sein muss, damit das Gerät hinsichtlich der Konformität bewertet werden kann. Wenn keine Konformitätsrichtlinie für den Benutzer bereitgestellt wird, wird das Gerät als konform behandelt, und es werden keine Zugriffsbeschränkungen angewendet.

### <a name="conditional-access-based-on-network-access-control"></a>Bedingter Zugriff basierend auf der Netzwerkzugriffssteuerung

Intune ist in Partnerlösungen wie Cisco ISE, Aruba Clear Pass und Citrix NetScaler integriert, um die Zugriffssteuerung basierend auf der Intune-Registrierung und dem Konformitätszustand des Geräts bereitzustellen.

Benutzern kann der Zugriff auf unternehmenseigene WLAN- oder VPN-Ressourcen erlaubt oder verweigert werden, je nachdem, ob das verwendete Gerät verwaltet wird und den Intune-Konformitätsrichtlinien für Geräte entspricht.

-   Erfahren Sie mehr über die [NAC-Integration in Intune](network-access-control-integrate.md).

### <a name="conditional-access-based-on-device-risk"></a>Bedingter Zugriff basierend auf dem Geräterisiko

Intune arbeitet mit MTD-Anbietern (Mobile Threat Defense) zusammen, um eine Sicherheitslösung bereitzustellen, die Schadsoftware, Trojaner und andere Bedrohungen auf mobilen Geräten erkennt.

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Funktionsweise von Intune und der Integration von MTD-Lösungen

Wenn der Mobile Threat Defense-Agent auf mobilen Geräten installiert ist, kann dieser Benachrichtigungen zum Konformitätszustand an Intune zurücksenden, um zu melden, ob auf dem mobilen Gerät eine Bedrohung gefunden wurde.

Die Integration von Intune und Mobile Threat Defense-Lösungen spielt eine wichtige Rolle bei Entscheidungen zum bedingten Zugriff basierend auf dem Geräterisiko.

-   Erfahren Sie mehr über [Intune Mobile Threat Defense](https://docs.microsoft.com/intune-classic/deploy-use/mobile-threat-defense).

### <a name="conditional-access-for-windows-pcs"></a>Bedingter Zugriff für Windows-PCs

Der bedingte Zugriff für PCs bietet eine Funktionalität, die der für mobile Geräte verfügbaren ähnlich ist. Im Folgenden finden Sie Informationen zu den verschiedenen Möglichkeiten, den bedingten Zugriff beim Verwalten von PCs mit Intune zu verwenden.

#### <a name="corporate-owned"></a>Unternehmenseigene Geräte

-   **In die lokale AD-Domäne eingebunden**: Diese Option wird häufig von Unternehmen genutzt, die ziemlich vertraut sind mit der Art, in der sie ihre PCs bereits über AD-Gruppenrichtlinien und/oder mit System Center Configuration Manager verwalten.

-   **In die Azure AD-Domäne eingebunden und über Intune verwaltet**: Diese Option zielt üblicherweise auf CYOD-Bereitstellungen (Choose Your Own Device) und Roamingszenarien mit Laptops ab, die selten mit dem Unternehmensnetzwerk verbunden sind. Das Gerät tritt der Azure AD-Domäne bei und wird bei Intune registriert. Dadurch entsteht keinerlei Abhängigkeit von einer lokalen Active Directory-Instanz oder Domänencontrollern. Diese Option kann als Kriterium für den bedingten Zugriff auf Unternehmensressourcen verwendet werden.

-   **In die AD-Domäne eingebunden und System Center Configuration Manager**: Im aktuellen Branch stellt System Center Configuration Manager Funktionen für den bedingten Zugriff bereit, die bestimmte Konformitätskriterien auswerten können. Zusätzlich muss der PC in die Domäne eingebunden sein:

    -   Ist der PC verschlüsselt?

    -   Ist Schadsoftware installiert? Ist der PC auf dem neuesten Stand?

    -   Wurde das Gerät per Jailbreak oder Rooting manipuliert?

#### <a name="bring-your-own-device-byod"></a>Bring Your Own Device (BYOD)

-   **Arbeitsplatzbeitritt und Intune-Verwaltung**: Bei dieser Option können Benutzer ihre persönlichen Geräte einbinden, um auf Unternehmensressourcen und -dienste zuzugreifen. Sie können den Arbeitsplatzbeitritt verwenden und Geräte bei Intune registrieren, um Richtlinien auf Geräteebene zu erhalten. Dies ist eine weitere Option zum Auswerten von Kriterien für den bedingten Zugriff.

## <a name="app-based-conditional-access"></a>App-basierter bedingter Zugriff

Intune und Azure Active Directory stellen gemeinsam sicher, dass nur verwaltete Geräte auf Unternehmens-E-Mails oder andere Office 365-Dienste zugreifen können.

-   Erfahren Sie mehr über den [App-basierten bedingten Zugriff mit Intune](app-based-conditional-access-intune.md).

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren des bedingten Zugriffs in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[Installieren des lokalen Exchange Connectors für Intune](https://docs.microsoft.com/intune/exchange-connector-install)

[Erstellen einer Richtlinie für den bedingten Zugriff auf Exchange lokal](conditional-access-exchange-create.md)
