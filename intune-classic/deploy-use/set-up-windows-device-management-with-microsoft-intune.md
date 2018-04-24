---
title: Einrichten der Windows-Geräteverwaltung mit Microsoft Intune
description: Aktivieren Sie die Verwaltung mobiler Geräte (Mobile Device Management, MDM) für Windows-Geräte mit Microsoft Intune.
keywords: ''
author: NathBarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fb2d724cc87ffdc506eda8d5ea2330ab9aacd3e9
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-windows-device-management"></a>Einrichten der Windows-Geräteverwaltung

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Dieses Thema hilft IT-Administratoren, die Windows-Registrierung für ihre Benutzer zu vereinfachen.  Windows-Geräte können ohne zusätzliche Schritte registriert werden, aber Sie können die Registrierung für Ihre Benutzer vereinfachen.

Zwei Faktoren bestimmen, wie Sie die Registrierung von Windows-Geräten vereinfachen können:
- **Verwenden Sie Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) ist in Enterprise Mobility + Security und in anderen Lizenzierungsplänen enthalten.
- **Welche Versionen von Windows-Clients werden registriert?** <br>Windows 10-Geräte können automatisch durch Hinzufügen eines Geschäfts-oder Schulkontos registriert werden. Frühere Versionen müssen mithilfe der Unternehmensportal-App registriert werden.

||**Azure AD Premium**|**AD (Sonstiges)**|
|----------|---------------|---------------|  
|**Windows 10**|[Automatische Registrierung](#enable-windows-10-automatic-enrollment) |[Benutzerregistrierung](#enable-windows-enrollment-without-automatic-enrollment)|
|**Frühere Windows-Versionen**|[Benutzerregistrierung](#enable-windows-enrollment-without-automatic-enrollment)|[Benutzerregistrierung](#enable-windows-enrollment-without-automatic-enrollment)|

[!INCLUDE [AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-automatic-enrollment"></a>Aktivieren der Windows-Registrierung ohne automatische Registrierung
Sie können Benutzern das Registrieren ihrer Geräte ohne automatische Azure AD Premium-Registrierung ermöglichen. Weisen Sie Benutzern Lizenzen zu, damit sie sich registrieren können, sobald sie den privat genutzten Geräten ihre Geschäftskonten hinzugefügt haben oder Ihrer Azure AD mit den firmeneigenen Geräten beigetreten sind. Das Erstellen einer DNS-Alias (CNAME-Eintragstyp) erleichtert Benutzern das Registrieren ihrer Geräte. Wenn Sie DNS-CNAME-Ressourceneinträge erstellen, können Benutzer sich mit Intune verbinden und dort registrieren, ohne einen Servernamen eingeben zu müssen.

**Schritt 1: Erstellen von CNAME-Einträgen** (optional)<br>
Erstellen Sie CNAME-DNS-Ressourceneinträge für die Domäne des Unternehmens. Wenn die Website Ihres Unternehmens beispielsweise „contoso.com“ heißt, würden Sie einen CNAME im DNS erstellen, der „EnterpriseEnrollment.contoso.com“ an „enterpriseenrollment-s.manage.microsoft.com“ umleitet.

Obwohl die Erstellung von CNAME DNS-Einträgen optional ist, vereinfachen diese die Registrierung für Benutzer. Wenn kein CNAME-Eintrag für die Registrierung gefunden wurde, werden Benutzer aufgefordert, manuell den MDM-Servernamen „enrollment.manage.microsoft.com“ einzugeben.

Existieren mehrere überprüfte Domänen, erstellen Sie einen CNAME-Eintrag für jede Domäne. Die CNAME-Ressourceneinträge müssen die folgenden Informationen enthalten:

CNAME-Ressourceneinträge müssen die folgenden Informationen enthalten:

|TYP|Hostname|Verweist auf|TTL|
|--------|-------------|-------------|-------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 Stunde|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 Stunde|

`EnterpriseEnrollment-s.manage.microsoft.com` – unterstützt eine Umleitung zum Intune-Dienst mit Domänenerkennung anhand des E-Mail-Domänennamens.

Wenn Ihr Unternehmen mehrere Domänen für die Anmeldeinformationen der Benutzer verwendet, erstellen Sie CNAME-Einträge für jede Domäne.

Wenn der Name Ihrer Unternehmenswebsite beispielsweise contoso.com lautet, erstellen Sie einen CNAME in DNS, der EnterpriseEnrollment.contoso.com an EnterpriseEnrollment-s.manage.microsoft.com umleitet. Es kann bis zu 72 Stunden dauern, bis Änderungen an DNS-Einträgen vollständig verteilt sind. Sie können die DNS-Änderung in Intune erst überprüfen, wenn der DNS-Eintrag verteilt ist.

**Schritt 2: Verifizieren des CNAME-Eintrags** (optional)<br>
Wählen Sie in der [Intune-Verwaltungskonsole](https://manage.microsoft.com) **Admin** &gt; **Verwaltung mobiler Geräte** &gt; **Windows** aus. Geben Sie die URL der überprüften Domäne der Unternehmenswebsite in das Feld **Verifizierten Domänennamen eingeben** ein, und wählen Sie anschließend **Automatische Erkennung testen** aus.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Benutzern mitteilen, wie Windows-Geräte registriert werden
Benutzern erklären, wie sie ihre Windows-Geräte registrieren können, und sie darüber informieren, was sie erwarten können, wenn ihre Geräte verwaltet werden.
Registrierungsanleitungen für Endbenutzer finden Sie unter [Registrieren Ihres Windows-Geräts bei Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). Sie können Benutzer auch auf [Was kann mein IT-Administrator sehen, wenn ich mein Gerät bei Intune registriere?](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows) verweisen.

Weitere Informationen zu Endbenutzeraufgaben finden Sie unter [Ressourcen zu Endbenutzerszenarios in Microsoft Intune](/intune/end-user-educate).

### <a name="see-also"></a>Siehe auch
[Voraussetzungen für die Registrierung von Geräten in Microsoft Intune](prerequisites-for-enrollment.md)
