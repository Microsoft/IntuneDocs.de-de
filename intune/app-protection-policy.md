---
title: Was sind App-Schutzrichtlinien?
titleSuffix: Microsoft Intune
description: Lernen Sie, wie Ihnen App-Schutzrichtlinien von Microsoft Intune helfen, Ihre Unternehmensdaten zu schützen und Datenverluste zu verhindern.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/14/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 64e58ef4d27d2f967eff8c503842345879799168
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48232204"
---
# <a name="what-are-app-protection-policies"></a>Was sind App-Schutzrichtlinien?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

App-Schutzrichtlinien von Microsoft Intune helfen, Ihre Unternehmensdaten zu schützen und Datenverluste zu verhindern.

## <a name="how-you-can-protect-app-data"></a>Wie Sie Ihre App-Daten schützen können
Ihre Mitarbeiter verwenden mobile Geräte für private und berufliche Aufgaben.  Sie möchten einerseits die Produktivität Ihrer Mitarbeiter sicherstellen, möchten andererseits aber auch Datenverlust verhindern, sei er beabsichtigt oder unbeabsichtigt.  Darüber hinaus möchten Sie auch dann die Möglichkeit zum Schützen der Unternehmensdaten haben, wenn der Zugriff darauf über Geräte erfolgt, die nicht von Ihnen verwaltet werden.

Sie können Intune-App-Schutzrichtlinien verwenden, um Ihre Unternehmensdaten zu schützen. Da Intune-App-Schutzrichtlinien **unabhängig von Lösungen für die Verwaltung mobiler Geräte (MDM) einsetzbar sind**, können Sie sie mit oder ohne Registrierung der Geräte bei einer Geräteverwaltungslösung zum Schutz Ihrer Unternehmensdaten verwenden. Durch die Implementierung von **Richtlinien auf App-Ebene** können Sie den Zugriff auf Unternehmensressourcen einschränken und Daten im Zuständigkeitsbereich der IT-Abteilung halten.

App-Schutzrichtlinien können für Apps konfiguriert werden, die auf Geräten ausgeführt werden, die folgende Voraussetzungen erfüllen:

- **Registriert bei Microsoft Intune:** Die Geräte in dieser Kategorie sind in der Regel unternehmenseigene Geräte.

- **Registriert bei einer Drittanbieterlösung für die Verwaltung mobiler Geräte (MDM, Mobile Device Management):** Die Geräte in dieser Kategorie sind in der Regel unternehmenseigene Geräte.

  > [!NOTE]
  > Verwaltungsrichtlinien für mobile Apps sollten nicht in Verbindung mit Verwaltungslösungen für mobile Geräte von Drittanbietern oder sicheren Containerlösungen verwendet werden.

- **Nicht bei einer Lösung für die Verwaltung mobiler Geräte registriert:** Die Geräte in dieser Kategorie sind in der Regel mitarbeitereigene Geräte, die weder bei Intune noch anderen MDM-Lösungen registriert sind oder dort verwaltet werden.

> [!IMPORTANT]
> Sie können Verwaltungsrichtlinien für mobile Apps für mobile Office-Apps erstellen, die eine Verbindung mit Office 365-Diensten herstellen. Außerdem können Sie den Zugriff auf lokale Exchange-Postfächer schützen, indem Sie Intune-App-Schutzrichtlinien für Outlook für iOS und Android erstellen, die mit hybrider moderner Authentifizierung aktiviert wurden. Bevor Sie dieses Feature verwenden, sollten Sie sicherstellen, dass Sie die [Anforderungen für Outlook für iOS und Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) erfüllen. App-Schutzrichtlinien werden nicht für andere Apps unterstützt, die eine Verbindung mit lokalen Exchange- oder SharePoint-Diensten herstellen.

**Die wichtigsten Vorteile von App-Schutzrichtlinien sind:**

-   Schutz Ihrer Unternehmensdaten auf App-Ebene.  Da die Verwaltung von mobilen Apps keine Geräteverwaltung voraussetzt, können Sie Unternehmensdaten auf verwalteten und auf unverwalteten Geräten schützen. Bei der Verwaltung wird die Benutzeridentität in den Mittelpunkt gestellt, wodurch sich die Geräteverwaltung erübrigt.

-   Die Produktivität der Endbenutzer wird nicht beeinträchtigt, und die Richtlinien werden nicht angewendet, wenn die App im privaten Kontext verwendet wird.  Die Richtlinien werden nur auf den beruflichen Kontext angewendet, wodurch Sie die Möglichkeit haben, Unternehmensdaten zu schützen, ohne dass private Daten einbezogen werden.

Es gibt weitere Vorteile bei der Verwendung einer MDM mit App-Schutzrichtlinien, und Unternehmen können App-Schutzrichtlinien sowohl mit als auch ohne MDM gleichzeitig verwenden. So kann ein Mitarbeiter beispielsweise ein unternehmenseigenes Smartphone und ein privates Tablet verwenden.  In diesem Fall wird das unternehmenseigene Smartphone in einer MDM registriert und von App-Schutzrichtlinien geschützt, während das private Geräte nur mit App-Schutzrichtlinien geschützt wird.

- **Eine MDM-Lösung stellt sicher, dass das Gerät geschützt ist**.  So können Sie beispielsweise die Eingabe einer PIN für den Zugriff auf das Gerät anfordern, oder Sie können verwaltete Apps auf dem Gerät bereitstellen. Sie können Apps auch über die MDM-Lösung auf Geräten bereitstellen, um mehr Kontrolle über die App-Verwaltung zu haben.

- **App-Schutzrichtlinien stellen sicher, dass Schutzfunktionen auf App-Ebene vorhanden sind**. So können Sie beispielsweise eine PIN anfordern, wenn eine App im beruflichen Kontext geöffnet werden soll oder wenn Daten zwischen Apps ausgetauscht werden können oder um zu verhindern, dass App-Daten des Unternehmens an einem privaten Speicherort gespeichert werden.


### <a name="supported-platforms-for-app-protection-polices"></a>Unterstützte Plattformen für App-Schutzrichtlinien
Die Plattform für Schutzrichtlinien für Intune-Apps ist auf die Plattformunterstützung für Office-Anwendungen ausgerichtet. Weitere Informationen finden Sie unter [Systemanforderungen für Office](https://products.office.com/en-US/office-system-requirements).

Windows-Geräte werden momentan nicht unterstützt. Wenn Sie jedoch Windows 10-Geräte mit Intune registrieren, können Sie Windows Information Protection verwenden, das ähnliche Funktionen bietet. Weitere Informationen finden Sie unter [Schutz von Unternehmensdaten mit Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
##  <a name="how-app-protection-policies-protect-app-data"></a>So schützen App-Schutzrichtlinien Ihre App-Daten

####  <a name="apps-without-app-protection-policies"></a>Apps ohne App-Schutzrichtlinien

![Die Abbildung zeigt, dass Daten ungehindert zwischen Apps verschoben werden können, wenn keine App-Schutzrichtlinien angewendet werden.](./media/apps-without-protection-policies.png)

Wenn Apps ohne Einschränkungen verwendet werden, können Unternehmensdaten und private Daten vermischt werden.  Unternehmensdaten könnten damit an Speicherorten wie dem persönlichen Speicher abgelegt oder an Apps außerhalb Ihres Zuständigkeitsbereichs übermittelt werden, was Datenverlust bedeuten würde. Die Pfeile im Diagramm zeigen die uneingeschränkte Datenbewegung zwischen Apps (geschäftlich und privat) und zu Speicherorten.


### <a name="data-protection-with-app-protection-policies"></a>Datenschutz mit App-Schutzrichtlinien

![Die Abbildung zeigt, wie Unternehmensdaten durch die Anwendung von App-Schutzrichtlinien geschützt werden. ](./media/apps-with-protection-policies.png)


Mit App-Schutzrichtlinien können Sie verhindern, dass Unternehmensdaten im lokalen Speicher des Geräts gespeichert werden. Außerdem können Sie das Verschieben von Daten in andere Apps einschränken, die nicht durch App-Schutzrichtlinien geschützt sind. Einstellungen für App-Schutzrichtlinien:
- Richtlinien zur Datenverschiebung wie **„Speichern unter“ verhindern**, **Ausschneiden, Kopieren und Einfügen einschränken**.
- Einstellungen von Zugriffsrichtlinien wie **Einfache PIN für den Zugriff erforderlich**, **Ausführen verwalteter Apps auf Geräten mit Jailbreak oder Rootzugriff blockieren**.

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mdm-solution"></a>Schutz von Daten mit App-Schutzrichtlinien auf Geräten, die durch eine MDM-Lösung verwaltet werden

![Die Abbildung zeigt, wie App-Schutzrichtlinien auf BYOD-Geräten funktionieren.](./media/app-protection-policies-with-mdm.png)

**Für Geräte, die in einer MDM-Lösung registriert sind**-

Die obige Abbildung zeigt die Schutzebenen, die durch den gemeinsamen Einsatz von MDM und App-Schutzrichtlinien geboten werden.

Die MDM-Lösung:

-   Registrieren das Gerät

-   Stellt die Apps auf dem Gerät bereit

-   Sorgt für kontinuierliche Gerätekonformität und -verwaltung

**App-Schutzrichtlinien bieten Mehrwert:**

-   Sie tragen zum Schutz der Unternehmensdaten bei, indem der Zugriff durch Verbraucher-Apps und -Dienste verhindert wird.

-   Es werden Einschränkungen („Speichern unter“, Zwischenablage, PIN usw.) auf Client-Apps angewendet.

-   Unternehmensdaten können aus Apps entfernt werden, ohne die Apps vom Gerät zu löschen.


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Schutz von Daten mit App-Schutzrichtlinien für Geräte ohne Registrierung

![Die Abbildung zeigt, wie App-Schutzrichtlinien auf verwalteten Geräten funktionieren.](./media/app-protection-policies-without-mdm.png)

Das obige Diagramm zeigt, wie die Datenschutzrichtlinien auf App-Ebene ohne MDM funktionieren.

Bei BYOD-Geräten, die nicht in einer MDM-Lösung registriert sind, können App-Schutzrichtlinien dazu beitragen, Unternehmensdaten auf App-Ebene zu schützen.
Es gibt jedoch einige Einschränkungen, die Sie kennen sollten:

-   Sie können auf dem Gerät keine Apps bereitstellen.  Der Endbenutzer muss die Apps aus dem Store beziehen.

-   Sie können auf diesen Geräten keine Zertifikatprofile bereitstellen.

-   Sie können auf diesen Geräten keine unternehmensweiten WLAN- und VPN-Einstellungen bereitstellen.

## <a name="app-protection-global-policy"></a>Globale App-Schutzrichtlinie

Wenn ein OneDrive-Administrator zu **admin.office.com** wechselt und **Gerätezugriff** auswählt, kann er die Steuerelemente für die **Verwaltung mobiler Anwendungen** auf die OneDrive- und SharePoint-Client-Apps festlegen. 

Die Einstellungen, die für die OneDrive-Administratorkonsole zur Verfügung gestellt wurden, konfigurieren eine besondere App-Schutzrichtlinie für Intune, die **globale Richtlinie**. Diese globale Richtlinie gilt für alle Benutzer in Ihrem Mandanten und kann nicht eingeschränkt angewendet werden. 

Sobald sie aktiviert ist, werden die OneDrive- und SharePoint-Apps für iOS und Android standardmäßig über die ausgewählten Einstellungen geschützt. Ein IT-Experte kann diese Richtlinie in der Intune-Konsole ändern, sobald sie erstellt wurde, und weitere Ziel-Apps hinzufügen und Richtlinieneinstellungen ändern. 

Standardmäßig darf nur eine **globale Richtlinie** pro Mandant vorhanden sein. Die [Intune Graph-APIs](intune-graph-apis.md) können jedoch verwendet werden, um zusätzliche globale Richtlinien pro Mandant zu erstellen. Dies wird jedoch nicht empfohlen. Das Erstellen zusätzlicher globaler Richtlinien wird nicht empfohlen, da die Problembehandlung bei der Implementierung einer solchen Richtlinie sehr kompliziert sein kann.

Obwohl die **globale Richtlinie** für alle Benutzer in Ihrem Mandanten gilt, werden diese Einstellungen von jeder standardmäßigen App-Schutzrichtlinie für Intune überschrieben.


## <a name="multi-identity"></a>Mehrere Identitäten

Apps, die mehrere Identitäten unterstützen, bieten Ihnen die Möglichkeit, verschiedene Konten (Geschäfts- und persönliche Konten) für den Zugriff auf die gleichen Apps zu verwenden. Hierbei werden App-Schutzrichtlinien nur angewendet, wenn die Apps im Arbeitskontext verwendet werden.

Wenn ein Benutzer beispielsweise die OneDrive-App mit seinem Geschäftskonto startet, kann er die Dateien nicht an einen persönlichen Speicherort verschieben. Wenn der Benutzer OneDrive jedoch mit einem persönlichen Konto verwendet, kann er Daten ohne Einschränkung aus dem persönlichen OneDrive kopieren und verschieben.

- Erfahren Sie mehr über die Apps, die [die Verwaltung mobiler Anwendungen und mehrerer Identitäten](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) mit Intune unterstützen.

##  <a name="next-steps"></a>Nächste Schritte

[Erstellen und Bereitstellen von App-Schutzrichtlinien mit Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Siehe auch
Apps von Drittanbietern wie beispielsweise die mobile Salesforce-App arbeiten auf eine bestimmte Weise mit Intune zusammen, um die Unternehmensdaten zu schützen. Weitere Informationen zur speziellen Zusammenarbeit der Salesforce-App mit Intune (einschließlich Konfigurationseinstellungen für die MDM-App) finden Sie unter [Salesforce-App und Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).
