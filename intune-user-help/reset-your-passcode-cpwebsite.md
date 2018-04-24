---
title: Zurücksetzen Ihrer Kennung über die Website des Unternehmensportals | Microsoft-Dokumentation
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 06/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 45b087b9617b783517f8296f1726891392764d5f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>So setzen Sie Ihre Kennung über die Unternehmensportalwebsite zurück

Wenn Sie die PIN oder das Kennwort für ein bei Intune registriertes Gerät verloren haben, können Sie die PIN bzw. das Kennwort über die [Unternehmensportalwebsite](https://portal.manage.microsoft.com#HelpDeskDialog) zurücksetzen. Sie können die Unternehmensportal-Website verwenden, um Computer und Geräte zu verwalten, die Sie bei Intune registriert haben. Außerdem können Sie auf dieser die meisten der Aufgaben ausführen, die auch über Ihre Unternehmensportal-App zur Verfügung stehen.

> [!NOTE]
> Es ist möglich, dass Sie die Schaltfläche „Kennung zurücksetzen“ auf der Unternehmensportalwebsite nicht sehen, wenn Sie ein beim Unternehmen registriertes Gerät verwenden. Wenden Sie sich in diesem Fall an den Support Ihres Unternehmens, um die Kennung zurücksetzen zu lassen.

So setzen Sie Ihre Kennung zurück

1. Tippen Sie auf der [Unternehmensportalwebsite](https://portal.manage.microsoft.com#HelpDeskDialog) auf die Schaltfläche __Menü__ ![Eine kleine Abbildung der Menü-Schaltfläche, drei horizontal übereinandergestapelte Balken.](/intune/media/CP_hamburger_menu.png), und wählen Sie dann __Meine Geräte__ aus.

2. Wählen Sie auf der Seite __Meine Geräte__ den Namen des Geräts aus, dessen Kennung Sie zurücksetzen möchten.

   ![Ein Screenshot der Seite „Meine Geräte“ mit mehreren nicht identifizierten Geräten oberhalb der Banneraufforderung, nicht aufgelistete Geräte zu registrieren oder nicht identifizierte Geräte zu identifizieren.](./media/macOS_enroll_002_tap_here_banner.png)

3. Das Gerät wird in einem Popupfenster geöffnet. Wählen Sie die Schaltfläche **Kennung zurücksetzen** aus.

   ![Alle Optionen für ein ausgewähltes Gerät auf der Unternehmensportalwebsite, darunter „Umbenennen“, „Entfernen“, „Gerät zurücksetzen“, „Kennung zurücksetzen“ und „Remotesperre“. ](./media/iwp-screen-with-all-options.png)

4. Daraufhin öffnet sich ein Banner, in dem Sie dazu aufgefordert werden, zu bestätigen, dass Sie Ihre Kennung zurücksetzen möchten, und dass Ihr Gerät Sie nach dem Vorgang abmeldet. Danach müssen Sie 5 Minuten warten, bevor Sie sich wieder anmelden können.

   ![Das Banner „Kennung zurücksetzen“ mit der Warnung bezüglich des Zurücksetzens der Kennung und der Abmeldung des Benutzers. Die Schaltflächen für Benutzereingaben sind „Abmelden“ und „Abbrechen“.](./media/iwp-reset-passcode-popup.png)

5. Wählen Sie **Abmelden** aus; danach erhalten Sie eine letzte Meldung, die Sie über die Entfernung der Kennung von dem Gerät informiert. Wenn Sie das Gerät nicht bei sich haben, entfernen Sie die Kennung nicht; ansonsten können Personen, die physisch Zugang zu Ihrem Gerät haben, auf die meisten – persönlichen und geschäftlichen – Daten auf Ihrem Gerät zugreifen. 

   ![Das zweite Banner „Kennung zurücksetzen“ mit der Warnung bezüglich des Zurücksetzens der Kennung und des Entfernens der Kennung von dem Gerät. Außerdem informiert es Sie darüber, wie Sie eine neue Kennung in den Geräteeinstellungen festlegen können.](./media/iwp-reset-passcode-2nd-popup.png)

   Unterschiedliche Geräte verfügen über unterschiedliche Arten von Kennungen.

   **Android**: Entfernt die vorhandene Kennung und erstellt eine vorübergehende Kennung mit Buchstaben und Zahlen 
  
   > [!NOTE]
   > Für Geräte mit Android 7.0 und höher kann die Kennung nicht zurückgesetzt werden. Setzen Sie diese Geräte in diesem Fall auf die Werkseinstellungen zurück, wenn Sie Ihre Kennung vergessen haben.

   **iOS**: Entfernt die aktuelle Kennung und erstellt keine neue temporäre Kennung. Wenn Sie den Touch-ID-Fingerabdruckscanner zum Öffnen Ihres Geräts oder zum Abwickeln von Käufen nutzen, müssen Sie diesen erneut einrichten.

   **Windows 10 Mobile**: Entfernt die vorhandene Kennung und erstellt eine vorübergehende Kennung mit Buchstaben und Zahlen. Wenn Sie die Windows Hello-Gesichtserkennung zum Anmelden verwenden, wird diese noch immer unterstützt.
    
   **Windows Phone 8.1**: Entfernt die vorhandene Kennung und erstellt eine vorübergehende Kennung mit Zahlen

   Bei Android- und Windows-Geräten wird das temporäre Kennwort unter **Gerätedetails** angezeigt. 

6. Entsperren Sie Ihr Gerät, und legen Sie eine neue Kennung fest, oder ändern Sie die temporäre Kennung auf Ihrem Gerät unter **Einstellungen**.

Um eine Benachrichtigung anzuzeigen, die bestätigt, dass Ihr Kennwort erfolgreich zurückgesetzt wurde, klicken Sie auf das Benachrichtigungskennzeichen oben rechts auf der Unternehmensportal-Website.

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://portal.manage.microsoft.com#HelpDeskDialog).
