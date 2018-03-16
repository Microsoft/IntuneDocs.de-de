---
title: "Erstellen eines WLAN-Profils über einen vorinstallierten Schlüssel"
titleSuffix: Microsoft Intune
description: "Verwenden Sie ein benutzerdefiniertes Intune-Profil, um ein WLAN-Profil mit einem vorinstallierten Schlüssel zu erstellen."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8229ac82e6854d75f569b7bbf04dd2f5e14856c7
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="use-a-custom-device-profile-to-create-a-wi-fi-profile-with-a-pre-shared-key"></a>Verwenden Sie ein benutzerdefiniertes Geräteprofil zum Erstellen eines WLAN-Profils mit einem vorinstallierten Schlüssel
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Erfahren Sie, wie Sie mithilfe von **benutzerdefinierten Geräteprofilen** in Intune ein WLAN-Profil mit einem vorinstallierten Schlüssel erstellen. Dieses Thema umfasst außerdem ein Beispiel für die Erstellung eines EAP-basierten WLAN-Profils.

> [!NOTE]
-   Möglicherweise ist es für Sie einfacher, den Code von einem Computer zu kopieren, der eine Verbindung mit dem jeweiligen Netzwerk herstellt, wie unten beschrieben.
- Bei Android haben Sie auch die Möglichkeit, diesen von Johnathon Biersack bereitgestellten [Android PSK Generator](http://intunepskgenerator.johnathonb.com/) zu verwenden.
-   Sie können mehrere Netzwerke und Schlüssel hinzufügen, indem Sie weitere OMA-URI-Einstellungen hinzufügen.
-  Verwenden Sie für iOS den Apple Configurator auf einer Mac-Station, um das Profil einzurichten. Verwenden Sie alternativ diesen [iOS PSK Mobile Config Generator](http://intunepskgenerator.johnathonb.com/), der von Johnathon Biersack bereitgestellt wird.


1.  Um ein WLAN-Profil mit einem vorinstallierten Schlüssel für Android oder Windows oder ein EAP-basiertes WLAN-Profil zu erstellen, wählen Sie beim Erstellen eines Geräteprofils anstelle eines WLAN-Profils die Option **Benutzerdefiniert** für die jeweilige Geräteplattform aus.

2.  Geben Sie einen Namen und eine Beschreibung an.
3.  Fügen Sie eine neue OMA-URI-Einstellung hinzu:

   ein.   Geben Sie einen Namen für diese WLAN-Netzwerkeinstellung ein.

   b.   Geben Sie eine Beschreibung für die OMA-URI-Einstellung ein, oder lassen Sie sie leer.

   c.   **Datentyp:** Legen Sie **String** fest.

   d.   **OMA-URI**:

    - **Für Android**: ./Vendor/MSFT/WiFi/Profile/<SSID>/Settings
    - **Für Windows**: ./Vendor/MSFT/WiFi/Profile/MyNetwork/WlanXml

    > [!NOTE]
Stellen Sie sicher, dass Sie den Punkt am Anfang eingeben.

    SSID steht für die SSID, für die Sie die Richtlinie erstellen. Beispiel: `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`

  e. **Wertfeld** Hier fügen Sie Ihren XML-Code ein. Hier sehen Sie ein Beispiel. Die einzelnen Werte sollten an Ihre Netzwerkeinstellungen angepasst werden. Einige Hinweise finden Sie im Kommentarabschnitt des Codes.
4. Wählen Sie **OK** aus, speichern Sie, und weisen Sie anschließend die Richtlinie zu.

    > [!NOTE]
    > Diese Richtlinie kann nur Benutzergruppen zugewiesen werden.

Wenn sich die einzelnen Geräte das nächste Mal anmelden, wird die Richtlinie angewendet, und auf dem Gerät wird ein WLAN-Profil erstellt. Das Gerät kann automatisch eine Verbindung mit dem Netzwerk herstellen.

## <a name="android-or-windows-wi-fi-profile"></a>Android- oder Windows-WLAN-Profil

Hier sehen Sie ein Beispiel für den XML-Code eines Android- oder Windows-WLAN-Profils:

> [!IMPORTANT]
>
> `<protected>false</protected>` muss auf **false** festgelegt werden, da **true** dazu führen könnte, dass das Gerät ein verschlüsseltes Kennwort erwartet, das es dann zu entschlüsseln versucht, was einen Verbindungsfehler bewirken würde.
>
>  `<hex>53534944</hex>` sollte auf den hexadezimalen Wert von `<name><SSID of wifi profile></name>` festgelegt werden.
>  Windows 10-Geräte können fälschlicherweise den Fehler *0x87D1FDE8: Fehler bei Wiederherstellung* zurückgeben, werden aber dennoch mit dem Profil bereitgestellt.

```
<!--
<Name of wifi profile> = Name of profile
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Password to connect to the network
x>53534944</hex> should be set to the hexadecimal value of <name><SSID of wifi profile></name>
-->
<WLANProfile
xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
  <name><Name of wifi profile></name>
  <SSIDConfig>
    <SSID>
      <hex>53534944</hex>
 <name><SSID of wifi profile></name>
    </SSID>
    <nonBroadcast>false</nonBroadcast>
  </SSIDConfig>
  <connectionType>ESS</connectionType>
  <connectionMode>auto</connectionMode>
  <autoSwitch>false</autoSwitch>
  <MSM>
    <security>
      <authEncryption>
        <authentication><Type of authentication></authentication>
        <encryption><Type of encryption></encryption>
        <useOneX>false</useOneX>
      </authEncryption>
      <sharedKey>
        <keyType>networkKey</keyType>
        <protected>false</protected>
        <keyMaterial>MyPassword</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

## <a name="eap-based-wi-fi-profile"></a>EAP-basiertes WLAN-Profil
Hier sehen Sie ein Beispiel für den XML-Code eines EAP-basierten WLAN-Profils:

```
    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
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
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>
```

## <a name="create-the-xml-file-from-an-existing-wi-fi-connection"></a>Erstellen der XML-Datei aus einer vorhandenen WLAN-Verbindung
Sie können die XML-Datei auch aus einer vorhandenen WLAN-Verbindung erstellen:
1. Öffnen Sie auf einem Computer, der mit dem WLAN verbunden ist oder vor kurzem damit verbunden war, den folgenden Ordner: „C:\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}“.

    Es wird empfohlen, einen Computer zu verwenden, der nicht mit allzu vielen WLANs verbunden ist, weil Sie die einzelnen Profile durchsuchen müssen, um das richtige zu finden.
3.     Durchsuchen Sie die XML-Dateien, um die Datei mit dem richtigen Namen zu finden.
4.     Nachdem Sie die richtige XML-Datei gefunden haben, kopieren Sie den XML-Code in das Feld „Daten“ auf der Seite mit den OMA-URI-Einstellungen.

## <a name="best-practices"></a>Bewährte Methoden
Bevor Sie ein WLAN-Profil mit PSK bereitstellen, überprüfen Sie, ob das Gerät eine direkte Verbindung mit dem Endpunkt herstellen kann.

Rechnen Sie beim Rotieren von Schlüsseln (Kennwörtern oder Passphrases) mit Ausfallzeiten, und planen Sie die Bereitstellung entsprechend. Erwägen Sie die Push-Übertragung von neuen WLAN-Profilen in der arbeitsfreien Zeit. Außerdem sollten Sie die Benutzer warnen, dass die Konnektivität beeinträchtigt sein kann.

Stellen Sie sicher, dass das Gerät des Endbenutzers eine alternative Verbindung mit dem Internet hat, damit ein reibungslosen Übergang gewährleistet ist. Der Endbenutzer muss z.B. dazu in der Lage sein, auf das Gast-WLAN (oder ein anderes WLAN-Netzwerk) oder eine Mobilfunkverbindung zuzugreifen, um mit Intune zu kommunizieren. Dadurch kann der Benutzer weiterhin Aktualisierungen zu Richtlinien erhalten, wenn das WLAN-Profil des Unternehmens auf dem Gerät aktualisiert wird.
