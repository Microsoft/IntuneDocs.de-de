---
title: Erstellen eines Zertifikatprofils in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erfahren Sie mehr über die Verwendung von Zertifikaten und Zertifikatprofilen des Typs Simple Certificate Enrollment Protocol (SCEP) oder Public Key Cryptography Standards (PKCS) mit Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5092fa37f0bf6bd1320fa06fa58ac5e36f55aa3c
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410185"
---
# <a name="use-certificates-for-authentication-in-microsoft-intune"></a>Verwenden von Zertifikaten zur Authentifizierung in Microsoft Intune

Verwenden Sie Zertifikate mit Intune, um Ihre Benutzer mithilfe von VPN, WLAN oder E-Mail-Profilen bei Anwendungen und Unternehmensressourcen zu authentifizieren. Wenn Sie Zertifikate verwenden, um diese Verbindungen zu authentifizieren, müssen die Endbenutzer keine Benutzernamen und Kennwörter eingeben. Dadurch wird ein nahtloser Zugriff ermöglicht. Zertifikate werden auch zum Signieren und Verschlüsseln von E-Mails mithilfe von S/MIME verwendet.

## <a name="intune-supported-certificates-and-usage"></a>Von Intune unterstützte Zertifikate und Nutzung

| Typ              | Authentifizierung | S/MIME-Signatur | S/MIME-Verschlüsselung  |
|--|--|--|--|
| Über PKCS (Public Key Cryptography Standards) importiertes Zertifikat |  | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png)|
| PKCS#12 (oder PFX)    | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) |  |
| Simple Certificate Enrollment-Protokoll (SCEP)  | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | |

Erstellen Sie Zertifikatprofile, und weisen Sie sie Geräten zu, um diese Zertifikate bereitzustellen.

Jedes einzelne Zertifikatprofil, das Sie erstellen, unterstützt eine einzelne Plattform. Wenn Sie z. B. PKCS-Zertifikate verwenden, erstellen Sie ein PKCS-Zertifikatprofil für Android und ein separates PKCS-Zertifikatprofil für iOS. Wenn Sie auch SCEP-Zertifikate für diese beiden Plattformen verwenden, erstellen Sie ein SCEP-Zertifikatprofil für Android und ein weiteres für iOS.

### <a name="general-considerations-when-you-use-a-microsoft-certification-authority"></a>Allgemeine Überlegungen bei der Verwendung einer Microsoft-Zertifizierungsstelle

Bei der Verwendung einer Microsoft-Zertifizierungsstelle (Certification Authority) gilt Folgendes:

- Sie müssen einen [NDES-Server (Network Device Enrollment Service, Registrierungsdienst für Netzwerkgeräte) für die Verwendung mit Intune einrichten](certificates-scep-configure.md#set-up-ndes), wenn Sie SCEP-Zertifikatprofile verwenden möchten.
- Sie müssen den [Microsoft Intune-Zertifikatconnector installieren](certificates-scep-configure.md#install-the-intune-certificate-connector), um die folgenden Zertifikatprofiltypen verwenden zu können:
  - SCEP-Zertifizierungsprofil
  - PKCS-Zertifikatprofil

- Verwenden von importierten PKCS-Zertifikaten:
  - [Installieren Sie den PFX-Zertifikatconnector für Microsoft Intune.](certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune)
  - Exportieren Sie Zertifikate von der Zertifizierungsstelle, und importieren Sie diese dann in Microsoft Intune. Weitere Informationen finden Sie unter dem [PowerShell-Projekt für PFXImport](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

- Verwenden Sie zum Bereitstellen von Zertifikaten die folgenden Mechanismen:
  - [vertrauenswürdige Zertifikatprofile](certificates-configure.md#create-trusted-certificate-profiles) zum Bereitstellen des Zertifikats der vertrauenswürdigen Stammzertifizierungsstelle von der Stamm- oder Zwischenzertifizierungsstelle für Geräte
  - SCEP-Zertifikatprofile
  - PKCS-Zertifikatprofile
  - importierte PKCS-Zertifikatprofile

### <a name="general-considerations-when-you-use-a-third-party-certification-authority"></a>Allgemeine Überlegungen bei der Verwendung einer Drittanbieter-Zertifizierungsstelle

Bei der Verwendung einer Drittanbieter-Zertifizierungsstelle (Certification Authority, nicht von Microsoft) gilt Folgendes:

- Führen Sie folgende Schritte aus, um SCEP-Zertifikatprofile zu verwenden:
  - Richten Sie die Integration mit einer Drittanbieter-Zertifizierungsstelle [von einem unserer unterstützten Partner ein](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners). Beim Einrichten müssen die Anweisungen der Drittanbieter-Zertifizierungsstelle befolgt werden, um die Integration der Zertifizierungsstelle in Intune abzuschließen.
  - [Erstellen Sie eine Anwendung in Azure AD](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration), die Rechte an Intune delegiert, um die Aufforderungsüberprüfung von SCEP-Zertifikaten durchzuführen.

- Im Fall von importierten PKCS-Zertifikaten ist es erforderlich, den [PFX-Zertifikatconnector für Microsoft Intune zu installieren](certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).

- Verwenden Sie zum Bereitstellen von Zertifikaten die folgenden Mechanismen:
  - [vertrauenswürdige Zertifikatprofile](certificates-configure.md#create-trusted-certificate-profiles) zum Bereitstellen des Zertifikats der vertrauenswürdigen Stammzertifizierungsstelle von der Stamm- oder Zwischenzertifizierungsstelle für Geräte
  - SCEP-Zertifikatprofile
  - PKCS-Zertifikatprofile *(werden nur mit der [DigiCert PKI-Plattform](certificates-digicert-configure.md) unterstützt)*
  - importierte PKCS-Zertifikatprofile

## <a name="supported-platforms-and-certificate-profiles"></a>Unterstützte Plattformen und Zertifikatprofile

| Plattform              | Vertrauenswürdiges Zertifikatprofil | PKCS-Zertifikatprofil | SCEP-Zertifikatprofil | Importiertes PKCS-Zertifikatprofil  |
|--|--|--|--|---|
| Android-Geräteadministrator | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png)|  ![Unterstützt](./media/certificates-configure/green-check.png) |
| Android Enterprise <br> – Vollständig verwaltet (Gerätebesitzer)   | ![Unterstützt](./media/certificates-configure/green-check.png) |   | ![Unterstützt](./media/certificates-configure/green-check.png) |   |
| Android Enterprise <br> – Dediziert (Gerätebesitzer)   | ![Unterstützt](./media/certificates-configure/green-check.png)  |   | ![Unterstützt](./media/certificates-configure/green-check.png)  |   |
| Android Enterprise <br> – Arbeitsprofil    | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) |
| iOS                   | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) |
| macOS                 | ![Unterstützt](./media/certificates-configure/green-check.png) |  ![Unterstützt](./media/certificates-configure/green-check.png) |![Unterstützt](./media/certificates-configure/green-check.png)|![Unterstützt](./media/certificates-configure/green-check.png)|
| Windows Phone 8.1     |![Unterstützt](./media/certificates-configure/green-check.png)  |  | ![Unterstützt](./media/certificates-configure/green-check.png)| ![Unterstützt](./media/certificates-configure/green-check.png) |
| Windows 8.1 und höher |![Unterstützt](./media/certificates-configure/green-check.png)  |  |![Unterstützt](./media/certificates-configure/green-check.png) |   |
| Windows 10 und höher  | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>Exportieren des Zertifikats der vertrauenswürdigen Stammzertifizierungsstelle

Wenn Sie PKCS-, SCEP- und PKCS-importierte Zertifikate verwenden möchten, müssen Geräte ihrer Stammzertifizierungsstelle vertrauen. Exportieren Sie das Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle sowie alle Zwischenzertifikate oder ausstellenden Zertifikate von Zertifizierungsstellen als öffentliches Zertifikat (.cer), um eine Vertrauensstellung einzurichten. Sie können diese Zertifikate von der ausstellenden Zertifizierungsstelle oder von einem beliebigen Gerät erhalten, das Ihrer ausstellenden Zertifizierungsstelle vertraut.

Informationen zum Exportieren des Zertifikats finden Sie in der Dokumentation zu Ihrer Zertifizierungsstelle. Sie müssen das öffentliche Zertifikat als CER-Datei exportieren.  Exportieren Sie nicht den privaten Schlüssel, eine PFX-Datei.

Sie verwenden diese CER-Datei, wenn Sie [vertrauenswürdige Zertifikatprofile erstellen](#create-trusted-certificate-profiles), um das Zertifikat für Ihre Geräte bereitzustellen.

## <a name="create-trusted-certificate-profiles"></a>Erstellen von vertrauenswürdigen Zertifikatprofilen

Erstellen Sie ein vertrauenswürdiges Zertifikatprofil, bevor Sie ein SCEP-, PKCS oder PKCS-importiertes Zertifikatprofil erstellen können. Durch Bereitstellen eines vertrauenswürdigen Zertifikatprofils wird sichergestellt, dass jedes Gerät die Rechtmäßigkeit Ihrer Zertifizierungsstelle erkennt. SCEP-Zertifikatprofile verweisen direkt auf ein vertrauenswürdiges Zertifikatprofil. PKCS-Zertifikatprofile verweisen nicht direkt auf das Profil des vertrauenswürdigen Zertifikats, sondern direkt auf den Server, der Ihre Zertifizierungsstelle hostet. Über PKCS importierte Zertifikatprofile verweisen nicht direkt auf das Profil des vertrauenswürdigen Zertifikats, sie können es jedoch auf dem Gerät verwenden. Durch die Bereitstellung eines vertrauenswürdigen Zertifikatprofils auf Geräten wird sichergestellt, dass dieses Vertrauen aufgebaut wird. Wenn die Stammzertifizierungsstelle von einem Gerät nicht als vertrauenswürdig eingestuft wird, schlägt die SCEP- oder PKCS-Zertifikatprofilrichtlinie fehl.

Erstellen Sie ein separates vertrauenswürdiges Zertifikatprofil für jede Geräteplattform, die Sie unterstützen möchten, genauso wie bei den SCEP-, PKCS- und über PKCS importierten Zertifikatprofilen.

### <a name="to-create-a-trusted-certificate-profile"></a>So erstellen Sie ein vertrauenswürdiges Zertifikatprofil

1. Melden Sie sich beim [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) an.

2. Wählen Sie **Geräte** > **Konfigurationsprofile** > **Profil erstellen** aus.

   ![Navigieren Sie zu Intune, und erstellen Sie ein neues Profil für ein vertrauenswürdiges Zertifikat.](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. Geben Sie die folgenden Eigenschaften ein:

   - **Name** für das Profil
   - Optional können Sie eine **Beschreibung** einfügen.
   - **Plattform**, auf der das Profil bereitgestellt werden soll
   - Für **Profiltyp** die Option **Vertrauenswürdiges Zertifikat**

4. Wählen Sie **Einstellungen**, und navigieren Sie dann zur CER-Datei des Zertifikats der vertrauenswürdigen Stammzertifizierungsstelle, die Sie zur Verwendung mit diesem Zertifikatprofil exportiert haben, und klicken Sie dann auf **OK**.

5. Wählen Sie (nur bei Windows 8.1- und Windows 10-Geräten) den **Zielspeicher** für das vertrauenswürdige Zertifikat aus:

   - **Computerzertifikatspeicher – Stamm**
   - **Computerzertifikatspeicher – Zwischenspeicher**
   - **Benutzerzertifikatspeicher – Zwischenspeicher**

6. Klicken Sie anschließend auf **OK**, navigieren Sie wieder zum Bereich **Profil erstellen**, und klicken Sie auf **Erstellen**.

Das Profil wird in der Liste der Profile im Fenster *Geräte – Konfigurationsprofile* mit dem Profiltyp **Vertrauenswürdiges Zertifikat** angezeigt. Stellen Sie sicher, dass Sie dieses Profil Geräten zuweisen, die SCEP- oder PKCS-Zertifikate verwenden werden. Informationen zur Zuweisung des Profils zu Gruppen finden Sie unter [Zuweisen von Geräteprofilen](../configuration/device-profile-assign.md).

> [!NOTE]
> Auf Android-Geräten wird möglicherweise die Benachrichtigung angezeigt, dass ein Drittanbieter ein vertrauenswürdiges Zertifikat installiert hat.

## <a name="additional-resources"></a>Zusätzliche Ressourcen

- [Zuweisen von Geräteprofilen](../configuration/device-profile-assign.md)  
- [Use S/MIME to sign and encrypt emails (Verwenden von S/MIME zum Signieren und Verschlüsseln von E-Mails)](certificates-s-mime-encryption-sign.md)  
- [Verwenden der Drittanbieter-Zertifizierungsstelle](certificate-authority-add-scep-overview.md)  

## <a name="next-steps"></a>Nächste Schritte

Erstellen Sie SCEP-, PKCS- oder über PKCS importierte Zertifikatprofile für jede Plattform, die Sie verwenden möchten. Weitere Informationen zum Fortfahren finden Sie in den folgenden Artikeln:

- [Konfigurieren Ihrer Infrastruktur für die Unterstützung von SCEP-Zertifikaten mit Intune](certificates-scep-configure.md)  
- [Konfigurieren Ihrer Microsoft Intune-Zertifikatsinfrastruktur für PKCS](certficates-pfx-configure.md)  
- [Erstellen eines importierten PKCS-Zertifikatprofils](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)
