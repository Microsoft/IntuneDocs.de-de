---
title: Bereitstellen von Apps
description: Die Informationen in diesem Thema helfen Ihnen beim Bereitstellen von Apps mit Microsoft Intune.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3b42019e-73da-4538-a496-212f11d5bf9b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ed098a22da1def82c90fbb159d54be9b1a369ba8
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="deploy-apps-in-microsoft-intune"></a>Bereitstellen von Apps in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Die Informationen in diesem Thema helfen Ihnen beim Bereitstellen von Apps mit Microsoft Intune.


## <a name="deploy-an-app"></a>Bereitstellen einer App
Bei dieser Vorgehensweise stellen Sie die App für ausgewählte Gruppen von Geräten oder für ausgewählte Benutzer bereit.

### <a name="to-deploy-an-app"></a>So stellen Sie eine App bereit

1. Klicken Sie in der [Microsoft Intune-Administratorkonsole](https://manage.microsoft.com) auf **Apps** &gt; **Apps**, um die Liste der von Ihnen verwalteten Apps anzuzeigen.

2.  Wählen Sie die bereitzustellende App aus, und klicken Sie anschließend auf **Bereitstellung verwalten**.

3.  Wählen Sie im Dialogfeld *&lt;Name der App&gt;* auf der Seite **Gruppen auswählen** die Benutzer- oder Gerätegruppen aus, für die die App bereitgestellt werden soll.

4.  Konfigurieren Sie auf der Seite **Bereitstellungsaktion** Folgendes:

    - **Genehmigung** – Legen Sie den Status der Bereitstellung fest:
        - **Erforderlich** (die Installation ist obligatorisch)
        - **Verfügbar** (Benutzer installieren die App über das Unternehmensportal nach Bedarf)
        - **Nicht verfügbar** (die App wird nicht installiert und nicht im Unternehmensportal angezeigt)
        - **Deinstallieren** (die App wird von den Zielgeräten deinstalliert).
    - **Stichtag** – Geben Sie für erforderliche Installationen an, wann die App bereitgestellt werden soll. Sie können entweder vordefinierte Werte oder **Benutzerdefiniert** auswählen, um einen eigenen Stichtag zu konfigurieren.

5. Wenn die bereitzustellende App mithilfe einer Richtlinie für die Verwaltung mobiler Anwendungen konfiguriert werden kann, wird die Seite **Verwaltung mobiler Apps** angezeigt. Wählen Sie auf dieser Seite die Richtlinie für die mobile Anwendungsverwaltung aus, die Sie dieser App zuordnen möchten.

    [Informieren Sie sich, welche Microsoft-Apps mit Richtlinien für die Verwaltung mobiler Anwendungen kompatibel sind.](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx)

6. Wenn die bereitzustellende App mit Intune-VPN-Profilen kompatibel ist, wird die Seite **VPN-Profil** angezeigt. Auf dieser Seite können Sie festlegen, dass iOS-Apps mit einem von Ihnen bereitgestellten VPN-Profil verknüpft werden sollen. Die VPN-Verbindung wird automatisch geöffnet, wenn die App gestartet wird. Um ein VPN-Profil verfügbar zu machen, müssen Sie die Profileinstellung **VPN pro App** aktivieren.
 Informationen zum Konfigurieren von VPN-Profilen, einschließlich Informationen zum Verknüpfen von Profilen mit Apps, finden Sie unter [VPN-Verbindungen in Microsoft Intune](vpn-connections-in-microsoft-intune.md).

<!---
>[!TIP]
>If an end user previously installed an iOS app and you now deploy it with a deployment action of **Available**, Intune will automatically begin to manage that app with no further action required by you, or the end-user.
--->

## <a name="example"></a>Beispiel

In diesem Beispiel haben Sie die App als **Verfügbar** für ein iOS-Gerät bereitgestellt.
Die App wird für Benutzergeräte im Unternehmensportal angezeigt. Die Benutzer können die App vom Portal aus installieren.

In diesem Screenshot wurde z. B. die App „Bing for iOS“ mit dem Installationstyp **Externer Link** zusammen mit einem benutzerdefinierten Symbol bereitgestellt. Die Option **Als ausgewählte App anzeigen und im Unternehmensportal hervorheben** wurde ausgewählt.  
![Verfügbare iOS-App](./media/available-install-on-iOS.png)

Wenn Sie die App als **Erforderlich** für ein iOS-Gerät bereitgestellt haben, wird der Benutzer benachrichtigt, dass diese App zur Installation bereitsteht. In diesem Screenshot wurde z. B. die App „Work Folders for iOS“ mit dem Installationstyp **Verwaltete iOS-App aus dem App Store** bereitgestellt.  
![Erforderliche iOS-App](./media/iOS-Required-install.PNG)

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie eine Anwendung bereitgestellt haben, ist es sinnvoll, deren Status zu überwachen. Weitere Informationen finden Sie unter [Überwachen von Apps in Microsoft Intune](monitor-apps-in-microsoft-intune.md).
