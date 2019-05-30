---
title: Verwenden von Sicherheitsrichtlinien in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Fügen Sie die empfohlenen Gruppensicherheitsrichtlinien hinzu, oder konfigurieren Sie sie, um Benutzer und Daten auf Geräten mit Microsoft Intune zur mobilen Geräteverwaltung zu schützen. Aktivieren von BitLocker, Konfigurieren von Windows Defender Advanced Threat Protection, Steuern von Internet Explorer, Verwenden von SmartScreen, Festlegen lokaler Sicherheitsrichtlinien, Anfordern eines Kennworts, Blockieren von Internetdownloads und vieles mehr.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 70638228875f1fb063a2ea22dc424c00f3940a30
ms.sourcegitcommit: ef4bc7318449129af3dc8c0154e54a264b7bf4e5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65197621"
---
# <a name="create-a-windows-10-security-baseline-in-intune"></a>Erstellen einer Windows 10-Sicherheitsbaseline in Intune

Sicherheitsbaselines sind ein Feature in der Vorschau, das für Geräte unter Windows 10 und höher verfügbar ist. Dieses Feature umfasst viele von Intune unterstützte Einstellungen, mit denen Sie Ihre Benutzer und Geräte sichern und schützen können. Es setzt diese Einstellungen auch automatisch auf Werte, die von Sicherheitsteams empfohlen werden. Die Baseline aktiviert beispielsweise u.a. automatisch BitLocker, fordert automatisch ein Kennwort zum Entsperren eines Geräts an und deaktiviert automatisch die Standardauthentifizierung.

Diese Funktion gilt für:

- Windows 10, Version 1809 und höher

> [!NOTE]
> Die Sicherheitsbaselines sind zwar in der Vorschau verfügbar, aber Microsoft empfiehlt nicht die Verwendung von Profilen in einer Produktionsumgebung, da die Baselines sich im Verlauf der Vorschau ändern können. Sobald die Sicherheitsbaselines allgemein verfügbar sind, werden bestehende Profile nicht mehr in die neusten unterstützten Profile konvertiert.

Das Ziel der Verwendung von Sicherheitsbaselines ist die Bereitstellung eines sicheren End-to-End-Workflows bei der Arbeit mit Microsoft 365. Einige Vorteile sind:

- Eine Sicherheitsbaseline enthält Best Practices und Empfehlungen für Einstellungen, die sich auf die Sicherheit auswirken. Partner von Intune ist dasselbe Windows-Sicherheitsteam, das Gruppenrichtlinien-Sicherheitsbaselines erstellt. Diese Empfehlungen basieren auf Anleitungen und umfassenden Erfahrungen.
- Wenn Sie noch keine Erfahrung mit Intune haben und nicht sicher sind, wo Sie anfangen sollen, bieten Sicherheitsbaselines Ihnen einen Vorteil. Sie können schnell ein sicheres Profil erstellen und bereitstellen und sicher sein, dass Sie so die Ressourcen und Daten Ihrer Organisation schützen.
- Wenn Sie zurzeit die Gruppenrichtlinie verwenden, ist mit diesen Baselines die Migration zu Intune zur Verwaltung viel einfacher. Diese Baselines sind nativ in Intune integriert und weisen eine moderne Benutzeroberfläche auf.

Sicherheitsbaselines erstellen ein „Konfigurationsprofil“ in Intune. Dieses Profil umfasst alle Einstellungen in der Baseline. Anschließend wenden Sie dieses Profil an oder weisen es Ihren Benutzern, Gruppen und Geräten zu.

Nach der Zuweisung des Profils können Sie das Profil und die Baseline überwachen. Beispielsweise können Sie sehen, welche Geräte mit der Baseline übereinstimmen oder nicht.

Dieser Artikel veranschaulicht die Verwendung der Sicherheitsbaselines zum Erstellen eines Profils, Zuweisen und Überwachen des Profils.

Der Artikel [Windows-Sicherheitsgrundsätze](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) ist eine hervorragende Ressource, um mehr über dieses Feature zu erfahren. Der Artikel [Mobile Geräteverwaltung](https://docs.microsoft.com/windows/client-management/mdm/) (Mobile Device Management, MDM) ist eine hervorragende Ressource zu MDM und den Möglichkeiten, die Ihnen Windows-Geräte bieten.

## <a name="prerequisites"></a>Voraussetzungen
Wenn Sie Baselines in Intune verwalten möchten, muss Ihr Konto über die integrierte Rolle [Policy and Profile Manger](role-based-access-control.md#built-in-roles) (Richtlinien- und Profilmanager) verfügen.


## <a name="co-managed-devices"></a>Gemeinsam verwaltete Geräte

Sicherheitsbaselines für von Intune verwaltete Geräten ähneln denen mit Configuration Manager gemeinsam verwalteter Geräte. Bei gemeinsam verwalteten Geräten werden System Center Configuration Manager und Microsoft Intune simultan zum Verwalten der Windows 10-Geräte verwendet. Sie können Ihre vorhandene Configuration Manager-Investition in der Cloud mit den Vorteilen von Intune verbinden. Der Artikel [Was ist gemeinsame Verwaltung?](https://docs.microsoft.com/sccm/comanage/overview) ist eine großartige Ressource, wenn Sie Configuration Manager verwenden und auch die Vorteile der Cloud genießen möchten.

Wenn Sie gemeinsam verwaltete Geräte verwenden, müssen Sie die **Gerätekonfiguration**-Workload (ihre Einstellungen) auf Intune verlagern. Im Abschnitt [Gerätekonfiguration](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration) finden Sie weitere Informationen.

## <a name="create-the-profile"></a>Erstellen des Profils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com/) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.
2. Wählen Sie **Gerätesicherheit** > **Sicherheitsbaselines (Vorschau)** aus. Eine Liste der verfügbaren Baselines ist verfügbar. Wenn mehrere Baselines hinzugefügt werden, werden diese hier angezeigt:

    ![Anzeigen einer Liste der derzeit in Intune verfügbaren Sicherheitsbaselines](./media/security-baselines/available-baselines.png)

3. Wählen Sie die Baseline, die Sie verwenden möchten, und dann **Profil erstellen** aus.
4. Geben Sie in **Grundlagen** die folgenden Eigenschaften ein:

    - **Name**: Geben Sie einen Namen für Ihr Sicherheitsbaselinesprofil ein. Geben Sie beispielsweise `pilot Windows 10 MDM baseline - Oct 2018` ein.
    - **Beschreibung**: Geben Sie einen Text ein, der die Funktion dieser Baseline beschreibt. Sie können einen beliebigen Text als Beschreibung eingeben. Dies ist optional, wird jedoch definitiv empfohlen.

5. Erweitern Sie **Einstellungen**. In der Liste werden alle Einstellungen in dieser Sicherheitsbaseline angezeigt, und worauf die Einstellung automatisch festgelegt wird. Die Einstellungen und deren Werte werden empfohlen und können von Ihnen geändert werden.

    ![Erweitern der Einstellung, um alle Einstellungen in dieser Sicherheitsbaseline in Intune anzuzeigen](./media/security-baselines/sample-list-of-settings.png)

    Erweitern Sie einige der Einstellungen, um deren Werte zu überprüfen. Erweitern Sie z. B. **Windows Defender**. Beachten Sie bei einigen der Einstellungen die festgelegten Werte:

    ![Anzeige der automatischen Festlegung einiger Windows Defender-Einstellungen in Intune](./media/security-baselines/expand-windows-defender.png)

6. **Erstellen** Sie das Profil. 
7. Wählen Sie **Profile** aus. Ihr Profil wird erstellt und in der Liste angezeigt. Aber es bewirkt noch nichts. Weisen Sie anschließend das Profil zu.

## <a name="assign-the-profile"></a>Zuweisen des Profils

Nachdem das Profil erstellt wurde, kann es Benutzern, Geräten und Gruppen zugewiesen werden. Nach der Zuweisung werden das Profil und seine Einstellungen auf Benutzer, Geräte und Gruppen Ihrer Wahl angewandt.

1. Wählen Sie in Intune **Sicherheitsbaselines** und dann eine Baseline und **Profile** aus.
2. Wählen Sie Ihr Profil und **Zuweisungen** aus.

    ![Auswählen Ihres Sicherheitsbaselineprofils in Intune und Klicken auf Zuweisungen, um das Profil bereitzustellen](./media/security-baselines/assignments.png)

3. Fügen Sie auf der Registerkarte **Einschließen** die Gruppen, Benutzer oder Geräte hinzu, auf die Sie diese Richtlinie anwenden möchten.

    > [!TIP]
    > Beachten Sie, dass Sie auch Gruppen **Ausschließen** können. Wenn Sie eine Richtlinie auf **Alle Benutzer** anwenden, erwägen Sie, die Administratorgruppen auszuschließen. Sie und Ihre Administratoren möchten bei einem Zwischenfall ja nicht ausgesperrt werden.

4. **Speichern** Sie die Änderungen.

Sobald Sie das Profil gespeichert haben, erfolgt die Pushübertragung auf Geräte, wenn sie sich bei Intune einchecken. Dies kann also sofort geschehen.

## <a name="available-security-baselines"></a>Verfügbare Sicherheitsbaselines  

Die folgenden Sicherheitsbaselines können für Intune verwendet werden.
- **Vorschau: Sicherheitsbaseline für die Verwaltung mobiler Geräte**
  - Version: [Oktober 2018](security-baseline-settings-windows.md)

## <a name="q--a"></a>Q & A

#### <a name="why-these-settings"></a>Warum diese Einstellungen?

Diese Empfehlungen basieren auf der jahrelangen Erfahrung des Microsoft-Sicherheitsteams in der direkten Zusammenarbeit mit Windows-Entwicklern und der Sicherheitscommunity. Die Einstellungen in dieser Baseline werden als die wichtigsten sicherheitsbezogenen Konfigurationsoptionen betrachtet. In jedem neuen Build von Windows passt das Team die Empfehlungen basierend auf neu herausgegebenen Features an.

#### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>Gibt es einen Unterschied in den Empfehlungen für die Windows-Sicherheitsbaselines für die Gruppenrichtlinie im Vergleich zu Intune?

Das gleiche Microsoft-Sicherheitsteam hat die Einstellungen für jede Baseline ausgewählt und organisiert. Intune umfasst alle relevanten Einstellungen in der Intune-Sicherheitsbaseline. Es gibt einige Einstellungen in der Gruppenrichtlinienbaseline, die für einen lokalen Domänencontroller spezifisch sind. Diese Einstellungen werden von den Intune-Empfehlungen ausgeschlossen. Alle anderen Einstellungen sind identisch.

#### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>Sind die Intune-Sicherheitsbaselines CIS- oder NSIT-kompatibel?

Streng genommen, nicht. Das Microsoft-Sicherheitsteam berät Unternehmen wie CIS, um Empfehlungen zusammenzutragen. Allerdings gibt es keine 1:1-Zuordnung von „CIS-kompatiblen“ und Microsoft-Baselines.

#### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Welche Zertifizierungen haben die Sicherheitsbaselines von Microsoft? 

- Microsoft veröffentlicht weiterhin Sicherheitsbaselines für Gruppenrichtlinien (GPOs) und das [Security Compliance Toolkit](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10), wie seit vielen Jahren. Diese Baselines werden von vielen Organisationen verwendet. Die Empfehlungen in diesen Baselines entstammen der Zusammenarbeit des Microsoft-Sicherheitsteams mit Unternehmenskunden und externen Einrichtungen, einschließlich des Department of Defense (DoD, Verteidigungsministerium der USA), National Institute of Standards and Technology (NIST, Nationales Institut für Standards und Technologie) und anderer. Wir teilen unsere Empfehlungen und Baselines mit diesen Organisationen. Diese Organisationen haben auch ihre eigenen Empfehlungen, die die Empfehlungen von Microsoft sehr genau widerspiegeln. Da die mobile Geräteverwaltung (MDM) in der Cloud zunimmt, hat Microsoft entsprechende MDM-Empfehlungen zu diesen Gruppenrichtlinien-Baselines erstellt. Diese zusätzlichen Baselines sind in Microsoft Intune integriert und enthalten Konformitätsberichte zu Benutzern, Gruppen und Geräten, die die Baseline befolgen (oder nicht).

- Viele Kunden nutzen die Intune-Baselineempfehlungen als Ausgangspunkt und passen sie ihren IT- und Sicherheitsanforderungen an. Die **MDM-Sicherheitsbaseline** für Windows 10 RS5 von Microsoft ist die erste Baseline, die freigegeben wird. Diese Baseline wird als allgemeine Infrastruktur erstellt, die Kunden ermöglicht, schließlich andere, auf CIS, NIST und anderen Standards basierende Sicherheitsbaselines zu importieren. Derzeit ist sie für Windows verfügbar und wird schließlich iOS und Android einschließen.

- Das Migrieren von lokalen Active Directory-Gruppenrichtlinien zu einer reinen Cloudlösung mithilfe von Azure Active Directory (AD) mit Microsoft Intune ist eine Reise. Zur Unterstützung dienen begleitende GPOs, die für hybride AD- und in Azure AD eingebundene Geräte veröffentlicht werden. Diese Geräte können MDM-Einstellungen aus der Cloud (Intune) und Gruppenrichtlinieneinstellungen vom lokalen Domänencontroller nach Bedarf abrufen.

## <a name="next-steps"></a>Nächste Schritte
- Lesen Sie sich den Artikel zu den [Windows-Einstellungen für Sicherheitsbaselines](security-baseline-settings-windows.md) durch, die von Intune unterstützt werden.  
- Überprüfen Sie den Status und überwachen Sie [Baseline und Profil](security-baselines-monitor.md).
