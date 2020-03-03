---
title: Behandeln von Problemen bei der Verwendung von SCEP-Zertifikatprofilen zum Bereitstellen von Zertifikaten mit Microsoft Intune | Microsoft-Dokumentation
description: Behandeln von Problemen bei der Verwendung von SCEP durch Geräte zum Anfordern von Zertifikaten für die Verwendung mit Intune einschließlich der Kommunikation zwischen Geräten und NDES, NDES und Zertifizierungsstellen sowie Intune Certificate Connector und Intune-Dienst.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4496a5bbc6d5ee5134dc4e6a795494710ea6865d
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515219"
---
# <a name="overview-for-troubleshooting-scep-certificate-profiles-with-microsoft-intune"></a>Übersicht zur Problembehandlung bei SCEP-Zertifikatprofilen in Microsoft Intune

Die Verwendung von Simple Certificate Enrollment-Protokoll-Zertifikatprofilen (SCEP) kann für die Problembehandlung in Intune schwierig sein. Dieser Artikel bietet eine Übersicht, die Ihnen helfen kann, Probleme zu behandeln:

- Erläutern der Architektur und des Kommunikationsflusses des SCEP-Prozesses
- Unterstützung beim Eingrenzen eines Problems in diesem Kommunikationsfluss
- Identifizieren der entscheidenden Protokolldateien, auf die in nachfolgenden Artikeln zur Problembehandlung bei Zertifikatprofilen verwiesen wird

Die Informationen in diesem und den zugehörigen Artikeln zur Problembehandlung bei SCEP-Zertifikaten gelten für die Verwendung von SCEP-Zertifikatprofilen mit Android-, iOS/iPad- und Windows-Geräten. Ähnliche Informationen für macOS sind zurzeit nicht verfügbar.

Informationen zum Behandeln von Problemen mit dem Registrierungsdienst für Netzwerkgeräte (Network Device Enrollment Service, NDES) finden Sie in den folgenden Artikeln von „support.microsoft.com“:

- [Überprüfen der lokalen NDES-Konfiguration für SCEP-Zertifikate in Intune](https://support.microsoft.com/help/4490130/ndes-configuration-on-premises-for-scep-certificates-in-intune)
- [Problembehandlung der NDES-Konfiguration für die Verwendung mit Microsoft Intune-Zertifikatprofilen]( https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune)

Bevor Sie fortfahren, stellen Sie sicher, dass Sie die [Voraussetzungen für die Verwendung von SCEP-Zertifikatprofilen](certificates-scep-configure.md#prerequisites-for-using-scep-for-certificates) einschließlich der Bereitstellung eines Stammzertifikats über ein vertrauenswürdiges Zertifikatsprofil erfüllen.

## <a name="scep-communication-flow-overview"></a>Übersicht über den SCEP-Kommunikationsfluss

Die folgende Grafik bietet eine grundlegende Übersicht über den SCEP-Kommunikationsprozess in Intune.

![SCEP-Zertifikatprofilflow](../protect/media/troubleshoot-scep-certificate-profiles/scep-certificate-profile-flow.png)

1. [Bereitstellen eines SCEP-Zertifikatprofils](troubleshoot-scep-certificate-profile-deployment.md) Intune generiert eine Abfragezeichenfolge, die einen bestimmten Benutzer, einen bestimmten Zertifikatzweck und einen Zertifikattyp erfordert.

2. [Kommunikation zwischen Geräten und NDES-Server](troubleshoot-scep-certificate-device-to-ndes.md) Das Gerät verwendet den URI für NDES aus dem Profil zum Kontaktieren des NDES-Servers, damit es eine Anforderung senden kann.

3. [Kommunikation zwischen NDES und Richtlinienmodul](troubleshoot-scep-certificate-ndes-policy-module.md). Der NDES leitet die Anforderung an das Intune Certificate Connector-Richtlinienmodul auf dem Server weiter, das die Anforderung überprüft.

4. [NDES mit Zertifizierungsstelle](troubleshoot-scep-certificate-ndes-policy-module.md). Der NDES übergibt gültige Anforderungen zum Ausstellen eines Zertifikats an die Zertifizierungsstelle (CA).

5. [Zertifikatübermittlung an das Gerät](troubleshoot-scep-certificate-delivery.md). Das Zertifikat wird an das Gerät übermittelt.

6. [Berichterstellung über die Bereitstellung in Intune](troubleshoot-scep-certificate-reporting.md). Der Intune Certificate Connector meldet das Ausstellen des Zertifikats an Intune.

## <a name="log-files"></a>Protokolldateien

Um Probleme mit dem Workflow für Kommunikation und Zertifikatbereitstellung zu identifizieren, überprüfen Sie sowohl die Protokolldateien aus der Serverinfrastruktur als auch von den Geräten. Spätere Abschnitte zur Problembehandlung bei SCEP-Zertifikatprofilen beziehen sich auf Protokolldateien, auf die in diesem Abschnitt verwiesen wird.

- [Infrastruktur- und Serverprotokolle](#logs-for-on-premises-infrastructure)

Geräteprotokolle sind von der Geräteplattform abhängig:  

- [iOS und iPadOS](#logs-for-ios-and-ipados-devices)
- [Android](#logs-for-android-devices)
- [Windows](#logs-for-windows-devices)

### <a name="logs-for-on-premises-infrastructure"></a>Protokolle für die lokale Infrastruktur
  
Die lokale Infrastruktur, die die Verwendung von SCEP-Zertifikatprofilen für Zertifikatbereitstellungen unterstützt, umfasst den Microsoft Intune Certificate Connector, den NDES, der auf einem Windows-Server ausgeführt wird, und die Zertifizierungsstelle.

Zu den Protokolldateien für diese Rollen zählen Windows-Ereignisanzeige, Zertifikatkonsolen und verschiedene Protokolldateien für Intune Certificate Connector, NDES oder andere Rollen und Vorgänge, die Teil der lokalen Infrastruktur sind.

Die folgende Liste enthält Protokolle oder Konsolen, auf die in den nachfolgenden SCEP-Artikeln zur Problembehandlung verwiesen wird. 

- **NDESConnector_date_time.svclog**:

  Dieses Protokoll zeigt die Kommunikation des Microsoft Intune Certificate Connector mit dem Intune-Clouddienst. Um diese Protokolldatei anzuzeigen, können Sie das [Service Trace Viewer-Tool](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) verwenden.

  Zugehöriger Registrierungsschlüssel: *HKLM\SW\Microsoft\MicrosoftIntune\NDESConnector\ConnectionStatus*

  Speicherort: Auf dem Server, der NDES auf *%program_files%\Microsoft intune\ndesconnectorisvc\logs\logs* hostet

- **CertificateRegistrationPoint_date_time.svclog**:

  Dieses Protokoll zeigt das NDES-Richtlinienmodul, das Zertifikatanforderungen empfängt und überprüft. Um diese Protokolldatei anzuzeigen, können Sie das [Service Trace Viewer-Tool](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) verwenden.

  Speicherort: Auf dem Server, der NDES auf *%program_files%\Microsoft intune\ndesconnectorisvc\logs\logs* hostet

- **NDESPlugin.log**:

  Dieses Protokoll zeigt das Übergeben von Zertifikatanforderungen an den Zertifikatregistrierungspunkt und die resultierende Überprüfung dieser Anforderungen.

  Speicherort: Auf dem Server, der NDES auf *% program_files%\Microsoft intune\NDESPolicyModule\logs* hostet

- **IIS-Protokolle**:

  IIS-Protokolle zeigen die Zertifikatanforderungen von mobilen Geräten an, die beim NDES eingehen.

  Speicherort: Auf dem Server, der NDES auf *c:\inetpub\logs\LogFiles\W3SVC1* hostet

- **Windows-Anwendungsprotokoll**:

  Dieses Protokoll ist nützlich, wenn Sie IIS-Probleme wie den SCEP-Anwendungspool untersuchen.

  Speicherort: Auf dem Server, der NDES hostet: Führen Sie **eventvwr.msc** aus, um die Windows-Ereignisanzeige zu öffnen.




### <a name="logs-for-android-devices"></a>Protokolle für Android-Geräte

Bei Geräten, auf denen Android ausgeführt wird, verwenden Sie die App-Protokolldatei des **Android-Unternehmensportals**, **OMADM.log**. Stellen Sie vor dem Erfassen und Überprüfen von Protokollen sicher, dass [ausführliche Protokollierung](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) aktiviert ist, und reproduzieren Sie dann das Problem.

Informationen zum Erfassen von OMADM-Protokollen von einem Gerät finden Sie unter [Hochladen und E-Mail-Versand von Protokollen mithilfe eines USB-Kabels](/intune-user-help/send-logs-to-your-it-admin-using-cable-android).

Unterstützung finden Sie auch unter [Hochladen und E-Mail-Versand von Protokollen aus der Microsoft Intune-App](/intune-user-help/send-logs-to-your-it-admin-by-email-android#upload-and-email-logs-from-microsoft-intune-app).

### <a name="logs-for-ios-and-ipados-devices"></a>Protokolle für iOS- und iPadOS-Geräte

Bei Geräten, auf denen iOS/iPadOS ausgeführt wird, verwenden Sie Debugprotokolle und **Xcode**, der auf einem Macintosh-Computer ausgeführt wird:

1. Verbinden Sie das iOS/iPadOS-Gerät mit dem Mac, und wechseln Sie dann zu **Anwendungen** > **Hilfsprogramme**, um die Konsolen-App zu öffnen. 

2. Wählen Sie unter **Aktion** die Option **Include Info Messages** (Informationsmeldungen einschließen) und **Include Debug Messages** (Debugmeldungen einschließen) aus.

   ![Auswählen von Protokolloptionen](../protect/media/troubleshoot-scep-certificate-profiles/message-options.png)

3. Reproduzieren Sie das Problem, und speichern Sie die Protokolle in einer Textdatei:
   1. Wählen Sie **Bearbeiten** > **Alle auswählen** aus, um alle Nachrichten auf dem aktuellen Bildschirm auszuwählen, und wählen Sie dann **Bearbeiten** > **Kopieren** aus, um die Nachrichten in die Zwischenablage zu kopieren. 
   2. Öffnen Sie die TextEdit-Anwendung, fügen Sie die kopierten Protokolle in eine neue Textdatei ein, und speichern Sie die Datei.


Das Unternehmensportalprotokoll für iOS- und iPadOS-Geräte enthält keine Informationen zu SCEP-Zertifikatprofilen.

### <a name="logs-for-windows-devices"></a>Protokolle für Windows-Geräte

Verwenden Sie für Geräte unter Windows die Windows-Ereignisprotokolle, um Probleme mit der Registrierung oder der Geräteverwaltung für Geräte zu diagnostizieren, die Sie mit Intune verwalten.

Öffnen Sie auf dem Gerät **Ereignisanzeige** > **Anwendungs- und Dienstprotokolle** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider**.

![Windows-Ereignisprotokolle](../protect/media/troubleshoot-scep-certificate-profiles/windows-event-log.png)

## <a name="next-steps"></a>Nächste Schritte

Überprüfen der [Bereitstellung von SCEP-Zertifikatprofilen](troubleshoot-scep-certificate-profile-deployment.md) 
