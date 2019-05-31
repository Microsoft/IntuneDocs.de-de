---
title: Zuweisen von Microsoft Intune-Lizenzen
description: Zuweisen von Lizenzen zu Benutzern, damit sich diese bei Intune registrieren können
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 14d5e01577100e0a66cfcf6ce935289a1dc26fab
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57459899"
---
# <a name="assign-licenses-to-users-so-they-can-enroll-devices-in-intune"></a>Zuweisen von Lizenzen zu Benutzern, damit sie ihre Geräte bei Intune registrieren können

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Egal, ob Sie manuell Benutzer hinzufügen oder aus Ihrem lokalen Active Directory synchronisieren, Sie müssen zunächst jedem Benutzer eine Intune-Lizenz zuweisen, bevor Benutzer ihre Geräte in Intune registrieren können. Eine Liste mit Lizenzen finden Sie unter [Lizenzen, die Intune enthalten](licenses.md).

## <a name="assign-an-intune-license-in-the-microsoft-365-admin-center"></a>Zuweisen einer Intune-Lizenz im Microsoft 365 Admin Center

Sie können das [Microsoft 365 Admin Center](http://go.microsoft.com/fwlink/p/?LinkId=698854) verwenden, um cloudbasierte Benutzer manuell hinzuzufügen. Außerdem können Sie es verwenden, um sowohl cloudbasierten Benutzerkonten als auch Konten, die aus Ihrer lokalen Active Directory-Bereitstellung mit Azure AD synchronisiert wurden, Lizenzen zuzuweisen.

1. Melden Sie sich mit den Anmeldeinformationen Ihres Mandantenadministrators beim [Microsoft 365 Admin Center](http://go.microsoft.com/fwlink/p/?LinkId=698854) an, und wählen Sie dann **Benutzer** > **Aktive Benutzer** aus.

2. Wählen Sie das Benutzerkonto, dem Sie eine Intune-Benutzerlizenz zuweisen möchten, und wählen Sie dann **Produktlizenzen** > **Bearbeiten**.

3. Schalten Sie **Intune** oder **Enterprise Mobility + Security** auf **An** um, und wählen Sie **Speichern**.

   ![Screenshot: Produktlizenzbereich im Microsoft 365 Admin Center](./media/office-assign-license.png)

4. Das Benutzerkonto verfügt jetzt über die erforderlichen Berechtigungen, um den Dienst zu nutzen und Geräte für die Verwaltung zu registrieren.

> [!NOTE]
> Benutzer werden erst in der Administratorkonsole angezeigt, nachdem sie ein Gerät registriert haben. Darüber hinaus können Sie eine Gruppe von Benutzern auswählen, die Sie gleichzeitig bearbeiten möchten; so können Sie für alle Benutzer entweder eine Lizenz hinzufügen oder diese ersetzen.

## <a name="assign-an-intune-license-by-using-azure-active-directory"></a>Zuweisen einer Intune-Lizenz mithilfe von Azure Active Directory

Sie können Benutzern mithilfe von Azure Active Directory eine Intune-Lizenz zuweisen. Weitere Informationen finden Sie im Artikel [Lizenzieren von Benutzern in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-group-assignment-azure-portal). 

## <a name="use-school-data-sync-to-assign-licenses-to-users-in-intune-for-education"></a>Verwenden der Synchronisierung von Schul-/Unidaten zum Zuweisen von Lizenzen zu Benutzern in Intune for Education
Wenn Sie zu einer Bildungseinrichtung gehören, können Sie mithilfe der Synchronisierung von Schul-/Unidaten (School Data Sync, SDS) synchronisierten Benutzern Intune for Education-Lizenzen zuweisen. Aktivieren Sie dazu lediglich beim Einrichten Ihres SDS-Profils das Kontrollkästchen „Intune for Education“.  

![Screenshot der SDS-Profileinstellung](./media/i4e-sds-profile-setup-setting.png)

Wenn Sie eine Intune Education-Lizenz zuweisen, stellen Sie sicher, dass auch eine Intune A Direct-Lizenz zugewiesen wird.

![Screenshot der Einrichtung der Produktlizenz](./media/i4e-set-licenses.png)

In dieser [Übersicht über die Synchronisierung von Schul-/Unidaten](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91) erfahren Sie mehr zu diesem Feature.

## <a name="how-user-and-device-licenses-affect-access-to-services"></a>Auswirkungen von Benutzer- und Gerätelizenzen auf den Zugriff auf Dienste
* Jeder **Benutzer**, dem Sie eine Benutzersoftwarelizenz zuweisen, kann die Onlinedienste und zugehörige Software (einschließlich System Center) zum Verwalten von Anwendungen und von bis zu 15 Geräten nutzen.
* Sie können Lizenzen für alle Geräte separat von Benutzerlizenzen erwerben. Gerätelizenzen müssen den Geräten nicht zugewiesen werden. Jedes Gerät, das auf die Onlinedienste und zugehörige Software (einschließlich System Center-Software) zugreift und sie nutzt, muss über eine Gerätelizenz verfügen.
* Wenn ein Gerät von mehreren Benutzern verwendet wird, erfordert jedes Gerät eine Gerätesoftwarelizenz, oder alle Benutzer benötigen eine Benutzersoftwarelizenz.

## <a name="understanding-the-type-of-licenses-you-have-purchased"></a>Informationen zu denen von Ihnen erworbenen Lizenztypen

Die Art und Weise, wie Sie Intune erworben haben, bestimmt Ihre Abonnementinformationen:

- Wenn Sie Intune über ein Enterprise Agreement erworben haben, finden Sie Ihre Abonnementinformationen im Volume Licensing-Portal unter **Abonnements**.
- Wenn Sie Intune über einen Cloudlösungsanbieter erworben haben, wenden Sie sich an Ihren Handelspartner.
- Wenn Sie Intune per Kreditkarte oder per Rechnung erworben haben, sind Ihre Lizenzen benutzerbezogen.




## <a name="use-powershell-to-selectively-manage-ems-user-licenses"></a>Selektive Verwaltung von EMS-Benutzerlizenzen über PowerShell
Organisationen, die Microsoft Enterprise Mobility + Security (EMS, früher Enterprise Mobility Suite) verwenden, verfügen jedoch möglicherweise über Benutzer, die nur Azure Active Directory Premium- oder Intune-Dienste im EMS-Paket benötigen. Sie können einen oder mehrere Dienste mithilfe von [Azure Active Directory PowerShell-Cmdlets](https://msdn.microsoft.com/library/jj151815.aspx) zuweisen.

Um Benutzerlizenzen für EMS-Dienste selektiv zuzuweisen, öffnen Sie PowerShell als Administrator auf einem Computer, auf dem das [Azure Active Directory-Modul für Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule) installiert ist. Sie können PowerShell auf einem lokalen Computer oder einem AD FS-Server installieren.

Sie müssen eine neue Lizenz-SKU-Definition erstellen, die nur für die gewünschten Servicepläne gilt. Deaktivieren Sie zu diesem Zweck die Pläne, die Sie nicht anwenden möchten. Sie können beispielsweise eine Lizenz-SKU-Definition erstellen, die keine Intune-Lizenzen zuweist. Um eine Liste der verfügbaren Dienste anzuzeigen, geben Sie Folgendes ein:.

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

Sie können den folgenden Befehl ausführen, um den Intune-Serviceplan auszuschließen. Mit der gleichen Methode können Sie die Definition auf eine vollständige Sicherheitsgruppe ausweiten oder detailliertere Filter verwenden.

**Beispiel 1**<br>
Erstellen Sie über die Befehlszeile einen neuen Benutzer, und weisen Sie eine EMS-Lizenz zu, ohne den auf Intune bezogenen Teil der Lizenz zu aktivieren:

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


Überprüfen Sie das Ergebnis:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**Beispiel 2**<br>
Deaktivieren Sie den auf Intune bezogenen Teil der EMS-Lizenz für einen Benutzer, dem bereits eine Lizenz zugewiesen wurde:

    Connect-MsolService

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -LicenseOptions $CustomEMS

Überprüfen Sie das Ergebnis:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)
