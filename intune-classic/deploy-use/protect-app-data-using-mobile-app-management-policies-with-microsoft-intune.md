---
title: Schützen von App-Daten mithilfe von MAM-Richtlinien
description: In diesem Thema wird erläutert, wie Verwaltungsrichtlinien für mobile Anwendungen helfen können, Ihre Unternehmensdaten zu schützen, Datenverlust zu verhindern sowie persönliche und geschäftliche Daten voneinander zu trennen.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: dcdee874e42aa9511c09fda43a8cc662afaea38a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="protect-app-data-using-app-protection-policies-with-microsoft-intune"></a>Schützen von App-Daten mithilfe der App-Schutzrichtlinien mit Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="how-you-can-protect-app-data"></a>Wie Sie Ihre App-Daten schützen können
Ihre Mitarbeiter verwenden mobile Geräte für private und berufliche Aufgaben. Sie möchten einerseits die Produktivität Ihrer Mitarbeiter sicherstellen, möchten andererseits aber auch Datenverlust verhindern, sei er beabsichtigt oder unbeabsichtigt.  Darüber hinaus möchten Sie Unternehmensdaten schützen können, auf die Mitarbeiter mit Geräten zugreifen, die nicht durch Sie verwaltet werden.

Sie können Intune-App-Schutzrichtlinien verwenden, um Ihre Unternehmensdaten zu schützen. Da Intune-App-Schutzrichtlinien **unabhängig von Lösungen für die Verwaltung mobiler Geräte (MDM) einsetzbar sind**, können Sie MAM mit oder ohne Registrierung der Geräte bei einer Geräteverwaltungslösung zum Schutz Ihrer Unternehmensdaten verwenden. Durch die Implementierung von **Richtlinien auf App-Ebene** können Sie den Zugriff auf Unternehmensressourcen einschränken und Daten im Zuständigkeitsbereich der IT-Abteilung halten.

Sie können App-Schutzrichtlinien für Apps konfigurieren, die auf Geräten ausgeführt werden, die folgende Voraussetzungen erfüllen:

-   **Registriert bei Microsoft Intune:** Die Geräte in dieser Kategorie sind in der Regel unternehmenseigene Geräte.

-   **Registriert bei einer MDM-Lösung eines Drittanbieters:** Die Geräte in dieser Kategorie sind in der Regel unternehmenseigene Geräte.

    > [!NOTE]
    > Die Verwendung von App-Schutzrichtlinien mit der mobilen Anwendungsverwaltung von Drittanbietern oder sicheren Containerlösungen wird nicht empfohlen.

-   **Nicht bei einer MDM-Lösung registriert:** Die Geräte in dieser Kategorie sind in der Regel mitarbeitereigene Geräte, die weder bei Intune noch anderen MDM-Lösungen registriert sind oder dort verwaltet werden.

> [!IMPORTANT]
> Sie können App-Schutzrichtlinien für mobile Office-Apps erstellen, die eine Verbindung mit Office 365-Diensten herstellen. App-Schutzrichtlinien werden nicht für Apps unterstützt, die eine Verbindung mit Exchange lokal, Skype for Business oder SharePoint-Diensten herstellen.

## <a name="benefits-of-using-app-protection-policies"></a>Vorteile der Verwendung von App-Schutzrichtlinien

-   **Sie erleichtern den Schutz Ihrer Unternehmensdaten auf App-Ebene.** Da die Verwaltung von mobilen Anwendungen keine Geräteverwaltung voraussetzt, können Sie Unternehmensdaten auf verwalteten und auf unverwalteten Geräten schützen. Bei der Verwaltung wird die Benutzeridentität in den Mittelpunkt gestellt, wodurch sich die Geräteverwaltung erübrigt.

-   **Die Produktivität der Benutzer wird nicht beeinträchtigt, und die Richtlinien werden nicht angewendet, wenn Sie die App im privaten Kontext verwenden.** Die Richtlinien werden nur auf den beruflichen Kontext angewendet, wodurch Sie die Möglichkeit haben, Unternehmensdaten zu schützen, ohne dass private Daten einbezogen werden.

Es gibt weitere Vorteile bei der Verwendung einer MDM mit App-Schutzrichtlinien, und Unternehmen können MAM gleichzeitig mit und ohne MDM verwenden. So kann ein Mitarbeiter beispielsweise ein unternehmenseigenes Smartphone und ein privates Tablet verwenden. In diesem Fall wird das unternehmenseigene Smartphone in einer MDM registriert und von App-Schutzrichtlinien geschützt, während das private Geräte nur mit App-Schutzrichtlinien geschützt wird.

- **Eine MDM-Lösung stellt sicher, dass das Gerät geschützt ist.** So können Sie beispielsweise die Eingabe einer PIN für den Zugriff auf das Gerät anfordern, oder Sie können verwaltete Apps auf dem Gerät bereitstellen. Sie können Apps auch über die MDM-Lösung auf Geräten bereitstellen, um mehr Kontrolle über die App-Verwaltung zu haben.

- **App-Schutzrichtlinien stellen sicher, dass Schutzfunktionen auf App-Ebene vorhanden sind**. So können Sie beispielsweise über eine Richtlinie verfügen, die eine PIN anfordert, wenn eine App im beruflichen Kontext geöffnet werden soll, und verhindert, dass Daten zwischen Apps ausgetauscht werden oder dass App-Daten des Unternehmens an einem privaten Speicherort gespeichert werden.

## <a name="devices-that-support-mam"></a>Geräte, die MAM unterstützen
Die Plattform für Schutzrichtlinien für Intune-Apps ist auf die Plattformunterstützung für Office-Anwendungen ausgerichtet. Weitere Informationen finden Sie unter [Systemanforderungen für Office](https://products.office.com/en-US/office-system-requirements).

>[!NOTE]
>Windows-Geräte werden in der MAM nicht ohne Registrierungsszenario unterstützt. Wenn Sie jedoch Windows 10-Geräte mit Intune registrieren, können Sie Windows Information Protection verwenden, das ähnliche Funktionen bietet. Weitere Informationen finden Sie unter [Schutz von Unternehmensdaten mit Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).


##  <a name="how-app-protection-policies-protect-app-data"></a>So schützen App-Schutzrichtlinien Ihre App-Daten

###  <a name="apps-without-app-protection-policies"></a>Apps ohne App-Schutzrichtlinien

![Die Abbildung zeigt, wie Daten ungehindert zwischen Apps verschoben werden können, wenn keine App-Schutzrichtlinien angewendet werden.](../media/Apps_without_MAM_policies.png)

Wenn Sie Apps ohne Einschränkungen verwenden, können Unternehmensdaten und private Daten vermischt werden. Unternehmensdaten könnten damit an Speicherorten wie dem persönlichen Speicher abgelegt oder an Apps außerhalb Ihres Zuständigkeitsbereichs übermittelt werden, was zu Datenverlusten führen könnte. Die Pfeile im Diagramm zeigen die uneingeschränkte Datenbewegung zwischen Apps (geschäftlich und privat) und zu Speicherorten.

### <a name="data-protection-with-app-protection-policies"></a>Datenschutz mit App-Schutzrichtlinien

![Das Bild zeigt, wie Unternehmensdaten durch die Anwendung von App-Schutzrichtlinien geschützt werden](../media/Apps_with_mobile_app_policies.png)

Mit App-Schutzrichtlinien können Sie verhindern, dass Unternehmensdaten im lokalen Speicher des Geräts gespeichert werden. Außerdem können Sie das Verschieben von Daten in andere Apps einschränken, die nicht durch App-Schutzrichtlinien geschützt sind. Einstellungen für App-Schutzrichtlinien:
- Richtlinien zur Datenverschiebung wie **„Speichern unter“ verhindern**und **Ausschneiden, Kopieren und Einfügen einschränken**.
- Einstellungen von Zugriffsrichtlinien wie **Einfache PIN für den Zugriff erforderlich** und **Ausführen verwalteter Apps auf mit Jailbreak oder Rooting manipulierten Geräten blockieren**.

### <a name="data-protection-with-app-protection-on-devices-that-are-managed-by-a-mdm-solution"></a>Schutz von Daten mit App-Schutzrichtlinien auf Geräten, die durch eine MDM-Lösung verwaltet werden

![Das Bild zeigt, wie App-Schutzrichtlinien auf BYOD-Geräten (Bring Your Own Devices) funktionieren](../media/MAM_BYOD_November.png)

**Für Geräte, die in einer MDM-Lösung registriert sind**: Das Diagramm oben zeigt die Schutzebenen, die MDM-Richtlinien und App-Schutzichtlinien zusammen bieten.

Die MDM-Lösung:

-   Registriert das Gerät.

-   Stellt Apps auf dem Gerät bereit.

-   Sorgt für kontinuierliche Gerätekompatibilität und -verwaltung.

**App-Schutzrichtlinien bieten Mehrwert wegen folgender Gründe:**

-   Sie tragen zum Schutz der Unternehmensdaten bei, indem der Zugriff durch Verbraucher-Apps und -Dienste verhindert wird.

-   Es werden Einschränkungen („Speichern unter“, Zwischenablage, PIN usw.) auf mobile Apps angewendet.

-   Unternehmensdaten können aus Apps entfernt werden, ohne die Apps vom Gerät zu löschen.


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Schutz von Daten mit App-Schutzrichtlinien für Geräte ohne Registrierung

![Das Bild zeigt, wie App-Schutzrichtlinien auf verwalteten Geräten funktionieren](../media/MAM_ManagedDevices_November.png)

Das voranstehende Diagramm zeigt, wie Datenschutzrichtlinien auf App-Ebene ohne MDM funktionieren.

Bei BYOD-Geräten, die nicht in einer MDM-Lösung registriert sind, können App-Schutzrichtlinien dazu beitragen, Unternehmensdaten auf App-Ebene zu schützen.

Es gibt jedoch einige Einschränkungen, die Sie kennen sollten:

-   Sie können auf dem Gerät keine Apps bereitstellen. Der Benutzer muss die Apps aus dem Store beziehen.

-   Sie können auf diesen Geräten keine Zertifikatprofile bereitstellen.

-   Sie können auf diesen Geräten keine unternehmensweiten WLAN- und VPN-Einstellungen einrichten.


## <a name="multi-identity"></a>Mehrere Identitäten

Apps, die mehrere Identitäten unterstützen, bieten Ihnen die Möglichkeit, verschiedene Konten (Geschäfts- und persönliche Konten) für den Zugriff auf die gleichen Apps zu verwenden. Hierbei werden App-Schutzrichtlinien nur angewendet, wenn die Apps im Arbeitskontext verwendet werden.  

Wenn ein Benutzer beispielsweise die OneDrive-App mit seinem Geschäftskonto startet, kann er die Dateien nicht an einen persönlichen Speicherort verschieben. Wenn der Benutzer OneDrive jedoch mit einem persönlichen Konto verwendet, kann er Daten ohne Einschränkung aus dem persönlichen OneDrive kopieren und verschieben.  

- Erfahren Sie mehr über die Apps, die [die Verwaltung mobiler Anwendungen und mehrerer Identitäten](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) mit Intune unterstützen.

##  <a name="next-steps"></a>Nächste Schritte
- [Vorbereitungen zum Konfigurieren von App-Schutzrichtlinien](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

- [Erstellen und Bereitstellen von App-Schutzrichtlinien mit Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)
