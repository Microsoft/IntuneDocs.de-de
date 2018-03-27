---
title: Konfigurieren von Skycure für die Verwendung von Azure Active Directory Single Sign-On (SSO)
description: Skycure für die Verwendung von Azure Active Directory Single Sign-On (SSO) konfigurieren
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 34d5d359-5c7c-4225-a205-8ce890b6f890
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: aef978e3d8431238a5b717628b13b875aa5b89cc
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="configure-skycure-to-use-azure-active-directory-single-sign-on-sso"></a>Skycure für die Verwendung von Azure Active Directory Single Sign-On (SSO) konfigurieren

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Azure AD-SSO wird verwendet, wenn Sie Intune mit Skycure integrieren. Dies sind die wichtigsten Vorteile:

-   **Administratoren** können dieselben Anmeldeinformationen verwenden, ohne sie bei jedem An- und Abmelden in den Microsoft-Portalen (Intune, Azure) und der Skycure-Verwaltungskonsole erneut eingeben zu müssen.

-   **Endbenutzer** können dieselben Azure AD-Anmeldeinformationen verwenden, ohne sie bei jedem An- und Abmelden in den Skycure-Apps erneut eingeben zu müssen.

Im Folgenden finden Sie die Schritte, um Skycure mit Azure Active Directory Single Sign-On (SSO) zu integrieren.

## <a name="to-retrieve-the-azure-active-directory-tenant-id"></a>So rufen Sie die Azure Active Directory-Mandanten-ID ab

Sie müssen die Azure AD-Mandanten-ID abrufen.

1.  Navigieren Sie zum [Azure-Portal](https://portal.azure.com/), und melden Sie sich mit Ihren Anmeldeinformationen an.

2.  Wählen Sie im **Dashboard** **Azure Active Directory** aus.

![Azure AD-Dashboard](../media/mtp/skycure-sso-1.png)

1.  Wählen Sie auf dem Blatt **Azure Active Directory** **Eigenschaften** aus.

![Blatt „Azure AD-Eigenschaften“](../media/mtp/skycure-sso-2.png)

1.  Klicken Sie auf dem Blatt **Azure Active Directory Properties** (Azure Active Directory-Eigenschaften) unter **Tenant Directory ID** (Directory-Mandanten-ID) auf das **Kopiersymbol**.

> Fügen Sie den kopierten Directory-ID-Wert in eine Textdatei ein, damit Sie ihn später verwenden können. Der Directory-ID-Wert ist später beim Integrationsvorgang von Skycure und Intune erforderlich.

![Azure AD-Dashboard](../media/mtp/skycure-sso-3.png)

## <a name="allow-skycure-to-communicate-with-azure-active-directory"></a>Zulassen von Kommunikation zwischen Skycure und Azure Active Directory

1.  Geben Sie folgende URL in Ihren Browser ein. Geben Sie anstatt der **DIRECTORY_ID** Ihre Azure Active Directory-Mandanten-ID ein, die Sie in die Textdatei kopiert haben.

        https://login.microsoftonline.com/<DIRECTORY_ID>/oauth2/authorize?client_id=28fd67fdb1794629a8b0dad420b697c7&prompt=admin_consent&redirect_uri=https%3A%2F%2Fmc.skycure.com%2Fapi%2Fexternal%2Fmdm%2Faad_app_consent%2Fmanagement_callback&response_type=code

2.  Sie müssen sich mit Ihren Azure Active Directory-Anmeldeinformationen anmelden. Klicken Sie auf **Accept** (Annehmen), um den Vorgang fortzusetzen.

![Azure AD, Anmeldeseite](../media/mtp/skycure-sso-4.png)

## <a name="create-an-azure-ad-security-group-for-skycure-optional"></a>Erstellen einer Azure AD-Sicherheitsgruppe für Skycure (optional)

Möglicherweise möchten Sie eine dedizierte Benutzergruppe erstellen, die z.B. Skycure-Benutzer enthält. Dies kann bei der Analyse von Skycure-Aktivität in den Berichten hilfreich sein.

-   Erfahren Sie mehr über das [Erstellen einer Gruppe und Hinzufügen von Mitgliedern in Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).

> [!NOTE] 
> Sie können auch eine vorhandene Azure AD-Sicherheitsgruppe verwenden.

## <a name="configure-the-azure-ad-account-to-integrate-intune-with-skycure"></a>Konfigurieren des Azure AD-Kontos für die Integration von Skycure und Intune

1.  Geben Sie in der [Skycure-Verwaltungskonsole](https://aad.skycure.com/) die zuvor in der Textdatei gespeicherte Azure Active Directory-Mandanten-ID ein.

![Skycure-Verwaltungskonsole, Feld „Azure AD-Mandanten-ID“](../media/mtp/skycure-sso-5.png)

> [!IMPORTANT] 
> Skycure überprüft durch Abfragen von Azure AD, ob die Azure AD-Mandanten-ID vorhanden ist. Wenn Skycure sie gefunden hat, kann der Administrator mit dem nächsten Schritt fortfahren: der grundlegenden Installation.

## <a name="next-steps"></a>Nächste Schritte

[Herunterladen der Skycure iOS-App-Konfigurationsrichtlinie](/intune-classic/deploy-use/download-skycure-ios-app-configuration-policy)
