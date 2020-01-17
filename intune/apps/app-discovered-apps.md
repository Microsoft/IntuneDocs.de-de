---
title: Ermittelte Apps
titleSuffix: Microsoft Intune
description: Informationen zu den erkannten Apps, die Intune auf einem Gerät gefunden hat.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: f368f5f15f71246a2899f2acb7a791d65df26c99
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857042"
---
# <a name="intune-discovered-apps"></a>Von Intune ermittelte Apps

Bei der von Intune **ermittelten Apps** handelt es sich um eine Liste ermittelter Apps von bei Intune registrierten Geräten in Ihrem Mandanten. Sie fungiert als Softwareinventur für Ihren Mandanten. Bei **Ermittelte Apps** handelt es sich um einen separaten Bericht aus den Berichten zur [App-Installation](apps-monitor.md). Intune sammelt für persönliche Geräte keine Informationen bezüglich nicht verwalteter Anwendungen. Auf Unternehmensgeräten wird jede App erfasst, egal, ob es sich um eine verwaltete App oder eine nicht verwaltete App handelt. Im Folgenden finden Sie die Tabelle, die das erwartete Verhalten darstellt: Im Allgemeinen wird der Bericht alle 7 Tage ab dem Registrierungszeitpunkt aktualisiert (keine wöchentliche Aktualisierung für den gesamten Mandanten). Die einzige Ausnahme zu diesem Aktualisierungszeitraum sind Anwendungsinformationen, die alle 24 Stunden über die Intune-Verwaltungserweiterung für Win32-Apps gesammelt werden.

## <a name="monitor-discovered-apps-with-intune"></a>Überwachen ermittelter Apps mit Intune

Intune stellt eine aggregierte Liste ermittelter Apps auf den bei Intune registrierten Geräten in Ihrem Mandanten bereit.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Apps** > **Überwachen** > **Ermittelte Apps** aus.

>[!NOTE]
>Sie können die Liste exportierter Apps in eine CSV-Datei importieren, indem Sie im Bereich **Ermittelte Apps** die Option **Exportieren** auswählen.
>
>Bei ermittelten Win32-Apps ist derzeit keine Aggregatanzahl vorhanden. Diese Art von Daten kann nur geräteweise angezeigt werden.

Intune enthält auch die Liste der ermittelten Apps für das jeweilige Gerät in Ihrem Mandanten.

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Klicken Sie auf **Geräte** > **Alle Geräte**.
3. Wählen Sie ein Gerät aus.
4. Um ermittelte Apps für dieses Gerät anzuzeigen, wählen Sie **Ermittelte Apps** im Abschnitt **Überwachen** aus.

## <a name="details-of-discovered-apps"></a>Details zu den ermittelten Apps

In der folgenden Liste erhalten Sie Informationen zum Plattformtyp der App, zu den Apps, die für persönliche Geräte überwacht werden, zu Apps, die für unternehmenseigene Geräte überwacht werden, sowie zum Aktualisierungszyklus. Weitere Informationen zu App-Typen, die von Intune unterstützt werden, finden Sie unter [App-Typen in Microsoft Intune](apps-add.md#app-types-in-microsoft-intune).

| Plattform | Benutzereigene Geräte | Unternehmenseigene Geräte | Aktualisierungszyklus |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Windows 10 (Win32-Apps) HINWEIS: [Erfordert die Intune-Verwaltungserweiterung](intune-management-extension.md) auf dem Gerät | Nicht zutreffend | Nur verwaltete Apps | Alle 24 Stunden ab der Geräteregistrierung |
| Windows 10 (Moderne Apps) | Nur verwaltete moderne Apps | Alle auf dem Gerät installierten modernen Apps | Alle 7 Tage ab der Geräteregistrierung |
| Windows 8.1 | Nur verwaltete Apps | Nur verwaltete Apps | Alle 7 Tage ab der Geräteregistrierung |
| Windows Phone 8 | Nur verwaltete Apps | Nur verwaltete Apps | Alle 7 Tage ab der Geräteregistrierung |
| Windows RT | Nur verwaltete Apps | Nur verwaltete Apps | Alle 7 Tage ab der Geräteregistrierung |
| iOS | Nur verwaltete Apps | Alle auf dem Gerät installierten Apps | Alle 7 Tage ab der Geräteregistrierung |
| macOS | Nur verwaltete Apps | Alle auf dem Gerät installierten Apps | Alle 7 Tage ab der Geräteregistrierung |
| Android | Nur verwaltete Apps | Alle auf dem Gerät installierten Apps | Alle 7 Tage ab der Geräteregistrierung |
| Android Enterprise | Nur verwaltete Apps | Nur im Arbeitsprofil installierte Apps | Alle 7 Tage ab der Geräteregistrierung |

> [!NOTE]
> - In Windows 10 Azure AD Hybrid eingebundene Geräte erfassen, wie in der Arbeitsauslastung der App-Verwaltung im Configuration Manager gezeigt, gemäß dem obigen Zeitplan zurzeit keinen App-Bestand über den Eingabemethoden-Editor (IME). Um dieses Problem zu beheben, muss die Arbeitsauslastung der App-Verwaltung im Configuration Manager auf Intune umgestellt werden, damit der IME auf dem Gerät installiert werden kann (der IME ist für die Win32-Inventur und PowerShell-Bereitstellung erforderlich). Beachten Sie, dass jegliche Änderungen oder Aktualisierungen zu diesem Verhalten unter [In der Entwicklung befindliche Microsoft Intune-Features](../fundamentals/in-development.md) und/oder unter [Neuerungen](../fundamentals/whats-new.md) angekündigt werden.
> - Private macOS-Geräte, die vor November 2019 registriert wurden, zeigen möglicherweise weiterhin alle auf dem Gerät installierten Apps an, bis die Geräte neu registriert werden.
> - Vollständig verwaltete und dedizierte Android Enterprise-Geräte zeigen ermittelte Apps nicht an.

Die Anzahl der ermittelten Apps stimmt mit der Statusanzahl von App-Installationen möglicherweise nicht überein. Es gibt folgende Möglichkeiten für Inkonsistenzen:

- Eine Zieländerung einer installierten verwalteten App kann dazu führen, dass die Installationsanzahl im Statusbereich verringert, in den ermittelten Apps aber weiterhin berichtet wird.
- Die Zielgruppenadressierung mehrerer Instanzen derselben App in einem Mandanten führt zu einer unterschiedlichen Anzahl Infolge von potenzieller Überschneidung von Benutzern oder Geräten. Jede Instanz der App zählt sich überschneidende Benutzer, doch bei den ermittelten Apps wird die Anzahl dupliziert.
- Ermittelte Apps und App-Status werden zu unterschiedlichen Zeitintervallen gesammelt, und das könnte zu einer Abweichung bei der App-Anzahl führen.

## <a name="next-steps"></a>Nächste Schritte

- [App-Typen in Microsoft Intune](apps-add.md#app-types-in-microsoft-intune)
- [Überwachen von App-Informationen und -Zuweisungen mit Microsoft Intune](apps-monitor.md)
