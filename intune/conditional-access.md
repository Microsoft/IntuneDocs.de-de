---
title: Bedingter Zugriff mit Microsoft Intune
titlesuffix: ''
description: Erfahren Sie, wie Sie die Bedingungen definieren, die Benutzer, Geräte und Apps erfüllen müssen, um Zugriff auf Unternehmensressourcen in Microsoft Intune zu erhalten.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 9ce2433213805b201a968740976b41de2970a62c
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231226"
---
# <a name="whats-conditional-access"></a>Was ist bedingter Zugriff?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Der Begriff „bedingter Zugriff“ bezieht sich auf Möglichkeiten zum Steuern der Geräte und Apps, die eine Verbindung mit E-Mail- und Unternehmensressourcen herstellen dürfen. In diesem Artikel erhalten Sie Informationen zu gerätebasiertem und App-basiertem bedingtem Zugriff. Außerdem werden häufige Szenarios zur Verwendung von bedingtem Zugriff mit Intune dargestellt.

Der bedingte Zugriff von Enterprise Mobility + Security (EMS) ist kein eigenständiges Produkt, sondern eine Lösung, die für alle Dienste und Produkte im Rahmen von EMS gilt. Die Lösung bietet eine präzise Zugriffssteuerung, sodass Sie die Sicherheit Ihrer Unternehmensdaten gewährleisten und gleichzeitig dafür sorgen können, dass die Benutzer mit jedem Gerät und an jedem Standort optimal arbeiten können.

Sie können Bedingungen definieren, die den Zugriff auf Ihre Unternehmensdaten basierend auf dem Ort, dem Gerät, dem Benutzerstatus und der Vertraulichkeit der Anwendung einschränken.

> [!NOTE] 
> Der bedingte Zugriff kann auch auf [Office 365-Dienste](https://blogs.technet.microsoft.com/wbaer/2017/02/17/conditional-access-policies-with-sharepoint-online-and-onedrive-for-business/) angewendet werden.

![Architekturdiagramm für den bedingten Zugriff](./media/ca-diagram-1.png)

## <a name="conditional-access-with-intune"></a>Bedingter Zugriff über Intune

Bei bedingtem Zugriff handelt es sich um eine Azure Active Directory-Funktion, die in einer Azure Active Directory Premium-Lizenz enthalten ist. Intune erweitert diese Funktion, indem es der Lösung Konformität der mobilen Geräte und Mobile App-Verwaltung hinzufügt. 

![Intune und der bedingte Zugriff bei Verwendung von EMS](./media/intune-with-ca-1.png)

Möglichkeiten der Verwendung des bedingten Zugriffs in Intune:

-   **Gerätebasierter bedingter Zugriff**

    -   Bedingter Zugriff für Exchange lokal

    -   Bedingter Zugriff basierend auf der Netzwerkzugriffssteuerung

    -   Bedingter Zugriff basierend auf dem Geräterisiko

    -   Bedingter Zugriff für Windows-PCs

        -   Unternehmenseigene Geräte

        -   Bring Your Own Device (BYOD)

-   **App-basierter bedingter Zugriff**

## <a name="next-steps"></a>Nächste Schritte

[Gängige Möglichkeiten der Verwendung des bedingten Zugriffs in Intune](conditional-access-intune-common-ways-use.md)
