---
title: Senden benutzerdefinierter Benachrichtigungen an Benutzer mit Microsoft Intune
titleSuffix: Microsoft Intune
description: Verwenden von Intune zum Erstellen und Senden benutzerdefinierter Pushbenachrichtigungen an Benutzer von iOS- und Android-Geräten
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3a4314abec83bc31cd6fe178873ba5bce7bf1a0c
ms.sourcegitcommit: 864fdf995c2b41f104a98a7e2665088c2864774f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68680103"
---
# <a name="send-custom-notifications-in-intune"></a>Senden benutzerdefinierter Benachrichtigungen in Intune  

Verwenden Sie Microsoft Intune zum Senden benutzerdefinierter Benachrichtigungen an die Benutzer von verwalteten iOS- und Android-Geräten. Diese Nachrichten werden wie auch Benachrichtigungen von anderen Anwendungen auf dem Gerät als Standardpushbenachrichtigung von der Unternehmensportal-App auf dem Gerät eines Benutzers angezeigt. Benutzerdefinierte Intune-Benachrichtigungen werden nicht von Windows-Geräten unterstützt.   

Benutzerdefinierte Benachrichtigungsnachrichten enthalten einen kurzen Titel und einen Nachrichtentext mit maximal 500 Zeichen. Diese Nachrichten können für jeden allgemeinen Kommunikationszweck angepasst werden.

## <a name="common-scenarios-for-sending-custom-notifications"></a>Allgemeine Szenarios für das Senden von benutzerdefinierten Benachrichtigungen  

- Sie verwenden benutzerdefinierte Benachrichtigungen, um bestimmte Benutzer über eine neue App zu informieren, die im Unternehmensportal verfügbar ist.  
- Sie informieren alle Mitarbeiter über eine Änderung des Zeitplans (wie z. B. Schließungen der Gebäude aufgrund schwieriger Wetterbedingungen).  

## <a name="considerations-for-using-custom-notifications"></a>Überlegungen zur Verwendung benutzerdefinierter Benachrichtigungen  

**Gerätekonfiguration:**  
- Bevor Benutzer benutzerdefinierte Benachrichtigungen erhalten können, muss die Unternehmensportal-App auf Geräten installiert sein. Außerdem müssen sie über Berechtigungen verfügen, damit die Unternehmensportal-App Pushbenachrichtigungen senden kann. Das Unternehmensportal fordert Benutzer auf, bei jeder Installation oder Aktualisierung Benachrichtigungen zuzulassen.  
- Unter Android ist Google Play Services eine erforderliche Abhängigkeit.  
- Auf dem Gerät muss MDM registriert sein.

**Erstellen von Benachrichtigungen:**  
- Verwenden Sie zum Erstellen einer Nachricht ein Konto, das einer Intune-Rolle zugewiesen ist, die die **Update**-Berechtigung für **Organisation** enthält. Informationen zum Zuweisen von Berechtigungen für einen Benutzer finden Sie unter [Rollenzuweisungen](role-based-access-control.md#role-assignments).  
- Benutzerdefinierte Benachrichtigungen sind auf 50 Zeichen lange Titel und 500 Zeichen lange Nachrichten beschränkt.  
- Gesendete Nachrichten werden von Intune nicht gespeichert. Sie müssen eine Nachricht noch mal erstellen, um sie noch mal zu senden.  
- Sie können nur maximal 25 Nachrichten pro Stunde senden. Diese Einschränkung gilt für die Mandantenebene.  
- Jede Benachrichtigung kann bis zu 25 Gruppen als Ziel haben. Verschachtelte Gruppen zählen nicht zu dieser Gesamtanzahl.  
- Gruppen können Benutzer oder Geräte enthalten. Nachrichten werden allerdings nur an Benutzer gesendet und werden an jedes iOS- oder Android-Gerät gesendet, das vom Benutzer registriert wurde.  

**Lieferung:**  
- Nach dem Senden einer Benachrichtigung versucht Intune maximal eine Stunde lang, die Lieferung auszuführen.  
- Intune sendet Nachrichten an die Unternehmensportal-App der Benutzer, die dann die Pushbenachrichtigung erstellt. Benutzer müssen nicht bei der App angemeldet sein, damit die Benachrichtigung auf dem Gerät übermittelt wird.  
- Intune und die Unternehmensportal-App können die Lieferung einer benutzerdefinierten Benachrichtigung nicht garantieren. Nach mehreren Stunden Verzögerung werden möglicherweise benutzerdefinierte Benachrichtigungen angezeigt, die dann nicht für dringende Nachrichten verwendet werden sollten.  
- Benutzerdefinierte Benachrichtigungsnachrichten von Intune werden auf Geräten als Standardpushbenachrichtigungen angezeigt. Wenn die Unternehmensportal-App auf einem iOS-Gerät beim Empfang der Benachrichtigung geöffnet ist, wird in der App anstelle einer Pushbenachrichtigung eine Benachrichtigung angezeigt.  
- Benutzerdefinierte Benachrichtigungen können je nach Geräteeinstellungen sowohl auf iOS- als auch auf Android-Geräten auf dem Sperrbildschirm sichtbar sein.  
- Auf Android-Geräten haben andere Apps möglicherweise Zugriff auf die Daten in Ihren benutzerdefinierten Benachrichtigungen. Verwenden Sie diese nicht für vertrauliche Kommunikation.  
- Benutzer von Geräten, deren Registrierung vor kurzem aufgehoben wurde und aus einer Gruppe entfernte Benutzer erhalten möglicherweise trotzdem eine benutzerdefinierte Benachrichtigung, die anschließend an diese Gruppe gesendet wird.  Wenn Sie einen Benutzer zu einer Gruppe hinzufügen, nachdem eine benutzerdefinierte Benachrichtigung an die Gruppe gesendet wurde, ist es auch möglich, dass der neu hinzugefügte Benutzer diese zuvor gesendete Benachrichtigungsmeldung empfängt.  

## <a name="send-a-custom-notification"></a>Senden einer benutzerdefinierten Benachrichtigung  

1. Melden Sie sich mit einem Konto mit Zugriffsberechtigungen zum Erstellen und Senden von Benachrichtigungen bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an, und navigieren Sie zu **Geräte** > **Send custom notifications** (Benutzerdefinierte Benachrichtigung senden).  

2. Geben Sie auf der Registerkarte „Basics“ (Grundlagen) das Folgende an, und klicken Sie dann auf **Weiter**, um fortzufahren.  
   - **Titel:** Geben Sie einen Titel für diese Benachrichtigung an. Titel sind auf 50 Zeichen beschränkt.  
   - **Body** (Text): Geben Sie die Nachricht an. Nachrichten sind auf 500 Zeichen beschränkt.

   ![Erstellen einer benutzerdefinierten Benachrichtigung](./media/custom-notifications/custom-notifications.png)  

3. Klicken Sie auf der Registerkarte **Zuweisungen** zuerst auf die Gruppen, an die Sie diese benutzerdefinierte Benachrichtigung senden möchten, und anschließend auf „Weiter“, um fortzufahren.  

4. Überprüfen Sie auf der Registerkarte **Review + Create** (Überprüfen und Erstellen) die Informationen, und klicken Sie dann auf **Erstellen**, wenn Sie zum Senden der Benachrichtigung bereit sind.  

Von Ihnen erstellte Nachrichten werden von Intune sofort verarbeitet. Die einzige Bestätigung für das Senden der Nachricht ist die Intune-Benachrichtigung, die bestätigt, dass die benutzerdefinierte Benachrichtigung gesendet wurde.  

![Bestätigung einer gesendeten Benachrichtigung](./media/custom-notifications/notification-sent.png)  

Intune verfolgt die von Ihnen gesendeten benutzerdefinierten Benachrichtigungen nicht, und der Empfang wird außerhalb des Benachrichtigungscenters des Geräts nicht protokolliert.  

## <a name="receive-a-custom-notification"></a>Empfangen einer benutzerdefinierten Benachrichtigung  

Benutzern werden auf einem Gerät benutzerdefinierte Benachrichtigungsnachrichten angezeigt, die von Intune als Standardpushbenachrichtigung aus der Unternehmensportal-App gesendet werden. Diese Benachrichtigungen ähneln den Pushbenachrichtigungen, die Benutzer von anderen Apps auf dem Gerät erhalten.  

Wenn die Unternehmensportal-App auf iOS-Geräten beim Empfang der Benachrichtigung geöffnet ist, wird in der App anstelle einer Pushbenachrichtigung eine Benachrichtigung angezeigt.  

Die Benachrichtigung bleibt so lange erhalten, bis Sie vom Benutzer geschlossen wird.  

## <a name="next-steps"></a>Nächste Schritte  
[Verwalten von Geräten](device-management.md)
