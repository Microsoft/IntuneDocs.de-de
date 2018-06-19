---
title: Vorbereitungen zum Konfigurieren von App-Schutzrichtlinien für Windows 10
description: Einrichten des MAM-Anbieters (Mobile Application Management) in Azure AD
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 04/18/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ebc7cfc8-40b9-47c2-8357-d392ebbb27c8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9b91d3740ead5815974d7ffee67c15b7769b0210
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025551"
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Vorbereitungen zum Konfigurieren von App-Schutzrichtlinien für Windows 10

[!INCLUDE [note for both-portals](../includes/note-for-both-portals.md)]

Vor der Erstellung einer Windows 10-App-Schutzrichtlinie müssen Sie die mobile Anwendungsverwaltung (MAM) für Windows 10 aktivieren, indem Sie den MAM-Anbieter in Azure AD einrichten. Mit dieser Konfiguration können Sie den Registrierungsstatus definieren, wenn Sie eine neue WIP-Richtlinie (Windows Information Protection) in Intune erstellen.

> [!NOTE]
> Der Registrierungsstatus kann entweder „MAM“ oder „Mobile Geräteverwaltung (MDM)“ lauten.

## <a name="to-configure-the-mam-provider"></a>Konfigurieren des MAM-Anbieters

1.  Navigieren Sie zum [Azure-Portal](https://portal.azure.com/) und melden Sie sich mit Ihren Intune-Anmeldeinformationen an.

2.  Wählen Sie im linken Menü **Azure Active Directory** aus.

    ![Konfiguration des MAM-Anbieters](../media/AppManagement/mam-provider-sc-1.png)

3.  Das Blatt **Azure AD** wird geöffnet. Wählen Sie **Mobilität (MDM und MAM)** und klicken Sie dann auf **Microsoft Intune**.

    ![Mobilität (MDM und MAM)](../media/AppManagement/mam-provider-sc-2.png)

4.  Das Blatt zur Konfiguration wird geöffnet. Wählen Sie zuerst **Standard-MAM-URLs wiederherstellen** aus und konfigurieren Sie dann Folgendes:

    ein.  MAM-Benutzerbereich: Mit MAM können Sie Unternehmensdaten für bestimmte Benutzergruppen, die Windows 10-Geräte verwenden, oder alle Benutzer schützen.

    b.  URL zu den MAM-Nutzungsbedingungen: Die URL zum Endpunkt für die Nutzungsbedingungen des MAM-Diensts. Hierdurch werden die Bedingungen des MAM-Diensts für Endbenutzer angezeigt.

    c.  URL für MAM-Ermittlung: Dies ist die URL, nach denen Geräte beim Anwenden von App-Schutzrichtlinien suchen müssen.

    d.  URL für MAM-Kompatibilität:

5.  Nachdem Sie diese Einstellungen konfiguriert haben, wählen Sie **Speichern**.

## <a name="next-steps"></a>Nächste Schritte

[Erstellen einer WIP-App-Schutzrichtlinie](/intune-classic/deploy-use/create-windows-information-protection-policy-with-intune)
