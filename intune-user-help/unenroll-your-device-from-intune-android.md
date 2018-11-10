---
title: Entfernen der Registrierung Ihres Android-Geräts aus Intune | Microsoft-Dokumentation
description: Beschreibt das Aufheben der Registrierung eines Android-Geräts bei Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: d932005c955afed7f16e9766b559b77b2cd43182
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959484"
---
# <a name="unenroll-your-android-device-from-management"></a>Aufheben der Registrierung Ihres Android-Geräts für die Verwaltung  

Entfernen Sie Android-Geräte, deren Registrierung aufgehoben wurde, damit diese nicht mehr von Ihrer Organisation verwaltet werden. In diesem Artikel wird beschrieben, wie Sie das Gerät aus der Unternehmensportal-App entfernen. Es hat folgende Konsequenzen, wenn das Gerät entfernt wird:  

* Dem Gerät wird der Zugriff auf die geschützten Daten und Ressourcen Ihrer Organisation entzogen.
* Das Gerät wird nicht mehr im Unternehmensportal angezeigt.
* Sie können keine Apps mehr über das Unternehmensportal installieren.
* Alle Einstellungen, die beim Hinzufügen des Geräts auf diesem geändert wurden, z.B. das Deaktivieren der Kamera oder die Anforderung einer bestimmten Kennwortlänge, werden unwirksam.  

1. Tippen Sie im Unternehmensportal auf die drei vertikal angeordneten Punkte in der oberen rechten Ecke. Dann öffnet sich das Menü „Aktion“.

   ![Ein Bild der Android-Unternehmensportal-App mit geöffnetem Aktionsmenü oben rechts. Die neue Option „Unternehmensportal entfernen“ steht als die dritte Option unter „Mein Profil“ und „Einstellungen“ und über „Nutzungsbedingungen“, „Hilfe und Feedback“ und „Info“ zur Verfügung.](./media/android_remove_cp_menu_action_after_1705.png)

2. Tippen Sie auf **Unternehmensportal entfernen**.  

3. Dann wird eine Nachricht mit Informationen darüber angezeigt, was geschieht, wenn Sie die Registrierung Ihres Geräts aufheben. Tippen Sie auf **OK**, um zu bestätigen, dass Sie das Gerät aus dem Unternehmensportal entfernen möchten.

   ![Ein Bild mit dem Bestätigungsdialogfeld, das nach der Auswahl der neuen Option „Unternehmensportal entfernen“ im Aktionsmenü verfügbar ist. Das Dialogfeld informiert den Benutzer über Folgendes: „by removing company portal, your device will no longer be managed by your company support and may remove access to company data, company apps, and company email.“ (Wenn Sie das Unternehmensportal entfernen, wird Ihr Gerät nicht länger durch den Support Ihres Unternehmens verwaltet, und der Zugriff auf Unternehmensdaten, Unternehmens-Apps und Unternehmens-E-Mails wird möglicherweise beendet.). Anschließend muss der Benutzer bestätigen, dass er die Unternehmensportal-App entfernen möchte, indem er „Ja“ auswählt.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>Entfernen von Daten, die von der Unternehmensportal-App gesammelt wurden  

So entfernen Sie alle Daten, die die Unternehmensportal-App für Android auf Ihrem Gerät gespeichert hat:

-   Klicken Sie zum Löschen von App-Daten auf die entsprechende App und anschließend auf die Schaltfläche „Daten löschen“.
-   Löschen Sie den Ordner „\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal“.

## <a name="uninstall-the-company-portal-app"></a>Deinstallieren der Unternehmensportal-App  
Das Unternehmensportal ist eine App zur Geräteverwaltung. Daher kann diese erst deinstalliert werden, wenn Sie [die Registrierung für die Verwaltung des Geräts aufheben](unenroll-your-device-from-intune-android.md#unenroll-your-android-device-from-management). Wenn dies geschehen ist, tippen Sie auf das Symbol für die Unternehmensportal-App und halten Sie dieses so lange gedrückt, bis die Option **Deinstallieren** angezeigt wird. Tippen Sie auf **Deinstallieren**, um die App von Ihrem Gerät zu entfernen.  

Stattdessen können Sie auch auf **Einstellungen** > **Apps** > **Unternehmensportal** > **Deinstallieren** tippen.  

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportalwebsite](https://go.microsoft.com/fwlink/?linkid=2010980).
