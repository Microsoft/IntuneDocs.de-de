---
title: Gerätekonformitätsrichtlinien in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie Gerätekonformitätsrichtlinien,erhalten Sie eine Übersicht über Status- und die Sicherheitsebenen, verwenden Sie den InGracePeriod-Status, arbeiten Sie mit bedingtem Zugriff, verwalten Sie Geräte ohne zugewiesene Richtlinie, und erfahren Sie mehr zu den Unterschieden bei der Konformität im Azure-Portal und im klassischen Portal in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: da0aa98774f25bf290391225c6ccae56a3859c22
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570415"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Erstellen einer Konformitätsrichtlinie in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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
  - Wenn Sie bedingten Zugriff verwenden, benötigen Sie die Azure Active Directory-Premium-Edition. In der Liste mit den [Preisen für Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/) finden Sie Angaben zu den unterschiedlichen Editionen. Für die Intune-Konformität ist Azure Active Directory nicht erforderlich.

- Verwenden Sie eine unterstützte Plattform:

  - Android
  - Android Enterprise
  - iOS
  - macOS (Vorschau)
  - Windows 10
  - Windows 8.1
  - Windows Phone 8.1

- Registrieren Sie Geräte in Intune (nur dann können Sie den Konformitätsstatus ermitteln).

- Registrieren Sie Geräte für einen Benutzer oder registrieren Sie ohne einen Hauptbenutzer. Für mehrere Benutzer registrierte Geräte werden nicht unterstützt.

## <a name="create-the-policy"></a>Erstellen der Richtlinie

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.
2. Wählen Sie **Gerätekompatibilität** aus. Hierzu stehen Ihnen folgende Optionen zur Verfügung:

    - **Übersicht:** Zusammenfassung und Anzahl der Geräte, die nicht konform sind, nicht ausgewertet wurden usw. Außerdem werden die Richtlinien und einzelnen Einstellungen in Ihren Richtlinien angezeigt. Unter [Monitor Intune device compliance policies (Überwachen von Intune-Richtlinien zur Gerätekonformität)](compliance-policy-monitor.md) erhalten Sie weitere Informationen.
    - **Verwalten:** Erstellen Sie Geräterichtlinien, senden Sie [Benachrichtigungen](quickstart-send-notification.md) an nicht konform Geräte, und aktivieren Sie das [Netzwerkfencing](use-network-locations.md).
    - **Überwachen:** Überprüfen Sie den Konformitätsstatus Ihrer Geräte auf Ebene von Einstellungen und Richtlinien. Unter [Monitor Intune device compliance policies (Überwachen von Intune-Richtlinien zur Gerätekonformität)](compliance-policy-monitor.md) erhalten Sie weitere Informationen. Sehen Sie sich auch die Protokolle und den Status des Bedrohungs-Agents Ihrer Geräte an.
    - **Setup:** Verwenden Sie die [integrierten Konformitätsrichtlinie](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies), aktivieren Sie [Windows Defender Advanced Threat Protection](advanced-threat-protection.md), fügen Sie einen [Mobile Threat Defense-Connector](mobile-threat-defense.md) hinzu, und verwenden Sie [Jamf](conditional-access-integrate-jamf.md).

3. Klicken Sie auf **Richtlinien** > **Richtlinie erstellen**. Geben Sie die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen aussagekräftigen Namen für die Richtlinie ein. Benennen Sie Ihre Richtlinien so, dass Sie diese später leicht wiedererkennen. Ein geeigneter Richtlinienname ist z. B. **iOS-Geräte mit Jailbreak als nicht konform markieren**.
    - **Beschreibung**: Geben Sie eine Beschreibung für die Richtlinie ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie die Plattform Ihrer Geräte aus. Folgende Optionen sind verfügbar:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 und höher**
       - **Windows 10 und höher**

    - **Einstellungen:** In den folgenden Artikel werden die Einstellungen für die einzelnen Plattformen aufgelistet und beschrieben:

        - [Android](compliance-policy-create-android.md)
        - [Android Enterprise](compliance-policy-create-android-for-work.md)
        - [iOS](compliance-policy-create-ios.md)
        - [macOS](compliance-policy-create-mac-os.md)
        - [Windows Phone 8.1, Windows 8.1 und höher](compliance-policy-create-windows-8-1.md)
        - [Windows 10 und höher](compliance-policy-create-windows.md)

4. Wählen Sie anschließend **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern. Die Richtlinie wird erstellt und in der Liste angezeigt. Weisen Sie die Richtlinie anschließend Ihrer Gruppe zu.

## <a name="assign-user-groups"></a>Zuweisen von Benutzergruppen

Wenn eine Richtlinie erstellt wurde, können Sie diese Gruppen zuweisen:

1. Wählen Sie eine Richtlinie aus, die Sie erstellt haben. Vorhandene Richtlinien befinden sich unter **Gerätekompatibilität** > **Richtlinien**.
2. Klicken Sie auf die Richtlinie und anschließend auf **Assignments** (Zuweisungen). Sie können Azure Active Directory (AD)-Sicherheitsgruppen ein- oder ausschließen.
3. Wählen Sie **Ausgewählte Gruppen**, um Ihre Azure AD-Sicherheitsgruppen anzuzeigen. Wählen Sie die Benutzergruppen aus, auf die diese Richtlinie angewendet werden soll, und klicken Sie dann auf **Save** (Speichern), um die Richtlinie für die Benutzer bereitzustellen.

Sie haben die Richtlinie auf Benutzer angewendet. Die von den Benutzern verwendeten Geräte, für die die Richtlinie gilt, werden auf Konformität überprüft.

### <a name="evaluate-how-many-users-are-targeted"></a>Auswerten der Anzahl der betroffenen Benutzer

Wenn Sie die Richtlinie zuweisen, können Sie auch **auswerten**, wie viele Benutzer betroffen sind. Durch diese Funktion wird eine Benutzeranzahl (jedoch keine Geräteanzahl) berechnet.

1. Klicken Sie in Intune auf **Device compliance** > **Policies** (Gerätekonformität > Richtlinien).
2. Wählen Sie eine Richtlinie aus, und klicken Sie dann auf **Assignments** > **Evaluate** (Zuweisungen > Auswerten). Eine Meldung mit der Anzahl der von dieser Richtlinie betroffenen Benutzer wird angezeigt.

Wenn die Schaltfläche **Evaluate** (Auswerten) ausgegraut ist, stellen Sie sicher, dass die Richtlinie mindestens einer Gruppe zugewiesen wurde.

## <a name="actions-for-noncompliance"></a>Aktionen bei Inkompatibilität

Für Geräte, die nicht Ihren Konformitätsrichtlinien entsprechen, können Sie Aktionen hinzufügen, die automatisch ausgeführt werden sollen. Sie können den Zeitplan anpassen, anhand dessen das Gerät als nicht konform markiert wird, z.B. nach einem Tag. Sie können auch eine zweite Aktion konfigurieren, durch die E-Mails an Benutzer gesendet werden, wenn das Gerät nicht mehr konform ist.

Weitere Informationen sowie Informationen zum Erstellen einer E-Mail-Benachrichtigung für Ihre Benutzer finden Sie unter [Hinzufügen von Aktionen für nicht konforme Geräte in Intune](actions-for-noncompliance.md).

Sie verwenden beispielsweise das Standortfeature und fügen einen Standort zu einer Konformitätsrichtlinie hinzu. Die Standardaktion für Nichtkonformität gilt, wenn Sie mindestens einen Standort auswählen. Wenn das Gerät nicht mit den ausgewählten Standorten verbunden ist, wird es sofort als nicht konform betrachtet. Sie können Ihren Benutzern eine Toleranzperiode gewähren, z.B. einen Tag.

## <a name="scope-tags"></a>Festlegen von Tags

Bereichsmarkierungen eignen sich zum Zuweisen und Filtern von Richtlinien für bestimmte Gruppen, z. B. Vertrieb, Personalabteilung, Alle Mitarbeiter in North Carolina (USA) usw. Nachdem Sie die Einstellungen hinzugefügt haben, können Sie Ihrer Konformitätsrichtlinie ebenfalls eine Bereichsmarkierung hinzufügen. Im Artikel zum [Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien](scope-tags.md) finden Sie weitere Informationen.

## <a name="refresh-cycle-times"></a>Aktualisierungszykluszeit

Bei der Prüfung der Konformität verwendet Intune den gleichen Aktualisierungszyklus wie für Konfigurationsprofile. Im Allgemeinen gelten folgende Zeiten:

| Plattform | Aktualisierungszyklus|
| --- | --- |
| iOS | Alle 6 Stunden |
| macOS | Alle 6 Stunden |
| Android | Alle 8 Stunden |
| Windows 10-PCs, die als Geräte registriert sind | Alle 8 Stunden |
| Windows Phone | Alle 8 Stunden |
| Windows 8.1 | Alle 8 Stunden |

Wenn das Gerät gerade registriert wurde, wird der Konformitäts-Check-In häufiger durchgeführt:

| Plattform | Häufigkeit |
| --- | --- |
| iOS | Alle 15 Minuten für 6 Stunden und dann alle 6 Stunden |  
| macOS | Alle 15 Minuten für 6 Stunden und dann alle 6 Stunden | 
| Android | Alle 3 Minuten für 15 Minuten, dann alle 15 Minuten für 2 Stunden und dann alle 8 Stunden | 
| Windows 10-PCs, die als Geräte registriert sind | Alle 3 Minuten für 30 Minuten und dann alle 8 Stunden | 
| Windows Phone | Alle 5 Minuten für 15 Minuten, dann alle 15 Minuten für 2 Stunden und dann alle 8 Stunden | 
| Windows 8.1 | Alle 5 Minuten für 15 Minuten, dann alle 15 Minuten für 2 Stunden und dann alle 8 Stunden | 

Benutzer können jederzeit die Unternehmensportal-App öffnen und das Gerät synchronisieren, um sofort zu prüfen, ob neue Richtlinien verfügbar sind.

### <a name="assign-an-ingraceperiod-status"></a>Zuweisung eines InGracePeriod-Status

Der InGracePeriod-Status für eine Konformitätsrichtlinie ist ein Wert. Der Wert wird durch die Kombination der Toleranzzeit eines Geräts und dem tatsächlichen Status eines Geräts für diese Konformitätsrichtlinie ermittelt.

Im Detail bedeutet das: Wenn ein Gerät den Status „NonCompliant“ für eine zugewiesene Richtlinie aufweist und:

- dem Gerät keine Toleranzperiode zugewiesen ist, lautet der zugewiesene Wert für die Konformitätsrichtlinie „NonCompliant“.
- die Toleranzperiode des Geräts abgelaufen ist, lautet der zugewiesene Wert für die Konformitätsrichtlinie „NonCompliant“.
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