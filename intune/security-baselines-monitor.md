---
title: Überprüfen von Erfolg oder Fehler bei Sicherheitsbaselines in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Überprüfen Sie Fehler-, Konflikt- und Erfolgsstatus bei der Bereitstellung von Sicherheitsbaselines für Benutzer und Geräte in Microsoft Intune MDM. Erfahren Sie, wie Sie Probleme mithilfe von Clientprotokollen und den Berichtsfunktionen in Intune behandeln.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/24/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b853d42efc247f6080cc4ed6ad8b4943b85b3215
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230821"
---
# <a name="monitor-the-security-baseline-and-profile-in-microsoft-intune"></a>Überwachen von Sicherheitsbaseline und Profil in Microsoft Intune

Bei der Verwendung von Sicherheitsbaselines stehen verschiedene Optionen für die Überwachung zur Verfügung. Sie können das Sicherheitsbaselineprofil überwachen, das für Ihre Benutzer und Geräte gilt. Sie können auch die tatsächliche Baseline überwachen, und alle Geräte, die den empfohlenen Werten entsprechen (oder nicht).

Dieser Artikel führt Sie durch beide Überwachungsoptionen.

Im Artikel [Erstellen einer Windows 10-Sicherheitsbaseline in Intune](security-baselines.md) finden Sie weitere Details zum Sicherheitsbaselinefeature in Microsoft Intune.

## <a name="monitor-the-baseline-and-your-devices"></a>Überwachen der Baseline und Ihrer Geräte

Wenn Sie die Baseline überwachen, erhalten Sie basierend auf den Empfehlungen von Microsoft Einblicke in den Sicherheitsstatus Ihrer Geräte.

> [!NOTE]
> Nach der Zuweisung einer Baseline kann es bis zu 24 Stunden dauern, bis Berichte aktualisiert werden. Anschließend kann es bis zur Aktualisierung 6 Stunden dauern.

1. Wählen Sie im [Azure-Portal](https://portal.azure.com/) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.
2. Wählen Sie **Sicherheitsbaselines (Vorschau)** und dann eine Baseline aus.
3. Das Diagramm in **Übersicht** zeigt, wie viele Geräte von der Baseline betroffen sind, die Sie ausgewählt haben, sowie die verschiedenen Status:

    ![Überprüfen des Status der Geräte](./media/security-baselines-monitor/overview.png)

    Die folgenden Status sind verfügbar:

    - **Entspricht Baseline**: Alle Einstellungen in der Baseline stimmen mit den empfohlenen Einstellungen überein.
    - **Entspricht nicht Baseline**: Mindestens eine Einstellung in der Basislinie entspricht nicht den empfohlenen Einstellungen.
    - **Falsch konfiguriert**: Mindestens eine Einstellung wurde nicht ordnungsgemäß konfiguriert. Dieser Status bedeutet, dass die Einstellung sich in einem Konflikt-, Fehler- oder ausstehenden Status befindet.
    - **Nicht zutreffend**: Mindestens eine Einstellung ist nicht zutreffend und wird nicht angewendet.

4. Wählen Sie einen Status aus, dem Geräte zugeordnet sind. Wählen Sie z.B. den Status **Falsch konfiguriert** aus.

5. Eine Liste aller Geräte mit diesem Status wird angezeigt. Wählen Sie ein bestimmtes Gerät aus, um weitere Details anzuzeigen. 

    Wählen Sie im folgenden Beispiel **Gerätekonfiguration** und dann das Profil mit einem Fehlerstatus aus:

    ![Überprüfen des Status der Geräte](./media/security-baselines-monitor/device-configuration-profile-list.png)

    Wählen Sie das „Fehler“-Profil aus. Eine Liste aller Einstellungen im Profil und deren Status werden angezeigt. Jetzt können Sie scrollen, um die Einstellung zu finden, die den Fehler verursacht:

    ![Anzeigen der Einstellung, die den Fehler verursacht hat](./media/security-baselines-monitor/profile-with-error-status.png)

Verwenden Sie diese Berichterstellung, um alle Einstellungen in einem Profil anzuzeigen, die ein Problem verursachen. Außerdem erhalten Sie weitere Informationen zu Richtlinien und Profilen, die auf den Geräten bereitgestellt werden.

> [!NOTE]
> Wenn eine Eigenschaft in der Baseline auf **Nicht konfiguriert** festgelegt ist, wird die Einstellung ignoriert, und keine Einschränkungen werden erzwungen. Die Eigenschaft wird nicht in Berichten angezeigt.

## <a name="monitor-the-profile"></a>Überwachen des Profils

Das Überwachen des Profils bietet Ihnen einen Einblick in den Bereitstellungsstatus Ihrer Geräte, aber nicht in den Sicherheitsstatus gemäß der Baselineempfehlungen.

1. Wählen Sie in Intune **Sicherheitsbaselines**, dann eine Baseline und dann **Erstellte Profile** aus.

2. Wählen Sie ein Profil aus. In **Übersicht** zeigt die Abbildung, wie vielen Geräten und Benutzern dieses Profil zugewiesen ist:

    ![Anzeige der Anzahl der Geräte und Benutzer, die dem Sicherheitsbaselineprofil zugewiesen sind](./media/security-baselines-monitor/existing-profile-overview.png)

3. Unter **Verwalten** > **Eigenschaften** wird eine Liste aller Einstellungen in der Baseline angezeigt. Sie können auch jede dieser Einstellungen ändern:

    ![Anzeigen und Aktualisieren von Einstellungen im Sicherheitsbaselineprofil](./media/security-baselines-monitor/manage-settings.png)

4. Unter **Überwachung** sehen Sie den Bereitstellungsstatus des Profils auf einzelnen Geräten, den Status für jeden Benutzer und den Status für jede Einstellung in der Baseline:

    ![Anzeigen der verschiedenen Überwachungsoptionen für ein Sicherheitsbaselineprofil](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="troubleshoot-using-per-setting-status"></a>Problembehandlung bei der Verwendung von Status pro Einstellung

Sie haben eine Sicherheitsbaseline bereitgestellt, aber der Bereitstellungsstatus zeigt einen Fehler an. Die folgenden Schritte bieten Ihnen eine Anleitung zur Problembehandlung.

1. Wählen Sie in Intune **Sicherheitsbaselines**, dann eine Baseline und dann **Erstellte Profile** aus.
2. Wählen Sie ein Profil unter **Überwachung** > **Status pro Einstellung** aus.
3. Die Tabelle enthält alle Einstellungen und den Status jeder Einstellung. Wählen Sie die Spalte **Fehler** oder **Konflikt** aus, um die Einstellung anzuzeigen, die Ursache des Fehlers ist.

### <a name="mdm-diagnostic-information"></a>MDM-Diagnoseinformationen

Jetzt kennen Sie die problematische Einstellung. Der nächste Schritt ist, herauszufinden, warum diese Einstellung einen Fehler oder Konflikt verursacht. 

Auf Windows 10-Geräten ist ein integrierter MDM-Diagnoseinformationsbericht verfügbar. Dieser Bericht enthält Standardwerte, aktuelle Werte, listet die Richtlinie auf, zeigt an, ob sie für das Gerät oder den Benutzer bereitgestellt wird, und vieles mehr. Verwenden Sie diesen Bericht, um zu ermitteln, warum die Einstellung einen Konflikt oder Fehler verursacht hat.

1. Navigieren Sie auf dem Gerät zu **Einstellungen** > **Konten** > **Zugriff auf Geschäfts-, Schul- oder Unikonto**.
2. Wählen Sie das Konto und dann **Informationen** > **Erweiterter Diagnosebericht** > **Bericht erstellen** aus.
3. Wählen Sie **Exportieren** aus, und öffnen Sie die generierte Datei.
4. Suchen Sie in den verschiedenen Abschnitten des Berichts nach der Fehler- oder Konflikteinstellung.

  Schauen Sie z.B. in den Abschnitt **Registrierte Konfigurationsquellen und Zielressourcen** oder **Nicht verwaltete Richtlinien**. So können Sie erfahren, warum der Fehler oder Konflikt verursacht wird.

[Diagnostizieren von MDM-Fehlern in Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) enthält weitere Informationen zu diesen integrierten Bericht.

> [!TIP]
> - Einige Einstellungen werden auch in der GUID aufgelistet. Sie können für diese GUID in der lokalen Registrierung (Regedit) nach festgelegten Werten suchen.
> - Die Protokolle der Ereignisanzeige können auch einige Fehlerinformationen zu der problematischen Einstellung enthalten (**Ereignisanzeige** > **Anwendungs- und Dienstprotokolle** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin** ).

## <a name="next-steps"></a>Nächste Schritte

[Überwachung von Geräteprofilen](device-profile-monitor.md) und [Betrachten einiger allgemeiner Probleme und ihrer Lösungen](device-profile-troubleshoot.md).
