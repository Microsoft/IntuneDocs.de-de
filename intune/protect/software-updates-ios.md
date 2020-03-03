---
title: Konfigurieren von Richtlinien für iOS/iPadOS-Softwareupdates in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen oder fügen Sie eine Konfigurationsrichtlinie in Microsoft Intune hinzu, um einzuschränken, wann Softwareupdates automatisch auf iOS/iPadOS-Geräten installiert werden. Sie können auswählen, an welchem Datum und zu welcher Uhrzeit Updates nicht installiert werden sollen. Sie können diese Richtlinie ebenfalls Gruppen, Benutzern oder Geräten zuweisen oder Überprüfungen auf Installationsfehler durchführen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77d4a90bb2eaa8434ff9c05362dcb0d7cb270651
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576154"
---
# <a name="add-iosipados-software-update-policies-in-intune"></a>Hinzufügen von iOS/iPadOS-Softwareupdaterichtlinien in Intune

Durch Richtlinien für Softwareupdates können Sie erzwingen, dass Updates für das Betriebssystem auf überwachten iOS/iPadOS-Geräten automatisch installiert werden. Bei überwachten Geräten handelt es sich um Geräte, die mithilfe von Apple Business Manager oder Apple School Manager registriert wurden. Beim Konfigurieren einer Richtlinie zum Bereitstellen von Updates können Sie folgende Aktionen ausführen:

- Sie können entweder das *neueste verfügbare Update* oder, wenn Sie dies nicht möchten, über die Updateversionsnummer ein älteres Update bereitstellen. Wenn Sie ein älteres Update bereitstellen, müssen Sie auch eine Gerätekonfigurationsrichtlinie festlegen, um die Sichtbarkeit von Softwareupdates einzuschränken.
- Sie können einen Zeitplan angeben, der festlegt, wann das Update installiert wird. Zeitpläne können so einfach sein wie das Installieren von Updates beim nächsten Einchecken des Geräts oder das Erstellen von Datums- und Zeitbereichen, in denen Updates installiert werden können oder deren Installation blockiert wird.

Diese Funktion gilt für:

- iOS 10.3 und höher (überwacht)

Das Gerät wird standardmäßig etwa alle acht Stunden bei Intune eingecheckt. Wenn ein Update über eine Updaterichtlinie verfügbar ist, wird das Update vom Gerät heruntergeladen. Das Gerät installiert dann das Update beim nächsten Einchecken innerhalb Ihrer Zeitplankonfiguration. Obwohl während des Updateprozesses in der Regel keine Benutzerinteraktion erforderlich ist, muss der Benutzer, wenn das Gerät über einen Passcode verfügt, diesen eingeben, um ein Softwareupdate zu starten. Profile verhindern nicht, dass Benutzer das Betriebssystem manuell aktualisieren. Benutzer können daran gehindert werden, das Betriebssystem manuell mit einer Gerätekonfigurationsrichtlinie zu aktualisieren, um die Sichtbarkeit von Softwareupdates einzuschränken.

## <a name="configure-the-policy"></a>Konfigurieren der Richtlinie

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Klicken Sie auf **Geräte** > **Update policies for iOS/iPadOS** > **Profil erstellen** (Updaterichtlinien für iOS/iPadOS).
3. Geben Sie auf der Registerkarte **Grundeinstellungen** einen Namen und eine Beschreibung (optional) für diese Richtlinie an, und klicken Sie dann auf **Weiter**.

   ![Registerkarte „Grundeinstellungen“](./media/software-updates-ios/basics-tab.png)

4. Konfigurieren Sie auf der Registerkarte **Richtlinieneinstellungen aktualisieren** Folgendes:

   1. **Zu installierende Version auswählen**. Es gibt folgende Auswahlmöglichkeiten:

      - *Neuestes Update:* Dadurch wird das zuletzt veröffentlichte Update für iOS/iPadOS bereitgestellt.
      - Außerdem kann jede vorherige Version bereitgestellt werden, die im Dropdownfeld verfügbar ist. Wenn Sie eine vorherige Version auswählen, müssen Sie auch eine Gerätekonfigurationsrichtlinie bereitstellen, um die Sichtbarkeit von Softwareupdates zu verzögern.

   2. **Zeitplantyp:** So konfigurieren Sie den Zeitplan für diese Richtlinie:

      - *Beim nächsten Einchecken aktualisieren:* Das Update wird beim nächsten Einchecken auf dem Gerät mit Intune installiert. Dies ist die einfachste Option, und es sind keine zusätzlichen Konfigurationen erforderlich.
      - *Update innerhalb des geplanten Zeitraums:* Sie konfigurieren mindestens ein Zeitfenster, in dem das Update beim Einchecken installiert wird.
      - *Update außerhalb des geplanten Zeitraums:* Sie konfigurieren mindestens ein Zeitfenster, in dem das Update beim Einchecken nicht installiert wird.

   3. **Wöchentlicher Zeitplan:** Konfigurieren Sie die folgenden Optionen, wenn Sie nicht den Zeitplantyp *Beim nächsten Einchecken aktualisieren* auswählen:

      ![Beispiel für Auswahl von Update während geplanten Zeitraums](./media/software-updates-ios/scheduled-time.png)

      - **Zeitzone:** Wählen Sie eine Zeitzone aus.
      - **Zeitfenster:** Definieren Sie mindestens einen Zeitblock, der einschränkt, wann das Update installiert wird. Es hängt vom ausgewählten Zeitplantyp ab, welche Auswirkung die folgenden Optionen haben: Durch die Verwendung eines Starttags und Endtags werden Zeitblöcke zu Nachtzeiten unterstützt. Zu den Optionen gehören:

        - **Starttag:** Wählen Sie den Tag aus, an dem das Zeitplanfenster gestartet wird.
        - **Startzeit**: Wählen Sie die Zeit aus, zu der das Zeitplanfenster beginnt. Wenn Sie beispielsweise beim Zeitplantyp *Update innerhalb des geplanten Zeitraums* 5 Uhr auswählen, beginnt die Installation von Updates um 5 Uhr. Wenn Sie den Zeitplantyp *Update außerhalb des geplanten Zeitraums* auswählen, beginnt ab 5 Uhr ein Zeitraum, in dem keine Updates installiert werden können.
        - **Endtag:** Wählen Sie den Tag aus, an dem das Zeitplanfenster endet.
        - **Endzeit:** Wählen Sie die Tageszeit aus, zu der das Zeitplanfenster endet. Wenn Sie beispielsweise beim Zeitplantyp *Update innerhalb des geplanten Zeitraums* 1 Uhr auswählen, können Updates ab 1 Uhr nicht mehr installiert werden. Wenn Sie den Zeitplantyp *Update außerhalb des geplanten Zeitraums* auswählen, beginnt ab 1 Uhr ein Zeitraum, in dem keine Updates installiert werden können.

       Wenn Sie keine Zeiten zum Starten oder Beenden konfigurieren, führt die Konfiguration zu keiner Einschränkung, und Updates können jederzeit installiert werden.  

       > [!NOTE]
       > Wenn Sie die Sichtbarkeit von Softwareupdates für einen bestimmten Zeitraum auf Ihren überwachten iOS/iPadOS-Geräten verzögern möchten, konfigurieren Sie diese Einstellungen unter [Geräteeinschränkungen](../configuration/device-restrictions-ios.md#general). Softwareupdaterichtlinien setzen jegliche Geräteeinschränkungen außer Kraft. Wenn Sie sowohl eine Softwareupdaterichtlinie als auch eine Einschränkung zum Verzögern der Sichtbarkeit von Softwareupdates festlegen, erzwingt das Gerät ein Softwareupdate gemäß der Richtlinie. Die Einschränkung bewirkt, dass Benutzer die Option zum Ausführen des Geräteupdates nicht selbst sehen, und das Update wird wie im Rahmen Ihrer iOS-Updaterichtlinie durchgeführt.

   Nachdem Sie die *Updaterichtlinieneinstellungen* konfiguriert haben, klicken Sie auf **Weiter**.

5. Klicken Sie auf der Registerkarte **Bereichstags** auf **+ Bereichstags auswählen**, um den Bereich *Tags auswählen* zu öffnen, wenn Sie sie auf die Updaterichtlinie anwenden möchten.

   - Wählen Sie im Bereich **Tags auswählen** mindestens einen Tag aus, und klicken Sie dann auf **Auswählen**, um sie zur Richtlinie hinzuzufügen und zum Bereich *Bereichstags* zurückzukehren.

   Klicken Sie auf **Weiter**, um mit *Zuweisungen* fortzufahren, wenn Sie bereit sind.

6. Klicken Sie auf der Registerkarte **Zuweisungen** auf **+ Einzuschließende Gruppen auswählen**, und weisen Sie dann die Richtlinie mindestens einer Gruppe zu. Klicken Sie auf **+ Auszuschließende Gruppen auswählen**, um die Zuweisung anzupassen. Klicken Sie auf **Weiter**, um fortzufahren.

   Die von den Benutzern verwendeten Geräte, für die die Richtlinie gilt, werden auf Updatekompatibilität überprüft. Diese Richtlinie unterstützt ebenfalls Geräte ohne Benutzer.

7. Überprüfen Sie die Einstellungen auf der Registerkarte **Überprüfen + erstellen**, und klicken Sie dann auf **Erstellen**, um Ihre iOS/iPadOS-Updaterichtlinie zu speichern. Ihre neue Richtlinie wird in der Liste der Updaterichtlinien für iOS/iPadOS anzuzeigen.

Unterstützung vom Supportteam für Intune erhalten Sie unter [Delay visibility of software updates in Intune for supervised devices (Verzögern der Sichtbarkeit von Softwareupdates in Intune für überwachte Geräte)](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> Die mobile Geräteverwaltung von Apple lässt nicht zu, dass das Installieren von Updates auf einem Gerät an einem bestimmten Datum oder zu einer bestimmten Uhrzeit erzwungen werden soll. Sie können keine Intune-Richtlinien für Softwareupdates verwenden, um die Betriebssystemversion auf einem Gerät herabzusetzen.

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
Unter **Softwareupdates** > **Installationsfehler für iOS-Geräte** wird eine Liste der überwachten iOS/iPadOS-Geräte angezeigt, für die eine Updaterichtlinie gilt und bei denen erfolglos ein Update versucht wurde. Für jedes Gerät können Sie den Status anzeigen, warum das Gerät nicht automatisch aktualisiert wurde. Fehlerfreie, aktuelle Geräte werden in der Liste nicht angezeigt. Ein Gerät gilt als aktuell, wenn das neueste Update installiert ist, das das Gerät unterstützt.

## <a name="next-steps"></a>Nächste Schritte

[Überwachen des Status](../configuration/device-profile-monitor.md)
