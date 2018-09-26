---
title: Behandlung von Problemen mit Richtlinien in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Allgemeine Probleme oder Probleme und Lösungen bei Verwendung von Richtlinien in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1d656dcc8c3abcf3a4b0a9c6aacbc42eb896289f
ms.sourcegitcommit: 7c70c3e0fcae7c4fa8c9e108aafb1cebb366332d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "44096499"
---
# <a name="troubleshoot-policies-in-intune"></a>Behandlung von Richtlinienproblemen in Intune

Wenn beim Bereitstellen und Verwalten von Intune-Richtlinien Probleme auftreten, beginnen Sie hier. In diesem Artikel werden einige der am häufigsten auftretenden Probleme sowie mögliche Lösungen beschrieben.

## <a name="general-issues"></a>Allgemeine Probleme

### <a name="was-a-deployed-policy-applied-to-the-device"></a>Wurde eine bereitgestellte Richtlinie auf das Gerät angewendet?
**Problem:** Sie sind sich nicht sicher, ob eine Richtlinie ordnungsgemäß angewendet wurde.

In Intune > **Geräte** > **Alle Geräte** > Auswahl des Geräts > **Gerätekonfiguration** werden die Richtlinien jedes Geräts aufgelistet. Jede Richtlinie verfügt über einen **Status**. Wenn alle für das Gerät geltenden Richtlinien sowie die Einschränkungen und Anforderungen der Hardware und des Betriebssystems zusammen betrachtet werden, wird der Status festgelegt. Mögliche Status sind:

- **Konform**: Das Gerät hat die Richtlinie empfangen und meldet dem Dienst, dass es der Einstellung entspricht.

- **Nicht zutreffend**: Die Richtlinieneinstellung ist nicht zutreffend. Beispielsweise wären E-Mail-Einstellungen für iOS-Geräte nicht auf ein Android-Gerät anwendbar.

- **Ausstehend**: Die Richtlinie wurde an das Gerät gesendet, hat aber noch keinen Status an den Dienst gemeldet. Beispiel: Verschlüsselung unter Android erfordert, dass der Benutzer die Verschlüsselung aktiviert, und sie könnte als ausstehend angezeigt werden.

> [!NOTE]
> Wenn zwei Richtlinien mit unterschiedlichen Einschränkungsstufen für das gleiche Gerät gelten, wird die restriktivere Richtlinie angewendet.

## <a name="issues-with-enrolled-devices"></a>Probleme mit registrierten Geräten

### <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Warnung: Fehler beim Speichern von Zugriffsregeln in Exchange
**Problem**: Sie erhalten die Warnung **Fehler beim Speichern von Zugriffsregeln in Exchange**  in der Verwaltungskonsole.

Wenn Sie Richtlinien im Exchange-Arbeitsbereich „Lokale Richtlinie“ in der Verwaltungskonsole erstellt haben, aber Office 365 verwenden, werden die konfigurierten Richtlinieneinstellungen von Intune nicht erzwungen. Beachten Sie die Richtlinienquelle in der Warnung.  Löschen Sie im Exchange-Arbeitsbereich „Lokale Richtlinie“ die Legacyregeln. Die Legacyregeln sind globale Exchange-Regeln in Intune für lokales Exchange und für Office 365 nicht relevant. Erstellen Sie dann eine neue Richtlinie für Office 365.

### <a name="cannot-change-security-policy-for-various-enrolled-devices"></a>Sicherheitsrichtlinie für verschiedene registrierte Geräte kann nicht geändert werden
Windows Phone-Geräte gestatten keine Verringerung der Sicherheitsstufe in Sicherheitsrichtlinien, die über MDM oder EAS festgelegt werden, nachdem diese festgelegt wurden. Angenommen, Sie legen ein **Kennwort mit Mindestanzahl von Zeichen** auf 8 fest und versuchen dann, diesen Wert auf 4 zu verringern. Die restriktivere Richtlinie wurde bereits auf das Gerät angewendet.

Abhängig von der Geräteplattform müssen Sie, wenn Sie die Richtlinie auf einen niedrigeren Sicherheitswert ändern möchten, Sicherheitsrichtlinien möglicherweise zurücksetzen.

In Windows wischen Sie beispielsweise auf dem Desktop von rechts nach innen, um die Leiste **Charms** zu öffnen. Wählen Sie **Einstellungen** > **Systemsteuerung** und dann **Benutzerkonten** aus. Wählen Sie auf der linken Seite den Link **Sicherheitsrichtlinien zurücksetzen** und dann **Richtlinien zurücksetzen** aus.

Andere MDM-Geräte, wie Android, Windows Phone 8.1 und höher sowie iOS, müssen möglicherweise außer Kraft gesetzt und bei dem Dienst neu registriert werden, damit Sie eine weniger restriktive Richtlinie anwenden können.

## <a name="issues-with-pcs-that-run-the-intune-software-client"></a>Probleme mit PCs mit dem Intune-Softwareclient

Gilt für das klassische Portal.

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Fehler in „policyplatform.log“ im Zusammenhang mit der Microsoft Intune-Richtlinie
Bei Windows-PCs, die mit dem Intune-Softwareclient verwaltet werden, können Richtlinienfehler in der Datei „policyplatform.log“ das Ergebnis nicht standardmäßiger Einstellungen in der Windows-Benutzerkontensteuerung (UAC) auf dem Gerät sein. Einige nicht standardmäßige UAC-Einstellungen können Microsoft Intune-Clientinstallationen und Richtlinienausführungen beeinträchtigen.

#### <a name="resolve-uac-issues"></a>Beheben von UAC-Problemen

1. Setzen Sie den Computer außer Betrieb. Siehe [Entfernen von Geräten](devices-wipe.md).

2. Warten Sie 20 Minuten, bis die Clientsoftware entfernt wurde.

    > [!NOTE]
    > Versuchen Sie nicht, den Client über „Programme und Funktionen“ zu entfernen.

3. Geben Sie im Startmenü **UAC** ein, um die Einstellungen der Benutzerkontensteuerung zu öffnen.

4. Verschieben Sie den Schieberegler für Benachrichtigungen auf die Standardeinstellung.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>FEHLER: Der Wert kann nicht vom Computer abgerufen werden, 0x80041013
Dieser Fehler tritt auf, wenn die Zeit auf dem lokalen System um mindestens fünf Minuten abweicht. Wenn die Zeit auf dem lokalen Computer nicht synchron ist, schlagen sichere Transaktionen fehl, da der Zeitstempel ungültig ist.

Um dieses Problem zu beheben, legen Sie die lokale Systemzeit so genau wie möglich auf die Internetzeit oder die auf den Domänencontrollern im Netzwerk eingestellte Zeit fest.

### <a name="next-steps"></a>Nächste Schritte
Wenn diese Informationen zur Problembehandlung nicht hilfreich waren, wenden Sie sich wie in [Anfordern von Support für Microsoft Intune](get-support.md) beschrieben an den Microsoft-Support.
