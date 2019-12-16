---
title: Registrierung von Windows-Geräten mit Microsoft Intune
titleSuffix: ''
description: Registrierung von Windows-Geräten
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0b84cd52dfe2eb6332ddbc89bc00a17ec3361b79
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000430"
---
# <a name="set-up-enrollment-for-windows-devices"></a>Registrierung von Windows-Geräten

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Dieser Artikel hilft IT-Administratoren, die Windows-Registrierung für ihre Benutzer zu vereinfachen. Sobald Sie [Intune eingerichtet](../fundamentals/setup-steps.md) haben, können Benutzer Windows-Geräte registrieren, indem sie sich mit ihrem Geschäfts-, Schul- oder Unikonto [anmelden](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows).  

Als Intune-Administrator können Sie die Registrierung auf folgende Weise vereinfachen:

- [Aktivieren der automatischen Registrierung](#enable-windows-10-automatic-enrollment) (Azure AD Premium erforderlich)
- [CNAME-Registrierung](#simplify-windows-enrollment-without-azure-ad-premium)
- [Aktivieren der Massenregistrierung](../windows-bulk-enroll.md) (Azure AD Premium und Windows Configuration Designer erforderlich)

Zwei Faktoren bestimmen, wie Sie die Registrierung von Windows-Geräten vereinfachen können:

- **Verwenden Sie Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) ist in Enterprise Mobility + Security und in anderen Lizenzierungsplänen enthalten.
- **Welche Versionen von Windows-Clients werden von Benutzern registriert?** <br>Windows 10-Geräte können automatisch durch Hinzufügen eines Geschäfts-oder Schulkontos registriert werden. Frühere Versionen müssen mithilfe der Unternehmensportal-App registriert werden.

||**Azure AD Premium**|**AD (Sonstiges)**|
|----------|---------------|---------------|  
|**Windows 10**|[Automatische Registrierung](#enable-windows-10-automatic-enrollment) |Benutzerregistrierung|
|**Frühere Windows-Versionen**|Benutzerregistrierung|Benutzerregistrierung|

Organisationen, die die automatische Registrierung nutzen, können mithilfe der Windows Configuration Designer-App auch [Geräte für die Massenregistrierung](../windows-bulk-enroll.md) konfigurieren.

## <a name="device-enrollment-prerequisites"></a>Voraussetzungen für die Geräteregistrierung

Bevor ein Administrator Geräte in Intune für die Verwaltung registrieren kann, müssen Lizenzen bereits dem Administratorkonto zugewiesen sein. [Informationen zum Zuweisen von Lizenzen für die Geräteregistrierung](../fundamentals/licenses-assign.md)

## <a name="multi-user-support"></a>Unterstützung mehrerer Benutzer

Intune unterstützt mehrere Benutzer für Geräte, die jeweils

- das Windows 10 Creators Update ausführen
- und mit der Azure Active Directory-Domäne verknüpft sind.

Wenn sich Standardbenutzer mit ihren Azure AD-Anmeldeinformationen anmelden, erhalten sie Apps und Richtlinien, die ihrem Benutzernamen zugewiesen wurden. Ausschließlich der [primäre Benutzer](../remote-actions/find-primary-user.md) kann das Unternehmensportal für Self-Service-Szenarios wie das Installieren von Apps und Ausführen von Geräteaktionen (Entfernen, Zurücksetzen) verwenden. Für freigegebene Windows 10-Geräte, denen kein primärer Benutzer zugewiesen ist, kann das Unternehmensportal noch immer zum Installieren von verfügbaren Apps verwendet werden.

[!INCLUDE [AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>Vereinfachen der Windows-Registrierung ohne Azure AD Premium
Um die Registrierung zu vereinfachen, erstellen Sie einen Domänennamenserver-Alias (DNS; Eintragstyp CNAME), der Registrierungsanforderungen an Intune-Server umleitet. Andernfalls müssen Benutzer, die eine Verbindung mit Intune herstellen möchten, während der Registrierung den Intune-Servernamen eingeben.

**Schritt 1: Erstellen von CNAME-Einträgen** (optional)<br>
Erstellen Sie CNAME-DNS-Ressourceneinträge für die Domäne des Unternehmens. Wenn die Website Ihres Unternehmens beispielsweise „contoso.com“ heißt, würden Sie einen CNAME im DNS erstellen, der „EnterpriseEnrollment.contoso.com“ an „enterpriseenrollment-s.manage.microsoft.com“ umleitet.

Obwohl die Erstellung von CNAME DNS-Einträgen optional ist, vereinfachen diese die Registrierung für Benutzer. Wenn kein CNAME-Eintrag für die Registrierung gefunden wurde, werden Benutzer aufgefordert, manuell den MDM-Servernamen „enrollment.manage.microsoft.com“ einzugeben.

|Typ|Hostname|Verweist auf|TTL|
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 Stunde|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 Stunde|

Wenn das Unternehmen mehr als ein UPN-Suffix verwendet, müssen Sie einen CNAME für jeden Domänennamen erstellen und jeden auf EnterpriseEnrollment-s.manage.microsoft.com zeigen. Benutzer bei Contoso verwenden beispielsweise die folgenden Formate für E-Mail/UPN:

- name@contoso.com
- name@us.contoso.com
- name@eu.contoso.com

Der Contoso DNS-Administrator sollte die folgenden CNAMEs erstellen:

|Typ|Hostname|Verweist auf|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 Stunde|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 Stunde|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 Stunde|

`EnterpriseEnrollment-s.manage.microsoft.com` – Unterstützt eine Umleitung zum Intune-Dienst mit Domänenerkennung anhand des E-Mail-Domänennamens

Es kann bis zu 72 Stunden dauern, bis Änderungen an DNS-Einträgen vollständig verteilt sind. Sie können die DNS-Änderung in Intune erst überprüfen, wenn der DNS-Eintrag verteilt ist.

## <a name="additional-endpoints-are-supported-but-not-recommended"></a>Zusätzliche Endpunkte werden unterstützt, aber nicht empfohlen
„EnterpriseEnrollment-s.manage.microsoft.com“ ist der bevorzugte vollqualifizierte Domänenname für die Registrierung, es gibt jedoch zwei andere Endpunkte, die bereits von Kunden verwendet wurden und unterstützt werden. „EnterpriseEnrollment.manage.microsoft.com“ (ohne „-s“) und „manage.microsoft.com“ sind beide gültige Ziele für den Server für die automatische Ermittlung, allerdings muss der Benutzer dann auf einer Bestätigungsmeldung auf „OK“ tippen. Wenn Sie auf „EnterpriseEnrollment-s.manage.microsoft.com“ zeigen, muss der Benutzer keinen zusätzlichen Bestätigungsschritt vornehmen, weshalb dies die empfohlene Konfiguration ist.

## <a name="alternate-methods-of-redirection-are-not-supported"></a>Alternative Umleitungsmethoden werden nicht unterstützt
Das Verwenden einer anderen Methode als die CNAME-Konfiguration wird nicht unterstützt. Beispielsweise wird die Verwendung eines Proxyservers zum Umleiten von „enterpriseenrollment.contoso.com/EnrollmentServer/Discovery.svc“ auf „enterpriseenrollment-s.manage.microsoft.com/EnrollmentServer/Discovery.svc“ oder „manage.microsoft.com/EnrollmentServer/Discovery.svc“ nicht unterstützt.

**Schritt 2: Verifizieren des CNAME-Eintrags** (optional)<br>
1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Geräte** > **Windows** > **Windows-Registrierung** > **CNAME-Validierung** aus.
2. Geben Sie in das Feld **Domäne** die Unternehmenswebsite ein, und wählen Sie dann **Testen** aus.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Benutzern mitteilen, wie Windows-Geräte registriert werden
Benutzern erklären, wie sie ihre Windows-Geräte registrieren können, und sie darüber informieren, was sie erwarten können, wenn ihre Geräte verwaltet werden.

> [!NOTE]
> Endbenutzer müssen über Microsoft Edge auf die Website des Unternehmensportals zugreifen, um Windows-Anwendungen anzuzeigen, die Sie für bestimmte Versionen von Windows zugewiesen haben. Andere Browser wie Google Chrome, Mozilla Firefox und Internet Explorer unterstützen diese Art der Filterung nicht.

Registrierungsanleitungen für Endbenutzer finden Sie unter [Registrieren Ihres Windows-Geräts bei Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). Sie können Benutzer auch auf [Welche Informationen erhält mein Unternehmen, wenn ich mein Gerät in Intune registriere?](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows) verweisen.

>[!IMPORTANT]
> Wenn Sie zwar die automatische Registrierung für die Verwaltung mobiler Geräte nicht aktiviert haben, Sie aber über Windows 10-Geräte verfügen, die mit Azure AD verknüpft wurden, werden nach der Registrierung zwei Datensätze in der Intune-Konsole angezeigt. Dies können Sie vermeiden, wenn Sie sicherstellen, dass Benutzer mit Geräten, die mit Azure AD verknüpft sind, zu **Konten** > **Access work or school** (Auf Arbeits- oder Schul- bzw. Unikonto zugreifen) navigieren und unter Verwendung dieses Kontos eine **Verbindung** herstellen. 

Weitere Informationen zu Endbenutzeraufgaben finden Sie unter [Ressourcen zu Endbenutzerszenarios in Microsoft Intune](../fundamentals/end-user-educate.md).

## <a name="registration-and-enrollment-cnames"></a>Registrieren von CNAME-Einträgen
Azure Active Directory umfasst einen weiteren CNAME, der für die Registrierung von iOS-, Android- und Windows-Geräten verwendet wird. Für den bedingten Intune-Zugriff müssen Geräte registriert werden. Dieser Vorgang wird auch als „dem Arbeitsplatz beitreten“ bezeichnet. Wenn Sie den bedingten Zugriff verwenden möchten, müssen Sie auch den CNAME-Eintrag „EnterpriseRegistration“ für jeden Unternehmensnamen konfigurieren.

| Typ | Hostname | Verweist auf | TTL |
| --- | --- | --- | --- |
| NAME | EnterpriseRegistration. company_domain.com | EnterpriseRegistration.windows.net | 1 Stunde|

Weitere Informationen zur Geräteregistrierung finden Sie unter [Verwalten von Geräteidentitäten mit dem Azure-Portal](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal).

## <a name="windows-10-auto-enrollment-and-device-registration"></a>Automatische Registrierung und Geräteregistrierung für Windows 10
Obwohl die Erstellung von CNAME DNS-Einträgen optional ist, vereinfachen diese die Registrierung für Benutzer. Wenn kein CNAME-Eintrag für die Registrierung gefunden wurde, werden Benutzer aufgefordert, manuell den MDM-Servernamen „enrollment.manage.microsoft.us“ einzugeben.

| Typ | Hostname | Verweist auf | TTL |
| --- | --- | --- | --- |
| CNAME | EnterpriseEnrollment.company_domain.com | EnterpriseEnrollment-s.manage.microsoft.us | 1 Stunde|
|CNAME | EnterpriseRegistration.company_domain.com | EnterpriseRegistration.windows.net | 1 Stunde |


## <a name="next-steps"></a>Nächste Schritte

- [Überlegungen bei der Verwaltung von Windows-Geräten mit Intune in Azure](../fundamentals/intune-legacy-pc-client.md).
