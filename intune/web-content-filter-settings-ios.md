---
title: Filtereinstellungen für Webinhalte für iOS-Geräte in Microsoft Intune
titlesuffix: ''
description: Informationen zu den Einstellungen in Microsoft Intune, die Sie verwenden können, um den Zugriff von iOS-Geräten auf Websites zulassen und blockieren können.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1c8eb121b3db52f0fdfc30d7d8dff7ef0f7bf97b
ms.sourcegitcommit: f21287c66dd5559688f08bd98b6c976a0dea055d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2018
ms.locfileid: "34456349"
---
# <a name="web-content-filter-settings-for-ios-devices"></a>Filtereinstellungen für Webinhalte für iOS-Geräte

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel werden die Microsoft Intune-Einstellungen dargestellt, die Sie verwenden können, um auf iOS-Geräten den URL-Zugriff der Browser kontrollieren zu können.

Ihnen stehen zwei Verfahren zum Konfigurieren von URLs zur Verfügung:

- **Konfigurieren von URLs**: Verwenden Sie den integrierten Webfilter von Apple, der nach nicht jugendfreien Inhalten wie Anzüglichkeiten oder Obszönitäten sucht. Diese Funktion bewertet jede Webseite, sobald diese geladen ist, und versucht, ungeeignete Inhalte zu identifizieren und zu blockieren. Darüber hinaus können Sie URLs konfigurieren, die vom Filter nicht geprüft werden. Sie können auch URLs konfigurieren, die unabhängig von den Filtereinstellungen blockiert werden.

- **Nur bestimmte Websites** (nur für den Safari-Webbrowser): Diese URLs werden zu den Lesezeichen des Safari-Browsers hinzugefügt. Benutzer dürfen **nur** diese Websites besuchen, der Zugriff auf andere Websites ist nicht möglich. Verwenden Sie diese Option nur, wenn Sie genau wissen, auf welche URLs Benutzer zugreifen können.
Wenn Sie hier keine URLs angeben, können Endbenutzer keine Websites außer „microsoft.com“, „microsoft.net“ und „apple.com“ öffnen.

## <a name="get-started"></a>Erste Schritte

1. Klicken Sie auf der Seite „Gerätefeatures“ auf die Option **Web Content Filter (supervised only)** (Webinhaltsfilter (nur überwacht)).
2. Klicken Sie auf der Seite **Webinhaltsfilter** auf den **Filtertyp**, den Sie konfigurieren möchten:
    - **Nicht konfiguriert**: Es wird keine Filterung ausgeführt.
    - **Konfigurieren von URLs**
    - **Nur bestimmte Websites**
3. Führen Sie danach je nach verwendetem Filtertyp eines der unten genannten Verfahren aus.


## <a name="configure-urls"></a>Konfigurieren von URLs

1. Wählen Sie auf der Seite **Webinhaltsfilter** bei Bedarf eine der folgenden Einstellungen aus:
   - **Zulässige URLs:** Geben Sie auf der Seite **Zulässige URLs** die URLs ein, die Sie zulassen möchten (der Apple-Webfilter wird dadurch umgangen), und drücken Sie nach jeder URL die EINGABETASTE.
     > [!NOTE]
     > Bei den URLs, die Sie hier angeben, handelt es sich um die, die nicht dem Apple-Webfilter unterliegen sollen. Diese URLs stellen keine Liste der einzigen zulässigen Websites dar. Wenn Sie dies wünschen, verwenden Sie **Nur bestimmte Websites**.

   - **Blockierte URLs:** Geben Sie auf der Seite **Blockierte URLs** die URLs ein, die Sie blockieren möchten (unabhängig von den Apple-Webfiltereinstellungen), und drücken Sie nach jeder URL die EINGABETASTE.
2. Klicken Sie zum Abschluss auf **OK**.


## <a name="specific-websites-only"></a>Nur bestimmte Websites

1. Konfigurieren Sie im Bereich **Webinhaltsfilter** für jede Website, die Sie zulassen möchten, die folgenden Einstellungen:
    - **URL**: Geben Sie die URL der Website ein, die Sie zulassen möchten, z.B. **http://www.contoso.com**.
    - **Pfad als Lesezeichen speichern**: Geben Sie den Pfad ein, in dem Sie Lesezeichen speichern möchten, z.B. **/Contoso/Business Apps**. Wenn Sie keinen Pfad angeben, wird das Lesezeichen zum Standardordner für Lesezeichen auf dem Gerät hinzugefügt.
    - **Titel**: Geben Sie einen beschreibenden Titel für das Lesezeichen ein.
2. Klicken Sie auf **Hinzufügen**, wenn Sie die Informationen für die jeweilige Website eingegeben haben.
3. Klicken Sie zum Abschluss auf **OK**.

> [!IMPORTANT]
> Die folgenden URLs werden von Intune automatisch zugelassen.
> - <www.microsoft.com>
> - <www.microsoft.net>
> - <www.apple.com>

## <a name="finish-up"></a>Fertig stellen

Klicken Sie auf **OK**, um zum Bereich **Profil erstellen** zurückzukehren, und klicken Sie dann auf **Erstellen**.

## <a name="next-steps"></a>Nächste Schritte

Sie können nun das Geräteprofil den von Ihnen ausgewählten Gruppen zuweisen. Weitere Informationen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).
