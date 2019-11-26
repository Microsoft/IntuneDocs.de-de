---
title: Erstellen von Gerätekonformitätsrichtlinien in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen von Gerätekonformitätsrichtlinien, Übersicht über den Status und die Sicherheitsebenen, Verwendung des InGracePeriod-Status, Arbeiten mit bedingtem Zugriff, Handhabung von Geräten ohne zugewiesene Richtlinie und die Unterschiede bei der Konformität im Azure-Portal und im klassischen Portal in Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c8452f9b56032864380ec703bfd444dc85ef129b
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188264"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Erstellen einer Konformitätsrichtlinie in Microsoft Intune

Konformitätsrichtlinien für Geräte sind ein wichtiges Feature bei der Verwendung von Intune, um die Ressourcen Ihrer Organisation zu schützen. Sie können in Intune Regeln und Einstellungen erstellen, die Geräte erfüllen müssen, um als konform angesehen zu werden, z. B. die mindestens erforderliche Betriebssystemversion. Wenn das Gerät nicht konform ist, können Sie dann den Zugriff auf Daten und Ressourcen mit [bedingtem Zugriff](conditional-access.md) blockieren.

Sie können auch Maßnahmen ergreifen, sollte das Gerät nicht konform sein, z. B. eine Benachrichtigungs-E-Mail an den Benutzer senden. Eine Übersicht der Funktionsweise von Konformitätsrichtlinie und wie Sie diese verwenden können, finden Sie unter [Erste Schritte mit den Gerätekonformitätsrichtlinien in Intune](device-compliance-get-started.md).

Inhalt dieses Artikels

- Liste der Voraussetzungen und Schritte zum Erstellen einer Konformitätsrichtlinie.
- Zuweisen der Richtlinie an einen Benutzer und an eine Gerätegruppe.
- Beschreibung zusätzlicher Funktionen, u. a. Bereichstags zum „Filtern“ Ihrer Richtlinien, und möglicher Maßnahmen für Geräte, die nicht konform sind.
- Liste der Check-In-Aktualisierungszykluszeiten, wenn Geräte Richtlinienaktualisierungen erhalten.

## <a name="before-you-begin"></a>Vorbereitung

Stellen Sie zum Verwenden von Konformitätsrichtlinien folgendes sicher:

- Verwenden Sie folgende Abonnements:

  - Intune
  - Wenn Sie den bedingten Zugriff verwenden, benötigen Sie die Azure Active Directory-Premium-Edition. In der Liste mit den [Preisen für Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/) finden Sie Angaben zu den unterschiedlichen Editionen. Für die Intune-Konformität ist Azure Active Directory nicht erforderlich.

- Verwenden Sie eine unterstützte Plattform:

  - Android-Geräteadministrator
  - Android Enterprise
  - iOS
  - macOS
  - Windows 10
  - Windows 8.1
  - Windows Phone 8.1

- Registrieren Sie Geräte in Intune (nur dann können Sie den Konformitätsstatus ermitteln).

- Registrieren Sie Geräte für einen Benutzer oder registrieren Sie ohne einen Hauptbenutzer. Für mehrere Benutzer registrierte Geräte werden nicht unterstützt.

## <a name="create-the-policy"></a>Erstellen der Richtlinie

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Konformitätsrichtlinien** > **Richtlinie erstellen** aus.

3. Legen Sie die folgenden Eigenschaften fest:

   - **Name**: Geben Sie einen aussagekräftigen Namen für die Richtlinie ein. Benennen Sie Ihre Richtlinien so, dass Sie diese später leicht wiedererkennen. Ein geeigneter Richtlinienname ist z. B. **iOS-Geräte mit Jailbreak als nicht konform markieren**.

   - **Beschreibung**: Geben Sie eine Beschreibung für die Richtlinie ein. Diese Einstellung ist optional, wird jedoch empfohlen.

   - **Plattform**: Wählen Sie die Plattform Ihrer Geräte aus. Folgende Optionen sind verfügbar:
     - **Android-Geräteadministrator**
     - **Android Enterprise**
     - **iOS/iPadOS**
     - **macOS**
     - **Windows Phone 8.1**
     - **Windows 8.1 und höher**
     - **Windows 10 und höher**

     Für *Android Enterprise* müssen Sie dann einen **Profiltyp** auswählen:
     - **Gerätebesitzer**
     - **Arbeitsprofil**

   - **Einstellungen:** In den folgenden Artikel werden die Einstellungen für die einzelnen Plattformen aufgelistet und beschrieben:
     - [Android-Geräteadministrator](compliance-policy-create-android.md)
     - [Android Enterprise](compliance-policy-create-android-for-work.md)
     - [iOS/iPadOS](compliance-policy-create-ios.md)
     - [macOS](compliance-policy-create-mac-os.md)
     - [Windows Phone 8.1, Windows 8.1 und höher](compliance-policy-create-windows-8-1.md)
     - [Windows 10 und höher](compliance-policy-create-windows.md)  

   - **Standorte** *(Android-Geräteadministrator)* : In Ihrer Richtlinie können Sie Konformität durch den Standort des Geräts erzwingen. Sie können vorhandene Standorte auswählen. Haben Sie noch keine Standorte? Unter [Verwenden von Standorten (Netzwerk-Fencing) in Intune](use-network-locations.md) erhalten Sie weitere Informationen.  

   - **Aktionen bei Inkompatibilität**: Für Geräte, die nicht Ihren Konformitätsrichtlinien entsprechen, können Sie Aktionen hinzufügen, die automatisch ausgeführt werden sollen. Sie können den Zeitplan anpassen, anhand dessen das Gerät als nicht konform markiert wird, z.B. nach einem Tag. Sie können auch eine zweite Aktion konfigurieren, durch die E-Mails an Benutzer gesendet werden, wenn das Gerät nicht mehr konform ist.

     Weitere Informationen sowie Informationen zum Erstellen einer E-Mail-Benachrichtigung für Ihre Benutzer finden Sie unter [Hinzufügen von Aktionen für nicht konforme Geräte in Intune](actions-for-noncompliance.md).

     Sie verwenden beispielsweise das Standortfeature und fügen einen Standort zu einer Konformitätsrichtlinie hinzu. Die Standardaktion für Nichtkonformität gilt, wenn Sie mindestens einen Standort auswählen. Wenn das Gerät nicht mit den ausgewählten Standorten verbunden ist, wird es sofort als nicht konform betrachtet. Sie können Ihren Benutzern eine Toleranzperiode gewähren, z.B. einen Tag.

   - **Bereich (Markierungen)** : Bereichsmarkierungen eignen sich zum Zuweisen und Filtern von Richtlinien für bestimmte Gruppen, z. B. Vertrieb, Personalabteilung, Alle Mitarbeiter in North Carolina (USA) usw. Nachdem Sie die Einstellungen hinzugefügt haben, können Sie Ihrer Konformitätsrichtlinie ebenfalls eine Bereichsmarkierung hinzufügen. Im Artikel zum [Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien](../fundamentals/scope-tags.md) finden Sie weitere Informationen.

4. Wählen Sie anschließend **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern. Die Richtlinie wird erstellt und in der Liste angezeigt. Weisen Sie die Richtlinie anschließend Ihrer Gruppe zu.

## <a name="assign-the-policy"></a>Zuweisen der Richtlinie

Wenn eine Richtlinie erstellt wurde, können Sie diese Gruppen zuweisen:

1. Wählen Sie eine Richtlinie aus, die Sie erstellt haben. Vorhandene Richtlinien befinden sich unter **Geräte** > **Konformitätsrichtlinien** > **Richtlinien**.

2. Wählen Sie *Richtlinie* > **Zuweisungen** aus. Sie können Azure Active Directory (AD)-Sicherheitsgruppen ein- oder ausschließen.

3. Wählen Sie **Ausgewählte Gruppen**, um Ihre Azure AD-Sicherheitsgruppen anzuzeigen. Wählen Sie die Gruppen aus, auf die diese Richtlinie angewendet werden soll, und wählen Sie dann **Speichern** aus, um die Richtlinie bereitzustellen.

Die Benutzer oder Geräte, auf die Ihre Richtlinie abzielt, werden hinsichtlich der Konformität ausgewertet, wenn sie mit Intune eingecheckt werden.

### <a name="evaluate-how-many-users-are-targeted"></a>Auswerten der Anzahl der betroffenen Benutzer

Wenn Sie die Richtlinie zuweisen, können Sie auch **auswerten**, wie viele Benutzer betroffen sind. Durch diese Funktion wird eine Benutzeranzahl (jedoch keine Geräteanzahl) berechnet.

1. Wählen Sie in Intune **Geräte** > **Konformitätsrichtlinien** > **Richtlinien** aus.

2. Wählen Sie *Richtlinie* > **Zuweisungen** > **Bewerten** aus. Eine Meldung mit der Anzahl der von dieser Richtlinie betroffenen Benutzer wird angezeigt.

Wenn die Schaltfläche **Evaluate** (Auswerten) ausgegraut ist, stellen Sie sicher, dass die Richtlinie mindestens einer Gruppe zugewiesen wurde.

<!-- ## Actions for noncompliance

For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. You can change the schedule when the device is marked non-compliant, such as after one day. You can also configure a second action that sends an email to the user when the device isn't compliant.

[Add actions for noncompliant devices](actions-for-noncompliance.md) provides more information, including creating a notification email to your users.

For example, you're using the Locations feature, and add a location in a compliance policy. The default action for noncompliance applies when you select at least one location. If the device isn't connected to the selected locations, it's immediately considered not compliant. You can give your users a grace period, such as one day.

## Scope tags

Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. After you add the settings, you can also add a scope tag to your compliance policies. [Use scope tags to filter policies](../fundamentals/scope-tags.md) is a good resource.
-->

## <a name="refresh-cycle-times"></a>Aktualisierungszykluszeit

Intune verwendet verschiedene Aktualisierungszyklen, um nach Updates der Konformitätsrichtlinien zu suchen. Wenn das Gerät kürzlich registriert wurde, wird der Check-In häufiger durchgeführt. Unter [Richtlinien- und Profilaktualisierungszyklen](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) werden die geschätzten Aktualisierungszeiten aufgeführt.

Benutzer können jederzeit die Unternehmensportal-App öffnen und das Gerät synchronisieren, um sofort nach Richtlinienupdates zu suchen.

### <a name="assign-an-ingraceperiod-status"></a>Zuweisung eines InGracePeriod-Status

Der InGracePeriod-Status für eine Konformitätsrichtlinie ist ein Wert. Der Wert wird durch die Kombination der Toleranzzeit eines Geräts und dem tatsächlichen Status eines Geräts für diese Konformitätsrichtlinie ermittelt.

Im Detail bedeutet das: Wenn ein Gerät den Status „NonCompliant“ für eine zugewiesene Richtlinie aufweist und:

- dem Gerät keine Toleranzperiode zugewiesen ist, dann ist der zugewiesene Wert für die Konformitätsrichtlinie „NonCompliant“.
- die Toleranzperiode des Geräts abgelaufen ist, dann lautet der zugewiesene Wert für die Konformitätsrichtlinie „NonCompliant“.
- die Toleranzperiode des Geräts erst in der Zukunft abläuft, lautet der zugewiesene Wert für die Konformitätsrichtlinie „InGracePeriod“.

In der folgenden Tabelle werden diese Punkte zusammengefasst:

|Tatsächlicher Konformitätsstatus|Wert der zugewiesenen Toleranzperiode|Effektiver Konformitätsstatus|
|---------|---------|---------|
|NonCompliant |Keine Toleranzperiode zugewiesen |NonCompliant |
|NonCompliant |Datum vom Vortag|NonCompliant|
|NonCompliant |Datum des folgenden Tages|InGracePeriod|

Weitere Informationen zum Überwachen der Richtlinien zur Gerätekonformität finden Sie unter [Überwachen von Intune-Richtlinien zur Gerätekonformität](compliance-policy-monitor.md).

### <a name="assign-a-resulting-compliance-policy-status"></a>Zuweisen eines resultierenden Konformitätsrichtlinienstatus

Wenn ein Gerät mehrere Konfigurationsprofile hat und es über verschiedene Konformitätsstatus für mindestens zwei zugeordnete Konformitätsprofile verfügt, wird genau ein resultierender Konformitätsstaus zugewiesen. Diese Zuweisung basiert auf einem konzeptuellen Schweregrad, der den einzelnen Konformitätsstatus zugewiesen ist. Jeder Konformitätsstatus verfügt über den folgenden Schweregrad:

|Status  |Schweregrad  |
|---------|---------|
|Unbekannt     |1|
|NotApplicable     |2|
|Kompatibel|3|
|InGracePeriod|4|
|NonCompliant|5|
|Fehler|6|

Hat ein Gerät mehrere Konformitätsrichtlinien, so wird dem Gerät der höchste Schweregrad aller Richtlinien zugewiesen.

Angenommen, einem Gerät sind z. B. drei Konformitätsrichtlinien zugewiesen: ein Status „Unknown“ (Unbekannt, Schweregrad = 1), ein Status „Compliant“ (Konform, Schweregrad = 3) und ein Status „InGracePeriod“ (Befristet, Schweregrad = 4). Der Status „InGracePeriod“ (Befristet) hat den höchsten Schweregrad. Deshalb haben alle drei Richtlinien den Konformitätsstatus „InGracePeriod“ (Befristet).

## <a name="next-steps"></a>Nächste Schritte

[Überwachen von Intune-Richtlinien zur Gerätekompatibilität](compliance-policy-monitor.md).
