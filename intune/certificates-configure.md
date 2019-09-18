---
title: Erstellen eines Zertifikatprofils in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Sie können für Ihre Geräte ein Zertifikatprofil hinzufügen oder erstellen, indem Sie eine SCEP- oder PKCS-Zertifikatumgebung konfigurieren, das öffentliche Zertifikat exportieren, das Profil im Azure-Portal erstellen und anschließend den Zertifikatprofilen in Microsoft Intune im Azure-Portal SCEP oder PKCS zuweisen
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/03/2019
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
ms.openlocfilehash: 76e6ba8cb1ed6804bfb50f69a00817a50fe1912e
ms.sourcegitcommit: 3db8af810b95c3a6ed3f8cc00f6ce79076ebb9db
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2019
ms.locfileid: "71012450"
---
# <a name="use-certificates-for-authentication-in-microsoft-intune"></a>Verwenden von Zertifikaten zur Authentifizierung in Microsoft Intune  

Verwenden Sie Zertifikate mit Intune, um Ihre Benutzer mithilfe von VPN, WLAN oder E-Mail-Profilen bei Anwendungen und Unternehmensressourcen zu authentifizieren. Wenn Sie Zertifikate verwenden, um diese Verbindungen zu authentifizieren, müssen die Endbenutzer keine Benutzernamen und Kennwörter eingeben. Dadurch wird ein nahtloser Zugriff ermöglicht. Zertifikate werden auch zum Signieren und Verschlüsseln von E-Mails mithilfe von S/MIME verwendet.

Intune unterstützt folgende Zertifikattypen:  

- Simple Certificate Enrollment-Protokoll (SCEP)  
- PKCS#12 (oder PFX)  
- Importiertes PKCS-Zertifikate

Erstellen Sie Zertifikatprofile, und weisen Sie sie Geräten zu, um diese Zertifikate bereitzustellen.  

Jedes einzelne Zertifikatprofil, das Sie erstellen, unterstützt eine einzelne Plattform. Wenn Sie z. B. PKCS-Zertifikate verwenden, erstellen Sie ein PKCS-Zertifikatprofil für Android und ein separates PKCS-Zertifikatprofil für iOS. Wenn Sie auch SCEP-Zertifikate für diese beiden Plattformen verwenden, erstellen Sie ein SCEP-Zertifikatprofil für Android und ein weiteres für iOS.  

**Allgemeine Aspekte**:  
- Wenn Sie nicht über eine Unternehmenszertifizierungsstelle (Certification Authority, CA) verfügen, müssen Sie eine erstellen oder eine von [einem unserer unterstützten Partner](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners) verwenden.
- Wenn Sie SCEP-Zertifikatprofile mit Microsoft Active Directory-Zertifikatdiensten verwenden, konfigurieren Sie einen Server für den Registrierungsdienst für Netzwerkgeräte (Network Device Enrollment Service, NDES).
- Wenn Sie ein SCEP mit einem unserer Zertifizierungsstellenpartner verwenden, müssen Sie es [in Intune integrieren](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration).
- Für SCEP- und PKCS-Zertifikatprofile müssen Sie den Microsoft Intune Certificate Connector herunterladen, installieren und konfigurieren. 
- Für PCKS-importierte Zertifikate müssen Sie den PFX-Zertifikatconnector für Microsoft Intune herunterladen, installieren und konfigurieren.
- PKCS-importierte Zertifikate erfordern, dass Sie Zertifikate aus Ihrer Zertifizierungsstelle exportieren und in Microsoft Intune importieren. Weitere Informationen finden Sie unter [dem PowerShell-Projekt für PFXImport](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).
- Damit ein Gerät SCEP-, PCKS- oder PKCS-importierte Zertifikatprofile verwendet, muss dieses Gerät Ihrer Stammzertifizierungsstelle vertrauen. Sie verwenden ein *vertrauenswürdiges Zertifikatprofil*, um Ihr Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle für Geräte bereitzustellen.  

## <a name="supported-platforms-and-certificate-profiles"></a>Unterstützte Plattformen und Zertifikatprofile  
| Plattform              | Vertrauenswürdiges Zertifikatprofil | PKCS-Zertifikatprofil | SCEP-Zertifikatprofil | Importiertes PKCS-Zertifikatprofil  |
|--|--|--|--|---|
| Android-Geräteadministrator | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png)|  ![Unterstützt](./media/certificates-configure/green-check.png) |
| Android Enterprise <br> – Gerätebesitzer   | ![Unterstützt](./media/certificates-configure/green-check.png) |   |  |   |
| Android Enterprise <br> – Arbeitsprofil    | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) |
| iOS                   | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) |
| macOS                 | ![Unterstützt](./media/certificates-configure/green-check.png) |   |![Unterstützt](./media/certificates-configure/green-check.png)|![Unterstützt](./media/certificates-configure/green-check.png)|
| Windows Phone 8.1     |![Unterstützt](./media/certificates-configure/green-check.png)  |  | ![Unterstützt](./media/certificates-configure/green-check.png)| ![Unterstützt](./media/certificates-configure/green-check.png) |
| Windows 8.1 und höher |![Unterstützt](./media/certificates-configure/green-check.png)  |  |![Unterstützt](./media/certificates-configure/green-check.png) |   |
| Windows 10 und höher  | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) | ![Unterstützt](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>Exportieren des Zertifikats der vertrauenswürdigen Stammzertifizierungsstelle  
Wenn Sie PKCS-, SCEP- und PKCS-importierte Zertifikate verwenden möchten, müssen Geräte ihrer Stammzertifizierungsstelle vertrauen. Um diese Vertrauensstellung einzurichten, exportieren Sie das Zertifikat der vertrauenswürdigen Stammzertifizierungsstelle sowie alle Zwischenzertifikate oder ausstellenden Zertifikate von Zertifizierungsstellen als öffentliches Zertifikat (.cer). Sie können diese Zertifikate von der ausstellenden Zertifizierungsstelle oder von einem beliebigen Gerät erhalten, das Ihrer ausstellenden Zertifizierungsstelle vertraut.  

Informationen zum Exportieren des Zertifikats finden Sie in der Dokumentation zu Ihrer Zertifizierungsstelle. Sie müssen das öffentliche Zertifikat als CER-Datei exportieren.  Exportieren Sie nicht den privaten Schlüssel, eine PFX-Datei.  

Sie verwenden diese CER-Datei, wenn Sie [vertrauenswürdige Zertifikatprofile erstellen](#create-trusted-certificate-profiles), um das Zertifikat für Ihre Geräte bereitzustellen.  

## <a name="create-trusted-certificate-profiles"></a>Erstellen von vertrauenswürdigen Zertifikatprofilen  
Erstellen Sie ein vertrauenswürdiges Zertifikatprofil, bevor Sie ein SCEP-, PKCS oder PKCS-importiertes Zertifikatprofil erstellen können. Durch Bereitstellen eines vertrauenswürdigen Zertifikatprofils wird sichergestellt, dass jedes Gerät die Rechtmäßigkeit Ihrer Zertifizierungsstelle erkennt. SCEP-Zertifikatprofile verweisen direkt auf ein vertrauenswürdiges Zertifikatprofil. PKCS-Zertifikatprofile verweisen nicht direkt auf das Profil des vertrauenswürdigen Zertifikats, sondern direkt auf den Server, der Ihre Zertifizierungsstelle hostet. Importierte PKCS-Zertifikatprofile verweisen nicht direkt auf das Profil des vertrauenswürdigen Zertifikats, sie können es jedoch auf dem Gerät verwenden. Durch die Bereitstellung eines vertrauenswürdigen Zertifikatprofils auf Geräten wird sichergestellt, dass dieses Vertrauen aufgebaut wird. Wenn die Stammzertifizierungsstelle von einem Gerät nicht als vertrauenswürdig eingestuft wird, schlägt die SCEP- oder PKCS-Zertifikatprofilrichtlinie fehl.  

Erstellen Sie ein separates vertrauenswürdiges Zertifikatprofil für jede Geräteplattform, die Sie unterstützen möchten, genauso wie bei den SCEP-, PCKS- und PKCS-importierten Zertifikatprofilen.  


### <a name="to-create-a-trusted-certificate-profile"></a>So erstellen Sie ein vertrauenswürdiges Zertifikatprofil  

1. Melden Sie sich beim [Intune-Portal](https://aka.ms/intuneportal) an.  
2. Klicken Sie auf **Gerätekonfiguration** > **Verwalten** > **Profile** > **Profil erstellen**.  
3. Geben Sie für das vertrauenswürdige Zertifikatprofil einen **Namen und eine Beschreibung** ein.  
4. Wählen Sie in der Dropdownliste **Plattform** die Geräteplattform für das vertrauenswürdige Zertifikat aus.  
5. Wählen Sie in der Dropdownliste **Profiltyp** die Option **Vertrauenswürdiges Zertifikat** aus.  
6. Navigieren Sie zur CER-Datei des Zertifikats der vertrauenswürdigen Stammzertifizierungsstelle, die Sie zur Verwendung mit diesem Zertifikatprofil exportiert haben, und klicken Sie dann auf **OK**.  
7. Wählen Sie (nur bei Windows 8.1- und Windows 10-Geräten) den **Zielspeicher** für das vertrauenswürdige Zertifikat aus:  
   - **Computerzertifikatspeicher – Stamm**
   - **Computerzertifikatspeicher – Zwischenspeicher**
   - **Benutzerzertifikatspeicher – Zwischenspeicher**
8. Klicken Sie anschließend auf **OK**, navigieren Sie wieder zum Bereich **Profil erstellen**, und klicken Sie auf **Erstellen**.
Das Profil wird in der Liste der Profile im Anzeigebereich *Gerätekonfiguration – Profile* mit dem Profiltyp **Vertrauenswürdiges Zertifikat** angezeigt.  Stellen Sie sicher, dass Sie dieses Profil Geräten zuweisen, die SCEP- oder PCKS-Zertifikate verwenden werden. Informationen zur Zuweisung des Profils zu Gruppen finden Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md).

> [!NOTE]  
> Auf Android-Geräten wird möglicherweise die Benachrichtigung angezeigt, dass ein Drittanbieter ein vertrauenswürdiges Zertifikat installiert hat.  

## <a name="additional-resources"></a>Zusätzliche Ressourcen  
- [Zuweisen von Geräteprofilen](device-profile-assign.md)  
- [Use S/MIME to sign and encrypt emails (Verwenden von S/MIME zum Signieren und Verschlüsseln von E-Mails)](certificates-s-mime-encryption-sign.md)  
- [Verwenden der Drittanbieter-Zertifizierungsstelle](certificate-authority-add-scep-overview.md)  

## <a name="next-steps"></a>Nächste Schritte  
Nachdem Sie die Profile des vertrauenswürdigen Zertifikats erstellt und zugewiesen haben, erstellen Sie SCEP-, PKCS- oder importierte PKCS- Zertifikatprofile für jede Plattform, die Sie verwenden möchten. Weitere Informationen zum Fortfahren finden Sie in den folgenden Artikeln:  
- [Konfigurieren Ihrer Infrastruktur für die Unterstützung von SCEP-Zertifikaten mit Intune](certificates-scep-configure.md)  
- [Konfigurieren Ihrer Microsoft Intune-Zertifikatsinfrastruktur für PKCS](certficates-pfx-configure.md)  
- [Erstellen eines importierten PKCS-Zertifikatprofils](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)  

