---
title: Behandeln von Problemen bei der Bereitstellung von SCEP-Zertifikatprofilen für Geräte mit Microsoft Intune | Microsoft-Dokumentation
description: Behandeln von Problemen beim Senden eines SCEP-Zertifikatprofils an ein Gerät mit Intune.
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
ms.openlocfilehash: 3dae74321b6825a1b94551addfd7621450fd8ae4
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916044"
---
# <a name="troubleshoot-deployment-of-a-scep-certificate-profile-to-devices-in-microsoft-intune"></a>Behandeln von Problemen bei der Bereitstellung von SCEP-Zertifikatprofilen für Geräte in Microsoft Intune

Verwenden Sie die folgenden Informationen zur Problembehandlung bei der Bereitstellung von Simple Certificate Enrollment-Protokoll-Zertifikatprofilen (SCEP) mit Intune.

Dieser Artikel verweist auf Schritt 1 der [Übersicht zur Problembehandlung bei SCEP-Zertifikatprofilen mit Microsoft Intune](troubleshoot-scep-certificate-profiles.md).


## <a name="android"></a>Android

SCEP-Zertifikatprofile für Android werden als SyncML auf das Gerät heruntergeladen und im [OMADM-Protokoll](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices) protokolliert.

### <a name="validate-that-the-android-device-was-sent-the-policy"></a>Überprüfen, ob die Richtlinie an das Android-Gerät gesendet wurde

Wenn Sie überprüfen möchten, ob ein Profil an das erwartete Gerät gesendet wurde, navigieren Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) zu **Problembehandlung und Support** > **Problembehandlung**.  Legen Sie im Fenster *Problembehandlung* die **Zuweisungen** auf **Konfigurationsprofile** fest, und überprüfen Sie dann die folgenden Konfigurationen:

1. Geben Sie einen Benutzer an, der das SCEP-Zertifikatprofil erhalten soll.

2. Überprüfen Sie die Gruppenmitgliedschaft der Benutzer, um sicherzustellen, dass sie in der Sicherheitsgruppe sind, die Sie mit dem SCEP-Zertifikatprofil verwendet haben.

3. Überprüfen Sie, wann das Gerät zuletzt in Intune eingecheckt wurde.

![Überprüfen der Richtlinie](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-android.png)

### <a name="validate-the-policy-reached-the-android-device"></a>Überprüfen, ob die Richtlinie das Android-Gerät erreicht hat

Überprüfen Sie das [Geräte-OMADM-Protokoll](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices). Suchen Sie nach Einträgen, die protokolliert wurden, als das Gerät das Profil von Intune erhielt, die den folgenden ähneln:

```
Time    VERB    Event     com.microsoft.omadm.syncml.SyncmlSession     9595        9    <?xml version="1.0" encoding="utf-8"?><SyncML xmlns="SYNCML:SYNCML1.2"><SyncHdr><VerDTD>1.2</VerDTD><VerProto>DM/1.2</VerProto><SessionID>1</SessionID><MsgID>6</MsgID><Target><LocURI>urn:uuid:UUID</LocURI></Target><Source><LocURI>https://a.manage.microsoft.com/devicegatewayproxy/AndroidHandler.ashx</LocURI></Source><Meta><MaxMsgSize xmlns="syncml:metinf">524288</MaxMsgSize></Meta></SyncHdr><SyncBody><Status><CmdID>1</CmdID><MsgRef>6</MsgRef><CmdRef>0</CmdRef><Cmd>SyncHdr</Cmd><Data>200</Data></Status><Replace><CmdID>2</CmdID><Item><Target><LocURI>./Vendor/MSFT/Scheduler/IntervalDurationSeconds</LocURI></Target><Meta><Format xmlns="syncml:metinf">int</Format><Type xmlns="syncml:metinf">text/plain</Type></Meta><Data>28800</Data></Item></Replace><Replace><CmdID>3</CmdID><Item><Target><LocURI>./Vendor/MSFT/EnterpriseAppManagement/EnterpriseIDs</LocURI></Target><Data>contoso.onmicrosoft.com</Data></Item></Replace><Exec><CmdID>4</CmdID><Item><Target><LocURI>./Vendor/MSFT/EnterpriseAppManagement/EnterpriseApps/ClearNotifications</LocURI></Target></Item></Exec><Add><CmdID>5</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/Root/{GUID}/EncodedCertificate</LocURI></Target><Data>Data</Data></Item></Add><Add><CmdID>6</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/Enroll/ModelName=AC_51…%2FLogicalName_39907…%3BHash=-1518303401/Install</LocURI></Target><Meta><Format xmlns="syncml:metinf">xml</Format><Type xmlns="syncml:metinf">text/plain</Type></Meta><Data>&lt;CertificateRequest&gt;&lt;ConfigurationParametersDocument&gt;&amp;lt;ConfigurationParameters xmlns="http://schemas.microsoft.com/SystemCenterConfigurationManager/2012/03/07/CertificateEnrollment/ConfigurationParameters"&amp;gt;&amp;lt;ExpirationThreshold&amp;gt;20&amp;lt;/ExpirationThreshold&amp;gt;&amp;lt;RetryCount&amp;gt;3&amp;lt;/RetryCount&amp;gt;&amp;lt;RetryDelay&amp;gt;1&amp;lt;/RetryDelay&amp;gt;&amp;lt;TemplateName /&amp;gt;&amp;lt;SubjectNameFormat&amp;gt;{ID}&amp;lt;/SubjectNameFormat&amp;gt;&amp;lt;SubjectAlternativeNameFormat&amp;gt;{ID}&amp;lt;/SubjectAlternativeNameFormat&amp;gt;&amp;lt;KeyStorageProviderSetting&amp;gt;0&amp;lt;/KeyStorageProviderSetting&amp;gt;&amp;lt;KeyUsage&amp;gt;32&amp;lt;/KeyUsage&amp;gt;&amp;lt;KeyLength&amp;gt;2048&amp;lt;/KeyLength&amp;gt;&amp;lt;HashAlgorithms&amp;gt;&amp;lt;HashAlgorithm&amp;gt;SHA-1&amp;lt;/HashAlgorithm&amp;gt;&amp;lt;HashAlgorithm&amp;gt;SHA-2&amp;lt;/HashAlgorithm&amp;gt;&amp;lt;/HashAlgorithms&amp;gt;&amp;lt;NDESUrls&amp;gt;&amp;lt;NDESUrl&amp;gt;https://breezeappproxy-contoso.msappproxy.net/certsrv/mscep/mscep.dll&amp;lt;/NDESUrl&amp;gt;&amp;lt;/NDESUrls&amp;gt;&amp;lt;CAThumbprint&amp;gt;{GUID}&amp;lt;/CAThumbprint&amp;gt;&amp;lt;ValidityPeriod&amp;gt;2&amp;lt;/ValidityPeriod&amp;gt;&amp;lt;ValidityPeriodUnit&amp;gt;Years&amp;lt;/ValidityPeriodUnit&amp;gt;&amp;lt;EKUMapping&amp;gt;&amp;lt;EKUMap&amp;gt;&amp;lt;EKUName&amp;gt;Client Authentication&amp;lt;/EKUName&amp;gt;&amp;lt;EKUOID&amp;gt;1.3.6.1.5.5.7.3.2&amp;lt;/EKUOID&amp;gt;&amp;lt;/EKUMap&amp;gt;&amp;lt;/EKUMapping&amp;gt;&amp;lt;/ConfigurationParameters&amp;gt;&lt;/ConfigurationParametersDocument&gt;&lt;RequestParameters&gt;&lt;CertificateRequestToken&gt;PENlcnRFbn... Hash: 1,010,143,298&lt;/CertificateRequestToken&gt;&lt;SubjectName&gt;CN=name&lt;/SubjectName&gt;&lt;Issuers&gt;CN=FourthCoffee CA; DC=fourthcoffee; DC=local&lt;/Issuers&gt;&lt;SubjectAlternativeName&gt;&lt;SANs&gt;&lt;SAN NameFormat="ID" AltNameType="2" OID="{OID}"&gt;&lt;/SAN&gt;&lt;SAN NameFormat="ID" AltNameType="11" OID="{OID}"&gt;john@contoso.onmicrosoft.com&lt;/SAN&gt;&lt;/SANs&gt;&lt;/SubjectAlternativeName&gt;&lt;NDESUrl&gt;https://breezeappproxy-contoso.msappproxy.net/certsrv/mscep/mscep.dll&lt;/NDESUrl&gt;&lt;/RequestParameters&gt;&lt;/CertificateRequest&gt;</Data></Item></Add><Get><CmdID>7</CmdID><Item><Target><LocURI>./Vendor/MSFT/CertificateStore/SCEP</LocURI></Target></Item></Get><Add><CmdID>8</CmdID><Item><Target><LocURI>./Vendor/MSFT/GCM</LocURI></Target><Data>Data</Data></Item></Add><Replace><CmdID>9</CmdID><Item><Target><LocURI>./Vendor/MSFT/GCM</LocURI></Target><Data>Data</Data></Item></Replace><Get><CmdID>10</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr</LocURI></Target></Item></Get><Get><CmdID>11</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr/CacheVersion</LocURI></Target></Item></Get><Get><CmdID>12</CmdID><Item><Target><LocURI>./Vendor/MSFT/NodeCache/SCConfigMgr/ChangedNodes</LocURI></Target></Item></Get><Get><CmdID>13</CmdID><Item><Target><LocURI>./DevDetail/Ext/Microsoft/LocalTime</LocURI></Target></Item></Get><Get><CmdID>14</CmdID><Item><Target><LocURI>./Vendor/MSFT/DeviceLock/DevicePolicyManager/IsActivePasswordSufficient</LocURI></Target></Item></Get><Get><CmdID>15</CmdID><Item><Target><LocURI>./Vendor/MSFT/WorkProfileLock/DevicePolicyManager/IsActivePasswordSufficient</LocURI></Target></Item></Get><Final /></SyncBody></SyncML>
```

Beispiele für Schlüsseleinträge:

- `ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c%3BHash=-1518303401`
- `NDESUrls&amp;gt;&amp;lt;NDESUrl&amp;gt;https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll&amp;lt;/NDESUrl&amp;gt;&amp;lt;/NDESUrls`

## <a name="ios-and-ipados"></a>iOS und iPadOS

### <a name="validate-that-the-ios-or-ipados-device-was-sent-the-policy"></a>Überprüfen, ob die Richtlinie an das iOS- oder iPadOS-Gerät gesendet wurde

Wenn Sie überprüfen möchten, ob ein Profil an das erwartete Gerät gesendet wurde, navigieren Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) zu **Problembehandlung und Support** > **Problembehandlung**.  Legen Sie im Fenster *Problembehandlung* die **Zuweisungen** auf **Konfigurationsprofile** fest, und überprüfen Sie dann die folgenden Konfigurationen:

1. Geben Sie einen Benutzer an, der das SCEP-Zertifikatprofil erhalten soll.

2. Überprüfen Sie die Gruppenmitgliedschaft der Benutzer, um sicherzustellen, dass sie in der Sicherheitsgruppe sind, die Sie mit dem SCEP-Zertifikatprofil verwendet haben.

3. Überprüfen Sie, wann das Gerät zuletzt in Intune eingecheckt wurde.

![Überprüfen der Richtlinie](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-ios.png)

### <a name="validate-the-policy-reached-the-ios-or-ipados-device"></a>Überprüfen, ob die Richtlinie das iOS- oder iPadOS-Gerät erreicht hat

Überprüfen Sie das [Gerätedebugprotokoll](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices). Suchen Sie nach Einträgen, die protokolliert wurden, als das Gerät das Profil von Intune erhielt, die den folgenden ähneln:

```
debug    18:30:54.638009 -0500    profiled    Adding dependent ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 to parent 636572740000000000000012 in domain PayloadDependencyDomainCertificate to system\
```

Beispiele für Schlüsseleinträge:

- `ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295`
- `PayloadDependencyDomainCertificate`

## <a name="windows"></a>Windows

### <a name="validate-that-the-windows-device-was-sent-the-policy"></a>Überprüfen, ob die Richtlinie an das Windows-Gerät gesendet wurde

Wenn Sie überprüfen möchten, ob das Profil an das erwartete Gerät gesendet wurde, navigieren Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431)[Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) zu **Problembehandlung und Support** > **Problembehandlung**.  Legen Sie im Fenster *Problembehandlung* die **Zuweisungen** auf **Konfigurationsprofile** fest, und überprüfen Sie dann die folgenden Konfigurationen:

1. Geben Sie einen Benutzer an, der das SCEP-Zertifikatprofil erhalten soll.

2. Überprüfen Sie die Gruppenmitgliedschaft der Benutzer, um sicherzustellen, dass sie in der Sicherheitsgruppe sind, die Sie mit dem SCEP-Zertifikatprofil verwendet haben.

3. Überprüfen Sie, wann das Gerät zuletzt in Intune eingecheckt wurde.

![Überprüfen der Richtlinie](../protect/media/troubleshoot-scep-certificate-profile-deployment/validate-policy-windows.png)

### <a name="validate-the-policy-reached-the-windows-device"></a>Überprüfen, ob die Richtlinie das Windows-Gerät erreicht hat

Der Eingang der Richtlinie für das Profil wird im Protokoll *DeviceManagement-Enterprise-Diagnostics-Provider* > **Admin** eines Windows-Geräts mit der Ereignis-ID **306** protokolliert. 

So öffnen Sie das Protokoll:

1. Führen Sie auf dem Gerät **eventvwr.msc** aus, um die Windows-Ereignisanzeige zu öffnen.

2. Erweitern Sie **Anwendungs- und Dienstprotokolle** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin**.

3. Suchen Sie nach Ereignis **306**, das dem folgenden Beispiel ähnelt:

   ```
   Event ID:      306
   Task Category: None
   Level:         Information
   User:          SYSTEM
   Computer:      <Computer Name>
   Description:
   SCEP: CspExecute for UniqueId : (ModelName_<ModelName>_LogicalName_<LogicalName>_Hash_<Hash>) InstallUserSid : (<UserSid>) InstallLocation : (user) NodePath : (clientinstall)  KeyProtection: (0x2) Result : (Unknown Win32 Error code: 0x2ab0003).
   ```

   Der Fehlercode **0x2ab0003** wird in **DM_S_ACCEPTED_FOR_PROCESSING** übersetzt.

   Ein Fehlercode über einen nicht erfolgreichen Verlauf gibt möglicherweise Aufschluss über das zugrunde liegende Problem.

## <a name="next-steps"></a>Nächste Schritte

Wenn das Profil das Gerät erreicht, besteht der nächste Schritt darin, die [Kommunikation zwischen Gerät und NDES-Server](troubleshoot-scep-certificate-device-to-ndes.md) zu überprüfen.
