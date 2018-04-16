---
title: "Zertifikatprofile für den Ressourcenzugriff"
description: "Sichern von VPN-, WLAN- und E-Mail-Zugriff mit einem Zertifikat, das auf jedem Benutzergerät installiert ist."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ccfd69579832c553dc1416c21ca93b85cd93cd78
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="secure-resource-access-with-certificate-profiles-in-microsoft-intune"></a>Sicherer Zugriff auf Ressourcen mit Zertifikatprofilen in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Wenn Sie Benutzern den Zugriff auf Unternehmensressourcen über VPN, WLAN oder E-Mail-Profile gestatten, können Sie diesen Zugriff mit einem Zertifikat absichern, das auf jedem Benutzergerät installiert wird. Gehen Sie dazu folgendermaßen vor:

1. Stellen Sie sicher, dass die richtige Zertifikatinfrastruktur eingerichtet ist, wie unter [Konfigurieren der Zertifikatinfrastruktur für SCEP](configure-certificate-infrastructure-for-scep.md) und [Konfigurieren der Zertifikatinfrastruktur für PFX](configure-certificate-infrastructure-for-pfx.md) beschrieben.

2. Installieren Sie auf jedem Gerät ein Stammzertifikat oder ein Zertifikat einer Zwischenzertifizierungsstelle, damit das Gerät die Rechtmäßigkeit Ihrer Zertifizierungsstelle erkennt. Zu diesem Zweck erstellen Sie ein **vertrauenswürdiges Zertifikatprofil** und stellen dieses bereit. Wenn Sie dieses Profil bereitstellen, wird das Stammzertifikat von den Geräten, die Sie mit Intune verwalten, angefordert und empfangen. Sie müssen für jede Plattform ein eigenes Profil erstellen. Das **vertrauenswürdige Zertifikatprofil** ist für folgende Plattformen verfügbar:
   -  iOS 8.0 und höher
   -  Mac OS X 10.9 und höher
   -  Android 4,0 und höher
   -  Android for Work
   -  Windows 8.1 und höher
   -  Windows Phone 8.1 und höher

3. Erstellen Sie Zertifikatprofile, damit Geräte ein Zertifikat für die Authentifizierung des VPN-, WLAN- und E-Mail-Zugriffs anfordern, wie unter [Konfigurieren von Intune-Zertifikatprofilen](configure-intune-certificate-profiles.md) beschrieben. Sie können ein **PKCS #12-Zertifikatprofil (.PFX)** *oder* ein **SCEP-Zertifikatprofil** für Geräte auf diesen Plattformen erstellen und bereitstellen:

   -  iOS 8.0 und höher
   -  Android 4,0 und höher
   -  Android for Work
   -  Windows 10 (Desktop und Mobile) und höher

   Verwenden Sie ein **SCEP-Zertifikatprofil** für Geräte, die diese Plattformen ausführen:
    -   Mac OS X 10.9 und höher
    -   Windows Phone 8.1

Sie müssen für jede Plattform ein eigenes Profil erstellen. Nachdem Sie das Profil erstellt haben, ordnen Sie es dem bereits erstellten **vertrauenswürdigen Stammzertifikatprofil** zu.

> [!NOTE]           
> - Wenn Sie über keine Unternehmenszertifizierungsstelle verfügen, müssen Sie eine erstellen.
>- Wenn Sie sich basierend auf Ihren Geräteplattformen entschließen, das SCEP-Profil (Simple Certificate Enrollment Protocol) zu verwenden, müssen Sie auch einen NDES-Server (Network Device Enrollment Service) konfigurieren.
>-  Unabhängig davon, ob Sie SCEP- oder .PFX-Profile verwenden möchten, müssen Sie den Microsoft Intune-Zertifikatconnector herunterladen und konfigurieren.
>-  Informationen zur Konfiguration aller erforderlichen Dienste finden Sie unter [Konfigurieren der Zertifikatinfrastruktur für SCEP](configure-certificate-infrastructure-for-scep.md) bzw. unter [Konfigurieren der Zertifikatinfrastruktur für PFX](configure-certificate-infrastructure-for-pfx.md).

### <a name="next-steps"></a>Nächste Schritte
- [Konfigurieren der Zertifikatinfrastruktur für SCEP](configure-certificate-infrastructure-for-scep.md)
- [Konfigurieren der Zertifikatinfrastruktur für PFX](configure-certificate-infrastructure-for-pfx.md)
- [Konfigurieren von Intune-Zertifikatprofilen](configure-intune-certificate-profiles.md)
