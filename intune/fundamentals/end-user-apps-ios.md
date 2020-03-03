---
title: Wie Ihre iOS/iPadOS-Benutzer Apps erhalten
description: Methoden, um iOS/iPadOS-Apps für Endbenutzer verfügbar zu machen.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 344c2e3f3ed53852aa6b749c9ebf6d451dd313ff
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514386"
---
# <a name="how-your-iosipados-users-get-their-apps"></a>Wie Ihre iOS/iPadOS-Benutzer Apps erhalten

Verwenden Sie diese Informationen, um zu verstehen, wie und wo Ihre Endbenutzer die Apps erhalten, die Sie über Microsoft Intune verteilen.

**Erforderliche Apps:** Apps, die vom Administrator benötigt werden und auf dem Gerät (abhängig von der Plattform) mit minimalen Benutzereingriffen installiert werden.

**Verfügbare Apps:** Apps, die in der App-Liste im Unternehmensportal enthalten sind und die ein Benutzer optional installieren kann.

**Verwaltete Apps:** Apps, die mittels Richtlinien verwaltet werden können und die von Intune „umschlossen“ werden oder mit dem Software Development Kit (SDK) für die Intune-App erstellt wurden. Diese Apps können von Intune verwaltet werden, und ihnen lassen sich App-Schutzrichtlinien zuweisen.

**Nicht verwaltete Apps:** Apps, die Benutzer aus dem iOS/iPadOS App Store herunterladen können und die nicht in das Intune App SDK integriert sind. Intune bietet keinerlei Kontrolle über die Verteilung, Verwaltung oder selektive Löschvorgänge dieser Apps.  

Einschränkungen seitens Apple verbieten die Auflistung von branchenspezifischen und verwalteten Apps aus dem App Store in der Unternehmensportal-App. Die Kacheln in der Unternehmensportal-App für iOS/iPadOS verweisen die Benutzer für alle ihre Apps auf verschiedene Ansichten an einem einzigen Speicherort (der Unternehmensportal-Website), um dieses Problem zu umgehen.

Registrierte Benutzer erhalten ihre Apps durch Berühren der folgenden Kacheln auf dem Bildschirm „Apps“ der Unternehmensportal-App:

- **Alle Apps** verweist auf eine Liste aller Apps auf der Registerkarte „ALLE“ der [Unternehmensportal-Website](https://portal.manage.microsoft.com).

- **Ausgewählte Apps** leitet Benutzer zur Registerkarte „EMPFOHLEN“ der Unternehmensportal-Website.

- **Kategorien** verweist auf die Registerkarte „KATEGORIEN“ der Unternehmensportal-Website.

![Apps-Bildschirm des iOS-Unternehmensportals](./media/end-user-apps-ios/ios-cp-app-main-apps-screen.png)

Informationen zum Hinzufügen von Apps finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](../apps/apps-add.md).

## <a name="see-also"></a>Weitere Informationen:

[Wie Ihre Android-Benutzer Apps erhalten](end-user-apps-android.md)

[Wie Ihre Windows-Benutzer Apps erhalten](end-user-apps-windows.md)
