---
title: Szenarien für bedingten Zugriff
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie der bedingte Zugriff von Intune im Allgemeinen für den gerätebasierten und den App-basierten bedingten Zugriff verwendet wird.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 92e6aa1a66429c6407556444e903c158aff9dfa0
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885996"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>Welche gängigen Möglichkeiten gibt es für die Verwendung des bedingten Zugriffs in Intune?

[!INCLUDE [azure_portal](../includes/azure_portal.md)]


Es gibt zwei Arten des bedingten Zugriffs in Intune: den gerätebasierten bedingten Zugriff und den App-basierten bedingten Zugriff. Sie müssen die entsprechenden Konformitätsrichtlinien konfigurieren, um die Konformität mit bedingtem Zugriff in Ihrer Organisation zu unterstützen. Der bedingte Zugriff wird häufig verwendet, um Aktionen wie die folgenden auszuführen: Zulassen oder Blockieren des Zugriffs auf Exchange, Steuern des Zugriffs auf das Netzwerk oder Integrieren in eine Mobile Threat Defense-Lösung.
 
In diesem Artikel finden Sie Informationen zur Verwendung der Intune-Funktionen für die Konformität von mobilen *Geräten* und der Intune-Funktionen für die Verwaltung mobiler *Anwendungen* (Mobile Application Management, MAM). 

> [!NOTE]
> Bei dem bedingtem Zugriff handelt es sich um eine Azure Active Directory-Funktion, die in einer Azure Active Directory Premium-Lizenz enthalten ist. Intune erweitert diese Funktion, indem es der Lösung Konformität der mobilen Geräte und Mobile App-Verwaltung hinzufügt. Bei dem Knoten für bedingten Zugriff, auf den aus *Intune* zugegriffen wird, handelt es sich um denselben Knoten, auf den aus *Azure AD* zugegriffen wird.  

## <a name="device-based-conditional-access"></a>Gerätebasierter bedingter Zugriff

Intune und Azure Active Directory stellen gemeinsam sicher, dass nur verwaltete und konforme Geräte Zugriff auf E-Mails, Office 365-Dienste, SaaS-Apps (Software-as-a-Service) und [lokale Apps](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) erhalten. Zusätzlich können Sie in Azure Active Directory eine Richtlinie festlegen, die nur Computern, die der Domäne angehören, oder mobilen Geräten, die in Intune registriert sind, den Zugriff auf Office 365-Dienste erlaubt.

Intune stellt Funktionen für Gerätekonformitätsrichtlinien bereit, die den Konformitätsstatus der Geräte bewerten. Der Konformitätsstatus wird an Azure Active Directory gemeldet, um die in Azure Active Directory erstellte Richtlinie für den bedingten Zugriff zu erzwingen, wenn ein Benutzer versucht, auf Unternehmensressourcen zuzugreifen.

Gerätebasierte Richtlinien für den bedingten Zugriff für Exchange Online und andere Office 365-Produkte werden im [Azure-Portal](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune) konfiguriert.  

- Erfahren Sie mehr über [Vorschreiben der Verwendung verwalteter Geräte für den Zugriff auf Cloud-Apps mithilfe des bedingten Zugriffs](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices).

- Erfahren Sie mehr über die [Gerätekonformität in Intune](device-compliance-get-started.md).

- Erfahren Sie mehr über [Unterstützte Browser für den bedingten Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/technical-reference#supported-browsers).

> [!NOTE]
> Wenn Sie auf Android-Geräten den gerätebasierten Zugriff für SharePoint Online oder den browserbasierten Zugriff auf Exchange Online aktivieren, müssen Benutzer die Option **Browserzugriff aktivieren** auf dem Gerät wie folgt aktivieren:
> 1. Starten Sie die **Unternehmensportal-App**.
> 2. Rufen Sie die Seite **Einstellungen** über die Schaltfläche mit den drei Punkten (…) oder über die physische Menütaste auf.
> 3. Drücken Sie die Schaltfläche **Browserzugriff aktivieren** . 
> 4. Melden Sie sich im Chrome-Browser von Office 365 ab, und starten Sie Chrome erneut.

### <a name="conditional-access-based-on-network-access-control"></a>Bedingter Zugriff basierend auf der Netzwerkzugriffssteuerung

Intune lässt sich in Partnerlösungen wie Cisco ISE, Aruba Clear Pass und Citrix NetScaler integrieren, um die Zugriffssteuerung basierend auf der Intune-Registrierung und dem Konformitätszustand eines Geräts bereitzustellen.

Benutzern kann der Zugriff auf unternehmenseigene WLAN- oder VPN-Ressourcen erlaubt oder verweigert werden, je nachdem, ob das verwendete Gerät verwaltet wird und den Intune-Richtlinien für die Gerätekonformität entspricht.

- Erfahren Sie mehr über die [NAC-Integration in Intune](network-access-control-integrate.md).

### <a name="conditional-access-based-on-device-risk"></a>Bedingter Zugriff basierend auf dem Geräterisiko

Intune arbeitet mit MTD-Anbietern (Mobile Threat Defense) zusammen, um eine Sicherheitslösung bereitzustellen, die Schadsoftware, Trojaner und andere Bedrohungen auf mobilen Geräten erkennt.

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Funktionsweise von Intune und der Integration von MTD-Lösungen

Wenn der Mobile Threat Defense-Agent auf mobilen Geräten installiert ist, sendet dieser Benachrichtigungen zum Konformitätszustand an Intune zurück, die eine Meldung enthalten, wenn auf dem mobilen Gerät eine Bedrohung gefunden wurde.

Die Integration von Intune und Mobile Threat Defense ist ein wichtiger Faktor bei Entscheidungen zum bedingten Zugriff basierend auf dem Geräterisiko.

- Erfahren Sie mehr über [Intune Mobile Threat Defense](mobile-threat-defense.md).

### <a name="conditional-access-for-windows-pcs"></a>Bedingter Zugriff für Windows-PCs

Der bedingte Zugriff für PCs bietet eine Funktionalität, die der für mobile Geräte verfügbaren ähnlich ist. Im Folgenden finden Sie Informationen zu den verschiedenen Möglichkeiten, den bedingten Zugriff beim Verwalten von PCs mit Intune zu verwenden.

#### <a name="corporate-owned"></a>Unternehmenseigene Geräte

- **In die lokale AD-Domäne eingebunden**: Diese Option wird häufig von Organisationen genutzt, die bereits mit der Verwaltung ihrer PCs über AD-Gruppenrichtlinien oder Configuration Manager vertraut sind.

- **In die Azure AD-Domäne eingebunden und über Intune verwaltet**: Dieses Szenario eignet sich für Organisationen, die einen Cloud-First-Ansatz (primäre Nutzung von Clouddiensten, sodass weniger lokale Infrastruktur erforderlich ist) oder einen Cloud-Only-Ansatz (gar keine lokale Infrastruktur) verfolgen möchten. Die Azure AD-Einbindung lässt sich gut in einer hybriden Umgebung einsetzen und bietet Zugriff auf Apps und Ressourcen sowohl in der Cloud als auch in der lokalen Infrastruktur. Geräte werden in Azure AD eingebunden und in Intune registriert – dies kann beim Zugriff auf Unternehmensressourcen als Kriterium für den bedingten Zugriff verwendet werden.

#### <a name="bring-your-own-device-byod"></a>Bring Your Own Device (BYOD)

- **Arbeitsplatzbeitritt und Intune-Verwaltung**: Bei dieser Option können Benutzer ihre persönlichen Geräte einbinden, um auf Unternehmensressourcen und -dienste zuzugreifen. Sie können den Arbeitsplatzbeitritt verwenden und Geräte bei Intune MDM registrieren, um Richtlinien auf Geräteebene zu erhalten. Dies ist eine weitere Option zum Auswerten von Kriterien für den bedingten Zugriff.

Erfahren Sie mehr über [Geräteverwaltung in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/overview).

## <a name="app-based-conditional-access"></a>App-basierter bedingter Zugriff

Intune und Azure Active Directory stellen gemeinsam sicher, dass nur verwaltete Geräte auf Unternehmens-E-Mails oder andere Office 365-Dienste zugreifen können.

- Erfahren Sie mehr über den [App-basierten bedingten Zugriff mit Intune](app-based-conditional-access-intune.md).

### <a name="intune-conditional-access-for-exchange-on-premises"></a>Bedingter Zugriff von Intune für Exchange lokal

Der bedingte Zugriff kann zum Zulassen oder Sperren des Zugriffs auf **Exchange lokal** basierend auf den Konformitätsrichtlinien für Geräte und dem Registrierungsstatus verwendet werden. Wenn der bedingte Zugriff zusammen mit einer Gerätekonformitätsrichtlinie verwendet wird, ist nur konformen Geräten der Zugriff auf Exchange lokal gestattet.

Sie können erweiterte Einstellungen wie die folgenden für den bedingten Zugriff konfigurieren, um eine präzisere Steuerung zu erzielen:

- Zulassen oder Blockieren bestimmter Plattformen

- Sofortiges Blockieren von Geräten, die nicht über Intune verwaltet werden

Jedes Gerät, mit dem auf Exchange lokal zugegriffen wird, wird auf Konformität überprüft, wenn Richtlinien für Gerätekonformität und bedingten Zugriff angewendet werden.

Wenn ein Gerät die festgelegten Bedingungen nicht erfüllt, erhält der Endbenutzer Anweisungen zum Registrieren des Geräts, um das Problem zu beheben, das die Konformität des Geräts verhindert.

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Funktionsweise des bedingten Zugriffs für Exchange lokal

Der bedingte Zugriff für Exchange lokal funktioniert anders als die Azure-Richtlinien für bedingten Zugriff. Sie installieren den Intune-Connector für Exchange lokal, um direkt mit dem Exchange-Server zu interagieren. Der Intune Exchange-Connector ruft alle EAS-Datensätze (Exchange Active Sync) ab, die auf dem Exchange-Server vorhanden sind, damit Intune diese Datensätze verwenden und den Intune-Gerätedatensätzen zuordnen kann. Bei diesen Datensätzen handelt es sich um Geräte, die bei Intune registriert sind und von Intune erkannt werden. Dieser Prozess erlaubt oder blockiert den E-Mail-Zugriff.

Wenn ein EAS-Datensatz neu und Intune noch nicht bekannt ist, gibt Intune ein Cmdlet („command-let“ ausgesprochen) aus, das den Exchange-Server anweist, den Zugriff auf E-Mails zu blockieren. Im Folgenden finden Sie weitere Details zur Funktionsweise dieses Prozesses:

![Flussdiagramm: Exchange lokal mit bedingtem Zugriff](./media/conditional-access-intune-common-ways-use/ca-intune-common-ways-1.png)

1. Ein Benutzer versucht, auf Unternehmens-E-Mails zuzugreifen, die in Exchange lokal 2010 SP1 oder höher gehostet werden.

2. Der E-Mail-Zugriff wird blockiert, wenn das Gerät nicht durch Intune verwaltet wird. Intune sendet eine Benachrichtigung zur Blockierung an den EAS-Client.

3. EAS empfängt die Benachrichtigung zur Blockierung, verschiebt das Gerät in die Quarantäne und sendet eine Quarantäne-E-Mail mit Schritten zur Behebung und entsprechenden Links, sodass Benutzer ihre Geräte registrieren können.

4. Der Prozess für den Arbeitsplatzbeitritt wird ausgeführt. Dies ist der erste Schritt, mit dem ein Gerät zur Verwaltung in Intune eingebunden wird.

5. Das Gerät wird in Intune registriert.

6. Intune ordnet den EAS-Datensatz einem Gerätedatensatz zu und speichert den Konformitätszustand des Geräts.

7. Die EAS-Client-ID wird vom Azure AD Device Registration-Prozess registriert, der eine Beziehung zwischen dem Intune-Gerätedatensatz und der EAS-Client-ID erstellt.

8. Der Azure AD Device Registration-Prozess speichert die Informationen zum Gerätezustand.

9. Wenn der Benutzer die Richtlinien für den bedingten Zugriff erfüllt, gibt Intune ein Cmdlet über den Intune Exchange Connector aus, mit dem das Postfach synchronisiert werden kann.

10. Der Exchange-Server sendet eine Benachrichtigung an den EAS-Client, damit der Benachrichtigung auf die E-Mails zugreifen kann.


#### <a name="whats-the-intune-role"></a>Was ist die Intune-Rolle?

Intune bewertet und verwaltet den Gerätezustand.

#### <a name="whats-the-exchange-server-role"></a>Was ist die Exchange-Server-Rolle?

Der Exchange-Server stellt die API und die Infrastruktur bereit, um Geräte in die Quarantäne zu verschieben.

> [!IMPORTANT]
> Denken Sie daran, dass dem Benutzer, der das Gerät verwendet, ein Konformitätsprofil und eine Intune-Lizenz zugewiesen sein müssen, damit das Gerät hinsichtlich der Konformität bewertet werden kann. Wenn keine Konformitätsrichtlinie für den Benutzer bereitgestellt wird, wird das Gerät als konform behandelt, und es werden keine Zugriffsbeschränkungen angewendet.

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren des bedingten Zugriffs in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[Einrichten App-basierter Richtlinien für bedingten Zugriff](app-based-conditional-access-intune-create.md)

[Installieren des lokalen Exchange Connectors für Intune](exchange-connector-install.md)

[Erstellen einer Richtlinie für den bedingten Zugriff auf Exchange lokal](conditional-access-exchange-create.md)
