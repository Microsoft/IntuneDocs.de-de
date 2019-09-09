---
title: Ermittelte Apps
titleSuffix: Microsoft Intune
description: Informationen zu den erkannten Apps, die Intune auf einem Gerät gefunden hat.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d545e5848330e8c4f34eca21a992ad05ca8c85d
ms.sourcegitcommit: ffbd1542d33810ab97a0be8faf26f8061328c228
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206406"
---
# <a name="intune-discovered-apps"></a>Von Intune ermittelte Apps

Bei der von Intune **ermittelten Apps** handelt es sich um eine Liste ermittelter Apps von bei Intune registrierten Geräten in Ihrem Mandanten. Sie fungiert als Softwareinventur für Ihren Mandanten. Bei **Ermittelte Apps** handelt es sich um einen separaten Bericht aus den Berichten zur [App-Installation](apps-monitor.md). Intune sammelt für persönliche Geräte keine Informationen bezüglich nicht verwalteter Anwendungen. Auf Unternehmensgeräten wird jede App erfasst, egal, ob es sich um eine verwaltete App oder eine nicht verwaltete App handelt. Im Folgenden finden Sie die Tabelle, die das erwartete Verhalten darstellt: Im Allgemeinen wird der Bericht alle 7 Tage ab dem Registrierungszeitpunkt aktualisiert (keine wöchentliche Aktualisierung für den gesamten Mandanten). Die einzige Ausnahme zu diesem Aktualisierungszeitraum sind Anwendungsinformationen, die alle 24 Stunden über die Intune-Verwaltungserweiterung für Win32-Apps gesammelt werden.

## <a name="monitor-discovered-apps-with-intune"></a>Überwachen ermittelter Apps mit Intune

Intune stellt eine aggregierte Liste ermittelter Apps auf den bei Intune registrierten Geräten in Ihrem Mandanten bereit.

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie im Bereich **Intune** **Client-Apps** > **Ermittelte Apps** aus.

>[!NOTE]
>Sie können die Liste exportierter Apps in eine CSV-Datei importieren, indem Sie auf dem Blatt **Ermittelte Apps** die Option **Exportieren** auswählen.
>
>Bei ermittelten Win32-Apps ist derzeit keine Aggregatanzahl vorhanden. Diese Art von Daten kann nur geräteweise angezeigt werden.

Intune enthält auch die Liste der ermittelten Apps für das jeweilige Gerät in Ihrem Mandanten. 

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie im Bereich Intune **Geräte** > **Alle Geräte** aus.
3. Wählen Sie ein Gerät aus.
4. Um ermittelte Apps für dieses Gerät anzuzeigen, wählen Sie **Ermittelte Apps** im Abschnitt **Überwachen** aus. 

## <a name="details-of-discovered-apps"></a>Details zu den ermittelten Apps

In der folgenden Liste erhalten Sie Informationen zum Plattformtyp der App, zu den Apps, die für persönliche Geräte überwacht werden, zu Apps, die für unternehmenseigene Geräte überwacht werden, sowie zum Aktualisierungszyklus. Weitere Informationen zu App-Typen, die von Intune unterstützt werden, finden Sie unter [App-Typen in Microsoft Intune](apps-add.md#app-types-in-microsoft-intune).

| Plattform | Benutzereigene Geräte | Unternehmenseigene Geräte | Aktualisierungszyklus |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Windows 10 (Win32-Apps) HINWEIS: [Erfordert die Intune-Verwaltungserweiterung](intune-management-extension.md) auf dem Gerät | Nicht zutreffend | Alle Win32-Apps, die in der Liste zum Hinzufügen oder Entfernen von Programmen enthalten sind | Alle 24 Stunden ab der Geräteregistrierung |
| Windows 10 (Moderne Apps) | Nur verwaltete moderne Apps | Alle auf dem Gerät installierten modernen Apps | Alle 7 Tage ab der Geräteregistrierung |
| Windows 8.1 | Nur verwaltete Apps | Nur verwaltete Apps | Alle 7 Tage ab der Geräteregistrierung |
| Windows Phone 8 | Nur verwaltete Apps | Nur verwaltete Apps | Alle 7 Tage ab der Geräteregistrierung |
| Windows RT | Nur verwaltete Apps | Nur verwaltete Apps | Alle 7 Tage ab der Geräteregistrierung |
| iOS | Nur verwaltete Apps | Alle auf dem Gerät installierten Apps | Alle 7 Tage ab der Geräteregistrierung |
| macOS | Alle auf dem Gerät installierten Apps | Alle auf dem Gerät installierten Apps | Alle 7 Tage ab der Geräteregistrierung |
| Android | Nur verwaltete Apps | Alle auf dem Gerät installierten Apps | Alle 7 Tage ab der Geräteregistrierung |
| Android Enterprise | Nur verwaltete Apps | Nur im Arbeitsprofil installierte Apps | Alle 7 Tage ab der Geräteregistrierung |

> [!NOTE]
>Für in Hybrid-Azure AD eingebundene Windows 10-Geräte mit der Intune-Verwaltungserweiterung wird der App-Bestand zurzeit nicht gemäß dem obigen Zeitplan erfasst. Dies ist ein bekanntes Problem. Jegliche Änderungen oder Aktualisierungen zu diesem Verhalten werden in [In der Entwicklung befindliche Microsoft Intune-Features](in-development.md) und/oder in [Neuerungen](whats-new.md) angekündigt.

Die Anzahl der ermittelten Apps stimmt mit der Statusanzahl von App-Installationen möglicherweise nicht überein. Es gibt folgende Möglichkeiten für Inkonsistenzen:
- Eine Zieländerung einer installierten verwalteten App kann dazu führen, dass die Installationsanzahl im Statusblade verringert, in den ermittelten Apps aber weiterhin berichtet wird.
- Die Zielgruppenadressierung mehrerer Instanzen derselben App in einem Mandanten führt zu einer unterschiedlichen Anzahl Infolge von potenzieller Überschneidung von Benutzern oder Geräten. Jede Instanz der App zählt sich überschneidende Benutzer, doch bei den ermittelten Apps wird die Anzahl dupliziert.
- Ermittelte Apps und App-Status werden zu unterschiedlichen Zeitintervallen gesammelt, und das könnte zu einer Abweichung bei der App-Anzahl führen.

## <a name="next-steps"></a>Nächste Schritte

- [App-Typen in Microsoft Intune](apps-add.md#app-types-in-microsoft-intune)
- [Überwachen von App-Informationen und -Zuweisungen mit Microsoft Intune](apps-monitor.md)
