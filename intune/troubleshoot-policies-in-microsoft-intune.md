---
title: Behandlung von Problemen mit Richtlinien in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Verwendung der integrierten Features zur Problembehandlung und über häufige Probleme bzw. Fehler und die entsprechenden Behebungen, die auftreten können, wenn Sie Konformitätsrichtlinien und Konfigurationsprofile in Microsoft Intune verwenden.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/20/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9314617640d0bfd7f3a7b0cd0ba572e99ede53f9
ms.sourcegitcommit: cd451ac487c7ace18ac9722a28b9facfba41f6d3
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298398"
---
# <a name="troubleshoot-policies-and-profiles-and-in-intune"></a>Richtlinien und Profile zur Problembehandlung in Intune

In Microsoft Intune sind Features zur Problembehandlung integriert. Verwenden Sie diese Features, um Probleme mit Konformitätsrichtlinien und Konfigurationsprofilen in Ihrer Umgebung zu beheben.

In diesem Artikel werden häufig verwendete Methoden zur Problembehandlung aufgeführt, zudem werden einige der Probleme beschrieben, die auftreten können.

## <a name="check-tenant-status"></a>Überprüfen des Status eines Mandanten
Überprüfen Sie die [Mandantenstatus](tenant-status.md) und bestätigen Sie das Abonnement ist aktiv. Sie können auch anzeigen, Details zu aktiven Incidents und Empfehlungen, die die Bereitstellung von Richtlinien oder Profilen beeinträchtigen können.

## <a name="use-built-in-troubleshooting"></a>Verwenden der integrierten Problembehandlung

1. In [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)Option **Problembehandlung**:

    ![„Hilfe und Support“ in Intune, die Option „Problembehandlung“ ist ausgewählt](./media/help-and-support-troubleshoot.png)

2. Klicken Sie auf **Benutzer auswählen**, wählen Sie den Benutzer aus, bei dem ein Problem auftritt, und klicken Sie auf **Auswählen**.
3. Überprüfen Sie, ob sich grüne Häkchen neben **Intune-Lizenz** und **Kontostatus** befinden:

    ![Auswahl des Benutzers in Intune und Überprüfung auf grüne Häkchen neben „Intune-Lizenz“ und „Kontostatus“](./media/account-status-intune-license-show-green.png)

    **Nützliche Links:**

    - [Zuweisen von Lizenzen zu Benutzern, damit sie ihre Geräte bei Intune registrieren können](licenses-assign.md)
    - [Hinzufügen von Benutzern zu Intune](users-add.md)

4. Suchen Sie unter **Geräte** das Gerät, bei dem ein Problem auftritt. Überprüfen Sie folgende Spalten:

    - **Verwaltet**: Damit ein Gerät Konformitäts- oder Konfigurationsrichtlinien empfangen kann, muss diese Eigenschaft auf **MDM** oder **EAS/MDM** festgelegt sein.

      - Wenn **Verwaltet** nicht auf **MDM** oder **EAS/MDM** festgelegt ist, ist das Gerät nicht registriert. Es empfängt keine Konformitäts- oder Konfigurationsrichtlinien, bevor die Registrierung durchgeführt wurde.

      - Ein Gerät muss jedoch nicht registriert sein, um App-Schutzrichtlinien (Mobile Anwendungsverwaltung) zu empfangen. Weitere Informationen finden Sie unter [Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md).

    - **Azure AD Join Type** (Azure AD-Verknüpfungstyp): Diese Spalte sollte auf **Arbeitsbereich** oder **Azure AD** festgelegt sein.
 
      - Wenn die Spalte den Wert **Nicht registriert** aufweist, liegt möglicherweise ein Problem mit der Registrierung vor. Dieses Problem kann üblicherweise durch das Aufheben der Registrierung und das erneute Registrieren des Geräts behoben werden.

    - **Intune compliant** (Intune-konform): Diese Option sollte auf **Ja** festgelegt sein. Wenn **Nein** angezeigt wird, liegt möglicherweise ein Problem mit den Konformitätsrichtlinien vor oder das Gerät ist nicht mit dem Intune-Dienst verbunden. Das Gerät könnte beispielsweise ausgeschaltet oder nicht mit dem Netzwerk verbunden sein. In Folge dessen wird das Gerät als „Nicht konform“ eingestuft (z.B. nach 30 Tagen).

      Weitere Informationen finden Sie unter [Erste Schritte mit den Gerätekonformitätsrichtlinien in Intune](device-compliance-get-started.md).

    - **Azure AD compliant** (Azure AD-konform): Diese Option sollte auf **Ja** festgelegt sein. Wenn **Nein** angezeigt wird, liegt möglicherweise ein Problem mit den Konformitätsrichtlinien vor oder das Gerät ist nicht mit dem Intune-Dienst verbunden. Das Gerät könnte beispielsweise ausgeschaltet oder nicht mit dem Netzwerk verbunden sein. In Folge dessen wird das Gerät als „Nicht konform“ eingestuft (z.B. nach 30 Tagen).

      Weitere Informationen finden Sie unter [Erste Schritte mit den Gerätekonformitätsrichtlinien in Intune](device-compliance-get-started.md).

    - **Letzte Anmeldung:** Diese Spalte sollte ein aktuelles Datum und eine aktuelle Uhrzeit enthalten. Intune-Geräte melden sich standardmäßig alle 8 Stunden an.

      - Wenn der Wert von **Letzte Anmeldung** über 24 Stunden zurück liegt, liegt vermutlich ein Problem mit dem Gerät vor. Ein Gerät, das sich nicht anmelden kann, kann auch keine Richtlinien von Intune empfangen.

      - So erzwingen Sie die Anmeldung:
        - Öffnen Sie auf Android-Geräten die Unternehmensportal-App, und navigieren Sie zu **Geräte**. Wählen Sie anschließend ein Gerät aus der Liste aus, und tippen Sie auf **Geräteeinstellungen überprüfen**.
        - Öffnen Sie auf iOS-Geräten die Unternehmensportal-App, und navigieren Sie zu **Geräte**. Wählen Sie anschließend ein Gerät aus der Liste aus, und tippen Sie auf **Einstellungen überprüfen**. 
        - Navigieren Sie auf Windows-Geräten zu **Einstellungen** > **Konten** > **Auf Arbeits- oder Schulkonto zugreifen**. Wählen Sie anschließend das Konto oder die MDM-Registrierung aus, und tippen sie auf **Info** > **Sync**.

    - Wählen Sie das Gerät aus, um die Informationen zur Richtlinie anzuzeigen.

      Unter **Gerätekonformität** wird der Status der Konformitätsrichtlinien angezeigt, die dem Gerät zugewiesen sind.

      Unter **Gerätekonfiguration** wird der Zustand der Konfigurationsrichtlinien angezeigt, die dem Gerät zugewiesen sind.

      Wenn die erwarteten Richtlinien nicht unter **Gerätekonformität** oder **Gerätekonfiguration** angezeigt werden, wurden die Richtlinien nicht ordnungsgemäß zugewiesen. Öffnen Sie die Richtlinie, und weisen Sie diese dem entsprechenden Benutzer oder Gerät zu.

      **Richtlinienzustände:**

      - **Nicht zutreffend:** Diese Richtlinie wird auf dieser Plattform nicht unterstützt. Beispielsweise funktionieren iOS-Richtlinien nicht unter Android. Samsung KNOX-Richtlinien funktionieren nicht auf Windows-Geräten.
      - **Konflikt**: Auf dem Gerät ist bereits eine Einstellung vorhanden, die von Intune nicht überschrieben werden kann. Möglicherweise haben Sie auch zwei Richtlinien mit der gleichen Einstellung, aber mit unterschiedlichen Werten bereitgestellt.
      - **Ausstehend**: Das Gerät hat sich noch nicht bei Intune angemeldet, um die Richtlinie abzurufen. Möglicherweise hat das Gerät die Richtlinie auch bereits empfangen, aber keinen Status an Intune gesendet.
      - **Fehler**: Weitere Informationen zu Fehlern und möglichen Fehlerbehebungen finden Sie unter [Behandlung von Problemen mit dem Zugriff auf Unternehmensressourcen](troubleshoot-company-resource-access-problems.md).

      **Nützliche Links:** 

      - [Möglichkeiten, die Gerätekonformitätsrichtlinien bereitzustellen](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies)
      - [Überwachen von Intune-Richtlinien zur Gerätekonformität](compliance-policy-monitor.md)

## <a name="youre-unsure-if-a-profile-is-correctly-applied"></a>Ermitteln, ob ein Profil korrekt angewendet wurde

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie **Geräte** > **Alle Geräte** aus, wählen Sie anschließend das Gerät aus, und klicken Sie auf **Gerätekonfiguration**. 

    Für jedes Gerät werden die Profile aufgelistet. Jedes Profil verfügt über einen **Status**. Der Status setzt sich aus den zugewiesenen Profilen (einschließlich Einschränkungen und Anforderungen von Hardware und Betriebssystem) zusammen. Mögliche Status sind:

    - **Konform**: Das Gerät hat das Profil empfangen und meldet Intune, dass es der Einstellung entspricht.

    - **Nicht zutreffend**: Die Profileinstellung ist nicht zutreffend. Beispielsweise sind E-Mail-Einstellungen für iOS-Geräte nicht auf ein Android-Gerät anwendbar.

    - **Ausstehend**: Das Profil wurde an das Gerät gesendet, hat aber noch keinen Status an Intune gemeldet. Beispiel: Verschlüsselung unter Android erfordert, dass der Benutzer die Verschlüsselung aktiviert, und sie könnte als ausstehend angezeigt werden.

**Nützlicher Link:** [Monitor device profiles in Microsoft Intune (Überwachen von Geräteprofilen in Microsoft Intune)](device-profile-monitor.md)

> [!NOTE]
> Wenn zwei Richtlinien mit unterschiedlichen Einschränkungsstufen für das gleiche Gerät gelten, wird die restriktivere Richtlinie angewendet.

## <a name="policy-troubleshooting-resources"></a>Richtlinie zur Problembehandlung

- [Problembehandlung bei iOS oder Android-Richtlinien nicht auf Geräte angewendet](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-tip-Troubleshooting-iOS-or-Android-policies-not-applying/ba-p/280154) (öffnet eine andere Microsoft-Website)
- [Problembehandlung für Windows 10-Intune-Richtlinie bei](http://configmgrdogsarchive.com/2018/08/09/troubleshooting-windows-10-intune-policy-failures/) (öffnet einen Blog)
- [Problembehandlung bei benutzerdefinierten CSP-Einstellungen für Windows 10](https://support.microsoft.com/en-us/help/4055338/troubleshoot-csp-setting-windows-10-computer-intune) (öffnet eine andere Microsoft-Website)
- [Windows 10-Gruppenrichtlinie und Intune-MDM Richtlinie](https://blogs.technet.microsoft.com/cbernier/2018/04/02/windows-10-group-policy-vs-intune-mdm-policy-who-wins/) (öffnet eine andere Microsoft-Website)

## <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Warnung: Fehler beim Speichern von Zugriffsregeln in Exchange

**Problem**: Sie erhalten die Warnung **Fehler beim Speichern von Zugriffsregeln in Exchange**  in der Verwaltungskonsole.

Wenn Sie Richtlinien im Exchange-Arbeitsbereich „Lokale Richtlinie“ (Verwaltungskonsole) erstellt haben, aber Office 365 verwenden, werden die konfigurierten Richtlinieneinstellungen von Intune nicht erzwungen. Beachten Sie die Richtlinienquelle in der Warnung. Löschen Sie im Arbeitsbereich „Richtlinie für lokales Exchange“ die Legacyregeln. Die Legacyregeln sind globale Exchange-Regeln in Intune für lokales Exchange und für Office 365 nicht relevant. Erstellen Sie dann eine neue Richtlinie für Office 365.

Unter [Behandeln von Problemen mit dem lokalen Intune Exchange Connector](troubleshoot-exchange-connector.md) finden Sie weitere Informationen.

## <a name="cant-change-security-policies-for-enrolled-devices"></a>Änderung der Sicherheitsrichtlinien für registrierte Geräte nicht möglich

Windows Phone-Geräte gestatten keine Verringerung der Sicherheitsstufe in Sicherheitsrichtlinien, die mittels MDM oder EAS festgelegt wurden, nachdem diese festgelegt wurden. Angenommen, Sie legen ein **Kennwort mit Mindestanzahl von Zeichen** auf 8 fest und versuchen dann, diesen Wert auf 4 zu verringern. In diesem Fall wird die restriktivere Richtlinie auf das Gerät angewendet.

Windows 10-Geräte dürfen nicht von Sicherheitsrichtlinien entfernen, wenn Sie die Richtlinie (Stop-Bereitstellung) die Zuweisung aufheben. Sie müssen möglicherweise behalten die Richtlinie zugewiesen, und ändern Sie dann die Sicherheitseinstellungen auf die Standardwerte zurück.

Abhängig von der Geräteplattform müssen Sie, wenn Sie die Richtlinie auf einen niedrigeren Sicherheitswert ändern möchten, die Sicherheitsrichtlinien möglicherweise zurücksetzen.

In Windows 8.1 wischen Sie beispielsweise auf dem Desktop von rechts nach innen, um die Leiste **Charms** zu öffnen. Wählen Sie **Einstellungen** > **Systemsteuerung** > **Benutzerkonten** aus. Wählen Sie auf der linken Seite den Link **Sicherheitsrichtlinien zurücksetzen** und dann **Richtlinien zurücksetzen** aus.

Andere Plattformen, wie Android, iOS und Windows Phone 8.1 müssen möglicherweise außer Kraft gesetzt und neu registriert werden, damit Sie eine weniger restriktive Richtlinie anwenden können.

Unter [Behandlung von Problemen bei der Geräteregistrierung bei Intune](troubleshoot-device-enrollment-in-intune.md) finden Sie weitere Informationen.

## <a name="pcs-using-the-intune-software-client---classic-portal"></a>PCs mit dem Intune-Softwareclient – klassisches Portal

> [!NOTE]
> Dieser Abschnitt gilt für das klassische Portal. 

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Fehler in „policyplatform.log“ im Zusammenhang mit der Microsoft Intune-Richtlinie

Bei Windows-PCs, die mit dem Intune-Softwareclient verwaltet werden, können Richtlinienfehler in der Datei `policyplatform.log` aus nicht standardmäßiger Einstellungen in der Windows-Benutzerkontensteuerung (UAC) auf dem Gerät resultieren. Einige nicht standardmäßige UAC-Einstellungen können Microsoft Intune-Clientinstallationen und Richtlinienausführungen beeinträchtigen.

#### <a name="resolve-uac-issues"></a>Beheben von UAC-Problemen

1. Setzen Sie den Computer außer Betrieb. Siehe [Entfernen von Geräten](devices-wipe.md).

2. Warten Sie 20 Minuten, bis die Clientsoftware entfernt wurde.

    > [!NOTE]
    > Versuchen Sie nicht, den Client über „Programme und Funktionen“ zu entfernen.

3. Geben Sie im Startmenü **UAC** ein, um die Einstellungen der Benutzerkontensteuerung zu öffnen.

4. Verschieben Sie den Schieberegler für Benachrichtigungen auf die Standardeinstellung.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>FEHLER: Der Wert kann nicht vom Computer abgerufen werden, 0x80041013

Dieser Fehler tritt auf, wenn die Zeit auf dem lokalen System um mindestens fünf Minuten abweicht. Wenn die Zeit auf dem lokalen Computer nicht synchron ist, schlagen sichere Transaktionen fehl, da die Zeitstempel ungültig sind.

Legen Sie die lokale Systemzeit so gut wie möglich auf die Internetzeit fest, um dieses Problem zu beheben. Alternativ können Sie die Systemzeit auf die Zeit der Domänencontroller im Netzwerk festlegen.


## <a name="next-steps"></a>Nächste Schritte

[Häufig auftretende Probleme und Lösungen für E-Mail-Profile in Microsoft Intune](troubleshoot-email-profiles-in-microsoft-intune.md)

Fordern Sie [Hilfe beim Microsoft-Support](get-support.md) an, oder nutzen Sie die [Communityforen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
