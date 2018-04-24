---
title: Überprüfen Ihres MAM-Setups
description: In diesem Thema wird beschrieben, wie Sie testen und überprüfen können, ob Ihre MAM-Richtlinie ordnungsgemäß eingerichtet wurde und wie erwartet funktioniert.
keywords: ''
author: andredm7
ms.author: andredm
manager: angerobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 41d82597-e13e-4c3e-9151-e71392236ca0
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.custom: intune-classic
ms.openlocfilehash: 6f11c2f2af53813040417a8f40e983b5c88d5189
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="validating-your-mobile-application-management-setup"></a>Überprüfen des Setups für die Verwaltung Ihrer mobilen Anwendungen

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Dieses Thema enthält Informationen zum Suchen nach Problemen nach der Einrichtung der mobilen Anwendungsverwaltung (MAM). Diese Anleitung gilt für MAM-Richtlinien im Azure-Portal.

### <a name="checking-for-symptoms"></a>Suchen nach Symptomen
Benutzer melden so gut wie keine Probleme, da MAM ein Tool zum Schutz von Daten ist. Liegt ein Problem mit der MAM-Konfiguration vor, erhält der Benutzer uneingeschränkten Zugriff, so wie es ohne MAM der Fall wäre, und er würde nicht bemerken, dass es ein Problem gibt. Aus diesem Grund wird empfohlen, dass Sie Ihre MAM-Konfiguration überprüfen, indem Sie Ihre MAM-Richtlinien mit einer kleinen Gruppe von Benutzern steuern, die bewusst die MAM-Einschränkungen testen können.


### <a name="what-to-check"></a>Was soll überprüft werden?

Wenn der Test zeigt, dass das Verhalten Ihrer MAM-Richtlinie nicht wie erwartet ist, empfiehlt es sich, folgende Punkte zu überprüfen:

- Sind die Benutzer für MAM lizenziert?
- Sind die Benutzer für Office 365 lizenziert?
- Der Status der MAM-Apps eines jeden Benutzers. Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**.

#### <a name="user-mam-status"></a>MAM-Status des Benutzers
1. Wählen Sie im Azure-Portal **Mobile Anwendungsverwaltung mit Intune** > **Einstellungen** > **App-Verwaltung** > **Alle Einstellungen** > **App-Berichterstellung nach Benutzer** > **Benutzer**.

2. Wählen Sie einen Benutzer aus der Liste aus, oder suchen Sie einen Benutzer und wählen Sie Ihn aus. Wählen Sie anschließend **Benutzer auswählen** aus. Am oberen Rand der Spalte **App-Berichterstellung** sehen Sie, ob der Benutzer für die MAM lizenziert ist. Nachfolgend sehen Sie, ob der Benutzer für Office 365 und den App-Status aller Geräte des Benutzers lizenziert ist.

![App-Statuts für MAM](../media/ts-mam-user-apps.png)

### <a name="what-to-do"></a>Aktion
Hier sind die Aktionen, die basierend auf den Benutzerstatus durchgeführt werden müssen:

- Wenn der Benutzer nicht für MAM lizenziert ist, weisen Sie dem Benutzer eine Intune-Lizenz zu, wie unter [Verwalten von Intune-Lizenzen](/intune/setup-steps) beschrieben.
- Wenn der Benutzer nicht für Office 365 lizenziert ist, rufen Sie eine Lizenz für den Benutzer ab.
- Wenn die App des Benutzer als **Nicht eingecheckt** aufgelistet ist, überprüfen Sie, ob Sie die MAM-Richtlinie für diese App ordnungsgemäß konfiguriert haben.
- Stellen Sie sicher, dass diese Bedingungen auf alle Benutzer angewendet werden, auf die die MAM Richtlinien angewendet werden sollen.

### <a name="see-also"></a>Siehe auch
[Vorbereiten der Konfiguration von Verwaltungsrichtlinien für mobile Apps mit Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

[Schützen von App-Daten mithilfe der Verwaltungsrichtlinien für mobile Apps mit Microsoft Intune](../deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
