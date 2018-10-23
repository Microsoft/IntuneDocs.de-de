---
title: Vorteile des Intune App SDK
titlesuffix: Microsoft Intune
description: Das Intune App Software Development Kit (SDK) ist für iOS- und Android-Plattformen erhältlich und ermöglicht Verwaltungsfunktionen für mobile Anwendungen mit Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fc49d7ba7cdc5b986c06f8a84ececc8339a812a2
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2018
ms.locfileid: "49425103"
---
# <a name="intune-app-sdk-overview"></a>Übersicht über das Intune App SDK
Das für IOS und Android verfügbare Intune App SDK aktiviert Ihre App für Intune-App-Schutzrichtlinien. Es zielt darauf ab, die vom App-Entwickler vorzunehmenden Codeänderungen zu minimieren. Sie werden feststellen, dass Sie die meisten SDK-Features aktivieren können, ohne das Verhalten Ihrer App ändern zu müssen. Um die Benutzerfreundlichkeit der App für Endbenutzer und IT-Administratoren zu verbessern, können Sie unsere APIs verwenden und so das App-Verhalten für Features anpassen, die Ihre Mitwirkung erfordern.

Nachdem Sie Ihre App für App-Schutzrichtlinien aktiviert haben, können IT-Administratoren diese Richtlinien zum Schutz ihrer Unternehmensdaten innerhalb der App bereitstellen.

## <a name="app-protection-features"></a>App-Schutzfunktionen

Es folgen Beispiele von Intune-App-Schutzfunktionen, die mit dem SDK aktiviert werden können.

### <a name="control-users-ability-to-move-corporate-files"></a>Steuern der Möglichkeit von Benutzern, Unternehmensdateien zu verschieben
IT-Administratoren können steuern, wohin Geschäfts-, Schul- oder Unidaten in der App verschoben werden können. So kann beispielsweise eine Richtlinie bereitgestellt werden, mit der verhindert wird, dass Unternehmensdaten in der Cloud gesichert werden.

### <a name="configure-clipboard-restrictions"></a>Konfigurieren von Einschränkungen für die Zwischenablage
IT-Administratoren können in von Intune verwalteten Apps das Verhalten der Zwischenablage konfigurieren. Sie können beispielsweise eine Richtlinie bereitstellen, die verhindert, dass Endbenutzer Daten aus der App ausschneiden oder kopieren und diese in eine nicht verwaltete, persönliche App einfügen.

### <a name="enforce-encryption-on-saved-data"></a>Erzwingen der Verschlüsselung von gespeicherten Daten
IT-Administratoren können mit einer Richtlinie erzwingen, dass auf dem Gerät gespeicherte Daten verschlüsselt werden.

### <a name="remotely-wipe-corporate-data"></a>Remotezurücksetzung von Unternehmensdaten
IT-Administratoren können Unternehmensdaten in einer von Intune verwalteten App remote zurücksetzen. Diese Funktion basiert auf der Identität, und es werden nur Dateien gelöscht, die der Unternehmensidentität des Endbenutzers zugeordnet sind. Hierfür ist die Mitwirkung der App erforderlich. Die App kann die Identität, für die die Zurücksetzung erfolgen soll, basierend auf den Benutzereinstellungen festlegen. Fehlen solche spezifischen Benutzereinstellungen in der App, besteht das Standardverhalten darin, das Anwendungsverzeichnis zu löschen und den Endbenutzer darüber zu informieren, dass der Zugriff entfernt wurde.

### <a name="enforce-the-use-of-a-managed-browser"></a>Erzwingen der Verwendung eines verwalteten Browsers
IT-Administratoren können erzwingen, dass Weblinks in der App mit der [Intune Managed Browser-App](app-configuration-managed-browser.md) geöffnet werden. Durch diese Funktion wird sichergestellt, dass in einer Unternehmensumgebung angezeigte Links in der Domäne von Apps, die von Intune verwaltet werden, beibehalten werden.

### <a name="enforce-a-pin-policy"></a>Erzwingen einer PIN-Richtlinie
IT-Administratoren können erzwingen, dass Endbenutzer eine PIN eingeben, ehe sie in der App Zugriff auf Unternehmensdaten erhalten. Dadurch wird sichergestellt, dass es sich bei der Person, die die App verwendet, um dieselben Person handelt, die sich ursprünglich mit ihrem Geschäfts-, Schul- oder Unikonto angemeldet hat. Wenn Endbenutzer ihre PIN konfigurieren, verwendet das Intune App SDK Azure Active Directory, um die Anmeldeinformationen der Endbenutzer mit den Daten des registrierten Intune-Kontos abzugleichen.

### <a name="require-users-to-sign-in-with-work-or-school-account-for-app-access"></a>Benutzer zwingen, sich für den Zugriff auf die App mit einem Geschäfts-, Schul- oder Unikonto anzumelden
IT-Administratoren können Benutzer zwingen, sich für den Zugriff auf die App mit ihrem Geschäfts-, Schul- oder Unikonto anzumelden. Das Intune App SDK verwendet Azure Active Directory für die Bereitstellung von einmaligem Anmelden (SSO), damit die einmal eingegebenen Anmeldeinformationen auch für nachfolgende Anmeldungen gelten. Darüber hinaus wird auch die Authentifizierung von Lösungen für die Identitätsverwaltung im Verbund mit Azure Active Directory unterstützt.

### <a name="check-device-health-and-compliance"></a>Überprüfen der Geräteintegrität und -konformität
IT-Administratoren können die Integrität des Geräts und dessen Konformität mit den Intune-Richtlinien abgleichen, bevor Endbenutzer auf die App zugreifen. Unter iOS überprüft diese Richtlinie, ob es sich um ein Gerät handelt, auf das ein Jailbreak angewendet wurde. Unter Android überprüft diese Richtlinie, ob es sich um ein Gerät handelt, das gerootet wurde.

### <a name="multi-identity-support"></a>Unterstützung mehrerer Identitäten
Die Unterstützung mehrerer Identitäten (Multi-Identity Support) ist ein Feature des SDK, das die Koexistenz von per Richtlinie verwalteten Geschäftskonten und nicht verwalteten Privatkonten in einer App gestattet.

So konfigurieren beispielsweise viele Benutzer in den mobilen Office-App für iOS und Android sowohl Unternehmens-E-Mail-Konten als auch private E-Mail-Konten. Wenn ein Benutzer auf Daten im Firmenkonto zugreift, muss der IT-Administrator sicher sein, dass die App-Schutzrichtlinie gilt. Wenn ein Benutzer jedoch auf ein privates E-Mail-Konto zugreift, sollten sich diese Daten außerhalb der Kontrolle des IT-Administrators befinden. Das Intune App SDK erreicht dies durch Begrenzen der App-Schutzrichtlinie auf **ausschließlich** die Firmenidentität in der App.

Das Feature für mehrere Identitäten hilft Ihnen, das Datenschutzproblem zu lösen, mit dem sich Organisation bei Store-Apps auseinandersetzen müssen, die sowohl Privat- als auch Geschäftskonten unterstützen.
 
### <a name="app-protection-without-device-enrollment"></a>App-Schutz ohne Geräteregistrierung

>[!IMPORTANT]
>Der Intune-App-Schutz ohne Geräteregistrierung ist mit den Intune App Wrapping Tools, dem Intune App SDK für Android, dem Intune App SDK für iOS und der Intune App SDK-Xamarin-Bindung verfügbar.

Viele Benutzer privater Geräten möchten auf Unternehmensdaten zugreifen, ohne ihr privates Gerät bei einem MDM-Anbieter (Mobile Device Management, Verwaltung mobiler Geräte) zu registrieren. Da die MDM-Registrierung eine globale Kontrolle des Geräts voraussetzt, zögern viele Benutzer häufig, diese globale Kontrolle über ihr privates Gerät an das Unternehmen zu übergeben.

Ein App-Schutz ohne Geräteregistrierung ermöglicht dem Microsoft Intune-Dienst das direkte Bereitstellen einer App-Schutzrichtlinie für eine App, ohne dass ein Geräteverwaltungskanal die Richtlinie bereitstellen muss.

### <a name="on-demand-application-vpn-connections-with-citrix-mvpn"></a>Bedarfsgesteuerte VPN-Verbindungen mit Anwendungen mit Citrix mVPN 
Sie können Geräte und Apps mit einer Kombination aus Citrix XenMobile MDX und Microsoft Intune verwalten. Dadurch können Sie Apps mit der Intune-App-Schutzrichtlinie verwalten, während Sie die mVPN-Technologie von Citrix verwenden. Die Integration mit Citrix mit dem Intune App Wrapping Tool (mit dem Flag „-citrix“) steht für das Intune App SDK für iOS und Android zur Verfügung.
 
Weitere Informationen zu Citrix MDX finden Sie in den Artikeln zu den [Grundlagen zum MDX-Toolkit](http://docs.citrix.com/en-us/mdx-toolkit/10/about-mdx-toolkit.html), zum [Citrix MDX-App-Wrapper für iOS](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-ios.html) und zum [Citrix MDX-App-Wrapper für Android](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-android.html).
