---
title: Windows 10-App-Bereitstellung mit Microsoft Intune
titleSuffix: ''
description: In diesem Artikel lernen Sie die für Microsoft Intune verfügbaren Bereitstellungsszenarien für Windows 10-Apps kennen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/25/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7251a2db0c36db9d01e51ca8fc62bd4e072d80e6
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609225"
---
# <a name="windows-10-app-deployment-by-using-microsoft-intune"></a>Windows 10-App-Bereitstellung mit Microsoft Intune 

Microsoft Intune unterstützt auf Windows 10-Geräten verschiedene App-Typen und Bereitstellungsszenarios. Nachdem Sie Intune eine App hinzugefügt haben, können Sie diese Benutzern und Geräten zuweisen. Dieser Artikel enthält weitere Informationen zu den unterstützten Windows 10-Szenarien sowie wichtige Details, die Sie beim Bereitstellen von Apps für Windows beachten müssen. 

Branchenspezifische Apps und Apps aus dem Microsoft Store für Unternehmen werden auf Windows 10-Geräten unterstützt. Zu den Dateierweiterungen für Windows-Apps gehören MSI, APPX und APPXBUNDLE.  

> [!Note]
> Zum Bereitstellen moderner Apps benötigen Sie mindestens Folgendes:
> - Für Windows 10 1803: [23. Mai 2018 – KB4100403 (Betriebssystembuild 17134.81)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403)
> - Für Windows 10 1709: [21. Juni 2018 – KB4284822 (Betriebssystembuild 16299.522)](https://support.microsoft.com/help/4284822)
>
> Nur Windows 10 Version 1803 und höher unterstützen die Installation von Apps, wenn kein primärer Benutzer zugeordnet ist.
>
> Die Bereitstellung branchenspezifischer Apps wird auf Geräten mit Windows 10 Home-Editionen nicht unterstützt.

## <a name="supported-windows-10-app-types"></a>Unterstützte Windows 10-App-Typen

Bestimmte App-Typen werden basierend auf der Version von Windows 10 unterstützt, die von Ihren Benutzern ausgeführt wird. In der folgenden Tabelle sind der App-Typ und die Unterstützung für Windows 10 enthalten.

| App-Typ | -Startseite | Pro | Business | Enterprise | Education | S-Modus | HoloLens<sup>1 | Surface Hub | WCOS | Handy |
|----------------|------|-----|----------|------------|-----------|--------|-----------|------------|------|--------|
|  .MSI | Nein | Ja | Ja | Ja | Ja | Nein | Nein | Nein | Nein | Nein |
| .IntuneWin | Nein | Ja | Ja | Ja | Ja | 19H2+ | Nein | Nein | Nein | Nein |
| Office C2R | Nein | Ja | Ja | Ja | Ja | RS4+ | Nein | Nein | Nein | Nein |
| LOB: APPX/MSIX | Ja | Ja | Ja | Ja | Ja | Ja | Ja | Ja | Ja | Ja |
| MSFB Offline | Ja | Ja | Ja | Ja | Ja | Ja | Ja | Ja | Ja | Ja |
| MSFB Online | Ja | Ja | Ja | Ja | Ja | Ja | RS4+ | Nein | Ja | Ja |
| Web-Apps | Ja | Ja | Ja | Ja | Ja | Ja | Ja<sup>2 | Ja<sup>2 | Ja | Ja<sup>2 |
| Store-Link | Ja | Ja | Ja | Ja | Ja | Ja | Ja | Ja | Ja | Ja |

<sup>1</sup> Wenn Sie die App-Verwaltung verwenden möchten, führen Sie ein Upgrade auf Ihr HoloLens-Gerät zu [Holographic for Business](../fundamentals/windows-holographic-for-business.md) aus.<br />
<sup>2</sup> Starten nur über das Unternehmensportal möglich.

> [!NOTE]
> Alle Windows-App-Typen erfordern eine Registrierung.

## <a name="windows-10-lob-apps"></a>Branchenspezifische Windows 10-Apps

Sie können branchenspezifische Windows 10-Apps signieren und in die Intune-Verwaltungskonsole hochladen. Bei diesen Apps kann es sich sowohl um moderne Apps wie UWP-Apps (Universelle Windows-Plattform) und Windows-App-Pakete (AppX) als auch um Win32-Apps handeln, z. B. einfache Microsoft Installer-Paketdateien (MSI). Der Administrator muss Updates branchenspezifischer Apps manuell hochladen und bereitstellen. Diese Updates werden automatisch auf Benutzergeräten installiert, auf denen die App installiert ist. Es ist kein Benutzereingriff erforderlich, und der Benutzer hat keine Kontrolle über die Updates. 

## <a name="microsoft-store-for-business-apps"></a>Apps aus Microsoft Store für Unternehmen

Bei Apps aus dem Microsoft Store für Unternehmen handelt es sich um moderne Apps, die über das Verwaltungsportal des Microsoft Store für Unternehmen erworben wurden. Sie werden dann mit Microsoft Intune für die Verwaltung synchronisiert. Die Apps können entweder online oder offline lizenziert werden. Der Microsoft Store verwaltet Updates direkt, ohne dass weitere Aktionen des Administrators erforderlich sind. Sie können Updates für bestimmte Apps jedoch mithilfe eines benutzerdefinierten Uniform Resource Identifiers (URI) verhindern. Weitere Informationen finden Sie im Artikel „Enterprise app management“ (Verwalten von Unternehmens-Apps) unter [Prevent app from automatic updates (Verhindern von automatischen App-Updates)](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates). Die Benutzer können auch Updates für alle Apps aus dem Microsoft Store für Unternehmen deaktivieren. 

### <a name="categorize-microsoft-store-for-business-apps"></a>Kategorisieren von Apps aus dem Microsoft Store für Unternehmen 
So kategorisieren Sie Apps aus dem Microsoft Store für Unternehmen: 

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Alle Apps** aus. 
3. Wählen Sie eine App im Microsoft Store für Unternehmen aus. Wählen Sie dann **Eigenschaften** > **App-Informationen** > **Kategorie** aus. 
4. Wählen Sie eine Kategorie aus.

## <a name="install-apps-on-windows-10-devices"></a>Installieren von Apps auf Windows 10-Geräten
Sie können Apps je nach Typ auf zwei Arten auf Windows 10-Geräten installieren:

- **Benutzerkontext**: Wenn eine Bereitstellung im Benutzerkontext erfolgt, wird die verwaltete App für diesen Benutzer auf dem Gerät installiert, wenn sich der Benutzer beim Gerät anmeldet. Beachten Sie, dass die App-Installation erst erfolgreich ausgeführt wird, wenn sich der Benutzer beim Gerät anmeldet. 
  - Moderne LOB-Apps (Line-Of-Business, branchenspezifisch) und Apps aus dem Microsoft Store für Unternehmen (online und offline) können im Benutzerkontext bereitgestellt werden. Die Apps unterstützen die Absichten „Erforderlich“ und „Verfügbar“.
  - Win32-Apps, die im „Benutzermodus“ oder „Dualmodus“ erstellt wurden, können im Benutzerkontext bereitgestellt werden und unterstützen sowohl die Absicht „Erforderlich“ als auch „Verfügbar“. 
- **Gerätekontext**: Wenn eine Bereitstellung im Gerätekontext erfolgt, wird die verwaltete App von Intune direkt auf dem Gerät installiert.
  - Nur moderne LOB-Apps und offline lizenzierte Apps aus dem Microsoft Store für Unternehmen können im Gerätekontext bereitgestellt werden. Diese Apps unterstützen nur die Absicht „Erforderlich“.
  - Win32-Apps, die im „Computermodus“ oder „Dualmodus“ erstellt wurden, können im Benutzerkontext bereitgestellt werden und unterstützen nur die Absicht „Erforderlich“.

> [!NOTE]
> Für Win32-Apps, die als Apps im „Dualmodus“ erstellt wurden, muss der Administrator wählen, ob die App als App im „Benutzermodus“ oder „Computermodus“ für alle Zuweisungen fungieren soll, die dieser Instanz zugeordnet sind. Der Bereitstellungskontext kann nicht je Zuweisung geändert werden.  

Apps können nur im Gerätekontext installiert werden, wenn sie vom Gerät und vom Intune-App-Typ unterstützt werden. Sie können die folgenden App-Typen im Gerätekontext installieren und diese Apps einer Gerätegruppe zuweisen:

- Win32-Apps
- Offline lizenzierte Apps im Microsoft Store für Unternehmen
- LOB-Apps (MSI, APPX und MSIX)
- Office 365 ProPlus

Windows LOB-Apps (insbesondere APPX und MSIX) und Microsoft Store für Unternehmens-Apps (Offline-Apps), die Sie für die Installation im Gerätekontext ausgewählt haben, müssen einer Gerätegruppe zugewiesen werden. Bei der Installation tritt ein Fehler auf, wenn eine dieser Apps im Benutzerkontext bereitgestellt wird. Der folgende Status und Fehler werden in der Verwaltungskonsole angezeigt:
  - Status: Fehlerhaft.
  - Fehler: Ein Benutzer kann nicht als Ziel für eine Gerätekontextinstallation festgelegt werden.

> [!IMPORTANT]
> Bei Verwendung in Kombination mit einem Autopilot-Bereitstellungsszenario mit intensiver Benutzerunterstützung ist nicht erforderlich, dass LOB-Apps und Microsoft Store für Unternehmen-Apps, die im Gerätekontext bereitgestellt werden, auf eine Gerätegruppe zielen. Weitere Informationen finden Sie unter [Windows Autopilot für Bereitstellung mit intensiver Benutzerunterstützung](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove).

> [!Note]
> Nachdem Sie eine App-Zuweisung mit einer bestimmten Bereitstellung gespeichert haben, können Sie den Kontext für die Zuweisung nur für moderne Apps ändern. Für moderne Apps können Sie den Kontext vom Benutzerkontext in den Gerätekontext ändern. 

Wenn in den Richtlinien für einen einzelnen Benutzer oder ein Gerät ein Konflikt auftritt, gelten die folgenden Prioritäten:
- Eine Richtlinie für den Gerätekontext hat eine höhere Priorität als eine Richtlinie für den Benutzerkontext. 
- Eine Installationsrichtlinie hat eine höhere Priorität als eine Deinstallationsrichtlinie.

Weitere Informationen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](apps-inc-exl-assignments.md). Weitere Informationen zu App-Typen in Intune finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md).

## <a name="next-steps"></a>Nächste Schritte

- [Zuweisen von Apps zu Gruppen mit Microsoft Intune](apps-deploy.md)
- [Überwachen von Apps](apps-monitor.md)
