---
title: Konfigurieren von Richtlinien für iOS-Softwareupdates in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen oder fügen Sie eine Konfigurationsrichtlinie in Microsoft Intune hinzu, um einzuschränken, wann Softwareupdates automatisch auf iOS-Geräten installiert werden. Sie können auswählen, an welchem Datum und zu welcher Uhrzeit Updates nicht installiert werden sollen. Sie können diese Richtlinie ebenfalls Gruppen, Benutzern oder Geräten zuweisen oder Überprüfungen auf Installationsfehler durchführen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: bb146fdee7a1d7d770575334eeed84f73cda8894
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207484"
---
# <a name="add-ios-software-update-policies-in-intune"></a>Hinzufügen von iOS-Softwareupdaterichtlinien in Intune

Durch Richtlinien für Softwareupdates können Sie erzwingen, dass das neueste Update für das Betriebssystem auf überwachten iOS-Geräten automatisch installiert wird. Wenn Sie eine Richtlinie konfigurieren, können Sie angeben, an welchen Tagen und zu welchen Uhrzeiten keine Updates auf Geräten installiert werden sollen.

Diese Funktion gilt für:

- iOS 10.3 und höher (überwacht)

Das Gerät wird etwa alle acht Stunden bei Intune eingecheckt. Wenn ein Update verfügbar ist, lädt das Gerät es herunter und installiert es, außerhalb der eingeschränkten Zeiten. Obwohl während des Aktualisierungsprozesses in der Regel keine Benutzerinteraktion erforderlich ist, muss der Benutzer, wenn das Gerät über einen Passcode verfügt, diesen eingeben, um ein Softwareupdate zu starten. Dies gilt für iOS 10.3 und höhere Versionen. Die Richtlinie verhindert nicht, dass ein Benutzer das Betriebssystem manuell aktualisiert.

## <a name="configure-the-policy"></a>Konfigurieren der Richtlinie

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Klicken Sie auf **Softwareupdates** > **Updaterichtlinien für iOS** > **Erstellen**.
3. Geben Sie auf der Registerkarte **Grundeinstellungen** einen Namen und eine Beschreibung (optional) für diese Richtlinie an, und klicken Sie dann auf **Weiter**.

   ![Registerkarte „Grundeinstellungen“](./media/software-updates-ios/basics-tab.png) 

4. Legen Sie auf der Registerkarte **Updaterichtlinieneinstellungen** einen eingeschränkten Zeitraum fest, in dem keine Updates erzwungen werden.  
   - Zeitblöcke zu Nachtzeiten werden nicht unterstützt und funktionieren möglicherweise nicht. Konfigurieren Sie beispielsweise keine Richtlinie mit der *Startzeit* 20 Uhr und der *Endzeit* 6 Uhr.
   - Eine Richtlinie, die um 00:00 Uhr beginnt und endet, wird als 0 Stunden ausgewertet und nicht als 24 Stunden. Diese Konfiguration resultiert also in keiner Einschränkung.

   Wenn Sie einen eingeschränkten Zeitrahmen festlegen, geben Sie die folgenden Details ein:

   - **Tage:** Wählen Sie die Wochentage aus, an denen keine Updates erstellt werden sollen. Wenn also montags, mittwochs und freitags keine Updates installiert werden sollen, wählen Sie diese Tage aus.
   - **Zeitzone:** Wählen Sie eine Zeitzone aus.
   - **Startzeit**: Wählen Sie die Startzeit für den eingeschränkten Zeitrahmen aus. Wenn Sie beispielsweise 5 Uhr angeben, werden von dieser Uhrzeit an keine Updates mehr installiert.
   - **Endzeit:** Wählen Sie die Endzeit für den eingeschränkten Zeitrahmen aus. Wenn Sie beispielsweise 1 Uhr eingeben, können von dieser Uhrzeit an Updates installiert werden.
  
   > [!IMPORTANT]  
   > Eine Richtlinie, bei der die *Startzeit* und die *Endzeit* auf 12 Uhr festgelegt wurde, wird als „0 Stunden“ und nicht als „24 Stunden“ ausgewertet. Diese Einstellung führt dazu, dass es keine Einschränkungen gibt.  
    
   Wenn Sie die Sichtbarkeit von Softwareupdates für einen bestimmten Zeitraum auf Ihren überwachten iOS-Geräten verzögern möchten, konfigurieren Sie diese Einstellungen unter [Geräteeinschränkungen](../configuration/device-restrictions-ios.md#general). Softwareupdaterichtlinien setzen jegliche Geräteeinschränkungen außer Kraft. Wenn Sie sowohl eine Softwareupdaterichtlinie als auch eine Einschränkung zum Verzögern der Sichtbarkeit von Softwareupdates festlegen, erzwingt das Gerät ein Softwareupdate gemäß der Richtlinie. Die Einschränkung bewirkt, dass Benutzer die Option zum Ausführen des Geräteupdates nicht selbst sehen, und das Update wird im ersten in Ihrer iOS-Updaterichtlinie definierten Zeitfenster durchgeführt.

   Nachdem Sie die *Updaterichtlinieneinstellungen* konfiguriert haben, klicken Sie auf **Weiter**. 

5. Klicken Sie auf der Registerkarte **Bereichstags** auf **+ Bereichstags auswählen**, um den Bereich *Tags auswählen* zu öffnen, wenn Sie sie auf die Updaterichtlinie anwenden möchten.
   
   - Wählen Sie im Bereich **Tags auswählen** mindestens einen Tag aus, und klicken Sie dann auf **Auswählen**, um sie zur Richtlinie hinzuzufügen und zum Bereich *Bereichstags* zurückzukehren.  

   Klicken Sie auf **Weiter**, um mit *Zuweisungen* fortzufahren, wenn Sie bereit sind.

6. Klicken Sie auf der Registerkarte **Zuweisungen** auf **+ Einzuschließende Gruppen auswählen**, und weisen Sie dann die Richtlinie mindestens einer Gruppe zu. Klicken Sie auf **+ Auszuschließende Gruppen auswählen**, um die Zuweisung anzupassen. Klicken Sie auf **Weiter**, um fortzufahren. 

   Die von den Benutzern verwendeten Geräte, für die die Richtlinie gilt, werden auf Updatekompatibilität überprüft. Diese Richtlinie unterstützt ebenfalls Geräte ohne Benutzer.

7. Überprüfen Sie die Einstellungen auf der Registerkarte **Überprüfen + erstellen**, und klicken Sie dann auf **Erstellen**, um Ihre iOS-Updaterichtlinie zu speichern. Ihre neue Richtlinie wird in der Liste der Updaterichtlinien für iOS anzuzeigen.


Unterstützung vom Supportteam für Intune erhalten Sie unter [Delay visibility of software updates in Intune for supervised devices (Verzögern der Sichtbarkeit von Softwareupdates in Intune für überwachte Geräte)](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> Die mobile Geräteverwaltung von Apple lässt nicht zu, dass das Installieren von Updates auf einem Gerät an einem bestimmten Datum oder zu einer bestimmten Uhrzeit erzwungen werden soll.

## <a name="edit-a-policy"></a>Bearbeiten einer Richtlinie
Sie können eine vorhandene Richtlinie bearbeiten und die eingeschränkten Zeiten ändern:

1. Klicken Sie auf **Softwareupdates** > **Updaterichtlinien für iOS**. Wählen Sie die Richtlinie aus, die Sie bearbeiten möchten.

2. Während Sie die **Eigenschaften** der Richtlinien anzeigen, können Sie bei der Richtlinienseite auf **Bearbeiten** klicken, die Sie ändern möchten.  
   ![Bearbeiten einer Richtlinie](./media/software-updates-ios/edit-policy.png)   

3. Nachdem Sie Ihre Änderungen vorgenommen haben, klicken Sie auf **Überprüfen und speichern** > **Speichern**, um Ihre Änderungen zu speichern und zu den *Eigenschaften* der Richtlinien zurückzukehren.  
 
> [!NOTE]
> Wenn die **Startzeit** und die **Endzeit** auf 00:00 Uhr festgelegt sind, prüft Intune nicht nach Einschränkungen zur Installation von Updates. D. h., dass alle Konfigurationen, die Sie für die Einstellung **Select times to prevent update installations** (Zeiten auswählen, zu denen Updateinstallationen verhindert werden sollen) festgelegt haben, ignoriert werden und jederzeit Updates installiert werden können.  


## <a name="monitor-device-installation-failures"></a>Überwachung von Installationsfehlern bei Geräten
<!-- 1352223 -->
Unter **Softwareupdates** > **Installationsfehler für iOS-Geräte** wird eine Liste der überwachten iOS-Geräte angezeigt, für die eine Updaterichtlinie gilt und bei denen erfolglos ein Update versucht wurde. Für jedes Gerät können Sie den Status anzeigen, warum das Gerät nicht automatisch aktualisiert wurde. Fehlerfreie, aktuelle Geräte werden in der Liste nicht angezeigt. Ein Gerät gilt als aktuell, wenn das neueste Update installiert ist, das das Gerät unterstützt.

## <a name="next-steps"></a>Nächste Schritte

[Überwachen des Status](../configuration/device-profile-monitor.md)
