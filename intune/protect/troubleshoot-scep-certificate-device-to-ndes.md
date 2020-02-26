---
title: Behandeln von Problemen bei der Kommunikation zwischen verwaltetem Gerät und NDES in Microsoft Intune | Microsoft-Dokumentation
description: Behandeln von Problemen bei der Kommunikation zwischen verwaltetem Gerät und NDES-Server bei Verwendung von SCEP-Zertifikatprofilen zum Bereitstellen von Zertifikaten mit Intune.
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
ms.openlocfilehash: 7945f1df3ddf1a6ff2c42a537e1071d1b5acff24
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514267"
---
# <a name="troubleshoot-device-to-ndes-server-communication-for-scep-certificate-profiles-in-microsoft-intune"></a>Problembehandlung für die Kommunikation zwischen Gerät und NDES-Server für SCEP-Zertifikatprofile in Microsoft Intune

Verwenden Sie die folgenden Informationen, um zu bestimmen, ob ein Gerät, das ein Simple Certificate Enrollment-Protokoll-Zertifikatprofil (SCEP) für Intune empfangen und verarbeitet hat, erfolgreich eine Verbindung mit dem Registrierungsdienst für Netzwerkgeräte (Network Device Enrollment Service, NDES) herstellen kann, um eine Herausforderung darzustellen. Auf dem Gerät wird ein privater Schlüssel generiert und die Zertifikatsignieranforderung (Certificate Signing Request, CSR) und die Abfrage werden vom Gerät an den NDES-Server übergeben. Zum Kontaktieren des NDES-Servers verwendet das Gerät den URI aus dem SCEP-Zertifikatprofil.

Dieser Artikel verweist auf Schritt 2 der [Übersicht zur Problembehandlung bei SCEP-Zertifikatprofilen mit Microsoft Intune](troubleshoot-scep-certificate-profiles.md).

## <a name="review-iis-logs-for-a-connection-from-the-device"></a>Überprüfen der IIS-Protokolle auf eine Verbindung vom Gerät

IIS-Protokolle enthalten für alle Plattformen denselben Typ von Einträgen.


1. Öffnen Sie auf dem NDES-Server die letzte IIS-Protokolldatei, die sich im folgenden Ordner befindet: *%SystemDrive%\inetpub\logs\logfiles\w3svc1*

2. Suchen Sie im Protokoll nach Einträgen, die den folgenden Beispielen ähneln. Beide Beispiele enthalten den Status **200**, der in der Nähe des Endes angezeigt wird:

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACaps&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 186 0.`

   Und

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACert&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 3567 0`

3. Wenn das Gerät IIS kontaktiert, wird eine HTTP GET-Anforderung für „mscep.dll“ protokolliert.

   Überprüfen Sie den Statuscode in der Nähe des Endes dieser Anforderung:
   - **Statuscode 200**: Dieser Status gibt an, dass die Verbindung mit dem NDES-Server erfolgreich hergestellt wurde.
   - **Statuscode 500**: Der IIS_IURS-Gruppe fehlen möglicherweise die richtigen Berechtigungen. Weitere Informationen finden Sie unter [Statuscode 500](#status-code-500) weiter unten in diesem Artikel.
   - Wenn der Statuscode nicht 200 oder 500 ist:

     - Weitere Informationen zum Überprüfen der Konfiguration finden Sie unter [Testen der SCEP-Server-URL](#test-the-scep-server-url) weiter unten in diesem Artikel.

     - Weitere Informationen zu weniger häufigen Fehlercodes finden Sie unter [Die HTTP-Statuscodes in IIS 7 und neueren Versionen](https://support.microsoft.com/help/943891).

   Wenn die Verbindungsanforderung überhaupt nicht protokolliert wird, ist der Kontakt zwischen dem Gerät und dem NDES-Server möglicherweise im Netzwerk blockiert.

## <a name="review-device-logs-for-connections-to-ndes"></a>Überprüfen von Geräteprotokolle für Verbindungen mit dem NDES

### <a name="android-devices"></a>Android-Geräte

Überprüfen Sie das [Geräte-OMADM-Protokoll](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices). Suchen Sie nach Einträgen, die protokolliert wurden, als das Gerät die Verbindung mit dem NDES herstellte, die den folgenden ähneln:

```
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  There are 1 requests
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  Trying to enroll certificate request: ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c;Hash=1677525787
2018-02-27T05:16:09.5530000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:14.6440000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Received '200 OK' when sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.8220000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10 Encoding message: org.jscep.message.PkcsReq@2b06f45f[messageData=org.<server>.pkcs.PKCS10CertificationRequest@699b3cd,messageType=PKCS_REQ,senderNonce=Nonce [D447AE9955E624A56A09D64E2B3AE76E],transId=251E592A777C82996C7CF96F3AAADCF996FC31FF]
2018-02-27T05:16:21.8790000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10  Signing pkiMessage using key belonging to [dn=CN=<uesrname>; serial=1]
2018-02-27T05:16:21.9580000  VERB  Event  org.jscep.transaction.EnrollmentTransaction  18327     10  Sending org.<server>.cms.CMSSignedData@ad57775
```

Zu den Schlüsseleinträgen zählen die folgenden Beispieltextzeichenfolgen:

- There are 1 requests (Es ist 1 Anforderung vorhanden).
- Received '200 OK' when sending GetCACaps(ca) to https://\<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca (Beim Senden von GetCACaps(ca) an „https://<Server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca“ wurde „200 OK“ empfangen.)
- Signing pkiMessage using key belonging to [dn=CN=\<username>; serial=1] (Signieren von pkiMessage mithilfe eines Schlüssels, der zu [dn=CN=<Benutzername>; serial=1] gehört)


Die Verbindung wird auch von IIS im Ordner „%SystemDrive%\inetpub\logs\LogFiles\W3SVC1\“ des NDES-Servers protokolliert. Hier ein Beispiel:

```
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACert&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 3909 0
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACaps&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 421 
```

### <a name="iosipados-devices"></a>iOS-/iPadOS-Geräte

Überprüfen Sie das [Gerätedebugprotokoll](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices). Suchen Sie nach Einträgen, die protokolliert wurden, als das Gerät die Verbindung mit dem NDES herstellte, die den folgenden ähneln:

```
debug    18:30:53.691033 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\ 
debug    18:30:54.640644 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
default    18:30:55.483977 -0500    profiled    Attempting to retrieve issued certificate...\ 
debug    18:30:55.487798 -0500    profiled    Sending CSR via GET.\  
debug    18:30:55.487908 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQGZwmPoqFMbX3g85CJT8khPaqFW05yGDTPSX9YpuEE0Bmtht9EwOpOZe6O7sd77IhfFZVmHmwy5mIYN7K6mpx/4Cb5zcNmY3wmTBlKEkDQpZDRf5PpVQ3bmQ3we9XxeK1S4UsAXHVdYGD+bg/bCafMIAGCSqGSIb3DQEHATAUBggqhkiG9w0DBwQI5D5J2lwZS5OggASCF6jSG9iZA/EJ93fEvZYLV0v7GVo3JAsR11O7DlmkIqvkAg5iC6DQvXO1j88T/MS3wV+rqUbEhktr8Xyf4sAAPI4M6HMfVENCJTStJw1PzaGwUJHEasq39793nw4k268UV5XHXvzZoF3Os2OxUHSfHECOj
```

Zu den Schlüsseleinträgen zählen die folgenden Beispieltextzeichenfolgen:

- operation=GetCACert
- Attempting to retrieve issued certificate (Versuch, das ausgestellte Zertifikat abzurufen)
- Sending CSR via GET (Senden von CSR über GET)
- operation=PKIOperation

### <a name="windows-devices"></a>Windows-Geräte

Auf einem Windows-Gerät, das eine Verbindung mit NDES herstellt, können Sie die Windows-Ereignisanzeige für Geräte anzeigen und nach Hinweisen auf eine erfolgreiche Verbindung suchen. Verbindungen werden als Ereignis-ID **36** im Protokoll *DeviceManagement-Enterprise-Diagnostics-Provide* > **Admin** von Geräten protokolliert.

So öffnen Sie das Protokoll:

1. Führen Sie auf dem Gerät **eventvwr.msc** aus, um die Windows-Ereignisanzeige zu öffnen.

2. Erweitern Sie **Anwendungs- und Dienstprotokolle** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin**.

3. Suchen Sie nach Ereignis **36**, das dem folgenden Beispiel ähnelt, mit der Schlüsselzeile **SCEP: Certificate request generated successfully** (SCEP: Zertifikatanforderung wurde erfolgreich generiert):

   ```
   Event ID:      36
   Task Category: None
   Level:         Information
   Keywords:
   User:          <UserSid>
   Computer:      <Computer Name>
   Description:
   SCEP: Certificate request generated successfully. Enhanced Key Usage: (1.3.6.1.5.5.7.3.2), NDES URL: (https://<server>/certsrv/mscep/mscep.dll/pkiclient.exe), Container Name: (), KSP Setting: (0x2), Store Location: (0x1).
   ```

## <a name="troubleshoot-common-errors"></a>Problembehandlung bei häufigen Fehlern

Die folgenden Abschnitte helfen bei häufigen Problemen bei Verbindungen zwischen allen Geräteplattformen und dem NDES.

### <a name="status-code-500"></a>Statuscode 500

Verbindungen mit dem Statuscode 500, die dem folgenden Beispiel ähneln, geben an, dass das Benutzerrecht *Annehmen der Clientidentität nach Authentifizierung* nicht der IIS_IURS-Gruppe auf dem NDES-Server zugewiesen ist. Der Statuswert **500** wird am Ende angezeigt:

```
2017-08-08 20:22:16 IP_address GET /certsrv/mscep/mscep.dll operation=GetCACert&message=SCEP%20Authority 443 - 10.5.14.22 profiled/1.0+CFNetwork/811.5.4+Darwin/16.6.0 - 500 0 1346 31
```

**So behandeln Sie dieses Problem**:

1. Führen Sie auf dem NDES-Server **secpol. msc** aus, um die lokale Sicherheitsrichtlinie zu öffnen.

2. Erweitern Sie **Lokale Richtlinien**, und klicken Sie dann auf **Zuweisen von Benutzerrechten**.

3. Doppelklicken Sie im rechten Bereich auf **Annehmen der Clientidentität nach Authentifizierung**.

4. Klicken Sie auf **Benutzer oder Gruppe hinzufügen**, geben Sie **IIS_IURS** in **Geben Sie die zu verwendenden Objektnamen ein** ein, und klicken Sie dann auf **OK**.

5. Klicken Sie auf **OK**.

6. Starten Sie den Computer neu, und versuchen Sie dann erneut, eine Verbindung vom Gerät aus herzustellen.

### <a name="test-the-scep-server-url"></a>Testen der SCEP-Server-URL

Führen Sie die folgenden Schritte aus, um die im SCEP-Zertifikatprofil angegebene URL zu testen.

1. Bearbeiten Sie in Intune das SCEP-Zertifikatprofil, und kopieren Sie die Server-URL. Die URL sollte *https://contoso.com/certsrv/mscep/msecp.dll* ähneln.

2. Öffnen Sie einen Webbrowser, und navigieren Sie dann zu dieser SCEP-Server-URL. Das Ergebnis sollte wie folgt lauten: **HTTP-Fehler 403.0 – Verboten**. Dieses Ergebnis zeigt an, dass die URL ordnungsgemäß funktioniert.

   Wenn Sie diese Fehlermeldung nicht erhalten, wählen Sie den Link aus, der dem Fehler ähnelt, den Sie sehen, um eine problemspezifische Anleitung zu erhalten:
   - [Ich erhalte eine allgemeine NDES-Nachricht](#general-ndes-message)
   - [Ich erhalte die Fehlermeldung „HTTP-Fehler 503. Der Dienst ist nicht verfügbar“](#http-error-503)
   - [Ich erhalte die Fehlermeldung „GatewayTimeout“](#gatewaytimeout)
   - [Ich erhalte die Fehlermeldung „HTTP 414 Anforderungs-URI ist zu lang“](#http-414-request-uri-too-long)
   - [Ich erhalte die Fehlermeldung „Diese Seite kann nicht angezeigt werden“](#this-page-cant-be-displayed)
   - [Ich erhalte die Fehlermeldung „500 – Interner Serverfehler“](#internal-server-error)

#### <a name="general-ndes-message"></a>Allgemeine NDES-Nachricht

Wenn Sie zur SCEP-Server-URL navigieren, erhalten Sie die folgende NDES-Nachricht:

![SCEP-Server-URL](../protect/media/troubleshoot-scep-certificate-device-to-ndes/ndes-server-url-message.png)

- **Ursache:** Dieses Problem hängt in der Regel mit der Microsoft Intune Connector-Installation zusammen.

  „Mscep.dll“ ist eine ISAPI-Erweiterung, die eingehende Anforderungen abfängt und den HTTP 403-Fehler anzeigt, wenn sie ordnungsgemäß installiert ist.
  
  **Lösung**: Überprüfen Sie die Datei *SetupMsi.log*, um zu bestimmen, ob der Microsoft Intune Connector erfolgreich installiert wurde. Im folgenden Beispiel wurde die *Installation erfolgreich abgeschlossen* und *Installationserfolg oder Fehlerstatus: 0* weist auf eine erfolgreiche Installation hin:

  ```
  MSI (c) (28:54) [16:13:11:905]: Product: Microsoft Intune Connector -- Installation completed successfully.
  MSI (c) (28:54) [16:13:11:999]: Windows Installer installed the product. Product Name: Microsoft Intune Connector. Product Version: 6.1711.4.0. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.
  ```

  Wenn bei der Installation ein Fehler auftritt, entfernen Sie den Microsoft Intune-Connector, und installieren Sie ihn dann erneut.

#### <a name="http-error-503"></a>HTTP-Fehler 503

Wenn Sie die SCEP-Server-URL aufrufen, erhalten Sie die folgende Fehlermeldung:

![HTTP-Fehler 503. Der Dienst ist nicht verfügbar](../protect/media/troubleshoot-scep-certificate-device-to-ndes/service-unavailable.png)

Dieses Problem tritt normalerweise auf, weil der **SCEP**-Anwendungspool in IIS nicht gestartet wird. Öffnen Sie auf dem NDES-Server **IIS-Manager**, und wechseln Sie zu **Anwendungspools**. Suchen Sie den **SCEP**-Anwendungspool, und vergewissern Sie sich, dass er gestartet wurde.

Wenn der SCEP-Anwendungspool nicht gestartet wurde, überprüfen Sie das Anwendungsereignisprotokoll auf dem Server:

1. Führen Sie auf dem Gerät **eventvwr.msc** aus, um die **Ereignisanzeige** zu öffnen, und wechseln Sie zu **Windows-Protokolle** > **Anwendung**.

2. Suchen Sie nach einem Ereignis, das dem folgenden Beispiel ähnelt. Dies bedeutet, dass der Anwendungspool bei Empfang einer Anforderung abstürzt:

   ```
   Log Name:      Application
   Source:        Application Error
   Event ID:      1000
   Task Category: Application Crashing Events
   Level:         Error
   Keywords:      Classic
   Description: Faulting application name: w3wp.exe, version: 8.5.9600.16384, time stamp: 0x5215df96
   Faulting module name: ntdll.dll, version: 6.3.9600.18821, time stamp: 0x59ba86db
   Exception code: 0xc0000005
   ```

**Häufige Gründe für den Absturz eines Anwendungspools**:

- **Ursache 1**: Zertifikate von Zwischenzertifizierungsstellen (nicht selbstsignierte) sind im Zertifikatspeicher für vertrauenswürdige Stammzertifizierungsstellen des NDES-Servers vorhanden.

  **Lösung**: Entfernen Sie die Zertifikate von Zwischenzertifizierungsstellen aus dem Zertifikatspeicher für vertrauenswürdige Stammzertifizierungsstellen, und starten Sie den NDES-Server neu.
  
  Um alle Zertifikate von Zwischenzertifizierungsstellen im Zertifikatspeicher für vertrauenswürdige Stammzertifizierungsstellen zu identifizieren, führen Sie das folgende PowerShell-Cmdlet aus: `Get-Childitem -Path cert:\LocalMachine\root -Recurse | Where-Object {$_.Issuer -ne $_.Subject}`

  Wenn ein Zertifikat die gleichen Werte für **Ausgestellt für** und **Ausgestellt von** aufweist, handelt es sich um ein Stammzertifikat. Andernfalls handelt es sich um ein Zwischenzertifikat.

  Nachdem Sie Zertifikate entfernt und den Server neu gestartet haben, führen Sie das PowerShell-Cmdlet erneut aus, um sicherzustellen, dass keine Zertifikate von Zwischenzertifizierungsstellen mehr vorhanden sind. Wenn welche vorhanden sind, überprüfen Sie, ob eine Gruppenrichtlinie die Zertifikate von Zwischenzertifizierungsstellen auf den NDES-Server pusht. Wenn dies der Fall ist, schließen Sie den NDES-Server von der Gruppenrichtlinie aus, und entfernen Sie die Zertifikate von Zwischenzertifizierungsstellen erneut.

- **Ursache 2**: Die URLs in der Zertifikatssperrliste (Certificate Revocation List, CRL) sind für die Zertifikate, die vom Intune Certificate Connector verwendet werden, gesperrt oder nicht erreichbar.

  **Lösung**: Aktivieren Sie zusätzliche Protokollierung, um weitere Informationen zu sammeln:
  1. Öffnen Sie die Ereignisanzeige, klicken Sie auf **Ansicht**, und vergewissern Sie sich, dass die Option **Anzeigen von Analyse- und Debugprotokollen** aktiviert ist.
  2. Wechseln Sie zu **Anwendungs- und Dienstprotokolle** > **Microsoft** > **Windows** > **CAPI2** > **Betriebsbereit**, klicken Sie mit der rechten Maustaste auf **Betriebsbereit**, und klicken Sie dann auf **Protokoll aktivieren**.
  3. Nach Aktivieren der CAPI2-Protokollierung reproduzieren Sie das Problem, und untersuchen Sie das Ereignisprotokoll, um das Problem zu behandeln.

- **Ursache 3**: Die IIS-Berechtigung für **CertificateRegistrationSvc** hat die **Windows-Authentifizierung** aktiviert.

  **Lösung**: Aktivieren Sie **Anonyme Authentifizierung**, deaktivieren Sie **Windows-Authentifizierung**, und starten Sie den NDES-Server neu.

  ![IIS-Berechtigungen](../protect/media/troubleshoot-scep-certificate-device-to-ndes/iis-permissions.png)

#### <a name="gatewaytimeout"></a>GatewayTimeout

Wenn Sie die SCEP-Server-URL aufrufen, erhalten Sie die folgende Fehlermeldung:

![GatewayTimeout-Fehler](../protect/media/troubleshoot-scep-certificate-device-to-ndes/gateway-timeout.png)

- **Ursache:** Der **Microsoft AAD-Anwendungsproxy-Connector**-Dienst wurde nicht gestartet.

  **Lösung**:  Führen Sie **services.msc** aus, und stellen Sie sicher, dass der **Microsoft AAD-Anwendungsproxy-Connector**-Dienst ausgeführt wird und für **Starttyp** die Option **Automatisch** festgelegt ist.

#### <a name="http-414-request-uri-too-long"></a>HTTP 414 Anforderungs-URI ist zu lang

Wenn Sie die SCEP-Server-URL aufrufen, erhalten Sie die folgende Fehlermeldung: `HTTP 414 Request-URI Too Long`

- **Ursache:** Die IIS-Anforderungsfilterung ist nicht für die Unterstützung der langen URLs (Abfragen) konfiguriert, die der NDES-Dienst empfängt. Diese Unterstützung wird konfiguriert, wenn Sie den [NDES-Dienst so konfigurieren](certificates-scep-configure.md#configure-the-ndes-service), dass er mit Ihrer Infrastruktur für SCEP verwendet werden kann.

- **Lösung**: Konfigurieren Sie die Unterstützung langer URLs.

  1. Öffnen Sie auf dem NDES-Server den IIS-Manager, und wählen Sie **Standardwebsite** > **Anforderungsfilterung** > **Featureeinstellung bearbeiten** aus, um die Seite **Einstellungen für die Anforderungsfilterung bearbeiten** zu öffnen.

  2. Konfigurieren Sie die folgenden Einstellungen:
     - **Maximale URL-Länge (Bytes)**  = 65534
     - **Maximale Länge einer Abfragezeichenfolge (Bytes)**  = 65534

  3. Klicken Sie auf **OK**, um diese Konfiguration zu speichern und den IIS-Manager zu schließen.

  4. Überprüfen Sie diese Konfiguration, indem Sie prüfen, ob der folgende Registrierungsschlüssel die entsprechenden Werte aufweist:

     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters

     Die folgenden Werte werden als DWORD-Einträge festgelegt:
     - Name: **MaxFieldLength** mit einem Dezimalwert von **65534**
     - Name: **MaxRequestBytes** mit einem Dezimalwert von **65534**

  5. Starten Sie den NDES-Server neu.

#### <a name="this-page-cant-be-displayed"></a>Diese Seite kann nicht angezeigt werden

Sie haben den Azure AD-Anwendungsproxy konfiguriert. Wenn Sie die SCEP-Server-URL aufrufen, erhalten Sie die folgende Fehlermeldung:

`This page can't be displayed`

- **Ursache:** Dieses Problem tritt auf, wenn die externe SCEP-URL in der Anwendungsproxykonfiguration falsch ist. Ein Beispiel für diese URl ist https://contoso.com/certsrv/mscep/mscep.dll.

  **Lösung**: Verwenden Sie die Standarddomäne *yourtenant.msappproxy.net* in der Anwendungsproxykonfiguration für die externe SCEP-URL.

#### <a name="internal-server-error"></a>500 – Interner Serverfehler

Wenn Sie die SCEP-Server-URL aufrufen, erhalten Sie die folgende Fehlermeldung:

![500 – Interner Serverfehler](../protect/media/troubleshoot-scep-certificate-device-to-ndes/500-internal-server-error.png)

- **Ursache 1**: Das NDES-Dienstkonto ist gesperrt oder sein Kennwort ist abgelaufen.

  **Lösung**: Entsperren Sie das Konto, oder setzen Sie das Kennwort zurück.

- **Ursache 2**: Die MSCEP-RA-Zertifikate sind abgelaufen.

  **Lösung**: Wenn die MSCEP-RA-Zertifikate abgelaufen sind, installieren Sie die NDES-Rolle neu, oder fordern Sie neue Zertifikate für die CEP-Verschlüsselung und den Exchange-Registrierungs-Agent (Offlineanforderung) an.

  Führen Sie die folgenden Schritte aus, um neue Zertifikate anzufordern:

  1. Öffnen Sie in der Zertifizierungsstelle oder ausgebenden Zertifizierungsstelle die Zertifikatvorlagen-MMC. Stellen Sie sicher, dass der angemeldete Benutzer und der NDES-Server über die Berechtigungen **Lesen** und **Registrieren** für die Zertifikatvorlagen für CEP-Verschlüsselung und Exchange-Registrierungs-Agent (Offlineanforderung) verfügen.

  2. Überprüfen Sie die abgelaufenen Zertifikate auf dem NDES-Server, und kopieren Sie die **Antragsteller**-Informationen aus dem Zertifikat.

  3. Öffnen Sie die Zertifikate-MMC für **Computerkonto**.

  4. Erweitern Sie **Persönlich**, klicken Sie mit der rechten Maustaste auf **Zertifikate**, und wählen Sie dann **Alle Aufgaben** > **Neues Zertifikat anfordern** aus.

  5. Wählen Sie auf der Seite **Zertifikat anfordern** die Option **CEP-Verschlüsselung** aus, und klicken Sie dann auf **Es werden zusätzliche Informationen für diese Zertifikatsregistrierung benötigt. Klicken Sie hier, um die Einstellungen zu konfigurieren**.

     ![Auswählen der CEP-Verschlüsselung](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-scep-encryption.png)

  6. Klicken Sie in **Zertifikateigenschaften** auf die Registerkarte **Antragsteller**, tragen Sie für den **Antragstellernamen** die Informationen ein, die Sie in Schritt 2 gesammelt haben, klicken Sie auf **Hinzufügen** und dann auf **OK**.

  7. Schließen Sie die Zertifikatregistrierung ab.

  8. Öffnen Sie die Zertifikate-MMC für **Eigenes Benutzerkonto**.

     Wenn Sie sich für das Zertifikat für den Exchange-Registrierungs-Agent (Offlineanforderung) registrieren, muss dies im Benutzerkontext erfolgen. Der Grund hierfür ist, dass als **Typ des Antragstellers** für diese Zertifikatvorlage **Benutzer** festgelegt ist.

  9. Erweitern Sie **Persönlich**, klicken Sie mit der rechten Maustaste auf **Zertifikate**, und wählen Sie dann **Alle Aufgaben** > **Neues Zertifikat anfordern** aus.

  10. Wählen Sie auf der Seite **Zertifikat anfordern** die Option **Exchange-Registrierungs-Agent (Offlineanforderung)** aus, und klicken Sie dann auf **Es werden zusätzliche Informationen für diese Zertifikatsregistrierung benötigt. Klicken Sie hier, um die Einstellungen zu konfigurieren**.

      ![Auswählen des Exchange-Registrierungs-Agent](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-exchange-enrollment-agent.png)

  11. Klicken Sie in **Zertifikateigenschaften** auf die Registerkarte **Antragsteller**, tragen Sie für den **Antragstellernamen** die Informationen ein, die Sie in Schritt 2 gesammelt haben, und klicken Sie auf **Hinzufügen**.

      ![Zertifikateigenschaften](../protect/media/troubleshoot-scep-certificate-device-to-ndes/certificate-properties.png)

      Wählen Sie die Registerkarte **Privater Schlüssel** und dann **Privaten Schlüssel exportierbar machen** aus, und klicken Sie dann auf **OK**.

      ![Privater Schlüssel](../protect/media/troubleshoot-scep-certificate-device-to-ndes/private-key.png)

  12. Schließen Sie die Zertifikatregistrierung ab.

  13. Exportieren Sie das Zertifikat für den Exchange-Registrierungs-Agent (Offlineanforderung) aus dem Zertifikatspeicher des aktuellen Benutzers. Wählen Sie im Assistenten zum Exportieren von Zertifikaten **Ja, privaten Schlüssel exportieren** aus.

  14. Importieren Sie das Zertifikat in den Zertifikatsspeicher des lokalen Computers.

  15. Führen Sie in der Zertifikate-MMC folgende Aktion für jedes neue Zertifikat aus:

      Klicken Sie mit der rechten Maustaste auf das Zertifikat, klicken Sie auf **Alle Aufgaben** > **Private Schlüssel verwalten**, und fügen Sie die Berechtigung **Lesen** dem NDES-Dienstkonto hinzu.

  16. Führen Sie den **iisreset**-Befehl aus, um IIS neu zu starten.

## <a name="next-steps"></a>Nächste Schritte

Wenn das Gerät den NDES-Server erfolgreich erreicht hat, um die Zertifikatanforderung zu präsentieren, besteht der nächste Schritt darin, das [Intune Certificate Connector-Richtlinienmodul](troubleshoot-scep-certificate-ndes-policy-module.md) zu überprüfen.
