---
title: Entfernen Ihres iOS-Geräts aus Intune | Microsoft-Dokumentation
description: Beschreibt das Entfernen eines iOS-Geräts aus Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 28914db1-3e62-45f5-9632-b0d2a808a44d
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 0a90cace32edb33293ba0b0b89d272465ea32418
ms.sourcegitcommit: 07528df71460589522a2e1b3e5f9ed63eb773eea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34547487"
---
# <a name="remove-your-ios-device-from-intune"></a>Entfernen Ihres iOS-Geräts aus Intune

Wenn Sie Ihr iOS-Gerät aus Intune entfernen, kann Ihr Gerät nicht mehr auf Unternehmensressourcen zugreifen und wird nicht mehr über Intune verwaltet.


## <a name="removing-the-device-from-my-devices"></a>Entfernen Ihres Geräts aus „Eigene Geräte“

Befolgen Sie zum Entfernen Ihres Geräts aus Intune die hier oder in diesem Video beschriebenen Schritte:


1.  Tippen Sie in der Unternehmensportal-App auf **Geräte**. Wählen Sie das Gerät aus, das entfernt werden soll. Wenn Sie nur ein Gerät besitzen, wird Ihnen direkt der Bildschirm „Gerätedetails“ angezeigt, wenn Sie auf **Geräte** tippen.

2.  Tippen Sie neben **Umbenennen** auf die Auslassungspunkte und dann auf **Gerät entfernen** > **Entfernen**.  

    |![Screenshot des Bildschirms „Geräte“ der Unternehmensportal-App, der die Optionen anzeigt, nachdem der Benutzer auf „Entfernen“ getippt hat Zeigt die Schaltflächen „Gerät entfernen“, „Zurück auf Werkseinstellungen“ und „Abbrechen“](/intune-user-help/media/cp_ios_unenroll_after_1804_001.png)|

    |![Screenshot des Bildschirms „Geräte“ der Unternehmensportal-App, der die Optionen anzeigt, nachdem der Benutzer auf „Gerät entfernen“ getippt hat Zeigt die rot hervorgehobene Schaltfläche „Entfernen“ und die blau hervorgehobenen Schaltflächen „Weitere Informationen“ und „Abbrechen“](/intune-user-help/media/cp_ios_unenroll_after_1804_002.png)|


  Wenn Sie die Registrierung Ihres Geräts bei Intune aufheben passiert Folgendes:

  -   Das Gerät wird nicht mehr im Unternehmensportal angezeigt.

  -   Sie können keine Apps mehr über das Unternehmensportal installieren.

  -   Alle Einstellungen, die beim Hinzufügen des Geräts auf diesem geändert wurden, z. B. das Deaktivieren der Kamera oder die Anforderung einer bestimmten Kennwortlänge, werden unwirksam.

  -   Unter Umständen haben Sie auf dem Gerät keinen Zugriff mehr auf einige Unternehmensressourcen, z. B. Dateifreigaben oder interne Websites.

  -   Sie können keine Unternehmens-Apps und Unternehmensdaten mehr auf dem Gerät verwenden.

  -   Möglicherweise können Sie keine Verbindung mehr zum Unternehmensnetzwerk über WiFi oder ein virtuelles privates Netzwerk (VPN) herstellen.

  -   Unternehmens-E-Mail-Profile werden vom Gerät entfernt.

  -   Geräte, die nur für E-Mail konfiguriert sind, werden nicht mehr in der Unternehmensportal-App oder auf der Unternehmensportal-Website angezeigt.
  
  -   Apps werden deinstalliert. Daten von Unternehmens-Apps werden entfernt.

## <a name="removing-data-collected-by-the-company-portal-app"></a>Entfernen von Daten, die von der Unternehmensportal-App gesammelt wurden

Das Unternehmensportal speichert lokale Daten an drei verschiedenen Stellen auf Ihrem Gerät.

-   **Informationsprotokolle:** Daten zu Standardaktivitäten von Apps, die Microsoft sammelt. Dazu zählt beispielsweise, wie lang die App geöffnet war oder ob sie abgestürzt ist. Diese werden automatisch gelöscht, wenn Sie das Gerät aus dem Unternehmensportal löschen.

-   **App Analytics:** Standardprogramm für die Aktivitätsdaten von App-Abstürzen, die Apple sammelt Diese Informationen können nur entfernt werden, wenn Sie Ihr Gerät auf die Werkseinstellungen zurücksetzen. Dadurch werden alle persönlichen Informationen auf Ihrem Gerät gelöscht. Öffnen Sie hierzu **Einstellungen** > **Allgemein** > **Zurücksetzen** > **Gesamten Inhalt und alle Einstellungen löschen**.

-   **Schlüsselbund:** Ihr Gerät speichert Ihre Kennwörter und andere Informationen, die für Anmeldungen verwendet werden, in Ihrem Schlüsselbund. Microsoft-Apps geben Ihre Anmeldeinformationen für alle von Microsoft entwickelten Apps frei, die auf Ihrem Gerät installiert sind, einschließlich Microsoft Outlook und Microsoft Authenticator. Wie bei App Analytics können diese Informationen nur entfernt werden, wenn Sie Ihr Gerät auf die Werkseinstellungen zurücksetzen. Dadurch werden alle persönlichen Informationen auf Ihrem Gerät gelöscht. Öffnen Sie hierzu **Einstellungen** > **Allgemein** > **Zurücksetzen** > **Gesamten Inhalt und alle Einstellungen löschen**.


Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://portal.manage.microsoft.com#HelpDeskDialog).
