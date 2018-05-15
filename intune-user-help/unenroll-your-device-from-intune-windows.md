---
title: Entfernen Ihres Windows-Geräts aus Intune | Microsoft-Dokumentation
description: Beschreibt das Entfernen eines Windows-Geräts aus Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 89a69f7d5cda31658cc9faf068a2a37698fdd93c
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="remove-your-windows-device-from-intune"></a>Entfernen Ihres Windows-Geräts aus Intune

Wenn Ihr Gerät in Intune registriert ist, aber Sie Ihr Windows-Gerät nicht mehr dafür verwenden möchten, auf geschäftliche E-Mails, Schul- und Uni-E-Mails oder andere Ressourcen zuzugreifen, müssen Sie Ihr Gerät aus der Verwaltung entfernen. Nachdem Sie Ihr Gerät aus Intune entfernt haben, können Sie nicht mehr auf diese Ressourcen zugreifen. Weitere Informationen dazu, was beim Entfernen Ihres Geräts aus der Verwaltung geschieht, finden Sie unter [Was geschieht, wenn Sie die Registrierung Ihres Geräts bei Intune aufheben?](what-happens-if-you-unenroll-your-device-from-intune-windows.md).

## <a name="remove-your-windows-10-device"></a>Entfernen Ihres Windows 10-Geräts

1.  Tippen Sie in Ihrer Apps-Liste auf die App **Unternehmensportal** .

2.  Melden Sie sich mit Ihren Geschäfts-, Schul- oder Unianmeldeinformationen an.

3.  Wählen Sie in **Meine Geräte**das Gerät aus, dessen Registrierung Sie aufheben möchten.

4.  Tippen Sie auf **Entfernen** &gt; **Entfernen**.

## <a name="remove-your-windows-81-computer"></a>Entfernen Ihres Windows 8.1-Computers

1.  Navigieren Sie zu **PC-Einstellungen** &gt; **Netzwerk** &gt; **Arbeitsplatz**.

2.  Wählen Sie unter **Arbeitsplatzeinbindung** **Leave** (Verlassen) aus.

3.  Wählen Sie unter **Turn on device management** (Geräteverwaltung aktivieren) **Turn off** (Deaktivieren) aus.

4.  Wählen Sie im sich öffnenden Popupfenster **Turn off** (Deaktivieren) aus.

## <a name="remove-your-windows-phone-81-mobile-device"></a>Entfernen Ihres mobilen Windows Phone 8.1-Geräts

1.  Tippen Sie auf **Einstellungen** &gt; **Arbeitsplatz**.

2.  Tippen Sie auf das Arbeitsplatzkonto, für das Sie die Registrierung aufheben möchten.

3.  Tippen Sie am unteren Bildschirmrand auf **Löschen**.

4.  Tippen Sie im Dialogfeld **Konto löschen** auf **Löschen**.

## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Entfernen Ihrer persönlichen Informationen nach dem Entfernen des Unternehmensportals

Es gibt zwei Arten von Daten, die das Unternehmensportal auf Ihrem Windows-Gerät speichert:

-   **Diagnoseprotokolle:** Daten zu Standardaktivitäten von Apps, die Microsoft sammelt. Dazu zählt beispielsweise, wie lang die App geöffnet war oder ob sie abgestürzt ist. Diese werden automatisch gelöscht, wenn die Unternehmensportal-App deinstalliert wird.
-   **Anwendungscache:** Dort werden bestimmte Unterstützungsdateien gespeichert, die erforderlich sind, damit die App funktioniert, z.B. Symbole und Einstellungen.

Sie müssen einige Schritte durchführen, um diese Informationen vollständig zu löschen.

### <a name="uninstall-the-company-portal"></a>Deinstallieren des Unternehmensportals  

Durch das [Deinstallieren einer Unternehmensportal-App](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) werden einige der App-Daten entfernt, die auf Ihrem Gerät gespeichert sind.  

### <a name="reset-the-company-portal"></a>Zurücksetzen des Unternehmensportals

Sie können die restlichen Daten der Unternehmensportal-App zurücksetzen, indem Sie die App in den Einstellungen zurücksetzen. Öffnen Sie **Einstellungen** > **Apps und Features** > **Unternehmensportal** > **Erweiterte Optionen** > **Zurücksetzen**.

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://portal.manage.microsoft.com#HelpDeskDialog).
