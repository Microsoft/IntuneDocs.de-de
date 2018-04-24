---
title: Aktualisierung von Apps
description: Verwenden Sie die Informationen in diesem Thema, um zu erfahren, wie Sie Apps aktualisieren, wenn eine neue Version erforderlich ist.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4ee48f751c181cd12c8e549c5aa4aab0c6252add
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="update-apps-using-microsoft-intune"></a>Aktualisieren von Apps mit 

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune unterstützt Sie bei der Verwaltung von App-Updates. Verwenden Sie die Informationen in diesem Thema, um zu erfahren, wie Sie Apps aktualisieren, wenn eine neue Version erforderlich ist.

## <a name="how-to-update-apps"></a>Aktualisieren von Apps
Wenn eine neue Version einer von Ihnen bereitgestellten App veröffentlicht wird, können Sie mit Intune die neuere Version der App aktualisieren und bereitstellen. Sie können eine Bereitstellung nur durch eine neuere Version der gleichen App (mit derselben ID) ersetzen. App-Updates können nicht zum Aktualisieren einer Bereitstellung mit einem anderen App-Paket verwendet werden.

### <a name="app-identifiers"></a>App-Bezeichner
Der App-Bezeichner ist eine Eigenschaft, die eine App eindeutig identifiziert. Sie können nicht mehrere Kopien einer App mit dem gleichen Bezeichner installieren. Im Folgenden sind einige Beispiele für App-IDs aufgeführt:

- **iOS** – Paket-ID (z. B. com.microsoft.excel)
- **Android** – Paket-ID (z. B. com.microsoft.excel)
- **Windows Phone-** – (XAP-Installer) mit Produkt-ID (GUID)
- **Windows** – (Appx/Appxbundle), verwenden Sie den vollständigen Paketnamen



> [!IMPORTANT]
> Beim Bereitstellen einer App mit der Bereitstellungsaktion **Erforderliche Installation** und einer späteren Änderung der Bereitstellungsaktion in **Verfügbare Installation**werden Updates für die App auf Geräten, auf denen die App vor der Bereitstellungsänderung installiert war, nicht automatisch installiert. Gehen Sie wie folgt vor, um dieses Problem zu beheben:
>
> -   Bitten Sie den Benutzer des Geräts, das Unternehmensportal zu öffnen, die installierte App auszuwählen und **Installieren** auszuwählen.
> -   Ändern Sie die Bereitstellungsaktion in **Deinstallieren**, und stellen Sie die App nach der Deinstallation der App erneut mit der Bereitstellungsaktion **Verfügbare Installation**bereit.

### <a name="to-update-an-app"></a>So aktualisieren Sie eine App

1.  Wählen Sie in der [Microsoft Intune-Verwaltungskonsole](https://manage.microsoft.com) **Apps** &gt; **Apps** aus.

2.  Wählen Sie in der Liste **Apps** die zu aktualisierende App und anschließend **Bearbeiten** aus.

3.  Geben Sie im Assistenten **Software bearbeiten** neue Details für das App-Paket ein.

4.  Wählen Sie anschließend **Aktualisieren** aus.

Wenn Geräte das nächste Mal prüfen, ob Apps verfügbar sind, wird die App automatisch auf die neueste Version aktualisiert.
Bei Apps, die aus einem App-Paket installiert wurden (branchenspezifische Apps), erfolgt das Upgrade für erforderliche sowie verfügbare Bereitstellungen automatisch, solange die App über denselben Bezeichner verfügt.

Bei Apps, die als Link zu einem Store bereitgestellt wurden, wird das Update von dem Store verwaltet, aus dem die App stammt.
