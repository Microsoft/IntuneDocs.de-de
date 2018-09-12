---
title: Geräteeinschränkungen für Android-Arbeitsprofile in Microsoft Intune – Azure | Microsoft-Dokumentation
description: 'Auf Geräten mit Android-Arbeitsprofilen können Sie auf dem Gerät einige Einstellungen einschränken, einschließlich Folgendem: Kopieren und Einfügen, Benachrichtigungen anzeigen, App-Berechtigungen, Datenfreigabe, Kennwortlänge, Anmeldefehler, Entsperren per Fingerabdruck, Wiederverwenden von Passwörtern und Aktivieren der Freigabe von Arbeitskontakten per Bluetooth.'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 51e52e26357143d214c4bcf7856dfdb75a68653c
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329768"
---
# <a name="work-device-restriction-settings-in-intune"></a>Einstellungen für Einschränkungen von Arbeitsgeräten in Intune

In diesem Artikel sind alle Einstellungen für Microsoft Intune-Geräteeinschränkungen aufgelistet, die Sie für Android-Arbeitsprofilgeräte konfigurieren können.

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="work-profile-settings"></a>Arbeitsprofileinstellungen

### <a name="general-settings"></a>Allgemeine Einstellungen

- **Kopieren und Einfügen zwischen Arbeitsprofilen und persönlichen Profilen**: Steuert das Kopieren und Einfügen zwischen Arbeits-Apps und persönlichen Apps. Klicken Sie auf **Blockieren**, um eine Blockierung zu aktivieren. Wählen Sie **Nicht konfiguriert** aus, um eine Blockierung zu deaktivieren.
- **Datenfreigabe zwischen Arbeitsprofilen und persönlichen Profilen**: Steuert, ob Apps im Arbeitsprofil Daten für Apps im persönlichen Profil freigeben können. Durch diese Einstellung werden Freigabeaktionen in Anwendungen (z.B. die Option **Freigeben...** in der Browser-App Chrome) gesteuert. Sie wird nicht auf das Verhalten beim Kopieren von Daten in die Zwischenablage und Einfügen angewendet. Im Gegensatz zu [Richtlinieneinstellungen für den App-Schutz](https://docs.microsoft.com/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) werden Einstellungen für Geräteeinschränkungen über das Intune-Portal verwaltet und mithilfe der Android-Arbeitsprofilpartition zum Isolieren von verwalteten Apps eingesetzt. Es stehen die folgenden Optionen zur Auswahl:
  - **Standardeinschränkungen für Freigabe**: Dies ist das standardmäßige Freigabeverhalten des Geräts, das abhängig von der Android-Version variiert. Standardmäßig ist die Freigabe von Daten des persönlichen Profils für das Arbeitsprofil zulässig. Die Freigabe von Daten des Arbeitsprofils für das persönliche Profil ist dagegen standardmäßig blockiert. Durch diese Einstellung wird die Freigabe von Daten des Arbeitsprofils für das persönliche Profil verhindert. Google bietet auf Geräten, auf denen die Version 6.0 und höher ausgeführt wird, keine Möglichkeit, um die Freigabe von Daten aus dem persönlichen Profil für das Arbeitsprofil zu blockieren.
  - **Apps im Arbeitsprofil können Freigabeanforderungen vom persönlichen Profil verarbeiten**: Aktiviert das integrierte Android-Feature, dass die Freigabe vom persönlichen Profil zum Arbeitsprofil ermöglicht. Wenn diese Option aktiviert ist, können Daten durch eine Freigabeanfrage einer App im persönlichen Profil für Apps im Arbeitsprofil freigegeben werden. Diese Einstellung ist das Standardverhalten für Android-Geräte, die frühere Versionen als 6.0 ausführen.
  - **Grenzübergreifende Freigabe zulassen**: Ermöglicht die Freigabe von Daten in beide Richtungen über die Begrenzungen des Arbeitsprofils hinaus. Wenn Sie diese Einstellung auswählen, können Apps im Arbeitsprofil Daten für Apps ohne Badgeverwendung im persönlichen Profil freigeben. Verwenden Sie diese Einstellung mit Vorsicht, da sie verwalteten Apps im Arbeitsprofil die Freigabe von Daten für Apps auf der nicht verwalteten Seite des Geräts ermöglicht.

- **Arbeitsprofilbenachrichtigungen bei Gerätesperre**: Steuert, ob Apps im Arbeitsprofil Daten in Benachrichtigungen anzeigen können, wenn das Gerät gesperrt ist.
- **Standardmäßige App-Berechtigungen**: Legt die Standardberechtigungsrichtlinie für alle Apps im Arbeitsprofil fest. Ab Android 6 wird der Benutzer aufgefordert, bestimmte von den Apps benötigte Berechtigungen zu erteilen, wenn die App gestartet wird. Bei dieser Richtlinieneinstellung können Sie festlegen, ob Benutzer aufgefordert werden sollen, Berechtigungen für alle Apps im Arbeitsprofil zu gewähren. Beispielsweise können Sie dem Arbeitsprofil eine App zuweisen, die Standortzugriff benötigt. In der Regel fordert diese App den Benutzer dazu auf, den Standortzugriff durch die App zu genehmigen oder abzulehnen. Mit dieser Richtlinie können Sie entscheiden, ob alle Berechtigungen automatisch ohne Aufforderung gewährt werden sollen, ohne Aufforderung automatisch verweigert werden sollen oder ob der Endbenutzer entscheiden kann. Es stehen die folgenden Optionen zur Auswahl:
  - **Gerätestandard**
  - **Eingabeaufforderung**
  - **Automatisch gewähren**
  - **Automatisch verweigern**

    Der Status zur Erteilung der Berechtigungen kann für bestimmte Apps weitergehend definiert werden, indem eine App-Konfigurationsrichtlinie für eine einzelne App (unter **Client-Apps** > **App-Konfigurationsrichtlinien**) verwendet wird.

- **Konten hinzufügen und entfernen**

   Verhindert, dass Benutzer Konten im Arbeitsprofil manuell hinzufügen oder entfernen.

   Wenn Sie beispielsweise die Gmail-App in einem Android-Arbeitsprofil bereitstellen, können Sie verhindern, dass Benutzer Konten in diesem Arbeitsprofil hinzufügen oder entfernen.

- **Kontaktfreigabe über Bluetooth:** Ermöglicht den Zugriff auf Arbeitskontakte von einem anderen Gerät aus, z.B. aus dem Auto, wenn es mit Bluetooth gekoppelt ist. Diese Einstellung ist standardmäßig nicht konfiguriert, und Kontakte aus dem Arbeitsprofil werden nicht angezeigt. Klicken Sie auf **Aktivieren**, um diese Freigabe zuzulassen und um Kontakte aus dem Arbeitsprofil anzuzeigen. Diese Einstellung ist auf Geräten unter Android OS 6.0 und höher verfügbar, auf denen Arbeitsprofile eingerichtet wurden. Wenn Sie dies aktivieren, können bestimmte Bluetooth-Geräte bei der ersten Verbindung Arbeitskontakte zwischenspeichern. Durch das Deaktivieren dieser Richtlinie nach einer ersten Kopplung bzw. Synchronisierung werden die Arbeitskontakte von einem Bluetooth-Gerät möglicherweise nicht entfernt.

- **Bildschirmaufnahme**: Blockiert die Bildschirmaufnahme auf dem Gerät im Arbeitsprofil. Zudem wird verhindert, dass der Inhalt auf Anzeigegeräten angezeigt wird, die über keine sichere Videoausgabe verfügen.

- **Anrufer-ID des Arbeitskontakts im persönlichen Profil anzeigen**: Wenn aktiviert (nicht konfiguriert), werden die Anruferdetails des Arbeitskontakts im persönlichen Profil angezeigt. Wenn blockiert, wird die Anrufernummer des Arbeitskontakts im persönlichen Profil nicht angezeigt. Gilt für Android OS v6.0 und neuere Versionen.

- **Kamera**: Blockiert die Kamera auf dem Gerät im Arbeitsprofil. Die Kamera im persönlichen Profil ist von dieser Einstellung nicht betroffen.

### <a name="work-profile-password"></a>Arbeitsprofilkennwort

- **Arbeitsprofilkennwort erforderlich**: Gilt für Android 7.0 und höher mit aktiviertem Arbeitsprofil. Definieren Sie eine Kennungsrichtlinie, die nur für Apps im Arbeitsprofil gilt. Standardmäßig kann der Endbenutzer die beiden separat definierten PINs verwenden oder diese zu einer PIN kombinieren, die die Stärke der jeweils stärkeren PIN übernimmt.
- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl (von **4**-**16**) an Zeichen an, die das Benutzerkennwort enthalten muss.
- **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Sperrung des Arbeitsprofils**: Wählen Sie die Zeitspanne aus, nach der das Arbeitsprofil gesperrt wird. Der Benutzer muss dann seine Anmeldeinformationen eingeben, um wieder Zugriff zu erhalten.
- **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird**: Geben Sie an, wie häufig ein falsches Kennwort eingegeben werden kann, bevor das Arbeitsprofil auf dem Gerät zurückgesetzt wird.
- **Kennwortablauf (Tage)**: Geben Sie die Anzahl der Tage an (von **1**-**255**), nach deren Verstreichen das Kennwort eines Endbenutzers geändert werden muss.
- **Erforderlicher Kennworttyp**: Wählen Sie den Typ des Kennworts, das auf dem Gerät festgelegt werden muss. Es stehen die folgenden Optionen zur Auswahl:
  - **Gerätestandard**
  - **Biometrie auf niedriger Sicherheitsstufe**
  - **Erforderlich**
  - **Mindestens numerisch**
  - **Numerisch komplex**: Sich wiederholende oder fortlaufende Ziffern wie „1111“ oder „1234“ sind nicht zulässig.
  - **Mindestens alphabetisch**
  - **Mindestens alphanumerisch**
  - **Mindestens alphanumerisch mit Symbolen**
- **Wiederverwendung vorheriger Kennwörter verhindern**: Geben Sie die Anzahl neuer Kennwörter ein (von **1**-**24**), die verwendet werden müssen, bevor ein altes Kennwort wiederverwendet werden kann.
- **Entsperrung durch Fingerabdruck**: Verhindert, dass ein Endbenutzer das Gerät mithilfe des Fingerabdruckscanners entsperren kann.
- **Smart Lock und andere Vertrauens-Agents**: Steuert das Smart Lock-Features auf kompatiblen Geräten. Diese Telefonfunktion wird manchmal als Vertrauens-Agent bezeichnet und ermöglicht Ihnen, das Kennwort für das Arbeitsprofil zu deaktivieren oder zu umgehen, wenn sich das Gerät an einem vertrauenswürdigen Standort befindet. Wenn das Gerät beispielsweise mit einem bestimmten Bluetooth-Gerät verbunden ist oder sich in der Nähe eines NFC-Tags befindet. Mit dieser Einstellung können Sie verhindern, dass Benutzer Smart Lock konfigurieren.

## <a name="device-password"></a>Gerätekennwort

- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl (von **4**-**14**) an Ziffern oder Zeichen an, die das Benutzerkennwort enthalten muss.
- **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung**: Wählen Sie den Zeitraum, nach dessen Verstreichen ein inaktives Gerät automatisch gesperrt wird.
- **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird**: Geben Sie an, wie häufig ein falsches Kennwort eingegeben werden kann, bevor alle Daten auf dem Gerät gelöscht werden.
- **Kennwortablauf (Tage)**: Geben Sie die Anzahl der Tage an (von **1**-**255**), nach deren Verstreichen das Kennwort eines Endbenutzers geändert werden muss.
- **Erforderlicher Kennworttyp**: Wählen Sie den Typ des Kennworts, das auf dem Gerät festgelegt werden muss. Es stehen die folgenden Optionen zur Auswahl:
  - **Gerätestandard**
  - **Biometrie auf niedriger Sicherheitsstufe**
  - **Erforderlich**
  - **Mindestens numerisch**
  - **Numerisch komplex**: Sich wiederholende oder fortlaufende Ziffern wie „1111“ oder „1234“ sind nicht zulässig.
  - **Mindestens alphabetisch**
  - **Mindestens alphanumerisch**
  - **Mindestens alphanumerisch mit Symbolen**
- **Wiederverwendung vorheriger Kennwörter verhindern**: Geben Sie die Anzahl neuer Kennwörter ein (von **1**-**24**), die verwendet werden müssen, bevor ein altes Kennwort wiederverwendet werden kann.
- **Entsperrung durch Fingerabdruck**: Verhindert, dass ein Endbenutzer das Gerät mithilfe des Fingerabdruckscanners entsperren kann.
- **Smart Lock und andere Vertrauens-Agents**: Steuert das Smart Lock-Features auf kompatiblen Geräten. Diese Telefonfunktion wird manchmal als Vertrauens-Agent bezeichnet und ermöglicht Ihnen, das Kennwort für den Gerätesperrbildschirm zu deaktivieren oder zu umgehen, wenn sich das Gerät an einem vertrauenswürdigen Standort befindet. Wenn das Gerät beispielsweise mit einem bestimmten Bluetooth-Gerät verbunden ist oder sich in der Nähe eines NFC-Tags befindet. Mit dieser Einstellung können Sie verhindern, dass Benutzer Smart Lock konfigurieren.

## <a name="system-security"></a>Systemsicherheit

- **Bedrohungsüberprüfung für Apps**: Erzwingen Sie, dass die Einstellung **Apps überprüfen** für geschäftliche und persönliche Profile aktiviert ist.

   > [!Note]
   > Diese Einstellung funktioniert nur auf Geräten mit Android O und höher.

## <a name="next-step"></a>Nächster Schritt

Informationen dazu, wie Sie Profile speichern und Benutzern sowie Geräten zuweisen, finden Sie unter [Konfigurieren der Einstellungen für Geräteeinschränkungen](device-restrictions-configure.md).
