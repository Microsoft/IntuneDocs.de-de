---
title: Verwenden von Microsoft Defender ATP in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) in einem End-to-End-Szenario aktivieren, inklusive Aktivieren von Microsoft Defender ATP in Intune und Microsoft Defender Security Center, Integrieren von Geräten über ein Microsoft Defender ATP-Konfigurationsprofil, Erstellen einer Intune-Gerätekompatibilitätsrichtlinie, Erstellen einer Azure AD-Richtlinie für bedingten Zugriff und Überwachen der Gerätekompatibilität.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af27a9b07434346a5425d0539759cb90ebf1ee6f
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68427088"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>Erzwingen der Konformität für Microsoft Defender ATP mit bedingtem Zugriff in Intune  

Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) und Microsoft Intune tragen gemeinsam zum Verhindern von Sicherheitsverletzungen bei und begrenzen die Auswirkungen von Sicherheitsverletzungen innerhalb einer Organisation.

Diese Funktion gilt für: Windows 10-Geräte

Eine Person sendet z.B. eine Word-Anlage mit eingebettetem bösartigem Code an einen Benutzer in Ihrer Organisation. Der Benutzer öffnet die Anlage und aktiviert den Inhalt. Ein Angriff mit erhöhten Rechten beginnt, und ein Angreifer an einem Remotecomputer verfügt über Administratorrechte für das Gerät des Opfers. Der Angreifer greift dann remote auf die anderen Geräte des Benutzers zu.

Diese Sicherheitsverletzung kann sich auf die gesamte Organisation auswirken.

Microsoft Defender ATP kann Sicherheitsereignisse wie dieses Szenario auflösen. Das Microsoft Defender Security Center meldet die Geräte als „hoch riskant“ und fügt einen detaillierten Bericht über verdächtige Aktivitäten bei. In unserem Beispiel erkennt Microsoft Defender ATP, dass das Gerät nicht ordnungsgemäßen Code ausgeführt hat, seine Prozessrechte erhöht wurden, dass es bösartigen Code eingeschleust und eine verdächtige Remoteshell aufgerufen hat. Microsoft Defender ATP bietet Ihnen dann Optionen, das Risiko zu minimieren.

Mit Intune können Sie eine Konformitätsrichtlinie erstellen, die eine akzeptable Risikostufe bestimmt. Wenn ein Gerät dieses Risiko überschreitet, gilt das Gerät nicht mehr als konform. In Kombination mit bedingtem Zugriff für Azure Active Directory (AD) wird dem Benutzer der Zugriff auf Unternehmensressourcen verweigert.

In diesem Artikel erfahren Sie, wie Sie Folgendes durchführen:

- Aktivieren Sie Intune im Microsoft Defender Security Center, und aktivieren Sie Microsoft Defender ATP in Intune. Diese Aufgaben erstellen eine Dienst-zu-Dienst-Verbindung zwischen Intune und Microsoft Defender ATP. Diese Verbindung ermöglicht Microsoft Defender ATP, das Computerrisiko für Ihre Intune-Geräte zu schreiben.
- Erstellen der Konformitätsrichtlinie in Intune.
- Aktivieren Sie in Azure Active Directory (AD) den bedingten Zugriff auf Geräten basierend auf deren Bedrohungsstufe.

## <a name="prerequisites"></a>Voraussetzungen

Um Microsoft Defender ATP mit Intune zu verwenden, stellen Sie sicher, dass Sie Folgendes konfiguriert haben und verwenden können:

- Lizenzierter Mandant für Enterprise Mobility + Security E3 und Windows E5 (oder Microsoft 365 Enterprise E5)
- Microsoft Intune-Umgebung mit [Intune-verwalteten](windows-enroll.md) Windows 10-Geräten, die auch mit Azure AD verknüpft sind
- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) und Zugriff auf das Microsoft Defender Security Center (ATP-Portal)

## <a name="enable-microsoft-defender-atp-in-intune"></a>Aktivieren von Microsoft Defender ATP in Intune

Wenn Sie eine neue Anwendung in Intune Mobile Threat Defense integrieren und die Verbindung aktivieren, erstellt Intune eine klassische Richtlinie für den bedingten Zugriff in Azure Active Directory. Jede MTD-App, die Sie integrieren (z. B. [Defender ATP](advanced-threat-protection.md) oder einer unserer zusätzlichen [MTD-Partner](mobile-threat-defense.md#mobile-threat-defense-partners)), erstellt eine neue klassische Richtlinie für bedingten Zugriff.  Diese Richtlinien können ignoriert werden, dürfen jedoch nicht bearbeitet, gelöscht oder deaktiviert werden.

Klassische bedingte Zugriffsrichtlinien für MTD-Apps: 

- Sie werden von Intune MTD verwendet und verlangen, dass Geräte in Azure AD registriert werden, damit Sie eine Geräte-ID erhalten. Die ID ist erforderlich, damit Geräte ihren Status erfolgreich an Intune melden können.  
- Die Zugriffsrichtlinien unterscheiden sich von Richtlinien für bedingten Zugriff, die Sie möglicherweise erstellen, damit sie Ihnen bei der Verwaltung von MTD helfen.
- Standardmäßig interagieren sie nicht mit anderen Richtlinien für den bedingten Zugriff, die Sie für die Auswertung verwenden.  

Wenn Sie klassische Richtlinien für den bedingten Zugriff in [Azure](https://portal.azure.com/#home) anzeigen möchten, wechseln Sie zu **Azure Active Directory** > **Bedingter Zugriff** > **Klassische Richtlinien**.

### <a name="to-enable-defender-atp"></a>Aktivieren von Defender ATP
1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie **Gerätekompatibilität** > **Microsoft Defender ATP** und dann unter *Connectoreinstellungen* die Option **Microsoft Defender Security Center öffnen** aus.

    ![Wählen Sie die Option zum Öffnen von Microsoft Defender Security Center aus.](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. In **Microsoft Defender Security Center**:
    1. Wählen Sie **Einstellungen** > **Erweiterte Features** aus.
    2. Wählen Sie für **Microsoft Intune-Verbindung** die Option **Ein** aus:

        ![Aktivieren der Verbindung mit Intune](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. Wählen Sie **Voreinstellungen speichern** aus.

4. Gehen Sie zurück zu Intune, **Gerätekompatibilität** > **Microsoft Defender ATP**. Legen Sie **Windows-Geräte der Version 10.0.15063 und höher mit "Microsoft Defender ATP" verbinden** auf **Ein** fest.
5. Wählen Sie **Speichern** aus.

Sie führen diese Aufgabe in der Regel einmal aus. Wenn also Microsoft Defender ATP bereits in Ihrer Intune-Ressource aktiviert ist, müssen Sie es nicht erneut tun.

## <a name="onboard-devices-using-a-configuration-profile"></a>Integrieren von Geräten mithilfe eines Konfigurationsprofils

Wenn sich ein Endbenutzer bei Intune registriert, können Sie unterschiedliche Einstellungen mithilfe von Push an Geräte mit Konfigurationsprofil übertragen. Das gilt auch für Microsoft Defender ATP.

Microsoft Defender ATP enthält ein integriertes Konfigurationspaket, das mit [ATP-Diensten](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) kommuniziert, um Dateien zu überprüfen, Bedrohungen zu erkennen und das Risiko an Microsoft Defender ATP zu melden.

Wenn Sie eine Integration durchführen, ruft Intune ein automatisch generiertes Konfigurationspaket von Microsoft Defender ATP ab. Intune überträgt beim Senden des Konfigurationsprofils an das Gerät das Konfigurationspaket mithilfe von Push an das Gerät, sodass Microsoft Defender ATP das Gerät auf Bedrohungen überwachen kann.

Sobald sie ein Gerät über das Konfigurationspaket integrieren, müssen Sie dies nicht erneut tun. Sie können Geräte auch mit einer [Gruppenrichtlinie oder System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) integrieren.

### <a name="create-the-configuration-profile"></a>Erstellen des Konfigurationsprofils

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie einen **Namen** und eine **Beschreibung** ein.
4. Wählen Sie unter **Plattform** die Option **Windows 10 und höher** aus.
5. Wählen Sie für **Profiltyp** die Option **Microsoft Defender ATP (Windows 10 Desktop)** aus.
6. Konfigurieren Sie die Einstellungen:

    - **Pakettyp für die Microsoft Defender ATP-Clientkonfiguration**: Wählen Sie **Onboarding** aus, um das Konfigurationspaket zum Profil hinzuzufügen. Klicken Sie auf **Offboard** (Integration aufheben), um das Konfigurationspaket aus dem Profil zu entfernen.
  
    > [!NOTE]  
    > Wenn Sie eine ordnungsgemäße Verbindung mit Microsoft Defender ATP hergestellt haben, führt Intune automatisch ein **Onboarding** für das Konfigurationsprofil für Sie durch, und die Einstellung **Pakettyp für die Microsoft Defender ATP-Clientkonfiguration** ist nicht verfügbar.
  
    - **Beispielfreigabe für alle Dateien**: Durch das **Aktivieren** dieser Option werden Stichproben erfasst und mit Microsoft Defender ATP geteilt. Wenn Sie z. B. eine verdächtige Datei sehen, können Sie sie zur gründlichen Analyse an Microsoft Defender ATP senden. Wenn **Nicht konfiguriert** festgelegt ist, werden keine Stichproben mit Microsoft Defender ATP geteilt.
    - **Häufigkeit von Telemetrieberichten erhöhen**: Bei Geräten mit hohem Risiko werden durch das **Aktivieren** dieser Option häufiger Telemetriedaten an den Microsoft Defender ATP-Dienst gemeldet.

    [Integrierte Windows 10-Computer mit System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm) enthält nähere Informationen zu diesen Microsoft Defender ATP-Einstellungen.

7. Wählen Sie **OK** und **Erstellen** aus, um Ihre Änderungen zu speichern, die das Profil erstellt.

## <a name="create-the-compliance-policy"></a>Erstellen der Konformitätsrichtlinie
Die Konformitätsrichtlinie legt eine akzeptable Risikostufe für ein Gerät fest.

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** aus.
3. Geben Sie einen **Namen** und eine **Beschreibung** ein.
4. Wählen Sie unter **Plattform** die Option **Windows 10 und höher** aus.
5. Legen Sie in den Einstellungen für **Microsoft Defender ATP** für **Anfordern, dass das Gerät höchstens das angegebene Computerrisiko aufweist** die bevorzugte Stufe fest. Bedrohungsstufenklassifizierungen werden [von Microsoft Defender ATP bestimmt](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue).

   - **Löschen**: Diese Stufe ist die sicherste Einstellung. Solange auf einem Gerät Bedrohungen vorhanden sind, ist kein Zugriff auf Unternehmensressourcen möglich. Wenn Bedrohungen gefunden werden, wird das Gerät als nicht kompatibel bewertet. (Microsoft Defender ATP verwendet den Wert *Sicher*.)
   - **Niedrig:** Das Gerät ist konform, wenn nur Bedrohungen auf niedriger Stufe vorliegen. Geräte mit mittleren oder hohen Bedrohungsstufen sind nicht konform.
   - **Mittel:** Das Gerät ist konform, wenn auf dem Gerät Bedrohungen niedriger oder mittlerer Stufe gefunden werden. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht kompatibel bewertet.
   - **Hoch**: Dies ist die unsicherste Stufe, die alle Bedrohungsstufen zulässt. Also werden Geräte mit hohen, mittleren oder niedrigen Bedrohungsstufen als konform angesehen.

6. Wählen Sie **OK** und **Erstellen** aus, um Ihre Änderungen zu speichern (und die Richtlinie zu erstellen).

## <a name="assign-the-policy"></a>Zuweisen der Richtlinie

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie **Gerätekompatibilität** > **Richtlinien** und Ihre Microsoft Defender ATP-Konformitätsrichtlinie aus.
3. Wählen Sie **Zuweisungen** aus.
4. Schließen Sie Ihre Azure AD-Gruppen ein- oder aus, um ihnen die Richtlinie zuzuweisen.
5. Wählen Sie zum Bereitstellen der Richtlinie für die Gruppen **Speichern** aus. Die Benutzergeräte, denen die Richtlinie zugewiesen wurde, werden auf Konformität überprüft.

## <a name="create-a-conditional-access-policy"></a>Erstellen einer Richtlinie für bedingten Zugriff
Die Richtlinie für bedingten Zugriff blockiert den Zugriff auf Ressourcen, *wenn* das Gerät nicht konform ist. Wenn also ein Gerät die Bedrohungsstufe überschreitet, können Sie den Zugriff auf Unternehmensressourcen wie SharePoint oder Exchange Online blockieren.  

> [!TIP]  
> Der bedingte Zugriff ist eine Technologie von Azure Active Directory (Azure AD). Bei dem Knoten für bedingten Zugriff, auf den aus *Intune* zugegriffen wird, handelt es sich um denselben Knoten, auf den aus *Azure AD* zugegriffen wird.  

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an, und wählen Sie **Bedingter Zugriff** > **Neue Richtlinie** aus.
2. Geben Sie einen **Namen** für die Richtlinie ein, und wählen Sie **Benutzer und Gruppen** aus. Fügen Sie mit den Optionen „Einschließen“ oder „Ausschließen“ Ihre Gruppen für die Richtlinie hinzu, und wählen Sie **Fertig** aus.
3. Wählen Sie **Cloud-Apps** und die zu schützenden Apps aus. Wählen Sie z.B. **Apps auswählen** und **Office 365 SharePoint Online** sowie **Office 365 Exchange Online** aus.

    Wählen Sie **Fertig** aus, um die Änderungen zu speichern.

4. Wählen Sie **Bedingungen** > **Client-Apps** aus, um die Richtlinie auf Apps und Browser anzuwenden. Wählen Sie z.B. **Ja** aus, und aktivieren Sie dann **Browser** sowie **Mobile Apps und Desktopclients**.

    Wählen Sie **Fertig** aus, um die Änderungen zu speichern.

5. Wählen Sie **Gewähren** aus, um den bedingten Zugriff basierend auf der Gerätekonformität anzuwenden. Wählen Sie z.B. **Zugriff gewähren** > **Markieren des Geräts als kompatibel erforderlich** aus.

    Wählen Sie **OK** aus, um die Änderungen zu speichern.

6. Wählen Sie **Richtlinie aktivieren** und dann **Erstellen** zum Speichern der Änderungen aus.

[Was ist bedingter Zugriff?](conditional-access.md) ist eine gute Ressource.

## <a name="monitor-device-compliance"></a>Überwachen der Gerätekonformität
Überwachen Sie als Nächstes den Status von Geräten, auf die die Microsoft Defender ATP-Konformitätsrichtlinie angewandt wird.

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
2. Wählen Sie **Gerätekompatibilität** > **Richtlinienkompatibilität** aus.
3. Suchen Sie Ihre Microsoft Defender ATP-Richtlinie in der Liste, und sehen Sie, welche Geräte konform bzw. nicht konform sind.

## <a name="more-good-stuff"></a>Weitere gute Tipps
[Microsoft Defender ATP – bedingter Zugriff](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)  
[Microsoft Defender ATP – Risikodashboard](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)  

[Erste Schritte mit den Gerätekonformitätsrichtlinien in Intune](device-compliance-get-started.md)  
[Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)