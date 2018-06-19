---
title: Einstellungen für Exchange ActiveSync-Richtlinien
description: Verwenden Sie die Intune Exchange ActiveSync-Richtlinie, um Einstellungen zu konfigurieren, mit denen Sie Features und Funktionen auf Geräten steuern können, die von Exchange ActiveSync verwaltet werden.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 25bdc7da543cdc38ccbe70651c145750ba96c082
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31018905"
---
# <a name="exchange-activesync-policy-settings-in-microsoft-intune"></a>Einstellungen für Exchange ActiveSync-Richtlinien in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Verwenden Sie die Microsoft Intune **Exchange ActiveSync**-Richtlinie, um Einstellungen zu konfigurieren, mit denen Sie eine Reihe von Features und Funktionen auf Geräten steuern können, die von Exchange ActiveSync verwaltet werden.


## <a name="password-settings"></a>Kennworteinstellungen

|Name der Einstellung|Details
|----------------|---|
|**Anfordern eines Kennworts zum Entsperren mobiler Geräte**|Gibt an, ob Geräte mithilfe eines Kennworts gesperrt werden müssen.<br>(Dies trifft nicht auf Geräte zu, auf denen Windows RT ausgeführt wird.)|
|**Erforderlicher Kennworttyp**|Gibt den erforderlichen Typ des Kennworts an, z. B. nur numerisch oder alphanumerisch.|
|**Minimale Kennwortlänge**|Gibt die Mindestanzahl von Zeichen an, die das Gerätekennwort enthalten muss.|
|**Einfache Kennwörter zulassen**|Gibt an, ob Sie einfache Kennwörter verwenden können, z. B. '0000' und '1234'.|
|**Anzahl zulässiger wiederholter Anmeldefehler, bevor das Gerät zurückgesetzt wird**|Gibt an, nach wie vielen Eingabeversuchen eines falschen Kennworts das Gerät zurückgesetzt wird.|
|**Kennwortablauf (Tage)**|Gibt die Anzahl der Tage an, nach denen das Gerätekennwort geändert werden muss.
|**Kennwortverlauf speichern**|Gibt an, ob dem Benutzer zuvor bereits verwendete Kennwörter erlaubt werden sollen.|
|**Kennwortverlauf speichern** – **Wiederverwendung vorheriger Kennwörter verhindern**|Gibt die Anzahl der zuvor bereits verwendeten Kennwörter an, die nicht erneut verwendet werden können.|
|**Minuten Inaktivität vor Anforderung des Kennworts**|Gibt den Zeitraum an, über den sich das Gerät im Leerlauf befinden muss, bevor der Bildschirm gesperrt wird.

## <a name="encryption-settings"></a>Verschlüsselungseinstellungen

|                           Name der Einstellung                           |                                                                                                                                    Details                                                                                                                                    |
|------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>Verschlüsselung auf mobilen Geräten vorschreiben</strong><sup>1</sup> | Erfordert die Verschlüsselung der Daten auf einem Gerät, falls dies unterstützt wird.<br><br>Für Windows Phone 8-Geräte müssen Sie hier <strong>Ja</strong>festlegen.<br /><br />Aktivieren Sie zum Verwenden der Verschlüsselung auf iOS-Geräten die Einstellung <strong>Kennwort zum Entsperren mobiler Geräte erforderlich</strong>. |
|       <strong>Verschlüsselung auf Speicherkarten vorschreiben</strong>       |                                                                                  Erfordert die Verschlüsselung von Daten, die auf externen Speichern, wie etwa SD-Karten, gespeichert sind (auf unterstützten Geräten).                                                                                  |

<sup>1</sup> Zusätzliche Informationen für Geräte unter Windows 8.1

-   Um die Verschlüsselung auf Geräten zu erzwingen, auf denen Windows 8.1 ausgeführt wird, installieren Sie das [MDM-Clientupdate für Windows von Dezember 2014](https://support.microsoft.com/kb/3013816) auf jedem Gerät.

-   Wenn Sie diese Einstellung für Windows 8.1-Geräte aktivieren, müssen alle Benutzer des Geräts ein Microsoft-Konto haben.

-   Damit die Verschlüsselung für Windows 8.1-Geräte funktioniert, muss das Gerät die Hardwarezertifizierungsanforderungen für Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) erfüllen.

-   Wenn Sie die Verschlüsselung auf einem Windows 8.1-Gerät erzwingen, ist der Wiederherstellungsschlüssel nur über das Microsoft-Konto des Benutzers zugänglich. Der Zugriff erfolgt über das OneDrive-Konto des Benutzers. Sie können diesen Schlüssel nicht im Auftrag eines Benutzers wiederherstellen.

## <a name="email-settings"></a>E-Mail-Einstellungen

|Name der Einstellung|Details
|----------------|---|
|**Herunterladen von E-Mail-Anhängen für Benutzer zulassen**|Gibt an, ob E-Mail-Anlagen auf das Gerät heruntergeladen werden können.|
|**Synchronisierungszeitraum für E-Mail**|Gibt die Anzahl der Tage an, über die empfangene E-Mails mit dem Gerät synchronisiert werden.
|**Synchronisierung mit Exchange für mobile Geräte zulassen, von denen Exchange ActiveSync-Einstellungen nicht vollständig unterstützt werden**|Gibt an, ob Exchange der Zugriff auf Geräte erlaubt wird, die eine oder mehrere Exchange ActiveSync-Einstellungen nicht unterstützen.

## <a name="browser-settings"></a>Browsereinstellungen

|Name der Einstellung|Details
|----------------|---|
|**Webbrowser zulassen**|Gibt an, ob der Webbrowser des Geräts verwendet werden darf.<br>(Für Windows RT oder Windows Phone nicht verfügbar.)

## <a name="hardware-settings"></a>Hardware-Einstellungen

|Name der Einstellung|Details
|----------------|---|
|**Kamera zulassen**|Gibt an, ob die Kamera des Geräts verwendet werden darf.<br>(Für Windows RT oder Windows Phone nicht verfügbar.)



### <a name="see-also"></a>Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
