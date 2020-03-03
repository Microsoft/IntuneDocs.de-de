---
title: Behandeln von Problemen und Überprüfen von WLAN-Geräteprofilprotokollen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verstehen und beheben Sie Probleme mit WLAN-Gerätekonfigurationsprofilen auf Android-, iOS-/iPadOS- und Windows-Geräten in Microsoft Intune. Überprüfen Sie Protokolle, und sehen Sie sich einige häufige Probleme und mögliche Lösungen an.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: db663f96f1e4fe84c506395b98c52956069e5426
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512822"
---
# <a name="troubleshoot-wi-fi-device-configuration-profiles-in-microsoft-intune"></a>Behandeln von Problemen mit Gerätekonfigurationsprofilen in Microsoft Intune

In Intune können Sie Gerätekonfigurationsprofile erstellen, die Verbindungseinstellungen für Ihr WLAN-Netzwerk enthalten. Verwenden Sie diese Einstellungen, um die Android-, iOS-/iPadOS- und Windows-Geräte der Benutzer mit Ihrem Organisationsnetzwerk zu verbinden.

In diesem Artikel wird gezeigt, wie ein WLAN-Profil bei der erfolgreichen Anwendung auf Geräte aussieht. Er enthält auch Protokollinformationen, häufige Probleme und vieles mehr. Verwenden Sie diesen Artikel, um die Problembehandlung für Ihre WLAN-Profile zu unterstützen.

Weitere Informationen zu WLAN-Profilen in Intune finden Sie unter [Hinzufügen und Verwenden von WLAN-Einstellungen auf Ihren Geräten](wi-fi-settings-configure.md).

## <a name="before-you-begin"></a>Vorbereitung

In den Beispielen in diesem Artikel wird die SCEP-Zertifikatauthentifizierung für die Intune-Profile verwendet. Außerdem wird davon ausgegangen, dass die vertrauenswürdigen Stamm- und SCEP-Profile auf dem Gerät ordnungsgemäß funktionieren.

## <a name="android"></a>Android

In diesem Abschnitt durchlaufen wir die Endbenutzererfahrung bei der Installation der Konfigurationsprofile auf einem Android-Gerät.

### <a name="end-user-experience-example"></a>Beispiel für die Endbenutzererfahrung

In diesem Szenario wird ein Nokia 6.1-Gerät verwendet. Installieren Sie die vertrauenswürdigen Stamm- und SCEP-Profile, bevor das WLAN-Profil auf dem Gerät installiert wird.

1. Endbenutzer erhalten eine Benachrichtigung zum Installieren des vertrauenswürdigen Stammzertifikatprofils:

    > [!div class="mx-imgBorder"]
    > ![Beispielbenachrichtigung einer Unternehmensportal-App unter Android zum Installieren des vertrauenswürdigen Stammzertifikatprofils](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-trusted-root.png)

2. Bei der nächsten Benachrichtigung werden Sie aufgefordert, das SCEP-Zertifikatprofil zu installieren:

    > [!div class="mx-imgBorder"]
    > ![Beispielbenachrichtigung einer Unternehmensportal-App unter Android zum Installieren des SCEP-Zertifikatprofils](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-scep-certificate.png)

    > [!TIP]
    > Wenn Sie ein vom Geräteadministrator verwaltetes Android-Gerät verwenden, werden möglicherweise mehrere Zertifikate aufgelistet. Wenn ein Zertifikatprofil widerrufen oder entfernt wird, bleibt das Zertifikat auf dem Gerät. Wählen Sie in diesem Szenario das neueste Zertifikat aus. Dies ist normalerweise das letzte Zertifikat, das in der Liste angezeigt wird.
    >
    > Diese Situation tritt nicht auf Android Enterprise- und Samsung Knox-Geräten auf. Weitere Informationen finden Sie unter [Verwalten von Android-Arbeitsprofilgeräten](../enrollment/android-enterprise-overview.md) und [Entfernen von SCEP- und PKCS-Zertifikaten](../protect/remove-certificates.md#android-knox-devices).

3. Anschließend erhalten Benutzer eine Benachrichtigung zum Installieren des WLAN-Profils:

    > [!div class="mx-imgBorder"]
    > ![Beispielbenachrichtigung einer Unternehmensportal-App unter Android zum Installieren des SCEP-Zertifikatprofils](./media/troubleshoot-wi-fi-profiles/android-end-user-install-wifi-profile.png)

4. Nach Abschluss des Vorgangs wird die WLAN-Verbindung als gespeichertes Netzwerk angezeigt:

    > [!div class="mx-imgBorder"]
    > ![Anzeigen der WLAN-Verbindung als gespeichertes Netzwerk](./media/troubleshoot-wi-fi-profiles/android-end-user-saved-networks.png)

### <a name="review-company-portal-app-logs"></a>Bewertung von Protokollen der Unternehmensportal-App

Unter Android werden in der Datei **Omadmlog.log** die Aktivitäten des WLAN-Profils ausführlich erläutert, wenn es auf dem Gerät installiert ist. Möglicherweise hat es bis zu fünf Omadmlog-Protokolldateien. Stellen Sie sicher, dass Sie den Zeitstempel der letzten Synchronisierung erhalten, da dieser Ihnen dabei hilft, die zugehörigen Protokolleinträge zu finden.

Verwenden Sie im folgenden Beispiel [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace), um die Protokolle zu lesen, und suchen Sie nach „wifimgr“:

> [!div class="mx-imgBorder"]
> ![Anzeigen der WLAN-Verbindung als gespeichertes Netzwerk](./media/troubleshoot-wi-fi-profiles/android-cmtrace-filter-wifimgr.png)

Im folgenden Protokoll werden die Suchergebnisse und die erfolgreiche Anwendung des WLAN-Profils angezeigt:

```log
2019-08-01T19:22:46.7340000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.7490000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:46.8100000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:46.8209999    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.8240000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected ca certificate with alias: 'user:205xxxxx.0' and thumbprint '<thumbprint>'.
2019-08-01T19:22:47.0990000    VERB    com.microsoft.omadm.platforms.android.certmgr.CertificateChainBuilder    15118    04142    Complete certificate chain built with Complete certs.
2019-08-01T19:22:47.1010000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    1 cert(s) matched criteria: User<ID>[i:<ID>,17CECEA1D337FAA7D167AD83A8CC7A8FCBF9xxxx;eku:1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2]
2019-08-01T19:22:47.1090000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    0 cert(s) excluded by criteria:
2019-08-01T19:22:47.1110000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected client cert with alias 'User<ID>' and requestId 'ModelName=<ModelName>%2FLogicalName_<LogicalName>;Hash=-912418295'.
2019-08-01T19:22:47.4120000    VERB    com.microsoft.omadm.Services    15118    04142    Successfully applied, enabled and saved wifi profile '<profile ID>'
2019-08-01T19:22:47.4240000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.4910000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.4970000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5080000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.5820000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.5900000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5910000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04142    Applied profile <profile ID>

```

## <a name="iosipados"></a>iOS/iPadOS

Nachdem das WLAN-Profil auf dem Gerät installiert wurde, wird es im **Verwaltungsprofil** angezeigt:

> [!div class="mx-imgBorder"]
> ![Verwaltungsprofil auf einem iOS-/iPadOS-Gerät in Intune](./media/troubleshoot-wi-fi-profiles/ios-management-profile.png)

> [!div class="mx-imgBorder"]
> ![Anzeigen der WLAN-Verbindung als WLAN-Netzwerk in Intune auf einem iOS-/iPadOS-Gerät](./media/troubleshoot-wi-fi-profiles/ios-wifi-connection-in-management-profile.png)

### <a name="review-the-iosipados-console-and-device-logs"></a>Überprüfen der iOS-/iPadOS-Konsole und der Geräteprotokolle

Auf iOS-/iPadOS-Geräten enthält das Protokoll der Unternehmensportal-App keine Informationen zu WLAN-Profilen. Verwenden Sie zum Anzeigen der Installationsdetails für Ihre WLAN-Profile die Konsolen-/Geräteprotokolle:

1. Verbinden Sie das iOS-/iPadOS-Gerät mit Mac. Gehen Sie zu **Anwendungen** > **Dienstprogramme**, und öffnen Sie die Konsolen-App.
2. Wählen Sie unter **Aktion** die Option **Include Info Messages** (Informationsmeldungen einschließen) und **Include Debug Messages** (Debugmeldungen einschließen) aus:

    > [!div class="mx-imgBorder"]
    > ![„Include Info Messages“ (Informationsmeldungen einschließen) und „Include Debug Messages“ (Debugmeldungen einschließen) in der iOS-/iPadOS-Konsolen-App](./media/troubleshoot-wi-fi-profiles/ios-console-app-include-info-messages-debug-messages.png)

3. Reproduzieren Sie das Szenario, und speichern Sie die Protokolle in einer Textdatei:

    1. Wählen Sie alle Nachrichten auf dem aktuellen Bildschirm aus: **Bearbeiten** > **Alle auswählen**.
    2. Kopieren Sie die Nachrichten: **Bearbeiten** > **Kopieren**.
    3. Fügen Sie die Protokolldaten in einen Text-Editor ein, und speichern Sie die Datei.

4. Durchsuchen Sie die gespeicherte Protokolldatei, um ausführliche Informationen anzuzeigen. Wenn das Profil erfolgreich installiert wurde, sieht die Ausgabe in etwa wie im folgenden Protokoll aus:

    ```log
    Line 390870: debug    11:19:58.994815 -0400    profiled    Adding dependent www.windowsintune.com.wifi.Contoso to parent Microsoft.Profiles.MDM in domain ManagingProfileToManagedProfile to system\
    Line 390872: debug    11:19:58.995210 -0400    profiled    Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.wifi.Contoso in domain ManagedProfileToManagingProfile to system\
    Line 392346: default    11:19:59.360460 -0400    profiled    Profile \'93www.windowsintune.com.wifi.Contoso\'94 installed.\
    ```

## <a name="windows"></a>Windows

Wenn das WLAN-Profil installiert ist, navigieren Sie auf dem Gerät zu **Einstellungen** > **Konten** > **Zugriff auf Geschäft, Schule oder Uni**. Wählen Sie Ihr Konto > **Info** aus:

> [!div class="mx-imgBorder"]
> ![„Zugriff auf Geschäft, Schule oder Uni“ und Auswählen von „Info“ auf einem Windows-Gerät](./media/troubleshoot-wi-fi-profiles/windows-access-work-school-info.png)

In **Areas managed by Microsoft** (Von Microsoft verwaltete Bereiche) wird **WLAN** angezeigt:

> [!div class="mx-imgBorder"]
> ![Der Punkt „WLAN“ in von Microsoft verwalteten Bereichen unter Windows](./media/troubleshoot-wi-fi-profiles/windows-wifi-areas-managed-by-microsoft.png)

Wechseln Sie zu **Einstellungen** > **Netzwerk und Internet**  > **WLAN**:

> [!div class="mx-imgBorder"]
> ![Die auf Windows angezeigte WLAN-Verbindung als bekanntes Netzwerk in den Einstellungen](./media/troubleshoot-wi-fi-profiles/windows-wifi-connection-known-networks.png)

### <a name="review-event-viewer-logs"></a>Überprüfen von Protokollen der Ereignisanzeige

Auf Windows-Geräten werden die Details zu WLAN-Profilen in der Ereignisanzeige protokolliert:

1. Öffnen Sie die **Ereignisanzeige**-App.
2. Wählen Sie im Menü **Ansicht** die Option **Analytische und Debugprotokolle einblenden** aus.
3. Erweitern Sie **Anwendungs- und Dienstprotokolle** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin**

Die Ausgabe sollte in etwa wie die folgenden Protokolle aussehen:

```log
Log Name:      Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
Source:        Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider
Date:          8/7/2019 8:01:41 PM
Event ID:      1506
Task Category: (1)
Level:         Information
Keywords:      (2)
User:          SYSTEM
Computer:      <Computer Name>
Description:
WiFiConfigurationServiceProvider: Node set value, type: (0x4), Result: (The operation completed successfully.).
```

## <a name="common-issues"></a>Häufige Probleme

### <a name="issue-1-the-wi-fi-profile-isnt-deployed-to-the-device"></a>Problem 1: Das WLAN-Profil wird nicht auf dem Gerät bereitgestellt

- Vergewissern Sie sich, dass das WLAN-Profil der richtigen Gruppe zugewiesen wurde:

    1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräte** > **Konfigurationsprofile** aus.
    2. Wählen Sie Ihr Profil und **Zuweisungen** aus. Vergewissern Sie sich, dass die ausgewählten Gruppen stimmen.
    3. Wählen Sie in Endpoint Manager **Problembehandlung + Support** aus. Überprüfen Sie die Information **Zuweisungen**.

- Wählen Sie in Endpoint Manager **Problembehandlung + Support** aus. Vergewissern Sie sich, dass das Gerät mit Intune synchronisiert werden kann, indem Sie die Zeit der **letzten Anmeldung** überprüfen.

- Wenn das WLAN-Profil mit den vertrauenswürdigen Stamm- und SCEP-Profilen verknüpft ist, vergewissern Sie sich, dass beide Profile auf dem Gerät bereitgestellt werden. Das WLAN-Profil ist von diesen Profilen abhängig.

- Überprüfen Sie auf Windows 10 und neueren Geräten das MDM-Diagnoseinformationenprotokoll:

  1. Navigieren Sie zu **Einstellungen** > **Konten** > **Access work or school** (Zugriff auf Geschäfts-, Schul- oder Unikonto).
  2. Wählen Sie Ihr Geschäfts-, Schul- oder Unikonto > **Info** aus.
  3. Wählen Sie unten auf der Seite **Einstellungen** die Option **Bericht erstellen** aus.
  4. Ein Fenster wird geöffnet, in dem der Pfad zu den Protokolldateien angezeigt wird. Wählen Sie **Exportieren** aus.
  5. Wechseln Sie zum Pfad `\Users\Public\Documents\MDMDiagnostics`, und zeigen Sie den Bericht an:

      > [!div class="mx-imgBorder"]
      > ![Beispiel von MDM-Diagnoseinformationen, die eine WLAN-Profilkonfiguration auf Windows 10-Geräten anzeigen](./media/troubleshoot-wi-fi-profiles/windows-mdm-diagnostic-info.png)

  > [!TIP]
  > Weitere Informationen finden Sie unter [Diagnostizieren von MDM-Fehlern in Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10).

- Wenn auf Android-Geräten die vertrauenswürdigen Stamm- und SCEP-Profile nicht auf dem Gerät installiert sind, wird der folgende Eintrag in der Omadmlog-Datei der Unternehmensportal-App angezeigt:

  ``` log
  2019-08-01T19:18:13.5120000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04105    Skipping Wifi profile <profile ID> because it is pending certificates.
  ```

  - Wenn sich die vertrauenswürdigen Stamm- und SCEP-Profile auf dem Android-Gerät befinden und kompatibel sind, ist das WLAN-Profil möglicherweise nicht auf dem Gerät. Dieses Problem tritt auf, wenn der **CertificateSelector**-Anbieter der Unternehmensportal-App kein Zertifikat findet, das den angegebenen Kriterien entspricht. Die spezifischen Kriterien können sich in der Zertifikatvorlage oder im SCEP-Profil befinden.

    Wenn das übereinstimmende Zertifikat nicht gefunden wird, sind die Zertifikate auf dem Gerät nicht installiert. Das WLAN-Profil wird nicht angewendet, weil es nicht über das richtige Zertifikat verfügt. In diesem Szenario wird der folgende Eintrag in der Omadmlog-Datei der Unternehmensportal-App angezeigt:

    ` Skipping Wifi profile <profile ID> because it is pending certificates.`

    Im folgenden Beispielprotokoll werden Zertifikate angezeigt, die ausgeschlossen werden, da das Kriterium **Beliebiger Zweck** der erweiterten Schlüsselverwendung festgelegt wurde. Die Zertifikate, die dem Gerät zugewiesen sind, haben jedoch nicht die folgende erweiterte Schlüsselverwendung:

    ```log
    2018-11-27T21:10:37.6390000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID1> and requestId <requestID1> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID2> and requestId <requestID2> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    0 cert(s) matched criteria:
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    2 cert(s) excluded by criteria:
    2018-11-27T21:10:37.6400000    INFO       com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager       14210                00948     Skipping Wifi profile <profile ID> because it is pending certificates.
    ```

    Das folgende Beispiel zeigt das SCEP-Profil, das in die erweiterte Schlüsselverwendung **Beliebiger Zweck** eingegeben wurde. Es wird jedoch nicht in die Zertifikatvorlage der Zertifizierungsstelle eingegeben. Fügen Sie der Zertifikatvorlage die Option **Beliebiger Zweck** hinzu, um das Problem zu beheben. Sie können die Option **Beliebiger Zweck** auch aus dem SCEP-Profil entfernen.

    > [!div class="mx-imgBorder"]
    > ![Hinzufügen von „Beliebiger Zweck“ zur Zertifikatvorlage der Zertifizierungsstelle unter Android](./media/troubleshoot-wi-fi-profiles/android-add-any-purpose-eku.png)

    > [!div class="mx-imgBorder"]
    > ![Hinzufügen von „Beliebiger Zweck“ zum Konfigurationsprofil des SCEP-Zertifikats in Intune unter Android](./media/troubleshoot-wi-fi-profiles/android-any-purpose-scep-device-config-profile.png)

  - Vergewissern Sie sich, dass sich alle erforderlichen Zertifikate in der vollständigen Zertifikatkette auf dem Android-Gerät befinden. Andernfalls kann das WLAN-Profil nicht auf dem Gerät installiert werden. Weitere Informationen finden Sie unter [Fehlende Zwischenzertifizierungsstelle](https://developer.android.com/training/articles/security-ssl#MissingCa) (öffnet die Website von Android).
  - Filtern Sie Omadmlog mit Schlüsselwörtern, um nach Informationen zu suchen, z. B. welches Zertifikat im WLAN-Profil verwendet wird und ob das Profil erfolgreich angewendet wurde.

    Verwenden Sie beispielsweise [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace), um die Protokolle zu lesen. Verwenden Sie die Suchzeichenfolge, um nach „wifimgr“ zu filtern:

    > [!div class="mx-imgBorder"]
    > ![Filtern in CMTrace, um nach WiFiMgr-Konfigurationsprofilen auf Android-Geräten zu suchen](./media/troubleshoot-wi-fi-profiles/cmtrace-filter-wifimgr.png)

    Die Ausgabe sieht in etwa wie im folgenden Protokoll aus:

    > [!div class="mx-imgBorder"]
    > ![Beispielausgabe eines CMTrace-Protokolls, dass die erfolgreiche Anwendung des Intune-WLAN-Konfigurationsprofils auf Geräte zeigt](./media/troubleshoot-wi-fi-profiles/cmtrace-sample-log-output.png)

    Wenn ein Fehler im Protokoll angezeigt wird, kopieren Sie den Zeitstempel des Fehlers, und heben Sie die Filterung des Protokolls auf. Verwenden Sie dann die Option „suchen“ mit dem Zeitstempel, um zu sehen, was direkt vor dem Fehler passiert ist.

### <a name="issue-2-the-wi-fi-profile-is-deployed-to-the-device-but-the-device-cant-connect-to-the-network"></a>Problem 2: Das WLAN-Profil wird auf dem Gerät bereitgestellt, das Gerät kann aber keine Verbindung mit dem Netzwerk herstellen

In der Regel wird dieses Problem durch etwas außerhalb von Intune verursacht. Die folgenden Aufgaben können Ihnen helfen, Konnektivitätsprobleme zu verstehen und zu beheben:

- Stellen Sie manuell eine Verbindung mit dem Netzwerk her, indem Sie ein Zertifikat verwenden, das die gleichen Kriterien wie das WLAN-Profil aufweist.

  Wenn Sie eine Verbindung herstellen können, sehen Sie sich die Zertifikateigenschaften in der manuellen Verbindung an. Aktualisieren Sie dann das Intune-WLAN-Profil mit denselben Zertifikateigenschaften.
- Konnektivitätsfehler werden in der Regel im RADIUS-Serverprotokoll protokolliert. Beispielsweise sollte angezeigt werden, ob das Gerät versucht hat, eine Verbindung mit dem WLAN-Profil herzustellen.

## <a name="need-more-help"></a>Benötigen Sie weitere Hilfe?

- Verwenden Sie die [Intune-Benutzerforen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc), oder [fordern Sie Support von Microsoft an](../fundamentals/get-support.md).

- Weitere Informationen zu WLAN-Profilen in Microsoft Intune finden Sie in den folgenden Artikeln:

  - Hinzufügen von WLAN-Einstellungen für Geräte mit [Android](wi-fi-settings-android.md), [iOS/iPadOS](wi-fi-settings-ios.md) und [Windows 10 und höher](wi-fi-settings-windows.md).
  - [Tipp zur Unterstützung: Konfigurieren von NDES für SCEP-Zertifikatbereitstellungen in Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-How-to-configure-NDES-for-SCEP-certificate/ba-p/455125)
  - Problembehandlung bei der [Bereitstellung des SCEP-Zertifikatprofils](https://support.microsoft.com/help/4526725/troubleshooting-scep-profile-deployment-to-android-devices-in-intune) und der [NDES-Konfiguration](https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune).

- Aktuelle Neuigkeiten, Informationen und technische Tipps finden Sie in den offiziellen Blogs:
  - [Blog des Microsoft Intune-Supportteams](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
  - [Blog von Microsoft Enterprise Mobility + Security](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity)

## <a name="next-steps"></a>Nächste Schritte

[Überwachen Sie Ihre Profile](device-profile-monitor.md).
