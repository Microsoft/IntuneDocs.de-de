---
title: Konfigurieren von Richtlinien für iOS-Softwareupdates in Microsoft Intune
titlesuffix: ''
description: Konfigurieren Sie die Richtlinien, damit unter iOS die automatische Installation des neuesten Softwareupdates bei überwachten iOS-Geräten durchgesetzt werden kann.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.openlocfilehash: 1d4223ae4feb417f77909b320cd0295347b44461
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31836587"
---
# <a name="configure-ios-update-policies-in-microsoft-intune"></a>Konfigurieren von iOS-Updaterichtlinien in Microsoft Intune

Durch Richtlinien für Softwareupdates können Sie erzwingen, dass auf überwachten iOS-Geräten mit iOS 10.3 und höher automatisch das neueste Update für das Betriebssystem installiert wird. Dieses Feature steht nur für überwachte Geräte zur Verfügung. Sie haben die Möglichkeit, die Tage und Uhrzeiten zu konfigurieren, an denen Geräte keine Updates installieren sollen. 

Wenn das Gerät außerhalb der eingeschränkten Zeiten eingecheckt wird (etwa alle 8 Stunden) und ein Update verfügbar ist, versucht das Gerät, das neueste Update für das Betriebssystem herunterzuladen und zu installieren. Es ist kein Benutzereingriff erforderlich, um das Gerät zu aktualisieren. Die Richtlinie verhindert nicht, dass ein Benutzer das Betriebssystem aktualisiert.

## <a name="configure-the-ios-update-policy"></a>Konfigurieren der iOS-Updaterichtlinie
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie im Bereich **Intune** die Option **Softwareupdates** > **iOS-Updaterichtlinien** aus.
4. Klicken Sie im Richtlinienbereich auf **Erstellen**, und geben Sie dann einen Namen und eine Beschreibung für die Richtlinie ein.
5. Klicken Sie auf **Einstellungen** > **Konfigurieren**, und geben Sie dann an, wann die Installation der neuesten Updates auf iOS-Geräte nicht erzwungen werden soll. Sie können die Wochentage, die Zeitzone sowie die Start- und Endzeit konfigurieren.
6. Wählen Sie **OK** aus, um diese Konfiguration zu speichern. Damit befinden Sie sich wieder im Bereich **Updaterichtlinie erstellen**. Wählen Sie **Erstellen** aus, um die Richtlinie zu erstellen und Ihre Einstellungen zu speichern.

Das Profil wird erstellt und im Bereich mit der Liste der iOS-Updaterichtlinien angezeigt. Mit Apple MDM kann nicht erzwungen werden, dass das Gerät das Update zu einer bestimmten Zeit oder an einem bestimmten Datum durchführt. 

## <a name="change-the-restricted-times-for-the-policy"></a>Ändern der eingeschränkten Zeiten für die Richtlinie

1.  Wählen Sie auf dem Blatt **Softwareupdates** die Option **iOS-Updaterichtlinien** aus.
2.  Wählen Sie die iOS-Updaterichtlinie aus, die Sie aktualisieren möchten.
3.  Wählen Sie **Eigenschaften** aus, und aktualisieren Sie die Informationen zu den eingeschränkten Zeiten.
4.  Auswählen der Wochentage
5.  Die Zeitzone, in der diese Richtlinie angewendet wird
6.  Start und Ende der gesperrten Zeit

## <a name="assign-an-ios-update-policy-to-users"></a>Zuweisen einer iOS-Updaterichtlinie zu Benutzern

Um Benutzern eine iOS-Updaterichtlinie zuzuweisen, wählen Sie eine Richtlinie aus, die Sie konfiguriert haben. Vorhandene Richtlinien befinden sich im Bereich **Softwareupdates** > **iOS-Updaterichtlinien**.

1. Wählen Sie die Richtlinie, die Sie Benutzern zuweisen möchten, und abschließend **Zuweisungen** aus. Es wird der Bereich geöffnet, in dem Sie Azure Active Directory-Sicherheitsgruppen auswählen und der Richtlinie zuweisen können.
2. Klicken Sie auf **Ausgewählte Gruppen**, um den Bereich mit den Azure AD-Sicherheitsgruppen zu öffnen. Bestimmen Sie, wer Zugriff auf die Richtlinie hat, indem Sie sowohl die ein- als auch die auszuschließenden Gruppen zuweisen.
3. Klicken Sie auf **Speichern**, um die Richtlinie für Benutzer bereitzustellen.

Sie haben die Richtlinie auf Ihre Benutzer oder Geräte angewendet. Die von den Benutzern verwendeten Geräte, denen die Richtlinie zugewiesen wurde, werden auf Updatekompatibilität überprüft. Diese Richtlinie unterstützt ebenfalls Geräte ohne Benutzer.

## <a name="monitor-ios-device-installation-failures"></a>Überwachung von Installationsfehlern bei iOS-Geräten
<!-- 1352223 -->
Der Bericht **Installationsfehler bei iOS-Geräten** ist im Bereich **Softwareupdates** verfügbar. Im Bericht wird Ihnen eine Liste der überwachten iOS-Geräte angezeigt, die unter eine iOS-Updaterichtlinie fallen sowie versucht haben, ein Update durchzuführen, jedoch nicht aktualisiert werden konnten. Für jedes Gerät können Sie einen Status anzeigen, warum das Gerät nicht automatisch aktualisiert wurde. Fehlerfreie, aktuelle Geräte werden in der Liste nicht angezeigt. Hierbei entspricht die Definition von „aktuell“ dem neuesten Update, das vom Gerät unterstützt wird.

