---
title: Early Edition – Microsoft Intune
titlesuffix: ''
description: Early Edition für Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 8cd32a7ec99064a36d58a5a714406659d9d16675
ms.sourcegitcommit: 06f62ae989da6c60bac4a52ccd41b429f7367d8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2019
ms.locfileid: "55072438"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>Die Early Edition für Microsoft Intune – Januar 2019

> [!Note]
> GHV-Benachrichtigung: Die folgenden Änderungen sind in der Entwicklung für Intune. Die Freigabe dieser Informationen erfolgt im Geheimhaltungsvertrag (GHV) auf einer sehr begrenzten Basis. Posten Sie keine der folgenden Informationen in sozialen Medien oder auf öffentlichen Websites wie Twitter, UserVoice, Reddit usw. 

Die **Early Edition** enthält eine Liste der Features, die im Rahmen des Geheimhaltungsvertrags freigegeben und in späteren Releases von Microsoft Intune zur Verfügung stehen werden. Diese Informationen werden auf einer begrenzten Basis bereitgestellt, und Änderungen sind vorbehalten. Verfassen Sie außerhalb Ihres Unternehmens keinen Tweet oder Post auf UserVoice o.Ä. über diese Informationen. Einige der hier aufgeführten Features werden möglicherweise bis zum Stichtag nicht fertig und werden erst in eine spätere Version aufgenommen. Andere Features werden in einer Pilotphase getestet (Test-Flighting), um sicherzustellen, dass sie für Kunden bereit sind. Wenden Sie sich mit Fragen oder Bedenken an den Ansprechpartner für Ihre Microsoft-Produktgruppe.

Diese Seite wird regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune im Azure-Portal

<!-- 1901 start -->


### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Bereitstellung von online lizenzierten Microsoft Store für Unternehmen-Apps <!-- 1672660  -->
Sie können die erforderlichen, online lizenzierten Microsoft Store für Unternehmen-Apps im Gerätekontext zuweisen. Wenn Sie eine Microsoft Store für Unternehmen-App auf diese Weise bereitstellen, kann die App für alle Benutzer auf dem Gerät installiert werden. Dies gilt nur für Windows 10 RS4-Desktopgeräte und höher. Die Option zur Installation im Gerätekontext ist auf der Seite für die Zuweisung von Client-Apps für online lizenzierte Microsoft Store für Unternehmen-Apps verfügbar.


<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android Enterprise APP-WE-App-Bereitstellung <!-- 1171203 -->
Für Android-Geräte in einem Bereitstellungsszenario mit einer nicht registrierten App-Schutzrichtlinie ohne Registrierung (App Protection Policy Without Enrollment, APP-WE) können Sie mit verwaltetem Google Play Store-Apps und branchenspezifische Apps für Benutzer bereitstellen. Insbesondere kann die IT-Abteilung Endbenutzern einen App-Katalog bieten und für einen Installationsvorgang sorgen, in dem Endbenutzer nicht mehr den Sicherheitsstatus ihrer Geräte kompromittieren müssen, indem sie Installationen aus unbekannten Quellen zulassen. Darüber hinaus sorgt dieses Bereitstellungsszenario für höhere Benutzerfreundlichkeit.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Das Intune App SDK unterstützt 256-Bit-Verschlüsselungsschlüssel <!-- 1832174 -->
Das Intune App SDK für Android verwendet 256-Bit-Verschlüsselungsschlüssel, wenn die Verschlüsselung durch App-Schutzrichtlinien aktiviert ist. Das SDK bietet zur Kompatibilität mit Inhalten und Apps, die ältere SDK-Versionen verwenden, weiterhin Unterstützung der 128-Bit-Schlüssel.


### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Authentifizierungsmethode für Intune-Richtlinienupdate und Installation der Unternehmensportal-App  <!-- 1927359 -->
Bei Geräten, die bereits mithilfe des Setup-Assistenten über eine der Methoden von Apple für die Registrierung von Unternehmensgeräten registriert wurden, unterstützt Intune das Unternehmensportal nicht mehr, wenn es manuell von Endbenutzern aus dem App-Store installiert wurde. Diese Änderung ist nur relevant, wenn Sie sich während der Registrierung mit dem Setup-Assistenten von Apple authentifizieren. Diese Änderung wirkt sich nur auf iOS-Geräte aus, die registriert werden über:  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple Device Enrollment Program (DEP)

Wenn Benutzer die Unternehmensportal-App aus dem App Store installieren und dann versuchen, diese Geräte darüber zu registrieren, erhalten sie eine Fehlermeldung. Es wird vorausgesetzt, dass diese Geräte die Unternehmensportal-App nur dann verwenden, wenn sie während der Registrierung automatisch von Intune per Push übertragen wird. Registrierungsprofile in Intune im Azure-Portal werden aktualisiert, sodass Sie angeben können, wie sich Geräte authentifizieren, und ob sie die Unternehmensportal-App erhalten. Wenn Sie wünschen, dass Ihre DEP-Gerätebenutzer die Unternehmensportal-App verwenden, müssen Sie Ihre Einstellungen in einem Registrierungsprofil angeben. Darüber hinaus wird der Bildschirm **Identifizieren Sie Ihr Gerät** in der Unternehmensportal-App bald veraltet sein.  
Um die Unternehmensportal-App auf bereits registrierten DEP-Geräten zu installieren, müssen Sie zu „Intune“ > „Client-Apps“ wechseln und sie als verwaltete App mit App-Konfigurationsrichtlinien mithilfe von Push übertragen. Nähere Informationen zu diesen Schritten erhalten Sie in zukünftigen Dokumentationen.


### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrative Vorlagen stehen als Public Preview zur Verfügung und werden in ihr eigenes Konfigurationsprofil verschoben <!-- 3322847 -->
Administrative Vorlagen in Intune (**Gerätekonfiguration** > **Administrative Vorlagen**) stehen derzeit als Public Preview zur Verfügung. Mit diesem Update: Administrative Vorlagen umfasst über 300 Einstellungen, die in Intune verwaltet werden können. Diese Einstellungen waren zuvor nur im Gruppenrichtlinien-Editor vorhanden.
Administrative Vorlagen stehen als Public Preview zur Verfügung und werden von **Gerätekonfiguration** > **Administrative Vorlagen** verschoben. Gehen Sie zukünftig wie folgt vor, um administrative Vorlagen aufzurufen: **Gerätekonfiguration** > **Profile** >**Profil erstellen**, wählen Sie für **Plattform** **Windows 10 und höher** und für **Profiltyp** **Administrative Vorlagen** aus.
Berichterstellung wird aktiviert. Gilt für: Windows 10 und höher

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Dunkler Modus für Intune macOS-Unternehmensportal <!-- 3300524 -->
Das Intune macOS-Unternehmensportal unterstützt ab sofort den dunklen Modus für macOS. Wenn Sie den dunklen Modus auf einem Gerät mit macOS 10.14 und höher aktivieren, wird das Erscheinungsbild des Unternehmensportals an die Farben für diesen Modus angepasst.

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>App-Schutzrichtlinieneinstellungen (APP) für Webdaten <!-- 2662995 -->
App-Richtlinieneinstellungen für Webinhalte auf Android- und iOS-Geräten werden aktualisiert, um sowohl HTTP- und HTTPS-Weblinks als auch Datenübertragungen über universelle iOS-Links und Android-App-Links besser zu verarbeiten.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Apple VPP-Token, das von einer anderen MDM-Software verwendet wird <!-- 1488946 -->
Intune erkennt und zeigt Details an, wenn ein VPP-Token (Apple Volume Purchase Program) von Intune und einer anderen MDM-Software verwendet wird.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Abgekoppelte Geräte im Gerätekonformitätsdashboard <!-- 1981119 -->
In einem zukünftigen Update werden abgekoppelte Geräte aus dem Gerätekonformitätsdashboard entfernt. Dadurch werden Ihre Konformitätsnummern geändert.


## <a name="notices"></a>Benachrichtigungen

Derzeit gibt es keine aktiven Benachrichtigungen.

### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).



