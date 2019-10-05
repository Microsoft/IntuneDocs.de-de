---
title: Senden benutzerdefinierter Benachrichtigungen an Benutzer mit Microsoft Intune
titleSuffix: Microsoft Intune
description: Verwenden von Intune zum Erstellen und Senden benutzerdefinierter Pushbenachrichtigungen an Benutzer von iOS- und Android-Geräten
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/19/2019
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
ms.openlocfilehash: d3c21e255db1142ec5ab15c99e8da6bc41de01cf
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728051"
---
# <a name="send-custom-notifications-in-intune"></a>Senden benutzerdefinierter Benachrichtigungen in Intune  

Verwenden Sie Microsoft Intune zum Senden benutzerdefinierter Benachrichtigungen an die Benutzer von verwalteten iOS- und Android-Geräten. Diese Nachrichten werden wie auch Benachrichtigungen von anderen Anwendungen auf dem Gerät als Standardpushbenachrichtigungen von der Unternehmensportal-App und der Microsoft Intune-App auf dem Gerät eines Benutzers angezeigt. Benutzerdefinierte Intune-Benachrichtigungen werden von macOS- und Windows-Geräten nicht unterstützt.   

Benutzerdefinierte Benachrichtigungsnachrichten enthalten einen kurzen Titel und einen Nachrichtentext mit maximal 500 Zeichen. Diese Nachrichten können für jeden allgemeinen Kommunikationszweck angepasst werden.

## <a name="common-scenarios-for-sending-custom-notifications"></a>Allgemeine Szenarios für das Senden von benutzerdefinierten Benachrichtigungen  

- Informieren Sie alle Mitarbeiter über eine Änderung des Zeitplans, z. B. bei Schließungen von Gebäuden aufgrund schwieriger Wetterbedingungen.
- Senden Sie eine Benachrichtigung an Benutzer einzelner Geräte, um eine dringende Anforderung mitzuteilen, beispielsweise zum Neustart des Geräts, um die Installation eines Updates abzuschließen. 

## <a name="considerations-for-using-custom-notifications"></a>Überlegungen zur Verwendung benutzerdefinierter Benachrichtigungen

**Gerätekonfiguration** 

- Bevor Benutzer benutzerdefinierte Benachrichtigungen erhalten können, muss die Unternehmensportal-App oder Microsoft Intune-App auf Geräten installiert sein. Außerdem müssen sie über Berechtigungen verfügen, damit die Unternehmensportal-App oder Microsoft Intune-App Pushbenachrichtigungen senden kann. Bei Bedarf können die Unternehmensportal-APP und die Microsoft Intune-App Benutzer auffordern, Benachrichtigungen zuzulassen.  
- Unter Android ist Google Play Services eine erforderliche Abhängigkeit.  
- Auf dem Gerät muss MDM registriert sein.

**Berechtigungen**:
- Um Benachrichtigungen an Gruppen zu senden, muss Ihr Konto über folgende RBAC-Berechtigungen (Role-Based Access Control, rollenbasierte Zugriffssteuerung) in Intune verfügen: *Organisation* > **Update**.
- Um Benachrichtigungen an ein Gerät zu senden, muss Ihr Konto über folgende RBAC-Berechtigungen in Intune verfügen: *Remoteaufgaben* > **Benutzerdefinierte Benachrichtigungen senden**.

**Erstellen von Benachrichtigungen:**  
- Verwenden Sie zum Erstellen einer Nachricht ein Konto, das einer Intune-Rolle zugewiesen ist, die die **Update**-Berechtigung für **Organisation** enthält. Informationen zum Zuweisen von Berechtigungen für einen Benutzer finden Sie unter [Rollenzuweisungen](../fundamentals/role-based-access-control.md#role-assignments).  
- Benutzerdefinierte Benachrichtigungen sind auf 50 Zeichen lange Titel und 500 Zeichen lange Nachrichten beschränkt.  
- Gesendete Nachrichten werden von Intune nicht gespeichert. Sie müssen eine Nachricht noch mal erstellen, um sie noch mal zu senden.  
- Sie können maximal 25 Nachrichten pro Stunde an Gruppen senden. Diese Einschränkung gilt für die Mandantenebene. Diese Einschränkung gilt nicht beim Senden von Benachrichtigungen an Einzelpersonen.
- Wenn Sie Nachrichten an einzelne Geräte senden, können Sie nur bis zu 10 Nachrichten pro Stunde an ein und dasselbe Gerät senden. 
- Sie können Benachrichtigungen an mehrere Benutzer oder Geräte senden, indem Sie die Benachrichtigung Gruppen zuweisen. Beim Verwenden von Gruppen kann jede Benachrichtigung direkt an bis zu 25 Gruppen gerichtet werden. Verschachtelte Gruppen zählen nicht zu dieser Gesamtanzahl.  

  Gruppen können Benutzer oder Geräte umfassen, Nachrichten werden allerdings nur an Benutzer gesendet. Nachrichten werden an jedes iOS- oder Android-Gerät gesendet, das von einem Benutzer registriert wurde.  
- Sie können Benachrichtigungen an einzelne Geräte senden. Anstatt Gruppen zu verwenden, wählen Sie ein Gerät aus und verwenden dann remote eine [Geräteaktion](device-management.md#available-device-actions), um die benutzerdefinierte Benachrichtigung zu senden.  

**Lieferung:**  
- Intune sendet Nachrichten an die Unternehmensportal-App oder Microsoft Intune-App der Benutzer, die dann die Pushbenachrichtigung erstellt. Benutzer müssen nicht bei der App angemeldet sein, damit die Benachrichtigung auf dem Gerät übermittelt wird.  
- Intune kann ebenso wie die Unternehmensportal-App und die Microsoft Intune-App die Lieferung einer benutzerdefinierten Benachrichtigung nicht garantieren. Nach mehreren Stunden Verzögerung werden möglicherweise benutzerdefinierte Benachrichtigungen angezeigt, die dann nicht für dringende Nachrichten verwendet werden sollten.  
- Benutzerdefinierte Benachrichtigungsnachrichten von Intune werden auf Geräten als Standardpushbenachrichtigungen angezeigt. Wenn die Unternehmensportal-App auf einem iOS-Gerät beim Empfang der Benachrichtigung geöffnet ist, wird in der App anstelle einer Pushbenachrichtigung eine Benachrichtigung angezeigt.  
- Benutzerdefinierte Benachrichtigungen können je nach Geräteeinstellungen sowohl auf iOS- als auch auf Android-Geräten auf dem Sperrbildschirm sichtbar sein.  
- Auf Android-Geräten haben andere Apps möglicherweise Zugriff auf die Daten in Ihren benutzerdefinierten Benachrichtigungen. Verwenden Sie diese nicht für vertrauliche Kommunikation.  
- Benutzer von Geräten, deren Registrierung vor kurzem aufgehoben wurde, und aus einer Gruppe entfernte Benutzer erhalten möglicherweise trotzdem eine benutzerdefinierte Benachrichtigung, die später an diese Gruppe gesendet wurde.  Gleiches gilt, wenn Sie einen Benutzer zu einer Gruppe hinzufügen, nachdem eine benutzerdefinierte Benachrichtigung an die Gruppe gesendet wurde: Es ist möglich, dass der neu hinzugefügte Benutzer diese zuvor gesendete Benachrichtigung empfängt.  

## <a name="send-a-custom-notification-to-groups"></a>Senden einer benutzerdefinierten Benachrichtigung an Gruppen  

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

## <a name="send-a-custom-notification-to-a-single-device"></a>Senden einer benutzerdefinierten Benachrichtigung an ein einzelnes Gerät  

1. Melden Sie sich mit einem Konto, das über Zugriffsberechtigungen zum Erstellen und Senden von Benachrichtigungen verfügt, bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an, und navigieren Sie zu **Geräte** > **Alle Geräte**.  

2. Wählen Sie das Gerät aus, an das Sie eine Benachrichtigung senden möchten.  

3. Wählen Sie in der **Übersicht** für das Gerät oben links auf der Seite die Option **Mehr...** aus.  

4. Wählen Sie die Geräteaktion **Benutzerdefinierte Benachrichtigung senden** aus, um den Bereich *Benutzerdefinierte Benachrichtigung senden* zu öffnen, in dem Sie die folgenden Informationen zur Nachricht angeben:  

   - **Titel:** Geben Sie einen Titel für diese Benachrichtigung an. Titel sind auf 50 Zeichen beschränkt.  
   - **Body** (Text): Geben Sie die Nachricht an. Nachrichten sind auf 500 Zeichen beschränkt.  

5. Wählen Sie **Senden** aus, um die benutzerdefinierte Benachrichtigung an das Gerät zu senden. Im Gegensatz zu Benachrichtigungen, die Sie an Gruppen senden, konfigurieren Sie keine Zuordnung oder überprüfen die Nachricht vor dem Senden.  

Intune verarbeitet die Nachricht sofort. Die einzige Bestätigung dafür, dass die Nachricht gesendet wurde, besteht in der Intune-Benachrichtigung, die Sie in der Konsole erhalten und die den Text der gesendeten Nachricht anzeigt.  

## <a name="receive-a-custom-notification"></a>Empfangen einer benutzerdefinierten Benachrichtigung  

Benutzern werden auf einem Gerät benutzerdefinierte Benachrichtigungsnachrichten angezeigt, die von Intune als Standardpushbenachrichtigung von der Unternehmensportal-App oder Microsoft Intune-App gesendet werden. Diese Benachrichtigungen ähneln den Pushbenachrichtigungen, die Benutzer von anderen Apps auf dem Gerät erhalten.  

Wenn die Unternehmensportal-App auf iOS-Geräten beim Empfang der Benachrichtigung geöffnet ist, wird in der App anstelle einer Pushbenachrichtigung eine Benachrichtigung angezeigt.  

Die Benachrichtigung bleibt so lange erhalten, bis Sie vom Benutzer geschlossen wird.  

## <a name="next-steps"></a>Nächste Schritte  

[Verwalten von Geräten](device-management.md)