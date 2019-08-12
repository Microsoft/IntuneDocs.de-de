---
title: Verwenden von Sicherheitsrichtlinien in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Schützen Sie Benutzer und Daten auf Geräten mit Microsoft Intune zur Verwaltung mobiler Geräte mit den empfohlenen Windows-Sicherheitseinstellungen. Aktivieren der Verschlüsselung, Konfigurieren von Microsoft Defender Advanced Threat Protection, Steuern von Internet Explorer, Festlegen lokaler Sicherheitsrichtlinien, Anfordern eines Kennworts, Blockieren von Internetdownloads und vieles mehr.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c378fd3b208396f9d2f83b7bd56f50dbf7a7e3f7
ms.sourcegitcommit: 864fdf995c2b41f104a98a7e2665088c2864774f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68679969"
---
# <a name="use-security-baselines-to-configure-windows-10-devices-in-intune"></a>Konfigurieren von Windows 10-Geräten in Intune mithilfe von Sicherheitsbaselines

Nutzen Sie die Sicherheitsbaselines von Intune, um Ihre Benutzer und Geräte abzusichern und zu schützen. Sicherheitsbaselines sind vorkonfigurierte Gruppen von Windows-Einstellungen, die Ihnen helfen, eine bekannte Zusammenstellung von Einstellungen und Standardwerten anzuwenden, die von den maßgeblichen Sicherheitsteams empfohlen werden. Wenn Sie in Intune ein Sicherheitsbaselineprofil erstellen, wird ein *Gerätekonfiguration*sprofil angelegt.

Diese Funktion gilt für:

- Windows 10, Version 1809 und höher

Sie stellen Sicherheitsbaselines für Gruppen von Benutzern oder Geräten in Intune bereit. Die Einstellungen gelten für Geräte, auf denen Windows 10 oder höher ausgeführt wird. Die *MDM-Sicherheitsbaselinie* aktiviert beispielsweise für Wechseldatenträger u.a. automatisch BitLocker, fordert automatisch ein Kennwort zum Entsperren eines Geräts an und deaktiviert automatisch die Standardauthentifizierung. Wenn eine Standardeinstellung für Ihre Umgebung nicht funktioniert, passen Sie die so Baseline an, dass die benötigten Einstellungen übernommen werden.  

Separate Baselinetypen können zwar die gleichen Einstellungen enthalten, aber unterschiedliche Standardwerte für diese Einstellungen verwenden. Es ist wichtig, die Standardwerte in den von Ihnen gewählten Baselines zu verstehen und anschließend jede Baseline an Ihre Unternehmensanforderungen anzupassen.  

> [!NOTE]
> Microsoft empfiehlt nicht, Vorschauversionen von Sicherheitsbaselines in einer Produktionsumgebung einzusetzen. Die Einstellungen in einer Vorschaubaseline können sich im Laufe der Vorschau ändern. 

Das Ziel von Sicherheitsbaselines ist die Ermöglichung eines durchgängig sicheren Workflows beim Arbeiten mit Microsoft 365. Einige Vorteile sind:

- Eine Sicherheitsbaseline enthält Best Practices und Empfehlungen für Einstellungen, die sich auf die Sicherheit auswirken. Partner von Intune ist dasselbe Windows-Sicherheitsteam, das Gruppenrichtlinien-Sicherheitsbaselines erstellt. Diese Empfehlungen basieren auf Anleitungen und umfassenden Erfahrungen.
- Wenn Sie noch keine Erfahrung mit Intune haben und nicht sicher sind, wo Sie anfangen sollen, sind Sicherheitsbaselines ein guter Einstieg. Sie können schnell ein sicheres Profil erstellen und bereitstellen und sicher sein, dass Sie so die Ressourcen und Daten Ihrer Organisation schützen.
- Wenn Sie zurzeit die Gruppenrichtlinie verwenden, ist mit diesen Baselines die Migration zu Intune zur Verwaltung viel einfacher. Diese Baselines sind nativ in Intune integriert und weisen eine moderne Benutzeroberfläche auf.



Der Artikel [Windows-Sicherheitsgrundsätze](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) ist eine hervorragende Ressource, um mehr über dieses Feature zu erfahren. Der Artikel [Mobile Geräteverwaltung](https://docs.microsoft.com/windows/client-management/mdm/) (Mobile Device Management, MDM) ist eine hervorragende Ressource zu MDM und den Möglichkeiten, die Ihnen Windows-Geräte bieten.

## <a name="security-baseline-versions-and-instances"></a>Versionen und Instanzen und Sicherheitsbaselines
Von Zeit zu Zeit werden neue Updates für eine Baseline veröffentlicht. Bei jeder neuen Versionsinstanz einer Baseline können Einstellungen hinzugefügt oder entfernt oder andere Änderungen vorgenommen werden. Wenn beispielsweise in neuen Versionen von Windows 10 neue Windows 10-Einstellungen verfügbar werden, erhält die MDM-Sicherheitsbaseline möglicherweise eine neue Versionsinstanz, die die neuesten Einstellungen enthält.  

In der Intune-Konsole können Sie die verfügbaren Sicherheitsbaselines und Informationen zu diesen anzeigen. Zu den verfügbaren Informationen gehört, wie viele Profile Sie haben, die diesen Baselinetyp verwenden, wie viele einzelne Instanzen des Baselinetyps verfügbar sind und wann die letzte aktuelle Instanz verfügbar gemacht bzw. veröffentlicht wurde.  Das folgende Beispiel zeigt die Kachel für eine gängige MDM-Sicherheitsbaseline:  

![Kachel „Baseline“](./media/security-baselines/baseline-tile.png)

Um Informationen zu den von Ihnen verwendeten Baselineversionen anzuzeigen, wählen Sie eine Baseline und dann **Versionen** aus. Intune zeigt Details zu den Versionen an, die von Ihren Profilen verwendet werden. Im Bereich „Versionen“ können Sie eine einzelne Version auswählen, um nähere Informationen über die Profile einzusehen, die diese Version verwenden. Sie können auch zwei verschiedene Versionen auswählen und dann **Baselines vergleichen** wählen, um eine CSV-Datei herunterzuladen, in der diese Unterschiede detailliert beschrieben sind.  

![Baselines vergleichen](./media/security-baselines/compare-baselines.png)

Wenn Sie ein Sicherheitsbaseline-*Profil* erstellen, verwendet das Profil automatisch die zuletzt veröffentlichte Instanz der Sicherheitsbaseline.  Sie können zuvor erstellte Profile, die eine frühere Instanz der Baselineversion verwenden, weiterhin einsetzen und bearbeiten, einschließlich der mit einer Vorschauversion erstellten Baselines. 

Sicherheitsbaseline-Profile unterstützen eine [Änderung der Version](#change-the-baseline-instance-for-a-profile) der verwendeten Baseline. Das bedeutet, dass Sie bei Veröffentlichung einer neuen Version kein neues Baselineprofil erstellen müssen, um in den Genuss der Vorteile zu kommen. Stattdessen können Sie, wenn Sie soweit sind, ein Baselineprofil auswählen und dann die integrierte Option zum Ändern der Instanzversion für dieses Profil verwenden.  

## <a name="available-security-baselines"></a>Verfügbare Sicherheitsbaselines 

Die folgenden Sicherheitsbaseline-Instanzen können für Intune verwendet werden. Klicken Sie auf die Links, um die Einstellungen für die neueste Instanz jeder Baseline anzuzeigen. 

- **MDM-Sicherheitsbaseline**
  - [MDM-Sicherheitsbaseline für Mai 2019](security-baseline-settings-mdm.md)
  - [Vorschau: MDM-Sicherheitsbaseline für Oktober 2018](security-baseline-settings-mdm-archive.md)

- **Microsoft Defender ATP-Baseline**  
  *(Um diese Baseline verwenden zu können, muss Ihre Umgebung den Anforderungen zur Verwendung von [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites) entsprechen)* .
  - [Vorschau: Microsoft Defender ATP-Baseline](security-baseline-settings-defender-atp.md)  

  > [!NOTE]
  > Die Microsoft Defender ATP-Sicherheitsbaseline wurde für physische Geräte optimiert und ist zurzeit nicht für die Verwendung auf virtuellen Computern (VMs) oder VDI-Endpunkten empfehlenswert. Bestimmte Baselineeinstellungen können sich auf interaktive Remotesitzungen in virtualisierten Umgebungen auswirken.  Weitere Informationen finden Sie unter [Increase compliance to the Microsoft Defender ATP security baseline (Erhöhung der Compliance für die Microsoft Defender ATP-Sicherheitsbaseline)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline).

Sie können die zuvor auf der Grundlage einer Vorschauvorlage erstellten Profile weiterhin nutzen und bearbeiten, auch wenn diese Vorschauvorlage für die Erstellung neuer Profile nicht mehr verfügbar ist. 

## <a name="prerequisites"></a>Voraussetzungen
- Wenn Sie Baselines in Intune verwalten möchten, muss Ihr Konto über die integrierte Rolle [Policy and Profile Manger](role-based-access-control.md#built-in-roles) (Richtlinien- und Profilmanager) verfügen.

- Einige Baselines können ein aktives Abonnement für zusätzliche Dienste wie Microsoft Defender ATP erfordern.  

## <a name="co-managed-devices"></a>Gemeinsam verwaltete Geräte

Sicherheitsbaselines für von Intune verwaltete Geräten ähneln denen mit Configuration Manager gemeinsam verwalteter Geräte. Bei gemeinsam verwalteten Geräten werden System Center Configuration Manager und Microsoft Intune simultan zum Verwalten der Windows 10-Geräte verwendet. Sie können Ihre vorhandene Configuration Manager-Investition in der Cloud mit den Vorteilen von Intune verbinden. Der Artikel [Was ist gemeinsame Verwaltung?](https://docs.microsoft.com/sccm/comanage/overview) ist eine großartige Ressource, wenn Sie Configuration Manager verwenden und auch die Vorteile der Cloud genießen möchten.

Wenn Sie gemeinsam verwaltete Geräte verwenden, müssen Sie die **Gerätekonfiguration**-Workload (ihre Einstellungen) auf Intune verlagern. Im Abschnitt [Gerätekonfiguration](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration) finden Sie weitere Informationen.

## <a name="create-the-profile"></a>Erstellen des Profils

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an, und wählen Sie **Gerätesicherheit** > **Sicherheitsbaselines** aus, um die Liste der verfügbaren Baselines anzuzeigen.


    ![Auswählen einer Sicherheitsbaseline zum Konfigurieren](./media/security-baselines/available-baselines.png)

2. Wählen Sie die Baseline, die Sie verwenden möchten, und dann **Profil erstellen** aus.  

3. Geben Sie auf der Registerkarte **Grundlagen** die folgenden Eigenschaften an:

    - **Name**: Geben Sie einen Namen für Ihr Sicherheitsbaselinesprofil ein. Geben Sie beispielsweise *Standardprofil für Defender ATP* ein.

    - **Beschreibung**: Geben Sie einen Text ein, der die Funktion dieser Baseline beschreibt. Sie können einen beliebigen Text als Beschreibung eingeben. Dies ist optional, wird jedoch empfohlen.  

   Klicken Sie auf **Weiter**, um zur nächsten Registerkarte zu gelangen. Nachdem Sie zu einer neuen Registerkarte gewechselt sind, können Sie den Namen der Registerkarte auswählen, um zu einer zuvor angezeigten Registerkarte zurückzukehren.  

4. Zeigen Sie auf der Registerkarte „Konfigurationseinstellungen“ die Gruppen von **Einstellungen** an, die in der von Ihnen ausgewählten Baseline verfügbar sind. Sie können eine Gruppe aufklappen, um die Einstellungen in dieser Gruppe und die Standardwerte für diese Einstellungen in der Baseline anzuzeigen. So finden Sie bestimmte Einstellungen
   - Wählen Sie eine Gruppe aus, um die verfügbaren Einstellungen aufzuklappen und zu überprüfen.  
   - Geben Sie Stichwörter in die *Suchleiste* an, um die Ansicht so zu filtern, dass nur die Gruppen angezeigt werden, die Ihren Suchkriterien entsprechen.  
 
   Jede Einstellung in einer Baseline hat für die jeweilige Baselineversion eine Standardkonfiguration. Konfigurieren Sie die Standardeinstellungen neu, damit sie ihre geschäftlichen Anforderungen erfüllen. Verschiedene Baselines können die gleiche Einstellung enthalten und je nach Zweck der Baseline unterschiedliche Standardwerte für die Einstellung verwenden. 

    ![Erweitern einer Gruppe, um die Einstellungen dafür anzuzeigen](./media/security-baselines/sample-list-of-settings.png)

5. Wählen Sie auf der Registerkarte **Bereichstags** den Befehl **Bereichstags auswählen** aus, um den Bereich *Tags auswählen* zu öffnen, in dem Sie dem Profil Bereichstags zuweisen. 

6. Wählen Sie auf der Registerkarte **Zuweisungen** den Befehl **Einzuschließende Gruppen auswählen**, und weisen Sie dann die Baseline einer oder mehreren Gruppen zu. Wählen Sie **Auszuschließende Gruppen auswählen**, um die Zuweisung anzupassen.  

   ![Zuweisen eines Profils](./media/security-baselines/assignments.png)
  
7. Wenn Sie die Baseline bereitstellen möchten, wechseln Sie zur Registerkarte **Überprüfen + erstellen**, um die Details der Baseline zu überprüfen. Klicken Sie auf **Erstellen**, um das Profil zu speichern und bereitzustellen.  

   Sobald Sie das Profil erstellt haben, gilt es in der zugewiesenen Gruppe möglicherweise sofort.

   > [!TIP]  
   > Wenn Sie ein Profil speichern, ohne es zuvor Gruppen zuzuweisen, können Sie es später bearbeiten.  

   ![Überprüfen der Baseline](./media/security-baselines/review.png) 

  
8. Nachdem Sie ein Profil erstellt haben, können Sie es bearbeiten, indem Sie zu **Gerätesicherheit** > **Sicherheitsbaselines** wechseln und dann den konfigurierten Baselinetyp und **Profile** auswählen.  Wählen Sie das Profil in der Liste der verfügbaren Profile aus, und klicken Sie dann auf **Eigenschaften**. Sie können Einstellungen auf allen verfügbaren Konfigurationsregisterkarten bearbeiten und auf **Überprüfen + speichern** klicken, um Ihre Änderungen zu übernehmen.  

## <a name="change-the-baseline-instance-for-a-profile"></a>Ändern der Baseline-Instanz eines Profils
Baselineprofile unterstützen eine Änderung der von dem Profil verwendeten Baseline-Instanz. Sie können eine ältere Instanz oder eine neuere Instanz der gleichen Baseline auswählen.  Sie können nicht zwischen zwei verschiedenen Baselines wechseln, d.h. ein Profil so ändern, dass es von der Verwendung einer Baseline für Defender ATP zur Verwendung der MDM-Sicherheitsbaseline wechselt. 

Während Sie eine Änderung der Baselineversion konfigurieren, haben Sie die Möglichkeit, eine CSV-Datei herunterzuladen, die die Änderungen zwischen den beiden beteiligten Baselineversionen auflistet. Sie haben auch die Möglichkeit, alle Ihre Anpassungen in der ursprünglichen Baselineversion zu belassen und sie auf die neue Version anzuwenden oder alle Standardwerte der neuen Baselineversion zu implementieren, die Sie ausgewählt haben. 

Nach dem Speichern im Anschluss an die Konvertierung wird die Baseline für zugewiesene Gruppen sofort erneut bereitgestellt.  

**Während der Konvertierung**:
- Neue nicht in der Originalversion vorhandene Einstellungen werden hinzugefügt und so festgelegt, dass sie die Standardwerte verwenden.  

- Nicht in der von Ihnen ausgewählten neuen Baselineversion enthaltene Einstellungen werden entfernt und von diesem Sicherheitsbaseline-Profil nicht mehr erzwungen.  

  Wenn eine Einstellung nicht mehr von einem Baselineprofil verwaltet wird, wird diese Einstellung auf dem Gerät nicht zurückgesetzt. Stattdessen bleibt die Einstellung auf dem Gerät auf ihre letzte Konfiguration festgelegt, bis ein anderer Prozess die Einstellung ändert. Beispiele für Prozesse, die eine Einstellung ändern können, nachdem Sie die Verwaltung eingestellt haben, sind ein anderes Baselineprofil, eine Gruppenrichtlinieneinstellung oder eine auf dem Gerät vorgenommene manuelle Konfiguration. 

### <a name="to-change-the-instance-for-a-baseline"></a>So ändern Sie die Instanz einer Baseline  

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an. Wählen Sie **Gerätesicherheit** > **Sicherheitsbaselines** und dann die Kachel des Baselinetyps aus, der das zu ändernde Profil enthält.  

2. Wählen Sie anschließend **Profile** aus, und aktivieren Sie dann das Kontrollkästchen des Profils, das Sie bearbeiten möchten. Klicken Sie anschließend auf **Version ändern**.  

   ![Auswählen einer Baseline](./media/security-baselines/select-baseline.png)  

3. Klicken Sie im Bereich **Version ändern** auf das Dropdownmenü **Hiermit wählen Sie eine Sicherheitsbaseline aus, auf die aktualisiert werden soll**, und wählen Sie die gewünschte Versionsinstanz aus.  

   ![Auswählen einer Version](./media/security-baselines/select-instance.png)  
   
4. Klicken Sie auf **Update überprüfen**, um eine CSV-Datei herunterzuladen, die die Unterschiede zwischen der aktuellen Instanzversion des Profils und der von Ihnen ausgewählten neuen Version zeigt. Überprüfen Sie diese Datei, um zu verstehen, welche Einstellungen hinzugefügt oder entfernt wurden bzw. welche Standardwerte für diese Einstellungen im aktualisierten Profil enthalten sind.  

   Wenn Sie fertig sind, fahren Sie mit dem nächsten Schritt fort.  

5. Wählen Sie eine der beiden Optionen für **Methode zum Aktualisieren des Profils auswählen**: 
   - **Baselineänderungen akzeptieren, aber meine vorhandenen Einstellungsanpassungen beibehalten**: Bei Wahl dieser Option werden die Anpassungen, die Sie am Baselineprofil vorgenommen haben, beibehalten und auf die neue Version angewendet, die Sie verwenden möchten.
   - **Baselineänderungen akzeptieren und vorhandene Einstellungsanpassungen verwerfen**: Bei Wahl dieser Option wird Ihr ursprüngliches Profil vollständig überschrieben. Im aktualisierten Profil werden für alle Einstellungen die Standardwerte verwendet.  

6. Klicken Sie auf **Senden**. Das Profil wird auf die ausgewählte Baselineversion aktualisiert. Nach der Konvertierung wird die Baseline zugewiesenen Gruppen sofort wieder bereitgestellt.

## <a name="remove-a-security-baseline-assignment"></a>Aufheben der Zuweisung einer Sicherheitsbaseline
Wenn eine Sicherheitsbaseline-Einstellung nicht mehr für ein Gerät gilt oder die Einstellungen in einer Baseline auf *Nicht konfiguriert* festgelegt sind, werden diese Einstellungen auf einem Gerät nicht auf eine zuvor verwaltete Konfiguration zurückgesetzt. Stattdessen behalten die zuvor verwalteten Einstellungen auf dem Gerät ihre letzten Konfigurationen, wie sie von der Baseline empfangen wurden, bis ein anderer Prozess diese Einstellungen auf dem Gerät aktualisiert.  

Andere Prozesse, die später die Einstellungen auf dem Gerät ggf. ändern, sind eine andere oder neue Sicherheitsbaseline, ein Gerätekonfigurationsprofil, Gruppenrichtlinienkonfigurationen oder die manuelle Bearbeitung der Einstellungen auf dem Gerät.  





## <a name="q--a"></a>Q & A

### <a name="why-these-settings"></a>Warum diese Einstellungen?

Diese Empfehlungen basieren auf der jahrelangen Erfahrung des Microsoft-Sicherheitsteams in der direkten Zusammenarbeit mit Windows-Entwicklern und der Sicherheitscommunity. Die Einstellungen in dieser Baseline werden als die wichtigsten sicherheitsbezogenen Konfigurationsoptionen betrachtet. In jedem neuen Build von Windows passt das Team die Empfehlungen basierend auf neu herausgegebenen Features an.

### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>Gibt es einen Unterschied in den Empfehlungen für die Windows-Sicherheitsbaselines für die Gruppenrichtlinie im Vergleich zu Intune?

Das gleiche Microsoft-Sicherheitsteam hat die Einstellungen für jede Baseline ausgewählt und organisiert. Intune umfasst alle relevanten Einstellungen in der Intune-Sicherheitsbaseline. Es gibt einige Einstellungen in der Gruppenrichtlinienbaseline, die für einen lokalen Domänencontroller spezifisch sind. Diese Einstellungen werden von den Intune-Empfehlungen ausgeschlossen. Alle anderen Einstellungen sind identisch.

### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>Sind die Intune-Sicherheitsbaselines CIS- oder NSIT-kompatibel?

Streng genommen, nicht. Das Microsoft-Sicherheitsteam berät Unternehmen wie CIS, um Empfehlungen zusammenzutragen. Allerdings gibt es keine 1:1-Zuordnung von „CIS-kompatiblen“ und Microsoft-Baselines.

### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Welche Zertifizierungen haben die Sicherheitsbaselines von Microsoft? 

- Microsoft veröffentlicht weiterhin Sicherheitsbaselines für Gruppenrichtlinien (GPOs) und das [Security Compliance Toolkit](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10), wie seit vielen Jahren. Diese Baselines werden von vielen Organisationen verwendet. Die Empfehlungen in diesen Baselines entstammen der Zusammenarbeit des Microsoft-Sicherheitsteams mit Unternehmenskunden und externen Einrichtungen, einschließlich des Department of Defense (DoD, Verteidigungsministerium der USA), National Institute of Standards and Technology (NIST, Nationales Institut für Standards und Technologie) und anderer. Wir teilen unsere Empfehlungen und Baselines mit diesen Organisationen. Diese Organisationen haben auch ihre eigenen Empfehlungen, die die Empfehlungen von Microsoft sehr genau widerspiegeln. Da die mobile Geräteverwaltung (MDM) in der Cloud zunimmt, hat Microsoft entsprechende MDM-Empfehlungen zu diesen Gruppenrichtlinien-Baselines erstellt. Diese zusätzlichen Baselines sind in Microsoft Intune integriert und enthalten Konformitätsberichte zu Benutzern, Gruppen und Geräten, die die Baseline befolgen (oder nicht).

- Viele Kunden nutzen die Intune-Baselineempfehlungen als Ausgangspunkt und passen sie ihren IT- und Sicherheitsanforderungen an. Die **MDM-Sicherheitsbaseline** für Windows 10 RS5 von Microsoft ist die erste Baseline, die freigegeben wird. Diese Baseline wird als allgemeine Infrastruktur erstellt, die Kunden ermöglicht, schließlich andere, auf CIS, NIST und anderen Standards basierende Sicherheitsbaselines zu importieren. Derzeit ist sie für Windows verfügbar und wird schließlich iOS und Android einschließen.

- Das Migrieren von lokalen Active Directory-Gruppenrichtlinien zu einer reinen Cloudlösung mithilfe von Azure Active Directory (AD) mit Microsoft Intune ist eine Reise. Zur Unterstützung sind im [Security Compliance Toolkit](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10) Gruppenrichtlinienvorlagen enthalten, die bei der Verwaltung von in hybrides Active Directory und Azure Active Directory eingebundenen Geräten helfen können. Diese Geräte können MDM-Einstellungen aus der Cloud (Intune) und Gruppenrichtlinieneinstellungen vom lokalen Domänencontroller nach Bedarf abrufen.

## <a name="next-steps"></a>Nächste Schritte
- Prüfen Sie die Einstellungen in den neuesten Versionen der verfügbaren Baselines:  
  - [MDM-Sicherheitsbaseline](security-baseline-settings-mdm.md)  
  - [Microsoft Defender ATP-Baseline](security-baseline-settings-defender-atp.md)  

- Überprüfen Sie den Status, und überwachen Sie [Baseline und Profil](security-baselines-monitor.md).

