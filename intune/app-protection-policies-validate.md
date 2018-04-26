---
title: Überprüfen der Einrichtung von App-Schutzrichtlinien
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie überprüfen können, ob Ihre App-Schutzrichtlinie ordnungsgemäß eingerichtet wurde und funktioniert.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6ea79a2e177b8a4e85454140c7efb9172defe5b6
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-validate-your-app-protection-policy-setup"></a>Überprüfen der Einrichtung von App-Schutzrichtlinien

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Überprüfen Sie, ob Ihre App-Schutzrichtlinie ordnungsgemäß eingerichtet wurde und funktioniert. Diese Anleitung gilt für App-Schutzrichtlinien im Azure-Portal.

### <a name="checking-for-symptoms"></a>Suchen nach Symptomen
Benutzer melden so gut wie keine Probleme, da der App-Schutz ein Tool zum Schutz von Daten ist. Liegt ein Problem mit der Konfiguration für den App-Schutz vor, erhält der Benutzer uneingeschränkten Zugriff, wie es auch ohne App-Schutz der Fall wäre, sodass ihm nicht bewusst wäre, dass es ein Problem gibt. Aus diesem Grund wird empfohlen, dass Sie die Konfiguration für Ihren App-Schutz überprüfen, indem Sie Ihre App-Schutzrichtlinien mit einer kleinen Gruppe von Benutzern steuern, die bewusst die Einschränkungen des App-Schutzes testen können.


### <a name="what-to-check"></a>Was soll überprüft werden?

Wenn der Test zeigt, dass das Verhalten Ihrer App-Schutzrichtlinie nicht wie erwartet ist, empfiehlt es sich, folgende Punkte zu überprüfen:

- Sind die Benutzer für den App-Schutz lizenziert?
- Sind die Benutzer für Office 365 lizenziert?
- Welchen Status haben die App-Schutz-Apps der einzelnen Benutzers? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**.

#### <a name="user-app-protection-status"></a>Schutzstatus der Benutzer-App
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Monitoring + Management**.
1. Wählen Sie **Apps verwalten** > **Überwachen** >  **Status des App-Schutzes** > **Zugewiesene Benutzer** aus.

2. Wählen Sie einen Benutzer aus der Liste aus, oder suchen Sie einen Benutzer und wählen Sie Ihn aus. Wählen Sie anschließend **Benutzer auswählen** aus. Am Anfang der Spalte **App-Berichterstellung** können Sie sehen, ob der Benutzer für den App-Schutz lizenziert ist. Zudem können Sie sehen, ob der Benutzer für Office 365 und den App-Status aller Geräte des Benutzers lizenziert ist.



### <a name="what-to-do"></a>Aktion
Hier sind die Aktionen, die basierend auf den Benutzerstatus durchgeführt werden müssen:

- Wenn der Benutzer nicht für den App-Schutz lizenziert ist, weisen Sie dem Benutzer eine Intune-Lizenz zu.
- Wenn der Benutzer nicht für Office 365 lizenziert ist, rufen Sie eine Lizenz für den Benutzer ab.
- Wenn die App eines Benutzer als **Nicht eingecheckt** aufgelistet ist, überprüfen Sie, ob Sie die App-Schutzrichtlinie für diese App ordnungsgemäß konfiguriert haben.
- Stellen Sie sicher, dass diese Bedingungen auf alle Benutzer angewendet werden, für die die App-Schutzrichtlinien gelten sollen.

### <a name="see-also"></a>Siehe auch

[Was sind Intune-App-Schutzrichtlinien?](app-protection-policies.md)
