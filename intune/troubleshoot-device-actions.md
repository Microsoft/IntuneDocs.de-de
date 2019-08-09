---
title: Behandeln von Problemen mit Geräteaktionen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hilfe bei der Behandlung von Problemen mit Geräte Aktionen
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 159e236a079adcd55ba73e8fea6f786c09d08bbd
ms.sourcegitcommit: 73fbecf7cee4fdfc37d3c30ea2007d2a9a6d2d12
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68772359"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Behandeln von Problemen mit Geräte Aktionen in InTune

Microsoft InTune umfasst viele Aktionen, die Sie bei der Verwaltung von Geräten unterstützen. Dieser Artikel enthält Antworten auf einige häufig gestellte Fragen, die Ihnen bei der Problembehandlung von Geräte Aktionen helfen können.

## <a name="bypass-activation-lock-action"></a>Aktion „Aktivierungssperre umgehen“

### <a name="i-clicked-the-bypass-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>Ich habe im Portal auf die Aktion "Umgehung Aktivierungssperre" geklickt, aber auf dem Gerät ist nichts passiert.
Dies ist zu erwarten. Nach dem Starten der Aktion "Aktivierungssperre umgehen" wird InTune von Apple ein aktualisierter Code angefordert. Sie geben den Code im Feld Kennung manuell ein, nachdem sich Ihr Gerät auf dem Aktivierungssperre-Bildschirm befindet. Dieser Code ist nur 15 Tage lang gültig. Achten Sie also darauf, dass Sie auf die Aktion klicken und den Code kopieren, bevor Sie das Löschen ausgeben.

### <a name="why-dont-i-see-the-bypass-activation-lock-code-in-the-hardware-overview-blade-of-my-ios-device"></a>Warum sehe ich den Code "Bypass Aktivierungssperre" auf dem Blatt "Hardware Übersicht" meines IOS-Geräts nicht?
Die wahrscheinlichsten Ursachen sind:
- Der Code ist abgelaufen und wurde aus dem Dienst gelöscht.
- Das Gerät wird nicht mit der Geräte Einschränkungs Richtlinie überwacht, um Aktivierungssperre zuzulassen.

Sie können den Code im Graph-Explorer mit der folgenden Abfrage überprüfen:

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-bypass-activation-lock-action-greyed-out-for-my-ios-device"></a>Warum ist die Umgehungs Aktivierungssperre Aktion für mein IOS-Gerät abgeblendet?
Die wahrscheinlichsten Ursachen sind: 
- Der Code ist abgelaufen und wurde aus dem Dienst gelöscht.
- Das Gerät wird nicht mit der Geräte Einschränkungs Richtlinie überwacht, um Aktivierungssperre zuzulassen.

### <a name="is-the-bypass-activation-lock-code-case-sensitive"></a>Ist der Umgehungs Aktivierungssperre Code Groß-/Kleinschreibung beachtet?
Nein. Und Sie müssen die Bindestriche nicht eingeben.

## <a name="remove-devices-action"></a>Aktion "Geräte entfernen"

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>Gewusst wie, von wem ein abkoppeln/zurücksetzen gestartet wurde?
Wechseln Sie zu **InTune** > **Geräte** > Geräte**Aktionen** > Überprüfen Sie die Spalte **initiiert von** .
Wenn kein Eintrag angezeigt wird, ist der Benutzer des Geräts die wahrscheinlichste Person, die die Aktion initiiert hat. Sie haben wahrscheinlich die Unternehmensportal APP oder Portal.Manage.Microsoft.com verwendet.

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>Warum wurde meine Anwendung nach dem abkoppeln nicht deinstalliert?
Da es nicht als verwaltete Anwendung betrachtet wurde. In diesem Kontext ist eine verwaltete Anwendung eine Anwendung, die mithilfe des InTune-Dienstanbieter installiert wurde. Dies umfasst u. a.:
- Die APP wurde bei Bedarf bereitgestellt.
- Die APP wurde als verfügbar bereitgestellt und vom Endbenutzer in der Unternehmensportal-App installiert.

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>Warum wird die zurück Löschung für Android-Unternehmens Arbeitsprofil-Geräte abgeblendet?
Dieses Verhalten ist normal. Google lässt das Zurücksetzen von Arbeitsprofil Geräten vom MDM-Anbieter nicht zu.

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>Warum kann ich mich wieder bei meinen Office-Apps anmelden, nachdem mein Gerät außer Betrieb genommen wurde?
Da das abkoppeln eines Geräts Zugriffs Token nicht widerrufen. Sie können Richtlinien für den bedingten Zugriff verwenden, um diese Bedingung zu mindern.

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>Wie kann ich nach der Ausgabe eine abkoppeln/zurücksetzen-Aktion überwachen?
Wechseln Sie zu Geräte**Aktionen**für **InTune** > -**Geräte** > .

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>Warum werden manchmal setzt als ausstehend angezeigt?
Geräte melden ihren Status nicht immer zurück an den InTune-Dienst, bevor die zurück Setzung gestartet wurde. Daher wird die Aktion als ausstehend angezeigt. Wenn Sie bestätigt haben, dass die Aktion erfolgreich war, löschen Sie das Gerät aus dem Dienst.

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>Was geschieht, wenn ich eine Außerbetriebnahme/zurück setzung auf einem Offline Gerät oder ein Gerät starte, das in einer Weile nicht mit dem Dienst kommuniziert hat?
Bis das MDM-Zertifikat abläuft, verbleibt das Gerät im Zustand "abkoppeln **/** zurücksetzen". Das MDM-Zertifikat dauert ein Jahr aus der Registrierung und wird jedes Jahr automatisch erneuert. Wenn das Gerät eincheckt, bevor das MDM-Zertifikat abläuft, wird es zurückgesetzt oder zurückgesetzt. Wenn das Gerät nicht eingecheckt wird, bevor das MDM-Zertifikat abläuft, kann es nicht mehr in den Dienst einchecken. 180 Tage nach Ablauf des MDM-Zertifikats wird das Gerät automatisch aus dem Azure-Portal entfernt.


## <a name="reset-passcode-action"></a>Passcode-Aktion Zurücksetzen

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>Warum ist die Aktion "Kennung zurücksetzen" auf meinem Android-Geräte Administrator registriert?
Um Ransom Ware zu bekämpfen, hat Google das Feature zum Zurücksetzen der Kennung auf der Geräte Administrator-API entfernt (gilt für Geräte der Version 7,0 oder höher).

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>Warum erhalte ich eine Meldung vom Typ "nicht unterstützt", wenn ich eine Kennung für das registrierte Android 8,0-oder spätere Arbeitsprofil auswähle?
Da das Token zum Zurücksetzen nicht auf dem Gerät aktiviert wurde. So aktivieren Sie das Token zum Zurücksetzen:
1. Sie müssen eine Arbeitsprofil Kennung in der Konfigurationsrichtlinie anfordern.
2. Der Endbenutzer muss eine entsprechende Arbeitsprofil Kennung festlegen.
3. Der Endbenutzer muss die sekundäre Eingabeaufforderung akzeptieren, um das Zurücksetzen der Kennung zuzulassen.
Nachdem diese Schritte ausgeführt wurden, sollten Sie diese Antwort nicht mehr erhalten.

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-ios-device-when-i-issue-the-remove-passcode-action"></a>Warum werde ich aufgefordert, bei der Ausgabe der Aktion "Kennung entfernen" eine neue Kennung auf meinem IOS-Gerät festzulegen?
Da eine ihrer Kompatibilitätsrichtlinien eine Kennung erfordert.

## <a name="next-steps"></a>Nächste Schritte

Fordern Sie [Hilfe beim Microsoft-Support](get-support.md) an, oder nutzen Sie die [Communityforen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
