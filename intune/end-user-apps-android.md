---
title: Wie Ihre Android-Benutzer Apps erhalten
description: Methoden, um Android-Apps für Endbenutzer verfügbar zu machen.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 878e4d0854722d82eab0545cf3a1ba743f2c52db
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-your-android-users-get-their-apps"></a>Wie Ihre Android-Benutzer Apps erhalten

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Verwenden Sie diese Informationen, um zu verstehen, wie und wo Ihre Android-Endbenutzer die Apps erhalten, die Sie über Microsoft Intune verteilen. Die Informationen können je nach Gerätetyp variieren (native Android-Geräte oder Samsung Knox Standard-Geräte).

## <a name="native-non-samsung-knox-standard-android-devices"></a>Native Android-Geräte (nicht Samsung Knox Standard)

| App-Typ | Branchenspezifische Apps | Play Store-Apps  |
| ------------- |-------------| -----|
| Verfügbare Apps      | Benutzer tippen im Unternehmensportal auf **Installieren**. Es wird eine Benachrichtigung angezeigt, auf die die Benutzer tippen, um die Installation zu starten. Nachdem die Installation erfolgreich durchgeführt wurde, verschwindet die Benachrichtigung. | Benutzer tippen im Unternehmensportal auf die App und werden zu einer App-Seite im Play Store weitergeleitet, auf der sie die Installation starten können.|
| Required apps      | Benutzern wird eine Benachrichtigung angezeigt, die sie nicht verwerfen können, in der sie darauf hingewiesen werden, dass sie eine App installieren müssen. Benutzer tippen auf die Benachrichtigung, um die Installation zu starten. Nachdem die Installation erfolgreich durchgeführt wurde, verschwindet die Benachrichtigung.    | Benutzern wird eine Benachrichtigung angezeigt, die sie nicht verwerfen können, in der sie darauf hingewiesen werden, dass sie eine App installieren müssen. Benutzer tippen auf die Benachrichtigung und werden zu einer App-Seite im Play Store weitergeleitet, auf der sie die Installation starten können. Nachdem die Installation erfolgreich durchgeführt wurde, verschwindet die Benachrichtigung. |

Ihre Benutzer müssen die Installation aus unbekannten Quellen zulassen, damit [branchenspezifische Apps](lob-apps-android.md) installiert werden können. Diese befinden sich normalerweise an zwei verschiedenen Orten:

* **Android 7.1.2 und früher**: **Einstellungen** > **Sicherheit** > **Unknown sources** (Unbekannte Quellen)
* **Android 8.0 und höher**: **Einstellungen** > **Apps & Benachrichtigungen** > **Special app access** > **Install unknown apps**  > **Unternehmensportal** > **Allow from this source** (Spezieller App-Zugriff > Unbekannte App installieren > Unternehmensportal > Aus dieser Quelle zulassen)

In diesem Fall informiert die Unternehmensportal-App den Benutzer und führt ihn zur entsprechenden Einstellung. 


## <a name="samsung-knox-standard-android-devices"></a>Android-Geräte mit Samsung Knox Standard

| App-Typ | Branchenspezifische Apps | Play Store-Apps  |
| ------------- |-------------| -----|
| Verfügbare Apps      | Benutzer tippen im Unternehmensportal auf **Installieren**. Die App wird ohne weiteres Eingreifen der Benutzer installiert. | Benutzer tippen im Unternehmensportal auf die App und werden zu einer App-Seite im Play Store weitergeleitet, auf der sie die Installation starten können.|
| Required apps      | Die App wird ohne weiteres Eingreifen der Benutzer installiert.    | Benutzern wird eine Benachrichtigung angezeigt, die sie nicht verwerfen können, in der sie darauf hingewiesen werden, dass sie eine App installieren müssen. Benutzer tippen auf die Benachrichtigung und werden zu einer App-Seite im Play Store weitergeleitet, auf der sie die Installation starten können. Nachdem die Installation erfolgreich durchgeführt wurde, verschwindet die Benachrichtigung. |

Apps können verwaltet oder nicht verwaltet sein, wie unten beschrieben. Das Verfahren, mit dem Apps in die Verwaltung eingebunden werden, ist das gleiche für alle Arten von Android-Geräten.

**Verwaltete Apps:** Dabei handelt es sich um Apps, die mittels Richtlinien verwaltet werden können. Sie wurden von Intune „umschlossen“ oder mit dem Intune App SDK erstellt. Diese Apps können von Intune verwaltet werden, und ihnen lassen sich Anwendungsrichtlinien zuweisen.

**Nicht verwaltete Apps:** Dabei handelt es sich um Apps, die nicht über Richtlinien verwaltet werden können. Diese Apps wurden nicht von Intune „umschlossen“ oder sind nicht in das Intune SDK integriert. Diesen Apps lassen sich keine Anwendungsrichtlinien zuweisen.

### <a name="see-also"></a>Siehe auch
[Hinzufügen von Apps mit Microsoft Intune](apps-add.md)

[Wie Ihre iOS-Benutzer Apps erhalten](end-user-apps-ios.md)

[Wie Ihre Windows-Benutzer Apps erhalten](end-user-apps-windows.md)
