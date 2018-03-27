---
title: Verwalten von Intune-Lizenzen mithilfe von PowerShell
description: Verwalten von Intune-Lizenzen mit PowerShell
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 02/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d2d31c80-c32c-4315-8271-1b0cf9a1f78a
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f6cd6f71b3f78a7b77435d1c7474c1bd672b8b95
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="manage-intune-licenses-using-powershell"></a>Verwalten von Intune-Lizenzen mithilfe von PowerShell

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

In diesem Thema erfahren Administratoren, wie sie PowerShell verwenden können, um Benutzerlizenzen in Intune zu verwalten.

Bevor Benutzer sich für die Verwendung des Intune-Diensts anmelden oder ihre Geräte für die Verwaltung registrieren können, müssen Sie zunächst jedem Benutzer eine Lizenz für Ihr Intune-Abonnement zuweisen (siehe [Verwalten von Intune-Lizenzen](/intune/licenses-assign)). Unternehmen, die jedoch Microsoft Enterprise Mobility + Security verwenden, verfügen möglicherweise über Benutzer, die nur Azure Active Directory Premium- oder Intune-Dienste im EMS-Paket benötigen. Sie können einen oder mehrere Dienste mithilfe von [Azure Active Directory PowerShell-Cmdlets](https://msdn.microsoft.com/library/jj151815.aspx) zuweisen.

Um Benutzerlizenzen für EMS-Dienste selektiv zuzuweisen, öffnen Sie PowerShell als Administrator auf einem Computer, auf dem das [Azure Active Directory-Modul für Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule) installiert ist. Sie können PowerShell auf einem lokalen Computer oder einem AD FS-Server installieren.

Sie müssen eine neue Lizenz-SKU-Definition erstellen, die nur für die gewünschten Servicepläne gilt. Deaktivieren Sie zu diesem Zweck die Pläne, die Sie nicht anwenden möchten. Sie können beispielsweise eine Lizenz-SKU-Definition erstellen, die keine Intune-Lizenzen zuweist. Um eine Liste der verfügbaren Dienste anzuzeigen, geben Sie Folgendes ein:.

    (Get-MsolAccountSku | Where {$\_.SkuPartNumber -eq "EMS"}).ServiceStatus

Sie können den folgenden Befehl ausführen, um den Intune-Serviceplan auszuschließen. Mit der gleichen Methode können Sie die Definition auf eine vollständige Sicherheitsgruppe ausweiten oder detailliertere Filter verwenden.

**Beispiel 1** Erstellen Sie über die Befehlszeile einen neuen Benutzer, und weisen Sie eine EMS-Lizenz zu, ohne den auf Intune bezogenen Teil der Lizenz zu aktivieren:

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


Überprüfen Sie das Ergebnis:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**Beispiel 2** Deaktivieren Sie den auf Intune bezogenen Teil der EMS-Lizenz für einen Benutzer, dem bereits eine Lizenz zugewiesen wurde:

    Connect-MsolService

    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -RemoveLicenses IAPProdPartnerTest:EMS

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS

Überprüfen Sie das Ergebnis:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com" .Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)

### <a name="next-steps"></a>Nächste Schritte
Gratulation! Sie haben Schritt 4 der Kurzanleitung *Erste Schritte mit Intune* abgeschlossen.
>[!div class="step-by-step"]
(/intune/custom-domain-name-configure) [&larr; **Synchronisieren von Benutzern mit Intune**](/intune/custom-domain-name-configure)     [**Organisieren von Benutzern und Geräten** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)  
