---
title: Was sind App-Schutzrichtlinien?
titleSuffix: Microsoft Intune
description: Lernen Sie, wie Ihnen App-Schutzrichtlinien von Microsoft Intune helfen, Ihre Unternehmensdaten zu schützen und Datenverluste zu verhindern.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: b6ebc3db81b969d83bc22034057ab4217e90931f
ms.sourcegitcommit: e9ba1280b95565a5c5674b825881655d0303e688
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54297280"
---
# <a name="what-are-app-protection-policies"></a>Was sind App-Schutzrichtlinien?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

App-Schutzrichtlinien von Microsoft Intune helfen, Ihre Unternehmensdaten zu schützen und Datenverluste zu verhindern.

## <a name="how-you-can-protect-app-data"></a>Wie Sie Ihre App-Daten schützen können
Ihre Mitarbeiter verwenden mobile Geräte für private und berufliche Aufgaben. Sie möchten einerseits die Produktivität Ihrer Mitarbeiter sicherstellen, möchten andererseits aber Datenverlust verhindern, sei er beabsichtigt oder unbeabsichtigt. Sie sollten außerdem Unternehmensdaten schützen, auf die über Geräte zugegriffen wird, die nicht von Ihnen verwaltet werden.

Sie können Intune-App-Schutzrichtlinien **unabhängig von jeglicher mobilen Geräteverwaltungslösung** verwenden. Diese Unabhängigkeit hilft Ihnen, die Daten Ihres Unternehmens zu schützen, egal, ob Geräte in einer Geräteverwaltungslösung registriert sind oder nicht. Durch die Implementierung von **Richtlinien auf App-Ebene** können Sie den Zugriff auf Unternehmensressourcen einschränken und Daten im Zuständigkeitsbereich der IT-Abteilung halten.

App-Schutzrichtlinien können für Apps konfiguriert werden, die auf Geräten ausgeführt werden, die folgende Voraussetzungen erfüllen:

- **Bei Microsoft Intune registriert:** In der Regel sind diese Geräte unternehmenseigene Geräte.

- **Bei einer Drittanbieterlösung für die Verwaltung mobiler Geräte (MDM, Mobile Device Management) registriert:** In der Regel sind diese Geräte unternehmenseigene Geräte.

  > [!NOTE]
  > Verwaltungsrichtlinien für mobile Apps sollten nicht in Verbindung mit Verwaltungslösungen für mobile Geräte von Drittanbietern oder sicheren Containerlösungen verwendet werden.

- **Nicht bei einer Lösung für die mobile Geräteverwaltung registriert:** Diese Geräte sind in der Regel eigene Geräte der Mitarbeiter, die nicht in Intune oder anderen MDM-Lösungen verwaltet oder registriert werden.

> [!IMPORTANT]
> Sie können Verwaltungsrichtlinien für mobile Apps für mobile Office-Apps erstellen, die eine Verbindung mit Office 365-Diensten herstellen. Außerdem können Sie den Zugriff auf lokale Exchange-Postfächer schützen, indem Sie Intune-App-Schutzrichtlinien für Outlook für iOS und Android erstellen, die mit hybrider moderner Authentifizierung aktiviert wurden. Bevor Sie dieses Feature verwenden, sollten Sie sicherstellen, dass Sie die [Anforderungen für Outlook für iOS und Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) erfüllen. App-Schutzrichtlinien werden nicht für andere Apps unterstützt, die eine Verbindung mit lokalen Exchange- oder SharePoint-Diensten herstellen.

**Die wichtigsten Vorteile von App-Schutzrichtlinien sind:**

-   Schutz Ihrer Unternehmensdaten auf App-Ebene. Da die Verwaltung von mobilen Apps keine Geräteverwaltung voraussetzt, können Sie Unternehmensdaten auf verwalteten und auf nicht verwalteten Geräten schützen. Bei der Verwaltung wird die Benutzeridentität in den Mittelpunkt gestellt, wodurch sich die Geräteverwaltung erübrigt.

-   Die Produktivität der Endbenutzer wird nicht beeinträchtigt, und Richtlinien werden nicht angewendet, wenn die App in einem privaten Kontext verwendet wird. Die Richtlinien werden nur auf den beruflichen Kontext angewendet, wodurch Sie die Möglichkeit haben, Unternehmensdaten zu schützen, ohne dass private Daten einbezogen werden.

Es gibt weitere Vorteile bei der Verwendung einer MDM mit App-Schutzrichtlinien, und Unternehmen können App-Schutzrichtlinien sowohl mit als auch ohne MDM gleichzeitig verwenden. Nehmen Sie beispielsweise weinen Mitarbeiter an, der sowohl ein unternehmenseigenes Smartphone als auch seinen privaten Tablet verwendet. Das unternehmenseigene Smartphone wird in einer MDM registriert und von App-Schutzrichtlinien geschützt, während das private Gerät nur von App-Schutzrichtlinien geschützt wird.

- **Eine MDM-Lösung stellt sicher, dass das Gerät geschützt ist**. So können Sie beispielsweise die Eingabe einer PIN für den Zugriff auf das Gerät anfordern, oder Sie können verwaltete Apps auf dem Gerät bereitstellen. Sie können Apps auch über die MDM-Lösung auf Geräten bereitstellen, um mehr Kontrolle über die App-Verwaltung zu haben.

- **App-Schutzrichtlinien stellen sicher, dass Schutzfunktionen auf App-Ebene vorhanden sind**. Beispielsweise können Sie folgende Aktionen ausführen:
  - Anfordern einer PIN zum Öffnen einer App in einem geschäftlichen Kontext 
  - Steuern des Teilens von Daten zwischen Apps 
  - Verhindern des Speicherns von Unternehmens-App-Daten an einem privaten Speicherort


### <a name="supported-platforms-for-app-protection-policies"></a>Unterstützte Plattformen für App-Schutzrichtlinien
Die Plattform für Schutzrichtlinien für Intune-Apps ist auf die Plattformunterstützung für mobile Office-Anwendungen für Android- und iOS-Geräte ausgerichtet. Weitere Informationen finden Sie im Abschnitt **Mobile Apps** unter [Systemanforderungen für Office](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg).

Windows-Geräte werden momentan nicht unterstützt. Sie können jedoch Windows Information Protection verwenden, das ähnliche Funktionen bietet. Weitere Informationen finden Sie unter [Schutz von Unternehmensdaten mit Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).


## <a name="how-app-protection-policies-protect-app-data"></a>So schützen App-Schutzrichtlinien Ihre App-Daten

#### <a name="apps-without-app-protection-policies"></a>Apps ohne App-Schutzrichtlinien

![Darstellung der Datenverschiebung zwischen Apps ohne Richtlinien](./media/apps-without-protection-policies.png)

Wenn Apps ohne Einschränkungen verwendet werden, können Unternehmensdaten und private Daten vermischt werden. Unternehmensdaten können damit an Speicherorten wie dem persönlichen Speicher abgelegt oder an Apps außerhalb Ihres Zuständigkeitsbereichs übermittelt werden, was Datenverlust bedeuten würde. Die Pfeile im vorangehenden Diagramm zeigen die uneingeschränkte Datenverschiebung zwischen sowohl geschäftlichen als auch privaten Apps sowie zu Speicherorten.


### <a name="data-protection-with-app-protection-policies"></a>Datenschutz mit App-Schutzrichtlinien

![Darstellung von Unternehmensdaten, die durch Richtlinien geschützt werden](./media/apps-with-protection-policies.png)


Mit App-Schutzrichtlinien können Sie verhindern, dass Unternehmensdaten im lokalen Speicher des Geräts gespeichert werden. Außerdem können Sie das Verschieben von Daten in andere Apps einschränken, die nicht durch App-Schutzrichtlinien geschützt sind. Einstellungen für App-Schutzrichtlinien:
- Richtlinien zur Datenverschiebung wie **„Speichern unter“ verhindern**und **Ausschneiden, Kopieren und Einfügen einschränken**.
- Einstellungen von Zugriffsrichtlinien wie **Einfache PIN für den Zugriff erforderlich** und **Ausführen verwalteter Apps auf mit Jailbreak oder Rooting manipulierten Geräten blockieren**.

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mobile-device-management-solution"></a>Schutz von Daten mit App-Schutzrichtlinien auf Geräten, die durch eine mobile Geräteverwaltungslösung verwaltet werden

![Die Abbildung zeigt, wie App-Schutzrichtlinien auf BYOD-Geräten funktionieren.](./media/app-protection-policies-with-mdm.png)

**Für Geräte, die in einer MDM-Lösung registriert sind**-

Die vorangehende Abbildung zeigt die Schutzebenen, die durch den gemeinsamen Einsatz von MDM und App-Schutzrichtlinien geboten werden.

Die MDM-Lösung:

-   Registrieren das Gerät

-   Stellt die Apps auf dem Gerät bereit

-   Sorgt für kontinuierliche Gerätekonformität und -verwaltung

**App-Schutzrichtlinien bieten Mehrwert:**

-   Sie tragen zum Schutz der Unternehmensdaten bei, indem der Zugriff durch Verbraucher-Apps und -Dienste verhindert wird.

-   Es werden Einschränkungen wie *Speichern unter*, *Zwischenablage* oder *PIN* auf Client-Apps angewendet.

-   Unternehmensdaten können aus Apps entfernt werden, ohne die Apps vom Gerät zu löschen.


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Schutz von Daten mit App-Schutzrichtlinien für Geräte ohne Registrierung

![Die Abbildung zeigt, wie App-Schutzrichtlinien auf verwalteten Geräten funktionieren.](./media/app-protection-policies-without-mdm.png)

Das voranstehende Diagramm zeigt, wie die Datenschutzrichtlinien auf App-Ebene ohne MDM funktionieren.

Bei BYOD-Geräten, die nicht in einer MDM-Lösung registriert sind, können App-Schutzrichtlinien dazu beitragen, Unternehmensdaten auf App-Ebene zu schützen.
Es gibt jedoch einige Einschränkungen, die Sie kennen sollten:

-   Sie können auf dem Gerät keine Apps bereitstellen. Der Endbenutzer muss die Apps aus dem Store beziehen.

-   Sie können auf diesen Geräten keine Zertifikatprofile bereitstellen.

-   Sie können auf diesen Geräten keine unternehmensweiten WLAN- und VPN-Einstellungen bereitstellen.

## <a name="app-protection-global-policy"></a>Globale App-Schutzrichtlinie

Wenn ein OneDrive-Administrator zu **admin.office.com** wechselt und **Gerätezugriff** auswählt, kann er die Steuerelemente für die **Verwaltung mobiler Anwendungen** auf die OneDrive- und SharePoint-Client-Apps festlegen. 

Die Einstellungen, die für die OneDrive-Administratorkonsole zur Verfügung gestellt wurden, konfigurieren eine besondere App-Schutzrichtlinie für Intune, die **globale Richtlinie**. Diese globale Richtlinie gilt für alle Benutzer in Ihrem Mandanten und kann nicht eingeschränkt angewendet werden. 

Sobald sie aktiviert ist, werden die OneDrive- und SharePoint-Apps für iOS und Android standardmäßig über die ausgewählten Einstellungen geschützt. Ein IT-Experte kann diese Richtlinie in der Intune-Konsole bearbeiten, um weitere Ziel-Apps hinzuzufügen und Richtlinieneinstellungen zu ändern. 

Standardmäßig darf nur eine **globale Richtlinie** pro Mandant vorhanden sein. [Intune Graph-APIs](intune-graph-apis.md) können Sie jedoch verwenden, um zusätzliche globale Richtlinien pro Mandant zu erstellen, was jedoch nicht empfohlen wird. Das Erstellen zusätzlicher globaler Richtlinien wird nicht empfohlen, da die Problembehandlung bei der Implementierung einer solchen Richtlinie sehr kompliziert sein kann.

Obwohl die **globale Richtlinie** für alle Benutzer in Ihrem Mandanten gilt, werden diese Einstellungen von jeder standardmäßigen App-Schutzrichtlinie für Intune überschrieben.


## <a name="multi-identity"></a>Mehrere Identitäten

Apps, die mehrere Identitäten unterstützen, bieten Ihnen die Möglichkeit, verschiedene Konten (Geschäfts- und persönliche Konten) für den Zugriff auf die gleichen Apps zu verwenden. Hierbei werden App-Schutzrichtlinien nur angewendet, wenn die Apps im Arbeitskontext verwendet werden.

Stellen Sie sich als Beispiel für privaten Kontext einen Benutzer vor, der ein neues Dokument in Word beginnt – dies gilt als privater Kontext, sodass die App-Schutzrichtlinien für Intune nicht angewendet werden. Sobald das Dokument im OneDrive-Unternehmenskonto gespeichert wird, steht es im Unternehmenskontext, und Intune-App-Schutzrichtlinien werden angewendet.

Betrachten Sie im geschäftlichen Kontext beispielsweise einen Benutzer, der die OneDrive-App mit seinem Geschäftskonto startet. Im geschäftlichen Kontext kann er keine Dateien an einen privaten Speicherort verschieben. Wenn der Benutzer OneDrive später jedoch mit einem persönlichen Konto verwendet, kann er Daten ohne Einschränkung aus dem persönlichen OneDrive kopieren und verschieben.

- Erfahren Sie mehr über die Apps, die [die Verwaltung mobiler Anwendungen und mehrerer Identitäten](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) mit Intune unterstützen.

## <a name="next-steps"></a>Nächste Schritte

[Erstellen und Bereitstellen von App-Schutzrichtlinien mit Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Siehe auch
Apps von Drittanbietern wie beispielsweise die mobile Salesforce-App arbeiten auf eine bestimmte Weise mit Intune zusammen, um die Unternehmensdaten zu schützen. Weitere Informationen zur speziellen Zusammenarbeit der Salesforce-App mit Intune (einschließlich Konfigurationseinstellungen für die MDM-App) finden Sie unter [Salesforce-App und Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).
