---
title: Problembehandlung bei der Berichterstattung von erfolgreichen Zertifikatbereitstellungen auf Geräten bei Verwendung von SCEP mit Microsoft Intune | Microsoft-Dokumentation
description: Problembehandlung bei der Berichterstellung durch NDES und den Connector für Intune über eine erfolgreiche Bereitstellung von Zertifikaten, die mit SCEP-Zertifikatprofilen bereitgestellt wurden.
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
ms.openlocfilehash: 2ccc738626efc140efca46d1b997164ed36dd37f
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916018"
---
# <a name="troubleshoot-ndes-reporting-of-certificate-deployments-in-microsoft-intune"></a>Problembehandlung bei der NDES-Berichterstellung von Zertifikatbereitstellungen in Microsoft Intune

Verwenden Sie die folgenden Informationen, um zu bestätigen, dass NDES und der Microsoft Intune Certificate Connector erfolgreich an Intune berichtet haben, dass das Zertifikat an ein Gerät übermittelt wurde. Die Berichterstellung an Intune ist die letzte Phase der Verwendung von SCEP-Zertifikatprofilen, um ein Zertifikat für Windows-Geräte bereitzustellen.

Dieser Artikel bezieht sich auf Schritt 6 des [SCEP-Kommunikationsworkflows](troubleshoot-scep-certificate-profiles.md).

## <a name="review-for-signs-of-successful-reporting"></a>Überprüfen auf Anzeichen für eine erfolgreiche Berichterstellung

Wenn die Berichterstellung erfolgreich war, finden Sie Einträge, die den folgenden Beispielen auf dem NDES-Server ähneln:

- **IIS-Protokoll**:

  `fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/Notify - 443 - fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 204 0 0 277 62`

- **NDESPlugin.log**:

  ```
  Calling Notifyrequest ...
  Sending request to certificate registration point.
  Exiting Notify with 0x0
  ```

- **CertificateRegistrationPoint.svclog**:

  ![Intune Certificate Connector-Protokoll](../protect/media/troubleshoot-scep-certificate-reporting/certificate-registration-point-log.png)

- **NDESConnector.svclog**:

  ![Intune Certificate Connector-Protokoll](../protect/media/troubleshoot-scep-certificate-reporting/ndesconnector-log.png)

- **CertificateRequestStatus**:

  Wechseln Sie zum Ordner *%ProgramFiles%\Microsoft Intune\CertificateRequestStatus*, in dem sich die Ordner **Failed**, **Processing** und **Succeed** befinden, die Statusdateien für Zertifikatanforderungen enthalten.

  Wenn die Zertifikatanforderung erfolgreich verarbeitet wurde, werden neue Dateien im **Succeed**-Ordner angezeigt. Sie können mit *Notepad.exe* die Dateien öffnen und die Daten anzeigen, die vom Intune Certificate Connector in den Intune-Dienst hochgeladen werden. Zu den hochgeladenen Daten zählen Details wie **Zertifikatseriennummer**, **Benutzer-ID**, **Geräte-ID** und **Fingerabdruck**.

### <a name="troubleshoot-stuck-files"></a>Problembehandlung bei hängengebliebenen Dateien

Wenn keine neuen Dateien im Ordner *Succeed* erstellt wurden, überprüfen Sie, ob Dateien im Ordner *Processing* hängengeblieben sind.

Vergewissern Sie sich, dass der Intune-Connectordienst auf dem NDES-Server gestartet wurde und keine Fehler in „Ndesconnector.svclog“ vorliegen.

## <a name="next-steps"></a>Nächste Schritte

[Anfordern von Support für Microsoft Intune](../fundamentals/get-support.md)
