---
title: Aktualisieren von Office 365 mithilfe von administrativen Vorlagen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie administrative Vorlagen in Microsoft Intune verwenden, um Office 365-Apps auf die neueste Version zu aktualisieren und auszuwählen, wie oft Office nach Updates sucht. Sie lernen auch die Geräteregistrierungsschlüssel kennen, die aktualisiert werden, wenn eine Intune-Richtlinie für das Office-Update angewendet wird.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cf872387d6e6f4f91af9f074f54695b081b79119
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74549108"
---
# <a name="use-update-channel-and-target-version-settings-to-update-office-365-with-microsoft-intune-administrative-templates"></a>Verwenden der Updatekanal- und Zielversionseinstellungen für das Aktualisieren von Office 365 mit den administrativen Vorlagen von Microsoft Intune

In Intune können Sie [Windows 10-Vorlagen zum Konfigurieren von Gruppenrichtlinieneinstellungen](administrative-templates-windows.md) verwenden. In diesem Artikel erfahren Sie, wie Sie Office 365 mithilfe einer administrativen Vorlage in Intune aktualisieren. Außerdem erhalten Sie Anleitungen dazu, wie Sie Ihre Richtlinien erfolgreich bestätigen können. Diese Informationen sind auch bei der Problembehandlung hilfreich.

In diesem Szenario erstellen Sie eine administrative Vorlage in Intune, mit der Office 365 auf Ihren Geräten aktualisiert wird.

Weitere Informationen zu administrativen Vorlagen finden Sie unter [Verwenden von Windows 10-Vorlagen zum Konfigurieren von Gruppenrichtlinieneinstellungen in Microsoft Intune](administrative-templates-windows.md).

Gilt für:

- Windows 10 und höher
- Office 365

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie sicher, dass Sie für Ihre Office-Apps [die automatischen Updates für Office 365 ProPlus](https://docs.microsoft.com/deployoffice/configure-update-settings-for-office-365-proplus) aktiviert haben. Hierfür können Sie die Gruppenrichtlinie oder die Office 2016-ADMX-Vorlage für Intune verwenden:

![Festlegen der Einstellung „Automatische Updates aktivieren“ in der administrativen Intune-Vorlage](./media/administrative-templates-update-office/admx-enable-automatic-updates.png)

## <a name="set-the-update-channel-in-the-intune-administrative-template"></a>Festlegen des Updatekanals in der administrativen Intune-Vorlage

1. Navigieren Sie in Ihrer [administrativen Intune-Vorlage](administrative-templates-windows.md#create-a-template) zur Einstellung **Updatekanal**, und geben Sie den gewünschten Kanal ein. Wählen Sie beispielsweise `Semi-Annual Channel` aus:

    ![Festlegen der Einstellung „Updatekanal“ für Office in der administrativen Intune-Vorlage](./media/administrative-templates-update-office/admx-enable-update-channel-setting.png)

    > [!NOTE]
    > Es wird empfohlen, häufiger zu aktualisieren. Der Kanalname „halbjährlich“ dient nur als Beispiel.

2. Stellen Sie sicher, dass Sie Ihren Windows 10-Geräten [die Richtlinie zuweisen](device-profile-assign.md). Sie können die Richtlinie auch synchronisieren, um Ihre Richtlinie früher überprüfen zu können:

    - [Synchronisieren der Richtlinie in Intune](../remote-actions/device-sync.md)
    - [Manuelles Synchronisieren der Richtlinie auf dem Gerät](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows#sync-from-settings-app)

## <a name="check-the-intune-registry-keys"></a>Überprüfen der Intune-Registrierungsschlüssel

Nachdem Sie die Richtlinien- und die Gerätesynchronisierungen zugewiesen haben, können Sie bestätigen, dass die Richtlinie angewendet wird:

1. Öffnen Sie auf dem Gerät die **Registrierungs-Editor-App**.
2. Navigieren Sie zum Intune-Richtlinienpfad: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`.

    > [!TIP]
    > Die `<Provider ID>` im Registrierungsschlüssel ändert sich. Öffnen Sie die **Registrierungs-Editor-App**, um die Anbieter-ID für Ihr Gerät zu finden, und navigieren Sie zu `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\AdmxInstalled`. Die Anbieter-ID wird angezeigt.

    Wenn die Richtlinie angewendet wird, werden die folgenden Registrierungsschlüssel angezeigt:

    - `L_UpdateBranch`
    - `L_UpdateTargetVersion`

    Im folgenden Beispiel sehen Sie, dass `L_UpdateBranch` einen ähnlichen Wert wie `<enabled /><data id="L_UpdateBranchID" value="Deferred" />` hat. Dieser Wert bedeutet, dass er auf „halbjährlicher Kanal“ festgelegt ist:

    ![Beispiel der administrativen Vorlage „L_Updatebranch“ für den Registrierungsschlüssel](./media/administrative-templates-update-office/admx-update-branch-registry-key.png)

    > [!TIP]
    > Im Artikel [Verwalten von Office 365 ProPlus mit dem Configuration Manager](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager) finden Sie die Werte und deren Bedeutung. Die Registrierungswerte basieren auf dem ausgewählten Verteilungskanal:
    >
    >- Monatlicher Kanal – Wert = "Current"
    >- Monatlicher Kanal (gezielt) – Wert = "Current"
    >- Halbjährlicher Kanal – Wert = "Current"
    >- Halbjährlicher Kanal (gezielt) – Wert = "FirstReleaseDeferred"
    >- Insider Fast – Wert = "InsiderFast"

An diesem Punkt wird die Intune-Richtlinie erfolgreich auf das Gerät angewendet.

## <a name="check-the-office-registry-keys"></a>Überprüfen der Office-Registrierungsschlüssel

1. Öffnen Sie auf dem Gerät die **Registrierungs-Editor-App**.
2. Navigieren Sie zum Office-Richtlinienpfad: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`.

    Sie sehen die folgenden Registrierungsschlüssel:

    - `UpdateChannel`: ist ein dynamischer Schlüssel, der sich abhängig von den konfigurierten Einstellungen ändert.
    - `CDNBaseUrl`: wird festgelegt, wenn Office 365 auf dem Gerät installiert ist.

3. Sehen Sie sich den Wert `UpdateChannel` an. Der Wert gibt an, wie häufig Office aktualisiert wird. Im Artikel [Verwalten von Office 365 ProPlus mit dem Configuration Manager](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager) finden Sie die Werte und deren Festlegung.

    Im folgenden Beispiel ist der Wert `UpdateChannel` auf `http://officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60` festgelegt, der **monatlich** ist:

    ![Beispiel der administrativen Office-Vorlage „UpdateChannel“ für den Registrierungsschlüssel](./media/administrative-templates-update-office/admx-update-channel-office-registry-key.png)

    Dieses Beispiel bedeutet, dass die Richtlinie noch nicht angewendet wird, da sie immer noch auf **monatlich** anstatt auf **halbjährlich** festgelegt ist.

Der Registrierungsschlüssel wird aktualisiert, wenn **Task Scheduler** > **Office Automatic Updates 2.0** (Aufgabenplanung > automatische Office-Updates 2.0) ausgeführt wird oder wenn sich ein Benutzer auf einem Gerät anmeldet. Öffnen Sie **Office Automatic Updates 2.0** task > **Triggers** (Automatische Office-Updates 2.0 > Aufgabe > Trigger), um diese zu bestätigen. Abhängig von Ihren Triggern kann es mindestens einen Tag oder mehrere Tage dauern, bevor der `UpdateChannel`-Registrierungsschlüssel aktualisiert ist.

## <a name="force-office-automatic-updates-to-run"></a>Erzwingen der Ausführung automatischer Office-Updates

Sie können die Richtlinieneinstellungen auf dem Gerät erzwingen, um die Richtlinie zu überprüfen. Durch die folgenden Schritte wird die Registrierung aktualisiert. Gehen Sie beim Aktualisieren der Registrierung wie immer vorsichtig vor.

1. Löschen Sie den Registrierungsschlüssel:

    1. Navigieren Sie zu `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Updates`.
    2. Doppelklicken Sie auf den `UpdateDetectionLastRunTime`-Schlüssel, löschen Sie den Datenwert, und klicken Sie auf **OK**.

2. Führen Sie die Aufgabe „Automatische Office-Updates“ aus:

    1. Öffnen Sie die App **Task Scheduler** (Aufgabenplanung) auf dem Gerät.
    2. Klappen Sie **Task Scheduler** > **Microsoft** > **Office** (Aufgabenplanungsbibliothek > Microsoft > Office) auf.
    3. Wählen Sie **Office Automatic Updates 2.0** > **Run** (Automatische Office-Updates 2.0 > Ausführen) aus:

        ![Öffnen der „Task Schedule“ (Aufgabenplanung) und Ausführen der automatischen Office-Updates](./media/administrative-templates-update-office/admx-task-scheduler-office-automatic-updates.png)

        Warten Sie, bis die Aufgabe abgeschlossen ist, was einige Minuten in Anspruch nehmen kann.

3. Navigieren Sie in der **Registrierungs-Editor-App** zu `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`. Überprüfen Sie den `UpdateChannel`-Wert.

    Der Wert sollte mit dem in der Richtlinie festgelegten Wert aktualisiert werden. In diesem Beispiel sollte der Wert auf `http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114` festgelegt werden.

An diesem Punkt wurde der Office-Updatekanal auf dem Gerät erfolgreich geändert. Sie können eine Office 365-App für einen Benutzer öffnen, der dieses Update empfängt, um den Status zu überprüfen.

## <a name="force-the-office-synchronization-to-update-account-information"></a>Erzwingen der Office-Synchronisierung zum Aktualisieren der Kontoinformationen  

Wenn Sie weitere Schritte durchführen möchten, können Sie das Update der neuesten Version durch Office erzwingen. Die folgenden Schritte sollten nur als Bestätigung durchgeführt werden, oder wenn Sie möchten, dass die Geräte das aktuellste Versionsupdate von diesem Kanal schnell erhalten. Andernfalls kann Office Updates automatisch ausführen.

### <a name="step-1-force-the-office-version-to-update"></a>Schritt 1: Erzwingen des Updates der Office-Version

1. Vergewissern Sie sich, dass die Office-Version den von Ihnen gewählten Updatekanal unterstützt. Im Artikel [Updateverlauf für Office 365 ProPlus (nach Datum)](https://docs.microsoft.com/officeupdates/update-history-office365-proplus-by-date) finden Sie die Buildnummern, die die unterschiedlichen Updatekanäle unterstützen.

2. Navigieren Sie in Ihrer [administrativen Intune-Vorlage](administrative-templates-windows.md#create-a-template) zur Einstellung **Zielversion**, und geben Sie die gewünschte Version ein.

    Ihre Einstellung **Zielversion** ähnelt der folgenden Einstellung:

    ![Festlegen der Einstellung „Zielversion“ in der administrativen Intune-Vorlage für Office](./media/administrative-templates-update-office/admx-enable-target-version-setting.png)

> [!IMPORTANT]
>
> - Vergewissern Sie sich, dass Sie die Richtlinie zugewiesen haben.
> - Wenn Sie eine vorhandene Richtlinie ändern, wirken sich die Änderungen auf alle zugewiesenen Benutzer aus.
> - Wenn Sie dieses Feature testen, empfiehlt es sich, eine Testrichtlinie zu erstellen und die Richtlinie einer Testgruppe von Benutzern zuzuweisen.

### <a name="step-2-check-the-office-version"></a>Schritt 2: Überprüfen der Office-Version

Befolgen Sie diese Schritte, um die Richtlinie zu überprüfen, bevor Sie die Richtlinie für alle Benutzer bereitstellen.

1. Navigieren Sie in der **Registrierungs-Editor-App** zu `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`.

2. Sehen Sie sich den Wert `L_UpdateTargetVersion` an. Nachdem die Richtlinie angewendet wurde, wird der Wert auf die von Ihnen eingegebene Version festgelegt, z. B. `<enabled /><data id="L_UpdateTargetVersionID" value="16.0.10730.20344" />`.

    An diesem Punkt wird die Intune-Richtlinie erfolgreich auf das Gerät angewendet.

3. Danach können Sie das Office-Update erzwingen. Öffnen Sie eine Office-App wie z. B. Excel. Wählen Sie „jetzt aktualisieren“ (möglicherweise im Menü **Konto**) aus.

    Das Update wird einige Minuten in Anspruch nehmen. Sie können bestätigen, dass Office versucht, die von Ihnen eingegebene Version zu erhalten:

      1. Navigieren Sie zu `C:\Program Files (x86)\Microsoft Office\Updates\Detection\Version` auf dem Gerät.
      2. Öffnen Sie die `VersionDescriptor.xml`-Datei, und navigieren Sie zum Abschnitt `<Version>`. Die verfügbare Version sollte die gleiche wie die in der Intune-Richtlinie eingegebene Version sein, wie z. B.:

          ![Überprüfen des Abschnitts „Version“ des Versionsdeskriptors der Office-XML-Datei](./media/administrative-templates-update-office/office-version-descriptor-xml-example.png)

4. Nachdem das Update installiert wurde, sollte die Office-App die neue Version anzeigen (z. B. im Menü **Konto**).

## <a name="next-steps"></a>Nächste Schritte

[Aktualisieren der Kanalwerte für Office 365-Clients](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager)

[Übersicht über den Office-Cloudrichtliniendienst für Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-office-cloud-policy-service)

[Verwenden von Windows 10-Vorlagen zum Konfigurieren von Gruppenrichtlinieneinstellungen (ADMX-Vorlagen) in Microsoft Intune](administrative-templates-windows.md)
