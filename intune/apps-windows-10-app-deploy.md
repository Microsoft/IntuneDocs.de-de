---
title: Windows 10-App-Bereitstellung mit Microsoft Intune
titlesuffix: ''
description: In diesem Artikel lernen Sie die Windows 10-App-Szenarios kennen, die für Microsoft Intune verfügbar sind.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7508f2c2eca06ceacf203103ab2cad53abc39a65
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347431"
---
# <a name="windows-10-app-deployment-using-microsoft-intune"></a>Windows 10-App-Bereitstellung mit Microsoft Intune 

Microsoft Intune unterstützt auf Windows 10-Geräten derzeit verschiedene App-Typen und Bereitstellungsszenarios. Nachdem Sie Intune eine App hinzugefügt haben, können Sie diese Benutzern und Geräten zuweisen. In diesem Artikel erfahren Sie mehr zu den unterstützten Windows 10-Szenarios und wichtige Details, die Sie beim Bereitstellen von Apps unter Windows beachten sollten. 

Branchenspezifische Apps und Apps aus dem Microsoft Store für Unternehmen werden auf Windows 10-Geräten unterstützt.

> [!Note]
> Das zum Bereitstellen von Apps im Gerätekontext erforderliche Mindestupdate für Windows 10 ist das vom [23. Mai 2018 – KB4100403 (Betriebssystembuild 17134.81)](https://support.microsoft.com/en-us/help/4100403/windows-10-update-kb4100403).

## <a name="windows-10-line-of-business-apps"></a>Branchenspezifische Apps für Windows 10

Branchenspezifische Windows 10-Apps sind signiert und werden in die Intune-Verwaltungskonsole hochgeladen. Bei diesen Apps kann es sich sowohl um moderne Apps, z.B. UWP-Apps (Universelle Windows-Plattform) und Windows-App-Pakete (AppX), als auch um Win32-Apps handeln, z.B. einfache Microsoft Installer-Paketdateien (MSI). Updates für Branchenanwendungen müssen manuell hochgeladen und immer vom Administrator bereitgestellt werden. Bereitgestellte Updates werden automatisch auf allen Benutzergeräten mit der App installiert. Der Benutzer hat keine Kontrolle über die Updates. 

## <a name="microsoft-store-for-business-apps"></a>Apps im Microsoft Store für Unternehmen

Bei Apps aus dem Microsoft Store für Unternehmen handelt es sich um moderne Apps, die über das Verwaltungsportal des Microsoft Store für Unternehmen erworben und dann über Microsoft Intune für die Verwaltung synchronisiert wurden. Diese Apps können entweder **online** oder **offline** lizenziert werden. Updates für Apps aus dem Microsoft Store für Unternehmen werden direkt vom Microsoft Store verwaltet, d.h., dass der Administrator nicht eingreifen muss. Der Administrator kann Updates für bestimmte Apps jedoch mithilfe von benutzerdefinierten Uniform Resource Identifiern (URI) verhindern. Weitere Informationen finden Sie im Artikel „Enterprise app management“ (Verwalten von Unternehmens-Apps) unter [Prevent app from automatic updates (Verhindern von automatischen App-Updates)](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates). Benutzer können auf ihren Geräten auch Updates für alle Apps aus dem Microsoft Store für Unternehmen deaktivieren. 

## <a name="installing-apps-on-windows-10-devices"></a>Installieren von Apps auf Windows 10-Geräten
Apps können je nach Typ auf zwei Arten auf Windows 10-Geräten installiert werden:

- **Benutzerkontext:** Wenn eine Bereitstellung im Benutzerkontext erfolgt, wird die verwaltete App erst auf dem Gerät installiert, wenn sich der Benutzer darauf anmeldet. Beachten Sie, dass die App-Installation erst erfolgreich ausgeführt wird, wenn sich der Benutzer auf dem Gerät anmeldet. 
    - Moderne Branchenanwendungen und Apps aus dem Microsoft für Unternehmen (online und offline) können im Benutzerkontext bereitgestellt werden und unterstützen die Absichten „Erforderlich“ und „Verfügbar“.
- **Gerätekontext:** Wenn eine Bereitstellung im Gerätekontext erfolgt, wird die verwaltete App von Intune direkt auf dem Gerät installiert.
    - Nur moderne branchenspezifische Apps und online lizenzierte Apps aus dem Microsoft Store für Unternehmen können im Gerätekontext bereitgestellt werden. Sie unterstützen nur die Absicht „Erforderlich“.

> [!Note]
> Die Bereitstellung von MSI-Dateien über MDM im Gerätekontext wird auf Windows 10-Geräten noch nicht unterstützt.

Wenn eine App im Gerätekontext bereitgestellt wird, ist die Installation nur erfolgreich, wenn das betreffende Gerät den Gerätekontext unterstützt. Darüber hinaus gilt Folgendes für Bereitstellungen im Gerätekontext:
- Wenn eine App im Gerätekontext für einen bestimmten Benutzer bereitgestellt wird, schlägt die Installation fehl. In der Verwaltungskonsole wird Folgendes angezeigt:
    - Status: Failed. (Fehler bei der Installation.)
    - Fehler: A user can’t be targeted with a Device context install. (Für einen bestimmten Benutzer kann keine Installation im Gerätekontext ausgeführt werden.)
- Wenn eine App für ein bestimmtes Gerät, das keinen Gerätekontext unterstützt, im Gerätekontext bereitgestellt wird, schlägt die Installation fehl. In der Verwaltungskonsole wird Folgendes angezeigt:
    - Status: Failed. (Fehler bei der Installation.)
    - Fehler: This platform does not support device context installs. (Diese Plattform unterstützt keine Installationen im Gerätekontext.) 

> [!Note]
> Wenn eine App-Zuweisung mit einer bestimmten Bereitstellung gespeichert wird, kann der Kontext für die Zuweisung nur noch für moderne Apps geändert werden. Bei modernen Apps kann der Kontext von „Benutzerkontext“ in „Gerätekontext“ geändert werden. 

Falls für einen einzelnen Benutzer oder ein einzelnes Gerät ein Richtlinienkonflikt auftritt, wird die endgültige Richtlinie anhand der folgenden Prioritäten ermittelt:
- Eine Richtlinie für den Gerätekontext hat eine höhere Priorität als eine Richtlinie für den Benutzerkontext. 
- Eine Installationsrichtlinie hat eine höhere Priorität als eine Deinstallationsrichtlinie.

Weitere Informationen zum Zuweisen von Apps mit Microsoft Intune finden Sie unter [Zuweisen von Apps zu Gruppen mit Microsoft Intune](apps-deploy.md) und [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](apps-inc-exl-assignments.md). Weitere Informationen zu App-Typen in Intune finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md).

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zum Zuweisen von Apps zu Gruppen finden Sie unter [Zuweisen von Apps zu Gruppen mit Microsoft Intune](apps-deploy.md).
- Weitere Informationen zum Überwachen von App-Zuweisungen finden Sie unter [Überwachen von App-Informationen und -Zuweisungen mit Microsoft Intune](apps-monitor.md).
