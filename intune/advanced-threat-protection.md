---
title: Verwenden von Windows Defender ATP in Microsoft Intune – Azure | Microsoft-Dokumentation
description: In einem End-to-End-Szenario erfahren Sie, wie Sie Windows Defender Advanced Threat Protection (ATP) aktivieren, inklusive Einschalten von ATP in Intune und Windows Defender Security Center (ATP-Portal), Integrieren von Geräten mit einem ATP-Konfigurationsprofil, Erstellen einer Intune-Gerätekonformitätsrichtlinie, Erstellen einer Azure AD-Richtlinie für bedingten Zugriff und Überwachen der Gerätekonformität.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2e99ed0bd1eb5bae90913aedba5973e5e1282f70
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2018
---
# <a name="enable-windows-defender-atp-with-conditional-access-in-intune"></a>Aktivieren von Windows Defender ATP mit bedingtem Zugriff in Intune

Windows Defender Advanced Threat Protection (ATP) und Microsoft Intune tragen gemeinsam zum Verhindern von Sicherheitsverletzungen bei und begrenzen die Auswirkungen von Sicherheitsverletzungen innerhalb einer Organisation.

Dieses Feature ist für Windows 10-Geräte gültig.

Eine Person sendet z.B. eine Word-Anlage mit eingebettetem bösartigem Code an einen Benutzer in Ihrer Organisation. Der Benutzer öffnet die Anlage und aktiviert den Inhalt. Ein Angriff mit erhöhten Rechten beginnt, und ein Angreifer an einem Remotecomputer verfügt über Administratorrechte für das Gerät des Opfers. Der Angreifer greift dann remote auf die anderen Geräte des Benutzers zu.

Diese Sicherheitsverletzung kann sich auf die gesamte Organisation auswirken.

Windows Defender ATP kann Sicherheitsereignisse wie dieses Szenario auflösen. Das Windows Defender Security Center (ATP-Konsole) meldet die Geräte als „hoch riskant“ und fügt einen detaillierten Bericht über verdächtige Aktivitäten bei. In unserem Beispiel erkennt Windows Defender ATP, dass das Gerät nicht ordnungsgemäßen Code ausgeführt hat, seine Prozessrechte erhöht wurden, dass es bösartigen Code eingeschleust und eine verdächtige Remoteshell aufgerufen hat. Windows Defender ATP bietet Ihnen dann Optionen, das Risiko zu minimieren.

Mit Intune können Sie eine Konformitätsrichtlinie erstellen, die eine akzeptable Risikostufe bestimmt. Wenn ein Gerät dieses Risiko überschreitet, gilt das Gerät nicht mehr als konform. In Kombination mit bedingtem Zugriff für Azure Active Directory (AD) wird dem Benutzer der Zugriff auf Unternehmensressourcen verweigert.

In diesem Artikel erfahren Sie, wie Sie Folgendes durchführen:

- Aktivieren von Intune in ATP und Aktivieren von ATP in Intune. Diese Aufgaben erstellen eine Dienst-zu-Dienst-Verbindung zwischen Intune und Windows Defender ATP. Diese Verbindung ermöglicht Windows Defender ATP, das Computerrisiko für Ihre Intune-Geräte zu schreiben.
- Erstellen der Konformitätsrichtlinie in Intune.
- Aktivieren Sie in Azure Active Directory (AD) bedingten Zugriff auf Geräte basierend auf deren Bedrohungsstufe.

## <a name="prerequisites"></a>Voraussetzungen

Um ATP mit Intune zu verwenden, stellen Sie sicher, dass Sie Folgendes konfiguriert haben und verwenden können:

- Lizenzierter Mandant für Enterprise Mobility + Security E5 und Windows E5 (oder Microsoft 365 Enterprise E5)
- Microsoft Intune-Umgebung mit [Intune-verwalteten](windows-enroll.md) Windows 10-Geräten, die auch mit Azure AD verknüpft sind
- [Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) und Zugriff auf das Windows Defender Security Center (ATP-Portal)

## <a name="enable-windows-defender-atp-in-intune"></a>Aktivieren von Windows Defender ATP in Intune

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste**, filtern Sie nach **Intune**, und klicken Sie dann auf **Microsoft Intune**.
3. Wählen Sie **Gerätekonformität** > **Windows Defender ATP** > **Verwaltungskonsole von Windows Defender Advanced Threat Protection öffnen**.

    ![Alternativer Text](./media/atp-device-compliance-open-windows-defender.png)

4. In **Windows Defender Security Center**:
    1. Wählen Sie **Einstellungen** > **Erweiterte Features** aus.
    2. Wählen Sie für **Microsoft Intune-Verbindung** die Option **Ein** aus:

        ![Alternativer Text](./media/atp-security-center-intune-toggle.png)

    3. Wählen Sie **Voreinstellungen speichern** aus.

5. Gehen Sie zurück zu Intune, **Gerätekonformität** > **Windows Defender ATP**. Setzen Sie **10.0.15063+-Geräte mit Windows Defender Advanced Threat Protection verbinden** auf **Ein**.
6. Wählen Sie **Speichern** aus.

Sie führen diese Aufgabe in der Regel einmal aus. Wenn also ATP bereits in Ihrer Intune-Ressource aktiviert ist, müssen Sie es nicht erneut tun.

## <a name="onboard-devices-using-a-configuration-profile"></a>Integrieren von Geräten mithilfe eines Konfigurationsprofils

Windows Defender enthält ein integriertes Konfigurationspaket, das auf Geräten installiert ist. Bei der Installation kommuniziert das Paket mit [Windows Defender ATP-Diensten](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection), um Dateien zu überprüfen, Bedrohungen zu erkennen und das Risiko an Windows Defender ATP zu melden. MIt Intune können Sie ein Konfigurationsprofil erstellen, das dieses Konfigurationspaket verwendet. Weisen Sie dieses Profils anschließend Geräten zu, die Sie zum ersten Mal integrieren.

Sobald sie ein Gerät über das Konfigurationspaket integrieren, müssen Sie dies nicht erneut tun. Dies ist in der Regel eine einmalige Aufgabe.

Sie können Geräte auch mit einer [Gruppenrichtlinie oder System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-windows-defender-advanced-threat-protection) integrieren.

Im Folgenden lernen Sie die Schritte zum Integrieren mit Intune kennen.

#### <a name="download-configuration-package"></a>Herunterladen des Konfigurationspakets

1. Wählen Sie im [Windows Defender Security Center](https://securitycenter.windows.com) die Option **Einstellungen** > **Onboarding** aus.
2. Legen Sie folgende Einstellungen fest:
  - **Betriebssystem**: Windows 10
  - **Computer integrieren** > **Bereitstellungsmethode**: Verwaltung mobiler Geräte / Microsoft Intune
3. Wählen Sie **Paket herunterladen** aus, und speichern Sie die Datei **WindowsDefenderATPOnboardingPackage.zip**. Extrahieren Sie die Datei.

Diese Zip-Datei enthält **WindowsDefenderATP.onboarding**, die Sie in den nächsten Schritten benötigen.

#### <a name="create-the-atp-configuration-profile"></a>Erstellen des ATP-Konfigurationsprofils

Dieses Profil verwendet das Onboardingpaket, das Sie in den vorherigen Schritten heruntergeladen haben.

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**.
3. Geben Sie einen **Namen** und eine **Beschreibung** ein.
4. Wählen Sie unter **Plattform** die Option **Windows 10 und höher** aus.
5. Wählen Sie für **Profiltyp** die Option **Windows Defender ATP (Windows 10 Desktop)** aus.
6. Konfigurieren Sie die Einstellungen:

  - **Onboarding für Konfigurationspaket durchführen**: Suchen Sie die Datei **WindowsDefenderATP.onboarding**, die Sie heruntergeladen haben, und wählen Sie sie aus. Diese Datei ermöglicht eine Einstellung, mit der Geräte Meldungen an den Windows Defender ATP-Dienst senden können.
  - **Beispielfreigabe für alle Dateien**: Ermöglicht das Sammeln von Beispielen und deren Freigabe mit Windows Defender ATP. Wenn Sie z.B. eine verdächtige Datei sehen, können Sie sie zur gründlichen Analyse an Windows Defender ATP senden.
  - **Häufigkeit von Telemetrieberichten erhöhen**: Aktivieren Sie diese Einstellung für Geräte mit hohem Risiko, damit sie häufiger Telemetriedaten an den Windows Defender ATP-Dienst melden.
  - **Offboarding für Konfigurationspaket durchführen**: Wenn Sie die Windows Defender ATP-Überwachung entfernen oder „auslagern“ möchten, können Sie ein Auslagerungspaket in [Windows Defender Security Center](https://securitycenter.windows.com) herunterladen und es hinzufügen. Überspringen Sie andernfalls diese Eigenschaft.

    [Konfigurieren von Endpunkten mithilfe von System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-sccm-windows-defender-advanced-threat-protection) enthält nähere Informationen zu diesen Windows Defender ATP-Einstellungen.

7. Wählen Sie **OK** und **Erstellen** aus, um Ihre Änderungen zu speichern, die das Profil erstellt.

## <a name="create-the-compliance-policy"></a>Erstellen der Konformitätsrichtlinie
Die Konformitätsrichtlinie legt eine akzeptable Risikostufe für ein Gerät fest.

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Wählen Sie **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** aus.
3. Geben Sie einen **Namen** und eine **Beschreibung** ein.
4. Wählen Sie unter **Plattform** die Option **Windows 10 und höher** aus.
5. Legen Sie in den Einstellungen für **Geräteintegrität** für **Anfordern, dass das Gerät höchstens der angegebenen Gerätebedrohungsstufe entspricht** die bevorzugte Stufe fest:

  - **Geschützt**: Diese Stufe ist die sicherste Einstellung. Solange auf einem Gerät Bedrohungen vorhanden sind, ist kein Zugriff auf Unternehmensressourcen möglich. Wenn Bedrohungen gefunden werden, wird das Gerät als nicht kompatibel bewertet.
  - **Niedrig**: Das Gerät ist konform, wenn nur Bedrohungen auf niedriger Stufe vorliegen. Geräte mit mittleren oder hohen Bedrohungsstufen sind nicht konform.
  - **Mittel**: Das Gerät ist konform, wenn auf dem Gerät Bedrohungen niedriger oder mittlerer Stufe gefunden werden. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht kompatibel bewertet.
  - **Hoch**: Dies ist die unsicherste Stufe, die alle Bedrohungsstufen zulässt. Also werden Geräte mit hohen, mittleren oder niedrigen Bedrohungsstufen als konform angesehen.

6. Wählen Sie **OK** und **Erstellen** aus, um Ihre Änderungen zu speichern (und die Richtlinie zu erstellen).

## <a name="assign-the-policy"></a>Zuweisen der Richtlinie

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Wählen Sie **Gerätekonformität** > **Richtlinien** und Ihre Windows Defender ATP-Konformitätsrichtlinie aus.
3. Wählen Sie **Zuweisungen** aus.
4. Schließen Sie Ihre Azure AD-Gruppen ein- oder aus, um ihnen die Richtlinie zuzuweisen.
5. Wählen Sie zum Bereitstellen der Richtlinie für die Gruppen **Speichern** aus. Die Benutzergeräte, denen die Richtlinie zugewiesen wurde, werden auf Konformität überprüft.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Erstellen einer Azure AD-Richtlinie für bedingten Zugriff
Die Richtlinie für bedingten Zugriff blockiert den Zugriff auf Ressourcen, *wenn* das Gerät nicht konform ist. Wenn also ein Gerät die Bedrohungsstufe überschreitet, können Sie den Zugriff auf Unternehmensressourcen wie SharePoint oder Exchange Online blockieren.

1. Öffnen Sie im [Azure-Portal](https://portal.azure.com) die Option **Azure Active Directory** > **Bedingter Zugriff** > **Neue Richtlinie**.
2. Geben Sie einen **Namen** für die Richtlinie ein, und wählen Sie **Benutzer und Gruppen** aus. Fügen Sie mit den Optionen „Einschließen“ oder „Ausschließen“ Ihre Gruppen für die Richtlinie hinzu, und wählen Sie **Fertig** aus.
3. Wählen Sie **Cloud-Apps** und die zu schützenden Apps aus. Wählen Sie z.B. **Apps auswählen** und **Office 365 SharePoint Online** sowie **Office 365 Exchange Online** aus.

    Wählen Sie **Fertig** aus, um die Änderungen zu speichern.

4. Wählen Sie **Bedingungen** > **Client-Apps** aus, um die Richtlinie auf Apps und Browser anzuwenden. Wählen Sie z.B. **Ja** aus, und aktivieren Sie dann **Browser** sowie **Mobile Apps und Desktopclients**.

    Wählen Sie **Fertig** aus, um die Änderungen zu speichern.

5. Wählen Sie **Gewähren** aus, um bedingten Zugriff basierend auf Gerätekonformität anzuwenden. Wählen Sie z.B. **Zugriff gewähren** > **Markieren des Geräts als kompatibel erforderlich** aus.

    Wählen Sie **OK** aus, um die Änderungen zu speichern.

6. Wählen Sie **Richtlinie aktivieren** und dann **Erstellen** zum Speichern der Änderungen aus.

[Was ist bedingter Zugriff?](conditional-access.md) ist eine gute Ressource.

## <a name="monitor-device-compliance"></a>Überwachen der Gerätekonformität
Überwachen Sie als Nächstes den Status von Geräten, auf die die Windows Defender ATP-Konformitätsrichtlinie angewandt wird.

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie dann **Microsoft Intune** aus.
2. Wählen Sie **Gerätekompatibilität** > **Richtlinienkompatibilität** aus.
3. Suchen Sie Ihre Windows Defender ATP-Richtlinie in der Liste, und sehen Sie, welche Geräte konform bzw. nicht konform sind.

## <a name="more-good-stuff"></a>Weitere gute Tipps
[Windows Defender ATP – bedingter Zugriff](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/conditional-access-windows-defender-advanced-threat-protection)  
[Windows Defender ATP – Risikodashboard](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection)  
[Erste Schritte mit den Gerätekonformitätsrichtlinien in Intune](device-compliance-get-started.md)  
[Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)