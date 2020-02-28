---
title: Behandeln von Problemen mit Geräteaktionen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: In diesem Artikel erhalten Sie Informationen zum Troubleshooting von Problemen bei Geräteaktionen.
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 545f287e8b7ee82e2008f239171b22e01714b8c7
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514743"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Troubleshooting für Geräteaktionen in Intune

In Microsoft Intune stehen Ihnen viele Aktionen zur Verfügung, die Sie beim Troubleshooting verwalteter Geräte unterstützen. In diesem Artikel erhalten Sie Antworten auf häufig gestellte Fragen, die Sie beim Troubleshooting von Problemen bei Geräteaktionen unterstützen.

## <a name="disable-activation-lock-action"></a>Aktion „Aktivierungssperre deaktivieren“

### <a name="i-clicked-the-disable-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>Ich habe im Portal auf die Aktion „Aktivierungssperre deaktivieren“ geklickt, aber auf dem Gerät ist nichts passiert.
Dieses Verhalten ist normal. Nach dem Start der Aktion „Aktivierungssperre deaktivieren“ wird in Intune ein aktualisierter Code von Apple angefordert. Sobald auf Ihrem Gerät der Bildschirm für die Aktivierungssperre angezeigt wird, geben Sie den Code manuell in das Passcodefeld ein. Dieser Code ist nur 15 Tage lang gültig. Klicken Sie also auf die Aktion, und kopieren Sie den Code, bevor Sie eine Zurücksetzen-Aktion starten.

### <a name="why-dont-i-see-the-disable-activation-lock-code-in-the-hardware-overview-blade-of-my-iosipados-device"></a>Warum wird der Code für die Aktion „Aktivierungssperre deaktivieren“ auf dem Hardwareübersichtsblatt meines iOS-/iPadOS-Geräts nicht angezeigt?
Die wahrscheinlichsten Ursachen sind die folgenden:
- Der Code ist abgelaufen und wurde aus dem Dienst gelöscht.
- Das Gerät wird nicht mit der Geräteeinschränkungsrichtlinie überwacht, die die Aktivierungssperre erlauben würde.

Führen Sie die folgende Abfrage aus, um den Code mithilfe des Graph-Testers zu überprüfen:

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-disable-activation-lock-action-greyed-out-for-my-iosipados-device"></a>Warum wird die Aktion „Aktivierungssperre deaktivieren“ für mein iOS-/iPadOS-Gerät abgeblendet angezeigt?
Die wahrscheinlichsten Ursachen sind die folgenden: 
- Der Code ist abgelaufen und wurde aus dem Dienst gelöscht.
- Das Gerät wird nicht mit der Geräteeinschränkungsrichtlinie überwacht, die die Aktivierungssperre erlauben würde.

### <a name="is-the-disable-activation-lock-code-case-sensitive"></a>Spielt Groß-/Kleinschreibung für den Code für die Aktion „Aktivierungssperre deaktivieren“ eine Rolle?
Nein. Außerdem müssen die Bindestriche nicht eingeben werden.

## <a name="remove-devices-action"></a>Aktion „Geräte entfernen“

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>Wie finde ich heraus, wer eine Abkoppeln/Zurücksetzen-Aktion gestartet hat?
Navigieren Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) zu **Mandantenverwaltung** > **Überwachungsprotokolle** und sehen Sie sich die Spalte **Initiiert von** an.
Wenn kein Eintrag angezeigt wird, wurde die Aktion höchstwahrscheinlich vom Gerätebenutzer selbst initiiert. Dazu wurde vermutlich die Unternehmensportal-App oder portal.manage.microsoft.com verwendet.

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>Warum wurde meine Anwendung nach Verwenden der Aktion „Abkoppeln“ nicht deinstalliert?
Die Anwendung wurde nicht als verwaltete Anwendung erkannt. In diesem Kontext ist eine verwaltete Anwendung eine Anwendung, die mithilfe des Intune-Diensts installiert wurde. Dies umfasst u. a.:
- Die App wurde als „Erforderlich“ bereitgestellt.
- Die App wurde als „Verfügbar“ bereitgestellt und dann vom Endbenutzer über die Unternehmensportal-App installiert.

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>Warum wird die Aktion „Zurücksetzen“ für Geräte mit Android Enterprise-Arbeitsprofil ausgegraut angezeigt?
Dieses Verhalten ist normal. Google erlaubt das Zurücksetzen auf Werkszustand für Geräte mit Android-Arbeitsprofil des MDM-Anbieters nicht.

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>Warum kann ich mich wieder bei meinen Office-Apps anmelden, obwohl mein Gerät abgekoppelt wurde?
Das liegt daran, dass Zugriffstoken durch das Abkoppeln eines Geräts nicht widerrufen werden. Sie können Richtlinien für den bedingten Zugriff verwenden, um diese Bedingung zu deaktivieren.

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>Wie kann ich eine Abkoppeln/Zurücksetzen-Aktion nach ihrem Start überwachen?
Navigieren Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) zu **Mandantenverwaltung** > **Überwachungsprotokolle**.

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>Warum wird für Zurücksetzen-Aktionen manchmal auf unbestimmte Zeit „Ausstehend“ angezeigt?
Geräte melden ihren Status für den Intune-Dienst nicht immer, bevor die Zurücksetzen-Aktion gestartet wurde. Daher wird die Aktion als „Ausstehend“ angezeigt. Sobald Sie überprüfen konnten, dass die Aktion erfolgreich war, können Sie das Gerät aus dem Dienst löschen.

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>Was geschieht, wenn ich eine Abkoppeln/Zurücksetzen-Aktion auf einem Gerät starte, das offline ist oder das schon seit längerer Zeit nicht mehr mit dem Dienst kommuniziert hat?
Das Gerät behält den Status **Abkoppeln und Zurücksetzen ausstehend**, bis das MDM-Zertifikat abläuft. Das MDM-Zertifikat gilt ab dem Zeitpunkt der Registrierung für ein Jahr und wird jedes Jahr automatisch verlängert. Wenn das Gerät eincheckt, bevor das MDM-Zertifikat abläuft, wird es abgekoppelt/zurückgesetzt. Wenn das Gerät nicht eingecheckt wird, bevor das MDM-Zertifikat abläuft, kann es nicht mehr in den Dienst einchecken. Geräte werden 180 Tage nach Ablauf des MDM-Zertifikats automatisch aus dem Azure-Portal entfernt.


## <a name="reset-passcode-action"></a>Aktion „Passcode zurücksetzen“

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>Warum wird die Aktion „Passcode zurücksetzen“ auf meinem von einem Android-Geräteadministrator registrierten Gerät ausgegraut angezeigt?
Google hat das Feature „Passcode zurücksetzen“ der Device Admin-API entfernt, um Ransomware zu bekämpfen (gilt für Geräte mit der Android-Version 7.0 und höher).

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>Warum erhalte ich die Nachricht „Nicht unterstützt“, wenn ich die Aktion „Passcode zurücksetzen“ für mein für ein Arbeitsprofil registriertes Gerät mit Android 8.0 oder höher starte?
Das liegt daran, dass das Token zum Zurücksetzen auf dem Gerät nicht aktiviert wurde. So aktivieren Sie das Token zum Zurücksetzen:
1. Sie müssen in Ihrer Konfigurationsrichtlinie einen Arbeitsprofilpasscode erzwingen.
2. Der Endbenutzer muss einen entsprechenden Arbeitsprofilpasscode festlegen.
3. Der Endbenutzer muss die zweite Aufforderung akzeptieren, damit die Aktion „Passcode zurücksetzen“ ausgeführt werden kann.
Nachdem diese Schritte ausgeführt wurden, sollte diese Meldung für Sie nicht mehr angezeigt werden.

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-iosipados-device-when-i-issue-the-remove-passcode-action"></a>Warum werde ich aufgefordert, auf meinem iOS-/iPadOS-Gerät einen neuen Passcode festzulegen, wenn ich die Aktion „Passcode entfernen“ starte?
Dies liegt daran, dass für eine Ihrer Kompatibilitätsrichtlinien ein Passcode erforderlich ist.


## <a name="wipe-action"></a>Aktion „Zurücksetzen“

### <a name="i-cant-restart-a-windows-10-device-after-using-the-wipe-action"></a>Nach Verwendung der Aktion „Zurücksetzen“ kann ich ein Windows 10-Gerät nicht neu starten.
Dies kann der Fall sein, wenn Sie die Option **Hiermit wird das Gerät zurückgesetzt. Dieser Vorgang wird auch dann fortgesetzt, wenn die Stromversorgung unterbrochen wird. Durch Auswahl dieser Option wird möglicherweise das erneute Starten einiger Windows 10-Geräte verhindert.** auf einem Windows 10-Gerät auswählen.

Dies kann der Fall sein, wenn bei der Installation von Windows eine größere Beschädigung vorliegt, die eine Neuinstallation des Betriebssystems verhindert. In diesem Fall schlägt der Prozess fehl, und das System befindet sich in der [Windows-Wiederherstellungsumgebung]( https://docs.microsoft.com/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference).

### <a name="i-cant-restart-a-bitlocker-encrypted-device-after-using-the-wipe-action"></a>Nach Verwendung der Aktion „Zurücksetzen“ kann ich ein mit BitLocker verschlüsseltes Gerät nicht neu starten.
Dies kann der Fall sein, wenn Sie die Option **Hiermit wird das Gerät zurückgesetzt. Dieser Vorgang wird auch dann fortgesetzt, wenn die Stromversorgung unterbrochen wird. Durch Auswahl dieser Option wird möglicherweise das erneute Starten einiger Windows 10-Geräte verhindert.** auf einem mit BitLocker verschlüsselten Gerät auswählen.

Installieren Sie zur Behebung dieses Problems Windows 10 mithilfe von startbaren Medien erneut auf dem Gerät.


## <a name="next-steps"></a>Nächste Schritte

Fordern Sie [Hilfe beim Microsoft-Support](../fundamentals/get-support.md) an, oder nutzen Sie die [Communityforen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
