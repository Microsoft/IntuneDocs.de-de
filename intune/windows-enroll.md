---
title: Registrierung von Windows-Geräten mit Microsoft Intune
titlesuffix: ''
description: Registrierung von Windows-Geräten
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 02cc111f8991a855db4f05360e54598af511f28f
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="set-up-enrollment-for-windows-devices"></a>Registrierung von Windows-Geräten

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Dieses Thema hilft IT-Administratoren, die Windows-Registrierung für ihre Benutzer zu vereinfachen. Sobald Sie [Intune eingerichtet](setup-steps.md) haben, können Benutzer Windows-Geräte registrieren, indem sie sich mit ihrem Geschäfts-, Schul- oder Unikonto [anmelden](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows).  

Als Intune-Administrator können Sie die Registrierung auf folgende Weise vereinfachen:
- [Aktivieren der automatischen Registrierung](#enable-windows-10-automatic-enrollment) (Azure AD Premium erforderlich)
- [CNAME-Registrierung](#simplify-windows-enrollment-without-azure-ad-premium)
- [Aktivieren der Massenregistrierung](windows-bulk-enroll.md) (Azure AD Premium und Windows Configuration Designer erforderlich)

Zwei Faktoren bestimmen, wie Sie die Registrierung von Windows-Geräten vereinfachen können:

- **Verwenden Sie Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) ist in Enterprise Mobility + Security und in anderen Lizenzierungsplänen enthalten.
- **Welche Versionen von Windows-Clients werden von Benutzern registriert?** <br>Windows 10-Geräte können automatisch durch Hinzufügen eines Geschäfts-oder Schulkontos registriert werden. Frühere Versionen müssen mithilfe der Unternehmensportal-App registriert werden.

||**Azure AD Premium**|**AD (Sonstiges)**|
|----------|---------------|---------------|  
|**Windows 10**|[Automatische Registrierung](#enable-windows-10-automatic-enrollment) |[Benutzerregistrierung](#enable-windows-enrollment-without-azure-ad-premium)|
|**Frühere Windows-Versionen**|[Benutzerregistrierung](#enable-windows-enrollment-without-azure-ad-premium)|[Benutzerregistrierung](#enable-windows-enrollment-without-azure-ad-premium)|

Organisationen, die die automatische Registrierung nutzen, können mithilfe der Windows Configuration Designer-App auch [Geräte für die Massenregistrierung](windows-bulk-enroll.md) konfigurieren.

**Unterstützung mehrerer Benutzer**<br>
Für Geräte, die das Windows 10 Creators Update ausführen und in die Azure Active Directory-Domäne eingebunden sind, haben wir Unterstützung für die Mehrbenutzerverwaltung hinzugefügt. Wenn sich Standardbenutzer mit ihren Azure AD-Anmeldeinformationen anmelden, erhalten sie Apps und Richtlinien, die ihrem Benutzernamen zugewiesen wurden. Benutzer können das Unternehmensportal derzeit nicht für Self-Service-Szenarien beispielsweise zum Installieren von Apps verwenden.

[!INCLUDE [AAD-enrollment](./includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>Vereinfachen der Windows-Registrierung ohne Azure AD Premium
Sie können die Registrierung für Ihre Benutzer vereinfachen, indem Sie einen Domänennamenserver-Alias (DNS) (Eintragstyp CNAME) erstellen, der Registrierungsanforderungen automatisch an Intune-Server umleitet. Wenn Sie keinen DNS-CNAME-Ressourceneintrag erstellen, müssen Benutzer beim Herstellen einer Verbindung mit Intune den Intune-Servernamen angeben.

**Schritt 1: Erstellen von CNAME-Einträgen** (optional)<br>
Erstellen Sie CNAME-DNS-Ressourceneinträge für die Domäne des Unternehmens. Wenn die Website Ihres Unternehmens beispielsweise „contoso.com“ heißt, würden Sie einen CNAME im DNS erstellen, der „EnterpriseEnrollment.contoso.com“ an „enterpriseenrollment-s.manage.microsoft.com“ umleitet.

Obwohl die Erstellung von CNAME DNS-Einträgen optional ist, vereinfachen diese die Registrierung für Benutzer. Wenn kein CNAME-Eintrag für die Registrierung gefunden wurde, werden Benutzer aufgefordert, manuell den MDM-Servernamen „enrollment.manage.microsoft.com“ einzugeben.

|Typ|Hostname|Verweist auf|TTL|
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 Stunde|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 Stunde|

Wenn Sie mehr als ein UPN-Suffix haben, müssen Sie einen CNAME für jeden Domänennamen erstellen und jeden auf EnterpriseEnrollment-s.manage.microsoft.com zeigen. Wenn Benutzer bei Contoso name@contoso.com sowie name@us.contoso.com und name@eu.constoso.com als E-Mail/UPN verwenden, sollte der Contoso-DNS-Administrator die folgenden CNAMEs erstellen:

|Typ|Hostname|Verweist auf|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 Stunde|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 Stunde|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 Stunde|

`EnterpriseEnrollment-s.manage.microsoft.com` – Unterstützt eine Umleitung zum Intune-Dienst mit Domänenerkennung anhand des E-Mail-Domänennamens

Es kann bis zu 72 Stunden dauern, bis Änderungen an DNS-Einträgen vollständig verteilt sind. Sie können die DNS-Änderung in Intune erst überprüfen, wenn der DNS-Eintrag verteilt ist.

**Schritt 2: Verifizieren des CNAME-Eintrags** (optional)<br>
Wählen Sie im Azure-Portal **Weitere Dienste** > **Überwachung und Verwaltung** > **Intune** aus. Wählen Sie auf dem Blatt „Intune“ die Option **Geräte registrieren** > **Windows-Registrierung aktivieren** aus. Geben Sie die URL der Unternehmenswebsite in das Feld **Verifizierten Domänennamen eingeben** ein, und wählen Sie anschließend **Automatische Erkennung testen** aus.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Benutzern mitteilen, wie Windows-Geräte registriert werden
Benutzern erklären, wie sie ihre Windows-Geräte registrieren können, und sie darüber informieren, was sie erwarten können, wenn ihre Geräte verwaltet werden.

> [!NOTE]
> Endbenutzer müssen über Microsoft Edge auf die Website des Unternehmensportals zugreifen, um Windows-Anwendungen anzuzeigen, die Sie für bestimmte Versionen von Windows zugewiesen haben. Andere Browser wie Google Chrome, Mozilla Firefox und Internet Explorer unterstützen diese Art der Filterung nicht.

Registrierungsanleitungen für Endbenutzer finden Sie unter [Registrieren Ihres Windows-Geräts bei Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). Sie können Benutzer auch auf [Welche Informationen erhält mein Unternehmen, wenn ich mein Gerät in Intune registriere?](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows) verweisen.

>[!IMPORTANT]
> Wenn Sie zwar die automatische Registrierung für die Verwaltung mobiler Geräte nicht aktiviert haben, Sie aber über Windows 10-Geräte verfügen, die mit Azure AD verknüpft wurden, werden nach der Registrierung zwei Datensätze in der Intune-Konsole angezeigt. Dies können Sie vermeiden, wenn Sie sicherstellen, dass Benutzer mit Geräten, die mit Azure AD verknüpft sind, zu **Konten** > **Access work or school** (Auf Arbeits- oder Schul- bzw. Unikonto zugreifen) navigieren und unter Verwendung dieses Kontos eine **Verbindung** herstellen. 

Weitere Informationen zu Endbenutzeraufgaben finden Sie unter [Ressourcen zu Endbenutzerszenarios in Microsoft Intune](end-user-educate.md).

## <a name="next-steps"></a>Nächste Schritte

- [Überlegungen bei der Verwaltung von Windows-Geräten mit Intune in Azure](/intune-classic/deploy-use/intune-on-azure).
