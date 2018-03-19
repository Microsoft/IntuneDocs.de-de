---
title: "Erstellen eines Zertifikatprofils in Microsoft Intune – Azure | Microsoft-Dokumentation"
description: "Sie können für Ihre Geräte ein Zertifikatprofil hinzufügen oder erstellen, indem Sie eine SCEP- oder PKCS-Zertifikatumgebung konfigurieren, das öffentliche Zertifikat exportieren, das Profil im Azure-Portal erstellen und anschließend den Zertifikatprofilen in Microsoft Intune im Azure-Portal SCEP oder PKCS zuweisen"
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b9d181c4a6e490018c88214a2ed91c90327f2526
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="configure-a-certificate-profile-for-your-devices-in-microsoft-intune"></a>Konfigurieren eines Zertifikatprofils für Ihre Geräte in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Wenn Sie Benutzern den Zugriff auf Unternehmensressourcen über VPN, WLAN oder E-Mail-Profile gestatten, können Sie diese Verbindungen mit Zertifikaten authentifizieren. Bei der Verwendung von Zertifikaten ist die Eingabe von Benutzernamen und Kennwörtern zum Authentifizieren von Verbindungen nicht erforderlich. 

Mit Intune können Sie diese Zertifikate Geräten zuweisen, die Sie verwalten. Intune unterstützt das Zuweisen und Verwalten folgender Zertifikattypen:

- Simple Certificate Enrollment-Protokoll (SCEP)
- PKCS#12 (oder PFX)

Jeder dieser Zertifikattypen hat eigene Voraussetzungen und Infrastrukturanforderungen.

## <a name="overview"></a>Übersicht

1. Stellen Sie sicher, dass Sie die richtige Zertifikatinfrastruktur eingerichtet haben. Sie können [SCEP-Zertifikate](certificates-scep-configure.md) und [PKCS-Zertifikate](certficates-pfx-configure.md) verwenden.

2. Installieren Sie auf jedem Gerät ein Stammzertifikat oder ein Zertifikat einer Zwischenzertifizierungsstelle, damit das Gerät die Rechtmäßigkeit Ihrer Zertifizierungsstelle erkennt. Erstellen Sie zu diesem Zweck ein **vertrauenswürdiges Zertifikatprofil** und weisen Sie es zu. Wenn Sie dieses Profil zuweisen, wird das Stammzertifikat von den Geräten, die Sie mit Intune verwalten, angefordert und empfangen. Sie müssen für jede Plattform ein eigenes Profil erstellen. Vertrauenswürdige Zertifikatprofile sind für folgende Plattformen verfügbar:

    - iOS 8.0 und höher
    - macOS 10.9 und höher
    - Android 4,0 und höher
    - Android for Work
    - Windows 8.1 und höher
    - Windows Phone 8.1 und höher
    - Windows 10 und höher

3. Erstellen Sie Zertifikatprofile, damit Geräte ein Zertifikat für die Authentifizierung des VPN-, WLAN- und E-Mail-Zugriffs anfordern. Sie können ein **PKCS**- oder **SCEP**-Zertifikatprofil für Geräte erstellen und zuweisen, die folgende Plattformen ausführen:

   - iOS 8.0 und höher
   - Android 4,0 und höher
   - Android for Work
   - Windows 10 (Desktop und Mobile) und höher

   Bei Geräten, die folgende Plattformen ausführen, können Sie nur ein **SCEP**-Zertifikatprofil verwenden:

   - macOS 10.9 und höher
   - Windows Phone 8.1 und höher

Stellen Sie sicher, dass Sie für jede Geräteplattform ein eigenes Profil erstellen. Nachdem Sie das Profil erstellt haben, ordnen Sie es dem bereits erstellten vertrauenswürdigen Stammzertifikatprofil zu.

### <a name="further-considerations"></a>Weitere Überlegungen

- Wenn Sie über keine Unternehmenszertifizierungsstelle verfügen, müssen Sie eine erstellen.
- Wenn Sie SCEP-Profile verwenden, müssen Sie einen NDES-Server (NDES = Network Device Enrollment Service; Registrierungsdienst für Netzwerkgeräte) konfigurieren.
- Unabhängig davon, ob Sie SCEP- oder PKCS-Profile verwenden möchten, müssen Sie den Microsoft Intune Certificate Connector herunterladen und konfigurieren.


## <a name="step-1-configure-your-certificate-infrastructure"></a>Schritt 1: Konfigurieren der Zertifikatinfrastruktur

Unter den folgenden Themen finden Sie Hilfe zum Konfigurieren der Infrastruktur für jeden Zertifikatprofiltyp:

- [Konfigurieren der Zertifikatinfrastruktur für SCEP in Microsoft Intune](certificates-scep-configure.md)
- [Konfigurieren Ihrer Microsoft Intune-Zertifikatsinfrastruktur für PKCS](certficates-pfx-configure.md)


## <a name="step-2-export-your-trusted-root-ca-certificate"></a>Schritt 2: Exportieren des vertrauenswürdigen Zertifikats der Stammzertifizierungsstelle

Exportieren Sie das Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle als öffentliches Zertifikat (.cer-Datei) von der ausstellenden Zertifizierungsstelle oder von einem beliebigen Gerät, das die ausstellende Zertifizierungsstelle als vertrauenswürdig erachtet. Exportieren Sie nicht den privaten Schlüssel (.pfx).

Sie importieren dieses Zertifikat, wenn Sie ein vertrauenswürdiges Zertifikatprofil einrichten.

## <a name="step-3-create-trusted-certificate-profiles"></a>Schritt 3: Erstellen von vertrauenswürdigen Zertifikatprofilen
Erstellen Sie ein vertrauenswürdiges Zertifikatprofil, bevor Sie ein SCEP- oder PKCS-Zertifikatprofil erstellen können. Sie benötigen für jede Geräteplattform ein vertrauenswürdiges Zertifikatprofil und ein SCEP- oder PKCS-Profil. Die Schritte zur Erstellung vertrauenswürdiger Zertifikate sind bei jeder Geräteplattform ähnlich.

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, und suchen Sie nach **Microsoft Intune**.
2. Wählen Sie in **Microsoft Intune** die Option **Gerätekonfiguration** und anschließend **Profile** aus. Wählen Sie dann **Profil erstellen** aus.
3. Geben Sie für das vertrauenswürdige Zertifikatprofil einen **Namen** und eine **Beschreibung** ein.
4. Wählen Sie bei der **Plattform** die Geräteplattform für dieses vertrauenswürdige Zertifikat aus: 

    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 und höher**
    - **Windows 10 und höher**

5. Wählen Sie bei **Profiltyp** die Option **Vertrauenswürdiges Zertifikat** aus. Navigieren Sie zu dem Zertifikat (*CertificateName*.cer), das Sie zuvor gespeichert haben (in Schritt 2).

    Wählen Sie (nur bei Windows 8.1- und Windows 10-Geräten) den **Zielspeicher** für das vertrauenswürdige Zertifikat aus:  

    - **Computerzertifikatspeicher – Stamm**
    - **Computerzertifikatspeicher – Zwischenspeicher**
    - **Benutzerzertifikatspeicher – Zwischenspeicher**

6. Wählen Sie **OK** aus, um Ihre Änderungen zu speichern, und anschließend **Erstellen**, um Ihr neues Profil zu speichern.

Das Profil wird erstellt und wird in der Liste angezeigt. Informationen zur Zuweisung dieses Profils zu Gruppen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).

Auf Android-Geräte wird möglicherweise die Benachrichtigung angezeigt, dass ein Drittanbieter ein vertrauenswürdiges Zertifikat installiert hat.

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>Schritt 4: Erstellen von SCEP- oder PKCS-Zertifikatprofilen

Unter den folgenden Themen finden Sie Hilfe zum Konfigurieren und Zuweisen jedes Zertifikatprofiltyps:

- [Konfigurieren der Zertifikatinfrastruktur für SCEP in Microsoft Intune](certificates-scep-configure.md)
- [Konfigurieren Ihrer Microsoft Intune-Zertifikatsinfrastruktur für PKCS](certficates-pfx-configure.md)

Nachdem Sie ein Profil des vertrauenswürdigen Zertifikats erstellt haben, erstellen Sie SCEP- oder PKCS-Zertifikatprofile für jede Plattform, die Sie verwenden möchten. Wenn Sie ein SCEP-Zertifikatprofil erstellen, geben Sie ein vertrauenswürdiges Zertifikatprofil für dieselbe Plattform ein. Durch diesen Schritt werden die beiden Zertifikatprofile verknüpft. Sie müssen trotzdem jedes Profil separat zuweisen.

## <a name="next-steps"></a>Nächste Schritte
Allgemeine Informationen zum Zuweisen von Geräteprofilen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).