---
title: Benutzerdefinierte Konfigurationen für Microsoft Intune-VPN-Profile
description: Verwenden Sie benutzerdefinierte Konfigurationen, um VPN-Profile in Intune zu erstellen.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 512bd38802dbb97a74d3d19d74a7d5086784d327
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="custom-configurations-for-microsoft-intune-vpn-profiles"></a>Benutzerdefinierte Konfigurationen für Microsoft Intune-VPN-Profile

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="create-a-custom-configuration"></a>Erstellen einer benutzerdefinierten Konfiguration
Sie können benutzerdefinierte Intune-Konfigurationsrichtlinien verwenden, um VPN-Profile für folgende Geräte zu erstellen:

* Geräte unter Android 4 und höher
* Android for Work-Geräte
* Registrierte Geräte unter Windows 8.1 und höher
* Geräte unter Windows Phone 8.1 und höher
* Registrierte Geräte unter Windows 10 Desktop
* Geräte unter Windows 10 Mobile

Dieser Richtlinientyp kann hilfreich sein, wenn die standardmäßigen Intune-VPN-Richtlinien nicht die Einstellungen enthalten, die Sie verwenden möchten.

## <a name="to-create-a-custom-configuration-policy"></a>So erstellen Sie eine benutzerdefinierte Konfigurationsrichtlinie:

1. Wählen Sie in der [Intune-Verwaltungskonsole](https://manage.microsoft.com) die Optionen **Richtlinie** > **Richtlinie hinzufügen** > *Plattform erweitern* > **Benutzerdefinierte Konfiguration** > **Richtlinie erstellen** aus.
2. Geben Sie einen Namen für die Richtlinie ein.
3. Wählen Sie für jede URI-Einstellung, die Sie festlegen möchten, die Option **Hinzufügen** aus, und geben Sie die erforderlichen Informationen an. Beispiel:

   ![Dialogfeld „Benutzerdefinierte VPN-Profilkonfiguration“](./media/Intune_Add_VPN_URI.png)

4. Nachdem Sie alle URI-Einstellungen eingegeben haben, wählen Sie **Richtlinie speichern** aus, und stellen Sie die Richtlinie anschließend bereit.

[Stellen Sie die Richtlinie dann wie immer bereit](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy).

## <a name="example-uri-settings"></a>Beispiel für URI-Einstellungen

Diese Einstellungen können verwendet werden, um eine benutzerdefinierte Konfiguration für ein VPN in einem fiktiven Unternehmen namens Contoso zu erstellen.
Details zu allen verfügbaren Einstellungen finden Sie unter [VPNv2 CSP](https://msdn.microsoft.com/library/windows/hardware/dn914776.aspx).

**Natives Contoso-VPN (IKEv2):**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

**vpn.contoso.com**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

**Ikev2<br />** ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

**SplitTunnel**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

**Eap**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration
``` xml
<EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
   <EapMethod>
      <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
      <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
      <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
      <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
   </EapMethod>
   <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
      <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
         <Type>13</Type>
         <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
            <CredentialsSource>
               <CertificateStore>
                  <SimpleCertSelection>true</SimpleCertSelection>
               </CertificateStore>
            </CredentialsSource>
            <ServerValidation>
               <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
               <ServerNames></ServerNames>
            </ServerValidation>
            <DifferentUsername>false</DifferentUsername>
            <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </PerformServerValidation>
            <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </AcceptServerName>
         </EapType>
      </Eap>
   </Config>
</EapHostConfig>
```
**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal**<br />
True

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials**<br />
1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address**<br />
10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize**<br />
8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn**<br />
true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id**<br />
%PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

Fragen zur Verwendung dieser Einstellungen und weitere Details zu ihrer Funktion finden Kunden in der [Dokumentation des Konfigurationsdienstanbieters](https://msdn.microsoft.com/library/windows/hardware/dn914776(v=vs.85).aspx).

## <a name="uri-settings-for-android-per-app-vpn-on-pulsesecure"></a>URI-Einstellungen für Android pro App VPN auf PulseSecure
### <a name="custom-uri-for-package-list"></a>BENUTZERDEFINIERTE URI FÜR DIE PAKETLISTE
-  Datentyp = String
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/Name/PackageList
-  Wert = durch Trennzeichen getrennte Paketliste.
   - Trennzeichen: Semikolon (;), Doppelpunkt (:), Komma (,), senkrechter Strich (|)

Beispiele:
- com.android.chrome
- com.android.chrome;com.android.browser

### <a name="custom-uri-for-mode-optional"></a>BENUTZERDEFINIERTE URI FÜR MODUS (OPTIONAL)
- Datentyp = String
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode

> Hinweise
> - Verwenden Sie den gleichen *Namen*, dem Sie dem benutzerdefinierten Profil zugewiesen haben.
> - Mögliche Werte: *GLOBAL*, *WHITELIST*, *BLACKLIST*
> - Der Standardlist ist *GLOBAL*, wenn keine PackageList angegeben ist (Abwärtskompatibilität mit systemweiten Profilen)
> - Standardmäßig *WHITELIST*, wenn eine PackageList angegeben ist


### <a name="see-also"></a>Siehe auch
[VPN-Verbindungen in Microsoft Intune](vpn-connections-in-microsoft-intune.md)
