---
title: Geräteeinschränkungen für Android-Arbeitsprofile in Microsoft Intune – Azure | Microsoft-Dokumentation
description: 'Auf Geräten mit Android Enterprise-Profilen können Sie auf dem Gerät einige Einstellungen einschränken, einschließlich Folgendem: Kopieren und Einfügen, Benachrichtigungen anzeigen, App-Berechtigungen, Datenfreigabe, Kennwortlänge, Anmeldefehler, Entsperren per Fingerabdruck, Wiederverwenden von Passwörtern und Aktivieren der Freigabe von Arbeitskontakten per Bluetooth.'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: f0270818a03c68afd24e32d86a9c1f847e2f2ee2
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181988"
---
# <a name="work-device-restriction-settings-in-intune"></a>Einstellungen für Einschränkungen von Arbeitsgeräten in Intune

In diesem Artikel sind alle Einstellungen für Microsoft Intune-Geräteeinschränkungen aufgelistet, die Sie für Android Enterprise-Profilgeräte konfigurieren können.

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="work-profile-settings"></a>Arbeitsprofileinstellungen

### <a name="general-settings"></a>Allgemeine Einstellungen

- **Kopieren und Einfügen zwischen Arbeitsprofilen und persönlichen Profilen**: Steuert das Kopieren und Einfügen zwischen Arbeits-Apps und persönlichen Apps. Klicken Sie auf **Blockieren**, um eine Blockierung zu aktivieren. Wählen Sie **Nicht konfiguriert** aus, um eine Blockierung zu deaktivieren.
- **Datenfreigabe zwischen Arbeitsprofilen und persönlichen Profilen**: Steuert, ob Apps im Arbeitsprofil Daten für Apps im persönlichen Profil freigeben können. Durch diese Einstellung werden Freigabeaktionen in Anwendungen (z. B. die Option **Freigeben...** in der Chrome-Browser-App. Diese Einstellung gilt nicht für das Verhalten beim Kopieren/Einfügen der Zwischenablage. Im Gegensatz zu [Richtlinieneinstellungen für den App-Schutz](https://docs.microsoft.com/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) werden Einstellungen für Geräteeinschränkungen über das Intune-Portal verwaltet und mithilfe der Android-Arbeitsprofilpartition zum Isolieren von verwalteten Apps eingesetzt. Es stehen die folgenden Optionen zur Auswahl:
  - **Standardeinschränkungen für Freigabe**: Dies ist das standardmäßige Freigabeverhalten des Geräts, das abhängig von der Android-Version variiert. Standardmäßig ist die Freigabe von Daten des persönlichen Profils für das Arbeitsprofil zulässig. Die Freigabe von Daten des Arbeitsprofils für das persönliche Profil ist dagegen standardmäßig blockiert. Durch diese Einstellung wird die Freigabe von Daten des Arbeitsprofils für das persönliche Profil verhindert. Auf Geräten mit den Versionen 6.0 und höher blockiert Google die Freigabe vom persönlichen Profil zum Arbeitsprofil nicht.
  - **Apps im Arbeitsprofil können Freigabeanforderungen vom persönlichen Profil verarbeiten**: Aktiviert das integrierte Android-Feature, dass die Freigabe vom persönlichen Profil zum Arbeitsprofil ermöglicht. Wenn diese Option aktiviert ist, können Daten durch eine Freigabeanfrage einer App im persönlichen Profil für Apps im Arbeitsprofil freigegeben werden. Diese Einstellung ist das Standardverhalten für Android-Geräte, die frühere Versionen als 6.0 ausführen.
  - **Grenzübergreifende Freigabe zulassen**: Ermöglicht die Freigabe von Daten in beide Richtungen über die Begrenzungen des Arbeitsprofils hinaus. Wenn Sie diese Einstellung auswählen, können Apps im Arbeitsprofil Daten für Apps ohne Badgeverwendung im persönlichen Profil freigeben. Diese Einstellung gestattet es verwalteten Apps im Arbeitsprofil, die Daten für Apps auf der nicht verwalteten Seite des Geräts freizugeben. Verwenden Sie diese Einstellung also mit Bedacht.

- **Arbeitsprofilbenachrichtigungen bei Gerätesperre**: Steuert, ob Apps im Arbeitsprofil Daten in Benachrichtigungen anzeigen können, wenn das Gerät gesperrt ist.
- **Standardmäßige App-Berechtigungen**: Legt die Standardberechtigungsrichtlinie für alle Apps im Arbeitsprofil fest. Ab Android 6 wird der Benutzer aufgefordert, bestimmte von den Apps benötigte Berechtigungen zu erteilen, wenn die App gestartet wird. Bei dieser Richtlinieneinstellung können Sie festlegen, ob Benutzer aufgefordert werden sollen, Berechtigungen für alle Apps im Arbeitsprofil zu gewähren. Beispielsweise können Sie dem Arbeitsprofil eine App zuweisen, die Standortzugriff benötigt. In der Regel fordert diese App den Benutzer dazu auf, den Standortzugriff durch die App zu genehmigen oder abzulehnen. Verwenden Sie diese Richtlinie, um Berechtigungen automatisch ohne Aufforderung zu erteilen, Berechtigungen ohne Aufforderung automatisch zu verweigern oder den Endbenutzer entscheiden zu lassen. Es stehen die folgenden Optionen zur Auswahl:
  - **Gerätestandard**
  - **Eingabeaufforderung**
  - **Automatisch gewähren**
  - **Automatisch verweigern**

    Sie können auch eine App-Konfigurationsrichtlinie verwenden, um Berechtigungen für einzelne Anwendungen zu erteilen (**Clientanwendungen** > **App-Konfigurationsrichtlinien**).

- **Konten hinzufügen und entfernen**

   Verhindert, dass Benutzer Konten im Arbeitsprofil manuell hinzufügen oder entfernen.

   Wenn Sie beispielsweise die Gmail-App in einem Android-Arbeitsprofil bereitstellen, können Sie verhindern, dass Benutzer Konten in diesem Arbeitsprofil hinzufügen oder entfernen.

- **Kontaktfreigabe über Bluetooth:** Ermöglicht den Zugriff auf Arbeitskontakte von einem anderen Gerät aus, z.B. aus dem Auto, wenn es mit Bluetooth gekoppelt ist. Diese Einstellung ist standardmäßig nicht konfiguriert, und Kontakte aus dem Arbeitsprofil werden nicht angezeigt. Klicken Sie auf **Aktivieren**, um diese Freigabe zuzulassen und um Kontakte aus dem Arbeitsprofil anzuzeigen. Diese Einstellung ist auf Geräten unter Android OS 6.0 und höher verfügbar, auf denen Arbeitsprofile eingerichtet wurden. Wenn Sie diese Einstellung aktivieren, können bestimmte Bluetooth-Geräte bei der ersten Verbindung Arbeitskontakte zwischenspeichern. Durch das Deaktivieren dieser Richtlinie nach einer ersten Kopplung bzw. Synchronisierung werden die Arbeitskontakte von einem Bluetooth-Gerät möglicherweise nicht entfernt.

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
- **Smart Lock und andere Vertrauens-Agents**: Steuert das Smart Lock-Features auf kompatiblen Geräten. Dieses Telefonfeature wird auch als Vertrauens-Agent bezeichnet und ermöglicht Ihnen, das Kennwort für das Arbeitsprofil zu deaktivieren oder zu umgehen, wenn sich das Gerät an einem vertrauenswürdigen Standort befindet. Umgehen Sie z. B. das Kennwort für das Arbeitsprofil, wenn das Gerät mit einem bestimmten Bluetooth-Gerät verbunden ist oder sich in der Nähe eines NFC-Tags befindet. Mit dieser Einstellung können Sie verhindern, dass Benutzer Smart Lock konfigurieren.

## <a name="device-password"></a>Gerätekennwort

- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl (von **4**-**14**) an Zeichen an, die das Benutzerkennwort enthalten muss.
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
- **Smart Lock und andere Vertrauens-Agents**: Steuert das Smart Lock-Features auf kompatiblen Geräten. Dieses Telefonfeature wird auch als Vertrauens-Agent bezeichnet und ermöglicht Ihnen, das Kennwort für den Gerätesperrbildschirm zu deaktivieren oder zu umgehen, wenn sich das Gerät an einem vertrauenswürdigen Standort befindet. Umgehen Sie z. B. das Kennwort für das Arbeitsprofil, wenn das Gerät mit einem bestimmten Bluetooth-Gerät verbunden ist oder sich in der Nähe eines NFC-Tags befindet. Mit dieser Einstellung können Sie verhindern, dass Benutzer Smart Lock konfigurieren.

## <a name="system-security"></a>Systemsicherheit

- **Bedrohungsüberprüfung für Apps**: Erzwingen Sie, dass die Einstellung **Apps überprüfen** für geschäftliche und persönliche Profile aktiviert ist.

   > [!Note]
   > Diese Einstellung funktioniert nur auf Geräten mit Android O und höher.

## <a name="connectivity"></a>Verbindung

- **Always On-VPN**: Wählen Sie **Aktivieren** aus, um einen VPN-Client so festzulegen, dass er automatisch eine Verbindung mit dem VPN herstellt und erneut herstellt. Always On-VPN-Verbindungen bleiben erhalten oder werden sofort hergestellt, wenn der Benutzer sein Gerät sperrt, das Gerät neu gestartet wird oder das drahtlose Netzwerk sich ändert. 

  Wählen Sie **Nicht konfiguriert** aus, um das Always On-VPN für alle VPN-Clients zu deaktivieren. 

  > [!IMPORTANT]
  > Stellen Sie sicher, dass Sie nur eine Always On-VPN-Richtlinie auf einem einzelnen Gerät bereitstellen. Die Bereitstellung mehrerer Always VPN-Richtlinien auf einem einzelnen Gerät wird nicht unterstützt.

- **VPN-Client**: Wählen Sie einen VPN-Client aus, der Always On unterstützt. Folgende Optionen sind verfügbar:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Benutzerdefiniert
    - **Paket-ID**: Geben Sie die Paket-ID der App im Google Play Store ein. Wenn z. B. die URL für die App im Play Store `https://play.google.com/store/details?id=com.contosovpn.android.prod` lautet, dann ist die Paket-ID `com.contosovpn.android.prod`.

    > [!IMPORTANT]
    >  - Der von Ihnen ausgewählte VPN-Client muss auf dem Gerät installiert sein und VPN pro Anwendung in Arbeitsprofilen unterstützen. Andernfalls tritt ein Fehler auf. 
    >  - Sie müssen die VPN-Client-App im **verwalteten Google Play Store** genehmigen, die App mit Intune synchronisieren und die App auf dem Gerät bereitstellen. Danach wird die App im Arbeitsprofil des Benutzers installiert.
    >  - Es gibt bekannte Probleme bei der Verwendung von VPN pro App mit F5 Access for Android 3.0.3. Weitere Informationen finden Sie auf der F5-Website mit den [Anmerkungen zu dieser Version zu F5 Access for Android 3.0.3](https://support.f5.com/kb/en-us/products/big-ip_apm/releasenotes/related/relnote-f5access-android-3-0-3.html#relnotes_known_issues_f5_access_android).

- **Sperrmodus**: **Aktivieren**, um den gesamten Netzwerkdatenverkehr zu zwingen, den VPN-Tunnel zu verwenden. Wenn keine Verbindung zum VPN hergestellt wird, hat das Gerät keinen Netzwerkzugriff.

  Wählen Sie **Nicht konfiguriert** aus, damit der Datenverkehr durch den VPN-Tunnel oder durch das Mobilfunknetz fließen kann.

## <a name="next-step"></a>Nächster Schritt

[Zuweisen von Profilen](device-profile-assign.md) zu Benutzern und Geräten.
