---
title: Bedingter Zugriff mit Microsoft Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie die Bedingungen definieren, die Benutzer, Geräte und Apps erfüllen müssen, um Zugriff auf Unternehmensressourcen in Microsoft Intune zu erhalten.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: cef8bcf74509d83b076b30a1ee7f2406e622b129
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722643"
---
# <a name="learn-about-conditional-access-and-intune"></a>Erfahren Sie mehr zum bedingten Zugriff und Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Der Begriff „bedingter Zugriff“ bezieht sich auf Möglichkeiten zum Steuern der Geräte und Apps, die eine Verbindung mit E-Mail- und Unternehmensressourcen herstellen dürfen. In diesem Artikel erhalten Sie Informationen zu gerätebasiertem und App-basiertem bedingtem Zugriff. Außerdem werden häufige Szenarios zur Verwendung von bedingtem Zugriff mit Intune dargestellt.

Der bedingte Zugriff von Enterprise Mobility + Security (EMS) ist kein eigenständiges Produkt, sondern eine Lösung, die für alle Dienste und Produkte im Rahmen von EMS gilt. Die Lösung bietet eine präzise Zugriffssteuerung, sodass Sie die Sicherheit Ihrer Unternehmensdaten gewährleisten und gleichzeitig dafür sorgen können, dass die Benutzer mit jedem Gerät und an jedem Standort optimal arbeiten können.

Sie können Bedingungen definieren, die den Zugriff auf Ihre Unternehmensdaten basierend auf dem Ort, dem Gerät, dem Benutzerstatus und der Vertraulichkeit der Anwendung einschränken.

> [!NOTE] 
> Der bedingte Zugriff kann auch auf [Office 365-Dienste](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access) angewendet werden.

![Architekturdiagramm für den bedingten Zugriff](./media/conditional-access/ca-diagram-1.png)

## <a name="use-conditional-access-with-intune"></a>Verwenden des bedingten Zugriffs mit Intune

Bei bedingtem Zugriff handelt es sich um eine Azure Active Directory-Funktion, die in einer Azure Active Directory Premium-Lizenz enthalten ist. Intune erweitert diese Funktion, indem es der Lösung Konformität der mobilen Geräte und Mobile App-Verwaltung hinzufügt. 

![Intune und der bedingte Zugriff bei Verwendung von EMS](./media/conditional-access/intune-with-ca-1.png)

Möglichkeiten der Verwendung des bedingten Zugriffs in Intune:

- **Gerätebasierter bedingter Zugriff**

  - Bedingter Zugriff für Exchange lokal

  - Bedingter Zugriff basierend auf der Netzwerkzugriffssteuerung

  - Bedingter Zugriff basierend auf dem Geräterisiko

  - Bedingter Zugriff für Windows-PCs

    - Unternehmenseigene Geräte

    - Bring Your Own Device (BYOD)

- **App-basierter bedingter Zugriff**

## <a name="next-steps"></a>Nächste Schritte

[Gängige Möglichkeiten für die Verwendung des bedingten Zugriffs mit Intune](conditional-access-intune-common-ways-use.md)
