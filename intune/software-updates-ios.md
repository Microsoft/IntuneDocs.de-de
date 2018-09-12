---
title: Konfigurieren von Richtlinien für iOS-Softwareupdates in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie in Microsoft Intune eine Konfigurationsrichtlinie, oder fügen Sie eine hinzu, um einzuschränken, wann Softwareupdates auf iOS-Geräten, die von Intune verwaltet oder überwacht werden, automatisch installiert werden. Sie können auswählen, an welchem Datum und zu welcher Uhrzeit Updates nicht installiert werden sollen. Sie können diese Richtlinie ebenfalls Gruppen, Benutzern oder Geräten zuweisen oder Überprüfungen auf Installationsfehler durchführen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.openlocfilehash: 1fe0258d3b6d9092c032184fca5fc0f8dc3f12df
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313495"
---
# <a name="configure-ios-update-policies-in-intune"></a>Konfigurieren von iOS-Updaterichtlinien in Intune

Durch Richtlinien für Softwareupdates können Sie erzwingen, dass das neueste Update für das Betriebssystem auf überwachten iOS-Geräten automatisch installiert wird. Dieses Feature steht nur für überwachte Geräte zur Verfügung. Wenn Sie eine Richtlinie konfigurieren, können Sie angeben, an welchen Tagen und zu welchen Uhrzeiten keine Updates auf Geräten installiert werden sollen. 

Das Gerät wird etwa alle acht Stunden bei Intune eingecheckt. Wenn ein Update verfügbar und das Einchecken nicht während eines eingeschränkten Zeitraums stattfindet, lädt das Gerät das neueste Update für das Betriebssystem herunter und installiert es. Es ist kein Benutzereingriff erforderlich, um das Gerät zu aktualisieren. Die Richtlinie verhindert nicht, dass ein Benutzer das Betriebssystem manuell aktualisiert.

Dieses Feature unterstützt Geräte, auf denen iOS 10.3 und höher ausgeführt wird.

## <a name="configure-the-policy"></a>Konfigurieren der Richtlinie
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Klicken Sie auf **Softwareupdates** > **Update policies for iOS** (Updaterichtlinien für iOS)  > **Erstellen**.
4. Geben Sie einen Namen und eine Beschreibung für die Richtlinie ein.
5. Klicken Sie auf **Einstellungen**. 

    Geben Sie an, wann die Installation der neuesten Updates auf iOS-Geräte nicht erzwungen werden soll. Durch diese Einstellungen wird ein eingeschränkter Zeitraum erstellt. Sie können die **Tage** der Woche, die **Zeitzone**, die **Startzeit**, die **Endzeit** und die **Verzögerung der Sichtbarkeit von Softwareupdates (in Tagen)** zum Eingeben von Benutzern konfigurieren. Sie können einen Verzögerungszeitraum von 1 bis 90 Tagen für Softwareupdates festlegen. Geben Sie 0 (null) ein, um keine Verzögerung für Softwareupdates festzulegen. Diese Updateeinstellungen gelten nur für überwachte iOS-Geräte.

6. Klicken Sie auf **OK**, um die Änderungen zu speichern. Klicken Sie auf **Erstellen**, um die Richtlinie zu erstellen.

Das Profil wird erstellt und in der Richtlinienliste angezeigt. Die mobile Geräteverwaltung von Apple lässt nicht zu, dass das Installieren von Updates auf einem Gerät an einem bestimmten Datum oder zu einer bestimmten Uhrzeit erzwungen werden soll. 

## <a name="change-the-restricted-times-for-the-policy"></a>Ändern der eingeschränkten Zeiten für die Richtlinie

1. Klicken Sie unter **Softwareupdates** auf **Update policies for iOS (Updaterichtlinien für iOS)**.
2. Wählen Sie eine vorhandene Richtlinie aus, und klicken Sie dann auf **Eigenschaften**.
3. Aktualisieren Sie die eingeschränkten Zeiträume:

    1. Auswählen der Wochentage
    2. Wählen Sie die Zeitzone aus, in der diese Richtlinie angewendet wird.
    3. Wählen Sie die Start- und Endzeit des gesperrten Zeitraums aus.

    > [!NOTE]
    > Wenn die **Startzeit** und die **Endzeit** auf 0 Uhr festgelegt werden, wird das Kontrollkästchen für die Wartungszeit deaktiviert.

## <a name="assign-the-policy-to-users"></a>Zuweisen der Richtlinie zu Benutzern

Vorhandene Richtlinien werden Gruppen, Benutzern oder Geräten zugewiesen. Wenn eine Richtlinie zugewiesen ist, wird sie angewendet.

1. Klicken Sie unter **Softwareupdates** auf **Update policies for iOS (Updaterichtlinien für iOS)**.
2. Wählen Sie eine vorhandene Richtlinie aus, und klicken Sie dann auf **Zuweisungen**. 
3. Wählen Sie die Azure Active Directory-Gruppen, -Benutzer oder -Geräte aus, die dieser Richtlinie hinzugefügt oder von ihr ausgeschlossen werden sollen.
4. Klicken Sie auf **Speichern**, um die Richtlinie für Ihre Gruppen bereitzustellen.

Die von den Benutzern verwendeten Geräte, für die die Richtlinie gilt, werden auf Updatekompatibilität überprüft. Diese Richtlinie unterstützt ebenfalls Geräte ohne Benutzer.

## <a name="monitor-device-installation-failures"></a>Überwachung von Installationsfehlern bei Geräten
Unter <!-- 1352223 -->
**Softwareupdates** > **Installationsfehler für iOS-Geräte** wird eine Liste der überwachten iOS-Geräte angezeigt, für die eine Updaterichtlinie gilt und bei denen ein Update erfolglos versucht wurde. Für jedes Gerät können Sie den Status anzeigen, warum das Gerät nicht automatisch aktualisiert wurde. Fehlerfreie, aktuelle Geräte werden in der Liste nicht angezeigt. Ein Gerät gilt als aktuell, wenn das neueste Update installiert ist, das das Gerät unterstützt.

