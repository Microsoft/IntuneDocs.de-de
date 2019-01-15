---
title: Entfernen der Registrierung Ihres Android-Geräts aus Intune | Microsoft-Dokumentation
description: Entfernen Ihres Android-Geräts aus dem Intune-Unternehmensportal
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/04/2019
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
ms.openlocfilehash: 75b26e178badbaa7905199eb91490134d2b72ba9
ms.sourcegitcommit: 61ed365f7f8826451c41bcab5e19bef97b5a3c72
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2019
ms.locfileid: "54057337"
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
Das Unternehmensportal ist eine App für die Geräteverwaltung. Daher kann diese erst deinstalliert werden, wenn Sie [die Registrierung für die Verwaltung des Geräts aufheben](unenroll-your-device-from-intune-android.md#unenroll-your-android-device-from-management). Wenn dies geschehen ist, tippen Sie auf das Symbol für die Unternehmensportal-App und halten Sie dieses so lange gedrückt, bis die Option **Deinstallieren** angezeigt wird. Tippen Sie auf **Deinstallieren**, um die App von Ihrem Gerät zu entfernen.  

Stattdessen können Sie auch auf **Einstellungen** > **Apps** > **Unternehmensportal** > **Deinstallieren** tippen.  

### <a name="remove-company-portal-app-as-device-administrator"></a>Entfernen der Unternehmensportal-App als Geräteadministrator  
Als letzte Alternative können Sie die App von Ihrem Gerät deinstallieren, indem Sie sie als Geräteadministrator entfernen.  

Wenn Sie ein unternehmenseigenes Gerät besitzen, setzt Ihre Organisation möglicherweise voraus, dass das Unternehmensportal immer auf dem Gerät installiert ist. Wenn Sie es deinstallieren, könnten Sie den Zugriff auf geschützte Unternehmensressourcen wie E-Mails, Apps, WLAN-Netzwerke oder VPNs verlieren, bis die App neu installiert wird. Weitere Informationen zum Installieren, Aktualisieren und Entfernen erforderlicher Apps finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](https://docs.microsoft.com/intune/apps-add#apps-that-are-added-automatically-by-intune).  

Führen Sie die folgenden Schritte aus, um das Unternehmensportal als Geräteadministrator zu deaktivieren. Die tatsächlichen Namen der einzelnen Einstellungen können je nach Android-Gerät variieren.  

**Schritte für Android (Option 1):**  
1. Klicken Sie auf **Einstellungen** > **Sicherheit** > **Andere Sicherheitseinstellungen** > **Geräteadministratoren**.  
2. Deaktivieren Sie die Option **Unternehmensportal**.  

**Schritte für Android (Option 2):**  
1. Klicken Sie auf **Einstellungen** > **Sperrbildschirm und Sicherheit** > **Andere Sicherheitseinstellungen** > **Geräteadministratoren**.  
2. Deaktivieren Sie die Option **Unternehmensportal**.    

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportalwebsite](https://go.microsoft.com/fwlink/?linkid=2010980).
