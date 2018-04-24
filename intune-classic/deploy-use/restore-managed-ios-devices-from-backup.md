---
title: Wiederherstellen von durch Intune verwalteten iOS-Geräten aus einer Sicherung
description: Stellen Sie einen Leitfaden für Endbenutzer bereit, der erklärt, wie sie ihre Geräte nach der Wiederherstellung aus einer Sicherung erneut registrieren können.
keywords: wiederherstellen, verwaltet, iOS
author: lenewsad
ms.author: lanewsad
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2c2a35a7faa022ab2b9b095d4a08075e1c338c70
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="restore-intune-managed-ios-devices-from-backup"></a>Wiederherstellen von durch Intune verwalteten iOS-Geräten aus einer Sicherung

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Es werden Fälle auftreten, in denen Sie oder Ihre Benutzer ein iOS-Gerät aus einer Sicherung wiederherstellen müssen, z.B. wenn ein Benutzer ein neues Gerät erhält. In diesem Thema werden zusätzliche Schritte erläutert, die Sie möglicherweise durchführen müssen, um die Intune-Verwaltung nach dem Wiederherstellen eines Geräts einzurichten.

## <a name="restoring-backups-onto-the-same-device"></a>Wiederherstellen von Sicherungen auf dem gleichen Gerät

Wenn die Sicherung auf dem gleichen Gerät wiederhergestellt wird, wird auch der Registrierungsstatus auf diesem Gerät wiederhergestellt. Es sind keine weiteren Aktionen erforderlich.

## <a name="restoring-backups-onto-different-devices"></a>Wiederherstellen von Sicherungen auf verschiedenen Geräten

Wenn die Sicherung auf einem anderen Gerät wiederhergestellt wird, wird der Registrierungsstatus nicht automatisch auf dem neuen Gerät wiederhergestellt. Benutzer müssen die Standardregistrierungsschritte in der Unternehmensportal-App Version 2.1.22 oder höher durchführen, um [ihr iOS-Gerät bei Intune zu registrieren](/intune-user-help/enroll-your-device-in-intune-ios).

> [!NOTE]
> Wenn Sie für Ihre Benutzer Richtlinien für den bedingten Zugriff verwenden, können sie nicht auf die Unternehmens-E-Mails zugreifen, bis sie sich erneut registriert haben.

> [!TIP]
> Eine Beispielmitteilung für Ihre Benutzer könnte wie folgt lauten: Um sich auf Ihrem neuen Gerät zu registrieren, vergewissern Sie sich, dass die Version der Unternehmensportal-App Version 2.1.22 oder höher ist. Um die Version zu überprüfen, öffnen Sie die Unternehmensportal-App, tippen Sie auf die Schaltfläche „Menu“ (Menü) oben rechts und anschließend auf „About“ (Info). Wenn Sie eine ältere Version installiert haben, beenden Sie die Unternehmensportal-App, und öffnen Sie den App Store. Tippen Sie in der unteren rechten Ecke auf die Schaltfläche „Updates“ und anschließend auf die Schaltfläche „Update“ (Aktualisieren) neben dem Element der Unternehmensportal-App in der Liste. Sobald das Update abgeschlossen ist, starten Sie die Unternehmensportal-App, und [registrieren Sie Ihr iOS-Gerät bei Intune](/intune-user-help/enroll-your-device-in-intune-ios).

## <a name="resolving-known-issues-with-restores"></a>Lösen von bekannten Problemen beim Wiederherstellen

Benutzer können mit Problemen konfrontiert sein, wenn sie ihr Gerät wiederhergestellt und die Unternehmensportal-App gestartet haben, während sie noch Version 2.1.21 oder eine frühere Version der Unternehmensportal-App verwendeten. Diese Probleme können durch die entsprechenden Schritte für die Situation des Benutzers behoben werden.

### <a name="for-users-who-will-only-use-their-new-device"></a>Für Benutzer, die nur ihr neues Gerät verwenden
Starten Sie die Unternehmensportal-App, und heben Sie die Registrierung auf, indem Sie die Kachel des aktuellen Geräts auswählen und auf die Schaltfläche __Entfernen__ tippen. Befolgen Sie nach dem Entfernen die Standardschritte zum [Registrieren eines iOS-Geräts bei Intune](/intune-user-help/enroll-your-device-in-intune-ios).

### <a name="for-users-who-will-use-both-their-old-and-new-devices"></a>Für Benutzer, die sowohl ihre alten als auch ihre neuen Geräte verwenden
Löschen Sie die Cookies von Safari, indem Sie auf __Einstellungen__ > __Safari__ > __Verlauf und Websitedaten löschen__ tippen. Deinstallieren Sie die Unternehmensportal-App nach dem Löschen der Cookies, und installieren Sie diese erneut. Befolgen Sie anschließend die Standardschritte zum [Registrieren eines iOS-Geräts bei Intune](/intune-user-help/enroll-your-device-in-intune-ios).
