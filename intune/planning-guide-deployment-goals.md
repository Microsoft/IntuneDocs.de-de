---
title: Bestimmen der Bereitstellungsziele, sonstigen Ziele und Herausforderungen
titlesuffix: Microsoft Intune
description: "Dieser Artikel hilft Ihnen beim Bestimmen von langfristigen und kurzfristigen Zielen sowie von Herausforderungen bei der Intune-Bereitstellung für eine reine Microsoft Intune-Cloudimplementierung."
keywords: 
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 24cf9d97-db39-4b95-a664-4aa2e33edb87
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f76e227037efd6ea8ee7ea95d61f3358698af1d9
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
---
# <a name="determine-deployment-goals-objectives-and-challenges"></a>Bestimmen der Bereitstellungsziele, sonstigen Ziele und Herausforderungen

Ein guter Bereitstellungsplan beginnt mit dem Ermitteln der langfristigen und kurzfristigen Ziele der Bereitstellung sowie von möglichen Herausforderungen für Ihre Organisation. Betrachten wir die einzelnen Bereiche im Detail.

## <a name="deployment-goals"></a>Langfristige Bereitstellungsziele

Bereitstellungsziele sind langfristig angelegt und sollen durch das Bereitstellen von Intune in Ihrer Organisation realisiert werden. Nachstehend finden Sie einige Beispiele solcher Ziele, jeweils mit Beschreibung und geschäftlichem Nutzen.

-   **Integration in Office 365 und Unterstützung der Verwendung von Office Mobile-Apps**

    -   **Beschreibung:** Bereitstellen einer engen Integration in Office 365 und Verwendung von Office Mobile-Apps mit App-Schutz.

    -   **Geschäftlicher Nutzen:** Sichere und verbesserte Benutzeroberfläche, da Benutzer Apps verwenden können, die sie kennen und bevorzugen.

-   **Aktivieren des Zugriffs auf interne Unternehmensdienste auf mobilen Geräten**

    -   **Beschreibung:** Mitarbeitern an jedem beliebigen Ort und mit dem jeweils geeigneten Gerät Produktivität ermöglichen. Dieses Projekt sollte darauf ausgerichtet sein, mobile Produktivität und Zugriff auf Unternehmensdaten auf sichere Weise zu ermöglichen.

    -   **Geschäftlicher Nutzen:** Indem Mitarbeitern die Flexibilität eingeräumt wird, an jedem beliebigen Standort zu arbeiten, ist das Unternehmen konkurrenzfähiger und kann eine interessante Arbeitsumgebung bieten.

-   **Bereitstellen von Datenschutz auf mobilen Geräten**

    -   **Beschreibung:** Wenn Daten auf einem mobilen Gerät gespeichert sind, müssen sie vor böswilligem und unbeabsichtigtem Datenverlust oder vor Freigabe geschützt werden.

    -   **Geschäftlicher Nutzen:** Datenschutz ist wichtig, um sicherzustellen, dass wir wettbewerbsfähig bleiben und unsere Kunden und deren Daten mit den größtmöglichen Sorgfalt behandeln.

-   **Kostensenkung**

    -   **Beschreibung:** Nach Möglichkeit werden durch das Projekt die Kosten für Bereitstellung und Betrieb verringert.

    -    **Geschäftlicher Nutzen:** Durch die effiziente Verwendung von Ressourcen kann das Unternehmen in andere Bereiche investieren, wirksamer konkurrieren und den Kunden einen besseren Service bieten.

## <a name="deployment-objectives"></a>Kurzfristige Bereitstellungsziele

Diese Ziele der Bereitstellung sind die Aktionen, mit denen Ihr Unternehmen seine langfristigen Ziele der Intune-Bereitstellungsziele umsetzen kann. Im Folgenden sind einige Beispiele für kurzfristige Bereitstellungsziele aufgeführt. Zudem wird erläutert, wie sie jeweils zu erreichen sind.

-   **Verringern der Anzahl von Geräteverwaltungslösungen**

    -   **Umsetzung:** Konsolidieren Sie auf eine einzige Lösung zur Verwaltung mobiler Geräte, nämlich Microsoft Intune, für den Schutz von Unternehmensdaten von Apps und Geräten.

-   **Bereitstellen eines sicheren Zugriffs auf Exchange Online und SharePoint Online**

    -   **Umsetzung:** Implementieren Sie den bedingten Zugriff für Exchange Online und SharePoint Online.

-   **Verhindern, dass Unternehmensdaten gespeichert oder an unternehmensfremde Dienste auf dem mobilen Gerät weitergeleitet werden**

    -   **Umsetzung:** Implementieren Sie Intune-Richtlinien zum App-Schutz für Microsoft Office- und branchenspezifische Apps.

-   **Bereitstellen der Funktion zum Entfernen von Unternehmensdaten vom Gerät**

    -   **Umsetzung:** Registrieren Sie Geräte bei Intune. Dies bietet Ihnen die Möglichkeit, bei Bedarf eine Remotezurücksetzung von Unternehmensdaten und -ressourcen vorzunehmen.

## <a name="deployment-challenges"></a>Herausforderungen bei der Bereitstellung

Herausforderungen bei der Bereitstellung sind Aspekte, die bei einer Organisation im Vordergrund stehen und sich negativ auf die Bereitstellung auswirken können. Mitunter stehen sie in Zusammenhang mit bei früheren Projekten aufgetretenen Problemen, die vermieden werden sollen, oder es handelt sich um neue Probleme bei den aktuellen Bereitstellungsbemühungen. Nachstehend sind einige Beispiele für die Herausforderungen bei der Bereitstellung von Intune sowie mögliche Gegenmaßnahmen aufgeführt.

-   Die Bereitschaft des Supports und Endbenutzerfahrung werden im anfänglichen Projektumfang nicht berücksichtigt. Dies führt zu einer schwachen Akzeptanz seitens der Endbenutzer und Herausforderungen für Ihre Supportorganisation.

    -   **Lösung:** Integrieren Sie Schulungen für den Support. Überprüfen Sie die Endbenutzererfahrung anhand der Erfolgsmetriken in Ihrem Bereitstellungsplan.

-   Das Fehlen klar definierter Ziele und Erfolgsmetriken führt zu vagen Ergebnissen. Es kann auch bewirken, dass Ihre Organisation in den Reaktionsmodus wechselt, sobald Probleme auftreten.

    -   **Lösung:** Definieren Sie Ihre Ziele und Erfolgsmetriken frühzeitig in Ihrem Projektumfang, und verwenden Sie diese Datenpunkte zur Ausarbeitung der übrigen Rolloutphasen. Stellen Sie sicher, dass Ihre Ziele spezifisch, messbar, erreichbar, realistisch und zeitgerecht sind. Planen Sie in allen Phasen Vergleichsmessungen mit Ihren Zielen ein, um sicherzustellen, dass Ihr Rolloutprojekt auf Kurs bleibt.

-   Sie vernachlässigen das Erstellen, Überprüfen und proaktive Vermitteln eines deutlichen Nutzenversprechens für Ihre Organisation. Dies führt häufig zu begrenzter Akzeptanz und einem Mangel an Rendite.

    -   **Lösung:** Auch wenn Sie sich gerne sofort in Ihr Projekt stürzen möchten, stellen Sie zuerst sicher, dass Sie Ihre langfristigen und kurzfristigen Ziele eindeutig definieren. Beziehen Sie diese in alle Sensibilisierungs- und Trainingsaktivitäten ein, um sicherzustellen, dass den Benutzern klar ist, warum das Unternehmen sich für Intune entschieden hat.

## <a name="next-steps"></a>Nächste Schritte

Sie haben Ihre langfristigen und kurzfristigen Ziele sowie die möglichen Herausforderungen Ihrer Bereitstellung identifiziert. Fahren Sie nun mit dem nächsten Abschnitt fort: [Identifizieren von Anwendungsszenarien](planning-guide-scenarios.md).
