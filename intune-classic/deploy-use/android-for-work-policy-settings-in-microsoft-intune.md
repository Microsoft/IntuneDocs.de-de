---
title: Android for Work-Richtlinieneinstellungen in Microsoft Intune
description: Erstellen Sie Richtlinien, die Einstellungen und Features auf Android for Work-Geräten steuern, die Sie mit Intune verwalten.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 02/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 35a53076-74d6-486d-b201-e0da2e170008
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 89c0e09a34a734ccfe704b9a89971544e9a25e86
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="android-for-work-policy-settings-in-microsoft-intune"></a>Einstellungen für Android for Work-Richtlinien in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune bietet eine Vielzahl von integrierten allgemeinen Einstellungen, die Sie auf [Android for Work-Geräten](android-for-work.md) konfigurieren können.

## <a name="general-configuration-policy"></a>Allgemeine Konfigurationsrichtlinie

Verwenden Sie die **Richtlinie für die allgemeine Konfiguration von Intune Android for Work** zum Konfigurieren von Sicherheits- und Arbeitsprofileinstellungen für Ihre Android for Work-Geräte.

Wenn die gesuchte Einstellung nicht in diesem Thema enthalten ist, können Sie sie ggf. mithilfe einer benutzerdefinierten Android-Richtlinie erstellen, die Ihnen das Steuern des Geräts mithilfe von OMA-URI-Einstellungen erlaubt. Weitere Informationen finden Sie weiter unten in diesem Thema unter [Benutzerdefinierte Richtlinieneinstellungen](#custom-policy-settings).

> [!TIP]
> Geräte werden beim Bereitstellen eines Arbeitsprofils automatisch verschlüsselt. Diese Einstellung kann nicht geändert werden.

### <a name="password-settings"></a>Kennworteinstellungen

|Name der Einstellung|Details|
|----------------|-|
|**Anfordern eines Kennworts zum Entsperren mobiler Geräte**|Gibt an, ob auf verwalteten Geräten ein Kennwort erforderlich ist. Es stehen die folgenden Optionen zur Auswahl:<br><br>- **Komplex**: erfordert mindestens einen Buchstaben, eine Zahl und ein Symbol<br>- **Alphanumerisch**: erfordert mindestens eine Zahl und ein alphabetisches Zeichen<br>- **Alphabetisch**: erfordert mindestens Buchstaben oder Symbole<br>- **Numerisch, komplex**: erfordert numerische Zeichen, die sich nicht wiederholen oder fortlaufend sind<br>- **Numerisch**<br><br>Wenn diese Einstellung nicht aktiviert ist, gelten keine Anforderungen an die Kennwortkomplexität.|
|**Minimale Kennwortlänge**|Gibt die Mindestanzahl von Zahlen oder Zeichen an, die das Kennwort enthalten muss.|
|**Inaktivität in Minuten, bevor das Gerät gesperrt wird**|Gibt die Anzahl der Minuten ohne Benutzeraktivität an, bevor das Gerät automatisch gesperrt wird.|
|**Smart Lock und andere Vertrauens-Agents zulassen**<br>(Android 6 und höher)|Ermöglicht Ihnen die Steuerung der Smart Lock-Funktion auf kompatiblen Android-Geräten. Diese Telefonfunktion wird manchmal als Vertrauens-Agent bezeichnet und ermöglicht Ihnen das Deaktivieren oder Umgehen des Kennworts für den Gerätesperrbildschirm, wenn sich das Gerät an einem vertrauenswürdigen Standort befindet, (wenn es z. B. mit einem bestimmten Bluetooth-Gerät verbunden ist oder sich in der Nähe eines NFC-Tags befindet). Mit dieser Einstellung können Sie verhindern, dass Benutzer Smart Lock konfigurieren.|
|**Anzahl wiederholter Anmeldefehler, bevor das Arbeitsprofil entfernt wird**|Gibt die Anzahl zulässiger Anmeldefehler an, bevor das Arbeitsprofil auf dem Gerät entfernt wird. Dabei wird keine vollständige Gerätezurücksetzung durchgeführt.|
|**Kennwortverlauf speichern**|Verhindert die Wiederverwendung zuvor verwendeter Kennwörter.|
|**Kennwortverlauf speichern** - **Wiederverwendung vorheriger Kennwörter verhindern**|Gibt die Anzahl der zuvor bereits verwendeten Kennwörter an, die gespeichert werden sollen.|
|**Kennwortablauf (Tage)**|Gibt die Anzahl der Tage an, bevor das Gerätekennwort geändert werden muss.|
|**Fingerabdruckentsperrung zulassen**<br>(Android 6 und höher)|Ermöglicht Ihnen die Verwendung eines Fingerabdrucks zum Entsperren von Geräten mit dieser Funktion.|


### <a name="work-profile-settings"></a>Arbeitsprofileinstellungen

|Name der Einstellung|Details|
|----------------|-|
|**Datenaustausch zwischen Arbeitsprofilen und persönlichen Profilen zulassen**|Lässt zu, dass Apps im Arbeitsprofil Daten mit Apps im persönlichen Profil des Benutzers austauschen. Es stehen die folgenden Optionen zur Auswahl:<br><br>- **Freigabe über Grenzen hinweg verhindern**<br>- **Apps im Arbeitsprofil können Freigabeanforderungen vom persönlichen Profil verarbeiten**<br>- **Keine Einschränkungen bei Freigabe**|
|**Benachrichtigungen des Arbeitsprofils ausblenden, wenn das Gerät gesperrt ist**<br>(Android 6 und höher)|Legt fest, ob Benachrichtigungen aus dem Arbeitsprofil angezeigt werden, wenn das Gerät gesperrt ist.|
|**Standardberechtigungsrichtlinie für Apps festlegen**<br>(Android 6 und höher)|Legt die Standardberechtigungsrichtlinie für alle Apps im Arbeitsprofil fest. Ab Android 6 wird der Endbenutzer während der Laufzeit zur Eingabe bestimmter Berechtigungen aufgefordert, die für Apps erforderlich sind.  Diese Richtlinieneinstellung ermöglicht der IT-Abteilung, zu entscheiden, wie oder ob Benutzer aufgefordert werden, Berechtigungen für Apps im Arbeitsprofil zu gewähren. <br/><br/>Beispielsweise kann die IT-Abteilung eine App mithilfe von Push in das Arbeitsprofil übertragen, die Speicherortzugriff benötigt.  Normalerweise würde diese App den Benutzer in einem Popupdialogfeld fragen, ob er der App Speicherortzugriff gewähren möchte, und der Benutzer könnte dies genehmigen oder ablehnen.  Mit dieser Richtlinie kann die IT-Abteilung entscheiden, ob alle Berechtigungen automatisch ohne Aufforderung gewährt werden sollen, ohne Aufforderung automatisch verweigert werden sollen, oder ob der Endbenutzer entscheiden kann.|


## <a name="custom-policy-settings"></a>Benutzerdefinierte Richtlinieneinstellungen
Stellen Sie mithilfe der **benutzerdefinierten Android for Work-Konfigurationsrichtlinie** von Microsoft Intune die Einstellungen für OMA-URI bereit, um Features auf Android for Work-Geräten zu steuern. Dies sind die Standardeinstellungen, die viele Hersteller von mobilen Geräten verwenden, um Gerätefunktionen zu steuern.

Diese Funktion soll es Ihnen ermöglichen, Android-Einstellungen bereitzustellen, die nicht mit Intune-Richtlinien konfigurierbar sind.
Intune unterstützt zurzeit eine begrenzte Anzahl von benutzerdefinierten Android-Richtlinien. Mit den Beispielen in diesem Thema finden Sie heraus, welche Richtlinien Sie konfigurieren können.

### <a name="general-settings"></a>Allgemeine Einstellungen

|Name der Einstellung|Details|
    |----------------|--------------------|
    |**Name**|Geben Sie einen eindeutigen Namen für die benutzerdefinierte Android-Richtlinie ein, damit Sie sie leichter in der Intune-Konsole identifizieren können.|
    |**Beschreibung**|Geben Sie eine Beschreibung ein, die einen Überblick über die Richtlinie bietet, und andere relevante Informationen, die Ihnen die Suche danach erleichtern.|

### <a name="oma-uri-settings"></a>OMA-URI-Einstellungen

   |Name der Einstellung|Details|
    |--------|--------------------|
    |**Einstellungsname**|Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung ein, damit Sie sie in der Liste der Einstellungen leichter identifizieren können.|
    |**Einstellungsbeschreibung**|Geben Sie eine Beschreibung ein, die einen Überblick über die Einstellung bietet, und andere relevante Informationen, die Ihnen die Suche danach erleichtern.|
    |**Datentyp**|Wählen Sie den Datentyp aus, in dem Sie diese OMA-URI-Einstellung angeben. Wählen Sie aus **Zeichenfolge, Zeichenfolge (XML), Datum und Uhrzeit, ganze Zahl, Gleitkomma** oder **Boolesch** aus.|
    |**OMA-URI (Groß-/Kleinschreibung beachten)**|Geben Sie den OMA-URI an, für den Sie eine Einstellung festlegen möchten.|
    |**Wert**|Geben Sie den mit der zuvor festgelegten OMA-URI-Einstellung zu verknüpfenden Wert an.|

### <a name="examples"></a>Beispiele

- [Erstellen eines WLAN-Profils über einen vorinstallierten Schlüssel](pre-shared-key-wi-fi-profile.md)
- [Verwenden einer benutzerdefinierten Richtlinie zum Erstellen eines Profils für ein App-bezogenes VPN für Android-Geräte](per-app-vpn-for-android-pulse-secure.md)

### <a name="see-also"></a>Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
