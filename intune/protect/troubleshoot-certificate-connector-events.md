---
title: Behandeln von Problemen mit dem Microsoft Intune Certificate Connector und den Ereignis-IDs | Microsoft-Dokumentation
description: Behandeln von Problemen mit dem Microsoft Intune Certificate Connector durch Überprüfen von Ereignis-IDs, Beschreibungen und Diagnosecodes für den Intune-Connectordienst
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/01/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 682d51269798dff181a3bd8384268da862118a70
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721759"
---
# <a name="intune-certificate-connector-events-and-diagnostic-codes"></a>Intune Certificate Connector-Ereignisse und Diagnosecodes

Ab Version 6.1806.x.x protokolliert der Intune-Connectordienst Ereignisse in der **Ereignisanzeige** (**Anwendungs- und Dienstprotokolle** > **Microsoft Intune-Connector**). Mit diesen Ereignissen können Sie mögliche Probleme bei der Konfiguration des Intune-Connectors beheben. In diesen Ereignissen werden erfolgreiche und fehlgeschlagene Vorgänge protokolliert. Außerdem enthalten sie Diagnosecodes mit Meldungen, die IT-Administratoren bei der Problembehandlung helfen.

> [!TIP]  
> Informationen zum Beheben von Problemen und Überprüfen des Intune-Connector-Setups finden Sie unter [Skriptbeispiele für die Zertifizierungsstelle](https://aka.ms/intuneconnectorverificationscript).

## <a name="event-ids-and-descriptions"></a>Ereignis-IDs und -beschreibungen

| Ereignis-ID      | Ereignisname    | Ereignisbeschreibung | Zugehörige Diagnosecodes |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Der Connectordienst wurde gestartet. | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Der Connectordienst wurde beendet. | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Das Connectorregistrierungszertifikat wurde erfolgreich erneuert. | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | Das Connectorregistrierungszertifikat konnte nicht erneuert werden. Installieren Sie den Connector neu. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | Das Connectorregistrierungszertifikat konnte nicht aus der Registrierung abgerufen werden. Den Zertifikatfingerabdruck für dieses Ereignis finden Sie in den Ereignisdetails. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Diagnoseinformationen finden Sie in den Ereignisdetails. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | Ein PKCS-Zertifikat wurde erfolgreich ausgestellt. Die Geräte- und Benutzer-ID, den Zertifizierungsstellennamen, den Zertifizierungsvorlagennamen und den Zertifikatfingerabdruck für dieses Ereignis finden Sie in den Ereignisdetails. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | Ein PKCS-Zertifikat konnte nicht ausgestellt werden. Die Geräte- und Benutzer-ID, den Zertifizierungsstellennamen, den Zertifizierungsvorlagennamen und den Zertifikatfingerabdruck für dieses Ereignis finden Sie in den Ereignisdetails. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | Das Zertifikat wurde erfolgreich widerrufen. Die Geräte- und Benutzer-ID, den Zertifizierungsstellennamen und die Zertifikatseriennummer für dieses Ereignis finden Sie in den Ereignisdetails. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | Das Zertifikat konnte nicht widerrufen werden. Die Geräte- und Benutzer-ID, den Zertifizierungsstellennamen und die Zertifikatseriennummer für dieses Ereignis finden Sie in den Ereignisdetails. Weitere Informationen finden Sie in den SCEP-SVC-Protokollen.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | Die Zertifikatanforderung oder die Widerrufdaten wurden erfolgreich hochgeladen. Informationen zu Uploads finden Sie in den Ereignisdetails. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | Die Zertifikatanforderung oder die Widerrufdaten konnten nicht hochgeladen werden. Zur Ermittlung des Fehlers können Sie den Uploadstatus in den Ereignisdetails überprüfen.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | Eine Anforderung zum Signieren eines Zertifikats, Herunterladen eines Clientzertifikats oder Widerrufen eines Zertifikats wurde erfolgreich heruntergeladen. Informationen zu Downloads finden Sie in den Ereignisdetails.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | Eine Anforderung zum Signieren eines Zertifikats, Herunterladen eines Clientzertifikats oder Widerrufen eines Zertifikats konnte nicht heruntergeladen werden. Informationen zu Downloads finden Sie in den Ereignisdetails. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | Der Zertifikatregistrierungspunkt hat die Clientabfrage erfolgreich überprüft. | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | Der Zertifikatregistrierungspunkt hat die Anforderung zwar abgeschlossen, diese jedoch abgelehnt. Weitere Informationen erhalten Sie durch den Diagnosecode und die zugehörige Meldung. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | Der Zertifikatregistrierungspunkt konnte die Clientabfrage nicht überprüfen. Weitere Informationen erhalten Sie durch den Diagnosecode und die zugehörige Meldung. Die Geräte-ID und die zugehörige Abfrage finden Sie in den Ereignismeldungsdetails. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | Der Zertifikatregistrierungspunkt hat den Benachrichtigungsprozess erfolgreich abgeschlossen und das Zertifikat an das Clientgerät gesendet. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | Der Zertifikatregistrierungspunkt konnten den Benachrichtigungsprozess nicht abschließen. Informationen zur Anforderung finden Sie in den Ereignismeldungsdetails. Überprüfen Sie die Verbindung zwischen dem SCEP-Server und der Zertifizierungsstelle. | 0x00000000, 0x0FFFFFFF |

## <a name="diagnostic-codes"></a>Diagnosecodes

| Diagnosecode | Diagnosename | Diagnosemeldung |
| -------------   | -------------   | -------------      |
| 0x00000000 | Erfolgreich  | Erfolgreich |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | Die Zertifizierungsstelle ist ungültig oder nicht erreichbar. Stellen Sie sicher, dass die Zertifizierungsstelle verfügbar ist und Ihr Server mit dieser kommunizieren kann. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | Das Symantec-Clientauthentifizierungszertifikat konnte im lokalen Zertifikatspeicher nicht gefunden werden. Weitere Informationen finden Sie im Artikel [Installieren des Symantec-Zertifikats zur Registrierungsautorisierung](certificates-digicert-configure.md#install-the-digicert-ra-certificate).  |
| 0x00000402 | RevokeCert_AccessDenied  | Für das angegebene Konto sind keine Berechtigungen vorhanden, mit denen ein Zertifikat der Zertifizierungsstelle widerrufen werden kann. Die ausstellende Zertifizierungsstelle können Sie durch das Feld für den Namen der Zertifizierungsstelle in den Ereignismeldungsdetails ermitteln.  |
| 0x00000403 | CertThumbprint_NotFound  | Für Ihre Eingabe konnte kein zugehöriges Zertifikat gefunden werden. Registrieren Sie den Zertifikatconnector, und wiederholen Sie den Vorgang. |
| 0x00000404 | Certificate_NotFound  | Für die Eingabe konnte kein zugehöriges Zertifikat gefunden werden. Registrieren Sie den Zertifikatconnector erneut, und wiederholen Sie den Vorgang. |
| 0x00000405 | Certificate_Expired  | Ein Zertifikat ist abgelaufen. Registrieren Sie den Zertifikatconnector erneut, um das Zertifikat zu erneuern, und wiederholen Sie den Vorgang. |
| 0x00000408 | CRPSCEPCert_NotFound  | Das CRP-Verschlüsselungszertifikat wurde nicht gefunden. Stellen Sie sicher, dass SCEP und der Intune-Connector richtig eingerichtet sind. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | Das Signaturzertifikat konnte nicht abgerufen werden. Stellen Sie sicher, dass der Intune-Connectordienst richtig konfiguriert ist und der Intune-Connectordienst ausgeführt wird. Achten Sie außerdem darauf, dass Zertifikatdownloads erfolgreich abgeschlossen wurden. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | Die SCEP-Abfrage konnte nicht deserialisiert werden. Stellen Sie sicher, dass SCEP und der Intune-Connector richtig eingerichtet sind. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Die Anforderung wurde aufgrund einer abgelaufenen Zertifikatabfrage abgelehnt. Das Clientgerät kann eine neue Anforderung stellen, nachdem es eine neue Abfrage vom Verwaltungsserver abgerufen hat. |
| 0x0FFFFFFFF | Unknown_Error  | Die Anforderung kann nicht abgeschlossen werden, da ein serverseitiger Fehler aufgetreten ist. Bitte versuchen Sie es erneut. |


## <a name="next-steps"></a>Nächste Schritte
Weitere Unterstützung finden Sie im Leitfaden zur [Problembehandlung für die Bereitstellung eines SCEP-Zertifikatprofils in Microsoft Intune](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune).
