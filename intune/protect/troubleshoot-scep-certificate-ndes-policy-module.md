---
title: Behandeln von Problemen mit dem Microsoft Intune Certificate Connector-Richtlinienmodul | Microsoft-Dokumentation
description: Problembehandlung beim Einsatz des NDES-Richtlinienmoduls, wenn das Modul bei der Verwendung von SCEP-Zertifikatprofilen zum Bereitstellen von Zertifikaten mit Intune eine Zertifikatanforderung verarbeitet.
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
ms.openlocfilehash: be53f6102226b004cab2bd953357e8c360a00f67
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915836"
---
# <a name="troubleshoot-the-ndes-policy-module-in-microsoft-intune"></a>Problembehandlung beim NDES-Richtlinienmodul in Microsoft Intune

Mithilfe der Informationen in diesem Artikel können Sie den Einsatz des NDES-Richtlinienmoduls (Network Device Enrollment Service, Registrierungsdienst für Netzwerkgeräte) überprüfen, das mit dem Microsoft Intune Certificate Connector installiert wird. Wenn der NDES eine Anforderung für ein Zertifikat empfängt, wird die Anforderung an das Richtlinienmodul weitergeleitet, das überprüft, ob die Anforderung für das Gerät gültig ist. Nach der Überprüfung kontaktiert der NDES die Zertifizierungsstelle (Certificate Authority, CA), um das Zertifikat im Auftrag des Geräts anzufordern.

Dieser Artikel bezieht sich auf die Schritte 3 und 4 des [SCEP-Kommunikationsworkflows](troubleshoot-scep-certificate-profiles.md).

## <a name="ndes-communication-to-the-policy-module"></a>NDES-Kommunikation mit dem Richtlinienmodul

Nach dem Empfang der Zertifikatanforderung von einem Gerät überprüft der NDES diese Anforderung mit Intune über das Richtlinienmodul, das mit dem Microsoft Intune Certificate Connector installiert wird. Diese Einträge beziehen sich auf den *Zertifikatregistrierungspunkt*.

**Protokolleinträge, die auf Erfolg hinweisen**:

Um zu bestätigen, dass die Überprüfungsanforderung an das Modul übermittelt wird, suchen Sie nach einem Eintrag, der den folgenden Beispielen in Protokollen auf dem NDES-Server ähnelt:

- **IIS-Protokolle**:

  ```
  fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 - 
  fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 201 0 0 341 875
  ```

- **NDESPlugin-Protokoll**:

  ```
  Calling VerifyRequest ...  
  Sending request to certificate registration point.
  ```

  Das folgende Beispiel zeigt eine erfolgreiche Überprüfung der Geräteanforderung, und dass NDES nun die Zertifizierungsstelle kontaktieren kann:

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **CertificateRegistrationPoint.svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`


**Wenn keine Erfolgsindikatoren vorhanden sind**:

Wenn Sie diese Einträge nicht finden, überprüfen Sie zunächst die Anleitungen zur Problembehandlung für die [Kommunikation von Geräten mit dem NDES-Server](troubleshoot-scep-certificate-device-to-ndes.md#troubleshoot-common-errors).

Wenn die Informationen in diesem Artikel Sie nicht bei der Behandlung des Problems unterstützen, finden Sie im Folgenden weitere Einträge, die auf Probleme hinweisen können.

### <a name="ndespluginlog-contains-an-error-12175"></a>„NDESPlugin.log“ enthält den Fehler 12175

Wenn das Protokoll den Fehler 12175 enthält, der etwa wie folgt aussieht, liegt möglicherweise ein Problem mit dem SSL-Zertifikat vor:

```
WINHTTP_CALLBACK_STATUS_FLAG_CERT_CN_INVALID
Failed to send http request /CertificateRegistrationSvc/Certificate/VerifyRequest. Error 12175
```

Moderne Browser und Browser auf mobilen Geräten ignorieren den *Allgemeinen Namen* auf einem SSL-Zertifikat, wenn *Alternative Antragstellernamen* vorhanden sind.

**Lösung**:  Stellen Sie das Webserver-SSL-Zertifikat mit den folgenden Attributen für *Allgemeiner Name* und *Alternativer Antragstellername* aus, und binden Sie es dann an Port 443 in IIS:

  - **Antragstellername**  
    CN = externer Servername
  - **Alternativer Antragstellername**  
     Name = externer Servername  
     DNS-Name = interner Servername

### <a name="ndespluginlog-contains-an-error-403--forbidden-access-is-denied"></a>„„NDESPlugin.log“ enthält den Fehler 403 – 
Verboten: Zugriff verweigert.“

Wenn die folgenden Protokolle den Fehler 403 enthalten, der etwa wie folgt aussieht, ist das Clientzertifikat möglicherweise nicht vertrauenswürdig oder ungültig:

**NDESPlugin.log**:

```
Sending request to certificate registration point.
Verify challenge returns <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head><meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
<title>403 - Forbidden: Access is denied.</title>
```

**IIS-Protokoll**:

```
POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 -<IP_address>
NDES_Plugin - 403 16 2148204809 453  
```

Dieses Problem tritt auf, wenn Zertifikate von Zwischenzertifizierungsstellen im Zertifikatspeicher für vertrauenswürdige Stammzertifizierungsstellen des NDES-Servers vorhanden sind.

Wenn ein Zertifikat die gleichen Werte für *Ausgestellt für* und *Ausgestellt von* aufweist, handelt es sich um ein Stammzertifikat. Andernfalls handelt es sich um ein Zwischenzertifikat.

**Lösung**: Um das Problem zu behandeln, identifizieren Sie die Zertifikate von Zwischenzertifizierungsstellen und entfernen sie aus dem Zertifikatspeicher für vertrauenswürdige Stammzertifizierungsstellen.

### <a name="ndespluginlog-indicates-the-challenge-returns-false"></a>„NDESPlugin.log“ gibt an, dass auf die Anforderung „false“ zurückgegeben wird

Wenn als Ergebnis der Anforderung **false** zurückgegeben wird, überprüfen Sie *CertificateRegistrationPoint.svclog* auf Fehler. Beispielsweise wird möglicherweise der Fehler „Das Signaturzertifikat konnte nicht abgerufen werden“ angezeigt, der dem folgenden Eintrag ähnelt:

```
Signing certificate could not be retrieved. System.Security.Cryptography.CryptographicException: m_safeCertContext is an invalid handle. at System.Security.Cryptography.X509Certificates.X509Certificate.ThrowIfContextInvalid() at System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString() at Microsoft.ConfigurationManager.CertRegPoint.CRPCertificate.RetrieveSigningCert(String certThumbprint
```

**Lösung**: Öffnen Sie auf dem Server, auf dem der Connector installiert ist, den Registrierungs-Editor, suchen Sie den Registrierungsschlüssel `HKLM\SOFTWARE\Microsoft\MicrosoftIntune\NDESConnector`, und überprüfen Sie dann, ob der Wert SigningCertificate vorhanden ist.

Wenn dieser Wert nicht vorhanden ist, starten Sie den Intune-Connectordienst in „services.msc“ neu, und überprüfen Sie dann, ob der Wert in der Registrierung angezeigt wird. Wenn der Wert noch immer fehlt, liegt dies häufig daran, dass zwischen dem NDES-Server und dem Intune-Dienst Netzwerkkonnektivitäts-Probleme bestehen.

## <a name="ndes-passes-the-request-to-issue-the-certificate"></a>NDES übergibt die Anforderung zum Ausstellen des Zertifikats

Nach einer erfolgreichen Überprüfung durch den Zertifikatregistrierungspunkt (das Richtlinienmodul) übergibt NDES die Zertifikatanforderung im Auftrag des Geräts an die Zertifizierungsstelle.

**Protokolleinträge, die auf Erfolg hinweisen**:

- **NDESPlugin-Protokoll**:

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **IIS-Protokolle**:

  ```
  fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe ... 80 - 
  fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 2713 1296
  ```

- **CertificateRegistrationPoint.svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`

**Wenn keine Erfolgsindikatoren vorhanden sind**:

Wenn die Einträge, die auf Erfolg hinweisen, nicht angezeigt werden, führen Sie die folgenden Schritte aus:

1. Suchen Sie nach Problemen, die in *CertificateRegistrationPoint.svclog* protokolliert werden, wenn der Zertifikatregistrierungspunkt die Herausforderung verifiziert. Suchen Sie nach den Einträgen zwischen den folgenden Zeilen:

   - VerifyRequest Started (VerifyRequest gestartet).
   - VerifyRequest Finished with status False (Verifyrequest mit dem Status „False“ abgeschlossen)

2. Öffnen Sie die Zertifizierungsstellen-MMC für die Zertifizierungsstelle, und wählen Sie **Fehlerhafte Anforderungen** aus, um nach Fehlern zu suchen, die zur Identifizierung eines Problems beitragen. Die folgende Abbildung dient als Beispiel:

   ![Beispiel für eine fehlerhafte Anforderung](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/failed-requests.png)

3. Überprüfen Sie das Anwendungsereignisprotokoll der Zertifizierungsstelle auf Fehler. In der Regel können Sie Fehler anzeigen, die dem entsprechen, was Sie im vorherigen Schritt unter **Fehlerhafte Anforderungen** sehen. Die folgende Abbildung dient als Beispiel:

   ![Überprüfen des Anwendungsprotokolls](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/application-log-errors.png)

## <a name="next-steps"></a>Nächste Schritte

Wenn das NDES-Richtlinienmodul die Anforderung überprüft und sie an die Zertifizierungsstelle weitergeleitet wird, besteht der nächste Schritt darin, die [Übermittlung des Zertifikats an das Gerät](troubleshoot-scep-certificate-delivery.md) zu überprüfen.
