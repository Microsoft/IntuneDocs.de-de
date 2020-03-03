---
title: Wie Ihre Android-Benutzer Apps erhalten
description: Methoden, um Android-Apps für Endbenutzer verfügbar zu machen.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 231b30e93a3e56811e1569c32cc1286e02320f0d
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514403"
---
# <a name="how-your-android-users-get-their-apps"></a>Wie Ihre Android-Benutzer Apps erhalten

Dieser Artikel bietet grundlegende Informationen dazu, wie und wo Ihre Android-Endbenutzer die Apps erhalten, die Sie über Microsoft Intune verteilen. Die Informationen können je nach Gerätetyp variieren (native Android-Geräte oder Samsung Knox Standard-Geräte).

## <a name="native-non-samsung-knox-standard-android-devices"></a>Native Android-Geräte (nicht Samsung Knox Standard)

| App-Typ | Branchenspezifische Apps | Play Store-Apps  |
| ------------- |-------------| -----|
| Verfügbare Apps      | Benutzer tippen im Unternehmensportal auf **Installieren**. Es wird eine Benachrichtigung angezeigt, auf die die Benutzer tippen, um die Installation zu starten. Nachdem die Installation erfolgreich durchgeführt wurde, verschwindet die Benachrichtigung. | Benutzer tippen im Unternehmensportal auf die App und werden zu einer App-Seite im Play Store weitergeleitet. Dort starten sie die Installation.|
| Required apps      | Benutzern wird eine Benachrichtigung angezeigt, die sie nicht verwerfen können und in der sie darauf hingewiesen werden, dass sie eine App installieren müssen. Benutzer tippen auf die Benachrichtigung, um die Installation zu starten. Nachdem die Installation erfolgreich durchgeführt wurde, verschwindet die Benachrichtigung.    | Benutzern wird eine Benachrichtigung angezeigt, die sie nicht verwerfen können und in der sie darauf hingewiesen werden, dass sie eine App installieren müssen. Benutzer tippen auf die Benachrichtigung und werden zu einer App-Seite im Play Store weitergeleitet. Dort starten sie die Installation. Nachdem die Installation erfolgreich durchgeführt wurde, verschwindet die Benachrichtigung. |

Ihre Benutzer müssen die Installation aus unbekannten Quellen zulassen, damit [branchenspezifische Apps](../apps/lob-apps-android.md) installiert werden können. Diese Einstellung befindet sich normalerweise an zwei verschiedenen Stellen:

* **Android 7.1.2 und höher:** **Einstellungen** > **Sicherheit** > **Unknown sources** (Unbekannte Quellen)
* **Android 8.0 und höher:** **Einstellungen** > **Apps & Benachrichtigungen** > **Special app access** > **Install unknown apps** > **Unternehmensportal** > **Allow from this source** (Spezieller App-Zugriff > Unbekannte App installieren > Unternehmensportal > Aus dieser Quelle zulassen)

In diesem Fall informiert die Unternehmensportal-App den Benutzer und führt ihn zur entsprechenden Einstellung. 

## <a name="samsung-knox-standard-android-devices"></a>Android-Geräte mit Samsung Knox Standard

| App-Typ | Branchenspezifische Apps | Play Store-Apps  |
| ------------- |-------------| -----|
| Verfügbare Apps      | Benutzer tippen im Unternehmensportal auf **Installieren**. Die App wird ohne weiteres Eingreifen der Benutzer installiert. | Benutzer tippen im Unternehmensportal auf die App und werden zu einer App-Seite im Play Store weitergeleitet. Dort starten sie die Installation.|
| Required apps      | Die App wird ohne weiteres Eingreifen der Benutzer installiert.    | Benutzern wird eine Benachrichtigung angezeigt, die sie nicht verwerfen können und in der sie darauf hingewiesen werden, dass sie eine App installieren müssen. Benutzer tippen auf die Benachrichtigung und werden zu einer App-Seite im Play Store weitergeleitet. Dort starten sie die Installation. Nachdem die Installation erfolgreich durchgeführt wurde, verschwindet die Benachrichtigung. |

Apps können verwaltet oder nicht verwaltet sein, wie unten beschrieben. Das Verfahren, mit dem Apps in die Verwaltung eingebunden werden, ist das gleiche für alle Arten von Android-Geräten.

**Verwaltete Apps**: Dabei handelt es sich um Apps, die mittels Richtlinien verwaltet werden. Sie wurden von Intune „umschlossen“ oder mit dem Intune App SDK erstellt. Diese Apps können von Intune verwaltet werden, und ihnen lassen sich Anwendungsrichtlinien zuweisen.

**Nicht verwaltete Apps**: Dabei handelt es sich um Apps, die nicht mittels Richtlinien verwaltet werden. Diese wurden nicht von Intune „umschlossen“ oder enthalten das Intune App SDK nicht. Diesen Apps können keine Anwendungsrichtlinien zugewiesen werden.

## <a name="zebra-devices-with-zebra-mobility-extensions"></a>Zebra-Geräte mit Zebra Mobility Extensions

Intune verwendet das Zebra Mobility Extensions-Toolkit (MX), um Apps unbeaufsichtigt auf Zebra-Geräten zu installieren, die vom Geräteadministrator verwaltet werden. Mit diesem Feature können Sie Apps ohne Benutzereingriff auf Zebra-Geräten bereitstellen und aktualisieren. Wenn die MX-Version auf Ihrem Gerät 4.2 oder älter ist, werden Apps nicht unbeaufsichtigt installiert. Weitere Informationen finden Sie auf der Zebra-Website unter [Full MX Feature Matrix](http://techdocs.zebra.com/mx/compatibility/) (Vollständige Featurematrix für Mobility Extensions).

Auf Zebra-Geräten bereitgestellte branchenspezifische Apps müssen über einen öffentlichen Ort auf dem Gerät installiert werden. Möglicherweise greifen andere Apps und Dienste, die auch Zugriff auf den öffentlichen Speicher auf dem Gerät haben, auf das APK-App-Paket zu. In der Regel erfolgt dieser Zugriff in einem kleinen Zeitfenster zwischen dem Abschluss des App-Downloads und dem Start der Installation. Dieses Fenster kann für einen zeitgesteuerten Angriff missbraucht werden. Beispielsweise kann während dieses Zeitfensters ein APK-Paket geändert werden. Intune minimiert den Zeitraum, für den sich die APK-Datei im öffentlichen Speicher befindet, und lässt keine Installation nicht signierter Apps zu. Um das Sicherheitsrisiko so weit wie möglich zu reduzieren, stellen Sie sicher, dass die APK-Dateien, die Sie hochladen, keine vertraulichen Informationen enthalten.

## <a name="see-also"></a>Weitere Informationen:

[Hinzufügen von Apps mit Microsoft Intune](../apps/apps-add.md)

[Wie Ihre iOS-/iPadOS-Benutzer Apps erhalten](end-user-apps-ios.md)

[Wie Ihre Windows-Benutzer Apps erhalten](end-user-apps-windows.md)
