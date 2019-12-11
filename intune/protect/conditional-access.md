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
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 179d135ee8e216495cd7435bf38d8087e5c990e8
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74188276"
---
# <a name="learn-about-conditional-access-and-intune"></a>Erfahren Sie mehr zum bedingten Zugriff und Intune

Mit bedingtem Zugriff können Sie die Geräte und Anwendungen steuern, die sich mit Ihren E-Mail- und Unternehmensressourcen verbinden können. 

Enterprise Mobility + Security (EMS) ist kein eigenständiges Produkt. Dabei handelt es sich um eine Lösung, die an allen Diensten und Produkten beteiligt ist, die Teil von EMS sind. Bedingter Zugriff bietet eine präzise Zugriffssteuerung, sodass Sie die Sicherheit Ihrer Unternehmensdaten gewährleisten und gleichzeitig dafür sorgen können, dass die Benutzer mit jedem Gerät und an jedem Standort optimal arbeiten können.

Sie können Bedingungen definieren, die den Zugriff auf Ihre Unternehmensdaten basierend auf dem Ort, dem Gerät, dem Benutzerstatus und der Vertraulichkeit der Anwendung einschränken.

> [!NOTE]
> Der bedingte Zugriff kann auch auf [Office 365-Dienste](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access) angewendet werden.

![Diagramm des bedingten Zugriffs](./media/conditional-access/ca-diagram-1.png)

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
