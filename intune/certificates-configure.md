---
title: Erstellen eines Zertifikatprofils in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Sie können für Ihre Geräte ein Zertifikatprofil hinzufügen oder erstellen, indem Sie eine SCEP- oder PKCS-Zertifikatumgebung konfigurieren, das öffentliche Zertifikat exportieren, das Profil im Azure-Portal erstellen und anschließend den Zertifikatprofilen in Microsoft Intune im Azure-Portal SCEP oder PKCS zuweisen
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 80be1d39d9a562dbc13b9384c6256eb02c9ef50e
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530561"
---
# <a name="configure-a-certificate-profile-for-your-devices-in-microsoft-intune"></a>Konfigurieren eines Zertifikatprofils für Ihre Geräte in Microsoft Intune

Sie erteilen Benutzern Berechtigungen zum Zugreifen auf Unternehmensressourcen über VPN, WLAN oder E-Mail-Profile. Mithilfe von Zertifikaten können Sie diese Verbindungen authentifizieren. Bei der Verwendung von Zertifikaten ist die Eingabe von Benutzernamen und Kennwörtern nicht zum Authentifizieren erforderlich.

Mit Intune können Sie diese Zertifikate Geräten zuweisen, die Sie verwalten. Intune unterstützt das Zuweisen und Verwalten folgender Zertifikattypen:

- Simple Certificate Enrollment-Protokoll (SCEP)
- PKCS#12 (oder PFX)

Jeder dieser Zertifikattypen hat eigene Voraussetzungen und Infrastrukturanforderungen.


## <a name="overview"></a>Übersicht

1. Stellen Sie sicher, dass Sie die richtige Zertifikatinfrastruktur eingerichtet haben. Sie können [SCEP-Zertifikate](certificates-scep-configure.md) und [PKCS-Zertifikate](certficates-pfx-configure.md) verwenden.

2. Installieren Sie auf jedem Gerät ein Stammzertifikat oder ein Zertifikat einer Zwischenzertifizierungsstelle, damit das Gerät die Rechtmäßigkeit Ihrer Zertifizierungsstelle erkennt. Erstellen Sie ein **vertrauenswürdiges Zertifikatprofil**, und weisen Sie es jedem Gerät zu, um das Zertifikat zu installieren. Wenn Sie dieses Profil zuweisen, wird das Stammzertifikat von den Geräten, die mit Intune verwaltet werden, angefordert und empfangen. Sie müssen für jede Plattform ein eigenes Profil erstellen. Vertrauenswürdige Zertifikatprofile sind für folgende Plattformen verfügbar:

    - iOS 8.0 und höher
    - macOS 10.11 und höher
    - Android 4,0 und höher
    - Android Enterprise  
    - Windows 8.1 und höher
    - Windows Phone 8.1 und höher
    - Windows 10 und höher

    > [!NOTE]  
    > Zertifikatprofile werden nicht auf Geräten unterstützt, die *Android Enterprise für dedizierte Geräte* ausführen.

3. Erstellen Sie Zertifikatprofile, damit Geräte ein Zertifikat für die Authentifizierung des VPN-, WLAN- und E-Mail-Zugriffs anfordern. Die folgenden Profiltypen sind für verschiedene Plattformen verfügbar:  

   | Plattform     |PKCS-Zertifikat|SCEP-Zertifikat| Importiertes PKCS-Zertifikat | 
   |--------------|----------------|----------------|-------------------|
   | Android                | Ja    | Ja    | Ja    |
   | Android Enterprise     | Ja    | Ja    | Ja    |
   | iOS                    | Ja    | Ja    | Ja    |
   | macOS                  |        | Ja    | Ja    |
   | Windows Phone 8.1      |        | Ja    | Ja    |
   | Windows 8.1 und höher  |        | Ja    |        |
   | Windows 10 und höher   | Ja    | Ja    | Ja    |

   Stellen Sie sicher, dass Sie für jede Geräteplattform ein eigenes Profil erstellen. Nachdem Sie das Profil erstellt haben, ordnen Sie es dem bereits erstellten vertrauenswürdigen Stammzertifikatprofil zu.

### <a name="further-considerations"></a>Weitere Überlegungen

- Wenn Sie über keine Unternehmenszertifizierungsstelle verfügen, müssen Sie eine erstellen.
- Wenn Sie SCEP-Profile verwenden, müssen Sie einen NDES-Server (NDES = Network Device Enrollment Service; Registrierungsdienst für Netzwerkgeräte) konfigurieren.
- Unabhängig davon, ob Sie SCEP- oder PKCS-Profile verwenden möchten, müssen Sie den Microsoft Intune Certificate Connector herunterladen und konfigurieren.


## <a name="step-1-configure-your-certificate-infrastructure"></a>Schritt 1: Konfigurieren der Zertifikatinfrastruktur

In den folgenden Artikeln finden Sie Hilfe zum Konfigurieren der Infrastruktur für jeden Zertifikatprofiltyp:

- [Konfigurieren der Zertifikatinfrastruktur für SCEP in Microsoft Intune](certificates-scep-configure.md)
- [Konfigurieren Ihrer Microsoft Intune-Zertifikatsinfrastruktur für PKCS](certficates-pfx-configure.md)


## <a name="step-2-export-your-trusted-root-ca-certificate"></a>Schritt 2: Exportieren des vertrauenswürdigen Zertifikats der Stammzertifizierungsstelle

Exportieren Sie das Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle als öffentliches Zertifikat (.cer-Datei) von der ausstellenden Zertifizierungsstelle oder von einem beliebigen Gerät, das die ausstellende Zertifizierungsstelle als vertrauenswürdig erachtet. Exportieren Sie nicht den privaten Schlüssel (.pfx).

Sie importieren dieses Zertifikat, wenn Sie ein vertrauenswürdiges Zertifikatprofil einrichten.

## <a name="step-3-create-trusted-certificate-profiles"></a>Schritt 3: Erstellen von vertrauenswürdigen Zertifikatprofilen
Erstellen Sie ein vertrauenswürdiges Zertifikatprofil, bevor Sie ein SCEP- oder PKCS-Zertifikatprofil erstellen können. Sie benötigen für jede Geräteplattform ein vertrauenswürdiges Zertifikatprofil und ein SCEP- oder PKCS-Profil. Die Schritte zur Erstellung vertrauenswürdiger Zertifikate sind bei jeder Geräteplattform ähnlich.

1. Melden Sie sich bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) an.
3. Klicken Sie auf **Gerätekonfiguration** > **Verwalten** > **Profile** > **Profil erstellen**.
4. Geben Sie für das vertrauenswürdige Zertifikatprofil einen **Namen** und eine **Beschreibung** ein.
5. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform für das vertrauenswürdige Zertifikat aus. Folgende Optionen sind verfügbar:

    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 und höher**
    - **Windows 10 und höher**

6. Wählen Sie in der Dropdownliste **Profiltyp** die Option **Vertrauenswürdiges Zertifikat** aus.
7. Navigieren Sie zum Zertifikat, das Sie unter [Schritt 2: Exportieren des vertrauenswürdigen Zertifikats der Stammzertifizierungsstelle](#step-2-export-your-trusted-root-ca-certificate) gespeichert haben, und klicken Sie dann auf **OK**.
8. Wählen Sie (nur bei Windows 8.1- und Windows 10-Geräten) den **Zielspeicher** für das vertrauenswürdige Zertifikat aus:

    - **Computerzertifikatspeicher – Stamm**
    - **Computerzertifikatspeicher – Zwischenspeicher**
    - **Benutzerzertifikatspeicher – Zwischenspeicher**

9. Klicken Sie anschließend auf **OK**, navigieren Sie wieder zum Bereich **Profil erstellen**, und klicken Sie auf **Erstellen**.

Das Profil wird erstellt und wird in der Liste angezeigt. Informationen zur Zuweisung dieses Profils zu Gruppen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).

   >[!NOTE]
   > Auf Android-Geräte wird möglicherweise die Benachrichtigung angezeigt, dass ein Drittanbieter ein vertrauenswürdiges Zertifikat installiert hat.

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>Schritt 4: Erstellen von SCEP- oder PKCS-Zertifikatprofilen

In den folgenden Artikeln finden Sie Hilfe zum Konfigurieren und Zuweisen jedes Zertifikatprofiltyps:

- [Konfigurieren der Zertifikatinfrastruktur für SCEP in Microsoft Intune](certificates-scep-configure.md)
- [Konfigurieren Ihrer Microsoft Intune-Zertifikatsinfrastruktur für PKCS](certficates-pfx-configure.md)

Nachdem Sie ein Profil des vertrauenswürdigen Zertifikats erstellt haben, erstellen Sie SCEP- oder PKCS-Zertifikatprofile für jede Plattform, die Sie verwenden möchten. Wenn Sie ein SCEP-Zertifikatprofil erstellen, geben Sie ein vertrauenswürdiges Zertifikatprofil für dieselbe Plattform ein. Durch diesen Schritt werden die beiden Zertifikatprofile verknüpft. Sie müssen trotzdem jedes Profil separat zuweisen.

## <a name="next-steps"></a>Nächste Schritte
[Zuweisen von Geräteprofilen](device-profile-assign.md)  
[Use S/MIME to sign and encrypt emails (Verwenden von S/MIME zum Signieren und Verschlüsseln von E-Mails)](certificates-s-mime-encryption-sign.md)  
[Use third-party certificate authority (Verwenden einer Drittanbieter-Zertifizierungsstelle)](certificate-authority-add-scep-overview.md)

## <a name="see-also"></a>Siehe auch

[Problembehandlung der NDES-Konfiguration für die Verwendung mit Microsoft Intune-Zertifikatprofilen](https://support.microsoft.com/help/4459540)

[Problembehandlung für die Bereitstellung eines SCEP-Zertifikatprofils in Microsoft Intune](https://support.microsoft.com/help/4457481)
