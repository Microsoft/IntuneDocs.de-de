---
title: Behandlung von Problemen mit Richtlinien
description: Behandeln Sie Richtlinienkonfigurationsprobleme.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 01/04/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9d9fa95e7992488e8c25e713136be17bcd1580bf
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshoot-policies-in-microsoft-intune"></a>Behandlung von Problemen mit Richtlinien in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Wenn beim Bereitstellen und Verwalten von Intune-Richtlinien Probleme auftreten, beginnen Sie hier. In diesem Thema werden einige allgemeine Probleme, die auftreten können, sowie deren Lösungen behandelt.

## <a name="general-issues"></a>Allgemeine Probleme

### <a name="was-a-deployed-policy-applied-to-the-device"></a>Wurde eine bereitgestellte Richtlinie auf das Gerät angewendet?
**Problem:** Sie sind sich nicht sicher, ob eine Richtlinie ordnungsgemäß angewendet wurde.

In der Intune-Verwaltungskonsole verfügt jedes Gerät unter **Geräteeigenschaften**über eine Registerkarte „Richtlinie“. Jede Richtlinie verfügt über einen **vorgesehenen Wert** und einen **Status**. Den vorgesehenen Wert möchten Sie durch Zuweisen der Richtlinie erzielen. Der Status gibt an, was tatsächlich angewendet wurde, wenn alle für das Gerät geltenden Richtlinien sowie die Einschränkungen und Anforderungen der Hardware und des Betriebssystems zusammen betrachtet werden. Mögliche Status sind:

-   **Konform**: Das Gerät hat die Richtlinie empfangen und meldet dem Dienst, dass es der Einstellung entspricht.

-   **Nicht zutreffend**: Die Richtlinieneinstellung ist nicht zutreffend. Beispielsweise wären E-Mail-Einstellungen für iOS-Geräte nicht auf ein Android-Gerät anwendbar.

-   **Ausstehend**: Die Richtlinie wurde an das Gerät gesendet, hat aber noch keinen Status an den Dienst gemeldet. Beispiel: Verschlüsselung unter Android erfordert, dass der Benutzer die Verschlüsselung aktiviert, und sie könnte aus diesem Grund ausstehen.

Der folgende Screenshot zeigt zwei eindeutige Beispiele:

-   **Einfache Kennwörter zulassen** ist auf **Ja**gesetzt, wie in der Spalte **Beabsichtigter Wert** gezeigt, der **Status** ist jedoch **Nicht zutreffend**. Dies liegt daran, dass einfache Kennwörter für Android-Geräte nicht unterstützt werden.

-   Ebenso gilt das erweiterte Richtlinienelement **E-Mail-Einstellungen für iOS-Geräte** nicht für dieses Gerät, da es ein Android-Gerät ist.

![Intune-Geräterichtlinie](../media/Intune-Device-Policy-v.2.jpg)

> [!NOTE]
> Denken Sie daran: Wenn zwei Richtlinien mit unterschiedlichen Einschränkungsstufen für das gleiche Gerät gelten, wird in der Praxis die restriktivere Richtlinie angewendet.


## <a name="issues-with-enrolled-devices"></a>Probleme mit registrierten Geräten

### <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Warnung: Fehler beim Speichern von Zugriffsregeln in Exchange
**Problem**: Sie erhalten die Warnung **Fehler beim Speichern von Zugriffsregeln in Exchange**  in der Verwaltungskonsole.

Wenn Sie Richtlinien im Exchange-Arbeitsbereich „Lokale Richtlinie“ in der Verwaltungskonsole erstellt haben, aber Office 365 verwenden, werden die konfigurierten Richtlinieneinstellungen von Intune nicht erzwungen. Beachten Sie die Richtlinienquelle in der Warnung.  Löschen Sie im Exchange-Arbeitsbereich „Lokale Richtlinie“ die Legacyregeln, weil diese in Intune globale Exchange-Regeln für lokales Exchange und für Office 365 nicht relevant sind. Erstellen Sie dann eine neue Richtlinie für Office 365.

### <a name="cannot-change-security-policy-for-various-enrolled-devices"></a>Sicherheitsrichtlinie für verschiedene registrierte Geräte kann nicht geändert werden
Windows Phone-Geräte gestatten keine Verringerung der Sicherheitsstufe in Sicherheitsrichtlinien, die mittels MDM oder EAS festgelegt wurden, nachdem diese festgelegt wurden. Angenommen, Sie legen ein **Kennwort mit Mindestanzahl von Zeichen** auf 8 fest und versuchen dann, diesen Wert auf 4 zu verringern. Die restriktivere Richtlinie wurde bereits auf das Gerät angewendet.

Abhängig von der Geräteplattform müssen Sie, wenn Sie die Richtlinie auf einen niedrigeren Sicherheitswert ändern möchten, Sicherheitsrichtlinien möglicherweise zurücksetzen.
In Windows wischen Sie beispielsweise auf dem Desktop von rechts nach innen, um die Leiste **Charms** zu öffnen, und wählen Sie **Einstellungen** &gt; **Systemsteuerung**.  Wählen Sie das Applet **Benutzerkonten** aus.
Im linken Navigationsmenü befindet sich unten ein Link **Sicherheitsrichtlinien zurücksetzen** . Klicken Sie darauf, und klicken Sie dann auf die Schaltfläche **Richtlinien zurücksetzen**.
Andere MDM-Geräte, wie Android, Windows Phone 8.1 und höher sowie iOS, müssen möglicherweise außer Kraft gesetzt und bei dem Dienst neu registriert werden, damit Sie eine weniger restriktive Richtlinie anwenden können.

## <a name="issues-with-pcs-that-run-the-intune-software-client"></a>Probleme mit PCs mit dem Intune-Softwareclient

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Fehler in „policyplatform.log“ im Zusammenhang mit der Microsoft Intune-Richtlinie
Bei Windows-PCs, die mit dem Intune-Softwareclient verwaltet werden, können Richtlinienfehler in der Datei „policyplatform.log“ das Ergebnis nicht standardmäßiger Einstellungen in der Windows-Benutzerkontensteuerung (UAC) auf dem Gerät sein. Einige nicht standardmäßige UAC-Einstellungen können Microsoft Intune-Clientinstallationen und Richtlinienausführungen beeinträchtigen.

#### <a name="to-resolve-uac-issues"></a>So beheben Sie UAC-Probleme

1.  Koppeln Sie den Computer ab, wie unter [Retire devices from Microsoft Intune management](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management) (Abkoppeln von Geräten in der Microsoft Intune-Verwaltung) beschrieben.

2.  Warten Sie 20 Minuten, bis die Clientsoftware entfernt wurde.

    > [!NOTE]
    > Versuchen Sie nicht, den Client über „Programme und Funktionen“ zu entfernen.

3.  Geben Sie im Startmenü **UAC** ein, um die Einstellungen der Benutzerkontensteuerung zu öffnen.

4.  Verschieben Sie den Schieberegler für Benachrichtigungen auf die Standardeinstellung.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>FEHLER: Der Wert kann nicht vom Computer abgerufen werden, 0x80041013
Dieser Fehler kann auftreten, wenn die Zeit auf dem lokalen System um mindestens fünf Minuten abweicht. Wenn die Zeit auf dem lokalen Computer nicht synchron ist, schlagen sichere Transaktionen fehl, da der Zeitstempel ungültig ist.

Um dieses Problem zu beheben, legen Sie die lokale Systemzeit so genau wie möglich auf die Internetzeit oder die auf den Domänencontrollern im Netzwerk eingestellte Zeit fest.








### <a name="next-steps"></a>Nächste Schritte
Wenn diese Informationen zur Problembehandlung für Sie nicht hilfreich waren, wenden Sie sich wie in [Anfordern von Support für Microsoft Intune](how-to-get-support-for-microsoft-intune.md) beschrieben an den Microsoft Support.
