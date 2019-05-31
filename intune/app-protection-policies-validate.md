---
title: Überprüfen der Einrichtung von App-Schutzrichtlinien
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie überprüfen können, ob Ihre App-Schutzrichtlinie ordnungsgemäß eingerichtet wurde und in Microsoft Intune funktioniert.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 760ff85bc31cf66e66a3bf98f7da22d5ce48eee0
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569440"
---
# <a name="how-to-validate-your-app-protection-policy-setup-in-microsoft-intune"></a>Überprüfen der Einrichtung von App-Schutzrichtlinien in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Überprüfen Sie, ob Ihre App-Schutzrichtlinie ordnungsgemäß eingerichtet wurde und funktioniert. Diese Anleitung gilt für App-Schutzrichtlinien im Azure-Portal.

## <a name="checking-for-symptoms"></a>Suchen nach Symptomen
Benutzer melden so gut wie keine Probleme, da der App-Schutz ein Tool zum Schutz von Daten ist. Liegt ein Problem mit der Konfiguration für den App-Schutz vor, erhält der Benutzer uneingeschränkten Zugriff, wie es auch ohne App-Schutz der Fall wäre. So wäre ihm nicht bewusst, dass es ein Problem gibt. Aus diesem Grund wird empfohlen, dass Sie die Konfiguration für Ihren App-Schutz überprüfen, indem Sie Ihre App-Schutzrichtlinien mit einer kleinen Gruppe von Benutzern steuern, die bewusst die Einschränkungen des App-Schutzes testen können.

## <a name="what-to-check"></a>Was soll überprüft werden?

Wenn der Test zeigt, dass das Verhalten Ihrer App-Schutzrichtlinie nicht wie erwartet funktioniert, überprüfen Sie folgende Punkte:

- Sind die Benutzer für den App-Schutz lizenziert?
- Sind die Benutzer für Office 365 lizenziert?
- Weisen die Apps zum Schützen von Apps der einzelnen Benutzer den erwarteten Status auf? Die möglichen Statuswerte für die apps sind **Eingecheckt** und **Nicht eingecheckt**.

### <a name="user-app-protection-status"></a>Schutzstatus der Benutzer-App
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Klicken Sie auf **Client apps** (Client-Apps) >  **Status des App-Schutzes** und dann auf die Kachel **Zugewiesene Benutzer**. 
4. Klicken Sie auf der Seite **App-Berichterstellung** auf **Benutzer auswählen**, um eine Liste von Benutzern und Gruppen anzuzeigen. 
5. Suchen Sie einen Benutzer, und wählen Sie ihn aus. Klicken Sie anschließend auf **Benutzer auswählen**. Im oberen Bereich von **App-Berichterstellung** können Sie sehen, ob der Benutzer für den App-Schutz lizenziert ist. Zudem können Sie sehen, ob der Benutzer eine Lizenz für Office 365 und den App-Status aller Geräte des Benutzers besitzt.

## <a name="what-to-do"></a>Aktion
Hier sind die Aktionen, die basierend auf den Benutzerstatus durchgeführt werden müssen:

- Wenn der Benutzer nicht für den App-Schutz lizenziert ist, weisen Sie dem Benutzer eine [Intune-Lizenz](licenses.md) zu.
- Wenn der Benutzer nicht für Office 365 lizenziert ist, beziehen Sie eine [Lizenz](licenses.md) für den Benutzer.
- Wenn die App eines Benutzer als **Nicht eingecheckt** aufgelistet ist, überprüfen Sie, ob Sie die [App-Schutzrichtlinie](app-protection-policies-validate.md) für diese App ordnungsgemäß konfiguriert haben.
- Stellen Sie sicher, dass diese Bedingungen auf alle Benutzer angewendet werden, für die die [App-Schutzrichtlinien](app-protection-policies-monitor.md) gelten sollen.

## <a name="see-also"></a>Siehe auch

- [Was sind Intune-App-Schutzrichtlinien?](app-protection-policies.md)
- [Licenses that include Intune (Lizenzen, die Intune enthalten)](licenses.md)
- [Zuweisen von Lizenzen zu Benutzern, damit sie ihre Geräte bei Intune registrieren können](licenses-assign.md)
- [Überprüfen der Einrichtung von App-Schutzrichtlinien](app-protection-policies-validate.md)
- [Überwachen von App-Schutzrichtlinien](app-protection-policies-monitor.md)

