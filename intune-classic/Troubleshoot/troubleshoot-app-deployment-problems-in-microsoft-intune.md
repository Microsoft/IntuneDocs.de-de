---
title: Behandlung von Problemen mit der App-Bereitstellung
description: Diese Themen helfen Ihnen, Probleme mit der App-Bereitstellung mit Microsoft Intune zu lösen.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 09/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ec4116a54377b3db7ea58d8e24e49c44edf73a7a
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="troubleshoot-app-deployment-problems-in-microsoft-intune"></a>Behandlung von Problemen mit der App-Bereitstellung in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Wenn beim Bereitstellen und Verwalten von Apps mit Intune Probleme auftreten, beginnen Sie hier. In diesem Thema werden einige allgemeine Probleme, die auftreten können, sowie deren Lösungen behandelt.

## <a name="common-app-deployment-error-codes"></a>Gängige Fehlercodes bei der App-Bereitstellung

|Fehlercode|Mögliches Problem|Lösungsvorschlag|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (Clientfehler)|Zur Installation der Anwendung müssen Sie über ein zum Querladen fähiges System verfügen.|Stellen Sie sicher, dass das App-Paket mit einer vertrauenswürdigen Signatur signiert und auf einem zur Domäne gehörenden Gerät mit aktivierter Richtlinie „AllowAllTrustedApps“ oder auf einem Gerät mit Windows Sideloading-Lizenz und aktivierter Richtlinie „AllowAllTrustedApps“ installiert ist.|
|0x80073CF0|Das Paket konnte nicht geöffnet werden.|Mögliche Ursachen:<br /><br />-   Das Paket ist nicht signiert.<br />-   Der Namen des Herausgebers stimmt nicht mit dem Signaturzertifikat des Antragstellers überein.<br /><br />Prüfen Sie das Ereignisprotokoll „AppxPackagingOM“, um weitere Informationen zu erhalten.|
|0x80073CF3|Fehler bei Updates des Pakets (Abhängigkeits- oder Konfliktüberprüfung)|Mögliche Ursachen:<br /><br />-   Das eingehende Paket ist mit einem installierten Paket nicht vereinbar.<br />-   Eine angegebene Paketabhängigkeit wurde nicht gefunden.<br />-   Das Paket unterstützt nicht die richtige Prozessorarchitektur.<br /><br />Prüfen Sie das Ereignisprotokoll „AppXDeployment-Server“, um weitere Informationen zu erhalten.|
|0x80073CFB|Das bereitgestellte Paket ist bereits installiert, und eine erneute Installation des Pakets wird blockiert.|Dieser Fehler kann auftreten, wenn Sie ein Paket installieren, das nicht bitweise mit dem bereits installierten Paket identisch ist. Überprüfen Sie, ob die digitale Signatur auch Teil des Pakets ist. Wenn ein Paket erneut erstellt oder signiert wird, ist das Paket nicht mehr bitweise identisch mit dem zuvor installierten Paket. Es gibt zwei Möglichkeiten, diesen Fehler zu beheben:<br /><br />-   Erhöhen Sie die Versionsnummer der Anwendung, und erstellen und signieren Sie das Paket dann erneut.<br />-   Entfernen Sie das alte Paket für jeden Benutzer des Systems, bevor Sie das neue Paket installieren.|
|0x87D1041C|Die Anwendung wurde erfolgreich installiert, wird jedoch nicht erkannt.|– Die App wurde erfolgreich von Intune bereitgestellt und später deinstalliert (möglicherweise vom Endbenutzer). Weisen Sie den Benutzer an, die App aus dem Unternehmensportal neu zu installieren. Erforderliche Apps werden automatisch beim nächsten Einchecken des Geräts neu installiert.|

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Problembehandlung bei Apps aus dem Microsoft Store

Mithilfe der Informationen im Artikel [Problembehandlung beim Packen, Bereitstellen und Abfragen von Microsoft Store-Apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) können Sie allgemeine Probleme beheben, die bei der Installation von Apps aus dem Microsoft Store (mit Intune oder mittels anderer Tools) auftreten können.

## <a name="troubleshooting-app-deployment-to-pcs-managed-by-the-intune-software-client"></a>Problembehandlung bei der Bereitstellung von Apps auf PCs, die vom Intune-Softwareclient verwaltet werden
Beim Beheben von Problemen beim Bereitstellen von Apps auf PCs, die vom Intune-Softwareclient verwaltet werden, können die beiden folgenden Protokolldateien aufschlussreich sein:
- %Programme%\Microsoft\OnlineManagement\Logs
- %Programme%\Microsoft\OnlineManagement\Updates\ReportingEvents.log

Wenn Sie darüber hinaus eine Supportanfrage für Intune erstellen müssen, ist es zudem sinnvoll, diese Protokolle auch an Microsoft zu senden.


### <a name="next-steps"></a>Nächste Schritte
Wenn diese Informationen zur Problembehandlung für Sie nicht hilfreich waren, wenden Sie sich wie in [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Anfordern von Support für Microsoft Intune) beschrieben an den Microsoft Support.
