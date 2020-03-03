---
title: Behandeln von Problemen bei der Übermittlung von Zertifikaten an Geräte bei Verwendung von SCEP mit Microsoft Intune | Microsoft-Dokumentation
description: Behandeln von Problemen bei der Übermittlung eines Zertifikats an ein Gerät von der Zertifizierungsstelle bei Verwendung von SCEP-Zertifikatprofilen mit Intune zum Bereitstellen von Zertifikaten.
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
ms.openlocfilehash: 40075ad3c90f9ce5131d88780d15eec5c258e276
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515253"
---
# <a name="troubleshoot-the-delivery-of-certificates-provisioned-by-scep-to-devices-in-microsoft-intune"></a>Behandeln von Problemen bei der Übermittlung von Zertifikaten, die von SCEP auf Geräten in Microsoft Intune bereitgestellt werden

Verwenden Sie die Informationen in diesem Artikel, um die Übermittlung von Zertifikaten an Geräte zu untersuchen, wenn Sie das Simple Certificate Enrollment-Protokoll (SCEP) zum Bereitstellen von Zertifikaten in Intune verwenden. Nachdem der NDES-Server (Network Device Enrollment Service, Registrierungsdienst für Netzwerkgeräte) das angeforderte Zertifikat für ein Gerät von der Zertifizierungsstelle (Certification Authority, CA) empfangen hat, gibt er das Zertifikat an das Gerät zurück.

Dieser Artikel bezieht sich auf Schritt 5 des [SCEP-Kommunikationsworkflows](troubleshoot-scep-certificate-profiles.md), Übermittlung des Zertifikats an das Gerät, das die Zertifikatanforderung gesendet hat.

## <a name="review-the-certification-authority"></a>Überprüfen der Zertifizierungsstelle

Wenn die Zertifizierungsstelle das Zertifikat ausgestellt hat, wird ein Eintrag ähnlich dem folgenden Beispiel für die Zertifizierungsstelle angezeigt:

![Beispiel für ausgestellte Zertifikate](../protect/media/troubleshoot-scep-certificate-delivery/certificate-authority.png)

## <a name="review-the-device"></a>Überprüfen des Geräts

### <a name="android"></a>Android

Für vom Geräteadministrator registrierte Geräte wird eine Benachrichtigung angezeigt, die der folgenden Abbildung ähnelt, in der Sie aufgefordert werden, das Zertifikat zu installieren:

![Android-Benachrichtigung](../protect/media/troubleshoot-scep-certificate-delivery/android-notification.png)

Für Android Enterprise oder Samsung Knox erfolgt die Zertifikatinstallation automatisch und unbeaufsichtigt.

Wenn Sie ein installiertes Zertifikat unter Android anzeigen möchten, verwenden Sie eine Drittanbieter-App für die Zertifikatanzeige.

Sie können auch das [Geräte-OMADM-Protokoll](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices) überprüfen. Suchen Sie nach bei der Installation von Zertifikaten protokollierten Einträgen, die den folgenden ähneln:

**Ein Stammzertifikat:**

```
2018-02-27T04:50:52.1890000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        9    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALL_REQUESTED
2018-02-27T04:53:31.1300000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        0    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T04:53:32.0390000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595       14    Root cert '17…' state changed from CERT_INSTALLING to CERT_INSTALL_SUCCESS
```

**Über SCEP bereitgestelltes Zertifikat**

```
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    There are 1 requests
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    Trying to enroll certificate request: ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787
2018-02-27T05:16:20.6150000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:20.6530000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:21.7460000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.7890000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:28.0340000    VERB    Event     org.jscep.transaction.EnrollmentTransaction    18327       10    Response: org.jscep.message.CertRep@3150777b[failInfo=<null>,pkiStatus=SUCCESS,recipientNonce=Nonce [GUID],messageData=org.spongycastle.cms.CMSSignedData@27cc8998,messageType=CERT_REP,senderNonce=Nonce [GUID],transId=TRANSID]
2018-02-27T05:16:28.2440000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       10    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ENROLLED to CERT_INSTALL_REQUESTED
2018-02-27T05:18:44.9820000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327        0    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T05:18:45.3460000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       14    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALLING to CERT_ACCESS_REQUESTED
2018-02-27T05:20:15.3520000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       21    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ACCESS_REQUESTED to CERT_ACCESS_GRANTED
```

### <a name="iosipados"></a>iOS/iPadOS

Auf dem iOS-oder iPadOS-Gerät können Sie das Zertifikat unter dem Geräteverwaltungsprofil anzeigen. Um weitere Informationen zu installierten Zertifikaten zu erhalten, führen Sie einen Drilldown durch.

![iOS-Zertifikat](../protect/media/troubleshoot-scep-certificate-delivery/ios-certificate.png)

Im [iOS-Debugprotokoll](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices) finden Sie auch Einträge, die den folgenden ähneln:

```
Debug 18:30:53.691033 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\  
Debug 18:30:54.640644 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
Debug 18:30:55.487908 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQG 
Debug 18:30:57.285730 -0500 profiled Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 in domain ManagedProfileToManagingProfile to system\ 
Default 18:30:57.320616 -0500 profiled Profile \'93www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295\'94 installed.\ 
```

### <a name="windows"></a>Windows

Überprüfen Sie auf dem Windows-Gerät, ob das Zertifikat übermittelt wurde:

- Führen Sie **eventvwr.msc** aus, um die Ereignisanzeige zu öffnen. Navigieren Sie zu **Anwendungs- und Dienstprotokolle** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin**, und suchen Sie nach **Ereignis 39**. Dieses Ereignis sollte eine allgemeine Beschreibung von Folgendem enthalten: **SCEP: Zertifikat wurde erfolgreich installiert.**

   ![Ereignis 39 im Windows-Anwendungsprotokoll](../protect/media/troubleshoot-scep-certificate-delivery/device-app-log.png)

Um das Zertifikat auf dem Gerät anzuzeigen, führen Sie **certmgr.msc** aus, um die Zertifikate-MMC zu öffnen und zu überprüfen, ob die Stamm- und SCEP-Zertifikate ordnungsgemäß im persönlichen Informationsspeicher auf dem Gerät installiert sind:

   1. Wechseln Sie zu **Zertifikate (lokaler Computer)** > **Vertrauenswürdige Stammzertifizierungsstellen** > **Zertifikate**, und vergewissern Sie sich, dass das Stammzertifikat der Zertifizierungsstelle vorhanden ist. Die Werte für *Ausgestellt für* und *Ausgestellt von* sind identisch.
   2. Wechseln Sie in der Zertifikate-MMC zu **Zertifikate – Aktueller Benutzer** > **Persönlich** > **Zertifikate**, und vergewissern Sie sich, dass das angeforderte Zertifikat vorhanden ist, wobei *Ausgestellt von* dem Namen der Zertifizierungsstelle entspricht.

## <a name="troubleshoot-failures"></a>Beheben von Fehlern

### <a name="android"></a>Android

Um Probleme mit diesem Schritt zu behandeln, überprüfen Sie die Fehler, die im OMA DM-Protokoll protokolliert werden.

### <a name="iosipados"></a>iOS/iPadOS

Um Probleme mit diesem Schritt zu behandeln, überprüfen Sie die Fehler, die im Gerätedebugprotokoll protokolliert werden.

### <a name="windows"></a>Windows

Um Probleme zu behandeln, die damit in Zusammenhang stehen, dass das Zertifikat nicht auf dem Gerät installiert wird, suchen Sie im Windows-Ereignisprotokoll nach Fehlern:

- Führen Sie auf dem Gerät **eventvwr.msc** aus, um die Ereignisanzeige zu öffnen, und navigieren Sie dann zu **Anwendungs- und Dienstprotokolle** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin**.

Fehler bei der Übermittlung und Installation des Zertifikats auf dem Gerät stehen in der Regel in Zusammenhang mit Windows-Vorgängen und nicht mit Intune.

## <a name="next-steps"></a>Nächste Schritte

Wenn das Zertifikat erfolgreich auf dem Gerät bereitgestellt wird, Intune jedoch keinen Erfolg meldet, finden Sie weitere Informationen zum Behandeln von Problemen mit der Berichterstellung unter [Problembehandlung bei der NDES-Berichterstellung von Zertifikatbereitstellungen in Microsoft Intune](troubleshoot-scep-certificate-reporting.md).
