---
title: Auflösen von Einschränkungen eines Zugriffspunkts in Intune
description: Erfahren Sie mehr über die drei häufigsten Meldungen bezüglich Intune-Einschränkungsrichtlinien für Zugriffspunkte und wie Sie diese beheben können.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: eeb47c072a4f34098bdebfd8766ab51b941d0bd3
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75858097"
---
# <a name="resolve-access-point-restrictions"></a>Auflösen von Einschränkungen eines Zugriffspunkts

Organisationen können die Standorte einschränken, von denen Geräte auf Unternehmensdaten zugreifen können.
Sie legen genehmigte Netzwerkstandorte fest, um diese *Zugriffspunkteinschränkungen* zu konfigurieren.  

Wenn Sie versuchen, eine Verbindung mit einem nicht genehmigten oder unbekannten Netzwerk herzustellen, erhalten Sie möglicherweise mindestens eine der folgenden Meldungen:

* Access point restrictions are not set up. (Es wurden keine Zugriffspunkteinschränkungen eingerichtet.)
* You are not connected to an approved network. (Sie sind nicht mit einem genehmigten Netzwerk verbunden.)
* An error occurred and the access point restrictions couldn't be enforced. (Ein Fehler ist aufgetreten. Die Zugriffspunkteinschränkungen konnten nicht erzwungen werden.)

 In den unten stehenden Tabellen werden die Meldungen mit den jeweiligen Bedeutungen und Maßnahmen aufgelistet, mit denen Sie wieder auf Ihre Arbeitsressourcen zugreifen können.

## <a name="access-point-restrictions-not-set-up"></a>Es wurden keine Zugriffspunkteinschränkungen eingerichtet.  
| Meldung im Unternehmensportal | Bedeutung der Meldung | Maßnahme                                                               
|------------------------|--------------------------|--------------------------|
| **Es wurden keine Zugriffspunkteinschränkungen eingerichtet. Zugriffspunkteinschränkungen sind aktiv und müssen eingerichtet werden.** | Ihr Unternehmen hat Zugriffspunkteinschränkungen auf Ihrem Gerät angewendet. Durch diese Einstellung muss die Unternehmensportal-App einige Netzwerkeinstellungen auf Ihrem Gerät überprüfen. | Tippen Sie auf **Resolve** (Beheben). Die Unternehmensportal-App überprüft, ob Sie mit einem vom Unternehmen genehmigten Netzwerk verbunden sind. |

## <a name="not-connected-to-an-approved-network"></a>Sie sind nicht mit einem genehmigten Netzwerk verbunden.  

| Meldung im Unternehmensportal | Bedeutung der Meldung | Maßnahme                                                                   
|------------------------|-----------------------------------|--------------------------|
| **Sie sind nicht mit einem genehmigten Netzwerk verbunden. Stellen Sie eine Verbindung mit einem genehmigten Funknetzwerk her.** | Sie sind mit einem Netzwerk verbunden, dass nicht für den Arbeitsplatzzugriff zugelassen ist. Solange Sie mit diesem Netzwerk verbunden sind, können Sie nicht auf Arbeits-E-Mails, -Apps und andere geschützte Unternehmensressourcen zugreifen. | Stellen Sie eine Verbindung mit einem von Ihrem Unternehmen genehmigten Netzwerk her. Tippen Sie dann auf **Beheben**, um es erneut zu versuchen. |

## <a name="restrictions-couldnt-be-enforced"></a>Einschränkungen konnten nicht erzwungen werden  

| Meldung im Unternehmensportal | Bedeutung der Meldung | Maßnahme                                                                      
|------------------------|-----------------------------------|--------------------------|
| **Die Zugriffspunkteinschränkungen konnten nicht erzwungen werden. Fehler im Unternehmensportal.** | Intune konnte nicht bestimmen, ob Sie mit einem genehmigten Netzwerk verbunden sind. Dieser Fehler kann wegen einer schlechten Netzwerkverbindung, wegen niedrigen Akkustands, Stromsparmodus oder einem Fehler im Unternehmensportal auftreten. | Stellen Sie sicher, dass Ihre Netzwerkverbindung stark genug ist. Deaktivieren Sie den Stromsparmodus, und achten Sie darauf, dass Ihr Akkustand mindestens 30 % beträgt. Tippen Sie dann auf **Beheben**, um es erneut zu versuchen. 

Benötigen Sie weitere Unterstützung? Es wird empfohlen, sich an die Supportabteilung Ihres Unternehmens zu wenden. Die genauen Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://portal.manage.microsoft.com/#HelpDeskDialog).
