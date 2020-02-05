---
title: Erstellen eines WLAN-Profils mit einem vorinstallierten Schlüssel in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden Sie ein benutzerdefiniertes Profil, um ein WLAN-Profil mit einem vorinstallierten Schlüssel zu erstellen, und rufen Sie XML-Beispielcode für Android- und Windows-WLAN-Profile sowie EAP-basierte WLAN-Profile in Microsoft Intune ab.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9b56ba1515608afb6c2a0d151f5412711d49e57
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886718"
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key-in-intune"></a>Verwenden eines benutzerdefinierten Geräteprofils zum Erstellen eines WLAN-Profils mit einem vorinstallierten Schlüssel in Intune



Vorinstallierte Schlüssel (Pre-shared keys, PSK) werden üblicherweise verwendet, um Benutzer in WLANs (drahtlosen Netzwerken) zu authentifizieren. In Intune können Sie mit einem vorinstallierten Schlüssel ein WLAN-Profil erstellen. Verwenden Sie zum Erstellen des Profils das Intune-Feature **Benutzerdefinierte Geräteprofile**. Dieser Artikel enthält auch einige Beispiele für die Erstellung eines EAP-basierten WLAN-Profils.

Dieses Features unterstützt folgende Betriebssysteme:

- Android-Geräteadministrator
- Windows
- EAP-basiertes WLAN

> [!IMPORTANT]
> - Die Verwendung eines vorinstallierten Schlüssels mit Windows 10 verursacht einen Wartungsfehler in Intune. In diesem Fall wird das WLAN-Profil ordnungsgemäß dem Gerät zugewiesen, und das Profil funktioniert wie erwartet.
> - Vergewissern Sie sich, dass die Datei geschützt ist, wenn Sie ein WLAN-Profil exportieren, das einen vorinstallierten Schlüssel enthält. Der Schlüssel wird in Nur-Text angegeben. Daher sind Sie für die Sicherheit des Schlüssels verantwortlich.

## <a name="before-you-begin"></a>Vorbereitung

- Möglicherweise ist es einfacher, den Code von einem Computer zu kopieren, der eine Verbindung mit dem jeweiligen Netzwerk herstellt, wie weiter unten in diesem Artikel beschrieben.
- Sie können mehrere Netzwerke und Schlüssel hinzufügen, indem Sie weitere OMA-URI-Einstellungen hinzufügen.
- Verwenden Sie für iOS den Apple Configurator auf einer Mac-Station, um das Profil einzurichten.
- PSK erfordert eine Zeichenfolge von 64 Hexadezimalziffern oder eine Passphrase von 8 bis 63 druckbaren ASCII-Zeichen. Einige Zeichen wie etwa das Sternchen (*) werden nicht unterstützt.

## <a name="create-a-custom-profile"></a>Erstellen eines benutzerdefinierten Profils

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.
2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.
3. Geben Sie die folgenden Eigenschaften ein:

    - **Name:** Geben Sie einen aussagekräftigen Namen für die Richtlinie ein. Benennen Sie Ihre Richtlinien so, dass Sie diese später leicht wiedererkennen. Ein geeigneter Richtlinienname ist beispielsweise **Benutzerdefinierte Profileinstellungen für OMA-URI-WLAN für Android-Geräte**.
    - **Beschreibung:** Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    - **Plattform**: Wählen Sie Ihre Plattform aus.
    - **Profiltyp**: Klicken Sie auf **Benutzerdefiniert**.

4. Wählen Sie in **Einstellungen** die Option **Hinzufügen** aus. Geben Sie eine neue OMA-URI-Einstellung mit folgenden Eigenschaften ein:

    1. **Name:** Geben Sie einen Namen für die OMA-URI-Einstellung ein.
    2. **Beschreibung:** Geben Sie eine Beschreibung für die OMA-URI-Einstellung ein. Diese Einstellung ist optional, wird jedoch empfohlen.
    3. **OMA-URI**: Verwenden Sie eine der folgenden Optionen:

        - **Für Android**: `./Vendor/MSFT/WiFi/Profile/SSID/Settings`
        - **Für Windows**: `./Vendor/MSFT/WiFi/Profile/SSID/WlanXml`

        > [!NOTE]
        > Stellen Sie sicher, dass Sie den Punkt am Anfang eingeben.

        SSID steht für die SSID, für die Sie die Richtlinie erstellen. Lautet der WLAN-Name beispielsweise `Hotspot-1`, geben Sie `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings` ein.

    4. **Datentyp**: Wählen Sie **Zeichenfolge** aus.

    5. **Wert:** Fügen Sie Ihren XML-Code ein. Sehen Sie sich das [Beispiel](#android-or-windows-wi-fi-profile-example) in diesem Artikel an. Aktualisieren Sie jeden Wert mit dem entsprechenden Wert für Ihre Netzwerkeinstellungen. Der Kommentarabschnitt des Codes enthält einige Hinweise.

5. Wenn Sie fertig sind, wählen Sie **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern.

Ihr Profil wird in der Profilliste angezeigt. Im nächsten Schritt [weisen Sie dieses Profil](../device-profile-assign.md) Ihren Benutzergruppen zu. Diese Richtlinie kann nur Benutzergruppen zugewiesen werden.

Wenn sich die einzelnen Geräte das nächste Mal anmelden, wird die Richtlinie angewendet, und auf dem Gerät wird ein WLAN-Profil erstellt. Das Gerät kann dann automatisch eine Verbindung mit dem Netzwerk herstellen.

## <a name="android-or-windows-wi-fi-profile-example"></a>Android- oder Windows-WLAN-Profil – Beispiel

Das folgende Beispiel enthält den XML-Code für ein Android- oder Windows-WLAN-Profil. Das Beispiel wird bereitgestellt, um das richtige Format sowie weitere Details zu zeigen. Es ist nur ein Beispiel, und dient nicht als empfohlene Konfiguration für Ihre Umgebung.

### <a name="what-you-need-to-know"></a>Was Sie wissen müssen

- `<protected>false</protected>` muss auf **false** festgelegt werden. Eine Festlegung auf **true** könnte dazu führen, dass das Gerät ein verschlüsseltes Kennwort erwartet, das es dann zu entschlüsseln versucht. Dies würde einen Verbindungsfehler bewirken.

- `<hex>53534944</hex>` sollte auf den hexadezimalen Wert von `<name><SSID of wifi profile></name>` festgelegt werden. Windows 10-Geräte können fälschlicherweise den Fehler `x87D1FDE8 Remediation failed` zurückgeben, doch das Gerät enthält das Profil weiterhin.

- XML enthält Sonderzeichen, wie z. B. `&` (kaufmännisches Und-Zeichen). Wenn Sie Sonderzeichen verwenden, funktioniert die XML eventuell nicht wie erwartet. 

### <a name="example"></a>Beispiel

``` xml
<!--
<hex>53534944</hex> = The hexadecimal value of <name><SSID of wifi profile></name>
<Name of wifi profile> = Name of profile shown to users. It could be <name>Your Company's Network</name>.
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped. It could be <name>Your Company's Network</name>.
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network, such as AES.
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Plain text of the password to connect to the network
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
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial>password</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

### <a name="eap-based-wi-fi-profile-example"></a>EAP-basiertes WLAN-Profil – Beispiel
Das folgende Beispiel enthält den XML-Code für ein EAP-basiertes WLAN-Profil: Das Beispiel wird bereitgestellt, um das richtige Format sowie weitere Details zu zeigen. Es ist nur ein Beispiel, und dient nicht als empfohlene Konfiguration für Ihre Umgebung.


```xml
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

Sie können die XML-Datei auch aus einer vorhandenen WLAN-Verbindung erstellen. Führen Sie auf einem Windows-Computer die folgenden Schritte aus:

1. Erstellen Sie einen lokalen Ordner für die exportierten WLAN-Profile, z. B. C:\WiFi.
2. Öffnen Sie eine Eingabeaufforderung als Administrator (klicken Sie dazu mit der rechten Maustaste auf `cmd` > **Als Administrator ausführen**).
3. Führen Sie `netsh wlan show profiles`aus. Dort sind alle Profilnamen aufgelistet.
4. Führen Sie `netsh wlan export profile name="YourProfileName" folder=c:\Wifi`aus. Mit diesem Befehl wird eine Datei namens `Wi-Fi-YourProfileName.xml` in „C:\Wifi“ erstellt.

    - Wenn Sie ein WLAN-Profil mit einem vorinstallierten Schlüssel exportieren, fügen Sie dem Befehl `key=clear` hinzu:
  
        `netsh wlan export profile name="YourProfileName" key=clear folder=c:\Wifi`

        `key=clear` exportiert den Schlüssel im Nur-Text-Format, was für die erfolgreiche Verwendung des Profils erforderlich ist.

Nachdem Sie die XML-Datei erstellt haben, kopieren Sie die XML-Syntax, und fügen Sie sie unter „OMA-URI-Einstellungen“ > **Datentyp** ein. Im Abschnitt [Erstellen eines benutzerdefinierten Profils](#create-a-custom-profile) (in diesem Artikel) werden die erforderlichen Schritte aufgelistet.

> [!TIP]
> `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}` umfasst auch alle Profile im XML-Format.

## <a name="best-practices"></a>Empfohlene Methoden

- Bevor Sie ein WLAN-Profil mit PSK bereitstellen, vergewissern Sie sich, dass das Gerät eine direkte Verbindung mit dem Endpunkt herstellen kann.

- Rechnen Sie beim Rotieren von Schlüsseln (Kennwörtern oder Passphrasen) mit Ausfallzeiten, und planen Sie Ihre Bereitstellungen. Erwägen Sie die Push-Übertragung von neuen WLAN-Profilen in der arbeitsfreien Zeit. Außerdem sollten Sie die Benutzer warnen, dass die Konnektivität beeinträchtigt sein kann.

- Stellen Sie für einen reibungslosen Übergang sicher, dass die Geräte der Benutzer über eine alternative Verbindung mit dem Internet verfügen. Der Endbenutzer kann z. B. dazu in der Lage sein auf das Gast-WLAN (oder ein anderes WLAN-Netzwerk) oder eine Mobilfunkverbindung zugreifen, um mit Intune zu kommunizieren. Durch die zusätzliche Verbindung kann der Benutzer weiterhin Richtlinienaktualisierungen erhalten, wenn das WLAN-Profil des Unternehmens auf dem Gerät aktualisiert wird.

## <a name="next-steps"></a>Nächste Schritte

Denken Sie daran, das [Profil zuzuweisen](device-profile-assign.md) und seinen Status zu [überwachen](device-profile-monitor.md).
