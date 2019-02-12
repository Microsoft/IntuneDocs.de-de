---
title: Wie Ihre iOS-Benutzer Apps erhalten
description: Methoden, um iOS-Apps für Endbenutzer verfügbar zu machen.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/28/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 52adb8b21189e4c0cf39f1b18f95b7ba68ff97f4
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55833734"
---
# <a name="how-your-ios-users-get-their-apps"></a>Wie Ihre iOS-Benutzer Apps erhalten

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Verwenden Sie diese Informationen, um zu verstehen, wie und wo Ihre Endbenutzer die Apps erhalten, die Sie über Microsoft Intune verteilen.

**Erforderliche Apps:** Apps, die vom Administrator benötigt werden und auf dem Gerät (abhängig von der Plattform) mit minimalen Benutzereingriffen installiert werden.

**Verfügbare Apps:** Apps, die in der App-Liste im Unternehmensportal enthalten sind und die ein Benutzer optional installieren kann.

**Verwaltete Apps:** Apps, die mittels Richtlinien verwaltet werden können und die von Intune „umschlossen“ werden oder mit dem Software Development Kit (SDK) für die Intune-App erstellt wurden. Diese Apps können von Intune verwaltet werden, und ihnen lassen sich App-Schutzrichtlinien zuweisen.

**Nicht verwaltete Apps**: Apps, die mittels Richtlinien verwaltet werden können und die nicht von Intune umschlossen wurden oder nicht in das Intune SDK integriert sind. Diesen Apps lassen sich keine Anwendungsrichtlinien zuweisen.

Einschränkungen seitens Apple verbieten die Auflistung von branchenspezifischen und verwalteten Apps aus dem App Store in der Unternehmensportal-App. Um dieses Problem zu umgehen, verweisen die Kacheln in der Unternehmensportal-App für iOS die Benutzer für alle ihre Apps auf verschiedene Ansichten an einem einzigen Speicherort (der Unternehmensportal-Website).

Registrierte Benutzer erhalten ihre Apps durch Berühren der folgenden Kacheln auf dem Bildschirm „Apps“ der Unternehmensportal-App:

- **Alle Apps** verweist auf eine Liste aller Apps auf der Registerkarte „ALLE“ der [Unternehmensportal-Website](https://portal.manage.microsoft.com).

- **Ausgewählte Apps** leitet Benutzer zur Registerkarte „EMPFOHLEN“ der Unternehmensportal-Website.

- **Kategorien** verweist auf die Registerkarte „KATEGORIEN“ der Unternehmensportal-Website.


![Apps-Bildschirm des iOS-Unternehmensportals](./media/ios-cp-app-main-apps-screen.png)

Informationen zum Hinzufügen von Apps finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md).

### <a name="see-also"></a>Siehe auch
[Wie Ihre Android-Benutzer Apps erhalten](end-user-apps-android.md)

[Wie Ihre Windows-Benutzer Apps erhalten](end-user-apps-windows.md)
