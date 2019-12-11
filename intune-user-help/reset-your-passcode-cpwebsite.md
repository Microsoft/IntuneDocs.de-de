---
title: Zurücksetzen Ihrer Kennung über die Website des Unternehmensportals | Microsoft-Dokumentation
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2056d37b00f5e2ae7b36c6e1c02f20dc244eb290
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502128"
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>So setzen Sie Ihre Kennung über die Unternehmensportalwebsite zurück

Wenn Sie die PIN oder das Kennwort verloren haben, können Sie die PIN bzw. das Kennwort über die [Unternehmensportalwebsite](https://portal.manage.microsoft.com) zurücksetzen. 

Die Option "Kennung zurücksetzen" wird möglicherweise nicht für ein vom Unternehmen registriertes Gerät angezeigt. Wenden Sie sich in diesem Fall an den Support Ihres Unternehmens, um ihn für Sie zurückzusetzen.  

Die zurück setzung der Kennung ist für Geräte mit Android 7,0 und höher nicht verfügbar. Wenn Sie die Kennung auf einem dieser Geräte vergessen, müssen Sie Sie auf die Werkseinstellungen zurücksetzen.  

## <a name="reset-your-passcode"></a>Zurücksetzen der Kennung

1. Öffnen Sie die [Unternehmensportal-Website](https://portal.manage.microsoft.com), und wählen Sie die Schaltfläche __Menü__ und anschließend die Option __Geräte__ aus.  

2. Wählen Sie das Gerät aus, für das die Kennung zurückgesetzt werden muss.  

    ![Ein Screenshot der Seite „Geräte“ mit zwei Kacheln, auf denen nicht identifizierte Geräte mit Standardnamen angezeigt werden. Unter den Geräten befindet sich ein graues Banner, das Benutzer dazu auffordert, das verwendete Gerät zu identifizieren oder ein neues hinzuzufügen.](./media/rename-reset-device-step2-1808.png) 

3. Wählen Sie **Kennung zurücksetzen** aus. Wenn die Option zum Zurücksetzen der Kennung oben auf Ihrer Seite nicht sichtbar ist, wählen Sie **Mehr (....)**  > **Kennung zurücksetzen** aus.   

   ![Seite mit Gerätedetails für ein ausgewähltes Gerät auf der Unternehmensportalwebsite mit einer Liste der Links oben auf der Seite zu „Umbenennen“, „Entfernen“, „Gerät zurücksetzen“, „Kennung zurücksetzen“ und „Remotesperre“. ](./media/rename-reset-device-1808.png)   

    ![Screenshot des Symbols für weitere Optionen, das durch einen roten Pfeil markiert ist.](./media/rename-reset-device-step3-more-1808.png)  

4. Klicken Sie bei entsprechender Aufforderung auf **Abmelden**. Wenn Sie erneut aufgefordert werden, melden Sie sich wieder an. Melden Sie sich innerhalb von fünf Minuten wieder auf der Unternehmensportalwebsite an, da das Unternehmensportal sonst die Gerätekennung nicht zurücksetzen wird.  

   > [!NOTE]
   > Melden Sie sich dann erneut an, um Ihre Identität zu bestätigen. Dies dient dazu, böswillige Versuche zu verhindern, die Gerätekennung zurückzusetzen.

   ![Beispielscreenshot mit einer Aufforderung zum Abmelden von der Unternehmensportal-App Die Schaltflächen für Benutzereingaben sind „Abmelden“ und „Abbrechen“.](./media/iwp-reset-passcode-popup-1808.png)

5. Eine Warnmeldung wird angezeigt, dass die vorhandene Gerätekennung entfernt werden soll. Klicken Sie zur Bestätigung auf **Kennung zurücksetzen**.  
    > [!WARNING]
    > Nachdem Sie Ihre Kennung zurückgesetzt haben, kann jeder, der physischen Zugriff auf das Gerät hat, auf die meisten persönlichen und geschäftlichen Informationen zugreifen. Wenn Sie sich das Gerät derzeit nicht in Ihrem Besitz befindet, sollten Sie die Kennung nicht zurücksetzen.  

   ![Beispielscreenshot zur zweiten Meldung beim Zurücksetzen der Kennung. Enthält einen Link, um mehr über das Festlegen einer neuen Kennung in der Dokumentation zu erfahren, und einzelne Schaltflächen, um die Kennung zurückzusetzen oder abzubrechen.](./media/iwp-reset-passcode-popup2-1808.png) 

6. Wenn Sie die Kennung für ein iOS-Gerät zurücksetzen, wird die vorhandene Kennung entfernt. Für Windows- oder Android-Geräte erhalten Sie eine temporäre Kennung, um das Gerät freizuschalten und eine neue Kennung festzulegen. 

   > [!NOTE]
   > Die temporäre Kennung für Windows- und Android-Geräte finden Sie im Unternehmensportal auf der Detailseite des Geräts. Weitere Beschreibungen zu betriebssystemspezifischen Kennungen finden Sie im Abschnitt [Einrichten einer neuen Kennung](reset-your-passcode-cpwebsite.md#set-up-a-new-passcode).  
   
7. Wechseln Sie auf Ihrem Gerät zu **Einstellungen**, und ändern Sie die temporäre Kennung. 

8. Oben rechts auf der Unternehmensportalwebsite wird ein Flag angezeigt. Klicken Sie darauf, um die Benachrichtigung zu lesen und zu bestätigen, dass die Kennung erfolgreich zurückgesetzt wurde.  

## <a name="set-up-a-new-passcode"></a>Einrichten einer neuen Kennung  

In diesem Abschnitt werden das Zurücksetzen der Kennung und das Verhalten temporärer Kennungen für die einzelnen Geräteplattformen beschrieben.  

**Android**: Entfernt die vorhandene Kennung und erstellt eine temporäre Kennung aus Buchstaben und Zahlen.

**iOS**: Entfernt die aktuelle Kennung und erstellt keine neue temporäre Kennung. Wenn Sie das Gerät mit der Fingereingabe-ID öffnen oder Einkäufe tätigen, müssen Sie es erneut einrichten.  

**Windows 10 Mobile**: Entfernt die vorhandene Kennung und erstellt eine temporäre Kennung aus Buchstaben und Zahlen. Wenn diese eingerichtet ist, funktioniert die Gesichtserkennung von Windows Hello auch weiterhin mit dem Gerät.

**Windows Phone 8.1**: Entfernt die vorhandene Kennung und erstellt eine temporäre Kennung aus Zahlen.  

Benötigen Sie weitere Unterstützung? Kontaktieren Sie den Support Ihres Unternehmens. Die entsprechenden Kontaktinformationen finden Sie auf der [Unternehmensportal-Website](https://go.microsoft.com/fwlink/?linkid=2010980).  
