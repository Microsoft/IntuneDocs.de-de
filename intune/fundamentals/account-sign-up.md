---
title: Registrieren oder Anmelden bei Microsoft Intune
description: Informationen zum Registrieren für ein Microsoft Intune-Abonnement bzw. zur Anmeldung, um Ihr Abonnement zu beginnen
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f3ce07a-b718-42a9-bace-f99a8b8abd94
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78d38b72c9853a9eadaf71fcdff7567fc66d35ca
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73414670"
---
# <a name="sign-up-or-sign-in-to-microsoft-intune"></a>Registrieren oder Anmelden bei Microsoft Intune

In diesem Thema werden Systemadministratoren darauf hingewiesen, wie Sie sich für ein Intune-Konto anmelden können.

Bevor Sie sich für ein Intune-Konto anmelden, bestimmen Sie, ob Sie bereits ein Microsoft Online Services-Konto, ein Enterprise Agreement oder einen gleichwertigen Volumenlizenzvertrag besitzen. Ein Microsoft-Volumenlizenzvertrag oder andere Microsoft-Clouddienstabonnements wie Office 365 enthalten normalerweise ein Arbeits- oder Schulkonto.

Wenn Sie bereits über ein Arbeits- oder Schulkonto verfügen, **melden Sie sich mit diesem Konto an**, und fügen Sie Intune Ihrem Abonnement hinzu. Sie können sich auch für ein neues Konto **registrieren**, um Intune für Ihre Organisation zu verwenden.

>[!WARNING]
>Sie können kein bestehendes Arbeits- oder Schulkonto nach der Registrierung für ein neues Konto kombinieren.

## <a name="how-to-sign-up-for-intune"></a>Registrieren für Intune

1. Besuchen Sie die Seite für die [Intune-Registrierung](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20).

   ![Screenshot der Website für die Registrierung für das Microsoft Intune-Testkonto](./media/account-sign-up/account-sign-up-site.png)

2. Registrieren Sie sich auf der Registrierungsseite, oder melden Sie sich an, um ein neues Intune-Abonnement zu verwalten.

## <a name="post-sign-up-considerations"></a>Überlegungen nach der Registrierung

Nachdem Sie sich für ein neues Abonnement registriert haben, wird eine E-Mail mit Ihren Kontoinformationen an die von Ihnen bei der Registrierung angegebene E-Mail-Adresse gesendet. Diese E-Mail bestätigt, dass Ihr Abonnement aktiv ist.

Nach Abschluss des Registrierungsprozesses werden Sie an das Microsoft 365 Admin Center weitergeleitet, das zum Hinzuzufügen von Benutzern und Zuweisen von Lizenzen verwendet wird. Wenn Sie nur cloudbasierte Konten mit Ihrem standardmäßigen Domänennamen onmicrosoft.com verwenden werden, können Sie an diesem Punkt Benutzer hinzufügen und ihnen Lizenzen zuweisen. Wenn Sie jedoch planen, den [Domänennamen Ihres Unternehmens](custom-domain-name-configure.md) zu verwenden oder [Benutzerkontoinformationen aus dem lokalen Active Directory zu synchronisieren](users-add.md#sync-active-directory-and-add-users-to-intune), können Sie dieses Browserfenster schließen.

## <a name="sign-in-to-microsoft-intune"></a>Anmelden bei Microsoft Intune

Nachdem Sie sich für Intune registriert haben, können Sie sich auf jedem Gerät mit [unterstütztem Browser](supported-devices-browsers.md#intune-supported-web-browsers) bei [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) anmelden, um den Dienst zu verwalten.

Standardmäßig muss Ihr Konto über eine der folgenden Berechtigungen in Azure AD verfügen:

- Globaler Administrator
- Intune-Dienstadministrator (auch als Intune-Administrator bezeichnet)

Informationen zum Gewähren des Zugriffs, um den Dienst für Benutzer mit anderen Berechtigungen zu verwalten, finden Sie unter [Rollenbasierte Zugriffssteuerung](role-based-access-control.md).

### <a name="intune-admin-portal-url"></a>Intune-Verwaltungsportal-URL

Microsoft 365 Admin Center: https://devicemanagement.microsoft.com

Intune-Azure-Portal: https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade

Intune for Education: https://intuneeducation.portal.azure.com

Klassisches Intune-Portal: https://manage.microsoft.com. Das klassische Intune-Portal wird nur zum Verwalten von Geräten verwendet, die mit dem Intune-PC-Softwareclient registriert wurden.

### <a name="urls-for-intune-services-provided-by-office-365"></a>URLs für von Office 365 bereitgestellte Intune-Dienste

Microsoft 365 Business: https://portal.microsoft.com/adminportal

Mobile Geräteverwaltung von Office 365: https://portal.office.com/adminportal/home#/MifoDevices

## <a name="see-also"></a>Siehe auch

[Sie können sich nicht bei Office 365, Azure oder Intune anmelden](https://support.microsoft.com/help/2412085)
