---
title: Suchen eines Paketfamiliennamens (PFN) für Pro-App-VPN
description: Suchen Sie einen Paketfamiliennamen (PFN), den Sie zum Konfigurieren eines anwendungsbezogenen VPN („VPN pro App“) benötigen.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 10/25/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 74643d1d-4fd9-4cff-ac79-1a42281d2f76
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tycast
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c6bbc1bd477cde7eecb78b78c8efa4bfde46976f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="find-a-package-family-name-pfn-for-per-app-vpn-configuration"></a>Suchen eines Paketfamiliennamens (PFN) für eine Konfiguration mit VPN pro App

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Es gibt zwei Möglichkeiten zum Suchen eines Paketfamiliennamens (PFN), den Sie zum Einrichten eines anwendungsbezogenen VPNs benötigen.

## <a name="find-a-pfn-for-an-app-thats-installed-on-a-windows-10-computer"></a>Suchen eines PFN für eine App, die auf einem Windows 10-Computer installiert ist

Wenn die App, mit der Sie arbeiten, bereits auf einem Windows 10-Computer installiert ist, können Sie den PFN mit dem PowerShell-Cmdlet [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) abrufen.

Die Syntax für die „Get-AppxPackage“ lautet:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
> Möglicherweise müssen Sie PowerShell als Administrator ausführen, um den PFN abzurufen.

Beispielsweise rufen Sie mit `Get-AppxPackage` die Informationen über alle auf dem Computer installierten universellen Apps ab.

Wenn Sie Informationen über eine App abrufen möchten, von der Sie den Namen oder einen Teil des Namens kennen, verwenden Sie `Get-AppxPackage *<app_name>`. Das Verwenden des Platzhalterzeichens ist besonders nützlich, wenn Sie den vollständigen Namen der App nicht genau kennen. Zum Beispiel können Sie mit `Get-AppxPackage *OneNote` Informationen über OneNote abrufen.


Für OneNote werden folgende Informationen abgerufen:

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## <a name="find-a-pfn-if-the-app-is-not-installed-on-a-computer"></a>Suchen eines PFN, wenn die App nicht auf dem Computer installiert ist

1.  Wechseln Sie zu https://www.microsoft.com/store/apps.
2.  Geben Sie in der Suchleiste den Namen der App ein. Suchen Sie z.B. nach OneNote.
3.  Wählen Sie den Link zu der App aus. Am Ende der URL finden Sie eine Reihe von Buchstaben. In unserem Beispiel sieht die URL folgendermaßen aus: `https://www.microsoft.com/store/apps/onenote/9wzdncrfhvjl`.
4.  Fügen Sie in eine andere Registerkarte die folgende URL ein: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`. Ersetzen Sie `<app id>` durch die App-ID, die Sie unter https://www.microsoft.com/store/apps gefunden haben (die Buchstabenfolge am Ende der URL aus Schritt 3). In unserem Beispiel für OneNote fügen Sie `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata` ein.

In Microsoft Edge werden die gewünschten Informationen angezeigt. In Internet Explorer müssen Sie **Öffnen** auswählen, um die Informationen anzuzeigen. Der PFN wird in der ersten Zeile angegeben. Dies sind die Ergebnisse für unser Beispiel:


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`
