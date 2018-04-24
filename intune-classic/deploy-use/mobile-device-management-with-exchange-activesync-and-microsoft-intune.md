---
title: Geräteverwaltung mit Exchange Active Sync
description: Verwalten mobiler Geräte mit der Exchange ActiveSync (EAS)-Verwaltung und dem Exchange Connector
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f5e9bd3dd2026096c323858fc7faa915895ed55d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="exchange-activesync-mobile-device-management-with-microsoft-intune"></a>Verwaltung mobiler Geräte mit Exchange ActiveSync und Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Damit mobile Geräte direkt mit Microsoft Intune verwaltet werden können, müssen sie [bei Intune registriert](prerequisites-for-enrollment.md) sein. Alternativ können Administratoren eine eingeschränktere Verwaltungslösung ermöglichen, bei der die Exchange ActiveSync-Verwaltung (EAS) mit einem Exchange Connector verwendet wird. Geräte können entweder mit lokalen Exchange-Servern oder mit Exchange Online unter Verwendung von Office 365 verwaltet werden. Intune unterstützt pro Abonnement nur eine Exchange Connector-Verbindung eines beliebigen Typs.

## <a name="exchange-access-rules-for-mobile-devices"></a>Exchange-Zugriffsregeln für mobile Geräte ##

In Exchange muss über einen Satz von Regeln definiert werden, was geschieht, wenn mobile Geräte eine Verbindung mit EAS herzustellen versuchen. Diese Regeln werden in der Intune-Verwaltungskonsole verwaltet.

[Exchange-Zugriffsregeln für mobile Geräte](exchange-access-rules-for-mobile-devices.md)

## <a name="install-the-exchange-connector"></a>Installieren des Exchange Connectors
Mit dem Exchange Connector können Sie Ihre Exchange-Bereitstellung in der Intune-Konsole verwalten. Zuerst müssen Sie den entsprechenden Intune-zu-Exchange-Connector installieren und einrichten. Wählen Sie die entsprechende Option je nachdem aus, ob es sich um einen lokalen Exchange-Server handelt oder ob er als Dienst in der Cloud gehostet wird:

-   [Konfigurieren von Intune für die Exchange Online-Umgebung oder für die neue Exchange Online Dedicated-Umgebung](intune-service-to-service-exchange-connector.md)
-   [Installieren des Intune-Connectors für lokale Exchange-Server und ältere Exchange Online Dedicated-Umgebungen](intune-on-premises-exchange-connector.md)


## <a name="apply-policy-for-exchange-managed-mobile-devices"></a>Anwenden der Richtlinie für mobile Geräte, die mit Exchange verwaltet werden
Die Intune-Konsole kann zum Verwalten von [EAS-Richtlinieneinstellungen](exchange-activesync-policy-settings-in-microsoft-intune.md) und zum [Beschränken des Zugriffs auf Unternehmensressourcen](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) verwendet werden. Eine Liste der Exchange ActiveSync-Richtlinieneinstellungen und -Funktionen, die von bestimmten mobilen Geräten unterstützt werden, finden Sie unter [Exchange ActiveSync Client Comparison Table (Vergleichstabelle der Exchange ActiveSync-Clients)](http://go.microsoft.com/fwlink/?LinkId=247270).

> [!NOTE]
> Nach dem Herstellen einer Verbindung zwischen Intune und einer Microsoft Exchange-Umgebung wird bei allen Benutzern, die über Intune verwaltet werden, die EAS-Richtlinie auf die aktuelle Standardrichtlinie auf dem Microsoft Exchange-Server zurückgesetzt, wenn keine spezifische Richtlinie in Intune definiert ist.

## <a name="wipe-company-data-from-mobile-devices"></a>Löschen von Unternehmensdaten von mobilen Geräten
Sie können [Unternehmensdaten von mobilen Geräten, die über EAS verwaltet werden, löschen](wipe-for-exchange-managed-mobile-devices.md), wenn diese nicht mehr verwendet werden oder wenn Geräte verloren gehen oder gestohlen werden.
