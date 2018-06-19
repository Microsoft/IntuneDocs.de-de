---
title: Gerätekompatibilitätsrichtlinien
description: In diesem Thema wird erläutert, was Gerätekonformitätsrichtlinien sind und wie sie funktionieren.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4c9c93d29ddee6d01e057c01a44c81950b857213
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31031752"
---
# <a name="device-compliance-policies-in-microsoft-intune"></a>Gerätekompatibilitätsrichtlinien in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="what-is-a-compliance-policy"></a>Was ist eine Konformitätsrichtlinie?
Um Unternehmensdaten zu schützen, müssen Sie sicherstellen, dass die Geräte, die für den Zugriff auf Unternehmens-Apps und Daten verwendet werden, bestimmten Regeln entsprechen. Diese Regeln könnten die Verwendung einer PIN für den Zugriff auf Geräte und das Verschlüsseln von Daten, die auf Geräten gespeichert sind, einschließen. Eine Gruppe solcher Regeln wird als Kompatibilitätsrichtlinie bezeichnet.

## <a name="how-should-i-use-compliance-policies"></a>Wie verwende ich Konformitätsrichtlinien?
Sie können Kompatibilitätsrichtlinien mit Richtlinien für bedingten Zugriff verwenden, um nur Geräte zuzulassen, die Kompatibilitätsrichtlinienregeln für den Zugriff auf E-Mail und andere Dienste entsprechen. Wie die beiden Richtlinien zusammen verwendet werden können, erfahren Sie im Artikel [Einschränken des Zugriffs auf E-Mail- und Office 365-Dienste](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

Sie können Konformitätsrichtlinien auch unabhängig vom bedingten Zugriff nutzen. Bei unabhängiger Nutzung von Kompatibilitätsrichtlinien werden die Zielgeräte ausgewertet und mit ihrem Kompatibilitätsstatus gemeldet. Sie können beispielsweise einen Bericht dazu erstellen, wie viele Geräte nicht verschlüsselt sind oder per Jailbreak oder Rootzugriff manipuliert wurden. Aber wenn Sie Kompatibilitätsrichtlinien unabhängig nutzen, gelten keine Zugriffsbeschränkungen für Unternehmensressourcen.

Sie stellen Konformitätsrichtlinien für Benutzer bereit. Wenn Sie eine Kompatibilitätsrichtlinie für einen Benutzer bereitstellen, wird die Kompatibilität der Geräte des Benutzers überprüft.
Informationen darüber, wie lange es dauert, bis eine Richtlinie für mobile Geräte nach der Bereitstellung der Richtlinie abgerufen wird, finden Sie unter [Verwalten von Einstellungen und Features auf Ihren Geräten](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#frequently-asked-questions-about-intune-policies).

Die folgende Tabelle enthält die Gerätetypen, die Kompatibilitätsrichtlinien unterstützen. In der Tabelle wird auch beschrieben, wie nicht kompatible Einstellungen verwaltet werden, wenn eine Kompatibilitätsrichtlinie mit einer Richtlinie für bedingten Zugriff verwendet wird.

-----------------------------

|Richtlinieneinstellung| Windows 8.1 und höher| Windows Phone 8.1 und höher| iOS 8.0 und höher|Android 4,0 und höher<br/>Samsung Knox Standard 4.0 und höher|
|-----|----|----|----|----|
|**PIN- oder Kennwortkonfiguration** |Wiederhergestellt|Wiederhergestellt|Wiederhergestellt|Isoliert|
|**Geräteverschlüsselung**|Nicht verfügbar|Wiederhergestellt|Wiederhergestellt (durch Festlegen der PIN)|Isoliert|
|**Per Jailbreak oder Rootzugriff manipuliertes Gerät**|Nicht verfügbar|Nicht verfügbar|Unter Quarantäne gestellt (keine Einstellung)|Unter Quarantäne gestellt (keine Einstellung)|
|**E-Mail-Profil**|Nicht verfügbar|Nicht verfügbar|Isoliert|Nicht verfügbar|
|**Minimale Version des Betriebssystems**|Isoliert|Isoliert|Isoliert|Isoliert|
|**Maximale Version des Betriebssystems**|Isoliert|Isoliert|Isoliert|Isoliert|
|**Windows-Integritätsnachweis**|Isoliert: Windows 10 und Windows 10 Mobile<br /><br />Nicht verfügbar: Windows 8.1|Nicht verfügbar|Nicht verfügbar|Nicht verfügbar|

------------------------------

**Wiederhergestellt** = Das Betriebssystem des Geräts erzwingt die Kompatibilität. (Beispiel: Der Benutzer ist gezwungen, eine PIN festzulegen.)

**Isoliert** = Das Betriebssystem des Geräts erzwingt keine Kompatibilität. (Beispiel: Android-Geräte zwingen den Benutzer nicht, das Gerät zu verschlüsseln.) Wenn die Geräte nicht kompatibel sind, erfolgen die folgenden Aktionen:

-   Das Gerät wird blockiert, wenn eine Richtlinie für bedingten Zugriff für den Benutzer gilt.

-   Das Unternehmensportal benachrichtigt den Benutzer über Kompatibilitätsprobleme.

## <a name="next-steps"></a>Nächste Schritte
[Erstellen einer Gerätekompatibilitätsrichtlinie](create-a-device-compliance-policy-in-microsoft-intune.md)

[Bereitstellen und Überwachen einer Kompatibilitätsrichtlinie für Geräte](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>Siehe auch
[Beschränken des Zugriffs auf E-Mail- und Office 365-Dienste](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
